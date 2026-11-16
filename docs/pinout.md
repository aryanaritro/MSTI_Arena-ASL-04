# Pinout and Wiring

## Components

- 1 × Arduino Uno
- 4 × LEDs
- 4 × 220 Ω resistors
- Jumper wires

## Pin Assignment

| LED | Arduino pin | ATmega328P port bit |
|---|---:|---|
| LED 1 | D4 | PD4 |
| LED 2 | D5 | PD5 |
| LED 3 | D6 | PD6 |
| LED 4 | D7 | PD7 |

## Wiring

For each LED, connect the assigned Arduino pin through a 220 Ω resistor to the LED anode (+). Connect the LED cathode (−) to Arduino GND.

```text
D4 ── 220 Ω ── LED 1 ── GND
D5 ── 220 Ω ── LED 2 ── GND
D6 ── 220 Ω ── LED 3 ── GND
D7 ── 220 Ω ── LED 4 ── GND
```

Use a separate resistor for each LED.

## Serial Monitor

Open the Wokwi Serial Monitor at **9600 baud**. Send `f` to make scanning faster or `s` to make it slower.

Circuit screenshot: `../evidence/simulation/circuit-overview.png`.
