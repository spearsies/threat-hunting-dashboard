# Contributing to Cybersecurity Threat Hunting Dashboard

Thank you for your interest in contributing to the Cybersecurity Threat Hunting Dashboard Notion template! This document provides guidelines for contributing to the project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Getting Started](#getting-started)
- [Contribution Guidelines](#contribution-guidelines)
- [Style Guidelines](#style-guidelines)
- [Community](#community)

## Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inspiring community for all. By participating in this project, you agree to:

- Use welcoming and inclusive language
- Be respectful of differing viewpoints
- Accept constructive criticism gracefully
- Focus on what is best for the community
- Show empathy towards other community members

### Our Standards

Examples of behavior that contributes to a positive environment:

- Demonstrating empathy and kindness
- Being respectful of differing opinions
- Giving and accepting constructive feedback
- Accepting responsibility for mistakes
- Focusing on the community's best interests

Examples of unacceptable behavior:

- Trolling, insulting comments, or personal attacks
- Public or private harassment
- Publishing others' private information
- Conduct that could reasonably be considered inappropriate

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check existing issues to avoid duplicates. When creating a bug report, include as many details as possible:

**Bug Report Template:**

```markdown
**Description**
A clear and concise description of the bug.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '...'
3. See error

**Expected Behavior**
What you expected to happen.

**Screenshots**
If applicable, add screenshots.

**Environment:**
- Notion Plan: [Free/Plus/Business/Enterprise]
- Browser: [e.g., Chrome, Safari]
- Version: [e.g., 22]

**Additional Context**
Any other context about the problem.
```

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion, include:

**Enhancement Template:**

```markdown
**Is your feature request related to a problem?**
A clear description of the problem.

**Describe the solution you'd like**
A clear description of what you want to happen.

**Describe alternatives you've considered**
Alternative solutions or features you've considered.

**Use Case**
Describe the specific use case for this enhancement.

**Additional Context**
Any other context, screenshots, or examples.
```

### Contributing Documentation

Documentation improvements are always welcome! You can contribute by:

- Fixing typos or grammatical errors
- Adding examples or clarifications
- Creating tutorials or guides
- Translating documentation
- Improving existing documentation

### Sharing Customizations

Share your customizations and improvements:

- Custom database views
- Useful formulas or rollups
- Integration guides
- Query library additions
- Detection rule templates
- Workflow improvements

### Contributing Queries and Rules

Contribute to the community knowledge base:

**Query Submission Template:**

```markdown
**Query Name**: [Name of the query]

**Platform**: [Splunk, ELK, Sentinel, etc.]

**Threat Type**: [What it detects]

**MITRE Technique**: [Relevant ATT&CK technique]

**Description**: 
[What the query does and why it's useful]

**Query Syntax**:
```
[Your query code here]
```

**False Positive Rate**: [Your assessment]

**Last Tested**: [Date]

**Notes**: 
[Any additional context, limitations, or requirements]
```

**Detection Rule Template:**

```markdown
**Rule Name**: [Name of the rule]

**Platform**: [SIEM/EDR platform]

**Severity**: [Critical/High/Medium/Low]

**MITRE Technique**: [Relevant ATT&CK technique]

**Description**:
[What the rule detects]

**Rule Logic**:
```
[Your rule code here]
```

**Data Sources**: [Required log sources]

**Tuning Notes**: 
[Recommendations for reducing false positives]

**Testing Instructions**:
[How to validate the rule]
```

## Getting Started

### Setting Up Your Environment

1. **Fork the Repository**
   ```bash
   # Click "Fork" on GitHub
   ```

2. **Clone Your Fork**
   ```bash
   git clone https://github.com/YOUR-USERNAME/threat-hunting-dashboard.git
   cd threat-hunting-dashboard
   ```

3. **Create a Branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

4. **Make Your Changes**
   - Edit documentation files
   - Add new resources
   - Update templates

5. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Description of your changes"
   ```

6. **Push to Your Fork**
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Create a Pull Request**
   - Go to the original repository
   - Click "New Pull Request"
   - Select your branch
   - Fill out the PR template

### Pull Request Process

1. **Before Submitting**
   - Ensure documentation is updated
   - Check for spelling and grammar errors
   - Verify all links work
   - Test any code or queries
   - Update version numbers if applicable

2. **PR Description**
   Include:
   - Summary of changes
   - Motivation and context
   - How changes were tested
   - Screenshots (if applicable)
   - Related issues

3. **Review Process**
   - Maintainers will review your PR
   - Address any requested changes
   - Once approved, your PR will be merged

4. **After Merging**
   - Delete your feature branch
   - Pull the latest changes
   - Celebrate your contribution! 🎉

## Contribution Guidelines

### Documentation Standards

- Use clear, concise language
- Include examples where helpful
- Keep formatting consistent
- Use proper markdown syntax
- Add table of contents for long documents
- Include version information

### File Organization

```
threat-hunting-dashboard/
├── README.md              # Main documentation
├── LICENSE                # License file
├── CONTRIBUTING.md        # This file
├── SETUP_GUIDE.md         # Setup instructions
├── TEMPLATE_STRUCTURE.md  # Template documentation
├── docs/                  # Additional documentation
│   ├── queries/          # Query examples
│   ├── rules/            # Detection rules
│   └── workflows/        # Workflow guides
└── examples/             # Example configurations
```

### Commit Message Guidelines

Follow these conventions:

**Format:**
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Formatting changes
- `refactor`: Code restructuring
- `test`: Adding tests
- `chore`: Maintenance tasks

**Examples:**
```
docs(readme): add installation instructions

Add detailed step-by-step installation instructions
for new users setting up the template for the first time.

Closes #123
```

```
feat(queries): add Splunk query for lateral movement

New query to detect unusual SMB traffic patterns
indicative of lateral movement. Includes notes on
tuning and expected false positive rate.
```

### Version Control

We use semantic versioning:

- **MAJOR.MINOR.PATCH**
- MAJOR: Breaking changes
- MINOR: New features (backward compatible)
- PATCH: Bug fixes

## Style Guidelines

### Markdown Style

- Use ATX-style headers (`#` not `===`)
- Use fenced code blocks with language tags
- Use tables for structured data
- Include blank lines between sections
- Use consistent bullet styles
- Indent nested lists with 2 spaces

### Writing Style

- Write in second person ("you") for instructions
- Use active voice
- Keep sentences concise
- Define technical terms
- Use consistent terminology
- Include relevant links

### Code Style

For any scripts or automation:

- Follow language-specific style guides
- Include comments for complex logic
- Use meaningful variable names
- Keep functions focused and small
- Include error handling

### Query Style

When contributing queries:

- Include inline comments
- Use consistent indentation
- Break long queries into readable sections
- Document required fields
- Note any platform-specific syntax

### Detection Rule Style

When contributing rules:

- Document the rule's purpose
- Include severity justification
- List all dependencies
- Provide tuning guidance
- Include testing steps

## Community

### Getting Help

- **GitHub Issues**: Technical questions and bugs
- **Discussions**: General questions and ideas
- **Wiki**: Community-contributed guides

### Staying Updated

- Watch the repository for updates
- Follow release notes
- Check the changelog
- Join community discussions

### Recognition

Contributors are recognized in:

- README.md Contributors section
- Release notes
- Project documentation

## Review Process

### For Maintainers

When reviewing contributions:

1. **Check Quality**
   - Documentation is clear and complete
   - Changes align with project goals
   - No broken links or typos
   - Proper formatting

2. **Provide Feedback**
   - Be constructive and specific
   - Suggest improvements
   - Acknowledge good work
   - Be timely in responses

3. **Testing**
   - Verify accuracy
   - Test any queries or rules
   - Check cross-references
   - Validate examples

4. **Merging**
   - Squash commits if needed
   - Update version numbers
   - Add to changelog
   - Thank the contributor

### Response Times

We aim to respond to:

- Bug reports: Within 48 hours
- Feature requests: Within 1 week
- Pull requests: Within 1 week
- Questions: Within 72 hours

## Special Contributions

### Translations

To contribute translations:

1. Create a new directory: `docs/translations/[language-code]/`
2. Translate README.md and other key documents
3. Update file with translation credits
4. Submit PR with all translated files

### Integrations

When contributing integration guides:

- Include prerequisites
- Provide step-by-step instructions
- Add screenshots where helpful
- Document limitations
- Test thoroughly
- Note any security considerations

### Templates

When contributing sub-templates:

- Explain the use case
- Document all properties
- Include example entries
- Provide import instructions
- Note any dependencies

## Legal

### License Agreement

By contributing, you agree that your contributions will be licensed under the same MIT License that covers the project.

### Contributor License Agreement

For substantial contributions, we may ask you to sign a Contributor License Agreement (CLA) to clarify the intellectual property rights.

### Privacy

- Don't include personal information
- Don't share sensitive security details
- Don't include proprietary information
- Sanitize all examples and screenshots

## Questions?

If you have questions about contributing:

1. Check existing documentation
2. Search closed issues
3. Ask in discussions
4. Open a new issue with the "question" label

## Thank You!

Every contribution, no matter how small, helps make this template better for the security community. Thank you for taking the time to contribute!

---

**Last Updated**: November 2025  
**Version**: 1.0.0
