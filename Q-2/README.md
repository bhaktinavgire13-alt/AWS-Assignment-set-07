Question 2:-AWS Network Architecture for a Web Application
Create a complete AWS network architecture for a web application using a custom VPC, two
Availability Zones, public and private subnets, Internet Gateway, NAT Gateway, route tables, and
Security Groups. Provide an architecture diagram and explain the purpose of each networking
component.

Objective:-
The objective of this task is to create a basic and secure network structure in AWS using a VPC, public and private subnets, Availability Zones, Internet Gateway, NAT Gateway, route tables and Security Groups.

AWS Services Used:-
- Amazon VPC
- Availability Zones
- Public Subnets
- Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups

Network Structure:-
Custom VPC
│
├── Availability Zone 1
│   ├── Public Subnet
│   └── Private Subnet
│
└── Availability Zone 2
    ├── Public Subnet
    └── Private Subnet

Steps Performed:-
1. I created a custom VPC.
2. I created public and private subnets.
3. I placed the subnets across two Availability Zones.
4. I created an Internet Gateway and attached it to the VPC.
5. I created a NAT Gateway in a public subnet.
6. I created route tables for the public and private subnets.
7. I added the required routes to the route tables.
8. I associated the route tables with the appropriate subnets.
9. I configured Security Groups to control network traffic.
10. I checked the complete VPC configuration from the AWS Console.

Components Used:-
VPC:
A VPC provides a separate network environment for the AWS resources.

Public Subnet:  
The public subnet is used for resources that need internet access.

Private Subnet:  
The private subnet is used for resources that should not be directly accessible from the internet.

Internet Gateway: 
It allows resources in the public subnet to communicate with the internet.

NAT Gateway: 
It allows resources in private subnets to make outbound internet connections.

Route Table:  
It decides where network traffic should be sent.

Security Group:  
It controls the inbound and outbound traffic for AWS resources.

Testing:-
I checked the VPC, subnets, route tables, Internet Gateway, NAT Gateway and Security Groups in the AWS Management Console to make sure they were configured correctly.

Result:-
The VPC network was created with public and private subnets across two Availability Zones. The required networking components were also configured.

Screenshots:-Saved in the `screenshots` folder.

Conclusion:-
I learned how to create a VPC and divide it into public and private subnets. I also learned how Internet Gateway, NAT Gateway, route tables and Security Groups are used to manage network connectivity and security in AWS.