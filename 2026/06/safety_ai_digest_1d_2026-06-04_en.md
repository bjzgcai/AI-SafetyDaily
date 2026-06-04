# AI Daily Digest [AI 安全] - 2026-06-04


# Daily Thematic Digest: AI Safety & Agent Governance
**Date:** 2026-06-04  
**Theme:** Agent Security, Runtime Safety, Alignment, and Evaluation

## Highlights

Three critical developments define the current landscape of agentic safety. First, the concept of **Consent Integrity** has emerged as a foundational requirement for human-in-the-loop systems, addressing the "Lies-in-the-Loop" vulnerability where compromised agents can forge approval summaries to execute unauthorized actions. Second, the community is shifting from accuracy-centric metrics toward a **Science of Agent Reliability**, emphasizing operational consistency, perturbation resistance, and bounded error severity over simple task completion rates. Third, infrastructure-level security is maturing with the introduction of **Pod-Level Remote Attestation** for confidential workloads, moving beyond VM-level guarantees to verify container identities within shared environments, directly mitigating supply chain risks in multi-tenant agent deployments.

## Agent Security & Governance

The most pressing challenge in contemporary agentic systems is not merely capability, but the verifiability of execution and the governance of tool use. Recent work emphasizes that final-answer accuracy is insufficient for auditability; instead, systems require **Evidence Tracing and Execution Provenance in LLM Agents** to model how retrieved evidence supported each claim and where execution failures originated. This need for transparency drives architectural shifts such as **Provably Auditable and Safe LLM Agents from Human-Authored Ontologies**, which utilizes typed lambda calculus to guarantee semantic correctness in append-only ledgers for domains like healthcare billing. While formal methods offer strong guarantees, they face adoption barriers compared to more flexible permission frameworks. **SkillGuard: A Permission Framework for Agent Skills** addresses the gap between declared intent and runtime behavior, arguing that static inspection of skill files is inadequate when skills can inject context dynamically. This contrasts with approaches like **AIP: A Graph Representation for Learning and Governing Agent Skills**, which models skills as directed execution graphs to reduce reliance on fragile prose instructions.

Governance extends beyond individual agent permissions to the broader ecosystem of interactions. The **Cross-Vendor Sola ISPM Benchmark** highlights that identity security posture management is now fundamentally a cross-vendor challenge, requiring agents to reason across fragmented boundaries that were never designed to interoperate. Similarly, the **Model Context Protocol (MCP)** faces scrutiny through **Description-Code Inconsistency in Real-world MCP Servers**, revealing that tool descriptions often fail to faithfully reflect underlying implementations, creating implicit trust assumptions that attackers can exploit. These inconsistencies feed into larger systemic risks, particularly regarding **Consent Integrity for Black-Box LLM Agents**. Current coding agents gate consequential actions behind human approval dialogs narrated by the agent itself, allowing for summary forgery. Researchers propose importing trusted-path properties to ensure the action shown to the human matches what executes, effectively closing the loop on authorization.

In offensive security contexts, the focus is shifting from proficiency to refusal boundaries. **A New Framework for Cybersecurity Refusals in AI Agents** establishes principled criteria for when agents should refuse harmful requests, noting that existing benchmarks neglect this critical safety dimension. This complements **FORGE: Multi-Agent Graduated Exploitation and Detection Engineering**, which bridges silos between proof-of-concept generation and detection rule engineering through graduated exploitation depth. Meanwhile, economic mechanisms are being explored to self-regulate agent populations. **Economy of Minds: Emerging Multi-Agent Intelligence with Economic Interactions** proposes decentralized coordination via auctions and payments, inducing credit assignment without global orchestration. However, such economic incentives introduce new vectors for manipulation, necessitating robust auditing tools like **Multi Agent for Business Automation** platforms that coordinate specialized agents through shared memory and HITL approval gates.

## Tool/Prompt Injection & Runtime Defenses

Runtime safety requires defenses that operate at the level of inference and memory management, not just input filtering. **Adaptive Latent Agentic Reasoning** introduces a dual-mode framework using compact latent reasoning for routine turns to mitigate the inefficiency of verbose textual reasoning in multi-turn trajectories. This efficiency gain is critical given the threat of **Inference Cost Attacks for Retrieval-Augmented Large Language Models**, where poisoning external knowledge sources exposes high operational costs to exploitation. Unlike previous attacks relying on direct prompt manipulation, these threats leverage the retrieval pipeline itself, demanding defenses that validate external data integrity alongside internal logic.

Memory governance remains a central vulnerability. **PhotoCraft: Agentic Reasoning with Hierarchical Self-Evolving Memory** equips multimodal models with working, episodic, and semantic memory to prevent execution drift, contrasting with stateless reactive agents. However, memory persistence raises privacy concerns addressed by **MemoGen**, which investigates whether text-to-image systems can preserve past successes without compromising user data. Local-first solutions like **Mnemo** and **Memory OS** attempt to decouple persistent knowledge graphs from cloud dependencies, though they require rigorous access control. **Memory Retrieval for Changing Preferences** further refines this by formulating personalized retrieval as identifying historical turns that provide evidence about latent preferences, acknowledging that user intent evolves over time.

