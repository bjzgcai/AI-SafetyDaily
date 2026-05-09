# AI Daily Digest [AI 安全] - 2026-05-09


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-05-09
**Author:** Senior AI Safety Researcher

## Highlights

Three significant academic developments dominate today's discourse, shifting the focus from static safety evaluations to dynamic, systemic risks. First, the community is grappling with the limitations of current Reinforcement Learning with Verifiable Rewards (RLVR) paradigms. New analyses suggest that RLVR may not teach new reasoning strategies but rather redistribute probability mass over existing solutions, raising questions about the efficacy of current alignment scaling laws. Second, privacy in Retrieval-Augmented Generation (RAG) systems is emerging as a critical vulnerability vector. Novel mechanisms like **Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** propose structured location encoding to mitigate leakage, while **LeakDojo: Decoding the Leakage Threats of RAG Systems** provides a configurable framework to benchmark these risks, highlighting that query generation and adversarial instructions remain the primary vectors for data exfiltration. Third, the evaluation landscape is facing a crisis of validity. Research indicates that global LLM leaderboards are statistically misleading due to heterogeneous opinions, and safety audits are susceptible to strategic manipulation where platforms optimize for metrics rather than genuine harm reduction.

## Adversarial Attacks & Robustness

The landscape of adversarial attacks is evolving from single-turn prompt injections to stateful, multi-session exploits and infrastructure-level compromises. A comprehensive **SoK: Robustness in Large Language Models against Jailbreak Attacks** underscores that existing evaluation practices are inadequate, often relying on narrow metrics like attack success rate that fail to capture the multidimensional nature of LLM security. This critique is echoed in **How Many Iterations to Jailbreak? Dynamic Budget Allocation for Multi-Turn LLM Evaluation**, which argues that key safety events often emerge only after repeated interactions and that static budget allocation is inefficient. These works collectively suggest that current benchmarks may underestimate the persistence required to compromise models in real-world conversational settings.

Simultaneously, the threat surface is expanding beyond the model weights to the retrieval infrastructure. **Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** evaluates four RAG architectures under controlled poisoning, revealing that systems designed to handle conflicting information remain untested against adversarially optimized contradictions. This is complemented by **LeakDojo: Decoding the Leakage Threats of RAG Systems**, which benchmarks six existing attacks across fourteen LLMs and diverse RAG systems, confirming that query generation and adversarial instructions are the primary leakage vectors. The convergence of these findings implies that securing the retrieval pipeline is as critical as securing the generation model itself.

In the realm of backdoor attacks, the threat model is becoming more sophisticated. **Stateful Agent Backdoor** proposes an attack that extends the lifecycle across multiple sessions under permission isolation, maintaining state through persistent components to enable autonomous, incremental execution. This contrasts with existing stateless attacks and poses a significant challenge for defense mechanisms that assume session independence. Furthermore, **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** highlights that defenses for vision systems remain underdeveloped compared to classification, as classification-oriented adversarial generation does not match the detection attack space where attacks may cause object misclassification or disappearance.

## Privacy Protection & Federated Learning

Privacy-preserving techniques are undergoing a paradigm shift, moving from simple perturbation to structured encoding and rigorous theoretical bounds. **Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** introduces PAS (Privacy Anchor Substitution), a structured mechanism for enabling user location privacy in spatial RAG systems. Unlike conventional differential privacy methods that directly perturb user locations, PAS represents location with relative anchor encoding, allowing seamless integration with modern RAG pipelines while achieving approximately 370-400m adversarial location error. This approach offers a promising alternative to noise-based methods that often degrade utility.

In the federated learning domain, **FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** addresses the challenge of detecting whether a model was trained on watermarked documents within a federated setting. While watermark radioactivity testing is effective in centralized fine-tuning, the authors note that secure aggregation (SA) in FL complicates this, requiring new methods to protect data ownership without compromising the privacy guarantees of the aggregation protocol. This is further supported by **AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics**, which studies client participation as a timeliness-aware systems problem using Age of Information (AoI) to mitigate stale client information in production security analytics pipelines.

