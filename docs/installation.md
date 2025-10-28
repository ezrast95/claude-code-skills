# Installation Guide

Complete guide for installing Claude Code skills from this repository.

## Prerequisites

- [Claude Code](https://claude.com/claude-code) installed and configured
- Git installed on your system
- Command line access (Terminal, PowerShell, or Command Prompt)

## Installation Methods

### Method 1: Individual Skill Installation (Recommended)

Install only the skills you need.

#### Linux/Mac

```bash
# Clone the repository
git clone https://github.com/ezrast95/claude-code-skills.git

# Navigate to repository
cd claude-code-skills

# Copy specific skill
cp -r skills/meta/skill-builder ~/.claude/skills/

# Verify installation
ls ~/.claude/skills/skill-builder
```

#### Windows (PowerShell)

```powershell
# Clone the repository
git clone https://github.com/ezrast95/claude-code-skills.git

# Navigate to repository
cd claude-code-skills

# Copy specific skill
xcopy /E /I skills\meta\skill-builder $env:USERPROFILE\.claude\skills\skill-builder

# Verify installation
dir $env:USERPROFILE\.claude\skills\skill-builder
```

### Method 2: Install All Skills

Install every skill in the collection.

#### Linux/Mac

```bash
# Clone the repository
git clone https://github.com/ezrast95/claude-code-skills.git
cd claude-code-skills

# Copy all skills
find skills -mindepth 2 -maxdepth 2 -type d -exec cp -r {} ~/.claude/skills/ \;

# Verify installation
ls ~/.claude/skills/
```

#### Windows (PowerShell)

```powershell
# Clone the repository
git clone https://github.com/ezrast95/claude-code-skills.git
cd claude-code-skills

# Copy all skills
Get-ChildItem -Path skills\*\* -Directory | ForEach-Object {
    xcopy /E /I $_.FullName "$env:USERPROFILE\.claude\skills\$($_.Name)"
}

# Verify installation
dir $env:USERPROFILE\.claude\skills\
```

### Method 3: Install as Project Skills

Install skills for a specific project (shared with your team via git).

```bash
# Navigate to your project
cd /path/to/your/project

# Clone or copy specific skill
cp -r /path/to/claude-code-skills/skills/meta/skill-builder .claude/skills/

# Commit to version control
git add .claude/skills/skill-builder
git commit -m "Add skill-builder skill"
git push
```

Team members will automatically get the skill when they pull the repository.

## Verifying Installation

### Check Skill Files

**Linux/Mac:**
```bash
ls -la ~/.claude/skills/
```

**Windows:**
```powershell
dir $env:USERPROFILE\.claude\skills\
```

You should see directories for each installed skill.

### Test Skill Activation

Start a new Claude Code session and try:

**For skill-builder:**
```
"Help me create a new skill"
```

Claude should recognize the request and activate the skill-builder, asking you questions about your workflow.

## Updating Skills

### Pull Latest Changes

```bash
cd claude-code-skills
git pull origin main

# Re-copy updated skills
cp -r skills/meta/skill-builder ~/.claude/skills/
```

### Subscribe to Updates

Watch this repository on GitHub to get notified of new skills and updates.

## Troubleshooting

### Skill Not Activating

**Problem:** Claude doesn't recognize your skill request

**Solutions:**
1. Verify SKILL.md exists in the correct location:
   - Personal: `~/.claude/skills/skill-name/SKILL.md`
   - Project: `.claude/skills/skill-name/SKILL.md`

2. Check YAML frontmatter is valid:
   ```yaml
   ---
   name: skill-name
   description: Clear description with trigger words
   ---
   ```

3. Try using exact trigger words from the skill's description

4. Restart your Claude Code session

### Permission Errors (Linux/Mac)

**Problem:** "Permission denied" when copying files

**Solution:**
```bash
# Ensure .claude directory exists and has correct permissions
mkdir -p ~/.claude/skills
chmod 755 ~/.claude/skills
```

### Path Issues (Windows)

**Problem:** Skills not found after installation

**Solution:**
1. Verify .claude directory location:
   ```powershell
   echo $env:USERPROFILE\.claude\skills
   ```

2. Ensure directory exists:
   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills"
   ```

### Dependencies Missing

**Problem:** Skill requires packages not installed

**Solution:**

**Python dependencies:**
```bash
pip install package-name==version
```

**Node.js dependencies:**
```bash
npm install package-name@version
```

Check skill's SKILL.md file for required dependencies in YAML frontmatter.

## Uninstalling Skills

### Remove Individual Skill

**Linux/Mac:**
```bash
rm -rf ~/.claude/skills/skill-name
```

**Windows:**
```powershell
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\skills\skill-name"
```

### Remove All Skills from This Repository

```bash
# List skills first to verify
ls ~/.claude/skills/

# Remove each one
rm -rf ~/.claude/skills/skill-builder
# ... repeat for other skills
```

## Best Practices

1. **Start with skill-builder** - It helps you create custom skills easily
2. **Install selectively** - Only install skills you'll actually use
3. **Keep updated** - Pull latest changes regularly for bug fixes and improvements
4. **Test before sharing** - If using project skills, test locally first
5. **Document custom skills** - Use skill-builder to generate proper documentation

## Getting Help

- [Creating Skills Guide](creating-skills.md) - Learn to build your own skills
- [Contributing Guide](contributing.md) - Share your skills with the community
- [GitHub Issues](https://github.com/ezrast95/claude-code-skills/issues) - Report problems or request features
- [Claude Code Documentation](https://docs.claude.com/en/docs/claude-code) - Official documentation

## Next Steps

After installation:

1. **Test skill-builder**: `"Help me create a skill for [your workflow]"`
2. **Create your first custom skill** using skill-builder
3. **Share feedback** - Open an issue with suggestions or improvements
4. **Contribute** - Submit your own skills via Pull Request

Happy coding! 🚀
