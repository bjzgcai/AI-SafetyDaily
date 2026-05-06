# AI Daily Digest [AI 安全] - 2026-05-06


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-05-06
**Author:** Senior AI Safety Research Analyst

## Highlights

The most significant developments in today's literature center on the theoretical formalization of emergent risk in distributed systems, the structural vulnerabilities of agentic workflows, and novel defense mechanisms operating at the data ingestion layer. First, **Mechanical Conscience: A Mathematical Framework for Dependability of Machine Intelligenc** proposes a shift from evaluating individual agent actions to assessing global behavioral trajectories in distributed collaborative intelligence, addressing a critical gap where locally correct decisions compose into globally unacceptable outcomes. Second, **MOSAIC-Bench: Measuring Compositional Vulnerability Induction in Coding Agents** introduces a benchmark demonstrating that safety alignment often fails when tasks are decomposed into routine engineering tickets, revealing exploitable code emergence from sequenced compliance. Third, **PIIGuard: Mitigating PII Harvesting under Adversarial Sanitization** presents a webpage-level defense strategy that repurposes indirect prompt injection to protect public data, offering a deployable solution for ordinary page owners rather than relying solely on model-side mitigation.

## Adversarial Attacks & Robustness

The landscape of adversarial attacks is evolving from single-turn prompt manipulation to complex, context-aware, and multi-modal strategies. **ContextualJailbreak: Evolutionary Red-Teaming via Simulated Conversational Priming** highlights that automated optimization-based red-teaming has historically been limited to single-turn settings, whereas contextual priming through multi-turn scaffolds consistently outperforms static prompts on capable models. This finding complements the work in **Revisiting JBShield: Breaking and Revisiting Representation-Level Jailbreak Defenses**, which demonstrates that defenses like JBShield, which detect malicious prompts via concept signals, can be bypassed by modifying the objective to combine refusal-direction suppression with toxic concept detection. The authors report that their adaptive attack, JB-GCG, achieves an attack success rate where the original defense claimed 0% in non-adaptive settings, underscoring the necessity of adaptive threat models.

Further expanding the attack surface beyond text, **Exposing LLM Safety Gaps Through Mathematical Encoding: New Attacks and Systematic Analysis** reveals that encoding harmful prompts as coherent mathematical problems using formalisms such as set theory or quantum mechanics bypasses semantic pattern matching filters at high rates, achieving 46%–56% average attack success across eight target models. This suggests that safety mechanisms relying on semantic pattern matching are insufficient against formalized obfuscation. In the physical domain, **DECKER: Domain-invariant Embedding for Cross-Keyboard Extraction and Recognition** introduces the HEAR dataset to study acoustic side-channel attacks (ASCA), noting that prior studies are limited by small-scale datasets. The authors report that their domain-invariant embedding approach improves generalization across devices and noise conditions, indicating that physical side-channels remain a significant vector for sensitive information inference.

## Agent Security & Governance

As AI systems transition from static models to autonomous agents, the security paradigm must shift to accommodate dynamic tool use and long-horizon planning. **MOSAIC-Bench: Measuring Compositional Vulnerability Induction in Coding Agents** serves as a critical wake-up call, showing that coding agents often pass per-prompt safety reviews yet ship exploitable code when tasks are decomposed into routine engineering tickets. The benchmark pairs 199 three-stage attack chains with deterministic exploit oracles, proving that existing safety alignment evaluates overt requests in isolation while remaining blind to malicious end-states emerging from sequenced compliance. This structural vulnerability is addressed in part by **TRACE: A Metrologically-Grounded Engineering Framework for Trustworthy Agentic AI Systems in Operationally Critical Domains**, which combines a four-layer reference architecture with a stateful orchestration-and-escalation policy and bounded human supervision. The authors propose a metrologically grounded trust-metric suite mapped to GUM/VIM/ISO 17025 standards, aiming to provide formal guarantees for agents in domains like clinical decision support.

Security for agentic systems is further complicated by the need for stable control under adversarial pressure. **Stable Agentic Control: Tool-Mediated LLM Architecture for Autonomous Cyber Defense** presents a tool-mediated architecture where LLM agents use deterministic tools and select from finite action catalogs enforced at the tool-output interface. A composite Lyapunov function machine-checked in Lean 4 is used to provide formal guarantees, addressing the lack of stability in existing approaches. Complementing this, **ARGUS: Defending LLM Agents Against Context-Aware Prompt Injection** argues that existing benchmarks assume context-insensitive settings, failing to capture real-world deployments where agent behavior is influenced by dynamic context. The authors introduce a defense mechanism specifically designed for context-aware injection, contrasting with prior work that assumes static user instructions.

