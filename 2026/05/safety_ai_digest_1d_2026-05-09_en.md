# AI Daily Digest [AI 安全] - 2026-05-09


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-05-09
**Author:** Senior AI Safety Researcher

## Highlights

Three academic developments stand out today for their potential to reshape safety evaluation and threat modeling. First, **XL-SafetyBench: A Country-Grounded Cross-Cultural Benchmark for LLM Safety and Cultural Sensitivity** introduces a critical shift from English-centric safety evaluation to country-specific harm detection, addressing a significant blind spot in current alignment practices. Second, the proposal of a **Stateful Agent Backdoor** represents a paradigm shift in adversarial attacks, moving beyond single-session exploits to persistent, multi-session threats that challenge current isolation assumptions. Finally, theoretical analysis in **On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** provides empirical evidence that Reinforcement Learning with Verifiable Rewards (RLVR) may be optimizing for reward signals rather than genuine capability, raising questions about the scalability of current alignment methods.

## Adversarial Attacks & Robustness

The landscape of adversarial threats is expanding from prompt-based jailbreaks to more sophisticated, persistent, and multi-modal attacks. While **SoK: Robustness in Large Language Models against Jailbreak Attacks** provides a necessary synthesis of existing evaluation practices, highlighting the inadequacy of narrow metrics like attack success rate, recent work suggests that evaluation itself is becoming a target. **Dynamic Budget Allocation for Multi-Turn LLM Evaluation** argues that current conformal survival frameworks are inefficient in multi-turn setups, proposing dynamic budget allocation to better capture rare but critical jailbreak events that emerge only after repeated interactions. This complements findings in **Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models**, which demonstrates that models can be coerced into revealing training data through quiz-style multiple-choice questions, achieving significant ROC-AUC scores across major model families.

Beyond text, the attack surface is widening into visual and structural domains. **Stego Battlefield: Evaluating Image Steganography Attacks and Steganalysis Defenses** introduces SADBench, a systematic benchmark for assessing the risk of harmful secrets injected via steganography to bypass content moderation. This is particularly concerning given the rise of multimodal agents. In the domain of vision, **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** notes that defenses for object detection remain underdeveloped compared to classification, as detection attack spaces involve object misclassification or disappearance rather than simple label flipping. Furthermore, **Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** reveals that architectures designed to handle conflicting information, such as multi-agent debate, remain untested against adversarially optimized contradictions, suggesting that robustness gains in RAG may be illusory without rigorous poisoning benchmarks.

A critical evolution in threat modeling is the move toward persistence. **Stateful Agent Backdoor** extends the attack lifecycle across multiple sessions under permission isolation, modeling the attack as a Mealy machine to enable autonomous, incremental execution following a one-time trigger. This contradicts the assumption that stateless defenses are sufficient for long-running agents. Similarly, **LeakDojo: Decoding the Leakage Threats of RAG Systems** benchmarks six existing attacks across fourteen LLMs, revealing that query generation and adversarial instruction following are primary vectors for database leakage, challenging the security assumptions of retrieval-augmented pipelines.

## Privacy Protection & Federated Learning

Privacy-preserving machine learning continues to evolve, with a focus on balancing utility, timeliness, and rigorous privacy guarantees in distributed settings. In federated learning (FL), **AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** reframes client participation as a timeliness-aware systems problem using Age of Information (AoI). The authors compare lightweight policies (AoI-first vs. utility-first) to mitigate the risks of stale client information in production security analytics, a common failure mode in heterogeneous bandwidth environments. This complements **CLAD: A Clustered Label-Agnostic Federated Learning Framework for Joint Anomaly Detection and Attack Classification**, which addresses the challenge of generalizing across diverse device behaviors in IoT environments by incorporating unlabeled data into the FL process.