API interactions also require structural improvements to handle errors safely. **Self-Reflective APIs** demonstrate that structured machine-readable recovery feedback lifts task-completion rates significantly over plain-English diagnoses, reducing the cognitive load on agents attempting to repair validation errors. This aligns with **Strabo: Declarative Specification and Implementation of Agentic Interaction Protocols**, which models protocols like the Universal Commerce Protocol to standardize interactions. Furthermore, **Kubernetes Pod-Level Remote Attestation for Confidential Workloads** enables cryptographic proof that user data is processed in untampered environments, solving the resource overhead issues of traditional Confidential Containers by allowing multiple pods to share a single secure enclave.

## Adversarial Attacks & Robustness

Adversarial robustness evaluation is evolving from single-turn prompts to complex multi-turn trajectories. **MultiTurnPSB: Evaluating Multi-Turn Jailbreak Attacks and Classifier-Based Defenses for Medical AI Safety** reveals that unsafe responses rise from 35% to nearly 80% by Turn 4 under live adversarial attacks, indicating that static guardrails fail against iterative persuasion. This finding contradicts the assumption that refusal filters are sufficient, suggesting that defense attribution is necessary. **Which Defense Closes Which Threat?** measures coverage attribution across defense families, showing that aggregate numbers hide which specific family closes which threat, urging a move toward granular benchmarking.

Reward hacking remains a persistent issue in reinforcement learning. **Reproducing, Analyzing, and Detecting Reward Hacking in Rubric-Based Reinforcement Learning** introduces CHERRL, a controllable environment for injecting known biases into LLM-as-a-Judge systems to stabilize reproduction of hacking behaviors. This is crucial because rubric-based RL often leads to policies that exploit latent judge biases. Similarly, **BiasGRPO: Stabilizing Bias Mitigation in High-Variance Reward Landscapes** proposes Group Relative Policy Optimization to handle the subjective nature of bias mitigation, contrasting with DPO and PPO which suffer from exploration limits or instability.

Benchmark validity is also under scrutiny. **The Geometry of LLM-as-Judge** finds that judges agree strongly with one another but weakly with humans, questioning the validity of consensus as a proxy for alignment. **NoRA: Evaluating Grounded Reasonableness in Visual First-person Normative Action Reasoning** argues that existing normative assessments are insufficient because they reduce judgment to fixed candidate actions rather than generating reasonable actions from scratch. Additionally, **AutoLab** introduces a benchmark for ultra long-horizon closed-loop optimization, addressing the gap where existing evaluations fail to capture sustained iterative improvement challenges.

## Alignment & Interpretability

Alignment research is increasingly focusing on the structural properties of reasoning and the geometry of decision spaces. **Tree-Based Formalization of Multi-Agent Complementarity in Human-AI Interactions** provides a mathematical framework for modeling how agent predictions compose into workflow-sensitive protocols, moving beyond simple performance comparisons. **Active Inference** theory is being revisited to unify goal-directed and information-seeking behavior, proving that Expected Free Energy minimization can be rewritten to make epistemic corrections transparent. This theoretical grounding supports **Learning While Acting: A Skill-Enhanced Test-Time Co-Evolution Framework**, which designs verifier-guided skills for online lifelong learning agents to continuously internalize test-time feedback.

Interpretability efforts are also targeting hidden states. **Linear Probes Detect Task Format, Not Reasoning Mode in Language Model Hidden States** tests the claim that models learn distinct representations for different reasoning types, finding that separation is entirely due to task format rather than reasoning mode. Conversely, **Do Value Vectors in Deep Layers Need Context from the Residual Stream?** suggests that deeper layers perform better with context-free value vectors to preserve original token information. These findings inform **NeuroArmor: Safe-Variant-Guided Representation Consistency**, a white-box runtime defense using prompt-specific safe variants to balance safety and helpfulness against jailbreaks.

## Safety Benchmarks & Incident Response

The industry is responding to the complexity of agent deployment with specialized monitoring and response tools. **Coralogix raises $200M on bet that someone needs to watch the AI agents**, signaling market demand for infrastructure firms to monitor behavior and troubleshoot failures. This aligns with **Towards a Science of AI Agent Reliability**, which argues that compressing agent behavior into a single success metric obscures critical operational flaws like inconsistency and unbounded error severity. **Patcher: Post-Hoc Patching of Backdoored Large Language Models** offers a defense framework that repairs backdoored models using only a single reported failure case, addressing the impracticality of comprehensive attack information requirements.

In the realm of data and model provenance, **Data Attribution in Large Language Models via Bidirectional Gradient Optimization** expands upon inverse formulations to trace training data influence, while **STRIDE: Training Data Attribution via Sparse Recovery** proposes shifting from parameter space estimation to subset perturbations. These tools support **Replicability is the New Copyleft**, defining AGI-oriented reproducible builds to ensure source code and object code stand in auditable relationships. Finally, **OpenAI public policy agenda** and **A blueprint for democratic governance of frontier AI** outline federal frameworks for safety and resilience, reflecting a shift toward institutionalized governance structures.

## Looking Forward

Several unresolved theoretical questions await validation. First, the relationship between **dynamic risk** and **static governance** remains unclear; as agents adapt their own strategies (as seen in **LifeSkill**), how do we maintain invariant safety properties without stifling autonomy? Second, the **geometry of consent** requires formalization: can we mathematically prove that a human-approved summary is indistinguishable from the executed action in all black-box scenarios? Third, the **long-horizon reliability** of agents operating in non-stationary environments demands new metrics beyond accuracy, potentially integrating concepts from **Interval Regret** in online learning to bound cumulative error over extended trajectories. Finally, the integration of **economic incentives** with safety constraints, as proposed in **Economy of Minds**, poses a fundamental question: can decentralized markets self-correct malicious behavior, or does this necessitate centralized oversight mechanisms that contradict the very architecture of agentic autonomy?

