# OCT — Organizational Cognitive Telemetry

> A system for observing, classifying, and improving how organizations think and interact with AI.

## Canonical Definition

**Organizational Cognitive Telemetry (OCT)** is a telemetry and insight system designed to capture **sanitized AI interaction signals** in order to surface cognitive friction, knowledge gaps, and recurring patterns across an organization.

OCT records **every prompt** submitted to the system, removes confidential and identifying information, preserves **sequence order**, retains the **date**, and intentionally omits **precise timestamps**. This allows OCT to identify trends and breakdowns in understanding without becoming a surveillance or logging system.

OCT is focused on **organizational awareness**, not content storage.

### Why OCT Exists

As AI adoption increases, organizations struggle to see:
- where confusion repeats,
- which knowledge is missing or unclear,
- how workflows break down,
- and why AI responses fail to land.

Traditional logs answer *what happened*.  
OCT answers *where understanding breaks down*.

### What OCT Is

OCT captures:
- sanitized prompt text,
- relative ordering of prompts,
- date-level activity,
- classification metadata (e.g. noise, friction, input error),
- topic or ontology tags,
- non-identifying correlation references.

OCT is consumed by:
- internal reporting tools,
- system designers,
- workflow and documentation owners,
- leadership and governance reviews.

### What OCT Is Not

OCT is intentionally **not**:
- a chat transcript archive,
- a document repository,
- a monitoring or surveillance tool,
- a data lake,
- a replacement for operational logs.

It stores **signals and patterns**, not raw data.

### Core Design Principles

#### Insight Over Surveillance
OCT is designed to surface patterns, not track individuals.
- no identity reconstruction
- no user-level replay
- no minute-by-minute activity tracking

#### Sanitized by Default
All prompts are scrubbed before storage:
- no PII
- no credentials
- no confidential identifiers

Sanitization occurs **before persistence**.

#### Order Without Precision
OCT preserves conversational flow without temporal overreach:
- prompts are stored in order,
- date is retained,
- timestamps are removed.

#### Security as a Prerequisite
OCT never widens access.
- all data has already passed permission checks upstream,
- OCT introduces no new visibility paths.

### Core OCT Domains

#### Cognitive Friction
Signals where users or systems struggle:
- repeated clarification
- low-confidence outcomes
- malformed or ambiguous prompts

#### Noise Detection
Identifies:
- low-signal usage,
- misdirected questions,
- non-actionable prompts.

#### Design & Knowledge Gaps
Surfaces:
- missing documentation,
- unclear ownership,
- inconsistent terminology,
- broken or absent workflows.

#### Usage Patterns
Aggregated views of:
- topic recurrence,
- escalation zones,
- cross-team overlap.

### Data Lifecycle & Retention

OCT follows **least-retention principles**:
- no raw sensitive content,
- no long-lived identity data,
- evolving aggregates instead of growing logs.

Operational debug logs remain separate and short-lived.

### Intended Use

OCT is intended to support:
- system improvement,
- documentation prioritization,
- workflow tuning,
- organizational clarity.

It is not intended for:
- employee performance monitoring,
- compliance replay,
- individual behavior analysis.

### Design & Specifications

The following documents define OCT’s architectural boundaries and invariants:

- **[ARCHITECTURE.md](ARCHITECTURE.md)**  
  Describes what feeds OCT, what it records, what it emits, and what it explicitly does not do.

- **[NON_GOALS.md](NON_GOALS.md)**  
  Lists out-of-scope responsibilities to prevent scope creep and misuse.

- **[ai/prompt-redaction-scaffolding.md](ai/prompt-redaction-scaffolding.md)**  
  Canonical specification for prompt sanitization and redaction prior to OCT persistence.

These documents are considered **foundational**.  
Contributions should align with them.

### Contributing

We welcome contributions to expand and improve the Organizational Cognitive Telemetry project. If you’re interested, please check out the **[contributing guidelines](./CONTRIBUTING.md)** for more information.

### Contact

- **Author:** William Shostak (https://github.com/wshostak)

### License

This project is licensed under the **ISC License** — see the **[LICENSE](./LICENSE.txt)** file for more details.

Copyright (c) 2025 William Shostak
