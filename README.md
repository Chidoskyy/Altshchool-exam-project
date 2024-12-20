# ***Project Documentation***

This documentation explains the steps I took to provision a server, link a GitHub repository, set up NGINX, add a domain name, and configure HTTPS for a secure web server.
### The URL of my server and the IP addres are: 
```
chidi.ebere.web.mooo.com
```
```
35.178.177.118
```
---
# *Project Report: Provisioning and Hosting My Web Server*

---

## **Provisioning My Server on AWS**

### **Logging In and Setting Up the Instance:**
1. Logged in to my AWS account and navigated to the EC2 dashboard.
2. Selected London as my region and created a new EC2 instance named `Altschool-AWS`.

### **Configuring the Instance:**
1. Chose **Ubuntu** as the machine image (AMI).
2. Selected the **Free Tier** option for the instance type.

### **Security Group and Key-Pair:**
1. Created a new security group to configure firewall rules and opened ```port 80``` in inbound rules.
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
``` sudo apt install git -y ```
### **Generating and Adding SSH Key:**

1. Generated an SSH key on the instance:
 ssh-keygen


2. Copied the public key:
 ``` cat ~/.ssh/id_ed25519.pub ```


3. Added the public key to my GitHub repository by navigating to Settings ```SSH and GPG Keys > Add New Key```

### **Cloning the Repository:**


1. Cloned the GitHub repository to the server:
 ```git clone <repository_url>```

## **Installing NGINX and Hosting My Web Page**
### **Installing NGINX:**


1. Updated all packages:
 ```sudo apt update```


2. Installed NGINX:
 ```sudo apt install nginx -y```


3. Started the server:
 ```sudo systemctl start nginx```


4. Verified NGINX status:
 ```service nginx status```


## **Deploying the Website:**


1. Moved the project directory to the NGINX web root:
 ```sudo mv altSchool/* /var/www/html```


2. Updated the NGINX configuration to point to the root directory:
 ```sudo nano /etc/nginx/sites-available/default```


3. Restarted the NGINX server:
 ```sudo systemctl restart nginx```

## **Automating Deployment Updates**
### **Creating a Deployment Script:**


1. Created a Bash script to pull updates from GitHub:
 nano ~/deploy.sh

```
Script contents:
#!/bin/bash
cd /var/www/html
git pull origin main
sudo systemctl restart nginx

```


2. Made the script executable:
 ```chmod +x ~/deploy.sh```


### **Accessing the Website:**


1. Accessed the website using the public IP of my instance.

## **Adding a Custom Domain Name**

### **Registering the Domain:**


1. I Registered a free domain name ```chidi.ebere.web.mooo.com``` using ```freedns.afraid.org``` and pointed it to the public IP of my instance.
### **Configuring NGINX for the Domain:**


1. Updated the NGINX configuration:
 ```server_name chidi.ebere.web.mooo.com www.chidi.ebere.web.mooo.com;```


2. Restarted the server:
 ```sudo systemctl restart nginx```



## **Configuring HTTPS with a Free SSL Certificate**

### **Installing Certbot:**


1. Updated packages  
 ```sudo apt update```

 2. Installed Certbot with the NGINX plugin:
```sudo apt install certbot python3-certbot-nginx -y```


### **Obtaining an SSL Certificate:**


1. Ran the following command to secure the domain:
 ```sudo certbot --nginx -d chidi.ebere.web.mooo.com```


### **Testing the Configuration:**


1. Verified the configuration:
 ```sudo nginx -t```


2. Restarted the NGINX server:
 ```sudo systemctl reload nginx```


### **Accessing the Secure Website:**


1. I Confirmed that the website was accessible on my dormain name:
 ```https://chidi.ebere.web.mooo.com```



