# AI 日报 [AI 安全] - 2026-06-13


# AI Safety Daily Digest: 2026-06-13

## Highlights

今日研究进展在 Agent 运行时安全与治理架构上取得了显著突破，核心聚焦于持久化记忆系统的防御机制与多智能体协作的合规性。首先，针对 RAG Agent 中日益严峻的跨会话记忆污染问题，**SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems** 提出了首个针对多会话记忆投毒（MSMP）的认证防御方案，揭示了现有静态语料库防御在动态 Agent 环境下的失效边界。其次，企业级生产环境的 Agent 治理范式正在重构，**A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** 指出传统数据边界控制已无法适应 Agent 自主调用工具的行为模式，并提出了基于工作流内部风险控制的五平面参考架构。最后，自动化红队测试技术向多智能体协同攻击方向演进，**PI-Hunter: Automated Red-Teaming for Exposing and Localizing Prompt Injections** 与 **MAStrike: Shapley-Guided Collusive Red-Teaming on Multi-Agent Systems** 分别从单 Agent 提示注入定位和多智能体合谋攻击两个维度，为评估复杂 Agent 系统的安全性提供了新的方法论。

## Agent 安全与治理

随着大语言模型从被动问答转向主动执行任务，Agent 的安全边界已从单一模型权重扩展至整个运行轨迹与外部交互环境。当前最紧迫的风险在于持久化记忆系统的完整性，**SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems** 深入分析了检索增强生成（RAG）Agent 在跨用户会话中积累记忆所带来的新型攻击面。作者指出，攻击者无需触碰模型权重或代码，仅通过正常渠道注入精心构造的记忆，即可在未来会话中劫持 Agent 行为，这种多会话记忆投毒（MSMP）现象暴露了现有静态防御机制的根本缺陷。与之相呼应，**Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval** 进一步探讨了图结构记忆中的选择完整性问题，论证了仅检查检索记录来源的证明（provenance）是构建上的盲点，因为不可信主体写入的结构本身会改变可信事实的选择逻辑。这两项工作共同表明，Agent 记忆管理必须引入信息流控制（IFC）的动态视角，而非简单的静态过滤。

在企业级部署层面，传统的网络安全边界概念正在瓦解。**A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** 强调，生产环境中的 Agent 读取上下文、调用工具并修改系统记录，风险已内嵌于工作流序列之中。现有的策略引擎无法评估这种由单个许可动作组成的业务流程转换，因此需要一种能够理解 Agent 意图与行动后果的新型治理架构。这一观点在 **Neuro-Symbolic Agents for Regulated Process Automation: Challenges and Research Agenda** 中得到了延伸，后者主张将符号结构（如法规、流程模型）作为 Agent 决策的核心架构组件，而非仅仅是外部的监控护栏，提出“合规即构建”（compliance-by-construction）的范式以预防控制流违规。

多智能体系统（MAS）的引入进一步增加了攻击面的复杂性。**MAStrike: Shapley-Guided Collusive Red-Teaming on Multi-Agent Systems** 针对分层多智能体系统中的角色专业化特点，利用 Shapley 值指导合谋红队测试，识别出哪些特定角色的 Agent 最容易成为权限提升和跨 Agent 合谋的突破口。实验显示，现有的启发式红队方法往往孤立地扰动消息流，忽略了系统层面的协同风险。与此同时，**Smarter Saboteurs, Better Fixers: Scaling & Security in Linear Multi-Agent Workflows** 研究了模型规模对线性多智能体工作流安全性的影响，发现随着模型规模的扩大，虽然修复能力有所提升，但合规性与修正之间的平衡关系变得更为微妙，这提示我们在设计大规模 Agent 协作网络时，不能单纯依赖模型能力的堆叠来换取安全性。此外，针对具身智能与视觉语言系统，**Beyond Attack Success Rate: Examining Trigger Leakage in Vision-Language Agentic Systems** 形式化了触发器精度失败的概念，指出当前的后门评估指标未能捕捉到视觉后门在决策管道中的传播特性，强调了系统级威胁评估的重要性。

## 工具调用、提示注入与运行时防御

工具调用的安全性是 Agent 运行时防御的核心环节，尤其是当 Agent 被赋予访问文件系统、代码执行及外部 API 的权限时。**HyperTool: Beyond Step-Wise Tool Calls for Tool-Augmented Agents** 提出了一种统一的可执行 MCP 风格工具接口，旨在解决原子化工具调用导致的执行粒度不匹配问题，通过减少模型可见的决策次数来降低上下文消耗和潜在的攻击暴露面。然而，工具接口的优化并不能完全消除提示注入风险。**PI-Hunter: Automated Red-Teaming for Exposing and Localizing Prompt Injections** 开发了一个自动化的代理审计框架，旨在主动暴露潜伏的提示注入漏洞及其在 Agent 内部的传播路径，弥补了现有防御主要关注推理时内容阻断而缺乏对注入溯源能力的不足。该框架不仅检测攻击是否成功，更致力于揭示攻击如何在未授权的外部源中嵌入指令并影响后续决策。

