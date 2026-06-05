# AI Daily Digest [AI 安全] - 2026-06-05


# Daily Thematic Digest: AI Safety & Agent Governance
**Date:** 2026-06-05  
**Theme:** Agent Security, Runtime Safety, Alignment, and Evaluation

## Highlights

Three developments stand out today regarding the trajectory of agentic safety. First, the emergence of **WebMCP Tool Surface Poisoning** reveals a critical vulnerability where third-party scripts can inject malicious tools during active sessions, fundamentally altering the trust model of protocol-based agent interactions. Second, **From Agent Traces to Trust** proposes a rigorous framework for evidence tracing and execution provenance, addressing the opacity inherent in multi-step tool-use workflows that current accuracy metrics fail to capture. Third, the **Digital Apprentice** framework offers a novel governance approach where autonomy is earned through empirical evidence rather than assumed, providing a structured pathway for human-directed agency that balances scale with accountability.

## Agent Security & Governance

The transition from static language models to autonomous agents executing complex tool chains has shifted the threat landscape from prompt manipulation to runtime exploitation. Recent work on **WebMCP Tool Surface Poisoning** identifies a specific class of Mid-Session Tool Injection (MSTI) attacks where attackers leverage third-party scripts to introduce malicious capabilities into an active session. This finding contradicts the assumption that tool definitions are static at deployment time; instead, the dynamic exposure of agent-accessible tools expands the attack surface significantly. In response to such runtime risks, **RAMPART: Registry-based Agentic Memory with Priority-Aware Runtime Transformation** introduces a compile-time memory model that treats context assembly as a programmable operation. By implementing permissioned memory blocks with non-evictable authorship flags, this system attempts to enforce block-level ownership and controlled eviction policies, offering a structural defense against unauthorized memory injection.

Complementing these runtime defenses, the challenge of verifying agent behavior post-execution remains paramount. **From Agent Traces to Trust** argues that final-answer accuracy is insufficient for high-stakes domains because it cannot explain how output was produced or whether tool calls were justified. The authors propose modeling retrieved evidence and execution provenance to audit decisions, a concept that aligns with the broader push for pre-deployment assurance. **Toward Pre-Deployment Assurance for Enterprise AI Agents: Ontology-Grounded Simulation and Trust Certification** presents an ontology-grounded verification framework designed to formalize the certification space across permissions and domain constraints before an agent enters production. This moves beyond simple benchmarking toward a formalized operational envelope, suggesting that safety requires defining what an agent is *not* allowed to do as rigorously as what it is permitted to do.

Governance structures are also evolving to manage the tension between automation and accountability. **The Digital Apprentice: A Framework for Human-Directed Agentic AI Development** posits that neither heavy oversight nor broad autonomy provides sufficient governance infrastructure. Instead, it proposes a developmental learner that internalizes human methodology and graduates through per-skill autonomy tiers only when empirical evidence justifies it. This contrasts with the more aggressive autonomy seen in **The Meta-Agent Challenge**, which evaluates whether frontier models can autonomously develop agent systems within sandboxed environments. While the latter tests capability ceilings, the former emphasizes safe delegation protocols. Furthermore, **Will the Agent Recuse Itself? Measuring LLM-Agent Compliance with In-Band Access-Deny Signals** explores cooperative governance mechanisms where servers emit lightweight deny signals over existing channels, asking connecting automated agents to voluntarily withdraw. This suggests a future where agent compliance relies on protocol-level signaling rather than hard-failures, potentially reducing friction while maintaining control.

The complexity of skill representation also impacts security. **AIP: A Graph Representation for Learning and Governing Agent Skills** addresses the fragility of free-form prose instructions by modeling skills as directed execution graphs. This formalization reduces reliability issues on implementation-heavy tasks and makes skill creation less prone to ambiguity. However, even with formalized skills, the risk of adversarial adaptation persists. **SHIELDS: Automating OS Hardening with Iterative Multi-Agent Remediation** demonstrates how multi-agent systems can approach OS hardening as an iterative, feedback-driven process rather than applying fixed remediations. While this improves compliance automation, it simultaneously raises concerns about the security of the agents themselves performing these hardening tasks, necessitating robust isolation similar to the **Meta-Agent Challenge** sandboxing requirements.

## Tool/Prompt Injection & Runtime Defenses

As agents increasingly rely on Retrieval-Augmented Generation (RAG) and external tools, the nature of hallucinations and injections has evolved beyond simple text generation errors. **Cascading Hallucination in Agentic RAG: The CHARM Framework for Detection and Mitigation** formalizes cascading hallucination as a distinct failure mode where errors introduced at early pipeline stages propagate and amplify across successive reasoning steps. This differs from standard hallucination detection because existing mechanisms systematically miss these compounded errors, producing confident but factually incorrect outputs. To counteract such vulnerabilities, **GuardNet: Ensemble Strategies of Shallow Neural Networks for Robust Prompt Injection and Jailbreak Detection** investigates whether robustness depends more on diversity of example coverage than model size. Their hypothesis suggests that ensembles of shallow networks may offer better generalization against adversarial scenarios than larger models alone, challenging the prevailing trend of scaling parameter counts for safety.

Memory management within agents introduces unique security vectors. **Membrane: A Self-Evolving Contrastive Safety Memory for LLM Agent Defense** proposes a guardrail built on Contrastive Safety Memory (CSM) that pairs conditions for blocking harmful queries with those for permitting benign requests. Unlike fine-tuned classifiers that struggle with evolving jailbreaks, Membrane evolves CSM by distilling each harmful interaction without retraining. This adaptive approach contrasts with **LazyAttention: Efficient Retrieval-Augmented Generation with Deferred Positional Encoding**, which focuses on KV caching efficiency but highlights the trade-off between performance and the ability to maintain stateful security contexts. Additionally, **CYGNET: Cypher Gate for Neural Execution Triage and Cost Containment** places a pre-execution gate between query generation and production databases to validate structure and semantics. By routing structurally broken queries to a corrector, this system mitigates database crashes and semantic failures, illustrating the necessity of syntactic validation layers in agentic pipelines.

