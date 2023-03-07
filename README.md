# matter-actions

Repository for the common library's GitHub actions.

It assumes the projects use [hatch](https://hatch.pypa.io/) as the management tool. 

There are three reusable action:

* Code lint
* Run tests
* Release Library

## Code lint

Example of code lint workflow usage:

```yaml
name: Code Lint

on: push

jobs:
  code-lint:
    name: Code Lint
    uses: Matter-Tech/matter-library-actions/.github/workflows/lint.yaml@v0
```

## Run tests

Example of run tests workflow usage:

```yaml
name: Test suite

on: push

jobs:
  run-test:
    name: Run tests
    uses: Matter-Tech/matter-library-actions/.github/workflows/run-tests.yaml@v0
```


## Release a new version

Example of release workflow usage:

```yaml
name: Prepare Release
on:
  workflow_dispatch:
    inputs:
      release-type:
        description: 'Release type? (major/minor/fix)'
        required: true
        default: ''


jobs:
  release-version:
    name: Release new version
    uses: Matter-Tech/matter-library-actions/.github/workflows/release.yaml@v0.0.1
    with:
      release-type: ${{github.event.inputs.release-type}}
```
