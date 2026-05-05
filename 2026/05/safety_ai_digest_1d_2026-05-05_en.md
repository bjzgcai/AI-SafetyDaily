# AI Daily Digest [AI 安全] - 2026-05-05


</think>

# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-05-05
**Author:** Senior AI Safety Research Analyst

## Highlights

This week’s research landscape indicates a significant shift toward operationalizing safety mechanisms within complex, multi-agent environments and addressing the limitations of current evaluation paradigms. A primary development is the emergence of **LocalAlign**, which proposes generating near-target adversarial examples to train defenses against prompt injection, moving beyond simple fine-tuning boundaries to create more robust separation between trusted commands and untrusted data. Concurrently, the **MultiBreak** benchmark introduces a scalable, active learning pipeline for multi-turn jailbreaks, highlighting that existing single-turn evaluations fail to capture the nuances of conversational safety degradation. Finally, the **SPECA** framework and related agentic auditing tools suggest a move toward specification-based verification, where safety is treated as a checklist derived from formal requirements rather than a probabilistic outcome of model behavior. These developments collectively point toward a future where safety is integrated into the architecture of agent systems and evaluation is grounded in long-horizon, real-world interaction scenarios.

## Adversarial Attacks & Robustness

The vulnerability of Large Language Models (LLMs) and Vision-Language Models (VLMs) to adversarial manipulation remains a central concern, with recent work focusing on the granularity of attacks and the efficacy of defenses. **LocalAlign** addresses the specific threat of prompt injection in systems interacting with external data. The authors observe that existing defenses, which rely on fine-tuning to preserve an explicit boundary between trusted commands and untrusted data, often block obvious injections but fail against more subtle manipulations. By generating near-target adversarial examples specifically for alignment training, **LocalAlign** aims to create a more generalizable defense mechanism. This approach contrasts with methods that rely on global suppression or homogenized agent responses, suggesting that targeted adversarial training may yield better robustness without sacrificing model utility.

In the realm of multimodal security, **VisInject** challenges the prevailing metrics used to evaluate universal adversarial attacks on aligned multimodal large language models. The authors argue that reported attack success rates, often cited in the 60-80% range, conflate two distinct events: the perturbation of the model's output (Influence) and the emission of the attacker's chosen target concept (Precise Injection). By composing existing techniques under an $L_{inf}$ budget and adding a dual-axis evaluation, **VisInject** reveals that while models may be influenced, precise injection remains more difficult than previously assumed. This distinction is critical for understanding the actual risk posed by visual perturbations as a prompt-injection channel.

Further complicating the attack surface is the issue of data poisoning in Retrieval-Augmented Generation (RAG) systems. **Needle-in-RAG** introduces a character-level traceback method for poisoned spans in retrieved evidence. While existing defenses operate at the passage level, which is too coarse for modern attacks where effective payloads may be short fabricated claims or hidden instructions, **Needle-in-RAG** presents a forensic framework capable of identifying specific character-level poison. This work complements **MultiBreak**, which focuses on the generation of multi-turn jailbreaks. While **MultiBreak** expands the diversity of adversarial prompts through active learning to test model safety, **Needle-in-RAG** focuses on the integrity of the external knowledge base. Together, they suggest that safety must be evaluated across both the model's internal reasoning and the external data it retrieves.

The threat of backdoor attacks in deep learning supply chains is further explored in **Checkerboard**, a theoretically grounded, learning-free clean-label backdoor attack. Unlike existing clean-label attacks that rely on expensive optimization or surrogate-model training, **Checkerboard** utilizes a low poisoning budget to poison training data while maintaining label consistency. This makes the attack harder to detect, as poisoned samples remain label-consistent. The authors demonstrate that such attacks can be effective even with minimal data access, highlighting the need for robust data validation pipelines. This finding is particularly relevant for contrastive learning, where reliance on third-party or internet data is common, as noted in **Repurposing and Evaluating the (In)Feasibility of Dataset Poisoning enabled Watermarking for Contrastive Learning**. The latter work reveals limitations in existing data-poisoning backdoor attacks on contrastive learning, including poor dataset adaptability and low success rates, suggesting that while the threat exists, current methods may not be as generalizable as feared.

In the context of information retrieval, **Led to Mislead** proposes **CRAFT**, a supervised framework for black-box adversarial rank attacks powered by large language models. Operating in three stages—adversarial dataset generation via retrieval-augmented generation, supervised fine-tuning, and preference-guided optimization—**CRAFT** demonstrates that neural ranking models remain highly vulnerable to adversarial manipulation. This work contrasts with **Beyond Semantic Relevance: Counterfactual Risk Minimization for Robust Retrieval-Augmented Generation** (CoRM-RAG), which proposes a framework to align retrieval with counterfactual risk minimization to bridge the "Relevance-Robustness Gap". While **CRAFT** focuses on the vulnerability of ranking models, **CoRM-RAG** offers a defensive strategy that prioritizes robustness over semantic relevance, acknowledging that maximizing relevance can paradoxically promote sycophantic evidence that reinforces hallucinations.

