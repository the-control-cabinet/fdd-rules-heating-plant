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
| F12 | **Outdoor sensor disagreement** | Local weather station vs online sources differ > 3 K | 1 h | Sensor in sun, failed station, stale feed | Use the validated value for weather compensation; check the station |
| F13 | **Overrun with no flow path** | Boiler in overrun (switched live just dropped) AND flow temperature rising, or boiler lockout (L1) shortly after a call ends | 1 event | No automatic bypass; all TRVs and closing zone valves shut. The Ideal Logic+ System S30 manual requires an ABV with TRVs on all radiators or two-port valves | Read the fault history; fit an automatic bypass valve or leave one radiator (≥ 10 % of minimum output, about 0.6 kW) open on twin lockshields |
| F14 | **Restricted radiator circuit** | Radiator zones calling AND a large boiler ΔT with slow room recovery on cold days | 3 days | Zone valve latched only partly open; balancing | Check the valve position; re-power the heads or replace the bodies |
| F15 | **Cylinder relay calling, stat not passing** | RAMSES cylinder relay ON AND opto "hot water enabled" ON AND opto "stat passing" OFF (6-way pos 1 or 2) | 10 min | Cylinder stat (boiler-control module) set below the Evohome DHW setpoint, or the **manual-reset overheat cut-out has tripped** | Check the cylinder stat setting (at or above the Evohome setpoint); inspect and reset the cut-out only after finding why it tripped |
| F16 | **Hot water disabled by the timer** | Evohome DHW calling (RAMSES) AND opto "hot water enabled" OFF | 5 min | Danfoss TS715Si off its permanent-ON setting (e.g. after a power cut); it still gates both hot-water relays | Return the timer to permanent ON; long term, take the relays' feed from the live bar |

**Origin of F13, F15 and F16:** the October 2026 junction box survey ([Evohome repo, A4 and A6](https://github.com/the-control-cabinet/evohome-heating-controls-ramses-integration/blob/main/docs/A4-junction-box-survey-and-wiring.md)). F15 and F16 use the re-scoped opto inputs ([plant monitoring, doc 11](https://github.com/the-control-cabinet/heating-plant-monitoring-esphome/blob/main/docs/11-opto-board-installation.md)) together with RAMSES-II relay states: a physical signal compared with the controller's intent.
