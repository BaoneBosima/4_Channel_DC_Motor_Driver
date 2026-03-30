# Quad-Channel Motor Driver Node (STM32 & CAN)

---


## 🚀 Key Features

- **Quad-Channel Drive:** Independent control of 4 DC motors using dual high-efficiency MOSFET H-Bridges.
- **Networked Intelligence:** Onboard STM32 microcontroller offloads low-level hardware timing from the main robot computer.
- **Industrial Communication:** CAN Bus (ISO 11898) interface with impedance-controlled differential routing for high noise immunity.
- **High-Efficiency Power Stage:** Integrated synchronous buck converter delivering 95% efficiency, drastically reducing thermal waste.
- **Robust Protection:** Hardware-level reverse polarity protection (P-MOSFET) and LC noise filtering.

---

## 🛠 Hardware Specifications

| | |
| --- | --- |
| **Microcontroller** | STM32F103C8T6 (ARM Cortex-M3, 72MHz) |
| **Motor Drivers** | 2x Toshiba TB6612FNG (1.2A Continuous / 3.2A Peak per channel) |
| **Power Regulation** | MP2315 Synchronous Buck Converter (12V to 3.3V @ 3A) |
| **Transceiver** | SN65HVD230 CAN Transceiver |
| **Input Voltage** | 12V DC Nominal |
| **Max Current Rating** | 4A Continuous (Board Total) |

---

## 📐 PCB Layout & Stackup

The board was designed in KiCad 8.0 utilizing a 4-layer, impedance-controlled stackup to ensure signal integrity in a mixed-signal environment.

| Layer | Description |
| --- | --- |
| **Layer 1 (Top - Signal)** | Component placement, high-speed MCU routing, and localized thermal ground pours. |
| **Layer 2 (Inner - GND Plane)** | Solid, unbroken reference plane to minimize loop inductance, suppress EMI, and prevent ground bounce. |
| **Layer 3 (Inner - Power Plane)** | Dedicated 12V distribution plane, calculated via IPC-2221 standards to handle high-current motor transients with minimal IR drop. |
| **Layer 4 (Bottom - Signal)** | Cross-under routing, jumper traces, and bottom thermal reliefs. |

### Thermal Management

Extensive via stitching is implemented around the H-Bridge drivers and the buck converter. This couples the surface copper to the internal planes, effectively turning the PCB itself into a heatsink to handle stall currents without external cooling hardware.
