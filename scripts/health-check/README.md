# Health Check Script Notes

This folder is for public-safe notes about future health-check scripts.

Do not commit live scripts that contain real paths, hostnames, addresses,
tokens, entity IDs, or service credentials.

Future examples should use names like:

- `health-check.example.sh`
- `config.example.yaml`

Checks should stay read-only:

- Home Assistant availability.
- MQTT availability.
- Zigbee2MQTT bridge state.
- SMB availability.
- External drive mounted state.
- Backup freshness.
- Disk usage.

