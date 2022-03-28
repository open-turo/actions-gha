# GitHub Action Test

GitHub Action runs tests within the consuming GitHub repository.

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

Note: by default, this action will perform actions/checkout as its first step.

## Test

For node based actions, it will run:

```shell
npm ci
npm test -- --coverage
```
