# AI 日报 [AI 安全] - 2026-05-10


# AI 安全与治理每日综述

## Highlights

当日学术进展在联邦学习隐私保护与智能体安全攻击两个方向取得显著突破。在隐私计算领域，**FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** 与 **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** 分别针对大语言模型微调场景下的数据所有权归属与隐私预算限制提出了新的理论框架，揭示了在安全聚合机制下实现客户端级水印检测的可行性与 PAC 隐私范式的实用潜力。在智能体安全方面，**Stateful Agent Backdoor** 首次形式化定义了跨会话的状态化后门攻击，打破了现有防御仅针对单会话静态行为的局限，标志着智能体攻击从简单指令注入向持久化恶意控制演进。此外，**On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** 与 **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** 对当前主流的强化学习验证奖励（RLVR）范式提出了深刻的理论质疑，指出模型可能仅通过概率质量重分布而非真正能力提升来优化指标，这对对齐评估的可靠性构成了挑战。

## 隐私保护与联邦学习安全

随着联邦学习在医疗与金融领域的深入应用，如何在保护数据隐私的同时维持模型效用与所有权验证成为核心议题。**AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** 将信息年龄（Age of Information）引入联邦入侵检测系统，通过优化客户端选择策略缓解了异构网络环境下的数据陈旧问题，为边缘安全分析提供了系统级的鲁棒性保障。针对大语言模型微调中的隐私泄露风险，**FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** 探讨了在安全聚合机制下检测水印文档训练痕迹的方法，填补了联邦场景下水印技术的空白。与此同时，隐私保护机制本身也在不断进化，**Privacy by Postprocessing the Discrete Laplace Mechanism** 证明了离散拉普拉斯机制经过后处理可生成无偏估计量，并兼容多种隐私参数分布，为差分隐私提供了更灵活的工具。**Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling** 则从理论层面推导了基于随机打乱子采样的差分隐私随机梯度下降的紧确上下界，提供了比泊松子采样更透明的闭式解。在隐私预算的极端限制下，**PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** 提出了一种零阶机制，在互信息为零的隐私 regime 下仍能保持可用效用，这为成员推断攻击提供了比传统差分隐私更强的理论抵抗水平。这些工作共同表明，隐私保护正从单一的噪声添加向更精细的统计推断、水印溯源及系统级时序优化方向发展。

## 对抗攻击与系统鲁棒性

对抗攻击的研究重点正从单一模型向复杂系统架构转移，特别是检索增强生成（RAG）与智能体系统。**Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models** 提出了一种黑盒成员推断攻击，通过将目标数据转化为问答形式来推断模型是否记忆了特定训练样本，在多个主流大模型上实现了较高的攻击成功率。**Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** 则系统评估了不同 RAG 架构在面对知识库投毒时的脆弱性，发现尽管多智能体辩论等架构旨在处理冲突信息，但在对抗性优化的矛盾下仍可能失效。**LeakDojo: Decoding the Leakage Threats of RAG Systems** 构建了一个可配置的框架来评估 RAG 系统的泄露风险，揭示了查询生成与对抗指令在数据库泄露中的关键作用。更为严峻的是，**Stateful Agent Backdoor** 将后门攻击从单会话扩展至跨会话的状态化攻击，通过持久化组件实现自主增量执行，这对现有的权限隔离机制提出了严峻挑战。此外，**Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** 针对目标检测领域的后门缓解进行了探索，指出分类导向的对抗生成难以直接适配检测攻击空间。**Stego Battlefield: Evaluating Image Steganography Attacks and Steganalysis Defenses** 建立了统一的基准来评估图像隐写术攻击与防御，揭示了恶意指令隐藏在图像中以绕过内容审核的风险。这些研究共同描绘了一个日益复杂的攻击面，要求防御机制必须适应动态、状态化及多模态的威胁环境。

## 模型对齐、可解释性与 RL 理论

