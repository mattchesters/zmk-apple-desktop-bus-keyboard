# ⌨️ Apple Desktop Bus Keyboard modernization project
[![Apple Desktop Bus Keyboard modification video](https://img.youtube.com/vi/NW_LLVD3R3c/0.jpg)](https://www.youtube.com/watch?v=NW_LLVD3R3c)

**This repository includes all the files used in the [mtt](https://www.youtube.com/@mttcx) YouTube video, _"[Apple's BEST keyboard... reimagined](https://www.youtube.com/watch?v=NW_LLVD3R3c)"_.**


<blockquote>
The 1986 Apple Desktop Bus Keyboard is a design marvel known for its enjoyable typing experience, but using it today requires some engineering. This modernization project introduces a custom PCB and development board to add Bluetooth connectivity using ZMK, a low-energy display for layer and device status, and a rotary encoder for volume control. 
</blockquote>

##

This README can be used as supporting information to the video. If you are undertaking this project yourself, please familiarize yourself with [ZMK firmware](https://zmk.dev), and the PCB design and schematic files.

## ⚠️ Disclaimer
The results will vary depending on the condition of your keyboard.  
While efforts have been made to create a functional project, variations in individual keyboard conditions may lead to unique issues.

## ✍️ Schematic & Design
The PCB was designed in KiCad 8.0.

The Schematic, Design, and component Footprints are included in the [KiCad project files](./assets/kicad). 

If you are working on this project, take the time to thoroughly review the design and schematic to understand PCB utilization.

## 🛒 Bill of Materials

| Description | Part | Quantity | Link |
|---|---|---|---|
| Development Board | Seeed Studio XIAO nRF52840 | 1 | [Seeed Studio](https://wiki.seeedstudio.com/XIAO_BLE/) |
| Display | nice!view | 1 | [nice!](https://nicekeyboards.com/nice-view) |
| Rotary encoder | EC11 | 1 | [Amazon](https://www.amazon.co.uk/gp/product/B08728PS6N/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
| USB Port | USB TYPE-C 6P | 1 | [LCSC Electronics](https://www.lcsc.com/product-detail/USB-Connectors_SHOU-HAN-TYPE-C-6P-QT073_C2681548.html/)|
| Display/Encoder receptacle | JST SM05B | 2 | [LCSC Electronics](https://www.lcsc.com/product-detail/Wire-To-Board-Connector_JST-SM05B-SRSS-TB-LF-SN_C136657.html)|
| Display/Encoder plug | JST SHR-05V-S-B | 2 | [See below](#display%20&amp;%20encoder%20cables)|
| Lithium Polymer Battery | 110mAh | 1 | [Cool Components](https://coolcomponents.co.uk/products/lithium-polymer-battery-110mah?_pos=1&_psq=110mw&_ss=e&_v=1.0)
| Battery Connector | JST S2B-PH | 1 | [LCSC Electronics](https://www.lcsc.com/product-detail/Wire-To-Board-Connector_JST-S2B-PH-K-S-GW_C157932.html)|
| 10k resistor | 10k 0805 | 4 | [LCSC Electronics](https://www.lcsc.com/product-detail/Chip-Resistor-Surface-Mount_UNI-ROYAL-Uniroyal-Elec-0805W8F1002T5E_C17414.html)|
| 5.1k resistor | 5.1k 0805 | 2 | [LCSC Electronics](https://www.lcsc.com/product-detail/Chip-Resistor-Surface-Mount_UNI-ROYAL-Uniroyal-Elec-0805W8F5101T5E_C27834.html)|
| Power switch | MINI MSK12CO2 | 1 | [LCSC Electronics](https://www.lcsc.com/product-detail/Slide-Switches_SHOU-HAN-MINI-MSK12CO2_C2681570.html)

## 🔌 Display & encoder cables
As the small JST connectors used to connect the PCB to the display and rotary encoder requires specialist crimping tools, I opted to have the two cables fabricated by [LCSC custom cables](https://www.lcsc.com/customcables/), to the following specification:

| LCSC Part | Manufacture Part | Quantity |
|---|---|---|
| C268102 | JST SHR-05V-S-B | 1 |
| C263995 | SSH-003T-P0.2-H | 5 |

* Cable: AWG 30
* Length: 300mm
* Side 1: JST Connector
* Side 2: Flat cut wires

## 🛍️ Ordering the PCB
For convenience, the Production files have been included in this repository. These can be used to order your own PCB from a prototyping company, such as JLCPCB or PCBWay.

Please be comfortable with the ordering and validation process, as each company is different and may have inaccuracies you are responsible for.

1. Upload the [./assets/pcb/production-packed.zip]() to a provider.
2. If using the Assembly services, make sure all components are correctly placed.

## 📸 Flashing the XIAO Dev Board with ZMK
If you want to modify the firmware, you can review the code in [./boards/shields/adbk]() following the guidance from [ZMK documentation](https://zmk.dev/docs/development/hardware-integration/new-shield).

I have added a release with the firmware I use daily.

1. Connect the XIAO to your computer.
2. Download the **adbk_fw.uf2** from the [Releases](https://github.com/mattchesters/zmk-apple-desktop-bus-keyboard/releases/).
3. Place the XIAO nRF52840 in [bootloader mode](https://wiki.seeedstudio.com/XIAO_BLE/).
4. Drag and drop the **adbk_fw.uf2** file to the **XIAO-SENSE** volume on your computer.

The board will automatically exit bootloader mode and is ready to use.

## 🧑‍🏭 Preparing the PCB
If you have ordered from a fabrication company with assembly services, the may only have to solder the XIAO nRF52840 and through-hole component.

Review the schematic and design files to understand how the components are placed on the PCB.

## 🪛 Preparing the Keyboard
To install the custom components, some parts need to be removed. The process is reversible, allowing the keyboard to be restored to its original state.

1. Flip over the keyboard and remove the 3x screws with a PH2 driver bit.
2. Holding the top of the keyboard, return it to the upright position, then remove the top casing by lifting it upwards.
3. Carefully remove the 20 pin DIP package by lifting each side with equal force.
4. Remove the board from the PCB, by lift the top, and then sliding it upwards.
5. Desolder and remove the ADB ports.
6. Store the ADB ports and 20-pin DIP package in anti-static packaging for preservation.

## 🖨️ 3D Printed parts
The following parts help facilitate the modifications. These are:
* [Power button with Display cutout](./assets/models/power-cap)
* [ADB Port with switch and USB-C cutout](./assets/models/usb)
* [ADB Port with EC11 cutout](./assets/models/encoder)
* [EC11 encoder knob]((./assets/models/encoder))

These files are provided in STEP and 3MF formats.  
STEP allows for accurate modification in CAD software.  
3MF is designed to be more accessible for 3D printing.