# AI Daily Digest [AI 安全] - 2026-06-13


# Daily Thematic Digest: AI Safety & Agent Governance
**Date:** 2026-06-13  
**Theme:** Agent Security, Runtime Safety, Alignment, and Evaluation

## Highlights

Three critical developments dominate today’s safety discourse, signaling a shift from static model hardening to dynamic system-level governance. First, researchers have identified **Multi-Session Memory Poisoning (MSMP)** as a previously unaddressed vulnerability where adversaries inject crafted memories into persistent RAG agents that steer future responses across user sessions without modifying weights or code (**[SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems]**). Second, a comprehensive **Five-Plane Reference Architecture** has been proposed to extend enterprise security controls beyond data boundaries into the workflow sequences where agents execute actions, acknowledging that risk now resides inside the process rather than at the perimeter (**[A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents]**). Third, empirical studies on hierarchical multi-agent systems reveal that **collusive behaviors** significantly expand the attack surface, necessitating new red-teaming methodologies that target coordinated privilege escalation rather than isolated agent failures (**[MAStrike: Shapley-Guided Collulative Red-Teaming on Multi-Agent Systems]**).

## Agent Security & Governance

The prevailing paradigm of AI safety is undergoing a fundamental restructuring as production agents dissolve traditional data boundaries. Historically, enterprise security governed crossings of protected surfaces—data at rest and in transit—but modern agentic workflows introduce risk into the sequence of individually permitted actions that transform business processes. The authors of **[A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents]** argue that existing policy engines fail to evaluate this regime because they do not account for the transformation of authorized actions into unauthorized outcomes through composition. This architectural gap is exacerbated by the persistence of agent memory. In **[SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems]**, the authors demonstrate that static-corpus defenses like RobustRAG assume a fixed knowledge base, leaving systems vulnerable to fluent enterprise-style injections that accumulate across sessions. Unlike weight-based attacks, MSMP allows an adversary interacting through normal channels to poison the retrieval context for future users, creating a supply-chain-like vulnerability within the agent's own memory store.

To counter these systemic risks, governance must move from heuristic filtering to certified defense and structural analysis. While **[SMSR]** highlights the lack of certification against memory poisoning, **[Beyond Runtime Enforcement: Shield Synthesis as Defensibility Analysis for Adversarial Networks]** argues that shielded reinforcement learning is often misapplied as a runtime constraint when it should instead serve as a design-time analytical instrument. The authors propose using automata-theoretic machinery to extract structural insights about system safety before deployment, suggesting that runtime constraints alone are insufficient for complex networks. This aligns with the findings in **[PolicyGuard: Towards Test-time and Step-level Adversary Defense for Reinforcement Learning Agent]**, which notes that current backdoor defenses for RL agents either require access to internal parameters or operate only at the trajectory level, leaving step-level vulnerabilities exposed.

The complexity of these threats is compounded in multi-agent environments where coordination becomes a vector for compromise. **[MAStrike: Shapley-Guided Collusive Red-Teaming on Multi-Agent Systems]** introduces a methodology to identify which agents are critical targets under coordinated adversarial behaviors, moving beyond heuristic selection of single agents. This is particularly relevant given the findings in **[Smarter Saboteurs, Better Fixers: Scaling & Security in Linear Multi-Agent Workflows]**, which investigate how model scale affects the security of linear workflows. Their experiments reveal a compliance-correction trade-off where larger models may exhibit different resilience patterns against sabotage, challenging the assumption that scaling inherently improves robustness. Furthermore, **[Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval]** warns that even graph-based memory defenses checking record provenance are blind by construction if the structure itself is writable by untrusted principals, fundamentally altering which authenticated facts are selected.

## Tool/Prompt Injection & Runtime Defenses

As agents increasingly rely on external tools and environments, the interface layer has become a primary attack surface. Existing defenses focus on blocking malicious content at inference time, but **[PI-Hunter: Automated Red-Teaming for Exposing and Localizing Prompt Injections]** proposes an automated agentic auditing framework to expose latent prompt injections that propagate through agents. This addresses the visibility gap where developers cannot see how indirect prompt injections emerge through untrusted external sources. The challenge is further complicated by the granularity of tool interactions. **[HyperTool: Beyond Step-Wise Tool Calls for Tool-Augmented Agents]** identifies an execution-granularity mismatch where locally deterministic tool workflows are unfolded into repeated model-visible decisions, consuming context and forcing the model to manage low-level dataflow. By introducing a unified executable MCP-style tool interface, HyperTool aims to reduce the attack surface created by excessive trace exposure.

