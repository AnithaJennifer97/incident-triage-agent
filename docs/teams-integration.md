# Microsoft Teams Integration
This document describes how the Incident Triage Agent is used through **Microsoft Teams** as its primary interaction surface.
Teams is treated as a **conversational interface**, not an automation or remediation platform.

---
## Why Microsoft Teams
In many organizations, Microsoft Teams is:
- The primary on‑call communication channel
- Where incidents are discussed in real time
- Where logs and error messages are shared informally
Integrating the agent into Teams allows engineers to perform incident triage **without leaving the conversation**.

---
## Interaction Model
1. An engineer posts a log, error message, or failure description in a Teams channel or thread.
2. The Incident Triage Agent processes the user‑provided input.
3. The agent responds in the same thread with either:
   - A full structured triage (known error), or
   - A single clarifying question (unknown error).
The entire interaction remains visible to the team.

---
## Message Characteristics
Agent responses in Teams are designed to be:
- Concise and scannable
- Clearly structured
- Easy to share or quote
- Suitable for high‑pressure incident situations
The strict response format ensures consistency across incidents.

---
## Human‑in‑the‑Loop by Design
The agent:
- Does not execute commands
- Does not modify systems
- Does not trigger remediation
- Does not escalate automatically
All decisions and actions remain with human engineers. Teams acts as a **decision support surface**, not a control plane.

---
## Benefits During Incidents
Using the agent in Teams helps:
- Reduce back‑and‑forth clarification
- Standardize incident understanding
- Improve handover between engineers
- Assist junior engineers during on‑call rotations
- Reduce cognitive load under pressure

---
## Scope and Limitations
This project documents **behavior and interaction design only**.
It does not include:
- Bot registration details
- Webhook or API configuration
- Authentication or authorization setup
- Production deployment instructions
These details are intentionally excluded from this repository.

---
## Summary
Microsoft Teams provides a natural, collaborative environment for incident triage.
By embedding a controlled, safety‑aware agent into the conversation,teams can improve incident response quality without introducing automation risk.
