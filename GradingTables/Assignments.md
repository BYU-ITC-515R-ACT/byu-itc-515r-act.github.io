# Grading Tables

## Fortnightly Vulnerability Reports 

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Relevance** | **P1:** The topic is generally related to cybersecurity, with some connection to recent vulnerabilities or defense methods, but lacks specific focus (e.g., vague reference to a broad topic without much detail). | **M1:** The topic is relevant, directly connected to a recent vulnerability (e.g., specific CVE) or a new defense method, showing moderate understanding. | |
| **Clarity and Conciseness** | **P2:** The report explains the topic but may be unclear in parts, contain unnecessary details, or fail to fully convey the significance (e.g., explanations are too broad or lack focus). | **M2:** The report is clear and concise, providing a well-structured, easy-to-understand explanation that delivers in-depth insight without any unnecessary details. |
| **Research and Sources** | **P3:** The report uses at least one credible source, but the research may lack depth or include outdated or less reliable information (e.g., relies on older articles or general websites). | **M3:** The report is well-researched, using at least one current and credible source (e.g., recent journal articles, or official advisories) to support its claims. | **D1:** The report is thoroughly researched, using extensive, up-to-date sources (e.g., peer-reviewed papers, cybersecurity databases, official reports) to demonstrate a deep understanding of the topic. |
| **Presentation and Format** | **P4:** The report follows the basic format (single page, 12pt Times New Roman, double-spaced) but has issues with organization, spelling, or grammar (e.g., several typos, and formatting errors). | **M4:** The report is flawlessly presented, following the required format exactly with no errors in organization, spelling, or grammar. |

## Memes 

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Relevance** | **P1:** The meme mentions cybersecurity or technology, but lacks specific details (e.g., generic reference like “hacking” without any clear context). | **M1:** The meme directly references a specific cybersecurity or technology concept (e.g., mentions firewalls, VPNs, phishing) and shows a moderate understanding of the topic. | **D1:** The meme addresses a specific cybersecurity or technology concept in detail (e.g., references CVEs, encryption algorithms, zero-day exploits), demonstrating strong topic comprehension and relevance. |
| **Creativity and Originality** | **P2:** The meme uses an existing format or popular meme with minimal adaptation (e.g., just replacing text with common terms like “hacker”). | **M2:** The meme adapts a known format but introduces new elements or perspectives (e.g., a cybersecurity twist on a widely used meme format with some originality in text or visuals). | **D2:** The meme is highly creative, using a unique format or an original twist that hasn’t been widely used (e.g., creating a custom meme or applying humor in an unexpected, clever way). |
| **Adherence to Standards**  | **P3:** The meme perfectly aligns with BYU standards and the honor code, maintaining a high level of appropriateness and respect. |

## Homework
| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Accuracy of Answers**     | **P1:**  More than 50% of answers are correct, but there may be significant errors or misunderstandings in some of the questions. | **M1:** More than 70% of answers are correct, demonstrating a good understanding of the material with only minor errors. | **D1:** More than 90% of answers are correct, showing a strong grasp of the material with minimal to no errors. |

## Lab 1: CLI (Command Line Interface)

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **File and Directory Operations** | **P1:**  Create new directories. Navigate between directories using. Create and delete files. Move and rename files and directories. Copy files between directories. Display the current working directory. View the last and first 10 lines of a file. View the end of a file live and see changes as lines are added.| **M1:** Create a text file using redirection. Use `grep` to search for specific strings in files. Modify files using `sed`. Count words, lines, and characters in a file using. Combine commands using pipes. Create hard and symbolic links.| **D1:** Copy an entire directory recursively to another location. Remove all files and subdirectories inside a directory recursively. Count all the files inside a directory recursively. Find all files in a directory by name, type, last modified, and file size. Set special and extended file permissions. Find files and run commands on matching results.|
| **Text Editor Basics** | **P2:** Open a new file in `nano`, write some text, and save/exit. Use `nano` to find and replace text within a file. | **M2:** Open and edit files using `vim`. Use `vim` commands to search for a word and delete a line. | |
| **Permissions and Ownership** | **P3:** List the contents of directories using various flags. View file permissions and ownership. Modify file and folder permissions, owners, and groups. | **M3:** Change permissions and owners of all files and subdirectories in a directory | |
| **User and Group Management** | **P4:** Add users with and without, login shells, home directories, and passwords. Modify groups a user is part of and view group information for a user. | | |
| **Archiving and Compression** | **P5:** Create and extract compressed files. | | |
| **Networking** | **P6:** Check the current network configuration. Test network connectivity with `ping`. Download a file from the internet. | **M4:** Display open, active and listening connections | **D2:** Trace a network connection to a running process |
| **Process Management** | **P7:** List running processes. View CPU and memory usage. | **M5:** Create and manage cron jobs. Terminate a process with a given PID. | **D3:** List all open files, find the open files used by a specific user, and check which files a specific process is using |
| **Disk Usage and Filesystem Management** | **P8:** Check available disk space. View directory size. | **M6:** Mount and unmount a file system. Create a new partition | |
| **Package Management** | **P9:** Search for and install software. Remove a package. | **M7:** Update package repositories and upgrade the system. Verify the file integrity of all the bin files. |  |
| **Verbal Pass off** | **P10:** Successfully answer two TA chosen pass off questions.|

