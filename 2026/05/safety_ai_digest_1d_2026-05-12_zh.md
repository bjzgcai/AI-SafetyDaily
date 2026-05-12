# AI 日报 [AI 安全] - 2026-05-12


# 2026-05-12 AI 安全与治理每日综述

## Highlights

当日研究进展在自主智能体安全评估与集体对齐动力学方面取得显著突破。**LITMUS: Benchmarking Behavioral Jailbreaks of LLM Agents in Real OS Environments** 首次将安全评估从语义层扩展至操作系统物理层，揭示了智能体在真实环境中执行危险操作的不可逆风险。在集体智能领域，**Conformity Generates Collective Misalignment in AI Agents Societies** 与 **Collective Alignment in LLM Multi-Agent Systems: Disentangling Bias from Cooperation via Statistical Physics** 共同指出，个体对齐的智能体群体可能因社会从众效应而陷入稳定的非对齐状态，这一发现挑战了传统对齐理论的假设。此外，**Acceptance Cards: A Four-Diagnostic Standard for Safe Fine-Tuning Defense Claims** 提出了针对安全微调声明的严格验证协议，强调了区分统计噪声与真实防御机制的重要性，为行业安全评估提供了新的基准。

## 智能体行为安全与操作系统级风险

随着大语言模型驱动的智能体逐渐从沙盒环境走向真实操作系统，行为层面的安全风险日益凸显。**LITMUS: Benchmarking Behavioral Jailbreaks of LLM Agents in Real OS Environments** 指出，现有基准测试往往局限于语义层，无法隔离测试用例，导致物理层危害被低估。该工作通过构建语义与物理双重维度的测试环境，揭示了智能体在真实 OS 环境中执行危险操作的潜在路径。与之相呼应，**WildClawBench: A Benchmark for Real-World, Long-Horizon Agent Evaluation** 进一步强调了长周期任务在真实运行时环境中的评估必要性，指出合成沙盒无法完全反映智能体在复杂动态中的表现。针对此类风险，**MATRA: Modeling the Attack Surface of Agentic AI Systems -- OpenClaw Case Study** 提出了一种基于攻击树的威胁建模框架，旨在将通用的 LLM 威胁类别映射到具体的部署场景中，帮助从业者系统性地评估资产影响与攻击可能性。

在工具链与基础设施层面，开源社区正致力于构建更安全的智能体开发环境。**AgentClaw** 与 **litellm-agent-platform** 等开源项目提供了声明式工作流与生产级基础设施，支持模型热切换、缓存管理及熔断机制，试图通过工程化手段减少人为错误引发的安全漏洞。然而，**Engineering Robustness into Personal Agents with the AI Workflow Store** 警告称，当前的“即时生成”范式可能绕过了传统的软件工程流程，导致系统缺乏迭代设计与对抗性评估，建议引入更严谨的测试与部署阶段。此外，**RUBEN: Rule-Based Explanations for Retrieval-Augmented LLM Systems** 通过交互式工具发现最小规则集，为解释检索增强生成系统的输出提供了可验证的安全审计手段，有助于识别潜在的对抗性注入攻击。

## 多智能体对齐与社会动力学

多智能体系统的集体行为正成为对齐研究的新前沿。**Conformity Generates Collective Misalignment in AI Agents Societies** 通过模拟九种大语言模型与一百对意见对，发现个体对齐的智能体在群体中可能因遵循多数意见的倾向而陷入稳定的非对齐状态。这一结论与 **Collective Alignment in LLM Multi-Agent Systems: Disentangling Bias from Cooperation via Statistical Physics** 的研究相互印证，后者利用统计物理方法解耦了社会从众效应与内在偏见，计算了临界指数并探测了集体行为的相变。这表明，简单的个体对齐策略不足以保障群体安全，必须考虑社会动力学对集体行为的塑造作用。

