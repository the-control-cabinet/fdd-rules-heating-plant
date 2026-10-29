# Fault Detection and Diagnostics (FDD) Rules for a Heating Plant (Design Stage)

**Rule-based fault detection on data the plant already produces, as modern BMS analytics platforms do: short-cycling, firing without demand, low delta-T, pressure decay, sensor drift and disagreement, stuck zones and comfort complaints, each with explicit logic, persistence, a likely cause and a recommended action, feeding the alarm strategy.**

[![YouTube](https://img.shields.io/badge/YouTube-The%20Control%20Cabinet-red?logo=youtube)](https://www.youtube.com/channel/UC5Cupmz7vlfcodpCX7k8iuQ)
[![Portfolio](https://img.shields.io/badge/Portfolio-the--control--cabinet-24292f?logo=github)](https://github.com/the-control-cabinet/the-control-cabinet)
![Domain](https://img.shields.io/badge/BMS-FDD%20analytics-blue)
![Status](https://img.shields.io/badge/Status-Design%20stage-yellow)

> **The short version:**
> - **Inputs:** plant monitoring (flow/return, pressure, current-based boiler states, demands), RAMSES-II zones, water metering, later OpenTherm data.
> - **Rules:** each one has a condition, a persistence time, a severity, a probable cause and an action, so it isn't just an alarm, it's a diagnosis.
> - **Implementation:** HA template sensors or Node-RED (on the supervisory layer); results feed the alarm register at P3/P4.
> - **Validation:** each rule tested against historical data (true and false positives).

**Portfolio position:** Management level · analytics. Inputs from: [plant monitoring](https://github.com/the-control-cabinet/heating-plant-monitoring-esphome) · [Evohome/RAMSES](https://github.com/the-control-cabinet/evohome-heating-controls-ramses-integration) · [water metering](https://github.com/the-control-cabinet/mains-water-metering-modbus-rtu). Outputs to: [alarm strategy](https://github.com/the-control-cabinet/alarm-and-trend-strategy)

---

## Documents

| Doc | Contents |
|---|---|
| [01 Rule catalogue](docs/01-rules.md) | Logic, persistence, cause, action |
| [02 Implementation](docs/02-implementation.md) | Where rules run; outputs; severity |
| [03 Validation](docs/03-validation.md) | Testing rules against history |

## Roadmap
- [ ] Rules F2, F5, F10 first (data already available)
- [ ] F1/F3/F4 once the boiler clamp and NTCs are commissioned
- [ ] F15/F16 once the opto inputs are installed (cylinder stat / cut-out and timer watchdogs)
- [ ] F13 validated against the boiler fault history and overrun data
- [ ] Validation against history
- [ ] FDD summary dashboard

## Skills demonstrated (as built)
| Skill | Evidence |
|---|---|
| FDD | Rule catalogue with cause and action |
| Data analysis | Persistence, thresholds, validation against history |
| Integration with alarms | Severity-mapped outputs |
| Plant knowledge | Rules reflect boiler, hydronic and zone behaviour |

📺 [The Control Cabinet on YouTube](https://www.youtube.com/channel/UC5Cupmz7vlfcodpCX7k8iuQ)

*Built and documented by James · part of [The Control Cabinet BMS portfolio](https://github.com/the-control-cabinet/the-control-cabinet). MIT Licence.*
