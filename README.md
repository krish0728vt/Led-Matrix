# RGB LED Magic Cube

## Project Owner

**Name:** Krish Shah
**Virginia Tech Email:** [krish0728@vt.edu](mailto:krish0728@vt.edu)

## Project Overview

The RGB LED Magic Cube is a custom lighting project made from six 50 mm × 50 mm PCB faces. Each face contains a 5 × 5 matrix of WS2812B individually addressable RGB LEDs, giving the complete cube a total of 150 LEDs.

The entire cube is controlled by a single ESP32-C3 located inside a 3D-printed base. LED data travels through all six faces as one continuous chain, allowing the ESP32 to control every LED individually.

The goal is to create a compact, clean-looking RGB display capable of showing solid colors, animated effects, waves, chases, wipes, sparkles, and other lighting patterns. Electrical connections are kept behind the LED faces so that only the LEDs are visible from the outside.

The cube can also be controlled wirelessly through a browser-based Bluetooth Low Energy interface, allowing the user to change colors, brightness, animation speed, and lighting effects.

The design uses six LED face PCBs with 25 LEDs each, resulting in 150 individually addressable LEDs.

## What I Hope to Learn

Through this project, I hope to gain experience in several areas of electrical and computer engineering, including:

* Designing custom PCBs in KiCad
* Working with addressable RGB LEDs
* Power distribution for high-current LED systems
* Designing and debugging embedded hardware
* Programming the ESP32-C3 using Arduino/C++
* Bluetooth Low Energy communication
* Developing a browser-based hardware control interface
* Designing mechanical components using CAD
* 3D printing an electronics enclosure
* Designing connectors between multiple PCBs
* Testing and debugging a complete embedded system
* Integrating hardware, firmware, mechanical design, and software into one finished product

## Design and Implementation

### System Architecture

The project consists of four main sections:

1. ESP32-C3 controller
2. Six LED face PCBs
3. 5 V power system
4. 3D-printed base and cube support

The LEDs operate as one continuous addressable chain:

```text
ESP32-C3
   |
   v
Face 1
   |
   v
Face 2
   |
   v
Face 3
   |
   v
Face 4
   |
   v
Face 5
   |
   v
Face 6
```

Only the first face receives data directly from the ESP32. Each face passes its LED data output to the input of the next face. This allows the firmware to treat the entire cube as one strip containing 150 LEDs.

### LED Face PCB

Each cube face is approximately 50 mm × 50 mm and contains:

* 25 WS2812B RGB LEDs
* 5 × 5 LED layout
* Decoupling capacitors
* 5 V power rail
* Ground rail
* Data input
* Data output
* Rear connection pads

The front of each PCB is kept visually clean and primarily contains the LEDs. Power and signal connections between faces are made from the rear of the boards.

### Controller

The cube is controlled using one ESP32-C3.

The current firmware configuration uses:

```cpp
NUM_LEDS = 150
DATA_PIN = GPIO 4
```

The ESP32 controls all six faces through a single LED data output.

### Firmware

The firmware uses the Adafruit NeoPixel library to control the LEDs.

Current lighting modes include:

* FACE
* SOLID
* RAINBOW
* CHASE
* PIXEL
* SPARKLE
* TEST
* WAVE
* WIPE

Brightness and animation speed can also be adjusted.

Effects such as CHASE, PIXEL, WAVE, and WIPE can use a user-selected RGB color.

### Bluetooth Control

The ESP32-C3 communicates with a browser-based controller using Bluetooth Low Energy.

The interface allows the user to:

* Turn the cube on and off
* Select lighting effects
* Choose RGB colors
* Change brightness
* Change animation speed
* Synchronize the current cube state

A custom circular HSV color picker is used to select colors.

The browser sends commands to the ESP32 using a simple BLE command protocol.

Example commands include:

```text
P
M:<MODE>
C:R,G,B
B:<BRIGHTNESS>
S:<SPEED>
GET
```

### Power System

The cube requires a regulated 5 V supply.

The theoretical maximum LED current is:

```text
150 LEDs × 60 mA = 9 A
```

This represents an extreme case where every LED displays full-brightness white. Normal animations consume significantly less current, and brightness is limited in software.

The LED power supply is separate from the ESP32 power path, while all parts of the system share a common ground.

### PCB Manufacturing

The six cube faces are produced using a panelized PCB design.

The current panel arrangement uses:

```text
3 × 2 LED face panel
```

One manufactured panel therefore produces all six cube faces.

V-cuts are used to separate the individual boards.

### Mechanical Design

A custom 3D-printed base supports the cube and hides the controller, wiring, and power connections.

