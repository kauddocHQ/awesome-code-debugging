# Awesome Code Debugging

A practical collection of techniques, tools, and workflows for debugging and understanding complex codebases.

## Why this exists

Debugging isn't always about finding the line where something broke.

In large codebases, the difficult part is often understanding:

- Where the problem actually originates
- How data flows through the system
- Which components are affected
- Why the failure happens
- Whether an unrelated change caused the issue

This repository collects practical resources for investigating those problems.

## Contents

- [Debugging Techniques](#debugging-techniques)
- [Codebase Investigation](#codebase-investigation)
- [Root Cause Analysis](#root-cause-analysis)
- [Security Investigation](#security-investigation)
- [Useful Tools](#useful-tools)
- [AI-Assisted Debugging](#ai-assisted-debugging)

## Debugging Techniques

### Start With Reproduction

Before changing code, make the failure reproducible.

A reliable reproduction gives you:

1. A known starting state
2. A predictable failure
3. A way to verify whether a fix actually works

### Follow the Data

When debugging complex behavior, trace the data instead of guessing.

Ask:

- Where is the data created?
- Where is it transformed?
- Where is it validated?
- Where is it stored?
- Where does the unexpected value first appear?

### Find the First Incorrect State

The visible error is often not the root cause.

```text
Observed failure
      ↓
Previous state
      ↓
Earlier transformation
      ↓
First incorrect state
      ↓
Root cause
