**Name:** Pradeep Sapkota

**Date:** 18 January 2026  

# Task 1 – Creating Ubuntu VM on Azure + SSH Connection

This is my simple documentation for setting up an Ubuntu virtual machine in Azure and connecting to it with SSH.

## Step 1: Azure Account + Free Credits

I logged in to [portal.azure.com](https://portal.azure.com) with my HAMK student email.  
Then I activated **Azure for Students** to get free credits.


## Step 2: Created Resource Group

I made a new resource group called `Linux-Management-1` in **Sweden Central**.



## Step 3: Created the Virtual Machine

Settings I used:
- Image: **Ubuntu Server 24.04 LTS**
- Size: **Standard D2s v3**
- Name: `prade-ubuntu-LinuxLearning`
- Authentication: SSH key
- Allowed SSH from my IP

After a small region issue (had to wait a bit), the VM was ready!

Here’s what the VM overview looks like:
![Information of the virtual manchine](Images/Virtual%20machine.png)


## Step 4: Connected with SSH using PuTTY

I downloaded PuTTY from the official site.  
Took the public IP from Azure → opened PuTTY → entered IP + username + loaded my SSH key.

First login worked perfectly! Got the Ubuntu welcome message.


![Reanining Other](Images/Disk.png)


## Step 5: Connected to the terminal
After completing all the step I have make it so that I can run it from terminal as per professor guidance. And we have created shortcut key so that it can be open easily afterward.