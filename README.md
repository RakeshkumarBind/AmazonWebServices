# CLOUD COMPUTING

CLOUD COMPUTING IS THE DELIVERY OF COMPUTING SERVICES INCLUDIMNG SERVERS, DATABASES , STORAGES , NETWORKING , SOFTWARE ANALYTICS AND INTELLIGEBNCE OVER INTERNET.

Earlier we have to purchase hardware resource , servers and have to setup , manage all the security issues and maintenance and we have to employ people whuich increse cost but with the cloud computing we can easily

                  Share 
                  ------resources
                  ------deploy applications
                  ------manage databases
                  ------focus on business nedds

# TYPES OF CLOUD COMPUTING :

There are three types of cloud comuting
# 1.  SAAS (SOFTWARE AS A SERVICE)
# 2.  PAAS (PLATFORM AS A SERVICE)
# 3.  IAAS (INFRASTRUCTURE AS A SERVICE)

# SAAS : 
1. Software as a service is a cloud computing in which you dont have to manage the deployment , hardware , security , midleware, os , runtime you just have to focus on consumuing data.
2. clou8d providers provide their software for use
3. examples are GMAIL, NETFLIX , YOUTUBE , PUBG , PAYPAL

# PAAS :
1.Platform as a service cloud computing is one wghich you will be provided wioth the platform you just have to deploy your code theat is applicatuion and you can consume it.
2.Just focus on Application and data.
3.Everything eklse is managed by cloud provider.
4.Examples are WORDPRESS, HEROKU, SAP , AMAZON RDS(RELATION DATABASE SERVICE) ----> RDS for installingg database services like Mysql

# IAAS :
1.In Infrastucture as a service you are going to provision your own system in the cloud.
2.You can configure your operating system , data , runtime, middle ware , application.
3.You dont have to worry about hardware resource,networking,storage,vitualization,servers.

# BENEFITS OF AWS CLOUD :
1.Dont need huge money for setting up data centers for running your application or web servers you can use aws cloud based on pay as you go model.
2.High spped and agility i.e you can spped up your system whenever you need like increse cpu , memory , storage.
3.Less cost .
4.No maintenance cost.
5.Go global with services like s3 bucket
6.Stop guessing capacity you can scale up and down using auto scaling groups.


# RESPONSIBILITY :
![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/1b8999b9-59bf-49eb-b4ed-48d9d3aec958)


# NETWORKING :
##   VPC VIRTUAL PRIVATE CLOUD 

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/21da6838-572d-4518-847c-ea08eabdcbdd)

TWO vpc cannot communicate with each other because they are isolated but they can communicate if configured.

VPC cannot extend over multiple reguions.

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/65109c55-d6dd-4419-8ba0-09cec2648207)


## SUBNETS 
It is a network within a network.
It is a logical division of network to smaller network.
with the help of subnet mask we can know the available ip address.
255.255.255.0      192.168.1.0/24  it indicates the 4 octet i can be occupied from 0-255 as 1 octet in binary is represented by 8 bytes so total of 32 are there.

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/ad31840a-447c-4ed8-bf4c-28075444c143)





# INTERNET GATEWAY

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/edd8d0c7-2270-48f3-98a6-d6c6a64a932c)




# What is the difference between public subnet and private subnet ?
                    1.It is the route table that makes the difference .
                    2.Public subnet routes the traffic to internet gateway.
                    3.Private subnet routes it locally.
                    4.Public subnet is exposed publically while private is not exposed publicly.





![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/381bf7fb-129c-4268-85cc-72b0f72b4f63)


# CONNECTING TO YOUR INSTANCE VIA SSH 
                                           ssh -i ky.pem user@public ip ( make sure to change the permission of key to 700 as it is not encrypted so anyone can have access to it )
                                           by default user name is ec2-user
                                    

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/48cc2605-bc43-49de-870b-dcece8940d0c)


![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/c579d568-1b12-48ef-917d-35d84aeca2a6)


![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/36ad1f62-9371-4157-ae62-3e7b1cc01d02)




