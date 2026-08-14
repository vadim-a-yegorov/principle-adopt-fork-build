---
name: never-reinvent-the-wheel
description: "GitHub-first build-vs-buy before build: Adopt/Fork/Build."
---

# Never Reinvent The Wheel

Restate a proposed idea, search for serious existing projects, and produce a recommendation on whether to adopt, fork, or build. Treat this as a pre-development architecture review, not an implementation task.

This skill is a fork of `Puss-M/Never-Reinvent-the-Wheel` (MIT) — adopted, not invented. The workflow below preserves the upstream decision process; the final section adds the user's framework-tier rule.

## Core Rules

- Warn the user before searching if the idea appears sensitive, proprietary, or commercially confidential. Ask them to anonymize it first if needed.
- Use existing search capabilities (Perplexity / Google deep research / web search) and focused `site:` queries. Do not invent custom API integrations.
- Search GitHub first for every request. Do not skip directly to package indexes or model hubs.
- Keep the search narrow and evidence-based. Inspect only the strongest candidates instead of scraping large result sets.
- For each serious GitHub candidate, inspect repository structure and at least 1 to 3 implementation files. Do not rely on `README`, repo description, or tags alone to judge actual capabilities.
- Include a real clickable URL for every project, package, model, or dataset mentioned.
- Do not fabricate popularity, maintenance, or capability claims. If evidence is weak, say so explicitly.
- Use current maintenance and adoption signals. Prefer real recency indicators, stars, forks, downloads, model likes, or similar ecosystem-specific traction signals when available.
- Stop and ask for confirmation after the GitHub phase and again after the secondary-platform phase before continuing to a broader search or final synthesis.

## Triggering

Use this skill proactively when the user is clearly about to build a complete product, subsystem, or workflow from scratch, even if they did not explicitly ask for a build-vs-buy review yet.

Strong trigger patterns:

- "I want to build", "help me build", "I am going to make", "create a project for"
- complete systems such as auth, upload, queue, editor, parser, crawler, chat, scheduling, feature flags, developer portals, agent frameworks, or workflow engines
- requests that imply a reusable product rather than a one-off script or tiny fix
- "from scratch", "without dependencies", "implement my own", "no framework"

High-frequency wheel-making areas:

- auth and permissions
- parsing and document extraction
- infrastructure and workflow orchestration
- common business subsystems such as billing, uploads, editors, dashboards, or notifications
- AI agent frameworks, automation runners, and multimodal pipelines

Do not trigger by default when:

- the user explicitly says the task is for learning, teaching, or practice
- the user is debugging or modifying an existing codebase
- the request is a narrow algorithm, regex, or function-level question
- the user has already chosen a concrete upstream project and wants help using it
- the task is obviously local and one-off rather than a reusable product decision

## Platform Selection

Use GitHub first for every request, then choose only the most relevant secondary platforms:

- `software`: GitHub, then npm and PyPI when reusable packages or SDKs matter
- `ai`: GitHub, then Hugging Face and Roboflow when models, datasets, or demos matter
- `mixed`: GitHub first, then combine the most relevant software and AI ecosystems without searching everything

Stopping rules:

- if GitHub already shows one or more high-fit mature projects, narrow the secondary search to validation rather than expansion
- if secondary platforms add no strong new evidence, stop instead of widening the search further
- do not use "no exact-name match" as evidence for `Build from scratch`

## Workflow

### Phase 0: Frame The Request

Restate the idea in one short paragraph:

- what the user wants to build
- the primary users or use case
- the core capabilities implied by the request
- whether the idea is software/product, AI/CV, or mixed

Then derive a compact search plan:

- primary keywords
- synonyms and adjacent terms
- exclusions to avoid false positives
- likely platform sequence after GitHub

Prefer capability-oriented phrasing over marketing language. Break compound ideas into searchable building blocks.

### Phase 1: GitHub Baseline Search

GitHub is mandatory and always comes first. Use targeted search queries such as `site:github.com <keywords>`. Prioritize reusable projects over tutorials, blog posts, wrappers, and abandoned demos.

For the top 3-5 serious candidates, capture only the minimum evidence needed:

