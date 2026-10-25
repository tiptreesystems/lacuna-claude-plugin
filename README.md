# Lacuna Research plugin for Claude

Lacuna is a knowledge graph of machine learning and AI research: 2.3 million papers from major ML venues, arXiv and OpenReview, the researchers behind them, and the research directions they form. This plugin connects Claude to Lacuna and adds four skills:

| Skill | Use it for |
|---|---|
| `lacuna-research-map` | What has been tried on a topic, and what is still open |
| `lacuna-novelty-check` | Whether an idea has been done, and the closest prior work |
| `lacuna-paper-context` | A paper explained and placed among related work, with its code and data |
| `lacuna-find-researchers` | Who works on a topic, similar researchers, who works on what at an institution |

Every answer links to the Lacuna page it came from. The connector is read-only and needs no account.

## Install

**Claude Code**

```
/plugin marketplace add tiptreesystems/lacuna-claude-plugin
/plugin install lacuna-research@lacuna-research
```

**claude.ai and the Claude apps:** add the Lacuna Research connector from the [connector directory](https://claude.ai/directory/lacuna-research).

**Other MCP clients:** see [lacuna.tiptreesystems.com/mcp](https://lacuna.tiptreesystems.com/mcp) or the [server repository](https://github.com/tiptreesystems/lacuna-research-mcp).

## Try

- What has been tried on test-time training, and what is still open?
- Has anyone combined sparse autoencoders with reward models?
- What is arXiv 2603.01092 about, and what is it related to?
- Who works on world models at Mila?

## Support

lacuna@tiptreesystems.com · [Privacy policy](https://tiptreesystems.com/privacy-policy)
