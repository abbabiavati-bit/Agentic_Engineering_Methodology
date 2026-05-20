# Agentic Engineering Methodology

A structured, human-led methodology for planning and executing projects with AI agents: websites, apps, internal and external tools, autonomous agents, process automations, data workflows, multi-sided platforms, and complex software systems. Built from practitioner experience and refined with research from Andrej Karpathy, Addy Osmani, and the broader AI-assisted development community.

The core principle: **planning takes 2-3x longer than implementation — by design.** This is not overhead. This is where the leverage comes from.

## Who Is This For?

| If you are... | This helps you... |
|---------------|-------------------|
| A **developer** using Claude Code, Cursor, or Copilot | Stop vibe coding. Ship production-quality work with AI leverage and your name on it. |
| An **engineering lead or CTO** | Give your team a shared standard for AI-assisted development before the shortcuts become technical debt. |
| A **freelancer or consultant** | Deliver faster without quality loss. A methodology you can explain to clients builds trust. |
| A **startup founder** building with AI | Move fast without the slop. The plan is the leverage — not skipping it. |
| An **operator or automation builder** | Turn messy recurring work into bounded workflows with triggers, logs, and review points. |
| A **product, design, or project lead** | Convert fuzzy requirements into reviewable artifacts before anyone starts generating implementation. |
| A **student or career changer** | Learn the right habits from the start. AI work without methodology produces unmaintainable output. |
| **Anyone burned by vibe coding** | This is the antidote. Same AI, structured process, reviewable output. |

> If you can't read the diff, you can't verify the step. This methodology assumes you're the expert — AI is your force multiplier, not your replacement.

## The Spectrum

Not all AI-assisted work is the same. Know which mode you're in:

| Mode | When | Oversight | Example |
|------|------|-----------|---------|
| **Vibe work** | Throwaway projects, demos, exploration | None — accept all, don't inspect deeply | Weekend hack, proof of concept |
| **Agentic engineering** | Professional work you care about | High — review artifacts, diffs, outputs, and behaviour | Production features, client work, automations, agents |
| **Hand-built core** | Novel, sensitive, or off-distribution work | Total — you write the core, AI assists around it | Custom algorithms, irreversible operations, unconventional architectures |

This methodology is for **agentic engineering** — the middle column. You want the AI's leverage without compromising quality.

As Karpathy puts it: *"A tight leash on an over-eager junior intern savant with encyclopedic knowledge of software, but who also bullshits you all the time, has an over-abundance of courage and shows little to no taste for good code."*

## Time Allocation

| Phase | Time | What happens |
|-------|------|--------------|
| Phase 0 | 5-10 min | Triage — choose lightweight vs full workflow and identify risk level |
| Phases 1-4 | ~50% | Project plan — objective, research, refinement, rewrite |
| Phase 2.5 | 5-15% | Harness setup — persistent context, permissions, hooks, MCP, guardrails |
| Phase 4.5 (optional) | 0-15% | Artifact design — UI mockups, agent contracts, process maps, schemas, or runbooks |
| Phase 5 | ~25% | Implementation plan — ordering, steps, verification criteria |
| Phase 5.5 | 5-10% | Readiness gate — confirm context, constraints, env, and rollback before execution |
| Phase 6 | ~25% | Execution — one step at a time, review every changed artifact |
| Phase 6.5 | 5-15% | Final review and ship — fresh review, PR/deploy, post-ship checks |
| Phase 7 | ~0-10% | Skillify stable workflows (optional — most projects skip this) |

---

## Project Archetypes

Use the same phases for every project, but emphasize different evidence depending on what you are building.

| Archetype | Research should emphasize | Design/spec should produce | Verification should prove |
|-----------|---------------------------|----------------------------|---------------------------|
| **Website or app** | Existing code, brand rules, content, users, analytics, SEO, accessibility, device targets | Sitemap, key screens, user flows, responsive states, content model | Pages load, flows work, responsive states hold, accessibility and SEO basics pass |
| **Tool or product surface** | User roles, workflows, permissions, integrations, operational context, success metrics | Core workflows, permission model, screen or API map, rollout path | Core tasks work end to end for each role, permissions hold, operational handoff is clear |
| **Agent or chatbot** | User tasks, tool access, decision boundaries, failure modes, privacy, logs, evaluation cases | Agent boundary, tool contracts, conversation examples, escalation paths | Representative tasks pass, tool calls are logged, unsafe requests fail safely, handoff works |
| **Process automation** | Current manual workflow, triggers, inputs, exceptions, approvals, ownership, audit needs | Process map, trigger rules, eligibility rules, retry/stop conditions, notification path | Happy path and failure path work, idempotency holds, audit trail exists, humans can intervene |
| **Data or reporting workflow** | Source systems, schemas, freshness, reconciliation rules, sample data, consumers | Data contract, transformations, report mockup, quality checks, ownership | Numbers reconcile, stale/missing data is detected, sample outputs match expectations |
| **Knowledge / company brain system** | Source inventory, trust tiers, permissions, freshness, citations, retrieval quality, operating ownership | Source taxonomy, permission model, retrieval architecture, answer policy, evaluation plan | Permission fidelity holds, citations are correct, freshness is acceptable, retrieval quality supports real tasks |
| **Marketplace or platform ecosystem** | Distinct actor groups, supply/demand mechanics, pricing, trust and safety, search/ranking, identity, support, abuse, regional constraints | Service blueprint, actor journeys, marketplace rules, trust model, escalation and support paths | Each actor can complete their workflow, policy boundaries hold, marketplace mechanics behave as intended, abuse paths are covered |
| **Complex system or enterprise platform** | Architecture, service boundaries, permissions, integrations, migrations, operational constraints, support path, scale bottlenecks | Architecture sketch, domain map, rollout plan, runbook, rollback strategy, dependency graph | Critical paths work, permissions are enforced, observability exists, failure isolation works, rollback is rehearsed |

If a project crosses archetypes, use the stricter checklist for each relevant part. For example, a customer-facing support agent is both an agent and a product UI; it needs conversation evals, tool logs, UX fallbacks, analytics, and support handoff.

For large-scale multi-domain platforms, do not treat the whole system as one implementation plan. Decompose it into bounded surfaces and systems:

1. **User-facing surfaces** — buyer, seller, guest, host, admin, support, mobile app, web app, API.
2. **Core platform systems** — identity, payments, search, ranking, inventory, messaging, notifications, trust and safety.
3. **Operational workflows** — onboarding, moderation, dispute handling, support, fraud review, incident response.
4. **Data and intelligence** — analytics, recommendations, forecasting, experimentation, reporting.

The methodology still applies, but the planning artifact changes from "one feature plan" to a portfolio of linked plans with explicit boundaries, dependencies, and ownership.

### Planning levels for large work

Do not use one document to plan every level of work. Large initiatives need different artifacts at different levels:

| Level | Purpose | Typical artifact |
|-------|---------|------------------|
| **Portfolio** | Decide which initiatives deserve funding, sequence, and executive attention | Roadmap, investment thesis, quarterly plan |
| **Program / initiative** | Define the end-to-end outcome across teams or systems | Initiative brief, program plan, dependency map |
| **Workstream / domain** | Define one bounded slice owned by one team or domain | Domain plan, service plan, rollout plan |
| **Execution step** | Complete one reviewable unit of work safely | Step in `PLAN.md`, issue, PR, runbook task |

Rules:

1. **One owner per level.** Shared accountability usually means no accountability.
2. **One artifact per decision.** If the decision is architecture, write an ADR. If it is rollout, write a rollout plan. If it is execution, write a step.
3. **Escalate upward only when needed.** Do not send step-level questions to the portfolio layer.
4. **Decompose before execution.** If one plan has too many teams, systems, or milestones to reason about, split it.

For large-scale multi-domain platform work, the methodology should produce a stack of linked artifacts, not one giant master document.

### Minimal artifact templates

The methodology becomes easier to run at team scale when key artifacts share a stable shape.

Use these minimum fields:

| Artifact | Minimum fields |
|----------|----------------|
| **Initiative brief** | Objective, owner, users/stakeholders, scope, non-goals, success metrics, dependencies, major risks |
| **Workstream plan** | Owner, bounded scope, interfaces/contracts, dependencies, milestones, quality gates, rollout path |
| **ADR** | Decision, context, options considered, chosen approach, consequences, owner, date |
| **Execution step** | Current step, files/systems affected, success criteria, checks, required reviewers, rollback note |
| **Release note / rollout plan** | Change summary, environments, approvals, feature flags, rollback, observation checks |
| **Post-ship review** | What changed, expected outcome, actual outcome, incidents/findings, follow-up actions, owner |

Templates are not ceremony. They reduce drift, speed up review, and make AI-generated artifacts easier to evaluate.

### Lifecycle states

Every initiative, workstream, or execution step should have an explicit state. This prevents hidden work, half-approved work, and "almost done" work that nobody can classify.

Recommended states:

| State | Meaning |
|-------|---------|
| **Intake** | The work exists as an idea, request, bug, or obligation, but is not yet accepted |
| **Ready** | Definition of Ready is met and the work may start |
| **In planning** | Research, design, architecture, or dependency clarification is underway |
| **Ready for execution** | Plan, guardrails, acceptance target, and merge/deploy gates are in place |
| **In execution** | Implementation is actively happening |
| **In review** | Evidence exists and merge/deploy review is underway |
| **Released** | The change has shipped or been handed off |
| **Observed** | Post-ship monitoring, validation, and follow-up are active |
| **Closed** | Done, learned from, and no further action is expected |
| **Sunset / decommissioned** | The system or workflow has been intentionally retired |

The state model matters because different artifacts and approvals belong to different stages. Teams should not improvise that boundary in chat.

## GitHub Operating Model

GitHub setup is part of system design. Repository topology, ownership, review gates, deployment controls, and planning surfaces determine whether the project stays operable as the team and product grow.

Make these decisions before implementation starts:

1. **Organization model** — personal account, team org, or enterprise org.
2. **Repository topology** — single repo, monorepo, multi-repo, or mixed model.
3. **Ownership model** — who owns which paths, services, environments, and approvals.
4. **Review model** — what must pass before merge, who approves, and what can bypass.
5. **Deployment model** — what environments exist, who can deploy, and what must be reviewed.
6. **Planning model** — issues, labels, milestones, projects, roadmaps, and intake flow.
7. **Security model** — dependency updates, secret protection, code scanning, advisories, and audit trail.

### Repository topology

Choose repository shape based on coupling, release cadence, and access boundaries:

