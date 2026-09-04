# O-NYX – Related Work and Research Progress

## 1. Research on Digital Twins for Cybersecurity

As part of our research on O-NYX, we studied how digital twins are being used in cybersecurity. Our main focus was to understand whether an organization-specific digital twin can help in analysing malware that tries to detect and avoid normal sandbox environments.

We studied several works related to this idea:

- **“Cyber digital twin simulator for security controls requirements”** – This work uses a digital twin of an enterprise network to study security controls and identify security gaps. It helped us understand how the structure of an organization can be represented in a digital environment.

- **“Sandbox-Enabled Digital Twin for Cyber-Physical Systems”** – This combines digital twins and sandbox environments for security monitoring and malware detection. We looked at this work to understand how the same idea could be useful for cyber-physical and industrial systems.

- **“Optimal Security Response to Network Intrusions in IT Systems”** – This work creates a digital twin of an IT infrastructure and uses it to study attacker and defender behaviour. It helped us understand how simulated networks can be used for security testing.

- **“Automated Security Response through Online Learning with Adaptive Conjectures”** – This research uses a lightweight digital twin to study attacker behaviour. We found its approach useful when thinking about how O-NYX could represent an organization's environment without recreating the entire physical infrastructure.

- **“Digital Twin-Based Cybersecurity for Smart Infrastructure Systems”** – We studied this work to understand how digital twins can be used for security and attacker-defender simulations in areas such as smart grids, transport and water systems.

- **“Advancing Cybersecurity with Digital Twin Technology”** – This helped us understand the connection between digital twins and cyber deception. We found that this area is still developing and that there are opportunities for practical implementations.

- **“Security Attacks and Solutions for Digital Twins”** – This work helped us understand how advanced malware can identify or bypass isolated environments such as sandboxes and air-gapped systems.

From these studies, we found that digital twins are already being explored for different cybersecurity applications. However, we did not find a single system that combines an **organization-specific digital twin, covert hypervisor-level monitoring and analysis across the malware lifecycle**. This gap helped us define the direction of our O-NYX research.

---

## 2. Research on Sandbox Evasion

We also studied how malware detects and avoids sandbox environments. This is important because one of the main goals of O-NYX is to reduce the effect of these evasion techniques.

The main works we studied include:

- **“Malware Dynamic Analysis Evasion Techniques: A Survey”** – We used this survey to understand common sandbox-evasion techniques such as environment fingerprinting, checking for human interaction and detecting virtual environments.

- **“POW-HOW: An Enduring Timing Side-Channel to Evade Online Malware Sandboxes”** – This paper showed how malware can use timing information to identify sandbox environments. It helped us understand that sandbox detection can involve more than simple virtual-machine checks.

- **“Beyond the Sandbox: Leveraging Symbolic Execution for Evasive Malware Classification”** – We studied its approach to filtering suspicious samples before complete sandbox execution. This gave us ideas for the initial analysis stage of O-NYX.

- **“Countering Malware Detection Evasion Techniques”** – We reviewed this patent to understand existing methods for identifying sandbox-detection behaviour.

- **“Undetectable Sandbox for Malware”** – We studied these patents because they directly address the problem of making sandbox environments difficult for malware to detect.

From this research, we understood one of the main problems with traditional sandbox analysis: **if malware realizes that it is inside an analysis environment, it may change its behaviour or avoid carrying out its malicious actions.**

This became one of the main problems we wanted to address through O-NYX.

---

## 3. Research on Hypervisor-Level Monitoring

Another important part of our research was Virtual Machine Introspection (VMI). We studied how a virtual machine can be monitored from outside the VM instead of relying only on software running inside it.

We reviewed the following works:

- **Garfinkel and Rosenblum – “A Virtual Machine Introspection Based Architecture for Intrusion Detection”** – This was one of the main references we used to understand the basic concept of monitoring a virtual machine externally.

- **“Dynamic Malware Analysis Using IntroVirt”** – This work uses a hypervisor to monitor malware and can also deal with some VM-detection techniques. We found it closely related to our idea of keeping the monitoring mechanism hidden from the malware.

- **“Leveraging Virtual Machine Introspection with Memory Forensics to Detect and Characterize Unknown Malware Using ML at Hypervisor”** – This combines VMI, memory analysis and machine learning. We studied it to understand how malware behaviour can be collected and analysed at the hypervisor level.

- **“Hardware Assisted Hypervisor Introspection”** – This helped us understand how hardware-supported mechanisms can be used to improve the security of hypervisor monitoring.

- **“Hypervisor Memory Introspection and Hypervisor Based Malware Honeypot”** – We studied this work because it connects VMI with honeypot and deception techniques.

- **“Register Caching for Efficient Virtual Machine Introspection”** – We looked at this work to understand the performance challenges involved in VMI-based monitoring.

Through this research, we understood why an **external and covert observer** can be useful for O-NYX. Our aim is to monitor the behaviour of malware without making the monitoring mechanism easily visible to it.

---

## 4. Research on Cyber Deception

We studied cyber deception to understand how realistic a controlled environment needs to be to prevent attackers or malware from identifying it as a decoy.

