---
name: lacuna-find-researchers
description: "Use when the user wants to find ML/AI researchers or understand one: who works on a topic, researchers similar to someone, possible collaborators or reviewers, who works on what at an institution, or whether a person has worked on a topic (e.g. 'who works on world models at Mila', 'researchers similar to Chelsea Finn', 'has X worked on RL'). Uses the Lacuna Research tools. Covers research output only, not biographies or contact details."
---

# Find ML researchers with Lacuna

Pick one route.

**Who works on a topic.** Author search matches names, not topics: never call `search_lacuna(search_type="author")` with a topic. Instead, search the topic with `search_type="cluster"` (or `"paper"`), call `get_direction` on the closest directions, and use the authors they list. Call `get_author_context` on the strongest 3–5 to confirm what they work on.

**Researchers similar to X.** `search_lacuna(search_type="author", query=<name>)`, check the match by papers and affiliation (names collide often), then `get_author_neighbors`. Fetch `get_author_context` for the top neighbours only when their profiles are needed. Do not run paper searches by author name for this.

**Profile of X.** `search_lacuna(search_type="author", query=<name>)`, then `get_author_context`. Base the summary on its profile text. Its `papers` list is a short recent slice; use `get_author_papers` when the question depends on the full record.

**Has X worked on topic T?** Find X, then page through `get_author_papers` (keep the same limit and increase `offset` by it) and check `get_author_directions`. Never answer "no" from the truncated context slice or one page.

**Who works on what at an institution.** `search_lacuna(search_type="institution", query=<name>)`, then `get_institution_context`, and page `get_institution_authors` if the capped list is not enough. Combine with a topic route to find who there works on the topic.

## Output

- A short list: name, main directions, two or three representative recent papers, and the Lacuna author page.
- Why each person is on the list: shared direction, similar papers, or both.

## Rules

- Lacuna describes research output. Its affiliation field can be incomplete or out of date: say "listed affiliation" and never infer current employment, seniority or biography.
- Do not look up or guess email addresses or personal details.
- Copy complete Lacuna author URLs exactly for everyone you name.
- Absence from a capped or paginated list is not absence from the record.
