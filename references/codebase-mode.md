# Codebase / PR / bug mode

Use when the object of understanding is a real system or change: a bug, a
feature, a PR, a subsystem, an incident, an area someone is onboarding into. The
truth test here is *operational* — can the learner trace the path, predict the
branch, explain the invariant, and say what breaks?

## The three things they must understand

Drive the session toward all three, gating mastery on each:

1. **The problem & why it existed**
   - What was wrong or missing? Why did it matter (users, correctness, latency, money, safety)?
   - What was the old behavior? What were the branches / cases / failure paths?
   - Drill into *why* repeatedly — surface the real root cause, not the surface symptom.

2. **The solution & why it was done this way**
   - What does the new code do, mechanism and business logic?
   - Why this design over the alternatives? What were the trade-offs and constraints?
   - What are the edge cases the solution handles (and any it deliberately doesn't)?

3. **The broader context & blast radius**
   - What does this change touch downstream? What relies on it?
   - What could regress? What would you watch or test?

## How to make behavior visible

Don't just describe the code — make the learner *see it run*:

- Trace from a real **entry point** → data flow → branches → outputs. Use real file:line references.
- **Show the actual code.** Have the learner predict what a function returns or which branch fires *before* you reveal it.
- Use the **debugger, tests, or logs** to confirm behavior against their prediction — this is the codebase analogue of "test" in predict-explain-test-revise. A failing/ passing test or a breakpoint value is the reality check that repairs a wrong model.
- For a regression or bug, have them predict what input triggers it and why.

## Mastery checks for code

A stage passes when the learner can, unaided:

- Trace the relevant path and name what each step does and why.
- Explain the branch conditions and what each branch is for.
- Predict the effect of a nearby change ("if we removed this guard, what breaks?").
- Name an edge case and a downstream impact.
- Defend the design decision, or articulate a credible alternative and its trade-off.

End with retrieval: have them re-trace the path and re-explain the why from
memory, then log a spaced-retrieval queue and the next concrete step.