## Model Alignment & Interpretability

Alignment research continues to evolve from simple preference optimization to more complex frameworks involving incentives, correction, and pluralistic value tracking. **AI Alignment via Incentives and Correction** applies law-and-economics models of deterrence and enforcement to AI alignment. The authors argue that misconduct in agentic AI pipelines should be treated as a strategic response to incentives, where a solver weighs the gain from violation against the probability of detection and the severity of punishment. This perspective shifts the focus from external failure to internal incentive structures, suggesting that alignment requires not just training but also the design of enforcement mechanisms.

The challenge of value lock-in as societal norms evolve is addressed by **Adaptive Pluralistic Alignment (APA)**. This modular pipeline updates pluralistically aligned AI systems to track evolving values without repeating costly pretraining. APA utilizes low-rank reward basis decomposition to learn compact personalized reward models, which then act as a jury to collectively select among candidate outputs through social-choice-theoretic mechanisms. This approach contrasts with prevailing alignment methods that target a fixed set of preferences, offering a potential solution to the rigidity of current alignment strategies.

Interpretability efforts are increasingly automated through multi-agent frameworks. **Automated Interpretability and Feature Discovery in Language Models with Agents** introduces a system that runs coupled loops of explanation refinement and feature discovery. The explanation refinement loop proposes competing hypotheses and tests them with targeted prompt controls, while the feature discovery loop generates prompt sets and constructs k-nearest-neighbor graphs in activation space. On Gemma-2 family models, this system demonstrates the ability to find internal features and explain them without manual intervention. This automation complements **Probe-Geometry Alignment: Erasing the Cross-Sequence Memorization Signature Below Chance**, which characterizes where behavioral unlearning retention lives and shows it can be surgically removed without measurable capability cost. The authors use a leave-one-out cross-sequence probe to test whether a memorization signature generalizes across held-out sequences, revealing that memorization-specific gaps are real and consistent across scale.

The geometry of transformer representations is further explored in **Concepts Whisper While Syntax Shouts: Spectral Anti-Concentration and the Dual Geometry of Transformer Representations**. This work tests whether the causal inner product enables cross-lingual concept transport. Across 17 models and 4 language pairs, a matched-spectrum randomization test finds that Whitened Causal Alignment is indistinguishable from spectral regularization alone. However, this failure reveals a broader phenomenon: anti-concentration is observed in residual-stream difference-of-means vectors across five architecture families. This suggests that while specific alignment techniques may not transfer concepts as expected, the underlying geometry of representations exhibits robust anti-concentration properties that could be leveraged for future interpretability tools.

In the domain of reasoning, **The Reasoning Trap: An Information-Theoretic Bound on Closed-System Multi-Step LLM Reasoning** identifies a phenomenon where multi-agent debate and closed-system reasoning tend to preserve answer accuracy while degrading the reasoning behind those answers. The authors name this the "Debate Trap" and the broader phenomenon the "Reasoning Trap", offering a programmatic theory of evidence-grounded reasoning failure. This finding is critical for understanding the limitations of multi-agent debate as a safety mechanism. It suggests that while debate may improve the final answer, it does not necessarily improve the underlying reasoning process, which could lead to hidden failures in high-stakes scenarios.

**Multi-Agent Reasoning Improves Compute Efficiency: Pareto-Optimal Test-Time Scaling** provides a systematic analysis of inference scaling strategies, including self-consistency, self-refinement, multi-agent debate, and mixture-of-agents. The authors evaluate methods on reasoning benchmarks to study their computational performance tradeoffs. This work complements **The Reasoning Trap** by offering a quantitative perspective on the efficiency of these methods. While **The Reasoning Trap** highlights the qualitative degradation of reasoning, **Multi-Agent Reasoning** quantifies the compute costs, suggesting that there may be a Pareto-optimal point where efficiency gains do not come at the cost of reasoning quality.

**Neuro-Symbolic Agents for Hallucination-Free Requirements Reuse** addresses the tension between the flexibility of LLMs and the structural validity of requirements reuse. The authors present a neuro-symbolic multi-agent system that re-conceptualizes requirements reuse as a Model-Driven Elicitation process. This approach aims to overcome the limitations of rigid templates while avoiding the risk of generating structurally invalid or inconsistent requirement combinations. This work is particularly relevant for safety-critical systems where requirements must be precise and verifiable.

