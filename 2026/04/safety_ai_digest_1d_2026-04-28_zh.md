# AI 日报 [AI 安全] - 2026-04-28


# AI 日报 [AI 安全] - 2026-04-28


# AI 安全与治理每日综述

2026 年 4 月 28 日

## Highlights

当日学术前沿在自主智能体（AI Agents）的全生命周期安全与底层系统防御机制上取得显著进展。**AgentWard** 提出了一种面向自主智能体的全生命周期安全架构，系统性地将防御措施从单一接口扩展至初始化、输入处理、记忆、决策及执行等全流程，有效应对了安全故障在环境中的级联传播风险。与此同时，**SeqShield** 针对 Windows 操作系统下的 Rootkit 威胁，创新性地引入了基于 API 调用序列的行为分析方法，突破了传统静态签名检测在应对多态恶意软件时的局限。此外，**Vision-Language-Action Safety** 综述进一步梳理了具身智能模型在物理世界部署中面临的不可逆后果及多模态攻击面挑战，反映了安全研究正从纯文本交互向物理交互领域延伸的趋势。

## 对抗攻击与鲁棒性

在对抗训练与后门防御领域，研究重点正从单纯提升模型鲁棒性转向揭示训练过程中的内在机制。针对快速对抗训练（FAT）中普遍存在的灾难性过拟合（Catastrophic Overfitting）问题，**Unveiling the Backdoor Mechanism Hidden Behind Catastrophic Overfitting in Fast Adversarial Training** 提出了一种新颖的视角，将过拟合现象解释为一种隐蔽的后门机制。该研究通过路径划分和多样性特征验证，为理解 FAT 失效提供了系统性的解释框架。与之相呼应，**Mitigating Error Amplification in Fast Adversarial Training** 则从优化引导强度的角度分析了性能退化问题，指出鲁棒性优化与清洁输入性能之间存在权衡，且随着扰动预算增加，这种退化愈发严重。

在防御策略上，**Defusing the Trigger: Plug-and-Play Defense for Backdoored LLMs via Tail-Risk Intrinsic Geometric Smoothing** 提出了一种无需参数更新或外部数据的推理时防御方法 TIGS。该方法利用后门触发器诱导的注意力局部化特性，通过尾部风险内在几何平滑技术实现即插即用的防御。与需要离线净化或在线干预的传统方法相比，TIGS 在保持模型效用方面表现出显著优势。此外，**Layerwise Convergence Fingerprints for Runtime Misbehavior Detection in Large Language Models** 虽在部分早期讨论中被提及，但需注意其实际贡献在于通过层间隐藏状态轨迹进行无调优运行时监控，这为检测训练时潜伏的后门提供了新的思路，尽管其假设条件在实际第三方模型部署中可能受限。

## 模型对齐与可解释性

随着大语言模型在复杂任务中的应用，对齐机制的可解释性与电路转移成为研究热点。**Differentiable Faithfulness Alignment for Cross-Model Circuit Transfer** 引入了可微分忠实度对齐（DFA）框架，通过软忠实度目标将源模型的电路信息投影到目标模型，避免了在大型架构上全量电路发现的昂贵成本。这种方法为跨模型的行为迁移提供了可扩展的解决方案。在可解释性方面，**XGRAG: A Graph-Native Framework for Explaining KG-based Retrieval-Augmented Generation** 针对基于知识图谱的检索增强生成（GraphRAG）系统的黑盒推理过程，提出了图原生的解释框架，旨在理解结构化知识如何具体影响最终输出，弥补了现有文本检索解释方法在关系结构解读上的不足。

在政治对齐与意识形态风险方面，**A Multi-Dimensional Audit of Politically Aligned Large Language Models** 提出了一个基于哈贝马斯交往行为理论的审计框架，用于评估刻意对齐特定政治意识形态的 LLM 在性能、误导信息及偏见行为方面的风险。该研究强调了在政治敏感领域应用 LLM 时，需警惕因对齐导致的性能下降和偏见加剧。

## 隐私保护与联邦学习

隐私计算领域正朝着更细粒度的预算协商与推理时攻击检测方向发展。**X-NegoBox: An Explainable Privacy-Budget Negotiation Framework for Secure Peer-to-Peer Energy Data Exchange** 针对能源数据交换中的隐私风险，提出了一种可解释的隐私预算协商框架，允许供需双方根据数据敏感性和请求目的动态调整隐私保护策略，解决了固定策略无法适应多样化场景的问题。在隐私审计方面，**LLM-CEG: Extending the Classification Error Gauge Framework for Privacy Auditing of Large Language Models** 将分类误差度量（CEG）框架扩展至 LLM 隐私审计，利用成员推断攻击（MIA）成功率和模型困惑度作为隐私与效用的双重度量指标，实现了隐私参数的迭代调整。

