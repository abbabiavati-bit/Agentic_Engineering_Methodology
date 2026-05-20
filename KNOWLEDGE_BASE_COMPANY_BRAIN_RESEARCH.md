# Company Brain / Knowledge Base Research

Updated: May 20, 2026

## Why this matters

A "company brain" is not only for AI agents.

At professional scale, it is a governed retrieval system that supports:

1. humans searching and asking questions
2. copilots and chat assistants
3. background automations
4. agents that need grounded context before acting
5. onboarding, support, operations, delivery, and decision-making

It is not just a document repository, vector database, or enterprise search bar. At professional scale, it is a governed retrieval system that:

1. Gives agents and humans access to current company knowledge.
2. Respects source-system permissions.
3. Produces grounded answers with citations.
4. Keeps knowledge fresh enough for operational use.
5. Can be evaluated, audited, and improved over time.

The practical shift is this:

- A wiki alone is not a company brain.
- A vector database alone is not a company brain.
- An agent with unrestricted search is not a company brain.

The right mental model is:

`owned sources + permission-aware retrieval + grounded answers + evals + operating model`

## When a company brain is useful

You should consider a company brain whenever the organization has high-value knowledge spread across multiple people, tools, or repositories and users keep losing time or quality because they cannot reliably retrieve it.

Common high-value uses:

1. **Onboarding** — new hires need fast access to how the company actually works.
2. **Engineering delivery** — developers need architecture, policy, API, repo, and rollout context quickly.
3. **Support and operations** — teams need grounded access to procedures, incidents, policies, and system ownership.
4. **Product and project work** — people need fast access to decisions, roadmaps, requirements, and prior learnings.
5. **Sales, success, and internal enablement** — teams need trusted answers from product, process, CRM, and policy knowledge.
6. **Cross-functional coordination** — people need to find the right owner, dependency, or governing decision without asking around.
7. **AI assistance** — copilots, chat assistants, and agents need grounded context rather than general-model guesses.

The company brain is especially useful when the cost of "asking around" or "searching five systems manually" is already high.

## When it is not necessary

Do not assume every team needs one immediately.

You may not need a formal company brain yet if:

1. the team is very small and knowledge is still mostly local and current
2. one canonical system already contains almost everything important
3. the main issue is poor source quality, not retrieval
4. the organization lacks source ownership and review discipline
5. sensitive knowledge cannot yet be governed safely for AI retrieval

In those cases, the first step is usually to improve canonical documentation and ownership before building a retrieval layer on top.

## What problem it is actually solving

A company brain primarily solves four classes of organizational problem:

1. **Fragmentation** — knowledge is spread across docs, tickets, chat, code, drives, wikis, and business systems.
2. **Latency** — people wait too long to find an answer or the right owner.
3. **Inconsistency** — different teams answer the same question differently because the source of truth is unclear.
4. **Non-reusability** — knowledge exists, but cannot be reliably reused by humans or software systems.

This is why a company brain is valuable even before fully autonomous agents enter the picture.

## How the methodology should decide whether you need one

Yes, the methodology should be able to recommend when a company brain is warranted.

Add a decision gate like this:

Build or adopt a company brain when **three or more** of the following are true:

1. important knowledge lives in more than three systems
2. people repeatedly ask the same operational, product, or policy questions
3. onboarding takes too long because knowledge is hard to find
4. support, engineering, or operations lose time searching for internal answers
5. teams rely on Slack, meetings, or specific individuals as the real source of truth
6. agents, copilots, or automations need grounded company context
7. stale or conflicting internal guidance causes quality or compliance issues
8. cross-team dependencies are hard to trace

Delay the build if these are true instead:

1. no one owns the underlying sources
2. permissions are too unclear to enforce safely
3. canonical policies and docs are missing or unmaintained
4. there is no capacity to evaluate or operate the system after launch

In other words: the methodology should recommend a company brain when the retrieval problem is real and the governance foundation is strong enough.

## Core findings from research

### 1. Permission fidelity is non-negotiable

This was the most consistent theme across official vendor material.

- OpenAI `company knowledge` uses workspace apps, RBAC, group permissions, SSO, and SCIM, and states that it respects existing per-user permissions.
- Glean documents permission-aware connectors as a core platform function and repeatedly emphasizes source-system access enforcement.
- Atlassian Rovo states that connector and agent access respects third-party app permissions and Atlassian administration controls.
- Microsoft 365 Copilot Search and the Retrieval API ground responses on Microsoft Graph and connectors while preserving user access controls.

