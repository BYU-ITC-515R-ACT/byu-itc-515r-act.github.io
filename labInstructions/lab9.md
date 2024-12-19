# Lab 9: Hardening

## Scenario

Welcome to Apex Innovations! We are a leading provider of advanced cybersecurity solutions and digital transformation services for businesses worldwide. Our mission is to protect organizations from evolving cyber threats while enabling them to innovate and grow in a secure environment. With a dynamic team of experts and cutting-edge technologies, Apex Innovations empowers clients to stay one step ahead in an increasingly complex digital landscape.

As a newly hired Security Analyst, you’ve been assigned to secure our flagship project server, which will serve as the backbone for our ongoing development efforts. This server will host critical information for both our internal teams and high-profile clients. Due to recent security breaches, there’s a possibility that the server has been compromised by malicious actors. Your predecessor left under mysterious circumstances, and it’s unclear whether the system was fully cleared of any threats. It’s now your responsibility to identify and eliminate any hidden vulnerabilities, malware, or unauthorized access points that may remain, ensuring that no sensitive client or corporate data is put at risk.

The stakes are high as Apex Innovations’ reputation is on the line. The breach could be the work of a competitor trying to sabotage the company or a former insider seeking revenge. With advanced tools and persistent attackers out there, you must act swiftly to secure the system. Your job is to restore confidence in the integrity of the server, keep an eye out for any signs of further compromise, and ensure that everything is locked down before transferring any high-value data.

Be vigilant—every move counts and the attackers may be closer than you think!

## Rules
- Do not block port 2222, this port is used by the blackteam to score your machine.
- Do not remove the Proxmox user agent which is called `qemu-guest-agent`
- To receive points for the lab, your VM must be powered on and still scorable after the lab.
- Any attempt to manipulate or gain access to the scoring machines will be considered cheating.
- Attempting to access the scoring engine from your competition VM is out of scope.
- This assignment is graded on an individual basis; however, you may collaborate in a group of 2 to 3 people to help bounce ideas off each other. Do not share details of the lab outside your group.
    - Inform TAs who you are working with. No daisy chaining of groups!
- You are not allowed to make any attempt to access other students' VMs or the scoring engine, doing so will be considered cheating and also result in failing the assignment.
- Do not do anything to the blackteam account. This includes but is not limited to 
    - changing the password
    - removing the SSH key
    - removing its admin privileges
    - Modifying the account will likely lock you out and the scoring engine, resulting in no points.
- Do not disable any scripts or services labeled with blackteam or that are being run by the blackteam account.
- You are not permitted to perform any major version upgrades on the virtual machines.
- Do not change the IP address of your VM.
- If your VM becomes unusable or corrupted beyond recovery, a TA can reset it to its original state. However, this will reset your points to 0, and no additional time will be granted for the assignment. Resets are only available during TA hours (9:00 a.m. to 5:00 p.m.).  
- The first reset is penalty-free, but each subsequent reset will incur a 10-point penalty. This includes any situation where a TA must intervene to restore access. Avoid contacting TAs outside their designated hours.
- Your VM must be powered on and scorable after the lab to obtain points.  We will not be performing resets for you the night it is due.

## Users

Controlling who can access a system and what they can do with that access is crucial to security. We don't want any former employees logging in and we also don't want users with admin access when they don't need it. You will need to add any users that should be there and then modify and delete any if needed. When adding users, make their username `firstnamelastname`. For example, if you were creating an account for `John Smith` the username would be `johnsmith`. Capital letters are not permitted in usernames. We also want our user's passwords to be secure. 

Authorized Users

1. Ethan Brooks
1. Olivia Carter
1. Mason Davis
1. Ava Johnson
1. Lucas Miller
1. Sophia Martinez
1. James Wilson
1. Isabella Taylor
1. William Anderson
1. Mia Thomas
1. blueteam
1. blackteam

## Services

If these services are working, you will receive points for it, but if it goes down, you will lose those points until it works again.

### FTP
All FTP scoring users must be able to log in, read, and write files. The files must keep the same file hash to be considered correct. The hash for the users is `$6$mWgVY9GDGccWAPPX$v7kDifzlJyTiqrHycaZyLw3u7NAmR.UZMG/x5ZuoiOC60sE6AyWuI3gEzA8zAjvqCOcLADGqXSFjyTyRGLlls0`.

