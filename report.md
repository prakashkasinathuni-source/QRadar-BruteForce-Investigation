# QRadar Brute Force Login Investigation

## Alert Description

IBM QRadar generated an offense indicating multiple failed login attempts targeting a privileged user account from a single external IP address within a short period of time.

The activity exceeded the organization’s brute-force detection threshold and triggered a high-severity offense.

---

## Severity

High

---

## Detection Source

IBM QRadar SIEM

---

## Offense Information

| Field | Value |
|------|------|
| Offense Type | Authentication Failure Spike |
| Source IP | 185.143.223.14 |
| Target User | administrator |
| Event Count | 245 Failed Logins |
| Log Source | Windows Security Event Logs |

---

## Investigation Steps

1. Opened the offense in QRadar console.
2. Reviewed magnitude, relevance, and credibility scores.
3. Analyzed authentication events associated with the source IP.
4. Verified whether login attempts were successful after failures.
5. Correlated firewall and VPN logs for additional suspicious activity.
6. Checked geolocation and threat reputation of the source IP.
7. Investigated whether other accounts were targeted from the same IP.
8. Verified if MFA was enabled for the affected account.

---

## Logs Reviewed

- Windows Security Logs
- VPN Authentication Logs
- Firewall Logs
- Active Directory Logs
- QRadar Event Correlation Data

---

## QRadar AQL Query Used

```sql
SELECT sourceIP, username, COUNT(*)
FROM events
WHERE eventName='Login Failed'
GROUP BY sourceIP, username
LAST 1 HOURS
```

---

## Indicators of Compromise (IOCs)

| Type | Value |
|------|------|
| Source IP | 185.143.223.14 |
| Username Targeted | administrator |
| Attack Type | Brute Force Authentication Attempt |

---

## MITRE ATT&CK Mapping

| Tactic | Technique |
|--------|-----------|
| Credential Access | Brute Force (T1110) |
| Initial Access | Valid Accounts (T1078) |

---

## Root Cause

An external attacker attempted to gain unauthorized access to a privileged account using repeated password guessing attempts against the VPN authentication portal.

---

## Containment Actions

- Blocked malicious IP address at firewall
- Disabled targeted account temporarily
- Forced password reset
- Enabled MFA enforcement
- Increased monitoring for authentication anomalies

---

## Final Conclusion

The brute-force attack was successfully detected and contained before unauthorized access was achieved. No successful login events or lateral movement activity were identified during the investigation.

---

## Recommendations

- Enforce MFA for all privileged accounts
- Configure account lockout policies
- Block repeated failed login attempts automatically
- Enable geo-location based login restrictions
- Tune QRadar correlation rules for authentication anomalies
