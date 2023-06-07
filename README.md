# GitHub Actions CI File for Ape Projects

This action allows you to use your favorte [`ape`](https://github.com/ApeWorX/ape) commands in the GitHub Actions CI environment, such as `ape compile` and `ape test`

## Inputs

### `python-version`

**Optional** Overrides the version of python used to run ape.
Default is using Python `'3.10'`.

### `ape-version`

**Optional** Overrides the pin used to install `eth-ape`.
Default is to use the latest version of `eth-ape` (no pin).
Cannot be used with `ape-commit`.

### `ape-plugins-list`

**Optional** Space-separated list of plugins to install.
Default is to install from local `ape-config.yaml`.

Note: When requesting a pin, put it all together like `'plugin-a plugin-b==1.2.3 plugin-c>1.2'`

### `ape-remote-git-version`

**Optional** Install Ape from remote GitHub URL instead of version.
This is useful when installing from a branch or a commit hash to test something out.
If supplied, will use this instead of version. Otherwise, will use
version. If neither supplied, defaults to latest release.

## Outputs

No outputs.

## Example usage

```yaml
steps:
  - uses: actions/checkout@v3
  - uses: ApeWorX/github-action@v2
    with:
      python-version: "3.10"  # (optional)
  - run: ape test -s
```

**NOTE** This action is still in development
