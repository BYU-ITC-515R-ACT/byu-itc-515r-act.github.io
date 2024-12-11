# Lab 5: Routers & Firewalls

## Introduction

In this lab, you’ll learn to set up, configure, and secure routers and firewalls, essential components for managing and protecting network traffic. You’ll explore firewall configuration, including creating and applying rules to control access, assigning network interfaces to zones, and optimizing traffic policies for three different firewalls, UFW, iptables, and Firewalld. Additionally, you’ll configure routers to enable communication between multiple networks, set up NAT for internet access, and implement security measures to block malicious traffic and prevent network attacks.

### Configuration Instructions

#### Virtual Machines and Operating Systems
You will be working with:  
- 1 CentOS 7 Machine
- 2 Ubuntu 20.04 Machines 

#### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network as follows:  

1. **`Lab-5-router` Machine**:  
   - WAN (`ens18` interface):  
     - IP: `172.18.x.5/16`  
     - Gateway: `172.18.0.1`  
   - LAN (`ens19` interface):  
     - IP: `192.168.x.1/16`  
     - No gateway required  

1. **`Lab-5-Internal-1` Machine**:  
   - IP: `192.168.x.2`  
   - Gateway: `192.168.x.1`  
   - DNS: `192.168.x.1`  

1. **`Lab-5-Internal-2` Machine**:  
   - IP: `192.168.x.3`  
   - Gateway: `192.168.x.1`  
   - DNS: `192.168.x.1`  

