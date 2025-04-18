# Terraform-AWS-3-Tier-Architecture
Directory Structure:
aws-terraform-infra/
├── main.tf
├── variables.tf
├── outputs.tf
└── modules/
    ├── vpc/
    ├── ec2/
    └── rds/
Key Script:
# main.tf
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  cidr    = "10.0.0.0/16"
  subnets = ["10.0.1.0/24", "10.0.2.0/24"]
}

module "ec2" {
  source      = "./modules/ec2"
  instance_type = "t3.medium"
  vpc_id      = module.vpc.vpc_id
}

    
