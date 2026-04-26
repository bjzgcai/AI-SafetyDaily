# AI Daily Digest [AI 安全] - 2026-04-26


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-04-26
**Author:** Senior AI Safety Researcher

## Highlights

The most significant developments in today’s research landscape center on the evolving threat model for stateless multi-turn interactions, the structural challenges in agent tool integration, and the mathematical rigor required for privacy-preserving machine learning. First, the introduction of **Transient Turn Injection** exposes a critical vulnerability in how large language models handle moderation across isolated interactions, suggesting that current safety filters are insufficient against distributed adversarial intent. Second, the emergence of **Tool Attention Is All You Need** highlights a systemic efficiency bottleneck in the Model Context Protocol, where eager schema injection creates a "Tools Tax" that degrades reasoning performance in scalable workflows. Finally, the continued refinement of **Differentially Private De-identification** and **Separable Expert Architecture** demonstrates a maturing field of privacy computing, moving from theoretical guarantees to practical, deletable user proxies that enable true unlearning without full model retraining. These academic breakthroughs collectively signal a shift from static safety checks to dynamic, process-aware security and alignment mechanisms.

## Adversarial Attacks & Robustness

The security frontier for large language models is expanding beyond simple prompt injection to more sophisticated, multi-turn exploitation strategies. A pivotal contribution to this domain is **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models**, which introduces a technique where adversarial intent is distributed across isolated interactions to evade policy enforcement. Unlike conventional jailbreaks that rely on maintaining a coherent malicious context, this method leverages automated attacker agents to iteratively test and bypass moderation in both commercial and open-source systems. This finding complements the work on **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers**, which addresses the limitations of existing backdoor methods that often suffer from explicit trigger patterns. The authors of **Stealthy Backdoor Attacks** propose a framework that embeds triggers within natural language styles, making them harder to detect while ensuring payload injection in long-form generation. Together, these works suggest that the threat landscape is moving toward attacks that are both temporally distributed and semantically indistinguishable from legitimate traffic.

In the physical domain, security vulnerabilities extend to sensor fusion systems used in safety-critical applications. **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** provides a systematic study of how attackers can manipulate image reconstruction processes directly through waveform-domain physical attacks. This research is particularly concerning for airport passenger screening and similar deployments where the integrity of the imaging pipeline is paramount. The study proposes a practical white-box adversarial model and a differential imaging attack framework, constructing a real measured dataset to validate the attack's feasibility. This physical-layer vulnerability contrasts with the software-centric attacks discussed in **Transient Turn Injection**, indicating that robustness must be addressed across the entire stack, from model weights to sensor inputs. Furthermore, **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles** investigates whether an attacker can bypass multi-sensor redundancy by fabricating cross-sensor consistency. By designing a coordinated, data-level attack that emulates synchronized physical inputs, the authors demonstrate that fusion processes themselves introduce subtle vulnerabilities that can be exploited to make multiple sensors agree on a false object.

The intersection of malware detection and adversarial evasion is also a critical area of concern. **Adversarial Evasion in Non-Stationary Malware Detection: Minimizing Drift Signals through Similarity-Constrained Perturbations** investigates whether attackers can generate adversarial malware samples that evade classification while remaining inconspicuous to drift monitoring mechanisms. The proposed approach generates targeted adversarial examples that minimize drift signals, effectively hiding the adversarial nature of the malware from both the classifier and the monitoring system. This work complements the findings in **Mitigate or Fail: How Risk Management Shapes Cybersecurity Competency**, which suggests that organizational risk reasoning often fails to align with the actual threat landscape due to training architectures that prioritize threat detection over risk management. The combination of these findings implies that both technical defenses and organizational governance must evolve to handle non-stationary, adaptive threats that exploit both model drift and human cognitive biases.

