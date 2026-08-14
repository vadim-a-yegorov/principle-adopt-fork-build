# wheelcheck

**Check for existing solutions before building. Adopt/Fork/Build decision framework.**

A GitHub-first build-vs-buy review tool that prevents wheel reinvention by systematically searching for serious existing projects before you write code.

## Philosophy

> "The best code is the code never written."

`wheelcheck` enforces a three-phase decision process:

1. **GitHub baseline** — search for reusable projects first
2. **Secondary platforms** — npm, PyPI, Hugging Face, Roboflow as relevant
3. **Final verdict** — Adopt / Fork / Build with evidence

## Installation

```bash
# As a skill (Hermes Agent)
cp -r software-development/never-reinvent-the-wheel ~/.hermes/skills/

# Or use the workflow directly
```

## Usage

```bash
# Trigger manually
wheelcheck "I want to build a scheduling board"

# Or let it auto-trigger on wheel-making patterns:
# - "I want to build", "help me build", "create a project for"
# - Complete systems: auth, queue, editor, parser, crawler, chat, scheduling
# - "from scratch", "without dependencies", "implement my own"
```

## Decision Heuristics

| Recommendation | When |
|----------------|------|
| **Adopt** | One candidate solves most of the core problem; healthy maintenance |
| **Fork/Compose** | Strong subsystems exist but full solution isn't a fit |
| **Build** | Options are stale, narrow, or structurally mismatched |

## License

MIT — forked from [Puss-M/Never-Reinvent-the-Wheel](https://github.com/Puss-M/Never-Reinvent-the-Wheel)
