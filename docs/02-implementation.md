# 02 Implementation

[← Back to README](../README.md)

- **Engine:** HA template binary sensors with `delay_on` for persistence; complex rules in Node-RED on the [supervisory layer](https://github.com/the-control-cabinet/ha-node-red-supervisory-layer).
- **Inputs by tag** where possible (see [semantic tagging](https://github.com/the-control-cabinet/haystack-semantic-tagging)).
- **Output:** a fault entity with `cause` and `action` attributes; severity P3/P4 into the [alarm register](https://github.com/the-control-cabinet/alarm-and-trend-strategy).

## Live alerts (11 Nov 2026)

The first rules now run as Home Assistant automations in the plant monitoring alerts package ([doc 15 there](https://github.com/the-control-cabinet/heating-plant-monitoring-esphome/blob/main/docs/15-alerts.md)), with **commissioning gates** (switches) for inputs that aren't live yet.

| Rule | As implemented | State |
|---|---|---|
| F1 / F17 | > 6 ignition attempts in the last hour (history_stats on the current-clamp state), repeat after 1 h | Live |
| F2 | "Firing without call" binary sensor, 2 min | Gated (opto) |
| F5 | 24 h pressure change < −0.1 bar, checked cold at 05:00 | Gated (boiler gauge box) |
| F7 | Any zone ≥ 95% heat demand and > 1 °C below setpoint for 2 h | Live |
| F9 | A cylinder's heat demand on for 90 min | Live |
| F10 | Control-room board offline 5 min | Live |
| F15 | IN3/IN4 on, IN5/IN6 off for 10 min | Gated (opto) |
| F16 | Hot water heat demand with IN2 off for 5 min | Gated (opto) |
| F18 | Heat demand on and the boiler off/idle for 15 min | Live |
| F19 | Inlet > 4.5 bar for 2 min (plus < 2 bar for 10 min) | Live |
| F20 | NTC < −10 or > 110 °C; pressure pin < 0.2 V | Live |

**Lesson: choose the input that really means "calling".** For the RAMSES hot water zones, `heat_demand` is 100 while a cylinder calls; `relay_demand` is not an on/off signal (it wandered 58 → 0% with no reheat), and gave two false alerts before the switch. The wired opto inputs will replace both for F9/F18 once live.
