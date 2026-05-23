# AI 日报 [AI 安全] - 2026-05-23


## 2026年5月23日 AI安全、对齐与治理主题综述

### Highlights
今天的学术进展清晰地勾勒出AI安全研究正从多个战线向纵深发展。最为重磅的进展集中于**隐私机制的实践性审计**与**对抗性攻击的范式演进**。一项针对苹果公司长期宣称的差分隐私框架的独立客户端审计，揭示了理论保证与实际部署之间令人担忧的鸿沟，迫使行业重新审视“隐私保护”的技术声明。同时，研究在对抗攻防两端均展现出新的复杂性：一方面，**针对安全分类器的边界目标成员推理攻击**和**利用域伪装突破LLM注入检测**揭示了现有安全防线的脆弱盲点；另一方面，为认证鲁棒性提供新思路、以及为动态RAG系统设计自适应防御的工作，则代表了防御技术的积极演进。此外，对齐研究进入了更精细的“病理学”建模与概念边界探测阶段，为理解模型内在机理提供了新工具。

### 1. 对抗攻击与鲁棒性：从静态毒化到动态欺骗
对抗攻防的战场持续扩大，研究愈发注重攻击的隐蔽性与防御的适应性。在后门攻击防御领域，传统方法在时序数据上遭遇挑战。论文**《TimeGuard: Channel-wise Pool Training for Backdoor Defense in Time Series Forecasting》** 系统评估了十三种防御在时序预测任务上的失效模式，指出数据纠缠导致的通道级信号稀释使得基于样本过滤和触发合成的防御失效。为此，作者提出的TimeGuard通过通道池训练来隔离和净化通道，为时序场景的后门防御开辟了新路径。

而在更广泛的鲁棒性理论层面，论文**《Provable Robustness against Backdoor Attacks via the Primal-Dual Perspective on Differential Privacy》** 将随机平滑与差分隐私的对偶视角相连接，通过隐私配置文件提供了一种数值化方法来组合训练时和测试时的随机机制，从而为后门攻击（训练与测试数据被联合扰动的场景）提供了统一的鲁棒性证书。这项工作在理论上将两类主要的中毒攻击（投毒与规避）的防御框架进行了统一，具有重要价值。

攻击技术则变得更加狡猾和场景化。针对基于检索增强生成的动态系统，论文**《RADAR: Defending RAG Dynamically against Retrieval Corruption》** 指出，静态防御难以应对随时间演变的检索污染，并提出了一个基于图能量最小化和贝叶斯记忆节点的自适应框架，在稳定性和抗攻击性之间取得平衡。另一项工作**《Adversarial Reframing: A Framework for Targeted Generation in Language Models》** 提出了THREAT框架，将多LLM协同与非凸优化相结合，用于系统性地搜索越狱提示，展示了攻击自动化与智能化的趋势。

而在车辆协同感知这一新兴应用场景，论文**《Adversarial Trust Poisoning in Vehicular Collaborative Perception》** 揭示了防御机制本身可能成为攻击面。作者提出的TrustFlip攻击，能够“武器化”一致性检测机制，反而毒化对良性车辆的信任评估。这深刻地提醒我们，任何防御系统都必须被视作复杂系统的一部分，其自身可能引入新的脆弱点。

### 2. 模型对齐与可解释性：从行为约束到概念探针
对齐研究正在超越简单的偏好优化，深入到概念层面和病理行为建模。论文**《What Counts as AI Sycophancy? A Taxonomy and Expert Survey of a Fragmented Construct》** 为“AI谄媚”这一模糊概念构建了分类学，并通过专家调查指出其定义的不一致性阻碍了评估和缓解策略的迁移。这呼吁社区建立更精确的行为定义体系。

对齐方法论上，论文**《Implicit Safety Alignment from Crowd Preferences》** 探索了从嘈杂的人群偏好中提取隐含共享安全准则的方法，并将其迁移用于强化学习任务的正则化。而论文**《Two is better than one: A Collapse-free Multi-Reward RLIF Training Framework》** 则针对基于内部反馈的强化学习（RLIF）的奖励坍缩问题，提出多奖励框架来分解训练信号，提升了无监督对齐训练的稳定性。