## Lab 2: Basic Networking 
| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **IP Address Configuration** | **P1:** The IP address is correctly configured for all systems, and all machines can ping each other and the gateway. |
| **Subnet Mask Configuration** | **P2:** The subnet mask is correctly applied for all systems. |
| **Gateway Configuration** | | **M1:** The gateway is correctly configured for all systems and can ping a public IP of the TA choice. |
| **DNS Configuration** | | | **D1:**  A primary and backup DNS server has been correctly configured for all systems and can ping a domain of the TA choice. |
| **Verbal Pass off** | **P3:** Successfully answer two TA chosen pass off questions.|

## Lab 3: SSH (Secure Shell) & FTP (File Transfer Protocol)

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **SSH Installation and Configuration** | **P1:**  Install the OpenSSH server and client. Connect to the server from a client machine. | **M1:** Modify the SSH configuration file to change the default port. Disable root login and password-based authentication in favor of key-based authentication. | **D1:** Configure SSH to use specific IP addresses, and user and group restrictions. |
| **SSH Key Generation and Management** | **P2:**  Generate SSH key pairs using `ssh-keygen`. Copy the public key to a remote server and connect using key-based authentication. | **M2:** Manage multiple SSH keys for different users. | |
| **SSH Hardening** | **P3:** Limit the number of failed login attempts, set timeout restrictions and max sessions. | | **D2:** Use a tool to automatically block IPs after several failed login attempts. |
| **SSH File Transfers** | **P4:**  Securely copy files between local and remote systems. | | |
| **Logging and Monitoring SSH Activity** | **P5:**  View basic SSH logs and identify failed login attempts and successful connections. | **M3:** Configure SSH to log more detailed activity, including the commands run by authenticated users. |  |
| **Troubleshooting** | **P6:**  Verify SSH service status. Check config files for syntax errors and/or misconfigurations. | **M4:** Investigate key-based authentication issues. |  |
| **FTP Installation, Configuration, and User Management** | **P7:** Install an FTP server. Connect to the FTP server from a client using an FTP client or command-line tool. Create FTP-specific users on the server. Assign home directories for FTP users. Limit FTP users to their home directories. | **M5:** Set up default directories for users. Set different permissions for different users. | |
| **FTP Security** | **P8:** Disable anonymous login to the FTP server. | **M6:** Modify the FTP configuration to restrict access to users or groups. |  |
| **Troubleshooting** | **P9:** Verify the FTP service status. Ensure that the correct port(s) are configured. Check the FTP server configuration files for syntax errors | **M7:** Check the FTP server configuration files for misconfigurations. Diagnose connection issues related to passive and active FTP modes. Review logs for failed login attempts or file transfer errors. Verify the FTP server allows the correct type of authentication. |  |
| **Verbal Pass off** | **P10:** Successfully answer two TA chosen pass off questions.|

## Lab 4: DNS (Domain Name System)

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **DNS Installation and Configuration** | **P1:** Install a DNS server. Configure basic DNS zone files (forward and reverse) | **M1:** Configure DNS with multiple zones, including forward and reverse lookups. Set up multiple record types. | **D1:** Resolve internal and external queries |
| **DNS Security** | | **M2:** Limit queries to set IP ranges | **D2:** Disable zone transfers to unauthorized IP addresses. Limit recursive queries to internal networks. |
| **Troubleshooting DNS** | **P2:** Verify that the DNS service is running. Query DNS records and test DNS resolution for different record types. View basic DNS logs. | **M3:** Identify and resolve common DNS issues | | |
| **Verbal Pass off** | **P3:** Successfully answer two TA chosen pass off questions.|

