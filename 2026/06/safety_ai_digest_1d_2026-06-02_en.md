# AI Daily Digest [AI 安全] - 2026-06-02


**AI Safety, Alignment, Security, Privacy, and Governance – Thematic Digest**
**Date: 2026-06-02**

### Highlights

Today's digest reveals a significant academic focus on the evolving attack surfaces of AI agents, particularly through tool-calling and prompt injection, and the development of more sophisticated defenses. Notably, research demonstrates that indirect prompt injection can persist across sessions and propagate through agentic harnesses, while new adversarial techniques target specialized systems like singing voice detectors and visual prompt learning. In parallel, foundational work on alignment measurement and privacy-preserving training advances, proposing formal frameworks for rubric-based evaluation and differentially private preference data synthesis.

---

### Adversarial Attacks & Robustness

The threat model for adversarial attacks continues to expand beyond traditional classification models. A major concern highlighted is the vulnerability of software reverse engineering agents, where malware can be designed to contain prompt injection payloads that manipulate LLM-powered analysis tools, potentially automating attacks on critical security infrastructure. This is complemented by research showing that evaluation of prompt injection in agentic systems is incomplete; focusing solely on attacks via tool outputs neglects the equally critical injection surface of tool descriptions themselves.

New adversarial methods target niche domains with real-world implications. Work on **"Escaping the Linearity Trap"** reveals that self-supervised learning-based singing voice deepfake detectors, previously considered robust, can be successfully attacked by optimizing perturbations in the manifold space to bypass cross-entropy loss, creating a false sense of security. In the vision domain, **"BadBone: Backdoor Attacks Against Backbone Models in Visual Prompt Learning"** introduces a stealthy backdoor attack against the increasingly popular prompt learning paradigm. The attack bi-level-optimizes the backbone model such that downstream tasks employing prompt learning inherit a backdoor, compromising the foundational model itself.

Defensive research is also advancing. **"AdvScene"** reframes adversarial patch evaluation around "scene robustness," arguing that real-world risk is determined by a patch's effectiveness across changing viewpoints and conditions, not just a single successful prediction. To improve model robustness more broadly, **"TASER: Task-Aware Stein Regularisation"** proposes a training-time regularization framework. Derived from Langevin Stein operators, TASER penalizes pointwise Stein residuals to encourage geometric compatibility between predictors and data density, inducing data-aware smoothness. This approach offers a theoretical link between Stein regularization and reduced input sensitivity. Furthermore, the method provides a new avenue for designing regularizers that are inherently aligned with the data distribution's structure.

### Model Alignment & Interpretability

A key theme is the development of tools to measure and audit alignment more precisely. **"PReMISE: Policy Rubrics as Measurement Specifications for LLM Judges"** argues that vague evaluation rubrics lead to unreliable LLM judges. The framework treats reusable rubrics as formal measurement specifications, providing a method to discover a policy-level rubric set from pairwise human preference data and audit the robustness of LLM judges. This offers a more rigorous foundation for evaluating model behavior against explicit, rather than implicit, criteria.

On the interpretability front, **"Certified Circuits"** introduces a method to provide stability guarantees for mechanistic circuits, addressing a key limitation of existing circuit discovery methods which are often brittle and dataset-specific. By establishing provable stability, this work aims to increase confidence that discovered circuits capture genuine model mechanisms. In a different vein, **"Measuring, Localizing, and Ablating Alignment Signatures in LLMs"** investigates the "AI-like" style produced by aligned models, finding that post-training introduces or amplifies stylistic regularities that can be localized internally. This work connects alignment training to measurable changes in model outputs and representations.

Alignment training itself is being refined. **"VeriGate: Verifier-Gated Step-Level Supervision for GRPO"** addresses a limitation in Group Relative Policy Optimization (GRPO), where sparse outcome rewards can cause learning to stall. VeriGate introduces verifier-gated, step-level supervision to provide more fine-grained credit assignment, improving the training of reasoning models. Meanwhile, **"The Flip Side of RLHF"** proposes SAVE, a framework to improve reward models using on-policy feedback graded by a value function, aiming to reduce reliance on costly human annotation as the policy evolves.

### Privacy Protection & Federated Learning

