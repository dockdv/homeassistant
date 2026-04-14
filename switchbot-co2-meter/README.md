# SwitchBot CO2 Meter Blueprint
*A Home Assistant automation blueprint that triggers actions based on CO2 ppm levels reported by a SwitchBot CO2 sensor.*

---

## What it does
This blueprint divides CO2 readings into three zones and runs a different action for each:

| Zone | Condition | Air quality |
| ---- | --------- | ----------- |
| **Above high** | CO2 > high threshold (default 1400 ppm) | Poor |
| **Within range** | Low threshold ≤ CO2 ≤ high threshold | Acceptable |
| **Below low** | CO2 < low threshold (default 1000 ppm) | Good |

### Trigger modes

| Mode | Behaviour |
| ---- | --------- |
| **value_change** (default) | Evaluates the zone whenever the sensor reports a new value |
| **periodic** | Evaluates the zone at a fixed interval (default 30 seconds, configurable from 5 to 3600 seconds) regardless of sensor updates |

### Time-of-day periods

The blueprint supports up to **4 time periods**, each with its own set of zone actions. This lets you respond differently at different times of day — for example, send a notification during the day but stay silent at night.

Each period has:
* An **enable toggle** (only enabled periods are considered)
* A **start time** (when the period begins)
* Three **zone actions** (Poor, Acceptable, Good)

The currently active period is whichever enabled period has the most recent start time, including wrap-around across midnight. For example, with only Period 1 (07:00) and Period 4 (22:00) enabled, Period 4 is active from 22:00 through 06:59 (next day), and Period 1 is active from 07:00 through 21:59.

Edge cases:
* **1 enabled period** — that period covers all 24 hours
* **0 enabled periods** — nothing runs

---

## Prerequisites
* A **SwitchBot CO2 sensor** (or any sensor with `device_class: carbon_dioxide`) integrated into Home Assistant
* Entities you want to control (lights, switches, fans, notification services, etc.)

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2Fmain%2Fswitchbot-co2-meter%2Fswitchbot-co2-meter.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Choose your trigger mode** — use "value_change" for immediate response or "periodic" to check at a fixed interval (configurable from 5 to 3600 seconds).
* **Enable multiple periods** to vary behaviour across the day (e.g. quieter actions at night).
* **Adjust thresholds** to match your environment.
* **Stack multiple actions** in each zone — e.g. turn on a fan *and* send a mobile notification when CO2 is high.
* **Use with any CO2 sensor** — not limited to SwitchBot; any sensor reporting `device_class: carbon_dioxide` will work.
* **Add hysteresis manually** by setting the high and low thresholds further apart to avoid rapid toggling near a boundary.

---

## License

MIT
