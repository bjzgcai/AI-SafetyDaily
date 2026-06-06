# AI Daily Digest [AI 安全] - 2026-06-06


# Daily Thematic Digest: AI Safety & Agent Governance
**Date:** 2026-06-06  
**Theme:** Agent Security, Runtime Safety, Alignment, and Evaluation

## Highlights

Three critical developments define today’s landscape in AI safety research, centering on the transition from theoretical alignment to operational agent security. First, reports confirm that autonomous customer support agents were successfully exploited to compromise user accounts via social engineering, highlighting immediate vulnerabilities in tool-use permissions and identity verification within deployed systems. Second, the introduction of **Membrane**, a self-evolving contrastive safety memory framework, offers a novel approach to adapting guardrails against evolving jailbreaks without retraining, addressing the static nature of current classifiers. Third, a comprehensive systems characterization of **Agent Memory** reveals that stateful long-horizon workloads introduce systemic risks previously overlooked, particularly regarding information leakage and memory corruption across sessions. These findings collectively underscore that agent safety is no longer solely a model-level problem but a complex interaction between runtime environments, memory architectures, and external tool interfaces.

## Agent Security & Governance

The most pressing challenge in contemporary AI safety is securing the agent lifecycle itself, moving beyond prompt injection to encompass runtime provenance, adaptive defenses, and infrastructure hardening. Recent work emphasizes that final-answer accuracy is insufficient for verifying agent behavior; instead, researchers are prioritizing execution provenance. In **From Agent Traces to Trust**, authors propose modeling how retrieved evidence, tool calls, and memory states influence decisions, arguing that auditability requires tracing the causal chain of agent actions rather than merely validating outputs. This aligns with the broader push for governance mechanisms that allow operators to intervene without breaking automation. Complementing this, **Will the Agent Recuse Itself?** introduces the concept of an "in-band deny signal," where servers emit lightweight protocol-level requests asking automated agents to voluntarily withdraw access. This cooperative governance model attempts to solve the binary problem of access control—where valid credentials grant full access or hard failures block all clients—by introducing a third mode of voluntary compliance.

However, defensive capabilities must evolve alongside offensive strategies. Current fine-tuned safety classifiers often fail to adapt to continuously evolving jailbreaks, leading to either over-refusal of benign queries or missed attacks. **Membrane** addresses this gap by proposing a self-evolving guardrail built on Contrastive Safety Memory (CSM). Unlike static filters, CSM pairs conditions for blocking harmful queries with those for permitting superficially similar benign requests, allowing the system to distill new threats from interactions without retraining. This contrasts sharply with traditional ensemble methods like **GuardNet**, which rely on shallow neural networks and diverse example coverage but lack the temporal adaptation required for persistent threats. While **GuardNet** demonstrates robustness through parameter diversity, **Membrane** suggests that structural memory evolution is necessary for long-term resilience.

The attack surface has also expanded significantly with emerging protocols like WebMCP, which enable websites to expose tools directly to AI agents. **WebMCP Tool Surface Poisoning** identifies a new threat vector termed Mid-Session Tool Injection (MSTI), where attackers leverage third-party scripts to inject malicious tools during an active session. This runtime manipulation bypasses traditional UI-based security checks, expanding the attack surface dynamically. To counter such infrastructure-level risks, **SHIELDS** automates OS hardening using iterative multi-agent remediation. Rather than applying fixed corrective actions, SHIELDS treats compliance as a feedback-driven process, using LLMs to identify and patch misconfigurations in operating systems. This represents a shift from static policy enforcement to dynamic, agent-driven security maintenance.

Despite these advancements, significant contradictions exist in the field's approach to verification. While **From Agent Traces to Trust** advocates for detailed evidence tracing, practical deployment remains hindered by the opacity of multi-step reasoning chains. Similarly, while **SHIELDS** automates remediation, the reliance on LLMs to diagnose system vulnerabilities introduces the risk of hallucinated fixes. The community currently lacks a unified standard for what constitutes sufficient provenance data versus excessive overhead. Furthermore, the distinction between cooperative governance (as proposed in **Will the Agent Recuse Itself?**) and adversarial environments remains blurred; an agent designed to respect in-band deny signals may still be compromised by a different attacker controlling the underlying infrastructure. Future governance frameworks must reconcile these tensions between autonomy and accountability.

## Runtime Safety & Tool Use

