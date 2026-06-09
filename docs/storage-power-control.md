# Storage Power Control

The external drive can be operated on demand, but storage power must be guarded.
Raw power toggles are not safe daily controls.

## Safe Shutdown Pattern

```text
Home Assistant request
  -> host-side helper
      -> check backup/write activity
      -> check open files
      -> unmount or eject filesystem
      -> only then turn off the smart plug
      -> publish success or failure status
```

If unmount fails, power stays on.

## Safe Power-On Pattern

```text
Home Assistant request
  -> turn on smart plug
  -> wait for disk to appear
  -> mount at expected private path
  -> verify storage path
  -> verify SMB availability
  -> publish success or failure status
```

## Dashboard Policy

The daily dashboard may show storage state. The actual storage power action
should live on a system or admin view and should use the guarded helper.

The raw smart-plug switch should not be treated like a normal light switch.

## Public / Private Split

Public docs can describe:

- guarded request flow,
- unmount-before-power-off rule,
- failure keeps power on,
- mount and SMB verification,
- dashboard separation.

Private docs keep:

- actual helper names,
- actual entity IDs,
- actual smart-plug entity,
- actual mount path,
- actual SMB share name,
- actual script path,
- actual logs,
- manual recovery commands.