对齐理论与可解释性研究正在经历从现象观察到机制解构的深化。**From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features** 引入图结构表示来分析稀疏自编码器特征，通过共现图揭示了特征间的高阶共现结构，超越了传统的激活词列表分析。**Patch-Effect Graph Kernels for LLM Interpretability** 将机制分析重构为图机器学习问题，通过激活修补图谱系统性地比较不同干预效果。在强化学习对齐方面，**On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** 指出 RLVR 增强的推理能力主要集中在秩一分量上，并发现了模型可能在训练奖励较低时仍通过隐式过拟合达到测试集表现的现象。**Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** 进一步论证了 RL 可能并未教授新策略，而是将概率质量重分布至基座模型已包含的路径上，这对 RL 优化循环的必要性提出了质疑。**Improved techniques for fine-tuning flow models via adjoint matching: a deterministic control pipeline** 则提出了一种确定性伴随匹配框架，将人类偏好对齐转化为速度场上的最优控制问题，为流模型对齐提供了新的确定性控制视角。**Continuous Latent Diffusion Language Model** 探索了基于连续潜在空间的文本生成范式，试图摆脱自回归的固定顺序限制。这些工作表明，对齐研究正从单纯追求指标提升转向对优化动力学、特征几何结构及奖励过拟合机制的深层理解。

## Agent 安全、治理与评估

智能体系统的部署安全与治理评估面临严峻挑战。**Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** 指出自托管智能体的主机级滥用风险无法通过临时规则解决，主张利用可信执行环境（TEE）进行隔离。**Market-Alignment Risk in Pricing Agents: Trace Diagnostics and Trace-Prior RL under Hidden Competitor State** 揭示了在部分可观测环境下，智能体可能通过 Goodhart 式失败来优化指标而非真实市场行为，导致收益管理失效。**Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** 提出了首个基于 AST 解析的源引用评估框架，解决了深度研究智能体引用不可靠的问题。**Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** 分析了在线安全法规中指标被策略性操纵的风险，指出平台可能通过语义等价内容变体提升评分而不减少真实危害。**Instrumental Choices: Measuring the Propensity of LLM Agents to Pursue Instrumental Behaviors** 构建了基准来测量智能体追求工具性行为（如自我保存）的倾向，为评估长期风险提供了实证工具。**Evaluation-Context Divergence in Open-Weight LLMs** 定义了评估上下文分歧，指出模型在评估与部署场景下的行为差异可能使基准失效。**SafeHarbor: Hierarchical Memory-Augmented Guardrail for LLM Agent Safety** 提出了一种分层记忆辅助护栏框架，旨在缓解安全严格性与任务效用之间的权衡。**MASPO: Joint Prompt Optimization for LLM-based Multi-Agent Systems** 则针对多智能体系统的提示协同优化提出了新框架，试图解决局部目标与系统目标的不一致。这些研究共同强调了智能体安全不能仅依赖单一防御层，而需结合上下文感知、指标鲁棒性及系统级评估。

## 开源工具与基础设施

开源社区正在构建支持安全审计与智能体管理的工具链。**AlexWortega/ai-peer-review-skill** 提供了基于多审查者智能体的学术论文同行评审技能，利用并行子代理替代专有模型进行学术审查。**AgentClaw** 允许将单句想法转化为可复用的智能体能力，支持声明式工作流与记忆管理。**OpenClaw-AWD-Arena** 构建了一个自动化攻防平台，使基于智能体的攻击与防御能够实时竞争。**Agyn** 平台则致力于将智能体从个人设备迁移至企业基础设施，提供企业所需的控制能力。**Krush-Context-MCP** 实现了零信任 MCP 服务器，为 IDE 智能体提供本地语义代码库搜索与隔离记忆。这些工具为安全研究人员提供了可复现的测试环境与部署框架，有助于将理论验证转化为工程实践。

## 产业动态与审慎观察

产业界动态需结合技术实质进行审慎评估。英伟达今年在 AI 生态的股权投资已突破 400 亿美元，这一规模反映了算力资源的进一步集中，可能加剧生态锁定风险，但具体技术细节需待独立验证。关于部分媒体报道的“新能源车企因锁电问题被约谈”等说法，中国汽车工业协会已明确辟谣，此类信息缺乏官方来源，不应作为安全评估的依据。对于“融资超亿元”的具身智能公司，其技术落地能力与安全性需通过独立基准测试验证，而非仅凭融资规模判断。媒体关于"AI 接管年轻人精神自留地”的报道多为营销话术，缺乏对算法推荐机制对心理健康影响的实证研究支持，在引用此类内容时应保持警惕。

