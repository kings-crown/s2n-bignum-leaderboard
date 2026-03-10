# s2n-bignum-bench Leaderboard

Leaderboard for the [s2n-bignum-bench](https://github.com/kings-crown/s2n-bignum-bench) tactic synthesis benchmark — 2,284 HOL Light proof problems derived from AWS [s2n-bignum](https://github.com/awslabs/s2n-bignum) cryptographic proofs.

## Viewing the Leaderboard

Open `index.html` in a browser. It loads `results.json` and renders an interactive table with sorting and category filters.

To serve locally (required for `fetch` to work):

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

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

4. **We evaluate and publish** — we run your answers through the benchmark evaluation pipeline and add the results to the leaderboard.

## Verdicts

Each problem receives one verdict:

| Verdict | Meaning |
|---------|---------|
| **OK** | Proof succeeded without adding axioms |
| **FAIL** | Tactic failed to prove the goal |
| **CHEATING** | Solution added axioms (detected via axiom count comparison) |
| **ERROR** | Runtime exception or compilation error |
| **TIMEOUT** | Exceeded category timeout (default: 120s) |

## Problem Categories

| Category | Count | Description |
|----------|-------|-------------|
| `generic` | 562 | General HOL Light lemmas |
| `program_state` | 552 | Program state properties |
| `functional_correctness_arm` | 437 | ARM64 functional correctness |
| `functional_correctness_x86` | 422 | x86-64 functional correctness |
| `bit_vector` | 311 | Bit vector operations |

## Maintainers

Balaji Rao, Juneyoung Lee ([@aqjune](https://github.com/aqjune))
