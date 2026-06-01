# Optional: SMB (Samba File Sharing)

## Introduction

In this lab, you will configure and secure a Samba server on Linux to provide SMB (Server Message Block) file sharing. SMB is the protocol used by Windows file shares and is widely used in enterprise environments. You will set up shared directories, manage Samba users and permissions, connect from a client machine, and harden the service against common attack vectors. This lab is directly relevant to Team Lab 1, where your team will migrate from FTP to SMB.

Resources to assist with the lab:
1. Homework Questions
1. Class Resources
1. Classmates/Teammates
1. Internet Resources
1. Teaching Assistants

Please reach out to the TAs only after making a genuine effort to resolve the issue independently. While they are available to provide guidance and support, their role is to assist you in developing your understanding rather than providing immediate solutions. You are encouraged to approach challenges proactively, fostering problem-solving skills and critical thinking in the process.

Developing problem-solving skills and critical thinking is fundamental to your education and growth. These skills are emphasized as part of the **Aims of a BYU Education**, which seek to cultivate individuals of faith, intellect, and character. Problem-solving and critical thinking are essential components of sound reasoning, effective communication, and intellectual depth — qualities that prepare you to succeed in both academic and real-world challenges.

BYU's focus on lifelong learning and service reminds us that the ability to independently approach, analyze, and resolve complex issues is just as important as mastering technical skills. These capabilities not only build competence but also instill the confidence to contribute meaningfully to the world and continue learning throughout life.

## Configuration Instructions

### Virtual Machines and Operating Systems
You will be working with:
  - 1 Rocky Linux 8 Machine (server)
  - 1 Ubuntu 20.04 Machine (client)

### Network Configuration
Since your machines do not currently have internet access, you will need to configure the network as follows:

1. **`Lab-smb-server` Machine** (Rocky Linux 8):
    - IP: `172.18.<ID>.17/16`
    - Gateway: `172.18.0.1`
    - Primary DNS: `172.18.0.1`
    - Secondary DNS: `8.8.8.8`

1. **`Lab-smb-client` Machine** (Ubuntu 20.04):
    - IP: `172.18.<ID>.18/16`
    - Gateway: `172.18.0.1`
    - Primary DNS: `172.18.0.1`
    - Secondary DNS: `8.8.8.8`

### **Accessing the Virtual Machines**
- The VMs can be accessed through your **Proxmox** instance.
- To track your progress, visit the <a href="http://172.18.0.3/lab/smb" target="_blank">scoreboard</a>.
- You need to be connected to the VPN to access the scoreboard and your Proxmox instance.

### Scoreboard Key
- **Green arrows** indicate that everything is working as intended.
- **Orange Exclamation** indicates that something is partially working.
- **Red down arrows** indicate that something is not working.

You can hover over your specific arrow and a tooltip will appear with a hint on what is wrong or not working.

#### **Credentials**
- All VMs have the same login credentials:
  - **Username**: `blueteam`
  - **Password**: `abc123`

#### **File Creation and Content**
- If a referenced file does not exist, you must create it.
- Unless otherwise stated, answer files should be placed on the `Lab-smb-server` machine.

### Scoring Advice
There may be a way to achieve a criteria that we have not accounted for. If you believe your method meets the criteria but is not being scored please reach out to a TA.

---

## Pass Criteria

### P1: Samba Installation and Basic Configuration

1. Install `samba` on the `Lab-smb-server` machine.
1. Enable and start the `smb` and `nmb` services.
1. Verify both services are running. Enter the line `smb-status:<command>` into `/home/blueteam/P1/P1.txt`.
1. Set the workgroup to `BLUETEAM` in the Samba configuration file.

### P2: Create a Public Share

Create a shared directory that any authenticated user can read from.

1. Create the directory `/srv/smb/public` on the server.
1. Set the owner to `root` and the group to `sambashare`. Set permissions to `775`.
1. Add a share called `[public]` to `/etc/samba/smb.conf` with the following settings:
    - Path: `/srv/smb/public`
    - Browseable: yes
    - Read only: yes
    - Valid users: members of the `sambashare` group

### P3: Samba User Management

1. Create the following Linux user accounts (no login shell required, no home directory):
    - `smbuser1`
    - `smbuser2`
    - `smbadmin`
