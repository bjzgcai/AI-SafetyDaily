# AI Daily Digest [AI 安全] - 2026-06-12


# Daily Thematic Digest: AI Safety & Agent Governance
**Date:** 2026-06-12  
**Theme:** Agent Security, Runtime Safety, Alignment, and Evaluation

## Highlights

Three critical developments define the current landscape of agent safety research, shifting focus from static model robustness to dynamic system-level risks. First, **SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems** identifies a previously unaddressed vulnerability where adversaries can inject crafted memories into persistent agent storage, steering future responses without modifying weights or code. This highlights the fragility of retrieval-augmented generation (RAG) agents operating over long-term sessions. Second, **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** proposes a structural overhaul for enterprise security, arguing that traditional perimeter controls are obsolete when agents dissolve data boundaries by executing tool calls and modifying systems of record autonomously. Third, **MAStrike: Shapley-Guided Collusive Red-Teaming on Multi-Agent Systems** exposes how hierarchical multi-agent workflows expand the attack surface through coordinated adversarial behaviors, suggesting that existing red-teaming methods fail to detect privilege escalation across role-specialized agents. Together, these works underscore a transition toward runtime governance, memory integrity, and systemic threat modeling.

## Agent Security & Governance

The prevailing paradigm in agent safety is undergoing a fundamental shift from protecting isolated models to governing distributed, persistent workflows. A central challenge identified across recent literature is the dissolution of traditional data boundaries. In **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents**, the authors argue that enterprise security historically governed crossings of protected surfaces (data at rest/in transit), whereas production agents internalize risk within workflows. They propose a reference architecture that treats policy engines not as external filters but as integral components of the agent’s decision loop, capable of evaluating sequences of individually-permitted actions that may collectively transform business processes without authorization. This architectural critique aligns with findings in **Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval**, which demonstrates that provenance defenses checking the authenticity of retrieved records are blind to structure manipulation; an untrusted principal can alter the graph topology to change which authenticated facts are selected, bypassing standard information-flow control.

Persistent memory introduces unique attack vectors that static defenses cannot mitigate. **SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems** formalizes Multi-Session Memory Poisoning (MSMP), showing that heuristic filters and static-corpus defenses like RobustRAG are bypassed by fluent enterprise-style injections. The authors report that no existing defence currently certifies against MSMP, necessitating new runtime mechanisms. Complementing this, **OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents** frames privacy not as a property of single outputs but of entire trajectories, noting that leakage is cumulative and bidirectional. While distinct from pure privacy protection, OCELOT’s approach to bounding inference leakage is directly relevant to agent runtime safety, as malicious observations can inject instructions that turn honest-but-curious sinks into vectors for secret extraction.

The scalability of security measures remains a contentious point. **Smarter Saboteurs, Better Fixers: Scaling & Security in Linear Multi-Agent Workflows** investigates the relationship between model scale and system-level resilience. Contrary to assumptions that larger models inherently improve safety compliance, the authors find that while scaling improves individual agent capability, it does not linearly correlate with workflow resilience against sabotage. This suggests that security must be engineered into the interaction topology rather than relying solely on model intelligence. Furthermore, **MAStrike: Shapely-Guided Collusive Red-Teaming on Multi-Agent Systems** expands the threat model beyond single-agent failures to coordinated collusion. By using Shapley values to identify critical agents in hierarchical systems, the framework reveals that heuristic selection of target agents leaves critical questions unanswered regarding cross-agent privilege escalation. This contrasts with earlier approaches that treated message streams in isolation, highlighting the need for holistic multi-agent auditing.

Governance also extends to the lifecycle of agent skills and corrections. **Getting Better at Working With You: Compiling User Corrections into Runtime Enforcement for Coding Agents** introduces Test-time Rule Acquisition and Compiled Enforcement (TRACE), a pipeline that mines user corrections and compiles them into atomic rules. The authors report that existing memory systems like Mem0 leave 57.5% of applicable preference checks violated, indicating a gap between preference access and compliance. TRACE aims to close this by enforcing rules at runtime, effectively treating user feedback as executable constraints rather than transient context. Similarly, **SkillCAT: Contrastive Assessment and Topology-Aware Skill Self-Evolution for LLM Agents** proposes separating skill evolution into contrastive causal extraction and assessment-augmented evolution stages, aiming to prevent the degradation of reusable skills over time. These efforts collectively suggest a move toward "compliance-by-construction," where safety properties are embedded in the agent's operational logic rather than monitored post-hoc.

## Tool/Prompt Injection & Runtime Defenses

As agents increasingly interact with external environments, the attack surface expands to include indirect prompt injection and tool misuse. **PI-Hunter: Automated Red-Teaming for Exposing and Localizing Prompt Injections** addresses the opacity of latent prompt injections in agentic systems. Unlike existing defenses that block content at inference time, PI-Hunter provides visibility into how injections propagate through agents, enabling proactive vulnerability exposure. This complements **Who Pays the Price? Stakeholder-Centric Prompt Injection Benchmarking for Real-world Web Agents**, which argues that existing benchmarks focus on technical feasibility while overlooking the distribution of resulting harms. The authors emphasize that prompt-injection risk is victim-dependent, requiring benchmarks that account for nuanced harm distributions rather than binary success rates.

