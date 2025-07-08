[< Previous: 10. Conditional Logic & Choice](10_conditional_logic_and_choice.md) | [Back to TOC](../README.md) (main documentation) | [Next: 12. Special Cast Types](12_special_cast_types.md)

# 11. Tokens

Tokens represent temporary or engine-generated cards. In MCD, tokens are described using the same `face` structure as normal cards. This ensures consistency in behavior and compatibility with abilities, targeting, and rules interactions.

Token effects must declare the full structure of the token (name, types, power/toughness, keywords, abilities, etc.). Optionally, tokens may have durations or be attached (for example, roles or auras).

**Example for a token definition:**

```lua
token = {
  name = "Soldier",
  types = {"Creature"},
  subtypes = {"Soldier"},
  power = 1,
  toughness = 1,
  color = {"White"},
  keywords = {"Vigilance"}
}
```

**Example for a temporary token (with duration):**

```lua
token = {
  name = "Spirit",
  types = {"Creature"},
  subtypes = {"Spirit"},
  power = 1,
  toughness = 1,
  color = {"White"},
  keywords = {"Flying"},
  duration = "UntilEndOfTurn"
}
```

---

[< Previous: 10. Conditional Logic & Choice](10_conditional_logic_and_choice.md) | [Back to TOC](../README.md) (main documentation) | [Next: 12. Special Cast Types](12_special_cast_types.md)