Methodology implication:

Do not build a company brain unless you can answer:

1. What identity is the system using?
2. Where do permissions come from?
3. How quickly do permission changes propagate?
4. What happens when permissions cannot be verified?

If you cannot answer those four questions, the system is not ready for sensitive internal use.

### 2. Hybrid retrieval beats vector-only retrieval for enterprise knowledge

Official retrieval platforms repeatedly push hybrid search:

- Azure AI Search recommends hybrid search with semantic ranking for many RAG workloads.
- Pinecone supports hybrid search and explicitly warns about weighting and production tuning.
- Vespa positions hybrid retrieval as core to enterprise search quality.
- Google Vertex AI Search combines search, RAG, connectors, and grounding on enterprise data.

Methodology implication:

Default to:

- lexical / keyword retrieval
- semantic / vector retrieval
- reranking
- metadata filtering

Do not default to embeddings-only retrieval for company knowledge. Enterprise knowledge contains exact names, acronyms, policy phrases, IDs, version numbers, code symbols, and product terms that vector-only retrieval often handles poorly.

### 3. Freshness is as important as relevance

Official vendor positioning consistently treats connectors, incremental crawling, and webhooks as first-class.

- Glean emphasizes webhooks and incremental crawling for freshness.
- Vertex AI Search emphasizes connectors and fresh enterprise data.
- Rovo distinguishes synced, synced-lite, direct, and smart-link connector types, which changes freshness and storage behavior.

Methodology implication:

Every source should have an explicit freshness model:

| Source type | Freshness expectation |
|-------------|-----------------------|
| Policies, legal, pricing | Immediate or tightly controlled updates |
| Product docs, engineering docs | Near-real-time or release-driven refresh |
| Support content | Daily or faster |
| Archived knowledge | Scheduled refresh acceptable |

If freshness is not defined, the company brain will become trusted for the wrong reasons and wrong answers will look authoritative.

### 4. A company brain is a source-ownership problem before it is an embedding problem

The documents and platforms are useful only if the source material is maintained.

Research and docs repeatedly point back to:

- source ownership
- connector coverage
- content quality
- citations
- documented permissions

Methodology implication:

Every important source needs:

1. a business owner
2. a technical owner
3. a freshness policy
4. an AI-eligibility policy
5. a review cadence

Without that, the company brain will index stale, conflicting, or low-trust content.

### 5. Evaluation must measure retrieval and answer quality separately

Official OpenAI material explicitly ties retrieval systems to evals. Emerging research such as `EnterpriseRAG-Bench` also reinforces the enterprise-specific evaluation problem.

Methodology implication:

Evaluate at least four layers:

1. **Coverage** — was the right source available?
2. **Retrieval quality** — were the right passages returned?
3. **Grounding quality** — did the answer stay faithful to retrieved evidence?
4. **Task utility** — did the answer actually help the user complete work?

If you only evaluate final answer quality, you will not know whether failures came from missing data, bad retrieval, weak ranking, or poor prompting.

## What a professional company brain should contain

The company brain should not attempt to absorb every piece of data equally. It needs source classes.

### Source classes

| Class | Examples | Should agents use it? | Notes |
|-------|----------|-----------------------|-------|
| **Canonical policy** | Security policy, finance policy, HR policy, legal guidance | Yes, high priority | Highest governance and freshness requirements |
| **Operational documentation** | Runbooks, incident guides, deployment procedures, support SOPs | Yes | Requires strong ownership and review cadence |
| **Product and engineering knowledge** | Architecture docs, API docs, ADRs, repo docs, release notes | Yes | Usually best combined with code and issue search |
| **Work coordination** | Jira, GitHub issues, PRs, milestones, project boards | Yes, with caution | Useful but noisy; often time-sensitive |
| **Communications** | Slack, Teams, email threads, meeting notes | Sometimes | High value, high noise, high permission sensitivity |
| **Business system data** | CRM notes, ticketing systems, BI docs | Sometimes | Useful when ownership and permission models are clear |
| **Raw data / analytics** | Tables, dashboards, warehouse docs | Usually via governed interfaces | Prefer summary, contracts, or query tools over raw unrestricted retrieval |
| **External web and market context** | Competitors, regulations, docs | Sometimes | Treat as a separate trust tier from internal sources |

