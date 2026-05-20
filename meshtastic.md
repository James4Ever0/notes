---
created: 2026-05-20T19:21:59+08:00
modified: 2026-05-20T19:32:09+08:00
---

# meshtastic

以下是完善后的笔记，对 Todo 部分进行了丰富和补充，已知信息已填入，不确定的地方已留出空白或标注待验证。

---

原始笔记

有Python包可以控制节点设备
pip install meshtastic[cli]
可以发信息、导入导出 yaml config、设置 primary message channel、设置 config url
手机端可以蓝牙配对 meshtastic 设备，设置设备名称、设备信息

todo
用 Heltec WiFi LoRa V3 和其他开发板配合来发送信息
比如用一些数据采集开发板：modbus 转串口或者 i2c，编码成信息让开发板发送
或者其他开发板通过串口和 meshtastic 开发板沟通并发送信息
了解具体的针脚，以及适合的其他开发板

---

完善笔记

1. Python 控制基础 (meshtastic CLI / API)

· 安装：pip install meshtastic[cli] 即可获得 meshtastic 命令行工具和 Python API。
· 功能：
  · 发送/接收消息（文本、位置等）。
  · 导入/导出 YAML 格式的配置文件（节点参数、通道、LoRa 设置等）。
  · 设置主要消息通道（--set-chan 或 Python 接口）。
  · 通过 --seturl 配置无线网络参数（URL 协议：meshtastic://）。
· 连接方式：USB 串口、蓝牙、TCP/IP（WiFi 节点）均可。

2. 手机端（Android / iOS）

· 通过蓝牙与 Meshtastic 设备配对。
· 可管理：设备名称、设备信息（短名称、长名称、位置精度等）、通道、加密密钥。

---

TODO 丰富：Heltec WiFi LoRa V3 + 其他开发板协同发送数据

2.1 硬件概览

目标：让数据采集板（如 Modbus 采集器、I2C 传感器）通过 Meshtastic 网络无线传输数据。

方案：利用 Meshtastic 的 串口模块（Serial Module） 或 外部 MCU 作为网关，将采集到的数据以文本/JSON 格式注入，再通过 LoRa 发送。

Heltec WiFi LoRa V3 关键引脚（Meshtastic 官方定义）

注意：不同批次的引脚可能略有差异，建议以 Meshtastic 官方文档 为准。

功能 GPIO 备注
LoRa NSS 8 片选
LoRa SCK 9 
LoRa MOSI 10 
LoRa MISO 11 
LoRa BUSY 13 
LoRa RST 12 
LoRa DIO1 14 
UART0 (USB) TX=43, RX=44 连接板载 USB-Serial 芯片，电脑通讯用
UART1 TX= 待确认 , RX= 待确认 通常用于外接模块，需查阅具体版本
I2C SDA= 42 , SCL= 41 板载 OLED 也使用此 I2C
用户 LED 35 可编程
按键 0 按住为低电平（BOOT）

不确定的 UART1 及其他复用引脚请留空，使用时需通过 meshtastic --info 或查阅原理图。

2.2 工作模式选择

模式 A：外部 MCU 通过串口直连 Heltec 的 UART1

1. 连接：将采集板（如 Arduino Nano、ESP32 DevKit）的 TX 接到 Heltec 的 RX，RX 接 TX，共地。
2. Meshtastic 配置：
   · 启用串口模块：meshtastic --set serial.enabled true
   · 指定串口引脚（根据硬件）：--set serial.rxd <引脚号>、--set serial.txd <引脚号>
   · 波特率：--set serial.baud 115200（须与采集板一致）
   · 模式：serial.mode 设为 TEXTMSG（收到字符串即作为文本消息发送到默认通道）
3. 数据编码：
   · 采集板只需将传感器数据格式化为文本（如 {"temp":23.5,"hum":60}）通过串口输出。
   · Heltec 收到后会自动广播。

模式 B：Modbus 设备 → 中间 MCU → 串口 → Heltec

· Modbus RTU 通常为 RS485 电平，不可直接接 3.3V 的 GPIO。
· 需要 MAX485 / SP3485 模块进行电平转换，与中间 MCU（如 Arduino Uno、ESP32）通信。
· 中间 MCU 轮询 Modbus 寄存器，再按格式输出到串口连接 Heltec。

模式 C：I2C 传感器 → 中间 MCU → 串口 → Heltec

· I2C 传感器（如 BME280、SHT30）连接到中间 MCU 的 I2C 总线。
· 中间 MCU 读取后，同样通过串口发送给 Heltec。
· 如果 Heltec 引脚充足，也可直接在 Heltec 上通过 I2C 读取传感器，但需要自定义 Meshtastic 固件或使用远程硬件功能（Remote Hardware，实验性）。推荐先走中间 MCU 方案，更稳定。

模式 D：其他开发板通过串口与 Heltec “沟通”

· 凡是具备 UART 的开发板（STM32、Raspberry Pi Pico、ATTiny 等）均可。
· 通信协议可自定义：纯文本、JSON、二进制（需解析），只要 Meshtastic 的串口模式支持（TEXTMSG 可接收任意字节流并发送）。
· 双向控制：可通过 Python API（连接 Heltec 的 USB）或串口命令（如 meshtastic --sendtext）发送指令。

2.3 适合搭配的其他开发板（推荐列表）

开发板 用途 接口 备注
Arduino Nano Modbus 转串口、I2C 采集 UART, I2C, SPI 5V 电平，需电平转换或直连（耐受性检查）
ESP32 DevKit 更复杂的网关、WiFi/蓝牙汇集 UART, I2C 3.3V 电平，直连安全
Raspberry Pi Pico 低功耗传感器采集 UART, I2C 3.3V，MicroPython 灵活
STM32 Blue Pill 工业采集，多路串口 UART 3.3V，高性能
MAX485 + 任何 MCU RS485 转 UART UART 用于连接 Modbus 设备

电平匹配：Heltec V3 为 3.3V 系统，直接连接 5V 板可能损坏引脚。务必使用逻辑电平转换器或确保对方板为 3.3V 容忍。

2.4 消息编码建议

· 简洁：T:23.5 H:60 （纯文本）
· 结构：{"t":23.5,"h":60} （JSON，方便解析）
· 二进制：0xAA 0x02 0x17 0x3C ... （需在接收端解码）
  Meshtastic 默认通道支持明文文本，如需低负载可启用 serial.mode 的 RAW 或 PROTO 模式，但需配套解析。

2.5 待验证 / 不确定部分

· Heltec V3 UART1 的确切 TX/RX 引脚（需查阅原理图或 meshtastic --info 输出）
· 串口模块的 serial.rxd / serial.txd 可使用的 GPIO 范围（是否与 LoRa、OLED 冲突）
· 在 TEXTMSG 模式下，最大数据包长度限制（通常约 237 字节，受 LoRa 包大小限制）
· 中间 MCU 与 Heltec 共享同一电源时的稳定性（建议加滤波电容）
· 使用 Remote Hardware（GPIO 控制、I2C 读取）的成熟度（Meshtastic 2.2+ 实验功能）

---

后续步骤

1. 烧录 Meshtastic 固件至 Heltec V3（使用 flasher.meshtastic.org）。
2. 通过 USB 连接，用 meshtastic --info 确认硬件引脚、通道等信息。
3. 尝试启用 Serial Module，用电脑模拟串口数据测试发送。
4. 连接实际传感器/采集板，验证端到端传输。
