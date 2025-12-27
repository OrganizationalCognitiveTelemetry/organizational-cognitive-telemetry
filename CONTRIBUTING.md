# Contributing to Organizational Cognitive Telemetry (OCT)

Thank you for your interest in contributing to **OCT — Organizational Cognitive Telemetry**.

This document explains how to contribute to OCT’s **taxonomy, schemas, and conceptual documentation**. OCT is an insight and telemetry system focused on **organizational cognition**, not content storage or system execution.

Contributions should respect OCT’s role as an **observational and classificatory layer**.

## How to Contribute

1. Fork the repository and clone it locally.
2. Create a feature branch:

   ```bash
   git checkout -b feature-name
   ```

3. Make changes with **clear intent and minimal scope**.
4. Ensure changes align with OCT design principles (sanitization, least retention, insight over surveillance).
5. Commit with a descriptive message:

   ```bash
   git commit -m "Refine OCT taxonomy / schema / documentation"
   ```

6. Push your branch and open a pull request.

## Scope Guidelines

OCT is **observational and interpretive**, not operational.

Valid contributions include:
- telemetry taxonomies (e.g., noise, friction, input error, design gap)
- event and metadata schema definitions
- classification rules and thresholds
- documentation and conceptual clarifications
- reporting and insight concepts
- sanitization and retention guidelines

OCT does **not**:
- store raw or sensitive content
- define system permissions or ACLs
- perform retrieval or reasoning
- execute workflows or actions
- replace operational logging systems

Contributions that blur these boundaries will not be accepted.

## Reporting Issues

When reporting issues:
- Specify whether the issue relates to:
  - taxonomy
  - schema
  - documentation
  - classification logic
- Describe the **observed pattern or ambiguity**, not individual usage
- Do not include real prompt content or sensitive data

Issues should focus on **organizational insight quality**, not system bugs.

## Submitting Changes

When submitting changes:
- Keep classifications deterministic and explainable
- Avoid identity-based or user-level tracking
- Preserve OCT’s sanitization guarantees
- Document *why* a change improves insight quality
- Reference related issues or design discussions when applicable

Changes should improve **clarity, correctness, and usefulness of telemetry**, not increase data volume.

## Community

OCT is an open project focused on:
- organizational understanding
- cognitive clarity
- trustworthy AI systems
- insight without surveillance

Contributions should reflect these values.

Thank you for helping improve how organizations learn from AI usage.
