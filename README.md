# claude-code-bootstrap

`~/.claude/CLAUDE.md` tells Claude Code how you work. It persists across projects and sessions. The problem is nobody writes one because it's not obvious what belongs in it.

This repo generates one for you. Clone it, open Claude Code, type "bootstrap me".

```bash
git clone https://github.com/akhljndl/claude-code-bootstrap.git
cd claude-code-bootstrap
claude
```

It asks ~8 questions about your workflow, then writes a `~/.claude/CLAUDE.md` matched to your answers, plus PostToolUse hooks for your languages.

## What it configures

Task approach:
- Plan before coding, or just go? How strict is the lifecycle?
- Auto-run code review after changes, or ask first?
- Keep docs in sync with code automatically?

Communication style:
- Concise or detailed responses
- Propose agents (planner, reviewer, architect) before launching, or just run them?

Parallel coordination:
- Multiple agents share findings via `docs/working-docs/`
- You pick whether those docs persist or get cleaned up

Hooks on every edit:
- Auto-formatting and linting for Python, Go, TypeScript
- Installs missing tools the hooks depend on

## The interview

| # | Question | Default |
|---|----------|---------|
| 0 | Quick start or full interview? | - |
| 1 | How autonomous should agents be? | Propose first, then run |
| 2 | How to handle parallel agent working docs? | Keep decisions, delete scratch |
| 3 | What languages do you use? | Auto-detected |
| 4 | Biggest pain point with AI assistants? | Missing workflow |
| 5 | Auto-run code reviews after changes? | Yes |
| 6 | Auto-update docs after structural changes? | Yes |
| 7 | What do you build? | Mix of everything |
| 8 | How strict is PLAN, IMPLEMENT, REVIEW, DOCUMENT? | Follow by default, skip for simple tasks |

Quick start accepts all defaults. Working setup in under a minute.

## Existing setup?

If you already have a `~/.claude/` config, the bootstrap scans it first:
- Detects your languages from installed hooks and rules
- Finds broken hooks (referencing tools that aren't installed)
- Spots duplicate hooks (plugins overlapping with manual hooks)
- Fixes what it finds, asks before changing anything

Safe to re-run. Detects previous bootstraps and offers to refresh or just health-check.

## Works with

- [everything-claude-code](https://github.com/affaan-m/everything-claude-code) -- detected automatically, no duplicate work. Not required.
- Any Claude Code setup, new or existing.

## Philosophy

The defaults are opinionated. They come from what actually works:

- Code is law -- when code changes, docs update in the same commit
- Surgical changes -- change what was asked, nothing more
- Simplicity first -- no abstractions for single-use code
- Goal-driven -- every task starts with "what does done look like?"
- Parallel by default -- independent agents run concurrently

All overridable during the interview.

## License

MIT
