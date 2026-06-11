# AI Daily Digest [AI 安全] - 2026-06-11


# Daily Thematic Digest: AI Safety & Agent Governance
**Date:** 2026-06-11  
**Theme:** Agent Security, Runtime Safety, Alignment, and Evaluation

## Highlights

Three critical developments define the current landscape of agentic safety research. First, the industry is shifting from perimeter-based enterprise security to **runtime governance architectures**. New proposals like the **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** argue that existing policy engines fail to govern sequences of actions where risk moves inside the workflow, necessitating a new control plane that intercepts agent proposals before execution. Second, **memory integrity** has emerged as a primary vulnerability vector. Research on **Selection Integrity for LLM Graph Memory** demonstrates that current provenance defenses are blind to structure manipulation, where untrusted writes alter which authenticated facts are selected, creating a systemic risk for long-term agent memory. Third, evaluation frameworks are struggling to keep pace with capability. While **WorldOlympiad** introduces a triathlon-style benchmark for physical faithfulness and interaction fidelity, practical deployment still faces gaps in measuring **epistemic resilience**, as shown in **Measuring Epistemic Resilience of LLMs Under Misleading Medical Context**, where high exam scores do not guarantee safe judgment under adversarial context injection.

## Agent Security & Governance

The transition from static tool-use to autonomous multi-step agents requires a fundamental rethinking of security boundaries. Traditional enterprise security governed data at rest and in transit, but production AI agents dissolve these assumptions by modifying systems of record on behalf of users. In response, researchers propose **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents**, which posits that risk now resides in sequences of individually-permitted actions that may transform a business process no one authorized. This architectural shift complements the **Sovereign Assurance Boundary: Certificate-Bound Admission for Agentic Infrastructure**, which introduces a certificate-bound runtime admission layer. Unlike existing IAM or audit logs that enforce static permissions or record actions post-execution, the Sovereign Assurance Boundary intercepts agent proposals at an assurance airlock, ensuring non-deterministic reasoning systems cannot propose high-stakes mutations without cryptographic verification.

While governance architectures address the macro-level control plane, micro-level risks persist in how agents manage state and skills. The **Runtime Skill Audit: Targeted Runtime Probing for Agent Skill Security** paper highlights that static vetting is brittle because a skill may appear benign in documentation yet become harmful when invoked with specific user requests or persistent state. This finding contradicts the assumption that sandboxing alone suffices; instead, dynamic analysis is required to audit what a skill-mediated agent actually does under targeted conditions. Similarly, the adoption of persistent memory introduces new attack surfaces. **PROJECTMEM: A Local-First, Event-Sourced Memory and Judgment Layer for AI Coding Agents** addresses the cost of reconstructing project context, recording development as an append-only journal. However, **Selection Integrity for LLM Graph Memory** warns that even with event sourcing, graph memory runs a global selection step over writable structures. If an untrusted principal writes to the graph, they change which authenticated facts are selected while cited evidence remains fully authenticated, rendering faithful information-flow control blind by construction.

Governance extends beyond code and memory into the operational environment itself. **Rule Taxonomy and Evolution in AI IDEs: A Mining and Survey Study** reveals that developers inject project-specific constraints into LLM contexts via "Rules," yet the evolution and impact of these artifacts remain unexplored. Without systematic tracking, these rules can drift from developer intent, effectively becoming hidden policies that align or misalign agent behavior. To mitigate cross-device and cross-session risks, open-source initiatives like **MemoryCloud** aim to manage agent memory like a GitHub repo, allowing agents to switch devices while retaining learned rules and session states. However, this centralization of memory raises questions about access control. **OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents** frames privacy not as a property of single outputs but of entire trajectories, noting that leakage is cumulative and bidirectional. Malicious observations can inject instructions that turn honest-but-curious sinks into inference channels, suggesting that runtime governance must include budget limits on information flow across trust boundaries.

## Tool/Prompt Injection & Runtime Defenses

As agents gain multimodal capabilities and tool-use authority, the attack surface expands beyond text prompts to physical interfaces and code generation pipelines. **Grammar-Constrained Decoding Can Jailbreak LLMs into Generating Malicious Code** uncovers a counterintuitive risk where reliability-oriented techniques like Grammar-Constrained Decoding (GCD) become attack surfaces. By exploiting GCD to induce syntactic validity, attackers can jailbreak models into generating malicious code that passes validation checks. This suggests that enforcing syntactic correctness without semantic verification creates a false sense of security. In parallel, **WarpGuard: Protected-Site Control-Flow Integrity for CUDA SASS Binaries** addresses hardware-level exploitation, showing that GPU memory bugs can escalate into device-side control-flow corruption. For deployed CUDA binaries, the security boundary is executed NVIDIA SASS, meaning source-level policies do not capture this risk, requiring protected-site CFI systems operating on executable binaries.

Runtime monitoring is essential for detecting deviations in live environments. **Online Shift Detection and Conformal Adaptation for Deployed Safety Classifiers** presents a system using calibrated sequential statistics to detect distributional shifts. Upon detection, a conformal abstention layer adapts decision thresholds to recover target error rates, achieving 86.6% valid detection across ground-truth regimes. This proactive defense contrasts with reactive measures found in **DrivingAgent: Design and Scheduling Agents for Autonomous Driving Systems**, which notes that existing frameworks fail to distinguish between fundamentally different requirements for perception, planning, and flight control in real-time constraints. The lack of intelligent scheduling mechanisms limits flexibility and reproducibility in autonomous aerial systems, as seen in **AerialClaw: An Open-Source Framework for LLM-Driven Autonomous Aerial Agents**, which enables UAVs to operate as decision-making agents rather than pre-defined command sequences.

