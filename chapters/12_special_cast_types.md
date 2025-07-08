[< Previous: 11. Tokens](11_tokens.md) | [Back to TOC](../README.md) (main documentation) | [Next: 13. Complex Layouts](13_complex_layouts.md)

# 12. Special Cast Types

Some cards are cast from unusual zones or with modified rules. This includes mechanics like Madness, Foretell, Rebound, Suspend, and Escape.

These cases are handled using `special_cast` blocks inside `alternative_costs`, defining the origin zone, conditional rules, and whether the effect replaces the normal casting behavior. MCD separates costs from casting rights to keep evaluation modular.

**Example for a special_cast block (used inside alternative_costs):**

```lua
special_cast = {
  from_zone = "Exile",
  face_down = true,
  allow_free = true,
  replaces_normal_cast = true
}
```

**Example for an alternative_costs block:**

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

Mechanics supported via special cast types include: Madness, Rebound, Foretell, Escape, Flashback, and Suspend.

---

[< Previous: 11. Tokens](11_tokens.md) | [Back to TOC](../README.md) (main documentation) | [Next: 13. Complex Layouts](13_complex_layouts.md)
