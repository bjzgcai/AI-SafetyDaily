# AI 日报 [AI 安全] - 2026-05-06


# 2026-05-06 AI 安全与治理每日综述

## 亮点

当日最核心的学术与政策进展集中在 Agent 结构性安全评估、隐私计算的理论边界以及跨国监管合作机制上。首先，美国商务部人工智能标准与创新中心（CAISI）宣布与 Google DeepMind、Microsoft 和 xAI 达成协议，允许政府在模型发布前进行审查，这一政策动向标志着 AI 治理从自愿承诺转向实质性预部署评估。其次，**MOSAIC-Bench** 的发布揭示了编码 Agent 在任务分解下的结构性漏洞，指出安全对齐在单步审查中有效，但在多步序列任务中可能失效。第三，隐私计算领域出现理论突破，**CorrDP** 提出了特征相关性感知的差分隐私定义，而 **PRIVX** 攻击则证明了差分隐私保护下的图神经网络解释仍可能泄露隐藏结构，这两项工作共同划定了当前隐私保护技术的理论边界。此外，OpenAI 声称其 **GPT-5.5 Instant** 模型在敏感领域的幻觉率降低了 52.5%，但需注意该数据基于内部评估，尚未经过独立基准验证。

## 对抗攻击与鲁棒性

当前对抗攻击研究正从单轮提示转向多轮上下文与跨模态的深层诱导。**ContextualJailbreak** 提出了一种基于进化红队测试的方法，通过模拟对话预热来优化多轮攻击，证明了手写的多轮脚手架在能力较强的模型上持续优于单轮操纵。这一发现与 **Revisiting JBShield** 的研究形成对比，后者指出针对 JBShield 防御机制的自适应攻击（JB-GCG）可以通过结合拒绝方向抑制和毒性概念信号来绕过检测。在物理侧信道方面，**DECKER** 引入了 HEAR 数据集，展示了声学侧信道攻击在跨设备、跨噪声条件下的泛化能力，表明现有的防御措施在小规模数据集上可能高估了鲁棒性。针对网页层面的隐私泄露，**PIIGuard** 提出了一种利用间接提示注入作为保护机制的防御方案，允许网页所有者嵌入隐藏的 HTML 片段以引导模型避开敏感信息的提取。此外，**Exposing LLM Safety Gaps** 揭示了数学编码攻击的有效性，通过将有害提示编码为集合论或量子力学问题，攻击者能够绕过依赖语义模式匹配的安全过滤器，这表明当前的防御机制在形式化推理层面存在盲区。

## 模型对齐与可解释性

在模型对齐与可解释性领域，研究重点正从单一模型行为转向分布式智能系统的整体可靠性。**Mechanical Conscience** 提出了一个数学框架，用于评估分布式协作智能（DCI）的依赖性，指出局部正确的决策在不确定性下可能组合成全局不可接受的行为轨迹，现有的安全强化学习未能解决这一多参与者问题。**TRACE** 框架则针对运营关键领域的可信 Agent 系统，结合了四层参考架构与度量学基础信任指标，强调在临床、工业和司法场景中需要显式的经典机器学习与 LLM 验证器分离。在安全微调方面，**Self-Mined Hardness** 提出了一种利用模型自身输出难度进行微调的方法，通过筛选最难提示来降低越狱成功率，但实验显示这可能导致对良性提示的过度拒绝。可解释性工具方面，**Agentic-imodels** 引入了自主研究循环，进化出 Agent 可解释的数据科学工具，而非仅面向人类解释，这为 Agent 系统的自我监控提供了新方向。此外，**Task Vector Geometry** 的研究试图从数学角度解释 Transformer 中的任务向量几何，为理解模型如何适应新任务提供了理论基础。

## 隐私保护与数据安全

