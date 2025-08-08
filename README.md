# Nextcloud-AWS
This repository contains a step-by-step guide for setting up your own cloud storage solution using Nextcloud on Amazon Web Services (AWS).

---

## Step 1: Launch an AWS EC2 Instance

1.1 Open the AWS Management Console
Go to https://aws.amazon.com and log in to your account.

1.2 Open the EC2 Dashboard
Search for “EC2” in the top search bar and select the EC2 service.

1.3 Launch a New Instance

Click on “Instances” > “Launch Instance”

Give your instance a name, e.g., Nextcloud

Choose an Amazon Machine Image (AMI):

Select Ubuntu Server 22.04 LTS (or a similar version).

Choose an instance type: For testing purposes, select t3.micro (included in the AWS Free Tier).

Create or select an existing SSH key pair
Name it keynextcloud, then click “Create key pair” and download the .pem file.

1.4 Configure Network Access
Scroll down to the Network Settings section and enable the following inbound rules:

✅ Allow SSH traffic from anywhere

✅ Allow HTTPS traffic from the internet

✅ Allow HTTP traffic from the internet

1.5 Configure Storage
(Optional, but recommended)
Under Storage, change the size from 1x8 GB to 1x30 GB — this is still within the Free Tier limit.

1.6 Launch the Instance
Click “Launch Instance”.
After the instance is running, note down the public IP address (e.g. 65.1.93.21) — you’ll use this for connecting via SSH and accessing your Nextcloud later.

## Step 2: Connect to the EC2 Instance

2.1 Go to the Instances page in the AWS EC2 dashboard.

2.2 Select your running instance.

2.3 Copy the Public IP address (e.g. 65.1.93.21).

2.4 Click “Connect” and choose EC2 Instance Connect and click connect 

---

## Step 3: Install and Configure Nextcloud
Once connected to your instance, run the following commands
1. sudo su
2. sudo apt update && sudo apt upgrade -y
3. sudo snap install nextcloud
4. snap changes nextcloud

Step 3.1: Verify Security Groups
3.2 In the EC2 dashboard, click on your Instance ID.
3.3 Navigate to the Networking tab.
3.4 Click on the Network Interface ID.
3.5 Check the Security Groups — you should see rules for:
✅ SSH
✅ HTTPS
✅ HTTP

---

## Step 4: Create a Swap Partition
4.1 fallocate --length 2GiB /mnt/swapfile
4.2 chmod 600 /mnt/swapfile
4.3 mkswap /mnt/swapfile
4.4 swapon /mnt/swapfile

To verify swap is active:
4.5 htop

---

## Step 5: Configure Firewall
5.1 sudo ufw allow 80,443/tcp

----

## Step 6: Manual Nextcloud Installation
Install Nextcloud with a username and password:
6.1 sudo nextcloud.manual-install testuser password1234

Check the current list of trusted domains:
6.2 sudo nextcloud.occ config:system:get trusted_domains

## Step 7: Fix "Access through untrusted domain" Error
If you try to access your server via IP (e.g., http://65.1.93.21) and get the error:
"Access through untrusted domain"
You need to add the IP to the list of trusted domains:
7.1 sudo nextcloud.occ config:system:set trusted_domains 1 --value=65.1.93.21

Verify again:
7.2 sudo nextcloud.occ config:system:get trusted_domains

You should now see your IP address listed.

---

## Step 8: Access Nextcloud in Your Browser

8.1 Open your browser and go to:
http://65.1.93.21

8.2 Log in using the credentials you created earlier:

8.3 Username or Email: testuser

8.4 Password: password1234

8.5 You should now have full access to your self-hosted Nextcloud server running on AWS.

and now we are done! 
