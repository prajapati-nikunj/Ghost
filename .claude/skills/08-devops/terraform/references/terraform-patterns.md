# Terraform Reference

## AWS Infrastructure for a Todo App
```hcl
terraform {
  required_providers {
    aws = { source = "hashicorp/aws", version = "~> 5.0" }
  }
  backend "s3" {
    bucket = "todo-terraform-state"
    key    = "prod/terraform.tfstate"
    region = "us-east-1"
  }
}

# VPC
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "5.0"
  name    = "todo-vpc"
  cidr    = "10.0.0.0/16"
  azs             = ["us-east-1a", "us-east-1b"]
  private_subnets = ["10.0.1.0/24", "10.0.2.0/24"]
  public_subnets  = ["10.0.101.0/24", "10.0.102.0/24"]
  enable_nat_gateway = true
}

# RDS
resource "aws_db_instance" "todo_db" {
  identifier        = "todo-db"
  engine            = "postgres"
  engine_version    = "16.1"
  instance_class    = "db.t3.micro"
  allocated_storage = 20
  db_name           = "tododb"
  username          = var.db_username
  password          = var.db_password
  multi_az          = true
  storage_encrypted = true
  skip_final_snapshot = false
}

# Variables
variable "db_username" { type = string; sensitive = true }
variable "db_password" { type = string; sensitive = true }
```

## Commands
```bash
terraform init     # Initialize providers
terraform plan     # Preview changes
terraform apply    # Apply changes
terraform destroy  # Tear down
```

## Rules
- Always use remote state (S3 + DynamoDB locking).
- Never hardcode secrets; use `var` + Secrets Manager.
- Use modules for reusable infrastructure.
- Tag all resources for cost tracking.
