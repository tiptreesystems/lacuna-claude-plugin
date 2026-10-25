---
name: lacuna-research-map
description: "Use when the user asks what has been tried on an ML/AI research topic, what the main lines of work are, what is still open, or wants a map of or reading path through a research area (e.g. 'what has been tried on test-time training', 'open problems in diffusion distillation', 'map out work on SAE interpretability'). Uses the Lacuna Research tools. Not for a single paper (lacuna-paper-context), one specific idea (lacuna-novelty-check), or a full report (lacuna-literature-review)."
---

# Map an ML research topic with Lacuna

Lacuna groups ML/AI papers into research directions: clusters of papers that share ideas, methods or findings. Each direction has a summary, its papers, its authors and related directions. Lacuna also holds AI-generated research proposals ("hypotheses") that point at gaps. Answer from these, not from memory, and cite the Lacuna page for each claim.

## Scope

Lacuna covers machine learning and AI research only. If the topic is outside ML/AI (chemistry, biology, law, news…), say Lacuna is not the right source and do not call its tools, unless the user asks about ML/AI methods for that domain.

## Workflow

1. **One direction search.** Call `search_lacuna(query=<topic>, search_type="cluster")`. Do not run a paper search alongside it. Keep the 2–4 directions that are actually about the topic.
2. **Read the directions.** Call `get_direction` on each kept direction. Use its summary, size, key papers and `related_directions`. To widen the map, follow `related_directions` from these results instead of running more searches.
3. **Representative papers.** Call `get_direction_papers` on the two or three main directions and use the listed papers directly. Do not search for their titles again. Call `get_paper` on a paper only if you need more than the listing gives.
4. **What is open.** Call `search_lacuna(query=<topic>, search_type="hypothesis")` and `get_hypothesis` on the top one or two. Combine them with limitations stated in the direction summaries and papers.
5. **Write the map.**

Do not loop on paraphrased queries. If the first search misses, inspect the closest hit, or try one clearly different angle (a sub-topic or the field's other name for it), then move on.

## Output

- One or two sentences on how Lacuna splits the topic.
- **What has been tried:** a short section per line of work, with the idea, the key papers (title, year, venue) and what made it work or not.
- **What is still open:** each item tied to its source: a paper's stated limitation, a direction summary, or a Lacuna hypothesis (these are generated proposals: say so and link them).
- What the map does not cover (directions you saw but did not open).
- One offered next step: a direction's full paper list, a deeper look at one open problem, or who works on it.

## Rules

- Cite the complete Lacuna URL the tools return for every direction, paper and hypothesis. Copy it exactly; never shorten it with "…" and never invent one.
- Payloads are capped and paginated. Absence from a capped list is not absence from Lacuna; phrase negative claims as "not in the results I examined".
