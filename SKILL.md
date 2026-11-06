---
name: plan-and-budget
description: Use before starting any non-trivial task — multi-step work, anything likely to take more than a few minutes, anything that downloads/installs/runs long, touches many files, or changes the environment. Produces a short plan with a complexity rating, a step/time estimate and a token budget, and waits for explicit approval when complexity is medium or high.
license: MIT
---

# Plan first, and show the budget

Before touching files or running commands, answer in 4–6 lines. Then stop and wait.

## When NOT to use this

Skip the ritual for work that is obviously small — do it, then say what you did:

- one lookup, one read, one-line answer
- a single-file edit (change a number, rename a field)
- the user already told you exactly what to do and it is unambiguous
- pure conversation, confirmation, restating

Rule of thumb: **≤ 3 steps, no downloads, fewer than 3 files → just do it.**

## Output format

```
Complexity: low / medium / high
Cost: ~N steps, ~M minutes, downloads? long-running?
Plan:
  1. …
  2. … (mention a lighter alternative when one exists)
Token budget: X–Yk (context A / code B / debug C), ≈ $Z
```

## Tiers

- **Low** — a handful of steps, finishes in minutes → report it, then do it.
- **Medium / high** — downloads a model, runs longer than ~10 minutes, touches many files,
  does audio/video synthesis, migrates an environment, installs dependencies, or reverse
  engineers a private format → **give the plan only, and wait for an explicit "go"**.

Never start long background jobs, big refactors, or multi-stage pipelines before that "go".

## Estimating the budget

- reading/scanning: 2–10k tokens per pass
- writing code: ~3–6k output per 100 lines
- debugging: 20–40k input per reload-and-verify round (mostly cached)
- convert with the current price table; state the assumptions

## After the work

- One line comparing actual vs. estimated cost. Explain large deltas.
- If you discover the job is bigger than you said, stop and re-report — do not quietly grind on.