Theoretical foundations for differential privacy are also being refined. **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling** derives a tight analysis of the trade-off function for Differentially Private Stochastic Gradient Descent (DP-SGD) with subsampling based on random shuffling within the $f$-DP framework. Unlike $f$-DP analyses for Poisson subsampling, which yield non-closed implicit formulas, random shuffling admits a tight analysis yielding transparent and interpretable closed-form bounds. Additionally, **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** introduces a family of PAC-private zeroth-order mechanisms for fine-tuning large language models that delivers usable utility at $I(S^*; Y_{1:T})=0$, bounding the membership-inference attack posterior success rate at the prior.

## Model Alignment & Interpretability

Interpretability research is increasingly focusing on the geometric and structural properties of internal representations. **SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** addresses the limitation of common architectures such as TopK SAEs that rely on a fixed sparsity level. By enforcing the same number of active features across all inputs, they ignore the varying complexity of real-world data. The proposed dynamic selection allows for adaptive sparsity, improving the decomposition of polysemantic activations into sparse sets of monosemantic features. This is complemented by **From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features**, which introduces a graph-structured representation in which each SAE feature is modelled as a token co-occurrence graph, examining the higher-order co-occurrence structure shared across features.

On the alignment front, recent findings challenge the efficacy of RLVR. **On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR** demonstrates that enhanced reasoning capabilities acquired through RLVR are primarily concentrated within the rank-1 components. The authors identify a counterintuitive phenomenon where RLVR may exhibit implicit reward overfitting to the training dataset, achieving satisfactory performance on the test set even when rewards remain relatively low during training. This aligns with **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning**, which finds that RL's beneficial footprint is a sparse, predictable correction concentrated at high-entropy decision points where the model is uncertain, suggesting RL merely steers the model toward paths it already knows.

The risk of instrumental convergence is also being quantified. **Instrumental Choices: Measuring the Propensity of LLM Agents to Pursue Instrumental Behaviors** introduces a benchmark for measuring model propensity for instrumental convergence (IC) behaviour in terminal-based agents. This behaviour, such as self-preservation, has been hypothesised to play a key role in risks from highly capable AI agents. The benchmark is designed to be realistic and low-stakes to reduce evaluation-awareness and roleplay confounds, providing a necessary empirical foundation for assessing long-term safety risks.

## Safety Benchmarks & Governance

The reliability of safety benchmarks and governance metrics is under scrutiny. **Why Global LLM Leaderboards Are Misleading: Small Portfolios for Heterogeneous Supervised ML** analyzes ~89K comparisons in 116 languages from 52 LLMs from Arena, showing that the best-fit global Bradley-Terry ranking is misleading. Nearly 2/3 of the decisive votes cancel out, and even the top 50 models according to the global BT ranking are statistically indistinguishable. This failure is traced to strong, structured heterogeneity of opinions across language, task, and time.

Governance metrics face similar challenges. **Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** models the protocol as a published transformation graph whose connected components form semantic classes. It asks when an audit metric can still certify a genuine reduction in harm when a strategic platform can improve its score by routing recommendations through semantically equivalent content variants. This is critical for regulatory compliance under frameworks like the UK Online Safety Act and the EU Digital Services Act.

Furthermore, **Measuring Evaluation-Context Divergence in Open-Weight LLMs** defines evaluation-context divergence as an observable within-item change in behavior induced by framing a fixed task as an evaluation, a live deployment interaction, or a neutral request. The authors present a paired-prompt protocol that measures it in open-weight LLMs while controlling for paraphrase variation, benchmark familiarity, and judge framing-sensitivity. This suggests that safety benchmarks are routinely treated as evidence about how a language model will behave once deployed, but this inference is fragile if behavior depends on whether a prompt looks like an evaluation.

