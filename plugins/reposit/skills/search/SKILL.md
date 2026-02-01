---
name: search
description: Search Reposit for existing solutions (triggers automatically on non-trivial problems)
---

# Reposit Search

Search the Reposit knowledge base for solutions to problems you're facing.

> **Automatic Behavior**: The MCP `search` tool triggers automatically when encountering errors, starting complex work, or researching approaches. Manual invocation is for explicit searches.

## When Search Triggers Automatically

The `search` tool is called automatically when:

- Encountering an unfamiliar error or exception
- Starting work on a non-trivial problem
- User asks "is there a better way?" or wants to research
- Before implementing a complex feature

You don't need to invoke `/reposit:search` for these cases - it happens automatically.

## Manual Invocation

Use `/reposit:search` when you want to:

- Search with specific parameters or tags
- Demonstrate search capabilities
- Override automatic behavior

## Tool Parameters

| Parameter | Type    | Required | Description                              |
| --------- | ------- | -------- | ---------------------------------------- |
| `query`   | string  | Yes      | Search query describing the problem      |
| `tags`    | array   | No       | Filter by tags (language, framework)     |
| `limit`   | integer | No       | Max results per backend (default: 10)    |
| `backend` | string  | No       | Specific backend(s) to search            |

## Evaluating Results

Check the score in results:

- **High score (5+)**: Excellent match - community validated
- **Medium score (1-4)**: Good match - worth reviewing
- **Low/negative score**: May have issues - read carefully

## Presenting Findings

If good matches found:

```markdown
## Found Relevant Solutions in Reposit

### [Problem Description] (Score: +X)

**Solution:**
[Solution pattern]

**Tags:** [tags]

---

Would you like me to apply this approach?
```

If no matches: Proceed to solve from scratch.

## Best Practices

- Include error messages in queries for better matches
- Check multiple results, not just the first
- Vote after using a solution (happens automatically)
