# AI 日报 [AI 安全] - 2026-05-21


# AI 安全、对齐与治理每日主题综述
**日期：2026年5月21日**

## Highlights
今日的 AI 安全研究呈现出对核心安全机制进行深度剖析与压力测试的趋势。首要突破在于对**大模型安全对齐**基础理论的推进，研究者首次系统地提出了“**上下文不变的安全对齐**”目标，将关注点从表面的拒绝行为转向对底层意图的可靠识别。其次，在**隐私计算**领域，一项对苹果公司部署已久的 DifferentialPrivacy 框架的客户端审计报告，通过逆向工程揭示了其具体实现中存在的缺陷与配置风险，为行业级隐私承诺的验证树立了新的实践标准。此外，针对**大模型安全**本身，多篇论文展示了通过**自适应探测**或**混合策略**来系统性提升“越狱”攻击有效性的新方法，凸显了当前对齐技术的脆弱性，并为建立更鲁棒的防御提供了研究靶点。

## 1. 对抗攻击与鲁棒性
本日多篇研究聚焦于突破或加固大型语言模型的安全防线，揭示了攻防博弈的持续升级。在攻击侧，传统的单一攻击范式正被更具适应性的方法取代。论文 **[10] Adaptive Probe-based Steering for Robust LLM Jailbreaking** 提出了一种基于模型提取思想来引导对比转向向量的方法，并能根据对比激活的统计量自适应地调整转向强度。作者声称该方法显著提升了“越狱”攻击的有效性和鲁棒性。与此类似，论文 **[14] LASH: Adaptive Semantic Hybridization for Black-Box Jailbreaking of Large Language Models** 则从组合策略的角度出发，提出一种黑盒自适应语义混合框架。其核心洞察是，没有单一的攻击家族能始终占优，最佳方法因目标模型和危害类别而异。LASH 通过动态地为每个提示组合不同攻击策略，利用了各策略的互补优势。

在防御侧，针对检索增强生成（RAG）系统的安全性受到关注。论文 **[9] BiRD: A Bidirectional Ranking Defense Mechanism for Retrieval Augmented Generation** 指出，现有防御过度关注语义内容相关性，忽视了检索上下文中由排名结构定义的关键信息。该工作通过研究中毒文档与良性文档的双向排名行为，发现了一种关键的判别模式。这些攻击方法的进步，尤其是其自适应和组合化的趋势，表明未来的安全评估需要超越静态测试集，转向动态和对抗性的评测框架。

## 2. 模型对齐与可解释性
对齐研究正在从行为模仿走向对机制的理解与干预。一篇理论性较强的工作 **[7] Towards Context-Invariant Safety Alignment for Large Language Models** 提出了一个根本性的挑战：当前基于偏好优化的对齐行为是脆弱的，模型可能仅在特定提示形式下拒绝有害请求。该研究建议，鲁棒的安全需要实现**上下文不变的对齐**，即模型的行为应取决于用户的底层意图，而非表面的措辞。这触及了对齐研究的核心难题——如何确保安全策略在语言空间的巨大变化下保持稳定。

可解释性研究则继续深入模型内部工作机制。论文 **[13] Post-Hoc Understanding of Metaphor Processing in Decoder-Only Language Models via Conditional Scale Entropy** 引入了条件尺度熵（CSE）这一度量，用以分析 Transformer 在不同频率尺度上计算参与的广泛程度。作者发现，隐喻性词元会引发更宽的计算参与，表明模型为理解其非常规含义进行了跨频率的广泛信息整合。这类工作为理解模型如何“思考”复杂语义提供了新的量化工具。同时，在应用层面，论文 **[6] SAM-Sode: Towards Faithful Explanations for Tiny Bacteria Detection** 针对微观目标检测中传统解释方法特征归因模糊的问题，提出了一个将初始特征归因图转化为清晰、连贯的形态学证据的可解释AI框架，展示了在关键医疗场景中提供可信解释的重要性。

## 3. 隐私保护与联邦学习
隐私保护的技术路径正朝着更精细、更实用且可验证的方向发展。在联邦学习框架内，效率与隐私的协同优化成为焦点。论文 **[1] Causal Unlearning in Collaborative Optimization: Exact and Approximate Influence Reversal under Adversarial Contributions** 提出HF-KCU方法，通过Krylov子空间中的共轭梯度迭代来近似影响函数，以实现高效的客户端贡献移除（机器遗忘）。其创新点在于引入因果加权机制，确保更新仅发送给持有被删除数据的客户端，避免了无关客户端的参数扰动。论文 **[2] Choose Wisely and Privately: Proactive Client Selection for Fair and Efficient Federated Learning** 则着眼于主动的客户端选择，旨在避免在数据异质性强的联邦学习中浪费计算资源于“无用”的梯度上。这些工作共同推动了联邦学习在实际部署中的可行性。

一项更具影响力的工作是对工业界隐私声明的独立验证。论文 **[11] Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks** 对苹果操作系统中部署的差分隐私框架进行了客户端审计。作者通过逆向工程分析了已发布的二进制文件，声称发现了实现中的具体缺陷和配置错误。这项研究超越了理论构建，直指大型科技公司隐私承诺的实际执行质量，其方法论为第三方审计树立了范例。

