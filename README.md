# Awesome SOC

Curated tools & resources to make your day-to-day SOC job easier.

A hand-picked collection of tools, platforms, frameworks, and resources for Security Operations Center (SOC) analysts, SOC leads, detection engineers, and blue team defenders. Whether you're triaging alerts, hunting threats, writing detection rules, building automation playbooks, or managing incident response — this list has something for you.

## Contents

- [SIEM & Log Management](#siem--log-management)
- [EDR / XDR / Endpoint](#edr--xdr--endpoint)
- [SOAR & Automation](#soar--automation)
- [Threat Intelligence Platforms](#threat-intelligence-platforms)
- [OSINT](#osint)
- [Detection Engineering](#detection-engineering)
- [DFIR & Forensics](#dfir--forensics)
- [Threat Hunting](#threat-hunting)
- [Network Security Monitoring & IDS](#network-security-monitoring--ids)
- [Malware Analysis & Sandboxes](#malware-analysis--sandboxes)
- [Cloud Security](#cloud-security)
- [Email Security & Phishing](#email-security--phishing)
- [Purple Team & Adversary Emulation](#purple-team--adversary-emulation)
- [Case Management & Ticketing](#case-management--ticketing)
- [SOC Toolkits & Distributions](#soc-toolkits--distributions)
- [People](#people)
- [Blogs & Newsletters](#blogs--newsletters)
- [Certifications](#certifications)
- [Learning & Training](#learning--training)
- [Books & Reading](#books--reading)

## SIEM & Log Management

- [Azure Sentinel (Microsoft Sentinel)](https://azure.microsoft.com/en-us/products/microsoft-sentinel) — Cloud-native SIEM and SOAR platform with built-in AI and threat intelligence integration
- [Cribl Stream](https://cribl.io/) — Observability pipeline for routing, reducing, and enriching log data before it reaches your SIEM
- [Datadog Cloud SIEM](https://www.datadoghq.com/product/cloud-siem/) — Cloud SIEM with out-of-the-box detection rules and log correlation
- [Elastic Security](https://www.elastic.co/security) — SIEM and endpoint security built on the Elastic Stack with detections, timelines, and case management
- [Flume](https://flume.apache.org/) — Distributed log ingestion and aggregation service for streaming data into HDFS and SIEMs
- [Gravwell](https://www.gravwell.io/) — Structure-on-read data platform for high-volume security log analytics and binary index-free searching
- [Graylog](https://www.graylog.org/) — Open-source log management platform with powerful search, dashboards, and alerting capabilities
- [Grafana Loki](https://grafana.com/oss/loki/) — Horizontally scalable, highly available log aggregation system inspired by Prometheus
- [IBM QRadar](https://www.ibm.com/qradar) — Enterprise SIEM with integrated threat intelligence, UEBA, and automated investigation
- [LogRhythm](https://logrhythm.com/) — SIEM platform combining log management, network and endpoint monitoring, and SOAR capabilities
- [Logstash](https://www.elastic.co/logstash) — Server-side data processing pipeline that ingests, transforms, and ships logs to Elasticsearch
- [Matano](https://www.matano.dev/) — Open-source cloud-native security lake platform built on AWS with Sigma rule support and real-time detection
- [OpenSearch](https://opensearch.org/) — Open-source search and analytics engine (fork of Elasticsearch) for building custom SIEM stacks
- [Security Onion](https://securityonionsolutions.com/) — Open-source platform combining NSM, SIEM, and log management with hundreds of tools pre-integrated
- [Sigma](https://github.com/SigmaHQ/sigma) — Generic and open signature format for SIEM systems enabling cross-platform detection rule sharing
- [Splunk](https://www.splunk.com/) — Market-leading data-to-everything platform for log management, SIEM, and security analytics
- [Sumo Logic](https://www.sumologic.com/solutions/cloud-siem/) — Cloud-native SIEM with continuous intelligence and real-time security analytics
- [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) — Windows system monitor that logs detailed process, network, and file activity to Windows Event Log
- [Wazuh](https://wazuh.com/) — Open-source security platform with XDR and SIEM capabilities, file integrity monitoring, and compliance checks
- [Winlogbeat](https://www.elastic.co/downloads/beats/winlogbeat) — Lightweight shipper for Windows event logs that feeds directly into Elasticsearch or Logstash

## EDR / XDR / Endpoint

- [Bitdefender GravityZone EDR](https://www.bitdefender.com/en-us/business/) — Enterprise EDR with risk analytics, incident visualization, and one-click investigation
- [Carbon Black EDR](https://www.carbonblack.com/) — Endpoint detection and response platform with continuous recording and live response (Broadcom)
- [Cortex XDR](https://www.paloaltonetworks.com/cortex/cortex-xdr) — Palo Alto's extended detection and response platform covering endpoint, network, and cloud
- [CrowdStrike Falcon](https://www.crowdstrike.com/falcon-platform/) — Cloud-native EDR/XDR platform with real-time threat detection, managed threat hunting, and full visibility
- [Elastic Defend](https://www.elastic.co/guide/en/security/current/install-endpoint.html) — Integrated EDR capabilities within Elastic Security with malware prevention and ransomware protection
- [LimaCharlie](https://www.limacharlie.io/) — Open-source cross-platform EDR with pay-as-you-go pricing, D&R rules, and cloud API
- [Microsoft Defender for Endpoint](https://www.microsoft.com/en-us/security/business/endpoint-security/microsoft-defender-endpoint) — Enterprise endpoint security platform built into Windows with EDR, ASR, and automated investigation
- [osquery](https://osquery.io/) — SQL-powered operating system instrumentation, monitoring, and analytics framework from Meta
- [SentinelOne Singularity](https://www.sentinelone.com/) — AI-powered autonomous endpoint protection platform with EDR, XDR, and identity protection
- [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) — Windows sysinternals tool that generates detailed endpoint telemetry for EDR/SIEM consumption
- [Tanium](https://www.tanium.com/) — Converged endpoint management and real-time endpoint visibility for detection and response
- [Velociraptor](https://docs.velociraptor.app/) — Open-source endpoint visibility, collection, and forensic analysis agent with powerful VQL query language
- [Wazuh](https://wazuh.com/) — Open-source XDR platform with FIM, vulnerability detection, and security configuration assessment

## SOAR & Automation

- [Chronicle SOAR](https://chronicle.security/products/soar/) — Google's SOAR platform with case management, playbooks, and integrated threat intelligence
- [Cortex XSOAR](https://www.paloaltonetworks.com/cortex/cortex-xsoar) — Palo Alto's comprehensive SOAR platform with thousands of pre-built integrations and playbooks
- [DFIR-IRIS](https://dfir-iris.org/) — Open-source collaborative incident response platform with case management and automation
- [n8n](https://n8n.io/) — Fair-code workflow automation platform for building SOC automation pipelines with 400+ integrations
- [Node-RED](https://nodered.org/) — Low-code flow-based programming tool for wiring together security APIs, webhooks, and automation tasks
- [Shuffle](https://shuffler.io/) — Open-source SOAR platform with drag-and-drop playbook builder, app integrations, and API workflows
- [Splunk SOAR (Phantom)](https://www.splunk.com/en_us/software/splunk-security-orchestration-and-automation.html) — Splunk's SOAR platform for automating security operations, incident response, and threat management
- [Swimlane](https://swimlane.com/) — Low-code security automation platform for building and managing SOAR playbooks at scale
- [Tines](https://www.tines.com/) — No-code automation platform for SOC teams to build workflows, enrich alerts, and automate repetitive IR tasks
- [Torq](https://torq.io/) — Hyperautomation platform with pre-built security automation workflows and slack-native incident response

## Threat Intelligence Platforms

- [Abuse.ch Feodo Tracker](https://feodotracker.abuse.ch/) — Tracks C2 servers for Dridex, Emotet, TrickBot, and other malware families with real-time blocklists
- [Abuse.ch MalwareBazaar](https://bazaar.abuse.ch/) — Database of malware samples with metadata, YARA signatures, and IOCs shared by the community
- [Abuse.ch ThreatFox](https://threatfox.abuse.ch/) — Platform for sharing IOCs including IPs, domains, and URLs with API access and integration
- [Abuse.ch URLhaus](https://urlhaus.abuse.ch/) — Database of malicious URLs used for malware distribution with submissions and API querying
- [AlienVault OTX](https://otx.alienvault.com/) — Open Threat Exchange with community-submitted threat intelligence, pulses, and IOC feeds
- [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/) — Web-based tool for annotating and exploring MITRE ATT&CK matrices for threat analysis and coverage mapping
- [Censys](https://censys.io/) — Internet intelligence platform for discovering and monitoring internet-facing assets, certificates, and exposures
- [Cisco Talos](https://talosintelligence.com/) — Threat intelligence from Cisco with reputation data, vulnerability research, and threat analysis
- [GreyNoise](https://greynoise.io/) — Noise-filtered threat intelligence that distinguishes targeted attacks from internet background noise
- [Malpedia](https://malpedia.caad.fkie.fraunhofer.de/) — Encyclopedia of malware with YARA rules, IOCs, and family descriptions curated by Fraunhofer FKIE
- [MISP](https://www.misp-project.org/) — Open-source threat intelligence and sharing platform for storing, correlating, and sharing IOCs
- [MITRE ATT&CK](https://attack.mitre.org/) — Globally accessible knowledge base of adversary tactics, techniques, and procedures based on real-world observations
- [OpenCTI](https://www.opencti.io/) — Open-source cyber threat intelligence platform for managing, sharing, and operationalizing threat data
- [Pulsedive](https://pulsedive.com/) — Free threat intelligence platform for searching, scanning, and enriching IOCs with risk scoring
- [Recorded Future](https://www.recordedfuture.com/) — Commercial threat intelligence platform with real-time IOC feeds, actor profiles, and risk scoring
- [Shodan](https://www.shodan.io/) — Search engine for discovering internet-connected devices, services, and vulnerabilities on exposed hosts
- [Talos Reputation Center](https://talosintelligence.com/reputation) — IP, domain, and URL reputation lookup tool for quick threat assessment
- [ThreatConnect](https://threatconnect.com/) — Commercial threat intelligence platform with aggregation, analysis, playbooks, and dissemination workflows
- [VirusTotal](https://www.virustotal.com/) — Multi-engine file and URL scanner for analyzing suspicious files, domains, IPs, and URLs with community comments
- [YARA](https://virustotal.github.io/yara/) — Pattern-matching Swiss Army knife for creating custom malware family detection signatures

## OSINT

- [Amass](https://github.com/owasp-amass/amass) — OWASP's network mapping and external asset discovery tool using DNS enumeration and OSINT techniques
- [Censys](https://censys.io/) — Internet-wide asset discovery and intelligence platform for mapping an organization's external attack surface
- [EmailRep](https://emailrep.io/) — Free API for email reputation scoring and OSINT enrichment with social profile and breach intelligence
- [haveibeenpwned](https://haveibeenpwned.com/) — Checks whether an email address or domain has been compromised in known data breaches
- [Maltego](https://www.maltego.com/) — Link analysis and data visualization tool for mapping relationships between people, domains, networks, and threats
- [Recon-ng](https://github.com/lanmaster53/recon-ng) — Full-featured reconnaissance framework with independent modules for OSINT gathering and reporting
- [Shodan](https://www.shodan.io/) — Search engine for discovering internet-facing devices, industrial control systems, and exposed services
- [SpiderFoot](https://www.spiderfoot.net/) — Open-source intelligence automation tool for querying 200+ data sources and correlating OSINT findings
- [theHarvester](https://github.com/laramies/theHarvester) — OSINT tool for gathering email addresses, subdomains, IPs, and URLs from public sources
- [urlscan.io](https://urlscan.io/) — Website scanner for analyzing URLs, capturing screenshots, inspecting DOM, and identifying phishing infrastructure

## Detection Engineering

- [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) — Library of simple, portable tests mapped to MITRE ATT&CK that every security team can execute
- [Attack Range](https://github.com/splunk/attack_range) — Splunk's detection development platform that builds small-scale lab environments on AWS/Azure
- [Chainsaw](https://github.com/WithSecureLabs/chainsaw) — Rapidly search and hunt through Windows event logs with Sigma rule matching and forensic artefacts
- [DetectionLab](https://github.com/clong/DetectionLab) — Automated lab environment bringing detection engineering and logging visibility into a single Vagrant deployment
- [Elastic Detection Rules](https://github.com/elastic/detection-rules) — Elastic's public detection rule repository with rule logic, tests, and TOML-based configuration
- [Hayabusa](https://github.com/Yamato-Security/hayabusa) — Windows event log fast forensics timeline generator and threat hunting tool with Sigma detection engine
- [Mordor](https://github.com/OTRF/mordor) — Pre-recorded security event datasets from simulated adversarial techniques for detection engineering
- [Prelude Operator](https://docs.prelude.org/) — Autonomous red-team platform for continuous security testing with adversary emulation capabilities
- [Sigma](https://github.com/SigmaHQ/sigma) — Generic open signature format that allows you to write detection rules once and convert them to any SIEM query
- [Sigma CLI](https://github.com/SigmaHQ/sigma-cli) — Command-line tool for converting Sigma rules to various SIEM backends (Splunk, Elastic, Sentinel, etc.)
- [pySigma](https://github.com/SigmaHQ/pySigma) — Python library for parsing and converting Sigma rules, the engine behind Sigma CLI
- [Splunk Attack Range](https://github.com/splunk/attack_range) — Detection development platform for building and testing detections in a realistic lab
- [Splunk Security Content](https://github.com/splunk/security_content) — Splunk's open repository of detection content: detections, response tasks, and investigation guides
- [Stratus Red Team](https://github.com/DataDog/stratus-red-team) — Granular adversary emulation for the cloud, with continuous testing of cloud-native detection controls
- [Uncoder.io](https://uncoder.io/) — Online detection rule converter and IDE supporting Sigma, KQL, SPL, YARA-L, and other query languages
- [Vectr](https://github.com/SecurityRiskAdvisors/VECTR) — Purple team engagement tracking and metrics platform for measuring detection coverage over time

## DFIR & Forensics

- [Autopsy](https://www.autopsy.com/) — Digital forensics GUI platform for The Sleuth Kit, with timeline analysis, keyword search, and reporting
- [Chainsaw](https://github.com/WithSecureLabs/chainsaw) — Rapid forensic triage tool that hunts Windows event logs using Sigma rules and maps findings to MITRE ATT&CK
- [CyberChef](https://gchq.github.io/CyberChef/) — Web-based "Cyber Swiss Army Knife" for decoding, decrypting, and analysing data on the fly
- [DumpIt](https://www.magnetforensics.com/resources/magnet-dumpit-for-windows/) — Lightweight tool for capturing Windows memory dumps for volatile forensic analysis
- [Eric Zimmerman's Tools](https://ericzimmerman.github.io/) — Suite of Windows forensic tools (Registry Explorer, Timeline Explorer, AmcacheParser, etc.)
- [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) — Free forensic imaging tool for disk, memory, and file acquisition with preview capabilities
- [Hayabusa](https://github.com/Yamato-Security/hayabusa) — Windows event log fast forensics timeline generator with Sigma-based threat detection
- [KAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kape) — Rapid targeted forensic triage tool for collecting the most forensically relevant files on a live system
- [Magnet RESPONSE](https://www.magnetforensics.com/products/magnet-response/) — Remote evidence acquisition for triaging multiple endpoints in incident response scenarios
- [Plaso](https://github.com/log2timeline/plaso) — Super timeline creation framework for Windows, Linux, and macOS forensic artefacts
- [Redline](https://fireeye.market/apps/211364) — Mandiant's free endpoint investigation tool for memory and file analysis with IOC-based scanning
- [Rekall](https://github.com/google/rekall) — Memory forensics framework from Google with advanced analysis and acquisition capabilities
- [The Sleuth Kit](https://www.sleuthkit.org/) — Open-source collection of command-line digital forensics tools and C library for analysing disk images
- [Timeline Explorer](https://ericzimmerman.github.io/) — Windows GUI tool for viewing, filtering, and analysing forensic timelines from CSV and Excel exports
- [Velociraptor](https://docs.velociraptor.app/) — Advanced endpoint visibility and forensic collection using VQL for live forensics and artifact collection
- [Volatility 3](https://github.com/volatilityfoundation/volatility3) — Advanced memory forensics framework for extracting artefacts, process listings, and malware traces from RAM dumps
- [Zimmerman's Registry Explorer](https://ericzimmerman.github.io/) — Comprehensive Windows registry forensics viewer with shellbag parsing, deleted data recovery, and bookmarking

## Threat Hunting

- [APT-Hunter](https://github.com/ahmedkhlief/APT-Hunter) — Threat hunting tool for Windows event logs that detects APT activity patterns and suspicious behaviours
- [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/) — Layer-based visualisation tool for mapping and tracking threat hunting coverage against MITRE ATT&CK
- [Chainsaw](https://github.com/WithSecureLabs/chainsaw) — Fast Windows event log hunting tool that matches forensic artefacts and Sigma rules against ATT&CK techniques
- [DeepBlueCLI](https://github.com/sans-blue-team/DeepBlueCLI) — PowerShell module that parses Windows event logs for threat hunting via command-line detections
- [Elastic Security](https://www.elastic.co/security) — Built-in threat hunting timelines, correlation rules, and search language for proactive detection hunting
- [Hayabusa](https://github.com/Yamato-Security/hayabusa) — Windows event log fast forensics timeline generator with built-in threat hunting rules
- [Kibana Timelines](https://www.elastic.co/guide/en/security/current/timelines-ui.html) — Elastic's interactive timeline for visualising and investigating security events during threat hunts
- [MISP](https://www.misp-project.org/) — Correlate threat intelligence against internal telemetry for proactive IOCs-based hunting
- [Mordor](https://github.com/OTRF/mordor) — Pre-recorded adversarial simulation datasets for testing and validating threat hunting hypotheses
- [Security Onion](https://securityonionsolutions.com/) — NSM distribution with hunt interface, built-in dashboards, and hundreds of tools for threat hunting
- [Splunk](https://www.splunk.com/) — SPL queries for hunting across indexed data with dashboards, risk-based alerting, and statistical analysis
- [ThreatHunting.net](https://www.threathunting.net/) — Community knowledge base of threat hunting blog posts, tools, and techniques

## Network Security Monitoring & IDS

- [Arkime (Moloch)](https://arkime.com/) — Large-scale packet capture and search system with web UI for full-packet indexing and analysis
- [Brim](https://www.brimdata.io/) — Desktop app for efficient pcap exploration and Zeek log analysis with a Zui-based GUI
- [Corelight](https://corelight.com/) — Commercial network detection and response platform built on Zeek with pre-built intelligence and analytics
- [Kapacitor](https://www.influxdata.com/time-series-platform/kapacitor/) — Real-time streaming data processing engine for alerting and anomaly detection on network metrics
- [nDPI](https://www.ntop.org/products/deep-packet-inspection/ndpi/) — Open-source deep packet inspection library for application protocol and service classification
- [NetworkMiner](https://www.netresec.com/?page=NetworkMiner) — Network forensic analysis tool that parses pcap files and reconstructs files, certificates, and credentials
- [Security Onion](https://securityonionsolutions.com/) — Full NSM distribution with Zeek, Suricata, Snort, Wazuh, Elasticsearch, and Kibana integrated
- [Snort](https://www.snort.org/) — Open-source network intrusion detection and prevention system with rule-based traffic analysis
- [Stenographer](https://github.com/google/stenographer) — Google's packet capture system for full-packet-capture with rapid disk-based pcap indexing
- [Suricata](https://suricata.io/) — High-performance open-source IDS/IPS and NSM engine with protocol detection, file extraction, and TLS logging
- [TShark](https://www.wireshark.org/docs/man-pages/tshark.html) — Command-line version of Wireshark for pcap analysis, filtering, and field extraction in automation
- [Wireshark](https://www.wireshark.org/) — Industry-standard network protocol analyser for deep inspection of pcap captures at the packet level
- [Zeek (formerly Bro)](https://zeek.org/) — Powerful network security monitor that generates high-fidelity transaction logs, files, and application-layer metadata
- [Zui](https://github.com/brimdata/zui) — Desktop and web GUI for exploring Zeek logs and pcaps with a columnar search interface

## Malware Analysis & Sandboxes

- [ANY.RUN](https://any.run/) — Interactive cloud malware sandbox with real-time process monitoring, network analysis, and MITRE ATT&CK mapping
- [CAPE Sandbox](https://github.com/kevoreilly/CAPEv2) — Open-source automated malware analysis system with deep behavioural analysis and payload extraction
- [Cuckoo Sandbox](https://cuckoosandbox.org/) — Leading open-source automated malware analysis system with extensive behavioural logging
- [CyberChef](https://gchq.github.io/CyberChef/) — Browser-based data analysis tool for decoding, deobfuscating, and dissecting malicious payloads
- [DRAKVUF](https://github.com/CERT-Polska/drakvuf-sandbox) — Black-box binary analysis system using virtual machine introspection to trace malware execution
- [Flare VM](https://github.com/mandiant/flare-vm) — Windows-based virtual machine distribution with pre-configured malware analysis and reverse engineering tools
- [Ghidra](https://ghidra-sre.org/) — NSA's open-source software reverse engineering framework with disassembler, decompiler, and scripting
- [Hybrid Analysis](https://www.hybrid-analysis.com/) — Free malware analysis sandbox powered by Falcon sandbox technology with detailed reports
- [IDA Pro](https://hex-rays.com/ida-pro/) — State-of-the-art interactive disassembler and debugger for binary reverse engineering
- [Intezer Analyze](https://analyze.intezer.com/) — Cloud-based malware analysis platform using genetic code analysis to detect code reuse and attribution
- [Joe Sandbox](https://www.joesandbox.com/) — Deep malware analysis platform for automated and interactive analysis across Windows, macOS, Android, and Linux
- [oletools](https://github.com/decalage2/oletools) — Python tools for analysing malicious Microsoft OLE and OOXML documents (macros, DDE, embedded objects)
- [REMnux](https://remnux.org/) — Linux distribution for reverse-engineering and analysing malware with hundreds of pre-installed tools
- [Triage](https://tria.ge/) — Cloud-based automated malware analysis sandbox with behavioural extraction, config decryption, and family identification
- [VirusTotal](https://www.virustotal.com/) — Multi-engine scanner for files, URLs, and domains with interactive behavioural reports and community comments
- [x64dbg](https://x64dbg.com/) — Open-source debugger for Windows executables with plugin support and graphical interface

## Cloud Security

- [BloodHound CE (Cloud)](https://github.com/BloodHoundAD/BloodHound) — Attack path mapping for cloud Active Directory to identify privilege escalation risks
- [Checkov](https://www.checkov.io/) — Static analysis for Infrastructure-as-Code scanning for misconfigurations in Terraform, CloudFormation, Kubernetes, and more
- [CloudSploit](https://www.aquasec.com/products/cloudsploit/) — Cloud security and configuration monitoring for AWS, Azure, and GCP across hundreds of security checks
- [CloudMapper](https://github.com/duo-labs/cloudmapper) — Duo's tool for visualising AWS environments and generating security audit reports
- [Falco](https://falco.org/) — Cloud-native runtime security for detecting anomalous behaviour in containers, Kubernetes, and cloud workloads
- [GuardDuty](https://aws.amazon.com/guardduty/) — AWS native threat detection service that monitors for malicious activity and anomalous API behaviour
- [kube-bench](https://github.com/aquasecurity/kube-bench) — Checks whether Kubernetes is deployed securely by running CIS Kubernetes Benchmark tests
- [kube-hunter](https://github.com/aquasecurity/kube-hunter) — Active vulnerability scanning tool for finding security weaknesses in Kubernetes clusters
- [Pacu](https://github.com/RhinoSecurityLabs/pacu) — AWS exploitation framework and penetration testing toolkit for testing cloud security posture
- [Prowler](https://github.com/prowler-cloud/prowler) — Open-source cloud security assessment tool for AWS, Azure, and GCP with hundreds of checks (CIS, GDPR, PCI, etc.)
- [ScoutSuite](https://github.com/nccgroup/ScoutSuite) — Multi-cloud security auditing tool from NCC Group for AWS, Azure, GCP, Alibaba, and Oracle Cloud
- [Stratus Red Team](https://github.com/DataDog/stratus-red-team) — Adversary emulation for cloud, testing detection controls against cloud-native attack techniques
- [Trivy](https://github.com/aquasecurity/trivy) — Comprehensive scanner for vulnerabilities in containers, IaC misconfigurations, and secrets in source code

## Email Security & Phishing

- [EmailRep](https://emailrep.io/) — API for assessing email address risk through OSINT, social profiles, and breach data correlation
- [GoPhish](https://getgophish.com/) — Open-source phishing framework for running simulated phishing campaigns and security awareness tests
- [haveibeenpwned](https://haveibeenpwned.com/) — Breach notification service to check if email addresses or domains have been compromised in data breaches
- [MxToolbox](https://mxtoolbox.com/) — Online diagnostics suite for DNS, SPF, DKIM, DMARC records, and email deliverability analysis
- [PhishStats](https://phishstats.info/) — Real-time phishing statistics and feed tracking active phishing sites with IP and domain data
- [PhishTool](https://www.phishtool.com/) — Community email phishing analysis platform with header inspection, attachment sandboxing, and IOC extraction
- [SpamAssassin](https://spamassassin.apache.org/) — Apache's open-source email filtering platform using header analysis, body patterns, and Bayesian filtering
- [urlscan.io](https://urlscan.io/) — Website scanner for analysing phishing URLs, capturing full page screenshots, and inspecting redirect chains

## Purple Team & Adversary Emulation

- [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) — Library of testable, MITRE ATT&CK-mapped atomic tests for validating detection coverage
- [Caldera](https://github.com/mitre/caldera) — MITRE's scalable automated adversary emulation system for running autonomous breach simulations
- [Cobalt Strike](https://www.cobaltstrike.com/) — Adversary simulation and red team operations platform for testing detection and response capabilities
- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) — Open-source (GPLv3) autonomous AI penetration-testing CLI with 50 specialist agents and 140+ offensive tools over MCP; runs on a local or cloud LLM, useful for validating detection via adversary emulation
- [Infection Monkey](https://www.akamai.com/infectionmonkey) — Akamai's open-source breach and attack simulation tool for testing lateral movement and propagation
- [Metasploit Framework](https://www.metasploit.com/) — Industry-standard penetration testing and exploit development framework for testing defence controls
- [Prelude Operator](https://docs.prelude.org/) — Autonomous agent-based adversary emulation platform for continuous security validation
- [PurpleSharp](https://github.com/mvelazc0/PurpleSharp) — C# adversary simulation tool that executes ATT&CK techniques natively on Windows AD environments
- [Red Team Automation (RTA)](https://github.com/endgameinc/RTA) — Endgame's collection of scripts for testing detection of common adversary techniques
- [SCYTHE](https://scythe.io/) — Purple team platform for campaign-based adversary emulation and detection gap analysis
- [Stratus Red Team](https://github.com/DataDog/stratus-red-team) — Granular cloud adversary emulation tool for testing cloud-native detection controls
- [Vectr](https://github.com/SecurityRiskAdvisors/VECTR) — Purple team tracking platform for measuring detection coverage, metrics, and progress over time

## Case Management & Ticketing

- [Cyber Triage](https://www.cybertriage.com/) — Automated incident response software for endpoint forensic triage and case tracking
- [DFIR-IRIS](https://dfir-iris.org/) — Open-source collaborative incident response platform with case management, timeline, and customer portal
- [Fast Incident Response (FIR)](https://github.com/certsocietegenerale/FIR) — Open-source incident response and case management platform built by CERT Société Générale
- [Jira Service Management](https://www.atlassian.com/software/jira/service-management) — Enterprise IT service management with customizable security incident workflows and automation
- [Request Tracker for Incident Response (RTIR)](https://bestpractical.com/rtir) — Incident response and case management system built on Request Tracker for managing incidents
- [TheHive](https://thehive-project.org/) — Scalable, open-source security incident response platform with case, alert, and task management
- [Timesketch](https://timesketch.org/) — Open-source collaborative forensic timeline analysis and case management web application

## SOC Toolkits & Distributions

- [FLARE VM](https://github.com/mandiant/flare-vm) — Windows-based malware analysis, reverse engineering, and forensic VM by Mandiant
- [Kali Linux](https://www.kali.org/) — Debian-based Linux distribution designed for digital forensics, penetration testing, and security research
- [Parrot OS](https://www.parrotsec.org/) — Linux distribution with tools for security, forensics, software development, and privacy
- [REMnux](https://remnux.org/) — Linux toolkit for malware analysis with pre-configured tools for static and dynamic analysis
- [SANS SIFT Workstation](https://www.sans.org/tools/sift-workstation/) — Ubuntu-based distribution for incident response and digital forensics by the SANS Institute
- [Security Onion](https://securityonionsolutions.com/) — Full NSM, SIEM, and threat hunting platform with Elastic, Zeek, Suricata, and Wazuh integrated
- [Tsurugi Linux](https://tsurugi-linux.org/) — Japanese Linux distribution focused on digital forensics, incident response, and malware analysis
- [Win-KeX](https://www.kali.org/docs/wsl/win-kex/) — Kali Linux in WSL2 with a GUI desktop for Windows environments

## People

Well-known practitioners, researchers, and educators worth following in the SOC / blue team space.

- [Anton Chuvakin](https://x.com/anton_chuvakin) — Former Gartner VP; SIEM and log management pioneer, and one of the most influential voices on SOC analytics and measurement
- [Carlos Perez](https://github.com/darkoperator) — Long-time threat hunter, detection engineer, and PowerShell security expert
- [Chris Crowley](https://www.sans.org/profiles/christopher-crowley) — SANS Senior Instructor, SOC consultant, and author of the SOC-Class blue team course
- [David Bianco](https://github.com/davidbianco) — Detection engineer best known for the Pyramid of Pain, a foundational model for SOC and intel teams
- [Florian Roth](https://github.com/Neo23x0) — Detection engineer behind Sigma, high-quality YARA rules, and the THOR scanner
- [Jake Williams](https://www.renditioninfosec.com/) — Incident responder and EDR expert with a sharp, no-nonsense take on detection and response
- [John Strand](https://github.com/strandjs) — Founder of Black Hills Information Security, blue team advocate, and prolific speaker on SOC operations
- [Lesley Carhart](https://tisiphone.net/) — DFIR veteran (Dragos) and outspoken voice on incident response, threat hunting, and analyst wellbeing
- [Mauricio Velazco](https://github.com/mvelazc0) — Cloud detection engineer behind Stratus Red Team, focused on AWS/Azure attack detection
- [Olaf Hartong](https://github.com/olafhartong) — Threat hunter and Sigma contributor known for Sysmon and EventLog tooling
- [Richard Bejtlich](https://taosecurity.blogspot.com/) — Author of *The Practice of Network Security Monitoring*; former CSO and Mandiant executive
- [Rob van Os](https://x.com/RobvanOs) — SOC operations expert and educator focused on blue teaming and security monitoring
- [Roberto Rodriguez](https://github.com/Cyb3rWard0g) — Threat hunter and OTRF founder; creator of the Mordor datasets

## Blogs & Newsletters

Follow these for threat research, detection content, and hands-on SOC analysis.

- [BleepingComputer](https://www.bleepingcomputer.com/) — Daily security news and threat coverage widely used by SOC teams for quick context
- [CrowdStrike Blog](https://www.crowdstrike.com/blog/) — Threat research and adversary reports from CrowdStrike's intel and hunting teams
- [Dark Reading](https://www.darkreading.com/) — Security news and analysis with a strong practitioner angle
- [Detection at Scale](https://detectionatscale.com/) — Practical writing on building, testing, and maintaining detection programs
- [Elastic Security Labs](https://www.elastic.co/security-labs/) — In-depth malware analysis, detection research, and YARA/Sigma releases
- [Krebs on Security](https://krebsonsecurity.com/) — Investigative security journalism covering breaches, scams, and cybercrime infrastructure
- [Mandiant Blog](https://www.mandiant.com/resources/blog) — Threat intel reports, APT analyses, and IR lessons from Mandiant's frontline
- [Microsoft Security Blog](https://www.microsoft.com/en-us/security/blog/) — Microsoft threat research, detections, and security product updates
- [SANS Internet Storm Center](https://isc.sans.org/) — Daily diaries and handler podcasts on current threats; often first to report new attacks
- [Splunk Security Blog](https://www.splunk.com/en_us/blog/security.html) — Detection content, use cases, and security analytics guidance from Splunk
- [TaoSecurity](https://taosecurity.blogspot.com/) — Richard Bejtlich's long-running blog on NSM, network defence, and security history
- [The DFIR Report](https://thedfirreport.com/) — Detailed write-ups of real intrusions with IOCs and detection guidance; a must-read
- [The Hacker News](https://thehackernews.com/) — Popular infosec news site covering vulnerabilities, breaches, and security research
- [Threat Hunter Playbook](https://threathunterplaybook.com/) — Open-source threat hunting procedures and analytics built around ATT&CK
- [Unit 42](https://unit42.paloaltonetworks.com/) — Palo Alto's threat research team publishing APT reports and campaign analyses
- [VX-Underground](https://vx-underground.org/) — Collection of malware samples, source code, and research papers

## Certifications

SOC-relevant certifications, from entry-level analyst to management and cloud.

- [AWS Certified Security – Specialty](https://aws.amazon.com/certification/certified-security-specialty/) — Cloud security cert validating AWS-specific detection, response, and IAM skills
- [CEH (Certified Ethical Hacker)](https://www.eccouncil.org/train-certify/certified-ethical-hacker-ceh-certification/) — Entry-level offensive cert useful for understanding attacker techniques from the defender side
- [CISM (Certified Information Security Manager)](https://www.isaca.org/credentialing/cism) — Management-focused cert covering governance, risk, and incident management
- [CISSP](https://www.isc2.org/certifications/cissp) — Industry-standard security management and engineering certification
- [CompTIA CASP+](https://www.comptia.org/certifications/comptia-advanced-security-practitioner) — Advanced practitioner cert for security operations and architecture
- [CompTIA CySA+](https://www.comptia.org/certifications/cybersecurity-analyst) — Analyst-level cert focused on monitoring, detection, and response; a direct SOC fit
- [CompTIA Security+](https://www.comptia.org/certifications/security) — Entry-level foundation cert covering core security concepts
- [GIAC GDAT](https://www.giac.org/certifications/defending-advanced-threats-gdat/) — Blue team cert focused on defending against advanced persistent threats
- [GIAC GCFA](https://www.giac.org/certifications/certified-forensic-analyst-gcfa/) — Advanced digital forensics and incident response certification
- [GIAC GCIA](https://www.giac.org/certifications/certified-intrusion-analyst-gcia/) — Network intrusion analysis and packet-level detection certification
- [GIAC GCIH](https://www.giac.org/certifications/certified-incident-handler-gcih/) — Incident handling and response cert with hands-on labs
- [GIAC GCTI](https://www.giac.org/certifications/cyber-threat-intelligence-gcti/) — Threat intelligence analysis and CTI tradecraft certification
- [GIAC GSEC](https://www.giac.org/certifications/security-essentials-gsec/) — Entry-level GIAC cert on information security fundamentals
- [Microsoft Azure Security Engineer (AZ-500)](https://learn.microsoft.com/en-us/credentials/certifications/azure-security-engineer/) — Azure-focused cert covering identity, platform protection, and security operations
- [OSCP](https://www.offsec.com/courses/pen-200/) — Hands-on penetration testing cert that sharpens understanding of attack paths
- [Security Blue Team BTL1](https://www.securityblue.team/why-btl1) — SOC-specific cert with hands-on blue team labs covering SIEM, DFIR, and phishing analysis

## Learning & Training

- [AttackIQ Academy](https://www.academy.attackiq.com/) — Free adversary emulation and MITRE ATT&CK courses with certification
- [Blue Team Labs Online](https://blueteamlabs.online/) — Hands-on SOC analyst and blue-team training with investigation labs and skills tracking
- [BTLO (Blue Team Labs Online)](https://blueteamlabs.online/) — Scenario-based blue team training platform with forensic investigations, SOC triage, and threat hunting
- [CyberDefenders](https://cyberdefenders.org/) — Blue team and DFIR CTF platform with realistic forensic images and security challenges
- [DetectionLab](https://github.com/clong/DetectionLab) — Self-contained SOC lab environment for learning detection engineering and log analysis
- [LetsDefend](https://letsdefend.io/) — Blue team training platform with simulated SOC environment, real alerts, and playbooks
- [Malware-Traffic-Analysis.net](https://www.malware-traffic-analysis.net/) — Packet capture exercises for learning network traffic analysis and incident response
- [MITRE ATT&CK](https://attack.mitre.org/) — Comprehensive knowledge base for studying adversary tactics, techniques, and real-world procedures
- [RangeForce](https://www.rangeforce.com/) — Interactive cyber defence training platform with team exercises and individual upskilling paths
- [SANS Cheatsheets](https://www.sans.org/blog/the-ultimate-list-of-sans-cheat-sheets/) — Collection of SANS reference posters, cheat sheets, and quick-reference guides for DFIR and security
- [Splunk Boss of the SOC (BOTS)](https://github.com/splunk/botsv1) — Hands-on Splunk workshops using realistic security datasets for training SOC analysts
- [TryHackMe](https://tryhackme.com/) — Browser-based cybersecurity training with SOC-specific learning paths and hands-on virtual labs
- [Wild West Hackin' Fest](https://www.wildwesthackinfest.com/) — Community-driven security conference and training with SOC and blue-team focused courses

## Books & Reading

- [Blue Team Field Manual (BTFM)](https://www.amazon.com/s?k=blue+team+field+manual) — Pocket reference for incident responders covering commands, checks, and quick-win triage steps (Alan White, Ben Clark)
- [Blue Team Handbook: Incident Response Edition](https://www.amazon.com/Blue-Team-Handbook-Incident-Response/dp/1500734756) — Step-by-step SOC and IR reference covering incident response lifecycle and tool usage (Don Murdoch)
- [Evading EDR](https://nostarch.com/evading-edr) — In-depth guide to how EDRs work, how attackers bypass them, and how to improve detection (Matt Hand)
- [Incident Response & Computer Forensics (3rd Edition)](https://www.mhprofessional.com/incident-response-computer-forensics-third-edition-9780071798686-usa) — Comprehensive IR reference covering forensic investigation from initial response to reporting (Luttgens, Pepe, Mandia)
- [Intelligence-Driven Incident Response](https://www.oreilly.com/library/view/intelligence-driven-incident-response/9781491935187/) — Practical approach to integrating cyber threat intelligence into incident response workflows (Scott J. Roberts, Rebekah Brown)
- [Network Security Through Data Analysis (2nd Edition)](https://www.oreilly.com/library/view/network-security-through/9781491962831/) — Building security monitoring and detection capabilities through data analysis of network logs (Michael Collins)
- [Operator Handbook: Red Team + OSINT + Blue Team](https://www.amazon.com/Operator-Handbook-Blue-Team/dp/B09GJGCRL6) — Compact reference guide with commands and tools for blue, red, and OSINT operations (Joshua Picolet)
- [Pentesting Azure Applications: The Definitive Guide to Testing and Securing Deployments](https://nostarch.com/azure) — Hands-on guide to Azure attack paths, IAM, storage, and compute hardening for defenders (Karl Fosaaen, Matt Toussaint)
- [Practical Malware Analysis](https://nostarch.com/malware) — Hands-on guide to analysing malicious software with labs covering static and dynamic techniques (Michael Sikorski, Andrew Honig)
- [Practical Packet Analysis (3rd Edition)](https://nostarch.com/packetanalysis3) — Learn Wireshark and network protocol analysis for security investigations (Chris Sanders)
- [The Hacker Playbook 3](https://www.amazon.com/s?k=the+hacker+playbook+3) — Red team techniques and methods useful for understanding attacker TTPs from a defender's perspective (Peter Kim)
- [The Practice of Network Security Monitoring](https://nostarch.com/nsm) — Foundational guide to building NSM capabilities with practical detection and analysis workflows (Richard Bejtlich)
- [The Web Application Hacker's Handbook (2nd Edition)](https://www.wiley.com/en-us/The%20Web%20Application%20Hacker%27s%20Handbook%3A%20Finding%20and%20Exploiting%20Security%20Flaws%2C%202nd%20Edition-p-9781118026472) — Comprehensive reference for understanding web attacks to improve detection and defence (Stuttard, Pinto)

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to add new tools and resources to this list.

## License

This work is licensed under the [MIT License](LICENSE).
