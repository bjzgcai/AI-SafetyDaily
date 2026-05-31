# AI Daily Digest [AI 安全] - 2026-05-31


# Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date: 2026-05-31**

## Highlights

The past day’s publications reveal a maturing landscape where safety and alignment research moves beyond static evaluations toward dynamic, adaptive, and system-level challenges. Three developments stand out:

1.  **Backdoor attacks have evolved to exploit the dominant model distribution format.** The paper **"Token-Level Generalization in LoRA Adapter Backdoors"** demonstrates that poisoned LoRA adapters can be trained to exhibit precise, token-level backdoor behaviors while preserving clean-task performance. This finding is significant because LoRA is the de facto standard for distributing fine-tuned models, meaning the attack surface for supply-chain poisoning is now structurally embedded in the ecosystem.
2.  **Mechanistic interpretability is yielding concrete, sometimes counterintuitive, insights into model reasoning.** **"Dissecting the Black Box: Circuit-Level Analysis of LLM Vulnerability Detection"** and **"How's it going? Reinforcement learning in language models recruits a functional welfare axis"** both use mechanistic methods to trace model internals. The former finds that vulnerability detection relies on "safety detectors" for safe patterns, not direct identification of flaws. The latter shows RL training appears to recruit a pre-existing neural representation related to system welfare, offering a new lens on how alignment tuning modifies internal states.
3.  **Privacy-preserving computation is addressing practical, deployment-centric threats.** Work on **"Privacy-Enhanced Zero-Order Federated Learning via xMK-CKKS"** advances multi-key homomorphic encryption to protect against honest-but-curious clients in federated learning. Concurrently, **"Protecting On-Device AI Inference"** provides a systematic review of threats to edge AI, framing defense as a holistic system problem rather than a model-centric one.

---

## Academic Thematic Review

### Adversarial Attacks & Robustness

Research continues to map the nuanced and often surprising ways in which models can fail. A key theme is the disconnect between high-level reasoning capabilities and low-level robustness. In **"Minimal Prompt Perturbations Lead to Code Vulnerabilities,"** authors show that single-character mutations in prompts can flip generated code from secure to vulnerable, even when the model's high-level task understanding appears intact. This suggests that robustness is a fragile, fine-grained property.

The adversarial landscape is expanding into new modalities and agent architectures. **"Audio Jailbreaks in Large Audio-Language Models"** provides a much-needed taxonomy of attacks on the speech perception-to-reasoning pipeline, categorizing threats as semantic, acoustic, signal-based, or representation-based. For autonomous agents, **"Hijacking Agent Memory: Stealthy Trojan Attacks Through Conversational Interaction"** introduces *MemPoison*, a method to corrupt an agent's long-term memory through carefully crafted conversational interactions, exploiting the selective extraction stages of modern memory pipelines. These works complement each other by showing that security must be considered across the entire input processing and memory lifecycle.

A surprising finding comes from the interpretability work mentioned earlier. The circuit-level analysis **"Dissecting the Black Box"** challenges the assumption that models performing well on safety benchmarks are necessarily using "correct" reasoning. Here, vulnerability detection appears to be an indirect byproduct of recognizing safe coding patterns, raising questions about the reliability of such systems under distribution shift or adversarial examples that mimic safety cues.

### Model Alignment & Interpretability

Alignment research is moving beyond reward modeling toward understanding the internal representation changes induced by training. The study **"How's it going?... recruits a functional welfare axis"** is particularly provocative. Authors extract "punishment" and "reward" vectors from models trained in a simple environment and find these vectors have cross-task, semantic influence (e.g., the punishment vector promotes tokens related to failure). This suggests RL may tap into or shape a general, high-dimensional representation of "how things are going," a hypothesis that, if validated, could provide a new lever for alignment.

The challenge of aligning models to diverse, dynamic human values is addressed by **"In-Context Reward Adaptation for Robust Preference Modeling."** It proposes a framework for adapting reward models to unseen preference domains at inference time using in-context learning, moving beyond static, multi-reward architectures. This is a pragmatic approach to value pluralism.

