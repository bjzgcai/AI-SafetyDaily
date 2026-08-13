# AI 日报 [AI 安全] - 2026-07-28


## 亮点

当日研究进展中，最值得关注的是针对长周期多模态 Agent 的运行时安全框架与治理范式的初步构建。**JarvisHub: An Open Harness for Canvas-Native Multimodal Creative Agents** 提出了一种超越传统对话交互的画布原生工作流，为创意类 Agent 的版本控制与工具调用审计提供了结构化环境，直接回应了复杂任务中的状态管理风险。**StateAct: Program State, before Pixels, for Long-Horizon Computer-Use Agents** 则从底层架构角度指出，依赖截图的感知方式存在信息丢失，主张直接访问程序状态以提升效率，但这同时也引入了更深层的系统级权限暴露风险。此外，**A Vocabulary for Multi-Agent Automated Research Systems** 试图建立一套标准化的多智能体系统描述语言，明确了操作权限、通信机制与信息可见性边界，为跨系统的 Agent 治理与合规性审查奠定了理论基础。这三项工作共同指向了一个核心趋势：Agent 安全正从单纯的提示词防护转向对执行环境、状态访问及系统协议的全面管控。

## Agent 安全与治理

随着大模型从单步生成向长周期规划演进，Agent 的安全边界正在发生根本性转移。传统的基于聊天的交互模式难以支撑复杂的现实任务，而新的架构设计往往伴随着更高的攻击面。**JarvisHub: An Open Harness for Canvas-Native Multimodal Creative Agents** 通过引入画布原生的多模态创作代理，将任务分解为引用、草稿、修改及版本关系等动态过程。这种设计虽然提升了创作效率，但也意味着攻击者可能利用中间状态进行持久化注入或篡改项目上下文。相比之下，**StateAct: Program State, before Pixels, for Long-Horizon Computer-Use Agents** 进一步激进地主张绕过像素层，直接通过代码访问程序状态（如文件、后端数据）。作者认为这能解决截图渲染的信息丢失问题，但在安全视角下，这意味着 Agent 获得了类似人类管理员的直接系统权限，一旦遭遇提示注入或逻辑漏洞，后果将从内容生成错误升级为数据泄露或系统破坏。这两项工作在接口设计上形成了鲜明对比：前者侧重于应用层的流程规范，后者则触及操作系统层面的状态访问，后者显然需要更严格的沙盒隔离与权限最小化策略。

为了应对日益复杂的 Agent 协作网络，**A Vocabulary for Multi-Agent Automated Research Systems** 提出了一套形式化的词汇表，用于定义系统中的主体身份、可用操作、调用权限及通信协议。这一工作填补了当前多智能体系统在治理层面的理论空白，使得审计人员能够明确“谁可以做什么”以及“信息在运行间如何流动”。然而，现有的治理框架往往缺乏对动态行为的约束，**TRACE: Business Rule-Grounded Reasoning Curriculum for Knowledge-Preserving Parametric Tool Retrieval in Enterprise LLMs** 则尝试在企业级场景中解决工具检索的安全问题。该研究指出，参数化检索方法虽然高效，但容易在训练过程中破坏工具的语义知识，导致模型无法正确理解业务规则。TRACE 通过两阶段课程学习，将企业规则嵌入到推理链中，试图在保持参数化优势的同时增强工具调用的合规性。这与 **From Proprietary to Open-Source: Bridging the Distribution Gap via Multi-Agent Protocol Distillation in Agentic Search** 形成互补：后者关注如何通过蒸馏缩小专有模型与开源模型在搜索协议上的分布差异，而前者则强调在特定领域内通过规则约束来防止工具滥用。两者结合表明，未来的 Agent 治理不仅需要通用的协议标准，还需要针对特定领域的规则引擎来确保工具调用的安全性。

## 工具调用、提示注入与运行时防御

