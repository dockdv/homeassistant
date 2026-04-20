# Bose TV Speaker Remote (IR) Blueprint
*A Home Assistant automation blueprint that sends Bose TV Speaker IR commands through an IR blaster's text entity, wired to fully custom triggers.*

---

## What it does
This blueprint maps eight Bose TV Speaker IR commands to eight independent trigger inputs. Each command is fired by writing its base-64 IR payload to a `text` entity that your IR blaster watches and auto-sends. Every trigger is a full HA trigger selector, so any source — Zigbee/Z-Wave remote, dashboard tap, voice assistant, state change, schedule, webhook, script call — can fire any command.

### Default IR codes

| Command | IR code (base-64) |
| ------- | ----------------- |
| **On/Off** | `CfEDwgUcAvABHALAB8AL4AcPBfAB8AHCBYADwAHADwXxxvEDwgXgASPAAUATA8IF8AHAAQnCBRwC8AHwAcIFgAPAAQfCBfABwgUcAg==` |
| **Volume Up** | `B/gDwQUOAtIB4A0DQBvgEwPANwP4xvgDQCfAD+AFBwHSAUAbAsEFbCADQAfgCQMB0gGAAwD44AJHQAFAF0ABQAdAA+ALO+ADEwfSAQ4C0gEOAg==` |
| **Volume Down** | `BfMDyQXxAeABAQEnAuADAwnJBScC8QHxAckF4A0DQAEByQUgIwDGwEcgCwAB4AkBA8kF8QFAAUAH4AEDAycCyQWADwfxAfEByQXxAQ==` |
| **Mute** | `BwsEyQUKAtMB4BEDQB8FyQXTAckFQAfgCQMF0wEKAgTHgEdAAUAP4AsD4As74AMTA9MBCgI=` |
| **Bluetooth** | `D9oDxQUfAsUF9AH0AR8C9AHgCQGAGwH0AUAHBcUFHwLFBUAH4AEDQAEBCcdARwH0AUADA/QBHwLgAQPgAQGAGwH0AUAH4AUDCR8CxQX0AfQB9AE=` |
| **Bass** | `BdEDyQUSAkADAeEB4AkD4AMXQAuAAwHhAcADAeEBgBMBDcfgC0fgAQFALwPhARICQAMByQXgCQMH4QHhAckF4QE=` |
| **Dialogue** | `BfoDygUiAkADAesB4A8DgAEBygXgDwMDIgLVxuADR+APAQEiAkADA8oF6wHgDAMCBesB` |
| **TV** | `B/QDwgUTAtwB4AUDQBPAA0AbA8IF3AGAA0ALAxMC3AHgAQNADwHnxsBHwAEBEwJAA0AbwAPgBw8TwgXcAdwBEwLcARMC3AETAsIFEwI=` |

Every code is a per-command text input, so you can override any default per-instance if your unit uses a different IR set.

### Custom triggers

Each of the eight commands exposes a **trigger selector** input. You can attach one or more triggers of any type — MQTT device triggers from a Zigbee remote, ZHA events, state changes, dashboard buttons, time/schedule triggers, webhooks, etc. Leave a trigger empty to disable that command.

Dispatch uses HA's grouped-trigger syntax (each `!input` group carries an `id`), which requires **Home Assistant 2024.10 or later**.

---

## Prerequisites
* An **IR blaster** that is driven by a Home Assistant `text` entity (e.g. an ESPHome-based blaster exposing a text component, or a Broadlink/Xiaomi blaster wrapped with a text helper) and that can emit Bose-compatible IR from line of sight to the speaker
* A **Bose TV Speaker** (or another device that accepts the same IR codes)
* One or more **trigger sources** for the commands you want to wire up (Zigbee remote, dashboard button, voice assistant, automation, etc.)

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2Fmain%2Fbose-tv-speaker-remote%2Fbose-tv-speaker-remote.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Override any IR code** per-instance if your hardware uses a different IR set — the defaults above are inputs, not constants.
* **Attach multiple triggers to a single command** — e.g. wire both a Zigbee remote button and a dashboard tap to Volume Up.
* **Mix trigger sources freely** — MQTT device triggers, ZHA events, state triggers, and time patterns can all coexist across the eight commands.
* **Leave commands you don't need empty** — a command with no triggers simply doesn't fire and costs nothing.
* **Use with any IR-controlled device** — not limited to the Bose TV Speaker; replace the eight default payloads with codes for any IR target.

---

## License

MIT
