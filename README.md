i# AWS Basic Cloud Networking Project
## Project Overview
This project creates a basic cloud network infrastructure on AWS using Terraform. It includes:
A custom Virtual Private Cloud (VPC)
Public and private subnets
An Internet Gateway for internet access in the public subnet
A NAT Gateway to allow limited internet access from the private subnet
Route tables and associations
Security groups for access control
This setup is foundational for cloud infrastructure, demonstrating an understanding of VPC networking, subnetting, and infrastructure as code (IaC) principles.
## Architecture
![Architecture Diagram](link_to_architecture_diagram_if_any)
### Resources Created
**VPC** with CIDR `10.0.0.0/16`
**Public Subnet** with CIDR `10.0.1.0/24`
**Private Subnet** with CIDR `10.0.2.0/24`
**Internet Gateway** for public subnet internet access
**NAT Gateway** for private subnet internet access via the public subnet
**Route Tables** for public and private subnets
## Prerequisites
An AWS account with appropriate permissions (EC2 and VPC access)
AWS CLI installed and configured with IAM user credentials
Terraform installed on your local machine
## Setup Instructions
**Clone the Repository**
   ```bash
   git clone https://github.com/your-username/aws-basic-cloud-network.git
   cd aws-basic-cloud-network
Configure AWS CLI
Ensure your AWS CLI is configured with valid credentials.
aws configure
Initialize Terraform
Initialize the Terraform project to download necessary providers and plugins.
terraform init
Apply the Terraform Configuration
Run the following command to create the resources:
terraform apply
Review the plan and type yes to confirm.
Verify the Resources in AWS Console
Go to the AWS Console and check the VPC, subnets, route tables, and gateways to ensure everything was created as expected.
Clean Up (Optional)
To avoid any charges, you can destroy the resources when you’re done:
terraform destroy
Problems Encountered and Solutions
Error: command not found: brew
	•	Problem: Homebrew was not installed on the system, which prevented Terraform installation via Homebrew.
	•	Solution: Installed Homebrew using the following command:
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" 	•	After installing Homebrew, Terraform was installed successfully.
Error: command not found: terraform
	•	Problem: Terraform was not installed on the machine.
	•	Solution: Installed Terraform using Homebrew:
brew install terraform
Error: No valid credential sources found
	•	Problem: Terraform could not locate AWS credentials to authenticate API requests.
	•	Solution: Configured the AWS CLI by running aws configure and providing the AWS Access Key ID and Secret Access Key.
Error: AccessDenied while listing S3 buckets
	•	Problem: The IAM user did not have permissions to perform s3:ListAllMyBuckets due to restricted policies.
	•	Solution: Added the AmazonS3ReadOnlyAccess policy in IAM for the user.
Error: Unauthorized to create VPC resources
	•	Problem: The IAM user lacked permissions for creating VPC and EC2 resources.
	•	Solution: Attached the AmazonEC2FullAccess policy to the IAM user to allow creation of VPC and subnet resources.
Warning: Terraform Version Outdated
	•	Problem: A warning indicated that the installed Terraform version was out of date.
	•	Solution: Although it was not critical, the latest Terraform version can be installed from Terraform’s official download page if needed.
Outputs
Upon successful deployment, Terraform will output:
	•	VPC ID: The ID of the created VPC.
	•	Public Subnet ID: The ID of the public subnet created within the VPC.
Example:
Outputs:
public_subnet_id = "subnet-xxxxxxxxxxxxxxxxx"
vpc_id = "vpc-xxxxxxxxxxxxxxxxx"
Repository Structure
aws-basic-cloud-network/
├── main.tf         # Main Terraform file with resource definitions
├── variables.tf    # Variables used in Terraform configuration
├── outputs.tf      # Outputs displayed after deployment
└── README.md       # Project documentation
Conclusion
This project demonstrates the creation of a basic cloud network using AWS and Terraform. It provides hands-on experience in VPC configuration, subnetting, and working with Infrastructure as Code. Additionally, it helps to understand common permission-related issues and how to troubleshoot them when working with AWS IAM.
