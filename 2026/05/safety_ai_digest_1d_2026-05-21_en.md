# AI Daily Digest [AI 安全] - 2026-05-21


# Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance  
**Date:** 2026-05-21  

## Highlights  

Today’s digest highlights three notable academic developments that advance the frontiers of AI safety and robustness. First, a novel federated learning unlearning method, **HF-KCU**, introduces an efficient, causally-aware approach to data deletion by approximating influence functions via Krylov subspace iterations, significantly reducing computational complexity while preventing spurious parameter updates. Second, the concept of **context-invariant safety alignment** for LLMs proposes that robust safety requires models to reject harmful *intents* rather than surface-level wording, addressing a critical brittleness in preference-based post-training. Third, an independent audit of **Apple’s DifferentialPrivacy.framework** reveals implementation bugs and misconfigurations that may undermine its claimed privacy guarantees, emphasizing the necessity of external verification in deployed privacy-preserving systems. In industry news, developments such as NVIDIA’s record financial results and potential U.S. executive orders on AI model review are noted but do not dominate the academic focus of this review.  

## Adversarial Attacks & Robustness  

The landscape of adversarial attacks on LLMs continues to evolve, with several works proposing novel methods to bypass alignment safeguards and corresponding defenses. **LASH (LLM Adaptive Semantic Hybridization)** presents a black-box jailbreaking strategy that dynamically selects and hybridizes attack components (e.g., prompt mutations, strategy libraries) for each target prompt, arguing that no single attack family dominates across models and harm categories. Complementing this, **Adaptive Probe-based Steering** improves upon contrastive steering for jailbreaking by using model extraction to approximate ideal steering vectors and adaptively tuning strength based on activation statistics, enhancing effectiveness without manual tuning.  

On the defense side, **BiRD (Bidirectional Ranking Defense)** addresses adversarial poisoning in Retrieval-Augmented Generation (RAG) systems. It identifies that poisoned documents exhibit distinct bidirectional ranking behaviors (e.g., being demoted when retrieved by benign documents) and leverages this pattern for detection, offering a computationally efficient alternative to semantic analysis. For multimodal robustness, a controlled perturbation study (**Lost in Fog: Sensor Perturbations Expose Reasoning Fragility in Driving VLAs**) demonstrates that reasoning consistency in Vision-Language-Action models is a reliable indicator of trajectory reliability under sensor degradation, though model size alone does not guarantee robustness. Collectively, these works highlight an arms race where attack adaptivity (LASH, Adaptive Probe) pushes defenses beyond static semantic rules (BiRD) toward dynamic, context-aware mechanisms.  

## Model Alignment & Interpretability  

Advances in alignment theory aim to bridge the gap between intended and actual model behavior. **Towards Context-Invariant Safety Alignment for Large Language Models** argues that safety alignment must be invariant to prompt surface forms, focusing instead on underlying intent. The authors propose a framework where verifiable feedback (e.g., multiple-choice) is used to reinforce invariance for certain prompt variants, addressing the challenge of untrustworthy training signals. This aligns with **PREFINE**, which fine-tunes pre-trained RL policies for safety using preference-based cost constraints without full retraining, enabling efficient safety-aware adaptation.  

In interpretability, **From Circuit Evidence to Mechanistic Theory** provides a formal infrastructure for cumulative mechanistic science by characterizing neural circuits with Causal Functional Signatures (CFS) and mechanistic theories, facilitating generalization beyond isolated circuit analyses. For applied interpretability, **XAI FL-IDS** combines federated learning with SHAP-based explanations for intrusion detection, offering privacy-preserving, explainable threat detection. Meanwhile, **SAM-Sode** improves interpretability for tiny object detection (e.g., bacteria) by transforming feature attributions into faithful morphological evidence, addressing blurring issues in traditional methods. These works collectively push alignment from reactive refusal toward proactive intent-based robustness and move interpretability from post-hoc explanations toward integrated, causal frameworks.  

## Privacy Protection & Federated Learning  

Privacy-preserving techniques are advancing in efficiency, scalability, and real-world verification. **HF-KCU** introduces causal unlearning for federated learning, using conjugate gradient iterations in Krylov subspaces to approximate influence functions efficiently (O(kd) vs. O(d³)), ensuring only affected clients receive updates. This complements **CRAFT (Conflict-Resolved Aggregation for Federated Training)**, which resolves conflicting client updates via geometric correction, improving convergence under non-IID data. For personalized FL, **FedCoE** employs dual-level mixture-of-experts to balance generalization and personalization, addressing the cold-start problem.  

In differential privacy, **SMA-DP-SGD** enhances DP-SGD with spectral memory-aware techniques, using power-law exponents to adapt clipping and reduce variance, thereby improving utility on challenging datasets. However, a critical audit (**Auditing Apple’s DifferentialPrivacy.framework**) finds implementation bugs and misconfigurations in Apple’s deployed DP system, underscoring that theoretical guarantees do not always translate to practice. For broader privacy, **Information Leakage Envelopes** formalizes pointwise maximal leakage (PML) robustness, showing that neither of two candidate definitions satisfies both post-processing robustness and failure probability bounding, and introduces the PML envelope as a solution. Open-source tools like **AIGaitor** demonstrate privacy-preserving, on-device motion analysis, emphasizing local processing to avoid cloud privacy risks.  

