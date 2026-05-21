# Round C-1 — v0.6 Visuals Merge Experiment — G1 Intake（C）

**By**：C（eva-theory 文档维护） · 2026-05-21 · 待 A G1 批
**已读**：
- v0.5 基准：`VISUALS/five-layer-overview-zh.svg`（viewBox 1400×1290，~162 元素：29 rect/104 text/5 path/24 line）、`VISUALS/signal-flow-zh.svg`（1400×1290，~160 元素）。
- v0.6 draft：`VISUALS/draft1-core-in-field-zh.svg`（1600×1120，~100 元素，127 行）、`VISUALS/draft2-active-persistence-zh.svg`（1400×920，~65 元素，95 行）。
- 正文：`THEORY/v0.6-extension.md` §2（含 §2.1-2.3 七层 persistence target、§2.4 recoverable vs terminal）、§8.4（existence-semantics 声明枚举）、变更记录 rev2 条目。

---

## 1. Feasibility 结论：GO（条件性）
一张竖向长图**可行**，且铰链叙事**理论上成立**——§2 开篇正本就是把"field 声明 existence semantics、framework 只 honor 不 override"放在"结构层级（§2.1-2.3）"与"个体生死动态（§2.4）"**之间**。所以用 existence-semantics 作"上承结构、下启动态"的唯一中枢，是忠于正文的结构，不是为合并硬造的连接点。
**但**：唯一实质风险=拥挤，集中在上段（见 §2）。故 GO 附带预置回退判据。

## 2. 拥挤风险 + 预置回退判据（诚实判断 > 硬合）
- **体量现实**：v0.5 两张各≈160 元素、各自占满 1400×1290 整幅。合并=把"结构带 + 中枢 + 动态带"竖向叠三段；若每段都做到 v0.5 密度，整图≈230-300 元素、高≈1400×3000-3400。中枢（6 项 existence-semantics）本身轻，是天然"细腰"，对清晰有利。
- **风险点=上段（结构带）**：v0.5 `five-layer` 的密度里含一块 380×985 的 anchor-system 侧栏 + L1-L5 栈 + operational content。若上段必须原样复现完整 anchor 侧栏，单上段就≈一整张 v0.5，叠上动态带后总高 > ~3600，会从"详尽"滑向"过长/过密/失清晰"。
- **预置回退判据（G2 我按渲染自查诚实裁定）**：若执行中上段无法压到"低于完整 five-layer 密度"（仍需 v0.5 全量 anchor 侧栏），则**回退两张**——图A=结构+中枢、图B=中枢重述+动态，两图共用 existence-semantics 母题衔接。回退是有效 A/B 结论，非失败。

## 3. 合并结构方案（竖向三段；减冗 = 控拥挤关键）
- **上段 结构/本体**：同一 core + 可替换 field（对标 `five-layer`：L1-L5 + operational content + anchor 跨层）。§2.1-2.3 的"七层 persistence target"以**分类语言**轻量呈现，且**不与 L1-L5 架构层混淆**。
- **中段 中枢铰链**：**existence-semantics 声明（6 项）**——全图唯一一次出现；画出"上接 field 结构声明、下启个体生死"的双向连线/锚点。
- **下段 动态/生命**：active vs passive + `RUNNING↔INTERRUPTED→TERMINAL→NEW INDIVIDUAL` 状态机 + active-persistence 闭环（rate-sensing→future viability→anticipatory pressure→bounded action）（对标 `signal-flow`/draft2；§2.4 + §1）。
- **减冗（合并红利，请 A 在 DP-C1 确认）**：draft1 底部 swap-strip 与 draft2 的 "THE FIELD DECLARES" 注记，本质都是"field 声明 existence semantics"——**折叠进中枢、不再各画一次**。这正是把"重复"变"统一卖点"的关键，也是控制拥挤的主要手段。

## 4. existence-semantics 项数差异标注（★ 供 A 决定是否同步）
- **eva-theory 正文 = 6 项**（`THEORY/v0.6-extension.md` §8.4 行 1077-1082，与 draft1 "framework 只读取这六项声明" 完全一致）：
  1. continuity criterion（继续存在判据）
  2. recoverable interruption（可恢复中断）
  3. terminal failure（终止失败）
  4. individual boundary（个体边界）
  5. reset semantics（重置语义）
  6. inheritance channel（继承通道）
  - §2 开篇（行 319）只行内点到其中 3 项（continued existence / recoverable interruption / terminal failure）；**权威枚举在 §8.4**。
- **eva-agent rev2 = 8 项**（A 指令：对齐 `ExistenceSemantics` dataclass）。多出的 2 项在 eva-theory 正文中**未命名**；属 eva-agent 仓，C 未越界去读。
- **本图按 eva-theory 6 项做**（遵指令：按正文、不擅改理论项数）。**请 A 裁 DP-C2**：(a) 保持 6 项（理论权威，**推荐**——不让一张图反向驱动理论改项数）；或 (b) 提供那 2 项以在图中呈现 8 项，并另行决定是否回填 eva-theory §8.4。
- **勿混淆**：正文另有 "outcome vector = **8** components"（§8.6 行 1108），那是结果维度，与 existence-semantics 的 6/8 无关。图中四种枚举（**5** 架构层 / **7** persistence 层 / **6** existence-semantics / **8** outcome 维度）须视觉区分，否则是额外的失清晰来源。

## 5. v0.5 风格基准核对（= 验收口径）
确认并将复用：
① 标题/段标/区块标题 `中文（English）`、主标题中文起首；② 每专业术语 inline `中文（english）`；③ 全角中文标点（，、；）替半角 `,`/`()`；④ 顶部写 Layout 注释块 + 正文左对齐到统一 x（five-layer 用 x=225）；⑤ 调色 core teal `#0d6e6a`/`#0a5450`、field/anchor amber `#c89726`/`#b5760a`/`#7a5208`，弱支撑层用灰虚线（L4/L5）；⑥ 每主要单元配 icon；⑦ EN + zh 双版本、内容对齐；⑧ 体量接近 v0.5 单图细致度。
当前 draft 违反 ①③④⑥（大量 raw English、半角括号、无 Layout 注释、icon 偏少）——合并版需逐条补齐。

## 6. 待译清单确认
指令 §3.2 待译清单与 draft raw English **核对一致、可用**。建议补 2 个 draft/v0.5 出现但未列入：`mediator role`→中介角色、`tool edge`→工具边缘（若上段含 L3 释放路径）。保留 inline-English 同 v0.5：`G(s)→A'(s)` / `LLM` / `RPE` / `HP=0` / `§` 编号；`burn rate`（若上段含 L2+ emergent anchor 则译"消耗速率"）。

## 7. 决策点（请 A 在 G1 裁示）
- **DP-C1（减冗授权）**：同意把 swap-strip + "field declares" 注记折叠进单一中枢、并在不损 v0.5 信息量前提下压缩上段 anchor 侧栏密度？（控拥挤主手段）
- **DP-C2（项数）**：existence-semantics 图中用 **6**（推荐）还是 **8**（需 A 提供 2 项 + 决定是否同步正文）？

## 8. 红线自检
- 未改任何 draft（`draft1-*`/`draft2-*`）、未改 v0.5 `five-layer`/`signal-flow`、未改理论正文（`THEORY`/`ARTICLES`）。
- 本 intake 仅在 sandbox `VISUALS/tmp-merge/` 落档；未引入与理论不符的新概念。
- SVG 产出（`merged-core-field-persistence{,-zh}.svg`）待 APPROVED 后做：zh 先定稿 → 镜像 EN。
