[< Previous: 8. Filters](08_filters.md) | [Back to TOC](../README.md) (main documentation) | [Next: 10. Conditional Logic & Choice](10_conditional_logic_and_choice.md)

# 9. Zones & Targets

Zones define where cards are located in the game: hand, battlefield, graveyard, exile, etc.  
Targets describe which card or player is the subject of an action.

MCD supports full zone logic for all legal transitions (e.g., hand → battlefield).  
Targeting paths can use dotted notation (e.g., `TargetPlayer.Graveyard.TopCard`) and support both direct and dynamic selection. Zones are referenced in many effect types and trigger conditions.

**Zones are referenced with:**
- `from_zone`, `to_zone`
- `TargetPlayer.Graveyard.TopCard`

**Common zone keywords:**

| Keyword       | Description                     |
|---------------|---------------------------------|
| `Library`     | Player's deck                   |
| `Graveyard`   | Discard pile                    |
| `Hand`        | Player's hand                   |
| `Exile`       | Exile zone                      |
| `Battlefield` | Cards in play                   |
| `Stack`       | Spells/abilities in process     |
| `Command`     | Command zone (Commander, emblems, etc.) |

**Example:**

```lua
effect = {
  type = "MoveCard",
  target = "TargetCreature",
  from_zone = "Battlefield",
  to_zone = "Exile"
}
```

---

[< Previous: 8. Filters](08_filters.md) | [Back to TOC](../README.md) (main documentation) | [Next: 10. Conditional Logic & Choice](10_conditional_logic_and_choice.md)
