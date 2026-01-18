# Attack Pattern Analysis

## Purpose
This document summarises the most common **attack patterns** observed in the cloud honeypot environment. The aim is to convert raw security events into repeatable patterns that can be used for:

- Detection engineering (rule creation and tuning)
- SOC triage playbooks
- Threat hunting hypotheses
- Preventative hardening and control improvements

This analysis focuses on **behavioural patterns**, not attribution.

---

## Data Inputs
Attack patterns were derived from correlated observations across:

- Honeypot application logs (service interactions)
- System authentication logs (success/failure patterns)
- Network connection metadata (scanning and targeting behaviour)
- Centralised log storage and querying (ELK)

All examples are anonymised and sanitised for public release.

---

## Pattern 1 — Opportunistic Network Scanning → Service Targeting
### Description
A common pattern involved broad scanning activity followed by interaction with a small set of commonly exposed services.

### Typical Sequence
1. Multiple ports probed in quick succession
2. Services that respond are then targeted repeatedly
3. Activity either ends quickly (automated) or continues (interactive probing)

### Indicators in Logs
- Many connection attempts across multiple ports from a single source in a short time window
- Repeated hits on ports such as SSH (22), HTTP (80), HTTPS (443) and other common admin/service ports
- Short session durations with limited command interaction

### Defensive Value
- Enable rate-based detections for scanning bursts
- Correlate scan behaviour with subsequent authentication attempts
- Use scanning waves as early warning signals for increased threat activity

---

## Pattern 2 — Brute Force Authentication Attempts
### Description
Repeated authentication attempts were observed against exposed services, consistent with brute force and credential abuse.

### Typical Sequence
1. Repeated authentication failures
2. Username rotation (admin-like usernames)
3. Retry bursts with short pauses (automation signature)

### Indicators in Logs
- High volume of failed logins within minutes
- Repeated attempts using common usernames
- Consistent source IP or rotating sources showing similar patterns

### Defensive Value
- Define thresholds for failed logins (per account, per IP, per service)
- Require MFA and apply risk-based controls (where applicable in real environments)
- Block or challenge high-confidence brute force sources based on behaviour, not only IP reputation

---

## Pattern 3 — Discovery Commands Following Access (Simulated / Observed Interaction)
### Description
When interactive behaviour was captured, attackers often attempted basic host discovery immediately after gaining access or simulating access.

### Typical Sequence
1. Login or session start
2. System discovery commands
3. Network or account enumeration
4. Attempt to progress further (persistence/tool transfer)

### Indicators in Logs
- Command strings such as system and identity checks
- Multiple discovery-related commands within a short timeframe
- Increased session duration and interactive pacing

### Defensive Value
- Alert on discovery command chains (sequence-based detections)
- Use detection logic that looks for "initial access + discovery" combinations
- Capture and monitor suspicious discovery activity on privileged accounts in real endpoints

---

## Pattern 4 — Payload Retrieval Attempts (Staging)
### Description
Some interactions suggested an attempt to retrieve tooling or scripts from remote sources.

### Typical Sequence
1. Discovery commands
2. Attempted download command or external request
3. Possible follow-up execution attempt (when applicable)

### Indicators in Logs
- Strings indicating download utilities or outbound requests
- Outbound connections to unfamiliar destinations after a session begins
- Sudden changes in traffic pattern after authentication events

### Defensive Value
- Restrict outbound network paths from exposed services where possible
- Detect tool transfer attempts via egress monitoring
- Build alert rules around download utilities and suspicious external destinations

---

## Pattern 5 — Short, Repeating Sessions (Automation Signature)
### Description
A high proportion of activity was consistent with automated scripts and bot behaviour.

### Characteristics
- Very short connection durations
- Highly repetitive sequences
- Minimal variation in commands or probing behaviour
- Burst behaviour (spikes in short time windows)

### Indicators in Logs
- Numerous sessions with identical patterns
- High event volume with low interaction depth
- Consistent pacing and request structure

### Defensive Value
- Use behavioural baselines to identify "automation noise"
- Reduce alert fatigue by separating automated scanning from interactive sessions
- Prioritise alerts that show adaptive behaviour or longer sessions

---

## Summary of Observed Patterns
The most consistent patterns can be summarised as:

- **Scanning → service targeting**
- **Brute force → repeated authentication failure bursts**
- **Discovery → early post-access enumeration**
- **Tool transfer → payload staging attempts**
- **Automation signatures → short, repetitive sessions**

These patterns are consistent with what many SOC teams see on internet-facing services and provide useful inputs for detection and response improvements.

---

## Next Step
Proceed to interpret behaviours at a higher level and classify attacker interaction types:

- `analysis/threat-actor-behaviour.md`

