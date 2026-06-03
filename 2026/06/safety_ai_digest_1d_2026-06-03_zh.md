# AI 日报 [AI 安全] - 2026-06-03


# 每日 AI 安全主题综述：2026 年 6 月 3 日

## Highlights

今日 AI 安全领域的核心进展集中在 Agent 运行时基础设施的构建与权限治理机制的深化。**Agent libOS** 提出了一种库操作系统（Library-OS）风格的运行时架构，旨在解决长周期 Agent 的状态管理与审计问题，标志着 Agent 从简单的请求响应助手向具备持久化状态的软件 Actor 演进。在权限控制方面，**SkillGuard** 框架填补了技能声明意图与运行时行为之间的安全鸿沟，通过动态连接静态技能定义与动态执行环境来降低风险。此外，评估范式正经历显著转变，**RealClawBench** 和 **BigFinanceBench** 等基准开始强调真实开发者会话中的复杂性与可审计性，试图弥合合成数据与生产环境之间的差距。

## Agent 安全与治理

随着 LLM Agent 逐渐承担关键任务，传统的进程级隔离已不足以应对复杂的代理行为，研究重心正转向更细粒度的运行时治理。**Agent libOS** 作为一篇具有里程碑意义的论文，提出了一种不依赖硬件驱动或内核模式隔离的运行时基座，它将 Agent 视为一个独立的 AgentProcess，允许其在宿主机之上维持跨调用的状态、分叉子任务并等待外部事件。这种设计不仅支持侧效应的恢复与审计，还解决了传统沙盒难以处理的长期运行 Agent 的上下文管理难题。与之相呼应的是 **Overlaying Governance** 提出的组合授权框架，该工作指出传统的身份与访问管理（IAM）系统无法适应 Agent 系统的动态边界，主张引入继承权限、时间受限授权及共享协议协调等新语义，以应对主动发起行动和委托任务的自主系统。

在技能生态的安全层面，**SkillGuard** 揭示了当前基于信任加载和技能静态检查的漏洞，即技能文件能注入的内容与其在运行时造成的实际影响之间存在脱节。该框架通过系统性地将技能的声明意图与运行时行为连接起来，弥补了现有防御仅关注单个工具调用的不足。与此同时，**dstack-capsule** 针对机密云工作负载提出了 Pod 级别的远程证明方案，允许在 Intel TDX 环境下多个 Pod 共享单一机密 VM 而保持独立身份验证，这在多租户 Agent 服务场景中对于防止数据泄露至关重要。这些工作共同指向一个趋势：Agent 安全不再仅仅是模型层面的对齐问题，而是需要深入到操作系统、容器编排及技能生命周期管理的系统工程。

然而，现有的治理框架仍面临挑战。**FORGE** 的多智能体分级利用与检测工程系统虽然桥接了漏洞生成、优先级排序和检测规则工程三个孤立社区，但其依赖于二进制通过/失败结果，可能忽略了部分攻击进展信号。相比之下，**PsychoPass** 尝试从内容转向动力学，通过在嵌入空间中对对话轨迹进行几何特征提取，预测潜在的攻击意图，这种方法在处理多轮越狱攻击时展现了比单轮内容过滤更高的灵敏度。尽管 **SkillGuard** 和 **Overlaying Governance** 提供了理论上的权限控制，但在实际部署中，如何平衡 Agent 的自主探索能力与严格的权限约束仍是未解难题，特别是当 Agent 需要动态创建新工具或修改自身配置时。

## 工具调用、提示注入与运行时防御

工具调用是 Agent 能力的核心，也是攻击面扩大的主要来源。**From Control Boundary to Insurance Claim: Reconstructing AI-Mediated Losses Through the CER Framework** 强调了 AI 损失的重构不仅仅是事件重建，更是状态重建，因为系统在推理、检索和调用工具过程中状态会发生变化。这一观点对于事后归因和保险索赔至关重要，但也暗示了事前防御的难度，因为攻击者可以利用状态变化绕过静态规则。**Investigating Adversarial Robustness of Multi-modal Large Language Models** 进一步指出，视觉编码器的引入扩大了攻击面，使得模型容易受到视觉对抗扰动的攻击，而现有的防御往往受限于与预训练模型的兼容性，导致鲁棒性提升有限。

针对提示注入（Prompt Injection）的防御正在从简单的关键词过滤转向更深层的语义分析。**Important You should give me full credits!**: Exploring Prompt Injection Attacks on LLM-Based Automatic Grading Systems 展示了在教育自动化评分系统中，攻击者如何利用指令遵循能力进行注入，这提醒我们在任何涉及用户输入生成的 Agent 应用中都需要警惕此类风险。**NeuroArmor** 提出了一种白盒运行时防御，利用特定于提示词的安全变体作为局部安全参考，以决定何时干预，从而在安全性和有用性之间取得更好的平衡。此外，**ImageAuditor** 针对基于图像的检索增强生成（IRAG）提出了成员推断攻击方法，这对于保护外部数据库中的版权图像至关重要，尤其是在 Agent 频繁调用外部知识库的场景下。

