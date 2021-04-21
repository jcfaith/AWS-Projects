# AWS-Projects

### Note: For billing purposes, each project is deleted after completion. Proof of project creation are screen-recorded below.

## Project 1 - Created a stateless, fault tolerant workload using EC2 Auto Scaling with launch templates in order to request EC2 Spot Instances

Project QuickTime Video: https://drive.google.com/file/d/1bwVJMiCi3hvpsqQFuI1M_zod7WZlX-FY/view?usp=sharing

Services Used: EC2 Auto Scaling, EC2 Spot Instances, Application Load Balancer

* Utilized AWS account's default VPC
* Application Load Balancer (ALB) will distribute http requests to the fleet of Amazon EC2 Spot Instances created
* Workload is highly available through all 6 availability zones in the US East Region, public subnets are used, and access is provided to 120 Spot Pools
* Created a security group with Health Checks enabled that will make the ALB reachable on TCP port 80/http from any Internet IP address
* Created a launch template that includes paraments required to launch an Amazon EC2 Instance such as the Amazon Machine Image (AMI) ID and an instance type
  * Launch template version is set to latest which means that whenever I update this launch template and a new version is created in the future, the Auto Scaling group will automatically begin to use the latest version on the very next instance it needs to launch
* Spot Instances are used due to the application being stateless and fault tolerant
* Primary instance type used is c5.large 