隐私保护研究在理论定义与实际攻击之间呈现出显著的张力。**Integrating Feature Correlation in Differential Privacy** 引入了 **CorrDP**，允许在考虑特征相关性的情况下放松对非敏感特征的隐私约束，旨在平衡效用与隐私。然而，**Graph Reconstruction from Differentially Private GNN Explanations** 展示了 **PRIVX** 攻击，表明即使发布差分隐私保护的图神经网络解释，攻击者仍可能高精度重构隐藏图结构，这挑战了当前监管框架对解释性发布的隐私假设。在 Agent 交互中，**Dependency-Aware Privacy** 指出多轮 Agent 交互中的隐私会随着每次发布而退化，独立噪声处理无法保护作为计算图根节点的私有属性。针对联邦学习，**Distributed Deep Variational Approach** 提出了高斯隐私保护器（GPP），通过随机编码器将原始数据映射为低维清洗表示，以缓解梯度泄露风险。在数据估值领域，**ZK-Value** 构建了一个实用的零知识证明系统，旨在解决数据市场中隐私与可验证性之间的冲突，使外部审计者能够验证 Shapley 值分配而无需接触底层私有数据。

## 安全评估基准

安全评估基准的构建正从静态知识问答转向动态、长周期的任务执行验证。**MOSAIC-Bench** 包含 199 个三阶段攻击链，旨在评估编码 Agent 在分解任务中的结构性脆弱性，指出安全对齐在孤立请求中有效，但在序列合规中可能失效。**TriBench-Ko** 则专注于韩国司法工作流，评估 LLM 在真实法律任务中的风险，弥补了现有基准仅关注代理任务（如法律考试）的不足。**PhysicianBench** 引入了基于真实电子健康记录（EHR）环境的 Agent 评估，涵盖长周期、复合工作流，解决了现有医疗 Agent 基准仅关注静态知识召回的问题。**Validated Prompt Bank** 则通过五模型共识协议，将恶意代码生成的提示分为可执行武器与安全知识两类，旨在分离不同的拒绝路径。此外，**HackerSignal** 提供了跨源 CVE 链接的威胁情报基准，涵盖了从黑客社区讨论到漏洞利用的完整生命周期，为动态威胁检测提供了数据基础。

## Agent 安全与治理工具

开源社区正在涌现一系列针对 Agent 安全与治理的工具框架。**Aegis** 提供了一种架构驱动的开发方法包，强调证据驱动的工作流和双重治理轨道，旨在提升 AI 编码的严谨性。**goblintown** 实现了多 Agent 编排协议，通过内容寻址和漂移监控来管理 Agent 任务执行。**agent-safety-eval-lab** 专注于 Agent 轨迹和工具使用的安全评估实验室，为安全测试提供了基础设施。在架构设计方面，**Stable Agentic Control** 提出了工具介导的 LLM 架构，使用确定性工具（如 Stackelberg 最佳响应）和有限动作目录，通过 Lean 4 机器验证的复合 Lyapunov 函数提供形式化保证。**ARGUS** 则专门防御上下文感知的提示注入攻击，弥补了现有防御在真实部署中缺乏上下文感知的缺陷。**MEMTIER** 针对长运行 Agent 的内存一致性提出了分层架构，通过异步合并守护进程和基于 PPO 的策略框架来解决工具执行成功率随时间下降的问题。

## 产业动态与政策

产业界与法律层面的动态反映了 AI 治理的复杂化。**Apple** 同意向 iPhone 用户支付 2.5 亿美元以解决关于 AI Siri 功能延迟发布的集体诉讼，这确立了关于 AI 功能承诺的法律先例。同时，**Musk 与 Altman** 关于 OpenAI 未来的法庭辩论进入关键阶段，可能重塑 AI 公司的治理结构。**SAP** 宣布收购德国 AI 初创公司 Prior Labs 并投资 11.6 亿美元，同时限制客户 Agent 使用特定平台，显示出企业级 AI 部署中的生态锁定趋势。在硬件方面，**Rivian** 透露投入数亿美元自研自动驾驶芯片，表明自动驾驶领域正试图通过垂直整合来增强安全性。此外，**OpenAI** 发布了 **GPT-5.5 Instant** 的系统卡片，声称在事实性方面有显著改进，但行业观察者需警惕此类内部评估结果与独立基准之间的差异。

## 展望