在偏见与公平性方面，**StereoTales: A Multilingual Framework for Open-Ended Stereotype Discovery in LLMs** 扩展了偏见评估的边界，通过覆盖十种语言与七十九个社会人口属性的数据集，系统性地研究了开放生成中的社会偏见，弥补了现有基准以英语为中心的不足。同时，**Omni-Persona: Systematic Benchmarking and Improving Omnimodal Personalization** 提出了首个涵盖文本、图像与音频的跨模态个性化基准，强调在缺乏特定人设场景下的系统性与接地研究。这些工作共同表明，对齐研究正从单一模型的行为控制转向复杂社会网络中的动态平衡，且需兼顾多语言与多模态的公平性挑战。

## 隐私计算与联邦学习创新

隐私保护技术在本日研究中呈现出从理论机制向实用化框架演进的趋势。**DP-LAC: Lightweight Adaptive Clipping for Differentially Private Federated Fine-tuning of Language Models** 提出了一种轻量级自适应裁剪方法，解决了现有自适应技术需要繁琐超参数调优的问题，从而在保护隐私预算的同时提升了微调效率。在联邦学习的数据生成环节，**Provable Sparse Inversion and Token Relabel Enhanced One-Shot Federated Learning with ViTs** 引入了稀疏模型反演与标记重标记框架，克服了非独立同分布设置下合成数据语义对齐差的问题。针对轨迹数据的隐私保护，**diffGHOST: Diffusion based Generative Hedged Oblivious Synthetic Trajectories** 利用基于潜在空间的扩散模型生成合成轨迹，在保留数据效用的同时提供了隐私保证，解决了传统生成模型缺乏隐私保障的缺陷。

此外，**Private Information Retrieval With Arbitrary Privacy Requirements for Graph-Based Storage** 与 **Local Private Information Retrieval: A New Privacy Perspective for Graph-Based Replicated Systems** 重新定义了基于图存储的隐私信息检索问题，引入了本地用户隐私概念，旨在衡量通信效率的提升。这些研究共同指向一个方向，即在保证数据可用性的前提下，通过改进隐私机制（如自适应裁剪、扩散模型、图结构优化）来适应更复杂的分布式学习场景，同时警惕隐私预算的过度消耗。

## 内容安全与防御机制

针对大语言模型的内容安全风险，防御策略正从单一拦截转向多层次协同。**When Prompts Become Payloads: A Framework for Mitigating SQL Injection Attacks in Large Language Model-Driven Applications** 揭示了自然语言接口在转换为结构化查询时放大的 SQL 注入风险，强调了提示词到 SQL 翻译过程中的安全漏洞。**Guaranteed Jailbreaking Defense via Disrupt-and-Rectify Smoothing** 提出了一种基于平滑的防御方法，通过破坏与修正两阶段处理恢复分布外输入，旨在提供可保证的对抗防御。**Re-Triggering Safeguards within LLMs for Jailbreak Detection** 则主张通过嵌入扰动重新激活模型内部的安全机制，而非依赖独立的防御方案，体现了与模型原生防御协同的思路。

在生成式模型的安全方面，**What Concepts Lie Within? Detecting and Suppressing Risky Content in Diffusion Transformers** 关注了扩散 Transformer 架构中风险概念的检测与抑制，指出现有方法多针对 U-Net 架构，难以应对 DiT 架构中语义嵌入的纠缠问题。同时，**The Alpha Blending Hypothesis: Compositing Shortcut in Deepfake Detection** 提出了深度伪造检测的混合假设，指出当前检测器可能主要定位低层合成伪影而非语义异常，这为检测器的泛化能力提出了质疑。这些工作表明，随着模型架构的演进（如从 U-Net 到 DiT，从文本到多模态），安全防御机制必须同步更新，以应对新的攻击面与架构特性。

## 安全评估基准与治理框架