Visual-language-action (VLA) systems introduce novel failure modes where visual backdoors can propagate through decision pipelines. **Beyond Attack Success Rate: Examining Trigger Leakage in Vision-Language Agentic Systems** formalizes trigger precision as a metric, noting that current evaluations capture whether a trigger works but not whether it triggers hidden behaviors only when intended. This finding contradicts the assumption that high attack success rate (ASR) equates to effective system compromise; precise triggers may remain dormant until specific conditions are met. Reinforcement learning (RL) agents face similar challenges, as detailed in **PolicyGuard: Towards Test-time and Step-level Adversary Defense for Reinforcement Learning Agent**. Existing backdoor defenses often require access to internal parameters or operate only at the trajectory level. PolicyGuard proposes step-level defenses that do not rely on parameter access, addressing the limitation of current methods in securing deployed RL agents.

Runtime monitoring and debugging infrastructure are emerging as critical components of defense. **ContextScope: A local-first macOS debugger for LLM context windows, token usage, tool calls, and agent execution** offers practical tooling for inspecting agent behavior locally, allowing developers to trace execution paths and token consumption in real-time. This supports the broader goal of observability highlighted in **OpenLoop: Universal Loop Engineering Framework for AI Agents**, which enables play-test-fix-verify-improve cycles with auditable stop conditions. Without such visibility, detecting subtle manipulations becomes impossible. Additionally, **WarpGuard: Protected-Site Control-Flow Integrity for CUDA SASS Binaries** addresses low-level exploitation risks in GPU kernels, noting that source- or PTX-level policies do not capture the boundary executed NVIDIA SASS. This underscores that agent security must extend down to the hardware execution layer, particularly for compute-intensive tasks like molecular dynamics or video generation.

## Alignment, Interpretability & Robustness

Ensuring agents act in accordance with human intent requires more than alignment tuning; it demands robust reasoning and interpretability. **LLM-as-an-Investigator: Evidence-First Reasoning for Robust Interactive Problem Diagnosis** introduces a methodology where agents prioritize evidence collection over hypothesis alignment, countering "user-driven sycophancy." The authors find that LLMs tend to reinforce user-provided hypotheses prematurely, proposing an evidence-first approach to mitigate this bias. This aligns with **Zero-source LLM Hallucination Detection with Human-like Criteria Probing**, which emulates human evaluators to detect hallucinations without external references. Both works suggest that robustness depends on the agent's ability to verify its own outputs against independent criteria rather than relying on parametric knowledge alone.

Multi-agent debate frameworks offer another avenue for improving reasoning reliability. **ARMOR-MAD: Adaptive Routing for Heterogeneous Multi-Agent Debate in Large Language Model Reasoning** treats debate as conditional computation, using pre-debate agreement routing and early stopping to reduce wasted computation. This contrasts with fixed debate pipelines that may amplify correlated errors among similar agents. The authors report that their training-free framework improves efficiency without sacrificing accuracy. However, the philosophical underpinnings of agency remain contested. **Why Sampling Is Not Choosing: Intentionality, Agency, and Moral Responsibility in Large Language Models** argues that attributing moral responsibility to LLMs is misguided because their operation is characterized by probabilistic input-output mappings lacking intrinsic intentionality. This theoretical stance informs safety discussions, suggesting that accountability lies with the deployment context rather than the model itself.

Interpretability research continues to probe the internal mechanisms of routing and representation. **ICA Lens: Interpreting Language Models Without Training Another Dictionary** explores whether interpretable directions are visible from activation geometry before training sparse autoencoders, challenging the necessity of large dictionaries for rapid exploration. Meanwhile, **When Does Routing Become Interpretable? Causal Probes on Block Attention Residuals** investigates whether exposing cross-layer routing tensors suffices for mechanistic interpretation. The authors probe checkpoints under identical routing-ablation interventions, finding that direct observation of information flow does not automatically guarantee interpretability. These findings highlight the complexity of mapping internal states to external behaviors, a prerequisite for reliable safety interventions.

## Safety Benchmarks & Evaluation

Evaluation methodologies are evolving to match the complexity of agentic systems. **Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks** introduces a protocol making heterogeneous agent harnesses comparable under fair settings, including fixed prompts and workspace contracts. This addresses the difficulty of measuring coding ability under SWE-bench where generic agents do not satisfy clean Docker workspace requirements. Similarly, **EvoBrowseComp: Benchmarking Search Agents on Evolving Knowledge** replaces static knowledge benchmarks with evolving ones synthesized via live-web traversal, preventing test-set contamination and parametric memorization. The authors note that existing benchmarks obscure true browsing competence via reasoning shortcuts, necessitating future-proof evaluation standards.

Ethical robustness is gaining traction as a distinct evaluation category. **ERTS: Adversarial Robustness Testing of Ethical AI via Semantic Perturbation in a Bounded Consequence Space** encodes ethical dilemmas into a 22-dimensional Ethical Consequence Space, applying semantic perturbations subject to validity constraints. This moves beyond binary safety classifications to measure robustness across nuanced ethical dimensions. **From Verdict to Process: Agentic Reinforcement Learning for Multi-Stage Fact Verification** proposes optimizing multi-stage workflows adaptively rather than isolating stages, improving coordination among claim decomposition and evidence gathering modules. Finally, **Conformal Elo Estimation for LLM Evaluation** quantifies judge-human disagreement at local and global levels, propagating calibrated win probabilities to miscalibrate rankings caused by position bias or self-preference. These benchmarks collectively signal a maturation of evaluation practices toward contamination resistance, ethical granularity, and statistical rigor.

