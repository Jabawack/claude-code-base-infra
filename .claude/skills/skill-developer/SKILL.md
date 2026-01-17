# Skill Developer

Create, manage, and refactor Claude Code skills following the 500-line modular pattern.

## Activation

This skill activates automatically when you:
- Say "help me to add skill [name]"
- Say "create skill", "new skill", "add skill"
- Work with files in `.claude/skills/`

## Core Principles

### The 500-Line Rule
Every file must stay under 500 lines. When exceeded:
1. Split into modular components
2. Create resource files for detailed content
3. Use SKILL.md as the orchestrator, not the container

### Skill Structure
```
.claude/skills/[skill-name]/
├── SKILL.md           # Main skill file (under 500 lines)
└── resources/         # Detailed resource files
    ├── core-concepts.md
    ├── patterns.md
    └── examples.md
```

## Creating a New Skill

### Step 1: Define the Skill
```bash
mkdir -p .claude/skills/[skill-name]/resources
```

### Step 2: Create SKILL.md Template
```markdown
# [Skill Name]

[One-line description]

## Activation
[When this skill should activate]

## Core Concepts
[Brief overview, link to resources/core-concepts.md for details]

## Key Patterns
[Brief overview, link to resources/patterns.md for details]

## Commands
- /[skill-name] - Activate this skill
- /[skill-name]:help - Show help

## Resources
- See `resources/` for detailed documentation
```

### Step 3: Update skill-rules.json
Add your skill to `.claude/skills/skill-rules.json`:
```json
"your-skill-name": {
  "description": "Brief description",
  "triggers": {
    "prompt": ["keyword1", "keyword2"],
    "files": ["path/pattern/**/*"]
  },
  "enforcement": "suggest",
  "priority": 2
}
```

## Enforcement Levels

| Level | Behavior |
|-------|----------|
| `auto` | Activates without user confirmation |
| `suggest` | Suggests activation, user decides |
| `manual` | Only activates when explicitly called |

## Resource File Patterns

### core-concepts.md
- Fundamental concepts
- Key terminology
- Architecture overview

### patterns.md
- Code patterns with examples
- Best practices
- Anti-patterns to avoid

### examples.md
- Real-world usage examples
- Copy-paste ready snippets
- Integration examples

## Refactoring Existing Skills

When a skill exceeds 500 lines:

1. **Identify sections** that can be extracted
2. **Create resource files** for each major section
3. **Update SKILL.md** to reference resources
4. **Keep SKILL.md** as the quick-reference guide

### Before (Monolithic)
```markdown
# My Skill
[... 600+ lines of content ...]
```

### After (Modular)
```markdown
# My Skill
## Overview
[Brief intro]

## Quick Reference
[Essential info only]

## Detailed Resources
- `resources/setup.md` - Detailed setup guide
- `resources/patterns.md` - All patterns with examples
- `resources/troubleshooting.md` - Common issues
```

## Skill Activation Flow

```
User Prompt
    ↓
UserPromptSubmit Hook
    ↓
Analyze prompt keywords
    ↓
Check file context
    ↓
Match against skill-rules.json
    ↓
Apply enforcement level
    ↓
Activate or Suggest skill
```

## Commands

- `/skill-developer` - Activate this skill
- `/skill-developer:create [name]` - Create new skill scaffold
- `/skill-developer:refactor [name]` - Refactor existing skill

## Resources

See `resources/` folder for:
- `skill-structure.md` - Detailed structure guide
- `activation-rules.md` - Rule configuration guide
- `modular-patterns.md` - Modularization patterns
- `best-practices.md` - Best practices checklist
