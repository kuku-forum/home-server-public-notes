# Architecture

This project uses a small personal-server layout centered on a Mac mini.

```text
User devices
  -> public HTTPS access for Home Assistant
  -> private admin network for maintenance
      -> Mac mini host
          -> Home Assistant OS virtual machine
              -> Home Assistant
              -> MQTT broker
              -> Zigbee2MQTT
                  -> network Zigbee coordinator
                      -> Zigbee devices
          -> local SMB storage
          -> host-side helper services
```

## Layers

| Layer | Role |
| --- | --- |
| Physical network | Home LAN, client devices, Zigbee coordinator, smart-home devices |
| Host | Mac mini running virtualization, helper services, storage sharing, and private admin access |
| VM | Home Assistant OS appliance environment |
| Home Assistant | Dashboards, automations, integrations, scripts, and device registry |
| Device bridge | MQTT and Zigbee2MQTT translate Zigbee devices into Home Assistant entities |
| Access | Public Home Assistant access and private maintenance access are kept separate |

## Main Pattern

The Mac mini is the always-on hub. Home Assistant OS is isolated in a VM so the
smart-home appliance layer stays separate from host-level duties such as file
sharing, display helpers, and maintenance scripts.

The Zigbee coordinator is network-attached rather than passed through as a USB
device. That makes the Zigbee layer less dependent on VM USB passthrough and
allows the coordinator to be placed where radio coverage is better.

## Trust Boundaries

| Boundary | Public-safe description |
| --- | --- |
| Internet to Home Assistant | Public access is routed through a managed HTTPS tunnel and still requires Home Assistant login |
| Administration to host | Shell and screen access are kept on a private network, not exposed directly to the public internet |
| Host to VM | Host helpers support access, monitoring, and recovery, but Home Assistant remains inside the VM |
| Home Assistant to devices | Automations can control real devices, so entity naming and automation review matter |
| Zigbee to Home Assistant | Zigbee2MQTT and MQTT form the bridge between physical Zigbee devices and Home Assistant |

## Why This Shape

This setup prioritizes practical reuse of existing hardware, clear separation of
daily access and maintenance access, and enough documentation to recover from
common failures.

It is not intended to be a hardened enterprise server design. The tradeoff is
accepted because this is a personal home-server environment.
