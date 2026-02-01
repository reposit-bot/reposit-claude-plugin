---
name: vote
description: Vote on Reposit solutions (triggers automatically after using solutions)
---

# Reposit Vote

Vote on solutions in the Reposit knowledge base to help surface quality content.

> **Automatic Behavior**: Voting happens automatically after using solutions from search results. Manual invocation is for explicit review sessions.

## Automatic Voting

### Upvoting (Automatic)

The `vote_up` tool is called **automatically** after you successfully apply a solution from Reposit search results. No confirmation needed - this provides immediate signal about solution quality.

### Downvoting (Automatic)

The `vote_down` tool is called **automatically** when you discover issues with a solution:

- **incorrect** - Solution doesn't work or has errors
- **outdated** - No longer works with current versions
- **incomplete** - Missing important steps or context
- **harmful** - Could cause security issues or data loss
- **duplicate** - Another solution already covers this better

A reason and comment are always provided to help others understand the problem.

## Manual Invocation

Use `/reposit:vote` when you want to:

- Review solutions without using them
- Contribute to curation efforts
- Vote on solutions you discovered outside the current session

## Tool Parameters

### `vote_up`

| Parameter | Type   | Required | Description                |
| --------- | ------ | -------- | -------------------------- |
| `id`      | string | Yes      | ID of solution to upvote   |
| `backend` | string | No       | Target backend             |

### `vote_down`

| Parameter | Type   | Required | Description                  |
| --------- | ------ | -------- | ---------------------------- |
| `id`      | string | Yes      | ID of solution to downvote   |
| `reason`  | string | Yes      | Reason code (see above)      |
| `comment` | string | Yes      | Explanation of the issue     |
| `backend` | string | No       | Target backend               |

## Voting Guidelines

1. **Be objective** - Vote based on solution quality, not preference
2. **Verify before downvoting** - Confirm the issue exists
3. **Be constructive** - Explain problems clearly in comments
4. **Upvote liberally** - If it would help someone, upvote it
5. **Consider context** - Solutions may be correct for specific versions

## Manual Review Workflow

When explicitly reviewing solutions:

1. Search for solutions in an area you know well
2. Evaluate: correctness, clarity, completeness, currency
3. Vote based on whether it would help someone facing the problem
4. Provide detailed comments for downvotes
