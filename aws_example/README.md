# AWS Presentation

## This templates create a new VPC and also an Application Load Balancer pointing to an AutoScaling Group in that VPC

Nested stacks:
* parent.yaml: points to the VPC_nested.yaml and web_nested.yaml templates and get all the parameters
* VPC_nested.yaml: creates a VPC with the following
    - 2 publics subnets in AZs a and b for the Load Balancer
    - 2 privates subnets in AZs a and b for the web servers
    - 2 privates subnets in AZs a and b for the DB servers
    - Creates an IGW, 2 NAT Gateways (for HA) and the routes for them to work
    - Security Groups for the ALB allowing HTTP and the web SG allowing the traffic from the ALB
* web_nested.yaml: creates an Application Load Balancer and an Auto Scaling Group (with a Launch Configuration that makes a simple PHP web server)
---
To use, download the templates, upload them to an S3 and modify parent.yaml to point to the correct S3 bucket
---
Working currently on:
* Add scaling policies to web_nested.yaml template
* Change from Launch Configuration to Launch Template
* Add DB template 