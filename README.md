# semver-release
 
Enforce the ref for a release.  The git ref:

- MUST be a SemVer version
- MUST NOT have a pre-release version

## Using

``` yaml
name: Release

on:
  release:
    types: [prereleased]

jobs:
  publish_release:
    runs-on: ubuntu-latest
    name: NAME
    steps:
      - name: Enforce SemVer for pre-release
        id: enforce_semver
        uses: NetChris/semver-release@SHA
      - name: Use the SemVer version
        run: echo Do something with semver_version: ${{ steps.enforce_semver.outputs.semver_version }}
```

Use the latest (or most-appropriate) SHA to ensure consistent results.
