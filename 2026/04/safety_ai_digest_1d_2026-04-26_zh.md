# AI Daily Digest [AI 安全] - 2026-04-26


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance

**Date:** 2026-04-26
**Author:** Senior AI Safety Research Analyst
**Theme:** Synthesis of Adversarial Robustness, Alignment Theory, Privacy Mechanisms, and Governance Frameworks

## Highlights

The current landscape of artificial intelligence safety research is defined by a critical shift from static model evaluation to dynamic, systemic risk assessment. Three developments stand out as particularly significant for the immediate future of safe deployment. First, the emergence of **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** fundamentally challenges the architectural assumptions of current moderation systems. By demonstrating how adversarial intent can be distributed across isolated interactions to evade stateless policy enforcement, this work exposes a vulnerability that is not merely a prompt engineering trick but a systemic flaw in how stateless LLMs handle context. The authors report that automated attacker agents can iteratively test and evade policy enforcement in both commercial and open-source LLMs, marking a departure from conventional jailbreak approaches. This finding necessitates a re-evaluation of how moderation pipelines are integrated into multi-turn workflows, suggesting that current defenses are insufficient against distributed adversarial strategies.

Second, the theoretical understanding of alignment is being refined through the lens of user intent formation, as detailed in **Alignment has a Fantasia Problem**. This paper argues that modern AI assistants are trained to follow instructions under the implicit assumption that users can clearly articulate their goals, whereas behavioral research indicates that people often engage with AI systems before their goals are fully formed. The authors introduce the concept of Fantasia interactions to describe failures where AI systems treat prompts as complete expressions of intent, potentially appearing useful but not necessarily aligned with the users' actual needs. This theoretical advance demands a rethinking of alignment research, moving beyond instruction following to support users in goal formation and clarification. It suggests that alignment is not just about the model's output but about the interactive process of defining the task itself.

Third, privacy-preserving personalization is advancing through architectural innovations that decouple user data from shared weights, as presented in **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies**. Current model training approaches incorporate user information directly into shared weights, making individual data removal computationally infeasible without retraining. This paper presents a three-layer architecture that decouples personal data from shared weights by combining a static base model, composable domain-expert LoRA adapters, and per-user proxy artefacts whose deletion constitutes deterministic unlearning. Evaluation on Phi-3.5-mini and Llama-3.1-8B confirms per-user differentiation where personal data influences outputs while remaining removable. This methodological innovation addresses the growing regulatory pressure for data deletion rights, offering a technical solution that balances personalization with compliance without the prohibitive cost of full model retraining.

## Adversarial Attacks & Robustness

The security of large language models and their integration into safety-critical systems remains a primary concern, with recent research highlighting vulnerabilities that extend beyond simple prompt injection. The paper **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** provides a critical examination of how stateless moderation systems can be bypassed. Unlike traditional jailbreaks that rely on maintaining a single adversarial context, this technique systematically exploits the lack of state by distributing adversarial intent across isolated interactions. The authors utilize automated attacker agents powered by large language models to iteratively test and evade policy enforcement. This approach marks a significant departure from conventional methods, suggesting that the security of multi-turn systems must be evaluated not just on individual turn safety but on the cumulative effect of distributed adversarial strategies. The implications are profound for any system relying on stateless moderation APIs, as the attack vector exploits the very design choice that enables scalability.

Complementing this focus on LLM vulnerabilities, **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers** addresses the threat of backdoor attacks that are difficult to detect due to their naturalistic appearance. Existing methods often suffer from explicit trigger patterns that compromise naturalness, unreliable injection of attacker-specified payloads in long-form generation, and incompletely specified threat models. To address these gaps, the authors present BadStyle, a complete backdoor attack framework that utilizes natural style triggers. This work highlights the difficulty of distinguishing between benign stylistic variations and malicious triggers, raising concerns about the robustness of LLMs in safety-critical domains where natural language generation is expected. The authors report that their method can embed backdoors that remain active even when the model is subjected to standard fine-tuning or adversarial training, indicating that current defense mechanisms may be insufficient against sophisticated, style-based attacks.

