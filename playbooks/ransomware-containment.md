# Ransomware Containment Playbook

## Objective

To provide a clear, rapid, and repeatable response process for SOC analysts when a ransomware alert fires. The primary goal is to contain the threat before it spreads laterally and before data exfiltration or encryption completes.

## Detection Signals

Ransomware incidents are typically identified via one or more of the following signals. When any combination fires, this playbook should be invoked **immediately**.

### EDR Alerts

- Ransomware behaviour detection (e.g., CrowdStrike "RansomwareBehaviourDetected", SentinelOne "RansomwareEncryption", Defender "Ransomware behavior detected")
- Mass file modification or rename operations in a short window
- Volume Shadow Copy deletion (`vssadmin.exe delete shadows`, `wmic shadowcopy delete`)
- Disabling of recovery tools (`bcdedit /set {default} recoveryenabled No`)
- Service tampering on security tools (stopping AV/EDR services)

### Windows Event Logs

- **Event ID 4688** (Process Creation): suspicious command-line patterns such as `net stop`, `sc stop`, `wbadmin delete`, `vssadmin delete shadows`, `bcdedit /set`, `wevtutil cl`
- **Event ID 4689** (Process Termination): unexpected termination of security agent processes
- **Event ID 4663** (File Access): rapid read-then-write access to a large number of files by a single process (volume of events is the signal)
- **Event ID 5145** (Network Share Object Access): SMB write access to a large number of files on network shares by one user

### File Extension Anomalies

- Appearance of known ransomware extensions: `.lockbit`, `.conti`, `.blackcat`, `.play`, `.hive`, `.ransom`, `<random string>`, etc.
- Creation of ransom notes in multiple directories: `README.txt`, `HOW_TO_DECRYPT.txt`, `_RESTORE_FILES_.txt`
- A large number of files with a newly appended or modified extension in a short time window

### Network Anomalies

- Outbound SMB (TCP 445) to a large number of internal hosts
- Outbound connections to known ransomware C2 IPs/domains
- Unusual volume of RDP (TCP 3389) being used for lateral movement

## Immediate Containment

The first goal is to **stop the bleeding**. Target completion: within 5 minutes of confirmation.

### Step 1: Isolate Affected Host(s)

Isolate the host(s) showing ransomware indicators at the network level using your EDR:

- **CrowdStrike Falcon**: Containment > Network Contain
- **Microsoft Defender for Endpoint**: Device page > Isolate device
- **SentinelOne**: Actions > Disconnect from Network
- **Carbon Black**: Take Action > Isolate Sensor
- **Velociraptor**: Create a hunt with an `networking.ifconfig` check, then implement iptables isolation

If EDR isolation is not available, manually isolate:
- Disable the switch port (switch CLI or network management tool)
- Remove the VM's network adapter (vSphere / Hyper-V / cloud console)
- Block the host IP at the firewall

### Step 2: Disable Compromised User Account(s)

1. Identify the user account associated with the ransomware process (check EDR process tree, event 4688, or security event 4624 on the affected host).
2. **Immediately** disable or revoke all sessions for the compromised account:
   - **Active Directory**: `Disable-ADAccount -Identity <username>` — and force reset password
   - **Microsoft 365**: `Revoke-AzureADUserAllRefreshToken -ObjectId <user>` and block sign-in
   - **Entra ID / Azure AD**: revoke sessions from the user's "Authentication methods" page
3. Check for other active sessions from the same user across the environment (4624 events in SIEM) and force-disconnect.

### Step 3: Block C2 and Anomalous Traffic at Perimeter

1. Extract any identified C2 IP addresses and domains from:
   - EDR alert details (network connections during ransomware execution)
   - Network traffic logs (Zeek/Suricata logs, flow data)
   - DNS query logs for domains queried around the time of detection
2. Block IOCs:
   - Add outbound deny rules at the edge firewall for C2 IPs
   - Add domains to the web proxy blocklist
   - Add DNS sinkhole entries for identified domains at the DNS resolver level
3. Block SMB (TCP 445) and RDP (TCP 3389) outbound from the affected subnet if lateral movement is suspected and containment is not yet achieved.

### Step 4: Contain Network Shares and Storage

