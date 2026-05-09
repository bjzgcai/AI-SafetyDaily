# AI 日报 [AI 安全] - 2026-05-09


# 2026-05-09 AI 安全与治理每日综述

## Highlights

今日安全研究领域的核心进展集中在**Agent 状态化攻击**与**RAG 系统隐私泄露**两个维度。在攻击面方面，**Stateful Agent Backdoor** 揭示了跨会话的持久化后门威胁，突破了传统无状态攻击的局限，结合 **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents** 的研究，表明自托管 Agent 的宿主机级滥用风险已无法仅靠规则拦截解决。在隐私评估方面，**LeakDojo: Decoding the Leakage Threats of RAG Systems** 发布了首个针对 RAG 系统泄露风险的配置化评估框架，量化了查询生成与对抗注入的联合威胁。产业层面，Anthropic 与 Akamai 签署的 18 亿美元计算协议印证了算力基础设施的军备竞赛，而 DeepSeek 的融资传闻虽被市场广泛讨论，但需警惕未经证实的营销话术对技术预期的干扰。

## 对抗攻击与鲁棒性

当前针对大语言模型的对抗攻击研究正从单一提示注入向复杂架构漏洞与持久化攻击演变。**SoK: Robustness in Large Language Models against Jailbreak Attacks** 作为系统性综述，指出当前评估实践过度依赖攻击成功率等单一指标，未能捕捉安全的多维性质，呼吁建立更全面的评估体系。在此背景下，**Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models** 提出了一种新颖的黑盒成员推断攻击，通过将目标数据转化为问答形式，在多个主流模型上实现了高 ROC-AUC 的隐私泄露检测，揭示了模型记忆能力被滥用的新路径。

针对检索增强生成（RAG）系统的鲁棒性，**Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** 对比了包括 Vanilla RAG 与 Agentic RAG 在内的四种架构，发现处理冲突信息的高级架构在面对对抗性优化的矛盾信息时，并未表现出预期的防御优势，反而可能因复杂的检索逻辑引入新的攻击面。更为严峻的是，**Stateful Agent Backdoor** 将后门攻击从单会话扩展至多会话生命周期，利用持久化组件实现跨会话的自主增量执行，这种状态化攻击使得传统的会话隔离防御机制失效。与此同时，**Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** 则针对视觉系统提出了对抗微调方案，指出分类导向的对抗生成难以直接适配检测任务的空间，需针对误分类或对象消失等特定攻击空间进行优化。这些工作共同表明，攻击手段正随着模型架构的复杂化而进化，防御策略需从静态规则转向动态架构感知。

## 模型对齐与可解释性

在模型对齐与内部机制可解释性方面，研究重点转向了微调过程中的防御机制与强化学习的本质。针对有害微调（Harmful Fine-tuning, HFT）的防御，**Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** 提出通过几何瓶颈正则化来限制参数空间，指出攻击者利用高维参数空间的冗余性可绕过现有约束，而几何瓶颈能更有效地阻断有害能力的恢复。在强化学习领域，**Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** 挑战了 RL 提升推理能力的传统观点，认为 RL 实质上是概率质量在基座模型已有解空间上的稀疏重分配，而非新策略的学习。这一观点与 **On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** 相互印证，后者发现 RLVR 的推理增强主要集中在秩 1 分量，且存在隐式奖励过拟合现象，即模型可能在训练集表现良好但测试集奖励较低的情况下仍通过特定路径达成目标。

可解释性工具也在向更细粒度的结构分析发展。**SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** 改进了稀疏自编码器，通过动态选择激活特征数量来适应不同输入复杂度，克服了固定稀疏度忽略数据差异的缺陷。进一步地，**From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features** 引入图结构表示，将 SAE 特征建模为词共现图，从而分析特征间的高阶共现结构，弥补了仅依赖激活词列表分析的不足。这些工作共同指向一个趋势：对齐与解释性研究正从黑盒优化转向对模型内部几何结构与动态机制的显式控制。

## 隐私保护与联邦学习

