# AI Daily Digest [AI 安全] - 2026-05-23


# Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance – May 23, 2026

## Highlights

Today's research landscape reveals significant advances in theoretical foundations, evaluation paradigms, and unifying frameworks for AI safety. Three developments stand out for their potential to reshape core aspects of the field:

1.  **A Foundational Bridge Between Differential Privacy and Robustness:** The paper **"Provable Robustness against Backdoor Attacks via the Primal-Dual Perspective on Differential Privacy"** establishes a profound connection between randomized smoothing for robustness certification and the dual view of differential privacy (DP). By leveraging privacy profiles for composing heterogeneous mechanisms, it extends provable robustness guarantees to the challenging case of backdoor attacks, where both training and test data are perturbed. This provides a more principled mathematical framework for analyzing poisoning robustness.
2.  **Exposing a Fundamental Flaw in Multimodal Explainability Evaluation:** The work on **"Measuring Cross-Modal Synergy"** demonstrates that current methods for evaluating Vision-Language Model (VLM) explanations are fundamentally flawed. It reveals that due to strong language priors and modality biases, VLMs can answer visual queries using text alone, causing unimodal perturbation metrics to penalize faithful explainers. This "evaluation collapse" necessitates entirely new benchmarks focused on cross-modal reasoning fidelity.
3.  **A Unifying Geometric Theory for Representation Robustness:** **"The Matching Principle"** presents a compelling theoretical synthesis, arguing that disparate problems like domain adaptation, adversarial robustness, and alignment safety are manifestations of a single statistical challenge: estimating and regularizing against nuisance variations. This geometric perspective on loss functions offers a unifying lens for designing and understanding robust representation learning methods.

## Thematic Review

### Adversarial Attacks & Robustness

The quest for robustness continues to evolve from empirical defenses toward more principled, theoretical guarantees. A landmark contribution is the work on **"Provable Robustness against Backdoor Attacks..."**, which successfully merges the randomized smoothing paradigm with differential privacy theory. This is a critical advance, as backdoor attacks, involving joint manipulation of training and test time, have been notoriously difficult to certify against. The authors' use of privacy profiles to handle the composition of differentially private mechanisms provides a powerful, numerically feasible tool for computing robustness certificates.

Parallel efforts focus on specific threat models and domains. In federated learning, **"EnCAgg"** proposes a dynamic defense against model poisoning by moving beyond fixed thresholds to a small number of trusted client gradients. This addresses the key challenge of adaptability to evolving attacker strategies. For time-series forecasting, **"TimeGuard"** systematically evaluates 13 defenses and identifies fundamental failure modes caused by "data entanglement," leading to their proposed channel-wise pool training method. The adversarial mindset is also being systematized through frameworks like **CCLab**, which provides a reinforcement learning-based adversarial tester for network congestion controllers, highlighting the need for robustness testing in non-AI critical infrastructure.

A concerning development is the weaponization of trust mechanisms themselves. **"Adversarial Trust Poisoning in Vehicular Collaborative Perception" (TrustFlip)** shows how consistency-based defenses can be exploited to poison trust scores, turning a security measure into an attack vector. This underscores the adversarial cat-and-mouse nature of security research. On the attack side, **"THREAT"** presents a reasoning-driven, multi-LLM jailbreaking framework that formulates prompt discovery as an optimization problem, demonstrating the increasing sophistication of automated red-teaming.

### Model Alignment & Interpretability

Research into understanding and steering model behavior is advancing on multiple fronts, from foundational theory to empirical auditing. **"The Matching Principle"** offers a deep theoretical contribution by framing alignment safety (among other goals) as a problem of regularizing a model's Jacobian against deployment-time nuisance variations. This geometric view could inspire new regularization techniques for alignment.

Empirical work is revealing both the mechanisms and failures of alignment. **"What Counts as AI Sycophancy?"** provides a much-needed taxonomy, disentangling the poorly defined concept into distinct behaviors. This is crucial for developing targeted mitigations, as a model resistant to one form may still exhibit another. Studies like **"Modeling Pathology-Like Behavioral Patterns"** use behavioral fine-tuning to induce and examine "maladaptive" patterns (e.g., depression, paranoia) in LLMs, offering a controlled method to study and potentially defend against pathological model states.

