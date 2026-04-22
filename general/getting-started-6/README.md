# Getting Started

> This project is, first and foremost, a [Copier](https://copier.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started

This project is, first and foremost, a [Copier](https://copier.readthedocs.io/) template.
What makes it nicer to consume is that it is also published as a Python package with a tiny wrapper CLI:

```bash
uvx python-package-copier-template [PATH_TO_PROJECT]
```

That wrapper exists so you do not need to remember the `copier copy` and `copier update` incantations every time.
It checks the destination directory:

- If there is no `.copier-answers.yml` or `.copier-answers.yaml`, it creates a project.
- If there is a Copier answers file, it updates the project in place.

The version-resolution details for the wrapper live in [CLI Reference](cli.md).

You can inspect the published wrapper version with:

```bash
uvx python-package-copier-template --version
```

If you want to use the latest development version from GitHub instead of the latest published release:

```bash
uvx git+https://github.com/mgaitan/python-package-copier-template [PATH_TO_PROJECT]
```

And to inspect that development wrapper version:

```bash
uvx git+https://github.com/mgaitan/python-package-copier-template -- --version
```

## Create a new project with the wrapper

The most convenient path is:

```bash
uvx python-package-copier-template /path/to/your/new/project
```

That will run Copier in copy mode with sensible defaults and prompt you for the remaining project metadata.

The capture below shows a real wrapper-driven project creation during the docs build.
Under the hood it runs non-interactively with defaults in a temporary directory, while displaying the normal command a user would type:

```{richterm} sh -lc 'tmp="$(mktemp -d)"; COPIER_TEMPLATE_DEFAULTS=1 uv run python-package-copier-template "$tmp/demo-project"'
:shown-command: uvx python-package-copier-template [PATH_TO_PROJECT]
```

After generation:

```bash
cd /path/to/your/new/project
uv sync
make qa
make test
make docs
```

That gives you a ready-to-work baseline with dependencies, QA, tests, and documentation.
Use `ma

*[truncated — see source for full prompt]*