# terraform-ci-cd-example-yandex-cloud

Simple example on how to set up basic CI/CD repository for Terraform with Yandex Cloud and state lock

## Configuration description

### `yc-terraform-state-lock.tf`

This file creates S3 bucket and YDB instance to save state for our future project and perform state lock on changes.

As a result, it prints ready backend configuration to use in our CI/CD project. It also writes aws access keys into `.env` file.

### `main.tf`

This file creates SA for Terraform and writes access key into `.key.json` file. It also creates GitLab Runner machine.

## Actions order

1. Run `terraform init`
2. Export environment from `yc` CLI:

```shell
export YC_TOKEN=$(yc iam create-token)
export YC_CLOUD_ID=$(yc config get cloud-id)
export YC_FOLDER_ID=$(yc config get folder-id)
export AWS_ACCESS_KEY_ID="mock_access_key"
export AWS_SECRET_ACCESS_KEY="mock_secret_key"
```

### unfinished readme