- FTP - Users must be able to log in using their password.
- FTP Write - Users must be able to write/upload files to the FTP server in the `/FTP` directory.
- FTP Read - The user must be able to read/download files from the server with the correct content.

## SSH
- Only authorized users should be able to ssh in.
- Only ssh keys can be used to log in - no passwords
- Set other security settings that are reasonable.

## UFW
- Firewall rules should reflect the other critical services that are allowed.

## Guidelines
- Authorized user passwords were correct at the time the lab started, but this is not guaranteed to remain the case.
- You can check your current score in the `Details` tab.
- Read all the requirements for the VM carefully, it will direct you on what to do. It does not specifically tell you everything you need to do to receive points, but it is a good start. Threat hunting will be required.
- The overall goal of the lab is to find and fix as many security, configuration, or policy issues as possible. However, you may make a change that could fix an issue that is not scored or do it in a way that is not recognized by the scoring engine. If you did not receive points for something you believe you should wait at least 5 minutes and then contact a TA.

## Grading Table

| **Criteria** | **Pass** | **Merit** | **Distinction** |
|------|--------------------------------------|--------------------------------------|--------------------------------------|
| **System Commands** | **P1:** Restore basic user-level system commands to correct functionality. | **M1:** Restore system-level binaries to correct functionality.    | **D1:** Fully restore all command functions. |
| **Scheduled Tasks** | **P2:** Review and remove obvious malicious scheduled tasks. | **M2:** Identify and remove condition-based automated tasks. | **D2:** Review and remove deeply embedded malicious system tasks. |
| **Update and Package Management** | **P3:** Update and upgrade packages. |  **M3:** Remove restrictions on firewall installation. | |
| **Firewall and Network Security** | | **M4:** Install a firewall and configure it to block malicious traffic.   |  |
| **User and Group Management** | **P4:** Remove obvious malicious users and secure legitimate users.  | **M5:** Identify and remove hidden malicious users.  | **D3:** Implement secure user password and hashing policies. |
| **SSH Security** | **P5:** Configure secure SSH settings, allowing legitimate users to use their SSH keys.  | **M6:** Remove malicious SSH settings and configurations.| **D4:** Terminate and block malicious SSH sessions. |
| **Malicious Programs and Software** | **P6:** Remove any bind or reverse shells. | **M7:** Identify and remove password loggers.  | **D5:** Find the rest of the malicious threats. |
| **Folder and File Permissions** | **P7:** Ensure critical files have correct permissions.  |  |  |
| **FTP Security** | **P8:** Configure secure FTP settings and allow users to access the FTP server | **M8:** Restrict access to users or groups. | |
| **Verbal Pass Off** | **P9:** Successfully answer two pass-off questions chosen by the TA. |  |  |


## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. What steps did you take to restore basic user-level system commands?
1. How did you identify and restore system-level binaries to their correct functionality?
1. What process did you follow to ensure all command functions were fully restored?
1. What criteria did you use to identify and remove obvious malicious scheduled tasks?
1. How did you detect and remove condition-based automated tasks from the system?
1. What approach did you use to identify and remove deeply embedded malicious system tasks?
1. What steps did you take to update and upgrade the system packages?
1. How did you address restrictions preventing firewall installation?
1. What firewall configurations did you implement to block malicious traffic?
1. How did you identify and remove malicious users from the system?
1. What methods did you use to ensure legitimate users were properly secured?
1. How did you identify hidden malicious users on the system, and how were they removed?
1. What password and hashing policies did you implement to secure user accounts?
1. How did you configure secure SSH settings to allow legitimate users to use their SSH keys?
1. What malicious SSH settings did you remove from the system, and how?
1. How did you terminate and block malicious SSH sessions on the server?
1. What steps did you take to identify and remove bind or reverse shells from the system?
1. How did you identify and remove password loggers from the server?
1. What malicious threats did you find and remove from the system?
1. How did you ensure that critical files had the correct folder and file permissions?

### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.
