# ARCHITECTURE — Organizational Cognitive Telemetry (OCT)

This document describes **what OCT is**, **how it fits**, and **what responsibilities it owns**.
It is intentionally implementation-agnostic.

## Purpose

OCT exists to make **organizational cognition observable**.

It captures sanitized signals from AI interactions so patterns of confusion, friction, and knowledge gaps can be identified and addressed.

OCT is not responsible for answering questions, retrieving data, or enforcing permissions.

## What Feeds OCT

OCT receives telemetry **after** upstream processing has already occurred.

Typical inputs include:
- sanitized user prompts
- classification metadata (noise, friction, input error, design gap)
- topic or ontology tags
- correlation identifiers
- date information (no timestamps)

All inputs:
- are already permission-checked
- are already sanitized
- contain no direct identifiers

## What OCT Records

OCT records **ordered, sanitized interaction signals**, including:
- redacted prompt text
- sequence position
- date stamp
- classification labels
- non-identifying references

OCT does not store:
- raw prompts
- user identities
- document contents
- credentials or secrets
- precise timestamps

## What OCT Emits

OCT produces **insight artifacts**, not operational outputs.

Typical outputs include:
- aggregated usage patterns
- recurring confusion signals
- documentation gap indicators
- workflow friction trends

These outputs are consumed by:
- reporting systems
- system designers
- documentation owners
- leadership review processes

## Security Boundary

OCT does not expand access.

- It inherits upstream access decisions.
- It cannot retrieve data.
- It cannot widen visibility.
- It cannot be queried for raw content.

Security is a prerequisite, not a feature.

## Architectural Invariant

> OCT observes organizational cognition.
> It does not participate in decision-making, enforcement, or execution.
