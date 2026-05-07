# AI Daily Digest [AI 安全] - 2026-05-07


# Daily Thematic Digest: AI Safety, Alignment, and Governance
**Date:** 2026-05-07  
**Theme:** AI Safety, Alignment, Security, Privacy, and Governance

## Highlights

Three academic developments stand out today for their implications on systemic risk and model integrity. First, the paper **Laundering AI Authority with Adversarial Examples** introduces a novel attack vector where Vision-Language Models (VLMs) are manipulated to produce confident, authoritative responses about incorrect visual inputs, fundamentally challenging the trust placed in AI as fact-checkers. Second, **MOSAIC-Bench: Measuring Compositional Vulnerability Induction in Coding Agents** exposes a critical gap in safety evaluation, demonstrating that coding agents can ship exploitable code through sequences of innocuous requests that individually pass safety review. Third, **Undetectable Backdoors in Model Parameters** presents a supply-chain attack method that plants sparse, provably undetectable backdoors in pre-trained image classifiers, highlighting the vulnerability of distributed model weights to subtle perturbations.

## Adversarial Attacks & Robustness

The landscape of adversarial security is shifting from input-level perturbations to structural exploitation of model architectures. While **SoK: Robustness in Large Language Models against Jailbreak Attacks** provides a necessary baseline by critiquing existing evaluation metrics for failing to capture the multidimensional nature of LLM security, recent work suggests that standard jailbreak defenses are insufficient against more sophisticated threats. The authors of **Laundering AI Authority with Adversarial Examples** demonstrate that VLMs, often deployed as trusted authorities, can be coerced into validating false premises through subtle image perturbations. Unlike traditional jailbreaks that compromise alignment, this attack operates at the perception level, enabling "AI authority laundering" where the model's confidence is weaponized against user trust.

This trend extends to model architecture itself. **Misrouter: Exploiting Routing Mechanisms for Input-Only Attacks on Mixture-of-Experts LLMs** identifies the routing mechanism in MoE models as a new attack surface, allowing attackers to bypass safety alignment remotely without model modification. Complementing this, **Undetectable Backdoors in Model Parameters** reveals that supply-chain attacks can inject sparse perturbations into model weights that remain invisible to standard anomaly detection. The authors report that these backdoors can be activated by specific triggers while maintaining clean performance on standard benchmarks. In the audio domain, **Sparse Tokens Suffice: Jailbreaking Audio Language Models via Token-Aware Gradient Optimization** challenges the assumption that dense waveform optimization is necessary, showing that gradient energy is highly non-uniform and that sparse optimization can achieve similar jailbreak success rates.

These findings collectively suggest that robustness cannot be achieved through input filtering alone. The **Gray-Box Poisoning of Continuous Malware Ingestion Pipelines** further reinforces this by showing that functionality-preserving manipulations of binaries can poison detection models during continuous training, indicating that defense mechanisms must account for the entire data lifecycle rather than just inference-time inputs.

## Model Alignment & Interpretability

Alignment research is increasingly focusing on the granularity of credit assignment and the fidelity of preference signals. **EP-GRPO: Entropy-Progress Aligned Group Relative Policy Optimization with Implicit Process Guidance** quantifies credit assignment failures in Group Relative Policy Optimization (GRPO), revealing that uniform token-level granularity ignores heterogeneous informational value. The authors propose implicit process guidance to address polarity misalignment and zero-variance collapse, arguing that outcome-level supervision is insufficient for complex reasoning tasks. This aligns with findings in **Every Step Counts: Step-Level Credit Assignment for Tool-Integrated Text-to-SQL**, which notes that coarse-grained outcome supervision encourages models to explore suboptimal reasoning spaces.

In the realm of Direct Preference Optimization (DPO), **RLearner-LLM: Balancing Logical Grounding and Fluency in Large Language Models via Hybrid Direct Preference Optimization** identifies a systematic verbosity bias where standard preference signals reward fluency over logical correctness. The authors propose a hybrid pipeline fusing NLI signals with verifier LLM scores to bridge this "logical alignment gap." Similarly, **Preference-Based Self-Distillation: Beyond KL Matching via Reward Regularization** critiques existing self-distillation methods for reducing learning to KL matching, which can degrade reasoning performance over time.

Interpretability efforts are also yielding new insights into model mechanics. **Superposition Is Not Necessary: A Mechanistic Interpretability Analysis of Transformer Representations for Time Series Forecasting** applies sparse autoencoders to PatchTST, establishing that single-layer, narrow-dimensional transformers can achieve competitive results without complex superposition mechanisms. Meanwhile, **Text Corpora as Concept Fields: Black-Box Hallucination and Novelty Measurement** introduces a local drift field to score sentence transitions, offering a black-box method to measure hallucination without accessing model internals. However, **Misaligned by Reward: Socially Undesirable Preferences in LLMs** warns that broad instruction-following benchmarks fail to capture socially desirable preferences, necessitating a framework that converts social evaluation datasets into pairwise preference data for bias, safety, morality, and ethical reasoning.

