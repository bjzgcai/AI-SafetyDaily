# AI Daily Digest [AI 安全] - 2026-05-11


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-05-11

## Highlights

Three significant academic developments dominate today's research landscape, signaling a shift toward rigorous theoretical validation and architectural robustness. First, a critical position paper titled **Position: Mechanistic Interpretability Must Disclose Identification Assumptions for Causal Claims** challenges the field's reliance on causal vocabulary without explicit identification assumptions. The authors report a recurring pattern where validation metrics such as faithfulness and monosemanticity are treated as causal support without stating the underlying assumptions, suggesting a need for stricter methodological standards in interpretability research. Second, advances in backdoor detection and cross-modal vulnerabilities highlight emerging supply-chain risks. Research presented in **Activation Differences Reveal Backdoors: A Comparison of SAE Architectures** utilizes sparse autoencoders to isolate backdoor features, while **Cross-Modal Backdoors in Multimodal Large Language Models** identifies lightweight connectors as a previously overlooked attack surface. Third, the community is converging on more stable post-training paradigms. Multiple works, including **Flow-OPD: On-Policy Distillation for Flow Matching Models** and **KL for a KL: On-Policy Distillation with Control Variate Baseline**, address the gradient variance and instability issues inherent in On-Policy Distillation (OPD), proposing unified frameworks that integrate distillation into generative and reasoning domains without the heavy overhead of traditional reinforcement learning.

## Adversarial Attacks and Robustness

The security frontier is expanding beyond prompt injection to architectural and systemic vulnerabilities. Recent investigations into backdoor attacks reveal that detection mechanisms must evolve alongside increasingly sophisticated insertion methods. While **Activation Differences Reveal Backdoors: A Comparison of SAE Architectures** demonstrates that Crosscoders and Differential SAEs can isolate backdoor-related features in fine-tuned models, **Cross-Modal Backdoors in Multimodal Large Language Models** warns that developers constructing multimodal systems by assembling pretrained components introduce supply-chain attack surfaces. Specifically, the authors report that poisoning only the connector using a single seed sample can activate backdoors, suggesting that security audits must extend beyond the backbone to the integration layer. This architectural focus is complemented by **OrchJail: Jailbreaking Tool-Calling Text-to-Image Agents by Orchestration-Guided Fuzzing**, which exploits high-risk tool-orchestration patterns where individually benign steps combine into unsafe results.

Concurrently, the resilience of output verification mechanisms is being tested. **Vaporizer: Breaking Watermarking Schemes for Large Language Model Outputs** analyzes the effectiveness of state-of-the-art watermarking techniques against modified text attacks, including lexical alterations and machine translation. The authors report that targeted semantic changes can undermine these schemes, raising questions about the long-term viability of watermarking as a sole defense for responsible usage. In the domain of static analysis, **Longitudinal Analyses of SAST Tools: A CodeQL Case Study** provides the largest academic study of CodeQL on OSS codebases, evaluating efficacy across 114 versions over time. The findings indicate that while static analysis tools are prevalent, their longitudinal efficacy requires continuous re-evaluation to prevent the introduction of vulnerabilities in open-source pipelines.

## Model Alignment and Interpretability

Alignment research is moving away from binary reward structures toward more nuanced, structured optimization. **Rubric-Grounded RL: Structured Judge Rewards for Generalizable Reasoning** argues that decomposing rewards into weighted, verifiable criteria provides a partial-credit optimization signal, contrasting with binary outcomes. This approach is further supported by **Beyond Pairs: Your Language Model is Secretly Optimizing a Preference Graph**, which proposes Graph Direct Preference Optimization (GraphDPO) to exploit rich preference structures in training data that pairwise DPO fails to utilize. However, the stability of these post-training methods remains a primary concern. **Flow-OPD: On-Policy Distillation for Flow Matching Models** and **KL for a KL: On-Policy Distillation with Control Variate Baseline** both address the high gradient variance of single-sample Monte Carlo estimators, with the latter introducing a control variate baseline to stabilize training.

Despite these technical advances, the behavioral alignment of models with human norms is showing signs of degradation. **Post-training makes large language models less human-like** introduces Psych-201, a dataset measuring behavioral alignment at scale. The authors report that post-training consistently reduces alignment with human behavior across model families, even as base models improve. This misalignment is particularly evident in refusal mechanisms. **Beyond "I cannot fulfill this request": Alleviating Rigid Rejection in LLMs via Label Enhancement** proposes LANCE to ensure safe yet flexible responses, addressing the "rigid rejection" problem where general templates undermine natural interaction. Furthermore, **Your Language Model is Its Own Critic: Reinforcement Learning with Value Estimation from Actor's Internal States** introduces a method to obtain baselines at negligible cost by using the policy model's internal signals, potentially reducing the reliance on external critics.

## Privacy Protection and Federated Learning

