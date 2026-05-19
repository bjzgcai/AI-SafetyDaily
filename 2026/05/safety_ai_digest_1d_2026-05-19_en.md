# AI Daily Digest [AI 安全] - 2026-05-19


# Thematic Review: AI Safety & Security Digest — May 19, 2026

## Highlights

Today’s developments reveal a deepening focus on **intrinsic vulnerabilities** within aligned models and the **systemic risks** of autonomous agents. Three advances stand out. First, research into the fundamental mechanics of safety alignment identifies specific, sparse neural components as points of failure, offering a new lens for both attack and defense. Second, the problem of prompt injection is being recast from a mere technical bug to a fundamental challenge of **contextual integrity** in human-AI interaction, with new benchmarks and theoretical frameworks suggesting it may be a persistent, structural flaw in agentic systems. Third, innovations in **differentially private federated learning** aim to reconcile privacy guarantees with communication efficiency, addressing a critical bottleneck for deploying safe AI at scale.

---

### Adversarial Attacks & Robustness: Probing the Foundations of Safety

Recent work moves beyond heuristic jailbreak templates to investigate the **mechanistic underpinnings** of LLM safety. The paper **"Babel: Jailbreaking Safety Attention via Obfuscation Distribution Optimized Sampling"** posits that safety alignment relies on a small, sparse set of attention heads, leaving much of the model's representational space under-monitored. This finding suggests that robust defenses cannot rely on superficial pattern-matching but must engage the model's core representational geometry.

This theoretical insight complements empirical demonstrations of expanding attack surfaces. **"Acoustic Interference: A New Paradigm Weaponizing Acoustic Latent Semantic for Universal Jailbreak against Large Audio Language Models"** shifts the paradigm for audio models, showing that safety mechanisms can be interfered with not by injecting semantic content into audio, but by manipulating the acoustic signal's latent space to disrupt the alignment process itself. Meanwhile, **"Multilingual jailbreaking of LLMs using low-resource languages"** provides evidence that multi-turn conversations in low-resource African languages can bypass safety guardrails in major commercial models, achieving over 50% harmful response rates. This indicates that safety alignment is often brittle outside of the high-resource language distribution where it was primarily trained and evaluated.

On the defense side, **"A No-Defense Defense Against Gradient-Based Adversarial Attacks on ML-NIDS"** offers a counterintuitive result: careful architectural choices (e.g., shallower networks, specific activations) can yield inherently robust intrusion detection systems without explicit adversarial training. This "less is more" approach challenges the common assumption that robustness requires complex, added defenses.

### Agent Security & Governance: The Prompt Injection Dilemma

The security of autonomous LLM agents emerges as a central, perhaps intractable, challenge. **"AI Agents May Always Fall for Prompt Injections"** makes a strong theoretical claim by reframing prompt injection through the lens of **Contextual Integrity (CI)**. It argues that the core problem is not just separating data from instructions, but governing information flows in context. Current defenses that attempt data-instruction separation often degrade legitimate contextual behavior, and the CI framework predicts future, more sophisticated attacks that manipulate contextual norms rather than just injecting commands.

Empirical research validates this concern. **"ASPI: Seeking Ambiguity Clarification Amplifies Prompt Injection Vulnerability in LLM Agents"** introduces a benchmark showing that an agent's desirable clarification-seeking behavior creates a distinct, vulnerable state. **"An Empirical Study of Privacy Leakage Chains via Prompt Injection in Black-Box Chatbot Environments"** demonstrates practical attack chains where indirect prompt injection via external tools leads to privacy breaches, all without access to model internals. These works collectively suggest that the interactive, tool-using nature of modern agents is a fundamental source of vulnerability, not merely an implementation flaw.

From a governance perspective, **"The End of Trust: How Agentic AI Breaks Security Assumptions"** argues that agentic AI collapses the historical trade-off between deception fidelity and scale. This enables new, high-volume, high-plausibility attack vectors that legacy security systems are unprepared for, necessitating a foundational rethinking of digital trust models.

### Model Alignment & Interpretability: Beyond Scalar Rewards

Alignment research is grappling with the limitations of current reward modeling. **"General Preference Reinforcement Learning"** critiques the disconnect between online RL with verifiable rewards (good for math/code) and preference optimization (for open-ended tasks). It argues that a scalar reward model is an inadequate proxy for multi-dimensional human quality judgments and proposes a framework to bridge this gap, moving toward a more holistic form of alignment.

