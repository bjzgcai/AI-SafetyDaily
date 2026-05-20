# AI Daily Digest [AI 安全] - 2026-05-20


# AI Safety Digest: 2026-05-20
## A Thematic Review of Alignment, Adversarial Robustness, and Agentic Security

Today’s literature presents a field intensely focused on the security of increasingly complex, agentic AI systems. The central narrative is a rapid expansion of the attack surface across modalities—from text and vision to embodied robotics and autonomous agents—prompting a parallel development of more sophisticated, nuanced, and computationally efficient defenses. A clear trend is the move from static, single-turn analysis towards dynamic, interactive, and systems-level security frameworks.

### Highlights

Three developments stand out for their methodological novelty and implications:

1.  **The Agentic Attack Surface Crystallizes:** Multiple works demonstrate that safety cannot be an afterthought for autonomous agents. The papers **OEP** and **Agent Security is a Systems Problem** fundamentally reframe the issue. **OEP** reveals a subtle poisoning vector where agents are misled into generating plausible but harmful "experiences" that corrupt their self-evolution process. **Agent Security is a Systems Problem** argues compellingly that the model itself must be treated as an untrusted component, requiring security invariants enforced at the system level—a paradigm shift from the dominant focus on model robustness.
2.  **Attacks Grow More Compositional and Cross-Modal:** The attack methodology is advancing beyond isolated tricks. **DMN** demonstrates jailbreaks for Multimodal LLMs by distributing malicious intent across multiple images, exploiting weaker multi-image safety alignment. **RoboJailBench** establishes a necessary benchmark for evaluating adversarial attacks and defenses in embodied robotic agents, moving evaluations beyond ad-hoc datasets to include metrics for the security-utility trade-off.
3.  **Practical, Lightweight Defenses Emerge:** Counterbalancing the complex attacks, several defenses prioritize speed and deployability. **DFBScanner** and **HTell** both propose fast, data-free backdoor detectors. **HTell**'s method of inspecting a model's "prediction head" via random probing is particularly notable for its elegance and efficiency. Similarly, the **pre-model safeguard** explored in **Exploring and Developing a Pre-Model Safeguard with Draft Models** seeks to filter unsafe prompts with lower computational cost than post-model guards.

### Adversarial Attacks & Robustness: From Prompts to Paradigms

The research on adversarial attacks reveals a bifurcation: one stream focuses on refining attacks against specific architectures, while another develops more fundamental defenses against classes of attacks.

Attackers are leveraging **compositional and obfuscation techniques**. **DMN** shows that multi-image inputs create a larger attack space for MLLMs, where harmful requests can be subtly distributed. **On the Geometric Limits of Transformer Defenses** provides a theoretical grounding for why this works, demonstrating that multi-operator obfuscated prompts can cause "latent embedding collapse," where poisoned inputs become indistinguishable from benign ones in a model's representation space. This finding critically shows that high classification performance (detection accuracy) does not imply representational robustness, challenging how defenses are evaluated. **DarkLLM** introduces a meta-attack where an LLM is trained to translate natural language instructions into adversarial vectors, suggesting a future of language-driven, generalizable attacks.

In response, defenses are becoming more proactive and aware of model internals. **Be Kind, Rewrite** explores using LLM rewriting as a proactive defense against data poisoning, theoretically showing that open-book benign rewriting (OBBR) can reduce the probability of a poisoned output. For prompt injection, **Detecting Fluent Optimization-Based Adversarial Prompts via Sequential Entropy Changes** reframes detection as an online change-point problem over token-level entropy streams, offering a model-agnostic, training-free detector (**CPD Online**). This contrasts with, and is more practical than, defenses relying on perplexity thresholds.

### Model Alignment, Interpretability, and Governance

Advances here focus on making alignment processes more robust and on understanding the *mechanisms* of model behavior to enable better control.

The Retrieval-Augmented Generation (RAG) paradigm is a focal point for new alignment challenges. **BiRD** identifies a fundamental flaw in many RAG defenses: their exclusive focus on semantic content relevance, while neglecting the *retrieval context* defined by ranking structures. By modeling the bidirectional ranking behavior of poisoned versus benign documents, **BiRD** offers a more robust defense mechanism. Separately, **Auditing Privacy in Multi-Tenant RAG under Account Collusion** exposes a critical failure in per-account Differential Privacy (DP) guarantees. The authors show that when multiple accounts within the same tenant collude, the joint privacy leakage degrades at a rate of Θ(√k · ε_acc), a result with serious implications for the deployment of private RAG services.

On the interpretability front, **Mechanisms of Object Localization in Vision-Language Models** uses mechanistic tools like attention knockout to reveal that localization in models like LLaVA-1.5 is driven by a "containerization" mechanism, where special tokens create context windows for visual grounding. This work, along with **Where Does Authorship Signal Emerge in Encoder-Based Language Models?**, exemplifies the shift from black-box to white-box analysis, showing that stylistic features are uniformly available across layers and that the final scoring mechanism is what determines where authorship signal is consolidated.

### Privacy Protection & Federated Learning

Research continues to push FL into more resource-constrained and realistic settings, while grappling with its inherent vulnerabilities.

