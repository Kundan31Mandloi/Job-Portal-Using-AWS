# Job-Portal-Using-AWS
**NOTE:** This Service is created using Console, Will add IAC in future probably using Typescript (AWS-CDK)

**Description:**
This application can be used as a job portal, which is built using AWS Components Services. This is basic application just to understand some of the AWS services such as VPC, Subnet(Private/Public), Ec2, Security Group, Network Access Control List, NAT Gateway, Routing Table, Internet Gateway, DynamoDB, S3, Lambda Function, 
SQS, VPC Endpoint & Route 53
I will try to implement IAC for the same architecture in near future and update it here.

**Important**
There may exist some of the better architecture than this, which may perform same task in better way but I have implemented this from the learning point of view, so that AWS Sevice can be visualized in real life scenario

**Assumption/Pre-Requisite**
We will have web application deployed into our Web EC2 instance, which will be sample form(Can have log-in using email or pwd, which can bring KMS or any other encryption in scenario or Secret Manager to keep it simple) and take user's input such as name, education details, dob, work experience details etc along with Resume File

**Working**
1. User will access application via some meaningful name(DNS, which can be registerd using Route 53 using different Route Policies)
2. 
