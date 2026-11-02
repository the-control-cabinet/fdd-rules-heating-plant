# 03 Validation

[← Back to README](../README.md)

For each rule: replay 30 days of history, count true and false positives, tune the thresholds and persistence, and record the result in [data/rule-validation.csv](../data/rule-validation.csv).

## F1 short-cycling: first real-data evidence (2 Nov 2026)

With median + moving-average filters on the boiler flow and return NTCs, the cycles are clear: at low heating load the boiler fires every **4-8 minutes**, above the rule's 6 firings/hour threshold. The likely cause is load below the boiler's minimum output (6.1 kW). Two mechanisms still need separating, using RAMSES-II relay states against the flow trace:

| Mechanism | Signature |
|---|---|
| Boiler cycling on its own flow thermostat | Relay demand steady; flow rises to the cut-off, falls, re-fires |
| Several BDR91s switching the boiler in turn | Each firing lines up with a relay change |

The same traces also show three clean end-of-run results (flow falls to meet return after the last burn, with no spike): weak evidence of a flow path during overrun. The F13 bypass requirement still stands.
