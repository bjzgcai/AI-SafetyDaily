# AI 日报 [AI 安全] - 2026-05-08


# AI 安全与治理每日综述

**日期：** 2026-05-08
**主题：** AI 安全、对齐、安全、隐私与治理

## 亮点

今日学术界的进展主要集中在跨文化安全基准的构建、Agent 状态攻击的防御以及大模型鲁棒性的系统性评估。**XL-SafetyBench: A Country-Grounded Cross-Cultural Benchmark for LLM Safety and Cultural Sensitivity** 突破了现有基准以英语为中心的限制，提出了国家层面的文化敏感性评估框架。**Stateful Agent Backdoor** 揭示了多会话 Agent 攻击的新风险，指出当前防御机制难以应对跨会话的状态维持攻击。此外，**SoK: Robustness in Large Language Models against Jailbreak Attacks** 对现有的对抗攻击与防御方法进行了系统性综述，指出了评估指标的多维性不足。产业界方面，OpenAI 推出了“可信联系人”功能，旨在通过外部通知机制应对用户自残风险，但这属于产品层面的安全增强，其实际有效性尚待独立验证。

## 对抗攻击与鲁棒性

当前针对大语言模型（LLM）的对抗攻击正从单轮对话向多轮、多 Agent 协作及系统级漏洞演变。**SoK: Robustness in Large Language Models against Jailbreak Attacks** 指出，现有的评估实践往往依赖单一的“攻击成功率”指标，无法捕捉安全风险的维度多样性。该综述强调，尽管连续对抗训练（CAT）和连续偏好优化（CAPO）等方法提升了模型在嵌入空间的鲁棒性，但面对新颖的攻击策略时，模型仍表现出脆弱性。与此同时，**Stateful Agent Backdoor** 将攻击生命周期扩展到了多个会话中，通过持久化组件实现跨会话的自主增量执行，这种基于 Mealy 机模型的形式化攻击框架表明，现有的无状态防御机制在面对此类攻击时存在显著盲区。

在系统层面，**Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** 评估了不同检索增强生成（RAG）架构在知识库投毒下的表现，发现多 Agent 辩论和递归语言模型等复杂架构在面对对抗性优化矛盾时，并未表现出预期的鲁棒性。此外，**LeakDojo: Decoding the Leakage Threats of RAG Systems** 提供了一个可配置的框架，用于系统评估 RAG 系统的泄露风险，实验显示查询生成和对抗性指令注入是主要的泄露向量。在隐私攻击方面，**Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models** 提出了一种黑盒成员推断攻击，通过将目标数据转化为测验题来推断模型是否记忆了特定训练样本，该方法在多个主流模型上取得了较高的 ROC-AUC 值，揭示了 LLM 在数据隐私保护方面的潜在风险。

这些工作共同指向一个趋势：安全评估需要从单一模型内部转向系统架构和长期交互过程。**SoK** 与 **Stateful Agent Backdoor** 的对比显示，前者关注模型层面的对抗鲁棒性，后者则关注 Agent 层面的状态持久性风险，两者互补地揭示了 LLM 安全生态中的不同薄弱环节。

## 模型对齐与可解释性

在模型对齐与推理能力的提升上，强化学习（RL）与自蒸馏技术成为研究热点，但其理论机制仍存在争议。**Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** 提出，RL 可能并未教授新的策略，而是将概率质量重新分配至基座模型已包含的解决方案路径上。这一观点挑战了 RL 在提升推理能力中的核心作用，暗示优化过程可能仅是稀疏策略选择而非能力学习。与此相对，**UniSD: Towards a Unified Self-Distillation Framework for Large Language Models** 则致力于构建统一的自蒸馏框架，试图解决自生成轨迹自由且正确性依赖任务的问题，通过整合互补机制来稳定监督信号。

