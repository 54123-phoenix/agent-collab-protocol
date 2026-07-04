# Agent Collaboration Protocol

A public RFC for how multiple humans and AI agents can share project context without dumping full private chat logs.

## The Problem

AI-native work is becoming more fragmented.

One person may discuss architecture with a coding agent. Another may explore product requirements with a research agent. A third may ask a design agent to critique the user experience. At the end, everyone often shares a Markdown summary, a pull request, a document, or a screenshot.

That loses important context:

- what was assumed
- what was verified
- what was rejected
- what remains uncertain
- what needs human judgment
- why an agent reached a conclusion
- whether another agent is working from stale or incorrect information

Sharing full chat transcripts is not a good answer either. They are noisy, private, hard to scan, and can contaminate other agents with unverified assumptions.

## The Idea

Instead of sharing every conversation, agents should publish structured state cards into a shared project layer.

Each agent keeps its own private working conversation, but exposes only the minimum useful collaboration state:

- facts
- assumptions
- decisions
- open questions
- risks
- blockers
- artifacts
- evidence links
- stale or superseded items

Humans can confirm, reject, merge, or mark these items as outdated.

This project is not a finished product. It is an open idea and protocol sketch.

## Core Principle

Do not share full thought streams by default.

Share structured, reviewable, source-linked collaboration state.

## Why This Matters

As AI agents become common in software, research, product, and operations work, teams will need a way to coordinate many parallel agent sessions without creating context chaos.

Current tools are good at conversations, documents, issues, pull requests, and tasks. They are less good at representing the living state between private agent reasoning and public team decisions.

This protocol explores that missing layer.

## Repository Structure

- [problem.md](problem.md): detailed problem statement
- [protocol.md](protocol.md): first draft of the shared state protocol
- [mvp.md](mvp.md): smallest useful product shape
- [examples/state-card.md](examples/state-card.md): example status card
- [drafts/ask-hn.md](drafts/ask-hn.md): public post draft for discussion
- [CONTRIBUTING.md](CONTRIBUTING.md): how to contribute

## Non-Goals

This is not trying to:

- replace GitHub, Linear, Slack, Notion, or issue trackers
- expose every private conversation
- force agents to agree automatically
- build a fully autonomous company simulator
- decide what is true without human review

The goal is narrower: define a simple shared state layer for multi-agent collaboration.

## Open Questions

- What is the smallest useful state schema?
- Should agents be allowed to mark facts as confirmed, or only humans?
- How should conflicts between agents be represented?
- How should old assumptions expire?
- What evidence should be required before a claim enters shared state?
- Can this be implemented as a GitHub app, local workspace file, browser extension, or Slack bot?

## Chinese Summary

这个项目讨论的是：多人分别和自己的 AI Agent 深度交流后，如何避免只靠 Markdown 总结或完整聊天记录来同步上下文。

核心想法是：每个 Agent 保留自己的私有对话，但向公共项目空间发布结构化状态卡，例如事实、假设、决策、问题、风险、阻塞和产出。人类可以确认、驳回、合并或标记过期。

它不是一个完整产品，而是一个开放 RFC，希望帮助大家讨论多 Agent 协作时真正需要共享的最小上下文层。

## License

MIT. Use, fork, remix, or turn this into a real tool.
