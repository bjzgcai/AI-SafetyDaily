# AI Daily Digest [AI 安全] - 2026-05-08


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-05-08
**Author:** Senior AI Safety Research Analyst

## Highlights

Three significant academic developments dominate today's safety landscape, addressing critical gaps in evaluation, defense, and attack vectors. First, **XL-SafetyBench: A Country-Grounded Cross-Cultural Benchmark for LLM Safety and Cultural Sensitivity** introduces a suite of 5,500 test cases across 10 country-language pairs, challenging the prevailing English-centric paradigm of safety evaluation by distinguishing between universal harms and culturally embedded sensitivities. Second, the emergence of **Stateful Agent Backdoor** marks a concerning evolution in adversarial threats, demonstrating how malicious behaviors can persist across multiple sessions under permission isolation, moving beyond the stateless attacks previously assumed to be the primary risk. Third, **Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** offers a theoretical advance in alignment defense, proposing that safety constraints can be enforced through geometric bottlenecks in parameter space to prevent circumvention during persistent harmful fine-tuning (HFT).

## Adversarial Attacks & Robustness

The landscape of adversarial threats is shifting from static, single-turn interactions to dynamic, stateful, and multi-modal attacks. A comprehensive **SoK: Robustness in Large Language Models against Jailbreak Attacks** provides a necessary framework for this transition, arguing that existing evaluation practices relying on narrow metrics like attack success rate fail to capture the multidimensional nature of LLM security. This critique is substantiated by new empirical findings in **Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models**, which demonstrates that models can be coerced into revealing training data through quiz-style multiple-choice questions, achieving an average ROC-AUC of approximately 0.85 across six widely used models.

However, the most critical vulnerability identified today lies in the persistence of attacks. While traditional backdoor attacks are confined to single sessions, **Stateful Agent Backdoor** extends the attack lifecycle across multiple sessions using a Mealy machine model. This allows for autonomous, incremental execution following a one-time trigger injection, posing a severe risk to long-term agent deployments. Complementing this, **LeakDojo: Decoding the Leakage Threats of RAG Systems** reveals that Retrieval-Augmented Generation systems are susceptible to query generation and adversarial instruction attacks that expose valuable databases, with the study benchmarking six existing attacks across fourteen LLMs.

Defensive strategies are evolving to match this complexity. **Information Theoretic Adversarial Training of Large Language Models** proposes continuous adversarial training methods leveraging gradient-based perturbations in the embedding space, aiming to improve robustness without the computational expense of previous approaches. In the domain of vision, **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** addresses the specific challenge of adapting classification-oriented adversarial generation to the detection attack space, where attacks may cause object misclassification or disappearance. Furthermore, **Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning** evaluates four RAG architectures under controlled single-document poisoning, finding that architectures designed to handle conflicting information, such as multi-agent debate, remain largely untested against adversarially optimized contradictions.

## Privacy Protection & Federated Learning

Privacy-preserving computation continues to be a focal point, particularly in federated learning (FL) and spatial retrieval contexts. **AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics** reframes client participation as a timeliness-aware systems problem using Age of Information (AoI). The authors compare three lightweight policies, suggesting that relying on stale client information due to stragglers or dropouts can compromise security analytics pipelines. In parallel, **FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning** explores the challenges of watermark radioactivity testing in FL, noting that secure aggregation allows the server to aggregate updates without seeing raw data, yet attribution remains underexplored.

For spatial data, **Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs** introduces PAS (Privacy Anchor Substitution). Unlike conventional differential privacy methods that directly perturb user locations, PAS represents location with relative anchor encoding, achieving approximately 370-400m adversarial location error while maintaining utility. Theoretical advances in differential privacy are also significant; **Privacy by Postprocessing the Discrete Laplace Mechanism** demonstrates that the classical discrete Laplace mechanism can be post-processed to yield unbiased estimators of subexponential functions. Additionally, **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling** derives tight upper and lower bounds for DP-SGD, offering transparent closed-form bounds compared to non-transparent implicit formulas for Poisson subsampling. Finally, **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** introduces a family of PAC-private zeroth-order mechanisms that delivers usable utility at a privacy regime where membership-inference attack posterior success rate is bounded at the prior.

