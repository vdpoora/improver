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
