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
