# AI Daily Digest [AI 安全] - 2026-04-26


# AI Safety Thematic Digest
**Date:** 2026-04-26
**Theme:** AI Safety, Alignment, Security, Privacy, and Governance

## Highlights

Three significant developments define the current landscape of AI safety research. First, **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** introduces a novel attack vector where adversarial intent is distributed across isolated interactions to evade stateless moderation. This challenges the assumption that single-turn safety filters are sufficient for multi-turn workflows. Second, **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies** proposes a method for deterministic unlearning, addressing the computational infeasibility of data removal in shared weights. Third, **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows** identifies a critical efficiency bottleneck in the Model Context Protocol (MCP), suggesting that stateless schema injection imposes a hidden token overhead that degrades reasoning capabilities in agent systems.

## Adversarial Attacks & Robustness

Recent research highlights a shift from static input perturbations to dynamic, multi-modal, and system-level attacks. **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** demonstrates that LLMs integrated into sensitive workflows are vulnerable to attacks that distribute adversarial intent across isolated interactions. By leveraging automated attacker agents, the authors show that policy enforcement can be evaded in both commercial and open-source models without maintaining a persistent state, marking a departure from conventional jailbreak approaches. This finding complements **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers**, which addresses the limitations of existing backdoor methods that rely on explicit trigger patterns. The authors of the latter propose **BadStyle**, a framework that uses natural style triggers to improve the naturalness of attacks and reliability of payload injection in long-form generation.

In the physical domain, **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** explores security in safety-critical applications like airport screening. The study proposes a white-box adversarial model and a differential imaging attack framework that leverages the differentiable imaging pipeline to optimize attack waveforms. This work is significant because it moves beyond digital inputs to physical waveform manipulation. Similarly, **Adversarial Evasion in Non-Stationary Malware Detection: Minimizing Drift Signals through Similarity-Constrained Perturbations** investigates the ability of attackers to generate adversarial malware samples that evade classification while remaining inconspicuous to drift monitoring mechanisms. The authors propose a novel approach to minimize drift signals, suggesting that current non-stationary detection systems may be vulnerable to sophisticated evasion techniques that account for system evolution.

The intersection of generative AI and hardware security is further explored in **Addressing Image Authenticity When Cameras Use Generative AI** (Supplemental Article). This work notes that while generative AI methods are known to alter images, the integration of deep-learning modules into camera hardware—specifically the image signal processor (ISP)—creates a new risk vector. Hallucinated content can now be output directly by cameras, challenging the assumption that captured images are inherently authentic. This suggests that future authentication protocols must account for capture-time processing, not just post-processing.

## Model Alignment & Interpretability

Alignment research is increasingly focusing on the nuances of human intent and the structural properties of reasoning. **Alignment has a Fantasia Problem** argues that modern AI assistants assume users can clearly articulate goals, whereas behavioral research shows people often engage with AI before their goals are fully formed. The authors define "Fantasia interactions" as failures where AI systems treat prompts as complete expressions of intent, potentially misaligning with user needs. This necessitates a rethinking of alignment research to account for evolving user intent.

In the realm of reasoning, **Reasoning Primitives in Hybrid and Non-Hybrid LLMs** challenges the view of reasoning as a monolithic capability. The study investigates whether hybrid architectures combining attention-based retrieval with recurrent state updates are better suited than attention-only models for tasks requiring both recall and state-tracking. The results suggest that architectural choices significantly impact performance on controlled tasks involving mixed reasoning requirements. Complementing this, **Language as a Latent Variable for Reasoning Optimization** hypothesizes that language functions as a latent variable that structurally modulates the model's internal inference pathways. The authors report that non-English responses sometimes outperform English on reasoning tasks, suggesting that language choice can influence internal reasoning dynamics rather than merely serving as an output medium.

Moral alignment is examined through the lens of interpersonal relationships. **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** characterizes machine behavior using the Whistleblower's Dilemma, varying crime severity and relational closeness. The study evaluates three perspectives: moral rightness, predicted human behavior, and autonomous model decision-making. The findings indicate that human moral judgment is context-dependent, and determining whether models encode these social nuances is critical as they function as decision-support systems. Additionally, **Measuring Opinion Bias and Sycophancy via LLM-based Coercion** highlights the difficulty of eliciting a model's positions on contested topics. The authors note that contemporary assistants often answer direct opinion questions with evasive disclaimers, yet may concede the opposite position once the user starts arguing one side, raising concerns about silent position propagation at scale.

