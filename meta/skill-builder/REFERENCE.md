# Skill Builder Reference Guide

## Quick Reference

### Skill Anatomy

```yaml
---
name: skill-name              # Required: lowercase-with-hyphens
description: What it does and when to use it  # Required: max 200 chars
version: 1.0.0               # Recommended: semantic versioning
dependencies:                # Optional: list of packages
  - python-package==1.0.0
  - npm:js-package@2.0.0
allowed-tools:               # Optional: restrict capabilities
  - Read
  - Grep
---

# Skill content in Markdown
```

### File Structure Options

```
Minimal:
skill-name/
└── SKILL.md

Standard:
skill-name/
├── SKILL.md
├── REFERENCE.md
└── templates/
    └── template.txt

Advanced:
skill-name/
├── SKILL.md
├── REFERENCE.md
├── templates/
│   ├── template1.txt
│   └── template2.json
└── scripts/
    ├── helper.py
    └── validator.js
```

## Activation Mechanics

Skills are **model-invoked** - Claude decides when to use them based on:

1. **Keyword matching** in description
2. **Contextual relevance** to current task
3. **Trigger phrases** user naturally says

### Writing Effective Descriptions

**Formula**: `[Action] + [Object] + [Context]. Use when [Trigger words] or [Scenarios].`

**Examples:**

✅ **Good Descriptions:**
```
"Extract text and tables from PDF files, fill forms, merge documents. Use when working with PDF files or when the user mentions PDFs, forms, or document extraction."

"Analyze code for security vulnerabilities using OWASP Top 10 standards. Use when reviewing code security, conducting audits, or when user mentions vulnerabilities, security issues, or penetration testing."

"Generate React components with TypeScript, styled-components, and accessibility features. Use when creating UI components or when user mentions React, components, or frontend development."
```

❌ **Bad Descriptions:**
```
"Helps with documents" - Too vague, no triggers
"PDF tool" - No context about when to use
"Code analysis" - Too broad, will activate incorrectly
```

### Trigger Word Strategy

Include **3 types of trigger words**:

1. **Direct terms**: Exact words user would say
   - "PDF", "security audit", "React component"

2. **Synonyms**: Alternative phrasings
   - "document", "vulnerability scan", "UI element"

3. **Context phrases**: Scenarios that indicate need
   - "working with PDFs", "reviewing code security", "building frontend"

## Skill Categories

### 1. Analysis Skills
- **Purpose**: Examine code/files and report findings
- **Pattern**: Discover → Analyze → Report
- **Tools**: Read, Grep, Glob (read-only)
- **Output**: Structured reports with recommendations

**Template**: `templates/analysis-skill-template.md`

### 2. Generator Skills
- **Purpose**: Create new files/content from templates
- **Pattern**: Gather → Select → Customize → Generate
- **Tools**: Read, Write, Grep (for context)
- **Output**: Production-ready files

**Template**: `templates/generator-skill-template.md`

### 3. Workflow Automation Skills
- **Purpose**: Multi-step processes with validation
- **Pattern**: Prerequisites → Execute → Validate → Complete
- **Tools**: All tools, often including Bash
- **Output**: Completed workflow with tracking

**Template**: `templates/workflow-automation-template.md`

### 4. Transformation Skills
- **Purpose**: Modify existing code/files
- **Pattern**: Read → Transform → Validate → Write
- **Tools**: Read, Edit, Grep
- **Output**: Updated files

### 5. Integration Skills
- **Purpose**: Connect external services/APIs
- **Pattern**: Authenticate → Call → Process → Return
- **Tools**: Bash (for CLI tools), MCP connections
- **Output**: Data from external sources

## Tool Restrictions

Use `allowed-tools` to limit capabilities for:

### Read-Only Skills
```yaml
allowed-tools:
  - Read
  - Grep
  - Glob
```
**Use for**: Analysis, auditing, reporting

### Generation Skills
```yaml
allowed-tools:
  - Read     # Context gathering
  - Write    # File creation
  - Grep     # Pattern searching
  - Glob     # File discovery
```
**Use for**: Scaffolding, templating, documentation

### Transformation Skills
```yaml
allowed-tools:
  - Read     # Load existing content
  - Edit     # Modify in place
  - Grep     # Find targets
  - Glob     # Discover files
```
**Use for**: Refactoring, updates, migrations

### Full Access
```yaml
# No allowed-tools field = all tools available
```
**Use for**: Complex workflows, automation, deployment

## Dependencies

### Python Packages
```yaml
dependencies:
  - pandas==2.0.0
  - requests==2.31.0
  - numpy==1.24.0
```

### Node.js Packages
```yaml
dependencies:
  - npm:axios@1.4.0
  - npm:lodash@4.17.21
```

### Mixed
```yaml
dependencies:
  - pandas==2.0.0          # Python
  - npm:prettier@3.0.0     # Node.js
```

**Important**: Packages must be pre-installed in environment before Claude can use them.

## Best Practices Checklist

### Description Quality
- [ ] Includes what the skill does
- [ ] Includes when to use it
- [ ] Has 3+ specific trigger words
- [ ] Mentions common synonyms
- [ ] Under 200 characters
- [ ] No vague terms like "helps with"

### Content Quality
- [ ] Clear step-by-step instructions
- [ ] Examples with inputs and outputs
- [ ] Error handling guidance
- [ ] Security considerations
- [ ] Troubleshooting section
- [ ] No TODOs or placeholders