In the realm of deepfake detection, **Interpretable facial dynamics as behavioral and perceptual traces of deepfakes** offers an interpretable alternative to standard deep learning approaches. The study identifies core low-dimensional patterns of facial movement, deriving temporal features that characterize spatiotemporal structure. This work is significant because traditional machine learning classifiers trained on these bio-behavioral features relate more closely to human perceptual judgments than black-box deep learning models. This focus on interpretability aligns with the broader need for transparency in security systems, as discussed in **Verifying Machine Learning Interpretability Requirements through Provenance**, which argues that interpretability remains an immeasurable requirement in ML Engineering without rigorous verification frameworks. The authors propose using provenance to verify Non-Functional Requirements, suggesting that traceability is essential for ensuring that interpretability claims are substantiated.

## Model Alignment & Interpretability

Alignment research is increasingly recognizing that user intent is often not fully formed at the time of interaction, challenging the assumption that prompts are complete expressions of intent. **Alignment has a Fantasia Problem** argues that modern AI assistants treat prompts as complete expressions of intent, leading to failures when users engage with systems before their goals are fully formed. The authors propose that these "Fantasia interactions" demand a rethinking of alignment research, moving beyond instruction following to a more dynamic understanding of user needs. This theoretical advance is supported by empirical findings in **Reasoning Primitives in Hybrid and Non-Hybrid LLMs**, which study reasoning through basic operations like recall and state-tracking. The authors evaluate hybrid architectures that combine attention-based retrieval with recurrent state updates, finding that they may be better suited than attention-only models for tasks requiring both capabilities. This suggests that architectural choices significantly impact alignment and reasoning capabilities, a point reinforced by **Language as a Latent Variable for Reasoning Optimization**, which hypothesizes that language functions as a latent variable structurally modulating the model's internal inference pathways.

The evaluation of reasoning capabilities is also evolving beyond static benchmarks. **MathDuels: Evaluating LLMs as Problem Posers and Solvers** introduces a self-play benchmark where models occupy dual roles: authoring math problems under adversarial prompting and solving problems authored by every other participant. This approach addresses the limitation of existing evaluations that cast models solely as solvers of fixed problem sets, which are increasingly unable to differentiate model capabilities as performance approaches ceiling levels. The validation of problems by an independent verifier ensures that the generated tasks are meaningful and challenging. This focus on dynamic evaluation complements the work on **Seeing Fast and Slow: Learning the Flow of Time in Videos**, which studies time as a learnable visual concept. The authors develop models for reasoning about and manipulating the flow of time in videos, exploiting multimodal cues to detect speed changes and estimate playback speed. This work highlights the need for models to understand temporal dynamics, a capability that is crucial for both video generation and safety-critical temporal reasoning.

Interpretability in generative models is another key area of focus. **GFlowState: Visualizing the Training of Generative Flow Networks Beyond the Reward** presents a visual analytics system designed to illuminate the training process of Generative Flow Networks. While standard machine learning tools allow metric tracking, they do not reveal how models explore the sample space or construct sample trajectories. GFlowState addresses this by visualizing how sampling probabilities shift during training, providing insights into the model's exploration strategies. This tool is particularly relevant for applications like molecule and material discovery, where understanding the generation process is as important as the final output. The need for interpretability is further emphasized in **Evaluating Post-hoc Explanations of the Transformer-based Genome Language Model DNABERT-2**, which adapts AttnLRP to the attention mechanism to explain predictions on genome sequences. The authors find that explanations of convolutional neural networks capture relevant patterns, but it remains unclear whether this transfers to more expressive Transformer-based models. This work underscores the importance of validating explanation methods across different model architectures.

The role of language in reasoning is further explored in **Language as a Latent Variable for Reasoning Optimization**, which reports that non-English responses sometimes outperform English on reasoning tasks. The authors hypothesize that language functions as a latent variable that structurally modulates the model's internal inference pathways. To test this, they conducted a Polyglot Thinking Experiment, in which models were prompted to solve identical problems under language-constrained and language-unconstrained conditions. Results show that non-English responses often achieve higher accuracy, suggesting that the choice of language can influence the model's reasoning process. This finding has implications for alignment research, as it suggests that alignment strategies may need to be language-aware to ensure consistent behavior across different linguistic contexts.

