# I18n Translation System Guide

> description: globs: alwaysApply: false

## Tags
`typescript` `openai`

## System Prompt
---
description:
globs:
alwaysApply: false
---
# I18n Translation System Guide

This project implements an intelligent translation system with incremental detection and language validation.

## 🌍 Translation Workflow

### Core Components
- **[scripts/processors/i18n-processor.ts](mdc:scripts/processors/i18n-processor.ts)** - Handles OpenAI-based translation
- **[scripts/formatters/agent-formatter.ts](mdc:scripts/formatters/agent-formatter.ts)** - Manages incremental translation logic
- **[scripts/validators/language-validator.ts](mdc:scripts/validators/language-validator.ts)** - Validates translation quality

### Translation Process Flow
1. **Source Detection**: Extract translatable fields from source files
2. **Incremental Check**: Compare with existing translations to detect changes
3. **Translation**: Use OpenAI to translate only new/changed content
4. **Merge**: Combine new translations with existing ones
5. **Validation**: Verify translation language matches expected locale
6. **Format**: Apply formatting and save results

## 🔄 Incremental Translation Logic

### Key Method: `getIncrementalData()`
Located in [scripts/formatters/agent-formatter.ts](mdc:scripts/formatters/agent-formatter.ts):

```typescript
private getIncrementalData = (sourceData: any, existingData: any) => {
  const needsTranslation = {};
  let hasUpdates = false;

  for (const key of config.selectors) {
    const sourceValue = get(sourceData, key);
    const existingValue = get(existingData, key);

    if (sourceValue && !isEqual(sourceValue, existingValue)) {
      set(needsTranslation, key, sourceValue);
      hasUpdates = true;
    }
  }

  return { hasUpdates, needsTranslation };
};
```

### Translation Strategy
- **Full Translation**: When no existing translation file exists
- **Incremental Translation**: When changes detected in source content
- **Skip Translation**: When no changes detected (content unchanged)
- **Merge Results**: Combine new translations with existing using `lodash.me

*[truncated — see source for full prompt]*