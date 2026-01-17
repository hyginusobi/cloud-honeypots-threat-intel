# Honeypot Deployment

## Purpose
This document explains how to deploy the honeypot host(s) and services within the isolated Azure environment created in `azure-environment-setup.md`.

The objectives are to:
- Deploy one or more honeypot virtual machines (VMs)
- Expose only intentionally selected services (e.g., SSH, web)
- Ensure safe containment and observability
- Prepare the environment for logging and threat intelligence collection

> **Important:** Do not publish real public IPs, usernames, passwords, SSH keys, subscription IDs, or resource IDs. Use placeholders.

---

## Deployment Options
You can deploy honeypots in different ways depending on your approach and tooling:

### Option A — Single VM Honeypot Host
A single VM hosts one or more honeypot services (good for simple environments).

Pros:
- Fast to deploy
- Easier to manage
- Lower cost

Cons:
- Less realistic segmentation between services

### Option B — Multi-VM Honeypot Services
Separate VMs for different honeypots (more realistic, more scalable).

Pros:
- Better isolation between services
- More realistic attack surface

Cons:
- Higher cost and management overhead

### Option C — Containerised Honeypot Platform
A single VM runs multiple honeypots via containers.

Pros:
- Flexible and scalable
- Easy to add/remove services

Cons:
- Requires container familiarity

This project follows an operationally practical approach aligned to threat intelligence collection and SOC workflows.

---

## Step 1 — Create the Honeypot VM
Create a VM in the `snet-honeypots` subnet.

Recommended baseline:
- OS: Linux (commonly used for honeypot tooling)
- Size: start small and scale based on logging volume
- Disk: standard SSD is often sufficient
- Authentication: use strong credentials and secure access patterns

**Security Notes:**
- Avoid exposing admin management ports publicly
- Use least privilege for VM access
- Keep the cloud layer hardened even if the honeypot layer is intentionally observable

---

## Step 2 — Configure Network Exposure (NSG Rules)
Expose only the services you intend to observe.

Examples (choose based on your honeypots):
- SSH (22) for SSH honeypot activity
- HTTP (80) / HTTPS (443) for web honeypot activity
- Other specific ports only if required

**Do not** open wide port ranges unless you have a controlled reason.

### Outbound Controls
Honeypots can be abused if not controlled.

Recommended:
- Restrict outbound traffic where possible
- Do not allow unrestricted outbound scanning behaviour
- Allow only what is necessary for updates and telemetry/log forwarding

---

## Step 3 — Install Honeypot Services
Install the honeypot service(s) based on the attack surface you want to observe.

Typical examples:
- SSH honeypot (captures brute force attempts, credential stuffing, commands)
- Web honeypot (captures probing, exploit attempts, malicious payloads)
- Generic service emulators (captures scanning and fingerprinting behaviour)

Key principle:
> Deploy only what you can monitor and safely contain.

---

## Step 4 — Configure Logging on the Honeypot Host
Enable or confirm local logging for:
- Authentication attempts
- System events
- Honeypot application logs
- Network connections

Ensure:
- Logs are timestamped consistently
- Logs are written to known locations
- Logging is not overwritten too quickly (retain enough for analysis)

You will centralise logs in `deployment/logging-and-collection.md`.

---

## Step 5 — Validation: Confirm the Honeypot is Reachable
From a safe test environment, validate that:
- Intended services respond
- Unintended ports are closed
- The system is stable under basic scanning activity

Checks:
- Confirm NSG inbound allows only your target ports
- Confirm no exposed admin interfaces
- Confirm logging is being generated

---

## Step 6 — Safety Controls & Containment Checks
Before leaving the environment running:

- Confirm outbound restrictions are in place
- Confirm no sensitive data exists on the honeypot host
- Confirm the honeypot cannot reach internal systems
- Confirm access to the VM is protected (strong credentials / limited access)
- Confirm you can rebuild the VM quickly if needed

> Assume compromise. Honeypots should be built to be disposable.

---

## Step 7 — Operational Notes (Runbook Mindset)
To operate this environment safely:
- Treat every event as potentially hostile
- Collect logs frequently (avoid losing data to rotation)
- Keep the environment monitored for abnormal outbound behaviour
- Document changes (config, ports, services) for repeatability

---

## Deployment Checklist
Use this checklist before proceeding:

- [ ] Honeypot VM deployed in correct subnet
- [ ] NSG inbound rules limited to intended honeypot services
- [ ] Outbound restrictions in place where feasible
- [ ] Honeypot service(s) installed and running
- [ ] Local logs enabled and generating expected events
- [ ] No exposed admin interfaces
- [ ] Environment is isolated from any production/internal networks
- [ ] Ready for centralised log collection configuration

---

## Next Step
Proceed to set up centralised logging and collection:

- `deployment/logging-and-collection.md`