### Structure Quality
- [ ] Proper YAML frontmatter
- [ ] Unix-style paths (forward slashes)
- [ ] Version number included
- [ ] Supporting files organized
- [ ] Templates are complete

### Security Quality
- [ ] No hardcoded secrets
- [ ] Input validation mentioned
- [ ] Tool restrictions appropriate
- [ ] External services via MCP
- [ ] Safe file operations

## Testing Strategies

### 1. Direct Trigger Test
Say the exact trigger words from your description:
```
Description: "...Use when user mentions PDF extraction..."
Test: "Help me extract text from this PDF"
Expected: Skill activates ✅
```

### 2. Synonym Test
Use related terms not in description:
```
Description: "...when user mentions PDF extraction..."
Test: "I need to pull text from a document"
Expected: Skill should still activate if description is good
```

### 3. Context Test
Describe the scenario without exact words:
```
Description: "...for code review and security audits..."
Test: "Can you check this code for vulnerabilities?"
Expected: Skill activates ✅
```

### 4. False Positive Test
Say something similar but different:
```
Description: "...for React component generation..."
Test: "Help me debug this React component"
Expected: Skill should NOT activate (debugging, not generation)
```

### Refining Based on Tests

**Skill doesn't activate when it should:**
- Add more trigger words to description
- Include synonyms and context phrases
- Make description more specific to scenario

**Skill activates incorrectly:**
- Make triggers more specific
- Differentiate from similar skills
- Use more precise language

## Common Patterns

### Discovery Questions Pattern
```markdown
## Instructions

### Step 1: Understand Requirements

Ask the user:

1. **[Question 1]**: [Purpose of question]
   - Options: [A/B/C]
   - Default: [if applicable]

2. **[Question 2]**: [Purpose of question]

3. **[Question 3]**: [Purpose of question]

### Step 2: Process Based on Answers
[Use their answers to guide execution]
```

### Validation Gate Pattern
```markdown
### Step 3: Execute Action

1. Perform [action]
2. Validate result:
   - Check: [validation 1]
   - Check: [validation 2]
   - Check: [validation 3]
3. If validation fails:
   - [Failure handling]
4. If validation passes:
   - Proceed to next step
```

### Progressive Enhancement Pattern
```markdown
### Step 2: Generate Output

1. Create minimal working version
2. Add [enhancement 1] if user specified
3. Add [enhancement 2] if user specified
4. Add [enhancement 3] if user specified

Default: Minimal version
Options: [list enhancements available]
```

## Skill Composition

Multiple skills can work together automatically:

**Example Scenario:**
```
User: "Analyze my code and generate a security report"

Activation sequence:
1. code-analyzer skill activates (finds issues)
2. report-generator skill activates (formats results)
3. Combined seamlessly without explicit invocation
```

**Design tip**: Make skills focused so they compose well rather than creating one large multi-purpose skill.

## Version Management

Track versions in content:

```markdown
# Skill Name

Version: 1.2.0

## Changelog

### 1.2.0 (2025-01-15)
- Added support for [feature]
- Fixed bug in [component]
- Improved performance of [step]

### 1.1.0 (2025-01-10)
- Added [feature]
- Updated [template]

### 1.0.0 (2025-01-05)
- Initial release
```

Benefits:
- Team knows what changed
- Can rollback if needed
- Documents evolution

## Distribution

### Personal Skills
```
Location: ~/.claude/skills/skill-name/
Availability: Just you, all projects
Sharing: Not automatically shared
```

### Project Skills
```
Location: .claude/skills/skill-name/
Availability: Team via git
Sharing: Committed to repository
```

### Plugin Skills
```
Location: Inside plugin package
Availability: Anyone who installs plugin
Sharing: Via plugin distribution
```

**Recommendation**: Start with personal, promote to project when proven, package as plugin for wide distribution.

## Troubleshooting

### Skill Not Activating

**Check:**
1. Is SKILL.md in correct location?
2. Is YAML frontmatter valid?
3. Does description have specific triggers?
4. Are you using words from description?

**Fix:**
1. Verify file path: `~/.claude/skills/[name]/SKILL.md`
2. Validate YAML syntax
3. Add more trigger words
4. Test with exact description phrases

### Skill Activates Incorrectly

**Check:**
1. Are triggers too broad?
2. Do other skills have similar descriptions?
3. Is context ambiguous?

**Fix:**
1. Make triggers more specific
2. Differentiate from other skills
3. Add context-specific trigger phrases

### Dependencies Not Found

**Check:**
1. Are packages installed in environment?
2. Is dependency syntax correct?
3. Are versions compatible?

**Fix:**
```bash
# Python
pip install package-name==version

# Node.js
npm install package-name@version
```

### Tool Restrictions Blocking

**Check:**
1. Does skill need tool not in allowed-tools?
2. Is allowed-tools too restrictive?

**Fix:**
1. Add necessary tools to allowed-tools list
2. Remove allowed-tools if full access needed

## Examples from Official Repository

See https://github.com/anthropics/skills for:

- **artifacts-builder**: Complex HTML artifact generation
- **mcp-builder**: MCP server scaffolding
- **webapp-testing**: Playwright browser testing
- **brand-guidelines**: Brand standard application
- **docx**: Word document manipulation
- **pdf**: PDF processing and generation
- **skill-creator**: Meta-skill for building skills

Clone and study these for patterns and inspiration!
