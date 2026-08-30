# Awesome Code Debugging

Practical guides for diagnosing bugs, tracing root causes, investigating security issues, and building a disciplined debugging workflow.

This repository is organized as a small reference library. Each guide is written to be useful on its own, but the set is designed to work together:

- Start with the debugging checklist when you first encounter a bug
- Use root-cause analysis to move from symptoms to causes
- Use the security investigation guide when the issue may involve auth, data exposure, or trust boundaries
- Reach for the techniques guide when you need a structured approach
- Use the tools guide to choose the right observability and inspection tools
- Use the AI-assisted debugging guide to get value from AI without trusting it blindly

## Repository Layout

- [checklists/debugging-checklist.md](checklists/debugging-checklist.md)
- [guides/root-cause-analysis.md](guides/root-cause-analysis.md)
- [guides/security-investigation.md](guides/security-investigation.md)
- [guides/debugging-techniques.md](guides/debugging-techniques.md)
- [guides/useful-tools.md](guides/useful-tools.md)
- [guides/ai-assisted-debugging.md](guides/ai-assisted-debugging.md)
- [guides/instrumentation-and-logging.md](guides/instrumentation-and-logging.md)
- [guides/reproducible-bug-reports.md](guides/reproducible-bug-reports.md)
- [examples/debugging-workflow-example.md](examples/debugging-workflow-example.md)
- [tools/debugging-tool-selection.md](tools/debugging-tool-selection.md)

## What This Repository Is For

The goal is to help developers debug more effectively in real projects. The focus is on:

- Finding the smallest reliable reproduction
- Distinguishing symptoms from causes
- Avoiding guesswork
- Preserving evidence before changing code
- Understanding when a bug is actually a security issue
- Using AI as an assistant, not as an authority

## How To Use It

If you are in the middle of an incident or a bug hunt, use this order:

1. Capture the symptom and the exact reproduction steps
2. Check the checklist for fast, high-value questions
3. Narrow the failure domain
4. Gather logs, traces, input data, and relevant history
5. Prove the cause with one or two controlled experiments
6. Fix the underlying defect
7. Add a regression test or a durable safeguard

## Core Principles

- Reproduce before you edit
- Change one variable at a time
- Prefer evidence over intuition
- Keep notes while you investigate
- Fix the cause, not just the current manifestation
- Treat security-sensitive bugs with extra caution

## Suggested Reading Order

If you want the shortest path through the repository:

1. [checklists/debugging-checklist.md](checklists/debugging-checklist.md)
2. [guides/root-cause-analysis.md](guides/root-cause-analysis.md)
3. [guides/debugging-techniques.md](guides/debugging-techniques.md)
4. [guides/instrumentation-and-logging.md](guides/instrumentation-and-logging.md)
5. [guides/security-investigation.md](guides/security-investigation.md)
6. [guides/ai-assisted-debugging.md](guides/ai-assisted-debugging.md)

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
