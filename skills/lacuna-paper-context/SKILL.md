---
name: lacuna-paper-context
description: "Use when the user gives an ML/AI paper (arXiv ID or URL, OpenReview link, Lacuna link, or title) and wants it explained, summarized, placed in context, compared to related work, or wants its code, datasets or other versions (e.g. 'what is 2603.01092 about', 'explain this paper', 'what is this paper related to', 'is there code for this paper'). Uses the Lacuna Research tools."
---

# Read an ML paper in context with Lacuna

## Workflow

1. **Find it once.** With an arXiv ID, OpenReview, arXiv or Lacuna URL, pass it straight to `get_paper`. With only a title, the only search is `search_lacuna(search_type="paper", query=<exact title>)`, with no extra keywords. If a top result's title matches, call `get_paper` on it and do not search again.
2. **Read the compact context first.** `get_paper` with the default `view="context"` gives the summary, authors, venue, figure preview, other versions and linked resources. Ask for one more specific view only if the context is not enough: `view="concepts"` for key concepts, `view="neighbors"` for related papers, `view="blog"` for the longer summary. Do not request several views speculatively.
3. **Place it.** Use the paper's directions and neighbours from those payloads. Do not run a direction search after fetching the paper; call `get_direction` on its main direction only if you need to describe that line of work.
4. **Code and data.** If asked, list the linked resources and call `get_resource` on the main one.
5. **Other versions.** To read another version (workshop vs conference, revisions), call `get_paper` with that version's id from the returned version list.

## Output

- What the paper does: problem, approach, main result, in two or three sentences.
- Where it sits: its direction(s) and closest related papers, and what it changes relative to them.
- Versions, code, datasets and models, when present.
- Lacuna links for the paper, its direction and every related paper mentioned.

## Rules

- Use the paper's own claims for results; mark Lacuna's generated summary as a summary.
- Copy complete Lacuna URLs exactly; never shorten or invent URLs or arXiv IDs.
- If the paper is not in Lacuna, say so and use other sources.
