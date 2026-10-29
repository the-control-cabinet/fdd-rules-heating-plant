# 02 Implementation

[← Back to README](../README.md)

- **Engine:** HA template binary sensors with `delay_on` for persistence; complex rules in Node-RED on the [supervisory layer](https://github.com/the-control-cabinet/ha-node-red-supervisory-layer).
- **Inputs by tag** where possible (see [semantic tagging](https://github.com/the-control-cabinet/haystack-semantic-tagging)).
- **Output:** a fault entity with `cause` and `action` attributes; severity P3/P4 into the [alarm register](https://github.com/the-control-cabinet/alarm-and-trend-strategy).
