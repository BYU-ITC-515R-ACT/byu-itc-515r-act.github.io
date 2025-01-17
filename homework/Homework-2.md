# Homework 2 – OS Structure

1. **Question:** What is the default file system used by Ubuntu?  
    - **Answer:** `ext4`

1. **Question:** Which file system is the default for both CentOS and Rocky Linux?  
   - **Answer:** `xfs`

1. **Question:** Which directory is used for storing logs and variable data in most distributions?  
    - **Answer:** `/var`

1. **Question:** Which command is used to update software packages in CentOS and Rocky Linux? Assume you are logged in as root.  
    - **Answer:** `dnf update` or `yum update`

1. **Question:** Which command is primarily used to manage software packages in Ubuntu?  
    - **Answer:** `apt`

1. **Question:** Which command is used to update software packages in Ubuntu? Assume you are logged in as root.  
    - **Answer:** `apt update`

1. **Question:** In which directory are user-installed software and libraries typically stored in Ubuntu?  
    - **Answer:** `/usr`

1. **Question:** What system and service manager is used by all three distributions: Ubuntu, CentOS, and Rocky Linux?  
   - **Answer:** `systemd`

1. **Question:** Which package manager is used by both CentOS and Rocky Linux?  
   - **Answer:** `dnf` or `yum`

1. **Question:** Which directory is used to store system-wide configuration files across Ubuntu, CentOS, and Rocky Linux?  
   - **Answer:** `/etc`

1. **Question:** What is the common command to view running processes?  
   - **Answer:** `ps`

1. **Question:** Where are boot loader files, kernel images, and initial RAM disk files stored in Ubuntu, CentOS, and Rocky Linux?  
   - **Answer:** `/boot`

1. **Question:** In which directory are user-specific data files stored in Ubuntu, CentOS, and Rocky Linux?  
    - **Answer:** `/home`

1. **Question:** Which distribution supports both `deb` and `snap` packages?  
    - **Answer:** `Ubuntu`

1. **Question:** In which directory are the systemd unit files located across Ubuntu, CentOS, and Rocky Linux?  
    - **Answer:** `/etc/systemd/system`

1. **Question:** Which distribution would use the `dpkg` command for package management tasks?  
    - **Answer:** `Ubuntu`

1. **Question:** What command would you use to check the status of the `sshd` service using `systemd`? Assume you are logged in as root. 
   - **Answer:** `systemctl status sshd` or `systemctl status ssh`

1. **Question:** Where are the `systemd` unit files stored in the system?  
   - **Answer:** `/etc/systemd/system`

1. **Question:** How would you reload the `systemd` configuration files after making changes? Assume you are logged in as root.
   - **Answer:** `systemctl daemon-reload`

1. **Question:** What command is used to edit the cron jobs for the current user in Ubuntu?  
    - **Answer:** `crontab -e`

1. **Question:** Where are system-wide cron jobs typically stored?  
    - **Answer:** `/etc/crontab` or `/etc/cron.d/`

1. **Question:** Which command lists all cron jobs for the current user?  
    - **Answer:** `crontab -l`

1. **Question:** What file stores user account information, including usernames and UIDs?  
    - **Answer:** `/etc/passwd`

1. **Question:** Where are the user passwords stored in a hashed format in Linux?  
    - **Answer:** `/etc/shadow`

1. **Question:** How can you list all the users currently logged into the system?  
    - **Answer:** `who` or `w`

1. **Question:** How do you display the current user's username in the terminal?  
    - **Answer:** `whoami`

1. **Question:** Which command can be used to restart a service using `systemd`? You do not need to include a service name. Assume you are logged in as root.
   - **Answer:** `systemctl restart`

1. **Question:** Which command would you use to disable a service from starting at boot with `systemd`? You do not need to include a service name. Assume you are logged in as root.
   - **Answer:** `systemctl disable`

1. **Question:** Which command would you use to view a user's last login time?  
   - **Answer:** `last`

1. **Question:** Which file in Ubuntu is used to list the software repositories?  
   - **Answer:** `/etc/apt/sources.list`

1. **Question:** Which command lists all the repositories enabled on a CentOS or Rocky Linux system? Assume you are logged in as root.  
   - **Answer:** `dnf repolist` or `yum repolist`

1. **Question:** How do you clean the local package cache to free up space in Ubuntu? Assume you are logged in as root. 
    - **Answer:** `apt clean` or `apt autoremove`

1. **Question:** What is the command to list all installed packages and their versions in CentOS or Rocky Linux? Assume you are logged in as root. 
    - **Answer:** `dnf list installed` or `yum list installed`

1. **Question:** The `sudo` group in Ubuntu is as to the `_____` group in Centos 
    - **Answer:** `wheel`