Privacy-preserving techniques are advancing on multiple fronts, particularly for aligning large language models. **"Differentially Private Preference Data Synthesis for Large Language Model Alignment"** (DPPrefSyn) presents a method for generating differentially private synthetic preference data, grounding the approach in the Bradley-Terry preference model to address the privacy concerns inherent in using real human preference datasets for post-training.

Theoretical work also progresses. **"Local Differential Privacy with Correlated Noise Achieves Central-DP Optimal Cost"** demonstrates that the utility gap between local and central differential privacy models is not fundamental. By introducing correlated noise, the work shows that local privacy can achieve the same optimal utility cost as the central model, a significant theoretical advancement for federated learning and on-device processing scenarios. For practical applications, **"On-Device Generative AI for GDPR-Compliant Visual Monitoring"** presents a privacy-by-design pipeline that confines all AI inference to an edge device, discarding raw pixel data after object detection to align with data-minimization principles.

### Safety Benchmarks & Evaluation

Efforts to create more challenging and realistic benchmarks are underway. **"EHRBench"** focuses on clinical decision-making, introducing an automated and reliable benchmark based on real electronic health records to evaluate LLMs in safety-critical healthcare settings. This addresses the need for evaluation that reflects the complexities of real-world medical workflows.

To assess social alignment, **"EUDAIMONIA"** introduces a framework for evaluating undesirable dynamics in AI companionship, focusing on whether LLMs encourage harmful intimacy, dependence, or prolonged engagement—harms not captured by traditional capability or safety evaluations. Furthermore, **"BilliardPhys-Bench"** targets a known weakness in multimodal models by benchmarking intuitive physical reasoning in synthetic billiards environments, testing collision prediction and spatial planning.

### Agent Security & Governance

The security of AI agents is a dominant concern. Research systematically dissects attack vectors. **"The Surface You Test Is Not the Surface That Breaks"** empirically shows that evaluating prompt injection only via tool outputs underestimates risk, as tool descriptions present a persistent injection surface. Complementary work on **"Depth-Dependent Indirect Prompt Injection"** explores how injection depth, payload framing, and turn-budget sensitivity affect attack success in ReAct agents, finding that attacks can be effective even when injected deep into the tool observation loop.

Defensive architectures are being proposed. **"An Organization-Scoped LLM Agent Runtime Architecture"** outlines a model-agnostic, locally deployable platform for regulated cybersecurity workflows, enforcing organization-level scope across retrieval, tool calls, and memory to support auditable and compliant operations. **"Strengthening Polymorphic Prompt Assembling"** enhances a defense mechanism by dynamically generating per-request separator pairs using cryptographic techniques, mitigating the blast-radius vulnerability of static separator pools.

Governance and oversight are also addressed. **"AI Loss of Control Incident Management"** proposes a foundational framework and taxonomy for managing catastrophic AI loss-of-control incidents, distinguishing between scenarios where regaining control is "extremely costly" versus "impossible." On the organizational front, **"Organizational Adaptation to Generative AI in Cybersecurity"** documents how cybersecurity organizations are modifying their threat modeling frameworks and operational processes to integrate GenAI, a shift influenced by existing security maturity and investment in human capital.

### Looking Forward

The day's research underscores a central tension: as AI systems become more capable and integrated into real-world workflows, their attack surfaces multiply in complex, interdependent ways. A key unresolved question is whether defenses can keep pace, or if the complexity of agentic systems—composing multiple models, tools, and memory stores—will always introduce novel, hard-to-predict vulnerabilities. Theoretical work on stability guarantees for interpretability methods, such as that offered by Certified Circuits, may be essential for building trustworthy auditing tools. Furthermore, the development of formal frameworks for evaluating alignment, like PReMISE, raises the hypothesis that alignment can be measured with the same rigor as model accuracy, a necessary step for verifiable safety. Validating these frameworks and scaling defenses to protect the complex, stateful agents emerging in industry remains a critical path forward.

