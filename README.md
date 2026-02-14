# claude-code-bootstrap

Most people install Claude Code and start prompting immediately. It works — but Claude doesn't know how you think, what your workflow looks like, or what it should do without being told.

`~/.claude/CLAUDE.md` is the most underused file in your setup. It's where you teach Claude how you work — once — and it remembers across every project, every session. But nobody writes one from scratch because it's not obvious what to put in it.

This repo fixes that. Clone it, open Claude Code, say **"bootstrap me"**.

```bash
git clone https://github.com/akhljndl/claude-code-bootstrap.git
cd claude-code-bootstrap
claude
```

Claude asks you ~8 questions about how you work, then generates a `~/.claude/CLAUDE.md` tuned to your answers — plus hooks and tooling to back it up.

## What it configures

**How Claude approaches tasks:**
- Should it plan before coding, or just go? How strict is the lifecycle?
- Should it auto-run code review after changes, or ask first?
- Should it keep docs in sync with code automatically?

**How Claude talks to you:**
- Too verbose? It'll be concise. Too passive? It'll take initiative.
- Should it propose agents (planner, reviewer, architect) or just launch them?

**How parallel work stays coordinated:**
- When multiple agents run simultaneously, they share findings via `docs/working-docs/`
- You choose whether those docs stick around or get cleaned up

**What runs automatically on every edit:**
- Auto-formatting and linting hooks for your languages (Python, Go, TypeScript)
- Installs any missing tools the hooks need

## The interview

| # | Question | Default |
|---|----------|---------|
| 0 | Quick start or full interview? | — |
| 1 | How autonomous should agents be? | Propose first, then run |
| 2 | How to handle parallel agent working docs? | Keep decisions, delete scratch |
| 3 | What languages do you use? | Auto-detected |
| 4 | Biggest pain point with AI assistants? | Missing workflow |
| 5 | Auto-run code reviews after changes? | Yes |
| 6 | Auto-update docs after structural changes? | Yes |
| 7 | What do you build? | Mix of everything |
| 8 | How strict is PLAN → IMPLEMENT → REVIEW → DOCUMENT? | Follow by default, skip for simple tasks |

**Quick start** accepts all defaults — you get a working setup in under a minute.

## Existing setup?

If you already have a `~/.claude/` config, the bootstrap scans it first:
- Detects your languages from installed hooks and rules
- Finds broken hooks (referencing tools that aren't installed)
- Spots duplicates (plugin hooks overlapping with your hooks)
- Fixes what it finds, asks before changing anything

Safe to re-run. It detects previous bootstraps and offers to refresh or just health-check.

## Works with

- **[everything-claude-code](https://github.com/affaan-m/everything-claude-code)** — detected automatically, no duplicate work. Not required.
- **Any Claude Code setup** — greenfield or existing.

## Philosophy

The defaults are opinionated. They come from a workflow that actually works in practice:

- **Code is law** — when code changes, docs update in the same commit
- **Surgical changes** — change what was asked, nothing more
- **Simplicity first** — no abstractions for single-use code
- **Goal-driven** — every task starts with "what does done look like?"
- **Parallel by default** — independent agents run concurrently, not sequentially

All overridable during the interview.

## License

MIT
