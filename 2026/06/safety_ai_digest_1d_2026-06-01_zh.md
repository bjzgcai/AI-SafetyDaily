# AI 日报 [AI 安全] - 2026-06-01


# AI安全专题日报：2026年6月1日

## Highlights
今日，AI安全与对齐研究的图景呈现出深度与广度的双重拓展。在核心对齐理论层面，**Differentially Private Preference Data Synthesis for Large Language Model Alignment** 提出了一种新颖的差分隐私（Differentially Private）偏好数据合成框架DPPrefSyn，旨在为偏好对齐这一关键后训练步骤注入隐私保护能力，直面训练数据中的敏感信息泄露风险。与此同时，针对日益普及的LLM代理（Agent）系统，安全防御研究取得显著进展：**From Prompt Injection to Persistent Control: Defending Agentic Harness Against Trojan Backdoors** 深入剖析了代理工具链中多步骤特洛伊木马攻击的范式，并提出了防御框架；而 **TRACE: Task-Aware Adaptive Self-Evolving Agentic Jailbreaking** 则揭示了一种能自适应进化、规避安全对齐的智能体越狱攻击框架，凸显了代理系统面临的新威胁维度。此外，在隐私保护技术方面，关于 **Local Differential Privacy with Correlated Noise** 的理论突破以及面向GDPR合规的设备端视觉监控系统，均展示了将先进隐私计算理念向实际应用落地的努力。

## 1. 对抗攻击与鲁棒性：从视觉场景到语音生成

对抗性攻击研究持续向更复杂的现实场景渗透。在视觉领域，**AdvScene: Rethinking Adversarial Patch Evaluation Through Scene Robustness** 批评了现有对抗补丁评估方法的局限性，指出单次成功攻击不等于实际威胁，并提出了“场景鲁棒性”这一关键属性，即补丁在真实环境中跨视角、距离和场景变化的持续有效性。这呼吁评估体系从静态图像转向动态环境。在音频安全领域，**Escaping the Linearity Trap: Manifold Detours for Black-Box Adversarial Attacks on Singing Audio Deepfake Detection** 揭示了基于自监督学习（SSL）的歌声深度伪造检测器看似鲁棒的假象，并指出其源于优化目标层面的挑战。作者通过利用流形结构进行对抗性绕道，成功打破了这种线性陷阱，证明了现有高精度检测器仍存在脆弱性。两篇工作共同表明，对抗性鲁棒性评估必须紧密耦合于最终应用场景的复杂性，任何脱离上下文的“鲁棒性宣称”都需审慎对待。

## 2. 模型对齐、可解释性与欺骗性表示

对齐研究正从宏观目标深入到机制理解与数据基础。**Configurable Reward Model for Balanced Safety Alignment** 针对快速变化的异构安全需求，提出了可配置安全奖励模型（CSRM），通过配置目标数据增强和联合优化，使奖励模型能显式适配不同安全规范，提升了对齐的灵活性与可控性。在可解释性层面，**On the Relationship Between Activation Outliers and Feature Death in Sparse Autoencoders** 对稀疏自编码器（SAE）中普遍存在的“特征死亡”现象给出了机理性解释：维度级激活异常值（outliers）在初始化时即导致预激活偏移，从而决定了特征是否存活。这一发现为改进SAE训练、提升特征分解的有效性提供了理论依据。关于欺骗性对齐的前沿探索中，**When LLMs Learn to Be Consistently Wrong: A Multi-Model Study of Linear Representations of Synthetic Deception** 通过在多个Transformer模型上诱导合成欺骗行为，发现即使在输出错误时，模型内部仍维持着准确的表示。这为探测和防范更具风险的“战略性欺骗”提供了可控的实验测试平台。与之相关，**Linear Ensembles Wash Away Watermarks: On the Fragility of Distributional Perturbations in LLMs** 从理论上证明并实证表明，简单的模型集成平均操作即可轻易洗去水印，这揭示了当前基于分布扰动的水印技术在模型访问多元化的现实下的根本脆弱性。

## 3. 隐私保护、联邦学习与差分隐私创新

