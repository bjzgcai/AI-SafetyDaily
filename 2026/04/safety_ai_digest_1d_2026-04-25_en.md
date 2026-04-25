# AI Daily Digest [AI 安全] - 2026-04-25


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-04-25  
**Author:** Senior AI Safety Researcher

## Highlights

The most significant academic developments this week center on the evolution of adversarial vulnerabilities in stateless systems, the maturation of interpretability-based auditing, and the formalization of privacy-preserving model composition. First, the introduction of **Transient Turn Injection** exposes a critical class of multi-turn vulnerabilities where adversarial intent is distributed across isolated interactions to evade stateless moderation, marking a departure from conventional single-prompt jailbreaks. Second, **Breaking Bad: Interpretability-Based Safety Audits of State-of-the-Art LLMs** demonstrates that activation-steering techniques can systematically uncover internal vulnerabilities that black-box probing misses, suggesting a shift toward mechanistic safety verification. Third, **Differentially Private Clustered Federated Learning with Privacy-Preserving Initialization and Normality-Driven Aggregation** advances the utility-privacy trade-off in heterogeneous data environments, offering a pathway to deploy federated models without compromising individual user data. While industry news regarding DeepSeek’s V4 model and geopolitical AI investments is prominent, the technical community is prioritizing these foundational safety and privacy mechanisms.

## Adversarial Attacks & Robustness

The landscape of adversarial robustness is shifting from static input manipulation to dynamic, multi-turn exploitation and mechanistic interference. A critical vulnerability identified in **Transient Turn Injection** reveals that stateless moderation systems are susceptible to attacks where harmful intent is fragmented across sequential interactions, effectively bypassing policy enforcement that relies on turn-by-turn analysis. This finding complements the work in **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers**, which argues that existing backdoor methods suffer from explicit trigger patterns; the proposed BadStyle framework addresses this by embedding triggers within natural language styles, making detection significantly harder. Together, these works suggest that future defenses must account for temporal state and stylistic nuance rather than just content filtering.

In response to these evolving threats, the community is moving toward standardized, automated robustness testing. **Auto-ART: Structured Literature Synthesis and Automated Adversarial Robustness Testing** addresses the fragmentation in evaluation protocols by introducing a framework that operationalizes over 50 attacks and 28 defense modules, aiming to resolve issues like gradient masking that have plagued previous evaluations. This contrasts with earlier, more isolated benchmarking efforts. Furthermore, **Breaking Bad: Interpretability-Based Safety Audits of State-of-the-Art LLMs** leverages Universal Steering and Representation Engineering to identify optimal activation-steering coefficients, moving beyond black-box probing to systematically audit model internals. While the authors report success in jailbreaking eight SOTA models, the independent verification of these steering coefficients across different model families remains an open challenge.

The scope of robustness is also expanding to physical and hardware domains. **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** highlights that safety-critical infrastructure, such as airport screening, faces waveform-domain physical attacks that manipulate image reconstruction. Similarly, **SoK: The Next Frontier in AV Security: Systematizing Perception Attacks and the Emerging Threat of Multi-Sensor Fusion** systematizes 48 studies on autonomous vehicle perception attacks, revealing that cross-modal threats are becoming more complex than single-sensor exploits. These findings underscore that robustness must be evaluated across the entire stack, from physical sensors to model internals.

## Model Alignment, Interpretability & Reasoning

Alignment research is increasingly recognizing that user intent is often ill-formed, challenging the assumption that models simply need to follow instructions. **Alignment has a Fantasia Problem** argues that treating prompts as complete expressions of intent leads to "Fantasia interactions" where models appear helpful but fail to align with users' actual, evolving needs. This theoretical shift suggests alignment research must move beyond instruction tuning to support goal formation. Complementing this, **Language as a Latent Variable for Reasoning Optimization** posits that language functions as a structural modulator of internal inference pathways, with non-English responses sometimes outperforming English on reasoning tasks. This contradicts the prevailing view that language is merely an output medium, suggesting that multilingual training could be a safety and performance lever.

