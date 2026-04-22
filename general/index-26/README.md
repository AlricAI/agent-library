# Index

> `python-package-copier-template` is a template for creating and maintaining modern Python packages with a batteries-included baseline: current packagi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# python-package-copier-template

`python-package-copier-template` is a template for creating and maintaining modern Python packages with a batteries-included baseline: current packaging practices, updated tooling, CI/CD automation, documentation scaffolding, and conventions that work well for both humans and code agents.

It is implemented as a [Copier](https://copier.readthedocs.io/) template and also published as a small Python CLI wrapper, so the most common entrypoint is:

```{richterm} sh -lc 'tmp="$(mktemp -d)"; COPIER_TEMPLATE_DEFAULTS=1 uv run python-package-copier-template "$tmp/demo-project"'
:shown-command: uvx python-package-copier-template [PATH_TO_PROJECT]
```

The docs build runs that example non-interactively with defaults in a temporary directory.
The command shown is the general entrypoint, and the capture is one concrete example of it.
The wrapper decides whether to run `copier copy` or `copier update` by inspecting the destination directory for a Copier answers file.
If you want the details of how the wrapper resolves template versions and source locations, see [CLI Reference](cli.md).
If you prefer the raw Copier commands, or want the latest development version from GitHub, the details are in [Getting Started](getting_started.md).

A public example generated from the template lives at [mgaitan/yet-another-demo](https://github.com/mgaitan/yet-another-demo).
It is useful both as a smoke target and as a concrete reference for what the scaffold looks like in practice.

## What this template includes

- A modern Python package baseline targeting Python 3.12+.
- Dependency and environment management with [uv](https://docs.astral.sh/uv/).
- Linting and formatting with [Ruff](https://docs.astral.sh/ruff/).
- Type checking with [ty](https://github.com/astral-sh/ty).
- Testing with [pytest](https://docs.pytest.org/), coverage, and related extensions.
- Optional QA orchestration and git hook setup with [prek](https://github.com/j178/prek).
- Sphinx docume

*[truncated — see source for full prompt]*