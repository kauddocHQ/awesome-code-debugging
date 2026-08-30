# Root-Cause Analysis for Bugs

Root-cause analysis is the discipline of moving from observed behavior to the smallest underlying cause that explains it.

The point is not to produce a clever theory. The point is to produce a cause that is:

- Specific
- Observable
- Testable
- Actionable
- Useful for preventing recurrence

## Symptom, Cause, and Trigger

These are not the same thing:

- A symptom is what the user sees
- A trigger is what causes the behavior to happen now
- A root cause is the underlying defect that makes the system vulnerable to that trigger

Example:

- Symptom: a page returns a 500 error
- Trigger: a request contains a missing field
- Root cause: the server assumes the field exists and dereferences it without validation

## Start From the Evidence

Begin with concrete facts:

- Stack traces
- Logs
- Input values
- Deployment history
- Configuration state
- Data samples
- Timing patterns

Avoid starting with a fix. Start with what can be verified.

## Trace Backwards

A practical sequence:

1. Identify the failing assertion, exception, or incorrect output
2. Locate the exact code path that produced it
3. Determine what inputs reached that path
4. Find where those inputs were created or modified
5. Ask which assumption was violated
6. Ask why the assumption was not enforced earlier

This often reveals whether the defect is in:

- Input validation
- State management
- Concurrency
- Error handling
- Data modeling
- Boundary conditions
- Integration contracts

## Useful Questions

- What must be true for this failure to occur?
- What changed between working and broken states?
- Is the bad state persistent or transient?
- Would the failure disappear if one precondition changed?
- Is there a missing invariant?
- Is the system relying on undocumented behavior?
- Is the cause local, or is it inherited from a previous step in the pipeline?

## Common Root-Cause Patterns

- Null or missing data was not handled
- A stale cache or stale object was trusted
- A race condition exposed an invalid intermediate state
- A configuration default differed from the expected one
- A dependency changed behavior
- A boundary check was off by one
- Error handling swallowed the real failure
- A schema or contract changed without a matching code update

## The Five Whys, Used Carefully

The Five Whys can help, but only when each answer is based on evidence.

Poor use:

- Why did it fail? Because the code broke.
- Why did the code break? Because it was buggy.

Better use:

- Why did the request fail? Because the service dereferenced a missing value.
- Why was the value missing? Because one producer stopped including it.
- Why did the consumer accept that state? Because validation was missing.
- Why was validation missing? Because the contract was implicit.
- Why was the contract implicit? Because the field was added without updating the interface documentation and tests.

## Validate the Cause

Before closing the investigation, ask:

- Can I reproduce the failure by recreating only the suspected cause?
- Does fixing the cause eliminate the failure reliably?
- Does the explanation account for all observed facts?
- Is there a simpler cause that fits the evidence better?

## Deliverable

A good root-cause summary should say:

- What happened
- Where it happened
- Why it happened
- What made it visible
- How the bug was fixed
- How the recurrence risk will be reduced
