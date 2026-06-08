# Pending permission requests

The agent appends requests here. The user reviews. To grant, move the block into `PERMISSIONS_GRANTED.md`. To deny, delete the block (optionally add a one-line `denied: <reason>` first so the agent learns).

Format:
```
## <ISO timestamp> — <short title>
- want to: <action>
- on: <path or resource>
- why: <one sentence>
- reversibility: <reversible | hard-to-reverse | destructive>
```

---

## 2026-06-08T08:17:21Z — improve ClaudeTools codebase
- want to: read and make improvements (refactor, fix bugs, enhance docs) to `/Users/vdpoora/src/ClaudeTools`
- on: /Users/vdpoora/src/ClaudeTools
- why: user inbox request to audit and improve this repo (scope: refactoring, bugs, features, docs).
- reversibility: reversible (all changes git-backed)

## 2026-06-08T08:17:21Z — improve claude-config codebase
- want to: read and make improvements (refactor, fix bugs, enhance docs) to `/Users/vdpoora/src/claude-config`
- on: /Users/vdpoora/src/claude-config
- why: user inbox request to audit and improve this repo and overall Claude configuration (scope: refactoring, bugs, features, docs).
- reversibility: reversible (all changes git-backed)
