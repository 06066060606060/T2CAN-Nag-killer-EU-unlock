# Nag-killer & EU-Unlock V2.5.2
### Unified firmware for LilyGO / T-2Can

> ⚠️ **Research / educational firmware only**
>
> This project interacts with a Tesla vehicle CAN bus. It is intended for controlled bench testing, code review, and research environments only.
>
> It sends signals directly to the controller, not a physical command to the steering wheel. **Do not use this on public roads or in any situation where unsafe behavior could put people or property at risk.**
>
> You are responsible for your own testing, wiring, configuration, and compliance with local laws.

---
### ⚠️ Do not activate TLSSC if you do not have an FSD subscription.  high risk of being banned. 

## 📋 What's New

### V2.5.2

- Added **TLSSC Restore** for banned cars.
- Added **Blindspot aggressiveness** settings (`MadMax`).

### V2.4

- Completely reworked code by **LP_YL**.
- New dashboard design by **LP_YL**.
- Summon TX Priority state machine.
- CAN A/B self-healing and hard reinitialization.
- Runtime and boot timing diagnostics.

### V2.3

- Added a dashboard toggle to enable **TLSSC** where it is not available.
  - A valid **FSD subscription** is required.
- Bypass **R79 EU restriction** in AP.
- Expanded Summon range to **±85 m**.
- Expanded lateral acceleration limits.
- Lane changes near forks are not disabled (EAP).
- Instantaneous lane change on blinker (EAP).
- No lane-change timeout once initiated (EAP).
- Automatically takes forks and exits (EAP).
- Continue on Green with Car in Front (EAP).
- OTA update support.

---

## 🚙 Model YL Branch

A dedicated branch is available for **Model YL**:

**https://github.com/06066060606060/Advanced-eap-eu-unlock/tree/modelYL**

---

## ✅ Compatibility

| Item | Version / Status |
|---|---|
| AP Injection | Does not work before **2026.20** |
| Tested version | **2026.26.6.1** |

---

## 🔧 Hardware Target

This fork was adapted for the **LilyGO / T-2Can**.

| Device | CAN Interface | CAN Bus | Function |
|---|---|---|---|
| LilyGO / T-2Can | CAN A — MCP2515 | Party CAN | Nag Killer |
| LilyGO / T-2Can | CAN B — TWAI | Chassis CAN | Summon Unlock |

**CAN speed:** 500 kbps  
**Power:** USB-C or a stable 12 V supply

### ⚠️ Important: 120 Ω resistors

Don't forget to remove the two **120-ohm resistors**, as they can cause signal errors.

<img width="407" height="180" alt="LILYGO-T-2CAN_9" src="https://github.com/user-attachments/assets/0d272b7e-bd82-408f-9ca1-239e6dab44d5" />

---

## 🛠️ Board Setup — Arduino IDE

### Board

- **LilyGo T-Display S3**

### Required libraries

- **ESP32 BLE Arduino** — built-in
- **MCP2515 by autowp** — install via the Arduino Library Manager
- Repository: https://github.com/autowp/arduino-mcp2515

---

## 📁 Sketch Files

The sketch folder contains:

```text
T2CAN_Unified.ino
index_html.h
pin_config.h
```

---

## 🔌 Wiring

| Interface | Transceiver | Vehicle CAN Bus | Function |
|---|---|---|---|
| **CAN A** | MCP2515 | Party CAN (2–3) | Nag Killer |
| **CAN B** | TWAI | Chassis CAN (13–14) | Summon Unlock |

---

## 🌐 Dashboard

After flashing the firmware:

1. Connect to the device's Wi-Fi access point.
2. The Wi-Fi AP name will be similar to:
   `T2CAN-A1B2`
3. Default password:
   `12345678`
4. Open the following address in your browser:
   **http://192.168.4.1**

> ⚠️ **TLSSC warning:** Do not enable TLSSC if you do not have the EAP option.

---

## 📡 OTA Firmware Update

To build the firmware for OTA updates using Arduino IDE:

1. Open the sketch in **Arduino IDE**.
2. Select:
   **Sketch → Export Compiled Binary**
3. Open the generated:
   ```text
   /T2CAN_Unified/build/
   ```
4. Locate:
   ```text
   T2CAN_Unified.ino.bin
   ```
   *(approximately 924 KB)*
5. Open the web dashboard.
6. Go to **Update** and upload the `.bin` file.

---

## 💬 Community & Support

### Discord

Join the project Discord server:

https://discord.gg/euPbYG8Npc

---


### ☕ Support the Project

<a href="https://www.buymeacoffee.com/xbmod" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me a Coffee" style="height: 60px !important;width: 217px !important;" ></a>

### ₿ Bitcoin

```text
bc1pl9nuyhqd78gjc2wdcqr39de7qwtff732ngr28vy8r2sxfa7a6uzsrhe387
```
### ⚡ Lightning

```text
₿cakegrip53@phoenixwallet.me
```

---

## 🙏 Credits

  - Inspired by **Ev Open Can Tools**  
- Created by **X₿mod**, edited by **LP_YL**.
- ESP32 TWAI driver by **Espressif Systems**.
- Automotive CAN research community.

---

## 📸 Dashboard

<img width="471" height="1000" alt="Dashboard" src="https://github.com/user-attachments/assets/c7b60bb3-f9ca-4d69-95fc-50dcbf2893b7" />
