# AWS-Projects

Note: For billing purposes, each project is deleted after completion. Proof of project creation are screen-recorded below. Convert to 720p for a clearer view.

## Project 1 - Stateless, Fault Tolerant Workload with Launch Templates in Order to Request EC2 Spot Instances

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

## Project 2 - Serverless Workflow that Orchestrates a Message Queue-Based Microservice

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

## Project 3 - Continuous Delivery Pipeline for a Web Appplication

Project QuickTime Video: https://drive.google.com/file/d/1jhFSgiR3-FrEFEIeCZYVkffck9O7GgPM/view?usp=sharing

Application  Architecture:

![Project 3](https://github.com/jcfaith/AWS-Projects/blob/main/Project%203%20Screen%20Shot.png?raw=true)

AWS Services Used: Elastic Beanstalk, CodeBuild, CodePipeline

* Uses a version control system to store source code
* Continuous delivery pipeline will automatically deploy the web application whenever source code is updated
* Github repository titled: 
  * Forked a GitHub repository to create a new one
  * Stored code and metadata in GitHub
  * Interacted with a code repository using Git
* Used AWS Elastic Beanstalk to create and deploy a web application
  * Elastic Beanstalk will provision one or more Amazon EC2 instances when creating an environment
  * Web server software uses HTTP protocol to serve content over the Internet
* Used AWS CodeBuild to build source code previously stored in GitHub repository
  * OAuth Open protocol used to connect GitHub to AWS CodeBuild
  * CodeBuild uses the provided Buildspec to run a build
* Used AWS CodePipeline to set up a continuous delivery pipeline with source, build, review, and deploy stages
  * Will detect chances in code stored in GitHub repository, build the source code, then deploy application to Elastic Beanstalk
  * Review stage in pipeline requires a manual approval before a change is deployed
