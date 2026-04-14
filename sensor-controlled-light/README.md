# Sensor-Controlled Light Blueprint
*A Home Assistant automation blueprint that linearly maps a light sensor reading to a bulb's brightness.*

---

## What it does
Given a sensor range (in lux) and a brightness range (in %), this blueprint computes the bulb brightness using linear interpolation:

```
brightness = brightness_min + ratio × (brightness_max − brightness_min)
ratio       = (sensor_value − sensor_min) / (sensor_max − sensor_min)
```

The ratio and the final brightness are both clamped so that sensor values outside the configured range simply pin the bulb at the nearest configured brightness.

### Example

| Sensor min | Sensor max | Brightness min | Brightness max | At 0 lx | At 250 lx | At 500 lx |
| ---------- | ---------- | -------------- | -------------- | ------- | --------- | --------- |
| 0 | 500 | 10% | 100% | 10% | 55% | 100% |
| 0 | 500 | 100% | 10% *(inverted)* | 100% | 55% | 10% |

To make the bulb brighten as the room gets darker, set **brightness_min > brightness_max** (inverted mapping).

### Trigger modes

| Mode | Behaviour |
| ---- | --------- |
| **value_change** (default) | Updates the light whenever the sensor reports a new value |
| **periodic** | Updates the light at a fixed interval (default 30 seconds, configurable from 5 to 3600 seconds) |

---

## Prerequisites
* An **illuminance sensor** (any sensor with `device_class: illuminance`)
* A **dimmable light** entity

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2Fmain%2Fsensor-controlled-light%2Fsensor-controlled-light.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Pick sensor_min / sensor_max** to match realistic lux readings for your space.
* **Pick brightness_min / brightness_max** to set the bulb's output range.
* **Invert the mapping** by setting brightness_min higher than brightness_max — useful if you want the bulb to compensate for darkness.
* **Choose your trigger mode** — use "value_change" for immediate response or "periodic" for fixed-interval updates.

---

## License

MIT
