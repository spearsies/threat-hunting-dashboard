# 🚀 Setup Guide - Cybersecurity Threat Hunting Dashboard

This guide will walk you through the complete setup process for the Cybersecurity Threat Hunting Dashboard Notion template.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Initial Setup](#initial-setup)
3. [Team Configuration](#team-configuration)
4. [Database Configuration](#database-configuration)
5. [Workflow Setup](#workflow-setup)
6. [Integration Planning](#integration-planning)
7. [Troubleshooting](#troubleshooting)

## Prerequisites

### Required

- **Notion Account**: Free, Plus, Business, or Enterprise
- **Browser**: Modern web browser (Chrome, Firefox, Safari, Edge)
- **Permissions**: Ability to create and share pages in your workspace

### Recommended

- Basic understanding of cybersecurity concepts
- Familiarity with threat hunting methodologies
- Knowledge of your organization's security tools and data sources
- List of team members who will use the dashboard

### Optional

- Existing threat hunting data to import
- Detection rules to document
- IOC feeds to integrate
- Query library to populate

## Initial Setup

### Step 1: Duplicate the Template

1. **Access the Template**
   ```
   https://www.notion.so/Cybersecurity-Threat-Hunting-Dashboard-21b945fa575080659ef7f0ddce820efa
   ```

2. **Duplicate to Your Workspace**
   - Click the "Duplicate" button in the top-right corner
   - Select your target workspace
   - Choose the location (personal or team space)
   - Click "Duplicate"

3. **Verify the Copy**
   - Confirm all 5 databases are present:
     - Threat Hunts
     - IOC Collection
     - Detection Rules
     - Threat Hunting Evidence Repository
     - Threat Hunting Query Library
   - Check that the Operational Guidelines callout is visible
   - Verify the Threat Priority Matrix is displayed

### Step 2: Customize the Dashboard

1. **Update the Operational Guidelines**
   - Click on the red Operational Guidelines callout
   - Edit the guidelines to match your organization's processes
   - Add or remove bullet points as needed
   - Save changes

2. **Adjust the Threat Priority Matrix**
   - Click on the green Priority Matrix callout
   - Modify severity levels to match your SLAs
   - Update time-to-response values
   - Adjust score ranges if using a scoring system
   - Save changes

3. **Rename the Dashboard (Optional)**
   - Click on the title "🛡️ Cybersecurity Threat Hunting Dashboard"
   - Add your organization name or team name
   - Example: "🛡️ [Company] Security - Threat Hunting Dashboard"

### Step 3: Set Workspace Permissions

1. **Configure Page Access**
   - Click "Share" in the top-right corner
   - Choose between:
     - **Private**: Only invited members can access
     - **Team Space**: Anyone in the workspace can access
   - Set default permission level (Can view, Can comment, Can edit)

2. **Lock Critical Sections (Optional)**
   - Lock the Operational Guidelines and Priority Matrix
   - Prevents accidental edits by team members
   - Click the six-dot handle, then "Lock page"

## Team Configuration

### Step 1: Invite Team Members

1. **Add Users to the Workspace**
   - Click "Share" at the top-right
   - Enter email addresses of team members
   - Set appropriate permission level
   - Send invitations

2. **Define Roles and Responsibilities**
   
   Suggested team structure:
   
   | Role | Permissions | Responsibilities |
   |------|-------------|------------------|
   | Team Lead | Full access | Oversee all hunting activities, approve rules |
   | Senior Analyst | Full access | Create hunts, validate IOCs, write rules |
   | Analyst | Can edit | Execute hunts, document findings |
   | Junior Analyst | Can edit | Support hunts, update evidence |
   | Viewer | Can view | Read-only access for stakeholders |

3. **Create a Team Directory (Optional)**
   - Add a new page under the dashboard
   - List team members and their roles
   - Include contact information
   - Link to individual analyst pages

### Step 2: Establish Notification Preferences

1. **Personal Notifications**
   - Each user should configure their notification settings
   - Navigate to Settings & Members → Notifications
   - Set preferences for:
     - Page mentions
     - Comments
     - Database updates

2. **Team Alerts**
   - Decide on critical alert methods
   - Configure integrations (Slack, email)
   - Document escalation procedures

## Database Configuration

### Threat Hunts Database

1. **Customize Status Options**
   - Open the database
   - Click on the "Status" property
   - Add, remove, or rename status options
   - Organize into groups (To Do, In Progress, Complete)

2. **Add Team-Specific Properties**
   - Click "+" to add new properties
   - Examples:
     - "Risk Score" (Number)
     - "Stakeholder" (Person)
     - "Related Incidents" (Relation)
     - "Budget" (Number)

3. **Configure Views**
   - Review existing views
   - Create custom views for your workflow:
     - "My Hunts" (filtered by current user)
     - "This Week" (filtered by date range)
     - "High Priority" (filtered by priority)

### IOC Collection Database

1. **Customize IOC Types**
   - Review the IOC Type select options
   - Add organization-specific types if needed
   - Remove irrelevant types

2. **Update Threat Actor List**
   - Add threat actors relevant to your industry
   - Include any tracked internal threat actors
   - Update descriptions with context

3. **Configure Malware Families**
   - Review and update the malware family list
   - Add families you commonly encounter
   - Remove outdated or irrelevant families

### Detection Rules Database

1. **Add MITRE Techniques**
   - Review the MITRE Techniques multi-select
   - Add additional techniques relevant to your environment
   - Include full technique IDs and names

2. **Update Data Sources**
   - Match data sources to your actual security stack
   - Add specific tool names (e.g., "Splunk Enterprise", "Azure Sentinel")
   - Remove unavailable sources

3. **Create Rule Templates**
   - Create example entries for common rule types
   - Use these as templates for new rules
   - Include formatting standards in descriptions

### Evidence Repository Database

1. **Customize Affected Systems**
   - Update system types to match your environment
   - Add specific system categories
   - Consider adding system criticality levels

2. **Configure Attack Vectors**
   - Add vectors specific to your threat model
   - Include emerging attack methods
   - Remove irrelevant options

3. **Set Up Evidence Storage**
   - Decide on evidence storage location
   - Configure Evidence Links format
   - Document access procedures

### Query Library Database

1. **Add Your Platforms**
   - Update Target Platform to match your tools
   - Include specific version information
   - Add platform-specific query syntax notes

2. **Define Query Categories**
   - Add threat type categories
   - Create query complexity levels
   - Include query performance tiers

3. **Set Testing Procedures**
   - Define what "Last Tested" means
   - Create testing checklist
   - Document validation process

## Workflow Setup

### Step 1: Define Your Threat Hunting Process

1. **Document the Hunt Lifecycle**
   - Create a sub-page under the dashboard
   - Outline stages: Planning → Execution → Analysis → Reporting
   - Include decision points and approvals

2. **Create Templates**
   - Threat Hunt Template
   - IOC Report Template
   - Detection Rule Specification
   - Investigation Report Template

3. **Establish SLAs**
   - Response times by severity
   - Investigation timelines
   - Reporting requirements

### Step 2: Configure Automation

1. **Database Relations**
   - Link related databases:
     - Hunts → IOCs
     - IOCs → Detection Rules
     - Hunts → Evidence
     - Evidence → IOCs

2. **Rollup Properties**
   - Create rollups to count related items
   - Calculate aggregated risk scores
   - Track completion percentages

3. **Formula Properties**
   - Days since last update
   - Auto-calculated priority scores
   - Status indicators

### Step 3: Create Dashboards and Reports

1. **Executive Dashboard**
   - Create a high-level view page
   - Include key metrics:
     - Active hunts by priority
     - New IOCs this week
     - Detection rule coverage
     - Evidence backlog

2. **Analyst Dashboard**
   - Personal view of assigned items
   - Quick access to common queries
   - Recent updates and comments

3. **Metrics Dashboard**
   - Hunt success rate
   - False positive rates
   - Mean time to detect/respond
   - Coverage by MITRE technique

## Integration Planning

### Security Tool Integration

1. **SIEM/Log Aggregation**
   - Document your SIEM platform
   - Plan query export process
   - Create query naming standards

2. **Threat Intelligence Platforms**
   - Define IOC export formats
   - Plan synchronization frequency
   - Document API endpoints

3. **Ticketing Systems**
   - Create ticket linking standards
   - Define when to create tickets
   - Document escalation procedures

### Notification Integration

1. **Slack Integration**
   - Set up Notion → Slack notifications
   - Create dedicated threat hunting channel
   - Configure alert routing

2. **Email Integration**
   - Configure email notifications
   - Create distribution lists
   - Set up digest schedules

3. **Custom Webhooks**
   - Document webhook endpoints
   - Plan event triggers
   - Test integration flow

## Troubleshooting

### Common Issues

#### Issue: Database Views Not Loading

**Solution:**
1. Refresh the page
2. Check Notion status page
3. Clear browser cache
4. Try a different browser

#### Issue: Cannot Add Team Members

**Solution:**
1. Verify workspace permission level
2. Check if workspace has available seats
3. Ensure email addresses are correct
4. Resend invitations if expired

#### Issue: Properties Not Updating

**Solution:**
1. Check edit permissions
2. Verify property type compatibility
3. Refresh the page
3. Check for browser extensions interfering

#### Issue: Slow Performance

**Solution:**
1. Reduce number of visible properties
2. Limit database relations
3. Archive old data
4. Split large databases

### Getting Help

1. **Notion Support**
   - Visit: https://www.notion.so/help
   - Email: team@makenotion.com
   - Live chat available

2. **Community Resources**
   - Notion Community Forum
   - Reddit: r/Notion
   - Discord servers

3. **Template-Specific Help**
   - Check GitHub Issues
   - Review documentation
   - Contact template maintainer

## Next Steps

After completing setup:

1. ✅ Import existing threat hunting data
2. ✅ Create your first threat hunt
3. ✅ Document current detection rules
4. ✅ Build your query library
5. ✅ Schedule team training session
6. ✅ Establish regular review meetings
7. ✅ Create backup procedures
8. ✅ Document customizations

## Best Practices Checklist

- [ ] Completed initial setup
- [ ] Invited all team members
- [ ] Customized all databases
- [ ] Created workflow documentation
- [ ] Established naming conventions
- [ ] Set up notifications
- [ ] Configured integrations
- [ ] Created backup process
- [ ] Documented security policies
- [ ] Scheduled regular reviews
- [ ] Trained team members
- [ ] Created support resources

## Appendix

### A. Recommended Notion Features to Enable

- [ ] Backlinks
- [ ] Page icons
- [ ] Page covers
- [ ] Comments
- [ ] Page history
- [ ] Database templates
- [ ] Linked databases

### B. Keyboard Shortcuts

| Action | Shortcut (Mac) | Shortcut (Windows) |
|--------|----------------|-------------------|
| New page | ⌘ + N | Ctrl + N |
| Search | ⌘ + P | Ctrl + P |
| Toggle sidebar | ⌘ + \ | Ctrl + \ |
| Create database | Type `/database` | Type `/database` |
| Quick find | ⌘ + K | Ctrl + K |

### C. Database Property Types Quick Reference

| Type | Use Case | Example |
|------|----------|---------|
| Title | Main identifier | Threat Hunt Name |
| Text | Long-form content | Findings Summary |
| Number | Numeric values | Risk Score |
| Select | Single choice | Priority Level |
| Multi-select | Multiple choices | Threat Types |
| Status | Workflow stages | Investigation Status |
| Date | Time tracking | Start Date |
| Person | Assignment | Assigned Analyst |
| Files & Media | Attachments | Evidence Files |
| Checkbox | Boolean flags | Validated |
| URL | External links | Evidence Link |
| Email | Contact info | Analyst Email |
| Phone | Contact info | Escalation Contact |
| Formula | Calculations | Days Open |
| Relation | Link databases | Related IOCs |
| Rollup | Aggregate data | Total IOC Count |

---

**Need Help?** Open an issue on GitHub or consult the main README.md

**Version**: 1.0.0  
**Last Updated**: November 2025