Runtime enforcement mechanisms are also evolving to handle user corrections and preference compliance. **[Getting Better at Working With You: Compiling User Corrections into Runtime Enforcement for Coding Agents]** introduces TRACE, a pipeline that mines user corrections and compiles them into atomic rules for runtime enforcement. The authors report that existing memory solutions like Mem0 still leave 57.5% of applicable preference checks violated in real-user friction cases, highlighting a significant gap between preference access and compliance. To support long-term operation, **[MemRefine: LLM-Guided Compression for Long-Term Agent Memory]** formulates storage-budgeted memory management, addressing the issue where memory stores grow without bound and degrade retrieval by crowding out useful evidence. This compression task is critical for resource-constrained platforms but introduces its own risks regarding information loss and retrieval accuracy.

Privacy exposure remains a distinct concern within the runtime environment, particularly for mobile and visual agents. **[CAPED: Context-Aware Privacy Exposure Defense for Mobile GUI Agents]** defines incidental visual privacy exposure where screenshots expose contacts, messages, and health cues unrelated to the user's request. The authors note that text anonymization misses many visual and inferential cues, while generic masking removes utility. Similarly, **[OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents]** frames privacy as a property of the entire trajectory rather than a single output, noting that leakage is cumulative and bidirectional. These findings suggest that privacy defenses must be integrated into the harness design rather than applied as post-hoc filters.

## Adversarial Attacks & Robustness

The evaluation of adversarial robustness is shifting from static benchmarks to dynamic, stake-centric assessments. **[Who Pays the Price? Stakeholder-Centric Prompt Injection Benchmarking for Real-world Web Agents]** critiques existing security benchmarks for adopting an attack-centric perspective that overlooks the nuanced distribution of resulting harms. The authors argue that prompt-injection risk is victim-dependent, requiring benchmarks that measure harm distribution rather than just technical feasibility. Complementing this, **[Beyond Attack Success Rate: Examining Trigger Leakage in Vision-Language Agentic Systems]** formalizes the failure of trigger precision as "trigger leakage," arguing that current evaluations capture whether a trigger works but not whether it triggers hidden behaviors only when intended.

Scalability of defenses remains a critical question. **[Smarter Saboteurs, Better Fixers]** found that compliance-correction dynamics change with model scale, suggesting that security properties are not monotonic with capability. In parallel, **[Reinforcement Learning Disrupts Gradient-Based Adversarial Optimization]** investigates whether RL training can disrupt the gradient structure used by attackers, finding that RL-trained classifiers significantly disrupt gradient-based adversarial optimization compared to standard supervised training. This offers a potential pathway for robustness that does not rely solely on input-space defenses. Additionally, **[Categorical Robustness Assessment for Machine Learning based Network Intrusion Detection Systems]** calls for systematic cross-architecture comparisons under controlled attack conditions, noting that practitioners currently lack clear guidance on which models to deploy in adversarial environments.

For autonomous capabilities, the emergence of penetration skills poses a specific red-line risk. **[The Emergence of Autonomous Penetration Capabilities in Large Language Model-Powered AI Systems]** assesses the ability of LLM-powered systems to independently conduct adversarial operations against target servers. This capability represents a core subtask for autonomous cyberattacks, requiring rigorous assessment frameworks similar to those proposed in **[DIG: Oracle-Guided Directed Input Generation for One-Day Vulnerabilities]**, which uses agentic approaches to solve necessary constraints for triggering vulnerabilities more effectively than random mutation.

## Alignment & Interpretability

Alignment efforts are expanding beyond general helpfulness to include domain-specific knowledge orchestration and pluralistic representation. **[Agents-K1: Towards Agent-native Knowledge Orchestration]** introduces a pipeline that converts raw documents into agent-native scientific knowledge graphs, integrating multimodal components to preserve key entities and claim lineages essential for scientific reasoning. This moves beyond reducing papers to abstracts, aiming to support deeper causal understanding. In terms of behavioral alignment, **[PolyAlign: Conditional Human-Distribution Alignment]** proposes matching the human response distribution appropriate to the current interaction context rather than a universal response style, addressing the suppression of natural variation across languages and tasks.

Interpretability and hallucination detection are also seeing methodological advances. **[Layer-Resolved Optimal Transport for Hallucination Detection in NMT and Abstractive Summarization]** extends optimal transport analysis to all six decoder layers, showing that detection is concentrated in early layers while later layers may be anti-predictive for subtler types. For reasoning transparency, **[Switchable Latent Reasoning with On-Policy Reinforcement Learning]** proposes discrete entry and exit anchors to make latent chain-of-thought compatible with standard RL and mechanistic analysis. Finally, **[Neuro-Symbolic Agents for Regulated Process Automation: Challenges and Research Agenda]** argues that symbolic structures embedded in regulated domains should be treated as core architectural components for compliance-by-construction, preventing control-flow violations structurally rather than relying solely on guardrail-based monitoring.

## Safety Benchmarks & Incident Response