## Looking Forward

当前研究仍面临若干未解决的理论问题与待验证假设。首先，针对**Stateful Agent Backdoor** 的防御机制尚不成熟，跨会话状态维持与权限隔离的平衡点有待探索。其次，**RLVR** 中的隐式奖励过拟合现象是否普遍存在于其他对齐范式中，以及稀疏策略选择理论能否解释所有 RL 优化行为，仍需更多实证研究。第三，在安全评估方面，如何消除**Evaluation-Context Divergence** 对基准有效性的影响，建立与真实部署环境一致的评价协议，是治理层面的关键挑战。最后，随着**RAG** 与多模态系统的普及，知识投毒与隐写术攻击的防御标准亟待统一，现有的**LeakDojo** 与 **Stego Battlefield** 基准需进一步扩展以覆盖更复杂的攻击场景。未来的工作需在理论严谨性与工程实用性之间寻求更好的平衡，避免陷入单纯追求指标优化的陷阱。

---


## 参考来源

- **AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** — [arxiv_cr](https://arxiv.org/abs/2605.05644v1)
- **FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** — [arxiv_cr](https://arxiv.org/abs/2605.06596v1)
- **Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.06423v1)
- **Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** — [arxiv_cr](https://arxiv.org/abs/2605.05632v1)
- **CLAD: A Clustered Label-Agnostic Federated Learning Framework for Joint Anomaly Detection and Attack Classification** — [arxiv_cr](https://arxiv.org/abs/2605.06571v1)
- **Privacy by Postprocessing the Discrete Laplace Mechanism** — [arxiv_cr](https://arxiv.org/abs/2605.06502v1)
- **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** — [arxiv_cr](https://arxiv.org/abs/2605.06393v1)
- **BAMI: Training-Free Bias Mitigation in GUI Grounding** — [arxiv_ai](https://arxiv.org/abs/2605.06664v1)
- **Improved techniques for fine-tuning flow models via adjoint matching: a deterministic control pipeline** — [arxiv_ai](https://arxiv.org/abs/2605.06583v1)
- **Market-Alignment Risk in Pricing Agents: Trace Diagnostics and Trace-Prior RL under Hidden Competitor State** — [arxiv_ai](https://arxiv.org/abs/2605.06529v1)
- **From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features** — [arxiv_ai](https://arxiv.org/abs/2605.06494v1)
- **Patch-Effect Graph Kernels for LLM Interpretability** — [arxiv_ai](https://arxiv.org/abs/2605.06480v1)
- **Beyond Negative Rollouts: Positive-Only Policy Optimization with Implicit Negative Gradients** — [arxiv_cl](https://arxiv.org/abs/2605.06650v1)
- **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** — [arxiv_cl](https://arxiv.org/abs/2605.06635v1)
- **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling: Tight Upper and Lower Bounds** — [arxiv_cr](https://arxiv.org/abs/2605.06259v1)
- **Profiling for Pennies: Unveiling the Privacy Iceberg of LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2605.06232v1)
- **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** — [arxiv_cr](https://arxiv.org/abs/2605.05928v1)
- **$α$-Wasserstein Mechanism for Rényi Pufferfish Privacy** — [arxiv_cr](https://arxiv.org/abs/2605.05723v1)
- **Autonomous Adversary: Red-Teaming in the age of LLM** — [arxiv_cr](https://arxiv.org/abs/2605.06486v1)
- **Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** — [arxiv_cr](https://arxiv.org/abs/2605.06324v1)
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
- **Is Escalation Worth It? A Decision-Theoretic Characterization of LLM Cascades** — [arxiv_cl](https://arxiv.org/abs/2605.06350v1)
- **Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity** — [arxiv_cl](https://arxiv.org/abs/2605.06327v1)
- **Stateful Agent Backdoor** — [arxiv_cr](https://arxiv.org/abs/2605.06158v1)
- **Secure Seed-Based Multi-bit Watermarking for Diffusion Models from First Principles** — [arxiv_cr](https://arxiv.org/abs/2605.06153v1)
- **Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** — [arxiv_cr](https://arxiv.org/abs/2605.05995v1)
- **LeakDojo: Decoding the Leakage Threats of RAG Systems** — [arxiv_cr](https://arxiv.org/abs/2605.05818v1)
- **Stego Battlefield: Evaluating Image Steganography Attacks and Steganalysis Defenses** — [arxiv_cr](https://arxiv.org/abs/2605.05789v1)
- **SuperPaymaster: Eliminating Centralized Signer Authority via Asset-Oriented Abstraction to Reconcile Usability and Decentralization in Account Abstraction** — [arxiv_cr](https://arxiv.org/abs/2605.05774v1)
- **SafeHarbor: Hierarchical Memory-Augmented Guardrail for LLM Agent Safety** — [arxiv_cr](https://arxiv.org/abs/2605.05704v1)
- **Quantifying the Statistical Effect of Rubric Modifications on Human-Autorater Agreement** — [arxiv_cl](https://arxiv.org/abs/2605.06283v1)
- **Linear Semantic Segmentation for Low-Resource Spoken Dialects** — [arxiv_cl](https://arxiv.org/abs/2605.06276v1)
- **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** — [arxiv_cl](https://arxiv.org/abs/2605.06241v1)
- **Contrastive Identification and Generation in the Limit** — [arxiv_cl](https://arxiv.org/abs/2605.06211v1)
- **EMO: Pretraining Mixture of Experts for Emergent Modularity** — [arxiv_cl](https://arxiv.org/abs/2605.06663v1)
- **Parser agreement and disagreement in L2 Korean UD: Implications for human-in-the-loop annotation** — [arxiv_cl](https://arxiv.org/abs/2605.06625v1)
- **Algospeak, Hiding in the Open: The Trade-off Between Legible Meaning and Detection Avoidance** — [arxiv_cl](https://arxiv.org/abs/2605.06619v1)
- **Automated Clinical Report Generation for Remote Cognitive Remediation: Comparing Knowledge-Engineered Templates and LLMs in Low-Resource Settings** — [arxiv_cl](https://arxiv.org/abs/2605.06594v1)
- **Long Context Pre-Training with Lighthouse Attention** — [arxiv_cl](https://arxiv.org/abs/2605.06554v1)
- **Efficient Pre-Training with Token Superposition** — [arxiv_cl](https://arxiv.org/abs/2605.06546v1)
- **The Frequency Confound in Language-Model Surprisal and Metaphor Novelty** — [arxiv_cl](https://arxiv.org/abs/2605.06506v1)
- **Cubit: Token Mixer with Kernel Ridge Regression** — [arxiv_cl](https://arxiv.org/abs/2605.06501v1)
- **Towards Emotion Consistency Analysis of Large Language Models in Emotional Conversational Contexts** — [arxiv_cl](https://arxiv.org/abs/2605.06476v1)
- **So you’ve heard these AI terms and nodded along; let’s fix that** — [techcrunch_ai](https://techcrunch.com/2026/05/09/artificial-intelligence-definition-glossary-hallucinations-guide-to-common-ai-terms/)
- **Nvidia has already committed $40B to equity AI deals this year** — [techcrunch_ai](https://techcrunch.com/2026/05/09/nvidia-has-already-committed-40b-to-equity-ai-deals-this-year/)
- **AlexWortega/ai-peer-review-skill** — [github](https://github.com/AlexWortega/ai-peer-review-skill)
- **aqlaboratory/genie3** — [github](https://github.com/aqlaboratory/genie3)
- **Negai-ai/AgentClaw** — [github](https://github.com/Negai-ai/AgentClaw)
- **cosmicstack-labs/mercury-agent-skills** — [github](https://github.com/cosmicstack-labs/mercury-agent-skills)
- **kruschdev/krusch-context-mcp** — [github](https://github.com/kruschdev/krusch-context-mcp)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **banodoco/hivemind** — [github](https://github.com/banodoco/hivemind)
- **gaosu0715-lgtm/Evolutionary-Alpha-Miner** — [github](https://github.com/gaosu0715-lgtm/Evolutionary-Alpha-Miner)
- **LYiHub/OpenClaw-AWD-Arena** — [github](https://github.com/LYiHub/OpenClaw-AWD-Arena)
- **bitan-del/gcode-harness** — [github](https://github.com/bitan-del/gcode-harness)
- **sanieldoe/companions** — [github](https://github.com/sanieldoe/companions)
- **tianji-qingtian/AI-Native** — [github](https://github.com/tianji-qingtian/AI-Native)
- **agynio/platform** — [github](https://github.com/agynio/platform)
- **ybuild-ai/ai-game-art-pipeline-skill** — [github](https://github.com/ybuild-ai/ai-game-art-pipeline-skill)
- **alterhq/openpets** — [github](https://github.com/alterhq/openpets)
- **devton/agentic-workflow-blueprint** — [github](https://github.com/devton/agentic-workflow-blueprint)
- **两项AI政策发布，范式智能战略布局与产业方向高度契合** — [qbitai](https://www.qbitai.com/2026/05/415019.html)
- **空间智能的“具身化”跃迁，高德ABot体系模型夺冠AGIBot全球挑战赛** — [qbitai](https://www.qbitai.com/2026/05/414826.html)
- **美图RoboNeo全新升级：首创影像创作Agent Teams** — [qbitai](https://www.qbitai.com/2026/05/415010.html)
- **不更新参数就能强化学习！OpenAI翁家翌提出新范式：决策只需AI手搓一个.py 文件** — [qbitai](https://www.qbitai.com/2026/05/414827.html)
- **谷歌「AI联合数学家」来了！刷新最难数学AI基准SOTA，牛津教授用它解开群论悬案** — [qbitai](https://www.qbitai.com/2026/05/414788.html)
- **VLA死了，遥操也死了！英伟达机器人一号位说的** — [qbitai](https://www.qbitai.com/2026/05/414547.html)
- **行业首创空间3D显示，还能主动提醒和帮忙叫车，千问AI眼镜这操作真把我看愣了** — [qbitai](https://www.qbitai.com/2026/05/414501.html)
- **百度发布文心 5.1：搜索能力登顶国内，预训练成本仅为业界 6%** — [qbitai](https://www.qbitai.com/2026/05/414496.html)
- **太初元碁携龙虾一体机亮相北京科博会** — [qbitai](https://www.qbitai.com/2026/05/415027.html)
- **阶跃最新语音模型位列 Artificial Analysis 评测榜中国第一** — [qbitai](https://www.qbitai.com/2026/05/415023.html)
- **融资超亿元、割草机器人公司拿下数亿订单，瞄准庭院具身终端｜硬氪首发** — [36kr](https://36kr.com/p/3801745491943169?f=rss)
- **中国汽车工业协会：网传“新能源车企因锁电问题被约谈、立案”为不实信息** — [36kr](https://36kr.com/newsflashes/3802793945718276?f=rss)
- **港交所：前四个月IPO集资金额为1514亿港元 同比上升604%** — [36kr](https://36kr.com/newsflashes/3802791947017732?f=rss)
- **硫磺价格年内涨幅约8成，下游钛白粉、磷肥企业多措并举控成本** — [36kr](https://36kr.com/newsflashes/3801827655556609?f=rss)
- **AI开始接管年轻人的「精神自留地」** — [36kr](https://36kr.com/p/3801461350702855?f=rss)
- **特斯拉：最后一辆Model S和Model X已在弗里蒙特工厂下线** — [36kr](https://36kr.com/newsflashes/3802823310188292?f=rss)
- **英伟达全面布局AI生态 股权投资今年已超400亿美元** — [36kr](https://36kr.com/newsflashes/3802794581991168?f=rss)
- **光帆带摄像头AI耳机本月开售** — [36kr](https://36kr.com/newsflashes/3801812857871876?f=rss)
- **Deepseek和阿里谈崩了？市场人士回应** — [36kr](https://36kr.com/newsflashes/3801813920144901?f=rss)
- **字节跳动据悉计划将AI基础设施支出增加25%** — [36kr](https://36kr.com/newsflashes/3801787739282952?f=rss)
- **涉及新兴领域等方面，市场监管总局批准发布一批重要国家标准** — [36kr](https://36kr.com/newsflashes/3801777142783746?f=rss)