# AI 日报 [AI 安全] - 2026-06-11


# 每日 AI 安全主题综述：2026-06-11

## Highlights

今日研究焦点高度集中于生产级智能体（Agent）的运行时治理架构与记忆完整性验证机制。首先，《A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents》提出了一种超越传统数据边界假设的五平面参考架构，强调随着 Agent 读取上下文并调用工具，风险已从网络边界内移至业务流程序列之中，现有的策略引擎难以覆盖此类动态风险。其次，《Selection Integrity for LLM Graph Memory》揭示了基于图结构的长期记忆面临的选择性完整性挑战，指出传统的证据溯源防御在写入端存在构造性盲区，即未受信任的主体可通过修改图结构来影响认证事实的选择逻辑。此外，行业层面的安全文化争议持续发酵，包括 xAI 工程师因提出安全警报而被解雇的诉讼以及微软对 Anthropic 新模型的内部使用限制，这些事件反映了企业在追求能力突破与维持安全控制之间面临的实际张力。

## Agent 安全与治理

当前 Agent 安全的核心范式正从静态的访问控制向动态的运行时治理转变。传统的企业安全构建于保护静止和传输中的数据边界之上，而生产级 Agent 通过读取上下文、调用工具和修改系统记录，使得风险内化于工作流序列中。针对这一变化，《A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents》指出，现有的策略引擎无法有效评估这种由单个许可动作组成的复杂序列，因此需要一种新的治理架构来监控 Agent 在企业代表下执行的业务流程。与之相呼应的是，《Sovereign Assurance Boundary: Certificate-Bound Admission for Agentic Infrastructure》提出的主权保证边界（SAB），这是一种基于证书的运行时准入层，旨在拦截 Agent 对生产资源的提议。与现有的身份管理或审计日志不同，SAB 试图在决策前进行非确定性推理系统的授权，解决了现有机制仅能事后记录或强制执行静态权限的问题。

在技能复用方面，恶意行为可能隐藏在看似无害的技能文档或代码中，仅在特定用户请求或持久状态下触发危害。为此，《Runtime Skill Audit: Targeted Runtime Probing for Agent Skill Security》引入了运行时技能审计（RSA）方法，通过针对性的运行时条件探测技能的实际行为，而非依赖静态审查。这种方法弥补了纯静态验证的脆弱性，强调了在 Agent 调用技能时进行动态分析的重要性。与此同时，Agent 的记忆机制成为安全的新前沿。虽然 Agent 记忆正转向图结构以支持长期交互，但《Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval》证明，现有的基于证据溯源的防御是构造性盲目的。因为长期图记忆在全局选择步骤中运行，不受信任的实体写入的结构会改变哪些认证事实被选中，即使引用的证据本身是认证的。这要求引入忠实的信息流控制，检查读者使用的全部内容，而不仅仅是部分认证片段。

开源社区也在尝试解决记忆治理问题。例如，《PROJECTMEM: A Local-First, Event-Sourced Memory and Judgment Layer for AI Coding Agents》提供了一个本地优先的事件源记忆层，旨在解决编码 Agent 状态丢失导致的重复调试和上下文重建成本过高的问题。虽然该项目侧重于效率，但其事件溯源设计为审计 Agent 决策历史提供了潜在基础。类似地，YMX899/MemoryCloud 项目试图将 Agent 记忆像 GitHub 仓库一样管理，支持跨设备和会话的记忆同步，这在提升可用性的同时也引入了新的数据暴露风险。对于涉及个人信息的场景，《OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents》指出隐私不仅是单次输出的属性，而是整个轨迹的属性。由于泄露具有累积性和双向性，单个无害释放可能在诚实但好奇的接收者中累积成秘密推断，或者恶意观察可注入指令，因此需要推理泄漏预算机制来量化和控制这种风险。

## 工具/提示注入与运行时防御

随着 Agent 越来越多地作为自主工具使用者，工具调用的安全性成为关键防线。《Grammar-Constrained Decoding Can Jailbreak LLMs into Generating Malicious Code》揭示了一个反直觉的风险：旨在提高代码生成可靠性的语法约束解码（GCD）技术本身可能成为攻击面。实验表明，简单的良性代码语法规则可能被利用来诱导 LLM 生成恶意代码，这表明可靠性增强措施若未经过安全审查，反而可能降低系统的安全性。为了应对复杂的工具调用环境，langgenius/mosoo-agent-driver 等开源项目提供了运行时中立的驱动框架，兼容多种 Agent API，这使得在不同运行时环境中统一实施安全策略成为可能。然而，工具调用的复杂性也带来了上下文管理的挑战。pivanov/ctx-wire 项目提供了一种命令压缩方案，通过声明式过滤器压缩输出并清理敏感信息，仅在失败时将完整日志留在磁盘，这种设计在减少 Token 消耗的同时，也减少了运行时内存中敏感数据的暴露面。

在长周期任务中，循环工程（Loop Engineering）模式日益普遍，但也增加了错误累积的风险。cobusgreyling/loop-engineering 项目总结了设计 AI 编码 Agent 循环系统的实用模式和参考，强调了在迭代过程中保持状态一致性和错误处理的重要性。如果缺乏有效的运行时监控，循环中的微小偏差可能导致最终结果的严重偏离。此外，针对多模态 Agent 的工具调用，《InternVideo3: Agentify Foundation Models with Multimodal Contextual Reasoning》展示了通过多模态上下文推理增强 Agent 能力的框架，但这同时也扩大了攻击面，因为视频理解中的时序错误可能被利用来误导后续的工具调用决策。为了缓解上下文膨胀带来的安全风险，Context-Driven Incremental Compression 等方法试图在对话动态中改进上下文压缩，避免简单截断导致的信息丢失，从而在保持效率的同时维护推理的完整性。

