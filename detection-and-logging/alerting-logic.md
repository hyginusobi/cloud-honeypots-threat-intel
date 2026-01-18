# Alerting Logic

## Purpose
This document describes the **alerting logic** used to detect suspicious and malicious activity within the honeypot environment.

Alerting is designed to:
- Identify meaningful attacker behaviour
- Reduce false positives
- Support SOC-style triage and escalation
- Enable timely investigation and response

Alerts are treated as **decision-support tools**, not automated enforcement mechanisms.

---

## Alerting Principles
The alerting strategy follows these principles:

- Prioritise high-confidence indicators
- Combine multiple signals where possible
- Avoid alert fatigue
- Ensure alerts are explainable and actionable
- Align alerts with known attack techniques

The focus is on **quality over quantity**.

---

## Alert Categories
Alerts are grouped into logical categories to support prioritisation.

### 1. Reconnaissance Alerts
Triggered by behaviour such as:
- Repeated connection attempts across multiple ports
- Rapid scanning activity from a single source
- Enumeration of services or directories

**Purpose:** identify early-stage attacker activity.

---

### 2. Authentication Attack Alerts
Triggered by:
- High volumes of failed authentication attempts
- Credential stuffing or brute-force patterns
- Login attempts across multiple accounts

**Purpose:** detect attempts to gain initial access.

---

### 3. Command Execution & Interaction Alerts
Triggered by:
- Execution of suspicious commands
- Attempts to download additional tools
- Use of known malicious command patterns

**Purpose:** detect post-authentication attacker behaviour.

---

### 4. Persistence & Lateral Movement Indicators
Triggered by:
- Attempts to modify system configurations
- Creation of unauthorised users or services
- Attempts to establish persistence mechanisms

**Purpose:** identify progression beyond initial access.

---

## Threshold & Correlation Logic
Alerts are not triggered by single events alone.

Examples of correlation logic:
- Multiple failed logins followed by a successful login
- Repeated scanning followed by service interaction
- Command execution following authentication success

Thresholds are tuned to:
- Reduce noise
- Improve confidence
- Reflect realistic attacker behaviour

---

## Severity Levels
Alerts are assigned severity levels to guide response:

- **Low:** background scanning or low-risk probing
- **Medium:** suspicious behaviour requiring review
- **High:** confirmed malicious interaction
- **Critical:** activity indicating potential compromise or misuse

Severity helps prioritise analyst effort.

---

## Alert Context & Enrichment
Each alert includes contextual information to support investigation:

- Source IP address (sanitised)
- Target service and port
- Timestamp and duration
- Associated log events
- Relevant MITRE ATT&CK techniques (where applicable)

Context reduces investigation time and improves accuracy.

---

## False Positive Management
To manage false positives:
- Alerts are reviewed and tuned iteratively
- Benign patterns are documented and excluded
- Thresholds are adjusted based on observed activity
- Detection logic evolves as attacker behaviour changes

False positives are treated as **learning opportunities**, not failures.

---

## SOC Workflow Integration
Alerts support a SOC-style workflow:

1. Alert generation
2. Analyst triage and validation
3. Correlation with other events
4. Documentation of findings
5. Escalation where appropriate
6. Feedback into detection tuning

This mirrors real-world SOC operations.

---

## Limitations
Alerting limitations include:
- Dependence on log quality and completeness
- Reduced effectiveness against highly stealthy attackers
- Manual tuning requirements

These limitations are acknowledged and documented.

---

## Next Step
Use alert outputs to support structured threat intelligence analysis:

- `threat-intelligence/attacker-behaviour-analysis.md`

