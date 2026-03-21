---
created: 2026-03-21T18:33:14+08:00
modified: 2026-03-21T18:33:47+08:00
---

# Run Android Emulator Without Android Studio

You can run the Android Emulator without installing the full Android Studio by using only the Android SDK Command Line Tools. This is lightweight and ideal for testing without heavy IDE overhead.

## 1. Install Required Tools

- Install **Java (JDK 11 or higher)** from the [Oracle JDK downloads](https://www.oracle.com/java/technologies/javase-downloads.html).
- Download **Command Line Tools** from the [Android Developer site](https://developer.android.com/studio#command-line-tools-only).
- Extract them to a directory, e.g.:
  - **macOS/Linux**: `~/Android/sdk`
  - **Windows**: `C:\AndroidSDK`

## 2. Set Environment Variables

Add these lines to your shell configuration (on macOS/Linux: `~/.zshrc` or `~/.bashrc`; on Windows: System Environment Variables):

```bash
export ANDROID_SDK_ROOT="$HOME/Android/sdk"
export PATH="$ANDROID_SDK_ROOT/cmdline-tools/latest/bin:$PATH"
export PATH="$ANDROID_SDK_ROOT/emulator:$PATH"
export PATH="$ANDROID_SDK_ROOT/platform-tools:$PATH"
```

Reload the configuration:

```bash
source ~/.zshrc
```

## 3. Install SDK Components

Run the following commands:

```bash
sdkmanager "platform-tools" "emulator"
sdkmanager "platforms;android-34"
sdkmanager "system-images;android-34;google_apis_playstore;x86_64"
```

Accept all licenses when prompted.

## 4. Create an Android Virtual Device (AVD)

```bash
avdmanager create avd --name MyAVD \
  --package "system-images;android-34;google_apis_playstore;x86_64" \
  --device pixel
```

Replace `MyAVD` with your preferred name.

## 5. Run the Emulator

```bash
emulator -avd MyAVD -no-snapshot-load -gpu on -memory 4096 -cores 4
```

- `-gpu on`: Enables GPU acceleration
- `-memory 4096`: Allocates 4GB RAM
- `-cores 4`: Uses 4 CPU cores

## Tips

- Use `emulator -list-avds` to see available devices.
- If the emulator freezes, stop it with:
  ```bash
  adb -s emulator-5554 emu kill
  ```
- Keep SDK updated:
  ```bash
  sdkmanager --update
  ```

This method gives you a fully functional Android Emulator without installing Android Studio, saving space and improving performance.
