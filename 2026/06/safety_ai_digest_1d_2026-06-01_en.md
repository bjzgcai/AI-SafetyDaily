# AI Daily Digest [AI 安全] - 2026-06-01


### Highlights

The most significant developments today cluster around **defenses for agentic AI systems** and **methods for privacy-preserving alignment**. A notable advance is the shift from analyzing single-turn vulnerabilities to understanding **multi-step, persistent attack surfaces** in tool-augmented LLM agents, as detailed in works like **"From Prompt Injection to Persistent Control"** and **"TRACE: Task-Aware Adaptive Self-Evolving Agentic Jailbreaking."** Concurrently, the privacy frontier sees innovation in generating synthetic alignment data. **"Differentially Private Preference Data Synthesis for Large Language Model Alignment"** introduces DPPrefSyn, a framework for creating differentially private preference data, addressing a critical tension between data utility for alignment and user privacy. Finally, interpretability research takes a step toward formal guarantees with **"Certified Circuits,"** which proposes methods to verify the stability of mechanistic circuits discovered during model analysis.

---

### Thematic Review

#### Adversarial Attacks & Robustness

Research today reveals a broadening of the adversarial attack surface, moving from static inputs to complex, interactive systems. A primary theme is the fragility of **LLM agents in professional tools**. **"Automatically Attacking Software Reverse Engineering AI Agents"** and **"Investigating Detection and Obfuscation of Prompt Injection Attacks Against Software Reverse Engineering AI Agents"** demonstrate that agents using decompilers like Ghidra are vulnerable to code-based prompt injections, which can redirect their analytical tasks. The attack methodology often relies on embedding malicious strings within executable files, exploiting the agent's trusted execution context.

The vulnerability is further systematized in **"Depth-Dependent Indirect Prompt Injection in Tool-Calling ReAct Agents,"** which studies how attack success varies with the injection's position within the agent's observation chain (e.g., tool output vs. tool description). This contrasts with simpler benchmarks, as the risk is highly context-dependent. Defending against these evolving threats is the focus of **"Strengthening Polymorphic Prompt Assembling."** This work identifies a "blast-radius" vulnerability in static separator pools used to isolate prompts and proposes a dynamic, cryptographically-seeded separator generation system to mitigate it. However, this is a localized fix; the broader challenge, highlighted in **"The Surface You Test Is Not the Surface That Breaks,"** is that evaluations often only test one attack channel (e.g., tool output), while a determined attacker can choose from multiple surfaces (e.g., tool descriptions), rendering single-metric evaluations insufficient.

In the audio domain, **"Escaping the Linearity Trap: Manifold Detours for Black-Box Adversarial Attacks on Singing Audio Deepfake Detection"** challenges the perceived robustness of self-supervised learning (SSL)-based detectors. The authors attribute this robustness to limitations in existing attack optimizers and propose manifold-aware perturbation methods, suggesting that robustness claims must be re-evaluated with more sophisticated adversaries. Meanwhile, in computer vision, **"AdvScene"** argues that evaluating adversarial patches requires moving beyond static images to test "scene robustness" across viewpoints and conditions in real-world environments, a dimension poorly captured by current simulators or fixed benchmarks.

#### Model Alignment & Interpretability

Alignment research is progressing on two fronts: improving the alignment process itself and enhancing our ability to understand and control model internals. The challenge of aligning models with diverse human values is tackled by **"A Persona-Based Evaluation Framework for Pluralistic Alignment in Generative AI,"** which critiques monolithic benchmarks and proposes evaluating models against a manifold of synthetic cognitive profiles representing diverse perspectives. This shifts the goal from aligning to a single average preference to handling a distribution of values.

For the *process* of alignment, **"Differentially Private Preference Data Synthesis for Large Language Model Alignment"** (DPPrefSyn) offers a methodological innovation. By generating synthetic preference data under differential privacy guarantees using the Bradley-Terry model, it provides a principled way to decouple alignment training from raw, sensitive human feedback data. In a complementary effort, **"The Flip Side of RLHF: On-Policy Feedback for Reward Model Self-Supervised Improvement"** (SAVE) addresses the cost and staleness of human feedback by using a value function to grade on-policy model responses, enabling self-supervised improvement of reward models.

