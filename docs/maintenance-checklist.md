# Maintenance Checklist

Use this checklist before and after changes that affect Home Assistant, Zigbee,
storage, backups, or host services.

## Before A Change

- Confirm Home Assistant is currently healthy.
- Confirm the latest backup is recent.
- Create a fresh backup before risky add-on, integration, Zigbee, or dashboard
  changes.
- Confirm at least one backup copy exists outside the HAOS VM.
- Confirm the external drive is mounted if it is needed for backup copy.
- Check whether the change touches public access or private administration.
- Keep secrets out of notes, screenshots, exports, and commits.

## During A Change

- Change one layer at a time.
- Avoid pairing, migration, and service restarts in the same maintenance window.
- Prefer stable entity IDs over device IDs in automations and dashboards.
- Keep physical wall-switch paths on the most reliable integration.
- Avoid raw storage power toggles.
- Do not expose new services publicly by default.

## After A Change

- Confirm Home Assistant is reachable.
- Confirm MQTT and Zigbee2MQTT are connected.
- Confirm permit-join is closed.
- Confirm dashboards load without missing critical controls.
- Confirm daily controls still work.
- Confirm backup status is still visible.
- Update private operating docs with exact values.
- Update public docs only with sanitized patterns.

## Risky Changes That Need A Window

- Zigbee2MQTT updates.
- MQTT broker changes.
- Home Assistant core updates.
- Dashboard resource changes used by mobile apps.
- Storage mount or power-control changes.
- Network route, tunnel, or private admin access changes.
- Backup destination changes.

