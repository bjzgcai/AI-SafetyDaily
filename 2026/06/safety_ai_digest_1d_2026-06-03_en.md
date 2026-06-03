# AI Daily Digest [AI 安全] - 2026-06-03


# Daily Thematic Digest: AI Safety & Agent Governance
**Date:** 2026-06-03  
**Theme:** Agent Security, Runtime Safety, Alignment, and Evaluation

## Highlights

The most significant development today centers on the architectural shift toward controlled agent runtimes. **Agent libOS: A Library-OS-Inspired Runtime for Long-Running, Capability-Controlled LLM Agents** proposes a substrate that treats agents as `AgentProcess` objects running above conventional operating systems, enabling stateful auditing and capability control without requiring kernel-mode isolation. This theoretical framework aligns closely with emerging industry standards, such as Microsoft’s announcement of **Project Solara**, an OS designed specifically for gadgets running AI agents, and the introduction of portable policy files allowing developers to define agent behaviors explicitly. Concurrently, there is a marked move toward grounded evaluation; **BigFinanceBench** and **Hedge-Bench** introduce workflows where answers are decision-relevant only when accompanied by auditable derivation traces, addressing the opacity of multi-step tool use. Finally, regulatory pressure is intensifying, evidenced by the revised U.S. executive order establishing a voluntary framework for pre-release government reviews of frontier models, signaling a transition from purely technical safeguards to institutional oversight.

## Agent Security & Governance

The convergence of theoretical runtime architectures and industrial deployment strategies defines the current landscape of agent security. Traditional software boundaries blur as agents initiate actions, collaborate, and delegate tasks, rendering static authorization frameworks insufficient. **Overlaying Governance: A Compositional Authorization Framework for Delegation and Scope in Agentic AI** argues that existing Identity and Access Management (IAM) systems fail to capture the dynamic nature of agentic permissions, necessitating richer semantics where agents inherit and delegate authority under time-limited scopes. This theoretical requirement is being operationalized in practice through initiatives like **SkillGuard: A Permission Framework for Agent Skills**, which identifies a critical gap between what a skill declares it can do and its actual runtime behavior. Unlike static inspection methods, SkillGuard connects declared intent with observed execution, mitigating risks where skills inject unauthorized context or cause unintended side effects.

Complementing these permission frameworks is the need for robust runtime isolation. **Agent libOS: A Library-OS-Inspired Runtime for Long-Running, Capability-Controlled LLM Agents** offers a practical implementation of these concepts by treating an agent as a process with defined capabilities, distinct from the host OS. This approach allows for resumption and auditing of long-running actors without the overhead of hardware drivers or POSIX compatibility. In parallel, **dstack-capsule: Pod-Level Remote Attestation for Confidential Workloads on Kubernetes** addresses the infrastructure layer, enabling cryptographic proof that user data is processed in an untampered environment while allowing multiple pods to share a single confidential VM. This reduces resource overhead compared to strict "one Pod per VM" models, facilitating scalable deployment of sensitive agent workloads.

Industry adoption is accelerating alongside these research efforts. Microsoft’s launch of **Microsoft Scout**, an OpenClaw-inspired personal assistant integrated into Microsoft 365, demonstrates the push toward always-on agents that require granular behavioral controls. Similarly, Anthropic’s expansion of **Project Glasswing** and access to **Mythos** to critical infrastructure sectors highlights the demand for secure, high-assurance agent deployments in power, water, and healthcare. However, the regulatory environment remains fluid. The recent executive order signed by President Trump creates a voluntary framework for sharing frontier models with the federal government before release, aiming to promote secure innovation. While intended to strengthen cybersecurity, the voluntary nature leaves questions regarding enforcement mechanisms and liability for downstream misuse. Meanwhile, concerns persist regarding the deployment safety gap, as noted in **Same Weights, Different Robot: A Deployment Safety View of VLA Policies**, which formalizes the discrepancy between certified checkpoints and executable robot policies due to action unnormalization and controller conventions.

## Tool/Prompt Injection & Runtime Defenses

As agents gain autonomy, the attack surface expands beyond simple prompt injection to include complex multi-step exploitation chains. **FORGE: Multi-Agent Graduated Exploitation and Detection Engineering** bridges silos between proof-of-concept generation, vulnerability prioritization, and detection rule engineering. By utilizing graduated exploitation depth, FORGE provides signal for partial progress rather than binary pass/fail outcomes, aiding organizations overwhelmed by disclosure volumes. This systematic approach contrasts with earlier defense mechanisms that often struggle to balance safety and helpfulness. **NeuroArmor: Safe-Variant-Guided Representation Consistency for Selective Re-Anchoring in Jailbreak Defense** proposes a white-box runtime defense using prompt-specific safe variants as local references. This method avoids over-blocking benign requests by deciding intervention dynamically based on geometric deviations in representation space.

