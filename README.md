# AWS CloudTrail & GuardDuty Incident Response Lab

## Project Overview
This project simulates a real-world cloud security incident involving suspicious IAM activity detected through AWS GuardDuty and investigated using AWS CloudTrail logs. The objective is to demonstrate hands-on experience with cloud threat detection, log analysis, incident investigation, and response documentation from a SOC analyst perspective.

This lab mirrors how security analysts investigate cloud-based identity compromise and unauthorized access attempts in production AWS environments.

---

## Threat Scenario
AWS GuardDuty generated a finding indicating suspicious API activity associated with an IAM user, suggesting potential credential compromise. The activity included unusual authentication patterns and API calls inconsistent with baseline behavior.

---

## Tools & Technologies
- AWS GuardDuty
- AWS CloudTrail
- AWS IAM
- AWS Management Console
- JSON log analysis
- Incident response documentation

---

## Detection
- GuardDuty identified anomalous behavior related to IAM authentication.
- Alerts indicated potential unauthorized access and API misuse.
- Detection hypothesis was formed based on GuardDuty findings and event context.

---

## Investigation Process
1. Reviewed GuardDuty findings and severity.
2. Identified affected IAM user and source IP addresses.
3. Correlated GuardDuty alerts with CloudTrail logs.
4. Analyzed event timestamps, API calls, and authentication attempts.
5. Constructed an investigation timeline to validate malicious activity.

---

## Incident Response Actions
- Documented indicators of compromise (IOCs).
- Assessed impact and scope of IAM exposure.
- Identified remediation steps, including credential rotation and policy review.
- Produced a formal incident report suitable for SOC escalation.

---

## Documentation Included
- Full incident report
- Detection hypothesis and assumptions
- Supporting evidence and logs
- Analyst notes and lessons learned

---

## Key Skills Demonstrated
- Cloud security monitoring
- IAM threat analysis
- Log correlation and investigation
- Incident response reporting
- SOC-style documentation

---

## Outcome & Lessons Learned
This project strengthened understanding of AWS-native security tooling, reinforced structured investigation workflows, and highlighted the importance of identity monitoring in cloud environments.

---

## Disclaimer
This project was conducted in a controlled lab environment for educational purposes only. No real customer data or production systems were involved.
