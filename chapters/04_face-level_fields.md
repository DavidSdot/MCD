[< Previous: 3. Card-Level Fields](03_card-level_fields.md) | [Back to TOC](../README.md) (main documentation) | [Next: 5. Abilities](05_abilities.md)

# 4. Face-Level Fields

The following table summarizes all fields within a card face definition. Some fields are required only for specific card types (for example, `power` and `toughness` for creatures, `loyalty` for planeswalkers):

| Field               | Required | Type    | Description                                 |
|---------------------|----------|---------|---------------------------------------------|
| `name`              | Yes      | string  | Display name of the face                    |
| `oid`               | Yes      | string  | Oracle ID for uniqueness & rulings          |
| `mana_cost`         | Yes      | string  | Mana string (unless costless)               |
| `types`             | Yes      | array   | Supertype + card type(s)                    |
| `subtypes`          | No       | array   | Subtypes (optional unless type-dependent)   |
| `power`             | No       | number  | Required for creature faces                 |
| `toughness`         | No       | number  | Required for creature faces                 |
| `loyalty`           | No       | number  | Required for planeswalkers                  |
| `abilities`         | No       | table   | Table grouped by triggered/activated/static |
| `keywords`          | No       | array   | Keyword string list                         |
| `flavor`            | No       | string  | Flavor text (UI only, via flavor_key)       |
| `art`               | No       | string  | Optional art descriptor                     |
| `alternative_costs` | No       | array   | Special cast / flashback / madness etc.     |

---

[< Previous: 3. Card-Level Fields](03_card-level_fields.md) | [Back to TOC](../README.md) (main documentation) | [Next: 5. Abilities](05_abilities.md)
