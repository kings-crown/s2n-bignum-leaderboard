# s2n-bignum-bench Leaderboard

Leaderboard for the [s2n-bignum-bench](https://github.com/kings-crown/s2n-bignum-bench) Neural Theorem Proving benchmark, evaluating low-level code reasoning of LLMs. 2,301 (evolving) HOL Light proof problems derived from AWS [s2n-bignum](https://github.com/awslabs/s2n-bignum) cryptographic proofs.

## Viewing the Leaderboard
[Leaderboard Webpage](https://kings-crown.github.io/s2n-bignum-leaderboard/)

## Submitting to the Leaderboard

To get your model featured on the leaderboard:

1. **Set up the benchmark** — follow the [s2n-bignum-bench GUIDE](https://github.com/kings-crown/s2n-bignum-bench/blob/main/GUIDE.md) to generate problems and evaluate your model's answers locally.

2. **Prepare your answers CSV** — a CSV with the columns `problem_id, category, query, answer`:
   ```
   problem_id,category,query,answer
   arm.bignum_add.BIGNUM_ADD_CORRECT,functional_correctness_arm,"..."," REWRITE_TAC[...] THEN ..."
   ```

3. **Zip your CSV** — compress the CSV into a `.zip` file before submitting. Raw CSV submissions are not accepted to prevent data contamination of answers in public issue threads.

4. **Submit via GitHub Issue** — open a [Leaderboard Submission](https://github.com/kings-crown/s2n-bignum-leaderboard/issues/new?template=leaderboard-submission.yml) issue with:
   - Model name and URL (if applicable)
   - Your name/org and profile link
   - Whether the model is open or closed source
   - Your answers `.zip` (drag and drop as an attachment)
   - Any additional details (compute used, prompting strategy, etc.)

5. **We evaluate and publish** — we run your answers through the benchmark evaluation pipeline and add the results to the leaderboard.

## Verdicts

Each problem receives one verdict:

| Verdict | Meaning |
|---------|---------|
| **OK** | Proof succeeded without adding axioms |
| **FAIL** | Tactic failed to prove the goal |
| **CHEATING** | Solution added axioms (detected via axiom count comparison) or CHEAT_TAC detected |
| **ERROR** | Runtime exception or compilation error |
| **TIMEOUT** | Exceeded category timeout (default: 120s - configurable, please let us know your time) |

## Problem Categories

| Category | Count | Description |
|----------|-------|-------------|
| `generic` | 564 | General HOL Light lemmas |
| `program_state` | 555 | Program state properties |
| `functional_correctness_arm` | 439 | ARM functional correctness |
| `functional_correctness_x86` | 425 | x86-64 functional correctness |
| `bit_vector` | 318 | Bit vector operations |

## Maintainers

Balaji Rao, Juneyoung Lee ([@aqjune](https://github.com/aqjune))
