# AI 日报 [AI 安全] - 2026-07-24


# AI 安全每日综述：2026-07-24

## Highlights

当日研究进展在智能体（Agent）的安全架构与治理机制上取得了显著突破。**NVIDIA-labs** 提出的 **OO Agents** 框架将 Python 类型注解转化为运行时契约，为智能体的工具调用提供了结构化的安全边界；**AREX** 工作深入探讨了递归自我改进（RSI）智能体中的发现 - 验证不对称性问题，揭示了深层研究中潜在的控制风险；同时，**Tencent WorkBuddy Bench** 构建了抗数据污染的编码智能体评估基准，强调了在真实业务场景下防止训练集泄露的重要性。这些进展共同指向了从静态代码约束到动态意图追踪的智能体全生命周期安全治理新范式。

## Agent 安全与治理

当前智能体安全的核心挑战已从单纯的提示词防护转向系统级的运行时治理与架构约束。传统开发模式往往将提示模板、工具 Schema 和回调代码割裂管理，这种碎片化极易导致状态不一致或权限越界。针对这一痛点，**NVIDIA-labs OO Agents** 提出了一种原生面向对象的智能体构建方法，其核心创新在于将智能体视为 Python 对象，其中方法对应动作，字段对应状态，而文档字符串则充当提示词。更为关键的是，该方法利用类型注解作为“契约”，使得确定性代码与由大语言模型驱动的运行时逻辑之间建立了明确的边界。作者声称这种设计不仅简化了开发流程，更重要的是通过静态类型检查在编译期拦截了部分非法的工具调用请求，从而在架构层面降低了提示注入的风险。然而，这种依赖特定编程语言特性的方案是否具备跨平台通用性，仍需进一步观察其在异构环境下的表现。

在智能体的自我演进能力方面，**AREX** 工作聚焦于深度研究任务中的递归自我改进（RSI）机制。该研究指出，发现满足多重约束的答案成本高昂，而验证候选答案通常可以分解为可处理的约束检查，这种发现与验证的非对称性意味着简单的搜索延长并不能保证安全性。AREX 引入了一种交替进行验证与优化的循环，旨在利用部分验证状态引导后续细化。尽管作者展示了该方法在特定约束下的有效性，但关于递归过程中错误累积的长期影响尚未完全量化。如果验证模块本身存在漏洞，自我改进循环可能加速有害行为的生成，这构成了 RSI 智能体治理中的重大隐患。相比之下，**OpenForgeRL** 则从训练基础设施的角度切入，解决了复杂推理智能体难以端到端训练的问题。该框架通过轻量级代理记录环境交互，允许在开放基础设施中训练基于 Harness 的智能体。这种方法虽然提升了训练效率，但也引入了新的攻击面：代理层若被篡改，可能导致训练数据被污染或策略被劫持。因此，如何在保持训练灵活性的同时确保 Harness 调用的审计完整性，是未来需要重点关注的治理方向。

此外，智能体在长程交互中的意图漂移问题日益凸显。**LLMs Get Lost in Evolving User Intent** 的研究表明，现有评估多基于单轮且意图明确的设定，忽略了用户意图在对话过程中动态演变的现实。该工作提出了一个追踪框架来衡量智能体在意图变化时的响应能力。从安全角度看，意图漂移不仅是性能问题，更是安全风险：攻击者可以通过逐步诱导用户修改意图，使智能体执行原本拒绝的操作。结合 **NVIDIA-labs OO Agents** 的结构化契约，未来的治理框架可能需要将“意图一致性”纳入类型系统的校验范围，确保智能体在状态更新时不会偏离预设的安全策略。与此同时，**Streaming Multi-Agent Autoregressive Diffusion Model** 提出的世界状态寄存器（World State Registers）为多智能体协作中的状态一致性提供了新思路。通过可学习的令牌存储共享信息并跟踪个体状态，该模型试图解决多视角下的状态维护难题。在多智能体系统中，这种共享状态的持久化若缺乏访问控制，可能导致敏感上下文泄露给未授权智能体，因此在设计此类寄存器时必须内置细粒度的权限隔离机制。

## 工具/提示注入与运行时防御

随着智能体对工具调用的依赖加深，如何防御复杂的提示注入和运行时攻击成为关键。除了上述提到的结构化契约外，模型微调过程中的稳定性也是运行时安全的重要防线。**Multi-Turn On-Policy Distillation with Prefix Replay** 提出了一种离环境的替代方案，利用预收集的教师轨迹作为重放前缀，让学生在选定步骤行动，而教师提供密集的步骤监督。这种方法减少了在线交互的成本，但也引发了关于数据分布偏移的担忧：如果重放的前缀包含未被充分清洗的恶意样本，学生模型可能会继承这些行为模式。与之相关的 **Sample-Efficient Learning from Agent Experience** 探讨了如何利用上下文蒸馏将交互历史内化为模型权重，以解决经验移除后增益消失的问题。然而，将外部交互历史压缩进权重的过程若缺乏过滤，可能导致记忆污染，使得智能体在推理时意外触发训练数据中的敏感模式。

