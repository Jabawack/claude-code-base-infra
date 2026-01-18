# /setup-hooks

Complete setup for Claude Code infrastructure.

## Usage

```
/setup-hooks
```

## What to Run

**Check and run these commands:**

```bash
# 1. If .git exists and is template repo (has claude-code-base-infra commits), reset it:
if [ -d .git ] && git log --oneline | grep -q "Initial commit: Claude Code"; then
  rm -rf .git && git init
  echo "Git reset complete"
fi

# 2. Install hook dependencies:
cd .claude/hooks && npm install
```

## One-liner (if you know you need full reset)

```bash
rm -rf .git && git init && cd .claude/hooks && npm install
```

## When to Use

| Scenario | What Happens |
|----------|--------------|
| Just cloned template | Resets git + installs deps |
| Existing project with .claude/ copied | Only installs deps |
| Already set up | Just reinstalls deps |
