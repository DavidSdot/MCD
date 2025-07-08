[< Previous: 23. Targets & Named References](23_targets_and_named_references.md) | [Back to TOC](../README.md) (main documentation) | [Next: 25. Card Color & Indicators](25_card_color_and_indicators.md)

# 24. Keyword Abilities Reference

This section provides a formal list of supported keyword abilities in MCD. These keywords can appear:

- As part of `keywords = { ... }` in a card face
- As part of an effect: `type = "Grant", keyword = "..."
- In conditions or removal effects (e.g. `RemoveKeyword`)

Keywords correspond directly to MTG Comprehensive Rules section 702.  
For a full list and details, see MTG CR 702.

### Usage

```lua
-- Static keyword assignment
keywords = { "Flying", "First Strike" }

-- Temporary via effect
{
  type = "Grant",
  target = "Self",
  keyword = "Hexproof",
  duration = "UntilEndOfTurn"
}
```

### Common Supported Keywords

| Keyword          | Description summary                                 |
| ---------------- | --------------------------------------------------- |
| `Flying`         | Can only be blocked by flying or reach              |
| `Reach`          | Can block creatures with flying                     |
| `Deathtouch`     | Any amount of damage destroys creatures             |
| `Lifelink`       | Controller gains life equal to damage dealt         |
| `Trample`        | Excess damage assigned to defending player          |
| `First Strike`   | Deals combat damage in first-strike step            |
| `Double Strike`  | Deals combat damage in both first and regular step  |
| `Hexproof`       | Cannot be the target of opponent's spells/abilities |
| `Indestructible` | Cannot be destroyed by damage or destroy effects    |
| `Menace`         | Must be blocked by two or more creatures            |
| `Haste`          | Can attack or use {T} on the turn it enters         |
| `Vigilance`      | Attacking does not cause tapping                    |
| `Ward`           | Opponents must pay cost to target                   |
| `Protection`     | Source has protection from specified quality        |
| `Prowess`        | Gets +1/+1 when casting noncreature spell           |
| `Defender`       | Cannot attack                                       |
| `Flash`          | Can be cast at instant speed                        |

### Notes

- The keyword string is case-sensitive and must match exactly (e.g. `"Hexproof"` not `"hexproof"`)
- Keywords not yet supported in rules or engine are ignored by default
- You may expand the keyword list to include special mechanics (e.g. Mutate, Companion) using the same mechanism

For full rules and corner cases, see MTG CR 702.

---

[< Previous: 23. Targets & Named References](23_targets_and_named_references.md) | [Back to TOC](../README.md) (main documentation) | [Next: 25. Card Color & Indicators](25_card_color_and_indicators.md)
