[< Previous: 22. Dynamic Value Reference](22_dynamic_value_reference.md) | [Back to TOC](../README.md) (main documentation) | [Next: 24. Keyword Abilities Reference](24_keyword_abilities_reference.md)

# 23. Targets & Named References

This section defines how `target` and `assign_to` are used within effect sequences and abilities.  
Targets are evaluated at effect resolution, using either predefined names, explicit strings, or dynamically assigned references.

### `target` Field

The `target` field specifies which object (card, player, token, zone, etc.) is affected by the effect. It supports the following reference types:

| Target String                    | Meaning                                              |
| -------------------------------- | ---------------------------------------------------- |
| `AnyTarget`                      | Any valid target (creature, planeswalker, or player) |
| `TargetCreature`                 | A targeted creature                                  |
| `TargetPlayer`                   | A player chosen as target                            |
| `Self`                           | Refers to the object this ability belongs to         |
| `Controller`                     | The controller of the current object                 |
| `Opponent`                       | An opponent of the controller                        |
| `TargetPlayer.Graveyard.TopCard` | Top card of target player's graveyard                |
| Custom Variable                  | Any name previously created via `assign_to = "Name"` |

### `assign_to` Field

Some effects can store the result of a computation or selection into a named reference. This allows later effects to use that value.

- `assign_to` defines a name in the current ability context.
- The scope is **local to the surrounding effect block** (not global).
- Subsequent steps can reference this name via `target`.

### Example

```lua
{
  type = "SearchLibrary",
  controller = "Controller",
  max = 4,
  filters = { type = "Card" },
  assign_to = "SelectedCards" -- assign selected cards to a reference
},
{
  type = "Reveal",
  target = "SelectedCards"    -- use the named reference as the target
}
```

### Notes

- Referenced names must match exactly (case-sensitive)
- It is recommended to use consistent naming conventions (e.g. `Chosen`, `Revealed`, `Targeted`, `Result`, etc.)
- Reusing names within a block overwrites previous assignments
- Assignments are not accessible across multiple ability sections

---

[< Previous: 22. Dynamic Value Reference](22_dynamic_value_reference.md) | [Back to TOC](../README.md) (main documentation) | [Next: 24. Keyword Abilities Reference](24_keyword_abilities_reference.md)
