---
created: 2026-03-25T13:24:37+08:00
modified: 2026-03-25T13:25:08+08:00
---

# Wearable time lapse camera

For your specific requirements—especially 24/7 operation and easy PC access—the **Raspberry Pi Zero W** is likely the better fit. It runs a full Linux OS, making USB mass storage access straightforward, and there is a complete, open-source build guide available for it.

The choice really depends on how much time you want to spend on software configuration and battery management. Here’s a quick comparison to help you decide:

| Feature | **Raspberry Pi Zero W (with Camera)** | **ESP32-S3 (e.g., M5Stack CAMS3)** |
| :--- | :--- | :--- |
| **Software Complexity** | Low to Medium (Linux OS, simpler scripting)  | High (Requires ESP-IDF/Arduino, deep sleep coding)  |
| **PC Access (USB)** | **Excellent.** Plug SD card into PC, or configure USB gadget mode. | **Limited.** Requires code to write to SD card; accessed by moving the card.  |
| **Power Efficiency** | **Higher power draw** (ideal to pair with a large power bank). | **Very low power draw** (can last days on a small battery with deep sleep). |
| **Build Resources** | **Complete.** Adafruit provides a step-by-step guide, 3D case, and software.  | **Modular.** You'll need to assemble parts and write your own camera control code. |
| **Cost** | Low (~$15 for Pi Zero + ~$10 for Camera Module)  | Low (~$20-$30 for a complete unit like M5Stack)  |

### 🏆 Why Raspberry Pi Zero is the Recommended Choice

For a first build that prioritizes reliability and ease of getting photos onto your computer, the **Raspberry Pi Zero W** is the clear winner.

*   **Your Own Personal Lifelogger:** There is a fantastic, **open-source project from Adafruit** specifically for a wearable time-lapse camera . It includes:
    *   **3D-Printable Case:** A lanyard-style case you can print yourself .
    *   **Complete Wiring Diagram:** Shows you how to connect a battery charger, power switch, and status LED .
    *   **Python Script:** A ready-to-run script that you can easily modify to take a photo every **60 seconds** (instead of the default 15) .
*   **Easy File Access:** By default, the Adafruit script saves photos to the `/boot` folder on the microSD card . This is the partition Windows or macOS can read. You can simply pop out the card, insert it into your computer, and copy the files—no special software or network setup needed.
*   **Solving the Battery Problem:** The guide's default 500mAh battery only lasts about **2 hours** . However, you can easily solve this by skipping the small battery and powering the Pi directly from a large **USB power bank** (e.g., 10,000mAh or 20,000mAh) via its USB port. This is the simplest way to get 24/7 operation.

### 🤔 When to Consider the ESP32-S3

An ESP32-S3 board, like the M5Stack CAMS3 Unit, is a fantastic choice if your top priority is a super-compact size and maximizing battery life .

*   **Ultra-Low Power:** Its main advantage is the ability to use "deep sleep." You can program it to wake up every minute, take a photo, save it to the microSD card, and go back to sleep. A single 1000mAh battery could last for days.
*   **The Trade-Off:** It requires more complex programming (C++). You also lose the easy "plug-and-play" USB access; you will need to write your own code to manage the USB connection or remove the SD card to view files .

### 🛠️ Getting Started with the Pi Zero Build

If you want to move forward with the Raspberry Pi option, here is your roadmap:

1.  **Get the Hardware:** You will need a **Raspberry Pi Zero W** (version 1.3 or later, with the camera connector), a **Raspberry Pi Camera Module** (V2 is great), a large **microSD card**, and a **high-capacity USB power bank** .
2.  **Follow the Guide:** The **Adafruit Wearable Time-Lapse Camera guide** is your bible for this project. It has everything: the bill of materials, wiring instructions, and software setup steps .
3.  **Modify the Software:** The guide's Python script is where you'll make your changes. Set the `INTERVAL` variable to `60`, and ensure the `DEST` variable points to a folder on the `/boot` partition for easy access .

A Raspberry Pi Zero running the Adafruit project will give you a proven, open-source foundation to build on.

If you decide to go with the Pi, do you need help choosing the right camera module version or figuring out the best way to mount a large power bank?
