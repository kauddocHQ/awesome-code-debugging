# Debugging Checklist

Use this checklist when a bug has just been reported and the first priority is to avoid wasted motion.

## Before You Change Code

- Write down the symptom in one sentence
- Record the exact environment
- Capture the failing input, request, or command
- Confirm whether the problem is deterministic
- Identify the last known good state
- Note whether the issue is new, intermittent, or long-standing
- Preserve logs, screenshots, stack traces, and request IDs

## Fast Triage Questions

- Is the failure reproducible on demand?
- Does it happen for every user or only specific accounts?
- Does it depend on browser, device, OS, region, or build version?
- Is the failure tied to a particular input shape or data set?
- Is the symptom in the UI, API, worker, database, or integration boundary?
- Did the problem appear after a deployment, config change, dependency upgrade, or data migration?

## Narrow the Scope

- Reproduce with the smallest possible input
- Remove optional components until the failure disappears
- Compare successful and failing runs
- Check whether the issue exists in a clean environment
- Compare current behavior with previous releases or branches

## Evidence To Collect

- Exact error messages
- Stack traces
- Logs around the failure window
- Network requests and responses
- Relevant database rows or queued jobs
- Configuration values that affect the code path
- Timing information if the bug is intermittent

## What To Avoid

- Changing multiple things at once
- Guessing based on a similar past bug
- Deleting logs or caches before collecting evidence
- Assuming the root cause is where the failure is observed
- Fixing the symptom without understanding the underlying mechanism

## When You Have a Likely Cause

- Prove it with a targeted experiment
- Add a regression test
- Confirm the fix does not break adjacent behavior
- Check whether the same pattern exists elsewhere
- Document the cause and the correction

## Exit Criteria

You are not done when the bug is merely hidden. You are done when:

- The failure is understood
- The fix is verified
- The regression path is covered
- The explanation is written clearly enough that another developer can follow it
