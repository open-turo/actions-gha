# GitHub Action Node Check Dist

GitHub Action runs checks to see if the code has changed without running a build.

## Usage

```yaml
jobs:
  build:
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Dist check
        uses: open-turo/actions-gha/node-check-dist@v1
```

## Dist check

Runs `npm run prepare` and checks to see if there are uncommitted changes.
