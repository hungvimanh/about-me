<!-- gitnexus:start -->
# GitNexus — Code Intelligence

This project is indexed by GitNexus as **portfolio** (356 symbols, 436 relationships, 0 execution flows). Use the GitNexus MCP tools to understand code, assess impact, and navigate safely.

> If any GitNexus tool warns the index is stale, run `npx gitnexus analyze` in terminal first.

## Always Do

- **MUST run impact analysis before editing any symbol.** Before modifying a function, class, or method, run `gitnexus_impact({target: "symbolName", direction: "upstream"})` and report the blast radius (direct callers, affected processes, risk level) to the user.
- **MUST run `gitnexus_detect_changes()` before committing** to verify your changes only affect expected symbols and execution flows.
- **MUST warn the user** if impact analysis returns HIGH or CRITICAL risk before proceeding with edits.
- When exploring unfamiliar code, use `gitnexus_query({query: "concept"})` to find execution flows instead of grepping. It returns process-grouped results ranked by relevance.
- When you need full context on a specific symbol — callers, callees, which execution flows it participates in — use `gitnexus_context({name: "symbolName"})`.

## Never Do

- NEVER edit a function, class, or method without first running `gitnexus_impact` on it.
- NEVER ignore HIGH or CRITICAL risk warnings from impact analysis.
- NEVER rename symbols with find-and-replace — use `gitnexus_rename` which understands the call graph.
- NEVER commit changes without running `gitnexus_detect_changes()` to check affected scope.

## Resources

| Resource | Use for |
|----------|---------|
| `gitnexus://repo/portfolio/context` | Codebase overview, check index freshness |
| `gitnexus://repo/portfolio/clusters` | All functional areas |
| `gitnexus://repo/portfolio/processes` | All execution flows |
| `gitnexus://repo/portfolio/process/{name}` | Step-by-step execution trace |

## CLI

| Task | Read this skill file |
|------|---------------------|
| Understand architecture / "How does X work?" | `.claude/skills/gitnexus/gitnexus-exploring/SKILL.md` |
| Blast radius / "What breaks if I change X?" | `.claude/skills/gitnexus/gitnexus-impact-analysis/SKILL.md` |
| Trace bugs / "Why is X failing?" | `.claude/skills/gitnexus/gitnexus-debugging/SKILL.md` |
| Rename / extract / split / refactor | `.claude/skills/gitnexus/gitnexus-refactoring/SKILL.md` |
| Tools, resources, schema reference | `.claude/skills/gitnexus/gitnexus-guide/SKILL.md` |
| Index, status, clean, wiki CLI commands | `.claude/skills/gitnexus/gitnexus-cli/SKILL.md` |

<!-- gitnexus:end -->

<!-- hero-vibe-kit:start -->
<!-- Managed by hero-vibe-kit. Update via the framework; edits inside this block are overwritten on `update`. -->
# Agent Instructions — portfolio

> Canonical development process: **[docs/AGENCY_WORKFLOW.md](docs/AGENCY_WORKFLOW.md)** (single source of truth). Applies to any AI agent working in this repo (Claude Code, Cursor, and compatible tools).

Active operating profile:
- Active assistance profile: Vibecode (`vibecode`)
- Project surface: Frontend (`frontend`)
- Verification level: strict
- Profile rules: [docs/ASSISTANCE_PROFILES.md](docs/ASSISTANCE_PROFILES.md)

Minimum non-negotiables:
1. Classify the request via the router before acting; don't run heavy workflow for small tasks.
2. **Resume (fast path):** read `.hero-vibe-kit/session.json` first → then the `resumePath` it names → then the latest handoff. Read [ACTIVE_STATE](docs/ACTIVE_STATE.md) only to switch work items or when session is blank/stale.
3. Use Plan Mode for paths with Gates before editing.
4. Read only the docs needed for the selected path; avoid loading unrelated context.
4. Framework instructions, skills, rules, and templates are English-only; respond to the user in the same language they use in chat unless they request another language.
5. Do not bypass hooks, checks, or verification.
6. Use GitNexus for Standard/Full impact/context analysis when available.
7. **Sub-agent delegation follows the active profile** in [ASSISTANCE_PROFILES](docs/ASSISTANCE_PROFILES.md): Standard/Full review is path-triggered for Vibecode, while Coding Assistant keeps developer review central and applies its recommended/required review rules. Delegating implementation is optional; sub-agents shine at research and review, and not every task needs one. See [TEAM_ROSTER](docs/TEAM_ROSTER.md).
8. Sub-agent model/effort selection follows [TEAM_ROSTER](docs/TEAM_ROSTER.md); do not hardcode model IDs elsewhere.
9. Keep outputs concise: findings, decisions, risks, next steps.
<!-- hero-vibe-kit:end -->
