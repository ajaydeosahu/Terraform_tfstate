## IAM permission Required to run this module

- AmazonS3FullAccess
- AmazonDynamoDBFullAccess
- kms-full-access

# AWS Network Terraform module

Terraform module to create Remote State Storage resources for workload deployment on AWS Cloud.

## Usage Example

```hcl
module "backend" {
  source = "git::https://{GIT_USER}:{GIT_TOKEN}@gitlab.com/squareops/sal/terraform/aws/tfstate.git?ref=dev"

  environment                                     = var.environment
  region                                          = var.region
  bucket_name                                     = var.name
  force_destroy                                   = var.force_destroy
  versioning_enabled                              = var.versioning_enabled
  logging                                         = var.logging
}

```
<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.13 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | 3.50.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 3.50.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_kms_key"></a> [kms\_key](#module\_kms\_key) | clouddrove/kms/aws | 0.15.0 |
| <a name="module_log_bucket"></a> [log\_bucket](#module\_log\_bucket) | terraform-aws-modules/s3-bucket/aws | 2.9.0 |
| <a name="module_s3_bucket"></a> [s3\_bucket](#module\_s3\_bucket) | terraform-aws-modules/s3-bucket/aws | 2.9.0 |

## Resources

| Name | Type |
|------|------|
| [aws_cloudtrail.s3_cloudtrail](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/resources/cloudtrail) | resource |
| [aws_cloudwatch_log_group.s3_cloudwatch](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/resources/cloudwatch_log_group) | resource |
| [aws_dynamodb_table.dynamodb_table](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/resources/dynamodb_table) | resource |
| [aws_iam_policy.s3_cloudtrail_cloudwatch_policy](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/resources/iam_policy) | resource |
| [aws_iam_role.s3_cloudtrail_cloudwatch_role](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/resources/iam_role) | resource |
| [aws_iam_role.this](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/resources/iam_role) | resource |
| [aws_iam_role_policy_attachment.s3_cloudtrail_policy_attachment](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/resources/iam_role_policy_attachment) | resource |
| [aws_kms_key.mykey](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/resources/kms_key) | resource |
| [aws_caller_identity.current](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/data-sources/caller_identity) | data source |
| [aws_iam_policy_document.bucket_policy](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.cloudtrail_assume_role](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.default](https://registry.terraform.io/providers/hashicorp/aws/3.50.0/docs/data-sources/iam_policy_document) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_bucket_name"></a> [bucket\_name](#input\_bucket\_name) | bucket name | `string` | `""` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | Select enviroment type: dev, demo, prod | `string` | `"demo"` | no |
| <a name="input_force_destroy"></a> [force\_destroy](#input\_force\_destroy) | Indicates all objects should be deleted from the bucket so that the bucket can be destroyed without error | `bool` | `false` | no |
| <a name="input_logging"></a> [logging](#input\_logging) | Map containing access bucket logging configuration | `bool` | `false` | no |
| <a name="input_region"></a> [region](#input\_region) | In which region S3 bucket will create | `string` | `""` | no |
| <a name="input_versioning_enabled"></a> [versioning\_enabled](#input\_versioning\_enabled) | keeping multiple variants of an object in the same bucket | `bool` | `false` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_bucket_region"></a> [bucket\_region](#output\_bucket\_region) | In which region S3 bucket will create |
| <a name="output_dynamodb_table_name"></a> [dynamodb\_table\_name](#output\_dynamodb\_table\_name) | dynamodb table name |
| <a name="output_log_bucket_name"></a> [log\_bucket\_name](#output\_log\_bucket\_name) | logging table name |
| <a name="output_state_bucket_name"></a> [state\_bucket\_name](#output\_state\_bucket\_name) | bucket name with id |
<!-- END_TF_DOCS -->
