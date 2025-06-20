# MOES Uzaktan Kumanda – Fan Control Blueprint  
*A Home Assistant automation blueprint for driving a ceiling-fan IR blaster with a MOES / Tuya Zigbee remote (TS004F).*

---

## What it does
This blueprint merges four separate automations (Fan **OFF**, **1**, **2**, **3**) into one tidy package:

| Remote Button | IR Action |
| ------------- | --------- |
| 1 × Press (1) | Fan OFF |
| 1 × Press (2) | Fan Speed 1 |
| 1 × Press (3) | Fan Speed 2 |
| 1 × Press (4) | Fan Speed 3 |

It simply writes a base-64 IR string to a **text** entity that your IR blaster monitors—no extra “send” step needed.

---

## Prerequisites
* **Home Assistant 2023.6 +** (blueprint format)
* MOES/Tuya Zigbee 4-button remote **TS004F** exposed via ZHA or Zigbee2MQTT  
  (Anything that produces `mqtt action` triggers with `subtype: 1_single … 4_single` will work.)
* An IR blaster that
  * exposes a **`text`** entity for the raw command, **and**
  * automatically transmits when that entity changes.  
  (Many Tuya Wi-Fi or Broadlink DIY devices behave this way.)

---

## Installation
1. **Copy** `moes_fan_control.yaml` into  
   `config/blueprints/automation/moes_fan_control.yaml`  
   *or* use **Settings ▸ Blueprints ▸ Import Blueprint** and paste the raw file URL.
2. **Reload Blueprints** (or restart HA).

---

## Creating an Automation
1. **Create Automation → From Blueprint → “MOES Uzaktan Kumanda – Fan Control”**  
2. Fill in the required fields:  
   * **Remote device** – select your TS004F remote  
   * **Text entity** – pick the `text.*` entity on your IR blaster  
   * **IR codes** – keep the defaults or paste your own base-64 strings
3. **Save** and test each button—done!

---

## Customisation
* **Change IR codes** any time in the automation’s *Variables* section.
* **Add more speeds**: duplicate a trigger/input pair (`fan_4`, `subtype: 5_single`, etc.).
* **Long-press actions**: copy a trigger with `subtype: 1_long` and add a corresponding IR string.
* **Other devices**: swap the IR strings for light, heater, or A/C commands—whatever your blaster supports.

---

## Credits
Blueprint by **\<your name or handle\>**.  
Original standalone automations contributed by the Home Assistant community.
