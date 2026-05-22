# AI 日报 [AI 安全] - 2026-05-22


# AI安全、对齐、隐私与治理每日专题评论
**日期：2026年5月22日**

## 亮点 (Highlights)

今日AI安全领域的学术进展呈现出纵深发展的态势，核心突破主要集中在**隐私保护技术的理论与实践验证**、**对抗鲁棒性评估与攻击新范式**，以及**大模型对齐与安全干预的机理分析**三大方向。首先，一项对苹果公司长期宣称受差分隐私保护的框架的**首次独立客户端审计**，揭示了其实现中的具体缺陷，这一实践性工作对于验证产业级隐私承诺的可信度至关重要。其次，在对抗鲁棒性领域，研究不仅提出了利用编译优化副作用植入后门的**新型攻击向量**，还发展了旨在克服评估方法固有偏差的**新评估范式**，形成了攻击-防御-评估的闭环。最后，关于直接偏好优化（DPO）与人类反馈强化学习（RLHF）理论等价条件的严格证明，以及对思维链（Chain-of-Thought）提示在性别偏见干预中内部机制的剖析，共同深化了我们对模型对齐与安全干预有效性的理解。

---

## 对抗攻击与鲁棒性

今日的工作从攻击、评估和防御三个维度共同揭示了当前模型鲁棒性研究的复杂性。在攻击方面，**《Trusted Weights, Treacherous Optimizations? Optimization-Triggered Backdoor Attacks on LLMs》** 提出了一种极具启发性的攻击框架。作者指出，广泛用于加速推理的编译优化技术，其“语义等价”的假设忽略了数值层面的副作用，而这种副作用可以被恶意利用来植入隐蔽后门。该工作提出了两种互补策略，能够在不修改编译器或硬件的情况下，仅通过精心构造的输入就触发特定的预测错误。这表明，**在部署优化技术时，对优化前后模型行为的数值一致性审计可能比传统的功能测试更为关键**。

评估方面的工作则致力于使鲁棒性测试本身更加可靠和有效。**《SDM: A Powerful Tool for Evaluating Model Robustness》** 指出，现有基于梯度的攻击方法性能受限于“高损失非对抗样本”问题。作者将此归因于攻击目标函数的不恰当设定，并提出了一个新的优化目标，旨在最大化非真实标签概率的总和与真实标签概率之间的差异。作者声称该方法显著提升了攻击成功率。同时，**《Mind Your Margin and Boundary: Are Your Distilled Datasets Truly Robust?》** 从数据角度挑战了现有的鲁棒数据集蒸馏方法。该工作指出，现有方法要么对所有对抗样本一视同仁，忽略了由近零鲁棒边界主导的风险分布，要么未能在攻击集中的决策边界区域显式增加类间分离。作者提出了相应改进，旨在同时提升蒸馏数据集的清洁准确率和鲁棒性。

综合来看，这些工作共同指向一个趋势：**安全评估需要更全面的威胁模型和更精细的优化目标**。新的攻击利用了系统优化栈中未被充分审视的信任链，而新的评估和防御方法则试图纠正现有评估流程中的内在偏差，从而使对模型“鲁棒性”的度量更加贴近真实威胁场景。

## 模型对齐与可解释性

本主题下的研究深入探讨了当前主流对齐方法的理论基础与实际效果之间的差距。**《Conditional Equivalence of DPO and RLHF: Implicit Assumption, Failure Modes, and Provable Alignment》** 从理论层面进行了重要澄清。作者证明了流行的DPO方法与RLHF之间的等价性是**有条件的**，而非普适的。这个条件依赖于一个“RLHF最优策略必须偏好人类偏好的响应”的隐含假设，而该假设在实践中经常被违反。当假设不成立时，DPO优化的可能是相对于参考策略的相对优势，而非与人类偏好的绝对对齐，这可能导致病态收敛。这项工作提醒我们，在采用简化对齐方法时，必须仔细验证其理论前提在特定应用场景下是否成立。

在可解释性与偏见分析方面，**《Mechanics of Bias and Reasoning: Interpreting the Impact of Chain-of-Thought Prompting on Gender Bias in LLMs》** 超越了仅通过基准测试评估偏见变化的范式。作者结合基准测试和机制可解释性方法（如激活修补），深入研究了思维链提示如何影响LLM内部的性别偏见表征。作者声称，他们的发现表明，CoT提示引发的表面行为变化可能并未伴随着模型内在偏见机制的有意义转变，这**挑战了CoT作为一种可靠偏见缓解工具的有效性**。

此外，针对高风险领域的对齐失败研究也颇具警示意义。**《Do No Harm? Hallucination and Actor-Level Abuse in Web-Deployed Medical Large Language Models》** 对大量在线医疗类GPT进行了大规模评估。作者引入了幻觉检测和策略违规评估框架，并声称发现这些模型普遍面临幻觉、不合规和设计不安全等问题。同样，**《Choose Wisely and Privately: Proactive Client Selection for Fair and Efficient Federated Learning》** 虽然聚焦联邦学习，但其核心关注——数据非独立同分布（non-IID）导致的性能下降与不公平问题——也与模型在分布式、多样化数据场景下的对齐挑战直接相关。

