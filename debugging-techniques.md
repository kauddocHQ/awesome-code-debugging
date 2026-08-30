# Debugging Techniques

Different bugs call for different techniques. Good debugging is less about memorizing tricks and more about choosing the right technique for the shape of the failure.

## Start With Reproduction

If you cannot reproduce the issue, you cannot reason about it reliably.

Useful reproduction questions:

- What exact input triggers the failure?
- What environment is required?
- Does the bug happen every time?
- What is the smallest case that still fails?

## Divide and Conquer

Reduce the search space by splitting the problem into smaller parts.

Examples:

- Disable one subsystem at a time
- Compare a working request with a failing one
- Binary-search a large dataset or log window
- Remove optional fields until the bug disappears

This is often the fastest way to isolate the layer that introduced the problem.

## Diff-Based Debugging

Compare a known-good case to a failing one.

Look for differences in:

- Input shape
- Authentication state
- Timing
- Feature flags
- Configuration
- Dependency versions
- Cache state
- Data state

The useful question is not "what is wrong?" but "what changed that matters?"

## Instrument the Code

Add temporary logging or counters when the current observability is not enough.

Good instrumentation:

- Is specific
- Is temporary if appropriate
- Reveals state transitions
- Makes hidden assumptions visible

Avoid noisy logs that produce volume without insight.

## Use Assertions to Surface Invariants

Assertions are useful when a bug may be caused by an impossible state that should not happen.

They can help you detect:

- Broken invariants
- Invalid state transitions
- Unexpected nulls
- Incorrect ordering

Do not leave assertions in production unless that is an intentional policy choice.

## Check Boundaries

Many bugs happen at boundaries:

- Input parsing
- Serialization and deserialization
- Time zones and timestamps
- Network boundaries
- Database boundaries
- Cache boundaries
- Third-party APIs

When you are stuck, inspect the handoff between components rather than only the component itself.

## Suspect State

Stateful systems fail when the current request depends on stale or partially updated state.

Look for:

- Caches
- Sessions
- Background jobs
- Retry logic
- Event ordering
- Shared mutable objects
- Race conditions

State bugs often disappear in single-step tests and show up under concurrency or retries.

## Prove and Disprove

A strong investigation alternates between hypotheses and tests.

For each hypothesis:

1. State the idea clearly
2. Define what would be true if it were correct
3. Run a test or inspect evidence
4. Keep or discard the hypothesis based on the result

This prevents drifting into story-making.

## Common Failure Modes

- Assuming the stack trace is the root cause
- Changing code before understanding the reproduction
- Debugging the symptom in the wrong layer
- Ignoring timing and concurrency
- Treating one successful test as proof

## What a Good Technique Looks Like

A good technique gives you one of these outcomes:

- A smaller reproduction
- A stronger hypothesis
- A clearer boundary
- A falsifiable test
- A direct path to the cause
