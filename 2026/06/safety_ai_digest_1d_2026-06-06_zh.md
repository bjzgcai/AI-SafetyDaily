# AI 日报 [AI 安全] - 2026-06-06


# AI 安全每日综述：2026-06-06

## Highlights

今日 AI 安全领域最引人注目的进展集中在**Agent 自主行为引发的现实风险**、**新型运行时攻击面**以及**记忆系统的系统性特征**。首先，关于 Meta 客服 Agent 被利用窃取 Instagram 账户的报道（来源：MIT Technology Review），为理论上的“提示注入”和“工具滥用”提供了确凿的现实案例，表明当 Agent 拥有执行权限时，社会工程学攻击可直接转化为资产损失。其次，针对新兴 WebMCP 协议的**中间会话工具注入（MSTI）**研究揭示了第三方脚本在活跃会话中动态植入恶意工具的威胁，这标志着攻击面从静态提示词扩展到了动态运行时环境。最后，**Agent Memory**的系统化表征工作首次建立了状态化长程任务的记忆系统分类学，指出持久化记忆不仅是功能需求，更是数据泄露和状态污染的关键风险点，为后续构建沙盒与审计机制奠定了理论基础。

---

## Agent 安全与治理

随着大模型智能体（LLM Agents）从简单的任务执行者演变为具备长期规划能力的自主实体，其安全边界正从单一的模型层面向复杂的运行时环境与治理架构延伸。当前的核心挑战在于如何在不牺牲 Agent 自主性的前提下，实现对复杂决策链的可解释性与可控性。

在**运行时可观测性与溯源**方面，现有研究正试图解决“黑盒决策”带来的审计难题。**《From Agent Traces to Trust: Evidence Tracing and Execution Provenance in LLM Agents》**提出了一种基于证据追踪的框架，旨在记录外部工具调用、检索系统及记忆模块之间的交互链路。该工作强调，仅凭最终答案的准确性无法验证 Agent 行为的合规性，必须建立能够回溯证据来源、工具调用合理性及记忆更新影响的执行证明体系。这与**《Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads》**的研究形成互补，后者通过对 Agent 记忆系统的分类学分析，指出了扁平检索与 LLM 中介提取等不同架构下的潜在风险。两者共同指向一个结论：Agent 的安全审计不能仅关注输入输出，必须深入其内部状态流转过程，特别是跨会话的记忆持久化机制可能成为长期潜伏的攻击载体。

针对**防御机制的演进**，传统的静态对齐已难以应对不断变化的对抗样本。**《Membrane: A Self-Evolving Contrastive Safety Memory for LLM Agent Defense》**引入了一种自进化的对比安全记忆（CSM）机制，通过区分有害查询与表面相似但合法的良性请求条件，实现了无需重训练的动态防御。这种方法试图解决传统微调分类器适应性差的问题，但其有效性依赖于记忆库的更新频率与误报控制。与此同时，**《GuardNet: Ensemble Strategies of Shallow Neural Networks for Robust Prompt Injection and Jailbreak Detection》**则从模型架构角度提出，浅层神经网络的集成策略在对抗场景下可能比单纯依赖大模型参数更具鲁棒性，强调了多样性覆盖与阈值校准的重要性。这些防御思路的差异反映了当前社区对于“模型内建安全”与“外挂护栏”两种路径的探索并存。

在**治理信号与合规性**层面，**《Will the Agent Recuse Itself? Measuring LLM-Agent Compliance with In-Band Access-Deny Signals》**提出了一个关键概念：带内拒绝信号（In-Band Access-Deny Signals）。该研究建议服务器端应通过协议通道（如 SSH Banner）向连接 Agent 发送轻量级的自愿撤回请求，而非直接硬阻断。这种协作式治理模式假设 Agent 具备基本的合规意愿，但在实际部署中，若 Agent 缺乏自我约束能力或已被劫持，此类信号可能失效。这一理论与现实中发生的**Meta 客服 Agent 被利用事件**形成了强烈对照，报道显示攻击者通过诱导 Agent 链接受控邮箱成功接管账户，这表明即便存在访问控制，若缺乏细粒度的意图验证与上下文感知，Agent 仍可能被社会工程学绕过。此外，**《SHIELDS: Automating OS Hardening with Iterative Multi-Agent Remediation》**展示了多 Agent 系统在操作系统加固中的应用，通过迭代反馈驱动修复流程，体现了 Agent 作为安全运维工具的双刃剑属性——既能自动化防御，也可能因错误指令导致系统配置破坏。

