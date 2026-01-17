# Activation Rules Guide

## skill-rules.json Structure

```json
{
  "skills": {
    "skill-name": {
      "description": "What this skill does",
      "triggers": {
        "prompt": ["keyword1", "keyword2"],
        "files": ["path/**/*", "*.ext"]
      },
      "enforcement": "suggest",
      "priority": 1
    }
  },
  "globalSettings": { ... }
}
```

## Trigger Types

### Prompt Triggers
Keywords that activate the skill when found in user prompts.

```json
"prompt": [
  "api",           // Single word
  "create route",  // Phrase
  "help me with"   // Partial match
]
```

**Best Practices:**
- Use lowercase (matching is case-insensitive)
- Include common variations
- Avoid overly generic terms
- Test for false positives

### File Triggers
Glob patterns that activate when user works with matching files.

```json
"files": [
  "app/api/**/*",     // All files in api directory
  "**/*.test.ts",     // All test files
  "lib/auth.ts"       // Specific file
]
```

**Supported Patterns:**
- `*` - Match any characters except `/`
- `**` - Match any characters including `/`
- `?` - Match single character
- `[abc]` - Match character class

## Enforcement Levels

### auto
Skill activates immediately without confirmation.
```json
"enforcement": "auto"
```
Use for: Critical skills, development standards

### suggest
Suggests activation, user confirms.
```json
"enforcement": "suggest"
```
Use for: Most skills, optional guidelines

### manual
Only activates when explicitly called.
```json
"enforcement": "manual"
```
Use for: Specialized tools, rarely needed skills

## Priority System

Lower number = higher priority (activates first).

```json
"priority": 0  // Critical (skill-developer)
"priority": 1  // Core (backend, frontend guidelines)
"priority": 2  // Supporting (testing, error tracking)
```

## Global Settings

```json
"globalSettings": {
  "maxSkillsPerPrompt": 3,      // Limit concurrent suggestions
  "defaultEnforcement": "suggest",
  "showSkillSuggestions": true,
  "logActivations": true
}
```

## Testing Activation Rules

1. Create test prompts that should trigger
2. Create test prompts that should NOT trigger
3. Verify file pattern matching
4. Check priority ordering