## 隐私保护与联邦学习

隐私保护技术今天在联邦学习、差分隐私和理论度量等多个子领域均有显著进展。在联邦学习框架内，**《Causal Unlearning in Collaborative Optimization: Exact and Approximate Influence Reversal under Adversarial Contributions》** 提出了一种高效的“机器遗忘”方法HF-KCU。该方法通过克雷洛夫子空间中的共轭梯度迭代来近似影响函数，将计算复杂度从O(d^3)降低至O(kd)。更重要的是，它引入因果加权机制，确保参数更新仅发送给持有被删除数据的客户端，避免对无关客户端造成扰动。这直接回应了GDPR等隐私法规中的“被遗忘权”要求。

另一方面，**《OmniISR: A Unified Framework for Centralized and Federated Learning via Intermediate Supervision and Regularization》** 试图解决全球化部署中集中式学习（CL）和联邦学习（FL）之间的优化体制矛盾。作者声称提出了一个统一框架，通过中间监督和正则化来弥合两种范式在梯度偏差和内部协变量偏移方面的差异。此外，**《Secure, Verifiable, and Scalable Multi-Client Data Sharing via Consensus-Based Privacy-Preserving Data Distribution》** 提出了一种轻量级的共识数据分发协议，通过双层保护机制（客户端仿射掩码和优先级顺序共识锁）来保障多客户端数据聚合中的机密性，无需持久性可信第三方。

在差分隐私（DP）领域，今日迎来了两项关键工作。**《SMA-DP: Spectral Memory-Aware Differential Privacy for Deep Learning》** 提出了一种新的DP-SGD变体。作者声称，该方法通过引入一个仅基于先前私有化噪声释放构建的分数记忆分支，并利用受WeightWatcher启发的幂律光谱指数作为组级可靠性信号，从而在保持隐私保证的同时降低了更新方差，提升了在复杂数据集上的效用。而一项更具实践影响力的工作 **《Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks》** 则对苹果自2016年以来宣称用于设备分析的DP框架进行了首次独立客户端审计。作者在macOS系统上对框架进行了逆向工程分析，声称发现了其实现中的具体错误和配置问题，并评估了由此带来的实际隐私风险。这项工作极具价值，因为它对产业界一个标志性的隐私承诺进行了可验证的检验。

理论层面，**《Information Leakage Envelopes》** 研究了在点态最大泄漏（PML）框架下，如何定义同时满足后处理稳健性和可上界化失效概率的隐私保证。作者指出，借鉴（近似）差分隐私灵感的两种候选定义都无法同时满足这两点要求，并提出了“PML包络”概念来量化关于秘密的最大信息泄漏量。这为隐私度量理论提供了新的思考方向。

## Agent安全与治理

随着AI Agent能力的增强，其安全性问题日益凸显，今日多篇工作从不同角度对此进行了探讨。一篇立场鲜明的文章 **《Agent Security is a Systems Problem》** 强调，必须将AI模型视为系统中的“不可信组件”，安全不变量必须在系统层面强制执行。作者认为，仅通过提升模型鲁棒性（当前社区主流观点）是不足够的，必须辅以来自操作系统、网络和形式化方法等系统安全领域的技术。这一观点为Agent安全研究提供了重要的范式参考。

在具体评估方面，**《Refusal Evaluation in Coding LLMs and Code Agents: A Systematic Review of Thirteen Malicious-Code Prompt Corpora》** 对13个公开的恶意代码提示语料库进行了系统综述，指出了评估协议、许可条款和可靠性标准的不一致性，为未来构建更可靠的编码Agent安全基准提供了路线图。**《Rethinking Fraud Safety Evaluation: Multi-Round Attacks Reveal Safety-Utility Tradeoffs in Graph-Context LLM Defenders》** 则揭示了单轮安全评估的局限性。在模拟多轮自适应欺诈攻击的场景下，作者发现基于图上下文的防御者虽然能提高早期安全拒绝率，但也产生了更多的良性过度拒绝，这凸显了真实Agent交互中安全与效用之间的根本性权衡。

此外，从具体应用场景看，**《Artificial Pancreas Implantables -- How Healthcare Professionals May Deal With DIY Bio Cases》** 探讨了监管之外的DIY人工胰腺系统带来的安全与治理挑战，而 **《Heartbeat-Bound Hierarchical Credentials: Cryptographic Revocation for AI Agent Swarms》** 则针对Agent蜂群架构提出了新的凭证撤销协议，通过将凭证有效性与父代理的定期活性证明绑定，来解决中心化撤销机制在网络断开时的“僵尸代理”问题。开源社区也贡献了工具，如 **`ai-kill-chain`** 项目，它为LLM和Agent威胁扩展了网络杀伤链模型，增加了模型供应链阶段，为威胁建模提供了实用框架。

