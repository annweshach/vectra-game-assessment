## Design decisions

Three things I changed after testing:

- **Removed a timed decision.** A countdown made the data noisier: a careful thinker and a panicked guesser looked the same once the clock ran out.
- **Split the reflection check into two signals.** A mismatch between what someone did and what they wrote could mean misrepresentation, or it could mean modesty. Those shouldn't be flagged the same way.
- **Rescaled the scoreboard grade.** With only three scored decisions, the best possible score a candidate could ever reach was 62 out of 100, and the worst was 46 — so the top and bottom grades were mathematically impossible before anyone played. I fixed this by grading each candidate against the scenario's actual best and worst possible outcome, rather than an arbitrary 0–100 scale that the scenario could never fill.

The full reasoning behind all three, including a worked example of a rubric row, is in [`docs/methodology.md`](docs/methodology.md).