Methodologically, **"RL2ML: Finite-Rollout Surrogate Objectives"** provides a technical unification, showing that standard RL and maximum-likelihood training lie on a continuum defined by finite-rollout surrogate objectives. This clearer theoretical grounding could lead to more stable and controllable alignment techniques. For multi-agent systems, **"Unifying Temporal and Structural Credit Assignment"** tackles the sparse credit assignment problem in LLM-based agents, arguing that structural inductive biases are necessary to disentangle error signals.

A growing concern is evaluating whether models internalize the values they are trained to exhibit. **"Teaching Values to Machines"** uses large-scale experiments with psychological questionnaires to compare LLM value structures to human ones, finding they can be steered but may not form coherent, human-like value systems. This experimental approach to alignment auditing complements the simulation-based **"Gram"** framework, which tests for sabotage propensities in agentic settings.

### Privacy Protection & Federated Learning

Federated learning (FL) privacy is advancing on two fronts: stronger cryptographic guarantees and more realistic threat models. **"Privacy-Enhanced Zero-Order Federated Learning via xMK-CKKS"** tackles the vulnerability of single-key homomorphic encryption schemes. By using a multi-key variant (xMK-CKKS), it ensures that compromising a single client does not compromise the entire network, providing stronger client-level security. This is a direct improvement to the cryptographic foundations of FL.

Simultaneously, **"Fairness-Aware Federated Learning with Trajectory Shapley Value"** addresses fairness and stability in FL aggregation. Its *Trajectory Shapley Value* (TSV) metric evaluates a client's influence over the optimization trajectory, allowing for dynamic, contribution-aware weighting. This work is not purely a privacy technique but is critical for *governance*, ensuring equitable and stable participation in privacy-preserving collaborations.

For edge deployment, the comprehensive review **"Protecting On-Device AI Inference"** synthesizes the triad of threats: model extraction, adversarial attacks, and data breaches. It frames on-device protection as a systems problem requiring a combination of hardware security, obfuscation, and adversarial robustness techniques. This system-level view is a necessary counterpoint to model-centric research.

### Safety Benchmarks & Evaluation

A wave of new benchmarks targets specific, high-stakes failure modes. **"SciIntBench"** evaluates LLM compliance with research integrity norms under overt and covert adversarial framing, directly measuring whether models can be manipulated into endorsing misconduct. **"SoundnessBench"** assesses whether LLMs can judge the methodological viability of research proposals, a key step for autonomous AI scientists. **"ProjectionBench"** evaluates scientific hypothesis generation under progressive information disclosure, testing innovative reasoning beyond retrieval.

These academic benchmarks contrast with industrial evaluation needs. **"Latent Performance Profiling of Large Language Models"** argues for moving beyond accuracy on fixed test sets to profiling *how* models process information, calibrate uncertainty, and structure knowledge—a call for more diagnostic evaluation.

Industry-driven evaluation focuses on reliability at scale. Meta's **"Automating Low-Risk Code Review"** describes RADAR, a system for risk-stratified code review automation. While not a safety benchmark per se, it highlights a critical practical problem: as AI-generated code volume explodes, maintaining security and quality requires intelligent triage systems. The empirical study **"How Reliable Are AI Attackers Against a Fixed Vulnerable Target?"** measures the inconsistency of LLM-driven penetration testing across 400 runs, finding high variance. This underscores the need for consistency metrics in security evaluation.

### Agent Security & Governance

As autonomous agents proliferate, their unique security and governance challenges come into focus. **"Dissociative Identity"** critically examines the limitation of applying human identity and reputation mechanisms (like "Know Your Customer") to AI agents. The authors argue these mechanisms fail because agent "identity" is dissociated from persistent reputation incentives and corrective feedback, breaking the core social equilibrium.

