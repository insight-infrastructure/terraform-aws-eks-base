# terraform-aws-eks-base

[![open-issues](https://img.shields.io/github/issues-raw/insight-infrastructure/terraform-aws-eks-base?style=for-the-badge)](https://github.com/insight-infrastructure/terraform-aws-eks-base/issues)
[![open-pr](https://img.shields.io/github/issues-pr-raw/insight-infrastructure/terraform-aws-eks-base?style=for-the-badge)](https://github.com/insight-infrastructure/terraform-aws-eks-base/pulls)

## Features

This module sets up a network and EKS cluster on AWS.  This is a simple base module that you can wrap from other 
modules or take the outputs from and use in adjacent modules. 

## Terraform Versions

For Terraform v0.12.0+

## Usage

```
module "this" {
  source = "github.com/insight-infrastructure/terraform-aws-eks-base"
  id = "awesome-cluster-id"
}
```
## Examples

- [defaults](https://github.com/insight-infrastructure/terraform-aws-eks-base/tree/master/examples/defaults)

## Known  Issues
No issue is creating limit on this module.

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Providers

No provider.

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:-----:|
| azs | List of availability zones | `list(string)` | <pre>[<br>  "us-east-1a",<br>  "us-east-1b",<br>  "us-east-1c"<br>]</pre> | no |
| cidr | The cidr range for network | `string` | `"10.0.0.0/16"` | no |
| cluster\_autoscale | Do you want the cluster's worker pool to autoscale? | `bool` | `false` | no |
| cluster\_autoscale\_max\_workers | Maximum number of workers in worker pool | `number` | `4` | no |
| cluster\_autoscale\_min\_workers | Minimum number of workers in worker pool | `number` | `1` | no |
| create | Bool to create | `bool` | `true` | no |
| id | The id of the resources | `string` | n/a | yes |
| num\_azs | The number of AZs to deploy into | `number` | `3` | no |
| num\_workers | Number of workers for worker pool | `number` | `1` | no |
| private\_subnets | Subnet ranges | `list(string)` | <pre>[<br>  "10.0.1.0/24",<br>  "10.0.2.0/24",<br>  "10.0.3.0/24"<br>]</pre> | no |
| public\_subnets | Subnet ranges | `list(string)` | <pre>[<br>  "10.0.101.0/24",<br>  "10.0.102.0/24",<br>  "10.0.103.0/24"<br>]</pre> | no |
| tags | Tags for resources | `map(string)` | `{}` | no |
| vpc\_name | The name of the VPC | `string` | `""` | no |
| worker\_instance\_type | The instance class for workers | `string` | `"m5.large"` | no |

## Outputs

| Name | Description |
|------|-------------|
| cluster\_arn | The Amazon Resource Name (ARN) of the cluster. |
| cluster\_certificate\_authority\_data | Nested attribute containing certificate-authority-data for your cluster. This is the base64 encoded certificate data required to communicate with your cluster. |
| cluster\_endpoint | The endpoint for your EKS Kubernetes API. |
| cluster\_id | The name/id of the EKS cluster. |
| cluster\_security\_group\_id | Security group ID attached to the EKS cluster. |
| cluster\_version | The Kubernetes server version for the EKS cluster. |
| config\_map\_aws\_auth | A kubernetes configuration to authenticate to this EKS cluster. |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Testing
This module has been packaged with terratest tests

To run them:

1. Install Go
2. Run `make test-init` from the root of this repo
3. Run `make test` again from root

## Authors

Module managed by [insight-infrastructure](https://github.com/insight-infrastructure)

## Credits

- [Anton Babenko](https://github.com/antonbabenko)

## License

Apache 2 Licensed. See LICENSE for full details.