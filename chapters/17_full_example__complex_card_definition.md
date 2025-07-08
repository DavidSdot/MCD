[< Previous: 16. Appendix: Keyword Reference](16_appendix__keyword_reference.md) | [Back to TOC](../README.md) (main documentation) | [Next: 18. Advanced Examples](18_advanced_examples.md)

# 17. Full Example: Complex Card Definition

Below is a full MCD definition of a card that uses triggered and static abilities, a token generator, conditional logic, and an alternative cost.

**Features in this example:**
- Token generation via triggered ability (creates a Spirit when another creature dies)
- Conditional static ability (grants Lifelink at low life)
- Activated ability (gain life)
- Alternative cost (Flashback)

```lua
return {
  id = "abc123",
  layout = "normal",
  faces = {
    {
      name = "Sunblade Archon",
      oid = "oid123",
      mana_cost = "{2}{W}{W}",
      types = { "Creature" },
      subtypes = { "Angel", "Cleric" },
      power = 4,
      toughness = 4,
      abilities = {
        triggered = {
          {
            condition = { event = "PermanentDies", filter = { type = "Creature", controller = "Controller" } },
            effect = {
              type = "CreateToken",
              token = {
                name = "Spirit",
                types = { "Creature" },
                subtypes = { "Spirit" },
                power = 1,
                toughness = 1,
                color = { "White" },
                keywords = { "Flying" }
              }
            }
          }
        },
        static = {
          {
            condition = {
              all_of = {
                { type = "LifeTotal", operator = "LT", value = 5 },
                { type = "Zone", value = "Battlefield" }
              }
            },
            effect = {
              type = "Grant",
              keyword = "Lifelink"
            }
          }
        },
        activated = {
          {
            cost = {
              { type = "mana", amount = "{1}{W}" },
              { type = "tap" }
            },
            effect = {
              type = "GainLife",
              amount = 3
            }
          }
        }
      },
      alternative_costs = {
        {
          label = "Flashback",
          mana = "{3}{W}",
          special_cast = {
            from_zone = "Graveyard"
          }
        }
      }
    }
  }
}
```

---

[< Previous: 16. Appendix: Keyword Reference](16_appendix__keyword_reference.md) | [Back to TOC](../README.md) (main documentation) | [Next: 18. Advanced Examples](18_advanced_examples.md)