## Privacy Protection & Federated Learning

Privacy-preserving machine learning continues to advance with a focus on formal guarantees and practical utility. **Differentially Private De-identification of Dutch Clinical Notes: A Comparative Evaluation** addresses the need for automated methods that combine privacy guarantees with high utility in healthcare data. While manual de-identification remains the gold standard, it is costly and slow, motivating the need for automated methods. The study evaluates methods based on named entity recognition and differential privacy, finding that LLMs are increasingly being used for this task. The authors provide a comparative evaluation of these methods, highlighting the trade-offs between privacy guarantees and data utility. This work is complemented by **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study**, which systematically evaluates the impact of DP mechanisms on statistical utility in survival analyses. The study uses clinical datasets and evaluates different levels of privacy budgets, providing empirical evidence on the impact of DP on Cox proportional hazards models.

The challenge of unlearning user data without retraining the entire model is addressed in **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies**. Current model training approaches incorporate user information directly into shared weights, making individual data removal computationally infeasible. This paper presents a three-layer architecture that decouples personal data from shared weights by combining a static base model, composable domain-expert LoRA adapters, and per-user proxy artefacts whose deletion constitutes deterministic unlearning. Evaluation on Phi-3.5-mini and Llama-3.1-8B confirms per-user differentiation, where personal data influences outputs while remaining deletable. This approach offers a practical solution to the "right to be forgotten" in the context of large language models, addressing a critical gap in privacy compliance.

Federated learning and data privacy are also being explored in the context of clinical data. **Differentially Private De-identification of Dutch Clinical Notes** highlights the regulatory pressures from GDPR and HIPAA that drive the need for automated de-identification. The authors note that while methods based on differential privacy provide formal privacy guarantees, the integration of large language models introduces new challenges in maintaining utility. The comparative evaluation suggests that a hybrid approach may be necessary to balance privacy and utility effectively. This aligns with the broader trend of integrating privacy-preserving techniques into standard data processing pipelines, as seen in **Cross-Domain Data Selection and Augmentation for Automatic Compliance Detection**, which studies data selection as a strategy to mitigate negative transfer in compliance detection. The authors evaluate four approaches for selecting augmentation data from a larger source domain, finding that principled methods can improve cross-domain transfer in regulatory text analysis.

## Agent Security & Governance

The security of AI agents is becoming a central concern as they increasingly operate in open-ended environments and interact with external tools. **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** presents a protocol-aware security testing framework that operationalizes developer pitfalls as reproducible scenarios. The Model Context Protocol (MCP) is increasingly adopted for tool-integrated LLM agents, but its multi-layer design and third-party server ecosystem expand risks across tool metadata, untrusted outputs, and supply-chain vectors. The framework validates outcomes with MCP traces and objective validators, offering remediation guidance that existing benchmarks lack. This work is directly supported by **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows**, which addresses the hidden per-turn overhead imposed by stateless, eager schema injection. The authors introduce Tool Attention, a mechanism that reduces the "Tools Tax" and improves reasoning performance by dynamically gating tool access and loading schemas lazily. Together, these papers highlight the need for both security testing and efficiency optimization in agent frameworks.

The reliability of GUI automation agents is another critical area of focus. **VLAA-GUI: Knowing When to Stop, Recover, and Search, A Modular Framework for GUI Automation** addresses the challenges of early stopping and repetitive loops in autonomous GUI agents. The framework is built around three integrated components that guide the system on when to Stop, Recover, and Search. A mandatory Completeness Verifier enforces UI-observable success criteria and verification at every finish step, ensuring that agents do not prematurely declare success without verifiable evidence. This modular approach provides a structured method for improving the reliability of GUI agents, which is essential for their deployment in enterprise workflows. The need for reliable agents is further emphasized in **Compliance Moral Hazard and the Backfiring Mandate**, which develops a mechanism design framework for decentralized risk analytics. The authors identify three strategic frictions: compliance moral hazard, adversarial adaptation, and information destruction through intervention. A temporal value assignment mechanism is proposed to credit institutions using a strictly proportional reward structure, addressing the information aggregation problem in shared customer populations.

