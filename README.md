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






   