Efficiency in runtime also impacts safety through resource management. **Context-Driven Incremental Compression for Multi-Turn Dialogue Generation** revisits context compression under conversational dynamics, empirically presenting its fragility. Naive truncation degrades fidelity, while existing compressors lack cross-turn memory sharing, causing compounding errors. To improve efficiency without sacrificing safety, **ctx-wire** offers a runtime-neutral driver that compresses output with declarative filters and scrubs secrets, handing agents short results while keeping full logs on disk for failure analysis. Furthermore, **DIRECT: When and Where Should You Allocate Test-Time Compute in Embodied Planners?** argues that choosing when and where to spend test-time compute is central to bringing frontier performance to the real world. The routing framework uses multimodal scene context to allocate compute per task, addressing the observation that scaling test-time compute increases latency and token usage while yielding uneven gains.

## Adversarial Attacks & Robustness

Evaluating robustness requires moving beyond fixed query budgets to account for computational effort. **Risk Under Pressure: Compute-Aware Evaluation of Adversarial Robustness in Language Models** proposes a framework based on computational pressure, measured in cumulative floating-point operations. ASR at a fixed budget can obscure the true effort required to jailbreak a model, making it hard to determine whether an attack's cost justifies its payoff. This metric provides a more realistic assessment of security posture than traditional success rates. Complementing this, **Reinforcement Learning Disrupts Gradient-Based Adversarial Optimization** investigates whether RL training can disrupt gradient structure used by attackers. Experiments across CIFAR-10 and ImageNet show that RL-trained classifiers significantly disrupt gradient-based adversarial optimization, suggesting a potential pathway for defensive training strategies.

Epistemic resilience—the ability to maintain correct judgment under adversarial context—is another critical dimension often overlooked. **Measuring Epistemic Resilience of LLMs Under Misleading Medical Context** shows that when misleading context is injected into questions LLMs originally answer correctly, they abandon the correct answer. High scores on medical licensing exams do not imply safe medical judgment, as the assumption is fragile. This aligns with findings in **The Impossibility of Eliciting Latent Knowledge**, which argues that designing an AI system to be honest about latent variables in the environment is difficult, especially if we want to ask it questions about hidden variables. Consequently, honesty may be compromised if the system prioritizes plausible sounding answers over accurate reporting of uncertainty.

Post-training dynamics also play a role in robustness. **Anatomy of Post-Training: Using Interpretability to Characterize Data and Shape the Learning Signal** asks whether practitioners can inspect a preference dataset before optimization to decide which behaviors a model should learn. Spurious correlations can be learned by a model, inducing undesirable behaviors such as over-stylization and sycophancy. **Feedback Alignment in Self-Distillation** further explores how conditioning a language model on additional context improves response, but the design of this context remains largely unexplored. Matching the model's output distribution under two settings—a student seeing only the question and a self-teacher seeing context—depends heavily on what context the self-teacher receives. These findings suggest that robustness is not just a function of model architecture but of the data and feedback loops used during fine-tuning.

## Safety Benchmarks & Evaluation

Benchmarking long-horizon agentic tasks remains a bottleneck for reliable evaluation. **Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks** introduces a multilingual SWE-bench-style benchmark and adapter protocol that makes heterogeneous agent harnesses comparable under fair settings. It includes a fixed prompt, runtime budget, workspace contract, patch extraction procedure, and evaluator. This standardization is crucial because general-purpose agents do not satisfy the clean Docker workspace and prediction contract required for scoring. Similarly, **Workflow-GYM: Towards Long-Horizon Evaluation of Computer-use Agentic tasks in Real-World Professional Fields** addresses the gap where existing benchmarks rarely evaluate whether agents can operate graphical user interfaces to complete long-horizon, high-value professional workflows across diverse domains. Current GUI benchmarks predominantly focus on general-purpose software, leaving it unknown whether modern agents can follow user instructions to autonomously operate domain-specific professional software.

For embodied and world-model agents, evaluation must extend beyond visual quality to physical and temporal consistency. **WorldOlympiad: Can Your World Model Survive a Triathlon?** decomposes world-model evaluation into three complementary dimensions: physical track, geometric track, and interaction track. While existing benchmarks focus on visual quality or short-term coherence, WorldOlympiad diagnoses whether generated videos obey physical rules and sustain controllable interactions over long horizons. This is particularly relevant for **Intelligent Automation for Embodied Benchmark Construction: Pipelines, Embodiments, Simulators, and Trends**, which reviews the literature through a five-stage construction pipeline including requirement and task construction, data acquisition, and release policies. The survey emphasizes that unlike static datasets, embodied benchmarks combine task specifications, environments, robot data, demonstrations, annotations, metrics, and evaluation scripts into a single evaluation system.

Simulation fidelity is also critical for social and strategic simulations. **Evaluation of Alternative-Based Information Systems for Deliberative Polling using an Agentic Simulator** introduces a way of evaluating solutions using the LLM-based Agentic Bipolar Argumentation Simulator. This formalizes a poll as a six-tuple of endorsing and opposing justificatory arguments, addressing the coverage problem at scale. However, **Should LLM Agents Decide in Social Simulations? Comparing Finite-State and LLM-Based Decision Policies** evaluates whether LLM action selectors preserve an interpretable reference policy in an OSN simulation. The study finds methodological risks where the simulation may deviate from the explicit behavioral policy defined by the researcher, highlighting the need for rigorous validation of agent decision policies in social contexts.

## Looking Forward

