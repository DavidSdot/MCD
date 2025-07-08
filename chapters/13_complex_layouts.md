[< Previous: 12. Special Cast Types](12_special_cast_types.md) | [Back to TOC](../README.md) (main documentation) | [Next: 14. Keywords & Game Mechanics](14_keywords_and_game_mechanics.md)

# 13. Complex Layouts

MCD supports all official MTG layout types, including Split, Adventure, Modal DFC, Transform, Meld, Saga, and more. Cards with multiple faces are represented as `faces = {}` arrays with layout metadata.

Each layout has rules for how faces interact with casting, resolution, and zones. MCD uses `layout` to signal the engine how the faces are interpreted (for example, only one is castable, both are combined, etc.).

Supported layouts include:

- **Split cards:** each face is a spell
- **Modal DFCs:** player chooses which face to play
- **Adventure:** face 1 = spell, face 2 = creature
- **Meld:** `layout = "meld"`, references for `meld_with`
- **Mutate, Saga, Class, Case:** treated as multi-step abilities or counters

**Example: Split Card**

```lua
return {
  id = "12345678-aaaa-bbbb-cccc-1234567890ab",
  layout = "split",
  faces = {
    {
      name = "Fire",
      mana_cost = "{1}{R}",
      types = {"Instant"},
      abilities = {
        spell = {
          effect = { type = "Damage", amount = 2, target = "AnyTarget" }
        }
      }
    },
    {
      name = "Ice",
      mana_cost = "{1}{U}",
      types = {"Instant"},
      abilities = {
        spell = {
          effect = { type = "Tap", target = "TargetPermanent" }
        }
      }
    }
  }
}
```

---

[< Previous: 12. Special Cast Types](12_special_cast_types.md) | [Back to TOC](../README.md) (main documentation) | [Next: 14. Keywords & Game Mechanics](14_keywords_and_game_mechanics.md)
