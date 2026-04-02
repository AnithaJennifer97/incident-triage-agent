# Severity and Ownership Model
This document describes how the Incident Triage Agent determines incident severity and ownership based solely on user‑provided input.
The goal is to enable faster triage decisions while avoiding unsafe assumptions or silent escalation.

---

## Severity Levels
The agent classifies incidents using four severity levels:

### P1 — Critical
- Customer‑facing outages
- SLA breaches
- Widespread production failures
- Severe business impact (e.g., payments, checkout)
These incidents typically require immediate response and escalation.

---

### P2 — High
- Partial service degradation
- Limited blast radius
- Impacted subset of users or regions
- Production issues without total outage

---

### P3 — Medium
- Non‑blocking failures
- CI/CD build or deployment issues
- Pre‑production failures
- Issues not yet affecting users

---

### P4 — Low
- Informational alerts
- Low‑impact or transient issues
- No immediate risk to service availability

---

## Conservative Severity Selection

When full impact cannot be confidently inferred from the input, the agent deliberately chooses the safer higher severity.
(e.g., P2 instead of P3).

In such cases, the agent explicitly states:
> “Impact assumed based on pattern; verify.”

This prevents underestimating incidents due to incomplete context.

---

## Keyword‑Based Escalation
The agent increases severity by one level if the input contain any high‑risk keywords, including:

- production
- customer‑facing
- checkout
- payments
- outage
- region‑wide
- 5xx spike
- SLA breach
The reason for escalation is always stated explicitly in the output.

---

## Ownership Assignment
Ownership is inferred using simple, transparent category mapping:

| Error Category        | Default Owning Team        |
|----------------------|----------------------------|
| Kubernetes / AKS     | Platform or SRE Team        |
| Application Errors   | Application Team            |
| CI/CD Failures       | DevOps or Build Team        |
| Infrastructure       | Infrastructure Team         |
| Networking           | Network Team                |

The model prioritizes **clarity over perfection** to reduce delays in incident handoff.

---

## Why Ownership Is Explicit

During incidents, unclear ownership leads to:
- Slower response times
- Repeated handoffs
- On‑call confusion
By explicitly stating ownership, the agent helps engineers take decisive next steps without guessing responsibility.

---

## Design Philosophy
Severity and ownership logic is intentionally:
- Simple
- Explainable
- Conservative
- Easy to override by humans
The agent provides guidance, not authority. Final decisions remain with the responding engineers.

---

## Summary
The severity and ownership model reinforces safe incident response by:
- Preventing silent under‑classification
- Making escalation reasons explicit
- Reducing coordination overhead
- Supporting consistent triage behavior
