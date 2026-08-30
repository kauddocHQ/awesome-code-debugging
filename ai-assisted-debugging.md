# AI-Assisted Debugging

AI can be useful in debugging, but only if you treat it as a reasoning aid rather than a source of truth.

## What AI Is Good At

- Summarizing large logs
- Suggesting hypotheses
- Spotting patterns across stack traces or files
- Generating candidate repro steps
- Drafting test cases
- Explaining unfamiliar code paths
- Proposing alternative interpretations of a failure

## What AI Is Not Good At

- Knowing the hidden state of your system
- Replacing reproduction
- Verifying runtime behavior on its own
- Making security judgments without evidence
- Guessing the right fix from a partial description

## Good Usage Pattern

Use AI to accelerate the workflow you would already use:

1. Give it the observed symptom
2. Provide the relevant evidence
3. Ask for plausible hypotheses
4. Ask what evidence would confirm or reject each one
5. Test the best hypotheses yourself

## Prompting for Debugging

Useful prompts are specific and bounded.

Good:

- "Here is the stack trace and the relevant code path. What are the most likely causes, ordered by evidence?"
- "Compare these two logs and identify the smallest difference that could explain the failure."
- "Given this input and output, what invariants might be broken?"

Weak:

- "Why is this broken?"
- "Fix my app"
- "What is the bug?"

## Validate Every Claim

Treat AI output as a hypothesis generator.

Before using a suggestion:

- Check it against the code
- Check it against runtime evidence
- Check it against the reproduction
- Confirm it does not conflict with known facts

If the suggestion is wrong, discard it quickly and move on.

## Use AI for Explanation, Not Authority

One of AI's best uses is to help you explain a bug clearly after you have already identified it.

It can help draft:

- A root-cause summary
- A test plan
- A regression note
- A postmortem section

But the final explanation should still reflect your verified evidence.

## Security Caution

Use extra care when a bug may involve:

- Authentication
- Authorization
- Data leakage
- Secrets
- Access control

Do not let AI normalize unsafe assumptions. If the issue may be security-related, verify the behavior directly and document the evidence precisely.

## Practical Rule

If AI does not help you form a testable hypothesis within a minute or two, stop using it and return to the system under investigation.