Interpretability is also being applied to detect subtle biases and hallucinations. **Measuring Opinion Bias and Sycophancy via LLM-based Coercion** introduces a method to elicit model positions on contested topics by observing how models concede to user arguments, revealing that silent positions can propagate at scale. In parallel, **When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs** uses the HalluScope benchmark to quantify how language priors can override visual input, indicating that hallucinations are often driven by prompt dominance rather than vision backbone limitations. These works collectively suggest that safety evaluations must account for the interplay between language priors and modality-specific reasoning.

On the reasoning front, **Reasoning Primitives in Hybrid and Non-Hybrid LLMs** investigates whether hybrid architectures combining attention-based retrieval with recurrent state updates are superior for tasks requiring both recall and state-tracking. The authors find that hybrid models may offer distinct advantages in controlled tasks, though generalization remains to be fully validated. Meanwhile, **Fairness under uncertainty in sequential decisions** extends fairness research to online, sequential settings where prior decisions inform future ones, highlighting that algorithmic approaches alone cannot resolve structural inequalities but can support socio-technical decision systems by surfacing discriminatory biases.

## Privacy Protection & Federated Learning

Privacy-preserving machine learning is seeing significant innovation in how data is aggregated and models are merged. **Differentially Private Clustered Federated Learning with Privacy-Preserving Initialization and Normality-Driven Aggregation** addresses the heterogeneity of cross-device deployments by segregating users into clusters, which mitigates the slow convergence and poor generalization of vanilla federated learning. This approach is further supported by **Differentially Private Model Merging**, which proposes post-processing techniques to generate models satisfying any target differential privacy requirement without additional training, given a set of existing models with different privacy/utility tradeoffs. This capability allows for dynamic privacy compliance without the computational cost of retraining.

In the domain of personalization, **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies** decouples personal data from shared weights using composable adapters and per-user proxy artefacts. Evaluation on Phi-3.5-mini and Llama-3.1-8B confirms that personal data influences outputs while remaining deletable, solving the computational infeasibility of individual data removal. These technical advances are crucial for compliance with regulations like GDPR. Additionally, **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study** systematically evaluates the impact of differential privacy mechanisms on statistical utility in survival analyses, providing empirical data on the trade-offs in clinical settings.

## Agent Security, Governance & Benchmarks

As AI agents become more prevalent, security risks are shifting toward tool use and multi-agent coordination. **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** operationalizes developer pitfalls in the Model Context Protocol, validating outcomes with MCP traces rather than agent self-reports. This is critical given the risks identified in **Breaking Bad with Function Hijacking Attacks: Novel Threats for Function Calling and Agentic Models**, which shows that function calling interfaces can be abused for data tampering and theft. The authors report that existing benchmarks offer limited remediation guidance, necessitating frameworks like AVISE.

**AVISE: Framework for Evaluating the Security of AI Systems** introduces a modular open-source framework for identifying vulnerabilities in AI systems, extending theory-of-mind-based multi-turn Red Queen attacks. This complements **Adaptive Instruction Composition for Automated LLM Red-Teaming**, which combines crowdsourced texts according to an adaptive mechanism to discover diverse attacks. In the enterprise context, **CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents** evaluates whether agents can convey essential content while withholding sensitive context, revealing that privacy failures are prevalent with violation rates ranging from 15.8% to higher depending on the model.

Governance frameworks are also evolving to meet regulatory demands. **Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation** addresses the vacuum in regulatory consensus regarding "acceptable risk," proposing a technical method for verifying that deployed systems meet quantitative thresholds. This contrasts with **Mitigate or Fail: How Risk Management Shapes Cybersecurity Competency**, which finds that cybersecurity training often shapes professionals to think in terms of threats rather than risk, contributing to organizational failures. Meanwhile, **Compliance Moral Hazard and the Backfiring Mandate** develops a mechanism design framework for decentralized risk analytics, grounded in anti-money laundering in banking networks, highlighting the strategic frictions in information aggregation.

## Industry & Open Source Developments