在强化学习（RL）领域，**Predictive Divergence Masks for LLM RL** 研究了用于稳定离策略更新的信任区域掩码。传统的 PPO 风格方法使用采样标记的重要性比率来制定邻近准则和方向准则，而近期工作 DPPO 改进了邻近准则，但在方向准则上仍存在局限。预测发散掩码旨在更精确地控制策略更新的方向，防止模型在优化过程中偏离安全基线。这对于防止智能体在探索阶段产生不可控行为至关重要。另一方面，**Visual Contrastive Self-Distillation** 提出了一种无需特权信息的自蒸馏方法，通过将图像内容移除转化为对比信号来驱动学习。这种方法虽然简化了训练流程，但在安全语境下，移除视觉内容可能导致智能体忽略关键的物理环境线索，从而在决策时产生幻觉。因此，在运行时防御中，必须平衡信息压缩带来的效率提升与环境感知的完整性，确保智能体在面对对抗性输入时仍能保持稳健的感知能力。

## 对抗攻击与鲁棒性

智能体在物理世界和复杂视觉环境中的鲁棒性直接关系到其部署的安全性。**ReferTrack** 提出了一种“先指后跟”的具身视觉跟踪范式，旨在解决现有视觉 - 语言 - 动作策略中思维链推理过于抽象、难以监督的问题。该模型首先选择目标，然后进行跟踪， grounding 于单目摄像头。这种显式的空间定位对于防止智能体在移动过程中发生碰撞或误操作具有重要意义。然而，如果目标识别受到对抗性干扰，跟踪链条的断裂可能导致灾难性后果。**Robostral Navigate** 则致力于降低导航系统的传感器假设，仅消耗单目 RGB 图像流即可预测航点。这种设计提高了硬件兼容性，但也增加了对光照变化和遮挡的敏感度。在安全评估中，必须测试该模型在极端视觉条件下的失效模式，以防止因传感器欺骗导致的导航失控。

多智能体系统中的状态一致性同样面临对抗风险。**Streaming Multi-Agent Autoregressive Diffusion Model** 强调维持跨智能体和跨视图的世界状态，但在实际应用中，恶意智能体可能通过伪造状态寄存器信息来误导其他智能体。**TableVerse** 提供了一个大规模桌面数据集，采用 Real2Sim 管道从非结构化场景中重建布局，而非依赖文本生成的幻觉布局。这种高保真数据对于训练具有物理常识的操纵策略至关重要，能够减少智能体在虚拟环境中习得的无效技能迁移到现实世界时产生的安全隐患。此外，**Color Pass-Through via Camera-Display Coupling** 研究了相机与显示器的耦合校准问题，指出分离校准会导致信息瓶颈和误差累积。对于依赖视觉反馈的智能体而言，色彩和亮度的失真可能影响其对物体属性的判断，进而引发操作失误。因此，在构建智能体感知栈时，需考虑端到端的校准机制，以减少因硬件特性差异导致的感知偏差。

## 模型对齐与可解释性

数据质量与知识结构的对齐是确保智能体行为符合人类价值观的基础。**Dataset Distillation by Influence Matching** 从结果中心视角重新审视数据集蒸馏，通过匹配最终训练结果而非过程代理来学习紧凑的合成集。这种方法虽然提高了数据效率，但如果合成集未能准确反映原始数据的分布特征，可能会导致模型在特定子任务上的对齐偏差。特别是在教育领域，**K12-KGraph** 构建了一个课程对齐的知识图谱，涵盖先修链、概念分类和教学序列。该图谱提取自官方教材，旨在评估和训练教育类大模型的课程认知能力。通过显式建模知识依赖关系，该工作有助于检测模型是否在推理过程中违反了学科逻辑，从而防止传播错误的科学概念。

