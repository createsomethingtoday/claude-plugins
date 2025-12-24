# CREATE SOMETHING Claude Code Plugins

Subtractive design methodology: DRY -> Rams -> Heidegger

## Philosophy

**"Creation is the discipline of removing what obscures."**

These plugins encode the Subtractive Triad - a three-level approach to code quality:

| Level | Discipline | Question | Action |
|-------|------------|----------|--------|
| **Implementation** | DRY | "Have I built this before?" | Unify |
| **Artifact** | Rams | "Does this earn its existence?" | Remove |
| **System** | Heidegger | "Does this serve the whole?" | Reconnect |

## Available Plugins

### canon

Design system enforcement with Dieter Rams principles.

Enforces "Tailwind for structure, Canon for aesthetics" - separating layout utilities from design tokens.

```bash
/plugin install canon@create-something
```

**Provides:**
- `/audit-canon` command - Check CSS Canon compliance
- `canon-auditor` agent - Proactive compliance checks
- PostToolUse hook - Automatic checking on Write/Edit

### hermeneutic-review

Code review through the Subtractive Triad lens.

Three-pass review: DRY (duplication) -> Rams (necessity) -> Heidegger (coherence)

```bash
/plugin install hermeneutic-review@create-something
```

**Provides:**
- `hermeneutic-reviewer` agent - Full triad analysis
- Subtractive Review skill - Review methodology
- PR audit script - Automated PR checks

### voice-validator

Content validation against the Five Principles of Communication.

Enforces clarity over cleverness, specificity over generality, honesty over polish.

```bash
/plugin install voice-validator@create-something
```

**Provides:**
- `/audit-voice` command - Check content compliance
- Voice Validator skill - Full validation workflow

### understanding-graphs

Minimal dependency graphs for codebase comprehension.

"Less, but better" applied to documentation.

```bash
/plugin install understanding-graphs@create-something
```

**Provides:**
- Understanding Graphs skill - Generate UNDERSTANDING.md files

## Installation

### Option 1: Web UI (Recommended)

Browse and manage plugins at **[createsomething.io/plugins](https://createsomething.io/plugins)**

- Visual plugin catalog with descriptions
- Toggle plugins on/off with one click
- Export settings.json for Claude Code

### Option 2: CLI

Add this marketplace to Claude Code:

```bash
/plugin marketplace add createsomethingtoday/claude-plugins
```

Then install individual plugins:

```bash
/plugin install canon@create-something
/plugin install hermeneutic-review@create-something
```

## For WORKWAY Projects

These plugins are designed to work with WORKWAY and other projects that follow CREATE SOMETHING methodology.

Add to your `.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "create-something": {
      "source": {
        "source": "github",
        "repo": "createsomethingtoday/claude-plugins"
      }
    }
  },
  "enabledPlugins": {
    "canon@create-something": true,
    "hermeneutic-review@create-something": true
  }
}
```

## The Subtractive Triad

For any decision, ask three questions in order:

1. **DRY** (Implementation) -> Eliminate duplication
2. **Weniger, aber besser** (Artifact) -> Eliminate excess
3. **Hermeneutic circle** (System) -> Eliminate disconnection

The triad is coherent because it's one principle - **subtractive revelation** - applied at three scales.

## Reference

- [createsomething.io/plugins](https://createsomething.io/plugins) - **Plugin Management UI**
- [createsomething.ltd](https://createsomething.ltd) - Philosophy and Canon
- [createsomething.io](https://createsomething.io) - Research and Papers
- [createsomething.space](https://createsomething.space) - Experiments

---

*The tool recedes; the methodology propagates.*