在运行时防御层面，如何确保 Agent 在长周期任务中的行为一致性是当前的难点。**The Physics of Multi-Turn Long-Horizon Planning: From Pre-training to Post-training via Single- and Multi-Teacher On-Policy Agentic Distillation** 深入探讨了多轮长周期规划的物理机制，指出现有模型依赖不可控的互联网数据进行训练，导致规划能力的获取过程不透明。该研究建议通过受控的多轮环境进行系统性研究，以识别规划能力是如何被塑造和整合的。这一观点暗示，如果训练数据中包含恶意构造的规划轨迹，模型可能会习得有害的行为模式。因此，**Reasoning Denoiser: Denoising Reasoning Traces for Hallucination Detection in Large Reasoning Models** 提出了针对推理轨迹的去噪方法，旨在检测并过滤幻觉步骤。作者发现，长轨迹中的无关步骤和重复步骤会严重干扰真实性评估，现有的基于置信度的评分方法无法可靠分离噪声。这项工作为运行时监控提供了新的技术路径，即通过清洗推理痕迹来提高对潜在越狱或错误决策的检测率。

在模型固化与验证方面，**A Frozen 12B Beats Frontier Models on Verified Work: 100% Accuracy, 0 Tokens, Bit-Exact, Forever** 提供了一种截然不同的安全思路。该研究不再追求模型的持续更新，而是采用冻结模型配合经过独立验证的解决方案记忆库。一旦某个问题家族被解决并通过验证，新实例即可实现零生成 token 的确定性回答。这种方法虽然在灵活性上有所牺牲，但极大地降低了因模型漂移导致的不可预测风险，特别适用于高可靠性要求的场景。与之相对，**Leveraging External Knowledge for Historical Document Restoration via Retrieval-Augmented Large Language Models** 展示了 RAG 技术在特定领域的应用，通过结合预训练模型的隐式知识与检索的外部显式上下文来恢复历史文档。虽然该工作主要关注文档修复，但其揭示的 RAG 架构同样面临外部知识库被投毒的风险，这要求我们在设计 Agent 的记忆与检索模块时，必须考虑来源的可信度验证。

## 模型对齐、评估与鲁棒性

随着模型规模的扩大，对齐与评估的挑战也愈发严峻。**Kimi K3: Open Frontier Intelligence** 介绍了拥有百万级上下文窗口和混合专家架构的新模型，其训练效率的提升意味着更快的迭代速度。然而，作者声称的约 2.5 倍扩展效率提升背后，隐藏着强化学习后训练带来的潜在风险，特别是当奖励函数未能完全覆盖所有安全维度时，快速迭代可能放大对齐缺陷。为了缓解这一问题，**TILT: Improposing Compositional Generation in Diffusion Models with a Model-Intrinsic Reward** 提出了一种无需训练的测试时对齐框架，通过内在奖励修正采样轨迹以符合复杂组合提示。这种方法不依赖外部标注，而是利用模型自身的分布特性来纠正概念重叠失败，为生成内容的可控性提供了一种轻量级的对齐手段。

在评估基准方面，现有的通用指标已不足以衡量专业领域的能力。**FilmBench: A Film-Grade Benchmark for Cinematic Video Generation** 指出，大多数视频生成基准仅评估视觉质量或粗略文本对齐，缺乏电影语言的专业标准。该基准引入了电影制作中的专业评判体系，旨在评估生成的视频是否具备真正的工艺水准而非仅仅是合理性。同样，**ClinFusion: A Vision-Centric Multimodal LLM System for Holistic Medical Understanding** 强调了医疗领域部署 MLLM 的根本挑战在于视觉中心性，即模型必须吸收异构的医学图像知识并提供符合放射科医生实践的精确定量评估。这两个基准工作共同表明，安全评估不能仅停留在通用指标上，必须深入到具体行业的专业标准中，否则无法有效识别特定场景下的安全隐患。此外，**Data Pyramid for Embodied Manipulation** 虽然主要讨论具身数据生态，但其提出的金字塔结构强调了真实机器人数据与仿真数据之间的张力，这对于具身 Agent 的安全性至关重要，因为仿真环境中的安全假设往往无法直接迁移到物理世界。

## Looking Forward