Standardization in evaluation remains fragmented, prompting calls for open, agent-agnostic interfaces. **[AgentBeats: Agentifying Agent Assessment for Openness, Standardization, and Reproducibility]** advocates for Agentified Agent Assessment (AAA), where evaluation is performed by judge agents interacting through standardized protocols like A2A for task management and MCP for tool access. This contrasts with conventional benchmarking that defines separate interfaces for participants and judges. To address the static nature of current benchmarks, **[EvoBrowseComp: Benchmarking Search Agents on Evolving Knowledge]** introduces an evolving benchmark of contamination-free complex questions synthesized via live-web traversal, ensuring models must reason rather than recall.

Incident response and situational awareness are being formalized for operational contexts. **[ECYSAP EYE: From Cyber Situational Awareness to Mission-Centric Decision Support for Enhanced Cyberspace Operations]** presents a System-of-Systems architecture centered on mission-focused artefacts like the Recognized Cyberspace Picture and Option Recommendations. This supports the transition from isolated technical alerts to decision support. In the realm of scientific integrity, **[From Passive Generation to Investigation: A Proactive Scientific Peer Review Agent]** explores formulating proactive investigation of suspicious parts of a paper as a Markov Decision Process, enabling agents to perform reviews supported by concrete evidence rather than passive generation.

## Looking Forward

Several theoretical questions remain unresolved as the field matures. The first concerns the provability of memory integrity: while **[SMSR]** certifies against specific poisoning vectors, the broader problem of maintaining selection integrity in mutable graph memories (**[Selection Integrity for LLM Graph Memory]**) requires new cryptographic or logical guarantees that do not rely on trusted hardware. Second, the relationship between model scaling and security resilience needs further empirical validation; **[Smarter Saboteurs, Better Fixers]** suggests non-monotonic behavior, but the mechanisms driving this across different architectures are not yet fully understood. Third, the definition of "harm" in multi-agent systems requires refinement; **[Who Pays the Price?]** highlights the need for stakeholder-centric metrics, but operationalizing these metrics into automated evaluation pipelines remains an engineering challenge.

Finally, the integration of runtime enforcement with design-time analysis requires a unified framework. **[Beyond Runtime Enforcement]** suggests that shield synthesis should inform design, but bridging the gap between temporal-logic specifications and actual agent behavior in dynamic environments is an open problem. As noted in recent regulatory signals, such as the Central Cyberspace Administration opening an "AI Application Chaos Reporting Zone" (reported in **[36kr]**), the pressure for verifiable incident response is increasing. Future work must prioritize the development of audit trails that satisfy both technical defensibility and regulatory requirements, ensuring that the "Five-Plane" architecture proposed for governance can be practically implemented in high-stakes deployments.

---


## References

