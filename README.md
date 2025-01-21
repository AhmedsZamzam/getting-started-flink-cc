# Flink CC Demo 

This repository contains infrastructure-as-code and code for https://confluentinc.atlassian.net/wiki/spaces/FLINK/pages/3351249309/Flink+on+Confluent+Cloud+-+Product+Demo.

## General Requirements

* **Confluent Cloud API Keys** - [Cloud resource management API Keys](https://docs.confluent.io/cloud/current/security/authenticate/workload-identities/service-accounts/api-keys/overview.html#resource-scopes) with Organisation Admin permissions
* **Terraform (v1.9.5+)** - The demo resources is automatically created using [Terraform](https://www.terraform.io).
* **Git CLI** - Git CLI to clone the repo 

<details>
<summary>Installing Terraform and Git on MAC</summary>

Install `git` and `terraform` by running:

```bash
brew install git terraform
```

</details>


<details>
<summary>Installing Terraform and Git on Windows</summary>

Install `git` and `terraform` by running:

```powershell
choco install git terraform
```

</details> 


## Setup

First, clone the repo and change directory to `demo-infrastructure`

```bash
git clone git@github.com:confluentinc/flink-cc-demo.git
cd flink-cc-demo/demo-infrastructure
```

In the `demo-infrastructure` directory, create a `terraform.tfvars` file to store the Confluent Cloud API keys required by Terraform. Replace the placeholders below with your own keys.

```bash
cat > ./terraform.tfvars <<EOF
confluent_cloud_api_key = "{Confluent Cloud API Key}"
confluent_cloud_api_secret = "{Confluent Cloud API Key Secret}"
EOF
```

In `demo-infrastructure` run the following commands to set up the whole demo environment

```bash
terraform init
terraform apply --auto-approve
```

Source the demo environment variables 

<details>
<summary>Mac</summary>


```bash
source env.sh
```

</details>

<details>
<summary>Windows</summary>

```
call env.bat
```
</details>

## Labs

**Next Lab:** [Lab 1: Getting Started with Flink](./flink-getting-started/lab1.md)



## Tear down

In `demo-infrastructure` run the following commands to destroy the whole demo environment

```bash
terraform destroy --auto-approve
```