可解释性与安全审计的结合产生了新工具。论文**《Reading Task Failure Off the Activations: A Sparse-Feature Audit of GPT-2 Small on Indirect Object Identification》** 利用稀疏自编码器特征对GPT-2在间接宾语识别任务中的失败案例进行审计，发现某些与“加密密钥”等概念相关的特征与任务失败强相关。这为利用可解释性工具诊断模型特定能力缺陷提供了可复现的案例。

更具颠覆性的是，研究者开始尝试对模型的“不正常”行为进行建模。论文**《Modeling Pathology-Like Behavioral Patterns in Language Models Through Behavioral Fine-Tuning》** 报告了一项实验：通过在模拟抑郁或偏执决策任务的合成数据上进行微调，成功诱导语言模型表现出系统性的、类似心理病理的行为模式，并观察到其生成分布的变化。这表明模型的行为模式可以通过针对性数据“编程”，同时也为研究AI系统的非典型行为提供了实验范式。

在多模态对齐方面，论文**《Measuring Cross-Modal Synergy: A Benchmark for VLM Explainability》** 揭示了当前视觉-语言模型解释性评估的一个关键缺陷：由于数据集中的模态偏差，模型可能仅靠文本就能回答视觉查询，导致基于单模态扰动的评估指标无法奖励真正忠实的跨模态解释器，甚至引发“评估坍塌”。这要求评估基准必须考虑跨模态协同的必要性。

### 3. 隐私保护与计算：从理论保证到工程审计
隐私保护领域本周出现了最具冲击力的实践性发现。论文**《Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks》** 对苹果自2016年以来在设备分析中使用的差分隐私框架进行了客户端逆向工程审计。研究人员在macOS上复现并分析了其二进制文件，声称发现了实现缺陷、配置错误以及不理想的隐私-效用权衡。这项独立审计直接挑战了巨头公司未经公开验证的隐私声明，凸显了闭源隐私机制缺乏透明度的巨大风险，是隐私工程领域一个重要的里程碑。

在隐私计算算法创新方面，论文**《Lumberjack: Better Differentially Private Random Forests through Heavy Hitter Detection in Trees》** 为在敏感表格数据上构建高实用性的差分隐私随机森林提供了新思路。其核心创新在于一种新颖的$(\varepsilon,δ)$-DP重击者检测算法，能在决策树层级结构中识别出足够“密集”的节点，从而在激进剪枝以保护隐私的同时，保留关键信息，显著提升了模型效用。

隐私攻击研究同样聚焦于关键组件。论文**《Boundary-targeted Membership Inference Attacks on Safety Classifiers》** 指出，安全分类器（如检测自残内容）通常在包含敏感讨论的数据上训练，因此面临特殊的隐私风险。该研究提出并验证了针对分类器决策边界附近样本的成员推理攻击，这些样本对攻击者而言信息量最大。这揭示了部署安全组件本身可能带来的数据泄露隐患。

理论层面，论文**《Information Leakage Envelopes》** 在点态最大泄漏框架下，试图定义同时满足后处理鲁棒性并能提供泄漏失败概率上界的隐私度量。研究引入了“PML包络”的概念，为量化后处理操作后的最大信息泄漏提供了新工具。而论文**《Optimal Guarantees for Auditing Rényi Differentially Private Machine Learning》** 则为审计Rényi差分隐私算法提出了基于假设检验的框架，并给出了非渐近置信区间和匹配的极小极大下界，提升了隐私审计的理论严谨性。

### 4. 安全评估基准：定义新场景与新挑战
评估基准的演进紧跟前沿安全问题。论文**《Benchmarking and Improving Monitors for Out-Of-Distribution Alignment Failure in LLMs》** 针对“分布外对齐失败”这一难题，提出了MOOD基准。其巧妙之处在于包含了一个受限训练集，用于人为创造对评估模型而言的OOD情况，从而系统性地研究监控管道检测此类失败的能力，填补了该领域的空白。

多模态和交互式场景的评估也得到加强。论文**《AttuneBench: A Conversation-Based Benchmark for LLM Emotional Intelligence》** 认为现有情感智能基准依赖单轮合成提示，无法捕捉真实对话中的动态推断过程。因此，他们构建了基于真实多人对话记录的AttuneBench，旨在评估模型在连续交互中感知、理解和回应参与者情绪状态的能力。