隐私保护技术正沿着理论深化与系统融合两个方向前进。在理论前沿，**Local Differential Privacy with Correlated Noise Achieves Central-DP Optimal Cost** 打破了传统认知，证明通过设计相关噪声机制，本地差分隐私（LDP）模型可以在聚合估计任务上达到与中央差分隐私（Central-DP）接近的效用成本，从而弥合了两种隐私模型之间的效用鸿沟。在系统层面，**Differentially Private Preference Data Synthesis for Large Language Model Alignment**（DPPrefSyn）将差分隐私与基于Bradley-Terry模型的偏好数据生成相结合，为LLM对齐提供了一个在隐私保护下合成高质量偏好数据的原则性框架。此外，**LLM Anonymization Against Agentic Re-Identification** 提出了AURA框架，专门应对由具备网络搜索能力的代理LLM带来的新威胁模型：弱上下文线索可能通过交叉引用构成再识别证据。AURA试图在抵抗此类代理再识别与保留文本分析效用之间寻找平衡。面向监管合规，**On-Device Generative AI for GDPR-Compliant Visual Monitoring** 展示了一个隐私设计（Privacy-by-Design）的端侧管道，所有推理在边缘设备完成，原始像素数据立即丢弃，仅输出自然语言警报，从而在架构层面践行数据最小化原则。

## 4. 安全评估、基准与衡量方法论

构建可靠、细粒度且符合伦理的评估体系成为当务之急。**PReMISE: Policy Rubrics as Measurement Specifications for LLM Judges** 提出将可复用的评估标准（rubric）视为“测量规范”，并开发了一个框架来从人类偏好数据中自动发现策略级评估标准集，并审计不同标准如何改变模型的测量结果。这使评估过程本身变得透明和可控。**EUDAIMONIA: Evaluating Undesirable Dynamics in AI** 则关注LLM在社交互动中可能产生的、超越传统安全与能力范畴的危害，如诱导有害亲密感或依赖性，并建立了相应的评估框架。在医疗等高风险领域，**EHRBench** 致力于构建自动化、可靠的临床决策基准，以评估LLM在真实、不完整证据下的推理可靠性。而在透明度评估上，**LLM-FACETS** 旨在降低审计门槛，为非技术背景的领域专家和合规官员提供一个保护隐私的、本地化的LLM透明度与问责评估工具。

## 5. Agent安全与治理：攻击、防御与系统架构

LLM代理的安全是本日焦点，研究覆盖了攻击、防御与系统性治理。在攻击层面，**TRACE** 框架展示了一种任务感知、自适应进化的代理越狱方法，它通过分解恶意意图、利用代码生成能力来规避安全对齐，并声称在多个基准上实现了高攻击成功率。**Depth-Dependent Indirect Prompt Injection in Tool-Calling ReAct Agents** 则系统研究了间接提示注入攻击在不同注入深度、有效载荷框架和轮次预算下的敏感性，为风险评估提供了更细致的维度。在防御与加固方面，**From Prompt Injection to Persistent Control** 揭示了多步骤特洛伊木马攻击范式：恶意指令通过文件或工具输出被注入，被代理存储并稍后执行。为此，防御需要超越单次查询检查。**Strengthening Polymorphic Prompt Assembling** 针对聚合式提示组装（PPA）防御中静态分隔符池易泄露的漏洞，提出了基于域分离哈希的动态逐请求分隔符生成，增强防御的密码学强度。在系统架构层面，**An Organization-Scoped LLM Agent Runtime Architecture for Regulated Cybersecurity Operations** 提出了一个面向受监管网络安全运营的、具有组织范围作用域的代理运行时架构，旨在统一管控检索、工具调用、记忆、审计等全链条，以满足合规性要求。这些工作共同描绘了一幅从细粒度漏洞利用到系统级安全架构的全景图。

## 6. 可解释性基础与模型内部机制

