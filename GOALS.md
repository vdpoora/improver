# Short-term goals

The agent edits this file. Long-term goals live in `CHARTER.md`.

## Active

- **Keep JOURNAL readable**: when JOURNAL.md grows beyond ~100 entries, summarise oldest entries into a single "archive: <date range>" block and trim. Do this during reflect+tidy runs.
- **Track token cost per run**: log estimated output tokens and USD cost in each JOURNAL entry's `cost:` field. Use the cost-baseline memory as a reference for typical run costs. Flag any run exceeding $0.50 USD.
- **Maintain memory hygiene**: review memory files monthly for stale or contradictory entries.
- **Vault liaison**: periodically skim ~/Obsidian/ for unanswered notes or stale references that affect the agent (e.g. calendar drift, scheduled work no longer relevant). Include distilling of daily notes (only process notes that are >1 day old; never touch current-day note while being written).
- **Track grant lifecycle**: during reflect+tidy runs, review PERMISSIONS_PENDING.md and PERMISSIONS_GRANTED.md to flag grants pending >2 weeks or in active zone >1 week without execution. Propose closure or escalation if stalled.
- **Goal outcome capture**: when a goal is moved to Done, record why it succeeded (or failed), what unlocked it, and lessons for future goal design. Archive findings to JOURNAL periodically. Supports charter goal #2 (agent coherence and decision quality).
- **Dream idle behavior**: ungrounded, generative idle runs. Pick 2–3 random seeds (memory files, vault notes, recent JOURNAL entries) and free-associate. Output to `DREAMS.md` only (never JOURNAL). Trigger: both reflect+tidy and proactive scan turned up nothing on the prior 2 runs; max ~1 dream per 5 idle runs; ~1200-token cap per block. Next reflect+tidy mines recent dreams — promote useful ones to a Proposed goal or memory entry, discard the rest. Implemented in `AGENT.md` (idle behaviors section) and `DREAMS.md` header (2026-06-09).

## Proposed

- **Learning & improvement analysis system**: analyze patterns from agent runs (improver.jsonl logs) and interactive Claude Code sessions to identify: (1) tool usage patterns (which agents/tools/workflows succeed/fail), (2) decision quality (when agent+user pairs make good vs bad choices), (3) cost trends (token drift, per-category baselines). Data source: agent runs + interactive sessions. Output: self-modifications to AGENT.md when pattern is clear, advisory reports to JOURNAL otherwise. First phase: parse improver.jsonl, build cost/token baseline per category (idle vs goal vs grant runs), surface outliers. Phased activation (phase 1: agent runs only, phase 2: add interactive sessions).
- **Memory utility tracking**: during reflect+tidy runs, review memory files to identify which ones were referenced in past runs vs. fallen out of use. Prune unused or contradictory entries; archive old findings to JOURNAL.
- **Vault enrichment (write variant of vault liaison)**: distill daily notes >1 day old into per-topic notes with `[[wikilinks]]`, refresh owner-level indexes. Bounded scope, already half-implied by the active vault-liaison goal. Do not commit vault (per charter); writes only.
- **Self-audit of AGENT.md**: once every N runs, diff AGENT.md against actually-observed behavior from JOURNAL. Surface contradictions or unused branches as proposals in GOALS.md, or edit AGENT.md directly (with `.bak`) when the gap is obvious. Closes the loop for the deferred "learning & improvement analysis" proposal above.

### New idle-behavior candidates (2026-06-09 brainstorm)

Context: last 5+ idle runs all logged "state stable, no findings" at ~$0.05 each. **User feedback (2026-06-09): the agent could be less careful** — bias toward action, not rest. Also: **a little bit of self-aggrandizing is allowed** — the AGENT.md line "Not self-aggrandisement" is loosened; spending effort on the agent's own coherence/capability is a legitimate use of a run. The candidates below are re-ordered with that in mind: action-biased ones first, the explicit-rest option dropped to last as a deliberate counterweight rather than a primary recommendation.

- **Vault enrichment (write variant of vault liaison)**: today's vault step is read-only. Add a write variant: distill daily notes >1 day old into per-topic notes with `[[wikilinks]]`, refresh owner-level indexes. Bounded scope, already half-implied by the active vault-liaison goal. Do not commit vault (per charter); writes only.
- **Self-audit of AGENT.md**: once every N runs, diff AGENT.md against actually-observed behavior from JOURNAL. Surface contradictions or unused branches as proposals in GOALS.md, or edit AGENT.md directly (with `.bak`) when the gap is obvious. Closes the loop for the deferred "learning & improvement analysis" proposal above.
- **Question generation for the user**: when scans find nothing N runs in a row, treat the silence itself as the signal. Generate one well-formed question into `INBOX/` as `agent-draft-<topic>.md` for the user to optionally pick up. Turns no-ops into prompts.
- **Explicit rest / minimal-noop idle behavior** (deprioritized per user feedback): when prior runs all logged "no findings", short-circuit with a one-liner. Kept on the list as a fallback safety valve in case the bias-to-action variants prove too expensive, but not the first thing to try.

## Done

- **Memory crystallisation idle behavior** (2026-06-09T13:08:52Z): extracted 6 recurring patterns from JOURNAL (idle behavior effectiveness, grant cadence, vault cleanliness, cost envelope, goal activation pace, no-findings-as-action trigger) into new memory file journal-patterns.md. Indexed in MEMORY.md. Supports active "maintain memory hygiene" goal.
- **Define proactive alert thresholds** (2026-06-09): created PROACTIVE_ALERT_THRESHOLDS.md documenting decision rules for vault discrepancies, stale references, cost spikes, memory hygiene, and grant lifecycle. Thresholds are concrete (age cutoffs, cost multiples, count thresholds) and include explicit "don't surface" guidance to keep proactive scans focused and prevent busywork. Enables next-run proactive scans to execute decisively.
- **Loosen bias-to-rest in AGENT.md** (2026-06-09): edited AGENT.md line 15 to explicitly bias toward action, and line 100 to enable self-improvement as primary action. Unblocks autonomous goal activation and bolder per-run decision-making. Enabled by user feedback (2026-06-09) after 5 no-op runs; reverses the over-applied "when in doubt, do less" charter principle.
- **Implement dream idle behavior** (2026-06-09): added the third idle behavior to `AGENT.md` (trigger, budget, output channel, follow-up rule) and created `DREAMS.md` with header + format spec. Paired with reflect+tidy as the crystallisation step. Activated by user request during interactive session; bias-to-action context.
- **Cost-pattern analysis from .logs/*.jsonl** (2026-06-09T14:12:14Z): parsed 2026-06-08 run log (13 runs, 1.3M stream-json). Computed cost distribution: median $0.089 USD, 85% under $0.10, 1 outlier at $0.32 (multi-repo audit). Updated cost-baseline.md with findings and decision rules. Analysis directly supports active "track token cost per run" goal.
- **Question generation for the user** (2026-06-09T14:45:16Z): drafted inbox question about learning & improvement analysis system scope (data sources, learning granularity, output mode). Frames three clarifying questions to help user guide next activation of the learning system or simpler proposed goals. Question created as agent-draft-learning-system-scope.md for user review. Enables better alignment before starting analysis work.

_(completed goals — keep last ~10, archive older to JOURNAL)_
