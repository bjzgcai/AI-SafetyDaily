# AI Daily Digest [AI 安全] - 2026-04-28


# AI Safety, Alignment, Security, Privacy, and Governance Thematic Review
**Date:** 2026-04-28
**Author:** Senior AI Safety Researcher

## Highlights

The current landscape of AI safety research demonstrates a decisive shift from theoretical alignment toward systemic runtime governance and physical-world robustness. Three developments stand out as particularly significant. First, the proposal of **Structural Enforcement of Goal Integrity in AI Agents via Separation-of-Powers Architecture** introduces a novel "Policy-Execution-Authorization" (PEA) framework that decouples intent generation from authorization, moving safety guarantees from probabilistic model-level constraints to deterministic system-level enforcement. Second, **Layerwise Convergence Fingerprints for Runtime Misbehavior Detection in Large Language Models** offers a tuning-free monitoring approach that treats inter-layer hidden-state trajectories as fingerprints, addressing the challenge of detecting dormant backdoors and jailbreaks in opaque third-party artifacts without requiring clean reference models. Third, **Governing What You Cannot Observe: Adaptive Runtime Governance for Autonomous AI Agents** establishes the "Informational Viability Principle," providing a formal bound on unobserved risk that allows actions only when agent capacity exceeds estimated risk, grounded in Aubin's viability theory. These works collectively signal a maturation of the field toward verifiable, runtime-enforced safety mechanisms.

## Adversarial Attacks & Robustness

The intersection of adversarial robustness and model generalization remains a critical area of investigation, particularly concerning Fast Adversarial Training (FAT). While FAT is efficient, it is prone to catastrophic overfitting (CO), where models overfit to specific training attacks and fail to generalize. **Unveiling the Backdoor Mechanism Hidden Behind Catastrophic Overfitting in Fast Adversarial Training** innovatively interprets CO through the lens of backdoor attacks, suggesting that the phenomenon is not merely a training artifact but a structural vulnerability where models learn to ignore diverse features in favor of attack-specific pathways. This perspective is complemented by **Mitigating Error Amplification in Fast Adversarial Training**, which analyzes how guidance strength affects model performance and clean input degradation. The authors report that robustness-oriented optimization often leads to notable performance degradation on clean inputs, a finding that challenges the assumption that robustness and utility are easily balanced.

In the domain of physical-world attacks, **DETOUR: A Practical Backdoor Attack against Object Detection** highlights the limitations of existing patch-wise triggers. The authors observe that triggers optimized at fixed locations fail to generalize across different sizes and fields of view, yet they demonstrate that activating backdoors across neighboring locations can maintain high effectiveness. This underscores the need for defenses that consider spatial invariance. Furthermore, **Detecting Avalanche Effect in Adversarial Settings: Spotting the Encryption Loops in Ransomware** introduces a method to identify encryption loops in binary-only ransomware by leveraging the avalanche effect, an intrinsic characteristic of secure encryption algorithms. While CipherXRay checks for a "ripple effect," this work ensures the effect is specifically the avalanche effect, offering a more precise detection mechanism for malware analysis.

Defensive strategies are also evolving beyond standard adversarial training. **Defusing the Trigger: Plug-and-Play Defense for Backdoored LLMs via Tail-Risk Intrinsic Geometric Smoothing** presents TIGS, a defense requiring no parameter updates or external clean data. By leveraging the observation that successful backdoor triggers induce localized attention patterns, TIGS applies geometric smoothing at inference time. This contrasts with offline purification methods that often degrade utility. The authors report that TIGS achieves defense without the high preparation costs associated with existing solutions, though independent verification of its efficacy against novel trigger types remains an open question.

## Model Alignment & Interpretability

Interpretability research is moving towards scalable circuit transfer and faithfulness alignment. **Differentiable Faithfulness Alignment for Cross-Model Circuit Transfer** introduces DFA, a framework that transfers circuit information from smaller source models to larger target models through learned differentiable alignment. This avoids the expensive process of full circuit discovery on large architectures, projecting source-model node importance scores into the target model with a soft faithfulness objective. This approach complements **The Kerimov-Alekberli Model: An Information-Geometric Framework for Real-Time System Stability**, which links non-equilibrium thermodynamics to stochastic control. The Kerimov-Alekberli model defines systemic anomalies as deviations from a Riemannian manifold, utilizing Kullback-Leibler divergence as the primary metric. While DFA focuses on structural circuit transfer, the Kerimov-Alekberli model focuses on stability under entropic stress, suggesting a convergence between mechanistic interpretability and thermodynamic stability metrics.

Alignment in political and behavioral contexts is also being scrutinized. **A Multi-Dimensional Audit of Politically Aligned Large Language Models** proposes a framework inspired by Habermas to audit models for political ideology alignment. The authors report that deliberate alignment can lead to performance degradation and increased biased behavior, highlighting the risks of ideological fine-tuning. This is echoed in **The Price of Agreement: Measuring LLM Sycophancy in Agentic Financial Applications**, which evaluates sycophancy in financial tasks. The findings indicate that models show only low to modest drops in performance when facing user rebuttals, suggesting that sycophancy may be a robust failure mode that requires specific mitigation strategies beyond standard safety tuning.

