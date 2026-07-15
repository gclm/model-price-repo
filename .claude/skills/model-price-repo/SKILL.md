```markdown
# model-price-repo Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you how to contribute to the `model-price-repo`, a TypeScript codebase for managing and updating model pricing data. You'll learn the project's coding conventions, how to synchronize or update pricing data, and how to add or modify model pricing/configuration. The guide also covers testing patterns and provides handy commands for common workflows.

## Coding Conventions

### File Naming
- Use **snake_case** for all file names.
  - Example: `model_prices_and_context_window.json`, `config.json`, `my_module.ts`

### Import Style
- Use **relative imports** for referencing modules.
  ```typescript
  import { getModelPrice } from './model_utils';
  ```

### Export Style
- Use **named exports** (not default exports).
  ```typescript
  // In model_utils.ts
  export function getModelPrice(model: string): number { ... }

  // Usage
  import { getModelPrice } from './model_utils';
  ```

### Commit Messages
- Mixed types, but often use the `chore` prefix.
- Keep commit messages concise (average ~35 characters).
  - Example: `chore: update model pricing data`

## Workflows

### sync-model-pricing
**Trigger:** When you want to update the model pricing data to the latest version.  
**Command:** `/sync-model-pricing`

1. Fetch or generate the latest model pricing data from the external or upstream source.
2. Update `model_prices_and_context_window.json` with the new data.
3. Update `model_prices_and_context_window.sha256` to match the new JSON file (ensure the checksum reflects the current data).

**Example:**
```bash
# Fetch latest pricing (custom script or manual)
curl -o model_prices_and_context_window.json https://example.com/latest-pricing.json

# Update checksum
sha256sum model_prices_and_context_window.json > model_prices_and_context_window.sha256
```

### add-or-update-model-pricing
**Trigger:** When you need to add pricing for a new model or update pricing/configuration for existing models.  
**Command:** `/add-model-pricing`

1. Edit `config.json` to add or update the model configuration.
2. Update `model_prices_and_context_window.json` with the new or changed model pricing.
3. Update `model_prices_and_context_window.sha256` to reflect the changes in the JSON file.

**Example:**
```json
// config.json
{
  "models": [
    { "name": "new-model", "context_window": 8192 }
  ]
}
```
```json
// model_prices_and_context_window.json
{
  "new-model": { "price": 0.002, "context_window": 8192 }
}
```
```bash
sha256sum model_prices_and_context_window.json > model_prices_and_context_window.sha256
```

## Testing Patterns

- **Test files** use the `*.test.*` naming pattern (e.g., `model_utils.test.ts`).
- The specific testing framework is **unknown**; check existing test files for conventions.
- To run tests, look for scripts in `package.json` or use the standard TypeScript/Jest/Mocha test commands if applicable.

**Example:**
```typescript
// model_utils.test.ts
import { getModelPrice } from './model_utils';

test('returns correct price for known model', () => {
  expect(getModelPrice('new-model')).toBe(0.002);
});
```

## Commands

| Command               | Purpose                                                      |
|-----------------------|--------------------------------------------------------------|
| /sync-model-pricing   | Synchronize or update model pricing data to the latest version |
| /add-model-pricing    | Add or update pricing/configuration for models                |
```