在评估方面，**FinanceComplexQA** 设计了针对工业级金融文档的智能体推理基准，利用专家知识合成复杂布局的财务文档。该基准生成的问答对数量庞大，旨在评估智能体在处理高风险领域的准确性。由于金融分析涉及严格的合规要求，任何推理错误都可能造成实质性损失，因此该基准的验证环节尤为关键。**Tencent WorkBuddy Bench** 则专注于多领域编码智能体，其核心在于反工程真实提交和拉取请求来构建任务，以确保提示词无法通过公开数据恢复。这种防污染的任务构造方法有效避免了评估结果虚高，为衡量智能体在真实开发环境中的安全性提供了可靠标尺。同时，**Show, Don't Tell** 提出在生成像素而非文本中评估空间认知，认为连续视觉场景更适合表达位置、区域和路径。这种评估范式的转变有助于发现模型在空间理解上的细微缺陷，防止智能体在物理交互中因空间认知错误而发生危险。最后，**SANA-Video 2.0** 介绍了混合线性注意力的高效视频生成架构，虽然主要关注生成效率，但其长序列扩展能力也影响了智能体在视频理解任务中的上下文窗口限制，间接关系到智能体处理长程依赖时的注意力分散风险。

## Looking Forward

尽管当日研究在智能体架构、训练稳定性和评估基准上取得了重要进展，但仍存在若干未解决的理论问题。首先是递归自我改进（RSI）的验证闭环问题，目前 **AREX** 等工作虽提出了验证机制，但尚未形成通用的形式化验证标准，难以保证在无限迭代中不出现目标漂移。其次是意图追踪的标准化，**LLMs Get Lost in Evolving User Intent** 指出了动态意图的挑战，但业界尚未建立统一的指标来量化智能体在意图演变过程中的安全边界。最后是具身智能的物理安全，**Robostral Navigate** 和 **ReferTrack** 等工作在感知鲁棒性上有所突破，但缺乏针对传感器欺骗和物理环境对抗的标准化测试协议。未来的研究需重点关注如何将静态的类型契约扩展为动态的行为约束，以及如何建立跨模态的、可审计的智能体运行时监控体系，以应对日益复杂的智能体安全威胁。

---


## 参考来源

- **NVIDIA-labs OO Agents: Native Python Object-Oriented Agents** — [huggingface_papers](https://arxiv.org/abs/2607.20709)
- **OpenForgeRL: Train Harness-native Agents in Any Environment** — [huggingface_papers](https://arxiv.org/abs/2607.21557)
- **FinanceComplexQA: Benchmarking Agentic Reasoning on Industrial-grade Financial Documents** — [huggingface_papers](https://arxiv.org/abs/2607.19238)
- **Streaming Multi-Agent Autoregressive Diffusion Model with World State Registers** — [huggingface_papers](https://arxiv.org/abs/2607.21594)
- **AREX: Towards a Recursively Self-Improving Agent for Deep Research** — [huggingface_papers](https://arxiv.org/abs/2607.21461)
- **Tencent WorkBuddy Bench: A Multi-Domain Coding-Agent Benchmark with Contamination-Resistant Task Construction** — [huggingface_papers](https://arxiv.org/abs/2607.20911)
- **Show, Don't Tell: Evaluating Spatial Cognition in Generative Pixels Rather Than LLM Text** — [huggingface_papers](https://arxiv.org/abs/2607.21072)
- **Sample-Efficient Learning from Agent Experience** — [huggingface_papers](https://arxiv.org/abs/2607.21051)
- **Multi-Turn On-Policy Distillation with Prefix Replay** — [huggingface_papers](https://arxiv.org/abs/2607.04763)
- **LLMs Get Lost in Evolving User Intent** — [huggingface_papers](https://arxiv.org/abs/2607.20734)
- **Dataset Distillation by Influence Matching** — [huggingface_papers](https://arxiv.org/abs/2607.16859)
- **ReferTrack: Referring Then Tracking for Embodied Visual Tracking** — [huggingface_papers](https://arxiv.org/abs/2607.20061)
- **Self-Supervised Learning of Structured Dynamics from Videos** — [huggingface_papers](https://arxiv.org/abs/2607.21576)
- **Robostral Navigate** — [huggingface_papers](https://arxiv.org/abs/2607.20785)
- **TableVerse: A Large-scale Tabletop Dataset with Real-world Grounded Layouts for Generalizable Manipulation** — [huggingface_papers](https://arxiv.org/abs/2607.21017)
- **Color Pass-Through via Camera-Display Coupling** — [huggingface_papers](https://arxiv.org/abs/2607.12746)
- **Predictive Divergence Masks for LLM RL** — [huggingface_papers](https://arxiv.org/abs/2607.10848)
- **Visual Contrastive Self-Distillation** — [huggingface_papers](https://arxiv.org/abs/2607.21556)
- **K12-KGraph: A Curriculum-Aligned Knowledge Graph for Benchmarking and Training Educational LLMs** — [huggingface_papers](https://arxiv.org/abs/2605.09635)
- **SANA-Video 2.0: Hybrid Linear Attention with Attention Residuals for Efficient Video Generation** — [huggingface_papers](https://arxiv.org/abs/2607.21553)