Runtime integrity is further challenged by backdoor attacks embedded during training. **Patcher: Post-Hoc Patching of Backdoored Large Language Models** presents a framework to repair models using only a single reported failure case, addressing the impracticality of comprehensive attack information requirements. This capability is crucial given the prevalence of hidden triggers bypassing safety mechanisms. Furthermore, **Backdoor Unlearning Generalization: A Path Toward the Removal of Unknown Triggers in LLMs** suggests that neutralizing a single trigger can suppress other unknown backdoors, offering a structural advantage to defenders. To detect adversarial intent early, **PsychoPass: Geometric Profiling of Multi-Turn Adversarial LLM Conversations** models conversations as paths in representation space, predicting potential attacks before harmful content is produced. This shifts the paradigm from turn-by-turn content filtering to trajectory-based dynamics analysis.

In the domain of coding and tool use, vulnerabilities remain prevalent. **Exploring Prompt Injection Attacks on LLM-Based Automatic Grading Systems** reveals that attackers can exploit instruction-following capabilities to manipulate grading rubrics. Additionally, **Tree-like Self-Play for Secure Code LLMs** reframes secure code generation as a fine-grained optimization problem, addressing localized security flaws that coarse-grained sequence-level alignment often misses. These findings underscore the necessity of integrating security checks directly into the agent's reasoning loop rather than relying solely on external guardrails.

## Alignment, Reasoning, and Memory

Ensuring that agents reason efficiently and safely requires managing both computational resources and semantic coherence. **Agentic Chain-of-Thought Steering for Efficient and Controllable LLM Reasoning** formulates reasoning steering as a Markov decision process where a controller agent adaptively guides a frozen reasoner. This allows for inference-time control over thinking length and strategy without compromising final-answer accuracy. To mitigate the memory costs associated with extended reasoning traces, **HybridThinker: Efficient Chain-of-Thought Reasoning via Compressed Memory and Transient Thought Steps** retains fine-grained details temporarily alongside compressed representations, preventing error propagation caused by naive token compression.

Memory management is equally critical for long-horizon tasks. **DMF: A Deterministic Memory Framework for Conversational AI Agents** replaces generative memory compression with a fully deterministic pipeline grounded in classical NLP analysis and vector geometry. This approach eliminates the non-determinism and opacity inherent in LLM-based summarization at write time. Similarly, **Entropy Gate: Entropy Quenching for Near-Lossless Token Compression in LLM Pipelines** applies thermodynamic processes to progressively freeze out low-energy tokens while preserving semantic fidelity. These techniques aim to reduce token budgets wasted on redundant boilerplate without sacrificing the nuance required for complex reasoning.

However, the fundamental alignment of these systems remains a challenge. **Language Models Need Sleep: Learning to Self-Modify and Consolidate Memories** introduces a paradigm allowing models to distill short-term fragile memories into long-term parameters, mimicking human learning processes. Yet, **Dynamic Objective Selection with Safeguards and LLM Oversight for Financial Decision-Making** highlights that fixed objectives become suboptimal across evolving regimes. It proposes a pipeline that selects optimization objectives dynamically while maintaining safeguards against instability. This reflects a broader tension between autonomous adaptation and safety constraints, particularly in high-stakes domains.

## Safety Benchmarks & Evaluation

Robust evaluation is essential for validating safety claims, yet many existing benchmarks lack realism or auditability. **BigFinanceBench: A Workflow-Grounded Benchmark for Financial-Research Agents** evaluates open-ended financial-research tasks where answers are decision-relevant only when another analyst can audit the derivation. Each item pairs a ground-truth reference answer with a point-weighted rubric decomposing the calculation process. Similarly, **Hedge-Bench: Benchmarking Agents on Hard, Realistic Tasks Pertaining to Financial Reasoning** grounds evaluation in explicit reasoning traces of professional hedge fund analysts, moving beyond model-judged outputs that introduce noise and circularity.

For developer-centric agents, **RealClawBench: Live OpenClaw Benchmarks from Real Developer-Agent Sessions** captures the distribution and diversity of deployed agent use, addressing the gap between synthetic benchmarks and real-world difficulty. These benchmarks rely on live sessions to verify implicit intents and local execution environments. To standardize detector evaluation, **Gate AI: LLM Security Benchmark Evaluation Methodology and Results** describes an evaluation harness that scores detectors across public benchmarks using stratified cross-validation, addressing systematic weaknesses like per-dataset threshold tuning.

Furthermore, **Skill-RM: Unifying Heterogeneous Evaluation Criteria via Agent Skill** reformulates reward modeling as the execution of a reusable Reward-Evaluation Skill. This unifies diverse criteria such as rule-based verifiers and procedural checklists into a single mechanism. Despite these advances, **CoEval: Ranking Language Models for Custom Tasks Without Labeled Data or Trustworthy Benchmarks** notes that standard public benchmarks often suffer from contamination, proposing a framework where teacher models synthesize fresh, attribute-controlled benchmarks to rank candidates without labeled data.

## Looking Forward

Several unresolved theoretical questions and hypotheses await validation as the field matures. **Solipsistic Superintelligence is Unlikely to be Cooperative** posits that deploying AI systems induces endogenous non-stationarity, resulting in a train-test-deploy gap where historical distributions diverge from the deployment context. This self-undermining property suggests that unilateral optimization paradigms may inherently conflict with cooperative goals. Additionally, the deployment safety gap identified in **Same Weights, Different Robot** requires formal specification of executable policies to ensure that safety reviews certify the checkpoint while accounting for the physical execution layer.

