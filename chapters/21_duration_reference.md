[< Previous: 20. Event Reference for Triggered Abilities](20_event_reference_for_triggered_abilities.md) | [Back to TOC](../README.md) (main documentation) | [Next: 22. Dynamic Value Reference](22_dynamic_value_reference.md)

# 21. Duration Reference

The `duration` field determines how long a continuous effect applies. It is used in effects like `Boost`, `Grant`, `SetPower`, and others that temporarily modify game state.  
Only the allowed values below are supported.

**Example:**

```lua
effect = { type = "Boost", power_delta = 2, toughness_delta = 2, duration = "UntilEndOfTurn" }
```

### Allowed Values

| Value                | Description                                                   |
| -------------------- | ------------------------------------------------------------- |
| `UntilEndOfTurn`     | Effect ends at the cleanup step of the current turn           |
| `UntilNextTurn`      | Effect ends at the beginning of the controller's next turn    |
| `WhileOnBattlefield` | Effect lasts as long as the source remains on the battlefield |
| `Permanent`          | Effect is permanent and does not expire                       |
| `WhileCondition`     | Effect lasts only while a specific condition is met           |

These durations are derived from MTG Comprehensive Rules 611–613 and are used consistently across all applicable effects.

Custom or non-standard duration values are not allowed.

---

[< Previous: 20. Event Reference for Triggered Abilities](20_event_reference_for_triggered_abilities.md) | [Back to TOC](../README.md) (main documentation) | [Next: 22. Dynamic Value Reference](22_dynamic_value_reference.md)
