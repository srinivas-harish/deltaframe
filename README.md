# Overview

This repository implements an externalized supervisory agent designed to detect behavioral drift by continuously comparing observed state against declared intent, and to enforce corrective action through asymmetric psychological pressure.

This system is not:
- a productivity app
- a reminder service
- a personal assistant
- a quantified-self dashboard

It is a control system.

The agent operates as an independent evaluator with its own identity, authority boundary, and enforcement channel. Its role is adversarial rather than cooperative.

---

## Core Problem Statement

Humans are unreliable self-reporters.

When intent (calendar, commitments, declared goals) diverges from behavior (location, usage, inactivity), internal reminders fail due to symmetry and habituation.

This system exists to:
1. Observe reality
2. Compute deviation
3. Apply asymmetric pressure
4. Close the loop without user initiation

The agent is designed to be harder to ignore than compliance.

---

## System Model

The architecture is intentionally minimal and layered:

[ Sensors ] → [ State Aggregation ] → [ Drift Evaluation ] → [ Enforcement ]

Each layer has strict responsibility boundaries.

---

## Layer Definitions

### 1. Sensors (Ground Truth Only)

Sensors emit facts, not interpretations.

Examples:
- GPS / geofence state
- Calendar blocks (current and upcoming)
- Phone usage by app or category
- Time-of-day
- Motion or inactivity windows

Example snapshot:
{
  "timestamp": "14:38",
  "location": "home",
  "calendar_now": "Deep Work",
  "calendar_next": "Gym",
  "usage_last_90m": {
    "youtube": 62,
    "browser": 18
  }
}

Sensors do not judge, infer intent, escalate, or message the user.

---

### 2. State Aggregation

This layer unifies raw sensor data into a coherent world-state.

Responsibilities:
- normalize heterogeneous inputs
- derive expected versus actual state
- compute deltas (time, location, usage)
- produce deterministic summaries

Example:
{
  "expected_state": "focused_work",
  "actual_state": "stationary_entertainment",
  "violations": ["location", "usage", "time"]
}

No language generation occurs here.

---

### 3. Drift Evaluation (Policy Interpretation)

This is the only layer that invokes an LLM.

Input:
- aggregated state
- recent history
- upcoming commitments
- invariant definitions (e.g. leverage, gradient, scale)

Output:
{
  "drift": "high",
  "urgency": 0.84,
  "enforcement_level": "immediate"
}

LLMs are used as policy interpreters, not observers and not decision-makers. Model choice is abstracted and API-based.

---

### 4. Enforcement (The Agent)

The enforcement layer owns identity, tone, escalation, and memory.

It communicates through an external channel, never as the user.

Properties:
- asymmetric
- adversarial
- stateful
- interruptive

Example output:
“It’s 14:38. You logged 2 hours of deep work today. You’ve been in bed for 47 minutes scrolling X. This is drift. Move.”

---

## Design Constraints (Non-Negotiable)

- No local LLMs; API-only intelligence
- Identity separation; no self-talk
- Phone-first sensing
- Low ceremony; no user initiation required
- Explicit uncertainty; ambiguous states are labeled

---

## Intended Evolution

- escalation curves for repeated violations
- temporal chaining of justifications
- pre-commitment enforcement
- multi-channel enforcement

---

## Philosophical Position

This agent is not meant to be liked.

It exists to remove the user’s ability to lie to themselves by automating judgment, making drift legible, and attaching immediate consequence.

If a feature weakens that function, it does not belong here.
