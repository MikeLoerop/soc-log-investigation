# SOC Log Analysis Project - SSH Brute Force Investigation

## Overview
Investigated real-world Open SSH logs to identify suspivious activity, analyze attacker behavior, and document security findings.

## Tools & Environment
- Operating System: Ubuntu Linux
- Log Source: OpenSSH authentication logs from Loghub dataset
- Tools used:
	- grep
	- awk
	- sort
	- uniq
	- wc
	- Bash terminal
	- git & Github

## Dataset
log file analyzed:
	OpenSSH_2k.log
Source:
	LogHub public log dataset containing real SSH authentication events.

## Investigation Steps
1. Identified hundreds of failed login attempts
1. Sorted "Failed password" attempts to identify brute-force behavior
1. Sorted usernames attackers were attempting to access and identified common targets (root, admin, oracle)
1. Detected successful login attempt for username "ftzu" from unique IP address not listed in brute-froce attacks.
1. Identified successful login was from a non-standard port
1. Reviewed session lifecycle event and observed session duration was ~13 minutes, open and closed normally, and no additional command logging available

## Security Findings
1. Brute-force activity: Multiple distributed SSH login attempts
1. Username enumeration: Attackers targeted common admin accounts
1. Successful authentication: Single login from unique IP
1. Suspisious Indicator: Non-standard source port
1. Risk level: Medium (requires verification)


## Analyst Assessment
1. Log data shows automated SSH brute-force activity consistent with internet-wide scanning.
1. A single successful login may represent either:
	- A legitimate user session, or
	- Credential compromise following brute-force attempts.
Additional telemtry (command history, endpoint logs, or user validation) would be required for confirmation.

