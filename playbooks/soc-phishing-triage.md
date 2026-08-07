# SOC Phishing Email Triage Playbook

## Objective

To provide a structured, repeatable process for SOC analysts to triage reported phishing emails, determine the threat level, extract IOCs, and initiate appropriate containment actions.

## Scope

This playbook covers:

- User-reported suspicious emails (reported via button, ticket, or forwarded email)
- Automated alerts from email security gateways (MDO, Proofpoint, Mimecast, etc.)
- Any email that triggers IOC matches from threat intelligence integrations

## Initial Triage (First 10 Minutes)

### 1. Obtain the Email

- For user-reported emails: obtain the full `.eml` or `.msg` file from the ticket, or use the "preview as raw" option in your email security gateway.
- For automated alerts: navigate to the alert and pull the full email source.
- **Do not** open attachments or click links on your analyst workstation. Use an isolated VM or sandbox.

### 2. Inspect Email Headers

- Use [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx) or paste headers into a local text editor.
- Extract and record:
  - `From` (display name and envelope sender)
  - `Return-Path`
  - `Reply-To` (if different from `From`)
  - `Message-ID`
  - Originating IP (from the first `Received` header at the bottom)
  - `Authentication-Results` (SPF, DKIM, DMARC)

### 3. Sender Spoofing Checks

