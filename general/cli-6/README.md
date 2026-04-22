# Cli

> `python-package-copier-template` is a small wrapper around [Copier](https://copier.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Reference

`python-package-copier-template` is a small wrapper around [Copier](https://copier.readthedocs.io/).
Its job is not to replace Copier, but to make the common path shorter and less error-prone.

## Main command

```bash
uvx python-package-copier-template [PATH_TO_PROJECT]
```

The wrapper inspects `PATH_TO_PROJECT`:

- if there is no `.copier-answers.yml` or `.copier-answers.yaml`, it runs copy mode;
- if there is a Copier answers file, it runs update mode.

Version output:

```bash
uvx python-package-copier-template --version
```

## How the wrapper resolves the template source

The most important detail is what happens in copy mode.
The wrapper does not always use the same source:

```{mermaid}
flowchart TD
    A["Run `python-package-copier-template DESTINATION`"] --> B{"Does DESTINATION already\nhave a Copier answers file?"}
    B -->|Yes| C["Run `copier update`\nusing project metadata"]
    B -->|No| D{"How was the wrapper installed?"}
    D -->|PyPI release| E["Use `gh:mgaitan/python-package-copier-template`\nwith `vcs_ref=<package version>`"]
    D -->|Git/VCS install| F["Use `gh:mgaitan/python-package-copier-template`\nwith `vcs_ref=<commit or requested revision>`"]
    D -->|Local editable/file install| G["Use the local checkout as `src_path`"]
```

In practice this means:

- `uvx python-package-copier-template ...` follows the matching published template release from PyPI.
- `uvx git+https://github.com/mgaitan/python-package-copier-template ...` follows the Git revision you installed from.
- `uv run python-package-copier-template ...` inside this repository uses the local checkout pinned to the current `HEAD` commit.

That behavior keeps the wrapper aligned with the version users actually invoked, instead of silently pulling the latest state of `main`.

## Environment variables

The wrapper consumes {term}`COPIER_TEMPLATE_DEFAULTS`.

When set to `1`, copy mode runs with Copier defaults enabled.
That is mostly useful for automated examples, t

*[truncated — see source for full prompt]*