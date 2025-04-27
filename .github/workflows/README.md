# GitHub Actions Workflows

## OpenAPI Specification Validation

The `validate-openapi.yml` workflow automatically validates OpenAPI specifications when creating a pull request to the master branch.

### What it validates

The workflow validates the following OpenAPI specification files:
- `api/transaction/build/transaction.yaml`
- `api/meta/build/meta.yaml`
- `api/registry/build/registry.yaml`

### How it works

The workflow:
1. Runs when a pull request is created or updated targeting the master or main branch
2. Only triggers when one of the OpenAPI specification files has been modified
3. Uses `swagger-cli` to validate each specification file against OpenAPI 3.0 standards
4. Fails the check if any validation errors are found, preventing the PR from being merged

### Troubleshooting

If the workflow fails due to OpenAPI validation errors:
1. Check the GitHub Actions workflow output for detailed error messages
2. Fix the identified issues in the respective YAML file
3. Push the changes to update the pull request and trigger a new validation run 