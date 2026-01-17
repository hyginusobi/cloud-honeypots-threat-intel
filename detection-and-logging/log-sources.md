# Log Sources

## Purpose
This document describes the **log sources** used within the honeypot environment and explains how each source contributes to threat detection and intelligence generation.

Understanding log sources is essential for:
- Accurate detection of malicious activity
- Effective SOC triage and investigation
- Correlation of events across systems
- Reliable incident documentation

---

## Overview of Log Sources
The honeypot environment generates logs from multiple layers, each providing a different perspective on attacker behaviour.

Primary log sources include:
- System-level logs
- Honeypot application logs
- Network-level logs
- Cloud platform logs

Together, these logs provide a **comprehensive view** of malicious activity.

---

## System-Level Logs
System logs capture activity occurring at the operating system level.

### Examples of System Events
- Authentication successes and failures
- Privilege escalation attempts
- Process creation and execution
- Service start and stop events

### Detection Value
System logs help identify:
- Brute-force and credential-stuffing attacks
- Attempts to gain persistence
- Suspicious command execution
- Indicators of post-compromise activity

These logs are critical for validating whether an attacker progressed beyond initial access.

---

## Honeypot Application Logs
Honeypot application logs capture interactions directly related to exposed services.

### Common Data Captured
- Source IP addresses (sanitised where necessary)
- Targeted services and ports
- Commands issued by attackers
- Request payloads and probes
- Session duration and interaction patterns

### Detection Value
These logs provide:
- High-fidelity insight into attacker intent
- Clear evidence of reconnaissance and exploitation attempts
- Data suitable for threat intelligence extraction

Honeypot logs are often the **primary signal** for malicious activity.

---

## Network-Level Logs
Network logs capture traffic patterns entering and leaving the honeypot environment.

### Examples
- Connection attempts to open and closed ports
- Repeated scanning behaviour
- Unusual traffic volumes or patterns
- Protocol anomalies

### Detection Value
Network logs support:
- Identification of automated scanning tools
- Detection of coordinated attack activity
- Correlation with host and application logs

They provide context that complements system and application logs.

---

## Cloud Platform Logs
Cloud-native logs provide visibility into control-plane and infrastructure-level activity.

### Examples
- Resource creation or modification events
- Network security group (NSG) changes
- Access and identity-related actions
- Failed or unauthorised configuration attempts

### Detection Value
Cloud logs help detect:
- Misconfiguration attempts
- Abuse of cloud resources
- Suspicious administrative activity

They are essential for maintaining the integrity of the cloud environment itself.

---

## Log Correlation
Effective detection relies on correlating events across multiple log sources.

Examples:
- Authentication failures followed by command execution
- Network scanning followed by service interaction
- Repeated access attempts from the same source across services

Correlation reduces false positives and improves confidence in detection decisions.

---

## Data Quality Considerations
To maintain detection accuracy:
- Ensure consistent timestamp formats
- Normalise key fields (IP, port, action)
- Validate log completeness
- Monitor for log loss or ingestion delays

Poor log quality can undermine detection and investigation.

---

## SOC Alignment
The use of multiple log sources aligns with standard SOC practices, enabling:
- Tier-1 alert triage
- Evidence-based escalation
- Structured incident documentation
- Threat intelligence enrichment

This mirrors real-world SOC environments where analysts rely on layered visibility.

---

## Next Step
Proceed to understanding how logs are analysed and visualised:

- `detection-and-logging/elk-stack-overview.md`

