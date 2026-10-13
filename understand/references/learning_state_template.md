# State file format

One file per topic at `~/.understand/<topic-slug>.md`. Keep it terse: it is the instrument later sessions read. Reviews read the queue and the reference model; a resumed session reads the roadmap and the log.

````markdown
# <Topic or code area>

- Mode: topic | codebase (repo: <absolute path>)
- Goal: <what the learner wants to do with it>
- Time: <per-session budget>
- Placement: <what they showed they already know; where teaching started>

## Roadmap
- Stage 1: <one-line goal> (not started | learning | fresh | retained)
- Stage 2: ...

## Reference model
<The compact correct model you grade against: mechanism, key examples, near misses, boundaries, sources. Codebase: the traced path with file:line.>

## Misconceptions
| Misconception | Evidence it was wrong | Repaired |
|---|---|---|

## Log
| Date | Item | Question | Result | Confidence |
|---|---|---|---|---|

## Review queue
| Item | Rung (days) | Due | Last result |
|---|---|---|---|
| Stage 1: <idea> | 1 | <YYYY-MM-DD> | |
| Teach-back | 1 | <YYYY-MM-DD> | |

## Next step
<smallest concrete next action>
````

Result is PASS, PARTIAL, or FAIL, with "lucky guess" or "confident error" added where it applies. Keep every log row: pass rates per rung are how anyone can tell whether the learning lasts.
