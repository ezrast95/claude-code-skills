# Creating Skills Guide

Learn how to create high-quality Claude Code skills using the skill-builder tool.

## Using skill-builder (Recommended)

The easiest way to create skills is using the **skill-builder** skill included in this repository.

### Quick Start

1. **Install skill-builder** (see [installation.md](installation.md))

2. **Start a conversation** with Claude Code:
   ```
   "Help me create a skill for [describe your workflow]"
   ```

3. **Answer the questions** skill-builder asks:
   - What task/workflow to automate
   - What trigger words should activate it
   - What tools it needs access to
   - Whether it's personal or shared with team
   - Any dependencies required

4. **Review and customize** the generated skill

5. **Test activation** with the suggested trigger phrases

### Example Session

```
You: "Help me create a skill for generating API documentation"

Claude (skill-builder activated):
"I'll help you create a skill for API documentation. Let me ask a few questions:

1. What task or workflow do you want to automate?"

You: "I want to automatically generate OpenAPI specs from FastAPI code"

Claude: "Great! What trigger words should activate this skill?"

You: "When I mention API docs, OpenAPI, Swagger, or API documentation"

Claude: "What tools does it need?
- File operations (read, write, edit)?
- External tools?
- Should any tools be restricted?"

You: "It needs to read Python files and write YAML output"

[skill-builder continues, then generates complete skill with SKILL.md, templates, etc.]
```

## Manual Skill Creation

If you prefer to create skills manually:

### 1. Choose a Skill Name

**Rules:**
- Lowercase letters only
- Use hyphens (not underscores or spaces)
- Descriptive and unique
- Examples: `api-documenter`, `code-reviewer`, `timestamp-converter`

### 2. Create Directory Structure

**Personal skill (just for you):**
```bash
mkdir -p ~/.claude/skills/your-skill-name
```

**Project skill (shared via git):**
```bash
mkdir -p .claude/skills/your-skill-name
```

### 3. Create SKILL.md

Create `SKILL.md` with this template:

```yaml
---
name: your-skill-name
description: Brief description with trigger words. Use when user mentions keywords or context.
version: 1.0.0
---

# Your Skill Name

[Overview of what this skill does]

## When to Use

This skill activates when:
- [Trigger scenario 1]
- [Trigger scenario 2]
- [Keywords mentioned: keyword1, keyword2, keyword3]

## Instructions

### Step 1: [First Action]

[Detailed instructions for Claude]

### Step 2: [Second Action]

[More instructions]

## Examples

### Example 1: [Use Case]

**User Request:**
```
[What user might say]
```

**Process:**
1. [What to do]
2. [Next step]

**Output:**
```
[Expected result]
```

## Best Practices

- [Guideline 1]
- [Guideline 2]

## Security Considerations

- Never hardcode secrets
- Validate inputs
- [Other security notes]
```

### 4. Write Trigger-Rich Descriptions

The description is **critical** for activation. Include:

**Formula:** `[Action] + [Object] + [Context]. Use when [Triggers] or [Scenarios].`

**Good Examples:**
```yaml
description: "Generate OpenAPI documentation from FastAPI code by analyzing routes and models. Use when documenting APIs, creating OpenAPI specs, or when user mentions API docs, Swagger, or REST documentation."

description: "Analyze Python code for security vulnerabilities using OWASP standards. Use when reviewing code security, conducting audits, or when user mentions vulnerabilities, security issues, or pen testing."
```

**Bad Examples:**
```yaml
description: "Helps with APIs"  # Too vague, no triggers

description: "Documentation tool"  # No context about when to use
```

### 5. Add Supporting Files (Optional)

```
your-skill-name/
├── SKILL.md           # Required
├── REFERENCE.md       # Additional context/guidelines
├── templates/         # Code templates
│   └── template.txt
└── scripts/           # Helper scripts
    └── helper.py
```

## Skill Categories

### Analysis Skills

**Purpose:** Examine code/files and report findings

**Pattern:**
1. Discover files to analyze
2. Check against criteria
3. Generate structured report
4. Prioritize findings

**Template:** Use `skill-builder` and select "analysis" pattern

**Tools:** Read, Grep, Glob (read-only recommended)

### Generator Skills

**Purpose:** Create new files/content from templates

**Pattern:**
1. Gather requirements from user
2. Select appropriate template
3. Customize with user's inputs
4. Generate production-ready files