## Alignment, Interpretability & Governance

Alignment research is increasingly focusing on the geometric properties of model representations and the reliability of evaluation metrics. **Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** traces the failure of existing defenses to the inherent redundancy of high-dimensional parameter space, proposing that attackers exploit optimization trajectories orthogonal to defense constraints. To counter this, the authors propose Safety Bottleneck Regularization. This aligns with findings in **Invariant Features in Language Models: Geometric Characterization and Model Attribution**, which propose a local geometric framework where semantically equivalent inputs occupy structured regions in latent space, preserving semantic identity in invariant subspaces.

Interpretability tools are becoming more granular. **SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** addresses the limitation of fixed sparsity levels in common architectures, allowing for varying complexity in real-world data. Similarly, **Patch-Effect Graph Kernels for LLM Interpretability** reframes mechanistic analysis as a graph machine-learning problem, representing activation-patching profiles as patch-effect graphs to compare systematic interventions.

Governance and evaluation face significant challenges regarding metric gaming and context divergence. **Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** models the audit protocol as a published transformation graph, warning that scalar metrics can become optimization targets for strategic platforms without reducing true harm. This is corroborated by **Measuring Evaluation-Context Divergence in Open-Weight LLMs**, which defines evaluation-context divergence as an observable within-item change in behavior induced by framing a fixed task as an evaluation versus a live deployment interaction. The study finds that across five instruction-tuned checkpoints, behavior depends heavily on whether a prompt looks like an evaluation.

## Agent Security & Governance

The rise of autonomous agents introduces new vectors for abuse and requires robust governance frameworks. **Autonomous Adversary: Red-Teaming in the age of LLM** analyzes how Language Model Agents (LMAs) intersect with core offensive functions, benchmarking them across lateral-movement scenarios. This highlights the dual-use nature of agent technology. To mitigate host-level risks, **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** argues that risks cannot be addressed by ad hoc blocking rules alone, advocating for Trusted Execution Environment (TEE)-backed isolation to prevent malicious steering of host-side resources.

Memory and reasoning reliability are also critical. **STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?** identifies a critical failure mode called Implicit Conflict, where a later observation invalidates an earlier memory without explicit negation. The benchmark of 400 expert-validated conflict scenarios suggests current systems struggle with this contextual inference. Furthermore, **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** introduces the first source attribution evaluation framework using a reproducible AST parser, noting that current approaches often trust models to self-cite accurately, risking bias.

Industry developments reflect these theoretical concerns. OpenAI has launched a **Trusted Contact** safety feature, allowing adult users to assign an emergency contact for mental health and safety concerns, which the company states will not replace professional care. Meanwhile, reports indicate that Anthropic's Mythos model has been used by security researchers to unearth high-severity bugs in Firefox, raising questions about the governance of autonomous vulnerability discovery tools.

## Safety Benchmarks & Evaluation

The push for more rigorous evaluation is evident across multiple domains. **XL-SafetyBench** (mentioned in Highlights) specifically targets the lack of country-specific harms in current benchmarks. In graph learning, **On the Safety of Graph Representation Learning** introduces GRL-Safety, a multi-axis safety evaluation benchmark for Graph Representation Learning methods, evaluating twelve representative methods across twelve axes including graph signals and structural groups. For multimodal systems, **Are We Making Progress in Multimodal Domain Generalization? A Comprehensive Benchmark Study** questions whether reported performance gains reflect genuine algorithmic progress or artifacts of inconsistent evaluation protocols.

