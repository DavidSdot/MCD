[< Previous: 1. Introduction](01_introduction.md) | [Back to TOC](../README.md) (main documentation) | [Next: 3. Card-Level Fields](03_card-level_fields.md)

# 2. General Structure

Every MCD card definition must follow this basic structure:

```lua
return {
    id = "UUID",           -- Scryfall ID or similar
    layout = "normal",      -- e.g. transform, split, adventure
    faces = {
        {
            name = "Card Name",
            oid = "UUID",         -- Oracle face ID
            mana_cost = "{2}{W}{W}",
            types = {"Legendary", "Creature"},
            subtypes = {"Angel"},
            power = 4,
            toughness = 4,
            abilities = {
                triggered = { ... },
                activated = { ... },
                static = { ... }
            }
        }
    }
}

---

[< Previous: 1. Introduction](01_introduction.md) | [Back to TOC](../README.md) (main documentation) | [Next: 3. Card-Level Fields](03_card-level_fields.md)