# ec2 instance

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/df244dcd-d57e-4d4d-b4b6-9dc696df3c5e)

Key pair are used as an authenticatio  for accesing instance

public keys are inside the instance while private key is inside the client sysytem here your laptop.

# Access reagin private key if it is lost using the private key of other instances.

To do so you nedd two instance one whose private key you have and another one whose private key is lost.

Firstly i am going to connect to my instance whose private key i have 

terminal : ssh -i downloads/key.pem ec2-user@publicipaddressofinstance
connected successfully

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/ca3ae168-2cb0-4e1f-9d3a-31f4de5be647)


cd /home/ec2-users/.ssh
cat authorized keys
copy it ------------------> this is the public key of that instance.

Now you have to put this public key to the instance whose private key is lost.

Now using aws console direct instance connect for browser i am going to cionnect my instance.

cd /home/ec2-users/.ssh
cat authorized keys
vi autghorizd keys

Paste it 

Now with the terminal: ssh -i oldkey ec2-user@ip


# REGAIN ACCES IN EC2 INSTANCE IF PUBLIC KEY IS LOST

We can get public key using private key
go to terminal 

ssh-keygen -y -f locationofprivatekey   -----------------> returns the public key associated with the private key.

Go to the ec2 instance using direct connect from the aws console and then 

cd /home/ec2-user/.ssh
cat authorized keys
vi authorized keys
paste the output of keygen or check whether it matches the previous one if it is already tere


# CONNECTING LINUX EC2 VIA SERIAL CONSOLE :

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/f8e331df-efb9-4a6b-ac6e-42de2e61feb3)

## NOTE : T2.MICRO DOES NOT SUPPORT SERIAL CONSOLE

CAHNGE INSTANCE TYPE FROM T2.MICRO TO T3.MICRO

Now only running instance have the serial console access so make sure to start the instance.

Now go to ec2 dashboard -------> account attributes ----------> serial conole (by default it is prevented beacause anyone is not allowed)

------> allow serial console

Now i am going to do ssh the instance or vitual machine and create a user

before that go to the directory where i have stored the krivate key

ssh -i key.pem ec2-user@ipaddresoftheinstance

sudo adduser serialadmin
sudo passwd

The Linux operating system has a special group named wheel. The wheel group is intended for all users who should be granted superuser privileges upon request. The wheel group will normally exist upon installing Linux. You normally will not need to create this group, although you may if the group does not already exist.

usermod -aG wheel serialadmin

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/a0b08914-d3fc-421f-b4be-c506deb74c69)

sudo nana /etc/ssh/sshd_config
crtl + w to seearch
Password_authentication yes 
ctrl + x to exit and save
sudo systemctl restart sshd

Now i can access it without providing the key [pair 

ssh serialadmin@ip
passwd : type the password

Now go to console to access serial console

Instance -----> action ------> monitor and troubleshoot -----> ec2 serial consp;e

## EC2 Serial Console for Linux instances

With the EC2 serial console, you have access to your Amazon EC2 instance's serial port, which you can <b> use to troubleshoot boot, network configuration, and other issues</b>. The serial console does not require your instance to have any networking capabilities. With the serial console, you can enter commands to an instance as if your keyboard and monitor are directly attached to the instance's serial port. The serial console session lasts during instance reboot and stop. During reboot, you can view all of the boot messages from the start.

Access to the serial console is not available by default. Your organization must grant account access to the serial console and configure IAM policies to grant your users access to the serial console. Serial console access can be controlled at a granular level by using instance IDs, resource tags, and other IAM levers. For more information, see Configure access to the EC2 Serial Console.

The serial console can be accessed by using the EC2 console or the AWS CLI.



## ADDING IAM POLICIES 

Go to policies (IAM)
Create new policies 

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/18b6f852-4822-4c69-9b40-a2ec9bd15668)

add above json format

and then attach the policies to user or group.

hera user so attach the users.


