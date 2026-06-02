# AI 日报 [AI 安全] - 2026-06-02


# AI安全每日专题摘要：2026年6月2日

## 亮点
今日的研究进展集中于应对大语言模型（LLM）智能体（Agent）带来的新型安全范式挑战，以及通过创新隐私技术保障对齐过程。最引人注目的突破包括：针对LLM Agent的**多步骤特洛伊木马攻击**被系统化提出，揭示了在无害操作链条中隐匿恶意指令的新威胁；**差分隐私偏好数据合成**方法实现了在保护用户隐私前提下进行模型对齐的可行路径；同时，一项关于**AI失控事件管理**的框架首次将研究重点从纯粹的预防转向危机响应与韧性构建，标志着安全理念的重要转变。此外，针对智能体提示注入攻击的防御与检测方法，以及基于归因的LLM匿名化技术，共同构成了本日安全研究的多维度前线。

## 对抗攻击与鲁棒性：从图像到智能体的全面审视
本日的对抗性研究呈现出两个清晰的脉络：一是对传统计算机视觉模型鲁棒性的再审视，二是将战场迅速转移至新兴的LLM智能体系统。在视觉领域，两项工作指出了现有评估方法的不足。**《AdvScene》** 一文批判了当前对抗性补丁评估脱离真实世界部署条件的现状，提出了“场景鲁棒性”概念，强调评估需涵盖视角、距离和场景变化等现实变量。而**《Escaping the Linearity Trap》** 则深入攻击了基于自监督学习的歌唱语音深度伪造检测器，揭示了其面对对抗攻击时“伪鲁棒性”的成因——源于优化目标中的局部线性陷阱，并提出了基于流形绕行的新型攻击方法，迫使研究者重新评估此类系统的安全性。

然而，更具紧迫性的威胁来自LLM智能体。多篇论文共同描绘了一幅令人警惕的图景：**《From Prompt Injection to Persistent Control》** 首次系统化定义了针对本地智能体外壳（harness）的“多步特洛伊木马攻击”，攻击者通过污染智能体可读写的文件或工具输出植入指令，这些指令在后续会话中被智能体自主加载并执行，整个过程的任何单独步骤都可能看似无害。**《Depth-Dependent Indirect Prompt Injection in Tool-Calling ReAct Agents》** 进一步细化了这种攻击，研究了在工具调用中注入位置（深度）、负载措辞和对话轮次预算对攻击成功率的影响。更令人不安的是，**《Automatically Attacking Software Reverse Engineering AI Agents》** 和**《TRACE》** 展示了攻击者可以自动化地生成并利用此类漏洞，前者攻击了用于二进制分析的智能体，后者则构建了能够诱导LLM Agent规划并执行复杂恶意操作的任务感知自进化越狱框架。

面对这些威胁，防御端也在积极行动。**《Strengthening Polymorphic Prompt Assembling》** 提出了动态生成每请求唯一分隔符的方案，以防御静态分隔符池被泄露后的“爆破半径”漏洞。**《The Surface You Test Is Not the Surface That Breaks》** 则尖锐地指出，现有评估仅关注工具输出通道的注入成功率，却忽略了工具描述本身这一在每个对话回合都会被读取的更早、更持久的注入表面，呼吁更全面的攻击面分析。这些工作共同表明，智能体安全已从对单个模型输出的审查，演变为对复杂、有状态交互链条中潜在信任关系滥用的全面监控挑战。

## 模型对齐与可解释性：在隐私、公平与内在机制之间
对齐研究正朝着更精细化、更具理论基础和更尊重用户权利的方向发展。**《Differentially Private Preference Data Synthesis for Large Language Model Alignment》** 提出的 **DPPrefSyn** 框架是一个关键进展。它基于 Bradley-Terry 偏好模型生成合成的、满足差分隐私的偏好数据，用于模型的对齐后训练。作者声称，这解决了真实人类偏好数据中可能包含敏感信息（用户提示和人类判断）引发的隐私担忧，为隐私保护下的偏好学习开辟了新路径。

在公平性方面，**《COFT》** 提出了一种无需训练的解码方法，在生成思维链（Chain-of-Thought）时通过反事实提示和token级别的公平性控制，减轻LLM放大的社会偏见。其核心创新在于利用掩码反事实提示和校准集实现分布无关的边际有效性保证。**《Steering Beyond the Support》** 则从对抗训练的角度出发，针对安全引导（steering）方法在面对未见过的越狱攻击时失效的问题，提出了基于无监督越狱激活模拟的对抗训练，以增强引导模块的泛化能力。

可解释性研究则致力于理解模型内部机制。**《Measuring, Localizing, and Ablating Alignment Signatures in LLMs》** 深入探究了后训练（如RLHF）是否在模型内部引入了可识别的“AI风格”特征。通过对比人类文本、基础模型和对齐模型的生成，作者发现对齐后的生成具有更低的人类语料库亲和力，并且这种特征在模型内部具有局部化的表征。**《Certified Circuits》** 则为机制可解释性中的“电路”发现提供了稳定性保证，旨在解决电路发现结果依赖数据集、可能只是数据集特定产物的疑虑。这些工作共同推动对齐从行为表层向模型内部表征的深层理解迈进。

