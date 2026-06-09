# Backup Check Script Notes

This folder is for public-safe notes about backup verification scripts.

The real script should live in the private operating environment. Public
examples must use placeholders only.

The check should answer:

- Is the latest Home Assistant backup recent?
- Does a copy exist outside the HAOS VM?
- Is the copy non-zero size?
- Can the archive listing be read?
- Can the backup manifest be inspected?
- Was the external drive available when expected?

Do not commit backup archives, backup IDs, real paths, token files, or restore
commands.

