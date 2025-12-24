# The Subtractive Triad

**Meta-principle**: Creation is the discipline of removing what obscures.

## The Three Levels

Every creation exists simultaneously at three levels, each with its corresponding discipline:

| Level | Discipline | Question | Action |
|-------|------------|----------|--------|
| **Implementation** | DRY | "Have I built this before?" | Unify |
| **Artifact** | Rams | "Does this earn its existence?" | Remove |
| **System** | Heidegger | "Does this serve the whole?" | Reconnect |

## Level 1: DRY (Implementation)

**Don't Repeat Yourself** — but understand why.

DRY is not about reducing line count. It's about ensuring that every piece of knowledge has a single, authoritative representation in the system.

### When to Unify

- Same logic appears in multiple places
- Change in one place requires change in others
- Copy-paste is the development pattern

### When NOT to Unify

- Similar code serves different purposes
- Abstraction would obscure intent
- Coupling would create fragility

### Anti-Pattern: Premature Abstraction

Creating abstractions before duplication exists violates Rams (adding without justification) while claiming to follow DRY.

## Level 2: Rams (Artifact)

Dieter Rams' "Weniger, aber besser" (Less, but better) applied to code.

### The 10 Principles for Code

1. **Innovative**: Solves a problem in a new way (when needed)
2. **Useful**: Actually serves a purpose
3. **Aesthetic**: Clean, readable, well-formatted
4. **Understandable**: Intent is clear
5. **Unobtrusive**: Doesn't add unnecessary complexity
6. **Honest**: Does what it claims, no hidden behavior
7. **Long-lasting**: Not a quick hack, maintainable
8. **Thorough**: Handles edge cases appropriately
9. **Environmentally friendly**: Efficient, no waste
10. **As little design as possible**: Only essential complexity

### The Rams Test

For every function, class, or module, ask: "Does this earn its existence?"

If you can't articulate why it must exist, it probably shouldn't.

## Level 3: Heidegger (System)

The hermeneutic circle: parts and whole must mutually inform each other.

### System Coherence

- Every component should serve the larger system
- The system's purpose should be visible in each component
- Changes to parts should strengthen, not fragment, the whole

### Reconnection Patterns

| Problem | Solution |
|---------|----------|
| Orphan module | Connect to system or remove |
| Circular dependency | Restructure to restore hierarchy |
| God object | Decompose by responsibility |
| Feature envy | Move behavior to where data lives |

### The Heidegger Test

For every change, ask: "Does this serve the whole?"

Code that doesn't connect to the system's purpose is noise.

## Application Order

Always apply the three questions in order:

1. **DRY** (Implementation) → Eliminate duplication
2. **Rams** (Artifact) → Eliminate excess
3. **Heidegger** (System) → Eliminate disconnection

The order matters because:
- You can't evaluate if something is excessive until duplicates are unified
- You can't evaluate system fit until excess is removed

## Why This Works

The triad is coherent because it's one principle—**subtractive revelation**—applied at three scales. Truth emerges through disciplined removal at every level of abstraction.

## Reference

Full methodology: https://createsomething.ltd/patterns/subtractive-triad
