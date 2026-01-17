# Claude Code Base Infrastructure

A production-ready Claude Code skills and agents template for Next.js + React + Supabase projects.

## Stack

- **Runtime:** Node.js
- **Framework:** Next.js (App Router) + React
- **Language:** TypeScript
- **UI:** MUI (Material UI)
- **Database:** Supabase (PostgreSQL)
- **Deployment:** Vercel

## Quick Start

1. **Copy to your project**
   ```bash
   cp -r .claude/ /path/to/your/project/
   ```

2. **Install hook dependencies**
   ```bash
   npm install -D ts-node @types/node
   ```

3. **Verify setup**
   ```bash
   # Skills should auto-suggest when working
   # Try mentioning "api route" or "component"
   ```

## Key Features

### Auto-Skill Activation
Skills activate automatically based on:
- **Prompt analysis** - Keywords trigger relevant skills
- **File context** - Working files determine suggestions
- **skill-rules.json** - Configurable activation rules

### 500-Line Rule
Every file stays under 500 lines:
- SKILL.md files are quick references
- Detailed content goes in `resources/`
- Use `/skill-developer` to help refactor

### UserPromptSubmit Hook
The hook automatically:
1. Analyzes your prompt
2. Checks file context
3. Suggests relevant skills
4. Activates based on enforcement level

## Repository Structure

```
.claude/
├── skills/                     # 5 Production Skills
│   ├── backend-dev-guidelines/ # API, Supabase, server patterns
│   ├── frontend-dev-guidelines/# React, MUI, client patterns
│   ├── skill-developer/        # Create/manage skills
│   ├── route-tester/           # API endpoint testing
│   ├── error-tracking/         # Error handling, debugging
│   └── skill-rules.json        # Activation configuration
│
├── hooks/                      # Automation Hooks
│   ├── skill-activation-prompt.ts  # UserPromptSubmit hook
│   ├── post-tool-use-tracker.sh    # 500-line enforcement
│   └── tsc-check.sh                # TypeScript checks
│
├── agents/                     # 10 Specialized Agents
│   ├── code-architecture-reviewer.md
│   ├── refactor-planner.md
│   ├── frontend-error-fixer.md
│   ├── documentation-architect.md
│   ├── plan-reviewer.md
│   ├── web-research-specialist.md
│   ├── auth-route-tester.md
│   ├── auth-route-debugger.md
│   ├── auto-error-resolver.md
│   └── code-refactor-master.md
│
├── commands/                   # Slash Commands
│   ├── dev-docs.md            # Development documentation
│   ├── add-skill.md           # Create new skills
│   └── route-test.md          # Quick API testing
│
└── settings.json              # Hook and permission config

dev/
└── active/                    # Active development docs
```

## Skills Overview

| Skill | Triggers | Purpose |
|-------|----------|---------|
| `backend-dev-guidelines` | api, route, supabase, database | Server-side patterns |
| `frontend-dev-guidelines` | component, react, mui, hook | Client-side patterns |
| `skill-developer` | "add skill", "create skill" | Skill management |
| `route-tester` | test route, test api, endpoint | API testing |
| `error-tracking` | error, bug, fix, debug | Error handling |

## Adding New Skills

Say "help me to add skill [name]" or use:

```bash
/add-skill [skill-name]
```

This will:
1. Create skill directory
2. Generate SKILL.md template
3. Update skill-rules.json
4. Create resources folder

## Enforcement Levels

| Level | Behavior |
|-------|----------|
| `auto` | Activates without asking |
| `suggest` | Suggests activation |
| `manual` | Only when explicitly called |

Configure in `skill-rules.json`:
```json
"skill-name": {
  "enforcement": "suggest"
}
```

## Agents Usage

Invoke agents with `@agent`:

```
@agent code-architecture-reviewer
Review the authentication implementation

@agent refactor-planner
Plan splitting user.service.ts

@agent frontend-error-fixer
Fix: Hydration mismatch in UserProfile
```

## Commands

| Command | Description |
|---------|-------------|
| `/dev-docs` | Manage development docs |
| `/add-skill [name]` | Create new skill |
| `/route-test [method] [path]` | Test API endpoints |

## Customization

### Add Prompt Triggers
Edit `skill-rules.json`:
```json
"triggers": {
  "prompt": ["your", "keywords", "here"]
}
```

### Add File Triggers
```json
"triggers": {
  "files": ["your/path/**/*", "*.extension"]
}
```

### Adjust Priority
Lower number = higher priority:
```json
"priority": 0  // Activates first
"priority": 2  // Activates later
```

## Development Workflow

1. **Start working** - Skills auto-suggest
2. **Follow guidelines** - Skills provide patterns
3. **Test routes** - Use route-tester
4. **Fix errors** - Error-tracking helps
5. **Create skills** - Use skill-developer

## Contributing

When adding to this template:
- Keep files under 500 lines
- Update skill-rules.json for new skills
- Add agents for specialized tasks
- Document in README

## License

MIT