| Topology | Use when | Strength | Failure mode |
|----------|----------|----------|--------------|
| **Single repo** | One product or one deployable owned by one team or a tightly coupled small group | Simple setup, fast onboarding, one review surface | Becomes messy when multiple services or teams need different release and permission boundaries |
| **Monorepo** | Many packages or services change together, share tooling, and benefit from atomic cross-cutting changes | Shared standards, easier large refactors, one source of truth | Becomes slow and political without strong tooling, ownership, and path-based CI |
| **Multi-repo** | Services or products have independent owners, release cadence, compliance boundaries, or visibility rules | Clear isolation, separate permissions, cleaner service autonomy | Dependency drift, duplicated setup, fragmented standards, cross-repo change pain |
| **Mixed model** | A platform has a few tightly coupled repos plus many independent services or public packages | Balances shared standards with real autonomy | Confusion if boundaries are inconsistent or ownership is vague |

Professional rule:

- Use a **monorepo** only if you are prepared to invest in build tooling, test selection, ownership boundaries, and consistent standards.
- Use **multi-repo** when independent release and permission boundaries are more important than cross-repo refactoring speed.
- For large-scale multi-domain platforms on GitHub, default to **an organization with domain-owned repositories or bounded monorepos**, not one giant repo by default.

### GitHub structure by product type

| What you are building | Recommended GitHub structure |
|-----------------------|------------------------------|
| **Website or single app** | One repo, one delivery pipeline, one `CODEOWNERS`, one project board, staged environments |
| **Product with web, mobile, backend, and shared packages** | Monorepo if releases and standards are tightly coupled; otherwise separate repos plus shared templates and reusable workflows |
| **Agent or automation** | Separate repo when secrets, tools, or runtime policy differ from the host product; keep evals, prompts, policies, and runbooks versioned with the agent |
| **Marketplace or platform** | Organization-level structure with domain repos for identity, payments, search, trust/safety, support tooling, and product surfaces |
| **Internal and external tools on one platform** | Separate repos when access, customer impact, or release cadence differ; shared org defaults and reusable workflows |
| **Open source product** | Public repo with stronger community health files, issue forms, security policy, release notes, and clearer contributor workflow |

### Organization baseline

At team scale, do not manage GitHub as a pile of ad hoc repositories. Set an org-level baseline:

1. **Teams reflect ownership.** Create teams by durable domain or responsibility, not temporary projects.
2. **Use nested teams carefully.** Parent teams should only have permissions safe for every child team.
3. **Centralize defaults in `.github`.** Put default `CONTRIBUTING.md`, `SECURITY.md`, issue templates, PR templates, and other community health files in a public `.github` repo.
4. **Use template repositories.** Create starter repos for your common stacks so new projects inherit structure, workflows, and docs on day one.
5. **Standardize project intake.** Use consistent issue forms, labels, issue types, and project fields across related repos.
6. **Separate admin from daily write access.** Keep repository admin rights narrow; use teams and code ownership for normal work.

### Repository baseline

Every serious repo should start with a predictable control surface:

| Area | Baseline |
|------|----------|
| **Docs** | `README.md`, `CONTRIBUTING.md`, `SECURITY.md`, architecture or runbook notes where appropriate |
| **Ownership** | `CODEOWNERS` in `.github/`, with ownership for critical paths and for the `CODEOWNERS` file itself |
| **Templates** | Issue forms in `.github/ISSUE_TEMPLATE/`, PR template in `.github/` or root |
| **Automation** | CI workflows, reusable actions or reusable workflows, dependency update config, release workflow |
| **Planning** | Label taxonomy, milestones if release-based, project integration for roadmap and status |
| **Security** | Dependabot, secret scanning, push protection, code scanning where available, advisory process |
| **Deployments** | Named environments such as `dev`, `staging`, `prod` with explicit protection rules and secrets |

Recommended `.github/` skeleton:

```text
.github/
  CODEOWNERS
  pull_request_template.md
  dependabot.yml
  ISSUE_TEMPLATE/
    bug.yml
    feature.yml
    task.yml
    config.yml
  workflows/
    ci.yml
    release.yml
    deploy.yml
```

### Architecture and standards model

Professional teams do not rely on reviewer memory to preserve architecture. They define standards as versioned artifacts and enforce them with ownership and automation.

Set up:

1. **Architecture decision records** for meaningful structural choices such as repo topology, service boundaries, data ownership, integration style, and deployment model.
2. **Definition of Ready** for work intake. Code should not start until the task has scope, owner, acceptance criteria, dependencies, and risk classification.
3. **Definition of Done** for merge and release. A change is not done because code exists; it is done when quality gates, docs, and deployment evidence pass.
4. **Contract-first boundaries** where they matter: API schemas, event contracts, data contracts, interface definitions, and policy files.
5. **Path-based standards** for high-risk directories such as auth, billing, infra, migrations, prompts, workflows, and security-sensitive code.
6. **Versioned engineering standards** in the repo: naming, testing expectations, dependency policy, logging, observability, and rollback expectations.

Recommended standards surface:

```text
docs/
  architecture/
    adr/
  standards/
    testing.md
    api-contracts.md
    observability.md
    dependency-policy.md
```

### Merge admission model

The team should be able to answer one simple question before merge: why is this change allowed to exist?

At minimum, require:

1. **A linked work item** — issue, task, bug, incident, or approved initiative.
2. **A defined spec or acceptance target** — acceptance criteria, contract update, design artifact, or ADR when the change is structural.
3. **Evidence of validation** — tests, screenshots, logs, reports, or deployment proof appropriate to the change type.
4. **Ownership approval** — code owner or delegated owner for affected paths.
5. **No unresolved architectural drift** — if the change conflicts with stated boundaries or standards, either reject it or update the architecture artifact deliberately.

If a team cannot explain what artifact authorized the change, review it, and proved it, the process is not professional yet.

### Quality gates by change type

Not every change needs the same checks, but every change needs the right checks.

| Change type | Minimum gate before merge |
|-------------|---------------------------|
| **UI or product feature** | Tests, screenshots or behavioural proof, accessibility check where relevant, owner review |
| **API or integration** | Contract validation, compatibility check, failure-path coverage, owner review |
| **Data or migration** | Migration plan, rollback path, fixture or staging proof, owner review, deploy control |
| **Infra or deployment** | Environment validation, rollback path, security review where needed, deploy approval |
| **Agent or automation** | Eval or scenario coverage, bounded permissions, logs/artifacts, stop conditions, owner review |
| **Security-sensitive paths** | Explicit reviewer set, code scanning or policy checks, documented risk review |

The rule is not "more checks everywhere." The rule is "the right gate for the actual risk."

### Merge and review controls

Use GitHub rulesets or branch protections as policy, not as documentation.

Baseline for any shared production repo:

1. **Require pull requests before merge.**
2. **Require passing status checks.**
3. **Require code owner review on owned paths.**
4. **Block force pushes and deletions on protected branches.**
5. **Use linear history when revertability matters.**
6. **Restrict bypass to explicit roles, teams, or apps.**
7. **Expose rules visibly.** People should be able to see which rules apply without needing admin access.
8. **Map status checks to standards.** Every required check should correspond to a written standard, contract, or release rule.

For higher-risk repos, add:

1. **Required deployments before merge** for critical paths that must prove staging readiness.
2. **Required code scanning results** for languages and surfaces where static analysis is meaningful.
3. **Required signed commits** if your compliance or provenance model needs it.
4. **Path restrictions** for generated files, release artifacts, or sensitive directories.
5. **Required architectural approval** when a change touches protected domains, core contracts, or foundational workflow logic.

### Deployment and environment model

GitHub environments are part of release governance, not just secret storage.

Set up:

1. **Named environments** with clear purpose: `dev`, `staging`, `prod`, or equivalent.
2. **Environment-specific secrets** rather than one giant repository secret pool.
3. **Required reviewers** for sensitive deployments.
4. **Branch policies** so only approved branches can target sensitive environments.
5. **Concurrency and deployment history** so overlapping deploys and rollbacks are visible.
6. **Custom protection rules** when third-party approval or change-management systems must gate deployment.

### Actions and automation model

Treat GitHub Actions as a delivery platform, not a pile of repository-local scripts.

At team scale:

1. **Prefer reusable workflows** for common CI, release, security, and deploy paths.
2. **Separate workflow logic from app logic.** The repo should consume workflows cleanly, not bury delivery policy inside ad hoc YAML.
3. **Version shared automation deliberately.** Breaking workflow changes should roll out like product changes.
4. **Keep default permissions narrow.** Automation should start read-only or least-privileged, then expand only where justified.
5. **Make automation outputs reviewable.** Releases, deployments, triage changes, and bot updates should leave artifacts humans can inspect.
6. **Use Actions to enforce standards consistently** across repos, instead of relying on maintainers to remember the same setup manually.

### Planning and coordination model

GitHub is also the work-management layer for many teams. Use it deliberately:

1. **Issue forms** for intake. Different forms for bugs, feature requests, incidents, and internal tasks.
2. **Label taxonomy** that reflects type, domain, priority, and state. Keep it small and stable.
3. **Projects** for team backlog, roadmap, and release tracking. Use custom fields for priority, risk, target date, and domain.
4. **Milestones** when you ship in named releases or batches.
5. **Issues-only or planning repos** when planning access needs to differ from source-code access.

If you cannot tell from GitHub who owns work, what is blocked, what is ready, and what is shipping next, your setup is not team-grade yet.

### Security and maintenance baseline

Security defaults should be enabled before the repo becomes busy:

1. **Dependabot alerts, security updates, and version updates** for dependencies.
2. **Secret scanning** to detect exposed credentials already in history and across collaboration surfaces.
3. **Push protection** to block secrets before they land in the repository.
4. **Security policy and advisory path** so reports do not arrive through random channels.
5. **Documented dismissal and triage rules** so security noise does not accumulate without explanation.

### Monorepo realism

Do not copy Google superficially. The useful lesson from Google's monorepo practice is that monorepos scale with strong source-control policy and tooling, not because one repo is inherently elegant.

Use a monorepo only if all of the following are true:

1. Cross-cutting changes are common and valuable.
2. Shared tooling and standards are non-negotiable.
3. Ownership can be expressed clearly with paths and teams.
4. CI can test selectively and stay fast enough for daily work.
5. The organization is willing to invest in tooling, not just folder structure.

If those conditions are weak, prefer multiple repos with strong templates, shared workflows, and org-level defaults.

### GitHub setup checklist for Phase 0 / 2.5

Before implementation starts, record:

1. **Repo topology choice** and why it fits the product.
2. **Organization and team ownership model**.
3. **Repository template or starter structure**.
4. **Rulesets / branch protection policy**.
5. **CODEOWNERS coverage**.
6. **Issue / PR template design**.
7. **Project, labels, milestone, and roadmap setup**.
8. **CI, environments, deployment approvals, and release flow**.
9. **Dependabot, secret scanning, push protection, and code scanning choices**.
10. **Admin, bypass, and emergency-change process**.

