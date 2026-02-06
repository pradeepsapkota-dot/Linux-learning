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

Here hupu is a unauthorized access so it should so access denied.

```bash
su - hupu
cd /opy/projekti
```

**Images**

![Step 6](Images/Step%206%20for%20hupu.png)

So as we can see, for ``tupu`` and ``lupu`` it allow the access but for ``hupu`` it denies it which shows that our assignment is correct.

# Conclusion
This task help me to learn how the linux user and permission management using users, groups, sudo access, and directory permission control.