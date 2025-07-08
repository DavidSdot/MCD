[< Previous: 9. Zones & Targets](09_zones_and_targets.md) | [Back to TOC](../README.md) (main documentation) | [Next: 11. Tokens](11_tokens.md)

# 10. Conditional Logic & Choice

MCD allows conditions to gate effects, triggers, and costs. Conditions may refer to game state (such as counters or life totals), past events (like damage dealt), or logical evaluations (e.g., `CreatureCount > 3`).

Choices let players make decisions between multiple effect options. A choice block defines how many options may be selected and what effects result. Choices can be simple (modal) or interactive (e.g., during resolution).

### Condition Examples

- Event-driven: `SpellIsCast`, `PermanentEnters`
- Comparison: `Damage > 3`, `CreatureCount > 2`
- State: `Self.HasKeyword("Flying")`

**Example for a nested condition:**

```lua
condition = {
  any_of = {
    { type = "LifeTotal", operator = "LT", value = 5 },
    {
      all_of = {
        { type = "CreatureCount", operator = "GT", value = 2 },
        { type = "HasCounter", counter = "+1/+1", operator = "GE", value = 3 }
      }
    }
  }
}
```

### Choice Example

```lua
choice = {
  min = 1,
  max = 2,
  options = {
    { label = "Draw", effect = { type = "Draw", amount = 2 } },
    { label = "Gain Life", effect = { type = "GainLife", amount = 4 } }
  }
}
```

---

[< Previous: 9. Zones & Targets](09_zones_and_targets.md) | [Back to TOC](../README.md) (main documentation) | [Next: 11. Tokens](11_tokens.md)
