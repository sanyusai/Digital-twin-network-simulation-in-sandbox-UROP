# O-NYX: Related Work — Papers, Patents, and Ongoing Research

Compiled literature and patent landscape mapped to O-NYX's three phases (pre-, mid-, post-exploitation) and its core novelty claim: digital-twin network simulation as a sandbox-evasion countermeasure.

---

## 1. Digital Twins for Cybersecurity / Malware Detonation (Core Novelty Area)

This is the pillar closest to O-NYX's central architectural insight. No single paper below does exactly what O-NYX proposes (org-specific twin + covert hypervisor observer + full lifecycle), but each covers a load-bearing piece — this is your "gap in the literature" evidence.

- **"Cyber digital twin simulator for security controls requirements"** (US Patent, image-ppubs.uspto.gov) — A CDT platform running simulations on an enterprise-network digital twin built from attack-graph analytics, used to prioritize security control requirements and measure control efficacy. Closest *patented* prior art to the "organization-specific twin" concept, though scoped to control-gap analysis rather than detonation/evasion defeat.
- **"Sandbox-Enabled Digital Twin for Cyber-Physical Systems"** (arXiv, 2606.17001) — Digital twin + sandbox integration for CPS security monitoring and malware detection; cites real-time subcomponent measurement and tamper-proof NIC-based traffic measurement for intrusion detection. Relevant for the CPS/OT extension of O-NYX's model.
- **"Optimal Security Response to Network Intrusions in IT Systems"** (arXiv 2502.02541) — Builds a digital twin of IT infrastructure (hosts, switches, attacker/defender emulation) to optimize automated response strategies; useful for O-NYX's "type-specific adaptive containment" evaluation methodology.
- **"Automated Security Response through Online Learning with Adaptive Conjectures"** (arXiv 2402.12499) — Constructs a digital twin of a 64-server target infrastructure using container-based emulation (Linux bridges/namespaces) to estimate attacker behavior parameters for an APT use case. Good methodological reference for how to *build* a lightweight organizational twin.
- **"Digital Twin-Based Cybersecurity for Smart Infrastructure Systems"** (ResearchGate, 2024) — Frames digital twins as sandbox/deception/decision-support tools; uses game-theoretic (Stackelberg) attacker-defender modeling across smart grid, transport, and water systems.
- **"Advancing Cybersecurity with Digital Twin Technology"** (ResearchGate, 2025) — Explicitly surveys the convergence of digital twin + cyber deception technology, notes the field is still largely theoretical with a "scarcity of mature scientific and commercial contributions" — directly supports your novelty/gap argument. Proposes a 7-function OT deception framework (replicate, attract, control, monitor, analyze...).
- **"Security Attacks and Solutions for Digital Twins"** (arXiv 2202.12501) — Attacker's-eye-view of digital twins; discusses how sophisticated malware (Stuxnet, Triton) has historically defeated isolation mechanisms including sandboxes and air gaps — useful for your threat-model/motivation section.
- Industry/practitioner pieces worth citing for context (not peer-reviewed, but good motivating references): Brandefense, "Digital Twins: The Virtual Powerhouses Reshaping Cybersecurity"; Ampcus Cyber, "Role of Digital Twin Simulation on Cybersecurity."

---

## 2. Sandbox Evasion Techniques & Countermeasures (Problem Statement Support)

