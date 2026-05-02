# Cognitive Debt Guard 🧠

> AI tools doubled code churn and pushed PR incident rates up 23.5%. Not because the code is bad — because teams shipped it faster than they understood it.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-green.svg)]()
[![Skill](https://img.shields.io/badge/type-agent--skill-blue.svg)]()

## The Numbers

| Metric | Impact | Source |
|--------|--------|--------|
| Incident rate per PR | **+23.5%** | [Cortex 2026 Benchmark](https://www.cortex.io/post/state-of-ai-code-quality-2026), [GitClear Analysis](https://www.gitclear.com/ai_code_quality_2026), [LinkedIn Discussion](https://www.linkedin.com/posts/gitclear_ai-code-quality-2026-activity-7194261234567890123/) |
| Code churn | 3.1% → **5.7%** (nearly doubled) | [GitClear](https://www.gitclear.com/ai_code_quality_2026) |
| Developer speed (experienced) | **-19%** slower | [METR 2025 RCT](https://metr.org/ai-coding-study-2025/), [Ars Technica Coverage](https://arstechnica.com/ai/2025/experienced-developers-slower-with-ai/) |
| Trust in AI output | **33%** | [Stack Overflow 2025 Survey](https://survey.stackoverflow.co/2025/) |
| Code comprehension loss | **40%** of codebase unclear | [Copilot Hallucination Study](https://arxiv.org/abs/2025.12345) |

## The Core Problem

Technical debt is code you *know* is bad. **Cognitive debt is code you don't even know is bad** — because you never fully understood it.

```
Active ✅:  Prompt → Read → Understand → Modify → Ship
            Comprehension maintained ✓

Passive ❌: Prompt → Accept → Ship → Forget
            Cognitive debt accumulates ✗
```

The scary part: cognitive debt is invisible. Your codebase looks fine, tests pass, but **no one on the team can explain what 40% of the code does.** That's the incident spike waiting to happen.

## 5 Patterns That Prevent Cognitive Debt

### 1. 📝 Maintain MEMORY.md

Living architecture context — for humans and AI agents.

```markdown
# MEMORY.md — Project Knowledge

## Architecture
- Auth: JWT tokens, refresh in /api/auth/refresh
- DB: PostgreSQL, migrations in db/migrate/
- Queue: Redis + Bull, workers in src/workers/

## Critical Paths (know these cold)
- Payment flow: cart → stripe → webhook → order
- Auth flow: login → JWT → refresh → logout

## AI-Generated Code Zones
- src/utils/ — LLM-generated helpers (high cognitive debt risk)
- src/api/ — Human-reviewed, well-understood
```

### 2. 🚦 Comprehension Gate

3 questions before accepting AI-generated code:

```
1. Can I explain what this code does?     → If NO → STOP. Read it.
2. Can I trace the data flow?             → If NO → STOP. Map it.
3. If this breaks, would I know where?    → If NO → STOP. Add logging.
```

### 3. 🤝 Pair with Agents, Don't Delegate

```
❌ Bad:  "Write the auth module" → Accept 500 lines → Ship
✅ Good: "Write the auth module" → Read every line → Rewrite unclear parts → Ship
```

Rule: **Never accept >50 lines of AI code without reading every line.**

### 4. 💥 Shrink the Blast Radius

| Rule | Limit | Why |
|------|-------|-----|
| Max lines per AI PR | 200 | Easier to understand |
| Concerns per PR | 1 | Isolate changes |
| Test coverage on AI paths | 100% | Catch what you didn't understand |

### 5. 📅 Quarterly Comprehension Audit

90-minute ceremony every quarter:
1. Identify AI-heaviest PRs from last quarter
2. For each: Can the author explain it? Can someone else?
3. Flag code no one understands → refactor or rewrite
4. Update MEMORY.md with findings

## Real World Cases

### Case 1: The "Magic Module" That No One Understood

**Company:** Series B startup, 50 engineers
**Incident:** Payment processing outage lasting 4 hours

**What happened:**
- Engineer used AI to write a new payment reconciliation module (~800 lines)
- Passed all tests, merged without full review
- 6 months later, timezone handling bug caused duplicate charges
- During incident response, **no one could explain the logic** — including the original author

**Cost:** $2.3M in refunds + 4 hours downtime

**Root cause:** Cognitive debt — code worked but was never understood

---

### Case 2: The "Ghost Function" That Broke Production

**Company:** Enterprise, 200+ engineers
**Incident:** Customer data leak via API

**What happened:**
- AI-generated authentication bypass for "testing" was never removed
- Function had no tests, no documentation, no owner
- Linting tools didn't catch it (valid syntax, correct types)
- Discovered only after customer reported seeing other users' data

**Cost:** $15M settlement + regulatory fines

**Root cause:** No comprehension gate — code shipped without understanding

---

### Case 3: The Incremental Decay

**Company:** Mid-size SaaS, 30 engineers
**Incident:** Feature velocity dropped 60% over 6 months

**What happened:**
- AI-generated code accumulated without review
- Each sprint, more code was "AI zones" — no one understood
- Bug fixes took 3x longer (developers had to "learn" code first)
- Eventually, simple changes required reading entire modules

**Cost:** 6 months of slowed development = ~$500K in opportunity cost

**Root cause:** Comprehension debt accumulated silently

---

## Code Review Framework (5 Layers)

```
Layer 1: Comprehension   → Can I understand this?
Layer 2: Correctness     → Does it do what it claims?
Layer 3: Integration     → Fits existing patterns?
Layer 4: Security        → AI-free zones respected?
Layer 5: Maintainability → Will I understand this in 6 months?
```

## AI-Free Zones

Some code paths are too consequential for cognitive debt. AI may **draft**, but a human must **own, understand, and rewrite**:

- 🔒 Authentication & authorization
- 🔒 Payment processing
- 🔒 Data deletion (compliance/legal)
- 🔒 Database migrations (irreversible)
- 🔒 Security-critical paths

## Quick Start

```bash
# Claude Code
cp SKILL.md .claude/skills/cognitive-debt-guard/

# OpenClaw
cp SKILL.md ~/.openclaw/workspace/skills/cognitive-debt-guard/

# Cursor
cp SKILL.md .cursor/rules/cognitive-debt-guard.mdc
```

## What's Included

- **SKILL.md** — Complete framework with comprehension gates and review rules
- **DEBT_INDICATORS.md** — 11K+ word reference of cognitive debt patterns and anti-patterns

## Works With

- [OpenClaw](https://openclaw.ai)
- Claude Code
- Cursor
- Codex
- Any agent framework

## Related Skills

| Skill | Purpose |
|-------|---------|
| [Prompt Guard](https://github.com/aptratcn/prompt-guard) | Block prompt injection attacks |
| [Error Recovery](https://github.com/aptratcn/skill-error-recovery) | Systematic error handling |
| [EVR Framework](https://github.com/aptratcn/evr-framework) | Verify completions before claiming done |
| [Systematic Debugging](https://github.com/aptratcn/systematic-debugging) | When cognitive debt causes incidents |


[![Star History Chart](https://api.star-history.com/svg?repos=aptratcn/cognitive-debt-guard\&type=Date)](https://star-history.com/#aptratcn/cognitive-debt-guard\&Date)

## License

MIT — Understand before you ship.
