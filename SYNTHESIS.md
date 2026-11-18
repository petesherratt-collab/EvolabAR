# Synthesis: EvoLab × Adaptive Router

Reflects the commits in `sources.lock` (main plus active work branches in each
repo, from the 2026-11-18 review).
Every entry cites committed files. Observed results, deterministic derivations
and interpretations are kept separate. Interpretations are marked.

## 1. Shared method

### S-01 · Models propose; deterministic code decides; no LLM judge
Both lines give models a proposal role only and leave scoring, acceptance and
authority to deterministic code. Neither uses a model-based grader.
- `evolab@111c4f4:README.md` ("The local model is a proposal generator. Deterministic code owns…")
- `evolab@111c4f4:COLLECTIVE_INTELLIGENCE_B0_PROTOCOL.md` §4.1, §13
- `Adaptive_Router@06f1d55:BUILD_HISTORY.md` Standing rule 10; "Core methodological principle"
- Decision: D-0001

### S-02 · Output conformance is not semantic correctness
Both lines found that a correctly shaped output can still be wrong. EvoLab
requests strict JSON Schema output, but its local semantic checks stay
authoritative. The Router's contracts catch format and type failures but admit
same-typed wrong values.
- `evolab@111c4f4:COLLECTIVE_INTELLIGENCE_B0_PROTOCOL.md` amendment 0.1-C
- `Adaptive_Router@06f1d55:RESEARCH_ENDPOINT_2026-09-22.md` "What remains useful"; `README.md` "Explicit runtime requests"
- Decision: D-0002

### S-03 · Prospective freezes, preserved failures, no silent reruns
Both lines freeze rules before generation, keep failed and invalid attempts with
their cost, and treat negative results as results. Retries get new identities.
- `evolab@111c4f4:COLLECTIVE_INTELLIGENCE_B0_PROTOCOL.md` §12.5, amendments 0.1-E, 0.1-F; `collective_runs/DEVELOPMENT_RESULTS_20261111.md`
- `Adaptive_Router@06f1d55:RESEARCH_ENDPOINT_2026-09-22.md` "Conditions for reopening"; `BUILD_HISTORY.md` Standing rules 1, 16
- Decision: D-0003

### S-07 · A model condition must beat a code-only floor
Both lines now run a condition with no model: a program written by someone who
knows the task format, seeing only what the agents see. EvoLab states the rule
directly: a model condition is worth its compute only where it beats this
program.
Observed (EvoLab, causal-1.0 development split only): `scripted_code` reached
Brier loss 0 on all nine tasks at exactly the minimum sufficient cost. No model
condition beat it on any task.
Observed (Router, planned jobs V3, 8 shapes, 160 jobs): keyword rules frozen
before the texts existed read 148/160 texts correctly. Models reading the same
jobs (ceiling arm D) read 160/160. The planning router beat code-only on
correctness (+6.3 points, interval +1.3 to +11.3). The plain whole-task race did
not clear zero (+4.4, interval −0.6 to +9.4). Code-only was about 10,000 times
faster.
Provenance: both arms came from one work session (branch `ccr-23487558-3yzwx4`
in both repos), following a suggestion made in the hub conversation on
2026-11-17. The hub is not an independent witness for this entry.
- `evolab@ac36da7:CODE_ONLY_CONDITION_AMENDMENT_0_1_G.md`; `collective_runs/SCRIPTED_DEVELOPMENT_RESULTS_20261117.md`
- `Adaptive_Router@dcecd34:README.md` "Planned jobs V3"; `FAST_PATH_PLANNED_V3_PLAN.md`; `code_only_v1_scores.json`
- Decision: D-0009

## 2. Connections