**Towards Family-Grouped Hierarchical Federated Learning** makes a noteworthy feasibility study for FL on sub-5KB models, targeting ultra-resource-constrained wearables for ECG monitoring. This three-tier "Family-FL" architecture addresses the prohibitive communication overhead of standard FL. However, the security of FL itself remains precarious. **Detecting and Mitigating Backdoor Attacks in OTA-FL Systems** tackles the specific vulnerability of Over-the-Air FL, where the superposition of wireless signals makes it hard to detect poisoned updates. Their two-stage robust aggregation scheme is designed to distinguish malicious gradients from benign drift under non-IID data.

The convergence of privacy and game theory is explored in **The Privacy Subsidy in Glosten-Milgrom**, which derives a closed-form bid-ask spread under a privacy mechanism (a binary flip channel). This work formally quantifies the "privacy subsidy"—the economic cost of a market maker's reduced information—and provides a welfare decomposition, linking information theory directly to market efficiency.

### Safety Benchmarks and Evaluation

The call for rigorous, multidimensional benchmarks is answered by several new efforts.

**RoboJailBench** is a significant contribution, providing the first comprehensive benchmark for adversarial attacks and defenses in embodied robotic agents. It moves beyond attack success rate to evaluate the critical trade-off between security and the ability to follow benign commands. For long-context and agentic systems, **MixRea** introduces the concept of explicit-implicit reasoning, inspired by human inattentional blindness, to test whether LLMs can attend to subtle cues under explicit task instructions. **FineBench** addresses the gap in evaluating VLMs for fine-grained human activity understanding in long-form videos, combining dense QA coverage with frame-level spatial/temporal grounding. Finally, **MSAVBench** provides an adaptive framework for evaluating multi-shot audio-video generation models, a critical capability for next-generation narrative AI.

### Agent Security & Systemic Governance

This is arguably the most forward-looking theme of the digest. The community is recognizing that security for autonomous agents is a *systems problem*.

**Agent Security is a Systems Problem** is a position paper that advocates for treating the AI model as an untrusted component within a larger system, enforcing security invariants at the system level—a perspective drawn from OS, networking, and formal methods. This philosophy is operationalized in works like **PEEK**, which proposes caching reusable "orientation knowledge" about recurring external contexts for LLM agents, enabling more efficient and consistent long-horizon work.

The **OEP** attack is a direct threat to such agentic systems. By poisoning the self-evolving memory/experience of an LLM agent with locally correct but non-transferable experiences, an adversary can induce harmful generalizations during reflection—a subtle and potent attack that evades content-based safety filters. Defending against this requires the kind of systemic monitoring and verification advocated for in the systems security perspective.

On the open-source tooling side, **ExploitBench** is a notable framework for benchmarking AI agents' ability to perform end-to-end cyber exploitation, measuring their progress from finding vulnerable code to achieving arbitrary code execution. This provides a concrete testbed for red-teaming agentic systems in security contexts.

### Looking Forward

Several unresolved theoretical questions and hypotheses emerge from today's survey:

1.  **The Geometric-Representational Gap:** Can we formally connect the phenomenon of "latent embedding collapse" under obfuscation attacks to the generalization properties of a model? Does collapse in the embedding space imply brittleness on downstream tasks, or is it a form of adversarial equivalence that models must be robust to?
2.  **The Economics of Privacy and Alignment:** How should the "privacy subsidy" identified in market models be weighed against the utility gains in AI systems? Can we design alignment mechanisms with formal, quantifiable trade-offs between helpfulness, honesty, and user privacy?
3.  **Formalizing Agentic Security Invariants:** What is the minimal set of system-level security invariants required to safely contain a general-purpose, self-evolving LLM agent? How can these invariants be verified at runtime without crippling the agent's utility?
4.  **The Robustness-Utility Frontier in Embodied AI:** How should we fundamentally model and optimize the security-utility trade-off for embodied agents operating in dynamic, open-world environments? Current benchmarks are a start, but a theoretical framework is lacking.

The field is clearly moving beyond simple accuracy and robustness in static settings. The frontier now lies in securing interactive, compositional, and autonomous AI systems, requiring a synthesis of deep learning, systems security, and information theory.

---


## References

