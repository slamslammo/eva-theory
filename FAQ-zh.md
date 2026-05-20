# FAQ

English: [FAQ.md](FAQ.md)

## 1. EVA 是想创造一个有生存本能的 AI 吗？

不是。

EVA **不**主张 unconstrained self-preservation。它的 claim 更窄：对某一类 agent 来说，continuity 应该被当作架构问题，而不是事后补丁。在 EVA 中，continuity 始终受到 integrity constraints 和 anchors 约束。

深入阅读见 `THEORY/v0.5-integrated.md`、`THEORY/v0.6-extension.md` 和 `ARTICLES/03-related-work-and-positioning-zh.md`。

## 2. EVA 是否声称 AI 是 alive？

不是。

EVA 不要求把 digital agents 当作生物意义上的 alive。更弱也更有用的 claim 是：某些 agent 更适合被理解为 persistent self-maintaining systems，而不是一次性 task executors。这已经足以推动一种不同架构。

简短范式入口见 `ARTICLES/01-paradigm-introduction-zh.md`。

## 3. EVA 和 long-running / persistent agents 有什么不同？

Long-running agent 仍然可以是 task-centered。EVA 的区别不只是 agent 运行更久，而是 continuity 被当作 first-order architectural condition。

这会改变 drive、memory、constraint 和 action release 在架构中的位置。

对比和定位见 `ARTICLES/03-related-work-and-positioning-zh.md`。架构差异见 `ARTICLES/02-architectural-contributions-zh.md`。

## 4. 为什么 EVA 不从更强的 LLM 开始？

因为更强模型不等于更强 agent architecture。

LLM 可以增强 reasoning，也能提供 human cumulative knowledge。但 EVA 认为 persistent agents 还需要自己的 drive structure、continuity-relevant memory、mediated action selection 和 anchors。在 EVA 中，这些架构组件比单纯 model scaling 更基础。

简短架构入口见 `ARTICLES/02-architectural-contributions-zh.md`。

## 5. v0.6 是否替代 v0.5？

不是。

v0.5 仍然是稳定核心架构。v0.6 在此基础上扩展，澄清 active persistence、persistence targets、capability provenance、observable stability、multi-dimensional outcome、scenario specification 和 scenario-defined existence semantics。

面向读者的简短版本见 `ARTICLES/04-v0.6-extension-zh.md`。

## 6. active persistence 会让 EVA 更倾向冒险吗？

不是。

Active persistence 的意思是：inaction 也要作为一种可能 trajectory 被评估，而不是自动视为安全。若不行动对 future viability 的损害大于行动风险，EVA 可以采取 bounded risks。但这些风险仍然受到 anchors、release authority 和 unrecoverability floors 约束。

## 7. 什么是 scenario specification？

Scenario specification 是 v0.6 中用于将 EVA 应用到新环境的纪律，目的是避免理论每遇到新环境就膨胀。

一个 scenario 应说明相关的 existence-field conditions：existence semantics(在该 field 中什么算持续存在、什么算 recoverable interruption、什么算 terminal failure)、active persistence targets、drive dimensions、capability sources and provenance、action-space constraints、outcome interpretation 和 observable stability traces。只有当新环境无法用现有框架表达、造成内部矛盾，或暴露出边界失败时，才应考虑理论扩展。
