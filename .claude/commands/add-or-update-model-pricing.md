---
name: add-or-update-model-pricing
description: Workflow command scaffold for add-or-update-model-pricing in model-price-repo.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-model-pricing

Use this workflow when working on **add-or-update-model-pricing** in `model-price-repo`.

## Goal

Add new model pricing or update existing models, possibly including configuration changes.

## Common Files

- `config.json`
- `model_prices_and_context_window.json`
- `model_prices_and_context_window.sha256`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit config.json to add or update model configuration.
- Update model_prices_and_context_window.json with new or changed model pricing.
- Update model_prices_and_context_window.sha256 to reflect changes.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.