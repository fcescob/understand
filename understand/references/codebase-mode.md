# Codebase mode

For a real system or change: a bug, feature, PR, subsystem, incident, or an area to onboard into. The test is operational: can the learner trace the path, predict the branch, explain the invariant, and say what breaks? Record the repo's absolute path in the state file so later sessions and reviews can reopen the code.

## Roadmap

For a change (a bug, feature, PR, or incident), one stage each, in order:

1. **The problem**: what was wrong or missing, and why it mattered (users, correctness, latency, money, safety); the old behaviour, its branches and failure paths. Ask "why?" until you reach the root cause rather than the symptom.
2. **The solution**: what the code does now, mechanism and business logic; why this design over the alternatives, under which constraints; the edge cases it handles and the ones it deliberately leaves.
3. **The blast radius**: what depends on it downstream, what could regress, and what you would watch or test.

For onboarding with no single change, the stages follow the main request path instead: entry point, core data flow, the branches that matter, and where it fails.

## Make behaviour visible

The code is the ground truth, so the learner watches it run:

- Trace from a real entry point through data flow and branches to outputs, with file:line references, and draw the path as a sequence or flow diagram.
- Predict-first on code: the learner says what a function returns or which branch fires before you show it.
- Settle each prediction with a test, a log line, a debugger value, or a small reproduction.
- For a bug or regression, the learner predicts the input that triggers it, and why.

## Additions to the bar

- Trace the path cold, saying what each step does and why.
- State each branch condition and what the branch is for.
- Predict the effect of a nearby change ("remove this guard: what breaks?").
- Name a downstream impact.
- Defend the design, or give a credible alternative and its trade-off.

The teach-back is a cold re-trace of the path, with the why at each step.
