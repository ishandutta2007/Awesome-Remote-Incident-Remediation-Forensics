# Awesome-Remote-Incident-Remediation-Forensics

# Top Remote Incident Remediation & Forensics Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Live Response, Forensic Collection & Self-Hosted DFIR Platforms*  
**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Remote Incident Remediation & Forensics**. These tools enable security teams to remotely investigate compromised endpoints, collect forensic evidence, and remediate threats—without physically touching the device or reimaging the system.

**Examples** include CrowdStrike Falcon Real Time Response (RTR), Tanium Threat Response, Cybereason Live Response, Microsoft Defender Live Response, Carbon Black Live Response, SentinelOne Remote Shell, Binalyze AIR, Velociraptor, Cado Security, and GRR Rapid Response (the category leaders).

**Open-source emphasis**: Remote Incident Remediation & Forensics is a domain where open-source tooling is **mature and production-proven at the DFIR layer**, with clear leaders for different philosophies. **Velociraptor** is the standout—an AGPL-licensed DFIR platform originally written by Mike Cohen (also behind GRR), now stewarded by Rapid7, with VQL-based artifact collection, live response actions, and massive fleet scalability . **GRR Rapid Response** (also Mike Cohen's work) provides live forensics at scale with Fleetspeak for low-latency communication and multi-party authorization for sensitive actions . The critical caveat: **commercial platforms differentiate on integrated EDR telemetry and automated remediation**—CrowdStrike RTR can reverse harmful registry changes and execute custom scripts at scale , while Tanium provides real-time endpoint data without pre-ingestion . Open-source tools excel at forensic depth and flexibility but require you to supply the detection layer and operational expertise.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[CrowdStrike Falcon Real Time Response (RTR)](https://www.crowdstrike.com/)**  
  Remote remediation within the Falcon platform; execute built-in commands or custom scripts on managed endpoints, isolate compromised hosts, remove malicious files, and **reverse harmful registry changes** . Integrates with Falcon Fusion SOAR for no-code automated remediation at scale . **Best for CrowdStrike customers** wanting integrated investigation and remediation without reimaging.

- **[Tanium Threat Response](https://www.tanium.com/)**  
  Live endpoint intelligence and remediation grounded in **real-time endpoint data, not a pre-ingested copy** . Features continuous system activity recording for forensic and historical analysis, threat intelligence integration (TAXII, iSight, VirusTotal), endpoint isolation, and **Tanium Automate playbook steps** for quarantine . **Best for organizations wanting live forensic context without deploying another agent**—Tanium's single lightweight agent handles both IT management and security .

- **[Cybereason Live Response](https://www.cybereason.com/)**  
  Point-and-click remediation from the console; isolate machines, kill processes, and remove persistence mechanisms with a single click . The **Malop** (malicious operation) visual interface organizes attack data into an interactive graph for rapid investigation . **Best for teams wanting intuitive, one-click remediation** without complex queries.

- **[Microsoft Defender Live Response](https://learn.microsoft.com/defender-endpoint/live-response)**  
  Remote shell into devices with a library of commands: `getfile` (up to 3GB), `putfile` (300MB Windows, 10MB other platforms), `collect` forensic package, `isolate`/`release` network, `remediate` entities, `scan` antivirus, and `run` PowerShell scripts . **Best for Microsoft Defender for Endpoint customers** wanting integrated live response without additional tooling.

- **[Carbon Black Live Response](https://techdocs.broadcom.com/)**  
  Remote shell with up to 100 simultaneous sessions, 250 commands per session, and multi-user attachment to the same session . Works on devices in bypass or quarantine mode. Sessions timeout after 15 minutes of inactivity . **Best for Carbon Black Cloud customers** needing collaborative investigation sessions.

- **[SentinelOne Remote Shell](https://www.sentinelone.com/)**  
  **Native shell capabilities**—anything you can do with PowerShell or Bash, you can do remotely . Full auditing of every session, dedicated password encryption per session, and two-factor authentication required before access . **Best for teams wanting unrestricted native shell access** with full audit trails.

- **[Binalyze AIR](https://binalyze.ai/)**  
  Forensic-grade investigation platform collecting **1000+ types of evidence** across platforms . Features DRONE triage/prioritization, concurrent YARA/osquery/Sigma scanning, collaborative investigation timelines, and **differential analysis** comparing current forensic state against previous points in time . **Best for organizations wanting deep forensic collection** with automated triage and timeline collaboration.

- **[Cado Security](https://docs.cadosecurity.com/)**  
  Cloud-native forensic acquisition via **Cado Host** binaries for Windows, Linux, and macOS; collects files, open files, process/network metadata, and optional memory; uploads to S3/Azure/GCS or local storage for air-gapped environments . Integrates with AWS EC2 via SSM, Kubernetes (ECS, EKS, GKE, AKS), and XDR systems including CrowdStrike, Defender, and SentinelOne . **Best for cloud and container forensic acquisition** with automated cloud storage upload.

- **[GRR Rapid Response](https://www.grr-response.com/)**  
  **Open-source** (listed here for its commercial support option) live forensics at scale; search files by path/regex/content, list processes and network connections, collect forensic artifacts, run osquery, and perform live memory analysis with YARA . Fleetspeak provides low-latency communication; multi-party authorization available for sensitive actions .

## Open-Source GitHub Projects

### Full DFIR Platforms (Velociraptor, GRR)

- **[Velociraptor](https://github.com/Velocidex/velociraptor)**  
  The **most capable open-source DFIR platform** available (AGPL-3.0, ~2.5k GitHub stars, Rapid7-stewarded since 2021) . Features: **VQL (Velociraptor Query Language)** for custom queries; **artifact-based collection** (version-controlled YAML+VQL, community library via Rapid7's velociraptor-artifacts repo); **live response actions** (kill process, isolate host, dump memory); **VFS (Virtual File System)** for interactive endpoint inspection with paged tables (250k files in <90 seconds); **hunts across thousands of hosts** with offline endpoint pickup; **client-side tracing** for debugging hung collections . **Best for large-scale hunting and forensic collection** across Windows, Linux, and macOS—but requires operational expertise and infrastructure.

- **[GRR Rapid Response](https://github.com/google/grr)**  
  Open-source **live forensics at scale** (Apache 2.0) originally developed by Google; now at v4.0.0.0 (December 2025) . Features: **Fleetspeak** for low-latency client-server communication; **multi-party authorization** for sensitive actions; **osquery integration**; **live process memory analysis** with YARA; **predefined ForensicArtifacts** recipes for reproducible evidence collection; **scheduled hunts** across fleets including offline endpoints . **Best for organizations wanting Google-backed, scalable live forensics** with strong security controls—but heavier to deploy than Velociraptor.

### Forensic Acquisition & Triage

- **[Cado Host](https://github.com/cado-security/cado-host)**  
  Open-source **forensic artifact acquisition tool** (Cado Security's acquisition binaries). Collects files from key forensic locations, open files, process/network metadata, and optional memory; stores in a zip file uploadable to S3/Azure/GCS or local storage for air-gapped environments . Supports Windows 7+, Linux (Debian 9+, Ubuntu 16.04+, RHEL 7+), and macOS 14+ (ARM) . **Best for cloud-native forensic triage**—but it is an acquisition tool, not a full investigation platform.

### Additional Strong Open-Source Options

- **Rapid7 Velociraptor Artifacts** — Community-maintained artifact library for Velociraptor; contains reusable VQL collectors for registry hives, MFT, browser history, Sysmon events, and more . **Not a standalone tool**—it extends Velociraptor's built-in artifact set.
- **KAPE (Kroll Artifact Parser and Extractor)** — Not open-source (free for commercial use), but widely used alongside open-source DFIR tools for targeted artifact collection; often compared to Velociraptor's "Acquire Triage" capability .

**Frameworks for building custom systems**: For **large-scale hunting and artifact collection**, Velociraptor provides the most complete open-source foundation with VQL flexibility and community artifacts . For **Google-backed scalable live forensics** with strong security controls, GRR Rapid Response . For **cloud-native forensic acquisition**, Cado Host . No open-source project matches the **integrated EDR telemetry and automated remediation** of CrowdStrike RTR (registry reversal)  or Tanium's live data without pre-ingestion —those are commercial advantages that require the underlying EDR agent and platform.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Remote remediation and forensic platforms handling endpoint data must comply with organizational security policies and privacy regulations; **live response access is highly privileged**—SentinelOne requires policy enablement, per-session encryption passwords, and 2FA before access . Ensure proper authorization and audit trails.
- **Open-source remote forensics is mature for collection and investigation but requires you to supply the detection layer**—Velociraptor and GRR provide production-grade DFIR capabilities , but they do not include the EDR detection telemetry that triggers investigations. Commercial platforms like CrowdStrike and Tanium integrate detection and response in a single agent —open-source requires pairing a DFIR tool with a separate detection system.
- Verify license terms for commercial use; Velociraptor uses AGPL-3.0 , GRR uses Apache 2.0 , and Cado Host is open-source (check repository) .

---

**Made for incident responders, DFIR analysts, and security teams building remote investigation capabilities.**  
Let's make remote incident remediation and forensics more open, but with clear eyes about the detection integration gap that commercial platforms still fill.
