# Beads Developer Course — Design Spec

**Date:** 2026-04-24
**Status:** Approved

---

## Overview

A self-paced developer course teaching Beads — the git-backed agentic memory system — to developers with zero prior Beads experience.

**Working title:** *Beads: Git-Backed Memory for Your Coding Agent*
**Tagline:** Stop losing context. Start shipping smarter.

**Completion time:** ~2h 45min total (4 core modules + 1 bonus)

---

## Audience

Developers who use Claude Code (or any AI coding agent) and experience:
- Re-explaining context to their agent every session
- Losing track of tasks across sessions
- No clear system for managing long-running agentic work

**Prerequisites:** Comfortable with git and a terminal. No Beads, Dolt, or agentic workflow experience needed.

**Environment:** Bring Your Own Machine — macOS, Linux, or Windows WSL. Claude Code is the primary AI harness used in examples.

---

## Learning Outcomes

By completing this course, learners will be able to:

1. Install and initialize Beads in any project
2. Use `bd create`, `bd ready`, `bd update`, `bd close` as their daily task loop
3. Configure Claude Code to prime Beads context automatically at session start
4. Keep their Beads installation healthy with `bd doctor`, cleanup, and upgrades
5. *(Bonus)* Connect Beads to a GitHub repo and link issues to PRs

**Explicit scope boundary — not covered:**
- Team/multi-writer Dolt remotes
- Formulas, molecules, or gates
- Jira integration

---

## Course Structure

### Module 1 — The Problem & The Fix (~35 min)

**Narrative:** Your agent forgets everything between sessions. Beads fixes that.

**Concepts:**
- What Beads is and why agent memory matters
- The `.beads/` directory and Dolt-backed storage
- Hash-based issue IDs and what makes them agent-safe

**Lab:**
- Install Beads (`curl` or Homebrew)
- `bd init` in an existing git project (learner's own repo or a provided sample clone)
- `bd create` a first issue, `bd show` it, `bd close` it

**Exit outcome:** Learner has a working Beads install and has run the full create→close cycle once.

---

### Module 2 — The Daily Loop (~35 min)

**Narrative:** Beads only works if it becomes a reflex, not a chore.

**Concepts:**
- The core habit loop: create → ready → claim → close → remember
- `bd ready` as the agent's starting point each session
- `bd remember` for storing insights that survive session boundaries

**Lab:**
- Simulate a mini coding session end-to-end
- Use `bd ready` to find work, `bd update --claim` to start it
- Complete the task and `bd close` with a reason
- Use `bd remember` to store a key architectural decision

**Exit outcome:** Learner can run a full agentic work session using Beads as the task backbone.

---

### Module 3 — Claude Code as Your Beads Partner (~40 min)

**Narrative:** The real payoff — Claude and Beads working together automatically.

**Concepts:**
- What `bd prime` outputs and why Claude needs it
- `CLAUDE.md` injection pattern for Beads context
- `SessionStart` hooks in `.claude/settings.json`
- What "context priming" means and why it matters at session start
- `bd remember` as cross-session memory for Claude

**Lab:**
- Add `bd prime` as a `SessionStart` hook in `.claude/settings.json`
- Start a new Claude Code session and verify it sees open issues
- Use `bd remember` to store an insight; start a new session and verify recall
- Walk through a realistic session: Claude files issues, claims work, closes on completion

**Exit outcome:** Claude Code automatically knows the project's open work at the start of every session, without manual re-briefing.

---

### Module 4 — Keeping It Healthy (~25 min)

**Narrative:** Small maintenance habits prevent big headaches.

**Concepts:**
- `bd doctor` — what it checks and how to read its output
- Issue DB size limits (~500 items) and why they matter
- `bd compact` and `bd stale` for hygiene
- Upgrade cadence (weekly/bi-weekly recommended)
- Common failure modes and how to recover

**Lab:**
- Run `bd doctor` and interpret the output
- Create a stale issue and use `bd stale` to surface it
- Simulate an orphaned dependency and clean it up with `bd orphans`
- Check the installed version and walk through the upgrade path

**Exit outcome:** Learner has a maintenance checklist and knows how to diagnose common Beads problems.

---

### Bonus Module — Integrating with GitHub (~30 min)

**Narrative:** Your Beads issues and your GitHub repo, talking to each other.

**Concepts:**
- `bd config set github.org` / `github.repo` configuration
- Beads ↔ GitHub Issues sync
- PR linking: connecting a Beads issue to an open pull request
- Using `bd` alongside `gh` CLI without conflicts

**Lab:**
- Configure Beads with a GitHub repo
- Push a Beads issue to GitHub Issues
- Link an open PR to a Beads issue
- Verify the two-way relationship in both `bd show` and the GitHub UI

**Exit outcome:** Learner can surface Beads work in GitHub and link code reviews back to the issues that motivated them.

---

## Content Format (Showroom / Antora)

- Platform: Showroom template (`rhpds/showroom_template_nookbag`), Antora + Asciidoc
- `role="execute"` on all copyable source blocks
- Images/SVGs: `link=self` for lightbox popout
- No blank line after `====` admonition delimiter
- Pre-render Mermaid diagrams as SVGs
- No trailing period after credential/command examples

---

## Key Resources

- Beads repo: https://github.com/gastownhall/beads
- Beads docs: https://gastownhall.github.io/beads
- Showroom template: https://github.com/rhpds/showroom_template_nookbag
- YUV blog post: https://yuv.ai/blog/beads-git-backed-memory-for-ai-agents-that-actually-remembers
- Yegge best practices: https://steve-yegge.medium.com/beads-best-practices-2db636b9760c
