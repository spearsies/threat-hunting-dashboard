# Usage Examples - Cybersecurity Threat Hunting Dashboard

This document provides practical examples of how to use the Cybersecurity Threat Hunting Dashboard for common threat hunting scenarios.

## Table of Contents

1. [Quick Start Examples](#quick-start-examples)
2. [Threat Hunting Scenarios](#threat-hunting-scenarios)
3. [IOC Management Examples](#ioc-management-examples)
4. [Detection Rule Examples](#detection-rule-examples)
5. [Evidence Documentation Examples](#evidence-documentation-examples)
6. [Query Library Examples](#query-library-examples)
7. [Team Collaboration Examples](#team-collaboration-examples)
8. [Reporting Examples](#reporting-examples)

## Quick Start Examples

### Example 1: Your First Threat Hunt

**Scenario**: Hunting for signs of credential dumping activity

1. **Create the Hunt**
   - Navigate to Threat Hunts database
   - Click "+ New"
   - Fill in details:
     - **Name**: "Credential Dumping Detection - Q4 2024"
     - **Priority**: High
     - **Threat Type**: Credential Theft
     - **Systems Analyzed**: Endpoints, Servers
     - **Start Date**: Today
     - **Team Members**: Assign your team
     - **Status**: Planning

2. **Find Relevant Queries**
   - Open Query Library
   - Filter by MITRE Technique: "T1003 - Credential Access"
   - Review existing queries
   - Adapt to your environment

3. **Execute and Document**
   - Run queries in your SIEM
   - Document findings in "Findings Summary"
   - Create IOC entries for any suspicious indicators
   - Link IOCs to the hunt

4. **Create Detection Rule**
   - If you find a valid threat pattern
   - Create a new Detection Rule
   - Link it to the hunt
   - Set status to "Testing"

5. **Close the Hunt**
   - Update "Recommended Actions"
   - Change status to "Completed"
   - Share findings with team

### Example 2: Tracking a Known IOC

**Scenario**: You receive an IOC from a threat intelligence feed

1. **Add the IOC**
   - Navigate to IOC Collection
   - Click "+ New"
   - Fill in details:
     - **Name**: "Emotet C2 Server IP"
     - **IOC Type**: IP Address
     - **IOC Value**: 192.0.2.100
     - **Status**: New
     - **Severity**: High
     - **Confidence Level**: High
     - **Malware Family**: Emotet
     - **Source**: "ACME Threat Intel Feed"
     - **Date Discovered**: Today

2. **Investigate**
   - Check logs for the IP
   - Update status to "Investigating"
   - Document findings in a linked Evidence page

3. **Take Action**
   - Block the IP in firewall
   - Create detection rule
   - Update status to "Confirmed" or "Mitigated"

## Threat Hunting Scenarios

### Scenario 1: Hunting for Ransomware Activity

**Objective**: Proactively search for early signs of ransomware deployment

**Setup:**

1. **Create Threat Hunt**
   ```
   Name: "Pre-Ransomware Activity Hunt - Week 45"
   Priority: Critical
   Threat Type: Ransomware
   Systems Analyzed: Endpoints, Servers, Network Devices
   Status: Planning
   ```

2. **Define Hunt Hypothesis**
   In "Findings Summary":
   ```
   Hypothesis: Attackers often perform reconnaissance and lateral 
   movement before deploying ransomware. Looking for:
   - Unusual SMB traffic patterns
   - Mass file access/enumeration
   - Suspicious scheduled tasks
   - Unusual credential usage
   - Tools associated with ransomware delivery
   ```

3. **Select Queries**
   From Query Library, use:
   - SMB lateral movement detection
   - Mass file access detection
   - Scheduled task creation monitoring
   - Credential usage anomalies

4. **Execute Hunt**
   - Run queries daily for 1 week
   - Document findings in Evidence Repository
   - Create IOCs for suspicious indicators
   - Update status to "In Progress"

5. **Analysis Phase**
   - Change status to "Analysis"
   - Correlate findings across systems
   - Identify false positives
   - Document patterns observed

6. **Create Detections**
   - For validated patterns, create Detection Rules
   - Link rules to the hunt
   - Set rules to "Testing" status

7. **Report and Close**
   - Recommended Actions:
     ```
     1. Deploy new detection rules to production
     2. Add confirmed IOCs to blocklist
     3. Review backup procedures
     4. Update incident response runbooks
     5. Schedule follow-up hunt in 30 days
     ```
   - Change status to "Completed"

### Scenario 2: Hunting for Insider Threats

**Objective**: Detect unusual data access or exfiltration by authorized users

**Hunt Process:**

1. **Create Hunt**
   ```
   Name: "Insider Threat - Unusual Data Access Q4"
   Priority: Medium
   Threat Type: Insider Threat, Data Exfiltration
   Systems Analyzed: Databases, Cloud Infrastructure, Web Applications
   ```

2. **Define Indicators**
   - Access to sensitive data outside normal hours
   - Large data downloads
   - Use of USB devices or cloud storage
   - Access from unusual locations
   - Privilege escalation attempts

3. **Gather Evidence**
   For each finding, create Evidence Repository entry:
   ```
   Threat Name: "Employee X - After Hours Database Access"
   Severity: Medium
   Attack Vector: Insider Threat
   Affected Systems: Databases
   Indicators of Compromise: 
   - User: jsmith@company.com
   - IP: 10.0.5.23
   - Database: CustomerDB
   - Time: 02:30 AM
   - Records Accessed: 50,000+
   Status: In Progress
   ```

4. **Document Actions**
   - Coordinate with HR if needed
   - Interview the user
   - Review access logs
   - Update Evidence with findings

### Scenario 3: APT Hunt Based on Threat Intelligence

**Objective**: Hunt for indicators of a specific APT group

**Hunt Strategy:**

1. **Create Hunt**
   ```
   Name: "APT29 Infrastructure Hunt - November 2024"
   Priority: Critical
   Threat Type: APT
   ```

2. **Gather Intelligence**
   - Collect known APT29 IOCs
   - Add each to IOC Collection:
     ```
     IOC Name: "APT29 C2 Domain - Campaign XYZ"
     IOC Type: Domain
     IOC Value: malicious-domain.com
     Threat Actor: APT29 (Cozy Bear)
     Campaign: "Operation XYZ"
     Confidence Level: Very High
     Source: "FBI Flash Alert"
     ```

3. **Hunt Execution**
   - Search logs for all IOCs
   - Look for TTPs associated with APT29
   - Check for similar infrastructure patterns

4. **Create Custom Queries**
   Add to Query Library:
   ```
   Query Name: "APT29 - Cobalt Strike Beacon Detection"
   Platform: Splunk
   Threat Type: APT, Command & Control
   MITRE Techniques: T1071 - C2 Protocol
   Query Syntax:
   index=proxy 
   | search url="*/api/v1/*" method=POST
   | stats count by src_ip, url, user_agent
   | where count > 50
   ```

## IOC Management Examples

### Example 1: IOC Triage Workflow

**Daily IOC Review Process:**

1. **New IOCs View**
   - Filter: Status = "New"
   - Review each IOC
   - Validate against threat intelligence
   - Update confidence levels

2. **Prioritization**
   - Critical IOCs → Immediate action
   - High IOCs → Investigate within 24h
   - Medium → Add to hunt list
   - Low → Monitor

3. **Investigation**
   ```
   IOC: suspicious-domain.net
   Status: New → Investigating
   
   Actions:
   1. Check DNS logs
   2. Search proxy logs
   3. Query threat intel platforms
   4. Document findings
   
   Results:
   - Found 3 internal hosts contacting domain
   - Domain registered yesterday
   - Associated with Qakbot malware
   
   Decision: Status → Confirmed
   Create Evidence entries for affected hosts
   ```

### Example 2: IOC Lifecycle Management

**Monthly IOC Cleanup:**

1. **Review Mitigated IOCs**
   - Filter: Status = "Mitigated", Date < 90 days ago
   - Verify blocks are still in place
   - Check for any new activity
   - Archive if no longer relevant: Status → "Archived"

2. **False Positive Review**
   - Filter: Status = "False Positive"
   - Review classification
   - Update confidence levels
   - Document lessons learned

3. **IOC Enrichment**
   - Add missing campaign information
   - Link related IOCs
   - Update threat actor attribution
   - Add external references

## Detection Rule Examples

### Example 1: Creating a Detection Rule

**Scenario**: Create a rule for detecting PowerShell download cradles

```
Rule Name: "PowerShell Download Cradle Detection"
Status: Draft
Severity: High
Description: 
Detects PowerShell commands commonly used to download and execute
malicious code from the internet.

Rule Logic:
(process_name="powershell.exe" OR process_name="pwsh.exe")
AND (
  command_line="*DownloadString*" OR
  command_line="*DownloadFile*" OR
  command_line="*Invoke-WebRequest*" OR
  command_line="*iwr *" OR
  command_line="*wget *" OR
  command_line="*curl *"
)
AND command_line="*http*"

MITRE Techniques:
- T1059 - Command & Scripting Interpreter
- T1105 - Ingress Tool Transfer

Data Sources: EDR, Windows Event Logs

Implementation Date: [To be set after testing]

Reference URL: https://attack.mitre.org/techniques/T1059/001/
```

**Testing Process:**
1. Status: Draft → Testing
2. Deploy to test environment
3. Validate with known good/bad samples
4. Tune to reduce false positives
5. Document tuning in rule
6. Status: Testing → Production

### Example 2: Rule Tuning

**Original Rule** (Too many false positives):
```
Rule Name: "Suspicious Scheduled Task Creation"
Rule Logic: 
event_id=4698 AND task_name!="Microsoft\\*"
False Positive Rate: High (>30%)
```

**Tuned Rule**:
```
Rule Name: "Suspicious Scheduled Task Creation - Tuned"
Rule Logic:
event_id=4698 
AND task_name!="Microsoft\\*"
AND task_name!="GoogleUpdate*"
AND task_name!="Adobe*"
AND action!="C:\\Program Files\\*"
AND NOT user="SYSTEM"

False Positive Rate: Low (1-5%)

Tuning Notes:
- Excluded common legitimate tasks
- Added Program Files path whitelist
- Excluded SYSTEM user (regular maintenance)
- Tested over 30 days in production
```

## Evidence Documentation Examples

### Example 1: Documenting a Security Incident

```
Threat Name: "Phishing Campaign - Employee Credentials Compromised"

Date Detected: 2024-11-05
Status: In Progress
Severity: High

Affected Systems:
- Workstations (3 endpoints)
- Web Applications (Email system)

Threat Actor: Unknown (likely Financially Motivated)

Attack Vector: Phishing

MITRE ATT&CK Techniques:
- T1566 - Phishing
- T1078 - Valid Accounts
- T1087 - Account Discovery

Indicators of Compromise:
- Phishing email from: admin@company-security.net (spoofed)
- Malicious URL: hxxp://secure-login-verify[.]com/auth
- 3 employees clicked link and entered credentials
- Subsequent unusual login from IP: 45.67.89.123 (Russia)

Evidence Links:
- Email samples: [Link to secure storage]
- Network logs: [Link to SIEM investigation]
- Screenshots: [Link to documentation]

Assigned To: John Doe (Security Analyst)

Remediation Notes:
1. Reset passwords for affected accounts
2. Enabled MFA for all accounts
3. Blocked malicious domain at proxy
4. Created detection rule for similar phishing attempts
5. Scheduled security awareness training
6. Monitoring affected accounts for 30 days

Next Steps:
- Continue monitoring
- Review email gateway rules
- Update phishing detection rules
```

### Example 2: Linking Evidence to Hunts and IOCs

**Workflow:**

1. **Create Evidence Entry**
   ```
   Threat Name: "Suspicious PowerShell Execution on CORP-WKS-142"
   ```

2. **Link to Threat Hunt**
   - Add relation to "Credential Dumping Detection - Q4 2024"
   - This evidence supports the ongoing hunt

3. **Create Related IOCs**
   - Extract IOCs from the evidence
   - Add to IOC Collection
   - Link back to evidence entry

4. **Create Detection Rule**
   - Based on the pattern observed
   - Link to evidence as reference
   - Link to the hunt

**Result**: Complete audit trail from hunt → evidence → IOCs → rules

## Query Library Examples

### Example 1: Building a Query Collection

**For Splunk Users:**

```
Query Name: "Failed Login Attempts - Brute Force Detection"
Platform: Splunk
Threat Type: Credential Theft, Initial Access
MITRE Techniques: T1110 - Brute Force

Description:
Detects multiple failed login attempts from a single source,
indicating possible brute force attack.

Query Syntax:
index=windows EventCode=4625
| stats count by src_ip, user
| where count > 10
| table src_ip, user, count
| sort -count

False Positive Rate: Low (1-5%)
Last Tested: 2024-11-05
Response Playbook: [Link to incident response plan]

Notes:
- Threshold of 10 failed attempts may need tuning
- Consider time window (default: last 24 hours)
- Exclude service accounts if generating noise
```

### Example 2: Query Testing and Validation

**Testing Process:**

1. **Create Test Query**
   ```
   Query Name: "Lateral Movement - PSExec Usage"
   Status: Draft (in notes)
   ```

2. **Test with Known Data**
   - Run against test data
   - Verify it catches known incidents
   - Check for false positives

3. **Document Results**
   ```
   Last Tested: 2024-11-05
   Test Results:
   - Detected 15/15 known PSExec executions
   - 2 false positives (legitimate admin tools)
   - Tuned to exclude admin subnet
   - Re-tested: 0 false positives
   False Positive Rate: Very Low (<1%)
   ```

4. **Add to Library**
   - Move from draft to official library
   - Share with team
   - Add to relevant hunts

## Team Collaboration Examples

### Example 1: Daily Standup Workflow

**Morning Review:**

1. **Each Analyst Reviews**
   - Open "My Hunts" view (filter: Team Members = me)
   - Check Evidence assigned to me
   - Review new IOCs (Status = New)

2. **Team Discussion**
   - Review Active Hunts board
   - Discuss priorities
   - Assign new tasks
   - Update hunt statuses

3. **Documentation**
   - Each analyst updates their hunt status
   - Adds comments on findings
   - Links evidence and IOCs

### Example 2: Knowledge Sharing

**Weekly Query Review:**

1. **Query Submission**
   - Analysts add successful queries to library
   - Tag with relevant techniques
   - Note false positive rates

2. **Peer Review**
   - Team reviews new queries
   - Tests in their environments
   - Provides feedback via comments
   - Improves documentation

3. **Library Curation**
   - Archive outdated queries
   - Update platform versions
   - Maintain best practices

## Reporting Examples

### Example 1: Executive Summary

**Monthly Threat Hunting Report:**

Create a new page with rollups:

```
# Threat Hunting Summary - October 2024

## Key Metrics
- Active Hunts: [Rollup count]
- Completed Hunts: [Rollup count]
- New IOCs: [Rollup count]
- Critical Findings: [Filter and count]
- Detection Rules Deployed: [Rollup count]

## Top Threats
[Linked database filtered by Severity=Critical]

## Completed Investigations
[Linked database filtered by Status=Completed, This Month]

## Recommended Actions
[Aggregated from hunt recommendations]
```

### Example 2: Metrics Dashboard

**Create KPI Page:**

1. **Hunt Velocity**
   - Hunts completed per month
   - Average hunt duration
   - Hunts by priority

2. **Detection Coverage**
   - Rules by MITRE technique
   - Coverage gaps
   - Rule effectiveness

3. **IOC Intelligence**
   - IOCs by type
   - IOCs by threat actor
   - Confirmation rate

4. **Team Performance**
   - Hunts per analyst
   - Evidence documented
   - Queries contributed

---

## Best Practice Templates

### Hunt Template

When creating a new hunt, use this structure:

```
Name: [Descriptive name with date/quarter]
Priority: [Based on threat and impact]
Threat Type: [Primary threats being hunted]
Systems Analyzed: [Specific systems or all]
Start Date: [Hunt start]
End Date: [Expected completion]
Team Members: [Assigned analysts]

Findings Summary:
## Hypothesis
[What you're looking for and why]

## Methodology
[Queries and approaches used]

## Findings
[What was discovered]

## Analysis
[Interpretation of findings]

Recommended Actions:
1. [Immediate actions]
2. [Short-term improvements]
3. [Long-term enhancements]
```

### Evidence Template

```
Threat Name: [Clear, descriptive name]
Date Detected: [When first observed]
Status: New
Severity: [Impact assessment]
Affected Systems: [Specific systems]
Threat Actor: [If known or suspected]
Attack Vector: [Initial access method]

Indicators of Compromise:
- [Specific indicators]
- [With context]

Evidence Links:
- [Logs]
- [Screenshots]
- [Reports]

Remediation Notes:
[Initial assessment and immediate actions]
```

---

**Version**: 1.0.0  
**Last Updated**: November 2025  

For more examples and community contributions, visit the GitHub repository.
