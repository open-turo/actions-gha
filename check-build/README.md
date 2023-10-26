# GitHub Action Check Node Build

## Description

GitHub Action that determines if the code has changed without actually running a build.

## Usage

```yaml
jobs:
  build:
    steps:
      - name: Check build
        uses: open-turo/actions-gha/check-build@v1
        with:
          ## example value for github-token provided below
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Dist check

Runs `npm run prepare` and checks to see if there are uncommitted changes.

<!-- prettier-ignore-start -->
<!-- action-docs-inputs -->
## Inputs

| parameter | description | required | default |
| --- | --- | --- | --- |
| github-token | GitHub token that can create/delete comments. e.g. 'secrets.GITHUB_TOKEN' | `true` |  |
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
