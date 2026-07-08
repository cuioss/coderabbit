# coderabbit

Central [CodeRabbit](https://coderabbit.ai) configuration for the **cuioss** organization.

CodeRabbit reads `.coderabbit.yaml` from a repository literally named `coderabbit` and
applies it to every organization repository that does **not** define its own
`.coderabbit.yaml`.

## What it does

Skips automatic reviews for bot-authored dependency/propagation PRs (they are already gated
by CI and auto-merge):

- **Dependabot** (`dependabot[bot]`) — dependency bumps.
- **Release bot** (`cuioss-release-bot[bot]`) — consumer-propagation PRs opened by the release
  App: parent-version bumps pushed to a project's `consumers` list, and `cuioss-organization`
  workflow-reference (SHA) bumps.

It also provides a manual opt-out label:

- Add the **`skip-coderabbit`** label to any pull request to skip its automatic review. All
  other PRs are still reviewed.

It tunes the review output to cut low-value noise (sequence diagrams, poem/fortune, suggested
labels/reviewers, the interactive finishing-touches checkboxes, and always-skipped pre-merge
checks) while keeping the substance — findings, **nitpicks** (treated as signal), committable
suggestions, and the machine-readable *Prompt for AI Agents* block.

## Signal vs. noise

See **[docs/review-signal-vs-noise.md](docs/review-signal-vs-noise.md)** for the full breakdown
of which parts of a CodeRabbit review are signal vs. noise, what each config setting does, and
what cannot be suppressed via config (and must be filtered downstream, e.g. in plan-marshall's
PR-comment triage).

## Precedence

A repository-level `.coderabbit.yaml` **fully overrides** this central file (sources do not
merge) unless that repository sets `inheritance: true`. Organization *Global Overrides* in the
CodeRabbit dashboard take precedence over this file.

See the [CodeRabbit configuration overview](https://docs.coderabbit.ai/guides/configuration-overview)
for the full precedence order.
