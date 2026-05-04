# AI 日报 [AI 安全] - 2026-05-04


# AI 安全与治理日报：2026 年 5 月 4 日

## Highlights

当日研究焦点集中在多模态模型的对抗鲁棒性、隐私保护下的数据投毒防御以及 Agent 系统的治理框架上。在学术突破方面，**STARE: Step-wise Temporal Alignment and Red-teaming Engine for Multi-modal Toxicity Attack** 提出了一种基于分层强化学习的多模态毒性攻击新范式，将去噪轨迹本身视为攻击面，为视觉 - 语言模型（VLM）的安全评估提供了白盒与黑盒结合的测试工具。同时，**ML-Bench&Guard: Policy-Grounded Multilingual Safety Benchmark and Guardrail for Large Language Models** 发布了首个基于政策的多语言安全基准，覆盖了 14 种语言，直接解决了现有基准依赖机器翻译导致的文化细微差异丢失问题。在产业安全方面，关于医疗 RAG 系统的匿名案例研究揭示了患者面 AI 在隐私泄露方面的潜在风险，强调了治理控制在生成式 AI 落地中的必要性。

## 对抗攻击与鲁棒性

多模态模型的安全性评估正从单一文本模态向复杂的视觉 - 文本交互场景扩展。**STARE: Step-wise Temporal Alignment and Red-teaming Engine for Multi-modal Toxicity Attack** 针对现有方法将图像生成视为黑盒的局限性，引入了一种分层强化学习框架。该框架不仅关注最终的毒性评分，更将扩散模型的去噪轨迹视为攻击面，通过高层提示编辑器与底层 T2I 微调的耦合，在直接白盒 T2I 和查询仅黑盒 VLM 设置下识别毒性语义的涌现时机。与之形成对比的是，**Jailbreaking Vision-Language Models Through the Visual Modality** 则从另一个角度探索了视觉模态的未开发攻击面，提出了四种利用视觉组件绕过安全对齐的攻击方法，包括将有害指令编码为视觉符号序列、用良性物体替换有害物体（如炸弹替换为香蕉）并提示执行有害动作等。这两项工作共同揭示了 VLM 在跨模态理解中的脆弱性，前者侧重于生成过程的时序攻击，后者侧重于语义替换的对抗样本，两者在方法论上互补，前者需要模型内部状态访问，后者仅需输入输出接口。

在数据层面的安全方面，**Defense against Poisoning Attacks under Shuffle-DP** 关注差分隐私（DP）在现实场景中的漏洞。尽管 Shuffle-DP 模型在隐私与效用之间取得了良好平衡，但现有协议假设所有用户诚实，忽略了恶意用户通过投毒攻击破坏隐私保证和分析结果的可能性。该研究针对这一假设缺陷提出了防御机制。与此同时，**Repurposing Image Diffusion Models for Adversarial Synthetic Structured Data: A Case Study of Ground Truth Drift** 展示了未修改的 Stable Diffusion U-Net 在重塑为单通道伪图像后，可用于生成对抗性合成结构化数据。该研究指出，扩散模型的归纳偏置（如空间局部性）使得特征布局成为设计变量，这为攻击者利用通用图像模型生成表格数据提供了新思路。

在物理系统的鲁棒性方面，**Scale-Aware Adversarial Analysis: A Diagnostic for Generative AI in Multiscale Complex Systems** 指出标准可解释性 AI（XAI）方法（如基于扰动的梯度显著性方法）依赖像素级扰动，会产生非物理伪影。该工作强调在超音速湍流等复杂物理系统中，机器学习架构是否内化了物理规律仍是未解之谜。此外，**Quantum Interval Bound Propagation for Certified Training of Quantum Neural Networks** 将经典机器学习中的区间边界传播（IBP）方法扩展至量子领域，旨在确保量子神经网络在对抗扰动下的预测正确性，尽管目前量子领域的认证训练努力仍然有限。这些工作共同表明，对抗攻击与鲁棒性研究正从传统的图像分类向生成过程、物理系统以及量子计算领域延伸，防御策略需从输入端防御转向对模型内部动态和物理约束的考量。

## 模型对齐与可解释性