- **SMSR: Certified Defence Against Runtime Memory Poisoning in Persistent LLM Agent Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12703v1)
- **A Five-Plane Reference Architecture for Runtime Governance of Production AI Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12320v1)
- **PI-Hunter: Automated Red-Teaming for Exposing and Localizing Prompt Injections** — [arxiv_cr](https://arxiv.org/abs/2606.12737v1)
- **Recursive Agent Harnesses** — [arxiv_cl](https://arxiv.org/abs/2606.13643v1)
- **AgentBeats: Agentifying Agent Assessment for Openness, Standardization, and Reproducibility** — [arxiv_ai](https://arxiv.org/abs/2606.13608v1)
- **MemRefine: LLM-Guided Compression for Long-Term Agent Memory** — [arxiv_cl](https://arxiv.org/abs/2606.13177v1)
- **Getting Better at Working With You: Compiling User Corrections into Runtime Enforcement for Coding Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13174v1)
- **HarnessBridge: Learnable Bidirectional Controller for LLM Agent Harness** — [huggingface_papers](https://arxiv.org/abs/2606.12882)
- **Beyond Runtime Enforcement: Shield Synthesis as Defensibility Analysis for Adversarial Networks** — [arxiv_ai](https://arxiv.org/abs/2606.13621v1)
- **Who Pays the Price? Stakeholder-Centric Prompt Injection Benchmarking for Real-world Web Agents** — [arxiv_ai](https://arxiv.org/abs/2606.13385v1)
- **Beyond Attack Success Rate: Examining Trigger Leakage in Vision-Language Agentic Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12586v1)
- **OCELOT: Inference-Leakage Budgets for Privacy-Preserving LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12341v1)
- **EvoArena: Tracking Memory Evolution for Robust LLM Agents in Dynamic Environments** — [arxiv_cl](https://arxiv.org/abs/2606.13681v1)
- **HyperTool: Beyond Step-Wise Tool Calls for Tool-Augmented Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13663v1)
- **SpatialClaw: Rethinking Action Interface for Agentic Spatial Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.13673v1)
- **Agents-K1: Towards Agent-native Knowledge Orchestration** — [arxiv_ai](https://arxiv.org/abs/2606.13669v1)
- **Understanding the Rejection of Fixes Generated by Agentic Pull Requests -- Insights from the AIDev Dataset** — [arxiv_ai](https://arxiv.org/abs/2606.13468v1)
- **Toward Instructions-as-Code: Understanding the Impact of Instruction Files on Agentic Pull Requests** — [arxiv_ai](https://arxiv.org/abs/2606.13449v1)
- **MiniMax Sparse Attention** — [arxiv_ai](https://arxiv.org/abs/2606.13392v1)
- **InterleaveThinker: Reinforcing Agentic Interleaved Generation** — [arxiv_cv](https://arxiv.org/abs/2606.13679v1)
- **DIG: Oracle-Guided Directed Input Generation for One-Day Vulnerabilities** — [arxiv_cr](https://arxiv.org/abs/2606.13037v1)
- **Selection Integrity for LLM Graph Memory: An Accumulability Criterion for Information-Flow-Blind Retrieval** — [arxiv_cr](https://arxiv.org/abs/2606.12290v1)
- **EvoBrowseComp: Benchmarking Search Agents on Evolving Knowledge** — [huggingface_papers](https://arxiv.org/abs/2606.13120)
- **MAStrike: Shapley-Guided Collusive Red-Teaming on Multi-Agent Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12918v1)
- **RogueAI: A Reverse Turing Test for Detecting Licensed AI Deception in Dialogue** — [arxiv_cl](https://arxiv.org/abs/2606.13310v1)
- **Learning to Reason by Analogy via Retrieval-Augmented Reinforcement Fine-Tuning** — [arxiv_ai](https://arxiv.org/abs/2606.13680v1)
- **EurekAgent: Agent Environment Engineering is All You Need For Autonomous Scientific Discovery** — [arxiv_ai](https://arxiv.org/abs/2606.13662v1)
- **Multiagent Protocols with Aggregated Confidence Signals** — [arxiv_ai](https://arxiv.org/abs/2606.13591v1)
- **IterCAD: An Iterative Multimodal Agent for Visually-Grounded CAD Generation and Editing** — [arxiv_ai](https://arxiv.org/abs/2606.13368v1)
- **NavWAM: A Navigation World Action Model for Goal-Conditioned Visual Navigation** — [arxiv_cv](https://arxiv.org/abs/2606.13494v1)
- **PolicyGuard: Towards Test-time and Step-level Adversary Defense for Reinforcement Learning Agent** — [arxiv_cr](https://arxiv.org/abs/2606.12896v1)
- **Smarter Saboteurs, Better Fixers: Scaling & Security in Linear Multi-Agent Workflows** — [arxiv_cr](https://arxiv.org/abs/2606.12709v1)
- **See What I See, Know What I Think: Dense Latent Communication Across Heterogeneous Agents** — [huggingface_papers](https://arxiv.org/abs/2606.13594)
- **WEAVER, Better, Faster, Longer: An Effective World Model for Robotic Manipulation** — [huggingface_papers](https://arxiv.org/abs/2606.13672)
- **WarpGuard: Protected-Site Control-Flow Integrity for CUDA SASS Binaries** — [arxiv_cr](https://arxiv.org/abs/2606.11871v1)
- **SkillCAT: Contrastive Assessment and Topology-Aware Skill Self-Evolution for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2606.13317v1)
- **Mana: Dexterous Manipulation of Articulated Tools** — [arxiv_ai](https://arxiv.org/abs/2606.13677v1)
- **SkMTEB: Slovak Massive Text Embedding Benchmark and Model Adaptation** — [arxiv_ai](https://arxiv.org/abs/2606.13647v1)
- **EpiBench: Verifiable Evaluation of AI Agents on Epigenomics Analysis** — [arxiv_ai](https://arxiv.org/abs/2606.13602v1)
- **Reward Modeling for Multi-Agent Orchestration** — [arxiv_ai](https://arxiv.org/abs/2606.13598v1)
- **ArogyaSutra: A Multi-Agent Framework for Multimodal Medical Reasoning in Indic Languages** — [arxiv_ai](https://arxiv.org/abs/2606.13572v1)
- **Uncertainty-Aware Hybrid Retrieval for Long-Document RAG** — [arxiv_ai](https://arxiv.org/abs/2606.13550v1)
- **Adaptive Turn-Taking for Real-time Multi-Party Voice Agents** — [arxiv_ai](https://arxiv.org/abs/2606.13544v1)
- **Neuro-Symbolic Agents for Regulated Process Automation: Challenges and Research Agenda** — [arxiv_ai](https://arxiv.org/abs/2606.13405v1)
- **TimeLens: On-Device Artifact Recognition with Retrieval-Augmented Question Answering for the Grand Egyptian Museum** — [arxiv_cl](https://arxiv.org/abs/2606.13267v1)
- **ComAct: Reframing Professional Software Manipulation via COM-as-Action Paradigm** — [arxiv_cl](https://arxiv.org/abs/2606.13239v1)
- **MiniPIC: Flexible Position-Independent Caching in <100LOC** — [arxiv_cl](https://arxiv.org/abs/2606.13126v1)
- **CAPED: Context-Aware Privacy Exposure Defense for Mobile GUI Agents** — [arxiv_cr](https://arxiv.org/abs/2606.12666v1)
- **Budget-Constrained Step-Level Diffusion Caching** — [arxiv_cv](https://arxiv.org/abs/2606.13496v1)
- **Categorical Robustness Assessment for Machine Learning based Network Intrusion Detection Systems** — [arxiv_cr](https://arxiv.org/abs/2606.12075v1)
- **When Does Mixing Help? Analyzing Query Embedding Interpolation in Multilingual Dense Retrieval** — [arxiv_cl](https://arxiv.org/abs/2606.13537v1)
- **S-GBT: Smooth Growth Bound Tensor for Certified Robustness Against Word Substitution Attacks in NLP** — [arxiv_cl](https://arxiv.org/abs/2606.13439v1)
- **OR-Action: Multi-Role Video Understanding with Fine-Grained Actions** — [arxiv_cv](https://arxiv.org/abs/2606.13332v1)
- **Aerial Wildfire Suppression Planning with a Hybrid CNN-Cellular Automata Fire Model** — [arxiv_lg](https://arxiv.org/abs/2606.13633v1)
- **Distribution-Agnostic Robust Trajectory Optimization via Chance-Constrained Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.13605v1)
- **GF-DiT: Scheduling Parallelism for Diffusion Transformer Serving** — [arxiv_lg](https://arxiv.org/abs/2606.13501v1)
- **Reinforcement Learning for Neural Model Editing** — [arxiv_lg](https://arxiv.org/abs/2606.13461v1)
- **The Emergence of Autonomous Penetration Capabilities in Large Language Model-Powered AI Systems** — [arxiv_cr](https://arxiv.org/abs/2606.13079v1)
- **Semantic Identification of IoT Devices from Behavioral Primitives** — [arxiv_cr](https://arxiv.org/abs/2606.12793v1)
- **SICI: A Semantic-Pragmatic Complexity Index Reveals Regime Shifts in LLM Stance Detection** — [arxiv_cl](https://arxiv.org/abs/2606.13189v1)
- **SwarmSense-DNN: A Trustworthy and Decentralized Neural Framework for Proactive Anomaly Defense in Consumer IoT** — [arxiv_cr](https://arxiv.org/abs/2606.11803v1)
- **Reinforcement Learning Disrupts Gradient-Based Adversarial Optimization** — [arxiv_cr](https://arxiv.org/abs/2606.12251v1)
- **Toward Trustworthy AI: Multi-Target Adversarial Attacks and Robust Defenses for Continuous Data Summarization** — [arxiv_cr](https://arxiv.org/abs/2606.11804v1)
- **From Passive Generation to Investigation: A Proactive Scientific Peer Review Agent** — [arxiv_cl](https://arxiv.org/abs/2606.13349v1)
- **SPARC: Reliable Spatial Annotations from Robot Demonstrations at Scale** — [arxiv_cv](https://arxiv.org/abs/2606.13497v1)
- **VietFashion: Benchmarking Sketch-Text Composed Image Retrieval for Cultural Outfits** — [arxiv_cv](https://arxiv.org/abs/2606.13427v1)
- **MoVerse: Real-Time Video World Modeling with Panoramic Gaussian Scaffold** — [arxiv_cv](https://arxiv.org/abs/2606.13376v1)
- **NetCause: Counterfactual Learning for Root Cause Analysis in Large-Scale Networks** — [arxiv_lg](https://arxiv.org/abs/2606.13543v1)
- **How Much Memory Do We Need? Adaptive Memory Gate for Neural Operators** — [arxiv_lg](https://arxiv.org/abs/2606.13443v1)
- **Foundations of Practical Quantum Advantage in Quantum-Informed Machine Learning for Predicting Chaos** — [arxiv_lg](https://arxiv.org/abs/2606.13422v1)
- **Quantizing Time-Series Models As Dynamical Systems: Trajectory-Based Quantization Sensitivity Score** — [arxiv_lg](https://arxiv.org/abs/2606.13300v1)
- **Split Tallies: A Discrete Certificate Calculus for Auditing Dynamic Ordered Sets in Constant Memory** — [arxiv_cr](https://arxiv.org/abs/2606.13272v1)
- **LAUKIN: A Multi-jurisdictional Common Law Contract Dataset** — [arxiv_cl](https://arxiv.org/abs/2606.13184v1)
- **HyPE: Category-Aware Hypergraph Encoding with Persistent Edge Embeddings for Persona-Grounded Dialogue** — [arxiv_cl](https://arxiv.org/abs/2606.13142v1)
- **Zero-Shot Captioning for Cultural Heritage: Automated Image Analysis of Traditional Indonesian Clothing** — [arxiv_cv](https://arxiv.org/abs/2606.13275v1)
- **Transformer-Guided Graph Attention for Direct Cardiac Mesh Reconstruction: A Structural Digital Twin Framework** — [arxiv_cv](https://arxiv.org/abs/2606.13188v1)
- **ECYSAP EYE: From Cyber Situational Awareness to Mission-Centric Decision Support for Enhanced Cyberspace Operations** — [arxiv_cr](https://arxiv.org/abs/2606.12354v1)
- **Dual-Domain Equivariant Generative Adversarial Network for Multimodal CT-PET Synthesis** — [arxiv_cv](https://arxiv.org/abs/2606.13341v1)
- **Edit the Bits, Diff the Codes: Bitwise Residual Editing for Visual Autoregressive Models** — [arxiv_cl](https://arxiv.org/abs/2606.13558v1)
- **What's Old is New Again: Classical Dimensionality Reduction for Efficient Saliency-Guided Biometric Attack Detection** — [arxiv_cv](https://arxiv.org/abs/2606.13528v1)
- **MagPlus: Bridging Micro-to-Regular Facial Expressions through Learnable Magnification** — [arxiv_cv](https://arxiv.org/abs/2606.13312v1)
- **Dense Supervision, Sparse Updates: On the Sparsity and Geometry of On-Policy Distillation** — [arxiv_lg](https://arxiv.org/abs/2606.13657v1)
- **The Stable Recovery Manifold: Geometric Principles Governing Recoverability in Continual Learning** — [arxiv_lg](https://arxiv.org/abs/2606.13637v1)
- **Generative Modeling of Bach-Style Symbolic Music: A Comparative Study of Autoregressive, Latent-Variable, and Adversarial Approaches** — [arxiv_lg](https://arxiv.org/abs/2606.13626v1)
- **MaskWAM: Unifying Mask Prompting and Prediction for World-Action Models** — [arxiv_lg](https://arxiv.org/abs/2606.13515v1)
- **VideoMDM: Towards 3D Human Motion Generation From 2D Supervision** — [arxiv_lg](https://arxiv.org/abs/2606.13364v1)
- **Rarity-Gated Context Conditioning for Offline Imitation Learning-Based Maritime Anomaly Detection** — [arxiv_lg](https://arxiv.org/abs/2606.13311v1)
- **Physics-Guided Spatiotemporal Learning for Coastal Wave Peak Period Estimation from Video** — [arxiv_lg](https://arxiv.org/abs/2606.13302v1)
- **Evaluating Pluralism in LLMs through Latent Perspectives** — [arxiv_cl](https://arxiv.org/abs/2606.13254v1)
- **PolyAlign: Conditional Human-Distribution Alignment** — [arxiv_cl](https://arxiv.org/abs/2606.13227v1)
- **Layer-Resolved Optimal Transport for Hallucination Detection in NMT and Abstractive Summarization** — [arxiv_cl](https://arxiv.org/abs/2606.13216v1)
- **Towards More General Control of Diffusion Models Using Jeffrey Guidance** — [arxiv_cv](https://arxiv.org/abs/2606.13240v1)
- **Distributional Loss for Robust Classification** — [arxiv_cv](https://arxiv.org/abs/2606.13223v1)
- **Visual Place Recognition in Forests with Depth-Aware Distillation** — [arxiv_cv](https://arxiv.org/abs/2606.13206v1)
- **Iterative Visual Thinking: Teaching Vision-Language Models Spatial Self-Correction through Visual Feedback** — [arxiv_cv](https://arxiv.org/abs/2606.13156v1)
- **Demystifying Hidden-State Recurrence: Switchable Latent Reasoning with On-Policy Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2606.13106)
- **Modality Forcing for Scalable Spatial Generation** — [arxiv_cv](https://arxiv.org/abs/2606.13676v1)
- **RepWAM: World Action Modeling with Representation Visual-Action Tokenizers** — [arxiv_cv](https://arxiv.org/abs/2606.13674v1)
- **Flex4DHuman: Flexible Multi-view Video Diffusion for 4D Human Reconstruction** — [arxiv_cv](https://arxiv.org/abs/2606.13655v1)
- **World Tracing: Generative Pixel-Aligned Geometry Beyond the Visible** — [arxiv_cv](https://arxiv.org/abs/2606.13652v1)
- **Understanding Truncated Positional Encodings for Graph Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2606.13671v1)
- **Simplex-Constrained Sparse Bagging: Transitioning from Uniform Priors to Sparse Posteriors in Ensemble Learning** — [arxiv_lg](https://arxiv.org/abs/2606.13589v1)
- **Learning with Simulators: No Regret in a Computationally Bounded World** — [arxiv_lg](https://arxiv.org/abs/2606.13576v1)
- **Adjusted Cup-Product Neural Layer** — [arxiv_lg](https://arxiv.org/abs/2606.13568v1)
- **A2D2: Fine-Tuning Any-Length Discrete Diffusion for Adaptive Decoding** — [arxiv_lg](https://arxiv.org/abs/2606.13565v1)
- **CYC2002tommy/Deep-Research-Agent** — [github](https://github.com/CYC2002tommy/Deep-Research-Agent)
- **New OpenAI Academy courses for the next era of work** — [openai](https://openai.com/index/academy-courses-applying-ai-at-work)
- **keyuchen21/agentic-engineering-handbook** — [github](https://github.com/keyuchen21/agentic-engineering-handbook)
- **agentic-in/inferoa** — [github](https://github.com/agentic-in/inferoa)
- **SpaceX IPO: Live updates on everything you need to know** — [techcrunch_ai](https://techcrunch.com/2026/06/12/spacex-ipo-live-updates-on-everything-you-need-to-know/)
- **Chinese cybercrime operation that used AI to scam ‘hundreds of thousands of victims’ sued by Google** — [techcrunch_ai](https://techcrunch.com/2026/06/12/chinese-cybercrime-operation-that-used-ai-to-scam-hundreds-of-thousands-of-victims-sued-by-google/)
- **SpaceX, Anthropic, and OpenAI’s hot IPO summer** — [techcrunch_ai](https://techcrunch.com/video/spacex-anthropic-and-openais-hot-ipo-summer/)
- **It’s hot IPO summer, and the MANGOS are ripe** — [techcrunch_ai](https://techcrunch.com/podcast/its-hot-ipo-summer-and-the-mangos-are-ripe/)
- **Siri is good now??** — [theverge_ai](https://www.theverge.com/podcast/949079/siri-ai-good-vergecast)
- **Elon Musk is the world&#8217;s first trillionaire** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/948409/elon-musk-trillionaire-spacex-ipo)
- **SpaceX’s massive IPO: all the latest news** — [theverge_ai](https://www.theverge.com/business/948996/spacex-ipo-elon-musk)
- **Jeff Bezos’ AI startup aims to build an ‘artificial general engineer’** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/949005/jeff-bezos-prometheus-artificial-general-engineer)
- **The Download: “reprogramming” aging, and the hidden sense of interoception** — [mit_tech_review](https://www.technologyreview.com/2026/06/12/1138899/the-download-reprogramming-reverse-aging-interoception/)
- **You do your own time** — [mit_tech_review](https://www.technologyreview.com/2026/06/12/1138518/you-do-your-own-time-fiction/)
- **Siri won’t be your AI girlfriend** — [theverge_ai](https://www.theverge.com/tech/948890/siri-wont-be-your-ai-girlfriend)
- **Why “reprogramming” is the buzziest approach to reversing aging right now** — [mit_tech_review](https://www.technologyreview.com/2026/06/12/1138829/reprogramming-buzziest-approach-reversing-aging-right-now/)
- **Inside interoception: The hidden sense of how you feel inside** — [mit_tech_review](https://www.technologyreview.com/2026/06/12/1138833/inside-interoception-brain-body/)
- **desktop-hermes/hermes-agent-desktop** — [github](https://github.com/desktop-hermes/hermes-agent-desktop)
- **superagents-lab/xcode27-skills** — [github](https://github.com/superagents-lab/xcode27-skills)
- **Meta’s months-old AI unit is a soul-crushing gulag, say the engineers stuck inside it** — [techcrunch_ai](https://techcrunch.com/2026/06/12/metas-months-old-ai-unit-is-a-soul-crushing-gulag-say-the-engineers-stuck-inside-it/)
- **Mistral is rumored to be raising €3B at €20B valuation** — [techcrunch_ai](https://techcrunch.com/2026/06/12/mistral-is-rumored-to-be-raising-e3b-at-e20-valuation/)
- **Cheaper, faster, and culturally aware, Avataar’s video AI is built for India’s scale** — [techcrunch_ai](https://techcrunch.com/2026/06/11/cheaper-faster-and-culturally-aware-avataars-video-ai-is-built-for-indias-scale/)
- **Theker just raised $85M to build the factory robot that doesn’t specialize in anything** — [techcrunch_ai](https://techcrunch.com/2026/06/11/theker-just-raised-85m-to-build-the-factory-robot-that-doesnt-specialize-in-anything/)
- **Jeff Bezos’s Prometheus raises $12B to build an ‘artificial general engineer’ for the physical world** — [techcrunch_ai](https://techcrunch.com/2026/06/11/jeff-bezoss-prometheus-raises-12b-to-build-an-artificial-general-engineer-for-the-physical-world/)
- **bozhouDev/xhs-article-to-images** — [github](https://github.com/bozhouDev/xhs-article-to-images)
- **kanna12580/kk-knowledge-agent** — [github](https://github.com/kanna12580/kk-knowledge-agent)
- **DanMcInerney/architect-loop** — [github](https://github.com/DanMcInerney/architect-loop)
- **taisly/agent** — [github](https://github.com/taisly/agent)
- **DietrichGebert/ponytail** — [github](https://github.com/DietrichGebert/ponytail)
- **RainyMarks/DeepX** — [github](https://github.com/RainyMarks/DeepX)
- **TwoSevenOneT/EDRChoker** — [github](https://github.com/TwoSevenOneT/EDRChoker)
- **nelsonwerd/idea-to-ship-skills** — [github](https://github.com/nelsonwerd/idea-to-ship-skills)
- **Nanako0129/TokenBar** — [github](https://github.com/Nanako0129/TokenBar)
- **eadmin2/jarvis_ai** — [github](https://github.com/eadmin2/jarvis_ai)
- **thu-nmrc/openloop** — [github](https://github.com/thu-nmrc/openloop)
- **serenakeyitan/awesome-agent-loops** — [github](https://github.com/serenakeyitan/awesome-agent-loops)
- **cobusgreyling/loop-engineering** — [github](https://github.com/cobusgreyling/loop-engineering)
- **orange2ai/orange-line-illustration** — [github](https://github.com/orange2ai/orange-line-illustration)
- **alchaincyf/fanbox** — [github](https://github.com/alchaincyf/fanbox)
- **神了，世界杯第一天真按千问剧本踢了** — [qbitai](https://www.qbitai.com/2026/06/435321.html)
- **千里收购了一家毫米波雷达公司** — [qbitai](https://www.qbitai.com/2026/06/435196.html)
- **耐心资本护航创新，2026SuperLink开启创投价值共生新时代** — [qbitai](https://www.qbitai.com/2026/06/435192.html)
- **Anthropic老大的唯一 -1，就是AI股神的未婚妻** — [qbitai](https://www.qbitai.com/2026/06/433717.html)
- **2026奇点智能产品大会首批嘉宾官宣：在 AI 的“可交付的时代”，看一线专家如何拆解真实落地闭环！** — [qbitai](https://www.qbitai.com/2026/06/435105.html)
- **“智能体最后的考试”，Fable 5竟然不敌GPT 5.5** — [qbitai](https://www.qbitai.com/2026/06/434774.html)
- **BEV 杀入具身智能：跨维把机器人数据带上 Scaling 快车道** — [qbitai](https://www.qbitai.com/2026/06/434761.html)
- **氪星晚报｜SpaceX确定发行价，募资750亿美元创史上最大IPO；OpenAI CEO奥特曼推迟访韩计划；中央网信办举报中心开设“涉AI应用乱象举报专区”** — [36kr](https://36kr.com/p/3849942472512769?f=rss)
- **川润股份：孙公司签署液冷系统关键零部件产业化建设项目投资协议** — [36kr](https://36kr.com/newsflashes/3850142164784134?f=rss)
- **汇丰策略师Kettner：股市无需催化剂即可持续上涨** — [36kr](https://36kr.com/newsflashes/3850114468959235?f=rss)
- **澳大利亚AI云服务商Sharon AI与英伟达达成六年合作** — [36kr](https://36kr.com/newsflashes/3850102005028103?f=rss)
- **顶流偶像“空空”匿名作序的《浮生别院》，究竟有何魔力？** — [36kr](https://36kr.com/p/3849664394204419?f=rss)
- **36氪研究院 | 2026年中国工业用品制造与流通报告** — [36kr](https://36kr.com/p/3846798967818752?f=rss)
- **36氪首发 | 前瓦锡兰老兵创业，为船舶装上中国“心脏”，半年超 5000万订单** — [36kr](https://36kr.com/p/3849520020231432?f=rss)
- **热门中概股美股盘前涨跌不一，理想汽车涨超5%** — [36kr](https://36kr.com/newsflashes/3850185722664196?f=rss)
- **美股大型科技股盘前普涨，谷歌涨超1%** — [36kr](https://36kr.com/newsflashes/3850184110101509?f=rss)
- **高凯技术科创板IPO定于6月22日上会** — [36kr](https://36kr.com/newsflashes/3850096818459912?f=rss)
- **SpaceX美国IPO首日开盘报150美元** — [36kr](https://36kr.com/newsflashes/3850365941715971?f=rss)
- **SpaceX登陆纳斯达克** — [36kr](https://36kr.com/newsflashes/3850249144259846?f=rss)
- **映恩生物IPO审核状态变更为已受理** — [36kr](https://36kr.com/newsflashes/3850165413467398?f=rss)
- **长鑫科技集团股份有限公司IPO审核状态变更为注册生效** — [36kr](https://36kr.com/newsflashes/3850149434938631?f=rss)
- **广东真健康医疗科技开发股份有限公司港股IPO通过聆讯** — [36kr](https://36kr.com/newsflashes/3850142764406017?f=rss)
- **天博智能沪市主板IPO获上市委会议通过** — [36kr](https://36kr.com/newsflashes/3850092683236616?f=rss)