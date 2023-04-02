# terraformproject_on_AWS
# AWS Terraform Script

This Terraform script creates an AWS IAM Role, an S3 bucket, a DynamoDB table, a Security Group, and an EC2 instance.

## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) installed on your machine.
- AWS credentials with sufficient privileges.

## Configuration

In `provider "aws"`, modify the `access_key` and `secret_key` values to match your AWS credentials. You can also modify the `region` value to use a different region.

## Resources Created

- `aws_iam_role.devopsguru_iam_role` - An IAM Role with an Assume Role Policy allowing EC2 instances to assume the role.
- `aws_iam_policy.devopsguru_s3_full_access` - An IAM Policy that allows full access to S3.
- `aws_iam_policy.devopsguru_dynamodb_full_access` - An IAM Policy that allows full access to DynamoDB.
- `aws_iam_policy.devopsguru_ec2_full_access` - An IAM Policy that allows full access to EC2.
- `aws_iam_role_policy_attachment.devopsguru_s3_policy` - Attaches the `aws_iam_policy.devopsguru_s3_full_access` policy to the `aws_iam_role.devopsguru_iam_role`.
- `aws_iam_role_policy_attachment.devopsguru_dynamodb_policy` - Attaches the `aws_iam_policy.devopsguru_dynamodb_full_access` policy to the `aws_iam_role.devopsguru_iam_role`.
- `aws_iam_role_policy_attachment.devopsguru_ec2_policy` - Attaches the `aws_iam_policy.devopsguru_ec2_full_access` policy to the `aws_iam_role.devopsguru_iam_role`.
- `aws_s3_bucket.devopsguru_s3bucket` - An S3 bucket with server-side encryption and versioning enabled.
- `aws_dynamodb_table.devopsguru_dbtablename` - A DynamoDB table with `userId` as the hash key and `PROVISIONED` billing mode.
- `aws_security_group.devopsguru_websg` - A Security Group allowing inbound traffic on port 80.
- `aws_instance.devopsguru_ec2_instance` - An EC2 instance with Amazon Linux 2 AMI, using the `t2.micro` instance type and attached to the `aws_security_group.devopsguru_websg` security group.

## Usage

1. Clone this repository to your machine.
2. In the cloned repository, run `terraform init` to initialize Terraform.
3. Run `terraform plan` to see the changes that Terraform will make.
4. Run `terraform apply` to apply the changes.
5. When you're finished, run `terraform destroy` to delete all resources created by this script.