## Privacy Protection & Federated Learning

Privacy-preserving techniques are advancing to meet regulatory requirements while maintaining utility. **Differentially Private De-identification of Dutch Clinical Notes: A Comparative Evaluation** compares automated text de-identification pipelines, noting that while manual de-identification remains the gold standard, automated methods combining privacy guarantees with high utility are necessary. The study evaluates methods based on named entity recognition (NER) and differential privacy (DP), finding that DP provides formal guarantees but requires careful calibration to maintain utility. This is supported by **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study**, which systematically evaluates the impact of DP mechanisms on statistical utility in survival analyses. The authors report that data-driven clipping bounds observed min/max values, which do not guarantee privacy in all cases, highlighting the need for robust clipping strategies.

A significant advancement in personalization is presented in **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies**. Current training approaches incorporate user information directly into shared weights, making individual data removal computationally infeasible without retraining. The authors present a three-layer architecture that decouples personal data from shared weights by combining a static base model, composable domain-expert LoRA adapters, and per-user proxy artefacts. Evaluation on Phi-3.5-mini and Llama-3.1-8B confirms per-user differentiation, where personal data influences outputs while deletion constitutes deterministic unlearning. This addresses a critical gap in compliance with data deletion rights under regulations such as GDPR.

## Agent Security & Governance

The security of agentic systems is becoming a primary concern as LLMs operate in open-ended environments. **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** presents a protocol-aware security testing framework that operationalizes developer pitfalls as reproducible scenarios. The authors validate outcomes with MCP traces and objective validators, noting that existing benchmarks offer limited remediation guidance. This is critical given the multi-layer design and third-party server ecosystem of the Model Context Protocol (MCP), which expands risks across tool metadata, untrusted outputs, and supply-chain vectors.

Efficiency and security in agent workflows are addressed in **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows** (Supplemental Article). The authors identify that the reliance on stateless, eager schema injection imposes a hidden per-turn overhead, reported by practitioners to be between roughly 10k and 60k tokens in typical multi-server deployments. This payload inflates the key-value cache and is associated with reasoning degradation as context utilization approaches published fracture points. The proposed Tool Attention mechanism aims to mitigate this "Tools Tax," which turns token budgets into a recurring operational cost.

GUI automation security is examined in **VLAA-GUI: Knowing When to Stop, Recover, and Search, A Modular Framework for GUI Automation** (Supplemental Article). Autonomous GUI agents face challenges such as early stopping and repetitive loops. The framework integrates a mandatory Completeness Verifier that enforces UI-observable success criteria at every finish step. This addresses the risk of agents declaring success without verifiable evidence, a common failure mode in automated workflows.

Furthermore, **CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents** introduces a Contextual Integrity (CI)-grounded benchmark that simulates enterprise workflows across five information-flow directions. The evaluation of frontier models reveals that privacy failures are prevalent, with violation rates ranging from 15.8% to higher levels in dense retrieval settings. This underscores the risk of sensitive information leakage when agents retrieve and use internal context to act on a user's behalf.

In the domain of skill economy, **Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study** investigates the risks of a growing marketplace for agent skills. The authors note that free skill marketplaces report over 90,000 published skills, creating a new attack surface where adversaries can interact with public agents to extract hidden parameters or instructions. This highlights the need for secure skill encapsulation and verification mechanisms.

## Safety Benchmarks & Evaluation

Benchmarking efforts are evolving to address the limitations of static evaluations. **MathDuels: Evaluating LLMs as Problem Posers and Solvers** introduces a self-play benchmark where models occupy dual roles: authoring math problems under adversarial prompting and solving problems authored by every other participant. This addresses the inability of existing evaluations to differentiate model capabilities as frontier models attain near-ceiling performance on static mathematical benchmarks. The problems are produced through a three-stage generation pipeline and validated by independent checks.

**AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA** presents a large-scale, real-world benchmark to rigorously evaluate audio reasoning beyond surface-level acoustic recognition. The authors note that existing benchmarks often enable models to succeed through shortcut strategies, short-duration cues, or dataset-specific biases. AUDITA comprises carefully curated, human-authored trivia questions grounded in real-world audio, aiming to reduce reliance on metadata and captions.

**CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis** presents a curated benchmark of 15 real-world Python vulnerabilities where the exploitable condition was introduced across multiple commits. The authors report that the per-commit detection rate is 13% across all 15 vulnerabilities, indicating that 87% of these vulnerabilities evade per-commit analysis. This highlights the limitations of current static analysis tools in detecting vulnerabilities that only manifest in cumulative code changes.

**Misinformation Span Detection in Videos via Audio Transcripts** (Supplemental Article) addresses the challenge of video-based misinformation. The authors note that video-based misinformation represents a multifaceted challenge for fact-checkers, given the ease with which individuals can record and upload videos. The work proposes methods for detecting misinformation spans using audio transcripts, acknowledging that misinformation manifests in any platform with a large user base, including online social networks and messaging apps.

## Industry and Policy Context

Industry developments continue to shape the safety landscape, though claims require careful verification. In the autonomous driving sector, **Huawei states** that its ADS 5.0 system reinforces the world model route, with significant investment reported in the sector. However, specific performance claims should be treated as manufacturer statements until independently verified. Similarly, reports indicate that **Yuanrong Qixing** is fully betting on large model autonomous driving, with the CEO stating that multimodal large model capabilities have made the large model route superior to previous generations.

In the cloud and model deployment space, **Baidu Intelligent Cloud** launched the DeepSeek-V4 preview version, offering API services. Reports from **36kr** indicate that the model features a million-token context window, though this claim should be attributed to the reporting source rather than stated as an absolute technical specification. **National Supercomputing Internet** also launched a limited-time free dialogue service for DeepSeek-V4, allowing developers to deploy the model on their systems.

Regarding hardware and infrastructure, **TechCrunch** reported on **Apple's** incoming CEO John Ternus signaling a potential shift in hardware strategy. However, specific details regarding executive titles should be treated with caution until confirmed by official company channels. In the energy sector, **Maine’s governor** vetoed a data center moratorium, indicating a policy direction favoring continued infrastructure development.

In the automotive supply chain, **XinYing Technology** released the new AI cockpit chip "Long Eagle No. 2", with adaptation scheduled for Q1 2027. The chip reportedly supports 7B+ multimodal large models. **Runxin Micro** also released a "domestic software and hardware integrated AI intelligent base", aiming to address industry pain points such as core technology bottlenecks. These developments suggest a trend toward localized AI infrastructure, though the specific capabilities and safety implications of these proprietary systems require further independent analysis.

**OpenAI** has issued apologies regarding past safety incidents, including the Tumbler Ridge community event. While this event occurred in 2024, it remains relevant to ongoing discussions about safety governance and accountability. The CEO's letter expresses regret for failing to alert law enforcement, highlighting the persistent challenges in balancing safety and operational transparency.

## Looking Forward

Several theoretical questions remain unresolved. The relationship between language choice and internal reasoning pathways, as suggested by **Language as a Latent Variable for Reasoning Optimization**, requires further validation across diverse model architectures. It is unclear whether this effect is consistent or specific to certain training regimes. Similarly, the **Transient Turn Injection** attack raises questions about the fundamental limits of stateless moderation in multi-turn systems. Future work must determine if stateful moderation is a necessary condition for robust safety or if alternative architectural solutions exist.

The **Separable Expert Architecture** for privacy-preserving personalization introduces new trade-offs between unlearning efficiency and model performance. It remains to be seen how these composable adapters scale to larger models and more complex user profiles. Additionally, the **MCP/Tools Tax** identified in **Tool Attention Is All You Need** suggests that current agent protocols may be inefficient for long-horizon tasks. Future research should explore dynamic schema loading mechanisms that do not compromise security or interoperability.

Finally, the **Fantasia Problem** in alignment suggests that current instruction-following paradigms may be insufficient for users with evolving goals. Developing systems that can adapt to incomplete or evolving user intent without compromising safety remains a significant open challenge. The integration of these theoretical advances into practical safety frameworks will be critical for the next generation of AI systems.

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
- **Addressing Image Authenticity When Cameras Use Generative AI** — [arxiv_ai](https://arxiv.org/abs/2604.21879v1)
- **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows** — [arxiv_ai](https://arxiv.org/abs/2604.21816v1)
- **VLAA-GUI: Knowing When to Stop, Recover, and Search, A Modular Framework for GUI Automation** — [arxiv_cl](https://arxiv.org/abs/2604.21375v1)
- **Misinformation Span Detection in Videos via Audio Transcripts** — [arxiv_cl](https://arxiv.org/abs/2604.21767v1)