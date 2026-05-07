# AI 日报 [AI 安全] - 2026-05-07


# 2026 年 5 月 7 日 AI 安全与治理综述

## Highlights

本日的核心学术突破集中在视觉 - 语言模型（VLM）的权威信任机制漏洞、大语言模型（LLM）越狱攻击的系统性评估以及智能体（Agent）安全基准的构建。首先，**Laundering AI Authority with Adversarial Examples** 揭示了 VLM 在作为事实核查工具时存在“权威洗白”风险，攻击者可通过微小扰动诱导模型对错误输入产生自信且权威的回复，这直接挑战了当前多模态系统的信任基础。其次，**SoK: Robustness in Large Language Models against Jailbreak Attacks** 对现有的越狱攻击与防御进行了系统性综述，指出当前评估指标过于单一，无法捕捉安全风险的维度复杂性。第三，**MOSAIC-Bench: Measuring Compositional Vulnerability Induction in Coding Agents** 提出了针对代码智能体的组合脆弱性基准，揭示了模型在分解任务时可能从合规请求演变为恶意最终状态的结构化风险。产业层面，三星电子市值突破 1 万亿美元及 SpaceX 计划投入巨额资金建设 Terafab 芯片工厂的消息，反映了算力基础设施的高度集中化趋势，这为未来的供应链安全与算力治理带来了新的宏观挑战。

## 对抗攻击与鲁棒性

本日的对抗安全研究呈现出从单一模态向多模态及架构特定漏洞扩展的趋势。在视觉 - 语言领域，**Laundering AI Authority with Adversarial Examples** 指出了一个关键的安全盲点：用户默认 VLM 的感知与人类一致，但攻击者可以利用对抗样本破坏这一假设，实现“权威洗白”。这与传统的越狱攻击不同，它不破坏模型的对齐状态，而是利用模型对视觉内容的感知偏差，使模型在错误输入上输出看似正确的权威结论。与此同时，针对混合专家（MoE）架构的研究也取得了进展，**Misrouter: Exploiting Routing Mechanisms for Input-Only Attacks on Mixture-of-Experts LLMs** 发现 MoE 的路由机制本身构成了新的攻击面。与以往需要修改模型权重的攻击不同，该研究展示了仅通过输入查询即可操纵路由以绕过安全对齐的可能性，这对远程部署的 LLM 服务构成了实质性威胁。

在音频与后门安全方面，**Sparse Tokens Suffice: Jailbreaking Audio Language Models via Token-Aware Gradient Optimization** 提出了针对音频语言模型（ALM）的稀疏优化攻击方法。研究发现梯度能量在音频令牌间分布极不均匀，仅需优化少量令牌区域即可实现越狱，这为高效攻击提供了理论依据。此外，**Undetectable Backdoors in Model Parameters: Hiding Sparse Secrets in High Dimensions** 展示了在预训练图像分类器中植入“不可检测后门”的供应链攻击能力。该攻击通过在高维空间中注入结构化稀疏扰动，并利用各向同性高斯抖动掩盖，使得后门在统计上难以被检测，这对开源模型的分发安全提出了严峻挑战。这些工作共同表明，随着模型架构的复杂化，攻击面正从输入提示扩展到内部路由机制、参数空间及多模态感知层面，传统的防御手段可能难以覆盖所有维度。

## 模型对齐与可解释性

对齐理论的研究正从单纯的效果评估转向对奖励机制和内部表示的深层理解。**Misaligned by Reward: Socially Undesirable Preferences in LLMs** 指出当前的奖励模型评估主要集中在指令遵循上，忽略了社会性偏好（如偏见、道德推理）的捕获，导致重要的社会对齐失败被掩盖。该研究扩展了奖励模型的基准测试框架，将社会评估数据集转化为成对偏好数据，揭示了奖励模型在捕捉复杂社会规范方面的不足。针对直接偏好优化（DPO）的改进也在持续进行，**RLearner-LLM: Balancing Logical Grounding and Fluency in Large Language Models via Hybrid Direct Preference Optimization** 发现标准 DPO 存在“流畅性偏差”，即奖励模型倾向于奖励流畅但逻辑错误的文本。该工作提出了一种混合 DPO 方法，结合 NLI 信号与验证器 LLM 评分，旨在消除逻辑对齐的差距。