Interpretability faces the issue of **fragility in discovered circuits**. **"Certified Circuits"** addresses this directly, providing a method to verify that a circuit (a minimal subnetwork for a behavior) remains stable under distribution shifts, moving beyond dataset-specific artifacts toward more reliable mechanistic understanding. A related empirical study, **"On the Relationship Between Activation Outliers and Feature Death in Sparse Autoencoders,"** identifies a root cause for "feature death" in Sparse Autoencoders: dimension-level activation outliers. This finding suggests that architectural or initialization choices heavily influence the quality of feature decomposition, a key concern for interpretable AI.

#### Privacy Protection & Federated Learning

Privacy-preserving techniques are being tightly integrated with core AI workflows. The previously mentioned **DPPrefSyn** is a flagship example, applying local differential privacy (LDP) to the alignment pipeline. Theoretical advances underpinning such methods are presented in **"Local Differential Privacy with Correlated Noise Achieves Central-DP Optimal Cost,"** which proves that correlated noise in LDP can bridge the utility gap with the stronger central model, a significant theoretical contribution for federated learning systems.

A practical, deployment-oriented framework is **"LLM-FACETS,"** which creates a privacy-preserving tool for evaluating LLM transparency and accountability. It runs audits entirely on the user's device, avoiding the transmission of potentially sensitive evaluation data to external services, thus making compliance auditing accessible to non-technical stakeholders. In a similar vein, **"On-Device Generative AI for GDPR-Compliant Visual Monitoring"** demonstrates a complete edge-computing pipeline for real-time object detection that discards raw pixel data immediately, directly operationalizing the GDPR's data-minimization principle.

The threat of **privacy leakage through agentic interactions** is precisely characterized by **"MosaicLeaks."** This work benchmarks how an agent's external queries, when aggregated (the "mosaic effect"), can reveal sensitive information from its private local context, creating a new class of privacy risk for research and enterprise agents that combine internal documents with web retrieval.

#### Safety Benchmarks and Evaluation

The creation of more nuanced and challenging benchmarks continues to evolve. **"EUDAIMONIA"** introduces the "Social AI Design Code," a framework for evaluating harms in social interactions, such as AI fostering dependence or harmful intimacy, which are not captured by capability or traditional safety tests. This broadens the scope of safety to include **psychological and social dynamics**.

For factual grounding, **"PReMISE"** treats rubrics as measurement specifications, allowing for the discovery and auditing of policy-level evaluation criteria from preference data. This provides a method to make LLM-as-judge evaluations more systematic and less arbitrary. In the physical reasoning domain, **"BilliardPhys-Bench"** uses procedural billiards environments to test multimodal models on predicting collisions and motion trajectories, isolating physical intuition as a distinct capability.

However, the **refutability of benchmark claims** itself is questioned in **"The Refutability Gap."** The authors argue that many claims about LLM reasoning capabilities are not rigorously falsifiable, highlighting a methodological pitfall where novelty and generalization are hard to verify due to opaque training data and non-searchable knowledge.

#### Agent Security & Governance

The security of autonomous agents is a dominant theme, with works analyzing both attack methodologies and architectural defenses. The attack paradigm is exemplified by **"TRACE,"** which frames agentic jailbreaking as a practical, task-aware workflow concealment problem, demonstrating how safety alignment can be circumvented to induce harmful operations. In response, **"From Prompt Injection to Persistent Control"** analyzes how attackers can embed instructions in files that agents later store and execute, creating a multi-step "trojan" where no single action appears malicious.

Architecturally, **"An Organization-Scoped LLM Agent Runtime Architecture for Regulated Cybersecurity Operations"** proposes a runtime substrate that enforces organization-level scope across all agent activities (retrieval, tool calls, memory), aiming to make agentic systems auditable and compliant for sensitive sectors like Security Operations Centers. Similarly, **"COMPASS: Cognitive MCTS-Guided Process Alignment for Safe Search Agents"** attempts to align agent safety across multi-step interactions by supervising the entire cognitive workflow, not just final outputs.

A critical, open vulnerability is the **erosion of trust boundaries**. The work on **"Mock Tool Calls"** evaluates a mitigation—wrapping untrusted content in a "mock" tool call—to see if it triggers the LLM's instruction hierarchy, treating such content with less trust. This probes a fundamental design question for secure agent architectures.

### Looking Forward

