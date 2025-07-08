[< Previous: 4. Face-Level Fields](04_face-level_fields.md) | [Back to TOC](../README.md) (main documentation) | [Next: 6. Costs](06_costs.md)

# 5. Abilities

Abilities define all rule-relevant behaviors that a card can have. In MCD, abilities are grouped as `triggered`, `activated`, or `static` depending on how and when they apply.

- **Triggered Abilities** respond to game events and execute one or more effects.
- **Activated Abilities** are player-controlled and require costs.
- **Static Abilities** apply continuously or conditionally as long as the source is on the battlefield or in a relevant zone.

All ability types reference the same effect system and can include costs, conditions, and optional target filters.

### 5.1 Triggered Abilities

```lua
triggered = {
  {
    condition = { event = "SpellIsCast", by = "Opponent" },
    effect = { type = "Draw", amount = 1 }
  }
}
```

### 5.2 Activated Abilities

```lua
activated = {
  {
    cost = {
      { type = "mana", amount = "{1}{U}" },
      { type = "tap" }
    },
    effect = { type = "Draw", amount = 1 }
  }
}
```

### 5.3 Static Abilities

Applied continuously or as conditionals.

```lua
static = {
  {
    condition = { type = "HasCounter", counter = "+1/+1", operator = "GE", value = 3 },
    effect = { type = "Grant", keyword = "Hexproof" }
  }
}
```

---

[< Previous: 4. Face-Level Fields](04_face-level_fields.md) | [Back to TOC](../README.md) (main documentation) | [Next: 6. Costs](06_costs.md)
