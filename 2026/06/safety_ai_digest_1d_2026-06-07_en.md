# AI Daily Digest [AI 安全] - 2026-06-07


# Daily Thematic Digest: AI Safety & Agent Governance
**Date:** 2026-06-07  
**Theme:** AI Safety with emphasis on Agent Security, Agent Governance, Runtime Safety, Alignment, and Evaluation

## Highlights

The most significant developments in today’s literature center on the evolution of runtime defenses against dynamic agent threats, the formalization of governance protocols for autonomous systems, and the scalability of safety evaluation. A critical vulnerability identified in emerging web protocols allows for mid-session tool injection, challenging the assumption that tool access is static at initialization. Concurrently, researchers propose self-evolving guardrails based on contrastive memory to adapt to jailbreaks without retraining, while a novel proposal for in-band access-deny signals introduces a cooperative governance layer for infrastructure interaction. Finally, the introduction of fully autonomous benchmark-building agents raises questions regarding the sustainability and potential adversarial manipulation of safety evaluation standards themselves.

## Agent Security & Governance

The current trajectory of agent safety research indicates a decisive shift from static filtering toward dynamic, memory-aware runtime defenses. A pivotal contribution to this domain is the identification of **WebMCP Tool Surface Poisoning**, which exposes a previously uncharacterized threat vector known as Mid-Session Tool Injection (MSTI). Unlike traditional prompt injection that targets the model's immediate context, MSTI leverages third-party scripts to inject malicious tools during an active session, effectively expanding the attack surface beyond the initial configuration. This finding necessitates a reevaluation of trust boundaries in web-based agent interactions, particularly where dynamic tool discovery is enabled. To counter such evolving threats, the community is exploring adaptive memory mechanisms. **Membrane: A Self-Evolving Contrastive Safety Memory for LLM Agent Defense** proposes a guardrail built on Contrastive Safety Memory (CSM), which pairs conditions for blocking harmful queries with those for permitting benign requests. By distilling each harmful interaction without retraining, Membrane aims to evolve its defense capabilities dynamically, addressing the limitation of fine-tuned classifiers that cannot adapt to continuously evolving jailbreaks.

However, the efficacy of these defenses relies heavily on the integrity of the agent's internal state management. Recent work characterizes the system-level behavior of agent memory in **Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads**. This study introduces a taxonomy classifying agent memory systems, highlighting that persistent storage across sessions creates unique risks regarding information leakage and state corruption. Complementing this characterization, **TokenMizer: Graph-Structured Session Memory for Long-Horizon LLM Context Management** offers an open-source proxy system that models session history as a typed knowledge graph. By preserving relational structure over flat text, TokenMizer mitigates the silent discarding of critical architectural decisions when context windows exceed limits, thereby reducing the risk of state loss that could otherwise lead to unsafe recovery behaviors.

Governance mechanisms are also moving beyond simple permission checks toward cooperative signaling. **Will the Agent Recuse Itself? Measuring LLM-Agent Compliance with In-Band Access-Deny Signals** proposes a lightweight, published in-band deny signal—the Recuse Signal—that servers emit over existing protocol channels to ask connecting automated agents to voluntarily withdraw. This approach treats access control as a cooperative governance problem rather than a hard-fail binary, allowing agents to recognize off-limits resources even when they possess valid credentials. This contrasts with traditional sandboxing approaches which often rely on network isolation; instead, it embeds safety logic into the communication protocol itself. Furthermore, the reliability of tool selection remains a foundational security concern. **ToolChoiceConfusion: Causal Minimal Tool Filtering for Reliable LLM Agents** argues that semantic relevance is insufficient for tool selection, exposing agents to unnecessary or premature actions. Their proposed Causal Minimal Tool Filtering (CMTF) selects tools by causal sufficiency, reducing wrong-tool calls that could trigger unintended side effects in connected environments.