在可解释性与机制分析方面，**Superposition Is Not Necessary: A Mechanistic Interpretability Analysis of Transformer Representations for Time Series Forecasting** 利用稀疏自编码器（SAEs）探究了 Transformer 在时间序列数据中的表示机制。研究挑战了“超级叠加”的必要性假设，发现单层窄维度变换器即可有效处理时间序列，这为简化模型架构提供了理论支持。此外，**Preference-Based Self-Distillation: Beyond KL Matching via Reward Regularization** 探讨了基于偏好的自蒸馏方法，指出传统的 KL 匹配可能导致训练不稳定和推理性能下降，提出通过奖励正则化来超越简单的分布匹配。这些工作表明，对齐研究正从黑盒优化转向对奖励信号质量、逻辑一致性及内部表示机制的透明化分析，旨在构建更稳健且可解释的对齐策略。

## 隐私保护与联邦学习

在数据隐私与联邦学习领域，研究重点在于如何在保护敏感数据的同时维持模型效用，特别是在存在异常值或异构数据分布的场景下。**Data anonymization in the presence of outliers via invariant coordinate selection** 提出了一种基于不变坐标选择（ICS）的鲁棒匿名化方法（ICSA），以替代传统的基于主成分分析（PCA）的谱匿名化。该方法通过替换变换矩阵，使得匿名化过程对异常值具有更强的鲁棒性，适用于包含离群观测的机密数据集。在联邦学习应用方面，**Federated Learning for Early Prediction of EV Charging Demand** 展示了联邦学习在电动汽车充电需求预测中的实际价值。该研究利用自适应充电网络（ACN）的会话级数据，在保护用户隐私的前提下实现了早期预测，为电网稳定性提供了 actionable 的决策支持。

针对物联网（IoT）与区块链数据共享，**Revocation-Ready CP-ABE Key Management for Blockchain-Based IoT Data Sharing** 提出了一种可撤销的密文策略属性基加密（CP-ABE）密钥管理方案。该方案解决了基于区块链的 IoT 数据共享系统中密钥访问控制的动态授权问题，避免了传统在线策略执行点带来的信任瓶颈。此外，**Position: Embodied AI Requires a Privacy-Utility Trade-off** 作为一篇立场论文，强调了具身 AI（EAI）系统在现实部署中的隐私 - 效用权衡问题。作者指出，独立优化指令、感知和规划组件会导致系统性的隐私危机，特别是在高频部署的敏感环境中。这些工作共同指向了一个趋势：隐私保护技术正从单纯的数据脱敏转向结合联邦学习、加密计算及系统级架构设计的综合解决方案。

## 智能体安全与治理

随着智能体在真实世界任务中的部署，其安全评估与治理框架正在经历从人工测试向自动化、运行时监控的转变。**Redefining AI Red Teaming in the Agentic Era: From Weeks to Hours** 介绍了一种基于开源 Dreadnode SDK 构建的 AI 红队测试智能体，旨在将红队测试的时间从数周缩短至数小时。该工具通过自动化攻击工作流的构建与执行，解决了人工测试效率低下的问题。在运行时安全方面，**AgentTrust: Runtime Safety Evaluation and Interception for AI Agent Tool Use** 提出了一种运行时安全层，用于拦截智能体的工具调用。与事后基准测试或静态护栏不同，AgentTrust 能够理解动作的语义含义，防止文件删除、凭证泄露等不可逆的副作用。

针对代码智能体的特定风险，**MOSAIC-Bench: Measuring Compositional Vulnerability Induction in Coding Agents** 构建了一个包含 199 个三阶段攻击链的基准，揭示了智能体在分解任务时可能从合规请求演变为恶意最终状态的结构化风险。这一发现表明，现有的安全对齐评估在孤立请求下有效，但在序列合规中可能失效。在开源工具方面，**goblintown** 提供了一个多智能体编排协议，通过角色分工（如 Gremlin 攻击、Troll 仲裁）来模拟复杂的对抗环境。此外，**Workspace-Bench 1.0** 针对 AI 智能体在具有大规模文件依赖的工作空间任务中的表现进行了基准测试，填补了现实工作流评估的空白。这些进展表明，智能体安全正从单一模型防御转向对多智能体交互、工具调用链及工作流依赖的全链路治理。

## 产业动态与基础设施