# window serial console

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/06e82120-c3c1-4959-9032-7f31c3031989)

  1. Connect to the window instance using rdp client.
  2. retrieve the password from the private key.
  3. connect to the window instance with administrator user.
  4. computer management ------> user --------> new user ( user cannot change password option ).
  5. now open command prompt and enable sac and boot menu .
  6. reboot the system using shutdown /r /t 0 (restart time 0s)
  7. and now connect the rdp again but this time provide the user as member of administrator group
  8. computer management --- > local and groups ----> users -----> group add (administrator)
  9. foolow the steps to diable the ssh and using console try to enable it



# Creating launch instance template

Launcgh template are used to create configured instance so that same seting should not be provided each time for creating same type of instance .

ec2 dashboard ------> instance -------> launch template

# AUTOSCALING 

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/5e348ec9-f759-4e3b-9225-9b4b063d1771)

Auto Scaling Groups (ASG) contains a collection of EC2 instances that are treated as a group for the purpose of automatic scaling and management. Scaling out is when we add server, scaling in is when we remove server and scaling up is when we increase the size of an instance.

Automatic scaling can occur via

Capacity Settings
Health Check Replacements
Scaling Policies

Capacity Settings : The simplest way to use Auto Scaling Group is through Capacity Settings.

The size of an ASG is based on Min, Max and Desired Capacity. Min is how many EC2 instances should at least be running. Max is the number of EC2 instances allowed to run. Desired capacity is how many EC2 instances, you want to run ideally. ASG will always launch instances to meet minimum capacity.

Health Check Replacements : We can also achieve auto scaling through Health Check. Health check can be run on EC2 or ELB instances. ASG will perform a health check on EC2 instances to determine if there is a software or hardware issue. If an instance is unhealthy ASG will terminate that instance and launch new one. For ELB type, the health check is performed on ELB health check, which can be performed by a ping to endpoint. If it does not get the desired response, let’s say 200 OK, it will assume that the instance is unhealthy, hence spin up new one.

Scaling Poilicies : The last way by which ASG is triggered through scaling policies. First type of scaling policy is Target Tracking Scaling policy which maintains a specific metric at a target value, e.g., if average CPU utilization exceeds 80%, then add another instance. Its either Scaling out — Adding more instances or Scaling in — removing instances. The second type of scaling policy is Simple Scaling Policy, which scales when an alarm is breached.

ASG Use Case : Let’s say we have one EC2 instance is running and a lot of traffic hitting our domain from internet. Route%3 points that traffic to our load balancer. The load balancer sends that traffic to the target group. The target group associated with our ASG and sends the traffic to the insatnces associated with the ASG. The ASG scaling policy will check, whether the resource utilization exceeds 80%. Then the scaling policy decides we need another instance and it launches a new EC2 instance with the associated launch configuration to our ASG.

Launch Configuration : A launch configuration is an instance configuration template taht an Auto Scaling Group uses to launch an EC2 instance. It is similar as to launching an instance, only saving a template for later use. Launch configuration cannot be edited, whenever you need to update the launch configuration, you need to create a new one.

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/a9c41ccb-c71e-4df0-be9e-9320a7b665fa)

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/998ae1b9-21d2-4c91-a8a4-20d5ec841d08)

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/07ed1ba3-30fe-468b-a790-8ddd41dc0933)

NACLs vs. Security Groups
NACLs and Security Groups (SGs) have very similar purposes. They filter traffic based on rules, to ensure that only authorized traffic is routed to its destination. Here we will highlight the differences between the two. Below is a high-level graphic that shows their usage and contrasts the two technologies.



Image comparing a NACL to a  Security Group

## NACLs
NACLs are used to controll access to network resources. They sit on subnets and evaluate traffic based on set rules, then determine whether or not that traffic should be allowed to continue. This applies traffic-based access control to your network, and is a powerful way to help secure your environment.

NACLs are “stateless”and require you to create separate rules for both  incoming and outgoing traffic. Just because a particular data stream is allowed in, doesn’t mean it will be allowed out.

NACLs are processed in number order. Therefore, if you need traffic to go both in and out of a protected subnet, you will  need to write rules for both directions.

What is particularly useful about NACLs, is that they are automatically applied to anything that falls under their umbrella. There is no need to apply NACLs to individual resources as they are created.

