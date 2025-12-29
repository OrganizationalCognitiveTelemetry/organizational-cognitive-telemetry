# OCT — Organizational Cognitive Telemetry

> A telemetry and insight system that surfaces cognitive friction and knowledge gaps across an organization — **without storing prompts**.

## Canonical Definition

**Organizational Cognitive Telemetry (OCT)** is a telemetry and insight system designed to capture **sanitized AI interaction signals** in order to surface **cognitive friction, knowledge gaps, and recurring patterns** across an organization.

OCT treats prompts as **transient inputs**, not records. Prompts exist only long enough to derive **non-identifying, organizational artifacts** (failure-mode summaries, trend states, confidence metrics). OCT is focused on **organizational awareness**, not content storage, surveillance, replay, or audit trails.

### Why OCT Exists

As AI adoption scales, organizations lose visibility into:
- where confusion repeats,
- what documentation is missing or unclear,
- which workflows produce consistent friction,
- why AI responses fail to land.

Traditional logs answer *what happened*.  
OCT answers **where understanding breaks down** — while remaining **non-surveillant by design**.

### Prompt Ephemerality as a Design Feature

In OCT, prompts are **transient inputs**, not records.

They exist only long enough to:
1. be classified (**noise** | **issue** | **input-error**)
2. be matched to an existing failure mode, or
3. initialize a new failure-mode candidate

After that, prompts are discarded.

- **No replay**
- **No lookup**
- **No audit trail**

This is not a limitation — it is OCT’s **safety guarantee**.

### OCT Data Lifecycle

#### 1) Pre-classification — *Ephemeral*
- prompt arrives
- model returns one of: `noise | issue | input-error`
- no logging, no embeddings, no persistence

If `noise` → prompt is immediately discarded.

#### 2) Redaction
- runs only for `issue` and `input-error`
- removes identifying and sensitive content
- operates entirely in-memory

#### 3) Failure-Type Classification
- classify into domain-specific failure categories
- produces classification signals only

#### 4) Resolution
- attempt failure-mode match
- similarity + domain + class check

**Branch:**
- match found → update summary
- no match → create new *emerging* failure-mode candidate

#### 5) Persist — *Derived Only*

**What gets stored:**
- failure-mode summaries
- derived trend indicators (or aggregate trend indicators)
- trend states
- confidence metrics

**What never gets stored:**
- raw prompts
- redacted prompts
- embeddings tied to prompts
- per-event logs

Only **derived organizational artifacts** are durable.

### One Crucial Guardrail: Summary Creation Thresholds

Because prompts disappear, summary creation rules must be hardened.

**Required invariant:** a new failure mode may only be created or promoted if it meets a minimum signal threshold.

Example thresholds:
- appears **twice within 7 days**, or
- exceeds similarity confidence **X**

Recommended states:
- `state = emerging` (candidate)
- `state = active` (confirmed)

This prevents:
- one-off curiosity creating permanent artifacts
- “summary spam” from transient signals

### What OCT Produces

OCT outputs **indicators**, not content:

- failure-mode summaries (human-readable)
- trend signals and states
- confidence metrics
- aggregated “where we get stuck” maps

These artifacts are designed to be consumed by:
- documentation owners
- process/workflow designers
- training enablement
- architecture and governance reviews

### What OCT Explicitly Does Not Do

OCT is not:
- a chat transcript archive
- a prompt search engine
- an employee monitoring system
- a replay/logging system
- a data lake of user interactions

OCT stores **patterns**, not people.

### Why This Matters

#### 1) Surveillance Risk Drops to Near Zero
Without prompts:
- no identity reconstruction
- no behavioral replay
- no fishing expeditions

Even with admin access, there is nothing sensitive to inspect.

#### 2) Governance Becomes Simple
You can truthfully say:

> “We do not store prompts. We store indicators.”

#### 3) Retention & Compliance Become Trivial
- no deletion policies needed
- no subject access requests
- no legal hold complications

Summaries are organizational artifacts, not personal data.

#### 4) Engineering Simplicity
- no large indexes
- no vector store growth
- no backfills
- no query tuning

OCT stays lightweight and durable.

### Subtle but Powerful Side Effect

Because summaries are the only durable object:
- documentation work closes failure modes
- training reduces input-error modes
- resolved issues fade out of existence

The organization’s understanding becomes **self-healing**.

### Architecture & Boundaries

- **[ARCHITECTURE.md](ARCHITECTURE.md)** — contracts, invariants, lifecycle rules, anti-patterns
- **[NON_GOALS.md](NON_GOALS.md)** — explicit scope boundaries

These documents are intended to be **normative** for OCT.

### Prompt Contracts (Normative)

OCT’s processing pipeline is defined by a set of **normative prompt contracts**.
These prompts specify behavioral guarantees and invariants, not implementation details.

Located in `./ai/`:

- `prompt-preclassify-scaffolding.md` — ephemeral pre-classification (`noise | issue | input-error`)
- `prompt-redaction-scaffolding.md` — in-memory sanitization and redaction
- `prompt-failure-type-classify-scaffolding.md` — post-redaction failure-type classification
- `prompt-summary-update-scaffolding.md` — constrained update of existing failure-mode summaries
- `prompt-summary-create-scaffolding.md` — creation of new emerging failure-mode summaries

These files are **normative**. Any OCT-compliant implementation MUST honor their constraints and invariants.

### Contributing

We welcome contributions to expand and improve the Organizational Cognitive Telemetry project. If you’re interested, please check out the **[contributing guidelines](./CONTRIBUTING.md)** for more information.

### Contact

- **Author:** William Shostak (https://github.com/wshostak)

### License

This project is licensed under the **ISC License** — see the **[LICENSE](./LICENSE.txt)** file for more details.

Copyright (c) 2025 William Shostak
