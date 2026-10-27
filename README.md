# Preflight: submit 1 + 1

Before the workshop, confirm that your local workspace, GitHub PR and TensorLearn result can complete one round.

The task itself is deliberately trivial, so that anything that goes wrong is in the setup (your fork, GitHub Actions, the grading App or the TensorLearn connector) and gets fixed before the workshop, not during it. Every later lab uses the same round. Allow 10 to 20 minutes the first time; most of it is setup.

**What you'll practise:** the round you repeat in every lab with Claude Code: ask Claude for a small change, check its diff, commit and push, open a PR in your fork, then `/submit` and `/check`.

## Task

1. Calculate 1 + 1.
2. Ask Claude to put the numeric answer in `answer.json`.
3. Check the file yourself: `answer.json` should hold `{"answer": 2}` (spacing and line breaks don't matter). Then submit as described in **How to submit** below.

### If something fails

- **No "Check preflight submission" check on your PR:** Actions are not enabled in your fork (open your fork's **Actions** tab and enable them), or the PR targets the upstream repository instead of your fork's `main`. Push a new commit after fixing either.
- **The lab page says your fork is not connected:** use **Connect GitHub for scoring** to install the grading App on your fork, then **Recheck connection**.
- **`/submit` is refused:** the round may not be launched yet. Run `/load` again after your instructor launches it, check that your branch is pushed and the PR is open, then run `/submit` again.

## Working rules

Change only `answer.json`. Review Claude's change before you commit it. No model judge is needed.

## Acceptance

- The answer is a JSON number equal to 2.
- Only answer.json changes.
- The selected PR head (the latest commit you pushed to your PR) has a saved TensorLearn result.

## Done when

- `answer.json` is exactly `{"answer": 2}`, and `git status` shows no other changed file.
- Your PR inside your fork shows the **Check preflight submission** check.
- `/check` (or the lab page) shows a saved score of 10/10.

## Graded format

- `answer.json` must contain exactly one key, `answer`, whose value is a JSON number: `{"answer": 2}`. The text `"2"`, an extra key or invalid JSON is graded invalid and scores 0/10.

## How to submit

1. Fork this repository to your personal GitHub account. Use fictional information
   only, keep the fork public, and keep `main` as its default branch. In your fork's
   **Actions** tab, click **I understand my workflows, go ahead and enable them** if shown.
2. On the lab page, use **Connect GitHub for scoring** to install the read-only grading
   App on your fork, then **Recheck connection**.
3. Download the TensorLearn connector from the lab page and extract it outside your fork.
   From your fork folder, run the page's `--code` connection command and paste your token
   only into the hidden terminal prompt. This opens a Claude Code session connected to the lab.
4. In that session, run `/load`. Run `/load` again after your instructor launches the round.
5. Create a branch such as `preflight/first-draft` and complete the task above. Change only the
   files the task allows: any other change, including `CLAUDE.md`, `.claude/` settings or
   agents, or notes files, makes the submission invalid.
6. Commit and push your branch. Open a PR **inside your own fork**, targeting its `main`
   branch (GitHub may suggest the upstream repository: select your fork instead). Check
   that **Check preflight submission** starts in the PR's checks. Keep the PR open; no merge
   is required.
7. Run **`/submit`** in the connected Claude Code session, then `/check` (or refresh the
   lab page) to read your saved score. The Actions run is useful feedback, but it does not
   submit your work.

A change to your answer needs a new commit, push and `/submit`. Keep `main` unchanged:
the grader compares your PR with the released starter.

## What is graded

The pinned grader in `.github/workflows/grade.yml` reads your files as data and runs your
code only in an isolated, offline container. Every check is a fixed rule; no AI model
judges your work. Your score is out of 10. Your facilitator separately reviews
clarity and reasoning.

- `answer.json` is exactly `{"answer": 2}`: one key, a number (not a string). Any other shape makes the submission invalid.
