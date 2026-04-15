# Vibe Coding Methodology

A structured, human-led methodology for planning and executing software projects with Claude Code (or any AI coding assistant). The core principle: planning is 2-3x longer than implementation — by design.

## Time Allocation

| Phase | Time | Description |
|-------|------|-------------|
| Phases 1-4 | ~50% | Project plan (objective, research, refinement, rewrite) |
| Phase 5 | ~25% | Implementation plan (ordering, steps, verification) |
| Phase 6 | ~25% | Execution (one step at a time) |

---

## Phase 1 — Human-Written Foundation

**Who writes:** You. No AI.

Write a text document with:

1. **Title** — what you're building
2. **Objective** — 2-3 lines on what you actually want to achieve and why
3. **Non-goals** — what is explicitly out of scope (prevents scope creep during execution)
4. **Key bullet points** — 5-10 high-level things that need to happen, straight from your head

This is your thinking, unfiltered. No AI assistance. You need to own the vision before anything else touches it.

### Why non-goals matter

The most common planning failure is scope creep during Phase 6. If you don't explicitly state what you're *not* building, you (or the AI) will naturally expand the scope. "Out of scope: mobile responsiveness, auth, analytics" costs you 30 seconds to write and saves hours of drift.

---

## Phase 2 — Research Document

**Who writes:** Claude.

Tell Claude to read all relevant parts of the project — codebase, docs, APIs, config — and produce a comprehensive research document alongside your plan.

- Be explicit: "Be super thorough. Don't leave anything out."
- This document can be long — 2,000-5,000 lines is normal for a complex project
- It should cover: existing architecture, relevant files, API contracts, data models, dependencies, constraints
- **Include external dependencies** — API keys needed, access to grant, third-party services to test, other people's work that must land first

This research doc is the AI's "memory" for the rest of the process. Instead of re-reading the codebase every time, you point it here. It saves enormous amounts of redundant searching.

### Tip: version control from here

Initialize git tracking on your plan document now. Every subsequent edit will show up as a diff, which is far faster to review than re-reading the whole document.

---

## Phase 3 — Iterative Refinement

**Who writes:** Both. Claude identifies issues, you make decisions.

Do 3-4 rounds of:

1. Tell Claude: "Read the research document and the plan. Find contradictions, missing decisions, ambiguities, and things I haven't thought about."
2. Claude writes its findings **at the bottom of the file** — not inline edits
3. You write your responses directly in the document under each item
4. Pick **one issue** and discuss it. Resolve it fully before moving to the next.

### Rules