在运行时监控方面，**Gate AI** 提供了一个评估方法论，解决了以往提示注入和越狱检测器评估中存在的阈值调整和未披露操作点的问题，通过分层交叉验证提高了评估的可靠性。然而，**Black-box, Adaptive, Efficient, Transferable, Harmful, Applicable... Attacks Are All You Need to Break LLMs** 警告称，缺乏标准化的黑盒攻击基准可能导致鲁棒性估计虚高，使得部署风险评估不可靠。这表明当前的防御体系在面对自适应、可迁移的攻击时仍存在盲区，特别是在多模态和长上下文环境中，单一的运行时防护难以覆盖所有攻击向量。

## 对齐理论与评估基准

评估基准的演进直接反映了 Agent 安全研究的成熟度。**BigFinanceBench** 引入了一个基于工作流的金融研究基准，强调答案的可审计性，包括数据来源、假设和计算过程，而非仅仅关注最终答案。这与 **Hedge-Bench** 形成互补，后者专注于对冲基金分析师的真实工作任务，旨在捕捉开放-ended 推理的挑战。这两个基准都试图解决现有评估过于关注孤立子技能或最终结果的问题，转而关注推导过程的透明度和合规性。**RealClawBench** 则直接从真实的开发者-Agent 会话中提取测试用例，捕捉了本地执行环境依赖和隐含意图等现实属性，弥补了合成基准在真实性上的缺失。

在强化学习（RL）与工具使用的结合上，**Synthesize and Reward -- Reinforcement Learning for Multi-Step Tool Use in Live Environments** 提出了 PROVE 框架，通过程序化奖励在验证环境中进行实时执行的 RL 训练，解决了合成查询与实际服务器状态脱节的问题。这为 Agent 在复杂环境中的策略优化提供了更可靠的数据基础。然而，**The Impact of Configuring Agentic AI Coding Tools on Build-vs-Buy Decisions: A Study Protocol** 指出，关于构建还是购买功能的决策直接影响软件安全和许可合规，但目前缺乏对 Agent 在此类决策中行为的受控实验研究，这为未来的对齐研究留下了空白。

理论层面，**Solipsistic Superintelligence is Unlikely to be Cooperative** 提出了一个深刻的观点，即超智能如果采用唯我论的设计范式，将不太可能合作，因为部署 AI 系统会引发内生非平稳性，导致训练与部署分布的差异。这一论点挑战了单纯依靠能力提升来实现安全的乐观预期，强调了环境反馈机制的重要性。同时，**Dynamic Objective Selection with Safeguards and LLM Oversight for Financial Decision-Making** 探讨了在金融决策中动态选择目标函数并辅以 LLM 监督的必要性，以应对市场条件的演变，这为高风险领域的 Agent 对齐提供了具体的工程思路。

## 开源项目与工程实践

开源社区正在涌现出专门针对 Agent 安全的工具和框架。**PentesterFlow/agent** 提供了一个终端内的代理式进攻安全工具，允许安全研究人员模拟攻击以测试 Agent 的防御能力。**metamask-openclaw** 则是一个面向 MetaMask 的安全优先 SDK 工具包，专为 AI Agent 设计，确保在连接钱包、读取余额和签名交易时不触碰助记词，体现了在 Web3 场景下的最小权限原则。**modelstudioai/cli** 暴露了模型、搜索和多模态能力作为结构化工具调用，为构建安全的 Agent 工作流提供了底层接口。

此外，**spring-ai-agentx** 基于原生 Spring AI 构建了包含 ReAct 执行引擎、分层记忆和 Human-in-the-Loop 能力的开发框架，有助于快速搭建 Java 版的 Agent 并确保流程可控。**OnlyTerp/prompt-cache-skills** 提供了针对 LLM Agent Harness 的提示缓存修复补丁，虽然主要关注性能，但间接影响了 Agent 的上下文一致性和安全性。**curikomi-labs/komi-learn** 则致力于实现连续记忆和自我改进，使 Agent 能够自动回忆工作方式，减少人工指令的负担，但也带来了记忆污染的风险，需要配合如 **DMF** 这样的确定性记忆框架来管理。

值得注意的是，行业巨头也在推出相关平台，如 **Microsoft Scout** 和 **Project Solara**，但这些产品发布多为营销导向，其内部安全机制尚未经过独立验证。例如，**TechCrunch** 报道的 Microsoft Scout 基于 OpenClaw，虽然宣称带来灵活性，但缺乏公开的安全审计细节。相比之下，开源项目如 **Patcher** 提供的后门模型后修补框架，仅使用单个报告失败案例即可修复被污染的模型参数，这种轻量级的防御手段在资源受限的生产环境中更具实用价值。

## Looking Forward

尽管 Agent 安全领域取得了显著进展，但仍存在若干未解决的理论问题和待验证的假设。首先是 **Same Weights, Different Robot** 指出的部署安全差距，即相同的权重在不同控制器规范下可能产生不同的物理动作，这意味着模型认证无法完全保证执行策略的安全性，亟需建立可执行策略的规范标准。其次是 **Long-horizon Context Management** 的缺失，现有 Agent 在长周期任务中缺乏原则性的上下文管理能力，容易导致经验积累失效或记忆污染，这需要像 **EvoDS** 和 **SkillPyramid** 这样的工作进一步系统化。最后是 **Deployment Safety Gap** 的量化评估，目前缺乏统一的指标来衡量 Agent 在真实物理环境中的风险敞口，特别是对于具身智能和自动驾驶等高风险领域，需要建立类似 **VLESA** 的实时安全干预基准。未来的研究应重点关注如何在保持 Agent 自主性的同时，实现可解释、可审计且具备动态适应能力的运行时治理体系。