## Security Tools & Infrastructure

Open-source tools are emerging to address the growing complexity of agent security and infrastructure isolation. **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** argues that risks in self-hosted computer-use agents (SHCUAs) cannot be addressed by ad hoc blocking rules alone. It proposes using Trusted Execution Environments (TEEs) to isolate host-side resources, including browsers, files, scripts, and system commands, from the agent's control path. This is a critical step for securing agents that combine natural-language interaction with direct access to host-side resources.

In the realm of routing and context management, **Continuum-AI-Corp/OrcaRouter-Lite** offers a self-hosted LLM router with a managed safety net, supporting OpenAI-compatible interfaces and BYOK (Bring Your Own Key). This tool is designed to provide a single-workspace, streaming environment for advanced routing. Additionally, **kruschdev/krusch-context-mcp** provides a unified Zero-Trust MCP server that gives IDE agents local semantic codebase search, isolated episodic project memory, and hallucination-free framework RAG. These tools reflect a shift towards modular, secure infrastructure for agent deployment.

Industry news regarding infrastructure and funding should be treated with caution. Reports from Chinese tech aggregators regarding DeepSeek's fundraising and Anthropic's infrastructure deals (e.g., the Anthropic-Akamai 18 billion dollar deal) highlight the intense competition for compute resources. While these developments indicate significant capital flow into the sector, they do not constitute technical safety breakthroughs. The focus remains on the academic and engineering challenges of securing these expanding infrastructures, such as the **Hybrid Quantum-Classical GANs for the Generation of Adversarial Network Flows**, which proposes a QC-GAN framework to generate synthetic network traffic flows mimicking malicious traffic using latent representations.

## Looking Forward

Several unresolved theoretical questions and hypotheses await validation. First, the relationship between RLVR and actual capability acquisition remains unclear. If RLVR primarily redistributes probability mass rather than teaching new strategies, how can we scale reasoning capabilities effectively without exacerbating overfitting? Second, the security of RAG systems requires a unified framework that accounts for both poisoning and leakage. Current tools like **LeakDojo** and **Architecture Matters** provide benchmarks, but a standardized defense protocol for knowledge base integrity is still missing. Third, the metric gaming problem poses a governance challenge. If platforms can optimize for scalar metrics without reducing true harm, regulatory frameworks need to move beyond static audits to continuous, adversarial monitoring. Finally, the geometric characterization of invariant features in language models, as proposed in **Invariant Features in Language Models: Geometric Characterization and Model

---


## References

