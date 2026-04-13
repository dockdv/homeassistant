# SwitchBot CO2 Meter Blueprint
*A Home Assistant automation blueprint that triggers actions based on CO2 ppm levels reported by a SwitchBot CO2 sensor.*

---

## What it does
This blueprint divides CO2 readings into three zones and runs a different action for each:

| Zone | Condition | Air quality |
| ---- | --------- | ----------- |
| **Above high** | CO2 > high threshold (default 1000 ppm) | Poor |
| **Within range** | Low threshold ≤ CO2 ≤ high threshold | Acceptable |
| **Below low** | CO2 < low threshold (default 1400 ppm) | Good |


---

## Prerequisites
* A **SwitchBot CO2 sensor** (or any sensor with `device_class: carbon_dioxide`) integrated into Home Assistant
* Entities you want to control (lights, switches, fans, notification services, etc.)

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2Fmain%2Fswitchbot-co2-meter%2Fswitchbot-co2-meter.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Adjust thresholds** to match your environment.
* **Stack multiple actions** in each zone — e.g. turn on a fan *and* send a mobile notification when CO2 is high.
* **Use with any CO2 sensor** — not limited to SwitchBot; any sensor reporting `device_class: carbon_dioxide` will work.
* **Add hysteresis manually** by setting the high and low thresholds further apart to avoid rapid toggling near a boundary.

---

## License

MIT