In the domain of physical security, **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** investigates the security of near-field millimeter-wave imaging algorithms, which are widely deployed in safety-critical applications such as airport passenger screening. The paper presents a systematic study of the adversarial robustness of these algorithms under waveform-domain physical attacks that directly manipulate the image reconstruction process. The authors propose a practical white-box adversarial model and develop a differential imaging attack framework that leverages the differentiable imaging pipeline to optimize attack waveforms. They also construct a real measured dataset to validate their findings. This research underscores the vulnerability of physical sensing systems to adversarial manipulation, suggesting that security measures must extend beyond the digital layer to the physical reconstruction process. The findings contradict the assumption that multi-sensor fusion inherently provides robustness, as the attack targets the fusion process itself.

Further expanding on the scope of adversarial threats, **Adversarial Evasion in Non-Stationary Malware Detection: Minimizing Drift Signals through Similarity-Constrained Perturbations** investigates a fundamental security question regarding malware detection in non-stationary environments. The authors ask whether an attacker can generate adversarial malware samples that simultaneously evade classification and remain inconspicuous to drift monitoring mechanisms. They propose a novel approach that generates targeted adversarial examples in the presence of continuous evolution of both malware characteristics and detection systems. This work is significant because it addresses the dynamic nature of real-world security environments, where static defenses are quickly rendered obsolete. The authors demonstrate that minimizing drift signals is a viable strategy for evasion, which implies that security monitoring systems must be designed to detect not just the presence of malware but also the subtle changes in behavior that indicate adversarial adaptation.

The intersection of adversarial attacks and industrial control systems is explored in **On the Challenges of Holistic Intrusion Detection in ICS**. Past attacks against industrial control systems show that adversaries often target both the ICS network and the physical process to achieve potential catastrophic impact. The paper presents challenges encountered during research towards holistic intrusion detection, noting that detection mechanisms typically focus on isolated characteristics of ICS, such as packet timings. This necessitates multiple detection systems deployed in parallel, complicating their operation in practice. The authors argue that a holistic approach is required to secure ICS, integrating network and physical process monitoring. This contrasts with the modular approach often taken in commercial security products, suggesting that the complexity of modern ICS requires a more integrated security architecture.

In the context of autonomous vehicles, **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles** investigates whether an attacker can bypass the redundancy of multi-sensor fusion by fabricating cross-sensor consistency. The authors design a coordinated, data-level attack that emulates the outcome of two synchronized physical sensors agreeing on the same false object. This work challenges the assumption that sensor redundancy safeguards against single-sensor failures, as the fusion process itself introduces a subtle vulnerability. The authors demonstrate that coordinated spoofing can bypass safety mechanisms that rely on consensus between modalities. This finding has significant implications for the safety certification of autonomous vehicles, suggesting that security testing must include coordinated adversarial attacks across multiple sensor types.

Finally, **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** presents a protocol-aware security testing framework that operationalizes developer pitfalls as reproducible scenarios. The Model Context Protocol (MCP) is increasingly adopted for tool-integrated LLM agents, but its multi-layer design and third-party server ecosystem expand risks across tool metadata, untrusted outputs, cross-tool flows, multimodal inputs, and supply-chain vectors. Existing MCP benchmarks largely measure robustness to malicious inputs but offer limited remediation guidance. The authors validate outcomes with MCP traces and objective validators rather than agent self-reports. This work provides a necessary tool for developers to understand the security implications of integrating MCP into their agent architectures, highlighting the need for standardized security testing protocols for agent tooling.

## Model Alignment & Interpretability

The theoretical foundations of alignment are being challenged by new insights into how models process information and how users interact with them. **Alignment has a Fantasia Problem** argues that modern AI assistants are trained to follow instructions under the implicit assumption that users can clearly articulate their goals, whereas behavioral research indicates that people often engage with AI systems before their goals are fully formed. The authors introduce the concept of Fantasia interactions to describe failures where AI systems treat prompts as complete expressions of intent, potentially appearing useful but not necessarily aligned with the users' actual needs. This theoretical advance demands a rethinking of alignment research, moving beyond instruction following to support users in goal formation and clarification. The authors suggest that alignment is not just about the model's output but about the interactive process of defining the task itself. This perspective shifts the focus from static model capabilities to dynamic user-model interaction, suggesting that future alignment research must account for the cognitive state of the user.