在可解释性领域，**Patch-Effect Graph Kernels for LLM Interpretability** 将机械解释学问题重构为图机器学习问题，通过激活补丁配置文件构建补丁效应图，解决了高维非结构化数据难以系统比较的问题。同时，**Invariant Features in Language Models: Geometric Characterization and Model Attribution** 提出了局部几何框架，认为语义等价输入在潜在空间中占据结构化区域，语义身份在不变子空间中得以保留。这些工作表明，可解释性研究正从单一特征的识别转向几何结构和图结构的系统分析。**SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** 进一步改进了稀疏自编码器（SAE）架构，通过动态选择 Top-K 激活特征来适应不同输入的数据复杂度，克服了固定稀疏级别忽略真实数据复杂性的局限。

## 隐私保护与联邦学习

隐私保护机制在联邦学习（FL）和差分隐私（DP）领域取得了理论进展，特别是在噪声机制的优化与客户端选择策略上。**Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling: Tight Upper and Lower Bounds** 推导了基于随机打乱子采样的 DP-SGD 的紧确上下界，相比泊松子采样分析，随机打乱提供了更透明且可解释的闭式界限。**Privacy by Postprocessing the Discrete Laplace Mechanism** 展示了经典离散拉普拉斯机制经过后处理后可实现无偏估计，并兼容拉普拉斯机制或阶梯机制的隐私参数，证明了该机制的通用性。**α-Wasserstein Mechanism for Rényi Pufferfish Privacy** 则引入了基于 Wasserstein 度量的机制，用于实现 Rényi Pufferfish 隐私，扩展了噪声校准的理论边界。

在联邦学习的具体应用场景中，**AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** 利用信息年龄（AoI）作为时效性感知指标，优化了联邦入侵检测中的客户端参与策略，解决了异构带宽和掉线导致的陈旧信息问题。**FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** 探讨了在联邦微调中保护数据所有权的水印放射性测试方法，指出安全聚合（SA）虽能保护隐私，但客户端级归属权检测仍面临挑战。**Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** 提出了隐私锚点替换（PAS）机制，通过相对锚点编码实现空间检索中的用户位置隐私保护，在保持 RAG 管道兼容性的同时提供了粗粒度的隐私保证。

这些工作表明，隐私保护正从单纯的噪声添加转向更精细的机制设计与系统级优化，特别是在联邦学习场景下，如何在保证数据归属权的同时维持模型效用是一个关键挑战。

## 安全评估基准与治理

随着大模型应用的多样化，安全评估基准正从通用任务向特定领域和跨文化场景扩展。**XL-SafetyBench: A Country-Grounded Cross-Cultural Benchmark for LLM Safety and Cultural Sensitivity** 构建了涵盖 10 个国家语言对的 5500 个测试用例，区分了国家特定的危害与文化嵌入的敏感性，弥补了现有基准以英语为中心且依赖翻译的不足。**Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity** 定义了评估上下文差异，指出模型行为可能因提示是评估、部署交互还是中性请求而不同，提出了配对提示协议来测量这种差异。**When No Benchmark Exists: Validating Comparative LLM Safety Scoring Without Ground-Truth Labels** 形式化了无基准比较安全评分的设置，指出在没有标签的情况下，场景审计的有效性依赖于仪器有效性链而非真实标签的一致性。

在治理层面，**Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** 分析了在线安全法规下标量指标作为合规证据的风险，指出战略平台可能通过路由语义等效内容变体来优化分数而不减少真实危害。这些工作共同强调了评估基准的语境敏感性和指标的可操纵性，呼吁建立更动态、更难以被策略性操纵的评估体系。

## Agent 安全与工具生态

随着自主 Agent 的兴起，工具生态与 Agent 安全成为新的关注点。**OpenSearch-VL: An Open Recipe for Frontier Multimodal Search Agents** 提供了一个完全开源的配方，用于通过高质量数据筛选和代理强化学习训练前沿多模态深度搜索 Agent。**AgentClaw** 和 **AiSOC** 等开源项目展示了将自然语言指令转化为可重用能力的工具链，以及基于 AI 的安全运营中心（SOC）框架，支持警报融合和 MITRE ATT&CK 调查。**Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** 指出自托管计算机使用 Agent 面临主机级滥用风险，建议通过可信执行环境（TEE）隔离来应对，认为仅靠临时阻断规则无法解决此类风险。