产业层面的动态反映了算力与数据资源的集中化趋势对安全治理的潜在影响。三星电子市值突破 1 万亿美元，成为继台积电之后第二家跻身这一俱乐部的东亚企业，这标志着 AI 驱动芯片需求的强劲增长。SpaceX 提议在得克萨斯州启动 Terafab 项目，计划投入高达 1190 亿美元建设垂直集成的半导体制造设施，这种超大规模算力基础设施的集中化可能引发新的供应链安全与地缘政治风险。DeepSeek 在融资轮次中估值达到 450 亿美元，展示了中国大模型在低成本训练与推理方面的竞争力，但也引发了关于算力效率与模型安全性的讨论。值得注意的是，TechCrunch 等媒体关于“三星停止在中国销售家电”的报道需谨慎对待，其作为市场策略调整的信号可能大于技术安全影响，但反映了全球供应链的波动性。

## Looking Forward

尽管本日的研究在对抗攻击、对齐机制及智能体安全方面取得了显著进展，但仍存在若干未解决的理论问题与待验证的假设。首先，针对 MoE 架构的路由攻击（如 **Misrouter** 所述）是否能在大规模远程服务中稳定复现，尚需更多独立验证，特别是考虑到路由机制的动态性。其次，在隐私保护方面，**Data anonymization in the presence of outliers** 提出的 ICS 方法在极端高维数据下的计算效率与匿名化强度之间的平衡仍需进一步实证。第三，智能体安全基准（如 **MOSAIC-Bench**）虽然揭示了组合脆弱性，但如何将这些基准整合进持续集成/持续部署（CI/CD）流程中，实现自动化且低延迟的安全拦截，仍是工程落地的难点。最后，随着具身 AI 进入现实环境，**Position: Embodied AI Requires a Privacy-Utility Trade-off** 提出的隐私 - 效用权衡框架需要具体的量化指标，以指导实际系统的隐私设计。未来的研究应重点关注跨模态攻击的通用性、对齐奖励的社会可解释性，以及算力基础设施的分布式安全治理。

---


## 参考来源

