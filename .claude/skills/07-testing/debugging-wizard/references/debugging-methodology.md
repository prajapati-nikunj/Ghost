# Debugging Methodology

## The Scientific Method for Bugs
1. **Observe**: What exactly is the symptom? (Error message, wrong output, crash)
2. **Hypothesize**: What could cause this? (List 3 possible causes)
3. **Predict**: If hypothesis X is correct, what else should be true?
4. **Test**: Write the smallest test that isolates the issue.
5. **Conclude**: Fix + write a regression test.

## Binary Search Debugging
When you can't find the source of a bug:
1. Identify the last known working state (git commit, version).
2. `git bisect start` → `git bisect good <commit>` → `git bisect bad HEAD`.
3. Git narrows down the exact commit that introduced the bug.

## Common Anti-Patterns
| Anti-Pattern | Better Approach |
|---|---|
| Changing random things | Form a hypothesis first |
| Print everywhere | Use debugger or structured logging |
| Fixing symptoms | Find root cause |
| Not writing a regression test | **Always** add a test for the bug |

## Rubber Duck Protocol
When stuck for > 15 minutes:
1. Explain the problem out loud (or in writing).
2. State what you **expect** to happen.
3. State what **actually** happens.
4. The gap between 2 and 3 is your investigation target.