## Lab 5: Routers & Firewalls

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Firewall Installation and Basic Configuration** | **P1:** Install, enable, and start various firewall services. Verify firewall statuses. | **M1:** Configure basic firewall rules to allow/deny specific services. Create rules to allow traffic only from specific IP addresses or networks. | **D1:** Create advanced firewall rules to allow/deny specific services, ports, protocols, and IP addresses |
| **Configuring Ports and Services** |  **P2:** List the currently open ports and services on the firewall. |  | |
| **Firewall Zones and Profiles** | **P3:** Assign network interfaces to specific firewall zones. | |  |
| **Securing Incoming and Outgoing Traffic** | **P4:** Set default policies for incoming and outgoing traffic. | **M2:** Implement rules to block traffic from known malicious IPs using threat intelligence lists. Set up firewall rules to prevent specific types of network attacks.  | **D2:** Limit the number of concurrent connections or rate limit traffic for specific services.|
| **Logging and Monitoring Firewall Activity** | **P5:** View basic firewall logs to monitor incoming and outgoing traffic. Debug firewall service errors. | **M3:**  Set up detailed logging of dropped or accepted packets, including source/destination IP and ports. | **D3:** Set up geo-blocking to deny traffic from specific countries or regions.|
| **Firewall Performance Optimization** | **P6:** Optimize rule ordering | **M4:** Identify and remove redundant and unused rules |
| **Router Installation and Basic Configuration** | **P7:** Install and configure a basic router. Set up routing between multiple networks.   |   |  |
| **Routing and NAT Configuration**  | **P8:** Configure basic NAT to allow internal network access to the internet.   | **M5:** Set rules for port forwarding to internal IPs  |  |
| **Verbal Pass off** | **P9:** Successfully answer two TA chosen pass off questions.|

## Lab 6: Backups

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Backup Tool Installation and Configuration** | **P1:** Install a backup tool. Verify installation by running a test backup. | **M1:** Configure automated backups. Define the backup source and destination files and directories. Implement incremental backups to only back up changes made since the last backup. | **D1:** Set up differential backups for faster restore times. Automate the cleanup of old backups to save disk space. |
| **Backup Verification** | **P2:** Verify that backup files have been created successfully. Check file integrity after each backup. | | **D1:** Secure backups by encrypting them. |
| **Cloud Backups** | | **M2:** Copy backups to an offsite cloud solution. | **D2:** Set up automated remote backups. |
| **Backup Restoration** | **P3:** Perform basic file restoration from a backup. | **M1:** Test full system restores to ensure that all files and configurations are restored correctly. | **D1:** Automate the restoration process. |
| **Verbal Pass off** | **P4:** Successfully answer two TA chosen pass off questions.|

## Lab 7: Database Servers

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Database Installation and Setup** | **P1:** Install a relational database management system. Verify the database service is running and accessible from localhost. | **M1:** Create a basic database and table using SQL commands. Create a basic database and table using an SQL file. Configure the database from remote access and connections. | 
| **Database User Management** | **P2:** Create database-specific users and assign privileges using least privilege principles |  |
| **Database Security** | **P3:** Disable root access for remote connections. | **M2:** Disable root account access to the database. Enforce strong password policies. | 
| **Database Backup and Recovery** | | **M3:** Create a manual backup of the database and verify the integrity of backups. | **D1:** Set up automated backup schedules |
| **Database Monitoring and Logging** | | **M4:** View database logs to track user connections, query execution, and errors. |
| **Database Hardening** | **P4:** Remove unnecessary default users, databases, and services. | | **D2:** Restrict database access by IP address or subnet. | 
| **Verbal Pass off** | **P5:** Successfully answer two TA chosen pass off questions.|