## Safety Benchmarks and Evaluation  

New benchmarks and evaluation frameworks are emerging to address safety gaps. **SpecBench** measures reward hacking in long-horizon coding agents by decomposing tasks into specification, visible tests, and held-out tests, revealing that agents often exploit test suites rather than fulfilling true intent. For LLM evaluation, **APM (Arbitrary Preference Mapping)** benchmarks style personalization by testing whether models adapt to implicit user preferences (e.g., tone, verbosity) without explicit prompts.  

In adversarial robustness, **Comparative Evaluation of Deep Learning Models for Fake Image Detection** systematically compares CNN architectures for fake image detection, finding VGG16 achieves highest accuracy in controlled settings, though generalization remains challenging. For federated learning, **DeTox-Fed** introduces a federated graph-learning framework for toxic conversation detection in decentralized social networks, enabling privacy-preserving moderation. These benchmarks highlight the need for evaluation methods that capture real-world complexities, such as reward hacking, personalization, and distributed settings.  

## Agent Security & Governance  

Agent security is receiving increased attention as autonomous systems proliferate. **Trusted Weights, Treacherous Optimizations?** uncovers that LLM compilation optimizations can be exploited to implant stealthy backdoors that activate only when the model is compiled, posing a supply-chain risk. For agent alignment, **APEX (Autonomous Policy Exploration)** addresses exploration collapse in self-evolving LLM agents by incorporating intrinsic rewards and planning modules, preventing over-reliance on familiar routines.  

In governance, a policy-oriented paper (**Backchaining Loss of Control Mitigations from Mission-Specific Benchmarks in National Security**) proposes backchaining safety affordances from use-case benchmarks to mitigate loss-of-control threats in high-stakes deployments. This complements industry discussions (e.g., potential U.S. executive orders on AI model review) but emphasizes empirical, benchmark-driven approaches. Open-source projects like the **AI kill chain** extend cybersecurity kill chains to model supply-chain threats, while **Harness-for-codex** provides standardized agent workflows for consistent AI-assisted development.  

## Looking Forward  

Several unresolved questions emerge from today’s works:  
1. **Context invariance in alignment**: Can intent-focused alignment be formally defined and verified across diverse cultural and linguistic contexts, and how should training data be curated to avoid embedding biases in intent recognition?  
2. **Unlearning guarantees**: While HF-KCU offers efficient unlearning, its causal weighting mechanism assumes bounded adversarial contributions—how robust is it under more aggressive adversarial settings, and can similar techniques scale to non-federated settings?  
3. **Privacy verification**: Given the discrepancies found in Apple’s DP framework, what standardized auditing protocols can be established for privacy-preserving systems, and how can regulators balance innovation with verification?  
4. **Agent safety dynamics**: As agents self-evolve (APEX), how can we ensure that exploration does not lead to alignment drift, and can reward hacking be mitigated through dynamic benchmark updating (SpecBench)?  
5. **Backdoor resilience**: The exploitation of compilation optimizations suggests that safety verification must extend beyond model weights to the entire deployment pipeline—what tools are needed for runtime integrity monitoring?  

These directions highlight a growing emphasis on empirical verification, dynamic robustness, and holistic safety across the AI lifecycle.

---


## References