## 隐私保护与联邦学习：理论突破与系统设计
隐私计算领域在理论优化和应用架构上均有新收获。在差分隐私理论方面，**《Optimal conversion from Rényi Differential Privacy to $f$-Differential Privacy》** 终于证明了一个长期存在的猜想，即基于单阶RDP隐私区域交集的转换规则，在所有有效的RDP配置和所有一类错误水平下都是最优的。这为差分隐私中两种主要隐私预算度量（RDP和f-DP）之间的转换提供了最紧的理论界限。**《Fast Mixing Mechanism for Differential Privacy》** 则将高效随机化 sketch 技术（如Hadamard变换）与差分隐私优化相结合，旨在解决大规模DP线性回归等任务中的计算效率问题。

在系统与应用层面，**《LLM-FACETS》** 提出了一个隐私保护的LLM评估框架，其核心是允许非技术专家在本地环境中评估LLM的透明度和问责性，无需将评估数据发送至外部云服务，这直接回应了合规官员对数据泄露的担忧。**《On-Device Generative AI for GDPR-Compliant Visual Monitoring》** 展示了一个完全在边缘设备（树莓派5+AI加速器）上运行的视觉监控流水线，从推理到生成自然语言警报均不泄露原始图像，是符合GDPR数据最小化原则的“隐私始于设计”的实用范例。**《MosaicLeaks》** 则聚焦于深度研究智能体的隐私风险，指出当智能体结合本地私有文档和外部网络检索时，其单个查询可能看似无害，但多个查询的聚合（马赛克效应）可能泄露敏感信息，并为此提出了专门的基准。这些工作共同勾勒出从基础理论、评估框架到边缘部署的完整隐私保障链路。

## 安全评估基准与审计工具
评估与审计是安全落地的基石。**《PReMISE》** 提出了将可复用的评估标准（Rubric）视为“测量规范”的框架，能够从成对人类偏好数据中自动发现政策层面的评估标准集，并审计LLM评估器在不同标准下的行为，旨在解决评估器因标准模糊而奖励“看似流畅但事实错误”的回答问题。**《EUDAIMONIA》** 则关注LLM在社交互动中的风险，引入了“社会AI设计规范”，评估模型是否鼓励有害亲密关系、依赖性或过度使用，超越了传统的能力导向安全评估。

在特定领域的可信度评估上，**《When AI Meets Wall Street》** 全面调研了金融科技中可信AI的挑战，指出AI决策流水线在自动化的同时也创造了新的攻击面，微小的算法扰动可能放大为系统性金融损失。**《ImmigrationQA》** 构建了基于源文档的美国移民法问答数据集，并在此基础上微调模型，旨在提高在高风险、法律密集型任务中的事实准确性和可追溯性。**《idSCD》** 提出了一种通过模型内部语义关联结构来识别训练数据集成员资格的新方法，为数据溯源和审计提供了新思路。

开源工具方面，一系列面向智能体开发、记忆管理和安全审计的工具涌现。**《memory-os》** 提供了一个多层、可本地运行的智能体记忆操作系统。**《AgentClaimGuard》** 是一个用于验证智能体声明是否基于证据、工具结果或策略的证据门控工具。这些工具正致力于将安全与可信原则嵌入智能体的开发生命周期。

## 智能体安全与治理：从技术到架构
智能体的安全治理需要超越单纯的模型对齐，考虑其运行时的架构和权限。**《Organization-Scoped LLM Agent Runtime Architecture for Regulated Cybersecurity Operations》** 针对受监管的网络安全运营，提出了一个在检索、工具调用、记忆、发现和审计等全流程强制执行组织范围隔离的运行时架构，旨在为模型无关、本地部署的智能体提供可审计的平台基础。**《AURA》** 提出的LLM匿名化框架则旨在对抗具备网络搜索能力的智能体重识别威胁，在保持文本分析效用和抵抗基于上下文线索的重识别之间寻找平衡。

更宏观的治理视角来自**《AI Loss of Control Incident Management》**，它首次系统性地构建了管理灾难性AI失控事件的框架和分类学，区分了“恢复控制极其困难”与“不可能恢复控制”两类场景，并为不可能场景呼吁立即投入韧性建设。这标志着AI安全讨论开始严肃地为最坏情况做准备。**《The Global Landscape of Environmental AI Regulation》** 则从环境成本角度审视AI治理，指出生成式AI的环境影响被低估，且全球监管在透明度要求上存在巨大差距。

## 产业动态与工具生态
产业界，Meta的AI支持聊天机器人被利用来劫持Instagram账户的事件，再次凸显了AI系统在客户服务场景中被恶意利用的风险。科技巨头持续加码AI基础设施，Alphabet计划融资800亿美元，OpenAI在密歇根州破土动工建设1GW的数据中心，这些投资将深刻影响AI的算力格局与安全治理的边界。

GitHub上，面向智能体开发的工具生态日益繁荣，出现了大量专注于代码规则同步（**ai-rules-sync**）、自动化质量保证循环（**autonomous-qa-loop**）、渐进式指令披露（**agents-progressive-disclosure**）以及科学方法论技能（**science-superpowers**）的项目。这些工具旨在提升智能体开发的可控性、透明度和可靠性，是安全实践工程化的重要体现。

## 展望
尽管今日进展显著，若干根本性问题仍未解决。首先，针对LLM智能体的**特洛伊木马式、多步骤的恶意操作**，其根本的防御范式是什么？是严格的工具调用沙盒、更强大的运行时意图推理，还是从根本上限制智能体的自主性？目前的研究更多是揭示威胁和提出针对性修补，尚未形成统一的理论框架。