## Phase 0 — Triage and Workflow Selection

**Who writes:** You. The AI can advise, but you decide.

Before writing a full plan, classify the task:

| Task type | Workflow |
|-----------|----------|
| Small, low-risk, isolated change | Use the Lightweight Workflow |
| Cross-file feature, unclear bug, production code, client work | Use the full methodology |
| Auth, billing, permissions, migrations, legal/compliance, external systems | Full methodology plus explicit guardrails and review escalation |
| Knowledge fragmentation is slowing delivery, onboarding, support, or internal AI | Use the full methodology and evaluate the company-brain path |
| Novel architecture or off-distribution work | Hand-code the core; use AI for research, review, tests, and boilerplate |

Write down:

1. **Risk level** — low, medium, high, or critical.
2. **Workflow choice** — lightweight or full.
3. **Why this workflow is enough** — one sentence.
4. **Human review boundary** — what the AI may do alone vs. what must be reviewed manually.
5. **Environment assumption** — local, cloud VM, remote control, CI, or production-adjacent.
6. **GitHub operating model** — repo topology, ownership, review gates, and deployment path.
7. **Architecture guardrails** — applicable ADRs, contracts, standards, and merge gates for this task.
8. **Methodology maturity target** — individual, team, multi-team, or organization-wide baseline expected for this work.

If knowledge is a bottleneck, ask explicitly:

1. Are important answers spread across several systems?
2. Do people repeatedly ask the same policy, product, or operational questions?
3. Do onboarding, support, or engineering workflows lose time because knowledge is hard to retrieve?
4. Do copilots, automations, or agents need grounded internal context?
5. Are source ownership and permissions mature enough to support retrieval safely?

If the answer is "yes" to the first four and at least "mostly yes" to the fifth, the methodology should recommend the company-brain path.

If the task grows during execution, promote it to the full methodology. Do not let a "quick fix" quietly become a migration, architecture change, or production agent.

---

## Lightweight Workflow

Not every task needs the full methodology. For small, low-risk changes, compress the same principles into a single session:

1. **Explore** — inspect relevant files, docs, data, process notes, tests, and git state without editing.
2. **Plan** — write a short plan with artifacts to touch, expected behaviour, risks, and verification commands.
3. **Code or create** — implement only the approved plan.
4. **Verify** — run the agreed checks, inspect the diff or output, and compare against success criteria.
5. **Commit or hand off** — checkpoint only after verification, with a message that states the user-facing change and test evidence.

Use this workflow for isolated bug fixes, docs updates, small UI adjustments, test additions, narrow refactors, small automations, and low-risk content or configuration changes.

Do not use it for migrations, auth, billing, permissions, production agents, cross-service changes, unclear requirements, irreversible operations, customer-facing automation, or anything with external dependencies. Those go through the full methodology because the planning cost is cheaper than recovering from a wrong implementation.

The invariant is the same: **exploration and planning happen before execution.**

---

## Phase 1 — Human-Written Foundation

**Who writes:** You. No AI.

Write a text document with:

1. **Title** — what you're building or changing
2. **Objective** — 2-3 lines on what you actually want to achieve and why
3. **Primary user or stakeholder** — who benefits, approves, operates, or is affected
4. **Planning level** — portfolio, initiative, workstream, or execution step
5. **Deliverable type** — website, app feature, internal tool, external product, agent, automation, report, integration, migration, platform capability, research artifact, or other
6. **Owner** — the human responsible for final decisions at this level
7. **Definition of Done draft** — what must be visibly true when the work is complete
8. **Non-goals** — what is explicitly out of scope
9. **Constraints** — deadline, budget, tech stack, permissions, data access, brand rules, compliance, backwards compatibility
10. **Key bullet points** — 5-10 high-level things that need to happen, straight from your head
11. **Initial risk level** — low, medium, high, or critical
12. **Acceptance artifact** — issue, spec, contract, design, ADR, or runbook that authorizes the work

This is your thinking, unfiltered. You need to own the vision before anything else touches it.

### Why non-goals matter

The most common planning failure is scope creep during execution. If you don't explicitly state what you're *not* building, you (or the AI) will naturally expand the scope. "Out of scope: mobile responsiveness, auth, analytics" costs 30 seconds to write and saves hours of drift. LLMs are especially prone to adding features you didn't ask for — non-goals give you a document to point at when they try.

### Optional: the interview pattern

If you're unsure what you don't know, ask the AI to interview you before writing Phase 1:

> "I want to build [brief description]. Interview me about it. Ask about technical implementation, edge cases, tradeoffs, and things I might not have considered. Don't ask obvious questions — dig into the hard parts."

Use the answers to write a better Phase 1. Then **start a fresh context** for Phase 2.

---

## Phase 2 — Research Document

**Who writes:** The AI, in a dedicated context.

Tell the AI to read all relevant parts of the project and produce a comprehensive research document alongside your plan.

- Be explicit: "Be super thorough. Don't leave anything out."
- This document can be long — 2,000-5,000 lines is normal for complex projects
- It should cover: existing architecture, relevant files, API contracts, data models, workflows, dependencies, constraints, users, failure modes, and source-of-truth documents
- **Include external dependencies** — API keys needed, access to grant, third-party services to test, other people's work that must land first
- **Include controlling artifacts** — ADRs, standards, contracts, policy files, quality gates, and protected paths that constrain implementation

This research doc is the AI's "memory" for the rest of the process. Instead of re-reading the codebase every time, you point it here.

Research scope depends on the project:

| If the project involves... | Research must include... |
|----------------------------|--------------------------|
| Code or product UI | Repo structure, patterns, design system, routes, state, tests, deployment path |
| Agent behaviour | Tasks, allowed tools, prohibited actions, human handoff, logs, eval examples, safety boundaries |
| Automation | Current manual process, triggers, inputs, owners, exceptions, retry rules, audit requirements |
| Data/reporting | Source systems, schemas, sample data, freshness, reconciliation rules, downstream consumers |
| Knowledge / company brain | Source inventory, source owners, trust tiers, freshness policies, permission model, retrieval options, answer policy, evaluation plan |
| Business process | Stakeholders, approvals, legal/compliance limits, customer impact, operational support path |
| External integrations | Auth, rate limits, API docs, sandbox/prod differences, failure responses, revocation path |

### Use subagents for research

If your tool supports it (Claude Code does), delegate research to subagents. They explore in a separate context and report back a summary, keeping your main context clean for the actual planning work. Codebase exploration is the single biggest token consumer — don't let it pollute your working context.

Subagents aren't just for Phase 2. Use them any time a task would take 3+ tool calls to research or execute:

| Use case | How |
|----------|-----|
| Codebase exploration | Spawn an Explore subagent |
| Independent code review | Fresh context agent reads the diff with no authorship bias |
| Parallel implementation steps | Two non-dependent steps run simultaneously |
| QA / test execution | Separate agent runs tests and reports back |

### Parallel agent hygiene

Running multiple agents is a coordination problem, not a productivity guarantee. Use parallel agents only when the work can be split cleanly.

Before launching more than one agent:

1. **Name every agent by outcome.** "Auth migration reviewer" is better than "Agent 2."
2. **Give each agent a disjoint scope.** Separate files, modules, questions, or verification targets.
3. **Isolate write work.** Prefer separate branches, worktrees, or clearly owned file sets so agents cannot overwrite each other.
4. **Define the merge point.** Decide who integrates findings, resolves conflicts, and performs final review.
5. **Track status centrally.** Keep a short table of agent, scope, status, blocker, and output link.
6. **Do not parallelize uncertain architecture.** If the design is unsettled, resolve the decision first. Parallel agents amplify ambiguity.

Useful parallel work: independent research, independent code review, test/QA runs, competing prototypes, or implementation steps with no shared files. Bad parallel work: several agents editing the same feature without ownership boundaries.

### CLAUDE.md — Persistent Context Across Sessions

The research document is the AI's memory for the project — but only if it's available at the start of every session. Wire it in permanently with `CLAUDE.md`:

```
## Research
See RESEARCH.md — read this before doing anything.

## Plan
See PLAN.md — current implementation state is at the top.
```

Claude Code automatically reads `CLAUDE.md` at the start of every session in that directory. You never have to manually re-provide context — the AI starts each session already oriented. This is one of the highest-leverage things you can do to improve first-pass quality.

### CLAUDE.md is context, not enforcement

`CLAUDE.md` improves adherence, but it is still context the model tries to follow. It is not a policy engine.

Keep it:

1. **Short** — every line loads into context; remove stale prose.
2. **Specific** — "Use pnpm for package commands" beats "follow project conventions."
3. **Scoped** — broad rules in root `CLAUDE.md`, path-specific rules in `.claude/rules/`, personal preferences in local/user files.
4. **Verifiable** — if a rule matters, pair it with tests, lint, hooks, CI, or review checklist items.
5. **Auditable** — use `/memory` or the tool's equivalent to inspect which instruction files loaded.

For long reading or research tasks, require proof of attention:

1. After every few file reads, ask the AI to write one concrete observation it learned.
2. If it skips content, require it to say what it skipped and why.
3. If a rule is critical, repeat it in the prompt packet near the end.

Silent skipping is not acceptable for high-risk work. If the AI cannot prove it read the relevant material, do not let it implement.

### Version control from here

Initialize git tracking on your plan document now. Every subsequent edit shows up as a diff, which is far faster to review than re-reading the whole thing.

---

## Phase 2.5 — Harness Setup and Guardrails

**Who writes:** You configure; the AI can draft.

Before refining or executing the plan, set up the environment that will keep the agent inside the right boundaries.

Add or verify:

1. **Persistent context** — `CLAUDE.md`, `.claude/rules/`, `RESEARCH.md`, `PLAN.md`, and current-state block.
2. **Permissions** — whether the agent can edit files, run commands, use the network, access MCP servers, or operate in auto-accept mode.
3. **Hooks and CI gates** — fast blocking hooks for hard rules; slower checks at review or CI boundaries.
4. **MCP/tool access** — only the external systems required for the task, preferably read-only first.
5. **Secrets and data boundaries** — files or systems the agent must not read or mutate.
6. **Rollback path** — git branch, worktree, backup, migration rollback, feature flag, or kill switch.
7. **Observation path** — logs, traces, screenshots, PR links, or artifacts that prove what happened.
8. **GitHub controls** — rulesets, `CODEOWNERS`, issue/PR templates, environments, deployment reviewers, and security features match the risk level.
9. **Architecture enforcement** — required checks, protected paths, ADR review triggers, contract tests, and policy checks are wired into the repo.
10. **Exception path** — who may approve temporary bypasses, how they are recorded, and when they expire.

