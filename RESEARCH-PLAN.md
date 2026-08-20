# O-NYX

### An AI-Powered Adaptive Threat Intelligence Platform Using Digital-Twin Network Simulation for Sandbox-Evasive Malware Detection

> **Undergraduate Research Opportunity Programme (UROP) — SRM Institute of Science and Technology**
> **Domain:** Cybersecurity · Malware Analysis · Applied AI

---

## Overview

**O-NYX** is a research-driven, AI-powered adaptive threat-intelligence and malware-defence framework designed to address a major weakness in conventional malware analysis: **sandbox evasion**.

Modern malware, particularly Advanced Persistent Threat (APT) tooling and environment-aware ransomware, can identify when it is being executed inside a sterile analysis environment. Instead of revealing its malicious behaviour, the malware may remain dormant, resulting in a false-negative verdict.

O-NYX approaches this problem from a different perspective.

Rather than placing suspicious files inside a generic sandbox, O-NYX constructs a **high-fidelity digital twin of the target organisation's network environment**. The simulated environment includes realistic infrastructure such as domain controllers, file and email servers, employee endpoints, databases, backup systems, network activity, and user sessions.

The suspicious file is then detonated inside this environment while a covert AI observation layer monitors its behaviour through **hypervisor-level virtual-machine introspection**.

The objective is to create an analysis environment in which malware has fewer obvious indicators that it is being observed.

O-NYX extends beyond malware detection by connecting **pre-exploitation interception, adaptive sandbox analysis, behavioural classification, containment, forensic evidence preservation, infection-impact prediction, and threat-intelligence distribution** into a continuous lifecycle.

---

## Research Motivation

Traditional sandbox-based malware analysis commonly relies on predefined or generic virtual environments.

Sophisticated malware can fingerprint these environments by checking for characteristics such as:

* Absence of realistic users
* Lack of domain membership
* Artificial filesystem structures
* Missing enterprise applications
* Minimal network activity
* Unrealistic hostnames and configurations
* Virtualisation artefacts
* Lack of realistic documents and business data

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
```

O-NYX investigates whether a **deception-oriented, organisation-specific digital twin** can increase the probability of activating and observing such malware.

---

# Core Research Idea

The central architectural insight behind O-NYX is:

> **Malware is more likely to reveal its true behaviour when it believes it is operating inside a realistic organisational environment.**

Instead of analysing a suspicious file in an isolated generic VM, O-NYX creates a simulated representation of the organisation and provides the malware with realistic environmental context.

```text
                    ┌──────────────────────┐
                    │   Suspicious File     │
                    └──────────┬───────────┘
                               │
                               ▼
                  ┌─────────────────────────┐
                  │  AI Pre-Screening Layer │
                  └────────────┬────────────┘
                               │
                       Suspicious / Unknown
                               │
                               ▼
              ┌────────────────────────────────┐
              │   Organisation Digital Twin     │
              │                                │
              │  Domain Controller             │
              │  Employee Endpoints            │
              │  File / Email Servers          │
              │  Database                       │
              │  Backup Server                  │
              │  Proxy / Network Activity       │
              └───────────────┬────────────────┘
                              │
                              ▼
                   ┌─────────────────────┐
                   │ Malware Detonation  │
                   └──────────┬──────────┘
                              │
                              ▼
                ┌───────────────────────────┐
                │ Covert AI Observer Agent  │
                │ Hypervisor Introspection  │
                └─────────────┬─────────────┘
                              │
                              ▼
                ┌───────────────────────────┐
                │ Behaviour & Intent        │
                │ Classification            │
                └─────────────┬─────────────┘
                              │
                              ▼
                ┌───────────────────────────┐
                │ ATT&CK Mapping & Risk     │
                │ Scoring                   │
                └─────────────┬─────────────┘
                              │
                              ▼
                ┌───────────────────────────┐
                │ Adaptive Containment       │
                │ + Blast-Radius Prediction  │
                └─────────────┬─────────────┘
                              │
                              ▼
                ┌───────────────────────────┐
                │ Forensic Evidence Sealing  │
                └─────────────┬─────────────┘
                              │
                              ▼
                ┌───────────────────────────┐
                │ Threat Intelligence       │
                │ STIX / TAXII Distribution  │
                └───────────────────────────┘