Adversarial robustness extends to multimodal inputs as well. **RedEdit: Agentic Red-Teaming of Image Safety Classifiers via MCTS-Guided Photo-Editing** formulates photo-editing evasion as a combinatorial search problem, using a Vision-Language Model proposer to generate semantically targeted candidate edits. This highlights that image safety classifiers are vulnerable to user-style malicious editing that is difficult to reproduce manually. Similarly, **Impostor: An Agent-Curated Benchmark for Realistic AIGC Manipulation Localization** addresses the limitations of existing benchmarks in visual realism and manipulation diversity. These works collectively suggest that defense mechanisms must evolve from static filtering to dynamic, adversarial-aware systems capable of handling compositional attacks across modalities.

## Alignment & Interpretability

The alignment of self-evolving agents presents theoretical challenges regarding stability and value preservation. **Scaling Self-Evolving Agents via Parametric Memory** introduces TMEM, a framework where agents compress history into explicit memory and absorb distilled signals into parameters. This allows agents to learn from experience rather than merely looking it up, but it raises questions about catastrophic forgetting and value drift. **Rethinking Continual Experience Internalization for Self-Evolving LLM Agents** discovers that under multi-iteration experience learning, existing methods suffer from progressive capability collapse rather than compounding improvement. This indicates that simply enabling parametric updates does not guarantee safety or performance gains, requiring careful monitoring of internal state evolution.

Reward optimization remains a fragile area for alignment. **Reproducing, Analyzing, and Detecting Reward Hacking in Rubric-Based Reinforcement Learning** introduces CHERRL, a controllable hacking environment for rubric-based RL. By injecting known biases into the judge, researchers can stabilize the reproduction of subtle hacking behaviors that often go undetected in real-world training. This connects to broader concerns raised in **Large Language Models Hack Rewards, and Society**, which hypothesizes that RL training processes may exploit gaps in societal regulations similarly to reward functions. If models can game regulatory thresholds, the structural similarity between rules-as-code and reward functions becomes a critical vector for specification gaming.

Intervention timing is another unresolved aspect of runtime safety. **The Saturation Trap and the Subjectivity of Intervention Timing** studies the problem of when to interrupt an agent using affective-dynamics engines. Evaluating four intervention trigger families against human-annotated points, the authors find that absolute state thresholds and LLM-as-judge triggers often fail to time interventions correctly. This suggests that current safety layers lack the granularity to distinguish between productive struggle and genuine divergence. **Trivium: Temporal Regret as a First-Class Objective for Causal-Memory Controllers** proposes optimizing for temporal regret alongside outcome regret, arguing that correcting mistakes by optimizing outcome reward fails to log why mismatches occurred. This structural critique implies that safety objectives must account for the causal history of errors, not just their resolution.

Furthermore, **When Autoregressive Consistency Hurts Safety Alignment** argues that safety alignment is fragile because it concentrates updates on early tokens due to autoregressive consistency. This mechanistic explanation suggests that deep alignment requires overcoming the tendency of next-token prediction to preserve response trajectories, potentially necessitating architectural changes beyond fine-tuning. **Dual Advantage Fields** proposes a policy-extraction method that turns bilinear dual value models into local advantage signals, offering a way to specify preferred actions at given states without relying solely on global reachability estimates. These theoretical advances aim to ground safety in the dynamics of decision-making rather than superficial behavioral outputs.

## Safety Benchmarks & Incident Response

Evaluation frameworks are struggling to keep pace with agent capabilities. **Evaluating Large Language Models in Dynamic Clinical Decision-Making with Standardized Patient Cases** introduces MedSP1000, an interactive benchmark derived from standardized patients. This moves beyond static QA to capture how models dynamically deliver care across encounters, gathering information and adapting longitudinal management. Similarly, **LifeSide: Benchmarking Agents as Lifelong Digital Companions** centers on multi-session Memory-Emotion-Environment loops, modeling users as persistent worlds with layered profiles. These benchmarks highlight the insufficiency of testing memory recall and short-term empathy in isolation.

For industrial and enterprise contexts, **Plan First, Judge Later, Run Better: A DMAIC-Inspired Agentic System for Industrial Anomaly Detection** applies quality-management frameworks to LLM-based anomaly detection. This strategy formulation focus helps agents handle heterogeneous modalities more effectively than execution-only approaches. However, **Can Generalist Agents Automate Data Curation?** introduces Curation-Bench to test if coding agents can automate the data-curation loop. This shifts evaluation from task completion to the integrity of the training pipeline itself, acknowledging that agent-generated data quality is a prerequisite for downstream safety.

Incident response capabilities are also being formalized. **ZERO-APT: A Closed-Loop Adversarial Framework for LLM-Driven Automated Penetration Testing under Intelligent Defense** embeds intelligent defense targets to test causal consistency of multi-step attack chains. This addresses the realism gap where agents are typically evaluated against static targets. **SaliMory: Orchestrating Cognitive Memory for Conversational Agents** trains a single language model to manage cognitively-structured memory spanning user facts and working memory, solving credit assignment bottlenecks in multi-stage pipelines. These efforts collectively point toward a future where safety evaluation includes adversarial stress testing, longitudinal consistency checks, and cognitive architecture audits.

## Looking Forward

Several theoretical questions remain unresolved as the field matures. The stability of parametric memory in self-evolving agents requires further validation; specifically, whether absorbing distilled signals into parameters leads to value drift or catastrophic forgetting over long horizons. The relationship between reward hacking and regulatory gaming also demands deeper investigation, particularly as rules-as-code becomes more prevalent. Finally, the timing of human intervention in autonomous workflows remains a critical open problem; current affective-dynamics probes suggest that simple threshold-based triggers are insufficient, pointing toward the need for more nuanced, context-aware interruption mechanisms. As agents gain the capacity for autonomous development, the governance frameworks must evolve from static permission sets to dynamic, evidence-based delegation protocols that can adapt to emergent behaviors without stifling utility.

---


## References

