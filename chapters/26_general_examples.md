# 26. General MCD Examples

This chapter collects general examples of Magic Card Definition (MCD) concepts and usage.  
These samples can be used as templates for your own cards and scripts.

[Back to TOC](../README.md) (main documentation)

---

## Spell Abilities Example

```lua
spell = {
  effect = {
    type = "Damage",
    target = "AnyTarget",
    amount = 3
  }
}
```

## Alternative Costs Example

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

## Nested Conditions Example

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

## TargetPlayer Definition Example

```lua
target = "TargetPlayer.Opponent"
```

## Detailed MCD Template Example

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

## Token with Duration Example

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

## Dynamic Value Example

```lua
amount = {
  type = "CardCount",
  zone = "Graveyard",
  controller = "Opponent",
  filter = { type = "Creature" }
}
```

## Complex Layout Example (Saga)

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

[Back to TOC](../README.md) (main documentation)