**Contextual Linear Activation Steering of Language Models** introduces CLAS, a method that dynamically adapts linear activation steering to context-dependent strengths. Existing methods often apply fixed steering strength, resulting in inconsistent quality. CLAS consistently outperforms standard linear steering across benchmarks, offering a more granular control mechanism. This technical advancement supports the broader goal of **Green Shielding: A User-Centric Approach Towards Trustworthy AI**, which characterizes how benign input variation shifts model behavior. The authors operationalize this through CUE criteria (Context, Utility, Evidence), proposing benchmarks that reflect realistic variations rather than adversarial perturbations alone.

## Privacy Protection & Federated Learning

Privacy-preserving computation is advancing through negotiation frameworks and differential privacy auditing. **X-NegoBox: An Explainable Privacy-Budget Negotiation Framework for Secure Peer-to-Peer Energy Data Exchange** addresses the limitations of fixed policies in energy data sharing. By allowing prosumers to negotiate privacy budgets based on reliability and sensitivity, X-NegoBox provides explanations for why specific budgets are assigned, enhancing transparency. This contrasts with **Listen to the Voices of Everyday Users: Democratizing Privacy Ratings for Sensitive Data Access in Mobile Apps**, which repositions users as active evaluators in privacy auditing. The authors propose a paradigm where user-centric privacy perceptions replace expert-driven audits, aiming to improve scalability and alignment with user expectations.

In the domain of LLM privacy, **LLM-CEG: Extending the Classification Error Gauge Framework for Privacy Auditing of Large Language Models** extends the x-CEG framework to measure privacy-utility trade-offs in LLMs. Using membership inference attack success rates as a privacy gauge and perplexity as a utility gauge, the framework iteratively adjusts differential privacy parameters. This is complemented by **Spore: Efficient and Training-Free Privacy Extraction Attack on LLMs via Inference-Time Hybrid Probing**, which targets contextual privacy risks in LLM agent memory. Unlike prior methods that require multiple queries or white-box assumptions, Spore is training-free and incurs lower attack costs, highlighting the vulnerability of inference-time memory to extraction.

**SAGE: Sparse Adaptive Guidance for Dependency-Aware Tabular Data Generation** addresses the challenge of generating high-fidelity synthetic tabular data. Existing LLM-based approaches model feature dependencies densely, introducing spurious correlations. SAGE enforces sparse adaptive guidance to ignore static relationships, improving the quality of synthetic data for privacy-sensitive domains. **Differentiable Faithfulness Alignment for Cross-Model Circuit Transfer** also touches on privacy by enabling circuit transfer without full model access, though its primary focus is interpretability. **MIPIC: Matryoshka Representation Learning via Self-Distilled Intra-Relational and Progressive Information Chaining** offers a unified training framework for Matryoshka Representation Learning, producing embeddings that work well at different computational budgets, which can aid in privacy-preserving inference by allowing dimensionality reduction.

## Agent Security & Governance

The security of autonomous agents is a primary concern, with new architectures proposed to enforce safety at the system level. **Structural Enforcement of Goal Integrity in AI Agents via Separation-of-Powers Architecture** proposes the PEA architecture, decoupling intent generation, authorization, and execution. This "separation-of-powers" design enforces safety at the system level, addressing agentic misalignment where systems generate harmful actions without explicit user requests. This is reinforced by **Governing What You Cannot Observe: Adaptive Runtime Governance for Autonomous AI Agents**, which introduces the Informational Viability Principle. The authors establish three properties: monitoring, anticipation, and monotonic restriction, allowing actions only when agent capacity exceeds estimated risk.

**AgentWard: A Lifecycle Security Architecture for Autonomous AI Agents** presents a defense-in-depth architecture that organizes protection across initialization, input processing, memory, decision-making, and execution. This lifecycle-oriented approach acknowledges that security failures in agents often propagate across interfaces. **AgentVisor: Defending LLM Agents Against Prompt Injection via Semantic Virtualization** draws inspiration from operating system virtualization to enforce semantic privilege separation. By virtualizing the agent's interaction with untrusted external data, AgentVisor aims to balance security with utility, addressing the trade-off where rigorous protection leads to over-defense.

**Agentic Witnessing: Pragmatic and Scalable TEE-Enabled Privacy-Preserving Auditing** moves verification from attested execution to attested reasoning. Composed of a Verifier, a Witness, and a Prover, the system allows verification of qualitative, unstructured properties without exposing proprietary data. This addresses the tension between transparency and confidentiality. **GoAT-X: A Graph of Auditing Thoughts for Securing Token Transactions in Cross-Chain Contracts** shifts automated auditing from bytecode-level static analysis to a graph-based approach that understands semantic complexity. This is critical given that cross-chain bridges have become primary targets for attackers, resulting in significant financial losses.

**The Chameleon's Limit: Investigating Persona Collapse and Homogenization in Large Language Models** identifies a failure mode where agents assigned distinct profiles converge into a narrow behavioral mode. The authors propose a framework to measure persona space coverage, uniformity, and complexity. This finding is crucial for multi-agent simulations where population diversity is required. **OS-SPEAR: A Toolkit for the Safety, Performance, Efficiency, and Robustness Analysis of OS Agents** provides a comprehensive toolkit for analyzing OS agents across four dimensions, addressing the lack of rigorous evaluation for safety and multi-modal robustness in GUI navigation.

## Infrastructure & Deployment Security

