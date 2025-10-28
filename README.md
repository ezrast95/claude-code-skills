# Claude Code Skills Collection

A curated collection of skills for [Claude Code](https://claude.com/claude-code) to enhance your development workflow.

## What Are Skills?

Skills are specialized capabilities that extend Claude's functionality in Claude Code. Each skill is a self-contained package that Claude automatically discovers and uses when relevant to your task.

## Available Skills

### 🛠️ Meta Skills

#### [skill-builder](skills/meta/skill-builder/)
Interactive guide for creating well-structured Claude Code skills with best practices built-in.

**Use when:** Creating new skills, building automation tools, or generating skill templates

**Features:**
- Interactive discovery process with guided questions
- 4 skill templates (basic, analysis, generator, workflow)
- Best practices automatically applied
- Trigger-rich description generation
- Security and testing guidance included

**Activation triggers:** "create a skill", "build a skill", "make a new skill", "skill builder"

### 🔧 Utilities

More skills coming soon! Use **skill-builder** to create your own.

## Installation

### Install Individual Skills

```bash
# Clone the repository
git clone https://github.com/ezrast95/claude-code-skills.git

# Copy specific skill to your personal skills directory
cp -r claude-code-skills/skills/meta/skill-builder ~/.claude/skills/

# On Windows, use:
# xcopy /E /I claude-code-skills\skills\meta\skill-builder %USERPROFILE%\.claude\skills\skill-builder
```

### Install All Skills

```bash
# Clone the repository
git clone https://github.com/ezrast95/claude-code-skills.git

# Copy all skills (Linux/Mac)
find claude-code-skills/skills -mindepth 2 -maxdepth 2 -type d -exec cp -r {} ~/.claude/skills/ \;

# On Windows:
# for /d %G in ("claude-code-skills\skills\*\*") do xcopy /E /I "%G" "%USERPROFILE%\.claude\skills\%~nxG"
```

### Verify Installation

Start a new Claude Code session and the skills should be automatically available. Try:
- "Help me create a new skill" (should activate skill-builder)

## Usage Examples

### Creating a New Skill with skill-builder

```
You: "Help me create a skill for analyzing Python code quality"

Claude: [skill-builder activates]
- Asks about your workflow
- Helps design trigger-rich descriptions
- Generates complete skill structure
- Creates files in correct location
- Provides testing guidance
```

## Creating Your Own Skills

### Quick Start

Use the **skill-builder** skill:
```
"Help me create a skill for [your workflow]"
```

### Manual Creation

1. Create a directory: `~/.claude/skills/your-skill-name/`
2. Add `SKILL.md` with YAML frontmatter:

```yaml
---
name: your-skill-name
description: What it does and when to use it with trigger words
version: 1.0.0
---

# Your Skill Name

[Instructions for Claude...]
```

See [docs/creating-skills.md](docs/creating-skills.md) for detailed guidance.

## Skill Categories

### 📁 Repository Structure

```
skills/
├── meta/          # Tools for building/managing skills
├── utilities/     # General purpose utilities
├── analysis/      # Code analysis and review
├── generators/    # Code/content generation
├── workflows/     # Multi-step automation
└── integrations/  # External API/service connections
```

As this collection grows, skills will be organized into these categories.

## Contributing

Contributions are welcome! Here's how:

1. **Fork this repository**
2. **Create a new skill** using skill-builder or manually
3. **Test thoroughly** - ensure it activates correctly
4. **Submit a Pull Request** with:
   - Skill in appropriate category directory
   - Updated README with skill description
   - Clear activation triggers documented

See [docs/contributing.md](docs/contributing.md) for detailed guidelines.

## Documentation

- [Installation Guide](docs/installation.md) - Detailed installation instructions
- [Creating Skills Guide](docs/creating-skills.md) - How to build skills with skill-builder
- [Contributing Guide](docs/contributing.md) - How to contribute new skills

## Requirements

- [Claude Code](https://claude.com/claude-code) installed
- For Python-based skills: Python 3.8+
- For Node.js-based skills: Node.js 16+

## Resources

- [Official Claude Code Skills Documentation](https://docs.claude.com/en/docs/claude-code/skills.md)
- [Anthropic's Official Skills Repository](https://github.com/anthropics/skills)
- [Claude Code Documentation](https://docs.claude.com/en/docs/claude-code)

## License

MIT License - see [LICENSE](LICENSE) for details

## Author

Created by [@ezrast95](https://github.com/ezrast95)

## Acknowledgments

- Inspired by [Anthropic's official skills repository](https://github.com/anthropics/skills)
- Built with [Claude Code](https://claude.com/claude-code)

---

**⭐ If you find these skills useful, please star this repository!**

**🔧 Have an idea for a skill?** Open an issue or use skill-builder to create it!
