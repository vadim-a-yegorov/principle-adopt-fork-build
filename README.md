# scan_reuse_adopt

**Search existing solutions before you build. Scan → Reuse → Adopt. Build only when nothing fits.**

A GitHub-first build-vs-buy framework executed before any new implementation starts.

## The ladder

Work down the rungs. Stop at the first that holds.

1. **Does it need to exist?** Speculative need = skip it (YAGNI).
2. **Already in this codebase?** Reuse the helper, util, type, or pattern already a few files over.
3. **Stdlib/native solves it?** Use it.
4. **Already-installed dependency solves it?** Use it. Never add a new one for a few lines.
5. **Can it be one line?** One line.
6. **Search GitHub first**, then relevant secondary platforms, for the strongest existing candidate.
7. **Then build** the minimum that works.

The best code is the code never written.

## Verdict

After scanning, recommend exactly one:

- **Adopt** — one candidate solves most of the problem; healthy maintenance.
- **Fork/Compose** — strong subsystems exist, but no full fit.
- **Build** — candidates stale, narrow, or structurally mismatched. Not because no exact-name match exists.

## Triggering

Fire automatically when the user is about to build a full product, subsystem, or workflow from scratch:

- "I want to build", "help me build", "create a project for"
- complete systems: auth, queue, editor, parser, crawler, chat, scheduling, agent frameworks
- "from scratch", "without dependencies", "implement my own"

Do **not** trigger on: learning/practice asks, debugging existing code, narrow algorithm/regex questions, or one-off local scripts.

## Framework-tier rule (delta)

When a build is genuinely warranted after the pass:

- Tier 0 (language-level, always available): React, Vue, Next.js, Prisma — base infrastructure, never a reason to write own code.
- Tier 1 (problem-tailored): use the most specific framework that solves ~99% of the task, write the ~1% glue.
- Never pick a general-purpose framework where a problem-tailored one exists.
- The only acceptable reason to write code yourself: the capability exists only closed-source. Research 10x deeper first.
- Drop any "no-dependency" stance — dependencies are the point.

## Decision heuristics

| Recommendation | When |
|----------------|------|
| **Adopt** | One candidate solves most of the core problem; healthy maintenance |
| **Fork/Compose** | Strong subsystems exist but the full solution isn't a fit |
| **Build** | Candidates are stale, narrow, or structurally mismatched |

Never recommend build solely because no exact-name match exists. Look for adjacent reusable components first.

## Evidence rules

- Search GitHub first for every request. Inspect repository structure + 1–3 key implementation files. Never judge capability by README alone.
- Include a clickable URL for every project/package/model mentioned.
- Use real recency/adoption signals (stars, forks, downloads, model likes). If evidence is weak, say so explicitly. Don't fabricate.
- Prefer Perplexity / Gemini deep research. Don't invent custom API integrations.

## License

MIT