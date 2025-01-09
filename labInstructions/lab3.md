# Lab 3: Secure Shell (SSH) & File Transfer Protocol (FTP)

## Introduction

In this lab, you’ll learn to set up, configure, and secure two essential network protocols: SSH (Secure Shell) and FTP (File Transfer Protocol). SSH is widely used for secure remote administration of servers, enabling encrypted connections that protect data during transmission. You’ll explore the configuration and hardening of SSH to prevent unauthorized access, including setting up key-based authentication, restricting login privileges, and enabling multi-factor authentication (MFA) for enhanced security. 

The second half of this lab covers FTP, a protocol traditionally used for transferring files between clients and servers. You’ll configure an FTP server, create and manage FTP-specific user accounts, and explore methods for securing FTP access through user restrictions and access controls. 

Resources to assist with the lab:  
1. Homework Questions  
1. Class Resources 
1. Classmates/Teammates  
1. Internet Resources
1. Teaching Assistants  

Please reach out to the TAs only after making a genuine effort to resolve the issue independently. While they are available to provide guidance and support, their role is to assist you in developing your understanding rather than providing immediate solutions. You are encouraged to approach challenges proactively, fostering problem-solving skills and critical thinking in the process.

Developing problem-solving skills and critical thinking is fundamental to your education and growth. These skills are emphasized as part of the **Aims of a BYU Education**, which seek to cultivate individuals of faith, intellect, and character. Problem-solving and critical thinking are essential components of sound reasoning, effective communication, and intellectual depth — qualities that prepare you to succeed in both academic and real-world challenges.  

BYU’s focus on lifelong learning and service reminds us that the ability to independently approach, analyze, and resolve complex issues is just as important as mastering technical skills. These capabilities not only build competence but also instill the confidence to contribute meaningfully to the world and continue learning throughout life.  

## Configuration Instructions

### Virtual Machines and Operating Systems
You will be working with:  
  - 1 CentOS 7 Machine

### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network as follows:  

1. **`Lab-3-ssh-ftp` Machine**:  
    - IP: `172.18.<ID>.3/16`  
    - Gateway: `172.18.0.1`
    - DNS: `172.18.0.1`

1. **`Lab-3-kali` Machine**:  
    - IP: `172.18.<ID>.4/16`  
    - Gateway: `172.18.0.1`
    - DNS: `172.18.0.1`

### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- To track your progress, visit the <a href="http://172.18.0.3/lab/3" target="_blank">scoreboard</a>.
- You need to be connected to the VPN to access the scoreboard and your Proxmox instance.

### Scoreboard Key
- **Green arrows** indicate that everything is working as intended.
- **Orange Exclamation** indicates that something is partially working. 
- **Red down arrows** indicate that something is not working.

#### Lab Time Estimates

- **Pass** :
- **Merit**:
- **Distinction**:

#### **Credentials**  
- All VMs have the same login credentials:  
  - **Username**: `blueteam`  
  - **Password**: `abc123`  

## Pass Criteria

### P1: SSH Installation and Configuration

1. Install `SSH` on the server by installing the `openssh-server` package

### P2: SSH Key Generation and Management

1. Generate an SSH key on your `lab-3-kali` machine.
1. Copy the public key over to your server to the `blueteam` account.
1. Connect to the server using the key instead of the password.

### P3: SSH Hardening

1. Limit the number of failed login attempts to `3`.
1. Set the timeout to be `1 minute`.
1. Set the maximum number of concurrent sessions to be `5`

### P4: SSH File Transfers 
1. Copy the file `ssh-file.txt` from your `lab-3-kali` machine `Documents` directory to your server. Place it in `/home/blueteam/P4/`.

### P5: Logging and Monitoring SSH Activity

1. View the SSH logs and answer the following questions
    - How many failed login attempts are there for the user `bob`? Enter the line `bob-failed:<count>` into the file `/home/blueteam/P5/P5.txt`.
    - How many successful logins are there for the user `redteam`? Enter the line `redteam-successful:<count>` into the file `/home/blueteam/P5/P5.txt`.
    - How many successful password logins are there for the user `bob`? Enter the line `bob-password:<count>` into the file `/home/blueteam/P5/P5.txt`.
    - How many of the successful logins for the `readteam` used an `ssh key`? Enter the line `redteam-key:<count>` into the file `/home/blueteam/P5/P5.txt`.

