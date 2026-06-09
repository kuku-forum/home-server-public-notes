# Restore Drill

Restore rehearsal should prove recoverability without damaging the live system.

## Non-Destructive Drill

For routine checks:

1. Create or select a recent Home Assistant backup.
2. Copy it outside the HAOS VM.
3. Confirm the archive is present.
4. Confirm the archive is non-zero size.
5. Read the archive listing.
6. Inspect the backup manifest.
7. Record the result in private operational notes.

This does not restore the live system.

## Full Restore Drill

A full restore should use a separate test VM or an actual disaster recovery
situation. Running a full restore on the live Home Assistant instance can
overwrite configuration and restart services.

## What To Record Privately

- Backup name or private identifier.
- Creation time.
- Copy destination.
- Archive size.
- Manifest result.
- Restore test target.
- Time required.
- Problems found.

Do not publish backup IDs, paths, archive contents, or restore commands.

## Success Criteria

A restore drill is successful when:

- the backup can be found,
- the backup can be read,
- the manifest is valid,
- the expected add-ons or components are represented,
- the operator knows where to restore it from,
- the live system was not damaged during rehearsal.