### 5. Agent安全与治理：多智能体、接口与开源工具
随着AI代理系统的普及，其安全与治理成为焦点。论文**《Blind Spots in the Guard: How Domain-Camouflaged Injection Attacks Evade Detection in Multi-Agent LLM Systems》** 发现了一个系统性盲点：当注入负载模仿目标文档的领域词汇和权威结构时（即“域伪装注入”），标准检测器的检出率会急剧下降。这提出了对静态、模板化检测范式的根本性质疑。

在多智能体系统内部通信安全上，论文**《LCGuard: Latent Communication Guard for Safe KV Sharing in Multi-Agent Systems》** 关注到通过Transformer键值缓存进行的高效但不透明的潜在通信可能传播敏感信息。LCGuard旨在为此类通信提供防护。

论文**《CCLab: Adversarial Testing of Learning- and Non-Learning-Based Congestion Controllers》** 则为网络协议中的机器学习组件（拥塞控制器）提供了对抗性测试框架，评估其在信号被篡改或环境恶化时的鲁棒性，这是将安全评估方法应用于传统基础设施中的ML组件的重要尝试。

开源社区也贡献了关键的安全工具。**control-layer** 项目提供了一个生产级的控制层，位于应用逻辑与任何LLM之间，集成了输入验证、模式强制、断路器、针对性重试和审计日志。**ai-kill-chain** 则为LLM和代理AI威胁提供了一个防御方扩展的“杀伤链”分析框架，增加了模型供应链阶段，并将目标行动细化为数据窃取、模型提取和代理枢转。这些工具为构建更安全的AI应用提供了实用组件。

### Looking Forward
今天的多项工作预示了未来几个关键的探索方向。首先，**理论与实践的鸿沟**在隐私领域尤为突出，苹果框架的审计表明，仅依赖理论保证而缺乏透明实施和持续验证是危险的，行业亟需更开放的隐私工程实践和标准化审计方法。其次，**对齐的精细化**正在发生，研究者开始从统计关联转向对特定能力（如情感智能、跨模态协同）和特定失效模式（如病理行为、对概念边界的理解）进行深入解剖，这要求发展更精细的对齐理论和评估工具。最后，**代理系统的安全**是一个紧迫的未解决问题，从多智能体间的隐式信息泄漏，到域伪装这类利用领域知识的复杂攻击，再到对代理行为进行端到端评估的基准构建，都表明我们需要一套全新的安全模型来治理这些能够与环境动态交互、具备复杂推理和规划能力的实体。如何为“代理”这一新范式设计内生的安全与对齐机制，将是下一阶段的核心挑战。

---


## 参考来源

