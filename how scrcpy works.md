---
created: 2026-03-27T00:25:28+08:00
modified: 2026-03-27T00:27:45+08:00
---

# how scrcpy works

check out myscrcpy for reference?

https://github.com/me2sy/MYScrcpy

https://pypi.org/project/pyscrcpy/

https://github.com/leng-yue/py-scrcpy-client

---

Scrcpy works by pushing a lightweight server component to the Android device and executing it via ADB. The server runs in the background, captures the screen, encodes it as a video stream (H.264/H.265), and sends it back to the PC client over a socket. The client then decodes and displays the stream. Below is a detailed explanation of the process, focusing on execution, communication, and how options are passed.

---

## 1. Pushing and Executing the Server

The scrcpy-server is a ZIP archive (containing `classes.dex`, `AndroidManifest.xml`, etc.) that is **not** installed as a regular app. Instead, it’s pushed to the device and executed directly using Android’s `app_process` tool.

**Steps:**

- **Push the server** to a writable location (e.g., `/data/local/tmp/scrcpy-server`):
  ```bash
  adb push scrcpy-server /data/local/tmp/
  ```

- **Set up ADB reverse tunnels** – the client creates two local TCP sockets and uses `adb reverse` to forward connections from the device to these ports.  
  *Why?* This allows the server (running on the device) to connect back to the client easily, without needing to know the PC’s IP address.
  ```bash
  adb reverse localabstract:scrcpy_video localabstract:scrcpy_video
  adb reverse localabstract:scrcpy_control localabstract:scrcpy_control
  ```
  (In practice, the client chooses random port numbers and uses `adb reverse tcp:PORT tcp:PORT`.)

- **Start the server** with `app_process`, specifying the video and control ports as arguments:
  ```bash
  adb shell CLASSPATH=/data/local/tmp/scrcpy-server app_process / com.genymobile.scrcpy.Server 1.25 2.4 27183 27184
  ```
  - `CLASSPATH` points to the server ZIP (the dex files are loaded from it).
  - `app_process` runs the Java class `com.genymobile.scrcpy.Server` in the shell’s process.
  - The arguments are: version, log level, video port, control port (actual order may vary, but ports are passed).

The server now runs on the device and will attempt to connect to `localhost:video_port` and `localhost:control_port`. Thanks to the ADB reverse tunnels, these connections are forwarded to the client’s corresponding local sockets.

---

## 2. Communication Channels

The client and server maintain **two separate sockets**:

1. **Video socket** – used for streaming the encoded video frames from device to client.
2. **Control socket** – used for:
   - Sending configuration options from client to server.
   - Acknowledging the setup.
   - Later, sending input events (touch, keyboard, etc.) from client to server (if enabled).

After the server connects both sockets, the communication proceeds as follows:

### 2.1 Sending Configuration Options

Once the control connection is established, the client sends a **device descriptor** – a serialized object containing all the requested settings:

- `displayId` – which display to mirror (0 = main display).
- `maxSize` – maximum width/height to scale the video.
- `bitRate` – encoding bitrate (e.g., 8 Mbps).
- `maxFps` – maximum frame rate.
- `lockVideoOrientation` – forced orientation.
- `tunnelForward` – whether to use a separate tunnel for video.
- … and other options like `sendFrameMeta`, `control` (enable/disable input control).

The server reads this descriptor, sets up the screen capture and encoder accordingly, and then sends an acknowledgment.

*Why not use command‑line arguments?*  
Early versions of scrcpy did pass options as command‑line parameters, but this limited flexibility (e.g., changing settings after connection). Moving to a socket‑based negotiation allows dynamic configuration and easier addition of new options.

### 2.2 Video Stream Transmission

The server uses Android’s **MediaProjection** API to capture the screen and **MediaCodec** to encode the frames. The encoded data (NAL units) is sent over the video socket using a simple packet format:

```
[4-byte length] [payload (H.264/H.265 data)]
```

- The client reads the length, then reads the exact number of bytes, and feeds them to a decoder (e.g., via FFmpeg or a hardware‑accelerated decoder) for display.

**Key details:**
- The server obtains a `Surface` from the encoder and passes it to `MediaProjection.createVirtualDisplay()` – the display output is drawn directly into the encoder.
- The encoder runs in a loop, pushing output buffers to the socket as soon as they are available.
- If control is enabled, the client can send input events (touch, key, mouse) over the control socket, which the server injects using `InputManager`.

---

## 3. How Options Like “display id” and “timeout” Are Handled

- **display id** – included in the device descriptor sent over the control socket. The server uses it to capture a specific display (e.g., secondary displays on foldable devices).
- **timeout** – usually refers to the **connection timeout** while waiting for the server to connect. The client sets a timeout (e.g., 3 seconds) when establishing the ADB reverse tunnels and waiting for the server to connect. If the server doesn’t connect within that time, the client aborts. There’s no “timeout” option passed to the server; it’s a client‑side mechanism.

---

## 4. Execution Flow Summary

| Step | Client (PC) | Device |
|------|-------------|--------|
| 1 | Push scrcpy-server ZIP | – |
| 2 | Create local sockets (video + control) | – |
| 3 | `adb reverse` to forward device ports to local sockets | – |
| 4 | – | `app_process` starts the server with the port numbers |
| 5 | – | Server connects to localhost:video_port and localhost:control_port (tunnelled to client) |
| 6 | Send device descriptor over control socket | – |
| 7 | – | Configure MediaProjection & MediaCodec according to descriptor, send ack |
| 8 | – | Start capturing and encoding video; send packets over video socket |
| 9 | Receive video packets, decode, display | – |
| 10 | (Optional) Send input events over control socket | – |

---

## 5. Why the Server Is a ZIP (Not an APK)

- The server runs in the **shell** user context, not as a regular app. It doesn’t need installation – it’s simply a Java program that can be launched with `app_process`.
- The ZIP contains the compiled dex code (`classes.dex`) and a minimal `AndroidManifest.xml` that is used **only** for the `MediaProjection` permission request. When the server needs to ask for screen‑capture permission, it starts an invisible activity declared in that manifest. This activity requests the permission and returns a token to the server, which then uses it to create the virtual display.
- The manifest also includes the necessary permissions (`FOREGROUND_SERVICE`, `RECORD_AUDIO`, etc.), but they are not enforced at install time because the server is not installed.

---

## 6. Security and Permissions

- The server runs with the shell’s UID, which has many system privileges (e.g., injecting input events) but **cannot capture the screen without explicit user consent**. The MediaProjection API requires an explicit user‑granted token, which is obtained via the temporary activity.
- The ADB reverse tunnels are created only for the duration of the session and are removed when the client exits.
- Input injection is only possible if the client enables the `--control` option and the server has the necessary permissions (the shell user can inject events via `InputManager` without additional user prompts).

---

## 7. References for Deeper Understanding

- Source code of the server: [scrcpy/server](https://github.com/Genymobile/scrcpy/tree/master/server)
- Source code of the client: [scrcpy/app](https://github.com/Genymobile/scrcpy/tree/master/app)
- `app_process` documentation (part of Android’s `dalvikvm` tools).

By understanding this flow, you can see how scrcpy achieves low‑latency screen mirroring without needing to install any permanent software on the device.
