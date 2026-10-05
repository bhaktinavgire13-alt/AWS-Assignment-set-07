Question 3:-Highly Available Web Application using EC2, ALB and Auto Scaling
Deploy a web application using EC2, an Application Load Balancer, and Auto Scaling across
multiple Availability Zones. Configure health checks and scaling parameters, access the
application through the Load Balancer DNS name, and document how AWS maintains application
availability when an instance fails.

Objective:-
The objective of this task is to deploy a web application using EC2 instances, an Application Load Balancer and Auto Scaling. The setup is designed to keep the application available even if one EC2 instance becomes unavailable.

AWS Services Used:-
- Amazon EC2
- Application Load Balancer
- Target Group
- Auto Scaling Group
- Availability Zones
- Security Groups

Architecture:-Added in screenshot folder

Steps Performed:-
1. I created EC2 instances in different Availability Zones.
2. I installed and configured the web server on the EC2 instances.
3. I created a simple web page for testing.
4. I created a Target Group.
5. I added the EC2 instances to the Target Group.
6. I created an Application Load Balancer.
7. I configured the listener for the Load Balancer.
8. I connected the Load Balancer with the Target Group.
9. I created an Auto Scaling Group.
10. I configured the required minimum, desired and maximum number of instances.
11. I configured health checks.
12. I accessed the website using the Load Balancer DNS name.
13. I checked the health status of the EC2 instances.

How the Setup Works:-
The Application Load Balancer receives requests from users and distributes them between the healthy EC2 instances.

The Target Group keeps track of the health of the EC2 instances.

The Auto Scaling Group helps maintain the required number of instances and can launch a replacement when an instance becomes unhealthy.

Testing:-
I accessed the web application using the Application Load Balancer DNS name. I also checked the health status of the instances from the Target Group.

The setup was tested to make sure that traffic could be handled by the available healthy EC2 instances.

Result:-The web application was successfully connected to the Application Load Balancer and Target Group. The EC2 instances were monitored using health checks and Auto Scaling was configured to maintain the required number of instances.

Screenshots:-Saved in the `screenshots` folder

Conclusion:-I learned how EC2, Application Load Balancer and Auto Scaling can be used together to create a more reliable web application. I also learned how load balancing and health checks help distribute traffic between available EC2 instances.

Code:-
#!/bin/bash

dnf install -y httpd

systemctl enable httpd
systemctl start httpd

cat <<EOF > /var/www/html/index.html
<!DOCTYPE html>
<html>
<head>
    <title>AWS Assignment Set 7</title>
</head>
<body>
    <h1>Welcome to My AWS Web Application</h1>
    <h2>Assignment Set 7 - Question 3</h2>
    <p>EC2 + Application Load Balancer + Auto Scaling</p>
    <p>Server: $(hostname)</p>
</body>
</html>
EOF