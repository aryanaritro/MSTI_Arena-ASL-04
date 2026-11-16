# System Architecture

## Overview

The Arduino Uno runs a four-LED scanner. It repeatedly lights LEDs in a forward-and-return sequence. The user can adjust the delay at runtime through the Serial Monitor.

## Functional Blocks

1. **GPIO configuration:** `DDRD` configures Arduino pins D4–D7 as outputs.
2. **LED scanner:** `PORTD` changes the output states to light one LED at a time.
3. **Serial speed control:** `Serial.read()` receives commands; the delay is updated and reported using `Serial.println()`.

## Register Mapping

| Arduino pin | AVR port bit |
|---|---|
| D4 | PD4 |
| D5 | PD5 |
| D6 | PD6 |
| D7 | PD7 |

`DDRD |= 0b11110000` sets PD4–PD7 as outputs while leaving the other DDRD bits unchanged. The firmware clears the D4–D7 PORTD bits before setting the selected LED bit.

## Scan Sequence

`D4 → D5 → D6 → D7 → D6 → D5 → repeat`

## Serial Control

Serial baud rate: 9600.

- `f` / `F`: subtract 50 ms from the delay.
- `s` / `S`: add 50 ms to the delay.
- Initial delay: 300 ms.
- Minimum delay: 50 ms.
- Maximum delay: 1000 ms.

After a recognized command, the updated delay is printed as `New Speed: X ms`.

## Block Diagram

```text
Serial Monitor (9600 baud)
          |
       f / s
          v
  Serial Speed Logic
          |
       delay value
          v
Arduino Uno / ATmega328P
   |                 |
 DDRD              PORTD
   |                 |
D4-D7 outputs --> Four LEDs
```

## Design Notes

- LED GPIO is controlled using AVR registers, not `pinMode()` or `digitalWrite()`.
- The Serial interface uses the Arduino hardware serial API.
- Each LED has an individual current-limiting resistor.
