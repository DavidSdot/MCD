[< Previous: 5. Abilities](05_abilities.md) | [Back to TOC](../README.md) (main documentation) | [Next: 7. Effects](07_effects.md)

# 6. Costs

Each activated ability or spell in MCD may have one or more costs that must be paid to activate it or cast it.

Costs define what must be paid or performed in order to activate an ability or cast a spell. MCD supports simple mana costs as well as complex cost compositions, including discards, sacrifices, tapping, and even conditional restrictions.

Costs are declared as arrays of structured entries. The engine handles validation and enforcement of all cost types, whether simple or compound. Alternative costs and special conditions are handled via `alternative_costs` or `only_if` modifiers.

**Supported cost types:**

- `type = "mana"` with `amount = "{2}{G}{G}"`
- `type = "tap"`, `type = "sacrifice"`, `type = "discard"`, etc.
- Composite and alternative costs via the `alternative_costs` list

**Example:**

```lua
cost = {
  { type = "mana", amount = "{1}{U}" },
  { type = "tap" },
  { type = "discard", filter = { type = "Card" } }
}

---

[< Previous: 5. Abilities](05_abilities.md) | [Back to TOC](../README.md) (main documentation) | [Next: 7. Effects](07_effects.md)