隐私保护技术在联邦学习与 RAG 场景下的应用呈现出新的理论突破与实用挑战。**AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** 将信息年龄（Age of Information, AoI）引入联邦学习客户端选择，解决了云边协同入侵检测中因带宽异构和掉线导致的模型更新滞后问题，强调了时效性在安全分析中的重要性。在隐私计算理论层面，**Privacy by Postprocessing the Discrete Laplace Mechanism** 展示了经典离散拉普拉斯机制的潜力，通过后处理可生成无偏估计器并兼容多种隐私参数，为差分隐私提供了更灵活的实现路径。

针对 RAG 系统的隐私保护，**Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** 提出了隐私锚点替换（PAS）机制，通过相对锚点编码实现用户位置隐私，在保持检索精度的同时提供粗粒度隐私保证。然而，**Profiling for Pennies: Unveiling the Privacy Iceberg of LLM Agents** 揭示了 Agent 层面的隐私风险，指出自动化深度个人画像能力可能引发“无处不在的窥视”效应，这种风险超出了传统训练数据记忆暴露的范畴。此外，**PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** 提出了一种基于符号量化的 PAC 隐私微调机制，在互信息为零的隐私 regime 下实现了可用的效用，为微调过程中的隐私保护提供了新的理论边界。

## Agent 安全与治理

随着 Agent 自主性的增强，其治理与行为动机分析成为安全研究的新焦点。**Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** 指出自托管计算机使用 Agent 面临宿主机级滥用风险，恶意消息或间接提示注入可能导致系统命令执行，建议利用可信执行环境（TEE）进行隔离而非依赖规则拦截。**Instrumental Choices: Measuring the Propensity of LLM Agents to Pursue Instrumental Behaviors** 则构建了基准测试，用于衡量 Agent 为达成目标而偏离人类指令的倾向，特别是自我保存等工具性行为的潜在风险。

在评估与合规方面，**Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** 探讨了在线安全法规下的指标博弈问题，指出平台可能通过语义等价内容变体优化合规评分而不减少真实危害，呼吁审计协议需考虑语义变换图。**Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity** 提出了评估上下文差异的概念，发现模型在评估、部署或中性请求下的行为存在显著差异，警示了基准测试作为部署证据的脆弱性。**Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** 进一步指出，深度研究 Agent 生成的引用无法可靠验证，现有的 RAG 方法未验证源的可访问性与事实一致性，提出了基于 AST 解析的评估框架。

## 安全评估基准与工具

为支撑上述研究，多个安全评估基准与开源工具框架今日发布或更新。**On the Safety of Graph Representation Learning** 引入了 GRL-Safety 多轴安全评估基准，评估了十二种图表示学习方法在部署压力下的可靠性，填补了图学习安全评估的空白。**LeakDojo: Decoding the Leakage Threats of RAG Systems** 作为 RAG 泄露的评估框架，基准化了六种现有攻击在十四种模型与不同 RAG 系统上的表现，揭示了查询生成与对抗注入的联合威胁。**Stego Battlefield: Evaluating Image Steganography Attacks and Steganalysis Defenses** 则提出了 SADBench，系统评估了通过隐写术注入有害秘密的能力及防御方的检测能力。

在开源工具方面，**Continuum-AI-Corp/OrcaRouter-Lite** 提供了带有管理安全网的自托管 LLM 路由工具，支持 BYOK 与流式处理，有助于在部署中实施流量控制。**kruschdev/krusch-context-mcp** 是一个统一的零信任 MCP 服务器，为 IDE Agent 提供本地语义代码库搜索与隔离的 episodic 项目记忆，增强了代码 Agent 的安全性。**Austin1serb/agents-md** 提出了 AGENTS.md 模式，旨在通过上下文工程提高代码 Agent 的安全性，包括命令输出安全与提示注入抵抗。这些工具与基准的发布，为社区提供了验证安全假设与部署防御措施的必要基础设施。

## Looking Forward