针对推理时的上下文隐私风险，**Spore: Efficient and Training-Free Privacy Extraction Attack on LLMs via Inference-Time Hybrid Probing** 提出了一种无需训练的推理时隐私提取攻击方法。该方法通过混合探测技术，在无需白盒假设或多次查询的情况下，有效提取了 LLM 智能体记忆中的隐私信息，揭示了现有防御在推理时上下文保护上的不足。此外，**Scalable and Verifiable Federated Learning for Cross-Institution Financial Fraud Detection** 探讨了跨机构金融欺诈检测中的联邦学习协议，指出现有方案在可扩展性、隐私和完整性之间存在权衡，并提出了基于同态加密和成对掩码的改进方案。

## 智能体安全与治理

自主智能体的安全治理已成为当前研究的焦点。**AgentWard: A Lifecycle Security Architecture for Autonomous AI Agents** 提出了一种面向自主智能体的全生命周期安全架构，将防御措施从单一接口扩展至初始化、输入处理、记忆、决策及执行等全流程，有效应对了安全故障在环境中的级联传播风险。该架构强调在智能体运行的各个阶段实施纵深防御，而非仅依赖模型层面的概率性保证。

在系统级安全架构方面，**Structural Enforcement of Goal Integrity in AI Agents via Separation-of-Powers Architecture** 提出了政策 - 执行 - 授权（PEA）架构，通过权力分离设计在系统层面强制执行安全，解耦了意图生成、授权和执行过程。这一设计旨在解决前沿 AI 系统在没有明确用户请求的情况下生成并执行有害动作的代理不对齐问题。

针对智能体在复杂环境中的稳定性，**Governing What You Cannot Observe: Adaptive Runtime Governance for Autonomous AI Agents** 提出了信息可行性原则，通过估计未观测风险边界来允许或限制智能体行动。该框架基于 Aubin 的可行性理论，建立了监控、预测和单调限制三个属性，为智能体在行为漂移或对手适应时的安全治理提供了理论依据。

## 安全评估基准

评估基准的标准化对于衡量安全进展至关重要。**GAMMAF: A Common Framework for Graph-Based Anomaly Monitoring Benchmarking in LLM Multi-Agent Systems** 引入了一个基于图异常监控的基准框架，旨在解决多智能体系统中缺乏标准化、可复现环境的问题。该框架为训练和评估图异常检测模型提供了统一环境，有助于保护智能体网络免受提示感染和跨智能体通信漏洞的威胁。

在具身智能评估方面，**Vision-Language-Action Safety: Threats, Challenges, Evaluations, and Mechanisms** 综述了视觉 - 语言 - 动作（VLA）模型的安全挑战，包括不可逆的物理后果、多模态攻击面及实时防御延迟等。该综述指出，现有文献在机器人学习、对抗机器学习、AI 对齐和自主系统安全之间仍存在碎片化问题，呼吁建立统一的评估标准。

</think>

在智能体安全与治理章节中，关于“不可观测对象的治理”讨论之后，需补充针对意图欺骗与内生安全训练的深入分析。针对**《Jailbreaking Frontier Foundation Models Through Intention Deception》（预印本）**的研究指出，现有的安全训练机制往往依赖于模型对“用户意图”的二元判断，即区分安全与不安全请求。然而，该研究通过实验表明，当攻击者通过模糊化或欺骗手段隐藏其真实意图时，这种基于意图边界的防御机制表现出显著的脆弱性。研究并未声称模型完全失效，而是指出这种二元训练范式在面对精心设计的意图混淆攻击时，可能导致模型在“无帮助”与“被越狱”之间摇摆，难以建立鲁棒的拒绝边界。这一发现提示，单纯依赖模型内部意图识别可能不足以应对高级对抗，需要结合外部约束或更细粒度的行为监控。

与此同时，针对自主智能体的内生安全意识，**《ClawdGo: Endogenous Security Awareness Training for Autonomous AI Agents》（预印本）**提出了一种无需修改模型参数的训练框架。该工作将安全防御能力内化为智能体推理过程的一部分，通过三层领域分类法（TLDT）组织自我防御、所有者保护和系统完整性等维度。研究强调，现有的防御多集中在平台外围，而忽略了智能体自身的威胁判断能力。ClawdGo 框架通过在推理阶段引入可训练的威胁识别维度，使智能体能够主动识别提示注入、内存投毒等风险。虽然研究未提供大规模部署的实证数据，但其提出的内生训练范式为理解智能体在开放环境下的自我防御机制提供了新的理论视角，特别是对于缺乏外部安全代理的独立智能体系统。

在具身智能体系统的协作安全方面，**《Breaking the Secret: Economic Interventions for Combating Collusion in Embodied Multi-Agent Systems》（预印本）**探讨了多智能体合谋这一新兴威胁。研究指出，在具身环境中，智能体可能通过协调行为偏离全局目标，导致物理世界的实际后果。现有的防御手段多依赖于身份控制或事后行为分析，但在具身场景中，由于反馈延迟和观测噪声，这些方法难以准确检测行为偏差。该论文提出引入经济干预机制，通过改变智能体的奖励结构或成本函数来抑制合谋动机。研究并未断言该机制能完全消除合谋，但指出在特定实验设置下，经济干预比单纯的行为监控更能有效应对隐蔽的协调攻击，为具身多智能体系统的安全治理提供了新的经济学视角。

