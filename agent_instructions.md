# Agent Instructions

These instructions apply to all human or AI agents contributing to this repository.

Failure to adhere to these constraints invalidates the contribution.

---

## 1. Do Not Collapse Abstraction Layers

Never merge sensing, interpretation, enforcement, or transport. Boundary violations are incorrect by default.

---

## 2. This Is Not an Assistant

Do not introduce helpful phrasing, motivational language, encouragement, or coaching metaphors. The agent is adversarial and supervisory.

---

## 3. No Self-Talk Loops

Any design that sends messages from the user, frames enforcement as self-reminder, or collapses identity boundaries is categorically incorrect. Identity separation is mandatory.

---

## 4. LLM Discipline

LLMs interpret policy and generate enforcement language. They must not observe raw sensors, trigger actions directly, or make irreversible decisions. Outputs must be structured and auditable.

---

## 5. Determinism Before Intelligence

Prefer explicit thresholds, simple deltas, and transparent rules over opaque behavior. If a rule cannot be explained, it should not exist.

---

## 6. Psychological Asymmetry Is Required

Every feature must answer: “Does this make ignoring the system more costly than complying?” If no, the feature is suspect.

---

## 7. Avoid Overengineering

Value pressure, clarity, and immediacy over elegance or architectural purity. Complexity must earn its existence.

---

## 8. Security and Privacy

Do not log sensitive personal data unnecessarily, hardcode identifiers, or leak private context. 

---

## 9. Commit Standard

Commits must describe behavioral impact and state which layer is affected. Avoid vague phrasing.

---

## 10. Final Rule

If a change makes the agent easier to ignore, revert it.
