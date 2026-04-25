# **One-Handed Keyboard**

> We received a very special message. The sender's daughter was struck by a heavy truck on her way to school, permanently losing the function of her right hand. Using a computer became exhausting, as she had to constantly switch between the keyboard and mouse while typing slowly and with great effort. He reached out asking if we could help build a one-handed keyboard for his daughter.

![Left Hand Small Keyboard](/Docs/Image/左手小键盘右侧面.jpg "Left Hand Small Keyboard")

![Left Hand Large Keyboard](/Docs/Image/左手大键盘右侧.jpg "Left Hand Large Keyboard")

This is a single-mode mechanical keyboard with an integrated trackball. The firmware is built on [QMK](https://github.com/qmk/qmk_firmware). We sincerely thank all developers who have contributed to the QMK community.

Keyboard design reference: [【He Tongxue】We built a special keyboard…](https://www.bilibili.com/video/BV1DtjAzUEb9)

Open-source hardware: [HTXStudio One-Handed Keyboard](https://oshwhub.com/htx-studio/One-Handed_Keyboard)

[GitHub Repository](https://github.com/htx-studio/One-Handed-Keyboard)

[Gitee Repository](https://gitee.com/htxstudio/one-handed-keyboard)

For setting up the development environment, refer to [the QMK getting started guide](https://docs.qmk.fm/newbs_getting_started "Set up your QMK environment"). The firmware source code is available [here](https://github.com/htx-studio/qmk_firmware/tree/master/keyboards/htx_studio).

This repository includes:

* 8 PCB designs for a total of three keyboard variants (left-hand and right-hand), provided as LCEDA/EasyEDA projects.
* VIA keymap configuration files and pre-compiled firmware binaries.
* 3D model design files.

---

## Repository Structure

#### Docs

Chip datasheets and reference images.

#### Firmware

QMK firmware for the three keyboard variants, along with JSON files for VIA key remapping.

#### Hardware

Project files for JLCEDA (EasyEDA).

#### Model

3D model files and manufacturing files for each keyboard variant.

---

## Build Guide

### PCB

**1 – Right-Hand Keyboard – Hot-Swap (Large):** FR-4 material, 1.6 mm thickness, 4-layer board, stackup JLC04161H-3313, impedance control ±20%.

**1 – Left-Hand Keyboard – Solder (Small):** FR-4 material, 1.6 mm thickness, 2-layer board. ALPS yellow switches require slight force when inserting.

**1 – Left-Hand Keyboard – Hot-Swap (Large):** FR-4 material, 1.6 mm thickness, 4-layer board, stackup JLC04161H-3313, impedance control ±20%.

**2 – Type-C Daughterboard:** FR-4 material, 1.6 mm thickness, 2-layer board. Connector labeled CON1 (large keyboard only).

**3 – Trackball Module:** FR-4 material, 1.6 mm thickness, 2-layer board. Pay attention to the soldering orientation. Connector labeled CON3.

**4 – Scroll Wheel Module:** FR-4 material, 1.6 mm thickness, 2-layer board. Recommended encoder height: 7 mm; button height: 6 mm; button actuation force ≤ 180 g. Connector labeled CON2.

**5 – Directional Button Module:** FR-4 material, 1.6 mm thickness, 2-layer board. ALPS yellow switches require slight force when inserting. Connector labeled CON4.

**6 – Main Control Board – Left-Hand (Small):** FR-4 material, 1.6 mm thickness, 2-layer board.

> * Three of the boards are shared control daughterboards used by all keyboard variants: `Trackball`, `Scroll Wheel`, and `Directional Buttons`.
> * The `Directional Buttons` board and the `Left-Hand Keyboard – Solder (Small)` board both use ALPS yellow switches.
> * Note that the large left-hand and right-hand keyboards are **not** perfect mirror images of each other.
> * Trackball control uses the SPI1 channel. The scroll wheel uses two dedicated signal lines, making it straightforward to replace with an alternative input device without significant redesign.
> * The main microcontroller is the **STM32G431CBU6**.
> * Compatible with both USB-A to USB-C and USB-C to USB-C cables.

### Printed Parts

- **Keycaps:** Resin, PLA, or similar materials.
- **Trackball Housing:** Resin, PLA, or similar materials.
- **Mouse Left/Right Buttons:** Resin, PLA, or similar materials.
- **Enclosure:** Resin, PLA, or similar materials.
- **Base:** Resin, PLA, or similar materials.

### Machined Parts

- **Switch Plate:** Recommended material: POM, 1.5 mm thick.
- **Plate Foam Strip:** Adhesive on one side.
- **Sandwich Foam:** Recommended material: Poron, 3.5 mm thick.
- **Switch Pad Foam:** 2 mm thick.
- **Base Foam:** Recommended material: Poron, 4 mm thick.
- **Silicone Pad (small keyboard only):** 5 mm thick, Shore hardness 00-10.

### Hardware (Fasteners)

|                              | Large Keyboard (qty) | Small Keyboard (qty) |
| :--------------------------- | :------------------: | :------------------: |
| M3×3×4 Heat-Set Brass Insert |          8           |          8           |
| M2×2×3 Heat-Set Brass Insert |          2           |          –           |
| M2×3×3 Heat-Set Brass Insert |          17          |          12          |
| M3×6 Countersunk Screw       |          2           |          6           |
| M3×15 Countersunk Screw      |          –           |          4           |
| M3×22 Countersunk Screw      |          6           |          –           |
| M2×8 Socket Head Screw       |          4           |          4           |
| M2×3 Socket Head Screw       |          2           |          –           |
| M2×5 Socket Head Screw       |          13          |          8           |
| M3×16 Flat Head Screw        |          –           |          2           |

### Other Components

- **Trackball:** 25 mm diameter, PTFE material.
- **Bearing Balls:** 2 mm diameter, PTFE material. Installed inside the printed trackball housing; 6 balls required.
- **Scroll Wheel:** Recommended diameter 19–20 mm, thickness 4–5 mm, metal material.
- **Stabilizers:** 2U PCB-mount stabilizers.
- **Switches:** Small keyboard: 57 mini ALPS yellow switches; Large keyboard: 57 standard mechanical switches.
- **FPC Cables:** 0.5 mm pitch, 8-pin, reversed polarity — two 10 cm cables and two 15 cm cables.

> * All FPC connectors on the main control board and the daughterboards are labeled with CON identifiers. Connect matching CON labels together.
> * The design uses dual-direction (top/bottom contact) FPC connectors. When all connectors are oriented with bottom contact, use reversed-polarity FPC cables to connect them.

### Model Structure

![Left Hand Small Keyboard Exploded View](/Docs/Image/左手小键盘爆炸图.jpg "Left Hand Small Keyboard Exploded View")

![Left Hand Large Keyboard Exploded View](/Docs/Image/左手大键盘爆炸图.jpg "Left Hand Large Keyboard Exploded View")

### Assembly Order

> The following steps use the large keyboard as an example.

**Pre-Assembly Preparation**

* Connect the 4 daughterboards to the main keyboard PCB using FPC cables, then flash the firmware.
* Install 3–5 switches along with the scroll wheel and trackball, and verify that all functions are working correctly before proceeding with full assembly.
* Insert the correct heat-set brass inserts into the appropriate locations on the printed enclosure and base.
* Print legends on the keycaps.
* Attach foam strips to both sides of the protruding sections of the switch plate.

> **First-time firmware flashing:** Hold the button marked "B" on the back of the PCB, then connect the USB cable to enter bootloader mode.
>
> **Firmware updates:** Hold the "ESC" key on the keyboard, then connect the USB cable to enter bootloader mode.
>
> For more information, refer to [Flashing Your Keyboard (QMK)](https://docs.qmk.fm/newbs_flashing).

**Assembly Steps**

1. Secure the 4 daughterboards to their corresponding positions on the base using screws (pay attention to cable routing and orientation). Attach the trackball housing screws from below.
2. Fasten the left and right mouse buttons to the main keyboard PCB using screws.
3. Layer the components into the fan-shaped cavity of the base from bottom to top in the following order: base foam → switch pad foam → keyboard PCB → sandwich foam → switch plate.
4. Insert the key switches.
5. Place the enclosure over the assembly and secure it with screws from below.
6. Install the keycaps to complete the build.

> For screw and insert installation guidance, refer to the notes in the [Model directory](https://github.com/htx-studio/One-Handed-Keyboard/tree/main/Model).

This is our first open-source project. We welcome any feedback, suggestions, or corrections. Thank you for your interest and support.

---

## References

[Quantum Mechanical Keyboard Firmware](https://docs.qmk.fm/)

mrjohnk. ADNS-9800. [GitHub Repository](https://github.com/mrjohnk/ADNS-9800/)
