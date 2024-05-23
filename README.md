# stepzen-login

This action deploys a StepZen schema assuming the environment has been logged into a StepZen account.

# What's new

First release

# Usage

## Pre-requisites

- Node
- StepZen CLI must be installed, see [stepzen-dev/stepzen-install action](https://github.com/stepzen-dev/stepzen-install/blob/main/README.md).
- Logged into StepZen account, see [stepzen-dev/stepzen-login action](https://github.com/stepzen-dev/stepzen-login/blob/main/README.md).

## Inputs

- `dir` - directory containing index.graphql
- `folder` - folder name for the endpoint
- `name` - name for the endpoint
- `tag` - tag to be appended to endpoint name (default empty), typically useful when testing to create a unique endpoint.

## Outputs

- `endpoint` - Endpoint name, for example `api/customers`
- `url` - Full URL of the deployed GraphQL endpoint

## Examples

### Standard deployment

<!-- start usage -->

```yaml
- uses: stepzen-dev/stepzen-deploy
  with:
    workspace: "schema/customers'
    folder: qa
    name: customers
```

<!-- end usage -->

### Unit testing

Using a tag such as the GitHub run identifier can ensure that concurrent runs of workflows do not conflict with each other.

<!-- start usage -->

```yaml
- uses: stepzen-dev/stepzen-deploy
  with:
    workspace: "schema/customers"
    folder: unittest
    name: customers
    tag: ${{ github.run_id }}
```

<!-- end usage -->
