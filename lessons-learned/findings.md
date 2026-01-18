# Key Findings

## Overview
This document summarises the most important findings from deploying and analysing cloud-based honeypots for threat intelligence collection.

The findings reflect real-world attacker behaviour observed against internet-facing services and highlight the value of proactive monitoring and analysis.

---

## Finding 1 — Opportunistic Attacks Dominate
The majority of observed activity was opportunistic rather than targeted.

- Automated scanning and probing accounted for most events
- Attackers prioritised exposed services rather than specific targets
- Behaviour was consistent across multiple source regions

**Implication:**  
Organisations should assume constant background attack activity and focus on resilience, not secrecy.

---

## Finding 2 — Credential Abuse Remains a Primary Threat
Brute-force authentication attempts were one of the most consistent attack patterns observed.

- Common usernames were repeatedly targeted
- Automation enabled sustained attack pressure
- Weak authentication would likely lead to compromise

**Implication:**  
Strong authentication controls (MFA, monitoring, lockouts) remain among the highest-impact defensive measures.

---

## Finding 3 — Discovery Activity Signals Escalation Risk
When attackers progressed beyond scanning into discovery activity, the risk level increased significantly.

- Discovery commands often followed initial access
- These actions suggest intent to assess environment value

**Implication:**  
Detection should prioritise sequences of events rather than isolated alerts.

---

## Finding 4 — Behavioural Detection Outperforms Static Indicators
Static indicators such as IP addresses had limited long-term value.

- Many sources were short-lived or shared infrastructure
- Behavioural patterns were more reliable indicators of malicious intent

**Implication:**  
SOC teams should prioritise behavioural analytics and correlation logic.

---

## Finding 5 — Honeypots Provide High-Value Context
Honeypots captured early-stage attacker behaviour that is often invisible in production environments.

- Safe observation without risk to real assets
- Clear insight into attack progression

**Implication:**  
Honeypots are a valuable complement to traditional monitoring tools.

---
