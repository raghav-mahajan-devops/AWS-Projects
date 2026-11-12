# AWS Projects

Hands-on AWS projects covering networking, high availability, static hosting,
serverless automation and cost control. Each project is built by hand in the
AWS console or CLI first, then automated (Terraform versions live in
[Terraform-projects](https://github.com/raghav-mahajan-devops/Terraform-projects)).

## Projects

| # | Project | AWS services | Status |
|---|---|---|---|
| 1 | **Static website on S3 + CloudFront**: private S3 bucket served through CloudFront with Origin Access Control, deployed automatically by GitHub Actions using OIDC (no access keys) | S3, CloudFront, IAM (OIDC), ACM, Route 53 | Planned |
| 2 | **Highly available 3-tier web app**: Flask + MySQL app behind an Application Load Balancer, Auto Scaling Group across 2 AZs in private subnets, RDS in isolated subnets, access via SSM (no SSH) | VPC, ALB, EC2 Auto Scaling, RDS, NAT Gateway, Secrets Manager, SSM, CloudWatch | Planned |
| 3 | **Serverless EC2 scheduler**: Lambda stops/starts instances tagged `AutoStop=true` on a schedule and emails a summary, to cut dev costs | Lambda (Python, boto3), EventBridge Scheduler, SNS, IAM, CloudWatch Logs | Planned |

## Standards for every project

- **Cost safety first:** an AWS Budgets alert and billing alarm are set before
  building anything. Expensive resources (NAT Gateway, ALB, RDS) are destroyed
  the same day.
- **Tagging:** every resource is tagged `Project=<name>` and `Owner=raghav`, so
  costs and leftovers can be traced.
- **Least privilege:** IAM roles instead of access keys; no credentials in this repo.
- **Documentation:** each project folder has an architecture diagram, setup
  steps, screenshots, a cost estimate, a cleanup section and a
  `TROUBLESHOOTING.md` log of the issues hit and how they were fixed.
