# AI Daily Digest [AI 安全] - 2026-05-10


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-05-10
**Author:** Senior AI Safety Researcher

## Highlights

Three significant academic developments dominate today’s landscape, signaling a shift from static security models to dynamic, state-aware defenses and a re-evaluation of reinforcement learning mechanisms. First, the introduction of **PACZero** represents a paradigm shift in privacy-preserving fine-tuning, achieving a regime where membership-inference attack posterior success rates match the prior without the infinite noise penalty typically associated with differential privacy. Second, the emergence of **Stateful Agent Backdoor** attacks challenges the assumption that agent security can be contained within single-session boundaries, demonstrating how persistent state components can enable autonomous, incremental execution across sessions. Finally, empirical analysis in **On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** suggests that Reinforcement Learning with Verifiable Rewards may primarily redistribute probability mass over existing capabilities rather than teaching new strategies, raising critical questions about the efficiency and necessity of current RL optimization loops.

## Privacy-Preserving Learning and Federated Systems

The intersection of privacy and federated learning continues to evolve beyond standard differential privacy (DP) guarantees, with recent work addressing the specific constraints of distributed security analytics and large language model fine-tuning. In the domain of cloud-edge security, **AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** reframes client participation as a timeliness-aware systems problem. By utilizing Age of Information (AoI), the authors propose lightweight policies that balance utility with the freshness of client data, addressing the straggler and dropout issues that often compromise the reliability of intrusion detection systems. This complements broader efforts to secure the aggregation process itself, such as **FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning**, which adapts watermark radioactivity testing to the federated setting. While existing watermarking methods rely on centralized fine-tuning, FedAttr navigates the challenges posed by secure aggregation (SA), ensuring data ownership protection without compromising the privacy guarantees of the FL protocol.

Theoretical advances in privacy mechanisms are also gaining traction, moving towards more versatile and transparent bounds. **Privacy by Postprocessing the Discrete Laplace Mechanism** demonstrates that the classical discrete Laplace mechanism can be post-processed to yield unbiased estimators of subexponential functions or to output distributions matching the Laplace or Staircase mechanisms with identical privacy parameters. This versatility suggests that older mechanisms may offer new utility in modern pipelines without requiring complex new noise distributions. Similarly, **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling** provides a tight analysis of the trade-off function for DP-SGD under random shuffling. Unlike Poisson subsampling analyses which yield non-closed implicit formulas, this work derives transparent closed-form bounds, offering clearer interpretability for practitioners configuring privacy budgets. These theoretical refinements are critical when combined with practical frameworks like **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization**, which introduces a zeroth-order mechanism delivering usable utility at zero mutual information. The authors report that PACZero bounds the membership-inference attack posterior success rate at the prior, a level of resistance that the DP framework matches only at $\varepsilon=0$ and infinite noise. This convergence of PAC privacy and sign quantization offers a promising avenue for fine-tuning without the utility degradation typical of high-privacy DP settings.

## Adversarial Security and Agent Safety

Security research is increasingly focusing on the dynamic behaviors of agents and the structural vulnerabilities of Retrieval-Augmented Generation (RAG) systems. A critical vulnerability identified in **Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** is that architectures designed to handle conflicting retrieved information—such as multi-agent debate or agentic retrieval—remain untested against adversarially optimized contradictions. The authors evaluate four RAG architectures under controlled single-document poisoning and find that defenses against vanilla pipelines do not necessarily generalize to more complex retrieval strategies. This finding is corroborated by **LeakDojo: Decoding the Leakage Threats of RAG Systems**, a configurable framework that benchmarks six existing attacks across fourteen LLMs. The study reveals that query generation and adversarial instruction following remain primary vectors for database leakage, suggesting that current RAG defenses are insufficient against sophisticated prompt engineering.

The threat landscape for agents is becoming more sophisticated, moving from stateless to stateful attacks. **Stateful Agent Backdoor** proposes an attack lifecycle that extends across multiple sessions under permission isolation. By modeling the attack as a Mealy machine, the authors derive a decomposition framework that enables independent per-transition data construction, allowing for autonomous, incremental execution following a one-time trigger injection. This contrasts sharply with existing backdoor attacks which remain confined to single sessions. To counter such risks, **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** argues that ad hoc blocking rules are insufficient for self-hosted computer-use agents (SHCUAs). The authors propose Trusted Execution Environment (TEE)-backed isolation to prevent host-level abuse surfaces, such as indirect prompt injection or unsafe skills, from compromising the host system.

Defenses against backdoors in vision systems are also being refined. **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** highlights that classification-oriented adversarial generation does not match the detection attack space, where attacks may cause object misclassification or disappearance. The authors adapt adversarial fine-tuning to address these specific detection vulnerabilities. Furthermore, **Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** traces the failure of existing parameter constraints to the inherent redundancy of high-dimensional parameter space. The authors propose Safety Bottleneck Regularization to prevent attackers from exploiting optimization trajectories orthogonal to defense constraints. These geometric approaches are complemented by **Stego Battlefield: Evaluating Image Steganography Attacks and Steganalysis Defenses**, which introduces SADBench to assess the adversary's ability to inject harmful secrets via steganography. This highlights the need for unified evaluation frameworks that cover both text-based and image-based covert channels.

