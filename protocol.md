# Protocol Draft

This is an early sketch of a shared state protocol for multi-agent collaboration.

## State Card

An agent publishes a state card when a work session reaches a meaningful checkpoint.

Each card should be short, structured, and reviewable.

```yaml
id: card-0001
project: example-project
created_at: 2026-07-04T00:00:00Z
created_by:
  type: agent
  name: coding-agent-a
session:
  private_transcript_available: false
  summary: "Investigated authentication flow and found a likely stale token issue."
status: proposed
items:
  - type: fact
    text: "The login flow stores access tokens in local storage."
    evidence:
      - "src/auth/session.ts"
    confidence: high
  - type: assumption
    text: "Token refresh may fail after the browser wakes from sleep."
    evidence: []
    confidence: medium
  - type: risk
    text: "Changing token storage could affect existing sessions."
    evidence:
      - "src/auth/session.ts"
    confidence: medium
  - type: open_question
    text: "Should existing sessions be migrated or invalidated?"
    owner: human
```

## Item Types

### fact

A claim believed to be true based on evidence.

Facts should include evidence whenever possible.

### assumption

A claim currently used for reasoning but not yet verified.

Assumptions should be easy to expire or challenge.

### decision

A choice that has been made by an authorized person or process.

Decisions should include the decision owner.

### open_question

Something that needs an answer before work can proceed confidently.

### risk

Something that may cause failure, regression, delay, security exposure, or user confusion.

### blocker

Something currently preventing progress.

### artifact

A produced file, branch, pull request, design, document, dataset, script, or external link.

### rejected_path

An explored option that should not be repeated unless new information appears.

### stale

An item that may no longer be reliable.

## Review Status

Each card or item can have a review status:

- proposed: produced by an agent, not yet reviewed
- confirmed: reviewed and accepted by a human or trusted process
- challenged: disputed or needs verification
- rejected: reviewed and rejected
- superseded: replaced by newer information
- stale: possibly outdated

## Governance Rules

1. Agents may propose state.
2. Humans or trusted automation should confirm important facts and decisions.
3. Every confirmed fact should have evidence or an explicit reviewer.
4. Assumptions must be visible as assumptions.
5. Rejected paths should be preserved to avoid repeated work.
6. Old state should be easy to mark stale.
7. Private transcripts should be optional and access-controlled.

## Minimal JSON Shape

```json
{
  "id": "card-0001",
  "project": "example-project",
  "created_at": "2026-07-04T00:00:00Z",
  "created_by": {
    "type": "agent",
    "name": "coding-agent-a"
  },
  "status": "proposed",
  "summary": "Investigated authentication flow.",
  "items": [
    {
      "type": "fact",
      "text": "The login flow stores access tokens in local storage.",
      "evidence": ["src/auth/session.ts"],
      "confidence": "high",
      "status": "proposed"
    }
  ]
}
```

## Design Bias

Prefer a small schema that people actually use over a complete ontology that nobody maintains.
