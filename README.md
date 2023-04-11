# Terraform Collaboration Private Registry Lab

Terraform code which deploys an s3 webapp for use in the  HashiCorp Academy Terraform Collaboration lab. This module is used to demonstrate TFC/TFE module publishing workflow into the [Private Module Registry](https://www.terraform.io/docs/cloud/registry/index.html).

The example module deploys an s3 webapp with an index.html that can be visited for inspection. It is a simple collection of Terraform resources that are grouped into a module.

This module also demonstrates how [`templatefile()`](https://developer.hashicorp.com/terraform/language/functions/templatefile) function can be used for templating which is useful passing in config/user data text files to infrastructure resources when required. In this case, the module takes a public key parameter and displays it on the index.html

## Usage
```hcl
module "webapp" {
  source     = "app.terraform.io..."
  version    = "x.x.x"
  public_key = "-----BEGIN PUBLIC KEY----- MIICIjANBgkqh..."
}

output "website_endpoint" {
  value = module.webapp.endpoint
}

```

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | n/a |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_s3_bucket.bucket](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket) | resource |
| [aws_s3_bucket_acl.bucket](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_acl) | resource |
| [aws_s3_bucket_policy.policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_policy) | resource |
| [aws_s3_bucket_website_configuration.bucket](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket_website_configuration) | resource |
| [aws_s3_object.webapp](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_object) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_name"></a> [name](#input\_name) | Name for webapp | `string` | `"<RANDOM_BUCKET_NAME>"` | no |
| <a name="input_prefix"></a> [prefix](#input\_prefix) | Prefix for the webapp name | `string` | `"academy-webapp"` | no |
| <a name="input_public_key"></a> [public\_key](#input\_public\_key) | Value of a public pem generated by AWS key-pair | `string` | n/a | yes |
| <a name="input_region"></a> [region](#input\_region) | AWS Cloud Hosting Region | `string` | `"us-east-2"` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_endpoint"></a> [endpoint](#output\_endpoint) | n/a |