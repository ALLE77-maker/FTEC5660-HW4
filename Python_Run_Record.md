# FTEC5660 Homework 4 — Python execution record

**Recorded on:** 17 November 2026  
**Source:** `solution_impl.py` and `smoke_test.py` included in this folder  
**Testing status:** Local representative smoke tests only; not the 60-question public-test benchmark.

## Command executed

```bash
python smoke_test.py
```

## Terminal output

```text
Table + metadata + 13 query parse cases: OK
Retrieval + unknown company/year abstention: OK
Disclosed/undisclosed generic-metric abstention: OK
Research report and earnings-call metadata/retrieval: OK
```

## What these results establish

The basic parsing, metadata, question parsing, retrieval and abstention branches pass the included synthetic fixtures. They **do not** establish the Homework 4 grade or end-to-end accuracy.

## Tests still required before submission

1. Download or fork the instructor's full repository at `https://github.com/hz0567/FTEC5660-HW4`.
2. Run `python apply_solution.py` there to insert the five implemented functions into the original `hw4.py`.
3. Run `python ablation.py --data-folder public_test` to generate measured ablation outcomes.
4. With your locally configured DeepSeek API key, run `python hw4.py --data-folder public_test` and then `python ablation.py --data-folder public_test` to generate measured retrieval/abstention metrics. Use the instructor runner for end-to-end answer accuracy.
5. Save the resulting `results.csv`, `ablation_results.csv`, and any terminal output you wish to keep as the final run record. Do not commit your `.env` or API key.

**Important:** The complete instructor runner and its public test corpus have not been executed in this workspace. The repository's README intentionally leaves benchmark scores unfilled until the real tests are run.

## Verified full public evaluation — 20 November 2026

GitHub Actions run: https://github.com/ALLE77-maker/FTEC5660-HW4/actions/runs/44727273016

The GitHub-hosted Python 3.11 job successfully installed dependencies and executed
`python public_test_check.py` and `python ablation.py` against all 40 public
documents and 60 questions. The measured final pipeline results were:

- 12/12 tables passed (mean cell score 100%).
- 40/40 documents passed metadata and probe checks.
- 60/60 query parses matched the public ground truth.
- Recall@5: 46/46 answerable questions (100%).
- Correct abstention: 14/14 unanswerable questions (100%).
- Simulated public Tasks 1–3: 55.00/55.00 points.
- No public document, parsing, retrieval or rejection failures.

The job produced `public_test_summary.json`, `retrieval_public_results.csv`,
`ablation_results.csv`, `ablation_errors.csv`, and text logs as a downloadable
artifact. Task 4 end-to-end DeepSeek answer accuracy has **not** been measured.
Configure the Actions secret `DEEPSEEK_API_KEY` and manually run
`DeepSeek official 60-question grading` to generate `results.csv`.


### Verified DeepSeek end-to-end public evaluation — 20 November 2026

The official, unchanged homework runner completed successfully on GitHub Actions [run #44728756334](https://github.com/ALLE77-maker/FTEC5660-HW4/actions/runs/44728756334), using the allowed `deepseek-v4-flash` generator and the repository's private Actions secret. It tested **40 documents and 60 public questions**. Task 1.1 **8/8**, Task 1.2 **7/7**, Task 2.1 **5/5**, Task 2.2 **10/10**, Task 2.3 **15/15**, Task 3 **10/10** and Task 4 **20/20**, giving a measured **75/75 for Tasks 1–4 on the public test set**. End-to-end answer accuracy was **100%**, including every fact, table, comparison, and unanswerable question. The generator made 46 model calls, with 54,769 input tokens and 150 output tokens, and the runner estimated its cost at **US$0.0083**. Total reported execution time was 6.4 seconds. The `results.csv` and complete grading log are available as a [workflow artifact](https://github.com/ALLE77-maker/FTEC5660-HW4/actions/runs/44728756334/artifacts/14624843394). Private-test results and TA-graded Tasks 5–6 are unknown.
