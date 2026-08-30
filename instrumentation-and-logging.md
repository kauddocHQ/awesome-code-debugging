# Instrumentation and Logging

Instrumentation is how you make internal system behavior visible. Logging is one form of instrumentation, but not the only one.

## Principles

- Make the behavior measurable
- Make the output searchable
- Make the data structured where possible
- Keep high-signal events visible
- Avoid logging noise that drowns out the evidence

## What to Log

Log the events that matter to diagnosis:

- Request identifiers
- User or account context where appropriate
- Branching decisions
- Validation failures
- Downstream service calls
- Retry attempts
- State transitions
- Error summaries

## What Not to Log

Avoid logging:

- Secrets
- Full credentials
- Sensitive personal data
- Excessive payloads
- Redundant noise

If data is sensitive, log a safe identifier or a redacted form instead.

## Structured Logging

Structured logs are easier to search and correlate than free-form text.

Prefer fields such as:

- Event name
- Trace ID
- Request ID
- User ID or account ID
- Operation name
- Status
- Duration

## Temporary Instrumentation

When a bug is hard to reproduce, temporary instrumentation may be the fastest way to see what the code is doing.

Use it to capture:

- Branch selection
- Input normalization
- Output derivation
- Cache hits and misses
- Unexpected nulls

Remove temporary instrumentation once the issue is understood unless it provides ongoing value.

## Correlation

The goal is often not a single log line but a chain of evidence.

Correlate by:

- Request ID
- User session
- Job ID
- Trace ID
- Timestamp range

Without correlation, distributed failures are hard to reconstruct.

## Event Design

Good events are:

- Stable
- Informative
- Easy to aggregate
- Consistent across the codebase

If events are too vague, they will not help future investigations.
