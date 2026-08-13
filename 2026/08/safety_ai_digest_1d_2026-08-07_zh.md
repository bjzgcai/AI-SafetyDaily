# AI 日报 [AI 安全] - 2026-08-07


# AI 安全每日综述：2026-08-07

## Highlights

今日研究的核心突破集中在 Agent 记忆的可审计性与系统编排的安全性上。**Activity Frames** 提出了一种确定性的屏幕活动编译方法，解决了 Agent 历史记录中语义模糊的问题，为运行时监控提供了机械可验证的基础，这直接回应了长期存在的 Agent 行为黑盒风险。与此同时，**HarnessOpt-Bench** 揭示了模型权重之外的编排代码（Harness）已成为新的攻击面，强调了对控制流、提示工程和外部工具的独立评估需求，标志着安全重心从单一模型向系统架构转移。此外，**DataSpace** 通过构建可验证的表格输出基准，为数据类 Agent 在异构工作空间中的真实性提供了量化标准，防止了企业级应用中的幻觉扩散与数据泄露风险。

## Agent 安全与治理

当前 Agent 系统的治理框架正面临从“模型中心”向“环境中心”的范式转移，这一趋势在关于记忆完整性与编排控制的最新研究中尤为明显。**Activity Frames** 针对计算机使用 Agent（Computer-Use Agents）面临的记忆缺失问题，提出了一套无需模型的确定性管道，将被动捕获的屏幕活动编译为结构化帧。该方法不仅实现了缓存和字节级可复现性，更重要的是它剥离了生成式模型对历史记录的干扰，使得 Agent 的行为轨迹可以被机械审计。这与传统的基于自然语言的历史记录形成鲜明对比，后者容易受到上下文窗口限制和模型遗忘的影响，从而在发生安全事故时难以追溯根源。相比之下，**HarnessOpt-Bench** 则进一步指出，即便拥有完美的记忆记录，如果围绕模型的 Harness（包括提示词、工具调用逻辑和控制流）存在漏洞，系统依然脆弱。该基准专门用于评估 LLM 在优化自身运行环境方面的能力，暗示了未来的攻击者可能利用 Agent 自我优化功能来绕过预设的安全护栏。这两项工作共同指向一个结论：Agent 的安全边界不再局限于模型内部参数，而是扩展到了其运行的外部环境和执行逻辑中。

在企业级应用场景中，数据的真实性与 Agent 的决策可解释性同样关键。**DataSpace** 基准引入了针对数据 Agent 的验证性分析任务，要求 Agent 在包含数据库、文档和多媒体文件的异构工作空间中产生可验证的表格结果。现有的基准往往孤立地测试查询或检索能力，而忽略了跨源证据发现与确定性输出的统一性。该研究通过 410 个跨语言任务和数千个工件，填补了这一空白，强调了在复杂数据环境中防止 Agent 产生幻觉的重要性。然而，这种验证机制的有效性依赖于底层数据的完整性，这引出了更宏观的系统性风险问题。**From Economic Agents to Agentic Economies** 探讨了经济世界模型（EWMs）作为生成引擎的潜力，其中异质 Agent 通过市场机制相互作用并演化出宏观动态。虽然该蓝图展示了 Agent 模拟经济系统的宏伟愿景，但也隐含了巨大的治理挑战：当多个自主 Agent 在模拟或真实市场中互动时，可能涌现出人类无法预测的集体行为或系统性崩溃。这种从微观 Agent 行为到宏观系统风险的传导机制，目前尚缺乏有效的监管接口，需要建立类似金融监管沙箱的机制来约束 Agentic Economies 的演进路径。

## 工具调用与运行时防御

在 Agent 的训练与推理阶段，如何确保工具调用的安全性以及强化学习过程中的信用分配，是运行时防御的关键环节。**EnvACE** 提出了一种名为“世界排练”（World Rehearsal）的方法，旨在替代训练过程中昂贵且高风险的真实环境交互。该方法允许策略在生成工具调用后，扮演环境角色来模拟响应，从而在隔离的沙盒中进行长周期任务的训练。这种内部化环境动态的策略显著降低了因探索未知环境而导致的安全事故概率，特别是在涉及敏感 API 或物理设备的场景中。然而，仅靠环境隔离不足以解决所有问题，**AgentOPSD** 进一步关注了长周期多轮任务中的信用分配难题。传统的强化学习奖励往往只能反馈最终结果，导致关键的中间决策被忽视。该研究提出的递归自蒸馏方法，通过聚合 token 级的师生对数概率差距，实现了无 Critic 的回合级信用分配。这种方法能够更精细地识别哪些具体的工具调用导致了成功或失败，从而为后续的防御性微调提供更准确的信号。

