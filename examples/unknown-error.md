# Example — Unknown or Vague Error
This example demonstrates how the Incident Triage Agent behaves when the input does not contain enough information to safely perform incident analysis.
In this scenario, the agent must not speculate and must ask exactly one clarifying question, then stop.

---
**EXAMPLE**

## User Input  (First Message)
Application failed during startup

## Decision Gate Outcome
- The input does **not** match any known error pattern
- The information provided is insufficient for triage
- The agent must enter **Clarification Mode**

---

## Agent Response
What platform is this running on (Kubernetes, VM, or CI/CD pipeline)?
(Since given input is not clear agents resposnds with anotehr clarity question)

## Important Constraints Demonstrated
- Only **one sentence** is returned
- The sentence is a **direct question**
- No explanation, reasoning, or guidance is provided
- No severity, ownership, or fixes are mentioned

---
## Why This Matters
This behavior prevents:
- Incorrect assumptions
- Unsafe recommendations
- False confidence during incidents
By requiring sufficient input before analysis, the agent maintains trust, safety, and predictable behavior under pressure.






