# SwitchBot CO2 Meter with Light Sensor Blueprint
*A Home Assistant automation blueprint that triggers actions based on CO2 ppm levels, with a light sensor deciding which set of actions to run.*

---

## What it does
This blueprint divides CO2 readings into three zones and runs a different action for each:

| Zone | Condition | Air quality |
| ---- | --------- | ----------- |
| **Above high** | CO2 > high threshold (default 1400 ppm) | Poor |
| **Within range** | Low threshold ≤ CO2 ≤ high threshold | Acceptable |
| **Below low** | CO2 < low threshold (default 1000 ppm) | Good |

### Light-based action sets

Instead of using fixed time-of-day periods, this blueprint uses an **illuminance sensor** to pick between two action sets:

| Light state | Condition | Typical scenario |
| ----------- | --------- | ---------------- |
| **Bright** | Light ≥ threshold (default 50 lx) | Daytime or lights on |
| **Dim** | Light < threshold | Nighttime or lights off |

Each light state has its own three zone actions, giving six action selectors in total. For example, during the day you might turn on a fan and send a notification when CO2 is high; at night you might only turn on the fan silently.

### Trigger modes

| Mode | Behaviour |
| ---- | --------- |
| **value_change** (default) | Evaluates the zone whenever the CO2 sensor reports a new value |
| **periodic** | Evaluates the zone at a fixed interval (default 30 seconds, configurable from 5 to 3600 seconds) regardless of sensor updates |

---

## Prerequisites
* A **SwitchBot CO2 sensor** (or any sensor with `device_class: carbon_dioxide`) integrated into Home Assistant
* An **illuminance sensor** (any sensor with `device_class: illuminance`)
* Entities you want to control (lights, switches, fans, notification services, etc.)

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2Fmain%2Fswitchbot-co2-meter-light-sensor%2Fswitchbot-co2-meter-light-sensor.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Choose your trigger mode** — use "value_change" for immediate response or "periodic" to check at a fixed interval (configurable from 5 to 3600 seconds).
* **Tune the light threshold** to match your sensor and room — typical indoor ambient levels range from ~1 lx (dark) to ~500 lx (well-lit).
* **Adjust CO2 thresholds** to match your environment.
* **Stack multiple actions** in each slot — e.g. turn on a fan *and* send a mobile notification when CO2 is high and the room is bright.
* **Use with any sensors** — not limited to SwitchBot; any CO2 sensor with `device_class: carbon_dioxide` and any illuminance sensor will work.

---

## License

MIT