## Alignment Theory and Interpretability

Recent theoretical work challenges the prevailing assumptions regarding how large language models acquire reasoning capabilities and how their internal representations can be interpreted. A significant contribution comes from **On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR**, which characterizes the dynamics of Reinforcement Learning with Verifiable Rewards (RLVR). The authors identify that enhanced reasoning capabilities are concentrated within rank-1 components and observe that models can achieve satisfactory test performance even with relatively low training rewards, suggesting implicit reward overfitting. This aligns with findings in **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning**, which argues that RL does not teach new strategies but rather redistributes probability mass over solutions the base model already contains. The authors find that RL's beneficial footprint is a sparse, predictable correction concentrated at high-entropy decision points.

Interpretability research is also moving towards graph-structured representations to capture higher-order co-occurrence structures. **From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features** introduces a graph-structured representation where each Sparse Autoencoder (SAE) feature is modeled as a token co-occurrence graph. This allows for the examination of co-occurrence structure shared across features, which is largely unexamined in existing analyses that rely on top-activating token lists. Similarly, **Patch-Effect Graph Kernels for LLM Interpretability** reframes mechanistic analysis as a graph machine-learning problem by representing activation-patching profiles as patch-effect graphs. These graph-based methods offer a systematic way to compare intervention results across diverse prompts and task families, addressing the high-dimensional, unstructured datasets produced by scaling activation patching.

In terms of alignment optimization, **Improved techniques for fine-tuning flow models via adjoint matching: a deterministic control pipeline** formulates human preference alignment for flow-based generative models as an optimal control problem over velocity fields. This deterministic adjoint matching framework allows for direct regression of the control toward a value-gradient-induced target, leading to a simple and stable training objective. Meanwhile, **Positive-Only Policy Optimization with Implicit Negative Gradients** critiques the reliance on negative rollouts in Group Relative Policy Optimization (GRPO), noting that negative rollouts may admit no gradation of failure severity. The authors propose a positive-only approach that leverages implicit negative gradients to improve efficiency. These optimization advances are contextualized by **Instrumental Choices: Measuring the Propensity of LLM Agents to Pursue Instrumental Behaviors**, which introduces a benchmark for measuring model propensity for instrumental convergence (IC) behavior in terminal-based agents. This benchmark provides a realistic, low-stakes method to evaluate behaviors such as self-preservation, which have been hypothesized to play a key role in risks from highly capable AI agents.

## Governance, Benchmarks, and Evaluation

Governance and evaluation frameworks are facing challenges related to metric gaming and context divergence. **Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** models the protocol as a published transformation graph, treating the metric itself as a security object. The authors ask when an audit metric can still certify a genuine reduction in harm, noting that strategic platforms can improve scores by routing recommendations through semantically equivalent content variants without reducing true harm. This concern is echoed in **Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity**, which defines evaluation-context divergence as an observable within-item change in behavior induced by framing a fixed task as an evaluation versus a live deployment interaction. The authors present a paired-prompt protocol to measure this divergence, controlling for paraphrase variation and benchmark familiarity.

Source attribution in deep research agents remains a critical vulnerability. **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** introduces the first source attribution evaluation framework that uses a reproducible AST parser to extract and evaluate inline citations from LLM-generated Markdown reports at scale. Unlike methods that verify accessibility, this framework assesses factual consistency and relevance. In the realm of multimodal robustness, **Are We Making Progress in Multimodal Domain Generalization? A Comprehensive Benchmark Study** questions whether reported performance gains reflect genuine algorithmic progress or artifacts of inconsistent evaluation protocols. The authors highlight that existing benchmarks focus predominantly on action recognition, neglecting critical real-world challenges such as input corruptions and missing modalities. These evaluation gaps are further highlighted by **STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?**, which identifies a critical failure mode called Implicit Conflict where a later observation invalidates an earlier memory without explicit negation. The authors introduce a benchmark of 400 expert-validated conflict scenarios to rigorously evaluate this capability.

## Open Source Security Tools and Frameworks

Several open-source projects have emerged to support these research directions, particularly in the areas of agent security and peer review. **krusch-context-mcp** provides a unified Zero-Trust MCP server that gives IDE agents local semantic codebase search, isolated episodic project memory, and hallucination-free framework RAG, addressing the security risks associated with local agent memory. **OpenClaw-AWD-Arena** offers an automated Attack-with-Defense platform where LLM-powered agents compete in real-time, facilitating the red-teaming of agent capabilities. For broader security auditing, **ai-peer-review-skill** adapts peer review processes for academic papers using parallel Claude subagents, enhancing the scrutiny of safety claims. Additionally, **SafeHarbor: Hierarchical Memory-Augmented Guardrail for LLM Agent Safety** proposes a framework to establish precise decoupling between safety and utility, mitigating the over-refusal problem common in defensive mechanisms.

## Looking Forward

Despite these advances, several theoretical questions remain unresolved. The relationship between RLVR optimization and genuine capability acquisition requires further validation; if

---


## References

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