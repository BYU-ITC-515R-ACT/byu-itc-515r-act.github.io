# IT&C 515R - Applications of Cybersecurity Final Exam

## Introduction

This final will test the skills you have developed over the semester by setting up and securing your network. There will be a red team for this exam that will be attacking your systems the entire time.

## Instructions

To summarize the exam, you will get points when services are working as they should, and you won't get points when they are not working. 

You will be working in teams of up to 5. There will be a scoreboard that will show the status of each service which will update every minute. The scoreboard is located at [`172.18.0.3`](http://172.18.0.3/exam/3) and is only accessible when you are connected to the VPN. The assignment will start at 09:00 on April 12th and end at 16:00 on April 12th. There will be a 1 hour break between noon and 13:00 where scoring will pause, and so will VM access.

You will not receive any help to debug your systems or set up any of your services. If you have a question about scoring, you may message the black team over Slack.

## Rules

### Exam Conduct

1. Throughout the exam, black team members may occasionally need access to a team's system(s) for scoring, troubleshooting, etc. Teams must immediately allow access when requested.
1. Team members are forbidden from entering or attempting to enter another team's exam workspace or room.
1. Teams are forbidden from collaborating with or communicating with other teams in any way. All questions should be directed towards the Black Team.
1. Teams must complete the exam without "outside assistance" from non-team members from the start of the exam to the end of the exam. All private communications (calls, emails, chat, texting, directed emails, forum postings, conversations, requests for assistance, etc.) with non-team members that would help the team gain an unfair advantage are not allowed.
1. Teams are free to secure their systems, but no offensive activity against any system outside the team's assigned network(s), including those of other teams, will be tolerated. Any team performing offensive activity against any system outside the team's assigned network(s) will immediately fail the exam. If there are any questions or concerns during the exam about whether or not specific actions can be considered offensive, contact the Black Team before performing those actions.
1. Teams are allowed to use active response mechanisms such as TCP resets when responding to suspicious/malicious activity. Any active mechanisms that interfere with the functionality of the scoring engine or manual scoring checks are exclusively the responsibility of the teams. Any firewall rule, IDS, IPS, or defensive action that interferes with the functionality of the scoring engine or manual scoring checks is exclusively the responsibility of the Blue Team.

### Internet Usage

1. Public internet resources such as FAQs, how-to's, existing forums and responses, and company websites are completely valid to be used for the exam provided there is no fee required to access those resources and access to those resources has not been granted based on a previous membership, purchase, or fee.
1. Only resources that could reasonably be available to all teams are permitted. For example, creating a personal public GitHub repository would be prohibited, as no other team would reasonably be able to access the repository.
1. All Internet resources used during the exam must be freely available to all other teams.
1. If there are any questions or concerns during the exam about whether or not specific materials are unauthorized, contact the Black Team immediately.
1. All network activity that takes place on the exam network may be logged and subject to release. We are not responsible for the security of any information, including login credentials, that students place on the exam network.

### Questions, Disputes, and Disclosures

1. Protests by any team must be presented in writing by the Team Captain as soon as possible. The Black Team will be the final arbitrators for any protests or questions arising before, during, or after the exam. Rulings by the Black Team are final.

### Scoring

1. Scoring will be based on keeping required services available and functional and controlling/preventing unauthorized access. Teams accumulate points by successfully maintaining services. 
1. Any team action that interrupts the scoring system is exclusively the responsibility of that team and will result in a lower score. Any team member that modifies a system or system component, with or without intent, to mislead the scoring engine into assessing a system or service as operational, when in fact it is not, may be disqualified and/or the team assessed penalties. Should any question arise about scoring, the scoring engine, or how scoring functions, the Team Captain should immediately contact the Black Team to address the issue.
1. Scoring will occur every 60 seconds, and machine statuses will update every 10 to 30 seconds

### Scoreboard Key
- **Green arrows** indicate that everything is working as intended.
- **Orange Exclamation** indicates that something is partially working. 
- **Red down arrows** indicate that something is not working.

## Service Requirements

NOTE: Any instance of `<T>` represents your team number. For example, if you're on Team 1, `172.18.100.<T>` translates to `172.18.100.1`

## Network Diagram

![](./Network-Diagram-Blueteam.png)

### Router 

The router should return an ICMP request on the external WAN IP of `172.18.10<T>.1`

### WWW

Note that all Web checks are scored through the router.

WWW will be regarded as functioning if a request can be made to your router and return the webpage with a `200` status code from your web server. The website files are located in  `/var/lib/the-music-store`.

### WWW Content

Note that all Web checks are scored through the router.

- Web Scoring User: `admin`
- Web Scoring Password: `admin`

Service Requirements:

- Web Server stays up
- PostgreSQL connection stays available to the web server
- Web content is correct (no errors) and fully functional
- Scoring User can log in and use the site as expected

### SSH

To score points for SSH, all of the users in the table below must be able to access the server using their SSH key The following machines have a scorable service for `SSH`:
- FTP/SSH
- Web
- Database
- DNS

#### Users

- camille_jenatzy
- gaston_chasseloup
- leon_serpollet
- william_vanderbilt
- henri_fournier
- maurice_augieres
- arthur_duray
- henry_ford
- louis_rigolly
- pierre_caters
- paul_baras
- victor_hemery
- fred_marriott
- lydston_hornsted
- kenelm_guinness
- rene_thomas
- ernest_eldridge
- malcolm_campbell
- ray_keech
- john_cobb
- dorothy_levitt
- paula_murphy
- betty_skelton
- rachel_kushner
- kitty_oneil
- jessi_combs
- andy_green

#### Scoring Key
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDeG5nScm9x0W1HOHEakXDMjFTqcoaTKmSjF83CACnJgjQxIypJXZ+Ao+MUsyZjBhGsLnsDCwVOBiKhUpExZUhB425QJ+PwVz3qrb8h0tOMPV1m4+CKc/BLgnwx3GtLuJ7Y1Ks7yNBBzL4syhFRAFEzKbn4cHMINV3Z64HXmMi/PFIq97smsIFdgfyza3qyO7w1Age0RjhqyB8w/JWFS7BriU2IbaerRdbRzjCvChqs5BRAxiSyesMRnDwUoqeQA/tVcikZHvR/+VePgs7Jlk4gKuIUAmUeUjw9VzrtVJf9NOkHc6ar5Qif1ewyKp8nmeO3bkHgPme9Q7x9AhWbnMHRnjow8cUL+E+/3gJDHrAZE0bhFwgb8m3N5PBU5h1gNwaxE2x7w2+wqlrTii6/gefEyhsqNw5udHb4ineG0LjCCedKYQzwoF1GahLCz1S8xPY8aZPxy+Wf6RWczjlqZOfFVpSKm5wU2BmfZBmI8jfzGBYOrgaqExVMqLz2v6JEZK0= SCORING KEY DO NOT REMOVE
```

### DNS

DNS should be available internally at `192.168.10<T>.2`
DNS should be available externally at `172.18.10<T>.1`
DNS Forward lookups for the following domain names point to the corresponding IP.
DNS Reverse lookups for the following IP Addresses point to the corresponding domain name

#### Required Domains

|DNS Address |  IP |    Description |
| -- | ------- | ------ |
| ns1.team\<T>.cyberjousting.org | 172.18.10\<T>.1 | Public DNS Nameserver |
| www.team\<T>.cyberjousting.org | 172.18.10\<T>.1 | Public Web Nameserver |
| shell.team\<T>.cyberjousting.org | 172.18.10\<T>.2 | Public SSH server |
| files.team\<T>.cyberjousting.org | 172.18.10\<T>.2 | Public File Share |
| ns1.team\<T>.net | 192.168.10\<T>.2 | Internal Alias for DNS Server |
| www.team\<T>.net | 192.168.10\<T>.3 | Internal Alias for Web server |
| db.team\<T>.net  | 192.168.10\<T>.4 | Internal Alias for MySQL server |

The above addresses containing `.cyberjousting.org` should be publicly available and will be scored through the router and checked for both forward and reverse lookups.

The above addresses containing `.team\<T>.net` will be scored from inside the internal network and checked for both forward and reverse lookups.

### FTP

All FTP scoring users must be able to log in, read, and write files. The files must keep the same file hash to be considered correct. 

FTP Login - Users must be able to log in using their password.
FTP Write - Users must be able to write/upload files to the FTP server.
FTP Read - The user must be able to read/download files from the server with the correct content.

#### Users 

- camille_jenatzy
- gaston_chasseloup
- leon_serpollet
- william_vanderbilt
- henri_fournier
- maurice_augieres
- arthur_duray
- henry_ford
- louis_rigolly
- pierre_caters
- paul_baras
- victor_hemery
- fred_marriott
- lydston_hornsted
- kenelm_guinness
- rene_thomas
- ernest_eldridge
- malcolm_campbell
- ray_keech
- john_cobb
- dorothy_levitt
- paula_murphy
- betty_skelton
- rachel_kushner
- kitty_oneil
- jessi_combs
- andy_green

#### FTP Files

- file_1.txt
- file_2.txt
- file_3.txt
- file_4.txt
- file_5.txt
- file_6.txt
- file_7.txt
- file_8.txt
- file_9.txt
- file_10.txt

The files are already located in `/mnt/files`

#### User Password Hash
This hash can be used to restore an account if the password ever changes. All the accounts will have different hashes but the password is all the same.

```
$6$HYKV0jeX4ipDSm7N$RlUWfiyfjz1rnvo82pqztm6GJn1ndFKY5gyTClmfuzfvI26.JcuoJ4TGwnaddP3Gstz4V7yLG4hW3YItAuKwb.
```

### SQL Login

- The database is initialized from the web application.
- The data is synced to the QA department via an automated task that reads PostgreSQL directly.
- The QA Department occasionally writes data back to the database as well.

#### Service Requirements

- The PostgreSQL Scoring user can log into PostgreSQL
- The PostgreSQL Scoring user can Read data
- The PostgreSQL Scoring user can Write data

 
#### Scoring Details

The PostgreSQL services are scored from the internal team network, using the internal IP address of `192.168.10<T>.4`.

- PostgreSQL scoring user: `bill_kaplan`
- PostgreSQL scoring password: `b1ackjack!`
- PostgreSQL Scoring user can log in, read, and write to the database `db`
- PostgreSQL Scoring user can log, read, and write to the table users