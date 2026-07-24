# Security policy

## Public repository rules

- Never commit OAuth tokens, API keys, passwords, or Telegram bot tokens.
- Never commit a credential-enabled n8n export.
- Keep `.env` private; only `.env.example` belongs in Git.
- Use HTTPS for production approval webhooks.
- Restrict Google Sheets and Looker Studio sharing to the intended audience.
- Rotate any credential that was exposed in an earlier local export.

## This repository

The workflow templates in `workflows/` were sanitized. They contain explicit
`YOUR_...` placeholders and no n8n credential objects.

## Reporting a vulnerability

Open a private security advisory in the GitHub repository instead of publishing
a secret in a public issue.
