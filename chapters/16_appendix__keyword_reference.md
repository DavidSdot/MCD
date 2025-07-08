[< Previous: 15. Design Philosophy](15_design_philosophy.md) | [Back to TOC](../README.md) (main documentation) | [Next: 17. Full Example: Complex Card Definition](17_full_example__complex_card_definition.md)

# 16. Appendix: Keyword Reference

This appendix lists commonly used MCD effect keywords along with their meaning and parameters. This list is not exhaustive but covers the majority of use cases.

| Keyword         | Description                                                                            | Common Parameters                            |
| --------------- | -------------------------------------------------------------------------------------- | -------------------------------------------- |
| `Draw`          | Draw cards from library (supports dynamic `amount`)                                    | `amount`                                     |
| `Discard`       | Discard cards from hand                                                                | `amount`, `random`, `target`                 |
| `Exile`         | Remove cards from the game                                                             | `target`                                     |
| `Destroy`       | Move a permanent to its controller's graveyard                                         | `target`                                     |
| `CreateToken`   | Put a token onto the battlefield                                                       | `token`, `attached_to`, `controller`         |
| `Boost`         | Modify power/toughness temporarily (supports dynamic `power_delta`, `toughness_delta`) | `power_delta`, `toughness_delta`, `duration` |
| `Grant`         | Give keyword ability to a card                                                         | `keyword`, `duration`, `target`              |
| `GainLife`      | Increase player's life total                                                           | `amount`, `target`                           |
| `LoseLife`      | Decrease player's life total                                                           | `amount`, `target`                           |
| `Damage`        | Deal damage to object or player (supports dynamic `amount`)                            | `amount`, `target`, `is_combat`              |
| `MoveCard`      | Move card between zones                                                                | `from_zone`, `to_zone`, `target`             |
| `Scry`          | Look at top cards of library                                                           | `amount`, `target`                           |
| `Explore`       | Reveal top card and decide to draw/put lands                                           | `target`                                     |
| `Venture`       | Advance dungeon progress                                                               | `target`, `dungeon`                          |
| `SetPower`      | Set base power/toughness                                                               | `power`, `toughness`, `duration`             |
| `ModifyLoyalty` | Increase or decrease loyalty of a planeswalker                                         | `amount`, `target`                           |
| `AddCounter`    | Place counters on permanent (supports dynamic `amount`)                                | `counter_type`, `amount`, `target`           |
| `RemoveCounter` | Remove counters from permanent                                                         | `counter_type`, `amount`, `target`           |
| `ReturnToHand`  | Return card to owner's hand                                                            | `target`                                     |
| `CopySpell`     | Copy a spell or ability                                                                | `target`, `controller`                       |

(Excerpt, see rules for full list)

**Example:**
```lua
effect = { type = "Draw", amount = 2 }
```

---

[< Previous: 15. Design Philosophy](15_design_philosophy.md) | [Back to TOC](../README.md) (main documentation) | [Next: 17. Full Example: Complex Card Definition](17_full_example__complex_card_definition.md)
