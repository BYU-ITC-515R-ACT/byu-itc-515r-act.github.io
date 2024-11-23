# Lab 2: Basic Networking

## Introduction

In this lab, you will configure network settings on three operating systems: Ubuntu 20.04, CentOS 7, and Kali Linux. This exercise is designed to help you understand and apply fundamental networking concepts such as IP address configuration, subnet masks, gateway settings, and DNS configuration. 

Resources to assist with the lab:  
1. Homework Questions  
1. Class Resources Repository: [https://github.com/BYU-ITC-515R-ACT/Resources](https://github.com/BYU-ITC-515R-ACT/Resources)  
1. Classmates/Teammates  
1. Internet Resources
1. Teaching Assistants  

Please reach out to the TAs only after making a genuine effort to resolve the issue independently. While they are available to provide guidance and support, their role is to assist you in developing your understanding rather than providing immediate solutions. You are encouraged to approach challenges proactively, fostering problem-solving skills and critical thinking in the process.

Developing problem-solving skills and critical thinking is fundamental to your education and growth. These skills are emphasized as part of the **Aims of a BYU Education**, which seek to cultivate individuals of faith, intellect, and character. Problem-solving and critical thinking are essential components of sound reasoning, effective communication, and intellectual depth — qualities that prepare you to succeed in both academic and real-world challenges.  

BYU’s focus on lifelong learning and service reminds us that the ability to independently approach, analyze, and resolve complex issues is just as important as mastering technical skills. These capabilities not only build competence but also instill the confidence to contribute meaningfully to the world and continue learning throughout life.  

## Configuration Instructions

### Virtual Machines and Operating Systems
You will be working with:  
  - 1 Kali Linux Machine
  - 1 Ubuntu 20.04 Machine
  - 1 CentOS 7 Machine

### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network as follows:  

1. **`Lab-2-kali` Machine**:  
    - IP: `172.18.<ID>.11/16`  
    - Gateway: `172.18.0.1`
    - Primary DNS: `172.18.0.1`
    - Secondary DNS: `8.8.8.8` 

1. **`Lab-2-ubuntu-20.04` Machine**:  
    - IP: `172.18.<ID>.12/16`  
    - Gateway: `172.18.0.1`
    - Primary DNS: `172.18.0.1`
    - Secondary DNS: `8.8.8.8`

1. **`Lab-2-centos-7` Machine**:  
    - IP: `172.18.<ID>.13/16`  
    - Gateway: `172.18.0.1`
    - Primary DNS: `172.18.0.1`
    - Secondary DNS: `8.8.8.8` 

### Network Topology 

![](./Topology.png)

### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- To track your progress, visit the [scoreboard](http://172.18.0.3/lab2).

### Scoreboard Key
- **Green arrows** indicate that everything is working as intended.
- **Red down arrows** indicate that something is not working.

#### **Credentials**  
- All VMs have the same login credentials:  
  - **Username**: `blueteam`  
  - **Password**: `abc123`  

## Pass Criteria

### P1: IP Address and Subnet Mask Configuration

1. Assign a static IP address to each system in the range of IP addresses assigned to you.
1. Verify that all systems can ping each other and the gateway.  

### P2: Subnet Mask Configuration

1. Ensure that the subnet mask is correctly applied to each system using a /16 network.

## Merit Criteria

### M1: Gateway Configuration

1. Set the default gateway on each system to 172.18.0.1.
1. Verify that each system can ping a public IP address.

## Distinction Criteria

### D1: DNS Configuration

1. Set a primary and backup DNS server on each system.
1. Verify that the systems can resolve a domain name and successfully ping it.

## Submission
You don't need to submit anything for this lab. All of the above criteria will auto-graded. Once you have finished the lab you will have to do a verbal pass off with a TA.

![](./Topology.png)

## Pass Criteria

### P1: IP Address and Subnet Mask Configuration

1. Assign a static IP address to each system in the range of IP addresses assigned to you.
1. Verify that all systems can ping each other and the gateway.  

### P2: Subnet Mask Configuration

1. Ensure that the subnet mask is correctly applied to each system using a /16 network.

## Merit Criteria

### M1: Gateway Configuration

1. Set the default gateway on each system to 172.18.0.1.
1. Verify that each system can ping a public IP address.

## Distinction Criteria

### D1: DNS Configuration

1. Set a primary and backup DNS server on each system.
1. Verify that the systems can resolve a domain name and successfully ping it.

## Submission

You don't need to submit anything for this lab. All of the above criteria will auto-graded. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass off. 

1. What is the difference between static and dynamic IP addresses, and why might you choose one over the other in a lab environment?
1. What is the purpose of a subnet mask, and how does it affect communication between devices on the same or different networks?
1. Explain what a /16 subnet mask means in terms of available IP addresses and network segmentation.
1. Why is it important for all systems to be able to ping each other, and what does this verify about network configuration?
1. Why might pinging the gateway be a crucial step in testing network connectivity?
1. What is the role of a default gateway, and how does it assist in inter-network communication?
1. Why should each system’s default gateway be set consistently, and what issues could arise if it’s misconfigured?
1. What is the significance of being able to ping a public IP address, and what does this confirm about the network configuration?
1. Why is DNS configuration necessary, and how does it simplify network communication for users and applications?
1. Explain why having both a primary and backup DNS server configured is essential for network resilience.
1. What are some ways you can verify that DNS is correctly configured on a system, and what signs indicate potential DNS issues?
1. Why is it useful to ping a resolved domain name as part of testing your DNS configuration?
1. What are some common troubleshooting steps if a system cannot communicate with another device on the same subnet?
1. What potential errors might occur if subnet masks aren’t configured correctly, and how would this impact network communication?

### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.