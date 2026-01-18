# Attacker Behaviour Analysis

## Purpose
This document analyses attacker behaviour observed within the honeypot environment and translates raw security events into **actionable threat intelligence**.

The objective is to:
- Identify common attacker behaviours
- Understand attack progression
- Distinguish automated activity from manual interaction
- Provide insight that can improve detection and defence strategies

---

## Data Sources
Analysis is based on correlated data from:
- Honeypot application logs
- System authentication logs
- Network-level connection data
- Centralised logs indexed within the ELK Stack

Only sanitised and non-identifiable data is used.

---

## Initial Access Patterns
Observed attacker behaviour commonly begins with **reconnaissance and initial access attempts**, including:

- Broad port scanning activity
- Repeated authentication attempts
- Use of default or commonly guessed credentials
- Enumeration of exposed services

These patterns indicate both opportunistic and automated attack activity.

---

## Brute-Force and Credential Abuse
A significant volume of activity involved:
- High-frequency login attempts
- Repeated credential guessing
- Attempts across multiple accounts or services

This behaviour aligns with common brute-force and credential-stuffing techniques.

Indicators include:
- Rapid authentication failures
- Consistent source addresses over short timeframes
- Repeated username patterns

---

## Post-Authentication Behaviour
Where authentication was simulated as successful, attackers attempted actions such as:

- Executing reconnaissance commands
- Checking system information
- Attempting to download or stage additional tools
- Exploring file system structures

These actions suggest attempts to assess system value and potential for persistence.

---

## Automated vs Manual Interaction
Analysis revealed two primary interaction types:

### Automated Activity
Characteristics:
- High volume
- Predictable command sequences
- Short session durations
- Limited adaptability

Often associated with scanning tools and botnets.

### Manual or Semi-Manual Activity
Characteristics:
- Slower interaction pace
- Adaptive command usage
- Longer session durations
- Context-aware behaviour

These interactions may indicate higher-skilled attackers.

---

## Temporal Patterns
Time-based analysis showed:
- Activity peaks during specific periods
- Repeated scanning waves
- Persistent sources returning over time

Temporal analysis helps identify campaign-style behaviour and recurring threat actors.

---

## Behavioural Trends
Common trends identified include:
- Preference for exposed remote access services
- Focus on weak authentication mechanisms
- Opportunistic exploitation rather than targeted attacks

These trends reflect real-world threat landscapes observed by SOC teams.

---

## Intelligence Value
The observed behaviours provide intelligence that can be used to:
- Improve detection rules
- Tune alert thresholds
- Inform defensive hardening decisions
- Support proactive threat hunting

Honeypots act as early-warning systems for emerging attack techniques.

---

## Limitations
Behavioural analysis limitations include:
- Bias toward automated attacks
- Limited insight into attacker intent
- No attribution to specific threat actors

Despite these limitations, the data provides valuable defensive insight.

---

## Next Step
Map observed behaviours to known adversary techniques:

- `threat-intelligence/mitre-attck-mapping.md`

