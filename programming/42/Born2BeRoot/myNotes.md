[[Born2beRoot]]

Logical Volume Manager :
In [Linux](https://en.wikipedia.org/wiki/Linux "Linux"), **Logical Volume Manager** (**LVM**) is a [device mapper](https://en.wikipedia.org/wiki/Device_mapper "Device mapper") framework that provides [logical volume management](https://en.wikipedia.org/wiki/Logical_volume_management "Logical volume management") for the [Linux kernel](https://en.wikipedia.org/wiki/Linux_kernel "Linux kernel"). Most modern [Linux distributions](https://en.wikipedia.org/wiki/Linux_distribution "Linux distribution") are LVM-aware to the point of being able to have their [root file systems](https://en.wikipedia.org/wiki/Root_file_system "Root file system") on a [logical volume](https://en.wikipedia.org/wiki/Logical_volume "Logical volume").

To see the partition:
```js
lsblk
```
or
```js
lsblk -a
```
which stands for "list block device"
Login as root:
```js
su -
```
Switch between users:
su - target_user_name

<u>**Install sudo:**</u>
```js
apt-get update -y
apt-get upgrade -y
apt install sudo
```

<u>**Install git:**</u>
```js
apt-get update -y
apt-get upgrade -y
apt-get install git -y
```
Check git version:
```js
git --version
```

<u>**Install wget:**</u>
Wget is a computer program that retrieves content from web servers. It supports downloading from [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol), [HTTPS](https://en.wikipedia.org/wiki/HTTPS) and [FTP](https://en.wikipedia.org/wiki/File_Transfer_Protocol).
```js
sudo apt-get install wget
```

<u>**Install Vim**</u>:
```js
sudo apt-get install Vim
```

<u>**Install Oh my zsh:</u>**
[Z shell](https://en.wikipedia.org/wiki/Z_shell) (Zsh) is a Unix shell that can be used as an interactive login shell and as a command interpreter for shell scripting.
"Oh My Zsh" is a user community website collecting third-party plug-ins and themes for Z shell with auto-update tool making it easier to keep installed plug-ins and themes updated.
```js
sudo apt-get install zsh
zsh --version
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

<u>**Install SSH and configure SSH service:**</u>
The [Secure Shell Protocol](https://en.wikipedia.org/wiki/Secure_Shell) is a cryptographic network protocol for operating network services securely over an unsecured network. Its most notable applications are remote login and command-line execution.
```js
sudo apt-get update
sudo apt install openssh-server
```
to check the SSH server status:
```js
sudo systemctl status ssh
```
or
```js
sudo service sshd status
```

to restart the SSH service:
```js
service ssh restart
```

<u>Changing default port (22) to 4242:</u>
```js
sudo nano /etc/ssh/sshd_config
```
"[nano](https://en.wikipedia.org/wiki/GNU_nano)" is a text editor for Unix-like computing systems.
Check if port setting is right:
```js
sudo grep Port /etc/ssh/sshd_config
```
Need to restart SSH:
```js
sudo service ssh restart
```

<u>**Adding user in sudo group:**</u>
```js
su -
usermod -aG sudo your_username
```

Check if user is in sudo group:
```js
getent group sudo
```

Give privilege as a super user:
```js
sudo visudo
```
add the new user as such:
```js
your_username	ALL=(ALL) ALL
```

<u>**Installing and configuring UFW:**</u>
[Uncomplicated Firewall](https://en.wikipedia.org/wiki/Uncomplicated_Firewall) is a program for managing a [Netfilter](https://en.wikipedia.org/wiki/Uncomplicated_Firewall) (framework provided by the Linux kernel allowing various networking-related operations to be implemented in the form of customized handlers) firewall designed to be easy to use.
Install UFW:
```js
apt-get install ufw
```
Enable UFW:
```js
sudo ufw enable
```
Check status:
```js
sudo ufw status numbered
```
Configure rules:
```js
sudo ufw allow ssh
```
Configure port rules:
```js
sudo ufw allow 4242
```
Delete the new rule:
```js
sudo ufw status numbered
sudo ufw delete (rule number to be deleted)
```

<u>**Set password policy:**</u>
[Pluggable Authentification Module](https://en.wikipedia.org/wiki/Pluggable_authentication_module)
[pam_unix.so](http://manpages.ubuntu.com/manpages/bionic/man8/pam_unix.8.html) is a module for traditional password authentification.
[pam_pwquality.so](http://manpages.ubuntu.com/manpages/bionic/man8/pam_pwquality.8.html) is a module to perform password quality checking.
[pam_deny.so](http://manpages.ubuntu.com/manpages/bionic/en/man8/pam_deny.8.html) is the locking-out PAM module.
[pam_permit.so](http://manpages.ubuntu.com/manpages/bionic/en/man8/pam_permit.8.html) is the promiscuous module that always permit access. This is dangerous.
Install password quality checking library:
```js
sudo apt-get install libpam-pwquality
```
Change length:
```js
sudo nano /etc/pam.d/common-password
```
[pam rules](https://helpful.knobs-dials.com/index.php/PAM_notes)
```js
password [success=1 default=ignore] pam_unix.so obscure sha512 minlen=10
```
obscure: enable some extra checks on password strenght (palindrome, similar, simple, rotated, etc...)
sha512: encryption using SHA512 algorithm
```js
password	requisite	pam_pwquality.so retry=3 lcredit=-1 ucredit=-1 dcredit=-1 maxrepeat=3 usercheck=0 difok=7 enforce_for_root
```
retry: prompt user with n times before returning "error"
lcredit: if n<0 this is the minimum number of lower case letters
ucredit: if n<0 this is the minimum number of upper case letters
dcredit: if n<0 this is the minimum number of digits
maxrepeat: reject password that contain more than n same consecutive characters
usercheck: if non zero, checks if password contains user name in some form (not for user names shorter than 3 characters)
difok: minimum number of changes from old to new password
enforce_for_root: will return "error" on a failed check even if the user changing the password is root
```js
password	requisite	pam_deny.so
```
```js
password	required	pam_permit.so
```

Password expiration:
```js
sudo nano /etc/login.defs
```
Change as per the following:
```js
PASS_MAX_DAYS  30
PASS_MIN_DAYS  0
PASS_WARN_AGE  7
```

Reboot the changes:

```js
sudo reboot
```

<u>**Create group:**</u>
```js
sudo groupadd user42
sudo groupadd evaluating
```
Check if group created:
```js
getent group
```

<u>**Create user and assign to group:**</u>
[/etc/passwd](https://linuxize.com/post/etc-passwd-file/) file is a text file with one entry per line, representing user account.
mark:x:1001:1001:mark,,,:/home/mark:/bin/bash
[--] - [--] [--] [-----] [--------] [--------]
|    |   |    |     |         |        |
|    |   |    |     |         |        +-> 7. Login shell
|    |   |    |     |         +----------> 6. Home directory
|    |   |    |     +--------------------> 5. GECOS
|    |   |    +--------------------------> 4. GID
|    |   +-------------------------------> 3. UID
|    +-----------------------------------> 2. Password
+----------------------------------------> 1. Username

Check all local users:
```js
cut -d: -f1 /etc/passwd
```
The "cut" utility cuts out selected portions of each line from each file and writes them to the standard output.
"-d" uses the character ":" as delimiter instead of the tab character
"-f1" specifies the 1st field from the file separated by the delimiter
Create the user:
[usermod](https://linuxize.com/post/usermod-command-in-linux/)
```js
sudo adduser new_username
```
Assigning an user into the "evaluating" group:
```js
sudo usermod -aG user42 your_username
sudo usermod -aG evaluating your_new_username
```
"-a" stands for "append" and allows the user to be added to the new group without being removed to existing groups if any
"-G" to be used if the user needs to be added to several groups which needs to be listed separated by a single ",".
Check if user is in group:
```js
getent group user42
getent group evaluating
```
or to check what groups is the current user in:
```js
groups
```
Check password rules for current user:
```js
chage -l your_new_username
```
"chage" stands for "change age" and is used to change or list "-l" the password expiry information of one user

<u>**Configuring sudoers group:**</u>
```js
sudo nano /etc/sudoers
```
```js
Defaults	passwd_tries=3
Defaults	badpass_message+"Password is wrong, please try again!"
Defaults	logfile="/var/log/sudo/sudo.log"
Defaults	log_input, log_output
Defaults	requiretty
```
The directory /var/log/sudo might need to be created.
"[tty](https://en.wikipedia.org/wiki/Tty_(Unix))" stands for "teletypewriter" and is a command to print the file name of the terminal connected to the standrd input.

<u>**Change the hostname:**</u>
In computer networking, [localhost](https://en.wikipedia.org/wiki/Localhost) is a hostname that refers to the current device used to access it. It is used to access the network services that are running on the host via the loopback network interface. Using the loopback interface bypasses any local network interface hardware.
Check current hostname:
```js
hostnamectl
```
Change the hostname:
```js
hostnamectl set-hostname new_hostname
```
Change /etc/hosts file:
```js
sudo nano /etc/hosts
```
Change old_hostname with new_hostname:
```js
127.0.0.1	localhost
127.0.0.1	new_hostname
```
Reboot and check the change:
```js
sudo reboot
```
The address "127.0.0.1" is the standard address for [IPv4](https://en.wikipedia.org/wiki/IPv4) loopback traffic.

<u>**Crontab configuration:**</u>
The [cron](https://en.wikipedia.org/wiki/Cron) command-line utility, also known as cron job, is a job scheduler on Unix-like operating systems.
Install the netstat tools:
In computing, [network statistics](https://en.wikipedia.org/wiki/Netstat) is a command-line network utility that displays network connections for Transmission Control Protocol (both incoming and outgoing), routing tables, and a number of network interface and network protocol statistics.
```js
sudo apt-get update -y
sudo apt-get install -y net-tools
```
"-y" to automatically assume "yes" to all prompts