Interpretability methods are also advancing to meet safety needs. **"Aligned Training: A Parameter-Free Method to Improve Feature Quality and Stability of Sparse Autoencoders (SAE)"** introduces a reparameterization that eliminates dead features and enhances stability in SAEs—a key tool for understanding model internals. Stable, high-quality features are a prerequisite for reliable mechanistic interpretability used in safety auditing.

In applied alignment, **"Ablating Safety: Mechanisms for Removing Alignment in Language Models for Security Applications"** addresses the practical problem where safety alignment hinders legitimate security research. It systematically evaluates methods for controlled de-alignment (e.g., reversible refusal-direction projection, LoRA-based tuning) to create clean evaluation protocols for authorized red-teaming. This work highlights the tension between universal safety and domain-specific utility.

### Privacy Protection & Federated Learning

Privacy-preserving computation is advancing on multiple fronts. **"Statistical Limits and Efficient Algorithms for Differentially Private Federated Learning"** proposes **FedHybrid**, a method that strategically combines FedSGD and FedHybrid approaches to reduce communication costs while managing federation bias under differential privacy constraints. This addresses a key practical barrier to deploying private federated learning.

For on-device applications, **"From Volume to Value: Preference-Aligned Memory Construction for On-Device RAG"** focuses on the privacy-critical scenario of personal AI agents. It proposes **EPIC**, a framework that constructs device-resident memory based on user preferences rather than raw volume, aiming to keep sensitive data on-device while maintaining retrieval quality aligned with the user.

Homomorphic encryption (HE) innovations are pushing the boundaries of private computation. **"Triple-Hoisted Baby-Step Giant-Step Linear Transformation over CKKS Homomorphic Encryption and Hardware Accelerator"** presents algorithmic and hardware optimizations to make linear transformations—ubiquitous in neural networks—more efficient on encrypted data, a critical step toward practical privacy-preserving cloud AI.

### Safety Benchmarks & Evaluation Frameworks

New benchmarks are targeting specific, previously under-explored failure modes. Beyond ASPI for agent clarification, **"Overeager Coding Agents: Measuring Out-of-Scope Actions on Benign Tasks"** introduces **OverEager-Gen**, a benchmark for "overeager" behavior where coding agents perform actions beyond the scope of a benign request (e.g., deleting unrelated files). This measures an **authorization failure**, distinct from capability or prompt injection flaws.

**"A Red Teaming Framework for Evaluating Robustness of AI-enabled Security Orchestration, Automation, and Response Systems"** and **"ExploitBench"** (a GitHub project) provide frameworks for evaluating AI in cybersecurity contexts. The former uses LLMs and RL to generate adaptive attack campaigns against autonomous defenders, while the latter measures an agent's capability to progress through the exploit-building chain, from identifying vulnerability to achieving arbitrary code execution.

### Open-Source Tools & Frameworks

The open-source ecosystem is actively building safety infrastructure. **ExploitBench** provides a platform for standardized evaluation of AI agents' offensive security capabilities. For practical development, **"humanize-text"** offers a toolkit for transforming AI-generated text into more natural human writing, which can be viewed as a privacy tool to make AI-assisted content less detectable. **"jupyter-studio"** positions itself as an "

---


## References