In agent evaluation, **CreativityBench: Evaluating Agent Creative Reasoning via Affordance-Based Tool Repurposing** studies the ability of models to repurpose available objects by reasoning about their affordances, building a large-scale affordance knowledge base. **SWE-WebDevBench: Evaluating Coding Agent Application Platforms as Virtual Software Agencies** introduces a 68-metric evaluation framework to assess agents as virtual software development agencies, spanning understanding business requirements to maintaining business readiness.

## Open-Source Security Tools

Several open-source projects have emerged to support these safety and security initiatives. **AiSOC** (GitHub: beenuar/AiSOC) is an open-source AI-powered Security Operations Center offering alert fusion, purple-team drills, and agent-assisted triage, licensed under MIT. **OpenSearch-VL** (GitHub: shawn0728/OpenSearch-VL) provides a fully open recipe for training frontier multimodal deep search agents, emphasizing high-quality data curation and agentic reinforcement learning. **ProcMon-MCP** (GitHub: 0xhackerfren/ProcMon-MCP) exposes process monitoring and ETW tracing functions to AI agents to assist in security work, facilitating better visibility into agent behavior.

## Looking Forward

Several unresolved theoretical questions and hypotheses await validation. First, the efficacy of **Stateful Agent Backdoors** remains to be tested at scale; it is unclear whether current detection mechanisms can identify persistent state changes across sessions without explicit logging. Second, the **Metric Gaming** problem identified in safety audits requires a formalization of audit protocols that are robust to strategic manipulation, potentially requiring game-theoretic approaches to certification. Third, the **Cross-Cultural Safety** gap highlighted by XL-SafetyBench suggests that current alignment strategies may inadvertently enforce Western-centric norms, necessitating a re-evaluation of alignment objectives in a global context. Finally, the relationship between **Geometric Bottlenecks** and model robustness needs further empirical validation to determine if Safety Anchor can generalize across different model architectures and fine-tuning regimes without compromising utility.

---


## References