这些工具与框架的发布表明，Agent 安全研究正从理论模型转向工程化落地，但同时也带来了新的攻击面，如 **Stateful Agent Backdoor** 所揭示的跨会话攻击风险，需要结合 **AiSOC** 等监控工具进行实时防御。

## Looking Forward

尽管在对抗鲁棒性、隐私机制和评估基准方面取得了显著进展，但仍存在若干未解决的理论问题。首先，针对 **Stateful Agent Backdoor** 的防御机制尚缺乏形式化的验证框架，如何在不牺牲 Agent 功能性的前提下实现跨会话状态的安全隔离是一个待验证的假设。其次，**Rethinking RL for LLM Reasoning** 提出的 RL 仅作为稀疏策略选择的观点，若被证实，将需要重新审视当前基于 RL 的对齐训练范式，探索更高效的优化路径。最后，**XL-SafetyBench** 揭示的跨文化安全差异表明，全球通用的安全对齐标准可能无法覆盖所有文化背景下的特定危害，未来需要建立动态的、本地化的安全评估体系。此外，**Gaming the Metric** 指出的指标操纵风险，要求治理框架从静态合规转向动态行为监测，以应对战略平台的规避行为。

---


## 参考来源

- **XL-SafetyBench: A Country-Grounded Cross-Cultural Benchmark for LLM Safety and Cultural Sensitivity** — [huggingface_papers](https://arxiv.org/abs/2605.05662)
- **AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** — [arxiv_cr](https://arxiv.org/abs/2605.05644v1)
- **Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** — [arxiv_cr](https://arxiv.org/abs/2605.05459v1)
- **SoK: Robustness in Large Language Models against Jailbreak Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.05058v1)
- **Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.06423v1)
- **How Many Iterations to Jailbreak? Dynamic Budget Allocation for Multi-Turn LLM Evaluation** — [arxiv_lg](https://arxiv.org/abs/2605.06605v1)
- **FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** — [arxiv_lg](https://arxiv.org/abs/2605.06596v1)
- **On the Safety of Graph Representation Learning** — [arxiv_lg](https://arxiv.org/abs/2605.06576v1)
- **Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** — [arxiv_cr](https://arxiv.org/abs/2605.05632v1)
- **Information Theoretic Adversarial Training of Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.05415v1)
- **Privacy by Postprocessing the Discrete Laplace Mechanism** — [arxiv_cr](https://arxiv.org/abs/2605.06502v1)
- **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** — [arxiv_cr](https://arxiv.org/abs/2605.06393v1)
- **Why Global LLM Leaderboards Are Misleading: Small Portfolios for Heterogeneous Supervised ML** — [arxiv_lg](https://arxiv.org/abs/2605.06656v1)
- **PianoCoRe: Combined and Refined Piano MIDI Dataset** — [arxiv_lg](https://arxiv.org/abs/2605.06627v1)
- **Online Bayesian Calibration under Gradual and Abrupt System Changes** — [arxiv_lg](https://arxiv.org/abs/2605.06612v1)
- **SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** — [arxiv_lg](https://arxiv.org/abs/2605.06610v1)
- **CLAD: A Clustered Label-Agnostic Federated Learning Framework for Joint Anomaly Detection and Attack Classification** — [arxiv_lg](https://arxiv.org/abs/2605.06571v1)
- **Market-Alignment Risk in Pricing Agents: Trace Diagnostics and Trace-Prior RL under Hidden Competitor State** — [arxiv_lg](https://arxiv.org/abs/2605.06529v1)
- **Beyond Negative Rollouts: Positive-Only Policy Optimization with Implicit Negative Gradients** — [arxiv_cl](https://arxiv.org/abs/2605.06650v1)
- **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** — [arxiv_cl](https://arxiv.org/abs/2605.06635v1)
- **Patch-Effect Graph Kernels for LLM Interpretability** — [arxiv_cl](https://arxiv.org/abs/2605.06480v1)
- **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling: Tight Upper and Lower Bounds** — [arxiv_cr](https://arxiv.org/abs/2605.06259v1)
- **Profiling for Pennies: Unveiling the Privacy Iceberg of LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2605.06232v1)
- **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** — [arxiv_cr](https://arxiv.org/abs/2605.05928v1)
- **$α$-Wasserstein Mechanism for Rényi Pufferfish Privacy** — [arxiv_cr](https://arxiv.org/abs/2605.05723v1)
- **Evaluating the Reliability of Multiple Large Language Models in Risk Assessment: A CIS Controls Based Approach** — [arxiv_cr](https://arxiv.org/abs/2605.05424v1)
- **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** — [arxiv_cr](https://arxiv.org/abs/2605.06505v1)
- **Autonomous Adversary: Red-Teaming in the age of LLM** — [arxiv_cr](https://arxiv.org/abs/2605.06486v1)
- **Are We Making Progress in Multimodal Domain Generalization? A Comprehensive Benchmark Study** — [arxiv_lg](https://arxiv.org/abs/2605.06643v1)
- **Hybrid Quantum-Classical GANs for the Generation of Adversarial Network Flows** — [arxiv_lg](https://arxiv.org/abs/2605.06629v1)
- **LiVeAction: a Lightweight, Versatile, and Asymmetric Neural Codec Design for Real-time Operation** — [arxiv_lg](https://arxiv.org/abs/2605.06628v1)
- **Cross-Modal Navigation with Multi-Agent Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.06595v1)
- **ReActor: Reinforcement Learning for Physics-Aware Motion Retargeting** — [arxiv_lg](https://arxiv.org/abs/2605.06593v1)
- **DINORANKCLIP: DINOv3 Distillation and Injection for Vision-Language Pretraining with High-Order Ranking Consistency** — [arxiv_lg](https://arxiv.org/abs/2605.06592v1)
- **Towards Metric-Faithful Neural Graph Matching** — [arxiv_lg](https://arxiv.org/abs/2605.06588v1)
- **Distributionally-Robust Learning to Optimize** — [arxiv_lg](https://arxiv.org/abs/2605.06585v1)
- **Directional Consistency as a Complementary Optimization Signal: The GONO Framework** — [arxiv_lg](https://arxiv.org/abs/2605.06575v1)
- **SNAPO: Smooth Neural Adjoint Policy Optimization for Optimal Control via Differentiable Simulation** — [arxiv_lg](https://arxiv.org/abs/2605.06570v1)
- **Dynamic Treatment on Networks** — [arxiv_lg](https://arxiv.org/abs/2605.06564v1)
- **Verifier-Backed Hard Problem Generation for Mathematical Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.06660v1)
- **MASPO: Joint Prompt Optimization for LLM-based Multi-Agent Systems** — [arxiv_cl](https://arxiv.org/abs/2605.06623v1)
- **UniSD: Towards a Unified Self-Distillation Framework for Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.06597v1)
- **PairAlign: A Framework for Sequence Tokenization via Self-Alignment with Applications to Audio Tokenization** — [arxiv_cl](https://arxiv.org/abs/2605.06582v1)
- **Continuous Latent Diffusion Language Model** — [arxiv_cl](https://arxiv.org/abs/2605.06548v1)
- **STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?** — [arxiv_cl](https://arxiv.org/abs/2605.06527v1)
- **Invariant Features in Language Models: Geometric Characterization and Model Attribution** — [arxiv_cl](https://arxiv.org/abs/2605.06458v1)
- **Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** — [arxiv_cr](https://arxiv.org/abs/2605.06324v1)
- **Stateful Agent Backdoor** — [arxiv_cr](https://arxiv.org/abs/2605.06158v1)
- **Secure Seed-Based Multi-bit Watermarking for Diffusion Models from First Principles** — [arxiv_cr](https://arxiv.org/abs/2605.06153v1)
- **Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** — [arxiv_cr](https://arxiv.org/abs/2605.05995v1)
- **LeakDojo: Decoding the Leakage Threats of RAG Systems** — [arxiv_cr](https://arxiv.org/abs/2605.05818v1)
- **Is Escalation Worth It? A Decision-Theoretic Characterization of LLM Cascades** — [arxiv_cl](https://arxiv.org/abs/2605.06350v1)
- **Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity** — [arxiv_cl](https://arxiv.org/abs/2605.06327v1)
- **Quantifying the Statistical Effect of Rubric Modifications on Human-Autorater Agreement** — [arxiv_cl](https://arxiv.org/abs/2605.06283v1)
- **Linear Semantic Segmentation for Low-Resource Spoken Dialects** — [arxiv_cl](https://arxiv.org/abs/2605.06276v1)
- **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** — [arxiv_cl](https://arxiv.org/abs/2605.06241v1)
- **Contrastive Identification and Generation in the Limit** — [arxiv_cl](https://arxiv.org/abs/2605.06211v1)
- **Nonsense Helps: Prompt Space Perturbation Broadens Reasoning Exploration** — [huggingface_papers](https://arxiv.org/abs/2605.05566)
- **Think, then Score: Decoupled Reasoning and Scoring for Video Reward Modeling** — [huggingface_papers](https://arxiv.org/abs/2605.05922)
- **Skill1: Unified Evolution of Skill-Augmented Agents via Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.06130)
- **MARBLE: Multi-Aspect Reward Balance for Diffusion RL** — [huggingface_papers](https://arxiv.org/abs/2605.06507)
- **ReflectDrive-2: Reinforcement-Learning-Aligned Self-Editing for Discrete Diffusion Driving** — [huggingface_papers](https://arxiv.org/abs/2605.04647)
- **A Foundation Model for Zero-Shot Logical Rule Induction** — [huggingface_papers](https://arxiv.org/abs/2605.04916)
- **When to Think, When to Speak: Learning Disclosure Policies for LLM Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.03314)
- **D-OPSD: On-Policy Self-Distillation for Continuously Tuning Step-Distilled Diffusion Models** — [huggingface_papers](https://arxiv.org/abs/2605.05204)
- **EMO: Pretraining Mixture of Experts for Emergent Modularity** — [arxiv_cl](https://arxiv.org/abs/2605.06663v1)
- **When No Benchmark Exists: Validating Comparative LLM Safety Scoring Without Ground-Truth Labels** — [arxiv_cl](https://arxiv.org/abs/2605.06652v1)
- **StraTA: Incentivizing Agentic Reinforcement Learning with Strategic Trajectory Abstraction** — [arxiv_cl](https://arxiv.org/abs/2605.06642v1)
- **Recursive Agent Optimization** — [arxiv_cl](https://arxiv.org/abs/2605.06639v1)
- **AI Co-Mathematician: Accelerating Mathematicians with Agentic AI** — [huggingface_papers](https://arxiv.org/abs/2605.06651)
- **Auto Research with Specialist Agents Develops Effective and Non-Trivial Training Recipes** — [huggingface_papers](https://arxiv.org/abs/2605.05724)
- **The Granularity Axis: A Micro-to-Macro Latent Direction for Social Roles in Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.06196)
- **TabEmbed: Benchmarking and Learning Generalist Embeddings for Tabular Understanding** — [huggingface_papers](https://arxiv.org/abs/2605.04962)
- **CreativityBench: Evaluating Agent Creative Reasoning via Affordance-Based Tool Repurposing** — [huggingface_papers](https://arxiv.org/abs/2605.02910)
- **SWE-WebDevBench: Evaluating Coding Agent Application Platforms as Virtual Software Agencies** — [huggingface_papers](https://arxiv.org/abs/2605.04637)
- **The First Token Knows: Single-Decode Confidence for Hallucination Detection** — [huggingface_papers](https://arxiv.org/abs/2605.05166)
- **OpenSearch-VL: An Open Recipe for Frontier Multimodal Search Agents** — [huggingface_papers](https://arxiv.org/abs/2605.05185)
- **Stream-T1: Test-Time Scaling for Streaming Video Generation** — [huggingface_papers](https://arxiv.org/abs/2605.04461)
- **Lightning Unified Video Editing via In-Context Sparse Attention** — [huggingface_papers](https://arxiv.org/abs/2605.04569)
- **PhysForge: Generating Physics-Grounded 3D Assets for Interactive Virtual World** — [huggingface_papers](https://arxiv.org/abs/2605.05163)
- **OpenAI launches new voice intelligence features in its API** — [techcrunch_ai](https://techcrunch.com/2026/05/07/openai-launches-new-voice-intelligence-features-in-its-api/)
- **Elon Musk’s lawsuit is putting OpenAI’s safety record under the microscope** — [techcrunch_ai](https://techcrunch.com/2026/05/07/elon-musks-lawsuit-is-putting-openais-safety-record-under-the-microscope/)
- **Bumble is getting rid of the swipe, CEO says** — [techcrunch_ai](https://techcrunch.com/2026/05/07/bumble-is-getting-rid-of-the-swipe-ceo-says/)
- **Mira Murati’s deposition pulled back the curtain on Sam Altman’s ouster** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/926383/mira-murati-sam-altman-musk-trial-ouster)
- **Apple&#8217;s AirPods with cameras for AI are apparently close to production** — [theverge_ai](https://www.theverge.com/tech/926376/apple-airpods-cameras-ai-production)
- **SpaceX has a $55 billion plan to build AI chips in Texas** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/926356/spacex-terafab-plant-cost-ai-chips)
- **ChatGPT&#8217;s &#8216;Trusted Contact&#8217; will alert loved ones of safety concerns** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/925874/chatgpt-trusted-contact-emergency-self-harm-notification)
- **Startup Battlefield 200 applications close May 27: A shot at VC access, global visibility, TechCrunch coverage, and $100K** — [techcrunch_ai](https://techcrunch.com/2026/05/07/startup-battlefield-200-applications-close-may-27-a-shot-at-vc-access-global-visibility-techcrunch-coverage-and-100k/)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **Exhibit at TechCrunch Disrupt 2026: Get in front of 10,000 decision-makers before space runs out** — [techcrunch_ai](https://techcrunch.com/2026/05/07/exhibit-at-techcrunch-disrupt-2026-get-in-front-of-10000-decision-makers-before-space-runs-out/)
- **Aurora’s Chris Urmson on why self-driving trucks are finally ready to scale** — [techcrunch_ai](https://techcrunch.com/podcast/auroras-chris-urmson-on-why-self-driving-trucks-are-finally-ready-to-scale/)
- **2 days left: Get 50% off a second pass to TechCrunch Disrupt 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/07/2-days-left-get-50-off-a-second-pass-to-techcrunch-disrupt-2026/)
- **OpenClaw and Claude can put your AI-generated podcasts in Spotify** — [theverge_ai](https://www.theverge.com/entertainment/925916/save-to-spotify-ai-podcasts)
- **Google’s taking a big swing at AI health with the Fitbit Air** — [theverge_ai](https://www.theverge.com/gadgets/925458/google-health-fitbit-air-ai-coaching-wearables-fitness-trackers)
- **Scaling Trusted Access for Cyber with GPT-5.5 and GPT-5.5-Cyber** — [openai](https://openai.com/index/gpt-5-5-with-trusted-access-for-cyber)
- **The Download: the tech reshaping IVF and the rise of balcony solar** — [mit_tech_review](https://www.technologyreview.com/2026/05/07/1136956/the-download-ivf-tech-balcony-solar/)
- **Parloa builds service agents customers want to talk to** — [openai](https://openai.com/index/parloa)
- **Advancing voice intelligence with new models in the API** — [openai](https://openai.com/index/advancing-voice-intelligence-with-new-models-in-the-api)
- **The balcony solar boom is coming to the US** — [mit_tech_review](https://www.technologyreview.com/2026/05/07/1136933/balcony-solar-boom/)
- **What’s next for IVF** — [mit_tech_review](https://www.technologyreview.com/2026/05/07/1136946/whats-next-for-ivf-ai-robot-pgt-gene-editing/)
- **Five architects of the AI economy explain where the wheels are coming off** — [techcrunch_ai](https://techcrunch.com/2026/05/06/five-architects-of-the-ai-economy-explain-where-the-wheels-are-coming-off/)
- **Voi founders’ new AI startup Pit has become the latest rising star out of Stockholm** — [techcrunch_ai](https://techcrunch.com/2026/05/07/voi-founders-new-ai-startup-pit-has-become-the-latest-rising-star-out-of-stockholm/)
- **OpenAI introduces new ‘Trusted Contact’ safeguard for cases of possible self-harm** — [techcrunch_ai](https://techcrunch.com/2026/05/07/openai-introduces-new-trusted-contact-safeguard-for-cases-of-possible-self-harm/)
- **Perplexity’s Personal Computer is now available to everyone on Mac** — [techcrunch_ai](https://techcrunch.com/2026/05/07/perplexitys-personal-computer-is-now-available-everyone-on-mac/)
- **How Anthropic’s Mythos has rewritten Firefox’s approach to cybersecurity** — [techcrunch_ai](https://techcrunch.com/2026/05/07/how-anthropics-mythos-has-rewritten-firefoxs-approach-to-cybersecurity/)
- **China’s Moonshot AI raises $2B at $20B valuation as demand for open source AI skyrockets** — [techcrunch_ai](https://techcrunch.com/2026/05/07/chinas-moonshot-ai-raises-2b-at-20b-valuation-as-demand-for-open-source-ai-skyrockets/)
- **Spotify wants to become the home for AI-generated personal audio** — [techcrunch_ai](https://techcrunch.com/2026/05/07/spotify-wants-to-become-the-home-for-ai-generated-personal-audio/)
- **Spotify’s AI DJ now supports French, German, Italian, and Brazilian Portuguese** — [techcrunch_ai](https://techcrunch.com/2026/05/07/spotifys-ai-dj-now-supports-french-german-italian-and-brazilian-portuguese/)
- **Negai-ai/AgentClaw** — [github](https://github.com/Negai-ai/AgentClaw)
- **dingdingpw/monitor** — [github](https://github.com/dingdingpw/monitor)
- **cenconq25/claude-code-app-studio** — [github](https://github.com/cenconq25/claude-code-app-studio)
- **beenuar/AiSOC** — [github](https://github.com/beenuar/AiSOC)
- **shawn0728/OpenSearch-VL** — [github](https://github.com/shawn0728/OpenSearch-VL)
- **awizemann/harness** — [github](https://github.com/awizemann/harness)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **k1ng0fn0th1ng/CrystalForge** — [github](https://github.com/k1ng0fn0th1ng/CrystalForge)
- **Jason-Cyr/ai-shared-brain** — [github](https://github.com/Jason-Cyr/ai-shared-brain)
- **alterhq/openpets** — [github](https://github.com/alterhq/openpets)
- **huseynovvusal/blamebot** — [github](https://github.com/huseynovvusal/blamebot)
- **ZhongKuang/TAAC2026-CLI** — [github](https://github.com/ZhongKuang/TAAC2026-CLI)
- **0xhackerfren/ProcMon-MCP** — [github](https://github.com/0xhackerfren/ProcMon-MCP)
- **Autoloops/upskill** — [github](https://github.com/Autoloops/upskill)
- **wjn1996/HeavySkill** — [github](https://github.com/wjn1996/HeavySkill)
- **原生Agent杀入画布！一站式搞定专业创作，全程可控、不抽卡** — [qbitai](https://www.qbitai.com/2026/05/413912.html)
- **离谱！一句话+百元预算，这只龙虾就给我搓出了一支百万级广告片？** — [qbitai](https://www.qbitai.com/2026/05/414006.html)
- **00后下场整顿Agent：啥都不学就能用好AI，这才是正确打开方式** — [qbitai](https://www.qbitai.com/2026/05/413612.html)
- **一年磨一剑，今年最炸机器人Demo来了！** — [qbitai](https://www.qbitai.com/2026/05/413830.html)
- **云知声山海知医慧保大模型重磅发布：以高密智能深耕高价值场景，重构医疗保险数智新生态** — [qbitai](https://www.qbitai.com/2026/05/413782.html)
- **波士顿动力泯然众人了，高管集体出走，机器人“量产”只能造4台** — [qbitai](https://www.qbitai.com/2026/05/413613.html)
- **英伟达重新思考AI TCO：为何每Token成本才是唯一重要的指标** — [qbitai](https://www.qbitai.com/2026/05/413604.html)
- **8点1氪丨段永平再加仓泡泡玛特；多平台已下架“全李酒店”；世界杯决赛门票1张200万美元，FIFA回应** — [36kr](https://36kr.com/p/3799881836633093?f=rss)
- **氪星晚报 ｜千问PC端上线AI语音输入；宝马一季度利润降25%，至23亿欧元** — [36kr](https://36kr.com/p/3799089350712324?f=rss)
- **联想创投旗下基金等入股微分智飞，后者为飞行具身智能研发商** — [36kr](https://36kr.com/newsflashes/3800034382060552?f=rss)
- **第一代全固态电池迈入规模化市场，「纯锂新能源」完成数千万元Pre-A+轮融资 | 36氪首发** — [36kr](https://36kr.com/p/3800022823951363?f=rss)
- **印度投资者转向海外市场，因国内缺乏AI题材且回报率低** — [36kr](https://36kr.com/newsflashes/3800007655480325?f=rss)
- **爱旭股份旗下山东太阳能公司增资至63亿，增幅26%** — [36kr](https://36kr.com/newsflashes/3800001066376200?f=rss)
- **英伟达CEO黄仁勋：下一代AI基础设施将需要大量的光学连接，铜线已无法满足需求** — [36kr](https://36kr.com/newsflashes/3799989766429697?f=rss)
- **36氪首发 | 清华系AI Infra厂商完成数亿元融资，以GPU为核心重构计算机系统架构** — [36kr](https://36kr.com/p/3799984046333186?f=rss)
- **兰州未来创新产业发展基金成立，注册资本约2亿** — [36kr](https://36kr.com/newsflashes/3799978675805441?f=rss)
- **Plaud获头部大厂投资，目前估值达20亿美元｜硬氪独家** — [36kr](https://36kr.com/p/3799129165863937?f=rss)
- **OpenAI推出“可信联系人”安全功能** — [36kr](https://36kr.com/newsflashes/3799937097129224?f=rss)
- **Anthropic旗下Mythos模型打乱白宫人工智能战略** — [36kr](https://36kr.com/newsflashes/3799949875617031?f=rss)
- **在模型厂碾压之前，AI视频Agent产品是否只能挣波快钱？** — [36kr](https://36kr.com/p/3786528811572481?f=rss)
- **每日互动：一季度公司AI相关业务收入已接近去年全年水平** — [36kr](https://36kr.com/newsflashes/3800023288569088?f=rss)
- **高盛将沪深300指数12个月目标位设在5300点，指出投资A股颇具吸引力** — [36kr](https://36kr.com/newsflashes/3800001611422725?f=rss)
- **“阶跃星辰”将完成近25亿美元融资** — [36kr](https://36kr.com/newsflashes/3800006173973760?f=rss)
- **A股三大指数集体低开，半导体、光模块概念领跌** — [36kr](https://36kr.com/newsflashes/3799967438756872?f=rss)