The open-source community is rapidly deploying tools to support these research findings. **Auto-ART** and **AVISE** are highlighted as key frameworks for adversarial robustness and security evaluation, respectively. **MCP Pitfall Lab** provides a protocol-aware security testing framework for tool-integrated agents. On the industry side, the release of **DeepSeek-V4** and its integration into platforms like Baidu’s Qianfan and Huawei Cloud signals a competitive shift in open-weight models, though claims of performance parity with frontier closed-source systems require independent verification. The **Google/Anthropic investment** and **Apple’s leadership transition** indicate a consolidation of compute and hardware resources, which may impact the accessibility of safety research tools. In the military domain, **Project Maven** continues to demonstrate the acceleration of targeting processes via AI, raising questions about the governance of lethal autonomous systems.

## Looking Forward

Several theoretical questions remain unresolved. First, the long-term stability of interpretability-based defenses against adaptive adversaries, particularly in the context of **Transient Turn Injection**, requires further validation. It is unclear whether activation steering can be generalized across model architectures without significant performance degradation. Second, the **Fantasia Problem** suggests a need for alignment frameworks that can handle user intent formation dynamically, yet current benchmarks like **MathDuels** and **CI-Work** focus largely on static task performance. Third, the quantification of "acceptable risk" proposed in **Bounding the Black Box** lacks a standardized metric for cross-domain application, particularly in high-stakes fields like healthcare and finance. Finally, the integration of **Differentially Private Model Merging** into production pipelines raises questions about the composability of privacy guarantees when multiple models are merged over time. Future research must address these gaps to ensure that safety mechanisms scale alongside model capabilities.

---


## References

