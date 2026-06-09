# Monitoring

The monitoring goal is to make the server visible when it breaks without making
the setup complicated.

## Current Pattern

Home Assistant already receives host health cues from host-side helpers. That is
useful for daily visibility, but it should not be the only monitoring layer
because Home Assistant can be part of the outage.

A private Uptime Kuma service has been added as the first availability-monitoring
layer. It should remain private and should not be exposed to the public internet.

## Recommended Stack

1. Uptime Kuma for availability checks.
2. Netdata or Glances for host metrics.
3. Home Assistant sensors for user-facing summary.
4. Small host-side scripts only where product tools cannot check the target.

## Uptime Kuma

Use Uptime Kuma first for:

- Home Assistant web availability.
- Public Home Assistant route.
- Private Home Assistant route.
- MQTT broker availability.
- Zigbee2MQTT web or bridge status.
- SMB availability from the host or a trusted client path.
- Backup destination availability.

Exposure should be private or LAN-only. Do not publish it directly to the
internet.

## Netdata Or Glances

Use one host metrics tool for:

- CPU.
- Memory.
- Disk usage.
- Network activity.
- Uptime.
- Process-level pressure.

Netdata has a richer UI. Glances is lighter. Either should remain private.

## Home Assistant Summary

Home Assistant should show a compact health summary:

- Home Assistant backup age.
- Host status.
- External storage mounted or powered off.
- Zigbee2MQTT connected.
- Permit-join closed.
- Disk usage warning.
- Public/private access check result if available.

## Staged Plan

1. Keep current HA host status sensors.
2. Add Uptime Kuma privately.
3. Add host metrics if the user needs more detail.
4. Add backup age and external-drive checks.
5. Add notification rules only after false positives are controlled.
