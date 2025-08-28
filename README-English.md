# **One-Handed Keyboard**

> We received a very special email. The sender’s daughter was tragically hit by a heavy truck on her way to school and permanently lost the use of her right hand. When using a computer, she has to constantly switch between the keyboard and the mouse, making typing slow and exhausting. He asked us to help create a one-handed keyboard for her.

![Left-hand small keyboard](/Docs/Image/左手小键盘右侧面.jpg "Left-hand small keyboard")

![Left-hand large keyboard](/Docs/Image/左手大键盘右侧.jpg "Left-hand large keyboard")

This is a single-mode mechanical keyboard with a built-in trackball. The firmware uses [QMK](https://github.com/qmk/qmk_firmware). Many thanks to all developers who contribute to the QMK community.

Keyboard inspiration: [Video by He Tongxue (Bilibili)](https://www.bilibili.com/video/BV1DtjAzUEb9)

Hardware open-source files: [HTXStudio One-Handed Keyboard](https://oshwhub.com/htx-studio/One-Handed_Keyboard)

[GitHub repository](https://github.com/htx-studio/One-Handed-Keyboard)
[Gitee repository](https://gitee.com/htxstudio/one-handed-keyboard)

Development setup guide is [here](https://docs.qmk.fm/newbs_getting_started "Set up your QMK environment"). The firmware source code is [here](https://github.com/htx-studio/qmk_firmware/tree/master/keyboards/htx_studio).

This repository contains:

* Eight PCB designs for three different keyboard models (both left- and right-handed), with LCSC EDA project files.
* VIA remapping configuration files and precompiled firmware.
* 3D model design files.

---

## Repository Structure

#### Docs (Documentation)

Datasheets and images of the chips.

#### Firmware

QMK firmware for the three keyboard models, plus VIA keymap JSON files.

#### Hardware

LCSC EDA project files.

#### Model

3D model files and machining files for each keyboard model.

---

## Build Guide

### PCB:

1. Right-hand keyboard – Hot-swappable (large): FR-4, 1.6mm thick, 4 layers, JLC04161H-3313 stackup, impedance control ±20%.
2. Left-hand keyboard – Soldered (small): FR-4, 1.6mm thick, 2 layers. ALPS yellow switches require firm pressing during installation.
3. Left-hand keyboard – Hot-swappable (large): FR-4, 1.6mm thick, 4 layers, JLC04161H-3313 stackup, impedance control ±20%.
4. Type-C daughterboard: FR-4, 1.6mm thick, 2 layers, marked CON1 (only for large keyboards).
5. Trackball module: FR-4, 1.6mm thick, 2 layers, watch soldering orientation, marked CON3.
6. Scroll wheel: FR-4, 1.6mm thick, 2 layers, recommended encoder height 7mm, button height 6mm, actuation ≤180g, marked CON2.
7. Direction keys: FR-4, 1.6mm thick, 2 layers, ALPS yellow switches require firm pressing during installation, marked CON4.
8. Main control board – Left-hand (small): FR-4, 1.6mm thick, 2 layers.

> * The three small control boards are shared across all keyboards: `3-Trackball`, `4-Scroll Wheel`, `5-Direction Keys`.
> * Both `5-Direction Keys` and `1-Left-hand Soldered (small)` use ALPS yellow switches.
> * Note: left-hand and right-hand large keyboards are not perfect mirrors.
> * Trackball uses SPI1 channel; scroll wheel uses two dedicated signal lines, allowing replacement with other devices.
> * MCU: STM32G431CBU6.
> * Compatible with both A-to-C and C-to-C cables.

### 3D-Printed Parts:

* Keycaps: resin, PLA, etc.
* Trackball mount: resin, PLA, etc.
* Mouse buttons: resin, PLA, etc.
* Case: resin, PLA, etc.
* Base: resin, PLA, etc.

### Materials:

* Positioning plate: POM, 1.5mm thick.
* Positioning plate foam strips: single-sided adhesive.
* Sandwich foam: PORON, 3.5mm thick.
* Switch pad foam: 2mm thick.
* Bottom foam: PORON, 4mm thick.
* Silicone pad (only for small keyboard): 5mm thick, Shore 00-10 hardness.

### Hardware:

| Component              | Large Keyboard | Small Keyboard |
| :--------------------- | :------------: | :------------: |
| M3×3×4 heat-set insert |        8       |        8       |
| M2×2×3 heat-set insert |        2       |        –       |
| M2×3×3 heat-set insert |       17       |       12       |
| M3×6 flat-head screw   |        2       |        6       |
| M3×15 flat-head screw  |        –       |        4       |
| M3×22 flat-head screw  |        6       |        –       |
| M2×8 button-head screw |        4       |        4       |
| M2×3 button-head screw |        2       |        –       |
| M2×5 button-head screw |       13       |        8       |
| M3×16 pan-head screw   |        –       |        2       |

### Other Components:

* Trackball: 25mm diameter, PTFE.
* Support balls: 2mm diameter, PTFE, 6 pieces installed in the printed trackball holder.
* Scroll wheel: recommended 19–20mm diameter, 4–5mm thickness, metal.
* Stabilizers: 2U plate-mount stabilizers.
* Switches:

  * Small keyboard: 57 ALPS yellow low-profile switches.
  * Large keyboard: 57 standard mechanical switches.
* Ribbon cables: 0.5mm pitch, 8-pin reverse, two at 10cm and two at 15cm.

> - All control boards and small boards have CON markings for matching connectors.
> - For FPC connectors placed on opposite sides, use reverse ribbon cables when all connectors are bottom-facing.

### Exploded Models:

![Small left-hand keyboard exploded](/Docs/Image/左手小键盘爆炸图.jpg "Small left-hand exploded")
![Large left-hand keyboard exploded](/Docs/Image/左手大键盘爆炸图.jpg "Large left-hand exploded")

### Assembly Order (Large Keyboard Example):

**Pre-assembly steps:**

* Connect the 4 small PCBs to the main keyboard PCB with ribbon cables, flash the firmware.
* Install 3–5 switches, scroll wheel, and trackball. Check functionality before full assembly.
* Insert heat-set inserts into the case and base.
* Print legends on keycaps.
* Stick foam strips onto positioning plate (both sides).

> For the first firmware flash, press the button labeled **“B”** on the back of the PCB while plugging in the USB cable.
> To update firmware, hold **ESC** while plugging in USB.
> See [Flashing Your Keyboard (QMK)](https://docs.qmk.fm/newbs_flashing) for details.

**Assembly steps:**

1. Fix the 4 small PCBs to the base with screws (watch cable orientation). The trackball holder is screwed from below.
2. Mount the mouse buttons on the keyboard PCB.
3. Stack layers in this order: bottom foam → switch pad foam → keyboard PCB → sandwich foam → positioning plate.
4. Insert switches.
5. Place the case on top and secure with screws.
6. Install keycaps. Assembly complete.

> Screw and insert installation guide can be found [here](https://github.com/htx-studio/One-Handed-Keyboard/tree/main/Model).

This is our first open-source project. Any feedback or suggestions are welcome. Thank you!

---

## References

[Quantum Mechanical Keyboard Firmware](https://docs.qmk.fm/)
mrjohnk. ADNS-9800. [GitHub repository](https://github.com/mrjohnk/ADNS-9800/)
