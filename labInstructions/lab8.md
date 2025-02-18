# Lab 8: Web Servers

## Introduction

In this lab, you will install and configure Nginx as a web server, set up a reverse proxy to route traffic to a Flask application, and implement security hardening measures. You will also learn how to manage firewall rules, monitor server activity through logs, and mitigate common web application vulnerabilities.

### Configuration Instructions

#### Virtual Machines and Operating Systems
You will be working with:  
  - 1 Ubuntu 20.04 Machine

#### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network as follows:  

1. **`Lab-8-webserver` Machine**:  
    - WAN (`ens18` interface):  
        - IP: `172.18.<ID>.12/16`  
        - Gateway: `172.18.0.1`  
        - DNS: `172.18.0.1`  

#### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- To monitor your progress, visit: <a href="http://172.18.0.3/lab/8" target="_blank">scoreboard</a>.

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
- For any questions requiring files to contain specific content, use the `Lab-8-webserver` machine.  

## Pass Criteria

### P1: Web Server Installation and Configuration
1. Install `Nginx`
1. Verify that it is running

### P2: Security Hardening 
1. Disable directory listing 
1. Set the correct file and directory permissions for the website.

### P3: Logging and Monitoring Web Activity
1. Find where the `http` access and error logs are stored. Enter the file location into `/home/blueteam/P3.txt` as `access:<filepath to access log file>` and `error:<filepath to error log file>`

### P4: Firewall and Access Controls
1. Allow `ssh` from only `172.18.0.3`
1. Allow `http` traffic from `172.18.0.3/16`
1. Allow `https` traffic from `172.18.0.3/16`
1. Ensure that the default rules are to `DENY` incoming and `ALLOW` outgoing.

## Merit Criteria

### M1: Web Server Installation and Configuration
1. Set up the website located in `/var/lib/etechacademy`
1. Install any needed packages and dependencies
1. Use the database server you set up in lab 7 as the database for the website. The website user should already have the correct permissions for the website, but you will need to add the IP of the lab-8-webserver machine to the allowed list of IPs.

### M2: Web Server Installation and Configuration
1. Set up a reverse proxy to forward traffic from port `80` to port `5000`

### Distinction Criteria

### D1: Security Hardening 
1. Find and fix the vulnerabilities in the code. This will need to be passed off with a TA.
1. Use the lecture slides and other common web vulnerabilities to get you started.


### D2: Firewall and Access Controls
1. Using the system logs, locate any malicious traffic and block the offending IP address.
1. The rules in `P4` should still apply after any blocked traffic
1. Blocked IPs should be blocked on all ports and protocols in a single rule


## Submission

You don't need to submit anything for this lab. All of the above criteria will be auto-graded unless stated otherwise. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. How do you install Nginx on a Linux system?  
1. What is the purpose of a reverse proxy in a web server architecture?  
1. What logs does Nginx generate, and where can you find them?  
1. How can you test your Nginx configuration before reloading it?  
1. What is CSRF (Cross-Site Request Forgery), and how can you mitigate it in a Flask application?  
1. How do you secure your Flask application by enabling HTTPS?  
1. What are common input validation vulnerabilities in Flask, and how can they be mitigated?  
1. How do you prevent SQL injection attacks in Flask applications using SQLAlchemy?  
1. How can you prevent Cross-Site Scripting (XSS) attacks in Flask applications?  
1. What is the `werkzeug` library, and what security vulnerabilities are associated with it in Flask applications?   
1. What is the potential risk of using `eval()` and `exec()` in Flask, and how can these be mitigated?  
1. How can you configure Flask to avoid directory traversal vulnerabilities when handling file uploads?  

### Grading

- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.