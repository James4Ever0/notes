---
created: 2026-03-26T20:04:12+08:00
modified: 2026-03-26T20:04:24+08:00
---

# Long time audio recording

Yes, what you're describing is absolutely achievable. An ESP32 is a great choice for this project because it balances processing power, connectivity, and low power consumption. It can handle the heavy work of compressing audio and managing files without draining your battery.

However, recording a full day of audio presents two main challenges: **storage space** and **power management**. Here is a practical architecture to solve them.

### 💡 The Recommended System Architecture

*   **Main Controller: ESP32**. It is powerful enough for Wi-Fi/Bluetooth and audio processing, while having excellent low-power modes for deep sleep between recordings.
*   **Audio Codec: VS1053**. This is a dedicated chip that handles MP3 encoding. It offloads the heavy work from the ESP32, saving power and simplifying your code.
*   **Storage: microSD Card**. A 32GB card provides ample space (about 178 days at 8kbps MP3) and uses the SDMMC or SPI interface for fast data writing.
*   **Microphone: MEMS (e.g., INMP441) with I2S**. These digital microphones connect directly to the ESP32's I2S bus, provide good quality, and are simple to interface with.

### 💾 Calculating Your Storage Needs

The choice of audio format is critical. MP3 is the best choice for balancing quality and file size. A setting of **8 kHz sample rate, 16-bit depth, and mono** is perfectly clear for speech and highly compressed.

Let's look at the storage difference for **24 hours** of recording:

*   **Uncompressed (WAV)**: ~2.5 GB (This would fill a card very fast and consume more power writing data).
*   **Low-bitrate MP3 (8 kbps)**: **~180 MB per day**. A 32GB SD card would hold **~178 days** of recordings!

### 🔋 Power Optimization Strategies

To achieve "all-day" recording on a battery, you need to be smart about power consumption.

1.  **Go to Deep Sleep**: Don't keep the ESP32 on continuously. Record for 1 minute, save the file, then put the ESP32 into deep sleep mode for the remainder of the minute. This can reduce average current consumption to just a few milliamps.
2.  **Turn Off Peripherals**: Power down the SD card and audio codec when they are not actively recording.
3.  **Underclock the ESP32**: Reducing the CPU frequency from 240 MHz to 80 MHz saves significant power, which is fine for simple recording tasks.
4.  **Battery Capacity**: Estimate your average current draw. If your system averages **50mA**, a **1200mAh** battery (like a typical Li-Po) would last **24 hours**.

### ⚠️ Important Technical Considerations

*   **RAM Limitations**: The ESP32 has limited internal RAM (around 290kB free). You must manage memory carefully to avoid crashes. Using **PSRAM (external RAM)** on your ESP32 board makes handling audio buffers much easier.
*   **File System**: Format your SD card as **FAT32**. Your code will need to increment a filename each minute (e.g., `recording_00001.mp3`) to avoid overwriting files.

### 🏆 An Ultra-Low-Power Alternative: Ambiq Apollo4

If you need battery life measured in weeks or months, consider the **Ambiq Apollo4** series. These microcontrollers are in a different league for power efficiency, consuming as little as **3µA per MHz**, compared to the ESP32's ~150mA when active.

However, the trade-off is that the Apollo4 is less common, more expensive, and has a steeper learning curve than the widely-supported ESP32.

### Summary

For your project, an **ESP32** combined with a **VS1053 audio codec** and a **microSD card** is a very effective and cost-efficient solution. By utilizing deep sleep between recordings and low-bitrate MP3s, you can easily achieve your goal of all-day, consecutive recording.

I hope this helps you get started! Would you like more detailed guidance on the wiring connections between the ESP32 and the VS1053 codec?
