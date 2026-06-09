# Backup Strategy

The backup goal is not just to create archives. The goal is to prove that a
usable copy exists outside the HAOS VM and can be inspected.

## Backup Categories

| Category | Why it matters |
| --- | --- |
| Home Assistant backup archive | Restores HA configuration, add-ons, dashboards, automations, and integrations |
| Copy outside the HAOS VM | Protects against VM-level loss |
| Host configuration notes | Rebuilds host services, access paths, and storage sharing |
| Service configuration templates | Recreates future host-side services without secrets |
| External drive data policy | Explains what the large storage is and is not used for |
| Private operational docs | Holds exact values that cannot be public |
| Secrets backup policy | Keeps credentials recoverable without committing them |

## MyBook Role

The external drive is a good local backup target for Home Assistant backup
copies and large archives. It is not an off-site backup by itself because it is
attached to the same host and location.

When the drive is used as a backup target:

1. Power it on through the guarded path.
2. Mount it at the expected private location.
3. Confirm the backup destination is available.
4. Copy or create the backup.
5. Verify archive size and metadata.
6. Safely unmount and power off if the drive is operated on demand.

## What Not To Commit

- Home Assistant backup archives.
- Secrets.
- Tokens.
- Private paths.
- Full dashboard exports.
- Full entity inventory.
- Recovery commands that directly operate the live host.

## Freshness Checks

A backup freshness check should answer:

- When was the latest successful backup?
- Is it inside the expected age threshold?
- Does an outside-VM copy exist?
- Is the copy non-zero size?
- Can the archive listing or manifest be read?
- Was the destination available when the check ran?

## Retention

Use a simple retention policy first:

- keep recent automatic backups,
- keep a few known-good manual backups before major changes,
- keep at least one copy outside the VM,
- avoid keeping the only backup on storage that is always writable from daily
  clients.

