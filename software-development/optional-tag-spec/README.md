# Optional Tag Spec

> **Title:**  Add “optional” Test-Case Support (Off-by-Default Tests)

---



Right now all tests without a `--remove TAG` are run by default, and users

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
**Title:**  Add “optional” Test-Case Support (Off-by-Default Tests)

---

## Problem Statement

Right now all tests without a `--remove TAG` are run by default, and users must explicitly include or exclude by tags. We need a way for test authors to mark certain tests (or entire areas) as off-by-default, so that casual runs don’t execute them, but power users can opt in when desired.

---

## Proposed Feature: `optional` Key

1. **Top-Level Key**

   * Add a new (optional) test-case and area attribute:

     ```yaml
     optional: <string> | [<string>, …]
     ```
   * Semantics: any test or area with an `optional` key is *excluded* by default.

2. **Inheritance & Additivity**

   * If an `area:` or `class:` block includes `optional: X`, all descendant tests inherit that value.
   * Child nodes may specify their own `optional:` (string or array) to *add* categories.

3. **CLI Behavior**

   * **Default** (`cycodt run`):

     * Runs only tests **without** any `optional` key.
   * **Re-include All Optionals** (`cycodt run --include-optional`):

     * Includes *all* tests marked `optional`, regardless of their category.
   * **Re-include by Category** (`cycodt run --include-optional slow network needsAI`):

     * Only re-includes tests whose `optional` array intersects the provided list.
   * Compatible with existing flags (`--contains`, `--remove`)—all filters stack in order.

4. **Tag vs. Optional**

   * **Tags** remain purely user-controlled filters—no change in default inclusion logic.
   * **Optional** is the sole mechanism for off-by-default semantics; tags continue to drive inclusion/exclusion as today.

5. **Logging & Debug**

   * No visible “X tests skipped” summary in normal stdout.
   * Internally log skipped and re-included counts under debug log level.

---

## Examples

### 1) Single Test Opt-in

```yaml
- name: Slow integration test
  bash: ./run-heavy.sh
  optional: slow
```

* `cycodt run` ☑️ skips
* `cycodt run --include-optional` ☑️ runs
* `cycod

*[truncated — see source for full prompt]*