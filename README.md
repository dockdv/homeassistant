# Home Assistant Blueprints

A collection of Home Assistant automation blueprints.

## Blueprints

### LoraTap TS0043 3-Button Remote

This blueprint provides fully customizable button mappings for the LoraTap/Tuya TS0043 3-button Zigbee remote via Zigbee2MQTT MQTT device triggers. Each of the three buttons supports single press, double press, and hold actions, giving you nine independently configurable actions in total. The automation runs in queued mode, ensuring rapid button presses are never lost.

### Zigbee Pair

This blueprint automates the power-cycling sequence needed to trigger pairing or factory-reset mode on IKEA/TRADFRI Zigbee bulbs. It toggles a smart plug through a configurable number of OFF/ON cycles with adjustable timing for each phase. The automation uses a dummy trigger so it cannot fire accidentally — you run it manually via the Home Assistant "Run" button or by calling `automation.trigger`.

### Fan Control

This blueprint maps up to four button actions from a MOES/Tuya TS004F Zigbee remote to base-64 encoded IR commands sent through an IR blaster's text entity. It ships with default IR codes for Westinghouse ceiling-fan receivers (off, speed 1, speed 2, speed 3), but both the remote action subtypes and IR payloads are fully remappable to suit any IR-controlled device.

### Motion Sensor Auto Light Off

This blueprint turns a light or switch on when a motion or occupancy sensor detects activity, then automatically turns it off after a configurable period of no motion. It supports both `motion` and `occupancy` device classes and can target either `light` or `switch` entities. The automation runs in restart mode, so any new motion resets the off timer.

### SwitchBot CO2 Meter

This blueprint monitors a SwitchBot CO2 sensor and triggers different actions based on three air quality zones. When CO2 rises above a high threshold (default 1000 ppm), air quality is poor and it runs one action such as turning on ventilation or a warning light. When CO2 drops below a low threshold (default 1400 ppm), air quality is good and it runs a second action. When CO2 is between the two thresholds, air quality is acceptable and it runs a third action, allowing you to automate the full cycle of air quality response. The blueprint also supports up to four configurable time-of-day periods, so you can vary the actions for each zone across the day.

### SwitchBot CO2 Meter Indicator Light

A simpler, purpose-built variant that turns a single RGB light into a CO2 quality indicator. The light colour reflects the current zone (red for Poor, amber for Acceptable, green for Good — hardcoded), and an illuminance sensor picks between two configurable brightness levels so the indicator is visible during the day but dim at night.

### Sensor-Controlled Light

This blueprint linearly maps an illuminance sensor reading to a bulb's brightness. You configure a sensor range (min/max lux) and a brightness range (min/max %), and the blueprint interpolates the bulb's brightness from the current sensor value. Values outside the sensor range are clamped to the nearest configured brightness. By setting the minimum brightness higher than the maximum, the mapping can be inverted so the bulb brightens as the room gets darker.
