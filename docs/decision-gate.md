# Decision Gate — Known vs Unknown Errors
The Decision Gate is the **central control mechanism** of the Incident Triage Agent.
Its purpose is to determine whether the agent should:
- Perform full incident triage immediately, or
- Pause and request clarification from the user
This gate is mandatory for every input the agent receives.

---

## Why a Decision Gate Is Necessary
Incident response often starts with incomplete or ambiguous information. Uncontrolled analysis in such situations can lead to:
- Incorrect assumptions
- Misleading guidance
- Loss of trust in automation
The Decision Gate ensures the agent **never overreaches** when context is missing.

---

## Classification Outcomes

Every input is classified into exactly one of the following:
### A) Known Error Pattern
The input clearly matches a recognized failure pattern.

Examples:
- `CrashLoopBackOff`
- `OOMKilled`
- `ImagePullBackOff`
- `Terraform apply failed`
- `mvn test failed`

When a known pattern is detected:
- No clarifying questions are allowed
- The agent must produce a full triage response
- The strict response format is enforced

---

### B) Unknown or Vague Error
The input does not provide enough concrete information to safely triage.

Examples:
- “Application failed during startup”
- “Service is not working”
- “Something broke after deploy”

When the error is unknown or vague:
- The agent must ask **exactly ONE** clarifying question
- The question must be the **only output**
- The agent must stop after asking the question

---

## Pattern Recognition Rules

To reduce false negatives, pattern matching follows these rules:
- Case-insensitive matching
- Partial matches are allowed
- Strong resemblance is treated as a match

This allows flexible handling