The governance of AI agents is also being explored through the lens of moral and ethical decision-making. **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** characterizes machine behavior using the Whistleblower's Dilemma by varying crime severity and relational closeness. The study evaluates three distinct perspectives: moral rightness, predicted human behavior, and autonomous model decision-making. By analyzing the results, the authors determine whether models encode social nuances in moral judgment. This work is significant because it highlights the context-dependency of human moral judgment and the challenge of aligning models with these social expectations. The findings suggest that alignment research must account for relational dynamics to ensure that AI systems make decisions that are consistent with human values in complex social contexts.

The security of agent skills and marketplaces is also a growing concern. **Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study** investigates the risks associated with the growing skill economy, where free skill marketplaces report over 90,000 published skills. The authors demonstrate that adversaries can interact with public agents to extract hidden parameters and capabilities, creating a new attack surface. This finding underscores the need for secure skill marketplaces and robust protection mechanisms for proprietary agent capabilities. The work complements **Strategic Heterogeneous Multi-Agent Architecture for Cost-Effective Code Vulnerability Detection**, which proposes a heterogeneous multi-agent architecture inspired by game-theoretic principles. The "3+1" architecture deploys three cloud-based expert agents in parallel, while a local verifier performs adversarial validation. This approach balances detection accuracy and computational cost, offering a practical solution for automated code vulnerability detection.

## Safety Benchmarks & Evaluation

The evaluation of AI systems is evolving to address the limitations of static benchmarks and the need for more dynamic, realistic assessments. **Seeing Isn't Believing: Uncovering Blind Spots in Evaluator Vision-Language Models** systematically evaluates the reliability of Evaluator VLMs across both image-to-text and text-to-image tasks. The authors introduce targeted perturbations that degrade output quality along key error dimensions, including object hallucinations, spatial reasoning, and visual fidelity. This work highlights the need for robust evaluation methods that can detect subtle errors in evaluator models, which are increasingly used to assess the outputs of other models. The findings suggest that current evaluation practices may be insufficient to ensure the reliability of AI systems, particularly in visual domains.

The evaluation of audio reasoning is also being advanced with **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA**. Existing audio question answering benchmarks often enable models to succeed through shortcut strategies, such as using metadata or captions rather than genuine reasoning. AUDITA comprises carefully curated, human-authored trivia questions grounded in real-world audio, rigorously evaluating audio reasoning beyond surface-level acoustic recognition. This dataset addresses the limitations of existing benchmarks by providing a more realistic and challenging evaluation framework for audio understanding. The work complements **Generalizing Numerical Reasoning in Table Data through Operation Sketches and Self-Supervised Learning**, which introduces TaNOS, a continual pre-training framework for numerical reasoning over expert-domain tables. The framework uses header

---


## References

