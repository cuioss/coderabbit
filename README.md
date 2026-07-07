# coderabbit

Central [CodeRabbit](https://coderabbit.ai) configuration for the **cuioss** organization.

CodeRabbit reads `.coderabbit.yaml` from a repository literally named `coderabbit` and
applies it to every organization repository that does **not** define its own
`.coderabbit.yaml`.

## What it does

- Skips automatic reviews for pull requests opened by **Dependabot** (`dependabot[bot]`).
  Dependency bumps are already gated by CI and the `dependabot-auto-merge` workflow.

## Precedence

A repository-level `.coderabbit.yaml` **fully overrides** this central file (sources do not
merge) unless that repository sets `inheritance: true`. Organization *Global Overrides* in the
CodeRabbit dashboard take precedence over this file.

See the [CodeRabbit configuration overview](https://docs.coderabbit.ai/guides/configuration-overview)
for the full precedence order.
