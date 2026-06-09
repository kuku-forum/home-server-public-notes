# Storage Script Notes

This folder is for public-safe notes about storage helpers.

The live external-drive helper is private because it contains real operational
values. Public examples should only demonstrate the pattern:

1. Check active writes.
2. Check open files.
3. Unmount or eject.
4. Power off only after success.
5. Report failure without forcing power off.
6. On power-on, wait for disk, mount it, and verify storage availability.

Use placeholder examples only:

- `storage-power.example.sh`
- `storage-status.template.yaml`

