---
name: lacuna-find-researchers
description: "Use when the user wants to find ML/AI researchers: who works on a topic, who is doing similar work to a given researcher, possible collaborators or reviewers, or who works on what at an institution (e.g. 'who works on world models at Mila', 'researchers similar to Chelsea Finn', 'who should review this paper', 'collaborators for my project'). Uses the Lacuna Research tools. Covers research output only, not biographies or contact details."
---

# Find ML researchers with Lacuna

## Workflow

**Who works on a topic**
1. Call `search_lacuna` with `search_type="cluster"` to find the topic's directions, then `get_direction` on the closest ones. Each direction lists its main authors.
2. Optionally call `search_lacuna` with `search_type="author"` and the topic, to catch people whose work spans several directions.
3. Call `get_author_context` on the strongest candidates to confirm what they work on and their recent papers.

**Who is similar to a researcher**
1. Find the person: `search_lacuna` with `search_type="author"` and their name. Check the match by papers and affiliation; names collide often.
2. Call `get_author_neighbors` for researchers with similar work, and `get_author_context` on the most relevant ones.

**Who works on what at an institution**
1. Find the institution: `search_lacuna` with `search_type="institution"`.
2. Call `get_institution_context`, then page `get_institution_authors` if needed. Combine with a topic search to find who there works on the topic.

## Output

- A short list of researchers. For each: name, what they work on (their main directions), two or three representative recent papers, and their Lacuna author page.
- Say why each one is on the list: shared direction, similar papers, or both.

## Rules

- Lacuna describes research output (papers, directions). Its affiliation field can be incomplete or out of date: say "listed affiliation" and never infer current employment, seniority or biography.
- Do not look up or guess email addresses or personal details.
- Cite the Lacuna author URL the tools return for everyone you name.
