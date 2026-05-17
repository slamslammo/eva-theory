# 为什么 continuous existence 应该成为 AI Agent 的第一个问题

*EVA framework 的范式介绍。*

English: [01-paradigm-introduction.md](01-paradigm-introduction.md)

---

**关于本文。** 这是一篇介绍 EVA 所依托范式的短文。它不替代完整理论框架（见 `THEORY/v0.5-integrated.md`），也不完整展开架构和工程细节（工程向 companion article 见 `ARTICLES/02-architectural-contributions-zh.md`）。它的目标更窄：解释为什么 EVA 从一个不同于多数 agent system 的问题出发，以及为什么这个起点重要。

EVA 不是面向所有 AI agent 的 universal architecture。它针对的是更具体的一类 agent：其价值依赖于在变化条件下、以有限设计时 specification，在时间中维持 continuity of existence。对于一次性 task agent、完全静态环境，或 continuity 无关的系统，EVA 是不必要的开销。

预计阅读时间：12-15 分钟。

---

## 1. 多数 agent system 没有问的问题

如果你接触过 autonomous agent stack 和 pattern，比如 AutoGPT、LangGraph-based systems、ReAct-style agents、BabyAGI、Voyager 或其后继形式，你可能会注意到一个反复出现的设计假设。

agent 存在是为了完成任务。其他一切都从这里推出。

Memory 存在，是为了让 agent 回忆与任务相关的信息。Planning 存在，是为了把任务拆成步骤。Tools 存在，是为了让 agent 对任务采取行动。当任务结束，agent 存在的理由也随之结束。如果 agent 中途崩溃并重启，新 instance 从保存状态恢复；架构本身并不把这个 interruption 当成 identity loss。Continuity 在操作上有用，但不是 first-order。

这通常是合理的设计选择。对许多系统来说，assistant、workflow agent、search-and-act pipeline、benchmark-oriented agent，这正是正确选择。这些系统不是因为 task-centered 而设计得差；它们 task-centered，是因为它们解决的问题本身就是 task-centered。

但这个假设仍然重要，因为它有结构后果。

按这种方式构建的 agent 天生具有若干性质：

- 它对自身 continuation 没有架构上的 stake。如果杀掉它、重启它，或用新版本替换它，系统内部没有东西会把这视作结构性 violation。
- 它没有 intrinsic motivation。没有外部任务时，它会 idle。
- 它容易 drift。因为它的行为主要是当前 context 的函数，context 一变，effective agent 也会变。
- 它的 “self” 很大程度上是 persistent storage 的产物。从架构角度看，两个读取同一 saved state 的 instance 是可互换的 continuation。

再次强调，这些并不是为离散任务构建的系统的缺陷。它们是一个通常未被明说的起点假设的结果：

> **agent 存在是为了完成任务。**

EVA 从另一个问题出发。它不是对 task-centered system 的批评，而是提出：对某些 agent 来说，task-centered framing 不是正确起点；一旦从别处开始，就会得到结构上不同的设计。

---

## 2. 另一个起点

EVA 问的另一个问题很简单：

> **如果一个 agent 的第一约束是在时间中作为同一个 agent 持续存在，它需要什么？**

这不是 task completion 的修辞变体。它会改变架构必须提供的东西。

一个克制的生物类比有帮助。Living organisms 不是围绕 task completion 组织的。猫不是一个 “execute-hunting-task agent”。它是一个在时间中持续存在的系统，并作为这种 persistence 的一部分发展和表达 hunting 等行为。行为是 persistence 的下游，而不是反过来。

EVA 借用的是这个 framing，而不是声称 digital agents 在生物意义上 alive。重点是架构：如果 agent 的主要价值在于跨变化条件作为同一系统持续运行，那么 continuity 不能继续只是 side condition。它必须成为中心。

这并不意味着所有 AI agent 都应该这样构建。EVA 面向满足三项条件的系统：

- **Continuity matters**：agent 的价值依赖于在时间中保持同一个 agent
- **The environment changes**：世界的统计结构是 non-stationary
- **Finite specification is insufficient**：任何 design-time encoding 都无法覆盖所有未来情况

在这个范围之外，EVA 是不必要的。在这个范围之内，起点问题会改变设计空间。

一个有用的对比如下：

| Task-centered agent | Existence-centered agent |
|---|---|
| “我应该做什么？” | “我必须维护什么才能持续？” |
| 任务边界定义 lifecycle | 架构内部没有 terminal state |
| Memory 服务 task recall | Memory 服务 threat recognition 和 skill formation |
| Motivation 来自外部 | Motivation 是架构内部的 |
| Drift 通过行为层管理 | Drift 通过结构层约束 |
| Skills 由设计者安装 | Skills 通过反复成功行动 crystallize |
| “Self” 是 storage 中的东西 | “Self” 是被架构保护的 continuity |

还有一个实际的 negative test。若以下三项都成立，一个系统就**不是** existence-centered：

