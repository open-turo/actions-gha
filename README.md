# `open-turo/actions-gha`

GitHub Actions for GitHub Action repositories

[![GitHub release](https://img.shields.io/github/release/Naereen/StrapDown.js.svg)](https://GitHub.com/Naereen/StrapDown.js/releases/)
[![Release date][release-date-image]][release-url]
[![GitHub latest commit](https://badgen.net/github/last-commit/Naereen/Strapdown.js)](https://GitHub.com/Naereen/StrapDown.js/commit/)
[![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg)](https://github.com/Naereen/StrapDown.js/blob/master/LICENSE)
![CI](https://github.com/open-turo/actions-gha/actions/workflows/release.yaml/badge.svg)
[![semantic-release][semantic-image]][semantic-url]
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

## Actions

### action: [`lint`](./lint)

Lint will run pre-commit linters against the consumer repository, optionally checking out, optionally running `npm ci`, install [actionlint](rhysd/actionlint), run [action-pre-commit](https://github.com/open-turo/action-pre-commit), and lastly optionally run [check-build](./check-build/README.md).

See usage [here](./lint/README.md#usage).

Documentation is found [here](./lint/README.md).

### action: [`check-build`](./check-build)

Checks to see if there are any changes in the consumer repository by running `npm run prepare` and determining if differences exist in the generated `dist` directory.

See usage [here](./check-build/README.md#usage).

Documentation is found [here](./check-build/README.md).

### action: [`release`](./release)

Release will optionally checkout the consumer repository and attempt a [Semantic Release](https://semantic-release.gitbook.io/semantic-release/usage/configuration) using the root level configuration file (e.g. `.releaserc.json`) indicating branches and plugins to use to facilitate the release. If a new release is published, a major version will also be released.

See usage [here](./release/README.md#usage).

Documentation is found [here](./release/README.md).

### action: [`test`](./test)

Optionally checks out the GitHub consumer repository, and if a `package-lock.json` file is found at the root level directory, runs `npm ci`, `npm test`, and [coveralls](https://github.com/coverallsapp/github-action).

See usage [here](./test/README.md#usage).

Documentation is found [here](./test/README.md).

## Get Help

Each Action has a detailed README for how to use it as referenced above. Please review Issues, post new Issues against this repository as needed.

## Contributions

Please see [here](https://github.com/open-turo/contributions) for guidelines on how to contribute to this project.

<!-- Links: -->

[version-image]: https://img.shields.io/github/package-json/v/open-turo/actions-gha.svg
[workflows-badge-image]: https://github.com/cycjimmy/semantic-release-action/workflows/Test%20Release/badge.svg
[release-date-image]: https://img.shields.io/github/release-date/open-turo/actions-gha.svg
[release-url]: https://github.com/cycjimmy/semantic-release-action/releases
[semantic-image]: https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg
[semantic-url]: https://github.com/semantic-release/semantic-release
[license-image]: https://img.shields.io/npm/l/@cycjimmy/semantic-release-action.svg
[license-url]: https://github.com/cycjimmy/semantic-release-action/blob/master/LICENSE
[changelog-url]: https://github.com/cycjimmy/semantic-release-action/blob/master/docs/CHANGELOG.md
[github-packages-registry]: https://github.com/features/packages
