# Indicators of Compromise (IOCs)

## Purpose
This document captures **sanitised Indicators of Compromise (IOCs)** observed during the honeypot deployment. These indicators are derived from logged activity and are presented in a defensive and educational context.

The goal is to support:
- Threat detection and alerting
- SOC triage and investigation
- Threat intelligence enrichment
- Pattern recognition and defensive baselining

> ⚠️ All indicators are anonymised and partially redacted to avoid exposing live or sensitive data.

---

## IOC Collection Methodology
Indicators were collected through:
- Honeypot service logs
- Network flow and connection logs
- Authentication attempt records
- Command interaction logs (where applicable)
- Centralised logging pipeline (ELK stack)

Only indicators that demonstrate **repeatable malicious patterns** were included.

---

## Network-Based Indicators

### Source IP Address Patterns
Observed attacker source IPs showed:
- High-volume connection attempts
- Repeated authentication failures
- Scanning behaviour across multiple ports

**Example (sanitised):**
