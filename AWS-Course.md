# Cloud Fundamentals

What is the Cloud Computing? 

- Cloud computing is the **on-demand delivery** of computing power, database storage, applications and other IT resources. 

- Cloud Services are provided with a **Pay-as-you-go Pricing**

- You can provision exactly the right **type and size** of computing resources you need and access them **instantly!**
#
## Cloud Deployment Models


![Alt text](Images/AWS%20cloud%20models.PNG)

#
## Cloud Characteristics

- On demand service, provisioning resources without human interaction.
- Broad Network access, resources available over the network can be acceseed by multiple client platforms. 
- Multi-tenancy, multiple customers can share the same infrastructure and are serviced from the same physical resources. 
- Rapid scalability, you can quickly and automatically aquire and dispose of resources based on demand. 
- Measured service, usage is measured so users pay correctly for what they use. 
#
## IaaS, PaaS, and SaaS
![Alt text](Images/iaas-paas-saas-hierarchy-diagram.jpg)

- IaaS (Infrastructure as a Service): Provides the infrastructure such as virtual machines and other resources like virtual-machine disk image library, block and file-based storage, firewalls, load balancers, IP addresses, virtual local area networks etc.

- PaaS (Platform as a Service): This is used for applications, and other development, while providing cloud components to software. This includes development tools, database management, business intelligence (BI) services, etc.

- SaaS (Software as a Service): In this service model, the cloud-based applications are provided to the user, as a service on demand. It is a single instance of the service running on the cloud and multiple end users are serviced.

![Alt text](Images/cloud-services-compared-to-transportation.jpg)

- On-premises IT infrastructure is like owning a car. When you buy a car, you’re responsible for its maintenance, and upgrading means buying a new car.

- IaaS is like leasing a car. When you lease a car, you choose the car you want and drive it wherever you wish, but the car isn’t yours. Want an upgrade? Just lease a different car!

- PaaS is like taking a taxi. You don’t drive a taxi yourself, but simply tell the driver where you need to go and relax in the back seat.

- SaaS is like going by bus. Buses have assigned routes, and you share the ride with other passengers.
![Alt text](Images/types%20of%20cloud.PNG)
#
## AWS Region Selection

**Compliance** - Data governance and legal requirements for keeping data in a region.

**Proximity** - Reduced latency for customers.

**Availability** - Services are not available in every region.

**Pricing** - Pricing varies based on region. 

![Alt text](Images/AWS%20services.PNG)

#
## AWS Responsibility
You need to understand what YOU are responsible for and what AWS is responsible for.

![Alt text](Images/AWS%20Responsibility.PNG)

# Cloud Security

There are many ways to implement security on the cloud such as: IAM, AWS access keys and more.

## IAM
IAM = Idenity and Access Managment (Global service)

**Root** users are created by default but shouldn't be used.

**Instead** create users for the organisation, these users can be grouped and provided permissions. 

![Alt text](Images/AWS%20groups.PNG)
#
### IAM Permissions

- Users or Groups can be assigned JSON documents called policies

- Policies define the permissions of the user

- Always apply the **Least privilege principle**: don't give more than a user needs. 

#
### IAM Creation

By navigating to the IAM tool, you can create users and groups. 

To create a user: 
![Alt text](Images/AWS%20IAM%20creation.PNG)

To set permissions, it's best to create a group:
![Alt text](Images/AWS%20IAM%20ADMIN.PNG)

You can now add users to this group and they will inherit all attached policies.

You can also email the login instructions to that user!

![Alt text](Images/AWS%20IAM%20Email.PNG)
#
### IAM Policies

The policy structure in JSON files:

![Alt text](Images/AWS%20IAM%20Policies.PNG)

These policies can be:

- Attached from Group: given access via a group policy

- Attached directly: given access directly with no links. 

You can also create your own policy! using either a JSON file or the visual editor. 
#
### IAM Security, Password Policy
Password policies are one of the ways you can protect your IAMs:

- Request strong passwords only
- Minimum password lengths
- Specific character types
- Require password expiration
- Prevent password re-use
#
### IAM Security, Multi Factor Authentication

MFA can be used to protect your root accounts and IAM users. 

MFA combines the password you know AND security device you own. 

![Alt text](Images/AWS%20IAM%20Security.PNG)

Even if the password is compromised, the account will not be compromised as the the physical device is required. 

MFA options: 

![Alt text](Images/AWS%20IAM%20MFA%20options%201.PNG)

![Alt text](Images/AWS%20IAM%20MFA%20options%202.PNG)

#
## AWS Access Keys, CLI and SDK

There are three ways to access AWS: 

- AWS managment console (Password + MFA)
- AWS Command line interface (CLI) (Access Keys)
- AWS Software Developer Kit (SDK) (Access Keys)

Access keys are generated through the AWS Console and are managed by the user that owns them.

![Alt text](<AWS Access Key Example.JPG>)

#
### AWS CLI

AWS CLI is a tool you can use to interact with AWS services using commands in your command-line shell. 

It gives you direct access to the public APIs of AWS services and you can develop script to manage resources. 

