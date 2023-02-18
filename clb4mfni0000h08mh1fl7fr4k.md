# Some AWS service basics to know

> Started DevOps pro journey. here is my learning in brief.

In this article, I will explain some AWS services in brief. in an upcoming article, I will share how to set up these services.

so let's understand

### **Beanstalk**

Lets first understand IAAS VS PAAS :

![No alt text provided for this image](https://media-exp1.licdn.com/dms/image/D4D12AQGD2ivr2B-LLA/article-inline_image-shrink_1000_1488/0/1669168198094?e=1675296000&v=beta&t=teVTNwHOMoJ4Gwj4Iti-RTEzBmGdV6EKhAvEbdtIigI align="left")

image from this link [redhat.com/en/topics/cloud-computing/what-i](http://redhat.com/en/topics/cloud-computing/what-i)[..](https://www.redhat.com/en/topics/cloud-computing/what-is-paas)

In PAAS you have to manage your app and data only and the infrastructure part is taken care of by your cloud provider.

**A**WS Elastic Beanstalk is an AWS-managed service for web applications. it is PAAS (platform as a service.).it is a simples way to deploy and scale your web app. it supports java, .net, node.js, PHP, ruby, python, go, and docker applications.

Beanstalk provides many features like auto load balancing, auto-scaling, managing platform updates, and health monitoring easily.

### **Lambda**

AWS Lambda is a serverless computing service. so what is serverless? think about what are things needed to develop and deploy an app.

*   we decide Where do we deploy the application?
    
*   What kind of server? Which OS to install?
    
*   How do we take care of scaling the application?
    
*   How do we ensure availability?
    
*   How we implement load balancers. which one to choose?
    

So these are some important points for developing and deploying an app. but in serverless, I don’t care about servers. we have to focus only on our product building.

> Serverless does not mean “ No server”.

**Features**

*   You don’t worry about infra part
    
*   Flexible scaling
    
*   Pay for use
    
*   You focus more on code
    

**AWS Lambda Supported language**

*   JAVA
    
*   Go
    
*   Powershell
    
*   C#
    
*   Node.js
    
*   Python
    
*   Ruby
    

### **Lightsail**

Aws lightsail is a compute service that helps to Build applications and websites fast at low-cost with pre-configured cloud resources.

it provides a Pre-configured development stack:- LAMP, Nginx, MEAN, and you can Run a website on WordPress, Magento, Joomla, etc easily.

you can create a website or application in just a few clicks. Automatically configure networking, access, and security environments. it offers Low & predictable monthly prices.

### **S3 bucket**

Amazon S3 (Simple Storage Service) provides object storage, which is built for storing and recovering any amount of information or data from anywhere

*   Inexpensive
    
*   Large object-storing capacity
    
*   Provide the REST API for getting access and to modify these objects.
    
*   Unlimited storage
    
*   Availability 99.99
    
*   Durability 99.999999
    

### **S3 Glacier**

it is an archived storage type in which you don't use data frequently. you can use an S3 glacier to store your Tb's of data that your use once in a while.

AWS provides different-different plans for it. if you use it once a month or once a year. S3 is a global service but we have to choose the region to provide better availability

### **Storage type**

There are two types of storage

*   Block storage
    
*   File storage
    

### **Block storage:**

Block storage chops data into blocks and stores them as separate pieces. An example of block storage is Hard disk in computers. block storage can be connected to only one host at a time.

## **EBS (Elastic Block Storage):**

Ebs is an AWS storage service that provides Easy to use, high-performance block storage at any scale. it provides 30 GB of storage for 12 months with the AWS Free Tier.

it is more Durable, The lifecycle is not tied to the EC2 Instance like instance store. you can Attach it to any ec2 instance & also you can de-attach it. it is 99.999% available.

### **Instance store:**

it creates at the time of ec2 creation. so if we terminate ec2 this storage type will also be deleted. it provides temporary block-level storage for your instance. Instance store is ideal for temporary storage like buffers, caches, and other temporary content

Data on an instance store volume persists only during the life of the associated instance; if an instance is stopped, restart, or terminated, any data on instance store volumes is lost. its Lifecycle is tied to EC2.

![No alt text provided for this image](https://media-exp1.licdn.com/dms/image/D4D12AQGdZYuLGcAPUA/article-inline_image-shrink_1500_2232/0/1669168258993?e=1675296000&v=beta&t=tKWX6Z25tfNwHmu_0o8FwHruB0HKVW3BV5E6bTvAt3A align="left")

image taken from : [medium.com/awesome-cloud/aws-difference-bet](http://medium.com/awesome-cloud/aws-difference-bet)[..](https://medium.com/awesome-cloud/aws-difference-between-ebs-and-instance-store-f030c4407387)

![No alt text provided for this image](https://media-exp1.licdn.com/dms/image/D4D12AQEBeMqlYzb6aQ/article-inline_image-shrink_1500_2232/0/1669171357096?e=1675296000&v=beta&t=uKy7GQq85isytUFQcSx3pRmyto5mK-tcj8w_UsEc3M0 align="left")

### **EFS :**

Amazon Elastic File System (Amazon EFS) provides a simple, serverless, set-and-forget elastic file system for use.

 It is built to scale on demand to petabytes without disrupting applications, growing and shrinking automatically as you add and remove files, eliminating the need to provision and manage capacity to accommodate growth. Compatibility is supported on Linux-based instances

### **FSX :**

FSX is amazon's Fully managed third-party file system optimized for a variety of workloads. With Amazon FSx, you can choose between four widely-used file systems:

*   Lustre
    
*   NetApp ONTAP,
    
*   OpenZFS,
    
*   Windows File Server
    

## **Cloud trail :**

AWS CloudTrail is an AWS service that helps you enable operational and risk auditing, governance, and compliance of your AWS account.

Actions taken by a user, role, or AWS service are recorded as events in CloudTrail. 

## **AWS config :**

AWS Config is a fully managed service that provides you with an AWS resource inventory, configuration history, and configuration change notifications to enable security and governance.

AWS Config continually assesses, audits, and evaluates the configurations and relationships of your resources.

That's it for now. I will share more as I learn. Give suggestions if any. Love to hear that