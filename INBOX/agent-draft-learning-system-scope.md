# Question: Learning & Improvement Analysis System — Scope & Output Mode

**Context:** The agent's foundational goals are now active and stable (cost tracking, memory hygiene, vault liaison, grant lifecycle, goal outcome capture). Two proposed goals remain:

1. **Build learning & improvement analysis system** — analyze patterns from agent runs and interactive Claude Code sessions to improve tool usage, cost trends, decision quality.
2. **Memory utility tracking** — review memory files for usage patterns and prune stale entries.

The learning system is the more complex one and blocks progress on both memory utility tracking (which feeds into it) and potentially future agent self-modification (which it would inform). Before activation, its scope needs clarification.

## Three questions for you:

1. **Data source**: Should the system analyze only agent runs (the improver.jsonl logs), or also interactive Claude Code sessions in other repos (ClaudeTools, claude-config, Factry repos, etc.)? Interactive sessions are broader but harder to parse — they're multimodal (user + agent back-and-forth, code diffs, tool outputs) and live across many projects.

2. **Learning granularity**: What patterns matter most? Cost trends (token drift, per-category baselines)? Tool usage (which tools/agents/workflows appear, succeed, fail)? Decision quality (when does the agent/user pair make good vs bad choices)? Or all three?

3. **Output mode**: Should the system modify AGENT.md directly when patterns suggest improvements (e.g. "this tool has 90% failure rate, disable it"), or surface findings as read-only reports in JOURNAL for you to review? Self-modifying is bolder and faster; advisory-only is safer and keeps you in the loop.

**Trade-off summary:**
- Scope: broad data (agent + interactive) is more useful but costlier and harder to parse cleanly. Starting narrow (agent runs only) is lower risk and can expand later.
- Output: self-modifying is risky if pattern detection is wrong, but aligns with charter goal #1 (betterment of the agent itself). Advisory-only is safer but could accumulate unread reports.

No rush — this can wait for your input. If you'd prefer the agent to first finish the simpler proposed goals (vault enrichment, self-audit) and re-surface the learning system later, that's fine too.