**Template:** Use `skill-builder` and select "generator" pattern

**Tools:** Read, Write, Grep

### Workflow Automation Skills

**Purpose:** Multi-step processes with validation

**Pattern:**
1. Verify prerequisites
2. Execute steps with validation gates
3. Handle failures with rollback
4. Track progress with TodoWrite

**Template:** Use `skill-builder` and select "workflow" pattern

**Tools:** All tools typically needed

## Best Practices

### Description Quality
- ✅ Include what it does AND when to use it
- ✅ Add 3+ specific trigger words
- ✅ Mention common synonyms and related terms
- ✅ Keep under 200 characters
- ❌ Avoid vague terms like "helps with" or "tool for"

### Content Quality
- ✅ Clear step-by-step instructions
- ✅ Include examples with inputs/outputs
- ✅ Add error handling guidance
- ✅ Document security considerations
- ✅ Provide troubleshooting tips
- ❌ No TODOs or placeholder comments
- ❌ No incomplete instructions

### Security
- ✅ Never hardcode API keys or passwords
- ✅ Use MCP connections for external services
- ✅ Validate all user inputs
- ✅ Use `allowed-tools` to restrict capabilities when appropriate
- ✅ Document any security implications

### Tool Restrictions

Use `allowed-tools` for security-sensitive skills:

```yaml
---
name: code-analyzer
allowed-tools:
  - Read
  - Grep
  - Glob
  # No Write/Edit - read-only analysis
---
```

## Testing Your Skill

### 1. Test Activation

Try these trigger patterns:

**Direct triggers:**
```
"[Use exact words from description]"
```

**Synonym test:**
```
"[Use related terms not in description]"
```

**Context test:**
```
"[Describe scenario without exact words]"
```

### 2. Verify Behavior

- Does it execute all steps correctly?
- Are outputs complete (no placeholders)?
- Does error handling work?
- Are security practices followed?

### 3. Refine Description

If skill doesn't activate:
- Add more trigger words
- Include synonyms and context phrases
- Make description more specific

If skill activates incorrectly:
- Make triggers more specific
- Differentiate from similar skills
- Add context requirements

## Advanced Features

### Dependencies

**Python packages:**
```yaml
dependencies:
  - pandas==2.0.0
  - requests==2.31.0
```

**Node.js packages:**
```yaml
dependencies:
  - npm:axios@1.4.0
  - npm:prettier@3.0.0
```

Packages must be pre-installed in the environment.

### Version Management

Track versions in your SKILL.md:

```markdown
# Skill Name

Version: 1.2.0

## Changelog

### 1.2.0 (2025-01-15)
- Added [feature]
- Fixed [bug]

### 1.1.0 (2025-01-10)
- Initial release
```

## Common Patterns

### Discovery Questions Pattern

```markdown
## Instructions

### Step 1: Understand Requirements

Ask the user:
1. **[Question 1]**: [Purpose]
2. **[Question 2]**: [Purpose]

### Step 2: Process Based on Answers
[Use answers to guide execution]
```

### Validation Gate Pattern

```markdown
### Step 2: Execute Action

1. Perform [action]
2. Validate:
   - Check: [criterion 1]
   - Check: [criterion 2]
3. If validation fails: [handle error]
4. If passes: proceed
```

### Progressive Enhancement

```markdown
### Step 3: Generate Output

1. Create minimal working version
2. If user wants [feature]: add it
3. If user wants [enhancement]: add it

Default: Minimal version
```

## Sharing Your Skill

### Personal → Project

To share a personal skill with your team:

```bash
# Copy from personal to project
cp -r ~/.claude/skills/your-skill ~/.claude/skills/

# Commit to git
git add .claude/skills/your-skill
git commit -m "Add your-skill for team"
git push
```

### Contributing to This Repository

See [contributing.md](contributing.md) for how to submit your skill to this collection.

## Resources

- **skill-builder templates:** See `skills/meta/skill-builder/templates/`
- **Official docs:** https://docs.claude.com/en/docs/claude-code/skills.md
- **Anthropic examples:** https://github.com/anthropics/skills

## Getting Help

- Use skill-builder: `"Help me create a skill"`
- Check [installation.md](installation.md) for setup issues
- Open an issue: https://github.com/ezrast95/claude-code-skills/issues

Happy skill building! 🚀
