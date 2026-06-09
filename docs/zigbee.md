# Zigbee

The Zigbee stack uses a network coordinator with Zigbee2MQTT and MQTT.

```text
Zigbee devices
  -> network Zigbee coordinator
  -> Zigbee2MQTT
  -> MQTT broker
  -> Home Assistant entities
```

## What Was Done

- A network Zigbee coordinator was selected instead of relying on VM USB
  passthrough.
- Zigbee2MQTT was configured as the main Zigbee integration path.
- MQTT discovery exposes Zigbee devices into Home Assistant.
- A dashboard entry was added for checking the Zigbee2MQTT map.
- Permit-join is normally closed and opened only for short pairing windows.
- Safety automation closes permit-join if it remains open too long.

## Migration Notes

Some Zigbee sensors and buttons work well through Zigbee2MQTT. Some wall-switch
relay devices were less reliable on this path and were kept on a more stable
existing integration.

The practical rule is:

- migrate sensors, buttons, and low-risk devices gradually
- keep fast, user-facing wall switches on the path that responds reliably
- preserve stable Home Assistant entity IDs where possible
- disable stale legacy entities only after dashboards and automations are
  checked

## Public Safety

The public notes omit coordinator addresses, serial URLs, IEEE identifiers,
firmware identifiers, MQTT topics tied to real friendly names, and exact
pairing routes.