- **One issue at a time.** Claude gets confused when handling multiple discussions simultaneously. One topic per round keeps it focused and accurate.
- **You do the writing.** Claude proposes, you decide. Add your responses in bullet point format directly in the document.
- **Surface blockers early.** If Claude identifies an external dependency (API access, credentials, someone else's work), flag it now so it can be unblocked in parallel.

### What to look for in each round

- **Round 1-2:** Structural gaps — missing components, incorrect assumptions, architectural issues
- **Round 3-4:** Finer issues — edge cases, error handling, naming, ordering constraints
- **Diminishing returns signal:** When Claude's findings are mostly cosmetic or hypothetical, you're done. Stop planning.

### Abort criteria

Define upfront: "If during implementation we discover X, we stop and re-plan." This turns the anxiety about fatal flaws into a concrete decision rule rather than a vague worry. Examples:
- "If the API doesn't support batch operations, this approach won't work — re-plan around individual calls"
- "If the migration takes more than 30 seconds on prod data, we need a different strategy"

---

## Phase 4 — Rewrite for Clarity

**Who writes:** Claude, then you review.

Once the content is solid:

1. Tell Claude: "Rewrite this plan for clarity. Remove as many words as possible without losing any accuracy."
2. The rewrite will naturally de-duplicate — your iterative edits will have introduced repetition
3. **Always read the rewrite.** LLMs will mess things up — subtle meaning changes, dropped details, softened constraints
4. Use `git diff` to see exactly what changed rather than re-reading the whole document
5. Fix anything that's wrong

### Definition of done (add it now)

Before leaving this phase, add a "Definition of Done" section at the top of the plan, near the objective:
- What does the user see when this is complete?
- What endpoints/pages/features work?
- What is the deploy state?
- How do you know it's shipped, not just "code complete"?

This prevents both gold-plating and stopping too early during Phase 6.

---

## Phase 5 — Implementation Plan

**Who writes:** Claude drafts, you review and edit.

Only start this after the project plan is locked down. This is a separate section — the explicit ordering of work.

1. Tell Claude: "Think really hard. Re-read the research document. Create an implementation plan with the explicit order in which these things need to happen."
2. Structure as **5-10 numbered steps**, each with:
   - What to do (sub-steps if needed)
   - **Verification criteria** — how to confirm this step worked before moving on
   - Which verifications Claude can do itself (tests pass, lint clean) vs. which are manual (check the database, load the URL, confirm the numbers)

### Review with inline notes

Go through the implementation plan line by line. Mark issues with a personal tag:

```
note AB - actually this has to happen before step 3 because of the foreign key constraint
note AB - this is wrong, the API uses POST not GET
note AB - fine, ignore this
```

Then tell Claude: "Find all `note AB` entries and address them one by one."

### Session handoff block

Add a 3-5 line "Current State" block at the very top of the plan:

```
## Current State
- Steps 1-3: complete
- Step 4: in progress — migration written, not yet run
- Blocker: waiting on API key from Alex
- Next: finish step 4, then step 5
```

Update this after each session. It means you (or Claude in a fresh context) can pick up without re-reading everything.

---

## Phase 6 — Execution

**Who writes:** Claude codes, you review.

### Setup
1. Clear the context (start a fresh conversation or compact)
2. Have Claude re-read the plan fresh
3. Confirm it understands the current state and what's next

### Per-step process

For each step:

1. **Instruct:** "Complete step N of this plan. Just step N, complete it to its entirety. Keep going until it meets the verification criteria."
2. **Wait:** Let Claude run to completion — this can take 20-30 minutes. Don't interrupt.
3. **Review:** Read every line of code that changed. Use `git diff`.
4. **Verify:** Run the verification criteria — both automated (tests, lint) and manual (load the page, check the data, confirm the numbers)
5. **Commit:** `git commit` after verified. This is your checkpoint.
6. **Update:** Update the "Current State" block in the plan
7. **Next:** Move to step N+1

### When things go wrong

- **Small plan adjustments:** Normal. Update the plan document and continue.
- **Step fails verification:** Debug with Claude in the same context. Don't move to the next step until this one is clean.
- **Hit an abort criterion:** Stop. Go back to Phase 3. Re-plan from the point of failure. Don't try to patch a fundamentally broken approach.
- **Context getting large (>200k tokens):** Clear context, re-read the plan, continue from current state. Ideally stay under 100k — quality degrades noticeably past 250k.

### What "done" looks like

When the last step is verified and committed, check your Definition of Done from Phase 4. If every criterion is met, you're done. If not, there's a gap in your plan — fill it and execute the missing piece.

---

## Quick Reference

```
Phase 1: Write objective + non-goals + key bullets (YOU, no AI)
Phase 2: Claude produces research document (comprehensive, 2-5k lines)
Phase 3: 3-4 rounds of contradiction/gap finding (one issue at a time)
Phase 4: Claude rewrites for clarity, you review diffs, add Definition of Done
Phase 5: Implementation plan with ordered steps + verification criteria
Phase 6: Execute one step at a time — instruct, wait, review, verify, commit
```

## Anti-Patterns

| Don't | Do instead |
|-------|------------|
| Ask Claude to do multiple things at once | One issue, one step at a time |
| Let Claude edit inline during refinement | Write findings at the bottom of the file |
| Skip to implementation ordering before the plan is solid | Phases 1-4 first, always |
| Re-read the whole document after every edit | Use git diffs |
| Keep going when context exceeds 250k tokens | Clear context, re-read plan, continue |
| Hope there are no fatal flaws | Define abort criteria upfront |
| Start coding before Phase 6 | No code until the plan is locked |
| Plan indefinitely | Stop when Claude's findings become cosmetic |