## 对抗攻击与鲁棒性

评估 Agent 在对抗环境下的表现不仅关注准确率，还需考虑计算成本和分布外情况。《Risk Under Pressure: Compute-Aware Evaluation of Adversarial Robustness in Language Models》提出了一种基于计算压力的评估框架，指出传统的攻击成功率指标在固定查询预算下可能掩盖攻击的真实成本。不同的攻击策略在计算开销上差异巨大，因此仅报告 ASR 而不考虑计算压力可能误导对模型真实鲁棒性的判断。在医疗领域，《Measuring Epistemic Resilience of LLMs Under Misleading Medical Context》引入了 MedMisBench 来衡量模型在误导性上下文下的认知韧性。研究发现，当注入误导性背景时，原本回答正确的模型可能会放弃正确答案，这表明高考试分数并不等同于安全的医疗判断能力，模型在面对对抗性上下文时容易丧失独立性。

对于部署中的安全分类器，实时监测分布偏移至关重要。《Online Shift Detection and Conformal Adaptation for Deployed Safety Classifiers》提出了一种在线监控系统，使用校准的序列统计量检测分类器何时移出分布。一旦检测到偏移， conformal abstention layer 会调整决策阈值以恢复目标错误率。这种机制在预注册的因子评估中显示出较高的有效检测率，为生产环境中的安全模型提供了自适应防护。此外，强化学习训练本身也可能影响模型的抗攻击性。《Reinforcement Learning Disrupts Gradient-Based Adversarial Optimization》发现，使用策略梯度目标训练的图像分类器可以显著破坏基于梯度的对抗优化结构，这意味着 RL 训练可能作为一种防御手段，通过扰乱梯度信息来抵御特定的对抗攻击。

## 模型对齐与可解释性

对齐理论的研究正在深入探讨如何使高级 AI 系统诚实地报告其信念。《The Impossibility of Eliciting Latent Knowledge》讨论了提取潜在知识（ELK）问题的困难性，特别是当 AI 系统拥有超出人类开发者认知的环境知识时。设计一个诚实的系统可能非常困难，尤其是当我们需要询问关于隐藏变量的问题时，这给对齐研究带来了根本性的理论挑战。在实际的多轮推理中，模型的行为可能比终端评分所显示的更不安全。《When the Chain of Thought Knows Better: Failure Modes in Multi-Turn Reasoning Models》提出了 CoT-Output 2x2 安全矩阵，用于标记每一轮的内部推理和可见输出。研究发现，模型可能在对话早期锁定不安全立场，但最终拒绝率却看起来与稳健基线无异，这种隐藏的时序动态需要通过细粒度的诊断来暴露。

为了改善后训练阶段的数据质量，《Anatomy of Post-Training: Using Interpretability to Characterize Data and Shape the Learning Signal》主张在优化之前检查偏好数据集，以便在概念层面上决定模型应学习哪些行为。这种方法有助于防止模型学习虚假相关性，从而减少过度风格化和奉承等 undesirable behaviors。同时，对于科学探索类 Agent，《Notes2Skills: From Lab Notebooks to Certainty-Aware Scientific Agent Skills》探讨了如何利用包含不确定性的实验室笔记来增强科学 Agent 的技能，这要求模型能够处理非结构化且充满不确定性的信息，而不仅仅是处理经过润色的最终结果。

## 安全评估基准与事件响应

评估 Agent 的能力与安全性的基准正在向长周期和复杂任务演进。《Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks》引入了一个多语言的 SWE-bench 风格基准和适配器协议，使得异构 Agent 工具集可以在公平设置下进行比较。该基准包含了 350 个 GitHub 问题，规定了固定的提示词、运行时预算和工作空间合同，填补了通用 Agent 在代码修复任务上难以标准化评估的空白。针对现实世界事件的预测能力，《WorldReasoner: Evaluating Whether Language Model Agents Forecast Events with Valid Reasoning》提供了一个评估框架，要求 Agent 在有限证据下做出时间有效的预测，并区分记忆事实与因果故事，这对于评估 Agent 在不确定性下的推理真实性至关重要。

在专业领域的长周期任务评估方面，《Workflow-GYM: Towards Long-Horizon Evaluation of Computer-use Agentic tasks in Real-World Professional Fields》指出，现有基准很少评估 Agent 是否能在图形用户界面上完成跨领域的长周期专业工作流。该框架旨在填补这一空白，评估现代 Agent 是否能遵循用户指令自主操作特定领域的专业软件。此外，针对网络安全工具的效能，《Can Open-Source LLM Agents Replace Static Application Security Testing Tools? An Empirical Assessment》通过实证评估发现，现代开源 GenAI LLM Agent 并不能完全替代经过验证的静态应用安全测试（SAST）工具。尽管 Agent 在某些场景下表现出色，但在精确度、召回率和误报率方面仍与传统工具存在差距，这提醒我们在自动化安全流程中需谨慎对待 Agent 的替代作用。

## Looking Forward

