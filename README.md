# Job-Portal-Using-AWS
**NOTE:** This Service is created using Console, Will add IAC in future probably using Typescript (AWS-CDK). 

**Description:**
This application can be used as a job portal, which is built using AWS Components Services. This is basic application just to understand some of the AWS services such as VPC, Subnet(Private/Public), Ec2, Security Group, Network Access Control List, NAT Gateway, Routing Table, Internet Gateway, RDS, S3, Lambda Function, 
SQS, VPC Endpoint & Route 53
I will try to implement IAC for the same architecture in near future and update it here.

**Important**
There may exist some of the better architecture than this, which may perform same task in better way but I have implemented this from the learning point of view, so that AWS Sevice can be visualized in real life scenario

**Assumption/Pre-Requisite**
We will have web application deployed into our Web EC2 instance, which will be sample form(Can have log-in using email or pwd, which can bring KMS or any other encryption in scenario or Secret Manager to keep it simple) and take user's input such as name, education details, dob, work experience details etc along with Resume File

**Usage**
1. Virtual Private Cloud is separte place for our services inside AWS
2. Route 53 is used for giving meaningful name to IP address and for managing the traffic using Routing Policies
3. Internet Gateway work as gatekeeper for VPC and connect VPC to the outer world
4. Routing Table define the routing of defined IP address to particular destination (e.g. IG to Public Subnet)
5. Network Access Control List(NACL) get created by default whenever we create VPC, although we can use it as extra security layer and to block some of the IP
6. Public Subnet is just a namespace, we have to define what can access it using Route table & security group and if we make it public then everything inside this will be Public and same with Private subnet
7. Security group defines which can access what
8. Ec2 instances can access the other AWS service (in our case DynamoDB & S3), so that we have VPC Endpoint in architecture.
9. As already mentioned that anything inside Private Subnet will not be accessible to outer world & vice versa, so if Ec2 instance in private subnet want to have access to IG then it can access it with NAT Gateway
10. RDS to store User details & can have unique id per user, also it stores the S3 url of resume for that particular user
11. S3 to store Resume
12. SQS will notify user via Lambda that your application has recived or just a confirmation mail to user


**Working**
1. User will access our application and can complete form along with providing the Resume
2. Resume will be stored directly in S3 using VPC EndPoint
3. Once user uploads details, details will be stored in RDS with the help DB instance & it will also store S3 url of Resume 
4. I have applied PUT Trigger on S3, so whenever something is uploaded in S3 it will send notification to SQS
5. SQS is associated with Lambda, which will be used to send confirmation mail to User
