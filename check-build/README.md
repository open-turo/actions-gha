# GitHub Action Check Node Build

GitHub Action runs checks to see if the code has changed without running a build.

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