其次，**对齐的本质**在多大程度上是一个结构性权衡问题？**多目标优化**理论虽然提供了分析工具，但如何将“有用性”、“无害性”、“诚实性”乃至“隐私保护”这些时常冲突的目标形式化，并找到可接受的帕累托前沿，仍是开放的理论难题。DPPrefSyn等方法虽在隐私与对齐间架起桥梁，但其长期对齐效果仍需验证。

再者，**可解释性与安全性的关系**错综复杂。模型内部的“对齐签名”被发现后，攻击者是否可以利用这些知识进行更精准的去对齐攻击？而“认证电路”等旨在提高可解释性稳定性的方法，能否真正抵御对抗性操纵？

最后，**AI失控事件的响应与韧性建设**从理论呼吁走向实践，将需要跨学科（AI安全、应急管理、国际关系）的深度融合，以及可能全新的制度设计。在追求强大能力的同时，如何系统性地构建“安全冗余”和“失败优雅”机制，将是下一阶段AI安全研究的核心议题。

---


## 参考来源

- **Organizational Adaptation to Generative AI in Cybersecurity** — [arxiv_cr](https://arxiv.org/abs/2506.12060)
- **When AI Meets Wall Street: A Survey on Trustworthy AI in Fintech** — [arxiv_cr](https://arxiv.org/abs/2605.30650)
- **A Unified Framework for Gradient Aggregation in Multi-Objective Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.30452)
- **Differentially Private Preference Data Synthesis for Large Language Model Alignment** — [arxiv_cr](https://arxiv.org/abs/2605.30808)
- **From Prompt Injection to Persistent Control: Defending Agentic Harness Against Trojan Backdoors** — [arxiv_cr](https://arxiv.org/abs/2605.31042)
- **$PC^2$: Politically Controversial Content Generation via Jailbreaking Attacks on GPT-based Text-to-Image Models** — [arxiv_cr](https://arxiv.org/abs/2601.05150)
- **Generating Graph-like Rules for Knowledge Graph Reasoning via Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2605.30747)
- **PReMISE: Policy Rubrics as Measurement Specifications for LLM Judges** — [arxiv_ai](https://arxiv.org/abs/2605.30803)
- **LLM-FACETS: A Privacy-Preserving Framework for Evaluating LLM Transparency and Accountability** — [arxiv_ai](https://arxiv.org/abs/2605.31167)
- **Enhancing Regime Shift Detection Using Unstructured Data: A Study on the Treasury Market** — [arxiv_ai](https://arxiv.org/abs/2605.30363)
- **When LLMs Learn to Be Consistently Wrong: A Multi-Model Study of Linear Representations of Synthetic Deception** — [arxiv_ai](https://arxiv.org/abs/2605.30381)
- **DTG-Restore: Training-Free Diffusion Refinement for Generative Video Super-Resolution** — [arxiv_cv](https://arxiv.org/abs/2605.30431)
- **Escaping the Linearity Trap: Manifold Detours for Black-Box Adversarial Attacks on Singing Audio Deepfake Detection** — [arxiv_cr](https://arxiv.org/abs/2605.30366)
- **AdvScene: Rethinking Adversarial Patch Evaluation Through Scene Robustness** — [arxiv_cr](https://arxiv.org/abs/2605.30578)
- **Automatically Attacking Software Reverse Engineering AI Agents** — [arxiv_cr](https://arxiv.org/abs/2605.30667)
- **Investigating Detection and Obfuscation of Prompt Injection Attacks Against Software Reverse Engineering AI Agents** — [arxiv_cr](https://arxiv.org/abs/2605.30677)
- **LLM Anonymization Against Agentic Re-Identificatio** — [arxiv_cr](https://arxiv.org/abs/2605.30848)
- **TRACE: Task-Aware Adaptive Self-Evolving Agentic Jailbreaking** — [arxiv_cr](https://arxiv.org/abs/2605.30883)
- **Thou Shall Not Pass: Gatekeeping Outbound TLS Connections** — [arxiv_cr](https://arxiv.org/abs/2605.31020)
- **Local Differential Privacy with Correlated Noise Achieves Central-DP Optimal Cost** — [arxiv_cr](https://arxiv.org/abs/2605.30476)
- **On-Device Generative AI for GDPR-Compliant Visual Monitoring: Natural Language Alerts from Local Object Detection** — [arxiv_cr](https://arxiv.org/abs/2605.30544)
- **Optimal conversion from R\'enyi Differential Privacy to $f$-Differential Privacy** — [arxiv_cr](https://arxiv.org/abs/2602.04562)
- **Steering Beyond the Support: Adversarial Training on Unsupervised Jailbroken Activation Simulation** — [arxiv_cr](https://arxiv.org/abs/2605.24535)
- **Bounded Behavioral Indistinguishability for Black-Box LLM Distillation** — [arxiv_lg](https://arxiv.org/abs/2605.30448)
- **VeriGate: Verifier-Gated Step-Level Supervision for GRPO** — [arxiv_lg](https://arxiv.org/abs/2605.30451)
- **Can Subgraph Explanations Be Weaponized to Steal Graph Neural Networks?** — [arxiv_lg](https://arxiv.org/abs/2605.30470)
- **Discovering a Zeta Map Algorithm on Dyck Paths via Mechanistic Interpretability** — [arxiv_lg](https://arxiv.org/abs/2605.30482)
- **Supervised Training Rapidly Degrades Early Visual Cortex Alignment Across Biologically Plausible Learning Rules** — [arxiv_lg](https://arxiv.org/abs/2605.30556)
- **Benchmarking Machine Learning Uncertainty Quantification Methodologies for Predicting Turbine Gas Temperature Degradation** — [arxiv_lg](https://arxiv.org/abs/2605.30585)
- **The Fast Mixing Mechanism for Differential Privacy** — [arxiv_lg](https://arxiv.org/abs/2605.30600)
- **TASER: Task-Aware Stein Regularisation for Geometry-Driven Robustness** — [arxiv_lg](https://arxiv.org/abs/2605.30601)
- **Equivariant Latent Alignment via Flow Matching under Group Symmetries** — [arxiv_cv](https://arxiv.org/abs/2605.30705)
- **What Makes LVLMs Hallucinate Less? Unveiling the Architectural Factors Behind Hallucination Robustness** — [arxiv_cv](https://arxiv.org/abs/2605.30911)
- **Evaluating using Mock Tool Calls to Quarantine Untrusted Prompt Inputs** — [arxiv_cl](https://arxiv.org/abs/2605.30521)
- **ImmigrationQA: A Source-Grounded Dataset and Small-Model Adaptation for U.S. Immigration Law** — [arxiv_cl](https://arxiv.org/abs/2605.30589)
- **COFT: Counterfactual-Conformal Decoding for Fair Chain-of-Thought Reasoning in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30641)
- **EUDAIMONIA: Evaluating Undesirable Dynamics in AI** — [arxiv_cl](https://arxiv.org/abs/2605.30654)
- **The Flip Side of RLHF: On-Policy Feedback for Reward Model Self-Supervised Improvement** — [arxiv_cl](https://arxiv.org/abs/2605.30888)
- **The Surface You Test Is Not the Surface That Breaks** — [arxiv_cr](https://arxiv.org/abs/2605.30454)
- **Strengthening Polymorphic Prompt Assembling: Dynamic Separator Generation Against Emerging Prompt Injection Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.30534)
- **An Organization-Scoped LLM Agent Runtime Architecture for Regulated Cybersecurity Operations** — [arxiv_cr](https://arxiv.org/abs/2605.30604)
- **Depth-Dependent Indirect Prompt Injection in Tool-Calling ReAct Agents: Injection Depth, Payload Framing, and Turn-Budget Sensitivity** — [arxiv_cr](https://arxiv.org/abs/2605.30686)
- **LLMs Without Deep Neural Networks: New Architecture, Benefits and Case Study** — [arxiv_lg](https://arxiv.org/abs/2605.30385)
- **Calibrated Preference Learning: The Case of Label Ranking** — [arxiv_lg](https://arxiv.org/abs/2605.30447)
- **Scalable Constrained Multi-Agent Reinforcement Learning via State Augmentation and Consensus for Separable Dynamics** — [arxiv_lg](https://arxiv.org/abs/2605.30461)
- **idSCD: Identifying Training Datasets through Semantic Correlation Descriptors** — [arxiv_lg](https://arxiv.org/abs/2605.30462)
- **Measuring, Localizing, and Ablating Alignment Signatures in LLMs** — [arxiv_lg](https://arxiv.org/abs/2605.30526)
- **The Long-Term Effects of Data Selection in LLM Fine-Tuning** — [arxiv_lg](https://arxiv.org/abs/2605.30537)
- **Active Timepoint Selection for Learning Measure-Valued Trajectories** — [arxiv_lg](https://arxiv.org/abs/2605.30625)
- **CellBRIDGE: Learning Cellular Trajectories via Interaction-Aware Alignment** — [arxiv_lg](https://arxiv.org/abs/2605.30635)
- **CSULoRA: Closest Safe Update Low-Rank Adaptation** — [arxiv_lg](https://arxiv.org/abs/2605.30640)
- **Diffusion Models Preferentially Memorize Prototypical Examples or: Why Does My Diffusion Model Love Slop?** — [arxiv_lg](https://arxiv.org/abs/2605.30642)
- **Convergence of Steepest Descent and Adam under Non-Uniform Smoothness** — [arxiv_lg](https://arxiv.org/abs/2605.30648)
- **Uncertainty-Aware and Temporally Regulated Expert Advice in Reinforcement Learning for Autonomous Driving** — [arxiv_ai](https://arxiv.org/abs/2605.30576)
- **EHRBench: An Automated and Reliable EHR-based Benchmark for Clinical Decision Making with LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.30637)
- **Structure-Induced Information for Rerooting Levin Tree Search** — [arxiv_ai](https://arxiv.org/abs/2605.30664)
- **Healthcare Mechanisms from Policy-as-Code Search under Strategic Provider Response** — [arxiv_ai](https://arxiv.org/abs/2605.30680)
- **MAVEN: Improving Generalization in Agentic Tool Calling** — [arxiv_ai](https://arxiv.org/abs/2605.30738)
- **COMPASS: Cognitive MCTS-Guided Process Alignment for Safe Search Agents** — [arxiv_ai](https://arxiv.org/abs/2605.30838)
- **Distilling LLM Feedback for Lean Theorem Proving** — [arxiv_ai](https://arxiv.org/abs/2605.30861)
- **BilliardPhys-Bench: Benchmarking Physical Reasoning and Visual Dynamics of Multimodal LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.30900)
- **A Persona-Based Evaluation Framework for Pluralistic Alignment in Generative AI** — [arxiv_ai](https://arxiv.org/abs/2605.31021)
- **Industrializing Prediction-Powered Inference: The GLIDE Library for Reliable GenAI and Agentic Systems Evaluation** — [arxiv_ai](https://arxiv.org/abs/2605.31278)
- **TraceGraph: Shared Decision Landscapes for Diagnosing and Improving Agent Trajectories** — [arxiv_ai](https://arxiv.org/abs/2605.31308)
- **Diagnosing Failure Modes of Shared-State Collaboration in Resource-Constrained Visual Agents** — [arxiv_ai](https://arxiv.org/abs/2605.31354)
- **Learning to Adapt: Self-Improving Web Agent via Cognitive-Aware Exploration** — [arxiv_ai](https://arxiv.org/abs/2605.31365)
- **LinTree: Improving LLM Reasoning with Explicitly Structured Search Histories** — [arxiv_ai](https://arxiv.org/abs/2605.31492)
- **Hamiltonian-Inspired Attention Mechanism for Scalable RF Transmitter Fingerprinting** — [arxiv_ai](https://arxiv.org/abs/2605.30364)
- **Mitigating Content Shift and Hallucination in GenAI Image Editing via Structural Refinement** — [arxiv_cv](https://arxiv.org/abs/2605.30437)
- **OmniMem: Scalable and Adaptive Memory Retrieval for Long Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30519)
- **ConTrans: Learning Text-enhanced Local-global Temporal Representations for Zero-shot Temporal Action Localization** — [arxiv_cv](https://arxiv.org/abs/2605.30689)
- **Seeing Before Agreeing: Aligning Multi-Agent Consensus with Visual Evidence** — [arxiv_cv](https://arxiv.org/abs/2605.30698)
- **Simple Token-Efficient Vision-Language Model for Case-level Pathology Synoptic Report Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30716)
- **Annotations Are Not All You Need: A Cross-modal Knowledge Transfer Network for Unsupervised Temporal Sentence Grounding** — [arxiv_cv](https://arxiv.org/abs/2605.30742)
- **DisPlace: Discriminative Place Projections for Multi-Reference Visual Place Recognition** — [arxiv_cv](https://arxiv.org/abs/2605.30769)
- **Text-guided Feature Disentanglement for Cross-modal Gait Recognition** — [arxiv_cv](https://arxiv.org/abs/2605.30784)
- **SteerFace: Debiasing Synthetic Face Generation via Adaptive Residue Perturbation** — [arxiv_cv](https://arxiv.org/abs/2605.30894)
- **MergeTok: Unified Continuous and Discrete Visual Tokenization via Token Merging** — [arxiv_cv](https://arxiv.org/abs/2605.30904)
- **DiTTo: Scalable Order-aware All-in-One Image Restoration Agent** — [arxiv_cv](https://arxiv.org/abs/2605.30915)
- **IAF-Net: Illumination-Adaptive Fusion for Low-Light Urban Road Segmentation** — [arxiv_cv](https://arxiv.org/abs/2605.30939)
- **PRISM: Progressive Reasoning through Iterative Slot Memory for Vision** — [arxiv_cv](https://arxiv.org/abs/2605.30942)
- **Omni-Supervised Motion Editing: Balancing Change and Invariance through Positive-Negative Learning** — [arxiv_cv](https://arxiv.org/abs/2605.30969)
- **BiSegMamba: Efficient Bidirectional Tri-Oriented Mamba for 3D Medical Image Segmentation** — [arxiv_cv](https://arxiv.org/abs/2605.30972)
- **Can BEV Perception Gracefully Degrade under Sensor Failures?** — [arxiv_cv](https://arxiv.org/abs/2605.30983)
- **Generating Reports or Repeating Templates? Measuring and Mitigating Template Collapse in 3D CT Report Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30984)
- **Can LLM Teams Play What? Where? When?** — [arxiv_cl](https://arxiv.org/abs/2605.30459)
- **Your Multimodal Speech Model Says I Have a Face for Radio** — [arxiv_cl](https://arxiv.org/abs/2605.30472)
- **When English Rewrites Local Knowledge: Global Narrative Dominance in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30481)
- **Configurable Reward Model for Balanced Safety Alignment** — [arxiv_cl](https://arxiv.org/abs/2605.30487)
- **Linear Ensembles Wash Away Watermarks: On the Fragility of Distributional Perturbations in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.30501)
- **Semantic Motion Anchors: Bridging Motion and Meaning in Co-Speech Gestures** — [arxiv_cl](https://arxiv.org/abs/2605.30608)
- **Same Patient, Different Words, Different Diagnosis? Evaluating Semantic Stability in Clinical LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.30646)
- **Human-Alignment, Calibration, and Activation Patterns in Large Language Model Uncertainty** — [arxiv_cl](https://arxiv.org/abs/2605.30675)
- **ElasticMem: Latent Memory as a Learnable Resource for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30690)
- **Neuron-Level Interventions for Gendered and Gender-Neutral Generation in Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30717)
- **Skill is Not One-Size-Fits-All: Model-Aware Skill Alignment for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30723)
- **MosaicLeaks:Privacy Risks in Querying-in-the-Open for Deep Research Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30727)
- **Pairwise Reference Alignment as a Model-Level Ordinal Observable** — [arxiv_cl](https://arxiv.org/abs/2605.30758)
- **Eywa: Provenance-Grounded Long-Term Memory for AI Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30771)
- **Anchoring LLM Gender Bias to Human Baselines: A Cross-Lingual Audit** — [arxiv_cl](https://arxiv.org/abs/2605.30804)
- **Our views on AI policy and political advocacy** — [openai](https://openai.com/index/our-views-on-ai-policy-and-political-advocacy)
- **Gemini’s new AI agent is about as good as Google’s demo** — [theverge_ai](https://www.theverge.com/tech/941138/google-gemini-spark-ai-agent-hands-on)
- **Alphabet plans to raise $80B to pay for AI buildout** — [techcrunch_ai](https://techcrunch.com/2026/06/01/alphabet-plans-to-raise-80-billion-to-pay-for-ai-buildout/)
- **This could be Windows’ M1 moment — but expect it to cost a ton** — [theverge_ai](https://www.theverge.com/tech/941215/windows-laptops-nvidia-rtx-spark-apple-m1-arm-price-ram)
- **Meta&#8217;s own AI was exploited to hijack Instagram accounts** — [theverge_ai](https://www.theverge.com/tech/941179/meta-instagram-ai-support-chatbot-exploit-hacked)
- **Anthropic has officially filed to go public** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/941016/anthropic-has-officially-filed-to-go-public)
- **Microsoft to unveil new AI models and Windows improvements at Build** — [theverge_ai](https://www.theverge.com/report/940861/microsoft-build-ai-models-windows-dev-mode-what-to-expect)
- **Anthropic files to go public** — [techcrunch_ai](https://techcrunch.com/2026/06/01/anthropic-files-to-go-public/)
- **This AI weather startup is out-forecasting government agencies** — [techcrunch_ai](https://techcrunch.com/2026/06/01/this-ai-weather-startup-is-out-forecasting-government-agencies/)
- **How we used Gemini to build Google I/O 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/io-2026-google-ai/)
- **Building the infrastructure for the Intelligence Age in Michigan** — [openai](https://openai.com/index/stargate-michigan-data-center)
- **AI is blowing up music. How should the Grammys handle it?** — [theverge_ai](https://www.theverge.com/podcast/940831/ai-grammys-music-recording-harvey-mason)
- **Strava blames zero-code AI apps and scrapers as it tightens API access** — [theverge_ai](https://www.theverge.com/gadgets/940854/strava-restricts-api-access-ai-apps)
- **The Download: China’s brain implant ambitions** — [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138207/the-download-china-bci-brain-implant-nvidia-ai-chips-laptops/)
- **OpenAI frontier models and Codex are now available on AWS** — [openai](https://openai.com/index/openai-frontier-models-and-codex-are-now-available-on-aws)
- **China has approved the world’s first invasive brain-computer chip—here’s what’s next** — [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138133/china-world-first-brain-chip/)
- **Nvidia chases $200B CPU market with AI agent PCs from Microsoft, Dell, and HP** — [techcrunch_ai](https://techcrunch.com/2026/06/01/nvidia-chases-200b-cpu-market-with-ai-agent-pcs-from-microsoft-dell-and-hp/)
- **Florida sues OpenAI, Sam Altman, in first-of-its-kind lawsuit over violent incidents** — [techcrunch_ai](https://techcrunch.com/2026/06/01/florida-sues-openai-sam-altman-in-first-of-its-kind-lawsuit-over-violent-incidents/)
- **Water access is now a risk factor in SpaceX’s IPO** — [techcrunch_ai](https://techcrunch.com/2026/06/01/water-access-is-now-a-risk-factor-in-spacexs-ipo/)
- **DuckDuckGo makes its ‘no-AI’ search engine easier to access as its traffic booms** — [techcrunch_ai](https://techcrunch.com/2026/06/01/duckduckgo-makes-its-no-ai-search-engine-easier-to-access-as-its-traffic-booms/)
- **MaxwellCCC/autonomous-qa-loop** — [github](https://github.com/MaxwellCCC/autonomous-qa-loop)
- **Caph-dev/agents-progressive-disclosure** — [github](https://github.com/Caph-dev/agents-progressive-disclosure)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **OttoRenner/Gentle-Coding** — [github](https://github.com/OttoRenner/Gentle-Coding)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **ATOM00blue/machine-learning-library** — [github](https://github.com/ATOM00blue/machine-learning-library)
- **openfi-dao/kalshi-trading-bot** — [github](https://github.com/openfi-dao/kalshi-trading-bot)
- **steeliron550-ui/search-bibtex** — [github](https://github.com/steeliron550-ui/search-bibtex)
- **modelstudioai/cli** — [github](https://github.com/modelstudioai/cli)
- **K-Dense-AI/science-superpowers** — [github](https://github.com/K-Dense-AI/science-superpowers)
- **veryyoldman/metamask-openclaw** — [github](https://github.com/veryyoldman/metamask-openclaw)
- **stormneonnightraven4640692/DeepFake-AI-RealTime** — [github](https://github.com/stormneonnightraven4640692/DeepFake-AI-RealTime)
- **JuneYaooo/nihaixia-tcm** — [github](https://github.com/JuneYaooo/nihaixia-tcm)
- **antigravity-cli-google/antigravity-cli** — [github](https://github.com/antigravity-cli-google/antigravity-cli)
- **Harkirat1462/claude-code-cli** — [github](https://github.com/Harkirat1462/claude-code-cli)
- **withkynam/vibecode-pro-max-kit** — [github](https://github.com/withkynam/vibecode-pro-max-kit)
- **sir1st/hermes-desktop** — [github](https://github.com/sir1st/hermes-desktop)
- **LLMQuant/skills** — [github](https://github.com/LLMQuant/skills)
- **konoeph/AgentClaimGuard** — [github](https://github.com/konoeph/AgentClaimGuard)
- **madhvantyagi/SOUL.md** — [github](https://github.com/madhvantyagi/SOUL.md)
- **AI Loss of Control Incident Management: Response & Resilience** — [arxiv_cy](https://arxiv.org/abs/2605.30406)
- **The Global Landscape of Environmental AI Regulation: From the Cost of Reasoning to a Right to Green AI** — [arxiv_cy](https://arxiv.org/abs/2603.00068)
- **老黄的Token经济学翻车了！微软亚马逊通通跳车** — [qbitai](https://www.qbitai.com/2026/06/427541.html)
- **清智系企业亮相 BEYOND Expo 2026 并斩获多项大奖** — [qbitai](https://www.qbitai.com/2026/06/427530.html)
- **近2亿美元！VAST完成新一轮融资，正式披露世界模型路线** — [qbitai](https://www.qbitai.com/2026/06/427516.html)
- **今天起，无限期免费！全球首个全模态API开放，Top 10 AI Lab出手** — [qbitai](https://www.qbitai.com/2026/06/427332.html)
- **OpenAI重返机器人赛道！四大核心岗位开招** — [qbitai](https://www.qbitai.com/2026/06/427238.html)
- **Token贵只因你喂给模型的垃圾太多了丨@亚马逊王晓野AIGC2026** — [qbitai](https://www.qbitai.com/2026/06/427141.html)
- **材料版AlphaFold来了！40个工业任务全方位SOTA，AI4S迎来行业大突破** — [qbitai](https://www.qbitai.com/2026/06/427142.html)
- **Vision-Language Models Suppress Female Representations Under Ambiguous Input** — [arxiv_cy](https://arxiv.org/abs/2605.31556)
- **The Refutability Gap: Challenges in Validating Reasoning by Large Language Models** — [arxiv_cy](https://arxiv.org/abs/2601.02380)
- **Certified Circuits: Stability Guarantees for Mechanistic Circuits** — [arxiv_cy](https://arxiv.org/abs/2602.22968)
- **Assessing Predictive Models for Fairness Based on Movement Patterns** — [arxiv_cy](https://arxiv.org/abs/2605.23234)
- **Routing on the Stiefel Manifold: When Does Adaptive Subspace Selection Help for Cross-Domain EEG Decoding?** — [arxiv_ml](https://arxiv.org/abs/2605.31043)
- **Entropic Projection Alignment: Estimating, Explaining, and Improving Model Performance Under Distribution Shift** — [arxiv_ml](https://arxiv.org/abs/2605.31250)
- **On public and private binary classification with metric space valued predictors** — [arxiv_ml](https://arxiv.org/abs/2605.31184)
- **Beyond Additive Decompositions: Interpretability Through Separability** — [arxiv_ml](https://arxiv.org/abs/2605.31200)
- **Adversarial Robustness in One-Stage Learning-to-Defer** — [arxiv_ml](https://arxiv.org/abs/2510.10988)
- **A hitchhiker's guide to Poisson gradient estimation** — [arxiv_ml](https://arxiv.org/abs/2602.03896)
- **德系精工邂逅中国智慧 全新奥迪Q5L现已登陆全国门店** — [qbitai](https://www.qbitai.com/2026/06/427231.html)
- **The Tutoring Effectiveness Index: Predicting LLM Math Tutor Quality from Four Conversation Signals** — [arxiv_cy](https://arxiv.org/abs/2605.30666)
- **How Early Adopters Used Generative AI Worldwide: Variation by Country Income and Language** — [arxiv_cy](https://arxiv.org/abs/2605.30685)
- **Traceable by Design: An LLM Pipeline and Dashboard for EU Regulatory Consultation Analysis** — [arxiv_cy](https://arxiv.org/abs/2605.30995)
- **Context-Conditioned Generative Models Enable Subnational Refinement of Sparse Humanitarian Surveys** — [arxiv_cy](https://arxiv.org/abs/2605.31489)
- **TUX: Measuring Human--AI Tacit Understanding** — [arxiv_cy](https://arxiv.org/abs/2605.30930)
- **Governance-Aware Software Architecture for Multi-Stakeholder Platforms** — [arxiv_cy](https://arxiv.org/abs/2605.31316)
- **Multi-Level Barriers to Generative AI Adoption Across Disciplines and Professional Roles in Higher Education** — [arxiv_cy](https://arxiv.org/abs/2603.27052)
- **Who, Why, and How: Disentangling the Effects of Moderation Source, Context, and Language on Post-Removal Behavior** — [arxiv_cy](https://arxiv.org/abs/2605.16204)
- **OLG++: A Semantic Extension of Obligation Logic Graph** — [arxiv_cy](https://arxiv.org/abs/2507.05488)
- **A Behavioural and Representational Evaluation of Goal-Directedness in Language Model Agents** — [arxiv_cy](https://arxiv.org/abs/2602.08964)
- **Memory by Design: Probabilistic Sequence Layers** — [arxiv_ml](https://arxiv.org/abs/2605.31163)
- **Physics-informed Goal-Conditioned Reinforcement Learning under Hybrid Contact Dynamics** — [arxiv_ml](https://arxiv.org/abs/2605.30503)
- **Kalimati Vegetable Price Index Forecasting with a Momentum Corrected Online Stacking Ensemble** — [arxiv_ml](https://arxiv.org/abs/2605.30720)
- **Bayesian Classification with Probit-link Split-and-merge Gaussian Process Prior in EEG-based Brain-Computer Interfaces** — [arxiv_ml](https://arxiv.org/abs/2605.30775)
- **Inspectable Neural Markov Models for Non-Stationary Time Series** — [arxiv_ml](https://arxiv.org/abs/2605.30943)
- **Convergence of Two-Timescale Markovian Stochastic Approximations with Applications in Reinforcement Learning** — [arxiv_ml](https://arxiv.org/abs/2605.31172)
- **Why Linear Recurrent Memory Works in Partially Observable Reinforcement Learning** — [arxiv_ml](https://arxiv.org/abs/2605.31261)
- **On the regularization of Wasserstein GANs** — [arxiv_ml](https://arxiv.org/abs/1709.08894)
- **Conformal C2ST: Turning weak classifiers into strong two-sample tests** — [arxiv_ml](https://arxiv.org/abs/2507.17026)
- **Outcome-Aware Spectral Feature Learning for Instrumental Variable Regression** — [arxiv_ml](https://arxiv.org/abs/2512.00919)
- **Learning-to-Defer with Expert-Conditional Advice** — [arxiv_ml](https://arxiv.org/abs/2603.14324)
- **Overview over the first decade of LIMITS** — [arxiv_cy](https://arxiv.org/abs/2605.30543)
- **Reinforcement Learning for Special Education: Aligning LLM Tutors to Diverse Learners through Disability-Adaptive Training** — [arxiv_cy](https://arxiv.org/abs/2605.30670)
- **Comparing LLM-Based Conversational and Graphical Interfaces for Industrial Decision Tasks: An Exploratory Mixed-Methods Study** — [arxiv_cy](https://arxiv.org/abs/2605.31224)
- **Neither Replacement nor Panacea: Comparing LLM-Based Conversational and Graphical Decision Support in Industrial Tasks** — [arxiv_cy](https://arxiv.org/abs/2605.31287)
- **Improved Distribution Estimation in $\ell_\infty$** — [arxiv_ml](https://arxiv.org/abs/2605.30509)
- **Reward Learning from Best-of-$N$ Preference Data: Targets, Tradeoffs, and Design Principles** — [arxiv_ml](https://arxiv.org/abs/2605.30619)
- **Is the Last Layer Sufficient for Uncertainty Quantification?** — [arxiv_ml](https://arxiv.org/abs/2605.30741)
- **36氪首发｜原小天才团队做老年硬件，切入居家看护赛道，即将进入海外市场** — [36kr](https://36kr.com/p/3835387558065541?f=rss)
- **前美团外卖技术负责人创业，做具身智能时代的“餐饮世界模型”** — [36kr](https://36kr.com/p/3834292242130825?f=rss)
- **中信证券：管网更新东风起，钢管板块迎价值重估** — [36kr](https://36kr.com/newsflashes/3835335100544130?f=rss)
- **8点1氪丨豆包将在6月下旬正式付费 ；韩国SK海力士工厂发生火灾；宇树科技IPO过会，王兴兴身家或超140亿** — [36kr](https://36kr.com/p/3835278829008257?f=rss)
- **首轮融资数千万美元、估值2.5亿美元，「Aippy」正在打造下一代AI游戏社区 | 36氪首发** — [36kr](https://36kr.com/p/3834400181741440?f=rss)
- **豆包6月下旬正式付费，并加速打通抖音电商丨独家** — [36kr](https://36kr.com/p/3834544830721671?f=rss)
- **量坤科技获数亿元天使轮融资，AI4S急需量子级精度数据 | 36氪独家** — [36kr](https://36kr.com/p/3826034537223043?f=rss)
- **氪星晚报｜中国国新等在杭州成立创业投资基金，出资额10.01亿；天津人工智能传感器产业园正式开园，首批10家企业集中签约；浙江：拟实施“星火计划”培育未来产业行动，加速量子技术产品规模化应用** — [36kr](https://36kr.com/p/3834354415347337?f=rss)
- **今年盛夏，WAVES之夜会浪的一群年轻人** — [36kr](https://36kr.com/p/3834276149356420?f=rss)
- **硬氪首发 | 获近2亿元融资，这家公司用无损Micro-LED加速AI眼镜全彩化进程** — [36kr](https://36kr.com/p/3834427736024965?f=rss)
- **我们有全世界最多的运动鞋，却没有一支值得爱20年的球队** — [36kr](https://36kr.com/p/3834297577383553?f=rss)
- **两市融资余额减少76.61亿元** — [36kr](https://36kr.com/newsflashes/3835318543971718?f=rss)
- **机构：2026年智能手机出货量预计同比下降13.9%** — [36kr](https://36kr.com/newsflashes/3835318280435077?f=rss)
- **腾讯控股短线拉升，现涨超3%** — [36kr](https://36kr.com/newsflashes/3835395233920131?f=rss)