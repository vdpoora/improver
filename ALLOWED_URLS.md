# Allowed URLs

URL prefixes the agent is permitted to fetch via `./bin/fetch-url`.

The user owns this file. The agent requests additions via `PERMISSIONS_PENDING.md`; the user grants by appending here (and moving the pending block into `PERMISSIONS_GRANTED.md` for audit).

## Format

One bullet per allowed URL prefix. Must be `http://` or `https://`. The match rule is:

- scheme, host, and port must match exactly
- entry's path must be a prefix of the requested URL's path

Example:

- `https://api.example.com/v1/` allows any request under that path on that host
- `https://example.com/exact/file.json` allows only that exact path (and longer paths beginning with it, which usually doesn't apply for single files)

## Allowed prefixes

_(none yet)_
