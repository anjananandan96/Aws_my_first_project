# Aws_my_first_project
# Jenkins Deployment on AWS EC2

This project contains a demonstration of how to deploy Jenkins on an AWS EC2 instance and host a simple application.

# 1. Launch an AWS EC2 Instance
- Chose Ubuntu Server
- create key (i used pem key)
- Connected to the instance via mobxterm
- sudo apt update
 

# 2.Installation of Java
Jenkins requires Java to run, yet not all Linux distributions include Java by default. Additionally, not all Java versions are compatible with Jenkins.
Update the Debian apt repositories, install OpenJDK 21, and check the installation using the following commands:

sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version

# Long Term Support release
A LTS (Long-Term Support) release is chosen every 12 weeks from the stream of regular releases as the stable release for that time period. It can be installed from the debian-stable apt repository.

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins

## Refer from https://www.jenkins.io/doc/book/installing/linux/


#  Start Jenkins
# You can enable the Jenkins service to start at boot with the command:
sudo systemctl enable jenkins

# You can start the Jenkins service with the command:
sudo systemctl start jenkins

# You can check the status of the Jenkins service using the command:
sudo systemctl status jenkins

# Steps to Set Security Group Inbound Rules in AWS
# Step 1: Go to AWS EC2 Security Groups
Log in to your AWS Management Console.
Navigate to EC2 → Security Groups.
Select the security group associated with your EC2 instance.

# Step 2: Edit Inbound Rules
Click Inbound rules → Edit inbound rules → Add rule.
add type custom tcp
add port 8080
add source anywhere
[http://ip_address:8080]
(in this format we can access throug web)
