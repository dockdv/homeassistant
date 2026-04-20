# Bose TV Speaker Remote (IR) Blueprint
*A Home Assistant automation blueprint that sends Bose TV Speaker IR commands through an IR blaster's text entity when a Zigbee remote button is pressed.*

---

## What it does
This blueprint maps four Zigbee remote button presses to four Bose TV Speaker IR commands. Each command has its own **remote device + button subtype + IR code** triplet, so you can drive all four from a single 4-button remote, from four single-button remotes, or from any mix in between.

When a configured button is pressed, the matching base-64 IR payload is written to the IR blaster's `text` entity and sent.

### IR codes

| Command | IR code (base-64) | Implemented |
| ------- | ----------------- | :---------: |
| **On/Off** | `CfEDwgUcAvABHALAB8AL4AcPBfAB8AHCBYADwAHADwXxxvEDwgXgASPAAUATA8IF8AHAAQnCBRwC8AHwAcIFgAPAAQfCBfABwgUcAg==` | ✅ |
| **Volume Up** | `B/gDwQUOAtIB4A0DQBvgEwPANwP4xvgDQCfAD+AFBwHSAUAbAsEFbCADQAfgCQMB0gGAAwD44AJHQAFAF0ABQAdAA+ALO+ADEwfSAQ4C0gEOAg==` | ✅ |
| **Volume Down** | `BfMDyQXxAeABAQEnAuADAwnJBScC8QHxAckF4A0DQAEByQUgIwDGwEcgCwAB4AkBA8kF8QFAAUAH4AEDAycCyQWADwfxAfEByQXxAQ==` | ✅ |
| **Mute** | `BwsEyQUKAtMB4BEDQB8FyQXTAckFQAfgCQMF0wEKAgTHgEdAAUAP4AsD4As74AMTA9MBCgI=` | ✅ |
| **Bluetooth** | `D9oDxQUfAsUF9AH0AR8C9AHgCQGAGwH0AUAHBcUFHwLFBUAH4AEDQAEBCcdARwH0AUADA/QBHwLgAQPgAQGAGwH0AUAH4AUDCR8CxQX0AfQB9AE=` | ❌ |
| **Bass** | `BdEDyQUSAkADAeEB4AkD4AMXQAuAAwHhAcADAeEBgBMBDcfgC0fgAQFALwPhARICQAMByQXgCQMH4QHhAckF4QE=` | ❌ |
| **Dialogue** | `BfoDygUiAkADAesB4A8DgAEBygXgDwMDIgLVxuADR+APAQEiAkADA8oF6wHgDAMCBesB` | ❌ |
| **TV** | `B/QDwgUTAtwB4AUDQBPAA0AbA8IF3AGAA0ALAxMC3AHgAQNADwHnxsBHwAEBEwJAA0AbwAPgBw8TwgXcAdwBEwLcARMC3AETAsIFEwI=` | ❌ |

> **Note:** Only On/Off, Volume Up, Volume Down, and Mute are wired into this blueprint. The Bluetooth, Bass, Dialogue, and TV codes are listed for reference only (captured from the real Bose remote) and are **not implemented** — use them directly from your IR blaster or a separate automation if you need them.

Every implemented code is a per-command text input, so you can override any default if your hardware uses a different IR set.

### Subtype strings

The subtype is the action string Zigbee2MQTT publishes when a button is pressed (e.g. `1_single`, `2_single`, `1_double`, `toggle`, etc.). The exact values depend on the remote model — check the HA automation trigger dropdown or the Z2M logs for the remote in question. Every subtype field defaults to `1_single`, which matches a single-press on the first (or only) button of most remotes.

---

## Prerequisites
* An **IR blaster** that is driven by a Home Assistant `text` entity (e.g. an ESPHome-based blaster exposing a text component, or a Broadlink/Xiaomi blaster wrapped with a text helper) and that can emit Bose-compatible IR from line of sight to the speaker
* A **Bose TV Speaker** (or another device that accepts the same IR codes)
* One or more **Zigbee remote(s)** paired via Zigbee2MQTT that publish MQTT device triggers

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2Fmain%2Fbose-tv-speaker-remote%2Fbose-tv-speaker-remote.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Single remote with 4 buttons** — set every `*_device` field to the same remote and give each command a distinct subtype (`1_single`, `2_single`, …).
* **Four single-button remotes** — set each `*_device` to a different remote and leave every subtype at `1_single`.
* **Anything in between** — mix devices and subtypes freely per command.
* **Override any IR code** per-instance if your hardware uses a different IR set.
* **Use with any IR-controlled device** — not limited to the Bose TV Speaker; replace the four default payloads with codes for any IR target.

---

## License

MIT