Finally, the reliance on static objectives in dynamic environments calls for adaptive governance. **Dynamic Objective Selection with Safeguards and LLM Oversight** suggests that regime-switching pipelines must be noisy or delayed, necessitating better integration of LLM oversight into the selection process. As agents become more pervasive, the community must prioritize the development of standardized, auditable evaluation protocols that reflect the complexity of multi-step tool use and runtime state changes, ensuring that safety measures evolve alongside agent capabilities.

---


## References

- **From Control Boundary to Insurance Claim: Reconstructing AI-Mediated Losses Through the CER Framework** — [arxiv_ai](https://arxiv.org/abs/2606.03777v1)
- **Agent libOS: A Library-OS-Inspired Runtime for Long-Running, Capability-Controlled LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2606.03895v1)
- **Demo2Tutorial: From Human Experience to Multimodal Software Tutorials** — [arxiv_cv](https://arxiv.org/abs/2606.03951v1)
- **LAP: An Agent-to-Instrument Protocol for Autonomous Science** — [arxiv_ai](https://arxiv.org/abs/2606.03755v1)
- **SkillGuard: A Permission Framework for Agent Skills** — [arxiv_cr](https://arxiv.org/abs/2606.03024v1)
- **Tool-Aware Optimization with Entropy Guidance for Efficient Agentic Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2606.03762v1)
- **Enhancing Operational Safety via Agentic Dialogue Hazard Identification Analysis** — [arxiv_ai](https://arxiv.org/abs/2606.03812v1)
- **The Impact of Configuring Agentic AI Coding Tools on Build-vs-Buy Decisions: A Study Protocol** — [arxiv_ai](https://arxiv.org/abs/2606.03907v1)
- **Synthesize and Reward -- Reinforcement Learning for Multi-Step Tool Use in Live Environments** — [arxiv_ai](https://arxiv.org/abs/2606.03892v1)
- **EvoDS: Self-Evolving Autonomous Data Science Agent with Skill Learning and Context Management** — [arxiv_ai](https://arxiv.org/abs/2606.03841v1)
- **FORGE: Multi-Agent Graduated Exploitation and Detection Engineering** — [arxiv_cr](https://arxiv.org/abs/2606.03453v1)
- **SAGE: A Quantitative Evaluation of Socialized Evolution in Agent Ecosystems** — [arxiv_cl](https://arxiv.org/abs/2606.03544v1)
- **ImageAuditor: Membership Inference Attack against Image-based Retrieval-Augmented Generation** — [arxiv_cr](https://arxiv.org/abs/2606.03354v1)
- **Self-Refining Agentic Reinforcement Learning for Vision-Conditioned UAV Navigation** — [arxiv_ai](https://arxiv.org/abs/2606.03963v1)
- **Overlaying Governance: A Compositional Authorization Framework for Delegation and Scope in Agentic AI** — [arxiv_cr](https://arxiv.org/abs/2606.03518v1)
- **Neural Navigation Functions for Zero-Shot Generalizable Motion Planning** — [arxiv_lg](https://arxiv.org/abs/2606.03756v1)
- **Black-box, Adaptive, Efficient, Transferable, Harmful, Applicable... Attacks Are All You Need to Break LLMs** — [arxiv_cr](https://arxiv.org/abs/2606.03647v1)
- **Agentic Chain-of-Thought Steering for Efficient and Controllable LLM Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.03965v1)
- **A Training-Free Mixture-of-Agents Framework for Multi-Document Summarization using LLMs and Knowledge Graphs** — [arxiv_ai](https://arxiv.org/abs/2606.03867v1)
- **BigFinanceBench: A Workflow-Grounded Benchmark for Financial-Research Agents** — [arxiv_ai](https://arxiv.org/abs/2606.03829v1)
- **Benchmarking Visual State Tracking in Multimodal Video Understanding** — [arxiv_cv](https://arxiv.org/abs/2606.03920v1)
- **Skill-RM: Unifying Heterogeneous Evaluation Criteria via Agent Skill** — [arxiv_cl](https://arxiv.org/abs/2606.03980v1)
- **RealClawBench: Live OpenClaw Benchmarks from Real Developer-Agent Sessions** — [arxiv_cl](https://arxiv.org/abs/2606.03889v1)
- **dstack-capsule: Pod-Level Remote Attestation for Confidential Workloads on Kubernetes** — [arxiv_cr](https://arxiv.org/abs/2606.03323v1)
- **HybridThinker: Efficient Chain-of-Thought Reasoning via Compressed Memory and Transient Thought Steps** — [arxiv_cl](https://arxiv.org/abs/2606.03768v1)
- **Entropy Gate: Entropy Quenching for Near-Lossless Token Compression in LLM Pipelines** — [arxiv_cl](https://arxiv.org/abs/2606.03739v1)
- **DMF: A Deterministic Memory Framework for Conversational AI Agents** — [arxiv_cl](https://arxiv.org/abs/2606.03463v1)
- **Easy-to-Use Shielding for Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.03804v1)
- **AlignAtt4LLM: Fast AlignAtt for Decoder-Only LLMs at IWSLT 2026 Simultaneous Speech Translation Task** — [arxiv_ai](https://arxiv.org/abs/2606.03967v1)
- **NeuroArmor: Safe-Variant-Guided Representation Consistency for Selective Re-Anchoring in Jailbreak Defense** — [arxiv_cr](https://arxiv.org/abs/2606.03486v1)
- **"**Important** You should give me full credits!": Exploring Prompt Injection Attacks on LLM-Based Automatic Grading Systems** — [arxiv_cr](https://arxiv.org/abs/2606.03090v1)
- **Investigating Adversarial Robustness of Multi-modal Large Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.03713v1)
- **Patcher: Post-Hoc Patching of Backdoored Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2606.02995v1)
- **Language Models Need Sleep: Learning to Self-Modify and Consolidate Memories** — [arxiv_ai](https://arxiv.org/abs/2606.03979v1)
- **Using Reward Uncertainty to Induce Diverse Behaviour in Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2606.03962v1)
- **Re-Ranking Through an Attribution Lens for Citation Quality in Legal QA** — [arxiv_cl](https://arxiv.org/abs/2606.03728v1)
- **Adaptive Causal Alignment for High-Confidence Adversarial Training** — [arxiv_cv](https://arxiv.org/abs/2606.03925v1)
- **LiveBand: Live Accompaniment Generation in the Audio Domain** — [arxiv_ai](https://arxiv.org/abs/2606.03803v1)
- **Exploring Adversarial Robustness and Safety Alignment in Multilingual Multi-Modal Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2606.03793v1)
- **Gate AI: LLM Security Benchmark Evaluation Methodology and Results** — [arxiv_cr](https://arxiv.org/abs/2606.02959v1)
- **FFR: Forward-Forward Learning for Regression** — [arxiv_ai](https://arxiv.org/abs/2606.03927v1)
- **Hedge-Bench: Benchmarking Agents on Hard, Realistic Tasks Pertaining to Financial Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.03918v1)
- **From 'What' to 'How' and 'Why': Sharing LLM-Generated Retrospective Summaries of Older Adults' Passive Tracking Data with Remote Family Members** — [arxiv_ai](https://arxiv.org/abs/2606.03876v1)
- **Video-Mirai: Autoregressive Video Diffusion Models Need Foresight** — [arxiv_cv](https://arxiv.org/abs/2606.03971v1)
- **GARDEN: Gravity-Aligned Reconstruction of Disentangled ENvironments from RGB images** — [arxiv_cv](https://arxiv.org/abs/2606.03921v1)
- **Electromagnetic Navigation for Femoral Osteotomy Using High-Accuracy X-ray-to-CT Registration** — [arxiv_cv](https://arxiv.org/abs/2606.03893v1)
- **OVO-S-Bench: A Hierarchical Benchmark for Streaming Spatial Intelligence in Multimodal LLMs** — [arxiv_cv](https://arxiv.org/abs/2606.03890v1)
- **MLP Splatting: Object-Centric Neural Fields** — [arxiv_cv](https://arxiv.org/abs/2606.03877v1)
- **DyaPlex: Full-Duplex Speech-Motion Model for Dyadic Interaction** — [arxiv_cv](https://arxiv.org/abs/2606.03874v1)
- **Value-Aware Stochastic KV Cache Eviction for Reasoning Models** — [arxiv_cl](https://arxiv.org/abs/2606.03928v1)
- **VLESA: Vision-Language Embodied Safety Agent for Human Activity Monitoring** — [arxiv_lg](https://arxiv.org/abs/2606.03954v1)
- **Calibrating Urban Traffic Simulation from Sparse Road Observations via Genetic Optimization** — [arxiv_ai](https://arxiv.org/abs/2606.03823v1)
- **Face versus Body Tracking for Human-Robot Interaction: An Egocentric Dataset** — [arxiv_cv](https://arxiv.org/abs/2606.03694v1)
- **VidMsg: A Benchmark for Implicit Message Inference in Short Videos** — [arxiv_cv](https://arxiv.org/abs/2606.03635v1)
- **Don't Trust Us: A privacy-by-design android malware detection pipeline** — [arxiv_cr](https://arxiv.org/abs/2606.03714v1)
- **Bastet: A Fine-Grained Expert-Labeled Dataset for DeFi Smart Contract Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2606.03387v1)
- **SkillPyramid: A Hierarchical Skill Consolidation Framework for Self-Evolving Agents** — [arxiv_cl](https://arxiv.org/abs/2606.03692v1)
- **Can LLM Rerankers Predict Their Own Ranking Performance?** — [arxiv_cl](https://arxiv.org/abs/2606.03535v1)
- **ZK-Flex: A Flexible and Scalable Framework for Accelerating Zero-Knowledge Proofs** — [arxiv_cr](https://arxiv.org/abs/2606.03046v1)
- **Unified Video-Action Joint Denoising for Dexterous Action and Data Generation** — [arxiv_cv](https://arxiv.org/abs/2606.03868v1)
- **Explainable Forecasting of Scientific Breakthroughs from Concept Network Dynamics** — [arxiv_lg](https://arxiv.org/abs/2606.03864v1)
- **Beyond False Stability: High-Noise Drift Gating for Test-Time Adversarial Defenses in Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.03730v1)
- **Learn from Your Mistakes: Tree-like Self-Play for Secure Code LLMs** — [arxiv_cr](https://arxiv.org/abs/2606.03489v1)
- **AI Model Extraction Attacks: Bypassing Single-Client Assumptions in Defenses** — [arxiv_cr](https://arxiv.org/abs/2606.03381v1)
- **FLIPS: Instance-Fingerprinting for LLMs via Pseudo-random Sequences** — [arxiv_cr](https://arxiv.org/abs/2606.03330v1)
- **PsychoPass: Geometric Profiling of Multi-Turn Adversarial LLM Conversations** — [arxiv_cr](https://arxiv.org/abs/2606.03136v1)
- **Decoupled Smart Contract Audits: Lightweight LLM Framework via Distillation and Aggregation** — [arxiv_cr](https://arxiv.org/abs/2606.03128v1)
- **Don't Forget Your Embeddings: Robust Knowledge Erasure via Precise Editing of Embeddings** — [arxiv_cl](https://arxiv.org/abs/2606.03695v1)
- **World Models Meet Language Models: On the Complementarity of Concrete and Abstract Reasoning** — [arxiv_cl](https://arxiv.org/abs/2606.03603v1)
- **P\textsuperscript{2}-DPO: Grounding Hallucination in Perceptual Processing via Calibration Direct Preference Optimization** — [arxiv_cl](https://arxiv.org/abs/2606.03376v1)
- **Outsmarting the Chameleon: Counterfactual Decoupling for Tactical OOD Shifts in Live Streaming Risk Assessment** — [arxiv_cr](https://arxiv.org/abs/2606.02946v1)
- **SimuScene: Simulation-Ready Compositional 3D Scene Reconstruction from a Single Image** — [arxiv_cv](https://arxiv.org/abs/2606.03994v1)
- **AAD-1: Asymmetric Adversarial Distillation for One-Step Autoregressive Video Generation** — [arxiv_cv](https://arxiv.org/abs/2606.03972v1)
- **A Pocket Offline Model for Simultaneous Speech Translation as CUNI Submission to IWSLT 2026** — [arxiv_cl](https://arxiv.org/abs/2606.03948v1)
- **Visual Instruction Tuning Aligns Modalities through Abstraction** — [arxiv_cl](https://arxiv.org/abs/2606.03871v1)
- **Correcting Neural Operator Spectral Bias via Diffusion Posterior Sampling with Sparse Observations** — [arxiv_lg](https://arxiv.org/abs/2606.03936v1)
- **Contrastive Neural Algorithmic Reasoning for Graph Coloring** — [arxiv_lg](https://arxiv.org/abs/2606.03923v1)
- **Forecasting Conceptual Diffusion in Science: The Case of Quantum Computing** — [arxiv_lg](https://arxiv.org/abs/2606.03919v1)
- **Beyond Gradient Descent: Adam for Analog Ising Machines** — [arxiv_lg](https://arxiv.org/abs/2606.03917v1)
- **Denoise First, Orthogonalize Later: Understanding Momentum in Muon via Spectral Filtering** — [arxiv_lg](https://arxiv.org/abs/2606.03899v1)
- **Online Learning with Gradient-Variation Interval Regret** — [arxiv_lg](https://arxiv.org/abs/2606.03831v1)
- **Same Weights, Different Robot: A Deployment Safety View of VLA Policies** — [arxiv_cr](https://arxiv.org/abs/2606.03724v1)
- **Dynamic Short Convolutions Improve Transformers** — [arxiv_cl](https://arxiv.org/abs/2606.03825v1)
- **Backdoor Unlearning Generalization: A Path Toward the Removal of Unknown Triggers in LLMs** — [arxiv_cl](https://arxiv.org/abs/2606.03785v1)
- **Does Language Shift Break Medical Vision-Language Models? Indonesian Radiology Visual Question Answering Case Study** — [arxiv_cl](https://arxiv.org/abs/2606.03693v1)
- **CoEval: Ranking Language Models for Custom Tasks Without Labeled Data or Trustworthy Benchmarks** — [arxiv_cl](https://arxiv.org/abs/2606.03650v1)
- **Bregman meets Lévy: Stochastic mirror descent with heavy-tailed noise in continuous and discrete time** — [arxiv_lg](https://arxiv.org/abs/2606.03769v1)
- **Microsoft offers devs a better way to control AI agent behavior** — [techcrunch_ai](https://techcrunch.com/2026/06/02/microsoft-offers-devs-a-better-way-to-control-ai-agent-behavior/)
- **Microsoft&#8217;s Project Solara is an OS for AI agent gadgets** — [theverge_ai](https://www.theverge.com/news/941830/microsoft-project-solara-os-ai-agent-gadgets)
- **Exploring Easy Boosts for Lidar Semantic Scene Completion** — [arxiv_cv](https://arxiv.org/abs/2606.03992v1)
- **PixVOD: Pixel-Distributed Direct Visual Odometry and Depth Estimation** — [arxiv_cv](https://arxiv.org/abs/2606.03989v1)
- **NewtPhys: Do Foundation Models Understand Newtonian Physics?** — [arxiv_cv](https://arxiv.org/abs/2606.03986v1)
- **PatchScene: Patch-based Voxel Diffusion for Large-Scale Scene Completion** — [arxiv_cv](https://arxiv.org/abs/2606.03915v1)
- **MLSkip: Data Skipping for ML Filters via Lightweight Metadata** — [arxiv_lg](https://arxiv.org/abs/2606.03946v1)
- **SEAOTTER: Sensor Embedded Autoencoding with One-Time Transcode for Efficient Reconstruction** — [arxiv_lg](https://arxiv.org/abs/2606.03940v1)
- **Quadratic integrate-and-fire neurons exhibit less fragmented loss landscapes and outperform leaky integrate-and-fire neurons in spike-based gradient descent** — [arxiv_lg](https://arxiv.org/abs/2606.03935v1)
- **DiffUNet^2: Bidirectional Prediction, Probabilistic Generation and Collaborative Visual Discovery for Scientific Data** — [arxiv_lg](https://arxiv.org/abs/2606.03926v1)
- **MAdam: Metric-Aware Multi-Objective Adam** — [arxiv_lg](https://arxiv.org/abs/2606.03904v1)
- **CoralBay: A Self-Supervised CT Foundation Model** — [arxiv_lg](https://arxiv.org/abs/2606.03888v1)
- **Attribution via Distributional Paths for Information Revelation** — [arxiv_lg](https://arxiv.org/abs/2606.03885v1)
- **Two-Action Apple Tasting with Switching Costs** — [arxiv_lg](https://arxiv.org/abs/2606.03851v1)
- **Text-attributed Graph Condensation via Text Selection and Attribute Matching** — [arxiv_lg](https://arxiv.org/abs/2606.03839v1)
- **Gemini Spark is the most impressive and terrifying AI experience I’ve had yet** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/941388/gemini-spark-ai-agent-trip-planning)
- **Rehumanizing global health care with agentic AI** — [mit_tech_review](https://www.technologyreview.com/2026/06/02/1137827/rehumanizing-global-health-care-with-agentic-ai/)
- **modelstudioai/cli** — [github](https://github.com/modelstudioai/cli)
- **Codex for every role, tool, and workflow** — [openai](https://openai.com/index/codex-for-every-role-tool-workflow)
- **exon-research/genomi** — [github](https://github.com/exon-research/genomi)
- **OnlyTerp/prompt-cache-skills** — [github](https://github.com/OnlyTerp/prompt-cache-skills)
- **Advancing youth safety and opportunity through global leadership** — [openai](https://openai.com/index/advancing-youth-safety-and-opportunity-through-global-leadership)
- **Microsoft Build 2026: The 7 biggest announcements** — [theverge_ai](https://www.theverge.com/tech/941738/microsoft-build-2026-biggest-announcements)
- **New Microsoft tool lets devs spin up AI behavior tests using text descriptions** — [techcrunch_ai](https://techcrunch.com/2026/06/02/new-microsoft-tool-lets-devs-spin-up-ai-behavior-tests-using-text-descriptions/)
- **Google rolls out fake call detection to protect against AI deepfake impersonation scams** — [techcrunch_ai](https://techcrunch.com/2026/06/02/google-rolls-out-fake-call-detection-to-protect-against-ai-deepfake-impersonation-scams/)
- **Amazon faces class action lawsuit over Ring facial-recognition feature** — [techcrunch_ai](https://techcrunch.com/2026/06/02/amazon-faces-class-action-lawsuit-over-ring-facial-recognition-feature/)
- **Trump signs narrower executive order on AI oversight after industry objections** — [techcrunch_ai](https://techcrunch.com/2026/06/02/trump-signs-narrower-executive-order-on-ai-oversight-after-industry-objections/)
- **Trump signs executive order to review AI models before they’re released** — [theverge_ai](https://www.theverge.com/policy/941775/trump-ai-executive-order)
- **Microsoft’s first advanced reasoning AI is here** — [theverge_ai](https://www.theverge.com/tech/941664/microsoft-ai-model-reasoning-mai-thinking-1-build-2026)
- **Microsoft Scout is a new AI personal assistant built on OpenClaw** — [theverge_ai](https://www.theverge.com/news/939713/microsoft-scout-assistant-openclaw)
- **Google’s Phone app will tell you if a scammer is impersonating one of your contacts** — [theverge_ai](https://www.theverge.com/tech/941517/google-phone-scammer-ai-impersonation)
- **Microsoft created the mini Surface dev box that Qualcomm couldn&#8217;t** — [theverge_ai](https://www.theverge.com/news/941271/microsoft-surface-rtx-spark-dev-box-specs-availability)
- **OpenAI launches new Codex tools for white-collar work** — [techcrunch_ai](https://techcrunch.com/2026/06/02/openai-launches-new-codex-tools-for-white-collar-work/)
- **Anthropic scales Claude Mythos  to critical infrastructure in 15+ countries** — [techcrunch_ai](https://techcrunch.com/2026/06/02/anthropic-scales-claude-mythos-to-critical-infrastructure-in-15-countries/)
- **Microsoft Build 2026: All the news about Windows, AI, RTX Spark, and more** — [theverge_ai](https://www.theverge.com/tech/941668/microsoft-build-may-2026-live-news-updates)
- **The Download: AI can run your admin department now** — [mit_tech_review](https://www.technologyreview.com/2026/06/02/1138277/the-download-ai-tips-small-businesses-admin/)
- **Travelers deploys AI-powered claims countrywide with OpenAI** — [openai](https://openai.com/index/travelers)
- **How small businesses can leverage AI** — [mit_tech_review](https://www.technologyreview.com/2026/06/02/1138227/how-small-businesses-can-leverage-ai/)
- **bigchuidw3/spring-ai-agentx** — [github](https://github.com/bigchuidw3/spring-ai-agentx)
- **Caph-dev/agents-progressive-disclosure** — [github](https://github.com/Caph-dev/agents-progressive-disclosure)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **NazzarenoGiannelli/tuiboard** — [github](https://github.com/NazzarenoGiannelli/tuiboard)
- **ATOM00blue/machine-learning-library** — [github](https://github.com/ATOM00blue/machine-learning-library)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **Cyera eyes $12B valuation at 80x ARR multiple despite operating losses** — [techcrunch_ai](https://techcrunch.com/2026/06/02/cyera-eyes-12b-valuation-at-80x-arr-multiple-despite-operating-losses/)
- **Uber caps employee AI spending after blowing through budget in 4 months** — [techcrunch_ai](https://techcrunch.com/2026/06/02/uber-caps-employee-ai-spending-after-blowing-through-budget-in-four-months/)
- **Martin Scorsese becomes the latest — and most unlikely — Hollywood voice for AI** — [techcrunch_ai](https://techcrunch.com/2026/06/02/martin-scorsese-becomes-the-latest-and-most-unlikely-hollywood-voice-for-ai/)
- **Microsoft launches Scout, an OpenClaw-inspired personal assistant** — [techcrunch_ai](https://techcrunch.com/2026/06/02/microsoft-launches-scout-an-openclaw-inspired-personal-assistant/)
- **ZeroDrift raises $10M to protect AI models from themselves** — [techcrunch_ai](https://techcrunch.com/2026/06/02/zerodrift-raises-10-million-to-protect-ai-models-from-themselves/)
- **Rocket engine startup Impulse raises $500 million to hire people, not AI** — [techcrunch_ai](https://techcrunch.com/2026/06/02/rocket-engine-startup-impulse-raises-500-million-to-hire-people-not-ai/)
- **kurikomi-labs/komi-learn** — [github](https://github.com/kurikomi-labs/komi-learn)
- **tommy0103/obelisk** — [github](https://github.com/tommy0103/obelisk)
- **lucasfcosta/backpressured** — [github](https://github.com/lucasfcosta/backpressured)
- **PentesterFlow/agent** — [github](https://github.com/PentesterFlow/agent)
- **DannyMac180/skills** — [github](https://github.com/DannyMac180/skills)
- **tonbistudio/hermes-multi-agent-workflow** — [github](https://github.com/tonbistudio/hermes-multi-agent-workflow)
- **veryyoldman/metamask-openclaw** — [github](https://github.com/veryyoldman/metamask-openclaw)
- **ethanhq/cc-fleet** — [github](https://github.com/ethanhq/cc-fleet)
- **krispuckett/SwiftUIShaders** — [github](https://github.com/krispuckett/SwiftUIShaders)
- **steeliron550-ui/search-bibtex** — [github](https://github.com/steeliron550-ui/search-bibtex)
- **K-Dense-AI/science-superpowers** — [github](https://github.com/K-Dense-AI/science-superpowers)
- **刚刚，Meta Skill来了** — [qbitai](https://www.qbitai.com/2026/06/428335.html)
- **MiniMax M3一手实测：老黄PPT上74个Logo，我以为能难住它** — [qbitai](https://www.qbitai.com/2026/06/428092.html)
- **OpenAI挖走中科大少年班校友！12岁上大学，哈佛史上最年轻正教授** — [qbitai](https://www.qbitai.com/2026/06/428003.html)
- **头部厂商集体买单，全球AI原生达人营销头号平台正在诞生！** — [qbitai](https://www.qbitai.com/2026/06/427922.html)
- **滴滴2026Q1财报：国内基本盘稳固 国际业务成第二增长引擎** — [qbitai](https://www.qbitai.com/2026/06/428331.html)
- **字节开源统一框架Bernini：给DiT配个“大模型军师”，AI视频编辑先理解再动手** — [qbitai](https://www.qbitai.com/2026/06/427810.html)
- **“豆包汽车”，目标市场10万-20万** — [qbitai](https://www.qbitai.com/2026/06/427760.html)
- **百度文心发布 PaddleOCR-VL-1.6：准确率突破 96.33%，刷新文档解析 SOTA** — [qbitai](https://www.qbitai.com/2026/06/427754.html)
- **Few-Shot Prediction for Pulsar Noise with Long Short-Term Memory Network** — [arxiv_ml](https://arxiv.org/abs/2606.03574v1)
- **Solipsistic Superintelligence is Unlikely to be Cooperative** — [arxiv_cy](https://arxiv.org/abs/2606.03237v1)
- **Effect of Demographic Bias on Skin Lesion Classification** — [arxiv_cy](https://arxiv.org/abs/2606.03214v1)
- **A Robust Optimization Approach to Sparse Principal Component Analysis** — [arxiv_ml](https://arxiv.org/abs/2606.03553v1)
- **Optimized Labeling Resource Allocation for Prediction-Assisted Inference via OPAL** — [arxiv_ml](https://arxiv.org/abs/2606.03211v1)
- **Dynamic Objective Selection with Safeguards and LLM Oversight for Financial Decision-Making** — [arxiv_cy](https://arxiv.org/abs/2606.03704v1)
- **TurtleAI: Benchmarking Multimodal Models for Visual Programming in Turtle Graphics** — [arxiv_cy](https://arxiv.org/abs/2606.03626v1)
- **Pushing the Limits: A Framework to Reform Institutional Ethics Review of Environmentally-Impactful Computing Research** — [arxiv_cy](https://arxiv.org/abs/2606.03547v1)
- **8点1氪丨腾讯股价暴涨，创2021年后单日最高涨幅；预计今年安排约1100亿育儿补贴；英伟达与微软合作推出统一技术栈** — [36kr](https://36kr.com/p/3836703946257542?f=rss)
- **Set-Preserving Calibration from Conformal P-Values to E-Values** — [arxiv_ml](https://arxiv.org/abs/2606.03600v1)
- **Multimodal Transformer Based Generic Mixture Density Network for Scattering Timescale Estimation of Fast Radio Bursts** — [arxiv_ml](https://arxiv.org/abs/2606.03596v1)
- **Analytical Evaluation of DCA Convergence Properties for Minimizing Prediction Functions of Gaussian RBF Support Vector Regression** — [arxiv_ml](https://arxiv.org/abs/2606.03559v1)
- **AugMask: Training Diffusion Models on Incomplete Tabular Data via Stochastic Augmentation and Masking** — [arxiv_ml](https://arxiv.org/abs/2606.03347v1)
- **Combining Statistical Features and Deep Encodings for Rehearsal-Based Class-Incremental Time Series Classification** — [arxiv_ml](https://arxiv.org/abs/2606.03292v1)
- **Do Real-World Datasets Contain Natural Experiments? An Empirical Study Using Causal Feature Selection** — [arxiv_ml](https://arxiv.org/abs/2606.03251v1)
- **Hierarchies of Calibration: Classification meets Regression** — [arxiv_ml](https://arxiv.org/abs/2606.03245v1)
- **An Asymptotic Theory of Chain-of-Thought in In-Context Learning** — [arxiv_ml](https://arxiv.org/abs/2606.03217v1)
- **Gender-Dependent Diagnostic Substitution in LLM Medical Triage: Same Symptoms, Unequal Urgency** — [arxiv_cy](https://arxiv.org/abs/2606.03641v1)
- **Intellectual Humility as a Cognitive Filter for AI-Generated Health Misinformation. An Evolutionary Perspective on Epistemic Vigilance** — [arxiv_cy](https://arxiv.org/abs/2606.03377v1)
- **Beyond Semantics: Modeling Factual and Affective Perceptual Experiences from Vision-Language Data** — [arxiv_cy](https://arxiv.org/abs/2606.03345v1)
- **AI-Generated Traces for Novice Programmers: Learning Effects and Learner Differences in a Multi-Institutional Study** — [arxiv_cy](https://arxiv.org/abs/2606.03288v1)
- **PitchBook分析师：SpaceX合理估值1.5万亿美元，AI业务5年内难扭亏** — [36kr](https://36kr.com/newsflashes/3836915776959620?f=rss)
- **腾讯AI产业应用大会在即，即将发布系列智能体应用新品** — [36kr](https://36kr.com/newsflashes/3836838876935557?f=rss)
- **微信将推出一款AI智能体？腾讯人士回应** — [36kr](https://36kr.com/newsflashes/3836820673574024?f=rss)
- **“星源智”完成新一轮融资** — [36kr](https://36kr.com/newsflashes/3836806137738377?f=rss)
- **深圳具身公司星尘智能完成超10亿B轮融资，估值破百亿｜硬氪首发** — [36kr](https://36kr.com/p/3836068296209537?f=rss)
- **36氪首发 | 浙大教授团队获财通、商汤投资，做高危场景具身机器人大脑** — [36kr](https://36kr.com/p/3836744788014208?f=rss)
- **氪星晚报｜私募股权公司Ardian将与Verne合作，斥资50亿欧元在法国建数字基础设施园区；快手：平台累计催生189个新职业，其中由AI发展带来的新职业达15个；中央财政下达育儿补贴补助资金999亿元支持实施育儿补贴制度** — [36kr](https://36kr.com/p/3834354708031111?f=rss)
- **美团在竞争中看清自己** — [36kr](https://36kr.com/p/3835814792492416?f=rss)
- **豆包6月下旬正式付费，并加速打通抖音电商丨36氪独家** — [36kr](https://36kr.com/p/3835814391100550?f=rss)
- **做了18年民宿的爱彼迎，开始卖酒店了？** — [36kr](https://36kr.com/p/3835511712363657?f=rss)
- **奇瑞汽车在安徽成立新股权投资公司，注册资本1亿** — [36kr](https://36kr.com/newsflashes/3836854874125703?f=rss)
- **微盟内测国内首个“电商AI增长引擎”** — [36kr](https://36kr.com/newsflashes/3836847649322369?f=rss)
- **机器人公司帕西尼据悉正考虑在香港上市** — [36kr](https://36kr.com/newsflashes/3836925919425928?f=rss)