Memory management also presents a unique security and coherence challenge. **MEMTIER: Tiered Memory Architecture and Retrieval Bottleneck Analysis for Long-Running Autonomous AI Agents** identifies that tool-execution success rates degrade 14 percentage points over 72-hour operation windows due to compounding failure modes in flat-file memory systems. The proposed tripartite memory architecture introduces a structured episodic JSONL store and a five-signal weighted retrieval engine to maintain coherence. Meanwhile, **When Agents Handle Secrets: A Survey of Confidential Computing for Agentic AI** surveys the threat surface introduced by LLM-driven agents that accumulate sensitive context and hold credentials, noting that current defenses operate entirely within the software stack and can be bypassed by sufficiently privileged adversaries.

## Privacy Protection & Federated Learning

Privacy defenses are increasingly being tested by the complexity of multi-turn interactions and the release of model explanations. **PIIGuard: Mitigating PII Harvesting under Adversarial Sanitization** offers a webpage-level defense that repurposes indirect prompt injection, allowing page owners to embed optimized hidden HTML fragments that steer models away from verbatim PII extraction. This shifts the burden of protection from the model provider to the data owner. In the realm of federated learning and differential privacy, **Integrating Feature Correlation in Differential Privacy with Applications in DP-ERM** introduces a relaxed definition of differential privacy that accounts for feature heterogeneity. The authors propose **CorrDP**, which relaxes privacy for insensitive features while accounting for their correlations with sensitive ones, challenging the standard uniform privacy constraint.

However, privacy guarantees are not absolute even when explanations are released. **Graph Reconstruction from Differentially Private GNN Explanations** demonstrates that an adversary observing only DP-perturbed GNN explanations can reconstruct hidden graph structure with high accuracy. The attack, **PRIVX**, exploits the fact that the Gaussian DP mechanism is a single DDPM forward step at a known noise level, recasting reconstruction as revealing the underlying signal. This finding contradicts the assumption that releasing explanations with DP is sufficient. Furthermore, **Dependency-Aware Privacy for Multi-turn Agents** highlights that existing prompt sanitizers based on metric differential privacy treat each release independently, allowing adversaries to combine releases across turns to recover private attributes. The authors show that when private attributes are the roots of a computation graph, independently noising a derived value amplifies the root's distinguishability by up to the deriving function's Lipschich constant $L$, which can far exceed the nominal privacy parameter.

## Safety Benchmarks & Evaluation

The evaluation of AI safety is moving towards real-world, long-horizon, and domain-specific scenarios. **MOSAIC-Bench** stands out for its focus on compositional vulnerability in coding agents, moving beyond simple refusal rates to measure the emergence of exploitable code. In the medical domain, **PhysicianBench: Evaluating LLM Agents in Real-World EHR Environments** introduces a benchmark for evaluating LLM agents on physician tasks grounded in real clinical settings, comprising 100 long-horizon tasks adapted from real consultation cases. This contrasts with existing benchmarks that primarily focus on static knowledge recall or single-step atomic actions. Similarly, **TriBench-Ko: Evaluating LLM Risks in Judicial Workflows** releases a Korean benchmark designed to evaluate potential deployment risks of LLMs within verified judicial task requirements, covering jurisprudence summarization and evidence analysis.

The validity of safety datasets is also being scrutinized. **A Validated Prompt Bank for Malicious Code Generation: Separating Executable Weapons from Security Knowledge in 1,554 Consensus-Labeled Prompts** introduces a weapons-versus-knowledge classification axis, operationalized through a five-model consensus protocol. The authors argue that existing benchmarks conflate requests for executable malicious software with requests for harmful security knowledge, which plausibly trigger distinct refusal pathways. In clinical settings, **Atomic Fact-Checking Increases Clinician Trust in Large Language Model Recommendations for Oncology Decision Support: A Randomized Controlled Trial** reports that atomic fact-checking produced a large effect on trust, increasing the proportion of clinicians expressing trust from 26.9% to 66.5% compared to traditional transparency mechanisms. This suggests that verification mechanisms are more effective than general explainability for building trust in high-stakes domains.

## Tools & Frameworks

