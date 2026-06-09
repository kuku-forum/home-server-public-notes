# Architecture Decisions

This page summarizes the major decisions without publishing operational values.

## Use A Mac mini As The Host

The Mac mini was available, quiet, efficient, and powerful enough for the job.
It can run virtualization, helper services, file sharing, and local maintenance
tools.

Tradeoff: macOS is not a headless-first server OS, and some helper services may
depend on user-session behavior.

## Run Home Assistant OS In A VM

Home Assistant OS gives a clean appliance-style experience with Supervisor,
add-ons, backups, and a familiar operational model.

Tradeoff: the VM layer adds another place where networking, boot behavior, and
recovery can fail.

## Keep Public Access And Admin Access Separate

Home Assistant daily use is reachable through a managed HTTPS path. Shell,
screen, and maintenance access remain private.

Tradeoff: there are two access models to document and monitor.

## Use A Network Zigbee Coordinator

A network coordinator avoids relying on VM USB passthrough and can be placed for
better radio coverage.

Tradeoff: coordinator network reliability matters, and the MQTT/Zigbee2MQTT
stack needs careful documentation.

## Use A Private Documentation Repository As Source Of Truth

The real operating documentation is private because it contains details that
should not be public.

Tradeoff: this public repo can only be a sanitized overview, not a recovery
manual.

## Attach External Storage To The Host

The external drive is managed by the Mac mini host and shared over SMB.

Tradeoff: the host must be running and healthy for the share to work, and the
drive is not a full NAS or redundant storage array.

## Prefer Conservative Automation Changes

Fast physical controls should stay on the integration path that is most
reliable for that device. Migration to Zigbee2MQTT is gradual rather than
all-or-nothing.

Tradeoff: the system may keep multiple integrations during migration, so naming
and cleanup discipline matter.