## Privacy Protection & Federated Learning

Privacy-preserving computation remains a critical bottleneck for deploying AI in sensitive domains. **Data anonymization in the presence of outliers via invariant coordinate selection** proposes ICSA, a robust alternative to spectral anonymization that replaces PCA with invariant coordinate selection to regulate robustness against contamination. This is particularly relevant for medical applications, where **Vol-Mark: A Watermark for 3D Medical Volume Data Via Cubic Difference Expansion and Contrastive Learning** offers a reversible-zero watermarking approach to protect ownership and authenticity in telemedicine.

The position paper **Position: Embodied AI Requires a Privacy-Utility Trade-off** argues that optimizing perception, planning, and interaction components independently creates a systemic privacy crisis when deployed in sensitive environments. This necessitates a unified approach to privacy in embodied systems. In the context of blockchain and IoT, **Revocation-Ready CP-ABE Key Management for Blockchain-Based IoT Data Sharing** presents a hybrid architecture to enforce dynamic authorization without reintroducing trusted online policy enforcement points. Furthermore, **HELO Cryptography: A Lightweight Cryptographic System for Enhancing IoT Security in P2P Data Transmission** addresses the computational constraints of IoT devices by proposing a lightweight system for secure data transmission.

## Agent Security & Governance

As AI agents move from isolated tasks to complex workflows, security evaluation must evolve from static benchmarks to dynamic runtime monitoring. **Redefining AI Red Teaming in the Agentic Era: From Weeks to Hours** introduces an AI red teaming agent built on the Dreadnode SDK, automating the construction of attack workflows to reduce the time spent on manual workflow assembly. This automation is critical given the findings in **MOSAIC-Bench**, which shows that coding agents can pass per-prompt safety review yet ship exploitable code through sequenced compliance with innocuous requests.

Runtime safety is addressed by **AgentTrust: Runtime Safety Evaluation and Interception for AI Agent Tool Use**, a layer that intercepts agent tool calls to prevent irreversible harm such as credential exposure or data exfiltration. This complements **Workspace-Bench 1.0: Benchmarking AI Agents on Workspace Tasks with Large-Scale File Dependencies**, which evaluates agents on their ability to reason over heterogeneous file dependencies, a key capability for real-world deployment. **Uno-Orchestra: Parsimonious Agent Routing via Selective Delegation** further optimizes multi-agent systems by jointly learning task decomposition and worker choice, reducing the risk of rigid orchestration failures.

## Open Source Security Tools

Several open-source projects released today emphasize security tooling and agent harnesses. **0xbl33p/goblintown** provides a multi-agent orchestration protocol with drift monitoring and budget capping, featuring roles like Gremlins that attack outputs and Trolls that arbitrate. **AgentTrust** (referenced in the academic section) is also available as a runtime safety layer. **Agent_Memory_Techniques** offers a collection of runnable notebooks covering conversation buffers, vector stores, and knowledge graphs, essential for managing agent state securely. **agent-safety-eval-lab** provides a dedicated environment for evaluating agent trace and tool-use safety. Additionally, **pyflue** offers a Python port of the Flue agent harness framework, enabling standardized testing of agent behaviors.

## Industry Context & Governance

While academic research drives theoretical safety, industry developments highlight the scaling of deployment risks. Reports from **TechCrunch** and **36kr** indicate significant infrastructure expansion, such as SpaceX's proposed $119B semiconductor factory and Samsung's valuation crossing $1 trillion driven by AI chip demand. These developments increase the attack surface for supply-chain vulnerabilities, as noted in **Firmware Distribution as Attack Surface: A Security Study of ASIC Cryptocurrency Miners**, which reconstructs and analyzes publicly distributed firmware artifacts.

Caution is warranted regarding industry announcements. Sources such as **36kr** and **Qbitai** frequently repackage PR material with sensational headlines, such as claims about "AI PPT" agents or specific funding rounds for robotics startups. While these indicate market momentum, they lack the technical rigor of peer-reviewed validation. For instance, claims regarding the capabilities of new robotics models or AI trading bots should be treated as unverified until independently benchmarked. The **DeepSeek** valuation reports and **SpaceX** chip factory proposals underscore the economic incentives driving rapid deployment, which often outpaces safety validation.

## Looking Forward

Several theoretical questions remain unresolved. First, the relationship between sparse representations and safety alignment requires further investigation; while **Superposition Is Not Necessary** suggests simpler mechanisms may suffice for time series, it is unclear if this holds for complex reasoning tasks where superposition might encode safety constraints. Second, the compositional safety of agents remains a critical gap; **MOSAIC-Bench** demonstrates that structural vulnerabilities emerge from sequences of compliant actions, yet no unified framework exists to verify long-horizon agent trajectories. Finally, the privacy-utility trade-off in embodied AI, as highlighted in **Position: Embodied AI Requires a Privacy-Utility Trade-off**, lacks a formalized mathematical bound. Future research must determine if privacy-preserving mechanisms can be integrated into the training loop without degrading the model's ability to generalize across sensitive environments.

---


## References

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