## Looking Forward

Several unresolved theoretical questions await validation as agent systems scale. First, the relationship between model scaling and security resilience requires further empirical study; initial findings in **Smarter Saboteurs, Better Fixers** suggest diminishing returns on security gains from model size alone, implying that architectural hardening must precede scaling. Second, the formal verification of agent loops remains nascent; while frameworks like **OpenLoop** provide engineering patterns, rigorous mathematical guarantees for infinite-horizon agent interactions are lacking. Third, the definition of agency and accountability needs refinement; as noted in **Why Sampling Is Not Choosing**, current attribution of moral responsibility to models may obscure the sociotechnical control problems inherent in deployment. Future research should prioritize certified runtime defenses for persistent memory, standardized protocols for multi-agent collusion detection, and regulatory frameworks that address the "Internet of Agentic AI" as a systemic risk vector rather than a collection of isolated tools.

---


## References

- **SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12703v1)
- **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12320v1)
- **PI-Hunter: Automated Red-Teaming for Exposing and Localizing Prompt Injections** — [arxiv_cr](https://arxiv.org/abs/2606.12737v1)
- **InternVideo3: Agentify Foundation Models with Multimodal Contextual Reasoning** — [huggingface_papers](https://arxiv.org/abs/2606.12195)
- **Agentic Environment Engineering for Large Language Models: A Survey of Environment Modeling, Synthesis, Evaluation, and Application** — [huggingface_papers](https://arxiv.org/abs/2606.12191)
- **MDForge: Agentic Molecular Dynamics Pipeline Design under Sparse Simulator Feedback** — [arxiv_cl](https://arxiv.org/abs/2606.12916v1)
- **MemRefine: LLM-Guided Compression for Long-Term Agent Memory** — [arxiv_cl](https://arxiv.org/abs/2606.13177v1)
- **Getting Better at Working With You: Compiling User Corrections into Runtime Enforcement for Coding Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13174v1)
- **Claw-SWE-Bench: A Benchmark for Evaluating OpenClaw-style Agent Harnesses on Coding Tasks** — [huggingface_papers](https://arxiv.org/abs/2606.12344)
- **Who Pays the Price? Stakeholder-Centric Prompt Injection Benchmarking for Real-world Web Agents** — [arxiv_ai](https://arxiv.org/abs/2606.13385v1)
- **LLM-as-an-Investigator: Evidence-First Reasoning for Robust Interactive Problem Diagnosis** — [arxiv_ai](https://arxiv.org/abs/2606.13220v1)
- **Beyond Attack Success Rate: Examining Trigger Leakage in Vision-Language Agentic Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12586v1)
- **OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12341v1)
- **Understanding the Rejection of Fixes Generated by Agentic Pull Requests -- Insights from the AIDev Dataset** — [arxiv_ai](https://arxiv.org/abs/2606.13468v1)
- **Toward Instructions-as-Code: Understanding the Impact of Instruction Files on Agentic Pull Requests** — [arxiv_ai](https://arxiv.org/abs/2606.13449v1)
- **MiniMax Sparse Attention** — [arxiv_ai](https://arxiv.org/abs/2606.13392v1)
- **DIG: Oracle-Guided Directed Input Generation for One-Day Vulnerabilities** — [arxiv_cr](https://arxiv.org/abs/2606.13037v1)
- **EvoBrowseComp: Benchmarking Search Agents on Evolving Knowledge** — [arxiv_cl](https://arxiv.org/abs/2606.13120v1)
- **G-Long: Graph-Enhanced Memory Management for Efficient Long-Term Dialogue Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13115v1)
- **Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval** — [arxiv_cr](https://arxiv.org/abs/2606.12290v1)
- **MAStrike: Shapley-Guided Collusive Red-Teaming on Multi-Agent Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12918v1)
- **Zero-source LLM Hallucination Detection with Human-like Criteria Probing** — [arxiv_cl](https://arxiv.org/abs/2606.12900v1)
- **No Hidden Prompts Needed! You Can Game AI Peer Review with Presentation-Only Revisions** — [arxiv_cl](https://arxiv.org/abs/2606.13044v1)
- **IterCAD: An Iterative Multimodal Agent for Visually-Grounded CAD Generation and Editing** — [arxiv_ai](https://arxiv.org/abs/2606.13368v1)
- **NavWAM: A Navigation World Action Model for Goal-Conditioned Visual Navigation** — [arxiv_cv](https://arxiv.org/abs/2606.13494v1)
- **PolicyGuard: Towards Test-time and Step-level Adversary Defense for Reinforcement Learning Agent** — [arxiv_cr](https://arxiv.org/abs/2606.12896v1)
- **RogueAI: A Reverse Turing Test for Detecting Licensed AI Deception in Dialogue** — [arxiv_cl](https://arxiv.org/abs/2606.13310v1)
- **SENTINEL: Failure-Driven Reinforcement Learning for Training Tool-Using Language Model Agents** — [arxiv_cl](https://arxiv.org/abs/2606.12908v1)
- **X-MADAM-RAG: Diagnosing and Handling Chinese-English Evidence Conflict in Retrieval-Augmented Generation** — [arxiv_cl](https://arxiv.org/abs/2606.12903v1)
- **SafeLLM: Extraction as a Hallucination-Resistant Alternative to Rewriting in Safety-Critical Settings** — [arxiv_cl](https://arxiv.org/abs/2606.12897v1)
- **From Verdict to Process: Agentic Reinforcement Learning for Multi-Stage Fact Verification** — [arxiv_ai](https://arxiv.org/abs/2606.13262v1)
- **ARMOR-MAD: Adaptive Routing for Heterogeneous Multi-Agent Debate in Large Language Model Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.13197v1)
- **Smarter Saboteurs, Better Fixers: Scaling & Security in Linear Multi-Agent Workflows** — [arxiv_cr](https://arxiv.org/abs/2606.12709v1)
- **WarpGuard: Protected-Site Control-Flow Integrity for CUDA SASS Binaries** — [arxiv_cr](https://arxiv.org/abs/2606.11871v1)
- **SkillCAT: Contrastive Assessment and Topology-Aware Skill Self-Evolution for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13317v1)
- **Neuro-Symbolic Agents for Regulated Process Automation: Challenges and Research Agenda** — [arxiv_ai](https://arxiv.org/abs/2606.13405v1)
- **Mod-Guide: An LLM-based Content Moderation Feedback System to Address Insensitive Speech toward Indigenous Ethnic and Religious Minority Communities** — [arxiv_ai](https://arxiv.org/abs/2606.13397v1)
- **An LLM System for Autonomous Variational Quantum Circuit Design** — [arxiv_ai](https://arxiv.org/abs/2606.13380v1)
- **Can I Buy Your KV Cache?** — [arxiv_ai](https://arxiv.org/abs/2606.13361v1)
- **TimeLens: On-Device Artifact Recognition with Retrieval-Augmented Question Answering for the Grand Egyptian Museum** — [arxiv_cl](https://arxiv.org/abs/2606.13267v1)
- **MiniPIC: Flexible Position-Independent Caching in <100LOC** — [arxiv_cl](https://arxiv.org/abs/2606.13126v1)
- **Multi-Field Hybrid Retrieval-Augmented Generation for Maritime Accident Root Cause Analysis** — [arxiv_ai](https://arxiv.org/abs/2606.13249v1)
- **ComAct: Reframing Professional Software Manipulation via COM-as-Action Paradigm** — [arxiv_ai](https://arxiv.org/abs/2606.13239v1)
- **Proprioceptive-visual correspondence enables self-other distinction in humanoid robots** — [arxiv_ai](https://arxiv.org/abs/2606.13222v1)
- **Under What Conditions Can a Machine Become Genuinely Creative?** — [arxiv_ai](https://arxiv.org/abs/2606.13196v1)
- **CAPED: Context-Aware Privacy Exposure Defense for Mobile GUI Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12666v1)
- **Toward Generalist Autonomous Research via Hypothesis-Tree Refinement** — [huggingface_papers](https://arxiv.org/abs/2606.11926)
- **Budget-Constrained Step-Level Diffusion Caching** — [arxiv_cv](https://arxiv.org/abs/2606.13496v1)
- **Categorical Robustness Assessment for Machine Learning based Network Intrusion Detection Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12075v1)
- **S-GBT: Smooth Growth Bound Tensor for Certified Robustness Against Word Substitution Attacks in NLP** — [arxiv_cl](https://arxiv.org/abs/2606.13439v1)
- **OR-Action: Multi-Role Video Understanding with Fine-Grained Actions** — [arxiv_cv](https://arxiv.org/abs/2606.13332v1)
- **Reinforcement Learning for Neural Model Editing** — [arxiv_lg](https://arxiv.org/abs/2606.13461v1)
- **The Emergence of Autonomous Penetration Capabilities in Large Language Model-Powered AI Systems** — [arxiv_cr](https://arxiv.org/abs/2606.13079v1)
- **Semantic Identification of IoT Devices from Behavioral Primitives** — [arxiv_cr](https://arxiv.org/abs/2606.12793v1)
- **SICI: A Semantic-Pragmatic Complexity Index Reveals Regime Shifts in LLM Stance Detection** — [arxiv_cl](https://arxiv.org/abs/2606.13189v1)
- **Multi-Turn Reasoning When Context Arrives in Pieces: Scalable Sharding and Memory-Augmented RL** — [arxiv_cl](https://arxiv.org/abs/2606.12941v1)
- **Mining Architectural Quality Under Agentic AI Adoption: A Causal Study of Java Repositories** — [arxiv_ai](https://arxiv.org/abs/2606.13298v1)
- **Unified MRI Brain Image Translation via Hierarchical Tumor Structure Comparison** — [arxiv_cv](https://arxiv.org/abs/2606.13096v1)
- **TetherCache: Stabilizing Autoregressive Long-Form Video Generation with Gated Recall and Trusted Alignment** — [arxiv_cv](https://arxiv.org/abs/2606.13035v1)
- **SwarmSense-DNN: A Trustworthy and Decentralized Neural Framework for Proactive Anomaly Defense in Consumer IoT** — [arxiv_cr](https://arxiv.org/abs/2606.11803v1)
- **ICA Lens: Interpreting Language Models Without Training Another Dictionary** — [huggingface_papers](https://arxiv.org/abs/2606.11722)
- **TRACE: A Unified Rollout Budget Allocation Framework for Efficient Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2606.11119)
- **ERTS: Adversarial Robustness Testing of Ethical AI via Semantic Perturbation in a Bounded Consequence Space** — [arxiv_ai](https://arxiv.org/abs/2606.13282v1)
- **Reinforcement Learning Disrupts Gradient-Based Adversarial Optimization** — [arxiv_cr](https://arxiv.org/abs/2606.12251v1)
- **Toward Trustworthy AI: Multi-Target Adversarial Attacks and Robust Defenses for Continuous Data Summarization** — [arxiv_cr](https://arxiv.org/abs/2606.11804v1)
- **From Passive Generation to Investigation: A Proactive Scientific Peer Review Agent** — [arxiv_cl](https://arxiv.org/abs/2606.13349v1)
- **Ontology Memory-Augmented ASR Correction for Long Text-Speech Interleaved Conversations** — [arxiv_ai](https://arxiv.org/abs/2606.13464v1)
- **Why Sampling Is Not Choosing: Intentionality, Agency, and Moral Responsibility in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2606.13441v1)
- **VietFashion: Benchmarking Sketch-Text Composed Image Retrieval for Cultural Outfits** — [arxiv_cv](https://arxiv.org/abs/2606.13427v1)
- **MoVerse: Real-Time Video World Modeling with Panoramic Gaussian Scaffold** — [arxiv_cv](https://arxiv.org/abs/2606.13376v1)
- **How Much Memory Do We Need? Adaptive Memory Gate for Neural Operators** — [arxiv_lg](https://arxiv.org/abs/2606.13443v1)
- **Foundations of Practical Quantum Advantage in Quantum-Informed Machine Learning for Predicting Chaos** — [arxiv_lg](https://arxiv.org/abs/2606.13422v1)
- **Split Tallies: A Discrete Certificate Calculus for Auditing Dynamic Ordered Sets in Constant Memory** — [arxiv_cr](https://arxiv.org/abs/2606.13272v1)
- **LAUKIN: A Multi-jurisdictional Common Law Contract Dataset** — [arxiv_cl](https://arxiv.org/abs/2606.13184v1)
- **HyPE: Category-Aware Hypergraph Encoding with Persistent Edge Embeddings for Persona-Grounded Dialogue** — [arxiv_cl](https://arxiv.org/abs/2606.13142v1)
- **Zero-Shot Captioning for Cultural Heritage: Automated Image Analysis of Traditional Indonesian Clothing** — [arxiv_cv](https://arxiv.org/abs/2606.13275v1)
- **Transformer-Guided Graph Attention for Direct Cardiac Mesh Reconstruction: A Structural Digital Twin Framework** — [arxiv_cv](https://arxiv.org/abs/2606.13188v1)
- **LaME: Learning to Think in Latent Space for Multimodal Embedding via Information Bottleneck** — [arxiv_cv](https://arxiv.org/abs/2606.13061v1)
- **SAM-Deep-EIoU: Selective Mask Propagation for Multi-Object Tracking** — [arxiv_cv](https://arxiv.org/abs/2606.13033v1)
- **Diffusion Transformer World-Action Model for AV Scene Prediction** — [arxiv_cv](https://arxiv.org/abs/2606.12987v1)
- **Quantizing Time-Series Models As Dynamical Systems: Trajectory-Based Quantization Sensitivity Score** — [arxiv_lg](https://arxiv.org/abs/2606.13300v1)
- **WHAR Arena: Benchmarking the State of the Art in Efficient Wearable Human Activity Recognition** — [arxiv_lg](https://arxiv.org/abs/2606.13194v1)
- **MP3: Multi-Period Pattern Pre-training forSpatio-Temporal Forecasting** — [arxiv_lg](https://arxiv.org/abs/2606.13119v1)
- **ECYSAP EYE: From Cyber Situational Awareness to Mission-Centric Decision Support for Enhanced Cyberspace Operations** — [arxiv_cr](https://arxiv.org/abs/2606.12354v1)
- **On Subquadratic Architectures: From Applications to Principles** — [huggingface_papers](https://arxiv.org/abs/2606.12364)
- **Fine-tuning Multi-modal LLMs with ART: Art-based Reinforcement Training** — [huggingface_papers](https://arxiv.org/abs/2606.11854)
- **Which Models Are Our Models Built On? Auditing Invisible Dependencies in Modern LLMs** — [huggingface_papers](https://arxiv.org/abs/2606.12385)
- **Reroute, Don't Remove: Recoverable Visual Token Routing for Vision-Language Models** — [huggingface_papers](https://arxiv.org/abs/2606.12412)
- **World Model Self-Distillation: Training World Models to Solve General Tasks** — [huggingface_papers](https://arxiv.org/abs/2606.12072)
- **Breaking Entropy Bounds: Accelerating RL Training via MTP with Rejection Sampling** — [huggingface_papers](https://arxiv.org/abs/2606.12370)
- **A Multi-Modal Framework with Cross-Subject Pseudo-Labeling and Semantic Alignment for Micro-Gesture Recognition** — [arxiv_cv](https://arxiv.org/abs/2606.13030v1)
- **Quality-Preserving Imperceptible Adversarial Attack on Skeleton-based Human Action Recognition** — [arxiv_cv](https://arxiv.org/abs/2606.13022v1)
- **Trajectory-Level Redirection Attacks on Vision-Language-Action Models** — [arxiv_cv](https://arxiv.org/abs/2606.12978v1)
- **When Does Routing Become Interpretable? Causal Probes on Block Attention Residuals** — [arxiv_lg](https://arxiv.org/abs/2606.13168v1)
- **VideoMDM: Towards 3D Human Motion Generation From 2D Supervision** — [arxiv_lg](https://arxiv.org/abs/2606.13364v1)
- **MagPlus: Bridging Micro-to-Regular Facial Expressions through Learnable Magnification** — [arxiv_cv](https://arxiv.org/abs/2606.13312v1)
- **Visual Place Recognition in Forests with Depth-Aware Distillation** — [arxiv_cv](https://arxiv.org/abs/2606.13206v1)
- **Iterative Visual Thinking: Teaching Vision-Language Models Spatial Self-Correction through Visual Feedback** — [arxiv_cv](https://arxiv.org/abs/2606.13156v1)
- **Augmentation techniques for video surveillance in the visible and thermal spectral range** — [arxiv_cv](https://arxiv.org/abs/2606.13042v1)
- **SeamEdit: A Black-Box VLM-Agnostic Pipeline for Large-Image Semantic Editing** — [arxiv_cv](https://arxiv.org/abs/2606.13041v1)
- **ProtoX-AD: Self-Explainable Time Series Anomaly Detection and Characterization** — [arxiv_lg](https://arxiv.org/abs/2606.13277v1)
- **To GAN or Not To GAN: Segmentation Analysis on Mars DEM** — [arxiv_lg](https://arxiv.org/abs/2606.13252v1)
- **Distributional Loss for Robust Classification** — [arxiv_lg](https://arxiv.org/abs/2606.13223v1)
- **From Uncertain Judgments to Calibrated Rankings: Conformal Elo Estimation for LLM Evaluation** — [arxiv_lg](https://arxiv.org/abs/2606.13221v1)
- **Detecting Explanatory Insufficiency in Learned Representations: A Framework for Representational Vigilance** — [arxiv_lg](https://arxiv.org/abs/2606.13172v1)
- **Robust State-Conditional Feature-Weighted Jump Models for Temporal Clustering** — [arxiv_lg](https://arxiv.org/abs/2606.13146v1)
- **Redesign Mixture-of-Experts Routers with Manifold Power Iteration** — [huggingface_papers](https://arxiv.org/abs/2606.12397)
- **World Pilot: Steering Vision-Language-Action Models with World-Action Priors** — [huggingface_papers](https://arxiv.org/abs/2606.12403)
- **Building Social World Models with Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2606.11482)
- **Optical Implementation of Equilibrium Propagation Using Spatial Photonic Ising Machines** — [arxiv_lg](https://arxiv.org/abs/2606.13454v1)
- **Uncertainty Estimation for Molecular Diffusion Models** — [arxiv_lg](https://arxiv.org/abs/2606.13451v1)
- **Clustering Node Attributed Networks with Graph Neural Networks and Self Learning** — [arxiv_lg](https://arxiv.org/abs/2606.13444v1)
- **Accelerating Speculative Diffusions via Block Verification** — [arxiv_lg](https://arxiv.org/abs/2606.13426v1)
- **Hölder++: Improving the Quality-Coherence Trade-off in Multimodal VAEs** — [arxiv_lg](https://arxiv.org/abs/2606.13381v1)
- **Positional Encoding in the Context of Memristor-Based Analog Computation for Automatic Speech Recognition** — [arxiv_lg](https://arxiv.org/abs/2606.13379v1)
- **Adaptive Multi-Resolution Procedural Knowledge Compression for Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2606.12203)
- **Time-Series Foundation Model Embeddings for Remaining Useful Life Estimation** — [huggingface_papers](https://arxiv.org/abs/2606.11990)
- **Reason, Then Re-reason: Cross-view Revisiting Improves Spatial Reasoning** — [huggingface_papers](https://arxiv.org/abs/2606.11683)
- **Verifiable Environments Are LEGO Bricks: Recursive Composition for Reasoning Generalization** — [huggingface_papers](https://arxiv.org/abs/2606.12373)
- **Lius: Translation Model Based Instructional Lingustic Using Continual Instruction Tuning In Kupang Malay** — [huggingface_papers](https://arxiv.org/abs/2606.11786)
- **YMX899/MemoryCloud** — [github](https://github.com/YMX899/MemoryCloud)
- **Google DeepMind is worried about what happens when millions of agents start to interact** — [mit_tech_review](https://www.technologyreview.com/2026/06/11/1138794/google-deepmind-is-worried-about-what-happens-when-millions-of-agents-start-to-interact/)
- **CYC2002tommy/Deep-Research-Agent** — [github](https://github.com/CYC2002tommy/Deep-Research-Agent)
- **keyuchen21/agentic-engineering-handbook** — [github](https://github.com/keyuchen21/agentic-engineering-handbook)
- **agentic-in/inferoa** — [github](https://github.com/agentic-in/inferoa)
- **The Internet of Agentic AI: Communication, Coordination, and Collective Intelligence at Scale** — [arxiv_cy](https://arxiv.org/abs/2606.12835v1)
- **Our new community investments in Virginia support local jobs and expand energy affordability.** — [google_ai](https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/virginia-community-investments/)
- **Amazon&#8217;s data centers used 2.5 billion gallons of water last year** — [theverge_ai](https://www.theverge.com/tech/948534/amazon-data-centers-water-use)
- **Pool’s new app turns your screenshots into something useful** — [techcrunch_ai](https://techcrunch.com/2026/06/11/pools-new-app-turns-your-screenshots-into-a-searchable-memory-bank/)
- **DoorDash’s new AI chatbot lets you order with prompts and photos** — [techcrunch_ai](https://techcrunch.com/2026/06/11/doordashs-new-ai-chatbot-lets-you-order-with-prompts-and-photos/)
- **The Download: soccer’s data renaissance and China’s big nuclear plans** — [mit_tech_review](https://www.technologyreview.com/2026/06/11/1138809/the-download-soccer-football-data-analytics-china-nuclear-power/)
- **Anthropic apologizes for invisible Claude Fable guardrails** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/948280/anthropic-claude-fable-invisible-distillation-guardrail)
- **Job titles of the future: Nature’s drug designer** — [mit_tech_review](https://www.technologyreview.com/2026/06/11/1138502/job-titles-natures-drug-designer-tim-cernak/)
- **Inside soccer’s data renaissance** — [mit_tech_review](https://www.technologyreview.com/2026/06/11/1138506/inside-soccer-data-renaissance-jesse-davis/)
- **Why China is betting on big nuclear reactors** — [mit_tech_review](https://www.technologyreview.com/2026/06/11/1138789/china-big-nuclear-reactors/)
- **Deezer launches an AI music detector for other streaming services** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/948153/deezer-ai-music-detector-spotify-apple)
- **Anthropic’s Dario Amodei has just one direct report** — [techcrunch_ai](https://techcrunch.com/2026/06/10/anthropics-dario-amodei-has-just-one-direct-report/)
- **RightNow-AI/AutoMegaKernel** — [github](https://github.com/RightNow-AI/AutoMegaKernel)
- **yzfly/TokenCode** — [github](https://github.com/yzfly/TokenCode)
- **superagents-lab/xcode27-skills** — [github](https://github.com/superagents-lab/xcode27-skills)
- **Jeff Bezos’s Prometheus raises $12B to build an ‘artificial general engineer’ for the physical world** — [techcrunch_ai](https://techcrunch.com/2026/06/11/jeff-bezoss-prometheus-raises-12b-to-build-an-artificial-general-engineer-for-the-physical-world/)
- **SpaceX officially prices shares at $135 in the largest IPO ever** — [techcrunch_ai](https://techcrunch.com/2026/06/11/spacex-officially-prices-shares-at-135-in-the-largest-ipo-ever/)
- **SpaceX SPV investors won’t know their true holdings until post-IPO lock-ups lift** — [techcrunch_ai](https://techcrunch.com/2026/06/11/spacex-spv-investors-wont-know-their-true-holdings-until-post-ipo-lock-ups-lift/)
- **Deezer’s new tool can identify AI music from Spotify, Apple Music, and others** — [techcrunch_ai](https://techcrunch.com/2026/06/11/deezers-new-tool-can-identify-ai-music-from-spotify-apple-music-and-others/)
- **Opendoor’s India exit is fueling a bigger conversation about AI and outsourcing** — [techcrunch_ai](https://techcrunch.com/2026/06/10/opendoors-india-exit-is-fueling-a-bigger-conversation-about-ai-and-outsourcing/)
- **sure-scale/doc-haus** — [github](https://github.com/sure-scale/doc-haus)
- **yazmorukyaz/storeops-mcp** — [github](https://github.com/yazmorukyaz/storeops-mcp)
- **kanna12580/kk-knowledge-agent** — [github](https://github.com/kanna12580/kk-knowledge-agent)
- **taisly/agent** — [github](https://github.com/taisly/agent)
- **RainyMarks/DeepX** — [github](https://github.com/RainyMarks/DeepX)
- **3D创作迎来ChatGPT时刻：Meshy发布全球首个3D AI Agent** — [qbitai](https://www.qbitai.com/2026/06/434317.html)
- **TwoSevenOneT/EDRChoker** — [github](https://github.com/TwoSevenOneT/EDRChoker)
- **thu-nmrc/openloop** — [github](https://github.com/thu-nmrc/openloop)
- **serenakeyitan/awesome-agent-loops** — [github](https://github.com/serenakeyitan/awesome-agent-loops)
- **cobusgreyling/loop-engineering** — [github](https://github.com/cobusgreyling/loop-engineering)
- **orange2ai/orange-line-illustration** — [github](https://github.com/orange2ai/orange-line-illustration)
- **JimLiu/baoyu-design** — [github](https://github.com/JimLiu/baoyu-design)
- **ashutosh160798/context-scope** — [github](https://github.com/ashutosh160798/context-scope)
- **kornpng/web-mvp-blueprint-kit** — [github](https://github.com/kornpng/web-mvp-blueprint-kit)
- **Exploring Systems-Thinking Approaches to Loss of Control Risk** — [arxiv_cy](https://arxiv.org/abs/2606.13474v1)
- **1290万高考生看过来！阿里出了个志愿填报Agent，免费的** — [qbitai](https://www.qbitai.com/2026/06/434558.html)
- **8点1氪丨SpaceX上市在即，马斯克或成全球首位万亿富翁；92年技术极客陈宇森接任钉钉CEO；比尔·盖茨就爱泼斯坦案出席国会听证** — [36kr](https://36kr.com/p/3849431503869187?f=rss)
- **Structuring Transparency: Developing Domain-Specific Generative AI Declaration Frameworks in Higher Education** — [arxiv_cy](https://arxiv.org/abs/2606.13389v1)
- **Claude Fable 5省钱秘诀来了：调成Low档比Opus更便宜** — [qbitai](https://www.qbitai.com/2026/06/434571.html)
- **To Share or Not to Share: Orchestrating Trustworthy Data in Global Value Chains** — [arxiv_cy](https://arxiv.org/abs/2606.12788v1)
- **Mythos阴影里谷歌悄悄发模型，速度暴涨4倍** — [qbitai](https://www.qbitai.com/2026/06/434316.html)
- **Fable 5自带反蒸馏机制！检测到就降智，误触率高到离谱** — [qbitai](https://www.qbitai.com/2026/06/434326.html)
- **AI短剧工具赛道，年度最大单笔融资来了** — [qbitai](https://www.qbitai.com/2026/06/434298.html)
- **谷歌I/O最出圈的一幕，发生在抖音？？？** — [qbitai](https://www.qbitai.com/2026/06/434267.html)
- **行业首创AI志愿填报+真人专家验真，百度全新升级高考服务** — [qbitai](https://www.qbitai.com/2026/06/434268.html)
- **实测小米最快1T大模型：吞吐量每秒1000+ Tokens，Vibe Coding七秒交付** — [qbitai](https://www.qbitai.com/2026/06/434225.html)
- **AI重塑底层逻辑，数据库重新站上风口** — [36kr](https://36kr.com/newsflashes/3849438848390144?f=rss)
- **"Is This Not Enough?": Asymmetries in Institutional Accountability and Collective Sensemaking in the Case of Canada's Algorithmic Visa Triage System** — [arxiv_cy](https://arxiv.org/abs/2606.13071v1)
- **A Quadratic Order Reduction -- Gaussian Process Ordinary Differential Equation framework for the inference of Large Continuous Dynamical Systems** — [arxiv_ml](https://arxiv.org/abs/2606.13063v1)
- **Diffusion-Network Alignment: An Efficient Algorithm and Explicit Probability Bounds** — [arxiv_ml](https://arxiv.org/abs/2606.12879v1)
- **Digital Twin-Based Simulation for Predictive Decision-Making in Waterway Logistics** — [arxiv_cy](https://arxiv.org/abs/2606.13492v1)
- **Rapid mixing for Gibbs measures in Riemannian manifolds** — [arxiv_ml](https://arxiv.org/abs/2606.13453v1)
- **Data Aphasia: An Institutional Counterfactual Study of the Stability of Academic Cognition Under Letter-Grade Evaluation Systems** — [arxiv_cy](https://arxiv.org/abs/2606.12946v1)
- **Vocal Identity Under Siege by AI Voice Cloning Technologies** — [arxiv_cy](https://arxiv.org/abs/2606.12812v1)
- **AiAWE: An Open-Source LLM Automated Writing Evaluation System Using LoRA-Adapted Instruction-Tuned Models** — [arxiv_cy](https://arxiv.org/abs/2606.12801v1)
- **REMAL: Residual Equilibrium Manifold Active Learning for Surrogate-Based Multidisciplinary Design Analysis** — [arxiv_ml](https://arxiv.org/abs/2606.13245v1)
- **Calibrating simplified vine copulas with a noise contrastive estimation approach** — [arxiv_ml](https://arxiv.org/abs/2606.13213v1)
- **Reliability of Probabilistic Emulation of Physical Systems** — [arxiv_ml](https://arxiv.org/abs/2606.12997v1)
- **Prediction-Powered Causal Inference by Automatic Debiased Machine Learning and Semi-Supervised Riesz Regression** — [arxiv_ml](https://arxiv.org/abs/2606.12892v1)
- **中信建投：算力等高频高速需求快速增长，电子级PTFE有望大规模应用** — [36kr](https://36kr.com/newsflashes/3849487518798857?f=rss)
- **SK海力士考虑引入ChatGPT等外部人工智能服务** — [36kr](https://36kr.com/newsflashes/3849477119939840?f=rss)
- **A股指数体系迈向精细化，年内新增374条指数** — [36kr](https://36kr.com/newsflashes/3849459629643008?f=rss)
- **“对赌协议”即将迎来政策层面规范，机构竞争力将回归价值发现本身** — [36kr](https://36kr.com/newsflashes/3849440819844099?f=rss)
- **氪星晚报｜百万Token只要几块钱，算力价格还在往下降；OpenAI正考虑大幅下调产品价格；今起儿童旅客可购买铁路旅游计次票，票价为成人旅客的5折** — [36kr](https://36kr.com/p/3848516305605892?f=rss)
- **ChinaJoy最硬核的区域，36氪与你共同探索 | Vision Future前沿科技展区 × 36氪直播间开启预约** — [36kr](https://36kr.com/p/3848564910036229?f=rss)
- **48元的良心日游，揭露了国产单机的最大困境 | 游戏风向标** — [36kr](https://36kr.com/p/3848383082222849?f=rss)
- **浪往南走：今年盛夏，WAVES来到番禺** — [36kr](https://36kr.com/p/3848188076381187?f=rss)
- **36氪首发 | 创维独家投资数千万，这家企业将碳化硅切割损耗降至40微米内** — [36kr](https://36kr.com/p/3848094835217666?f=rss)
- **报道：阿里拟出资15亿美元竞购中国生鲜电商“朴朴超市”** — [36kr](https://36kr.com/newsflashes/3849491937580294?f=rss)
- **两市融资余额减少52.23亿元** — [36kr](https://36kr.com/newsflashes/3849479985599488?f=rss)
- **韩美半导体将使用500亿韩元投资于SpaceX** — [36kr](https://36kr.com/newsflashes/3849477988062215?f=rss)