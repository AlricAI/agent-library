# Board Architecture

> ## Autofill Architecture

Board-specific autofill scripts follow a composition-based architecture:

- **`scripts/autofill_common.py`** — shared utilit

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Board Architecture

## Autofill Architecture

Board-specific autofill scripts follow a composition-based architecture:

- **`scripts/autofill_common.py`** — shared utilities (label matching, option selection, screenshot capture, page snapshotting, report writing, submit button clicking, captcha helpers)
- **`scripts/autofill_pipeline.py`** — shared orchestration (`autofill_main` for CLI entry + payload building, `run_browser_pipeline` for browser-based navigate/fill/submit/confirm flow)
- **`scripts/autofill_{board}.py`** — board-specific logic only (CSS selectors, form parsing, field inference, form filling)
- **`scripts/question_classifier.py`** — unified question classifier. Single entry point (`classify_question()`) that maps question labels to categories using priority-ordered detector dispatch. Board scripts use the category result, then let shared policy code decide whether the prompt is affirmative positive-fit, profile-driven, or still non-deterministic.
- **`scripts/application_submit_common.py`** — lower-level shared functions (profile parsing, `resolve_shared_question_policy()`, LLM answer generation, Gmail polling, Notion sync, individual question detector functions, credential-backed claim lookup)

New boards import from `autofill_common`, `autofill_pipeline`, and `application_submit_common` only. Simple single-page ATS families (Breezy, Recruitee, Jobvite, JazzHR, Paycor) reuse shared payload helpers from `application_submit_common.py`, shared fill/classification helpers from `autofill_common.py`, and the thin runtime wrapper in `autofill_pipeline.py` while still keeping board naming, selectors, and submit-state rules explicit in each `autofill_{board}.py`. API-based boards (Dover) and multi-page wizard or auth-gated boards (Workday, Phenom, SuccessFactors) use `autofill_main` with a custom `run_browser_fn` callback instead of raw `run_browser_pipeline`.

**Supported boards (25):** Greenhouse, Ashby, Lever, Gem, Dover, Workday, Phenom, iCIMS, Eightf

*[truncated — see source for full prompt]*