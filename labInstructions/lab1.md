# Lab 1: Command Line Interface (CLI)

## Introduction
In this lab assignment, you will explore the Linux CLI, which is essential for effective system administration and development tasks. The assignment is designed to enhance your command-line skills through hands-on practice with various operations related to files, directories, permissions, text editing, user management, networking, process management, and package management. You will work through a series of tasks categorized by levels of mastery: Pass, Merit, and Distinction.

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
  - 1 Ubuntu 20.04 Machine

### Network Configuration

Your machine already has internet access set up and can be accessed through your `Proxmox` instance. In future labs, you will practice setting the network settings but for this lab, it has been done for you. 

### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- To track your progress, visit the <a href="http://172.18.0.3/lab/1" target="_blank">scoreboard</a>.
- You need to be connected to the VPN to access the scoreboard and your Proxmox instance.

### Scoreboard Key
- **Green arrows** indicate that everything is working as intended.
- **Orange Exclamation** indicates that something is partially working. 
- **Red down arrows** indicate that something is not working.

You can hover over your specific arrow and a tooltip will appear with a hint on what is wrong or not working.

#### Lab Time Estimates

- **Pass** : 1.5 hours
- **Merit**: 2.5 hours
- **Distinction**: 4 hours

#### **Credentials**  
- All VMs have the same login credentials:  
  - **Username**: `blueteam`  
  - **Password**: `abc123`

## Connecting to Proxmox