1. Identify network shares the compromised user had write access to (review your share audit logs or check the user's group memberships).
2. Temporarily set all shares the user had write access to as **read-only** until triage is complete.
3. If cloud storage (S3, Azure Blob, GCS) is involved, revoke write access for the compromised principal.

### Step 5: Suspend Backups (When Appropriate)

If the backup system is on the same network and accessible to the compromised account, scripts on the affected host may attempt to delete or encrypt backups. As a temporary measure:
- Suspend backup jobs until containment is confirmed
- Verify backup integrity from a **clean** host before restoration

## Eradication

### Step 6: Identify the Root Cause

1. From the EDR process tree on the affected host, identify the initial access vector (parent process chain).
2. Common entry points to investigate:
   - Phishing attachment opened by the user
   - RDP brute-force (correlate event 4625 logon failures then 4624 success)
   - Exploitation of an unpatched internet-facing service
   - Credential reuse from a prior breach
3. Correlate with vulnerability management data to determine if a known CVE was exploited.

### Step 7: Rebuild Affected Systems

- **DO NOT** attempt to "clean" a ransomware-infected system. Re-image from known-good media.
- For physical hosts: wipe and re-image using your standard provisioning process.
- For VMs: delete and redeploy from a known-good template or backup snapshot confirmed to be pre-infection.
- Restore data from **clean** backups only. Verify backup integrity before restoration.

### Step 8: Reset All Credentials

- Reset the password for the compromised user account.
- If the account had privileged access: reset the KRBTGT password (twice) if domain compromise is suspected.
- If the account had any service accounts or managed identities under its scope, rotate all associated keys and secrets.
- If cloud access keys were potentially exposed, revoke and rotate them immediately.

## Recovery

### Step 9: Restore from Clean Backups

- Identify the last known-good backup prior to the initial compromise timestamp.
- Scan backup files for indicators before restoration.
- Restore data to the rebuilt host in phases (critical services first).

### Step 10: Gradually Reconnect

- Do not reconnect rebuilt hosts to the production network all at once.
- Bring hosts online in a monitoring-only VLAN first. Monitor for 24 hours for any residual beaconing or anomalous behaviour.
- Restore share access gradually after confirming each host is clean.
- Remove temporary firewall and proxy blocks only after confirming no further C2 activity.

## Evidence Preservation

Preserve evidence **before** eradication (destination must not be a network share accessible from the affected host):

### 1. Memory Acquisition (First Priority)

Memory is most volatile. Acquire **before** rebooting the host:

- **Windows**: use [DumpIt](https://www.magnetforensics.com/resources/magnet-dumpit-for-windows/), [KAPE](https://www.kroll.com/en/services/cyber-risk/incident-response-litigation-support/kape) with the `!WMemory` target, or `winpmem`
- **Linux**: `avml`, `LiME`, or `fmem`
- Save the memory image to an external USB drive or an isolated forensic collection server, not a network share.

### 2. Disk Image (Second Priority)

- Acquire a full forensic disk image using [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager), `dd`, or a triage target with KAPE.
- Ensure the image is stored on forensically clean media.

### 3. Triage Collection

- Run KAPE triage on the system (targets: `!SANS_Triage`, `!BasicCollection`) to collect event logs, registry hives, prefetch, amcache, scheduled tasks, and other forensic artefacts.
- Collect specific logs from the SIEM: all events from the affected host for the 7 days preceding detection plus the full detection day.

### 4. Network Evidence

- Preserve relevant pcaps (full packet capture) from the time window if your NSM infrastructure supports it (Arkime / Stenographer).
- Export Zeek/Suricata connection logs, DNS logs, and HTTP logs for the affected host IP.

## Communication & Escalation

### Who to Notify

| When | Who | Action |
|------|-----|--------|
| Immediately upon confirmation | SOC Lead / Incident Manager | Declare a security incident |
| Within 15 minutes of confirmation | IT Operations / Infrastructure Lead | Coordinate share lockdown and network isolation |
| Within 30 minutes | CISO / Security Management | Brief on scope, containment status, and next steps |
| Within 60 minutes | Legal / Privacy Counsel | Assess data breach notification obligations |
| Within 2 hours | Internal Communications / Executive Team | Initial situation report |
| If data exfiltration is confirmed | External IR Retainer / Cyber Insurance Carrier | Activate retainer and start claims process |

### Escalation Triggers

Declare a **major security incident** when any of the following are true:

- Ransomware has affected more than 3 hosts
- A domain controller or Tier-0 asset is affected
- Data exfiltration is confirmed (outbound network volume spike, DLP alerts, cloud-to-cloud transfer anomalies)
- The threat actor is an identified ransomware group (e.g., LockBit, ALPHV/BlackCat, Clop, Play, Akira)
- The ransomware note contains credible threats to leak data
- Encrypted data includes regulated data (PII, PHI, PCI) triggering mandatory disclosure obligations

### When to Call It a Day

- All affected hosts have been rebuilt and are clean
- No further C2 traffic, lateral movement, or encryption activity observed for a full 72-hour monitoring period
- All IOCs have been operationalised into detection rules and block policies
- Root cause has been identified and remediated
- Backup integrity has been verified
- Post-incident report has been drafted and a lessons-learned session scheduled

---

**Document Owner**: SOC Lead
**Review Cycle**: Quarterly
**Last Updated**: 2026-08-07