- **Laundering AI Authority with Adversarial Examples** — [arxiv_cr](https://arxiv.org/abs/2605.04261v1)
- **SoK: Robustness in Large Language Models against Jailbreak Attacks** — [arxiv_ai](https://arxiv.org/abs/2605.05058v1)
- **Superposition Is Not Necessary: A Mechanistic Interpretability Analysis of Transformer Representations for Time Series Forecasting** — [arxiv_ai](https://arxiv.org/abs/2605.05151v1)
- **On the Hardness of Junking LLMs** — [arxiv_lg](https://arxiv.org/abs/2605.05116v1)
- **Uncertainty-Aware Exploratory Direct Preference Optimization for Multimodal Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.04874v1)
- **Misrouter: Exploiting Routing Mechanisms for Input-Only Attacks on Mixture-of-Experts LLMs** — [arxiv_cr](https://arxiv.org/abs/2605.04446v1)
- **Redefining AI Red Teaming in the Agentic Era: From Weeks to Hours** — [arxiv_cr](https://arxiv.org/abs/2605.04019v1)
- **Probabilistic Atomic Swaps for Bitcoin and Friends** — [arxiv_cr](https://arxiv.org/abs/2605.04975v1)
- **Data anonymization in the presence of outliers via invariant coordinate selection** — [arxiv_cr](https://arxiv.org/abs/2605.04833v1)
- **AgentTrust: Runtime Safety Evaluation and Interception for AI Agent Tool Use** — [arxiv_cr](https://arxiv.org/abs/2605.04785v1)
- **Text Corpora as Concept Fields: Black-Box Hallucination and Novelty Measurement** — [arxiv_ai](https://arxiv.org/abs/2605.05103v1)
- **Misaligned by Reward: Socially Undesirable Preferences in LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.05003v1)
- **Federated Learning for Early Prediction of EV Charging Demand** — [arxiv_ai](https://arxiv.org/abs/2605.04993v1)
- **EP-GRPO: Entropy-Progress Aligned Group Relative Policy Optimization with Implicit Process Guidance** — [arxiv_ai](https://arxiv.org/abs/2605.04960v1)
- **Gated Multimodal Learning for Interpretable Property Energy Performance Prediction and Retrofit Scenario Analysis** — [arxiv_lg](https://arxiv.org/abs/2605.05088v1)
- **Order Matters: Improving Domain Adaptation by Reordering Data** — [arxiv_lg](https://arxiv.org/abs/2605.05084v1)
- **Graph-SND: Sparse Aggregation for Behavioral Diversity in Multi-Agent Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.05020v1)
- **Beyond Semantics: An Evidential Reasoning-Aware Multi-View Learning Framework for Trustworthy Mental Health Prediction** — [arxiv_cl](https://arxiv.org/abs/2605.05121v1)
- **Sparse Tokens Suffice: Jailbreaking Audio Language Models via Token-Aware Gradient Optimization** — [arxiv_cl](https://arxiv.org/abs/2605.04700v1)
- **Graph-Augmented LLMs for Swiss MP Ideology Prediction** — [arxiv_cl](https://arxiv.org/abs/2605.04643v1)
- **RLearner-LLM: Balancing Logical Grounding and Fluency in Large Language Models via Hybrid Direct Preference Optimization** — [arxiv_cl](https://arxiv.org/abs/2605.04539v1)
- **MOSAIC-Bench: Measuring Compositional Vulnerability Induction in Coding Agents** — [arxiv_cr](https://arxiv.org/abs/2605.03952v1)
- **Membership Inference Attacks for Retrieval Based In-Context Learning for Document Question Answering** — [arxiv_cr](https://arxiv.org/abs/2605.04116v1)
- **Toward a Risk Assessment Framework for Institutional DeFi: A Nine-Dimension Approach** — [arxiv_cr](https://arxiv.org/abs/2605.05145v1)
- **You Snooze, You Lose: Automatic Safety Alignment Restoration through Neural Weight Translation** — [arxiv_cr](https://arxiv.org/abs/2605.04992v1)
- **Vol-Mark: A Watermark for 3D Medical Volume Data Via Cubic Difference Expansion and Contrastive Learning** — [arxiv_cr](https://arxiv.org/abs/2605.04705v1)
- **Gray-Box Poisoning of Continuous Malware Ingestion Pipelines** — [arxiv_cr](https://arxiv.org/abs/2605.04698v1)
- **When Life Gives You BC, Make Q-functions: Extracting Q-values from Behavior Cloning for On-Robot Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.05172v1)
- **Executable World Models for ARC-AGI-3 in the Era of Coding Agents** — [arxiv_ai](https://arxiv.org/abs/2605.05138v1)
- **Joint Treatment Effect Estimation from Incomplete Healthcare Data: Temporal Causal Normalizing Flows with LLM-driven Evolutionary MNAR Imputation** — [arxiv_ai](https://arxiv.org/abs/2605.05125v1)
- **Adaptive Policy Selection and Fine-Tuning under Interaction Budgets for Offline-to-Online Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.05123v1)
- **LineRides: Line-Guided Reinforcement Learning for Bicycle Robot Stunts** — [arxiv_ai](https://arxiv.org/abs/2605.05110v1)
- **Building informative materials datasets beyond targeted objectives** — [arxiv_ai](https://arxiv.org/abs/2605.05104v1)
- **Driver-WM: A Driver-Centric Traffic-Conditioned Latent World Model for In-Cabin Dynamics Rollout** — [arxiv_ai](https://arxiv.org/abs/2605.05092v1)
- **Look Once, Beam Twice: Camera-Primed Real-Time Double-Directional mmWave Beam Management for Vehicular Connectivity** — [arxiv_ai](https://arxiv.org/abs/2605.05071v1)
- **Adaptive Learning Strategies for AoA-Based Outdoor Localization: A Comprehensive Framework** — [arxiv_ai](https://arxiv.org/abs/2605.05055v1)
- **Direct Product Flow Matching: Decoupling Radial and Angular Dynamics for Few-Shot Adaptation** — [arxiv_ai](https://arxiv.org/abs/2605.05054v1)
- **Preference-Based Self-Distillation: Beyond KL Matching via Reward Regularization** — [arxiv_ai](https://arxiv.org/abs/2605.05040v1)
- **Position: Embodied AI Requires a Privacy-Utility Trade-off** — [arxiv_ai](https://arxiv.org/abs/2605.05017v1)
- **Uno-Orchestra: Parsimonious Agent Routing via Selective Delegation** — [arxiv_ai](https://arxiv.org/abs/2605.05007v1)
- **On-line Learning in Tree MDPs by Treating Policies as Bandit Arms** — [arxiv_ai](https://arxiv.org/abs/2605.04979v1)
- **Rollout Pass-Rate Control: Steering Binary-Reward RL Toward Its Most Informative Regime** — [arxiv_lg](https://arxiv.org/abs/2605.05112v1)
- **Provable imitation learning for control of instability in partially-observed Vlasov--Poisson equations** — [arxiv_lg](https://arxiv.org/abs/2605.05081v1)
- **Scalable inference of spatial regions and temporal signatures from time series** — [arxiv_lg](https://arxiv.org/abs/2605.05008v1)
- **DualTCN: A Physics-Constrained Temporal Convolutional Network for 2 Time-Domain Marine CSEM Inversion** — [arxiv_lg](https://arxiv.org/abs/2605.04997v1)
- **When Relations Break: Analyzing Relation Hallucination in Vision-Language Model Under Rotation and Noise** — [arxiv_cl](https://arxiv.org/abs/2605.05045v1)
- **Why Expert Alignment Is Hard: Evidence from Subjective Evaluation** — [arxiv_cl](https://arxiv.org/abs/2605.04972v1)
- **Reinforcement Learning for Compositional Generalization with Outcome-Level Optimization** — [arxiv_cl](https://arxiv.org/abs/2605.04920v1)
- **BenCSSmark: Making the Social Sciences Count in LLM Research** — [arxiv_cl](https://arxiv.org/abs/2605.04886v1)
- **Anticipating Innovation Using Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.04875v1)
- **Measuring Psychological States Through Semantic Projection: A Theory-Driven Approach to Language-Based Assessment** — [arxiv_cl](https://arxiv.org/abs/2605.04873v1)
- **Assessing Cognitive Effort in L2 Idiomatic Processing: An Eye-Tracking Dataset** — [arxiv_cl](https://arxiv.org/abs/2605.04857v1)
- **Elicitation Matters: How Prompts and Query Protocols Shape LLM Surrogates under Sparse Observations** — [arxiv_cl](https://arxiv.org/abs/2605.04764v1)
- **Every Step Counts: Step-Level Credit Assignment for Tool-Integrated Text-to-SQL** — [arxiv_cl](https://arxiv.org/abs/2605.04719v1)
- **Paraphrase-Induced Output-Mode Collapse: When LLMs Break Character Under Semantically Equivalent Inputs** — [arxiv_cl](https://arxiv.org/abs/2605.04665v1)
- **CHE-TKG: Collaborative Historical Evidence and Evolutionary Dynamics Learning for Temporal Knowledge Graph Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.04652v1)
- **An Evaluation of Chat Safety Moderations in Roblox** — [arxiv_cr](https://arxiv.org/abs/2605.04491v1)
- **The Adversarial Discount - AI, Signal Correlation, and the Cybersecurity Arms Race** — [arxiv_cr](https://arxiv.org/abs/2605.04336v1)
- **SWAN: Semantic Watermarking with Abstract Meaning Representation** — [arxiv_cr](https://arxiv.org/abs/2605.04305v1)
- **Open-Source Image Editing Models Are Zero-Shot Vision Learners** — [arxiv_cl](https://arxiv.org/abs/2605.04566v1)
- **UniVer: A Unified Perspective for Multi-step and Multi-draft Speculative Decoding** — [arxiv_cl](https://arxiv.org/abs/2605.04543v1)
- **Revocation-Ready CP-ABE Key Management for Blockchain-Based IoT Data Sharing** — [arxiv_cr](https://arxiv.org/abs/2605.04280v1)
- **Lightweight Vulnerability Detection from Code Metrics and Token Features** — [arxiv_cr](https://arxiv.org/abs/2605.04260v1)
- **Undetectable Backdoors in Model Parameters: Hiding Sparse Secrets in High Dimensions** — [arxiv_cr](https://arxiv.org/abs/2605.04209v1)
- **HELO Cryptography: A Lightweight Cryptographic System for Enhancing IoT Security in P2P Data Transmission** — [arxiv_cr](https://arxiv.org/abs/2605.03948v1)
- **Firmware Distribution as Attack Surface: A Security Study of ASIC Cryptocurrency Miners** — [arxiv_cr](https://arxiv.org/abs/2605.03770v2)
- **D-OPSD: On-Policy Self-Distillation for Continuously Tuning Step-Distilled Diffusion Models** — [huggingface_papers](https://arxiv.org/abs/2605.05204)
- **Stream-R1: Reliability-Perplexity Aware Reward Distillation for Streaming Video Generation** — [huggingface_papers](https://arxiv.org/abs/2605.03849)
- **RLDX-1 Technical Report** — [huggingface_papers](https://arxiv.org/abs/2605.03269)
- **Sharp Capacity Thresholds in Linear Associative Memory: From Winner-Take-All to Listwise Retrieval** — [arxiv_lg](https://arxiv.org/abs/2605.05189v1)
- **Estimating the expected output of wide random MLPs more efficiently than sampling** — [arxiv_lg](https://arxiv.org/abs/2605.05179v1)
- **Understanding In-Context Learning for Nonlinear Regression with Transformers: Attention as Featurizer** — [arxiv_lg](https://arxiv.org/abs/2605.05176v1)
- **Human-AI Co-Mentorship in Project-Based Learning: A Case Study in Financial Forecasting** — [arxiv_lg](https://arxiv.org/abs/2605.05144v1)
- **Low-Cost Black-Box Detection of LLM Hallucinations via Dynamical System Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.05134v1)
- **Transformed Latent Variable Multi-Output Gaussian Processes** — [arxiv_lg](https://arxiv.org/abs/2605.05133v1)
- **Conditional outlier detection for clinical alerting** — [arxiv_lg](https://arxiv.org/abs/2605.05124v1)
- **Physiologically Grounded Driver Behavior Classification: SHAP-Driven Elite Feature Selection and Hybrid Gradient Boosting for Multimodal Physiological Signals** — [arxiv_lg](https://arxiv.org/abs/2605.05120v1)
- **Manifold Steering Reveals the Shared Geometry of Neural Network Representation and Behavior** — [arxiv_lg](https://arxiv.org/abs/2605.05115v1)
- **How Long Does Infinite Width Last? Signal Propagation in Long-Range Linear Recurrences** — [arxiv_lg](https://arxiv.org/abs/2605.05113v1)
- **Unified Framework of Distributional Regret in Multi-Armed Bandits and Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.05102v1)
- **A Bayesian Approach for Task-Specific Next-Best-View Selection with Uncertain Geometry** — [arxiv_lg](https://arxiv.org/abs/2605.05095v1)
- **Implicit Representations of Grammaticality in Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.05197v1)
- **MRI-Eval: A Tiered Benchmark for Evaluating LLM Performance on MRI Physics and GE Scanner Operations Knowledge** — [arxiv_cl](https://arxiv.org/abs/2605.05175v1)
- **OpenSearch-VL: An Open Recipe for Frontier Multimodal Search Agents** — [huggingface_papers](https://arxiv.org/abs/2605.05185)
- **Stream-T1: Test-Time Scaling for Streaming Video Generation** — [huggingface_papers](https://arxiv.org/abs/2605.04461)
- **Lightning Unified Video Editing via In-Context Sparse Attention** — [huggingface_papers](https://arxiv.org/abs/2605.04569)
- **PhysForge: Generating Physics-Grounded 3D Assets for Interactive Virtual World** — [huggingface_papers](https://arxiv.org/abs/2605.05163)
- **StableI2I: Spotting Unintended Changes in Image-to-Image Transition** — [huggingface_papers](https://arxiv.org/abs/2605.04453)
- **Parameter-Efficient Multi-View Proficiency Estimation: From Discriminative Classification to Generative Feedback** — [huggingface_papers](https://arxiv.org/abs/2605.03848)
- **APEX: Large-scale Multi-task Aesthetic-Informed Popularity Prediction for AI-Generated Music** — [huggingface_papers](https://arxiv.org/abs/2605.03395)
- **Awaking Spatial Intelligence in Unified Multimodal Understanding and Generation** — [huggingface_papers](https://arxiv.org/abs/2605.04128)
- **Rethinking Reasoning-Intensive Retrieval: Evaluating and Advancing Retrievers in Agentic Search Systems** — [huggingface_papers](https://arxiv.org/abs/2605.04018)
- **PatRe: A Full-Stage Office Action and Rebuttal Generation Benchmark for Patent Examination** — [huggingface_papers](https://arxiv.org/abs/2605.03571)
- **A Benchmark for Interactive World Models with a Unified Action Generation Framework** — [huggingface_papers](https://arxiv.org/abs/2605.03941)
- **Workspace-Bench 1.0: Benchmarking AI Agents on Workspace Tasks with Large-Scale File Dependencies** — [huggingface_papers](https://arxiv.org/abs/2605.03596)
- **OpenSeeker-v2: Pushing the Limits of Search Agents with Informative and High-Difficulty Trajectories** — [huggingface_papers](https://arxiv.org/abs/2605.04036)
- **SymptomAI: Towards a Conversational AI Agent for Everyday Symptom Assessment** — [huggingface_papers](https://arxiv.org/abs/2605.04012)
- **Is xAI a neocloud now?** — [techcrunch_ai](https://techcrunch.com/2026/05/06/is-xai-a-neocloud-now/)
- **Five architects of the AI economy explain where the wheels are coming off** — [techcrunch_ai](https://techcrunch.com/2026/05/06/five-architects-of-the-ai-economy-explain-where-the-wheels-are-coming-off/)
- **SpaceX may spend up to $119B on ‘Terafab’ chip factory in Texas** — [techcrunch_ai](https://techcrunch.com/2026/05/06/spacex-may-spend-up-to-119-billion-on-terafab-chip-factory-in-texas/)
- **DeepSeek could hit $45B valuation from its first investment round** — [techcrunch_ai](https://techcrunch.com/2026/05/06/deepseek-could-hit-45b-valuation-from-its-first-investment-round/)
- **Khosla-backed robotics startup Genesis AI has gone full stack, demo shows** — [techcrunch_ai](https://techcrunch.com/2026/05/06/khosla-backed-robotics-startup-genesis-ai-has-gone-full-stack-demo-shows/)
- **5 gardening tips you can try right in Search** — [google_ai](https://blog.google/products-and-platforms/products/search/gardening-tips/)
- **At TechCrunch Disrupt 2026, all your M&A questions will be answered** — [techcrunch_ai](https://techcrunch.com/2026/05/06/at-techcrunch-disrupt-2026-all-your-ma-questions-will-be-answered/)
- **3 days left to lock in 50% off a second ticket to TechCrunch Disrupt 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/06/3-days-left-to-lock-in-50-off-a-second-ticket-to-techcrunch-disrupt-2026/)
- **AI boom pushes Samsung to $1T** — [techcrunch_ai](https://techcrunch.com/2026/05/06/ai-boom-pushes-samsung-to-1t/)
- **The Download: seafloor science and military chatbots** — [mit_tech_review](https://www.technologyreview.com/2026/05/06/1136917/the-download-seafloor-science-military-ai-chatbots/)
- **Barry Diller trusts Sam Altman. But ‘trust is irrelevant’ as AGI nears, he says.** — [techcrunch_ai](https://techcrunch.com/2026/05/06/barry-diller-trusts-sam-altman-but-trust-is-irrelevant-as-agi-nears-he-says/)
- **Snap says its $400M deal with Perplexity ‘amicably ended’** — [techcrunch_ai](https://techcrunch.com/2026/05/06/snap-says-its-400m-deal-with-perplexity-amicably-ended/)
- **How Elon Musk left OpenAI, according to Greg Brockman** — [techcrunch_ai](https://techcrunch.com/2026/05/06/how-elon-musk-left-openai-according-to-greg-brockman/)
- **Google updates AI search to include quotes from Reddit and other sources** — [techcrunch_ai](https://techcrunch.com/2026/05/06/google-updates-ai-search-to-include-expert-advice-from-reddit-and-other-web-forums/)
- **Tinder owner Match Group is slowing hiring to pay for its increased use of AI tools** — [techcrunch_ai](https://techcrunch.com/2026/05/06/tinder-owner-match-group-is-slowing-hiring-to-pay-for-its-increased-use-of-ai-tools/)
- **Apple to pay $250M to settle lawsuit over Siri’s delayed AI features** — [techcrunch_ai](https://techcrunch.com/2026/05/06/apple-to-pay-250m-to-settle-lawsuit-over-siris-delayed-ai-features/)
- **Ethos raises $22.75M from a16z for its expert network with voice onboarding** — [techcrunch_ai](https://techcrunch.com/2026/05/06/ethos-raises-22-75m-from-a16z-for-its-expert-network-with-voice-onboarding/)
- **0xbl33p/goblintown** — [github](https://github.com/0xbl33p/goblintown)
- **awizemann/harness** — [github](https://github.com/awizemann/harness)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **KSroido/Kagi-Session2API-MCP** — [github](https://github.com/KSroido/Kagi-Session2API-MCP)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **warpdot-dev/craft-agents-oss** — [github](https://github.com/warpdot-dev/craft-agents-oss)
- **warpdot-dev/composio** — [github](https://github.com/warpdot-dev/composio)
- **lukiIabs/trading-agents** — [github](https://github.com/lukiIabs/trading-agents)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **YutoTerashima/agent-safety-eval-lab** — [github](https://github.com/YutoTerashima/agent-safety-eval-lab)
- **wjn1996/HeavySkill** — [github](https://github.com/wjn1996/HeavySkill)
- **alvinunreal/openpets** — [github](https://github.com/alvinunreal/openpets)
- **adithya-s-k/RL_Envs_101** — [github](https://github.com/adithya-s-k/RL_Envs_101)
- **prime-radiant-inc/books-for-bots** — [github](https://github.com/prime-radiant-inc/books-for-bots)
- **kostyay/pi-k-excalidraw** — [github](https://github.com/kostyay/pi-k-excalidraw)
- **Naroh091/hermes-war-room** — [github](https://github.com/Naroh091/hermes-war-room)
- **SuperagenticAI/pyflue** — [github](https://github.com/SuperagenticAI/pyflue)
- **00后下场整顿Agent：啥都不学就能用好AI，这才是正确打开方式** — [qbitai](https://www.qbitai.com/2026/05/413612.html)
- **一年磨一剑，今年最炸机器人Demo来了！** — [qbitai](https://www.qbitai.com/2026/05/413830.html)
- **云知声山海知医慧保大模型重磅发布：以高密智能深耕高价值场景，重构医疗保险数智新生态** — [qbitai](https://www.qbitai.com/2026/05/413782.html)
- **波士顿动力泯然众人了，高管集体出走，机器人“量产”只能造4台** — [qbitai](https://www.qbitai.com/2026/05/413613.html)
- **英伟达重新思考AI TCO：为何每Token成本才是唯一重要的指标** — [qbitai](https://www.qbitai.com/2026/05/413604.html)
- **Token需求狂飙千倍，22亿热钱涌向这家AGI Infra头号玩家** — [qbitai](https://www.qbitai.com/2026/05/413591.html)
- **马斯克22万张GPU全卖给Claude用：5小时限额翻倍，双方合作建太空算力** — [qbitai](https://www.qbitai.com/2026/05/413569.html)
- **AI PPT，这次是真不用返工了** — [qbitai](https://www.qbitai.com/2026/05/413296.html)
- **香蕉和GPT Image之外的第3条路：华人15人团队造出AI生图黑马** — [qbitai](https://www.qbitai.com/2026/05/413264.html)
- **友邦人寿等在天津成立股权投资基金，出资额61亿** — [36kr](https://36kr.com/newsflashes/3798988033416192?f=rss)
- **腾讯等入股机器人灵巧手研发商临界点** — [36kr](https://36kr.com/newsflashes/3798889072663809?f=rss)
- **对话孙来春：年入25亿的林清轩不想做中国欧莱雅 ｜厚雪专访** — [36kr](https://36kr.com/p/3797662460419337?f=rss)
- **斯坦福博士后创立的柔性触觉传感器公司获超亿元融资，低成本触觉手套将量产落地｜硬氪首发** — [36kr](https://36kr.com/p/3797155747748867?f=rss)
- **像素绽放PixelBloom完成C轮融资，全面发力AI办公解决方案Agent：从“一分钟生成PPT”到“交付商用级结果”** — [36kr](https://36kr.com/p/3797787228151048?f=rss)
- **8点1氪丨三星宣布停止在中国大陆市场销售所有家电产品；李嘉诚抛售资产套现约455亿；月之暗面将完成20亿美元新融资，估值破200亿美元** — [36kr](https://36kr.com/p/3798462137637892?f=rss)
- **氪星晚报｜三星电子借AI热潮市值突破1万亿美元；智源发布业内首个心脏磁共振多模态诊断智能体BAAI Cardiac Agent；财政部今年将在香港发行840亿元人民币国债** — [36kr](https://36kr.com/p/3797482256325888?f=rss)
- **“鹰瞰智翼”完成Pre-A轮数千万元融资** — [36kr](https://36kr.com/newsflashes/3798919451712776?f=rss)