1. Install OpenVPN on your computer:
   - Download the installer [here](https://openvpn.net/client/).
   - After installation, import the VPN profile that was emailed to your BYU email address.
   - Connect to the VPN.

1. Access Proxmox:
   - In your browser, navigate to the Proxmox URL from the email (e.g., `https://172.18.<ID>.100:8006`, where 'ID' is your user ID).
   - You will see a warning when the page loads. This is expected due to Proxmox's self-signed TLS certificate. Click `Advanced`, then `Proceed to...`.

1. Login to Proxmox:
   - Username: `student`
   - Password: Use the password sent to you via email.
   - Change the `Realm` from `Linux PAM standard authentication` to `Proxmox VE authentication server`.
   - Click `Login`.
   - You should see the Lab1 VMs in the panel on the left-hand side. You may have to expand the node button (It has the green checkmark next to it) to see them.


### Scoring Advice
There may be a way to achieve a criteria that we have not accounted for. If you believe your method meets the criteria but is not being scored please reach out to a TA.

## Pass Criteria

### P1: File and Directory Operations

1. Create a directory called `P1` in `/home/blueteam/`.
1. Change the directory you're in to the `P1` directory you just created.
1. Use `touch` to create a file called `P1.txt`
1. Display the full path of your current directory. Enter the line `path:<command>` into the file `/home/blueteam/P1/P1.txt`
1. Use `tail` to view file changes in `/var/log/auth.log` in real-time. Enter the line `live-tail:<command>` into the file `/home/blueteam/P1/P1.txt`
1. View the first 10 lines of `/var/log/auth.log` using `head`. Enter the line `head:<command>` into the file `/home/blueteam/P1/P1.txt`
1. View the last 10 lines of `/var/log/auth.log` using `tail`. Enter the line `tail:<command>` into the file `/home/blueteam/P1/P1.txt`
1. Delete the directory `/home/blueteam/P1-delete-me`
1. Move and rename the file in a single command `/home/blueteam/P1-move-me.txt` to `/home/blueteam/P1/moved.txt`.
1. Copy the file  `/home/blueteam/P1-copy-me.txt` to `/home/blueteam/P1/P1-copy-me.txt`

### P2: Text Editor Basics
1. Create `/home/blueteam/P2/P2.txt` using nano and put the line `nano is too easy` as the first line
1. Open the file `/home/blueteam/P2/P2-2.txt` and use the find and replace to change every instance of `Vim` to `Nano`

### P3: Permissions and Ownership
1. View file permissions and ownership using `ls`.
    - List all files (including hidden ones) contained in `/home/blueteam/P3/`. Enter the line `hidden:<command>` into the file `/home/blueteam/P3/P3.txt`. Run the command from inside of the `P3` directory.
    - List all files (including hidden ones) and use the long list format on the file in `/home/blueteam/P3/`. Enter the line `hidden-long:<command>` into the file `/home/blueteam/P3/P3.txt`. Run the command using the absolute file path.
1. Modify file and folder permissions using `chmod`.
    - Change the permissions on the hidden file in `/home/blueteam/P3` to be read only by the file owner and no permissions to anyone else
    - Change the permissions on the file `/home/blueteam/P3/P3-3.txt` to be read and write by the owner and read only by others in the group and all others
1. Change file owners and groups using `chown`.
    - Change the owner of the hidden file to `blueteam` and the group to `sudo`
    - Change the owner of the file `/home/blueteam/P3/P3-4.txt` to `root`
    - Change the group of the file `/home/blueteam/P3/P3-2.txt` to `blueteam`

### P4: User and Group Management
1. Add users with/without login shells, home directories, and passwords using `useradd` or `adduser`
    - Create a user called `no-shell` that does not have a shell or password they can log in with but does have a home directory. It should say `/usr/sbin/nologin` or `/bin/false` for the user in `/etc/passwd` after the user has been created
    - Create a user called `shell` that has a shell and password they can use to log in, but no home directory
    - Create a user called `no-password` that has a shell, but no password they can log in with, and no home directory
    - Create a user called `login` with a login shell, home directory, and a password they can log in with
1. Modify groups that a user belongs to using `usermod` and view group info using `groups`
    - Add the `login` user to the `sudo` group
    - Remove the `backup` user from the `redteam` group 

### P5: Archiving and Compression
1. Create compressed files using `zip`. Compress the directory `/home/blueteam/P5/` and all of its contents into a zip called `P5.zip` and put it in `/home/blueteam`
1. Extract compressed files using `zip`. Extract the zip `/home/blueteam/P5-unzip.zip`. Make sure the directory that contains all the extracted files is located at `/home/blueteam/P5-unzip/`

### P6: Networking
1. Check network configuration. Enter the line `network:<command>` into the file `/home/blueteam/P6/P6.txt`
1. Test connectivity to `google.com` using an ICMP-based check. Enter the line `ping:<command>` into the file `/home/blueteam/P6/P6.txt`
1. Download the `google.com` homepage from the internet. Enter the line `download:<command>` into the file `/home/blueteam/P6/P6.txt`. Make sure you get the homepage and not a redirect page.

### P7: Process Management
1. List running processes using `ps` that displays processes for all users in a user-oriented format that includes processes without a terminal. Enter the line `ps:<command>` into the file `/home/blueteam/P7/P7.txt` and enter the flags in alphabetical order
1. View CPU and memory usage using `top` that displays only the processes for the `blueteam` user. Enter the line `top:<command>`into the file `/home/blueteam/P7/P7.txt`

### P8: Disk Usage and Filesystem Management
1. Check how much space is left on the disk using the `df` command and a flag to make the data human readable. Enter the line `df:<command>`into the file `/home/blueteam/P8/P8.txt`
1. Check how large the `/opt/` directory is using the `du` command and display the size in `K`. Enter the line `du:<command>` into the file `/home/blueteam/P8/P8.txt`

### P9: Package Management
1. Install the package `net-tools` using `apt`
1. Completely `remove` and `purge` the package `nmap` using `apt`

### Merit Criteria:

### M1: File and Directory Operations
1. Count words, lines, and characters. Use the file `/home/blueteam/M1/Never-Gonna-Give-You-Up.txt` and put your answers in `/home/blueteam/M1/M1.txt`
    - Count the number of words in the file and enter the line `word-count:<command>,<number of words>` into the `/home/blueteam/M1/M1.txt` file. Ensure that the only number your command returns is the word count.
    - Count the number of lines in the file and enter the line `lines:<command>,<number of lines>` into the `/home/blueteam/M1/M1.txt` file
    - Count the number of characters in the file and enter the line `char:<command>,<number of characters>` into the `/home/blueteam/M1/M1.txt` file
    - Count the number of times `Never` appears in the file and enter the line `never:<number of times>` into the `/home/blueteam/M1/M1.txt` file
1. Use `sed` to replace the word "Always" with "Never" in the file `/home/blueteam/M1/Never-Gonna-Give-You-Up-sed.txt`. Enter the line `sed:<command>`into the `/home/blueteam/M1/M1.txt` file
1. Combine the commands `cowsay` and `fortune` to make the cow say a fortune. Enter the line `cowsay:<command>`into the `/home/blueteam/M1/M1.txt` file
1. Create a hard link to `/home/blueteam/M1-hardlink.txt` called `M1-hardlink.txt` in `/home/blueteam/M1/`:
1. Create a symbolic link to `/home/blueteam/M1-symlink.txt` called `M1-symlink.txt` in `/home/blueteam/M1/`:

### M2: Text Editor Basics
1. Open the file `/home/blueteam/M2/WeLoveVim.md` using `VIM` and add the line `I <3 VIM` as the last line of the file
1. Using the same file as above use `VIM` to find and replace every instance of `Nano` to `Vim`

### M3: Permissions and Ownership
1. Using recursion change the owner of all files and directories in `/home/blueteam/M3` to `blueteam:sudo`
1. Using recursion change the file (not folder) permissions of all files in `/home/blueteam/M3` to `640`

### M4: Networking
1. Display all `tcp` and `udp` connections using `netstat`. Enter the line `tcp-udp:<command>` into the `/home/blueteam/M4/M4.txt` file
1. Display all connections. Enter the line `all:<command>` into the `/home/blueteam/M4/M4.txt` file
1. Display all listening sockets. Enter the line `listening:<command>` into the `/home/blueteam/M4/M4.txt` file
1. Display all TCP and UDP connections that are listening and show the numerical addresses instead of resolving the hostnames. Enter the line `everything:<command>` into the `/home/blueteam/M4/M4.txt` file. Order the flags in alphabetical order.

### M5: Process Management
1. Create a cronjob for the `blueteam` account that will execute `/home/blueteam/M5/cronScript.py` every `5 minutes`. The cronjob should be placed in your user's `crontab`
1. Terminate the process that is running `pleasekillme.py` and remove the cronjob that is enabling it to be persistent but do not remove the script. 

You can remove scripts that point to blackteam but do not remove the scripts themselves. Note that the redteam may use accounts that seem to be out of scope to maintain persistence in your system.

### M6: Disk Usage and Filesystem Management
1. Partition the drive `sdb` to use `xfs` and mount the directory `/mnt/M6-mount` to `sdb`
1. Unmount the drive mounted to `/mnt/M6-unmount`

### M7: Package Management
1. Update and upgrade all packages
1. Verify the integrity of system binaries and repair any binaries that do not match 

## Distinction Criteria:

### D1: File and Directory Operations

1. Copy the directory `/home/blueteam/D1` and all of its contents to `/home/blueteam/D1-copy` using recursion. Enter the line `copy:<command>` into the `/home/blueteam/D1/D1.txt` file.Use the full filepath in the command.
1. Count the number of files in the directory `/home/blueteam/D1` using recursion. Enter the line `count:<count>` into the `/home/blueteam/D1/D1.txt` file.
1. Remove all files and subdirectories from `/home/blueteam/D1-copy` using recursion. Enter the line `remove:<command>` into the `/home/blueteam/D1/D1.txt` file. Use the full filepath in the command.
1. Locate files by name, type, modification date, and file size.
    - Locate all files with `game` in the name. Enter the line `game:<command>` into the `/home/blueteam/D1/D1.txt` file
    - Locate all `python` files on the system. Enter the line `python:<command>` into the `/home/blueteam/D1/D1.txt` file
    - Locate all files that are larger than `1GB`. Enter the line `1GB:<command>` into the `/home/blueteam/D1/D1.txt` file
    - Locate all files with the `Set User ID` permissions set. Enter the line `SUID:<command>` into the `/home/blueteam/D1/D1.txt` file
1. Add the `Set User ID` permission to the file `/home/blueteam/D1/script.py`

### D2: Networking
1. Something is listening on port 1337. Find the PID of the process. Enter the line `sus:<filepath>` (with the filepath of the file that is running in the process) into the `/home/blueteam/D2/D2.txt` file
1. Kill the process you identified and stop it from respawning.

### D3: Process Management
1. List all open files. Enter the line `all-files:<command>` into the `/home/blueteam/D3/D3.txt` file
1. List all open files for the root user. Enter the line `root-files:<command>` into the `/home/blueteam/D3/D3.txt` file
1. List all open files for SSH for your current `SSH` session. Enter the line `ssh-files:<command>` into the `/home/blueteam/D3/D3.txt` file

## Submission
You don't need to submit anything for this lab. All of the above criteria will be auto-graded unless stated otherwise. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. What is the purpose of creating directories and files in Linux, and how does it help in organizing system resources?
1. Why might it be important to view the full path of your current directory, especially when working with scripts or configuration files?
1. What are some reasons you might want to monitor log files like `/var/log/auth.log` in real-time, and how could this benefit system security?
1. In what scenarios would it be useful to view the first or last few lines of a file with commands like `head` and `tail`?
1. How can the `find and replace` feature be useful in text editors when updating configuration files or scripts?
1. What does listing hidden files and viewing permissions reveal about the security and access control of a directory?
1. Why is it essential to set specific permissions on files, and what could happen if permissions are too open or too restrictive?
1. What is the significance of file ownership in Linux, and why would you change a file’s owner to `root` in certain cases?
1. Why might you create a user without a login shell or password, and in what scenarios could this type of user account be necessary?
1. What is the role of groups in Linux, and how does adding a user to the `sudo` group affect their system privileges?
1. Why is compressing files and directories useful in Linux, and how does it impact storage and file transfers?
1. Why would you want to download a web page from the internet using a command, and what are some examples of how this is used in system administration?
1. What information does the `ps` command provide about processes, and how does viewing processes for all users improve system monitoring?
1. Why might you filter processes in `top` to show only those for a specific user, and how does this assist in resource management?
1. What are the advantages of using human-readable formatting when checking disk usage, and what critical information can this reveal?
1. What role does package management play in Linux, and why is it crucial to verify that a package is fully installed or completely removed?

### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.



