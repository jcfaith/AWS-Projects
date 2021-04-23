# AWS-Projects

Note: For billing purposes, each project is deleted after completion. Proof of project creation are screen-recorded below.

## Project 1 - Created a Stateless, Fault Tolerant Workload with Launch Templates in Order to Request EC2 Spot Instances

Project QuickTime Video: https://drive.google.com/file/d/1zE0L6xjXycdTbVKwWq7XxTtucpVkhkok/view?usp=sharing

AWS Services Used: EC2 Auto Scaling, EC2 Spot Instances, Application Load Balancer

* Utilized AWS account's default VPC
* Application Load Balancer (ALB) will distribute http requests to the fleet of Amazon EC2 Spot Instances created
* Workload is highly available through all 6 availability zones in the US East Region, public subnets are used, and access is provided to 120 Spot Pools
* Created a security group with Health Checks enabled that will make the ALB reachable on TCP port 80/http from any Internet IP address
* Created a launch template that includes paraments required to launch an Amazon EC2 Instance such as the Amazon Machine Image (AMI) ID and an instance type
  * Launch template version is set to latest which means that whenever I update this launch template and a new version is created in the future, the Auto Scaling group will automatically begin to use the latest version on the very next instance it needs to launch
* Spot Instances are used due to the application being stateless and fault tolerant
* Primary instance type used is c5.large 

## Project 2 - Created a Serverless Workflow that Orchestrates a Message Queue-Based Microservice

Project QuickTime Video: https://drive.google.com/file/d/1UbsbbcZbxn3Runw3nhrn-tUBlBRH78KX/view?usp=sharing

AWS Services Used: Step Functions, Simple Queue Service (SQS), Identity and Access Management (IAM), Lambda

* Will simulate inventory verification requests from incoming orders in an e-commerce application as part of an order processing workflow
* Application does not require strict ordering
* Designed a workflow using Step Functions that will request verification of inventory from a microservice
  * Microservice used is AWS Lambda
* Step Functions add a task token to the JSON payload and wait for a callback
  * JSON code appends .waitForTaskToken to resource
* IAM role allows Step Functions to access SQS
* Lambda function will retrieve messages from SQS and return a message to Step Functions that represents the result of the request

## Project 3 - Created a Continuous Delivery Pipeline for a Web Appplication

AWS Services Used: Elastic Beanstalk, CodeBuild, CodePipeline

Application Architecture:

* Uses a version control system to store source code
* Continuous delivery pipeline will automatically deploy your web application whenever source code is updated

