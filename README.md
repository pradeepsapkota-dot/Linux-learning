**Name:** Pradeep Sapkota

**Date:** 18 January 2026  

# Assignment No: 0

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


# Assignment NO: 2

For this time my professor (Toni Laitinen) have given a assignment where we have to select five different **Level 2** directories and save their contents in one file, `listing.md`.  
Here **Level 2** directories means /home/name. Not /home which is **Level 1** directory.

So, I was having a problem on how to save the content in **lissting.md**, so I used chatgpt for that. Rest of was easy as we have to find the content which was already exist in our files.

So, here is are the code that I have used in while I was coding my asignment.

``` linux
prade@prade-ubuntu-LinuxLearning:~$ ls /
bin                home               media  run                 sys
bin.usr-is-merged  lib                mnt    sbin                tmp
boot               lib.usr-is-merged  opt    sbin.usr-is-merged  usr
dev                lib64              proc   snap                var
etc                lost+found         root   srv
prade@prade-ubuntu-LinuxLearning:~$ ls /home
mickey  pluto  prade
prade@prade-ubuntu-LinuxLearning:~$ ls /usr
bin  games  include  lib  lib64  libexec  local  sbin  share  src
prade@prade-ubuntu-LinuxLearning:~$ ls /var
backups  crash  local  log   opt  snap   tmp
cache    lib    lock   mail  run  spool
prade@prade-ubuntu-LinuxLearning:~$ ls /run
0_waagent.pid    initctl               snapd-snap.socket
agetty.reload    lock                  snapd.socket
blkid            log                   sshd
chrony           lvm                   sshd.pid
cloud-init       lxd-installer.socket  sudo
console-setup    motd.d                systemd
credentials      motd.dynamic          tmpfiles.d
crond.pid        mount                 udev
crond.reboot     multipath             udisks2
cryptsetup       multipathd.pid        unattended-upgrades.lock
dbus             needrestart           unattended-upgrades.progress
dhcpcd           screen                user
dmeventd-client  sendsigs.omit.d       utmp
dmeventd-server  setrans               uuidd
fsck             shm                   waagent.pid
prade@prade-ubuntu-LinuxLearning:~$ cd /home/prade
prade@prade-ubuntu-LinuxLearning:~$ cd /home/mickey
prade@prade-ubuntu-LinuxLearning:/home/mickey$ cd /usr/bin
prade@prade-ubuntu-LinuxLearning:/usr/bin$ cd /usr/games
prade@prade-ubuntu-LinuxLearning:/usr/games$ cd /var/log
prade@prade-ubuntu-LinuxLearning:/var/log$ cd ~
prade@prade-ubuntu-LinuxLearning:~$ mkdir listing.md
mkdir: cannot create directory ‘listing.md’: File exists
prade@prade-ubuntu-LinuxLearning:~$ > listing.md
prade@prade-ubuntu-LinuxLearning:~$ echo "## /home/prade" >> listing.md
ls /home/prade >> listing.md
echo "" >> listing.md

echo "## /home/mickey" >> listing.md
ls /home/mickey >> listing.md
echo "" >> listing.md

echo "## /usr/bin" >> listing.md
ls /usr/bin >> listing.md
echo "" >> listing.md

echo "## /usr/games" >> listing.md
ls /usr/games >> listing.md
echo "" >> listing.md

echo "## /var/log" >> listing.md
ls /var/log >> listing.md
echo "" >> listing.md
prade@prade-ubuntu-LinuxLearning:~$ ls listing.md
listing.md
prade@prade-ubuntu-LinuxLearning:~$ less listing.md
prade@prade-ubuntu-LinuxLearning:~$
```
And the image of this:
![1st](Images/1st%20one.png)

![2nd](Images/2nd%20one.png)


# Assigment 3
For `Assignment 3` the task was to create users and use created users to test out file access permissions.

## Step 1: Create the Tupu user using the `adduser` script.
In this step, we were told just to use ``adduser`` script and add user tupu.

```bash
sudo adduser tupu
```
**Image**
![step1](Images/Step%201.png)

## Step 2: Create the Lupu user using the ``useradd`` command. Try to create a user profile, home directory, and user group similar to Tupu.
In this step, we were told to create ``lupu`` user using ``useradd`` command.

But, I was having a problem on creating a ``-G lupu lupu`` because -G is a secondary group and it always shows the problem: 
```
useradd: group 'lupu' does not exist
```
So thats why I use ``-g`` because it is a primary group and I have already add lupu in a group. 

```bash
sudo groupadd lupu
```
```bash
sudo useradd -m -d /home/lupu -s /bin/bash -g lupu lupu
```

**Image**
![Step2](Images/Step%202.png)

## Step 3: Create the Hupu system user with the login shell set to ``/bin/false``.

In this step, we were told to create a hupu system using ``/bin/false``.

```bash
sudo useradd --system --shell /bin/false hupu
```
**Image**
![Step3](Images/Step%203.png)

## Step 4: Add the users Tupu and Lupu to the sudo users.
In this we have given two option to add the users accordingly.
First one: 
```bash
sudo visudo
```
After this:
```
Add the following lines:
tupu ALL=(ALL:ALL) ALL
lupu ALL=(ALL:ALL) ALL
```
Second one:
```bash
sudo usermod -aG sudo tupu
sudo usermod -aG sudo lupu
```
So, I have done this step by using the second solution.

**Images**
![Step4](Images/Step%204.png)

## Step 5: Create a directory ``/opt/projekti`` and add both users (Tupu and Lupu) as owners. Only Tupu and Lupu should have access to list files in the directory, read, and modify them.

At first, I created a common group for both of the user.
```bash
sudo groupadd projekti
```
And added both users to the group:
```bash
sudo usermod -aG projekti tupu
sudo usermod -aG projekti lupu
```
After doing this, I created the projekti directory:
```bash
sudo mkdir /opt/projekti
```
Then, I assign group ownership:
```bash
sudo chown root:projekti /opt/projekti
```
After doing so, I set the directory permissions.
```bash
sudo chmod 770 /opt/projekti
```
With this:
- Owner and Groups can read, write, execute.
-Others they have no access.

After this, setgid bit ensures all newly created files and directories inherit the ``projekti`` group.
```bash
sudo chmod g+s /opt/projekti
```

**Images**
![Step 5](Images/Step%205.png)

## Step 6: Premisssion Testing
I was a bit curious about it works or not so I run a testing program too.

- Test as ``tupu``
```bash
su - tupu
cd /opt/projekti
touch test_tupup.txt
ls -l
```
**Image**
![Step6](Images/Step%206%20for%20tupu.png)

- Test as ``lupu``
```bash
su - lupu
cd /opt/projekti
echo "hello" >> test_tupu.txt
touch test_lupu.txt
ls -l
```
**Images**
![Step 6](Images/Step%206%20for%20lupu.png)

- Test as ``hupu``
Her hupu is a unauthorized access so it should so access denied.

```bash
su - hupu
cd /opy/projekti
```

**Images**
![Step 6](Images/Step%206%20for%20hupu.png)

So as we can see, for ``tupu`` and ``lupu`` it allow the access but for ``hupu`` it denies it which shows that our assignment is correct.

# Conclusion
This task help me to learn how the linux user and permission management using users, groups, sudo access, and directory permission control.