随着大语言模型（LLM）在跨语言环境中的部署，安全对齐面临文化差异与监管合规的双重挑战。**ML-Bench&Guard: Policy-Grounded Multilingual Safety Benchmark and Guardrail for Large Language Models** 通过直接从法规构建基准，而非依赖通用风险分类和机器翻译，试图弥合这一差距。该基准覆盖 14 种语言，旨在使护栏模型能够与特定区域的监管和文化细微差别保持一致。相比之下，**Themis: Training Robust Multilingual Code Reward Models for Flexible Multi-Criteria Scoring** 则专注于代码生成的奖励模型。现有工作多依赖执行反馈，限制了后训练仅优化功能正确性。Themis 通过编译 Themis-CodeRewardBench 基准，评估了多语言、多标准代码奖励模型，强调了在代码生成中超越功能正确性，关注代码质量、安全性等多维度的重要性。

在公平性与可解释性方面，**Meritocratic Fairness in Budgeted Combinatorial Multi-armed Bandits via Shapley Values** 提出了基于 Shapley 值的功绩公平性框架，扩展了经典博弈论概念至 K-Shapley 值，以在部分反馈设置中计算臂的贡献。这与 **Fairness of Classifiers in the Presence of Constraints between Features** 形成了理论呼应，后者指出当特征间存在约束时，决策不应仅依赖受保护特征，而应依赖不包含受保护特征的“公平解释”（prime-implicant reason）。**Aitchison Embeddings for Learning Compositional Graph Representations** 则从几何角度提出基于 Aitchison 几何的图嵌入框架，将节点表示为单纯形值组合，以更好地解释节点特征与图结构的关系。

在推理与数学证明能力方面，**Evaluating the Architectural Reasoning Capabilities of LLM Provers via the Obfuscated Natural Number Game** 区分了语义模式匹配与真正的架构推理能力。该研究使用混淆的自然数游戏基准，评估模型是否仅依赖预训练数据还是能利用局部公理合成形式证明。这一评估对于未来自动化定理发现 AI 至关重要。此外，**HyCOP: Hybrid Composition Operators for Interpretable Learning of PDEs** 引入了模块化框架，通过组合简单模块（如平流、扩散）来学习参数化 PDE 解算子，而非学习单体映射，从而产生可解释的程序。这些工作共同推动了模型对齐从单纯的性能优化向可解释性、公平性和逻辑推理能力的深度转变。

## 隐私保护与联邦学习

隐私保护技术在联邦学习（FL）中的应用正面临统计异构性和遗忘需求的挑战。**FedKPer: Tackling Generalization and Personalization in Medical Federated Learning via Knowledge Personalization** 指出医疗 FL 中机构间的统计异构性导致全局模型难以泛化且易发生遗忘。该工作将泛化与个性化视为统一挑战，而非分离问题，通过知识个性化解决。与之相关的是 **EASE: Federated Multimodal Unlearning via Entanglement-Aware Anchor Closure**，该研究针对联邦多模态学习中的遗忘问题，识别出跨模态重构通道和客户端梯度子空间的纠缠阻碍了联邦遗忘。EASE 提出了锚定原则，通过切断跨模态重构通道和分离遗忘方向，实现了有效的联邦多模态对比遗忘。

在差分隐私与采样方面，**Defense against Poisoning Attacks under Shuffle-DP** 再次强调了 Shuffle-DP 中用户诚实假设的脆弱性，指出恶意用户可利用此漏洞进行投毒攻击。而 **Decentralized Proximal Stochastic Gradient Langevin Dynamics** 则提出了一种去中心化的马尔可夫链蒙特卡洛（MCMC）算法，用于在凸域约束下对对数凹概率分布进行采样。该算法通过共享的邻近正则化强制执行约束，并建立了非渐近收敛保证。此外，**Unlearning Offline Stochastic Multi-Armed Bandits** 启动了离线随机多臂老虎机（MAB）中的机器遗忘研究，形式化了隐私约束并衡量了遗忘后的决策质量。这些工作表明，隐私保护与联邦学习正从单纯的模型训练扩展到数据遗忘、采样算法以及对抗性隐私攻击的防御，特别是在医疗等敏感领域，个性化与遗忘机制成为关键。

## Agent 安全与治理

随着 AI Agent 在复杂工作流中的应用，其调度、执行与治理成为安全研究的核心。**SAGA: Workflow-Atomic Scheduling for AI Agent Inference on GPU Clusters** 指出当前 GPU 调度器将每个 LLM 调用视为独立请求，忽略了 Agent 工作流中的中间状态，导致端到端延迟增加。SAGA 提出将 Agent 工作流作为第一类可调度单元，通过 Agent 执行图、状态保持和批处理机制，实现了程序级调度。这与 **RunAgent: Interpreting Natural-Language Plans with Constraint-Guided Execution** 相呼应，后者提出多 Agent 计划执行平台，通过约束和标准强制执行逐步执行， bridging 自然语言的表达力与编程的确定性。

