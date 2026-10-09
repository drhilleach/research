# SVM lab book — ENTRY 76: REGISTRATION — ARM4B four-arm, two-block priming study — written 9 Oct 2026, 13:20 Adelaide, BEFORE any ARM4B data exist

**Status: REGISTERED PLAN.** It is time-stamped by commit to the research GitHub repository before the first
participant starts. Forms: ENTRY 75 / arm4b_forms_built.md. Nothing in this entry may change once data exist.
Deviations are reported as deviations.

## 76.1 Design (ENTRY 75)
- **Blocks:**
  - Block 1 (B1): the development 20, in development primed-form order.
  - Block 2 (B2): the 20 CALIB59 conjugates (Ck at the position of Qk; v3 wording).
- **Primed block:** the development interleaving, F1 4T F2 4T F3 4T F4 4T F5 4T.

| arm | first block | second block |
|---|---|---|
| A | B1 primed | B2 plain |
| B | B1 plain | B2 primed |
| C | B2 primed | B1 plain |
| D | B2 plain | B1 primed |

- **Every form:** Prolific ID, G1, G2, 40 thinking items and 5 food items. Router arm4b_live.html (FNV-1a "arm4b:",
  mod 4). Completion code CD9XDLJS.

## 76.2 Recruitment: rolling experience comb (throttle)
- **One Prolific study**, internal name "4 arm 2 block". It excludes every earlier SVM study, including CALIB59.
- **Filter:** OR across five narrow bands of "Number of previous Survey submissions". The purpose is to spread
  collection over days and time zones. The bands are not analysis strata.

  | comb | bands |
  |---|---|
  | A (launch) | 100; 300; 1,000–1,005; 2,000–2,002; 3,000–3,030 |
  | B | 150; 450; 1,500–1,505; 2,500–2,503; 4,000–4,040 |
  | C | 70; 200; 700–705; 1,200–1,203; 3,500–3,535 |
  | D | 120; 600; 1,800–1,805; 2,800–2,803; ≥ 5,000 |

  After D, the cycle repeats with every band shifted +1 (A′, B′, …).
- **Shift rule (throughput only):** move to the next comb when fewer than 5 submissions arrive in 6 hours while
  places remain. Every shift is logged with its time and bands. No shift decision may use any answer.
- **Tranches:**
  - Tranche 1 = 100 places, the function tranche. It is checked only for router, form, timing, exclusions and
    completion code, as in ENTRY 67.
  - Later tranches add places to the same study.
  - The forms do not change. If they ever must, the people before the change are kept separate and reported apart.
- **Target:** 450 analysed per arm, 1,800 in total. Recruitment stops at the first of:
  - 1,800 analysed, counted after exclusions only;
  - all four combs and their +1 repeats exhausted;
  - budget spent.
  No outcome is computed before recruitment stops.
- **Reward:** £6/hr at the posted time. The posted time can be adjusted between tranches for fair pay.

## 76.3 Exclusions (fixed)
1. **Prolific status:** APPROVED or AWAITING REVIEW only. Returned, timed-out and rejected submissions are dropped.
2. **PID:** trimmed. Repaired if exactly one Prolific ID occurs inside it. Rows whose PID is not in the export are
   dropped. For duplicates, the earliest submission is kept.
3. **Guard:** |G1 + G2 − 11| > 6.
4. **Time:** Prolific time taken < 75 s or > 900 s. This is RAMP38's 60–720 s for 38 items, scaled to 47.
5. **Straight-lining:** the same answer on ≥ 90% of the 40 thinking items.
6. **Incomplete:** any missing answer.
7. **Allocation:** a person whose form differs from the router hash (a forced test link) is analysed in the form
   actually answered and flagged.

## 76.4 Outcomes
- **L1, primary.** The frozen development priming lens applied to Block 1:
  - score = Σ ((x − μ)/σ)·w, with μ, σ and w from arm4b_frozen_priming_lens.json (sha256 prefix b3f302396b4ab3d3);
  - development only: ridge-0.10 Fisher, primed vs control, n 1,803 / 1,833;
  - development d in-sample 0.31, 10-fold OOF 0.23;
  - higher = more like primed.
- **L2, secondary.** The mirror lens on Block 2: score = Σ −w_k · ((C_k − m_k)/s_k), with m and s the B2 item means and
  SDs over all analysed ARM4B people.
  - Hypothesis: priming acts on the same value dimension, so a conjugate moves opposite to its original.
  - Fixed now and exploratory in status.
- **Exploratory:**
  - per-item d;
  - pole scores;
  - LIN under the designed Qk–Ck pairs and under OPPOSED_EXACT;
  - an OOF ridge-0.10 Fisher priming lens fitted within ARM4B on B2, with a 200-shuffle null;
  - 3VSLR and sex × role maps.

## 76.5 Contrasts
d = Cohen's d with pooled SD; 95% CI by bootstrap of people (2,000, seed 20261009); Welch t.

| # | contrast | outcome | question | test |
|---|---|---|---|---|
| **H1** | A vs B | L1 | priming of the development 20, first position (independent replication) | **primary**, one-sided, α 0.05, predicted A > B |
| H2 | D vs C | L1 | priming of the development 20, second position (after B2) | secondary, one-sided, D > C; Holm with H3 |
| H3 | C vs B | L1 | carry-over: a plain B1 after primed B2 vs plain B1 first | secondary, two-sided; Holm with H2 |
| H4 | (D − A) − (C − B) | L1 | priming × position; the cost of answering a second block cancels | estimation, 95% CI |
| H5 | C vs D; B vs A | L2 | priming of the new block, first and second position | secondary, two-sided, estimation |
| H6 | {A, D} vs {B, C}, within person | z(L1) − z(L2) | within-person crossover | exploratory |

**Power for H1:**
- At 450 per arm, one-sided α 0.05, power is 0.94 if the frozen lens keeps d 0.20 out of sample, and 0.82 at d 0.15.
- 309 per arm gives 80% at d 0.20.

## 76.6 Pooling with development (reported, never tested)
- Arms A and B (Block 1, first position) are added to the development data, with wave or study as a stratum. The
  pooled estimate of the primed − control difference on L1 is reported as the best estimate.
- **The replication test is H1 on ARM4B data alone.**
- **Known deviation:** arm B uses the primed form's title ("Everyday Thoughts") and Prolific-ID position, whereas the
  development control form was "Thinking style 1" with the ID last.

## 76.7 Covariates and blocks (estimation only; the primary test is unadjusted)
- As sensitivity:
  - comb in force at "Started at";
  - day;
  - Prolific Total approvals (log);
  - age;
  - sex.
- The comb shift log is kept with the data.

## 76.8 Scripts
- **Before the first outcome is computed:**
  - an assembler (in the style of calib59_assemble.py, with the 76.3 rules);
  - an analysis script implementing 76.4–76.6.
- **Dry run:** both are run on synthetic data with a planted effect.
- **Then:** both are filed unedited, and run once on the real data.

## 76.9 Function tranche (first 100)
- **Checked:**
  - all four arms reached;
  - completion code accepted;
  - median time (expected about 5.9 min at the pilot pace of 7.5 s per item);
  - exclusion counts;
  - headers parse.
- **Not computed:** no L1, L2 or item statistic.