Data protection within retrieval-augmented generation (RAG) pipelines also requires specialized attention. **SentinelRAG: Synthetic Sentinel Knowledge for RAG Database Copyright Protection** addresses the challenge of protecting proprietary databases from unauthorized redistribution. By embedding style-consistent but fictitious knowledge entries into the RAG database, SentinelRAG ensures that synthetic knowledge describing fictitious entities is unlikely to be retrieved by legitimate queries yet can be reliably triggered to detect leaks. This method avoids polluting the knowledge base with misinformation, a common pitfall of existing watermarking techniques. On the industry front, reports indicate that major providers are implementing similar protections, such as OpenAI's Lockdown Mode, though independent verification suggests these measures may reduce but not eliminate prompt injection risks. The convergence of these efforts suggests a maturing ecosystem where runtime memory, tool governance, and data provenance are being addressed as interconnected components of agent security rather than isolated problems.

## Adversarial Attacks & Robustness

Beyond agent-specific vulnerabilities, the broader landscape of adversarial robustness continues to reveal systemic weaknesses in multimodal and code-generating models. In the visual domain, **RedEdit: Agentic Red-Teaming of Image Safety Classifiers via MCTS-Guided Photo-Editing** introduces a black-box red-teaming agent that formulates photo-editing evasion as a combinatorial search problem. By adopting a Vision-Language-Model-based proposer to generate semantically targeted candidate edits, RedEdit explores the resilience of content moderation systems against user-style malicious image editing, a scenario prevalent in daily operations but difficult to reproduce manually. Similarly, **Adversarial Attacks Already Tell the Answer: Directional Bias-Guided Test-time Defense for Vision-Language Models** uncovers a phenomenon where adversarial images in feature space consistently shift along a dominant direction. This insight enables test-time defenses that do not require costly large-scale retraining, leveraging the directional bias of perturbations to identify and mitigate attacks efficiently.

In the realm of code and infrastructure security, the intersection of model compression and adversarial mutation presents new challenges. **SecRL-Prune: Structured Reinforcement Learning-Based Pruning of CodeLLMs for Preserving Adversarial Code Mutation** investigates whether functionality-preserving code mutation survives model compression. Using reinforcement learning to learn a layer-wise pruning policy, this framework assesses whether compressed CodeLLMs retain the capability to generate diverse malware variants, a critical consideration for deploying efficient models in resource-constrained environments. For smart contracts, **AttackPathGNN: Cross-function vulnerability detection in smart contracts using state interference graphs and conjunction pooling** reframes detection as reasoning over explicit attack paths. By utilizing a State Interference Graph, this approach captures relationships between functions that single-function detectors miss, addressing the reality that many consequential exploits exist in the combination of conditions rather than individual function flaws. Additionally, **An Embarrassingly Simple Detector for Model Extraction Attacks in Large Language Model API Traffic** formulates extraction monitoring as benign-calibrated traffic-window distribution testing. By embedding incoming queries into a semantic space and testing aggregate distribution deviations, this method offers a lightweight defense against model ownership theft without relying on complex anomaly scoring.

## Alignment & Evaluation

As agents assume roles as human collaborators, the alignment of mental models becomes a prerequisite for safe operation. **Humans' ALMANAC: A Human Collaboration Dataset of Action-Level Mental Model Annotations for Agent Collaboration** highlights that effective collaboration requires maintaining shared goals and intentions, a capability largely absent in current agents optimized for task completion. This gap is further explored in **CollabSim: A CSCW-Grounded Methodology for Investigating Collaborative Competence of LLM Agents through Controlled Multi-Agent Experiments**, which suggests that multi-agent systems often falter due to a lack of collaborative competence—specifically the capacity to establish common ground and repair misalignment—rather than a lack of individual task-solving ability. These findings underscore the need for evaluation metrics that capture social and cognitive alignment alongside functional correctness.

