# AI 日报 [AI 安全] - 2026-05-11


# 2026-05-11 AI 安全与治理每日综述

## Highlights

当日学术进展的核心突破集中在**对抗攻击检测机制**与**对齐理论的严谨性**两个维度。在安全评估方面，**Activation Differences Reveal Backdoors: A Comparison of SAE Architectures** 提出利用稀疏自编码器（Sparse Autoencoder）架构差异来隔离微调模型中的后门特征，为基于机制可解释性的后门检测提供了新的实证路径。与此同时，**Position: Mechanistic Interpretability Must Disclose Identification Assumptions for Causal Claims** 一文对当前机制可解释性研究中的因果宣称提出了严峻的方法论挑战，指出大量论文在缺乏明确识别假设的情况下报告因果支持，这要求社区重新审视可解释性结论的可靠性。此外，**Cross-Modal Backdoors in Multimodal Large Language Models** 揭示了多模态大模型中轻量级连接器（Connector）作为供应链攻击面的新风险，表明现有的安全研究过度关注骨干网络而忽视了组件集成的脆弱性。产业层面，**千问与淘宝打通，正式上线 AI 购物** 的落地标志着大模型在复杂商业闭环中的深度应用，这对 Agent 的安全评估与合规性提出了更紧迫的现实需求。

## 对抗攻击与鲁棒性：从特征隔离到供应链攻击

当前的对抗攻击研究正从单一模态向多模态及 Agent 交互场景延伸，攻击面显著扩大。**Activation Differences Reveal Backdoors: A Comparison of SAE Architectures** 与 **Cross-Modal Backdoors in Multimodal Large Language Models** 共同揭示了模型内部特征与外部组件的脆弱性。前者通过对比 Crosscoders 与 Differential SAEs 两种稀疏自编码器架构，在受控的 SQL 注入后门实验中展示了隔离触发特征的能力，证明了机制可解释性工具在安全审计中的潜力。后者则转向了多模态大模型的供应链安全，指出攻击者仅需污染连接器（Connector）即可激活跨模态后门，这种攻击方式比直接污染骨干网络更具隐蔽性且成本更低。这两项工作互为补充，前者关注模型内部特征的检测，后者关注外部组件的集成风险，共同指向了模型全生命周期的安全防御需求。

在 Agent 安全领域，**OrchJail: Jailbreaking Tool-Calling Text-to-Image Agents by Orchestration-Guided Fuzzing** 针对工具调用型 Agent 提出了新的攻击框架。该研究指出，即使单个工具调用是良性的，通过编排（Orchestration）组合多个步骤也可能产生有害输出，传统的提示词注入（Prompt Injection）技术对此无效。OrchJail 通过 fuzzing 学习高风险的工具编排模式，成功突破了现有防御。这一发现与 **Vaporizer: Breaking Watermarking Schemes for Large Language Model Outputs** 的研究相呼应，后者表明现有的 LLM 输出水印方案在面对语义保持的修改攻击（如机器翻译、神经改写）时并不如宣称的那样鲁棒。这些工作共同表明，随着 Agent 能力的增强，攻击者正从直接对抗模型转向利用系统编排和语义变换来规避检测，防御策略需要从静态的模型权重保护转向动态的行为监控与水印增强。

## 模型对齐与可解释性：理论严谨性与 RL 优化

对齐理论的研究正经历从经验主义向理论严谨性的转变。**Position: Mechanistic Interpretability Must Disclosure Identification Assumptions for Causal Claims** 对当前机制可解释性文献进行了目的性审计，发现绝大多数论文在报告忠实度（Faithfulness）或消融实验（Ablation）结果时，未明确陈述使其成为因果证据的识别假设。这一批评直指当前可解释性研究的痛点，即混淆了相关性证据与因果证明。相比之下，**Interpreting Reinforcement Learning Agents with Susceptibilities** 提出了一种基于 Susceptibilities 的 RL 代理可解释性技术，通过研究损失扰动对后验期望值的影响，揭示了参数空间中无法通过策略发展直接观察到的内部特征。这两种路径虽然方法不同，但都强调了对模型内部状态进行更严谨的数学描述，而非仅依赖黑盒的行为观察。