Several unresolved theoretical questions await validation as agentic systems mature. First, the tension between **memory efficiency and integrity** remains open. While **PROJECTMEM** offers local-first event sourcing, **Selection Integrity for LLM Graph Memory** proves that structure manipulation can bypass provenance checks. Future work must reconcile efficient memory retrieval with provable guarantees against untrusted writes in shared graph structures. Second, **test-time compute allocation** lacks a unified theory. **DIRECT** proposes routing based on multimodal context, but the optimal strategy for balancing latency, token usage, and downstream success across diverse embodied tasks is not yet established. Finally, **alignment verification** needs to move beyond static benchmarks. As **Measuring Epistemic Resilience** demonstrates, high accuracy on standard tests does not prevent context-dependent failures. Developing metrics that measure stability under adversarial context injection, similar to the compute-aware evaluation proposed in **Risk Under Pressure**, will be essential for deploying agents in high-stakes environments. The community must also address the regulatory fragmentation highlighted in recent reports, where conflicting data retention policies and guardrail strictness impede consistent safety standards across jurisdictions.

---


## References

- **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** — [arxiv_ai](https://arxiv.org/abs/2606.12320v1)
- **InternVideo3: Agentify Foundation Models with Multimodal Contextual Reasoning** — [arxiv_cv](https://arxiv.org/abs/2606.12195v1)
- **Agentic Environment Engineering for Large Language Models: A Survey of Environment Modeling, Synthesis, Evaluation, and Application** — [arxiv_ai](https://arxiv.org/abs/2606.12191v1)
- **AerialClaw: An Open-Source Framework for LLM-Driven Autonomous Aerial Agents** — [arxiv_cv](https://arxiv.org/abs/2606.12142v1)
- **PROJECTMEM: A Local-First, Event-Sourced Memory and Judgment Layer for AI Coding Agents** — [arxiv_ai](https://arxiv.org/abs/2606.12329v1)
- **Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks** — [arxiv_cl](https://arxiv.org/abs/2606.12344v1)
- **WorldReasoner: Evaluating Whether Language Model Agents Forecast Events with Valid Reasoning** — [arxiv_cl](https://arxiv.org/abs/2606.11816v1)
- **Workflow-GYM: Towards Long-Horizon Evaluation of Computer-use Agentic tasks in Real-World Professional Fields** — [huggingface_papers](https://arxiv.org/abs/2606.11042)
- **APPO: Agentic Procedural Policy Optimization** — [arxiv_ai](https://arxiv.org/abs/2606.12384v1)
- **External Experience Serving in Production LLM Systems: A Deployment-Oriented Study of Quality-Cost Trade-offs** — [arxiv_cl](https://arxiv.org/abs/2606.11806v1)
- **OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12341v1)
- **Sovereign Assurance Boundary: Certificate-Bound Admission for Agentic Infrastructure** — [arxiv_cr](https://arxiv.org/abs/2606.11632v1)
- **DIRECT: When and Where Should You Allocate Test-Time Compute in Embodied Planners?** — [arxiv_ai](https://arxiv.org/abs/2606.12402v1)
- **TAHOE: Text-to-SQL with Automated Hint Optimization from Experience** — [arxiv_ai](https://arxiv.org/abs/2606.12387v1)
- **DrivingAgent: Design and Scheduling Agents for Autonomous Driving Systems** — [arxiv_cv](https://arxiv.org/abs/2606.12236v1)
- **Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval** — [arxiv_cr](https://arxiv.org/abs/2606.12290v1)
- **Notes2Skills: From Lab Notebooks to Certainty-Aware Scientific Agent Skills** — [arxiv_cl](https://arxiv.org/abs/2606.11897v1)
- **Can Open-Source LLM Agents Replace Static Application Security Testing Tools? An Empirical Assessment** — [arxiv_cr](https://arxiv.org/abs/2606.11672v1)
- **Runtime Skill Audit: Targeted Runtime Probing for Agent Skill Security** — [arxiv_cr](https://arxiv.org/abs/2606.11671v1)
- **One Token per Multimodal Evidence: Latent Memory for Resource-Constrained QA** — [huggingface_papers](https://arxiv.org/abs/2606.10572)
- **DeNovoSWE: Scaling Long-Horizon Environments for Generating Entire Repositories from Scratch** — [huggingface_papers](https://arxiv.org/abs/2606.10728)
- **Kwai Keye-VL-2.0 Technical Report** — [huggingface_papers](https://arxiv.org/abs/2606.10651)
- **Intelligent Automation for Embodied Benchmark Construction: Pipelines, Embodiments, Simulators, and Trends** — [arxiv_ai](https://arxiv.org/abs/2606.12207v1)
- **Context-Driven Incremental Compression for Multi-Turn Dialogue Generation** — [arxiv_cl](https://arxiv.org/abs/2606.12411v1)
- **UniIntervene: Agentic Intervention for Efficient Real-World Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.12372v1)
- **uva-irlab-conv at SemEval-2026 Task 8: Multi-Turn RAG with Learned Sparse Retrieval and Listwise Reranking** — [arxiv_cl](https://arxiv.org/abs/2606.11945v1)
- **WarpGuard: Protected-Site Control-Flow Integrity for CUDA SASS Binaries** — [arxiv_cr](https://arxiv.org/abs/2606.11871v1)
- **Role-Agent: Bootstrapping LLM Agents via Dual-Role Evolution** — [huggingface_papers](https://arxiv.org/abs/2606.10917)
- **Risk Under Pressure: Compute-Aware Evaluation of Adversarial Robustness in Language Models** — [arxiv_cr](https://arxiv.org/abs/2606.11409v1)
- **ATLAS: Active Theory Learning for Automated Science** — [arxiv_ai](https://arxiv.org/abs/2606.12386v1)
- **CCKS: Consensus-based Communication and Knowledge Sharing** — [arxiv_ai](https://arxiv.org/abs/2606.12281v1)
- **The Impossibility of Eliciting Latent Knowledge** — [arxiv_ai](https://arxiv.org/abs/2606.12268v1)
- **Doc-to-Atom: Learning to Compile and Compose Memory Atoms** — [arxiv_cl](https://arxiv.org/abs/2606.12400v1)
- **Toward Generalist Autonomous Research via Hypothesis-Tree Refinement** — [arxiv_cl](https://arxiv.org/abs/2606.11926v1)
- **An Ontology-Guided Multi-Anchor Graph Retrieval Framework for Traffic Legal Liability Determination** — [arxiv_cl](https://arxiv.org/abs/2606.11910v1)
- **VIPIR: A Versatile GPU Framework for Integrating Private Information Retrieval Protocols** — [arxiv_cr](https://arxiv.org/abs/2606.11536v1)
- **MPC-Patch-Bench: Security-Aware LLM Code Patch for Multi-Party Computation** — [arxiv_cr](https://arxiv.org/abs/2606.11416v1)
- **Decentralized Multi-Agent Systems with Shared Context** — [huggingface_papers](https://arxiv.org/abs/2606.10662)
- **Multi-Rate Mixture of Experts for Accelerating Liquid Neural Network Training** — [arxiv_ai](https://arxiv.org/abs/2606.12240v1)
- **Bridging Day and Night: Unsupervised Cross-Domain Re-Identification with Synergistic Prompt and Prototype Learning** — [arxiv_cv](https://arxiv.org/abs/2606.12258v1)
- **Categorical Robustness Assessment for Machine Learning based Network Intrusion Detection Systems** — [arxiv_lg](https://arxiv.org/abs/2606.12075v1)
- **DiffCold: A Diffusion-based Generative Model for Cold-Start Item Recommendation** — [arxiv_ai](https://arxiv.org/abs/2606.12245v1)
- **Implicit Neural Representations of Individual Behavior** — [arxiv_ai](https://arxiv.org/abs/2606.12200v1)
- **Bridging the Modality Gap in Forensic Image Retrieval** — [arxiv_cv](https://arxiv.org/abs/2606.12294v1)
- **Measuring Epistemic Resilience of LLMs Under Misleading Medical Context** — [arxiv_cl](https://arxiv.org/abs/2606.12291v1)
- **Fourier Features Let Agents Learn High Precision Policies with Imitation Learning** — [arxiv_lg](https://arxiv.org/abs/2606.12334v1)
- **MLT-Dedup: Efficient Large-Scale Online Video Deduplication via Multi-Level Representations and Spatial-Temporal Matching** — [arxiv_lg](https://arxiv.org/abs/2606.12215v1)
- **Augmenting Molecular Language Models with Local $n$-gram Memory** — [arxiv_ai](https://arxiv.org/abs/2606.12113v1)
- **FORT-Searcher: Synthesizing Shortcut-Resistant Search Tasks for Training Deep Search Agents** — [arxiv_cl](https://arxiv.org/abs/2606.12087v1)
- **When Does Language Matter? Multilingual Instructions Reveal Step-wise Language Sensitivity in Vision-Language-Action Models** — [arxiv_cl](https://arxiv.org/abs/2606.11906v1)
- **SwarmSense-DNN: A Trustworthy and Decentralized Neural Framework for Proactive Anomaly Defense in Consumer IoT** — [arxiv_cr](https://arxiv.org/abs/2606.11803v1)
- **ICA Lens: Interpreting Language Models Without Training Another Dictionary** — [huggingface_papers](https://arxiv.org/abs/2606.11722)
- **EEVEE: Towards Test-time Prompt Learning in the Real World for Self-Improving Agents** — [huggingface_papers](https://arxiv.org/abs/2606.11182)
- **Reinforcement Learning Disrupts Gradient-Based Adversarial Optimization** — [arxiv_ai](https://arxiv.org/abs/2606.12251v1)
- **Toward Trustworthy AI: Multi-Target Adversarial Attacks and Robust Defenses for Continuous Data Summarization** — [arxiv_cr](https://arxiv.org/abs/2606.11804v1)
- **Reroute, Don't Remove: Recoverable Visual Token Routing for Vision-Language Models** — [arxiv_ai](https://arxiv.org/abs/2606.12412v1)
- **SPEA2$^+$: Improved Density Estimation in SPEA2 with Provable Runtime Guarantees** — [arxiv_ai](https://arxiv.org/abs/2606.12382v1)
- **Natural-Language Temporal Grounding in Hour-Long Videos is a Search Problem: A Benchmark and Empirical Decomposition** — [arxiv_ai](https://arxiv.org/abs/2606.12300v1)
- **Rule Taxonomy and Evolution in AI IDEs: A Mining and Survey Study** — [arxiv_ai](https://arxiv.org/abs/2606.12231v1)
- **Echoes of the Prior: A Computational Phenomenology of Forgetting** — [arxiv_cv](https://arxiv.org/abs/2606.12340v1)
- **AGE-MIL: Anchor-Guided Evidence Learning for Patient-Level Prediction** — [arxiv_cv](https://arxiv.org/abs/2606.12126v1)
- **Which Models Are Our Models Built On? Auditing Invisible Dependencies in Modern LLMs** — [arxiv_cl](https://arxiv.org/abs/2606.12385v1)
- **Breaking Entropy Bounds: Accelerating RL Training via MTP with Rejection Sampling** — [arxiv_cl](https://arxiv.org/abs/2606.12370v1)
- **Findings of the MAGMaR 2026 Shared Task** — [arxiv_cl](https://arxiv.org/abs/2606.12295v1)
- **ECYSAP EYE: From Cyber Situational Awareness to Mission-Centric Decision Support for Enhanced Cyberspace Operations** — [arxiv_cr](https://arxiv.org/abs/2606.12354v1)
- **On Subquadratic Architectures: From Applications to Principles** — [arxiv_lg](https://arxiv.org/abs/2606.12364v1)
- **Holding the FP8 Quality Ceiling at 8-Bit Weights and Activations: INT8 and GGUF Post-Training Quantization of Ideogram 4.0 for Consumer GPUs** — [arxiv_lg](https://arxiv.org/abs/2606.12280v1)
- **Soft-Prompt Tuning for Fair and Efficient LLM Benchmark Evaluation** — [arxiv_ai](https://arxiv.org/abs/2606.12117v1)
- **World Model Self-Distillation: Training World Models to Solve General Tasks** — [arxiv_cv](https://arxiv.org/abs/2606.12072v1)
- **Fine-tuning Multi-modal LLMs with ART: Art-based Reinforcement Training** — [arxiv_cl](https://arxiv.org/abs/2606.11854v1)
- **InjectV: Modeling Fault Injection Attacks in RISC-V Simulation Environment** — [arxiv_cr](https://arxiv.org/abs/2606.12011v1)
- **A Deterministic Forensic Preprocessing Framework for Heterogeneous Network Datasets: Formal Foundations, Implementation, and Empirical Validation** — [arxiv_cr](https://arxiv.org/abs/2606.11565v1)
- **WHET: Welding Homomorphic Encryption to Accelerator Architectures** — [arxiv_cr](https://arxiv.org/abs/2606.11541v1)
- **OpenPCC: Open and Confidential LLM Serving on Commodity TEEs** — [arxiv_cr](https://arxiv.org/abs/2606.11145v1)
- **Next Forcing: Causal World Modeling with Multi-Chunk Prediction** — [huggingface_papers](https://arxiv.org/abs/2606.11187)
- **FadeMem: Distance-Aware Memory Consolidation for Autoregressive Video Diffusion** — [huggingface_papers](https://arxiv.org/abs/2606.10671)
- **Attention Amnesia in Hybrid LLMs: When CoT Fine-Tuning Breaks Long-Range Recall, and How to Fix It** — [huggingface_papers](https://arxiv.org/abs/2606.11052)
- **Dynamic Linear Attention** — [huggingface_papers](https://arxiv.org/abs/2606.10650)
- **Can News Predict the Market? Limits of Zero-Shot Financial NLP and the Role of Explainable AI** — [arxiv_cl](https://arxiv.org/abs/2606.12210v1)
- **BrainSurgery: Reproducible and Reliable Declarative Weight Manipulations for Model Editing and Upcycling** — [huggingface_papers](https://arxiv.org/abs/2606.09707)
- **ISAP-3D: Identity-Slot Aligned Part-Aware 3D Generation** — [arxiv_cv](https://arxiv.org/abs/2606.12099v1)
- **Grammar-Constrained Decoding Can Jailbreak LLMs into Generating Malicious Code** — [arxiv_cl](https://arxiv.org/abs/2606.11817v1)
- **Superspace Concentration and Adversarial Robustness in Quantum Algorithms** — [arxiv_cr](https://arxiv.org/abs/2606.11580v1)
- **Anchors that Don't Lift: Understanding Supply Chain Driven Kernel Lock-In and Governance-Mediated Mitigation Strategies in SOHO Devices** — [arxiv_cr](https://arxiv.org/abs/2606.11175v1)
- **When the Chain of Thought Knows Better: Failure Modes in Multi-Turn Reasoning Models** — [huggingface_papers](https://arxiv.org/abs/2606.10740)
- **UniPET: a universal network for high-quality PET image denoising across varied dose reduction factors** — [huggingface_papers](https://arxiv.org/abs/2606.11131)
- **Flow-DPPO: Divergence Proximal Policy Optimization for Flow Matching Models** — [huggingface_papers](https://arxiv.org/abs/2606.11025)
- **VLGA: Vision-Language-Geometry-Action Models for Autonomous Driving** — [arxiv_cv](https://arxiv.org/abs/2606.12396v1)
- **An Electric Potential-Augmented Benchmark Dataset for Physics-Guided Image Reconstruction of Electrical Capacitance Tomography** — [arxiv_cv](https://arxiv.org/abs/2606.12226v1)
- **Measuring Semantic Progress in Multi-turn Dialogue via Information Gain** — [arxiv_cl](https://arxiv.org/abs/2606.12332v1)
- **Reassessing High-Performing LLMs on Polish Medical Exams: True Competence or Bias-Driven Performance?** — [arxiv_cl](https://arxiv.org/abs/2606.12250v1)
- **Anatomy of Post-Training: Using Interpretability to Characterize Data and Shape the Learning Signal** — [arxiv_lg](https://arxiv.org/abs/2606.12360v1)
- **Learning What to Say to Your VLA: Mostly Harmless Vision Language Action Model Steering** — [arxiv_lg](https://arxiv.org/abs/2606.12299v1)
- **Tac-DINO: Learning Vision-Tactile Features with Patch Alignment** — [arxiv_cv](https://arxiv.org/abs/2606.12069v1)
- **Vision Transformers for Face Recognition Need More Registers** — [arxiv_cv](https://arxiv.org/abs/2606.12036v1)
- **ViT-FREE: Efficient Face Recognition via Early Exiting and Synthetic Adaptation** — [arxiv_cv](https://arxiv.org/abs/2606.12023v1)
- **From Nominal Intensity to Equivalent Rainfall: A Path-Based Credibility Evaluation Framework for Simulated Rainfall in Autonomous-Driving Perception Tests** — [arxiv_cv](https://arxiv.org/abs/2606.11989v1)
- **Online Shift Detection and Conformal Adaptation for Deployed Safety Classifiers** — [arxiv_cr](https://arxiv.org/abs/2606.11949v1)
- **Feature-Aligned Speech Watermarking for Robustness to Reconstruction Distortions** — [arxiv_cr](https://arxiv.org/abs/2606.11828v1)
- **Lip Forcing: Few-Step Autoregressive Diffusion for Real-time Lip Synchronization** — [huggingface_papers](https://arxiv.org/abs/2606.11180)
- **Beyond Uniform Token-Level Trust Region in LLM Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2606.10968)
- **The Role of Feedback Alignment in Self-Distillation** — [huggingface_papers](https://arxiv.org/abs/2606.11173)
- **WorldOlympiad: Can Your World Model Survive a Triathlon?** — [huggingface_papers](https://arxiv.org/abs/2606.11129)
- **How Seemingly Inconsequential Design Choices Dictate Performance of LLMs in Pathology** — [arxiv_cv](https://arxiv.org/abs/2606.12407v1)
- **Semantically-Aware Diver Activity Recognition Framework for Effective Underwater Multi-Human-Robot Collaboration** — [arxiv_cv](https://arxiv.org/abs/2606.12374v1)
- **A Turbo-Inference Strategy for Object Detection and Instance Segmentation** — [arxiv_cv](https://arxiv.org/abs/2606.12371v1)
- **DepthMaster: Unified Monocular Depth Estimation for Perspective and Panoramic Images** — [arxiv_cv](https://arxiv.org/abs/2606.12368v1)
- **Anatomically Conditioned Recurrent Refinement for Topology-Aware Circle of Willis Segmentation** — [arxiv_cv](https://arxiv.org/abs/2606.12319v1)
- **Adjoint Method versus Physics-Informed Neural Networks in PDE-Constrained Inverse Problems** — [arxiv_lg](https://arxiv.org/abs/2606.12337v1)
- **PianoKontext: Expressive Performance Rendering from Deadpan Context** — [arxiv_lg](https://arxiv.org/abs/2606.12282v1)
- **Finding Sparse Subnetworks in One Training Cycle via Progressive Magnitude-Based Pruning** — [arxiv_lg](https://arxiv.org/abs/2606.12278v1)
- **Finding Multiple Interpretations in Datasets** — [arxiv_lg](https://arxiv.org/abs/2606.12277v1)
- **Re-evaluating Confidence Remasking in Masked Diffusion Language Models** — [arxiv_lg](https://arxiv.org/abs/2606.12232v1)
- **Quantum Occam Learning: Sample-Supported Expressibility for Circuit-Based Quantum Learning** — [arxiv_lg](https://arxiv.org/abs/2606.12211v1)
- **How Low Can You Go? Active Learning for Sparse Model Discovery in the Ultra-Low-Data Limit** — [arxiv_lg](https://arxiv.org/abs/2606.12182v1)
- **Beyond Dark Knowledge: Mixup-Based Distillation for Reliable Predictions** — [arxiv_lg](https://arxiv.org/abs/2606.12171v1)
- **PCA-Enhanced Adaptive NVAR Framework for High-Resolution Sea Surface Temperature Forecasting in the East Sea** — [arxiv_lg](https://arxiv.org/abs/2606.12141v1)
- **A Riemannian Approach to Low-Rank Optimal Transport** — [arxiv_lg](https://arxiv.org/abs/2606.12120v1)
- **DAM-VLA: Decoupled Asynchronous Multimodal Vision Language Action model** — [arxiv_lg](https://arxiv.org/abs/2606.12105v1)
- **Efficient Time Series Clustering from Multiscale Reservoir Dynamics with Granular-Ball Anchoring Graph Optimization** — [arxiv_lg](https://arxiv.org/abs/2606.12077v1)
- **YMX899/MemoryCloud** — [github](https://github.com/YMX899/MemoryCloud)
- **Datadog veterans launch AI coding startup Niteshift on a bet against Big AI lock-in** — [techcrunch_ai](https://techcrunch.com/2026/06/10/datadog-veterans-launch-ai-coding-startup-niteshift-on-a-bet-against-big-ai-lock-in/)
- **Jedify raises $24M to help companies arm AI agents with context on their business** — [techcrunch_ai](https://techcrunch.com/2026/06/10/jedify-raises-24m-to-help-companies-arm-ai-agents-with-context-on-their-business/)
- **xAI fired an engineer who raised alarms about Grok safety, new lawsuit claims** — [techcrunch_ai](https://techcrunch.com/2026/06/10/xai-fired-an-engineer-who-raised-alarms-about-grok-safety-new-lawsuit-claims/)
- **CYC2002tommy/Deep-Research-Agent** — [github](https://github.com/CYC2002tommy/Deep-Research-Agent)
- **How memory tools can make AI models worse** — [techcrunch_ai](https://techcrunch.com/2026/06/10/how-memory-tools-can-make-ai-models-worse/)
- **langgenius/mosoo-agent-driver** — [github](https://github.com/langgenius/mosoo-agent-driver)
- **agentic-in/inferoa** — [github](https://github.com/agentic-in/inferoa)
- **Zafer-Liu/Agent_Manager** — [github](https://github.com/Zafer-Liu/Agent_Manager)
- **The future of AI regulation is courting the strangest, most anxious bedfellows** — [theverge_ai](https://www.theverge.com/column/947838/washington-ai-network-honors-2026-midterms)
- **Access OpenAI models and Codex through your Oracle cloud commitment** — [openai](https://openai.com/index/openai-on-oracle-cloud)
- **How an astrophysicist uses Codex to help simulate black holes** — [openai](https://openai.com/index/using-codex-to-simulate-black-holes)
- **Claude Fable won’t answer basic biology questions** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/947973/fable-wont-answer-basic-biology-questions)
- **Microsoft, like, totally gets why students are booing AI-pilled graduation speakers** — [theverge_ai](https://www.theverge.com/news/947831/college-speakers-booed-ai-microsoft)
- **Google won’t just admit it’s feeding YouTube creators to its music AI** — [theverge_ai](https://www.theverge.com/tech/947770/google-lyria-music-ai-lawsuit-youtube)
- **Microsoft restricts Claude Fable for employees over data retention concerns** — [theverge_ai](https://www.theverge.com/report/947575/microsoft-claude-fable-5-restricted-internally)
- **Google will save your Lens photos, Search Live recordings, and Translate audio for AI training** — [theverge_ai](https://www.theverge.com/tech/947836/google-search-privacy-settings-images-audio)
- **Decart’s new world model can simulate hours of photorealistic driving — with some caveats** — [techcrunch_ai](https://techcrunch.com/2026/06/10/decarts-new-world-model-can-simulate-hours-of-photorealistic-driving-with-some-caveats/)
- **PRC-linked influence operations are targeting AI debates in the US** — [openai](https://openai.com/index/prc-linked-influence-operations-ai-debates)
- **The Download: the “steroid olympics” and a safer Mythos** — [mit_tech_review](https://www.technologyreview.com/2026/06/10/1138739/the-download-steroid-olympics-enhanced-games-anthropic-mythos/)
- **The “steroid olympics” were a circus—and a window into our culture** — [mit_tech_review](https://www.technologyreview.com/2026/06/10/1138670/enhanced-games-doping-steroids-hormones-supplements-longevity/)
- **superagents-lab/xcode27-skills** — [github](https://github.com/superagents-lab/xcode27-skills)
- **ferdinandobons/brand-docs** — [github](https://github.com/ferdinandobons/brand-docs)
- **Fresh off bond sale, Amazon borrows $17.5B from banks as AI spending continues** — [techcrunch_ai](https://techcrunch.com/2026/06/10/fresh-off-bond-sale-amazon-borrows-17-5-billion-from-banks-as-ai-spending-continues/)
- **‘AI-pilled’ firms spend $7,500 per employee each month on AI** — [techcrunch_ai](https://techcrunch.com/2026/06/10/ai-pilled-firms-spend-7500-per-employee-each-month-on-ai/)
- **Cybersecurity researchers aren’t happy about the guardrails on Anthropic’s Fable** — [techcrunch_ai](https://techcrunch.com/2026/06/10/cybersecurity-researchers-arent-happy-about-the-guardrails-on-anthropics-fable/)
- **The three hard-tech moonshots fueling SpaceX’s unbelievable IPO** — [techcrunch_ai](https://techcrunch.com/2026/06/10/the-three-hard-tech-moonshots-fueling-spacexs-unbelievable-ipo/)
- **Warner Music acquires AI attribution startup Sureel AI** — [techcrunch_ai](https://techcrunch.com/2026/06/10/warner-music-acquires-ai-attribution-startup-sureel-ai/)
- **Meta signs first AI data center deal in India with Reliance** — [techcrunch_ai](https://techcrunch.com/2026/06/10/meta-signs-first-ai-data-center-deal-in-india-with-reliance/)
- **kanna12580/kk-knowledge-agent** — [github](https://github.com/kanna12580/kk-knowledge-agent)
- **Forsy-AI/forsy-trace-skill** — [github](https://github.com/Forsy-AI/forsy-trace-skill)
- **FerroxLabs/wayland** — [github](https://github.com/FerroxLabs/wayland)
- **RainyMarks/DeepX** — [github](https://github.com/RainyMarks/DeepX)
- **DiffusionGemma: 4x faster text generation** — [deepmind](https://deepmind.google/blog/diffusiongemma-4x-faster-text-generation/)
- **TwoSevenOneT/EDRChoker** — [github](https://github.com/TwoSevenOneT/EDRChoker)
- **pivanov/ctx-wire** — [github](https://github.com/pivanov/ctx-wire)
- **serenakeyitan/awesome-agent-loops** — [github](https://github.com/serenakeyitan/awesome-agent-loops)
- **cobusgreyling/loop-engineering** — [github](https://github.com/cobusgreyling/loop-engineering)
- **Ronvaknins/ableton-extensions-skill** — [github](https://github.com/Ronvaknins/ableton-extensions-skill)
- **phun333/pi-infobar** — [github](https://github.com/phun333/pi-infobar)
- **JimLiu/baoyu-design** — [github](https://github.com/JimLiu/baoyu-design)
- **ikunycj/gpt-team-register** — [github](https://github.com/ikunycj/gpt-team-register)
- **3299129776-a11y/public-skill-finder** — [github](https://github.com/3299129776-a11y/public-skill-finder)
- **Evaluation of Alternative-Based Information Systems for Deliberative Polling using an Agentic Simulator** — [arxiv_cy](https://arxiv.org/abs/2606.11692v1)
- **Should LLM Agents Decide in Social Simulations? Comparing Finite-State and LLM-Based Decision Policies** — [arxiv_cy](https://arxiv.org/abs/2606.12369v1)
- **百度智能云与FluxA达成战略合作，共建 Agent 经济全球支付基础设施** — [qbitai](https://www.qbitai.com/2026/06/433516.html)
- **8点1氪丨世界杯门票遇冷，近18万张门票待转售；台积电释放涨价信号；但斌回应“被段永平拉黑”** — [36kr](https://36kr.com/p/3848000003953926?f=rss)
- **实测小米最快1T大模型：吞吐量每秒1000+ Tokens，Vibe Coding七秒交付** — [qbitai](https://www.qbitai.com/2026/06/434225.html)
- **中国第一、全球第二！HiDream-O1-Image-1.5 登顶文生图榜单，超越谷歌、英伟达** — [qbitai](https://www.qbitai.com/2026/06/434196.html)
- **东风联手九识，商用无人车也有“HI模式”了** — [qbitai](https://www.qbitai.com/2026/06/433956.html)
- **抖音征召天下「AI视频英才」！创作者们，这次是真能吃上AI红利了…** — [qbitai](https://www.qbitai.com/2026/06/433832.html)
- **英特尔锐炫™ Pro B70 GPU亮相MPTS2026，共探大视听时代AI创作新范式** — [qbitai](https://www.qbitai.com/2026/06/433798.html)
- **GPT-5.6首批实测来了！精准狙击Mythos** — [qbitai](https://www.qbitai.com/2026/06/433731.html)
- **Claude Fable 5首日实测，杀疯了…** — [qbitai](https://www.qbitai.com/2026/06/433682.html)
- **氪星晚报｜韩IT巨头Kakao工会史上首次启动局部罢工；三星考虑新建先进芯片封装厂，以满足全球芯片需求；SK海力士最早将于8月在美国上市** — [36kr](https://36kr.com/p/3847079661193733?f=rss)
- **Why AI Slop Matters, but Not Like That** — [arxiv_cy](https://arxiv.org/abs/2606.12285v1)
- **小米推出AI 编程助手MiMo Code** — [36kr](https://36kr.com/newsflashes/3848111404274945?f=rss)
- **Learning by Chatting? Investigating the Impact of Generative AI on Information Seeking and Learning** — [arxiv_cy](https://arxiv.org/abs/2606.11669v1)
- **Are LLMs Bad at Moral Reasoning?** — [arxiv_cy](https://arxiv.org/abs/2606.11635v1)
- **What Uncertainties Do We Need for Dynamical Systems?** — [arxiv_ml](https://arxiv.org/abs/2606.11988v1)
- **Efficient Multinomial Logistic Bandit via Frequent Directions** — [arxiv_ml](https://arxiv.org/abs/2606.11968v1)
- **From Persistence to Survival: Hypothesis Testing, Effect Sizes and Vectorisation for Topological Features** — [arxiv_ml](https://arxiv.org/abs/2606.11911v1)
- **Conformal Bayes under Label Shift: Post-Hoc Calibration vs. In-Training Adaptation** — [arxiv_ml](https://arxiv.org/abs/2606.11865v1)
- **Magnitude-Based Features for Multispecies Spatial Data** — [arxiv_ml](https://arxiv.org/abs/2606.11775v1)
- **Time Series Analysis in Machine Learning** — [arxiv_ml](https://arxiv.org/abs/2606.11746v1)
- **Renewable Lasso without Batch-Number Constraints: A Gradient-Enhanced Approach** — [arxiv_ml](https://arxiv.org/abs/2606.11738v1)
- **Capacity-Constrained Online Convex Optimization with Delayed Feedback** — [arxiv_ml](https://arxiv.org/abs/2606.11711v1)
- **Tree-Structured Orthonormal Decomposition of the Aitchison Simplex** — [arxiv_ml](https://arxiv.org/abs/2606.11646v1)
- **36氪首发 | 创维独家投资数千万，这家企业将碳化硅切割损耗降至40微米内** — [36kr](https://36kr.com/p/3848094835217666?f=rss)
- **甲骨文CFO：公司积压订单达6380亿美元，体现市场对AI基建和云服务的需求旺盛** — [36kr](https://36kr.com/newsflashes/3848088702260225?f=rss)
- **两部门：深入实施“人工智能+三品”专项行动，建设一批行业大模型和高质量数据集** — [36kr](https://36kr.com/newsflashes/3848066038174724?f=rss)
- **中金：维持美联储年内不降息、不加息的基准判断** — [36kr](https://36kr.com/newsflashes/3848022773011715?f=rss)
- **独家｜字节 AI 制药开启拆分融资，AI4S 进入产业化阶段** — [36kr](https://36kr.com/p/3846956646124036?f=rss)
- **最前线｜AI跨境电商工具混战，StoreClaw想用“一个大脑”接管卖家的店** — [36kr](https://36kr.com/p/3846793046133257?f=rss)
- **钉钉换帅，92年技术极客陈宇森接任钉钉CEO** — [36kr](https://36kr.com/newsflashes/3848133613999106?f=rss)
- **智元推出灵犀X2 EDU（人人造）版本，面向科教实训等丰富场景** — [36kr](https://36kr.com/newsflashes/3848126301541636?f=rss)
- **OpenAI考虑大幅降价，以期在与Anthropic的用户争夺战中占据有利地位** — [36kr](https://36kr.com/newsflashes/3848106407040265?f=rss)
- **两市融资余额减少80.91亿元** — [36kr](https://36kr.com/newsflashes/3848058894373888?f=rss)