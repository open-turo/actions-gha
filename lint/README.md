# GitHub Action Lint

<!-- prettier-ignore-start -->
<!-- action-docs-description -->
## Description

GitHub Action that runs lint on a GitHub Action
<!-- action-docs-description -->
<!-- prettier-ignore-end -->

## Usage

```yaml
jobs:
  build:
    steps:
      - name: Lint
        uses: open-turo/actions-gha/lint@v1
          ## example value for github-token provided below
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Lint Checks

This action runs the following lint checks:

- [action-pre-commit](https://github.com/open-turo/action-pre-commit)
- [check-build](../check-build/README.md) - if the action is `node`, this checks that build has been run and committed.

## Notes

- By default, this action will perform actions/checkout as its first step.
- If the consumer repository has a `package-lock.json`
  - It will execute `npm ci` before running the `pre-commit` step.
  - It will run the `check-build` action.
- This expects that `.commitlintrc.yaml` will be present at the root level of the consumer repository to enforce [`conventional-commit`](https://github.com/wagoid/commitlint-github-action).

<!-- prettier-ignore-start -->
<!-- action-docs-inputs -->
## Inputs

| parameter | description | required | default |
| --- | --- | --- | --- |
| checkout-repo | Perform checkout as first step of action | `false` | true |
| github-token | GitHub token that can create/delete comments. Usually - 'secrets.GITHUB_TOKEN' | `true` |  |
<!-- action-docs-inputs -->

<!-- action-docs-outputs -->

<!-- action-docs-outputs -->

<!-- action-docs-runs -->
## Runs

This action is a `composite` action.
<!-- action-docs-runs -->

<!-- action-docs-usage  -->
<!-- action-docs-usage -->
<!-- prettier-ignore-end -->
