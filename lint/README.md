# GitHub Action Lint

![][version-image]
![][workflows-badge-image]
[![Release date][release-date-image]][release-url]
[![semantic-release][semantic-image]][semantic-url]
[![npm license][license-image]][license-url]

GitHub Action runs lint on a GitHub Action

## Usage

```yaml
steps:
  - name: Checkout
    uses: actions/checkout@v2
  - name: Action Lint
    uses: open-turo/actions-gha/lint@v1
```

## Lint Checks

This action runs the following lint checks:

- [wagoid/commitlint-github-action](https://github.com/wagoid/commitlint-github-action)
- [pre-commit/action](https://github.com/pre-commit/action)

## Notes

- If the repository has a `package-lock.json`, it will execute `npm ci` before running the `pre-commit` step.
- `actionlint` will be installed and in the path to ensure that https://github.com/rhysd/actionlint can be run directly.
- This expects that `.commitlintrc.yml` will be present to enforce [`conventional-commit`](https://github.com/wagoid/commitlint-github-action).