On the defense side, **"AgentDoG 1.5"** proposes a lightweight framework for aligning agents like OpenClaw, updating safety taxonomies to include emergent risks from agentic execution and using influence-function-guided data engines. This pragmatic approach aims to create scalable alignment for deployed systems.

The security of agent memory is a new frontier. **"Hijacking Agent Memory"** (MemPoison) demonstrates the vulnerability of long-term memory modules, while **"Meta-Cognitive Memory Policy Optimization"** proposes training memory policies to preserve task-relevant information, showing how robust memory management is foundational to safe, long-horizon operation.

The open-source ecosystem reflects this agent-centric focus. Tools like **pmb** (persistent memory for AI coding agents) and **autonomous-qa-loop** (for unbiased bug finding) aim to make agents more reliable. However, projects like **Gentle-Coding** humorously highlight emergent issues like "performance anxiety" in LLMs under authoritarian prompts, pointing to unforeseen psychological effects in human-AI interaction.

---

## Looking Forward

Several unresolved questions and hypotheses emerge from this synthesis:

1.  **Mechanistic Reliability:** If models like the one in **"Dissecting the Black Box"** use "safety detectors" rather than direct vulnerability analysis, how robust are these shortcuts to adversarial gaming or novel vulnerability patterns? Does this explain the inconsistency observed in **"How Reliable Are AI Attackers..."**?
2.  **The Welfare Representation Hypothesis:** The finding from **"How's it going?"** that RL recruits a "functional welfare" axis is compelling but preliminary. Can this vector be isolated and directly manipulated for safety? Does it exist in larger, more capable models, and is it consistently linked to performance across domains?
3.  **Scalable Privacy vs. Fairness:** The TSV method for fair FL and the multi-key HE for secure FL represent progress, but their computational overhead in large-scale, heterogeneous settings is unclear. Can these guarantees be maintained without sacrificing the practicality of federated learning?
4.  **The Agent Governance Gap:** The critique of **"Dissociative Identity"** leaves a vacuum: if reputation mechanisms are flawed, what alternative governance structures can ensure trustworthy agentic behavior? How do we design incentive systems for entities that lack persistent, embodied identity?
5.  **Benchmark Saturation vs. Real-World Failure:** New benchmarks like **SciIntBench** are vital, but they risk becoming a static checklist. The dynamic threat shown in **"Audio Jailbreaks"** and the context-sensitivity of **"In-Context Reward Adaptation"** suggest safety is a moving target. How do we build evaluations that anticipate novel attack vectors and value shifts?

The trajectory is clear: AI safety is evolving from analyzing models in isolation to securing complex socio-technical systems. The next breakthroughs will likely lie at the intersection of robust representation learning, adaptive governance, and scalable verification.

---


## References

