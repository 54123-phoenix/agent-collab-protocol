# Example State Card

```yaml
id: card-2026-07-04-001
project: agent-collaboration-protocol
created_at: 2026-07-04T02:00:00Z
created_by:
  type: human_agent_session
  human: "project-owner"
  agent: "research-agent"
status: proposed
summary: "Explored whether teams need a shared state layer for multi-agent collaboration."
items:
  - type: fact
    text: "Sharing full agent transcripts can create noise and privacy concerns."
    evidence:
      - "conversation-summary"
    confidence: high
    status: proposed

  - type: assumption
    text: "Teams will increasingly use multiple specialized agents in parallel."
    evidence: []
    confidence: medium
    status: proposed

  - type: decision
    text: "The first public artifact should be an RFC-style open repository, not a finished product pitch."
    owner: "project-owner"
    status: confirmed

  - type: open_question
    text: "Should this protocol start as YAML files, a GitHub app, or a browser extension?"
    owner: "community"
    status: proposed

  - type: risk
    text: "If the schema becomes too complex, nobody will maintain it."
    confidence: high
    status: proposed

  - type: rejected_path
    text: "Sharing complete private chat logs by default."
    reason: "Too noisy, privacy-sensitive, and likely to spread unverified assumptions."
    status: proposed
```
*** End of File
# Ask HN Draft

Title:

```txt
Ask HN: How should AI agents share project context without dumping full chats?
```

Post:

```txt
I’m thinking about a problem that may become common in AI-native teams.

Each person may work with their own coding, research, product, or design agent. After a session, they usually share a Markdown summary, a PR, a document, or a ticket. But this loses important context: assumptions, rejected paths, unresolved risks, decisions, and why the agent believed something.

Sharing full transcripts seems wrong too. They are noisy, private, hard to scan, and may contaminate other agents with unverified assumptions.

So I’m wondering whether we need a shared “agent collaboration state layer.”

Each agent could keep its private chat, but publish structured state cards into a shared project space:

- facts
- assumptions
- decisions
- open questions
- risks
- blockers
- artifacts
- evidence links
- stale or superseded items

Humans could confirm, reject, merge, or mark items stale. Other agents could read the reviewed state instead of every raw transcript.

Does something like this already exist in a good form?

If not, what would be the smallest useful protocol or MVP?
```

Short GitHub Discussion version:

```txt
This repository proposes a small shared state protocol for multi-agent collaboration.

The core idea: do not share full private agent transcripts by default. Instead, publish structured, reviewable state cards containing facts, assumptions, decisions, questions, risks, blockers, artifacts, and evidence.

I’m looking for feedback on whether this problem is real, whether existing tools already solve it, and what the smallest useful protocol should include.
```
