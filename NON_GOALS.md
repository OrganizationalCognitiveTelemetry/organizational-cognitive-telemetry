# NON_GOALS — Organizational Cognitive Telemetry (OCT)

This document lists **explicit non-goals** for OCT.
Anything listed here is intentionally out of scope.

## OCT Is Not

- A chat transcript archive
- A document repository
- A data lake
- A logging or monitoring replacement
- A compliance replay system
- An employee surveillance tool
- A user behavior analytics platform
- A permission or ACL system
- A retrieval or search engine
- A workflow executor
- A reasoning or planning engine

## OCT Will Not

- Store raw or unredacted prompts
- Store personally identifiable information
- Track individual user activity over time
- Enable identity reconstruction
- Provide minute-by-minute activity timelines
- Be used for performance evaluation
- Replace operational audit logs
- Make access control decisions

## Design Guardrail

If a proposed feature requires:
- identities,
- raw content,
- enforcement logic,
- replay capability,
- or user-level metrics

then it does **not** belong in OCT.

## Invariant

> OCT prioritizes insight over control and patterns over people.
