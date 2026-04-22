# Adopt Existing Project

> This guide is for the case where you already have a Python project, but it was not originally generated from `python-package-copier-template`.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Adopt the Template in an Existing Project

This guide is for the case where you already have a Python project, but it was not originally generated from `python-package-copier-template`.

The important constraint is this:

- `copier update` only works naturally after a project is already linked to the template through `.copier-answers.yml`.

So the first adoption is not a normal update.
The practical way to do it, especially with code agents, is:

1. render a fresh project from the template using metadata that matches the existing repository,
2. compare that rendered scaffold against the real project,
3. let the agent apply the template pieces incrementally,
4. create and keep `.copier-answers.yml`,
5. from then on, use normal template updates.

## Recommended migration strategy

For non-trivial repositories, do not try to “force” the template onto the project in one destructive pass.
Instead, use a bootstrap PR that introduces the template structure in controlled steps.

That gives you:

- smaller diffs,
- easier review,
- fewer merge conflicts,
- a clear checkpoint after which `copier update` becomes viable.

## Automated workflow with a code agent

The agent-friendly workflow looks like this.

### 1. Work on a dedicated branch

Create a migration branch in the existing project:

```bash
git checkout -b chore/adopt-python-package-copier-template
```

### 2. Render the template into a temporary directory

Render a clean scaffold with metadata that matches the existing project as closely as possible.

Example:

```bash
uvx --with=copier-template-extensions copier copy --trust \
  --data project_name="My Project" \
  --data project_description="My existing Python project" \
  --data author_fullname="Your Name" \
  --data author_email="you@example.com" \
  --data author_username="your-github-user" \
  --data gh_repo_create=skip \
  --data python_package_distribution_name="my-project" \
  --data python_package_import_name="my_project" \
  --data python_package_command

*[truncated — see source for full prompt]*