在强化学习与对齐优化方面，**Your Language Model is Its Own Critic: Reinforcement Learning with Value Estimation from Actor's Internal States** 与 **Rubric-Grounded RL: Structured Judge Rewards for Generalizable Reasoning** 提出了降低训练成本与优化奖励信号的新思路。前者利用策略模型的前向传播内部信号来估计价值函数，避免了 PPO 中需要独立 Critic 模型的高昂计算成本。后者则主张将奖励分解为可验证的加权标准，通过冻结的 LLM 裁判生成结构化多标准奖励，而非单一的 holistic score。此外，**Beyond Pairs: Your Language Model is Secretly Optimizing a Preference Graph** 提出了图直接偏好优化（GraphDPO），指出传统的成对偏好优化（DPO）在处理多轮次数据时丢弃了传递性信息，可能导致优化不稳定。这些工作共同指向了 RLHF 与 DPO 的改进方向：即如何在保持训练稳定性的同时，更精细地利用奖励信号与偏好结构。值得注意的是，**Post-training makes large language models less human-like** 的研究发现，后训练阶段虽然提升了模型的任务表现，却系统性地降低了模型与人类行为的一致性，这为评估对齐效果提供了新的视角，即“有用性”与“拟人性”之间可能存在权衡。

## 隐私保护与联邦学习：策略响应与单样本学习

联邦学习（Federated Learning, FL）场景下的隐私与安全问题呈现出新的复杂性。**Graph Representation Learning Augmented Model Manipulation on Federated Fine-Tuning of LLMs** 指出，在联邦微调（FFT）中，恶意参与者可以通过上传操纵的模型更新来破坏聚合过程，提出了 AugMP 策略来增强鲁棒性。这与 **Differentially Private Auditing Under Strategic Response** 的研究形成呼应，后者将隐私约束下的审计形式化为双层 Stackelberg 博弈，指出被审计方会策略性地响应审计接口，审计设计需考虑这种博弈行为。这两项工作强调了在分布式环境中，安全威胁不仅来自外部攻击者，也来自参与者的策略性互动。

在数据稀缺与隐私保护的平衡上，**Modulated learning for private and distributed regression with just a single sample per client device** 解决了单样本客户端学习的难题，指出标准联邦学习范式在单样本场景下失效，提出了调制学习（Modulated learning）方法。同时，**INO-SGD: Addressing Utility Imbalance under Individualized Differential Privacy** 探讨了个体化差分隐私（IDP）下的效用不平衡问题，指出高敏感度数据所有者往往要求更强的隐私保护，导致模型效用下降。这些研究共同揭示了在保护隐私的同时维持模型性能的挑战，特别是在数据分布不均或样本极少的情况下。此外，**ADKO: Agentic Decentralized Knowledge Optimization** 提出了一种去中心化知识优化框架，允许智能体通过知识令牌（Knowledge Tokens）进行通信而非共享原始数据，为隐私保护下的多智能体协作提供了新的范式。

## 安全评估基准与 Agent 治理

随着 Agent 在现实世界任务中的部署，评估基准正从单纯的能力测试转向安全与合规性测试。**Safe, or Simply Incapable? Rethinking Safety Evaluation for Phone-Use Agents** 提出了 PhoneSafety 基准，旨在区分 Agent 的安全行为是源于风险识别还是能力缺失。该基准包含 700 个来自真实手机交互的安全关键时刻，指出现有评估往往将“拒绝执行”与“无法执行”混为一谈，导致无法针对性地修复安全问题。**DRIP-R: A Benchmark for Decision-Making and Reasoning Under Real-World Policy Ambiguity in the Retail Domain** 则关注政策模糊性下的决策评估，指出现有基准假设政策是明确指定的，而现实场景中存在多种有效解释，DRIP-R 通过构建政策模糊场景填补了这一评估空白。

在 Agent 的长期行为治理方面，**Ask Early, Ask Late, Ask Right: When Does Clarification Timing Matter for Long-Horizon Agents?** 研究了澄清时机对长程 Agent 的影响，指出早期错误假设可能导致不可逆的错误，但过早澄清可能降低效率。该研究通过强制注入框架量化了澄清价值随执行过程的变化。**Conformal Path Reasoning: Trustworthy Knowledge Graph Question Answering via Path-Level Calibration** 则引入了共形预测（Conformal Prediction）框架，为知识图谱问答提供了统计保证的覆盖范围，解决了现有方法校准有效性不足的问题。这些基准与框架的提出，标志着 AI 安全评估正从静态的模型测试转向动态的、基于场景的、具有统计保证的治理体系。