- **Display name spoofing**: does the `From` display name match an internal executive or a known brand (e.g., Microsoft, DocuSign) but the actual address is from a free mail provider or lookalike domain?
- **Domain similarity**: check the sender domain for typosquatting or lookalike characters using [dnstwist](https://github.com/elceef/dnstwist) or [urlscan.io](https://urlscan.io/) domain search.
- **DMARC/SPF/DKIM results**: check the `Authentication-Results` header for `dkim=fail` and `spf=fail`. A `dmarc=fail` with `p=reject` should have been blocked by the gateway — if it wasn't, investigate the gateway configuration.
- **First external IP**: does the originating IP belong to a known mail service (e.g., Google, Outlook) or does it belong to a residential/bulletproof hosting range? Use [AbuseIPDB](https://www.abuseipdb.com/) or [GreyNoise](https://viz.greynoise.io/) to check.

### 4. URL Analysis

- Extract all URLs from the email body (including href values behind displayed text).
- **Do not click the URLs.**
- Submit each extracted URL to [VirusTotal](https://www.virustotal.com/).
- Scan with [urlscan.io](https://urlscan.io/) in private/unlisted mode to capture:
  - Screenshot of the landing page
  - Redirect chain
  - Associated domains and IPs
  - Indicators of credential phishing (fake login portal, brand impersonation)
- For shortened URLs (bit.ly, tinyurl, etc.): expand using `curl -I` or [unshorten.me](https://unshorten.me/) before scanning.
- If any URL resolves to a known phishing domain (PhishStats, URLhaus), mark the email as malicious immediately.

### 5. Attachment Analysis

- Identify all attachments. Record filenames, extensions, and sizes.
- Check the file extension against known malicious patterns:
  - Executables disguised as documents: `.pdf.exe`, `.docx.exe`, `.xlsx.exe`
  - ISO, IMG, VHD files used to bypass Mark-of-the-Web
  - Archive files with password protection (`.zip`, `.rar`, `.7z`) — high confidence phishing
  - HTML attachments with obfuscated JavaScript or embedded phishing forms
- Calculate hashes (MD5, SHA1, SHA256) of each attachment: `sha256sum attachment.ext`
- Check hashes against [VirusTotal](https://www.virustotal.com/) and [MalwareBazaar](https://bazaar.abuse.ch/).
- If the email appears malicious and you have a sandbox, detonate in a controlled environment:
  - [ANY.RUN](https://any.run/) — interactive analysis with network capture
  - [Joe Sandbox](https://www.joesandbox.com/) — automated in-depth analysis
  - [Triage](https://tria.ge/) — behavioural analysis with config extraction
- For Office documents with macros, use [oletools](https://github.com/decalage2/oletools) (`olevba`, `oleid`) to inspect macro content prior to detonation.
- For PDFs, use [pdfid](https://blog.didierstevens.com/programs/pdf-tools/) and [peepdf](https://github.com/jesparza/peepdf) to identify embedded scripts or objects.

## Decision Points

### Benign

- Sender is legitimate, authentication passes, URLs resolve to expected domains, attachments are expected file types.
- **Action**: close the ticket with a brief note confirming the email is safe. Educate the user on why the email is safe but thank them for reporting.
- **No further escalation**.

### Suspicious

- Sender is external but not overtly malicious (no known bad, but unusual context).
- Some authentication headers fail but could be misconfiguration.
- URLs not on any blocklist but the domain is newly registered.
- **Action**: escalate to Tier 2 for deeper analysis. Advise the user not to interact further. Add IOCs to the case.

### Malicious

- Confirmed phishing URL (credential harvesting page, known phishing domain, or brand impersonation).
- Malicious attachment detonated successfully in sandbox with C2 callbacks or payload execution.
- Sender is a known phishing actor or domain.
- **Action**: immediately begin containment. Notify the user, initiate credential reset if credentials were submitted. Purge the email from all mailboxes. Escalate to incident response if any post-compromise activity is detected.

## IOC Extraction

Once an email is confirmed malicious, extract and record the following IOCs:

- **URIs/URLs**: all unique URLs including redirects from [urlscan.io](https://urlscan.io/) result
- **Domains**: sender domain, phishing landing domain, redirect domains, any C2 domains from sandbox detonation
- **IP addresses**: sending MTA IP, phishing host IP, sandbox C2 IP
- **Email addresses**: sender address, Reply-To, envelope sender
- **Subject**: email subject line for mail-rule-based purging
- **Attachment hashes**: MD5, SHA1, SHA256
- **X-Mailer / User-Agent**: mail client string for correlation with other campaigns

Submit IOCs to:
- Your internal SIEM/TIP (MISP, OpenCTI)
- [MISP](https://www.misp-project.org/) instance (internal)
- [URLhaus](https://urlhaus.abuse.ch/) (malicious URLs)
- [PhishStats](https://phishstats.info/) (phishing sites)
- [VirusTotal](https://www.virustotal.com/) (hashes)

## Containment

### Email-Level Containment

1. Purge the email from all recipient mailboxes using your mail security gateway (Microsoft 365 Compliance Search & Purge, Google Vault, Proofpoint TAP, etc.).
2. Block the sender domain and email address at the email gateway.
3. Block all extracted URLs at the web proxy (if applicable) and email gateway URL rewriting.

### Credential Compromise Containment

1. If the phishing page collected credentials, force password reset for the affected user(s) **immediately**.
2. Revoke all active sessions for the user (Microsoft 365: `Revoke-AzureADUserAllRefreshToken`; Google Workspace: reset sign-in cookies).
3. Review the user's recent sign-in logs for anomalous geoip logins during the exposure window.

### Endpoint Containment

1. If an attachment was opened and detonation showed malicious behaviour, isolate the affected endpoint in your EDR:
   - CrowdStrike: "Network Contain"
   - Microsoft Defender for Endpoint: "Isolate Device"
   - SentinelOne: "Disconnect from Network"
2. Initiate a full endpoint scan and forensic evidence collection on the host.

## Eradication & Recovery

- For credential phishing: verify that no mailbox forwarding rules, OAuth app grants, or inbox rules were created post-compromise.
- For malware delivery: follow your organisation's full malware incident response playbook (re-image or clean infected hosts).
- If the phishing page is still live: submit a takedown request to the hosting provider (check WHOIS abuse contact) and the domain registrar.

## Evidence Preservation

- Save the `.eml`/`.msg` source as an attachment to the case/ticket.
- Preserve [urlscan.io](https://urlscan.io/) public scan results (share the UUID).
- Retain any sandbox analysis report links.
- If the email led to a full incident, ensure evidence is preserved according to chain-of-custody procedures.

## Lessons Learned

After closure, conduct a brief review:

- Was the email blocked by any existing controls?
- Why did the user need to report it (i.e., why did automated detection miss it)?
- Are there gaps in the email security gateway rules (missing blocklists, SPF/DKIM handling)?
- Should a new detection rule (Sigma, SIEM correlation, gateway policy) be created?
- Was the credential phishing page infrastructure also used in other campaigns (check URLscan search for similar pages)?

---

**Document Owner**: SOC Lead
**Review Cycle**: Quarterly
**Last Updated**: 2026-08-07