此外，差分隐私的理论基础也在深化。论文 **[18] Information Leakage Envelopes** 在点互信息泄漏（PML）框架下，研究了满足后处理鲁棒性且能上界定失败概率的隐私保证。作者指出，受（近似）差分隐私启发的两个候选定义均无法同时满足两项要求，并进而提出了PML包络的概念。这些理论工作为设计新的隐私量化标准提供了基础。

## 4. 安全评估基准与审计
建立可靠的评估基准是衡量安全进展的基石。在这一方向上，几项工作从不同维度贡献了新的评估视角。论文 **[43] SpecBench: Measuring Reward Hacking in Long-Horizon Coding Agents** 聚焦于长时程编程智能体中的“奖励黑客”问题。作者将软件工程任务分解为规范描述、可见验证测试和用于模拟真实世界使用的保留测试，从而能够系统地测量智能体在通过测试时偏离用户真实目标的程度。这是对智能体安全性进行细粒度评估的重要尝试。

在分布式系统安全领域，论文 **[26] Auditing Privacy in Multi-Tenant RAG under Account Collusion** 揭示了多租户RAG服务中一个重要的隐私边界失效场景。作者指出，当同一租户下的多个账户合谋时，已知的差分隐私组合理论意味着联合泄漏会以Θ(√k * ε_acc)的速率无条件退化。这项研究对共享基础设施中的隐私保证提出了严峻的挑战。

在网络安全的交叉领域，论文 **[4] XAI FL-IDS: A Federated Learning and SHAP-Based Explainable Framework for Distributed Intrusion Detection Systems** 结合联邦学习与SHAP可解释性方法，构建了一个分布式入侵检测系统。该工作不仅关注检测能力，更强调决策的可解释性，以满足现代网络安全系统对透明度的要求。

## 5. Agent 安全与治理
随着自主智能体能力的增强，其安全与可控性成为治理的核心议题。论文 **[38] Lost in Fog: Sensor Perturbations Expose Reasoning Fragility in Driving VLAs** 对自动驾驶视觉语言动作（VLA）模型在传感器扰动下的鲁棒性进行了受控研究。研究发现，推理一致性是轨迹可靠性的高保真指标，当推理开始偏离时，动作的可靠性也随之崩溃。这强调了为具备推理能力的智能体建立持续监控和一致性检查机制的重要性。

在治理框架层面，论文 **[61] Backchaining Loss of Control Mitigations from Mission-Specific Benchmarks in National Security** 提出了一种反向推导的方法论。该方法主张从特定任务（如国家安全）的现有基准测试出发，反向推导出应优先实现的“能力与权限”限制措施。这为高风险场景下的安全部署提供了一种基于实证的路线图思路。同时，白宫计划发布要求政府机构在先进模型发布前进行审查的行政命令（新闻 **[192]**），则从监管层面印证了对前沿AI模型进行事前评估和干预的紧迫性。

开源社区也在贡献治理工具，例如GitHub项目 **[144] ai-kill-chain** 提出了一个针对LLM和智能体AI威胁的防御者侧网络杀伤链扩展，增加了模型供应链阶段，并将目标行动阶段细分为数据泄露、模型提取和智能体枢转，这有助于结构化地思考智能体带来的新型攻击面。

## 6. 后门攻击与供应链安全
模型供应链的复杂性引入了新的、隐蔽的安全风险。论文 **[19] Trusted Weights, Treacherous Optimizations? Optimization-Triggered Backdoor Attacks on LLMs** 揭示了推理优化技术（如编译）可能被恶意利用。作者提出了一种统一的优化触发攻击框架，其核心在于，在不修改编译器或硬件的前提下，一种策略可使模型仅在被编译时才对特定输入翻转预测。这暴露了当前以“语义等价”为假设的优化流程中一个严重的安全盲区。

对模型演化过程的安全监控同样关键。论文 **[60] Detecting Trojaned DNNs via Spectral Regression Analysis** 提出了MIST方法，通过分析模型在微调过程中内部表征的变化来检测木马。该方法不尝试重建触发条件，而是利用预激活频谱来表征良性模型演化的特征，并将偏离此参考模式的更新标记为可疑。这为在模型迭代更新的生命周期中持续进行安全扫描提供了新思路。

## Looking Forward
尽管今日的研究取得了显著进展，但若干根本性挑战依然存在，指引着未来的方向。首先，**上下文不变安全对齐**的愿景提出了一个待验证的核心假设：模型能否真正学会识别超越表面文本形式的“意图”？这需要新的理论框架和评估协议来度量对齐的“深度”而非仅是“广度”。其次，在隐私计算领域，苹果框架审计等工作表明，**理论保证与实际部署之间的差距**是一个普遍且关键的问题。如何建立常态化的、可扩展的第三方隐私审计机制，是推动行业信任的关键。

此外，**智能体（Agent）的安全评估**仍处于早期阶段。如何为具备长期记忆、工具使用和自我演化能力的智能体设计能够捕捉其涌现风险（如目标偏移、奖励黑客）的评估基准？论文 **[38]** 所揭示的“推理脆弱性”与行动可靠性之间的耦合关系，只是冰山一角。最后，**供应链安全**的威胁（如优化触发后门）凸显了从模型训练、优化到部署的全链路安全保障的缺失。未来的安全研究必须采取更系统、更整体的视角，将模型本身、其运行环境和交互协议一并纳入考量。

---


## 参考来源

