# Cloud-Based Honeypots for Threat Intelligence

## Overview
This project demonstrates the design, deployment, and operation of **cloud-based honeypots** to collect and analyse real-world attacker behaviour and generate actionable **threat intelligence**.  

The environment was deployed in **Microsoft Azure** and designed to safely capture malicious activity while maintaining strong isolation, ethical controls, and compliance considerations. The findings are analysed using log aggregation and monitoring techniques aligned with **Security Operations Centre (SOC)** workflows.

This repository has been adapted from an independent MSc research project and restructured for **industry and operational relevance**, with all sensitive or identifiable information removed.

---

## Problem Statement
Modern organisations often lack early visibility into attacker behaviour. Traditional security controls typically detect threats **after** compromise or during later stages of an attack lifecycle.

Honeypots provide a proactive mechanism to:
- Attract malicious activity in a controlled environment
- Observe attacker techniques, tools, and behaviours
- Generate threat intelligence that can improve detection and response capabilities

---

## Project Objectives
- Design and deploy secure cloud-based honeypots
- Safely capture malicious traffic and attacker interactions
- Collect and centralise logs for analysis
- Identify attacker techniques and patterns
- Map observed behaviour to **MITRE ATT&CK**
- Demonstrate a SOC-aligned detection and investigation workflow
- Address ethical, legal, and data protection considerations

---

## Architecture Summary
The solution is deployed in a **segmented Azure environment** with strict isolation controls.

High-level components include:
- Cloud-hosted virtual machines configured as honeypots
- Network isolation using virtual networks and security groups
- Centralised logging and monitoring pipeline
- Analysis layer for identifying malicious activity and trends

Full architectural details are provided in:

---

## Deployment Approach
The deployment follows a **security-by-design** approach:
- Isolated Azure networking to prevent lateral movement
- Hardened configurations to limit unintended exposure
- Controlled ingress rules to attract malicious scanning and access attempts
- Logging enabled across all relevant services

Step-by-step deployment details are documented in:

---

## Detection & Logging
The honeypot environment generates logs from multiple sources, including:
- Network connections
- Authentication attempts
- Service interactions
- System-level events

Logs are aggregated and analysed to:
- Identify suspicious or malicious behaviour
- Distinguish automated scanning from targeted attacks
- Support alerting and investigation workflows

Detection and logging design is detailed in:

---

## Threat Intelligence Analysis
Captured data is analysed to extract:
- Common attacker behaviours and tactics
- Frequently targeted services and ports
- Indicators of compromise (sanitised)
- Patterns aligned to known adversary techniques

Observed behaviours are mapped to the **MITRE ATT&CK framework** to support structured threat intelligence.

Analysis outputs are documented in:

---

## Incident Workflow (SOC Alignment)
This project mirrors a **Level-1 SOC workflow**, including:
1. Detection of suspicious activity
2. Initial triage and validation
3. Escalation criteria for confirmed threats
4. Documentation of findings and outcomes
5. Lessons learned and improvement opportunities

The workflow is documented in:

---

## Outcomes & Key Findings
- Successfully captured real-world malicious activity
- Identified common scanning and attack techniques
- Demonstrated how honeypots can enhance early threat visibility
- Validated the usefulness of honeypots as a threat intelligence source
- Highlighted limitations and areas for improvement

Key findings are summarised in:

---

## What This Project Demonstrates
This repository demonstrates:
- Practical cloud security design
- Threat detection and intelligence generation
- SOC-aligned investigation workflows
- Strong documentation and analytical skills
- Awareness of ethical and legal considerations in security research

---

## Future Enhancements
Potential improvements include:
- Integration with enterprise SIEM platforms
- Automated enrichment of indicators
- Detection engineering use cases
- Correlation with external threat intelligence feeds

---

## Disclaimer
This project is for **educational and professional demonstration purposes only**.  
All sensitive data, identifiers, IP addresses, and credentials have been **sanitised or removed**.  
No real production systems or user data were impacted.

---
