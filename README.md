# O-NYX

### An AI-Powered Adaptive Threat Intelligence Platform Using Digital-Twin Network Simulation for Sandbox-Evasive Malware Detection

> **Undergraduate Research Opportunity Programme (UROP) — SRM Institute of Science and Technology**  
> **Domain:** Cybersecurity · Malware Analysis · Applied AI

---

## Overview

**O-NYX** is a research-driven, AI-powered adaptive threat-intelligence and malware-defence framework designed to address a major weakness in conventional malware analysis: **sandbox evasion**.

Modern evasive malware, particularly Advanced Persistent Threat (APT) tooling and environment-aware ransomware, can identify when it is being executed inside a sterile analysis environment. Instead of revealing its malicious behaviour, the malware may remain dormant, resulting in a false-negative verdict.

O-NYX approaches this problem from a different perspective.

Rather than placing suspicious files inside a generic sandbox, O-NYX constructs a **high-fidelity digital twin of the target organisation's network environment**. The simulated environment includes realistic infrastructure such as domain controllers, file and email servers, employee endpoints, databases, backup systems, network activity, and user sessions.

The suspicious file is then detonated inside this environment while a covert AI observation layer monitors its behaviour through **hypervisor-level virtual-machine introspection**.

The objective is to create an analysis environment in which malware has fewer obvious indicators that it is being observed.

O-NYX extends beyond malware detection by connecting **pre-exploitation interception, adaptive sandbox analysis, behavioural classification, containment, forensic evidence preservation, infection-impact prediction, and threat-intelligence distribution** into a continuous lifecycle.

---

# Research Motivation

Traditional sandbox-based malware analysis commonly relies on predefined or generic virtual environments.

Sophisticated malware can fingerprint these environments by checking for characteristics such as:

- Absence of realistic users
- Lack of domain membership
- Artificial filesystem structures
- Missing enterprise applications
- Minimal network activity
- Unrealistic hostnames and configurations
- Virtualisation artefacts
- Lack of realistic documents and business data

When these indicators are detected, malware may deliberately remain inactive.

This creates a fundamental problem:

```text
Suspicious File
      │
      ▼
Generic Sandbox
      │
      ▼
Environment Fingerprinting
      │
      ▼
Malware Detects Analysis Environment
      │
      ▼
Malicious Behaviour Remains Dormant
      │
      ▼
False-Negative Verdict