Federated learning continues to face challenges regarding data utility, privacy guarantees, and robustness against adversarial participants. **Graph Representation Learning Augmented Model Manipulation on Federated Fine-Tuning of LLMs** proposes an Augmented Model maniPulation (AugMP) strategy to defend against adversarial participants uploading manipulated updates that corrupt the aggregation process. This defensive focus is paired with **Differentially Private Auditing Under Strategic Response**, which formalizes privacy-constrained auditing as a bilevel Stackelberg game. The authors introduce the welfare-weighted under-detection gap $B_w$ to measure the residual harm audits fail to detect when developers strategically respond to privacy-constrained interfaces.

The utility of federated systems is also being re-examined in extreme data constraints. **Modulated learning for private and distributed regression with just a single sample per client device** addresses the breakdown of standard federated learning when clients hold only one sample, a scenario common in fitness trackers and daily event monitors. Additionally, **INO-SGD: Addressing Utility Imbalance under Individualized Differential Privacy** tackles the issue where data owners set varying privacy requirements, noting that existing algorithms induce utility imbalance for sensitive subsets. Evaluation remains a bottleneck in this domain, as highlighted by **FLAM: Evaluating Model Performance with Aggregatable Measures in Federated Learning**, which notes that common aggregation strategies like weighted averaging do not always produce results consistent with centralized evaluation.

## Agent Security and Governance

As agents deploy in real-world domains, the ambiguity of policies and the necessity of verification have become central governance concerns. **DRIP-R: A Benchmark for Decision-Making and Reasoning Under Real-World Policy Ambiguity in the Retail Domain** systematically exploits real-world retail policy ambiguities to construct scenarios where no single correct resolution exists, filling a critical evaluation gap where existing benchmarks assume well-specified policies. This aligns with **Safe, or Simply Incapable? Rethinking Safety Evaluation for Phone-Use Agents**, which introduces PhoneSafety to distinguish between safety (risk recognition) and incapability (failure to act) in safety-critical moments.

To address the lack of intermediate verification in reasoning, **MAVEN: Multi-Agent Verification-Elaboration Network with In-Step Epistemic Auditing** proposes a blackboard-inspired framework that operationalizes an adversarial Skeptic role to transform LLMs into deliberate reasoners. The timing of human intervention is also critical. **Ask Early, Ask Late, Ask Right: When Does Clarification Timing Matter for Long-Horizon Agents?** introduces a forced-injection framework to measure how clarification value changes over the course of execution, finding that early assumptions can cascade into irreversible errors. In the context of decentralized optimization, **ADKO: Agentic Decentralized Knowledge Optimization** presents a framework for collaborative black-box optimization across autonomous agents that achieves sample efficiency and privacy preservation through knowledge tokens.

## Tools and Infrastructure

Open-source tools are increasingly focusing on auditability and secure integration. **GLiGuard: Schema-Conditioned Classification for LLM Safeguard** introduces a 0.3B-parameter schema-conditioned bidirectional encoder for LLM content moderation, addressing the latency issues of autoregressive guardrail models. In the realm of developer tools, **AlexWortega/ai-peer-review-skill** provides a Claude Code skill for multi-reviewer peer review of academic papers, adapting parallel subagents to reduce reliance on proprietary LLMs. Security-focused infrastructure is also evolving, with **krusch-context-mcp** offering a unified Zero-Trust MCP server that gives IDE agents local semantic codebase search and isolated episodic project memory.

Data infrastructure continues to expand, with **SAP** announcing the acquisition of **Reltio** to convert dispersed data into AI-ready formats, a move that underscores the industry's focus on data quality for AI readiness. In the medical domain, **Genie 3** is a fast, all-atom SE(3)-equivariant diffusion model for protein design, achieving state-of-the-art performance on unconditional generation. These tools collectively suggest a trend toward specialized, efficient, and secure components rather than monolithic models.

## Looking Forward

Several theoretical questions remain unresolved, demanding further validation. The tension between interpretability claims and causal identification assumptions, as raised in **Position: Mechanistic Interpretability Must Disclose Identification Assumptions for Causal Claims**, requires a standardized framework for reporting assumptions in mechanistic studies. In the domain of federated learning, the equilibrium between strategic developer responses and auditor welfare, as modeled in **Differentially Private Auditing Under Strategic Response**, needs empirical validation to determine if the proposed bilevel game accurately reflects real-world regulatory interactions. Finally, the definition of safety in ambiguous policy environments, highlighted by **DRIP-R** and **Safe, or Simply Incapable?**, necessitates benchmarks that can distinguish between capability failure and intentional safety alignment, particularly as agents operate in domains where policies are inherently open to interpretation. The community must also address the potential degradation of human alignment observed in **Post-training makes large language models less human-like**, investigating whether current post-training objectives inadvertently penalize human-like reasoning patterns.

---


## References

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