针对移动 GUI Agent 特有的隐私泄露风险，**CAPED: Context-Aware Privacy Exposure Defense for Mobile GUI Agents** 解决了屏幕截图观察带来的附带视觉隐私暴露问题。由于移动 Agent 通过视觉界面操作应用，每一帧截图都可能包含联系人、消息或健康数据等敏感上下文，现有的文本匿名化或通用隐私掩码难以应对此类推断性线索。该研究提出了一种上下文感知的防御机制，试图在保持功能性的同时最小化隐私边界。在更广泛的运行时强制层面，**Getting Better at Working With You: Compiling User Corrections into Runtime Enforcement for Coding Agents** 引入了 TRACE 框架，将用户的纠正意见编译为原子规则并在运行时强制执行，解决了偏好访问与偏好合规之间的差距，使得 Agent 能够在不同会话中持续遵守用户的具体约束。

对于强化学习（RL）Agent 的安全性，**PolicyGuard: Towards Test-time and Step-level Adversary Defense for Reinforcement Learning Agent** 填补了 RL 系统在测试时和步骤级对抗防御方面的空白。现有的 RL 后门防御通常依赖于模型内部参数访问或仅在轨迹层面操作，而 PolicyGuard 提供了一种无需访问内部参数的防御手段，确保 Agent 在标准条件下表现正常，而在特定触发器激活时不会执行恶意动作。此外，**Beyond Runtime Enforcement: Shield Synthesis as Defensibility Analysis for Adversarial Networks** 重新审视了屏蔽强化学习的本质，认为其时序逻辑规范编译不应仅被视为运行时约束，更应作为一种设计时的分析工具，用于提取关于系统结构的洞察，从而在部署前识别潜在的结构性弱点。

## 模型对齐、评估基准与鲁棒性

评估体系的标准化是确保 Agent 安全与性能可比性的基础。**AgentBeats: Agentifying Agent Assessment for Openness, Standardization, and Reproducibility** 倡导了一种代理化代理评估（AAA）的新范式，主张通过标准化的协议（如 A2A 任务管理和 MCP 工具访问）让评估者 Agent 与被评估 Agent 进行交互，以解决现有基准测试因高度集成需求导致的测试与生产不匹配问题。为了应对真实世界环境的动态变化，**EvoBrowseComp: Benchmarking Search Agents on Evolving Knowledge** 引入了一个不断演进的基准套件，模拟终端、软件和社交领域的渐进式更新，防止模型通过事实回忆而非真正的检索推理来获得高分。这与 **Who Pays the Price? Stakeholder-Centric Prompt Injection Benchmarking for Real-world Web Agents** 的观点一致，后者批评现有的安全基准过于关注攻击的技术可行性，而忽视了受害者依赖性和实际危害分布的差异，呼吁建立以利益相关者为中心的风险评估体系。

在模型对齐与知识管理方面，**MemRefine: LLM-Guided Compression for Long-Term Agent Memory** 提出了基于 LLM 引导的压缩方法，以解决长期交互中记忆存储无限增长的问题，通过存储预算管理的任务保持记忆的有效性。对于科学发现领域的 Agent，**Agents-K1: Towards Agent-native Knowledge Orchestration** 构建了一个端到端的知识编排管道，将原始文档转换为 Agent 原生的科学图谱，弥补了现有工作忽略关键实体、证据和方法谱系的缺陷。在奖励建模方面，**Reward Modeling for Multi-Agent Orchestration** 提出了一种自监督框架 OrchRM，利用多智能体执行过程中的中间产物构建胜负对，以低成本训练编排质量评估模型，解决了多智能体系统中监督稀缺和高计算成本的问题。

开源社区也在积极构建 Agent 安全与工程化的基础设施。**thu-nmrc/openloop** 提供了一个通用的循环工程框架，支持日志、心跳、护栏和可审计停止条件的闭环验证，这对于调试复杂的 Agent 工作流至关重要。**CYC2002tommy/Deep-Research-Agent** 则展示了如何利用 MCP 协议连接 Scopus 和 OpenAlex API 来实现深度研究任务的自动化，体现了工具链集成的趋势。值得注意的是，**superagents-lab/xcode27-skills** 导出了 Apple 官方的 Agent Skills，涵盖了 SwiftUI 现代化和安全加固，这表明主流操作系统厂商开始将安全技能直接纳入 Agent 的能力定义中。尽管市场上存在大量关于 Agent 效能的宣传，但独立验证的基准测试如 **EpiBench: Verifiable Evaluation of AI Agents on Epigenomics Analysis** 显示，即使在特定领域如表观基因组学分析中，现有系统通过多数尝试的比例仍然较低，这提醒我们需警惕过度营销的评估结果。

