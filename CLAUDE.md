# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Purpose

This is the **Showroom course repo** for a developer course on [Beads](https://github.com/gastownhall/beads) — the git-backed agentic memory system. Content is authored in Antora/Asciidoc using the `rhpds/showroom_template_nookbag` template.

Course audience: developers with zero prior Beads experience.

## Course Structure

| Module | Working Title | Time |
|--------|--------------|------|
| 1 | The Problem & The Fix | ~35 min |
| 2 | The Daily Loop | ~35 min |
| 3 | Claude Code as Your Beads Partner | ~40 min |
| 4 | Keeping It Healthy | ~25 min |
| Bonus | Integrating with GitHub | ~30 min |

See `docs/superpowers/specs/2026-04-24-beads-course-design.md` for full design spec.

## Key Resources

- Beads repo: https://github.com/gastownhall/beads
- Beads docs: https://gastownhall.github.io/beads
- Showroom template: https://github.com/rhpds/showroom_template_nookbag
- Beads blog post: https://yuv.ai/blog/beads-git-backed-memory-for-ai-agents-that-actually-remembers
- Best practices: https://steve-yegge.medium.com/beads-best-practices-2db636b9760c

## Showroom / Antora Authoring Conventions

When writing or reviewing course content (Asciidoc):

- `role="execute"` on source blocks renders a copy button
- Images/SVGs: use `link=self` (not `window=blank`) for lightbox popout
- No trailing period after credential examples
- No blank line after `====` admonition delimiter — breaks attribute substitution
- Pre-render Mermaid diagrams as SVGs for split-panel readability
- Target platform: macOS, Linux, Windows WSL

<!-- BEGIN BEADS INTEGRATION v:1 profile:minimal hash:ca08a54f -->
## Beads Issue Tracker

This project uses **bd (beads)** for issue tracking. Run `bd prime` to see full workflow context and commands.

### Quick Reference

```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --claim  # Claim work
bd close <id>         # Complete work
```

### Rules

- Use `bd` for ALL task tracking — do NOT use TodoWrite, TaskCreate, or markdown TODO lists
- Run `bd prime` for detailed command reference and session close protocol
- Use `bd remember` for persistent knowledge — do NOT use MEMORY.md files

## Session Completion

**When ending a work session**, you MUST complete ALL steps below. Work is NOT complete until `git push` succeeds.

**MANDATORY WORKFLOW:**

1. **File issues for remaining work** - Create issues for anything that needs follow-up
2. **Run quality gates** (if code changed) - Tests, linters, builds
3. **Update issue status** - Close finished work, update in-progress items
4. **PUSH TO REMOTE** - This is MANDATORY:
   ```bash
   git pull --rebase
   bd dolt push
   git push
   git status  # MUST show "up to date with origin"
   ```
5. **Clean up** - Clear stashes, prune remote branches
6. **Verify** - All changes committed AND pushed
7. **Hand off** - Provide context for next session

**CRITICAL RULES:**
- Work is NOT complete until `git push` succeeds
- NEVER stop before pushing - that leaves work stranded locally
- NEVER say "ready to push when you are" - YOU must push
- If push fails, resolve and retry until it succeeds
<!-- END BEADS INTEGRATION -->
