# Decision Debt

**Decision debt** is what builds up when organizations make decisions and then forget them: old decisions that were quietly replaced but still look active, decisions that conflict with each other, and decisions that block other work.

**Decision Debt** is an AI agent that finds this debt using a knowledge graph. Every answer comes with the graph path that proves it.

Built for **Graph Hacks: Context for AI Agents** (WeMakeDevs x FalkorDB).

**Live demo:** [link] | **Demo video:** [link] | **Blog post:** [link]

---

## The problem
Teams make decisions in meetings, documents, and chats. Over time:
- An old decision gets replaced, but people still follow it
- Two teams make decisions that conflict
- Work gets stuck behind a decision nobody remembers

Nobody tracks this, so the debt keeps growing.

## What it does
- Checks whether a decision is still valid or was replaced
- Shows what depends on a decision, and what breaks if it changes
- Finds decisions that conflict with each other
- Finds bottleneck decisions that many others depend on
- Gives the exact graph path and source for every answer

## Why a graph?
These questions are about **connections**: "replaced by", "depends on", "conflicts with". A graph follows those links directly, so the agent can show its reasoning. FalkorDB is the core of the project, and the agent can't answer without it.

## How it works
1. **Data:** [data source] is loaded into FalkorDB.
2. **Graph:** decisions are nodes, linked by `SUPERSEDES`, `REQUIRES`, `CONFLICTS_WITH`, and so on.
3. **Agent:** an LLM agent uses graph tools (path search, impact analysis, bottleneck detection) to answer questions.
4. **Answer:** the agent returns the answer plus the graph path and source.

## Data model
[Add a diagram or list of node types and relationship types here]

Nodes: `Decision`, `Person`, `Team`, `Document`
Relationships: `SUPERSEDES`, `REQUIRES`, `CONFLICTS_WITH`, `DECIDED_BY`, `DISCUSSED_IN`

## Graph algorithms used
| Algorithm | Used for | Why |
|---|---|---|
| Shortest path / traversal | Following "replaced by" chains | [your reason] |
| PageRank | Finding the most depended-on decisions | [your reason] |
| Betweenness centrality | Finding bottlenecks | [your reason] |

## Results
[Add your real results here: accuracy on your test set, and how it compares to plain vector search. Include cases where it failed.]

## Tech stack
- FalkorDB (graph database)
- [LLM and framework]
- [MCP, if used]
- [Frontend and hosting]

## Run it locally
```bash
# 1. Start FalkorDB
docker run -p 6379:6379 -p 3000:3000 falkordb/falkordb:latest

# 2. Install dependencies
[your install command]

# 3. Add your keys
cp .env.example .env

# 4. Load the data
[your load command]

# 5. Run the app
[your run command]
```

## Limitations
[Be honest here: what doesn't work well, what you'd improve with more time]

## Author
Himanshi | [GitHub] | [LinkedIn] | [X]
