[< Previous: 18. Advanced Examples](18_advanced_examples.md) | [Back to TOC](../README.md) (main documentation) | [Next: 20. Event Reference for Triggered Abilities](20_event_reference_for_triggered_abilities.md)

# 19. Internationalization & Localization

MCD files are designed to be strictly language-independent. All textual content (e.g. descriptions, labels, flavor text) must be externalized via translation keys. This ensures full compatibility with multilingual engines and UI systems.

### Principles

- **No translatable text in .lua files**
- All fields with visible text use `*_key` instead of raw strings
- Language resources (e.g. `i18n.de.lua`) provide actual translations
- The engine may fall back to `*_key` if no translation is found

### Common Fields

| Field             | Purpose                              |
| ----------------- | ------------------------------------ |
| `label_key`       | Choice labels, ability alternatives  |
| `description_key` | Optional UI descriptions for effects |
| `flavor_key`      | Flavor text                          |
| `name_key`        | Multilingual name if not hardcoded   |

### Example: Localized Choice

```lua
choice = {
  min = 1,
  max = 1,
  options = {
    {
      label_key = "choice.draw2",
      effect = { type = "Draw", amount = 2 }
    },
    {
      label_key = "choice.gain4",
      effect = { type = "GainLife", amount = 4 }
    }
  }
}
```

### Example: Translation Resource (i18n.de.lua)

```lua
return {
  ["choice.draw2"] = "Ziehe 2 Karten",
  ["choice.gain4"] = "Erhalte 4 Lebenspunkte"
}
```

### Notes

- `*_key` fields are strings used for lookup, not shown to the player
- If a key has no translation, the engine may default to showing the key itself
- This pattern applies to any user-facing or explainable string

---

[< Previous: 18. Advanced Examples](18_advanced_examples.md) | [Back to TOC](../README.md) (main documentation) | [Next: 20. Event Reference for Triggered Abilities](20_event_reference_for_triggered_abilities.md)
