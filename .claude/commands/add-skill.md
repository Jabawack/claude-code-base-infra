# /add-skill

Create a new skill using the skill-developer template.

## Usage

```
/add-skill [skill-name]
/add-skill api-caching
```

## What This Command Does

1. Creates skill directory structure
2. Generates SKILL.md from template
3. Creates resources folder
4. Updates skill-rules.json

## Generated Structure

```
.claude/skills/[skill-name]/
├── SKILL.md           # Main skill file
└── resources/         # Resource files directory
    └── .gitkeep
```

## SKILL.md Template

```markdown
# [Skill Name]

[Brief description]

## Activation

This skill activates when you:
- [Trigger condition 1]
- [Trigger condition 2]

## Quick Reference

[Essential information in table/list format]

## Core Concepts

[Brief overview]

## Commands

- `/[skill-name]` - Activate this skill
- `/[skill-name]:help` - Show help

## Resources

See `resources/` for detailed documentation.
```

## skill-rules.json Entry

```json
"[skill-name]": {
  "description": "[Description]",
  "triggers": {
    "prompt": ["keyword1", "keyword2"],
    "files": ["path/pattern/**/*"]
  },
  "enforcement": "suggest",
  "priority": 2
}
```

## Post-Creation Steps

After creating a skill:

1. **Edit SKILL.md** - Add specific content
2. **Update triggers** - Customize in skill-rules.json
3. **Add resources** - Create resource files as needed
4. **Test activation** - Verify skill triggers correctly

## Examples

```bash
# Create a caching skill
/add-skill api-caching

# Create a deployment skill
/add-skill vercel-deployment

# Create a testing skill
/add-skill e2e-testing
```

## 500-Line Rule

Remember:
- SKILL.md should stay under 500 lines
- Split detailed content into resources/
- Use links to connect related content
