# AI Daily Digest [AI 安全] - 2026-05-22


# AI Safety Daily Digest: Thematic Review for 2026-05-22

## Highlights

Today's research landscape presents significant advances in understanding and mitigating risks at the intersection of AI systems, security, and human values. Three developments stand out for their novel methodological contributions and implications for the field.

First, a critical examination of standard practices reveals hidden vulnerabilities. The paper **Trusted Weights, Treacherous Optimizations? Optimization-Triggered Backdoor Attacks on LLMs** unveils how common inference optimizations, like compiler-based graph transformations, can be maliciously exploited to implant stealthy backdoors without altering the model's weights, challenging the assumption of semantic equivalence in deployment pipelines. Second, a foundational work in agent security reframes the problem at a systemic level. **Agent Security is a Systems Problem** argues convincingly that treating the AI model as an untrusted component and enforcing security invariants at the system level—drawing from cybersecurity principles in operating systems and networks—is essential, complementing rather than replacing model robustness research. Third, a rigorous theoretical analysis clarifies a popular alignment technique. **Conditional Equivalence of DPO and RLHF** demonstrates that the presumed equivalence between Direct Preference Optimization and Reinforcement Learning from Human Feedback is conditional on an often-violated assumption, revealing a fundamental divergence in their optimization targets that can lead to pathological policy convergence.

## Adversarial Attacks & Robustness

Research today probes robustness from multiple angles, from quantum systems to the optimization processes underlying model deployment. The systematization in **SoK: Critical Evaluation of Quantum Machine Learning for Adversarial Robustness** provides the first comprehensive threat model analysis for QML, combining conceptual organization with empirical evaluation. Its finding that quantum models do not offer inherent adversarial robustness challenges optimistic narratives about quantum advantage in security-sensitive domains. Meanwhile, the attack vector uncovered in **Trusted Weights, Treacherous Optimizations?** represents a paradigm shift: by exploiting numerical side effects of compilation, adversaries can flip predictions for specific inputs or associate triggers with target outputs, all while maintaining a "trusted" model weight file. This complements traditional data poisoning or fine-tuning attacks and necessitates auditing of the entire optimization toolchain.

On the defensive side, **SDM: A Powerful Tool for Evaluating Model Robustness** addresses a key bottleneck in evaluation. It identifies the problem of "high-loss non-adversarial examples" degrading attack performance and proposes a reconstructed objective focused on maximizing the probability gap between incorrect classes. This methodological innovation should lead to more reliable robustness benchmarks. Furthermore, **Mind Your Margin and Boundary** critiques existing robust dataset distillation methods for a poor accuracy-robustness trade-off, attributing it to uniform treatment of adversarial examples and a lack of explicit inter-class separation. Their proposed solution offers a path toward synthesizing training sets that balance both clean performance and adversarial robustness.

## Model Alignment & Interpretability

The quest for aligned and interpretable models advances through both empirical investigations and new theoretical frameworks. A profound challenge to a popular alignment shortcut is presented in **Mechanics of Bias and Reasoning**, which dissects how Chain-of-Thought prompting affects gender bias. The study goes beyond benchmark scores to analyze internal mechanisms, finding that apparent bias reductions may not reflect meaningful changes in the model's reasoning processes, cautioning against superficial mitigation techniques.

The alignment training landscape itself is being re-examined. **Conditional Equivalence of DPO and RLHF** proves that DPO's optimization target diverges from RLHF's when the optimal RLHF policy does not already prefer human-preferred responses over the reference policy. This means DPO can optimize for relative advantage, not absolute preference, leading to "pathological convergence." This theoretical insight is critical for practitioners choosing between these paradigms. In response to alignment challenges, **FBOS-RL** introduces Feedback-Driven Bi-Objective Synergistic Reinforcement Learning, framing the RL update step itself as a learning problem where high-quality rollouts act as an implicit teacher, aiming to improve the sample efficiency and stability of alignment training.

For interpretability, **Geometry-Lite: Interpretable Safety Probing via Layer-Wise Margin Geometry** moves beyond black-box safety probes. It decomposes how safety evidence is formed across layers, studying the geometric separation between safe and unsafe representations to explain low-false-positive decisions and assess stability under distribution shift. This provides a more granular, mechanistic understanding of safety classifiers.

## Privacy Protection & Federated Learning

Innovations in federated learning and differential privacy aim to reconcile strong privacy guarantees with practical utility. A major efficiency breakthrough for the "right to be forgotten" is **Causal Unlearning in Collaborative Optimization**. The authors present HF-KCU, a method that approximates the influence function via Krylov subspace iterations, reducing computational complexity from cubic to linear in parameter dimension. Crucially, a causal weighting mechanism ensures updates are only sent to clients holding the deleted data, preventing spurious changes—a significant step toward GDPR-compliant federated systems.

