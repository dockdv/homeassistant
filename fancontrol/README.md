# MOES Uzaktan Kumanda – Fan Control Blueprint  
*A Home Assistant automation blueprint that drives a ceiling-fan IR blaster with a MOES / Tuya Zigbee remote (TS004F).*

> **Out-of-the-box compatibility:**  
> The four default IR strings included in this blueprint have been tested and verified to work with standard **Westinghouse ceiling-fan receivers**. If your fan is a different brand or model, simply paste in your own base-64 codes during set-up.

---

## What it does
This blueprint rolls four separate automations (Fan **OFF**, **1**, **2**, **3**) into a single, tidy package:

| Remote Button | IR Action | Default Westinghouse Code |
| ------------- | --------- | ------------------------- |
| 1 × Press (1) | Fan **OFF** | `A/MEpwFAAwPcAfME4A…TcAQ==` |
| 1 × Press (2) | Fan Speed **1** | `A/cElAFAAwPCAfcE4B…AwIE9wQ=` |
| 1 × Press (3) | Fan Speed **2** | `A/QElQFAAwPCAfQEwA…fQElQE=` |
| 1 × Press (4) | Fan Speed **3** | `A/cElAFAAwPBAfcEwA…f9wSUAfcE` |

It simply writes the selected IR string to a **text** entity that your IR blaster watches—no extra “send” step needed.

---

## Prerequisites
* **Home Assistant 2023.6 or newer** (blueprint format)  
* MOES/Tuya Zigbee 4-button remote **TS004F** exposed via ZHA or Zigbee2MQTT  
  (Anything producing `mqtt action` triggers with `subtype: 1_single … 4_single` will work.)  
* An IR blaster that  
  * exposes a **`text`** entity for the raw command, **and**  
  * automatically transmits whenever that entity changes.  
  (Many Tuya Wi-Fi or Broadlink DIY devices behave this way.)  
* *(Optional)* Different fan brand? Have your own **base-64** IR strings handy so you can paste them into the blueprint inputs.

---

## Installation

<a href="https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdockdv%2Fhomeassistant%2Fblob%2F0f344e5b778ae7b3619b86f4e2702fad1dc241a3%2Ffancontrol%2Ffancontrol.yaml" target="_blank" rel="noreferrer noopener"><img src="https://my.home-assistant.io/badges/blueprint_import.svg" alt="Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled." /></a>

---

## Customisation
* **Swap IR codes** any time in the automation’s *Variables* section.  
* **Add more speeds or functions**: duplicate a trigger/input pair (`subtype: 5_single`, etc.) and provide the matching code.  
* **Long-press actions**: copy a trigger with `subtype: 1_long` and add a corresponding IR string.  
* **Other devices**: exchange the IR payloads for light, heater, or A/C commands—whatever your blaster supports.

---

## License

MIT