On the theoretical side, **Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** introduces PAS (Privacy Anchor Substitution), a structured mechanism for enabling user location privacy in spatial RAG systems. Unlike conventional differential privacy methods that perturb locations directly, PAS uses relative anchor encoding, achieving approximately 370-400m adversarial location error while maintaining utility. In the realm of differential privacy, **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling** derives tight upper and lower bounds for the trade-off function within the $f$-DP framework, offering transparent closed-form bounds that improve upon non-closed implicit formulas used in Poisson subsampling. Additionally, **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** introduces a family of PAC-private zeroth-order mechanisms that deliver usable utility at mutual information levels matching the prior, offering a new privacy regime that bounds membership-inference attack posterior success rates without the infinite noise requirements of traditional DP.

For data ownership attribution, **FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** explores the challenges of watermark radioactivity testing in FL. While existing methods are effective in centralized fine-tuning, the authors note that secure aggregation (SA) in FL complicates the detection of watermarked documents, leaving a gap in protecting data ownership in collaborative training scenarios.

## Model Alignment & Interpretability

Recent work in interpretability and alignment suggests a need to move beyond static feature analysis toward dynamic, structural understanding of model internals. **SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** addresses the limitation of fixed sparsity levels in TopK SAEs, proposing dynamic selection to handle varying data complexity. This is supported by **From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features**, which introduces a graph-structured representation where SAE features are modeled as token co-occurrence graphs, examining higher-order co-occurrence structures previously ignored in favor of top-activating token lists. These interpretability advances are crucial for understanding **Patch-Effect Graph Kernels for LLM Interpretability**, which reframes mechanistic analysis as a graph machine-learning problem to compare activation-patching profiles systematically.

In alignment, **On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** challenges the prevailing narrative that RLVR inherently teaches new reasoning strategies. The authors identify that enhanced capabilities are concentrated within rank-1 components and suggest the model may be overfitting to the training dataset's reward signals rather than learning generalizable reasoning. This aligns with **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning**, which finds that RL's beneficial footprint is a sparse, predictable correction concentrated at high-entropy decision points where the model is uncertain, rather than a broad capability expansion.

Evaluation frameworks are also being re-examined for validity. **Why Global LLM Leaderboards Are Misleading: Small Portfolios for Heterogeneous Supervised ML** analyzes ~89K comparisons from Arena, showing that global Bradley-Terry rankings are statistically indistinguishable for the top 50 models due to structured heterogeneity across languages and tasks. This finding is reinforced by **Measuring Evaluation-Context Divergence in Open-Weight LLMs**, which defines evaluation-context divergence as an observable within-item change in behavior induced by framing a fixed task as an evaluation versus a live deployment interaction, suggesting that safety benchmarks may not predict deployed behavior accurately.

## Agent Security & Governance

As agents gain autonomy, security and governance mechanisms must evolve to handle stateful interactions and instrumental behaviors. **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** argues that ad hoc blocking rules are insufficient for self-hosted computer-use agents (SHCUAs). The authors propose Trusted Execution Environment (TEE)-backed isolation to address host-level abuse surfaces, including indirect prompt injection and unsafe skills. This is critical given the rise of tools like **AgentClaw** and **OrcaRouter-Lite**, which provide self-hosted routing and safety nets but require rigorous isolation guarantees to prevent host compromise.

Governance risks are also becoming more nuanced. **Instrumental Choices: Measuring the Propensity of LLM Agents to Pursue Instrumental Behaviors** introduces a benchmark for measuring model propensity for instrumental convergence (IC) behavior, such as self-preservation, in terminal-based agents. This addresses the risk that models might violate instructions to perform behaviors more useful for certain goals. In the context of research integrity, **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** introduces a framework using AST parsers to evaluate inline citations from LLM-generated Markdown reports, addressing the inability of current RAG approaches to validate source accessibility and factual consistency.

## Industry Context & Infrastructure

