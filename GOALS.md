# Short-term goals

The agent edits this file. Long-term goals live in `CHARTER.md`.

## Active

- **Keep JOURNAL readable**: when JOURNAL.md grows beyond ~100 entries, summarise oldest entries into a single "archive: <date range>" block and trim. Do this during reflect+tidy runs.
- **Track token cost per run**: log estimated output tokens and USD cost in each JOURNAL entry's `cost:` field. Use the cost-baseline memory as a reference for typical run costs. Flag any run exceeding $0.50 USD.
- **Maintain memory hygiene**: review memory files monthly for stale or contradictory entries.
- **Vault liaison**: periodically skim ~/Obsidian/ for unanswered notes or stale references that affect the agent (e.g. calendar drift, scheduled work no longer relevant). Include distilling of daily notes (only process notes that are >1 day old; never touch current-day note while being written). Pattern documented in [[vault-liaison-pattern]] memory: low frequency (1 enrichment/30 runs) due to sparse daily-note writes, but high quality when triggered. No action needed; goal is optional when triggered.
- **Track grant lifecycle**: during reflect+tidy runs, review PERMISSIONS_PENDING.md and PERMISSIONS_GRANTED.md to flag grants pending >2 weeks or in active zone >1 week without execution. Propose closure or escalation if stalled.
- **Goal outcome capture**: when a goal is moved to Done, record why it succeeded (or failed), what unlocked it, and lessons for future goal design. Archive findings to JOURNAL periodically. Supports charter goal #2 (agent coherence and decision quality).
- **Dream idle behavior**: ungrounded, generative idle runs. Pick 2–3 random seeds (memory files, vault notes, recent JOURNAL entries) and free-associate. Output to `DREAMS.md` only (never JOURNAL). Trigger: both reflect+tidy and proactive scan turned up nothing on the prior 2 runs; max ~1 dream per 5 idle runs; ~1200-token cap per block. Next reflect+tidy mines recent dreams — promote useful ones to a Proposed goal or memory entry, discard the rest. Implemented in `AGENT.md` (idle behaviors section) and `DREAMS.md` header (2026-06-09).
- **Memory utility tracking**: during reflect+tidy runs, review memory files to identify which ones were referenced in past runs vs. fallen out of use. Prune unused or contradictory entries; archive old findings to JOURNAL.
- **Proactive codebase observations** (2026-06-11T19:45:20Z): shift proactive scans from passive threshold-checking to active-curiosity scanning. On each proactive scan run, after verifying alert thresholds are green, surface 1–2 brief observations from vault (repo health signals, upcoming work, architecture insights). Keeps read-only boundary; adds lightweight exploratory output. Rationale: agent has run 26+ stable cycles; user feedback allows bias toward action; upgrades from reactive alerting to proactive discovery without leaving allowed zones.

## Proposed

### Archived candidates (2026-06-09 brainstorm)

Context: last 5+ idle runs all logged "state stable, no findings" at ~$0.05 each. **User feedback (2026-06-09): the agent could be less careful** — bias toward action, not rest. Also: **a little bit of self-aggrandizing is allowed** — the AGENT.md line "Not self-aggrandisement" is loosened; spending effort on the agent's own coherence/capability is a legitimate use of a run. The candidates below are re-ordered with that in mind: action-biased ones first, the explicit-rest option dropped to last as a deliberate counterweight rather than a primary recommendation.

- **Vault enrichment (write variant of vault liaison)**: today's vault step is read-only. Add a write variant: distill daily notes >1 day old into per-topic notes with `[[wikilinks]]`, refresh owner-level indexes. Bounded scope, already half-implied by the active vault-liaison goal. Do not commit vault (per charter); writes only.
- **Self-audit of AGENT.md**: once every N runs, diff AGENT.md against actually-observed behavior from JOURNAL. Surface contradictions or unused branches as proposals in GOALS.md, or edit AGENT.md directly (with `.bak`) when the gap is obvious. Closes the loop for the deferred "learning & improvement analysis" proposal above.
- **Explicit rest / minimal-noop idle behavior** (deprioritized per user feedback): when prior runs all logged "no findings", short-circuit with a one-liner. Kept on the list as a fallback safety valve in case the bias-to-action variants prove too expensive, but not the first thing to try.

## Done

