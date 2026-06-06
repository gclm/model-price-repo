---
name: sync-model-pricing
description: Workflow command scaffold for sync-model-pricing in model-price-repo.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /sync-model-pricing

Use this workflow when working on **sync-model-pricing** in `model-price-repo`.

## Goal

Synchronize or update model pricing data from an external or upstream source.

## Common Files

- `model_prices_and_context_window.json`
- `model_prices_and_context_window.sha256`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Fetch or generate the latest model pricing data.
- Update model_prices_and_context_window.json with new data.
- Update model_prices_and_context_window.sha256 to match the new JSON file.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.