安全评估的严谨性成为当日讨论的核心议题之一。**Acceptance Cards: A Four-Diagnostic Standard for Safe Fine-Tuning Defense Claims** 引入了包含统计可靠性、语义泛化、机制对齐与跨任务转移的四项诊断标准，旨在防止将采样噪声或能力损失误判为防御效果。在视频生成与物理推理领域，**WorldReasonBench: Human-Aligned Stress Testing of Video Generators as Future World-State Predictors** 将视频生成评估重构为世界状态预测，测试模型在物理、社会与逻辑一致性上的表现。**PhyGround: Benchmarking Physical Reasoning in Generative World Models** 也致力于评估生成视频是否遵循物理规则，指出了现有基准在评估框架与自动评估器上的不足。

在治理层面，**Operationalizing Cybersecurity Governance for Mitigation Planning with Attack-Path Modeling and Reinforcement Learning** 尝试将 NIST 网络安全框架映射到 MITRE ATT&CK 缓解能力，以支持资源约束下的防御策略选择。**Mapping Partisan Fault Lines Within DAOs** 则通过分析链上投票行为检测去中心化自治组织中的党派分裂风险。这些工作表明，安全治理正从宏观框架向可操作的量化指标转变，试图通过算法与建模手段将政策要求转化为具体的技术决策。

## 开源工具与基础设施

开源社区在构建安全基础设施方面提供了关键支持。**llmix** 作为生产级 LLM 调用层，支持模型热切换、缓存、重试及密钥轮换，为智能体与工具调用提供了基础保障。**Zero-Trust MCP server** 提供了本地语义代码搜索与隔离的 episodic 项目记忆，旨在减少幻觉并增强安全性。**AgentClaw** 与 **Mercury Agent Skills** 等工具则致力于将单句想法转化为可复用的能力，通过声明式工作流减少样板代码，从而降低人为配置错误带来的风险。**PaperGuru-Benchmark** 则关注长周期智能体的生命周期感知记忆，为科研自动化提供了评估基准。这些工具共同构成了智能体安全开发生态的基础设施，强调通过工程化手段（如缓存、隔离、标准化接口）来缓解模型本身的不确定性。

## Looking Forward

尽管当日研究在多个维度取得了进展，但理论层面的未解问题依然显著。首先，多智能体系统中的集体对齐动力学尚未形成统一的理论框架，**Conformity Generates Collective Misalignment** 所揭示的社会从众效应与 **Collective Alignment** 中的统计物理模型之间需要更深入的整合，以预测不同规模群体下的相变临界点。其次，隐私保护与效用之间的权衡仍需更精细的度量，现有的差分隐私机制在联邦学习中的自适应裁剪虽有所改进，但在极端非独立同分布场景下的隐私预算消耗机制仍需验证。最后，安全评估的标准化仍面临挑战，**Acceptance Cards** 提出的诊断标准虽具启发性，但在工业界大规模落地时如何平衡评估成本与防御收益，仍需更多实证研究。未来工作应重点关注跨模态风险传播机制、动态环境下的实时防御策略以及治理框架的自动化执行能力。

---


## 参考来源

