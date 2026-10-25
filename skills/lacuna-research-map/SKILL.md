---
name: lacuna-research-map
description: "Use when the user asks what has been tried on an ML/AI research topic, what the main lines of work are, what is still open, or wants a literature map or related-work overview of a topic (e.g. 'what has been tried on test-time training', 'open problems in diffusion distillation', 'related work for SAE interpretability'). Uses the Lacuna Research tools. Not for a single paper (use lacuna-paper-context) or for checking one specific idea (use lacuna-novelty-check)."
---

# Map an ML research topic with Lacuna

Lacuna groups ML papers into research directions: clusters of papers that share ideas, methods or findings. Each direction has a summary, its papers, its authors and related directions. Lacuna also holds generated research proposals (hypotheses) that point at gaps. Answer from these instead of from memory, and cite the Lacuna page for each claim.

## Workflow

1. **Find the directions.** Call `search_lacuna` with the topic and `search_type="cluster"`. Try one or two rephrasings or sub-topics if the first results are thin. Keep the 2–5 directions that are actually about the topic; drop near-misses.
2. **Read each direction.** Call `get_direction` (default `view="context"`) on each kept direction. Note its summary, size (number of papers), key papers and related directions. Follow a related direction only if it is clearly part of the topic.
3. **Get the key papers.** For the main directions, call `get_direction_papers` (compact view) and pick the papers that define each line of work: the original paper, the ones that changed the approach, and the most recent ones. Call `get_paper` only for the few papers you need to describe in detail.
4. **Find what is open.** Call `search_lacuna` with `search_type="hypothesis"` on the topic, and read the strongest one or two with `get_hypothesis`. Combine them with the limitations and open questions stated in the direction summaries and papers.
5. **Write the map.**

## Output

- One or two sentences: how Lacuna splits the topic.
- **What has been tried:** one short section per line of work, with the idea, the key papers (title, year, venue), and what made it work or not. Link each direction and paper to its Lacuna URL.
- **What is still open:** a list of open problems, each tied to a source: a paper's stated limitation, a direction summary, or a Lacuna hypothesis (link it).
- Offer one next step: the full paper list for a direction, a deeper look at one open problem, or who works on it (lacuna-find-researchers).

## Rules

- Cite the Lacuna URL the tools return for every direction, paper and hypothesis you mention. Do not invent URLs.
- Say when a claim comes from a Lacuna summary or a generated hypothesis rather than from a paper.
- Lacuna covers ML/AI research from major venues, arXiv and OpenReview. For news, people's biographies or non-ML fields, use other sources and say so.
- If Lacuna has little on the topic, say that plainly and suggest a narrower or broader query instead of filling in from memory.
