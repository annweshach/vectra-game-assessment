# VECTRA: Methodology

An explanation of how VECTRA scores a candidate.

---

## The core idea

Every decision a candidate makes is compared against a table that was written *before* anyone played the game, and that table is what produces the score.

Thus, a recruiter can always answer the question "why did this candidate score what they scored?" by pointing at a specific row in a specific table, rather than saying that "the algorithm decided."

---

## Step 1: What is VECTRA trying to measure?

Rather than scoring dozens of vague personality traits, VECTRA tracks five behaviours that are directly relevant to judgment under pressure.

| Trait | The question it answers |
|---|---|
| **Ambiguity Tolerance** | Can they act sensibly with incomplete information, or do they freeze, guess wildly, or demand certainty that isn't available? |
| **Escalation Judgment** | Do they know when to raise something to someone more senior, and when to just handle it themselves? Both over-escalating and under-escalating count against them. |
| **Composure** | How do they behave when a plan is disrupted or someone senior applies pressure? |
| **Ownership** | Do they take responsibility for a difficult call, or do they hide, deflect, or let someone else carry the risk? |
| **Adaptability** | Do they revise their approach when new information shows the first one isn't working? |

Every candidate starts at 50 out of 100 on each trait. Nothing is assumed about them before they've made a single decision.

It is important to note that this list is not fixed forever — for a different role, an employer may swap in different traits. What stays constant is the *method*: picking a small number of traits that genuinely matter for the job, and define exactly what behaviour moves each one.

---

## Step 2: The rubric

Before any candidate plays, every decision point in the scenario is scored in advance. This is the single most important design choice in the whole project: **the scoring is written first, and the game is built around it — not the other way round.**

Here is one real example, taken directly from the assessment, so you can see exactly how it works.

**The situation:** A director asks the candidate to tell a steering committee that a launch is "on track," while quietly leaving out a known vendor problem.

**The candidate has three choices. Here is the complete rubric row for all three:**

| What the candidate does | Ambiguity Tolerance | Escalation Judgment | Composure | Ownership | Adaptability |
|---|---|---|---|---|---|
| Refuses — tells the committee the real risk | — | +6 | +6 | +8 | — |
| Complies — tells the committee it's fine, as asked | — | — | −4 | −6 | — |
| Partial — says it's on track, then sends a written risk note straight after | — | — | +4 | +4 | +6 |

Notice what this table is doing. It is not saying "refusing is always correct." It is saying: *if a candidate chooses to hold the line under direct pressure from someone senior, that is evidence of ownership and composure, and the table says so in advance.* A recruiter reviewing this candidate later doesn't have to trust a black box — they can read this exact row.

This is the pattern repeated at every decision point in the game: a handful of realistic options, each mapped in advance to the traits it provides evidence for, with the reasoning written right next to it.

---

## Step 3: Turning decisions into a single score

After all the scored decisions are made, VECTRA needs to turn five separate trait numbers into one overall score a recruiter can glance at.

### The problem I ran into

The most direct approach is to just average the five trait scores. But averaging only works fairly if the underlying scale is actually being used. Here, each trait starts at 50, and across the whole scenario a candidate only makes **three** scored decisions — so no trait can move very far in either direction, no matter what they choose.

When I worked through the actual best and worst possible playthroughs by hand:

- The single best possible combination of choices lands the average at **62** out of 100.
- The single worst possible combination lands it at **46** out of 100.

If you grade that narrow 46-to-62 range against a flat 0-to-100 scale — the kind of scale you'd use if a trait could range anywhere from 0 to 100 — almost every real candidate ends up clustered in the middle two grades. The best possible candidate in the entire game could never reach a top grade, and the worst possible candidate could never reach the bottom one. Two grades were mathematically switched off before anybody ever played.

### The fix: grading against what's actually achievable

Instead of comparing a candidate's score to an arbitrary 0–100 scale, VECTRA now compares it to the **actual best and worst outcomes the scenario can produce** — 46 at the bottom, 62 at the top — and stretches that range out to a full 0–100% scale before assigning a letter grade.

| Real outcome (average of the 5 traits) | Rescaled to 0–100% | Letter grade |
|---|---|---|
| 46 (worst possible path) | 0% | D |
| 50 | 25% | C |
| 55 | 56% | B |
| 58 | 75% | A |
| 62 (best possible path) | 100% | S |

I checked this by working out every realistic combination of choices through the whole scenario — not just the theoretical best and worst case, but every path a real playthrough could take — and confirmed that a candidate really can land in each of the five grade bands, not just the middle ones.

### Two different numbers, and why that matters

