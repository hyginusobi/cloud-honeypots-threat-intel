# Azure Environment Setup

## Purpose
This document describes how to set up a **secure, isolated Microsoft Azure environment** to host cloud-based honeypots for threat intelligence collection.

The goal is to:
- Deploy honeypots in a **controlled cloud network**
- Allow carefully scoped inbound access to attract attackers
- Ensure strong isolation to prevent lateral movement or third-party impact
- Enable logging and monitoring from day one

> **Important:** Do not publish subscription IDs, tenant IDs, public IP addresses, usernames, passwords, or SSH keys. Use placeholders in any examples.

---

## Prerequisites
Before starting, ensure you have:
- An Azure subscription with permission to create resources
- A dedicated resource group for the honeypot environment
- Basic familiarity with Azure networking (VNet, subnets, NSGs)
- A plan for log collection (documented in `deployment/logging-and-collection.md`)

Optional but recommended:
- Separate Azure subscription for this environment (strong isolation)
- Budget alert configured to prevent unexpected costs

---

## Step 1 — Create a Resource Group
Create a dedicated resource group to contain all honeypot assets.

Recommended naming convention:
- Resource Group: `rg-honeypot-threatintel`
- Region: choose a region appropriate for the project and cost

**Why:** a single resource group simplifies management, cleanup, and access control.

---

## Step 2 — Create a Virtual Network (VNet)
Create a dedicated VNet for honeypot resources.

Example structure:
- VNet: `vnet-honeypot-threatintel`
- Address space: `10.50.0.0/16` (example)

**Why:** a dedicated VNet ensures the honeypots are separated from any other workloads.

---

## Step 3 — Create Subnets
Create at least two subnets to support segmentation:

Recommended:
- `snet-honeypots` (honeypot VMs)
- `snet-management` (optional management/jump access if required)

Example:
- `snet-honeypots`: `10.50.10.0/24`
- `snet-management`: `10.50.20.0/24`

**Why:** segmentation supports containment and reduces blast radius if a system is compromised.

---

## Step 4 — Network Security Groups (NSGs)
Create NSGs and apply them at subnet level.

### 4.1 NSG for Honeypot Subnet
Create an NSG:
- `nsg-honeypots`

**Inbound rules (principle: minimal but attractive):**
Allow only the services you intentionally want to expose, for example:
- SSH (22) if running an SSH honeypot
- HTTP/HTTPS (80/443) if running web honeypots
- Any additional honeypot ports as required by your configuration

**Outbound rules (principle: prevent harm):**
- Restrict outbound traffic as much as possible
- Consider allowing only necessary outbound destinations for updates/telemetry
- Block high-risk outbound traffic paths where feasible

> The objective is to observe attacker activity, not allow the honeypot to be used to attack others.

### 4.2 NSG for Management Subnet (Optional)
If a management subnet is used:
- Allow inbound access only from trusted sources (your IP or a private jump)
- Restrict administrative ports and require strong authentication controls

---

## Step 5 — Public Exposure Strategy
Honeypots often require controlled public exposure.

Best practice approach:
- Assign a public IP only to honeypot-facing components that require it
- Avoid exposing management interfaces publicly
- Use NSGs to strictly limit what is reachable

**Recommendation:** Treat the environment as hostile and assume compromise.

---

## Step 6 — Identity & Access Control (Azure RBAC)
Apply least privilege access:

Recommended roles:
- Use separate accounts for administration and standard access
- Grant access only to what is required (resource group scope where possible)
- Avoid subscription-wide owner roles unless necessary

**Auditability:**
- Ensure activity logging is enabled (covered in logging section)
- Use clear tagging and naming conventions to support tracking

---

## Step 7 — Resource Tagging & Naming
Use consistent naming and tags to support governance and cost tracking.

Suggested tags:
- `Environment: HoneypotLab`
- `Project: CloudThreatIntel`
- `Owner: <your-handle>`
- `DataSensitivity: Low`
- `CostCenter: SecurityResearch`

**Why:** tag discipline supports professional operations and simplifies reporting.

---

## Step 8 — Baseline Hardening (Cloud Layer)
Even though honeypots may simulate vulnerable services, the **cloud control plane** should be hardened:

- Enable MFA for admin accounts
- Limit who can create/modify NSG rules
- Use Azure security recommendations where appropriate
- Enable resource locks (optional) to prevent accidental deletion
- Configure budget alerts

---

## Step 9 — Validation Checklist (Before Deploying Honeypots)
Confirm the following before deploying the honeypot VMs:

- [ ] Resource group created and isolated
- [ ] VNet and subnets created correctly
- [ ] NSG rules match intended exposed services
- [ ] Outbound restrictions considered and applied
- [ ] Management access is restricted (or not exposed)
- [ ] RBAC permissions follow least privilege
- [ ] Naming and tags applied consistently
- [ ] Logging plan is ready (next document)

---

## Next Steps
Proceed to deploy the honeypot host(s) and services:

- `deployment/honeypot-deployment.md`

Then configure logging and collection:

- `deployment/logging-and-collection.md`

