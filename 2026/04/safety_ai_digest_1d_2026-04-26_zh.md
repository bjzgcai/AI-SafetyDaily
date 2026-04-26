# AI Daily Digest [AI 安全] - 2026-04-26


# AI Daily Digest [AI 安全] - 2026-04-26


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-04-26

## Highlights

Three developments stand out in today's research landscape, reflecting a shift toward structural robustness and systemic evaluation. First, **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** introduces a novel attack vector that exploits stateless moderation by distributing adversarial intent across isolated interactions, challenging existing single-turn jailbreak defenses. Second, **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies** offers a methodological advance in privacy, decoupling personal data from shared weights to enable deterministic unlearning without full retraining. Third, **Learning to Communicate: Toward End-to-End Optimization of Multi-Agent Language Systems** proposes a framework for jointly optimizing latent communication and reasoning in multi-agent systems, addressing a gap in how agents exchange information beyond text-based protocols.

## Adversarial Attacks & Robustness

Recent work continues to expose vulnerabilities in LLMs and physical AI systems, moving beyond simple prompt injection to more sophisticated state exploitation. **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** demonstrates that commercial and open-source models are susceptible to attacks where adversarial intent is fragmented across multiple turns to evade policy enforcement. This contrasts with conventional jailbreak approaches that rely on maintaining a specific context window; instead, TTI leverages automated attacker agents to iteratively test and evade moderation. Complementing this, **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers** addresses the limitations of explicit trigger patterns. The authors report that their BadStyle framework utilizes natural style triggers to embed backdoors, improving the naturalness of the attack and reliability of payload injection in long-form generation.

Physical security remains a critical frontier. **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** systematically studies the security of safety-critical imaging algorithms used in airport screening. The authors propose a white-box adversarial model and a differential imaging attack framework that manipulates the image reconstruction process directly. This work highlights that redundancy in sensor fusion does not guarantee security, a finding echoed in **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles**. The latter investigates whether an attacker can bypass Multi-Sensor Fusion (MSF) by fabricating cross-sensor consistency, making multiple sensors agree on a false object. While TTI targets the logical layer of LLMs, these physical attacks target the perception layer, suggesting that robustness must be addressed across the entire AI stack.

## Model Alignment & Interpretability

Alignment research is increasingly focusing on the nuances of human intent and the internal mechanisms of reasoning. **Alignment has a Fantasia Problem** argues that modern AI assistants often fail when users have goals that are not fully formed, treating prompts as complete expressions of intent when they are not. The authors suggest that Fantasia interactions demand a rethinking of alignment research to accommodate users whose goals evolve during interaction. This aligns with findings in **Reasoning Primitives in Hybrid and Non-Hybrid LLMs**, which study whether hybrid architectures combining attention-based retrieval with recurrent state updates are better suited for tasks requiring both recall and state-tracking. The authors evaluate matched transformer and hybrid models, finding that the architectural choice significantly impacts performance on controlled tasks involving state-tracking.

Interpretability efforts are also expanding to specific domains. **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** offers an interpretable machine learning model that outputs time-varying probabilities of students engaging in mechanistic reasoning. This approach leverages evidence from individual utterances and group contributions, providing a tool for STEM education researchers to identify reasoning moments without manual transcript searching. In the realm of generative models, **Quotient-Space Diffusion Models** establishes a formal framework for diffusion modeling on general quotient spaces, applying it to molecular structure generation where symmetry identifies equivalent objects. This addresses the intrinsic problem structure of certain tasks, ensuring the target distribution is defined on the quotient space with respect to the group.

## Privacy Protection & Federated Learning

Privacy-preserving techniques are evolving to balance utility with formal guarantees, particularly in high-stakes domains like healthcare. **Differentially Private De-identification of Dutch Clinical Notes: A Comparative Evaluation** evaluates automated text de-identification pipelines using Named Entity Recognition (NER) and Differential Privacy (DP). While manual de-identification remains the gold standard, the authors compare DP methods to ensure privacy guarantees do not compromise utility. Similarly, **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study** systematically evaluates the impact of DP mechanisms on statistical utility in survival analyses. The study uses clinical datasets and 15 levels of $\varepsilon$, observing that data-driven clipping bounds can mitigate utility loss compared to fixed bounds.

A significant architectural shift is proposed in **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies**. Current training approaches incorporate user information directly into shared weights, making individual data removal computationally infeasible. This paper presents a three-layer architecture that decouples personal data from shared weights using composable domain-expert LoRA adapters and per-user proxy artefacts. Evaluation on Phi-3.5-mini and Llama-3.1-8B confirms per-user differentiation where personal data influences outputs while remaining deletable. This complements **Multilinguality at the Edge: Developing Language Models for the Global South**, which addresses the "last mile" challenge of deploying LMs in non-English-speaking and hardware-constrained communities. The authors note that technical requirements for edge deployment often compete with multilinguality goals, suggesting that privacy and accessibility must be considered together in resource-constrained settings.