Methodology rule:

Do not give all sources equal trust. The company brain should rank or label sources by trust tier and usage policy.

## Recommended methodology for building a company brain

This is the part most relevant for the main methodology.

### Phase A — Define the operating goal

Start with the actual jobs the company brain must support.

Examples:

- answer policy questions
- unblock engineering implementation
- support incident response
- accelerate onboarding
- assist support or sales
- ground internal agents

Write:

1. user groups
2. tasks
3. failure cost
4. required freshness
5. required citation behavior

If the answer to "who is this for?" is "everyone," the scope is too vague.

### Phase B — Define source inventory and trust tiers

Create a source inventory with:

1. source name
2. system of record
3. owner
4. sensitivity tier
5. freshness expectation
6. permission model
7. AI retrieval allowed / not allowed
8. connector status

This should become a versioned artifact, not a spreadsheet that disappears.

### Phase C — Define the knowledge model

Before tooling, decide what units of knowledge matter.

For each source, define:

1. document or record unit
2. chunking strategy
3. metadata fields
4. parent-child structure
5. citation format
6. archival behavior

Recommended metadata:

- source system
- owner
- trust tier
- updated at
- sensitivity
- audience
- product/domain
- URL / record ID
- version / release if relevant

### Phase D — Define permission and identity behavior

This is a hard gate.

Choose one pattern:

1. **Source-enforced retrieval** — retrieve live or with permission checks tied directly to the source system.
2. **Indexed retrieval with ACL sync** — index content and permissions metadata; filter at query time.
3. **Audience-separated indexes** — separate indexes or namespaces by access tier.

For most organizations, indexed retrieval with ACL sync plus metadata filtering is the practical middle ground.

Document:

1. identity provider
2. group sync
3. connector auth model
4. permission refresh model
5. audit logging
6. failure behavior when permissions are stale or unknown

### Phase E — Build retrieval intentionally

Default retrieval stack:

1. keyword retrieval
2. vector retrieval
3. metadata filtering
4. reranking
5. citation selection
6. answer generation

Optional:

1. query rewriting
2. agentic retrieval for decomposition
3. structured retrieval for tables or APIs
4. graph-style relationship resolution

Do not jump to "agentic retrieval" unless simpler retrieval is already working. Complex retrieval layers multiply debugging cost.

### Phase F — Add answer policy

Every company brain should define answer rules:

1. cite sources
2. prefer canonical sources over chat sources
3. say "I don't know" when evidence is weak
4. refuse when permissions or safety rules require refusal
5. expose recency when it matters
6. distinguish sourced answers from model inference

### Phase G — Evaluate before rollout

Build eval sets by use case:

- policy Q&A
- engineering Q&A
- support Q&A
- onboarding Q&A
- cross-source synthesis
- permission-sensitive queries

Minimum eval dimensions:

1. retrieval relevance
2. citation correctness
3. hallucination rate
4. source preference correctness
5. latency
6. permission leakage
7. stale-answer rate

### Phase H — Operate it like a product

The company brain needs:

1. source onboarding workflow
2. source offboarding workflow
3. change-management process for sensitive sources
4. quality review cadence
5. usage analytics
6. incident response path
7. owner for the platform

This is not "set up once and forget."

## Methodology implications

The main methodology should not assume every project needs a company brain, but it should be able to recommend one deliberately.

### Phase 0 trigger

Phase 0 should ask:

1. Is knowledge fragmentation slowing delivery, onboarding, support, or decision-making?
2. Do people repeatedly need answers that exist somewhere in company systems but are hard to retrieve?
3. Do copilots, automations, or agents need grounded internal context to be useful?
4. Are source ownership and permissions mature enough to support retrieval safely?

If the answer is "yes" to the first three and at least "mostly yes" to the fourth, the methodology should recommend the company-brain path.

### Phase 2 research requirement

When the company-brain path is selected, research must include:

1. source inventory
2. source owners
3. trust tiers
4. freshness policies
5. permission model
6. retrieval architecture options
7. answer policy
8. evaluation plan
9. operating model after launch

### Phase 5 implementation requirement

The implementation plan should explicitly name:

1. connector / ingestion work
2. chunking and metadata model
3. permission enforcement
4. ranking and retrieval strategy
5. citation behavior
6. evals
7. ownership after launch
8. review and refresh cadence

### A dedicated archetype is justified

The main methodology should eventually add:

