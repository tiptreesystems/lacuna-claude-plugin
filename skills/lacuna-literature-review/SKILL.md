---
name: lacuna-literature-review
description: "Use when the user asks for a report-style survey of an ML/AI topic: a literature review, related-work section, survey, state-of-the-art report or bibliography, often with date bounds, venues, required sections or a file format (e.g. 'write a literature review of LLM unlearning since 2023', 'survey of diffusion distillation methods with a comparison table'). Uses the Lacuna Research tools. For a quick overview of what has been tried, use lacuna-research-map instead."
---

# Write an ML literature review with Lacuna

## 1. Pin down the request

Write down only what the user actually stated:
- the core ML/AI topic, stripped of task wording;
- date bounds (`date_from`, `date_to`), venues, required sections or subtopics (`must_cover`), and any file format asked for.

Never invent a date bound, venue or structure. If the topic is outside ML/AI, say Lacuna is not the right source.

## 2. Plan

1. Find seed directions with `search_lacuna(query=<topic>, search_type="cluster")` and `get_direction` on the closest few.
2. Write an outline. It must have a section for every `must_cover` item and follow any requested structure.
3. Split the research into 3–5 distinct facets so they collect different sources, for example: foundational and canonical papers; a method taxonomy with representative papers per family; datasets, benchmarks and evaluation; limitations, trade-offs and open challenges; recent frontier (only if the date bounds allow it). Assign every `must_cover` item to exactly one facet.

## 3. Research each facet

For each facet, start from the seed directions: `get_direction_papers` for their literature and `related_directions` to widen. Use `search_lacuna(search_type="paper", date_from=…, date_to=…, venue=…)` only for what the directions do not cover. Apply the date bounds and venue limits to every paper search.

Call `get_paper` on every paper you describe, and describe it from that payload. Search results give titles and snippets only; never describe a paper's method or results from its title or from memory. A typical review reads 8–15 papers. If subagents are available, research the facets in parallel, one per facet, and have each return its findings with complete source URLs.

Do not re-search to validate hits you already have, and do not loop on paraphrased queries.

## 4. Write

- Open with a short framing paragraph; follow the outline; close with open directions.
- Give every `must_cover` item real, cited coverage, not just a heading.
- Use a table to compare several methods, papers or directions.
- Deduplicate across facets. Drop evidence outside the date bounds.
- Every row of a comparison table is a paper you fetched.
- If the user asked for a file (Word, Excel, slides, CSV), build it from the finished review with the same findings and citations, then reopen it and check that the sections and citations are there.

## Rules

- Cite the complete Lacuna URL for every paper, direction and hypothesis, copied exactly. Never shorten or invent URLs, papers, authors or results.
- Lacuna hypotheses are AI-generated proposals; label them as such.
- State what the review covers: Lacuna's ML/AI corpus (major venues, arXiv, OpenReview), the date window and the facets researched.
