# GitHub Actions CI File for Ape Projects

This action allows you to use your favorte [`ape`](https://github.com/ApeWorX/ape) commands in the GitHub Actions CI environment, such as `ape compile` and `ape test`

## Inputs

No inputs

## Outputs

No outputs

## Example usage

```yaml
steps:
  - uses: actions/checkout@v2
  - uses: ApeWorX/ape-action@main  # Runs `ape test`
```

**NOTE** This action is still in development
