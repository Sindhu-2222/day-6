Examples of IaC in Action
Example 1: Terraform for AWS Infrastructure
A Terraform script to provision an AWS EC2 instance:
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
This script ensures every deployment results in the same EC2 configuration.

Example 2: Ansible for Server Configuration
An Ansible playbook to install and start an Nginx web server:
- name: Install and Start Nginx
  hosts: webservers
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
    - name: Start Nginx
      service:
        name: nginx
        state: started
This guarantees that all servers in the "webservers" group have Nginx installed and running.