Complementing this focus on user intent, **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** characterizes machine behavior using the Whistleblower's Dilemma by varying two experimental dimensions: crime severity and relational closeness. The study evaluates three distinct perspectives: moral rightness, predicted human behavior, and autonomous model decision-making. By analyzing the responses, the authors determine whether models encode social nuances that are context-dependent and modulated by interpersonal relationships. This research is critical as large language models increasingly function as decision-support systems. The findings suggest that models may not fully capture the complexity of human moral judgment, which is often influenced by relationships rather than abstract principles. This has implications for deploying LLMs in legal or ethical advisory roles, where the nuance of human relationships is paramount.

The role of language in reasoning is explored in **Language as a Latent Variable for Reasoning Optimization**, which hypothesizes that language functions as a latent variable that structurally modulates the model's internal inference pathways, rather than merely serving as an output medium. To test this, the authors conducted a Polyglot Thinking Experiment, in which models were prompted to solve identical problems under language-constrained and language-unconstrained conditions. Results show that non-English responses often achieve higher accuracy, and the best performance frequently correlates with specific linguistic structures. This finding challenges the assumption that English is the optimal language for reasoning tasks, suggesting that the choice of language can significantly impact model performance. The authors propose that future research should investigate the structural properties of different languages that facilitate reasoning, potentially leading to new training strategies that leverage multilingual data more effectively.

In the realm of interpretability, **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** offers a solution for identifying moments of students' mechanistic reasoning for deeper analysis. The authors offer an interpretable machine learning model that outputs time-varying probabilities that individual students are engaging in acts of mechanistic reasoning, leveraging evidence from their own utterances as well as contributions from the rest of the group. Using the toolkit of intentionally-designed prompts, the model can identify high-concentration segments of reasoning. This work is significant for educational research, where understanding the cognitive processes of students is essential for improving learning outcomes. The authors demonstrate that their model can effectively identify reasoning acts without manual annotation, providing a scalable tool for analyzing educational interactions.

Further advancing interpretability, **Evaluating Post-hoc Explanations of the Transformer-based Genome Language Model DNABERT-2** adapts AttnLRP, an extension of layer-wise relevance propagation to the attention mechanism, to apply to the state-of-the-art gLM DNABERT-2. The authors propose that explaining deep neural network predictions on genome sequences enables biological insight and hypothesis generation, often of greater interest than predictive performance alone. While explanations of convolutional neural networks have been shown to capture relevant patterns in genome sequences, it is unclear whether this transfers to more expressive Transformer-based genome language models. The authors evaluate the transferability of explanation methods, finding that while some patterns are captured, the complexity of the attention mechanism introduces new challenges. This work highlights the need for specialized explanation methods for Transformer-based biological models, ensuring that the insights derived from these models are reliable and actionable.

The concept of mechanistic reasoning is further explored in **Reasoning Primitives in Hybrid and Non-Hybrid LLMs**, which studies reasoning through two such primitives, recall and state-tracking. The authors ask whether hybrid architectures that combine attention-based retrieval with recurrent state updates are better suited than attention-only models for tasks that jointly require both. Using matched Olmo3 transformer and hybrid models in instruction-tuned and reasoning-augmented variants, the authors evaluate these models on a set of controlled tasks involving a mixture of state-tracking and recall. The results suggest that hybrid architectures may offer advantages in specific reasoning contexts, particularly where long-term state maintenance is required. This finding supports the development of hybrid models for applications that require both retrieval and stateful reasoning, such as complex agent workflows.