```

---

# Full-Lifecycle Architecture

O-NYX is organised into **three integrated phases**.

## Phase 1 — Pre-Exploitation

The first stage operates at the file-download layer.

Suspicious files are intercepted and evaluated before they reach the endpoint.

The proposed pre-screening pipeline incorporates:

* Hash-based reputation checks
* YARA-based analysis
* Machine-learning classification
* Phishing URL analysis
* Static analysis
* Content Disarm and Reconstruction (CDR)
* Honeypot network observation
* Ransomware snapshot / rollback mechanisms
* Attacker-intent analysis
* Trust scoring

The resulting analysis determines whether a file should be:

```text
BLOCK + ALERT
      │
      ├── PASS THROUGH
      │
      └── DEEP SANDBOX ANALYSIS
```

The architecture describes a **0–100 trust score** as an additional decision signal.

---

# Phase 2 — Mid-Exploitation

Files that remain suspicious after initial analysis are transferred into the digital-twin environment.

The digital twin is intended to represent the organisation's real network structure, including components such as:

* Domain controller
* File servers
* Email servers
* Employee endpoints
* Database
* Backup server
* Web proxy
* Organisational folder conventions
* Hostnames
* Domain structure
* Simulated user sessions

The environment is continuously updated through a network-discovery process.

The suspicious file is then executed at a dedicated detonation point.

---

## Covert Hypervisor-Level AI Observer

One of the central components of O-NYX is the **covert AI observer agent**.

Instead of relying exclusively on monitoring mechanisms visible inside the guest operating system, the proposed architecture uses **hypervisor-level virtual-machine introspection**.

The observer analyses:

* Process behaviour
* System activity
* Network behaviour
* Malware intent
* ATT&CK techniques
* Risk indicators
* Potential attack progression

The observer is designed to remain outside the malware's normal execution environment, reducing the likelihood that the malware can directly identify and disable the monitoring mechanism.

---

# AI-Powered Behaviour Analysis

O-NYX combines behavioural observation with AI-assisted reasoning.

The analysis pipeline includes:

```text
Runtime Behaviour
       │
       ▼
Behaviour Watcher
       │
       ▼
Intent Classification
       │
       ▼
MITRE ATT&CK Mapping
       │
       ▼
Risk Scoring
       │
       ▼
Forensic Report
```

Rather than making a final judgement from incomplete activity during an ongoing attack, the architecture proposes producing the primary forensic assessment after the complete analysis run.

This is intended to reduce unreliable conclusions based on partial behavioural evidence.

---

# Adaptive Containment

O-NYX does not treat every malicious sample identically.

The framework proposes **type-specific containment strategies** for malware categories including:

* Ransomware
* Botnets
* Worms
* Remote Access Trojans (RATs)
* Trojans

The containment system is connected to a predicted **blast-radius map**.

Instead of producing only:

```text
MALICIOUS
```

O-NYX aims to answer:

```text
What happened?
       +
What technique was used?
       +
What systems could be affected?
       +
How could the infection propagate?
       +
What containment action should be considered?
```

All consequential containment actions remain subject to human approval.

---

# Infection & Blast-Radius Analysis

A major research direction of O-NYX is the use of the digital twin to understand potential attack propagation.

The system can model the potential relationship between:

```text
Compromised Endpoint
        │
        ├── File Server
        │
        ├── Domain Controller
        │
        ├── Database
        │
        ├── Backup Infrastructure
        │
        └── Other Endpoints
```

This allows the framework to move beyond simple malware classification and investigate **potential organisational impact**.

The research specifically targets blast-radius and business-impact prediction as part of its adaptive containment architecture.

---

# Phase 3 — Post-Exploitation

After analysis is complete, O-NYX moves into the post-exploitation and evidence-preservation stage.

Collected evidence may include:

* Volatile memory
* Network captures
* Filesystem differences
* Behavioural observations
* AI-generated forensic reports

The evidence is:

1. Hash-chained
2. Cryptographically signed
3. Stored in an immutable audit store
4. Preserved before sandbox disposal

The environment is then securely disposed of through:

```text
VM Termination
      ↓
Memory Zeroisation
      ↓
Disk Cryptoshredding
      ↓
VPC Teardown
      ↓