1. Add all three users to the `sambashare` group.
1. Set Samba passwords for each user:
    - `smbuser1`: `user1-pass`
    - `smbuser2`: `user2-pass`
    - `smbadmin`: `admin-pass`

### P4: Connect from the Client

From the `Lab-smb-client` machine:

1. Install `smbclient` on the client.
1. List the available shares on the server using `smbclient`. Enter the line `list-shares:<command>` into `/home/blueteam/P4/P4.txt` on the **server**.
1. Connect to the `public` share as `smbuser1` and download the file `welcome.txt` from the share to `/home/blueteam/` on the client.

### P5: Troubleshooting

To complete `P5`, `P1–P4` must have a green arrow before starting.

1. Fix the errors in the Samba configuration that are preventing the service from functioning correctly.
1. Restart the service and confirm it is running.

---

## Merit Criteria

### M1: Create a Private Write Share

Create a share that allows authenticated users to read and write, but is not visible when browsing.

1. Create the directory `/srv/smb/private` on the server.
1. Set the owner and group to `smbadmin`. Set permissions to `770`.
1. Add a share called `[private]` to `smb.conf` with the following settings:
    - Path: `/srv/smb/private`
    - Browseable: no
    - Read only: no
    - Create mask: `0660`
    - Directory mask: `0770`
    - Valid users: `smbadmin`, `smbuser1`

### M2: User-Isolated Home Shares

Configure Samba to automatically share each user's home directory to that user only.

1. Enable the `[homes]` section in `smb.conf`.
1. Set it so that:
    - The share is not browseable
    - The share is read/write
    - Only the owner of the home directory can access it

### M3: Firewall Configuration

1. Using `firewalld` on the `Lab-smb-server` machine, allow only the ports required for Samba to function (TCP `139`, TCP `445`, UDP `137`, UDP `138`).
1. Allow traffic only from the `172.18.0.0/16` network.
1. Deny all other inbound traffic.
1. Make all rules permanent.

### M4: Logging and Monitoring

1. Configure Samba to log to `/var/log/samba/samba.log`.
1. Set the log level to `2`.
1. Set the maximum log file size to `5000` (KB).
1. From the client, attempt to connect with an **incorrect** password for `smbuser2`. Then locate the failed authentication event in the Samba logs on the server. Enter the line `failed-auth-log:<log filepath>` into `/home/blueteam/M4/M4.txt`.

---

## Distinction Criteria

### D1: Restrict Access by Host

1. Restrict the `[private]` share so it can only be accessed from `172.18.<ID>.18` (your client machine).
1. Confirm that attempting to access it from any other IP is denied.
1. Enter the line `host-restrict:<smb.conf directive used>` into `/home/blueteam/D1/D1.txt`.

### D2: Harden the Samba Configuration

Apply the following hardening settings to `smb.conf` under the `[global]` section:

1. Disable `NetBIOS` by setting `disable netbios = yes` and stopping the `nmb` service.
1. Force the minimum SMB protocol version to `SMB2` to prevent use of the legacy SMB1 protocol.
1. Disable printing support (`load printers = no`, `printing = bsd`, `printcap name = /dev/null`).
1. Set `server signing = mandatory` to require packet signing on all connections.
1. Restart the `smb` service and confirm it is still functioning after these changes.

---

## Submission
You don't need to submit anything for this lab. All of the above criteria will be auto-graded unless stated otherwise. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off.

1. What is SMB, and what is it commonly used for in enterprise environments?
1. What is Samba, and how does it allow Linux systems to participate in Windows file sharing?
1. What is the difference between the `smb` and `nmb` services in Samba?
1. How do Samba users differ from Linux system users, and why do you need to set a separate Samba password?
1. What is the purpose of the `valid users` directive in a share definition?
1. How does the `browseable` setting affect whether a share appears in network discovery?
1. What does `create mask` control in a Samba share, and why might you want to restrict it?
1. What ports does Samba use, and which transport protocol does each use?
1. Why is SMB1 considered insecure, and what vulnerability is it associated with?
1. What does `server signing = mandatory` protect against?
1. How would you diagnose a Samba connectivity issue from the client side?
1. Why is restricting Samba access by IP or hostname a useful security measure, and how would you implement it?

### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.