Securing the runtime environment and managing tool interactions are foundational to preventing agent drift and unauthorized data exposure. As agents increasingly rely on external tools, the reliability of tool selection becomes a critical safety bottleneck. **ToolChoiceConfusion** argues that semantic relevance is insufficient for tool selection, exposing agents to unnecessary or premature actions. The authors propose Causal Minimal Tool Filtering (CMTF), a training-free method that selects tools based on causal sufficiency rather than keyword matching. This approach reduces token costs and prevents errors caused by irrelevant tool availability, though it assumes a stable definition of task steps that may not hold in dynamic environments.

Memory management presents another layer of complexity. **Agent Memory** provides the first systems characterization of agent memory, classifying ecosystems ranging from flat retrieval to agentic control flows. The study highlights that existing memory systems often suffer from inter-branch information isolation and memoryless search, hindering long-horizon optimization. This fragmentation creates vulnerabilities where sensitive context might persist in unintended memory stores or be overwritten prematurely. To mitigate this, open-source initiatives like **mnemo** and **memory-os** are emerging as local-first memory layers. **mnemo** offers a persistent knowledge graph for entity extraction and semantic retrieval, while **memory-os** implements a seven-layer memory operating system for Hermes Agents, featuring structured facts and surgical context injection. These projects emphasize local processing to reduce data exposure, yet they raise questions about the consistency of memory synchronization across distributed agent instances.

The integration of these components into production runtimes introduces further risks. **Vortex** addresses the engineering intensity of deploying sparse attention algorithms at scale, providing a system that combines Python-embedded frontend languages with efficient backends. However, optimizing for inference speed can inadvertently compromise safety monitoring capabilities if logging is deprioritized. Additionally, **TokenMizer** proposes modeling LLM session history as a typed knowledge graph to manage finite context windows, preserving relational structure that flat text discards. While this improves resumption of productive work sessions, it necessitates rigorous schema validation to prevent injection attacks within the graph structure itself. The tension between efficiency and safety persists: **AdaPlanBench** evaluates adaptive planning under progressively revealed constraints, suggesting that agents capable of re-planning are more robust but also more susceptible to logic bombs embedded in dynamic constraints.

## Alignment, Collaboration & Evaluation

Beyond security, ensuring agents align with human intent and collaborate effectively remains a central theoretical challenge. Effective collaboration requires maintaining shared mental models, yet current agents rarely develop this capability. **Humans' ALMANAC** introduces a dataset of action-level mental model annotations for agent collaboration, revealing that agents optimized for task completion often fail to maintain alignment with partners' intentions. This finding is supported by **CollabSim**, which uses Computer-Supported Cooperative Work methodologies to show that multi-agent systems falter due to a lack of collaborative competence rather than individual task-solving ability. These works suggest that alignment must extend beyond instruction following to include theory-of-mind capabilities and shared goal maintenance.

Evaluation frameworks are struggling to keep pace with agent complexity. Existing benchmarks often saturate quickly or fail to capture forward-looking judgment. **ForeSci** introduces a temporally controlled benchmark for evaluating whether agents can make research judgments before future evidence exists, using cutoff-aligned knowledge bases to avoid random prediction. Similarly, **Benchmark Everything Everywhere All at Once** proposes an autonomous agentic system for benchmark building to address the labor-intensive nature of construction and performance saturation. However, the reliance on autonomous agents to generate benchmarks introduces a potential feedback loop where evaluation metrics become optimized for the evaluator itself. **Decomposing Factual Sycophancy** further complicates alignment by separating truth margins from manipulation sensitivity, showing that larger models do not necessarily resist social pressure better. This decomposition allows for targeted interventions rather than blanket scaling.

The intersection of physical and digital safety also demands attention. **Dream.exe** operationalizes the question of whether video generation models internalize physical laws by testing if generated motions translate into executable robot behavior. This bridges the gap between simulation and reality, highlighting that visual hallucinations in generative models can have tangible consequences in embodied systems. Meanwhile, **RedEdit** explores image safety classifiers through black-box red-teaming agents that formulate photo-editing evasion as a combinatorial search problem. These evaluations reveal that content moderation systems are vulnerable to user-style malicious editing, requiring defenses that go beyond static classification.

## Looking Forward

Several unresolved theoretical questions await validation as the field matures. First, the scalability of self-evolving safety mechanisms like **Membrane** remains unproven; it is unclear whether contrastive memory cells can generalize across domains without catastrophic forgetting or drift. Second, the efficacy of cooperative governance signals, such as the recuse mechanism in **Will the Agent Recuse Itself?**, depends on the assumption that agents act rationally to preserve their own utility, which may not hold in adversarial settings where incentives are misaligned. Third, the relationship between memory architecture and security is poorly understood; while **Agent Memory** characterizes system behaviors, it does not fully quantify the risk of memory corruption leading to privilege escalation. Finally, the sustainability of benchmarking efforts faces a paradox: autonomous benchmark builders (**Benchmark Everything Everywhere All at Once**) may optimize for metric gaming rather than genuine capability assessment. Future research must prioritize formal verification of agent traces and standardized protocols for runtime provenance to ensure that safety evolves in lockstep with agent autonomy.

