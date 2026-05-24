# IBM QRadar Brute Force Investigation

This investigation demonstrates how IBM QRadar SIEM can be used to detect and analyze brute-force authentication attacks targeting privileged user accounts.

The scenario focuses on failed login monitoring, event correlation, IOC analysis, and incident response activities performed by a SOC analyst.

---

# Investigation Overview

A high-severity QRadar offense was generated after multiple failed login attempts were detected from a single external IP address within a short time period.

The investigation involved:
- Authentication log analysis
- Event correlation
- Source IP reputation review
- User activity verification
- Containment and remediation

---

# Tools Used

- IBM QRadar SIEM
- Windows Security Event Logs
- Firewall Logs
- VPN Authentication Logs
- Active Directory Logs

---

# Detection Logic

The QRadar correlation rule triggered when:
- Failed login attempts exceeded threshold
- Multiple authentication failures targeted privileged accounts
- Events originated from same external source IP

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|--------|-----------|----|
| Credential Access | Brute Force | T1110 |
| Initial Access | Valid Accounts | T1078 |

---

# Investigation Workflow

1. Review QRadar offense details
2. Analyze authentication events
3. Verify affected accounts
4. Check source IP reputation
5. Correlate VPN and firewall logs
6. Identify successful login attempts
7. Contain malicious activity
8. Recommend security improvements

---

# Sample AQL Query

```sql
SELECT sourceIP, username, COUNT(*)
FROM events
WHERE eventName='Login Failed'
GROUP BY sourceIP, username
LAST 1 HOURS
```

---

# Skills Demonstrated

- QRadar Offense Investigation
- SIEM Monitoring
- Log Correlation
- Authentication Analysis
- Threat Detection
- Incident Response
- IOC Analysis
- AQL Querying

---

# Recommendations

- Enable MFA
- Configure account lockout policies
- Improve authentication monitoring
- Restrict suspicious IP addresses
- Tune QRadar detection rules

---

# Disclaimer

All logs, usernames, IP addresses, and indicators used in this repository are for educational purposes only.