Interpretability tools are being refined and critically evaluated. **"SegCompass"** uses Sparse Autoencoders (SAEs) to create an interpretable alignment pathway between text reasoning and visual grounding in segmentation, moving beyond opaque "black box" methods. Conversely, **"Reading Task Failure Off the Activations"** performs a sparse-feature audit of GPT-2, finding specific features (e.g., one labeled 'cryptographic keys') that correlate strongly with failure on the Indirect Object Identification task. This suggests SAEs can be used for granular model diagnostics.

Alignment from human preferences is also being operationalized in new ways. **"Implicit Safety Alignment from Crowd Preferences"** aims to distill shared safety principles from diverse human preference data, using them to regularize downstream RL agents. This addresses the challenge of transferring implicit, crowd-sourced safety norms.

### Privacy Protection & Federated Learning

Privacy research is intensely focused on bridging the gap between formal guarantees and practical utility. The audit of **Apple's DifferentialPrivacy.framework** is a standout contribution. By reverse-engineering Apple's implementation, the researchers uncovered implementation bugs, misconfigurations, and practical risks that could undermine the promised privacy guarantees. This work exemplifies the critical importance of third-party auditing for deployed systems making strong privacy claims.

In machine learning, differential privacy remains a key tool, but its performance cost is a major hurdle. **"Lumberjack"** tackles this for random forests, introducing a novel heavy-hitter detection algorithm for hierarchical data to enable aggressive, privacy-preserving pruning, thereby achieving substantially higher utility. The theoretical underpinning for DP auditing is strengthened by **"Optimal Guarantees for Auditing Rényi Differentially Private Machine Learning,"** which provides a hypothesis-testing framework with non-asymptotic confidence intervals and proves minimax optimality.

Attacks also evolve to target privacy assurances. **"Boundary-targeted Membership Inference Attacks"** hypothesize that safety classifiers are most vulnerable at their decision boundaries, where confidence is lowest. This directs attacks more efficiently. The field of privacy metrics is itself under scrutiny, with **"Information Leakage Envelopes"** introducing the PML envelope to quantify worst-case leakage under post-processing, addressing a limitation in pointwise maximal leakage.

### Safety Benchmarks and Evaluation

The community is developing more nuanced and challenging benchmarks to probe model failures. **"Measuring Cross-Modal Synergy"** is a pivotal critique, arguing that existing VLM explainability benchmarks are ill-conceived. Its proposed benchmark will force evaluation of true cross-modal integration, not just language prior exploitation. Similarly, **"Benchmarking and Improving Monitors for Out-Of-Distribution Alignment Failure in LLMs" (MOOD)** creates a controlled benchmark to test if monitoring pipelines can detect OOD alignment failures, a key challenge for real-world deployment.

Domain-specific safety and capability benchmarks are proliferating. **"AttuneBench"** uses genuine multi-turn conversations to evaluate emotional intelligence, while **"SpaceDG"** tests spatial reasoning under visual degradation like blur and low light, moving beyond pristine-input assumptions. For agentic AI, **"Boiling the Frog"** introduces a multi-turn benchmark for agent safety, shifting focus from what agents *say* to what they *do* in an environment. **"TerminalWorld"** benchmarks agents on real-world terminal tasks, revealing significant gaps in current model capabilities. These benchmarks collectively push evaluations toward more realistic, challenging, and safety-relevant scenarios.

### Agent Security & Governance

The security of multi-agent and autonomous systems is emerging as a critical frontier. **"LCGuard"** addresses a novel threat in latent communication, proposing a guard to prevent sensitive information from leaking through KV-cache sharing between LLM agents. The problem of prompt injection in agents is highlighted by **"Blind Spots in the Guard,"** which shows that "domain-camouflaged" injections can evade detectors with high success rates, drastically reducing detection accuracy from ~94% to as low as ~10%.

Foundational work for secure agent architectures is also appearing. **"RADAR"** defends Retrieval-Augmented Generation (RAG) systems against dynamic retrieval corruption using a graph-based energy minimization approach with Bayesian memory. For hardware security in the IoT/healthcare domain, **"QT-PUF"** proposes a quantum-tunneling-based Physical Unclonable Function for implantable medical devices, tying device identity to inherent physical variations.