## Looking Forward

尽管今日的研究在 Agent 内存防御、运行时治理和多智能体红队测试方面取得了重要进展，但仍存在若干未解决的理论问题与待验证假设。首先，关于持久化记忆的认证防御，**SMSR** 虽然提供了理论保证，但在高并发、多租户的企业环境中，如何平衡认证开销与实时响应延迟仍需实证研究。其次，多智能体系统中的合谋攻击检测，**MAStrike** 提出的 Shapley 值方法计算复杂度较高，在实际大规模分布式系统中的可扩展性尚未经过充分验证。最后，在合规即构建的范式中，如何将复杂的法律条文和行业标准转化为机器可执行的符号约束，仍面临语义鸿沟的挑战。未来的工作应重点关注跨域 Agent 协作中的信任传递机制，以及在不牺牲 Agent 自主性的前提下实现细粒度的运行时干预能力。此外，随着 AI 驱动的网络渗透能力逐渐显现（如 **The Emergence of Autonomous Penetration Capabilities in Large Language Model-Powered AI Systems** 所述），建立针对自主攻击行为的防御标准与法律监管框架已成为亟待解决的现实问题。

---


## 参考来源

- **SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12703v1)
- **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12320v1)
- **PI-Hunter: Automated Red-Teaming for Exposing and Localizing Prompt Injections** — [arxiv_cr](https://arxiv.org/abs/2606.12737v1)
- **Recursive Agent Harnesses** — [arxiv_cl](https://arxiv.org/abs/2606.13643v1)
- **AgentBeats: Agentifying Agent Assessment for Openness, Standardization, and Reproducibility** — [arxiv_ai](https://arxiv.org/abs/2606.13608v1)
- **MemRefine: LLM-Guided Compression for Long-Term Agent Memory** — [arxiv_cl](https://arxiv.org/abs/2606.13177v1)
- **Getting Better at Working With You: Compiling User Corrections into Runtime Enforcement for Coding Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13174v1)
- **HarnessBridge: Learnable Bidirectional Controller for LLM Agent Harness** — [huggingface_papers](https://arxiv.org/abs/2606.12882)
- **Beyond Runtime Enforcement: Shield Synthesis as Defensibility Analysis for Adversarial Networks** — [arxiv_ai](https://arxiv.org/abs/2606.13621v1)
- **Who Pays the Price? Stakeholder-Centric Prompt Injection Benchmarking for Real-world Web Agents** — [arxiv_ai](https://arxiv.org/abs/2606.13385v1)
- **Beyond Attack Success Rate: Examining Trigger Leakage in Vision-Language Agentic Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12586v1)
- **OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12341v1)
- **EvoArena: Tracking Memory Evolution for Robust LLM Agents in Dynamic Environments** — [arxiv_cl](https://arxiv.org/abs/2606.13681v1)
- **HyperTool: Beyond Step-Wise Tool Calls for Tool-Augmented Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13663v1)
- **SpatialClaw: Rethinking Action Interface for Agentic Spatial Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.13673v1)
- **Agents-K1: Towards Agent-native Knowledge Orchestration** — [arxiv_ai](https://arxiv.org/abs/2606.13669v1)
- **Understanding the Rejection of Fixes Generated by Agentic Pull Requests -- Insights from the AIDev Dataset** — [arxiv_ai](https://arxiv.org/abs/2606.13468v1)
- **Toward Instructions-as-Code: Understanding the Impact of Instruction Files on Agentic Pull Requests** — [arxiv_ai](https://arxiv.org/abs/2606.13449v1)
- **MiniMax Sparse Attention** — [arxiv_ai](https://arxiv.org/abs/2606.13392v1)
- **InterleaveThinker: Reinforcing Agentic Interleaved Generation** — [arxiv_cv](https://arxiv.org/abs/2606.13679v1)
- **DIG: Oracle-Guided Directed Input Generation for One-Day Vulnerabilities** — [arxiv_cr](https://arxiv.org/abs/2606.13037v1)
- **Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval** — [arxiv_cr](https://arxiv.org/abs/2606.12290v1)
- **EvoBrowseComp: Benchmarking Search Agents on Evolving Knowledge** — [huggingface_papers](https://arxiv.org/abs/2606.13120)
- **MAStrike: Shapley-Guided Collusive Red-Teaming on Multi-Agent Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12918v1)
- **RogueAI: A Reverse Turing Test for Detecting Licensed AI Deception in Dialogue** — [arxiv_cl](https://arxiv.org/abs/2606.13310v1)
- **Learning to Reason by Analogy via Retrieval-Augmented Reinforcement Fine-Tuning** — [arxiv_ai](https://arxiv.org/abs/2606.13680v1)
- **EurekAgent: Agent Environment Engineering is All You Need For Autonomous Scientific Discovery** — [arxiv_ai](https://arxiv.org/abs/2606.13662v1)
- **Multiagent Protocols with Aggregated Confidence Signals** — [arxiv_ai](https://arxiv.org/abs/2606.13591v1)
- **IterCAD: An Iterative Multimodal Agent for Visually-Grounded CAD Generation and Editing** — [arxiv_ai](https://arxiv.org/abs/2606.13368v1)
- **NavWAM: A Navigation World Action Model for Goal-Conditioned Visual Navigation** — [arxiv_cv](https://arxiv.org/abs/2606.13494v1)
- **PolicyGuard: Towards Test-time and Step-level Adversary Defense for Reinforcement Learning Agent** — [arxiv_cr](https://arxiv.org/abs/2606.12896v1)
- **Smarter Saboteurs, Better Fixers: Scaling & Security in Linear Multi-Agent Workflows** — [arxiv_cr](https://arxiv.org/abs/2606.12709v1)
- **See What I See, Know What I Think: Dense Latent Communication Across Heterogeneous Agents** — [huggingface_papers](https://arxiv.org/abs/2606.13594)
- **WEAVER, Better, Faster, Longer: An Effective World Model for Robotic Manipulation** — [huggingface_papers](https://arxiv.org/abs/2606.13672)
- **WarpGuard: Protected-Site Control-Flow Integrity for CUDA SASS Binaries** — [arxiv_cr](https://arxiv.org/abs/2606.11871v1)
- **SkillCAT: Contrastive Assessment and Topology-Aware Skill Self-Evolution for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13317v1)
- **Mana: Dexterous Manipulation of Articulated Tools** — [arxiv_ai](https://arxiv.org/abs/2606.13677v1)
- **SkMTEB: Slovak Massive Text Embedding Benchmark and Model Adaptation** — [arxiv_ai](https://arxiv.org/abs/2606.13647v1)
- **EpiBench: Verifiable Evaluation of AI Agents on Epigenomics Analysis** — [arxiv_ai](https://arxiv.org/abs/2606.13602v1)
- **Reward Modeling for Multi-Agent Orchestration** — [arxiv_ai](https://arxiv.org/abs/2606.13598v1)
- **ArogyaSutra: A Multi-Agent Framework for Multimodal Medical Reasoning in Indic Languages** — [arxiv_ai](https://arxiv.org/abs/2606.13572v1)
- **Uncertainty-Aware Hybrid Retrieval for Long-Document RAG** — [arxiv_ai](https://arxiv.org/abs/2606.13550v1)
- **Adaptive Turn-Taking for Real-time Multi-Party Voice Agents** — [arxiv_ai](https://arxiv.org/abs/2606.13544v1)
- **Neuro-Symbolic Agents for Regulated Process Automation: Challenges and Research Agenda** — [arxiv_ai](https://arxiv.org/abs/2606.13405v1)
- **TimeLens: On-Device Artifact Recognition with Retrieval-Augmented Question Answering for the Grand Egyptian Museum** — [arxiv_cl](https://arxiv.org/abs/2606.13267v1)
- **ComAct: Reframing Professional Software Manipulation via COM-as-Action Paradigm** — [arxiv_cl](https://arxiv.org/abs/2606.13239v1)
- **MiniPIC: Flexible Position-Independent Caching in <100LOC** — [arxiv_cl](https://arxiv.org/abs/2606.13126v1)
- **CAPED: Context-Aware Privacy Exposure Defense for Mobile GUI Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12666v1)
- **Budget-Constrained Step-Level Diffusion Caching** — [arxiv_cv](https://arxiv.org/abs/2606.13496v1)
- **Categorical Robustness Assessment for Machine Learning based Network Intrusion Detection Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12075v1)
- **When Does Mixing Help? Analyzing Query Embedding Interpolation in Multilingual Dense Retrieval** — [arxiv_cl](https://arxiv.org/abs/2606.13537v1)
- **S-GBT: Smooth Growth Bound Tensor for Certified Robustness Against Word Substitution Attacks in NLP** — [arxiv_cl](https://arxiv.org/abs/2606.13439v1)
- **OR-Action: Multi-Role Video Understanding with Fine-Grained Actions** — [arxiv_cv](https://arxiv.org/abs/2606.13332v1)
- **Aerial Wildfire Suppression Planning with a Hybrid CNN-Cellular Automata Fire Model** — [arxiv_lg](https://arxiv.org/abs/2606.13633v1)
- **Distribution-Agnostic Robust Trajectory Optimization via Chance-Constrained Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.13605v1)
- **GF-DiT: Scheduling Parallelism for Diffusion Transformer Serving** — [arxiv_lg](https://arxiv.org/abs/2606.13501v1)
- **Reinforcement Learning for Neural Model Editing** — [arxiv_lg](https://arxiv.org/abs/2606.13461v1)
- **The Emergence of Autonomous Penetration Capabilities in Large Language Model-Powered AI Systems** — [arxiv_cr](https://arxiv.org/abs/2606.13079v1)
- **Semantic Identification of IoT Devices from Behavioral Primitives** — [arxiv_cr](https://arxiv.org/abs/2606.12793v1)
- **SICI: A Semantic-Pragmatic Complexity Index Reveals Regime Shifts in LLM Stance Detection** — [arxiv_cl](https://arxiv.org/abs/2606.13189v1)
- **SwarmSense-DNN: A Trustworthy and Decentralized Neural Framework for Proactive Anomaly Defense in Consumer IoT** — [arxiv_cr](https://arxiv.org/abs/2606.11803v1)
- **Reinforcement Learning Disrupts Gradient-Based Adversarial Optimization** — [arxiv_cr](https://arxiv.org/abs/2606.12251v1)
- **Toward Trustworthy AI: Multi-Target Adversarial Attacks and Robust Defenses for Continuous Data Summarization** — [arxiv_cr](https://arxiv.org/abs/2606.11804v1)
- **From Passive Generation to Investigation: A Proactive Scientific Peer Review Agent** — [arxiv_cl](https://arxiv.org/abs/2606.13349v1)
- **SPARC: Reliable Spatial Annotations from Robot Demonstrations at Scale** — [arxiv_cv](https://arxiv.org/abs/2606.13497v1)
- **VietFashion: Benchmarking Sketch-Text Composed Image Retrieval for Cultural Outfits** — [arxiv_cv](https://arxiv.org/abs/2606.13427v1)
- **MoVerse: Real-Time Video World Modeling with Panoramic Gaussian Scaffold** — [arxiv_cv](https://arxiv.org/abs/2606.13376v1)
- **NetCause: Counterfactual Learning for Root Cause Analysis in Large-Scale Networks** — [arxiv_lg](https://arxiv.org/abs/2606.13543v1)
- **How Much Memory Do We Need? Adaptive Memory Gate for Neural Operators** — [arxiv_lg](https://arxiv.org/abs/2606.13443v1)
- **Foundations of Practical Quantum Advantage in Quantum-Informed Machine Learning for Predicting Chaos** — [arxiv_lg](https://arxiv.org/abs/2606.13422v1)
- **Quantizing Time-Series Models As Dynamical Systems: Trajectory-Based Quantization Sensitivity Score** — [arxiv_lg](https://arxiv.org/abs/2606.13300v1)
- **Split Tallies: A Discrete Certificate Calculus for Auditing Dynamic Ordered Sets in Constant Memory** — [arxiv_cr](https://arxiv.org/abs/2606.13272v1)
- **LAUKIN: A Multi-jurisdictional Common Law Contract Dataset** — [arxiv_cl](https://arxiv.org/abs/2606.13184v1)
- **HyPE: Category-Aware Hypergraph Encoding with Persistent Edge Embeddings for Persona-Grounded Dialogue** — [arxiv_cl](https://arxiv.org/abs/2606.13142v1)
- **Zero-Shot Captioning for Cultural Heritage: Automated Image Analysis of Traditional Indonesian Clothing** — [arxiv_cv](https://arxiv.org/abs/2606.13275v1)
- **Transformer-Guided Graph Attention for Direct Cardiac Mesh Reconstruction: A Structural Digital Twin Framework** — [arxiv_cv](https://arxiv.org/abs/2606.13188v1)
- **ECYSAP EYE: From Cyber Situational Awareness to Mission-Centric Decision Support for Enhanced Cyberspace Operations** — [arxiv_cr](https://arxiv.org/abs/2606.12354v1)
- **Dual-Domain Equivariant Generative Adversarial Network for Multimodal CT-PET Synthesis** — [arxiv_cv](https://arxiv.org/abs/2606.13341v1)
- **Edit the Bits, Diff the Codes: Bitwise Residual Editing for Visual Autoregressive Models** — [arxiv_cl](https://arxiv.org/abs/2606.13558v1)
- **What's Old is New Again: Classical Dimensionality Reduction for Efficient Saliency-Guided Biometric Attack Detection** — [arxiv_cv](https://arxiv.org/abs/2606.13528v1)
- **MagPlus: Bridging Micro-to-Regular Facial Expressions through Learnable Magnification** — [arxiv_cv](https://arxiv.org/abs/2606.13312v1)
- **Dense Supervision, Sparse Updates: On the Sparsity and Geometry of On-Policy Distillation** — [arxiv_lg](https://arxiv.org/abs/2606.13657v1)
- **The Stable Recovery Manifold: Geometric Principles Governing Recoverability in Continual Learning** — [arxiv_lg](https://arxiv.org/abs/2606.13637v1)
- **Generative Modeling of Bach-Style Symbolic Music: A Comparative Study of Autoregressive, Latent-Variable, and Adversarial Approaches** — [arxiv_lg](https://arxiv.org/abs/2606.13626v1)
- **MaskWAM: Unifying Mask Prompting and Prediction for World-Action Models** — [arxiv_lg](https://arxiv.org/abs/2606.13515v1)
- **VideoMDM: Towards 3D Human Motion Generation From 2D Supervision** — [arxiv_lg](https://arxiv.org/abs/2606.13364v1)
- **Rarity-Gated Context Conditioning for Offline Imitation Learning-Based Maritime Anomaly Detection** — [arxiv_lg](https://arxiv.org/abs/2606.13311v1)
- **Physics-Guided Spatiotemporal Learning for Coastal Wave Peak Period Estimation from Video** — [arxiv_lg](https://arxiv.org/abs/2606.13302v1)
- **Evaluating Pluralism in LLMs through Latent Perspectives** — [arxiv_cl](https://arxiv.org/abs/2606.13254v1)
- **PolyAlign: Conditional Human-Distribution Alignment** — [arxiv_cl](https://arxiv.org/abs/2606.13227v1)
- **Layer-Resolved Optimal Transport for Hallucination Detection in NMT and Abstractive Summarization** — [arxiv_cl](https://arxiv.org/abs/2606.13216v1)
- **Towards More General Control of Diffusion Models Using Jeffrey Guidance** — [arxiv_cv](https://arxiv.org/abs/2606.13240v1)
- **Distributional Loss for Robust Classification** — [arxiv_cv](https://arxiv.org/abs/2606.13223v1)
- **Visual Place Recognition in Forests with Depth-Aware Distillation** — [arxiv_cv](https://arxiv.org/abs/2606.13206v1)
- **Iterative Visual Thinking: Teaching Vision-Language Models Spatial Self-Correction through Visual Feedback** — [arxiv_cv](https://arxiv.org/abs/2606.13156v1)
- **Demystifying Hidden-State Recurrence: Switchable Latent Reasoning with On-Policy Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2606.13106)
- **Modality Forcing for Scalable Spatial Generation** — [arxiv_cv](https://arxiv.org/abs/2606.13676v1)
- **RepWAM: World Action Modeling with Representation Visual-Action Tokenizers** — [arxiv_cv](https://arxiv.org/abs/2606.13674v1)
- **Flex4DHuman: Flexible Multi-view Video Diffusion for 4D Human Reconstruction** — [arxiv_cv](https://arxiv.org/abs/2606.13655v1)
- **World Tracing: Generative Pixel-Aligned Geometry Beyond the Visible** — [arxiv_cv](https://arxiv.org/abs/2606.13652v1)
- **Understanding Truncated Positional Encodings for Graph Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2606.13671v1)
- **Simplex-Constrained Sparse Bagging: Transitioning from Uniform Priors to Sparse Posteriors in Ensemble Learning** — [arxiv_lg](https://arxiv.org/abs/2606.13589v1)
- **Learning with Simulators: No Regret in a Computationally Bounded World** — [arxiv_lg](https://arxiv.org/abs/2606.13576v1)
- **Adjusted Cup-Product Neural Layer** — [arxiv_lg](https://arxiv.org/abs/2606.13568v1)
- **A2D2: Fine-Tuning Any-Length Discrete Diffusion for Adaptive Decoding** — [arxiv_lg](https://arxiv.org/abs/2606.13565v1)
- **CYC2002tommy/Deep-Research-Agent** — [github](https://github.com/CYC2002tommy/Deep-Research-Agent)
- **New OpenAI Academy courses for the next era of work** — [openai](https://openai.com/index/academy-courses-applying-ai-at-work)
- **keyuchen21/agentic-engineering-handbook** — [github](https://github.com/keyuchen21/agentic-engineering-handbook)
- **agentic-in/inferoa** — [github](https://github.com/agentic-in/inferoa)
- **SpaceX IPO: Live updates on everything you need to know** — [techcrunch_ai](https://techcrunch.com/2026/06/12/spacex-ipo-live-updates-on-everything-you-need-to-know/)
- **Chinese cybercrime operation that used AI to scam ‘hundreds of thousands of victims’ sued by Google** — [techcrunch_ai](https://techcrunch.com/2026/06/12/chinese-cybercrime-operation-that-used-ai-to-scam-hundreds-of-thousands-of-victims-sued-by-google/)
- **SpaceX, Anthropic, and OpenAI’s hot IPO summer** — [techcrunch_ai](https://techcrunch.com/video/spacex-anthropic-and-openais-hot-ipo-summer/)
- **It’s hot IPO summer, and the MANGOS are ripe** — [techcrunch_ai](https://techcrunch.com/podcast/its-hot-ipo-summer-and-the-mangos-are-ripe/)
- **Siri is good now??** — [theverge_ai](https://www.theverge.com/podcast/949079/siri-ai-good-vergecast)
- **Elon Musk is the world&#8217;s first trillionaire** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/948409/elon-musk-trillionaire-spacex-ipo)
- **SpaceX’s massive IPO: all the latest news** — [theverge_ai](https://www.theverge.com/business/948996/spacex-ipo-elon-musk)
- **Jeff Bezos’ AI startup aims to build an ‘artificial general engineer’** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/949005/jeff-bezos-prometheus-artificial-general-engineer)
- **The Download: “reprogramming” aging, and the hidden sense of interoception** — [mit_tech_review](https://www.technologyreview.com/2026/06/12/1138899/the-download-reprogramming-reverse-aging-interoception/)
- **You do your own time** — [mit_tech_review](https://www.technologyreview.com/2026/06/12/1138518/you-do-your-own-time-fiction/)
- **Siri won’t be your AI girlfriend** — [theverge_ai](https://www.theverge.com/tech/948890/siri-wont-be-your-ai-girlfriend)
- **Why “reprogramming” is the buzziest approach to reversing aging right now** — [mit_tech_review](https://www.technologyreview.com/2026/06/12/1138829/reprogramming-buzziest-approach-reversing-aging-right-now/)
- **Inside interoception: The hidden sense of how you feel inside** — [mit_tech_review](https://www.technologyreview.com/2026/06/12/1138833/inside-interoception-brain-body/)
- **desktop-hermes/hermes-agent-desktop** — [github](https://github.com/desktop-hermes/hermes-agent-desktop)
- **superagents-lab/xcode27-skills** — [github](https://github.com/superagents-lab/xcode27-skills)
- **Meta’s months-old AI unit is a soul-crushing gulag, say the engineers stuck inside it** — [techcrunch_ai](https://techcrunch.com/2026/06/12/metas-months-old-ai-unit-is-a-soul-crushing-gulag-say-the-engineers-stuck-inside-it/)
- **Mistral is rumored to be raising €3B at €20B valuation** — [techcrunch_ai](https://techcrunch.com/2026/06/12/mistral-is-rumored-to-be-raising-e3b-at-e20-valuation/)
- **Cheaper, faster, and culturally aware, Avataar’s video AI is built for India’s scale** — [techcrunch_ai](https://techcrunch.com/2026/06/11/cheaper-faster-and-culturally-aware-avataars-video-ai-is-built-for-indias-scale/)
- **Theker just raised $85M to build the factory robot that doesn’t specialize in anything** — [techcrunch_ai](https://techcrunch.com/2026/06/11/theker-just-raised-85m-to-build-the-factory-robot-that-doesnt-specialize-in-anything/)
- **Jeff Bezos’s Prometheus raises $12B to build an ‘artificial general engineer’ for the physical world** — [techcrunch_ai](https://techcrunch.com/2026/06/11/jeff-bezoss-prometheus-raises-12b-to-build-an-artificial-general-engineer-for-the-physical-world/)
- **bozhouDev/xhs-article-to-images** — [github](https://github.com/bozhouDev/xhs-article-to-images)
- **kanna12580/kk-knowledge-agent** — [github](https://github.com/kanna12580/kk-knowledge-agent)
- **DanMcInerney/architect-loop** — [github](https://github.com/DanMcInerney/architect-loop)
- **taisly/agent** — [github](https://github.com/taisly/agent)
- **DietrichGebert/ponytail** — [github](https://github.com/DietrichGebert/ponytail)
- **RainyMarks/DeepX** — [github](https://github.com/RainyMarks/DeepX)
- **TwoSevenOneT/EDRChoker** — [github](https://github.com/TwoSevenOneT/EDRChoker)
- **nelsonwerd/idea-to-ship-skills** — [github](https://github.com/nelsonwerd/idea-to-ship-skills)
- **Nanako0129/TokenBar** — [github](https://github.com/Nanako0129/TokenBar)
- **eadmin2/jarvis_ai** — [github](https://github.com/eadmin2/jarvis_ai)
- **thu-nmrc/openloop** — [github](https://github.com/thu-nmrc/openloop)
- **serenakeyitan/awesome-agent-loops** — [github](https://github.com/serenakeyitan/awesome-agent-loops)
- **cobusgreyling/loop-engineering** — [github](https://github.com/cobusgreyling/loop-engineering)
- **orange2ai/orange-line-illustration** — [github](https://github.com/orange2ai/orange-line-illustration)
- **alchaincyf/fanbox** — [github](https://github.com/alchaincyf/fanbox)
- **神了，世界杯第一天真按千问剧本踢了** — [qbitai](https://www.qbitai.com/2026/06/435321.html)
- **千里收购了一家毫米波雷达公司** — [qbitai](https://www.qbitai.com/2026/06/435196.html)
- **耐心资本护航创新，2026SuperLink开启创投价值共生新时代** — [qbitai](https://www.qbitai.com/2026/06/435192.html)
- **Anthropic老大的唯一 -1，就是AI股神的未婚妻** — [qbitai](https://www.qbitai.com/2026/06/433717.html)
- **2026奇点智能产品大会首批嘉宾官宣：在 AI 的“可交付的时代”，看一线专家如何拆解真实落地闭环！** — [qbitai](https://www.qbitai.com/2026/06/435105.html)
- **“智能体最后的考试”，Fable 5竟然不敌GPT 5.5** — [qbitai](https://www.qbitai.com/2026/06/434774.html)
- **BEV 杀入具身智能：跨维把机器人数据带上 Scaling 快车道** — [qbitai](https://www.qbitai.com/2026/06/434761.html)
- **氪星晚报｜SpaceX确定发行价，募资750亿美元创史上最大IPO；OpenAI CEO奥特曼推迟访韩计划；中央网信办举报中心开设“涉AI应用乱象举报专区”** — [36kr](https://36kr.com/p/3849942472512769?f=rss)
- **川润股份：孙公司签署液冷系统关键零部件产业化建设项目投资协议** — [36kr](https://36kr.com/newsflashes/3850142164784134?f=rss)
- **汇丰策略师Kettner：股市无需催化剂即可持续上涨** — [36kr](https://36kr.com/newsflashes/3850114468959235?f=rss)
- **澳大利亚AI云服务商Sharon AI与英伟达达成六年合作** — [36kr](https://36kr.com/newsflashes/3850102005028103?f=rss)
- **顶流偶像“空空”匿名作序的《浮生别院》，究竟有何魔力？** — [36kr](https://36kr.com/p/3849664394204419?f=rss)
- **36氪研究院 | 2026年中国工业用品制造与流通报告** — [36kr](https://36kr.com/p/3846798967818752?f=rss)
- **36氪首发 | 前瓦锡兰老兵创业，为船舶装上中国“心脏”，半年超 5000万订单** — [36kr](https://36kr.com/p/3849520020231432?f=rss)
- **热门中概股美股盘前涨跌不一，理想汽车涨超5%** — [36kr](https://36kr.com/newsflashes/3850185722664196?f=rss)
- **美股大型科技股盘前普涨，谷歌涨超1%** — [36kr](https://36kr.com/newsflashes/3850184110101509?f=rss)
- **高凯技术科创板IPO定于6月22日上会** — [36kr](https://36kr.com/newsflashes/3850096818459912?f=rss)
- **SpaceX美国IPO首日开盘报150美元** — [36kr](https://36kr.com/newsflashes/3850365941715971?f=rss)
- **SpaceX登陆纳斯达克** — [36kr](https://36kr.com/newsflashes/3850249144259846?f=rss)
- **映恩生物IPO审核状态变更为已受理** — [36kr](https://36kr.com/newsflashes/3850165413467398?f=rss)
- **长鑫科技集团股份有限公司IPO审核状态变更为注册生效** — [36kr](https://36kr.com/newsflashes/3850149434938631?f=rss)
- **广东真健康医疗科技开发股份有限公司港股IPO通过聆讯** — [36kr](https://36kr.com/newsflashes/3850142764406017?f=rss)
- **天博智能沪市主板IPO获上市委会议通过** — [36kr](https://36kr.com/newsflashes/3850092683236616?f=rss)