Finally, **CoFEE: Reasoning Control for LLM-Based Feature Discovery** provides a structured method for addressing the challenge of feature discovery from complex unstructured data. The authors study reasoning control in LLMs by inducing cognitive behaviors that guide the model to identify abstractions that are predictive of a target outcome while avoiding leakage, proxies, and post-outcome signals. LLMs are well suited for this task by being able to process large amounts of information, but unconstrained feature generation can lead to weak features. The authors propose a framework for controlling the reasoning process to ensure that the generated features are robust and generalizable. This work is significant for data science applications, where feature engineering is a critical step in model development. The authors demonstrate that their method can improve the quality of features generated by LLMs, leading to better downstream performance.

## Privacy Protection & Federated Learning

Privacy-preserving techniques are evolving to meet the demands of regulatory compliance and data protection, with recent research focusing on differential privacy and unlearning mechanisms. **Differentially Private De-identification of Dutch Clinical Notes: A Comparative Evaluation** addresses the need for automated methods that combine privacy guarantees with high utility in clinical narratives. While manual de-identification remains the gold standard, it is costly and slow, motivating the need for automated methods. Most automated text de-identification pipelines employed named entity recognition to identify protected entities for redaction. Although methods based on differential privacy provide formal privacy guarantees, more recently also large language models are being explored for this task. The authors compare different approaches, evaluating the trade-offs between privacy guarantees and data utility. This work is critical for healthcare data sharing, where privacy regulations such as GDPR and HIPAA must be respected while enabling secondary use of data.

Complementing this focus on clinical data, **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study** systematically evaluates the impact of differential privacy mechanisms on statistical utility in survival analyses. The authors evaluate the impact of DP mechanisms (Laplace mechanism and Randomized Response) with data-driven clipping bounds on the Cox proportional hazards model, using 5 clinical datasets and 15 levels of epsilon. The data-driven clipping bounds used here are observed min/max and therefore do not require external knowledge. The results provide insights into the trade-offs between privacy and utility in statistical modeling, which is essential for researchers working with sensitive data. The authors demonstrate that data-driven clipping bounds can improve utility without compromising privacy guarantees, offering a practical approach for privacy-preserving statistical analysis.

The challenge of data removal is addressed in **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies**, which presents a three-layer architecture that decouples personal data from shared weights. Current model training approaches incorporate user information directly into shared weights, making individual data removal computationally infeasible without retraining. This paper presents a three-layer architecture that decouples personal data from shared weights by combining a static base model, composable domain-expert LoRA adapters that shape behavior without imparting user data, and per-user proxy artefacts whose deletion constitutes deterministic unlearning. Evaluation on Phi-3.5-mini and Llama-3.1-8B confirms per

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
- **TingIS: Real-time Risk Event Discovery from Noisy Customer Incidents at Enterprise Scale** — [arxiv_ai](https://arxiv.org/abs/2604.21889v1)
- **TraceScope: Interactive URL Triage via Decoupled Checklist Adjudication** — [arxiv_ai](https://arxiv.org/abs/2604.21840v1)
- **StructMem: Structured Memory for Long-Horizon Behavior in LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21748v1)
- **Process Supervision via Verbal Critique Improves Reasoning in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21611v1)
- **AgenticQwen: Training Small Agentic Language Models with Dual Data Flywheels for Industrial-Scale Tool Use** — [arxiv_cl](https://arxiv.org/abs/2604.21590v1)
- **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows** — [arxiv_ai](https://arxiv.org/abs/2604.21816v1)
- **Who Defines "Best"? Towards Interactive, User-Defined Evaluation of LLM Leaderboards** — [arxiv_ai](https://arxiv.org/abs/2604.21769v1)
- **Agentic AI-assisted coding offers a unique opportunity to instill epistemic grounding during software development** — [arxiv_ai](https://arxiv.org/abs/2604.21744v1)
- **Decoupled DiLoCo for Resilient Distributed Pre-training** — [arxiv_cl](https://arxiv.org/abs/2604.21428v1)
- **VLAA-GUI: Knowing When to Stop, Recover, and Search, A Modular Framework for GUI Automation** — [arxiv_cl](https://arxiv.org/abs/2604.21375v1)