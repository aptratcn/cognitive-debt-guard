# Cognitive Debt Guard 🧠

> Prevent the 23.5% incident spike from AI-generated code

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**AI tools doubled code churn to 5.7% and pushed PR incident rates up 23.5%.** Root cause: teams shipped code faster than they understood it.

Cognitive Debt Guard gives you the framework to use AI tools **actively** — without losing comprehension.

## The Numbers

| Metric | Impact | Source |
|--------|--------|--------|
| Incident rate | **+23.5%** per PR | Cortex 2026 Benchmark |
| Code churn | 3.1% → **5.7%** (nearly doubled) | GitClear |
| Developer speed | **-19%** slower (experienced devs) | METR 2025 RCT |
| Trust in AI output | **33%** (down from higher) | Stack Overflow 2025 |

## The Core Problem

Unlike technical debt (code you *know* is bad), cognitive debt is code you **don't even know is bad** — because you never fully understood it.

| Pattern | Result |
|---------|--------|
| Active ✅: Prompt → Read → Understand → Modify → Ship | Comprehension maintained |
| Passive ❌: Prompt → Accept → Ship → Forget | Cognitive debt accumulates |

## 5 Patterns That Prevent Cognitive Debt

### 1. Maintain MEMORY.md
Living architecture context for humans and AI agents.

### 2. Comprehension Gate
3 questions before accepting AI-generated code:
1. Can I explain what this code does?
2. Can I trace the data flow?
3. If this breaks, would I know where to look?

### 3. Pair with Agents, Don't Delegate
Never accept >50 lines of AI code without reading every line.

### 4. Shrink the Blast Radius
- Max 200 lines per AI PR
- 1 concern per PR
- 100% test coverage on AI paths

### 5. Quarterly Comprehension Audit
90-minute sprint ceremony to review AI-heaviest PRs.

## Quick Start

```
# Install
clawhub install cognitive-debt-guard

# Or clone
git clone https://github.com/aptratcn/cognitive-debt-guard.git
```

## Code Review Framework (5 Layers)

```
Layer 1: Comprehension — Can I understand this?
Layer 2: Correctness   — Does it do what it claims?
Layer 3: Integration   — Fits existing patterns?
Layer 4: Security      — AI-free zones respected?
Layer 5: Maintainability — Will I understand this in 6 months?
```

## AI-Free Zones

Some code paths are too consequential for cognitive debt:
- 🔒 Authentication & authorization
- 🔒 Payment processing
- 🔒 Data deletion (compliance)
- 🔒 Database migrations (irreversible)

AI may draft. A human must own, understand, and rewrite.

## Related Skills

- [EVR Framework](https://github.com/aptratcn/evr-framework) — Verify before claiming "done"
- [Systematic Debugging](https://github.com/aptratcn/systematic-debugging) — When cognitive debt causes incidents
- [Prompt Guard](https://github.com/aptratcn/prompt-guard) — Security-first AI interactions

## License

MIT
