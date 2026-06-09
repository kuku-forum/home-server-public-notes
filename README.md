# Home Server Public Notes

This repository is a sanitized public overview of a personal home-server project.
It explains what was built and why, without publishing live addresses,
credentials, hostnames, internal paths, recovery commands, or device-specific
identifiers.

## What Was Built

- A Mac mini is used as the main home-server host.
- Home Assistant OS runs in a virtual machine.
- Home Assistant provides the main automation, dashboard, and device-control
  surface.
- Zigbee devices are bridged through a network coordinator, Zigbee2MQTT, and
  MQTT.
- Remote access is split into two categories:
  - a public HTTPS path for normal Home Assistant use
  - a private administration path for shell, screen, and maintenance access
- A phone-first dashboard and a wall-mounted tablet dashboard were built for
  daily control.
- An external hard drive is shared as a local, authenticated SMB storage area.
- Operational notes, architecture decisions, and security tradeoffs are
  documented in a private source-of-truth repository.

## Public Scope

This repo intentionally describes patterns, not live infrastructure.

Included:

- high-level architecture
- design decisions
- Home Assistant dashboard and automation approach
- Zigbee migration notes
- storage and backup approach
- security principles and tradeoffs

Excluded:

- real public domains and URLs
- LAN, VPN, or tailnet addresses
- MAC addresses, coordinator IDs, serial URLs, and exact port maps
- access tokens, passwords, private keys, and secret file locations
- runnable recovery commands
- full Home Assistant entity inventory
- full dashboard exports, backups, scripts, and LaunchAgent files

## Read The Notes

- [Architecture](docs/architecture.md)
- [Home Assistant](docs/home-assistant.md)
- [Zigbee](docs/zigbee.md)
- [Dashboards](docs/dashboards.md)
- [Storage And Backups](docs/storage-and-backups.md)
- [Security Scope](docs/security-scope.md)
- [Architecture Decisions](docs/decisions.md)

## Status

The foundation is working: host, VM, Home Assistant, Zigbee bridge, dashboards,
private admin access, public Home Assistant access, and local storage sharing
are in place.

The private operational documentation remains the source of truth. This public
repo is only a safe overview.
