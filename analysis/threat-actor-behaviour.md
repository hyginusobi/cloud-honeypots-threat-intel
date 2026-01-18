# Threat Actor Behaviour Analysis

## Purpose
This document analyses the **behavioural characteristics** of attackers interacting with the cloud-based honeypot environment. Rather than focusing on attribution, the aim is to classify behaviour types, intent, and sophistication levels based on observed activity.

This analysis supports:
- SOC triage prioritisation
- Threat modelling and risk assessment
- Detection tuning and false-positive reduction
- Security awareness and reporting

---

## Behaviour Classification Method
Threat actor behaviours were classified using:
- Session duration
- Interaction depth
- Command diversity
- Adaptability to environment responses
- Sequencing of actions

These characteristics allow grouping into **behavioural categories** rather than named threat actors.

---

## Behaviour Type 1 — Opportunistic Automated Scanners
### Characteristics
- High-volume, short-lived sessions
- Broad port and service scanning
- Minimal interaction after service identification
- No evidence of adaptive behaviour

### Observed Intent
- Identify exposed services
- Feed scanning results into larger automation pipelines
- Low-cost reconnaissance at scale

### Risk Level
**Low to Medium**  
(High noise, low sophistication, but can enable later-stage attacks)

---

## Behaviour Type 2 — Credential Harvesting Actors
### Characteristics
- Repeated authentication attempts
- Use of common/default usernames
- Consistent retry patterns
- Minimal post-authentication activity

### Observed Intent
- Account compromise through brute force
- Credential reuse testing
- Opportunistic access rather than targeted exploitation

### Risk Level
**Medium**  
(Can lead to successful compromise if controls are weak)

---

## Behaviour Type 3 — Interactive Probing Actors
### Characteristics
- Longer session durations
- Execution of discovery commands
- Sequential enumeration of system and network information
- Signs of manual or semi-automated control

### Observed Intent
- Validate access
- Understand system context
- Assess potential for further exploitation

### Risk Level
**Medium to High**  
(Indicates higher intent and adaptability)

---

## Behaviour Type 4 — Payload Staging Attempts
### Characteristics
- Discovery followed by download attempts
- Outbound network activity
- Attempts to retrieve scripts or binaries

### Observed Intent
- Establish persistence
- Deploy additional tooling
- Expand control beyond initial access

### Risk Level
**High**  
(Represents progression beyond reconnaissance)

---

## Behavioural Insights Summary
- The majority of activity is **opportunistic and automated**
- A smaller subset demonstrates **interactive and adaptive behaviour**
- Risk increases significantly when attackers transition from scanning to discovery and tool staging

---

## Defensive Implications
- Prioritise alerts involving **longer sessions and discovery activity**
- Reduce alert fatigue by filtering pure scanning noise
- Focus analyst time on behaviours indicating progression

---

## Next Step
Examine how attacks evolve over time:

- `analysis/timeline-analysis.md`