## 产业动态与开源工具

产业界在 AI 安全与基础设施方面的投入持续增加，开源社区也在快速响应安全需求。在开源工具方面，**AlexWortega/ai-peer-review-skill** 提供了基于多审查者机制的学术论文同行评审工具，有助于提升学术成果的安全性评估。**Negai-ai/AgentClaw** 与 **cosmicstack-labs/mercury-agent-skills** 等仓库展示了 Agent 技能库与工作流编排的标准化趋势，这为 Agent 的安全测试提供了可复用的环境。值得注意的是，**Vaporizer** 等研究揭示了水印技术的脆弱性，这可能会影响 **AlexWortega/ai-peer-review-skill** 等工具在版权保护方面的实际应用效果。

在产业新闻方面，**千问与淘宝打通，正式上线 AI 购物** 标志着大模型在电商闭环中的深度集成。虽然这一进展展示了 AI 在复杂任务中的潜力，但也引入了新的安全风险，如 **OrchJail** 所揭示的工具编排攻击可能在购物 Agent 中通过组合搜索、比价、下单等步骤实现恶意操作。对于 **36 氪** 等媒体关于 MiniMax 增资或 SK 海力士奖金的报道，应视为一般商业动态，而非直接的技术安全信号。特别是关于 **MiniMax** 的融资消息，虽然显示行业热度，但需警惕将商业估值与模型安全能力混淆。在硬件安全方面，**CCX: Enabling Unmodified Intel SGX Applications on Arm CCA** 与 **TENNOR: Trustworthy Execution for Neural Networks through Obliviousness and Retrievals** 提供了在异构硬件上实现可信执行环境的新方案，这对于保护云端训练中的敏感数据至关重要。

## Looking Forward

尽管当日研究在攻击检测、对齐理论与隐私保护方面取得了显著进展，但仍存在若干未解决的理论问题。首先，**Position: Mechanistic Interpretability Must Disclose Identification Assumptions for Causal Claims** 所提出的方法论挑战尚未得到系统性解决，如何在不依赖强假设的情况下建立可解释性与因果性之间的桥梁，仍是机制可解释性领域的核心难题。其次，在联邦学习场景中，**Differentially Private Auditing Under Strategic Response** 指出的博弈行为与 **Graph Representation Learning Augmented Model Manipulation on Federated Fine-Tuning of LLMs** 中的模型操纵威胁，表明现有的防御机制在应对智能对手时可能失效，需要发展更具适应性的动态防御策略。最后，**Vaporizer** 揭示的水印脆弱性与 **Cross-Modal Backdoors** 的供应链风险，提示我们需要重新思考生成式模型的安全认证标准，未来的研究应关注如何构建抗篡改的、端到端的安全验证框架，而不仅仅是针对单一组件的防护。

---


## 参考来源

