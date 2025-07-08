[< Previous: 19. Internationalization & Localization](19_internationalization_and_localization.md) | [Back to TOC](../README.md) (main documentation) | [Next: 21. Duration Reference](21_duration_reference.md)

# 20. Event Reference for Triggered Abilities

This chapter provides a structured list of event identifiers usable in MCD trigger conditions (`condition.event = ...`). Events are grouped by origin: core rule events and, where relevant, extended/engine-level events.

Use these event names in triggered ability conditions, for example:

```lua
triggered = {
  {
    condition = { event = "SpellCast", by = "Opponent" },
    effect = { type = "Draw", amount = 1 }
  }
}
```

### A. Core Rule Events (from MTG Comprehensive Rules)

| Event               | Description                                         |
| ------------------- | --------------------------------------------------- |
| `SpellCast`         | A spell is cast                                     |
| `PermanentEnters`   | A permanent enters the battlefield                  |
| `PermanentLeaves`   | A permanent leaves the battlefield                  |
| `Dies`              | A creature or permanent goes from battlefield to GY |
| `BecomesTapped`     | A permanent becomes tapped                          |
| `BecomesUntapped`   | A permanent becomes untapped                        |
| `BecomesTarget`     | A permanent becomes the target of a spell/ability   |
| `Attacks`           | A creature is declared as attacker                  |
| `Blocks`            | A creature is declared as blocker                   |
| `CombatDamageDealt` | Combat damage is assigned/resolved                  |
| `DrawStep`          | Start of draw step                                  |
| `UpkeepStep`        | Start of upkeep step                                |
| `EndStep`           | Start of end step                                   |
| `CardDrawn`         | A card is drawn                                     |
| `LifeChanged`       | A player gains or loses life                        |
| `DamageDealt`       | A permanent or player is dealt damage               |
| `CounterAdded`      | A counter is added to a permanent                   |
| `CounterRemoved`    | A counter is removed from a permanent               |

---

[< Previous: 19. Internationalization & Localization](19_internationalization_and_localization.md) | [Back to TOC](../README.md) (main documentation) | [Next: 21. Duration Reference](21_duration_reference.md)