`Knowledge / company brain system`

This archetype is justified because the design center is different from a normal website, agent, or automation:

- knowledge quality matters more than feature surface area
- permissions and freshness are hard gates
- source ownership is core architecture
- evaluation must measure retrieval, not only final output

## Tool options

The tool landscape splits into two broad strategies:

1. buy an enterprise search / company knowledge product
2. build a governed retrieval layer on your own stack

### Option 1 — Company knowledge / enterprise search products

Best when:

- you need fast deployment
- you have many SaaS tools already
- you want connectors and permissions handled for you
- you want broad search across the company before custom agents

#### OpenAI Company knowledge

What it is:

- ChatGPT Business / Enterprise / Edu feature that uses installed apps as company knowledge sources with citations and RBAC-aware access.

Strengths:

- very fast path to usable company-grounded answers
- workspace RBAC and group controls
- per-user app permissions
- good fit for general knowledge assistance

Limits:

- centered around ChatGPT experience
- less suited if you need deep custom retrieval logic or highly bespoke workflows
- depends on app support with `File Search`

Best fit:

- organizations standardizing on ChatGPT as the main assistant surface
- quick rollout of knowledge assistance before custom application development

Sources:

- https://help.openai.com/en/articles/12628342-company-knowledge-in-chatgpt-business-enterprise-and-edu
- https://openai.com/solutions/blueprints/knowledge-retrieval/
- https://platform.openai.com/docs/api-reference/vector-stores/search

#### Glean

What it is:

- enterprise search and AI answer platform built around connectors, permission enforcement, and knowledge graph concepts.

Strengths:

- strong connector story
- strong permission-awareness positioning
- broad enterprise-search orientation
- good fit for cross-app search and internal answers

Limits:

- less of a fully custom build substrate than a raw search stack
- vendor-managed platform tradeoffs

Best fit:

- medium to large organizations needing broad internal search and answers across many systems

Sources:

- https://docs.glean.com/connectors/about
- https://docs.glean.com/user-guide/assistant/ai-answers
- https://docs.glean.com/administration/search/faq

#### Atlassian Rovo

What it is:

- search, chat, and agents grounded in Atlassian plus connected third-party systems via Teamwork Graph connectors.

Strengths:

- good fit if Jira and Confluence are already central systems
- connector types give architecture options: synced, synced-lite, direct, smart-link
- agents can use organizational knowledge with permission respect

Limits:

- strongest fit inside the Atlassian ecosystem
- knowledge scope and connector behavior require careful admin design

Best fit:

- Atlassian-centric engineering and operations organizations

Sources:

- https://support.atlassian.com/organization-administration/docs/manage-rovo-connectors/
- https://support.atlassian.com/organization-administration/docs/rovo-connector-types/
- https://support.atlassian.com/rovo/docs/knowledge-sources-for-agents/
- https://support.atlassian.com/rovo/docs/rovo-data-privacy-and-usage-guidelines/

#### Microsoft 365 Copilot Search

What it is:

- universal AI-powered search grounded in Microsoft Graph plus third-party connectors.

Strengths:

- strong fit for Microsoft-heavy organizations
- Graph grounding and Retrieval API
- enterprise identity and access alignment

Limits:

- strongest value if Microsoft 365 is already the knowledge center
- can be less attractive for highly heterogeneous stacks unless connector coverage is sufficient

Best fit:

- enterprises centered on SharePoint, OneDrive, Teams, Outlook, and Microsoft identity

Sources:

- https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-search
- https://learn.microsoft.com/en-us/microsoftsearch/semantic-index-for-copilot
- https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-reference/copilotroot-retrieval

#### Notion Enterprise Search

What it is:

- AI enterprise search layered into the Notion workspace with connectors and citations.

Strengths:

- strong end-user experience
- good for knowledge-centric teams already living in Notion
- combines workspace and cross-tool search

Limits:

- best fit when Notion is already a core operating hub
- less of a custom retrieval platform

Best fit:

- startups and growth-stage teams with Notion-centered knowledge operations

Sources:

- https://www.notion.com/product/enterprise-search
- https://www.notion.com/help/enterprise-search

#### Google Vertex AI Search

What it is:

- Google-quality search and enterprise RAG / grounding platform inside Vertex AI Agent Builder.

Strengths:

- good out-of-the-box RAG and grounding
- connectors, document processing, and search quality
- strong fit if you want search plus custom agents on Google Cloud

