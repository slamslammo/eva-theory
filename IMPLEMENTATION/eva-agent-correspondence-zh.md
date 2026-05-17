# eva-agent 理论 / 实现边界

English: [eva-agent-correspondence.md](eva-agent-correspondence.md)

`eva-theory` 和 `eva-agent` 是分工不同的两个项目。

## eva-theory 负责

- EVA 的问题定义、适用范围、核心理论 claim 和术语
- v0.5 core architecture 与 v0.6 theoretical extension
- 面向读者的理论解释文章和图示
- scenario specification 等理论侧边界

## eva-agent 负责

- framework 和 runtime 的具体实现
- scenario-specific drives、sensors、actions、anchor policies、prior skills、outcome observers
- runner assembly、runtime status、validation traces、metrics 和 engineering roadmap
- implementation-specific documentation

想看理论，读 `eva-theory`。想看实现，读 [`eva-agent`](https://github.com/slamslammo/eva-agent)。

