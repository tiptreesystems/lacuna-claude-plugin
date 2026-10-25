---
name: lacuna-novelty-check
description: "Use when the user describes an ML/AI research idea and asks whether it has been done, how novel it is, what the closest prior work is, or how to position it (e.g. 'has anyone tried X', 'is this idea new', 'closest work to my project', 'how is my approach different from'). Uses the Lacuna Research tools to find the closest papers, directions and proposals. Not a substitute for a full literature search: say what was checked."
---

# Check whether an ML idea has been done

## Workflow

1. **Restate the idea** in one sentence, then split it into its parts: the problem, the method, the setting or data, and the claimed result. Novelty usually lives in a combination of parts, not in one.
2. **Search each angle.** Call `search_lacuna` with `search_type="paper"` for the whole idea, then for the two or three most distinctive combinations of its parts. Use the field's own terms and common synonyms (for example "test-time training" and "test-time adaptation").
3. **Find its neighbourhood.** Call `search_lacuna` with `search_type="cluster"` to find the directions the idea belongs to, and `get_direction` on the closest one to see what that line of work already covers.
4. **Check the proposals.** Call `search_lacuna` with `search_type="hypothesis"`. A close Lacuna hypothesis means the gap has been spotted but, as far as Lacuna knows, not filled.
5. **Read the closest papers.** Call `get_paper` on the 3–5 closest results to confirm what they actually did. Do not judge closeness from titles alone.

## Output

- **Verdict:** one of "done", "partly done", "close work exists but this combination looks open", or "nothing close found in Lacuna". One sentence on why.
- **Closest prior work:** for each paper, what it shares with the idea and what it does not. Link each to its Lacuna URL.
- **The direction it sits in:** the Lacuna direction(s), with links.
- **What would make it new:** the specific difference that no paper found covers, and any Lacuna hypothesis that points at it.
- **What was checked:** the queries run, and that this covers Lacuna's ML/AI corpus only (major venues, arXiv, OpenReview), not every paper ever written. Newer than a few days may be missing.

## Rules

- Never call an idea novel just because the searches came back empty. Say "nothing close found in Lacuna" and list what was searched.
- Cite the Lacuna URL for every paper, direction and hypothesis you mention.
