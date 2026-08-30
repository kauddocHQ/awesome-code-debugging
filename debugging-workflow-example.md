# Debugging Workflow Example

This example shows how the guides fit together in practice.

## Situation

A user reports that saving a profile intermittently fails after a recent release.

## Step 1: Reproduce

Confirm:

- Which account types are affected
- Whether the bug happens in staging and production
- Whether it depends on a specific browser or input

## Step 2: Narrow the Problem

Compare a successful save with a failed save.

Collect:

- Network request payloads
- Response status codes
- Server logs
- Database writes
- Any validation errors

## Step 3: Find the Boundary

Ask whether the issue is in:

- Form validation
- API validation
- Authentication or authorization
- Persistence
- A downstream service

## Step 4: Test a Hypothesis

Suppose the failure only happens when a display name contains trailing spaces.

Test:

- Trim the input and retry
- Submit a short name
- Submit the same name from an API client

If the failure disappears only after trimming, the root cause is likely inconsistent normalization between layers.

## Step 5: Fix and Verify

Possible fix:

- Normalize the value on the server
- Add a regression test
- Add a validation message if needed
- Confirm the same issue cannot occur through another path

## Step 6: Record the Result

Write a short summary:

- What failed
- Why it failed
- How it was fixed
- What test now prevents recurrence

This makes the debugging session useful to the next developer who encounters a similar issue.
