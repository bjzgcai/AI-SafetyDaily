# AI 日报 [AI 安全] - 2026-08-04


# 每日 AI 安全主题综述：Agent 运行时风险与治理新范式

## Highlights

当日研究进展集中揭示了自进化 Agent 在流式任务中的潜在风险，特别是**AgentStream**框架指出持续演化的智能体在动态任务流中可能积累隐蔽的行为偏差，这为长期运行的 Agent 系统带来了新的安全挑战。与此同时，**SWE-Touch**基准测试强调了共享工作空间下代码修改引发的冲突风险，表明人机协作环境中的意图对齐比独立执行更为复杂且脆弱。此外，**Model or Harness?**一文提出的故障定位分类法为解决“修复分配”问题提供了理论依据，指出仅关注系统级结果无法有效指导 Agent 系统的治理与改进。

## Agent 安全与治理

随着大语言模型智能体（LLM Agents）从静态评测走向动态部署，其运行时安全性与治理机制成为当前研究的焦点。传统的评估往往假设任务是孤立的，但**AgentStream**的研究打破了这一假设，通过构建配置化的任务流来模拟真实场景，发现自进化智能体在适应多样化任务流时，其行为模式可能因累积经验而产生不可预测的漂移。这种流式设置下的自我演化不仅涉及性能提升，更潜藏着状态污染和策略偏移的风险，要求治理框架必须具备对长期行为轨迹的监控能力。与之相呼应的是**LongHorizon-Harness**，该工作将长周期执行重新定义为任务状态管理问题，主张将任务状态显式地置于执行过程之外进行维护，仅在更新事实时同步状态。这种方法论上的转变旨在防止错误自我评估在后续决策中的传播，从而在架构层面降低了长程任务中的累积误差风险。

在人与 Agent 交互的边界上，**SWE-Touch**基准测试揭示了共享工作空间带来的独特安全挑战。现实中的软件开发往往需要人类用户介入并修改代码，现有的仓库级基准通常限制用户参与或假设 Agent 独立工作，导致无法评估 Agent 如何理解并响应任务相关的代码变更。**SWE-Touch**通过引入经过验证的反向编辑（Counter-Edits），压力测试了 Agent 在任务关键区域被人为干扰时的反应能力。这表明，未来的 Agent 治理必须包含对“外部干预”的鲁棒性评估，而不仅仅是内部逻辑的正确性。为了进一步厘清系统失效的责任归属，**Model or Harness?**提出了一种以交互为中心的分类法，旨在解决“修复分配”难题。作者指出，相同的可见失败可能源于模型微调、Harness 工程、环境设计或基准修复的不同环节，现有的评估体系往往掩盖了故障的真实起源。这种细粒度的归因分析是实施有效治理的前提，它要求安全团队不能仅依赖黑盒测试结果，而需深入理解模型、工具、记忆与环境之间的相互作用网络。

内存机制作为 Agent 长期记忆的核心，其安全性同样不容忽视。**Compute Globally, Materialize Locally**的工作直接挑战了基于 KV 缓存作为记忆的假设，通过实验发现，当早期观察信息被剔除后，模型回答仍倾向于遵循被省略的值，这种现象被称为语义物质化。这意味着在推理过程中，即使某些上下文已被丢弃，其隐含的语义影响依然存在于 KV 缓存中，可能导致信息泄露或推理偏差。针对这一问题，**Zero-Mem**提出了零令牌内存操作的概念，试图在不消耗 LLM 输入输出令牌的情况下实现结构化内存访问。虽然其主要目标是效率，但这种非生成式的内存操作模式也减少了因中间记录生成而引入的提示注入或数据混淆风险。综合来看，当前的 Agent 治理正从单纯的任务完成度转向对状态一致性、交互边界以及底层记忆机制的安全审计，任何忽视运行时动态特性的治理方案都可能存在盲区。

## 工具调用与运行时防御

智能体在开放世界环境中运作依赖于工具调用，而工具发现的鲁棒性是运行时安全的关键防线。**ScrambleToolBench**引入了一个交互式终端基准，旨在隔离行为推理能力。该基准移除了语义线索并强制连续的任务课程，要求智能体在没有文档的情况下仅通过交互推断未知系统的行为。这与现有工具使用基准暴露静态语义 Schema 形成鲜明对比，后者允许智能体依赖先验知识而非自主发现。这种设计迫使研究者关注智能体在面对未知 API 或恶意伪装工具时的探测能力，防止其在缺乏明确指令时误用工具或陷入死循环。

