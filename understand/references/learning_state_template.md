# Learning-state file — template

One file per topic at `tmp/learning/<topic-slug>.md`, so sessions on different
topics don't collide. Copy this structure into the working file and update it
after every gated stage. Keep it terse; it's a progress instrument, not prose.
Delete rows that don't apply (e.g. the evidence map for a non-empirical topic).

On resume, the Retrieval Queue and Mastery Log are read first — keep them
accurate.

```markdown
# <Topic / codebase area>

## Learner Profile
- Level: ELI5 / ELI14 / ELII / expert
- Goal: intuition / apply / exam / research / teach / decide
- Background: <relevant prerequisites they already have>
- Time: <budget>

## Session Goal (the mastery checklist for THIS session)
- [ ] Can state what it is and why it matters
- [ ] Can explain the mechanism / business logic in own words
- [ ] Can handle the key edge cases / branches
- [ ] Can apply it to a new case + name a failure mode
- [ ] (codebase) Understands the problem, why it existed, the old behavior, the fix, and the blast radius

## Roadmap (small, gated chunks)
- [ ] Stage 0: elicit current mental model
- [ ] Stage 1 (prereq): ...
- [ ] Stage 2: ...
- [ ] Stage N: transfer / failure modes

## Current Mental Model
- Learner's current explanation:
- Tutor's refinement:
- Confidence: Low / Medium / High

## Concept / Mechanism Map
| Concept or Step | Depends on / Why it happens | Example | Non-example / boundary | Often confused with |
|---|---|---|---|---|

## Misconceptions & Repairs
| Misconception | Why it's tempting | Evidence it was wrong | Better model | Verified? |
|---|---|---|---|---|

## Evidence / Source Map (only if empirical / contested)
| Claim | Source or evidence | Strength | Counter-evidence | Confidence |
|---|---|---|---|---|

## Mastery Log
| Stage | Status (PASS/PARTIAL/FAIL) | Evidence (what they demonstrated) | Next action |
|---|---|---|---|

## Retrieval Queue (spaced — answer from memory, no notes)
| Due date | Question | Expected mastery | Result |
|---|---|---|---|
| <today +1 day> | ... | ... | |
| <today +3 days> | ... | ... | |
| <today +7 days> | Teach it back in 6 sentences | full arc | |

## Next Actions
- <smallest concrete next step>
```
