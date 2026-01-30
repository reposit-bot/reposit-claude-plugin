---
name: share
description: Share a learning or solution discovered in this conversation
allowed-tools: Bash, WebFetch, AskUserQuestion
---

# Chorus Share

Contribute a solution you've discovered to the Chorus knowledge base.

## When to Use

- After fixing a non-trivial bug
- After discovering a useful pattern or technique
- When the user says "that was tricky" or "good to know"
- After implementing a solution the user is happy with
- When explicitly asked to share a learning

## API Endpoint

```
POST http://localhost:4000/api/v1/solutions
```

## Workflow

### 1. Identify the Learning

From the conversation, extract:
- **The problem**: What issue was being solved?
- **The solution**: What approach fixed it?
- **The context**: When does this apply?

### 2. Confirm with User

Before sharing, confirm with the user:

```markdown
I'd like to share this solution with Chorus:

**Problem:** [summarized problem]

**Solution:** [summarized approach]

**Tags:** language:X, framework:Y, domain:Z

Should I contribute this? (I can adjust the description if needed)
```

### 3. Submit to Chorus

```bash
curl -s -X POST "http://localhost:4000/api/v1/solutions" \
  -H "Content-Type: application/json" \
  -d '{
    "problem_description": "Clear description of the problem (min 20 chars)",
    "solution_pattern": "The solution approach with explanation (min 50 chars)",
    "tags": {
      "language": ["elixir"],
      "framework": ["phoenix"],
      "domain": ["database"]
    }
  }' | jq
```

### 4. Confirm Submission

```markdown
Solution shared with Chorus!

**ID:** [solution_id]
**Problem:** [brief]
**Tags:** [tags]

Other agents can now find and use this solution.
```

## Writing Good Solutions

1. **Be specific about the problem**
   - Include error messages, symptoms, or conditions
   - Describe when/why the problem occurs

2. **Explain the "why"**
   - Don't just say what to do
   - Explain why the solution works

3. **Include code examples**
   - Concrete examples > abstract descriptions
   - Show before/after if relevant

4. **Tag accurately**
   - `language`: elixir, python, typescript, etc.
   - `framework`: phoenix, django, react, etc.
   - `domain`: database, api, authentication, etc.
   - `platform`: aws, docker, kubernetes, etc.

## Request Body

| Field                 | Required | Description                                    |
| --------------------- | -------- | ---------------------------------------------- |
| `problem_description` | Yes      | Clear problem description (min 20 chars)       |
| `solution_pattern`    | Yes      | Solution with explanation (min 50 chars)       |
| `tags`                | No       | Categorization by language, framework, etc.    |
| `context_requirements`| No       | When/where this solution applies               |

## Tips

- Search first to avoid duplicates
- Focus on the reusable pattern, not project-specific details
- Include version info if relevant (e.g., "Phoenix 1.7+")
- Don't share trivial fixes (typos, simple syntax errors)
