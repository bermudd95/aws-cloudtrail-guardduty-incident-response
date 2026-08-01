# AWS GuardDuty Initial Triage Notes

**Ticket ID:** AWS-101  
**Analyst:** Danny Bermudez  
**Date:** 2026-08-01  
**Severity:** Medium-High (7.0)  

---

## 1. Finding Overview
* **Finding Type:** `UnauthorizedAccess:IAMUser/UnusualBehavior`
* **Target Identity:** IAM User `dev-analyst` (Access Key: `AKIAIOSFODNN7EXAMPLE`)
* **Triggering Action:** `iam:CreateAccessKey`
* **Source IP:** `198.51.100.42` (ASN: `Suspicious-Hosting-Provider`)

---

## 2. Detection Hypothesis
An external actor has likely compromised the static IAM credentials (`AKIAIOSFODNN7EXAMPLE`) for user `dev-analyst`. The actor is attempting persistence by creating secondary Access Keys outside standard operational baselines.

---

## 3. Initial Indicators of Compromise (IOCs)
| Indicator Type | Value | Context |
| :--- | :--- | :--- |
| **IAM User** | `dev-analyst` | Target compromised identity |
| **Access Key ID** | `AKIAIOSFODNN7EXAMPLE` | Primary key used in trigger event |
| **Source IP** | `198.51.100.42` | External non-baseline IP address |
| **AWS API Event** | `CreateAccessKey` | Persistence mechanism attempt |

---

## 4. Next Actions (Pivoting to AWS-102)
1. Query CloudTrail logs for `198.51.100.42` across the past 24 hours.
2. Identify all API actions executed by `dev-analyst` before and after `10:14:22 UTC`.
3. Verify if new persistence mechanisms or privilege escalations were successful.