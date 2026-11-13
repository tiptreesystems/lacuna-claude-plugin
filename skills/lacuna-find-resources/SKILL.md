---
name: lacuna-find-resources
description: "Use when the user wants code, datasets, models or demos from ML/AI research: the GitHub repository or Hugging Face model for a paper, datasets or benchmarks for a task, open implementations of a method, or which papers use a given dataset or codebase (e.g. 'is there code or a Hugging Face model for this paper', 'benchmark datasets for long-context QA', 'which papers use the DROID dataset'). Uses the Lacuna Research tools. Covers GitHub, Hugging Face and Zenodo resources that Lacuna has linked to a paper."
---

# Find code, datasets and models with Lacuna

Lacuna links papers to their resources: GitHub repositories, Hugging Face datasets and models, Zenodo records, and demos. Each resource has a Lacuna page that lists the papers linked to it and how they relate to it (for example `code_for` or `dataset_for`).

Pick one route.

**Resources for a paper.** With a Lacuna paper URL or artifact id (`art_…`), call `get_paper` directly. With an arXiv ID, an arXiv or OpenReview URL, or a title, first run one `search_lacuna(search_type="paper", query=<the ID, URL or exact title, nothing else>)`; it resolves identifiers exactly. Then call `get_paper` on the matching result's id. The default `view="context"` lists the linked resources. Call `get_resource` on the ones the user asked about (the official code, the released model) for the summary, license, provider metrics and README excerpt. Do not run a resource search for a paper you have already fetched.

**Resources for a topic, task or method.** Call `search_lacuna(search_type="resource", query=<topic>)`. Narrow with `resource_kind` (`codebase`, `dataset`, `model` or `demo`; one value or a list) and `provider` (`github`, `huggingface` or `zenodo`) when the user asked for one kind or one host. For benchmark or evaluation datasets, use `resource_kind="dataset"` with the task or the dataset name as the query. Resource search takes no date bounds, venue filter or year sorting; leave those out. Run at most three resource searches: the topic, then one or two clearly different angles (a sub-task, or the field's other name for it). Do not loop on paraphrases, and do not probe for datasets you remember by name one at a time; report what Lacuna has linked.

**Papers that use a resource.** Find it by name with `search_lacuna(search_type="resource", query=<name>)`, check the match by its external URL, then call `get_resource` and read `publications`. Each entry gives the paper and its relationship to the resource. Call `get_paper` on a publication only when the user needs what that paper reported.

## Output

- For each resource: name, kind, host, what it is in one line, the license when given, its external URL and its Lacuna page.
- The paper or papers it is linked to, with Lacuna links, and the relationship (official code, dataset introduced by, dataset used by…).
- When several resources match, a short table, and which one is the official release if the payload says so.

## Rules

- Lacuna lists a resource only when it has linked it to a paper. No linked resource means "none linked in Lacuna", not "no code exists"; say so and suggest checking the paper itself.
- Take license, size and metrics from the `get_resource` payload. Never guess them from the name.
- Reported results come from the paper (`get_paper`), not from a resource's README excerpt.
- Copy complete Lacuna URLs and external URLs exactly; never shorten or invent a repository, dataset or model name.
- `linked_paper_count` and `publications` can be capped. Absence from a capped list is not absence from the record.