Security Groups
Security Groups apply to EC2 instances and act as a host-based firewall. Like NACLs, they utilize rules that determine if traffic going to or from a given EC2 instance should be allowed.

This provides granular traffic control for resources that have specific network requirements. Security Groups, unlike NACLs, are stateful; this means that any traffic allowed into your EC2 instance, will automatically be allowed out, and vice versa. All security groups rules are evaluated simulataineously; if no ALLOW exists, then traffic will be blocked.

Security Groups need to be applied at the time of resource creation and must be explicitly configured. This means that planning is necessary in order to ensure functional application of traffic blocking rules.

## Similarities and Differences
Both NACLs and Security Groups utilize rules that prevent unwanted traffic in your environment. The rules themselves also look very similar. However, one difference between them, is that NACLs allow for DENY rules to be created.

The largest difference, though,  is where they are applied. This is important, because it helps define their function and how they should be used. NACLs are applied at the subnet level, while Security Groups are applied at the EC2 level. NACLs protect the network while Security Groups help protect the resource. This helps shape your security strategy.

As NACLs are higher in the architecture, they apply to a much wider group of resources. Any rule you create will therefor affect the operation of every resource in the subnet. Security Groups on the other hand, only affect the EC2 instances that they are applied to.

Despite their differences, these two layers work together to create overall defense-in-depth for your cloud environment. When planned appropriately, NACLs can remove the traffic burden from the subnet, improving security and optimizing performance.

They can also provide a means of troubleshooting, as layering traffic makes it easier to segment and investigate. For example, when investigating suspicious traffic: it’s easier to look through the logs of a smaller network segment,  as  you know that it would be impossible for traffic to have gone elsewhere.

Unfortunately, they occasionally work against one other. Bad planning and maintenance can create a web of rules that can be almost impossible to untangle. It is in your best interest to follow the guidance around applying these services, in a way that is effective and maintainable.



<b> NACL ARE ASSOCIATED WITH SUBNETS WHILE SECURITY GROUPS ARE ASSOCIATED WITH RESOURCES AND INSTANCE </b>

VPC racks and server when we want to create our own infrastructure than we can use vpc racks while using server we can add resource.Both are installed on our local premise but we have to configure it and connect to our regions over vpc networks we have both on premise network as well as internet our direct connect over regions .


# STORAGES :

There are different types of storages
    1.Elastic block storage
    2.file 
    3. Object S3 bucket

  ![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/df1ef952-0acc-440b-a822-2f7692e34407)

  ## S3 bucket has many storage classes:
                                      ##   1.S3 standard ---------> Access frequently in millisecond , example:webserver
                                     ##   2.S3 INFREQUENT ACCESS S1A -----------> Not frequently but in millisecond
                                   ##     3.S3  ONE XONE INFREQUENT ACCESS --------> Only differeence from above is that it is stored in single availability zone while other are backed up in multiple availabiility zines
                                     ##   4.S3 GLACIER ----------> Archival group for storing data for longer duration in milliseconds
                                    ##    5.S3 GLACIER FLEXIBLE -----> Longer duration archival dtaa but you select type expedite---5 mn retrieval time  standard 20 min and 2 hr
                                    ##    6.S3 GLACIER DEEP ARCHIVAL ACCESS -----> Cheaper 1 dollar per tb per kmonth but before retrival we have to move the data from the other stoerage to normal and than access takes upto 12 hr to 24 hr
                                   ##     7.S3 intelligent ------> automatically selecvt storage classes based on the needs.
                                   ##     8.Amazon Outpost ---------> Physicall to your premuise


## Infrequent access -----> more than 30 days
## archive acces----------> more than 90
## deep archive ----------> more than 180 days


# DATA LIFE CYCLE POLICY IN S3 BUCKET


# MOUNTING EFS 

