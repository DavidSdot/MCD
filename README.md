# Magic Card Definition (MCD)

**MCD** (Magic Card Definition) is a declarative, structured format for representing Magic: The Gathering cards in a machine-readable way. It is designed to support rule-faithful simulations, deck building, game engines, and AI-driven interactions with MTG cards – all without requiring custom hardcoded logic for each individual card.

> **Note:** This project is a fan-made, non-commercial initiative. It is neither affiliated with nor endorsed by Wizards of the Coast.

---

## What is MCD?

MCD is a Lua-based data format that models the rules, costs, abilities, and all key information about a Magic card. Each card is defined as a structured Lua table with clearly labeled fields for:

- Card ID and layout
- One or more *faces* (name, mana cost, types, color, etc.)
- Ability blocks (`triggered`, `activated`, `static`)
- Costs, conditions, effects
- Special cast mechanics (e.g. Flashback, Suspend)
- Token definitions
- Filters and targeting logic
- Rule-level constructs like Monarch, Dungeons, etc.

This allows engines to **simulate gameplay** based purely on data – without hardcoding cards in C# or another host language.

---

## Use Case

You can use MCD with any modular Magic: The Gathering engine that supports:

- Full game rule execution (zones, stack, timing, priority)
- Dynamic card loading from Lua
- Multiple formats (e.g. Commander, Standard, etc.)
- AI or simulation support
- Optional GUI or CLI frontends

---

## Project Structure

- `/core/` – Shared logic, enums, and templates (e.g. `MCD_Template.lua`)
- `/doc/` – Documentation including the full handbook
- `/samples/` – Example scripts for testing

Each `.lua` file contains the full definition for a card or token, following a strict data structure that is checked by the engine for correctness.

---

## MCD Handbook

The full documentation is organized by topic below.
Click any chapter to jump directly to the corresponding section.

## Table of Contents
- [1. Introduction](chapters/01_introduction.md)
- [2. General Structure](chapters/02_general_structure.md)
- [3. Card-Level Fields](chapters/03_card-level_fields.md)
- [4. Face-Level Fields](chapters/04_face-level_fields.md)
- [5. Abilities](chapters/05_abilities.md)
- [6. Costs](chapters/06_costs.md)
- [7. Effects](chapters/07_effects.md)
- [8. Filters](chapters/08_filters.md)
- [9. Zones & Targets](chapters/09_zones_and_targets.md)
- [10. Conditional Logic & Choice](chapters/10_conditional_logic_and_choice.md)
- [11. Tokens](chapters/11_tokens.md)
- [12. Special Cast Types](chapters/12_special_cast_types.md)
- [13. Complex Layouts](chapters/13_complex_layouts.md)
- [14. Keywords & Game Mechanics](chapters/14_keywords_and_game_mechanics.md)
- [15. Design Philosophy](chapters/15_design_philosophy.md)
- [16. Appendix: Keyword Reference](chapters/16_appendix__keyword_reference.md)
- [17. Full Example: Complex Card Definition](chapters/17_full_example__complex_card_definition.md)
- [18. Advanced Examples](chapters/18_advanced_examples.md)
- [19. Internationalization & Localization](chapters/19_internationalization_and_localization.md)
- [20. Event Reference for Triggered Abilities](chapters/20_event_reference_for_triggered_abilities.md)
- [21. Duration Reference](chapters/21_duration_reference.md)
- [22. Dynamic Value Reference](chapters/22_dynamic_value_reference.md)
- [23. Targets & Named References](chapters/23_targets_and_named_references.md)
- [24. Keyword Abilities Reference](chapters/24_keyword_abilities_reference.md)
- [25. Card Color & Indicators](chapters/25_card_color_and_indicators.md)
- [26. General MCD Examples](chapters/26_general_examples.md)

---

## Legal Notice

This project is unofficial **Fan Content** permitted under the [Wizards of the Coast Fan Content Policy](chapters/https://company.wizards.com/en/legal/fancontentpolicy).  
It is not approved or endorsed by Wizards.  
Portions of the materials used are property of Wizards of the Coast LLC.  
© Wizards of the Coast LLC.

**Magic: The Gathering™** and all associated logos and card names are trademarks of Wizards of the Coast.

---

## External Sources

This project uses Magic: The Gathering card data provided by:

- **Scryfall** – https://scryfall.com  
  Data is used under [CC BY-NC 4.0](chapters/https://creativecommons.org/licenses/by-nc/4.0/)

Card names, IDs, mana costs, types, and rules text may be derived via the [Scryfall API](chapters/https://scryfall.com/docs/api).

---

## License

This repository is provided under the **MIT License** unless stated otherwise.  
See `LICENSE` file for details.

---

## Contributing

Contributions are welcome!  
If you find an issue, want to suggest an improvement, or would like to add a new feature, please open an Issue or Pull Request on GitHub.  
Please follow the existing style and structure.  
If you are unsure, feel free to start a discussion in the Issues section before making a larger change.
