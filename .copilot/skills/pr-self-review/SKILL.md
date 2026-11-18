---
name: pr-self-review
description: Critically self-review all changes made for a pull request, prioritizing correctness and simplifying unnecessary complexity without posting review comments.
---

# PR self-review

Use after implementing a pull request's changes, when asked to self-review or clean up the work before handing it back.

## Scope and intent

- Review the complete set of changes made for this PR. Include staged, unstaged, and committed branch changes relative to the PR base as relevant.
- Read surrounding code and project conventions where needed to understand behavior; do not broaden the review into unrelated cleanup.
- Treat correctness and preserving intended behavior as the highest priority. Simplification is valuable only when it remains clear, maintainable, and behavior-preserving.

## Review pass

1. Establish the PR's purpose and inspect the full diff, including all changed files. Trace affected code paths and callers where necessary.
2. Look for defects, regressions, missed edge cases, and compatibility issues before style or cleanup.
3. Critically assess whether each new or changed part is needed:
   - Can logic be made simpler without obscuring intent or changing behavior?
   - Is there redundant, dead, speculative, or over-engineered code?
   - Do comments and documentation explain non-obvious intent or constraints, or merely restate the code?
   - Do tests protect meaningful behavior, or are they redundant, brittle, or testing implementation details? Never remove a test just because it is verbose or inconvenient; preserve meaningful regression coverage.
4. Make small, high-confidence improvements that fit the PR's intent and repository conventions. For uncertain or behavior-changing choices, do not guess: report the tradeoff privately.
5. Run the narrowest relevant tests or checks after edits. Do not claim correctness beyond what the review and checks support.

## Reporting and boundaries

- Report useful findings and any cleanup performed in the conversation, with file and line references where practical. Be concise and distinguish confirmed defects from optional simplifications.
- Do not post GitHub PR review comments, inline comments, approvals, or other public feedback as part of this self-review.
- Do not remove code, comments, documentation, or tests solely to make the diff smaller. Explain why a change is unnecessary and preserve correctness and useful context.