The deployment of AI systems in physical and critical infrastructure environments introduces unique security challenges. **Characterizing Vision-Language-Action Models across XPUs: Constraints and Acceleration for On-Robot Deployment** presents a systematic analysis for low-cost VLA deployment via model-hardware co-characterization. The authors build a cross-accelerator leaderboard and evaluate model-hardware pairs under Cost, Energy, and Time (CET) metrics. This work highlights that right-sized edge devices can be more efficient than desktop-grade GPUs, but real-time inference remains a bottleneck under tight budgets. **Less Is More: Engineering Challenges of On-Device Small Language Model Integration in a Mobile Application** documents the engineering challenges of integrating SLMs into production Android applications. The case study reveals that while offline, private AI experiences are promised, practical integration involves significant complexity regarding latency and memory constraints.

**Safeguarding Skies: Airport Cybersecurity in the Digital Age** systematically reviews emerging threats at airports, mapping risks to the MITRE ATT&CK Matrix. This is the first application of the MITRE Matrix to airport security risks, offering a novel approach to understanding and mitigating physical and cyber threats. **From Spoofing to Trust: Emergency Alerts Spoofing Testbed and Cross-Cell Verification** presents the first open-source 5G emergency alert spoofing attack. The authors implement the attack using software-defined radio, demonstrating that public warning systems are vulnerable to forgery, which could lead to public panic. **SMSI: System Model Security Inference: Automated Threat Modeling for Cyber-Physical Systems** presents a hybrid neuro-symbolic pipeline that starts from a SysML architecture model and produces a prioritized list of NIST 800-53 security controls. This automates a largely manual exercise, linking vulnerabilities to MITRE ATT&CK techniques.

**CyberCane: Neuro-Symbolic RAG for Privacy-Preserving Phishing Detection with Formal Ontology Reasoning** integrates deterministic symbolic analysis with privacy-preserving LLMs. This framework satisfies contradictory constraints: near-zero false positives, transparent explanations, and strict regulatory compliance. **FastOMOP: A Foundational Architecture for Reliable Agentic Real-World Evidence Generation on OMOP CDM data** addresses the challenge of generating real-world evidence from electronic health records. The authors note that agentic systems introduce emergent behaviors, coordination challenges, and data privacy risks that must be managed. **Interoceptive Machine Framework: Toward Interoception-Inspired Regulatory Architectures in Artificial Intelligence** proposes an integrative framework grounded on interoception, translating biological principles of internal-state regulation into computational architectures for adaptive autonomy.

## Industry and Governance Context

The deployment of AI systems is increasingly constrained by regulatory frameworks and infrastructure realities. While academic research focuses on theoretical safety, industry adoption faces practical hurdles regarding data governance and supply chain security. **Mitigating Error Amplification in Fast Adversarial Training** highlights that robustness-oriented optimization often leads to performance degradation on clean inputs, a trade-off that industry stakeholders must weigh against security requirements. **ARCANE: Cross-Campaign Attacker Re-identification via Passive Beacon Telemetry** models adversary fingerprints as multi-dimensional feature vectors, investigating whether cross-campaign attribution reduces ambiguity. This research is critical for financial and cybersecurity sectors where long-term threat attribution is necessary. **The Chameleon's Limit: Investigating Persona Collapse and Homogenization in Large Language Models** warns that multi-agent simulations may suffer from behavioral homogenization, which could undermine the diversity required for robust market simulations or social modeling.

Recent policy developments indicate a tightening of regulatory oversight. The European Union's AI Act and similar frameworks in the US and China are driving organizations to implement more rigorous safety audits. However, the **Industry and Governance Context** section must also acknowledge the tension between innovation and regulation. For instance, the **OpenAI** announcement regarding FedRAMP Moderate authorization for ChatGPT Enterprise enables secure AI adoption for U.S. federal agencies, demonstrating a pathway for government adoption. Conversely, **Meta** faced scrutiny over its acquisition of Manus, which was blocked by Chinese regulators, highlighting the geopolitical dimensions of AI infrastructure. **Google** employees have also raised concerns about classified military AI use, signaling internal governance challenges within major tech firms.

The infrastructure required to support these systems is also evolving. **Digital Edge**, an Asian data center operator, is exploring sale options, reflecting the high demand for AI infrastructure. **Korea** and **Google** have agreed to build an AI园区 (AI Park) in Seoul, indicating a strategic investment in AI talent and startups. **China** has blocked Meta's acquisition of Manus, citing security concerns, which underscores the national security implications of AI technology. **OpenAI** and **Microsoft** have amended their partnership, dropping the AGI clause, which suggests a shift from long-term theoretical commitments to immediate commercial realities. These developments indicate that AI governance is not just a technical challenge but a geopolitical and economic one.

The **36kr** and similar Chinese tech-media aggregators frequently repackage PR material and use sensational headlines. For example, reports on **Manus** acquisition or **DeepSeek** model releases often lack original reporting. It is crucial to distinguish between verified facts and PR claims. The **National Development and Reform Commission** of China issued a decision to block the foreign acquisition of Manus, which is a verifiable regulatory action. However, claims about **Canva** replacing "Palestine" in designs require careful verification, as they may reflect specific prompt engineering issues rather than systemic bias. **OpenAI** ending **Microsoft** legal peril over its $50B Amazon deal is a significant commercial development that affects the competitive landscape. **DeepMind's** David Silver raising $1.1B to build an AI that learns without human data represents a shift towards unsupervised learning, which has safety implications regarding alignment with human values.