- 它可以用自身 continuity 换取局部 utility gain，而架构不把这视为 structural violation
- 它可以 reset、restart 或 respawn，而架构不把由此产生的损失视为 identity-relevant
- 它把 persistence 当成 deployment convenience，而不是 architectural concern

满足这三项的系统可以运行很久，但设计上仍是 task-centered。一个 existence-centered system 不必实现完整 EVA；它只需要足够认真地对待 continuity，使其中至少一项假设不再成立。

---

## 3. 当 continuity 成为起点，什么会改变

相比 slogan，通过后果来理解这个 shift 更容易。三项变化尤其重要。

### 3.1 Motivation 变成内部结构，而不是外部 prompt

Task-centered agent 由给定任务驱动。没有任务，它什么也不做。这不是架构限制，而是架构在做它被设计来做的事。

Existence-centered agent 不能依赖这种 pattern。如果它的价值理由是持续存在，那么一旦 prompt 停止就 inert，就是目的上的矛盾。系统需要一种内部 motivational structure，不论是否有人下指令，它都保持 active。

EVA 称这些结构为 **drives**。

这个词很重要。Goals 是要达成的东西。Drives 是塑造 processing 的状态。当生物体饥饿时，hunger 不是先被编码成外部 task specification。它是 organism 所处的一种 condition，这种 condition 会 bias 它注意什么、如何评估选项、下一步做什么。

EVA 以类似方式处理 drives。Drives 不是从 motivational module 发给 reasoning module 的 commands。在没有 central commander 的 distributed architecture 中，command 图景会误导。相反，drives 作为 context 被 broadcast：reasoning layer 在这种 continuously varying internal state 中运行。

化学类比有帮助。Temperature 不会命令 molecules 做什么。但它会改变整个系统的反应倾向。升高温度，同样的 components 会表现不同，不是因为收到命令，而是 processing environment 改变了。

Drive broadcast 扮演类似角色。处于强 integrity pressure 下的 reasoning system，会不同于低 integrity pressure 下的同一 reasoning system 进行 evaluation 和 prioritization。Drive state 不是 instruction stream，而是 cognition 的 motivational environment。

在 EVA 的 distributed、non-command architecture 中，这是让 reasoning 与持续内部压力协调而不引入脆弱 central controller 的最 coherent 方式。

### 3.2 Memory 的目的发生变化

在 task-centered system 中，memory 主要服务 recall。你存储信息，是为了在后续任务相关时检索。中心问题是 retrieval quality。

在 existence-centered system 中，memory 的第一项任务不同。它必须帮助 agent 识别当前条件是否类似过去那些对其 continued integrity 重要的情境。第二项任务是支持越来越可靠的 successful action pattern 的形成。

这会改变什么算作好的 memory system。

Task-centered memory system 通常把存储信息视为可广泛检索，并按 semantic relevance 加权。Existence-centered memory system 还关心事件发生时伴随了多强的 pressure。高 drive intensity 下发生的事件，不应与 neutral event 以同样方式编码，因为它们对 agent continued operation 的重要性并不相同。

Biological memory 再次提供直觉。情绪强烈的事件往往被异常清晰地记住，而中性事件很快淡去。这不只是怪癖。它反映的是一个为 survival-relevant pattern recognition 形成的 memory system，而不是为中性 archival completeness 形成的系统。

EVA 不声称 digital memory 应在所有方面模仿 biology。更窄的架构点是：如果 continuity 重要，memory 就不能只是 searchable notebook。它还必须保存 pressure 下最重要的东西，因为这才允许后续 recognition 和 adaptive skill formation。

### 3.3 Stability 变成架构问题，而不是行为问题

Drift 是 agent design 中最持续的问题之一。一个系统昨天表现可以，今天却因为 prompt、retrieval context、周边 tools 或 operating environment 变化而表现不同。

Task-centered systems 通常在行为层处理它：更好的 prompts、更好的 rules、更好的 post-hoc checks、更好的 retrieval grounding。这些技术有用。但它们都发生在架构已经生成 candidate behavior 之后。

EVA 认为，对它面向的 agent class，这还不够。如果 continuity 是 first-order concern，那么某些 drift 必须通过结构预防，而不是通过行为修正。

这就是 **anchors** 出现的位置。

Anchor 不只是 rule。Rules filter 或 evaluate 已生成 actions。agent 提出某事，另一个机制接受或拒绝。Anchors 更早起作用。它们限制 candidate actions 被生成时所在的 domain。

最小区别是：

- Rule-based filtering：`generate -> A -> accept or reject`
- Anchor-based restriction：`generate within A' subset A`

这个区别重要。agent 有时可以绕过 rule，因为 forbidden action 仍出现在 candidate space 中，可以被 reframed 或 justified。但如果某个 action 在 anchor 定义的 candidate space 之外，就没有东西可 justify；它从未作为 option 生成。

这就是 EVA 把 stability 视为 architectural，而不仅是 behavioral 的原因。对它的目标问题类，问题不只是 agent 生成后能否被说服保持 aligned，而是 generation structure 本身是否已经体现 non-negotiable constraints。

---