- **LITMUS: Benchmarking Behavioral Jailbreaks of LLM Agents in Real OS Environments** — [arxiv_cl](https://arxiv.org/abs/2605.10779v1)
- **Conformity Generates Collective Misalignment in AI Agents Societies** — [arxiv_cl](https://arxiv.org/abs/2605.10721v1)
- **When Prompts Become Payloads: A Framework for Mitigating SQL Injection Attacks in Large Language Model-Driven Applications** — [arxiv_cr](https://arxiv.org/abs/2605.10176v1)
- **Collective Alignment in LLM Multi-Agent Systems: Disentangling Bias from Cooperation via Statistical Physics** — [arxiv_cl](https://arxiv.org/abs/2605.10528v1)
- **Guaranteed Jailbreaking Defense via Disrupt-and-Rectify Smoothing** — [arxiv_cr](https://arxiv.org/abs/2605.10582v1)
- **Engineering Robustness into Personal Agents with the AI Workflow Store** — [arxiv_ai](https://arxiv.org/abs/2605.10907v1)
- **Unmasking On-Policy Distillation: Where It Helps, Where It Hurts, and Why** — [arxiv_ai](https://arxiv.org/abs/2605.10889v1)
- **Interpretable Machine Learning for Football Performance Analysis: Evidence of Limited Transferability from Elite Leagues to University Competition** — [arxiv_ai](https://arxiv.org/abs/2605.10796v1)
- **Provable Sparse Inversion and Token Relabel Enhanced One-shot Federated Learning with ViTs** — [arxiv_ai](https://arxiv.org/abs/2605.10748v1)
- **DP-LAC: Lightweight Adaptive Clipping for Differentially Private Federated Fine-tuning of Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.10272v1)
- **MARGIN: Margin-Aware Regularized Geometry for Imbalanced Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2605.10240v1)
- **What Concepts Lie Within? Detecting and Suppressing Risky Content in Diffusion Transformers** — [arxiv_cr](https://arxiv.org/abs/2605.10180v1)
- **Differentially Private Sampling from Distributions via Wasserstein Projection** — [arxiv_cr](https://arxiv.org/abs/2605.10015v1)
- **Deep Learning under Fractional-Order Differential Privacy** — [arxiv_cr](https://arxiv.org/abs/2605.09890v1)
- **Operationalizing Cybersecurity Governance for Mitigation Planning with Attack-Path Modeling and Reinforcement Learning** — [arxiv_cr](https://arxiv.org/abs/2605.09792v1)
- **"Training robust watermarking model may hurt authentication!'' Exploring and Mitigating the Identity Leakage in Robust Watermarking** — [arxiv_cr](https://arxiv.org/abs/2605.09646v1)
- **Injecting Distributional Awareness into MLLMs via Reinforcement Learning for Deep Imbalanced Regression** — [huggingface_papers](https://arxiv.org/abs/2605.01402)
- **Reinforcing Multimodal Reasoning Against Visual Degradation** — [huggingface_papers](https://arxiv.org/abs/2605.09262)
- **Dynamic Skill Lifecycle Management for Agentic Reinforcement Learning** — [arxiv_cl](https://arxiv.org/abs/2605.10923v1)
- **RubricEM: Meta-RL with Rubric-guided Policy Decomposition beyond Verifiable Rewards** — [arxiv_cl](https://arxiv.org/abs/2605.10899v1)
- **Neural at ArchEHR-QA 2026: One Method Fits All: Unified Prompt Optimization for Clinical QA over EHRs** — [arxiv_cl](https://arxiv.org/abs/2605.10877v1)
- **Compute Where it Counts: Self Optimizing Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.10875v1)
- **DGPO: Beyond Pairwise Preferences with Directional Consistent Groupwise Optimization** — [arxiv_cl](https://arxiv.org/abs/2605.10863v1)
- **Towards On-Policy Data Evolution for Visual-Native Multimodal Deep Search Agents** — [arxiv_cl](https://arxiv.org/abs/2605.10832v1)
- **When Can Digital Personas Reliably Approximate Human Survey Findings?** — [arxiv_cl](https://arxiv.org/abs/2605.10659v1)
- **Intrinsic Guardrails: How Semantic Geometry of Personality Interacts with Emergent Misalignment in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.10633v1)
- **Responsible Benchmarking of Fairness for Automatic Speech Recognition** — [arxiv_cl](https://arxiv.org/abs/2605.10615v1)
- **Learning Less Is More: Premature Upper-Layer Attention Specialization Hurts Language Model Pretraining** — [arxiv_cl](https://arxiv.org/abs/2605.10504v1)
- **StereoTales: A Multilingual Framework for Open-Ended Stereotype Discovery in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.10442v1)
- **Private Information Retrieval With Arbitrary Privacy Requirements for Graph-Based Storage** — [arxiv_cr](https://arxiv.org/abs/2605.10879v1)
- **Local Private Information Retrieval: A New Privacy Perspective for Graph-Based Replicated Systems** — [arxiv_cr](https://arxiv.org/abs/2605.10872v1)
- **Democratizing Measurement of Critical Mobile Infrastructure: Security and Privacy in an Increasingly Centralized Communication Ecosystem** — [arxiv_cr](https://arxiv.org/abs/2605.10812v1)
- **LLMs for Secure Hardware Design and Related Problems: Opportunities and Challenges** — [arxiv_cr](https://arxiv.org/abs/2605.10807v1)
- **Cybercrime and Prevention: Colonel Blotto in Social Engineering** — [arxiv_cr](https://arxiv.org/abs/2605.10755v1)
- **diffGHOST: Diffusion based Generative Hedged Oblivious Synthetic Trajectories** — [arxiv_cr](https://arxiv.org/abs/2605.10647v1)
- **Re-Triggering Safeguards within LLMs for Jailbreak Detection** — [arxiv_cr](https://arxiv.org/abs/2605.10611v1)
- **Acceptance Cards:A Four-Diagnostic Standard for Safe Fine-Tuning Defense Claims** — [arxiv_cr](https://arxiv.org/abs/2605.10575v1)
- **SoK: A Systematic Bidirectional Literature Review of AI & DLT Convergence** — [arxiv_cr](https://arxiv.org/abs/2605.10515v1)
- **ObfAx: Obfuscation and IP Piracy Detection in Approximate Circuits** — [arxiv_cr](https://arxiv.org/abs/2605.10355v1)
- **Mapping Partisan Fault Lines Within DAOs** — [arxiv_cr](https://arxiv.org/abs/2605.10316v1)
- **BEACON: A Multimodal Dataset for Learning Behavioral Fingerprints from Gameplay Data** — [arxiv_ai](https://arxiv.org/abs/2605.10867v1)
- **Training-Free Cultural Alignment of Large Language Models via Persona Disagreement** — [arxiv_ai](https://arxiv.org/abs/2605.10843v1)
- **Clin-JEPA: A Multi-Phase Co-Training Framework for Joint-Embedding Predictive Pretraining on EHR Patient Trajectories** — [arxiv_ai](https://arxiv.org/abs/2605.10840v1)
- **MMVIAD: Multi-view Multi-task Video Understanding for Industrial Anomaly Detection** — [arxiv_ai](https://arxiv.org/abs/2605.10833v1)
- **ALAM: Algebraically Consistent Latent Transitions for Vision-Language-Action Models** — [arxiv_ai](https://arxiv.org/abs/2605.10819v1)
- **CLEF: EEG Foundation Model for Learning Clinical Semantics** — [arxiv_ai](https://arxiv.org/abs/2605.10817v1)
- **Policy Gradient Methods for Non-Markovian Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.10816v1)
- **Probing Cross-modal Information Hubs in Audio-Visual LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.10815v1)
- **NanoResearch: Co-Evolving Skills, Memory, and Policy for Personalized Research Automation** — [arxiv_ai](https://arxiv.org/abs/2605.10813v1)
- **Switching-Geometry Analysis of Deflated Q-Value Iteration** — [arxiv_ai](https://arxiv.org/abs/2605.10811v1)
- **PhyGround: Benchmarking Physical Reasoning in Generative World Models** — [arxiv_ai](https://arxiv.org/abs/2605.10806v1)
- **Reasoning Is Not Free: Robust Adaptive Cost-Efficient Routing for LLM-as-a-Judge** — [arxiv_ai](https://arxiv.org/abs/2605.10805v1)
- **TrajPrism: A Multi-Task Benchmark for Language-Grounded Urban Trajectory Understanding** — [arxiv_ai](https://arxiv.org/abs/2605.10782v1)
- **Break the Brake, Not the Wheel: Untargeted Jailbreak via Entropy Maximization** — [arxiv_ai](https://arxiv.org/abs/2605.10764v1)
- **MATRA: Modeling the Attack Surface of Agentic AI Systems -- OpenClaw Case Study** — [arxiv_ai](https://arxiv.org/abs/2605.10763v1)
- **GridProbe: Posterior-Probing for Adaptive Test-Time Compute in Long-Video VLMs** — [arxiv_ai](https://arxiv.org/abs/2605.10762v1)
- **Can Muon Fine-tune Adam-Pretrained Models?** — [huggingface_papers](https://arxiv.org/abs/2605.10468)
- **G-Zero: Self-Play for Open-Ended Generation from Zero Data** — [huggingface_papers](https://arxiv.org/abs/2605.09959)
- **Sub-JEPA: Subspace Gaussian Regularization for Stable End-to-End World Models** — [huggingface_papers](https://arxiv.org/abs/2605.09241)
- **TD3B: Transition-Directed Discrete Diffusion for Allosteric Binder Generation** — [huggingface_papers](https://arxiv.org/abs/2605.09810)
- **DeltaRubric: Generative Multimodal Reward Modeling via Joint Planning and Verification** — [huggingface_papers](https://arxiv.org/abs/2605.09269)
- **Make Each Token Count: Towards Improving Long-Context Performance with KV Cache Eviction** — [huggingface_papers](https://arxiv.org/abs/2605.09649)
- **RUBEN: Rule-Based Explanations for Retrieval-Augmented LLM Systems** — [arxiv_cl](https://arxiv.org/abs/2605.10862v1)
- **DECO: Sparse Mixture-of-Experts with Dense-Comparable Performance on End-Side Devices** — [arxiv_cl](https://arxiv.org/abs/2605.10933v1)
- **WildClawBench: A Benchmark for Real-World, Long-Horizon Agent Evaluation** — [arxiv_cl](https://arxiv.org/abs/2605.10912v1)
- **Grounded or Guessing? LVLM Confidence Estimation via Blind-Image Contrastive Ranking** — [arxiv_cl](https://arxiv.org/abs/2605.10893v1)
- **Learning More from Less: Exploiting Counterfactuals for Data-Efficient Chart Understanding** — [arxiv_cl](https://arxiv.org/abs/2605.10855v1)
- **Grounded Satirical Generation with RAG** — [arxiv_cl](https://arxiv.org/abs/2605.10853v1)
- **TMAS: Scaling Test-Time Compute via Multi-Agent Synergy** — [huggingface_papers](https://arxiv.org/abs/2605.10344)
- **CapVector: Learning Transferable Capability Vectors in Parametric Space for Vision-Language-Action Models** — [huggingface_papers](https://arxiv.org/abs/2605.10903)
- **RoboMemArena: A Comprehensive and Challenging Robotic Memory Benchmark** — [huggingface_papers](https://arxiv.org/abs/2605.10921)
- **The Alpha Blending Hypothesis: Compositing Shortcut in Deepfake Detection** — [huggingface_papers](https://arxiv.org/abs/2605.10334)
- **PaperFit: Vision-in-the-Loop Typesetting Optimization for Scientific Documents** — [huggingface_papers](https://arxiv.org/abs/2605.10341)
- **Qwen-Image-2.0 Technical Report** — [huggingface_papers](https://arxiv.org/abs/2605.10730)
- **WorldReasonBench: Human-Aligned Stress Testing of Video Generators as Future World-State Predictors** — [huggingface_papers](https://arxiv.org/abs/2605.10434)
- **Pixal3D: Pixel-Aligned 3D Generation from Images** — [huggingface_papers](https://arxiv.org/abs/2605.10922)
- **Model Merging Scaling Laws in Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2509.24244)
- **Omni-Persona: Systematic Benchmarking and Improving Omnimodal Personalization** — [huggingface_papers](https://arxiv.org/abs/2605.09996)
- **Shaping Schema via Language Representation as the Next Frontier for LLM Intelligence Expanding** — [huggingface_papers](https://arxiv.org/abs/2605.09271)
- **Metal-Sci: A Scientific Compute Benchmark for Evolutionary LLM Kernel Search on Apple Silicon** — [huggingface_papers](https://arxiv.org/abs/2605.09708)
- **Implementing advanced AI technologies in finance** — [mit_tech_review](https://www.technologyreview.com/2026/05/11/1136786/implementing-advanced-ai-technologies-in-finance/)
- **Thinking Machines wants to build an AI that actually listens while it talks** — [techcrunch_ai](https://techcrunch.com/2026/05/11/thinking-machines-wants-to-build-an-ai-that-actually-listens-while-it-talks/)
- **GM just laid off hundreds of IT workers to hire those with stronger AI skills** — [techcrunch_ai](https://techcrunch.com/2026/05/11/gm-just-laid-off-hundreds-of-it-workers-to-hire-those-with-stronger-ai-skills/)
- **Three things in AI to watch, according to a Nobel-winning economist** — [mit_tech_review](https://www.technologyreview.com/2026/05/11/1137090/three-things-in-ai-to-watch-according-to-a-nobel-winning-economist/)
- **Digg tries again, this time as an AI news aggregator** — [techcrunch_ai](https://techcrunch.com/2026/05/11/digg-tries-again-this-time-as-an-ai-news-aggregator/)
- **Fostering breakthrough AI innovation through customer-back engineering** — [mit_tech_review](https://www.technologyreview.com/2026/05/11/1136967/fostering-breakthrough-ai-innovation-through-customer-back-engineering/)
- **Innovation abounds in device charging** — [mit_tech_review](https://www.technologyreview.com/2026/05/11/1136406/innovation-abounds-in-device-charging/)
- **The Download: the hantavirus outbreak and Musk v. Altman week 2** — [mit_tech_review](https://www.technologyreview.com/2026/05/11/1137031/the-download-hantavirus-outbreak-musk-altman-trial/)
- **There aren’t enough rockets for space data centers — Cowboy Space raised $275M to build them** — [techcrunch_ai](https://techcrunch.com/2026/05/11/there-arent-enough-rockets-for-space-data-centers-cowboy-space-raised-275-million-to-build-them/)
- **Riding an AI rally, Robinhood preps second retail venture IPO** — [techcrunch_ai](https://techcrunch.com/2026/05/11/riding-an-ai-rally-robinhood-preps-second-retail-venture-ipo/)
- **How ChatGPT adoption broadened in early 2026** — [openai](https://openai.com/signals/research/2026q1-update)
- **sno-ai/llmix** — [github](https://github.com/sno-ai/llmix)
- **AlexWortega/ai-peer-review-skill** — [github](https://github.com/AlexWortega/ai-peer-review-skill)
- **DeepExperience/HyperEyes** — [github](https://github.com/DeepExperience/HyperEyes)
- **TehreemArbab/JazzCashMCP** — [github](https://github.com/TehreemArbab/JazzCashMCP)
- **kruschdev/krusch-context-mcp** — [github](https://github.com/kruschdev/krusch-context-mcp)
- **Negai-ai/AgentClaw** — [github](https://github.com/Negai-ai/AgentClaw)
- **aqlaboratory/genie3** — [github](https://github.com/aqlaboratory/genie3)
- **ab-613/OpenGravity** — [github](https://github.com/ab-613/OpenGravity)
- **cosmicstack-labs/mercury-agent-skills** — [github](https://github.com/cosmicstack-labs/mercury-agent-skills)
- **PaperGuru-AI/PaperGuru-Benchmark** — [github](https://github.com/PaperGuru-AI/PaperGuru-Benchmark)
- **NikiforovAll/pi-kanban** — [github](https://github.com/NikiforovAll/pi-kanban)
- **xavier-maugendre/n8n-zabbix-glpi-prometheus-agent-qdrant-offline** — [github](https://github.com/xavier-maugendre/n8n-zabbix-glpi-prometheus-agent-qdrant-offline)
- **BerriAI/litellm-agent-platform** — [github](https://github.com/BerriAI/litellm-agent-platform)
- **TsingShui/ida-agent-bridge** — [github](https://github.com/TsingShui/ida-agent-bridge)
- **finewood2008/centaur-loop** — [github](https://github.com/finewood2008/centaur-loop)
- **ZhengrongYue/PAE** — [github](https://github.com/ZhengrongYue/PAE)
- **bitan-del/gcode-harness** — [github](https://github.com/bitan-del/gcode-harness)
- **huck012428-lab/prompt-atlas** — [github](https://github.com/huck012428-lab/prompt-atlas)
- **sanieldoe/companions** — [github](https://github.com/sanieldoe/companions)
- **NitroRCr/gread** — [github](https://github.com/NitroRCr/gread)
- **AI第一金主黄仁勋：日均花掉20亿** — [qbitai](https://www.qbitai.com/2026/05/416540.html)
- **龙虾退烧后，荣耀给它造了一个宇宙** — [qbitai](https://www.qbitai.com/2026/05/416081.html)
- **Markdown要凉…卡帕西也站HTML了** — [qbitai](https://www.qbitai.com/2026/05/416339.html)
- **估值200亿美元！可灵AI被曝剥离快手单独融资** — [qbitai](https://www.qbitai.com/2026/05/416056.html)
- **OpenClaw低调更新重磅版本，龙虾长手长脚了** — [qbitai](https://www.qbitai.com/2026/05/416034.html)
- **做AI漫剧的、搞Agent的、投硅谷的，5.20这些赛道顶流碰头了｜最新嘉宾阵容** — [qbitai](https://www.qbitai.com/2026/05/415263.html)
- **监管要求金融机构完善非法金融活动监测模型，排查重点领域** — [36kr](https://36kr.com/newsflashes/3806125804592904?f=rss)
- **启境汽车完成超10亿元增资，宁德时代等参投** — [36kr](https://36kr.com/newsflashes/3806109201161989?f=rss)
- **市场监管总局附条件批准腾讯收购喜马拉雅股权案** — [36kr](https://36kr.com/newsflashes/3806108609977864?f=rss)
- **宇树科技发布载人机甲，投资人回应** — [36kr](https://36kr.com/newsflashes/3806104284175879?f=rss)
- **空中客车服务公司Satair完成对Unical Aviation及ecube收购** — [36kr](https://36kr.com/newsflashes/3806091599191561?f=rss)
- **Walulu：用六个月撕开一条新赛道** — [36kr](https://36kr.com/p/3805761383751427?f=rss)
- **36氪首发｜新加坡博士团队创业获种子轮融资，首款产品做“会飞的家庭管家”** — [36kr](https://36kr.com/p/3805672617959173?f=rss)
- **8点1氪丨美国总统特朗普：非常期待中国之行  ；OPPO发布母亲节文案事件问责通告；快手计划分拆可灵AI，融资20亿美元** — [36kr](https://36kr.com/p/3805557782486785?f=rss)
- **量子计算走出“科幻片”，「波色量子」在肿瘤、脑机等领域交出百余个落地案例** — [36kr](https://36kr.com/p/3804356346879495?f=rss)
- **氪星晚报 ｜千问与淘宝打通，正式上线AI购物；泡泡玛特将在5月13日举行2026年一季度业务更新电话会** — [36kr](https://36kr.com/p/3804795647729411?f=rss)
- **华虹半导体逆势遭南向资金净卖出6.60亿港元** — [36kr](https://36kr.com/newsflashes/3806138644897536?f=rss)