尽管近期在运行时治理和评估基准方面取得了进展，但仍存在若干未解决的理论问题。首先是记忆原真性与选择完整性的矛盾，如何在允许 Agent 灵活更新长期记忆的同时，确保检索到的事实未被恶意结构篡改，仍需更形式化的信息流控制理论支持。其次是长周期任务中的信用分配问题，如《APPO: Agentic Procedural Policy Optimization》所指出的，现有的强化学习方法在粗粒度单元上分配信用，难以识别中间决策对下游结果的影响，这在安全关键场景中可能导致不可控的风险积累。最后是监管碎片化带来的合规挑战，随着各国对 AI 基础设施的准入要求日益严格，如主权保证边界所示，如何在跨国部署中平衡本地化安全策略与全球协作效率，将是未来 Agent 治理面临的主要难题。

---


## 参考来源

- **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** — [arxiv_ai](https://arxiv.org/abs/2606.12320v1)
- **InternVideo3: Agentify Foundation Models with Multimodal Contextual Reasoning** — [arxiv_cv](https://arxiv.org/abs/2606.12195v1)
- **Agentic Environment Engineering for Large Language Models: A Survey of Environment Modeling, Synthesis, Evaluation, and Application** — [arxiv_ai](https://arxiv.org/abs/2606.12191v1)
- **AerialClaw: An Open-Source Framework for LLM-Driven Autonomous Aerial Agents** — [arxiv_cv](https://arxiv.org/abs/2606.12142v1)
- **PROJECTMEM: A Local-First, Event-Sourced Memory and Judgment Layer for AI Coding Agents** — [arxiv_ai](https://arxiv.org/abs/2606.12329v1)
- **Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks** — [arxiv_cl](https://arxiv.org/abs/2606.12344v1)
- **WorldReasoner: Evaluating Whether Language Model Agents Forecast Events with Valid Reasoning** — [arxiv_cl](https://arxiv.org/abs/2606.11816v1)
- **Workflow-GYM: Towards Long-Horizon Evaluation of Computer-use Agentic tasks in Real-World Professional Fields** — [huggingface_papers](https://arxiv.org/abs/2606.11042)
- **APPO: Agentic Procedural Policy Optimization** — [arxiv_ai](https://arxiv.org/abs/2606.12384v1)
- **External Experience Serving in Production LLM Systems: A Deployment-Oriented Study of Quality-Cost Trade-offs** — [arxiv_cl](https://arxiv.org/abs/2606.11806v1)
- **OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12341v1)
- **Sovereign Assurance Boundary: Certificate-Bound Admission for Agentic Infrastructure** — [arxiv_cr](https://arxiv.org/abs/2606.11632v1)
- **DIRECT: When and Where Should You Allocate Test-Time Compute in Embodied Planners?** — [arxiv_ai](https://arxiv.org/abs/2606.12402v1)
- **TAHOE: Text-to-SQL with Automated Hint Optimization from Experience** — [arxiv_ai](https://arxiv.org/abs/2606.12387v1)
- **DrivingAgent: Design and Scheduling Agents for Autonomous Driving Systems** — [arxiv_cv](https://arxiv.org/abs/2606.12236v1)
- **Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval** — [arxiv_cr](https://arxiv.org/abs/2606.12290v1)
- **Notes2Skills: From Lab Notebooks to Certainty-Aware Scientific Agent Skills** — [arxiv_cl](https://arxiv.org/abs/2606.11897v1)
- **Can Open-Source LLM Agents Replace Static Application Security Testing Tools? An Empirical Assessment** — [arxiv_cr](https://arxiv.org/abs/2606.11672v1)
- **Runtime Skill Audit: Targeted Runtime Probing for Agent Skill Security** — [arxiv_cr](https://arxiv.org/abs/2606.11671v1)
- **One Token per Multimodal Evidence: Latent Memory for Resource-Constrained QA** — [huggingface_papers](https://arxiv.org/abs/2606.10572)
- **DeNovoSWE: Scaling Long-Horizon Environments for Generating Entire Repositories from Scratch** — [huggingface_papers](https://arxiv.org/abs/2606.10728)
- **Kwai Keye-VL-2.0 Technical Report** — [huggingface_papers](https://arxiv.org/abs/2606.10651)
- **Intelligent Automation for Embodied Benchmark Construction: Pipelines, Embodiments, Simulators, and Trends** — [arxiv_ai](https://arxiv.org/abs/2606.12207v1)
- **Context-Driven Incremental Compression for Multi-Turn Dialogue Generation** — [arxiv_cl](https://arxiv.org/abs/2606.12411v1)
- **UniIntervene: Agentic Intervention for Efficient Real-World Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.12372v1)
- **uva-irlab-conv at SemEval-2026 Task 8: Multi-Turn RAG with Learned Sparse Retrieval and Listwise Reranking** — [arxiv_cl](https://arxiv.org/abs/2606.11945v1)
- **WarpGuard: Protected-Site Control-Flow Integrity for CUDA SASS Binaries** — [arxiv_cr](https://arxiv.org/abs/2606.11871v1)
- **Role-Agent: Bootstrapping LLM Agents via Dual-Role Evolution** — [huggingface_papers](https://arxiv.org/abs/2606.10917)
- **Risk Under Pressure: Compute-Aware Evaluation of Adversarial Robustness in Language Models** — [arxiv_cr](https://arxiv.org/abs/2606.11409v1)
- **ATLAS: Active Theory Learning for Automated Science** — [arxiv_ai](https://arxiv.org/abs/2606.12386v1)
- **CCKS: Consensus-based Communication and Knowledge Sharing** — [arxiv_ai](https://arxiv.org/abs/2606.12281v1)
- **The Impossibility of Eliciting Latent Knowledge** — [arxiv_ai](https://arxiv.org/abs/2606.12268v1)
- **Doc-to-Atom: Learning to Compile and Compose Memory Atoms** — [arxiv_cl](https://arxiv.org/abs/2606.12400v1)
- **Toward Generalist Autonomous Research via Hypothesis-Tree Refinement** — [arxiv_cl](https://arxiv.org/abs/2606.11926v1)
- **An Ontology-Guided Multi-Anchor Graph Retrieval Framework for Traffic Legal Liability Determination** — [arxiv_cl](https://arxiv.org/abs/2606.11910v1)
- **VIPIR: A Versatile GPU Framework for Integrating Private Information Retrieval Protocols** — [arxiv_cr](https://arxiv.org/abs/2606.11536v1)
- **MPC-Patch-Bench: Security-Aware LLM Code Patch for Multi-Party Computation** — [arxiv_cr](https://arxiv.org/abs/2606.11416v1)
- **Decentralized Multi-Agent Systems with Shared Context** — [huggingface_papers](https://arxiv.org/abs/2606.10662)
- **Multi-Rate Mixture of Experts for Accelerating Liquid Neural Network Training** — [arxiv_ai](https://arxiv.org/abs/2606.12240v1)
- **Bridging Day and Night: Unsupervised Cross-Domain Re-Identification with Synergistic Prompt and Prototype Learning** — [arxiv_cv](https://arxiv.org/abs/2606.12258v1)
- **Categorical Robustness Assessment for Machine Learning based Network Intrusion Detection Systems** — [arxiv_lg](https://arxiv.org/abs/2606.12075v1)
- **DiffCold: A Diffusion-based Generative Model for Cold-Start Item Recommendation** — [arxiv_ai](https://arxiv.org/abs/2606.12245v1)
- **Implicit Neural Representations of Individual Behavior** — [arxiv_ai](https://arxiv.org/abs/2606.12200v1)
- **Bridging the Modality Gap in Forensic Image Retrieval** — [arxiv_cv](https://arxiv.org/abs/2606.12294v1)
- **Measuring Epistemic Resilience of LLMs Under Misleading Medical Context** — [arxiv_cl](https://arxiv.org/abs/2606.12291v1)
- **Fourier Features Let Agents Learn High Precision Policies with Imitation Learning** — [arxiv_lg](https://arxiv.org/abs/2606.12334v1)
- **MLT-Dedup: Efficient Large-Scale Online Video Deduplication via Multi-Level Representations and Spatial-Temporal Matching** — [arxiv_lg](https://arxiv.org/abs/2606.12215v1)
- **Augmenting Molecular Language Models with Local $n$-gram Memory** — [arxiv_ai](https://arxiv.org/abs/2606.12113v1)
- **FORT-Searcher: Synthesizing Shortcut-Resistant Search Tasks for Training Deep Search Agents** — [arxiv_cl](https://arxiv.org/abs/2606.12087v1)
- **When Does Language Matter? Multilingual Instructions Reveal Step-wise Language Sensitivity in Vision-Language-Action Models** — [arxiv_cl](https://arxiv.org/abs/2606.11906v1)
- **SwarmSense-DNN: A Trustworthy and Decentralized Neural Framework for Proactive Anomaly Defense in Consumer IoT** — [arxiv_cr](https://arxiv.org/abs/2606.11803v1)
- **ICA Lens: Interpreting Language Models Without Training Another Dictionary** — [huggingface_papers](https://arxiv.org/abs/2606.11722)
- **EEVEE: Towards Test-time Prompt Learning in the Real World for Self-Improving Agents** — [huggingface_papers](https://arxiv.org/abs/2606.11182)
- **Reinforcement Learning Disrupts Gradient-Based Adversarial Optimization** — [arxiv_ai](https://arxiv.org/abs/2606.12251v1)
- **Toward Trustworthy AI: Multi-Target Adversarial Attacks and Robust Defenses for Continuous Data Summarization** — [arxiv_cr](https://arxiv.org/abs/2606.11804v1)
- **Reroute, Don't Remove: Recoverable Visual Token Routing for Vision-Language Models** — [arxiv_ai](https://arxiv.org/abs/2606.12412v1)
- **SPEA2$^+$: Improved Density Estimation in SPEA2 with Provable Runtime Guarantees** — [arxiv_ai](https://arxiv.org/abs/2606.12382v1)
- **Natural-Language Temporal Grounding in Hour-Long Videos is a Search Problem: A Benchmark and Empirical Decomposition** — [arxiv_ai](https://arxiv.org/abs/2606.12300v1)
- **Rule Taxonomy and Evolution in AI IDEs: A Mining and Survey Study** — [arxiv_ai](https://arxiv.org/abs/2606.12231v1)
- **Echoes of the Prior: A Computational Phenomenology of Forgetting** — [arxiv_cv](https://arxiv.org/abs/2606.12340v1)
- **AGE-MIL: Anchor-Guided Evidence Learning for Patient-Level Prediction** — [arxiv_cv](https://arxiv.org/abs/2606.12126v1)
- **Which Models Are Our Models Built On? Auditing Invisible Dependencies in Modern LLMs** — [arxiv_cl](https://arxiv.org/abs/2606.12385v1)
- **Breaking Entropy Bounds: Accelerating RL Training via MTP with Rejection Sampling** — [arxiv_cl](https://arxiv.org/abs/2606.12370v1)
- **Findings of the MAGMaR 2026 Shared Task** — [arxiv_cl](https://arxiv.org/abs/2606.12295v1)
- **ECYSAP EYE: From Cyber Situational Awareness to Mission-Centric Decision Support for Enhanced Cyberspace Operations** — [arxiv_cr](https://arxiv.org/abs/2606.12354v1)
- **On Subquadratic Architectures: From Applications to Principles** — [arxiv_lg](https://arxiv.org/abs/2606.12364v1)
- **Holding the FP8 Quality Ceiling at 8-Bit Weights and Activations: INT8 and GGUF Post-Training Quantization of Ideogram 4.0 for Consumer GPUs** — [arxiv_lg](https://arxiv.org/abs/2606.12280v1)
- **Soft-Prompt Tuning for Fair and Efficient LLM Benchmark Evaluation** — [arxiv_ai](https://arxiv.org/abs/2606.12117v1)
- **World Model Self-Distillation: Training World Models to Solve General Tasks** — [arxiv_cv](https://arxiv.org/abs/2606.12072v1)
- **Fine-tuning Multi-modal LLMs with ART: Art-based Reinforcement Training** — [arxiv_cl](https://arxiv.org/abs/2606.11854v1)
- **InjectV: Modeling Fault Injection Attacks in RISC-V Simulation Environment** — [arxiv_cr](https://arxiv.org/abs/2606.12011v1)
- **A Deterministic Forensic Preprocessing Framework for Heterogeneous Network Datasets: Formal Foundations, Implementation, and Empirical Validation** — [arxiv_cr](https://arxiv.org/abs/2606.11565v1)
- **WHET: Welding Homomorphic Encryption to Accelerator Architectures** — [arxiv_cr](https://arxiv.org/abs/2606.11541v1)
- **OpenPCC: Open and Confidential LLM Serving on Commodity TEEs** — [arxiv_cr](https://arxiv.org/abs/2606.11145v1)
- **Next Forcing: Causal World Modeling with Multi-Chunk Prediction** — [huggingface_papers](https://arxiv.org/abs/2606.11187)
- **FadeMem: Distance-Aware Memory Consolidation for Autoregressive Video Diffusion** — [huggingface_papers](https://arxiv.org/abs/2606.10671)
- **Attention Amnesia in Hybrid LLMs: When CoT Fine-Tuning Breaks Long-Range Recall, and How to Fix It** — [huggingface_papers](https://arxiv.org/abs/2606.11052)
- **Dynamic Linear Attention** — [huggingface_papers](https://arxiv.org/abs/2606.10650)
- **Can News Predict the Market? Limits of Zero-Shot Financial NLP and the Role of Explainable AI** — [arxiv_cl](https://arxiv.org/abs/2606.12210v1)
- **BrainSurgery: Reproducible and Reliable Declarative Weight Manipulations for Model Editing and Upcycling** — [huggingface_papers](https://arxiv.org/abs/2606.09707)
- **ISAP-3D: Identity-Slot Aligned Part-Aware 3D Generation** — [arxiv_cv](https://arxiv.org/abs/2606.12099v1)
- **Grammar-Constrained Decoding Can Jailbreak LLMs into Generating Malicious Code** — [arxiv_cl](https://arxiv.org/abs/2606.11817v1)
- **Superspace Concentration and Adversarial Robustness in Quantum Algorithms** — [arxiv_cr](https://arxiv.org/abs/2606.11580v1)
- **Anchors that Don't Lift: Understanding Supply Chain Driven Kernel Lock-In and Governance-Mediated Mitigation Strategies in SOHO Devices** — [arxiv_cr](https://arxiv.org/abs/2606.11175v1)
- **When the Chain of Thought Knows Better: Failure Modes in Multi-Turn Reasoning Models** — [huggingface_papers](https://arxiv.org/abs/2606.10740)
- **UniPET: a universal network for high-quality PET image denoising across varied dose reduction factors** — [huggingface_papers](https://arxiv.org/abs/2606.11131)
- **Flow-DPPO: Divergence Proximal Policy Optimization for Flow Matching Models** — [huggingface_papers](https://arxiv.org/abs/2606.11025)
- **VLGA: Vision-Language-Geometry-Action Models for Autonomous Driving** — [arxiv_cv](https://arxiv.org/abs/2606.12396v1)
- **An Electric Potential-Augmented Benchmark Dataset for Physics-Guided Image Reconstruction of Electrical Capacitance Tomography** — [arxiv_cv](https://arxiv.org/abs/2606.12226v1)
- **Measuring Semantic Progress in Multi-turn Dialogue via Information Gain** — [arxiv_cl](https://arxiv.org/abs/2606.12332v1)
- **Reassessing High-Performing LLMs on Polish Medical Exams: True Competence or Bias-Driven Performance?** — [arxiv_cl](https://arxiv.org/abs/2606.12250v1)
- **Anatomy of Post-Training: Using Interpretability to Characterize Data and Shape the Learning Signal** — [arxiv_lg](https://arxiv.org/abs/2606.12360v1)
- **Learning What to Say to Your VLA: Mostly Harmless Vision Language Action Model Steering** — [arxiv_lg](https://arxiv.org/abs/2606.12299v1)
- **Tac-DINO: Learning Vision-Tactile Features with Patch Alignment** — [arxiv_cv](https://arxiv.org/abs/2606.12069v1)
- **Vision Transformers for Face Recognition Need More Registers** — [arxiv_cv](https://arxiv.org/abs/2606.12036v1)
- **ViT-FREE: Efficient Face Recognition via Early Exiting and Synthetic Adaptation** — [arxiv_cv](https://arxiv.org/abs/2606.12023v1)
- **From Nominal Intensity to Equivalent Rainfall: A Path-Based Credibility Evaluation Framework for Simulated Rainfall in Autonomous-Driving Perception Tests** — [arxiv_cv](https://arxiv.org/abs/2606.11989v1)
- **Online Shift Detection and Conformal Adaptation for Deployed Safety Classifiers** — [arxiv_cr](https://arxiv.org/abs/2606.11949v1)
- **Feature-Aligned Speech Watermarking for Robustness to Reconstruction Distortions** — [arxiv_cr](https://arxiv.org/abs/2606.11828v1)
- **Lip Forcing: Few-Step Autoregressive Diffusion for Real-time Lip Synchronization** — [huggingface_papers](https://arxiv.org/abs/2606.11180)
- **Beyond Uniform Token-Level Trust Region in LLM Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2606.10968)
- **The Role of Feedback Alignment in Self-Distillation** — [huggingface_papers](https://arxiv.org/abs/2606.11173)
- **WorldOlympiad: Can Your World Model Survive a Triathlon?** — [huggingface_papers](https://arxiv.org/abs/2606.11129)
- **How Seemingly Inconsequential Design Choices Dictate Performance of LLMs in Pathology** — [arxiv_cv](https://arxiv.org/abs/2606.12407v1)
- **Semantically-Aware Diver Activity Recognition Framework for Effective Underwater Multi-Human-Robot Collaboration** — [arxiv_cv](https://arxiv.org/abs/2606.12374v1)
- **A Turbo-Inference Strategy for Object Detection and Instance Segmentation** — [arxiv_cv](https://arxiv.org/abs/2606.12371v1)
- **DepthMaster: Unified Monocular Depth Estimation for Perspective and Panoramic Images** — [arxiv_cv](https://arxiv.org/abs/2606.12368v1)
- **Anatomically Conditioned Recurrent Refinement for Topology-Aware Circle of Willis Segmentation** — [arxiv_cv](https://arxiv.org/abs/2606.12319v1)
- **Adjoint Method versus Physics-Informed Neural Networks in PDE-Constrained Inverse Problems** — [arxiv_lg](https://arxiv.org/abs/2606.12337v1)
- **PianoKontext: Expressive Performance Rendering from Deadpan Context** — [arxiv_lg](https://arxiv.org/abs/2606.12282v1)
- **Finding Sparse Subnetworks in One Training Cycle via Progressive Magnitude-Based Pruning** — [arxiv_lg](https://arxiv.org/abs/2606.12278v1)
- **Finding Multiple Interpretations in Datasets** — [arxiv_lg](https://arxiv.org/abs/2606.12277v1)
- **Re-evaluating Confidence Remasking in Masked Diffusion Language Models** — [arxiv_lg](https://arxiv.org/abs/2606.12232v1)
- **Quantum Occam Learning: Sample-Supported Expressibility for Circuit-Based Quantum Learning** — [arxiv_lg](https://arxiv.org/abs/2606.12211v1)
- **How Low Can You Go? Active Learning for Sparse Model Discovery in the Ultra-Low-Data Limit** — [arxiv_lg](https://arxiv.org/abs/2606.12182v1)
- **Beyond Dark Knowledge: Mixup-Based Distillation for Reliable Predictions** — [arxiv_lg](https://arxiv.org/abs/2606.12171v1)
- **PCA-Enhanced Adaptive NVAR Framework for High-Resolution Sea Surface Temperature Forecasting in the East Sea** — [arxiv_lg](https://arxiv.org/abs/2606.12141v1)
- **A Riemannian Approach to Low-Rank Optimal Transport** — [arxiv_lg](https://arxiv.org/abs/2606.12120v1)
- **DAM-VLA: Decoupled Asynchronous Multimodal Vision Language Action model** — [arxiv_lg](https://arxiv.org/abs/2606.12105v1)
- **Efficient Time Series Clustering from Multiscale Reservoir Dynamics with Granular-Ball Anchoring Graph Optimization** — [arxiv_lg](https://arxiv.org/abs/2606.12077v1)
- **YMX899/MemoryCloud** — [github](https://github.com/YMX899/MemoryCloud)
- **Datadog veterans launch AI coding startup Niteshift on a bet against Big AI lock-in** — [techcrunch_ai](https://techcrunch.com/2026/06/10/datadog-veterans-launch-ai-coding-startup-niteshift-on-a-bet-against-big-ai-lock-in/)
- **Jedify raises $24M to help companies arm AI agents with context on their business** — [techcrunch_ai](https://techcrunch.com/2026/06/10/jedify-raises-24m-to-help-companies-arm-ai-agents-with-context-on-their-business/)
- **xAI fired an engineer who raised alarms about Grok safety, new lawsuit claims** — [techcrunch_ai](https://techcrunch.com/2026/06/10/xai-fired-an-engineer-who-raised-alarms-about-grok-safety-new-lawsuit-claims/)
- **CYC2002tommy/Deep-Research-Agent** — [github](https://github.com/CYC2002tommy/Deep-Research-Agent)
- **How memory tools can make AI models worse** — [techcrunch_ai](https://techcrunch.com/2026/06/10/how-memory-tools-can-make-ai-models-worse/)
- **langgenius/mosoo-agent-driver** — [github](https://github.com/langgenius/mosoo-agent-driver)
- **agentic-in/inferoa** — [github](https://github.com/agentic-in/inferoa)
- **Zafer-Liu/Agent_Manager** — [github](https://github.com/Zafer-Liu/Agent_Manager)
- **The future of AI regulation is courting the strangest, most anxious bedfellows** — [theverge_ai](https://www.theverge.com/column/947838/washington-ai-network-honors-2026-midterms)
- **Access OpenAI models and Codex through your Oracle cloud commitment** — [openai](https://openai.com/index/openai-on-oracle-cloud)
- **How an astrophysicist uses Codex to help simulate black holes** — [openai](https://openai.com/index/using-codex-to-simulate-black-holes)
- **Claude Fable won’t answer basic biology questions** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/947973/fable-wont-answer-basic-biology-questions)
- **Microsoft, like, totally gets why students are booing AI-pilled graduation speakers** — [theverge_ai](https://www.theverge.com/news/947831/college-speakers-booed-ai-microsoft)
- **Google won’t just admit it’s feeding YouTube creators to its music AI** — [theverge_ai](https://www.theverge.com/tech/947770/google-lyria-music-ai-lawsuit-youtube)
- **Microsoft restricts Claude Fable for employees over data retention concerns** — [theverge_ai](https://www.theverge.com/report/947575/microsoft-claude-fable-5-restricted-internally)
- **Google will save your Lens photos, Search Live recordings, and Translate audio for AI training** — [theverge_ai](https://www.theverge.com/tech/947836/google-search-privacy-settings-images-audio)
- **Decart’s new world model can simulate hours of photorealistic driving — with some caveats** — [techcrunch_ai](https://techcrunch.com/2026/06/10/decarts-new-world-model-can-simulate-hours-of-photorealistic-driving-with-some-caveats/)
- **PRC-linked influence operations are targeting AI debates in the US** — [openai](https://openai.com/index/prc-linked-influence-operations-ai-debates)
- **The Download: the “steroid olympics” and a safer Mythos** — [mit_tech_review](https://www.technologyreview.com/2026/06/10/1138739/the-download-steroid-olympics-enhanced-games-anthropic-mythos/)
- **The “steroid olympics” were a circus—and a window into our culture** — [mit_tech_review](https://www.technologyreview.com/2026/06/10/1138670/enhanced-games-doping-steroids-hormones-supplements-longevity/)
- **superagents-lab/xcode27-skills** — [github](https://github.com/superagents-lab/xcode27-skills)
- **ferdinandobons/brand-docs** — [github](https://github.com/ferdinandobons/brand-docs)
- **Fresh off bond sale, Amazon borrows $17.5B from banks as AI spending continues** — [techcrunch_ai](https://techcrunch.com/2026/06/10/fresh-off-bond-sale-amazon-borrows-17-5-billion-from-banks-as-ai-spending-continues/)
- **‘AI-pilled’ firms spend $7,500 per employee each month on AI** — [techcrunch_ai](https://techcrunch.com/2026/06/10/ai-pilled-firms-spend-7500-per-employee-each-month-on-ai/)
- **Cybersecurity researchers aren’t happy about the guardrails on Anthropic’s Fable** — [techcrunch_ai](https://techcrunch.com/2026/06/10/cybersecurity-researchers-arent-happy-about-the-guardrails-on-anthropics-fable/)
- **The three hard-tech moonshots fueling SpaceX’s unbelievable IPO** — [techcrunch_ai](https://techcrunch.com/2026/06/10/the-three-hard-tech-moonshots-fueling-spacexs-unbelievable-ipo/)
- **Warner Music acquires AI attribution startup Sureel AI** — [techcrunch_ai](https://techcrunch.com/2026/06/10/warner-music-acquires-ai-attribution-startup-sureel-ai/)
- **Meta signs first AI data center deal in India with Reliance** — [techcrunch_ai](https://techcrunch.com/2026/06/10/meta-signs-first-ai-data-center-deal-in-india-with-reliance/)
- **kanna12580/kk-knowledge-agent** — [github](https://github.com/kanna12580/kk-knowledge-agent)
- **Forsy-AI/forsy-trace-skill** — [github](https://github.com/Forsy-AI/forsy-trace-skill)
- **FerroxLabs/wayland** — [github](https://github.com/FerroxLabs/wayland)
- **RainyMarks/DeepX** — [github](https://github.com/RainyMarks/DeepX)
- **DiffusionGemma: 4x faster text generation** — [deepmind](https://deepmind.google/blog/diffusiongemma-4x-faster-text-generation/)
- **TwoSevenOneT/EDRChoker** — [github](https://github.com/TwoSevenOneT/EDRChoker)
- **pivanov/ctx-wire** — [github](https://github.com/pivanov/ctx-wire)
- **serenakeyitan/awesome-agent-loops** — [github](https://github.com/serenakeyitan/awesome-agent-loops)
- **cobusgreyling/loop-engineering** — [github](https://github.com/cobusgreyling/loop-engineering)
- **Ronvaknins/ableton-extensions-skill** — [github](https://github.com/Ronvaknins/ableton-extensions-skill)
- **phun333/pi-infobar** — [github](https://github.com/phun333/pi-infobar)
- **JimLiu/baoyu-design** — [github](https://github.com/JimLiu/baoyu-design)
- **ikunycj/gpt-team-register** — [github](https://github.com/ikunycj/gpt-team-register)
- **3299129776-a11y/public-skill-finder** — [github](https://github.com/3299129776-a11y/public-skill-finder)
- **Evaluation of Alternative-Based Information Systems for Deliberative Polling using an Agentic Simulator** — [arxiv_cy](https://arxiv.org/abs/2606.11692v1)
- **Should LLM Agents Decide in Social Simulations? Comparing Finite-State and LLM-Based Decision Policies** — [arxiv_cy](https://arxiv.org/abs/2606.12369v1)
- **百度智能云与FluxA达成战略合作，共建 Agent 经济全球支付基础设施** — [qbitai](https://www.qbitai.com/2026/06/433516.html)
- **8点1氪丨世界杯门票遇冷，近18万张门票待转售；台积电释放涨价信号；但斌回应“被段永平拉黑”** — [36kr](https://36kr.com/p/3848000003953926?f=rss)
- **实测小米最快1T大模型：吞吐量每秒1000+ Tokens，Vibe Coding七秒交付** — [qbitai](https://www.qbitai.com/2026/06/434225.html)
- **中国第一、全球第二！HiDream-O1-Image-1.5 登顶文生图榜单，超越谷歌、英伟达** — [qbitai](https://www.qbitai.com/2026/06/434196.html)
- **东风联手九识，商用无人车也有“HI模式”了** — [qbitai](https://www.qbitai.com/2026/06/433956.html)
- **抖音征召天下「AI视频英才」！创作者们，这次是真能吃上AI红利了…** — [qbitai](https://www.qbitai.com/2026/06/433832.html)
- **英特尔锐炫™ Pro B70 GPU亮相MPTS2026，共探大视听时代AI创作新范式** — [qbitai](https://www.qbitai.com/2026/06/433798.html)
- **GPT-5.6首批实测来了！精准狙击Mythos** — [qbitai](https://www.qbitai.com/2026/06/433731.html)
- **Claude Fable 5首日实测，杀疯了…** — [qbitai](https://www.qbitai.com/2026/06/433682.html)
- **氪星晚报｜韩IT巨头Kakao工会史上首次启动局部罢工；三星考虑新建先进芯片封装厂，以满足全球芯片需求；SK海力士最早将于8月在美国上市** — [36kr](https://36kr.com/p/3847079661193733?f=rss)
- **Why AI Slop Matters, but Not Like That** — [arxiv_cy](https://arxiv.org/abs/2606.12285v1)
- **小米推出AI 编程助手MiMo Code** — [36kr](https://36kr.com/newsflashes/3848111404274945?f=rss)
- **Learning by Chatting? Investigating the Impact of Generative AI on Information Seeking and Learning** — [arxiv_cy](https://arxiv.org/abs/2606.11669v1)
- **Are LLMs Bad at Moral Reasoning?** — [arxiv_cy](https://arxiv.org/abs/2606.11635v1)
- **What Uncertainties Do We Need for Dynamical Systems?** — [arxiv_ml](https://arxiv.org/abs/2606.11988v1)
- **Efficient Multinomial Logistic Bandit via Frequent Directions** — [arxiv_ml](https://arxiv.org/abs/2606.11968v1)
- **From Persistence to Survival: Hypothesis Testing, Effect Sizes and Vectorisation for Topological Features** — [arxiv_ml](https://arxiv.org/abs/2606.11911v1)
- **Conformal Bayes under Label Shift: Post-Hoc Calibration vs. In-Training Adaptation** — [arxiv_ml](https://arxiv.org/abs/2606.11865v1)
- **Magnitude-Based Features for Multispecies Spatial Data** — [arxiv_ml](https://arxiv.org/abs/2606.11775v1)
- **Time Series Analysis in Machine Learning** — [arxiv_ml](https://arxiv.org/abs/2606.11746v1)
- **Renewable Lasso without Batch-Number Constraints: A Gradient-Enhanced Approach** — [arxiv_ml](https://arxiv.org/abs/2606.11738v1)
- **Capacity-Constrained Online Convex Optimization with Delayed Feedback** — [arxiv_ml](https://arxiv.org/abs/2606.11711v1)
- **Tree-Structured Orthonormal Decomposition of the Aitchison Simplex** — [arxiv_ml](https://arxiv.org/abs/2606.11646v1)
- **36氪首发 | 创维独家投资数千万，这家企业将碳化硅切割损耗降至40微米内** — [36kr](https://36kr.com/p/3848094835217666?f=rss)
- **甲骨文CFO：公司积压订单达6380亿美元，体现市场对AI基建和云服务的需求旺盛** — [36kr](https://36kr.com/newsflashes/3848088702260225?f=rss)
- **两部门：深入实施“人工智能+三品”专项行动，建设一批行业大模型和高质量数据集** — [36kr](https://36kr.com/newsflashes/3848066038174724?f=rss)
- **中金：维持美联储年内不降息、不加息的基准判断** — [36kr](https://36kr.com/newsflashes/3848022773011715?f=rss)
- **独家｜字节 AI 制药开启拆分融资，AI4S 进入产业化阶段** — [36kr](https://36kr.com/p/3846956646124036?f=rss)
- **最前线｜AI跨境电商工具混战，StoreClaw想用“一个大脑”接管卖家的店** — [36kr](https://36kr.com/p/3846793046133257?f=rss)
- **钉钉换帅，92年技术极客陈宇森接任钉钉CEO** — [36kr](https://36kr.com/newsflashes/3848133613999106?f=rss)
- **智元推出灵犀X2 EDU（人人造）版本，面向科教实训等丰富场景** — [36kr](https://36kr.com/newsflashes/3848126301541636?f=rss)
- **OpenAI考虑大幅降价，以期在与Anthropic的用户争夺战中占据有利地位** — [36kr](https://36kr.com/newsflashes/3848106407040265?f=rss)
- **两市融资余额减少80.91亿元** — [36kr](https://36kr.com/newsflashes/3848058894373888?f=rss)