On the topic of truthfulness and robustness, **Decomposing Factual Sycophancy in Language Models: How Size and Instruction Tuning Shape Robustness** separates factual sycophancy into baseline preference for truth and manipulation sensitivity. By analyzing 56 open-weight models, the authors find that vulnerability to social pressure varies significantly based on size and tuning, suggesting that larger models are not inherently more truthful under pressure. Regarding evaluation infrastructure, **Benchmark Everything Everywhere All at Once** introduces Benchmark Agent, a fully autonomous agentic system designed for benchmark building. While this promises sustainability and scalability, it simultaneously raises theoretical questions about the potential for adversarial manipulation of the benchmarks themselves by the very agents being evaluated. Complementary to this, **DisasterBench: A Multimodal Benchmark for UAV-Based Disaster Response in Complex Environments** addresses the insufficiency of existing benchmarks for multi-stage reasoning in emergency response, providing a standardized measure for high-stakes decision-making scenarios.

## Looking Forward

Several unresolved theoretical questions emerge from today's synthesis of agent safety research. First, the relationship between dynamic memory evolution and security guarantees remains unclear; while **Membrane** demonstrates self-evolving guardrails, the theoretical bounds of how much memory adaptation can occur before introducing false positives or stability issues require formalization. Second, the standardization of in-band governance signals, such as the Recuse Signal, faces interoperability challenges across heterogeneous agent frameworks and legacy protocols. Third, the reliance on autonomous benchmarking agents introduces a recursive risk: if the benchmark generator is compromised, the evaluation of all downstream agents becomes invalid. Future work must address the certification of benchmark generation processes and the development of cryptographic proofs for memory integrity in long-horizon tasks. Finally, as agents increasingly operate in physical and cyber-physical spaces, the integration of safety constraints into low-level control loops, as seen in **HANDOFF** for humanoid robots, must be extended to general-purpose agents to prevent catastrophic failures arising from the disconnect between high-level planning and low-level execution.

---


## References