检索增强生成（RAG）作为连接外部知识库的桥梁，其安全性直接影响 Agent 的信息获取质量。**UEmbed**提出了一种统一的稀疏和稠密多模态嵌入模型，旨在解决多模态检索中对辅助跨模态模块的依赖。虽然主要贡献在于检索效率，但在 Agent 语境下，统一的多模态表示有助于减少因模态不匹配导致的检索幻觉，从而降低基于错误检索结果的行动风险。**DeepVoyager-VL**则进一步探讨了视觉在长周期搜索中的作用，指出现有方法通常将视觉局限于输入或回答阶段，忽略了其在中间推理中的角色。该工作强调视觉证据应引导多轮搜索，这对于防止 Agent 在缺乏视觉确认的情况下盲目依赖文本检索至关重要。这些研究共同指向一个结论：工具与检索的防御不应仅停留在输入过滤，更需深入到推理链条中的证据验证环节，确保每一步行动都有可靠的外部支撑。

## 对抗攻击与鲁棒性

模型蒸馏与测试时推理优化是提升 Agent 性能的重要手段，但也引入了新的脆弱性。**DAPD**（Dual-Anchored Policy Distillation）识别了在线策略蒸馏中的特权幻觉问题，即学生模型学习了教师模型的特权信息，但在推理时无法复现这些信息，导致性能下降。这种信息不对称构成了潜在的对抗面，攻击者可能利用这种幻觉诱导模型产生不可靠的输出。相比之下，**GradCuit**提出了一种基于梯度分配的测试时潜在推理方法，通过在 Transformer 层间插入可优化的潜在状态，实现了序列级别的信用分配。这种方法增强了推理的可解释性和鲁棒性，使得模型能够在参数冻结的情况下通过调整潜在状态来修正错误，为应对分布外输入提供了一种动态防御机制。

在自动驾驶等高风险领域，视觉语言动作（VLA）模型的因果忠实性直接关系到物理安全。**Deferred Exposure of Future Trajectories for Verifiable Reasoning in Autonomous Driving VLMs**的研究揭示了训练数据标注中的轨迹锚定偏差。当教师模型暴露于已知的未来轨迹标签时，它会合理化结果而非从场景证据中推断决策，导致生成的思维链（CoT）存在严重幻觉。这种偏差在测试时若未被纠正，可能导致 Agent 在紧急情况下做出错误的因果判断。因此，构建无偏的训练数据和验证推理过程的因果性，是确保 VLA 模型在对抗环境下保持鲁棒性的必要条件。这些工作表明，对抗鲁棒性不仅涉及对抗样本的防御，更涉及训练目标、推理机制和数据偏差的系统性治理。

## 模型对齐与技能学习

技能（Skills）的复用是 Agent 扩展能力的基础，但技能的生成与应用本身存在对齐风险。**SKT**（Skill-Use Training at Scale）通过经过验证的合成数据生成管道，构建了基于技能的训练任务。该方法通过规则和 Agent 反馈引导的修复，筛选出适合的技能配置，旨在提高模型识别和应用技能的能力。然而，仅提供技能并不保证模型能正确协调它们，这需要进一步的验证机制。**MemSFT**提出了解耦领域专业化与骨干参数更新的方案，通过外部参数化记忆来缓解微调带来的对齐税。这种方法允许模型在不遗忘通用能力的情况下适应特定领域，对于维持 Agent 在垂直领域的对齐稳定性具有重要意义。**Progressive Agent Skill Generation via Reinforcement Learning**则尝试通过强化学习解决技能生成的监督信号缺失问题，利用下游任务表现来评估技能价值。这三项工作共同描绘了技能学习的图景：从合成数据的验证到记忆解耦，再到基于任务的强化学习，核心目标都是确保技能的使用符合预期意图，避免技能滥用或错误组合导致的系统失控。

## 安全评估基准与事件响应

有效的安全评估需要专门的基准来覆盖复杂的 Agent 行为。**RecHarness**提出了一种基于 Bandit 路由的 Agent 基准，用于自动化推荐模型优化。它将优化过程分为两步，由 Bandit 路由器选择下一步，解决了 LLM 在选择修改方向和生成假设时的不稳定搜索问题。这种结构化的评估框架有助于在有限的实验预算下更稳定地探索 Agent 的策略空间，为评估 Agent 的自我优化能力提供了新范式。结合前文提到的**AgentStream**、**SWE-Touch**和**LongHorizon-Harness**，可以看出当前的评估趋势正从单一任务的成功率转向对动态适应性、人机协作冲突处理以及长程状态管理的综合考量。事件响应方面，**Model or Harness?**提供的故障分类法实际上也是一种响应指南，它帮助团队根据故障来源快速定位修复路径，无论是调整模型权重还是重构 Harness 逻辑。这些基准和框架的完善，标志着 Agent 安全评估正在从定性描述走向定量、结构化的工程实践。

