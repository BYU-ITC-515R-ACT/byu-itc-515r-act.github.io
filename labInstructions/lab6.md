# Lab 6: Backups

## Introduction

In this lab, you'll focus on creating and managing backups for essential network services and systems to ensure data integrity and quick recovery in case of failure or redteam activities. You'll practice configuring automated and secure backup strategies.

### Configuration Instructions

#### Virtual Machines and Operating Systems
You will be working with:  
- 1 Ubuntu 20.04 Machine
- 2 Rocky 7 Machines

#### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network as follows:  

1. **`Lab-6-SSH-FTP` Machine**:  
    - WAN (`ens18` interface):  
        - IP: `172.18.<ID>.7/16`  
        - Gateway: `172.18.0.1`  
        - DNS: `172.18.0.1`  

1. **`Lab-6-DNS` Machine**:  
    - LAN (`ens18` interface):  
        - IP: `172.18.<ID>.8/16`    
        - Gateway: `172.18.0.1`  
        - DNS:  `172.18.0.1`  

1. **`Lab-6-Backup` Machine**:  
    - LAN (`ens18` interface):  
        - IP: `172.18.<ID>.9/16`   
        - Gateway: `172.18.0.1`  
        - DNS: `172.18.0.1`  

#### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- To monitor your progress, visit: [http://172.18.0.3/lab/6](http://172.18.0.3/lab/6). 

#### Scoreboard Key
- **Green arrows** indicate that everything is working as intended.
- **Orange exclamation marks** indicate that something is partially working.
- **Red down arrows** indicate that something is not working.

You can hover over each specific arrow, and a tooltip will appear with a hint on what is wrong or not working.

#### **Credentials**  
- All VMs have the same login credentials:  
  - **Username**: `blueteam`  
  - **Password**: `abc123`  

#### **File Creation and Content**  
- If a referenced file does not exist, you must create it.  
- For any questions requiring files to contain specific content, use the `Lab-6-backup` machine.  


## Pass Criteria

### P1: Backup Tool Installation and Configuration

Install a backup tool. Verify installation by running a test backup. 
1. Install `rsync` onto each machine.
1. Using rsync backup the file `/etc/ssh/sshd_config` from the `Lab-6-SSH-FTP` machine to the `Lab-6-Backup` machine. Place the backup file in the `/backups/ssh-ftp` directory.

### P2: Backup Verification
1. Compare the MD5 file hash of the original file and the backup. Enter the lines `original:<filehash>` and `backup:<filehash>` into the file `/home/blueteam/P2/P2.txt` on the `Lab-6-Backup` machine.
1. The file hashes should be the same. If they are not the file has been changed.

### P3: Backup Restoration
To complete `P3` `P1-P2` must have a green arrow before starting.

1. Check the hashes again. This time they should be different.
1. Use rsync to restore the backup file from `Lab-6-Backup` to `Lab-6-SSH-FTP`.

## Merit Criteria

### M1: Backup Tool Installation and Configuration

1. Automate the backup of sshd_config from `Lab-6-SSH-FTP` to `Lab-6-Backup` (using the blueteam crontab) to run every 2 minutes and only backup files that have been changed since the last backup. Ensure that you preserve:
  - file permissions
  - file owner(s)
  - timestamps

1. Back up the following files and directories:
- Lab-6-SSH-FTP
  - `/etc/ssh/sshd_config`
  - `/etc/vsftpd.conf`
  - `/etc/shadow`
  - `/etc/passwd`

- Lab-6-DNS
  - `/etc/ssh/sshd_config`
  - `/etc/named.conf`
  - `/etc/shadow`
  - `/etc/passwd`

- Place the backups in `/backups/ssh-ftp` and `/backups/dns` respectively on the `Lab-6-Backup` machine.

### M2: Cloud Backups  
1. Choose an offsite solution to back up 3 of the files outlined in `M1`. Some options include `Google Drive`, `Dropbox`, `OneDrive`, `GitHub` etc. We would advise against using your personal accounts for this, especially during the competition, as the redteam may compromise your real account credentials if you use them.

   **Note:** If you back up valid and secure configuration files of various places to a public github repo, you can use those during the NCAE competition either to reset your service configuration or to reference as you secure it :)

1. This will need to be passed off manually with a TA.

## Distinction Criteria

### D1: Backup Restoration
To complete `D1` `P1-P3` and `M1` must have a green arrow before starting.
1. It appears that some of your files have been maliciously altered since you backed them up. Using rsync restore all the files from the `Lab-6-Backup` machine to their original machine, only if the file has changed.


## Submission
You don't need to submit anything for this lab. All of the above criteria will be auto-graded unless stated otherwise. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. Why would you want to back up files?
2. What strengths does rsync have to other backup solutions?
3. What are some risks of automating backups / restores?
4. What would YOU do in a competition setting for backups?

### Grading

- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.

