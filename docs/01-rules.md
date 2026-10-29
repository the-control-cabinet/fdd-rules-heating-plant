# 01 Rule catalogue

[← Back to README](../README.md)

| # | Fault | Logic | Persistence | Probable cause | Action |
|---|---|---|---|---|---|
| F1 | **Short-cycling** | > 6 boiler firings/hour with demand present | 2 h | Oversized output vs load, high flow temp, TPI settings | Lower flow temp; review TPI cycle rate; OpenTherm modulation |
| F2 | **Firing without demand** | Boiler firing AND no BDR91 demand | 2 min | Wiring fault, stuck relay, boiler frost/pump cycle | Check the BDR91s / switched live |
| F3 | **Low ΔT** | Firing AND ΔT < 5 K | 30 min | Pump speed high, bypass open | Check pump speed / bypass |
| F4 | **High return temp** | Return > 55 °C for most of the burn | per day | Not condensing: flow temp too high | Weather compensation (OpenTherm) |
| F5 | **Pressure decay** | Same-condition pressure falling > 0.05 bar/day | 3 days | Leak, expansion vessel, PRV weep | Leak-detection procedure |
| F6 | **Sensor disagreement** | NTC flow vs OpenTherm flow differ > 3 K | 1 h | Sensor drift/placement | Recalibrate |
| F7 | **Stuck zone** | Zone demand 100 % but temp not rising for 1 h | 1 h | Valve/actuator fault, airlock | Check the actuator |
| F8 | **Comfort complaint** | Occupied zone > 1 °C below setpoint for 1 h | 1 h | Under-capacity, schedule, open window | Check the zone |
| F9 | **DHW priority overrun** | Cylinder calling > 90 min | 90 min | Cylinder coil, valve, stat | Check the cylinder |
| F10 | **Stale sensor** | No update > 10 min | 10 min | Board offline / sensor failure | Check the board |
| F11 | **Simultaneous heating and cooling** | A zone's heat demand > 0 AND the aircon cooling the same room | 5 min | Conflicting setpoints, no dead band | Apply the heating/cooling dead-band interlock |
| F13 | **Overrun with no flow path** | Boiler in overrun AND flow temperature rising, or boiler lockout shortly after a call ends | 1 event | No bypass; all TRVs and zone valves closed | Confirm the bypass; fit an automatic bypass valve or leave one radiator without a TRV head |
| F14 | **Restricted radiator circuit** | Radiator zones calling AND a large boiler ΔT with slow room recovery on cold days | 3 days | Zone valve latched only partly open; balancing | Check the valve position; re-power the heads or replace the bodies |
| F12 | **Outdoor sensor disagreement** | Local weather station vs online sources differ > 3 K | 1 h | Sensor in sun, failed station, stale feed | Use the validated value for weather compensation; check the station |
