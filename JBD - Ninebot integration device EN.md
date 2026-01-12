## Description:

![Integrator](img/integrator.jpg)

Integrator - device that allows you to connect JBD BMS to the controller of Ninebot G3 \ ZT3 \ F3 \ GT3 \ GT3 Pro series scooters. 
Key Features :
1. Full Plug & play, no need to flash the controller or bms
2. Supported apps:  Segway mobility, Powernine, Xiaodash
3. Full projection of battery information: current, temperature, cells voltage, battery voltage.
4. Extreme use timers.
5. Sleep mode to minimize power consumption
6. Battery connection up to 16s (17s 18s 19s ... 22s need MCU modding, more info below)
7. Charging mode display function
8. OTA updates

| **Device**                | **Compatible** |                                     Note                                      |
| ------------------------- | :------------: | :---------------------------------------------------------------------------: |
| Ninebot ZT3 Pro           |       ✅        |            >13s hw patch, > 16s deep board rework limited with 20s            |
| Ninebot G3                |       ✅        |            >13s hw patch, > 16s deep board rework limited with 20s            |
| Ninebot GT3               |       ✅        |            >13s hw patch, > 16s deep board rework limited with 20s            |
| Ninebot GT3 Pro           |       ✅        |                             20s design by default                             |
| Ninebot G30 / G2          |       ❌        | [Legacy integrator required](https://github.com/truesurge/Legacy-integrator/) |
| Ninebot GT1 / GT2         |       ❌        | [Legacy integrator required](https://github.com/truesurge/Legacy-integrator/) |
| Any else unlisted Ninebot |       ❌        | [Legacy integrator required](https://github.com/truesurge/Legacy-integrator/) |

⚠️ WARNING: To increase the voltage, you must replace the resistor inside the MCU that matches your voltage from the list below. Acceptable range is +5% 


![Placement](img/placement.png)

Type: SMD 0603

| Config          | Rate    | P.S.                                                                                                                             |
| --------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------- |
| 13s             | 200khom |                                                                                                                                  |
| 14s             | 215khom |                                                                                                                                  |
| 15s             | 230khom |                                                                                                                                  |
| 16s             | 246khom |                                                                                                                                  |
| 17s             | 260khom | Dangerous. Close to the limits of MOSFETs. You could burn them out. Be careful or just replace it together with the capacitors.  |
| 18s             | 276khom | Dangerous.  Close to the limits of MOSFETs. You could burn them out. Be careful or just replace it together with the capacitors. |
| 19s 20s 21s 22s |         | Dangerous. Close to the limits of MOSFETs. You could burn them out. Be careful or just replace it together with the capacitors.  |


## Installation:

1) ⚠️ Disable charge\discharge fets in app ⚠️

![tutorial](img/jbd_app_fets.jpg)

2) Conect Integrator to BMS with small 4 pin connector to uart port
3) Connect Integrator to MCU with 4pin Molex minifit connector
4) Connect Integrator with xt90 to MCU
5) Connect battery with xt90 to integrator
6) Enable charge\discharge fets in app
 
    Disconnection - ⚠️ in reverse order ⚠️

![tutorial](img/install_tutorial.jpg)
## Ordering and support

Russia - https://t.me/SurgeSPB
Belarus / Europe - https://shop.jsb.by
Support group - https://t.me/ninebotfun
## Best practices:

1) If you are using an electric brake, it is recommended that you set the overvoltage and overcurrent limits in the BMS settings to the maximum possible for your BMS. During braking, current flows into the battery and the voltage/current can be higher than the rated values, especially if the battery is 100% charged. If this is not done, the BMS may go into protection and the current will have nowhere to go but to stay somewhere in the controller(MCU), causing damage to the controller. It is also recommended not to charge the battery to 100%, thus prolonging the life of the battery itself and leaving free space for excess current during braking. This is the same as if you were trying to fill a bottle with more water than its capacity.
2) There is a folder with firmware in the repository: https://github.com/truesurge/integrator/tree/main/updates To flash the firmware, use: https://utility-beta.cfw.sh/