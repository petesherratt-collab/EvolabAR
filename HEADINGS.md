# Headings

Append-only. Each review scores the previous prediction before writing a new heading.

## H-001 · 2026-11-17

**Previous prediction:** none (first review).

**Heading:** Interpretation. Joint work is gated on EvoLab's next generator version. Until a development run shows tasks hard enough to leave headroom, no cross-line experiment has anything to measure. The Router is closed and contributes constraints (S-02, S-05), not new results.

**Basis:** D-0005, D-0006, D-0007, D-0008; S-04, S-05, S-06.

**Confidence:** Medium. EvoLab's development results explicitly recommend a new generator version before evaluation. Peter could still authorise evaluation on causal-1.0 or move EvoLab elsewhere.

**Prediction:** By the next review, EvoLab commits a new generator version identifier (successor to `causal-1.0`) with an evidence-budget rule derived mechanically from each task's minimum sufficient cost.

**What would change it:** EvoLab generates an evaluation seed for causal-1.0 without a new version, or the Router opens a successor question under its reopening conditions.

## H-002 · 2026-11-18

**Previous prediction (H-001):** EvoLab commits a successor to causal-1.0 with a budget derived mechanically from minimum sufficient cost. **Scored HIT, but invalid as a test.** causal-1.1 (2026-11-12) set each budget to the minimum sufficient cost plus a frozen 2/3/4-unit reserve. That was committed before H-001 was written, which happened because the first review read only `main`. The heading was right about EvoLab and wrong about the Router: it said the Router would stay quiet, and the Router reopened on 2026-11-15.

**Heading:** Interpretation. Both lines have adopted a code-only floor (S-07). The joint work is moving towards one question: where does reading by a model beat a program written by someone who knows the format? The Router has measured part of the answer on prose (S-08). EvoLab has shown its current task text gives models nothing to do beyond what a script does. EvoLab's own question, whether communication beats a strong single agent, is at risk of being reframed in Router terms (see BALANCE in STATUS).

**Basis:** D-0009, D-0010, D-0011, D-0012, D-0013; S-07, S-08, S-09, S-10.

**Confidence:** Medium. Both repos' latest handoff and results documents name this as the next step. One session produced both code-only arms, so the convergence partly reflects a single direction of work, not two independent lines arriving at it.

**Prediction:** By the next review, EvoLab commits a generator version whose acceptance audit rejects tasks that `scripted_code`, or a stronger script, already solves.

**What would change it:** EvoLab pays for another development run on a generator that has not been checked against `scripted_code`. Or the Router's next work moves away from reading steps, for example to cheaper learning rosters only.