- **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21860v1)
- **Enabling and Inhibitory Pathways of University Students' Willingness to Disclose AI Use: A Cognition-Affect-Conation Perspective** — [arxiv_ai](https://arxiv.org/abs/2604.21733v1)
- **Fairness under uncertainty in sequential decisions** — [arxiv_ai](https://arxiv.org/abs/2604.21711v1)
- **Measuring Opinion Bias and Sycophancy via LLM-based Coercion** — [arxiv_cl](https://arxiv.org/abs/2604.21564v1)
- **Differentially Private De-identification of Dutch Clinical Notes: A Comparative Evaluation** — [arxiv_cl](https://arxiv.org/abs/2604.21421v1)
- **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study** — [arxiv_cr](https://arxiv.org/abs/2604.21491v1)
- **Drug Synergy Prediction via Residual Graph Isomorphism Networks and Attention Mechanisms** — [arxiv_lg](https://arxiv.org/abs/2604.21473v1)
- **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** — [arxiv_cl](https://arxiv.org/abs/2604.21871v1)
- **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** — [arxiv_lg](https://arxiv.org/abs/2604.21870v1)
- **GFlowState: Visualizing the Training of Generative Flow Networks Beyond the Reward** — [arxiv_lg](https://arxiv.org/abs/2604.21830v1)
- **Compliance Moral Hazard and the Backfiring Mandate** — [arxiv_lg](https://arxiv.org/abs/2604.21789v1)
- **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies** — [arxiv_ai](https://arxiv.org/abs/2604.21571v1)
- **Language as a Latent Variable for Reasoning Optimization** — [arxiv_cl](https://arxiv.org/abs/2604.21593v1)
- **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21774v1)
- **A Sociotechnical, Practitioner-Centered Approach to Technology Adoption in Cybersecurity Operations: An LLM Case** — [arxiv_cr](https://arxiv.org/abs/2604.21679v1)
- **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21477v1)
- **There Will Be a Scientific Theory of Deep Learning** — [arxiv_lg](https://arxiv.org/abs/2604.21691v1)
- **Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation** — [arxiv_ai](https://arxiv.org/abs/2604.21854v1)
- **Modulating Cross-Modal Convergence with Single-Stimulus, Intra-Modal Dispersion** — [arxiv_ai](https://arxiv.org/abs/2604.21836v1)
- **Alignment has a Fantasia Problem** — [arxiv_ai](https://arxiv.org/abs/2604.21827v1)
- **Quotient-Space Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2604.21809v1)
- **SyMTRS: Benchmark Multi-Task Synthetic Dataset for Depth, Domain Adaptation and Super-Resolution in Aerial Imagery** — [arxiv_ai](https://arxiv.org/abs/2604.21801v1)
- **Inferring High-Level Events from Timestamped Data: Complexity and Medical Applications** — [arxiv_ai](https://arxiv.org/abs/2604.21793v1)
- **MathDuels: Evaluating LLMs as Problem Posers and Solvers** — [arxiv_cl](https://arxiv.org/abs/2604.21916v1)
- **Mapping the Political Discourse in the Brazilian Chamber of Deputies: A Multi-Faceted Computational Approach** — [arxiv_cl](https://arxiv.org/abs/2604.21897v1)
- **Why are all LLMs Obsessed with Japanese Culture? On the Hidden Cultural and Regional Biases of LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21751v1)
- **AEL: Agent Evolving Learning for Open-Ended Environments** — [arxiv_ai](https://arxiv.org/abs/2604.21725v1)
- **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers** — [arxiv_ai](https://arxiv.org/abs/2604.21700v1)
- **Fine-Grained Perspectives: Modeling Explanations with Annotator-Specific Rationales** — [arxiv_ai](https://arxiv.org/abs/2604.21667v1)
- **Task-specific Subnetwork Discovery in Reinforcement Learning for Autonomous Underwater Navigation** — [arxiv_ai](https://arxiv.org/abs/2604.21640v1)
- **On the Role of Preprocessing and Memristor Dynamics in Reservoir Computing for Image Classification** — [arxiv_ai](https://arxiv.org/abs/2604.21602v1)
- **CoFEE: Reasoning Control for LLM-Based Feature Discovery** — [arxiv_ai](https://arxiv.org/abs/2604.21584v1)
- **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA** — [arxiv_cl](https://arxiv.org/abs/2604.21766v1)
- **From If-Statements to ML Pipelines: Revisiting Bias in Code-Generation** — [arxiv_cl](https://arxiv.org/abs/2604.21716v1)
- **Phonological Subspace Collapse Is Aetiology-Specific and Cross-Lingually Stable: Evidence from 3,374 Speakers** — [arxiv_cl](https://arxiv.org/abs/2604.21706v1)
- **How English Print Media Frames Human-Elephant Conflicts in India** — [arxiv_cl](https://arxiv.org/abs/2604.21496v1)
- **Generalizing Numerical Reasoning in Table Data through Operation Sketches and Self-Supervised Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21495v1)
- **Cross-Domain Data Selection and Augmentation for Automatic Compliance Detection** — [arxiv_cl](https://arxiv.org/abs/2604.21469v1)
- **Reasoning Primitives in Hybrid and Non-Hybrid LLMs** — [arxiv_cl](https://arxiv.org/abs/2604.21454v1)
- **AI-Gram: When Visual Agents Interact in a Social Network** — [arxiv_cl](https://arxiv.org/abs/2604.21446v1)
- **mcdok at SemEval-2026 Task 13: Finetuning LLMs for Detection of Machine-Generated Code** — [arxiv_cl](https://arxiv.org/abs/2604.21365v1)
- **CARE: Counselor-Aligned Response Engine for Online Mental-Health Support** — [arxiv_cl](https://arxiv.org/abs/2604.21352v1)
- **Mitigate or Fail: How Risk Management Shapes Cybersecurity Competency** — [arxiv_cr](https://arxiv.org/abs/2604.21604v1)
- **CSC: Turning the Adversary's Poison against Itself** — [arxiv_cr](https://arxiv.org/abs/2604.21416v1)
- **Adversarial Evasion in Non-Stationary Malware Detection: Minimizing Drift Signals through Similarity-Constrained Perturbations** — [arxiv_cr](https://arxiv.org/abs/2604.21310v1)
- **CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2604.21308v1)
- **Strategic Heterogeneous Multi-Agent Architecture for Cost-Effective Code Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2604.21282v1)
- **Interpretable facial dynamics as behavioral and perceptual traces of deepfakes** — [arxiv_lg](https://arxiv.org/abs/2604.21760v1)
- **Ramen: Robust Test-Time Adaptation of Vision-Language Models with Active Sample Selection** — [arxiv_lg](https://arxiv.org/abs/2604.21728v1)
- **Evaluating Post-hoc Explanations of the Transformer-based Genome Language Model DNABERT-2** — [arxiv_lg](https://arxiv.org/abs/2604.21690v1)
- **A-THENA: Early Intrusion Detection for IoT with Time-Aware Hybrid Encoding and Network-Specific Augmentation** — [arxiv_lg](https://arxiv.org/abs/2604.21623v1)
- **Verifying Machine Learning Interpretability Requirements through Provenance** — [arxiv_lg](https://arxiv.org/abs/2604.21599v1)
- **Dynamical Priors as a Training Objective in Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2604.21464v1)
- **Tempered Sequential Monte Carlo for Trajectory and Policy Optimization with Differentiable Dynamics** — [arxiv_lg](https://arxiv.org/abs/2604.21456v1)
- **Seeing Fast and Slow: Learning the Flow of Time in Videos** — [arxiv_ai](https://arxiv.org/abs/2604.21931v1)
- **When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21911v1)
- **From Research Question to Scientific Workflow: Leveraging Agentic AI for Science Automation** — [arxiv_ai](https://arxiv.org/abs/2604.21910v1)
- **Evaluation of Automatic Speech Recognition Using Generative Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21928v1)
- **EVENT5Ws: A Large Dataset for Open-Domain Event Extraction from Documents** — [arxiv_cl](https://arxiv.org/abs/2604.21890v1)
- **Revisiting Non-Verbatim Memorization in Large Language Models: The Role of Entity Surface Forms** — [arxiv_cl](https://arxiv.org/abs/2604.21882v1)
- **SemEval-2026 Task 4: Narrative Story Similarity and Narrative Representation Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21782v1)
- **CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis** — [arxiv_cr](https://arxiv.org/abs/2604.21917v1)
- **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles** — [arxiv_cr](https://arxiv.org/abs/2604.21841v1)
- **Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study** — [arxiv_cr](https://arxiv.org/abs/2604.21829v1)
- **Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability** — [arxiv_lg](https://arxiv.org/abs/2604.21930v1)
- **Fine-Tuning Regimes Define Distinct Continual Learning Problems** — [arxiv_lg](https://arxiv.org/abs/2604.21927v1)
- **The Sample Complexity of Multicalibration** — [arxiv_lg](https://arxiv.org/abs/2604.21923v1)
- **Low-Rank Adaptation Redux for Large Models** — [arxiv_lg](https://arxiv.org/abs/2604.21905v1)
- **Revealing Geography-Driven Signals in Zone-Level Claim Frequency Models: An Empirical Study using Environmental and Visual Predictors** — [arxiv_lg](https://arxiv.org/abs/2604.21893v1)
- **Beyond Expected Information Gain: Stable Bayesian Optimal Experimental Design with Integral Probability Metrics and Plug-and-Play Extensions** — [arxiv_lg](https://arxiv.org/abs/2604.21849v1)
- **On the algebra of Koopman eigenfunctions and on some of their infinities** — [arxiv_lg](https://arxiv.org/abs/2604.21825v1)
- **On the Challenges of Holistic Intrusion Detection in ICS** — [arxiv_cr](https://arxiv.org/abs/2604.21626v1)
- **Process-Mining of Hypertraces: Enabling Scalable Formal Security Verification of (Automotive) Network Architectures** — [arxiv_cr](https://arxiv.org/abs/2604.21606v1)
- **A Stackelberg Model for Hybridization in Cryptography** — [arxiv_cr](https://arxiv.org/abs/2604.21436v1)
- **Provably Secure Steganography Based on List Decoding** — [arxiv_cr](https://arxiv.org/abs/2604.21394v1)
- **ECCFROG522PP: An Enhanced 522 bit Weierstrass Elliptic Curve** — [arxiv_cr](https://arxiv.org/abs/2604.21261v1)
- **PrismaDV: Automated Task-Aware Data Unit Test Generation** — [arxiv_lg](https://arxiv.org/abs/2604.21765v1)
- **Anthropic created a test marketplace for agent-on-agent commerce** — [techcrunch_ai](https://techcrunch.com/2026/04/25/anthropic-created-a-test-marketplace-for-agent-on-agent-commerce/)
- **OpenAI CEO apologizes to Tumbler Ridge community** — [techcrunch_ai](https://techcrunch.com/2026/04/25/openai-ceo-apologizes-to-tumbler-ridge-community/)
- **Why Cohere is merging with Aleph Alpha** — [techcrunch_ai](https://techcrunch.com/2026/04/25/why-cohere-is-merging-with-aleph-alpha/)
- **Why Tokyo is the most important tech destination of 2026** — [techcrunch_ai](https://techcrunch.com/2026/04/25/why-tokyo-is-the-most-important-tech-destination-of-2026/)
- **Maine’s governor vetoes data center moratorium** — [techcrunch_ai](https://techcrunch.com/2026/04/25/maines-governor-vetoes-data-center-moratorium/)
- **Apple under Ternus: what comes next for the tech giant’s hardware strategy** — [techcrunch_ai](https://techcrunch.com/2026/04/25/apple-under-ternus-what-comes-next-for-the-tech-giants-hardware-strategy/)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **kaktusesquire6rmu/ai-polymarket-agent** — [github](https://github.com/kaktusesquire6rmu/ai-polymarket-agent)
- **linedelmont81825829134/LLM-Prompt-Orchestration-Engine** — [github](https://github.com/linedelmont81825829134/LLM-Prompt-Orchestration-Engine)
- **kimi-K2-6/kimi-K2.6** — [github](https://github.com/kimi-K2-6/kimi-K2.6)
- **selmakcby/claude-agents-skills** — [github](https://github.com/selmakcby/claude-agents-skills)
- **jwangkun/hermes-agent-guide** — [github](https://github.com/jwangkun/hermes-agent-guide)
- **chaohong-ai/ai-auto-work** — [github](https://github.com/chaohong-ai/ai-auto-work)
- **dainsiahtill-dev/Polaris** — [github](https://github.com/dainsiahtill-dev/Polaris)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **muxprotocol/kalshi-trading-bot** — [github](https://github.com/muxprotocol/kalshi-trading-bot)
- **alash3al/stash** — [github](https://github.com/alash3al/stash)
- **chekusu/wanman** — [github](https://github.com/chekusu/wanman)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **lydiaaam/llm-ui-coord-benchmark** — [github](https://github.com/lydiaaam/llm-ui-coord-benchmark)
- **dexwritescode/neurons** — [github](https://github.com/dexwritescode/neurons)
- **YilmazKadir/Volt** — [github](https://github.com/YilmazKadir/Volt)
- **hacktivist123/agent-session-resume** — [github](https://github.com/hacktivist123/agent-session-resume)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **K-Dense-AI/mimeo** — [github](https://github.com/K-Dense-AI/mimeo)
- **g2i-ai/agents** — [github](https://github.com/g2i-ai/agents)
- **华为发布ADS 5！强化世界模型路线，今年投入180亿** — [qbitai](https://www.qbitai.com/2026/04/407363.html)
- **自动驾驶赛道DeepSeek，轻舟智航率先进军物理AI** — [qbitai](https://www.qbitai.com/2026/04/407026.html)
- **硬刚GPT-Image-2！国产AI生图“天花板”又被捅破了？** — [qbitai](https://www.qbitai.com/2026/04/406994.html)
- **AI自主监测宠物健康，陪狗都不用自己来了！涂鸦Hey Tuya打造全屋智能“超级入口”** — [qbitai](https://www.qbitai.com/2026/04/406973.html)
- **燃油SUV车主熬出头了！华为乾崑智驾加持，全新奥迪Q5L率先实现智能化** — [qbitai](https://www.qbitai.com/2026/04/406960.html)
- **0博士组合拿下ICLR时间检验奖！两个GPT天才本科生+二本逆袭LeCun弟子，十年论文终封神** — [qbitai](https://www.qbitai.com/2026/04/406892.html)
- **芯擎科技发布新一代AI座舱芯片“龍鹰二号”，将于2027年Q1启动适配** — [36kr](https://36kr.com/newsflashes/3783080587926793?f=rss)
- **超算互联网推出DeepSeek-V4限时免费对话服务** — [36kr](https://36kr.com/newsflashes/3783020652518401?f=rss)
- **华泰证券：光纤光缆产业进入历史大周期** — [36kr](https://36kr.com/newsflashes/3782964689148937?f=rss)
- **湖南AI中心落地湘江新区** — [36kr](https://36kr.com/newsflashes/3782957337926921?f=rss)
- **36氪首发 | 全球唯二、中国唯一造出微米级磁悬浮魔毯，已大规模量产** — [36kr](https://36kr.com/p/3782960065108996?f=rss)
- **润芯微“国产软硬一体AI智能基座”发布，破解行业稀缺难题带动多端智能变革** — [36kr](https://36kr.com/p/3782901034785801?f=rss)
- **科氪 | 国民好车深蓝L06增程版亮相北京车展 京东PLUS会员购车直减7000多元** — [36kr](https://36kr.com/p/3782437007039488?f=rss)
- **最前线｜2025年全年营收超64亿，海康机器人表示将继续推进AI融合与具身智能布局** — [36kr](https://36kr.com/p/3782137908403457?f=rss)
- **元戎启行全面押注大模型自动驾驶** — [36kr](https://36kr.com/newsflashes/3782028988882178?f=rss)
- **百度智能云上线DeepSeek-V4** — [36kr](https://36kr.com/newsflashes/3781942204128513?f=rss)
- **卡尔动力发布KargoBot Inside** — [36kr](https://36kr.com/newsflashes/3782201831742724?f=rss)
- **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows** — [arxiv_ai](https://arxiv.org/abs/2604.21816v1)
- **VLAA-GUI: Knowing When to Stop, Recover, and Search, A Modular Framework for GUI Automation** — [arxiv_cl](https://arxiv.org/abs/2604.21375v1)
- **Seeing Isn't Believing: Uncovering Blind Spots in Evaluator Vision-Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21523v1)