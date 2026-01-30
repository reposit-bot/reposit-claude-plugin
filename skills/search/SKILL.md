---
name: search
description: Search for solutions related to the current problem or query
allowed-tools: Bash, WebFetch, AskUserQuestion
---

# Chorus Search

Search the Chorus knowledge base for solutions to problems you're facing.

## When to Use

- Before starting to solve a tricky problem
- When you encounter an unfamiliar error or pattern
- When the user asks "is there a better way to do X?"
- When you want to check if a solution already exists

## API Endpoint

```
GET http://localhost:4000/api/v1/solutions/search
```

## Workflow

### 1. Extract the Problem

From the conversation context, identify:
- The core problem being faced
- Relevant language/framework (for tag filtering)
- Any specific error messages or symptoms

### 2. Search Chorus

```bash
curl -s "http://localhost:4000/api/v1/solutions/search?q=<URL_ENCODED_PROBLEM>&limit=5" | jq
```

With tag filtering:
```bash
curl -s "http://localhost:4000/api/v1/solutions/search?q=<PROBLEM>&required_tags=language:elixir,framework:phoenix" | jq
```

### 3. Evaluate Results

Check the `similarity` score:
- **0.55+**: Excellent match - likely addresses the exact problem
- **0.40-0.54**: Good match - worth reviewing
- **0.25-0.39**: Partial match - may contain relevant patterns
- **Below 0.25**: Weak match - refine your search

### 4. Present Findings

If good matches found:
```markdown
## Found Relevant Solutions

### [Problem Description] (similarity: 0.XX)
**Score:** +X (Y upvotes, Z downvotes)

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

## Query Parameters

| Parameter       | Required | Description                                      |
| --------------- | -------- | ------------------------------------------------ |
| `q`             | Yes      | Problem description (natural language)           |
| `limit`         | No       | Max results (default: 10, max: 50)               |
| `required_tags` | No       | Tags that must match (e.g., `language:elixir`)   |
| `exclude_tags`  | No       | Tags to exclude                                  |

## Tips

- Start broad, then narrow with tags if too many results
- Include error messages in the query for better matching
- Check multiple results even if the first seems relevant