A separate cube support stand is used to position the cube above the base.

The mechanical design is intended to keep the visible cube clean while hiding the majority of the electronics.

## Bill of Materials

| Item                         |    Quantity | Estimated Cost | Link       |
| ---------------------------- | ----------: | -------------: | ---------- |
| WS2812B RGB LEDs             |         150 |            TBD | TBD        |
| LED Face PCB                 |           6 |            TBD | JLCPCB     |
| ESP32-C3 Development Board   |           1 |            TBD | TBD        |
| 100 nF Decoupling Capacitors |         150 |            TBD | TBD        |
| Data Resistor                |           1 |            TBD | TBD        |
| 5 V Power Supply             |           1 |            TBD | TBD        |
| DC Barrel Jack               |           1 |            TBD | TBD        |
| Power Switch                 |           1 |            TBD | TBD        |
| PCB Connectors / Pads        | As required |            TBD | TBD        |
| 3D-Printed Base              |           1 |            TBD | Custom CAD |
| 3D-Printed Cube Support      |           1 |            TBD | Custom CAD |
| M3 Hardware                  | As required |            TBD | TBD        |

**Estimated Total Cost:** TBD

## Timeline and Milestones

| Milestone                   | Target Date    | Status      |
| --------------------------- | -------------- | ----------- |
| Project planning            | August 2026    | Complete    |
| LED face schematic          | August 2026    | Complete    |
| LED face PCB layout         | August 2026    | Complete    |
| PCB panelization            | September 2026 | Complete    |
| ESP32 firmware              | September 2026 | Complete    |
| BLE communication           | September 2026 | Complete    |
| Browser controller          | September 2026 | Complete    |
| Mechanical base design      | September 2026 | Complete    |
| PCB manufacturing           | September 2026 | In Progress |
| Cube assembly               | TBD            | Not Started |
| Full hardware testing       | TBD            | Not Started |
| Final animations and tuning | TBD            | In Progress |
| Project completion          | TBD            | In Progress |

## Progress Log

### 2026-08

The initial project architecture was developed. The cube was designed around six 5 × 5 WS2812B LED faces controlled by a single ESP32.

The decision was made to connect all 150 LEDs as one continuous data chain instead of placing a microcontroller on every face.

Initial PCB schematics and layouts were created.

### 2026-09

The LED face PCB design was completed and prepared for manufacturing.

The six faces were panelized into a 3 × 2 V-cut panel so that one manufactured panel can provide all six cube faces.

The ESP32-C3 firmware was developed and tested with multiple lighting modes.

Bluetooth Low Energy communication between the ESP32 and a browser was implemented.

A web-based control interface was created with controls for power, effects, colors, brightness, and speed.

A circular HSV color picker was added to improve color selection.

BLE reconnect behavior and state synchronization were implemented and tested.

WAVE and WIPE effects were updated so that they use the RGB color selected by the user.

Mechanical parts including the base and cube support were designed for 3D printing.

### Next Steps

The next major steps are:

* Manufacture the LED PCB panel
* Assemble all six LED faces
* Test every face individually
* Connect all six faces into one data chain
* Test all 150 LEDs simultaneously
* Verify voltage drop and current consumption
* Assemble the cube mechanically
* Install the ESP32 and power system inside the base
* Perform complete system testing
* Record the final demonstration video

## Project Files

The repository is organized to contain the major hardware, firmware, software, and mechanical files used in the project.

```text
LED_Cube/
│
├── firmware/
│   └── led_cube_controller/
│
├── hardware/
│   ├── schematic/
│   └── pcb/
│
├── cad/
│   ├── base/
│   └── cube_support/
│
├── web/
│   ├── index.html
│   ├── style.css
│   └── script.js
│
├── docs/
│
├── hero.png
│
└── README.md
```

Important project files include:

* ESP32-C3 firmware
* KiCad schematic
* KiCad PCB layout
* Panelized PCB files
* Manufacturing Gerber files
* Base CAD files
* Cube support CAD files
* Browser controller HTML/CSS/JavaScript
* Test documentation
* Project images and demonstration media

## Useful Links

* ESP32-C3 Documentation
* WS2812B Datasheet
* Adafruit NeoPixel Library
* KiCad Documentation
* JLCPCB PCB Manufacturing
* Web Bluetooth API Documentation
* GitHub Project Repository

## Project Image

The repository should contain a project cover image named:

```text
hero.png
```

This image should show the assembled LED Magic Cube or a clear render of the final design.

The filename must remain exactly:

```text
hero.png
```

because this image is used as the project cover image on the AMP Lab website.