## 展望未来 (Looking Forward)

今天的进展虽丰，但也清晰地勾勒出若干亟待突破的理论与实践挑战。首先，**对齐理论的“条件等价性”揭示，当前许多高效对齐方法的理论基础可能比预想中更脆弱**。一个核心的开放问题是：在实践的大规模、复杂偏好数据中，那些使得DPO等效于RLHF的隐含假设在多大程度上成立？如何设计在这些假设失败时依然稳健的对齐算法？

其次，**隐私保护技术正在从“追求可证明的界限”向“确保实际实现的可靠性”演进**。苹果DP审计工作表明，即使拥有强大的理论保证，实现中的细微错误也可能使承诺落空。未来的挑战在于如何建立一套贯穿算法设计、工程实现和独立验证的**端到端隐私保证体系**，特别是对于复杂的深度学习系统。

再者，**“Agent安全是一个系统问题”这一论断提出了一个庞大的跨学科研究议程**。如何为混合了可信硬件、不可信AI模型和动态环境的复杂Agent系统，设计可形式化验证、可动态调整的安全架构？这需要将传统的访问控制、信息流控制、运行时监控与AI的不确定性推理能力深度融合。

最后，AI生成内容（包括文本、图像、视频）的来源认证与溯源，尽管在水印和加密来源方面已有技术进展，但其**在国际法、国内司法和产品监管等多元证据体系中的法律效力与可采纳性**，仍是一个复杂的跨学科难题，需要技术、法律和政策领域的持续对话与共同构建。

---


## 参考来源

