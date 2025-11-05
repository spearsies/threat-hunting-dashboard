# 📐 Template Structure Documentation

This document provides a comprehensive overview of the Cybersecurity Threat Hunting Dashboard template structure, including all databases, properties, views, and relationships.

## Table of Contents

1. [Dashboard Overview](#dashboard-overview)
2. [Database Schemas](#database-schemas)
3. [View Configurations](#view-configurations)
4. [Database Relationships](#database-relationships)
5. [Property Reference](#property-reference)
6. [MITRE ATT&CK Mapping](#mitre-attck-mapping)

## Dashboard Overview

### Main Components

```
🛡️ Cybersecurity Threat Hunting Dashboard
│
├── Operational Guidelines (Callout)
├── Threat Priority Matrix (Callout)
│
├── 📊 Threat Hunts Database
├── 📚 IOC Collection Database
├── 🚷 Detection Rules Database
├── 🛡️ Threat Hunting Evidence Repository
└── 🛡️ Threat Hunting Query Library
```

### Page Layout

The dashboard uses a two-column layout for the callout sections:

**Left Column:**
- Operational Guidelines (Red background)
  - Update hunt status in real-time
  - Document all findings with evidence
  - Link related incidents
  - Maintain chain of custody

**Right Column:**
- Threat Priority Matrix (Green background)
  - Severity levels with response times
  - Score ranges for prioritization

## Database Schemas

### 1. Threat Hunts Database

**Purpose**: Central repository for managing threat hunting campaigns and operations.

#### Properties

| Property Name | Type | Required | Options/Values |
|--------------|------|----------|----------------|
| Threat Hunt Name | Title | Yes | Free text |
| Status | Status | Yes | Planning, In Progress, Analysis, Completed, Closed |
| Priority | Select | No | Critical, High, Medium, Low |
| Threat Type | Multi-select | No | Malware, Ransomware, APT, Insider Threat, Data Exfiltration, Phishing, DDoS, Zero-Day, Credential Theft |
| Systems Analyzed | Multi-select | No | Endpoints, Servers, Network Devices, Cloud Infrastructure, IoT Devices, Databases, Mobile Devices, Web Applications |
| Start Date | Date | No | Date picker |
| End Date | Date | No | Date picker |
| Team Members | Person | No | Workspace members |
| Findings Summary | Text | No | Long text |
| Recommended Actions | Text | No | Long text |

#### Status Groups

- **To Do**: Planning
- **In Progress**: In Progress, Analysis
- **Complete**: Completed, Closed

#### Views

1. **All Threat Hunts** (Table)
   - Sort: Start Date (descending)
   - Shows: All properties
   - Purpose: Comprehensive view of all hunts

2. **Active Hunts** (Board)
   - Group by: Status
   - Shows: Threat Hunt Name, Priority, Threat Type
   - Purpose: Kanban board for active hunt management

3. **Hunt Calendar** (Calendar)
   - Calendar by: Start Date
   - Shows: Threat Hunt Name
   - Purpose: Timeline visualization of hunts

4. **By Threat Type** (Table)
   - Group by: Threat Type
   - Sort: Priority (descending)
   - Shows: Key properties
   - Purpose: Categorize hunts by threat type

5. **Timeline View** (Timeline)
   - Timeline by: Start Date to End Date
   - Shows: Threat Hunt Name
   - Purpose: Gantt-style project view

### 2. IOC Collection Database

**Purpose**: Centralized repository for tracking indicators of compromise.

#### Properties

| Property Name | Type | Required | Options/Values |
|--------------|------|----------|----------------|
| IOC Name | Title | Yes | Free text |
| IOC Type | Select | No | IP Address, Domain, Hash, URL, Email, File, Registry, Process, Network, Other |
| IOC Value | Text | Yes | Actual indicator value |
| Status | Status | Yes | New, Investigating, Confirmed, Mitigated, False Positive, Archived |
| Severity | Select | No | Critical, High, Medium, Low, Informational |
| Confidence Level | Select | No | Low, Medium, High, Very High |
| Threat Actor | Multi-select | No | APT1, APT28 (Fancy Bear), APT29 (Cozy Bear), APT33 (Elfin), Lazarus Group, FIN7, Carbanak, Unknown, Hacktivist, Financially Motivated |
| Malware Family | Multi-select | No | Emotet, Qakbot, Ryuk, TrickBot, Conti, Cobalt Strike, Lokibot, WannaCry, Dridex, Unknown |
| Campaign | Text | No | Campaign identifier |
| Date Discovered | Date | No | Date picker |
| Source | Text | No | Intelligence source |

#### Status Groups

- **To Do**: New
- **In Progress**: Investigating, Confirmed
- **Complete**: Mitigated, False Positive, Archived

#### Views

1. **All IOCs** (Table)
   - Sort: Date Discovered (descending)
   - Shows: All properties
   - Purpose: Complete IOC inventory

2. **Active Threats** (Board)
   - Group by: Status
   - Shows: IOC Name, Severity, Threat Actor
   - Purpose: Active IOC management

3. **By Severity** (Table)
   - Group by: Severity
   - Sort: Severity (descending)
   - Shows: Key properties
   - Purpose: Prioritize by severity

4. **Threat Timeline** (Timeline)
   - Timeline by: Date Discovered
   - Shows: IOC Name
   - Purpose: Temporal analysis of threats

5. **By IOC Type** (Table)
   - Group by: IOC Type
   - Sort: Severity (descending)
   - Shows: Key properties
   - Purpose: Categorize by indicator type

### 3. Detection Rules Database

**Purpose**: Version control and management of detection rules.

#### Properties

| Property Name | Type | Required | Options/Values |
|--------------|------|----------|----------------|
| Rule Name | Title | Yes | Free text |
| Status | Status | Yes | Draft, Testing, Production, Deprecated |
| Severity | Select | No | Critical, High, Medium, Low, Informational |
| Description | Text | No | Rule description |
| Rule Logic | Text | Yes | Actual rule syntax |
| MITRE Techniques | Multi-select | No | T1059 - Command & Scripting, T1082 - System Information Discovery, T1078 - Valid Accounts, T1486 - Data Encryption, T1566 - Phishing, T1053 - Scheduled Task/Job, T1083 - File & Directory Discovery, T1204 - User Execution, T1569 - System Services, T1105 - Ingress Tool Transfer |
| Data Sources | Multi-select | No | EDR, SIEM, Network Traffic, Firewall Logs, DNS Logs, Cloud Logs, Authentication Logs, Web Proxy, Email Security |
| Implementation Date | Date | No | Date picker |
| Last Updated | Date | No | Date picker |
| Reference URL | URL | No | External link |

#### Status Groups

- **To Do**: Draft
- **In Progress**: Testing
- **Complete**: Production, Deprecated

#### Views

1. **All Rules** (Table)
   - Sort: Rule Name (ascending)
   - Shows: All properties
   - Purpose: Complete rule inventory

2. **By Status** (Board)
   - Group by: Status
   - Shows: Rule Name, Severity, MITRE Techniques
   - Purpose: Track rule lifecycle

3. **By Severity** (Board)
   - Group by: Severity
   - Shows: Rule Name, Status, MITRE Techniques, Data Sources
   - Purpose: Priority-based organization

4. **Implementation Timeline** (Timeline)
   - Timeline by: Implementation Date
   - Shows: Rule Name
   - Purpose: Track deployment schedule

5. **Technical Details** (Table)
   - Sort: Rule Name (ascending)
   - Shows: All properties including Rule Logic
   - Purpose: Detailed technical reference

### 4. Threat Hunting Evidence Repository

**Purpose**: Document and organize evidence from investigations.

#### Properties

| Property Name | Type | Required | Options/Values |
|--------------|------|----------|----------------|
| Threat Name | Title | Yes | Free text |
| Date Detected | Date | Yes | Date picker |
| Status | Status | Yes | New, In Progress, Contained, Resolved, False Positive |
| Severity | Select | No | Critical, High, Medium, Low, Informational |
| Affected Systems | Multi-select | No | Workstations, Servers, Network Devices, Cloud Services, Mobile Devices, IoT Devices, Databases, Web Applications |
| Threat Actor | Select | No | APT29, APT28, Lazarus Group, Conti, Unknown, Internal, Ransomware Group, Nation State, Hacktivist |
| Attack Vector | Select | No | Phishing, Malware, Zero-day Exploit, Social Engineering, Supply Chain, Brute Force, Credential Stuffing, Drive-by Download, Insider Threat |
| MITRE ATT&CK Techniques | Multi-select | No | T1059 - Command and Scripting Interpreter, T1566 - Phishing, T1486 - Data Encryption for Impact, T1082 - System Information Discovery, T1087 - Account Discovery, T1078 - Valid Accounts, T1105 - Ingress Tool Transfer, T1027 - Obfuscated Files or Information, T1053 - Scheduled Task/Job, T1569 - System Services |
| Indicators of Compromise | Text | No | Related IOCs |
| Evidence Links | URL | No | Storage location |
| Assigned To | Person | No | Investigating analyst |
| Remediation Notes | Text | No | Actions taken |

#### Status Groups

- **To Do**: New
- **In Progress**: In Progress, Contained
- **Complete**: Resolved, False Positive

#### Views

1. **All Threats** (Table)
   - Sort: Date Detected (descending)
   - Shows: All properties
   - Purpose: Complete evidence inventory

2. **Active Investigations** (Board)
   - Group by: Status
   - Shows: Threat Name, Severity, Date Detected, Assigned To
   - Purpose: Track ongoing investigations

3. **Severity Dashboard** (Board)
   - Group by: Severity
   - Shows: Threat Name, Date Detected, Status
   - Purpose: Prioritize by severity

4. **Timeline** (Calendar)
   - Calendar by: Date Detected
   - Shows: Threat Name
   - Purpose: Temporal analysis

5. **By Attack Vector** (Table)
   - Group by: MITRE ATT&CK Techniques
   - Sort: Severity (descending)
   - Shows: Key properties
   - Purpose: Analyze by attack method

### 5. Threat Hunting Query Library

**Purpose**: Reusable threat hunting queries for various security platforms.

#### Properties

| Property Name | Type | Required | Options/Values |
|--------------|------|----------|----------------|
| Query Name | Title | Yes | Free text |
| Description | Text | Yes | What the query detects |
| Query Syntax | Text | Yes | Actual query code |
| Target Platform | Select | No | Splunk, ELK Stack, Microsoft Sentinel, QRadar, CrowdStrike, Chronicle, Sumo Logic, Graylog, Sysmon |
| Threat Type | Multi-select | No | Malware, Ransomware, Data Exfiltration, Lateral Movement, Privilege Escalation, Persistence, Initial Access, Defense Evasion, Command & Control |
| MITRE ATT&CK Techniques | Multi-select | No | T1059 - Command Execution, T1078 - Valid Accounts, T1027 - Obfuscation, T1105 - Ingress Tool Transfer, T1003 - Credential Access, T1136 - Account Creation, T1071 - C2 Protocol, T1082 - System Info Discovery, T1486 - Data Encryption |
| Data Sources | Multi-select | No | Windows Event Logs, Network Flows, EDR Data, Firewall Logs, Proxy Logs, DNS Logs, Authentication Logs, Cloud Logs, Email Logs |
| Severity | Select | No | Critical, High, Medium, Low, Informational |
| False Positive Rate | Select | No | Very Low (<1%), Low (1-5%), Medium (5-15%), High (15-30%), Very High (>30%) |
| Last Tested | Date | No | Date picker |
| Author | Person | No | Query creator |
| Response Playbook | URL | No | Link to procedures |

#### Views

1. **All Queries** (Table)
   - Sort: Severity (descending)
   - Shows: All properties
   - Purpose: Complete query library

2. **By Threat Type** (Board)
   - Group by: Threat Type
   - Shows: Query Name, Severity, Target Platform, Last Tested
   - Purpose: Organize by threat category

3. **MITRE Framework** (Table)
   - Group by: MITRE ATT&CK Techniques
   - Shows: Query Name, MITRE ATT&CK Techniques, Threat Type, Target Platform, Severity
   - Purpose: Align with MITRE framework

4. **Recently Tested** (Calendar)
   - Calendar by: Last Tested
   - Shows: Query Name
   - Purpose: Track query validation

5. **Critical Threats** (List)
   - Sort: Threat Type (descending)
   - Shows: Query Name
   - Purpose: Quick access to critical queries

## View Configurations

### Common View Settings

All views share these common features:

- **Filters**: Can be applied to any property
- **Sorts**: Support multiple sort levels
- **Display Properties**: Customizable column visibility
- **Grouping**: Available in table and board views
- **Hide Empty Groups**: Toggle empty group visibility

### View Type Capabilities

| View Type | Best For | Features |
|-----------|----------|----------|
| Table | Detailed data analysis | Multiple columns, sorts, filters, grouping |
| Board | Kanban-style workflow | Grouped by select/status, drag-and-drop |
| Gallery | Visual browsing | Card-based layout, cover images |
| List | Simple overviews | Minimal display, quick scanning |
| Calendar | Time-based views | Date-based organization, monthly/weekly views |
| Timeline | Project planning | Gantt-style, date ranges, dependencies |

## Database Relationships

### Recommended Relations

While not pre-configured, these relationships enhance workflow:

```
Threat Hunts ←→ IOC Collection
    - Link IOCs discovered during hunts
    - Track which hunts found which IOCs

Threat Hunts ←→ Evidence Repository
    - Link evidence to specific hunts
    - Track investigation outcomes

IOC Collection ←→ Detection Rules
    - Link IOCs to related detection rules
    - Track rule effectiveness

Evidence Repository ←→ IOC Collection
    - Link evidence to specific IOCs
    - Cross-reference findings

Detection Rules ←→ Query Library
    - Link detection rules to hunting queries
    - Track query-to-rule conversion

Query Library ←→ Evidence Repository
    - Link queries that found evidence
    - Track query effectiveness
```

### Creating Relations

To create a relation between databases:

1. Add a "Relation" property to the first database
2. Select the target database
3. Choose "Dual property" to create bidirectional link
4. Name both directions of the relationship
5. Optionally add rollup properties to count related items

## Property Reference

### Property Type Best Practices

#### Title
- First property in every database
- Used as the main identifier
- Appears in page names and links
- Should be descriptive and unique

#### Text
- For long-form content
- Supports markdown formatting
- Useful for descriptions, notes, summaries
- No character limit

#### Number
- For numeric values
- Supports formulas
- Can format as currency, percent, etc.
- Useful for scores, counts, metrics

#### Select
- Single choice from list
- Color-coded options
- Good for status, priority, categories
- Limited to one selection per entry

#### Multi-select
- Multiple choices from list
- Color-coded options
- Good for tags, categories, classifications
- Support multiple selections

#### Status
- Special select type
- Grouped into workflow stages
- Supports drag-and-drop in board views
- Recommended for workflow tracking

#### Date
- Date or date-time picker
- Supports date ranges
- Used in calendar and timeline views
- Can include time if needed

#### Person
- Assigns workspace members
- Supports multiple assignees
- Shows profile pictures
- Used for ownership and collaboration

#### Files & Media
- Upload or link files
- Supports images, PDFs, videos
- Stored in Notion or linked externally
- Preview available in database

#### URL
- Link to external resources
- Validates URL format
- Clickable in database
- Useful for references

#### Relation
- Links to other databases
- Creates connections between data
- Bidirectional if desired
- Foundation for complex workflows

#### Rollup
- Aggregates data from related items
- Requires a relation property
- Supports various calculations (count, sum, average, etc.)
- Updates automatically

## MITRE ATT&CK Mapping

### Technique Coverage

The template includes properties mapping to MITRE ATT&CK techniques across multiple databases:

#### Detection Rules - MITRE Techniques
- T1059 - Command & Scripting Interpreter
- T1082 - System Information Discovery
- T1078 - Valid Accounts
- T1486 - Data Encryption for Impact
- T1566 - Phishing
- T1053 - Scheduled Task/Job
- T1083 - File & Directory Discovery
- T1204 - User Execution
- T1569 - System Services
- T1105 - Ingress Tool Transfer

#### Evidence Repository - MITRE ATT&CK Techniques
- T1059 - Command and Scripting Interpreter
- T1566 - Phishing
- T1486 - Data Encryption for Impact
- T1082 - System Information Discovery
- T1087 - Account Discovery
- T1078 - Valid Accounts
- T1105 - Ingress Tool Transfer
- T1027 - Obfuscated Files or Information
- T1053 - Scheduled Task/Job
- T1569 - System Services

#### Query Library - MITRE ATT&CK Techniques
- T1059 - Command Execution
- T1078 - Valid Accounts
- T1027 - Obfuscation
- T1105 - Ingress Tool Transfer
- T1003 - Credential Access
- T1136 - Account Creation
- T1071 - C2 Protocol
- T1082 - System Info Discovery
- T1486 - Data Encryption

### Adding More Techniques

To expand MITRE coverage:

1. Visit https://attack.mitre.org/
2. Navigate to desired technique
3. Copy technique ID and name
4. Add to relevant multi-select property
5. Update documentation

## Data Flow Diagram

```
┌─────────────────────┐
│  Threat Hunt Starts │
└──────────┬──────────┘
           │
           ▼
    ┌──────────────┐
    │Query Library │◄─── Use proven queries
    └──────┬───────┘
           │
           ▼
   ┌───────────────┐
   │Execute Search │
   └───────┬───────┘
           │
           ▼
    ┌─────────────┐
    │Find Evidence│
    └──────┬──────┘
           │
           ▼
┌─────────────────────┐
│Evidence Repository  │
└──────┬──────────────┘
       │
       ├──► Extract IOCs ──► IOC Collection
       │
       ├──► Create Rules ──► Detection Rules
       │
       └──► Document ──────► Threat Hunts DB
```

## Customization Guidelines

### Safe to Modify
- Property names (won't break functionality)
- Select/multi-select options
- View configurations
- Page layout and styling
- Add new properties
- Add new views

### Modify with Caution
- Property types (may break formulas)
- Status property groups (affects workflows)
- Database relations (affects links)
- Remove existing properties (may lose data)

### Documentation Requirements

When customizing, document:
- Why the change was made
- What was changed
- Impact on existing data
- Update training materials
- Notify team members

---

**Version**: 1.0.0  
**Last Updated**: November 2025  
**Template ID**: 21b945fa575080659ef7f0ddce820efa