The rule: instructions guide behaviour; harness controls behaviour. If failure would be expensive, use the harness.

---

## Phase 3 — Iterative Refinement

**Who writes:** Both. The AI identifies issues, you make decisions.

Do 3-4 rounds of:

1. Tell the AI: "Read the research document and the plan. Find contradictions, missing decisions, ambiguities, and things I haven't thought about."
2. The AI writes its findings **at the bottom of the file** — not inline edits
3. You write your responses directly in the document under each item
4. Pick **one issue** and discuss it. Resolve it fully before moving to the next.

### Rules

- **One issue at a time.** LLMs get confused when handling multiple discussions simultaneously. One topic per round keeps them focused and accurate.
- **You do the writing.** The AI proposes, you decide. Add your responses in bullet point format directly in the document.
- **Surface blockers early.** If the AI identifies an external dependency (API access, credentials, someone else's work), flag it now so it can be unblocked in parallel with planning.

### What to look for in each round

- **Round 1-2:** Structural gaps — missing components, incorrect assumptions, architectural issues
- **Round 3-4:** Finer issues — edge cases, error handling, naming, ordering constraints
- **Diminishing returns signal:** When the AI's findings are mostly cosmetic or hypothetical, you're done. Stop.

### Ask for approaches, not code

During refinement, when a technical decision comes up, don't ask for code. Ask for options:

> "Give me 2-3 approaches for this, with pros and cons for each."

As Karpathy notes: *"There's almost always a few ways to do things and the LLM's judgement is not always great."* You pick the approach. The AI presents the tradeoffs.

### Use extended thinking for hard problems

When you're stuck on a genuinely complex decision — architectural choices, dependency ordering, subtle tradeoffs — tell the AI to think carefully before responding. Claude 4.7's adaptive thinking will automatically allocate more reasoning tokens to hard problems. Phase 3 and Phase 5 are where this earns its cost most.

### The LLM council

When stuck on a critical decision, ask multiple models the same question. Different models have different blind spots. Karpathy: *"I often pay for several models and ask them the same question, treating them as my personal 'LLM council.'"*

### Abort criteria

Define upfront: "If during implementation we discover X, we stop and re-plan." This turns anxiety about fatal flaws into a concrete decision rule. Examples:
- "If the API doesn't support batch operations, re-plan around individual calls"
- "If the migration takes more than 30 seconds on prod data, different strategy"

---

## Phase 4 — Rewrite for Clarity

**Who writes:** The AI, then you review.

Once the content is solid:

1. Tell the AI: "Rewrite this plan for clarity. Remove as many words as possible without losing any accuracy."
2. The rewrite will naturally de-duplicate — your iterative edits will have introduced repetition
3. **Always read the rewrite.** LLMs will mess things up — subtle meaning changes, dropped details, softened constraints. They especially like to remove or alter comments they don't fully understand.
4. Use `git diff` to see exactly what changed
5. Fix anything wrong

### Add the Definition of Done

Before leaving this phase, add a "Definition of Done" section near the objective:
- What does the user see when this is complete?
- What behaviour, workflow, report, interface, or operational outcome works?
- What artifact proves it works: endpoint response, page, screenshot, report sample, log, eval result, PR, deployment, or handoff doc?
- What is the deploy, rollout, or delivery state?
- How do you know it's **shipped**, not just "code complete"?

Karpathy's framing: *"Demo is works.any(), product is works.all()"* — getting a demo working is trivial. Your Definition of Done should describe the product, not the demo.

### Add the Definition of Ready

Before leaving planning, add a short "Definition of Ready" section too:

- What approved artifact authorizes the change?
- Which contracts, standards, or ADRs constrain implementation?
- Which owners must review it?
- Which quality gates must pass before merge?
- What evidence must exist before deployment or handoff?

This is how teams stop low-spec work from quietly turning into merged code.

---

## Phase 4.5 (Optional) — Artifact and Experience Design

**Who writes:** The AI drafts, guided by you.

If the project has a user-facing experience, operational workflow, agent behaviour, data output, or approval path, design that artifact before writing the implementation plan. Designing after implementation starts locks you into accidental constraints. Designing before means Phase 5 can describe exactly what to build.

**When to use this phase:**
- The project involves any user-facing interface
- The project involves an agent, automation, report, dashboard, operational process, or customer handoff
- Stakeholders need to approve a layout before development starts
- The interaction model, process flow, output format, or visual hierarchy is undecided

**When to skip it:**
- The output is trivial or already defined by an existing standard
- The work is purely internal refactoring with no behaviour, workflow, or interface change

### How to run it

Produce the smallest artifact that removes ambiguity:

| Project type | Design artifact |
|--------------|-----------------|
| Website or app | Sitemap, wireframe, rendered mockup, responsive states, empty/error/loading states |
| Tool or product surface | Workflow map, role-based screens, API map, approval path, service touchpoints |
| Agent or chatbot | Conversation examples, tool-call contract, escalation tree, refusal/fallback examples |
| Process automation | Process map, trigger/input rules, approval points, retry and stop conditions |
| Data/reporting | Target table/schema, report mockup, reconciliation examples, freshness rules |
| Knowledge / company brain | Source taxonomy, trust model, permission map, retrieval architecture, citation policy, evaluation plan |
| Marketplace or platform ecosystem | Actor journeys, service blueprint, trust/safety flows, support and dispute flows |
| Complex system or enterprise platform | Architecture sketch, domain map, dependency graph, operator runbook, rollout sequence |

For UI work in Claude Code, `/frontend-design` can generate rendered HTML/CSS mockups you can open in a browser. Treat the output like lightweight Figma: useful as a visual spec, not automatically production code.

Reference the approved artifact in Phase 5 step descriptions: "Build the dashboard matching visual-spec.png", "Implement tool calls matching agent-contract.md", or "Create the automation flow in process-map.md."

---

## Phase 5 — Implementation Plan

**Who writes:** The AI drafts, you review and edit.

Only start this after the project plan is locked down. This is a separate section — the explicit ordering of work.

1. Tell the AI: "Think really hard. Re-read the research document. Create an implementation plan with the explicit order in which these things need to happen."
2. Structure as **5-10 numbered steps**, each with:
   - What to do (sub-steps if needed)
   - **Success criteria** — not "what to do" but "what must be true when done" (declarative, not imperative)
   - Which verifications the AI can do itself (tests pass, lint clean) vs. which are manual (check the database, load the URL, confirm the numbers)

Each step should produce or change one reviewable artifact: code diff, config change, migration, prompt, runbook, test fixture, report sample, screenshot, workflow rule, or deployment artifact. If a step cannot be reviewed, split it.

For structural work, require the plan to name the controlling artifact explicitly: ADR, contract, migration spec, API schema, environment rule, or policy file.

### Declarative over imperative

Frame verification as success criteria, not instructions. Instead of "add validation," write "invalid inputs return a 400 with a descriptive error message." Instead of "fix the bug," write "the test that reproduces issue #42 passes." This gives the AI a clear target and lets you objectively verify completion.

### Archetype add-ons

Add the relevant checklist to the implementation plan:

| Archetype | Add to the plan |
|-----------|-----------------|
| **Website or app** | Routing, state, content, responsive behaviour, loading/error/empty states, accessibility, SEO, analytics, browser/device checks |
| **Tool or product surface** | User roles, permissions, workflow states, service/API contracts, operational ownership, rollout and support path |
| **Agent or chatbot** | Boundary, tool schema, prompt/policy files, memory/state, eval set, logs, fallback/handoff, abuse cases, cost/latency budget |
| **Process automation** | Trigger, input queue, eligibility rules, idempotency, retries, stop conditions, notifications, audit log, manual override |
| **Data/reporting** | Source extraction, transformations, schema checks, freshness checks, reconciliation, sample outputs, ownership, backfill strategy |
| **Knowledge / company brain** | Source onboarding, metadata and chunking model, trust tiers, permission enforcement, freshness policy, citation behavior, retrieval/reranking strategy, evals, operating ownership |
| **Marketplace or platform ecosystem** | Actor-specific workflows, supply/demand rules, ranking/search assumptions, payments, trust/safety, support tooling, fraud/abuse paths, regional policy differences |
| **Complex system or enterprise platform** | Architecture, domain boundaries, permissions, migrations, feature flags, observability, support runbook, dependency management, rollback, staged rollout |

This keeps the core methodology general while making the actual implementation plan specific enough to execute.

### Agent production checklist

If the project includes an autonomous or semi-autonomous agent, the implementation plan needs more than feature steps. Agents are production software with tools, state, runtime behaviour, and operational failure modes.

Add explicit decisions for:

1. **Agent boundary** — what the agent owns, what remains deterministic application code, and when it must hand off to a human.
2. **Tool contract** — which tools the agent may call, their input/output schemas, failure modes, permissions, and rate limits.
3. **Session state** — what conversation or task state is stored, where it lives, how long it persists, and how it is reset.
4. **Orchestration** — if multiple agents exist, define each agent's capabilities and the routing rule. Do not create multi-agent systems just because the framework makes it easy.
5. **Observability** — logs, traces, tool-call records, latency, cost, error rates, and user-visible failure paths.
6. **Evaluation** — representative tasks, expected outputs, regression cases, and how production traces feed back into tests.
7. **Deployment model** — local script, app server, managed agent runtime, scheduled job, or queue worker. Include rollback and kill-switch behaviour.

This is the difference between a demo agent and a production agent. A demo only needs to answer once. A production agent needs to be inspected, debugged, constrained, evaluated, and shut down safely.

### Proactive workflow checklist

If an agent runs without a human actively prompting it — scheduled jobs, backlog sweeps, nightly PRs, monitoring loops — add extra constraints. Proactive does not mean unsupervised.

Define:

1. **Trigger** — schedule, webhook, queue event, or manual approval. Avoid vague "always watch everything" loops.
2. **Input queue** — the exact source of work: approved issues, labeled tickets, failing tests, security alerts, or a curated backlog.
3. **Eligibility rules** — what the agent may pick up automatically and what must stay human-led.
4. **Change budget** — max files, max diff size, allowed directories, time limit, token/cost limit, and number of retries.
5. **Review artifact** — usually a PR, draft PR, report, or patch file. Never let background work disappear into chat history.
6. **Stop conditions** — failing tests, missing context, unclear requirements, touched sensitive files, or repeated correction loops.
7. **Notification path** — who gets pinged, what summary they receive, and what decision they need to make.

The safe pattern is: **approved input → bounded execution → verifiable artifact → human review.** If any of those four pieces are missing, the workflow is not ready to run in the background.

### Review with inline notes

Go through the implementation plan line by line. Mark issues with a personal tag:

```
note AB - actually this has to happen before step 3 because of the foreign key
note AB - this is wrong, the API uses POST not GET
note AB - fine, ignore this
```

Then tell the AI: "Find all `note AB` entries and address them one by one."

### Session handoff block

Add a "Current State" block at the very top of the plan:

```
## Current State
- Steps 1-3: complete
- Step 4: in progress — migration written, not yet run
- Blocker: waiting on API key from Alex
- Next: finish step 4, then step 5
```

Update this after each session. It means anyone (you, the AI, a teammate) can pick up without re-reading everything.

### Build the prompt packet

Before Phase 6, turn the plan into a reusable prompt packet. A good execution prompt is not a clever one-liner. It is a structured brief the AI can follow repeatedly.

Use this shape:

1. **Role and task** — 1-2 sentences: what the AI is doing and what success means.
2. **Context** — links to `RESEARCH.md`, `PLAN.md`, relevant files, API docs, screenshots, or retrieved data.
3. **Current step** — the exact step to complete, copied from the implementation plan.
4. **Constraints** — non-goals, files not to touch, compatibility requirements, style rules, and known traps.
5. **Examples** — existing code patterns, expected input/output, UI screenshots, API payloads, or tests that define the target.
6. **Output format** — what the AI should return: changed files, verification results, open risks, and anything requiring human review.
7. **Critical reminder** — repeat the one thing that must not be missed.

Example:

```
You are implementing Step 3 of PLAN.md. Complete only this step.

Context:
- Read RESEARCH.md first.
- Relevant files: src/routes/import.ts, src/lib/parser.ts, tests/import.test.ts.
- Match the error-handling style already used in src/routes/export.ts.

Constraints:
- Do not change the database schema.
- Do not refactor unrelated parser code.
- If the CSV library cannot represent a malformed row, stop and report that limitation.

Success criteria:
- Invalid rows return a 400 with row number and field name.
- Existing valid import tests still pass.
- New malformed-row tests cover missing required fields and invalid dates.

Return:
- Files changed
- Verification commands run
- Any residual risks

Critical reminder: this step is validation only, not import redesign.
```

This pattern comes from prompt engineering more than software planning: task description, context, detailed instructions, examples, repeated critical information, and an explicit output format. It reduces ambiguity and gives you a stable artifact to improve when the AI fails.

---

## Phase 5.5 — Readiness Gate

**Who writes:** You approve; the AI can prepare evidence.

No implementation starts until this gate passes.

Confirm:

1. **Plan is locked** — open decisions are either resolved or explicitly deferred.
2. **Current state is accurate** — completed work, in-progress step, blockers, and next action are written at the top of the plan.
3. **Prompt packet is ready** — role, context, current step, constraints, examples, output format, and critical reminder are present.
4. **Environment is correct** — local/cloud/CI assumptions match the task, dependencies are installed, and required services are reachable.
5. **Guardrails are active** — hooks, permissions, MCP scopes, CI checks, and protected files are configured.
6. **GitHub governance is active** — rulesets, ownership, templates, environments, and deployment approvals are in place for the target repo.
7. **Verification is concrete** — commands, manual checks, screenshots, endpoints, fixtures, or review artifacts are named.
8. **Rollback exists** — branch, checkpoint, backup, migration rollback, feature flag, or explicit abort criterion.
9. **Merge admission is defined** — linked work item, acceptance artifact, required owners, and required evidence are all clear.
10. **Adoption bundle exists** — the repo template, planning pack, guardrails, and AI guidance needed for this work are available or explicitly waived.

If any item is vague, stop and improve the plan. Readiness gates are cheaper than debugging an agent that started from bad assumptions.

---

## Phase 6 — Execution

**Who writes:** The AI executes, you review.

### Setup
1. **Clear the context** — start a fresh conversation or compact. This is critical.
2. Have the AI re-read the plan fresh
3. Paste the prompt packet for the current step
4. Confirm it understands the current state and what's next

### Per-step process

For each step:

1. **Instruct:** Paste the prompt packet. The minimum form is: "Complete step N of this plan. Just step N, complete it to its entirety. Keep going until it meets the success criteria."
2. **Wait:** Let the AI run to completion — this can take 20-30 minutes per step. Don't interrupt.
3. **Review:** Read every line of code that changed. Use `git diff`. Expect bloated code, excessive try/catch, redundant logic, poor aesthetics. This is normal — LLMs overcomplicate. Clean it up or ask the AI to simplify.
4. **Verify:** Run the success criteria — see the verification hierarchy below.
5. **Commit:** `git commit` after verified. This is your checkpoint.
6. **Update:** Update the "Current State" block in the plan.
7. **Next:** Move to step N+1.

### Prompt iteration loop

Prompting is empirical. If the output is wrong, don't only patch the code — patch the prompt packet so the next run has the missing context.

Use this loop:

1. **Observe the failure:** What did the AI misunderstand — task, context, constraints, examples, or output format?
2. **Add the smallest missing instruction:** One concrete constraint beats a paragraph of anxiety.
3. **Add an example when words are ambiguous:** Point to existing code, a test case, a payload, or a screenshot.
4. **Repeat critical information near the end:** Models can miss constraints buried in the middle.
5. **Retry in a fresh context if needed:** Especially after two failed corrections.

Do not treat "think step by step" as a magic spell. Ask for reasoning when the task genuinely requires tradeoff analysis, dependency ordering, or ambiguity resolution. For routine edits, clear context and precise success criteria matter more.

### Verification hierarchy

Not all verification is equal. Apply in order before marking any step complete:

1. **Automated** — tests pass, lint clean, types check. The AI handles this.
2. **Logical** — does the output match the success criteria exactly? Read the diff; don't just run it.
3. **Behavioural** — load the URL, call the endpoint, open the file. Confirm actual behaviour, not just code structure.
4. **Semantic** — step back: does this step move the project toward the Definition of Done, or does it solve the wrong problem well?

If step 3 or 4 fails, do not move on. Silent failures — code that runs but produces wrong results — are the most expensive bugs to find later.

### Confidence thresholds

When the AI hedges ("this might work", "I think", "probably"), treat it as a signal. Ask: "How confident are you? What could go wrong?" If the AI's own confidence is low, stop and re-examine the approach before committing. Don't let optimism carry you past a weak foundation.

### When things go wrong

- **Small plan adjustments:** Normal. Update the plan document and continue.
- **Step fails verification:** Debug in the same context. Don't move on until it's clean.
- **Two failed corrections on the same issue:** Clear context and start fresh with a better prompt incorporating what you learned. A clean session with a better prompt almost always outperforms a long session with accumulated corrections.
- **Hit an abort criterion:** Stop. Go back to Phase 3. Re-plan from the point of failure. Don't patch a fundamentally broken approach.
- **Context getting large (>200k tokens):** Clear context, re-read the plan, continue from current state. Quality degrades noticeably past 250k. Ideally stay under 100k.
- **AI "remembers wrong":** If the AI keeps suggesting standard approaches when you're doing something intentionally non-standard, it's pulling from training data, not your plan. Be more explicit, or hand-code that part.

### Independent review (optional but high-value)

After completing all steps, open a fresh context and have the AI review the full diff against the plan. A fresh session has no bias toward the code — it didn't write it. This catches things the implementation session overlooked.

### Review escalation ladder

Use deeper review only when the risk justifies the cost and time.

1. **Local quick review** — while iterating: ask the current session to review the diff against the step's success criteria.
2. **Fresh-context review** — before committing a completed step: start a clean session and ask it to review the diff with no authorship bias.
3. **Parallel/deep review** — before merging substantial or sensitive changes: use a dedicated review tool or multiple independent agents that verify findings, not just suggest style changes.
4. **Human final review** — always required for security-sensitive code, legal/compliance risk, product judgment, data migrations, billing, auth, permissions, and irreversible operations.

The key distinction: review findings should be **reproduced or tied to concrete evidence**. A long list of speculative suggestions is not better review; it is more review-shaped noise.

### Security review patterns for high-risk work

For security-sensitive changes, the methodology should produce a review loop that is scoped, confidence-aware, and repeatable.

Add these rules:

1. **Prefer bounded scans to vague full sweeps.** Review the changed service, directory, branch, data flow, or trust boundary first.
2. **Record confidence with every finding.** High-confidence issues should move fastest; low-confidence issues need explicit validation before they interrupt engineering.
3. **Require documented triage.** If a finding is dismissed, record why so the same issue does not keep resurfacing with no institutional memory.
4. **Optimize for time from finding to fix.** A result that becomes a reviewed patch today is more valuable than a large backlog ticket that no one acts on.
5. **Schedule recurring coverage.** Security review should run on a cadence for critical systems, not only before launches or after incidents.
6. **Route findings into existing workflows.** PRs, Jira, Slack, audit logs, and incident tooling should carry the result; do not trap security decisions in chat history.
7. **Keep human approval on remediation.** AI can scan, validate, and draft patches; humans still decide whether the finding is real and whether the fix is acceptable.

---

## Phase 6.5 — Final Review and Ship

**Who writes:** You own the final decision. The AI can assist.

After all implementation steps pass their local success criteria, do a final integration pass before calling the project done.

1. **Fresh-context review** — review the final diff against the plan and Definition of Done.
2. **Regression sweep** — run the highest-signal automated checks for the whole changed surface, not just the last step.
3. **Behavioural proof** — capture screenshots, endpoint responses, logs, or demo notes showing the user-visible outcome works.
4. **Risk review** — check security, permissions, data migration, billing, external APIs, and operational failure paths.
5. **Documentation update** — update README, runbooks, comments, API docs, or user-facing notes only where needed.
6. **Ship artifact** — commit, PR, release, deploy, migration, or handoff document.
7. **Post-ship check** — verify production/staging state, monitor logs, and record follow-up work.

For critical systems, add a recurring post-ship review path: scheduled security checks, documented dismissals, and a clear route from new finding to reviewed remediation.

If the work changes ownership or replaces an older system, do not stop at release. Add:

1. **Ownership handoff** — who operates it now, where the runbook lives, and who handles incidents.
2. **Sunset plan** — what old path, script, workflow, service, or manual process is being retired.
3. **Decommission checks** — data retention, access removal, dependency cleanup, alert cleanup, and documentation updates.

If the final review finds a structural issue, go back to Phase 3 or Phase 5. Do not patch around a broken plan at the finish line.

---

## Phase 7 — Skillify When Stable (Optional)

**Who writes:** You, after running the workflow 2-3 times.

Not every project has a Phase 7. Most don't. But when you find yourself re-running the same workflow across sessions or projects, stop copy-pasting prompts and lift the workflow into a reusable Claude Code **skill** or **plugin**.

### The difference

- **Skill** — a single-purpose `SKILL.md` file in `~/.claude/skills/<name>/`. Invoked with `/<name>` from any directory. Zero install overhead for you personally.
- **Plugin** — a bundle of skills + slash commands + MCP servers + hooks, distributed via git or marketplace. Right fit when ≥3 related skills belong together and teammates need to install them.

### The skillify test

Extract a workflow into a skill when **all three** are true:

1. **Repeated** — invoked across multiple sessions or projects, not one-shot.
2. **Stable** — the prompt has settled; you've stopped tweaking it.
3. **Triggered by a recognizable cue** — "new campaign", "deploy this", "run QA", not ad-hoc.

Bundle skills into a plugin when **both** are true:

1. **Clustered** — three or more related skills form one logical workflow.
2. **Shared** — teammates need to run it on their own machines.

### When NOT to skillify

- Project-bound code (Express routes, page HTML, specific chart rendering) — stays in the project.
- One-shot maintenance scripts (`patch_*.js`, `debug_tags.js`, data migrations) — not workflows.
- Prompts still in flux — if you're tweaking the wording every run, it's not stable enough yet.
- Single-invocation tasks — if you ran it once and won't run it again, skip.

### How to extract

1. Copy the phase prompt from `CLAUDE.md` into `~/.claude/skills/<name>/SKILL.md`.
2. Add frontmatter: `name`, `description` (one line that makes relevance obvious), and a clear "trigger when" rule.
3. Reference the scripts the skill calls by relative path — do not inline the script logic.
4. Invoke `/<name>` from a fresh directory and confirm it runs end-to-end.
5. When ≥3 skills cluster, create `plugin.json` and bundle.

### Why this is optional

Skillification has a real cost: the skill becomes a separate thing to version, test, and keep in sync with the project's scripts. Don't pay that cost until the workflow has earned it. The rule of thumb: run it twice project-local, then extract on the third run.

## Context Management

Context is your most precious resource. Manage it like memory.

- **Clear between unrelated tasks.** Don't let one task's context pollute another.
- **Clear between planning and execution.** The planning context is full of discussion, alternatives, and dead ends. Execution needs a clean slate with just the plan.
- **Use subagents for exploration.** They work in a separate context and report back summaries.
- **Stay under 100k tokens.** Performance starts degrading around 32k for buried information (the "lost in the middle" problem). At 250k+, the AI actively loses focus and forgets things.
- **After two failed corrections, start fresh.** Don't throw good tokens after bad. Clear context, write a better prompt, try again.
- **Name your sessions.** If your tool supports it, name sessions by task so you can resume the right one.

### Context budget checklist

Before a long session, decide what belongs in context and what should stay outside.

| Context source | Loads when | Use for | Watch for |
|----------------|------------|---------|-----------|
| `CLAUDE.md` | Every session | Durable project rules and conventions | Bloated rules that apply to every request |
| Prompt packet | Current task | Step-specific constraints and success criteria | Repeating the whole plan when only one step matters |
| File reads | On demand | Exact code needed for the task | Reading huge files or generated artifacts unnecessarily |
| Tool output | After commands | Test failures, logs, diagnostics | Dumping entire build logs into context |
| Skills | Description at start, body on use | Stable workflows | Too many always-visible skill descriptions |
| MCP tools | Tool names at start, schemas on use | Live external systems | Large tool surfaces and unnecessary schemas |
| Subagents | Separate context | Research, QA, review, isolated exploration | Poor summaries that omit evidence |
| Hooks | Outside context unless they return text | Guardrails and side effects | Hook output that injects noisy context |

Operational rules:

1. **Run context diagnostics.** Use `/context` or the tool's equivalent before long implementation sessions and before blaming the model.
2. **Compact deliberately.** Use `/compact` with a focus when possible: what must be preserved, what can be dropped, and what step comes next.
3. **Add compact instructions.** Put a "Compact Instructions" section in `CLAUDE.md` for long projects so summaries preserve decisions, current state, blockers, and success criteria.
4. **Summarize tool output.** Ask the AI to extract the relevant lines from logs instead of carrying the whole output forward.
5. **Move durable state into files.** `PLAN.md`, `RESEARCH.md`, issue links, and test fixtures survive context resets better than chat history.
6. **Use isolated contexts intentionally.** Subagents and fresh sessions are how you throw away exploration while keeping only findings.
7. **Recover from context thrash.** If compaction immediately fills again, stop, write a handoff summary to the plan, clear context, and resume from the artifact.

Context management is not just about fitting more tokens. It is about keeping the right information salient when the model decides what to do next.

### Understand the agentic loop

Claude Code is not autocomplete. It is a harness around a model plus tools. Most work cycles through:

1. **Gather context** — read files, search code, inspect git state, retrieve docs.
2. **Take action** — edit files, run commands, call tools, create branches or artifacts.
3. **Verify results** — run tests, inspect errors, compare output to the success criteria, then loop.

Your job is to control the loop, not micromanage every tool call. Intervene when the agent is gathering the wrong context, taking action outside scope, verifying the wrong thing, or repeating a failed correction pattern.

Because sessions, memory, tool outputs, and persistent instructions all compete for context, put durable rules in `CLAUDE.md`, keep task-specific constraints in the prompt packet, and use fresh sessions when the loop has learned the wrong lesson.

### Permission and environment boundaries

The same agentic loop behaves differently depending on where it runs:

| Environment | Use when | Watch for |
|-------------|----------|-----------|
| **Local** | You need real repo state, local services, credentials, or hardware access | Accidental edits outside scope, dirty worktree conflicts |
| **Cloud/remote VM** | You want isolated execution, long-running tasks, or repos not present locally | Missing local secrets, different tool versions, incomplete reproduction |
| **Remote control / browser UI** | You want web supervision while code still runs on your machine | Same local safety risks, less terminal situational awareness |
| **CI/CD** | You want repeatable verification or scheduled automation | Permissions, secrets, destructive commands, noisy failures |

Document the chosen environment in the implementation plan when it matters. A task that passes in a managed VM may still fail locally if the database, env vars, filesystem, or dependency versions differ.

---

## Team Operating Model

When AI makes code generation cheap, the bottleneck moves. The scarce work becomes verification, review, cross-functional alignment, security, and deciding which processes should no longer exist.

For teams adopting this methodology:

1. **Audit noisy workflows.** Pick the recurring meeting, review, status report, or approval path people dread. Ask whether it still serves a purpose. Kill it, automate it, or make it lighter.
2. **Move debates into artifacts.** When implementation is cheap, endless architecture debate is expensive. For reversible decisions, ask for 2-3 small competing PRs or prototypes and compare real diffs, APIs, tests, and user impact.
3. **Treat code as the source of truth.** Docs drift. If a spec must exist, keep it in the repo and verify that code and spec still agree.
4. **Shift quality left.** More generated code means human QA and late manual review will not scale. Invest earlier in tests, type checks, linting, security scans, fixtures, and automated review.
5. **Redraw human review boundaries.** Let AI handle style, duplicate logic, routine bugs, test suggestions, and review-response cleanup. Keep humans on product judgment, legal/compliance risk, security-sensitive boundaries, and architectural taste.
6. **Keep managers close to the work.** Engineering leaders need enough hands-on exposure to understand the new workflow. If managers cannot use the tools, they cannot design sane process around them.
7. **Avoid vanity metrics.** "Percent of code written by AI" is not the goal. Track whether onboarding is faster, PR cycle time is shorter, quality is stable, reliability is protected, and customers are better served.

Do not preserve old process just because it used to be load-bearing. Many software rituals were designed for a world where implementation was the expensive part. In agentic engineering, the expensive part is knowing whether the generated work is correct, safe, maintainable, and worth shipping.

### Decision rights

Professional teams move faster when decision rights are explicit.

Define:

1. **Product owner** — approves scope, priority, and user-facing tradeoffs.
2. **Technical owner** — approves architecture, standards, contracts, and implementation direction.
3. **Service or domain owner** — approves changes affecting a bounded system, API, or operational workflow.
4. **Release owner** — approves timing, environment readiness, and rollback posture.
5. **Security / compliance owner** — approves exceptions on high-risk paths where required.

The point is not bureaucracy. The point is to remove ambiguity about who can say "yes," who can say "not yet," and who must be consulted before merge or deploy.

### Operating cadence

Methodology needs rhythm, not just documents. For teams, set a cadence that keeps plans current and catches drift early:

1. **Intake cadence** — new work is classified, scoped, and accepted or rejected.
2. **Planning cadence** — initiative and workstream plans are refined, dependencies updated, and blockers surfaced.
3. **Execution cadence** — current-state blocks, PR flow, and review queues stay current daily.
4. **Release cadence** — environments, deployment approvals, release notes, and rollback readiness are reviewed before ship windows.
5. **Learning cadence** — incidents, false positives, rollout failures, and prompt or workflow failures feed back into standards and automation.

If the documents are static but the system keeps changing, the methodology has already drifted out of date.

### Methodology scorecard

Teams should measure whether the methodology improves delivery, not just whether it produces more artifacts.

Track a small scorecard:

1. **Flow** — PR lead time, time to merge, time from intake to ready, time from ready to ship.
2. **Quality** — change failure rate, rollback rate, escaped defects, open security findings, review rework rate.
3. **Review health** — review turnaround time, stale PR count, percent of changes with required evidence attached.
4. **Operational health** — deployment success rate, incident count after release, unresolved dependency count.
5. **AI effectiveness** — reduction in boilerplate work, review burden trend, adoption quality, not just seat usage.

If the scorecard gets worse after adopting more AI or more process, change the workflow. The point is better outcomes, not methodological purity.

### Adoption maturity path

Do not ask every team to jump from ad hoc work to a fully governed operating model in one move. Mature the system in stages:

| Level | What is true |
|-------|---------------|
| **Level 1 — Individual discipline** | One person uses the methodology consistently for planning, review, and verification |
| **Level 2 — Shared team baseline** | Repo standards, ownership, templates, CI checks, and review gates are consistent across one team |
| **Level 3 — Multi-team operating model** | Planning levels, dependencies, scorecards, and decision rights work across teams or domains |
| **Level 4 — Platformized methodology** | Reusable workflows, templates, guardrails, policy checks, and AI operating standards are shared organization-wide |

The goal is not to "reach level 4" by force. The goal is to adopt only the amount of structure your scale and risk require, while keeping the path upward clear.

### Exception and waiver model

Professional systems allow exceptions, but not silent exceptions.

When a team needs to bypass a rule:

1. **Record the exception explicitly** — what rule is being bypassed, why, who approved it, and when it expires.
2. **Time-box it.** Exceptions should have an owner and a review date.
3. **Separate emergency from convenience.** Production incident response may justify short-term bypass; schedule pressure alone usually does not.
4. **Capture compensating controls.** If one gate is skipped, note what temporary safeguard replaces it.
5. **Review recurring exceptions.** If the same waiver happens repeatedly, the standard or tooling is probably wrong.

The methodology should be strict enough to protect quality and flexible enough to handle reality. The audit trail is what makes that balance professional.

### Reference operating bundle

Teams adopt methodology faster when they get a concrete starting bundle instead of a philosophy document alone.

A practical reference bundle includes:

1. **Repo template** — baseline files, workflows, issue forms, PR template, CODEOWNERS, and docs structure.
2. **Planning pack** — initiative brief template, workstream plan template, ADR template, rollout plan template, post-ship review template.
3. **Guardrail pack** — rulesets, required checks, environment setup, dependency policy, secret policy, emergency-change procedure.
4. **AI pack** — prompt packet pattern, CLAUDE.md guidance, review policy, agent permission model, eval or scenario examples.
5. **Scorecard pack** — the small metrics set, owners, and review cadence.

Without a reference bundle, teams tend to agree with the methodology in theory and reimplement it inconsistently in practice.

### Dependency and escalation model

Large-team work fails at the seams. Track seams explicitly:

1. **Name blockers as dependencies, not surprises.**
2. **Assign an owner and due date to every cross-team dependency.**
3. **Escalate missing decisions early** when another team, contract, or environment blocks progress.
4. **Separate reversible from irreversible decisions.** Debate the irreversible ones more; prototype the reversible ones faster.
5. **Keep a short escalation path.** If a blocker sits too long, it should move to the right owner without creating a new committee.

### Enterprise rollout patterns

AI-native adoption looks different depending on who the system serves. Pick the rollout pattern before choosing tools.

| Pattern | Primary user | What to optimize | Main risk |
|---------|--------------|------------------|-----------|
| **Internal autonomous agent** | Engineering or ops teams | Throughput, verification, safe merge/deploy paths | Silent bad changes at high volume |
| **Org-wide coding standard** | Engineers, data scientists, technical teams | Governance, shared practices, onboarding, review quality | Uneven adoption and inconsistent guardrails |
| **Customer-facing AI workflow** | End users, including non-coders | Trust, control, explainability, UX, support handoff | Users cannot inspect or debug the AI's work |

Each pattern needs a different Definition of Done. An internal PR agent needs merge safety and regression protection. An org-wide coding rollout needs training, policy, and review boundaries. A customer-facing agent needs product UX, fallbacks, abuse handling, and support visibility.

The common mistake is treating all three as "add AI." They are different products with different users, risks, and operating metrics.

### AI rollout and measurement

GitHub's Copilot rollout material reinforces a point that belongs in this methodology: buying seats is not adoption, and adoption is not impact.

For team-scale AI rollout:

1. **Start with a system goal.** Faster PR lead time, lower review burden, better test coverage, faster onboarding, or lower change failure rate.
2. **Instrument leading indicators and system metrics together.** Usage and developer sentiment matter, but so do merge time, review time, successful builds, failure rate, and security posture.
3. **Roll out with governance and enablement.** Access, training, policy, and measurement need to ship together.
4. **Provision access intentionally.** Team-wide default access is fine only when enablement and policy are already ready; otherwise roll out by group.
5. **Keep human judgment on subjective work.** AI is best at boilerplate, obvious fixes, objective policy checks, and first drafts. Experts still handle ambiguous product judgment, architecture, and subjective accessibility or UX tradeoffs.
6. **Automate objective remediations first.** Objective issues such as simple policy violations, deterministic fixes, and repetitive hygiene work are the right starting point for agents.
7. **Review AI by outcomes, not excitement.** If delivery metrics and quality do not improve, the rollout is not working regardless of usage volume.

---

## Tooling Notes and Claude Code Examples

The methodology is tool-agnostic. Claude Code, Cursor, Copilot, custom agent harnesses, and internal platforms can all implement the same phases. The examples below use Claude Code because several useful workflow features are visible there today.

### Adaptive Thinking

Claude Opus 4.7 introduces *adaptive thinking*: instead of a fixed reasoning budget, the model dynamically allocates thinking tokens based on task complexity. For agentic engineering:

- **Use it on hard planning problems.** Phase 3 (contradiction finding) and Phase 5 (implementation ordering) benefit most — complex dependency analysis and subtle tradeoffs are where the extra reasoning earns its cost.
- **Don't force it on simple steps.** Routine execution in Phase 6 doesn't need deep reasoning. The model calibrates automatically.
- **128k output, 1M context.** Long research documents (Phase 2) and large codebases no longer require aggressive summarisation to fit context.

### MCP Servers — External Tool Integration

MCP (Model Context Protocol) servers let Claude call external tools — databases, APIs, internal services — natively during execution. Relevant to Phase 6:

- If your project integrates an external API, consider an MCP server rather than a brittle one-off wrapper
- Claude Code ships with built-in MCP servers; add custom ones in `.claude/settings.json`
- MCP Tool Search lazy-loads servers — only tools you actually invoke consume context (up to 95% context reduction vs loading all tools upfront)

Use MCP when the agent needs live structured access to another system, not when a copied excerpt or fixture would do.

| Need | Better fit |
|------|------------|
| One-time reference from docs, logs, or tickets | Paste/link the relevant excerpt into `RESEARCH.md` |
| Repeated access to an external system during implementation | MCP server |
| Deterministic local project workflow | Script, hook, or skill |
| Team-wide access to the same integration | Project-scoped MCP config with documented auth |
| Personal experimental tool | Local/user-scoped MCP config |

MCP planning checklist:

1. **Scope the server.** Local for personal experiments, project for team-shared integrations, user for tools you use across repos.
2. **Document auth and revocation.** The plan should say who needs access, how to log in, and how to revoke tokens.
3. **Minimize tool surface.** Expose only the tools the task needs; a huge tool list burns context and widens the blast radius.
4. **Write server instructions.** Explain when to use the tools, what they can do, and what not to do. Keep critical details first.
5. **Prefer read-only first.** Add write tools only after read flows are reliable and reviewed.
6. **Log external actions.** Any MCP call that mutates Jira, GitHub, Stripe, a database, or production systems needs an audit trail.
7. **Include fallback behaviour.** If the MCP server is unavailable, the implementation plan should say whether to stop, use fixtures, or ask for manual data.

MCP is powerful because it removes copy-paste. That is also the risk: the agent can now act on systems outside the repo. Treat every MCP server as part of the system boundary.

### Multi-Agent Systems

Use multiple agents only when responsibilities are genuinely separable. A useful subagent has a clear capability, a narrow tool set, and a result that can be evaluated independently. An "orchestrator" agent should route between defined capabilities, not supervise a vague committee.

Before adding another agent, ask:

1. Does this agent need different tools, context, permissions, or evaluation criteria?
2. Can its output be verified independently?
3. Is agent-to-agent communication simpler than a normal function call, queue, or workflow step?
4. What logs prove which agent did what?

If the answers are weak, keep it as one agent or ordinary code. Multi-agent architecture multiplies debugging surface area.

### Agentic workflows on GitHub

GitHub's agentic workflow direction reinforces the same rule used elsewhere in this methodology: autonomy is acceptable only when permissions, outputs, and review paths are bounded.

Good defaults:

1. **Start read-only.**
2. **Use preapproved write paths or safe outputs** for controlled mutations.
3. **Trigger from explicit artifacts** such as issues, PRs, CI failures, or labeled work queues.
4. **Route results back into PRs, issues, comments, or workflow artifacts** so the work is inspectable.
5. **Do not let agents invent their own backlog.**

### Hooks — Automated Behaviours

Claude Code hooks let you wire shell commands to events: before a tool runs, after the agent stops, on file save. Use them to enforce guardrails without relying on prompt instructions:

- Run your linter automatically after every edit
- Block commits that fail tests
- Post a Slack message when a long execution step completes

Hooks are configured in `.claude/settings.json`. Unlike prompt instructions, hooks execute at the harness level — the AI cannot bypass them.

Use hooks for deterministic policy, not taste:

| Hook use | Good fit | Poor fit |
|----------|----------|----------|
| **PreToolUse** | Block writes to generated files, secrets, migrations, or protected directories | Asking the model to reconsider style |
| **PostToolUse** | Run formatters, lint changed files, capture audit logs | Long full-suite tests after every tiny edit |
| **UserPromptSubmit** | Inject required project context or reject unsafe prompts | Loading huge docs into every prompt |
| **Stop/SubagentStop** | Summarize work, notify humans, save session metadata | Making final quality decisions without review |
| **PreCompact** | Preserve key state before context compression | Dumping noisy history back into context |

Hook safety rules:

1. **Keep blocking hooks fast.** If a hook blocks the agentic loop, it should finish quickly and fail clearly.
2. **Use async hooks for slow side effects.** Notifications, full test suites, and telemetry should not freeze every edit unless they are gating a high-risk operation.
3. **Return actionable errors.** A blocked tool call should tell the agent exactly what violated policy and what to do instead.
4. **Version project hooks.** Shared guardrails belong in `.claude/settings.json` and scripts under `.claude/hooks/`; personal notifications belong in local/user settings.
5. **Test hooks like code.** A broken hook can stall every agent session.
6. **Inspect active hooks.** Use the tool's hook viewer/menu before debugging strange agent behaviour.

Good hook policy turns "please remember not to do this" into "the harness physically prevents this." Bad hook policy turns every edit into a slow, surprising side effect.

### Capability Intake

AI coding tools change fast. Do not blindly add every new feature to your workflow. Treat tool updates like dependencies: evaluate, constrain, and promote only when they improve the methodology.

For each meaningful new capability:

1. **Map it to a phase.** Planning, research, execution, review, proactive automation, or team operations.
2. **Run it on low-risk work first.** A docs update, test-only change, or small bugfix reveals failure modes cheaply.
3. **Define the promotion rule.** Example: local review stays optional, deep parallel review becomes required for auth, billing, migrations, or large PRs.
4. **Update the artifact, not just memory.** Put the new rule in `PLAN.md`, `CLAUDE.md`, a hook, a skill, or CI.
5. **Track cost and latency.** A better tool that makes every small change expensive will quietly kill adoption.
6. **Revisit quarterly.** Model and tool capabilities shift; your trust boundary should move deliberately, not by accident.

Examples: a cloud review feature belongs in the review escalation ladder, not every edit. A routine/scheduled-agent feature belongs in the proactive workflow checklist, not free-form backlog browsing. A usage or cost breakdown belongs in verification before long-running sessions, not as an afterthought after the bill arrives.

---

## What LLMs Get Wrong (Expect This)

These aren't bugs — they're predictable failure modes. Plan for them:

| Failure mode | What happens | How to handle |
|-------------|--------------|---------------|
| **Overcomplication** | Excessive abstractions, unnecessary error handling, bloated code | Ask: "Would a senior engineer say this is overcomplicated? If yes, simplify." |
| **Scope creep** | Adds features, refactors adjacent work, "improves" things you didn't ask about | Point at non-goals. "Only change what's in the step." |
| **Silent failures** | Code runs without errors but produces wrong results | Verify correctness, not just execution. Check actual outputs. |
| **Confident bullshit** | States incorrect things with certainty, doesn't flag uncertainty | Verify API docs yourself. Don't trust the AI's memory of external APIs. |
| **Poor taste** | Ugly variable names, inconsistent style, unnecessary comments | Review and clean up. Or include style examples in the plan. |
| **Training data bleed** | Suggests standard patterns when you're doing something intentionally different | Be more explicit, or hand-code that part. |
| **Artifact mutation** | Changes or removes comments, copy, data, config, or code it doesn't fully understand as side effects | Review diffs carefully. Every changed line should trace to the request. |

---

## Quick Reference

```
Phase 0:   Triage risk + choose lightweight or full workflow        (YOU decide)
Phase 1:   Write objective + stakeholder + DoD draft + constraints  (YOU, no AI)
Phase 2:   AI produces research document + set up CLAUDE.md         (AI, 2-5k lines)
Phase 2.5: Configure harness guardrails + permissions + tools       (you configure, AI drafts)
Phase 3:   3-4 rounds of contradiction/gap finding                  (both, one issue at a time)
Phase 4:   AI rewrites for clarity, you review diffs                (AI drafts, you verify)
Phase 4.5: Design artifact: UI, agent contract, process, schema     (AI drafts, you approve)
Phase 5:   Implementation plan with steps + success criteria        (AI drafts, you review)
Phase 5.5: Readiness gate before execution                          (YOU approve)
Phase 6:   Execute one step at a time, verify hierarchy             (AI executes, you review)
Phase 6.5: Final review, ship, and post-ship check                  (YOU own final decision)
Phase 7:   Skillify stable workflows into ~/.claude/skills/         (OPTIONAL, most projects skip)
```

## Anti-Patterns

| Don't | Do instead |
|-------|------------|
| Ask the AI to do multiple things at once | One issue, one step at a time |
| Let the AI edit inline during refinement | Findings go at the bottom of the file |
| Skip to implementation before the plan is solid | Phases 1-4 first, always |
| Use the full methodology for every tiny change | Use Explore → Plan → Code → Verify → Commit for small, low-risk tasks |
| Let a "quick fix" grow silently | Re-triage and promote to the full workflow when risk expands |
| Create repos ad hoc with no ownership model | Decide repo topology, team ownership, and review gates up front |
| Start implementation from a vague request | Require a Definition of Ready with owner, scope, acceptance target, and risk |
| Re-read the whole document after every edit | Use git diffs |
| Keep going past 200k tokens of context | Clear context, re-read plan, continue |
| Hope there are no fatal flaws | Define abort criteria upfront |
| Start execution before Phase 6 | No implementation until the plan is locked |
| Plan indefinitely | Stop when findings become cosmetic |
| Correct the same mistake three times | Clear context, write a better prompt |
| Trust the AI's memory of external APIs | Verify docs yourself |
| Let the AI explore the codebase freely | Scope investigations, use subagents |
| Ask "how should I do this?" | Ask for 2-3 approaches with pros/cons |
| Frame verification as instructions | Frame as success criteria (declarative) |
| Skip CLAUDE.md setup | Wire in persistent context from Phase 2 |
| Treat CLAUDE.md as guaranteed enforcement | Pair critical rules with hooks, tests, CI, or review gates |
| Let architectural rules live only in senior engineer memory | Version ADRs, standards, contracts, and protected-path rules in the repo |
| Design the experience after implementation | Use Phase 4.5 to lock the relevant artifact first |
| Ignore AI hedging ("I think", "probably") | Treat as a confidence signal — stop and examine |
| Use vague one-line prompts for execution | Build a prompt packet with role, context, constraints, examples, output format |
| Keep correcting bad output in chat forever | Improve the prompt packet, then retry in a fresh context |
| Rely on "think step by step" for everything | Use explicit reasoning only when the task needs it |
| Build multi-agent systems by default | Split agents only when tools, permissions, or evaluation differ |
| Launch many agents into the same files | Give each agent disjoint scope and isolate write work |
| Pick a monorepo because big companies use one | Use a monorepo only when coupling, tooling, and ownership justify it |
| Treat Claude Code like autocomplete | Manage the context-action-verification loop explicitly |
| Ignore where the agent is running | Document local, cloud, remote, or CI environment assumptions |
| Merge code because the diff "looks fine" | Require linked work, acceptance artifact, owner approval, and evidence |
| Let context fill with raw logs and exploration | Summarize evidence and move durable state into files |
| Rely on auto-compaction to preserve intent | Add compact instructions and handoff summaries |
| Add MCP servers because they are available | Connect MCP only when live structured access beats copied context |
| Give MCP broad write access on day one | Start read-only, minimize tools, and add audited writes deliberately |
| Index every source before defining trust tiers | Define source classes, trust levels, freshness, and permissions first |
| Give broad repo admin access to everyone shipping code | Keep admin rights narrow; use teams, CODEOWNERS, rulesets, and environments for normal work |
| Ship an agent without logs or evals | Define observability and regression cases before deployment |
| Treat Slack, email, or chat as canonical policy by default | Prefer governed source systems and label lower-trust conversational sources clearly |
| Use one status-check stack for every change | Apply gates by change type and risk, not by habit |
| Measure AI adoption by generated-code percentage | Measure onboarding time, PR cycle time, quality, reliability, and customer outcomes |
| Keep legacy meetings and reviews by default | Audit noisy workflows; kill, automate, or simplify them |
| Resolve every technical disagreement in meetings | Compare small prototypes or PRs when code is cheaper than debate |
| Use one AI rollout playbook for every audience | Pick the pattern: internal agent, org-wide coding standard, or customer-facing workflow |
| Let proactive agents browse the whole backlog | Feed them approved, labeled, bounded work queues |
| Let background agents push directly to main | Require a review artifact: PR, draft PR, report, or patch |
| Adopt every new AI feature immediately | Map it to a phase, test it on low-risk work, then promote it deliberately |
| Treat deeper AI review as automatically better | Require evidence-backed findings and reserve deep review for higher-risk changes |
| Put important safety rules only in prompts | Enforce deterministic rules with fast blocking hooks |
| Make every hook synchronous and expensive | Keep blocking hooks fast; run slow side effects async or at review gates |
| Store all deployment secrets at repository scope | Use environment-specific secrets and reviewers for sensitive deploys |
| Ship a company brain without retrieval evals, citation checks, or permission tests | Validate relevance, grounding, freshness, and access control before rollout |
| Treat lightweight workflow as permission to skip planning | Keep exploration and planning before code, even in one session |
| Call work done after local tests only | Run final review, behavioural proof, and post-ship checks |

---

## The Expertise Paradox

This methodology works best for people who understand the domain well enough to verify the result. The AI provides leverage — speed, breadth, tirelessness — but you provide judgment, taste, and correctness. You need to inspect the artifact the AI produces and know whether it is right.

As Karpathy puts it: *"Deep technical expertise may be even more of a multiplier than before because of the added leverage."*

The risk for less experienced builders: if you cannot inspect the diff, output, workflow, report, or behaviour, you cannot verify the step, and you are back to vibe work — which is fine for throwaway projects but will produce slop at scale.

The methodology mitigates this by front-loading decisions into the plan (where you can think carefully) and reducing execution to mechanical verification (where the criteria are already defined). But ultimately, you need to understand the work well enough to reject a plausible wrong answer.

---

*Based on practitioner experience, refined with insights from Andrej Karpathy (who coined "vibe coding" and later proposed "agentic engineering"), Addy Osmani, GitHub Docs on rulesets, teams, CODEOWNERS, Projects, template repositories, community health files, environments, Dependabot, and secret scanning, Google's [Software Engineering at Google](https://abseil.io/resources/swe-book) guidance on version control and dependency management at scale, Anthropic's [Prompting 101 | Code w/ Claude](https://www.youtube.com/watch?v=ysPbXH0LpIE) workshop, Google Cloud's [Building AI agents with Claude in Vertex AI](https://www.youtube.com/watch?v=TUysIAtxyrQ) workshop, Fiona Fung's [Running an AI-native engineering org](https://www.youtube.com/watch?v=igO8iyca2_g) talk, Anthropic's [Building AI-native at enterprise scale](https://www.youtube.com/watch?v=XFaeIbL-lvE) panel, Anthropic's [Build a proactive agent workflow with Claude Code](https://www.youtube.com/watch?v=eSP7PLTXNy8) workshop, Anthropic's [What's new in Claude Code](https://www.youtube.com/watch?v=sRvUXLquiRg) session, Anthropic's [Agent view in Claude Code](https://www.youtube.com/watch?v=-INveHwbRz4) demo, Anthropic's [How Claude Code Works](https://www.youtube.com/watch?v=6bs5b4FltCU) session, Anthropic's [Hooks in Claude Code](https://www.youtube.com/watch?v=IkaPHiMDazM) demo, Anthropic's [MCP in Claude Code](https://www.youtube.com/watch?v=kkBFmwkDzdo) demo, Anthropic's [Context Management in Claude Code](https://www.youtube.com/watch?v=eW3oTyfeWZ0) session, Anthropic's [Explore → Plan → Code → Commit workflow](https://www.youtube.com/watch?v=xJQuF02NAK8) session, Anthropic's [The CLAUDE.md file](https://www.youtube.com/watch?v=O0FGCxkHM-U) session, and the AI-assisted development community. Updated May 2026 to reflect GitHub operating models for scaling teams, repository topology choices, org-level governance, rulesets, deployment environments, community health defaults, dependency and secret security, Claude 4.7 adaptive thinking, context management, CLAUDE.md hygiene, MCP tooling, hooks, visual design workflows, structured prompt packets, production agent operations, proactive workflows, parallel agent coordination, environment boundaries, lightweight workflows, AI-native team process, enterprise rollout patterns, and capability intake.*