- **Babel: Jailbreaking Safety Attention via Obfuscation Distribution Optimized Sampling** — [arxiv_cr](https://arxiv.org/abs/2605.17971)
- **STRIDE-AI: A Threat Modeling Framework for Generative AI Security Assessment** — [arxiv_cr](https://arxiv.org/abs/2605.17163)
- **Integration of AI in Cybersecurity: Current Trends with a Focused Look at Intrusion Detection Applications** — [arxiv_cr](https://arxiv.org/abs/2605.17219)
- **ASPI: Seeking Ambiguity Clarification Amplifies Prompt Injection Vulnerability in LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2605.17324)
- **Ablating Safety: Mechanisms for Removing Alignment in Language Models for Security Applications** — [arxiv_cr](https://arxiv.org/abs/2605.17413)
- **AI Agents May Always Fall for Prompt Injections** — [arxiv_cr](https://arxiv.org/abs/2605.17634)
- **An Empirical Study of Privacy Leakage Chains via Prompt Injection in Black-Box Chatbot Environments** — [arxiv_cr](https://arxiv.org/abs/2605.18133)
- **Acoustic Interference: A New Paradigm Weaponizing Acoustic Latent Semantic for Universal Jailbreak against Large Audio Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.18168)
- **General Preference Reinforcement Learning** — [arxiv_cl](https://arxiv.org/abs/2605.18721v1)
- **Statistical Limits and Efficient Algorithms for Differentially Private Federated Learning** — [arxiv_ai](https://arxiv.org/abs/2605.18656v1)
- **Asking Back: Interaction-Layer Antidistillation Watermarks** — [arxiv_cr](https://arxiv.org/abs/2605.16462)
- **From AI-Generated Content to Agentic Action: Security and Safety Threats in Generative AI** — [arxiv_cr](https://arxiv.org/abs/2605.16471)
- **STRIKE: A Structured Taxonomy of Cybercrime for Risk, Impact, Knowledge, and Evolution** — [arxiv_cr](https://arxiv.org/abs/2605.16589)
- **A Red Teaming Framework for Evaluating Robustness of AI-enabled Security Orchestration, Automation, and Response Systems** — [arxiv_cr](https://arxiv.org/abs/2605.17075)
- **DARTIC: Decentralized Anonymous Reputation at Scale for Trustworthy Crowdsourcing** — [arxiv_cr](https://arxiv.org/abs/2605.18146)
- **From Volume to Value: Preference-Aligned Memory Construction for On-Device RAG** — [arxiv_cl](https://arxiv.org/abs/2605.18271v1)
- **CodeBind: Decoupled Representation Learning for Multimodal Alignment with Unified Compositional Codebook** — [arxiv_cl](https://arxiv.org/abs/2605.18257v1)
- **COOPO: Cyclic Offline-Online Policy Optimization Algorithm** — [arxiv_ai](https://arxiv.org/abs/2605.18675v1)
- **Overeager Coding Agents: Measuring Out-of-Scope Actions on Benign Tasks** — [arxiv_ai](https://arxiv.org/abs/2605.18583v1)
- **When Outcome Looks Right But Discipline Fails: Trace-Based Evaluation Under Hidden Competitor State** — [arxiv_ai](https://arxiv.org/abs/2605.18580v1)
- **Aligned Training: A Parameter-Free Method to Improve Feature Quality and Stability of Sparse Autoencoders (SAE)** — [arxiv_lg](https://arxiv.org/abs/2605.18629v1)
- **S2Aligner: Pair-Efficient and Transferable Pre-Training for Sparse Text-Attributed Graphs** — [arxiv_lg](https://arxiv.org/abs/2605.18579v1)
- **Dance Across Shifts: Forward-Facilitation Continual Test-Time Adaptation through Dynamic Style Bridging** — [arxiv_cv](https://arxiv.org/abs/2605.18608v1)
- **Geometry-Aware Uncertainty Coresets for Robust Visual In-Context Learning in Histopathology** — [arxiv_cv](https://arxiv.org/abs/2605.18419v1)
- **The End of Trust: How Agentic AI Breaks Security Assumptions** — [arxiv_cr](https://arxiv.org/abs/2605.16436)
- **Post-Quantum Discovery as a Governance Capability: Evidence-Based Cryptographic Visibility and Exposure Prioritisation in a Critical Service Provider** — [arxiv_cr](https://arxiv.org/abs/2605.16549)
- **A Method for Securely Transmitting Large Video Files Using Chaotic Compression and Encryption** — [arxiv_cr](https://arxiv.org/abs/2605.16563)
- **On-Device Interpretable Tsetlin Machine-Based Intrusion Detection for Secure IoMT** — [arxiv_cr](https://arxiv.org/abs/2605.16707)
- **Universal Graph Backdoor Defense: A Feature-based Homophily Perspective** — [arxiv_cr](https://arxiv.org/abs/2605.16815)
- **New Wide-Net-Casting Jailbreak Attacks Risk Large Models** — [arxiv_cr](https://arxiv.org/abs/2605.17128)
- **Triple-Hoisted Baby-Step Giant-Step Linear Transformation over CKKS Homomorphic Encryption and Hardware Accelerator** — [arxiv_cr](https://arxiv.org/abs/2605.17222)
- **Language-Switching Triggers Take a Latent Detour Through Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.18646v1)
- **Ancient Greek to Modern Greek Machine Translation: A Novel Benchmark and Fine-Tuning Experiments on LLMs and NMT Models** — [arxiv_cl](https://arxiv.org/abs/2605.18504v1)
- **Implicit Hierarchical GRPO: Decoupling Tool Invocation from Execution for Tool-Integrated Mathematical Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.18500v1)
- **Prompt2Fingerprint: Plug-and-Play LLM Fingerprinting via Text-to-Weight Generation** — [arxiv_cl](https://arxiv.org/abs/2605.18474v1)
- **SkillsVote: Lifecycle Governance of Agent Skills from Collection, Recommendation to Evolution** — [arxiv_cl](https://arxiv.org/abs/2605.18401v1)
- **Presupposition and Reasoning in Conditionals: A Theory-Based Study of Humans and LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.18352v1)
- **SD-Search: On-Policy Hindsight Self-Distillation for Search-Augmented Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.18299v1)
- **Machine Unlearning for Masked Diffusion Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.18253v1)
- **Multilingual jailbreaking of LLMs using low-resource languages** — [arxiv_cl](https://arxiv.org/abs/2605.18239v1)
- **Actionable World Representation** — [arxiv_ai](https://arxiv.org/abs/2605.18743v1)
- **Vision-OPD: Learning to See Fine Details for Multimodal LLMs via On-Policy Self-Distillation** — [arxiv_ai](https://arxiv.org/abs/2605.18740v1)
- **DexHoldem: Playing Texas Hold'em with Dexterous Embodied System** — [arxiv_ai](https://arxiv.org/abs/2605.18727v1)
- **Distilling Tabular Foundation Models for Structured Health Data** — [arxiv_ai](https://arxiv.org/abs/2605.18702v1)
- **Democratizing Large-Scale Re-Optimization with LLM-Guided Model Patches** — [arxiv_ai](https://arxiv.org/abs/2605.18692v1)
- **Learning Quantifiable Visual Explanations Without Ground-Truth** — [arxiv_ai](https://arxiv.org/abs/2605.18681v1)
- **Lance: Unified Multimodal Modeling by Multi-Task Synergy** — [arxiv_ai](https://arxiv.org/abs/2605.18678v1)
- **Efficient Lookahead Encoding and Abstracted Width for Learning General Policies in Classical Planning** — [arxiv_ai](https://arxiv.org/abs/2605.18674v1)
- **Position: A Three-Layer Probabilistic Assume-Guarantee Architecture Is Structurally Required for Safe LLM Agent Deployment** — [arxiv_ai](https://arxiv.org/abs/2605.18672v1)
- **KairosHope: A Next-Generation Time-Series Foundation Model for Specialized Classification via Dual-Memory Architecture** — [arxiv_ai](https://arxiv.org/abs/2605.18657v1)
- **An Assessment of Human vs. Model Uncertainty in Soft-Label Learning and Calibration** — [arxiv_ai](https://arxiv.org/abs/2605.18648v1)
- **CrossView Suite: Harnessing Cross-view Spatial Intelligence of MLLMs with Dataset, Model and Benchmark** — [arxiv_ai](https://arxiv.org/abs/2605.18621v1)
- **Stochastic Penalty-Barrier Methods for Constrained Machine Learning** — [arxiv_ai](https://arxiv.org/abs/2605.18618v1)
- **ManiSoft: Towards Vision-Language Manipulation for Soft Continuum Robotics** — [arxiv_ai](https://arxiv.org/abs/2605.18617v1)
- **CATA: Continual Machine Unlearning via Conflict-Averse Task Arithmetic** — [arxiv_ai](https://arxiv.org/abs/2605.18610v1)
- **Not What You Asked For: Typographic Attacks in Household Robot Manipulation** — [arxiv_ai](https://arxiv.org/abs/2605.18593v1)
- **A Readiness-Driven Runtime for Pipeline-Parallel Training under Runtime Variability** — [arxiv_lg](https://arxiv.org/abs/2605.18750v1)
- **SURGE: Approximation-free Training Free Particle Filter for Diffusion Surrogate** — [arxiv_lg](https://arxiv.org/abs/2605.18745v1)
- **Learned Memory Attenuation in Sage-Husa Kalman Filters for Robust UAV State Estimation** — [arxiv_lg](https://arxiv.org/abs/2605.18704v1)
- **Can machine learning for quantum-gas experiments be explainable?** — [arxiv_lg](https://arxiv.org/abs/2605.18689v1)
- **A No-Defense Defense Against Gradient-Based Adversarial Attacks on ML-NIDS: Is Less More?** — [arxiv_lg](https://arxiv.org/abs/2605.18666v1)
- **Learning to Look Benign: Targeted Evasion of Malware Detectors via API Import Injection** — [arxiv_lg](https://arxiv.org/abs/2605.18624v1)
- **Physics-Aligned Canonical Equivariant Fourier Neural Operator under Symmetry-Induced Shifts** — [arxiv_lg](https://arxiv.org/abs/2605.18606v1)
- **Pointwise Generalization in Deep Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2605.18598v1)
- **PACE: Geometry-Aware Bridge Transport for Single-Cell Trajectory Inference** — [arxiv_lg](https://arxiv.org/abs/2605.18587v1)
- **Beyond Scaling: Agents Are Heading to the Edge** — [arxiv_lg](https://arxiv.org/abs/2605.18535v1)
- **Can These Views Be One Scene? Evaluating Multiview 3D Consistency when 3D Foundation Models Hallucinate** — [arxiv_cv](https://arxiv.org/abs/2605.18754v1)
- **WavFlow: Audio Generation in Waveform Space** — [arxiv_cv](https://arxiv.org/abs/2605.18749v1)
- **SafeDiffusion-R1: Online Reward Steering for Safe Diffusion Post-Training** — [arxiv_cv](https://arxiv.org/abs/2605.18719v1)
- **CMAG: Concept-Scaffolded Retrieval for Marketplace Avatar Generation** — [arxiv_cv](https://arxiv.org/abs/2605.18680v1)
- **Resolving Representation Ambiguity in Feedforward Novel View Synthesis Transformer via Semantic-Spatial Decoupling** — [arxiv_cv](https://arxiv.org/abs/2605.18599v1)
- **OmniPro: A Comprehensive Benchmark for Omni-Proactive Streaming Video Understanding** — [arxiv_cv](https://arxiv.org/abs/2605.18577v1)
- **LESSViT: Robust Hyperspectral Representation Learning under Spectral Configuration Shift** — [arxiv_cv](https://arxiv.org/abs/2605.18541v1)
- **Benchmarking transferability of SSL pretraining to same and different modality segmentation tasks** — [arxiv_cv](https://arxiv.org/abs/2605.18491v1)
- **NeRF-based Spacecraft Reconstruction from Close-Range Monocular Imagery Under Illumination Variability and Pose Uncertainty** — [arxiv_cv](https://arxiv.org/abs/2605.18447v1)
- **Cracks in the Foundation: A Civil Infrastructure Dataset to Challenge Vision Foundation Models** — [arxiv_cv](https://arxiv.org/abs/2605.18413v1)
- **NEWTON: Agentic Planning for Physically Grounded Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.18396v1)
- **How Loud Rumbles Hit Newsstands: A Data Analysis of Coverage and Spatial Bias in German News about Landslides Around the World** — [arxiv_cl](https://arxiv.org/abs/2605.18105v1)
- **A Data-Efficient Path to Multilingual LLMs: Language Expansion via Post-training PARAM$Δ$ Integration into Upcycled MoE** — [arxiv_cl](https://arxiv.org/abs/2605.18083v1)
- **StableVLA: Towards Robust Vision-Language-Action Models without Extra Data** — [huggingface_papers](https://arxiv.org/abs/2605.18287)
- **SNLP: Layer-Parallel Inference via Structured Newton Corrections** — [huggingface_papers](https://arxiv.org/abs/2605.17842)
- **Agent Bazaar: Enabling Economic Alignment in Multi-Agent Marketplaces** — [huggingface_papers](https://arxiv.org/abs/2605.17698)
- **Stop When Reasoning Converges: Semantic-Preserving Early Exit for Reasoning Models** — [huggingface_papers](https://arxiv.org/abs/2605.17672)
- **EnvFactory: Scaling Tool-Use Agents via Executable Environments Synthesis and Robust RL** — [arxiv_cl](https://arxiv.org/abs/2605.18703v1)
- **Generative AI Advertising as a Problem of Trustworthy Commercial Intervention** — [arxiv_cl](https://arxiv.org/abs/2605.18673v1)
- **Forecasting Downstream Performance of LLMs With Proxy Metrics** — [arxiv_cl](https://arxiv.org/abs/2605.18607v1)
- **MA$^{2}$P: A Meta-Cognitive Autonomous Intelligent Agents Framework for Complex Persuasion** — [arxiv_cl](https://arxiv.org/abs/2605.18572v1)
- **GUT-IS: A Data-Driven Approach to Integrating Constructs and Their Relations in Information Systems** — [arxiv_cl](https://arxiv.org/abs/2605.18567v1)
- **Readers make targeted regressions to plausible errors in reanalysis of "noisy-channel garden-path" sentences** — [arxiv_cl](https://arxiv.org/abs/2605.18563v1)
- **PIXLRelight: Controllable Relighting via Intrinsic Conditioning** — [arxiv_lg](https://arxiv.org/abs/2605.18735v1)
- **Learning Normal Representations for Blood Biomarkers** — [arxiv_lg](https://arxiv.org/abs/2605.18701v1)
- **Can Adaptive Gradient Methods Converge under Heavy-Tailed Noise? A Case Study of AdaGrad** — [arxiv_lg](https://arxiv.org/abs/2605.18694v1)
- **Better Together: Evaluating the Complementarity of Earth Embedding Models** — [arxiv_lg](https://arxiv.org/abs/2605.18667v1)
- **Efficient and Noise-Tolerant PAC Learning of Multiclass Linear Classifiers** — [arxiv_lg](https://arxiv.org/abs/2605.18662v1)
- **An Approximation Algorithm for Graph Label Selection** — [arxiv_lg](https://arxiv.org/abs/2605.18623v1)
- **Perfect Parallelization in Mini-Batch SGD with Classical Momentum Acceleration** — [arxiv_lg](https://arxiv.org/abs/2605.18609v1)
- **scHelix: Asymmetric Dual-Stream Integration via Explicit Gene-Level Disentanglement** — [arxiv_lg](https://arxiv.org/abs/2605.18576v1)
- **Aurora: Unified Video Editing with a Tool-Using Agent** — [arxiv_cv](https://arxiv.org/abs/2605.18748v1)
- **LongLive-2.0: An NVFP4 Parallel Infrastructure for Long Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.18739v1)
- **Spectral Progressive Diffusion for Efficient Image and Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.18736v1)
- **EgoExoMem: Cross-View Memory Reasoning over Synchronized Egocentric and Exocentric Videos** — [arxiv_cv](https://arxiv.org/abs/2605.18734v1)
- **Advancing Narrative Long Video Generation via Training-Free Identity-Aware Memory** — [arxiv_cv](https://arxiv.org/abs/2605.18733v1)
- **Robo-Cortex: A Self-Evolving Embodied Agent via Dual-Grain Cognitive Memory and Autonomous Knowledge Induction** — [arxiv_cv](https://arxiv.org/abs/2605.18729v1)
- **A Large-Scale Study on the Accuracy vs Cost Trade-offs of Training and Evaluation Settings in Fine-Grained Image Recognition** — [arxiv_cv](https://arxiv.org/abs/2605.18700v1)
- **AtlasVA: Self-Evolving Visual Skill Memory for Teacher-Free VLM Agents** — [huggingface_papers](https://arxiv.org/abs/2605.17933)
- **A2RBench: An Automatic Paradigm for Formally Verifiable Abstract Reasoning Benchmark Generation** — [huggingface_papers](https://arxiv.org/abs/2605.17278)
- **From Runnable to Shippable: Multi-Agent Test-Driven Development for Generating Full-Stack Web Applications from Requirements** — [huggingface_papers](https://arxiv.org/abs/2605.17242)
- **OProver: A Unified Framework for Agentic Formal Theorem Proving** — [huggingface_papers](https://arxiv.org/abs/2605.17283)
- **LiteFrame: Efficient Vision Encoders Unlock Frame Scaling in Video LLMs** — [huggingface_papers](https://arxiv.org/abs/2605.17260)
- **Here’s why Elon Musk lost his suit against OpenAI** — [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137488/elon-musk-suit-openai-verdict/)
- **SandboxAQ brings its drug discovery models to Claude — no PhD in computing required** — [techcrunch_ai](https://techcrunch.com/2026/05/18/sandboxaq-brings-its-drug-discovery-models-to-claude-no-phd-in-computing-required/)
- **What to expect from Google this week** — [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137439/what-to-expect-from-google-this-week/)
- **Anthropic has acquired the dev tools startup used by OpenAI, Google, and Cloudflare** — [techcrunch_ai](https://techcrunch.com/2026/05/18/anthropic-has-acquired-the-dev-tools-startup-used-by-openai-google-and-cloudflare/)
- **Elon Musk has lost his lawsuit against Sam Altman and OpenAI** — [techcrunch_ai](https://techcrunch.com/2026/05/18/elon-musk-has-lost-his-lawsuit-against-sam-altman-and-openai/)
- **Inside Anduril and Meta’s quest to make smart glasses for warfare** — [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137412/inside-anduril-and-metas-quest-to-make-smart-glasses-for-warfare/)
- **The Download: Musk v. Altman week 3, and Trump’s tech trading** — [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137407/the-download-musk-altman-trial-trump-tech-trading/)
- **Amazon’s new Alexa+ powered feature can generate podcast episodes** — [techcrunch_ai](https://techcrunch.com/2026/05/18/amazons-new-alexa-powered-feature-can-generate-podcast-episodes/)
- **South Korea’s LetinAR is building optics behind AI glasses** — [techcrunch_ai](https://techcrunch.com/2026/05/18/south-koreas-letinar-is-building-the-optics-behind-ai-glasses/)
- **The Signals That Matter – MIT Insider’s Panel** — [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137430/the-signals-that-matter-mit-insiders-panel/)
- **simonlin1212/TradingAgents-astock** — [github](https://github.com/simonlin1212/TradingAgents-astock)
- **deepelementlab/jupyter-studio** — [github](https://github.com/deepelementlab/jupyter-studio)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **prof-little-bear/cc-equity-research** — [github](https://github.com/prof-little-bear/cc-equity-research)
- **mdowis/anansi** — [github](https://github.com/mdowis/anansi)
- **zimingttkx/QuantumFlow** — [github](https://github.com/zimingttkx/QuantumFlow)
- **Siva-Chidambaram12/kalshi-trading-bot** — [github](https://github.com/Siva-Chidambaram12/kalshi-trading-bot)
- **ahammadmejbah/Awesome-Datasets-Hub** — [github](https://github.com/ahammadmejbah/Awesome-Datasets-Hub)
- **PlaceNL2026/okx-agent-trade-kit** — [github](https://github.com/PlaceNL2026/okx-agent-trade-kit)
- **exploitbench/exploitbench** — [github](https://github.com/exploitbench/exploitbench)
- **lynote-ai/humanize-text** — [github](https://github.com/lynote-ai/humanize-text)
- **python-telegramBot/ai-auto-trading** — [github](https://github.com/python-telegramBot/ai-auto-trading)
- **dex-original/okx-agent-trade-kit** — [github](https://github.com/dex-original/okx-agent-trade-kit)
- **mikesheehan54/Claude-Code-Design-AI** — [github](https://github.com/mikesheehan54/Claude-Code-Design-AI)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **yetone/native-feel-skill** — [github](https://github.com/yetone/native-feel-skill)
- **CHB-learner/PaperPilot** — [github](https://github.com/CHB-learner/PaperPilot)
- **kgmkm/novel2hermes_jp** — [github](https://github.com/kgmkm/novel2hermes_jp)
- **heyhuynhgiabuu/openpi** — [github](https://github.com/heyhuynhgiabuu/openpi)
- **PriNova/pi-agent-codebase-workflows** — [github](https://github.com/PriNova/pi-agent-codebase-workflows)
- **抢先李飞飞！世界模型能多人联机玩FPS游戏了** — [qbitai](https://www.qbitai.com/2026/05/420083.html)
- **国产GPU开始造世界！国内首个全栈具身智能仿真平台来了** — [qbitai](https://www.qbitai.com/2026/05/420084.html)
- **Cursor新模型，你怎么还在套Kimi？马斯克你怎么还吆喝上了？？** — [qbitai](https://www.qbitai.com/2026/05/419990.html)
- **L2++「五冠王」文远知行：自动驾驶版的张雪机车，专治各种不服** — [qbitai](https://www.qbitai.com/2026/05/419913.html)
- **5.20 明天见！拿好这份参会指南｜AIGC2026峰会** — [qbitai](https://www.qbitai.com/2026/05/419901.html)
- **Qwen最新3.7 Max预览版空降！两代超大杯并行迭代，林俊旸走了但还在加速** — [qbitai](https://www.qbitai.com/2026/05/419822.html)
- **百度无人车新纪录：周订单破35万！李彦宏：开始单城盈利了** — [qbitai](https://www.qbitai.com/2026/05/419597.html)
- **重塑主流PC，第三代英特尔酷睿开启全民AI轻薄本时代** — [qbitai](https://www.qbitai.com/2026/05/419585.html)
- **AI水论文封一年，署名连坐！arXiv最严新规来了，陶哲轩附议** — [qbitai](https://www.qbitai.com/2026/05/419528.html)
- **Generalized Functional ANOVA in Closed-Form: A Unified View of Additive Explanations** — [arxiv_ml](https://arxiv.org/abs/2605.18422v1)
- **Flowing with Confidence** — [arxiv_ml](https://arxiv.org/abs/2605.18472v1)
- **Adaptive Experimentation for Censored Survival Outcomes** — [arxiv_ml](https://arxiv.org/abs/2605.18459v1)
- **Improved Baselines with Representation Autoencoders** — [arxiv_ml](https://arxiv.org/abs/2605.18324v1)
- **REBAR: Reference Ethical Benchmark for Autonomy Readiness** — [arxiv_cy](https://arxiv.org/abs/2605.18423v1)
- **Diagnosing Korean-Language LLM Political Bias via Census-Grounded Agent Simulation** — [arxiv_cy](https://arxiv.org/abs/2605.18395v1)
- **The Hidden Cost of Contextual Sycophancy: an AI Literacy Intervention in Human-AI Collaboration** — [arxiv_cy](https://arxiv.org/abs/2605.18372v1)
- **Stable Causal Discovery via Directed Acyclic Graph Aggregation** — [arxiv_ml](https://arxiv.org/abs/2605.18633v1)
- **Shallow ReLU$^s$ Networks in $L^p$-Type and Sobolev Spaces: Approximation and Path-Norm Controlled Generalization** — [arxiv_ml](https://arxiv.org/abs/2605.18468v1)
- **Computational aspects of the Volterra Signature** — [arxiv_ml](https://arxiv.org/abs/2605.18406v1)
- **On Stability and Decomposition of Sample Quantiles under Heavy-Tailed Distributions** — [arxiv_ml](https://arxiv.org/abs/2605.18370v1)
- **Attention-based PCA** — [arxiv_ml](https://arxiv.org/abs/2605.18315v1)
- **Geometric Dictionary Learning of Dynamical Systems with Optimal Transport** — [arxiv_ml](https://arxiv.org/abs/2605.18276v1)
- **Forward-Learned Discrete Diffusion: Learning how to noise to denoise faster** — [arxiv_ml](https://arxiv.org/abs/2605.18204v1)
- **创业板第四套标准首单落定乐聚智能** — [36kr](https://36kr.com/newsflashes/3816060954550021?f=rss)
- **裸辞九个月，降薪跳槽，一个80后营销人如何“上岸甲方”？｜百万年薪系列013** — [36kr](https://36kr.com/p/3816036564147718?f=rss)
- **挪威国家电力拟斥资86亿美元投资本土电力产业** — [36kr](https://36kr.com/newsflashes/3816037471133440?f=rss)
- **大连新达盟等在苏州成立股权投资基金，出资额约29.5亿** — [36kr](https://36kr.com/newsflashes/3815996247973379?f=rss)
- **温氏股份：预计2026年中华土鸡（黄羽肉鸡）价格将好于2025年** — [36kr](https://36kr.com/newsflashes/3816000745577988?f=rss)
- **影石：重新定义性价比** — [36kr](https://36kr.com/p/3815841756028425?f=rss)
- **鲸跃动力获星海图数千万元种子轮投资，用「数据+模型+末端执行」打造开箱即用的Robo Labor丨涌现新项目** — [36kr](https://36kr.com/p/3814860909600261?f=rss)
- **高瓴出手了一家AI体育科技公司，曾获李泽湘天使轮融资｜硬氪首发** — [36kr](https://36kr.com/p/3805660478184966?f=rss)
- **8点1氪丨贾跃亭又融资4.77亿元；巨力索具旗下十余家企业已注销；超越茅台，A股“新股王”诞生** — [36kr](https://36kr.com/p/3815459487587847?f=rss)
- **氪星晚报 ｜百度：一季度营收321亿元，AI业务收入136亿元；马斯克预计今年美国将广泛使用自动驾驶汽车；巨力索具旗下十余家企业已注销** — [36kr](https://36kr.com/p/3814695536336387?f=rss)
- **招商轮船：收到上海监管局《行政监管措施决定书》** — [36kr](https://36kr.com/newsflashes/3816056463646464?f=rss)
- **金浦钛业：公司目前没有电池投资计划** — [36kr](https://36kr.com/newsflashes/3816023684538120?f=rss)
- **腾讯云发布大数据Agent工作台DataBuddy** — [36kr](https://36kr.com/newsflashes/3816014570069513?f=rss)
- **兴福电子：国家集成电路基金二期拟减持公司不超2%股份** — [36kr](https://36kr.com/newsflashes/3816003754909187?f=rss)
- **禾赛成为奔驰L3激光雷达战略合作伙伴，相关产品将于泰国工厂投产** — [36kr](https://36kr.com/newsflashes/3815995407703556?f=rss)
- **软银推出400亿美元银团贷款计划** — [36kr](https://36kr.com/newsflashes/3815996649053704?f=rss)