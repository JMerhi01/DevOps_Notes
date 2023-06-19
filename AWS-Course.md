# Cloud Fundamentals

What is the Cloud Computing? 

- Cloud computing is the **on-demand delivery** of computing power, database storage, applications and other IT resources. 

- Cloud Services are provided with a **Pay-as-you-go Pricing**

- You can provision exactly the right **type and size** of computing resources you need and access them **instantly!**
#
## Cloud Deployment Models

![Alt text](<AWS cloud models.PNG>)
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

![Alt text](<types of cloud.PNG>)
#
## AWS Region Selection

**Compliance** - Data governance and legal requirements for keeping data in a region.

**Proximity** - Reduced latency for customers.

**Availability** - Services are not available in every region.

**Pricing** - Pricing varies based on region. 

![Alt text](<AWS services.PNG>)

#
## AWS Responsibility
You need to understand what YOU are responsible for and what AWS is responsible for.

![Alt text](<AWS Responsibility.PNG>)

# IAM
IAM = Idenity and Access Managment (Global service)

**Root** users are created by default but shouldn't be used.

**Instead** create users for the organisation, these users can be grouped and provided permissions. 

![Alt text](<AWS groups.PNG>)
#
## IAM Permissions

- Users or Groups can be assigned JSON documents called policies

- Policies define the permissions of the user

- Always apply the **Least privilege principle**: don't give more than a user needs. 

![Alt text](image.png)
#
## IAM Creation

By navigating to the IAM tool, you can create users and groups. 

To create a user: 
![Alt text](<AWS IAM creation.PNG>)

To set permissions, it's best to create a group:
![Alt text](<AWS IAM ADMIN.PNG>)

You can now add users to this group and they will inherit all attached policies.

You can also email the login instructions to that user!

![Alt text](<AWS IAM Email.PNG>)
#
## IAM Policies

The policy structure in JSON files:

![Alt text](<AWS IAM Policies.PNG>)

These policies can be:

- Attached from Group: given access via a group policy

- Attached directly: given access directly with no links. 

You can also create your own policy! using either a JSON file or the visual editor. 
#
## IAM Security, Password Policy
Password policies are one of the ways you can protect your IAMs:

- Request strong passwords only
- Minimum password lengths
- Specific character types
- Require password expiration
- Prevent password re-use
#
## IAM Security, Multi Factor Authentication

MFA can be used to protect your root accounts and IAM users. 

MFA combines the password you know AND security device you own. 

![Alt text](<AWS IAM Security.PNG>)

Even if the password is compromised, the account will not be compromised as the the physical device is required. 

MFA options: 

![Alt text](<AWS IAM MFA options 1.PNG>)

![Alt text](<AWS IAM MFA options 2.PNG>)

