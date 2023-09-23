# Yet another repository of reusable workflows
[![GitHub](https://img.shields.io/github/license/vbem/reusable)](LICENSE)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/vbem/reusable?label=Release&logo=github)](https://github.com/vbem/reusable/releases)
[![Test linter-default](https://github.com/vbem/reusable/actions/workflows/linter-default.test.yml/badge.svg)](https://github.com/vbem/reusable/actions/workflows/linter-default.test.yml)

## Linters
A set of code-linter related [reusable workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows).

### `linter-default`
[`linter-default.yml`](.github/workflows/linter-default.yml) predefines some configurations for the well-known [*Super-Linter* action](https://github.com/marketplace/actions/super-linter). Create `.github/workflows/linter.yaml` in your repository:
```yaml
---
name: Super Linter

concurrency:
  group: ${{ github.workflow }}@${{ github.ref }}
  cancel-in-progress: true

on:
  push:
    branches: [master, main]
  workflow_dispatch:

jobs:
  calling:
    uses: vbem/reusable/.github/workflows/linter-default.yml@v1
...
```