Governance and evaluation frameworks for agents are being operationalized. **"Agentic CLEAR"** offers a dynamic evaluation framework for LLM agents at system, trace, and node levels. The **"AI-kill-chain"** repository proposes an adapted cyber kill chain for LLM and agentic threats, including stages for model extraction and agentic pivots, providing a structured lens for defenders. The news item on **Intel's SuperClaw** solution, claiming 99% sensitive information recognition and 70% cloud token reduction, represents the industry's push for practical, privacy-preserving agent architectures, though these claims await independent verification.

## Looking Forward

Despite substantial progress, several deep theoretical and practical questions remain unresolved, pointing toward fertile ground for future work:

1.  **Compositionality of Robustness Guarantees:** While papers like the DP-Robustness bridge offer strong foundations, composing guarantees across the full ML pipeline (data collection, training, inference, deployment) under heterogeneous threat models remains a grand challenge. Can a unified theory of "end-to-end robustness" be formalized?
2.  **The Cross-Modal Reasoning Gap:** The critique of VLM explainability evaluation opens a key question: what constitutes *faithful* cross-modal reasoning, and how can we design training objectives and architectures that intrinsically foster it, rather than relying on language shortcuts?
3.  **From Geometric Theory to Alignment Practice:** The Matching Principle provides a beautiful unifying framework. The next step is to operationalize it: can we design novel, computationally tractable regularization objectives based on this principle that demonstrably improve alignment and safety over existing methods like RLHF or adversarial training?
4.  **Security in Open, Dynamic Environments:** Benchmarks like "Boiling the Frog" and "TerminalWorld" highlight the fragility of agents in open-ended settings. A major open question is how to design agents that maintain safety and security guarantees while interacting with dynamic, partially observable, and potentially adversarial environments over long horizons. The tension between adaptability and security needs fundamental resolution.
5.  **The Verifiability of Privacy in Deployed Systems:** The Apple DP audit underscores a critical issue: as privacy mechanisms become more complex, how can we build verifiable, open-source frameworks for their implementation and auditing, ensuring that deployed systems live up to their stated guarantees? The development of more practical DP algorithms like Lumberjack is necessary but not sufficient without trust in their implementation.

---


## References