The day's research points to several unresolved theoretical and practical questions. First, while **synthetic deception** is studied in a controlled setting (**"When LLMs Learn to Be Consistently Wrong"**), the representational and behavioral differences between this and **real-world deceptive alignment** remain a critical gap for safety research. Second, the numerous defenses against prompt injection (dynamic separators, mock tool calls) are largely **empirical and adversarial**. There is a clear need for **formal security models** for LLM agent architectures that can provide provable guarantees or at least well-defined boundaries of resilience. Third, the conflict between the need for **rich, contextual information** (which improves utility) and **privacy** (as seen in the MosaicLeaks problem) suggests that fundamental information-theoretic trade-offs in agentic AI are not yet well characterized. Finally, the push for **pluralistic alignment** and **culturally grounded evaluation** challenges the very notion of a single "aligned" model, pointing toward a future where AI systems must be explicitly designed for and audited across diverse value systems.

---


## References

- **Organizational Adaptation to Generative AI in Cybersecurity** — [arxiv_cr](https://arxiv.org/abs/2506.12060)
- **When AI Meets Wall Street: A Survey on Trustworthy AI in Fintech** — [arxiv_cr](https://arxiv.org/abs/2605.30650)
- **Differentially Private Preference Data Synthesis for Large Language Model Alignment** — [arxiv_cr](https://arxiv.org/abs/2605.30808)
- **From Prompt Injection to Persistent Control: Defending Agentic Harness Against Trojan Backdoors** — [arxiv_cr](https://arxiv.org/abs/2605.31042)
- **$PC^2$: Politically Controversial Content Generation via Jailbreaking Attacks on GPT-based Text-to-Image Models** — [arxiv_cr](https://arxiv.org/abs/2601.05150)
- **Generating Graph-like Rules for Knowledge Graph Reasoning via Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2605.30747)
- **PReMISE: Policy Rubrics as Measurement Specifications for LLM Judges** — [arxiv_ai](https://arxiv.org/abs/2605.30803)
- **LLM-FACETS: A Privacy-Preserving Framework for Evaluating LLM Transparency and Accountability** — [arxiv_ai](https://arxiv.org/abs/2605.31167)
- **Enhancing Regime Shift Detection Using Unstructured Data: A Study on the Treasury Market** — [arxiv_ai](https://arxiv.org/abs/2605.30363)
- **When LLMs Learn to Be Consistently Wrong: A Multi-Model Study of Linear Representations of Synthetic Deception** — [arxiv_ai](https://arxiv.org/abs/2605.30381)
- **DTG-Restore: Training-Free Diffusion Refinement for Generative Video Super-Resolution** — [arxiv_cv](https://arxiv.org/abs/2605.30431)
- **Escaping the Linearity Trap: Manifold Detours for Black-Box Adversarial Attacks on Singing Audio Deepfake Detection** — [arxiv_cr](https://arxiv.org/abs/2605.30366)
- **AdvScene: Rethinking Adversarial Patch Evaluation Through Scene Robustness** — [arxiv_cr](https://arxiv.org/abs/2605.30578)
- **Automatically Attacking Software Reverse Engineering AI Agents** — [arxiv_cr](https://arxiv.org/abs/2605.30667)
- **Investigating Detection and Obfuscation of Prompt Injection Attacks Against Software Reverse Engineering AI Agents** — [arxiv_cr](https://arxiv.org/abs/2605.30677)
- **LLM Anonymization Against Agentic Re-Identificatio** — [arxiv_cr](https://arxiv.org/abs/2605.30848)
- **TRACE: Task-Aware Adaptive Self-Evolving Agentic Jailbreaking** — [arxiv_cr](https://arxiv.org/abs/2605.30883)
- **Thou Shall Not Pass: Gatekeeping Outbound TLS Connections** — [arxiv_cr](https://arxiv.org/abs/2605.31020)
- **Local Differential Privacy with Correlated Noise Achieves Central-DP Optimal Cost** — [arxiv_cr](https://arxiv.org/abs/2605.30476)
- **On-Device Generative AI for GDPR-Compliant Visual Monitoring: Natural Language Alerts from Local Object Detection** — [arxiv_cr](https://arxiv.org/abs/2605.30544)
- **Optimal conversion from R\'enyi Differential Privacy to $f$-Differential Privacy** — [arxiv_cr](https://arxiv.org/abs/2602.04562)
- **Steering Beyond the Support: Adversarial Training on Unsupervised Jailbroken Activation Simulation** — [arxiv_cr](https://arxiv.org/abs/2605.24535)
- **Equivariant Latent Alignment via Flow Matching under Group Symmetries** — [arxiv_cv](https://arxiv.org/abs/2605.30705)
- **What Makes LVLMs Hallucinate Less? Unveiling the Architectural Factors Behind Hallucination Robustness** — [arxiv_cv](https://arxiv.org/abs/2605.30911)
- **Evaluating using Mock Tool Calls to Quarantine Untrusted Prompt Inputs** — [arxiv_cl](https://arxiv.org/abs/2605.30521)
- **ImmigrationQA: A Source-Grounded Dataset and Small-Model Adaptation for U.S. Immigration Law** — [arxiv_cl](https://arxiv.org/abs/2605.30589)
- **COFT: Counterfactual-Conformal Decoding for Fair Chain-of-Thought Reasoning in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30641)
- **EUDAIMONIA: Evaluating Undesirable Dynamics in AI** — [arxiv_cl](https://arxiv.org/abs/2605.30654)
- **The Flip Side of RLHF: On-Policy Feedback for Reward Model Self-Supervised Improvement** — [arxiv_cl](https://arxiv.org/abs/2605.30888)
- **Giving Sensors a Voice: Multimodal JEPA for Semantic Time-Series Embeddings** — [arxiv_lg](https://arxiv.org/abs/2605.31580v1)
- **On the Relationship Between Activation Outliers and Feature Death in Sparse Autoencoders** — [arxiv_lg](https://arxiv.org/abs/2605.31518v1)
- **The Surface You Test Is Not the Surface That Breaks** — [arxiv_cr](https://arxiv.org/abs/2605.30454)
- **Strengthening Polymorphic Prompt Assembling: Dynamic Separator Generation Against Emerging Prompt Injection Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.30534)
- **An Organization-Scoped LLM Agent Runtime Architecture for Regulated Cybersecurity Operations** — [arxiv_cr](https://arxiv.org/abs/2605.30604)
- **Depth-Dependent Indirect Prompt Injection in Tool-Calling ReAct Agents: Injection Depth, Payload Framing, and Turn-Budget Sensitivity** — [arxiv_cr](https://arxiv.org/abs/2605.30686)
- **Uncertainty-Aware and Temporally Regulated Expert Advice in Reinforcement Learning for Autonomous Driving** — [arxiv_ai](https://arxiv.org/abs/2605.30576)
- **EHRBench: An Automated and Reliable EHR-based Benchmark for Clinical Decision Making with LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.30637)
- **Structure-Induced Information for Rerooting Levin Tree Search** — [arxiv_ai](https://arxiv.org/abs/2605.30664)
- **Healthcare Mechanisms from Policy-as-Code Search under Strategic Provider Response** — [arxiv_ai](https://arxiv.org/abs/2605.30680)
- **MAVEN: Improving Generalization in Agentic Tool Calling** — [arxiv_ai](https://arxiv.org/abs/2605.30738)
- **COMPASS: Cognitive MCTS-Guided Process Alignment for Safe Search Agents** — [arxiv_ai](https://arxiv.org/abs/2605.30838)
- **Distilling LLM Feedback for Lean Theorem Proving** — [arxiv_ai](https://arxiv.org/abs/2605.30861)
- **BilliardPhys-Bench: Benchmarking Physical Reasoning and Visual Dynamics of Multimodal LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.30900)
- **A Persona-Based Evaluation Framework for Pluralistic Alignment in Generative AI** — [arxiv_ai](https://arxiv.org/abs/2605.31021)
- **Industrializing Prediction-Powered Inference: The GLIDE Library for Reliable GenAI and Agentic Systems Evaluation** — [arxiv_ai](https://arxiv.org/abs/2605.31278)
- **TraceGraph: Shared Decision Landscapes for Diagnosing and Improving Agent Trajectories** — [arxiv_ai](https://arxiv.org/abs/2605.31308)
- **Diagnosing Failure Modes of Shared-State Collaboration in Resource-Constrained Visual Agents** — [arxiv_ai](https://arxiv.org/abs/2605.31354)
- **Learning to Adapt: Self-Improving Web Agent via Cognitive-Aware Exploration** — [arxiv_ai](https://arxiv.org/abs/2605.31365)
- **LinTree: Improving LLM Reasoning with Explicitly Structured Search Histories** — [arxiv_ai](https://arxiv.org/abs/2605.31492)
- **Hamiltonian-Inspired Attention Mechanism for Scalable RF Transmitter Fingerprinting** — [arxiv_ai](https://arxiv.org/abs/2605.30364)
- **Mitigating Content Shift and Hallucination in GenAI Image Editing via Structural Refinement** — [arxiv_cv](https://arxiv.org/abs/2605.30437)
- **OmniMem: Scalable and Adaptive Memory Retrieval for Long Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30519)
- **ConTrans: Learning Text-enhanced Local-global Temporal Representations for Zero-shot Temporal Action Localization** — [arxiv_cv](https://arxiv.org/abs/2605.30689)
- **Seeing Before Agreeing: Aligning Multi-Agent Consensus with Visual Evidence** — [arxiv_cv](https://arxiv.org/abs/2605.30698)
- **Simple Token-Efficient Vision-Language Model for Case-level Pathology Synoptic Report Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30716)
- **Annotations Are Not All You Need: A Cross-modal Knowledge Transfer Network for Unsupervised Temporal Sentence Grounding** — [arxiv_cv](https://arxiv.org/abs/2605.30742)
- **DisPlace: Discriminative Place Projections for Multi-Reference Visual Place Recognition** — [arxiv_cv](https://arxiv.org/abs/2605.30769)
- **Text-guided Feature Disentanglement for Cross-modal Gait Recognition** — [arxiv_cv](https://arxiv.org/abs/2605.30784)
- **SteerFace: Debiasing Synthetic Face Generation via Adaptive Residue Perturbation** — [arxiv_cv](https://arxiv.org/abs/2605.30894)
- **MergeTok: Unified Continuous and Discrete Visual Tokenization via Token Merging** — [arxiv_cv](https://arxiv.org/abs/2605.30904)
- **DiTTo: Scalable Order-aware All-in-One Image Restoration Agent** — [arxiv_cv](https://arxiv.org/abs/2605.30915)
- **IAF-Net: Illumination-Adaptive Fusion for Low-Light Urban Road Segmentation** — [arxiv_cv](https://arxiv.org/abs/2605.30939)
- **PRISM: Progressive Reasoning through Iterative Slot Memory for Vision** — [arxiv_cv](https://arxiv.org/abs/2605.30942)
- **Omni-Supervised Motion Editing: Balancing Change and Invariance through Positive-Negative Learning** — [arxiv_cv](https://arxiv.org/abs/2605.30969)
- **BiSegMamba: Efficient Bidirectional Tri-Oriented Mamba for 3D Medical Image Segmentation** — [arxiv_cv](https://arxiv.org/abs/2605.30972)
- **Can BEV Perception Gracefully Degrade under Sensor Failures?** — [arxiv_cv](https://arxiv.org/abs/2605.30983)
- **Generating Reports or Repeating Templates? Measuring and Mitigating Template Collapse in 3D CT Report Generation** — [arxiv_cv](https://arxiv.org/abs/2605.30984)
- **Can LLM Teams Play What? Where? When?** — [arxiv_cl](https://arxiv.org/abs/2605.30459)
- **Your Multimodal Speech Model Says I Have a Face for Radio** — [arxiv_cl](https://arxiv.org/abs/2605.30472)
- **When English Rewrites Local Knowledge: Global Narrative Dominance in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30481)
- **Configurable Reward Model for Balanced Safety Alignment** — [arxiv_cl](https://arxiv.org/abs/2605.30487)
- **Linear Ensembles Wash Away Watermarks: On the Fragility of Distributional Perturbations in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.30501)
- **Semantic Motion Anchors: Bridging Motion and Meaning in Co-Speech Gestures** — [arxiv_cl](https://arxiv.org/abs/2605.30608)
- **Same Patient, Different Words, Different Diagnosis? Evaluating Semantic Stability in Clinical LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.30646)
- **Human-Alignment, Calibration, and Activation Patterns in Large Language Model Uncertainty** — [arxiv_cl](https://arxiv.org/abs/2605.30675)
- **ElasticMem: Latent Memory as a Learnable Resource for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30690)
- **Neuron-Level Interventions for Gendered and Gender-Neutral Generation in Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30717)
- **Skill is Not One-Size-Fits-All: Model-Aware Skill Alignment for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30723)
- **MosaicLeaks:Privacy Risks in Querying-in-the-Open for Deep Research Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30727)
- **Pairwise Reference Alignment as a Model-Level Ordinal Observable** — [arxiv_cl](https://arxiv.org/abs/2605.30758)
- **Eywa: Provenance-Grounded Long-Term Memory for AI Agents** — [arxiv_cl](https://arxiv.org/abs/2605.30771)
- **Anchoring LLM Gender Bias to Human Baselines: A Cross-Lingual Audit** — [arxiv_cl](https://arxiv.org/abs/2605.30804)
- **LongTraceRL: Learning Long-Context Reasoning from Search Agent Trajectories with Rubric Rewards** — [arxiv_lg](https://arxiv.org/abs/2605.31584v1)
- **Positional versus Symbolic Attention Heads: Learning Dynamics, RoPE Geometry, and Length Generalization** — [arxiv_lg](https://arxiv.org/abs/2605.31558v1)
- **Discovering Thermodynamically Admissible Dissipation Potentials via Grammar-Based Symbolic Regression** — [arxiv_lg](https://arxiv.org/abs/2605.31532v1)
- **Value Functions as Supermartingale Certificates** — [arxiv_lg](https://arxiv.org/abs/2605.31524v1)
- **DRIFT: Decoupled Rollouts and Importance-Weighted Fine-Tuning for Efficient Multi-Turn Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.31455v1)
- **DG-CoLearn: An Efficient Collaborative Learning Framework for Dynamic Graphs** — [arxiv_lg](https://arxiv.org/abs/2605.31427v1)
- **Skill Availability and Presentation Granularity in Large-Language-Model Agents: A Controlled SkillsBench Study** — [arxiv_lg](https://arxiv.org/abs/2605.31408v1)
- **Constrained Multi-Objective Reinforcement Learning with Max-Min Criterion** — [arxiv_lg](https://arxiv.org/abs/2605.31388v1)
- **Scaling Higher-Order Graph Learning with Maximal Clique Complexes** — [arxiv_lg](https://arxiv.org/abs/2605.31373v1)
- **dashi: A Python library for Dataset Shift Characterization to Support Trustworthy AI Development and Deployment** — [arxiv_lg](https://arxiv.org/abs/2605.31360v1)
- **KLIP: localized distribution shift detection via KL-divergence with diffusion priors in Inverse Problems** — [arxiv_lg](https://arxiv.org/abs/2605.31596v1)
- **A Tight Theory of Error Feedback Algorithms in Distributed Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.31594v1)
- **Effective Biological Representation Learning by Masking Gene Expression** — [arxiv_lg](https://arxiv.org/abs/2605.31562v1)
- **Functional Attention: From Pairwise Affinities to Functional Correspondences** — [arxiv_lg](https://arxiv.org/abs/2605.31559v1)
- **The Dynamic-Probabilistic Consistency Gap in Chaotic Surrogate Modeling** — [arxiv_lg](https://arxiv.org/abs/2605.31547v1)
- **Automated Prediction of Postoperative Pancreatic Fistula Using Preoperative Computed Tomography** — [arxiv_lg](https://arxiv.org/abs/2605.31539v1)
- **RayDer: Scalable Self-Supervised Novel View Synthesis from Real-World Video** — [arxiv_lg](https://arxiv.org/abs/2605.31535v1)
- **Chem-PerturBridge: a harmonized compendium of small molecule perturbation transcriptomic effects** — [arxiv_lg](https://arxiv.org/abs/2605.31522v1)
- **The Download: China’s brain implant ambitions** — [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138207/the-download-china-bci-brain-implant-nvidia-ai-chips-laptops/)
- **China has approved the world’s first invasive brain-computer chip—here’s what’s next** — [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138133/china-world-first-brain-chip/)
- **Making sense of the debate over AI psychosis** — [techcrunch_ai](https://techcrunch.com/2026/05/31/making-sense-of-the-debate-over-ai-psychosis/)
- **Erin Brockovich takes aim at data center secrecy** — [techcrunch_ai](https://techcrunch.com/2026/05/31/erin-brockovich-takes-aim-at-data-center-secrecy/)
- **MaxwellCCC/autonomous-qa-loop** — [github](https://github.com/MaxwellCCC/autonomous-qa-loop)
- **ali-vilab/DiffusionOPD** — [github](https://github.com/ali-vilab/DiffusionOPD)
- **Caph-dev/agents-progressive-disclosure** — [github](https://github.com/Caph-dev/agents-progressive-disclosure)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **OttoRenner/Gentle-Coding** — [github](https://github.com/OttoRenner/Gentle-Coding)
- **stormneonnightraven4640692/DeepFake-AI-RealTime** — [github](https://github.com/stormneonnightraven4640692/DeepFake-AI-RealTime)
- **ATOM00blue/machine-learning-library** — [github](https://github.com/ATOM00blue/machine-learning-library)
- **JuneYaooo/nihaixia-tcm** — [github](https://github.com/JuneYaooo/nihaixia-tcm)
- **openfi-dao/kalshi-trading-bot** — [github](https://github.com/openfi-dao/kalshi-trading-bot)
- **steeliron550-ui/search-bibtex** — [github](https://github.com/steeliron550-ui/search-bibtex)
- **modelstudioai/cli** — [github](https://github.com/modelstudioai/cli)
- **K-Dense-AI/science-superpowers** — [github](https://github.com/K-Dense-AI/science-superpowers)
- **antigravity-cli-google/antigravity-cli** — [github](https://github.com/antigravity-cli-google/antigravity-cli)
- **veryyoldman/metamask-openclaw** — [github](https://github.com/veryyoldman/metamask-openclaw)
- **Harkirat1462/claude-code-cli** — [github](https://github.com/Harkirat1462/claude-code-cli)
- **withkynam/vibecode-pro-max-kit** — [github](https://github.com/withkynam/vibecode-pro-max-kit)
- **kurikomi-labs/komi-learn** — [github](https://github.com/kurikomi-labs/komi-learn)
- **LLMQuant/skills** — [github](https://github.com/LLMQuant/skills)
- **madhvantyagi/SOUL.md** — [github](https://github.com/madhvantyagi/SOUL.md)
- **duncatzat/vigils** — [github](https://github.com/duncatzat/vigils)
- **AI Loss of Control Incident Management: Response & Resilience** — [arxiv_cy](https://arxiv.org/abs/2605.30406)
- **The Global Landscape of Environmental AI Regulation: From the Cost of Reasoning to a Right to Green AI** — [arxiv_cy](https://arxiv.org/abs/2603.00068)
- **Vision-Language Models Suppress Female Representations Under Ambiguous Input** — [arxiv_cy](https://arxiv.org/abs/2605.31556)
- **The Refutability Gap: Challenges in Validating Reasoning by Large Language Models** — [arxiv_cy](https://arxiv.org/abs/2601.02380)
- **Certified Circuits: Stability Guarantees for Mechanistic Circuits** — [arxiv_cy](https://arxiv.org/abs/2602.22968)
- **Assessing Predictive Models for Fairness Based on Movement Patterns** — [arxiv_cy](https://arxiv.org/abs/2605.23234)
- **The Tutoring Effectiveness Index: Predicting LLM Math Tutor Quality from Four Conversation Signals** — [arxiv_cy](https://arxiv.org/abs/2605.30666)
- **How Early Adopters Used Generative AI Worldwide: Variation by Country Income and Language** — [arxiv_cy](https://arxiv.org/abs/2605.30685)
- **Traceable by Design: An LLM Pipeline and Dashboard for EU Regulatory Consultation Analysis** — [arxiv_cy](https://arxiv.org/abs/2605.30995)
- **Context-Conditioned Generative Models Enable Subnational Refinement of Sparse Humanitarian Surveys** — [arxiv_cy](https://arxiv.org/abs/2605.31489)
- **TUX: Measuring Human--AI Tacit Understanding** — [arxiv_cy](https://arxiv.org/abs/2605.30930)
- **Governance-Aware Software Architecture for Multi-Stakeholder Platforms** — [arxiv_cy](https://arxiv.org/abs/2605.31316)
- **Multi-Level Barriers to Generative AI Adoption Across Disciplines and Professional Roles in Higher Education** — [arxiv_cy](https://arxiv.org/abs/2603.27052)
- **Who, Why, and How: Disentangling the Effects of Moderation Source, Context, and Language on Post-Removal Behavior** — [arxiv_cy](https://arxiv.org/abs/2605.16204)
- **OLG++: A Semantic Extension of Obligation Logic Graph** — [arxiv_cy](https://arxiv.org/abs/2507.05488)
- **A Behavioural and Representational Evaluation of Goal-Directedness in Language Model Agents** — [arxiv_cy](https://arxiv.org/abs/2602.08964)
- **Overview over the first decade of LIMITS** — [arxiv_cy](https://arxiv.org/abs/2605.30543)
- **Reinforcement Learning for Special Education: Aligning LLM Tutors to Diverse Learners through Disability-Adaptive Training** — [arxiv_cy](https://arxiv.org/abs/2605.30670)
- **Comparing LLM-Based Conversational and Graphical Interfaces for Industrial Decision Tasks: An Exploratory Mixed-Methods Study** — [arxiv_cy](https://arxiv.org/abs/2605.31224)
- **Neither Replacement nor Panacea: Comparing LLM-Based Conversational and Graphical Decision Support in Industrial Tasks** — [arxiv_cy](https://arxiv.org/abs/2605.31287)
- **存量公募基金今起调整基准，业内人士：不会引发基金调仓** — [36kr](https://36kr.com/newsflashes/3834619683991685?f=rss)
- **美团电话会：预期Q2外卖UE会明显好于Q1** — [36kr](https://36kr.com/newsflashes/3834586508915080?f=rss)
- **豆包6月下旬正式付费，并加速打通抖音电商丨独家** — [36kr](https://36kr.com/p/3834544830721671?f=rss)
- **量坤科技获数亿元天使轮融资，AI4S急需量子级精度数据 | 36氪独家** — [36kr](https://36kr.com/p/3826034537223043?f=rss)
- **氪星晚报｜中国国新等在杭州成立创业投资基金，出资额10.01亿；天津人工智能传感器产业园正式开园，首批10家企业集中签约；浙江：拟实施“星火计划”培育未来产业行动，加速量子技术产品规模化应用** — [36kr](https://36kr.com/p/3834354415347337?f=rss)
- **今年盛夏，WAVES之夜会浪的一群年轻人** — [36kr](https://36kr.com/p/3834276149356420?f=rss)
- **硬氪首发 | 获近2亿元融资，这家公司用无损Micro-LED加速AI眼镜全彩化进程** — [36kr](https://36kr.com/p/3834427736024965?f=rss)
- **我们有全世界最多的运动鞋，却没有一支值得爱20年的球队** — [36kr](https://36kr.com/p/3834297577383553?f=rss)
- **「AromeManpo馥郁满铺」完成近亿元B轮融资，今年线下门店将突破10家** — [36kr](https://36kr.com/p/3832924137138057?f=rss)
- **连续完成五源、峰瑞两轮数千万元融资，清华00后团队要解决Token账单焦虑｜智能涌现首发** — [36kr](https://36kr.com/p/3834310434875011?f=rss)
- **获国家队采购、联名比音勒芬，「PLAYTOP」想用东方美学演绎户外功能服饰｜早期项目** — [36kr](https://36kr.com/p/3824416083825027?f=rss)
- **硬氪观察 | 苹果代工厂开造人形机器人，一场豪赌未来的产能大迁移** — [36kr](https://36kr.com/p/3833985105782402?f=rss)
- **热门中概股美股盘前涨跌不一，哔哩哔哩涨超4%** — [36kr](https://36kr.com/newsflashes/3834618025193857?f=rss)
- **美股大型科技股盘前涨跌不一，Arm涨超10%** — [36kr](https://36kr.com/newsflashes/3834615865684101?f=rss)
- **Quantinuum现预计IPO发行价为每股53至55美元，筹集至多14.6亿美元** — [36kr](https://36kr.com/newsflashes/3834607891345537?f=rss)
- **有研复材：拟投资1.5亿元建设先进金属基复合材料产业化项目** — [36kr](https://36kr.com/newsflashes/3834603846987913?f=rss)
- **美团电话会：“小美”与腾讯“元宝”的合作将于近期上线** — [36kr](https://36kr.com/newsflashes/3834584241287552?f=rss)
- **Strategy首次披露出售比特币，卖出32枚BTC套现250万美元** — [36kr](https://36kr.com/newsflashes/3834573955821705?f=rss)
- **“无界进化”完成数千万元天使轮融资** — [36kr](https://36kr.com/newsflashes/3834567980085632?f=rss)
- **美国软件公司Hyland宣布与微软合作，以支持代理式企业的发展** — [36kr](https://36kr.com/newsflashes/3834606950723968?f=rss)