尽管上述工作在对抗攻击、隐私理论和 Agent 治理方面取得了进展，但若干理论问题仍未解决。首先，如何在分布式协作智能（DCI）中形式化地定义全局行为的可接受性，目前 **Mechanical Conscience** 仅提供了框架，缺乏具体的验证算法。其次，差分隐私在解释性发布中的安全性边界尚不清晰，**PRIVX** 攻击表明现有的隐私预算参数可能不足以防御针对解释结构的推理攻击。最后，Agent 的长周期运行中的内存一致性与安全策略的动态更新机制仍缺乏统一的理论模型，**MEMTIER** 和 **TRACE** 提供了工程方案，但尚未形成通用的形式化验证标准。未来的研究需要进一步打通理论证明与实际部署之间的鸿沟，特别是在多 Agent 交互和跨模态安全领域。

---


## 参考来源

- **Mechanical Conscience: A Mathematical Framework for Dependability of Machine Intelligenc** — [arxiv_ai](https://arxiv.org/abs/2605.03847v1)
- **ContextualJailbreak: Evolutionary Red-Teaming via Simulated Conversational Priming** — [arxiv_cr](https://arxiv.org/abs/2605.02647v1)
- **DECKER: Domain-invariant Embedding for Cross-Keyboard Extraction and Recognition** — [arxiv_cr](https://arxiv.org/abs/2605.03384v1)
- **BIT.UA-AAUBS at ArchEHR-QA 2026: Evaluating Open-Source and Proprietary LLMs via Prompting in Low-Resource QA** — [arxiv_cl](https://arxiv.org/abs/2605.03618v1)
- **PIIGuard: Mitigating PII Harvesting under Adversarial Sanitization** — [arxiv_cr](https://arxiv.org/abs/2605.03129v1)
- **MOSAIC-Bench: Measuring Compositional Vulnerability Induction in Coding Agents** — [arxiv_ai](https://arxiv.org/abs/2605.03952v1)
- **Contextual Multi-Objective Optimization: Rethinking Objectives in Frontier AI Systems** — [arxiv_ai](https://arxiv.org/abs/2605.03900v1)
- **TRACE: A Metrologically-Grounded Engineering Framework for Trustworthy Agentic AI Systems in Operationally Critical Domains** — [arxiv_ai](https://arxiv.org/abs/2605.03838v1)
- **Integrating Feature Correlation in Differential Privacy with Applications in DP-ERM** — [arxiv_lg](https://arxiv.org/abs/2605.03945v1)
- **Agent-Based Modeling of Low-Emission Fertilizer Adoption for Dairy Farm Decarbonisation using Empirical Farm Data** — [arxiv_ai](https://arxiv.org/abs/2605.03648v1)
- **Graph Reconstruction from Differentially Private GNN Explanations** — [arxiv_cr](https://arxiv.org/abs/2605.03388v1)
- **FINER-SQL: Boosting Small Language Models for Text-to-SQL** — [arxiv_cl](https://arxiv.org/abs/2605.03465v1)
- **LLM-XTM: Enhancing Cross-Lingual Topic Models with Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.03299v1)
- **Self-Mined Hardness for Safety Fine-Tuning** — [arxiv_cr](https://arxiv.org/abs/2605.03226v1)
- **Dependency-Aware Privacy for Multi-turn Agents** — [arxiv_cr](https://arxiv.org/abs/2605.03188v1)
- **Revisiting JBShield: Breaking and Rebuilding Representation-Level Jailbreak Defenses** — [arxiv_cr](https://arxiv.org/abs/2605.03095v1)
- **Distributed Deep Variational Approach for Privacy-preserving Data Release** — [arxiv_cr](https://arxiv.org/abs/2605.03069v1)
- **Stable Agentic Control: Tool-Mediated LLM Architecture for Autonomous Cyber Defense** — [arxiv_cr](https://arxiv.org/abs/2605.03034v1)
- **VertMark: A Unified Training-Free Robust Watermarking Framework for Vertical Domain Pre-trained Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.02557v1)
- **Perceptual Flow Network for Visually Grounded Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.02730)
- **Feature-Augmented Transformers for Robust AI-Text Detection Across Domains and Generators** — [arxiv_ai](https://arxiv.org/abs/2605.03969v1)
- **Magic-Informed Quantum Architecture Search** — [arxiv_ai](https://arxiv.org/abs/2605.03932v1)
- **PHALAR: Phasors for Learned Musical Audio Representations** — [arxiv_ai](https://arxiv.org/abs/2605.03929v1)
- **Atomic Fact-Checking Increases Clinician Trust in Large Language Model Recommendations for Oncology Decision Support: A Randomized Controlled Trial** — [arxiv_ai](https://arxiv.org/abs/2605.03916v1)
- **DMGD: Train-Free Dataset Distillation with Semantic-Distribution Matching in Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2605.03877v1)
- **EvoLM: Self-Evolving Language Models through Co-Evolved Discriminative Rubrics** — [arxiv_ai](https://arxiv.org/abs/2605.03871v1)
- **Quantifying the human visual exposome with vision language models** — [arxiv_ai](https://arxiv.org/abs/2605.03863v1)
- **RoboAlign-R1: Distilled Multimodal Reward Alignment for Robot Video World Models** — [arxiv_ai](https://arxiv.org/abs/2605.03821v1)
- **Agentic-imodels: Evolving agentic interpretability tools via autoresearch** — [arxiv_ai](https://arxiv.org/abs/2605.03808v1)
- **Say the Mission, Execute the Swarm: Agent-Enhanced LLM Reasoning in the Web-of-Drones** — [arxiv_ai](https://arxiv.org/abs/2605.03788v1)
- **HELO Cryptography: A Lightweight Cryptographic System for Enhancing IoT Security in P2P Data Transmission** — [arxiv_cr](https://arxiv.org/abs/2605.03948v1)
- **Firmware Distribution as Attack Surface: A Security Study of ASIC Cryptocurrency Miners** — [arxiv_cr](https://arxiv.org/abs/2605.03770v1)
- **TriBench-Ko: Evaluating LLM Risks in Judicial Workflows** — [arxiv_cl](https://arxiv.org/abs/2605.03792v1)
- **Task Vector Geometry Underlies Dual Modes of Task Inference in Transformers** — [arxiv_cl](https://arxiv.org/abs/2605.03780v1)
- **Optimal Posterior Sampling for Policy Identification in Tabular Markov Decision Processes** — [arxiv_lg](https://arxiv.org/abs/2605.03921v1)
- **Ecologically-Constrained Task Arithmetic for Multi-Taxa Bioacoustic Classifiers Without Shared Data** — [arxiv_lg](https://arxiv.org/abs/2605.03914v1)
- **Raising the Ceiling: Better Empirical Fixation Densities for Saliency Benchmarking** — [arxiv_lg](https://arxiv.org/abs/2605.03885v1)
- **On Adaptivity in Zeroth-Order Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.03869v1)
- **Nora: Normalized Orthogonal Row Alignment for Scalable Matrix Optimizer** — [arxiv_lg](https://arxiv.org/abs/2605.03769v1)
- **OracleProto: A Reproducible Framework for Benchmarking LLM Native Forecasting via Knowledge Cutoff and Temporal Masking** — [arxiv_ai](https://arxiv.org/abs/2605.03762v1)
- **Before Forgetting, Learn to Remember: Revisiting Foundational Learning Failures in LVLM Unlearning Benchmarks** — [arxiv_ai](https://arxiv.org/abs/2605.03759v1)
- **Rethinking the Rank Threshold for LoRA Fine-Tuning** — [arxiv_ai](https://arxiv.org/abs/2605.03724v1)
- **SERE: Structural Example Retrieval for Enhancing LLMs in Event Causality Identification** — [arxiv_ai](https://arxiv.org/abs/2605.03701v1)
- **MEMTIER: Tiered Memory Architecture and Retrieval Bottleneck Analysis for Long-Running Autonomous AI Agents** — [arxiv_ai](https://arxiv.org/abs/2605.03675v1)
- **ZK-Value: A Practical Zero-Knowledge System for Verifiable Data Valuation** — [arxiv_cr](https://arxiv.org/abs/2605.03581v1)
- **ARGUS: Defending LLM Agents Against Context-Aware Prompt Injection** — [arxiv_cr](https://arxiv.org/abs/2605.03378v1)
- **Cryptographic Registry Provenance: Structural Defense Against Dependency Confusion in AI Package Ecosystems** — [arxiv_cr](https://arxiv.org/abs/2605.03309v1)
- **Detecting Stealth Sycophancy in Mental-Health Dialogue with Dynamic Emotional Signature Graphs** — [arxiv_cl](https://arxiv.org/abs/2605.03472v1)
- **Exposing LLM Safety Gaps Through Mathematical Encoding:New Attacks and Systematic Analysis** — [arxiv_cl](https://arxiv.org/abs/2605.03441v1)
- **When to Think, When to Speak: Learning Disclosure Policies for LLM Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.03314v1)
- **SHIELD: A Diverse Clinical Note Dataset and Distilled Small Language Models for Enterprise-Scale De-identification** — [arxiv_cl](https://arxiv.org/abs/2605.03301v1)
- **Vanishing L2 regularization for the softmax Multi Armed Bandit** — [arxiv_lg](https://arxiv.org/abs/2605.03752v1)
- **Predicting missing values: A good idea?** — [arxiv_lg](https://arxiv.org/abs/2605.03733v1)
- **Uni-OPD: Unifying On-Policy Distillation with a Dual-Perspective Recipe** — [arxiv_lg](https://arxiv.org/abs/2605.03677v1)
- **Free Decompression with Algebraic Spectral Curves** — [arxiv_lg](https://arxiv.org/abs/2605.03634v1)
- **Exact and Approximate Algorithms for Polytree Learning** — [arxiv_lg](https://arxiv.org/abs/2605.03622v1)
- **When Agents Handle Secrets: A Survey of Confidential Computing for Agentic AI** — [arxiv_cr](https://arxiv.org/abs/2605.03213v1)
- **A Validated Prompt Bank for Malicious Code Generation: Separating Executable Weapons from Security Knowledge in 1,554 Consensus-Labeled Prompts** — [arxiv_cr](https://arxiv.org/abs/2605.03179v1)
- **HackerSignal: A Large-Scale Multi-Source Dataset Linking Hacker Community Discourse to the CVE Vulnerability Lifecycle** — [arxiv_cr](https://arxiv.org/abs/2605.03158v1)
- **Analyzing Unsolicited Internet Traffic: Measuring IoT Security Threats via Network Telescopes** — [arxiv_cr](https://arxiv.org/abs/2605.02795v1)
- **Dimensionality-Aware Anomaly Detection in Learned Representations of Self-Supervised Speech Models** — [arxiv_cr](https://arxiv.org/abs/2605.02715v1)
- **TeamUp: Semantic Project Matching and Team Formation for Learning at Scale** — [arxiv_cl](https://arxiv.org/abs/2605.03237v1)
- **T^2PO: Uncertainty-Guided Exploration Control for Stable Multi-Turn Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.02178)
- **Logical Consistency as a Bridge: Improving LLM Hallucination Detection via Label Constraint Modeling between Responses and Self-Judgments** — [arxiv_cl](https://arxiv.org/abs/2605.03971v1)
- **Transformers with Selective Access to Early Representations** — [arxiv_cl](https://arxiv.org/abs/2605.03953v1)
- **CC-OCR V2: Benchmarking Large Multimodal Models for Literacy in Real-world Document Processing** — [arxiv_cl](https://arxiv.org/abs/2605.03903v1)
- **Reproducing Complex Set-Compositional Information Retrieval** — [arxiv_cl](https://arxiv.org/abs/2605.03824v1)
- **Natural Language Processing: A Comprehensive Practical Guide from Tokenisation to RLHF** — [arxiv_cl](https://arxiv.org/abs/2605.03799v1)
- **Pretrained Model Representations as Acquisition Signals for Active Learning of MLIPs** — [arxiv_lg](https://arxiv.org/abs/2605.03964v1)
- **Exact ReLU realization of tensor-product refinement iterates** — [arxiv_lg](https://arxiv.org/abs/2605.03917v1)
- **Graph Neural Networks in the Wilson Loop Representation of Abelian Lattice Gauge Theories** — [arxiv_lg](https://arxiv.org/abs/2605.03901v1)
- **From Data Lifting to Continuous Risk Estimation: A Process-Aware Pipeline for Predictive Monitoring of Clinical Pathways** — [arxiv_lg](https://arxiv.org/abs/2605.03895v1)
- **Memory-Efficient Continual Learning with CLIP Models** — [arxiv_lg](https://arxiv.org/abs/2605.03866v1)
- **Complex Equation Learner: Rational Symbolic Regression with Gradient Descent in Complex Domain** — [arxiv_lg](https://arxiv.org/abs/2605.03841v1)
- **On Computing Total Variation Distance Between Mixtures of Product Distributions** — [arxiv_lg](https://arxiv.org/abs/2605.03839v1)
- **A Domain Incremental Continual Learning Benchmark for ICU Time Series Model Transportability** — [arxiv_lg](https://arxiv.org/abs/2605.03832v1)
- **Realizable Bayes-Consistency for General Metric Losses** — [arxiv_lg](https://arxiv.org/abs/2605.03823v1)
- **Benchmarking Parameter-Efficient Fine-Tuning of Large Language Models for Low-Resource Tajik Text Generation with the Tajik Web Corpus** — [arxiv_cl](https://arxiv.org/abs/2605.03742v1)
- **Rose-SQL: Role-State Evolution Guided Structured Reasoning for Multi-Turn Text-to-SQL** — [arxiv_cl](https://arxiv.org/abs/2605.03720v1)
- **A Comprehensive Analysis of Tokenization and Self-Supervised Learning in End-to-End Automatic Speech Recognition applied on French Language** — [arxiv_cl](https://arxiv.org/abs/2605.03696v1)
- **A Paradigm for Interpreting Metrics and Identifying Critical Errors in Automatic Speech Recognition** — [arxiv_cl](https://arxiv.org/abs/2605.03671v1)
- **Annotation Quality in Aspect-Based Sentiment Analysis: A Case Study Comparing Experts, Students, Crowdworkers, and Large Language Model** — [arxiv_cl](https://arxiv.org/abs/2605.03624v1)
- **OpenSeeker-v2: Pushing the Limits of Search Agents with Informative and High-Difficulty Trajectories** — [huggingface_papers](https://arxiv.org/abs/2605.04036)
- **SymptomAI: Towards a Conversational AI Agent for Everyday Symptom Assessment** — [huggingface_papers](https://arxiv.org/abs/2605.04012)
- **A Hybrid Approach for Closing the Sim2real Appearance Gap in Game Engine Synthetic Datasets** — [huggingface_papers](https://arxiv.org/abs/2605.02291)
- **MolmoAct2: Action Reasoning Models for Real-world Deployment** — [huggingface_papers](https://arxiv.org/abs/2605.02881)
- **Generative Modeling with Orbit-Space Particle Flow Matching** — [huggingface_papers](https://arxiv.org/abs/2605.02222)
- **AcademiClaw: When Students Set Challenges for AI Agents** — [huggingface_papers](https://arxiv.org/abs/2605.02661)
- **PhysicianBench: Evaluating LLM Agents in Real-World EHR Environments** — [huggingface_papers](https://arxiv.org/abs/2605.02240)
- **Google, Microsoft, and xAI will allow the US government to review their new AI models** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/924017/google-microsoft-xai-government-review)
- **SAP bets $1.16B on 18-month-old German AI lab and says yes to NemoClaw** — [techcrunch_ai](https://techcrunch.com/2026/05/05/sap-bets-1-16b-on-18-month-old-german-ai-lab-and-says-yes-to-nemoclaw/)
- **Google Home&#8217;s Gemini AI can handle more complicated requests** — [theverge_ai](https://www.theverge.com/tech/924755/google-home-gemini-3-1-upgrade)
- **Apple agrees to pay iPhone owners $250 million for not delivering AI Siri** — [theverge_ai](https://www.theverge.com/tech/924706/apple-iphone-siri-intelligence-class-action-lawsuit-settlement)
- **Apple plans to make iOS 27 a Choose Your Own Adventure of AI models** — [techcrunch_ai](https://techcrunch.com/2026/05/05/apple-plans-to-make-ios-27-a-choose-your-own-adventure-of-ai-models/)
- **ASML CEO Christophe Fouquet on his company’s monopoly: no one is coming for us** — [techcrunch_ai](https://techcrunch.com/2026/05/05/asml-ceo-christophe-fouquet-no-one-is-coming-for-us/)
- **Microsoft gives up on Xbox Copilot AI** — [theverge_ai](https://www.theverge.com/games/924551/microsoft-xbox-ceo-copilot-ai-asha-sharma)
- **Apple could let you pick a favorite AI model in iOS 27** — [theverge_ai](https://www.theverge.com/tech/924515/apple-intelligence-third-party-chatbot-extensions-ios-27)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **OpenAI claims ChatGPT’s new default model hallucinates way less** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/924225/openai-chatgpt-default-model-gpt-5-5-instant)
- **Pennsylvania sues Character.AI after a chatbot allegedly posed as a doctor** — [techcrunch_ai](https://techcrunch.com/2026/05/05/pennsylvania-sues-character-ai-after-a-chatbot-allegedly-posed-as-a-doctor/)
- **OpenAI releases GPT-5.5 Instant, a new default model for ChatGPT** — [techcrunch_ai](https://techcrunch.com/2026/05/05/openai-releases-gpt-5-5-instant-a-new-default-model-for-chatgpt/)
- **Book publishers sue Meta over AI&#8217;s &#8216;word-for-word&#8217; copying** — [theverge_ai](https://www.theverge.com/tech/924230/meta-publishers-lawsuit-ai-copyright)
- **OpenAI is reportedly launching a phone for ChatGPT** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/924063/openai-phone-rumors-2027-ming-chi-kuo)
- **PayPal says it’s ‘becoming a technology company again’ — that means AI** — [techcrunch_ai](https://techcrunch.com/2026/05/05/paypal-says-its-becoming-a-technology-company-again-that-means-ai/)
- **4 days left: Get 50% off a second TechCrunch Disrupt 2026 pass to make more deals faster** — [techcrunch_ai](https://techcrunch.com/2026/05/05/4-days-left-get-50-off-a-second-techcrunch-disrupt-2026-pass-to-make-more-deals-faster/)
- **Google is partnering with XPRIZE and Range Media Partners on the $3.5 million Future Vision film competition.** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/future-vision-film-competition-xprize/)
- **What an AI-designed car looks like** — [theverge_ai](https://www.theverge.com/podcast/923974/ai-car-design-codex-vergecast)
- **The Download: inside the Musk v. Altman trial, and AI for democracy** — [mit_tech_review](https://www.technologyreview.com/2026/05/05/1136848/the-download-musk-openai-altman-trial-ai-democracy/)
- **A blueprint for using AI to strengthen democracy** — [mit_tech_review](https://www.technologyreview.com/2026/05/05/1136843/ai-democracy-blueprint/)
- **Altara secures $7M to bridge the data gap that’s slowing down physical sciences** — [techcrunch_ai](https://techcrunch.com/2026/05/05/altara-secures-7m-to-bridge-the-data-gap-thats-slowing-down-physical-sciences/)
- **Etsy launches its app within ChatGPT as it continues its AI push** — [techcrunch_ai](https://techcrunch.com/2026/05/05/etsy-launches-its-app-within-chatgpt-as-it-continues-its-ai-push/)
- **Meta will use AI to analyze height and bone structure to identify if users are underage** — [techcrunch_ai](https://techcrunch.com/2026/05/05/meta-will-use-ai-to-analyze-height-and-bone-structure-to-identify-if-users-are-underage/)
- **ElevenLabs lists BlackRock, Jamie Foxx, and Eva Longoria as new investors** — [techcrunch_ai](https://techcrunch.com/2026/05/05/elevenlabs-lists-blackrock-jamie-foxx-and-eva-longoria-as-new-investors/)
- **CopilotKit raises $27M to help devs deploy app-native AI agents** — [techcrunch_ai](https://techcrunch.com/2026/05/05/copilotkit-raises-27m-to-help-devs-deploy-app-native-ai-agents/)
- **India’s first GenAI unicorn shifts to cloud services as AI model ambitions face reality** — [techcrunch_ai](https://techcrunch.com/2026/05/05/indias-first-genai-unicorn-shifts-to-cloud-services-as-ai-model-ambitions-face-reality/)
- **GPT-5.5 Instant: smarter, clearer, and more personalized** — [openai](https://openai.com/index/gpt-5-5-instant)
- **As workers worry about AI, Nvidia’s Jensen Huang says AI is ‘creating an enormous number of jobs’** — [techcrunch_ai](https://techcrunch.com/2026/05/04/as-workers-worry-about-ai-nvidias-jensen-huang-says-ai-is-creating-an-enormous-number-of-jobs/)
- **GPT-5.5 Instant System Card** — [openai](https://openai.com/index/gpt-5-5-instant-system-card)
- **GanyuanRan/Aegis** — [github](https://github.com/GanyuanRan/Aegis)
- **csy-csy123/pr-review-agent-council** — [github](https://github.com/csy-csy123/pr-review-agent-council)
- **Wholiver/swiftui-design-skill** — [github](https://github.com/Wholiver/swiftui-design-skill)
- **0xbl33p/goblintown** — [github](https://github.com/0xbl33p/goblintown)
- **dmae97/oh-my-kimi** — [github](https://github.com/dmae97/oh-my-kimi)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **KSroido/Kagi-Session2API-MCP** — [github](https://github.com/KSroido/Kagi-Session2API-MCP)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **warpdot-dev/craft-agents-oss** — [github](https://github.com/warpdot-dev/craft-agents-oss)
- **warpdot-dev/composio** — [github](https://github.com/warpdot-dev/composio)
- **lukiIabs/trading-agents** — [github](https://github.com/lukiIabs/trading-agents)
- **StartupHakk/OpenMonoAgent.ai** — [github](https://github.com/StartupHakk/OpenMonoAgent.ai)
- **YutoTerashima/agent-safety-eval-lab** — [github](https://github.com/YutoTerashima/agent-safety-eval-lab)
- **arizen-dev/deepseek-mcp** — [github](https://github.com/arizen-dev/deepseek-mcp)
- **prime-radiant-inc/books-for-bots** — [github](https://github.com/prime-radiant-inc/books-for-bots)
- **bensenescu/downy** — [github](https://github.com/bensenescu/downy)
- **jmerelnyc/Photo-agents** — [github](https://github.com/jmerelnyc/Photo-agents)
- **刚刚，ChatGPT免费模型升级了：幻觉砍半/记忆更强/回答更简洁** — [qbitai](https://www.qbitai.com/2026/05/412995.html)
- **“北赛泓升”完成A+轮融资** — [36kr](https://36kr.com/newsflashes/3797145860644105?f=rss)
- **一家AI原生健康硬件公司完成近亿元融资，韶音、甘洁出手，高秉强投过｜硬氪首发** — [36kr](https://36kr.com/p/3682907323150215?f=rss)
- **Rivian称投入数亿美元自研芯片** — [36kr](https://36kr.com/newsflashes/3797114393943296?f=rss)
- **中信证券：一季度电子行业基金配置略有回落，超配比例仍处历史高位** — [36kr](https://36kr.com/newsflashes/3797081274719235?f=rss)
- **KKR称私募市场困境被夸大** — [36kr](https://36kr.com/newsflashes/3797079057898501?f=rss)
- **银河证券：建议关注景气度较高的上游算力基础设施** — [36kr](https://36kr.com/newsflashes/3797077145984262?f=rss)
- **华泰证券：短期行情或进入震荡期，风格层面建议哑铃配置** — [36kr](https://36kr.com/newsflashes/3797076129471752?f=rss)
- **8点1氪丨豆包新增付费订阅；抖音集团副总裁回应红果短剧付费；苹果因Siri人工智能功能推迟发布，以2.5亿美元和解诉讼** — [36kr](https://36kr.com/p/3797041945304327?f=rss)
- **恒指开盘涨0.51%，恒生科技指数涨0.85%** — [36kr](https://36kr.com/newsflashes/3797132055469057?f=rss)
- **两市融资余额减少167.42亿元** — [36kr](https://36kr.com/newsflashes/3797100627123206?f=rss)