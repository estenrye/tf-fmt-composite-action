# TF-FMT Composite Action

This repository contains a composite action for GitHub Actions that checks out the repository and runs `terraform fmt --check --recursive`
over the specified path.

## Usage

To use this composite action, follow these steps:

1. Add the composite action to your workflow file:

```yaml
jobs:
  check-tf-fmt:
    runs-on: ubuntu-latest
    steps:
    - name: Check Terraform Formatting
      uses: estenrye/tf-fmt-composite-action@v1.0.0
      with:
        working_directory: './tf-tests/validly-formatted'
        terraform_version: 'latest'
        continue_on_error: false
```

## Inputs

| Name | Description | Required | Default |
|------|-------------|----------|---------|
| `working_directory` | The directory to run `terraform fmt` in. | No | `.` |
| `terraform_version` | The version of Terraform to use. | No | `latest` |
| `continue_on_error` | Whether to continue the workflow if an error occurs. | No | `false` |

## Outputs

| Name | Description |
|------|-------------|
| `output` | The output of the `terraform fmt` command. |
| `exit-code` | The exit-code of the `terraform fmt` command. |