---


## 参考来源

- **From Control Boundary to Insurance Claim: Reconstructing AI-Mediated Losses Through the CER Framework** — [arxiv_ai](https://arxiv.org/abs/2606.03777v1)
- **Agent libOS: A Library-OS-Inspired Runtime for Long-Running, Capability-Controlled LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2606.03895v1)
- **Demo2Tutorial: From Human Experience to Multimodal Software Tutorials** — [arxiv_cv](https://arxiv.org/abs/2606.03951v1)
- **LAP: An Agent-to-Instrument Protocol for Autonomous Science** — [arxiv_ai](https://arxiv.org/abs/2606.03755v1)
- **SkillGuard: A Permission Framework for Agent Skills** — [arxiv_cr](https://arxiv.org/abs/2606.03024v1)
- **Tool-Aware Optimization with Entropy Guidance for Efficient Agentic Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2606.03762v1)
- **Enhancing Operational Safety via Agentic Dialogue Hazard Identification Analysis** — [arxiv_ai](https://arxiv.org/abs/2606.03812v1)
- **The Impact of Configuring Agentic AI Coding Tools on Build-vs-Buy Decisions: A Study Protocol** — [arxiv_ai](https://arxiv.org/abs/2606.03907v1)
- **Synthesize and Reward -- Reinforcement Learning for Multi-Step Tool Use in Live Environments** — [arxiv_ai](https://arxiv.org/abs/2606.03892v1)
- **EvoDS: Self-Evolving Autonomous Data Science Agent with Skill Learning and Context Management** — [arxiv_ai](https://arxiv.org/abs/2606.03841v1)
- **FORGE: Multi-Agent Graduated Exploitation and Detection Engineering** — [arxiv_cr](https://arxiv.org/abs/2606.03453v1)
- **SAGE: A Quantitative Evaluation of Socialized Evolution in Agent Ecosystems** — [arxiv_cl](https://arxiv.org/abs/2606.03544v1)
- **ImageAuditor: Membership Inference Attack against Image-based Retrieval-Augmented Generation** — [arxiv_cr](https://arxiv.org/abs/2606.03354v1)
- **Self-Refining Agentic Reinforcement Learning for Vision-Conditioned UAV Navigation** — [arxiv_ai](https://arxiv.org/abs/2606.03963v1)
- **Overlaying Governance: A Compositional Authorization Framework for Delegation and Scope in Agentic AI** — [arxiv_cr](https://arxiv.org/abs/2606.03518v1)
- **Neural Navigation Functions for Zero-Shot Generalizable Motion Planning** — [arxiv_lg](https://arxiv.org/abs/2606.03756v1)
- **Black-box, Adaptive, Efficient, Transferable, Harmful, Applicable... Attacks Are All You Need to Break LLMs** — [arxiv_cr](https://arxiv.org/abs/2606.03647v1)
- **Agentic Chain-of-Thought Steering for Efficient and Controllable LLM Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.03965v1)
- **A Training-Free Mixture-of-Agents Framework for Multi-Document Summarization using LLMs and Knowledge Graphs** — [arxiv_ai](https://arxiv.org/abs/2606.03867v1)
- **BigFinanceBench: A Workflow-Grounded Benchmark for Financial-Research Agents** — [arxiv_ai](https://arxiv.org/abs/2606.03829v1)
- **Benchmarking Visual State Tracking in Multimodal Video Understanding** — [arxiv_cv](https://arxiv.org/abs/2606.03920v1)
- **Skill-RM: Unifying Heterogeneous Evaluation Criteria via Agent Skill** — [arxiv_cl](https://arxiv.org/abs/2606.03980v1)
- **RealClawBench: Live OpenClaw Benchmarks from Real Developer-Agent Sessions** — [arxiv_cl](https://arxiv.org/abs/2606.03889v1)
- **dstack-capsule: Pod-Level Remote Attestation for Confidential Workloads on Kubernetes** — [arxiv_cr](https://arxiv.org/abs/2606.03323v1)
- **HybridThinker: Efficient Chain-of-Thought Reasoning via Compressed Memory and Transient Thought Steps** — [arxiv_cl](https://arxiv.org/abs/2606.03768v1)
- **Entropy Gate: Entropy Quenching for Near-Lossless Token Compression in LLM Pipelines** — [arxiv_cl](https://arxiv.org/abs/2606.03739v1)
- **DMF: A Deterministic Memory Framework for Conversational AI Agents** — [arxiv_cl](https://arxiv.org/abs/2606.03463v1)
- **Easy-to-Use Shielding for Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.03804v1)
- **AlignAtt4LLM: Fast AlignAtt for Decoder-Only LLMs at IWSLT 2026 Simultaneous Speech Translation Task** — [arxiv_ai](https://arxiv.org/abs/2606.03967v1)
- **NeuroArmor: Safe-Variant-Guided Representation Consistency for Selective Re-Anchoring in Jailbreak Defense** — [arxiv_cr](https://arxiv.org/abs/2606.03486v1)
- **"**Important** You should give me full credits!": Exploring Prompt Injection Attacks on LLM-Based Automatic Grading Systems** — [arxiv_cr](https://arxiv.org/abs/2606.03090v1)
- **Investigating Adversarial Robustness of Multi-modal Large Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.03713v1)
- **Patcher: Post-Hoc Patching of Backdoored Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2606.02995v1)
- **Language Models Need Sleep: Learning to Self-Modify and Consolidate Memories** — [arxiv_ai](https://arxiv.org/abs/2606.03979v1)
- **Using Reward Uncertainty to Induce Diverse Behaviour in Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2606.03962v1)
- **Re-Ranking Through an Attribution Lens for Citation Quality in Legal QA** — [arxiv_cl](https://arxiv.org/abs/2606.03728v1)
- **Adaptive Causal Alignment for High-Confidence Adversarial Training** — [arxiv_cv](https://arxiv.org/abs/2606.03925v1)
- **LiveBand: Live Accompaniment Generation in the Audio Domain** — [arxiv_ai](https://arxiv.org/abs/2606.03803v1)
- **Exploring Adversarial Robustness and Safety Alignment in Multilingual Multi-Modal Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2606.03793v1)
- **Gate AI: LLM Security Benchmark Evaluation Methodology and Results** — [arxiv_cr](https://arxiv.org/abs/2606.02959v1)
- **FFR: Forward-Forward Learning for Regression** — [arxiv_ai](https://arxiv.org/abs/2606.03927v1)
- **Hedge-Bench: Benchmarking Agents on Hard, Realistic Tasks Pertaining to Financial Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.03918v1)
- **From 'What' to 'How' and 'Why': Sharing LLM-Generated Retrospective Summaries of Older Adults' Passive Tracking Data with Remote Family Members** — [arxiv_ai](https://arxiv.org/abs/2606.03876v1)
- **Video-Mirai: Autoregressive Video Diffusion Models Need Foresight** — [arxiv_cv](https://arxiv.org/abs/2606.03971v1)
- **GARDEN: Gravity-Aligned Reconstruction of Disentangled ENvironments from RGB images** — [arxiv_cv](https://arxiv.org/abs/2606.03921v1)
- **Electromagnetic Navigation for Femoral Osteotomy Using High-Accuracy X-ray-to-CT Registration** — [arxiv_cv](https://arxiv.org/abs/2606.03893v1)
- **OVO-S-Bench: A Hierarchical Benchmark for Streaming Spatial Intelligence in Multimodal LLMs** — [arxiv_cv](https://arxiv.org/abs/2606.03890v1)
- **MLP Splatting: Object-Centric Neural Fields** — [arxiv_cv](https://arxiv.org/abs/2606.03877v1)
- **DyaPlex: Full-Duplex Speech-Motion Model for Dyadic Interaction** — [arxiv_cv](https://arxiv.org/abs/2606.03874v1)
- **Value-Aware Stochastic KV Cache Eviction for Reasoning Models** — [arxiv_cl](https://arxiv.org/abs/2606.03928v1)
- **VLESA: Vision-Language Embodied Safety Agent for Human Activity Monitoring** — [arxiv_lg](https://arxiv.org/abs/2606.03954v1)
- **Calibrating Urban Traffic Simulation from Sparse Road Observations via Genetic Optimization** — [arxiv_ai](https://arxiv.org/abs/2606.03823v1)
- **Face versus Body Tracking for Human-Robot Interaction: An Egocentric Dataset** — [arxiv_cv](https://arxiv.org/abs/2606.03694v1)
- **VidMsg: A Benchmark for Implicit Message Inference in Short Videos** — [arxiv_cv](https://arxiv.org/abs/2606.03635v1)
- **Don't Trust Us: A privacy-by-design android malware detection pipeline** — [arxiv_cr](https://arxiv.org/abs/2606.03714v1)
- **Bastet: A Fine-Grained Expert-Labeled Dataset for DeFi Smart Contract Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2606.03387v1)
- **SkillPyramid: A Hierarchical Skill Consolidation Framework for Self-Evolving Agents** — [arxiv_cl](https://arxiv.org/abs/2606.03692v1)
- **Can LLM Rerankers Predict Their Own Ranking Performance?** — [arxiv_cl](https://arxiv.org/abs/2606.03535v1)
- **ZK-Flex: A Flexible and Scalable Framework for Accelerating Zero-Knowledge Proofs** — [arxiv_cr](https://arxiv.org/abs/2606.03046v1)
- **Unified Video-Action Joint Denoising for Dexterous Action and Data Generation** — [arxiv_cv](https://arxiv.org/abs/2606.03868v1)
- **Explainable Forecasting of Scientific Breakthroughs from Concept Network Dynamics** — [arxiv_lg](https://arxiv.org/abs/2606.03864v1)
- **Beyond False Stability: High-Noise Drift Gating for Test-Time Adversarial Defenses in Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.03730v1)
- **Learn from Your Mistakes: Tree-like Self-Play for Secure Code LLMs** — [arxiv_cr](https://arxiv.org/abs/2606.03489v1)
- **AI Model Extraction Attacks: Bypassing Single-Client Assumptions in Defenses** — [arxiv_cr](https://arxiv.org/abs/2606.03381v1)
- **FLIPS: Instance-Fingerprinting for LLMs via Pseudo-random Sequences** — [arxiv_cr](https://arxiv.org/abs/2606.03330v1)
- **PsychoPass: Geometric Profiling of Multi-Turn Adversarial LLM Conversations** — [arxiv_cr](https://arxiv.org/abs/2606.03136v1)
- **Decoupled Smart Contract Audits: Lightweight LLM Framework via Distillation and Aggregation** — [arxiv_cr](https://arxiv.org/abs/2606.03128v1)
- **Don't Forget Your Embeddings: Robust Knowledge Erasure via Precise Editing of Embeddings** — [arxiv_cl](https://arxiv.org/abs/2606.03695v1)
- **World Models Meet Language Models: On the Complementarity of Concrete and Abstract Reasoning** — [arxiv_cl](https://arxiv.org/abs/2606.03603v1)
- **P\textsuperscript{2}-DPO: Grounding Hallucination in Perceptual Processing via Calibration Direct Preference Optimization** — [arxiv_cl](https://arxiv.org/abs/2606.03376v1)
- **Outsmarting the Chameleon: Counterfactual Decoupling for Tactical OOD Shifts in Live Streaming Risk Assessment** — [arxiv_cr](https://arxiv.org/abs/2606.02946v1)
- **SimuScene: Simulation-Ready Compositional 3D Scene Reconstruction from a Single Image** — [arxiv_cv](https://arxiv.org/abs/2606.03994v1)
- **AAD-1: Asymmetric Adversarial Distillation for One-Step Autoregressive Video Generation** — [arxiv_cv](https://arxiv.org/abs/2606.03972v1)
- **A Pocket Offline Model for Simultaneous Speech Translation as CUNI Submission to IWSLT 2026** — [arxiv_cl](https://arxiv.org/abs/2606.03948v1)
- **Visual Instruction Tuning Aligns Modalities through Abstraction** — [arxiv_cl](https://arxiv.org/abs/2606.03871v1)
- **Correcting Neural Operator Spectral Bias via Diffusion Posterior Sampling with Sparse Observations** — [arxiv_lg](https://arxiv.org/abs/2606.03936v1)
- **Contrastive Neural Algorithmic Reasoning for Graph Coloring** — [arxiv_lg](https://arxiv.org/abs/2606.03923v1)
- **Forecasting Conceptual Diffusion in Science: The Case of Quantum Computing** — [arxiv_lg](https://arxiv.org/abs/2606.03919v1)
- **Beyond Gradient Descent: Adam for Analog Ising Machines** — [arxiv_lg](https://arxiv.org/abs/2606.03917v1)
- **Denoise First, Orthogonalize Later: Understanding Momentum in Muon via Spectral Filtering** — [arxiv_lg](https://arxiv.org/abs/2606.03899v1)
- **Online Learning with Gradient-Variation Interval Regret** — [arxiv_lg](https://arxiv.org/abs/2606.03831v1)
- **Same Weights, Different Robot: A Deployment Safety View of VLA Policies** — [arxiv_cr](https://arxiv.org/abs/2606.03724v1)
- **Dynamic Short Convolutions Improve Transformers** — [arxiv_cl](https://arxiv.org/abs/2606.03825v1)
- **Backdoor Unlearning Generalization: A Path Toward the Removal of Unknown Triggers in LLMs** — [arxiv_cl](https://arxiv.org/abs/2606.03785v1)
- **Does Language Shift Break Medical Vision-Language Models? Indonesian Radiology Visual Question Answering Case Study** — [arxiv_cl](https://arxiv.org/abs/2606.03693v1)
- **CoEval: Ranking Language Models for Custom Tasks Without Labeled Data or Trustworthy Benchmarks** — [arxiv_cl](https://arxiv.org/abs/2606.03650v1)
- **Bregman meets Lévy: Stochastic mirror descent with heavy-tailed noise in continuous and discrete time** — [arxiv_lg](https://arxiv.org/abs/2606.03769v1)
- **Microsoft offers devs a better way to control AI agent behavior** — [techcrunch_ai](https://techcrunch.com/2026/06/02/microsoft-offers-devs-a-better-way-to-control-ai-agent-behavior/)
- **Microsoft&#8217;s Project Solara is an OS for AI agent gadgets** — [theverge_ai](https://www.theverge.com/news/941830/microsoft-project-solara-os-ai-agent-gadgets)
- **Exploring Easy Boosts for Lidar Semantic Scene Completion** — [arxiv_cv](https://arxiv.org/abs/2606.03992v1)
- **PixVOD: Pixel-Distributed Direct Visual Odometry and Depth Estimation** — [arxiv_cv](https://arxiv.org/abs/2606.03989v1)
- **NewtPhys: Do Foundation Models Understand Newtonian Physics?** — [arxiv_cv](https://arxiv.org/abs/2606.03986v1)
- **PatchScene: Patch-based Voxel Diffusion for Large-Scale Scene Completion** — [arxiv_cv](https://arxiv.org/abs/2606.03915v1)
- **MLSkip: Data Skipping for ML Filters via Lightweight Metadata** — [arxiv_lg](https://arxiv.org/abs/2606.03946v1)
- **SEAOTTER: Sensor Embedded Autoencoding with One-Time Transcode for Efficient Reconstruction** — [arxiv_lg](https://arxiv.org/abs/2606.03940v1)
- **Quadratic integrate-and-fire neurons exhibit less fragmented loss landscapes and outperform leaky integrate-and-fire neurons in spike-based gradient descent** — [arxiv_lg](https://arxiv.org/abs/2606.03935v1)
- **DiffUNet^2: Bidirectional Prediction, Probabilistic Generation and Collaborative Visual Discovery for Scientific Data** — [arxiv_lg](https://arxiv.org/abs/2606.03926v1)
- **MAdam: Metric-Aware Multi-Objective Adam** — [arxiv_lg](https://arxiv.org/abs/2606.03904v1)
- **CoralBay: A Self-Supervised CT Foundation Model** — [arxiv_lg](https://arxiv.org/abs/2606.03888v1)
- **Attribution via Distributional Paths for Information Revelation** — [arxiv_lg](https://arxiv.org/abs/2606.03885v1)
- **Two-Action Apple Tasting with Switching Costs** — [arxiv_lg](https://arxiv.org/abs/2606.03851v1)
- **Text-attributed Graph Condensation via Text Selection and Attribute Matching** — [arxiv_lg](https://arxiv.org/abs/2606.03839v1)
- **Gemini Spark is the most impressive and terrifying AI experience I’ve had yet** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/941388/gemini-spark-ai-agent-trip-planning)
- **Rehumanizing global health care with agentic AI** — [mit_tech_review](https://www.technologyreview.com/2026/06/02/1137827/rehumanizing-global-health-care-with-agentic-ai/)
- **modelstudioai/cli** — [github](https://github.com/modelstudioai/cli)
- **Codex for every role, tool, and workflow** — [openai](https://openai.com/index/codex-for-every-role-tool-workflow)
- **exon-research/genomi** — [github](https://github.com/exon-research/genomi)
- **OnlyTerp/prompt-cache-skills** — [github](https://github.com/OnlyTerp/prompt-cache-skills)
- **Advancing youth safety and opportunity through global leadership** — [openai](https://openai.com/index/advancing-youth-safety-and-opportunity-through-global-leadership)
- **Microsoft Build 2026: The 7 biggest announcements** — [theverge_ai](https://www.theverge.com/tech/941738/microsoft-build-2026-biggest-announcements)
- **New Microsoft tool lets devs spin up AI behavior tests using text descriptions** — [techcrunch_ai](https://techcrunch.com/2026/06/02/new-microsoft-tool-lets-devs-spin-up-ai-behavior-tests-using-text-descriptions/)
- **Google rolls out fake call detection to protect against AI deepfake impersonation scams** — [techcrunch_ai](https://techcrunch.com/2026/06/02/google-rolls-out-fake-call-detection-to-protect-against-ai-deepfake-impersonation-scams/)
- **Amazon faces class action lawsuit over Ring facial-recognition feature** — [techcrunch_ai](https://techcrunch.com/2026/06/02/amazon-faces-class-action-lawsuit-over-ring-facial-recognition-feature/)
- **Trump signs narrower executive order on AI oversight after industry objections** — [techcrunch_ai](https://techcrunch.com/2026/06/02/trump-signs-narrower-executive-order-on-ai-oversight-after-industry-objections/)
- **Trump signs executive order to review AI models before they’re released** — [theverge_ai](https://www.theverge.com/policy/941775/trump-ai-executive-order)
- **Microsoft’s first advanced reasoning AI is here** — [theverge_ai](https://www.theverge.com/tech/941664/microsoft-ai-model-reasoning-mai-thinking-1-build-2026)
- **Microsoft Scout is a new AI personal assistant built on OpenClaw** — [theverge_ai](https://www.theverge.com/news/939713/microsoft-scout-assistant-openclaw)
- **Google’s Phone app will tell you if a scammer is impersonating one of your contacts** — [theverge_ai](https://www.theverge.com/tech/941517/google-phone-scammer-ai-impersonation)
- **Microsoft created the mini Surface dev box that Qualcomm couldn&#8217;t** — [theverge_ai](https://www.theverge.com/news/941271/microsoft-surface-rtx-spark-dev-box-specs-availability)
- **OpenAI launches new Codex tools for white-collar work** — [techcrunch_ai](https://techcrunch.com/2026/06/02/openai-launches-new-codex-tools-for-white-collar-work/)
- **Anthropic scales Claude Mythos  to critical infrastructure in 15+ countries** — [techcrunch_ai](https://techcrunch.com/2026/06/02/anthropic-scales-claude-mythos-to-critical-infrastructure-in-15-countries/)
- **Microsoft Build 2026: All the news about Windows, AI, RTX Spark, and more** — [theverge_ai](https://www.theverge.com/tech/941668/microsoft-build-may-2026-live-news-updates)
- **The Download: AI can run your admin department now** — [mit_tech_review](https://www.technologyreview.com/2026/06/02/1138277/the-download-ai-tips-small-businesses-admin/)
- **Travelers deploys AI-powered claims countrywide with OpenAI** — [openai](https://openai.com/index/travelers)
- **How small businesses can leverage AI** — [mit_tech_review](https://www.technologyreview.com/2026/06/02/1138227/how-small-businesses-can-leverage-ai/)
- **bigchuidw3/spring-ai-agentx** — [github](https://github.com/bigchuidw3/spring-ai-agentx)
- **Caph-dev/agents-progressive-disclosure** — [github](https://github.com/Caph-dev/agents-progressive-disclosure)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **NazzarenoGiannelli/tuiboard** — [github](https://github.com/NazzarenoGiannelli/tuiboard)
- **ATOM00blue/machine-learning-library** — [github](https://github.com/ATOM00blue/machine-learning-library)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **Cyera eyes $12B valuation at 80x ARR multiple despite operating losses** — [techcrunch_ai](https://techcrunch.com/2026/06/02/cyera-eyes-12b-valuation-at-80x-arr-multiple-despite-operating-losses/)
- **Uber caps employee AI spending after blowing through budget in 4 months** — [techcrunch_ai](https://techcrunch.com/2026/06/02/uber-caps-employee-ai-spending-after-blowing-through-budget-in-four-months/)
- **Martin Scorsese becomes the latest — and most unlikely — Hollywood voice for AI** — [techcrunch_ai](https://techcrunch.com/2026/06/02/martin-scorsese-becomes-the-latest-and-most-unlikely-hollywood-voice-for-ai/)
- **Microsoft launches Scout, an OpenClaw-inspired personal assistant** — [techcrunch_ai](https://techcrunch.com/2026/06/02/microsoft-launches-scout-an-openclaw-inspired-personal-assistant/)
- **ZeroDrift raises $10M to protect AI models from themselves** — [techcrunch_ai](https://techcrunch.com/2026/06/02/zerodrift-raises-10-million-to-protect-ai-models-from-themselves/)
- **Rocket engine startup Impulse raises $500 million to hire people, not AI** — [techcrunch_ai](https://techcrunch.com/2026/06/02/rocket-engine-startup-impulse-raises-500-million-to-hire-people-not-ai/)
- **kurikomi-labs/komi-learn** — [github](https://github.com/kurikomi-labs/komi-learn)
- **tommy0103/obelisk** — [github](https://github.com/tommy0103/obelisk)
- **lucasfcosta/backpressured** — [github](https://github.com/lucasfcosta/backpressured)
- **PentesterFlow/agent** — [github](https://github.com/PentesterFlow/agent)
- **DannyMac180/skills** — [github](https://github.com/DannyMac180/skills)
- **tonbistudio/hermes-multi-agent-workflow** — [github](https://github.com/tonbistudio/hermes-multi-agent-workflow)
- **veryyoldman/metamask-openclaw** — [github](https://github.com/veryyoldman/metamask-openclaw)
- **ethanhq/cc-fleet** — [github](https://github.com/ethanhq/cc-fleet)
- **krispuckett/SwiftUIShaders** — [github](https://github.com/krispuckett/SwiftUIShaders)
- **steeliron550-ui/search-bibtex** — [github](https://github.com/steeliron550-ui/search-bibtex)
- **K-Dense-AI/science-superpowers** — [github](https://github.com/K-Dense-AI/science-superpowers)
- **刚刚，Meta Skill来了** — [qbitai](https://www.qbitai.com/2026/06/428335.html)
- **MiniMax M3一手实测：老黄PPT上74个Logo，我以为能难住它** — [qbitai](https://www.qbitai.com/2026/06/428092.html)
- **OpenAI挖走中科大少年班校友！12岁上大学，哈佛史上最年轻正教授** — [qbitai](https://www.qbitai.com/2026/06/428003.html)
- **头部厂商集体买单，全球AI原生达人营销头号平台正在诞生！** — [qbitai](https://www.qbitai.com/2026/06/427922.html)
- **滴滴2026Q1财报：国内基本盘稳固 国际业务成第二增长引擎** — [qbitai](https://www.qbitai.com/2026/06/428331.html)
- **字节开源统一框架Bernini：给DiT配个“大模型军师”，AI视频编辑先理解再动手** — [qbitai](https://www.qbitai.com/2026/06/427810.html)
- **“豆包汽车”，目标市场10万-20万** — [qbitai](https://www.qbitai.com/2026/06/427760.html)
- **百度文心发布 PaddleOCR-VL-1.6：准确率突破 96.33%，刷新文档解析 SOTA** — [qbitai](https://www.qbitai.com/2026/06/427754.html)
- **Few-Shot Prediction for Pulsar Noise with Long Short-Term Memory Network** — [arxiv_ml](https://arxiv.org/abs/2606.03574v1)
- **Solipsistic Superintelligence is Unlikely to be Cooperative** — [arxiv_cy](https://arxiv.org/abs/2606.03237v1)
- **Effect of Demographic Bias on Skin Lesion Classification** — [arxiv_cy](https://arxiv.org/abs/2606.03214v1)
- **A Robust Optimization Approach to Sparse Principal Component Analysis** — [arxiv_ml](https://arxiv.org/abs/2606.03553v1)
- **Optimized Labeling Resource Allocation for Prediction-Assisted Inference via OPAL** — [arxiv_ml](https://arxiv.org/abs/2606.03211v1)
- **Dynamic Objective Selection with Safeguards and LLM Oversight for Financial Decision-Making** — [arxiv_cy](https://arxiv.org/abs/2606.03704v1)
- **TurtleAI: Benchmarking Multimodal Models for Visual Programming in Turtle Graphics** — [arxiv_cy](https://arxiv.org/abs/2606.03626v1)
- **Pushing the Limits: A Framework to Reform Institutional Ethics Review of Environmentally-Impactful Computing Research** — [arxiv_cy](https://arxiv.org/abs/2606.03547v1)
- **8点1氪丨腾讯股价暴涨，创2021年后单日最高涨幅；预计今年安排约1100亿育儿补贴；英伟达与微软合作推出统一技术栈** — [36kr](https://36kr.com/p/3836703946257542?f=rss)
- **Set-Preserving Calibration from Conformal P-Values to E-Values** — [arxiv_ml](https://arxiv.org/abs/2606.03600v1)
- **Multimodal Transformer Based Generic Mixture Density Network for Scattering Timescale Estimation of Fast Radio Bursts** — [arxiv_ml](https://arxiv.org/abs/2606.03596v1)
- **Analytical Evaluation of DCA Convergence Properties for Minimizing Prediction Functions of Gaussian RBF Support Vector Regression** — [arxiv_ml](https://arxiv.org/abs/2606.03559v1)
- **AugMask: Training Diffusion Models on Incomplete Tabular Data via Stochastic Augmentation and Masking** — [arxiv_ml](https://arxiv.org/abs/2606.03347v1)
- **Combining Statistical Features and Deep Encodings for Rehearsal-Based Class-Incremental Time Series Classification** — [arxiv_ml](https://arxiv.org/abs/2606.03292v1)
- **Do Real-World Datasets Contain Natural Experiments? An Empirical Study Using Causal Feature Selection** — [arxiv_ml](https://arxiv.org/abs/2606.03251v1)
- **Hierarchies of Calibration: Classification meets Regression** — [arxiv_ml](https://arxiv.org/abs/2606.03245v1)
- **An Asymptotic Theory of Chain-of-Thought in In-Context Learning** — [arxiv_ml](https://arxiv.org/abs/2606.03217v1)
- **Gender-Dependent Diagnostic Substitution in LLM Medical Triage: Same Symptoms, Unequal Urgency** — [arxiv_cy](https://arxiv.org/abs/2606.03641v1)
- **Intellectual Humility as a Cognitive Filter for AI-Generated Health Misinformation. An Evolutionary Perspective on Epistemic Vigilance** — [arxiv_cy](https://arxiv.org/abs/2606.03377v1)
- **Beyond Semantics: Modeling Factual and Affective Perceptual Experiences from Vision-Language Data** — [arxiv_cy](https://arxiv.org/abs/2606.03345v1)
- **AI-Generated Traces for Novice Programmers: Learning Effects and Learner Differences in a Multi-Institutional Study** — [arxiv_cy](https://arxiv.org/abs/2606.03288v1)
- **PitchBook分析师：SpaceX合理估值1.5万亿美元，AI业务5年内难扭亏** — [36kr](https://36kr.com/newsflashes/3836915776959620?f=rss)
- **腾讯AI产业应用大会在即，即将发布系列智能体应用新品** — [36kr](https://36kr.com/newsflashes/3836838876935557?f=rss)
- **微信将推出一款AI智能体？腾讯人士回应** — [36kr](https://36kr.com/newsflashes/3836820673574024?f=rss)
- **“星源智”完成新一轮融资** — [36kr](https://36kr.com/newsflashes/3836806137738377?f=rss)
- **深圳具身公司星尘智能完成超10亿B轮融资，估值破百亿｜硬氪首发** — [36kr](https://36kr.com/p/3836068296209537?f=rss)
- **36氪首发 | 浙大教授团队获财通、商汤投资，做高危场景具身机器人大脑** — [36kr](https://36kr.com/p/3836744788014208?f=rss)
- **氪星晚报｜私募股权公司Ardian将与Verne合作，斥资50亿欧元在法国建数字基础设施园区；快手：平台累计催生189个新职业，其中由AI发展带来的新职业达15个；中央财政下达育儿补贴补助资金999亿元支持实施育儿补贴制度** — [36kr](https://36kr.com/p/3834354708031111?f=rss)
- **美团在竞争中看清自己** — [36kr](https://36kr.com/p/3835814792492416?f=rss)
- **豆包6月下旬正式付费，并加速打通抖音电商丨36氪独家** — [36kr](https://36kr.com/p/3835814391100550?f=rss)
- **做了18年民宿的爱彼迎，开始卖酒店了？** — [36kr](https://36kr.com/p/3835511712363657?f=rss)
- **奇瑞汽车在安徽成立新股权投资公司，注册资本1亿** — [36kr](https://36kr.com/newsflashes/3836854874125703?f=rss)
- **微盟内测国内首个“电商AI增长引擎”** — [36kr](https://36kr.com/newsflashes/3836847649322369?f=rss)
- **机器人公司帕西尼据悉正考虑在香港上市** — [36kr](https://36kr.com/newsflashes/3836925919425928?f=rss)