# Deploying a Web Page in EC2
The following is a project on how to set up an EC2 instance, install apache to deploy a webpage on the EC2 instance and how to configure a security group.

### Launch an EC2 instance
* In AWS management console, search for EC2 under the services offered by AWs. In the EC2 console, select insatnces,  then click on Launch an instance to create a new instance
* Select a suitable AMI for your instance
* Create a key pair to securely connect to your instance
* Use the default VPC or you can create a VPC with your own configurations
* Launch the instance

### Configure a Security group
* Navigate to "Security Groups" in EC2 console and select the one associated with your instance. From there edit the inbound rules
* Allow SSH access: Type: SSH, Protocol: TCP, Port Range: 22, Source: 0.0.0.0/0; This rule is essential for you to connect to your EC2 instance securely via a terminal.
* Allow HTTP access: Type: HTTP, Protocol: TCP, Port Range: 80, Source: Anywhere (0.0.0.0/0); This rule allows users to access your web server via unencrypted HTTP traffic.

### Install Web Server
* Connect to your EC2 instance using SSH terminal, this can be acheved using the folllowing commands:
   ```bash
   chmod 400 your-key-pair-name.pem
   ssh -i /path/to/your-key-pair-name.pem user-name@public-ip-address
* The chmod commmand restricts permissions to only the owner o fteh file while SSh command connects you to your   instance
* Use the folowing commands to install and run the Apache web server:
  ```bash
  sudo dnf update -y # good practice to ensure server is up to date
  sudo dnf install httpd -y # install Apache
  sudo systemctl start httpd  # get the server running
  sudo systemctl enable httpd # your webserver starts automatically every time ec2 reboots

### 
