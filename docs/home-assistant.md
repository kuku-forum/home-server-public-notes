# Home Assistant

Home Assistant is the main control plane for the home. It owns dashboards,
automations, scripts, integrations, and the device/entity registry.

## Current Role

Home Assistant connects several classes of integrations:

- Zigbee2MQTT and MQTT for Zigbee sensors, buttons, and compatible devices
- vendor integrations for lights, plugs, appliances, bridges, and media devices
- mobile-app sensors for presence and device context
- helper entities and scripts for dashboard actions
- host-side status sensors for server health cues

The current system is treated as an entity-driven setup. Dashboards and
automations reference stable entity IDs rather than device IDs wherever possible.

## Operating Principles

- Keep current docs focused on the live operating state.
- Record old experiments and failure logs outside the public overview.
- Prefer native or local control paths when a device appears through multiple
  integrations.
- Keep risky controls, restart actions, pairing actions, and maintenance buttons
  away from casual daily-control screens.
- Use clear naming for rooms, device roles, and automation intent.
- Do not edit Home Assistant internal storage files directly when an API, MCP,
  or UI path is available.

## Automation Approach

Automations are documented by purpose rather than by raw YAML dump. The useful
questions are:

- What triggers it?
- What conditions must be true?
- What does it control?
- Is it a daily automation, a safety fallback, or a deprecated no-op?

Examples of active automation categories:

- presence-driven lighting
- humidity and ventilation control
- bathroom and hallway lighting behavior
- Zigbee permit-join safety
- mobile presence mode notifications
- system-status and maintenance cues

## What Is Not Published Here

This public repo does not include full entity IDs, full automation exports,
dashboard JSON, exact device inventory, or live registry snapshots.