## Privacy Protection & Federated Learning

Privacy-preserving machine learning remains a critical area of research, particularly in healthcare and distributed systems. **FLRSP: Privacy-Preserving Federated Learning Using Randomly Selected Model Parameters** proposes a method that uses randomly selected model parameters to update global models. This approach aims to prevent attackers from reconstructing original training data if shared updates are compromised. The authors highlight that high-quality deep neural networks require huge amounts of training data, which raises privacy concerns when dealing with sensitive information. By randomly selecting parameters, **FLRSP** attempts to balance model quality with privacy protection.

In the context of healthcare, **Class-Aware Adaptive Differential Privacy in Deep Learning for Sensor-Based Fall Detection** proposes a framework that applies differential privacy with class-aware noise adaptation. Existing privacy approaches apply uniform noise across all training samples, which affects prediction performance. **Class-Aware Adaptive Differential Privacy** integrates with a hybrid 3D Convolutional Neural Network and Bidirectional Long Short-Term Memory to address this limitation. This work is particularly relevant for elderly care applications where timely fall detection is critical, and privacy concerns are significant.

**Federated Semi-Supervised Graph Neural Networks with Prototype-Guided Pseudo-Labeling for Privacy-Preserving Gestational Diabetes Mellitus Prediction** addresses the coupled constraints of label scarcity and data privacy in clinical deployment. The proposed **FedTGNN-SS** framework allows each hospital to build models locally while sharing only prototype-guided pseudo-labels. This approach reduces the need for sharing patient-level data while addressing the scarcity of confirmed diagnostic labels. The authors demonstrate that this framework can improve risk stratification for Gestational Diabetes Mellitus without compromising patient privacy.

**Toward Resilient 5G Networks: Comparative Analysis of Federated and Centralized Learning for RF Jamming Detection** proposes a federated learning-based jamming detection framework that operates on over-the-air In-phase and Quadrature (IQ) samples. This work highlights that conventional machine learning approaches typically require centralized data collection, compromising the privacy of user equipment. By using federated learning, the framework can detect jamming attacks while preserving the privacy of user equipment. The authors compare federated and centralized learning, suggesting that federated learning offers a viable alternative for security-critical applications where privacy is paramount.

**ShieldShare: Building a VPN-backed Android Hotspot for Secure Internet Sharing with Per-User Traffic Accounting** presents a proxy-based Android application that enables secure VPN-backed hotspot sharing with per-user traffic accounting without requiring root access. This tool addresses the limitations of mainstream VPN providers that impose device limits and Android's native hotspot functionality that lacks support for routing shared traffic through VPN connections. **ShieldShare** provides a practical solution for secure internet sharing in mobile environments, emphasizing the need for accessible privacy tools.

**MelShield: Robust Mel-Domain Audio Watermarking for Provenance Attribution of AI Generated Synthesized Speech** proposes a keyed audio watermarking framework that embeds identifiable signals into AI-generated audio for copyright protection and reliable attribution. Operating in the Mel-spectrogram domain during the generation process, **MelShield** targets intermediate acoustic representations in Mel-conditioned pipelines for text-to-speech generation. This work addresses the growing need for provenance attribution in AI-generated content, ensuring that synthesized speech can be reliably identified as machine-generated.

**PQC Validator: Validating Post-Quantum Readiness in Cloud-Native 5G Core Networks** addresses the challenge of validating post-quantum security in 5G Core networks. The authors highlight that deploying PQ primitives does not guarantee PQ security, as network functions may advertise PQ support but silently fall back to classical primitives. **PQC Validator** provides a framework for validating post-quantum readiness, ensuring that operators and vendors are truly implementing PQ security measures. This work is critical for the long-term security of communication networks as they migrate to post-quantum cryptography.

## Agent Security & Governance

The security and governance of agentic AI systems are becoming increasingly important as these systems gain autonomy and access to external tools. **AgenticVM: Agentic AI for Adaptive Software Vulnerability Management** introduces a multi-agent framework that integrates large language models with security tools to automate vulnerability detection, assessment, prioritization, and reporting. **AgenticVM** combines rule-based processing, a BERT-based CVSS prediction module, and specialized LLM-driven agents, leveraging data from sources such as the National Vulnerability Database and the European Union Vulnerability Database. This work demonstrates the potential of multi-agent systems to improve the efficiency of vulnerability management.

**Architectural Obsolescence of Unhardened Agentic-AI Runtimes** presents a critical analysis of agentic-AI runtimes, showing that upstream OpenClaw, the most engineered single-user agentic-AI gateway in public release, catches none of the four ways an action can diverge from its audit record. The authors demonstrate that recall is 0.000 on every cell of every confusion matrix, on a 1600-sample template baseline. This finding suggests that current agentic-AI runtimes may be fundamentally unhardened, requiring significant architectural changes to ensure safety.