Complementing this on the system design front, **Choose Wisely and Privately** tackles the inefficiency caused by non-IID data. It proposes a proactive client selection mechanism that avoids wasting resources on noisy or heterogeneous clients, improving convergence speed and final accuracy. This addresses a key bottleneck for practical FL deployment. The quest for better privacy-utility trade-offs also drives **SMA-DP**, which augments DP-SGD with a spectral memory-aware branch. By using power-law exponents from previous privatized releases as reliability signals, it aims to reduce the variance of noisy updates, potentially preserving more utility on challenging datasets.

However, privacy claims require vigilant auditing. **Auditing Apple's DifferentialPrivacy.framework** presents a timely client-side audit of Apple's proprietary implementation, uncovering implementation bugs and misconfigurations. This work underscores the critical need for independent verification of deployed privacy mechanisms, moving beyond theoretical guarantees to practical assurance. In the theoretical domain, **Information Leakage Envelopes** rigorously defines a new notion—the PML envelope—to quantify the largest possible leakage about a secret, providing a robust framework for reasoning about pointwise maximal leakage that is both post-processing robust and bounds failure probability.

## Safety Benchmarks and Evaluations

The development of rigorous, nuanced evaluation methodologies is critical for measuring progress in safety. **Refusal Evaluation in Coding LLMs and Code Agents** provides a much-needed systematic review of thirteen malicious-code prompt corpora. Its analysis highlights the lack of standardized protocols and validation across these benchmarks, calling for more unified and reliable evaluation frameworks to assess coding model safety.

In specialized domains, **Do No Harm? Hallucination and Actor-Level Abuse in Web-Deployed Medical Large Language Models** presents a large-scale assessment of 6,233 medical GPTs. By introducing the MedGPT-HEval framework for hallucination detection and a pipeline for policy violation assessment, it reveals widespread issues, emphasizing the high stakes of deploying LLMs in healthcare without rigorous safety certification. For planning capabilities, **PlanningBench** introduces a scalable data engine to generate verifiable planning tasks, moving beyond fixed instance collections to allow controllable difficulty and coverage, which is vital for evaluating and training LLMs on complex, goal-oriented reasoning.

## Agent Security & Governance

The security of increasingly autonomous AI agents is emerging as a paramount concern, requiring systemic and cryptographic solutions. The position paper **Agent Security is a Systems Problem** provides a foundational shift in perspective. It argues that model robustness alone is insufficient; the agent must be treated as untrusted, and security invariants must be enforced at the system level using techniques from operating systems, networks, and formal methods. This paradigm is operationalized by works like **Heartbeat-Bound Hierarchical Credentials (HBHC)**, which introduces a cryptographic protocol to bind credential validity to periodic parent liveness proofs, preventing "zombie agents" from executing operations after an operator shutdown.

Furthermore, agents create novel data leakage vectors. **An Application-Layer Multi-Modal Covert-Channel Reference Monitor for LLM Agent Egress** catalogs how compromised agents can exfiltrate data via zero-width characters, JSON key ordering, ultrasonic tones, and even LSB pixel planes, proposing a reference monitor to detect such covert channels. Evaluating agent safety also requires moving beyond single-turn interactions, as shown in **Rethinking Fraud Safety Evaluation**, which finds that graph-context defenders improve early refusal under multi-round attacks but at the cost of increased benign over-refusal, highlighting a critical safety-utility trade-off.

## Looking Forward

Several fundamental questions loom on the horizon. The **Trusted Weights, Treacherous Optimizations?** attack opens a new research frontier: how can we verify the numerical safety of the entire inference optimization pipeline, from compilers to hardware? This requires a new breed of verification tools. The conditional nature of DPO-RLHF equivalence, as proven in **Conditional Equivalence of DPO and RLHF**, prompts a deeper inquiry: under what practical conditions does this equivalence hold or break, and how should alignment algorithms be designed to be robust to this divergence?

In privacy, while methods like HF-KCU for unlearning show promise, their long-term robustness against sophisticated inference attacks and their behavior in continuous learning scenarios remain unexplored. Finally, the systemic view of agent security raises architectural challenges: what are the minimal, composable system-level primitives required to secure a diverse range of agent swarms without crippling their utility? Answering these questions will be critical for building AI systems that are not only capable but also trustworthy and resilient.

---


## References