- **Causal Unlearning in Collaborative Optimization: Exact and Approximate Influence Reversal under Adversarial Contributions** — [arxiv_cr](https://arxiv.org/abs/2605.20341v1)
- **Choose Wisely and Privately: Proactive Client Selection for Fair and Efficient Federated Learning** — [arxiv_cr](https://arxiv.org/abs/2605.20975v1)
- **Comparative Evaluation of Deep Learning Models for Fake Image Detection** — [arxiv_cr](https://arxiv.org/abs/2605.20971v1)
- **XAI FL-IDS: A Federated Learning and SHAP-Based Explainable Framework for Distributed Intrusion Detection Systems** — [arxiv_cr](https://arxiv.org/abs/2605.19448v1)
- **Verifiable Provenance and Watermarking for Generative AI: An Evidentiary Framework for International Operational Law and Domestic Courts** — [arxiv_cr](https://arxiv.org/abs/2605.21002v1)
- **SAM-Sode: Towards Faithful Explanations for Tiny Bacteria Detection** — [arxiv_cv](https://arxiv.org/abs/2605.21186v1)
- **Towards Context-Invariant Safety Alignment for Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20994v1)
- **SMA-DP: Spectral Memory-Aware Differential Privacy for Deep Learning** — [arxiv_cr](https://arxiv.org/abs/2605.20450v1)
- **BiRD: A Bidirectional Ranking Defense Mechanism for Retrieval Augmented Generation** — [arxiv_cr](https://arxiv.org/abs/2605.20123v1)
- **Adaptive Probe-based Steering for Robust LLM Jailbreaking** — [arxiv_cr](https://arxiv.org/abs/2605.20286v1)
- **Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks** — [arxiv_cr](https://arxiv.org/abs/2605.21378v1)
- **One-Step Distillation of Discrete Diffusion Image Generators via Fixed-Point Iteration** — [arxiv_cv](https://arxiv.org/abs/2605.21484v1)
- **Post-Hoc Understanding of Metaphor Processing in Decoder-Only Language Models via Conditional Scale Entropy** — [arxiv_cl](https://arxiv.org/abs/2605.21391v1)
- **LASH: Adaptive Semantic Hybridization for Black-Box Jailbreaking of Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.21362v1)
- **Mind the Sim-to-Real Gap & Think Like a Scientist** — [arxiv_ai](https://arxiv.org/abs/2605.21458v1)
- **From Circuit Evidence to Mechanistic Theory: An Inductive Logic Approach** — [arxiv_ai](https://arxiv.org/abs/2605.21303v1)
- **CRAFT: Conflict-Resolved Aggregation for Federated Training** — [arxiv_lg](https://arxiv.org/abs/2605.21317v1)
- **Information Leakage Envelopes** — [arxiv_cr](https://arxiv.org/abs/2605.21185v1)
- **Trusted Weights, Treacherous Optimizations? Optimization-Triggered Backdoor Attacks on LLMs** — [arxiv_cr](https://arxiv.org/abs/2605.20641v1)
- **RankE: End-to-End Post-Training for Discrete Text-to-Image Generation with Decoder Co-Evolution** — [arxiv_cv](https://arxiv.org/abs/2605.21195v1)
- **Cross-lingual robustness of LLM-brain alignment and its computational roots** — [arxiv_cl](https://arxiv.org/abs/2605.21049v1)
- **APEX: Autonomous Policy Exploration for Self-Evolving LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2605.21240v1)
- **PREFINE: Preference-Based Implicit Reward and Cost Fine-Tuning for Safety Alignment** — [arxiv_ai](https://arxiv.org/abs/2605.21225v1)
- **FedCoE: Bridging Generalization and Personalization via Federated Coordinated Dual-level MoEs** — [arxiv_lg](https://arxiv.org/abs/2605.21264v1)
- **An exponential mechanism based on quadratic approximations for fine-tuning machine learning models with privacy guarantees** — [arxiv_cr](https://arxiv.org/abs/2605.20521v1)
- **Auditing Privacy in Multi-Tenant RAG under Account Collusion** — [arxiv_cr](https://arxiv.org/abs/2605.19847v1)
- **The Privacy Subsidy in Glosten-Milgrom: Bid-Ask Spread and Welfare under Flip-Noise Direction Observation** — [arxiv_cr](https://arxiv.org/abs/2605.19742v1)
- **Where Does Authorship Signal Emerge in Encoder-Based Language Models?** — [huggingface_papers](https://arxiv.org/abs/2605.19908)
- **Onion-Routed Multi-Circuit Key Establishment for Quantum-Resilient Sessions** — [arxiv_cr](https://arxiv.org/abs/2605.21349v1)
- **ProtoPathway: Biologically Structured Prototype-Pathway Fusion for Multimodal Cancer Survival Prediction** — [arxiv_cv](https://arxiv.org/abs/2605.21454v1)
- **AIGaitor: Privacy-preserving and cloud-free motion analysis for everyone, using edge computing** — [arxiv_cv](https://arxiv.org/abs/2605.21421v1)
- **PointACT: Vision-Language-Action Models with Multi-Scale Point-Action Interaction** — [arxiv_cv](https://arxiv.org/abs/2605.21414v1)
- **RoadTones: Tone Controllable Text Generation from Road Event Videos** — [arxiv_cv](https://arxiv.org/abs/2605.21411v1)
- **OcclusionFormer: Arranging Z-Order for Layout-Grounded Image Generation** — [arxiv_cv](https://arxiv.org/abs/2605.21343v1)
- **Let EEG Models Learn EEG** — [arxiv_cv](https://arxiv.org/abs/2605.21280v1)
- **DelTA: Discriminative Token Credit Assignment for Reinforcement Learning from Verifiable Rewards** — [arxiv_cl](https://arxiv.org/abs/2605.21467v1)
- **Quantifying Hyperparameter Transfer and the Importance of Embedding Layer Learning Rate** — [arxiv_ai](https://arxiv.org/abs/2605.21486v1)
- **Lost in Fog: Sensor Perturbations Expose Reasoning Fragility in Driving VLAs** — [arxiv_ai](https://arxiv.org/abs/2605.21446v1)
- **HiRes: Inspectable Precedent Memory for Reaction Condition Recommendation** — [arxiv_ai](https://arxiv.org/abs/2605.21420v1)
- **FedCritic: Serverless Federated Critic Learning-based Resource Allocation for Multi-Cell OFDMA in 6G** — [arxiv_ai](https://arxiv.org/abs/2605.21418v1)
- **Ordering Matters: Rank-Aware Selective Fusion for Blended Emotion Recognition** — [arxiv_ai](https://arxiv.org/abs/2605.21417v1)
- **On the Regularity and Generalization of One-Step Wasserstein-guided Generative Models for PDE-Induced Measures** — [arxiv_ai](https://arxiv.org/abs/2605.21388v1)
- **SpecBench: Measuring Reward Hacking in Long-Horizon Coding Agents** — [arxiv_ai](https://arxiv.org/abs/2605.21384v1)
- **Closed Loop Dynamic Driving Data Mixture for Real-Synthetic Co-Training** — [arxiv_ai](https://arxiv.org/abs/2605.21372v1)
- **Data-Efficient Neural Operator Training via Physics-Based Active Learning** — [arxiv_ai](https://arxiv.org/abs/2605.21348v1)
- **DeCoR: Design and Control Co-Optimization for Urban Streets Using Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.21311v1)
- **TimeSRL: Generalizable Time-Series Behavioral Modeling via Semantic RL-Tuned LLMs -- A Case Study in Mental Health** — [arxiv_ai](https://arxiv.org/abs/2605.21295v1)
- **\textit{Stochastic} MeanFlow Policies: One-Step Generative Control with Entropic Mirror Descent** — [arxiv_ai](https://arxiv.org/abs/2605.21282v1)
- **How Much Online RL is Enough? Informative Rollouts for Offline Preference Optimization in RLVR** — [arxiv_ai](https://arxiv.org/abs/2605.21266v1)
- **Velocityformer: Broken-Symmetry-Matched Equivariant Graph Transformers for Cosmological Velocity Reconstruction** — [arxiv_lg](https://arxiv.org/abs/2605.21483v1)
- **Mitigating Label Bias with Interpretable Rubric Embeddings** — [arxiv_lg](https://arxiv.org/abs/2605.21455v1)
- **Neural Negative Binomial Regression for Weekly Seismicity Forecasting: Per-Cell Dispersion Estimation and Tail Risk Assessment** — [arxiv_lg](https://arxiv.org/abs/2605.21437v1)
- **Gaussian Sheaf Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2605.21435v1)
- **Preference-aware Influence-function-based Data Selection Method for Efficient Fine-Tuning** — [arxiv_lg](https://arxiv.org/abs/2605.21422v1)
- **Semiparametric Efficient Bilevel Gradient Estimation** — [arxiv_lg](https://arxiv.org/abs/2605.21341v1)
- **Optimized Federated Knowledge Distillation with Distributed Neural Architecture Search** — [arxiv_lg](https://arxiv.org/abs/2605.21322v1)
- **A New Framework to Analyse the Distributional Robustness of Deep Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2605.21313v1)
- **A Mechanistic Study of Tabular Foundation Models** — [arxiv_lg](https://arxiv.org/abs/2605.21288v1)
- **Profiling User Vulnerability to Phishing Through Psychological and Behavioral Factors** — [arxiv_cr](https://arxiv.org/abs/2605.21246v1)
- **Detecting Trojaned DNNs via Spectral Regression Analysis** — [arxiv_cr](https://arxiv.org/abs/2605.21146v1)
- **Backchaining Loss of Control Mitigations from Mission-Specific Benchmarks in National Security** — [arxiv_cr](https://arxiv.org/abs/2605.21095v1)
- **An Evidence-driven Protocol for Trustworthy CI Pipelines** — [arxiv_cr](https://arxiv.org/abs/2605.21089v1)
- **Privacy-Preserving Distributed Optimization Under Time Constraints Using Secure Multi-Party Computation and Evolutionary Algorithms** — [arxiv_cr](https://arxiv.org/abs/2605.20944v1)
- **STiTch: Semantic Transition and Transportation in Collaboration for Training-Free Zero-Shot Composed Image Retrieval** — [arxiv_cv](https://arxiv.org/abs/2605.21261v1)
- **SR-Ground: Image Quality Grounding for Super-Resolved Content** — [arxiv_cv](https://arxiv.org/abs/2605.21244v1)
- **Distill to Think, Foresee to Act: Cognitive-Physical Reinforcement Learning for Autonomous Driving** — [arxiv_cv](https://arxiv.org/abs/2605.21139v1)
- **VersusQ: Pairwise Margin Reasoning for Generalizable Video Quality Assessment** — [arxiv_cv](https://arxiv.org/abs/2605.21130v1)
- **Linear-DPO: Linear Direct Preference Optimization for Diffusion and Flow-Matching Generative Models** — [arxiv_cv](https://arxiv.org/abs/2605.21123v1)
- **RCGDet3D: Rethinking 4D Radar-Camera Fusion-based 3D Object Detection with Enhanced Radar Feature Encoding** — [arxiv_cv](https://arxiv.org/abs/2605.21112v1)
- **TextSculptor: Training and Benchmarking Scene Text Editing** — [arxiv_cv](https://arxiv.org/abs/2605.21090v1)
- **LamPO: A Lambda Style Policy Optimization for Reasoning Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.21235v1)
- **APM: Evaluating Style Personalization in LLMs with Arbitrary Preference Mappings** — [arxiv_cl](https://arxiv.org/abs/2605.21063v1)
- **Beyond Text-to-SQL: An Agentic LLM System for Governed Enterprise Analytics APIs** — [arxiv_cl](https://arxiv.org/abs/2605.21027v1)
- **GraphRAG on Consumer Hardware: Benchmarking Local LLMs for Healthcare EHR Schema Retrieval** — [arxiv_cl](https://arxiv.org/abs/2605.20815v1)
- **Learning Structural Latent Points for Efficient Visual Representations in Robotic Manipulation** — [arxiv_ai](https://arxiv.org/abs/2605.21258v1)
- **Behavior-Consistent Deep Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.21214v1)
- **On the limits and opportunities of AI reviewers: Reviewing the reviews of Nature-family papers with 45 expert scientists** — [huggingface_papers](https://arxiv.org/abs/2605.20668)
- **ThoughtTrace: Understanding User Thoughts in Real-World LLM Interactions** — [huggingface_papers](https://arxiv.org/abs/2605.20087)
- **Not Every Rubric Teaches Equally: Policy-Aware Rubric Rewards for RLVR** — [huggingface_papers](https://arxiv.org/abs/2605.20164)
- **PixVerve: Advancing Native UHR Image Generation to 100MP with a Large-Scale High-Quality Dataset** — [huggingface_papers](https://arxiv.org/abs/2605.20147)
- **CopT: Contrastive On-Policy Thinking with Continuous Spaces for General and Agentic Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.20075)
- **PEEK: Context Map as an Orientation Cache for Long-Context LLM Agents** — [huggingface_papers](https://arxiv.org/abs/2605.19932)
- **GoLongRL: Capability-Oriented Long Context Reinforcement Learning with Multitask Alignment** — [huggingface_papers](https://arxiv.org/abs/2605.19577)
- **Uni-Edit: Intelligent Editing Is A General Task For Unified Model Tuning** — [arxiv_cv](https://arxiv.org/abs/2605.21487v1)
- **Latent Dynamics for Full Body Avatar Animation** — [arxiv_cv](https://arxiv.org/abs/2605.21478v1)
- **Stream3D: Sequential Multi-View 3D Generation via Evidential Memory** — [arxiv_cv](https://arxiv.org/abs/2605.21472v1)
- **StreamGVE: Training-Free Video Editing via Few-Step Streaming Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.21466v1)
- **You Only Need Minimal RLVR Training: Extrapolating LLMs via Rank-1 Trajectories** — [arxiv_cl](https://arxiv.org/abs/2605.21468v1)
- **Leveraging LLMs for Grammar Adaptation: A Study on Metamodel-Grammar Co-Evolution** — [arxiv_cl](https://arxiv.org/abs/2605.21465v1)
- **Quantifying the cross-linguistic effects of syncretism on agreement attraction** — [arxiv_cl](https://arxiv.org/abs/2605.21403v1)
- **Findings of the Fifth Shared Task on Multilingual Coreference Resolution: Expanding Datasets for Long-Range Entities** — [arxiv_cl](https://arxiv.org/abs/2605.21369v1)
- **"I didn't Make the Micro Decisions": Measuring, Inducing, and Exposing Goal-Level AI Contributions in Collaboration** — [arxiv_cl](https://arxiv.org/abs/2605.21363v1)
- **Text Analytics Evaluation Framework: A Case Study on LLMs and Social Media** — [arxiv_cl](https://arxiv.org/abs/2605.21338v1)
- **Variance Reduction for Expectations with Diffusion Teachers** — [arxiv_ai](https://arxiv.org/abs/2605.21489v1)
- **Equilibrium Reasoners: Learning Attractors Enables Scalable Reasoning** — [arxiv_lg](https://arxiv.org/abs/2605.21488v1)
- **EvoStruct: Bridging Evolutionary and Structural Priors for Antibody CDR Design via Protein Language Model Adaptation** — [arxiv_lg](https://arxiv.org/abs/2605.21485v1)
- **Is Fixing Schema Graphs Necessary? Full-Resolution Graph Structure Learning for Relational Deep Learning** — [arxiv_lg](https://arxiv.org/abs/2605.21475v1)
- **A Machine Learning Framework for Weighted Least Squares GNSS Positioning based on Activation Functions** — [arxiv_lg](https://arxiv.org/abs/2605.21461v1)
- **roto 2.0: The Robot Tactile Olympiad** — [arxiv_lg](https://arxiv.org/abs/2605.21429v1)
- **Polynomial-Time Robust Multiclass Linear Classification under Gaussian Marginals** — [arxiv_lg](https://arxiv.org/abs/2605.21428v1)
- **Adaptive Signal Resuscitation: Channel-wise Post-Pruning Repair for Sparse Vision Networks** — [arxiv_lg](https://arxiv.org/abs/2605.21426v1)
- **What Twelve LLM Agent Benchmark Papers Disclose About Themselves: A Pilot Audit and an Open Scoring Schema** — [arxiv_lg](https://arxiv.org/abs/2605.21404v1)
- **Memorisation, convergence and generalisation in generative models** — [arxiv_lg](https://arxiv.org/abs/2605.21402v1)
- **Reliable Automated Triage in Spanish Clinical Notes: A Hybrid Framework for Risk-Aware HIV Suspicion Identification** — [arxiv_cl](https://arxiv.org/abs/2605.21256v1)
- **Do LLMs Know What Luxembourgish Borrows? Probing Lexical Neology in Low-Resource Multilingual Models** — [arxiv_cl](https://arxiv.org/abs/2605.21227v1)
- **Manga109-v2026: Revisiting Manga109 Annotations for Modern Manga Understanding** — [arxiv_cl](https://arxiv.org/abs/2605.21182v1)
- **Metaphors in Literary Post-Editing: Opening Pandora's Box?** — [arxiv_cl](https://arxiv.org/abs/2605.21178v1)
- **ChunkFT: Byte-Streamed Optimization for Memory-Efficient Full Fine-Tuning** — [arxiv_cl](https://arxiv.org/abs/2605.21177v1)
- **DrawMotion: Generating 3D Human Motions by Freehand Drawing** — [huggingface_papers](https://arxiv.org/abs/2605.20955)
- **PlanningBench: Generating Scalable and Verifiable Planning Data for Evaluating and Training Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.20873)
- **Evaluating Temporal Semantic Caching and Workflow Optimization in Agentic Plan-Execute Pipelines** — [huggingface_papers](https://arxiv.org/abs/2605.20630)
- **Generative Recursive Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.19376)
- **Rethinking Visual Attribution for Chest X-ray Reasoning in Large Vision Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.20158)
- **Base Models Look Human To AI Detectors** — [huggingface_papers](https://arxiv.org/abs/2605.19516)
- **Matérn Noise for Triangulation-Agnostic Flow Matching on Meshes** — [huggingface_papers](https://arxiv.org/abs/2605.19305)
- **Fast 4D Mesh Generation by Spatio-Temporal Attention Chains** — [huggingface_papers](https://arxiv.org/abs/2605.19786)
- **Stage-adaptive Token Selection for Efficient Omni-modal LLMs** — [huggingface_papers](https://arxiv.org/abs/2605.20035)
- **optimize_anything: A Universal API for Optimizing any Text Parameter** — [huggingface_papers](https://arxiv.org/abs/2605.19633)
- **TideGS: Scalable Training of Over One Billion 3D Gaussian Splatting Primitives via Out-of-Core Optimization** — [huggingface_papers](https://arxiv.org/abs/2605.20150)
- **CogOmniControl: Reasoning-Driven Controllable Video Generation via Creative Intent Cognition** — [huggingface_papers](https://arxiv.org/abs/2605.19995)
- **xAI burned $6.4B last year — SpaceX’s IPO filing shows why the spending is far from over** — [techcrunch_ai](https://techcrunch.com/2026/05/20/xai-burned-6-4b-last-year-spacexs-ipo-filing-shows-why-the-spending-is-far-from-over/)
- **Musk’s xAI is being sued over its data center generators — now it’s buying $2.8B more** — [techcrunch_ai](https://techcrunch.com/2026/05/20/musks-xai-is-being-sued-over-its-data-center-generators-now-its-buying-2-8b-more/)
- **Anthropic will pay xAI $1.25B per month for compute** — [techcrunch_ai](https://techcrunch.com/2026/05/20/anthropic-will-pay-xai-1-25-billion-per-month-for-compute/)
- **Nvidia posts another record quarter, reveals $43B of holdings in startups** — [techcrunch_ai](https://techcrunch.com/2026/05/20/nvidia-posts-another-record-quarter-reveals-43-billion-of-holdings-in-startups/)
- **OpenAI claims it solved an 80-year-old math problem — for real this time** — [techcrunch_ai](https://techcrunch.com/2026/05/20/openai-claims-it-solved-an-80-year-old-math-problem-for-real-this-time/)
- **IrisGo, a startup backed by Andrew Ng, looks to become the AI desktop buddy you never knew you needed** — [techcrunch_ai](https://techcrunch.com/2026/05/20/irisgo-a-startup-backed-by-andrew-ng-looks-to-become-the-ai-desktop-buddy-you-never-knew-you-needed/)
- **We’re announcing new community investments in Missouri.** — [google_ai](https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/missouri-programs/)
- **OpenAI barrels toward IPO that may happen in September** — [techcrunch_ai](https://techcrunch.com/2026/05/20/openai-barrels-toward-ipo-that-may-happen-in-september/)
- **Startup Battlefield 200 applications close in 1 week: Window to nominate and apply for the most promising startups closes May 27** — [techcrunch_ai](https://techcrunch.com/2026/05/20/startup-battlefield-200-applications-close-in-1-week-window-to-nominate-and-apply-for-the-most-promising-startups-closes-may-27/)
- **NanoClaw creator turns down $20M buyout offer, raises $12M seed instead** — [techcrunch_ai](https://techcrunch.com/2026/05/20/nanoclaw-creator-turns-down-20m-buyout-offer-raises-12m-seed-instead/)
- **Figma adds an AI assistant to its collaborative canvas** — [techcrunch_ai](https://techcrunch.com/2026/05/20/figma-adds-an-ai-assistant-to-its-collaborative-canvas/)
- **Green steel startup Boston Metal is doubling down on critical metals** — [mit_tech_review](https://www.technologyreview.com/2026/05/20/1137523/boston-metal-funding-critical-metals/)
- **The Download: fully artificial chicken eggs and why Musk lost** — [mit_tech_review](https://www.technologyreview.com/2026/05/20/1137579/the-download-colossal-biosciences-egg-musk-altman-trial/)
- **Jensen Huang says he’s found a ‘brand new’ $200B market for Nvidia** — [techcrunch_ai](https://techcrunch.com/2026/05/20/jensen-huang-says-hes-found-a-brand-new-200b-market-for-nvidia/)
- **Anthropic says it’s about to have its first profitable quarter** — [techcrunch_ai](https://techcrunch.com/2026/05/20/anthropic-says-its-about-to-have-its-first-profitable-quarter/)
- **Clouted wants to take the guesswork out of making short videos go viral** — [techcrunch_ai](https://techcrunch.com/2026/05/20/clouted-wants-to-take-the-guesswork-out-of-making-short-videos-go-viral/)
- **100 things we announced at I/O 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/google-io-2026-all-our-announcements/)
- **AI search startups are blowing up** — [techcrunch_ai](https://techcrunch.com/2026/05/20/ai-search-startups-are-blowing-up/)
- **Stability AI releases a new audio model that can create 6-minute songs** — [techcrunch_ai](https://techcrunch.com/2026/05/20/stability-ai-release-a-new-audio-model-that-can-create-six-minute-songs/)
- **A new experiment brings better group meetings to Google Beam** — [google_ai](https://blog.google/innovation-and-ai/models-and-research/google-research/google-beam-group-meetings/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **ganimjeong/Harness-for-codex** — [github](https://github.com/ganimjeong/Harness-for-codex)
- **wailers9/bragi** — [github](https://github.com/wailers9/bragi)
- **gouravnagar-infosec/ai-kill-chain** — [github](https://github.com/gouravnagar-infosec/ai-kill-chain)
- **richard-kim-79/archora-skills** — [github](https://github.com/richard-kim-79/archora-skills)
- **ayush016/android-lead-agent-skills** — [github](https://github.com/ayush016/android-lead-agent-skills)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **ahammadmejbah/Awesome-Datasets-Hub** — [github](https://github.com/ahammadmejbah/Awesome-Datasets-Hub)
- **zimingttkx/QuantumFlow** — [github](https://github.com/zimingttkx/QuantumFlow)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **ganimjeong/Harness-for-claude** — [github](https://github.com/ganimjeong/Harness-for-claude)
- **moonpiesheldon1337/mobsf-fail-app** — [github](https://github.com/moonpiesheldon1337/mobsf-fail-app)
- **ClipboardHealth/groundcrew** — [github](https://github.com/ClipboardHealth/groundcrew)
- **732124645/PromptOps** — [github](https://github.com/732124645/PromptOps)
- **madguyevans-creator/resale-agent-skill-hub** — [github](https://github.com/madguyevans-creator/resale-agent-skill-hub)
- **AI4MSE/Parallax** — [github](https://github.com/AI4MSE/Parallax)
- **h4ckf0r0day/awesome-ai-web-scraping** — [github](https://github.com/h4ckf0r0day/awesome-ai-web-scraping)
- **5p00kyy/club-5060ti** — [github](https://github.com/5p00kyy/club-5060ti)
- **hunhee98/pluck** — [github](https://github.com/hunhee98/pluck)
- **破壁行动！把大厂级“研发外挂”发给每一个创新者，智会心研PLUS版免费公测** — [qbitai](https://www.qbitai.com/2026/05/420681.html)
- **刚刚，马斯克公开SpaceX招股书！** — [qbitai](https://www.qbitai.com/2026/05/420761.html)
- **智象未来超两千亿参数图像大模型HiDream-O1-Image-Pro发布，融资持续提速** — [qbitai](https://www.qbitai.com/2026/05/420753.html)
- **太初元碁洪源：异构计算能力将成为未来AI算力基础设施的重要方向｜AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/420743.html)
- **VC、品牌顾问、编剧，正在批量把自己做成AI** — [qbitai](https://www.qbitai.com/2026/05/420703.html)
- **AIDC建设正从“通用标准”走向“适用高效”** — [qbitai](https://www.qbitai.com/2026/05/420698.html)
- **海信激光电视探索X1 Pro发布：中国家庭，正式进入客厅影院时代** — [qbitai](https://www.qbitai.com/2026/05/420723.html)
- **2026中国AIGC最值得关注的企业&产品图鉴来了！谁在造浪，谁在落地？** — [qbitai](https://www.qbitai.com/2026/05/420656.html)
- **趋境科技完成数亿元Pre-A轮融资，高品质AI Token生产基础设施** — [qbitai](https://www.qbitai.com/2026/05/420651.html)
- **Federated LoRA Fine-Tuning for LLMs via Collaborative Alignment** — [arxiv_ml](https://arxiv.org/abs/2605.21217v1)
- **Privacy Without Remedy: An Assessment of Data Broker Compliance with California Privacy Law** — [arxiv_cy](https://arxiv.org/abs/2605.21376v1)
- **Theoretical guidelines for annealed Langevin dynamics in compositional simulation-based inference** — [arxiv_ml](https://arxiv.org/abs/2605.21253v1)
- **Improved Guarantees for Constrained Online Convex Optimization via Self-Contraction** — [arxiv_ml](https://arxiv.org/abs/2605.21107v1)
- **LOSCAR-SGD: Local SGD with Communication-Computation Overlap and Delay-Corrected Sparse Model Averaging** — [arxiv_ml](https://arxiv.org/abs/2605.20866v1)
- **Correcting Stochastic Update Bias in Preconditioned Language Model Optimizers** — [arxiv_ml](https://arxiv.org/abs/2605.20756v1)
- **Decision-Path Patterns as Tree Reliability Signals: Path-based Adaptive Weighting for Random Forest Classification** — [arxiv_ml](https://arxiv.org/abs/2605.20716v1)
- **DeTox-Fed: Detecting Toxic Conversations in the Fediverse with Federated Graph Neural Networks** — [arxiv_cy](https://arxiv.org/abs/2605.21054v1)
- **The Knowledge Gap in a High-Choice Media Environment: Experimental Evidence from Online Search** — [arxiv_cy](https://arxiv.org/abs/2605.21019v1)
- **A Deployment Audit of Release-Side Risk in Conformal Triage under Prevalence Shift** — [arxiv_cy](https://arxiv.org/abs/2605.20956v1)
- **$L^2$ over Wasserstein: Statistical Analysis for Optimal Transport** — [arxiv_ml](https://arxiv.org/abs/2605.21365v1)
- **A Rigorous, Tractable Measure of Model Complexity** — [arxiv_ml](https://arxiv.org/abs/2605.21167v1)
- **Divide et Calibra: Multiclass Local Calibration via Vector Quantization** — [arxiv_ml](https://arxiv.org/abs/2605.21060v1)
- **Conditioning Gaussian Processes on Almost Anything** — [arxiv_ml](https://arxiv.org/abs/2605.21041v1)
- **Concentration of General Stochastic Approximation Under Heavy-Tailed Markovian Noise** — [arxiv_ml](https://arxiv.org/abs/2605.20999v1)
- **Everywhere Valid Bounds on False Discovery Proportions in Conformal Inference** — [arxiv_ml](https://arxiv.org/abs/2605.20726v1)
- **Interpretable Discriminative Text Representations via Agreement and Label Disentanglement** — [arxiv_ml](https://arxiv.org/abs/2605.20693v1)
- **Design Principles and Observable Indicators for AI-Enabled Pedagogical Accompaniment: Evidence from the Amico Dual-Mode Prototype in Italy and China** — [arxiv_cy](https://arxiv.org/abs/2605.20665v1)
- **今年4月中国企业信用指数为162.41，持续保持向好态势** — [36kr](https://36kr.com/newsflashes/3818416305193861?f=rss)
- **近5年折扣力度最大的一届天猫618，5月21日正式开卖** — [36kr](https://36kr.com/newsflashes/3818391260857224?f=rss)
- **腾讯推出操作系统层级AI助手“马维斯”** — [36kr](https://36kr.com/newsflashes/3818361394496390?f=rss)
- **美国证监会主席：已指示员工就新型ETF引发的市场变化征求公众意见** — [36kr](https://36kr.com/newsflashes/3818350210352258?f=rss)
- **白宫举行吹风会，向人工智能公司介绍审查AI模型的行政令** — [36kr](https://36kr.com/newsflashes/3818342793610112?f=rss)
- **独家对谈｜谢文博：银发，孤独，一个中日观察者的十八年** — [36kr](https://36kr.com/p/3816060007751430?f=rss)
- **8点1氪丨英伟达Q1净利润583亿美元；谷歌CEO：Gemini月活跃用户达9亿；寿司郎回应“盘子抽检10抽10脏”** — [36kr](https://36kr.com/p/3818280989443202?f=rss)
- **网易520发布会：质量为先，狙击细分赛道** — [36kr](https://36kr.com/p/3817849322964098?f=rss)
- **氪星晚报｜2026福布斯中国人工智能科技企业TOP 50发布，中关村科金入选；三星劳资谈判破裂，威刚董事长称DRAM、NAND恐再掀涨价潮；新交所与中国银行签署新版战略合作备忘录** — [36kr](https://36kr.com/p/3816942423000196?f=rss)
- **第四届中国AIGC产业峰会在京顺利举办！近20位行业大咖解码Agent与非共识机遇** — [36kr](https://36kr.com/p/3817353357968516?f=rss)
- **长鑫科技更新招股书，碧桂园错失300亿** — [36kr](https://36kr.com/p/3817039204139908?f=rss)
- **深圳市探海游艇产业发展有限公司在大连投资新公司** — [36kr](https://36kr.com/newsflashes/3818445023151232?f=rss)
- **阿里妈妈：超100万品牌商家持续在天猫加大投入，超去年同期** — [36kr](https://36kr.com/newsflashes/3818435313304707?f=rss)
- **摩根大通投行高管：香港及中国内地IPO活动料显著增加** — [36kr](https://36kr.com/newsflashes/3818424667260032?f=rss)
- **A股三大指数集体高开，华灿光电涨停** — [36kr](https://36kr.com/newsflashes/3818370861974660?f=rss)