### S-04 · EvoLab supplies a task family with a mechanically exact answer
`causal-1.0` generates fictional fault-isolation tasks whose correct answer and
evidence-conditioned posterior are computed by an exact oracle, without model
judgment. The generator is frozen and passed a 225-task offline audit and
public-view leakage probes. For this task family, a successor Router question
could state the "completely specified bounded correctness claim" its reopening
conditions require.
Boundary: this is a validator for EvoLab's synthetic domain only. It does not
supply a semantic validator for the Router's own workloads (structured JSON,
labels, bullets).
Interpretation: the nearer Router analogue is the paused verifiable-witness
design (`d2174f1`), which also separates finding an answer from checking it.
- `evolab@111c4f4:COLLECTIVE_INTELLIGENCE_B0_PROTOCOL.md` amendments 0.1-D, 0.1-E; `collective_runs/CAUSAL_GENERATOR_AUDIT_DEV.md`
- `Adaptive_Router@06f1d55:RESEARCH_ENDPOINT_2026-09-22.md` "Conditions for reopening"
- `Adaptive_Router@d2174f1:VERIFIABLE_WITNESS_ROUTING_V1_PLAN.md`
- Decisions: D-0004 (original framing rejected), D-0005

### S-08 · The Router's unseen-text method is a ready-made gate for EvoLab's next generator
Observed (EvoLab): in causal-1.0 the evidence text is templated and names the
candidate groups outright. EvoLab's own recommendation is that the next
generator fail any task `scripted_code` (or a stronger script) already solves,
using varied wording, mappings that must be inferred and noisy channels.
Observed (Router): on prose written by a model outside the roster and
hand-checked, frozen keyword rules failed on complaints with no complaint word,
places missing from their lists, negations and meetings described only by
subject. Models did not fail on these texts.
Interpretation: the Router's V3 procedure is a working protocol for that EvoLab
gate. Freeze the script before the text exists, have an out-of-roster model write
the text, then hand-check it. Its failure list shows which text features defeat
a template reader. Whether the same features defeat a script that has to *buy*
evidence, as opposed to reading prose, is untested.
- `evolab@ac36da7:collective_runs/SCRIPTED_DEVELOPMENT_RESULTS_20261117.md` "Reading"
- `Adaptive_Router@dcecd34:README.md` "Planned jobs V3"; `FAST_PATH_PLANNED_V3_PLAN.md`
- Decision: D-0011

## 3. Tensions

### S-05 · Router requires a deterministic baseline; B0 has none — CONTESTED (2026-11-18)
Observed: the Router's reopening conditions require a deterministic baseline
arm, and any model-search role must survive comparison with ordinary
deterministic code. B0's four conditions are all model-backed (§9). No
deterministic acquisition policy is defined.
Observed: EvoLab's oracle computes exact candidate posteriors from any purchased
evidence set.
Interpretation: a deterministic policy that buys evidence along the oracle's
minimum sufficient path would likely reach near-zero loss on `causal-1.0`
tasks. This is not a defect in B0, whose question is collective versus single
agent. But any joint experiment run in EvoLab's arena must include such an arm,
or it cannot satisfy the Router's conditions.
- `Adaptive_Router@06f1d55:RESEARCH_ENDPOINT_2026-09-22.md` "Conditions for reopening"
- `evolab@111c4f4:COLLECTIVE_INTELLIGENCE_B0_PROTOCOL.md` §9; amendment 0.1-D
- Decision: D-0006

**New evidence (2026-11-18), contesting the claim above.** EvoLab amendment
0.1-G adds a deterministic condition, `scripted_code`, for development use. It
sits beside B0 and leaves the frozen files untouched. It reached loss 0 at
minimum cost on all nine causal-1.0 development tasks, so the interpretation
above is now observed. B0's frozen four-condition evaluation configuration
still has no deterministic arm, and `scripted_code` has not been run on the
causal-1.1 to 1.5 task sets.
Awaiting Peter: retire S-05 into S-07, or revise it to "B0's frozen evaluation
configuration has no deterministic arm".
- `evolab@ac36da7:CODE_ONLY_CONDITION_AMENDMENT_0_1_G.md`; `collective_runs/SCRIPTED_DEVELOPMENT_RESULTS_20261117.md`
- Decision: D-0010

