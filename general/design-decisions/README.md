# Design Decisions

> This template is intentionally opinionated.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Features and Decisions

This template is intentionally opinionated.
It is meant to capture a working baseline for modern Python projects, not to be a neutral scaffold with every choice deferred.

The original rationale is described in the blog post [My opinionated scaffolding for modern Python projects](https://mgaitan.github.io/en/posts/opinionated-python-project-scaffolding/).
This chapter translates that rationale into a feature-by-feature reference.

## Copier template, plus a wrapper

The foundation is [Copier](https://copier.readthedocs.io/), not a plain GitHub template repository.
That matters because Copier supports project updates, so conventions can evolve after the initial scaffold.

This repository also publishes a wrapper CLI as `python-package-copier-template`.
The wrapper is intentionally small:

- it detects copy vs update mode from the destination,
- it keeps the happy path short,
- it hides the extra `copier-template-extensions` setup most users do not want to remember.

When you want full control, you can always drop to raw Copier commands.

## Python packaging defaults

Generated projects assume:

- Python 3.12+,
- a `src/` layout,
- metadata centralized in `pyproject.toml`,
- [`uv_build`](https://docs.astral.sh/uv/concepts/build-backend/) as the build backend for pure-Python packages,
- an optional CLI entrypoint implemented with [`argparse`](https://docs.python.org/3/library/argparse.html).

These defaults aim for a modern baseline without introducing unnecessary packaging complexity.
They match current packaging guidance better than older `setup.py`-centric layouts and are a good fit for libraries and small applications that do not need compiled extensions.

## Dependency management with uv

The template uses [uv](https://docs.astral.sh/uv/) for environment management, dependency resolution, and package publishing.
That decision is mostly about coherence:

- one tool for local environments and CI,
- fast installs and syncs,
- dependency grou

*[truncated — see source for full prompt]*