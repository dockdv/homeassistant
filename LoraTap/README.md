# Home Assistant Blueprint — LoraTap 3-Button Remote (Zigbee2MQTT / TS0043)

This repo provides a Home Assistant blueprint for the common **LoraTap 3-button Zigbee remote**, often identified as **Tuya TS0043**, when paired via **Zigbee2MQTT**.

## What’s included

- `TS0043.yaml` — blueprint for **Zigbee2MQTT**

## Requirements

- Home Assistant
- Zigbee2MQTT integration
- The remote paired in Zigbee2MQTT (it should expose an `action` sensor, typically `sensor.<name>_action`)

## Install

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/dockdv/homeassistant/blob/main/LoraTap/TS0043.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

### Option A: Import from URL (recommended)

1. In Home Assistant go to **Settings → Automations & Scenes → Blueprints**
2. Click **Import Blueprint**
3. Paste the **raw GitHub URL** to `loratap_ts0043_z2m.yaml`
4. Click **Preview** → **Import**

### Option B: Manual install

Copy the YAML file into your Home Assistant config:

- `config/blueprints/automation/loratap_ts0043_z2m.yaml`

Then restart Home Assistant (or reload automations) and create an automation using the blueprint.

## Usage

1. Go to **Settings → Automations & Scenes → Automations**
2. Click **Create Automation**
3. Choose **Start with blueprint**
4. Select the blueprint and map actions for button presses (e.g. single/double/hold for buttons 1–3)

## License

MIT
