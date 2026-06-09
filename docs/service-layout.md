# Service Layout

Future host-side services should be added in a predictable structure instead of
as one-off experiments.

## Target Shape

```text
homelab/
  stacks/
    uptime-kuma/
    netdata-or-glances/
    immich/
    plex-or-jellyfin/
    paperless-ngx/
    n8n/
    open-webui/
  scripts/
    health/
    backup/
    storage/
  docs/
    operations/
    services/
  secrets/
```

This is a private host layout. The public repo should only include sanitized
examples and documentation.

## Service README Template

Each service should document:

- purpose,
- exposure: public, private, LAN-only, or disabled,
- data touched,
- backup requirement,
- Home Assistant integration,
- restart method,
- restore notes,
- security caution.

## Secrets Rule

Use examples only:

- `.env.example`
- `config.example.yaml`
- `*.template.yaml`
- `*.example.sh`

Never commit real `.env` files, passwords, tokens, private domains, private
paths, or full volume mappings.

## Exposure Rule

Default all management services to private or LAN-only. Public exposure should
be a separate decision with authentication, update, and monitoring plans.

