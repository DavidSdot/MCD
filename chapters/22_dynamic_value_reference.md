[< Previous: 21. Duration Reference](21_duration_reference.md) | [Back to TOC](../README.md) (main documentation) | [Next: 23. Targets & Named References](23_targets_and_named_references.md)

# 22. Dynamic Value Reference

Certain numeric fields in MCD (e.g., `amount`, `power`, `counter`, etc.) can be defined as dynamic values instead of fixed literals. This allows the engine to evaluate context-sensitive quantities during resolution.

Dynamic values are allowed only for fields explicitly documented as "dynamic-capable". (You cannot use them everywhere.)

### Format

```lua
amount = {
  type = "CreatureCount",
  controller = "Controller",
  filter = { ...optional filter... }
}
```

### Common Dynamic Types

| Type                | Description                                     |
| ------------------- | ----------------------------------------------- |
| `CreatureCount`     | Number of creatures matching an optional filter |
| `CardCount`         | Number of cards in a zone (e.g., `Graveyard`)   |
| `CounterValue`      | Number of counters of a given type on a target  |
| `LifeTotal`         | Current life total of a player                  |
| `HandSize`          | Number of cards in a player's hand              |
| `PowerOfTarget`     | Current power of a referenced creature          |
| `ToughnessOfTarget` | Current toughness of a referenced creature      |
| `LandsControlled`   | Count of lands controlled by a player           |
| `SpellCMC`          | Converted mana cost of a spell                  |

### Example: Dynamic Draw

```lua
amount = {
  type = "CreatureCount",
  controller = "Controller",
  filter = { subtype = "Elf" }
}
```

Dynamic values are evaluated **at the time of resolution**. When used inside effects like `Draw`, `Damage`, `Boost`, or conditional conditions, they must follow this structure.

---

[< Previous: 21. Duration Reference](21_duration_reference.md) | [Back to TOC](../README.md) (main documentation) | [Next: 23. Targets & Named References](23_targets_and_named_references.md)