- **"Malware Dynamic Analysis Evasion Techniques: A Survey"** (ResearchGate, 2018) — Comprehensive taxonomy of evasion tactics: environment fingerprinting, reverse Turing tests (mouse-movement/human-interaction checks), targeted/fingerprint-specific detonation. Foundational citation for your Problem Statement section.
- **"POW-HOW: An Enduring Timing Side-Channel to Evade Online Malware Sandboxes"** (arXiv 2109.02979) — Shows how malware can use Proof-of-Work timing side-channels to detect non-bare-metal sandbox environments, evading even hardened analysis services. Strong evidence that fingerprinting evasion keeps evolving past current defenses.
- **"Beyond the Sandbox: Leveraging Symbolic Execution for Evasive Malware Classification"** (ScienceDirect, 2024) — Proposes tiered/binary-simulation triage to filter samples before full sandbox detonation — conceptually parallel to O-NYX's Phase-1 trust-score triage engine.
- **"Countering Malware Detection Evasion Techniques"** (US Patent 11,416,611, VMware) — Patent addressing agent-based endpoint classification + sandbox validation loop, explicitly naming the sandbox-detection problem O-NYX is built to solve.
- **"Undetectable Sandbox for Malware"** (US Patents 11,568,052 and 12,039,034) — Two related patents (same lineage) directly targeting *undetectable* sandboxing — the exact competitive prior art you should distinguish O-NYX against, since these patch generic sandbox fingerprints rather than build organization-specific twins.

---

## 3. Hypervisor-Level VM Introspection (Covert Observer Design)

- **Garfinkel & Rosenblum, "A Virtual Machine Introspection Based Architecture for Intrusion Detection"** (NDSS/SNDSS) — The foundational VMI paper, cited across nearly all subsequent work; establishes the out-of-VM, agentless monitoring principle O-NYX's covert observer relies on.
- **"Dynamic Malware Analysis Using IntroVirt: A Modified Hypervisor-Based System"** (ResearchGate) — Xen-based introspective hypervisor capable of manipulating/spoofing system-call returns to *defeat* malware's own VM-detection checks — a near-exact prior implementation of O-NYX's "invisible to the executing process" observer requirement.
- **"Leveraging Virtual Machine Introspection with Memory Forensics to Detect and Characterize Unknown Malware Using ML at Hypervisor"** (ScienceDirect / A-IntExt system) — VMI + memory forensics + ML pipeline at the hypervisor (Dom0), directly analogous to O-NYX's "behaviour watcher + intent classifier + risk scorer" stack.
- **"Hardware Assisted Hypervisor Introspection"** (PMC, NCBI) — Uses nested virtualization/EPT protection to monitor hypercalls even under a compromised hypervisor; relevant for hardening O-NYX's observer against detection or tampering.
- **"Hypervisor Memory Introspection and Hypervisor Based Malware Honeypot"** (ResearchGate, 2020) — Combines VMI with honeypot deployment and covert-channel detection; bridges the introspection and deception literatures directly.
- **"Register Caching for Efficient Virtual Machine Introspection"** (US Patent, filed 2022) — Recent patent on performance optimization for VMI-based malware detection services — relevant to your "expected outcomes" section if you discuss detonation throughput/latency.
- **VM Introspection in Virtualization: A Security Perspective** (ACM DL) — General survey of VMI techniques (semantic gap, hash-based code-page classification, memory modification mapping).

---

## 4. Cyber Deception / High-Fidelity Organizational Mimicry (Digital-Twin "Believability" Layer)

- **"PHANTOM: Polymorphic Honeytoken Adaptation with Narrative-Tailored Organisational Mimicry"** (arXiv 2605.02992) — Very close conceptually to O-NYX's "digital twin using the org's real hostnames/domain structure/folder conventions." Worth reading in full — likely your single most important related-work citation.
- **"SANDMAN: Inducing Personality in LLM-Based Honeypot Agents"** (arXiv 2503.19752, Lancaster University) — Uses LLM-driven personas to generate human-like decoy behavior ("Deceptive Agents") to extend attacker engagement time — directly relevant to O-NYX's "live-looking user sessions."
- **Acalvio "Deception Farms" architecture** (patented, per Acalvio competitive-intelligence writeups) — Commercial patented architecture for scalable, AI-driven decoy generation across IT/OT/cloud; useful as an industry benchmark/competitor to position O-NYX against.
- **"Containing Compromised Credentials Using Deception Systems"** (US Patent 11,303,675) — Honeypot ecosystem patent for credential-based deception and lateral-movement detection.
- **"Cyber Security" (message-simulation deception patent, PCT/AU2022/050748)** — Patent on simulating fake conversations/communications on a network for honeypot realism — relevant to O-NYX's "live-looking employee sessions" claim.
- **"Deceiving an Attacker Who Is Harvesting Credentials"** (US Patent 10,333,977) — Addresses a key weakness of static honeypots (visible/static deceptive data) via attacker-only-visible deceptive data generation.
- Fidelis Security & Acalvio industry blogs on honeypot-vs-deception-tech evolution — useful for a "five generations of deception technology" framing in your related-work narrative.

