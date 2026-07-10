# setup-protoc

[![Check npm Dependencies status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-npm-dependencies-task.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-npm-dependencies-task.yml)
![test](https://github.com/embeint-cloud/setup-protoc/workflows/test/badge.svg)
[![Check Markdown status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-markdown-task.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-markdown-task.yml)
[![Check License status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-license.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-license.yml)
[![Check Taskfiles status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-taskfiles.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-taskfiles.yml)
[![Integration Tests status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/test-integration.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/test-integration.yml)
[![Check npm status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-npm-task.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-npm-task.yml)
[![Check TypeScript status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-typescript-task.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-typescript-task.yml)
[![Check tsconfig status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-tsconfig-task.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-tsconfig-task.yml)
[![Check Packaging status](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-packaging-ncc-typescript-task.yml/badge.svg)](https://github.com/embeint-cloud/setup-protoc/actions/workflows/check-packaging-ncc-typescript-task.yml)

This action makes the `protoc` compiler available to Workflows.

> **Note:** This is an Embeint-maintained fork of [arduino/setup-protoc](https://github.com/arduino/setup-protoc), diverged to keep it running on current Node.js/CI tooling. It is not intended to be merged upstream, so issues and PRs should be filed against this repo rather than the original.

## Upgrade from v1 to v2 or v3

Added support **only** for the new protobuf tag naming convention `MINOR.PATCH`.

## Usage

To get the latest stable version of `protoc` just add this step:

```yaml
- name: Install Protoc
  uses: embeint-cloud/setup-protoc@v4
```

If you want to pin a major or minor version you can use the `.x` wildcard:

```yaml
- name: Install Protoc
  uses: embeint-cloud/setup-protoc@v4
  with:
    version: "23.x"
```

You can also require to include releases marked as `pre-release` in Github using the `include-pre-releases` flag (the dafault value for this flag is `false`)

```yaml
- name: Install Protoc
  uses: embeint-cloud/setup-protoc@v4
  with:
    version: "23.x"
    include-pre-releases: true
```

To pin the exact version:

```yaml
- name: Install Protoc
  uses: embeint-cloud/setup-protoc@v4
  with:
    version: "23.2"
```

### Avoiding GitHub API rate limits

This action queries the GitHub API to list `protoc` releases. Unauthenticated requests
are limited to 60/hour per IP, which is shared by every GitHub-hosted runner and can be
exhausted quickly, causing the action to fail with a rate limit error. Authenticated
requests get 5,000/hour, so **always pass `repo-token`** in your workflow, using the
automatically-provided `GITHUB_TOKEN` secret (no extra setup required):

```yaml
- name: Install Protoc
  uses: embeint-cloud/setup-protoc@v4
  with:
    repo-token: ${{ secrets.GITHUB_TOKEN }}
```

## Enable verbose logging for a pipeline

Additional log events with the prefix ::debug:: can be enabled by setting the secret `ACTIONS_STEP_DEBUG` to `true`.

See [step-debug-logs](https://github.com/actions/toolkit/blob/master/docs/action-debugging.md#step-debug-logs) for reference.

## Security

If you think you found a vulnerability or other security-related bug in this project, please report it
to the Embeint Security Team 🛡️ Thank you!

e-mail contact: security@embeint.com

## Contributing

To report bugs or make feature requests, please submit an issue: https://github.com/embeint-cloud/setup-protoc/issues

Pull requests are welcome! Please see the [contribution guidelines](.github/CONTRIBUTING.md) for information.