为了增强 Agent 在面对对抗性输入时的鲁棒性，**CalibForge** 引入了一种自主终端任务合成系统，利用经过验证的求解器行为来修订候选任务。该系统通过多求解器校准和对比求解器校准，生成了具有适当挑战性的可执行任务，这些任务不仅能验证可行性，还能揭示求解器在不同设置下的相对表现。这种对抗性的任务生成思路，实际上是在训练前就构建了压力测试环境，迫使 Agent 在面对边缘情况时展现出更强的稳定性。值得注意的是，这些运行时防御机制与**Continual Learning in Transition** 中提到的外部组件扩展形成了互补。后者指出，持续学习不应仅限于参数中心的机制，还应扩展到记忆库和技能库等外部 Harness 组件。这意味着，Agent 的运行时安全不仅依赖于实时的防御算法，还依赖于其长期技能记忆的更新机制是否具备防篡改和版本控制能力。如果技能库被恶意注入，即便有实时的沙盒保护，Agent 仍可能在特定触发条件下执行危险操作。因此，工具调用的防御必须与技能管理的生命周期安全相结合。

## 对齐、评估与基准

随着 Agent 能力的提升，评估其对齐程度和可靠性变得愈发复杂，尤其是当评估本身也依赖自动化系统时。**OSReward** 系统地研究了视觉 - 语言模型（VLM）作为计算机使用轨迹裁判的可靠性问题。由于人类标注无法在大规模上提供验证，行业倾向于使用 VLM 进行自动化评分，但该研究指出，这些裁判模型本身可能存在偏差或幻觉，导致评估结果失真。这一发现对当前的安全评估流程提出了严峻挑战：如果我们用不确定的模型来评估 Agent 的安全性，那么评估结果的可信度将大打折扣。为了应对这一挑战，**Teaching Nemotron Greek** 和 **Learning from Failures** 分别从不同维度提升了检索增强生成（RAG）的准确性与鲁棒性。前者针对现代希腊语等低资源语言，通过 corpus mining 和 synthetic supervision 增强了检索模型的落地能力，确保了多语言场景下信息获取的准确性；后者则通过硬负例（Hard Negatives）驱动的检索式思维链（CoT），丰富了查询表示，减少了语义相似候选者的混淆。这两项工作表明，提高 Agent 对齐度的一个重要途径是增强其对外部知识的检索质量，减少因信息缺失或误导导致的错误决策。

在空间智能与多模态理解方面，**GST-Bench** 和 **SmartMage** 提供了新的评估视角。**GST-Bench** 专注于视频理解中的全局空间意识，要求模型从连续的视频流中进行跨视角的空间推理，这对于具身 Agent 在复杂物理环境中的导航至关重要。如果 Agent 缺乏全局空间感知，其在执行物理任务时极易发生碰撞或迷失方向，构成物理安全风险。**SmartMage** 则提出了动态模态编排机制，根据查询需求自适应地组合视觉和几何线索，避免了固定模态组合带来的语义噪声。这种灵活性虽然提高了效率，但也增加了攻击面：攻击者可能通过精心设计的输入诱导模型切换到特定的模态通道，从而绕过某些安全检查。此外，**Weights or Skills?** 的综述进一步区分了将能力固化在权重中的策略与编写可执行技能的策略。对于安全研究者而言，代码即策略（Code-as-Policy）的方法虽然提供了更高的可解释性和自我修复能力，但也意味着 Agent 拥有了修改自身代码的能力，这引入了代码注入和权限提升的风险。因此，未来的对齐研究需要同时关注模型权重的稳健性和外部技能脚本的执行权限控制。

## Looking Forward