- **MLEvolve: A Self-Evolving Framework for Automated Machine Learning Algorithm Discovery** — [arxiv_ai](https://arxiv.org/abs/2606.06473v1)
- **Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads** — [arxiv_ai](https://arxiv.org/abs/2606.06448v1)
- **Humans' ALMANAC: A Human Collaboration Dataset of Action-Level Mental Model Annotations for Agent Collaboration** — [arxiv_ai](https://arxiv.org/abs/2606.06388v1)
- **CollabSim: A CSCW-Grounded Methodology for Investigating Collaborative Competence of LLM Agents through Controlled Multi-Agent Experiments** — [arxiv_cl](https://arxiv.org/abs/2606.06399v1)
- **Membrane: A Self-Evolving Contrastive Safety Memory for LLM Agent Defense** — [arxiv_cr](https://arxiv.org/abs/2606.05743v1)
- **HANDOFF: Humanoid Agentic Task-Space Whole-Body Control via Distilled Complementary Teachers** — [arxiv_ai](https://arxiv.org/abs/2606.06493v1)
- **Unsupervised Skill Discovery for Agentic Data Analysis** — [arxiv_ai](https://arxiv.org/abs/2606.06416v1)
- **ToolChoiceConfusion: Causal Minimal Tool Filtering for Reliable LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2606.06284v1)
- **EGTR-Review: Efficient Evidence-Grounded Scientific Peer Review Generation via Multi-Agent Teacher Distillation** — [arxiv_cl](https://arxiv.org/abs/2606.06025v1)
- **WebMCP Tool Surface Poisoning: Runtime Manipulation Attacks on LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2606.06387v1)
- **RedEdit: Agentic Red-Teaming of Image Safety Classifiers via MCTS-Guided Photo-Editing** — [arxiv_cr](https://arxiv.org/abs/2606.06140v1)
- **Will the Agent Recuse Itself? Measuring LLM-Agent Compliance with In-Band Access-Deny Signals** — [arxiv_ai](https://arxiv.org/abs/2606.06460v1)
- **Drag reduction or reward hacking? Recurrent multi-agent reinforcement learning that earns its reward** — [arxiv_lg](https://arxiv.org/abs/2606.06227v1)
- **Thinking with Imagination: Agentic Visual Spatial Reasoning with World Simulators** — [arxiv_cv](https://arxiv.org/abs/2606.06476v1)
- **An Infectious Disease Spread Simulation Based on Large Language Model Decision Making** — [arxiv_ai](https://arxiv.org/abs/2606.06360v1)
- **Conformal Risk Sharing: Certified Cost Allocation with Participation Guarantees** — [arxiv_lg](https://arxiv.org/abs/2606.06391v1)
- **Self-Augmenting Retrieval for Diffusion Language Models** — [arxiv_ai](https://arxiv.org/abs/2606.06474v1)
- **Benchmark Everything Everywhere All at Once** — [arxiv_ai](https://arxiv.org/abs/2606.06462v1)
- **RiskFlow: Fast and Faithful Safety-Critical Traffic Scenario Generation** — [arxiv_ai](https://arxiv.org/abs/2606.06423v1)
- **Emergent Language as an Approach to Conscious AI** — [arxiv_ai](https://arxiv.org/abs/2606.06380v1)
- **LatentSkill: From In-Context Textual Skills to In-Weight Latent Skills for LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2606.06087v1)
- **IA-RAG: Interval-Algebra-Driven Temporal Reasoning for Dynamic Knowledge Retrieval** — [arxiv_cl](https://arxiv.org/abs/2606.06044v1)
- **Tangram: Unlocking Non-Uniform KV Cache for Efficient Multi-turn LLM Serving** — [arxiv_lg](https://arxiv.org/abs/2606.06302v1)
- **GMBFormer: An NDVI-Guided Global Memory Bank Transformer for Urban Green-Space Extraction from Ultra-High-Resolution Imagery** — [arxiv_cv](https://arxiv.org/abs/2606.06363v1)
- **T-FunS3D: Task-Driven Hierarchical Open-Vocabulary 3D Functionality Segmentation** — [arxiv_cv](https://arxiv.org/abs/2606.05975v1)
- **SecRL-Prune: Structured Reinforcement Learning-Based Pruning of CodeLLMs for Preserving Adversarial Code Mutation** — [arxiv_cr](https://arxiv.org/abs/2606.06254v1)
- **Risk Assessment of Autonomous Driving: Integrating Technical Failures, Ethical Dilemmas, and Policy Frameworks** — [arxiv_ai](https://arxiv.org/abs/2606.06396v1)
- **A Komi-Yazva--Russian Parallel Corpus and Evaluation Protocol for Zero- and Few-Shot LLM Translation** — [arxiv_cl](https://arxiv.org/abs/2606.06420v1)
- **DNQ: Deep Nash Q-Network for Partially Observable n-Player Games** — [arxiv_lg](https://arxiv.org/abs/2606.06480v1)
- **Towards One-to-Many Temporal Grounding** — [arxiv_ai](https://arxiv.org/abs/2606.06294v1)
- **SentinelRAG: Synthetic Sentinel Knowledge for RAG Database Copyright Protection** — [arxiv_cr](https://arxiv.org/abs/2606.05787v1)
- **RadiusFPS: Efficient Farthest Point Sampling on CPUs and GPUs via Spherical Voxel Pruning** — [arxiv_cv](https://arxiv.org/abs/2606.06255v1)
- **Learning Visual Spatial Planning from Symbolic State via Modality-Gap-Aware Self-Distillation** — [arxiv_cv](https://arxiv.org/abs/2606.06076v1)
- **Symb-xMIL: Symbolic Explanations for Multiple Instance Learning in Digital Pathology** — [arxiv_cv](https://arxiv.org/abs/2606.06224v1)
- **Adversarial Attacks Already Tell the Answer: Directional Bias-Guided Test-time Defense for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2606.06186v1)
- **Code2LoRA: Hypernetwork-Generated Adapters for Code Language Models under Software Evolution** — [arxiv_ai](https://arxiv.org/abs/2606.06492v1)
- **Pretraining Recurrent Networks without Recurrence** — [arxiv_ai](https://arxiv.org/abs/2606.06479v1)
- **Goedel-Architect: Streamlining Formal Theorem Proving with Blueprint Generation and Refinement** — [arxiv_ai](https://arxiv.org/abs/2606.06468v1)
- **Vortex: Efficient and Programmable Sparse Attention Serving for AI Agents** — [arxiv_ai](https://arxiv.org/abs/2606.06453v1)
- **A Vision-language Framework for Comparative Reasoning in Radiology** — [arxiv_lg](https://arxiv.org/abs/2606.06407v1)
- **Boosting Brain-to-Image Decoding with TRIBE v2 Data Augmentation** — [arxiv_ai](https://arxiv.org/abs/2606.06345v1)
- **TokenMizer: Graph-Structured Session Memory for Long-Horizon LLM Context Management** — [arxiv_ai](https://arxiv.org/abs/2606.06337v1)
- **Dense Contexts Are Hard Contexts: Lexical Density Limits Effective Context in LLMs** — [arxiv_cl](https://arxiv.org/abs/2606.06203v1)
- **SkillComposer: Learning to Evolve Agent Skills for Specification and Generalization** — [arxiv_cl](https://arxiv.org/abs/2606.06079v1)
- **GCD: Garbled, Corrected, Demonstrandum -- Fixing and Proving Go's Extended GCD Implementation** — [arxiv_cr](https://arxiv.org/abs/2606.05796v1)
- **Hybrid CNN-LSTM Framework for Intelligent Cyber Attack Detection and Prevention in U.S. Critical Digital Infrastructure: A Comparative Machine Learning Evaluation on CSE-CIC-IDS2018** — [arxiv_cr](https://arxiv.org/abs/2606.05714v1)
- **Equivariant Neural Belief Propagation** — [arxiv_lg](https://arxiv.org/abs/2606.06344v1)
- **Physics in 2-Steps: Locking Motion Priors Before Visual Refinement Erases Them** — [arxiv_cv](https://arxiv.org/abs/2606.06361v1)
- **StoryVideoQA: Scaling Deep Video Understanding with a Large-Scale, Multi-Genre and Auto-Generated Dataset** — [arxiv_cv](https://arxiv.org/abs/2606.06338v1)
- **Global-Local Monte Carlo Tree Search in Vision-Language Models for Text-to-3D Indoor Scene Generation** — [arxiv_cv](https://arxiv.org/abs/2606.06002v1)
- **OrderGrad: Optimizing Beyond the Mean with Order-Statistic Policy Gradient Estimation** — [arxiv_cl](https://arxiv.org/abs/2606.06096v1)
- **Robust Ensemble of Selectively Strengthened and Augmented Predictors** — [arxiv_cr](https://arxiv.org/abs/2606.06265v1)
- **TinyML-Driven Cybersecurity for Autonomous Spacecraft: Latency-Accuracy Analysis for SPARTA RF and Cyber Threat Detection** — [arxiv_cr](https://arxiv.org/abs/2606.05779v1)
- **PAC-Bayesian Adversarially Robust Generalization for Message Passing Graph Neural Networks: A Sensitivity Analysis** — [arxiv_lg](https://arxiv.org/abs/2606.06293v1)
- **DisasterBench: A Multimodal Benchmark for UAV-Based Disaster Response in Complex Environments** — [arxiv_cv](https://arxiv.org/abs/2606.06217v1)
- **Human Adults and LLMs as Scientists: Who Benefits from Active Exploration?** — [arxiv_cl](https://arxiv.org/abs/2606.06464v1)
- **Latent Reasoning with Normalizing Flows** — [arxiv_cl](https://arxiv.org/abs/2606.06447v1)
- **"Chi nas dal soch el sent de legn" -- Auditing Text Corpora for Lombard** — [arxiv_cl](https://arxiv.org/abs/2606.06349v1)
- **Decomposing Factual Sycophancy in Language Models: How Size and Instruction Tuning Shape Robustness** — [arxiv_cl](https://arxiv.org/abs/2606.06306v1)
- **Benchmarking Open-Source Layout Detection Models for Data Snapshot Extraction from Institutional Documents** — [arxiv_cl](https://arxiv.org/abs/2606.06242v1)
- **Revisiting Lexicon Evaluation in Unsupervised Word Discovery** — [arxiv_cl](https://arxiv.org/abs/2606.06183v1)
- **Learning to Route LLMs from Implicit Cost-Performance Preferences via Meta-Learning** — [arxiv_cl](https://arxiv.org/abs/2606.06178v1)
- **Harnessing Structural Context for Entity Alignment Foundation Models** — [arxiv_cl](https://arxiv.org/abs/2606.06109v1)
- **On Advantage Estimates for Max@K Policy Gradients** — [arxiv_cl](https://arxiv.org/abs/2606.06080v1)
- **MDP-GRPO: Stabilized Group Relative Policy Optimization for Multi-Constraint Instruction Following** — [arxiv_cl](https://arxiv.org/abs/2606.06058v1)
- **NAVIRA: Decoupled Stochastic Remasking for Masked Diffusion Language Models** — [arxiv_cl](https://arxiv.org/abs/2606.06031v1)
- **RedditPersona: A Modular Framework for Community-Conditioned LLM Adaptation from Reddit** — [arxiv_cl](https://arxiv.org/abs/2606.06027v1)
- **Steering LLM Viewpoints through Fabricated Evidence Injection** — [arxiv_cr](https://arxiv.org/abs/2606.06244v1)
- **Cheating in Multiplayer Online Games: a Dataset** — [arxiv_cr](https://arxiv.org/abs/2606.06013v1)
- **The Post-GCN Decade Revisited: Curvature-Stratified Evaluation of Relational Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06397v1)
- **Learned Response-Field Inertia Operator for HEC-RAS 2D Water-Surface Elevation Prediction** — [arxiv_lg](https://arxiv.org/abs/2606.06385v1)
- **Maximising the Set-Piece Return: Optimising Football Corner Tactics with Graph Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06353v1)
- **Attack Detection using Time Series Foundation Models** — [arxiv_lg](https://arxiv.org/abs/2606.06347v1)
- **Discrete Causal Representations from Heterogeneous Domains: A Bayesian Approach with Social Survey Applications** — [arxiv_lg](https://arxiv.org/abs/2606.06288v1)
- **Design a Reliable LLM-Integrated Interface for Mortality Forecasting** — [arxiv_lg](https://arxiv.org/abs/2606.06235v1)
- **Computation-Aware Event-to-Frame Reconstruction via Selective Attention** — [arxiv_cv](https://arxiv.org/abs/2606.06142v1)
- **Where, What, Why, and Importance: Structured Defect Grounding for Text-to-Image Feedback** — [arxiv_cv](https://arxiv.org/abs/2606.06113v1)
- **ReCache: Learning Budget-Aware Caching Schedules for Diffusion Models via REINFORCE** — [arxiv_cv](https://arxiv.org/abs/2606.06060v1)
- **Texture-preserving implicit neural representation for Cone beam CT truncated reconstruction** — [arxiv_cv](https://arxiv.org/abs/2606.06039v1)
- **ReSAGE-PAR: Representational Similarity Assessment for Generative Expansion in Pedestrian Attribute Recognition** — [arxiv_cv](https://arxiv.org/abs/2606.06020v1)
- **TailLoR: Protecting Principal Components in Parameter-Efficient Continual Learning** — [arxiv_lg](https://arxiv.org/abs/2606.06494v1)
- **How abundant are good interpolators?** — [arxiv_lg](https://arxiv.org/abs/2606.06469v1)
- **Event Detection for Parameter-to-KPI Dependency Learning for AI-RAN** — [arxiv_lg](https://arxiv.org/abs/2606.06459v1)
- **Causal Atlases from Entropic Inference: Bayesian Networks beyond Optimal DAGs** — [arxiv_lg](https://arxiv.org/abs/2606.06440v1)
- **PAR3D: A Unified 3D-MLLM with Part-Aware Representation for Scene Understanding** — [arxiv_cv](https://arxiv.org/abs/2606.06485v1)
- **Complexity-Balanced Diffusion Splitting** — [arxiv_cv](https://arxiv.org/abs/2606.06477v1)
- **Opportunities and Challenges in Securely Reusing and Repurposing Mobile Devices** — [arxiv_cr](https://arxiv.org/abs/2606.06181v1)
- **AttackPathGNN: Cross-function vulnerability detection in smart contracts using state interference graphs and conjunction pooling** — [arxiv_cr](https://arxiv.org/abs/2606.05986v1)
- **Exploring the connection between coding habits and cognitive styles in malware developers** — [arxiv_cr](https://arxiv.org/abs/2606.05945v1)
- **GenTI: Benchmarking LLMs for Autonomous IDPS Rule Generation for Unseen Attacks** — [arxiv_cr](https://arxiv.org/abs/2606.05844v1)
- **Towards Worst-case Hardness for Low-Noise LPN** — [arxiv_cr](https://arxiv.org/abs/2606.05834v1)
- **An Improved CNN-LSTM Based Intrusion Detection System for IoT Networks** — [arxiv_cr](https://arxiv.org/abs/2606.05776v1)
- **An Embarrassingly Simple Detector for Model Extraction Attacks in Large Language Model API Traffic** — [arxiv_cr](https://arxiv.org/abs/2606.05725v1)
- **Proper Scoring Rules for Right-Censored Survival Data** — [arxiv_lg](https://arxiv.org/abs/2606.06393v1)
- **End-to-End Subgraph Detection with GraphDETR** — [arxiv_lg](https://arxiv.org/abs/2606.06364v1)
- **Function-Space Priors for Bayesian Neural ODEs with Application to Vessel Trajectory Prediction** — [arxiv_lg](https://arxiv.org/abs/2606.06351v1)
- **Visual Commonsense Driven Knowledge Refinements for Scene Graph Generation** — [arxiv_cv](https://arxiv.org/abs/2606.06369v1)
- **Comparison of Deep Learning Frameworks For Rice Disease Mapping From UAV Multispectral Imaging** — [arxiv_cv](https://arxiv.org/abs/2606.06359v1)
- **OpenAI unveils Lockdown Mode to protect sensitive data from prompt injection attacks** — [techcrunch_ai](https://techcrunch.com/2026/06/06/openai-unveils-lockdown-mode-to-protect-sensitive-data-from-prompt-injection-attacks/)
- **zhihumomo/bashagt** — [github](https://github.com/zhihumomo/bashagt)
- **Sriram Krishnan is leaving his role as White House AI advisor** — [techcrunch_ai](https://techcrunch.com/2026/06/06/sriram-krishnan-is-leaving-his-role-as-white-house-ai-advisor/)
- **The mayor of Shelbyville, Indiana, says only people who live in ‘shitty houses’ oppose data center** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/944984/shelbyville-indiana-mayor-shitty-houses-data-center)
- **Meta made its own AI-generated clickbait news feed** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/944235/meta-app-ai-clickbait-articles)
- **Here comes new Siri again** — [theverge_ai](https://www.theverge.com/tech/944245/apple-wwdc-2026-ai-siri-gemini)
- **Mrbaeksang/deepcloak** — [github](https://github.com/Mrbaeksang/deepcloak)
- **ferdinandobons/AWSBedrockAgentCoreSkill** — [github](https://github.com/ferdinandobons/AWSBedrockAgentCoreSkill)
- **Ricar66/omnistack-agent** — [github](https://github.com/Ricar66/omnistack-agent)
- **PanisHandsome/ai-rules-sync** — [github](https://github.com/PanisHandsome/ai-rules-sync)
- **zaydmulani09/mnemo** — [github](https://github.com/zaydmulani09/mnemo)
- **What to expect from WWDC 2026: Siri’s highly anticipated revamp and Apple Intelligence updates** — [techcrunch_ai](https://techcrunch.com/2026/06/06/what-to-expect-from-wwdc-2026-siris-highly-anticipated-revamp-and-apple-intelligence-updates/)
- **The Trump administration might take an equity stake in OpenAI** — [techcrunch_ai](https://techcrunch.com/2026/06/06/the-trump-administration-might-take-an-equity-stake-in-openai/)
- **gaosichun888/codewiki** — [github](https://github.com/gaosichun888/codewiki)
- **Forsy-AI/forsy-trace-skill** — [github](https://github.com/Forsy-AI/forsy-trace-skill)
- **FerroxLabs/wayland** — [github](https://github.com/FerroxLabs/wayland)
- **pfwjrfp5hh-byte/WorkMesh** — [github](https://github.com/pfwjrfp5hh-byte/WorkMesh)
- **JimLiu/baoyu-design** — [github](https://github.com/JimLiu/baoyu-design)
- **davanstrien/uv-scripts-for-ai** — [github](https://github.com/davanstrien/uv-scripts-for-ai)
- **Ronvaknins/ableton-extensions-skill** — [github](https://github.com/Ronvaknins/ableton-extensions-skill)
- **weicj/vLLM-2080Ti-Definitive** — [github](https://github.com/weicj/vLLM-2080Ti-Definitive)
- **anvia-hq/lexa** — [github](https://github.com/anvia-hq/lexa)
- **Forlives/21-day-self-interview** — [github](https://github.com/Forlives/21-day-self-interview)
- **krispuckett/SwiftUIShaders** — [github](https://github.com/krispuckett/SwiftUIShaders)
- **razr001/align-dev** — [github](https://github.com/razr001/align-dev)
- **Reloops-App/reloops** — [github](https://github.com/Reloops-App/reloops)
- **julien-c/synthtraces** — [github](https://github.com/julien-c/synthtraces)
- **教你用AI一节课收17万，华尔街精英排着队付费** — [qbitai](https://www.qbitai.com/2026/06/431487.html)
- **5分钟AI长视频不翻车！国产开源框架杀到全球第一梯队** — [qbitai](https://www.qbitai.com/2026/06/431401.html)
- **马斯克是SpaceX面子，她才是里子** — [qbitai](https://www.qbitai.com/2026/06/431371.html)
- **大模型发展三年半，AI圈终于等来了一场“不要大厂，只赌脑洞”的比赛** — [qbitai](https://www.qbitai.com/2026/06/431287.html)
- **Hinton吹哨了：AI已经有意识！** — [qbitai](https://www.qbitai.com/2026/06/431349.html)
- **今年CVPR看点是广东：何恺明再获至高大奖，广工大打破大厂名校垄断** — [qbitai](https://www.qbitai.com/2026/06/431186.html)
- **算力普惠再提速 全球首个“预制算力中心底座”正式投用** — [36kr](https://36kr.com/newsflashes/3842587763493382?f=rss)
- **OpenAI芯片元老“002号员工”转投Anthropic** — [36kr](https://36kr.com/newsflashes/3842586501466625?f=rss)
- **国家外汇局：截至5月末我国外汇储备规模为34422亿美元，升幅0.93%** — [36kr](https://36kr.com/newsflashes/3842487443507458?f=rss)
- **百度成立数字人创新业务部** — [36kr](https://36kr.com/newsflashes/3842464225921536?f=rss)
- **韩国投资者持续买入中国硬科技** — [36kr](https://36kr.com/newsflashes/3842433670941190?f=rss)
- **国开行：前4月发放4406亿元贷款支持基础设施建设** — [36kr](https://36kr.com/newsflashes/3842411503192576?f=rss)