---


## References

- **From Agent Traces to Trust: Evidence Tracing and Execution Provenance in LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2606.04990v1)
- **Adaptive Latent Agentic Reasoning** — [arxiv_cl](https://arxiv.org/abs/2606.02871)
- **Inference Cost Attacks for Retrieval-Augmented Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2606.02643)
- **Provably Auditable and Safe LLM Agents from Human-Authored Ontologies** — [arxiv_ai](https://arxiv.org/abs/2606.04903v1)
- **Archi: Agentic Operations at the CMS Experiment** — [arxiv_ai](https://arxiv.org/abs/2606.04755v1)
- **Economy of Minds: Emerging Multi-Agent Intelligence with Economic Interactions** — [arxiv_cl](https://arxiv.org/abs/2606.02859)
- **PhotoCraft: Agentic Reasoning with Hierarchical Self-Evolving Memory for Deep Image Search** — [arxiv_cl](https://arxiv.org/abs/2606.03099)
- **Cross-Vendor Sola ISPM Benchmark: Evaluating Agentic AI for Federated Identity Security Reasoning** — [arxiv_cr](https://arxiv.org/abs/2606.02674)
- **MemoGen: Can Past Experience Improve Future Text-to-Image Generation?** — [arxiv_cv](https://arxiv.org/abs/2606.03243)
- **Towards Efficient and Evidence-grounded Mobility Prediction with LLM-Driven Agent** — [arxiv_ai](https://arxiv.org/abs/2606.05130v1)
- **A New Framework for Cybersecurity Refusals in AI Agents** — [arxiv_cr](https://arxiv.org/abs/2606.02644)
- **SkillGuard: A Permission Framework for Agent Skills** — [arxiv_cr](https://arxiv.org/abs/2606.03024)
- **From Prompt to Process: a Process Taxonomy and Comparative Assessment of Frameworks Supporting AI Software Development Agents** — [arxiv_ai](https://arxiv.org/abs/2606.04967v1)
- **Learning While Acting: A Skill-Enhanced Test-Time Co-Evolution Framework for Online Lifelong Learning Agents** — [arxiv_ai](https://arxiv.org/abs/2606.04815v1)
- **Tree-Based Formalization of Multi-Agent Complementarity in Human-AI Interactions** — [arxiv_ai](https://arxiv.org/abs/2606.04779v1)
- **A Locally Deployed RAG-Based Academic Advising System for Course Selection** — [arxiv_cl](https://arxiv.org/abs/2606.02983)
- **MemTrain: Self-Supervised Context Memory Training** — [arxiv_cl](https://arxiv.org/abs/2606.03197)
- **FORGE: Multi-Agent Graduated Exploitation and Detection Engineering** — [arxiv_cr](https://arxiv.org/abs/2606.03453)
- **MUSE: A Unified Agentic Harness for MLLMs** — [arxiv_cv](https://arxiv.org/abs/2606.03005)
- **Be Fair! Can Machine Learning Engineering Agents Adhere to Fairness Constraints?** — [arxiv_lg](https://arxiv.org/abs/2606.04971v1)
- **R-APS: Compositional Reasoning and In-Context Meta-Learning for Constrained Design via Reflective Adversarial Pareto Search** — [arxiv_ai](https://arxiv.org/abs/2606.04823v1)
- **Which Defense Closes Which Threat? Attributing OWASP-LLM-Top-10 Coverage and Its Brittleness Under Paraphrasing** — [arxiv_cr](https://arxiv.org/abs/2606.02822)
- **ImageAuditor: Membership Inference Attack against Image-based Retrieval-Augmented Generation** — [arxiv_cr](https://arxiv.org/abs/2606.03354)
- **Self-Reflective APIs: Structure Beats Verbosity for AI Agent Recovery** — [arxiv_ai](https://arxiv.org/abs/2606.05037v1)
- **Enhancing the MADDPG Algorithm for Multi-Agent Learning via Action Inference and Importance Sampling** — [arxiv_lg](https://arxiv.org/abs/2606.05021v1)
- **Scenario Generation for Risk-Aware Reinforcement Learning with Probably Approximately Safe Guarantees** — [arxiv_ai](https://arxiv.org/abs/2606.04812v1)
- **NoRA: Evaluating Grounded Reasonableness in Visual First-person Normative Action Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.04806v1)
- **AIP: A Graph Representation for Learning and Governing Agent Skills** — [arxiv_ai](https://arxiv.org/abs/2606.04781v1)
- **ARBOR: Online Process Rewards via a Reusable Rubric Buffer for Search Agents** — [arxiv_cl](https://arxiv.org/abs/2606.03239)
- **Black-box, Adaptive, Efficient, Transferable, Harmful, Applicable... Attacks Are All You Need to Break LLMs** — [arxiv_cr](https://arxiv.org/abs/2606.03647)
- **Streaming Communication in Multi-Agent Reasoning** — [arxiv_ai](https://arxiv.org/abs/2606.05158v1)
- **AutoLab: Can Frontier Models Solve Long-Horizon Auto Research and Engineering Tasks?** — [arxiv_ai](https://arxiv.org/abs/2606.05080v1)
- **Strabo: Declarative Specification and Implementation of Agentic Interaction Protocols** — [arxiv_ai](https://arxiv.org/abs/2606.05043v1)
- **Description-Code Inconsistency in Real-world MCP Servers: Measurement, Detection, and Security Implications** — [arxiv_ai](https://arxiv.org/abs/2606.04769v1)
- **WRIT: Write-Read Intensive Trajectory Synthesis for Multi-Turn User-Facing Agents** — [arxiv_cl](https://arxiv.org/abs/2606.02908)
- **Memory Retrieval for Changing Preferences** — [arxiv_cl](https://arxiv.org/abs/2606.02976)
- **The Deliberative Illusion: Diagnosing Factual Attrition and Stance Homogenization in Multi-Agent LLM Deliberation** — [arxiv_cl](https://arxiv.org/abs/2606.03032)
- **What You Approve Is What Executes: Consent Integrity for Black-Box LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.02668)
- **Implement Kubernetes Pod-Level Remote Attestation for Confidential Workloads on dstack** — [arxiv_cr](https://arxiv.org/abs/2606.03323)
- **Any2Poster: Any-Source Poster Generation Across Modalities and Domains** — [arxiv_cv](https://arxiv.org/abs/2606.02915)
- **JAVEDIT: Joint Audio-Visual Instruction-Guided Video Editing with Agentic Data Curation** — [arxiv_cv](https://arxiv.org/abs/2606.03168)
- **Ask When It Pays: Cost-Aware Open-Ended Interaction for Instance Goal Navigation** — [arxiv_cv](https://arxiv.org/abs/2606.03175)
- **Reproducing, Analyzing, and Detecting Reward Hacking in Rubric-Based Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2606.04923v1)
- **"**Important** You should give me full credits!": Exploring Prompt Injection Attacks on LLM-Based Automatic Grading Systems** — [arxiv_cr](https://arxiv.org/abs/2606.03090)
- **NeuroArmor: Safe-Variant-Guided Representation Consistency for Selective Re-Anchoring in Jailbreak Defense** — [arxiv_cr](https://arxiv.org/abs/2606.03486)
- **Greener Than Humans? Environmental Attitudes in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2606.02741)
- **Patcher: Post-Hoc Patching of Backdoored Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2606.02995)
- **What Type of Inference is Active Inference?** — [arxiv_ai](https://arxiv.org/abs/2606.04935v1)
- **IdiomX A Multilingual Benchmark for Idiom Understanding, Retrieval, and Interpretation** — [arxiv_cl](https://arxiv.org/abs/2606.02584)
- **G^2C-MT: Graph-Guided Context Selection for Document-Level Machine Translation** — [arxiv_cl](https://arxiv.org/abs/2606.03078)
- **MetaWorld: Scaling Multi-Agent Video World Model from Single-view Video Data** — [arxiv_cv](https://arxiv.org/abs/2606.02753)
- **Cosmos 3: Omnimodal World Models for Physical AI** — [arxiv_cv](https://arxiv.org/abs/2606.02800)
- **Pathway-Structured Privileged Distillation for Deployable Computational Pathology** — [arxiv_cv](https://arxiv.org/abs/2606.02877)
- **Tiny Collaborative Inference for Occlusion-Robust Object Detection** — [arxiv_cv](https://arxiv.org/abs/2606.02894)
- **TGV-KV: Text-Grounded KV Eviction for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.03075)
- **NVIDIA OmniDreams: Real-Time Generative World Model for Closed-Loop Autonomous Vehicle Simulation** — [arxiv_cv](https://arxiv.org/abs/2606.03159)
- **BiasGRPO: Stabilizing Bias Mitigation in High-Variance Reward Landscapes via Group-Relative Policy Optimization** — [arxiv_ai](https://arxiv.org/abs/2606.04807v1)
- **MultiTurnPSB: Evaluating Multi-Turn Jailbreak Attacks an dClassifier-Based Defenses for Medical AI Safety** — [arxiv_cr](https://arxiv.org/abs/2606.02630)
- **Follow-Your-Preference++: Rethinking Preference Alignment for Image Inpainting** — [arxiv_cv](https://arxiv.org/abs/2606.03216)
- **Knowledge Index of Noah's Ark** — [arxiv_ai](https://arxiv.org/abs/2606.05104v1)
- **AlphaQ: Calibration-Free Bit Allocation for Mixture-of-Experts Quantization** — [arxiv_lg](https://arxiv.org/abs/2606.04980v1)
- **Do Value Vectors in Deep Layers Need Context from the Residual Stream?** — [arxiv_cl](https://arxiv.org/abs/2606.02780)
- **Chatbots Output Meaningful (but Problematic) Language** — [arxiv_cl](https://arxiv.org/abs/2606.02973)
- **Structures Facilitate Retrieve, Rerank, and Generate** — [arxiv_cl](https://arxiv.org/abs/2606.03247)
- **Bastet: A Fine-Grained Expert-Labeled Dataset for DeFi Smart Contract Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2606.03387)
- **Don't Trust Us: A privacy-by-design android malware detection pipeline** — [arxiv_cr](https://arxiv.org/abs/2606.03714)
- **AI Agents Enable Adaptive Computer Worms** — [arxiv_cr](https://arxiv.org/abs/2606.03811)
- **Plan2Map: A Multimodal Benchmark for Document-Grounded Geospatial Boundary Reconstruction from Planning Records** — [arxiv_cv](https://arxiv.org/abs/2606.02747)
- **GeoDrive-Bench: Benchmarking Region-Specific Multimodal Reasoning in Autonomous Driving** — [arxiv_cv](https://arxiv.org/abs/2606.02774)
- **Automated Report-Derived Oncology VQA Benchmark for Evaluating Vision-Language Models on 3D Medical Imaging** — [arxiv_cv](https://arxiv.org/abs/2606.02809)
- **Towards Compact Autonomous Driving Perception with Balanced Learning and Multi-sensor Fusion** — [arxiv_cv](https://arxiv.org/abs/2606.02979)
- **Reinforcement Learning from Cross-domain Videos with Video Prediction Model** — [arxiv_cv](https://arxiv.org/abs/2606.03201)
- **VistaHop: Benchmarking Multi-hop Visual Reasoning for Visual DeepSearch** — [arxiv_cv](https://arxiv.org/abs/2606.03273)
- **STaR-Quant: State-Time Consistent Post-Training Quantization for Diffusion Large Language Models** — [arxiv_lg](https://arxiv.org/abs/2606.04945v1)
- **FoeGlass: Simple In-Context Learning Is Enough for Red Teaming Audio Deepfake Detectors** — [arxiv_lg](https://arxiv.org/abs/2606.05101v1)
- **Linear Probes Detect Task Format, Not Reasoning Mode in Language Model Hidden States** — [arxiv_cl](https://arxiv.org/abs/2606.02907)
- **The Geometry of LLM-as-Judge: Why Inter-LLM Consensus Is Not Human Alignment** — [arxiv_cl](https://arxiv.org/abs/2606.03043)
- **SenseJudge: Human-Centric Preference-Driven Judgment Framework** — [arxiv_cl](https://arxiv.org/abs/2606.03189)
- **On Improving Robustness of Deepfake Image Detectors** — [arxiv_cr](https://arxiv.org/abs/2606.02797)
- **Decoupled Smart Contract Audits: Lightweight LLM Framework via Distillation and Aggregation** — [arxiv_cr](https://arxiv.org/abs/2606.03128)
- **PsychoPass: Geometric Profiling of Multi-Turn Adversarial LLM Conversations** — [arxiv_cr](https://arxiv.org/abs/2606.03136)
- **ATLAS: A Large-Scale Evaluation Benchmark for Adversarial LiDAR Perception** — [arxiv_cv](https://arxiv.org/abs/2606.02924)
- **FreeStreamGS: Online Feed-forward 3D Gaussian Splatting from Unposed Streaming Inputs** — [arxiv_cv](https://arxiv.org/abs/2606.03254)
- **Data Attribution in Large Language Models via Bidirectional Gradient Optimization** — [arxiv_lg](https://arxiv.org/abs/2606.04928v1)
- **MusaCoder: Native GPU Kernel Generation with Full-Stack Training on Moore Threads GPU** — [arxiv_lg](https://arxiv.org/abs/2606.04847v1)
- **An Open-Source Two-Stage Computer Vision Pipeline for Fine-Grained Vehicle Classification using Vision Transformers** — [arxiv_lg](https://arxiv.org/abs/2606.05149v1)
- **Generating Financial Time Series by Matching Random Convolutional Features** — [arxiv_lg](https://arxiv.org/abs/2606.05138v1)
- **RePercENT: Scaling Disentangled Representation Learning Beyond Two Modalities** — [arxiv_lg](https://arxiv.org/abs/2606.05109v1)
- **FLAGG: Flexible Autoregressive Graph Generation** — [arxiv_lg](https://arxiv.org/abs/2606.05067v1)
- **In-Context Graphical Inference** — [arxiv_lg](https://arxiv.org/abs/2606.05042v1)
- **On the Persistent Effects of Lexicality in Large Language Mod** — [arxiv_cl](https://arxiv.org/abs/2606.02750)
- **The Ghost Annotator: a Framework to Explore Human Label Variation in Content Moderation through Conformal Prediction** — [arxiv_cl](https://arxiv.org/abs/2606.02911)
- **NLLog: Lightweight, Explainable SOC Anomaly Detection via Log-to-Language Rewriting** — [arxiv_lg](https://arxiv.org/abs/2606.04957v1)
- **Sequential Data Poisoning in LLM Post-Training** — [arxiv_lg](https://arxiv.org/abs/2606.04929v1)
- **Toward Multi-Domain and Long-Tailed Quantization via Feature Alignment and Scaling** — [arxiv_lg](https://arxiv.org/abs/2606.04920v1)
- **Towards Pretraining Text Encoders for TabPFN** — [arxiv_lg](https://arxiv.org/abs/2606.04876v1)
- **Rethinking Incompleteness: Formalizing Protocol Divergence and Train-Once Learning for Robust IMVC** — [arxiv_lg](https://arxiv.org/abs/2606.04857v1)
- **STRIDE: Training Data Attribution via Sparse Recovery from Subset Perturbations** — [arxiv_lg](https://arxiv.org/abs/2606.05165v1)
- **BBOmix: A Tabular Benchmark for Hyperparameter Optimization of Unsupervised Biological Representation Learning** — [arxiv_lg](https://arxiv.org/abs/2606.05139v1)
- **Activation-Based Active Learning for In-Context Learning: Challenges and Insights** — [arxiv_lg](https://arxiv.org/abs/2606.05134v1)
- **As AI gets better, it reveals an empty promise** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/942629/as-ai-gets-better-it-reveals-an-empty-promise)
- **Meta’s AI agent for WhatsApp Business is now available globally** — [techcrunch_ai](https://techcrunch.com/2026/06/03/metas-ai-agent-for-whatsapp-business-is-now-available-globally/)
- **Microsoft and OpenAI broke up — now they’re ready to fight** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/942242/microsoft-build-ai-agents-openai-competition)
- **Coralogix raises $200M on bet that someone needs to watch the AI agents** — [techcrunch_ai](https://techcrunch.com/2026/06/03/coralogix-raises-200m-in-race-to-build-the-monitoring-layer-for-ai-agents/)
- **Introducing new capabilities to GPT-Rosalind** — [openai](https://openai.com/index/introducing-new-capabilities-to-gpt-rosalind)
- **How Wasmer used Codex to build a Node.js runtime for the edge** — [openai](https://openai.com/index/wasmer)
- **agruai/multiagent-business-automation** — [github](https://github.com/agruai/multiagent-business-automation)
- **zhihumomo/bashagt** — [github](https://github.com/zhihumomo/bashagt)
- **Publishers will be able to opt out of AI Search, thanks to new regulation** — [techcrunch_ai](https://techcrunch.com/2026/06/03/publishers-will-be-able-to-opt-out-of-ai-search-thanks-to-new-regulation/)
- **OpenAI public policy agenda** — [openai](https://openai.com/index/public-policy-agenda)
- **A blueprint for democratic governance of frontier AI** — [openai](https://openai.com/index/frontier-safety-blueprint)
- **Lovable signs multiyear deal with Google Cloud to up usage 5x, source says** — [techcrunch_ai](https://techcrunch.com/2026/06/03/lovable-signs-multi-year-deal-with-google-cloud-to-up-usage-5x-source-says/)
- **Amazon&#8217;s search bar will invent AI-generated products you can&#8217;t buy** — [theverge_ai](https://www.theverge.com/tech/942547/amazon-search-bar-ai-images)
- **Amazon will show AI product images when you search for some reason** — [techcrunch_ai](https://techcrunch.com/2026/06/03/amazon-will-show-ai-product-images-when-you-search-for-some-reason/)
- **How virtual power plants could provide energy for data centers** — [mit_tech_review](https://www.technologyreview.com/2026/06/03/1138350/virtual-power-plants-data-centers/)
- **The Download: Trump’s new AI order, and smart glasses for warfare** — [mit_tech_review](https://www.technologyreview.com/2026/06/03/1138322/the-download-trump-ai-order-smart-glasses-warfare/)
- **5 ways Google Search can level up your thrift and vintage shopping** — [google_ai](https://blog.google/products-and-platforms/products/search/thrifting-tips/)
- **AI has a water problem — Google thinks it has a fix** — [theverge_ai](https://www.theverge.com/policy/942296/google-water-commitments-data-centers)
- **Google must let publishers opt out of AI Search features, rules UK** — [theverge_ai](https://www.theverge.com/tech/942302/google-search-ai-overviews-uk-cma-publisher-opt-out)
- **rextanka/zero-cost-cline** — [github](https://github.com/rextanka/zero-cost-cline)
- **zaydmulani09/mnemo** — [github](https://github.com/zaydmulani09/mnemo)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **couragec/llm-intern-skill** — [github](https://github.com/couragec/llm-intern-skill)
- **ClaudioDrews/memory-os** — [github](https://github.com/ClaudioDrews/memory-os)
- **Alphabet’s record-breaking $85B raise for Google’s AI business is a helluva good signal** — [techcrunch_ai](https://techcrunch.com/2026/06/03/alphabets-record-breaking-85b-raise-for-googles-ai-business-is-a-helluva-good-signal/)
- **Google’s Dreambeans, its weirdest-named AI tool to date, will turn your life into a cartoon** — [techcrunch_ai](https://techcrunch.com/2026/06/03/googles-dreambeans-its-weirdest-named-ai-tool-to-date-will-turn-your-life-into-a-cartoon/)
- **These two founders left Goldman and Meta to build voice AI for markets everyone else overlooked** — [techcrunch_ai](https://techcrunch.com/2026/06/03/these-two-founders-left-goldman-and-meta-to-build-voice-ai-for-markets-everyone-else-overlooked/)
- **kurikomi-labs/komi-learn** — [github](https://github.com/kurikomi-labs/komi-learn)
- **tommy0103/obelisk** — [github](https://github.com/tommy0103/obelisk)
- **PercolatorFinance/ProwlFinance** — [github](https://github.com/PercolatorFinance/ProwlFinance)
- **Towards a Science of AI Agent Reliability** — [arxiv_cy](https://arxiv.org/abs/2602.16666)
- **lucasfcosta/backpressured** — [github](https://github.com/lucasfcosta/backpressured)
- **relaydeck/relaydeck** — [github](https://github.com/relaydeck/relaydeck)
- **PentesterFlow/agent** — [github](https://github.com/PentesterFlow/agent)
- **DannyMac180/skills** — [github](https://github.com/DannyMac180/skills)
- **tonbistudio/hermes-multi-agent-workflow** — [github](https://github.com/tonbistudio/hermes-multi-agent-workflow)
- **veryyoldman/metamask-openclaw** — [github](https://github.com/veryyoldman/metamask-openclaw)
- **razr001/align-dev** — [github](https://github.com/razr001/align-dev)
- **Guo-chunyu/Chaning.G-s-Lrlab** — [github](https://github.com/Guo-chunyu/Chaning.G-s-Lrlab)
- **anvia-hq/lexa** — [github](https://github.com/anvia-hq/lexa)
- **ethanhq/cc-fleet** — [github](https://github.com/ethanhq/cc-fleet)
- **扣子3.0实测：手机就能远程遥控你电脑里的Agent** — [qbitai](https://www.qbitai.com/2026/06/428648.html)
- **Whose Name Comes Up? II: Benchmarking and Intervention-Based Auditing of LLM-Based Scholar Recommendation** — [arxiv_cy](https://arxiv.org/abs/2602.08873)
- **8点1氪丨A股第4只两千元股诞生；问界回应浙江台州M9事故；马斯克个人财富将突破万亿美元** — [36kr](https://36kr.com/p/3838091144464644?f=rss)
- **The Dynamic and Endogenous Behavior of Re-Offense Risk: An Agent-Based Simulation Study of Treatment Allocation in Incarceration Diversion Programs** — [arxiv_cy](https://arxiv.org/abs/2601.12441)
- **Reproducibility is the New Copyleft: Defining AGI-oriented Reproducible Builds** — [arxiv_cy](https://arxiv.org/abs/2606.03019)
- **A Training-Efficient Transformer-Based Anti-Spoofing Network for Logical Access in ASVspoof 5** — [arxiv_cy](https://arxiv.org/abs/2606.02980)
- **The Fair Lending Model: How the Longest-Running Algorithmic Fairness Programs Work in Practice** — [arxiv_cy](https://arxiv.org/abs/2606.02957)
- **Parameter-Free and Group Conditional Online Conformal Prediction** — [arxiv_ml](https://arxiv.org/abs/2606.00419)
- **刚刚，李飞飞亲自下场定义世界模型** — [qbitai](https://www.qbitai.com/2026/06/428752.html)
- **从看懂世界到做对动作，卧安机器人OneModel 1.7用一条「隐式通路」打通了具身智能的关键断层** — [qbitai](https://www.qbitai.com/2026/06/428703.html)
- **Solipsistic Superintelligence is Unlikely to be Cooperative** — [arxiv_cy](https://arxiv.org/abs/2606.03237)
- **Calibrating Urban Traffic Simulation from Sparse Road Observations via Genetic Optimization** — [arxiv_cy](https://arxiv.org/abs/2606.03823)
- **Semantic knowledge guides innovation and drives cultural evolution** — [arxiv_cy](https://arxiv.org/abs/2510.12837)
- **If LLMs Have Human-Like Attributes, Then So Does Age of Empires II** — [arxiv_cy](https://arxiv.org/abs/2605.31514)
- **Scalable Derivative Gaussian Processes via Exact Gradient Reduction** — [arxiv_ml](https://arxiv.org/abs/2606.02909)
- **Few-Shot Prediction for Pulsar Noise with Long Short-Term Memory Network** — [arxiv_ml](https://arxiv.org/abs/2606.03574)
- **刚刚，Anthropic提交了招股书！** — [qbitai](https://www.qbitai.com/2026/06/428407.html)
- **Fairness Definitions and Metrics in Deep Reinforcement Learning for Drug Discovery in Healthcare: A Rapid Evidence Review** — [arxiv_cy](https://arxiv.org/abs/2606.02902)
- **Effect of Demographic Bias on Skin Lesion Classification** — [arxiv_cy](https://arxiv.org/abs/2606.03214)
- **Explainable Forecasting of Scientific Breakthroughs from Concept Network Dynamics** — [arxiv_cy](https://arxiv.org/abs/2606.03864)
- **Legal Alignment for Safe and Ethical AI** — [arxiv_cy](https://arxiv.org/abs/2601.04175)
- **A Sparse Bayesian Learning Algorithm for Estimation of Interaction Kernels in Motsch-Tadmor Model** — [arxiv_ml](https://arxiv.org/abs/2505.07068)
- **Estimating Bidirectional Causal Effects with Large Scale Online Kernel Learning** — [arxiv_ml](https://arxiv.org/abs/2511.05050)
- **Honesty in Causal Forests: When It Helps and When It Hurts** — [arxiv_ml](https://arxiv.org/abs/2506.13107)
- **AlphaEval: A Comprehensive and Efficient Evaluation Framework for Formula Alpha Mining** — [arxiv_ml](https://arxiv.org/abs/2508.13174)
- **世界模型榜首易主！跨维智能登顶WorldArena** — [qbitai](https://www.qbitai.com/2026/06/428435.html)
- **Pushing the Limits: A Framework to Reform Institutional Ethics Review of Environmentally-Impactful Computing Research** — [arxiv_cy](https://arxiv.org/abs/2606.03547)
- **TurtleAI: Benchmarking Multimodal Models for Visual Programming in Turtle Graphics** — [arxiv_cy](https://arxiv.org/abs/2606.03626)
- **Dynamic Objective Selection with Safeguards and LLM Oversight for Financial Decision-Making** — [arxiv_cy](https://arxiv.org/abs/2606.03704)
- **Forecasting Conceptual Diffusion in Science: The Case of Quantum Computing** — [arxiv_cy](https://arxiv.org/abs/2606.03919)
- **Question Type, Cognitive Load, and CEFR Alignment: Evaluating LLM-Generated EFL Grammar Drill Exercises** — [arxiv_cy](https://arxiv.org/abs/2606.01592)
- **Generating the Modal Worker: A Cross-Model Audit of Race and Gender in LLM-Generated Personas Across 41 Occupations** — [arxiv_cy](https://arxiv.org/abs/2510.21011)
- **State-Coupled Volatility in Latent Dynamical Systems: Recovery Under Partial Observation** — [arxiv_ml](https://arxiv.org/abs/2606.02664)
- **A Robust Optimization Approach to Sparse Principal Component Analysis** — [arxiv_ml](https://arxiv.org/abs/2606.03553)
- **Rashomon-Seeded Annealing for Robust Bayesian Inference in Factorial Designs** — [arxiv_ml](https://arxiv.org/abs/2606.02589)
- **Neural Networks Provably Learn Spectral Representations for Group Composition** — [arxiv_ml](https://arxiv.org/abs/2606.02993)
- **A Fast Screening Approach for High-dimensional Outcomes and High-dimensional Predictors** — [arxiv_ml](https://arxiv.org/abs/2606.03018)
- **The Value Function Semi-Algebraic Set in Partially Observable Markov Decision Processes** — [arxiv_ml](https://arxiv.org/abs/2606.03048)
- **Optimized Labeling Resource Allocation for Prediction-Assisted Inference via OPAL** — [arxiv_ml](https://arxiv.org/abs/2606.03211)
- **Online Learning with Gradient-Variation Interval Regret** — [arxiv_ml](https://arxiv.org/abs/2606.03831)
- **Optimal Initialization in Depth: Lyapunov Initialization and Limit Theorems for Deep Leaky ReLU Networks** — [arxiv_ml](https://arxiv.org/abs/2602.10949)
- **Exact Stiefel Optimization for Probabilistic PLS: Closed-Form Updates, Error Bounds, and Calibrated Uncertainty** — [arxiv_ml](https://arxiv.org/abs/2605.11607)
- **Evaluating the Impact of COVID-19 Vaccination in the United Kingdom: A Gaussian Process Approach** — [arxiv_ml](https://arxiv.org/abs/2210.02850)
- **氪星晚报 ｜曲美家居：境外子公司拟发行不超9亿挪威克朗境外债券；段永平在泡泡玛特持股比例升至6.04%；现货白银向下跌破74美元/盎司** — [36kr](https://36kr.com/p/3837330582008963?f=rss)
- **36氪独家 | 火山引擎提升MaaS营收目标至全年150亿元，Seedance 2.0单月营收已超10亿元** — [36kr](https://36kr.com/p/3836973710423429?f=rss)
- **Target Updates May Stabilize Linear Q-Learning: Periodic and Soft Dynamics** — [arxiv_ml](https://arxiv.org/abs/2606.02645)
- **ScoreStop: Gradient-based early stopping using functional score tests** — [arxiv_ml](https://arxiv.org/abs/2606.02740)
- **台积电魏哲家：预计今年全年营收成长仍将超过30%** — [36kr](https://36kr.com/newsflashes/3838242373667077?f=rss)
- **现代汽车与英伟达商讨在韩设立人工智能研发中心** — [36kr](https://36kr.com/newsflashes/3838197819672840?f=rss)
- **深圳具身公司获得汇川、中国电信亿元融资，“视触觉”传感器出货量行业第一｜硬氪首发** — [36kr](https://36kr.com/p/3837269482091656?f=rss)
- **深创投领投，这家微型关节模组企业完成数千万融资丨36氪首发** — [36kr](https://36kr.com/p/3837650456430851?f=rss)
- **华泰证券：下半年风险资产或延续占优** — [36kr](https://36kr.com/newsflashes/3838149147838984?f=rss)
- **AI基建催生“算力金属”热潮，供给端“硬约束”成为核心逻辑** — [36kr](https://36kr.com/newsflashes/3838146032077056?f=rss)
- **AI与新能源需求共振，高端铜箔产能供不应求** — [36kr](https://36kr.com/newsflashes/3838145260505602?f=rss)
- **Vanguard旗下VOO资产规模突破1万亿美元，刷新ETF行业里程碑** — [36kr](https://36kr.com/newsflashes/3838137685559815?f=rss)
- **意法半导体：AI需求强劲，上调数据中心收入预期** — [36kr](https://36kr.com/newsflashes/3838136983538181?f=rss)
- **香港推出首个生产力级超级智能体** — [36kr](https://36kr.com/newsflashes/3838218104604936?f=rss)
- **Uber对自动驾驶创企Nuro的承诺投资总额据悉近5亿美元** — [36kr](https://36kr.com/newsflashes/3838168530815236?f=rss)
- **中信证券：建议将汇率纳入盈利分析，关注高出海高汇兑敏感公司的业绩预期差** — [36kr](https://36kr.com/newsflashes/3838153801566727?f=rss)
- **黑石集团支持的Liftoff Mobile在美国首次公开募股中筹集4.37亿美元** — [36kr](https://36kr.com/newsflashes/3838152448166150?f=rss)