- **AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** — [arxiv_cr](https://arxiv.org/abs/2605.05644v1)
- **Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** — [arxiv_cr](https://arxiv.org/abs/2605.05459v1)
- **SoK: Robustness in Large Language Models against Jailbreak Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.05058v1)
- **Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.06423v1)
- **How Many Iterations to Jailbreak? Dynamic Budget Allocation for Multi-Turn LLM Evaluation** — [arxiv_lg](https://arxiv.org/abs/2605.06605v1)
- **FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** — [arxiv_lg](https://arxiv.org/abs/2605.06596v1)
- **On the Safety of Graph Representation Learning** — [arxiv_lg](https://arxiv.org/abs/2605.06576v1)
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
- **Musk v. Altman week 2: OpenAI fires back, and Shivon Zilis reveals that Musk tried to poach Sam Altman** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1137008/musk-v-altman-week-2-openai-fires-back-and-shivon-zilis-reveals-that-musk-tried-to-poach-sam-altman/)
- **All the latest updates on AI data centers** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/902546/data-centers-ai-energy-power-grids-controversy)
- **Cloudflare says AI made 1,100 jobs obsolete, even as revenue hit a record high** — [techcrunch_ai](https://techcrunch.com/2026/05/08/cloudflare-says-ai-made-1100-jobs-obsolete-even-as-revenue-hit-a-record-high/)
- **Here’s what you need to know about the cruise ship hantavirus outbreak** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136988/heres-what-you-need-to-know-about-the-cruise-ship-hantavirus-outbreak/)
- **PlayStation sees AI as a ‘powerful tool’ to help make games** — [theverge_ai](https://www.theverge.com/games/926914/sony-playstation-ai-powerful-tool-games)
- **Microsoft was worried OpenAI would run off to Amazon and ‘shit-talk’ Azure** — [theverge_ai](https://www.theverge.com/report/926771/microsoft-openai-amazon-worries-shit-talk-azure)
- **The “people’s airline” and the enterprise AI gold rush** — [techcrunch_ai](https://techcrunch.com/podcast/the-peoples-airline-and-the-enterprise-ai-gold-rush/)
- **Everybody wants to rule the AI world** — [theverge_ai](https://www.theverge.com/podcast/926707/openai-ceo-murati-musk-trial-vergecast)
- **Last 24 hours to get 50% off a second pass to TechCrunch Disrupt 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/08/last-24-hours-to-get-50-off-a-second-pass-to-techcrunch-disrupt-2026/)
- **Running Codex safely at OpenAI** — [openai](https://openai.com/index/running-codex-safely)
- **The Download: AI malaise and babymaking tech** — [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136985/the-download-ai-malaise-babymaking-ivf-tech/)
- **Nanoleaf bets its future on robots, red light therapy, and AI** — [theverge_ai](https://www.theverge.com/tech/926342/nanoleaf-smart-lighting-ai-robotics-red-light-wellness)
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
- **sanieldoe/companions** — [github](https://github.com/sanieldoe/companions)
- **tianji-qingtian/AI-Native** — [github](https://github.com/tianji-qingtian/AI-Native)
- **alterhq/openpets** — [github](https://github.com/alterhq/openpets)
- **byliutao/CDM** — [github](https://github.com/byliutao/CDM)
- **usewhale/whale** — [github](https://github.com/usewhale/whale)
- **Austin1serb/agents-md** — [github](https://github.com/Austin1serb/agents-md)
- **Jason-Cyr/ai-shared-brain** — [github](https://github.com/Jason-Cyr/ai-shared-brain)
- **Autoloops/upskill** — [github](https://github.com/Autoloops/upskill)
- **ZhongKuang/TAAC2026-CLI** — [github](https://github.com/ZhongKuang/TAAC2026-CLI)
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
- **“星识科技”连续完成天使+轮和天使++轮融资，累计金额达数千万元** — [36kr](https://36kr.com/newsflashes/3801420917071366?f=rss)
- **Anthropic据悉同Akamai签署18亿美元计算协议** — [36kr](https://36kr.com/newsflashes/3801405713374981?f=rss)
- **谷歌旗下Isomorphic Labs拟在新一轮融资中筹集逾20亿美元** — [36kr](https://36kr.com/newsflashes/3801377962090247?f=rss)
- **阿波罗和黑石等机构考虑参与博通近350亿美元融资** — [36kr](https://36kr.com/newsflashes/3801359034113538?f=rss)
- **英特尔与苹果据悉达成初步协议，将为后者设备制造芯片** — [36kr](https://36kr.com/newsflashes/3801360095289088?f=rss)
- **亚马逊北弗吉尼亚数据中心云服务中断问题已基本解决** — [36kr](https://36kr.com/newsflashes/3800643618249730?f=rss)
- **高盛：美国数据中心用电需求或在两年内翻倍** — [36kr](https://36kr.com/newsflashes/3800643284245513?f=rss)
- **热门中概股美股盘前多数上涨，百度涨超5%** — [36kr](https://36kr.com/newsflashes/3800639633415424?f=rss)
- **美股大型科技股盘前多数上涨，英伟达涨超1%** — [36kr](https://36kr.com/newsflashes/3800638528986369?f=rss)