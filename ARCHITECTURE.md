# ARCHITECTURE — Organizational Cognitive Telemetry (OCT)

This document defines OCT’s **architectural contracts, invariants, and prohibited behaviors**.
It is intentionally implementation-agnostic.

## Normative Language

- **MUST** — required for OCT compliance
- **SHOULD** — recommended to prevent known failure modes
- **MAY** — optional or context-dependent

## Core Invariant: Prompt Ephemerality

OCT treats prompts as **transient inputs**, not records.

### Ephemerality Requirements (Normative)
- Prompts **MUST NOT** be persisted in any form.
- Redacted prompts **MUST NOT** be stored.
- Prompt-level embeddings **MUST NOT** be retained.
- OCT **MUST NOT** provide replay, lookup, or per-event inspection.
- No system component **MAY** reconstruct a prompt after ingestion.

This invariant is OCT’s primary safety guarantee.

## Conceptual Lifecycle Contract

OCT operates in three conceptual phases:

1. **Ingest (Ephemeral)** → derive classification + similarity signals in a short-lived buffer
2. **Resolution** → match to existing failure modes or initialize an emerging candidate
3. **Persist (Derived Only)** → store summaries and aggregates only

Later phases MUST NOT rely on prompt persistence.

## Responsibilities & Contracts

### 1) Ingest (Ephemeral)
**Purpose:** convert a prompt into non-identifying signals, then discard it

**Inputs:**
- prompt content (transient)
- minimal routing context (domain / source / class)

**Outputs (non-persistent):**
- class label: `noise | issue | input-error`
- similarity vector for matching (ephemeral)

**Contract (Normative):**
- MUST redact identifiers before any persistence or derived artifact creation (and only for non-noise inputs).
- MUST classify the prompt.
- MUST generate similarity signal for matching.
- MUST discard the prompt after resolution.

**Must-Not:**
- MUST NOT write the prompt (raw or redacted) to storage.
- MUST NOT retain embeddings tied to the prompt event.

### 2) Resolution
**Purpose:** match signals to known failure modes

**Contract (Normative):**
- MUST attempt match against existing failure modes.
- SHOULD apply similarity + domain + class checks.
- MUST NOT create durable artifacts from a single unconfirmed event.

**Outputs:**
- update to an existing failure-mode summary, OR
- creation/update of an `emerging` candidate (derived only)

### 3) Persistence (Derived Only)
**Purpose:** store organizational artifacts that cannot be replayed as user content

**What may be persisted (MUST be derived):**
- failure-mode summaries
- rolling window aggregates
- trend states
- confidence metrics

**Contract (Normative):**
- MUST persist only derived artifacts.
- MUST NOT persist prompts, redacted prompts, or prompt-level embeddings.
- SHOULD ensure persisted artifacts are non-identifying and non-replayable.

## Failure-Mode Thresholding (Required Guardrail)

Because prompts are discarded, OCT must harden creation and promotion rules.

**Contract (Normative):**
- New failure modes MUST begin as `state = emerging`.
- Promotion to `state = active` MUST require a minimum signal threshold.

Example thresholds (non-normative):
- ≥2 occurrences within 7 days
- or similarity confidence ≥ X

This prevents summary spam and one-off artifacts.

## Explicit Anti-Patterns

The following violate OCT architecture:

- storing prompts (raw or redacted)
- storing prompt-level embeddings
- providing prompt replay, prompt lookup, or per-event audit trails
- identity-linked telemetry or employee analytics
- using OCT as a logging system

## Architectural Invariant

> OCT observes organizational cognition.  
> It never observes individuals.