One important work we studied was **“PHANTOM: Polymorphic Honeytoken Adaptation with Narrative-Tailored Organisational Mimicry.”** It is related to our idea of creating a digital environment that follows the structure and naming patterns of a real organization.

We also studied **“SANDMAN: Inducing Personality in LLM-Based Honeypot Agents.”** This work uses human-like behaviour in honeypots. It helped us think about how O-NYX could create environments that look more realistic instead of behaving like static decoys.

We also reviewed existing deception technologies and patents related to compromised credentials, simulated communications and automated decoy generation.

From this research, we understood that simple honeypots may not be enough against advanced attackers. A more realistic environment can make it harder for an attacker or malware to identify that it is being monitored.

This supports our approach of using an **organization-specific digital twin** instead of relying only on a generic sandbox.

---

## 5. Research on MITRE ATT&CK-Based Behaviour Analysis

We also studied how malware behaviour can be mapped to the MITRE ATT&CK framework.

Some of the important works we reviewed were:

- **“Malware2ATT&CK: A Sophisticated Model for Mapping Malware to ATT&CK Techniques”** – This work maps observed malware behaviour to ATT&CK techniques. It helped us understand how automated behaviour classification can be used.

- **“Malware of Dynamic Behavior and Attack Patterns Using ATT&CK Framework”** – This research uses an LLM to map observed behaviour to ATT&CK techniques. We studied it to understand how machine learning can support malware analysis.

- **“MITRE ATT&CK: State of the Art and Way Forward”** – We used this as a broader reference for current research related to ATT&CK.

- **“Mind the Gap: On Bridging the Semantic Gap between ML and Information Security”** – This introduced the Malware Behavior Catalog as a more detailed way of describing malware behaviour.

- **“A Multi-Label Visualisation Approach for Malware Behaviour Analysis”** – We studied this to understand how different analysis methods can be combined to explain malware behaviour.

We also looked at **Joe Sandbox Cloud** as a reference for existing malware analysis systems.

This research helped us plan the analysis stage of O-NYX. We want the system to identify observed behaviour, map it to known attack techniques and use this information to understand the level of risk.

---

## 6. Research on Ransomware Detection and Recovery

We also studied existing approaches for ransomware detection and recovery.

We reviewed patents covering:

- Snapshot-based ransomware detection and recovery.
- Automated storage rollback.
- Virtualized storage snapshots.
- Detection based on unusual file and I/O activity.
- Faster investigation of snapshots for recovery.

We also studied **“Towards Low-Latency and Adaptive Ransomware Detection Using Contrastive Learning.”** This work combines ransomware detection with lightweight backup and recovery methods.

This research helped us understand that detecting ransomware is only one part of the problem. A useful system should also be able to **contain the attack and recover the affected environment**.

Based on this, we considered an automatic rollback or **“time-machine”** feature as part of the O-NYX design.

---

## 7. Research on Threat Intelligence Sharing

For the post-exploitation stage, we studied how cyber threat intelligence can be shared using **STIX and TAXII**.

We reviewed research on cyber threat intelligence sharing and how STIX/TAXII compares with formats such as IODEF and OpenIOC.

We also studied how STIX/TAXII can be used for IoT threat intelligence and how security platforms can use these feeds.

This helped us understand how the information collected by O-NYX could be converted into a standard format and shared with other security tools.

Our goal is to make the results of malware analysis useful beyond just the individual analysis environment.

---

## 8. Other Research We Are Following

We are also following recent work that may be useful for the future development of O-NYX.

One paper we studied, **“The Rhythm of Execution: Unveiling the Impact of Sandbox Execution Time on Cyber Threat Intelligence Data,”** looks at how execution time affects the information collected during malware analysis. We found this relevant because we are considering complete execution behaviour rather than relying only on short observations.

We also looked at research related to passive cyber attribution. This is relevant to our approach because O-NYX is intended to focus on **observed behaviour and TTP similarity** rather than making strong claims about the exact identity of an attacker.

We are also keeping track of commercial research and patents related to cyber deception, sandbox security and ransomware protection. This will help us compare our approach with existing systems as our project develops.

---

# Overall Research Progress

Through this literature and patent study, we focused on three main questions:

1. **Why can traditional sandbox environments fail?**  
   We found that malware can identify virtualized or controlled environments and change its behaviour.

2. **Can a more realistic environment make analysis harder to detect?**  
   Our research on digital twins and cyber deception suggests that making the environment more realistic can help reduce this problem.

3. **How can malware behaviour be monitored without exposing the monitoring mechanism?**  
   Our study of hypervisor-level introspection showed us that monitoring can be performed from outside the virtual machine.

Based on our current research, we identified a gap in combining these ideas into one system. Our work on **O-NYX** is focused on exploring an organization-specific digital twin, covert hypervisor-level monitoring, behavioural classification, adaptive containment and threat-intelligence sharing as parts of one malware analysis workflow.

Our next step is to use the findings from this research to refine the O-NYX architecture and compare our approach with existing sandbox, deception, VMI and ransomware-response systems.