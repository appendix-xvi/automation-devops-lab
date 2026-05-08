# AWS Infrastructure Automation Pipeline

A DevOps lab that demonstrates end-to-end infrastructure automation on AWS using Terraform, Ansible, GitLab CI/CD, and a monitoring stack.

The project is designed as a practical portfolio repository: it shows how infrastructure can be provisioned, configured, and validated through repeatable automation rather than manual setup.

## Overview

This lab covers a complete infrastructure delivery flow:

1. GitLab CI/CD runs the automation pipeline.
2. Terraform provisions AWS infrastructure such as VPC, EC2, S3, and RDS.
3. Ansible configures EC2 instances and installs application or monitoring components.
4. Prometheus and Grafana provide basic observability for the deployed environment.

## Capabilities

| Area | Implementation |
|---|---|
| Infrastructure provisioning | Terraform modules and AWS resources |
| Configuration management | Ansible playbooks |
| Dynamic inventory | Ansible with EC2 inventory integration |
| CI/CD automation | GitLab CI/CD pipeline stages |
| Monitoring | Prometheus and Grafana |
| Documentation | Markdown and architecture diagrams |

## Project Structure

```text
automation-devops-lab/
├── README.md
├── .gitlab-ci.yml
├── terraform/
│   ├── main.tf
│   ├── vpc.tf
│   ├── rds.tf
│   ├── s3.tf
│   └── variables.tf
├── ansible/
│   ├── site.yml
│   ├── prometheus_grafana.yml
│   └── aws_ec2_inventory.py
└── images/
    ├── infra-deploy-flow.png
    └── grafana-ui.png
```

## Prerequisites

- AWS account and IAM credentials
- Terraform installed locally or available in the CI runner
- Ansible installed locally or available in the CI runner
- GitLab project with CI/CD enabled
- Required AWS permissions for VPC, EC2, S3, and RDS resources

## Quick Start

Clone the repository:

```bash
git clone https://github.com/Nuntin/automation-devops-lab.git
cd automation-devops-lab
```

Provision AWS infrastructure:

```bash
cd terraform
terraform init
terraform apply -auto-approve -var-file="terraform.tfvars"
```

Run Ansible configuration:

```bash
cd ../ansible
chmod +x aws_ec2_inventory.py
ansible-playbook -i aws_ec2_inventory.py site.yml
ansible-playbook -i aws_ec2_inventory.py prometheus_grafana.yml
```

## Validation

After deployment, validate the environment by checking:

- Terraform apply output and resource state
- EC2 instance reachability
- Ansible playbook success summary
- Prometheus target health
- Grafana dashboard availability

## Planned Improvements

The next improvement areas are focused on production readiness:

- Terraform remote state and state locking with S3 and DynamoDB
- Environment separation for `dev`, `staging`, and `prod`
- Reusable Terraform modules
- CI security checks using tools such as `tfsec`, `checkov`, and `ansible-lint`
- Optional containerized monitoring stack for local testing
- GitOps-ready deployment path for Kubernetes-based workloads

## Notes

- This repository is a lab environment, not a production-ready baseline.
- Review IAM scope, network exposure, secrets handling, and cost impact before running it in a real AWS account.
- Do not commit real credentials, private keys, or production configuration files.

## Author

Nuntin Padmadin

- GitHub: [github.com/Nuntin](https://github.com/Nuntin)
- LinkedIn: [linkedin.com/in/nuntin-padmadin-97b708145](https://www.linkedin.com/in/nuntin-padmadin-97b708145/)