- **Causal Unlearning in Collaborative Optimization: Exact and Approximate Influence Reversal under Adversarial Contributions** — [arxiv_lg](https://arxiv.org/abs/2605.20341)
- **Comparative Evaluation of Deep Learning Models for Fake Image Detection** — [arxiv_cr](https://arxiv.org/abs/2605.20971)
- **Choose Wisely and Privately: Proactive Client Selection for Fair and Efficient Federated Learning** — [arxiv_cr](https://arxiv.org/abs/2605.20975)
- **SoK: Critical Evaluation of Quantum Machine Learning for Adversarial Robustness** — [arxiv_cr](https://arxiv.org/abs/2511.14989)
- **It Takes Two: Complementary Self-Distillation for Contextual Integrity in LLMs** — [arxiv_lg](https://arxiv.org/abs/2605.20258)
- **OmniISR: A Unified Framework for Centralized and Federated Learning via Intermediate Supervision and Regularization** — [arxiv_lg](https://arxiv.org/abs/2605.20276)
- **Adaptive Probe-based Steering for Robust LLM Jailbreaking** — [arxiv_cr](https://arxiv.org/abs/2605.20286)
- **Verifiable Provenance and Watermarking for Generative AI: An Evidentiary Framework for International Operational Law and Domestic Courts** — [arxiv_cr](https://arxiv.org/abs/2605.21002)
- **SMA-DP: Spectral Memory-Aware Differential Privacy for Deep Learning** — [arxiv_cr](https://arxiv.org/abs/2605.20450)
- **Secure, Verifiable, and Scalable Multi-Client Data Sharing via Consensus-Based Privacy-Preserving Data Distribution** — [arxiv_cr](https://arxiv.org/abs/2601.00418)
- **Mechanics of Bias and Reasoning: Interpreting the Impact of Chain-of-Thought Prompting on Gender Bias in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.20410)
- **Do No Harm? Hallucination and Actor-Level Abuse in Web-Deployed Medical Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20591)
- **Findings of the Counter Turing Test: AI-Generated Text Detection** — [arxiv_cl](https://arxiv.org/abs/2605.20761)
- **FBOS-RL: Feedback-Driven Bi-Objective Synergistic Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20256)
- **Conformal Selective Acting: Anytime-Valid Risk Control for RLVR-Trained LLMs** — [arxiv_lg](https://arxiv.org/abs/2605.20270)
- **Neural Collapse by Design: Learning Class Prototypes on the Hypersphere** — [arxiv_lg](https://arxiv.org/abs/2605.20302)
- **Decomposing MXFP4 quantization error for LLM reinforcement learning: reducible bias, recoverable deadzone, and an irreducible floor** — [arxiv_lg](https://arxiv.org/abs/2605.20402)
- **Trusted Weights, Treacherous Optimizations? Optimization-Triggered Backdoor Attacks on LLMs** — [arxiv_cr](https://arxiv.org/abs/2605.20641)
- **Information Leakage Envelopes** — [arxiv_cr](https://arxiv.org/abs/2605.21185)
- **Auditing Apple's DifferentialPrivacy.framework: Implementation Bugs, Misconfigurations, and Practical Risks** — [arxiv_cr](https://arxiv.org/abs/2605.21378)
- **An exponential mechanism based on quadratic approximations for fine-tuning machine learning models with privacy guarantees** — [arxiv_cr](https://arxiv.org/abs/2605.20521)
- **Agent Security is a Systems Problem** — [arxiv_cr](https://arxiv.org/abs/2605.18991)
- **Synchronization and Turn-Taking in Full-Duplex Speech Dialogue Models** — [arxiv_cl](https://arxiv.org/abs/2605.20356)
- **Regulating Anatomy-Aware Rewards via Trajectory-Integral Feedback for Volumetric Computed Tomography Analysis** — [arxiv_cv](https://arxiv.org/abs/2605.20277)
- **Can Vision Models Truly Forget? Mirage: Representation-Level Certification of Visual Unlearning** — [arxiv_cv](https://arxiv.org/abs/2605.20282)
- **SDM: A Powerful Tool for Evaluating Model Robustness** — [arxiv_cv](https://arxiv.org/abs/2605.20308)
- **Capability $\neq$ Interpretability: Human Interpretability of Vision Foundation Models** — [arxiv_cv](https://arxiv.org/abs/2605.20337)
- **Mind Your Margin and Boundary: Are Your Distilled Datasets Truly Robust?** — [arxiv_cv](https://arxiv.org/abs/2605.20606)
- **Conditional Equivalence of DPO and RLHF: Implicit Assumption, Failure Modes, and Provable Alignment** — [huggingface_papers](https://arxiv.org/abs/2605.20834)
- **Neural Estimation of Pairwise Mutual Information in Masked Discrete Sequence Models** — [arxiv_lg](https://arxiv.org/abs/2605.20187)
- **Geometry-Lite: Interpretable Safety Probing via Layer-Wise Margin Geometry** — [arxiv_lg](https://arxiv.org/abs/2605.20241)
- **GROW: Aligning GRPO with State-Action Modeling for Open-World VLM Agents** — [arxiv_lg](https://arxiv.org/abs/2605.20246)
- **CP-MoE: Consistency-Preserving Mixture-of-Experts for Continual Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20247)
- **Graph Transductive Sharpening: Leveraging Unlabeled Predictions in Node Classification** — [arxiv_lg](https://arxiv.org/abs/2605.20248)
- **Multi-Agent Reinforcement Learning for Safe Autonomous Driving Under Pedestrian Behavioral Uncertainty** — [arxiv_lg](https://arxiv.org/abs/2605.20255)
- **Chronicle: A Multimodal Foundation Model for Joint Language and Time Series Understanding** — [arxiv_lg](https://arxiv.org/abs/2605.20268)
- **Spectral Unforgetting: Post-Hoc Recovery of Damaged Capabilities Without Retraining** — [arxiv_lg](https://arxiv.org/abs/2605.20296)
- **Robust Subspace-Constrained Quadratic Models for Low-Dimensional Structure Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20300)
- **WaveGraphNet: Physics-Consistent Guided-Wave Damage Localization through Coupled Inverse-Forward Graph Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20311)
- **Less Data, Faster Training: repeating smaller datasets speeds up learning via sampling biases** — [arxiv_lg](https://arxiv.org/abs/2605.20314)
- **Symmetrization of Loss Functions for Robust Training of Neural Networks in the Presence of Noisy Labels** — [arxiv_lg](https://arxiv.org/abs/2605.20347)
- **Consistently Informative Soft-Label Temperature for Knowledge Distillation** — [arxiv_lg](https://arxiv.org/abs/2605.20357)
- **Artificial Pancreas Implantables -- How Healthcare Professionals May Deal With DIY Bio Cases** — [arxiv_cr](https://arxiv.org/abs/2605.20208)
- **Refusal Evaluation in Coding LLMs and Code Agents: A Systematic Review of Thirteen Malicious-Code Prompt Corpora (2023-2025)** — [arxiv_cr](https://arxiv.org/abs/2605.20351)
- **Latent Geometry as a Structural Monitor: Eigenspace Alignment for Anomaly Detection in Anonymity Networks** — [arxiv_cr](https://arxiv.org/abs/2605.20391)
- **Detecting Data Exfiltration through I2P Anonymity Networks: A Two-Phase Machine Learning Approach** — [arxiv_cr](https://arxiv.org/abs/2605.20546)
- **Heartbeat-Bound Hierarchical Credentials: Cryptographic Revocation for AI Agent Swarms** — [arxiv_cr](https://arxiv.org/abs/2605.20704)
- **An Application-Layer Multi-Modal Covert-Channel Reference Monitor for LLM Agent Egress** — [arxiv_cr](https://arxiv.org/abs/2605.20734)
- **Rethinking Fraud Safety Evaluation: Multi-Round Attacks Reveal Safety-Utility Tradeoffs in Graph-Context LLM Defenders** — [arxiv_cr](https://arxiv.org/abs/2605.20759)
- **An Evidence-driven Protocol for Trustworthy CI Pipelines** — [arxiv_cr](https://arxiv.org/abs/2605.21089)
- **Shiny Stories, Hidden Struggles: Investigating the Representation of Disability Through the Lens of LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.20191)
- **Leveraging Large Language Models for Sentiment Analysis: Multi-Modal Analysis of Decentraland's MANA Token** — [arxiv_cl](https://arxiv.org/abs/2605.20192)
- **Parallel LLM Reasoning for Bias-Resilient, Robust Conceptual Abstraction** — [arxiv_cl](https://arxiv.org/abs/2605.20194)
- **MedicalBench: Evaluating Large Language Models Toward Improved Medical Concept Extraction** — [arxiv_cl](https://arxiv.org/abs/2605.20197)
- **Under Pressure: Emotional Framing Induces Measurable Behavioral Shifts and Structured Internal Geometry in Small Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20202)
- **DEL: Digit Entropy Loss for Numerical Learning of Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20369)
- **Do as I Say, Not as I Do: Instruction-Induction Conflict in LLMs** — [arxiv_cl](https://arxiv.org/abs/2605.20382)
- **Stage-Audit: Auditable Source-Frontier Discovery for Cross-Wiki Tables** — [arxiv_cl](https://arxiv.org/abs/2605.20478)
- **When Irregularity Helps: A Subclass Analysis of Inductive Bias in Neural Morphology** — [arxiv_cl](https://arxiv.org/abs/2605.20558)
- **Divide-Prompt-Refine: a Training-Free, Structure-Aware Framework for Biomedical Abstract Generation** — [arxiv_cl](https://arxiv.org/abs/2605.20628)
- **On the limits and opportunities of AI reviewers: Reviewing the reviews of Nature-family papers with 45 expert scientists** — [arxiv_cl](https://arxiv.org/abs/2605.20668)
- **Beyond Semantic Similarity: A Two-Phase Non-Parametric Retrieval Workflow for Corporate Credit Underwriting** — [arxiv_cl](https://arxiv.org/abs/2605.20684)
- **SCRIBE: Diagnostic Evaluation and Rich Transcription Models for Indic ASR** — [arxiv_cl](https://arxiv.org/abs/2605.20712)
- **MTR-Suite: A Framework for Evaluating and Synthesizing Conversational Retrieval Benchmarks** — [arxiv_cl](https://arxiv.org/abs/2605.20729)
- **Distributional Alignment as a Criterion for Designing Task Vectors in In-Context Learning** — [arxiv_cl](https://arxiv.org/abs/2605.20730)
- **The Illusion of Intervention: Your LLM-Simulated Experiment is an Observational Study** — [arxiv_cl](https://arxiv.org/abs/2605.20767)
- **Co-Fusion4D: Spatio-temporal Collaborative Fusion for Robust 3D Object Detection** — [arxiv_cv](https://arxiv.org/abs/2605.20301)
- **Lighting-aware Unified Model for Instance Segmentation** — [arxiv_cv](https://arxiv.org/abs/2605.20436)
- **Understanding Model Behavior in Monocular Polyp Sizing** — [arxiv_cv](https://arxiv.org/abs/2605.20461)
- **EPC-3D-Diff: Equivariant Physics Consistent Conditional 3D Latent Diffusion for CBCT to CT Synthesis** — [arxiv_cv](https://arxiv.org/abs/2605.20470)
- **MAPS: A Synthetic Dataset for Probing Vision Models in a Controlled 3D Scene Space** — [arxiv_cv](https://arxiv.org/abs/2605.20549)
- **End-to-End Unmixing with Material Prompts for Hyperspectral Object Tracking** — [arxiv_cv](https://arxiv.org/abs/2605.20569)
- **QwenSafe: Multimodal Content Rating Description Identification via Preference-Aligned VLMs** — [arxiv_cv](https://arxiv.org/abs/2605.20584)
- **Head-Aware Key-Value Compression for Efficient Autoregressive Image Generation** — [arxiv_cv](https://arxiv.org/abs/2605.20600)
- **Pareto-Enhanced Portrait Generation: Vision-Aligned Text Supervision for Alignment, Realism, and Aesthetics** — [arxiv_cv](https://arxiv.org/abs/2605.20640)
- **Diversed Model Discovery via Structured Table Discovery** — [huggingface_papers](https://arxiv.org/abs/2605.22766)
- **IndusAgent: Reinforcing Open-Vocabulary Industrial Anomaly Detection with Agentic Tools** — [huggingface_papers](https://arxiv.org/abs/2605.20682)
- **OcclusionFormer: Arranging Z-Order for Layout-Grounded Image Generation** — [huggingface_papers](https://arxiv.org/abs/2605.21343)
- **Leveraging Vision-Language Models to Detect Attention in Educational Videos** — [arxiv_cv](https://arxiv.org/abs/2605.20211)
- **Why Latent Actions Fail, and How to Prevent It** — [arxiv_cv](https://arxiv.org/abs/2605.20223)
- **AI-Assisted Competency Assessment from Egocentric Video in Simulation-Based Nursing Education** — [arxiv_cv](https://arxiv.org/abs/2605.20233)
- **AnimeAdapter: Fine-grained and Consistent Zero-shot Anime Character Generation** — [arxiv_cv](https://arxiv.org/abs/2605.20237)
- **Generation of Heterogeneous PET Images from Uniform Organ Activity Maps Using a Pretrained Domain-Adapted Diffusion Model** — [arxiv_cv](https://arxiv.org/abs/2605.20267)
- **You Don't Need Attention: Gated Convolutional Modeling for Watch-Based Fall Detection** — [arxiv_cv](https://arxiv.org/abs/2605.20275)
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
- **Same Architecture, Different Capacity: Optimizer-Induced Spectral Scaling Laws** — [huggingface_papers](https://arxiv.org/abs/2605.21803)
- **You Only Need Minimal RLVR Training: Extrapolating LLMs via Rank-1 Trajectories** — [huggingface_papers](https://arxiv.org/abs/2605.21468)
- **OCTOPUS: Optimized KV Cache for Transformers via Octahedral Parametrization Under optimal Squared error quantization** — [huggingface_papers](https://arxiv.org/abs/2605.21226)
- **iTryOn: Mastering Interactive Video Virtual Try-On with Spatial-Semantic Guidance** — [huggingface_papers](https://arxiv.org/abs/2605.21431)
- **DrawMotion: Generating 3D Human Motions by Freehand Drawing** — [huggingface_papers](https://arxiv.org/abs/2605.20955)
- **PlanningBench: Generating Scalable and Verifiable Planning Data for Evaluating and Training Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.20873)
- **Roundtables: Can AI Learn to Understand the World?** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137756/roundtables-can-ai-learn-to-understand-the-world/)
- **Scaling creativity in the age of AI** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137613/scaling-creativity-in-the-age-of-ai/)
- **Spotify and Universal Music strike deal allowing fan-made AI covers and remixes** — [techcrunch_ai](https://techcrunch.com/2026/05/21/spotify-and-universal-music-strike-deal-allowing-fan-made-ai-covers-and-remixes/)
- **Trump delays AI security executive order, saying language ‘could have been a blocker’** — [techcrunch_ai](https://techcrunch.com/2026/05/21/trump-delays-ai-security-executive-order-i-dont-want-to-get-in-the-way-of-that-leading/)
- **Anthropic’s Code with Claude showed off coding’s future—whether you like it or not** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137735/anthropics-code-with-claude-showed-off-codings-future-whether-you-like-it-or-not/)
- **The Download: online safety’s future and climate tech’s big pivot** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137733/the-download-online-safety-climate-tech-pivot/)
- **Hark raises $700M Series A for its secretive ‘universal’ AI interface** — [techcrunch_ai](https://techcrunch.com/2026/05/21/hark-raises-700m-series-a-for-its-secretive-universal-ai-interface/)
- **Google is pitching an AI agent ecosystem to consumers who may not buy it** — [techcrunch_ai](https://techcrunch.com/2026/05/21/google-is-pitching-an-ai-agent-ecosystem-to-consumers-who-may-not-buy-it/)
- **Climate tech companies are pivoting to critical minerals** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137622/climate-tech-pivot-critical-minerals/)
- **Tech researchers are suing the Trump administration over the future of online safety** — [mit_tech_review](https://www.technologyreview.com/2026/05/21/1137632/lawsuit-trump-administration-online-safety-coalition-for-independent-technology-research/)
- **Six search engines worth trying now that Google isn’t really Google anymore** — [techcrunch_ai](https://techcrunch.com/2026/05/21/six-search-engines-worth-trying-now-that-google-isnt-really-google-anymore/)
- **Spotify adds AI-powered Q&A and briefing generation features to podcasts** — [techcrunch_ai](https://techcrunch.com/2026/05/21/spotify-adds-ai-powered-qa-and-briefing-generation-features-to-podcasts/)
- **Spotify takes on Google’s NotebookLM with its new app** — [techcrunch_ai](https://techcrunch.com/2026/05/21/spotify-debuts-a-new-desktop-app-for-creating-personal-podcasts/)
- **Spotify launches an ElevenLabs-powered audiobook creation tool** — [techcrunch_ai](https://techcrunch.com/2026/05/21/spotify-launches-an-elevenlabs-powered-audiobook-creation-tool/)
- **The Path, founded by Tony Robbins and Calm alums, hopes to offer safer AI therapy** — [techcrunch_ai](https://techcrunch.com/2026/05/21/the-path-founded-by-tony-robbins-and-calm-alums-wants-to-offer-safer-ai-therapy/)
- **With aluminum prices up 20%, recycling startups bet on AI to cash in** — [techcrunch_ai](https://techcrunch.com/2026/05/21/with-aluminum-prices-up-20-recycling-startups-bet-on-ai-to-cash-in/)
- **AdventHealth advances whole-person care with OpenAI** — [openai](https://openai.com/index/adventhealth)
- **We’re launching the Google DeepMind Accelerator program in Asia Pacific to tackle environmental risks** — [deepmind](https://deepmind.google/blog/were-launching-the-google-deepmind-accelerator-program-in-asia-pacific-to-tackle-environmental-risks/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **ganimjeong/Harness-for-codex** — [github](https://github.com/ganimjeong/Harness-for-codex)
- **wailers9/bragi** — [github](https://github.com/wailers9/bragi)
- **5bv57zcm44-max/NOXUS-AI-Open-WhatsApp** — [github](https://github.com/5bv57zcm44-max/NOXUS-AI-Open-WhatsApp)
- **gouravnagar-infosec/ai-kill-chain** — [github](https://github.com/gouravnagar-infosec/ai-kill-chain)
- **MarbleRoller/Ads-Power-Crack-Latest-TS** — [github](https://github.com/MarbleRoller/Ads-Power-Crack-Latest-TS)
- **tuchg/Lucarne** — [github](https://github.com/tuchg/Lucarne)
- **ayush016/android-lead-agent-skills** — [github](https://github.com/ayush016/android-lead-agent-skills)
- **kingbootoshi/directional-prompting** — [github](https://github.com/kingbootoshi/directional-prompting)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **zimingttkx/QuantumFlow** — [github](https://github.com/zimingttkx/QuantumFlow)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **c4pt0r/pie** — [github](https://github.com/c4pt0r/pie)
- **lywnl/ai-app-generation** — [github](https://github.com/lywnl/ai-app-generation)
- **madguyevans-creator/resale-agent-skill-hub** — [github](https://github.com/madguyevans-creator/resale-agent-skill-hub)
- **h4ckf0r0day/awesome-ai-web-scraping** — [github](https://github.com/h4ckf0r0day/awesome-ai-web-scraping)
- **ForgeAILab/forge** — [github](https://github.com/ForgeAILab/forge)
- **hasanyilmaz/operon** — [github](https://github.com/hasanyilmaz/operon)
- **AI4MSE/Parallax** — [github](https://github.com/AI4MSE/Parallax)
- **The Matching Principle: A Geometric Theory of Loss Functions for Nuisance-Robust Representation Learning** — [arxiv_ml](https://arxiv.org/abs/2605.22800v1)
- **39万！雷军发布小米最贵SUV** — [qbitai](https://www.qbitai.com/2026/05/422088.html)
- **联想集团Q4营收利润双创新高，兑现历史最佳财年** — [qbitai](https://www.qbitai.com/2026/05/422127.html)
- **腾讯混元开源全新翻译模型Hy-MT2 ，上线小程序「腾讯Hy翻译」** — [qbitai](https://www.qbitai.com/2026/05/422068.html)
- **菲尔兹奖得主都看懵了：OpenAI非数学模型首次自主突破80年未解数学难题** — [qbitai](https://www.qbitai.com/2026/05/422032.html)
- **风行在线CEO易正朝：先全员Coding，再All in众创丨AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/422001.html)
- **Artificial Analysis放榜：千问3.7问鼎国产模型冠军，全球前五** — [qbitai](https://www.qbitai.com/2026/05/422009.html)
- **AI首次实现中国风光发电普查，北大、阿里达摩院研究登上《自然》** — [qbitai](https://www.qbitai.com/2026/05/422002.html)
- **上海交大AI教授亲授：半天带你拆解Agent底层逻辑** — [qbitai](https://www.qbitai.com/2026/05/421697.html)
- **得场景者得AI天下，出行赛道跑出了一家值得关注的数据玩家** — [qbitai](https://www.qbitai.com/2026/05/421694.html)
- **520当天400万AI人，都在量子位听这近20场演讲&对谈｜第四届中国AIGC产业峰会** — [qbitai](https://www.qbitai.com/2026/05/421691.html)
- **Proxy-Based Approximation of Shapley and Banzhaf Interactions** — [arxiv_ml](https://arxiv.org/abs/2605.22738v1)
- **The efficiency-gain illusion: People underestimate the rate of AI use and overestimate its benefits on simple tasks** — [arxiv_cy](https://arxiv.org/abs/2605.22687v1)
- **A Martingale Kernel Independence Test** — [arxiv_ml](https://arxiv.org/abs/2605.22549v1)
- **Generative Modeling by Value-Driven Transport** — [arxiv_ml](https://arxiv.org/abs/2605.22507v1)
- **Do Not Trust The Auctioneer: Learning to Bid in Feedback-Manipulated Auctions** — [arxiv_ml](https://arxiv.org/abs/2605.22438v1)
- **AI-Enabled Serious Games: Integrating Intelligence and Adaptivity in Training Systems** — [arxiv_cy](https://arxiv.org/abs/2605.21962v1)
- **Detecting Offensive Cyber Agents: A Detection-in-Depth Approach** — [arxiv_cy](https://arxiv.org/abs/2605.21956v1)
- **Finite-Particle Convergence Rates for Conservative and Non-Conservative Drifting Models** — [arxiv_ml](https://arxiv.org/abs/2605.22795v1)
- **SDPM: Survival Diffusion Probabilistic Model for Continuous-Time Survival Analysis** — [arxiv_ml](https://arxiv.org/abs/2605.22776v1)
- **Uniform Diffusion Models Revisited: Leave-One-Out Denoiser and Absorbing State Reformulation** — [arxiv_ml](https://arxiv.org/abs/2605.22765v1)
- **Plug-in Losses for Evidential Deep Learning: A Simplified Framework for Uncertainty Estimation that Includes the Softmax Classifier** — [arxiv_ml](https://arxiv.org/abs/2605.22746v1)
- **Multiple Neural Operators Achieve Near-Optimal Rates for Multi-Task Learning** — [arxiv_ml](https://arxiv.org/abs/2605.22724v1)
- **Beyond Temperature: Hyperfitting as a Late-Stage Geometric Expansion** — [arxiv_ml](https://arxiv.org/abs/2605.22579v1)
- **Healthcare LLM Benchmarks Are Only as Good as Their Explicit Assumptions** — [arxiv_cy](https://arxiv.org/abs/2605.22612v1)
- **Guiding Multi-Objective Genetic Programming with Description Length Improves Symbolic Regression Solutions** — [arxiv_ml](https://arxiv.org/abs/2605.22374v1)
- **Departure from Regularity: Degree Heterogeneity and Eigengap as the Structural Drivers of ASE-LSE Latent Subspace Disagreement** — [arxiv_ml](https://arxiv.org/abs/2605.22346v1)
- **From Sequential Nodes to GPU Batches: Parallel Branch and Bound for Optimal $k$-Sparse GLMs** — [arxiv_ml](https://arxiv.org/abs/2605.22188v1)
- **Aerodynamic force reconstruction using physics-informed Gaussian processes** — [arxiv_ml](https://arxiv.org/abs/2605.22111v1)
- **Uniform-in-Time Weak Propagation-of-Chaos in Shallow Neural Networks** — [arxiv_ml](https://arxiv.org/abs/2605.22010v1)
- **Epicure: Navigating the Emergent Geometry of Food Ingredient Embeddings** — [arxiv_cy](https://arxiv.org/abs/2605.22391v1)
- **Perception or Prejudice: Can MLLMs Go Beyond First Impressions of Personality?** — [arxiv_cy](https://arxiv.org/abs/2605.22109v1)
- **博坦发布全新旗舰无人机ATOM 3** — [36kr](https://36kr.com/newsflashes/3819844675031427?f=rss)
- **中信证券：解决新型电力系统复杂“三体”问题，绿电直连从“点对点”到“点对群”** — [36kr](https://36kr.com/newsflashes/3819729670508936?f=rss)
- **「闹剧场」阿球：一个同济土木生转行，想把喜剧变成可批量复制的科学｜独家对谈** — [36kr](https://36kr.com/p/3816066708872713?f=rss)
- **中信证券：具身智能、半导体、AI上游装备&材料、世界杯的主题热情有望爆发** — [36kr](https://36kr.com/newsflashes/3819720760217733?f=rss)
- **8点1氪丨“拉勾网”被曝主动申请破产；特斯拉Model S和X正式停产退役；三星内存工人，奖金或达280万元** — [36kr](https://36kr.com/p/3819709302329735?f=rss)
- **氪星晚报｜马斯克旗下SpaceX启动史上最大规模IPO计划；全国首张综合性司机服务地图上线；海关总署在粤发布《海关支持粤港澳大湾区建设若干措施》** — [36kr](https://36kr.com/p/3816942732133510?f=rss)
- **新石器NewClaw：AI一体化解决方案，零门槛当无人车指挥官| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818927367046018?f=rss)
- **业绩快报 | 唯品会一季度净营收266亿元，SVIP用户贡献超50%线上销售额** — [36kr](https://36kr.com/p/3818915823764610?f=rss)
- **从概念到产线一：AI在工业制造领域的深水区探索| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818903062004870?f=rss)
- **城市级AI服务：从试点到常态化，机器人的实景作战与规模化落地| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818889074557829?f=rss)
- **36氪x PureblueAI清蓝战略合作启动仪式暨《2026消费品牌AI推荐力名册》发布 | 2026 AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818877539091333?f=rss)
- **把确定性，写进农业：四个外行、两次失败、三千万学费换来的答案| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3818800487679111?f=rss)
- **从算力到价值：AI时代的基础设施重构与产业增长新引擎| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3817502775329667?f=rss)
- **摩根大通期货潘凤：已有境外机构启动国债期货投资计划与套保报备** — [36kr](https://36kr.com/newsflashes/3819802311577736?f=rss)
- **两市融资余额减少83.53亿元** — [36kr](https://36kr.com/newsflashes/3819748426453380?f=rss)
- **From Betting to Empirical Bernstein LIL** — [arxiv_ml](https://arxiv.org/abs/2605.22124v1)