# Risk Assessment

## Purpose
This document translates observed attacker behaviours into **practical security risk** for organisations operating cloud-based, internet-facing services.

The assessment considers:
- Likelihood of occurrence
- Potential impact
- Control effectiveness
- Residual risk

---

## Risk 1 — Exposure to Opportunistic Scanning
### Description
Internet-facing services are continuously scanned by automated actors.

**Likelihood:** High  
**Impact:** Low (alone)

### Risk Consideration
Scanning itself is low-risk but enables later attack stages.

### Mitigation
- Reduce exposed attack surface
- Use rate limiting and monitoring
- Maintain accurate asset inventories

---

## Risk 2 — Credential-Based Attacks
### Description
Brute force and credential abuse are persistent threats.

**Likelihood:** Medium to High  
**Impact:** Medium to High

### Risk Consideration
Weak authentication controls significantly increase compromise risk.

### Mitigation
- Enforce MFA
- Apply strong password policies
- Monitor failed login thresholds

---

## Risk 3 — Undetected Post-Access Discovery
### Description
Once access is gained, discovery activity may go unnoticed.

**Likelihood:** Medium  
**Impact:** High

### Risk Consideration
Discovery enables lateral movement and privilege escalation.

### Mitigation
- Endpoint and command logging
- Behaviour-based alerting
- Privileged access monitoring

---

## Risk 4 — Tool Staging and Persistence
### Description
Attackers may attempt to download and deploy tooling.

**Likelihood:** Low to Medium  
**Impact:** High

### Risk Consideration
This represents a transition to active compromise.

### Mitigation
- Restrict outbound connectivity
- Monitor egress traffic
- Alert on download utilities and unusual destinations

---

## Overall Risk Summary
| Risk Area | Likelihood | Impact | Priority |
|---------|-----------|--------|---------|
| Scanning | High | Low | Medium |
| Credential Abuse | High | High | High |
| Discovery | Medium | High | High |
| Tool Staging | Low-Medium | High | High |

---

## Strategic Takeaways
- Behavioural detection provides higher value than static indicators
- Early-stage detection dramatically reduces downstream risk
- Honeypots provide actionable intelligence when integrated into SOC workflows

---

## End of Analysis Section
This analysis completes the **interpretation phase** of the project and feeds directly into defensive strategy and learning outcomes.