### P6: Troubleshooting
To complete `P6` `P1-5` must have a green arrow before starting

1. Fix the errors in the ssh config files to allow the service to restart.
1. Restart the service.

### P7: FTP Installation, Configuration, and User Management
1. Install an FTP server by installing `vsftpd`
1. Create a user called `ftpuser` and make sure it has a home directory
1. Restrict `ftp` users to their home directories
1. Connect to the FTP server from your computer using `ftpuser`
    - You can use the CLI or an FTP client

### P8: FTP Security
1. Disable anonymous login to the FTP server. 

### P9: Troubleshooting
To complete `P9` `P1-8` must have a green arrow before starting

1. Fix the errors in the FTP config files to allow the service to function.
1. Restart the service.

## Merit Criteria

### M1: SSH Installation and Configuration

1. Modify the ssh port to also use port `2222`. Make sure it is still also running on port `22`.
1. Disable `root` account login via ssh
1. Disable `password` authentication and only allow `key` authentication 

### M2: SSH Key Generation and Management
1. Use the given public SSH keys and configure the user to use their specific key.

### M3: Logging and Monitoring SSH Activity

1. Install the package `auditd`
1. Using `auditd`. What was the last file the `readteam` account viewed?  Enter the line `filepath:<full filepath>` into the file `/home/blueteam/M4/M4.txt`.

### M4: Troubleshooting
To complete `M5` `P1-9 and M1-3` must have a green arrow before starting.

1. Some of the users are having issues connecting with their keys. Fix the issues.

### M5: FTP Installation, Configuration, and User Management
1. Create the directory `/shared-ftp`
1. Allow `read` and `write` access to the ftp `user` and any member of the `ftp` group to `/shared-ftp`
1. Place all users in the `/shared-ftp` directory when they log in and do not allow them to exit the directory.

### M6: FTP Security
1. Block the user `ssh1` from accessing the FTP server only
1. Set the default file upload permissions to be `644`
1. The `ftpuser` can read and write files to the system

### M7: Troubleshooting
To complete `M7` `P1-9 and M1-6` must have a green arrow before starting.

1. The ftp server seems to have gone down. Let's see if you can fix it.

## Distinction Criteria

### D1: SSH Installation and Configuration

1. Allow the users `ssh1`, `blueteam` and `blackteam` to ssh into the server
1. Allow the group `wheel` to ssh into the server
1. Allow the user `ssh2` to ssh into the server but only from `172.18.0.3`
1. Deny the user `redteam` using ssh

### D2: Logging and Monitoring SSH Activity

1. Use a tool to automatically block an IP after `5` failed login attempts for `10 minutes`.
1. This will be graded manually by a TA

## Submission
You don't need to submit anything for this lab. All of the above criteria will be auto-graded unless stated otherwise. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. What is the purpose of SSH, and how does it enhance the security of remote connections?
1. How does changing the default SSH port improve security, and what risks are associated with leaving it unchanged?
1. Why is it beneficial to disable root login for SSH, and how does this impact server security?
1. What are the advantages of using key-based authentication over password-based authentication in SSH?
1. What are the benefits of restricting SSH access to specific IP addresses or user groups and the pros and cons of both approaches?
1. Explain the process of generating SSH key pairs and how they facilitate secure remote connections.
1. How would you manage SSH keys for multiple users on the same system, and why might this be necessary?
1. What purpose does limiting failed login attempts serve in SSH, and how does it protect the server?
1. Why is logging SSH activity essential, and what information can SSH logs provide for security monitoring?
1. What are the advantages of monitoring SSH connections in real-time, especially in a high-security environment?
1. What are common issues with SSH key-based authentication, and how would you troubleshoot them?
1. What is FTP, and how does it differ from SSH in terms of function and security?
1. How does restricting FTP users to their home directories improve security and privacy on a multi-user system.?
1. What is the benefit of disabling anonymous FTP login, and what risks might anonymous access present?
1. Why is SFTP recommended over standard FTP, and how does it improve data security?
1. What are the key differences between active and passive FTP modes, and when would each be used?

### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.
