---
name: github-actions-debug
description: >-
  Guide for debugging failing GitHub Actions workflows. Use this when asked to
  debug failing GitHub Actions workflows or CI/CD pipeline failures in a pull
  request or repository.
license: MIT
---

# GitHub Actions Debug

Systematically diagnose and fix failing GitHub Actions workflows using
GitHub MCP Server tools.

## Workflow

1. Use the `list_workflow_runs` tool to look up recent workflow runs for the
   pull request or repository and check their status.
2. Use the `get_job_logs` tool with `failed_only: true` to retrieve logs for
   all failed jobs in a workflow run.
3. Read the failure messages carefully to understand the root cause.
4. Attempt to reproduce the failure in the local environment when possible.
5. Apply a fix and verify the workflow succeeds by re-running it.

## Gotchas

- Always check that secrets and environment variables referenced in workflows
  are configured in the repository settings — missing secrets are a common
  cause of silent failures.
- `actions/checkout` defaults to a shallow clone; jobs that need full history
  must pass `fetch-depth: 0`.
- Workflow syntax errors surface only at runtime; validate YAML locally with
  `actionlint` before pushing.
- Matrix jobs can fail independently — examine each failed matrix leg's logs
  separately.