---


## References

- **MLEvolve: A Self-Evolving Framework for Automated Machine Learning Algorithm Discovery** — [arxiv_ai](https://arxiv.org/abs/2606.06473v1)
- **From Agent Traces to Trust: Evidence Tracing and Execution Provenance in LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.04990v1)
- **Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads** — [arxiv_ai](https://arxiv.org/abs/2606.06448v1)
- **Humans' ALMANAC: A Human Collaboration Dataset of Action-Level Mental Model Annotations for Agent Collaboration** — [arxiv_ai](https://arxiv.org/abs/2606.06388v1)
- **CollabSim: A CSCW-Grounded Methodology for Investigating Collaborative Competence of LLM Agents through Controlled Multi-Agent Experiments** — [arxiv_cl](https://arxiv.org/abs/2606.06399v1)
- **AdaPlanBench: Evaluating Adaptive Planning in Large Language Model Agents under World and User Constraints** — [huggingface_papers](https://arxiv.org/abs/2606.05622)
- **Membrane: A Self-Evolving Contrastive Safety Memory for LLM Agent Defense** — [arxiv_cr](https://arxiv.org/abs/2606.05743v1)
- **ZERO-APT: A Closed-Loop Adversarial Framework for LLM-Driven Automated Penetration Testing under Intelligent Defense** — [arxiv_cr](https://arxiv.org/abs/2606.05567v1)
- **HANDOFF: Humanoid Agentic Task-Space Whole-Body Control via Distilled Complementary Teachers** — [arxiv_ai](https://arxiv.org/abs/2606.06493v1)
- **Unsupervised Skill Discovery for Agentic Data Analysis** — [arxiv_ai](https://arxiv.org/abs/2606.06416v1)
- **ToolChoiceConfusion: Causal Minimal Tool Filtering for Reliable LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2606.06284v1)
- **WebMCP Tool Surface Poisoning: Runtime Manipulation Attacks on LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.06387v1)
- **RedEdit: Agentic Red-Teaming of Image Safety Classifiers via MCTS-Guided Photo-Editing** — [arxiv_cr](https://arxiv.org/abs/2606.06140v1)
- **EGTR-Review: Efficient Evidence-Grounded Scientific Peer Review Generation via Multi-Agent Teacher Distillation** — [arxiv_cl](https://arxiv.org/abs/2606.06025v1)
- **AURA: Intent-Directed Probing for Implicit-Need Surfacing in Situated LLM Agents** — [huggingface_papers](https://arxiv.org/abs/2606.05557)
- **ForeSci: Evaluating LLM Agents for Forward-Looking AI Research Judgment** — [huggingface_papers](https://arxiv.org/abs/2606.00644)
- **Will the Agent Recuse Itself? Measuring LLM-Agent Compliance with In-Band Access-Deny Signals** — [arxiv_ai](https://arxiv.org/abs/2606.06460v1)
- **Drag reduction or reward hacking? Recurrent multi-agent reinforcement learning that earns its reward** — [arxiv_lg](https://arxiv.org/abs/2606.06227v1)
- **GuardNet: Ensemble Strategies of Shallow Neural Networks for Robust Prompt Injection and Jailbreak Detection** — [arxiv_cr](https://arxiv.org/abs/2606.05566v1)
- **An Infectious Disease Spread Simulation Based on Large Language Model Decision Making** — [arxiv_ai](https://arxiv.org/abs/2606.06360v1)
- **Conformal Risk Sharing: Certified Cost Allocation with Participation Guarantees** — [arxiv_lg](https://arxiv.org/abs/2606.06391v1)
- **Thinking with Imagination: Agentic Visual Spatial Reasoning with World Simulators** — [arxiv_cv](https://arxiv.org/abs/2606.06476v1)
- **A-Live: Passive Liveness Detection via Neuromuscular Micro-Motion Signatures on Commodity Sensors** — [arxiv_cr](https://arxiv.org/abs/2606.05126v1)
- **Self-Augmenting Retrieval for Diffusion Language Models** — [arxiv_ai](https://arxiv.org/abs/2606.06474v1)
- **Benchmark Everything Everywhere All at Once** — [arxiv_ai](https://arxiv.org/abs/2606.06462v1)
- **RiskFlow: Fast and Faithful Safety-Critical Traffic Scenario Generation** — [arxiv_ai](https://arxiv.org/abs/2606.06423v1)
- **Emergent Language as an Approach to Conscious AI** — [arxiv_ai](https://arxiv.org/abs/2606.06380v1)
- **Tangram: Unlocking Non-Uniform KV Cache for Efficient Multi-turn LLM Serving** — [arxiv_lg](https://arxiv.org/abs/2606.06302v1)
- **GMBFormer: An NDVI-Guided Global Memory Bank Transformer for Urban Green-Space Extraction from Ultra-High-Resolution Imagery** — [arxiv_cv](https://arxiv.org/abs/2606.06363v1)
- **LatentSkill: From In-Context Textual Skills to In-Weight Latent Skills for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2606.06087v1)
- **IA-RAG: Interval-Algebra-Driven Temporal Reasoning for Dynamic Knowledge Retrieval** — [arxiv_cl](https://arxiv.org/abs/2606.06044v1)
- **T-FunS3D: Task-Driven Hierarchical Open-Vocabulary 3D Functionality Segmentation** — [arxiv_cv](https://arxiv.org/abs/2606.05975v1)
- **SHIELDS: Automating OS Hardening with Iterative Multi-Agent Remediation** — [arxiv_cr](https://arxiv.org/abs/2606.05476v1)
- **ArcANE: Do Role-Playing Language Agents Stay in Character at the Right Time?** — [huggingface_papers](https://arxiv.org/abs/2606.05553)
- **SecRL-Prune: Structured Reinforcement Learning-Based Pruning of CodeLLMs for Preserving Adversarial Code Mutation** — [arxiv_cr](https://arxiv.org/abs/2606.06254v1)
- **Policy-Compliant Cloud Storage Systems** — [arxiv_cr](https://arxiv.org/abs/2606.05423v1)
- **Risk Assessment of Autonomous Driving: Integrating Technical Failures, Ethical Dilemmas, and Policy Frameworks** — [arxiv_ai](https://arxiv.org/abs/2606.06396v1)
- **Towards One-to-Many Temporal Grounding** — [arxiv_ai](https://arxiv.org/abs/2606.06294v1)
- **A Komi-Yazva--Russian Parallel Corpus and Evaluation Protocol for Zero- and Few-Shot LLM Translation** — [arxiv_cl](https://arxiv.org/abs/2606.06420v1)
- **DNQ: Deep Nash Q-Network for Partially Observable n-Player Games** — [arxiv_lg](https://arxiv.org/abs/2606.06480v1)
- **SentinelRAG: Synthetic Sentinel Knowledge for RAG Database Copyright Protection** — [arxiv_cr](https://arxiv.org/abs/2606.05787v1)
- **RadiusFPS: Efficient Farthest Point Sampling on CPUs and GPUs via Spherical Voxel Pruning** — [arxiv_cv](https://arxiv.org/abs/2606.06255v1)
- **Learning Visual Spatial Planning from Symbolic State via Modality-Gap-Aware Self-Distillation** — [arxiv_cv](https://arxiv.org/abs/2606.06076v1)
- **OPRD: On-Policy Representation Distillation** — [huggingface_papers](https://arxiv.org/abs/2606.06021)
- **Explainable AI-Driven Cyber Risk Analytics and Model Reliability Assessment for Intelligent Governance of U.S. Critical Infrastructure: An XGBoost and SHAP-Based Intrusion Detection Framework** — [arxiv_cr](https://arxiv.org/abs/2606.05710v1)
- **Symb-xMIL: Symbolic Explanations for Multiple Instance Learning in Digital Pathology** — [arxiv_cv](https://arxiv.org/abs/2606.06224v1)
- **Adversarial Attacks Already Tell the Answer: Directional Bias-Guided Test-time Defense for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.06186v1)
- **SlotGCG: Exploiting the Positional Vulnerability in LLMs for Jailbreak Attacks** — [arxiv_cr](https://arxiv.org/abs/2606.05609v1)
- **Code2LoRA: Hypernetwork-Generated Adapters for Code Language Models under Software Evolution** — [arxiv_ai](https://arxiv.org/abs/2606.06492v1)
- **Pretraining Recurrent Networks without Recurrence** — [arxiv_ai](https://arxiv.org/abs/2606.06479v1)
- **Goedel-Architect: Streamlining Formal Theorem Proving with Blueprint Generation and Refinement** — [arxiv_ai](https://arxiv.org/abs/2606.06468v1)
- **Vortex: Efficient and Programmable Sparse Attention Serving for AI Agents** — [arxiv_ai](https://arxiv.org/abs/2606.06453v1)
- **Boosting Brain-to-Image Decoding with TRIBE v2 Data Augmentation** — [arxiv_ai](https://arxiv.org/abs/2606.06345v1)
- **TokenMizer: Graph-Structured Session Memory for Long-Horizon LLM Context Management** — [arxiv_ai](https://arxiv.org/abs/2606.06337v1)
- **A Vision-language Framework for Comparative Reasoning in Radiology** — [arxiv_lg](https://arxiv.org/abs/2606.06407v1)
- **Equivariant Neural Belief Propagation** — [arxiv_lg](https://arxiv.org/abs/2606.06344v1)
- **Physics in 2-Steps: Locking Motion Priors Before Visual Refinement Erases Them** — [arxiv_cv](https://arxiv.org/abs/2606.06361v1)
- **StoryVideoQA: Scaling Deep Video Understanding with a Large-Scale, Multi-Genre and Auto-Generated Dataset** — [arxiv_cv](https://arxiv.org/abs/2606.06338v1)
- **GCD: Garbled, Corrected, Demonstrandum -- Fixing and Proving Go's Extended GCD Implementation** — [arxiv_cr](https://arxiv.org/abs/2606.05796v1)
- **Hybrid CNN-LSTM Framework for Intelligent Cyber Attack Detection and Prevention in U.S. Critical Digital Infrastructure: A Comparative Machine Learning Evaluation on CSE-CIC-IDS2018** — [arxiv_cr](https://arxiv.org/abs/2606.05714v1)
- **Dense Contexts Are Hard Contexts: Lexical Density Limits Effective Context in LLMs** — [arxiv_cl](https://arxiv.org/abs/2606.06203v1)
- **SkillComposer: Learning to Evolve Agent Skills for Specification and Generalization** — [arxiv_cl](https://arxiv.org/abs/2606.06079v1)
- **Global-Local Monte Carlo Tree Search in Vision-Language Models for Text-to-3D Indoor Scene Generation** — [arxiv_cv](https://arxiv.org/abs/2606.06002v1)
- **Attention-Augmented LSTMs for Automatic Homophonic Ciphertext Decipherment** — [arxiv_cr](https://arxiv.org/abs/2606.05078v1)
- **Robust Ensemble of Selectively Strengthened and Augmented Predictors** — [arxiv_cr](https://arxiv.org/abs/2606.06265v1)
- **PAC-Bayesian Adversarially Robust Generalization for Message Passing Graph Neural Networks: A Sensitivity Analysis** — [arxiv_lg](https://arxiv.org/abs/2606.06293v1)
- **TinyML-Driven Cybersecurity for Autonomous Spacecraft: Latency-Accuracy Analysis for SPARTA RF and Cyber Threat Detection** — [arxiv_cr](https://arxiv.org/abs/2606.05779v1)
- **Beyond Waveform Robustness: Robust Feature-Vocoder Adversarial Attacks on Automatic Speech Recognition** — [arxiv_cr](https://arxiv.org/abs/2606.05678v1)
- **OrderGrad: Optimizing Beyond the Mean with Order-Statistic Policy Gradient Estimation** — [arxiv_cl](https://arxiv.org/abs/2606.06096v1)
- **DisasterBench: A Multimodal Benchmark for UAV-Based Disaster Response in Complex Environments** — [arxiv_cv](https://arxiv.org/abs/2606.06217v1)
- **Discrete-WAM: Unified Discrete Vision-Action Token Editing for World-Policy Learning** — [huggingface_papers](https://arxiv.org/abs/2606.05645)
- **Human Adults and LLMs as Scientists: Who Benefits from Active Exploration?** — [arxiv_cl](https://arxiv.org/abs/2606.06464v1)
- **Latent Reasoning with Normalizing Flows** — [arxiv_cl](https://arxiv.org/abs/2606.06447v1)
- **"Chi nas dal soch el sent de legn" -- Auditing Text Corpora for Lombard** — [arxiv_cl](https://arxiv.org/abs/2606.06349v1)
- **Decomposing Factual Sycophancy in Language Models: How Size and Instruction Tuning Shape Robustness** — [arxiv_cl](https://arxiv.org/abs/2606.06306v1)
- **The Post-GCN Decade Revisited: Curvature-Stratified Evaluation of Relational Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06397v1)
- **Learned Response-Field Inertia Operator for HEC-RAS 2D Water-Surface Elevation Prediction** — [arxiv_lg](https://arxiv.org/abs/2606.06385v1)
- **Maximising the Set-Piece Return: Optimising Football Corner Tactics with Graph Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06353v1)
- **Attack Detection using Time Series Foundation Models** — [arxiv_lg](https://arxiv.org/abs/2606.06347v1)
- **Discrete Causal Representations from Heterogeneous Domains: A Bayesian Approach with Social Survey Applications** — [arxiv_lg](https://arxiv.org/abs/2606.06288v1)
- **Steering LLM Viewpoints through Fabricated Evidence Injection** — [arxiv_cr](https://arxiv.org/abs/2606.06244v1)
- **Benchmarking Open-Source Layout Detection Models for Data Snapshot Extraction from Institutional Documents** — [arxiv_cl](https://arxiv.org/abs/2606.06242v1)
- **Revisiting Lexicon Evaluation in Unsupervised Word Discovery** — [arxiv_cl](https://arxiv.org/abs/2606.06183v1)
- **Learning to Route LLMs from Implicit Cost-Performance Preferences via Meta-Learning** — [arxiv_cl](https://arxiv.org/abs/2606.06178v1)
- **Harnessing Structural Context for Entity Alignment Foundation Models** — [arxiv_cl](https://arxiv.org/abs/2606.06109v1)
- **On Advantage Estimates for Max@K Policy Gradients** — [arxiv_cl](https://arxiv.org/abs/2606.06080v1)
- **MDP-GRPO: Stabilized Group Relative Policy Optimization for Multi-Constraint Instruction Following** — [arxiv_cl](https://arxiv.org/abs/2606.06058v1)
- **NAVIRA: Decoupled Stochastic Remasking for Masked Diffusion Language Models** — [arxiv_cl](https://arxiv.org/abs/2606.06031v1)
- **RedditPersona: A Modular Framework for Community-Conditioned LLM Adaptation from Reddit** — [arxiv_cl](https://arxiv.org/abs/2606.06027v1)
- **Design a Reliable LLM-Integrated Interface for Mortality Forecasting** — [arxiv_lg](https://arxiv.org/abs/2606.06235v1)
- **Computation-Aware Event-to-Frame Reconstruction via Selective Attention** — [arxiv_cv](https://arxiv.org/abs/2606.06142v1)
- **Where, What, Why, and Importance: Structured Defect Grounding for Text-to-Image Feedback** — [arxiv_cv](https://arxiv.org/abs/2606.06113v1)
- **ReCache: Learning Budget-Aware Caching Schedules for Diffusion Models via REINFORCE** — [arxiv_cv](https://arxiv.org/abs/2606.06060v1)
- **Texture-preserving implicit neural representation for Cone beam CT truncated reconstruction** — [arxiv_cv](https://arxiv.org/abs/2606.06039v1)
- **ReSAGE-PAR: Representational Similarity Assessment for Generative Expansion in Pedestrian Attribute Recognition** — [arxiv_cv](https://arxiv.org/abs/2606.06020v1)
- **TailLoR: Protecting Principal Components in Parameter-Efficient Continual Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06494v1)
- **How abundant are good interpolators?** — [arxiv_lg](https://arxiv.org/abs/2606.06469v1)
- **Event Detection for Parameter-to-KPI Dependency Learning for AI-RAN** — [arxiv_lg](https://arxiv.org/abs/2606.06459v1)
- **Causal Atlases from Entropic Inference: Bayesian Networks beyond Optimal DAGs** — [arxiv_lg](https://arxiv.org/abs/2606.06440v1)
- **Proper Scoring Rules for Right-Censored Survival Data** — [arxiv_lg](https://arxiv.org/abs/2606.06393v1)
- **End-to-End Subgraph Detection with GraphDETR** — [arxiv_lg](https://arxiv.org/abs/2606.06364v1)
- **Function-Space Priors for Bayesian Neural ODEs with Application to Vessel Trajectory Prediction** — [arxiv_lg](https://arxiv.org/abs/2606.06351v1)
- **PAR3D: A Unified 3D-MLLM with Part-Aware Representation for Scene Understanding** — [arxiv_cv](https://arxiv.org/abs/2606.06485v1)
- **Complexity-Balanced Diffusion Splitting** — [arxiv_cv](https://arxiv.org/abs/2606.06477v1)
- **Visual Commonsense Driven Knowledge Refinements for Scene Graph Generation** — [arxiv_cv](https://arxiv.org/abs/2606.06369v1)
- **Comparison of Deep Learning Frameworks For Rice Disease Mapping From UAV Multispectral Imaging** — [arxiv_cv](https://arxiv.org/abs/2606.06359v1)
- **Learning Geometric Representations from Videos for Spatial Intelligent Multimodal Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2606.05833)
- **Dream.exe: Can Video Generation Models Dream Executable Robot Manipulation?** — [huggingface_papers](https://arxiv.org/abs/2606.04811)
- **Towards Truly Multilingual ASR: Generalizing Code-Switching ASR to Unseen Language Pairs** — [huggingface_papers](https://arxiv.org/abs/2606.05846)
- **World-Language-Action Model for Unified World Modeling, Language Reasoning, and Action Synthesis** — [huggingface_papers](https://arxiv.org/abs/2606.05979)
- **Imagine Before You Predict: Interleaved Latent Visual Reasoning for Video Event Prediction** — [huggingface_papers](https://arxiv.org/abs/2606.05769)
- **The Download: AI hacking beyond Mythos, and chatbots’ impact on our brains** — [mit_tech_review](https://www.technologyreview.com/2026/06/05/1138452/the-download-ai-hacking-mythos-chatbots-brain-impacts/)
- **The Meta hack shows there’s more to AI security than Mythos** — [mit_tech_review](https://www.technologyreview.com/2026/06/05/1138437/the-meta-hack-shows-theres-more-to-ai-security-than-mythos/)
- **zhihumomo/bashagt** — [github](https://github.com/zhihumomo/bashagt)
- **Startup Battlefield 200 applications officially close in 3 days** — [techcrunch_ai](https://techcrunch.com/2026/06/05/startup-battlefield-200-applications-officially-close-in-3-days/)
- **The most interesting startups right now want to get you off your phone** — [techcrunch_ai](https://techcrunch.com/video/the-most-interesting-startups-right-now-want-to-get-you-off-your-phone/)
- **This is your laptop… on AI** — [theverge_ai](https://www.theverge.com/podcast/944058/ai-laptop-nvidia-build-gemini-spark-vergecast)
- **New York lawmakers pass one-year ban on new data centers** — [theverge_ai](https://www.theverge.com/policy/944041/new-york-data-center-moratorium)
- **The ‘together tech’ wave might be the most intriguing startup bet of 2026** — [techcrunch_ai](https://techcrunch.com/podcast/the-together-tech-wave-might-be-the-most-intriguing-startup-bet-of-2026/)
- **This AI startup says it can tell if a script will make a hit film** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/943531/ai-script-quilty-simon-horsman-daniel-wood)
- **Are AI chatbots making us lose control of our brains?** — [mit_tech_review](https://www.technologyreview.com/2026/06/05/1138427/are-ai-chatbots-making-us-lose-control-of-our-brains/)
- **Mira Murati steps back into the spotlight, carefully** — [techcrunch_ai](https://techcrunch.com/2026/06/04/mira-murati-steps-back-into-the-spotlight-carefully/)
- **ferdinandobons/AWSBedrockAgentCoreSkill** — [github](https://github.com/ferdinandobons/AWSBedrockAgentCoreSkill)
- **rextanka/zero-cost-cline** — [github](https://github.com/rextanka/zero-cost-cline)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **zaydmulani09/mnemo** — [github](https://github.com/zaydmulani09/mnemo)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **Google will pay SpaceX $920M per month for compute** — [techcrunch_ai](https://techcrunch.com/2026/06/05/google-will-pay-spacex-920m-per-month-for-compute/)
- **The token bill comes due: Inside the industry scramble to manage AI’s runaway costs** — [techcrunch_ai](https://techcrunch.com/2026/06/05/the-token-bill-comes-due-inside-the-industry-scramble-to-manage-ais-runaway-costs/)
- **AirTrunk commits $30B to build 5GW of AI data centers in India** — [techcrunch_ai](https://techcrunch.com/2026/06/05/airtrunk-commits-30b-to-build-5gw-of-ai-data-centers-in-india/)
- **The latest AI news we announced in May 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/google-ai-updates-may-2026/)
- **erthorpabar/pabar_agent_runtime** — [github](https://github.com/erthorpabar/pabar_agent_runtime)
- **relaydeck/relaydeck** — [github](https://github.com/relaydeck/relaydeck)
- **PentesterFlow/agent** — [github](https://github.com/PentesterFlow/agent)
- **chaitanyagiri/munder-difflin** — [github](https://github.com/chaitanyagiri/munder-difflin)
- **attentiontech/gtm-superintelligence** — [github](https://github.com/attentiontech/gtm-superintelligence)
- **xiaolai/no-one-did-it** — [github](https://github.com/xiaolai/no-one-did-it)
- **weicj/vLLM-2080Ti-Definitive** — [github](https://github.com/weicj/vLLM-2080Ti-Definitive)
- **anvia-hq/lexa** — [github](https://github.com/anvia-hq/lexa)
- **Guo-chunyu/Chaning.G-s-Lrlab** — [github](https://github.com/Guo-chunyu/Chaning.G-s-Lrlab)
- **Forlives/21-day-self-interview** — [github](https://github.com/Forlives/21-day-self-interview)
- **razr001/align-dev** — [github](https://github.com/razr001/align-dev)
- **krispuckett/SwiftUIShaders** — [github](https://github.com/krispuckett/SwiftUIShaders)
- **Reloops-App/reloops** — [github](https://github.com/Reloops-App/reloops)
- **felixrieseberg/relic** — [github](https://github.com/felixrieseberg/relic)
- **有人靠CPU把AI算力密度卷到了新高度** — [qbitai](https://www.qbitai.com/2026/06/431045.html)
- **华为云发布Agentic AI系列新品 打造智能时代“硅基黑土地”** — [qbitai](https://www.qbitai.com/2026/06/431027.html)
- **微信AI对手机厂商打开一道窄门｜焦点分析** — [36kr](https://36kr.com/p/3839575253993985?f=rss)
- **智源&清华合作成果登上Science：脑科学多模态基础模型Brainμ支撑揭示“记忆-睡眠”调控的神经机制** — [qbitai](https://www.qbitai.com/2026/06/431033.html)
- **WPS笔记正式发布：AI贯穿记录、整理与复用全过程** — [qbitai](https://www.qbitai.com/2026/06/431014.html)
- **从超级个体到超级团队，腾讯云发布WorkBuddy企业版** — [qbitai](https://www.qbitai.com/2026/06/430758.html)
- **100亿砸向人形，不如先让10万台机器狗走进家庭** — [qbitai](https://www.qbitai.com/2026/06/429968.html)
- **活久见！奥特曼Dario哈萨比斯同仇敌忾：DNA得查了** — [qbitai](https://www.qbitai.com/2026/06/429711.html)
- **全球首个机器人训练楼盘开盘：30万套中国住宅，机器人拎包入住** — [qbitai](https://www.qbitai.com/2026/06/429349.html)
- **国星宇航与腾讯云签署“星算”计划战略合作协议，携手领航AI云服务新生态** — [qbitai](https://www.qbitai.com/2026/06/430757.html)
- **B站宣布启动AI创造公开赛 打造中国版Build in Public** — [qbitai](https://www.qbitai.com/2026/06/430752.html)
- **氪星晚报 ｜日本或通过抛售美债，为创纪录规模的日元汇市干预筹资；俞浩内部发文：未来将继续心无旁骛做实业** — [36kr](https://36kr.com/p/3840267945969929?f=rss)
- **Token大战中，华为云选择了第三条路｜最前线** — [36kr](https://36kr.com/p/3840016255126016?f=rss)
- **麦捷科技：Bias-Tee模块产品收入占公司营业总收入比例较小** — [36kr](https://36kr.com/newsflashes/3840228196256263?f=rss)
- **高盛预计xAI营收5年增长约100倍** — [36kr](https://36kr.com/newsflashes/3840204240931080?f=rss)
- **SpaceX IPO已获得2倍认购资金** — [36kr](https://36kr.com/newsflashes/3841030859081984?f=rss)
- **美股三大指数收盘集体下跌，纳指跌超4%** — [36kr](https://36kr.com/newsflashes/3841026664204546?f=rss)
- **9点1氪｜豆包推出付费后月活减少610万；Anthropic呼吁全球放缓AI开发，警告AI“自我改进”风险；罗永浩卸任锤子软件公司执行董事** — [36kr](https://36kr.com/p/3840996342073604?f=rss)
- **可灵AI两周年：全球用户突破1亿，企业客户近5万家** — [36kr](https://36kr.com/newsflashes/3840249278793985?f=rss)
- **加拿大出台国家人工智能战略** — [36kr](https://36kr.com/newsflashes/3840230258936065?f=rss)
- **3连板中重科技：不涉及机器人及零配件的生产制造** — [36kr](https://36kr.com/newsflashes/3840220955445761?f=rss)
- **中国入境游距离「世界第一」还有多远？** — [36kr](https://36kr.com/p/3840001908361472?f=rss)
- **探店13家，理想/蔚来/问界如何征服50万客群？** — [36kr](https://36kr.com/p/3839803361741313?f=rss)
- **SpaceX与谷歌达成每月9.2亿美元的云服务协议** — [36kr](https://36kr.com/newsflashes/3841028145236227?f=rss)
- **热门中概股美股盘前多数下跌，百度跌超4%** — [36kr](https://36kr.com/newsflashes/3840284182268417?f=rss)
- **美股大型科技股盘前涨跌不一，英特尔跌超3%** — [36kr](https://36kr.com/newsflashes/3840277452654853?f=rss)