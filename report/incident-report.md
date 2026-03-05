# SSH Brute Force Investigation

## Objective
Analyze SSH Authentication logs to determine if malicious activity occured.

## Environment
- OS: Ubuntu Linux
- Dataset: OpenSSH Authentication logs
- Tools: grep, awk, sort, uniq

## Investigation Process
Authentication logs were analyzed to identify failed login attempts, attacker IP addresses, targeted usernames, and sucessful authentication events.

## Findings

### Brute Force Activity
- Multiple IP addresses conducted password guessing attacks.
- One IP performed over 200 login attempts.
- Primary targets were privileged accounts: root, admin

### Successful Authentication Event
- User: ftzu
- Login occured with first successful attempt
- Source IP differed from high-volume attackers.
- Session duration: ~13 minutes.
- Connection originated from non-standard port: 49116

## Assessment
Activity is consistent with automated brute-force attacks combine with a potentially unauthorized successful login attempt.

## Recommendations
- Determine if successful login was legitimate
- Enforce multi-factor authentication
- Ensure root ssh login is disabled
- Monitor non-standard ports
- Implement IP blocking
