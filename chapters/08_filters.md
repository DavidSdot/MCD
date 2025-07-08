[< Previous: 7. Effects](07_effects.md) | [Back to TOC](../README.md) (main documentation) | [Next: 9. Zones & Targets](09_zones_and_targets.md)

# 8. Filters

Filters define how the engine selects cards or players for evaluation. They are used in targeting, cost requirements, triggers, and conditional logic.

Each filter consists of one or more fields specifying types, conditions, and comparisons. Filters can be combined via `all_of`, `any_of`, or negated. They support reference paths (e.g., `TargetPlayer.Graveyard`) and dynamic values (e.g., life total, counter counts).

Used to narrow targets or apply effects:

```lua
filter = {
  type = "Creature",
  controller = "Opponent",
  power = { operator = "GT", value = 3 }
}
```

**Example for nested filters:**

```lua
filter = {
  all_of = {
    { type = "Creature" },
    { controller = "Opponent" },
    { power = { operator = "GT", value = 3 } }
  }
}
```

Filters support chaining, logic operators (AND/OR), and nested conditions.

---

[< Previous: 7. Effects](07_effects.md) | [Back to TOC](../README.md) (main documentation) | [Next: 9. Zones & Targets](09_zones_and_targets.md)