Zero-Persistence Verification
```

A fresh digital twin can subsequently be reconstructed for the next analysis cycle.

---

# Threat Intelligence Layer

O-NYX is designed to extend beyond individual malware analysis.

After analysis, extracted intelligence can include:

### TTP Similarity

The observed behaviour is compared against known threat-actor techniques and behaviours.

Importantly, the framework uses **confidence-scored similarity rather than claiming definitive attribution**.

### MITRE ATT&CK Mapping

Observed behaviour is mapped to relevant ATT&CK techniques and tactics.

### IOC Extraction

Indicators of compromise can be packaged for downstream security systems.

### STIX / TAXII Distribution

Validated intelligence can be distributed through standardised threat-intelligence protocols.

The architecture proposes integration with platforms such as **MISP** and distinguishes ordinary IOC sharing from zero-day candidate handling.

---

# Responsible Zero-Day Handling

O-NYX does **not** automatically claim that a previously unknown behaviour is a confirmed zero-day.

Instead, the framework proposes a:

> **Reviewer-confirmed zero-day candidate**

workflow.

Potential candidates are flagged for analyst review and external corroboration.

This distinction is deliberate:

```text
Unusual Behaviour
       ↓
Potential Novel Technique
       ↓
AI Candidate Flag
       ↓
Human / Analyst Review
       ↓
External Corroboration
       ↓
Validated Finding
```

This avoids overstating what automated analysis can establish.

---

# Human-in-the-Loop Security

O-NYX intentionally avoids completely autonomous high-impact response.

Containment, policy changes, firewall actions, and intelligence disclosure actions are routed through a **human-approval gate**.

```text
AI Recommendation
       │
       ▼
Human Analyst
       │
   ┌───┴───┐
   │       │
APPROVE   REJECT
   │       │
   ▼       ▼
ACTION    LOG
```

This design reduces the potential impact of false positives and keeps consequential security decisions under human oversight.

---

# Key Research Contributions

The current O-NYX research framework focuses on the following contributions:

### 1. Organisation-Specific Digital Twin

A high-fidelity digital-twin environment designed specifically to make sandbox-evasive malware more likely to reveal its behaviour.

### 2. Covert Hypervisor-Level Observation

A stateless AI observation mechanism operating through VM introspection rather than relying exclusively on guest-visible monitoring.

### 3. Full-Lifecycle Defence

Integration of:

```text
Pre-Exploitation
        ↓
Mid-Exploitation
        ↓
Post-Exploitation
```

into a continuous pipeline.

### 4. Adaptive Malware-Specific Containment

Containment recommendations tailored to different malware families rather than a generic response.

### 5. Blast-Radius Prediction

Use of the digital twin to estimate potential organisational impact and infection propagation.

### 6. Forensically Sound Evidence Handling

Cryptographic evidence sealing, immutable auditing, and verifiable sandbox disposal.

### 7. Threat-Intelligence Generation

Transformation of malware observations into:

* TTP similarity
* ATT&CK mappings
* IOCs
* Threat-intelligence packages

### 8. Human-Controlled Response

Security-critical actions remain subject to analyst approval.

These contributions are based on the project's current research abstract and architecture description.

---

# Research Objectives

The project investigates whether O-NYX can:

1. Increase the activation/detonation rate of sandbox-aware malware compared with generic sandbox environments.
2. Improve malware behavioural visibility through organisation-specific digital twins.
3. Reduce time-to-containment through adaptive response playbooks.
4. Predict potential malware blast radius using simulated network infrastructure.
5. Generate structured forensic evidence from complete malware executions.
6. Produce reusable threat-intelligence artefacts.
7. Reduce the time between malware analysis and IOC availability through STIX/TAXII distribution.

These objectives are aligned with the evaluation directions defined in the project abstract.

---

# Evaluation Strategy

The research will focus on measurable outcomes rather than feature count.

## Metric 1 — Malware Activation Rate

Compare:

```text
Generic Sandbox
        VS
O-NYX Digital Twin
```

using known sandbox-evasive malware samples.

### Goal

Determine whether the organisation-specific environment increases the proportion of samples that reveal meaningful malicious behaviour.

---

## Metric 2 — Time-to-Containment

Measure the time between:

```text
Detection
   ↓
Classification
   ↓
Human Approval
   ↓
