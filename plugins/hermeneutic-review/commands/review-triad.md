# Review Triad Command

Apply the Subtractive Triad code review methodology to any code.

## Usage

```
/review-triad [path]
```

## What It Does

Three-pass code review through the Subtractive Triad lens:

### Pass 1: DRY (Unify)

**Question**: "Have I built this before?"

- Detect duplication patterns
- Identify repeated logic across files
- Find copy-paste code
- Suggest abstractions (only when warranted)

### Pass 2: Rams (Remove)

**Question**: "Does this earn its existence?"

Apply Dieter Rams' 10 principles to code artifacts:

1. Is it **innovative**? (Does it solve a new problem?)
2. Does it make the code **useful**?
3. Is it **aesthetic**? (Clean, readable)
4. Does it make the code **understandable**?
5. Is it **unobtrusive**? (No unnecessary complexity)
6. Is it **honest**? (Does what it claims)
7. Is it **long-lasting**? (Not a quick hack)
8. Is it **thorough**? (Handles edge cases)
9. Is it **environmentally friendly**? (Efficient)
10. Is it **as little design as possible**?

### Pass 3: Heidegger (Reconnect)

**Question**: "Does this serve the whole?"

- Verify system-level coherence
- Check that changes fit the architectural vision
- Ensure the hermeneutic circle is maintained
- Identify disconnected or orphaned code

## Output Format

```markdown
## Subtractive Triad Review: [path]

### Pass 1: DRY (Unify)

| Pattern | Location | Suggestion |
|---------|----------|------------|
| [duplication] | [file:line] | [how to unify] |

**DRY Score**: X/10

### Pass 2: Rams (Remove)

| Violation | Principle | Location | Action |
|-----------|-----------|----------|--------|
| [what] | [which principle] | [where] | [remove/simplify] |

**Rams Score**: X/10

### Pass 3: Heidegger (Reconnect)

| Issue | System Impact | Resolution |
|-------|---------------|------------|
| [disconnection] | [how it breaks coherence] | [how to reconnect] |

**Coherence Score**: X/10

### Verdict

**Overall**: [PASS | NEEDS WORK | FAIL]

**Priority Actions**:
1. [Most critical fix]
2. [Second priority]
3. [Third priority]
```

## Anti-Patterns Detected

The review flags these anti-patterns:

| Anti-Pattern | Triad Level | Description |
|--------------|-------------|-------------|
| Premature abstraction | DRY | Abstracting before duplication exists |
| God object | Rams | Class/module doing too much |
| Dead code | Rams | Unused functions/variables |
| Orphan module | Heidegger | Code not connected to system |
| Circular dependency | Heidegger | Breaks hermeneutic circle |
| Over-engineering | Rams | Complexity without justification |

## Scope

- No argument: Review current file or staged changes
- File path: Review specific file
- Directory: Review all code files in directory

## Philosophy

The Subtractive Triad is one principle—**subtractive revelation**—applied at three scales:

1. **Implementation** (DRY): Eliminate duplication
2. **Artifact** (Rams): Eliminate excess
3. **System** (Heidegger): Eliminate disconnection

Truth emerges through disciplined removal at every level of abstraction.

## Reference

See https://createsomething.ltd/patterns/subtractive-triad for full methodology.
