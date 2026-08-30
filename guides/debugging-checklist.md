# Debugging Checklist

A practical checklist for investigating software bugs systematically instead of guessing at fixes.

## 1. Reproduce the Problem

Before changing code, make sure the failure can be reproduced.

- What exact action triggers the problem?
- Does it happen every time?
- What inputs are required?
- Does it happen locally, in staging, or only in production?
- Can you reproduce it with a smaller test case?

If the issue cannot be reproduced, collect logs, traces, and environment details before making changes.

## 2. Read the Error Carefully

Start with the actual error rather than immediately trying a fix.

Check:

- Error type
- Error message
- Stack trace
- File and line number
- Request or operation that failed
- Relevant input values
- Recent changes

The line where an error appears is not always where the underlying problem originated.

## 3. Find the Origin of the Failure

Trace the execution path backward.

Ask:

- Where did the failing value come from?
- Which function created it?
- Which component called the failing function?
- Was the value transformed before reaching the failure?
- Where was the first unexpected state introduced?

The goal is to find the **first incorrect state**, not merely the final crash.

## 4. Trace Data Flow

Follow important values through the system.

For each value, identify:

```text
Input
  ↓
Validation
  ↓
Transformation
  ↓
Business Logic
  ↓
Storage / External Service
  ↓
Output