Containment
```

The research will investigate whether type-specific response playbooks reduce containment time.

---

## Metric 3 — Threat Intelligence Latency

Measure:

```text
Malware Detonation
        ↓
Analysis
        ↓
IOC Extraction
        ↓
STIX/TAXII Publication
        ↓
Availability to Connected Systems
```

The research aims to evaluate how quickly useful intelligence can become available after a single malware detonation.

---

# Research Scope

The initial O-NYX architecture is deliberately bounded around the **file-download attack surface**.

It is designed to complement rather than replace:

* Email security gateways
* Endpoint security
* Firewalls
* IDS/IPS
* Existing SOC infrastructure

This bounded scope is intended to keep the first version of the research technically and experimentally manageable.

---

# Safety & Ethics

O-NYX is a cybersecurity research platform intended for controlled malware-analysis environments.

All malware execution and experimentation should take place within appropriately isolated infrastructure.

Recommended principles include:

* Never execute unknown malware on a production system.
* Use isolated virtual networks.
* Avoid exposing analysis environments directly to the public Internet.
* Use synthetic or controlled organisational data.
* Do not use real credentials.
* Maintain strict access controls.
* Require human approval for consequential security actions.
* Preserve forensic evidence securely.
* Follow responsible disclosure procedures for potential vulnerabilities.
* Conduct experiments only on systems and samples for which appropriate authorization exists.

---

# Project Architecture

The repository is organised around the major research components of O-NYX.

```text
O-NYX/
│
├── README.md
│
├── docs/
│   ├── architecture/
│   ├── research/
│   ├── threat-model/
│   └── diagrams/
│
├── digital-twin/
│   ├── network-topology/
│   ├── domain-controller/
│   ├── endpoints/
│   ├── servers/
│   └── services/
│
├── sandbox/
│   ├── detonation/
│   ├── snapshots/
│   ├── isolation/
│   └── disposal/
│
├── ai/
│   ├── pre-screening/
│   ├── behaviour-analysis/
│   ├── intent-classification/
│   ├── risk-scoring/
│   └── threat-intelligence/
│
├── hypervisor-agent/
│   ├── introspection/
│   ├── monitoring/
│   └── telemetry/
│
├── containment/
│   ├── ransomware/
│   ├── botnet/
│   ├── worm/
│   ├── rat/
│   └── trojan/
│
├── forensics/
│   ├── memory/
│   ├── network/
│   ├── filesystem/
│   └── evidence/
│
├── threat-intelligence/
│   ├── ioc/
│   ├── stix/
│   ├── taxii/
│   └── attack-mapping/
│
├── experiments/
│   ├── datasets/
│   ├── baselines/
│   ├── results/
│   └── evaluation/
│
└── research-paper/
    ├── abstract/
    ├── methodology/
    ├── results/
    └── references/
```

> **Note:** The repository structure can evolve as implementation progresses. Components described in the architecture should not be interpreted as completed implementations unless corresponding implementation and evaluation results are provided.

---

# Technology Direction

The project may integrate technologies from several areas:

| Layer                | Research Direction                        |
| -------------------- | ----------------------------------------- |
| Virtualisation       | Isolated VM infrastructure                |
| Digital Twin         | Simulated organisational network          |
| Malware Analysis     | Static + dynamic analysis                 |
| AI/ML                | Behaviour classification and risk scoring |
| Hypervisor           | VM introspection                          |
| Threat Intelligence  | MITRE ATT&CK, STIX/TAXII                  |
| Forensics            | Memory, network and filesystem analysis   |
| Containment          | Malware-specific response playbooks       |
| Evidence             | Hash chaining and cryptographic signing   |
| Intelligence Sharing | MISP / STIX / TAXII                       |

Specific technologies and implementations may change during the research lifecycle.

---

# Research Workflow

```text
                    ┌─────────────────────┐
                    │ File Download        │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ AI Pre-Screening     │
                    └──────────┬──────────┘
                               │
                     ┌─────────┴─────────┐
                     │                   │
                   SAFE              SUSPICIOUS
                     │                   │
                     ▼                   ▼
                  PASS          Digital-Twin Sandbox
                                         │
                                         ▼
                                  Malware Detonation
                                         │
                                         ▼
                                  Covert AI Observer
                                         │
                                         ▼
                                  Behaviour Analysis
                                         │
                                         ▼
                                  ATT&CK + Risk Score
                                         │
                                         ▼
                                  Blast-Radius Analysis
                                         │
                                         ▼
                               Human Approval Gate
                                         │
                                         ▼
                                  Containment Action
                                         │
                                         ▼
                                  Evidence Sealing
                                         │
                                         ▼
                                  Sandbox Disposal
                                         │
                                         ▼
                                Threat Intelligence
                                         │
                                         ▼
                                   STIX / TAXII