## Safety Benchmarks & Evaluation

Evaluation methodologies are becoming more rigorous to differentiate model capabilities and detect hidden biases. **MathDuels: Evaluating LLMs as Problem Posers and Solvers** introduces a self-play benchmark where models author math problems under adversarial prompting and solve problems authored by others. This addresses the limitation of static mathematical benchmarks where models attain near-ceiling performance. The authors validate problems through a three-stage generation pipeline, ensuring that evaluations can differentiate model capabilities beyond fixed problem sets. In the domain of enterprise security, **CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents** introduces a Contextual Integrity (CI)-grounded benchmark that simulates enterprise workflows. The evaluation of frontier models reveals that privacy failures are prevalent, with violation rates ranging from 15.8% to higher figures depending on the information-flow direction.

The reliability of evaluators themselves is under scrutiny. **Seeing Isn't Believing: Uncovering Blind Spots in Evaluator Vision-Language Models** systematically evaluates the reliability of Evaluator VLMs across image-to-text and text-to-image tasks. The authors introduce targeted perturbations that degrade output quality along key error dimensions, including object hallucinations and spatial reasoning. This work suggests that reliance on VLMs for evaluation may introduce systematic errors if the evaluator itself is not robust to specific perturbations. Additionally, **CoFEE: Reasoning Control for LLM-Based Feature Discovery** provides a structured method for feature discovery from complex unstructured data. By inducing cognitive behaviors in LLMs, the authors aim to avoid leakage and proxies, ensuring that discovered features are predictive without relying on post-outcome signals.

## Agent Security & Governance

As agents become more autonomous, security frameworks must evolve to handle multi-vector risks. **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** presents a protocol-aware security testing framework for the Model Context Protocol (MCP). The authors operationalize developer pitfalls as reproducible scenarios, validating outcomes with MCP traces and objective validators. This is critical given that MCP's multi-layer design expands risks across tool metadata and supply-chain vectors. Complementing this, **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows** addresses the overhead of stateless, eager schema injection in MCP. The authors introduce Tool Attention to reduce the "Tools Tax," which inflates key-value cache and is associated with reasoning degradation as context utilization approaches published fracture points.

Long-term agent behavior is also a focus. **Agent Evolving Learning for Open-Ended Environments** introduces a two-timescale framework to address the obstacle of how agents use remembered experience. At the fast timescale, a Thompson sampling policy selects actions, while at the slow timescale, the agent updates its strategy based on prior outcomes. This contrasts with stateless agents that solve tasks from scratch. Furthermore, **Learning to Communicate: Toward End-to-End Optimization of Multi-Agent Language Systems** proposes DiffMAS, a training framework that treats latent communication as a learnable component of multi-agent systems. Unlike text-based protocols, DiffMAS jointly optimizes communication with multi-agent reasoning, offering a promising alternative for internal representation exchange.

## Industry & Deployment Context

Industry developments continue to shape the deployment landscape, though claims require independent verification. Recent announcements from hardware and software providers indicate a push toward sovereign AI alternatives and integrated computing platforms. For instance, reports indicate that **Cohere is merging with Aleph Alpha** with government support to offer a sovereign alternative to American players. Similarly, **Huawei has released ADS 5**, emphasizing a world model route for autonomous driving with significant investment. In the chip sector, **Xingyuan Technology released the "Longying No. 2" AI cockpit chip**, which claims to support 7B+ multimodal large models. While these developments suggest a trend toward localized and specialized AI infrastructure, the specific performance claims and security implications should be monitored through independent benchmarks.

In the realm of open-source tooling, several repositories have emerged to support agent development and security. **Polaris** is described as a transaction-driven AI software factory kernel that manages execution and audit. **Stash** provides a persistent memory layer for AI agents, storing episodes and facts in Postgres. These tools aim to address the operational challenges of agentic workflows, such as session management and context persistence. However, the security of these tools themselves must be evaluated, particularly as they integrate with Model Context Protocol servers and external APIs.

</think>

In the domain of robustness and environmental safety, recent advances in spatiotemporal super-resolution offer critical pathways for enhancing the reliability of climate and disaster monitoring systems. The paper **A Scale-Adaptive Framework for Joint Spatiotemporal Super-Resolution with Diffusion Models** addresses a persistent limitation in deep-learning video super-resolution, where existing models are often constrained to fixed spatial and temporal upscaling factors, hindering their transferability across diverse resolutions and frame rates. By introducing a scale-adaptive framework that reuses diffusion components across varying super-resolution factors, the authors propose a method capable of handling joint spatiotemporal upscaling without the need for retraining for each specific pair of factors. This innovation is particularly significant for safety-critical applications such as climate modeling and disaster response, where data availability often varies in both spatial granularity and temporal cadence. The authors report that their framework achieves superior performance compared to single-factor models, suggesting that adaptive diffusion mechanisms can provide more consistent and reliable high-fidelity reconstructions of dynamic environmental phenomena. This work underscores the importance of developing flexible generative priors that can adapt to the heterogeneous nature of real-world sensor data, thereby reducing the risk of misinterpretation in downstream safety-critical decision-making processes.

