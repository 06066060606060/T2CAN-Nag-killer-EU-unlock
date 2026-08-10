
# Nag-killer & EU-Unlock V2.3-BETA for LilyGO/T-2Can Model YL version

> ⚠️ Research / educational firmware only.
>
> This project interacts with a vehicle CAN bus. It is intended for controlled bench testing, code review, and research environments only.It sends signals directly to the controller, not a physical command to the steering wheel. Do not use this on public roads or in any situation where unsafe behavior could put people or property at risk. You are responsible for your own testing, wiring, configuration, and local laws.
---

## distinctive feature of the Tesla Model YL (after March, 2026)
Some CAN frames are not present on the chassis & Party BUS and must be retrieved from Body/VH BUS

| Flag            | Source         | Condition                | Model YL bus                           |  
|-----------------|----------------|--------------------------|----------------------------------------|       
| `Parked`        | CAN 280 / 390  | Gear == P                | Party CAN(pin 2/3)                     |  
| `Summoning`     | CAN 280        | `ACA == 1` AND `SPR ≠ 0` | Party CAN (pin 2/3)                    |  
| `gateAPActive ` | CAN 921        | status == 3 ,4 ,5 ,6     | Party CAN (pin 2/3)                    | 
| `autopilot    ` | CAN 1021 + 1016|                          | Body/Vh CAN (pin 9/10)                 |

## What V2.3 Update Changes
- Added a toggle in dashboard to enable TLSSC where it is not available.
- 
--------------------Update 2.2-------------------
- bypass R79 EU restriction in AP
- Expend summon to +/-  85m
- expanded lateral acceleration limits
- lane changes near forks isn't disabled (EAP)
- instantaneous lane change on blinker (EAP)
- no lane change timeout once initiated (EAP)
- takes forks and exits automatically (EAP)
- Continue on Green with Car in Front (EAP)
- OTA Update

## Hardware Target

This fork was adapted for:

| Device                       | Can Transceiver                         | CAN RX / CAN TX   | Can Bus      | Power                     |
| ---------------------------- | --------------------------------------- | ----------------- | ------------ | ------------------------- |
| LilyGO/T-2Can                |CAN A Party CAN → Nag Killer & EU Unlock |                   |              |                           |
|                              |CAN B Body/VH CAN → EU Unlock            |                   | 500 kbps CAN | USB-C or stable 12V supply|



---

## Board Setup (Arduino IDE)  
- Board: LilyGo T-Display S3 

## Libraries needed:  
- ESP32 BLE Arduino (built-in)  
- mcp2515 by autowp (install via Library Manager)  
https://github.com/autowp/arduino-mcp2515

## Files in sketch folder:
- nag-killer-t2can-test.ino  
- index_html.h  
- pin_config.h  

## Wiring
- CAN A (MCP2515): connect to the Party CAN bus - X179(2-3)
- CAN B (TWAI): connect to the Body/Vehicule CAN bus -  X179(9-10)

## Dashboard Notes

- The Wifi AP name will be something like T2CAN-A1B2 (password: 12345678).  
- Open 192.168.4.1 in a browser.  
- Use the tabs to switch between Nag Echo and Summon Unlock.  

## Build firmware using arduino IDE for OTA
- Open Sketch > Export Compiled Binary.
- Open /T2CAN_Unified/build/ folder
- Upload T2CAN_Unified.ino.bin (924Ko) using the web dashboard & Update
---  

## Discord server: 
https://discord.gg/euPbYG8Npc

> **Support the project:**  
> [![Buy Me A Coffee](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://buymeacoffee.com/mickymurcid)


## Credits

- Inspired by `Ev Open Can Mod` https://github.com/ev-open-can-tools/ev-open-can-tools
- Created by X₿mod.
- ESP32 TWAI driver by Espressif Systems
- Automotive CAN research community

<img width="471" height="760" alt="image" src="https://github.com/user-attachments/assets/b0663d9f-4e92-4fb0-9cbd-e9eb729d3dc5" />



