# Response Contract — Structured Output Enforcement
This document explains the strict response contract enforced by the Incident Triage Agent and why this design is essential for safe and effective incident response.

---

## What Is the Response Contract?
When sufficient input is provided, the agent must respond using exactly the following headings, in this order:
1. Summary
2. Likely Root Cause
3. Possible Fixes
4. Additional Checks
5. Severity & Ownership
6. Owning Team
No additional sections, commentary, or formatting is allowed.

---

## Why a Strict Contract Is Necessary
During incidents, engineers need:
- Fast comprehension
- Predictable structure
- Zero ambiguity
- No hidden recommendations

A free‑form response introduces risk:
- Important details may be buried
- Severity may be unclear
- Ownership may be missed
- Guidance may feel authoritative when it should be advisory
The response contract eliminates these risks.

---

## Purpose of Each Section
Summary
Provides a one‑sentence explanation of what is failing and why it matters.This is optimized for quick scanning during active incidents.

Likely Root Cause
Lists the most probable causes based only on the provided input.This section avoids speculation and unnecessary breadth.

Possible Fixes
Contains 2–4 safe, actionable steps. Fixes are framed as guidance, not commands, and should be low-risk investigations or validations.

Additional Checks
Directs engineers to logs, commands, or dashboards that can confirm or refute the proposed hypothesis.This reinforces a validate‑before‑act mindset.

Severity & Ownership
Explicitly states:
- The inferred incident severity
- Whether the severity is assumed
- The rationale for ownership
This prevents silent severity inflation or underestimation.

Owning Team
Names the single team most likely responsible for next action. This reduces delay caused by ownership ambiguity.

Safety Benefits of the Contract
The strict response contract ensures:
- Consistent triage across engineers and incidents
- Reduced cognitive load during outages
- Clear separation between analysis and action
- Predictable outputs suitable for enterprise use
Most importantly, it prevents the agent from appearing authoritative or autonomous.

Summary
The response contract turns the agent from a generic chatbot into a reliable incident response assistant.
It prioritizes:
- Clarity over verbosity
- Safety over creativity
- Consistency over flexibility
``