Parallel to developments in generative robustness, the field of parameter-efficient fine-tuning continues to evolve with a focus on minimizing computational overhead while maintaining model integrity. **GiVA: Gradient-Informed Bases for Vector-Based Adaptation** introduces a novel gradient-based initialization strategy for vector-based adaptation methods, aiming to overcome the performance gap that typically exists between these methods and the widely adopted Low-Rank Adaptation (LoRA). While vector-based adaptation offers extreme parameter efficiency, previous iterations required substantially higher ranks to match LoRA's performance, leading to increased training costs and potential stability issues. The authors demonstrate that by initializing the adaptation bases with gradient-informed vectors, the method can achieve comparable or superior performance with significantly lower rank requirements. This advancement has direct implications for the governance of large-scale model deployment, as it reduces the computational footprint required for domain-specific customization, thereby lowering the barrier to entry for organizations with limited resources. Furthermore, the reduced parameter count may mitigate risks associated with catastrophic forgetting and data leakage during the fine-tuning process, contributing to a more secure and efficient model lifecycle management strategy.

Finally, the intersection of interactive learning and agent safety is explored through the lens of strategic gaming environments in **Nemobot Games: Crafting Strategic AI Gaming Agents for Interactive Learning with Large Language Models**. This work presents Nemobot, an interactive agentic engineering environment that operationalizes Claude Shannon's taxonomy of game-playing machines, allowing users to create and deploy LLM-powered game agents while actively engaging with AI-driven strategies. The authors argue that such interactive environments provide a controlled sandbox for testing agent alignment, strategic reasoning, and emergent behaviors under adversarial conditions. By integrating an LLM-based chatbot within the Nemobot framework, the study demonstrates capabilities across four distinct classes of game-playing strategies, offering a novel paradigm for evaluating how agents adapt to dynamic, multi-agent interactions. This research is crucial for the safety community as it provides a testbed for observing how agents negotiate, cooperate, or compete, which are essential skills for safe deployment in complex real-world systems. The findings suggest that strategic gaming agents can serve as effective proxies for understanding the boundaries of agent autonomy and the potential for unintended strategic behaviors, thereby informing the development of more robust governance frameworks for autonomous systems.

## Looking Forward

Several unresolved theoretical questions and hypotheses await validation in the coming quarters. First, the relationship between latent communication and reasoning performance in multi-agent systems requires further empirical study. While DiffMAS proposes joint optimization, the extent to which latent communication outperforms text-based protocols in complex, open-ended environments remains to be determined. Second, the scalability of privacy-preserving personalization architectures, such as the Separable Expert Architecture, needs to be tested at larger parameter scales and across more diverse data distributions. Third, the robustness of evaluator VLMs against targeted perturbations suggests a need for standardized evaluation protocols that account for evaluator bias. Finally, the integration of physical security considerations into the broader AI safety framework remains nascent; as attacks like the Cross-Modal Phantom demonstrate, the boundary between logical and physical security is increasingly porous. Future research should aim to develop unified frameworks that address these interdependencies.

---



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
- **StructMem: Structured Memory for Long-Horizon Behavior in LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21748v1)
- **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows** — [arxiv_ai](https://arxiv.org/abs/2604.21816v1)
- **VLAA-GUI: Knowing When to Stop, Recover, and Search, A Modular Framework for GUI Automation** — [arxiv_cl](https://arxiv.org/abs/2604.21375v1)
- **Learning to Communicate: Toward End-to-End Optimization of Multi-Agent Language Systems** — [arxiv_ai](https://arxiv.org/abs/2604.21794v1)
- **Multilinguality at the Edge: Developing Language Models for the Global South** — [arxiv_cl](https://arxiv.org/abs/2604.21637v1)
- **Seeing Isn't Believing: Uncovering Blind Spots in Evaluator Vision-Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21523v1)
- **A Scale-Adaptive Framework for Joint Spatiotemporal Super-Resolution with Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2604.21903v1)
- **GiVA: Gradient-Informed Bases for Vector-Based Adaptation** — [arxiv_ai](https://arxiv.org/abs/2604.21901v1)
- **Nemobot Games: Crafting Strategic AI Gaming Agents for Interactive Learning with Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21896v1)