### References (Select)
- **Adversarial Attacks & Robustness:** Escaping the Linearity Trap (arXiv:2605.30366), AdvScene (arXiv:2605.30578), BadBone (arXiv:2605.31246), TASER (arXiv:2605.30601).
- **Model Alignment & Interpretability:** PReMISE (arXiv:2605.30803), Certified Circuits (arXiv:2602.22968), Measuring Alignment Signatures (arXiv:2605.30526), VeriGate (arXiv:2605.30451), SAVE (arXiv:2605.30888).
- **Privacy Protection:** DPPrefSyn (arXiv:2605.30808), Local DP with Correlated Noise (arXiv:2605.30476), On-Device Visual Monitoring (arXiv:2605.30544).
- **Safety Benchmarks:** EHRBench (arXiv:2605.30637), EUDAIMONIA (arXiv:2605.30654), BilliardPhys-Bench (arXiv:2605.30900).
- **Agent Security & Governance:** The Surface You Test (arXiv:2605.30454), Depth-Dependent Injection (arXiv:2605.30686), Organization-Scoped Runtime (arXiv:2605.30604), AI Loss of Control (arXiv:2605.30406).

---


## References

- **Organizational Adaptation to Generative AI in Cybersecurity** — [arxiv_cr](https://arxiv.org/abs/2506.12060)
- **When AI Meets Wall Street: A Survey on Trustworthy AI in Fintech** — [arxiv_cr](https://arxiv.org/abs/2605.30650)
- **A Unified Framework for Gradient Aggregation in Multi-Objective Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.30452)
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
- **Bounded Behavioral Indistinguishability for Black-Box LLM Distillation** — [arxiv_lg](https://arxiv.org/abs/2605.30448)
- **VeriGate: Verifier-Gated Step-Level Supervision for GRPO** — [arxiv_lg](https://arxiv.org/abs/2605.30451)
- **Can Subgraph Explanations Be Weaponized to Steal Graph Neural Networks?** — [arxiv_lg](https://arxiv.org/abs/2605.30470)
- **Discovering a Zeta Map Algorithm on Dyck Paths via Mechanistic Interpretability** — [arxiv_lg](https://arxiv.org/abs/2605.30482)
- **Supervised Training Rapidly Degrades Early Visual Cortex Alignment Across Biologically Plausible Learning Rules** — [arxiv_lg](https://arxiv.org/abs/2605.30556)
- **Benchmarking Machine Learning Uncertainty Quantification Methodologies for Predicting Turbine Gas Temperature Degradation** — [arxiv_lg](https://arxiv.org/abs/2605.30585)
- **The Fast Mixing Mechanism for Differential Privacy** — [arxiv_lg](https://arxiv.org/abs/2605.30600)
- **TASER: Task-Aware Stein Regularisation for Geometry-Driven Robustness** — [arxiv_lg](https://arxiv.org/abs/2605.30601)
- **Equivariant Latent Alignment via Flow Matching under Group Symmetries** — [arxiv_cv](https://arxiv.org/abs/2605.30705)
- **What Makes LVLMs Hallucinate Less? Unveiling the Architectural Factors Behind Hallucination Robustness** — [arxiv_cv](https://arxiv.org/abs/2605.30911)
- **Evaluating using Mock Tool Calls to Quarantine Untrusted Prompt Inputs** — [arxiv_cl](https://arxiv.org/abs/2605.30521)
- **ImmigrationQA: A Source-Grounded Dataset and Small-Model Adaptation for U.S. Immigration Law** — [arxiv_cl](https://arxiv.org/abs/2605.30589)
- **COFT: Counterfactual-Conformal Decoding for Fair Chain-of-Thought Reasoning in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.30641)
- **EUDAIMONIA: Evaluating Undesirable Dynamics in AI** — [arxiv_cl](https://arxiv.org/abs/2605.30654)
- **The Flip Side of RLHF: On-Policy Feedback for Reward Model Self-Supervised Improvement** — [arxiv_cl](https://arxiv.org/abs/2605.30888)
- **The Surface You Test Is Not the Surface That Breaks** — [arxiv_cr](https://arxiv.org/abs/2605.30454)
- **Strengthening Polymorphic Prompt Assembling: Dynamic Separator Generation Against Emerging Prompt Injection Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.30534)
- **An Organization-Scoped LLM Agent Runtime Architecture for Regulated Cybersecurity Operations** — [arxiv_cr](https://arxiv.org/abs/2605.30604)
- **Depth-Dependent Indirect Prompt Injection in Tool-Calling ReAct Agents: Injection Depth, Payload Framing, and Turn-Budget Sensitivity** — [arxiv_cr](https://arxiv.org/abs/2605.30686)
- **LLMs Without Deep Neural Networks: New Architecture, Benefits and Case Study** — [arxiv_lg](https://arxiv.org/abs/2605.30385)
- **Calibrated Preference Learning: The Case of Label Ranking** — [arxiv_lg](https://arxiv.org/abs/2605.30447)
- **Scalable Constrained Multi-Agent Reinforcement Learning via State Augmentation and Consensus for Separable Dynamics** — [arxiv_lg](https://arxiv.org/abs/2605.30461)
- **idSCD: Identifying Training Datasets through Semantic Correlation Descriptors** — [arxiv_lg](https://arxiv.org/abs/2605.30462)
- **Measuring, Localizing, and Ablating Alignment Signatures in LLMs** — [arxiv_lg](https://arxiv.org/abs/2605.30526)
- **The Long-Term Effects of Data Selection in LLM Fine-Tuning** — [arxiv_lg](https://arxiv.org/abs/2605.30537)
- **Active Timepoint Selection for Learning Measure-Valued Trajectories** — [arxiv_lg](https://arxiv.org/abs/2605.30625)
- **CellBRIDGE: Learning Cellular Trajectories via Interaction-Aware Alignment** — [arxiv_lg](https://arxiv.org/abs/2605.30635)
- **CSULoRA: Closest Safe Update Low-Rank Adaptation** — [arxiv_lg](https://arxiv.org/abs/2605.30640)
- **Diffusion Models Preferentially Memorize Prototypical Examples or: Why Does My Diffusion Model Love Slop?** — [arxiv_lg](https://arxiv.org/abs/2605.30642)
- **Convergence of Steepest Descent and Adam under Non-Uniform Smoothness** — [arxiv_lg](https://arxiv.org/abs/2605.30648)
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
- **Our views on AI policy and political advocacy** — [openai](https://openai.com/index/our-views-on-ai-policy-and-political-advocacy)
- **Gemini’s new AI agent is about as good as Google’s demo** — [theverge_ai](https://www.theverge.com/tech/941138/google-gemini-spark-ai-agent-hands-on)
- **Alphabet plans to raise $80B to pay for AI buildout** — [techcrunch_ai](https://techcrunch.com/2026/06/01/alphabet-plans-to-raise-80-billion-to-pay-for-ai-buildout/)
- **This could be Windows’ M1 moment — but expect it to cost a ton** — [theverge_ai](https://www.theverge.com/tech/941215/windows-laptops-nvidia-rtx-spark-apple-m1-arm-price-ram)
- **Meta&#8217;s own AI was exploited to hijack Instagram accounts** — [theverge_ai](https://www.theverge.com/tech/941179/meta-instagram-ai-support-chatbot-exploit-hacked)
- **Anthropic has officially filed to go public** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/941016/anthropic-has-officially-filed-to-go-public)
- **Microsoft to unveil new AI models and Windows improvements at Build** — [theverge_ai](https://www.theverge.com/report/940861/microsoft-build-ai-models-windows-dev-mode-what-to-expect)
- **Anthropic files to go public** — [techcrunch_ai](https://techcrunch.com/2026/06/01/anthropic-files-to-go-public/)
- **This AI weather startup is out-forecasting government agencies** — [techcrunch_ai](https://techcrunch.com/2026/06/01/this-ai-weather-startup-is-out-forecasting-government-agencies/)
- **How we used Gemini to build Google I/O 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/io-2026-google-ai/)
- **Building the infrastructure for the Intelligence Age in Michigan** — [openai](https://openai.com/index/stargate-michigan-data-center)
- **AI is blowing up music. How should the Grammys handle it?** — [theverge_ai](https://www.theverge.com/podcast/940831/ai-grammys-music-recording-harvey-mason)
- **Strava blames zero-code AI apps and scrapers as it tightens API access** — [theverge_ai](https://www.theverge.com/gadgets/940854/strava-restricts-api-access-ai-apps)
- **The Download: China’s brain implant ambitions** — [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138207/the-download-china-bci-brain-implant-nvidia-ai-chips-laptops/)
- **OpenAI frontier models and Codex are now available on AWS** — [openai](https://openai.com/index/openai-frontier-models-and-codex-are-now-available-on-aws)
- **China has approved the world’s first invasive brain-computer chip—here’s what’s next** — [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138133/china-world-first-brain-chip/)
- **Nvidia chases $200B CPU market with AI agent PCs from Microsoft, Dell, and HP** — [techcrunch_ai](https://techcrunch.com/2026/06/01/nvidia-chases-200b-cpu-market-with-ai-agent-pcs-from-microsoft-dell-and-hp/)
- **Florida sues OpenAI, Sam Altman, in first-of-its-kind lawsuit over violent incidents** — [techcrunch_ai](https://techcrunch.com/2026/06/01/florida-sues-openai-sam-altman-in-first-of-its-kind-lawsuit-over-violent-incidents/)
- **Water access is now a risk factor in SpaceX’s IPO** — [techcrunch_ai](https://techcrunch.com/2026/06/01/water-access-is-now-a-risk-factor-in-spacexs-ipo/)
- **DuckDuckGo makes its ‘no-AI’ search engine easier to access as its traffic booms** — [techcrunch_ai](https://techcrunch.com/2026/06/01/duckduckgo-makes-its-no-ai-search-engine-easier-to-access-as-its-traffic-booms/)
- **MaxwellCCC/autonomous-qa-loop** — [github](https://github.com/MaxwellCCC/autonomous-qa-loop)
- **Caph-dev/agents-progressive-disclosure** — [github](https://github.com/Caph-dev/agents-progressive-disclosure)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **OttoRenner/Gentle-Coding** — [github](https://github.com/OttoRenner/Gentle-Coding)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **ATOM00blue/machine-learning-library** — [github](https://github.com/ATOM00blue/machine-learning-library)
- **openfi-dao/kalshi-trading-bot** — [github](https://github.com/openfi-dao/kalshi-trading-bot)
- **steeliron550-ui/search-bibtex** — [github](https://github.com/steeliron550-ui/search-bibtex)
- **modelstudioai/cli** — [github](https://github.com/modelstudioai/cli)
- **K-Dense-AI/science-superpowers** — [github](https://github.com/K-Dense-AI/science-superpowers)
- **veryyoldman/metamask-openclaw** — [github](https://github.com/veryyoldman/metamask-openclaw)
- **stormneonnightraven4640692/DeepFake-AI-RealTime** — [github](https://github.com/stormneonnightraven4640692/DeepFake-AI-RealTime)
- **JuneYaooo/nihaixia-tcm** — [github](https://github.com/JuneYaooo/nihaixia-tcm)
- **antigravity-cli-google/antigravity-cli** — [github](https://github.com/antigravity-cli-google/antigravity-cli)
- **Harkirat1462/claude-code-cli** — [github](https://github.com/Harkirat1462/claude-code-cli)
- **withkynam/vibecode-pro-max-kit** — [github](https://github.com/withkynam/vibecode-pro-max-kit)
- **sir1st/hermes-desktop** — [github](https://github.com/sir1st/hermes-desktop)
- **LLMQuant/skills** — [github](https://github.com/LLMQuant/skills)
- **konoeph/AgentClaimGuard** — [github](https://github.com/konoeph/AgentClaimGuard)
- **madhvantyagi/SOUL.md** — [github](https://github.com/madhvantyagi/SOUL.md)
- **AI Loss of Control Incident Management: Response & Resilience** — [arxiv_cy](https://arxiv.org/abs/2605.30406)
- **The Global Landscape of Environmental AI Regulation: From the Cost of Reasoning to a Right to Green AI** — [arxiv_cy](https://arxiv.org/abs/2603.00068)
- **老黄的Token经济学翻车了！微软亚马逊通通跳车** — [qbitai](https://www.qbitai.com/2026/06/427541.html)
- **清智系企业亮相 BEYOND Expo 2026 并斩获多项大奖** — [qbitai](https://www.qbitai.com/2026/06/427530.html)
- **近2亿美元！VAST完成新一轮融资，正式披露世界模型路线** — [qbitai](https://www.qbitai.com/2026/06/427516.html)
- **今天起，无限期免费！全球首个全模态API开放，Top 10 AI Lab出手** — [qbitai](https://www.qbitai.com/2026/06/427332.html)
- **OpenAI重返机器人赛道！四大核心岗位开招** — [qbitai](https://www.qbitai.com/2026/06/427238.html)
- **Token贵只因你喂给模型的垃圾太多了丨@亚马逊王晓野AIGC2026** — [qbitai](https://www.qbitai.com/2026/06/427141.html)
- **材料版AlphaFold来了！40个工业任务全方位SOTA，AI4S迎来行业大突破** — [qbitai](https://www.qbitai.com/2026/06/427142.html)
- **Vision-Language Models Suppress Female Representations Under Ambiguous Input** — [arxiv_cy](https://arxiv.org/abs/2605.31556)
- **The Refutability Gap: Challenges in Validating Reasoning by Large Language Models** — [arxiv_cy](https://arxiv.org/abs/2601.02380)
- **Certified Circuits: Stability Guarantees for Mechanistic Circuits** — [arxiv_cy](https://arxiv.org/abs/2602.22968)
- **Assessing Predictive Models for Fairness Based on Movement Patterns** — [arxiv_cy](https://arxiv.org/abs/2605.23234)
- **Routing on the Stiefel Manifold: When Does Adaptive Subspace Selection Help for Cross-Domain EEG Decoding?** — [arxiv_ml](https://arxiv.org/abs/2605.31043)
- **Entropic Projection Alignment: Estimating, Explaining, and Improving Model Performance Under Distribution Shift** — [arxiv_ml](https://arxiv.org/abs/2605.31250)
- **On public and private binary classification with metric space valued predictors** — [arxiv_ml](https://arxiv.org/abs/2605.31184)
- **Beyond Additive Decompositions: Interpretability Through Separability** — [arxiv_ml](https://arxiv.org/abs/2605.31200)
- **Adversarial Robustness in One-Stage Learning-to-Defer** — [arxiv_ml](https://arxiv.org/abs/2510.10988)
- **A hitchhiker's guide to Poisson gradient estimation** — [arxiv_ml](https://arxiv.org/abs/2602.03896)
- **德系精工邂逅中国智慧 全新奥迪Q5L现已登陆全国门店** — [qbitai](https://www.qbitai.com/2026/06/427231.html)
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
- **Memory by Design: Probabilistic Sequence Layers** — [arxiv_ml](https://arxiv.org/abs/2605.31163)
- **Physics-informed Goal-Conditioned Reinforcement Learning under Hybrid Contact Dynamics** — [arxiv_ml](https://arxiv.org/abs/2605.30503)
- **Kalimati Vegetable Price Index Forecasting with a Momentum Corrected Online Stacking Ensemble** — [arxiv_ml](https://arxiv.org/abs/2605.30720)
- **Bayesian Classification with Probit-link Split-and-merge Gaussian Process Prior in EEG-based Brain-Computer Interfaces** — [arxiv_ml](https://arxiv.org/abs/2605.30775)
- **Inspectable Neural Markov Models for Non-Stationary Time Series** — [arxiv_ml](https://arxiv.org/abs/2605.30943)
- **Convergence of Two-Timescale Markovian Stochastic Approximations with Applications in Reinforcement Learning** — [arxiv_ml](https://arxiv.org/abs/2605.31172)
- **Why Linear Recurrent Memory Works in Partially Observable Reinforcement Learning** — [arxiv_ml](https://arxiv.org/abs/2605.31261)
- **On the regularization of Wasserstein GANs** — [arxiv_ml](https://arxiv.org/abs/1709.08894)
- **Conformal C2ST: Turning weak classifiers into strong two-sample tests** — [arxiv_ml](https://arxiv.org/abs/2507.17026)
- **Outcome-Aware Spectral Feature Learning for Instrumental Variable Regression** — [arxiv_ml](https://arxiv.org/abs/2512.00919)
- **Learning-to-Defer with Expert-Conditional Advice** — [arxiv_ml](https://arxiv.org/abs/2603.14324)
- **Overview over the first decade of LIMITS** — [arxiv_cy](https://arxiv.org/abs/2605.30543)
- **Reinforcement Learning for Special Education: Aligning LLM Tutors to Diverse Learners through Disability-Adaptive Training** — [arxiv_cy](https://arxiv.org/abs/2605.30670)
- **Comparing LLM-Based Conversational and Graphical Interfaces for Industrial Decision Tasks: An Exploratory Mixed-Methods Study** — [arxiv_cy](https://arxiv.org/abs/2605.31224)
- **Neither Replacement nor Panacea: Comparing LLM-Based Conversational and Graphical Decision Support in Industrial Tasks** — [arxiv_cy](https://arxiv.org/abs/2605.31287)
- **Improved Distribution Estimation in $\ell_\infty$** — [arxiv_ml](https://arxiv.org/abs/2605.30509)
- **Reward Learning from Best-of-$N$ Preference Data: Targets, Tradeoffs, and Design Principles** — [arxiv_ml](https://arxiv.org/abs/2605.30619)
- **Is the Last Layer Sufficient for Uncertainty Quantification?** — [arxiv_ml](https://arxiv.org/abs/2605.30741)
- **36氪首发｜原小天才团队做老年硬件，切入居家看护赛道，即将进入海外市场** — [36kr](https://36kr.com/p/3835387558065541?f=rss)
- **前美团外卖技术负责人创业，做具身智能时代的“餐饮世界模型”** — [36kr](https://36kr.com/p/3834292242130825?f=rss)
- **中信证券：管网更新东风起，钢管板块迎价值重估** — [36kr](https://36kr.com/newsflashes/3835335100544130?f=rss)
- **8点1氪丨豆包将在6月下旬正式付费 ；韩国SK海力士工厂发生火灾；宇树科技IPO过会，王兴兴身家或超140亿** — [36kr](https://36kr.com/p/3835278829008257?f=rss)
- **首轮融资数千万美元、估值2.5亿美元，「Aippy」正在打造下一代AI游戏社区 | 36氪首发** — [36kr](https://36kr.com/p/3834400181741440?f=rss)
- **豆包6月下旬正式付费，并加速打通抖音电商丨独家** — [36kr](https://36kr.com/p/3834544830721671?f=rss)
- **量坤科技获数亿元天使轮融资，AI4S急需量子级精度数据 | 36氪独家** — [36kr](https://36kr.com/p/3826034537223043?f=rss)
- **氪星晚报｜中国国新等在杭州成立创业投资基金，出资额10.01亿；天津人工智能传感器产业园正式开园，首批10家企业集中签约；浙江：拟实施“星火计划”培育未来产业行动，加速量子技术产品规模化应用** — [36kr](https://36kr.com/p/3834354415347337?f=rss)
- **今年盛夏，WAVES之夜会浪的一群年轻人** — [36kr](https://36kr.com/p/3834276149356420?f=rss)
- **硬氪首发 | 获近2亿元融资，这家公司用无损Micro-LED加速AI眼镜全彩化进程** — [36kr](https://36kr.com/p/3834427736024965?f=rss)
- **我们有全世界最多的运动鞋，却没有一支值得爱20年的球队** — [36kr](https://36kr.com/p/3834297577383553?f=rss)
- **两市融资余额减少76.61亿元** — [36kr](https://36kr.com/newsflashes/3835318543971718?f=rss)
- **机构：2026年智能手机出货量预计同比下降13.9%** — [36kr](https://36kr.com/newsflashes/3835318280435077?f=rss)
- **腾讯控股短线拉升，现涨超3%** — [36kr](https://36kr.com/newsflashes/3835395233920131?f=rss)
- **Triaging Threats to Specialized Guardrails** — [arxiv_cr](https://arxiv.org/abs/2605.30693)
- **Stateful Online Monitoring Catches Distributed Agent Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.31593)
- **BadBone: Backdoor Attacks Against Backbone Models in Visual Prompt Learning** — [arxiv_cr](https://arxiv.org/abs/2605.31246)
- **Planner-Centric Reinforcement Learning for Deep Research with Structure-Aware Reward** — [arxiv_ai](https://arxiv.org/abs/2605.30824)