在 RAG 系统的安全方面，**When RAG Chatbots Expose Their Backend: An Anonymized Case Study of Privacy and Security Risks in Patient-Facing Medical AI** 报告了对公开患者面医疗 RAG 聊天机器人的匿名安全评估，识别了治理教训。该研究强调 AI 辅助开发降低了构建门槛，但仍需严格的安全、隐私和治理控制。针对 RAG 知识库中的恶意文档，**CleanBase: Detecting Malicious Documents in RAG Knowledge Databases** 提出了一种检测恶意文档的方法，其核心洞察是恶意文档通常包含精心设计的注入提示，可通过特定特征检测。此外，**BlenderRAG: High-Fidelity 3D Object Generation via Retrieval-Augmented Code Synthesis** 展示了 RAG 在代码生成中的应用，通过检索专家验证的示例，提高了编译成功率和语义对齐度。

在硬件与系统安全方面，**KingsGuard: Enclave Data Protection Under Real-World TEE Vulnerabilities** 提出了新的可信执行环境（TEE）设计，通过硬件层面的细粒度数据流跟踪和控制，防止敏感数据泄露。**Zero-Knowledge Model Checking** 则引入了一种技术，在不揭示系统本身的情况下形式化验证软件系统是否满足功能正确性的时序规范，结合了演绎模型检查与零知识证明。此外，**Position: agentic AI orchestration should be Bayes-consistent** 论证了 Agent AI 的控制层应遵循贝叶斯原则，以在不确定性下维持信念。**Decouple before Integration: Test-time Synthesis of SFT and RLVR Task Vectors** 分析了 SFT 和 RLVR 的集成挑战，揭示了任务向量中的结构属性（如幅度差异、符号干扰），并提出了解耦集成策略。这些工作共同构建了 Agent 安全的多层次防御体系，从调度优化、执行约束到硬件隔离和形式化验证。

## 产业动态与开源生态

开源社区在 AI 安全工具与框架的构建上展现出活跃态势。**pr-review-agent-council** 项目实践了基于多 Agent 审查的 PR Review 流程，引入了辩论委员会、工具调用和结构化报告评估机制。**llm-wiki** 利用 AI 持续构建和维护个人知识库，支持从多种素材源自动整理为结构化 Wiki。**goblintown** 提供了针对 OpenAI 的多 Agent 编排协议，包含 Goblins、Gremlin、Troll 等角色，实现了内容寻址、漂移监控和预算限制。**slop-review** 为 Claude Code 等工具提供了原生审查窗口，允许在发布前审查代码质量。**oh-my-kimichan** 则是面向 Kimi Code CLI 的生产级多 Agent 编排基础，支持工作区团队执行、DAG/集合规划和质量门控。**composio** 提供了多提供商的 AI Agent SDK，支持工具集成和自动化。**craft-agents-oss** 则是一个基于 Electron 的桌面 AI 客户端，支持多 LLM 和 MCP 技能。**Stable-Diffusion-AI-Free** 展示了本地部署的开源图像生成工具，强调身份锚定和实时视频一致性。

在资本与基础设施层面，**OpenMonoAgent.ai** 强调 AI 不应有令牌限制，主张基于本地 LLM 的终端原生编码 Agent，完全开源且免费。**NVIDIA-Omniverse/content-agents** 利用视觉 - 语言模型自动化 3D 内容工作流。**0xhimanshu/governor** 作为补充资源，提供了 Claude Code 使用治理工具，包括紧凑输出、上下文精简、工具输出过滤和漂移护栏。这些工具反映了产业界对 Agent 安全性、可观测性和成本控制的需求。尽管市场波动频繁，但资本流向显示了对基础设施层和治理工具的持续投入，而非单纯的应用层炒作。特别是在医疗和工业场景中，安全与隐私成为部署的关键考量。

## Looking Forward

展望未来 3-6 个月，AI 安全与治理领域预计将呈现以下趋势。首先，多模态模型的对抗鲁棒性评估将标准化，STARE 等工具可能成为 VLM 安全测试的基准组件，特别是在医疗和自动驾驶等高风险领域。其次，联邦学习中的遗忘机制与隐私保护将深度融合，EASE 和 FedKPer 提出的个性化与遗忘框架可能成为医疗数据协作的标准协议。第三，Agent 系统的治理将从代码审查扩展到执行轨迹的实时监控，SAGA 和 RunAgent 的调度与执行约束机制可能演变为 Agent 操作系统的核心模块。

