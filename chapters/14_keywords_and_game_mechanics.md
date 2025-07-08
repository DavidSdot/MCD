[< Previous: 13. Complex Layouts](13_complex_layouts.md) | [Back to TOC](../README.md) (main documentation) | [Next: 15. Design Philosophy](15_design_philosophy.md)

# 14. Keywords & Game Mechanics

MCD supports rule-based mechanics like Monarch, Initiative, Dungeons, Emblems, Roles, and counters. These are represented using specific effect types (`BecomeMonarch`, `CreateEmblem`, `VentureIntoDungeon`, etc.) and engine-handled status flags.

Mechanics with permanent game effect (like Monarch control) or external state (like Dungeon progress) are always resolved through dedicated rule systems tied into the engine core.

**Supported mechanics include:**

- Monarch, Initiative
- Emblems, Dungeons
- Counters (loyalty, defense, lore, etc.)
- Face-down tech: Morph, Disguise, Foretell, etc.
- All abilities definable in static / triggered form

**Example for granting Monarch:**
```lua
effect = { type = "BecomeMonarch", target = "TargetPlayer" }
```

**Example for venturing into the dungeon:**
```lua
effect = { type = "VentureIntoDungeon" }
```

**Example for creating an emblem:**
```lua
effect = { type = "CreateEmblem", emblem = { ... } }
```

Face-down mechanics (like Morph, Disguise, or Foretell) are modeled with engine flags and status, and may use `face_down = true` or similar fields.

---

[< Previous: 13. Complex Layouts](13_complex_layouts.md) | [Back to TOC](../README.md) (main documentation) | [Next: 15. Design Philosophy](15_design_philosophy.md)
