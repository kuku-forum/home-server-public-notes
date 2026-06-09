# Recovery Runbook

This runbook is public-safe. It describes recovery order and decision points,
not live commands.

## Home Assistant Unreachable

1. Try the normal Home Assistant web surface.
2. Try the private administration path.
3. Check whether the HAOS VM is running.
4. Check whether Home Assistant responds inside the private network.
5. Check host helper services only after the VM and Home Assistant are known.
6. If public access is the only failing path, inspect the public tunnel or DNS
   route instead of changing Home Assistant.

## MQTT Broker Unavailable

1. Confirm Home Assistant itself is running.
2. Check the broker add-on or service status from the trusted admin surface.
3. Review recent broker logs.
4. Restart only the broker if Home Assistant is otherwise stable.
5. Confirm Zigbee2MQTT reconnects after the broker recovers.

## Zigbee2MQTT Unavailable

1. Confirm MQTT is available.
2. Confirm the network coordinator is powered and reachable.
3. Confirm Zigbee2MQTT is running.
4. Check recent Zigbee2MQTT logs.
5. Avoid mass re-pairing. Most outages should be handled by restoring the bridge
   first.

## Zigbee Permit-Join Left Open

1. Close permit-join from the admin surface.
2. Confirm the dashboard shows the closed state.
3. Check whether the safety automation exists and is enabled.
4. Review whether any pairing session was interrupted.

## SMB Share Unavailable

1. Confirm the external drive is powered as expected.
2. Confirm the drive is mounted at the expected private path.
3. Confirm the SMB server is running.
4. Confirm trusted clients use authenticated access.
5. Do not publish SMB directly to the internet.

## External Drive Not Mounted

1. Confirm whether the drive is powered.
2. Confirm whether the host sees the physical disk.
3. Mount through the private runbook or the guarded helper.
4. Verify the SMB share after mounting.
5. If the disk mounts at the wrong path, use the private runbook to remount it
   at the expected location.

## Backup Failure

1. Confirm Home Assistant backup status.
2. Confirm the backup destination is reachable.
3. Confirm the external drive is powered and mounted if it is the target.
4. Confirm the new backup is non-zero size and readable.
5. Do not run a full restore on the live system as a routine test.

## Public Access Issue

1. Check private Home Assistant access first.
2. If private access works, inspect the public route.
3. Do not expose management services while debugging public access.

## Private Admin Access Issue

1. Check whether Home Assistant still works for daily use.
2. Check local network reachability.
3. Check private network client state.
4. Use local console or screen access only if the private path is unavailable.