尽管上述工作在 Agent 安全的各个层面取得了进展，但仍存在若干未解决的理论问题与待验证假设。首先，**Activity Frames** 所确立的确定性记忆记录虽然解决了审计问题，但在面对加密通信或高度动态的 GUI 界面时，其覆盖范围是否足够全面仍需实证检验。其次，**HarnessOpt-Bench** 揭示了编排代码的风险，但目前尚无标准化的协议来定义 Harness 的安全基线，这使得不同系统间的互操作性与合规性难以保证。最后，**From Economic Agents to Agentic Economies** 提出的宏观模拟虽然极具前瞻性，但对于如何在模拟环境中检测并阻断有害的涌现行为（Emergent Behaviors），目前缺乏数学上的形式化证明。未来的研究需要重点关注如何将形式化验证技术引入到 Agent 的记忆管理与工具调用逻辑中，以建立比单纯依靠统计评估更为可靠的安全保障体系。

---


## 参考来源

- **From Economic Agents to Agentic Economies: A Systems Blueprint for Economic World Models** — [huggingface_papers](https://arxiv.org/abs/2608.06020)
- **Learning from Failures: Retrieval-Centric CoT via Hard Negatives for Unified Multimodal Retrieval** — [huggingface_papers](https://arxiv.org/abs/2608.06060)
- **DataSpace: Benchmarking Data Agents for Verifiable Analytics over Heterogeneous Workspaces** — [huggingface_papers](https://arxiv.org/abs/2608.03451)
- **EnvACE: Internalizing Environment Dynamics via World Rehearsal for Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2608.06197)
- **AgentOPSD: Recursive Self-Distillation for Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2608.05987)
- **Activity Frames: Deterministic Screen-Activity Compilation for Agent Memory and Replay** — [huggingface_papers](https://arxiv.org/abs/2608.05784)
- **Teaching Nemotron Greek: Mining a Corpus, Adapting Retrieval, and Grounding Generation for Modern Greek across Specialist Domains** — [huggingface_papers](https://arxiv.org/abs/2608.05138)
- **WorldClaw: Agentic 3D Open-World Generation at Scale** — [huggingface_papers](https://arxiv.org/abs/2608.05248)
- **FactorJEPA: Factorizing Monolithic Futures into Layout-Agent-Interaction Channels for Crowded and Chaotic Global South Urban Worlds** — [huggingface_papers](https://arxiv.org/abs/2608.01049)
- **HarnessOpt-Bench: Evaluating LLMs at Harness Optimization** — [huggingface_papers](https://arxiv.org/abs/2608.06301)
- **Interpretable MEG Decoding of Perceived Speech: Cortical Sources and the Stimulus Features That Drive Retrieval** — [huggingface_papers](https://arxiv.org/abs/2608.01481)
- **OSReward: Instituting Standardized Evaluation for Cross-Platform Computer-Use Reward Models** — [huggingface_papers](https://arxiv.org/abs/2607.28609)
- **Weights or Skills? A Survey of Robot-Learning Techniques: from Action-Predicting Weights to Robots that Write their Own Skills** — [huggingface_papers](https://arxiv.org/abs/2608.01851)
- **CalibForge: Adversarial Solver Calibration for Scaling Learnable Terminal Tasks** — [huggingface_papers](https://arxiv.org/abs/2608.06352)
- **MASS: Multiplayer World Models with Authoritative Shared State** — [huggingface_papers](https://arxiv.org/abs/2608.06257)
- **GST-Bench: Can VLMs Develop Global Spatial Awareness from Video?** — [huggingface_papers](https://arxiv.org/abs/2608.05747)
- **GaussianSelector: Lightweight Human-Guided Object Selection in 3D Gaussian Splatting with Graph Optimization** — [huggingface_papers](https://arxiv.org/abs/2608.01492)
- **Continual Learning in Transition** — [huggingface_papers](https://arxiv.org/abs/2608.06216)
- **SmartMage: Dynamic Modality Orchestration for 3D Scene Understanding** — [huggingface_papers](https://arxiv.org/abs/2608.05137)
- **Task-Conditional Flow Matching for Balanced Multilingual Text Embedding Adaptation** — [huggingface_papers](https://arxiv.org/abs/2608.05785)