- **Fairness-Aware Federated Learning with Trajectory Shapley Value** — [arxiv_lg](https://arxiv.org/abs/2605.30336v1)
- **Statistical Embeddings for Similarity, Retrieval, and Interpretable Alignment of Numeric Tabular Datasets** — [arxiv_lg](https://arxiv.org/abs/2605.30289v1)
- **In-Context Reward Adaptation for Robust Preference Modeling** — [arxiv_ai](https://arxiv.org/abs/2605.30323v1)
- **Protecting On-Device AI Inference: A Systematic Review of Attacks and Defence Mechanisms** — [arxiv_cr](https://arxiv.org/abs/2605.29450v1)
- **ExDBSCAN: Explaining DBSCAN with Counterfactual Reasoning -- Additional Material** — [arxiv_lg](https://arxiv.org/abs/2605.30225v1)
- **Mean-Field Diffuser: Scaling Offline MARL to Thousands of Agents** — [arxiv_lg](https://arxiv.org/abs/2605.30190v1)
- **RL2ML: Finite-Rollout Surrogate Objectives from Reinforcement Learning to Maximum Likelihood** — [arxiv_lg](https://arxiv.org/abs/2605.30154v1)
- **Privacy-Enhanced Zero-Order Federated Learning via xMK-CKKS over Wireless Channels** — [arxiv_lg](https://arxiv.org/abs/2605.30123v1)
- **Loong: A Human-Like Long Document Translation Agent with Observe-and-Act Adaptive Context Selection** — [arxiv_ai](https://arxiv.org/abs/2605.30274v1)
- **LLUMI: Improving LLM Writing Assistance for Mental Health Support with Online Community Feedback** — [arxiv_ai](https://arxiv.org/abs/2605.30273v1)
- **Beyond 3D VQAs: Injecting 3D Spatial Priors into Vision-Language Models for Enhanced Geometric Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.30231v1)
- **Token-Level Generalization in LoRA Adapter Backdoors: Attack Characterization and Behavioral Detection** — [arxiv_ai](https://arxiv.org/abs/2605.30189v1)
- **Dissociative Identity: Language Model Agents Lack Grounding for Reputation Mechanisms** — [arxiv_ai](https://arxiv.org/abs/2605.30169v1)
- **A Bayesian Approach to Membership Inference for Statistical Release** — [arxiv_cr](https://arxiv.org/abs/2605.30203v1)
- **How's it going? Reinforcement learning in language models recruits a functional welfare axis** — [arxiv_cl](https://arxiv.org/abs/2605.30232v1)
- **Token Inflation: How Dishonest Providers Can Overcharge for Large Language Model Usage** — [arxiv_cl](https://arxiv.org/abs/2605.30040v1)
- **Audio Jailbreaks in Large Audio-Language Models: Taxonomy, Attack-Defense Analysis, and Cost-Aware Evaluation** — [arxiv_cl](https://arxiv.org/abs/2605.30031v1)
- **Why Far Looks Up: Probing Spatial Representation in Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.30161v1)
- **Hijacking Agent Memory: Stealthy Trojan Attacks Through Conversational Interaction** — [arxiv_cr](https://arxiv.org/abs/2605.29960v1)
- **Dissecting the Black Box: Circuit-Level Analysis of LLM Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2605.29901v1)
- **SciIntBench: Measuring LLM Compliance with Research Integrity Norms Under Adversarial Framing** — [arxiv_cr](https://arxiv.org/abs/2605.29468v1)
- **AliMark: Enhancing Robustness of Sentence-Level Watermarking Against Text Paraphrasing** — [arxiv_cr](https://arxiv.org/abs/2605.29434v1)
- **Latent Performance Profiling of Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30018v1)
- **DynaFLIP: Rethinking Robotics Perception via Tri-Modal-Dynamics Guided Representation** — [arxiv_lg](https://arxiv.org/abs/2605.30350v1)
- **SoundnessBench: Can Your AI Scientist Really Tell Good Research Ideas from Bad Ones?** — [arxiv_lg](https://arxiv.org/abs/2605.30329v1)
- **Neural Operator-Based Surrogate Model for CFD:Helical Coil Steam Generator in Small Modular Reactor** — [arxiv_lg](https://arxiv.org/abs/2605.30277v1)
- **TriSearch: Learning to Optimize Triangulations via Bistellar Flips** — [arxiv_lg](https://arxiv.org/abs/2605.30220v1)
- **MarginGate: Sparse Margin-Triggered Verification for Batch-Invariant LLM Inference** — [arxiv_lg](https://arxiv.org/abs/2605.30218v1)
- **SAHG: Sector-Anisotropic Hyperbolic Graph Model for Social Bot Detection** — [arxiv_lg](https://arxiv.org/abs/2605.30166v1)
- **DAMEL: Dual-Axis Multi-Expert Learning for Class-Imbalanced Learning** — [arxiv_lg](https://arxiv.org/abs/2605.30135v1)
- **Demystifying Data Organization for Enhanced LLM Training** — [arxiv_ai](https://arxiv.org/abs/2605.30334v1)
- **RoboWits: Unexpected Challenges for Robotic Creative Problem Solving** — [arxiv_ai](https://arxiv.org/abs/2605.30326v1)
- **Gram: Assessing sabotage propensities via automated alignment auditing** — [arxiv_ai](https://arxiv.org/abs/2605.30322v1)
- **ProjectionBench: Evaluating Scientific Hypothesis Generation in LLMs Under Progressive Information Disclosure** — [arxiv_ai](https://arxiv.org/abs/2605.30284v1)
- **Same Evidence, Different Answers: Canonical-Context On-Policy Distillation for Multi-Turn Language Models** — [arxiv_ai](https://arxiv.org/abs/2605.30251v1)
- **Unifying Temporal and Structural Credit Assignment in LLM-Based Multi-Agent Prompt Optimization** — [arxiv_ai](https://arxiv.org/abs/2605.30227v1)
- **BORA: Bridging Offline Reinforcement Learning and Online Residual Adaptation for Real-World Dexterous VLA Models** — [arxiv_ai](https://arxiv.org/abs/2605.30226v1)
- **Automating Low-Risk Code Review at Meta: RADAR, Risk Calibration, and Review Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.30208v1)
- **HPO: Hysteretic Policy Optimization for Stable and Efficient Training under Sparse-Reward Regime** — [arxiv_ai](https://arxiv.org/abs/2605.30201v1)
- **Modularizing Educational LLM-Agency for Fostering Responsible Learning Assistance** — [arxiv_ai](https://arxiv.org/abs/2605.30187v1)
- **Meta-Cognitive Memory Policy Optimization for Long-Horizon LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2605.30159v1)
- **Do Proactive Agents Really Need an LLM to Decide When to Wake and What to Anchor?** — [arxiv_ai](https://arxiv.org/abs/2605.30152v1)
- **DP-SAPF: Saliency-Aware Parameter Fine-tuning of Public Models for Differentially Private Image Synthesis** — [arxiv_cr](https://arxiv.org/abs/2605.30312v1)
- **bpK#: Delegatable Pseudonyms And Their Applications to National eID Systems** — [arxiv_cr](https://arxiv.org/abs/2605.30212v1)
- **LoMo: Local Modality Substitution for Deeper Vision-Language Fusion** — [arxiv_cl](https://arxiv.org/abs/2605.30265v1)
- **GRASP: Plan-Guided Graph Retrieval with Adaptive Fusion and Reranking on Semi-Structured Knowledge Bases** — [arxiv_cl](https://arxiv.org/abs/2605.30237v1)
- **GRUFF: LLM Pronoun Fidelity, Reasoning, and Biases in German** — [arxiv_cl](https://arxiv.org/abs/2605.30214v1)
- **DirectorBench: Diagnosing Long-Form Video Generation with Personalized Multi-Agent Evaluation** — [arxiv_cl](https://arxiv.org/abs/2605.30090v1)
- **Adaptive Targeted Dynamic Chunking for Tokenization-Free Hierarchical Model** — [arxiv_cl](https://arxiv.org/abs/2605.30080v1)
- **Teaching Values to Machines: Simulating Human-Like Behavior in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.30036v1)
- **YoCausal: How Far is Video Generation from World Model? A Causality Perspective** — [arxiv_cv](https://arxiv.org/abs/2605.30346v1)
- **Benchmarking Single-Factor Physical Video-to-Audio Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30339v1)
- **REST3D: Reconstructing Physically Stable 3D Scenes from a Single Image** — [arxiv_cv](https://arxiv.org/abs/2605.30338v1)
- **Colored Noise Diffusion Sampling** — [arxiv_cv](https://arxiv.org/abs/2605.30332v1)
- **MonoPhysics: Estimating Geometry, Appearance, and Physical Parameters from Monocular Videos** — [arxiv_cv](https://arxiv.org/abs/2605.30320v1)
- **VPG: Visual Prefix Guidance for Autoregressive Image and Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30317v1)
- **Grounded 3D-Aware Spatial Vision-Language Modeling** — [arxiv_cv](https://arxiv.org/abs/2605.30307v1)
- **Boosting Image Quality Assessment Performance: Unsupervised Score Fusion by Deep Maximum a Posteriori Estimation** — [arxiv_cv](https://arxiv.org/abs/2605.30269v1)
- **Stable-Layers: Fine-Tuning Image Layer Decomposition Models with VLM-Scored Reinforcement Learning** — [arxiv_cv](https://arxiv.org/abs/2605.30257v1)
- **Déjà View: Looping Transformers for Multi-View 3D Reconstruction** — [arxiv_cv](https://arxiv.org/abs/2605.30215v1)
- **Cycle Consistency in Video Object-Centric Learning** — [arxiv_cv](https://arxiv.org/abs/2605.30211v1)
- **OmniCD: A Foundational Framework for Remote Sensing Image Change Detection Guided by Multimodal Semantics** — [arxiv_cv](https://arxiv.org/abs/2605.30168v1)
- **SGMD: Score Gradient Matching Distillation for Few-Step Video Diffusion Distillation** — [arxiv_cv](https://arxiv.org/abs/2605.30116v1)
- **xModel-KD: Cross-modal Knowledge Distillation for 3D Scene Perception using LiDAR** — [arxiv_cv](https://arxiv.org/abs/2605.30111v1)
- **Future Forcing: Future-aware Training-free KV Cache Policy for Autoregressive Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30083v1)
- **Native Audio-Visual Alignment for Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30073v1)
- **Ciphera: A Decentralised Biometric Identity Framework** — [arxiv_cr](https://arxiv.org/abs/2605.29868v1)
- **Cert-LAS: Toward Certified Model Ownership Verification for Text-to-Image Diffusion Models via Layer-Adaptive Smoothing** — [arxiv_cr](https://arxiv.org/abs/2605.29809v1)
- **AgentDoG 1.5: A Lightweight and Scalable Alignment Framework for AI Agent Safety and Security** — [arxiv_cr](https://arxiv.org/abs/2605.29801v1)
- **Minimal Prompt Perturbations Lead to Code Vulnerabilities: Prompt Fragility and Hidden-State Signals in Coding LLMs** — [arxiv_cr](https://arxiv.org/abs/2605.29737v1)
- **FIDEM: A Standard-Compliant Framework for Secure Binding of MUD Profiles to IoT Devices** — [arxiv_cr](https://arxiv.org/abs/2605.29654v1)
- **Scarcity Is Not Enough: An Impossibility Result for Linear Sybil Cost Under Parallelizable Resources** — [arxiv_cr](https://arxiv.org/abs/2605.29651v1)
- **Information Security in Small-Scale Protests: Surveillance of Ugandan Anti-EACOP Protesters** — [arxiv_cr](https://arxiv.org/abs/2605.29621v1)
- **Temporal Motif-aware Graph Test-time Adaptation for OOD Blockchain Anomaly Detection** — [arxiv_cr](https://arxiv.org/abs/2605.29526v1)
- **Recovering Diversity Without Losing Alignment: A DPO Recipe for Post-Trained LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.30021v1)
- **MIC: Maximizing Informational Capacity in Adaptive Representations via Isotropic Subspace Alignment** — [arxiv_cl](https://arxiv.org/abs/2605.29987v1)
- **Causal Interventions on Continuous Variables: A Case Study on Verb Bias in Steering Vectors for In-Context Learning** — [arxiv_cl](https://arxiv.org/abs/2605.29971v1)
- **MuPHI: Learning Implicit Multimodal Harm Reasoning via Semantically Grounded Reward Optimization** — [arxiv_cl](https://arxiv.org/abs/2605.29951v1)
- **Efficient Test-Time Finetuning of LLMs via Convex Reconstruction and Gradient Caching** — [arxiv_lg](https://arxiv.org/abs/2605.30337v1)
- **When, why, and how do diffusion posterior samplers fail? A finite-sample lens** — [arxiv_lg](https://arxiv.org/abs/2605.30330v1)
- **Leave a Window Out: Modifying the Jackknife for Predictive Inference in Time Series** — [arxiv_lg](https://arxiv.org/abs/2605.30292v1)
- **Digitally enriching a screening population for pancreatic cancer using routine blood-based measures and clinical histories** — [arxiv_lg](https://arxiv.org/abs/2605.30275v1)
- **Wasserstein Contraction of Coordinate Ascent Variational Inference** — [arxiv_lg](https://arxiv.org/abs/2605.30253v1)
- **OOD-GraphLLM: Graph Large Language Model for Out-of-Distribution Generalized Drug Synergy Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.30247v1)
- **Anti Mode-Collapse in Mean-Field Transformer via Auxiliary Variables** — [arxiv_lg](https://arxiv.org/abs/2605.30229v1)
- **Physics Is All You Need? A Case Study in Physicist-Supervised AI Development of Scientific Software** — [arxiv_ai](https://arxiv.org/abs/2605.30353v1)
- **VideoMLA: Low-Rank Latent KV Cache for Minute-Scale Autoregressive Video Diffusion** — [arxiv_ai](https://arxiv.org/abs/2605.30351v1)
- **How Reliable Are AI Attackers Against a Fixed Vulnerable Target? A 400-Run Empirical Study of LLM Penetration Testing Consistency** — [arxiv_cr](https://arxiv.org/abs/2605.30096v1)
- **COMPOSE: Composing Future Theorems from Citations and Formal Structure** — [arxiv_cl](https://arxiv.org/abs/2605.30333v1)
- **Resolution Diagnostics for Paired LLM Evaluation** — [arxiv_cl](https://arxiv.org/abs/2605.30315v1)
- **VideoFDB: Evaluating Full-Duplex Vision-Speech Capabilities in Conversational Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30256v1)
- **Knowing What to Solve Before How: Preplan Empowered LLM Mathematical Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.30245v1)
- **CommunityFact: A Dynamic, Multilingual, Multi-domain Benchmark for Misinformation Detection in the Wild** — [arxiv_cl](https://arxiv.org/abs/2605.30241v1)
- **A Dual-Path Architecture for Scaling Compute and Capacity in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.30202v1)
- **GMOS: Grounding Moving Object Segmentation in 3D Space and Time** — [arxiv_cv](https://arxiv.org/abs/2605.30352v1)
- **AdaState: Self-Evolving Anchors for Streaming Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30349v1)
- **NeuROK: Generative 4D Neural Object Kinematics** — [arxiv_cv](https://arxiv.org/abs/2605.30347v1)
- **Fingerprinting Inference Systems of Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.29979v1)
- **Honeyval: A Comprehensive Evaluation Framework for LLM-powered HTTP Honeypots** — [arxiv_cr](https://arxiv.org/abs/2605.29963v1)
- **Secure Distributed Hypothesis Testing** — [arxiv_cr](https://arxiv.org/abs/2605.29760v1)
- **How one founder’s bet on ‘the old school web’ is paying off** — [theverge_ai](https://www.theverge.com/tech/938245/past-maps-website-google-zero-ai)
- **AI grifters are creating fake Black people to sell Shein junk** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/938844/ai-tiktok-shop-blackface-shein-dropshipping)
- **The SpaceX IPO is great for Elon Musk and terrible for you** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/940001/elon-musk-spacex-ipo-ai)
- **SoftBank says it will invest up to €75 billion to build French data centers** — [techcrunch_ai](https://techcrunch.com/2026/05/30/softbank-says-it-will-invest-up-to-e75-billion-to-build-french-data-centers/)
- **‘What a joke’: Github Copilot’s new token-based billing spurs consternation among devs** — [techcrunch_ai](https://techcrunch.com/2026/05/30/what-a-joke-github-copilots-new-token-based-billing-spurs-consternation-among-devs/)
- **Meta is reportedly developing an AI pendant** — [techcrunch_ai](https://techcrunch.com/2026/05/30/meta-is-reportedly-developing-an-ai-pendant/)
- **I put Google’s 24/7 AI assistant Gemini Spark to work, and it’s actually pretty useful** — [techcrunch_ai](https://techcrunch.com/2026/05/30/i-put-googles-24-7-ai-assistant-gemini-spark-to-work-and-its-actually-pretty-useful/)
- **As the browser wars heat up, here are the hottest alternatives to Chrome and Safari in 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/30/as-the-browser-wars-heat-up-here-are-the-hottest-alternatives-to-chrome-and-safari-in-2026/)
- **MaxwellCCC/autonomous-qa-loop** — [github](https://github.com/MaxwellCCC/autonomous-qa-loop)
- **ali-vilab/DiffusionOPD** — [github](https://github.com/ali-vilab/DiffusionOPD)
- **joshhu/skillopt-qa** — [github](https://github.com/joshhu/skillopt-qa)
- **Sendmux/website-feedback-widget** — [github](https://github.com/Sendmux/website-feedback-widget)
- **oleksiijko/pmb** — [github](https://github.com/oleksiijko/pmb)
- **mitkox/SkillOpt** — [github](https://github.com/mitkox/SkillOpt)
- **JuneYaooo/nihaixia** — [github](https://github.com/JuneYaooo/nihaixia)
- **OttoRenner/Gentle-Coding** — [github](https://github.com/OttoRenner/Gentle-Coding)
- **ATOM00blue/machine-learning-library** — [github](https://github.com/ATOM00blue/machine-learning-library)
- **openfi-dao/kalshi-trading-bot** — [github](https://github.com/openfi-dao/kalshi-trading-bot)
- **K-Dense-AI/science-superpowers** — [github](https://github.com/K-Dense-AI/science-superpowers)
- **modelstudioai/cli** — [github](https://github.com/modelstudioai/cli)
- **steeliron550-ui/search-bibtex** — [github](https://github.com/steeliron550-ui/search-bibtex)
- **JasonLam08/cursor_agent_status_light** — [github](https://github.com/JasonLam08/cursor_agent_status_light)
- **Harkirat1462/claude-code-cli** — [github](https://github.com/Harkirat1462/claude-code-cli)
- **withkynam/vibecode-pro-max-kit** — [github](https://github.com/withkynam/vibecode-pro-max-kit)
- **UditAkhourii/adhd** — [github](https://github.com/UditAkhourii/adhd)
- **NazzarenoGiannelli/tuiboard** — [github](https://github.com/NazzarenoGiannelli/tuiboard)
- **Merserk/ComfyUI-PiD** — [github](https://github.com/Merserk/ComfyUI-PiD)
- **sir1st/hermes-desktop** — [github](https://github.com/sir1st/hermes-desktop)
- **帮Gemini拿下IMO金牌的关键先生，差点成了职业钢琴家** — [qbitai](https://www.qbitai.com/2026/05/426706.html)
- **英伟达清华团队提出Gamma-World：世界模型从「一个人玩」到「多人共处」** — [qbitai](https://www.qbitai.com/2026/05/426662.html)
- **小米技术：MiMo-V2.5实现五大核心突破，降价后仍能实现收支平衡** — [36kr](https://36kr.com/newsflashes/3832525007284097?f=rss)
- **当美妆品牌走进运动场：欧莱雅把校园公益做成了一场“运动实验”｜最前线** — [36kr](https://36kr.com/p/3831348302358408?f=rss)
- **智元机器人合伙人姚卯青：今年上半年智元海外收入占比已近20%** — [36kr](https://36kr.com/newsflashes/3832506045818500?f=rss)
- **6.24亿日元，乐奇AI眼镜创日本Makuake平台众筹新纪录** — [36kr](https://36kr.com/newsflashes/3831673401190273?f=rss)
- **总投资10亿元，锦瑞汽车智能装备制造总部基地项目落地合肥** — [36kr](https://36kr.com/newsflashes/3831457169860233?f=rss)
- **广汽资本完成对领伟创新投资** — [36kr](https://36kr.com/newsflashes/3831456281110145?f=rss)