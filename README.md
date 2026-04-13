# Home Assistant Blueprints

A collection of Home Assistant automation blueprints for Zigbee remotes, smart plugs, IR blasters, motion sensors, and air quality monitors.

## Blueprints

### LoraTap TS0043 3-Button Remote

This blueprint provides fully customizable button mappings for the LoraTap/Tuya TS0043 3-button Zigbee remote via Zigbee2MQTT MQTT device triggers. Each of the three buttons supports single press, double press, and hold actions, giving you nine independently configurable actions in total. The automation runs in queued mode, ensuring rapid button presses are never lost.

### Zigbee Pair

This blueprint automates the power-cycling sequence needed to trigger pairing or factory-reset mode on IKEA/TRADFRI Zigbee bulbs. It toggles a smart plug through a configurable number of OFF/ON cycles with adjustable timing for each phase. The automation uses a dummy trigger so it cannot fire accidentally — you run it manually via the Home Assistant "Run" button or by calling `automation.trigger`.

### Fan Control

This blueprint maps up to four button actions from a MOES/Tuya TS004F Zigbee remote to base-64 encoded IR commands sent through an IR blaster's text entity. It ships with default IR codes for Westinghouse ceiling-fan receivers (off, speed 1, speed 2, speed 3), but both the remote action subtypes and IR payloads are fully remappable to suit any IR-controlled device.

### Motion Sensor Auto Light Off

This blueprint turns a light or switch on when a motion or occupancy sensor detects activity, then automatically turns it off after a configurable period of no motion. It supports both `motion` and `occupancy` device classes and can target either `light` or `switch` entities. The automation runs in restart mode, so any new motion resets the off timer.

### Sonoff CO2 Meter

This blueprint monitors a Sonoff CO2 sensor and triggers different actions based on three configurable zones. When CO2 rises above a high threshold (default 1000 ppm), it runs one action such as turning on ventilation or a warning light. When CO2 drops below a low threshold (default 600 ppm), it runs a second action. When CO2 returns to the normal range between the two thresholds, it runs a third recovery action, allowing you to automate the full cycle of air quality response.
