# EC2 Secure Web Server Lab

## Objective

The goal of this project was to launch and configure a secure EC2 instance, deploy a web server, and control access using AWS security groups.

This lab was designed to build hands-on experience with AWS compute services, basic Linux administration, and network-level security controls.

---

## Services Used

- AWS EC2
- Amazon Linux 2
- AWS Security Groups
- Apache HTTP Server (`httpd`)

---

## What I Implemented

- Launched an EC2 instance using Amazon Linux 2
- Created and used a key pair for secure instance access
- Configured a security group with:
  - SSH (port 22) restricted to my IP
  - HTTP (port 80) open for public web access
- Connected to the EC2 instance
- Installed and started Apache web server
- Created and deployed a custom web page
- Verified the web server through the instance’s public IPv4 address

---

## Security Concepts Demonstrated

- Principle of least privilege
- Network-level access control using security groups
- Restricting administrative access to a known IP
- Separating management access (SSH) from public access (HTTP)

---

## Architecture Summary

This project used a single EC2 instance as a public web server.

- **SSH access** was limited to my IP address for secure administration
- **HTTP access** was allowed publicly so the hosted web page could be reached through a browser
- Apache was installed on the instance to serve a custom HTML page

---

## Key Commands Used

### Update the server

```bash
sudo yum update -y

## Install Apache
sudo yum install httpd -y

## Start Apache 
sudo systemctl start httpd

## Enable Apache to start on boot
sudo systemctl enable httpd

## Create custom web page
echo "Hello from Nicky’s Secure EC2 Server" | sudo tee /var/www/html/index.html

## Restart Apache
sudo systemctl restart httpd

After configuration, I tested the deployment by entering the EC2 instance’s public IPv4 address into a browser, expecting to see : Hello from Nicky’s Secure EC2 Server

However the default Apache page, "It works!", appeared instead of my custom page.
The root cause:The default web content was still being served by Apache, which meant my custom file had not fully replaced the original content being used by the server.

Resolution: Removed the existing files from /var/www/html/
Recreated the index.html file with my custom content
Restarted the Apache service
Refreshed the browser and verified the updated output

Troubleshooting Commands : sudo rm -f /var/www/html/*
echo "Hello from Nicky’s Secure EC2 Server" | sudo tee /var/www/html/index.html
sudo systemctl restart httpd

Lesson learned:

This project helped me understand how AWS EC2 provides compute resources in the cloud and how security groups function as virtual firewalls to control inbound traffic.

I also learned how to:

deploy a basic web server on Linux
expose a service safely to the internet
troubleshoot default server behavior
validate whether a service is actually serving the intended content

This lab reinforced the relationship between compute, network security, and service configuration in AWS.

Summary :
Deployed a secure Ec2-based web server by launching an Amazon Linux 2 instance,
configuring security group rules, installing and managing Apache, and applying least privilege principles to restrict administrative access while
allowing public HTTP traffic. 