- **Provable Robustness against Backdoor Attacks via the Primal-Dual Perspective on Differential Privacy** — [arxiv_cr](https://arxiv.org/abs/2605.21780v1)
- **Measuring Cross-Modal Synergy: A Benchmark for VLM Explainability** — [arxiv_ai](https://arxiv.org/abs/2605.22168)
- **The Matching Principle: A Geometric Theory of Loss Functions for Nuisance-Robust Representation Learning** — [arxiv_lg](https://arxiv.org/abs/2605.22800v1)
- **EnCAgg: Enhanced Clustering Aggregation for Robust Federated Learning against Dynamic Model Poisoning** — [arxiv_cr](https://arxiv.org/abs/2605.22506v1)
- **CCLab: Adversarial Testing of Learning- and Non-Learning-Based Congestion Controllers** — [arxiv_cr](https://arxiv.org/abs/2605.21915v1)
- **AOP-Wiki EMOD 3.0: Data Model Expansions and Content Evaluation Framework for Using Agentic AI to Improve Integration between AOPs and New Approach Methodologies (NAMs)** — [arxiv_ai](https://arxiv.org/abs/2605.21645)
- **Investigating Concept Alignment Using Implausible Category Members** — [arxiv_ai](https://arxiv.org/abs/2605.21683)
- **A Causal Argumentation Method for Explainability of Machine Learning Models** — [arxiv_ai](https://arxiv.org/abs/2605.21758)
- **What Counts as AI Sycophancy? A Taxonomy and Expert Survey of a Fragmented Construct** — [arxiv_ai](https://arxiv.org/abs/2605.21778)
- **Implicit Safety Alignment from Crowd Preferences** — [arxiv_ai](https://arxiv.org/abs/2605.21822)
- **ECPO: Evidence-Coupled Policy Optimization for Evidence-Certified Candidate Ranking** — [arxiv_ai](https://arxiv.org/abs/2605.21993)
- **Evaluating Commercial AI Chatbots as News Intermediaries** — [arxiv_cl](https://arxiv.org/abs/2605.22785v1)
- **TimeGuard: Channel-wise Pool Training for Backdoor Defense in Time Series Forecasting** — [arxiv_cr](https://arxiv.org/abs/2605.22365v1)
- **QT-PUF: Quantum Tunneling Leakage Based PUF for Implantable IoMT Devices** — [arxiv_cr](https://arxiv.org/abs/2605.22113v1)
- **RADAR: Defending RAG Dynamically against Retrieval Corruption** — [arxiv_cr](https://arxiv.org/abs/2605.22041v1)
- **Lumberjack: Better Differentially Private Random Forests through Heavy Hitter Detection in Trees** — [arxiv_lg](https://arxiv.org/abs/2605.22756v1)
- **Proxy-Based Approximation of Shapley and Banzhaf Interactions** — [arxiv_lg](https://arxiv.org/abs/2605.22738v1)
- **Reading Task Failure Off the Activations: A Sparse-Feature Audit of GPT-2 Small on Indirect Object Identification** — [arxiv_lg](https://arxiv.org/abs/2605.22719v1)
- **SegCompass: Exploring Interpretable Alignment with Sparse Autoencoders for Enhanced Reasoning Segmentation** — [arxiv_lg](https://arxiv.org/abs/2605.22658v1)
- **Two is better than one: A Collapse-free Multi-Reward RLIF Training Framework** — [arxiv_cl](https://arxiv.org/abs/2605.22620v1)
- **Boundary-targeted Membership Inference Attacks on Safety Classifiers** — [arxiv_cl](https://arxiv.org/abs/2605.22373v1)
- **Modeling Pathology-Like Behavioral Patterns in Language Models Through Behavioral Fine-Tuning** — [arxiv_cl](https://arxiv.org/abs/2605.22356v1)
- **Optimal Guarantees for Auditing Rényi Differentially Private Machine Learning** — [arxiv_cr](https://arxiv.org/abs/2605.21938v1)
- **Adversarial Reframing: A Framework for Targeted Generation in Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.21674v1)
- **Near-Optimal Generalized Private Testing** — [arxiv_cr](https://arxiv.org/abs/2605.21601v1)
- **Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks** — [arxiv_cr](https://arxiv.org/abs/2605.21378v2)
- **Information Leakage Envelopes** — [arxiv_cr](https://arxiv.org/abs/2605.21185v1)
- **Benchmarking and Improving Monitors for Out-Of-Distribution Alignment Failure in LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.21602)
- **Latent-space Attacks for Refusal Evasion in Language Models** — [arxiv_ai](https://arxiv.org/abs/2605.21706)
- **AttuneBench: A Conversation-Based Benchmark for LLM Emotional Intelligence** — [arxiv_ai](https://arxiv.org/abs/2605.21739)
- **Who Uses AI? Platforms, Workforce, and AI Exposure** — [arxiv_ai](https://arxiv.org/abs/2605.21743)
- **Trace2Skill: Verifier-Guided Skill Evolution for Long-Context EDA Agents** — [arxiv_ai](https://arxiv.org/abs/2605.21810)
- **Planning in the LLM Era: Building for Reliability and Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.21902)
- **AI-Enabled Serious Games: Integrating Intelligence and Adaptivity in Training Systems** — [arxiv_ai](https://arxiv.org/abs/2605.21962)
- **A Camera-Cooperative ISAC Framework for Multimodal Non-Cooperative UAVs Sensing** — [arxiv_ai](https://arxiv.org/abs/2605.22090)
- **ArborKV: Structure-Aware KV Cache Management for Scaling Tree-based LLM Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.22106)
- **Efficient Agentic Reasoning Through Self-Regulated Simulative Planning** — [arxiv_ai](https://arxiv.org/abs/2605.22138)
- **Adapting the Interface, Not the Model: Runtime Harness Adaptation for Deterministic LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2605.22166)
- **LLM-Metrics: Measuring Research Impact Through Large Language Model Memory** — [arxiv_ai](https://arxiv.org/abs/2605.22176)
- **CLORE: Content-Level Optimization for Reasoning Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.22211)
- **Remember to be Curious: Episodic Context and Persistent Worlds for 3D Exploration** — [arxiv_lg](https://arxiv.org/abs/2605.22814v1)
- **LCGuard: Latent Communication Guard for Safe KV Sharing in Multi-Agent Systems** — [arxiv_lg](https://arxiv.org/abs/2605.22786v1)
- **Vector Policy Optimization: Training for Diversity Improves Test-Time Search** — [arxiv_cl](https://arxiv.org/abs/2605.22817v1)
- **TriSweep: A Four-Drone Swarm Framework for Electromagnetic Side-Channel Analysis** — [arxiv_cr](https://arxiv.org/abs/2605.22709v1)
- **A Formal Basis for Quantum Cryptographic Exposure Measurement under HNDL Threat** — [arxiv_cr](https://arxiv.org/abs/2605.22569v1)
- **A Constant-Time Implementation Methodology for Activation Functions on Microcontrollers** — [arxiv_cr](https://arxiv.org/abs/2605.22441v1)
- **Adversarial Trust Poisoning in Vehicular Collaborative Perception** — [arxiv_cr](https://arxiv.org/abs/2605.22122v1)
- **Safeguarding Text-to-Image Generative Models Against Unauthorized Knowledge Distillation** — [arxiv_cr](https://arxiv.org/abs/2605.22060v1)
- **Secure and Parallel Determinant Computation for Large-Scale Matrices in Edge Environments** — [arxiv_cr](https://arxiv.org/abs/2605.22039v1)
- **The Distillation Game: Adaptive Attacks & Efficient Defenses** — [arxiv_lg](https://arxiv.org/abs/2605.22737v1)
- **Post-Training is About States, Not Tokens: A State Distribution View of SFT, RL, and On-Policy Distillation** — [arxiv_lg](https://arxiv.org/abs/2605.22731v1)
- **Live Music Diffusion Models: Efficient Fine-Tuning and Post-Training of Interactive Diffusion Music Generators** — [arxiv_lg](https://arxiv.org/abs/2605.22717v1)
- **Abstraction for Offline Goal-Conditioned Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.22711v1)
- **The Secretary Problem with a Stochastic Precursor** — [arxiv_lg](https://arxiv.org/abs/2605.22653v1)
- **A note on convergence of Wasserstein policy optimization** — [arxiv_lg](https://arxiv.org/abs/2605.22622v1)
- **UNAD+: An Explainable Hybrid Framework for Unknown Network Attack Detection** — [arxiv_lg](https://arxiv.org/abs/2605.22621v1)
- **MoSA: Motion-constrained Stress Adaptation for Mitigating Real-to-Sim Gap in Continuum Dynamics via Learning Residual Anisotropy** — [arxiv_lg](https://arxiv.org/abs/2605.22597v1)
- **Factored Diffusion Policies:Compositionally Generalized Robot Control with a Single Score Network** — [arxiv_lg](https://arxiv.org/abs/2605.22596v1)
- **Reducing Political Manipulation with Consistency Training** — [arxiv_cl](https://arxiv.org/abs/2605.22771v1)
- **ChronoMedKG: A Temporally-Grounded Biomedical Knowledge Graph and Benchmark for Clinical Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.22734v1)
- **Beyond Acoustic Emotion Recognition: Multimodal Pathos Analysis in Political Speech Using LLM-Based and Acoustic Emotion Models** — [arxiv_cl](https://arxiv.org/abs/2605.22732v1)
- **AMEL: Accumulated Message Effects on LLM Judgments** — [arxiv_cl](https://arxiv.org/abs/2605.22714v1)
- **Self-Policy Distillation via Capability-Selective Subspace Projection** — [arxiv_cl](https://arxiv.org/abs/2605.22675v1)
- **Moral Semantics Survive Machine Translation: Cross-Lingual Evidence from Moral Foundations Corpora** — [arxiv_cl](https://arxiv.org/abs/2605.22660v1)
- **Boiling the Frog: A Multi-Turn Benchmark for Agentic Safety** — [arxiv_cl](https://arxiv.org/abs/2605.22643v1)
- **The Double Dilemma in Multi-Task Radiology Report Generation: A Gradient Dynamics Analysis and Solution** — [arxiv_cl](https://arxiv.org/abs/2605.22635v1)
- **Agentic CLEAR: Automating Multi-Level Evaluation of LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2605.22608v1)
- **LANG: Reinforcement Learning for Multilingual Reasoning with Language-Adaptive Hint Guidance** — [arxiv_cl](https://arxiv.org/abs/2605.22567v1)
- **One prompt is not enough: Instruction Sensitivity Undermines Embedding Model Evaluation** — [arxiv_cl](https://arxiv.org/abs/2605.22544v1)
- **SpaceDG: Benchmarking Spatial Intelligence under Visual Degradation** — [arxiv_cl](https://arxiv.org/abs/2605.22536v1)
- **Search-E1: Self-Distillation Drives Self-Evolution in Search-Augmented Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.22511v1)
- **Polite on the Surface, Wrong in Practice: A Curated Dataset for Fixing Honorific Failures in Multilingual Bangla Generation** — [arxiv_cl](https://arxiv.org/abs/2605.22487v1)
- **From Correlation to Cause: A Five-Stage Methodology for Feature Analysis in Transformer Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.22462v1)
- **Blind Spots in the Guard: How Domain-Camouflaged Injection Attacks Evade Detection in Multi-Agent LLM Systems** — [arxiv_cr](https://arxiv.org/abs/2605.22001v1)
- **SPIDER: Two Server Functionality for the Cost of Zero** — [arxiv_cr](https://arxiv.org/abs/2605.21857v1)
- **Forecasting Scientific Progress with Artificial Intelligence** — [huggingface_papers](https://arxiv.org/abs/2605.22681)
- **One Sentence, One Drama: Personalized Short-Form Drama Generation via Multi-Agent Systems** — [huggingface_papers](https://arxiv.org/abs/2605.22144)
- **Maestro: Reinforcement Learning to Orchestrate Hierarchical Model-Skill Ensembles** — [huggingface_papers](https://arxiv.org/abs/2605.22177)
- **Diversed Model Discovery via Structured Table Discovery** — [huggingface_papers](https://arxiv.org/abs/2605.22766)
- **Onion-Routed Multi-Circuit Key Establishment for Quantum-Resilient Sessions** — [arxiv_cr](https://arxiv.org/abs/2605.21349v1)
- **Integrable Elasticity via Neural Demand Potentials** — [arxiv_lg](https://arxiv.org/abs/2605.22820v1)
- **Finite-Particle Convergence Rates for Conservative and Non-Conservative Drifting Models** — [arxiv_lg](https://arxiv.org/abs/2605.22795v1)
- **MOSS: Self-Evolution through Source-Level Rewriting in Autonomous Agent Systems** — [arxiv_lg](https://arxiv.org/abs/2605.22794v1)
- **FAME: Failure-Aware Mixture-of-Experts for Message-Level Log Anomaly Detection** — [arxiv_lg](https://arxiv.org/abs/2605.22779v1)
- **FashionLens: Toward Versatile Fashion Image Retrieval via Task-Adaptive Learning** — [huggingface_papers](https://arxiv.org/abs/2605.22552)
- **SEGA: Spectral-Energy Guided Attention for Resolution Extrapolation in Diffusion Transformers** — [huggingface_papers](https://arxiv.org/abs/2605.22668)
- **DecQ: Detail-Condensing Queries for Enhanced Reconstruction and Generation in Representation Autoencoders** — [huggingface_papers](https://arxiv.org/abs/2605.22777)
- **LatentOmni: Rethinking Omni-Modal Understanding via Unified Audio-Visual Latent Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.22012)
- **Segment Anything with Motion, Geometry, and Semantic Adaptation for Complex Nonlinear Visual Object Tracking** — [huggingface_papers](https://arxiv.org/abs/2605.22538)
- **SceneAligner: 3D-Grounded Floorplan Localization in the Wild** — [huggingface_papers](https://arxiv.org/abs/2605.22581)
- **Sensor2Sensor: Cross-Embodiment Sensor Conversion for Autonomous Driving** — [huggingface_papers](https://arxiv.org/abs/2605.22809)
- **From Reasoning Chains to Verifiable Subproblems: Curriculum Reinforcement Learning Enables Credit Assignment for LLM Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.22074)
- **WorldKV: Efficient World Memory with World Retrieval and Compression** — [huggingface_papers](https://arxiv.org/abs/2605.22718)
- **Bernini: Latent Semantic Planning for Video Diffusion** — [huggingface_papers](https://arxiv.org/abs/2605.22344)
- **TerminalWorld: Benchmarking Agents on Real-World Terminal Tasks** — [huggingface_papers](https://arxiv.org/abs/2605.22535)
- **Spreadsheet-RL: Advancing Large Language Model Agents on Realistic Spreadsheet Tasks via Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.22642)
- **Gated DeltaNet-2: Decoupling Erase and Write in Linear Attention** — [huggingface_papers](https://arxiv.org/abs/2605.22791)
- **Swift Sampling: Selecting Temporal Surprises via Taylor Series** — [huggingface_papers](https://arxiv.org/abs/2605.22678)
- **ACC: Compiling Agent Trajectories for Long-Context Training** — [huggingface_papers](https://arxiv.org/abs/2605.21850)
- **RiT: Vanilla Diffusion Transformers Suffice in Representation Space** — [huggingface_papers](https://arxiv.org/abs/2605.21981)
- **Elon Musk can’t hear you over the sound of his $1.75 trillion IPO** — [techcrunch_ai](https://techcrunch.com/podcast/elon-musk-cant-hear-you-over-the-sound-of-his-1-75-trillion-ipo/)
- **We tried Google’s AI glasses and they’re almost there** — [techcrunch_ai](https://techcrunch.com/2026/05/22/we-tried-googles-ai-glasses-and-theyre-almost-there/)
- **SpaceX files to go public, and the math requires a little faith** — [techcrunch_ai](https://techcrunch.com/video/spacex-files-to-go-public-and-the-math-requires-a-little-faith/)
- **The Download: coding’s future, the ‘Steroid Olympics,’ and AI-driven science** — [mit_tech_review](https://www.technologyreview.com/2026/05/22/1137845/the-download-coding-future-steroid-olympics-ai-science/)
- **Google I/O showed how the path for AI-driven science is shifting** — [mit_tech_review](https://www.technologyreview.com/2026/05/22/1137813/google-i-o-showed-how-the-path-for-ai-science-is-shifting/)
- **The Enhanced Games fit right in with the rest of 2026’s longevity vibes** — [mit_tech_review](https://www.technologyreview.com/2026/05/22/1137753/the-enhanced-games-fit-right-in-with-the-rest-of-2026s-longevity-vibes/)
- **AI is being used to resurrect the voices of dead pilots** — [techcrunch_ai](https://techcrunch.com/2026/05/22/ai-is-being-used-to-resurrect-the-voices-of-dead-pilots/)
- **Google goes for the glitter with disco-ball icons: ‘Are y’all sure you still want this?’** — [techcrunch_ai](https://techcrunch.com/2026/05/22/google-goes-for-the-glitter-with-disco-ball-icons-are-yall-sure-you-still-want-this/)
- **How VCs and founders use inflated ‘ARR’ to crown AI startups** — [techcrunch_ai](https://techcrunch.com/2026/05/22/how-vcs-and-founders-use-inflated-arr-to-kingmake-ai-startups/)
- **Catch up on the Dialogues stage at Google I/O 2026.** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/io-2026-dialogues-recap/)
- **You can no longer Google the word ‘disregard’** — [techcrunch_ai](https://techcrunch.com/2026/05/22/you-can-no-longer-google-the-word-disregard/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **Emmimal/control-layer** — [github](https://github.com/Emmimal/control-layer)
- **wdnmd1265/ai-flow-architect** — [github](https://github.com/wdnmd1265/ai-flow-architect)
- **open-gsd/gsd-pi** — [github](https://github.com/open-gsd/gsd-pi)
- **gouravnagar-infosec/ai-kill-chain** — [github](https://github.com/gouravnagar-infosec/ai-kill-chain)
- **5bv57zcm44-max/NOXUS-AI-Open-WhatsApp** — [github](https://github.com/5bv57zcm44-max/NOXUS-AI-Open-WhatsApp)
- **ayush016/android-lead-agent-skills** — [github](https://github.com/ayush016/android-lead-agent-skills)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **kingbootoshi/directional-prompting** — [github](https://github.com/kingbootoshi/directional-prompting)
- **tuchg/Lucarne** — [github](https://github.com/tuchg/Lucarne)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **lywnl/ai-app-generation** — [github](https://github.com/lywnl/ai-app-generation)
- **nkzw-tech/cloudsail** — [github](https://github.com/nkzw-tech/cloudsail)
- **workos/auth.md** — [github](https://github.com/workos/auth.md)
- **h4ckf0r0day/awesome-ai-web-scraping** — [github](https://github.com/h4ckf0r0day/awesome-ai-web-scraping)
- **zhongweiv/hermes-edu-skills** — [github](https://github.com/zhongweiv/hermes-edu-skills)
- **hasanyilmaz/operon** — [github](https://github.com/hasanyilmaz/operon)
- **xuanlinAI/overmind** — [github](https://github.com/xuanlinAI/overmind)
- **XingYu-Zhong/DeepSeek-GUI** — [github](https://github.com/XingYu-Zhong/DeepSeek-GUI)
- **美团外卖前负责人入局餐饮具身模型，元节智能获千万级种子轮融资** — [qbitai](https://www.qbitai.com/2026/05/423159.html)
- **龙虾养不动了？周鸿祎给虾搭了个云端办公室，专业私教在线炼虾** — [qbitai](https://www.qbitai.com/2026/05/422811.html)
- **李飞飞再出手，空间智能的ImageNet来了** — [qbitai](https://www.qbitai.com/2026/05/422738.html)
- **融资700亿！DeepSeek Code真要来了，ACM金牌大神崔添翼挂帅** — [qbitai](https://www.qbitai.com/2026/05/422624.html)
- **狂揽F轮融资+拿下4100万用户！深圳玩家出手，把企业旧系统变成AI能力库** — [qbitai](https://www.qbitai.com/2026/05/422615.html)
- **中信证券：中国制罐企业有望获得更多全球市场拓展空间，逐步构建全球产能布局** — [36kr](https://36kr.com/newsflashes/3821373000077704?f=rss)
- **商务部：1-4月全国吸收外资2876.9亿元人民币** — [36kr](https://36kr.com/newsflashes/3821372272660615?f=rss)
- **36氪首发 | 北大项目孵化，国内首家原生机器人“大脑芯片”企业获数亿元融资** — [36kr](https://36kr.com/p/3821371042877575?f=rss)
- **短期态度转冷，国际投行下调黄金目标价** — [36kr](https://36kr.com/newsflashes/3821220090646657?f=rss)
- **传京东考虑20亿英镑竞购英国电商平台The Very Group** — [36kr](https://36kr.com/newsflashes/3821218974879878?f=rss)
- **本周机构调研热情不减，超三成机构调研股实现正收益** — [36kr](https://36kr.com/newsflashes/3821209183522952?f=rss)
- **用AI来管公司，Moka推出三款AI HR工具｜涌现新栏目** — [36kr](https://36kr.com/p/3819979202253189?f=rss)
- **Anthropic最快下周完成逾300亿美元融资轮** — [36kr](https://36kr.com/newsflashes/3821194878947715?f=rss)
- **9点1氪丨永辉超市向王健林等追债超36亿元；《柳叶刀》：全球近12亿人有精神障碍；微信回应“只能撤回2分钟内消息”** — [36kr](https://36kr.com/p/3821177784881541?f=rss)
- **氪星晚报｜优步与印度JSW集团达成协议，合作在印度开发及部署电动汽车；英伟达、AMD、英特尔参投，AI初创公司Hark完成7亿美元融资；神舟二十三号发射在即，各系统准备就绪** — [36kr](https://36kr.com/p/3816943010071427?f=rss)
- **AI时代核心终端生态定位与用户需求洞察| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3820318177841541?f=rss)
- **江行智能：从感知环境到改变世界：物理AI的机遇、路径与实践| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3820298219425924?f=rss)
- **小米YU7家族再推新车，雷军：标准版打特斯拉，GT版狙BBA** — [36kr](https://36kr.com/p/3817022407181188?f=rss)
- **让智能体看见世界：CV × AI Agent 的行业场景新实践| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3820220616495492?f=rss)
- **SpaceX IPO将包含散户配售** — [36kr](https://36kr.com/newsflashes/3821222961025157?f=rss)
- **星巴克叫停AI库存自动盘点工具：上线9个月，错误频出** — [36kr](https://36kr.com/newsflashes/3821221746266498?f=rss)
- **微软支付2.5亿美元了结动视暴雪股东诉讼** — [36kr](https://36kr.com/newsflashes/3821197911675268?f=rss)
- **英特尔推出混合AI解决方案SuperClaw，主打隐私安全与低成本** — [36kr](https://36kr.com/newsflashes/3821197146722696?f=rss)