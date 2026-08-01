# AWS CloudTrail Incident Timeline & Evidence Analysis

**Ticket ID:** AWS-102  
**Analyst:** Danny Bermudez  
**Date:** 2026-08-01  
**Target Identity:** `dev-analyst`

---

## 1. Chronological Event Sequence Matrix

| Timestamp (UTC) | Event Name         | Source IP       | Access Key ID Used     | Key Action / Impact                                                          | Status      |
| :-------------- | :----------------- | :-------------- | :--------------------- | :--------------------------------------------------------------------------- | :---------- |
| `09:45:10`      | `ConsoleLogin`     | `198.51.100.42` | N/A                    | Password brute-force / credential spraying attempt                           | **FAILED**  |
| `10:14:22`      | `CreateAccessKey`  | `198.51.100.42` | `AKIAIOSFODNN7EXAMPLE` | Generated secondary access key (`AKIAI4444444EXAMPLE`) for persistence       | **SUCCESS** |
| `10:18:05`      | `AttachUserPolicy` | `198.51.100.42` | `AKIAI4444444EXAMPLE`  | Privilege Escalation: Attached `AdministratorAccess` policy to `dev-analyst` | **SUCCESS** |
| `10:22:40`      | `ListBuckets`      | `198.51.100.42` | `AKIAI4444444EXAMPLE`  | Reconnaissance: Enumerated all S3 storage buckets in account                 | **SUCCESS** |

---

## 2. Key Investigation Findings

1. **Initial Vector:** Compromised static Access Key `AKIAIOSFODNN7EXAMPLE` used via AWS CLI.
2. **Persistence Mechanism:** Attacker invoked `iam:CreateAccessKey` to establish a back-door key (`AKIAI4444444EXAMPLE`), ensuring access if the primary key was disabled.
3. **Privilege Escalation:** Attacker elevated rights by attaching `arn:aws:iam::aws:policy/AdministratorAccess` directly to `dev-analyst`.
4. **Active Scope:** Attacker began resource discovery (`ListBuckets`) using the newly created secondary credentials.

---

## 3. Scope & Blast Radius Summary

- **Compromised IAM Identity:** `dev-analyst`
- **Compromised Access Keys:** `AKIAIOSFODNN7EXAMPLE` (Original), `AKIAI4444444EXAMPLE` (Attacker-created)
- **Affected Services:** IAM (Privilege Escalation), S3 (Reconnaissance)
- **Containment Urgency:** **CRITICAL** — Immediate credential revocation and policy detachment required.
