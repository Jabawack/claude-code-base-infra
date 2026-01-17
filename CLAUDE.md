# Claude Code Project Configuration

This file provides context to Claude Code about this project.

## Project Type
Claude Code Skills and Agents Template for Next.js/React/Supabase projects.

## Key Conventions

### 500-Line Rule
- No file should exceed 500 lines
- Split large files into modular resources
- Use `/skill-developer` for refactoring guidance

### Skill Structure
```
.claude/skills/[name]/
├── SKILL.md        # Max 500 lines, quick reference
└── resources/      # Detailed content, split by topic
```

### Auto-Activation
Skills activate based on:
1. Prompt keywords (from skill-rules.json)
2. File context (glob patterns)
3. Enforcement level (auto/suggest/manual)

## Stack Reference
- Runtime: Node.js
- Framework: Next.js (App Router)
- UI: React + MUI
- Database: Supabase
- Language: TypeScript
- Deployment: Vercel

## Common Tasks

### Add a New Skill
"Help me to add skill [name]" triggers skill-developer

### Test API Routes
Use `/route-tester` or "test api endpoint"

### Debug Errors
"Error" or "debug" triggers error-tracking skill

### Review Code
Use `@agent code-architecture-reviewer`

## File Organization
```
.claude/
├── skills/       # Skill definitions
├── hooks/        # Automation hooks
├── agents/       # Specialized agents
├── commands/     # Slash commands
└── settings.json # Configuration
```