Limits:

- cloud-platform complexity versus pure SaaS search products
- requires more technical design than a simple workspace-native search tool

Best fit:

- teams building custom internal or external search / agent products on Google Cloud

Sources:

- https://cloud.google.com/enterprise-search
- https://docs.cloud.google.com/generative-ai-app-builder/docs/enterprise-search-introduction
- https://docs.cloud.google.com/vertex-ai/generative-ai/docs/grounding/grounding-with-vertex-ai-search

### Option 2 — Build your own governed retrieval layer

Best when:

- you need custom workflows, custom agent behavior, or productized external AI
- you need more control over indexing and ranking
- you must integrate unusual data sources or rules
- you need your company brain embedded inside your own app or platform

#### OpenAI retrieval stack

Pieces:

- File Search
- vector stores
- Agents / Chat SDKs
- Evals
- company knowledge for workspace-native usage

Strengths:

- fast start for custom assistants
- strong eval story
- good fit if OpenAI is your primary model layer

Use when:

- you want a managed retrieval foundation plus custom application logic

Sources:

- https://openai.com/solutions/blueprints/knowledge-retrieval/
- https://platform.openai.com/docs/api-reference/vector-stores/search

#### Azure AI Search

Pieces:

- vector search
- hybrid search
- semantic ranking
- integrated chunking and vectorization
- agentic retrieval

Strengths:

- very mature retrieval substrate
- strong documentation around hybrid retrieval and chunking
- good fit for custom enterprise RAG

Use when:

- you want custom control and Azure alignment

Sources:

- https://learn.microsoft.com/en-us/azure/search/search-what-is-azure-search
- https://learn.microsoft.com/en-us/azure/search/hybrid-search-how-to-query
- https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview
- https://learn.microsoft.com/en-us/azure/search/search-how-to-semantic-chunking

#### Pinecone

Pieces:

- managed vector / hybrid retrieval
- namespaces
- metadata filtering
- dense + sparse retrieval patterns

Strengths:

- focused retrieval infrastructure
- strong docs on metadata filtering and hybrid patterns

Use when:

- you want a managed search layer and will build the surrounding company brain yourself

Sources:

- https://docs.pinecone.io/guides/search/filter-by-metadata
- https://docs.pinecone.io/guides/search/hybrid-search
- https://docs.pinecone.io/guides/index-data/data-modeling

#### pgvector

Pieces:

- vector similarity search inside Postgres

Strengths:

- vectors live with relational data
- ACID, joins, PITR, familiar ops for Postgres teams

Limits:

- you own more of the retrieval product design
- less turnkey than enterprise search platforms

Use when:

- the team is strong in Postgres and wants tight integration with application data

Source:

- https://github.com/pgvector/pgvector

#### Vespa

Pieces:

- large-scale hybrid search platform
- real-time ingest
- multi-stage ranking

Strengths:

- strong fit for large-scale search-heavy systems
- advanced ranking and serving model

Use when:

- the company brain is becoming a serious search platform or customer-facing product

Sources:

- https://vespa.ai/architecture/
- https://vespa.ai/vespa-content/uploads/2025/02/Managers-Guide-to-RAG.pdf

#### Anthropic MCP + CLAUDE.md + source systems

What it is:

- not a complete company brain platform by itself, but a strong pattern for governed agent context:
  - `CLAUDE.md` for persistent instructions and project memory
  - MCP connectors for direct access to governed source systems

Strengths:

- good for agent workflows where live tools matter more than large centralized indexes
- strong project / enterprise memory layering

Limits:

- not a complete enterprise search platform
- requires surrounding retrieval and knowledge design

Use when:

- you want agents to act against live systems with clear instruction layers and tool boundaries

Sources:

- https://docs.anthropic.com/en/docs/claude-code/memory
- https://docs.anthropic.com/en/docs/agents-and-tools/mcp-connector

## Practical tool selection guidance

### If you want the fastest internal rollout

Start with:

- OpenAI Company knowledge
- Glean
- Notion Enterprise Search
- Microsoft 365 Copilot Search
- Atlassian Rovo

Choose based on where your knowledge already lives and how strong the permission / connector story is for your stack.

### If you want a custom internal assistant or company brain product

Start with:

- OpenAI retrieval stack
- Azure AI Search
- Vertex AI Search
- Pinecone
- pgvector
- Vespa

Choose based on:

