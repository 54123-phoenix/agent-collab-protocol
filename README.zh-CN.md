# Agent Collaboration Protocol

一个关于多人和多个 AI Agent 如何共享项目上下文、但不直接倾倒完整私有聊天记录的公开 RFC。

语言：[English](README.md) | [简体中文](README.zh-CN.md)

## 问题

AI 原生工作流正在变得越来越碎片化。

一个人可能和编程 Agent 讨论架构，另一个人可能和研究 Agent 梳理需求，第三个人可能让设计 Agent 评审界面。最后，大家通常会共享一份 Markdown 总结、一个 Pull Request、一份文档、一张截图，或者一条消息。

这些产出很有用，但会丢失很多重要上下文：

- 当时做了哪些假设
- 哪些内容已经验证过
- 哪些方案被排除过
- 哪些问题仍然不确定
- 哪些地方需要人类判断
- Agent 为什么得出这个结论
- 其他 Agent 是否还在使用过期或错误的信息

直接共享完整聊天记录也不是好答案。完整记录通常很吵、很长、很难扫读，也可能包含隐私内容。更麻烦的是，其他 Agent 读到未经验证的假设后，可能会把它继续当成事实扩散。

## 想法

不要默认共享所有对话。

每个 Agent 可以保留自己的私有工作对话，但在关键节点向公共项目空间发布一张结构化状态卡。

状态卡只暴露协作所需的最小信息，例如：

- 事实
- 假设
- 决策
- 开放问题
- 风险
- 阻塞
- 产出物
- 证据链接
- 已过期或被替代的信息

人类可以确认、驳回、合并，或者把这些状态标记为过期。

这个项目不是一个完成的产品，而是一个开放的协议草案和问题陈述。

## 核心原则

默认不共享完整思考流。

共享结构化、可审查、带来源的协作状态。

## 为什么重要

随着 AI Agent 进入软件开发、研究、产品、运营和设计工作流，团队会越来越常见地并行使用多个 Agent。

如果每个 Agent 都只活在自己的聊天窗口里，团队会遇到严重的上下文断裂：

- 重复解释
- 重复调查
- 错误假设传播
- 旧结论没人标记过期
- 决策来源不清楚
- 产出物和推理过程脱节

现有工具擅长聊天、文档、Issue、PR 和任务管理，但不太擅长表达“私有 Agent 推理”和“公共团队决策”之间那层活的项目状态。

这个协议想探索的就是这层缺失的协作上下文。

## 仓库结构

- [problem.md](problem.md)：详细问题定义
- [protocol.md](protocol.md)：共享状态协议草案
- [mvp.md](mvp.md)：最小可行产品形态
- [examples/state-card.md](examples/state-card.md)：状态卡示例
- [drafts/ask-hn.md](drafts/ask-hn.md)：可用于公开讨论的英文发布草稿
- [CONTRIBUTING.md](CONTRIBUTING.md)：贡献说明

## 非目标

这个项目暂时不试图：

- 替代 GitHub、Linear、Slack、Notion 或 Issue Tracker
- 暴露每个人的完整私有对话
- 让 Agent 自动达成一致
- 构建一个全自动公司模拟器
- 在没有人类审查的情况下决定什么是真的

目标更窄：定义一个简单的多 Agent 协作共享状态层。

## 一个状态卡应该包含什么

最小状态卡可以长这样：

```yaml
summary: "调查登录流程后，发现 token 刷新逻辑可能存在过期状态问题。"
items:
  - type: fact
    text: "当前登录流程把 access token 存在 local storage。"
    evidence:
      - "src/auth/session.ts"
    status: proposed

  - type: assumption
    text: "浏览器休眠后 token refresh 可能失败。"
    evidence: []
    status: proposed

  - type: risk
    text: "修改 token 存储方式可能影响已有登录会话。"
    evidence:
      - "src/auth/session.ts"
    status: proposed

  - type: open_question
    text: "已有会话应该迁移，还是直接失效？"
    owner: human
    status: proposed
```

## 开放问题

- 最小可用的状态 schema 应该是什么？
- Agent 能不能确认事实，还是只能由人类确认？
- 多个 Agent 的结论冲突时应该如何展示？
- 假设应该如何过期？
- 一个事实进入公共状态前，应该需要什么证据？
- 第一版应该做成 GitHub App、本地文件协议、浏览器扩展，还是 Slack bot？

## 适合参与的人

如果你正在思考这些问题，欢迎参与：

- 多 Agent 协作
- AI 编程工作流
- 团队知识管理
- Agent memory
- Agent observability
- AI-native project management
- 人机协作协议

## 贡献方式

最有价值的贡献不是抽象赞同，而是具体例子：

- 你在真实项目中遇到的 Agent 协作断裂
- 你觉得状态卡里缺少的字段
- 你认为应该删掉的复杂概念
- 你对冲突处理、过期状态、证据链接的建议
- 你认为这个想法不成立的原因

## License

MIT。可以自由使用、fork、改造，或者把它变成真正的工具。