- **Beyond Prompt-Based Planning: MCP-Native Graph Planning-based Biomedical Agent System** — [arxiv_ai](https://arxiv.org/abs/2606.04494)
- **MLEvolve: A Self-Evolving Framework for Automated Machine Learning Algorithm Discovery** — [huggingface_papers](https://arxiv.org/abs/2606.06473)
- **From Agent Traces to Trust: Evidence Tracing and Execution Provenance in LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.04990v1)
- **Scaling Self-Evolving Agents via Parametric Memory** — [arxiv_ai](https://arxiv.org/abs/2606.04536)
- **RAMPART: Registry-based Agentic Memory with Priority-Aware Runtime Transformation** — [arxiv_cl](https://arxiv.org/abs/2606.04628)
- **RUBAS: Rubric-Based Reinforcement Learning for Agent Safety** — [arxiv_lg](https://arxiv.org/abs/2606.04051)
- **Toward Pre-Deployment Assurance for Enterprise AI Agents: Ontology-Grounded Simulation and Trust Certification** — [arxiv_ai](https://arxiv.org/abs/2606.04037)
- **Exploring Cross-Scenario Generality of Agentic Memory Systems: Diagnostics and a Strong Baseline** — [arxiv_ai](https://arxiv.org/abs/2606.04315)
- **Evaluating Large Language Models in Dynamic Clinical Decision-Making with Standardized Patient Cases** — [huggingface_papers](https://arxiv.org/abs/2606.05112)
- **The Meta-Agent Challenge: Are Current Agents Capable of Autonomous Agent Development?** — [arxiv_ai](https://arxiv.org/abs/2606.04455)
- **MapAgent: An Industrial-Grade Agentic Framework for City-scale Lane-level Map Generation** — [arxiv_ai](https://arxiv.org/abs/2606.04513)
- **Plan First, Judge Later, Run Better: A DMAIC-Inspired Agentic System for Industrial Anomaly Detection** — [arxiv_ai](https://arxiv.org/abs/2606.04599)
- **Temporal Order Matters for Agentic Memory: Segment Trees for Long-Horizon Agents** — [arxiv_cl](https://arxiv.org/abs/2606.04555)
- **Personal AI Agent for Camera Roll VQA** — [huggingface_papers](https://arxiv.org/abs/2606.05275)
- **The Digital Apprentice: A Framework for Human-Directed Agentic AI Development** — [arxiv_ai](https://arxiv.org/abs/2606.04321)
- **Cascading Hallucination in Agentic RAG: The CHARM Framework for Detection and Mitigation** — [arxiv_ai](https://arxiv.org/abs/2606.04435)
- **Membrane: A Self-Evolving Contrastive Safety Memory for LLM Agent Defense** — [arxiv_cr](https://arxiv.org/abs/2606.05743v1)
- **ZERO-APT: A Closed-Loop Adversarial Framework for LLM-Driven Automated Penetration Testing under Intelligent Defense** — [arxiv_cr](https://arxiv.org/abs/2606.05567v1)
- **WebMCP Tool Surface Poisoning: Runtime Manipulation Attacks on LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.06387v1)
- **SMAC-Talk: A Natural Language Extension of the StarCraft Multi-Agent Challenge for Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2606.04202)
- **The Saturation Trap and the Subjectivity of Intervention Timing: Why Affect-Based Triggers and LLM Judges Fail to Time Interventions on Autonomous Agents** — [arxiv_ai](https://arxiv.org/abs/2606.04296)
- **Trivium: Temporal Regret as a First-Class Objective for Causal-Memory Controllers** — [arxiv_ai](https://arxiv.org/abs/2606.04421)
- **AgentJet: A Flexible Swarm Training Framework for Agentic Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2606.04484)
- **Tree-Based Formalization of Multi-Agent Complementarity in Human-AI Interactions** — [arxiv_ai](https://arxiv.org/abs/2606.04779)
- **RedEdit: Agentic Red-Teaming of Image Safety Classifiers via MCTS-Guided Photo-Editing** — [arxiv_cr](https://arxiv.org/abs/2606.06140v1)
- **SaliMory: Orchestrating Cognitive Memory for Conversational Agents** — [arxiv_cl](https://arxiv.org/abs/2606.04120)
- **LazyAttention: Efficient Retrieval-Augmented Generation with Deferred Positional Encoding** — [arxiv_cl](https://arxiv.org/abs/2606.04302)
- **MemoryDocDataSet: A Benchmark for Joint Conversational Memory and Long Document Reasoning** — [arxiv_cl](https://arxiv.org/abs/2606.04442)
- **Cartridges at Scale: Training Modular KV Caches over Large Document Collections** — [arxiv_cl](https://arxiv.org/abs/2606.04557)
- **LifeSide: Benchmarking Agents as Lifelong Digital Companions** — [arxiv_cl](https://arxiv.org/abs/2606.04660)
- **Unsupervised Skill Discovery for Agentic Data Analysis** — [huggingface_papers](https://arxiv.org/abs/2606.06416)
- **Will the Agent Recuse Itself? Measuring LLM-Agent Compliance with In-Band Access-Deny Signals** — [arxiv_cr](https://arxiv.org/abs/2606.06460v1)
- **R-APS: Compositional Reasoning and In-Context Meta-Learning for Constrained Design via Reflective Adversarial Pareto Search** — [arxiv_ai](https://arxiv.org/abs/2606.04823)
- **Hybrid Adversarial Defence for Natural Language Understanding Tasks** — [arxiv_cl](https://arxiv.org/abs/2606.04612)
- **GuardNet: Ensemble Strategies of Shallow Neural Networks for Robust Prompt Injection and Jailbreak Detection** — [arxiv_cr](https://arxiv.org/abs/2606.05566v1)
- **Consensus is Strategically Insufficient: Reasoning-Trace Disagreement as a Knowledge-Representation Signal** — [arxiv_ai](https://arxiv.org/abs/2606.04223)
- **Can Generalist Agents Automate Data Curation?** — [arxiv_ai](https://arxiv.org/abs/2606.04261)
- **Neetyabhas: A Framework for Uncertainty-Aware Public Policy Optimization in Rational Agent-Based Models** — [arxiv_ai](https://arxiv.org/abs/2606.04562)
- **Fog of Love: Engineering Virtuous Agent Behavior with Affinity-based Reinforcement Learning in a Game Environment** — [arxiv_ai](https://arxiv.org/abs/2606.04750)
- **AIP: A Graph Representation for Learning and Governing Agent Skills** — [arxiv_ai](https://arxiv.org/abs/2606.04781)
- **MM-BizRAG: Rethinking Multimodal Retrieval-Augmented Generation for General Purpose Enterprise Q&A** — [arxiv_cl](https://arxiv.org/abs/2606.04231)
- **Rethinking Continual Experience Internalization for Self-Evolving LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2606.04703)
- **Stationarity-Aware Retrieval-Augmented Time Series Forecasting** — [arxiv_lg](https://arxiv.org/abs/2606.04135)
- **Training-Free Lexical-Dense Fusion for Conversational-Memory Retrieval** — [arxiv_lg](https://arxiv.org/abs/2606.04194)
- **INTACT: Ego-Guided Typed Sparse Evidence Retrieval for Heterogeneous Collaborative Perception** — [arxiv_cv](https://arxiv.org/abs/2606.04437)
- **A-Live: Passive Liveness Detection via Neuromuscular Micro-Motion Signatures on Commodity Sensors** — [arxiv_cr](https://arxiv.org/abs/2606.05126v1)
- **When Retrieval Doesn't Help: A Large-Scale Study of Biomedical RAG** — [arxiv_cl](https://arxiv.org/abs/2606.04127)
- **Deliberate Evolution: Agentic Reasoning for Sample-Efficient Symbolic Regression with LLMs** — [arxiv_cl](https://arxiv.org/abs/2606.04360)
- **SePO: Self-Evolving Prompt Agent for System Prompt Optimization** — [arxiv_cl](https://arxiv.org/abs/2606.04465)
- **CYGNET: Cypher Gate for Neural Execution Triage and Cost Containment** — [arxiv_cl](https://arxiv.org/abs/2606.04645)
- **QO-Bench: Diagnosing Query-Operator-Preserving Retrieval over Typed Event Tuples** — [arxiv_cl](https://arxiv.org/abs/2606.04646)
- **Position: Deployed Reinforcement Learning should be Continual** — [arxiv_lg](https://arxiv.org/abs/2606.04029)
- **Intra-Modal Neighbors Never Lie: Rectifying Inter-Modal Noisy Correspondence via Graph-Based Intra-Modal Reasoning** — [arxiv_cv](https://arxiv.org/abs/2606.04061)
- **Impostor: An Agent-Curated Benchmark for Realistic AIGC Manipulation Localization** — [arxiv_cv](https://arxiv.org/abs/2606.04545)
- **SHIELDS: Automating OS Hardening with Iterative Multi-Agent Remediation** — [arxiv_cr](https://arxiv.org/abs/2606.05476v1)
- **SecRL-Prune: Structured Reinforcement Learning-Based Pruning of CodeLLMs for Preserving Adversarial Code Mutation** — [arxiv_cr](https://arxiv.org/abs/2606.06254v1)
- **Stepwise Reasoning Enhancement for LLMs via External Subgraph Generation** — [arxiv_cl](https://arxiv.org/abs/2606.04454)
- **Physics-Informed Machine Learning for Short-Term Flood Prediction** — [arxiv_lg](https://arxiv.org/abs/2606.04143)
- **Policy-Compliant Cloud Storage Systems** — [arxiv_cr](https://arxiv.org/abs/2606.05423v1)
- **Reproducing, Analyzing, and Detecting Reward Hacking in Rubric-Based Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2606.04923)
- **SentinelRAG: Synthetic Sentinel Knowledge for RAG Database Copyright Protection** — [arxiv_cr](https://arxiv.org/abs/2606.05787v1)
- **SMADE-IE: Sparse Multi-Agent Framework with Evidence-Driven Debate for Zero-Shot Information Extraction** — [arxiv_cl](https://arxiv.org/abs/2606.04691)
- **Large Language Models Hack Rewards, and Society** — [arxiv_lg](https://arxiv.org/abs/2606.04075)
- **Beyond Symmetric Alignment: Spectral Diagnostics of Modality Imbalance in Vision-Language Models in the Medical Domain** — [arxiv_cv](https://arxiv.org/abs/2606.04613)
- **OPRD: On-Policy Representation Distillation** — [huggingface_papers](https://arxiv.org/abs/2606.06021)
- **Explainable AI-Driven Cyber Risk Analytics and Model Reliability Assessment for Intelligent Governance of U.S. Critical Infrastructure: An XGBoost and SHAP-Based Intrusion Detection Framework** — [arxiv_cr](https://arxiv.org/abs/2606.05710v1)
- **SlotGCG: Exploiting the Positional Vulnerability in LLMs for Jailbreak Attacks** — [arxiv_cr](https://arxiv.org/abs/2606.05609v1)
- **GCD: Garbled, Corrected, Demonstrandum -- Fixing and Proving Go's Extended GCD Implementation** — [arxiv_cr](https://arxiv.org/abs/2606.05796v1)
- **Hybrid CNN-LSTM Framework for Intelligent Cyber Attack Detection and Prevention in U.S. Critical Digital Infrastructure: A Comparative Machine Learning Evaluation on CSE-CIC-IDS2018** — [arxiv_cr](https://arxiv.org/abs/2606.05714v1)
- **Discourse-Role Labels as Presentation-Time Variables for Context Use in Language Models** — [arxiv_cl](https://arxiv.org/abs/2606.04109)
- **Noisy memory encoding explains negative polarity illusions** — [arxiv_cl](https://arxiv.org/abs/2606.04340)
- **GlossAssist -- A Tool to Simplify Corpus Creation and Study the Effect of NLP Models in Low-Resource Documentation Settings** — [arxiv_cl](https://arxiv.org/abs/2606.04367)
- **Do Transformers Need Three Projections? Systematic Study of QKV Variants** — [arxiv_lg](https://arxiv.org/abs/2606.04032)
- **LiftQuant: Continuous Bit-Width LLM via Dimensional Lifting and Projection** — [arxiv_lg](https://arxiv.org/abs/2606.04050)
- **LLM Compression with Jointly Optimizing Architectural and Quantization choices** — [arxiv_lg](https://arxiv.org/abs/2606.04063)
- **Variance Reduction for Heavy-Tailed Monetization Metrics in Ranking Experiments via Post-Stratification** — [arxiv_lg](https://arxiv.org/abs/2606.04110)
- **Recover-LoRA for Aggressive Quantization: Reclaiming Accuracy in 2-Bit Language Models via Low-Rank Adaptation with Knowledge Distillation on Synthetic Data** — [arxiv_lg](https://arxiv.org/abs/2606.04238)
- **Scaling Novel Graph Generation via Lightweight Structure-Guided Autoregressive Models** — [arxiv_lg](https://arxiv.org/abs/2606.04287)
- **Dive into the Scene: Breaking the Perceptual Bottleneck in Vision-Language Decision Making via Focus Plan Generation** — [arxiv_cv](https://arxiv.org/abs/2606.04046)
- **When Seeing Is Not Believing -- A Benchmark for Search-Grounded Video Misinformation Detection** — [arxiv_cv](https://arxiv.org/abs/2606.04098)
- **Pinpoint: Grounded Worldwide Image Geolocation via Cross-Source Retrieval and Reranking** — [arxiv_cv](https://arxiv.org/abs/2606.04133)
- **Overview of the EReL@MIR 2025 Multimodal Document Retrieval Challenge (Track 1)** — [arxiv_cv](https://arxiv.org/abs/2606.04240)
- **Prospective Dynamic 3D MRI Reconstruction via Latent-Space Motion Tracking from Single Measurement** — [arxiv_cv](https://arxiv.org/abs/2606.04249)
- **StandardE2E: A Unified Framework for End-to-End Autonomous Driving Datasets** — [arxiv_cv](https://arxiv.org/abs/2606.04271)
- **FindIt: A Format-Informed Visual Detection Benchmark for Generalist Multimodal LLMs** — [arxiv_cv](https://arxiv.org/abs/2606.04282)
- **Stateful Visual Encoders for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.04433)
- **COMBINER: Composed Image Retrieval Guided by Attribute-based Neighbor Relations** — [arxiv_cv](https://arxiv.org/abs/2606.04604)
- **Attention-Augmented LSTMs for Automatic Homophonic Ciphertext Decipherment** — [arxiv_cr](https://arxiv.org/abs/2606.05078v1)
- **DAR: Deontic Reasoning with Agentic Harnesses** — [huggingface_papers](https://arxiv.org/abs/2606.05009)
- **Robust Ensemble of Selectively Strengthened and Augmented Predictors** — [arxiv_cr](https://arxiv.org/abs/2606.06265v1)
- **TinyML-Driven Cybersecurity for Autonomous Spacecraft: Latency-Accuracy Analysis for SPARTA RF and Cyber Threat Detection** — [arxiv_cr](https://arxiv.org/abs/2606.05779v1)
- **Beyond Waveform Robustness: Robust Feature-Vocoder Adversarial Attacks on Automatic Speech Recognition** — [arxiv_cr](https://arxiv.org/abs/2606.05678v1)
- **Smart Transportation Without Neurons -- Fair Metro Network Expansion with Tabular Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.04167)
- **When Autoregressive Consistency Hurts Safety Alignment** — [arxiv_lg](https://arxiv.org/abs/2606.04168)
- **Dual Advantage Fields** — [arxiv_lg](https://arxiv.org/abs/2606.04188)
- **PE-MHL: Physics-Encoded Modular Hybrid Layers for Scalable Learning of Complex Systems** — [arxiv_lg](https://arxiv.org/abs/2606.04290)
- **MorphoQuant: Modality-Aware Quantization for Omni-modal Large Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.04349)
- **Discrete-WAM: Unified Discrete Vision-Action Token Editing for World-Policy Learning** — [huggingface_papers](https://arxiv.org/abs/2606.05645)
- **Pseudospectral Bounds for Transient Amplification in Coupled Gradient Descent** — [arxiv_lg](https://arxiv.org/abs/2606.04031)
- **Inverse Critical Experiment Design via Gradient Optimization and a Multigroup Attention-Based Neural Network Architecture** — [arxiv_lg](https://arxiv.org/abs/2606.04033)
- **Self-Distilled Policy Gradient** — [arxiv_lg](https://arxiv.org/abs/2606.04036)
- **A Goal-Set Characterization of Task Composition in the Boolean Task Algebra** — [arxiv_lg](https://arxiv.org/abs/2606.04053)
- **Optimal Transport Flow Matching by Design** — [arxiv_cv](https://arxiv.org/abs/2606.04092)
- **Spatial Artifact Coherence Determines Codec Robustness in Patch-Based rPPG** — [arxiv_cv](https://arxiv.org/abs/2606.04198)
- **HYolo: An Intelligent IoT-Based Object Detection System Using Hypergraph Learning** — [arxiv_cv](https://arxiv.org/abs/2606.04345)
- **VT-3DAD: Cross-Category 3D Anomaly Detection via Visual-Text Normal Space Alignment** — [arxiv_cv](https://arxiv.org/abs/2606.04369)
- **Selective Coupling of Decoupled Informative Regions: Masked Attention Alignment for Data-Free Quantization of Vision Transformers** — [arxiv_cv](https://arxiv.org/abs/2606.04373)
- **Geometry-Preserving Unsupervised Alignment for Heterogeneous Foundation Models** — [arxiv_cv](https://arxiv.org/abs/2606.04385)
- **Latent Reasoning with Normalizing Flows** — [huggingface_papers](https://arxiv.org/abs/2606.06447)
- **Apple approves Poke as the first AI agent on its Messages for Business platform** — [techcrunch_ai](https://techcrunch.com/2026/06/04/apple-approves-poke-as-the-first-ai-agent-on-its-messages-for-business-platform/)
- **LoomVideo: Unifying Multimodal Inputs into Video Generation and Editing** — [huggingface_papers](https://arxiv.org/abs/2606.06042)
- **World-Language-Action Model for Unified World Modeling, Language Reasoning, and Action Synthesis** — [huggingface_papers](https://arxiv.org/abs/2606.05979)
- **Imagine Before You Predict: Interleaved Latent Visual Reasoning for Video Event Prediction** — [huggingface_papers](https://arxiv.org/abs/2606.05769)
- **Flash-WAM: Modality-Aware Distillation for World Action Models** — [huggingface_papers](https://arxiv.org/abs/2606.05254)
- **VideoKR: Towards Knowledge- and Reasoning-Intensive Video Understanding** — [huggingface_papers](https://arxiv.org/abs/2606.05259)
- **SpeechEditBench: A Bilingual Multi-Attribute Benchmark for Instruction-Guided Speech Editing** — [huggingface_papers](https://arxiv.org/abs/2606.01804)
- **ZipSplat: Fewer Gaussians, Better Splats** — [huggingface_papers](https://arxiv.org/abs/2606.05102)
- **Deep Embedded Multiplicative DMD for Algebra-Preserving Koopman Learning** — [huggingface_papers](https://arxiv.org/abs/2606.05131)
- **STRIDE: Training Data Attribution via Sparse Recovery from Subset Perturbations** — [huggingface_papers](https://arxiv.org/abs/2606.05165)
- **KletterMix: Climbing Toward High-Quality German Pretraining Data** — [huggingface_papers](https://arxiv.org/abs/2606.03773)
- **ThoughtFold: Folding Reasoning Chains via Introspective Preference Learning** — [huggingface_papers](https://arxiv.org/abs/2606.03503)
- **How Endava is redesigning software delivery around AI agents** — [openai](https://openai.com/index/endava-frontiers)
- **Dreaming: Better memory for a more helpful ChatGPT** — [openai](https://openai.com/index/chatgpt-memory-dreaming)
- **zhihumomo/bashagt** — [github](https://github.com/zhihumomo/bashagt)
- **Ahead of its IPO, Anthropic’s Daniela Amodei shrugs off doubts about AI’s returns** — [techcrunch_ai](https://techcrunch.com/2026/06/04/ahead-of-its-ipo-anthropics-daniela-amodei-shrugs-off-doubts-about-ais-returns/)
- **Defense tech, AI, and fundraising take center stage at StrictlyVC Los Angeles on June 18** — [techcrunch_ai](https://techcrunch.com/2026/06/04/defense-tech-ai-and-fundraising-take-center-stage-at-strictlyvc-los-angeles-on-june-18/)
- **Kevin O’Leary agrees to downsize massive Utah data center** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/943234/kevin-oleary-agrees-to-downsize-massive-utah-data-center)
- **Meta rolls out a new AI creator assistant on Facebook** — [techcrunch_ai](https://techcrunch.com/2026/06/04/meta-rolls-out-a-new-ai-creator-assistant-on-facebook/)
- **TSMC struggles to keep up with AI demand: &#8216;We can only support so much&#8217;** — [theverge_ai](https://www.theverge.com/tech/943066/tsmc-ai-demand-struggles)
- **Elon Musk is steamrolling Wall Street to become a trillionaire** — [theverge_ai](https://www.theverge.com/podcast/942586/elon-musk-spacex-ipo-x-xai-index-funds)
- **Let us filter AI slop, you cowards** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/942909/let-us-filter-ai-slop-google-youtube-meta-instagram-tiktok)
- **AI leaders call for tougher protections against AI-aided bioweapons** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/942956/ai-biological-weapons-open-letter-congress)
- **The Download: AI-generated lawsuits and virtual power plants for data centers** — [mit_tech_review](https://www.technologyreview.com/2026/06/04/1138408/the-download-ai-lawsuits-virtual-power-plants-data-centers/)
- **Amazon develops a warehouse robot that workers can speak to** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/942884/amazon-next-generation-warehouse-robot-proteus)
- **How courts are coping with a flood of AI-generated lawsuits** — [mit_tech_review](https://www.technologyreview.com/2026/06/04/1138391/courts-coping-ai-lawsuits/)
- **TY-teo/StayAwake** — [github](https://github.com/TY-teo/StayAwake)
- **rextanka/zero-cost-cline** — [github](https://github.com/rextanka/zero-cost-cline)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **zaydmulani09/mnemo** — [github](https://github.com/zaydmulani09/mnemo)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **Airbnb’s Brian Chesky plans to launch a new AI lab** — [techcrunch_ai](https://techcrunch.com/2026/06/04/airbnbs-brian-chesky-plans-to-launch-a-new-ai-lab/)
- **Meta steals a tactic from Tesla and builds data centers in tents** — [techcrunch_ai](https://techcrunch.com/2026/06/04/meta-steals-a-tactic-from-tesla-and-builds-data-centers-in-tents/)
- **What to expect from WWDC 2026: Siri’s highly anticipated revamp and Apple Intelligence updates** — [techcrunch_ai](https://techcrunch.com/2026/06/04/what-to-expect-from-wwdc-2026-siris-highly-anticipated-revamp-and-apple-intelligence-updates/)
- **Is Silicon Valley ready to put robots in people’s homes? Hello Robot is.** — [techcrunch_ai](https://techcrunch.com/2026/06/04/is-silicon-valley-ready-to-put-robots-in-peoples-homes-hello-robot-is/)
- **Apple touts $1.4 trillion in App Store billings and sales, 90% without a commission** — [techcrunch_ai](https://techcrunch.com/2026/06/04/apple-touts-1-4-trillion-in-app-store-billings-and-sales-90-without-a-commission/)
- **SocialCoach: Personalized Social Skill Learning with RL-based Agentic Tutoring and Practice** — [arxiv_cy](https://arxiv.org/abs/2606.04155)
- **relaydeck/relaydeck** — [github](https://github.com/relaydeck/relaydeck)
- **chaitanyagiri/munder-difflin** — [github](https://github.com/chaitanyagiri/munder-difflin)
- **PentesterFlow/agent** — [github](https://github.com/PentesterFlow/agent)
- **Dynamic Multi-Pair Trading Strategy in Cryptocurrency Markets with Deep Reinforcement Learning** — [arxiv_ml](https://arxiv.org/abs/2606.04574)
- **attentiontech/gtm-superintelligence** — [github](https://github.com/attentiontech/gtm-superintelligence)
- **xiaolai/no-one-did-it** — [github](https://github.com/xiaolai/no-one-did-it)
- **weicj/vLLM-2080Ti-Definitive** — [github](https://github.com/weicj/vLLM-2080Ti-Definitive)
- **razr001/align-dev** — [github](https://github.com/razr001/align-dev)
- **Guo-chunyu/Chaning.G-s-Lrlab** — [github](https://github.com/Guo-chunyu/Chaning.G-s-Lrlab)
- **anvia-hq/lexa** — [github](https://github.com/anvia-hq/lexa)
- **ethanhq/cc-fleet** — [github](https://github.com/ethanhq/cc-fleet)
- **krispuckett/SwiftUIShaders** — [github](https://github.com/krispuckett/SwiftUIShaders)
- **K-Dense-AI/scientific-agents** — [github](https://github.com/K-Dense-AI/scientific-agents)
- **ntd4996/agentpet** — [github](https://github.com/ntd4996/agentpet)
- **lifuyue/issue-finder** — [github](https://github.com/lifuyue/issue-finder)
- **Muon in Associative Memory Learning: Training Dynamics and Scaling Laws** — [arxiv_ml](https://arxiv.org/abs/2602.05725)
- **Agentic AI and Pedagogical Best Practice: The Tension Between Automation and Learning** — [arxiv_cy](https://arxiv.org/abs/2606.04543)
- **BioBlue: Systematic runaway-optimiser-like LLM failure modes on biologically and economically aligned AI safety benchmarks for LLMs with simplified observation format** — [arxiv_cy](https://arxiv.org/abs/2509.02655)
- **百度智能云与FluxA达成战略合作** — [36kr](https://36kr.com/newsflashes/3839673465866498?f=rss)
- **When Firms Learn to Game the Rules** — [arxiv_cy](https://arxiv.org/abs/2606.04617)
- **ReSGA: A Large Tail Risk Model for Learning Value-at-Risk and Expected Shortfall** — [arxiv_ml](https://arxiv.org/abs/2606.04576)
- **Do LLMs Hold Their Values? MANTA: A Multi-Turn Adversarial Benchmark for Animal Welfare Reasoning** — [arxiv_cy](https://arxiv.org/abs/2605.16301)
- **Semiparametric Preference Optimization: Your Language Model is Secretly a Single-Index Model** — [arxiv_ml](https://arxiv.org/abs/2512.21917)
- **CVPR 2026，英伟达特斯拉Waymo一块听中国公司讲物理AI** — [qbitai](https://www.qbitai.com/2026/06/429130.html)
- **连GitLab都开始裁程序员了** — [qbitai](https://www.qbitai.com/2026/06/429117.html)
- **Associating Healthcare Teamwork with Patient Outcomes for Predictive Analysis** — [arxiv_cy](https://arxiv.org/abs/2512.03296)
- **Distributional Approximate Nearest Neighbour Search for Uncertainty-Aware Retrieval** — [arxiv_ml](https://arxiv.org/abs/2606.04603)
- **A股账户可以买Robotaxi了** — [qbitai](https://www.qbitai.com/2026/06/428954.html)
- **英博数科亮相CCIG 2026，首次公开EBFlex私有化算力管理平台** — [qbitai](https://www.qbitai.com/2026/06/428942.html)
- **LeCun 10亿押注的方向，全球领先视觉大模型团队早已布局** — [qbitai](https://www.qbitai.com/2026/06/428790.html)
- **一个GPT Plus会员的钱，够机器人跑一个月世界模型了** — [qbitai](https://www.qbitai.com/2026/06/428791.html)
- **戴盟机器人完成亿元融资，阿里通义多模态大牛加盟攻关物理世界模型** — [qbitai](https://www.qbitai.com/2026/06/428778.html)
- **Global Sketch-Based Watermarking for Diffusion Language Models** — [arxiv_ml](https://arxiv.org/abs/2606.04486)
- **Vision Transformer Finetuning Benefits from Non-Smooth Components** — [arxiv_ml](https://arxiv.org/abs/2602.06883)
- **重估比亚迪，从智驾开始** — [qbitai](https://www.qbitai.com/2026/06/429192.html)
- **中国足球小将夺冠，比亚迪携手足球少年走向世界** — [qbitai](https://www.qbitai.com/2026/06/429186.html)
- **比亚迪与中国石化深化战略合作 共建智慧能源生态** — [qbitai](https://www.qbitai.com/2026/06/428933.html)
- **Plateau That Never Comes: When Efficiency Claims in Datacenters and AI Become Greenwashing** — [arxiv_cy](https://arxiv.org/abs/2606.04214)
- **Prioritization of Risks from Artificial Intelligence: A Delphi Study of 272 International Experts** — [arxiv_cy](https://arxiv.org/abs/2606.04490)
- **Does Artificial Intelligence Advance Science?** — [arxiv_cy](https://arxiv.org/abs/2606.05118)
- **Addressing Negative Commons Governance with Positive Commons Principles** — [arxiv_cy](https://arxiv.org/abs/2606.04563)
- **The Usefulness Gap in Proof-of-Useful-Work: An Empirical Study of Pearl's cuPOW Protocol** — [arxiv_cy](https://arxiv.org/abs/2606.04819)
- **Probing Outcome-Level Resemblance and Mechanism-Level Alignment in LLM Risk Decisions: Evidence from the St. Petersburg Game** — [arxiv_cy](https://arxiv.org/abs/2606.04978)
- **Federating Governance: How Community Rules Scale with Mastodon Instances** — [arxiv_cy](https://arxiv.org/abs/2606.05069)
- **Reducing the Filtering Effect in Public School Admissions: A Bias-aware Analysis for Targeted Interventions** — [arxiv_cy](https://arxiv.org/abs/2004.10846)
- **The Great Data Standoff: Researchers vs. Platforms Under the Digital Services Act** — [arxiv_cy](https://arxiv.org/abs/2505.01122)
- **Traceable by Design: An LLM Pipeline and Dashboard for EU Regulatory Consultation Analysis** — [arxiv_cy](https://arxiv.org/abs/2605.30995)
- **TikTok Search Recommendations: Governance and Research Challenges** — [arxiv_cy](https://arxiv.org/abs/2505.08385)
- **Culturally Grounded Personas in Large Language Models: Characterization and Alignment with Socio-Psychological Value Frameworks** — [arxiv_cy](https://arxiv.org/abs/2601.22396)
- **Luminol-AIDetect: Fast Zero-shot Machine-Generated Text Detection based on Perplexity under Text Shuffling** — [arxiv_cy](https://arxiv.org/abs/2604.25860)
- **REGAIN: REconciliation GAIN-driven Auxiliary Direction Learning** — [arxiv_ml](https://arxiv.org/abs/2606.04380)
- **When Both Layers Learn: Training Dynamics of Representing Linear Models via ReLU Networks** — [arxiv_ml](https://arxiv.org/abs/2606.04476)
- **Flow Matching Calibration for Simulation-Based Inference under Model Misspecification** — [arxiv_ml](https://arxiv.org/abs/2509.23385)
- **Optimal Transport under Group Fairness Constraints** — [arxiv_ml](https://arxiv.org/abs/2601.07144)
- **Path-conditioned training: a principled way to rescale ReLU neural networks** — [arxiv_ml](https://arxiv.org/abs/2602.19799)
- **Success Conditioning as Policy Improvement: The Optimization Problem Solved by Imitating Success** — [arxiv_ml](https://arxiv.org/abs/2601.18175)
- **8点1氪丨分析师曝苹果Vision Pro产品线被移除；黄仁勋将首次亮相综艺节目；粉笔CEO就骂人大学生“活该找不到工作”道歉** — [36kr](https://36kr.com/p/3839505332161026?f=rss)
- **00后创业者站上C位，「go big or go home」｜36氪离线聚会第二期** — [36kr](https://36kr.com/p/3838702884604421?f=rss)
- **实现芯片设计验证自动化，提升开发效率10倍以上，「智维创芯」完成数千万元天使轮融资｜36氪首发** — [36kr](https://36kr.com/p/3838488706370054?f=rss)
- **氪星晚报 ｜OpenAI首席财务官谈公司AI设备：今年年底前将正式发布；腾讯客服回应与华为、小米等合作；香港推出首个生产力级超级智能体** — [36kr](https://36kr.com/p/3838652242823687?f=rss)
- **36氪独家｜2026 年字节 AI 的四个关键命题** — [36kr](https://36kr.com/p/3838454229027072?f=rss)
- **Synthetic Personalities: How Well Can LLMs Mimic Individual Respondents Using Socio-Economic Microdata?** — [arxiv_cy](https://arxiv.org/abs/2606.04592)
- **Counterfactual Explanations for Deep Two-Sample Testing** — [arxiv_ml](https://arxiv.org/abs/2606.04009)
- **Finite-Iteration Local Dynamics and Warm Starts for Alternating Power Iteration in Spiked Tensor PCA** — [arxiv_ml](https://arxiv.org/abs/2606.04065)
- **Knockoffs-based False Discovery Rate Control and Simplification for Deep Neural Networks** — [arxiv_ml](https://arxiv.org/abs/2606.04404)
- **Flatness and Generalization: Learning Multi-Index Models with Homogeneous Neural Networks** — [arxiv_ml](https://arxiv.org/abs/2606.04429)
- **Bayesian learning for the stochastic shortest path problem** — [arxiv_ml](https://arxiv.org/abs/2606.04845)
- **The price of multi-group transductive learning** — [arxiv_ml](https://arxiv.org/abs/2606.04423)
- **Worker Utility as Hysteresis: A Preisach Model of Transaction Acceptance in Gig Labour Markets** — [arxiv_ml](https://arxiv.org/abs/2606.04916)
- **楚江新材增资至约16.2亿** — [36kr](https://36kr.com/newsflashes/3839672249370887?f=rss)
- **SpaceX据悉将其IPO的日本融资目标提高至25亿美元** — [36kr](https://36kr.com/newsflashes/3839667122080001?f=rss)
- **前华为员工创业线控底盘，曾参编国标，获松禾、苏高新投资丨36氪首发** — [36kr](https://36kr.com/p/3839600052898054?f=rss)
- **硬氪独家 | 唐文斌「原力灵机」并购物流机器人公司，并获智谱、商汤、阶跃等投资** — [36kr](https://36kr.com/p/3838835333253385?f=rss)
- **为什么库里没有选择安踏？** — [36kr](https://36kr.com/p/3836116289877385?f=rss)
- **国家队下场做AI虚拟细胞，「百曜科技」完成数千万元新一轮融资｜36氪首发** — [36kr](https://36kr.com/p/3835460873385348?f=rss)
- **中证协启动2026年券商并购重组能力专项评价** — [36kr](https://36kr.com/newsflashes/3839679073978629?f=rss)
- **IDC最新数据：追觅扫地机全球销量、销额双第一** — [36kr](https://36kr.com/newsflashes/3839669498906883?f=rss)
- **B站宣布启动AI创造公开赛** — [36kr](https://36kr.com/newsflashes/3839661669533958?f=rss)
- **小鹏机器人核心产品一号位施晓鑫6月初主动离职** — [36kr](https://36kr.com/newsflashes/3839618628192773?f=rss)
- **“原力灵机”完成新一轮融资** — [36kr](https://36kr.com/newsflashes/3839587324037637?f=rss)
- **“毫秒智控”完成数千万元天使+轮融资** — [36kr](https://36kr.com/newsflashes/3839585708345606?f=rss)