Logging in: 
- `aws configure`
- `<Access Key>`
- `<Secret Access Key>`
- `<Region Name>`

- `aws iam list-users` will give all users in my account
#
### AWS SDK

SDK is the Software Development Kit, it is actually integrated within your application to access and manage AWS services programmatically while supporting a large variety of languages and libraries. 


### AWS Cloudshell

Cloudshell is a terminal in the cloud and it's free to use!

You can use ACLI commands the same way! You have your own repository, you can create files and all files in this environment will stay. It can be configured and scaled. This means you can download or upload files to and from it. 


### IAM roles for AWS services

Some AWS services will need to take action on our behalf so:

IAM roles are used to assign permissions to the services.

IAM roles are similar to how users have policies.


Summary:

![Alt text](Images/AWS%20IAM%20SUMMARY.JPG)


# AWS EC2
Elastic Compute Cloud = Infrastructure as a service

Allows you to: 
- Rent virtual machines
- store data on vitual drives
- distribute load using elastic load balancers. 
- scale the services using an auto scaling group

You can configure: 

- OS, operating system, Linux, Windows, Mac and more. 

- How much computing power? CPU
- How much random-access memory? Ram
- Storage space, Network attached (EBS and EFS) or Hardware (EC2 instance store)
- Network card, speed of the card and public ip address
- Firewall rules: Security Groups
- Bootstrap script: EC2 User Data

User data: bootstrapping means launch commands when machine starts, it's only run once on it's first start. It's used to automate boot tasks such as installing updates, software, downloading files and more. IT WILL RUN AS ROOT USER. 

EC2 types: 
![Alt text](Images/aws%20ec2%20types.JPG)

### Budget Setup

You can create4 budgets using templates with a time-scale of your choosing. 

You can select for example $10 per month with email alerts. 

### EC2 types

If you had a type named m5.2xlarge
m = instance class
5 = generation
2xlarge = size within the instance class. 

You have general purpose insatnce types which have a good balance between computing, memory and networking. 

You have compute Optimised instance types which provide high performance processors. e.g gaming servers, machine learning and more. 

You have memory optimised instance types for large data sense requiring memory (RAM)

You haqve storage optimised instances which are great for storage intensive tasks that require high read and right access to large data sets. (Databases)

### Security Groups

Security groups allow you to control how traffic is allowed in to or out of our EC2 instances. 

Secury groups only contain ALLOW rules and can reference by IP. 

They regulate access to ports, autorised IP ranges and inbound/outbound network.

Good to note: 
- Security groups can be attached to multiple instances but are locked down to a region or VPC. 
- Security groups live "outside" of the EC2. 
- All inbound traffic is blocked by default and all outbound traffic is authorised by default. 

Ports: 22 = ssh, 21 = FTP, 22 = SFTP, 80 = HTTP, 443 = HTTPS, 3389 = RDP. 

### SSH

Secure Shell Connection, manual setup.

When using SSH, we create a `public key` and a `private key`

The Public Key is the Lock

The Private Key is the Key

- SSH is used for Mac, Linux and Windows 10 and under. 
- Putty is used for Windows 10 and later. 
- EC2 Instance Connect allows for all OS. 

### EC2 Purchasing Options

On demand instances
- Pay for what you use, billed per second or per hour, recommended for short term and uninterrupted work load. 

EC2 reserved instances
- 72% discount because you reserve a period of time, pay upfront and set the instance scope for even MORE discount. 

EC2 Savings Plan
- Discount based on long-term usage
- Commit to a certain type of usage for a long time


EC2 Spot Instances
- Can get up to a 90% discount and very cost efficient.
- Instances that you can "lose" at any point of time if your max price is less than the current spot price. 
- Useful for workloads that are resilient to failure.

EC2 Dedicated Hosts
- A physical server with EC2 instance capacity fully dedicated to your use
- Allows you to address compiance requirements and use your existing server-bound software licenses. 
- You can do either on demand or reserved. Very expensive compared to others. 

EC2 Dedicated Instances
- Instances run on hardware dedicated to you, may share hardware with other instances in the same account but you have no control over instance placement. 

Just remember that dedicated instances mean you have your own instance on your own hardware whereas dedicated host you get access to a physical server itself.

![Alt text](Images/aws%20ec2%20purchase.JPG)

### EC2 Shared Responsibility

![Alt text](Images/aws%20ec2%20responsibility.JPG)

### EC2 Exam Prep

![Alt text](Images/aws%20ec2%20exam.JPG)

## AWS EC2 Storage



### EBS Volumes

EBS volumes - Elastic Block Store, a network drive you can attach to your instances while they run, allows instances to persist data. One instance at a time and one availability zone. "Network USB sticks"

They can be detached and attached to another instance fast. Price scalable. 

### EBS Snapshots

You can take snapshots of your EBS volume at any point, this snapshot can be taken while the volume is running and the snapshots can be copied accross regions. 

Snapshots can be moved to an archive where they are cheaper but it takes 24-72 hours to restore the archive.