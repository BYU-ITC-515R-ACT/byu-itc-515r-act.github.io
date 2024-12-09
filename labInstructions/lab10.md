# Lab 10: Script Writing

## Introduction


Resources to assist with the lab:  
1. Homework Questions  
1. Class Resources Repository 
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
  - 1 Ubuntu 20.04

### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network. You can use any IPs in your assigned range for the VMs.

### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- There will be no scoreboard for this lab. A full pass-off with a TA will need to be completed. 
- You need to be connected to the VPN to access your Proxmox instance.

#### **Credentials**  
- All VMs have the same login credentials:  
  - **Username**: `blueteam`  
  - **Password**: `abc123`  

## Pass Criteria

### P1: Script Approval

1. Before you begin creating your script the professor or TA must approve the idea to ensure it meets the minimum requirements. Your script must work on both Ubuntu 20.04 and CentOS 7. 
1. Here are some ideas that you could use:
    - Automated Firewall Configuration  
    - Checksum Integrity Verifier  
    - Database Security Checker  
    - Database Setup  
    - DNS Setup  
    - FTP Security Checker  
    - Log File Analyzer  
    - Open Port Enumerator  
    - Process Monitor for Suspicious Activity  
    - Sensitive File Scanner  
    - SSH Security Checker  
    - Suspicious Network Activity Logger  
    - User Account Monitoring  
    - Web Setup  

### P2: Script Creation

1. Create a basic script using one of the following options (Bash or Python are recommended):
    - Bash
    - Python
    - Perl
    - Ruby
1. Include detailed code comments

### P3: Scheduling and Automation

1. Schedule the script to run at a specific time using a method that ensures it runs consistently and persists across reboots.

### P4: Security and Permissions

1. Ensure the script has the correct file permissions and runs with the appropriate user privileges to execute all functionality properly.  


## Merit Criteria

### M1: Script Creation

1. Include functionality that:
    - Accepts user input.
    - Uses conditional statements to perform actions based on the input.
    - Uses loops to iterate over files or data.

### M2: Error Handling and Logging

1. Include basic error handling in your script to display error messages when something goes wrong.


## Distinction Criteria

### D1: Script Creation

1. Include functions to modularize tasks and error-handling mechanisms to ensure reliability.

### D2: Error Handling and Logging

1. Use advanced error handling to manage exceptions, log errors, and gracefully exit when the script encounters an issue.

### D3: Security and Permissions

1. Include permission checks within the script to ensure it is being run by the correct user/group and with the correct permissions.

## Submission
You will need to submit your script for this lab. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. Can you describe the purpose of the script you created and how it meets the requirements of the assignment?
1. How does your script accept user input, and how does it handle different types of input?
1. Can you explain the conditional statements used in your script and how they determine the flow of execution?
1. What is the purpose of the loop in your script, and how does it iterate over files or data?
1. Can you explain how you ensured your script handles edge cases or unexpected inputs?
1. How does your script behave when the user provides invalid input or when an error occurs?
1. Could you describe the different components or functions you used in your script to modularize tasks?
1. How does your script handle the case where a required file or resource is missing?
1. Could you walk me through how the script would behave if it encountered an unexpected system failure?
1. How did you test your script to ensure it works correctly before scheduling it for automation?
1. What steps did you take to ensure the script runs with the correct user privileges and permissions?
1. How does your script ensure it has the appropriate permissions to perform its tasks on sensitive files or services?
1. Can you explain how you set the file permissions for your script and why that was necessary?
1. How does your script check and validate that it is being run by the correct user or group?
1. What actions does your script take to prevent unauthorized access or potential security risks during execution?
1. How did you schedule your script to run at a specific time, and how did you ensure it persists across reboots?
1. What scheduling tool did you use (e.g., cron, systemd), and why did you choose that method for your script?
1. Can you explain the process of making your script run automatically without manual intervention after reboot?
1. What happens if your script fails to execute during the scheduled time? How does it handle that situation?
1. Can you describe how the script maintains functionality even if the system is rebooted during execution?



### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.