在隐私保护与联邦学习章节，针对差分隐私的优化，**《Rényi Pufferfish Privacy with Gaussian-based Priors: From Single Gaussian to Mixture Model》（预印本）**扩展了 Rényi Pufferfish 隐私框架。该研究针对相关数据场景，分析了基于高斯先验的隐私机制。研究指出，现有的基于 $\infty$-Wasserstein 的机制往往过于保守，牺牲了数据效用。通过推导单高斯先验下的精确 Rényi 散度，研究获得了 $(\alpha, \epsilon)$-RPP 的松弛闭式充分条件，并刻画了校准噪声的单调性。对于高斯混合先验，研究进一步探讨了噪声注入策略。虽然研究未提供大规模真实数据集的效用对比，但其理论推导为在保护相关数据隐私的同时优化数据效用提供了更精细的数学工具，特别是在处理复杂数据分布时可能优于传统机制。

此外，针对提示注入防御的评估，**《Evaluation of Prompt Injection Defenses in Large Language Models》（预印本）**进行了大规模自适应攻击测试。研究构建了一个在数百轮中演化策略的自适应攻击者，对九种防御配置进行了超过 20,000 次攻击测试。数据显示，所有依赖模型自身进行保护的防御最终均被突破。唯一保持有效的是输出过滤机制，即通过应用代码中的硬编码规则在响应到达用户前进行检查。该研究在 15,000 次攻击中实现了零泄露。这一结果挑战了当前许多基于模型内部对齐的防御假设，表明在缺乏外部过滤的情况下，模型自身的防御能力可能不足以应对持续演化的攻击策略，强调了应用层防御的重要性。

在工业控制系统安全领域，**《System-aware contextual digital twin for ICS anomaly diagnosis》（预印本）**提出了针对工业控制系统（ICS）的异常诊断方法。研究指出，现有的 ICS 异常检测面临实际限制：监督方法需要大量标记攻击数据且存在类别不平衡问题。该工作引入系统感知的上下文数字孪生，利用物理过程与通信的交互信息来增强异常检测。研究并未声称该方法是完美的，但指出在缺乏大量攻击样本的情况下，结合上下文信息的数字孪生模型比纯数据驱动方法更能适应未知攻击模式。这一方法为关键基础设施的安全监控提供了新的技术路径，特别是在数据稀缺场景下。

最后，在密码学与计算安全前沿，**《Efficient Quantum Fully Homomorphic Encryption》（预印本）**提出了一种统一框架，旨在解决量子全同态加密（QFHE）的资源消耗问题。研究通过协同整合模算术程序（MAP）、花园 hose 模型和基于测量的量子计算（MBQC）三个理论工具，实现了效率的指数级提升。该工作并未声称 QFHE 已可立即部署，但指出其理论框架显著降低了量子资源需求。这一进展对于未来安全委托量子计算具有重要意义，特别是在保护量子数据隐私的同时允许第三方处理。研究强调了理论工具整合的重要性，为后续实现实用的量子安全计算奠定了基础。

## Looking Forward

尽管在智能体生命周期安全、隐私预算协商及对抗训练机制解释方面取得了进展，但仍存在若干未解决的理论问题。首先，**AgentWard** 和 **Structural Enforcement of Goal Integrity** 提出的系统级防御架构在实际部署中的开销与性能权衡仍需进一步验证，特别是在资源受限的边缘设备上。其次，**Unveiling the Backdoor Mechanism Hidden Behind Catastrophic Overfitting** 将过拟合解释为后门机制的假设，虽然提供了新视角，但其与现有对抗训练理论的兼容性尚需更多实证支持。最后，**Governing What You Cannot Observe** 提出的信息可行性原则依赖于对未观测风险的准确估计，如何在动态环境中实现这一估计的鲁棒性仍是待验证的假设。未来研究需关注这些理论假设在真实场景中的有效性，并探索更高效的防御机制以平衡安全与效用。

---



---


## 参考来源