1. cloud alignment
2. permission model complexity
3. need for hybrid retrieval
4. engineering capacity
5. scale and latency requirements

### If you want agents that can read and act

You usually need both:

1. a company brain or retrieval layer
2. tool / action integration

That means combinations such as:

- Company knowledge + ticketing / code / CRM actions
- Azure AI Search + app APIs
- Vertex AI Search + Agent Builder tools
- MCP connectors + governed source systems

## Recommended methodology additions for this repo

The main methodology should eventually get a dedicated section for company brain systems. Suggested structure:

### 1. Add a new archetype

`Knowledge / company brain system`

Research should emphasize:

- source inventory
- permissions
- freshness
- trust tiers
- answer policy
- evals

Design/spec should produce:

- source taxonomy
- permission model
- retrieval architecture
- citation policy
- eval plan

Verification should prove:

- permission fidelity
- citation quality
- freshness
- retrieval relevance
- hallucination control

### 2. Add planning gates specific to company brain work

Before execution:

1. source inventory exists
2. source owners are assigned
3. permission model is documented
4. freshness model is documented
5. eval set exists
6. citation behavior is defined
7. failure / refusal behavior is defined

### 3. Add anti-patterns

- indexing every source before defining trust tiers
- mixing public web and internal knowledge without labeling provenance
- using vector-only retrieval for exact-identifier-heavy enterprise content
- ignoring permission propagation lag
- shipping without evals for leakage, staleness, and citation correctness
- treating Slack or email as canonical policy

## Recommended starting strategy

For most teams, the right sequence is:

1. **Fix canonical knowledge first** — policies, runbooks, ADRs, product docs, standards.
2. **Add a workspace-native search layer** if you need immediate value quickly.
3. **Add custom retrieval** only when workflows or product needs exceed what the search product can do.
4. **Add action-taking agents last** once retrieval quality, permissions, and evals are trustworthy.

This is the same pattern as the rest of the methodology:

`foundation -> constraints -> evals -> execution -> scale`

## Source list

### OpenAI

- https://openai.com/solutions/blueprints/knowledge-retrieval/
- https://help.openai.com/en/articles/12628342-company-knowledge-in-chatgpt-business-enterprise-and-edu
- https://platform.openai.com/docs/api-reference/vector-stores/search

### Anthropic

- https://docs.anthropic.com/en/docs/claude-code/memory
- https://docs.anthropic.com/en/docs/agents-and-tools/mcp-connector

### Microsoft

- https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-search
- https://learn.microsoft.com/en-us/microsoftsearch/semantic-index-for-copilot
- https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-reference/copilotroot-retrieval
- https://learn.microsoft.com/en-us/azure/search/search-what-is-azure-search
- https://learn.microsoft.com/en-us/azure/search/hybrid-search-how-to-query
- https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview
- https://learn.microsoft.com/en-us/azure/search/search-how-to-semantic-chunking

### Google Cloud

- https://cloud.google.com/enterprise-search
- https://docs.cloud.google.com/generative-ai-app-builder/docs/enterprise-search-introduction
- https://docs.cloud.google.com/vertex-ai/generative-ai/docs/grounding/grounding-with-vertex-ai-search
- https://docs.cloud.google.com/vertex-ai/generative-ai/docs/agent-builder/overview

### Atlassian

- https://support.atlassian.com/organization-administration/docs/manage-rovo-connectors/
- https://support.atlassian.com/organization-administration/docs/rovo-connector-types/
- https://support.atlassian.com/rovo/docs/knowledge-sources-for-agents/
- https://support.atlassian.com/rovo/docs/rovo-data-privacy-and-usage-guidelines/

### Glean

- https://docs.glean.com/connectors/about
- https://docs.glean.com/user-guide/assistant/ai-answers
- https://docs.glean.com/administration/search/faq
- https://docs.glean.com/administration/search/troubleshooting

### Notion

- https://www.notion.com/product/enterprise-search
- https://www.notion.com/help/enterprise-search

### Retrieval infrastructure

- https://docs.pinecone.io/guides/search/filter-by-metadata
- https://docs.pinecone.io/guides/search/hybrid-search
- https://docs.pinecone.io/guides/index-data/data-modeling
- https://github.com/pgvector/pgvector
- https://vespa.ai/architecture/

### Supplementary research

- https://arxiv.org/abs/2605.05253
- https://arxiv.org/abs/2605.05538
