# ClipFlow Security Plan

## Secrets

- Never store API keys, OAuth tokens, or secrets in source code.
- Never commit `.env` files.
- Use environment variables in local development.
- Use a managed secret manager in production.
- Rotate credentials if they are exposed.

## OAuth tokens

- Store access tokens encrypted at rest.
- Store refresh tokens encrypted at rest.
- Use short-lived access tokens where possible.
- Refresh tokens only when needed.
- Store only the minimum necessary scopes.
- Invalidate tokens when a user disconnects an account.

## Duplicate prevention

- Use `(source_platform, source_clip_id)` as a unique key.
- Check for an existing publication before uploading.
- Use database transactions or idempotency keys for upload operations.

## Logging

- Do not log OAuth tokens.
- Do not log API keys.
- Do not log full user personal data.
- Log clip IDs, platform, status, timestamps, and error codes.

## API safety

- Validate all incoming URLs.
- Restrict accepted Kick and Twitch URL formats.
- Apply rate limiting to public endpoints.
- Use HTTPS everywhere.
- Use least-privilege OAuth scopes.
- Handle API failures with retries and exponential backoff.