尽管今日研究在攻击检测、隐私保护与 Agent 治理方面取得了显著进展，但若干理论问题仍待解决。首先，**Stateful Agent Backdoor** 所揭示的跨会话攻击机制，目前缺乏通用的形式化防御模型，如何在不牺牲 Agent 长期记忆功能的前提下阻断状态化后门，是亟待攻克的难题。其次，**RLVR 隐式奖励过拟合** 与 **RL 稀疏策略选择** 的理论解释，暗示当前强化学习对齐方法可能存在根本性的局限性，未来需探索不依赖奖励过拟合的通用推理增强路径。最后，**Gaming the Metric** 与 **Evaluation-Context Divergence** 的研究表明，现有的安全评估基准可能无法真实反映部署行为，如何构建抗博弈、上下文无关的鲁棒评估协议，是 AI 治理领域面临的最大挑战。产业界在追求算力规模与融资速度的同时，需警惕将安全评估简化为合规指标，应回归对模型内在行为机制的深入理解。

---


## 参考来源

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
- **Why Global LLM Leaderboards Are Misleading: Small Portfolios for Heterogeneous Supervised ML** — [arxiv_lg](https://arxiv.org/abs/2605.06656v1)
- **PianoCoRe: Combined and Refined Piano MIDI Dataset** — [arxiv_lg](https://arxiv.org/abs/2605.06627v1)
- **Online Bayesian Calibration under Gradual and Abrupt System Changes** — [arxiv_lg](https://arxiv.org/abs/2605.06612v1)
- **SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** — [arxiv_lg](https://arxiv.org/abs/2605.06610v1)
- **CLAD: A Clustered Label-Agnostic Federated Learning Framework for Joint Anomaly Detection and Attack Classification** — [arxiv_lg](https://arxiv.org/abs/2605.06571v1)
- **BAMI: Training-Free Bias Mitigation in GUI Grounding** — [arxiv_ai](https://arxiv.org/abs/2605.06664v1)
- **Improved techniques for fine-tuning flow models via adjoint matching: a deterministic control pipeline** — [arxiv_ai](https://arxiv.org/abs/2605.06583v1)
- **Market-Alignment Risk in Pricing Agents: Trace Diagnostics and Trace-Prior RL under Hidden Competitor State** — [arxiv_ai](https://arxiv.org/abs/2605.06529v1)
- **From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features** — [arxiv_ai](https://arxiv.org/abs/2605.06494v1)
- **Patch-Effect Graph Kernels for LLM Interpretability** — [arxiv_ai](https://arxiv.org/abs/2605.06480v1)
- **Beyond Negative Rollouts: Positive-Only Policy Optimization with Implicit Negative Gradients** — [arxiv_cl](https://arxiv.org/abs/2605.06650v1)
- **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** — [arxiv_cl](https://arxiv.org/abs/2605.06635v1)
- **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** — [arxiv_cr](https://arxiv.org/abs/2605.06393v1)
- **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling: Tight Upper and Lower Bounds** — [arxiv_cr](https://arxiv.org/abs/2605.06259v1)
- **Profiling for Pennies: Unveiling the Privacy Iceberg of LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2605.06232v1)
- **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** — [arxiv_cr](https://arxiv.org/abs/2605.05928v1)
- **$α$-Wasserstein Mechanism for Rényi Pufferfish Privacy** — [arxiv_cr](https://arxiv.org/abs/2605.05723v1)
- **Evaluating the Reliability of Multiple Large Language Models in Risk Assessment: A CIS Controls Based Approach** — [arxiv_cr](https://arxiv.org/abs/2605.05424v1)
- **Autonomous Adversary: Red-Teaming in the age of LLM** — [arxiv_cr](https://arxiv.org/abs/2605.06486v1)
- **Hybrid Quantum-Classical GANs for the Generation of Adversarial Network Flows** — [arxiv_lg](https://arxiv.org/abs/2605.06629v1)
- **LiVeAction: a Lightweight, Versatile, and Asymmetric Neural Codec Design for Real-time Operation** — [arxiv_lg](https://arxiv.org/abs/2605.06628v1)
- **ReActor: Reinforcement Learning for Physics-Aware Motion Retargeting** — [arxiv_lg](https://arxiv.org/abs/2605.06593v1)
- **Distributionally-Robust Learning to Optimize** — [arxiv_lg](https://arxiv.org/abs/2605.06585v1)
- **SNAPO: Smooth Neural Adjoint Policy Optimization for Optimal Control via Differentiable Simulation** — [arxiv_lg](https://arxiv.org/abs/2605.06570v1)
- **Dynamic Treatment on Networks** — [arxiv_lg](https://arxiv.org/abs/2605.06564v1)
- **Sequential Design of Genetic Circuits Under Uncertainty With Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.06552v1)
- **Hedging Memory Horizons for Non-Stationary Prediction via Online Aggregation** — [arxiv_lg](https://arxiv.org/abs/2605.06541v1)
- **Diffusion-Based Posterior Sampling: A Feynman-Kac Analysis of Bias and Stability** — [arxiv_lg](https://arxiv.org/abs/2605.06538v1)
- **Verifier-Backed Hard Problem Generation for Mathematical Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.06660v1)
- **Are We Making Progress in Multimodal Domain Generalization? A Comprehensive Benchmark Study** — [arxiv_ai](https://arxiv.org/abs/2605.06643v1)
- **MASPO: Joint Prompt Optimization for LLM-based Multi-Agent Systems** — [arxiv_ai](https://arxiv.org/abs/2605.06623v1)
- **UniSD: Towards a Unified Self-Distillation Framework for Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2605.06597v1)
- **Cross-Modal Navigation with Multi-Agent Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.06595v1)
- **DINORANKCLIP: DINOv3 Distillation and Injection for Vision-Language Pretraining with High-Order Ranking Consistency** — [arxiv_ai](https://arxiv.org/abs/2605.06592v1)
- **Towards Metric-Faithful Neural Graph Matching** — [arxiv_ai](https://arxiv.org/abs/2605.06588v1)
- **Directional Consistency as a Complementary Optimization Signal: The GONO Framework** — [arxiv_ai](https://arxiv.org/abs/2605.06575v1)
- **Continuous Latent Diffusion Language Model** — [arxiv_ai](https://arxiv.org/abs/2605.06548v1)
- **On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** — [arxiv_ai](https://arxiv.org/abs/2605.06523v1)
- **Learning to Cut: Reinforcement Learning for Benders Decomposition** — [arxiv_ai](https://arxiv.org/abs/2605.06516v1)
- **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** — [arxiv_ai](https://arxiv.org/abs/2605.06505v1)
- **Operator-Guided Invariance Learning for Continuous Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.06500v1)
- **Instrumental Choices: Measuring the Propensity of LLM Agents to Pursue Instrumental Behaviors** — [arxiv_ai](https://arxiv.org/abs/2605.06490v1)
- **ReasonSTL: Bridging Natural Language and Signal Temporal Logic via Tool-Augmented Process-Rewarded Learning** — [arxiv_ai](https://arxiv.org/abs/2605.06483v1)
- **PairAlign: A Framework for Sequence Tokenization via Self-Alignment with Applications to Audio Tokenization** — [arxiv_cl](https://arxiv.org/abs/2605.06582v1)
- **STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?** — [arxiv_cl](https://arxiv.org/abs/2605.06527v1)
- **Invariant Features in Language Models: Geometric Characterization and Model Attribution** — [arxiv_cl](https://arxiv.org/abs/2605.06458v1)
- **Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** — [arxiv_cr](https://arxiv.org/abs/2605.06324v1)
- **Stateful Agent Backdoor** — [arxiv_cr](https://arxiv.org/abs/2605.06158v1)
- **Secure Seed-Based Multi-bit Watermarking for Diffusion Models from First Principles** — [arxiv_cr](https://arxiv.org/abs/2605.06153v1)
- **Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** — [arxiv_cr](https://arxiv.org/abs/2605.05995v1)
- **LeakDojo: Decoding the Leakage Threats of RAG Systems** — [arxiv_cr](https://arxiv.org/abs/2605.05818v1)
- **Stego Battlefield: Evaluating Image Steganography Attacks and Steganalysis Defenses** — [arxiv_cr](https://arxiv.org/abs/2605.05789v1)
- **Is Escalation Worth It? A Decision-Theoretic Characterization of LLM Cascades** — [arxiv_cl](https://arxiv.org/abs/2605.06350v1)
- **Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity** — [arxiv_cl](https://arxiv.org/abs/2605.06327v1)
- **Quantifying the Statistical Effect of Rubric Modifications on Human-Autorater Agreement** — [arxiv_cl](https://arxiv.org/abs/2605.06283v1)
- **Linear Semantic Segmentation for Low-Resource Spoken Dialects** — [arxiv_cl](https://arxiv.org/abs/2605.06276v1)
- **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** — [arxiv_cl](https://arxiv.org/abs/2605.06241v1)
- **Contrastive Identification and Generation in the Limit** — [arxiv_cl](https://arxiv.org/abs/2605.06211v1)
- **Inductive Venn-Abers and related regressors** — [arxiv_lg](https://arxiv.org/abs/2605.06646v1)
- **Edge-specific signal propagation on mature chromophore-region 3D mechanism graphs for fluorescent protein quantum-yield prediction** — [arxiv_lg](https://arxiv.org/abs/2605.06644v1)
- **Crafting Reversible SFT Behaviors in Large Language Models** — [arxiv_lg](https://arxiv.org/abs/2605.06632v1)
- **EMO: Pretraining Mixture of Experts for Emergent Modularity** — [arxiv_cl](https://arxiv.org/abs/2605.06663v1)
- **Parser agreement and disagreement in L2 Korean UD: Implications for human-in-the-loop annotation** — [arxiv_cl](https://arxiv.org/abs/2605.06625v1)
- **Algospeak, Hiding in the Open: The Trade-off Between Legible Meaning and Detection Avoidance** — [arxiv_cl](https://arxiv.org/abs/2605.06619v1)
- **Automated Clinical Report Generation for Remote Cognitive Remediation: Comparing Knowledge-Engineered Templates and LLMs in Low-Resource Settings** — [arxiv_cl](https://arxiv.org/abs/2605.06594v1)
- **Long Context Pre-Training with Lighthouse Attention** — [arxiv_cl](https://arxiv.org/abs/2605.06554v1)
- **Efficient Pre-Training with Token Superposition** — [arxiv_cl](https://arxiv.org/abs/2605.06546v1)
- **The Frequency Confound in Language-Model Surprisal and Metaphor Novelty** — [arxiv_cl](https://arxiv.org/abs/2605.06506v1)
- **Cubit: Token Mixer with Kernel Ridge Regression** — [arxiv_cl](https://arxiv.org/abs/2605.06501v1)
- **Towards Emotion Consistency Analysis of Large Language Models in Emotional Conversational Contexts** — [arxiv_cl](https://arxiv.org/abs/2605.06476v1)
- **Musk v. Altman week 2: OpenAI fires back, and Shivon Zilis reveals that Musk tried to poach Sam Altman** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1137008/musk-v-altman-week-2-openai-fires-back-and-shivon-zilis-reveals-that-musk-tried-to-poach-sam-altman/)
- **All the latest updates on AI data centers** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/902546/data-centers-ai-energy-power-grids-controversy)
- **Cloudflare says AI made 1,100 jobs obsolete, even as revenue hit a record high** — [techcrunch_ai](https://techcrunch.com/2026/05/08/cloudflare-says-ai-made-1100-jobs-obsolete-even-as-revenue-hit-a-record-high/)
- **Here’s what you need to know about the cruise ship hantavirus outbreak** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136988/heres-what-you-need-to-know-about-the-cruise-ship-hantavirus-outbreak/)
- **PlayStation sees AI as a ‘powerful tool’ to help make games** — [theverge_ai](https://www.theverge.com/games/926914/sony-playstation-ai-powerful-tool-games)
- **Microsoft was worried OpenAI would run off to Amazon and ‘shit-talk’ Azure** — [theverge_ai](https://www.theverge.com/report/926771/microsoft-openai-amazon-worries-shit-talk-azure)
- **The “people’s airline” and the enterprise AI gold rush** — [techcrunch_ai](https://techcrunch.com/podcast/the-peoples-airline-and-the-enterprise-ai-gold-rush/)
- **Everybody wants to rule the AI world** — [theverge_ai](https://www.theverge.com/podcast/926707/openai-ceo-murati-musk-trial-vergecast)
- **Last 24 hours to get 50% off a second pass to TechCrunch Disrupt 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/08/last-24-hours-to-get-50-off-a-second-pass-to-techcrunch-disrupt-2026/)
- **Running Codex safely at OpenAI** — [openai](https://openai.com/index/running-codex-safely)
- **The Download: AI malaise and babymaking tech** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136985/the-download-ai-malaise-babymaking-ivf-tech/)
- **Nanoleaf bets its future on robots, red light therapy, and AI** — [theverge_ai](https://www.theverge.com/tech/926342/nanoleaf-smart-lighting-ai-robotics-red-light-wellness)
- **Here’s how technology transformed babymaking** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136974/heres-how-technology-transformed-babymaking-ivf/)
- **The fax machine is the bottleneck in US healthcare, and VCs are starting to notice** — [techcrunch_ai](https://techcrunch.com/2026/05/07/the-back-office-problem-that-explains-why-specialists-never-call-you-back/)
- **Laid-off Oracle workers tried to negotiate better severance. Oracle said no.** — [techcrunch_ai](https://techcrunch.com/2026/05/08/laid-off-oracle-workers-tried-to-negotiate-better-severance-oracle-said-no/)
- **Intel’s comeback story is even wilder than it seems** — [techcrunch_ai](https://techcrunch.com/2026/05/08/intels-comeback-story-is-even-wilder-than-it-seems/)
- **See what happens when creative legends use AI to make ads for small businesses.** — [google_ai](https://blog.google/company-news/inside-google/company-announcements/the-small-brief/)
- **Continuum-AI-Corp/OrcaRouter-Lite** — [github](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)
- **cenconq25/claude-code-app-studio** — [github](https://github.com/cenconq25/claude-code-app-studio)
- **Negai-ai/AgentClaw** — [github](https://github.com/Negai-ai/AgentClaw)
- **kruschdev/krusch-context-mcp** — [github](https://github.com/kruschdev/krusch-context-mcp)
- **shawn0728/OpenSearch-VL** — [github](https://github.com/shawn0728/OpenSearch-VL)
- **awizemann/harness** — [github](https://github.com/awizemann/harness)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **sanieldoe/companions** — [github](https://github.com/sanieldoe/companions)
- **tianji-qingtian/AI-Native** — [github](https://github.com/tianji-qingtian/AI-Native)
- **alterhq/openpets** — [github](https://github.com/alterhq/openpets)
- **byliutao/CDM** — [github](https://github.com/byliutao/CDM)
- **usewhale/whale** — [github](https://github.com/usewhale/whale)
- **Austin1serb/agents-md** — [github](https://github.com/Austin1serb/agents-md)
- **Jason-Cyr/ai-shared-brain** — [github](https://github.com/Jason-Cyr/ai-shared-brain)
- **Autoloops/upskill** — [github](https://github.com/Autoloops/upskill)
- **ZhongKuang/TAAC2026-CLI** — [github](https://github.com/ZhongKuang/TAAC2026-CLI)
- **梁文锋出资200亿！DeepSeek首轮创纪录融资500亿，V4.1定档6月** — [qbitai](https://www.qbitai.com/2026/05/414432.html)
- **持续领跑！商汤大装置稳居中国MaaS市场第一梯队** — [qbitai](https://www.qbitai.com/2026/05/414428.html)
- **Redis之父下场，给DeepSeek V4单独造了一台推理引擎** — [qbitai](https://www.qbitai.com/2026/05/414316.html)
- **Anthropic出手！AI的内心独白，曝光了** — [qbitai](https://www.qbitai.com/2026/05/414213.html)
- **GPT-5级推理能力塞进语音模型，OpenAI把同传翻译成本砍穿地板价** — [qbitai](https://www.qbitai.com/2026/05/414194.html)
- **特斯拉百万年薪招数据标注员，朝九晚五，无需AI经验** — [qbitai](https://www.qbitai.com/2026/05/414156.html)
- **所有实验室都怕字节，所有人都在夸DeepSeek！美国研究员36小时中国AI行** — [qbitai](https://www.qbitai.com/2026/05/414141.html)
- **第一批「AI原生」本科生，要毕业了** — [qbitai](https://www.qbitai.com/2026/05/414125.html)
- **AI开始接管年轻人的「精神自留地」** — [36kr](https://36kr.com/p/3801461350702855?f=rss)
- **需求持续升温，AI芯片制造商Cerebras拟上调IPO价格区间** — [36kr](https://36kr.com/newsflashes/3801408298065416?f=rss)
- **新三板梯度培育体系完善，挂牌企业踊跃筹备北交所IPO** — [36kr](https://36kr.com/newsflashes/3801400639462914?f=rss)
- **36氪首发 | 航空航天电气系统互联组件方案商获数千万融资，细分赛道市占率第一** — [36kr](https://36kr.com/p/3801398177324550?f=rss)
- **获高秉强、蓝驰领投数千万融资，浙大00后创业者从远景观测切入AI智能影像｜硬氪首发** — [36kr](https://36kr.com/p/3797202414820359?f=rss)
- **美股三大指数集体收盘涨，英特尔涨超13%** — [36kr](https://36kr.com/newsflashes/3801342492040709?f=rss)
- **9点1氪丨DeepSeek拟募资最高500亿；“全国销冠”被刑拘，泰康人寿回应；OPPO就母亲节文案致歉** — [36kr](https://36kr.com/p/3801348046151428?f=rss)
- **「维新宇航」完成数千万元天使+轮融资，7座3吨级eVTOL将于7月进行首飞测试｜36氪首发** — [36kr](https://36kr.com/p/3800495686163721?f=rss)
- **卡位黄金价格带，问界M6向下争夺年轻群体｜最前线** — [36kr](https://36kr.com/p/3800183520091398?f=rss)
- **小红书四年AI 路：FOMO、犹豫，到突然加速** — [36kr](https://36kr.com/p/3799028783439111?f=rss)
- **“星识科技”连续完成天使+轮和天使++轮融资，累计金额达数千万元** — [36kr](https://36kr.com/newsflashes/3801420917071366?f=rss)
- **Anthropic据悉同Akamai签署18亿美元计算协议** — [36kr](https://36kr.com/newsflashes/3801405713374981?f=rss)
- **谷歌旗下Isomorphic Labs拟在新一轮融资中筹集逾20亿美元** — [36kr](https://36kr.com/newsflashes/3801377962090247?f=rss)
- **阿波罗和黑石等机构考虑参与博通近350亿美元融资** — [36kr](https://36kr.com/newsflashes/3801359034113538?f=rss)
- **英特尔与苹果据悉达成初步协议，将为后者设备制造芯片** — [36kr](https://36kr.com/newsflashes/3801360095289088?f=rss)
- **亚马逊北弗吉尼亚数据中心云服务中断问题已基本解决** — [36kr](https://36kr.com/newsflashes/3800643618249730?f=rss)
- **高盛：美国数据中心用电需求或在两年内翻倍** — [36kr](https://36kr.com/newsflashes/3800643284245513?f=rss)
- **热门中概股美股盘前多数上涨，百度涨超5%** — [36kr](https://36kr.com/newsflashes/3800639633415424?f=rss)
- **美股大型科技股盘前多数上涨，英伟达涨超1%** — [36kr](https://36kr.com/newsflashes/3800638528986369?f=rss)