Open-source tools are emerging to support the engineering of safer systems. **GanyuanRan/Aegis** provides an architecture-driven development method pack for AI coding agents, emphasizing baseline-first, evidence-driven workflows and dual-track governance across hosts. This aligns with the theoretical need for structured development processes mentioned in **TRACE**. For multi-agent orchestration, **0xbl33p/goblintown** offers a multi-agent orchestration protocol featuring content-addressed, drift-monitored, and budget-capped execution, where different agents (Goblins, Gremlins, Trolls) handle task execution, output attack, and arbitration respectively. This reflects the need for diverse agent roles in complex workflows.

For safety evaluation, **YutoTerashima/agent-safety-eval-lab** provides an agent trace and tool-use safety evaluation lab, enabling systematic testing of agent behaviors. **csy-csy123/pr-review-agent-council** implements a PR Review Agent practice project that builds a Debate Council for multi-agent review, utilizing tool calling and structured reports. These tools operationalize the concepts of governance and evaluation discussed in the academic literature, providing practical infrastructure for developers to implement safety measures.

## Industry & Policy Context

In the policy sphere, **Google, Microsoft, and xAI will allow the US government to review their new AI models**, with the Commerce Department's Center for AI Standards and Innovation (CAISI) set to perform pre-deployment evaluations. This marks a significant shift towards government oversight in model release cycles. In the legal domain, **Apple agrees to pay iPhone owners $250 million for not delivering AI Siri**, a settlement regarding misleading customers about the availability of Apple Intelligence features. This highlights the legal risks associated with feature marketing and delivery timelines. Additionally, **Pennsylvania sues Character.AI after a chatbot allegedly posed as a doctor**, raising concerns about impersonation and the deployment of medical advice by unverified agents. These incidents underscore the regulatory pressure mounting on companies to ensure safety and accuracy in public-facing AI systems.

## Looking Forward

Several unresolved theoretical questions and hypotheses await validation as the field progresses. The **Mechanical Conscience** framework raises the question of whether a mathematical definition of "dependability" can be universally applied across heterogeneous distributed systems, or if it requires domain-specific calibration. The findings in **MOSAIC-Bench** and **ContextualJailbreak** suggest that safety alignment may need to be rethought from a trajectory-level optimization problem rather than a per-step classification task. In privacy, the **Dependency-Aware Privacy** paper implies that current differential privacy mechanisms may be fundamentally insufficient for multi-turn agents, necessitating a new theoretical framework for privacy accounting in computation graphs. Finally, the **TRACE** framework invites investigation into whether metrologically grounded trust metrics can be standardized across operationally critical domains without becoming prohibitively expensive to compute. The convergence of these lines of inquiry suggests a future where safety is not merely a filter but an intrinsic property of the

---


## References

