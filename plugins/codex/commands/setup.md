---
description: Check whether the LLM is configured and ready, optionally toggle the stop-time review gate
argument-hint: '[--enable-review-gate|--disable-review-gate]'
allowed-tools: Bash(node:*), Bash(env:*), AskUserQuestion
---

Run:

```bash
node "${CLAUDE_PLUGIN_ROOT}/scripts/codex-companion.mjs" setup --json $ARGUMENTS
```

Environment variables required:
- `LLM_API_KEY` - API key for the LLM provider
- `LLM_API_BASE_URL` (optional) - Override the default API endpoint (defaults to https://api.anthropic.com)
- `LLM_MODEL` (optional) - Model to use (defaults to claude-sonnet-4-20250514)

If the result says LLM is not configured:
- Use `AskUserQuestion` to ask whether Claude should help configure the LLM.
- Options:
  - `Set LLM_API_KEY`
  - `Skip for now`

Output rules:
- Present the final setup output to the user.
- If setup was skipped, present the original setup output.