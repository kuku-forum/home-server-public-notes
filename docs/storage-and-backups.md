# Storage And Backups

An external hard drive is attached to the Mac mini host and shared over SMB for
local authenticated access.

## Storage Pattern

```text
Client devices
  -> LAN or private network
      -> Mac mini host
          -> SMB service
              -> external hard drive

Home Assistant OS VM
  -> optional network-storage backup target
      -> host SMB share
```

The drive is managed by the host instead of being passed directly into the Home
Assistant OS VM. This keeps file sharing separate from Home Assistant add-ons,
Supervisor behavior, and VM restarts.

## Why Host-managed Storage

- The host can mount, unmount, repair, and inspect the disk directly.
- SMB is widely supported by macOS, Windows, iOS, iPadOS, and Android clients.
- Home Assistant backup copies can be stored outside the VM.
- Storage can be powered or mounted only when needed.

## Safe Power Approach

The external drive may be controlled through a smart plug, but raw power toggles
are not exposed as normal daily switches.

Safe shutdown requires:

1. confirm no important write is active
2. unmount or eject the filesystem on the host
3. power off only after unmount succeeds
4. report failure instead of forcing power off

Power-on requires:

1. turn on the plug
2. wait for the disk to appear
3. mount it at the expected host location
4. verify the SMB share is available

## Backup Approach

Home Assistant backups are separate from host backups. A host disk backup alone
does not replace a Home Assistant backup archive.

The intended model is:

- keep Home Assistant backups enabled
- copy important backups outside the VM
- periodically rehearse restore steps without destroying the live system
- avoid using GitHub for secrets or full Home Assistant backups
- keep at least one backup path that is not always writable from daily clients

## Not Included

This public repo does not include share names, network addresses, disk serials,
mount paths, credentials, backup IDs, or filesystem command output.