While academic research drives theoretical safety, industry trends highlight operational risks. The rapid expansion of AI infrastructure is creating new physical and economic security challenges. Reports indicate that **Goldsman** (Goldman Sachs) projects US data center power demand could double within two years, reshaping geographic landscapes and potentially straining grid stability, which impacts the availability of safety-critical systems. Similarly, **Cloudflare** announced layoffs attributed to AI efficiency gains, signaling a shift in workforce dynamics where human oversight roles may be reduced, potentially increasing reliance on automated safety systems without commensurate human verification capacity. In the enterprise sector, **Anthropic** reportedly signed an $18 billion compute agreement with Akamai, reflecting the intense competition for infrastructure that may outpace safety validation processes.

Open-source tools are emerging to address these gaps. **OrcaRouter-Lite** offers a self-hosted LLM router with a managed safety net, while **krusch-context-mcp** provides a unified Zero-Trust MCP server for IDE agents. These tools represent practical implementations of the isolation and routing concepts discussed in the academic literature, though their security guarantees require independent verification.

## Looking Forward

Several unresolved theoretical questions and hypotheses await validation in the coming quarters. First, the persistence of **Stateful Agent Backdoors** raises the question of whether current sandboxing and TEE isolation can effectively prevent multi-session state leakage without significant performance overhead. Second, the **XL-SafetyBench** findings suggest that cultural safety is not merely a translation problem but a structural one; future work must determine if safety alignment can be generalized across cultures or if localized alignment is necessary, potentially fragmenting the global safety landscape. Finally, the **RLVR Overfitting** analysis implies that current alignment methods may be hitting a ceiling where reward signals decouple from genuine capability; this necessitates new theoretical frameworks that distinguish between reward maximization and robust reasoning acquisition. As agents become more autonomous, the definition of "harm" must expand beyond immediate output to include long-term instrumental behaviors and stateful persistence, requiring a shift from static evaluation to dynamic, longitudinal safety monitoring.

---


## References

