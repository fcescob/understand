# understand: a mastery-gated tutor skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Agent Skill](https://img.shields.io/badge/Agent%20Skill-d97757)

`/understand` tutors you on a topic, a paper, or a real codebase until you can explain it, predict it, and use it somewhere new, then brings it back on a schedule so you still can weeks later. Nothing counts as learned on fluency: a stage passes in the session only when you meet the bar cold, and it counts as retained only when you pass it again on a later day.

## Invoke it

You start it; the agent never reaches for it on its own.

| Host | Command |
|---|---|
| Claude Code | `/understand <topic>` |
| oh-my-pi | `/skill:understand <topic>` |
| Codex | `$understand <topic>` |

With no topic, it runs whatever reviews are due. Say "stop", "no tutoring", or "just tell me" at any point and it drops the gating.

It works in two modes, often both in one session:

- **Topic**: algorithms, papers, theorems, math, domains, mechanisms.
- **Codebase**: a system, PR, bug, or incident, traced from entry point through data flow and branches, with tests, logs, or a debugger making the behaviour visible.

## A session

1. **Reviews first.** Anything due comes back cold, as a new variant of the question, across all your topics.
2. **Placement.** Your goal, your time, your current explanation, and 1-3 diagnostic questions. It places you by what you produce, not by a self-rating.
3. **Chunks.** One idea at a time: you predict before each reveal, then answer a check that also revisits an earlier idea. Every answer carries a 1-5 confidence, so lucky guesses and confident errors show up.
4. **The bar.** A stage passes when you can explain it, give an example and a near miss, name a misconception, and transfer it to a new context.
5. **Teach-back.** You explain the whole topic back, it corrects you, and each stage goes on a review ladder of 1, 3, 7, 21, and 60 days.

## State and reminders

Each topic has one file in `~/.understand/`, so reviews and resumed sessions work from any directory. A host that restricts writes to the project directory asks before the first write there. Because the skill never starts by itself, it offers an `.ics` reminder for the next due date, or the review queue as a CSV deck for Anki.

Upgrading from a version that wrote `tmp/learning/<topic>.md`: move those files into `~/.understand/`.

## Why it works this way

- Retrieval practice and spaced practice are the two techniques rated high-utility in a review of ten common study techniques ([Dunlosky et al. 2013](https://doi.org/10.1177/1529100612453266)).
- Reviews run out to 60 days because the best gap grows with how long you want to remember: for a year, roughly 5-10% of it ([Cepeda et al. 2008](https://doi.org/10.1111/j.1467-9280.2008.02209.x)). Spaced relearning sessions are what make it last ([Rawson & Dunlosky 2011](https://doi.org/10.1037/a0023956)).
- A pass in the session is only "fresh": performance right after teaching is an unreliable sign of learning ([Soderstrom & Bjork 2015](https://doi.org/10.1177/1745691615569000)).
- Confidence ratings matter because accurate self-judgment predicts retention ([Dunlosky & Rawson 2012](https://doi.org/10.1016/j.learninstruc.2011.08.003)), and errors made with high confidence are the most correctable ([Butterfield & Metcalfe 2001](https://doi.org/10.1037/0278-7393.27.6.1491)).
- Placement uses diagnostic questions because self-assessment tracks real skill poorly ([Dunning et al. 2004](https://doi.org/10.1111/j.1529-1006.2004.00018.x)), and the first move depends on it: a worked example first for novices ([Kalyuga et al. 2003](https://doi.org/10.1207/S15326985EP3801_4)), an attempt first when you can make one ([Sinha & Kapur 2021](https://doi.org/10.3102/00346543211019105)).
- Hints come before answers because students who leaned on an unguarded AI did worse once it was taken away ([Bastani et al. 2025](https://doi.org/10.1073/pnas.2422633122)).
- Claims are grounded in code, a computation, or a source because AI tutors state wrong answers confidently; the AI tutor that beat in-class active learning in a Harvard RCT was given step-by-step solutions for that reason ([Kestin et al. 2025](https://doi.org/10.1038/s41598-025-97652-6)).

## It's working if

- Every session ends with your own teach-back, and the state file shows your next review date.
- Reviews feel effortful, and the log shows cold passes at 21 and 60 days.
- Confident errors get rarer from one review to the next.

## Install

```bash
npx skills add fcescob/understand -g   # globally, for every project
npx skills add fcescob/understand      # into the current project only
```

Or copy the `understand/` folder into the directory your host scans for skills.

User-only invocation comes from `disable-model-invocation: true` in the frontmatter (Claude Code, oh-my-pi) and `policy.allow_implicit_invocation: false` in `agents/openai.yaml` (Codex). claude.ai uploads and the Skills API accept only the Agent Skills spec's frontmatter fields, so they reject this skill.

## What's inside

- `understand/SKILL.md`: the session steps, grading, review ladder, hints, and stop signals.
- `understand/references/topic-mode.md`: roadmap, representations, and derivations for ideas.
- `understand/references/codebase-mode.md`: roadmap and tracing for real systems and changes.
- `understand/references/learning_state_template.md`: the per-topic state file.
- `understand/agents/openai.yaml`: Codex picker metadata and the explicit-only policy.

## License

[MIT](LICENSE).