### S-09 · Model agreement: a reliable label in the Router, the weakest condition in EvoLab
Observed (Router): unanimous agreement among five racing models from several
providers is stored as a gate example. No stored request example was wrong in
timing V1, timing V2 or the majority follow-up. Exception: in jobs V2, three
probe examples contradicted the reference where the specification was silent
or weaker.
Observed (EvoLab): independent vote, which averages four isolated copies of one
model, had the highest mean Brier loss in causal-1.1, 1.2, 1.4 and 1.5 (partial),
and the second highest in 1.3. Its accuracy was 25%, 44%, 22%, 3/9 and 3/7.
Interpretation: two differences could explain this, and nothing yet separates
them. Router racers each see the whole task and come from different providers.
EvoLab voters each see a quarter of the evidence and are the same model. What
would settle it: an agreement condition that varies information partition and
model diversity separately. Any EvoLab version of that needs a protocol outside
B0, because B0 excludes mixed models.
- `Adaptive_Router@dcecd34:README.md` "Timing V1", "Timing V2", "Jobs V2", "Planned jobs V2" follow-up 1
- `evolab@b303534:collective_runs/CAUSAL_V11…V14_DEVELOPMENT_RESULTS_*.md`; `CAUSAL_V15_PARTIAL_RESULTS_20261117.md`
- Decision: D-0012

## 4. Shared open problems

### S-06 · No difficulty measure fixed before model exposure has been validated against model behaviour
EvoLab (observed, descriptive, 8 compute-eligible development tasks): oracle-
assigned easy/moderate/hard bands did not become behavioural difficulty. Every
condition reached 100% accuracy and single-agent mean Brier loss was 0.012532.
Router (standing rule, reconstructed, not an experimental result): TTFT is not
task difficulty, and probe latency's predictive value has not been established.
Neither line claims a measure that predicts model performance.
- `evolab@111c4f4:collective_runs/DEVELOPMENT_RESULTS_20261111.md` "What the development run teaches us" item 1
- `Adaptive_Router@06f1d55:BUILD_HISTORY.md` Standing rule 4; `README.md` "What it does not claim"
- Decision: D-0008
Refined 2026-11-18 (D-0014): in causal-1.4, once a floor was achieved,
oracle-assigned bands still did not reliably order single-agent loss
(relational easy/moderate/hard 0.05/0.80/0.67; coordination trap 0.05/0.80/0.80).
On causal-1.0, a script cleared every band at minimum cost (S-07). Structural
cost does not by itself make a task hard for models or for code.
- `evolab@b303534:collective_runs/CAUSAL_V14_DEVELOPMENT_RESULTS_20261117.md`

### S-10 · Neither line has a cost unit that captures what a condition can do
Observed (EvoLab): under equal provider tokens, the single agent spent 75.3% of
its tokens on reviews that could not buy evidence, against 7.6% for the
collective. Equal tokens did not give equal acquisition opportunity.
Observed (Router): the planning router's speed gains cost 6.6 to 17 times the
race's calls and 2.5 to 5 times its tokens. Its learning took 16 times the calls
and 28 times the tokens of the hand-written ceiling.
Neither line compares conditions on a unit the other could use. Any joint
experiment needs one fixed before generation.
- `evolab@b303534:collective_runs/CAUSAL_V14_ACQUISITION_AUDIT_20261117.md` §1
- `Adaptive_Router@dcecd34:README.md` "Planned jobs V2" follow-ups 1, 4, 6
- Decision: D-0013

## 5. Candidate joint experiments

None. The heterogeneous-collective question is on HOLD (D-0007, updated by D-0016).

## Change log

- 2026-11-17: S-01 to S-06 created (first review, main branches only).
- 2026-11-18: S-07, S-08, S-09, S-10 added. S-05 marked CONTESTED. S-06 refined.
  Review widened to active work branches.
