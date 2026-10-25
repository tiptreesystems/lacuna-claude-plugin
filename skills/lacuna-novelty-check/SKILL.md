---
name: lacuna-novelty-check
description: "Use when the user describes an ML/AI research idea and asks whether it has been done, how novel it is, what the closest prior work is, or how to position it (e.g. 'has anyone tried X', 'is this idea new', 'closest work to my project', 'how is my approach different from'). Uses the Lacuna Research tools. Reports what was checked; it is not an exhaustive literature search."
---

# Check whether an ML idea has been done

## Scope

Lacuna covers ML/AI research only. For ideas outside ML/AI, say so and do not call its tools.

## Workflow

1. **Restate the idea** in one sentence and name its parts: the problem, the method, the setting or data, the claimed result. Novelty usually lives in a combination of parts.
2. **Paper searches, bounded.** Call `search_lacuna(search_type="paper")` once for the whole idea and once each for its two most distinctive combinations of parts (at most three paper searches). Use the field's usual terms. Do not paraphrase a query that already returned relevant hits; fetch those instead.
3. **Its direction.** Call `search_lacuna(search_type="cluster")` once and `get_direction` on the closest direction, to see what that line of work already covers.
4. **Generated proposals.** Call `search_lacuna(search_type="hypothesis")`. A close Lacuna hypothesis means the gap has been spotted, not that it has been filled. Fetch it with `get_hypothesis`.
5. **Read before judging.** Call `get_paper` on the 3–5 closest papers to confirm what they actually did. Never judge closeness from titles or snippets alone.

## Output

- **Verdict:** "done", "partly done", "close work exists but this combination looks open", or "nothing close found in Lacuna", with one sentence on why.
- **Closest prior work:** for each paper, what it shares with the idea and what it does not.
- **The direction it sits in**, linked.
- **What would make it new:** the specific difference no paper found covers, and any Lacuna hypothesis that points at it.
- **What was checked:** the queries run, and that this covers Lacuna's ML/AI corpus (major venues, arXiv, OpenReview), where the newest few days may be missing.

## Rules

- Empty searches do not make an idea novel. Say "nothing close found in the Lacuna searches I ran" and list them.
- Cite the complete Lacuna URL for every paper, direction and hypothesis, copied exactly. Never shorten or invent URLs.
