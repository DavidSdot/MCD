[< Previous: 17. Full Example: Complex Card Definition](17_full_example__complex_card_definition.md) | [Back to TOC](../README.md) (main documentation) | [Next: 19. Internationalization & Localization](19_internationalization_and_localization.md)

# 18. Advanced Examples

This section showcases real-world cards of varying complexity expressed in MCD format. The examples range from simple keywords to multi-step effects involving opponent interaction, tokens, and alternative costs.

### Example A: Lightning Bolt

```lua
return {
  id = "bolt001",
  layout = "normal",
  faces = {
    {
      name = "Lightning Bolt",
      oid = "oracle001",
      mana_cost = "{R}",
      types = { "Instant" },
      abilities = {
        spell = {
          {
            effect = {
              type = "Damage",
              target = "AnyTarget",
              amount = 3
            }
          }
        }
      }
    }
  }
}
```

### Example B: Llanowar Elves

```lua
return {
  id = "elf001",
  layout = "normal",
  faces = {
    {
      name = "Llanowar Elves",
      oid = "oracle002",
      mana_cost = "{G}",
      types = { "Creature" },
      subtypes = { "Elf", "Druid" },
      power = 1,
      toughness = 1,
      abilities = {
        activated = {
          {
            cost = { { type = "tap" } },
            effect = { type = "AddMana", amount = "{G}" }
          }
        }
      }
    }
  }
}
```

### Example C: Monastery Mentor

```lua
return {
  id = "mentor001",
  layout = "normal",
  faces = {
    {
      name = "Monastery Mentor",
      oid = "oracle003",
      mana_cost = "{2}{W}",
      types = { "Creature" },
      subtypes = { "Human", "Monk" },
      power = 2,
      toughness = 2,
      abilities = {
        triggered = {
          {
            condition = {
              event = "NoncreatureSpellCast",
              by = "Controller"
            },
            effect = {
              type = "CreateToken",
              token = {
                name = "Monk",
                types = { "Creature" },
                subtypes = { "Monk" },
                power = 1,
                toughness = 1,
                color = { "White" },
                keywords = { "Prowess" }
              }
            }
          }
        }
      }
    }
  }
}
```

### Example D: The One Ring

```lua
return {
  id = "ring001",
  layout = "normal",
  faces = {
    {
      name = "The One Ring",
      oid = "oracle004",
      mana_cost = "{4}",
      types = { "Legendary", "Artifact" },
      abilities = {
        triggered = {
          {
            condition = { event = "EntersTheBattlefield", source = "Self" },
            effect = { type = "GainProtection", from = "Everything", duration = "UntilNextTurn" }
          }
        },
        activated = {
          {
            cost = { { type = "tap" } },
            effect = {
              type = "Draw",
              amount = {
                type = "CounterValue",
                counter_type = "Burden",
                target = "Self"
              }
            }
          }
        },
        static = {
          {
            effect = {
              type = "AddCounter",
              counter_type = "Burden",
              amount = 1,
              target = "Self"
            },
            condition = { type = "TurnBegins", player = "Controller" }
          }
        }
      }
    }
  }
}
```

### Example E: Gifts Ungiven

(see full example below)

These templates demonstrate how MCD can scale from simple removal and mana dorks to complex triggered, static, and alternative play patterns with opponent interaction and counters.

---

### Example F: Delver of Secrets / Insectile Aberration (Transform)

```lua
return {
  id = "delver001",
  layout = "transform",
  faces = {
    {
      name = "Delver of Secrets",
      oid = "oracle005a",
      mana_cost = "{U}",
      types = { "Creature" },
      subtypes = { "Human", "Wizard" },
      power = 1,
      toughness = 1,
      abilities = {
        triggered = {
          {
            condition = { event = "UpkeepStep", player = "Controller" },
            effect = {
              type = "RevealTop",
              count = 1,
              assign_to = "RevealedCard"
            }
          },
          {
            condition = {
              type = "IsInstantOrSorcery",
              target = "RevealedCard"
            },
            effect = {
              type = "Transform",
              target = "Self"
            }
          }
        }
      }
    },
    {
      name = "Insectile Aberration",
      oid = "oracle005b",
      types = { "Creature" },
      subtypes = { "Insect" },
      power = 3,
      toughness = 2,
      keywords = { "Flying" },
      abilities = {}
    }
  }
}
```

### Example G: Brazen Borrower (Adventure)

