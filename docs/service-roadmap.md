# Service Roadmap

This roadmap favors stability, recoverability, and privacy over adding many
services quickly.

## Recommended Order

1. Finish operations docs.
2. Finish monitoring docs.
3. Verify backup strategy.
4. Document storage power control.
5. Add service layout.
6. Add next-services roadmap.
7. Install or finalize Uptime Kuma.
8. Install or finalize Netdata or Glances.
9. Add backup verification script.
10. Add Immich.
11. Add Plex or Jellyfin.
12. Add Paperless-ngx.
13. Add n8n.
14. Add Open WebUI and Ollama.
15. Add vector search or personal RAG.
16. Add a read-only home/server summary agent.

## Decision Rules

- Stable beats flashy.
- Recoverable beats complex.
- Private beats public.
- Dashboard visibility beats hidden scripts.
- Documentation beats memory.
- Small safe increments beat large install batches.

## Delay Rules

Delay a service if:

- backup is unclear,
- exposure is public by default,
- it needs credentials that cannot be safely stored yet,
- it stores important data without a restore plan,
- it consumes enough resources to threaten Home Assistant,
- it depends on the external drive being always on when the drive is normally
  operated on demand.

