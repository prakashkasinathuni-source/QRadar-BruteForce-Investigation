# QRadar Malware Investigation

This folder contains a SOC investigation of a malware incident detected using IBM QRadar SIEM.

---

## Overview

A malicious executable was detected on a user workstation, which triggered QRadar correlation rules due to suspicious process execution and outbound network communication.

---

## What was analyzed

- Process execution logs (Sysmon)
- Network traffic logs
- Persistence mechanisms
- SIEM correlation events
- Threat intelligence data

---

## Key Findings

- Execution of suspicious file: `invoice_update.exe`
- Connection to external IP: `91.240.118.172`
- Registry-based persistence attempt detected
- Malware behavior confirmed via SIEM correlation

---

## Skills Demonstrated

- SIEM (QRadar) analysis
- Malware investigation
- Log correlation
- IOC extraction
- Incident response workflow
- MITRE ATT&CK mapping

---

## MITRE ATT&CK

- T1204 – User Execution
- T1547.001 – Registry Run Keys
- T1071 – Command and Control

---

## Disclaimer

All artifacts used in this investigation are fictional and used for educational purposes only.
