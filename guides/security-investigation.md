# Security Investigation for Software Bugs

Security bugs should be investigated differently from ordinary functional bugs.

A small failure can expose sensitive data, bypass authorization, or allow an attacker to influence system behavior.

## 1. Identify the Security Boundary

Start by determining what the affected component is allowed to access.

Ask:

- What data can this component read?
- What actions can it perform?
- Which users or services can invoke it?
- What authentication is required?
- What authorization checks should exist?
- What external systems does it trust?

The goal is to understand the intended security boundary before investigating how it was violated.

## 2. Reproduce the Behavior Safely

Confirm the issue in a controlled environment.

Record:

- The request or action that triggers the behavior
- Required authentication state
- User roles and permissions
- Relevant inputs
- Expected behavior
- Actual behavior

Prefer minimal test cases that demonstrate the problem without exposing real user data.

## 3. Trace Untrusted Input

Follow user-controlled or externally controlled data through the system.

Typical flow:

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
