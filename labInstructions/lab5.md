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
   - WAN (`ether3` interface):  
     - IP: `172.18.x.6/16`  
     - Gateway: `172.18.0.1`
     - DNS: `172.18.0.1`  
   - LAN (`ether4` interface):  
     - IP: `192.168.x.1/16`  

1. **`Lab-5-website` Machine**:  
   - IP: `192.168.x.2/16`  
   - Gateway: `192.168.x.1`  
   - DNS1: `192.168.x.3` 
   - DNS2: `172.18.0.1` 

1. **`Lab-5-dns` Machine**:  
   - IP: `192.168.x.3/16`  
   - Gateway: `192.168.x.1`  
   - DNS1: `172.18.0.1`
   - DNS2: `8.8.8.8`  

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
- For any questions requiring files to contain specific content, use the `Lab-5-website` machine.  

## Pass Criteria

Make sure the `VM Scoring` Arrow is green before continuing past this point.

### P1: Router Installation and Basic Configuration
1. Using the `Lab-5-router` machine set it up as a router. When it is properly configured the internal machines should be able to access the internet. 
1. Use the [MikroTik Router and Mini Hack Completion](https://www.youtube.com/watch?v=gu5A2yCITRs) video to help you with the setup.

### P2: Firewall Installation and Basic Configuration

#### `Lab-5-website` Machine  
1. Enable the `ufw` service
1. Check the status of the `ufw` service. Enter the line `ufw:<command>` into the file `/home/blueteam/P2/P2.txt` on the router.

Note: The dashboard will mark your VMs as not scoring until the `ssh` rules have been added in P3.

### P3: Securing Incoming and Outgoing Traffic

1. Set all default policies to `deny` incoming and `allow` outgoing for all machines and applicable zones
1. Remove any other inbound rules for the `WAN` interface
1. Allow `SSH` traffic over `TCP` `IN` on `Lab-5-website`
1. Allow `HTTP` traffic over `TCP` `IN` on `Lab-5-website`
1. Allow `HTTPS` traffic over `TCP` `IN` on `Lab-5-website`

### P4: Configuring Ports and Services


#### `Lab-5-website` Machine   
1. List all the current firewall rules for `ufw`. Enter the line `ufw:<command>` into the file `/home/blueteam/P4/P4.txt` on the router.

#### `Lab-5-dns` Machine  
1. List all the current firewall rules for `iptables`. Enter the line `iptables:<command>` into the file `/home/blueteam/P4/P4.txt` on the router.

### P5: Logging and Monitoring Firewall Activity 

By default, some firewalls may not log traffic. 

UFW has 5 options for log levels

- No logs
- All blocked packets (default).
- All blocked packets and some allowed connections.
- All blocked and allowed packets, including detailed packet headers.
- All possible logging for detailed debugging.

Firewalld also has 5 options:

- Disable logging for denied packets (default).
- Log all denied packets.
- Log denied unicast packets.
- Log denied broadcast packets.
- Log denied multicast packets.

1. On the `Lab-5-website` machine enable logging for all blocked packets and some allowed connections.
1. Locate the `UFW` traffic logs on the machine. Enter the line `ufw-filepath:<Full Absolute Filepath>` into the file `/home/blueteam/P5/P5.txt` on the router. 


### P6: Troubleshooting
To complete `P5` `P1-P4` must have a green arrow before starting.

1. There seems to be some problems with the firewalls and router. Troubleshoot the errors and restore proper network connections to the network.

## Merit Criteria

### M1: Firewall Installation and Basic Configuration
Implement your rules on the `Lab-5-website` machine. Consider the order the rules will need to be in to be effective. You may have to alter or remove existing rules.

1. Allow all incoming traffic on the `192.168.0.0/16` network that has the destination ports for `SSH`, `HTTP`, and `HTTPS` traffic.
1. Ensure that the correct transport layer protocol is applied to the rules as well. If the service is only used over `TCP` then `UDP` should not be allowed and vice versa.
1. Block traffic from `192.168.0.15` for `HTTP` and `HTTPS` traffic
1. Block traffic from `172.18.0.16` for `HTTP` and `HTTPS` traffic
1. Block traffic from `192.168.99.0/24` for `SSH` traffic
1. Allow all incoming traffic on the `172.18.0.0/16` network that has the destination ports for, `HTTP`, and `HTTPS` traffic.
1. Deny all other incoming traffic

### M2: Securing Incoming and Outgoing Traffic 

1. Using the logs on `Lab-5-router` and `Lab-5-website`. Identify the IP of the scoring engine. Enter the line `scoring:<IP>` into the file `/home/blueteam/M2/M2.txt` on the router.

### M3: Routing and NAT Configuration
Implement your rules on the`Lab-5-router` machine.
1. Port forward TCP traffic on ports `80` and `443` from the `Lab-5-router` to `Lab-5-website`
1. Port forward UDP traffic on ports `53` from the `Lab-5-router` to `Lab-5-dns`

## Distinction Criteria

### D1: Firewall Installation and Basic Configuration

1. Someone has removed the firewall from the `Lab-5-dns` machine. Install `iptables` and configure it.
1. Set all default policies to `deny` incoming and `allow` outgoing for the `Lab-5-dns` machine.
1. Allow `SSH` traffic over `TCP` `IN` from anywhere  on `Lab-5-dns`
1. Allow `DNS` traffic over `UDP` `IN` from anywhere on `Lab-5-dns`
1. Ensure that you can still access the internet

## Submission
You don't need to submit anything for this lab. All of the above criteria will be auto-graded unless stated otherwise. Once you have finished the lab you will have to do a verbal pass off with a TA.

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