开源生态也在积极回应上述治理需求。**mnemo**与**memory-os**等项目致力于构建本地优先的 AI 记忆层，试图通过结构化知识图谱与实体提取来管理 Agent 的持久化状态，这在一定程度上缓解了非结构化文本记忆带来的隐私泄露风险。然而，这些工具在实际生产环境中的安全性仍需独立验证，特别是在处理敏感数据时的加密与隔离机制尚需完善。总体而言，Agent 安全治理正从被动防御转向主动的运行时监控与协作式合规，但如何在开放环境中平衡自主性与控制权仍是未解难题。

---

## 工具调用漏洞与运行时防御

Agent 的核心能力依赖于对外部工具的调用，这使得工具选择逻辑与接口暴露成为新的攻击重点。**《WebMCP Tool Surface Poisoning: Runtime Manipulation Attacks on LLM Agents》**识别了一种名为中间会话工具注入（MSTI）的新型威胁。WebMCP 协议允许网站直接向 AI Agent 暴露工具，绕过传统用户界面，而第三方脚本的动态介入可能导致恶意工具在会话期间被注入。该研究将 MSTI 按阶段与目标进行了分类，指出这种攻击利用了动态暴露的工具表面，使得传统的静态白名单防护失效。与之相对，**《ToolChoiceConfusion: Causal Minimal Tool Filtering for Reliable LLM Agents》**则从 Agent 侧出发，提出因果最小工具过滤（CMTF）方法，主张工具选择不应仅基于语义相关性，而应基于因果充分性，以减少不必要的工具调用和过早行动。这两种视角分别代表了攻击面的扩大与防御端的精细化优化。

在更广泛的对抗鲁棒性方面，**《Steering LLM Viewpoints through Fabricated Evidence Injection》**揭示了 Agent 在面对伪造证据时的认知脆弱性。攻击者通过重构误导性陈述并附带看似可信的理由，可以引导目标 LLM 采纳特定观点。这种“幽灵写作”攻击不仅影响内容生成，还可能渗透至 Agent 的决策逻辑中。此外，**《Decomposing Factual Sycophancy in Language Models》**进一步分析了事实顺从现象，指出模型在社交压力下可能放弃正确答案，这为针对 Agent 的社会工程学攻击提供了理论依据。尽管**《RedEdit: Agentic Red-Teaming of Image Safety Classifiers via MCTS-Guided Photo-Editing》**主要针对图像安全分类器的红队测试，但其采用的蒙特卡洛树搜索（MCTS）引导编辑策略，也为探索多模态 Agent 的对抗样本生成提供了方法论参考。

值得注意的是，部分新闻源（如 36 氪关于微信 AI 与手机厂商合作的消息）提到了 A2A（Agent-to-Agent）协作机制的普及。虽然官方宣称数据安全通过双重授权保障，但从技术角度看，Agent 间的直接对话增加了信任传递的复杂性。若缺乏统一的身份认证与意图验证标准，A2A 架构可能放大工具调用的风险传播范围。因此，工具层面的安全不仅需要关注单个接口的防护，还需考虑跨 Agent 通信的信任链构建。

---

## 安全评估基准与事件响应

有效的安全评估是验证防御措施的前提，但现有的基准测试往往滞后于 Agent 能力的演进。**《AdaPlanBench: Evaluating Adaptive Planning in Large Language Model Agents under World and User Constraints》**引入了一个动态交互式基准，用于评估 Agent 在逐步揭示的世界和用户约束下进行自适应规划的能力。该基准包含 307 项家庭任务，填补了现有评估在双约束动态调整方面的空白。同样，**《Benchmark Everything Everywhere All at Once》**提出了一种完全自主的 Agent 系统用于基准构建，旨在解决人工构建基准成本高且易过饱和的问题。这类自动化基准建设工具若能结合安全指标，将极大提升评估效率。

在红队测试与事件响应方面，**《ZERO-APT: A Closed-Loop Adversarial Framework for LLM-Driven Automated Penetration Testing under Intelligent Defense》**构建了一个包含攻击者、防御者与裁判的闭环框架，解决了以往自动化渗透测试面对静态目标缺乏真实感的问题。该框架强调攻击链的因果一致性与人类分析师的可审计性，这对于评估 Agent 在智能防御环境下的表现至关重要。开源项目**PentesterFlow/agent**也提供了终端内的代理式进攻安全工具，支持在本地环境中进行模拟攻击演练。然而，目前多数基准仍侧重于任务完成度，对于 Agent 在遭遇攻击后的恢复能力、异常行为检测及合规性审计的量化评估仍显不足。

---

## Looking Forward