- **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21860v1)
- **Enabling and Inhibitory Pathways of University Students' Willingness to Disclose AI Use: A Cognition-Affect-Conation Perspective** — [arxiv_ai](https://arxiv.org/abs/2604.21733v1)
- **Differentially Private Clustered Federated Learning with Privacy-Preserving Initialization and Normality-Driven Aggregation** — [arxiv_cr](https://arxiv.org/abs/2604.20596v1)
- **Fairness under uncertainty in sequential decisions** — [arxiv_ai](https://arxiv.org/abs/2604.21711v1)
- **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study** — [arxiv_cr](https://arxiv.org/abs/2604.21491v1)
- **Measuring Opinion Bias and Sycophancy via LLM-based Coercion** — [arxiv_cl](https://arxiv.org/abs/2604.21564v1)
- **Drug Synergy Prediction via Residual Graph Isomorphism Networks and Attention Mechanisms** — [arxiv_lg](https://arxiv.org/abs/2604.21473v1)
- **Differentially Private De-identification of Dutch Clinical Notes: A Comparative Evaluation** — [arxiv_cl](https://arxiv.org/abs/2604.21421v1)
- **Differentially Private Model Merging** — [arxiv_cr](https://arxiv.org/abs/2604.20985v1)
- **Breaking Bad: Interpretability-Based Safety Audits of State-of-the-Art LLMs** — [arxiv_cr](https://arxiv.org/abs/2604.20945v1)
- **Adaptive Defense Orchestration for RAG: A Sentinel-Strategist Architecture against Multi-Vector Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.20932v1)
- **UniGenDet: A Unified Generative-Discriminative Framework for Co-Evolutionary Image Generation and Generated Image Detection** — [huggingface_papers](https://arxiv.org/abs/2604.21904)
- **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies** — [arxiv_ai](https://arxiv.org/abs/2604.21571v1)
- **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21774v1)
- **A Sociotechnical, Practitioner-Centered Approach to Technology Adoption in Cybersecurity Operations: An LLM Case** — [arxiv_cr](https://arxiv.org/abs/2604.21679v1)
- **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21477v1)
- **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** — [arxiv_cl](https://arxiv.org/abs/2604.21871v1)
- **Language as a Latent Variable for Reasoning Optimization** — [arxiv_cl](https://arxiv.org/abs/2604.21593v1)
- **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** — [arxiv_lg](https://arxiv.org/abs/2604.21870v1)
- **GFlowState: Visualizing the Training of Generative Flow Networks Beyond the Reward** — [arxiv_lg](https://arxiv.org/abs/2604.21830v1)
- **Compliance Moral Hazard and the Backfiring Mandate** — [arxiv_lg](https://arxiv.org/abs/2604.21789v1)
- **There Will Be a Scientific Theory of Deep Learning** — [arxiv_lg](https://arxiv.org/abs/2604.21691v1)
- **Physically Unclonable Functions for Secure IoT Authentication and Hardware-Anchored AI Model Integrity** — [arxiv_cr](https://arxiv.org/abs/2604.21188v1)
- **Breaking MCP with Function Hijacking Attacks: Novel Threats for Function Calling and Agentic Models** — [arxiv_cr](https://arxiv.org/abs/2604.20994v1)
- **AVISE: Framework for Evaluating the Security of AI Systems** — [arxiv_cr](https://arxiv.org/abs/2604.20833v1)
- **Auto-ART: Structured Literature Synthesis and Automated Adversarial Robustness Testing** — [arxiv_cr](https://arxiv.org/abs/2604.20704v1)
- **SoK: The Next Frontier in AV Security: Systematizing Perception Attacks and the Emerging Threat of Multi-Sensor Fusion** — [arxiv_cr](https://arxiv.org/abs/2604.20621v1)
- **Towards Certified Malware Detection: Provable Guarantees Against Evasion Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.20495v1)
- **Trust but Verify: Introducing DAVinCI -- A Framework for Dual Attribution and Verification in Claim Inference for Language Models** — [huggingface_papers](https://arxiv.org/abs/2604.21193)
- **Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation** — [arxiv_ai](https://arxiv.org/abs/2604.21854v1)
- **Modulating Cross-Modal Convergence with Single-Stimulus, Intra-Modal Dispersion** — [arxiv_ai](https://arxiv.org/abs/2604.21836v1)
- **Alignment has a Fantasia Problem** — [arxiv_ai](https://arxiv.org/abs/2604.21827v1)
- **Quotient-Space Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2604.21809v1)
- **SyMTRS: Benchmark Multi-Task Synthetic Dataset for Depth, Domain Adaptation and Super-Resolution in Aerial Imagery** — [arxiv_ai](https://arxiv.org/abs/2604.21801v1)
- **Inferring High-Level Events from Timestamped Data: Complexity and Medical Applications** — [arxiv_ai](https://arxiv.org/abs/2604.21793v1)
- **Why are all LLMs Obsessed with Japanese Culture? On the Hidden Cultural and Regional Biases of LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21751v1)
- **AEL: Agent Evolving Learning for Open-Ended Environments** — [arxiv_ai](https://arxiv.org/abs/2604.21725v1)
- **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers** — [arxiv_ai](https://arxiv.org/abs/2604.21700v1)
- **Fine-Grained Perspectives: Modeling Explanations with Annotator-Specific Rationales** — [arxiv_ai](https://arxiv.org/abs/2604.21667v1)
- **Task-specific Subnetwork Discovery in Reinforcement Learning for Autonomous Underwater Navigation** — [arxiv_ai](https://arxiv.org/abs/2604.21640v1)
- **On the Role of Preprocessing and Memristor Dynamics in Reservoir Computing for Image Classification** — [arxiv_ai](https://arxiv.org/abs/2604.21602v1)
- **CoFEE: Reasoning Control for LLM-Based Feature Discovery** — [arxiv_ai](https://arxiv.org/abs/2604.21584v1)
- **Mitigate or Fail: How Risk Management Shapes Cybersecurity Competency** — [arxiv_cr](https://arxiv.org/abs/2604.21604v1)
- **MathDuels: Evaluating LLMs as Problem Posers and Solvers** — [arxiv_cl](https://arxiv.org/abs/2604.21916v1)
- **Mapping the Political Discourse in the Brazilian Chamber of Deputies: A Multi-Faceted Computational Approach** — [arxiv_cl](https://arxiv.org/abs/2604.21897v1)
- **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA** — [arxiv_cl](https://arxiv.org/abs/2604.21766v1)
- **From If-Statements to ML Pipelines: Revisiting Bias in Code-Generation** — [arxiv_cl](https://arxiv.org/abs/2604.21716v1)
- **Phonological Subspace Collapse Is Aetiology-Specific and Cross-Lingually Stable: Evidence from 3,374 Speakers** — [arxiv_cl](https://arxiv.org/abs/2604.21706v1)
- **How English Print Media Frames Human-Elephant Conflicts in India** — [arxiv_cl](https://arxiv.org/abs/2604.21496v1)
- **Generalizing Numerical Reasoning in Table Data through Operation Sketches and Self-Supervised Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21495v1)
- **Cross-Domain Data Selection and Augmentation for Automatic Compliance Detection** — [arxiv_cl](https://arxiv.org/abs/2604.21469v1)
- **Reasoning Primitives in Hybrid and Non-Hybrid LLMs** — [arxiv_cl](https://arxiv.org/abs/2604.21454v1)
- **Interpretable facial dynamics as behavioral and perceptual traces of deepfakes** — [arxiv_lg](https://arxiv.org/abs/2604.21760v1)
- **Ramen: Robust Test-Time Adaptation of Vision-Language Models with Active Sample Selection** — [arxiv_lg](https://arxiv.org/abs/2604.21728v1)
- **Evaluating Post-hoc Explanations of the Transformer-based Genome Language Model DNABERT-2** — [arxiv_lg](https://arxiv.org/abs/2604.21690v1)
- **A-THENA: Early Intrusion Detection for IoT with Time-Aware Hybrid Encoding and Network-Specific Augmentation** — [arxiv_lg](https://arxiv.org/abs/2604.21623v1)
- **Verifying Machine Learning Interpretability Requirements through Provenance** — [arxiv_lg](https://arxiv.org/abs/2604.21599v1)
- **Dynamical Priors as a Training Objective in Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2604.21464v1)
- **Tempered Sequential Monte Carlo for Trajectory and Policy Optimization with Differentiable Dynamics** — [arxiv_lg](https://arxiv.org/abs/2604.21456v1)
- **CSC: Turning the Adversary's Poison against Itself** — [arxiv_cr](https://arxiv.org/abs/2604.21416v1)
- **Adversarial Evasion in Non-Stationary Malware Detection: Minimizing Drift Signals through Similarity-Constrained Perturbations** — [arxiv_cr](https://arxiv.org/abs/2604.21310v1)
- **CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2604.21308v1)
- **Strategic Heterogeneous Multi-Agent Architecture for Cost-Effective Code Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2604.21282v1)
- **Adaptive Instruction Composition for Automated LLM Red-Teaming** — [arxiv_cr](https://arxiv.org/abs/2604.21159v1)
- **AI-Gram: When Visual Agents Interact in a Social Network** — [arxiv_cl](https://arxiv.org/abs/2604.21446v1)
- **mcdok at SemEval-2026 Task 13: Finetuning LLMs for Detection of Machine-Generated Code** — [arxiv_cl](https://arxiv.org/abs/2604.21365v1)
- **CARE: Counselor-Aligned Response Engine for Online Mental-Health Support** — [arxiv_cl](https://arxiv.org/abs/2604.21352v1)
- **Vista4D: Video Reshooting with 4D Point Clouds** — [huggingface_papers](https://arxiv.org/abs/2604.21915)
- **Encoder-Free Human Motion Understanding via Structured Motion Descriptions** — [huggingface_papers](https://arxiv.org/abs/2604.21668)
- **Explainable Disentangled Representation Learning for Generalizable Authorship Attribution in the Era of Generative AI** — [huggingface_papers](https://arxiv.org/abs/2604.21300)
- **StyleID: A Perception-Aware Dataset and Metric for Stylization-Agnostic Facial Identity Recognition** — [huggingface_papers](https://arxiv.org/abs/2604.21689)
- **WorldMark: A Unified Benchmark Suite for Interactive Video World Models** — [huggingface_papers](https://arxiv.org/abs/2604.21686)
- **Seeing Fast and Slow: Learning the Flow of Time in Videos** — [arxiv_ai](https://arxiv.org/abs/2604.21931v1)
- **When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21911v1)
- **From Research Question to Scientific Workflow: Leveraging Agentic AI for Science Automation** — [arxiv_ai](https://arxiv.org/abs/2604.21910v1)
- **Evaluation of Automatic Speech Recognition Using Generative Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21928v1)
- **EVENT5Ws: A Large Dataset for Open-Domain Event Extraction from Documents** — [arxiv_cl](https://arxiv.org/abs/2604.21890v1)
- **Revisiting Non-Verbatim Memorization in Large Language Models: The Role of Entity Surface Forms** — [arxiv_cl](https://arxiv.org/abs/2604.21882v1)
- **SemEval-2026 Task 4: Narrative Story Similarity and Narrative Representation Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21782v1)
- **Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability** — [arxiv_lg](https://arxiv.org/abs/2604.21930v1)
- **Fine-Tuning Regimes Define Distinct Continual Learning Problems** — [arxiv_lg](https://arxiv.org/abs/2604.21927v1)
- **The Sample Complexity of Multicalibration** — [arxiv_lg](https://arxiv.org/abs/2604.21923v1)
- **Low-Rank Adaptation Redux for Large Models** — [arxiv_lg](https://arxiv.org/abs/2604.21905v1)
- **Revealing Geography-Driven Signals in Zone-Level Claim Frequency Models: An Empirical Study using Environmental and Visual Predictors** — [arxiv_lg](https://arxiv.org/abs/2604.21893v1)
- **Beyond Expected Information Gain: Stable Bayesian Optimal Experimental Design with Integral Probability Metrics and Plug-and-Play Extensions** — [arxiv_lg](https://arxiv.org/abs/2604.21849v1)
- **On the algebra of Koopman eigenfunctions and on some of their infinities** — [arxiv_lg](https://arxiv.org/abs/2604.21825v1)
- **PrismaDV: Automated Task-Aware Data Unit Test Generation** — [arxiv_lg](https://arxiv.org/abs/2604.21765v1)
- **Context Unrolling in Omni Models** — [huggingface_papers](https://arxiv.org/abs/2604.21921)
- **Three reasons why DeepSeek’s new model matters** — [mit_tech_review](https://www.technologyreview.com/2026/04/24/1136422/why-deepseeks-v4-matters/)
- **8 Gemini tips for organizing your space (and life)** — [google_ai](https://blog.google/products-and-platforms/products/gemini/gemini-spring-cleaning-tips/)
- **Google to invest up to $40B in Anthropic in cash and compute** — [techcrunch_ai](https://techcrunch.com/2026/04/24/google-to-invest-up-to-40b-in-anthropic-in-cash-and-compute/)
- **Apple’s new CEO, and why Elon Musk wants to buy Cursor for $60B** — [techcrunch_ai](https://techcrunch.com/podcast/apples-new-ceo-and-why-elon-musk-wants-to-buy-cursor-for-60b/)
- **Marked-up Mac minis flood eBay amid shortages driven by AI** — [techcrunch_ai](https://techcrunch.com/2026/04/24/mac-mini-price-expensive-ebay-shortage-ai-memory/)
- **How Project Maven taught the military to love AI** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/917996/project-maven-military-ai-katrina-manson)
- **Uber CTO Praveen Neppalli Naga joins stacked StrictlyVC SF lineup for April 30 event** — [techcrunch_ai](https://techcrunch.com/2026/04/24/uber-cto-praveen-neppalli-naga-joins-stacked-strictlyvc-sf-lineup-for-april-30-event/)
- **Tim Cook is stepping down. What happens to Apple now?** — [techcrunch_ai](https://techcrunch.com/video/tim-cook-is-stepping-down-what-happens-to-apple-now/)
- **DeepSeek previews new AI model that ‘closes the gap’ with frontier models** — [techcrunch_ai](https://techcrunch.com/2026/04/24/deepseek-previews-new-ai-model-that-closes-the-gap-with-frontier-models/)
- **AirPods, Touch Bars, and the rest of Tim Cook&#8217;s legacy** — [theverge_ai](https://www.theverge.com/podcast/917965/apple-ceo-cook-ternus-transition)
- **The Download: supercharged scams and studying AI healthcare** — [mit_tech_review](https://www.technologyreview.com/2026/04/24/1136400/the-download-supercharged-scams-questionable-ai-healthcare/)
- **Musk vs. Altman is here, and it&#8217;s going to get messy** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/917755/musk-altman-openai-xai-gossip)
- **China’s DeepSeek previews new AI model a year after jolting US rivals** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/918035/deepseek-preview-v4-ai-model)
- **Prestigious photo contest answers ‘what is a photo?’** — [theverge_ai](https://www.theverge.com/gadgets/918016/prestigious-photo-contest-answers-what-is-a-photo)
- **Meta’s loss is Thinking Machines’ gain** — [techcrunch_ai](https://techcrunch.com/2026/04/24/metas-loss-is-thinking-machines-gain/)
- **ComfyUI hits $500M valuation as creators seek more control over AI-generated media** — [techcrunch_ai](https://techcrunch.com/2026/04/24/comfyui-hits-500m-valuation-as-creators-seek-more-control-over-ai-generated-media/)
- **Nothing introduces an AI-powered dictation tool** — [techcrunch_ai](https://techcrunch.com/2026/04/24/nothing-introduces-an-ai-powered-dictation-tool/)
- **In another wild turn for AI chips, Meta signs deal for millions of Amazon AI CPUs** — [techcrunch_ai](https://techcrunch.com/2026/04/24/in-another-wild-turn-for-ai-chips-meta-signs-deal-for-millions-of-amazon-ai-cpus/)
- **9点1氪丨马斯克花4000多亿买下00后公司；世界杯决赛门票转手价近230万美元** — [36kr](https://36kr.com/p/3781532841581576?f=rss)
- **sjsyrek/design-council** — [github](https://github.com/sjsyrek/design-council)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **巨星农牧：一季度公司的商品肥猪完全成本约为6.35元/斤** — [36kr](https://36kr.com/newsflashes/3782000516635648?f=rss)
- **Momenta一年间量产搭载量逾80万台** — [36kr](https://36kr.com/newsflashes/3781966595234825?f=rss)
- **百度智能云上线DeepSeek-V4** — [36kr](https://36kr.com/newsflashes/3781942204128513?f=rss)
- **我国单机容量最大“超级充电宝”3号机组顺利投运** — [36kr](https://36kr.com/newsflashes/3781921407507459?f=rss)
- **本田在华研发转向中方主导** — [36kr](https://36kr.com/newsflashes/3781884274318344?f=rss)
- **下游需求激增，CPU重回AI核心，A股布局公司梳理** — [36kr](https://36kr.com/newsflashes/3781844281007361?f=rss)
- **kimi-K2-6/kimi-K2.6** — [github](https://github.com/kimi-K2-6/kimi-K2.6)
- **selmakcby/claude-agents-skills** — [github](https://github.com/selmakcby/claude-agents-skills)
- **jwangkun/hermes-agent-guide** — [github](https://github.com/jwangkun/hermes-agent-guide)
- **dainsiahtill-dev/Polaris** — [github](https://github.com/dainsiahtill-dev/Polaris)
- **chaohong-ai/ai-auto-work** — [github](https://github.com/chaohong-ai/ai-auto-work)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **chekusu/wanman** — [github](https://github.com/chekusu/wanman)
- **intertwine/dspy-agent-skills** — [github](https://github.com/intertwine/dspy-agent-skills)
- **muxprotocol/kalshi-trading-bot** — [github](https://github.com/muxprotocol/kalshi-trading-bot)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **TheRealSeanDonahoe/agents-md** — [github](https://github.com/TheRealSeanDonahoe/agents-md)
- **alchaincyf/huashu-design** — [github](https://github.com/alchaincyf/huashu-design)
- **司美格鲁肽专利到期月余未见“国产首证”，多家申报企业称审批因数据保护期“暂缓”** — [36kr](https://36kr.com/newsflashes/3781834150976773?f=rss)
- **首个全国产控制系统水光互补项目今天投运** — [36kr](https://36kr.com/newsflashes/3781761309400068?f=rss)
- **天猫618推家电"送装一体"，覆盖全国95%区域** — [36kr](https://36kr.com/newsflashes/3781735819222022?f=rss)
- **潘功胜：持续整治金融机构“内卷式”竞争，高质量统筹做好金融“五篇大文章”** — [36kr](https://36kr.com/newsflashes/3781734984473856?f=rss)
- **美图立方视觉艺术中心开工，预计2028年投入使用** — [36kr](https://36kr.com/newsflashes/3781662685371396?f=rss)
- **阿塞拜疆主权财富基金第一季度抛售约22吨黄金，十多年来首次减持** — [36kr](https://36kr.com/newsflashes/3781654300450048?f=rss)
- **“固收+”基金规模突破3万亿元** — [36kr](https://36kr.com/newsflashes/3781603152780293?f=rss)
- **甲骨文密歇根数据中心获160亿美元融资** — [36kr](https://36kr.com/newsflashes/3781600900176901?f=rss)
- **36氪首发 | 核心团队来自微软，获近亿投资，要打通AI进厂最后一公里** — [36kr](https://36kr.com/p/3781548853533959?f=rss)
- **低头是日常，抬头是阅读** — [36kr](https://36kr.com/p/3780986341153798?f=rss)
- **最前线｜AI+激光通信，中科天塔要用「太空智驾」体系实现卫星管理模式的三级跨越** — [36kr](https://36kr.com/p/3780910411193602?f=rss)
- **氪星晚报｜美团万亿级参数大模型开放测试，训练全程由国产算力集群完成；百度联盟正式发布海外App业务；央行等八部门发布金融产品网络营销管理办法** — [36kr](https://36kr.com/p/3777694346548482?f=rss)
- **科氪|高配不溢价，20万内首选！国民好车2.0深蓝L06增程版折后价低至127155元起** — [36kr](https://36kr.com/p/3780654186535941?f=rss)
- **YilmazKadir/Volt** — [github](https://github.com/YilmazKadir/Volt)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **g2i-ai/agents** — [github](https://github.com/g2i-ai/agents)
- **realZillionX/InspireSkill** — [github](https://github.com/realZillionX/InspireSkill)
- **Google-Cloud-AI/agent-platform** — [github](https://github.com/Google-Cloud-AI/agent-platform)
- **Mahiruxia/hermes-forge** — [github](https://github.com/Mahiruxia/hermes-forge)
- **自动驾驶赛道DeepSeek，轻舟智航率先进军物理AI** — [qbitai](https://www.qbitai.com/2026/04/407026.html)
- **硬刚GPT-Image-2！国产AI生图“天花板”又被捅破了？** — [qbitai](https://www.qbitai.com/2026/04/406994.html)
- **AI自主监测宠物健康，陪狗都不用自己来了！涂鸦Hey Tuya打造全屋智能“超级入口”** — [qbitai](https://www.qbitai.com/2026/04/406973.html)
- **燃油SUV车主熬出头了！华为乾崑智驾加持，全新奥迪Q5L率先实现智能化** — [qbitai](https://www.qbitai.com/2026/04/406960.html)
- **0博士组合拿下ICLR时间检验奖！两个GPT天才本科生+二本逆袭LeCun弟子，十年论文终封神** — [qbitai](https://www.qbitai.com/2026/04/406892.html)
- **DeepSeek V4报告太详尽了！484天换代之路全公开** — [qbitai](https://www.qbitai.com/2026/04/406809.html)
- **Mobileye 2026财年一季度营收增长27%，自动驾驶商业化进程持续推进** — [qbitai](https://www.qbitai.com/2026/04/406775.html)
- **优必选发布Thinker cosmos：加码开发者生态，推动人形机器人走向规模化** — [qbitai](https://www.qbitai.com/2026/04/406806.html)
- **PPIO首批上线DeepSeek-V4预览版，1M超长上下文能力开箱即用** — [qbitai](https://www.qbitai.com/2026/04/406802.html)
- **DeepSeek-V4发布，华为云首发适配** — [qbitai](https://www.qbitai.com/2026/04/406791.html)