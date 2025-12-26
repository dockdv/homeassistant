# Zigbee Bulb Pairing Mode via Smart Plug (Manual-Run Home Assistant Blueprint)

This repo contains a **Home Assistant automation blueprint** that power-cycles a **smart plug** to help put a **Zigbee bulb** into **pairing/reset mode**.

It’s commonly used for **IKEA TRÅDFRI** bulbs (which often enter pairing/reset after repeated power toggles), but the same idea may work with **other Zigbee bulbs** that use a similar “power toggle” reset procedure.

> ⚠️ Important: Different bulbs/brands may require different counts/timings (or a completely different reset method).
> Treat the defaults as a starting point and adjust as needed.

---

## What this does

- You select a **smart plug** entity that powers the bulb.
- You configure:
  - **Number of cycles** (OFF → ON toggles)
  - **OFF duration**
  - **ON duration**
- You **run the automation manually** (no automatic triggers).

The blueprint includes a **dummy trigger** so it won’t start on its own.

---

## Recommended defaults (good starting point)

For many bulbs (including IKEA in many setups):

- **Cycles:** `6`
- **OFF duration:** `1.0 s` (or `800 ms`)
- **ON duration:** `1.0 s` (or `800 ms`)

If it doesn’t work reliably:
- Increase **OFF** duration to `1.5–2.0 s`
- Keep **ON** around `0.8–1.0 s`

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/dockdv/homeassistant/blob/main/ZigbeePair/zigbee-pair.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>


---
## License

MIT