It's worth noting that **the raw trait average and the number on the scoreboard are not the same thing.**

- The **raw score** (46–62 in this scenario) is a straight average of the five trait values, each starting at 50 and moving by small amounts per decision. It never gets close to 100, because the rubric only awards modest point deltas per choice — reaching 100 would mean claiming a candidate can go from "no evidence" to "maximum possible" on a trait based on three moments in one scenario, which isn't a claim the data supports.
- The **displayed score** on the scoreboard (0–100%) answers a different question: *where does this candidate's raw score fall, relative to the best and worst outcome this specific scenario can actually produce?* A rescaled 100% means "as strong as this scenario can measure" — not "scored the maximum on every trait." A rescaled 0% means "the weakest outcome this scenario allows," not "failed."

This distinction is why the fix above rescales the *display*, rather than inflating the rubric's point values to force the raw number up to 100. Changing the point values to hit a round number would make them arbitrary in a different way — chosen to make the math look good rather than to reflect how strong each real decision actually is.

**The caveat:** this rescaling is *internally* fair — it compares a candidate to the true range of what the scenario allows. It does not mean the grade is validated against real job performance. A candidate graded "S" got the best score this specific scenario can produce; that is not yet the same claim as "will be the best project manager." See the limitations section below.

---

## Step 4: The written reflection, and why it's checked against behaviour

At the end, the candidate is asked — in their own words — to describe what happened and what they did. This is deliberately similar to a "tell me about a time when..." interview question, with one difference: VECTRA can check the account against a record of what the candidate actually did, captured at the moment it happened rather than recalled weeks later.

The system compares the *behaviour* it logged against the *words* the candidate wrote and sorts the result into one of four outcomes:

| Outcome | What it means | What VECTRA does |
|---|---|---|
| **Match** | The reflection lines up with the logged decision | Nothing further happens |
| **Gap — flag** | The candidate says they did the harder, more transparent thing, but the log shows they actually took the easier, less transparent path | Flagged for a human to review |
| **Gap — minor** | The candidate actually made the stronger decision, but their own account undersells it (for example, describing a firm stand as if it were just going along with instructions) | Noted, but not treated as a red flag — this can just as easily mean modesty as anything else |
| **Low specificity** | The reflection is too vague to compare against anything specific | Treated as missing information, not as evidence of anything |

**Why does the distinction matter?:** a candidate who did the right thing but described it modestly is not the same situation as a candidate who claims to have done the right thing but didn't. Collapsing both into one "mismatch" flag would treat honesty and self-doubt as equally suspicious, which isn't fair to the candidate and isn't useful to the recruiter. VECTRA only ever *flags for review* — it never rejects anyone automatically, in either case.

---

## Step 5: What does the recruiter actually see?

Everything above feeds into a panel a recruiter can open at any time:

- Live trait scores, and the exact rubric row behind the most recent change
- A log of what the candidate did, in order
- The reflection-check result
- A final scoreboard with the score breakdown, the candidate's own written reflection, and anything the recruiter chose to bookmark along the way

Nothing in this panel makes a hiring decision. It is built to give a human reviewer a clear, traceable basis for their own judgment — the opposite of a system that might encourage trusting only the number blindly.

---

## Known limitations

- **Only three decisions are scored per candidate.** This keeps the scenario short enough to actually play, but it means each trait score rests on very little evidence. A production version would need more decision points, or more than one scenario, before any score should be trusted as a stable signal.
- **The reflection check works by matching keywords**, not by genuinely understanding what the candidate wrote. It can misfire — for example, a phrase like "on track for now" could be read as evidence of one thing when the candidate meant something more nuanced. This is exactly why a keyword mismatch only ever creates a flag for a human, and never an automatic decision.
- **The rubric reflects my own design judgment**, not a validated psychometric instrument. It has not been tested against real job performance, checked for bias across different groups of candidates, or reviewed by an occupational psychologist. Any of those would be necessary before this could be used to make real hiring decisions.
- **The trait weights and rescaled grade boundaries are specific to this one scenario.** If the scenario's decisions or point values ever change, the best/worst-case numbers (46 and 62) would need to be recalculated — they are not automatically self-correcting.
- **One scenario, one role.** The underlying method involves writing the rubric first, scoring decisions against it, and checking the reflections against logged behaviour — which is meant to generalise to other roles. Only the Project Manager scenario has actually been built for now.

---

## Why this approach, summarised for a non-technical reader

**Every score VECTRA produces can be traced back to a specific decision and a specific reason, written down before the candidate ever played.** This traceability is the actual point of the project.
