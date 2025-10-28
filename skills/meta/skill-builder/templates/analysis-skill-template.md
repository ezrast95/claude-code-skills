---
name: SKILL_NAME_HERE
description: Analyze [WHAT] for [PURPOSE]. Use when user mentions [TRIGGER_WORDS] or requests [ANALYSIS_TYPE].
version: 1.0.0
allowed-tools:
  - Read
  - Grep
  - Glob
  # Read-only for analysis - no modifications
---

# [Analysis Type] Analyzer

Comprehensive analysis tool for [specific domain or use case].

## When to Use

Activate this skill when:
- User requests [analysis type] analysis
- User mentions keywords: [keyword1], [keyword2], [keyword3]
- Context involves [specific scenarios]

## Analysis Framework

### Step 1: Discovery

1. Identify files to analyze using Glob:
   - Pattern: `[file patterns]`
   - Look for: [specific file types or locations]

2. Read relevant files systematically

### Step 2: Analysis Criteria

Analyze each file/component against these criteria:

#### Criterion 1: [Name]
- **What to check**: [Specific checks]
- **Good patterns**: [What good looks like]
- **Issues to flag**: [What to report]
- **Severity levels**: Critical / High / Medium / Low

#### Criterion 2: [Name]
- **What to check**: [Specific checks]
- **Good patterns**: [What good looks like]
- **Issues to flag**: [What to report]

#### Criterion 3: [Name]
- **What to check**: [Specific checks]
- **Good patterns**: [What good looks like]
- **Issues to flag**: [What to report]

### Step 3: Report Generation

Create a structured report with:

```markdown
# [Analysis Type] Report

## Summary
- Files analyzed: [count]
- Issues found: [count by severity]
- Overall assessment: [rating/status]

## Critical Issues
[List critical issues with file:line references]

## High Priority Issues
[List high priority issues]

## Medium Priority Issues
[List medium priority issues]

## Low Priority Issues
[List low priority issues]

## Recommendations
1. [Actionable recommendation with priority]
2. [Actionable recommendation with priority]
3. [Actionable recommendation with priority]

## Positive Findings
[Things that are done well]
```

### Step 4: Prioritization

Help user understand what to fix first:
1. Security issues → Immediate
2. Functionality blockers → High priority
3. Performance issues → Medium priority
4. Style/maintainability → Low priority

## Best Practices

- Always provide file:line references for issues
- Explain WHY something is an issue, not just WHAT
- Offer concrete solutions, not just criticism
- Acknowledge good patterns found
- Prioritize findings by impact

## Examples

### Example: [Specific Analysis Scenario]

**User Request:**
```
Analyze [specific component] for [concerns]
```

**Analysis Process:**
1. Use Glob to find relevant files: `[pattern]`
2. Read each file systematically
3. Check against all criteria
4. Document findings with references
5. Generate prioritized report

**Output Format:**
```markdown
# Analysis Report: [Component]

## Summary
- 15 files analyzed
- 3 critical issues, 5 high, 8 medium, 12 low
- Overall: Needs improvement

## Critical Issues

### Issue: [Problem Description]
- **Location**: `src/auth.js:45`
- **Severity**: Critical
- **Impact**: [Security/Performance/etc]
- **Recommendation**: [How to fix]

[Additional issues...]

## Recommendations
1. Fix critical security vulnerability in auth.js:45 (IMMEDIATE)
2. Refactor database queries in api.js (This week)
3. Add error handling in 8 locations (Next sprint)
```

## Security Considerations

- Never modify files during analysis (read-only)
- Don't expose sensitive data in reports
- Validate file paths before reading
- Handle large files gracefully

## Troubleshooting

**Issue**: Too many low-priority findings cluttering report
**Solution**: Group similar findings, focus on actionable items

**Issue**: Analysis too slow on large codebase
**Solution**: Allow user to specify scope/subdirectory

**Issue**: False positives in findings
**Solution**: Refine detection criteria, provide context