#### **Accessing the Virtual Machines**  
- The VMs can be accessed through your **Proxmox** instance.  
- To monitor your progress, visit: [http://172.18.0.3/lab/5](http://172.18.0.3/lab/5). 

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
- For any questions requiring files to contain specific content, use the `Lab-5-router` machine.  

## Pass Criteria

### P1: Firewall Installation and Basic Configuration

#### `Lab-5-router` Machine  
1. Install `firewalld`
1. Enable the `firewalld` service
1. Check the status of the `firewalld` service. Enter the line `firewalld:<command>` into the file `/home/blueteam/P1/P1.txt`.

#### `Lab-5-Internal-1` Machine   
1. Install `ufw`
1. Enable the `ufw` service
1. Check the status of the `ufw` service. Enter the line `ufw:<command>` into the file `/home/blueteam/P1/P1.txt`.

#### `Lab-5-Internal-2` Machine  
1. Install `iptables`
1. Enable the `iptables` service
1. Check the status of the `iptables` service. Enter the line `iptables:<command>` into the file `/home/blueteam/P1/P1.txt`.

### P2: Configuring Ports and Services

#### `Lab-5-router` Machine  
1. List all the current firewall rules for `firewalld`. Enter the line `firewalld:<command>` into the file `/home/blueteam/P2/P2.txt`.

#### `Lab-5-Internal-1` Machine   
1. List all the current firewall rules for `ufw`. Enter the line `ufw:<command>` into the file `/home/blueteam/P2/P2.txt`.

#### `Lab-5-Internal-2` Machine  
1. List all the current firewall rules for `iptables`. Enter the line `iptables:<command>` into the file `/home/blueteam/P2/P2.txt`.

### P3: Securing Incoming and Outgoing Traffic
1. Set all default policies to `deny` incoming and `allow` outgoing for all machines
1. Allow `ICMP` in on the `WAN` address of `Lab-5-router`
1. Allow `SSH` in on the `LAN` address of `Lab-5-router`
1. Allow `SSH` in on `Lab-5-Internal-1`
1. Allow `SSH` in on `Lab-5-Internal-2`
1. Allow `FTP` in on `Lab-5-Internal-1`
1. Allow `DNS` in on `Lab-5-Internal-2`

### P4: Logging and Monitoring Firewall Activity 

By default, some firewalls may not log traffic. 

- To enable logging in ufw use `sudo ufw logging on`
- To enable logging in `firewalld` use `sudo firewall-cmd --set-log-denied=all`

1. On the `Lab-5-Internal-1` machine use the logs to see how many devices have attempted to access the machine using `SSH`. If you have attempted it, disregard your IP from the list. Enter the line `ssh:<number of IPs>` into the file `/home/blueteam/P4/P4.txt`.
1. On the `Lab-5-router` machine use the logs to see how many devices have attempted to resolve a `DNS` query through the router.  If you have attempted it, disregard your IP from the list. Enter the line `dns:<number of IPs>` into the file `/home/blueteam/P4/P4.txt`.

### P5: Troubleshooting
To complete `P5` `P1-P4` must have a green arrow before starting.

1. There seems to be an issue with the `Lab-5-Internal-1` firewall. Troubleshoot the errors and restore proper network connections to it.

### P6: Router Installation and Basic Configuration
1. Using the `Lab-5-router` machine set it up as a router. When it is properly configured the internal machines should be able to access the internet. 
1. Use the `CentOS 7 Router Setup Guide` in `Lecture 8 - Routers Resources & Readings` to help you with the setup.

## Merit Criteria

### M1: Firewall Installation and Basic Configuration
Implement your rules on the `Lab-5-Internal-1` machine. Consider the order the rules will need to be in to be effective.
1. Allow all incoming traffic on the `192.168.0.0/16` network that has the destination ports for `SSH`, `FTP`, `HTTP`, and `HTTPS` traffic.
1. Ensure that the correct transport layer protocol is applied to the rules as well. If the service is only used over `TCP` then `UDP` should not be allowed and vice versa.
1. Block traffic from `192.168.X.15` that is website traffic
1. Block traffic from `192.168.100.0/24` that is SSH traffic
1. Allow only `DNS` traffic from `Lab-5-Internal-1` to `Lab-5-Internal-2`

### M2: Securing Incoming and Outgoing Traffic 

1. Configure `iptables` for stateful inspection
1. Prevent a `SYN` flood attack
1. Limit SSH brute force attempts to 5 in 60 seconds
1. Drop invalid packets
1. Limit `DNS` requests to 10 per second

### M3: Routing and NAT Configuration
1. Port forward TCP traffic on ports `80` and `443` from the `Lab-5-router` to `Lab-5-Internal-1`
1. Port forward UDP traffic on ports `53` from the `Lab-5-router` to `Lab-5-Internal-2`

## Distinction Criteria

### D1: Firewall Installation and Basic Configuration 
1. Using the firewall logs on `Lab-5-router` and `Lab-5-Internal-1`. Identify malicious traffic and block the Protocol and/or IP address.

## Submission
You don't need to submit anything for this lab. All of the above criteria will auto-graded. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off. 

1. Describe the purpose of firewall zones in `firewalld`, and how you assigned a network interface to a specific zone.
1. Explain the difference between a `permanent` and `temporary` rule in `firewalld`.
1. How does a firewall determine which rules to apply to incoming traffic?
1. What are the differences between `firewalld`, `ufw` and `iptables`?
1. What role does a firewall play in protecting a network, and how does it help control traffic?
1. How does a firewall decide which incoming and outgoing connections should be allowed or blocked?
1. What are the main differences between stateless and stateful firewalls?
1. How does Network Address Translation (NAT) help in conserving IP addresses and improving security?
1. Why is it important to assign network interfaces to firewall zones, and how do zones affect traffic handling?
1. Why is logging dropped or accepted packets an important part of firewall operations?
1. How do firewalls handle traffic from unknown or unexpected sources, such as new or unrecognized IP addresses?
1. How does the concept of "least privilege" apply when configuring firewall rules for specific services?
1. What is the significance of setting up a default deny policy in a firewall, and how does it enhance security?
1. How does stateful inspection in firewalls differ from simple packet filtering, and why is it considered more secure?
1. What is the difference between a network firewall and a host firewall, and when would each type be used?
1. How does a host firewall protect an individual device, and what are some advantages of using host-based firewalls in addition to network firewalls?
1. Why might you configure a host firewall to block all incoming traffic by default and allow only specific applications or services?
1. What are the potential limitations of using host firewalls alone to secure a network, and how can these limitations be addressed with network firewalls?
1. How can you configure both network and host firewalls to complement each other, creating a layered defense strategy for a more secure network environment?

### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.