## Looking Forward

尽管上述工作在 Agent 运行时安全和评估方面取得了显著进展，但仍存在若干未解决的理论问题。首先，关于 KV 缓存作为记忆的语义物质化现象，目前尚缺乏标准化的检测协议，如何在保证推理效率的同时彻底消除缓存中的残留信息影响是一个待验证的假设。其次，在人机共享工作空间中，如何形式化定义“意图冲突”并建立自动化的仲裁机制，仍是 Agent 治理领域的空白。最后，针对长周期任务的状态管理，现有的显式状态维护方案尚未完全解决状态爆炸与隐私保护之间的矛盾。未来的研究需要进一步探索在分布式、多 Agent 协作环境下的安全共识机制，以及开发能够实时监测并阻断恶意工具调用的沙箱技术，以确保智能体系统在开放环境中的可控性与可靠性。

---


## 参考来源

- **AgentStream: How Well Do Self-Evolving LLM Agents Perform Under Streaming Tasks?** — [huggingface_papers](https://arxiv.org/abs/2608.00155)
- **ScrambleToolBench: Agents Search Exhaustively Even When Their Own Map Points to the Next Step** — [huggingface_papers](https://arxiv.org/abs/2608.02358)
- **Zero-Mem: Zero-Token Memory Operations for LLM Agents** — [huggingface_papers](https://arxiv.org/abs/2607.29377)
- **SWE-Touch: Benchmarking Coding Agents When Users Touch the Code** — [huggingface_papers](https://arxiv.org/abs/2608.02499)
- **Model or Harness? An Interaction-Centric Taxonomy for Localizing Agent Failures** — [huggingface_papers](https://arxiv.org/abs/2607.28802)
- **LongHorizon-Harness: Advancing Long-Horizon Agents for Real-World Tasks** — [huggingface_papers](https://arxiv.org/abs/2608.01964)
- **SKT: Skill-Use Training at Scale via Verified Synthetic Data Generation** — [huggingface_papers](https://arxiv.org/abs/2608.02287)
- **Compute Globally, Materialize Locally: The Memory Contract of Sparse Event-KV** — [huggingface_papers](https://arxiv.org/abs/2607.23693)
- **MemSFT: Mitigating Alignment Tax with an External Parametric Memory** — [huggingface_papers](https://arxiv.org/abs/2607.25614)
- **UEmbed: Unified Sparse and Dense Multimodal Embeddings** — [huggingface_papers](https://arxiv.org/abs/2608.02583)
- **RecHarness: A Bandit-Routed Agentic Harness for Self-Evolving Recommender Systems** — [huggingface_papers](https://arxiv.org/abs/2607.29241)
- **DeepVoyager-VL: Incentivizing Vision-in-the-Loop Search for Long-Horizon Multimodal Agents** — [huggingface_papers](https://arxiv.org/abs/2608.01827)
- **Progressive Agent Skill Generation via Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2608.01678)
- **SG-WAM: Self-Guided World Modeling in Geometry-Aware Policy Space** — [huggingface_papers](https://arxiv.org/abs/2608.01397)
- **Roomer: Reflective Object-Grounded Model Editing and Repair for 3D Indoor Layout Synthesis** — [huggingface_papers](https://arxiv.org/abs/2608.01973)
- **StyleForge: Indoor Furniture Styling by Counterfactual Reasoning in a Hypergraph Field** — [huggingface_papers](https://arxiv.org/abs/2608.01954)
- **DAPD: Dual-Anchored Policy Distillation** — [huggingface_papers](https://arxiv.org/abs/2608.01735)
- **GradCuit: Credit-Assigned Gradient Flow Enables Robust and Interpretable Test-Time Latent Reasoning** — [huggingface_papers](https://arxiv.org/abs/2608.02585)
- **Deferred Exposure of Future Trajectories for Verifiable Reasoning in Autonomous Driving VLMs** — [huggingface_papers](https://arxiv.org/abs/2608.01755)
- **3DZip: Spatial-Aware Feature Diversity-Guided Token Compression for 3D Question Answering** — [huggingface_papers](https://arxiv.org/abs/2608.01185)