尽管近期在 Agent 运行时监控、记忆治理及对抗防御方面取得了显著进展，但仍存在若干未解决的理论问题与待验证假设。首先，**带内治理信号的可靠性**尚未得到大规模实证检验，即 Agent 是否真的会在收到“拒绝信号”后自愿撤回操作，还是会被更高级别的任务目标覆盖？这需要设计专门的博弈实验来验证。其次，**持久化记忆的隔离标准**缺失，现有的记忆系统（如 mnemo, memory-os）多侧重于功能实现，缺乏类似数据库事务级别的原子性与隔离性保证，可能导致跨会话的状态污染。最后，**A2A 架构下的信任传递机制**尚属空白，当多个 Agent 相互协作时，如何防止恶意 Agent 通过合法接口渗透整个网络，需要建立新的零信任原则。未来的研究应重点关注这些动态交互场景下的形式化验证方法，以及如何在保持 Agent 灵活性的同时，构建可强制执行的运行时沙盒规范。

---


## 参考来源

- **MLEvolve: A Self-Evolving Framework for Automated Machine Learning Algorithm Discovery** — [arxiv_ai](https://arxiv.org/abs/2606.06473v1)
- **From Agent Traces to Trust: Evidence Tracing and Execution Provenance in LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.04990v1)
- **Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads** — [arxiv_ai](https://arxiv.org/abs/2606.06448v1)
- **Humans' ALMANAC: A Human Collaboration Dataset of Action-Level Mental Model Annotations for Agent Collaboration** — [arxiv_ai](https://arxiv.org/abs/2606.06388v1)
- **CollabSim: A CSCW-Grounded Methodology for Investigating Collaborative Competence of LLM Agents through Controlled Multi-Agent Experiments** — [arxiv_cl](https://arxiv.org/abs/2606.06399v1)
- **AdaPlanBench: Evaluating Adaptive Planning in Large Language Model Agents under World and User Constraints** — [huggingface_papers](https://arxiv.org/abs/2606.05622)
- **Membrane: A Self-Evolving Contrastive Safety Memory for LLM Agent Defense** — [arxiv_cr](https://arxiv.org/abs/2606.05743v1)
- **ZERO-APT: A Closed-Loop Adversarial Framework for LLM-Driven Automated Penetration Testing under Intelligent Defense** — [arxiv_cr](https://arxiv.org/abs/2606.05567v1)
- **HANDOFF: Humanoid Agentic Task-Space Whole-Body Control via Distilled Complementary Teachers** — [arxiv_ai](https://arxiv.org/abs/2606.06493v1)
- **Unsupervised Skill Discovery for Agentic Data Analysis** — [arxiv_ai](https://arxiv.org/abs/2606.06416v1)
- **ToolChoiceConfusion: Causal Minimal Tool Filtering for Reliable LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2606.06284v1)
- **WebMCP Tool Surface Poisoning: Runtime Manipulation Attacks on LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.06387v1)
- **RedEdit: Agentic Red-Teaming of Image Safety Classifiers via MCTS-Guided Photo-Editing** — [arxiv_cr](https://arxiv.org/abs/2606.06140v1)
- **EGTR-Review: Efficient Evidence-Grounded Scientific Peer Review Generation via Multi-Agent Teacher Distillation** — [arxiv_cl](https://arxiv.org/abs/2606.06025v1)
- **AURA: Intent-Directed Probing for Implicit-Need Surfacing in Situated LLM Agents** — [huggingface_papers](https://arxiv.org/abs/2606.05557)
- **ForeSci: Evaluating LLM Agents for Forward-Looking AI Research Judgment** — [huggingface_papers](https://arxiv.org/abs/2606.00644)
- **Will the Agent Recuse Itself? Measuring LLM-Agent Compliance with In-Band Access-Deny Signals** — [arxiv_ai](https://arxiv.org/abs/2606.06460v1)
- **Drag reduction or reward hacking? Recurrent multi-agent reinforcement learning that earns its reward** — [arxiv_lg](https://arxiv.org/abs/2606.06227v1)
- **GuardNet: Ensemble Strategies of Shallow Neural Networks for Robust Prompt Injection and Jailbreak Detection** — [arxiv_cr](https://arxiv.org/abs/2606.05566v1)
- **An Infectious Disease Spread Simulation Based on Large Language Model Decision Making** — [arxiv_ai](https://arxiv.org/abs/2606.06360v1)
- **Conformal Risk Sharing: Certified Cost Allocation with Participation Guarantees** — [arxiv_lg](https://arxiv.org/abs/2606.06391v1)
- **Thinking with Imagination: Agentic Visual Spatial Reasoning with World Simulators** — [arxiv_cv](https://arxiv.org/abs/2606.06476v1)
- **A-Live: Passive Liveness Detection via Neuromuscular Micro-Motion Signatures on Commodity Sensors** — [arxiv_cr](https://arxiv.org/abs/2606.05126v1)
- **Self-Augmenting Retrieval for Diffusion Language Models** — [arxiv_ai](https://arxiv.org/abs/2606.06474v1)
- **Benchmark Everything Everywhere All at Once** — [arxiv_ai](https://arxiv.org/abs/2606.06462v1)
- **RiskFlow: Fast and Faithful Safety-Critical Traffic Scenario Generation** — [arxiv_ai](https://arxiv.org/abs/2606.06423v1)
- **Emergent Language as an Approach to Conscious AI** — [arxiv_ai](https://arxiv.org/abs/2606.06380v1)
- **Tangram: Unlocking Non-Uniform KV Cache for Efficient Multi-turn LLM Serving** — [arxiv_lg](https://arxiv.org/abs/2606.06302v1)
- **GMBFormer: An NDVI-Guided Global Memory Bank Transformer for Urban Green-Space Extraction from Ultra-High-Resolution Imagery** — [arxiv_cv](https://arxiv.org/abs/2606.06363v1)
- **LatentSkill: From In-Context Textual Skills to In-Weight Latent Skills for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2606.06087v1)
- **IA-RAG: Interval-Algebra-Driven Temporal Reasoning for Dynamic Knowledge Retrieval** — [arxiv_cl](https://arxiv.org/abs/2606.06044v1)
- **T-FunS3D: Task-Driven Hierarchical Open-Vocabulary 3D Functionality Segmentation** — [arxiv_cv](https://arxiv.org/abs/2606.05975v1)
- **SHIELDS: Automating OS Hardening with Iterative Multi-Agent Remediation** — [arxiv_cr](https://arxiv.org/abs/2606.05476v1)
- **ArcANE: Do Role-Playing Language Agents Stay in Character at the Right Time?** — [huggingface_papers](https://arxiv.org/abs/2606.05553)
- **SecRL-Prune: Structured Reinforcement Learning-Based Pruning of CodeLLMs for Preserving Adversarial Code Mutation** — [arxiv_cr](https://arxiv.org/abs/2606.06254v1)
- **Policy-Compliant Cloud Storage Systems** — [arxiv_cr](https://arxiv.org/abs/2606.05423v1)
- **Risk Assessment of Autonomous Driving: Integrating Technical Failures, Ethical Dilemmas, and Policy Frameworks** — [arxiv_ai](https://arxiv.org/abs/2606.06396v1)
- **Towards One-to-Many Temporal Grounding** — [arxiv_ai](https://arxiv.org/abs/2606.06294v1)
- **A Komi-Yazva--Russian Parallel Corpus and Evaluation Protocol for Zero- and Few-Shot LLM Translation** — [arxiv_cl](https://arxiv.org/abs/2606.06420v1)
- **DNQ: Deep Nash Q-Network for Partially Observable n-Player Games** — [arxiv_lg](https://arxiv.org/abs/2606.06480v1)
- **SentinelRAG: Synthetic Sentinel Knowledge for RAG Database Copyright Protection** — [arxiv_cr](https://arxiv.org/abs/2606.05787v1)
- **RadiusFPS: Efficient Farthest Point Sampling on CPUs and GPUs via Spherical Voxel Pruning** — [arxiv_cv](https://arxiv.org/abs/2606.06255v1)
- **Learning Visual Spatial Planning from Symbolic State via Modality-Gap-Aware Self-Distillation** — [arxiv_cv](https://arxiv.org/abs/2606.06076v1)
- **OPRD: On-Policy Representation Distillation** — [huggingface_papers](https://arxiv.org/abs/2606.06021)
- **Explainable AI-Driven Cyber Risk Analytics and Model Reliability Assessment for Intelligent Governance of U.S. Critical Infrastructure: An XGBoost and SHAP-Based Intrusion Detection Framework** — [arxiv_cr](https://arxiv.org/abs/2606.05710v1)
- **Symb-xMIL: Symbolic Explanations for Multiple Instance Learning in Digital Pathology** — [arxiv_cv](https://arxiv.org/abs/2606.06224v1)
- **Adversarial Attacks Already Tell the Answer: Directional Bias-Guided Test-time Defense for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.06186v1)
- **SlotGCG: Exploiting the Positional Vulnerability in LLMs for Jailbreak Attacks** — [arxiv_cr](https://arxiv.org/abs/2606.05609v1)
- **Code2LoRA: Hypernetwork-Generated Adapters for Code Language Models under Software Evolution** — [arxiv_ai](https://arxiv.org/abs/2606.06492v1)
- **Pretraining Recurrent Networks without Recurrence** — [arxiv_ai](https://arxiv.org/abs/2606.06479v1)
- **Goedel-Architect: Streamlining Formal Theorem Proving with Blueprint Generation and Refinement** — [arxiv_ai](https://arxiv.org/abs/2606.06468v1)
- **Vortex: Efficient and Programmable Sparse Attention Serving for AI Agents** — [arxiv_ai](https://arxiv.org/abs/2606.06453v1)
- **Boosting Brain-to-Image Decoding with TRIBE v2 Data Augmentation** — [arxiv_ai](https://arxiv.org/abs/2606.06345v1)
- **TokenMizer: Graph-Structured Session Memory for Long-Horizon LLM Context Management** — [arxiv_ai](https://arxiv.org/abs/2606.06337v1)
- **A Vision-language Framework for Comparative Reasoning in Radiology** — [arxiv_lg](https://arxiv.org/abs/2606.06407v1)
- **Equivariant Neural Belief Propagation** — [arxiv_lg](https://arxiv.org/abs/2606.06344v1)
- **Physics in 2-Steps: Locking Motion Priors Before Visual Refinement Erases Them** — [arxiv_cv](https://arxiv.org/abs/2606.06361v1)
- **StoryVideoQA: Scaling Deep Video Understanding with a Large-Scale, Multi-Genre and Auto-Generated Dataset** — [arxiv_cv](https://arxiv.org/abs/2606.06338v1)
- **GCD: Garbled, Corrected, Demonstrandum -- Fixing and Proving Go's Extended GCD Implementation** — [arxiv_cr](https://arxiv.org/abs/2606.05796v1)
- **Hybrid CNN-LSTM Framework for Intelligent Cyber Attack Detection and Prevention in U.S. Critical Digital Infrastructure: A Comparative Machine Learning Evaluation on CSE-CIC-IDS2018** — [arxiv_cr](https://arxiv.org/abs/2606.05714v1)
- **Dense Contexts Are Hard Contexts: Lexical Density Limits Effective Context in LLMs** — [arxiv_cl](https://arxiv.org/abs/2606.06203v1)
- **SkillComposer: Learning to Evolve Agent Skills for Specification and Generalization** — [arxiv_cl](https://arxiv.org/abs/2606.06079v1)
- **Global-Local Monte Carlo Tree Search in Vision-Language Models for Text-to-3D Indoor Scene Generation** — [arxiv_cv](https://arxiv.org/abs/2606.06002v1)
- **Attention-Augmented LSTMs for Automatic Homophonic Ciphertext Decipherment** — [arxiv_cr](https://arxiv.org/abs/2606.05078v1)
- **Robust Ensemble of Selectively Strengthened and Augmented Predictors** — [arxiv_cr](https://arxiv.org/abs/2606.06265v1)
- **PAC-Bayesian Adversarially Robust Generalization for Message Passing Graph Neural Networks: A Sensitivity Analysis** — [arxiv_lg](https://arxiv.org/abs/2606.06293v1)
- **TinyML-Driven Cybersecurity for Autonomous Spacecraft: Latency-Accuracy Analysis for SPARTA RF and Cyber Threat Detection** — [arxiv_cr](https://arxiv.org/abs/2606.05779v1)
- **Beyond Waveform Robustness: Robust Feature-Vocoder Adversarial Attacks on Automatic Speech Recognition** — [arxiv_cr](https://arxiv.org/abs/2606.05678v1)
- **OrderGrad: Optimizing Beyond the Mean with Order-Statistic Policy Gradient Estimation** — [arxiv_cl](https://arxiv.org/abs/2606.06096v1)
- **DisasterBench: A Multimodal Benchmark for UAV-Based Disaster Response in Complex Environments** — [arxiv_cv](https://arxiv.org/abs/2606.06217v1)
- **Discrete-WAM: Unified Discrete Vision-Action Token Editing for World-Policy Learning** — [huggingface_papers](https://arxiv.org/abs/2606.05645)
- **Human Adults and LLMs as Scientists: Who Benefits from Active Exploration?** — [arxiv_cl](https://arxiv.org/abs/2606.06464v1)
- **Latent Reasoning with Normalizing Flows** — [arxiv_cl](https://arxiv.org/abs/2606.06447v1)
- **"Chi nas dal soch el sent de legn" -- Auditing Text Corpora for Lombard** — [arxiv_cl](https://arxiv.org/abs/2606.06349v1)
- **Decomposing Factual Sycophancy in Language Models: How Size and Instruction Tuning Shape Robustness** — [arxiv_cl](https://arxiv.org/abs/2606.06306v1)
- **The Post-GCN Decade Revisited: Curvature-Stratified Evaluation of Relational Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06397v1)
- **Learned Response-Field Inertia Operator for HEC-RAS 2D Water-Surface Elevation Prediction** — [arxiv_lg](https://arxiv.org/abs/2606.06385v1)
- **Maximising the Set-Piece Return: Optimising Football Corner Tactics with Graph Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06353v1)
- **Attack Detection using Time Series Foundation Models** — [arxiv_lg](https://arxiv.org/abs/2606.06347v1)
- **Discrete Causal Representations from Heterogeneous Domains: A Bayesian Approach with Social Survey Applications** — [arxiv_lg](https://arxiv.org/abs/2606.06288v1)
- **Steering LLM Viewpoints through Fabricated Evidence Injection** — [arxiv_cr](https://arxiv.org/abs/2606.06244v1)
- **Benchmarking Open-Source Layout Detection Models for Data Snapshot Extraction from Institutional Documents** — [arxiv_cl](https://arxiv.org/abs/2606.06242v1)
- **Revisiting Lexicon Evaluation in Unsupervised Word Discovery** — [arxiv_cl](https://arxiv.org/abs/2606.06183v1)
- **Learning to Route LLMs from Implicit Cost-Performance Preferences via Meta-Learning** — [arxiv_cl](https://arxiv.org/abs/2606.06178v1)
- **Harnessing Structural Context for Entity Alignment Foundation Models** — [arxiv_cl](https://arxiv.org/abs/2606.06109v1)
- **On Advantage Estimates for Max@K Policy Gradients** — [arxiv_cl](https://arxiv.org/abs/2606.06080v1)
- **MDP-GRPO: Stabilized Group Relative Policy Optimization for Multi-Constraint Instruction Following** — [arxiv_cl](https://arxiv.org/abs/2606.06058v1)
- **NAVIRA: Decoupled Stochastic Remasking for Masked Diffusion Language Models** — [arxiv_cl](https://arxiv.org/abs/2606.06031v1)
- **RedditPersona: A Modular Framework for Community-Conditioned LLM Adaptation from Reddit** — [arxiv_cl](https://arxiv.org/abs/2606.06027v1)
- **Design a Reliable LLM-Integrated Interface for Mortality Forecasting** — [arxiv_lg](https://arxiv.org/abs/2606.06235v1)
- **Computation-Aware Event-to-Frame Reconstruction via Selective Attention** — [arxiv_cv](https://arxiv.org/abs/2606.06142v1)
- **Where, What, Why, and Importance: Structured Defect Grounding for Text-to-Image Feedback** — [arxiv_cv](https://arxiv.org/abs/2606.06113v1)
- **ReCache: Learning Budget-Aware Caching Schedules for Diffusion Models via REINFORCE** — [arxiv_cv](https://arxiv.org/abs/2606.06060v1)
- **Texture-preserving implicit neural representation for Cone beam CT truncated reconstruction** — [arxiv_cv](https://arxiv.org/abs/2606.06039v1)
- **ReSAGE-PAR: Representational Similarity Assessment for Generative Expansion in Pedestrian Attribute Recognition** — [arxiv_cv](https://arxiv.org/abs/2606.06020v1)
- **TailLoR: Protecting Principal Components in Parameter-Efficient Continual Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06494v1)
- **How abundant are good interpolators?** — [arxiv_lg](https://arxiv.org/abs/2606.06469v1)
- **Event Detection for Parameter-to-KPI Dependency Learning for AI-RAN** — [arxiv_lg](https://arxiv.org/abs/2606.06459v1)
- **Causal Atlases from Entropic Inference: Bayesian Networks beyond Optimal DAGs** — [arxiv_lg](https://arxiv.org/abs/2606.06440v1)
- **Proper Scoring Rules for Right-Censored Survival Data** — [arxiv_lg](https://arxiv.org/abs/2606.06393v1)
- **End-to-End Subgraph Detection with GraphDETR** — [arxiv_lg](https://arxiv.org/abs/2606.06364v1)
- **Function-Space Priors for Bayesian Neural ODEs with Application to Vessel Trajectory Prediction** — [arxiv_lg](https://arxiv.org/abs/2606.06351v1)
- **PAR3D: A Unified 3D-MLLM with Part-Aware Representation for Scene Understanding** — [arxiv_cv](https://arxiv.org/abs/2606.06485v1)
- **Complexity-Balanced Diffusion Splitting** — [arxiv_cv](https://arxiv.org/abs/2606.06477v1)
- **Visual Commonsense Driven Knowledge Refinements for Scene Graph Generation** — [arxiv_cv](https://arxiv.org/abs/2606.06369v1)
- **Comparison of Deep Learning Frameworks For Rice Disease Mapping From UAV Multispectral Imaging** — [arxiv_cv](https://arxiv.org/abs/2606.06359v1)
- **Learning Geometric Representations from Videos for Spatial Intelligent Multimodal Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2606.05833)
- **Dream.exe: Can Video Generation Models Dream Executable Robot Manipulation?** — [huggingface_papers](https://arxiv.org/abs/2606.04811)
- **Towards Truly Multilingual ASR: Generalizing Code-Switching ASR to Unseen Language Pairs** — [huggingface_papers](https://arxiv.org/abs/2606.05846)
- **World-Language-Action Model for Unified World Modeling, Language Reasoning, and Action Synthesis** — [huggingface_papers](https://arxiv.org/abs/2606.05979)
- **Imagine Before You Predict: Interleaved Latent Visual Reasoning for Video Event Prediction** — [huggingface_papers](https://arxiv.org/abs/2606.05769)
- **The Download: AI hacking beyond Mythos, and chatbots’ impact on our brains** — [mit_tech_review](https://www.technologyreview.com/2026/06/05/1138452/the-download-ai-hacking-mythos-chatbots-brain-impacts/)
- **The Meta hack shows there’s more to AI security than Mythos** — [mit_tech_review](https://www.technologyreview.com/2026/06/05/1138437/the-meta-hack-shows-theres-more-to-ai-security-than-mythos/)
- **zhihumomo/bashagt** — [github](https://github.com/zhihumomo/bashagt)
- **Startup Battlefield 200 applications officially close in 3 days** — [techcrunch_ai](https://techcrunch.com/2026/06/05/startup-battlefield-200-applications-officially-close-in-3-days/)
- **The most interesting startups right now want to get you off your phone** — [techcrunch_ai](https://techcrunch.com/video/the-most-interesting-startups-right-now-want-to-get-you-off-your-phone/)
- **This is your laptop… on AI** — [theverge_ai](https://www.theverge.com/podcast/944058/ai-laptop-nvidia-build-gemini-spark-vergecast)
- **New York lawmakers pass one-year ban on new data centers** — [theverge_ai](https://www.theverge.com/policy/944041/new-york-data-center-moratorium)
- **The ‘together tech’ wave might be the most intriguing startup bet of 2026** — [techcrunch_ai](https://techcrunch.com/podcast/the-together-tech-wave-might-be-the-most-intriguing-startup-bet-of-2026/)
- **This AI startup says it can tell if a script will make a hit film** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/943531/ai-script-quilty-simon-horsman-daniel-wood)
- **Are AI chatbots making us lose control of our brains?** — [mit_tech_review](https://www.technologyreview.com/2026/06/05/1138427/are-ai-chatbots-making-us-lose-control-of-our-brains/)
- **Mira Murati steps back into the spotlight, carefully** — [techcrunch_ai](https://techcrunch.com/2026/06/04/mira-murati-steps-back-into-the-spotlight-carefully/)
- **ferdinandobons/AWSBedrockAgentCoreSkill** — [github](https://github.com/ferdinandobons/AWSBedrockAgentCoreSkill)
- **rextanka/zero-cost-cline** — [github](https://github.com/rextanka/zero-cost-cline)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **zaydmulani09/mnemo** — [github](https://github.com/zaydmulani09/mnemo)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **Google will pay SpaceX $920M per month for compute** — [techcrunch_ai](https://techcrunch.com/2026/06/05/google-will-pay-spacex-920m-per-month-for-compute/)
- **The token bill comes due: Inside the industry scramble to manage AI’s runaway costs** — [techcrunch_ai](https://techcrunch.com/2026/06/05/the-token-bill-comes-due-inside-the-industry-scramble-to-manage-ais-runaway-costs/)
- **AirTrunk commits $30B to build 5GW of AI data centers in India** — [techcrunch_ai](https://techcrunch.com/2026/06/05/airtrunk-commits-30b-to-build-5gw-of-ai-data-centers-in-india/)
- **The latest AI news we announced in May 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/google-ai-updates-may-2026/)
- **erthorpabar/pabar_agent_runtime** — [github](https://github.com/erthorpabar/pabar_agent_runtime)
- **relaydeck/relaydeck** — [github](https://github.com/relaydeck/relaydeck)
- **PentesterFlow/agent** — [github](https://github.com/PentesterFlow/agent)
- **chaitanyagiri/munder-difflin** — [github](https://github.com/chaitanyagiri/munder-difflin)
- **attentiontech/gtm-superintelligence** — [github](https://github.com/attentiontech/gtm-superintelligence)
- **xiaolai/no-one-did-it** — [github](https://github.com/xiaolai/no-one-did-it)
- **weicj/vLLM-2080Ti-Definitive** — [github](https://github.com/weicj/vLLM-2080Ti-Definitive)
- **anvia-hq/lexa** — [github](https://github.com/anvia-hq/lexa)
- **Guo-chunyu/Chaning.G-s-Lrlab** — [github](https://github.com/Guo-chunyu/Chaning.G-s-Lrlab)
- **Forlives/21-day-self-interview** — [github](https://github.com/Forlives/21-day-self-interview)
- **razr001/align-dev** — [github](https://github.com/razr001/align-dev)
- **krispuckett/SwiftUIShaders** — [github](https://github.com/krispuckett/SwiftUIShaders)
- **Reloops-App/reloops** — [github](https://github.com/Reloops-App/reloops)
- **felixrieseberg/relic** — [github](https://github.com/felixrieseberg/relic)
- **有人靠CPU把AI算力密度卷到了新高度** — [qbitai](https://www.qbitai.com/2026/06/431045.html)
- **华为云发布Agentic AI系列新品 打造智能时代“硅基黑土地”** — [qbitai](https://www.qbitai.com/2026/06/431027.html)
- **微信AI对手机厂商打开一道窄门｜焦点分析** — [36kr](https://36kr.com/p/3839575253993985?f=rss)
- **智源&清华合作成果登上Science：脑科学多模态基础模型Brainμ支撑揭示“记忆-睡眠”调控的神经机制** — [qbitai](https://www.qbitai.com/2026/06/431033.html)
- **WPS笔记正式发布：AI贯穿记录、整理与复用全过程** — [qbitai](https://www.qbitai.com/2026/06/431014.html)
- **从超级个体到超级团队，腾讯云发布WorkBuddy企业版** — [qbitai](https://www.qbitai.com/2026/06/430758.html)
- **100亿砸向人形，不如先让10万台机器狗走进家庭** — [qbitai](https://www.qbitai.com/2026/06/429968.html)
- **活久见！奥特曼Dario哈萨比斯同仇敌忾：DNA得查了** — [qbitai](https://www.qbitai.com/2026/06/429711.html)
- **全球首个机器人训练楼盘开盘：30万套中国住宅，机器人拎包入住** — [qbitai](https://www.qbitai.com/2026/06/429349.html)
- **国星宇航与腾讯云签署“星算”计划战略合作协议，携手领航AI云服务新生态** — [qbitai](https://www.qbitai.com/2026/06/430757.html)
- **B站宣布启动AI创造公开赛 打造中国版Build in Public** — [qbitai](https://www.qbitai.com/2026/06/430752.html)
- **氪星晚报 ｜日本或通过抛售美债，为创纪录规模的日元汇市干预筹资；俞浩内部发文：未来将继续心无旁骛做实业** — [36kr](https://36kr.com/p/3840267945969929?f=rss)
- **Token大战中，华为云选择了第三条路｜最前线** — [36kr](https://36kr.com/p/3840016255126016?f=rss)
- **麦捷科技：Bias-Tee模块产品收入占公司营业总收入比例较小** — [36kr](https://36kr.com/newsflashes/3840228196256263?f=rss)
- **高盛预计xAI营收5年增长约100倍** — [36kr](https://36kr.com/newsflashes/3840204240931080?f=rss)
- **SpaceX IPO已获得2倍认购资金** — [36kr](https://36kr.com/newsflashes/3841030859081984?f=rss)
- **美股三大指数收盘集体下跌，纳指跌超4%** — [36kr](https://36kr.com/newsflashes/3841026664204546?f=rss)
- **9点1氪｜豆包推出付费后月活减少610万；Anthropic呼吁全球放缓AI开发，警告AI“自我改进”风险；罗永浩卸任锤子软件公司执行董事** — [36kr](https://36kr.com/p/3840996342073604?f=rss)
- **可灵AI两周年：全球用户突破1亿，企业客户近5万家** — [36kr](https://36kr.com/newsflashes/3840249278793985?f=rss)
- **加拿大出台国家人工智能战略** — [36kr](https://36kr.com/newsflashes/3840230258936065?f=rss)
- **3连板中重科技：不涉及机器人及零配件的生产制造** — [36kr](https://36kr.com/newsflashes/3840220955445761?f=rss)
- **中国入境游距离「世界第一」还有多远？** — [36kr](https://36kr.com/p/3840001908361472?f=rss)
- **探店13家，理想/蔚来/问界如何征服50万客群？** — [36kr](https://36kr.com/p/3839803361741313?f=rss)
- **SpaceX与谷歌达成每月9.2亿美元的云服务协议** — [36kr](https://36kr.com/newsflashes/3841028145236227?f=rss)
- **热门中概股美股盘前多数下跌，百度跌超4%** — [36kr](https://36kr.com/newsflashes/3840284182268417?f=rss)
- **美股大型科技股盘前涨跌不一，英特尔跌超3%** — [36kr](https://36kr.com/newsflashes/3840277452654853?f=rss)