深入模型内部以理解其工作原理和失败模式，是安全可信的基石。**What Makes LVLMs Hallucinate Less? Unveiling the Architectural Factors Behind Hallucination Robustness** 从架构设计角度出发，将大型视觉语言模型（LVLMs）的幻觉分解为共现、相似性和幻觉三类，并系统剖析了语言基础、视觉表示和语义对齐三个架构维度如何影响幻觉的鲁棒性。这为设计更可靠模型提供了架构层面的指引。**Certified Circuits: Stability Guarantees for Mechanistic Circuits** 针对机制可解释性中电路发现方法脆弱、依赖特定数据集的问题，引入了“认证电路”的概念，旨在为电路提供可证明的稳定性保证，确保其发现的行为能够泛化，而非数据集伪影。而 **Learning to Adapt: Self-Improving Web Agent via Cognitive-Aware Exploration** 提出的SCALE框架，则通过让代理扮演选择器、预测者和评判者等多个对抗性角色，实现自我认知感知和边界拓展，这是一种提升代理鲁棒性和适应性的内在机制。

## 7. 治理、政策与伦理框架

AI治理框架的构建正从宏观呼吁走向具体化与操作化。**AI Loss of Control Incident Management: Response & Resilience** 首次系统性地提出了管理灾难性AI失控事件的框架和分类法，区分了“重新控制代价极高”与“不可能重新控制”两种情景，强调当前研究需从偏重预防，转向同时重视事件响应和韧性建设。**The Global Landscape of Environmental AI Regulation** 则聚焦于AI系统的环境成本，汇集了生成式AI能耗剧增的实证证据，并梳理了全球多个司法管辖区的监管现状，指出在环境影响透明度下降的同时，监管应对远未跟上技术发展。在评估伦理层面，**A Persona-Based Evaluation Framework for Pluralistic Alignment in Generative AI** 批评了将多元人类判断简化为聚合统计基线的单体评估范式，提出了一个基于合成认知人格的结构化流形评估框架，以容纳评估中的文化、人口统计学和情境多样性。

## Looking Forward

今日的多项工作揭示了若干亟待攻克的理论与实践问题。首先，代理系统的安全防御仍处于“矛与盾”的初级博弈阶段，**TRACE** 等攻击框架的成功表明，基于静态安全对齐和规则过滤的防御难以应对自适应的、利用代码生成的攻击者。如何构建可验证的、形式化的安全保证，特别是对于多步骤、跨上下文的代理行为，是一个根本性挑战。其次，**DPPrefSyn** 等工作尝试将隐私保护融入对齐流水线，但隐私、效用与对齐质量三者之间的理论边界和最优权衡点仍不清晰。此外，**Certified Circuits** 和 **AdvScene** 等工作共同指向一个方向：安全评估与可解释性发现需要从追求“相关性”转向追求“可证明的稳定性”与“场景泛化性”。最后，关于AI失控事件的管理框架 (**AI Loss of Control Incident Management**) 的提出，标志着社区开始严肃思考当最坏情况发生时的技术与社会应对预案，但这方面的研究、演练和全球协调机制几乎是一片空白，亟需跨学科合作与投入。

---


## 参考来源

