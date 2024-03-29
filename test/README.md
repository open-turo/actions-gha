# GitHub Action Test

## Description

GitHub Action that conditionally uses Node.js to test a GitHub Action

## Usage

```yaml
jobs:
  test:
    steps:
      - name: Test
        uses: open-turo/actions-gha/test@v1
          ## example value for github-token provided below
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Notes

- By default, this action will perform actions/checkout as its first step.

<!-- prettier-ignore-start -->
<!-- action-docs-inputs -->
## Inputs

| parameter | description | required | default |
| --- | --- | --- | --- |
| checkout-repo | Perform checkout as first step of action | `false` | true |
| github-token | GitHub token passed to coveralls. Usually - 'secrets.GITHUB_TOKEN'. Coveralls uses this token to verify the posted coverage data on the consumer repo and create a new check based on the results. It is built into Github Actions and does not need to be manually specified in your secrets store. | `true` |  |
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