- project name
- URL
- one-line purpose
- apparent scope and fit
- source inspection evidence from repository structure plus 1 to 3 key implementation files
- maintenance recency
- traction indicators
- obvious strengths or red flags

Use `README` only as an entry point. Before you describe what a repository can actually do, verify it against code evidence such as:

- repository structure and major modules
- entrypoints, CLI wiring, server startup, or package exports
- core implementation files for the claimed capability
- configuration, examples, tests, or adapters that confirm the real execution path

When code inspection is partial, say exactly what was verified from source and what remains unverified.

Then pause and report the reformulated idea, search terms, top candidates, leading ecosystem patterns, and what is still unknown. End this phase by explicitly asking whether to continue to secondary platforms, narrow the problem, or stop with a GitHub-first verdict.

### Phase 2: Secondary Platform Search

Choose platforms based on the idea type. Do not search every ecosystem by default.

For software or product ideas, prefer npm and PyPI. For AI, ML, or CV ideas, prefer Hugging Face and Roboflow. For mixed ideas, use both but stay selective.

Limit detailed analysis to the top relevant candidates from each platform. Treat packages, models, and datasets as evidence of ecosystem maturity and reusable building blocks, not proof that the full product already exists.

If a search yields nothing useful, apply zero-result recovery before concluding the space is empty:

- remove overly specific qualifiers
- swap in synonyms
- search for the adjacent workflow rather than the exact product framing
- broaden from branded phrasing to capability phrasing

After this phase, pause again and summarize which additional ecosystems were checked, the strongest non-GitHub candidates, whether the ecosystem suggests adopt/fork/build pressure, and what uncertainty remains.

### Phase 3: Final Verdict

Produce a concise decision report with these sections:

1. `Idea Restatement`
2. `Search Strategy`
3. `Candidate Comparison`
4. `Maturity Analysis`
5. `Gaps vs Requested Idea`
6. `Recommendation`
7. `Suggested Next Actions`

The `Candidate Comparison` section should be a compact table when possible. Evaluate each serious candidate on:

- relevance to the requested idea
- maintenance recency
- community traction
- completeness
- forkability or extensibility
- execution risk

The `Recommendation` section must choose exactly one:

- `Adopt existing project`
- `Fork/compose an existing component`
- `Build from scratch`

Justify the winning option and explain why the other two did not win.

## Decision Heuristics

Lean toward `Adopt existing project` when:

- one candidate already solves most of the core problem
- maintenance and community signals are healthy
- customization needs appear modest

Lean toward `Fork/compose an existing component` when:

- a full solution is not a fit, but strong subsystems exist
- the gap is architectural integration, productization, or domain adaptation
- the upstream project is viable enough to reuse but not enough to adopt whole

Lean toward `Build from scratch` when:

- available options are stale, narrow, or structurally mismatched
- the idea depends on differentiated workflow or architecture not present upstream
- reuse would add more complexity than it removes

Do not recommend building from scratch just because no exact-name match exists. Look for reusable adjacent projects and components first.

## User's Framework-Tier Rule (this fork's delta)

When a build is actually warranted (after the full build-vs-buy pass), the user's framework policy applies:

- Tier 0 (language-level, always available): React, Vue, Flutter, Next.js, Prisma — treat as base infrastructure, never a reason to write own code.
- Tier 1 (problem-tailored): use the most specific framework that solves ~99% of the task. You still write ~1% glue. Example: scheduling board → a scheduling/calendar component library, not a hand-rolled calendar.
- NEVER choose a general-purpose framework where a problem-tailored one exists (e.g. don't hand-roll auth when a tailored auth library solves it).
- The ONLY acceptable reason to write own code at all: the needed capability exists only closed-source. Then do 10x deeper research first. If nothing free/open works right away, only then use a problem-tailored framework and write the minimum glue.
- Ditch any "no-dependency" philosophy — dependencies are the point. The best code is the code never written.

## Output Discipline

- Prefer compact summaries over raw dumps.
- Mention only the strongest candidates.
- Call out uncertainty instead of padding with weak evidence.
- Distinguish between repositories, packages, models, datasets, and end-user products.
- Treat recent updates and community traction as evidence, not guarantees.
- If the user asks for a deeper pass after the final verdict, continue from the strongest branch instead of restarting from scratch.