- **Organizational Adaptation to Generative AI in Cybersecurity** — [arxiv_cr](https://arxiv.org/abs/2506.12060)
- **When AI Meets Wall Street: A Survey on Trustworthy AI in Fintech** — [arxiv_cr](https://arxiv.org/abs/2605.30650)
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
- **Equivariant Latent Alignment via Flow Matching under Group Symmetries** — [arxiv_cv](https://arxiv.org/abs/2605.30705)
- **What Makes LVLMs Hallucinate Less? Unveiling the Architectural Factors Behind Hallucination Robustness** — [arxiv_cv](https://arxiv.org/abs/2605.30911)
- **Evaluating using Mock Tool Calls to Quarantine Untrusted Prompt Inputs** — [arxiv_cl](https://arxiv.org/abs/2605.30521)
- **ImmigrationQA: A Source-Grounded Dataset and Small-Model Adaptation for U.S. Immigration Law** — [arxiv_cl](https://arxiv.org/abs/2605.30589)
- **COFT: Counterfactual-Conformal Decoding for Fair Chain-of-Thought Reasoning in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30641)
- **EUDAIMONIA: Evaluating Undesirable Dynamics in AI** — [arxiv_cl](https://arxiv.org/abs/2605.30654)
- **The Flip Side of RLHF: On-Policy Feedback for Reward Model Self-Supervised Improvement** — [arxiv_cl](https://arxiv.org/abs/2605.30888)
- **Giving Sensors a Voice: Multimodal JEPA for Semantic Time-Series Embeddings** — [arxiv_lg](https://arxiv.org/abs/2605.31580v1)
- **On the Relationship Between Activation Outliers and Feature Death in Sparse Autoencoders** — [arxiv_lg](https://arxiv.org/abs/2605.31518v1)
- **The Surface You Test Is Not the Surface That Breaks** — [arxiv_cr](https://arxiv.org/abs/2605.30454)
- **Strengthening Polymorphic Prompt Assembling: Dynamic Separator Generation Against Emerging Prompt Injection Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.30534)
- **An Organization-Scoped LLM Agent Runtime Architecture for Regulated Cybersecurity Operations** — [arxiv_cr](https://arxiv.org/abs/2605.30604)
- **Depth-Dependent Indirect Prompt Injection in Tool-Calling ReAct Agents: Injection Depth, Payload Framing, and Turn-Budget Sensitivity** — [arxiv_cr](https://arxiv.org/abs/2605.30686)
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
- **LongTraceRL: Learning Long-Context Reasoning from Search Agent Trajectories with Rubric Rewards** — [arxiv_lg](https://arxiv.org/abs/2605.31584v1)
- **Positional versus Symbolic Attention Heads: Learning Dynamics, RoPE Geometry, and Length Generalization** — [arxiv_lg](https://arxiv.org/abs/2605.31558v1)
- **Discovering Thermodynamically Admissible Dissipation Potentials via Grammar-Based Symbolic Regression** — [arxiv_lg](https://arxiv.org/abs/2605.31532v1)
- **Value Functions as Supermartingale Certificates** — [arxiv_lg](https://arxiv.org/abs/2605.31524v1)
- **DRIFT: Decoupled Rollouts and Importance-Weighted Fine-Tuning for Efficient Multi-Turn Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.31455v1)
- **DG-CoLearn: An Efficient Collaborative Learning Framework for Dynamic Graphs** — [arxiv_lg](https://arxiv.org/abs/2605.31427v1)
- **Skill Availability and Presentation Granularity in Large-Language-Model Agents: A Controlled SkillsBench Study** — [arxiv_lg](https://arxiv.org/abs/2605.31408v1)
- **Constrained Multi-Objective Reinforcement Learning with Max-Min Criterion** — [arxiv_lg](https://arxiv.org/abs/2605.31388v1)
- **Scaling Higher-Order Graph Learning with Maximal Clique Complexes** — [arxiv_lg](https://arxiv.org/abs/2605.31373v1)
- **dashi: A Python library for Dataset Shift Characterization to Support Trustworthy AI Development and Deployment** — [arxiv_lg](https://arxiv.org/abs/2605.31360v1)
- **KLIP: localized distribution shift detection via KL-divergence with diffusion priors in Inverse Problems** — [arxiv_lg](https://arxiv.org/abs/2605.31596v1)
- **A Tight Theory of Error Feedback Algorithms in Distributed Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.31594v1)
- **Effective Biological Representation Learning by Masking Gene Expression** — [arxiv_lg](https://arxiv.org/abs/2605.31562v1)
- **Functional Attention: From Pairwise Affinities to Functional Correspondences** — [arxiv_lg](https://arxiv.org/abs/2605.31559v1)
- **The Dynamic-Probabilistic Consistency Gap in Chaotic Surrogate Modeling** — [arxiv_lg](https://arxiv.org/abs/2605.31547v1)
- **Automated Prediction of Postoperative Pancreatic Fistula Using Preoperative Computed Tomography** — [arxiv_lg](https://arxiv.org/abs/2605.31539v1)
- **RayDer: Scalable Self-Supervised Novel View Synthesis from Real-World Video** — [arxiv_lg](https://arxiv.org/abs/2605.31535v1)
- **Chem-PerturBridge: a harmonized compendium of small molecule perturbation transcriptomic effects** — [arxiv_lg](https://arxiv.org/abs/2605.31522v1)
- **The Download: China’s brain implant ambitions** — [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138207/the-download-china-bci-brain-implant-nvidia-ai-chips-laptops/)
- **China has approved the world’s first invasive brain-computer chip—here’s what’s next** — [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138133/china-world-first-brain-chip/)
- **Making sense of the debate over AI psychosis** — [techcrunch_ai](https://techcrunch.com/2026/05/31/making-sense-of-the-debate-over-ai-psychosis/)
- **Erin Brockovich takes aim at data center secrecy** — [techcrunch_ai](https://techcrunch.com/2026/05/31/erin-brockovich-takes-aim-at-data-center-secrecy/)
- **MaxwellCCC/autonomous-qa-loop** — [github](https://github.com/MaxwellCCC/autonomous-qa-loop)
- **ali-vilab/DiffusionOPD** — [github](https://github.com/ali-vilab/DiffusionOPD)
- **Caph-dev/agents-progressive-disclosure** — [github](https://github.com/Caph-dev/agents-progressive-disclosure)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **OttoRenner/Gentle-Coding** — [github](https://github.com/OttoRenner/Gentle-Coding)
- **stormneonnightraven4640692/DeepFake-AI-RealTime** — [github](https://github.com/stormneonnightraven4640692/DeepFake-AI-RealTime)
- **ATOM00blue/machine-learning-library** — [github](https://github.com/ATOM00blue/machine-learning-library)
- **JuneYaooo/nihaixia-tcm** — [github](https://github.com/JuneYaooo/nihaixia-tcm)
- **openfi-dao/kalshi-trading-bot** — [github](https://github.com/openfi-dao/kalshi-trading-bot)
- **steeliron550-ui/search-bibtex** — [github](https://github.com/steeliron550-ui/search-bibtex)
- **modelstudioai/cli** — [github](https://github.com/modelstudioai/cli)
- **K-Dense-AI/science-superpowers** — [github](https://github.com/K-Dense-AI/science-superpowers)
- **antigravity-cli-google/antigravity-cli** — [github](https://github.com/antigravity-cli-google/antigravity-cli)
- **veryyoldman/metamask-openclaw** — [github](https://github.com/veryyoldman/metamask-openclaw)
- **Harkirat1462/claude-code-cli** — [github](https://github.com/Harkirat1462/claude-code-cli)
- **withkynam/vibecode-pro-max-kit** — [github](https://github.com/withkynam/vibecode-pro-max-kit)
- **kurikomi-labs/komi-learn** — [github](https://github.com/kurikomi-labs/komi-learn)
- **LLMQuant/skills** — [github](https://github.com/LLMQuant/skills)
- **madhvantyagi/SOUL.md** — [github](https://github.com/madhvantyagi/SOUL.md)
- **duncatzat/vigils** — [github](https://github.com/duncatzat/vigils)
- **AI Loss of Control Incident Management: Response & Resilience** — [arxiv_cy](https://arxiv.org/abs/2605.30406)
- **The Global Landscape of Environmental AI Regulation: From the Cost of Reasoning to a Right to Green AI** — [arxiv_cy](https://arxiv.org/abs/2603.00068)
- **Vision-Language Models Suppress Female Representations Under Ambiguous Input** — [arxiv_cy](https://arxiv.org/abs/2605.31556)
- **The Refutability Gap: Challenges in Validating Reasoning by Large Language Models** — [arxiv_cy](https://arxiv.org/abs/2601.02380)
- **Certified Circuits: Stability Guarantees for Mechanistic Circuits** — [arxiv_cy](https://arxiv.org/abs/2602.22968)
- **Assessing Predictive Models for Fairness Based on Movement Patterns** — [arxiv_cy](https://arxiv.org/abs/2605.23234)
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
- **Overview over the first decade of LIMITS** — [arxiv_cy](https://arxiv.org/abs/2605.30543)
- **Reinforcement Learning for Special Education: Aligning LLM Tutors to Diverse Learners through Disability-Adaptive Training** — [arxiv_cy](https://arxiv.org/abs/2605.30670)
- **Comparing LLM-Based Conversational and Graphical Interfaces for Industrial Decision Tasks: An Exploratory Mixed-Methods Study** — [arxiv_cy](https://arxiv.org/abs/2605.31224)
- **Neither Replacement nor Panacea: Comparing LLM-Based Conversational and Graphical Decision Support in Industrial Tasks** — [arxiv_cy](https://arxiv.org/abs/2605.31287)
- **存量公募基金今起调整基准，业内人士：不会引发基金调仓** — [36kr](https://36kr.com/newsflashes/3834619683991685?f=rss)
- **美团电话会：预期Q2外卖UE会明显好于Q1** — [36kr](https://36kr.com/newsflashes/3834586508915080?f=rss)
- **豆包6月下旬正式付费，并加速打通抖音电商丨独家** — [36kr](https://36kr.com/p/3834544830721671?f=rss)
- **量坤科技获数亿元天使轮融资，AI4S急需量子级精度数据 | 36氪独家** — [36kr](https://36kr.com/p/3826034537223043?f=rss)
- **氪星晚报｜中国国新等在杭州成立创业投资基金，出资额10.01亿；天津人工智能传感器产业园正式开园，首批10家企业集中签约；浙江：拟实施“星火计划”培育未来产业行动，加速量子技术产品规模化应用** — [36kr](https://36kr.com/p/3834354415347337?f=rss)
- **今年盛夏，WAVES之夜会浪的一群年轻人** — [36kr](https://36kr.com/p/3834276149356420?f=rss)
- **硬氪首发 | 获近2亿元融资，这家公司用无损Micro-LED加速AI眼镜全彩化进程** — [36kr](https://36kr.com/p/3834427736024965?f=rss)
- **我们有全世界最多的运动鞋，却没有一支值得爱20年的球队** — [36kr](https://36kr.com/p/3834297577383553?f=rss)
- **「AromeManpo馥郁满铺」完成近亿元B轮融资，今年线下门店将突破10家** — [36kr](https://36kr.com/p/3832924137138057?f=rss)
- **连续完成五源、峰瑞两轮数千万元融资，清华00后团队要解决Token账单焦虑｜智能涌现首发** — [36kr](https://36kr.com/p/3834310434875011?f=rss)
- **获国家队采购、联名比音勒芬，「PLAYTOP」想用东方美学演绎户外功能服饰｜早期项目** — [36kr](https://36kr.com/p/3824416083825027?f=rss)
- **硬氪观察 | 苹果代工厂开造人形机器人，一场豪赌未来的产能大迁移** — [36kr](https://36kr.com/p/3833985105782402?f=rss)
- **热门中概股美股盘前涨跌不一，哔哩哔哩涨超4%** — [36kr](https://36kr.com/newsflashes/3834618025193857?f=rss)
- **美股大型科技股盘前涨跌不一，Arm涨超10%** — [36kr](https://36kr.com/newsflashes/3834615865684101?f=rss)
- **Quantinuum现预计IPO发行价为每股53至55美元，筹集至多14.6亿美元** — [36kr](https://36kr.com/newsflashes/3834607891345537?f=rss)
- **有研复材：拟投资1.5亿元建设先进金属基复合材料产业化项目** — [36kr](https://36kr.com/newsflashes/3834603846987913?f=rss)
- **美团电话会：“小美”与腾讯“元宝”的合作将于近期上线** — [36kr](https://36kr.com/newsflashes/3834584241287552?f=rss)
- **Strategy首次披露出售比特币，卖出32枚BTC套现250万美元** — [36kr](https://36kr.com/newsflashes/3834573955821705?f=rss)
- **“无界进化”完成数千万元天使轮融资** — [36kr](https://36kr.com/newsflashes/3834567980085632?f=rss)
- **美国软件公司Hyland宣布与微软合作，以支持代理式企业的发展** — [36kr](https://36kr.com/newsflashes/3834606950723968?f=rss)