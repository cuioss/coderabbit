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

## Precedence

A repository-level `.coderabbit.yaml` **fully overrides** this central file (sources do not
merge) unless that repository sets `inheritance: true`. Organization *Global Overrides* in the
CodeRabbit dashboard take precedence over this file.

See the [CodeRabbit configuration overview](https://docs.coderabbit.ai/guides/configuration-overview)
for the full precedence order.
