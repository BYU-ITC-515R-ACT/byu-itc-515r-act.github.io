
# Lab 4: Domain Name System (DNS) 

## Introduction

In this lab, you’ll learn to set up, configure, and secure DNS. It is a critical service for translating domain names into IP addresses, enabling users to access network resources using human-readable names. You’ll explore DNS configuration, including creating forward and reverse lookup zones, setting up A and PTR records, and implementing DNS security measures to prevent unauthorized modifications.

Resources to assist with the lab:  
1. Homework Questions  
1. Class Resources
1. Classmates/Teammates  
1. Internet Resources
1. Teaching Assistants  

Please reach out to the TAs only after making a genuine effort to resolve the issue independently. While they are available to provide guidance and support, their role is to assist you in developing your understanding rather than providing immediate solutions. You are encouraged to approach challenges proactively, fostering problem-solving skills and critical thinking in the process.

Developing problem-solving skills and critical thinking is fundamental to your education and growth. These skills are emphasized as part of the **Aims of a BYU Education**, which seek to cultivate individuals of faith, intellect, and character. Problem-solving and critical thinking are essential components of sound reasoning, effective communication, and intellectual depth — qualities that prepare you to succeed in both academic and real-world challenges.  

BYU’s focus on lifelong learning and service reminds us that the ability to independently approach, analyze, and resolve complex issues is just as important as mastering technical skills. These capabilities not only build competence but also instill the confidence to contribute meaningfully to the world and continue learning throughout life.  


### Configuration Instructions

#### Virtual Machines and Operating Systems
You will be working with:  
- 2 Ubuntu 20.04 Machines 

#### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network as follows:  

1. **`Lab-4-DNS` Machine**:  
    - WAN (`ens18` interface):  
        - IP: `172.18.x.4/16`  
        - Gateway: `172.18.0.1`
        - DNS: `172.18.0.1`
    - LAN (`ens19` interface):  
        - IP: `192.168.x.10/24`  
        - No gateway required  

1. **`Lab-4-Internal` Machine**:  
    - LAN (`ens18` interface):  
        - IP: `192.168.x.11/24`  
        - No gateway required  
        - DNS: `192.168.x.10`  

The internal machine will not have internet access even after the network has been configured but it should be able to reach the LAN IP of the DNS server.

#### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- To monitor your progress, visit: [http://172.18.0.3/lab4](http://172.18.0.3/lab4). 

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
- For any questions requiring files to contain specific content, use the `Lab-4-DNS` machine.  

## Domains

### Internal Domains

| **Service**        | **Domain Name**                 | **Record Types** | **Resolving IP** |
|--------------------|---------------------------------|------------------|-----------------|
| **DNS**            | `ns.friedchicken.local`         | NS, PTR          | `192.168.1.10`  | 
| **Intranet**       | `intranet.friedchicken.local`   | A, PTR           | `192.168.1.30`  | 
| **HR System**      | `hr.friedchicken.local`         | A, PTR           | `192.168.1.31`  | 
| **Finance**        | `finance.friedchicken.local`    | A, PTR           | `192.168.1.32`  | 
| **Development**    | `dev.friedchicken.local`        | A, PTR           | `192.168.1.33`  |
| **QA/Test**        | `qa.friedchicken.local`         | A, PTR           | `192.168.1.34`  | 
| **Helpdesk**       | `helpdesk.friedchicken.local`   | A, PTR           | `192.168.1.35`  | 
| **Inventory**      | `inventory.friedchicken.local`  | A, PTR           | `192.168.1.36`  | 
| **Wiki**           | `wiki.friedchicken.local`       | A, PTR           | `192.168.1.37`  | 

### External Domains

| **Service**        | **Domain Name**                 | **Record Types** | **Resolving IP** |
|--------------------|---------------------------------|------------------|-----------------|
| **DNS**            | `ns.friedchicken.com`           | NS, PTR          | `172.19.X.4`    | 
| **Website**        | `friedchicken.com`              | A, PTR           | `172.19.X.4`    | 
| **Website**        | `www.friedchicken.com`          | CNAME, PTR       | `172.19.X.4`    | 
| **Mail Server**    | `mail.friedchicken.com`         | MX, PTR          | `172.19.X.5`    | 
| **APIs**           | `api.friedchicken.com`          | A, PTR           | `172.19.X.6`    | 
| **Status Page**    | `status.friedchicken.com`       | A, PTR           | `172.19.X.7`    | 
| **E-commerce**     | `shop.friedchicken.com`         | A, PTR           | `172.19.X.8`    | 
| **Blog**           | `blog.friedchicken.com`         | A, PTR           | `172.19.X.9`    | 

For forward lookups, the A, NS or CNAME records must resolve and for a reverse lookup, the PTR record must resolve. Forward lookups resolve a domain to an IP address. A reverse lookup does the opposite and resolves an IP to a domain name.

## Pass Criteria

### P1: DNS Installation and Configuration

1. Install `DNS` on the server by installing the `bind9` package
1. Configure a forward lookup zone for all the domains with `A` records in the `Internal Domains` table
1. Configure a reverse lookup zone for all the domains with `PTR` records in the `Internal Domains` table

### P2: Troubleshooting
To complete `P2` `P1` must have a green arrow before starting

1. Check the status of the `bind9` service. Enter the line `status:<command>` into the file `/home/blueteam/P6/P6.txt`.
1. Fix the errors in the DNS config files to allow the service to restart.
1. Restart the service.

## Merit Criteria

### M1: DNS Installation and Configuration

1. Configure a forward lookup zone for all the domains in the `External Domains` table.
1. Configure a reverse lookup zone for all the domains with `PTR` records in the `External Domains` table.

### M2: DNS Security

1. Limit queries to any domain or IP in the `Internal Domains` table to `192.168.0.0/16`.
1. Limit queries to any domain or IP in the `External Domains` table to `172.19.0.0/16`.

### M3: Troubleshooting 

To complete `M3` `P1-2` and `M1-2` must have a green arrow before starting.

1. Some of the domains are having issues resolving. Fix the issues.

## Distinction Criteria

### D1: DNS Installation and Configuration*

1. Resolve public domains using your `Lab-4-DNS` machine as the recursive resolver. You should be able to look up public domains from your `Lab-4-Internal` machine.

### D2: DNS Security

1. Disable zone transfers. 
1. Limit recursive queries to the internal network of `192.168.0.0/16`.

## Submission
You don't need to submit anything for this lab. All of the above criteria will auto-graded. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. What command did you use to install the DNS server?
1. Describe the purpose of a forward lookup zone and the types of records you would typically find in one.
1. What is the function of a reverse lookup zone, and which DNS records are involved in reverse lookups?
1. Explain the difference between an A record and a C record.
1. How does the DNS service you configured translate domain names into IP addresses?
1. What file did you use to define the forward lookup zones for the internal domains, and what were the contents of this file?
1. How can you verify that forward lookups are working correctly?
1. What command did you use to check the status of the `bind9` service, and where did you store the output?
1. When you encountered errors in the DNS configuration, what steps did you take to troubleshoot and resolve them?
1. Why is it important to limit query access to the internal and external domains, and how did you configure these restrictions?
1. Why are zone transfers a potential security risk, and how did you disable them?
1. What does a recursive query in DNS mean, and how did you limit recursive queries to internal IP addresses?
1. What are the differences between an NS record and an A record, and how did you configure the NS records for this lab?

### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.