**SPECA: Specification-to-Checklist Agentic Auditing Framework** (Source [128]) introduces a framework that converts specifications into checklists for agentic auditing. This approach allows for more systematic evaluation of agent behavior against formal requirements. **SPECA** complements **MemORAI: Memory Organization and Retrieval via Adaptive Graph Intelligence for LLM Conversational Agents** (Source [129]), which addresses the lack of persistent memory in LLMs for long-term personalized conversations. **MemORAI** integrates selective memory filtering with dual-layer compression, a provenance-enriched multi-relational graph, and query-adaptive subgraph retrieval. This framework aims to retain user-persona-relevant content while tracking factual origins at the turn level.

**Bug-Bounty-Agents** (Source [132]) provides an AI-powered agent framework for bug-bounty pentesting and red-teaming purposes. This open-source project leverages LLMs to automate the identification of security vulnerabilities in software systems. The authors demonstrate that AI agents can be effective in identifying security flaws, suggesting a potential shift in how security testing is conducted.

**Feedback-Normalized Developer Memory for Reinforcement-Learning Coding Agents: A Safety-Gated MCP Architecture** (Source [16]) presents a local-first, Model Context Protocol (MCP)-native developer-memory architecture for RL coding agents. This framework treats memory selection as a safety-gated process, ensuring that persistent memory does not compromise the integrity of reinforcement learning code development. This work is particularly relevant for long software-engineering episodes where small details can alter Bellman targets or validation claims.

**MAD-OPD: Breaking the Ceiling in On-Policy Distillation via Multi-Agent Debate** (Source [19]) proposes a framework that recasts the distillation teacher as a deliberative collective of teachers that debate over the student's on

---


## References

