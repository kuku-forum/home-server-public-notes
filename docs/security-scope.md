# Security Scope

This public repo is intentionally limited. It is meant to show the architecture
and lessons learned without creating a target map for the live home network.

## Published

- general architecture
- component roles
- broad security model
- tradeoffs and operating principles
- non-sensitive lessons learned

## Not Published

- real domain names or public hostnames
- LAN, VPN, or tailnet IP addresses
- MAC addresses and hardware identifiers
- exact port maps and tunnel origins
- token file paths or secret locations
- Home Assistant access tokens
- Cloudflare tunnel tokens
- SSH keys or private key material
- account names, passwords, or password hints
- full script, LaunchAgent, or dashboard source
- recovery commands that directly operate the live host

## Security Principles

- No router port forwarding for management services.
- Public access is limited to the Home Assistant web surface.
- Administrative access stays on a private network.
- Home Assistant credentials and multi-factor authentication matter because the
  login page can be internet-reachable.
- SMB is kept authenticated and is not published directly to the internet.
- Secrets are never committed to documentation.
- Public notes are written as patterns, not operational instructions.

## Known Tradeoffs

The design favors a working personal home-server foundation over perfect
hardening. Some host services depend on a logged-in desktop session. Some
storage and backup workflows are pragmatic rather than enterprise-grade.

Those tradeoffs are acceptable only because this is a private home environment
with a small operator set.
