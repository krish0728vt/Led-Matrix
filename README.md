# RGB LED Magic Cube

## Project Owner

**Name:** Krish Shah
**Virginia Tech Email:** [krish0728@vt.edu](mailto:krish0728@vt.edu)

## Project Overview

The RGB LED Magic Cube is a custom-built interactive lighting display made from six 50 mm × 50 mm PCB faces. Each face contains a 5 × 5 matrix of individually addressable WS2812B RGB LEDs, giving the completed cube a total of **150 LEDs**.

A single **ESP32-C3** located inside the base controls the entire cube. The six faces are connected as one continuous LED data chain, allowing every LED to be controlled individually while keeping the electronics and wiring hidden from view.

The cube can display solid colors and animated effects including rainbows, chases, sparkles, waves, and wipes. It can also be controlled wirelessly from a custom browser interface using **Bluetooth Low Energy (BLE)**. From the website, the user can turn the cube on or off, select effects, choose colors, and adjust brightness and animation speed.

The project combines custom PCB design, embedded programming, Bluetooth communication, web development, and 3D-printed mechanical parts into one complete system.

## What I Hope to Learn

This project gave me practical experience with:

* PCB design and manufacturing
* ESP32 embedded programming
* Addressable RGB LED control
* Bluetooth Low Energy communication
* Web-based hardware control
* Power distribution and electronics testing
* CAD and 3D printing
* Integrating hardware, firmware, and software into one finished product

## Design and Implementation

### LED Cube

The cube consists of **six custom PCB faces**, each containing 25 WS2812B LEDs arranged in a 5 × 5 grid.

```text
25 LEDs per face × 6 faces = 150 LEDs
```

The boards are connected in one continuous data chain:

```text
ESP32-C3
   ↓
Face 1 → Face 2 → Face 3 → Face 4 → Face 5 → Face 6
```

This allows one ESP32 GPIO pin to control all 150 LEDs individually.

### Controller

An **ESP32-C3** located inside the base runs the cube firmware.

```text
Controller: ESP32-C3
LED Data Pin: GPIO 4
Total LEDs: 150
```

The firmware uses the **Adafruit NeoPixel library** and supports several lighting effects including:

* Solid Color
* Rainbow
* Chase
* Sparkle
* Pixel
* Wave
* Wipe
* Face Effects

### Bluetooth Web Controller

The ESP32-C3 also acts as a Bluetooth Low Energy device.

A custom web controller connects directly to the cube through Web Bluetooth and allows the user to:

* Turn the cube on/off
* Select animations
* Choose RGB colors
* Adjust brightness
* Adjust animation speed

This allows the cube to be controlled from a compatible computer or phone without requiring a dedicated mobile application.

### Mechanical Design

The electronics are housed inside a custom **3D-printed base** that supports the cube while hiding the ESP32, power connections, and wiring.

The PCB connections are located behind the LED faces so the finished cube maintains a clean appearance.

## Bill of Materials

| Item                    |    Quantity | Estimated Cost | Link      |
| ----------------------- | ----------: | -------------: | --------- |
| WS2812B RGB LEDs        |         150 |              — | LCSC      |
| Custom LED PCBs         |           6 |              — | JLCPCB    |
| ESP32-C3                |           1 |              — | Digikey   |
| 100 nF Capacitors       |         150 |              — | LCSC      |
| 5 V Power Supply        |           1 |              — | Digikey   |
| DC Barrel Jack          |           1 |              — | LCSC      |
| 3D-Printed Base         |           1 |              — | Custom    |
| PCB/Mechanical Hardware | As Required |              — | Custom    |

**Estimated Total Cost:** Final project cost varies based on PCB manufacturing and component sourcing.

## Timeline and Milestones

| Milestone               | Status   |
| ----------------------- | -------- |
| Project planning        | Complete |
| Circuit and PCB design  | Complete |
| PCB manufacturing       | Complete |
| ESP32 firmware          | Complete |
| Bluetooth communication | Complete |
| Web controller          | Complete |
| Mechanical design       | Complete |
| Cube assembly           | Complete |
| Hardware testing        | Complete |
| Final system testing    | Complete |
| Project completion      | Complete |

## Progress Log

### August–September 2026

Designed the six LED PCB faces and created a 3 × 2 manufacturing panel containing all six sides of the cube.

Developed the ESP32-C3 firmware and implemented the LED effects.

Created a browser-based Bluetooth controller for selecting colors, effects, brightness, and animation speed.

Designed and 3D printed the base and cube support structure.

Assembled the complete cube, connected all 150 LEDs, and tested the hardware, firmware, Bluetooth communication, and web interface as a complete system.

## Project Files

The repository contains the main files required to reproduce or modify the project, including:

* ESP32-C3 firmware
* KiCad schematic and PCB files
* PCB manufacturing files
* Web controller source code
* CAD and 3D-printing files
* Project documentation

## Useful Links

**ESP32-C3 Documentation**
[Espressif ESP32-C3 Documentation](https://docs.espressif.com/projects/esp-idf/en/latest/esp32c3/?utm_source=chatgpt.com)

**Adafruit NeoPixel Library**
[Adafruit NeoPixel GitHub Repository](https://github.com/adafruit/Adafruit_NeoPixel?utm_source=chatgpt.com)

**KiCad**
[KiCad Official Website](https://www.kicad.org/?utm_source=chatgpt.com)

**KiCad Documentation**
[KiCad Documentation](https://docs.kicad.org/?utm_source=chatgpt.com)

**JLCPCB**
[JLCPCB PCB Manufacturing](https://jlcpcb.com/?utm_source=chatgpt.com)

**Web Bluetooth API**
[MDN Web Bluetooth Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Web_Bluetooth_API?utm_source=chatgpt.com)

**Project Repository**
[LED Cube GitHub Repository](https://github.com/krish0728vt/Led_Cube?utm_source=chatgpt.com)

## Project Image

The project cover image is stored in the root of the repository as:

```text
hero.png
```

The image shows the completed RGB LED Magic Cube and is used as the project cover image on the AMP Lab website.
