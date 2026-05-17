# Related Work and Positioning

*一篇简洁的面向读者说明，用于解释 EVA 与相邻 agent 和研究传统的关系。*

English: [03-related-work-and-positioning.md](03-related-work-and-positioning.md)

---

**关于本文。** 这不是完整 literature review。它的目标更窄：帮助读者把 EVA 放在相邻的 agent framework、self-maintenance tradition 和 safety/control work 中理解，同时避免夸大 originality。

EVA 不是第一个讨论 persistence、self-maintenance、internal state 或 intelligent systems 中 architectural constraint 的 framework。这些主题已经出现在若干相邻传统中：long-running agent frameworks、cognitive architectures、active-inference 与 homeostatic-control traditions、artificial-life thinking，以及关于 corrigibility 和 behavioral constraint 的 AI safety work。

EVA 的 claim 更窄。

它认为，对于一类特定 agent，即价值依赖 **continuous existence under changing conditions** 的 agent，主流 task-centered framing 在结构上不充分。因此，EVA 不把自己定位为当前 agent framework 的 universal replacement。它是针对另一类问题的另一种架构答案。

## 1. EVA 与哪些现有工作相邻

几个已有方向与 EVA 的部分内容重叠。

**Task-centered agent frameworks**，例如 ReAct、AutoGPT、BabyAGI、LangGraph 及相关系统，已经处理 planning、memory、tool use、statefulness 和 long-running execution。EVA 在工程层面与它们相邻，但组织目标不同：这些系统通常为完成 task 或 workflow 而构建；EVA 则追问，当“在时间中保持同一个 agent”本身成为 primary constraint 时，需要什么架构。

**Predictive processing、active inference 和 homeostatic-control traditions** 已经把 regulation、internal state 和 viability 当作中心问题，而不是外围问题。EVA 明显比普通 workflow agent 更接近这些传统。不过，EVA 不被提出为 general theory of mind 或单一 computational principle。它的贡献更偏架构：为 continuity pressure 下运行的 digital agents 提出一种具体 layered arrangement。

**Artificial-life 和 autopoietic traditions** 也很重要。EVA 不声称自己发现了 self-maintenance 的重要性。Persistence 和 boundary-maintenance 是 foundational 这一更深直觉，已经存在于这些传统中。EVA 试图把这个直觉 operationalize 到 digital agents 上，同时不要求更强的 claim，即这类 agent literally alive。

**AI safety and control work**，包括 Constitutional AI、corrigibility、shielded control，以及关于 drift 或 self-preservation 的相关工作，与 EVA 的关切相交：long-running systems 不应简单优化 unconstrained continuation。EVA 应与这些文献对话，而不是站在它们之外。

## 2. EVA 声称什么、不声称什么

EVA **不**声称发明了：

- persistent 或 long-running agents
- internal motivation 或 drive-like state
- layered 或 modular control
- constraint-based safety mechanisms
- distinct from deliberation 的 action-selection mechanisms

这些主题都有重要先例。

EVA 提出的更具体 claim 是：

> 对于 primary property 是 continuous existence under changing conditions 的 agent，这些 ingredients 需要以不同于主流 task-centered systems 的方式排列。

EVA 应在这个层面被评价。

## 3. 主要差异点

EVA 的独特性集中在少数 architectural commitments 上。

### 3.1 Continuous existence 作为 first-order design constraint

多数当前 agent framework 假设 agent 存在是为了完成任务。EVA 从另一个问题开始：

> 一个 agent 必须维护什么，才能在时间中作为同一个 agent 持续存在？

这个 shift 是 framework 的主要差异。EVA 的其余部分都从这里推出。

### 3.2 Drive 是 contextual broadcast，不是 command

许多系统要么从外部任务借用 motivation，要么把 motivation 表示为 explicit objectives、instructions 或 reward terms。EVA 则把 drives 视为 continuously broadcast internal context。Reasoning layer 在 drive state **之内**运行，而不是从 drive state 接收命令。

### 3.3 Anchor 是 pre-generative structural constraint

许多 alignment 和 control scheme 在 candidate outputs 或 actions 已经可用之后才约束行为。EVA 的 anchor claim 更强：anchors 作用在 candidate-space formation 层级。架构应在已经受限的 domain 内生成，而不是先广泛生成再过滤。

### 3.4 Action selection 是 independent peer circuit

EVA 不把 candidate generation、evaluation 和 release 塌缩成单一无差别 reasoning core。它把 action release 视为带 default inhibition 的 distinct architectural function。这很重要，因为 existence-centered agent 不应默认 action-ready。

### 3.5 显式 scope conditions

EVA 不声称 universality。它显式绑定到一个更窄 regime，其中：

- continuity matters，
- environment changes，
- finite design-time specification is insufficient。

这种 scope discipline 是 framework positioning 的一部分，不是事后添加的 caveat。

## 4. 关于原创性

EVA 最强的 originality claim **不是**每个 component 都前所未有。更准确地说，EVA 把相邻思想组合成一个更显式的 organizing framework，用于一个更窄也更苛刻的问题类。

可以简洁表述为：

- EVA 的许多邻近主题已经存在于 prior work；
- EVA 不声称发明了 persistence、internal drives、layering 或 constraint；
- framework 的独特性在于，当 continuity 被视为 first-order 时，它如何安排这些元素。

更具体地说，EVA 最可辩护的 differentiators 是：

- **problem framing** — continuous existence 被视为 distinct design regime，而不是 operational convenience；
- **architectural placement of drive** — drive 被视为 contextual broadcast，而不是 command；
- **architectural placement of constraint** — anchors 旨在作为 pre-generative structural restriction，而不仅是 post-hoc filtering；
- **architectural placement of action release** — selection 和 release 不塌缩进 reasoning core；
- **scope discipline** — EVA 明确限制在 continuity、non-stationarity 和 finite pre-specification 同时重要的系统中。

这就是 EVA 应被理解为 original 的意义：不是声称此前无人讨论 persistence 或 constraint，而是声称一旦 continuity 被视为 first-order，这些关切会 justify 一种不同架构。

## 5. 可复用的简短定位语

如果未来写作需要更短表述，可以使用：

> EVA 最好被理解为一种 continuity-first organizing framework，面向一类更窄的 agent，而不是从零发明 persistence-oriented agents。它借鉴关心 self-maintenance、architectural control 和 long-running agency 的相邻传统，最清楚的差异在于它如何在架构中放置 motivation、constraint 和 action release。

## 6. 下一步读什么

范式 framing 见 `ARTICLES/01-paradigm-introduction-zh.md`。

更详细的工程 commitments 见 `ARTICLES/02-architectural-contributions-zh.md`。

完整理论，包括 scope、derivation、anchor formalization 和与相邻 framework 的关系，见 `THEORY/v0.5-integrated.md`。
