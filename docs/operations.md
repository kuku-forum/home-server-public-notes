# Operations

This page describes safe operating checks for the home-server pattern without
publishing live commands, addresses, hostnames, paths, or identifiers.

## Daily Health Check

Check the system in this order:

1. Home Assistant web surface is reachable.
2. Home Assistant reports no critical repairs.
3. The HAOS virtual machine is running.
4. The MQTT broker and Zigbee2MQTT bridge are available.
5. Zigbee permit-join is closed unless a pairing session is active.
6. The Mac mini host status summary is current.
7. The external drive is in the expected mounted or powered-off state.
8. The latest Home Assistant backup is recent.
9. Public Home Assistant access and private administration access still follow
   separate paths.

## Reboot Checklist

After a host reboot:

1. Confirm the host is reachable through the private administration path.
2. Confirm the HAOS VM is running.
3. Confirm Home Assistant responds locally or through its normal web surface.
4. Confirm the public Home Assistant route works.
5. Confirm private administration still works.
6. Confirm host helper services restarted.
7. Confirm the external storage state is expected.
8. Confirm dashboards show health cues again.

Some host helpers may depend on a logged-in user session. That is documented in
the private runbook because the exact helpers and local paths are private.

## Service Restart Order

When multiple parts are down, recover from the inside out:

1. Host networking.
2. HAOS VM.
3. Home Assistant.
4. MQTT broker.
5. Zigbee2MQTT.
6. Public tunnel or normal web route.
7. Dashboard-only helpers.

Do not restart Zigbee2MQTT during pairing, firmware updates, or active device
debugging unless the private runbook says to do so.

## Storage Operation

The external drive should be treated as host-managed storage:

- Power-on should wait for the disk to appear.
- The host should mount the filesystem at the expected private location.
- SMB should be verified after the mount.
- Power-off should only happen after open writes are checked and unmount
  succeeds.
- Failure should leave power on and report the error.

The public docs do not include the real mount path, share name, script path, or
smart-plug entity.

## Dashboard Checks

Daily dashboards should show useful health cues without exposing risky controls.
Maintenance actions such as restart, pairing, storage power, backup actions, and
health checks should live on an admin or system view that requires deliberate
navigation.

