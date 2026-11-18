# Status

**Reviewed:** 2026-11-18 · evolab main@111c4f4, codex/causal-1-3@b303534, ccr-23487558@ac36da7 · Adaptive_Router main@e43e950, ccr-29a53f53@8d519c5, ccr-23487558@dcecd34

**Heading:** Both lines now use a code-only floor. Joint work is moving towards the question of where reading by a model beats code written by someone who knows the format. Confidence medium. Last prediction: HIT, but invalid as a test (the event predated it; the first review read `main` only).

## Needs your decision
1. **CONTESTED S-05.** EvoLab's amendment 0.1-G added a deterministic condition (`scripted_code`, loss 0 at minimum cost on causal-1.0). Retire S-05 into S-07, or revise it to "B0's frozen evaluation configuration has no deterministic arm"?
2. **BALANCE: EvoLab's collective question is being read in Router terms.** S-07 and S-08 frame EvoLab mainly as an arena for "model vs code". EvoLab's most consistent result is not used anywhere in the synthesis: communication beat independent synthesis in every version (+0.078, +0.175, +0.262, +0.130, +0.472 partial). S-09 uses EvoLab's vote result but not this one. The code-only amendment in `evolab` was written by a Router-side session.
3. **Project instructions are out of date.** They describe the Router as closed and quiet. It reopened on 2026-11-15 with the fast path (local authority still closed), merged to `main` on 2026-11-17. The hub now also tracks unmerged work branches. Confirm that is wanted.
- No new proposals. HOLD D-0016 (mixed collective) is not yet resolvable.

## Admitted this review
- D-0009 → S-07 A model condition must beat a code-only floor (both lines)
- D-0010 → S-05 marked CONTESTED
- D-0011 → S-08 Router's unseen-text method as a gate for EvoLab's next generator
- D-0012 → S-09 Agreement: reliable in the Router, weakest in EvoLab
- D-0013 → S-10 No shared cost unit
- D-0014 → S-06 refined (bands still do not order behaviour)

## Rejected this review
- D-0015 "Both lines' setbacks are harness scheduling": fails test 1 (Cross-line)

## Line-only activity
- EvoLab: causal-1.1 to 1.4 development runs, none passing the gates. The 1.4 acquisition audit; 1.5 interrupted at 7/9 tasks ($2.49), with gate 6 unreachable and no retry. Unmerged.
- Router: fast-path line from 2026-11-15: timing V1/V2, jobs V1/V2, planned jobs V1–V3, ceiling arm, isolation fixes, long streams, two-model learning roster. V3 primary not supported on time. Merged to main 2026-11-17 apart from the V3 branch.

## Synthesis size and balance
- Entries: Shared method 4 · Connections 2 · Tensions 2 · Open problems 2 · Joint experiments 0 (total 10; +4)
- Entries citing EvoLab 10/10 · Router 10/10
- Admissions over the last 2 reviews: 6 + 5 (plus 1 refinement), all drawing on both lines
- Proposals hosted: EvoLab 0 · Router 0
- Source vs arena: EvoLab is source in S-04. The Router is source in S-05 and S-08 (EvoLab is the arena). S-07 came from a single session working both repos. The rest are shared.
- Note: the hub is no longer independent of the work it reviews (S-07 provenance).