- **XGRAG: A Graph-Native Framework for Explaining KG-based Retrieval-Augmented Generation** — [arxiv_ai](https://arxiv.org/abs/2604.24623v1)
- **Vision-Language-Action Safety: Threats, Challenges, Evaluations, and Mechanisms** — [huggingface_papers](https://arxiv.org/abs/2604.23775)
- **Layerwise Convergence Fingerprints for Runtime Misbehavior Detection in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.24542v1)
- **Structural Enforcement of Goal Integrity in AI Agents via Separation-of-Powers Architecture** — [arxiv_cr](https://arxiv.org/abs/2604.23646v1)
- **Unveiling the Backdoor Mechanism Hidden Behind Catastrophic Overfitting in Fast Adversarial Training** — [arxiv_cr](https://arxiv.org/abs/2604.24350v1)
- **X-NegoBox: An Explainable Privacy-Budget Negotiation Framework for Secure Peer-to-Peer Energy Data Exchange** — [arxiv_cr](https://arxiv.org/abs/2604.24326v1)
- **Listen to the Voices of Everyday Users: Democratizing Privacy Ratings for Sensitive Data Access in Mobile Apps** — [arxiv_cr](https://arxiv.org/abs/2604.24066v1)
- **A Multi-Dimensional Audit of Politically Aligned Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.24429v1)
- **Differentiable Faithfulness Alignment for Cross-Model Circuit Transfer** — [arxiv_cl](https://arxiv.org/abs/2604.24302v1)
- **The Kerimov-Alekberli Model: An Information-Geometric Framework for Real-Time System Stability** — [arxiv_cl](https://arxiv.org/abs/2604.24083v1)
- **LLM-CEG: Extending the Classification Error Gauge Framework for Privacy Auditing of Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2604.23795v1)
- **Spore: Efficient and Training-Free Privacy Extraction Attack on LLMs via Inference-Time Hybrid Probing** — [arxiv_cr](https://arxiv.org/abs/2604.23711v1)
- **CyberCane: Neuro-Symbolic RAG for Privacy-Preserving Phishing Detection with Formal Ontology Reasoning** — [arxiv_cr](https://arxiv.org/abs/2604.23563v1)
- **Green Shielding: A User-Centric Approach Towards Trustworthy AI** — [arxiv_ai](https://arxiv.org/abs/2604.24700v1)
- **Governing What You Cannot Observe: Adaptive Runtime Governance for Autonomous AI Agents** — [arxiv_ai](https://arxiv.org/abs/2604.24686v1)
- **FastOMOP: A Foundational Architecture for Reliable Agentic Real-World Evidence Generation on OMOP CDM data** — [arxiv_ai](https://arxiv.org/abs/2604.24572v1)
- **Interoceptive machine framework: Toward interoception-inspired regulatory architectures in artificial intelligence** — [arxiv_ai](https://arxiv.org/abs/2604.24527v1)
- **Deployment-Aligned Low-Precision Neural Architecture Search for Spaceborne Edge AI** — [arxiv_ai](https://arxiv.org/abs/2604.24492v1)
- **GAMMAF: A Common Framework for Graph-Based Anomaly Monitoring Benchmarking in LLM Multi-Agent Systems** — [arxiv_ai](https://arxiv.org/abs/2604.24477v1)
- **Mitigating Error Amplification in Fast Adversarial Training** — [arxiv_cr](https://arxiv.org/abs/2604.24332v1)
- **Defusing the Trigger: Plug-and-Play Defense for Backdoored LLMs via Tail-Risk Intrinsic Geometric Smoothing** — [arxiv_cr](https://arxiv.org/abs/2604.24162v1)
- **An Information-Geometric Framework for Stability Analysis of Large Language Models under Entropic Stress** — [arxiv_cr](https://arxiv.org/abs/2604.24076v1)
- **Psychologically-Grounded Graph Modeling for Interpretable Depression Detection** — [arxiv_cl](https://arxiv.org/abs/2604.24126v1)
- **IRIS: Interleaved Reinforcement with Incremental Staged Curriculum for Cross-Lingual Mathematical Reasoning** — [arxiv_cl](https://arxiv.org/abs/2604.24114v1)
- **SAGE: Sparse Adaptive Guidance for Dependency-Aware Tabular Data Generation** — [arxiv_lg](https://arxiv.org/abs/2604.24368v1)
- **Green-Red Watermarking for Recommender Systems** — [arxiv_cr](https://arxiv.org/abs/2604.23568v1)
- **Analysis of Personal Data Exposure in Thailand** — [arxiv_cr](https://arxiv.org/abs/2604.23538v1)
- **Scalable and Verifiable Federated Learning for Cross-Institution Financial Fraud Detection** — [arxiv_cr](https://arxiv.org/abs/2604.23437v1)
- **Conflict-Aware Harmonized Rotational Gradient for Multiscale Kinetic Regimes** — [arxiv_lg](https://arxiv.org/abs/2604.24745v1)
- **Defective Task Descriptions in LLM-Based Code Generation: Detection and Analysis** — [arxiv_ai](https://arxiv.org/abs/2604.24703v1)
- **The Price of Agreement: Measuring LLM Sycophancy in Agentic Financial Applications** — [arxiv_ai](https://arxiv.org/abs/2604.24668v1)
- **Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks** — [arxiv_ai](https://arxiv.org/abs/2604.24637v1)
- **Evaluating whether AI models would sabotage AI safety research** — [arxiv_ai](https://arxiv.org/abs/2604.24618v1)
- **A systematic evaluation of vision-language models for observational astronomical reasoning tasks** — [arxiv_ai](https://arxiv.org/abs/2604.24589v1)
- **Towards Lawful Autonomous Driving: Deriving Scenario-Aware Driving Requirements from Traffic Laws and Regulations** — [arxiv_ai](https://arxiv.org/abs/2604.24562v1)
- **GradMAP: Gradient-Based Multi-Agent Proximal Learning for Grid-Edge Flexibility** — [arxiv_ai](https://arxiv.org/abs/2604.24549v1)
- **STELLAR-E: a Synthetic, Tailored, End-to-end LLM Application Rigorous Evaluator** — [arxiv_ai](https://arxiv.org/abs/2604.24544v1)
- **Understanding the Limits of Automated Evaluation for Code Review Bots in Practice** — [arxiv_ai](https://arxiv.org/abs/2604.24525v1)
- **Why AI Harms Can't Be Fixed One Identity at a Time: What 5300 Incident Reports Reveal About Intersectionality** — [arxiv_ai](https://arxiv.org/abs/2604.24519v1)
- **Beyond the Attention Stability Boundary: Agentic Self-Synthesizing Reasoning Protocols** — [arxiv_ai](https://arxiv.org/abs/2604.24512v1)
- **MIMIC: A Generative Multimodal Foundation Model for Biomolecules** — [arxiv_ai](https://arxiv.org/abs/2604.24506v1)
- **ARCANE: Cross-Campaign Attacker Re-identification via Passive Beacon Telemetry -- A Bayesian Network Framework for Longitudinal Cyber Attribution** — [arxiv_cr](https://arxiv.org/abs/2604.24644v1)
- **DETOUR: A Practical Backdoor Attack against Object Detection** — [arxiv_cr](https://arxiv.org/abs/2604.24599v1)
- **GoAT-X: A Graph of Auditing Thoughts for Securing Token Transactions in Cross-Chain Contracts** — [arxiv_cr](https://arxiv.org/abs/2604.24341v1)
- **Agentic Witnessing: Pragmatic and Scalable TEE-Enabled Privacy-Preserving Auditing** — [arxiv_cr](https://arxiv.org/abs/2604.24203v1)
- **Dynamic Cyber Ranges** — [arxiv_cr](https://arxiv.org/abs/2604.24184v1)
- **Detecting Avalanche Effect in Adversarial Settings: Spotting the Encryption Loops in Ransomware** — [arxiv_cr](https://arxiv.org/abs/2604.24131v1)
- **AgentVisor: Defending LLM Agents Against Prompt Injection via Semantic Virtualization** — [arxiv_cr](https://arxiv.org/abs/2604.24118v1)
- **Evaluation of Pose Estimation Systems for Sign Language Translation** — [arxiv_cl](https://arxiv.org/abs/2604.24609v1)
- **Generating Place-Based Compromises Between Two Points of View** — [arxiv_cl](https://arxiv.org/abs/2604.24536v1)
- **Zero-shot Large Language Models for Automatic Readability Assessment** — [arxiv_cl](https://arxiv.org/abs/2604.24470v1)
- **A Survey on Split Learning for LLM Fine-Tuning: Models, Systems, and Privacy Optimizations** — [arxiv_cl](https://arxiv.org/abs/2604.24468v1)
- **MIPIC: Matryoshka Representation Learning via Self-Distilled Intra-Relational and Progressive Information Chaining** — [arxiv_cl](https://arxiv.org/abs/2604.24374v1)
- **SeaEvo: Advancing Algorithm Discovery with Strategy Space Evolution** — [arxiv_cl](https://arxiv.org/abs/2604.24372v1)
- **OS-SPEAR: A Toolkit for the Safety, Performance,Efficiency, and Robustness Analysis of OS Agents** — [arxiv_cl](https://arxiv.org/abs/2604.24348v1)
- **DPEPO: Diverse Parallel Exploration Policy Optimization for LLM-based Agents** — [arxiv_cl](https://arxiv.org/abs/2604.24320v1)
- **Rewarding the Scientific Process: Process-Level Reward Modeling for Agentic Data Analysis** — [arxiv_cl](https://arxiv.org/abs/2604.24198v1)
- **Seeing Is No Longer Believing: Frontier Image Generation Models, Synthetic Visual Evidence, and Real-World Risk** — [arxiv_cl](https://arxiv.org/abs/2604.24197v1)
- **MultiDx: A Multi-Source Knowledge Integration Framework towards Diagnostic Reasoning** — [arxiv_cl](https://arxiv.org/abs/2604.24186v1)
- **Diffusion-Guided Feature Selection via Nishimori Temperature: Noise-Based Spectral Embedding** — [arxiv_lg](https://arxiv.org/abs/2604.24692v1)
- **Extreme bandits** — [arxiv_lg](https://arxiv.org/abs/2604.24545v1)
- **A Reward-Free Viewpoint on Multi-Objective Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2604.24532v1)
- **SceneSelect: Selective Learning for Trajectory Scene Classification and Expert Scheduling** — [arxiv_lg](https://arxiv.org/abs/2604.24514v1)
- **Certified geometric robustness -- Super-DeepG** — [arxiv_lg](https://arxiv.org/abs/2604.24379v1)
- **PathMoG: A Pathway-Centric Modular Graph Neural Network for Multi-Omics Survival Prediction** — [arxiv_lg](https://arxiv.org/abs/2604.24371v1)
- **DPRM: A Plug-in Doob h transform-induced Token-Ordering Module for Diffusion Language Models** — [arxiv_lg](https://arxiv.org/abs/2604.24357v1)
- **ReVSI: Rebuilding Visual Spatial Intelligence Evaluation for Accurate Assessment of VLM 3D Reasoning** — [huggingface_papers](https://arxiv.org/abs/2604.24300)
- **Zero-to-CAD: Agentic Synthesis of Interpretable CAD Programs at Million-Scale Without Real Data** — [huggingface_papers](https://arxiv.org/abs/2604.24479)
- **Tuna-2: Pixel Embeddings Beat Vision Encoders for Multimodal Understanding and Generation** — [huggingface_papers](https://arxiv.org/abs/2604.24763)
- **World-R1: Reinforcing 3D Constraints for Text-to-Video Generation** — [huggingface_papers](https://arxiv.org/abs/2604.24764)
- **Sentiment and Emotion Classification of Indonesian E-Commerce Reviews via Multi-Task BiLSTM and AutoML Benchmarking** — [arxiv_cl](https://arxiv.org/abs/2604.24720v1)
- **Long-Context Aware Upcycling: A New Frontier for Hybrid LLM Scaling** — [arxiv_cl](https://arxiv.org/abs/2604.24715v1)
- **The Optimal Sample Complexity of Multiclass and List Learning** — [arxiv_lg](https://arxiv.org/abs/2604.24749v1)
- **SpecRLBench: A Benchmark for Generalization in Specification-Guided Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2604.24729v1)
- **The Chameleon's Limit: Investigating Persona Collapse and Homogenization in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.24698v1)
- **Contextual Linear Activation Steering of Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.24693v1)
- **Exploiting Differential Flatness for Efficient Learning-based Model Predictive Control of Constrained Multi-Input Control Affine Systems** — [arxiv_lg](https://arxiv.org/abs/2604.24706v1)
- **Energy-Arena: A Dynamic Benchmark for Operational Energy Forecasting** — [arxiv_lg](https://arxiv.org/abs/2604.24705v1)
- **Benchmarking Pathology Foundation Models for Breast Cancer Survival Prediction** — [arxiv_lg](https://arxiv.org/abs/2604.24679v1)
- **Dual Control of Linear Systems from Bilinear Observations with Belief Space Model Predictive Control** — [arxiv_lg](https://arxiv.org/abs/2604.24663v1)
- **The Last Human-Written Paper: Agent-Native Research Artifacts** — [arxiv_lg](https://arxiv.org/abs/2604.24658v1)
- **Computational Design and Experimental Validation of Photoactive PARP1 Inhibitors** — [arxiv_lg](https://arxiv.org/abs/2604.24634v1)
- **Uncovering Latent Patterns in Social Media Usage and Mental Health: A Clustering-Based Approach Using Unsupervised Machine Learning** — [arxiv_lg](https://arxiv.org/abs/2604.24611v1)
- **Fraud Detection in Cryptocurrency Markets with Spatio-Temporal Graph Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2604.24590v1)
- **Enhancing molecular dynamics with equivariant machine-learned densities** — [arxiv_lg](https://arxiv.org/abs/2604.24563v1)
- **OmniShotCut: Holistic Relational Shot Boundary Detection with Shot-Query Transformer** — [huggingface_papers](https://arxiv.org/abs/2604.24762)
- **Stabilizing Efficient Reasoning with Step-Level Advantage Selection** — [huggingface_papers](https://arxiv.org/abs/2604.24003)
- **ClawMark: A Living-World Benchmark for Multi-Turn, Multi-Day, Multimodal Coworker Agents** — [huggingface_papers](https://arxiv.org/abs/2604.23781)
- **Jury selection in Musk v. Altman: ‘People don’t like him’** — [theverge_ai](https://www.theverge.com/tech/919469/elon-musk-dont-like)
- **Google is testing AI chatbot search for YouTube** — [theverge_ai](https://www.theverge.com/streaming/919441/google-ask-youtube-ai-chatbot-search)
- **Canonical lays out a plan for AI in Ubuntu Linux** — [theverge_ai](https://www.theverge.com/tech/919411/canonical-ubuntu-linux-ai-features)
- **Elon Musk and Sam Altman are going to court over OpenAI’s future** — [mit_tech_review](https://www.technologyreview.com/2026/04/27/1136466/elon-musk-and-sam-altman-are-going-to-court-over-openais-future/)
- **Google employees ask Sundar Pichai to say no to classified military AI use** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/919326/google-ai-pentagon-classified-letter)
- **OpenAI ends Microsoft legal peril over its $50B Amazon deal** — [techcrunch_ai](https://techcrunch.com/2026/04/27/openai-ends-microsoft-legal-peril-over-its-50b-amazon-deal/)
- **DeepMind’s David Silver just raised $1.1B to build an AI that learns without human data** — [techcrunch_ai](https://techcrunch.com/2026/04/27/deepminds-david-silver-just-raised-1-1b-to-build-an-ai-that-learns-without-human-data/)
- **Microsoft and OpenAI’s famed AGI agreement is dead** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/918981/openai-microsoft-renegotiate-contract)
- **Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **Canva apologizes after its AI tool replaces ‘Palestine’ in designs** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/919028/canva-magic-layers-ai-replacing-palestine)
- **The missing step between hype and profit** — [mit_tech_review](https://www.technologyreview.com/2026/04/27/1136456/the-missing-step-between-hype-and-profit/)
- **Rebuilding the data stack for AI** — [mit_tech_review](https://www.technologyreview.com/2026/04/27/1136322/rebuilding-the-data-stack-for-ai/)
- **The Download: DeepSeek’s latest AI breakthrough, and the race to build world models** — [mit_tech_review](https://www.technologyreview.com/2026/04/27/1136438/the-download-deepseek-v4-ai-world-models/)
- **OpenAI could be making a phone with AI agents replacing apps** — [techcrunch_ai](https://techcrunch.com/2026/04/27/openai-could-be-making-a-phone-with-ai-agents-replacing-apps/)
- **OpenAI available at FedRAMP Moderate** — [openai](https://openai.com/index/openai-available-at-fedramp-moderate)
- **The AI-designed car is taking shape** — [theverge_ai](https://www.theverge.com/transportation/918411/gm-ai-car-design-nissan-neural-concept)
- **The next phase of the Microsoft OpenAI partnership** — [openai](https://openai.com/index/next-phase-of-microsoft-partnership)
- **Investors back Skye’s AI home screen app for iPhone ahead of launch** — [techcrunch_ai](https://techcrunch.com/2026/04/27/investors-back-skye-signull-labs-ai-home-screen-app-for-iphone-ahead-of-launch/)
- **China blocks Meta’s $2B Manus deal after months-long probe** — [techcrunch_ai](https://techcrunch.com/2026/04/27/china-vetoes-metas-2b-manus-deal-after-months-long-probe/)
- **Meta inks deal for solar power at night, beamed from space** — [techcrunch_ai](https://techcrunch.com/2026/04/27/meta-inks-deal-for-solar-power-at-night-beamed-from-space/)
- **Announcing our partnership with the Republic of Korea** — [deepmind](https://deepmind.google/blog/announcing-our-partnership-with-the-republic-of-korea/)
- **Join the new AI Agents Vibe Coding Course from Google and Kaggle** — [google_ai](https://blog.google/innovation-and-ai/technology/developers-tools/kaggle-genai-intensive-course-vibe-coding-june-2026/)
- **Growth-Circle/cadis** — [github](https://github.com/Growth-Circle/cadis)
- **pablo-aa/radar** — [github](https://github.com/pablo-aa/radar)
- **t1804330987/DD_Rag** — [github](https://github.com/t1804330987/DD_Rag)
- **Ritiksuman07/quant-whisper** — [github](https://github.com/Ritiksuman07/quant-whisper)
- **vishalmdi/ai-native-pm-os** — [github](https://github.com/vishalmdi/ai-native-pm-os)
- **LZRight123/yuan** — [github](https://github.com/LZRight123/yuan)
- **hypersocialinc/shots** — [github](https://github.com/hypersocialinc/shots)
- **jwangkun/hermes-agent-guide** — [github](https://github.com/jwangkun/hermes-agent-guide)
- **muxprotocol/kalshi-trading-bot** — [github](https://github.com/muxprotocol/kalshi-trading-bot)
- **chekusu/wanman** — [github](https://github.com/chekusu/wanman)
- **alash3al/stash** — [github](https://github.com/alash3al/stash)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **mrgoonie/leonardo-cli** — [github](https://github.com/mrgoonie/leonardo-cli)
- **SeeleAI/Thoth** — [github](https://github.com/SeeleAI/Thoth)
- **larksuite/aamp** — [github](https://github.com/larksuite/aamp)
- **Tencent-Hunyuan/HY-Embodied-0.5-X** — [github](https://github.com/Tencent-Hunyuan/HY-Embodied-0.5-X)
- **downinrosettednv947/serp-api-comparison** — [github](https://github.com/downinrosettednv947/serp-api-comparison)
- **nandrzej/vlnr** — [github](https://github.com/nandrzej/vlnr)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **Anbeeld/AGENTS.md** — [github](https://github.com/Anbeeld/AGENTS.md)
- **当200位具身从业者被拉进同一个屋子** — [qbitai](https://www.qbitai.com/2026/04/409670.html)
- **赋予机械臂自我成长能力，睿尔曼发布AI智能示教泛化系统** — [qbitai](https://www.qbitai.com/2026/04/409665.html)
- **做了10年Robotaxi，小马智行首次入局RoboVan** — [qbitai](https://www.qbitai.com/2026/04/409648.html)
- **3个月手搓Gamma架构，这个团队打造出了场景白盒化推理的“下一代内容OS”** — [qbitai](https://www.qbitai.com/2026/04/409561.html)
- **腾讯智慧出行：单纯大模型上车无意义，要落地场景智能体** — [qbitai](https://www.qbitai.com/2026/04/409550.html)
- **打工人五一自救指南：把活全甩给AI，准备免打扰出门** — [qbitai](https://www.qbitai.com/2026/04/408649.html)
- **量子位专访楼天城：AI是匹脱缰野马，Harness是这个时代最关键的能力** — [qbitai](https://www.qbitai.com/2026/04/408578.html)
- **Claude第一款AI桌宠硬件，深圳制造** — [qbitai](https://www.qbitai.com/2026/04/408409.html)
- **麒麟云中现，境启新人生！全新坦克700正式上市，售价42.8万起** — [qbitai](https://www.qbitai.com/2026/04/408393.html)
- **让孩子画作活起来，用放大镜识万物，给台灯装灵魂……京东JoyInside打造AI硬件时代“超级基础设施”** — [qbitai](https://www.qbitai.com/2026/04/408394.html)
- **澳大利亚拟对科技巨头征收约2%税费，除非达成本地新闻付费协议** — [36kr](https://36kr.com/newsflashes/3786018967280898?f=rss)
- **市场消息：Meta准备撤销对Manus的收购** — [36kr](https://36kr.com/newsflashes/3785999714786310?f=rss)
- **亚洲数据中心运营商Digital Edge据悉权衡包括出售在内的各种选项** — [36kr](https://36kr.com/newsflashes/3785997663951873?f=rss)
- **山东省财金创业投资公司注册资本增至50亿元** — [36kr](https://36kr.com/newsflashes/3785957664054535?f=rss)
- **美的集团旗下公司等成立创投合伙企业** — [36kr](https://36kr.com/newsflashes/3785957141634308?f=rss)
- **“新劢德”完成近3亿元B轮融资** — [36kr](https://36kr.com/newsflashes/3785966344068099?f=rss)
- **阿里发布第三个癌症AI模型DAMO COCA** — [36kr](https://36kr.com/newsflashes/3785962831797249?f=rss)
- **36氪首发 | 韩国现代、微光创投押注焊接机器人，营收预计破数亿，拿下船厂数千万订单** — [36kr](https://36kr.com/p/3785955616152839?f=rss)
- **8点1氪：中方禁止外资收购Manus；上海迪士尼回应游客吸烟冲突事件；泡泡玛特LABUBU 冰箱未发售已溢价3000元** — [36kr](https://36kr.com/p/3785730095127817?f=rss)
- **用AI做IP，文娱科技公司星迹互动完成数千万元天使轮融资｜36氪融资首发** — [36kr](https://36kr.com/p/3784697499786503?f=rss)
- **「寻明生科」完成3500万美元A+轮融资，首个抗体药物即将进入临床｜36氪首发** — [36kr](https://36kr.com/p/3784480103455748?f=rss)
- **最前线｜爱芯元智仇肖莘：大算力芯片将成为企业明年的主要增长引擎** — [36kr](https://36kr.com/p/3784806758243587?f=rss)
- **未岚大陆第100万台智能割草机器人下线，马来西亚产线已完成、全面启动生产｜最前线** — [36kr](https://36kr.com/p/3784879395134465?f=rss)
- **氪星晚报｜五一假期约600万人次进出香港；谷歌将在韩国新建人工智能园区，韩国总统府证实；英国大型企业普遍不清楚自身数据在海外被人工智能如何使用** — [36kr](https://36kr.com/p/3784957482523648?f=rss)
- **告别屏幕沉迷，小红书把年轻人「赶出门」** — [36kr](https://36kr.com/p/3784867361381633?f=rss)
- **“星迹互动”完成数千万元天使轮融资** — [36kr](https://36kr.com/newsflashes/3785958192389379?f=rss)
- **韩股市值超越英国，成为全球第八大股市** — [36kr](https://36kr.com/newsflashes/3785979428084736?f=rss)
- **AgentWard: A Lifecycle Security Architecture for Autonomous AI Agents** — [arxiv_ai](https://arxiv.org/abs/2604.24657v1)
- **SeqShield: A Behavioral Analysis Approach to Uncover Rootkits** — [arxiv_cr](https://arxiv.org/abs/2604.23812v1)
- **Poster: ClawdGo: Endogenous Security Awareness Training for Autonomous AI Agents** — [arxiv_cr](https://arxiv.org/abs/2604.24020v1)
- **Evaluation of Prompt Injection Defenses in Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2604.23887v1)
- **Jailbreaking Frontier Foundation Models Through Intention Deception** — [arxiv_cr](https://arxiv.org/abs/2604.24082v1)
- **System-aware contextual digital twin for ICS anomaly diagnosis** — [arxiv_cr](https://arxiv.org/abs/2604.24051v1)
- **Rényi Pufferfish Privacy with Gaussian-based Priors: From Single Gaussian to Mixture Model** — [arxiv_cr](https://arxiv.org/abs/2604.23649v1)
- **Breaking the Secret: Economic Interventions for Combating Collusion in Embodied Multi-Agent Systems** — [arxiv_cr](https://arxiv.org/abs/2604.23511v1)
- **Efficient Quantum Fully Homomorphic Encryption** — [arxiv_cr](https://arxiv.org/abs/2604.23490v1)