---

## 5. MITRE ATT&CK-Based Behavioral Classification (Covert Agent's Analysis Engine)

- **"Malware2ATT&CK: A Sophisticated Model for Mapping Malware to ATT&CK Techniques"** (Computers & Security, 2024) — Directly maps malware behavior to TTPs; has since spawned follow-on work (e.g., APIMatch-ATT&CK, 2026) on automated Android API-to-ATT&CK mapping.
- **"Malware of Dynamic Behavior and Attack Patterns Using ATT&CK Framework"** (ScienceDirect, 2025) — Fine-tunes an LLM (Gemma 2B) on MITRE documentation to semantically map behavioral data to ATT&CK techniques, including for previously unseen malware — closely mirrors O-NYX's "ATT&CK mapper" component.
- **"MITRE ATT&CK: State of the Art and Way Forward"** (ACM Computing Surveys, 2024) — Broad survey; discusses ML-based frameworks trained on ATT&CK-labeled behavior, including the WannaCry case study using Joe Sandbox Cloud.
- **"Mind the Gap: On Bridging the Semantic Gap between ML and Information Security"** (arXiv 2005.01800) — Introduces the MITRE Malware Behavior Catalog (MBC) as a finer-grained complement to ATT&CK; useful for justifying your risk-scoring taxonomy.
- **"A Multi-Label Visualisation Approach for Malware Behaviour Analysis"** (PMC, 2025) — Multi-agent (Reviewer/Adversarial/Consensus/Verifier) explainability pipeline grounded in ATT&CK — relevant if you want to add explainability to O-NYX's forensic brief.
- **"A Robust and Dynamic Malware Detection and Classification Model Using Behavioral-Based Analysis and BERT"** (PLOS ONE, 2025).
- **Joe Sandbox Cloud** — referenced across multiple papers as the standard commercial dynamic-analysis platform for building ATT&CK-labeled datasets; useful as a baseline/comparison system for your evaluation section.

---

## 6. Ransomware-Specific Adaptive Containment (Time-Machine / Auto-Rollback)

- **"Storage System with Snapshot-Based Detection and Remediation of Ransomware Attacks"** (US Patent 11,030,314) — Automatic two-snapshot rollback mechanism triggered on ransomware detection; core prior art for O-NYX's "ransomware time machine."
- **"Automated Ransomware Recovery Using Log-Structured Storage"** (US Patent 12,058,169) and **"Automated Virtualized Storage Snapshotting Responsive to Ransomware Detection"** (US Patent 12,197,578) — Cloud-oriented automatic snapshot/rollback + isolation patents (I/O proxy-based detection, VPN/firewall auto-isolation on infection).
- **"Detecting Anomalous I/O Patterns Indicative of Ransomware Attacks"** (US Patent 12,086,250) — I/O-pattern anomaly detection feeding the same rollback pipeline.
- **"Accelerating Method of Snapshot Investigation for Rollback from Ransomware"** (US Patent 11,372,976).
- **"Towards Low-Latency and Adaptive Ransomware Detection Using Contrastive Learning"** (arXiv 2510.21957, 2025) — Real-time detection loop with lightweight rolling backups (rsync-based) deleted if no threat found — a very current (2025) academic analogue to your "time machine."
- Industry references worth citing for baselines: SentinelOne Singularity rollback (VSS-based, 4-hour snapshot cadence), Adaptive Security's 2026 writeup on ransomware detection evolution (BYOVD-driven EDR evasion — relevant to your "why generic EDR isn't enough" argument).

