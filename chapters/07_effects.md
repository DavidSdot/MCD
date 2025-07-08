[< Previous: 6. Costs](06_costs.md) | [Back to TOC](../README.md) (main documentation) | [Next: 8. Filters](08_filters.md)

# 7. Effects

Effects are the core of all card behavior. Each effect is a declarative instruction that the engine evaluates and executes. Effects may apply to game objects, players, the game state, or be purely mechanical (e.g., targeting, selection).

Effect blocks support chaining and ordering, and may include conditional logic. Duration-based effects are handled using explicit `duration` fields. All effects are atomic and engine-resolvable.

Multiple effect entries listed within a single `effect = { ... }` array are executed **in order**, from top to bottom. This allows modeling of compound effects like "Draw, then discard" or "Reveal, then choose".

**Example for a compound effect:**
```lua
effect = {
  { type = "Draw", amount = 1 },
  { type = "Discard", amount = 1 }
}
```

Each `effect` is a declarative statement (literal or dynamic values supported):

```lua
{ type = "Draw", amount = 1 }
{ type = "Exile", target = "TargetCreature" }
{ type = "CreateToken", token = { ...token def... } }
```

Specialized effect types include:

- `MoveCard`
- `Damage`
- `Grant`, `RemoveKeyword`
- `SetPower`, `Boost`, `ModifyLoyalty`

Conditional effects, choice blocks, and modal sections are supported as well.

---

[< Previous: 6. Costs](06_costs.md) | [Back to TOC](../README.md) (main documentation) | [Next: 8. Filters](08_filters.md)
