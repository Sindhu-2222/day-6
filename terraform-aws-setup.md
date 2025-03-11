# Setting Up an AWS EC2 Instance Using Terraform

## **Prerequisites**
Before starting, ensure you have:
- An **AWS account** with an **IAM user** configured.
- **Terraform installed** on your local machine.
- AWS CLI installed and configured (`aws configure`).

## **1. Initialize a Terraform Project**
Create a new directory and navigate into it:
```sh
mkdir terraform-aws && cd terraform-aws

Create a Terraform configuration file:

sh
touch main.tf
Write a Basic Terraform Configuration
Open main.tf and add the following configuration:

h
Copy
Edit
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0" # Replace with a valid AMI ID
  instance_type = "t2.micro"

  tags = {
    Name = "TerraformEC2"
  }
}
3. Initialize Terraform
Run:

sh
Copy
Edit
terraform init
4. Plan the Deployment
To check the execution plan:

sh
Copy
Edit
terraform plan
5. Apply the Configuration
Deploy the EC2 instance:

sh
Copy
Edit
terraform apply -auto-approve
6. Verify the EC2 Instance
Find the instance in the AWS Management Console under EC2.

7. Destroy the Infrastructure (Optional)
To delete the instance:

sh
Copy
Edit
terraform destroy -auto-approve
bash
Copy
Edit

### **4. Create the Terraform Configuration File (`main.tf`)**  
Run:  
```sh
nano main.tf
Then, open it:

sh
code main.tf
Content for main.tf
Copy and paste the following:

hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0" # Replace with a valid AMI ID
  instance_type = "t2.micro"

  tags = {
    Name = "TerraformEC2"
  }
}