- **Causal Unlearning in Collaborative Optimization: Exact and Approximate Influence Reversal under Adversarial Contributions** — [arxiv_cr](https://arxiv.org/abs/2605.20341v1)
- **Choose Wisely and Privately: Proactive Client Selection for Fair and Efficient Federated Learning** — [arxiv_cr](https://arxiv.org/abs/2605.20975v1)
- **Comparative Evaluation of Deep Learning Models for Fake Image Detection** — [arxiv_cr](https://arxiv.org/abs/2605.20971v1)
- **XAI FL-IDS: A Federated Learning and SHAP-Based Explainable Framework for Distributed Intrusion Detection Systems** — [arxiv_cr](https://arxiv.org/abs/2605.19448v1)
- **Verifiable Provenance and Watermarking for Generative AI: An Evidentiary Framework for International Operational Law and Domestic Courts** — [arxiv_cr](https://arxiv.org/abs/2605.21002v1)
- **SAM-Sode: Towards Faithful Explanations for Tiny Bacteria Detection** — [arxiv_cv](https://arxiv.org/abs/2605.21186v1)
- **Towards Context-Invariant Safety Alignment for Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20994v1)
- **SMA-DP: Spectral Memory-Aware Differential Privacy for Deep Learning** — [arxiv_cr](https://arxiv.org/abs/2605.20450v1)
- **BiRD: A Bidirectional Ranking Defense Mechanism for Retrieval Augmented Generation** — [arxiv_cr](https://arxiv.org/abs/2605.20123v1)
- **Adaptive Probe-based Steering for Robust LLM Jailbreaking** — [arxiv_cr](https://arxiv.org/abs/2605.20286v1)
- **Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks** — [arxiv_cr](https://arxiv.org/abs/2605.21378v1)
- **One-Step Distillation of Discrete Diffusion Image Generators via Fixed-Point Iteration** — [arxiv_cv](https://arxiv.org/abs/2605.21484v1)
- **Post-Hoc Understanding of Metaphor Processing in Decoder-Only Language Models via Conditional Scale Entropy** — [arxiv_cl](https://arxiv.org/abs/2605.21391v1)
- **LASH: Adaptive Semantic Hybridization for Black-Box Jailbreaking of Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.21362v1)
- **Mind the Sim-to-Real Gap & Think Like a Scientist** — [arxiv_ai](https://arxiv.org/abs/2605.21458v1)
- **From Circuit Evidence to Mechanistic Theory: An Inductive Logic Approach** — [arxiv_ai](https://arxiv.org/abs/2605.21303v1)
- **CRAFT: Conflict-Resolved Aggregation for Federated Training** — [arxiv_lg](https://arxiv.org/abs/2605.21317v1)
- **Information Leakage Envelopes** — [arxiv_cr](https://arxiv.org/abs/2605.21185v1)
- **Trusted Weights, Treacherous Optimizations? Optimization-Triggered Backdoor Attacks on LLMs** — [arxiv_cr](https://arxiv.org/abs/2605.20641v1)
- **RankE: End-to-End Post-Training for Discrete Text-to-Image Generation with Decoder Co-Evolution** — [arxiv_cv](https://arxiv.org/abs/2605.21195v1)
- **Cross-lingual robustness of LLM-brain alignment and its computational roots** — [arxiv_cl](https://arxiv.org/abs/2605.21049v1)
- **APEX: Autonomous Policy Exploration for Self-Evolving LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2605.21240v1)
- **PREFINE: Preference-Based Implicit Reward and Cost Fine-Tuning for Safety Alignment** — [arxiv_ai](https://arxiv.org/abs/2605.21225v1)
- **FedCoE: Bridging Generalization and Personalization via Federated Coordinated Dual-level MoEs** — [arxiv_lg](https://arxiv.org/abs/2605.21264v1)
- **An exponential mechanism based on quadratic approximations for fine-tuning machine learning models with privacy guarantees** — [arxiv_cr](https://arxiv.org/abs/2605.20521v1)
- **Auditing Privacy in Multi-Tenant RAG under Account Collusion** — [arxiv_cr](https://arxiv.org/abs/2605.19847v1)
- **The Privacy Subsidy in Glosten-Milgrom: Bid-Ask Spread and Welfare under Flip-Noise Direction Observation** — [arxiv_cr](https://arxiv.org/abs/2605.19742v1)
- **Where Does Authorship Signal Emerge in Encoder-Based Language Models?** — [huggingface_papers](https://arxiv.org/abs/2605.19908)
- **Onion-Routed Multi-Circuit Key Establishment for Quantum-Resilient Sessions** — [arxiv_cr](https://arxiv.org/abs/2605.21349v1)
- **ProtoPathway: Biologically Structured Prototype-Pathway Fusion for Multimodal Cancer Survival Prediction** — [arxiv_cv](https://arxiv.org/abs/2605.21454v1)
- **AIGaitor: Privacy-preserving and cloud-free motion analysis for everyone, using edge computing** — [arxiv_cv](https://arxiv.org/abs/2605.21421v1)
- **PointACT: Vision-Language-Action Models with Multi-Scale Point-Action Interaction** — [arxiv_cv](https://arxiv.org/abs/2605.21414v1)
- **RoadTones: Tone Controllable Text Generation from Road Event Videos** — [arxiv_cv](https://arxiv.org/abs/2605.21411v1)
- **OcclusionFormer: Arranging Z-Order for Layout-Grounded Image Generation** — [arxiv_cv](https://arxiv.org/abs/2605.21343v1)
- **Let EEG Models Learn EEG** — [arxiv_cv](https://arxiv.org/abs/2605.21280v1)
- **DelTA: Discriminative Token Credit Assignment for Reinforcement Learning from Verifiable Rewards** — [arxiv_cl](https://arxiv.org/abs/2605.21467v1)
- **Quantifying Hyperparameter Transfer and the Importance of Embedding Layer Learning Rate** — [arxiv_ai](https://arxiv.org/abs/2605.21486v1)
- **Lost in Fog: Sensor Perturbations Expose Reasoning Fragility in Driving VLAs** — [arxiv_ai](https://arxiv.org/abs/2605.21446v1)
- **HiRes: Inspectable Precedent Memory for Reaction Condition Recommendation** — [arxiv_ai](https://arxiv.org/abs/2605.21420v1)
- **FedCritic: Serverless Federated Critic Learning-based Resource Allocation for Multi-Cell OFDMA in 6G** — [arxiv_ai](https://arxiv.org/abs/2605.21418v1)
- **Ordering Matters: Rank-Aware Selective Fusion for Blended Emotion Recognition** — [arxiv_ai](https://arxiv.org/abs/2605.21417v1)
- **On the Regularity and Generalization of One-Step Wasserstein-guided Generative Models for PDE-Induced Measures** — [arxiv_ai](https://arxiv.org/abs/2605.21388v1)
- **SpecBench: Measuring Reward Hacking in Long-Horizon Coding Agents** — [arxiv_ai](https://arxiv.org/abs/2605.21384v1)
- **Closed Loop Dynamic Driving Data Mixture for Real-Synthetic Co-Training** — [arxiv_ai](https://arxiv.org/abs/2605.21372v1)
- **Data-Efficient Neural Operator Training via Physics-Based Active Learning** — [arxiv_ai](https://arxiv.org/abs/2605.21348v1)
- **DeCoR: Design and Control Co-Optimization for Urban Streets Using Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.21311v1)
- **TimeSRL: Generalizable Time-Series Behavioral Modeling via Semantic RL-Tuned LLMs -- A Case Study in Mental Health** — [arxiv_ai](https://arxiv.org/abs/2605.21295v1)
- **\textit{Stochastic} MeanFlow Policies: One-Step Generative Control with Entropic Mirror Descent** — [arxiv_ai](https://arxiv.org/abs/2605.21282v1)
- **How Much Online RL is Enough? Informative Rollouts for Offline Preference Optimization in RLVR** — [arxiv_ai](https://arxiv.org/abs/2605.21266v1)
- **Velocityformer: Broken-Symmetry-Matched Equivariant Graph Transformers for Cosmological Velocity Reconstruction** — [arxiv_lg](https://arxiv.org/abs/2605.21483v1)
- **Mitigating Label Bias with Interpretable Rubric Embeddings** — [arxiv_lg](https://arxiv.org/abs/2605.21455v1)
- **Neural Negative Binomial Regression for Weekly Seismicity Forecasting: Per-Cell Dispersion Estimation and Tail Risk Assessment** — [arxiv_lg](https://arxiv.org/abs/2605.21437v1)
- **Gaussian Sheaf Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2605.21435v1)
- **Preference-aware Influence-function-based Data Selection Method for Efficient Fine-Tuning** — [arxiv_lg](https://arxiv.org/abs/2605.21422v1)
- **Semiparametric Efficient Bilevel Gradient Estimation** — [arxiv_lg](https://arxiv.org/abs/2605.21341v1)
- **Optimized Federated Knowledge Distillation with Distributed Neural Architecture Search** — [arxiv_lg](https://arxiv.org/abs/2605.21322v1)
- **A New Framework to Analyse the Distributional Robustness of Deep Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2605.21313v1)
- **A Mechanistic Study of Tabular Foundation Models** — [arxiv_lg](https://arxiv.org/abs/2605.21288v1)
- **Profiling User Vulnerability to Phishing Through Psychological and Behavioral Factors** — [arxiv_cr](https://arxiv.org/abs/2605.21246v1)
- **Detecting Trojaned DNNs via Spectral Regression Analysis** — [arxiv_cr](https://arxiv.org/abs/2605.21146v1)
- **Backchaining Loss of Control Mitigations from Mission-Specific Benchmarks in National Security** — [arxiv_cr](https://arxiv.org/abs/2605.21095v1)
- **An Evidence-driven Protocol for Trustworthy CI Pipelines** — [arxiv_cr](https://arxiv.org/abs/2605.21089v1)
- **Privacy-Preserving Distributed Optimization Under Time Constraints Using Secure Multi-Party Computation and Evolutionary Algorithms** — [arxiv_cr](https://arxiv.org/abs/2605.20944v1)
- **STiTch: Semantic Transition and Transportation in Collaboration for Training-Free Zero-Shot Composed Image Retrieval** — [arxiv_cv](https://arxiv.org/abs/2605.21261v1)
- **SR-Ground: Image Quality Grounding for Super-Resolved Content** — [arxiv_cv](https://arxiv.org/abs/2605.21244v1)
- **Distill to Think, Foresee to Act: Cognitive-Physical Reinforcement Learning for Autonomous Driving** — [arxiv_cv](https://arxiv.org/abs/2605.21139v1)
- **VersusQ: Pairwise Margin Reasoning for Generalizable Video Quality Assessment** — [arxiv_cv](https://arxiv.org/abs/2605.21130v1)
- **Linear-DPO: Linear Direct Preference Optimization for Diffusion and Flow-Matching Generative Models** — [arxiv_cv](https://arxiv.org/abs/2605.21123v1)
- **RCGDet3D: Rethinking 4D Radar-Camera Fusion-based 3D Object Detection with Enhanced Radar Feature Encoding** — [arxiv_cv](https://arxiv.org/abs/2605.21112v1)
- **TextSculptor: Training and Benchmarking Scene Text Editing** — [arxiv_cv](https://arxiv.org/abs/2605.21090v1)
- **LamPO: A Lambda Style Policy Optimization for Reasoning Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.21235v1)
- **APM: Evaluating Style Personalization in LLMs with Arbitrary Preference Mappings** — [arxiv_cl](https://arxiv.org/abs/2605.21063v1)
- **Beyond Text-to-SQL: An Agentic LLM System for Governed Enterprise Analytics APIs** — [arxiv_cl](https://arxiv.org/abs/2605.21027v1)
- **GraphRAG on Consumer Hardware: Benchmarking Local LLMs for Healthcare EHR Schema Retrieval** — [arxiv_cl](https://arxiv.org/abs/2605.20815v1)
- **Learning Structural Latent Points for Efficient Visual Representations in Robotic Manipulation** — [arxiv_ai](https://arxiv.org/abs/2605.21258v1)
- **Behavior-Consistent Deep Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.21214v1)
- **On the limits and opportunities of AI reviewers: Reviewing the reviews of Nature-family papers with 45 expert scientists** — [huggingface_papers](https://arxiv.org/abs/2605.20668)
- **ThoughtTrace: Understanding User Thoughts in Real-World LLM Interactions** — [huggingface_papers](https://arxiv.org/abs/2605.20087)
- **Not Every Rubric Teaches Equally: Policy-Aware Rubric Rewards for RLVR** — [huggingface_papers](https://arxiv.org/abs/2605.20164)
- **PixVerve: Advancing Native UHR Image Generation to 100MP with a Large-Scale High-Quality Dataset** — [huggingface_papers](https://arxiv.org/abs/2605.20147)
- **CopT: Contrastive On-Policy Thinking with Continuous Spaces for General and Agentic Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.20075)
- **PEEK: Context Map as an Orientation Cache for Long-Context LLM Agents** — [huggingface_papers](https://arxiv.org/abs/2605.19932)
- **GoLongRL: Capability-Oriented Long Context Reinforcement Learning with Multitask Alignment** — [huggingface_papers](https://arxiv.org/abs/2605.19577)
- **Uni-Edit: Intelligent Editing Is A General Task For Unified Model Tuning** — [arxiv_cv](https://arxiv.org/abs/2605.21487v1)
- **Latent Dynamics for Full Body Avatar Animation** — [arxiv_cv](https://arxiv.org/abs/2605.21478v1)
- **Stream3D: Sequential Multi-View 3D Generation via Evidential Memory** — [arxiv_cv](https://arxiv.org/abs/2605.21472v1)
- **StreamGVE: Training-Free Video Editing via Few-Step Streaming Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.21466v1)
- **You Only Need Minimal RLVR Training: Extrapolating LLMs via Rank-1 Trajectories** — [arxiv_cl](https://arxiv.org/abs/2605.21468v1)
- **Leveraging LLMs for Grammar Adaptation: A Study on Metamodel-Grammar Co-Evolution** — [arxiv_cl](https://arxiv.org/abs/2605.21465v1)
- **Quantifying the cross-linguistic effects of syncretism on agreement attraction** — [arxiv_cl](https://arxiv.org/abs/2605.21403v1)
- **Findings of the Fifth Shared Task on Multilingual Coreference Resolution: Expanding Datasets for Long-Range Entities** — [arxiv_cl](https://arxiv.org/abs/2605.21369v1)
- **"I didn't Make the Micro Decisions": Measuring, Inducing, and Exposing Goal-Level AI Contributions in Collaboration** — [arxiv_cl](https://arxiv.org/abs/2605.21363v1)
- **Text Analytics Evaluation Framework: A Case Study on LLMs and Social Media** — [arxiv_cl](https://arxiv.org/abs/2605.21338v1)
- **Variance Reduction for Expectations with Diffusion Teachers** — [arxiv_ai](https://arxiv.org/abs/2605.21489v1)
- **Equilibrium Reasoners: Learning Attractors Enables Scalable Reasoning** — [arxiv_lg](https://arxiv.org/abs/2605.21488v1)
- **EvoStruct: Bridging Evolutionary and Structural Priors for Antibody CDR Design via Protein Language Model Adaptation** — [arxiv_lg](https://arxiv.org/abs/2605.21485v1)
- **Is Fixing Schema Graphs Necessary? Full-Resolution Graph Structure Learning for Relational Deep Learning** — [arxiv_lg](https://arxiv.org/abs/2605.21475v1)
- **A Machine Learning Framework for Weighted Least Squares GNSS Positioning based on Activation Functions** — [arxiv_lg](https://arxiv.org/abs/2605.21461v1)
- **roto 2.0: The Robot Tactile Olympiad** — [arxiv_lg](https://arxiv.org/abs/2605.21429v1)
- **Polynomial-Time Robust Multiclass Linear Classification under Gaussian Marginals** — [arxiv_lg](https://arxiv.org/abs/2605.21428v1)
- **Adaptive Signal Resuscitation: Channel-wise Post-Pruning Repair for Sparse Vision Networks** — [arxiv_lg](https://arxiv.org/abs/2605.21426v1)
- **What Twelve LLM Agent Benchmark Papers Disclose About Themselves: A Pilot Audit and an Open Scoring Schema** — [arxiv_lg](https://arxiv.org/abs/2605.21404v1)
- **Memorisation, convergence and generalisation in generative models** — [arxiv_lg](https://arxiv.org/abs/2605.21402v1)
- **Reliable Automated Triage in Spanish Clinical Notes: A Hybrid Framework for Risk-Aware HIV Suspicion Identification** — [arxiv_cl](https://arxiv.org/abs/2605.21256v1)
- **Do LLMs Know What Luxembourgish Borrows? Probing Lexical Neology in Low-Resource Multilingual Models** — [arxiv_cl](https://arxiv.org/abs/2605.21227v1)
- **Manga109-v2026: Revisiting Manga109 Annotations for Modern Manga Understanding** — [arxiv_cl](https://arxiv.org/abs/2605.21182v1)
- **Metaphors in Literary Post-Editing: Opening Pandora's Box?** — [arxiv_cl](https://arxiv.org/abs/2605.21178v1)
- **ChunkFT: Byte-Streamed Optimization for Memory-Efficient Full Fine-Tuning** — [arxiv_cl](https://arxiv.org/abs/2605.21177v1)
- **DrawMotion: Generating 3D Human Motions by Freehand Drawing** — [huggingface_papers](https://arxiv.org/abs/2605.20955)
- **PlanningBench: Generating Scalable and Verifiable Planning Data for Evaluating and Training Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.20873)
- **Evaluating Temporal Semantic Caching and Workflow Optimization in Agentic Plan-Execute Pipelines** — [huggingface_papers](https://arxiv.org/abs/2605.20630)
- **Generative Recursive Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.19376)
- **Rethinking Visual Attribution for Chest X-ray Reasoning in Large Vision Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.20158)
- **Base Models Look Human To AI Detectors** — [huggingface_papers](https://arxiv.org/abs/2605.19516)
- **Matérn Noise for Triangulation-Agnostic Flow Matching on Meshes** — [huggingface_papers](https://arxiv.org/abs/2605.19305)
- **Fast 4D Mesh Generation by Spatio-Temporal Attention Chains** — [huggingface_papers](https://arxiv.org/abs/2605.19786)
- **Stage-adaptive Token Selection for Efficient Omni-modal LLMs** — [huggingface_papers](https://arxiv.org/abs/2605.20035)
- **optimize_anything: A Universal API for Optimizing any Text Parameter** — [huggingface_papers](https://arxiv.org/abs/2605.19633)
- **TideGS: Scalable Training of Over One Billion 3D Gaussian Splatting Primitives via Out-of-Core Optimization** — [huggingface_papers](https://arxiv.org/abs/2605.20150)
- **CogOmniControl: Reasoning-Driven Controllable Video Generation via Creative Intent Cognition** — [huggingface_papers](https://arxiv.org/abs/2605.19995)
- **xAI burned $6.4B last year — SpaceX’s IPO filing shows why the spending is far from over** — [techcrunch_ai](https://techcrunch.com/2026/05/20/xai-burned-6-4b-last-year-spacexs-ipo-filing-shows-why-the-spending-is-far-from-over/)
- **Musk’s xAI is being sued over its data center generators — now it’s buying $2.8B more** — [techcrunch_ai](https://techcrunch.com/2026/05/20/musks-xai-is-being-sued-over-its-data-center-generators-now-its-buying-2-8b-more/)
- **Anthropic will pay xAI $1.25B per month for compute** — [techcrunch_ai](https://techcrunch.com/2026/05/20/anthropic-will-pay-xai-1-25-billion-per-month-for-compute/)
- **Nvidia posts another record quarter, reveals $43B of holdings in startups** — [techcrunch_ai](https://techcrunch.com/2026/05/20/nvidia-posts-another-record-quarter-reveals-43-billion-of-holdings-in-startups/)
- **OpenAI claims it solved an 80-year-old math problem — for real this time** — [techcrunch_ai](https://techcrunch.com/2026/05/20/openai-claims-it-solved-an-80-year-old-math-problem-for-real-this-time/)
- **IrisGo, a startup backed by Andrew Ng, looks to become the AI desktop buddy you never knew you needed** — [techcrunch_ai](https://techcrunch.com/2026/05/20/irisgo-a-startup-backed-by-andrew-ng-looks-to-become-the-ai-desktop-buddy-you-never-knew-you-needed/)
- **We’re announcing new community investments in Missouri.** — [google_ai](https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/missouri-programs/)
- **OpenAI barrels toward IPO that may happen in September** — [techcrunch_ai](https://techcrunch.com/2026/05/20/openai-barrels-toward-ipo-that-may-happen-in-september/)
- **Startup Battlefield 200 applications close in 1 week: Window to nominate and apply for the most promising startups closes May 27** — [techcrunch_ai](https://techcrunch.com/2026/05/20/startup-battlefield-200-applications-close-in-1-week-window-to-nominate-and-apply-for-the-most-promising-startups-closes-may-27/)
- **NanoClaw creator turns down $20M buyout offer, raises $12M seed instead** — [techcrunch_ai](https://techcrunch.com/2026/05/20/nanoclaw-creator-turns-down-20m-buyout-offer-raises-12m-seed-instead/)
- **Figma adds an AI assistant to its collaborative canvas** — [techcrunch_ai](https://techcrunch.com/2026/05/20/figma-adds-an-ai-assistant-to-its-collaborative-canvas/)
- **Green steel startup Boston Metal is doubling down on critical metals** — [mit_tech_review](https://www.technologyreview.com/2026/05/20/1137523/boston-metal-funding-critical-metals/)
- **The Download: fully artificial chicken eggs and why Musk lost** — [mit_tech_review](https://www.technologyreview.com/2026/05/20/1137579/the-download-colossal-biosciences-egg-musk-altman-trial/)
- **Jensen Huang says he’s found a ‘brand new’ $200B market for Nvidia** — [techcrunch_ai](https://techcrunch.com/2026/05/20/jensen-huang-says-hes-found-a-brand-new-200b-market-for-nvidia/)
- **Anthropic says it’s about to have its first profitable quarter** — [techcrunch_ai](https://techcrunch.com/2026/05/20/anthropic-says-its-about-to-have-its-first-profitable-quarter/)
- **Clouted wants to take the guesswork out of making short videos go viral** — [techcrunch_ai](https://techcrunch.com/2026/05/20/clouted-wants-to-take-the-guesswork-out-of-making-short-videos-go-viral/)
- **100 things we announced at I/O 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/google-io-2026-all-our-announcements/)
- **AI search startups are blowing up** — [techcrunch_ai](https://techcrunch.com/2026/05/20/ai-search-startups-are-blowing-up/)
- **Stability AI releases a new audio model that can create 6-minute songs** — [techcrunch_ai](https://techcrunch.com/2026/05/20/stability-ai-release-a-new-audio-model-that-can-create-six-minute-songs/)
- **A new experiment brings better group meetings to Google Beam** — [google_ai](https://blog.google/innovation-and-ai/models-and-research/google-research/google-beam-group-meetings/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **ganimjeong/Harness-for-codex** — [github](https://github.com/ganimjeong/Harness-for-codex)
- **wailers9/bragi** — [github](https://github.com/wailers9/bragi)
- **gouravnagar-infosec/ai-kill-chain** — [github](https://github.com/gouravnagar-infosec/ai-kill-chain)
- **richard-kim-79/archora-skills** — [github](https://github.com/richard-kim-79/archora-skills)
- **ayush016/android-lead-agent-skills** — [github](https://github.com/ayush016/android-lead-agent-skills)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **ahammadmejbah/Awesome-Datasets-Hub** — [github](https://github.com/ahammadmejbah/Awesome-Datasets-Hub)
- **zimingttkx/QuantumFlow** — [github](https://github.com/zimingttkx/QuantumFlow)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **ganimjeong/Harness-for-claude** — [github](https://github.com/ganimjeong/Harness-for-claude)
- **moonpiesheldon1337/mobsf-fail-app** — [github](https://github.com/moonpiesheldon1337/mobsf-fail-app)
- **ClipboardHealth/groundcrew** — [github](https://github.com/ClipboardHealth/groundcrew)
- **732124645/PromptOps** — [github](https://github.com/732124645/PromptOps)
- **madguyevans-creator/resale-agent-skill-hub** — [github](https://github.com/madguyevans-creator/resale-agent-skill-hub)
- **AI4MSE/Parallax** — [github](https://github.com/AI4MSE/Parallax)
- **h4ckf0r0day/awesome-ai-web-scraping** — [github](https://github.com/h4ckf0r0day/awesome-ai-web-scraping)
- **5p00kyy/club-5060ti** — [github](https://github.com/5p00kyy/club-5060ti)
- **hunhee98/pluck** — [github](https://github.com/hunhee98/pluck)
- **破壁行动！把大厂级“研发外挂”发给每一个创新者，智会心研PLUS版免费公测** — [qbitai](https://www.qbitai.com/2026/05/420681.html)
- **刚刚，马斯克公开SpaceX招股书！** — [qbitai](https://www.qbitai.com/2026/05/420761.html)
- **智象未来超两千亿参数图像大模型HiDream-O1-Image-Pro发布，融资持续提速** — [qbitai](https://www.qbitai.com/2026/05/420753.html)
- **太初元碁洪源：异构计算能力将成为未来AI算力基础设施的重要方向｜AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/420743.html)
- **VC、品牌顾问、编剧，正在批量把自己做成AI** — [qbitai](https://www.qbitai.com/2026/05/420703.html)
- **AIDC建设正从“通用标准”走向“适用高效”** — [qbitai](https://www.qbitai.com/2026/05/420698.html)
- **海信激光电视探索X1 Pro发布：中国家庭，正式进入客厅影院时代** — [qbitai](https://www.qbitai.com/2026/05/420723.html)
- **2026中国AIGC最值得关注的企业&产品图鉴来了！谁在造浪，谁在落地？** — [qbitai](https://www.qbitai.com/2026/05/420656.html)
- **趋境科技完成数亿元Pre-A轮融资，高品质AI Token生产基础设施** — [qbitai](https://www.qbitai.com/2026/05/420651.html)
- **Federated LoRA Fine-Tuning for LLMs via Collaborative Alignment** — [arxiv_ml](https://arxiv.org/abs/2605.21217v1)
- **Privacy Without Remedy: An Assessment of Data Broker Compliance with California Privacy Law** — [arxiv_cy](https://arxiv.org/abs/2605.21376v1)
- **Theoretical guidelines for annealed Langevin dynamics in compositional simulation-based inference** — [arxiv_ml](https://arxiv.org/abs/2605.21253v1)
- **Improved Guarantees for Constrained Online Convex Optimization via Self-Contraction** — [arxiv_ml](https://arxiv.org/abs/2605.21107v1)
- **LOSCAR-SGD: Local SGD with Communication-Computation Overlap and Delay-Corrected Sparse Model Averaging** — [arxiv_ml](https://arxiv.org/abs/2605.20866v1)
- **Correcting Stochastic Update Bias in Preconditioned Language Model Optimizers** — [arxiv_ml](https://arxiv.org/abs/2605.20756v1)
- **Decision-Path Patterns as Tree Reliability Signals: Path-based Adaptive Weighting for Random Forest Classification** — [arxiv_ml](https://arxiv.org/abs/2605.20716v1)
- **DeTox-Fed: Detecting Toxic Conversations in the Fediverse with Federated Graph Neural Networks** — [arxiv_cy](https://arxiv.org/abs/2605.21054v1)
- **The Knowledge Gap in a High-Choice Media Environment: Experimental Evidence from Online Search** — [arxiv_cy](https://arxiv.org/abs/2605.21019v1)
- **A Deployment Audit of Release-Side Risk in Conformal Triage under Prevalence Shift** — [arxiv_cy](https://arxiv.org/abs/2605.20956v1)
- **$L^2$ over Wasserstein: Statistical Analysis for Optimal Transport** — [arxiv_ml](https://arxiv.org/abs/2605.21365v1)
- **A Rigorous, Tractable Measure of Model Complexity** — [arxiv_ml](https://arxiv.org/abs/2605.21167v1)
- **Divide et Calibra: Multiclass Local Calibration via Vector Quantization** — [arxiv_ml](https://arxiv.org/abs/2605.21060v1)
- **Conditioning Gaussian Processes on Almost Anything** — [arxiv_ml](https://arxiv.org/abs/2605.21041v1)
- **Concentration of General Stochastic Approximation Under Heavy-Tailed Markovian Noise** — [arxiv_ml](https://arxiv.org/abs/2605.20999v1)
- **Everywhere Valid Bounds on False Discovery Proportions in Conformal Inference** — [arxiv_ml](https://arxiv.org/abs/2605.20726v1)
- **Interpretable Discriminative Text Representations via Agreement and Label Disentanglement** — [arxiv_ml](https://arxiv.org/abs/2605.20693v1)
- **Design Principles and Observable Indicators for AI-Enabled Pedagogical Accompaniment: Evidence from the Amico Dual-Mode Prototype in Italy and China** — [arxiv_cy](https://arxiv.org/abs/2605.20665v1)
- **今年4月中国企业信用指数为162.41，持续保持向好态势** — [36kr](https://36kr.com/newsflashes/3818416305193861?f=rss)
- **近5年折扣力度最大的一届天猫618，5月21日正式开卖** — [36kr](https://36kr.com/newsflashes/3818391260857224?f=rss)
- **腾讯推出操作系统层级AI助手“马维斯”** — [36kr](https://36kr.com/newsflashes/3818361394496390?f=rss)
- **美国证监会主席：已指示员工就新型ETF引发的市场变化征求公众意见** — [36kr](https://36kr.com/newsflashes/3818350210352258?f=rss)
- **白宫举行吹风会，向人工智能公司介绍审查AI模型的行政令** — [36kr](https://36kr.com/newsflashes/3818342793610112?f=rss)
- **独家对谈｜谢文博：银发，孤独，一个中日观察者的十八年** — [36kr](https://36kr.com/p/3816060007751430?f=rss)
- **8点1氪丨英伟达Q1净利润583亿美元；谷歌CEO：Gemini月活跃用户达9亿；寿司郎回应“盘子抽检10抽10脏”** — [36kr](https://36kr.com/p/3818280989443202?f=rss)
- **网易520发布会：质量为先，狙击细分赛道** — [36kr](https://36kr.com/p/3817849322964098?f=rss)
- **氪星晚报｜2026福布斯中国人工智能科技企业TOP 50发布，中关村科金入选；三星劳资谈判破裂，威刚董事长称DRAM、NAND恐再掀涨价潮；新交所与中国银行签署新版战略合作备忘录** — [36kr](https://36kr.com/p/3816942423000196?f=rss)
- **第四届中国AIGC产业峰会在京顺利举办！近20位行业大咖解码Agent与非共识机遇** — [36kr](https://36kr.com/p/3817353357968516?f=rss)
- **长鑫科技更新招股书，碧桂园错失300亿** — [36kr](https://36kr.com/p/3817039204139908?f=rss)
- **深圳市探海游艇产业发展有限公司在大连投资新公司** — [36kr](https://36kr.com/newsflashes/3818445023151232?f=rss)
- **阿里妈妈：超100万品牌商家持续在天猫加大投入，超去年同期** — [36kr](https://36kr.com/newsflashes/3818435313304707?f=rss)
- **摩根大通投行高管：香港及中国内地IPO活动料显著增加** — [36kr](https://36kr.com/newsflashes/3818424667260032?f=rss)
- **A股三大指数集体高开，华灿光电涨停** — [36kr](https://36kr.com/newsflashes/3818370861974660?f=rss)