- **LocalAlign: Enabling Generalizable Prompt Injection Defense via Generation of Near-Target Adversarial Examples for Alignment Training** — [arxiv_cr](https://arxiv.org/abs/2605.01462v1)
- **Catching the Infection Before It Spreads: Foresight-Guided Defense in Multi-Agent Systems** — [arxiv_ai](https://arxiv.org/abs/2605.01758v1)
- **Less is More: Geometric Unlearning for LLMs with Minimal Data Disclosure** — [arxiv_cl](https://arxiv.org/abs/2605.01735v1)
- **MultiBreak: A Scalable and Diverse Multi-turn Jailbreak Benchmark for Evaluating LLM Safety** — [arxiv_cl](https://arxiv.org/abs/2605.01687v1)
- **FLRSP: Privacy-Preserving Federated Learning Using Randomly Selected Model Parameters** — [arxiv_cr](https://arxiv.org/abs/2605.01204v1)
- **Who Decides What Is Harmful? Content Moderation Policy Through A Multi-Agent Personalised Inference Framework** — [arxiv_cl](https://arxiv.org/abs/2605.01416v1)
- **Beyond Semantic Relevance: Counterfactual Risk Minimization for Robust Retrieval-Augmented Generation** — [arxiv_cl](https://arxiv.org/abs/2605.01302v1)
- **Repurposing and Evaluating the (In)Feasibility of Dataset Poisoning enabled Watermarking for Contrastive Learning** — [arxiv_ai](https://arxiv.org/abs/2605.01834v1)
- **Probe-Geometry Alignment: Erasing the Cross-Sequence Memorization Signature Below Chance** — [arxiv_ai](https://arxiv.org/abs/2605.01699v1)
- **Class-Aware Adaptive Differential Privacy in Deep Learning for Sensor-Based Fall Detection** — [arxiv_ai](https://arxiv.org/abs/2605.01679v1)
- **The Reasoning Trap: An Information-Theoretic Bound on Closed-System Multi-Step LLM Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.01704v1)
- **Adversarial Imitation Learning with General Function Approximation: Theoretical Analysis and Practical Algorithms** — [arxiv_lg](https://arxiv.org/abs/2605.01778v1)
- **Anticipation-VLA: Solving Long-Horizon Embodied Tasks via Anticipation-based Subgoal Generation** — [arxiv_lg](https://arxiv.org/abs/2605.01772v1)
- **Toward Resilient 5G Networks: Comparative Analysis of Federated and Centralized Learning for RF Jamming Detection** — [arxiv_lg](https://arxiv.org/abs/2605.01705v1)
- **Automated Interpretability and Feature Discovery in Language Models with Agents** — [arxiv_ai](https://arxiv.org/abs/2605.01555v1)
- **Feedback-Normalized Developer Memory for Reinforcement-Learning Coding Agents: A Safety-Gated MCP Architecture** — [arxiv_cl](https://arxiv.org/abs/2605.01567v1)
- **Auditing demographic bias in AI-based emergency police dispatch: a cross-lingual evaluation of eleven large language models** — [arxiv_cl](https://arxiv.org/abs/2605.01451v1)
- **Injecting Distributional Awareness into MLLMs via Reinforcement Learning for Deep Imbalanced Regression** — [arxiv_cl](https://arxiv.org/abs/2605.01402v1)
- **MAD-OPD: Breaking the Ceiling in On-Policy Distillation via Multi-Agent Debate** — [arxiv_cl](https://arxiv.org/abs/2605.01347v1)
- **AgenticVM: Agentic AI for Adaptive Software Vulnerability Management** — [arxiv_cr](https://arxiv.org/abs/2605.01739v1)
- **Remote Action Generation: Remote Control with Minimal Communication** — [arxiv_ai](https://arxiv.org/abs/2605.01833v1)
- **RMGAP: Benchmarking the Generalization of Reward Models across Diverse Preferences** — [arxiv_ai](https://arxiv.org/abs/2605.01831v1)
- **Federated Semi-Supervised Graph Neural Networks with Prototype-Guided Pseudo-Labeling for Privacy-Preserving Gestational Diabetes Mellitus Prediction** — [arxiv_ai](https://arxiv.org/abs/2605.01810v1)
- **TMD-Bench: A Multi-Level Evaluation Paradigm for Music-Dance Co-Generation** — [arxiv_ai](https://arxiv.org/abs/2605.01809v1)
- **Khala: Scaling Acoustic Token Language Models Toward High-Fidelity Music Generation** — [arxiv_ai](https://arxiv.org/abs/2605.01790v1)
- **The Compliance Gap: Why AI Systems Promise to Follow Process Instructions but Don't** — [arxiv_ai](https://arxiv.org/abs/2605.01771v1)
- **Talk is Cheap, Communication is Hard: Dynamic Grounding Failures and Repair in Multi-Agent Negotiation** — [arxiv_ai](https://arxiv.org/abs/2605.01750v1)
- **NH-CROP: Robust Pricing for Governed Language Data Assets under Cost Uncertainty** — [arxiv_ai](https://arxiv.org/abs/2605.01745v1)
- **Architectural Obsolescence of Unhardened Agentic-AI Runtimes** — [arxiv_ai](https://arxiv.org/abs/2605.01740v1)
- **GEASS: Training-Free Caption Steering for Hallucination Mitigation in Vision-Language Models** — [arxiv_ai](https://arxiv.org/abs/2605.01733v1)
- **FEDIN: Frequency-Enhanced Deep Interest Network for Click-Through Rate Prediction** — [arxiv_ai](https://arxiv.org/abs/2605.01726v1)
- **SignVerse-2M: A Two-Million-Clip Pose-Native Universe of 25+ Sign Languages** — [arxiv_ai](https://arxiv.org/abs/2605.01720v1)
- **Beyond ECE: Calibrated Size Ratio, Risk Assessment, and Confidence-Weighted Metrics** — [arxiv_lg](https://arxiv.org/abs/2605.01796v1)
- **Robust Linear Dueling Bandits with Post-serving Context under Unknown Delays and Adversarial Corruptions** — [arxiv_lg](https://arxiv.org/abs/2605.01752v1)
- **Benchmarking Single-Pose Docking, Consensus Rescoring, and Supervised ML on the LIT-PCBA Library: A Critical Evaluation of DiffDock, AutoDock-GPU, GNINA, and DiffDock-NMDN** — [arxiv_lg](https://arxiv.org/abs/2605.01681v1)
- **Limit Properties at Critical Indices of Linear Canonical Riesz Potentials and Their Applications to Security of Multi-Image Encryption** — [arxiv_cr](https://arxiv.org/abs/2605.01654v1)
- **Toward a Principled Framework for Agent Safety Measurement** — [arxiv_cr](https://arxiv.org/abs/2605.01644v1)
- **ShieldShare: Building a VPN-backed Android Hotspot for Secure Internet Sharing with Per-User Traffic Accounting** — [arxiv_cr](https://arxiv.org/abs/2605.01569v1)
- **MelShield: Robust Mel-Domain Audio Watermarking for Provenance Attribution of AI Generated Synthesized Speech** — [arxiv_cr](https://arxiv.org/abs/2605.01515v1)
- **PQC Validator: Validating Post-Quantum Readiness in Cloud-Native 5G Core Networks** — [arxiv_cr](https://arxiv.org/abs/2605.01454v1)
- **VisInject: Disruption != Injection -- A Dual-Dimension Evaluation of Universal Adversarial Attacks on Vision-Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.01449v1)
- **AI Alignment via Incentives and Correction** — [arxiv_ai](https://arxiv.org/abs/2605.01643v1)
- **Prosa: Rubric-Based Evaluation of LLMs on Real User Chats in Brazilian Portuguese** — [arxiv_ai](https://arxiv.org/abs/2605.01630v1)
- **Concepts Whisper While Syntax Shouts: Spectral Anti-Concentration and the Dual Geometry of Transformer Representations** — [arxiv_ai](https://arxiv.org/abs/2605.01609v1)
- **Beyond Perplexity: Character Distribution Signatures and the MDTA Benchmark for AI Text Detection** — [arxiv_cl](https://arxiv.org/abs/2605.01647v1)
- **Led to Mislead: Adversarial Content Injection for Attacks on Neural Ranking Models** — [arxiv_cl](https://arxiv.org/abs/2605.01591v1)
- **Towards Efficient and Expressive Offline RL via Flow-Anchored Noise-conditioned Q-Learning** — [arxiv_lg](https://arxiv.org/abs/2605.01663v1)
- **Exact Loop Controllers for ReLU Realization of Homogeneous Curve Refinements** — [arxiv_lg](https://arxiv.org/abs/2605.01655v1)
- **Adaptive Pluralistic Alignment: A pipeline for dynamic artificial democracy** — [arxiv_lg](https://arxiv.org/abs/2605.01642v1)
- **Minimum Specification Perturbation: Robustness as Distance-to-Falsification in Causal Inference** — [arxiv_lg](https://arxiv.org/abs/2605.01579v1)
- **Hybrid Quantum Reinforcement Learning with QAOA for Improved Vehicle Routing Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.01574v1)
- **Checkerboard: A Simple, Effective, Efficient and Learning-free Clean Label Backdoor Attack with Low Poisoning Budget** — [arxiv_cr](https://arxiv.org/abs/2605.01298v1)
- **Artificial intelligence language technologies in multilingual healthcare: Grand challenges ahead** — [arxiv_cl](https://arxiv.org/abs/2605.01441v1)
- **Medmarks: A Comprehensive Open-Source LLM Benchmark Suite for Medical Tasks** — [arxiv_cl](https://arxiv.org/abs/2605.01417v1)
- **MTA: Multi-Granular Trajectory Alignment for Large Language Model Distillation** — [arxiv_cl](https://arxiv.org/abs/2605.01374v1)
- **LLM Output Detectability and Task Performance Can be Jointly Optimized** — [arxiv_cl](https://arxiv.org/abs/2605.01350v1)
- **A Multi-View Media Profiling Suite: Resources, Evaluation, and Analysis** — [arxiv_cl](https://arxiv.org/abs/2605.01336v1)
- **Enhancing Game Review Sentiment Classification on Steam Platform with Attention-Based BiLSTM** — [arxiv_cl](https://arxiv.org/abs/2605.01315v1)
- **Needle-in-RAG: Prompt-Conditioned Character-Level Traceback of Poisoned Spans in Retrieved Evidence** — [arxiv_cr](https://arxiv.org/abs/2605.01782v1)
- **VulKey: Automated Vulnerability Repair Guided by Domain-Specific Repair Patterns** — [arxiv_cr](https://arxiv.org/abs/2605.01769v1)
- **Automated Channel Fault Analysis with Tofu** — [arxiv_cr](https://arxiv.org/abs/2605.01721v1)
- **Only Say What You Know: Calibration-Aware Generation for Long-Form Factuality** — [arxiv_cl](https://arxiv.org/abs/2605.01749v1)
- **EGAD: Entropy-Guided Adaptive Distillation for Token-Level Knowledge Transfer** — [arxiv_cl](https://arxiv.org/abs/2605.01732v1)
- **Learning Koopman operators for coupled systems via information on governing equations of subsystems** — [arxiv_lg](https://arxiv.org/abs/2605.01835v1)
- **Hybrid Visual Telemetry for Bandwidth-Constrained Robotic Vision: A Pilot Study with HEVC Base Video and JPEG ROI Stills** — [arxiv_lg](https://arxiv.org/abs/2605.01826v1)
- **Molecular Representations for Large Language Models** — [arxiv_lg](https://arxiv.org/abs/2605.01822v1)
- **Skipping the Zeros in Diffusion Models for Sparse Data Generation** — [arxiv_lg](https://arxiv.org/abs/2605.01817v1)
- **MAGIC: Multi-Step Advantage-Gated Causal Influence for Multi-agent Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.01805v1)
- **Zero-Shot, Safe and Time-Efficient UAV Navigation via Potential-Based Reward Shaping, Control Lyapunov and Barrier Functions** — [arxiv_lg](https://arxiv.org/abs/2605.01787v1)
- **A Semi-Supervised Kernel Two-Sample Test** — [arxiv_lg](https://arxiv.org/abs/2605.01775v1)
- **Mitigating Multimodal LLMs Hallucinations via Relevance Propagation at Inference Time** — [arxiv_lg](https://arxiv.org/abs/2605.01766v1)
- **Distributional Causal Mediation via Conditional Generative Modeling** — [arxiv_lg](https://arxiv.org/abs/2605.01765v1)
- **Prescriptive Scaling Laws for Data Constrained Training** — [arxiv_cl](https://arxiv.org/abs/2605.01640v1)
- **From Stealthy Data Fabrication to Unsafe Driving: Realistic Scenario Attacks on Collaborative Perception** — [arxiv_cr](https://arxiv.org/abs/2605.01301v1)
- **FP-Agent: Fingerprinting AI Browsing Agents** — [arxiv_cr](https://arxiv.org/abs/2605.01247v1)
- **Write-Domain Separation and Non-Custodial Enforcement: A Structural Impossibility in Account-Based Ledgers, with a Commitment-Based Construction** — [arxiv_cr](https://arxiv.org/abs/2605.01210v1)
- **Phishing Detection in Ethereum via Temporal Graph Contrastive Learning** — [arxiv_cr](https://arxiv.org/abs/2605.01207v1)
- **OpenAI’s president does ‘all the things,’ except answer a question** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/923684/musk-brockman-altman-openai-trial)
- **The creator of Roomba is back with a furry robot companion** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/922947/roomba-creator-new-robot-familiar-machines-magic-ai-launch)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **Sierra raises $950M as the race to own enterprise AI gets serious** — [techcrunch_ai](https://techcrunch.com/2026/05/04/sierra-raises-950m-as-the-race-to-own-enterprise-ai-gets-serious/)
- **Elon Musk sent ominous texts to Greg Brockman, Sam Altman after asking for a settlement, OpenAI claims** — [techcrunch_ai](https://techcrunch.com/2026/05/04/elon-musk-sent-ominous-texts-to-greg-brockman-sam-altman-after-asking-for-a-settlement-openai-claims/)
- **5 days only: Bring a partner or colleague and get 50% off a second TechCrunch Disrupt 2026 pass** — [techcrunch_ai](https://techcrunch.com/2026/05/04/5-days-only-bring-a-partner-or-colleague-and-get-50-off-a-second-techcrunch-disrupt-2026-pass/)
- **Week one of the Musk v. Altman trial: What it was like in the room** — [mit_tech_review](https://www.technologyreview.com/2026/05/04/1136826/week-one-of-the-musk-v-altman-trial-what-it-was-like-in-the-room/)
- **DoorDash adds AI tools to speed up merchant onboarding, edit photos of dishes** — [techcrunch_ai](https://techcrunch.com/2026/05/04/doordash-adds-ai-tools-to-speed-up-merchant-onboarding-edit-photos-of-dishes/)
- **Tailoring AI solutions for health care needs** — [mit_tech_review](https://www.technologyreview.com/2026/05/04/1134425/tailoring-ai-solutions-for-health-care-needs/)
- **OpenAI’s cozy partner Cerebras is on track for a blockbuster IPO** — [techcrunch_ai](https://techcrunch.com/2026/05/04/openais-cozy-partner-cerebras-is-on-track-for-a-blockbuster-ipo/)
- **Image AI models now drive app growth, beating chatbot upgrades** — [techcrunch_ai](https://techcrunch.com/2026/05/04/image-ai-models-now-drive-app-growth-beating-chatbot-upgrades/)
- **Elon Musk’s only AI expert witness at the OpenAI trial fears an AGI arms race** — [techcrunch_ai](https://techcrunch.com/2026/05/04/elon-musks-only-expert-witness-at-the-openai-trial-fears-an-agi-arms-race/)
- **The latest AI news we announced in April 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/google-ai-updates-april-2026/)
- **Anthropic and OpenAI are both launching joint ventures for enterprise AI services** — [techcrunch_ai](https://techcrunch.com/2026/05/04/anthropic-and-openai-are-both-launching-joint-ventures-for-enterprise-ai-services/)
- **Reduce friction and latency for long-running jobs with Webhooks in Gemini API** — [google_ai](https://blog.google/innovation-and-ai/technology/developers-tools/event-driven-webhooks/)
- **csy-csy123/pr-review-agent-council** — [github](https://github.com/csy-csy123/pr-review-agent-council)
- **liangdabiao/llm-wiki** — [github](https://github.com/liangdabiao/llm-wiki)
- **0xbl33p/goblintown** — [github](https://github.com/0xbl33p/goblintown)
- **dmae97/oh-my-kimi** — [github](https://github.com/dmae97/oh-my-kimi)
- **Abishek-kk/AutoMart-AI** — [github](https://github.com/Abishek-kk/AutoMart-AI)
- **KSroido/Kagi-Session2API-MCP** — [github](https://github.com/KSroido/Kagi-Session2API-MCP)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **warpdot-dev/craft-agents-oss** — [github](https://github.com/warpdot-dev/craft-agents-oss)
- **endless-sky-team/ai-trading-agent** — [github](https://github.com/endless-sky-team/ai-trading-agent)
- **warpdot-dev/composio** — [github](https://github.com/warpdot-dev/composio)
- **StartupHakk/OpenMonoAgent.ai** — [github](https://github.com/StartupHakk/OpenMonoAgent.ai)
- **lukiIabs/trading-agents** — [github](https://github.com/lukiIabs/trading-agents)
- **Senabayu08989/Stable-Diffusion-AI-Free** — [github](https://github.com/Senabayu08989/Stable-Diffusion-AI-Free)
- **Julpygo/Claude-Code-AI-Design** — [github](https://github.com/Julpygo/Claude-Code-AI-Design)
- **YutoTerashima/agent-safety-eval-lab** — [github](https://github.com/YutoTerashima/agent-safety-eval-lab)
- **Dsadd4/AgentFigureGallery** — [github](https://github.com/Dsadd4/AgentFigureGallery)
- **prime-radiant-inc/books-for-bots** — [github](https://github.com/prime-radiant-inc/books-for-bots)
- **bensenescu/downy** — [github](https://github.com/bensenescu/downy)
- **houyuanchen111/UniVidX** — [github](https://github.com/houyuanchen111/UniVidX)
- **“DeepSeek版Claude Code”，Github 2.3k星** — [qbitai](https://www.qbitai.com/2026/05/412914.html)
- **五月，适合想清楚一件事｜幕启** — [36kr](https://36kr.com/p/3794961189821698?f=rss)
- **豆包将在免费模式外新增付费订阅，推出三档月包/年包价格｜最前线** — [36kr](https://36kr.com/p/3794799114476809?f=rss)
- **陈发树一季度新进伊利股份，持股市值近16亿元** — [36kr](https://36kr.com/newsflashes/3794771402185991?f=rss)
- **港交所拟重启黄金期货交易** — [36kr](https://36kr.com/newsflashes/3794732876700931?f=rss)
- **豆包将在免费模式外新增付费订阅，官方回应** — [36kr](https://36kr.com/newsflashes/3794495772712195?f=rss)
- **剂泰科技寻求通过香港IPO募资21.1亿港元** — [36kr](https://36kr.com/newsflashes/3795702003981319?f=rss)
- **精锻科技：当前公司机器人业务尚未形成销售收入** — [36kr](https://36kr.com/newsflashes/3794483360046337?f=rss)
- **恒指午间休盘涨1.7%，恒生科技指数涨2.86%** — [36kr](https://36kr.com/newsflashes/3794457822059523?f=rss)
- **印度数据中心公司Yotta：公司在IPO前寻求60亿美元的估值** — [36kr](https://36kr.com/newsflashes/3794749752728585?f=rss)
- **Model Routing as a Trust Problem: Route Receipts for Adaptive AI Systems** — [arxiv_ai](https://arxiv.org/abs/2605.01710v1)
- **Evaluating Agentic AI in the Wild: Failure Modes, Drift Patterns, and a Production Evaluation Framework** — [arxiv_ai](https://arxiv.org/abs/2605.01604v1)
- **GRAVITY: Architecture-Agnostic Structured Anchoring for Long-Horizon Conversational Memory** — [arxiv_ai](https://arxiv.org/abs/2605.01688v1)
- **Hallucinations Undermine Trust; Metacognition is a Way Forward** — [arxiv_cl](https://arxiv.org/abs/2605.01428v1)
- **lthoangg/openagentd** — [github](https://github.com/lthoangg/openagentd)
- **NyxFoundation/speca** — [github](https://github.com/NyxFoundation/speca)
- **MemORAI: Memory Organization and Retrieval via Adaptive Graph Intelligence for LLM Conversational Agents** — [arxiv_cl](https://arxiv.org/abs/2605.01386v1)
- **Neuro-Symbolic Agents for Hallucination-Free Requirements Reuse** — [arxiv_ai](https://arxiv.org/abs/2605.01562v1)
- **Multi-Agent Reasoning Improves Compute Efficiency: Pareto-Optimal Test-Time Scaling** — [arxiv_ai](https://arxiv.org/abs/2605.01566v1)
- **matty69v/Bug-Bounty-Agents** — [github](https://github.com/matty69v/Bug-Bounty-Agents)