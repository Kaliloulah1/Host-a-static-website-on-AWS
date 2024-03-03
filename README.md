![Alt text](/Host_a_Static_Website_on_AWS.png)



# Host a Static Website on AWS

## Overview:
This project demonstrates the process of hosting a static HTML web application on AWS utilizing various resources and services. Below is an overview of the steps involved along with the scripts used for deployment.

1. **Virtual Private Cloud (VPC) Configuration**:
   - Configured a VPC with public and private subnets across two different availability zones for enhanced reliability and fault tolerance.

2. **Internet Connectivity**:
   - Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.

3. **Security Mechanisms**:
   - Established Security Groups to act as a network firewall mechanism, ensuring secure communication within the infrastructure.

4. **High Availability**:
   - Leveraged two Availability Zones to enhance system reliability and fault tolerance.

5. **Subnet Utilization**:
   - Utilized Public Subnets for resources like the NAT Gateway and Application Load Balancer, while positioning web servers (EC2 instances) within Private Subnets for enhanced security.

6. **Secure Connections**:
   - Implemented EC2 Instance Connect Endpoint for secure connections to assets within both public and private subnets.

7. **Internet Access for Private Subnets**:
   - Enabled instances in private subnets to access the Internet via the NAT Gateway.

8. **Web Hosting**:
   - Hosted the website on EC2 Instances.

9. **Load Balancing and Auto Scaling**:
   - Employed an Application Load Balancer and a target group for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
   - Utilized an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

10. **Version Control and Collaboration**:
    - Stored web files on GitHub for version control and collaboration.

11. **Security Certificates**:
    - Secured application communications using a Certificate Manager.

12. **Monitoring and Alerts**:
    - Configured Simple Notification Service (SNS) to alert about activities within the Auto Scaling Group.

13. **Domain Setup**:
    - Registered the domain name and set up a DNS record using Route 53.

## Deployment Script:

```bash
#!/bin/bash
# Switch to the root user to gain full administrative privileges
sudo su
# Update all installed packages to their latest versions
yum update -y
# Install Apache HTTP Server
yum install -y httpd
# Change the current working directory to the Apache web root
cd /var/www/html
# Install Git
yum install git -y
# Clone the project GitHub repository to the current directory
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/
# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws
# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd
# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

## Usage:
- Execute the provided deployment script on an EC2 instance within the configured environment to set up the static website hosting infrastructure.
 
## Reference:
- The reference diagram and deployment scripts can be found in the GitHub repository: [Host a Static Website on AWS](https://github.com/Kaliloulah1/Host-a-static-website-on-AWS.git)

## Conclusion
This setup ensures a scalable, secure, and fault tolerant environment for hosting a static web application, leveraging AWS"s robust infrastructure.



