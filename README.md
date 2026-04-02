# Incident Triage Agent 🚨🤖
A prompt‑driven **Log Explainer and Incident Triage Agent** designed for DevOps and SRE users to quickly understand failures, identify likely root causes, and receive safe, actionable guidance directly via Microsoft Teams.

This repository showcases the instruction design, decision logic, and controlled response behavior of the agent. It is a learning and portfolio project, not a production monitoring or alerting system.

---
# Purpose
Incident response often starts with fragmented inputs: log snippets, error messages, or half‑formed failure descriptions.
This agent is designed to:
- Reduce cognitive load during incidents
- Enforce consistent triage behavior
- Prevent over‑assumption when information is incomplete
- Provide structured, repeatable incident analysis

The agent **does not ingest signals automatically**.  All analysis is based **only on user‑provided input**.

---
# What This Agent Does
Given a log line, error message, stack trace, or CI/CD failure output,the agent:
1. Explains the issue in clear, beginner‑friendly technical language
2. Identifies the most likely root cause (based only on provided input)
3. Suggests 2–4 safe and actionable fixes
4. Recommends additional checks for validation
5. Classifies severity and identifies the owning team
6. Responds in a strict, structured format
The agent is intentionally read‑only and advisory.

---
# Decision Gate (Core Design)
Every user input passes through a **mandatory decision gate**:

- *Known Error Pattern*
  - The agent provides full triage immediately
  - No clarifying questions are allowed

- *Unknown or Vague Error*
  - The agent asks exactly ONE clarifying question
  - The question is the only output
  - The agent stops after the question
This prevents hallucination and uncontrolled guidance.

---
# Supported Error Categories
The agent recognizes common failure patterns across:
- *Kubernetes / AKS*
  - CrashLoopBackOff
  - ImagePullBackOff
  - OOMKilled
  - Liveness / Readiness probe failures

- *Applications*
  - Startup failures
  - Datasource initialization errors
  - Cache or database connectivity issues
  - Unhandled exceptions (e.g., NullPointerException)

- *CI/CD*
  - Build failures
  - Test failures
  - Deployment or Helm upgrade failures
  - Terraform plan/apply errors

Pattern matching is case‑insensitive and allows partial or close matches.

---
# Response Contract (Strict)
When sufficient input is provided, the agent must  respond using the following headings, in this exact order:
1.Summary
2.Likely Root Cause
3.Possible Fixes
4.Additional Checks
5.Severity & Ownership
6.Owning Team
No extra sections, commentary, or formatting is allowed.This strict contract ensures consistency during high‑pressure incidents.

---
# Safety & Guardrails
The agent enforces multiple guardrails:
- Never assumes missing context
- Never provides remediation scripts or commands to execute blindly
- Escalates severity conservatively when impact is unclear
- Limits clarifying questions to one
- Avoids repetition across multi‑message incidents
**All recommendations are advisory, not prescriptive.**

---
# Incident Memory (Conversation‑Scoped)
Within a conversation:
- The agent treats all messages as part of a single incident
- Prior logs and answers are remembered
- Repeated clarifying questions are avoided
- Hypotheses may evolve as new evidence appears
Context is reset only when the user explicitly states **“new incident”**.

---
# Microsoft Teams Integration
Microsoft Teams is used as the interaction surface for this agent.
Engineers can paste logs or errors directly into a Teams channel and receive structured triage responses in the same thread, reducing context switching during active incidents.

---
# What This Repository Includes
- The full system instructions used to define agent behavior
- Decision gate and response format documentation
- Severity and ownership classification logic
- Example interactions for:
  - Known error patterns
  - Unknown errors requiring clarification
  - Multi‑message incidents using memory

---
# Disclaimer
This project is a **personal technical showcase** , (It is live and used by my current SRE Team) .It does not contain proprietary systems, internal data, or production integrations.  All examples are generalized and intended for learning and demonstration purposes only.
