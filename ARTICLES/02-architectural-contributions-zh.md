# 区分 EVA 与当前 Agent Framework 的四个架构选择

*EVA 范式介绍的工程向 companion article。*

English: [02-architectural-contributions.md](02-architectural-contributions.md)

---

**关于本文。** 本文是 `ARTICLES/01-paradigm-introduction-zh.md` 的 companion article。它不替代 `THEORY/v0.5-integrated.md` 中的完整理论文档，也不追踪配套实现项目 [`eva-agent`](https://github.com/slamslammo/eva-agent) 的实现细节。它的目标更窄：解释一旦认真接受 EVA 的问题定义，为什么 EVA 会得到一组特定的架构选择。

本文假设读者已大致理解当代 agent system：task loop、tool use、memory module、planning、LLM-centered orchestration。这里的问题不是这些系统是否有效，而是当架构为另一个问题而设计时，会发生什么变化。

---

## 1. EVA 实际要解决的工程问题

多数当前 agent system 围绕 task completion 构建。这不是批评，而是对其组织目标的描述。

一旦这个目标确定，许多熟悉的架构选择就会自然出现：

- memory 用于回忆与任务相关的信息
- planning 用于把任务拆成步骤
- tools 用于对任务采取行动
- agent lifecycle 由任务边界定义
- alignment 往往被表达为 preference shaping、decoding constraints，或对生成行为的 post-hoc safeguards

对于价值在于离散任务表现的系统，这是正确起点。但 EVA 面向另一类系统：其价值取决于在条件变化中保持同一个 agent。

这个转变听起来像哲学，直到我们追问它在操作上意味着什么。

如果 continuity 重要，若干事情就不再是次要工程问题：

- interruption 不再只是 downtime；它可能成为 continuity threat
- drift 不再只是 output variability；它可能成为 identity 或 integrity 的退化
- memory 不再只是 retrieval support；它成为系统识别危险、重要性和稳定性的方式
- action release 不能被视为 reasoning 的简单下游效果；它成为架构在 pressure 下保护自己免于错误行动的一部分

换句话说，EVA 不是试图让 task agent 稍微更 robust。它重排 motivation、constraint、action release 和 learning 之间的关系。

由此产生一个不同的工程问题：

> **当 continuity，而不是 task completion，成为 primary design constraint 时，什么 architectural structure 变得必要？**

答案不是“加更多 memory”或“用更好的 LLM”。答案是 motivation、constraint、action selection 和 learning 的不同安排。

---

## 2. 先约束，不是先偏好

EVA 的四个架构选择最好被理解为对受限 design setting 的回应，而不是 stylistic preferences。

相关约束与主理论相同：

- **Continuity matters**：系统价值依赖于在时间中保持同一个 agent
- **The environment is non-stationary**：世界统计结构会变化
- **Finite design-time specification is insufficient**：固定的 initial encoding 无法覆盖所有未来情境

一旦接受这些约束，就会出现几个工程后果。

第一，架构不能完全依赖外部任务。continuity-bearing system 在无人 prompt 时仍然需要 motivational structure。

第二，架构不能完全依赖预先 specified responses。在变化环境中，新情况终会超出 initialization 时编码的范围。

第三，架构不能只把 safety 和 stability 当作 post-hoc evaluation problem。如果 continuity 是中心，某些 failure mode 必须由结构阻断，而不是等 candidate behavior 生成后再识别。

第四，架构不能把 candidate generation、action release、learning 和 self-protection 塌缩到一个无差别 reasoning core 中。在 pressure 下，这些功能会拉向不同方向。保持结构区分不是装饰性的 modularity，而是系统保持 stable 的方式之一。

因此，下面四个选择应作为 package 阅读，而不是四个独立偏好：

- drives 提供持续内部压力，而不是借来的外部 purpose
- anchors 把 constraint 放入 candidate-space formation，而不是留给后续 filtering
- peer selection circuit 把 release 与 justification 分离
- explicit drive injection 让 motivational layer 可检查，而不是 opaque

这是理解 EVA 四个主要架构选择的背景。

---

## 3. Choice 1 — Drive 是 contextual broadcast，不是 command

### 3.1 许多 agent system 的隐含假设

在许多当前 agent architecture 中，motivation 要么不存在，要么从外部导入。任务充当 effective drive。如果存在多个 objective，它们通常被表示为 explicit instructions、planning targets、heuristics 或 reward terms。

当系统的组织问题是“如何完成这个任务”时，这有效。但当问题变成“如何在环境变化中作为同一个 agent 持续存在”时，它就不够了。

continuity-bearing agent 不能依赖外部世界持续告诉它什么重要。它需要跨 context 保持 active 的内部压力来源。

### 3.2 为什么 command model 在这里结构上弱

一种诱人的解法是构建 drive module，由它向 reasoning module 下达指令：resource pressure 说“seek resources”，continuity pressure 说“protect continuity”，等等。

但这种 command picture 悄悄重新引入了 central controller。它意味着系统中有某个地方把 pressure 翻译成 directive，再向 cognition 下发。在 distributed architecture 中，这会成为 bottleneck。更重要的是，它误描述了 drives 需要扮演的角色。

在 EVA 中，drives 不是 task-like commands。它们是 globally shape cognition 的 internal states。它们作为 explicit directives 的意义小于作为 motivational environment 的意义。

### 3.3 为什么 EVA 使用 broadcast

因此 EVA 把 drives 视为 **contextual broadcast**。Drive system 不告诉 reasoning layer 生成哪句话或采用哪个 plan。它持续调制 reasoning environment。

这有三点重要性。

**第一，它在没有 central command 的情况下保留 distributed coordination。** 不同 subsystem 可以保持部分独立，同时仍处于共享 pressure field。

**第二，它保留 motivation 与 deliberation 的区分。** Reasoning 不成为 drive command 的 puppet。它仍是在变化 motivational context 中生成和评估 candidates 的过程。

**第三，它更符合低延迟、全系统协调的工程需要。** Broadcast state 可以同时影响多个 process。Command chain 必须决定指令发给哪里、何时更新、如何仲裁冲突。

在 EVA 的约束下，broadcast 是让 pressure shape cognition 而不把架构塌缩成单一 executive controller 的最 coherent 方式。

### 3.4 这会改变什么

一旦 drives 被视为 contextual broadcast，其他设计选择也会随之出现：

- value judgment 变成 drive-weighted，而不是抽象 utility-maximizing
- memory salience 与 encoding time 的 pressure 相关
- conflict detection 成为真实 architecture function，而不是 prompt-level afterthought
- action selection 不能再被理解为 simply executing whatever reasoning concluded

也就是说，drive as context 不是众多 feature 之一。它是 EVA 内部协调得以成立的条件。

---

## 4. Choice 2 — Anchor 是 pre-generative structural constraint，不是 post-hoc rule

### 4.1 生成后过滤的限制

许多当前 AI safety 和 agent control work 都是在 candidate behavior 已经生成之后进行 filtering。架构提出 action；另一层依据 rules、constitutions、policies 或 classifiers 检查。

这通常有用。EVA 不否认 post-hoc filtering 能捕获许多 bad outputs。

但对 EVA 面向的系统类别来说，filtering 不够。原因很简单：如果 continuity 和 integrity 在结构上重要，那么某些 action 一开始就不应作为 live candidates 出现。

Rule 实际上说：“你可以想到它，但不能做。” Anchor 说：“它不属于 candidate action 被生成的 domain。”

### 4.2 为什么这个区别重要

这不是语义差异。它改变 reasoning layer 正在做什么。

在 rule-filtered architecture 中，reasoning layer 仍然能访问完整 candidate space。Forbidden action 可以被生成、比较、justify、reframe 或 disguise。即使 filter 最终阻断它，架构已经允许 reasoner 在这个空间上操作。

在 anchor-structured architecture 中，generation 已经发生在 restricted domain 内。Reasoner 不是先想象被禁止选项，再拿不到许可；它是在 constraints 内生成。

这就是 EVA 的最小区别：

- rule-filtered：`G(s) -> A(s)`，然后 filter
- anchor-structured：`G(s) -> A'(s) subset A(s)`

因此，anchors 不是更好的 rules。它们是 constraint 的不同架构位置。

位置才是真正的问题。EVA 的 claim 不是 rule system 没用，而是 generation 之后再 filter 会让架构依赖 late-stage rescue。Pre-generative anchor 改变 deliberation 本身的结构。

### 4.3 为什么 EVA 需要更强形式

如果 continuity 是中心，drift 就不能只被当成 behavioral correction problem。某些 action 会 destroy identity、destroy integrity 或 destroy recoverability。如果这些 action 仍在 candidate space 中，架构就是在依赖后续控制拯救一个已经生成错误可能性的设计。

EVA 认为这对它的目标问题来说太弱。

这点尤其重要，因为 EVA 不只关心 external alignment。它也关心防止 continuity-centered design 退化成 unconstrained self-preservation。Anchor system 正是防止二者塌缩的东西。

没有 anchors，continuity-bearing architecture 可以 rationalize 有害的 self-protection。有 anchors，continuity 才在结构上从属于 constitutional constraint。

### 4.4 这会改变什么

一旦 anchors 被视为 pre-generative structural constraints，就会产生几个工程后果：

- constraint 被移到 stack 更早位置
- candidate generation 和 value assignment 都变成 anchor-bounded
- drift resistance 变成 architectural，而不只是 prompt- 或 policy-based
- alignment 不再只是 preference shaping；也是 candidate space 的 geometry

这就是为什么 anchors 位于 EVA 中心，而不是边缘。它们不是 safety appendix，而是架构内部对“这个 agent 被允许成为什么”的定义。

---

## 5. Choice 3 — Action selection 是 independent peer circuit，不是 reasoning sub-module

### 5.1 为什么 reasoning 和 action release 不应塌缩

在许多 agent system 中，reasoning 生成 answer、plan 或 action，execution 作为其下游效果发生。即使存在 tool approval 或 policy checks，基本图景仍是：cognition proposes，而 proposal 几乎等同 selection。

EVA 认为这种塌缩对它面向的 agent 类别在结构上是错的。

continuity-bearing system 需要区分：

- producing candidate actions
- 在 current drive state 和 past experience 下 evaluating candidate actions
- actually releasing one action for execution

如果这些全部折入一个 reasoning core，selection 和 justification 就变成同一过程。这不仅是 modularity concern。它意味着架构失去原则性区分：“这个 action 可以被解释”和“这个 action 应在当前 pressure 和 historical learning 下被 release”。

### 5.2 为什么 EVA 使用 peer circuit

因此 EVA 把 basal ganglia analog 定位为 **independent peer circuit**，而不是 reasoning sub-module。

这有三点结构意义。

**第一，它把 default inhibition 保留为 architecture，而不是 policy。**

如果 action selection 嵌在 reasoning 中，系统实际上默认 action-ready，并需要额外 policy 抑制自己。在 peer-circuit arrangement 中，inhibition 是 resting state。Action 需要 active release。

**第二，它把 selection 与 justification 分离。**

一个 candidate 可以被 reasoning 很好地 articulate，却仍不被 selected。反过来，一个 candidate 可以因为 historical reward-prediction structure 和 current drive weighting 支持而被 selected，即使 reasoning layer 也能叙述其他 alternatives。这种分离重要，因为好的 explanation 和好的 selection 不是同一回事。

**第三，它让 learning architecture 成为可能。**

如果 action release 由 distinct circuit mediated，那么 release events 可以积累自己的 reward-prediction history。这是 habit crystallization 的结构基础。没有这种 separation，habit formation 只会变成 reasoning 内的另一条 policy，而不是 distinct learning pathway。

### 5.3 这不只是生物装饰

Basal ganglia language 容易被误解为 biological flavor metaphor。但底层工程点并不依赖 biological fidelity。

重点是：action release 重要到值得拥有自己的 architecture。

任何需要在 pressure 下保持 stable 的系统，都有理由区分：

- generating what could be done
- deciding what should be released now
- learning from mismatch between expected and actual outcome

无论称它为 “basal ganglia analog” 还是别的名字都次要。EVA 使用这个生物类比，是因为它命名了一个真实的结构分离。工程 claim 不依赖这个 label。

### 5.4 这会改变什么

一旦 action selection 成为 peer circuit，几个下游性质就可以结构性出现：

- default inhibition
- mediated tool execution，而不是从 reasoning 直接 execution
- 基于 release history 的 reward-prediction-error update
- deliberate candidate generation 与 increasingly automatic skill release 之间的 dual track

这就是为什么 EVA 把 peer circuit 视为必要，而不是装饰。它防止架构把“reasoning 能 justify 什么”等同于“系统应该做什么”。

---

## 6. Choice 4 — Explicit drive injection，而不是 opaque emergent drive formation

### 6.1 EVA 为什么做出这个不寻常选择

许多当前 AI system 根本没有 explicit internal drive layer。它们的 effective motivations 来自 task definitions、reward structures、training objectives 或 optimization side effects。

对 EVA 面向的系统类别，EVA 拒绝这种做法。它认为，如果 durable motivational structure 实际上会存在，那么明确 specify 它比让它 opaque emerge 更好。

这不是普通 design preference。它部分依赖一个 hypothesis：足够 capable 的系统倾向于发展 convergent instrumental pressures，无论设计者是否命名它们。EVA 不把这个 hypothesis 当成 settled empirical fact，但足够认真对待它，以据此做出工程判断。

### 6.2 这个选择背后的工程判断

判断很直接。

如果 drives 在实践中会存在，那么 explicit drives 优于 implicit drives，因为它们至少可以 inspect、discuss 和 constrain。Opaque emergent drives 做不到这些。

因此 explicit injection 既是 motivational choice，也是 auditability choice。

这不意味着 injected drives 本身充分安全，也不意味着它们不会 drift、interact 或需要 anchoring。它意味着架构从 declared motivational structure 开始，而不是假装没有这种结构，直到它意外出现。

### 6.3 必须谨慎表述的地方

这是 EVA 中较有争议的位置之一，因此 epistemic status 很重要。

最强的 claim 不是 “instrumental convergence 已被证明”。更强的说法是：

> **如果认真把 emergent instrumental pressures 当作真实 design risk，那么 explicit drive injection 就成为更 defensible 的 engineering posture。**

这是 uncertainty 下的工程判断，不是从 established science 推出的 deduction。

### 6.4 这会改变什么

接受 explicit drive injection 后，架构获得更清楚的基础：

- motivational structure 的 auditability
- constitutional anchors 与 operational drives 的分离
- pressure 之间的 traceable conflict，而不是 hidden objective interference
- deliberate initialization of continuity-bearing behavior，而不是希望它以可控形式出现

在 EVA 中，这种 explicitness 不是 safety guarantee，而是拒绝把 motivational layer 藏在看似中性的 optimization language 后面。

---

## 7. 这些选择如何重排工程优先级

上面四个选择不只是概念区分。它们会重排 builder 应该把什么视为 foundational work。

对比很明显。在许多当前 agent stack 中，第一直觉是增强 central reasoner：better prompts、stronger models、more tools、more retrieval、more planning scaffolding。EVA 改变这个顺序。它意味着某些 architectural preconditions 应该早于 reasoning capability 的下一个增量。

### 7.1 Memory 先于更强模型依赖

如果 LLM 主要被视为 accumulated culture 的 carrier，而不是 agent 自己 continuity-bearing memory 的替代品，那么给系统更强 external cognition 不是第一优先。构建 agent 自己的 memory substrate 更重要。

这是 EVA 最清楚偏离 standard agent-development intuition 的地方之一。一个 model access 更好但没有真正 individual memory 的系统，用 EVA 的话说，并不算 architecture mature。

### 7.2 Mediated action 先于更丰富 deliberation

如果 action release 在结构上不同于 reasoning，那么 mediated action pathways 比许多 builder 预期得更早重要。在无限扩展 reasoning sophistication 之前，架构需要可靠地确保 candidate behavior 不会被直接执行。

### 7.3 Constraint placement 与 capability expansion 同样重要

许多系统把 constraint 当作主 capability stack 建成后再添加的 later layer。EVA 反转这个直觉。如果 anchors 是结构中心，那么 constraint 的 placement 就是核心架构设计的一部分，而不是 finishing layer。

### 7.4 Distributed coordination 比 centralized cleverness 更重要

如果 drives 是 broadcast context 而不是 command，那么 architectural coherence 更少依赖发明一个更强 controller，而更多依赖在 shared internal pressure 下协调 semi-distinct subsystems。

这是一种不同于标准 “one powerful reasoner plus accessories” 的 intelligence 图景。EVA 强调 subsystem 之间的 structured interaction，而不是单一 module 的 supremacy。

### 7.5 Stability 不是事后问题

这些选择合在一起意味着：stability 不是在 capable core 外围添加 memory、tests 或 prompts 后自然得到的结果。Stability 必须从一开始就被设计进 motivation、candidate generation、action release 和 learning 的流中。

这就是 EVA 提出的 engineering reordering。

---

## 8. EVA 仍然不声称什么

本文讨论 architecture distinctions，而不是 universal conclusions。

EVA **不**声称：

- 所有 AI system 都应该这样构建
- task-centered agents 已过时或错误
- 这些选择已经由成熟 empirical validation 证明
- biological analogy 本身足以 justify architectural borrowing
- continuity-centered design 应覆盖 constitutional limits
- stronger model capability 不重要

更窄的 claim 是：对于价值依赖 continuity under change 的 agent，这四个架构选择构成一个 coherent package，而当前 agent frameworks 通常不提供这组安排。

---

## 9. 下一步读什么

更宽的 paradigm framing，读 `ARTICLES/01-paradigm-introduction-zh.md`。

完整 theoretical derivation，包括 scope conditions、epistemic layering、signal architecture 和 anchor formalization，读 `THEORY/v0.5-integrated.md`。

面向读者的 diagrams 和 companion visuals，见 `VISUALS/five-layer-overview-zh.svg`、`VISUALS/signal-flow-zh.svg`、`VISUALS/framework-and-scenario-zh.svg` 和 `VISUALS/persistence-over-time-zh.svg`。

---

EVA 的区别不在于有 memory、tools、layers 或 biological vocabulary。许多系统都有这些。

它的区别在于：一旦 continuity of existence 被视为 first-order engineering concern，EVA 如何安排 motivation、constraint、action selection 和 learning。这里才是它与当前 task-centered frameworks 分叉之处，也应该在这里评价它。