## 1. Go TO efs SERVICE
   2. create elastic file system
   3. make sure to create the efs in same region where your ec2 instance is created
   4. You can create replicatiuon of your efs
   5. Now you can select the type use elastic to upscale whenever workload increases.
   6. Use provisioned when you know the exact workloads.
   7. Now launch the ec2 instance and install the efs utility using command : sudo yum install amazon-efs-utils
   8. Now create the mount point for munting the efs
   9. Now go to efs console and click on attach there you will find the command for mounting via dns and ip .
   10. Copy and paste in ec2 instance
   11. There you will find error.
   12. To resolve it go to efs networking there you will find the security group where nfs for instance is not enabled add inbound rules nfs and source = security group of ec2 instance
   13. Now copuy paste the mount command and it ios mounted succesfull. 

## sudo yum install -y amazon-efs-utils

# AWS SNOW FAMILY

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/11d918f0-d1af-4708-911b-a3e375eb6621)

<b> Purpose-built devices to cost effectively move petabytes of data, offline. Lease a Snow device to move your data to the cloud.</b>

AWS Snow Family key features
Each feature listed below are standard features across each device type. To learn more about AWS Snowcone or AWS Snowball device specifications unique to each device type, visit their feature pages.
AWS Snow Family key features
Each feature listed below are standard features across each device type. To learn more about AWS Snowcone or AWS Snowball device specifications unique to each device type, visit their feature pages.
On-board computing
Snow Family devices have computing resources to collect and process data at the edge. Devices can support Amazon EC2 instances, AWS IoT Greengrass functions, and Kubernetes deployments on Amazon EKS Anywhere.
End-to-end tracking
Each device uses an E-Ink shipping label for easy tracking and automatic label updates for return shipping using Amazon Simple Notification Service (SNS), text messages, and via the AWS Console.
Simple management and monitoring
AWS OpsHub is a complimentary graphical user interface (GUI) available to makes it easy to setup and manage Snow devices. Rapidly deploy edge computing workloads and migrate data to the cloud. Download AWS OpsHub here.
Encryption
All data moved to AWS Snow Family devices is automatically encrypted with 256-bit encryption keys that are managed by the AWS Key Management Service (KMS). Encryption keys are never stored on the device so your data stays secure during transit.
Secure erasure
Once the data migration job is complete and verified, AWS performs a software erasure of the device that follows the National Institute of Standards and Technology (NIST) guidelines for media sanitization.
NFS endpoint
Applications can work with Snow Family devices as an NFS mount point. NFS v3 and v4.1 are supported so you can easily use Snow devices with your existing on-premises servers and file-based applications.
Anti-tamper & Tamper-evident
AWS Snow devices feature a Trusted Platform Module (TPM) that provides a hardware root of trust. Each device is inspected after each use to ensure the integrity of the device and helps preserve the confidentiality of your data.

# Creating a static web hosting on s3 bucket 

STEPS: https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html
       1. Create a s3 bucket with default configuration
       2. Now enable static web hosting from properties of S3 bucket.
       3. Add permission ----> allow all public access 
       4. Only allowing the public is not enough we have to add bucket policy to get object from the s3 buckeyts : {
   ## "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
      5.Create the index.html file from chatgpt : Create a web page for grocesry store.include htpl code for webpage and create a beautifull web page .
      6. Edit the index.html by pasrting the url of the object available in s3 bucket.
      7.Now add the index.html file in root of s3 bucket 
      8. Now from the properties you will get the link of static web hosting and you can see the result.

SUCCESSFULLY CREATED

# DATABASES IN AWS

There are two types of databases
1. Relational Database --------> Haviong relatuions like mysql, oracle
2. Non Relational Database -------> Documents not relational like mongodb


![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/a3c18c20-5e29-461f-ab1a-869fc3ade42c)

![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/e0c3e5a3-be4f-48a2-a372-760790631ffd)




## Note : IN amazon rds we have 2 security group
one of the security group is attached to rds to allow inbound rules to connect all the instance having this security group
one of the security group is attched to instance hich will have the outbound rules for connecting to thr datavbases.


# MONITORING TOOLS

# CLOUD TRAIL 
Logs events in cloud trail by default 
![image](https://github.com/RakeshkumarBind/AmazonWebServices/assets/109387080/19b8bc9f-2720-4012-b960-7f57cd0c29e8)


