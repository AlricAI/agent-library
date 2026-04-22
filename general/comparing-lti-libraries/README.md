# Comparing Lti Libraries

> Elixir's LTI ecosystem is small.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Comparing Elixir LTI Libraries

Elixir's LTI ecosystem is small. If you need LTI 1.3 support, there are
two real options: Ltix and `lti_1p3`. This guide compares their design
philosophies so you can choose the right fit for your project.

## Landscape

| Library | LTI version | Status | Hex downloads |
|---|---|---|---|
| **Ltix** | 1.3 | Active | New |
| **`lti_1p3`** | 1.3 | Active | ~62,000 |
| `lti` | 1.0 only | Unmaintained | ~132,000 (legacy) |
| `plug_lti` | 1.x | Unmaintained | Not on Hex |
| `lightbulb` | 1.3 | Active (Gleam, not Elixir) | ~200 |

[`lti_1p3`](https://hex.pm/packages/lti_1p3) comes from the
Simon Initiative at Carnegie Mellon University. It was generously
extracted from [OLI Torus](https://github.com/Simon-Initiative/oli-torus),
a large Phoenix/LiveView learning platform, and has been in production
since 2021. The same team maintains `lightbulb`, a Gleam LTI library
targeting the BEAM.

Ltix would not exist without `lti_1p3`. It was born from extensive
experience building tools on top of `lti_1p3` and reflects lessons
learned about what a tool-focused LTI library could look like when
designed from scratch.

## Different starting points

The libraries come from different contexts, which shaped their designs:

**`lti_1p3`** was extracted from a production LMS. It supports both the
platform and tool sides of LTI, includes database-backed storage with
Ecto schemas, and reflects the needs of a large application that manages
its own registrations, JWKs, and platform instances.

**Ltix** was designed as a standalone library for tool developers. It
focuses on the tool side only, keeps storage abstract, and tries to
minimize the surface area a host app needs to implement.

Neither approach is wrong — they serve different audiences.

## API comparison

### Launch flow

Both libraries handle the three-step OIDC launch. The main difference
is how claims are returned.

**Ltix** parses claims into typed structs during validation:

```elixir
{:ok, %{redi

*[truncated — see source for full prompt]*