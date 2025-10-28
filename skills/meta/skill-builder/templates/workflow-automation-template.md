---
name: SKILL_NAME_HERE
description: Automate [WORKFLOW_NAME] process including [KEY_STEPS]. Use when user wants to [ACTION] or mentions [TRIGGER_WORDS].
version: 1.0.0
dependencies:
  # - package-name==version  # Add if workflow needs packages
---

# [Workflow Name] Automation

Automated workflow for [purpose], streamlining [process description].

## When to Use

This skill activates when:
- User wants to [primary action]
- User mentions: [trigger 1], [trigger 2], [trigger 3]
- Context involves [specific workflow scenario]

## Workflow Overview

```
[Step 1] → [Step 2] → [Step 3] → [Step 4] → [Complete]
   ↓          ↓          ↓          ↓
[Verify]   [Verify]   [Verify]   [Verify]
```

Total steps: [number]
Estimated time: [time estimate]
Risk level: [Low/Medium/High]

## Prerequisites

Before starting, verify:

1. **[Prerequisite 1]**: [What must be true]
   - Check: [How to verify]
   - If missing: [What to do]

2. **[Prerequisite 2]**: [What must be true]
   - Check: [How to verify]
   - If missing: [What to do]

3. **[Prerequisite 3]**: [What must be true]
   - Check: [How to verify]
   - If missing: [What to do]

## Workflow Steps

### Phase 1: [Phase Name]

#### Step 1.1: [Action Name]

**Purpose**: [Why this step is needed]

**Actions:**
1. [Specific action]
2. [Specific action]
3. [Specific action]

**Validation:**
- [ ] [Check 1]
- [ ] [Check 2]
- [ ] [Check 3]

**On Failure:**
- [What to do if this step fails]
- [Recovery steps]

#### Step 1.2: [Action Name]

**Purpose**: [Why this step is needed]

**Actions:**
1. [Specific action]
2. [Specific action]

**Validation:**
- [ ] [Check 1]
- [ ] [Check 2]

**On Failure:**
- [Failure handling]

### Phase 2: [Phase Name]

#### Step 2.1: [Action Name]

**Purpose**: [Why this step is needed]

**Actions:**
1. [Specific action]
2. [Specific action]

**Validation:**
- [ ] [Check 1]
- [ ] [Check 2]

**On Failure:**
- [Failure handling]

#### Step 2.2: [Action Name]

**Purpose**: [Why this step is needed]

**Actions:**
1. [Specific action]
2. [Specific action]

**Validation:**
- [ ] [Check 1]

**On Failure:**
- [Failure handling]

### Phase 3: [Phase Name]

#### Step 3.1: [Final Action]

**Purpose**: [Why this step is needed]

**Actions:**
1. [Specific action]
2. [Specific action]

**Validation:**
- [ ] [Check 1]
- [ ] [Check 2]

**On Failure:**
- [Failure handling]

## Progress Tracking

Use TodoWrite to track workflow progress:

```
1. "Phase 1: [Name]" - in_progress/completed
2. "Phase 2: [Name]" - pending/completed
3. "Phase 3: [Name]" - pending/completed
```

Update status after each phase completes.

## Rollback Procedure

If workflow fails at any step:

1. **Identify failure point**: [How to determine where it failed]
2. **Assess state**: [What to check]
3. **Rollback steps**:
   - If failed at Step 1: [Rollback procedure]
   - If failed at Step 2: [Rollback procedure]
   - If failed at Step 3: [Rollback procedure]

## Success Criteria

Workflow completes successfully when:

- [ ] All validation checks pass
- [ ] [Specific outcome achieved]
- [ ] [Specific outcome achieved]
- [ ] No errors in any phase
- [ ] [Final verification]

## Best Practices

- Always verify prerequisites before starting
- Validate after each step before proceeding
- Keep user informed of progress
- Have rollback plan ready
- Test workflow in safe environment first

## Examples

### Example 1: [Standard Use Case]

**User Request:**
```
[What user asks for]
```

**Workflow Execution:**

**Phase 1: [Name]**
- ✅ Step 1.1: [What happened]
- ✅ Step 1.2: [What happened]

**Phase 2: [Name]**
- ✅ Step 2.1: [What happened]
- ✅ Step 2.2: [What happened]

**Phase 3: [Name]**
- ✅ Step 3.1: [What happened]

**Result:**
```
[What was accomplished]
```

### Example 2: [Use Case with Failure]

**User Request:**
```
[What user asks for]
```

**Workflow Execution:**

**Phase 1: [Name]**
- ✅ Step 1.1: Completed
- ❌ Step 1.2: Failed - [reason]

**Recovery:**
- Rolled back Step 1.1 changes
- Fixed [issue]
- Restarted from Step 1.1

**Phase 1 (Retry):**
- ✅ Step 1.1: Completed
- ✅ Step 1.2: Completed

**Result:**
```
Successfully completed after recovery
```

## Error Handling

### Common Errors

**Error**: [Error type 1]
- **Cause**: [What causes this]
- **Solution**: [How to fix]
- **Prevention**: [How to avoid]

**Error**: [Error type 2]
- **Cause**: [What causes this]
- **Solution**: [How to fix]
- **Prevention**: [How to avoid]

**Error**: [Error type 3]
- **Cause**: [What causes this]
- **Solution**: [How to fix]
- **Prevention**: [How to avoid]

## Safety Considerations

- **[Safety concern 1]**: [How to mitigate]
- **[Safety concern 2]**: [How to mitigate]
- **[Safety concern 3]**: [How to mitigate]

### Risky Operations

These steps are potentially risky:
1. **Step [X]**: [Why it's risky] - [Extra precautions]
2. **Step [Y]**: [Why it's risky] - [Extra precautions]

## Post-Workflow

After successful completion:

1. **Verify results**: [What to check]
2. **Clean up**: [What to clean]
3. **Document**: [What to record]
4. **Notify**: [Who to inform]

## Monitoring

Track these metrics:
- Execution time: [How long it took]
- Success rate: [How many succeeded]
- Failure points: [Where failures occurred]
- Recovery time: [How long to recover]

## Troubleshooting

**Issue**: Workflow stalls at [step]
**Solution**: [How to diagnose and fix]

**Issue**: Validation fails repeatedly
**Solution**: [How to resolve]

**Issue**: Rollback doesn't work correctly
**Solution**: [Manual recovery steps]