- **Mechanical Conscience: A Mathematical Framework for Dependability of Machine Intelligenc** — [arxiv_ai](https://arxiv.org/abs/2605.03847v1)
- **ContextualJailbreak: Evolutionary Red-Teaming via Simulated Conversational Priming** — [arxiv_cr](https://arxiv.org/abs/2605.02647v1)
- **DECKER: Domain-invariant Embedding for Cross-Keyboard Extraction and Recognition** — [arxiv_cr](https://arxiv.org/abs/2605.03384v1)
- **BIT.UA-AAUBS at ArchEHR-QA 2026: Evaluating Open-Source and Proprietary LLMs via Prompting in Low-Resource QA** — [arxiv_cl](https://arxiv.org/abs/2605.03618v1)
- **PIIGuard: Mitigating PII Harvesting under Adversarial Sanitization** — [arxiv_cr](https://arxiv.org/abs/2605.03129v1)
- **MOSAIC-Bench: Measuring Compositional Vulnerability Induction in Coding Agents** — [arxiv_ai](https://arxiv.org/abs/2605.03952v1)
- **Contextual Multi-Objective Optimization: Rethinking Objectives in Frontier AI Systems** — [arxiv_ai](https://arxiv.org/abs/2605.03900v1)
- **TRACE: A Metrologically-Grounded Engineering Framework for Trustworthy Agentic AI Systems in Operationally Critical Domains** — [arxiv_ai](https://arxiv.org/abs/2605.03838v1)
- **Integrating Feature Correlation in Differential Privacy with Applications in DP-ERM** — [arxiv_lg](https://arxiv.org/abs/2605.03945v1)
- **Agent-Based Modeling of Low-Emission Fertilizer Adoption for Dairy Farm Decarbonisation using Empirical Farm Data** — [arxiv_ai](https://arxiv.org/abs/2605.03648v1)
- **Graph Reconstruction from Differentially Private GNN Explanations** — [arxiv_cr](https://arxiv.org/abs/2605.03388v1)
- **FINER-SQL: Boosting Small Language Models for Text-to-SQL** — [arxiv_cl](https://arxiv.org/abs/2605.03465v1)
- **LLM-XTM: Enhancing Cross-Lingual Topic Models with Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.03299v1)
- **Self-Mined Hardness for Safety Fine-Tuning** — [arxiv_cr](https://arxiv.org/abs/2605.03226v1)
- **Dependency-Aware Privacy for Multi-turn Agents** — [arxiv_cr](https://arxiv.org/abs/2605.03188v1)
- **Revisiting JBShield: Breaking and Rebuilding Representation-Level Jailbreak Defenses** — [arxiv_cr](https://arxiv.org/abs/2605.03095v1)
- **Distributed Deep Variational Approach for Privacy-preserving Data Release** — [arxiv_cr](https://arxiv.org/abs/2605.03069v1)
- **Stable Agentic Control: Tool-Mediated LLM Architecture for Autonomous Cyber Defense** — [arxiv_cr](https://arxiv.org/abs/2605.03034v1)
- **VertMark: A Unified Training-Free Robust Watermarking Framework for Vertical Domain Pre-trained Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.02557v1)
- **Perceptual Flow Network for Visually Grounded Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.02730)
- **Feature-Augmented Transformers for Robust AI-Text Detection Across Domains and Generators** — [arxiv_ai](https://arxiv.org/abs/2605.03969v1)
- **Magic-Informed Quantum Architecture Search** — [arxiv_ai](https://arxiv.org/abs/2605.03932v1)
- **PHALAR: Phasors for Learned Musical Audio Representations** — [arxiv_ai](https://arxiv.org/abs/2605.03929v1)
- **Atomic Fact-Checking Increases Clinician Trust in Large Language Model Recommendations for Oncology Decision Support: A Randomized Controlled Trial** — [arxiv_ai](https://arxiv.org/abs/2605.03916v1)
- **DMGD: Train-Free Dataset Distillation with Semantic-Distribution Matching in Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2605.03877v1)
- **EvoLM: Self-Evolving Language Models through Co-Evolved Discriminative Rubrics** — [arxiv_ai](https://arxiv.org/abs/2605.03871v1)
- **Quantifying the human visual exposome with vision language models** — [arxiv_ai](https://arxiv.org/abs/2605.03863v1)
- **RoboAlign-R1: Distilled Multimodal Reward Alignment for Robot Video World Models** — [arxiv_ai](https://arxiv.org/abs/2605.03821v1)
- **Agentic-imodels: Evolving agentic interpretability tools via autoresearch** — [arxiv_ai](https://arxiv.org/abs/2605.03808v1)
- **Say the Mission, Execute the Swarm: Agent-Enhanced LLM Reasoning in the Web-of-Drones** — [arxiv_ai](https://arxiv.org/abs/2605.03788v1)
- **HELO Cryptography: A Lightweight Cryptographic System for Enhancing IoT Security in P2P Data Transmission** — [arxiv_cr](https://arxiv.org/abs/2605.03948v1)
- **Firmware Distribution as Attack Surface: A Security Study of ASIC Cryptocurrency Miners** — [arxiv_cr](https://arxiv.org/abs/2605.03770v1)
- **TriBench-Ko: Evaluating LLM Risks in Judicial Workflows** — [arxiv_cl](https://arxiv.org/abs/2605.03792v1)
- **Task Vector Geometry Underlies Dual Modes of Task Inference in Transformers** — [arxiv_cl](https://arxiv.org/abs/2605.03780v1)
- **Optimal Posterior Sampling for Policy Identification in Tabular Markov Decision Processes** — [arxiv_lg](https://arxiv.org/abs/2605.03921v1)
- **Ecologically-Constrained Task Arithmetic for Multi-Taxa Bioacoustic Classifiers Without Shared Data** — [arxiv_lg](https://arxiv.org/abs/2605.03914v1)
- **Raising the Ceiling: Better Empirical Fixation Densities for Saliency Benchmarking** — [arxiv_lg](https://arxiv.org/abs/2605.03885v1)
- **On Adaptivity in Zeroth-Order Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.03869v1)
- **Nora: Normalized Orthogonal Row Alignment for Scalable Matrix Optimizer** — [arxiv_lg](https://arxiv.org/abs/2605.03769v1)
- **OracleProto: A Reproducible Framework for Benchmarking LLM Native Forecasting via Knowledge Cutoff and Temporal Masking** — [arxiv_ai](https://arxiv.org/abs/2605.03762v1)
- **Before Forgetting, Learn to Remember: Revisiting Foundational Learning Failures in LVLM Unlearning Benchmarks** — [arxiv_ai](https://arxiv.org/abs/2605.03759v1)
- **Rethinking the Rank Threshold for LoRA Fine-Tuning** — [arxiv_ai](https://arxiv.org/abs/2605.03724v1)
- **SERE: Structural Example Retrieval for Enhancing LLMs in Event Causality Identification** — [arxiv_ai](https://arxiv.org/abs/2605.03701v1)
- **MEMTIER: Tiered Memory Architecture and Retrieval Bottleneck Analysis for Long-Running Autonomous AI Agents** — [arxiv_ai](https://arxiv.org/abs/2605.03675v1)
- **ZK-Value: A Practical Zero-Knowledge System for Verifiable Data Valuation** — [arxiv_cr](https://arxiv.org/abs/2605.03581v1)
- **ARGUS: Defending LLM Agents Against Context-Aware Prompt Injection** — [arxiv_cr](https://arxiv.org/abs/2605.03378v1)
- **Cryptographic Registry Provenance: Structural Defense Against Dependency Confusion in AI Package Ecosystems** — [arxiv_cr](https://arxiv.org/abs/2605.03309v1)
- **Detecting Stealth Sycophancy in Mental-Health Dialogue with Dynamic Emotional Signature Graphs** — [arxiv_cl](https://arxiv.org/abs/2605.03472v1)
- **Exposing LLM Safety Gaps Through Mathematical Encoding:New Attacks and Systematic Analysis** — [arxiv_cl](https://arxiv.org/abs/2605.03441v1)
- **When to Think, When to Speak: Learning Disclosure Policies for LLM Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.03314v1)
- **SHIELD: A Diverse Clinical Note Dataset and Distilled Small Language Models for Enterprise-Scale De-identification** — [arxiv_cl](https://arxiv.org/abs/2605.03301v1)
- **Vanishing L2 regularization for the softmax Multi Armed Bandit** — [arxiv_lg](https://arxiv.org/abs/2605.03752v1)
- **Predicting missing values: A good idea?** — [arxiv_lg](https://arxiv.org/abs/2605.03733v1)
- **Uni-OPD: Unifying On-Policy Distillation with a Dual-Perspective Recipe** — [arxiv_lg](https://arxiv.org/abs/2605.03677v1)
- **Free Decompression with Algebraic Spectral Curves** — [arxiv_lg](https://arxiv.org/abs/2605.03634v1)
- **Exact and Approximate Algorithms for Polytree Learning** — [arxiv_lg](https://arxiv.org/abs/2605.03622v1)
- **When Agents Handle Secrets: A Survey of Confidential Computing for Agentic AI** — [arxiv_cr](https://arxiv.org/abs/2605.03213v1)
- **A Validated Prompt Bank for Malicious Code Generation: Separating Executable Weapons from Security Knowledge in 1,554 Consensus-Labeled Prompts** — [arxiv_cr](https://arxiv.org/abs/2605.03179v1)
- **HackerSignal: A Large-Scale Multi-Source Dataset Linking Hacker Community Discourse to the CVE Vulnerability Lifecycle** — [arxiv_cr](https://arxiv.org/abs/2605.03158v1)
- **Analyzing Unsolicited Internet Traffic: Measuring IoT Security Threats via Network Telescopes** — [arxiv_cr](https://arxiv.org/abs/2605.02795v1)
- **Dimensionality-Aware Anomaly Detection in Learned Representations of Self-Supervised Speech Models** — [arxiv_cr](https://arxiv.org/abs/2605.02715v1)
- **TeamUp: Semantic Project Matching and Team Formation for Learning at Scale** — [arxiv_cl](https://arxiv.org/abs/2605.03237v1)
- **T^2PO: Uncertainty-Guided Exploration Control for Stable Multi-Turn Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.02178)
- **Logical Consistency as a Bridge: Improving LLM Hallucination Detection via Label Constraint Modeling between Responses and Self-Judgments** — [arxiv_cl](https://arxiv.org/abs/2605.03971v1)
- **Transformers with Selective Access to Early Representations** — [arxiv_cl](https://arxiv.org/abs/2605.03953v1)
- **CC-OCR V2: Benchmarking Large Multimodal Models for Literacy in Real-world Document Processing** — [arxiv_cl](https://arxiv.org/abs/2605.03903v1)
- **Reproducing Complex Set-Compositional Information Retrieval** — [arxiv_cl](https://arxiv.org/abs/2605.03824v1)
- **Natural Language Processing: A Comprehensive Practical Guide from Tokenisation to RLHF** — [arxiv_cl](https://arxiv.org/abs/2605.03799v1)
- **Pretrained Model Representations as Acquisition Signals for Active Learning of MLIPs** — [arxiv_lg](https://arxiv.org/abs/2605.03964v1)
- **Exact ReLU realization of tensor-product refinement iterates** — [arxiv_lg](https://arxiv.org/abs/2605.03917v1)
- **Graph Neural Networks in the Wilson Loop Representation of Abelian Lattice Gauge Theories** — [arxiv_lg](https://arxiv.org/abs/2605.03901v1)
- **From Data Lifting to Continuous Risk Estimation: A Process-Aware Pipeline for Predictive Monitoring of Clinical Pathways** — [arxiv_lg](https://arxiv.org/abs/2605.03895v1)
- **Memory-Efficient Continual Learning with CLIP Models** — [arxiv_lg](https://arxiv.org/abs/2605.03866v1)
- **Complex Equation Learner: Rational Symbolic Regression with Gradient Descent in Complex Domain** — [arxiv_lg](https://arxiv.org/abs/2605.03841v1)
- **On Computing Total Variation Distance Between Mixtures of Product Distributions** — [arxiv_lg](https://arxiv.org/abs/2605.03839v1)
- **A Domain Incremental Continual Learning Benchmark for ICU Time Series Model Transportability** — [arxiv_lg](https://arxiv.org/abs/2605.03832v1)
- **Realizable Bayes-Consistency for General Metric Losses** — [arxiv_lg](https://arxiv.org/abs/2605.03823v1)
- **Benchmarking Parameter-Efficient Fine-Tuning of Large Language Models for Low-Resource Tajik Text Generation with the Tajik Web Corpus** — [arxiv_cl](https://arxiv.org/abs/2605.03742v1)
- **Rose-SQL: Role-State Evolution Guided Structured Reasoning for Multi-Turn Text-to-SQL** — [arxiv_cl](https://arxiv.org/abs/2605.03720v1)
- **A Comprehensive Analysis of Tokenization and Self-Supervised Learning in End-to-End Automatic Speech Recognition applied on French Language** — [arxiv_cl](https://arxiv.org/abs/2605.03696v1)
- **A Paradigm for Interpreting Metrics and Identifying Critical Errors in Automatic Speech Recognition** — [arxiv_cl](https://arxiv.org/abs/2605.03671v1)
- **Annotation Quality in Aspect-Based Sentiment Analysis: A Case Study Comparing Experts, Students, Crowdworkers, and Large Language Model** — [arxiv_cl](https://arxiv.org/abs/2605.03624v1)
- **OpenSeeker-v2: Pushing the Limits of Search Agents with Informative and High-Difficulty Trajectories** — [huggingface_papers](https://arxiv.org/abs/2605.04036)
- **SymptomAI: Towards a Conversational AI Agent for Everyday Symptom Assessment** — [huggingface_papers](https://arxiv.org/abs/2605.04012)
- **A Hybrid Approach for Closing the Sim2real Appearance Gap in Game Engine Synthetic Datasets** — [huggingface_papers](https://arxiv.org/abs/2605.02291)
- **MolmoAct2: Action Reasoning Models for Real-world Deployment** — [huggingface_papers](https://arxiv.org/abs/2605.02881)
- **Generative Modeling with Orbit-Space Particle Flow Matching** — [huggingface_papers](https://arxiv.org/abs/2605.02222)
- **AcademiClaw: When Students Set Challenges for AI Agents** — [huggingface_papers](https://arxiv.org/abs/2605.02661)
- **PhysicianBench: Evaluating LLM Agents in Real-World EHR Environments** — [huggingface_papers](https://arxiv.org/abs/2605.02240)
- **Google, Microsoft, and xAI will allow the US government to review their new AI models** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/924017/google-microsoft-xai-government-review)
- **SAP bets $1.16B on 18-month-old German AI lab and says yes to NemoClaw** — [techcrunch_ai](https://techcrunch.com/2026/05/05/sap-bets-1-16b-on-18-month-old-german-ai-lab-and-says-yes-to-nemoclaw/)
- **Google Home&#8217;s Gemini AI can handle more complicated requests** — [theverge_ai](https://www.theverge.com/tech/924755/google-home-gemini-3-1-upgrade)
- **Apple agrees to pay iPhone owners $250 million for not delivering AI Siri** — [theverge_ai](https://www.theverge.com/tech/924706/apple-iphone-siri-intelligence-class-action-lawsuit-settlement)
- **Apple plans to make iOS 27 a Choose Your Own Adventure of AI models** — [techcrunch_ai](https://techcrunch.com/2026/05/05/apple-plans-to-make-ios-27-a-choose-your-own-adventure-of-ai-models/)
- **ASML CEO Christophe Fouquet on his company’s monopoly: no one is coming for us** — [techcrunch_ai](https://techcrunch.com/2026/05/05/asml-ceo-christophe-fouquet-no-one-is-coming-for-us/)
- **Microsoft gives up on Xbox Copilot AI** — [theverge_ai](https://www.theverge.com/games/924551/microsoft-xbox-ceo-copilot-ai-asha-sharma)
- **Apple could let you pick a favorite AI model in iOS 27** — [theverge_ai](https://www.theverge.com/tech/924515/apple-intelligence-third-party-chatbot-extensions-ios-27)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **OpenAI claims ChatGPT’s new default model hallucinates way less** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/924225/openai-chatgpt-default-model-gpt-5-5-instant)
- **Pennsylvania sues Character.AI after a chatbot allegedly posed as a doctor** — [techcrunch_ai](https://techcrunch.com/2026/05/05/pennsylvania-sues-character-ai-after-a-chatbot-allegedly-posed-as-a-doctor/)
- **OpenAI releases GPT-5.5 Instant, a new default model for ChatGPT** — [techcrunch_ai](https://techcrunch.com/2026/05/05/openai-releases-gpt-5-5-instant-a-new-default-model-for-chatgpt/)
- **Book publishers sue Meta over AI&#8217;s &#8216;word-for-word&#8217; copying** — [theverge_ai](https://www.theverge.com/tech/924230/meta-publishers-lawsuit-ai-copyright)
- **OpenAI is reportedly launching a phone for ChatGPT** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/924063/openai-phone-rumors-2027-ming-chi-kuo)
- **PayPal says it’s ‘becoming a technology company again’ — that means AI** — [techcrunch_ai](https://techcrunch.com/2026/05/05/paypal-says-its-becoming-a-technology-company-again-that-means-ai/)
- **4 days left: Get 50% off a second TechCrunch Disrupt 2026 pass to make more deals faster** — [techcrunch_ai](https://techcrunch.com/2026/05/05/4-days-left-get-50-off-a-second-techcrunch-disrupt-2026-pass-to-make-more-deals-faster/)
- **Google is partnering with XPRIZE and Range Media Partners on the $3.5 million Future Vision film competition.** — [google_ai](https://blog.google/innovation-and-ai/technology/ai/future-vision-film-competition-xprize/)
- **What an AI-designed car looks like** — [theverge_ai](https://www.theverge.com/podcast/923974/ai-car-design-codex-vergecast)
- **The Download: inside the Musk v. Altman trial, and AI for democracy** — [mit_tech_review](https://www.technologyreview.com/2026/05/05/1136848/the-download-musk-openai-altman-trial-ai-democracy/)
- **A blueprint for using AI to strengthen democracy** — [mit_tech_review](https://www.technologyreview.com/2026/05/05/1136843/ai-democracy-blueprint/)
- **Altara secures $7M to bridge the data gap that’s slowing down physical sciences** — [techcrunch_ai](https://techcrunch.com/2026/05/05/altara-secures-7m-to-bridge-the-data-gap-thats-slowing-down-physical-sciences/)
- **Etsy launches its app within ChatGPT as it continues its AI push** — [techcrunch_ai](https://techcrunch.com/2026/05/05/etsy-launches-its-app-within-chatgpt-as-it-continues-its-ai-push/)
- **Meta will use AI to analyze height and bone structure to identify if users are underage** — [techcrunch_ai](https://techcrunch.com/2026/05/05/meta-will-use-ai-to-analyze-height-and-bone-structure-to-identify-if-users-are-underage/)
- **ElevenLabs lists BlackRock, Jamie Foxx, and Eva Longoria as new investors** — [techcrunch_ai](https://techcrunch.com/2026/05/05/elevenlabs-lists-blackrock-jamie-foxx-and-eva-longoria-as-new-investors/)
- **CopilotKit raises $27M to help devs deploy app-native AI agents** — [techcrunch_ai](https://techcrunch.com/2026/05/05/copilotkit-raises-27m-to-help-devs-deploy-app-native-ai-agents/)
- **India’s first GenAI unicorn shifts to cloud services as AI model ambitions face reality** — [techcrunch_ai](https://techcrunch.com/2026/05/05/indias-first-genai-unicorn-shifts-to-cloud-services-as-ai-model-ambitions-face-reality/)
- **GPT-5.5 Instant: smarter, clearer, and more personalized** — [openai](https://openai.com/index/gpt-5-5-instant)
- **As workers worry about AI, Nvidia’s Jensen Huang says AI is ‘creating an enormous number of jobs’** — [techcrunch_ai](https://techcrunch.com/2026/05/04/as-workers-worry-about-ai-nvidias-jensen-huang-says-ai-is-creating-an-enormous-number-of-jobs/)
- **GPT-5.5 Instant System Card** — [openai](https://openai.com/index/gpt-5-5-instant-system-card)
- **GanyuanRan/Aegis** — [github](https://github.com/GanyuanRan/Aegis)
- **csy-csy123/pr-review-agent-council** — [github](https://github.com/csy-csy123/pr-review-agent-council)
- **Wholiver/swiftui-design-skill** — [github](https://github.com/Wholiver/swiftui-design-skill)
- **0xbl33p/goblintown** — [github](https://github.com/0xbl33p/goblintown)
- **dmae97/oh-my-kimi** — [github](https://github.com/dmae97/oh-my-kimi)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **KSroido/Kagi-Session2API-MCP** — [github](https://github.com/KSroido/Kagi-Session2API-MCP)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **warpdot-dev/craft-agents-oss** — [github](https://github.com/warpdot-dev/craft-agents-oss)
- **warpdot-dev/composio** — [github](https://github.com/warpdot-dev/composio)
- **lukiIabs/trading-agents** — [github](https://github.com/lukiIabs/trading-agents)
- **StartupHakk/OpenMonoAgent.ai** — [github](https://github.com/StartupHakk/OpenMonoAgent.ai)
- **YutoTerashima/agent-safety-eval-lab** — [github](https://github.com/YutoTerashima/agent-safety-eval-lab)
- **arizen-dev/deepseek-mcp** — [github](https://github.com/arizen-dev/deepseek-mcp)
- **prime-radiant-inc/books-for-bots** — [github](https://github.com/prime-radiant-inc/books-for-bots)
- **bensenescu/downy** — [github](https://github.com/bensenescu/downy)
- **jmerelnyc/Photo-agents** — [github](https://github.com/jmerelnyc/Photo-agents)
- **刚刚，ChatGPT免费模型升级了：幻觉砍半/记忆更强/回答更简洁** — [qbitai](https://www.qbitai.com/2026/05/412995.html)
- **“北赛泓升”完成A+轮融资** — [36kr](https://36kr.com/newsflashes/3797145860644105?f=rss)
- **一家AI原生健康硬件公司完成近亿元融资，韶音、甘洁出手，高秉强投过｜硬氪首发** — [36kr](https://36kr.com/p/3682907323150215?f=rss)
- **Rivian称投入数亿美元自研芯片** — [36kr](https://36kr.com/newsflashes/3797114393943296?f=rss)
- **中信证券：一季度电子行业基金配置略有回落，超配比例仍处历史高位** — [36kr](https://36kr.com/newsflashes/3797081274719235?f=rss)
- **KKR称私募市场困境被夸大** — [36kr](https://36kr.com/newsflashes/3797079057898501?f=rss)
- **银河证券：建议关注景气度较高的上游算力基础设施** — [36kr](https://36kr.com/newsflashes/3797077145984262?f=rss)
- **华泰证券：短期行情或进入震荡期，风格层面建议哑铃配置** — [36kr](https://36kr.com/newsflashes/3797076129471752?f=rss)
- **8点1氪丨豆包新增付费订阅；抖音集团副总裁回应红果短剧付费；苹果因Siri人工智能功能推迟发布，以2.5亿美元和解诉讼** — [36kr](https://36kr.com/p/3797041945304327?f=rss)
- **恒指开盘涨0.51%，恒生科技指数涨0.85%** — [36kr](https://36kr.com/newsflashes/3797132055469057?f=rss)
- **两市融资余额减少167.42亿元** — [36kr](https://36kr.com/newsflashes/3797100627123206?f=rss)