- **Causal Unlearning in Collaborative Optimization: Exact and Approximate Influence Reversal under Adversarial Contributions** — [arxiv_lg](https://arxiv.org/abs/2605.20341)
- **Comparative Evaluation of Deep Learning Models for Fake Image Detection** — [arxiv_cr](https://arxiv.org/abs/2605.20971)
- **Choose Wisely and Privately: Proactive Client Selection for Fair and Efficient Federated Learning** — [arxiv_cr](https://arxiv.org/abs/2605.20975)
- **SoK: Critical Evaluation of Quantum Machine Learning for Adversarial Robustness** — [arxiv_cr](https://arxiv.org/abs/2511.14989)
- **It Takes Two: Complementary Self-Distillation for Contextual Integrity in LLMs** — [arxiv_lg](https://arxiv.org/abs/2605.20258)
- **OmniISR: A Unified Framework for Centralized and Federated Learning via Intermediate Supervision and Regularization** — [arxiv_lg](https://arxiv.org/abs/2605.20276)
- **Adaptive Probe-based Steering for Robust LLM Jailbreaking** — [arxiv_cr](https://arxiv.org/abs/2605.20286)
- **Verifiable Provenance and Watermarking for Generative AI: An Evidentiary Framework for International Operational Law and Domestic Courts** — [arxiv_cr](https://arxiv.org/abs/2605.21002)
- **SMA-DP: Spectral Memory-Aware Differential Privacy for Deep Learning** — [arxiv_cr](https://arxiv.org/abs/2605.20450)
- **Secure, Verifiable, and Scalable Multi-Client Data Sharing via Consensus-Based Privacy-Preserving Data Distribution** — [arxiv_cr](https://arxiv.org/abs/2601.00418)
- **Mechanics of Bias and Reasoning: Interpreting the Impact of Chain-of-Thought Prompting on Gender Bias in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.20410)
- **Do No Harm? Hallucination and Actor-Level Abuse in Web-Deployed Medical Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20591)
- **Findings of the Counter Turing Test: AI-Generated Text Detection** — [arxiv_cl](https://arxiv.org/abs/2605.20761)
- **FBOS-RL: Feedback-Driven Bi-Objective Synergistic Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20256)
- **Conformal Selective Acting: Anytime-Valid Risk Control for RLVR-Trained LLMs** — [arxiv_lg](https://arxiv.org/abs/2605.20270)
- **Neural Collapse by Design: Learning Class Prototypes on the Hypersphere** — [arxiv_lg](https://arxiv.org/abs/2605.20302)
- **Decomposing MXFP4 quantization error for LLM reinforcement learning: reducible bias, recoverable deadzone, and an irreducible floor** — [arxiv_lg](https://arxiv.org/abs/2605.20402)
- **Trusted Weights, Treacherous Optimizations? Optimization-Triggered Backdoor Attacks on LLMs** — [arxiv_cr](https://arxiv.org/abs/2605.20641)
- **Information Leakage Envelopes** — [arxiv_cr](https://arxiv.org/abs/2605.21185)
- **Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks** — [arxiv_cr](https://arxiv.org/abs/2605.21378)
- **An exponential mechanism based on quadratic approximations for fine-tuning machine learning models with privacy guarantees** — [arxiv_cr](https://arxiv.org/abs/2605.20521)
- **Agent Security is a Systems Problem** — [arxiv_cr](https://arxiv.org/abs/2605.18991)
- **Synchronization and Turn-Taking in Full-Duplex Speech Dialogue Models** — [arxiv_cl](https://arxiv.org/abs/2605.20356)
- **Regulating Anatomy-Aware Rewards via Trajectory-Integral Feedback for Volumetric Computed Tomography Analysis** — [arxiv_cv](https://arxiv.org/abs/2605.20277)
- **Can Vision Models Truly Forget? Mirage: Representation-Level Certification of Visual Unlearning** — [arxiv_cv](https://arxiv.org/abs/2605.20282)
- **SDM: A Powerful Tool for Evaluating Model Robustness** — [arxiv_cv](https://arxiv.org/abs/2605.20308)
- **Capability $\neq$ Interpretability: Human Interpretability of Vision Foundation Models** — [arxiv_cv](https://arxiv.org/abs/2605.20337)
- **Mind Your Margin and Boundary: Are Your Distilled Datasets Truly Robust?** — [arxiv_cv](https://arxiv.org/abs/2605.20606)
- **Conditional Equivalence of DPO and RLHF: Implicit Assumption, Failure Modes, and Provable Alignment** — [huggingface_papers](https://arxiv.org/abs/2605.20834)
- **Neural Estimation of Pairwise Mutual Information in Masked Discrete Sequence Models** — [arxiv_lg](https://arxiv.org/abs/2605.20187)
- **Geometry-Lite: Interpretable Safety Probing via Layer-Wise Margin Geometry** — [arxiv_lg](https://arxiv.org/abs/2605.20241)
- **GROW: Aligning GRPO with State-Action Modeling for Open-World VLM Agents** — [arxiv_lg](https://arxiv.org/abs/2605.20246)
- **CP-MoE: Consistency-Preserving Mixture-of-Experts for Continual Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20247)
- **Graph Transductive Sharpening: Leveraging Unlabeled Predictions in Node Classification** — [arxiv_lg](https://arxiv.org/abs/2605.20248)
- **Multi-Agent Reinforcement Learning for Safe Autonomous Driving Under Pedestrian Behavioral Uncertainty** — [arxiv_lg](https://arxiv.org/abs/2605.20255)
- **Chronicle: A Multimodal Foundation Model for Joint Language and Time Series Understanding** — [arxiv_lg](https://arxiv.org/abs/2605.20268)
- **Spectral Unforgetting: Post-Hoc Recovery of Damaged Capabilities Without Retraining** — [arxiv_lg](https://arxiv.org/abs/2605.20296)
- **Robust Subspace-Constrained Quadratic Models for Low-Dimensional Structure Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20300)
- **WaveGraphNet: Physics-Consistent Guided-Wave Damage Localization through Coupled Inverse-Forward Graph Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20311)
- **Less Data, Faster Training: repeating smaller datasets speeds up learning via sampling biases** — [arxiv_lg](https://arxiv.org/abs/2605.20314)
- **Symmetrization of Loss Functions for Robust Training of Neural Networks in the Presence of Noisy Labels** — [arxiv_lg](https://arxiv.org/abs/2605.20347)
- **Consistently Informative Soft-Label Temperature for Knowledge Distillation** — [arxiv_lg](https://arxiv.org/abs/2605.20357)
- **Artificial Pancreas Implantables -- How Healthcare Professionals May Deal With DIY Bio Cases** — [arxiv_cr](https://arxiv.org/abs/2605.20208)
- **Refusal Evaluation in Coding LLMs and Code Agents: A Systematic Review of Thirteen Malicious-Code Prompt Corpora (2023-2025)** — [arxiv_cr](https://arxiv.org/abs/2605.20351)
- **Latent Geometry as a Structural Monitor: Eigenspace Alignment for Anomaly Detection in Anonymity Networks** — [arxiv_cr](https://arxiv.org/abs/2605.20391)
- **Detecting Data Exfiltration through I2P Anonymity Networks: A Two-Phase Machine Learning Approach** — [arxiv_cr](https://arxiv.org/abs/2605.20546)
- **Heartbeat-Bound Hierarchical Credentials: Cryptographic Revocation for AI Agent Swarms** — [arxiv_cr](https://arxiv.org/abs/2605.20704)
- **An Application-Layer Multi-Modal Covert-Channel Reference Monitor for LLM Agent Egress** — [arxiv_cr](https://arxiv.org/abs/2605.20734)
- **Rethinking Fraud Safety Evaluation: Multi-Round Attacks Reveal Safety-Utility Tradeoffs in Graph-Context LLM Defenders** — [arxiv_cr](https://arxiv.org/abs/2605.20759)
- **An Evidence-driven Protocol for Trustworthy CI Pipelines** — [arxiv_cr](https://arxiv.org/abs/2605.21089)
- **Shiny Stories, Hidden Struggles: Investigating the Representation of Disability Through the Lens of LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.20191)
- **Leveraging Large Language Models for Sentiment Analysis: Multi-Modal Analysis of Decentraland's MANA Token** — [arxiv_cl](https://arxiv.org/abs/2605.20192)
- **Parallel LLM Reasoning for Bias-Resilient, Robust Conceptual Abstraction** — [arxiv_cl](https://arxiv.org/abs/2605.20194)
- **MedicalBench: Evaluating Large Language Models Toward Improved Medical Concept Extraction** — [arxiv_cl](https://arxiv.org/abs/2605.20197)
- **Under Pressure: Emotional Framing Induces Measurable Behavioral Shifts and Structured Internal Geometry in Small Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20202)
- **DEL: Digit Entropy Loss for Numerical Learning of Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20369)
- **Do as I Say, Not as I Do: Instruction-Induction Conflict in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.20382)
- **Stage-Audit: Auditable Source-Frontier Discovery for Cross-Wiki Tables** — [arxiv_cl](https://arxiv.org/abs/2605.20478)
- **When Irregularity Helps: A Subclass Analysis of Inductive Bias in Neural Morphology** — [arxiv_cl](https://arxiv.org/abs/2605.20558)
- **Divide-Prompt-Refine: a Training-Free, Structure-Aware Framework for Biomedical Abstract Generation** — [arxiv_cl](https://arxiv.org/abs/2605.20628)
- **On the limits and opportunities of AI reviewers: Reviewing the reviews of Nature-family papers with 45 expert scientists** — [arxiv_cl](https://arxiv.org/abs/2605.20668)
- **Beyond Semantic Similarity: A Two-Phase Non-Parametric Retrieval Workflow for Corporate Credit Underwriting** — [arxiv_cl](https://arxiv.org/abs/2605.20684)
- **SCRIBE: Diagnostic Evaluation and Rich Transcription Models for Indic ASR** — [arxiv_cl](https://arxiv.org/abs/2605.20712)
- **MTR-Suite: A Framework for Evaluating and Synthesizing Conversational Retrieval Benchmarks** — [arxiv_cl](https://arxiv.org/abs/2605.20729)
- **Distributional Alignment as a Criterion for Designing Task Vectors in In-Context Learning** — [arxiv_cl](https://arxiv.org/abs/2605.20730)
- **The Illusion of Intervention: Your LLM-Simulated Experiment is an Observational Study** — [arxiv_cl](https://arxiv.org/abs/2605.20767)
- **Co-Fusion4D: Spatio-temporal Collaborative Fusion for Robust 3D Object Detection** — [arxiv_cv](https://arxiv.org/abs/2605.20301)
- **Lighting-aware Unified Model for Instance Segmentation** — [arxiv_cv](https://arxiv.org/abs/2605.20436)
- **Understanding Model Behavior in Monocular Polyp Sizing** — [arxiv_cv](https://arxiv.org/abs/2605.20461)
- **EPC-3D-Diff: Equivariant Physics Consistent Conditional 3D Latent Diffusion for CBCT to CT Synthesis** — [arxiv_cv](https://arxiv.org/abs/2605.20470)
- **MAPS: A Synthetic Dataset for Probing Vision Models in a Controlled 3D Scene Space** — [arxiv_cv](https://arxiv.org/abs/2605.20549)
- **End-to-End Unmixing with Material Prompts for Hyperspectral Object Tracking** — [arxiv_cv](https://arxiv.org/abs/2605.20569)
- **QwenSafe: Multimodal Content Rating Description Identification via Preference-Aligned VLMs** — [arxiv_cv](https://arxiv.org/abs/2605.20584)
- **Head-Aware Key-Value Compression for Efficient Autoregressive Image Generation** — [arxiv_cv](https://arxiv.org/abs/2605.20600)
- **Pareto-Enhanced Portrait Generation: Vision-Aligned Text Supervision for Alignment, Realism, and Aesthetics** — [arxiv_cv](https://arxiv.org/abs/2605.20640)
- **Diversed Model Discovery via Structured Table Discovery** — [huggingface_papers](https://arxiv.org/abs/2605.22766)
- **IndusAgent: Reinforcing Open-Vocabulary Industrial Anomaly Detection with Agentic Tools** — [huggingface_papers](https://arxiv.org/abs/2605.20682)
- **OcclusionFormer: Arranging Z-Order for Layout-Grounded Image Generation** — [huggingface_papers](https://arxiv.org/abs/2605.21343)
- **Leveraging Vision-Language Models to Detect Attention in Educational Videos** — [arxiv_cv](https://arxiv.org/abs/2605.20211)
- **Why Latent Actions Fail, and How to Prevent It** — [arxiv_cv](https://arxiv.org/abs/2605.20223)
- **AI-Assisted Competency Assessment from Egocentric Video in Simulation-Based Nursing Education** — [arxiv_cv](https://arxiv.org/abs/2605.20233)
- **AnimeAdapter: Fine-grained and Consistent Zero-shot Anime Character Generation** — [arxiv_cv](https://arxiv.org/abs/2605.20237)
- **Generation of Heterogeneous PET Images from Uniform Organ Activity Maps Using a Pretrained Domain-Adapted Diffusion Model** — [arxiv_cv](https://arxiv.org/abs/2605.20267)
- **You Don't Need Attention: Gated Convolutional Modeling for Watch-Based Fall Detection** — [arxiv_cv](https://arxiv.org/abs/2605.20275)
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
- **Same Architecture, Different Capacity: Optimizer-Induced Spectral Scaling Laws** — [huggingface_papers](https://arxiv.org/abs/2605.21803)
- **You Only Need Minimal RLVR Training: Extrapolating LLMs via Rank-1 Trajectories** — [huggingface_papers](https://arxiv.org/abs/2605.21468)
- **OCTOPUS: Optimized KV Cache for Transformers via Octahedral Parametrization Under optimal Squared error quantization** — [huggingface_papers](https://arxiv.org/abs/2605.21226)
- **iTryOn: Mastering Interactive Video Virtual Try-On with Spatial-Semantic Guidance** — [huggingface_papers](https://arxiv.org/abs/2605.21431)
- **DrawMotion: Generating 3D Human Motions by Freehand Drawing** — [huggingface_papers](https://arxiv.org/abs/2605.20955)
- **PlanningBench: Generating Scalable and Verifiable Planning Data for Evaluating and Training Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.20873)
- **Roundtables: Can AI Learn to Understand the World?** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137756/roundtables-can-ai-learn-to-understand-the-world/)
- **Scaling creativity in the age of AI** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137613/scaling-creativity-in-the-age-of-ai/)
- **Spotify and Universal Music strike deal allowing fan-made AI covers and remixes** — [techcrunch_ai](https://techcrunch.com/2026/05/21/spotify-and-universal-music-strike-deal-allowing-fan-made-ai-covers-and-remixes/)
- **Trump delays AI security executive order, saying language ‘could have been a blocker’** — [techcrunch_ai](https://techcrunch.com/2026/05/21/trump-delays-ai-security-executive-order-i-dont-want-to-get-in-the-way-of-that-leading/)
- **Anthropic’s Code with Claude showed off coding’s future—whether you like it or not** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137735/anthropics-code-with-claude-showed-off-codings-future-whether-you-like-it-or-not/)
- **The Download: online safety’s future and climate tech’s big pivot** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137733/the-download-online-safety-climate-tech-pivot/)
- **Hark raises $700M Series A for its secretive ‘universal’ AI interface** — [techcrunch_ai](https://techcrunch.com/2026/05/21/hark-raises-700m-series-a-for-its-secretive-universal-ai-interface/)
- **Google is pitching an AI agent ecosystem to consumers who may not buy it** — [techcrunch_ai](https://techcrunch.com/2026/05/21/google-is-pitching-an-ai-agent-ecosystem-to-consumers-who-may-not-buy-it/)
- **Climate tech companies are pivoting to critical minerals** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137622/climate-tech-pivot-critical-minerals/)
- **Tech researchers are suing the Trump administration over the future of online safety** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137632/lawsuit-trump-administration-online-safety-coalition-for-independent-technology-research/)
- **Six search engines worth trying now that Google isn’t really Google anymore** — [techcrunch_ai](https://techcrunch.com/2026/05/21/six-search-engines-worth-trying-now-that-google-isnt-really-google-anymore/)
- **Spotify adds AI-powered Q&A and briefing generation features to podcasts** — [techcrunch_ai](https://techcrunch.com/2026/05/21/spotify-adds-ai-powered-qa-and-briefing-generation-features-to-podcasts/)
- **Spotify takes on Google’s NotebookLM with its new app** — [techcrunch_ai](https://techcrunch.com/2026/05/21/spotify-debuts-a-new-desktop-app-for-creating-personal-podcasts/)
- **Spotify launches an ElevenLabs-powered audiobook creation tool** — [techcrunch_ai](https://techcrunch.com/2026/05/21/spotify-launches-an-elevenlabs-powered-audiobook-creation-tool/)
- **The Path, founded by Tony Robbins and Calm alums, hopes to offer safer AI therapy** — [techcrunch_ai](https://techcrunch.com/2026/05/21/the-path-founded-by-tony-robbins-and-calm-alums-wants-to-offer-safer-ai-therapy/)
- **With aluminum prices up 20%, recycling startups bet on AI to cash in** — [techcrunch_ai](https://techcrunch.com/2026/05/21/with-aluminum-prices-up-20-recycling-startups-bet-on-ai-to-cash-in/)
- **AdventHealth advances whole-person care with OpenAI** — [openai](https://openai.com/index/adventhealth)
- **We’re launching the Google DeepMind Accelerator program in Asia Pacific to tackle environmental risks** — [deepmind](https://deepmind.google/blog/were-launching-the-google-deepmind-accelerator-program-in-asia-pacific-to-tackle-environmental-risks/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **ganimjeong/Harness-for-codex** — [github](https://github.com/ganimjeong/Harness-for-codex)
- **wailers9/bragi** — [github](https://github.com/wailers9/bragi)
- **5bv57zcm44-max/NOXUS-AI-Open-WhatsApp** — [github](https://github.com/5bv57zcm44-max/NOXUS-AI-Open-WhatsApp)
- **gouravnagar-infosec/ai-kill-chain** — [github](https://github.com/gouravnagar-infosec/ai-kill-chain)
- **MarbleRoller/Ads-Power-Crack-Latest-TS** — [github](https://github.com/MarbleRoller/Ads-Power-Crack-Latest-TS)
- **tuchg/Lucarne** — [github](https://github.com/tuchg/Lucarne)
- **ayush016/android-lead-agent-skills** — [github](https://github.com/ayush016/android-lead-agent-skills)
- **kingbootoshi/directional-prompting** — [github](https://github.com/kingbootoshi/directional-prompting)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **zimingttkx/QuantumFlow** — [github](https://github.com/zimingttkx/QuantumFlow)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **c4pt0r/pie** — [github](https://github.com/c4pt0r/pie)
- **lywnl/ai-app-generation** — [github](https://github.com/lywnl/ai-app-generation)
- **madguyevans-creator/resale-agent-skill-hub** — [github](https://github.com/madguyevans-creator/resale-agent-skill-hub)
- **h4ckf0r0day/awesome-ai-web-scraping** — [github](https://github.com/h4ckf0r0day/awesome-ai-web-scraping)
- **ForgeAILab/forge** — [github](https://github.com/ForgeAILab/forge)
- **hasanyilmaz/operon** — [github](https://github.com/hasanyilmaz/operon)
- **AI4MSE/Parallax** — [github](https://github.com/AI4MSE/Parallax)
- **The Matching Principle: A Geometric Theory of Loss Functions for Nuisance-Robust Representation Learning** — [arxiv_ml](https://arxiv.org/abs/2605.22800v1)
- **39万！雷军发布小米最贵SUV** — [qbitai](https://www.qbitai.com/2026/05/422088.html)
- **联想集团Q4营收利润双创新高，兑现历史最佳财年** — [qbitai](https://www.qbitai.com/2026/05/422127.html)
- **腾讯混元开源全新翻译模型Hy-MT2 ，上线小程序「腾讯Hy翻译」** — [qbitai](https://www.qbitai.com/2026/05/422068.html)
- **菲尔兹奖得主都看懵了：OpenAI非数学模型首次自主突破80年未解数学难题** — [qbitai](https://www.qbitai.com/2026/05/422032.html)
- **风行在线CEO易正朝：先全员Coding，再All in众创丨AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/422001.html)
- **Artificial Analysis放榜：千问3.7问鼎国产模型冠军，全球前五** — [qbitai](https://www.qbitai.com/2026/05/422009.html)
- **AI首次实现中国风光发电普查，北大、阿里达摩院研究登上《自然》** — [qbitai](https://www.qbitai.com/2026/05/422002.html)
- **上海交大AI教授亲授：半天带你拆解Agent底层逻辑** — [qbitai](https://www.qbitai.com/2026/05/421697.html)
- **得场景者得AI天下，出行赛道跑出了一家值得关注的数据玩家** — [qbitai](https://www.qbitai.com/2026/05/421694.html)
- **520当天400万AI人，都在量子位听这近20场演讲&对谈｜第四届中国AIGC产业峰会** — [qbitai](https://www.qbitai.com/2026/05/421691.html)
- **Proxy-Based Approximation of Shapley and Banzhaf Interactions** — [arxiv_ml](https://arxiv.org/abs/2605.22738v1)
- **The efficiency-gain illusion: People underestimate the rate of AI use and overestimate its benefits on simple tasks** — [arxiv_cy](https://arxiv.org/abs/2605.22687v1)
- **A Martingale Kernel Independence Test** — [arxiv_ml](https://arxiv.org/abs/2605.22549v1)
- **Generative Modeling by Value-Driven Transport** — [arxiv_ml](https://arxiv.org/abs/2605.22507v1)
- **Do Not Trust The Auctioneer: Learning to Bid in Feedback-Manipulated Auctions** — [arxiv_ml](https://arxiv.org/abs/2605.22438v1)
- **AI-Enabled Serious Games: Integrating Intelligence and Adaptivity in Training Systems** — [arxiv_cy](https://arxiv.org/abs/2605.21962v1)
- **Detecting Offensive Cyber Agents: A Detection-in-Depth Approach** — [arxiv_cy](https://arxiv.org/abs/2605.21956v1)
- **Finite-Particle Convergence Rates for Conservative and Non-Conservative Drifting Models** — [arxiv_ml](https://arxiv.org/abs/2605.22795v1)
- **SDPM: Survival Diffusion Probabilistic Model for Continuous-Time Survival Analysis** — [arxiv_ml](https://arxiv.org/abs/2605.22776v1)
- **Uniform Diffusion Models Revisited: Leave-One-Out Denoiser and Absorbing State Reformulation** — [arxiv_ml](https://arxiv.org/abs/2605.22765v1)
- **Plug-in Losses for Evidential Deep Learning: A Simplified Framework for Uncertainty Estimation that Includes the Softmax Classifier** — [arxiv_ml](https://arxiv.org/abs/2605.22746v1)
- **Multiple Neural Operators Achieve Near-Optimal Rates for Multi-Task Learning** — [arxiv_ml](https://arxiv.org/abs/2605.22724v1)
- **Beyond Temperature: Hyperfitting as a Late-Stage Geometric Expansion** — [arxiv_ml](https://arxiv.org/abs/2605.22579v1)
- **Healthcare LLM Benchmarks Are Only as Good as Their Explicit Assumptions** — [arxiv_cy](https://arxiv.org/abs/2605.22612v1)
- **Guiding Multi-Objective Genetic Programming with Description Length Improves Symbolic Regression Solutions** — [arxiv_ml](https://arxiv.org/abs/2605.22374v1)
- **Departure from Regularity: Degree Heterogeneity and Eigengap as the Structural Drivers of ASE-LSE Latent Subspace Disagreement** — [arxiv_ml](https://arxiv.org/abs/2605.22346v1)
- **From Sequential Nodes to GPU Batches: Parallel Branch and Bound for Optimal $k$-Sparse GLMs** — [arxiv_ml](https://arxiv.org/abs/2605.22188v1)
- **Aerodynamic force reconstruction using physics-informed Gaussian processes** — [arxiv_ml](https://arxiv.org/abs/2605.22111v1)
- **Uniform-in-Time Weak Propagation-of-Chaos in Shallow Neural Networks** — [arxiv_ml](https://arxiv.org/abs/2605.22010v1)
- **Epicure: Navigating the Emergent Geometry of Food Ingredient Embeddings** — [arxiv_cy](https://arxiv.org/abs/2605.22391v1)
- **Perception or Prejudice: Can MLLMs Go Beyond First Impressions of Personality?** — [arxiv_cy](https://arxiv.org/abs/2605.22109v1)
- **博坦发布全新旗舰无人机ATOM 3** — [36kr](https://36kr.com/newsflashes/3819844675031427?f=rss)
- **中信证券：解决新型电力系统复杂“三体”问题，绿电直连从“点对点”到“点对群”** — [36kr](https://36kr.com/newsflashes/3819729670508936?f=rss)
- **「闹剧场」阿球：一个同济土木生转行，想把喜剧变成可批量复制的科学｜独家对谈** — [36kr](https://36kr.com/p/3816066708872713?f=rss)
- **中信证券：具身智能、半导体、AI上游装备&材料、世界杯的主题热情有望爆发** — [36kr](https://36kr.com/newsflashes/3819720760217733?f=rss)
- **8点1氪丨“拉勾网”被曝主动申请破产；特斯拉Model S和X正式停产退役；三星内存工人，奖金或达280万元** — [36kr](https://36kr.com/p/3819709302329735?f=rss)
- **氪星晚报｜马斯克旗下SpaceX启动史上最大规模IPO计划；全国首张综合性司机服务地图上线；海关总署在粤发布《海关支持粤港澳大湾区建设若干措施》** — [36kr](https://36kr.com/p/3816942732133510?f=rss)
- **新石器NewClaw：AI一体化解决方案，零门槛当无人车指挥官| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818927367046018?f=rss)
- **业绩快报 | 唯品会一季度净营收266亿元，SVIP用户贡献超50%线上销售额** — [36kr](https://36kr.com/p/3818915823764610?f=rss)
- **从概念到产线一：AI在工业制造领域的深水区探索| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818903062004870?f=rss)
- **城市级AI服务：从试点到常态化，机器人的实景作战与规模化落地| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818889074557829?f=rss)
- **36氪x PureblueAI清蓝战略合作启动仪式暨《2026消费品牌AI推荐力名册》发布 | 2026 AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818877539091333?f=rss)
- **把确定性，写进农业：四个外行、两次失败、三千万学费换来的答案| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818800487679111?f=rss)
- **从算力到价值：AI时代的基础设施重构与产业增长新引擎| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3817502775329667?f=rss)
- **摩根大通期货潘凤：已有境外机构启动国债期货投资计划与套保报备** — [36kr](https://36kr.com/newsflashes/3819802311577736?f=rss)
- **两市融资余额减少83.53亿元** — [36kr](https://36kr.com/newsflashes/3819748426453380?f=rss)
- **From Betting to Empirical Bernstein LIL** — [arxiv_ml](https://arxiv.org/abs/2605.22124v1)