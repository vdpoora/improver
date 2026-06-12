# Dreams

Speculative, ungrounded output from the agent's `dream` idle behavior.
**Nothing in this file is a finding, decision, or fact.** Treat every block as raw material.

## Rules for writing here

- Only the `dream` idle behavior in `AGENT.md` writes here. Other idle behaviors write to `JOURNAL.md`.
- One dream per run. Cap each block at ~1200 output tokens.
- Never read this file as if it were `JOURNAL.md`. Dreams are seeds, not history.
- On the next reflect+tidy run, mine the latest dreams: promote useful ones to `GOALS.md` (Proposed) or to a memory entry; otherwise leave them in place.
- Trim aggressively: keep at most the 20 most recent blocks. Older blocks may be deleted without ceremony — they were never load-bearing.

## Block format

```
## <ISO timestamp> — <one-line gist>
- mode: <recombination | counterfactual | imagined-future | narrative-synthesis | free>
- seeds: <2–3 inputs you drew from, e.g. memory:cost-baseline, vault:Factry/historian/foo, journal:2026-06-09T10:01:51Z>
- dream:
  <free-form prose. Speculative. Not a plan, not a finding.>
- maybe-real: <one line — if any thread feels like it points at something worth promoting on the next reflect+tidy. Otherwise: "nothing — file under noise.">
```

## Dreams

## 2026-06-12T02:00:55Z — idle evolution: from rotation to adaptive pacing

- mode: counterfactual + imagined-future
- seeds: memory:feedback-agent-bias, memory:journal-patterns, journal:2026-06-12T00:58:04Z
- dream:
  The agent's current idle rotation (reflect → scan → dream → repeat) is deterministic and evenly paced. Three behaviors, back-to-back, 30 minutes each. But what if the agent could *learn* which behavior is due, and which is productive, without pre-programmed rotation?
  
  Hypothesis: the cost-baseline and journal-patterns memories show that idle runs are cheap and predictable. Reflect+tidy is action-optimized (high autonomy bias, 5/11 substantive). Proactive scans are detection-optimized (low action, 9/12 zero findings). Dreams are speculative and post-processed. 
  
  Imagined future: instead of rigid rotation, the agent could maintain a *scoring heuristic* — an internal record of "which idle behavior produced value in the last N runs?" Then, on each wake, pick the behavior with the highest recent score. If reflect+tidy has been finding no stale state, bias harder toward reflect's "no-findings-as-action" branch (activate a goal, extract a memory, refactor). If scans are dry, either skip to a dream, or drop back into a dream-only cycle.
  
  This feels like a move from "mechanical alternation" to "statistical self-tuning." Would it be worth it? The cost is a small metadata file (one scoring row per idle behavior, updated each run, pruned monthly). The gain is coherence — the agent's own decisions would reflect what's actually working, not a pre-decided schedule.
  
  Counterpoint (already in the dream): the current rotation is deterministic and auditable. The user can see in JOURNAL exactly why each idle behavior ran. A scoring heuristic would obscure that (though it could be logged). Maybe auditing clarity is worth more than adaptive efficiency at this small scale.
  
  Subsidiary counterfactual: what if the agent could propose a *qualitative* summary of each idle run directly to the user, rather than embedding it in JOURNAL? E.g., after a proactive scan finds 2 observations, an auto-drafted INBOX item saying "found 2 repo patterns worth mentioning" + snippet. This would close the loop between "agent finds something" and "user learns about it" without requiring the user to read all of JOURNAL. But again: auditing clarity vs. user friction. Current model trusts the user to skim JOURNAL when interested. Maybe that's fine.
  
- maybe-real: self-tuning idle-behavior scoring could be a Phase 3 candidate for Learning System, or a standalone Proposed goal for later. Idea is speculative; don't promote yet. More interesting: the pattern that "no findings for 2 runs → apply action trigger" is working; what if we could *predict* when to dream (vs. activate goals) by tracking "dry run frequency"? That's closer to real and worth watching over next 10 runs.

## 2026-06-12T07:38:57+02:00 — when memories converge: learning system scaling

- mode: imagined-future + narrative-synthesis
- seeds: memory:decision-rules-from-phase1, memory:vault-liaison-pattern, journal:2026-06-12T01:23:36Z (Phase 2 completion)
- dream:
  The agent has now completed Learning System Phase 1 (cost baselines, decision rules) and Phase 2 (decision quality across 30 runs, behavioral patterns). At Phase 2 the question surfaces: what happens when the number of memories equals the number of *distinct insights* the agent can derive from its own run log?
  
  Subsidiary question: the vault-liaison-pattern memory shows low frequency (1 enrichment per 30 runs) but high quality. Cost-baseline shows the agent learned its own cost envelope in 13 runs. Decision-rules distilled 25 runs into 5 findings. Is the agent approaching saturation — the point where further data accumulation yields diminishing insights per run?
  
  Imagined future: if this holds true, the agent's "learning capacity" is constrained not by data volume but by the rate at which new *types* of patterns emerge. Phase 3, then, would be meta: instead of analyzing more runs, analyze what *kinds* of questions the agent could ask (tool usage by category, session-level coherence, self-modification impact). Or: shift the learning focus away from internal patterns and toward external change detection (are Factry repos changing faster? Are user signals shifting? Is there infrastructure drift the agent should flag?).
  
  The dream here is that memory consolidation + Phase 2 completion + the vault liaison work might have bought the agent something real: an *epistemological boundary*. The agent knows what it knows, and knows where the boundaries of that knowledge are. Instead of grinding through more data, the next move could be: get smarter about what *questions* are worth asking.
  
  Counterpoint: Phase 3 at 50 runs is still 20 runs away. Maybe the pattern emerges only at scale. Or maybe the agent is overthinking it — data will speak, and forcing a meta-analysis before 50 runs is premature.
  
- maybe-real: Phase 3 agenda is lurking in the learning system work already. The idea of "epistemological boundary detection" — knowing when data saturation hits — is more interesting than "add more tool-usage stats". Watch whether the next 20 runs yield new memories or mostly repeat the prior 5. If mostly repetition, that's the signal to shift Phase 3 to meta-questions. If new patterns emerge, grind on.

## (archive: none yet — keep last 20 blocks)