```

---

# Current Research Status

O-NYX is being developed as an **undergraduate research project under the UROP framework at SRM Institute of Science and Technology**.

The project is currently focused on:

* Research architecture
* Digital-twin network simulation
* Sandbox-evasion analysis
* AI-assisted malware classification
* Hypervisor-level observation
* Adaptive containment
* Infection/blast-radius analysis
* Forensic evidence handling
* Threat-intelligence extraction
* Experimental evaluation

Implementation status of individual components will be documented throughout the research lifecycle.

---

# Limitations

O-NYX is a research framework and does not claim to eliminate malware or guarantee detection of all evasive threats.

Important limitations include:

* Advanced malware may use previously unknown evasion techniques.
* Digital-twin fidelity directly affects analysis quality.
* AI models may generate false positives or false negatives.
* Hypervisor introspection introduces implementation and performance challenges.
* Blast-radius prediction is inherently probabilistic.
* TTP similarity does not constitute definitive threat-actor attribution.
* Potential zero-day findings require external validation.
* Threat-intelligence sharing depends on compatible infrastructure.
* The current research scope is intentionally limited to the file-download attack surface.

These limitations are part of the research problem rather than being hidden from the evaluation.

---

# Expected Impact

O-NYX aims to demonstrate a shift from:

```text
Detect → Block
```

towards:

```text
Intercept
   ↓
Understand
   ↓
Deceive
   ↓
Observe
   ↓
Classify
   ↓
Predict
   ↓
Contain
   ↓
Preserve Evidence
   ↓
Learn
   ↓
Share Intelligence
```

The long-term research direction is to investigate whether a realistic digital representation of an organisation can become an active component of malware defence rather than simply a passive simulation.

---

# Research Philosophy

O-NYX follows several principles:

### Realistic over Generic

The analysis environment should resemble the target organisation rather than a sterile laboratory VM.

### Behaviour over Verdicts

Complete behavioural evidence should be preferred over premature conclusions.

### Adaptive over Static

Containment should consider malware type and potential impact.

### Evidence over Assumption

Security conclusions should be supported by preserved forensic evidence.

### Human-Controlled over Blind Automation

High-impact actions should remain under analyst control.

### Intelligence over Isolation

The outcome of one analysis should contribute useful intelligence to future defensive operations.

---

# Disclaimer

O-NYX is an academic cybersecurity research project.

This repository may contain experimental code, simulated infrastructure, security-testing components, and research prototypes. It is intended exclusively for **authorized, isolated, and controlled environments**.

Do not deploy experimental components against systems, networks, files, or infrastructure without explicit authorization.

The research framework does not guarantee complete malware detection, attribution, containment, or zero-day discovery.

---

# Research Citation

If this research is formally published or presented, the citation information will be added here.

```text
O-NYX: An AI-Powered Adaptive Threat Intelligence Platform
Using Digital-Twin Network Simulation for Sandbox-Evasive
Malware Detection.

Undergraduate Research Opportunity Programme (UROP)
SRM Institute of Science and Technology.
```

---

# Acknowledgements

This project is being developed as part of the **Undergraduate Research Opportunity Programme (UROP)** at **SRM Institute of Science and Technology**.

The research combines concepts from:

* Cybersecurity
* Malware Analysis
* Digital Twins
* Artificial Intelligence
* Threat Intelligence
* Virtualisation
* Digital Forensics
* Network Security

---

## Project Status

**Research Stage:** Active Development
**Project:** O-NYX
**Focus:** Sandbox-Evasive Malware Detection
**Architecture:** Digital Twin + AI + Hypervisor Introspection + Threat Intelligence
**Research Scope:** Pre-Exploitation → Mid-Exploitation → Post-Exploitation

---

> **O-NYX — Make the sandbox look like home.**
