# GitHub Action Release

## Description

GitHub Action that produces a new Release of an Action - adds a new major tag

## Configuration

### Step1: Set any [Semantic Release Configuration](https://github.com/semantic-release/semantic-release/blob/master/docs/usage/configuration.md#configuration) in the consumer repository.

### Step2: [Add Secrets](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) in the consumer repository for the [Semantic Release Authentication](https://github.com/semantic-release/semantic-release/blob/master/docs/usage/ci-configuration.md#authentication) Environment Variables.

### Step3: Add a [Workflow File](https://help.github.com/en/articles/workflow-syntax-for-github-actions) to the consumer repository to create custom automated processes.

## Usage

```yaml
steps:
  - name: Release
    uses: open-turo/actions-gha/release@v1
    with:
      github-token: ${{ secrets.GITHUB_TOKEN }}
```

**IMPORTANT**: `GITHUB_TOKEN` does not have the required permissions to operate on protected branches.
If you are using this action for protected branches, replace `GITHUB_TOKEN` with [Personal Access Token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line). If using the `@semantic-release/git` plugin for protected branches, avoid persisting credentials as part of `actions/checkout@v4` by setting the parameter `persist-credentials: false`. This credential does not have the required permission to operate on protected branches.

<!-- prettier-ignore-start -->
<!-- action-docs-inputs -->
## Inputs

| parameter | description | required | default |
| --- | --- | --- | --- |
| checkout-repo | Perform checkout as first step of action | `false` | true |
| dry-run | Whether to run semantic release in `dry-run` mode. It will override the `dryRun` attribute in your configuration file | `false` |  |
| extra-plugins | Extra plugins for pre-install. You can also specify specifying version range for the extra plugins if you prefer.  Defaults to install @open-turo/semantic-release-config. | `false` | @open-turo/semantic-release-config  |
| github-token | GitHub token that can create/delete comments. e.g.  'secrets.GITHUB_TOKEN' | `false` |  |
<!-- action-docs-inputs -->

<!-- action-docs-outputs -->
## Outputs

| parameter | description |
| --- | --- |
| new-release-published | Whether a new release was published |
| new-release-version | Version of the new release |
| new-release-major-version | Major version of the new release |
<!-- action-docs-outputs -->

<!-- action-docs-runs -->
## Runs

This action is a `composite` action.
<!-- action-docs-runs -->

<!-- action-docs-usage  -->
<!-- action-docs-usage -->
<!-- prettier-ignore-end -->

## Additional Examples

### extra-plugins example

The action can be used with `extra-plugins` option to specify plugins which are not in the [default list of plugins of semantic release](https://semantic-release.gitbook.io/semantic-release/usage/plugins#default-plugins). When using this option, please make sure that these plugins are also mentioned in your [semantic release config's plugins](https://semantic-release.gitbook.io/semantic-release/usage/configuration#plugins) array.

For example, if you want to use `@semantic-release/git` and `@semantic-release/changelog` extra plugins, these must be added to `extra-plugins` in your actions file and `plugins` in your [release config file](https://semantic-release.gitbook.io/semantic-release/usage/configuration#configuration-file) as shown bellow:

Github Action Workflow:

```yaml
steps:
  - name: Release
    uses: open-turo/actions-gha/release@v1
    with:
      # You can specify specifying version range for the extra plugins if you prefer.
      extra-plugins: |
        @semantic-release/changelog@3.0.0
        @semantic-release/git
```

Similar to parameter `semantic_version`. _It is recommended to manually specify a version of semantic-release plugins to prevent errors caused._

Release Config:

```diff
  plugins: [
    .
+   "@semantic-release/changelog"
+   "@semantic-release/git",
  ]
```

### dry-run example

```yaml
jobs:
  build:
    steps:
      - name: Release
        uses: open-turo/actions-gha/release@v1
        with:
          dry-run: true
```

### using output parameters example

```yaml
jobs:
  build:
    steps:
      - name: Release
        uses: open-turo/actions-gha/release@v1
        id: semantic # Need an `id` for output variables
      - name: Do something when a new release published
        if: steps.semantic.outputs.new-release-published == 'true'
        run: |
          echo ${{ steps.semantic.outputs.new-release-version }}
          echo ${{ steps.semantic.outputs.new-release-major-version }}
```

## Notes

- By default, this action will perform actions/checkout as its first step.
