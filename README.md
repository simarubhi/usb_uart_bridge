# USB to UART Bridge

## Overview

In order to debug and flash custom microcontroller boards for future projects, I designed a USB to UART bridge with the CP2102N chip in KiCad. Parts are currently in transit and assembly will begin soon!

Total Cost Per Board: ~$5.21<br>
Equivalent Board On Market: $5.59

Not only is my price per board cheaper than buying a prebuilt board, but it also offers proper overvoltage protection and LED indicators.

## Schematic

![Schematic](/Docs/schematic.jpg)

## PCB Layout

![Layout](/Docs/layout.jpg)

<br>

![3D View](/Docs/3d.jpg)

## Update (Debug Notes)

After some debugging (and re-reading the CP2102N datasheet), I realized I made a pin-mapping mistake on the USB VBUS side:

- I accidentally treated **pins 7 and 8 as VBUS**
- **Pin 7 should be VREGIN**
- **Pin 8 should be VBUS**
- On top of that, **VBUS needed a voltage divider** (for the VBUS sense input)

I ended up cutting traces and soldering in the fixes. After the rework, the bridge will _sometimes_ be recognized by the computer when plugged in, but it quickly disconnects shortly after.

Possible causes:

- a bad/weak solder joint from the rework
- the CP2102N being damaged during assembly or rework

At this point it’s not worth spending more time trying to salvage this exact board (especially since the CP2102N price has gone up since the original part selection). In the future, I plan to make a proper debug that includes things like push buttons, LEDs, STM32 flashing support, UART headers, and other useful test features to make troubleshooting a lot easier for future projects.

![Update](/Docs/update.jpg)
