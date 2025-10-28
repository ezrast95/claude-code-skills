# Contributing Guide

Thank you for considering contributing to the Claude Code Skills collection! This guide will help you submit high-quality skills.

## How to Contribute

### 1. Fork the Repository

Click the "Fork" button on GitHub to create your own copy.

### 2. Create Your Skill

**Option A: Use skill-builder (Recommended)**
```
"Help me create a skill for [your workflow]"
```

**Option B: Manual Creation**
Follow the [Creating Skills Guide](creating-skills.md)

### 3. Test Thoroughly

Before submitting, verify:

#### Activation Tests
- [ ] Activates with trigger words from description
- [ ] Activates with synonym variations
- [ ] Activates in relevant contexts
- [ ] Does NOT activate in unrelated contexts

#### Functionality Tests
- [ ] All steps execute correctly
- [ ] No placeholder or TODO comments
- [ ] Error handling works properly
- [ ] Security practices followed
- [ ] Examples in SKILL.md are accurate

#### Quality Checks
- [ ] YAML frontmatter is valid
- [ ] Description is under 200 characters
- [ ] Description includes trigger words
- [ ] All files use Unix-style paths (forward slashes)
- [ ] No hardcoded secrets or credentials

### 4. Choose the Right Category

Place your skill in the appropriate directory:

- **meta/** - Tools for building/managing skills
- **utilities/** - General purpose tools (time, conversion, formatting)
- **analysis/** - Code review, security audits, quality checks
- **generators/** - Code/content generation, scaffolding
- **workflows/** - Multi-step automation, deployment, CI/CD
- **integrations/** - External API/service connections

Not sure? Default to **utilities/** or ask in your Pull Request.

### 5. Update Documentation

#### Update Main README

Add your skill to the "Available Skills" section:

```markdown
### 🔧 Utilities

#### [your-skill-name](skills/utilities/your-skill-name/)
Brief one-line description of what it does.

**Use when:** Clear use case explanation

**Features:**
- Feature 1
- Feature 2
- Feature 3

**Activation triggers:** "keyword1", "keyword2", "context phrase"
```

#### Create Skill README (Optional)

Add `skills/category/your-skill/README.md` with:
- Detailed description
- Installation instructions specific to this skill
- Usage examples
- Screenshots/demos (if applicable)

### 6. Submit Pull Request

1. **Commit your changes:**
   ```bash
   git add skills/category/your-skill/
   git add README.md
   git commit -m "Add [your-skill-name]: [brief description]"
   ```

2. **Push to your fork:**
   ```bash
   git push origin main
   ```

3. **Create Pull Request** on GitHub with:
   - **Title:** `Add [skill-name]: [one-line description]`
   - **Description:** Explain what the skill does and why it's useful
   - **Testing:** Describe how you tested it
   - **Category:** Explain why you chose that category

## Pull Request Template

```markdown
## Skill: [skill-name]

### Description
[Brief description of what the skill does]

### Category
[meta/utilities/analysis/generators/workflows/integrations]

### Use Cases
- [Use case 1]
- [Use case 2]
- [Use case 3]

### Testing
- [x] Tested activation with trigger words
- [x] Tested functionality with examples
- [x] Verified no security issues
- [x] Checked YAML frontmatter is valid
- [x] Updated main README

### Additional Notes
[Any other relevant information]
```

## Skill Quality Standards

### Required Elements

Every skill MUST have:

1. **Valid YAML frontmatter**
   ```yaml
   ---
   name: skill-name
   description: Clear description with triggers
   version: 1.0.0
   ---
   ```

2. **Clear trigger-rich description**
   - Explains what it does
   - Explains when to use it
   - Includes specific trigger words
   - Under 200 characters

3. **Structured instructions**
   - Step-by-step process
   - Clear and actionable
   - No ambiguity

4. **Examples**
   - At least one complete example
   - Shows input and expected output
   - Demonstrates common use case

5. **Security considerations**
   - No hardcoded secrets
   - Input validation guidance
   - Tool restrictions if needed

### Recommended Elements

Skills SHOULD include:

- **REFERENCE.md** - For complex skills with extensive context
- **Templates** - Reusable code/content templates
- **Scripts** - Helper scripts if needed
- **Troubleshooting section** - Common issues and solutions
- **Version history** - Track changes over time

## Code Style

### YAML Frontmatter
- Use lowercase for `name`
- Use hyphens (not underscores) in names
- Keep `description` under 200 chars
- Include `version` following semantic versioning

### Markdown Content
- Use proper headers (##, ###)
- Include code blocks with language specifiers
- Use lists for clarity
- Keep line length reasonable (~80-120 chars)

### File Paths
- Always use Unix-style paths (forward slashes)
- Example: `src/utils/helper.js` ✅
- NOT: `src\utils\helper.js` ❌

## Security Guidelines

### Never Include
- ❌ API keys or tokens
- ❌ Passwords or credentials
- ❌ Private repository URLs with auth
- ❌ Personal identifiable information

### Always Include
- ✅ Input validation guidance
- ✅ Security considerations section
- ✅ Safe file operation practices
- ✅ Tool restrictions when appropriate

### Use allowed-tools for Restrictions

For read-only skills:
```yaml
allowed-tools:
  - Read
  - Grep
  - Glob
```

For security-sensitive workflows:
```yaml
allowed-tools:
  - Read
  - Write
  # Explicitly list only what's needed
```

## Testing Checklist

Before submitting, complete this checklist:

### Activation
- [ ] Activates with exact trigger words from description
- [ ] Activates with natural language variations
- [ ] Activates in relevant contextual scenarios
- [ ] Does NOT activate for unrelated requests

### Functionality
- [ ] All instructions are clear and actionable
- [ ] Examples work as documented
- [ ] Error handling is appropriate
- [ ] No TODO or placeholder content
- [ ] Output is production-ready

### Quality
- [ ] YAML frontmatter is syntactically valid
- [ ] Description is comprehensive but under 200 chars
- [ ] Unix-style paths used throughout
- [ ] No spelling or grammar errors
- [ ] Version number included

### Security
- [ ] No hardcoded secrets or credentials
- [ ] Input validation documented
- [ ] Tool restrictions appropriate for use case
- [ ] Security section included

### Documentation
- [ ] Main README updated with skill entry
- [ ] Category placement is appropriate
- [ ] Examples are accurate and complete
- [ ] Installation notes if dependencies required

## Review Process

1. **Automated checks** run on your PR (if configured)
2. **Manual review** by maintainers:
   - Quality standards met
   - Security practices followed
   - Appropriate category
   - Documentation complete
3. **Feedback** provided if changes needed
4. **Merge** once approved

## Communication

- **Questions?** Open a GitHub issue or ask in PR comments
- **Bugs?** Open an issue with steps to reproduce
- **Feature requests?** Open an issue describing the use case
- **General discussion?** Use GitHub Discussions

## Recognition

Contributors will be:
- Listed in commit history
- Credited in skill documentation (if desired)
- Acknowledged in release notes for significant contributions

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

## Getting Help

- **Creating skills:** See [creating-skills.md](creating-skills.md)
- **Installation:** See [installation.md](installation.md)
- **Questions:** Open a GitHub issue
- **Real-time help:** Use skill-builder to create skills interactively

## Examples of Good Contributions

Look at existing skills for examples:
- **skill-builder** - Complex skill with templates
- **Anthropic's skills repo** - https://github.com/anthropics/skills

## Thank You!

Your contributions help the entire Claude Code community. Thank you for sharing your skills!

---

**Ready to contribute?** Create your skill and submit a PR! 🚀