理论层面，**Decouple before Integration** 和 **Position: agentic AI orchestration should be Bayes-consistent** 提出的任务向量解耦与贝叶斯一致性原则，可能成为未来 Agent 架构设计的理论基础。同时，**Possibilistic Predictive Uncertainty for Deep Learning** 提出的狄利克雷近似可能性后验预测，有望解决深度神经网络在未见输入上的过度自信问题，提升模型的可信度。然而，仍需解决的理论问题包括：如何在资源受限的边缘设备上实现高效的认证训练（如量子 IBP 的扩展）；如何在多 Agent 协作中平衡效率与形式化验证的成本；以及如何在全球监管框架下实现跨语言安全对齐的自动化。此外，开源社区需警惕工具被滥用于生成对抗样本的风险，如 **Repurposing Image Diffusion Models** 所示，通用模型的滥用可能带来新的安全挑战。产业界应继续推动透明化评估，避免夸大营销，确保技术落地符合伦理与法律规范。

## 参考来源

1.  [arxiv_cr] STARE: Step-wise Temporal Alignment and Red-teaming Engine for Multi-modal Toxicity Attack
2.  [arxiv_cr] Defense against Poisoning Attacks under Shuffle-DP
3.  [arxiv_lg] Jailbreaking Vision-Language Models Through the Visual Modality
4.  [arxiv_cr] When RAG Chatbots Expose Their Backend: An Anonymized Case Study of Privacy and Security Risks in Patient-Facing Medical AI
5.  [arxiv_cr] Repurposing Image Diffusion Models for Adversarial Synthetic Structured Data: A Case Study of Ground Truth Drift
6.  [arxiv_cr] ML-Bench&Guard: Policy-Grounded Multilingual Safety Benchmark and Guardrail for Large Language Models
7.  [arxiv_lg] Meritocratic Fairness in Budgeted Combinatorial Multi-armed Bandits via Shapley Values
8.  [arxiv_lg] Themis: Training Robust Multilingual Code Reward Models for Flexible Multi-Criteria Scoring
9.  [arxiv_lg] Quantum Interval Bound Propagation for Certified Training of Quantum Neural Networks
10. [arxiv_lg] FedKPer: Tackling Generalization and Personalization in Medical Federated Learning via Knowledge Personalization
11. [arxiv_lg] SAGA: Workflow-Atomic Scheduling for AI Agent Inference on GPU Clusters
12. [arxiv_lg] Scale-Aware Adversarial Analysis: A Diagnostic for Generative AI in Multiscale Complex Systems
13. [arxiv_cr] CleanBase: Detecting Malicious Documents in RAG Knowledge Databases
14. [arxiv_lg] HyCOP: Hybrid Composition Operators for Interpretable Learning of PDEs
15. [arxiv_lg] SAVGO: Learning State-Action Value Geometry with Cosine Similarity for Continuous Control
16. [arxiv_lg] EASE: Federated Multimodal Unlearning via Entanglement-Aware Anchor Closure
17. [arxiv_l

---


## 参考来源

- **STARE: Step-wise Temporal Alignment and Red-teaming Engine for Multi-modal Toxicity Attack** — [arxiv_cr](https://arxiv.org/abs/2605.00699v1)
- **Defense against Poisoning Attacks under Shuffle-DP** — [arxiv_cr](https://arxiv.org/abs/2605.00625v1)
- **Jailbreaking Vision-Language Models Through the Visual Modality** — [arxiv_lg](https://arxiv.org/abs/2605.00583v1)
- **When RAG Chatbots Expose Their Backend: An Anonymized Case Study of Privacy and Security Risks in Patient-Facing Medical AI** — [arxiv_cr](https://arxiv.org/abs/2605.00796v1)
- **Repurposing Image Diffusion Models for Adversarial Synthetic Structured Data: A Case Study of Ground Truth Drift** — [arxiv_cr](https://arxiv.org/abs/2605.00788v1)
- **ML-Bench&Guard: Policy-Grounded Multilingual Safety Benchmark and Guardrail for Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.00689v1)
- **Meritocratic Fairness in Budgeted Combinatorial Multi-armed Bandits via Shapley Values** — [arxiv_lg](https://arxiv.org/abs/2605.00762v1)
- **Themis: Training Robust Multilingual Code Reward Models for Flexible Multi-Criteria Scoring** — [arxiv_lg](https://arxiv.org/abs/2605.00754v1)
- **Quantum Interval Bound Propagation for Certified Training of Quantum Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2605.00747v1)
- **FedKPer: Tackling Generalization and Personalization in Medical Federated Learning via Knowledge Personalization** — [arxiv_lg](https://arxiv.org/abs/2605.00698v1)
- **SAGA: Workflow-Atomic Scheduling for AI Agent Inference on GPU Clusters** — [arxiv_lg](https://arxiv.org/abs/2605.00528v1)
- **Scale-Aware Adversarial Analysis: A Diagnostic for Generative AI in Multiscale Complex Systems** — [arxiv_lg](https://arxiv.org/abs/2605.00510v1)
- **CleanBase: Detecting Malicious Documents in RAG Knowledge Databases** — [arxiv_cr](https://arxiv.org/abs/2605.00460v1)
- **HyCOP: Hybrid Composition Operators for Interpretable Learning of PDEs** — [arxiv_lg](https://arxiv.org/abs/2605.00820v1)
- **SAVGO: Learning State-Action Value Geometry with Cosine Similarity for Continuous Control** — [arxiv_lg](https://arxiv.org/abs/2605.00787v1)
- **EASE: Federated Multimodal Unlearning via Entanglement-Aware Anchor Closure** — [arxiv_lg](https://arxiv.org/abs/2605.00733v1)
- **Decentralized Proximal Stochastic Gradient Langevin Dynamics** — [arxiv_lg](https://arxiv.org/abs/2605.00723v1)
- **Aitchison Embeddings for Learning Compositional Graph Representations** — [arxiv_lg](https://arxiv.org/abs/2605.00716v1)
- **Evaluating the Architectural Reasoning Capabilities of LLM Provers via the Obfuscated Natural Number Game** — [arxiv_lg](https://arxiv.org/abs/2605.00677v1)
- **Augmented Lagrangian Multiplier Network for State-wise Safety in Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.00667v1)
- **Reinforcement Learning with Markov Risk Measures and Multipattern Risk Approximation** — [arxiv_lg](https://arxiv.org/abs/2605.00654v1)
- **PEACE: Cross-modal Enhanced Pediatric-Adult ECG Alignment for Robust Pediatric Diagnosis** — [arxiv_lg](https://arxiv.org/abs/2605.00647v1)
- **Unlearning Offline Stochastic Multi-Armed Bandits** — [arxiv_lg](https://arxiv.org/abs/2605.00638v1)
- **BlenderRAG: High-Fidelity 3D Object Generation via Retrieval-Augmented Code Synthesis** — [arxiv_lg](https://arxiv.org/abs/2605.00632v1)
- **Fairness of Classifiers in the Presence of Constraints between Features** — [arxiv_lg](https://arxiv.org/abs/2605.00592v1)
- **Stable-GFlowNet: Toward Diverse and Robust LLM Red-Teaming via Contrastive Trajectory Balance** — [arxiv_lg](https://arxiv.org/abs/2605.00553v1)
- **Self-Adaptive Multi-Agent LLM-Based Security Pattern Selection for IoT Systems** — [arxiv_cr](https://arxiv.org/abs/2605.00741v1)
- **KingsGuard: Enclave Data Protection Under Real-World TEE Vulnerabilities** — [arxiv_cr](https://arxiv.org/abs/2605.00613v1)
- **Pick and Sort for Graphical Authentication** — [arxiv_cr](https://arxiv.org/abs/2605.00558v1)
- **ForesightFlow: An Information Leakage Score Framework for Prediction Markets** — [arxiv_cr](https://arxiv.org/abs/2605.00493v1)
- **Zero-Knowledge Model Checking** — [arxiv_cr](https://arxiv.org/abs/2605.00487v1)
- **In Harvard study, AI offered more accurate emergency room diagnoses than two human doctors** — [techcrunch_ai](https://techcrunch.com/2026/05/03/in-harvard-study-ai-offered-more-accurate-diagnoses-than-emergency-room-doctors/)
- **How the internet’s favorite squirrel dad made the hottest camera app of 2026** — [theverge_ai](https://www.theverge.com/tech/921690/dualshot-recorder-iphone-camera-app-derrick-downey-jr)
- **AI music is flooding streaming services — but who wants it?** — [theverge_ai](https://www.theverge.com/column/921599/ai-music-is-flooding-streaming-services-but-who-wants-it)
- **‘This is fine’ creator says AI startup stole his art** — [techcrunch_ai](https://techcrunch.com/2026/05/03/this-is-fine-creator-says-ai-startup-stole-his-art/)
- **csy-csy123/pr-review-agent-council** — [github](https://github.com/csy-csy123/pr-review-agent-council)
- **liangdabiao/llm-wiki** — [github](https://github.com/liangdabiao/llm-wiki)
- **0xbl33p/goblintown** — [github](https://github.com/0xbl33p/goblintown)
- **dbachelder/slop-review** — [github](https://github.com/dbachelder/slop-review)
- **CCCpan/ai-api-integration** — [github](https://github.com/CCCpan/ai-api-integration)
- **dmae97/oh-my-kimichan** — [github](https://github.com/dmae97/oh-my-kimichan)
- **Abishek-kk/AutoMart-AI** — [github](https://github.com/Abishek-kk/AutoMart-AI)
- **coleam00/ai-transformation-workshop** — [github](https://github.com/coleam00/ai-transformation-workshop)
- **NVIDIA-Omniverse/content-agents** — [github](https://github.com/NVIDIA-Omniverse/content-agents)
- **KSroido/Kagi-Session2API-MCP** — [github](https://github.com/KSroido/Kagi-Session2API-MCP)
- **warpdot-dev/craft-agents-oss** — [github](https://github.com/warpdot-dev/craft-agents-oss)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **StartupHakk/OpenMonoAgent.ai** — [github](https://github.com/StartupHakk/OpenMonoAgent.ai)
- **warpdot-dev/composio** — [github](https://github.com/warpdot-dev/composio)
- **endless-sky-team/ai-trading-agent** — [github](https://github.com/endless-sky-team/ai-trading-agent)
- **lukiIabs/trading-agents** — [github](https://github.com/lukiIabs/trading-agents)
- **Julpygo/Claude-Code-AI-Design** — [github](https://github.com/Julpygo/Claude-Code-AI-Design)
- **Senabayu08989/Stable-Diffusion-AI-Free** — [github](https://github.com/Senabayu08989/Stable-Diffusion-AI-Free)
- **noonghunna/club-3090** — [github](https://github.com/noonghunna/club-3090)
- **YutoTerashima/agent-safety-eval-lab** — [github](https://github.com/YutoTerashima/agent-safety-eval-lab)
- **太抓马了！马斯克OpenAI开庭，硅谷巨富互揭老底像极了村口吵架** — [qbitai](https://www.qbitai.com/2026/05/412080.html)
- **不好！1930年的AI都来抢程序员饭碗了** — [qbitai](https://www.qbitai.com/2026/05/412896.html)
- **豆包将在免费模式外新增付费订阅，官方回应** — [36kr](https://36kr.com/newsflashes/3794495772712195?f=rss)
- **精锻科技：当前公司机器人业务尚未形成销售收入** — [36kr](https://36kr.com/newsflashes/3794483360046337?f=rss)
- **恒指午间休盘涨1.7%，恒生科技指数涨2.86%** — [36kr](https://36kr.com/newsflashes/3794457822059523?f=rss)
- **恒生科技指数涨近4%，小米集团涨逾10%** — [36kr](https://36kr.com/newsflashes/3794415662373895?f=rss)
- **高盛据悉将向与Anthropico合资的企业注资约1.5亿美元** — [36kr](https://36kr.com/newsflashes/3794354869869833?f=rss)
- **Position: agentic AI orchestration should be Bayes-consistent** — [arxiv_lg](https://arxiv.org/abs/2605.00742v1)
- **Hierarchical Abstract Tree for Cross-Document Retrieval-Augmented Generation** — [arxiv_lg](https://arxiv.org/abs/2605.00529v1)
- **RunAgent: Interpreting Natural-Language Plans with Constraint-Guided Execution** — [arxiv_lg](https://arxiv.org/abs/2605.00798v1)
- **Decouple before Integration: Test-time Synthesis of SFT and RLVR Task Vectors** — [arxiv_lg](https://arxiv.org/abs/2605.00610v1)
- **Possibilistic Predictive Uncertainty for Deep Learning** — [arxiv_lg](https://arxiv.org/abs/2605.00600v1)
- **0xhimanshu/governor** — [github](https://github.com/0xhimanshu/governor)