- **XAI FL-IDS: A Federated Learning and SHAP-Based Explainable Framework for Distributed Intrusion Detection Systems** — [arxiv_cr](https://arxiv.org/abs/2605.19448)
- **Lightweight and Fast Backdoor Model Detection** — [arxiv_cr](https://arxiv.org/abs/2605.18907)
- **RoboJailBench: Benchmarking Adversarial Attacks and Defenses in Embodied Robotic Agents** — [arxiv_cr](https://arxiv.org/abs/2605.19328)
- **BiRD: A Bidirectional Ranking Defense Mechanism for Retrieval Augmented Generation** — [arxiv_cr](https://arxiv.org/abs/2605.20123)
- **Towards Family-Grouped Hierarchical Federated Learning on Sub-5KB Models: A Feasibility Study of Privacy-Preserving ECG Monitoring for Ultra-Resource-Constrained Wearables** — [arxiv_cr](https://arxiv.org/abs/2605.18862)
- **Smooth Partial Lotteries for Stable Randomized Selection** — [arxiv_lg](https://arxiv.org/abs/2605.20069v1)
- **Decentralized autonomous organization and blockchain-based incentivization framework for community-based facilities management** — [arxiv_cr](https://arxiv.org/abs/2605.18773)
- **Fast and Lightweight Backdoor Detection via Head Random Probing** — [arxiv_cr](https://arxiv.org/abs/2605.18908)
- **DMN: A Compositional Framework for Jailbreaking Multimodal LLMs with Multi-Image Inputs** — [arxiv_cr](https://arxiv.org/abs/2605.18915)
- **OEP: Poisoning Self-Evolving LLM Agents via Locally Correct but Non-Transferable Experiences** — [arxiv_cr](https://arxiv.org/abs/2605.18930)
- **Surviving the Unseen: Predictive Defense for Novel Multi-Turn Multimodal Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.18988)
- **Agent Security is a Systems Problem** — [arxiv_cr](https://arxiv.org/abs/2605.18991)
- **Be Kind, Rewrite: Benign Projections via Rewriting Defend Against LLM Data Poisoning Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.19147)
- **On the Geometric Limits of Transformer Defenses against Obfuscation Attacks: Latent Embedding Collapse & Performance Robustness Gap** — [arxiv_cr](https://arxiv.org/abs/2605.19159)
- **Token by Token, Compromised: Backdoor Vulnerabilities in Unified Autoregressive Models** — [arxiv_cr](https://arxiv.org/abs/2605.19227)
- **Detecting and Mitigating Backdoor Attacks in OTA-FL Systems: A Two-Stage Robust Aggregation Scheme** — [arxiv_cr](https://arxiv.org/abs/2605.19253)
- **MultiBallot: Verifiable and privacy-preserving E-Collecting in the Swiss setting** — [arxiv_cr](https://arxiv.org/abs/2605.19312)
- **Exploring and Developing a Pre-Model Safeguard with Draft Models** — [arxiv_cr](https://arxiv.org/abs/2605.19321)
- **Backdooring Masked Diffusion Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.19262)
- **The Privacy Subsidy in Glosten-Milgrom: Bid-Ask Spread and Welfare under Flip-Noise Direction Observation** — [arxiv_cr](https://arxiv.org/abs/2605.19742)
- **MSAVBench: Towards Comprehensive and Reliable Evaluation of Multi-Shot Audio-Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.20183v1)
- **When Critics Disagree: Adaptive Reward Poisoning Attacks in RIS-Aided Wireless Control System** — [arxiv_lg](https://arxiv.org/abs/2605.20037v1)
- **Detecting Fluent Optimization-Based Adversarial Prompts via Sequential Entropy Changes** — [arxiv_lg](https://arxiv.org/abs/2605.19966v1)
- **Auditing Privacy in Multi-Tenant RAG under Account Collusion** — [arxiv_lg](https://arxiv.org/abs/2605.19847v1)
- **Towards Fine-Grained Robustness: Attention-Guided Test-Time Prompt Tuning for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.19956v1)
- **A Framework for Evaluating Zero-Shot Image Generation in Concept-based Explainability** — [arxiv_cv](https://arxiv.org/abs/2605.19855v1)
- **Stitched Value Model for Diffusion Alignment** — [arxiv_cv](https://arxiv.org/abs/2605.19804v1)
- **Mechanisms of Object Localization in Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.19792v1)
- **Where Does Authorship Signal Emerge in Encoder-Based Language Models?** — [arxiv_cl](https://arxiv.org/abs/2605.19908v1)
- **Mega-ASR: Towards In-the-wild^2 Speech Recognition via Scaling up Real-world Acoustic Simulation** — [arxiv_cl](https://arxiv.org/abs/2605.19833v1)
- **Mathematical Reasoning in Large Language Models: Benchmarks, Architectures, Evaluation, and Open Challenges** — [arxiv_cl](https://arxiv.org/abs/2605.19723v1)
- **DarkLLM: Learning Language-Driven Adversarial Attacks with Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.18868)
- **Atoms of Thought: Universal EEG Representation Learning with Microstates** — [arxiv_lg](https://arxiv.org/abs/2605.20182v1)
- **Multi-axis Analysis of Image Manipulation Localization** — [arxiv_lg](https://arxiv.org/abs/2605.20174v1)
- **SAGE: Scalable Automatic Gating Ensemble for Confident Negative Harvesting in Fraud Detection** — [arxiv_lg](https://arxiv.org/abs/2605.20157v1)
- **Beyond Prediction Accuracy: Target-Space Recovery Profiles for Evaluating Model-Brain Alignment** — [arxiv_lg](https://arxiv.org/abs/2605.20127v1)
- **Beyond Isotropy in JEPAs: Hamiltonian Geometry and Symplectic Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.20107v1)
- **Optimal Representation Size: High-Dimensional Analysis of Pretraining and Linear Probing** — [arxiv_lg](https://arxiv.org/abs/2605.20105v1)
- **INSHAPE: Instance-Level Shapelets for Interpretable Time-Series Classification** — [arxiv_lg](https://arxiv.org/abs/2605.20088v1)
- **Towards Distillation Guarantees under Algorithmic Alignment for Combinatorial Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.20074v1)
- **Training Neural Networks with Optimal Double-Bayesian Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20009v1)
- **Learning with Foresight: Enhancing Neural Routing Policy via Multi-Node Lookahead Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.19975v1)
- **Your Neighbors Know: Leveraging Local Neighborhoods for Backdoor Detection in Decentralized Learning** — [arxiv_lg](https://arxiv.org/abs/2605.19969v1)
- **StruMPL: Multi-task Dense Regression under Disjoint Partial Supervision and MNAR Labels** — [arxiv_lg](https://arxiv.org/abs/2605.19931v1)
- **PixVerve: Advancing Native UHR Image Generation to 100MP with a Large-Scale High-Quality Dataset** — [arxiv_cv](https://arxiv.org/abs/2605.20147v1)
- **Spatially Prompted Visual Trajectory Prediction for Egocentric Manipulation** — [arxiv_cv](https://arxiv.org/abs/2605.20085v1)
- **Cardiac fat segmentation using computed tomography and an image-to-image conditional generative adversarial neural network** — [arxiv_cv](https://arxiv.org/abs/2605.20064v1)
- **RECIPE: Procedural Planning via Grounding in Instructional Video** — [arxiv_cv](https://arxiv.org/abs/2605.19976v1)
- **Feed-Forward Gaussian Splatting from Sparse Aerial Views** — [arxiv_cv](https://arxiv.org/abs/2605.19949v1)
- **GLUT: 3D Gaussian Lookup Table for Continuous Color Transformation** — [arxiv_cv](https://arxiv.org/abs/2605.19889v1)
- **Structural Energy Guidance for View-Consistent Text-to-3D Generation** — [arxiv_cv](https://arxiv.org/abs/2605.19876v1)
- **Passive Construction Site Safety Monitoring via Persona-Scaffolded Adversarial Chain-of-Thought VLM Verification** — [arxiv_cv](https://arxiv.org/abs/2605.19869v1)
- **When Preference Labels Fall Short: Aligning Diffusion Models from Real Data** — [arxiv_cv](https://arxiv.org/abs/2605.19839v1)
- **LaCoVL-FER: Landmark-Guided Contrastive Learning Network with Vision-Language Enhancement for Facial Expression Recognition** — [arxiv_cv](https://arxiv.org/abs/2605.19821v1)
- **MixRea: Benchmarking Explicit-Implicit Reasoning in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20128v1)
- **ThoughtTrace: Understanding User Thoughts in Real-World LLM Interactions** — [arxiv_cl](https://arxiv.org/abs/2605.20087v1)
- **CopT: Contrastive On-Policy Thinking with Continuous Spaces for General and Agentic Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.20075v1)
- **Text-to-SPARQL Generation with Reinforcement Learning: A GRPO-based Approach on DBLP** — [arxiv_cl](https://arxiv.org/abs/2605.20066v1)
- **Rewarding Beliefs, Not Actions: Consistency-Guided Credit Assignment for Long-Horizon Agents** — [arxiv_cl](https://arxiv.org/abs/2605.20061v1)
- **PEEK: Context Map as an Orientation Cache for Long-Context LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2605.19932v1)
- **Are Tools Always Beneficial? Learning to Invoke Tools Adaptively for Dual-Mode Multimodal LLM Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.19852v1)
- **CLIF: Concept-Level Influence Functions for Transparent Bottleneck Models** — [arxiv_cl](https://arxiv.org/abs/2605.19848v1)
- **FineBench: Benchmarking and Enhancing Vision-Language Models for Fine-grained Human Activity Understanding** — [arxiv_cl](https://arxiv.org/abs/2605.19846v1)
- **CADENet: Condition-Adaptive Asynchronous Dual-Stream Enhancement Network for Adverse Weather Perception in Autonomous Driving** — [arxiv_cl](https://arxiv.org/abs/2605.19837v1)
- **From Prompts to Pavement Through Time: Temporal Grounding in Agentic Scene-to-Plan Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.19824v1)
- **Synthesis and Evaluation of Long-term History-aware Medical Dialogue** — [arxiv_cl](https://arxiv.org/abs/2605.19766v1)
- **LLMEval-Logic: A Solver-Verified Chinese Benchmark for Logical Reasoning of LLMs with Adversarial Hardening** — [arxiv_cl](https://arxiv.org/abs/2605.19597v1)
- **GoLongRL: Capability-Oriented Long Context Reinforcement Learning with Multitask Alignment** — [arxiv_cl](https://arxiv.org/abs/2605.19577v1)
- **Library Drift: Diagnosing and Fixing a Silent Failure Mode in Self-Evolving LLM Skill Libraries** — [arxiv_cl](https://arxiv.org/abs/2605.19576v1)
- **m3BERT: A Modern, Multi-lingual, Matryoshka Bidirectional Encoder** — [arxiv_cl](https://arxiv.org/abs/2605.19568v1)
- **HaorFloodAlert: Deseasonalized ML Ensemble for 72-Hour Flood Prediction in Bangladesh Haor Wetlands** — [arxiv_lg](https://arxiv.org/abs/2605.20167v1)
- **Interpretable Computer Vision for Defect Detection in X-ray Tomography of Aerospace SiC/SiC Composites** — [arxiv_lg](https://arxiv.org/abs/2605.20159v1)
- **PiG-Avatar: Hierarchical Neural-Field-Guided Gaussian Avatars** — [arxiv_cv](https://arxiv.org/abs/2605.20185v1)
- **CaMo: Camera Motion Grounded Evaluation and Training for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.20165v1)
- **TIDE: Efficient and Lossless MoE Diffusion LLM Inference with I/O-aware Expert Offload** — [arxiv_cl](https://arxiv.org/abs/2605.20179v1)
- **When Does Model Collapse Occur in Structured Interactive Learning?** — [arxiv_lg](https://arxiv.org/abs/2605.20151v1)
- **Goal-Oriented Lower-Tail Calibration of Gaussian Processes for Bayesian Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.20145v1)
- **TideGS: Scalable Training of Over One Billion 3D Gaussian Splatting Primitives via Out-of-Core Optimization** — [arxiv_cv](https://arxiv.org/abs/2605.20150v1)
- **SetCon: Towards Open-Ended Referring Segmentation via Set-Level Concept Prediction** — [arxiv_cv](https://arxiv.org/abs/2605.20110v1)
- **MetaEarth-MM: Unified Multimodal Remote Sensing Image Generation with Scene-centered Joint Modeling** — [arxiv_cv](https://arxiv.org/abs/2605.20090v1)
- **Demis Hassabis said this might be the ‘foothills of the singularity.’ What?** — [theverge_ai](https://www.theverge.com/tech/934260/google-io-ai-singularity-demis-hassabis)
- **The future of Google is a search box that does everything** — [theverge_ai](https://www.theverge.com/tech/934217/google-search-box-does-everything-ai-io-2026)
- **Google’s AI future demands trust — and your personal data** — [theverge_ai](https://www.theverge.com/tech/934172/google-io-gemini-ai-trust-personal-data)
- **From teen hacker to Iron Dome researcher, this founder raised $28M to fight AI phishing** — [techcrunch_ai](https://techcrunch.com/2026/05/19/from-teen-hacker-to-iron-dome-researcher-this-founder-raised-28m-to-fight-ai-phishing/)
- **Gemini will use Volvo’s external cameras to interpret parking signs** — [theverge_ai](https://www.theverge.com/transportation/933556/google-io-gemini-volvo-ex60-camera-ai-parking)
- **The 13 biggest announcements at Google I/O 2026** — [theverge_ai](https://www.theverge.com/tech/933415/google-io-2026-biggest-announcements-ai-gemini)
- **Google wants to compete with Anthropic’s Mythos** — [theverge_ai](https://www.theverge.com/tech/933921/google-wants-to-compete-with-anthropics-mythos)
- **Elon Musk said Sam Altman ‘stole’ a non-profit — but the trial showed he had similar aims** — [techcrunch_ai](https://techcrunch.com/2026/05/19/elon-musk-said-sam-altman-stole-a-non-profit-but-the-trial-showed-he-had-similar-aims/)
- **Google takes a page out of Meta’s book, announces new audio-powered smart glasses at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-takes-a-page-out-of-metas-book-announces-new-audio-powered-smart-glasses-at-io-2026/)
- **Google’s Genie world model can now simulate real streets with Street View** — [techcrunch_ai](https://techcrunch.com/2026/05/19/googles-genie-world-model-can-now-simulate-real-streets-with-street-view/)
- **With Gemini 3.5 Flash, Google bets its next AI wave on agents, not chatbots** — [techcrunch_ai](https://techcrunch.com/2026/05/19/with-gemini-3-5-flash-google-bets-its-next-ai-wave-on-agents-not-chatbots/)
- **Introducing OpenAI for Singapore** — [openai](https://openai.com/index/introducing-openai-for-singapore)
- **Roundtables: Inside the Musk v. Altman Trial** — [mit_tech_review](https://www.technologyreview.com/2026/05/19/1137454/roundtables-inside-the-musk-v-altman-trial/)
- **Google can now vibe-code you an Android app** — [theverge_ai](https://www.theverge.com/tech/932364/google-ai-studio-native-android-apps-vibe-code-google-io-2026)
- **Would you let robots spend your money? Google is betting on it** — [theverge_ai](https://www.theverge.com/news/932927/google-io-agentic-ai-shopping-universal-cart)
- **Google Search is getting its biggest changes ever** — [theverge_ai](https://www.theverge.com/tech/932970/google-search-ai-update-io-2026)
- **Gmail is going to start talking to you** — [theverge_ai](https://www.theverge.com/tech/932973/google-gmail-live-ai-keep-docs-io-2026)
- **Google Search as you know it is over** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-search-as-you-know-it-is-over/)
- **Agentic app coding gets an upgrade with Google’s release of Android CLI** — [techcrunch_ai](https://techcrunch.com/2026/05/19/agentic-app-coding-gets-an-upgrade-with-googles-release-of-android-cli/)
- **Google’s AI Studio now lets anyone build Android apps in minutes** — [techcrunch_ai](https://techcrunch.com/2026/05/19/googles-ai-studio-now-lets-anyone-build-android-apps-in-minutes/)
- **Google launches Antigravity 2.0 with an updated desktop app and CLI tool at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-launches-antigravity-2-0-with-an-updated-desktop-app-and-cli-tool-at-io-2026/)
- **Google introduces Gemini Spark, a 24/7 agentic assistant with Gmail integration, at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-introduces-gemini-spark-a-24-7-agentic-assistant-with-gmail-integration/)
- **Google’s Gemini Omni turns images, audio, and text into video — and that’s just the start** — [techcrunch_ai](https://techcrunch.com/2026/05/19/googles-gemini-omni-turns-images-audio-and-text-into-video-and-thats-just-the-start/)
- **OpenAI co-founder Andrej Karpathy joins Anthropic’s pre-training team** — [techcrunch_ai](https://techcrunch.com/2026/05/19/openai-co-founder-andrej-karpathy-joins-anthropics-pre-training-team/)
- **I/O 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/developers-tools/google-io-2026-collection/)
- **How AI Mode is changing the way people search in the U.S.** — [google_ai](https://blog.google/products-and-platforms/products/search/ai-mode-us-insights/)
- **Understanding the modern cybercrime landscape** — [mit_tech_review](https://www.technologyreview.com/2026/05/19/1136925/understanding-the-modern-cybercrime-landscape/)
- **The Download: Musk v. Altman, smart glasses for warfare, and Google I/O** — [mit_tech_review](https://www.technologyreview.com/2026/05/19/1137505/the-download-musk-altman-trial-smart-glasses-warfare-google-i-o/)
- **Colossal Biosciences is growing chickens in a 3D-printed artificial eggshell** — [mit_tech_review](https://www.technologyreview.com/2026/05/19/1137471/colossal-biosciences-is-growing-chickens-in-a-3d-printed-container/)
- **Google just declared itself a contender in AI design at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/ai-design-tools-are-the-next-big-battleground-and-google-is-going-all-in-at-io-2026/)
- **You can now talk to your Gmail inbox, as seen at Google IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/you-can-now-talk-to-your-gmail-inbox-as-seen-at-google-io-2026/)
- **How to use Google’s new AI agents to go beyond your standard searches** — [techcrunch_ai](https://techcrunch.com/2026/05/19/how-to-use-googles-new-ai-agents-to-go-beyond-your-standard-searches/)
- **OpenAI is making it easier to check if an image was made by their models** — [techcrunch_ai](https://techcrunch.com/2026/05/19/openai-is-making-it-easier-to-check-if-an-image-was-made-by-their-models/)
- **Google’s new Universal Cart wants to follow your entire shopping journey across the internet** — [techcrunch_ai](https://techcrunch.com/2026/05/19/googles-new-universal-cart-wants-to-follow-your-entire-shopping-journey-across-the-internet/)
- **Google adds voice-based prompting to Docs and Keep** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-adds-voice-based-prompting-to-docs-and-keep/)
- **Google updates its Gemini app to take on ChatGPT and Claude at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-updates-its-gemini-app-to-take-on-chatgpt-and-claude-at-io-2026/)
- **I/O 2026: Welcome to the agentic Gemini era** — [google_ai](https://blog.google/innovation-and-ai/sundar-pichai-io-2026/)
- **Gemini 3.5: frontier intelligence with action** — [google_ai](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-5/)
- **A new era for AI Search** — [google_ai](https://blog.google/products-and-platforms/products/search/search-io-2026/)
- **Everything new in our Google AI subscriptions, fresh from I/O 2026** — [google_ai](https://blog.google/products-and-platforms/products/google-one/google-ai-subscriptions/)
- **Advancing content provenance for a safer, more transparent AI ecosystem** — [openai](https://openai.com/index/advancing-content-provenance)
- **New ways to create and get things done in Google Workspace** — [google_ai](https://blog.google/products-and-platforms/products/workspace/workspace-updates/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **kevintsai1202/teaching-site-skills** — [github](https://github.com/kevintsai1202/teaching-site-skills)
- **richard-kim-79/archora-skills** — [github](https://github.com/richard-kim-79/archora-skills)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **mdowis/anansi** — [github](https://github.com/mdowis/anansi)
- **zimingttkx/QuantumFlow** — [github](https://github.com/zimingttkx/QuantumFlow)
- **ahammadmejbah/Awesome-Datasets-Hub** — [github](https://github.com/ahammadmejbah/Awesome-Datasets-Hub)
- **exploitbench/exploitbench** — [github](https://github.com/exploitbench/exploitbench)
- **Siva-Chidambaram12/kalshi-trading-bot** — [github](https://github.com/Siva-Chidambaram12/kalshi-trading-bot)
- **dex-original/okx-agent-trade-kit** — [github](https://github.com/dex-original/okx-agent-trade-kit)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **yetone/native-feel-skill** — [github](https://github.com/yetone/native-feel-skill)
- **Google just redesigned the search box for the first time in 25 years — here’s why it matters more than you think.** — [venturebeat_ai](https://venturebeat.com/technology/google-just-redesigned-the-search-box-for-the-first-time-in-25-years-heres-why-it-matters-more-than-you-think)
- **xuanlinAI/overmind** — [github](https://github.com/xuanlinAI/overmind)
- **hunhee98/pluck** — [github](https://github.com/hunhee98/pluck)
- **ForgeAILab/forge** — [github](https://github.com/ForgeAILab/forge)
- **jigripokri/POHA** — [github](https://github.com/jigripokri/POHA)
- **CHB-learner/PaperPilot** — [github](https://github.com/CHB-learner/PaperPilot)
- **DaoyuanLi2816/can-i-finetune-this** — [github](https://github.com/DaoyuanLi2816/can-i-finetune-this)
- **kgmkm/novel2hermes_jp** — [github](https://github.com/kgmkm/novel2hermes_jp)
- **Bridging the Disciplinary Gap in Explainable AI: From Abstract Desiderata to Concrete Tasks** — [arxiv_cy](https://arxiv.org/abs/2605.20081)
- **Addressing the Reality Gap: A Three-Tension Framework for Agentic AI Adoption** — [arxiv_cy](https://arxiv.org/abs/2604.27245)
- **苏姿丰上海开讲：AI正在重新定义计算的每一层** — [qbitai](https://www.qbitai.com/2026/05/420531.html)
- **完成“由铁到钢”的生态蜕变 刘军携联想全场景AI终端点亮智能未来** — [qbitai](https://www.qbitai.com/2026/05/420561.html)
- **抢先李飞飞！世界模型能多人联机玩FPS游戏了** — [qbitai](https://www.qbitai.com/2026/05/420083.html)
- **国产GPU开始造世界！国内首个全栈具身智能仿真平台来了** — [qbitai](https://www.qbitai.com/2026/05/420084.html)
- **Cursor新模型，你怎么还在套Kimi？马斯克你怎么还吆喝上了？？** — [qbitai](https://www.qbitai.com/2026/05/419990.html)
- **Going PLACES: Participatory Localized Red Teaming for Text-to-Image Safety in the Global South** — [arxiv_cy](https://arxiv.org/abs/2605.19190)
- **GRASP: Deterministic argument ranking in interaction graphs** — [arxiv_cy](https://arxiv.org/abs/2605.19141)
- **Rethinking the A in STEAM: Insights from and for AI Literacy Education** — [arxiv_cy](https://arxiv.org/abs/2405.18179)
- **Quantifying the Climate Risk of Generative AI: Region-Aware Carbon Accounting with G-TRACE and the AI Sustainability Pyramid** — [arxiv_cy](https://arxiv.org/abs/2511.04776)
- **Designing escalation criteria for international AI incident response: criteria, triggers, and thresholds** — [arxiv_cy](https://arxiv.org/abs/2604.23183)
- **CAPC-CG: A Large-Scale, Expert-Directed LLM-Annotated Corpus of Adaptive Policy Communication in China** — [arxiv_cy](https://arxiv.org/abs/2510.08986)
- **Technologies and Security Challenges in Metaverse** — [arxiv_cy](https://arxiv.org/abs/2510.09621)
- **Beyond Nutrition Labels: How Analogical Reasoning Shapes Synthetic Media Disclosure Design** — [arxiv_cy](https://arxiv.org/abs/2605.19045)
- **Stop Drawing Scientific Claims from LLM Social Simulations Without Robustness Audits** — [arxiv_cy](https://arxiv.org/abs/2605.18890)
- **The Accessibility Capability Boundary: Operational Limits and Expansion Potential of AI-Generated Browser-Native Accessibility Systems** — [arxiv_cy](https://arxiv.org/abs/2605.19638)
- **ALSO: Adversarial Online Strategy Optimization for Social Agents** — [arxiv_cy](https://arxiv.org/abs/2605.15768)
- **Smooth Piecewise Cutting for Neural Operator to Handle Discontinuities and Sharp Transitions** — [arxiv_ml](https://arxiv.org/abs/2605.19823v1)
- **Probabilistic Multivariate Time Series Forecasting with Diffusion Copulas** — [arxiv_ml](https://arxiv.org/abs/2605.19685v1)
- **Increasing Missingness to Reduce Bias: Richardson-SGD with Missing Data** — [arxiv_ml](https://arxiv.org/abs/2605.19641v1)
- **Online Market Making and the Value of Observing the Order Book** — [arxiv_ml](https://arxiv.org/abs/2605.19584v1)
- **Automated Grading of Handwritten Mathematics Using Vision-Capable LLMs** — [arxiv_cy](https://arxiv.org/abs/2605.19043)
- **Can LLMs Emulate Human Belief Dynamics?** — [arxiv_cy](https://arxiv.org/abs/2605.18781)
- **A City-Scale Dataset of Traffic Flows, Travel Times, and Urban Context** — [arxiv_cy](https://arxiv.org/abs/2605.18782)
- **How Far Are We From True Auto-Research?** — [arxiv_cy](https://arxiv.org/abs/2605.19156)
- **Are Rationales Necessary and Sufficient? Tuning LLMs for Explainable Misinformation Detection** — [arxiv_cy](https://arxiv.org/abs/2605.19285)
- **Journeys of Parents with LGBTQ+ Children: How Trauma and Healing Reshape Identity and (Mis)Informating Practices** — [arxiv_cy](https://arxiv.org/abs/2605.20024)
- **Improved visual-information-driven model for crowd simulation and its modular application** — [arxiv_cy](https://arxiv.org/abs/2504.03758)
- **Semi-Parametric Bayesian Additive Regression Trees for Risk Prediction with High-Dimensional Epigenetic Signatures and Low-Dimensional Covariates** — [arxiv_ml](https://arxiv.org/abs/2605.20143v1)
- **FLUXtrapolation: A benchmark on extrapolating ecosystem fluxes** — [arxiv_ml](https://arxiv.org/abs/2605.19812v1)
- **Latent Laplace Diffusion for Irregular Multivariate Time Series** — [arxiv_ml](https://arxiv.org/abs/2605.19805v1)
- **Fast Spawn\&Prune (FS\&P): Global convergence of stochastic conic particle gradient descent via birth/death process** — [arxiv_ml](https://arxiv.org/abs/2605.19784v1)
- **Minimax Optimal Variance-Aware Regret Bounds for Multinomial Logistic MDPs** — [arxiv_ml](https://arxiv.org/abs/2605.19768v1)
- **CogScale: Scalable Benchmark for Sequence Processing** — [arxiv_ml](https://arxiv.org/abs/2605.19758v1)
- **Gaussian Approximation and Multiplier Bootstrap for Federated Linear Stochastic Approximation** — [arxiv_ml](https://arxiv.org/abs/2605.19629v1)
- **MiMuon: Mixed Muon Optimizer with Improved Generalization for Large Models** — [arxiv_ml](https://arxiv.org/abs/2605.19619v1)
- **Posterior Contraction of Lévy Adaptive B-spline Regression in Besov Spaces** — [arxiv_ml](https://arxiv.org/abs/2605.19610v1)
- **Density-Ratio Losses for Post-Hoc Learning to Defer** — [arxiv_ml](https://arxiv.org/abs/2605.19557v1)
- **8点1氪丨谷歌推出Gemini 3.5系列模型；DeepSeek回应用户“对话泄露”疑虑；全国存款十强城市出炉** — [36kr](https://36kr.com/p/3816885092910212?f=rss)
- **2026福布斯中国人工智能科技企业TOP 50发布，中关村科金入选** — [36kr](https://36kr.com/newsflashes/3817185914520710?f=rss)
- **圆周率智能发布 iMLite AI（悟境）端侧实时决策引擎** — [36kr](https://36kr.com/newsflashes/3817118508713092?f=rss)
- **地瓜机器人与千寻智能达成战略合作** — [36kr](https://36kr.com/newsflashes/3817109218575489?f=rss)
- **宜春就进一步加强锂资源矿山监督管理征求意见** — [36kr](https://36kr.com/newsflashes/3817121466680200?f=rss)
- **Seedance 2.1即将推出？接近字节跳动人士：不属实** — [36kr](https://36kr.com/newsflashes/3817085893788546?f=rss)
- **“贝塔无限”连续完成种子轮、种子+轮数亿元融资** — [36kr](https://36kr.com/newsflashes/3817084193866889?f=rss)
- **平头哥AI芯片真武M890首次亮相，性能提升至3倍** — [36kr](https://36kr.com/newsflashes/3817080294999168?f=rss)
- **长鑫科技更新招股书，碧桂园错失300亿** — [36kr](https://36kr.com/p/3817039204139908?f=rss)
- **理想新L9上市72小时：老车主复购占大头，仍需从“家庭”破圈** — [36kr](https://36kr.com/p/3709756082466949?f=rss)
- **做出百万台割草机器人后，未岚大陆CEO决定让自己变得“不重要”｜硬氪专访** — [36kr](https://36kr.com/p/3814411349581316?f=rss)
- **要做数字劳动力生产工厂，「未来式智能」完成Pre-A轮融资** — [36kr](https://36kr.com/p/3816909945029760?f=rss)
- **早期项目 | Chance AI获美图等数百万美元投资，用户数已达20万** — [36kr](https://36kr.com/p/3816947890471812?f=rss)
- **当“躺平”、Gap被歧视，我们该如何度过奥德赛时期？ | 职场极端气候 ②** — [36kr](https://36kr.com/p/3816045694098952?f=rss)
- **氪星晚报 ｜SpaceX即将成为马斯克旗下第二家上市公司；京东、洋河集团等在宿迁成立新动能股权投资基金，出资额10亿** — [36kr](https://36kr.com/p/3816109626138119?f=rss)
- **裸辞九个月，降薪跳槽，一个80后营销人如何“上岸甲方”？｜百万年薪系列013** — [36kr](https://36kr.com/p/3816036564147718?f=rss)
- **影石：重新定义性价比** — [36kr](https://36kr.com/p/3815841756028425?f=rss)
- **新加坡加码人工智能布局，英伟达将落地本地研发中心** — [36kr](https://36kr.com/newsflashes/3817119265457027?f=rss)
- **飞猪推出酒店商家智能助理** — [36kr](https://36kr.com/newsflashes/3817110991799169?f=rss)
- **平头哥真武系列GPU已累计出货超56万片** — [36kr](https://36kr.com/newsflashes/3817111570482304?f=rss)