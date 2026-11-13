# Lacuna Research plugin for Claude

Lacuna is a knowledge graph of machine learning and AI research: 2.3 million papers from arXiv, OpenReview and major ML venues, 215,000 authors, 6,200 venues and 28,000 research directions.

Use it for literature reviews, related-work sections, and finding out who is working on what.

With this plugin, Claude can:

- Find papers on a topic, method or benchmark, and pull up related papers
- Read a paper's summary and figures
- Find the code, datasets and models linked to a paper (GitHub, Hugging Face, Zenodo)
- Look up an author's papers, collaborators and research directions
- See the researchers and papers associated with an institution or venue
- Explore active research directions and open hypotheses in a subfield

All tools are read-only and work without an account. Every answer links to the Lacuna page it came from.

## Skills

The plugin connects Claude to Lacuna and adds six skills:

| Skill | Use it for |
|---|---|
| `lacuna-research-map` | What has been tried on a topic, and what is still open |
| `lacuna-literature-review` | A cited literature review or related-work section, with date bounds and required sections |
| `lacuna-novelty-check` | Whether an idea has been done, and the closest prior work |
| `lacuna-paper-context` | A paper's summary and figures, placed among related work |
| `lacuna-find-resources` | Code, datasets and models for a paper or a topic, and which papers use them |
| `lacuna-find-researchers` | Who works on a topic, similar researchers, who works on what at an institution or venue |

## Install

**Claude Code**

```
/plugin marketplace add tiptreesystems/lacuna-claude-plugin
/plugin install lacuna-research@lacuna-research
```

**claude.ai and the Claude apps:** add the Lacuna Research connector from the [connector directory](https://claude.ai/directory/lacuna-research).

**Other MCP clients:** see [lacuna.tiptreesystems.com/mcp](https://lacuna.tiptreesystems.com/mcp) or the [server repository](https://github.com/tiptreesystems/lacuna-research-mcp).

## Try asking

- "Find recent papers on sparse autoencoders and summarize the main approaches"
- "Is there code or a Hugging Face model for this paper?"
- "Who is working on test-time adaptation, and what have they published?"
- "What are the open research directions in diffusion model distillation?"

## What it sends

The plugin has no hooks, scripts or local servers. Its only network access is the Lacuna MCP server at `https://lacuna.tiptreesystems.com/api/mcp`, which receives the search queries and paper, author, direction, venue, institution, hypothesis and resource IDs that Claude passes to its tools. The server is read-only and needs no account. Its request logs are covered by the privacy policy below.

## Support

lacuna@tiptreesystems.com · [Privacy policy](https://tiptreesystems.com/privacy-policy)