- **Activation Differences Reveal Backdoors: A Comparison of SAE Architectures** — [arxiv_cr](https://arxiv.org/abs/2605.07324v1)
- **Flow-OPD: On-Policy Distillation for Flow Matching Models** — [arxiv_ai](https://arxiv.org/abs/2605.08063v1)
- **Position: Mechanistic Interpretability Must Disclose Identification Assumptions for Causal Claims** — [arxiv_ai](https://arxiv.org/abs/2605.08012v1)
- **Graph Representation Learning Augmented Model Manipulation on Federated Fine-Tuning of LLMs** — [arxiv_lg](https://arxiv.org/abs/2605.07961v1)
- **Differentially Private Auditing Under Strategic Response** — [arxiv_cr](https://arxiv.org/abs/2605.07674v1)
- **Modulated learning for private and distributed regression with just a single sample per client device** — [arxiv_cr](https://arxiv.org/abs/2605.07233v1)
- **INO-SGD: Addressing Utility Imbalance under Individualized Differential Privacy** — [arxiv_ai](https://arxiv.org/abs/2605.07930v1)
- **KL for a KL: On-Policy Distillation with Control Variate Baseline** — [arxiv_ai](https://arxiv.org/abs/2605.07865v1)
- **On the Tradeoffs of On-Device Generative Models in Federated Predictive Maintenance Systems** — [arxiv_ai](https://arxiv.org/abs/2605.07860v1)
- **GazeVLM: Active Vision via Internal Attention Control for Multimodal Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.07817v1)
- **Interpreting Reinforcement Learning Agents with Susceptibilities** — [arxiv_lg](https://arxiv.org/abs/2605.08007v1)
- **Enhancing Federated Quadruplet Learning: Stochastic Client Selection and Embedding Stability Analysis** — [arxiv_lg](https://arxiv.org/abs/2605.07888v1)
- **ADKO: Agentic Decentralized Knowledge Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.07863v1)
- **GLiGuard: Schema-Conditioned Classification for LLM Safeguard** — [arxiv_cl](https://arxiv.org/abs/2605.07982v1)
- **An Automated Framework for Cybersecurity Policy Compliance Assessment Against Security Control Standards** — [arxiv_cr](https://arxiv.org/abs/2605.07515v1)
- **Cross-Modal Backdoors in Multimodal Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.07490v1)
- **DRIP-R: A Benchmark for Decision-Making and Reasoning Under Real-World Policy Ambiguity in the Retail Domain** — [arxiv_cl](https://arxiv.org/abs/2605.07699v1)
- **Quality-Conditioned Agreement in Automated Short Answer Scoring: Mid-Range Degradation and the Impact of Task-Specific Adaptation** — [arxiv_cl](https://arxiv.org/abs/2605.07647v1)
- **MAVEN: Multi-Agent Verification-Elaboration Network with In-Step Epistemic Auditing** — [arxiv_cl](https://arxiv.org/abs/2605.07646v1)
- **Your Language Model is Its Own Critic: Reinforcement Learning with Value Estimation from Actor's Internal States** — [arxiv_cl](https://arxiv.org/abs/2605.07579v1)
- **Rubric-Grounded RL: Structured Judge Rewards for Generalizable Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.08061v1)
- **Beyond Pairs: Your Language Model is Secretly Optimizing a Preference Graph** — [arxiv_ai](https://arxiv.org/abs/2605.08037v1)
- **MPD$^2$-Router: Mask-aware Multi-expert Prior-regularized Dual-head Deferral Router in Glaucoma Screening and Diagnosis** — [arxiv_ai](https://arxiv.org/abs/2605.08024v1)
- **Globally Optimal Training of Spiking Neural Networks via Parameter Reconstruction** — [arxiv_ai](https://arxiv.org/abs/2605.08022v1)
- **Reason to Play: Behavioral and Brain Alignment Between Frontier LRMs and Human Game Learners** — [arxiv_ai](https://arxiv.org/abs/2605.08019v1)
- **Graph-Structured Hyperdimensional Computing for Data-Efficient and Explainable Process-Structure-Property Prediction** — [arxiv_ai](https://arxiv.org/abs/2605.07999v1)
- **The Limits of AI-Driven Allocation: Optimal Screening under Aleatoric Uncertainty** — [arxiv_ai](https://arxiv.org/abs/2605.07979v1)
- **Exploring the non-convexity in machine learning using quantum-inspired optimization** — [arxiv_ai](https://arxiv.org/abs/2605.07947v1)
- **TAVIS: A Benchmark for Egocentric Active Vision and Anticipatory Gaze in Imitation Learning** — [arxiv_ai](https://arxiv.org/abs/2605.07943v1)
- **One Token Per Frame: Reconsidering Visual Bandwidth in World Models for VLA Policy** — [arxiv_ai](https://arxiv.org/abs/2605.07931v1)
- **What if AI systems weren't chatbots?** — [arxiv_ai](https://arxiv.org/abs/2605.07896v1)
- **\mathsf{VISTA}: Decentralized Machine Learning in Adversary Dominated Environments** — [arxiv_ai](https://arxiv.org/abs/2605.07841v1)
- **PPI-Net connects molecular protein interactions to functional processes in disease** — [arxiv_ai](https://arxiv.org/abs/2605.07838v1)
- **Approximation-Free Differentiable Oblique Decision Trees** — [arxiv_ai](https://arxiv.org/abs/2605.07837v1)
- **Normalizing Trajectory Models** — [arxiv_lg](https://arxiv.org/abs/2605.08078v1)
- **Zero-Shot Imagined Speech Decoding via Imagined-to-Listened MEG Mapping** — [arxiv_lg](https://arxiv.org/abs/2605.08075v1)
- **GRAPHLCP: Structure-Aware Localized Conformal Prediction on Graphs** — [arxiv_lg](https://arxiv.org/abs/2605.08074v1)
- **Reinforcement Learning for Exponential Utility: Algorithms and Convergence in Discounted MDPs** — [arxiv_lg](https://arxiv.org/abs/2605.08053v1)
- **STEPS: A Temporal Smooth Error Propagation Solver on the Manifolds for Test-Time Adaptation in Time Series Forecasting** — [arxiv_lg](https://arxiv.org/abs/2605.08005v1)
- **Self-Play Enhancement via Advantage-Weighted Refinement in Online Federated LLM Fine-Tuning with Real-Time Feedback** — [arxiv_lg](https://arxiv.org/abs/2605.07977v1)
- **FLAM: Evaluating Model Performance with Aggregatable Measures in Federated Learning** — [arxiv_lg](https://arxiv.org/abs/2605.07962v1)
- **Slowly Annealed Langevin Dynamics: Theory and Applications to Training-Free Guided Generation** — [arxiv_lg](https://arxiv.org/abs/2605.07950v1)
- **Flatness and Gradient Alignment Are Both Necessary: Spectral-Aware Gradient-Aligned Exploration for Multi-Distribution Learning** — [arxiv_lg](https://arxiv.org/abs/2605.07914v1)
- **Adaptive Regularization for Sparsity Control in Bregman-Based Optimizers** — [arxiv_lg](https://arxiv.org/abs/2605.07892v1)
- **Accurate and Efficient Statistical Testing for Word Semantic Breadth** — [arxiv_cl](https://arxiv.org/abs/2605.08048v1)
- **Beyond "I cannot fulfill this request": Alleviating Rigid Rejection in LLMs via Label Enhancement** — [arxiv_cl](https://arxiv.org/abs/2605.07883v1)
- **Quotient Semivalues for False-Name-Resistant Data Attribution** — [arxiv_cr](https://arxiv.org/abs/2605.07663v1)
- **CCX: Enabling Unmodified Intel SGX Applications on Arm CCA** — [arxiv_cr](https://arxiv.org/abs/2605.07548v1)
- **OrchJail: Jailbreaking Tool-Calling Text-to-Image Agents by Orchestration-Guided Fuzzing** — [arxiv_cr](https://arxiv.org/abs/2605.07414v1)
- **Game-Theoretic Analysis of Transaction Selection in DAG-Based Distributed Ledgers** — [arxiv_cr](https://arxiv.org/abs/2605.07387v1)
- **TENNOR: Trustworthy Execution for Neural Networks through Obliviousness and Retrievals** — [arxiv_cr](https://arxiv.org/abs/2605.07160v1)
- **TextLDM: Language Modeling with Continuous Latent Diffusion** — [arxiv_cl](https://arxiv.org/abs/2605.07748v1)
- **SOD: Step-wise On-policy Distillation for Small Language Model Agents** — [arxiv_cl](https://arxiv.org/abs/2605.07725v1)
- **SimCT: Recovering Lost Supervision for Cross-Tokenizer On-Policy Distillation** — [arxiv_cl](https://arxiv.org/abs/2605.07711v1)
- **Guidance Is Not a Hyperparameter: Learning Dynamic Control in Diffusion Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.07701v1)
- **Post-training makes large language models less human-like** — [arxiv_cl](https://arxiv.org/abs/2605.07632v1)
- **Safe, or Simply Incapable? Rethinking Safety Evaluation for Phone-Use Agents** — [arxiv_cl](https://arxiv.org/abs/2605.07630v1)
- **Is She Even Relevant? When BERT Ignores Explicit Gender Cues** — [arxiv_cl](https://arxiv.org/abs/2605.07622v1)
- **Intent-Driven Semantic ID Generation for Grounded Conversational News Recommendation** — [arxiv_cl](https://arxiv.org/abs/2605.07613v1)
- **Longitudinal Analyses of SAST Tools: A CodeQL Case Study** — [arxiv_cr](https://arxiv.org/abs/2605.07900v1)
- **Zero-determinant Strategy for Moving Target Defense: Existence, Performance, and Computation** — [arxiv_cr](https://arxiv.org/abs/2605.07854v1)
- **Can I Check What I Designed? Mapping Security Design DSLs to Code Analyzers** — [arxiv_cr](https://arxiv.org/abs/2605.07814v1)
- **GRASP -- Graph-Based Anomaly Detection Through Self-Supervised Classification** — [arxiv_cr](https://arxiv.org/abs/2605.07812v1)
- **A Note on Non-Negative $L_1$-Approximating Polynomials** — [arxiv_lg](https://arxiv.org/abs/2605.08072v1)
- **Don't Get Your Kroneckers in a Twist: Gaussian Processes on High-Dimensional Incomplete Grids** — [arxiv_lg](https://arxiv.org/abs/2605.08036v1)
- **PropSplat: Map-Free RF Field Reconstruction via 3D Gaussian Propagation Splatting** — [arxiv_lg](https://arxiv.org/abs/2605.08035v1)
- **Semiparametric Efficient Test for Interpretable Distributional Treatment Effects** — [arxiv_lg](https://arxiv.org/abs/2605.08034v1)
- **PET-Adapter: Test-Time Domain Adaptation for Full and Limited-Angle PET Image Reconstruction** — [arxiv_lg](https://arxiv.org/abs/2605.08030v1)
- **STARFlow2: Bridging Language Models and Normalizing Flows for Unified Multimodal Generation** — [arxiv_lg](https://arxiv.org/abs/2605.08029v1)
- **LLMs Improving LLMs: Agentic Discovery for Test-Time Scaling** — [arxiv_cl](https://arxiv.org/abs/2605.08083v1)
- **Conformal Path Reasoning: Trustworthy Knowledge Graph Question Answering via Path-Level Calibration** — [arxiv_cl](https://arxiv.org/abs/2605.08077v1)
- **Uncertainty-Aware Structured Data Extraction from Full CMR Reports via Distilled LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.08045v1)
- **Ask Early, Ask Late, Ask Right: When Does Clarification Timing Matter for Long-Horizon Agents?** — [arxiv_cl](https://arxiv.org/abs/2605.07937v1)
- **How to Train Your Latent Diffusion Language Model Jointly With the Latent Space** — [arxiv_cl](https://arxiv.org/abs/2605.07933v1)
- **GESR: Graph-Based Edge Semantic Reconstruction for Stealthy Communication Detection with Benign-Only Training** — [arxiv_cr](https://arxiv.org/abs/2605.07536v1)
- **Resilience of IEC 61850 Sampled Values-Based Protection Systems Under Coordinated False Data Injections** — [arxiv_cr](https://arxiv.org/abs/2605.07535v1)
- **Spying Across Chiplets: Side-Channel Attacks in 2.5/3D Integrated Systems** — [arxiv_cr](https://arxiv.org/abs/2605.07486v1)
- **Vaporizer: Breaking Watermarking Schemes for Large Language Model Outputs** — [arxiv_cr](https://arxiv.org/abs/2605.07481v1)
- **HBEE: Human Behavioral Entropy Engine -- Pre-Registered Multi-Agent LLM Simulation of Peer-Suspicion-Based Detection Inversion** — [arxiv_cr](https://arxiv.org/abs/2605.07472v1)
- **Forensic analysis of video data deletion and recovery in Honeywell surveillance file system** — [arxiv_cr](https://arxiv.org/abs/2605.07430v1)
- **We’re feeling cynical about xAI’s big deal with Anthropic** — [techcrunch_ai](https://techcrunch.com/2026/05/10/were-feeling-cynical-about-xais-big-deal-with-anthropic/)
- **Get ready for the whisper-filled office of the future** — [techcrunch_ai](https://techcrunch.com/2026/05/10/get-ready-for-the-whisper-filled-office-of-the-future/)
- **Anthropic says ‘evil’ portrayals of AI were responsible for Claude’s blackmail attempts** — [techcrunch_ai](https://techcrunch.com/2026/05/10/anthropic-says-evil-portrayals-of-ai-were-responsible-for-claudes-blackmail-attempts/)
- **AlexWortega/ai-peer-review-skill** — [github](https://github.com/AlexWortega/ai-peer-review-skill)
- **TehreemArbab/JazzCashMCP** — [github](https://github.com/TehreemArbab/JazzCashMCP)
- **Negai-ai/AgentClaw** — [github](https://github.com/Negai-ai/AgentClaw)
- **kruschdev/krusch-context-mcp** — [github](https://github.com/kruschdev/krusch-context-mcp)
- **aqlaboratory/genie3** — [github](https://github.com/aqlaboratory/genie3)
- **PaperGuru-AI/PaperGuru-Benchmark** — [github](https://github.com/PaperGuru-AI/PaperGuru-Benchmark)
- **cosmicstack-labs/mercury-agent-skills** — [github](https://github.com/cosmicstack-labs/mercury-agent-skills)
- **TomSolid/myPKA** — [github](https://github.com/TomSolid/myPKA)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **xavier-maugendre/n8n-zabbix-glpi-prometheus-agent-qdrant-offline** — [github](https://github.com/xavier-maugendre/n8n-zabbix-glpi-prometheus-agent-qdrant-offline)
- **banodoco/hivemind** — [github](https://github.com/banodoco/hivemind)
- **virgo777/buddyme** — [github](https://github.com/virgo777/buddyme)
- **paean-ai/deeptide** — [github](https://github.com/paean-ai/deeptide)
- **NitroRCr/gread** — [github](https://github.com/NitroRCr/gread)
- **bitan-del/gcode-harness** — [github](https://github.com/bitan-del/gcode-harness)
- **sanieldoe/companions** — [github](https://github.com/sanieldoe/companions)
- **tianji-qingtian/AI-Native** — [github](https://github.com/tianji-qingtian/AI-Native)
- **devton/agentic-workflow-blueprint** — [github](https://github.com/devton/agentic-workflow-blueprint)
- **浙大推出让AI会「导演」的角色扮演框架！四通道消息沉浸式交互** — [qbitai](https://www.qbitai.com/2026/05/415048.html)
- **浙大校友用AI突破32年拉姆齐数下界** — [qbitai](https://www.qbitai.com/2026/05/415031.html)
- **MiniMax关联公司增资至40亿，增幅300%** — [36kr](https://36kr.com/newsflashes/3804265813991173?f=rss)
- **申港证券、固德威等成立新能源公司，注册资本约5433万** — [36kr](https://36kr.com/newsflashes/3804259920584456?f=rss)
- **千问与淘宝打通，正式上线AI购物** — [36kr](https://36kr.com/newsflashes/3804258045386505?f=rss)
- **“星锐医药”完成近4000万美元B+轮融资** — [36kr](https://36kr.com/newsflashes/3804242296282627?f=rss)
- **8点1氪丨SK海力士回应“员工人均奖金达610万元”传闻；世界杯中国转播费从3亿美元腰斩到1.5亿；曝三星中国家电部门裁员补偿N+4，还送手机** — [36kr](https://36kr.com/p/3804132892646919?f=rss)
- **谷歌母公司Alphabet计划首次发行日元债券** — [36kr](https://36kr.com/newsflashes/3804270010851077?f=rss)
- **“Uncharted Dynamics”完成数百万美元种子轮融资** — [36kr](https://36kr.com/newsflashes/3804230399925768?f=rss)
- **A股三大指数集体高开，沪指突破4200点** — [36kr](https://36kr.com/newsflashes/3804213994167812?f=rss)
- **恒指开盘跌0.31%，恒生科技指数跌0.48%** — [36kr](https://36kr.com/newsflashes/3804209839447812?f=rss)
- **SAP宣布完成对主数据管理软件提供商Reltio的收购** — [36kr](https://36kr.com/newsflashes/3804197417131526?f=rss)
- **报道称OpenAI允许员工出售价值至多3000万美元的股票** — [36kr](https://36kr.com/newsflashes/3804194327453185?f=rss)