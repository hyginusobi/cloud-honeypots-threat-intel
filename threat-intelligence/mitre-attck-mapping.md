# MITRE ATT&CK Mapping

## Purpose
This document maps observed attacker behaviours from the honeypot environment to the **MITRE ATT&CK® framework**. The objective is to translate raw events into a structured, widely understood taxonomy of adversary tactics and techniques.

This supports:
- SOC triage and escalation
- Detection engineering and rule development
- Threat hunting hypotheses
- Clear reporting to technical and non-technical stakeholders

> Note: This mapping is based on observed behaviours and patterns. It does not attempt to attribute activity to a specific threat actor.

---

## Mapping Approach
The mapping process follows these steps:
1. Identify recurring attacker behaviours (e.g., brute force, enumeration, suspicious commands)
2. Group behaviours into attack phases (tactics)
3. Map behaviours to the closest ATT&CK techniques
4. Document evidence signals (what to look for in logs)
5. Capture defensive recommendations aligned to each technique

---

## High-Level Tactics Observed
The honeypot environment primarily observed behaviour aligned to:
- **Reconnaissance**
- **Initial Access**
- **Credential Access**
- **Discovery**
- **Command and Control (limited / potential)**
- **Execution (where simulated or observed via honeypot interaction)**

---

## Technique Mapping (Examples)

### 1) Reconnaissance / Service Discovery
**Observed behaviour:**
- Broad port scanning
- Probing common services
- High-volume connection attempts across multiple ports

**MITRE ATT&CK technique alignment:**
- **T1046 – Network Service Scanning**
- **T1595 – Active Scanning** (Reconnaissance tactic)

**Evidence signals (logs):**
- Multiple connection attempts from a single source IP across many ports in a short timeframe
- Repeated SYN attempts or connection resets
- Short-lived sessions with no authentication attempt

**Defensive value:**
- Improve perimeter monitoring for scanning waves
- Use rate limiting and geo/risk-based controls
- Feed scanning indicators into threat hunting baselines

---

### 2) Credential Abuse / Brute Force
**Observed behaviour:**
- High-frequency login attempts
- Repeated authentication failures
- Attempts using common usernames and password patterns

**MITRE ATT&CK technique alignment:**
- **T1110 – Brute Force**
  - (Sub-techniques may apply depending on the pattern observed)

**Evidence signals (logs):**
- Many failed authentication attempts for the same account or multiple accounts
- Rapid retries from the same source IP or rotating IPs
- Repeated use of default/admin usernames

**Defensive value:**
- Enforce MFA and strong password policies
- Implement conditional access / risk-based authentication
- Apply lockout policies and monitoring for brute-force thresholds

---

### 3) Discovery Commands (Post-Access Behaviour)
**Observed behaviour:**
- Enumeration of system information
- Commands to identify users, processes, and configuration
- Attempted navigation of file system structures

**MITRE ATT&CK technique alignment:**
- **T1082 – System Information Discovery**
- **T1057 – Process Discovery**
- **T1087 – Account Discovery**
- **T1016 – System Network Configuration Discovery**

**Evidence signals (logs):**
- Command execution traces (where honeypot logs capture command content)
- Sequence of discovery commands shortly after access
- Increased interactive session duration

**Defensive value:**
- Alert on discovery command chains
- Monitor unusual discovery activity for privileged accounts
- Use endpoint logging to detect reconnaissance patterns

---

### 4) Execution (Interaction / Command Activity)
**Observed behaviour:**
- Attempted command execution on interactive services
- Behaviour consistent with initial foothold testing

**MITRE ATT&CK technique alignment:**
- **T1059 – Command and Scripting Interpreter**

**Evidence signals (logs):**
- Shell command patterns in honeypot logs
- Requests indicating execution attempts (for web-based honeypots)
- Suspicious strings consistent with exploitation probes

**Defensive value:**
- Create detection rules for known suspicious command patterns
- Apply allow-listing or constrained execution in real endpoints
- Monitor and restrict administrative tool usage

---

### 5) Attempted Tool Transfer / Payload Staging (Where Observed)
**Observed behaviour:**
- Attempts to download additional tooling
- Commands suggesting retrieval of remote scripts or binaries

**MITRE ATT&CK technique alignment:**
- **T1105 – Ingress Tool Transfer**

**Evidence signals (logs):**
- Network requests to external destinations after interactive access
- Command strings referencing download utilities
- Unusual outbound traffic for the host profile

**Defensive value:**
- Restrict outbound traffic from exposed services
- Monitor egress for suspicious destinations
- Alert on download utility usage

---

## How This Mapping Helps a SOC
Using MITRE ATT&CK mapping provides:
- A structured way to communicate what attackers are doing
- Better prioritisation (tactics and intent)
- Direct inputs for detection engineering and threat hunting
- A common language across security teams and leadership

---

## Reporting Example (SOC-Friendly Summary)
Based on observed activity, the environment shows repeated evidence of:
- **Active Scanning / Network Service Scanning**
- **Credential abuse and brute-force attempts**
- **System discovery following simulated access**
- **Command execution attempts**
- **Potential payload staging behaviours**

These patterns align to common opportunistic attacks seen across internet-facing services.

---

## Limitations
- Honeypots primarily attract opportunistic attacks and automated scanning.
- Mapping is behaviour-based and does not confirm attacker objectives.
- Attribution is out of scope and not attempted.

---

## Next Step
Extract and document indicators and defensive outputs:

- `threat-intelligence/indicators-of-compromise.md`

