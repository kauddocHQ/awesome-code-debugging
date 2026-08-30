# Security Investigation for Software Bugs

Security bugs require a different investigation mindset than ordinary functional defects.

A small mistake can expose sensitive data, bypass authorization, corrupt system state, or let an attacker influence behavior in ways the original design never intended.

The goal is not merely to prove that something breaks. The goal is to understand the security boundary that failed and how to restore it.

## 1. Identify the Security Boundary

Start by defining what the component is allowed to do.

Ask:

- What data can this component read?
- What data can it modify?
- Who can call it?
- What authentication is required?
- What authorization checks should exist?
- Which roles are allowed?
- Which external systems does it trust?
- What secrets, tokens, or credentials are in scope?
- What resources would be sensitive if exposed?

Map the expected boundary explicitly:

```text
Actor
  ↓
Authentication
  ↓
Authorization
  ↓
Application Logic
  ↓
Resource Access
  ↓
Sensitive Data / External System
```

The investigation should identify which layer failed and whether the failure was due to missing checks, incorrect assumptions, or a broken trust relationship.

## 2. Reproduce Safely

Reproduce the issue in a controlled environment and avoid using real user data unless that is unavoidable.

Record:

- Exact request or action
- Authentication state
- Role or account type
- Relevant headers, tokens, or cookies
- Input payloads
- Expected behavior
- Actual behavior

Use a minimal reproduction. The smaller the test case, the easier it is to reason about the security boundary.

## 3. Trace Untrusted Input

Follow attacker-controlled or user-controlled data through the system:

```text
Untrusted Input
      ↓
Parsing
      ↓
Validation
      ↓
Transformation
      ↓
Business Logic
      ↓
Database / External Service
      ↓
Output
```

At each step, ask:

- Is the data validated?
- Is it normalized before use?
- Are trust boundaries crossed?
- Does the system assume the data came from a safe source?
- Does the code preserve the original meaning of the input?

## 4. Look for Broken Assumptions

Security defects often come from assumptions that are true in normal operation but false under adversarial conditions.

Common examples:

- The client will only send valid values
- The user interface will prevent bad input
- A hidden field cannot be modified
- A previous check makes a later check unnecessary
- A token is always bound to the right identity
- A cached object still reflects current authorization
- A redirect target is safe because it came from the application

If a defense depends on the client behaving correctly, treat it as suspect.

## 5. Check Authorization at Every Meaningful Boundary

Authorization problems often hide in one of these forms:

- Missing checks on a new endpoint
- Object-level access control failures
- Role checks applied too late
- Checks performed on one identifier while another one is used for the action
- Access decisions based on stale or cached state
- Privilege escalation through indirect object references

Verify:

- Which identity is being used
- Which object or resource is being accessed
- Whether the check matches the actual resource
- Whether the logic is race-safe
- Whether alternate paths bypass the check

## 6. Evaluate Impact Carefully

Consider the realistic impact, not just the technical flaw.

Ask:

- What data could be exposed?
- What actions could be performed?
- Could a lower-privileged user access higher-privileged data?
- Could the issue affect other tenants, customers, or systems?
- Could an attacker persist access or escalate privileges?
- Is the problem local to one account, or systemic?

## 7. Fix the Root Weakness

Security fixes should strengthen the control, not just patch a single path.

Good fixes usually include:

- Server-side validation
- Explicit authorization checks
- Canonicalization before comparison
- Safer default behavior
- Safer output encoding
- Stronger separation of trust domains
- Regression tests for the attack path

Avoid fixes that only block one observed payload while leaving the underlying flaw intact.

## 8. Add Defense in Depth

Even when one layer should be sufficient, add supporting controls where practical:

- Input validation
- Output encoding
- Least privilege
- Scoped credentials
- Rate limiting
- Logging and alerting
- Audit trails
- Secure defaults

Defense in depth matters because security bugs often survive through a single broken assumption.

## 9. Preserve Evidence

Before modifying state, capture:

- Request IDs
- Timestamps
- Relevant logs
- Authorization context
- Failing payloads
- Data samples, if safe to retain

This helps with incident review, remediation, and future hardening.

## 10. Document the Investigation

Write down:

- What the issue was
- What boundary failed
- How it was reproduced
- What the impact could have been
- What the fix changed
- What tests or controls now prevent recurrence

The objective is not simply to close the bug.

The objective is to make the system harder to break in the same way again.