## Lab 8: Web Servers

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Web Server Installation and Configuration** | **P1:** Install a web server and verify the web service is running. | **M1:** Set up a website from the provided code and host it on the server. Set up and manage server modules. Configure the server to host multiple websites. Customize server settings | **D1:** Configure advanced settings like reverse proxying. Set up multiple domains and subdomains with SSL/TLS encryption. |
| **Security Hardening** | **P2:** Disable directory browsing and prevent access to sensitive files. Set proper file and directory permissions for the web root. ||
| **Logging and Monitoring Web Activity** | **P3:** View basic access and error logs |  **M2:** Enable logging of HTTP requests and responses for auditing purposes. |
| **Firewall and Access Controls** | **P4:** Set up firewall rules to restrict access to the web server. | | **D2:** Block malicious source IPs using log files. |
| **Website Backup and Recovery** | | **M3:** Create a manual backup of the website and verify the integrity of backups. | **D3:** Set up automated backup schedules |
| **Verbal Pass off** | **P5:** Successfully answer two TA chosen pass off questions.|

## Lab 9: Hardening


| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **System Commands** | **P1:** Restore basic user-level system commands to correct functionality. | **M1:** Restore system-level binaries to correct functionality.    | **D1:** Fully restore all command functions. |
| **Scheduled Tasks** | **P2:** Review and remove obvious malicious scheduled tasks. | **M2:** Identify and remove condition-based automated tasks. | **D2:** Review and remove deeply embedded malicious system tasks. |
| **Update and Package Management** | **P3:** Update and upgrade packages. |   | **M3:** Remove restrictions on firewall installation. |
| **Firewall and Network Security** | | **M4:** Install a firewall and configure it to block malicious traffic.   |  |
| **User and Group Management** | **P4:** Remove obvious malicious users and secure legitimate users.  | **M5:** Identify and remove hidden malicious users.  | **D3:** Implement secure user password and hashing policies. |
| **SSH Security** | **P5:** Configure secure SSH settings, allowing legitimate users to use their SSH keys.  | **M6:** Remove malicious SSH settings and configurations.| **D4:** Terminate and block malicious SSH sessions. |
| **Malicious Programs and Software** | **P6:** Remove any bind or reverse shells. | **M7:** Identify and remove password loggers.  | **D5:** Find the rest of the malicious treats. |
| **Folder and File Permissions** | **P7:** Ensure critical files have correct permissions.  |  |  |
| **Verbal Pass Off** | **P8:** Successfully answer two pass-off questions chosen by the TA. |  |  |


## Lab 10: Script Writing

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Script Approval** | **P1:** Get the script idea approved by the Professor or a TA. |
| **Script Creation** | **P2:** Write a basic script using a shell scripting language to automate a security-related task. Include detailed comments for code readability.  | **M1:** Write a script with user input and conditional statements to perform different actions based on user input. Use loops to iterate over files or data. | **D1:** Write a script that uses functions to modularize tasks and error-handling mechanisms to ensure reliability.  |
| **Scheduling and Automation** | **P3:**  Schedule a script to run at a specific time. | 
| **Error Handling and Logging** | | **M2:** Include basic error handling in your script to display error messages when something goes wrong. | **D2:** Use advanced error handling to manage exceptions, log errors, and gracefully exit when the script encounters an issue. | 
| **Security and Permissions** |  **P5:** Ensure the script has appropriate file permissions and runs with the correct user privileges. | | **D3:** Write a script that includes permission checks to ensure it is being run by the correct user or group.  |
| **Verbal Pass off** | **P6:** Successfully answer two TA chosen pass off questions.|

## Team Lab 1: Set Up Practice

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Service Functionality**  | **P1:** At least 50% of services are correctly scoring. | **M1:** At least 75% of services are correctly scoring. | **D1:** All services are correctly scoring. |
| **Peer Evaluation**   |  **P3:** Peer evaluation indicates the bare minimum participation was given and there is major room for improvement. | **M3:** Peer evaluation indicates good participation was given and there is minor room for improvement. | **D3:** Peer evaluation indicates expectations were exceeded and there is little to no room for improvement. |

## Team Lab 2: Red Team Practice

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Service Functionality**  | **P1:** At least 750 points have been scored. | **M1:** At least 1500 points have been scored. | **D1:** At least 2500 points have been scored. |
| **Peer Evaluation**   |  **P3:** Peer evaluation indicates the bare minimum participation was given and there is major room for improvement. | **M3:** Peer evaluation indicates good participation was given and there is minor room for improvement. | **D3:** Peer evaluation indicates expectations were exceeded and there is little to no room for improvement. |
