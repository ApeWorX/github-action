# GitHub Actions CI File for Ape Projects

This action allows you to use your favorte [`ape`](https://github.com/ApeWorX/ape) commands in the GitHub Actions CI environment, such as `ape compile` and `ape test`

## Inputs

### `python-version`

**Optional** Overrides the version of python used to run ape.
Default is using Python `'3.10'`.

### `ape-version-pin`

**Optional** Overrides the pin used to install `eth-ape`.
The default is to use the latest version of `eth-ape` (no pin).
You can use a `git+` value to install a branch, commit, or tag.
You can also paths, such as `"."` if you already have Ape checked out.

Example values:

- `1.0.0`
- `==1.0.0`
- `>=1.0.0,<2.0`
- `git+https://github.com/your-github/ape.git@your-branch`
- `$HOME/path/to/ape`
- `.`
- `.[test]`

### `ape-plugins-list`

**Optional** Space-separated list of plugins to install.
The default is to install from your project's local `ape-config.yaml`.
If you do not have any plugin version constraints specified in your `ape-config.yaml` file, the default includes the `-U` (`--upgrade`) flag to ensure you get the latest plugin versons.
Otherwise, it relies on the constraints you have configured.

To request specific versions of plugins, use a space-separated value like this `'plugin-a plugin-b==1.2.3 plugin-c>1.2'`.

## Outputs

### `ape-version`

The version of Ape installed.
This will either be the same as the `ape-version-pin` input if you provided that, else it will be the latest version found from `pypi`.

## Example usage

```yaml
steps:
  - uses: actions/checkout@v4
  - uses: ApeWorX/github-action@v3
    with:
      python-version: '3.10' # (optional)
      ape-version-pin: '>=0.8.24' # (optional)
      ape-plugins-list: 'solidity vyper==0.8.8' # (optional)
  - run: ape test -s
```

## Caching

This github action caches resources needed to efficiently use Ape.
The following table highlights the cached items:

- Compiler binaries located in `$HOME/.vvm` and `$HOME/.solcx`
- `$github.workspace/.build` - the compiled project
- `$HOME/.ape` to avoid having to re-download dependencies / re-create accounts.
