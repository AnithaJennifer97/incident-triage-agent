# Example — Known Error Pattern (CrashLoopBackOff)

This example demonstrates how the Incident Triage Agent behaves when the input clearly matches a **known error pattern**.

In this case, the agent must:
- Perform full triage immediately
- Ask no clarifying questions
- Follow the strict response format

---
**EXAMPLE**

## User Input

CrashLoopBackOff: Back-off restarting failed container

## Agent Response

Summary:
The container is repeatedly crashing and restarting, indicating that the application cannot start successfully inside the pod. (Category: Kubernetes)

Likely Root Cause:
- Application startup failure due to misconfiguration or missing dependencies
- Unhandled exception causing the container process to exit
- Incorrect environment variables or secrets

Possible Fixes:
- Review container startup logs to identify the exact failure reason
- Validate required environment variables and secrets are present
- Confirm the container image version is compatible with the deployment configuration

Additional Checks:
- `kubectl logs <pod-name> --previous`
- `kubectl describe pod <pod-name>`
- Review recent configuration or image changes

Severity & Ownership:
- Severity: P2 (Impact inferred based on service crash; verify if customer-facing)
- Ownership rationale: Platform-level Kubernetes runtime issue

Owning Team:
- Platform / SRE Team
