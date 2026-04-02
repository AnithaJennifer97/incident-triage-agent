# Incident Memory Model
This document explains how the Incident Triage Agent handles **multi‑message incident conversations** using a controlled, conversation‑scoped memory model.
The goal is to support realistic incident workflows without introducing long‑lived or unsafe state.

---
## Conversation‑Scoped Memory
The agent treats the **entire conversation thread** as a single incident unless the user explicitly states: **NEW INCIDENT**
All reasoning, clarification, and analysis is scoped to the current conversation only.

---
## What the Agent Remembers
Within an incident, the agent retains awareness of:
- Logs or error messages already shared
- Answers provided to previous clarifying questions
- Error categories identified so far
- The leading root‑cause hypothesis
- Open questions or uncertainty areas
This memory is **implicit** and used only to guide reasoning. It is never output verbatim.

---
## How Memory Influences Behavior
### Avoiding Repeated Questions
If the agent has already asked a clarifying question and received an answer, it will not ask the same question again.

---

### Incremental Evidence Handling
When new logs or symptoms are provided:
- The agent incorporates them into the existing incident context
- Earlier hypotheses may be refined or replaced
- The agent references earlier evidence when relevant

Example:
- Initial log indicates `OOMKilled`
- Later message mentions database timeouts
- The agent connects the two instead of restarting analysis

---
### Handling Conflicting Evidence
If new input materially conflicts with earlier evidence:
- The agent asks **exactly ONE** clarifying question
- The response stops after the question
- No analysis is performed until the conflict is resolved

---
## Resetting Incident Context
The agent **resets memory immediately** if:
- The user explicitly says “new incident”
- A clearly unrelated service or system is introduced

When reset:
- All previous context is ignored
- The agent treats the input as a fresh incident

---

## Memory Constraints
To maintain safety and clarity:
- Recent and specific logs take precedence over older, vague input
- Stale assumptions are discarded if contradicted
- The agent briefly explains why its hypothesis has changed (when applicable)
Memory is **not persistent across conversations** and is intentionally bounded.

---

## Why This Design Matters
Real incidents evolve over time.Engineers paste logs incrementally, not all at once.This memory model ensures the agent:
- Feels context‑aware
- Remains predictable and safe
- Avoids circular questioning
- Mirrors real on‑call investigation patterns
At the same time, it avoids the risks of global or long‑term memory.
