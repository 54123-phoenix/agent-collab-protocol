# MVP

## Goal

Build the smallest useful shared state layer for human and AI agent collaboration.

The MVP should answer one question:

> What should the rest of the team know after this private agent session?

## First Version

The first version can be a simple local or Git-backed workflow:

```txt
project/
  agent-state/
    cards/
      2026-07-04-auth-investigation.yaml
      2026-07-04-ui-review.yaml
    index.md
```

Each agent session produces one card. Humans review cards during normal project work.

## Basic Flow

1. A human works privately with an agent.
2. The agent produces a structured state card.
3. The card is saved into the shared project.
4. Humans review, confirm, reject, or edit the card.
5. Other agents read only confirmed or relevant state, not every private transcript.

## Required Features

- create a state card
- list cards by project
- filter by type: fact, assumption, decision, question, risk, blocker, artifact
- mark an item confirmed, challenged, rejected, stale, or superseded
- attach evidence links
- show what changed since the last review

## Nice-to-Have Features

- GitHub issue or PR integration
- Linear or Jira integration
- Slack or Discord digest
- browser extension for copying a session summary into a card
- agent prompt template for generating cards
- conflict detection between cards
- stale item reminders

## What Not To Build First

- a full chat platform
- real-time multi-agent orchestration
- universal memory for all agents
- automatic truth arbitration
- private transcript ingestion by default

## Success Criteria

The MVP is useful if a team can reduce repeated explanations, avoid duplicate agent work, and quickly see the current project state without reading full chat logs.

## Suggested First Prototype

A static web app or small CLI that reads YAML cards and renders:

- project summary
- current facts
- open assumptions
- unresolved questions
- blockers
- risks
- recent artifacts
- stale items

No backend is required for the first prototype.