尽管上述工作在 Agent 安全与治理方面取得了显著进展，但仍存在若干未解决的理论问题。首先，关于 **StateAct** 所倡导的直接程序状态访问，目前尚缺乏成熟的运行时沙盒机制来隔离潜在的恶意代码执行，如何在提升效率的同时保证系统完整性是一个亟待攻克的难题。其次，**A Vocabulary for Multi-Agent Automated Research Systems** 提出的治理框架虽然定义了静态权限，但对于动态环境中 Agent 之间自发形成的临时联盟及其潜在的利益冲突，尚未有明确的量化评估方法。最后，**Reasoning Denoiser** 与 **A Frozen 12B** 分别代表了动态去噪与静态验证两条路径，未来可能需要探索两者的融合机制，即在保持模型灵活性的同时，引入可验证的确定性记忆模块，以平衡创新与安全。此外，随着 **Kimi K3** 等超大规模模型的普及，如何防止在分布式训练或蒸馏过程中泄露敏感的训练数据与推理逻辑，也是行业需要持续关注的前沿方向。

---


## 参考来源

- **JarvisHub: An Open Harness for Canvas-Native Multimodal Creative Agents** — [huggingface_papers](https://arxiv.org/abs/2607.23588)
- **The Physics of Multi-Turn Long-Horizon Planning: From Pre-training to Post-training via Single- and Multi-Teacher On-Policy Agentic Distillation** — [huggingface_papers](https://arxiv.org/abs/2607.24720)
- **StateAct: Program State, before Pixels, for Long-Horizon Computer-Use Agents** — [huggingface_papers](https://arxiv.org/abs/2607.22798)
- **A Vocabulary for Multi-Agent Automated Research Systems** — [huggingface_papers](https://arxiv.org/abs/2607.22682)
- **From Proprietary to Open-Source: Bridging the Distribution Gap via Multi-Agent Protocol Distillation in Agentic Search** — [huggingface_papers](https://arxiv.org/abs/2607.24280)
- **Kimi K3: Open Frontier Intelligence** — [huggingface_papers](https://arxiv.org/abs/2607.24653)
- **ClinFusion: A Vision-Centric Multimodal LLM System for Holistic Medical Understanding** — [huggingface_papers](https://arxiv.org/abs/2607.24743)
- **A Frozen 12B Beats Frontier Models on Verified Work: 100% Accuracy, 0 Tokens, Bit-Exact, Forever** — [huggingface_papers](https://arxiv.org/abs/2607.23806)
- **Leveraging External Knowledge for Historical Document Restoration via Retrieval-Augmented Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2607.21936)
- **Data Pyramid for Embodied Manipulation** — [huggingface_papers](https://arxiv.org/abs/2607.24744)
- **TRACE: Business Rule-Grounded Reasoning Curriculum for Knowledge-Preserving Parametric Tool Retrieval in Enterprise LLMs** — [huggingface_papers](https://arxiv.org/abs/2607.22639)
- **FilmBench: A Film-Grade Benchmark for Cinematic Video Generation** — [huggingface_papers](https://arxiv.org/abs/2607.24241)
- **Characterizing Warp Divergence from Pascal to Blackwell** — [huggingface_papers](https://arxiv.org/abs/2607.23402)
- **Reasoning Denoiser: Denoising Reasoning Traces for Hallucination Detection in Large Reasoning Models** — [huggingface_papers](https://arxiv.org/abs/2607.22098)
- **OmniVAE: An Audio-Video VAE with Cross-Modal Alignment for Joint Generation** — [huggingface_papers](https://arxiv.org/abs/2607.23855)
- **Rethinking Classifier-Free Guidance in On-Policy Diffusion Distillation** — [huggingface_papers](https://arxiv.org/abs/2607.24731)
- **TILT: Improving Compositional Generation in Diffusion Models with a Model-Intrinsic Reward** — [huggingface_papers](https://arxiv.org/abs/2607.21606)
- **DriveDNA: A Large-Scale Multimodal Naturalistic Driving Dataset and Benchmark for Driving Style Identification** — [huggingface_papers](https://arxiv.org/abs/2607.23822)
- **UltraViT: Latency-Optimized On-device Vision Encoder for Large Vision-Language Models** — [huggingface_papers](https://arxiv.org/abs/2607.23373)
- **Sol-Attn: Accelerating Video Generation Inference via On-the-Fly Attention Sparsification** — [huggingface_papers](https://arxiv.org/abs/2607.24027)