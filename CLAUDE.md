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
## 🧭 hero-vibe-kit workflow

> **READ BEFORE DOING ANYTHING:** [`docs/AGENCY_WORKFLOW.md`](docs/AGENCY_WORKFLOW.md) is the **single source of truth** for the portfolio development process. Classify every request via the router table → pick a path (Read-only / Fast / Standard / Full). Don't run the heavy process for small tasks.

> **Active operating profile:**
> - Active assistance profile: Vibecode (`vibecode`)
> - Project surface: Frontend (`frontend`)
> - Verification level: strict
> See [ASSISTANCE_PROFILES](docs/ASSISTANCE_PROFILES.md) before changing gate, delegation, or verification strictness.

### Context loading
- **Always start with:** [AGENCY_WORKFLOW](docs/AGENCY_WORKFLOW.md) for routing, gates, sub-agents, and path-specific requirements.
- **Resume (fast path):** read `.hero-vibe-kit/session.json` first → then the `resumePath` it names → then the latest handoff only if needed. Read [ACTIVE_STATE](docs/ACTIVE_STATE.md) only to switch work items or when session is blank/stale.
- **Artifacts:** read [ARTIFACTS_AND_STORAGE](docs/ARTIFACTS_AND_STORAGE.md) only when creating/linking PRDs, plans, reports, design assets, or help content.
- **Completion:** read [DEFINITION_OF_DONE](docs/DEFINITION_OF_DONE.md) before claiming done.
- **Read on demand:** [BRANCHING](docs/BRANCHING.md), [TEAM_ROSTER](docs/TEAM_ROSTER.md), [COMMUNICATION_PROTOCOL](docs/COMMUNICATION_PROTOCOL.md), [SECURITY_STANDARDS](docs/SECURITY_STANDARDS.md), [PERFORMANCE_STANDARDS](docs/PERFORMANCE_STANDARDS.md), [DESIGN_STANDARDS](docs/DESIGN_STANDARDS.md), [BROWNFIELD_DISCOVERY](docs/BROWNFIELD_DISCOVERY.md), and templates under `docs/templates/` only when the selected path requires them.

### Non-negotiables
- **Gates:** when a path requires a Gate, use Plan Mode (`EnterPlanMode` → `ExitPlanMode`) for real sign-off — not a prose promise.
- **Enforcement:** `git-guard` (PreToolUse) + `stop-reminder` (Stop) hooks are installed under `.claude/`. Don't bypass them.
- **GitNexus (if installed):** skip on empty repos; use impact/context analysis for Standard/Full code changes and stale-index checks per [AGENCY_WORKFLOW](docs/AGENCY_WORKFLOW.md).
- **Skills (if installed):** invoke relevant process skills via the `Skill` tool; do not load unrelated skill/docs context.
- **Language:** framework instructions, skills, rules, and templates are English-only. Respond to the user in the same language they use in chat unless they request another language.
- **Sub-agent delegation follows the active profile.** Resolve [ASSISTANCE_PROFILES](docs/ASSISTANCE_PROFILES.md) before changing review/QA strictness: Standard/Full review is path-triggered for Vibecode, while Coding Assistant keeps developer review central and applies its recommended/required review rules. Sub-agents are best for research and review; **delegating implementation is optional** — use when it helps, and not every task needs one. Sub-agent model/effort selection follows [TEAM_ROSTER](docs/TEAM_ROSTER.md); do not hardcode model IDs elsewhere.
<!-- hero-vibe-kit:end -->
