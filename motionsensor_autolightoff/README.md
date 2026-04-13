# Motion Sensor Auto Light Off Blueprint
*A Home Assistant automation blueprint that turns a light on when motion is detected and automatically turns it off after a configurable period of no motion.*

---

## What it does
This blueprint monitors a motion or occupancy sensor and controls a light or switch accordingly:

| Event | Action |
| ----- | ------ |
| **Motion detected** | Turns on the target light or switch |
| **No motion** for X seconds | Turns off the target light or switch |

The automation runs in **restart** mode — any new motion while the timer is counting down resets the delay, so the light stays on as long as there is activity.

---

## Prerequisites
* A **motion** or **occupancy** binary sensor integrated into Home Assistant
* A **light** or **switch** entity to control

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2Fmain%2Fmotionsensor_autolightoff%2Fmotionsensor_autolightoff.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Adjust the no-motion delay** — default is 60 seconds, but you can set any value from 1 second upward.
* **Use with any binary sensor** — supports both `motion` and `occupancy` device classes, covering PIR sensors, mmWave radar sensors, and more.
* **Target lights or switches** — works with either `light` or `switch` domain entities, so you can control smart bulbs, relay modules, or plug-in switches.

---

## License

MIT
