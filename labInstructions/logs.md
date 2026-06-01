# Required: Logs

## Introduction

In this lab, you will learn to work with the Linux logging ecosystem — an essential skill for monitoring system health, detecting intrusions, and responding to incidents. You will explore `journald` (systemd's journal), `rsyslog` for traditional syslog-style logging, and `logrotate` for managing log file growth. You will also practice analyzing log output to identify suspicious activity and answer investigative questions.

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
  - 1 Rocky Linux 8 Machine

### Network Configuration
Since your machine does not currently have internet access, you will need to configure the network as follows:

1. **`Lab-logs-rocky` Machine**:
    - IP: `172.18.<ID>.16/16`
    - Gateway: `172.18.0.1`
    - Primary DNS: `172.18.0.1`
    - Secondary DNS: `8.8.8.8`

### **Accessing the Virtual Machines**
- The VMs can be accessed through your **Proxmox** instance.
- To track your progress, visit the <a href="http://172.18.0.3/lab/logs" target="_blank">scoreboard</a>.
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
- All answer files should be placed on the `Lab-logs-rocky` machine unless otherwise specified.

### Scoring Advice
There may be a way to achieve a criteria that we have not accounted for. If you believe your method meets the criteria but is not being scored please reach out to a TA.

---

## Pass Criteria

### P1: Journald — Basic Usage

Using `journalctl`, answer the following questions. Record your answers in `/home/blueteam/P1/P1.txt`.

1. View all journal entries for the current boot. Enter the line `current-boot:<command>` into `P1.txt`.
1. View only `error`-level and above entries. Enter the line `errors:<command>` into `P1.txt`.
1. View the last 25 lines of the journal. Enter the line `tail:<command>` into `P1.txt`.
1. Follow the journal in real-time. Enter the line `follow:<command>` into `P1.txt`.
1. View all journal entries for the `sshd` unit. Enter the line `sshd:<command>` into `P1.txt`.

### P2: Journald — Log Analysis

Use `journalctl` and standard text processing tools to answer the following. Record your answers in `/home/blueteam/P2/P2.txt`.

1. How many times did the `sshd` service start during the current boot? Enter the line `sshd-starts:<count>` into `P2.txt`.
1. What is the PID of the most recent `sshd` process that appears in the journal? Enter the line `sshd-pid:<pid>` into `P2.txt`.
1. How many `error` or higher severity messages appear across all boots? Enter the line `error-count:<count>` into `P2.txt`.

### P3: Rsyslog — Installation and Configuration

1. Ensure `rsyslog` is installed and running.
1. Verify that `/var/log/messages` and `/var/log/secure` exist and are being written to.
1. Configure rsyslog to write all `authpriv` messages to `/var/log/auth-custom.log` in addition to the default destinations.
1. Restart the rsyslog service and confirm it is active.

### P4: Log File Analysis

Use the log files on the system to answer the following. Record your answers in `/home/blueteam/P4/P4.txt`.

1. How many failed SSH login attempts appear in `/var/log/secure`? Enter the line `failed-ssh:<count>` into `P4.txt`.
1. What usernames were targeted in those failed attempts? List each unique username, one per line, after the key `targeted-users:` in `P4.txt`.
1. What IP address appears most frequently in failed login attempts? Enter the line `top-attacker:<ip>` into `P4.txt`.

---

## Merit Criteria

### M1: Journald — Persistence

By default on some systems, the journal is stored only in memory and lost on reboot.

1. Configure `journald` to persist logs across reboots by writing to disk.
1. Set the maximum disk space the journal may use to `500M`.
1. Set the maximum size of individual journal files to `50M`.
1. Restart the `systemd-journald` service and confirm the changes are in effect.

### M2: Rsyslog — Remote Logging

1. Configure rsyslog to **send** all `authpriv` log messages to a remote syslog server at `172.18.0.50` over UDP port `514`.
1. Configure rsyslog to **receive** log messages from any host on the `172.18.0.0/16` network over UDP port `514`.
1. Confirm rsyslog is listening on the correct port. Enter the line `listening:<command and output>` into `/home/blueteam/M2/M2.txt`.

### M3: Logrotate — Configuration

1. Verify that `logrotate` is installed.
1. Create a custom logrotate configuration at `/etc/logrotate.d/auth-custom` for the file `/var/log/auth-custom.log` with the following settings:
    - Rotate weekly
    - Keep 4 weeks of backups
    - Compress rotated logs
    - Skip rotation if the log is empty
    - Create new log files with permissions `640`, owner `root`, group `adm`
1. Perform a dry run of logrotate and confirm your config is valid. Enter the line `dry-run:<command>` into `/home/blueteam/M3/M3.txt`.

### M4: Log Analysis — Threat Hunting

Using any log files available on the system, answer the following. Record your answers in `/home/blueteam/M4/M4.txt`.

1. Is there any evidence of a successful login from an unexpected IP address? Enter the line `unexpected-login:<yes/no>,<ip if yes>` into `M4.txt`.
1. Is there any process running that has opened an unusual listening port? Enter the line `unusual-port:<yes/no>,<port if yes>` into `M4.txt`.
1. What cron job, if any, appears to be running on a suspicious schedule? Enter the line `suspicious-cron:<description or none>` into `M4.txt`.

---

## Distinction Criteria

### D1: Auditd — Installation and Configuration

1. Install `auditd` and ensure it is running and enabled on boot.
1. Add a rule to audit all writes to `/etc/passwd`.
1. Add a rule to audit all writes to `/etc/sudoers` and files under `/etc/sudoers.d/`.
1. Add a rule to audit all executions of `/usr/bin/sudo`.
1. Make the rules persistent across reboots.

### D2: Auditd — Log Analysis

After making the above audit rules active, trigger each rule at least once and then answer the following. Record your answers in `/home/blueteam/D2/D2.txt`.

1. What does the `aureport` command show for recent `sudo` usage? Enter the line `sudo-report:<command>` into `D2.txt`.
1. Using `ausearch`, find the audit event for the last modification of `/etc/passwd`. Enter the `time`, `pid`, and `comm` fields from that event as `passwd-event:<time>,<pid>,<comm>` into `D2.txt`.

---

## Submission
You don't need to submit anything for this lab. All of the above criteria will be auto-graded unless stated otherwise. Once you have finished the lab you will have to do a verbal pass off with a TA.

## Pass Off Questions

You will be asked two of these questions at random during your verbal pass-off.

1. What is the difference between `journald` and `rsyslog`, and why might a system use both?
1. Where does `journald` store its logs by default, and how can you make them persist across reboots?
1. What does the `-p` flag do in `journalctl`, and what priority levels are available?
1. How would you filter journal entries to show only messages from a specific systemd unit?
1. What is `rsyslog`, and how does it decide where to send log messages?
1. Explain the format of a rule in `/etc/rsyslog.conf` — what do the facility, severity, and destination fields mean?
1. What is `logrotate` and why is it important for system administration?
1. What does the `compress` directive do in a logrotate config, and what compression format is used by default?
1. What is `auditd`, and how does it differ from regular syslog-based logging?
1. How would you use `ausearch` to find audit events related to a specific file?
1. What are some common indicators in log files that a system may have been compromised?
1. How can you use `grep`, `awk`, or `sed` to extract useful information from large log files?

### Grading:
- **Pass**: All Pass criteria and verbal pass-off has been completed.
- **Merit:** All **Pass** and **Merit** criteria completed.
- **Distinction:** All **Pass**, **Merit**, and **Distinction** criteria completed.
