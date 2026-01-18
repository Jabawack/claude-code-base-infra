# Claude Code Base Infrastructure

Production-ready Claude Code skills and agents for Next.js + React + Supabase projects.

## Two Ways to Use

### Option 1: Start a New Project

Clone this repo as your project foundation:

```bash
git clone <this-repo> my-project
cd my-project
/setup-hooks
```

`/setup-hooks` resets git history and installs hook dependencies.

### Option 2: Add to Existing Project

Copy the infrastructure to your existing codebase:

```bash
# From this repo directory
/init-infra-setup
```

This copies `.claude/` to your project, then run `/setup-hooks`.

For complete reference of all commands, skills, agents, and hooks, see [docs/cheatsheet.md](docs/cheatsheet.md).

---

## Stack

- **Runtime:** Node.js
- **Framework:** Next.js (App Router) + React
- **Language:** TypeScript
- **UI:** MUI (Material UI)
- **Database:** Supabase (PostgreSQL)
- **Deployment:** Vercel

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
- Use `/add-skill` to help refactor

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
│   ├── add-skill/              # Create/manage skills
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
| `add-skill` | "add skill", "create skill" | Skill management |
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
5. **Create skills** - Use add-skill

## Contributing

When adding to this template:
- Keep files under 500 lines
- Update skill-rules.json for new skills
- Add agents for specialized tasks
- Document in README

## License

MIT
