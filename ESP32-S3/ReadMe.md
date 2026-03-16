What is the ESP32-S3?
The ESP32-S3 is a powerful System-on-Chip (SoC) made by Espressif Systems. It's the brain of your entire board — a microcontroller with built-in Wi-Fi and Bluetooth.

Key Features (from your schematic — U2: ESP32-S3-WROOM-1)
🧠 Processing Power
- Dual-core Xtensa LX7 processor running at up to 240 MHz
- Much faster than a regular Arduino (16 MHz)
- Can run two tasks simultaneously on two cores

📶 Wireless
- Wi-Fi 802.11 b/g/n — connect to internet/router
- Bluetooth 5.0 (BLE) — connect to phones, sensors, etc.
- All antenna circuitry is built into the WROOM-1 module

Overview
A fully custom ESP32-S3-WROOM-1 development board designed from scratch in KiCad. The board integrates USB-C connectivity, onboard LDO power regulation, RGB LED, temperature & humidity sensing (Si7021), QWIIC connector, SPI I/O header, and user controls — making it a versatile platform for IoT and embedded development.
Schematic Breakdown

🔌 USB-C Interface
- USB-C Receptacle with VBUS, D+/D− lines
- Polyfuse (1A) for overcurrent protection
- BLM21PG220 ferrite bead for EMI filtering
- 1N5817 Schottky diode for reverse polarity protection
- USBLC6-2SC6 TVS diode for USB ESD protection
- CC1/CC2 pull-down resistors (5.1kΩ) for USB-C power negotiation
- 22Ω series resistors on USB D+/D− for signal integrity

⚡ LDO Power Regulation
- LM1117-3.3 linear regulator — converts 5V (USB) to clean 3.3V
- Input bulk capacitor: 22µF
- Output decoupling: 22µF + 100nF
- Power indicator LED (D4) on 3.3V rail

🧠 Microcontroller — ESP32-S3-WROOM-1 (U2)
- Dual-core Xtensa LX7 @ 240 MHz
- Wi-Fi 802.11 b/g/n + Bluetooth 5 (LE)
- Full GPIO breakout: IO0–IO48
- UART: ESP_TXD, ESP_RXD
- SPI: MOSI, MISO, CLK, CS broken out to I/O header
- I2C: SDA, SCL routed to QWIIC and Si7021
- ESP_EN with RC reset filter (10kΩ + 1µF) and reset switch (SW2)
- ESD protection (ESD9B3.3ST5G) on ESP_EN and BOOT lines

🔁 Boot & Reset Controls
- SW2 (RESET) — Manual reset button with RC debounce
- SW2 (BOOT) — Boot mode selection (GPIO0 pull-down)
- ESD9B3.3ST5G protection diodes on both switches

🌈 RGB LED
- LED_Generic_RGB_ARGB (LED1)
- Individual current-limiting resistors: R10 (R), R11 (G), R12 (B)
- Controlled via ESP32-S3 GPIOs: R_LED, G_LED, B_LED

🌡️ Temperature & Humidity Sensor
- Si7021-A20 (U4) — I2C digital sensor
- Decoupling capacitor: 100nF
- Connected via SDA / SCL lines (shared I2C bus)

🔗 QWIIC Connector Interface
- Conn_01x04 (J4) — Standard QWIIC pinout: VCC, GND, SDA, SCL
- Color-coded: VCC=RED, GND=BLACK, SCL=YELLOW, SDA=BLUE
- Pull-up resistors (2.2kΩ) on SDA and SCL

📡 SPI / I/O Header
- Pin_02x05 (J3) — 10-pin dual-row header
- Exposes: RESET, MOSI, MISO, CLK, CS, IRQ, 3V3, GND

🔲 User Switch
- SW3 (USER_SW) — General-purpose user button
- Connected to ESP32 GPIO via 10kΩ pull-up
- Decoupling cap: 1µF for debounce

🔧 Miscellaneous
- 4× Mounting Holes (H1–H4) for mechanical enclosure mounting
- J2 (Conn_02x03) — Debug/programming header: ESP_EN, ESP_TXD, ESP_RXD, ESP_IO0, GND, 3V3
- PSRAM interface pins broken out on ESP32-S3
