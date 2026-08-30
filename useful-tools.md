# Useful Tools for Debugging

The best tools are the ones that make hidden behavior visible without distorting it.

## Logs

Logs are the first line of investigation in many systems.

Use logs to:

- Confirm control flow
- Capture unexpected input
- Record decisions
- Correlate events over time

Good logs are structured, searchable, and consistent.

## Debuggers

A debugger is useful when you need to inspect state directly.

Use it to:

- Pause on a failing line
- Inspect variables
- Step through branches
- Verify assumptions about order and mutation

## Traces

Distributed tracing is valuable when a request crosses multiple services.

It helps answer:

- Where did latency accumulate?
- Which service returned the wrong result?
- Which hop introduced the failure?

## Network Inspection

Use request inspection tools when the bug may be in transport, headers, cookies, redirects, caching, or payload shape.

Inspect:

- Request method
- URL
- Query parameters
- Headers
- Status codes
- Response body
- Redirect chains

## Source Control History

Git history can show:

- When the issue began
- Which commit changed behavior
- How the implementation evolved
- Whether the bug came from a refactor, fix, or dependency update

The useful question is not only "what changed?" but "what assumption changed with it?"

## Tests

Tests are not just for verification. They are also a debugging tool.

Add focused tests to:

- Reproduce the bug
- Prove the fix
- Lock in the expected behavior
- Explore edge cases safely

## Profilers and Monitors

Use profilers when the issue may involve:

- Performance regressions
- Hot loops
- Memory growth
- I/O contention

Use monitors when the issue is time-based, intermittent, or load-dependent.

## Data Inspection Tools

For problems involving persistence, inspect:

- Database rows
- Queue entries
- Cache keys
- Object storage artifacts
- Search indexes

## Choose the Simplest Tool That Answers the Question

Do not start with the most complex tool. Start with the tool that can verify your current hypothesis with the least overhead.
