# SwitchBot CO2 Meter Indicator Light Blueprint
*A Home Assistant automation blueprint that drives a single RGB light to visually indicate CO2 air quality, with brightness adjusted by ambient light.*

---

## What it does
This blueprint turns one light into a CO2 quality indicator. The colour reflects the current CO2 zone, and the brightness switches between two levels based on an ambient light sensor.

### Colours per zone

| Zone | Condition | Colour |
| ---- | --------- | ------ |
| **Poor** | CO2 > high threshold (default 1400 ppm) | 🔴 Red |
| **Acceptable** | Low threshold ≤ CO2 ≤ high threshold | 🟡 Amber |
| **Good** | CO2 < low threshold (default 1000 ppm) | 🟢 Green |

Colours are hardcoded in the blueprint.

### Brightness

An ambient light sensor decides which brightness level is applied:

| Ambient state | Condition | Brightness |
| ------------- | --------- | ---------- |
| **Bright** | Light ≥ threshold (default 50 lx) | Configurable (default 100%) |
| **Dim** | Light < threshold | Configurable (default 20%) |

### Trigger modes

| Mode | Behaviour |
| ---- | --------- |
| **value_change** (default) | Updates the light whenever the CO2 sensor reports a new value |
| **periodic** | Updates the light at a fixed interval (default 30 seconds, configurable from 5 to 3600 seconds) |

---

## Prerequisites
* A **SwitchBot CO2 sensor** (or any sensor with `device_class: carbon_dioxide`)
* An **illuminance sensor** (any sensor with `device_class: illuminance`)
* An **RGB-capable light** entity

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2Fmain%2Fswitchbot-co2-meter-light-sensor%2Fswitchbot-co2-meter-light-sensor.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Choose your trigger mode** — use "value_change" for immediate response or "periodic" for fixed-interval updates.
* **Tune the light threshold** — typical indoor levels range from ~1 lx (dark) to ~500 lx (well-lit).
* **Set the two brightness levels** (bright / dim) to suit your room.
* **Adjust CO2 thresholds** to match your environment.

---

## License

MIT
