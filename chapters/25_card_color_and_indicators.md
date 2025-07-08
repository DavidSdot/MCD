[< Previous: 24. Keyword Abilities Reference](24_keyword_abilities_reference.md) | [Back to TOC](../README.md) (main documentation)

# 25. Card Color & Indicators



MCD uses the `color` field to define a card's color identity explicitly when it cannot be derived from its mana cost or when a special rule applies (e.g. Devoid, tokens, lands with color indicators).

### Usage

```lua
color = { "White" }
color = { "Blue", "Red" }
color = {} -- colorless
```

### Rules

- The `color` field is **optional** for most printed cards
- If `color` is **omitted**, the engine derives color from `mana_cost`
- Tokens **must define** their `color` explicitly
- Cards with the **Devoid** mechanic must use `color = {}`
- Cards with **color indicators** (e.g. DFCs, snow permanents) should use this field to reflect their actual color

### Valid Values

| Value   | Meaning              |
| ------- | -------------------- |
| `White` | Plains-based color   |
| `Blue`  | Island-based color   |
| `Black` | Swamp-based color    |
| `Red`   | Mountain-based color |
| `Green` | Forest-based color   |

> Values are case-sensitive strings, e.g. `"White"`, `"Red"`

### Special Cases

| Case                 | Notes                                     |
| -------------------- | ----------------------------------------- |
| `Devoid`             | Use `color = {}` even with colored cost   |
| `Color Indicator`    | Explicitly set `color = { ... }`          |
| `Tokens`             | Always set `color` manually               |
| `Artifacts`, `Lands` | Usually colorless unless stated otherwise |

If color is derived from `mana_cost`, it is calculated as per CR 105.2 (each mana symbol co

---

## Handbook Version

This handbook refers to the Magic Card Definition (MCD) **Version 1.0.0** (as of 2025-07-06).

---

## Additional Examples

### Spell Abilities Example

```lua
spell = {
  effect = {
    type = "Damage",
    target = "AnyTarget",
    amount = 3
  }
}
```

### Alternative Costs Example

```lua
alternative_costs = {
  {
    label = "Madness",
    mana = "{1}{R}",
    special_cast = {
      from_zone = "Exile",
      replaces_normal_cast = true
    }
  }
}
```

### Nested Conditions Example

```lua
condition = {
  any_of = {
    { type = "LifeTotal", operator = "LT", value = 5 },
    {
      all_of = {
        { type = "CreatureCount", operator = "GT", value = 2 },
        { type = "HasCounter", counter = "+1/+1", operator = "GE", value = 3 }
      }
    }
  }
}
```

### TargetPlayer Definition Example

```lua
target = "TargetPlayer.Opponent"
```

### Detailed MCD Template Example

```lua
return {
  id = "REPLACE_WITH_UUID",
  layout = "normal",
  faces = {
    {
      name = "Card Name",
      oid = "REPLACE_WITH_ORACLE_ID",
      mana_cost = "{1}{G}",
      types = {"Creature"},
      subtypes = {"Elf", "Druid"},
      power = 2,
      toughness = 2,
      color = {"Green"},
      keywords = {"Flying", "Haste"},
      flavor = "Optional flavor text",
      abilities = {
        triggered = {}, 
        activated = {
          {
            cost = {
              { type = "mana", amount = "{1}{G}" },
              { type = "tap" }
            },
            effect = { type = "CreateToken", token = { name = "TokenName", power = 1, toughness = 1 } }
          }
        },
        static = {}
      },
      alternative_costs = {
        {
          label = "Flashback",
          mana = "{2}{G}",
          special_cast = {
            from_zone = "Graveyard"
          }
        }
      }
    }
  }
}
```

### Token with Duration Example

```lua
token = {
  name = "Spirit",
  types = {"Creature"},
  subtypes = {"Spirit"},
  power = 1,
  toughness = 1,
  duration = "UntilEndOfTurn"
}
```

### Dynamic Value Example

```lua
amount = {
  type = "CardCount",
  zone = "Graveyard",
  controller = "Opponent",
  filter = { type = "Creature" }
}
```

### Complex Layout Example (Saga)

```lua
return {
  id = "saga001",
  layout = "saga",
  faces = {
    {
      name = "History of Benalia",
      oid = "oracle123",
      mana_cost = "{1}{W}{W}",
      types = {"Enchantment"},
      subtypes = {"Saga"},
      abilities = {
        triggered = {
          {
            condition = { event = "LoreCounterAdded", count = 1 },
            effect = { type = "CreateToken", token = { name = "Knight", types = {"Creature"}, subtypes = {"Knight"}, power = 2, toughness = 2 } }
          }
        }
      }
    }
  }
}
```

[< Previous: 24. Keyword Abilities Reference](24_keyword_abilities_reference.md) | [Back to TOC](../README.md) (main documentation)