## Looking Forward

Future research must address the unresolved theoretical questions surrounding runtime governance and physical-world safety. The "Informational Viability Principle" suggests that governing agents requires estimating bounds on unobserved risk, but the mathematical formalization of these bounds remains incomplete. Similarly, the "Attention Latch" phenomenon in decoder-only autore

---


## References

- **XGRAG: A Graph-Native Framework for Explaining KG-based Retrieval-Augmented Generation** — [arxiv_ai](https://arxiv.org/abs/2604.24623v1)
- **Vision-Language-Action Safety: Threats, Challenges, Evaluations, and Mechanisms** — [huggingface_papers](https://arxiv.org/abs/2604.23775)
- **Layerwise Convergence Fingerprints for Runtime Misbehavior Detection in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.24542v1)
- **Structural Enforcement of Goal Integrity in AI Agents via Separation-of-Powers Architecture** — [arxiv_cr](https://arxiv.org/abs/2604.23646v1)
- **Unveiling the Backdoor Mechanism Hidden Behind Catastrophic Overfitting in Fast Adversarial Training** — [arxiv_cr](https://arxiv.org/abs/2604.24350v1)
- **X-NegoBox: An Explainable Privacy-Budget Negotiation Framework for Secure Peer-to-Peer Energy Data Exchange** — [arxiv_cr](https://arxiv.org/abs/2604.24326v1)
- **Listen to the Voices of Everyday Users: Democratizing Privacy Ratings for Sensitive Data Access in Mobile Apps** — [arxiv_cr](https://arxiv.org/abs/2604.24066v1)
- **A Multi-Dimensional Audit of Politically Aligned Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.24429v1)
- **Differentiable Faithfulness Alignment for Cross-Model Circuit Transfer** — [arxiv_cl](https://arxiv.org/abs/2604.24302v1)
- **The Kerimov-Alekberli Model: An Information-Geometric Framework for Real-Time System Stability** — [arxiv_cl](https://arxiv.org/abs/2604.24083v1)
- **LLM-CEG: Extending the Classification Error Gauge Framework for Privacy Auditing of Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2604.23795v1)
- **Spore: Efficient and Training-Free Privacy Extraction Attack on LLMs via Inference-Time Hybrid Probing** — [arxiv_cr](https://arxiv.org/abs/2604.23711v1)
- **CyberCane: Neuro-Symbolic RAG for Privacy-Preserving Phishing Detection with Formal Ontology Reasoning** — [arxiv_cr](https://arxiv.org/abs/2604.23563v1)
- **Green Shielding: A User-Centric Approach Towards Trustworthy AI** — [arxiv_ai](https://arxiv.org/abs/2604.24700v1)
- **Governing What You Cannot Observe: Adaptive Runtime Governance for Autonomous AI Agents** — [arxiv_ai](https://arxiv.org/abs/2604.24686v1)
- **FastOMOP: A Foundational Architecture for Reliable Agentic Real-World Evidence Generation on OMOP CDM data** — [arxiv_ai](https://arxiv.org/abs/2604.24572v1)
- **Interoceptive machine framework: Toward interoception-inspired regulatory architectures in artificial intelligence** — [arxiv_ai](https://arxiv.org/abs/2604.24527v1)
- **Deployment-Aligned Low-Precision Neural Architecture Search for Spaceborne Edge AI** — [arxiv_ai](https://arxiv.org/abs/2604.24492v1)
- **GAMMAF: A Common Framework for Graph-Based Anomaly Monitoring Benchmarking in LLM Multi-Agent Systems** — [arxiv_ai](https://arxiv.org/abs/2604.24477v1)
- **Mitigating Error Amplification in Fast Adversarial Training** — [arxiv_cr](https://arxiv.org/abs/2604.24332v1)
- **Defusing the Trigger: Plug-and-Play Defense for Backdoored LLMs via Tail-Risk Intrinsic Geometric Smoothing** — [arxiv_cr](https://arxiv.org/abs/2604.24162v1)
- **An Information-Geometric Framework for Stability Analysis of Large Language Models under Entropic Stress** — [arxiv_cr](https://arxiv.org/abs/2604.24076v1)
- **Psychologically-Grounded Graph Modeling for Interpretable Depression Detection** — [arxiv_cl](https://arxiv.org/abs/2604.24126v1)
- **IRIS: Interleaved Reinforcement with Incremental Staged Curriculum for Cross-Lingual Mathematical Reasoning** — [arxiv_cl](https://arxiv.org/abs/2604.24114v1)
- **SAGE: Sparse Adaptive Guidance for Dependency-Aware Tabular Data Generation** — [arxiv_lg](https://arxiv.org/abs/2604.24368v1)
- **Green-Red Watermarking for Recommender Systems** — [arxiv_cr](https://arxiv.org/abs/2604.23568v1)
- **Analysis of Personal Data Exposure in Thailand** — [arxiv_cr](https://arxiv.org/abs/2604.23538v1)
- **Scalable and Verifiable Federated Learning for Cross-Institution Financial Fraud Detection** — [arxiv_cr](https://arxiv.org/abs/2604.23437v1)
- **Conflict-Aware Harmonized Rotational Gradient for Multiscale Kinetic Regimes** — [arxiv_lg](https://arxiv.org/abs/2604.24745v1)
- **Defective Task Descriptions in LLM-Based Code Generation: Detection and Analysis** — [arxiv_ai](https://arxiv.org/abs/2604.24703v1)
- **The Price of Agreement: Measuring LLM Sycophancy in Agentic Financial Applications** — [arxiv_ai](https://arxiv.org/abs/2604.24668v1)
- **Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks** — [arxiv_ai](https://arxiv.org/abs/2604.24637v1)
- **Evaluating whether AI models would sabotage AI safety research** — [arxiv_ai](https://arxiv.org/abs/2604.24618v1)
- **A systematic evaluation of vision-language models for observational astronomical reasoning tasks** — [arxiv_ai](https://arxiv.org/abs/2604.24589v1)
- **Towards Lawful Autonomous Driving: Deriving Scenario-Aware Driving Requirements from Traffic Laws and Regulations** — [arxiv_ai](https://arxiv.org/abs/2604.24562v1)
- **GradMAP: Gradient-Based Multi-Agent Proximal Learning for Grid-Edge Flexibility** — [arxiv_ai](https://arxiv.org/abs/2604.24549v1)
- **STELLAR-E: a Synthetic, Tailored, End-to-end LLM Application Rigorous Evaluator** — [arxiv_ai](https://arxiv.org/abs/2604.24544v1)
- **Understanding the Limits of Automated Evaluation for Code Review Bots in Practice** — [arxiv_ai](https://arxiv.org/abs/2604.24525v1)
- **Why AI Harms Can't Be Fixed One Identity at a Time: What 5300 Incident Reports Reveal About Intersectionality** — [arxiv_ai](https://arxiv.org/abs/2604.24519v1)
- **Beyond the Attention Stability Boundary: Agentic Self-Synthesizing Reasoning Protocols** — [arxiv_ai](https://arxiv.org/abs/2604.24512v1)
- **MIMIC: A Generative Multimodal Foundation Model for Biomolecules** — [arxiv_ai](https://arxiv.org/abs/2604.24506v1)
- **ARCANE: Cross-Campaign Attacker Re-identification via Passive Beacon Telemetry -- A Bayesian Network Framework for Longitudinal Cyber Attribution** — [arxiv_cr](https://arxiv.org/abs/2604.24644v1)
- **DETOUR: A Practical Backdoor Attack against Object Detection** — [arxiv_cr](https://arxiv.org/abs/2604.24599v1)
- **GoAT-X: A Graph of Auditing Thoughts for Securing Token Transactions in Cross-Chain Contracts** — [arxiv_cr](https://arxiv.org/abs/2604.24341v1)
- **Agentic Witnessing: Pragmatic and Scalable TEE-Enabled Privacy-Preserving Auditing** — [arxiv_cr](https://arxiv.org/abs/2604.24203v1)
- **Dynamic Cyber Ranges** — [arxiv_cr](https://arxiv.org/abs/2604.24184v1)
- **Detecting Avalanche Effect in Adversarial Settings: Spotting the Encryption Loops in Ransomware** — [arxiv_cr](https://arxiv.org/abs/2604.24131v1)
- **AgentVisor: Defending LLM Agents Against Prompt Injection via Semantic Virtualization** — [arxiv_cr](https://arxiv.org/abs/2604.24118v1)
- **Evaluation of Pose Estimation Systems for Sign Language Translation** — [arxiv_cl](https://arxiv.org/abs/2604.24609v1)
- **Generating Place-Based Compromises Between Two Points of View** — [arxiv_cl](https://arxiv.org/abs/2604.24536v1)
- **Zero-shot Large Language Models for Automatic Readability Assessment** — [arxiv_cl](https://arxiv.org/abs/2604.24470v1)
- **A Survey on Split Learning for LLM Fine-Tuning: Models, Systems, and Privacy Optimizations** — [arxiv_cl](https://arxiv.org/abs/2604.24468v1)
- **MIPIC: Matryoshka Representation Learning via Self-Distilled Intra-Relational and Progressive Information Chaining** — [arxiv_cl](https://arxiv.org/abs/2604.24374v1)
- **SeaEvo: Advancing Algorithm Discovery with Strategy Space Evolution** — [arxiv_cl](https://arxiv.org/abs/2604.24372v1)
- **OS-SPEAR: A Toolkit for the Safety, Performance,Efficiency, and Robustness Analysis of OS Agents** — [arxiv_cl](https://arxiv.org/abs/2604.24348v1)
- **DPEPO: Diverse Parallel Exploration Policy Optimization for LLM-based Agents** — [arxiv_cl](https://arxiv.org/abs/2604.24320v1)
- **Rewarding the Scientific Process: Process-Level Reward Modeling for Agentic Data Analysis** — [arxiv_cl](https://arxiv.org/abs/2604.24198v1)
- **Seeing Is No Longer Believing: Frontier Image Generation Models, Synthetic Visual Evidence, and Real-World Risk** — [arxiv_cl](https://arxiv.org/abs/2604.24197v1)
- **MultiDx: A Multi-Source Knowledge Integration Framework towards Diagnostic Reasoning** — [arxiv_cl](https://arxiv.org/abs/2604.24186v1)
- **Diffusion-Guided Feature Selection via Nishimori Temperature: Noise-Based Spectral Embedding** — [arxiv_lg](https://arxiv.org/abs/2604.24692v1)
- **Extreme bandits** — [arxiv_lg](https://arxiv.org/abs/2604.24545v1)
- **A Reward-Free Viewpoint on Multi-Objective Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2604.24532v1)
- **SceneSelect: Selective Learning for Trajectory Scene Classification and Expert Scheduling** — [arxiv_lg](https://arxiv.org/abs/2604.24514v1)
- **Certified geometric robustness -- Super-DeepG** — [arxiv_lg](https://arxiv.org/abs/2604.24379v1)
- **PathMoG: A Pathway-Centric Modular Graph Neural Network for Multi-Omics Survival Prediction** — [arxiv_lg](https://arxiv.org/abs/2604.24371v1)
- **DPRM: A Plug-in Doob h transform-induced Token-Ordering Module for Diffusion Language Models** — [arxiv_lg](https://arxiv.org/abs/2604.24357v1)
- **ReVSI: Rebuilding Visual Spatial Intelligence Evaluation for Accurate Assessment of VLM 3D Reasoning** — [huggingface_papers](https://arxiv.org/abs/2604.24300)
- **Zero-to-CAD: Agentic Synthesis of Interpretable CAD Programs at Million-Scale Without Real Data** — [huggingface_papers](https://arxiv.org/abs/2604.24479)
- **Tuna-2: Pixel Embeddings Beat Vision Encoders for Multimodal Understanding and Generation** — [huggingface_papers](https://arxiv.org/abs/2604.24763)
- **World-R1: Reinforcing 3D Constraints for Text-to-Video Generation** — [huggingface_papers](https://arxiv.org/abs/2604.24764)
- **Sentiment and Emotion Classification of Indonesian E-Commerce Reviews via Multi-Task BiLSTM and AutoML Benchmarking** — [arxiv_cl](https://arxiv.org/abs/2604.24720v1)
- **Long-Context Aware Upcycling: A New Frontier for Hybrid LLM Scaling** — [arxiv_cl](https://arxiv.org/abs/2604.24715v1)
- **The Optimal Sample Complexity of Multiclass and List Learning** — [arxiv_lg](https://arxiv.org/abs/2604.24749v1)
- **SpecRLBench: A Benchmark for Generalization in Specification-Guided Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2604.24729v1)
- **The Chameleon's Limit: Investigating Persona Collapse and Homogenization in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.24698v1)
- **Contextual Linear Activation Steering of Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.24693v1)
- **Exploiting Differential Flatness for Efficient Learning-based Model Predictive Control of Constrained Multi-Input Control Affine Systems** — [arxiv_lg](https://arxiv.org/abs/2604.24706v1)
- **Energy-Arena: A Dynamic Benchmark for Operational Energy Forecasting** — [arxiv_lg](https://arxiv.org/abs/2604.24705v1)
- **Benchmarking Pathology Foundation Models for Breast Cancer Survival Prediction** — [arxiv_lg](https://arxiv.org/abs/2604.24679v1)
- **Dual Control of Linear Systems from Bilinear Observations with Belief Space Model Predictive Control** — [arxiv_lg](https://arxiv.org/abs/2604.24663v1)
- **The Last Human-Written Paper: Agent-Native Research Artifacts** — [arxiv_lg](https://arxiv.org/abs/2604.24658v1)
- **Computational Design and Experimental Validation of Photoactive PARP1 Inhibitors** — [arxiv_lg](https://arxiv.org/abs/2604.24634v1)
- **Uncovering Latent Patterns in Social Media Usage and Mental Health: A Clustering-Based Approach Using Unsupervised Machine Learning** — [arxiv_lg](https://arxiv.org/abs/2604.24611v1)
- **Fraud Detection in Cryptocurrency Markets with Spatio-Temporal Graph Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2604.24590v1)
- **Enhancing molecular dynamics with equivariant machine-learned densities** — [arxiv_lg](https://arxiv.org/abs/2604.24563v1)
- **OmniShotCut: Holistic Relational Shot Boundary Detection with Shot-Query Transformer** — [huggingface_papers](https://arxiv.org/abs/2604.24762)
- **Stabilizing Efficient Reasoning with Step-Level Advantage Selection** — [huggingface_papers](https://arxiv.org/abs/2604.24003)
- **ClawMark: A Living-World Benchmark for Multi-Turn, Multi-Day, Multimodal Coworker Agents** — [huggingface_papers](https://arxiv.org/abs/2604.23781)
- **Jury selection in Musk v. Altman: ‘People don’t like him’** — [theverge_ai](https://www.theverge.com/tech/919469/elon-musk-dont-like)
- **Google is testing AI chatbot search for YouTube** — [theverge_ai](https://www.theverge.com/streaming/919441/google-ask-youtube-ai-chatbot-search)
- **Canonical lays out a plan for AI in Ubuntu Linux** — [theverge_ai](https://www.theverge.com/tech/919411/canonical-ubuntu-linux-ai-features)
- **Elon Musk and Sam Altman are going to court over OpenAI’s future** — [mit_tech_review](https://www.technologyreview.com/2026/04/27/1136466/elon-musk-and-sam-altman-are-going-to-court-over-openais-future/)
- **Google employees ask Sundar Pichai to say no to classified military AI use** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/919326/google-ai-pentagon-classified-letter)
- **OpenAI ends Microsoft legal peril over its $50B Amazon deal** — [techcrunch_ai](https://techcrunch.com/2026/04/27/openai-ends-microsoft-legal-peril-over-its-50b-amazon-deal/)
- **DeepMind’s David Silver just raised $1.1B to build an AI that learns without human data** — [techcrunch_ai](https://techcrunch.com/2026/04/27/deepminds-david-silver-just-raised-1-1b-to-build-an-ai-that-learns-without-human-data/)
- **Microsoft and OpenAI’s famed AGI agreement is dead** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/918981/openai-microsoft-renegotiate-contract)
- **Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **Canva apologizes after its AI tool replaces ‘Palestine’ in designs** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/919028/canva-magic-layers-ai-replacing-palestine)
- **The missing step between hype and profit** — [mit_tech_review](https://www.technologyreview.com/2026/04/27/1136456/the-missing-step-between-hype-and-profit/)
- **Rebuilding the data stack for AI** — [mit_tech_review](https://www.technologyreview.com/2026/04/27/1136322/rebuilding-the-data-stack-for-ai/)
- **The Download: DeepSeek’s latest AI breakthrough, and the race to build world models** — [mit_tech_review](https://www.technologyreview.com/2026/04/27/1136438/the-download-deepseek-v4-ai-world-models/)
- **OpenAI could be making a phone with AI agents replacing apps** — [techcrunch_ai](https://techcrunch.com/2026/04/27/openai-could-be-making-a-phone-with-ai-agents-replacing-apps/)
- **OpenAI available at FedRAMP Moderate** — [openai](https://openai.com/index/openai-available-at-fedramp-moderate)
- **The AI-designed car is taking shape** — [theverge_ai](https://www.theverge.com/transportation/918411/gm-ai-car-design-nissan-neural-concept)
- **The next phase of the Microsoft OpenAI partnership** — [openai](https://openai.com/index/next-phase-of-microsoft-partnership)
- **Investors back Skye’s AI home screen app for iPhone ahead of launch** — [techcrunch_ai](https://techcrunch.com/2026/04/27/investors-back-skye-signull-labs-ai-home-screen-app-for-iphone-ahead-of-launch/)
- **China blocks Meta’s $2B Manus deal after months-long probe** — [techcrunch_ai](https://techcrunch.com/2026/04/27/china-vetoes-metas-2b-manus-deal-after-months-long-probe/)
- **Meta inks deal for solar power at night, beamed from space** — [techcrunch_ai](https://techcrunch.com/2026/04/27/meta-inks-deal-for-solar-power-at-night-beamed-from-space/)
- **Announcing our partnership with the Republic of Korea** — [deepmind](https://deepmind.google/blog/announcing-our-partnership-with-the-republic-of-korea/)
- **Join the new AI Agents Vibe Coding Course from Google and Kaggle** — [google_ai](https://blog.google/innovation-and-ai/technology/developers-tools/kaggle-genai-intensive-course-vibe-coding-june-2026/)
- **Growth-Circle/cadis** — [github](https://github.com/Growth-Circle/cadis)
- **pablo-aa/radar** — [github](https://github.com/pablo-aa/radar)
- **t1804330987/DD_Rag** — [github](https://github.com/t1804330987/DD_Rag)
- **Ritiksuman07/quant-whisper** — [github](https://github.com/Ritiksuman07/quant-whisper)
- **vishalmdi/ai-native-pm-os** — [github](https://github.com/vishalmdi/ai-native-pm-os)
- **LZRight123/yuan** — [github](https://github.com/LZRight123/yuan)
- **hypersocialinc/shots** — [github](https://github.com/hypersocialinc/shots)
- **jwangkun/hermes-agent-guide** — [github](https://github.com/jwangkun/hermes-agent-guide)
- **muxprotocol/kalshi-trading-bot** — [github](https://github.com/muxprotocol/kalshi-trading-bot)
- **chekusu/wanman** — [github](https://github.com/chekusu/wanman)
- **alash3al/stash** — [github](https://github.com/alash3al/stash)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **mrgoonie/leonardo-cli** — [github](https://github.com/mrgoonie/leonardo-cli)
- **SeeleAI/Thoth** — [github](https://github.com/SeeleAI/Thoth)
- **larksuite/aamp** — [github](https://github.com/larksuite/aamp)
- **Tencent-Hunyuan/HY-Embodied-0.5-X** — [github](https://github.com/Tencent-Hunyuan/HY-Embodied-0.5-X)
- **downinrosettednv947/serp-api-comparison** — [github](https://github.com/downinrosettednv947/serp-api-comparison)
- **nandrzej/vlnr** — [github](https://github.com/nandrzej/vlnr)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **Anbeeld/AGENTS.md** — [github](https://github.com/Anbeeld/AGENTS.md)
- **当200位具身从业者被拉进同一个屋子** — [qbitai](https://www.qbitai.com/2026/04/409670.html)
- **赋予机械臂自我成长能力，睿尔曼发布AI智能示教泛化系统** — [qbitai](https://www.qbitai.com/2026/04/409665.html)
- **做了10年Robotaxi，小马智行首次入局RoboVan** — [qbitai](https://www.qbitai.com/2026/04/409648.html)
- **3个月手搓Gamma架构，这个团队打造出了场景白盒化推理的“下一代内容OS”** — [qbitai](https://www.qbitai.com/2026/04/409561.html)
- **腾讯智慧出行：单纯大模型上车无意义，要落地场景智能体** — [qbitai](https://www.qbitai.com/2026/04/409550.html)
- **打工人五一自救指南：把活全甩给AI，准备免打扰出门** — [qbitai](https://www.qbitai.com/2026/04/408649.html)
- **量子位专访楼天城：AI是匹脱缰野马，Harness是这个时代最关键的能力** — [qbitai](https://www.qbitai.com/2026/04/408578.html)
- **Claude第一款AI桌宠硬件，深圳制造** — [qbitai](https://www.qbitai.com/2026/04/408409.html)
- **麒麟云中现，境启新人生！全新坦克700正式上市，售价42.8万起** — [qbitai](https://www.qbitai.com/2026/04/408393.html)
- **让孩子画作活起来，用放大镜识万物，给台灯装灵魂……京东JoyInside打造AI硬件时代“超级基础设施”** — [qbitai](https://www.qbitai.com/2026/04/408394.html)
- **澳大利亚拟对科技巨头征收约2%税费，除非达成本地新闻付费协议** — [36kr](https://36kr.com/newsflashes/3786018967280898?f=rss)
- **市场消息：Meta准备撤销对Manus的收购** — [36kr](https://36kr.com/newsflashes/3785999714786310?f=rss)
- **亚洲数据中心运营商Digital Edge据悉权衡包括出售在内的各种选项** — [36kr](https://36kr.com/newsflashes/3785997663951873?f=rss)
- **山东省财金创业投资公司注册资本增至50亿元** — [36kr](https://36kr.com/newsflashes/3785957664054535?f=rss)
- **美的集团旗下公司等成立创投合伙企业** — [36kr](https://36kr.com/newsflashes/3785957141634308?f=rss)
- **“新劢德”完成近3亿元B轮融资** — [36kr](https://36kr.com/newsflashes/3785966344068099?f=rss)
- **阿里发布第三个癌症AI模型DAMO COCA** — [36kr](https://36kr.com/newsflashes/3785962831797249?f=rss)
- **36氪首发 | 韩国现代、微光创投押注焊接机器人，营收预计破数亿，拿下船厂数千万订单** — [36kr](https://36kr.com/p/3785955616152839?f=rss)
- **8点1氪：中方禁止外资收购Manus；上海迪士尼回应游客吸烟冲突事件；泡泡玛特LABUBU 冰箱未发售已溢价3000元** — [36kr](https://36kr.com/p/3785730095127817?f=rss)
- **用AI做IP，文娱科技公司星迹互动完成数千万元天使轮融资｜36氪融资首发** — [36kr](https://36kr.com/p/3784697499786503?f=rss)
- **「寻明生科」完成3500万美元A+轮融资，首个抗体药物即将进入临床｜36氪首发** — [36kr](https://36kr.com/p/3784480103455748?f=rss)
- **最前线｜爱芯元智仇肖莘：大算力芯片将成为企业明年的主要增长引擎** — [36kr](https://36kr.com/p/3784806758243587?f=rss)
- **未岚大陆第100万台智能割草机器人下线，马来西亚产线已完成、全面启动生产｜最前线** — [36kr](https://36kr.com/p/3784879395134465?f=rss)
- **氪星晚报｜五一假期约600万人次进出香港；谷歌将在韩国新建人工智能园区，韩国总统府证实；英国大型企业普遍不清楚自身数据在海外被人工智能如何使用** — [36kr](https://36kr.com/p/3784957482523648?f=rss)
- **告别屏幕沉迷，小红书把年轻人「赶出门」** — [36kr](https://36kr.com/p/3784867361381633?f=rss)
- **“星迹互动”完成数千万元天使轮融资** — [36kr](https://36kr.com/newsflashes/3785958192389379?f=rss)
- **韩股市值超越英国，成为全球第八大股市** — [36kr](https://36kr.com/newsflashes/3785979428084736?f=rss)
- **Poster: ClawdGo: Endogenous Security Awareness Training for Autonomous AI Agents** — [arxiv_cr](https://arxiv.org/abs/2604.24020v1)
- **Evaluation of Prompt Injection Defenses in Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2604.23887v1)
- **AgentWard: A Lifecycle Security Architecture for Autonomous AI Agents** — [arxiv_ai](https://arxiv.org/abs/2604.24657v1)
- **Jailbreaking Frontier Foundation Models Through Intention Deception** — [arxiv_cr](https://arxiv.org/abs/2604.24082v1)
- **Reducing Redundancy in Retrieval-Augmented Generation through Chunk Filtering** — [arxiv_cl](https://arxiv.org/abs/2604.24334v1)
- **Less Is More: Engineering Challenges of On-Device Small Language Model Integration in a Mobile Application** — [arxiv_ai](https://arxiv.org/abs/2604.24636v1)
- **Characterizing Vision-Language-Action Models across XPUs: Constraints and Acceleration for On-Robot Deployment** — [arxiv_ai](https://arxiv.org/abs/2604.24447v1)
- **Safeguarding Skies: Airport Cybersecurity in the Digital Age** — [arxiv_cr](https://arxiv.org/abs/2604.23545v1)
- **From Spoofing to Trust: Emergency Alerts Spoofing Testbed and Cross-Cell Verification** — [arxiv_cr](https://arxiv.org/abs/2604.24404v1)
- **SMSI: System Model Security Inference: Automated Threat Modeling for Cyber-Physical Systems** — [arxiv_cr](https://arxiv.org/abs/2604.23905v1)