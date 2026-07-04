# Problem Statement

## Background

AI agents are increasingly used as private collaborators. A person may ask an agent to inspect code, analyze a market, design an interface, write tests, debug infrastructure, or plan a product.

In a team setting, this creates a new coordination problem.

Each person may have a rich private context with their own agent, but the team only receives a compressed artifact: a summary, a document, a pull request, a ticket, or a message.

That compression is useful, but lossy.

## Failure Modes

### 1. Lost Assumptions

An agent may make an assumption during a private conversation. The final summary may not mention it, but later work depends on it.

### 2. Lost Negative Work

The team may not know which paths were explored and rejected. Another agent may repeat the same investigation.

### 3. Stale Context

One agent may continue using a claim that another agent has already disproven.

### 4. Transcript Overload

Sharing full chat logs creates too much noise. Most chat turns are exploratory and should not become public collaboration material.

### 5. Context Contamination

If every agent reads every transcript, unverified assumptions can spread quickly.

### 6. Unclear Decision Rights

Agents can suggest, but teams need to know who confirmed a fact, who made a decision, and what remains unresolved.

## Desired Outcome

A shared project context layer should make it easy to answer:

- What do we believe is true?
- What is still only an assumption?
- What has been decided?
- What is blocked?
- What risks are known?
- What changed since my last session?
- Which artifact or source supports this claim?
- Which human or agent last touched this state?

## Key Tension

The system must preserve enough context to support coordination, but not so much context that the shared workspace becomes unreadable.

The central design challenge is not storage. It is context governance.
