# Service Health

This page defines what should be observable. It does not publish live endpoints.

## Health Targets

| Target | Expected signal | Where it should be visible |
| --- | --- | --- |
| Home Assistant web | reachable and authenticated | daily dashboard and monitor |
| HAOS VM | running | private admin check |
| MQTT broker | accepting connections | admin check and HA status |
| Zigbee2MQTT | bridge connected | HA status and admin dashboard |
| Zigbee permit-join | normally closed | admin or system dashboard |
| Public Home Assistant access | reachable through public route | monitor |
| Private admin access | reachable through private route | monitor |
| SMB share | reachable from trusted client | monitor or manual check |
| External drive mount | mounted only when expected | HA system view |
| External drive power | on only when needed | HA system view |
| Disk usage | below warning threshold | HA system view |
| Backup age | recent | HA system view |
| Host uptime | current | HA system view |

## Status Categories

Use simple states:

- OK: expected and healthy.
- Warning: usable but needs attention soon.
- Failed: unavailable or unsafe.
- Maintenance: intentionally changed by the operator.
- Unknown: no current signal.

Unknown should not be treated as OK.

## Dashboard Placement

Daily dashboards should show summary status and warnings. Admin dashboards should
show detailed checks and deliberate actions.

