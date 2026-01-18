# Defensive Improvements

## Purpose
This document outlines practical defensive improvements informed directly by the honeypot observations.

These recommendations align with real-world SOC and cloud security operations.

---

## Authentication Hardening
- Enforce MFA on all remote and privileged access
- Apply conditional access and risk-based authentication
- Monitor failed authentication thresholds and alert on anomalies

---

## Network Exposure Reduction
- Minimise publicly exposed services
- Use just-in-time access where possible
- Apply network segmentation and restrictive security group rules

---

## Logging and Visibility Enhancements
- Enable detailed authentication and command logging
- Centralise logs for correlation and analysis
- Ensure adequate log retention for investigation and trend analysis

---

## Detection Engineering Improvements
- Create sequence-based detection rules
- Alert on discovery activity following access
- Differentiate automation noise from interactive sessions

---

## Incident Response Readiness
- Develop playbooks for common attack patterns
- Improve detection-to-response time
- Regularly test incident response processes

---

## Strategic Benefit
Implementing these improvements reduces:
- Time to detect threats
- Likelihood of successful compromise
- Operational impact of security incidents

---