- **Provable Robustness against Backdoor Attacks via the Primal-Dual Perspective on Differential Privacy** — [arxiv_cr](https://arxiv.org/abs/2605.21780v1)
- **Measuring Cross-Modal Synergy: A Benchmark for VLM Explainability** — [arxiv_ai](https://arxiv.org/abs/2605.22168)
- **The Matching Principle: A Geometric Theory of Loss Functions for Nuisance-Robust Representation Learning** — [arxiv_lg](https://arxiv.org/abs/2605.22800v1)
- **EnCAgg: Enhanced Clustering Aggregation for Robust Federated Learning against Dynamic Model Poisoning** — [arxiv_cr](https://arxiv.org/abs/2605.22506v1)
- **CCLab: Adversarial Testing of Learning- and Non-Learning-Based Congestion Controllers** — [arxiv_cr](https://arxiv.org/abs/2605.21915v1)
- **AOP-Wiki EMOD 3.0: Data Model Expansions and Content Evaluation Framework for Using Agentic AI to Improve Integration between AOPs and New Approach Methodologies (NAMs)** — [arxiv_ai](https://arxiv.org/abs/2605.21645)
- **Investigating Concept Alignment Using Implausible Category Members** — [arxiv_ai](https://arxiv.org/abs/2605.21683)
- **A Causal Argumentation Method for Explainability of Machine Learning Models** — [arxiv_ai](https://arxiv.org/abs/2605.21758)
- **What Counts as AI Sycophancy? A Taxonomy and Expert Survey of a Fragmented Construct** — [arxiv_ai](https://arxiv.org/abs/2605.21778)
- **Implicit Safety Alignment from Crowd Preferences** — [arxiv_ai](https://arxiv.org/abs/2605.21822)
- **ECPO: Evidence-Coupled Policy Optimization for Evidence-Certified Candidate Ranking** — [arxiv_ai](https://arxiv.org/abs/2605.21993)
- **Lumberjack: Better Differentially Private Random Forests through Heavy Hitter Detection in Trees** — [arxiv_lg](https://arxiv.org/abs/2605.22756v1)
- **Evaluating Commercial AI Chatbots as News Intermediaries** — [arxiv_cl](https://arxiv.org/abs/2605.22785v1)
- **TimeGuard: Channel-wise Pool Training for Backdoor Defense in Time Series Forecasting** — [arxiv_cr](https://arxiv.org/abs/2605.22365v1)
- **QT-PUF: Quantum Tunneling Leakage Based PUF for Implantable IoMT Devices** — [arxiv_cr](https://arxiv.org/abs/2605.22113v1)
- **RADAR: Defending RAG Dynamically against Retrieval Corruption** — [arxiv_cr](https://arxiv.org/abs/2605.22041v1)
- **Proxy-Based Approximation of Shapley and Banzhaf Interactions** — [arxiv_lg](https://arxiv.org/abs/2605.22738v1)
- **Reading Task Failure Off the Activations: A Sparse-Feature Audit of GPT-2 Small on Indirect Object Identification** — [arxiv_lg](https://arxiv.org/abs/2605.22719v1)
- **SegCompass: Exploring Interpretable Alignment with Sparse Autoencoders for Enhanced Reasoning Segmentation** — [arxiv_lg](https://arxiv.org/abs/2605.22658v1)
- **Two is better than one: A Collapse-free Multi-Reward RLIF Training Framework** — [arxiv_cl](https://arxiv.org/abs/2605.22620v1)
- **Boundary-targeted Membership Inference Attacks on Safety Classifiers** — [arxiv_cl](https://arxiv.org/abs/2605.22373v1)
- **Modeling Pathology-Like Behavioral Patterns in Language Models Through Behavioral Fine-Tuning** — [arxiv_cl](https://arxiv.org/abs/2605.22356v1)
- **Optimal Guarantees for Auditing Rényi Differentially Private Machine Learning** — [arxiv_cr](https://arxiv.org/abs/2605.21938v1)
- **Adversarial Reframing: A Framework for Targeted Generation in Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.21674v1)
- **Near-Optimal Generalized Private Testing** — [arxiv_cr](https://arxiv.org/abs/2605.21601v1)
- **Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks** — [arxiv_cr](https://arxiv.org/abs/2605.21378v2)
- **Information Leakage Envelopes** — [arxiv_cr](https://arxiv.org/abs/2605.21185v1)
- **Benchmarking and Improving Monitors for Out-Of-Distribution Alignment Failure in LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.21602)
- **Latent-space Attacks for Refusal Evasion in Language Models** — [arxiv_ai](https://arxiv.org/abs/2605.21706)
- **AttuneBench: A Conversation-Based Benchmark for LLM Emotional Intelligence** — [arxiv_ai](https://arxiv.org/abs/2605.21739)
- **Who Uses AI? Platforms, Workforce, and AI Exposure** — [arxiv_ai](https://arxiv.org/abs/2605.21743)
- **Trace2Skill: Verifier-Guided Skill Evolution for Long-Context EDA Agents** — [arxiv_ai](https://arxiv.org/abs/2605.21810)
- **Planning in the LLM Era: Building for Reliability and Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.21902)
- **AI-Enabled Serious Games: Integrating Intelligence and Adaptivity in Training Systems** — [arxiv_ai](https://arxiv.org/abs/2605.21962)
- **A Camera-Cooperative ISAC Framework for Multimodal Non-Cooperative UAVs Sensing** — [arxiv_ai](https://arxiv.org/abs/2605.22090)
- **ArborKV: Structure-Aware KV Cache Management for Scaling Tree-based LLM Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.22106)
- **Efficient Agentic Reasoning Through Self-Regulated Simulative Planning** — [arxiv_ai](https://arxiv.org/abs/2605.22138)
- **Adapting the Interface, Not the Model: Runtime Harness Adaptation for Deterministic LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2605.22166)
- **LLM-Metrics: Measuring Research Impact Through Large Language Model Memory** — [arxiv_ai](https://arxiv.org/abs/2605.22176)
- **CLORE: Content-Level Optimization for Reasoning Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.22211)
- **Remember to be Curious: Episodic Context and Persistent Worlds for 3D Exploration** — [arxiv_lg](https://arxiv.org/abs/2605.22814v1)
- **LCGuard: Latent Communication Guard for Safe KV Sharing in Multi-Agent Systems** — [arxiv_lg](https://arxiv.org/abs/2605.22786v1)
- **Vector Policy Optimization: Training for Diversity Improves Test-Time Search** — [arxiv_cl](https://arxiv.org/abs/2605.22817v1)
- **Reducing Political Manipulation with Consistency Training** — [arxiv_cl](https://arxiv.org/abs/2605.22771v1)
- **TriSweep: A Four-Drone Swarm Framework for Electromagnetic Side-Channel Analysis** — [arxiv_cr](https://arxiv.org/abs/2605.22709v1)
- **A Formal Basis for Quantum Cryptographic Exposure Measurement under HNDL Threat** — [arxiv_cr](https://arxiv.org/abs/2605.22569v1)
- **A Constant-Time Implementation Methodology for Activation Functions on Microcontrollers** — [arxiv_cr](https://arxiv.org/abs/2605.22441v1)
- **Adversarial Trust Poisoning in Vehicular Collaborative Perception** — [arxiv_cr](https://arxiv.org/abs/2605.22122v1)
- **Safeguarding Text-to-Image Generative Models Against Unauthorized Knowledge Distillation** — [arxiv_cr](https://arxiv.org/abs/2605.22060v1)
- **Secure and Parallel Determinant Computation for Large-Scale Matrices in Edge Environments** — [arxiv_cr](https://arxiv.org/abs/2605.22039v1)
- **The Distillation Game: Adaptive Attacks & Efficient Defenses** — [arxiv_lg](https://arxiv.org/abs/2605.22737v1)
- **Post-Training is About States, Not Tokens: A State Distribution View of SFT, RL, and On-Policy Distillation** — [arxiv_lg](https://arxiv.org/abs/2605.22731v1)
- **Live Music Diffusion Models: Efficient Fine-Tuning and Post-Training of Interactive Diffusion Music Generators** — [arxiv_lg](https://arxiv.org/abs/2605.22717v1)
- **Abstraction for Offline Goal-Conditioned Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.22711v1)
- **The Secretary Problem with a Stochastic Precursor** — [arxiv_lg](https://arxiv.org/abs/2605.22653v1)
- **A note on convergence of Wasserstein policy optimization** — [arxiv_lg](https://arxiv.org/abs/2605.22622v1)
- **UNAD+: An Explainable Hybrid Framework for Unknown Network Attack Detection** — [arxiv_lg](https://arxiv.org/abs/2605.22621v1)
- **MoSA: Motion-constrained Stress Adaptation for Mitigating Real-to-Sim Gap in Continuum Dynamics via Learning Residual Anisotropy** — [arxiv_lg](https://arxiv.org/abs/2605.22597v1)
- **Factored Diffusion Policies:Compositionally Generalized Robot Control with a Single Score Network** — [arxiv_lg](https://arxiv.org/abs/2605.22596v1)
- **ChronoMedKG: A Temporally-Grounded Biomedical Knowledge Graph and Benchmark for Clinical Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.22734v1)
- **Beyond Acoustic Emotion Recognition: Multimodal Pathos Analysis in Political Speech Using LLM-Based and Acoustic Emotion Models** — [arxiv_cl](https://arxiv.org/abs/2605.22732v1)
- **AMEL: Accumulated Message Effects on LLM Judgments** — [arxiv_cl](https://arxiv.org/abs/2605.22714v1)
- **Self-Policy Distillation via Capability-Selective Subspace Projection** — [arxiv_cl](https://arxiv.org/abs/2605.22675v1)
- **Moral Semantics Survive Machine Translation: Cross-Lingual Evidence from Moral Foundations Corpora** — [arxiv_cl](https://arxiv.org/abs/2605.22660v1)
- **Boiling the Frog: A Multi-Turn Benchmark for Agentic Safety** — [arxiv_cl](https://arxiv.org/abs/2605.22643v1)
- **The Double Dilemma in Multi-Task Radiology Report Generation: A Gradient Dynamics Analysis and Solution** — [arxiv_cl](https://arxiv.org/abs/2605.22635v1)
- **Agentic CLEAR: Automating Multi-Level Evaluation of LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2605.22608v1)
- **LANG: Reinforcement Learning for Multilingual Reasoning with Language-Adaptive Hint Guidance** — [arxiv_cl](https://arxiv.org/abs/2605.22567v1)
- **One prompt is not enough: Instruction Sensitivity Undermines Embedding Model Evaluation** — [arxiv_cl](https://arxiv.org/abs/2605.22544v1)
- **SpaceDG: Benchmarking Spatial Intelligence under Visual Degradation** — [arxiv_cl](https://arxiv.org/abs/2605.22536v1)
- **Search-E1: Self-Distillation Drives Self-Evolution in Search-Augmented Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.22511v1)
- **Polite on the Surface, Wrong in Practice: A Curated Dataset for Fixing Honorific Failures in Multilingual Bangla Generation** — [arxiv_cl](https://arxiv.org/abs/2605.22487v1)
- **From Correlation to Cause: A Five-Stage Methodology for Feature Analysis in Transformer Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.22462v1)
- **Blind Spots in the Guard: How Domain-Camouflaged Injection Attacks Evade Detection in Multi-Agent LLM Systems** — [arxiv_cr](https://arxiv.org/abs/2605.22001v1)
- **SPIDER: Two Server Functionality for the Cost of Zero** — [arxiv_cr](https://arxiv.org/abs/2605.21857v1)
- **Forecasting Scientific Progress with Artificial Intelligence** — [huggingface_papers](https://arxiv.org/abs/2605.22681)
- **One Sentence, One Drama: Personalized Short-Form Drama Generation via Multi-Agent Systems** — [huggingface_papers](https://arxiv.org/abs/2605.22144)
- **Maestro: Reinforcement Learning to Orchestrate Hierarchical Model-Skill Ensembles** — [huggingface_papers](https://arxiv.org/abs/2605.22177)
- **Diversed Model Discovery via Structured Table Discovery** — [huggingface_papers](https://arxiv.org/abs/2605.22766)
- **Onion-Routed Multi-Circuit Key Establishment for Quantum-Resilient Sessions** — [arxiv_cr](https://arxiv.org/abs/2605.21349v1)
- **Integrable Elasticity via Neural Demand Potentials** — [arxiv_lg](https://arxiv.org/abs/2605.22820v1)
- **Finite-Particle Convergence Rates for Conservative and Non-Conservative Drifting Models** — [arxiv_lg](https://arxiv.org/abs/2605.22795v1)
- **MOSS: Self-Evolution through Source-Level Rewriting in Autonomous Agent Systems** — [arxiv_lg](https://arxiv.org/abs/2605.22794v1)
- **FAME: Failure-Aware Mixture-of-Experts for Message-Level Log Anomaly Detection** — [arxiv_lg](https://arxiv.org/abs/2605.22779v1)
- **FashionLens: Toward Versatile Fashion Image Retrieval via Task-Adaptive Learning** — [huggingface_papers](https://arxiv.org/abs/2605.22552)
- **SEGA: Spectral-Energy Guided Attention for Resolution Extrapolation in Diffusion Transformers** — [huggingface_papers](https://arxiv.org/abs/2605.22668)
- **DecQ: Detail-Condensing Queries for Enhanced Reconstruction and Generation in Representation Autoencoders** — [huggingface_papers](https://arxiv.org/abs/2605.22777)
- **LatentOmni: Rethinking Omni-Modal Understanding via Unified Audio-Visual Latent Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.22012)
- **Segment Anything with Motion, Geometry, and Semantic Adaptation for Complex Nonlinear Visual Object Tracking** — [huggingface_papers](https://arxiv.org/abs/2605.22538)
- **SceneAligner: 3D-Grounded Floorplan Localization in the Wild** — [huggingface_papers](https://arxiv.org/abs/2605.22581)
- **Sensor2Sensor: Cross-Embodiment Sensor Conversion for Autonomous Driving** — [huggingface_papers](https://arxiv.org/abs/2605.22809)
- **From Reasoning Chains to Verifiable Subproblems: Curriculum Reinforcement Learning Enables Credit Assignment for LLM Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.22074)
- **WorldKV: Efficient World Memory with World Retrieval and Compression** — [huggingface_papers](https://arxiv.org/abs/2605.22718)
- **Bernini: Latent Semantic Planning for Video Diffusion** — [huggingface_papers](https://arxiv.org/abs/2605.22344)
- **TerminalWorld: Benchmarking Agents on Real-World Terminal Tasks** — [huggingface_papers](https://arxiv.org/abs/2605.22535)
- **Spreadsheet-RL: Advancing Large Language Model Agents on Realistic Spreadsheet Tasks via Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.22642)
- **Gated DeltaNet-2: Decoupling Erase and Write in Linear Attention** — [huggingface_papers](https://arxiv.org/abs/2605.22791)
- **Swift Sampling: Selecting Temporal Surprises via Taylor Series** — [huggingface_papers](https://arxiv.org/abs/2605.22678)
- **ACC: Compiling Agent Trajectories for Long-Context Training** — [huggingface_papers](https://arxiv.org/abs/2605.21850)
- **RiT: Vanilla Diffusion Transformers Suffice in Representation Space** — [huggingface_papers](https://arxiv.org/abs/2605.21981)
- **Elon Musk can’t hear you over the sound of his $1.75 trillion IPO** — [techcrunch_ai](https://techcrunch.com/podcast/elon-musk-cant-hear-you-over-the-sound-of-his-1-75-trillion-ipo/)
- **We tried Google’s AI glasses and they’re almost there** — [techcrunch_ai](https://techcrunch.com/2026/05/22/we-tried-googles-ai-glasses-and-theyre-almost-there/)
- **SpaceX files to go public, and the math requires a little faith** — [techcrunch_ai](https://techcrunch.com/video/spacex-files-to-go-public-and-the-math-requires-a-little-faith/)
- **The Download: coding’s future, the ‘Steroid Olympics,’ and AI-driven science** — [mit_tech_review](https://www.technologyreview.com/2026/05/22/1137845/the-download-coding-future-steroid-olympics-ai-science/)
- **Google I/O showed how the path for AI-driven science is shifting** — [mit_tech_review](https://www.technologyreview.com/2026/05/22/1137813/google-i-o-showed-how-the-path-for-ai-science-is-shifting/)
- **The Enhanced Games fit right in with the rest of 2026’s longevity vibes** — [mit_tech_review](https://www.technologyreview.com/2026/05/22/1137753/the-enhanced-games-fit-right-in-with-the-rest-of-2026s-longevity-vibes/)
- **AI is being used to resurrect the voices of dead pilots** — [techcrunch_ai](https://techcrunch.com/2026/05/22/ai-is-being-used-to-resurrect-the-voices-of-dead-pilots/)
- **Google goes for the glitter with disco-ball icons: ‘Are y’all sure you still want this?’** — [techcrunch_ai](https://techcrunch.com/2026/05/22/google-goes-for-the-glitter-with-disco-ball-icons-are-yall-sure-you-still-want-this/)
- **How VCs and founders use inflated ‘ARR’ to crown AI startups** — [techcrunch_ai](https://techcrunch.com/2026/05/22/how-vcs-and-founders-use-inflated-arr-to-kingmake-ai-startups/)
- **Catch up on the Dialogues stage at Google I/O 2026.** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/io-2026-dialogues-recap/)
- **You can no longer Google the word ‘disregard’** — [techcrunch_ai](https://techcrunch.com/2026/05/22/you-can-no-longer-google-the-word-disregard/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **Emmimal/control-layer** — [github](https://github.com/Emmimal/control-layer)
- **wdnmd1265/ai-flow-architect** — [github](https://github.com/wdnmd1265/ai-flow-architect)
- **open-gsd/gsd-pi** — [github](https://github.com/open-gsd/gsd-pi)
- **gouravnagar-infosec/ai-kill-chain** — [github](https://github.com/gouravnagar-infosec/ai-kill-chain)
- **5bv57zcm44-max/NOXUS-AI-Open-WhatsApp** — [github](https://github.com/5bv57zcm44-max/NOXUS-AI-Open-WhatsApp)
- **ayush016/android-lead-agent-skills** — [github](https://github.com/ayush016/android-lead-agent-skills)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **kingbootoshi/directional-prompting** — [github](https://github.com/kingbootoshi/directional-prompting)
- **tuchg/Lucarne** — [github](https://github.com/tuchg/Lucarne)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **lywnl/ai-app-generation** — [github](https://github.com/lywnl/ai-app-generation)
- **nkzw-tech/cloudsail** — [github](https://github.com/nkzw-tech/cloudsail)
- **workos/auth.md** — [github](https://github.com/workos/auth.md)
- **h4ckf0r0day/awesome-ai-web-scraping** — [github](https://github.com/h4ckf0r0day/awesome-ai-web-scraping)
- **zhongweiv/hermes-edu-skills** — [github](https://github.com/zhongweiv/hermes-edu-skills)
- **hasanyilmaz/operon** — [github](https://github.com/hasanyilmaz/operon)
- **xuanlinAI/overmind** — [github](https://github.com/xuanlinAI/overmind)
- **XingYu-Zhong/DeepSeek-GUI** — [github](https://github.com/XingYu-Zhong/DeepSeek-GUI)
- **美团外卖前负责人入局餐饮具身模型，元节智能获千万级种子轮融资** — [qbitai](https://www.qbitai.com/2026/05/423159.html)
- **龙虾养不动了？周鸿祎给虾搭了个云端办公室，专业私教在线炼虾** — [qbitai](https://www.qbitai.com/2026/05/422811.html)
- **李飞飞再出手，空间智能的ImageNet来了** — [qbitai](https://www.qbitai.com/2026/05/422738.html)
- **融资700亿！DeepSeek Code真要来了，ACM金牌大神崔添翼挂帅** — [qbitai](https://www.qbitai.com/2026/05/422624.html)
- **狂揽F轮融资+拿下4100万用户！深圳玩家出手，把企业旧系统变成AI能力库** — [qbitai](https://www.qbitai.com/2026/05/422615.html)
- **中信证券：中国制罐企业有望获得更多全球市场拓展空间，逐步构建全球产能布局** — [36kr](https://36kr.com/newsflashes/3821373000077704?f=rss)
- **商务部：1-4月全国吸收外资2876.9亿元人民币** — [36kr](https://36kr.com/newsflashes/3821372272660615?f=rss)
- **36氪首发 | 北大项目孵化，国内首家原生机器人“大脑芯片”企业获数亿元融资** — [36kr](https://36kr.com/p/3821371042877575?f=rss)
- **短期态度转冷，国际投行下调黄金目标价** — [36kr](https://36kr.com/newsflashes/3821220090646657?f=rss)
- **传京东考虑20亿英镑竞购英国电商平台The Very Group** — [36kr](https://36kr.com/newsflashes/3821218974879878?f=rss)
- **本周机构调研热情不减，超三成机构调研股实现正收益** — [36kr](https://36kr.com/newsflashes/3821209183522952?f=rss)
- **用AI来管公司，Moka推出三款AI HR工具｜涌现新栏目** — [36kr](https://36kr.com/p/3819979202253189?f=rss)
- **Anthropic最快下周完成逾300亿美元融资轮** — [36kr](https://36kr.com/newsflashes/3821194878947715?f=rss)
- **9点1氪丨永辉超市向王健林等追债超36亿元；《柳叶刀》：全球近12亿人有精神障碍；微信回应“只能撤回2分钟内消息”** — [36kr](https://36kr.com/p/3821177784881541?f=rss)
- **氪星晚报｜优步与印度JSW集团达成协议，合作在印度开发及部署电动汽车；英伟达、AMD、英特尔参投，AI初创公司Hark完成7亿美元融资；神舟二十三号发射在即，各系统准备就绪** — [36kr](https://36kr.com/p/3816943010071427?f=rss)
- **AI时代核心终端生态定位与用户需求洞察| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3820318177841541?f=rss)
- **江行智能：从感知环境到改变世界：物理AI的机遇、路径与实践| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3820298219425924?f=rss)
- **小米YU7家族再推新车，雷军：标准版打特斯拉，GT版狙BBA** — [36kr](https://36kr.com/p/3817022407181188?f=rss)
- **让智能体看见世界：CV × AI Agent 的行业场景新实践| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3820220616495492?f=rss)
- **SpaceX IPO将包含散户配售** — [36kr](https://36kr.com/newsflashes/3821222961025157?f=rss)
- **星巴克叫停AI库存自动盘点工具：上线9个月，错误频出** — [36kr](https://36kr.com/newsflashes/3821221746266498?f=rss)
- **微软支付2.5亿美元了结动视暴雪股东诉讼** — [36kr](https://36kr.com/newsflashes/3821197911675268?f=rss)
- **英特尔推出混合AI解决方案SuperClaw，主打隐私安全与低成本** — [36kr](https://36kr.com/newsflashes/3821197146722696?f=rss)