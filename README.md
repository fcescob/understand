# understand: a mastery-gated tutor skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Agent Skill](https://img.shields.io/badge/Agent%20Skill-d97757)

`/understand` is an agent skill that tutors someone to **deep, durable,
transferable understanding** of a topic or a real codebase. It is portable: any
agent host that supports `SKILL.md` frontmatter and bundled files can run it.

It won't advance until the learner can predict, explain, derive when appropriate,
and transfer the idea. It elicits the learner's current model, teaches in small
chunks with predict -> explain -> test -> revise, quizzes with misconceptions as
distractors, repairs the mental model, grounds the idea in real code or data, and
ends with from-memory retrieval plus a spaced schedule. Sessions persist: state
lives in `tmp/learning/<topic>.md`, and resuming a topic starts with the due
retrieval questions before any new material. It also knows when to stop: say
"stop", "no tutoring", or "no more questions" and it will.

It works in two modes, often both in one session:

- **Topic / concept**: algorithms, papers, theorems, math, domains, mechanisms.
- **Codebase / PR / bug**: trace a real system from entry point to data flow to
  branches, using code, tests, logs, or a debugger to make behavior visible.

## Install

`/understand` is just `SKILL.md` plus the `references/` it points to, so it works
with any agent host that loads skills from a directory.

The quickest way is [`npx skills`](https://github.com/vercel-labs/skills):

```bash
npx skills add fcescob/understand -g   # globally, for every project
npx skills add fcescob/understand      # into the current project only
```

You can also install by hand: copy or clone this repo into the directory your
host scans for skills, keeping `SKILL.md` and `references/` together.

## Use

Invoke it with `/understand`, or describe the intent. It should trigger on
requests like *"help me understand X"*, *"teach me X so it sticks"*, *"walk me
through how X works"*, *"make sure I really understand Z before I change it"*, or
*"onboard me to this service by tracing the code"*.

It stays out of the way for quick lookups, one-line answers, summaries,
code-writing, bug fixes, PR reviews, and prose editing. Once a session is
running, you stay in control: say "stop", "no tutoring", or "no more questions"
and it drops the gating.

## What's inside

- `SKILL.md`: concise trigger-facing dispatcher and non-negotiable contract.
- `references/session-loop.md`: detailed tutoring loop.
- `references/topic-mode.md`: topic/concept teaching mode.
- `references/codebase-mode.md`: codebase/PR/bug comprehension mode.
- `references/learning_state_template.md`: template for the per-topic
  `tmp/learning/<topic-slug>.md` state file.

## License

[MIT](LICENSE).