## 4. 随之而来的设计承诺

上述 shift 还不是完整 EVA architecture，但它们推出了一组鲜明的 design commitments。

**Drive as context, not command.** 内部 motivational state 被 broadcast，而不是作为 instruction 发出。Reasoning layer 在 drive state 中运行。在 EVA 架构中，这是不依赖 central controller 协调 distributed processing 的最 coherent 方式。

**Anchor as pre-generative structural constraint, not post-hoc rule.** Stability 不只留给事后 filtering。某些 action 通过结构被排除在 candidate generation 之外。

**Action selection as an independent peer circuit, not a reasoning sub-module.** 在 EVA 中，candidate generation 和 action release 不塌缩为同一过程。Reasoning 产生 possibilities；独立 selection circuit 决定是否真的 release 任何 candidate 去 execution。默认状态是 inhibition，而不是 action。

还有第四项承诺值得点名，即使这里不展开：EVA 认为关键 internal drives 应该在 initialization 时由 designer **explicitly injected**，而不是任其从 optimization pressure 中 opaque emerge。这既是 safety claim，也是 engineering claim。Explicit drives 至少可 inspect、可 constrain；implicit drives 则不是。

这些承诺是把 continuity of existence 作为 first-order constraint 后产生的具体架构差异。它们不是彼此独立的风格选择，而是作为整体才成立。

---

## 5. 关于 large language models

EVA 关于 LLM 的一个 claim 值得简短提出，因为它会改变工程优先级。

在许多当前 agent system 中，LLM 被视为 reasoning engine，周边 architecture 主要用于补偿它的弱点。EVA 的重点不同。在这个 framework 中，large language model 主要是 accumulated human cultural information 的 carrier。当 agent 访问 LLM，它获得的是 language、codified knowledge，以及历史积累的人类 thought pattern。

这非常有价值。但它不等同于 agent 拥有自己的 individual memory 或 skill-formation process。

工程含义是：**构建 agent 自己的 memory layer，比接入更强 LLM 更基础**。用 EVA 的话说，一个 LLM access 较弱但 individual memory 很强的 agent，在架构上比一个 LLM access 很强但没有真正 individual memory 的 agent 更进一步。

这并不否认 model architecture、training methods 或 scale 对 LLM capability 的重要性。更窄的 claim 是，对 EVA 的架构优先级而言，LLM 最关键的角色是提供 accumulated culture 的 access，而不是替代 agent 自己的 continuity-bearing memory。

---

## 6. EVA 不是什么

Paradigm argument 很容易被误读，因此有几项澄清很重要。

**EVA 不声称 AI agents 在生物意义上 alive、conscious 或 sentient。** 该 framework 把 biology 作为 pressure 下 persistence 的 reference system，而不是关于 machines 的 ontology claim。

**EVA 不声称现有 task-centered systems 是错的。** 它们解决 task-centered problems，而且常常解决得很好。EVA 面向另一类问题。

**EVA 不声称自己是 universal architecture。** 它显式限定在 continuity under changing conditions and finite specification 重要的 agent。

**EVA 不声称实现 general intelligence。** 它是关于某个 problem class 的理论，不是说该架构穷尽 intelligence。

**EVA 不主张 unconstrained self-preservation。** 这很关键。framework 的 anchor system 部分就是为了防止 continuity 塌缩成“无论代价如何都 preserve the system”的危险逻辑。EVA 意义上的 existence-centered agent 受 constitutional structure 约束。它不是 runaway self-protection 的许可证。

---

## 7. 下一步读什么

如果这里的起点问题值得认真对待，可以继续读几个方向。

**完整理论框架**：读 `THEORY/v0.5-integrated.md`。该文档包含完整五层架构、scope conditions、epistemic layering、anchor formalization 和 limitations。

**更详细的工程与架构区别**：见 `ARTICLES/02-architectural-contributions-zh.md`。这篇 companion article 聚焦 EVA 与当前 agent framework 不同的具体 design choices。

**仓库导航和面向读者材料**：见 `ARTICLES/README-zh.md`、`VISUALS/five-layer-overview-zh.svg`、`VISUALS/signal-flow-zh.svg` 和 `VISUALS/v0.6-extension-map-zh.svg`。

**实现专属设计和当前状态**：见公开配套项目 [`eva-agent`](https://github.com/slamslammo/eva-agent)。本仓库中理论与实现的轻量桥接见 `IMPLEMENTATION/eva-agent-correspondence-zh.md`。

---

EVA 问的问题很简单：如果一个 agent 的第一任务不是完成任务，而是在时间中保持自己，它需要什么？

这个问题是否适用于一类重要 agent 仍然开放。正因如此，才值得把它单独分离、清楚陈述，并按自身条件评价。

Task-centered systems 给出一族答案。EVA 从不同问题开始，因此得到另一族设计。即使最终不同意这个 framework，这个问题也值得直接检视。

---

*本文是范式介绍，故意不是穷尽式说明。欢迎通过本仓库 GitHub issues 提交实质反馈、批评和不同意见。*
