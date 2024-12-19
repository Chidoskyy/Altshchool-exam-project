# Project Documentation

This documentation explains the steps taken to provision a server, link a GitHub repository, set up NGINX, add a domain name, and configure HTTPS for a secure web server.

---
# **Project Report: Provisioning and Hosting My Web Server**

---

## **Provisioning My Server on AWS**

### **Logging In and Setting Up the Instance:**
1. Logged in to my AWS account and navigated to the EC2 dashboard.
2. Selected London as my region and created a new EC2 instance named `Altschool-AWS`.

### **Configuring the Instance:**
1. Chose **Ubuntu** as the machine image (AMI).
2. Selected the **Free Tier** option for the instance type.

### **Security Group and Key-Pair:**
1. Created a new security group to configure firewall rules.
2. Added the security group to my instance.
3. Selected a previously created key-pair for secure login.

### **Launching and Connecting to the Instance:**
1. Launched the instance and navigated to the **Connect** button.
2. Copied the public DNS from the **SSH Client** option.
3. Opened Git Bash, navigated to the directory containing my key-pair, and connected to the instance using the SSH command provided by AWS.
4. Successfully logged into the Ubuntu machine.

---

## **Linking My GitHub Repository to the Server**

### **Installing Git:**
```bash
sudo apt install git -y


Here is the text reformatted in Markdown:

Linking GitHub Repository to Server

Step 1: Install Git

Install Git on the instance using the following command:

bash
sudo apt install git -y


Step 2: Generate and Add SSH Key

Generate SSH Key

Generate an SSH key on the instance:

bash
ssh-keygen


Copy Public Key

Copy the public key:

bash
cat ~/.ssh/id_ed25519.pub


Add Public Key to GitHub Repository

Add the public key to your GitHub repository:

1. Navigate to Settings > SSH and GPG Keys > Add New Key
2. Paste the copied public key

Step 3: Clone Repository

Clone the GitHub repository to the server:

bash
git clone <repository_url>

Replace <repository_url> with the actual URL of your GitHub repository.