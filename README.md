# Shareable Workflows

Reusable GitHub Actions workflows for Terraform and AWS operations.

## Workflows

### terraform-apply.yaml
Deploys Terraform infrastructure across environments (dev, uat, prod, root).

**Usage:**
```yaml
uses: ./.github/workflows/terraform-apply.yaml
with:
  environment: dev
secrets:
  admin_account_id: ${{ secrets.ADMIN_ACCOUNT_ID }}
  role_name: ${{ secrets.ROLE_NAME }}
```

### terraform-cost.yaml
Generates cost estimates for Terraform changes using Infracost.

**Usage:**
```yaml
uses: ./.github/workflows/terraform-cost.yaml
secrets:
  admin_account_id: ${{ secrets.ADMIN_ACCOUNT_ID }}
  role_name: ${{ secrets.ROLE_NAME }}
```

### terraform-lint.yaml
Lints Terraform code using TFLint.

**Usage:**
```yaml
uses: ./.github/workflows/terraform-lint.yaml
with:
  environment: dev
```

### s3-upload.yaml
Uploads repository contents to S3 bucket by environment.

**Usage:**
```yaml
uses: ./.github/workflows/s3-upload.yaml
with:
  environment: dev
secrets:
  admin_account_id: ${{ secrets.ADMIN_ACCOUNT_ID }}
  role_name: ${{ secrets.ROLE_NAME }}
```

## Required Secrets

- `ADMIN_ACCOUNT_ID`: AWS account ID for secret storage
- `ROLE_NAME`: OIDC provider role name

## Prerequisites

- AWS OIDC provider configured
- SSM parameters for account IDs and API keys
- Terraform backend configuration files