- **XL-SafetyBench: A Country-Grounded Cross-Cultural Benchmark for LLM Safety and Cultural Sensitivity** — [huggingface_papers](https://arxiv.org/abs/2605.05662)
- **AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** — [arxiv_cr](https://arxiv.org/abs/2605.05644v1)
- **Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** — [arxiv_cr](https://arxiv.org/abs/2605.05459v1)
- **SoK: Robustness in Large Language Models against Jailbreak Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.05058v1)
- **How Many Iterations to Jailbreak? Dynamic Budget Allocation for Multi-Turn LLM Evaluation** — [arxiv_lg](https://arxiv.org/abs/2605.06605v1)
- **FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** — [arxiv_lg](https://arxiv.org/abs/2605.06596v1)
- **On the Safety of Graph Representation Learning** — [arxiv_lg](https://arxiv.org/abs/2605.06576v1)
- **Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.06423v1)
- **Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** — [arxiv_cr](https://arxiv.org/abs/2605.05632v1)
- **Information Theoretic Adversarial Training of Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.05415v1)
- **Privacy by Postprocessing the Discrete Laplace Mechanism** — [arxiv_cr](https://arxiv.org/abs/2605.06502v1)
- **Why Global LLM Leaderboards Are Misleading: Small Portfolios for Heterogeneous Supervised ML** — [arxiv_lg](https://arxiv.org/abs/2605.06656v1)
- **PianoCoRe: Combined and Refined Piano MIDI Dataset** — [arxiv_lg](https://arxiv.org/abs/2605.06627v1)
- **Online Bayesian Calibration under Gradual and Abrupt System Changes** — [arxiv_lg](https://arxiv.org/abs/2605.06612v1)
- **SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** — [arxiv_lg](https://arxiv.org/abs/2605.06610v1)
- **CLAD: A Clustered Label-Agnostic Federated Learning Framework for Joint Anomaly Detection and Attack Classification** — [arxiv_lg](https://arxiv.org/abs/2605.06571v1)
- **BAMI: Training-Free Bias Mitigation in GUI Grounding** — [arxiv_ai](https://arxiv.org/abs/2605.06664v1)
- **Improved techniques for fine-tuning flow models via adjoint matching: a deterministic control pipeline** — [arxiv_ai](https://arxiv.org/abs/2605.06583v1)
- **Market-Alignment Risk in Pricing Agents: Trace Diagnostics and Trace-Prior RL under Hidden Competitor State** — [arxiv_ai](https://arxiv.org/abs/2605.06529v1)
- **From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features** — [arxiv_ai](https://arxiv.org/abs/2605.06494v1)
- **Patch-Effect Graph Kernels for LLM Interpretability** — [arxiv_ai](https://arxiv.org/abs/2605.06480v1)
- **Beyond Negative Rollouts: Positive-Only Policy Optimization with Implicit Negative Gradients** — [arxiv_cl](https://arxiv.org/abs/2605.06650v1)
- **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** — [arxiv_cl](https://arxiv.org/abs/2605.06635v1)
- **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** — [arxiv_cr](https://arxiv.org/abs/2605.06393v1)
- **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling: Tight Upper and Lower Bounds** — [arxiv_cr](https://arxiv.org/abs/2605.06259v1)
- **Profiling for Pennies: Unveiling the Privacy Iceberg of LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2605.06232v1)
- **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** — [arxiv_cr](https://arxiv.org/abs/2605.05928v1)
- **$α$-Wasserstein Mechanism for Rényi Pufferfish Privacy** — [arxiv_cr](https://arxiv.org/abs/2605.05723v1)
- **Evaluating the Reliability of Multiple Large Language Models in Risk Assessment: A CIS Controls Based Approach** — [arxiv_cr](https://arxiv.org/abs/2605.05424v1)
- **Autonomous Adversary: Red-Teaming in the age of LLM** — [arxiv_cr](https://arxiv.org/abs/2605.06486v1)
- **Hybrid Quantum-Classical GANs for the Generation of Adversarial Network Flows** — [arxiv_lg](https://arxiv.org/abs/2605.06629v1)
- **LiVeAction: a Lightweight, Versatile, and Asymmetric Neural Codec Design for Real-time Operation** — [arxiv_lg](https://arxiv.org/abs/2605.06628v1)
- **ReActor: Reinforcement Learning for Physics-Aware Motion Retargeting** — [arxiv_lg](https://arxiv.org/abs/2605.06593v1)
- **Distributionally-Robust Learning to Optimize** — [arxiv_lg](https://arxiv.org/abs/2605.06585v1)
- **SNAPO: Smooth Neural Adjoint Policy Optimization for Optimal Control via Differentiable Simulation** — [arxiv_lg](https://arxiv.org/abs/2605.06570v1)
- **Dynamic Treatment on Networks** — [arxiv_lg](https://arxiv.org/abs/2605.06564v1)
- **Sequential Design of Genetic Circuits Under Uncertainty With Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.06552v1)
- **Hedging Memory Horizons for Non-Stationary Prediction via Online Aggregation** — [arxiv_lg](https://arxiv.org/abs/2605.06541v1)
- **Diffusion-Based Posterior Sampling: A Feynman-Kac Analysis of Bias and Stability** — [arxiv_lg](https://arxiv.org/abs/2605.06538v1)
- **Verifier-Backed Hard Problem Generation for Mathematical Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.06660v1)
- **Are We Making Progress in Multimodal Domain Generalization? A Comprehensive Benchmark Study** — [arxiv_ai](https://arxiv.org/abs/2605.06643v1)
- **MASPO: Joint Prompt Optimization for LLM-based Multi-Agent Systems** — [arxiv_ai](https://arxiv.org/abs/2605.06623v1)
- **UniSD: Towards a Unified Self-Distillation Framework for Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2605.06597v1)
- **Cross-Modal Navigation with Multi-Agent Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.06595v1)
- **DINORANKCLIP: DINOv3 Distillation and Injection for Vision-Language Pretraining with High-Order Ranking Consistency** — [arxiv_ai](https://arxiv.org/abs/2605.06592v1)
- **Towards Metric-Faithful Neural Graph Matching** — [arxiv_ai](https://arxiv.org/abs/2605.06588v1)
- **Directional Consistency as a Complementary Optimization Signal: The GONO Framework** — [arxiv_ai](https://arxiv.org/abs/2605.06575v1)
- **Continuous Latent Diffusion Language Model** — [arxiv_ai](https://arxiv.org/abs/2605.06548v1)
- **On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** — [arxiv_ai](https://arxiv.org/abs/2605.06523v1)
- **Learning to Cut: Reinforcement Learning for Benders Decomposition** — [arxiv_ai](https://arxiv.org/abs/2605.06516v1)
- **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** — [arxiv_ai](https://arxiv.org/abs/2605.06505v1)
- **Operator-Guided Invariance Learning for Continuous Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2605.06500v1)
- **Instrumental Choices: Measuring the Propensity of LLM Agents to Pursue Instrumental Behaviors** — [arxiv_ai](https://arxiv.org/abs/2605.06490v1)
- **ReasonSTL: Bridging Natural Language and Signal Temporal Logic via Tool-Augmented Process-Rewarded Learning** — [arxiv_ai](https://arxiv.org/abs/2605.06483v1)
- **PairAlign: A Framework for Sequence Tokenization via Self-Alignment with Applications to Audio Tokenization** — [arxiv_cl](https://arxiv.org/abs/2605.06582v1)
- **STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?** — [arxiv_cl](https://arxiv.org/abs/2605.06527v1)
- **Invariant Features in Language Models: Geometric Characterization and Model Attribution** — [arxiv_cl](https://arxiv.org/abs/2605.06458v1)
- **Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** — [arxiv_cr](https://arxiv.org/abs/2605.06324v1)
- **Stateful Agent Backdoor** — [arxiv_cr](https://arxiv.org/abs/2605.06158v1)
- **Secure Seed-Based Multi-bit Watermarking for Diffusion Models from First Principles** — [arxiv_cr](https://arxiv.org/abs/2605.06153v1)
- **Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** — [arxiv_cr](https://arxiv.org/abs/2605.05995v1)
- **LeakDojo: Decoding the Leakage Threats of RAG Systems** — [arxiv_cr](https://arxiv.org/abs/2605.05818v1)
- **Stego Battlefield: Evaluating Image Steganography Attacks and Steganalysis Defenses** — [arxiv_cr](https://arxiv.org/abs/2605.05789v1)
- **Is Escalation Worth It? A Decision-Theoretic Characterization of LLM Cascades** — [arxiv_cl](https://arxiv.org/abs/2605.06350v1)
- **Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity** — [arxiv_cl](https://arxiv.org/abs/2605.06327v1)
- **Quantifying the Statistical Effect of Rubric Modifications on Human-Autorater Agreement** — [arxiv_cl](https://arxiv.org/abs/2605.06283v1)
- **Linear Semantic Segmentation for Low-Resource Spoken Dialects** — [arxiv_cl](https://arxiv.org/abs/2605.06276v1)
- **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** — [arxiv_cl](https://arxiv.org/abs/2605.06241v1)
- **Contrastive Identification and Generation in the Limit** — [arxiv_cl](https://arxiv.org/abs/2605.06211v1)
- **When to Trust Imagination: Adaptive Action Execution for World Action Models** — [huggingface_papers](https://arxiv.org/abs/2605.06222)
- **Continuous-Time Distribution Matching for Few-Step Diffusion Distillation** — [huggingface_papers](https://arxiv.org/abs/2605.06376)
- **A^2TGPO: Agentic Turn-Group Policy Optimization with Adaptive Turn-level Clipping** — [huggingface_papers](https://arxiv.org/abs/2605.06200)
- **Nonsense Helps: Prompt Space Perturbation Broadens Reasoning Exploration** — [huggingface_papers](https://arxiv.org/abs/2605.05566)
- **Think, then Score: Decoupled Reasoning and Scoring for Video Reward Modeling** — [huggingface_papers](https://arxiv.org/abs/2605.05922)
- **Skill1: Unified Evolution of Skill-Augmented Agents via Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.06130)
- **MARBLE: Multi-Aspect Reward Balance for Diffusion RL** — [huggingface_papers](https://arxiv.org/abs/2605.06507)
- **Inductive Venn-Abers and related regressors** — [arxiv_lg](https://arxiv.org/abs/2605.06646v1)
- **Edge-specific signal propagation on mature chromophore-region 3D mechanism graphs for fluorescent protein quantum-yield prediction** — [arxiv_lg](https://arxiv.org/abs/2605.06644v1)
- **Crafting Reversible SFT Behaviors in Large Language Models** — [arxiv_lg](https://arxiv.org/abs/2605.06632v1)
- **EMO: Pretraining Mixture of Experts for Emergent Modularity** — [arxiv_cl](https://arxiv.org/abs/2605.06663v1)
- **Parser agreement and disagreement in L2 Korean UD: Implications for human-in-the-loop annotation** — [arxiv_cl](https://arxiv.org/abs/2605.06625v1)
- **Algospeak, Hiding in the Open: The Trade-off Between Legible Meaning and Detection Avoidance** — [arxiv_cl](https://arxiv.org/abs/2605.06619v1)
- **Automated Clinical Report Generation for Remote Cognitive Remediation: Comparing Knowledge-Engineered Templates and LLMs in Low-Resource Settings** — [arxiv_cl](https://arxiv.org/abs/2605.06594v1)
- **Long Context Pre-Training with Lighthouse Attention** — [arxiv_cl](https://arxiv.org/abs/2605.06554v1)
- **Efficient Pre-Training with Token Superposition** — [arxiv_cl](https://arxiv.org/abs/2605.06546v1)
- **The Frequency Confound in Language-Model Surprisal and Metaphor Novelty** — [arxiv_cl](https://arxiv.org/abs/2605.06506v1)
- **Cubit: Token Mixer with Kernel Ridge Regression** — [arxiv_cl](https://arxiv.org/abs/2605.06501v1)
- **Towards Emotion Consistency Analysis of Large Language Models in Emotional Conversational Contexts** — [arxiv_cl](https://arxiv.org/abs/2605.06476v1)
- **GeoStack: A Framework for Quasi-Abelian Knowledge Composition in VLMs** — [huggingface_papers](https://arxiv.org/abs/2605.06477)
- **BioTool: A Comprehensive Tool-Calling Dataset for Enhancing Biomedical Capabilities of Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.05758)
- **SwiftI2V: Efficient High-Resolution Image-to-Video Generation via Conditional Segment-wise Generation** — [huggingface_papers](https://arxiv.org/abs/2605.06356)
- **Auto Research with Specialist Agents Develops Effective and Non-Trivial Training Recipes** — [huggingface_papers](https://arxiv.org/abs/2605.05724)
- **The Granularity Axis: A Micro-to-Macro Latent Direction for Social Roles in Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.06196)
- **Musk v. Altman week 2: OpenAI fires back, and Shivon Zilis reveals that Musk tried to poach Sam Altman** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1137008/musk-v-altman-week-2-openai-fires-back-and-shivon-zilis-reveals-that-musk-tried-to-poach-sam-altman/)
- **Here’s what you need to know about the cruise ship hantavirus outbreak** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136988/heres-what-you-need-to-know-about-the-cruise-ship-hantavirus-outbreak/)
- **All the latest updates on AI data centers** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/902546/data-centers-ai-energy-power-grids-controversy)
- **PlayStation sees AI as a ‘powerful tool’ to help make games** — [theverge_ai](https://www.theverge.com/games/926914/sony-playstation-ai-powerful-tool-games)
- **Cloudflare says AI made 1,100 jobs obsolete, even as revenue hit a record high** — [techcrunch_ai](https://techcrunch.com/2026/05/08/cloudflare-says-ai-made-1100-jobs-obsolete-even-as-revenue-hit-a-record-high/)
- **Microsoft was worried OpenAI would run off to Amazon and ‘shit-talk’ Azure** — [theverge_ai](https://www.theverge.com/report/926771/microsoft-openai-amazon-worries-shit-talk-azure)
- **Everybody wants to rule the AI world** — [theverge_ai](https://www.theverge.com/podcast/926707/openai-ceo-murati-musk-trial-vergecast)
- **The “people’s airline” and the enterprise AI gold rush** — [techcrunch_ai](https://techcrunch.com/podcast/the-peoples-airline-and-the-enterprise-ai-gold-rush/)
- **Last 24 hours to get 50% off a second pass to TechCrunch Disrupt 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/08/last-24-hours-to-get-50-off-a-second-pass-to-techcrunch-disrupt-2026/)
- **The Download: AI malaise and babymaking tech** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136985/the-download-ai-malaise-babymaking-ivf-tech/)
- **Nanoleaf bets its future on robots, red light therapy, and AI** — [theverge_ai](https://www.theverge.com/tech/926342/nanoleaf-smart-lighting-ai-robotics-red-light-wellness)
- **Running Codex safely at OpenAI** — [openai](https://openai.com/index/running-codex-safely)
- **Here’s how technology transformed babymaking** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136974/heres-how-technology-transformed-babymaking-ivf/)
- **The fax machine is the bottleneck in US healthcare, and VCs are starting to notice** — [techcrunch_ai](https://techcrunch.com/2026/05/07/the-back-office-problem-that-explains-why-specialists-never-call-you-back/)
- **Laid-off Oracle workers tried to negotiate better severance. Oracle said no.** — [techcrunch_ai](https://techcrunch.com/2026/05/08/laid-off-oracle-workers-tried-to-negotiate-better-severance-oracle-said-no/)
- **Intel’s comeback story is even wilder than it seems** — [techcrunch_ai](https://techcrunch.com/2026/05/08/intels-comeback-story-is-even-wilder-than-it-seems/)
- **See what happens when creative legends use AI to make ads for small businesses.** — [google_ai](https://blog.google/company-news/inside-google/company-announcements/the-small-brief/)
- **Continuum-AI-Corp/OrcaRouter-Lite** — [github](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)
- **cenconq25/claude-code-app-studio** — [github](https://github.com/cenconq25/claude-code-app-studio)
- **Negai-ai/AgentClaw** — [github](https://github.com/Negai-ai/AgentClaw)
- **kruschdev/krusch-context-mcp** — [github](https://github.com/kruschdev/krusch-context-mcp)
- **shawn0728/OpenSearch-VL** — [github](https://github.com/shawn0728/OpenSearch-VL)
- **awizemann/harness** — [github](https://github.com/awizemann/harness)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **tianji-qingtian/AI-Native** — [github](https://github.com/tianji-qingtian/AI-Native)
- **alterhq/openpets** — [github](https://github.com/alterhq/openpets)
- **byliutao/CDM** — [github](https://github.com/byliutao/CDM)
- **Austin1serb/agents-md** — [github](https://github.com/Austin1serb/agents-md)
- **Jason-Cyr/ai-shared-brain** — [github](https://github.com/Jason-Cyr/ai-shared-brain)
- **usewhale/whale** — [github](https://github.com/usewhale/whale)
- **Autoloops/upskill** — [github](https://github.com/Autoloops/upskill)
- **ZhongKuang/TAAC2026-CLI** — [github](https://github.com/ZhongKuang/TAAC2026-CLI)
- **0xhackerfren/ProcMon-MCP** — [github](https://github.com/0xhackerfren/ProcMon-MCP)
- **打破科技数据壁垒！智会心研官宣：高级检索+AI深度分析，面向个人免费开放！** — [qbitai](https://www.qbitai.com/2026/05/414445.html)
- **梁文锋出资200亿！DeepSeek首轮创纪录融资500亿，V4.1定档6月** — [qbitai](https://www.qbitai.com/2026/05/414432.html)
- **持续领跑！商汤大装置稳居中国MaaS市场第一梯队** — [qbitai](https://www.qbitai.com/2026/05/414428.html)
- **Redis之父下场，给DeepSeek V4单独造了一台推理引擎** — [qbitai](https://www.qbitai.com/2026/05/414316.html)
- **Anthropic出手！AI的内心独白，曝光了** — [qbitai](https://www.qbitai.com/2026/05/414213.html)
- **GPT-5级推理能力塞进语音模型，OpenAI把同传翻译成本砍穿地板价** — [qbitai](https://www.qbitai.com/2026/05/414194.html)
- **特斯拉百万年薪招数据标注员，朝九晚五，无需AI经验** — [qbitai](https://www.qbitai.com/2026/05/414156.html)
- **所有实验室都怕字节，所有人都在夸DeepSeek！美国研究员36小时中国AI行** — [qbitai](https://www.qbitai.com/2026/05/414141.html)
- **第一批「AI原生」本科生，要毕业了** — [qbitai](https://www.qbitai.com/2026/05/414125.html)
- **AI开始接管年轻人的「精神自留地」** — [36kr](https://36kr.com/p/3801461350702855?f=rss)
- **需求持续升温，AI芯片制造商Cerebras拟上调IPO价格区间** — [36kr](https://36kr.com/newsflashes/3801408298065416?f=rss)
- **新三板梯度培育体系完善，挂牌企业踊跃筹备北交所IPO** — [36kr](https://36kr.com/newsflashes/3801400639462914?f=rss)
- **36氪首发 | 航空航天电气系统互联组件方案商获数千万融资，细分赛道市占率第一** — [36kr](https://36kr.com/p/3801398177324550?f=rss)
- **获高秉强、蓝驰领投数千万融资，浙大00后创业者从远景观测切入AI智能影像｜硬氪首发** — [36kr](https://36kr.com/p/3797202414820359?f=rss)
- **美股三大指数集体收盘涨，英特尔涨超13%** — [36kr](https://36kr.com/newsflashes/3801342492040709?f=rss)
- **9点1氪丨DeepSeek拟募资最高500亿；“全国销冠”被刑拘，泰康人寿回应；OPPO就母亲节文案致歉** — [36kr](https://36kr.com/p/3801348046151428?f=rss)
- **「维新宇航」完成数千万元天使+轮融资，7座3吨级eVTOL将于7月进行首飞测试｜36氪首发** — [36kr](https://36kr.com/p/3800495686163721?f=rss)
- **卡位黄金价格带，问界M6向下争夺年轻群体｜最前线** — [36kr](https://36kr.com/p/3800183520091398?f=rss)
- **小红书四年AI 路：FOMO、犹豫，到突然加速** — [36kr](https://36kr.com/p/3799028783439111?f=rss)
- **牧原股份在横琴成立现代农牧科技公司，注册资本5亿** — [36kr](https://36kr.com/newsflashes/3801450279083783?f=rss)
- **“北辰航天”完成数千万元天使轮融资** — [36kr](https://36kr.com/newsflashes/3801443958496773?f=rss)
- **“星识科技”连续完成天使+轮和天使++轮融资，累计金额达数千万元** — [36kr](https://36kr.com/newsflashes/3801420917071366?f=rss)
- **Anthropic据悉同Akamai签署18亿美元计算协议** — [36kr](https://36kr.com/newsflashes/3801405713374981?f=rss)
- **谷歌旗下Isomorphic Labs拟在新一轮融资中筹集逾20亿美元** — [36kr](https://36kr.com/newsflashes/3801377962090247?f=rss)
- **阿波罗和黑石等机构考虑参与博通近350亿美元融资** — [36kr](https://36kr.com/newsflashes/3801359034113538?f=rss)
- **英特尔与苹果据悉达成初步协议，将为后者设备制造芯片** — [36kr](https://36kr.com/newsflashes/3801360095289088?f=rss)
- **亚马逊北弗吉尼亚数据中心云服务中断问题已基本解决** — [36kr](https://36kr.com/newsflashes/3800643618249730?f=rss)
- **高盛：美国数据中心用电需求或在两年内翻倍** — [36kr](https://36kr.com/newsflashes/3800643284245513?f=rss)