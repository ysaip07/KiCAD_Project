A Solar Panel Monitoring System PCB designed using KiCad. This board enables real-time measurement and logging of solar panel voltage, current, and power output — providing actionable data for solar energy performance analysis and optimization.
System Description
The Solar Monitoring System uses voltage dividers and current sensing ICs to measure panel output parameters. A microcontroller reads ADC values, computes power, and outputs data to a display or wireless interface for remote monitoring.

Measured Parameters:
- Voltage — Panel output voltage via precision voltage divider
- Current — Load current via shunt resistor + INA219 current sensor IC
- Power — Computed: P = V × I
- Energy — Accumulated over time (Wh)

Features
- Real-time voltage and current measurement
- INA219 / ACS712 current sensor integration
- Microcontroller-based data acquisition (ESP32 / Arduino)
- OLED / LCD display for local readout
- Wi-Fi data logging support (ESP32 variant)
- Overvoltage protection circuitry
- Compact 2-layer PCB design
