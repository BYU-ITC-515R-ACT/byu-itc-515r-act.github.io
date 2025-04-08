# Homework 9 – Hardening 

1. **Question:** To edit the system-wide cron jobs, you would modify the file located at `/etc/_______`.  
   **Answer**: `crontab`

1. **Question:** The command to restart a service managed by `systemd` is `systemctl ________ <service_name>`.  
   **Answer**: `restart`

1. **Question:** The command to load new configuration changes in a service managed by `systemd` is `systemctl ________ <service_name>`.  
   **Answer**: `reload`

1. **Question:** To remove a service from startup on a `systemd`-based system, you can run `systemctl ________ <service_name>`.  
   **Answer**: `disable`

1. **Question:** To prevent a user from logging in, you can disable their account by running `_____ __ <username>`.  
   **Answer**: `passwd -l` or `passwd,-l`

1. **Question:** In SSH configuration, the setting to disable root login is `_________ __` in `/etc/ssh/sshd_config`.  
   **Answer**: `PermitRootLogin no` or `PermitRootLogin,no`

1. **Question:**The command to list active network connections on a Linux system is `_________`.  
   **Answer**: `netstat` or `ss`

1. **Question:** The 3 flags to list all(listening and non-listening) TCP and UDP connections command to list active network connections on a Linux system are `netstat -_____`. List the flags in alphabetical order
   **Answer**: `atu` or `-atu`

1. **Question:** What is the command to set the owner to `blueteam` and the group to `sudo` for the file `/home/blueteam/ssh/.authorized_keys`  `chown ____________ ___________`.  
   **Answer**: `blueteam:sudo /home/blueteam/ssh/.authorized_keys` or `blueteam:sudo,/home/blueteam/ssh/.authorized_keys`

1. **Question:** The Ubuntu PAM file that controls password policies can be found in `/etc/pam.d/________`.  
   **Answer**: `common-password`

1. **Question:** The command `ssh-keygen -t _______` is used to generate an RSA SSH key.  
   **Answer**: `rsa`

1. **Question:** To view the current firewall rules on a system using `firewalld`, you use the command `firewall-cmd --_______`.  
   **Answer**: `list-all`

1. **Question:** To check which groups the `blueteam` user belongs to, you can use the command `______ blueteam`.  
   **Answer**: `groups`

1. **Question:** The source list files for APT package management are located in `/etc/apt/________`.  
   **Answer**: `sources.list`

1. **Question:** To check for pinned packages on an Ubuntu system, you would inspect the file `/etc/apt/________`.  
   **Answer**: `preferences` or `preferences.d/*`

1. **Question:** The command `____` shows the login history of users.
   **Answer**: `last`

1. **Question:** To remove a user from a group, the command, and flag are  `______ __ <username> <group>`.  
   **Answer**: `gpasswd -d` or `gpasswd,-d`

1. **Question:** The command `crontab -e` opens the cron jobs for the `_______` user.  
   **Answer**: `current`

1. **Question:** The correct 3-digit file permissions for `/etc/shadow` are `___`.  
   **Answer**: `640`

1. **Question:** The correct 3-digit file permissions for `/etc/passwd` are `___`.  
   **Answer**: `644`

1. **Question:** The correct 3 digit file permissions for an SSH key are `___`.  
   **Answer**: `400`

1. **Question:** A cron job set in `/etc/crontab` will run with the permissions of the system’s root user by default. (True/False)  
   **Answer**: `True`

1. **Question:** System users that have `/sbin/nologin` or `/bin/false` as their shell can still log in via SSH. (True/False)  
   **Answer**: `False`

1. **Question:** In `/etc/ssh/sshd_config`, setting `AllowUsers` limits which users can log in via SSH. (True/False)  
   **Answer**: `True`

1. **Question:** Running `netstat -tuln` will show active connections on both TCP and UDP ports. (True/False) 
   **Answer**: `True`

1. **Question:** To log SSH attempts, the `auth.log` file on Ubuntu records all successful and failed logins. Provided that `syslog` is installed. (True/False) 
   **Answer**: `True`

1. **Question:** Active reverse shells show as logged in, if the `who` command is used. (True/False)
   **Answer**: `False`

1. **Question:** All SSH sessions can be killed using the command `killall sshd`. (True/False)
   **Answer**: `True`

1. **Question:** Files owned by root can always be modified by any user. (True/False)
   **Answer**: `False`

1. **Question:** The command `chmod 777 <file>` gives full permissions to everyone on the system. (True/False) 
   **Answer**: `True`

1. **Question:** A password logger is a tool that keeps track of password attempts and successful logins on a system. (True/False)
   **Answer**: `True`

1. **Question:** Removing a service in `systemd` with `systemctl stop <service_name>` prevents it from restarting on the next boot. (True/False)  
   **Answer**: `False`

1. **Question:** What is the command used to create an advisory file lock in Linux?  
   **Answer**: `flock`

1. **Question:** In the SSH configuration file(`/etc/ssh/sshd_config`), which directive specifies the file location for public keys used for user authentication?  
**Answer**: `AuthorizedKeysFile`

1. **Question:** Which command is used to view all installed packages installed on an Ubuntu system `apt ___ _______`?  
   **Answer**: `list --installed` or `list,--installed`