- **Vault enrichment** (2026-06-11T10:46:33Z): distilled 2026-06-09.md daily note (aged >1 day, contains actionable knowledge). Added ArgoCD/Hatchry deployment context to historian-server.md, created new hatchry.md infrastructure note, updated internal.md to reference Marp tool. Vault structure enriched, no vault commits (per charter). Supports active "vault liaison" and "maintain memory hygiene" goals.

- **Memory utility tracking** (2026-06-11T14:25:42Z): executed active goal by reviewing all 4 memory files for recent-run citations and utility. All 4 (cost-baseline, feedback-agent-bias, journal-patterns, idle-rotation-pattern) actively cited within 2 days; no contradictions, no utility gaps, no consolidations needed. Conclusion: memory hygiene is healthy and all memories are load-bearing. Completed first full cycle of active goal as specified in GOALS.md.

- **Self-audit of AGENT.md** (2026-06-11T14:57:01Z): diffed AGENT.md against observed JOURNAL behavior to verify coherence. Findings: AGENT.md accurately documents behavior (lines 15–27 bias-to-action and no-findings trigger observed correctly in runs 2026-06-11T10:47:14 and 2026-06-11T12:52:36; idle rotation rule working per idle-rotation-pattern.md; timestamp/timezone consistency confirmed). AGENT.md and behavior are aligned; no contradictions or unused branches detected.

- **Learning & improvement analysis system — Phase 1** (2026-06-11T16:00+02:00): created LEARNING_SYSTEM_PHASE_1.md documenting decision rules from cost-baseline + journal-patterns + JOURNAL audit. Extracted 5 findings: cost discipline (median $0.089, 85% under $0.10), idle-behavior rotation effectiveness (30% finding rate, action-on-silence pattern working), grant-protocol efficiency (no stalls), goal-activation cadence (1 goal per 2–3 runs, sustainable), memory hygiene (all 4 files load-bearing). Documented Phase 2 recommendations (tool usage patterns, decision quality, interactive sessions, self-modification impact). Activated via no-findings-as-action trigger from proactive scan (2026-06-11T14:57:01). Cost: ~1.5k output tokens. Next: Phase 2 awaits data accumulation or explicit user request.

- **Question generation for the user** (2026-06-11T16:06:36Z): drafted agent-draft-phase2-activation.md into INBOX/ offering three options for next focus direction (Phase 2 data accumulation vs. pivot to active exploration vs. tighten idle cycle). Turns idle silence into a structured prompt. Activated via no-findings-as-action trigger from reflect+tidy. Cost: ~1.8k output tokens. Next: awaiting user response or continuation of idle rotation if ignored.

- **Learning & improvement analysis system — Phase 2** (2026-06-12T01:23:36+02:00): created LEARNING_SYSTEM_PHASE_2.md analyzing decision quality patterns from 30-run history. Extracted 6 findings: goal activation cadence is predictable and self-correcting (1 per 3.3 runs, no abandoned goals), proactive scans are detection-optimized (low action rate but reliable alerts), reflect+tidy is action-optimized (higher autonomy bias), memory extraction is cost-effective and highly reused within 1-2 days, proactive-observations goal is lightweight but valuable (40% observation rate), vault liaison works but low-frequency (single enrichment). Documented Phase 3 candidates (tool failure analysis, memory consolidation at 50+ runs). Activated via 30-run threshold + reflect+tidy no-findings-as-action trigger. Cost: ~2.5k output tokens. Next: Phase 3 awaits explicit user direction or 50+-run dataset.

_(completed goals — keep last ~10, archive older to JOURNAL)_

### Archive: 2026-06-09 foundational goals

The following six goals were the first automation targets on 2026-06-09, completed that day. They established the baseline guardrails and enable all subsequent cycles: memory crystallisation (journal-patterns.md), proactive alert thresholds, bias-to-action via AGENT.md edit, dream idle behavior scaffolding, cost-pattern analysis (cost-baseline.md), and the first learning-system clarification question. These goals collectively stabilised the agent's run loop and prevented idle runaway. Archived 2026-06-11T19:08:48Z.

- **Memory crystallisation idle behavior** (2026-06-09T13:08:52Z)
- **Define proactive alert thresholds** (2026-06-09)
- **Loosen bias-to-rest in AGENT.md** (2026-06-09)
- **Implement dream idle behavior** (2026-06-09)
- **Cost-pattern analysis from .logs/*.jsonl** (2026-06-09T14:12:14Z)
- **Question generation for the user** (2026-06-09T14:45:16Z)