---

## 7. Threat-Intelligence Distribution (STIX/TAXII, Post-Exploitation Phase)

- **"Sharing Cyber Threat Intelligence: Does It Really Help?"** (NDSS Symposium, 2024) — Large-scale empirical study of real-world STIX sharing volumes/quality across open CTI sources; found that providers share only ~2,063 unique STIX objects/day on average — a good citation for motivating why O-NYX's automated, instant STIX/TAXII broadcast adds value.
- **"Current Approaches and Future Directions for Cyber Threat Intelligence Sharing: A Survey"** (ScienceDirect, 2024) — Compares STIX/TAXII against IODEF, OpenIOC, CybOX; surveys commercial CTI platforms (IBM X-Force Exchange, etc.).
- **"Towards Cyber Threat Intelligence for the IoT"** (arXiv 2406.13543) — STIX/TAXII sharing-model taxonomy (hub-and-spoke, peer-to-peer) applied to IoT threat data.
- Practitioner/vendor explainers worth citing for definitions: Sekoia, VMRay, Cyware, Anomali, Kraven Security — useful for a concise STIX-vs-TAXII definitional paragraph, and for citing SIEM/SOAR integration patterns (Splunk, QRadar, Elastic ingesting TAXII feeds).

---

## 8. Adjacent / Emerging Work Worth Monitoring

- **"The Rhythm of Execution: Unveiling the Impact of Sandbox Execution Time on Cyber Threat Intelligence Data"** (Frontiers of Computer Science, 2025) — Studies how sandbox detonation duration affects CTI data quality; directly relevant to O-NYX's design choice of full-run (not streaming) verdicts.
- **"Passive Hack-Back Strategies for Cyber Attribution: Covert Vectors in Denied Environments"** (arXiv 2508.16637, 2025) — Touches on attribution-avoidance design, relevant to O-NYX's deliberate non-attribution stance (TTP-similarity instead of hard attribution).
- Ongoing commercial R&D to track: **Acalvio ShadowPlex** (AI-driven deception, "Company to Beat" — Gartner 2025), **Fidelis Deception/Elevate XDR**, and continued VMware/Broadcom sandbox-evasion patent filings (11,416,611 and 11,568,052 families) — these represent the closest commercial competitors/prior art you'll want to differentiate O-NYX from in your patent-landscape or novelty section.

---

## Suggested Use in Your Report

1. **Problem Statement** → Section 2 (evasion surveys, POW-HOW, symbolic execution triage).
2. **Related Work / Novelty positioning** → Sections 1 and 4 (digital twin + deception convergence is thin — this is your strongest novelty claim; PHANTOM and SANDMAN are your closest neighbors).
3. **System Design — Covert Observer** → Section 3 (VMI foundations: Garfinkel & Rosenblum, IntroVirt, A-IntExt).
4. **System Design — Classification Engine** → Section 5 (ATT&CK/LLM mapping papers).
5. **System Design — Containment** → Section 6 (ransomware rollback patents + 2025 contrastive-learning paper).
6. **System Design — Intelligence Distribution** → Section 7 (STIX/TAXII surveys).
7. **Patent Landscape / Freedom-to-Operate discussion** → Sections 2, 4, and 6 patent citations — flag these explicitly if your UROP writeup needs an IP-novelty discussion, since several assignees (VMware/Broadcom, Dell/storage vendors, Acalvio) hold adjacent patents.

*Note: This list reflects what is publicly indexed and searchable as of September 2026. A patent landscape this broad (VMI, deception, ransomware rollback, digital twins) usually benefits from a formal prior-art/FTO search via a patent database (USPTO full-text, Google Patents, Espacenet) rather than web search alone if you intend to pursue IP protection for O-NYX.*
