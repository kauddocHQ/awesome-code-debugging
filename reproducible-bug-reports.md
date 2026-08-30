# Reproducible Bug Reports

A useful bug report is one that another developer can act on without guessing.

## Minimum Contents

Include:

- Clear summary
- Environment
- Exact steps to reproduce
- Expected behavior
- Actual behavior
- Frequency
- Error messages or screenshots
- Relevant inputs or sample data

## Good Reproduction Steps

Reproduction steps should be:

- Ordered
- Specific
- Minimal
- Repeatable
- Free of implied knowledge

Example format:

1. Open the app in a clean session
2. Sign in as a user with read-only access
3. Navigate to the billing page
4. Enter the provided test input
5. Click submit
6. Observe the failure

## Helpful Context

Add context such as:

- Whether the issue is new
- Whether it began after a deploy
- Whether it is intermittent
- Whether it depends on browser or device
- Whether it affects one user or many

## Sample Data

When possible, provide:

- A sanitized request payload
- A small data sample
- A request ID
- A failing record identifier

## What Makes Reports Hard To Use

- Vague language
- Missing environment details
- Unclear steps
- Multiple unrelated issues in one report
- No description of expected behavior

## Good Report Example

> Summary: Export fails for users with long filenames.
>
> Environment: Production web app, Chrome 126, macOS 14.
>
> Steps:
> 1. Sign in as a standard user.
> 2. Open the export dialog.
> 3. Use the attached file name.
> 4. Click Export.
>
> Expected: The file exports successfully or the UI shows a validation message.
>
> Actual: The request returns a 500 error and the export never completes.

That level of detail is enough to begin investigation without guesswork.