- **XL-SafetyBench: A Country-Grounded Cross-Cultural Benchmark for LLM Safety and Cultural Sensitivity** — [huggingface_papers](https://arxiv.org/abs/2605.05662)
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
- **Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation** — [arxiv_cr](https://arxiv.org/abs/2605.06393v1)
- **Why Global LLM Leaderboards Are Misleading: Small Portfolios for Heterogeneous Supervised ML** — [arxiv_lg](https://arxiv.org/abs/2605.06656v1)
- **PianoCoRe: Combined and Refined Piano MIDI Dataset** — [arxiv_lg](https://arxiv.org/abs/2605.06627v1)
- **Online Bayesian Calibration under Gradual and Abrupt System Changes** — [arxiv_lg](https://arxiv.org/abs/2605.06612v1)
- **SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders** — [arxiv_lg](https://arxiv.org/abs/2605.06610v1)
- **CLAD: A Clustered Label-Agnostic Federated Learning Framework for Joint Anomaly Detection and Attack Classification** — [arxiv_lg](https://arxiv.org/abs/2605.06571v1)
- **Market-Alignment Risk in Pricing Agents: Trace Diagnostics and Trace-Prior RL under Hidden Competitor State** — [arxiv_lg](https://arxiv.org/abs/2605.06529v1)
- **Beyond Negative Rollouts: Positive-Only Policy Optimization with Implicit Negative Gradients** — [arxiv_cl](https://arxiv.org/abs/2605.06650v1)
- **Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents** — [arxiv_cl](https://arxiv.org/abs/2605.06635v1)
- **Patch-Effect Graph Kernels for LLM Interpretability** — [arxiv_cl](https://arxiv.org/abs/2605.06480v1)
- **Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling: Tight Upper and Lower Bounds** — [arxiv_cr](https://arxiv.org/abs/2605.06259v1)
- **Profiling for Pennies: Unveiling the Privacy Iceberg of LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2605.06232v1)
- **Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning** — [arxiv_cr](https://arxiv.org/abs/2605.05928v1)
- **$α$-Wasserstein Mechanism for Rényi Pufferfish Privacy** — [arxiv_cr](https://arxiv.org/abs/2605.05723v1)
- **Evaluating the Reliability of Multiple Large Language Models in Risk Assessment: A CIS Controls Based Approach** — [arxiv_cr](https://arxiv.org/abs/2605.05424v1)
- **PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization** — [arxiv_cr](https://arxiv.org/abs/2605.06505v1)
- **Autonomous Adversary: Red-Teaming in the age of LLM** — [arxiv_cr](https://arxiv.org/abs/2605.06486v1)
- **Are We Making Progress in Multimodal Domain Generalization? A Comprehensive Benchmark Study** — [arxiv_lg](https://arxiv.org/abs/2605.06643v1)
- **Hybrid Quantum-Classical GANs for the Generation of Adversarial Network Flows** — [arxiv_lg](https://arxiv.org/abs/2605.06629v1)
- **LiVeAction: a Lightweight, Versatile, and Asymmetric Neural Codec Design for Real-time Operation** — [arxiv_lg](https://arxiv.org/abs/2605.06628v1)
- **Cross-Modal Navigation with Multi-Agent Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2605.06595v1)
- **ReActor: Reinforcement Learning for Physics-Aware Motion Retargeting** — [arxiv_lg](https://arxiv.org/abs/2605.06593v1)
- **DINORANKCLIP: DINOv3 Distillation and Injection for Vision-Language Pretraining with High-Order Ranking Consistency** — [arxiv_lg](https://arxiv.org/abs/2605.06592v1)
- **Towards Metric-Faithful Neural Graph Matching** — [arxiv_lg](https://arxiv.org/abs/2605.06588v1)
- **Distributionally-Robust Learning to Optimize** — [arxiv_lg](https://arxiv.org/abs/2605.06585v1)
- **Directional Consistency as a Complementary Optimization Signal: The GONO Framework** — [arxiv_lg](https://arxiv.org/abs/2605.06575v1)
- **SNAPO: Smooth Neural Adjoint Policy Optimization for Optimal Control via Differentiable Simulation** — [arxiv_lg](https://arxiv.org/abs/2605.06570v1)
- **Dynamic Treatment on Networks** — [arxiv_lg](https://arxiv.org/abs/2605.06564v1)
- **Verifier-Backed Hard Problem Generation for Mathematical Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.06660v1)
- **MASPO: Joint Prompt Optimization for LLM-based Multi-Agent Systems** — [arxiv_cl](https://arxiv.org/abs/2605.06623v1)
- **UniSD: Towards a Unified Self-Distillation Framework for Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.06597v1)
- **PairAlign: A Framework for Sequence Tokenization via Self-Alignment with Applications to Audio Tokenization** — [arxiv_cl](https://arxiv.org/abs/2605.06582v1)
- **Continuous Latent Diffusion Language Model** — [arxiv_cl](https://arxiv.org/abs/2605.06548v1)
- **STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?** — [arxiv_cl](https://arxiv.org/abs/2605.06527v1)
- **Invariant Features in Language Models: Geometric Characterization and Model Attribution** — [arxiv_cl](https://arxiv.org/abs/2605.06458v1)
- **Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation** — [arxiv_cr](https://arxiv.org/abs/2605.06324v1)
- **Stateful Agent Backdoor** — [arxiv_cr](https://arxiv.org/abs/2605.06158v1)
- **Secure Seed-Based Multi-bit Watermarking for Diffusion Models from First Principles** — [arxiv_cr](https://arxiv.org/abs/2605.06153v1)
- **Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks** — [arxiv_cr](https://arxiv.org/abs/2605.05995v1)
- **LeakDojo: Decoding the Leakage Threats of RAG Systems** — [arxiv_cr](https://arxiv.org/abs/2605.05818v1)
- **Is Escalation Worth It? A Decision-Theoretic Characterization of LLM Cascades** — [arxiv_cl](https://arxiv.org/abs/2605.06350v1)
- **Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity** — [arxiv_cl](https://arxiv.org/abs/2605.06327v1)
- **Quantifying the Statistical Effect of Rubric Modifications on Human-Autorater Agreement** — [arxiv_cl](https://arxiv.org/abs/2605.06283v1)
- **Linear Semantic Segmentation for Low-Resource Spoken Dialects** — [arxiv_cl](https://arxiv.org/abs/2605.06276v1)
- **Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning** — [arxiv_cl](https://arxiv.org/abs/2605.06241v1)
- **Contrastive Identification and Generation in the Limit** — [arxiv_cl](https://arxiv.org/abs/2605.06211v1)
- **Nonsense Helps: Prompt Space Perturbation Broadens Reasoning Exploration** — [huggingface_papers](https://arxiv.org/abs/2605.05566)
- **Think, then Score: Decoupled Reasoning and Scoring for Video Reward Modeling** — [huggingface_papers](https://arxiv.org/abs/2605.05922)
- **Skill1: Unified Evolution of Skill-Augmented Agents via Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.06130)
- **MARBLE: Multi-Aspect Reward Balance for Diffusion RL** — [huggingface_papers](https://arxiv.org/abs/2605.06507)
- **ReflectDrive-2: Reinforcement-Learning-Aligned Self-Editing for Discrete Diffusion Driving** — [huggingface_papers](https://arxiv.org/abs/2605.04647)
- **A Foundation Model for Zero-Shot Logical Rule Induction** — [huggingface_papers](https://arxiv.org/abs/2605.04916)
- **When to Think, When to Speak: Learning Disclosure Policies for LLM Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.03314)
- **D-OPSD: On-Policy Self-Distillation for Continuously Tuning Step-Distilled Diffusion Models** — [huggingface_papers](https://arxiv.org/abs/2605.05204)
- **EMO: Pretraining Mixture of Experts for Emergent Modularity** — [arxiv_cl](https://arxiv.org/abs/2605.06663v1)
- **When No Benchmark Exists: Validating Comparative LLM Safety Scoring Without Ground-Truth Labels** — [arxiv_cl](https://arxiv.org/abs/2605.06652v1)
- **StraTA: Incentivizing Agentic Reinforcement Learning with Strategic Trajectory Abstraction** — [arxiv_cl](https://arxiv.org/abs/2605.06642v1)
- **Recursive Agent Optimization** — [arxiv_cl](https://arxiv.org/abs/2605.06639v1)
- **AI Co-Mathematician: Accelerating Mathematicians with Agentic AI** — [huggingface_papers](https://arxiv.org/abs/2605.06651)
- **Auto Research with Specialist Agents Develops Effective and Non-Trivial Training Recipes** — [huggingface_papers](https://arxiv.org/abs/2605.05724)
- **The Granularity Axis: A Micro-to-Macro Latent Direction for Social Roles in Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.06196)
- **TabEmbed: Benchmarking and Learning Generalist Embeddings for Tabular Understanding** — [huggingface_papers](https://arxiv.org/abs/2605.04962)
- **CreativityBench: Evaluating Agent Creative Reasoning via Affordance-Based Tool Repurposing** — [huggingface_papers](https://arxiv.org/abs/2605.02910)
- **SWE-WebDevBench: Evaluating Coding Agent Application Platforms as Virtual Software Agencies** — [huggingface_papers](https://arxiv.org/abs/2605.04637)
- **The First Token Knows: Single-Decode Confidence for Hallucination Detection** — [huggingface_papers](https://arxiv.org/abs/2605.05166)
- **OpenSearch-VL: An Open Recipe for Frontier Multimodal Search Agents** — [huggingface_papers](https://arxiv.org/abs/2605.05185)
- **Stream-T1: Test-Time Scaling for Streaming Video Generation** — [huggingface_papers](https://arxiv.org/abs/2605.04461)
- **Lightning Unified Video Editing via In-Context Sparse Attention** — [huggingface_papers](https://arxiv.org/abs/2605.04569)
- **PhysForge: Generating Physics-Grounded 3D Assets for Interactive Virtual World** — [huggingface_papers](https://arxiv.org/abs/2605.05163)
- **OpenAI launches new voice intelligence features in its API** — [techcrunch_ai](https://techcrunch.com/2026/05/07/openai-launches-new-voice-intelligence-features-in-its-api/)
- **Elon Musk’s lawsuit is putting OpenAI’s safety record under the microscope** — [techcrunch_ai](https://techcrunch.com/2026/05/07/elon-musks-lawsuit-is-putting-openais-safety-record-under-the-microscope/)
- **Bumble is getting rid of the swipe, CEO says** — [techcrunch_ai](https://techcrunch.com/2026/05/07/bumble-is-getting-rid-of-the-swipe-ceo-says/)
- **Mira Murati’s deposition pulled back the curtain on Sam Altman’s ouster** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/926383/mira-murati-sam-altman-musk-trial-ouster)
- **Apple&#8217;s AirPods with cameras for AI are apparently close to production** — [theverge_ai](https://www.theverge.com/tech/926376/apple-airpods-cameras-ai-production)
- **SpaceX has a $55 billion plan to build AI chips in Texas** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/926356/spacex-terafab-plant-cost-ai-chips)
- **ChatGPT&#8217;s &#8216;Trusted Contact&#8217; will alert loved ones of safety concerns** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/925874/chatgpt-trusted-contact-emergency-self-harm-notification)
- **Startup Battlefield 200 applications close May 27: A shot at VC access, global visibility, TechCrunch coverage, and $100K** — [techcrunch_ai](https://techcrunch.com/2026/05/07/startup-battlefield-200-applications-close-may-27-a-shot-at-vc-access-global-visibility-techcrunch-coverage-and-100k/)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **Exhibit at TechCrunch Disrupt 2026: Get in front of 10,000 decision-makers before space runs out** — [techcrunch_ai](https://techcrunch.com/2026/05/07/exhibit-at-techcrunch-disrupt-2026-get-in-front-of-10000-decision-makers-before-space-runs-out/)
- **Aurora’s Chris Urmson on why self-driving trucks are finally ready to scale** — [techcrunch_ai](https://techcrunch.com/podcast/auroras-chris-urmson-on-why-self-driving-trucks-are-finally-ready-to-scale/)
- **2 days left: Get 50% off a second pass to TechCrunch Disrupt 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/07/2-days-left-get-50-off-a-second-pass-to-techcrunch-disrupt-2026/)
- **OpenClaw and Claude can put your AI-generated podcasts in Spotify** — [theverge_ai](https://www.theverge.com/entertainment/925916/save-to-spotify-ai-podcasts)
- **Google’s taking a big swing at AI health with the Fitbit Air** — [theverge_ai](https://www.theverge.com/gadgets/925458/google-health-fitbit-air-ai-coaching-wearables-fitness-trackers)
- **Scaling Trusted Access for Cyber with GPT-5.5 and GPT-5.5-Cyber** — [openai](https://openai.com/index/gpt-5-5-with-trusted-access-for-cyber)
- **The Download: the tech reshaping IVF and the rise of balcony solar** — [mit_tech_review](https://www.technologyreview.com/2026/05/07/1136956/the-download-ivf-tech-balcony-solar/)
- **Parloa builds service agents customers want to talk to** — [openai](https://openai.com/index/parloa)
- **Advancing voice intelligence with new models in the API** — [openai](https://openai.com/index/advancing-voice-intelligence-with-new-models-in-the-api)
- **The balcony solar boom is coming to the US** — [mit_tech_review](https://www.technologyreview.com/2026/05/07/1136933/balcony-solar-boom/)
- **What’s next for IVF** — [mit_tech_review](https://www.technologyreview.com/2026/05/07/1136946/whats-next-for-ivf-ai-robot-pgt-gene-editing/)
- **Five architects of the AI economy explain where the wheels are coming off** — [techcrunch_ai](https://techcrunch.com/2026/05/06/five-architects-of-the-ai-economy-explain-where-the-wheels-are-coming-off/)
- **Voi founders’ new AI startup Pit has become the latest rising star out of Stockholm** — [techcrunch_ai](https://techcrunch.com/2026/05/07/voi-founders-new-ai-startup-pit-has-become-the-latest-rising-star-out-of-stockholm/)
- **OpenAI introduces new ‘Trusted Contact’ safeguard for cases of possible self-harm** — [techcrunch_ai](https://techcrunch.com/2026/05/07/openai-introduces-new-trusted-contact-safeguard-for-cases-of-possible-self-harm/)
- **Perplexity’s Personal Computer is now available to everyone on Mac** — [techcrunch_ai](https://techcrunch.com/2026/05/07/perplexitys-personal-computer-is-now-available-everyone-on-mac/)
- **How Anthropic’s Mythos has rewritten Firefox’s approach to cybersecurity** — [techcrunch_ai](https://techcrunch.com/2026/05/07/how-anthropics-mythos-has-rewritten-firefoxs-approach-to-cybersecurity/)
- **China’s Moonshot AI raises $2B at $20B valuation as demand for open source AI skyrockets** — [techcrunch_ai](https://techcrunch.com/2026/05/07/chinas-moonshot-ai-raises-2b-at-20b-valuation-as-demand-for-open-source-ai-skyrockets/)
- **Spotify wants to become the home for AI-generated personal audio** — [techcrunch_ai](https://techcrunch.com/2026/05/07/spotify-wants-to-become-the-home-for-ai-generated-personal-audio/)
- **Spotify’s AI DJ now supports French, German, Italian, and Brazilian Portuguese** — [techcrunch_ai](https://techcrunch.com/2026/05/07/spotifys-ai-dj-now-supports-french-german-italian-and-brazilian-portuguese/)
- **Negai-ai/AgentClaw** — [github](https://github.com/Negai-ai/AgentClaw)
- **dingdingpw/monitor** — [github](https://github.com/dingdingpw/monitor)
- **cenconq25/claude-code-app-studio** — [github](https://github.com/cenconq25/claude-code-app-studio)
- **beenuar/AiSOC** — [github](https://github.com/beenuar/AiSOC)
- **shawn0728/OpenSearch-VL** — [github](https://github.com/shawn0728/OpenSearch-VL)
- **awizemann/harness** — [github](https://github.com/awizemann/harness)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **k1ng0fn0th1ng/CrystalForge** — [github](https://github.com/k1ng0fn0th1ng/CrystalForge)
- **Jason-Cyr/ai-shared-brain** — [github](https://github.com/Jason-Cyr/ai-shared-brain)
- **alterhq/openpets** — [github](https://github.com/alterhq/openpets)
- **huseynovvusal/blamebot** — [github](https://github.com/huseynovvusal/blamebot)
- **ZhongKuang/TAAC2026-CLI** — [github](https://github.com/ZhongKuang/TAAC2026-CLI)
- **0xhackerfren/ProcMon-MCP** — [github](https://github.com/0xhackerfren/ProcMon-MCP)
- **Autoloops/upskill** — [github](https://github.com/Autoloops/upskill)
- **wjn1996/HeavySkill** — [github](https://github.com/wjn1996/HeavySkill)
- **原生Agent杀入画布！一站式搞定专业创作，全程可控、不抽卡** — [qbitai](https://www.qbitai.com/2026/05/413912.html)
- **离谱！一句话+百元预算，这只龙虾就给我搓出了一支百万级广告片？** — [qbitai](https://www.qbitai.com/2026/05/414006.html)
- **00后下场整顿Agent：啥都不学就能用好AI，这才是正确打开方式** — [qbitai](https://www.qbitai.com/2026/05/413612.html)
- **一年磨一剑，今年最炸机器人Demo来了！** — [qbitai](https://www.qbitai.com/2026/05/413830.html)
- **云知声山海知医慧保大模型重磅发布：以高密智能深耕高价值场景，重构医疗保险数智新生态** — [qbitai](https://www.qbitai.com/2026/05/413782.html)
- **波士顿动力泯然众人了，高管集体出走，机器人“量产”只能造4台** — [qbitai](https://www.qbitai.com/2026/05/413613.html)
- **英伟达重新思考AI TCO：为何每Token成本才是唯一重要的指标** — [qbitai](https://www.qbitai.com/2026/05/413604.html)
- **8点1氪丨段永平再加仓泡泡玛特；多平台已下架“全李酒店”；世界杯决赛门票1张200万美元，FIFA回应** — [36kr](https://36kr.com/p/3799881836633093?f=rss)
- **氪星晚报 ｜千问PC端上线AI语音输入；宝马一季度利润降25%，至23亿欧元** — [36kr](https://36kr.com/p/3799089350712324?f=rss)
- **联想创投旗下基金等入股微分智飞，后者为飞行具身智能研发商** — [36kr](https://36kr.com/newsflashes/3800034382060552?f=rss)
- **第一代全固态电池迈入规模化市场，「纯锂新能源」完成数千万元Pre-A+轮融资 | 36氪首发** — [36kr](https://36kr.com/p/3800022823951363?f=rss)
- **印度投资者转向海外市场，因国内缺乏AI题材且回报率低** — [36kr](https://36kr.com/newsflashes/3800007655480325?f=rss)
- **爱旭股份旗下山东太阳能公司增资至63亿，增幅26%** — [36kr](https://36kr.com/newsflashes/3800001066376200?f=rss)
- **英伟达CEO黄仁勋：下一代AI基础设施将需要大量的光学连接，铜线已无法满足需求** — [36kr](https://36kr.com/newsflashes/3799989766429697?f=rss)
- **36氪首发 | 清华系AI Infra厂商完成数亿元融资，以GPU为核心重构计算机系统架构** — [36kr](https://36kr.com/p/3799984046333186?f=rss)
- **兰州未来创新产业发展基金成立，注册资本约2亿** — [36kr](https://36kr.com/newsflashes/3799978675805441?f=rss)
- **Plaud获头部大厂投资，目前估值达20亿美元｜硬氪独家** — [36kr](https://36kr.com/p/3799129165863937?f=rss)
- **OpenAI推出“可信联系人”安全功能** — [36kr](https://36kr.com/newsflashes/3799937097129224?f=rss)
- **Anthropic旗下Mythos模型打乱白宫人工智能战略** — [36kr](https://36kr.com/newsflashes/3799949875617031?f=rss)
- **在模型厂碾压之前，AI视频Agent产品是否只能挣波快钱？** — [36kr](https://36kr.com/p/3786528811572481?f=rss)
- **每日互动：一季度公司AI相关业务收入已接近去年全年水平** — [36kr](https://36kr.com/newsflashes/3800023288569088?f=rss)
- **高盛将沪深300指数12个月目标位设在5300点，指出投资A股颇具吸引力** — [36kr](https://36kr.com/newsflashes/3800001611422725?f=rss)
- **“阶跃星辰”将完成近25亿美元融资** — [36kr](https://36kr.com/newsflashes/3800006173973760?f=rss)
- **A股三大指数集体低开，半导体、光模块概念领跌** — [36kr](https://36kr.com/newsflashes/3799967438756872?f=rss)