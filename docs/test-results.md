# Test Results

## Test Environment

| Item | Configuration |
|---|---|
| Simulator | Wokwi |
| Board | Arduino Uno |
| Microcontroller | ATmega328P |
| LED pins | D4, D5, D6, D7 |
| Serial baud rate | 9600 |

## Verified Tests

| Test | Expected behavior | Result |
|---|---|---|
| Forward scan | D4 → D5 → D6 → D7 | PASS |
| Reverse scan | D6 → D5, then repeat | PASS |
| DDRD configuration | D4–D7 configured as outputs | PASS |
| PORTD control | LED states controlled through PORTD | PASS |
| Faster command | `f` decreases delay by 50 ms | PASS |
| Slower command | `s` increases delay by 50 ms | PASS |
| Serial feedback | Prints `New Speed: X ms` | PASS |

## Observed Serial Output

The user verified speed changes in Wokwi. Observed output included:

```text
New Speed: 250 ms
New Speed: 300 ms
New Speed: 350 ms
New Speed: 400 ms
New Speed: 350 ms
New Speed: 300 ms
New Speed: 250 ms
New Speed: 200 ms
New Speed: 150 ms
New Speed: 200 ms
New Speed: 250 ms
New Speed: 300 ms
```

This demonstrates both faster and slower adjustments.

## Evidence

- `circuit-overview.png` — complete circuit.
- `scanner-operation.png` — LEDs during scanning.
- `serial-speed-control.png` — Serial Monitor commands and speed feedback.

The tests were performed in Wokwi. No physical Arduino Uno hardware test is claimed.