```lua
return {
  id = "borrower001",
  layout = "adventure",
  faces = {
    {
      name = "Petty Theft",
      oid = "oracle006a",
      types = { "Instant" },
      mana_cost = "{1}{U}",
      abilities = {
        spell = {
          {
            effect = {
              type = "ReturnToHand",
              target = {
                type = "Permanent",
                controller = "Opponent",
                nonland = true
              }
            }
          }
        }
      }
    },
    {
      name = "Brazen Borrower",
      oid = "oracle006b",
      types = { "Creature" },
      subtypes = { "Faerie", "Rogue" },
      power = 3,
      toughness = 1,
      mana_cost = "{1}{U}{U}",
      keywords = { "Flash", "Flying" },
      abilities = {
        static = {
          {
            effect = {
              type = "RestrictCast",
              condition = { type = "CanBlockOnlyFlying" }
            }
          }
        }
      }
    }
  }
}
```

### Example H: Nethroi, Apex of Death (Mutate)

```lua
return {
  id = "nethroi001",
  layout = "normal",
  faces = {
    {
      name = "Nethroi, Apex of Death",
      oid = "oracle007",
      mana_cost = "{2}{W}{B}{G}",
      types = { "Legendary", "Creature" },
      subtypes = { "Cat", "Nightmare", "Beast" },
      power = 5,
      toughness = 5,
      keywords = { "Mutate", "Deathtouch", "Lifelink" },
      mutate_cost = "{4}{B}{G}",
      abilities = {
        triggered = {
          {
            condition = { event = "Mutates", target = "Self" },
            effect = {
              type = "ReturnFromGraveyard",
              filter = {
                type = "Creature",
                total_power = { operator = "LE", value = 10 }
              },
              to_zone = "Battlefield"
            }
          }
        }
      }
    }
  }
}
```

### Example I: Bloodbraid Elf (Cascade)

```lua
return {
  id = "cascade001",
  layout = "normal",
  faces = {
    {
      name = "Bloodbraid Elf",
      oid = "oracle008",
      mana_cost = "{2}{R}{G}",
      types = { "Creature" },
      subtypes = { "Elf", "Berserker" },
      power = 3,
      toughness = 2,
      keywords = { "Haste" },
      abilities = {
        triggered = {
          {
            condition = { event = "SpellCast", target = "Self" },
            effect = { type = "Cascade" }
          }
        }
      }
    }
  }
}
```

### Example J: Lost Mine of Phandelver (Dungeon)

```lua
return {
  id = "dungeon001",
  layout = "dungeon",
  faces = {
    {
      name = "Lost Mine of Phandelver",
      oid = "oracleDungeon1",
      types = { "Dungeon" },
      rooms = {
        {
          name = "Cave Entrance",
          effects = {
            { type = "Scry", amount = 1 }
          }
        },
        {
          name = "Goblin Lair",
          effects = {
            { type = "CreateToken", token = {
              name = "Goblin",
              types = { "Creature" },
              subtypes = { "Goblin" },
              power = 1, toughness = 1,
              color = { "Red" }
            } }
          }
        }
        -- etc.
      }
    }
  }
}
```

These extended examples further demonstrate how MCD handles transforms, modal and adventure spells, mutate triggers, cascade resolution, and persistent structures like dungeons.

This example showcases a multi-step card resolution with player search, opponent choice, and multi-zone outcome.

```lua
return {
  id = "gifts123",
  layout = "normal",
  faces = {
    {
      name = "Gifts Ungiven",
      oid = "oracle456",
      mana_cost = "{3}{U}",
      types = { "Instant" },
      abilities = {
        spell = {
          {
            effect = {
              type = "ResolveInSequence",
              steps = {
                {
                  type = "SearchLibrary",
                  controller = "Controller",
                  max = 4,
                  filters = { type = "Card" },
                  unique_names = true,
                  assign_to = "SelectedCards"
                },
                {
                  type = "Reveal",
                  target = "SelectedCards"
                },
                {
                  type = "OpponentChoosesCards",
                  from = "SelectedCards",
                  amount = 2,
                  assign_to = "OpponentChosen"
                },
                {
                  type = "MoveCard",
                  target = "OpponentChosen",
                  from_zone = "Library",
                  to_zone = "Graveyard"
                },
                {
                  type = "MoveCard",
                  target = {
                    type = "ListDifference",
                    base = "SelectedCards",
                    exclude = "OpponentChosen"
                  },
                  from_zone = "Library",
                  to_zone = "Hand"
                },
                {
                  type = "ShuffleLibrary",
                  target = "Controller"
                }
              }
            }
          }
        }
      }
    }
  }
}
```

---

[< Previous: 17. Full Example: Complex Card Definition](17_full_example__complex_card_definition.md) | [Back to TOC](../README.md) (main documentation) | [Next: 19. Internationalization & Localization](19_internationalization_and_localization.md)
