# Timeline Analysis

## Purpose
This document analyses the **temporal progression** of attacks observed in the honeypot environment. The objective is to understand how attacker activity unfolds over time and identify key escalation points.

---

## Timeline Construction
Timelines were derived by correlating:
- Network connection timestamps
- Authentication events
- Command execution logs
- Outbound traffic attempts

Events were grouped into logical attack phases.

---

## Phase 1 — Initial Exposure & Scanning
**Timeframe:** Seconds to minutes

### Observed Activity
- Rapid port scanning
- Broad service probing
- High-volume connection attempts

### Interpretation
- Automated discovery of exposed services
- No targeting or adaptation at this stage

---

## Phase 2 — Authentication Pressure
**Timeframe:** Minutes

### Observed Activity
- Burst authentication failures
- Username rotation
- Short pauses between attempts

### Interpretation
- Credential abuse attempts
- Automation-driven brute force

---

## Phase 3 — Post-Access Discovery (When Applicable)
**Timeframe:** Minutes after access

### Observed Activity
- System information queries
- User and network enumeration
- Longer interactive sessions

### Interpretation
- Validation of access
- Assessment of environment value

---

## Phase 4 — Payload Staging Attempts
**Timeframe:** Shortly after discovery

### Observed Activity
- Outbound connection attempts
- Download commands
- External resource references

### Interpretation
- Preparation for persistence or further exploitation

---

## Timeline Patterns Observed
- Many attacks terminate early (automation noise)
- Fewer attacks progress beyond authentication attempts
- The highest-risk events occur when discovery and outbound activity are chained

---

## Defensive Value
- Early detection at Phase 1 and 2 can prevent escalation
- Time-based correlation improves alert accuracy
- Shortening detection-to-response time reduces risk impact

---

## Next Step
Translate findings into organisational risk:

- `analysis/risk-assessment.md`
