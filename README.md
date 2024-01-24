# Host a Static Website on AWS

## Overview

This DevOps project showcases the hosting of a static HTML web app on AWS, utilizing a set of resources and configurations detailed below. 

## Project Resources and Configurations

1. **Virtual Private Cloud (VPC):**
   - Configured a VPC with both public and private subnets across two different availability zones.

2. **Internet Gateway:**
   - Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.

3. **Security Groups:**
   - Established Security Groups as a network firewall mechanism.

4. **Availability Zones:**
   - Leveraged two Availability Zones to enhance system reliability and fault tolerance.

5. **Public Subnets:**
   - Utilized Public Subnets for infrastructure components like the NAT Gateway and Application Load Balancer.

6. **EC2 Instance Connect Endpoint:**
   - Implemented EC2 Instance Connect Endpoint for secure connections to assets within both public and private subnets.

7. **Web Servers Placement:**
   - Positioned web servers (EC2 instances) within Private Subnets for enhanced security.

8. **Internet Access for Private Subnets:**
   - Enabled instances in both the private Application and Data subnets to access the Internet via the NAT Gateway.

9. **Website Hosting:**
   - Hosted the website on EC2 Instances.

10. **Load Balancing:**
    - Employed an Application Load Balancer and a target group for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.

11. **Auto Scaling Group:**
    - Utilized an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

12. **Version Control:**
    - Stored web files on GitHub for version control and collaboration.

13. **Security with Certificate Manager:**
    - Secured application communications using Certificate Manager.

14. **Notification Service (SNS):**
    - Configured Simple Notification Service (SNS) to alert about activities within the Auto Scaling Group.

15. **Domain Name and DNS:**
    - Registered the domain name and set up a DNS record using Route 53.

## Deployment Script

```bash
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



