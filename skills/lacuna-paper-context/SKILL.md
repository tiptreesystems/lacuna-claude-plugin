---
name: lacuna-paper-context
description: "Use when the user gives an ML/AI paper (arXiv ID or URL, OpenReview link, Lacuna link, or title) and wants it explained, summarized, placed in context, compared to related work, or wants its code, datasets or other versions (e.g. 'what is 2603.01092 about', 'explain this paper', 'what is this paper related to', 'is there code for this paper'). Uses the Lacuna Research tools."
---

# Read an ML paper in context with Lacuna

## Workflow

1. **Find the paper.** If you have an arXiv ID, OpenReview or Lacuna URL, pass it straight to `get_paper`. With only a title, call `search_lacuna` with `search_type="paper"` and the exact title, then pick the matching result (check authors and year).
2. **Read it.** Call `get_paper` with the default `view="context"`. This gives the summary, authors, venue, a figure preview, other versions and linked resources (code, datasets, models).
3. **Place it.** Use the paper's research directions and related papers from the context. Call `get_direction` on its main direction to say what line of work it belongs to and what it adds. Use `view="neighbors"` on `get_paper` if you need more related papers.
4. **Code and data.** If the user asks, list the linked resources and call `get_resource` on the main one for details (stars, license, what it contains).

## Output

- What the paper does, in two or three sentences: the problem, the approach, the main result.
- Where it sits: the Lacuna direction(s) and the closest related papers, with what it changes relative to them.
- Versions (workshop vs conference, arXiv revisions) when there is more than one.
- Code, datasets and models, if any.
- Lacuna links for the paper, its direction and every related paper mentioned.

## Rules

- Use the paper's own claims for results; mark anything from Lacuna's generated summary as a summary.
- Cite the Lacuna URL the tools return. Do not invent URLs or arXiv IDs.
- If the paper is not in Lacuna, say so and fall back to other sources.
