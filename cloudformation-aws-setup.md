# Implementing IaC with AWS CloudFormation

## **Introduction**
AWS CloudFormation enables Infrastructure as Code (IaC) by allowing users to define and deploy AWS resources using YAML or JSON templates. This guide walks through creating an **EC2 instance** using CloudFormation.

## **1. Prerequisites**
- **AWS account** with IAM permissions for CloudFormation and EC2.
- **AWS CLI installed and configured** (`aws configure`).
- **CloudFormation template (`ec2-instance.yml`)**.

## **2. Create the CloudFormation Template**
The CloudFormation YAML template defines an EC2 instance with security group settings.

### **File: `ec2-instance.yml`**
```yaml
AWSTemplateFormatVersion: "2010-09-09"
Resources:
  MyEC2Instance:
    Type: "AWS::EC2::Instance"
    Properties:
      ImageId: "ami-0c55b159cbfafe1f0"  # Replace with a valid AMI ID
      InstanceType: "t2.micro"
      Tags:
        - Key: "Name"
          Value: "CloudFormationEC2"
Deploy the CloudFormation Stack
Run the following command to create a CloudFormation stack:

sh
aws cloudformation create-stack --stack-name MyEC2Stack --template-body file://ec2-instance.yml
4. Check Deployment Status
Verify the status of the stack:

sh
aws cloudformation describe-stacks --stack-name MyEC2Stack
5. Delete the CloudFormation Stack (Optional)
To remove the stack and delete the EC2 instance:

sh
aws cloudformation delete-stack --stack-name MyEC2Stack
yaml
Copy
Edit

---

## **3. Create the CloudFormation YAML Template (`ec2-instance.yml`)**  

### **Create the File**  
```sh
touch ec2-instance.yml
Open and Edit the File
sh
code ec2-instance.yml
Content for ec2-instance.yml
Copy and paste the following CloudFormation YAML template:

yaml
AWSTemplateFormatVersion: "2010-09-09"
Resources:
  MyEC2Instance:
    Type: "AWS::EC2::Instance"
    Properties:
      ImageId: "ami-0c55b159cbfafe1f0"  # Replace with a valid AMI ID
      InstanceType: "t2.micro"
      Tags:
        - Key: "Name"
          Value: "CloudFormationEC2"
