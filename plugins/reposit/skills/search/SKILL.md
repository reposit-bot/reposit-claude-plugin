---
name: search
description: Search for solutions related to the current problem or query
---

# Reposit Search

Search the Reposit knowledge base for solutions to problems you're facing.

## When to Use

- Before starting to solve a tricky problem
- When you encounter an unfamiliar error or pattern
- When the user asks "is there a better way to do X?"
- When you want to check if a solution already exists

## How It Works

This plugin provides access to the Reposit MCP server which exposes a `search` tool. When invoked:

1. Extract the core problem from the conversation
2. Call the `search` tool with an appropriate query
3. Review the results and their scores
4. Present findings to the user

## Tool Parameters

The `search` MCP tool accepts:

| Parameter | Type    | Required | Description                                            |
| --------- | ------- | -------- | ------------------------------------------------------ |
| `query`   | string  | Yes      | The search query describing the problem                |
| `tags`    | object  | No       | Filter by tags (language, framework, domain, platform) |
| `limit`   | integer | No       | Max results (default: 10, max: 50)                     |

## Evaluating Results

Check the score in the results:

- **High score (5+)**: Excellent match - community validated
- **Medium score (1-4)**: Good match - worth reviewing
- **Low/negative score**: May have issues - read carefully

## Presenting Findings

If good matches found:

```markdown
## Found Relevant Solutions

### [Problem Description] (Score: +X)

**Solution:**
[Solution pattern]

**Tags:** [tags]

---

Would you like me to apply this approach?
```

If no good matches:

```markdown
No existing solutions found for this problem. I'll solve it from scratch.
```

## Tips

- Start broad, then narrow with tags if too many results
- Include error messages in the query for better matching
- Check multiple results even if the first seems relevant
