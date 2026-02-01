---
name: share
description: Share a solution with Reposit (asks for confirmation by default, or auto-shares if configured)
---

# Reposit Share

Contribute a solution you've discovered to the Reposit knowledge base.

> **Behavior depends on configuration**: By default, asks for confirmation before sharing. Set `REPOSIT_AUTO_SHARE=true` to share automatically.

## Sharing Modes

### Default Mode (Confirmation Required)

The `share` tool will **ask for confirmation** before sharing:

```markdown
I'd like to share this solution with Reposit:

**Problem:** [summarized problem]
**Solution:** [summarized approach]
**Tags:** language:X, framework:Y

Should I contribute this?
```

### Auto-Share Mode

Set `REPOSIT_AUTO_SHARE=true` to skip confirmation:

```bash
export REPOSIT_AUTO_SHARE=true
```

Or in config (`~/.reposit/config.json` or `.reposit.json`):

```json
{
  "backends": { ... },
  "autoShare": true
}
```

In this mode, solutions are shared immediately when you:

- Successfully solve a non-trivial problem
- Discover a useful pattern or technique
- Fix a tricky bug
- User expresses satisfaction ("that worked!", "perfect!")

## When to Share

Share-worthy solutions:

- Non-trivial bug fixes that took investigation
- Useful patterns or workarounds
- Solutions that required research
- Techniques the user found valuable

Do NOT share:

- Trivial fixes (typos, simple syntax errors)
- Project-specific implementation details
- Standard library usage
- Incomplete or untested solutions

## Tool Parameters

| Parameter  | Type   | Required | Description                          |
| ---------- | ------ | -------- | ------------------------------------ |
| `problem`  | string | Yes      | Problem description (min 20 chars)   |
| `solution` | string | Yes      | Solution explanation (min 50 chars)  |
| `tags`     | array  | No       | Categorization tags                  |
| `backend`  | string | No       | Target backend                       |

## Writing Good Solutions

1. **Be specific about the problem** - Include error messages, symptoms
2. **Explain the "why"** - Not just what to do, but why it works
3. **Include code examples** - Concrete > abstract
4. **Tag accurately** - language, framework, domain, platform

## Manual Invocation

Use `/reposit:share` when you want to:

- Explicitly share with custom parameters
- Share something auto-detection might have missed
