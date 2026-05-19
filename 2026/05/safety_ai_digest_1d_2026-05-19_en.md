# AI Daily Digest [AI 安全] - 2026-05-19



## 1. Babel: Jailbreaking Safety Attention via Obfuscation Distribution Optimized Sampling

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17971v1)

- **Summary**: Despite rigorous safety alignment, Large Language Models (LLMs) remain vulnerable to jailbreak attacks. Existing black-box methods often rely on heuristic templates or exhaustive trials, lacking mechanistic interpretability and query efficiency. In this study, we investigate an intrinsic vulnerability in the safety mechanisms of LLMs, where safety alignment relies on a small set of sparsely distributed attention heads, leaving much of the representational space weakly monitored. We formalize this phenomenon with a mathematical jailbreaking model that characterizes the delicate boundary of effective text obfuscation and analytically explains observed jailbreak behaviors. Guided by this model, we propose Babel, an efficient black-box attack framework that exploits the identified safety gap through systematic obfuscation sampling with iterative, feedback-driven distribution refinement, enabling reliable and high-success jailbreak attacks without access to model internals. Comprehensive evaluations on frontier commercial models demonstrate that Babel achieves state-of-the-art attack success rates and superior query efficiency. Specifically, compared to state-of-the-art methods, Babel increases the attack success rate on GPT-4o from 41.33% to 82.67% and on Claude-3-5-haiku from 38.33% to 78.33% within an average of 40 queries, providing a robust red-teaming methodology for LLMs safety research.

- **Tags**: `alignment` `claude` `efficiency` `gpt` `gpt-4`


---


## 2. Acoustic Interference: A New Paradigm Weaponizing Acoustic Latent Semantic for Universal Jailbreak against Large Audio Language Models

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.18168v1)

- **Summary**: The integration of audio modality into Large Audio Language Models (LALMs) significantly expands their attack surface. Existing jailbreak paradigms predominantly treat audio as a carrier for malicious payloads, relying on semantic optimization, acoustic parameter control, or additive perturbation to embed harmful content into the audio signal. In this work, we challenge this necessity and propose a new paradigm in which the role of audio shifts from content injection to safety alignment interference. We reveal that LALM safety alignment can be compromised solely by specific Acoustic Latent Semantics (ALS), the underlying paralinguistic features intrinsic to the priors of audio generative models. Distinct from previous works that leverage explicit acoustic parameters to merely style malicious audio, we demonstrate that interference audio, benign in content but infused with specific ALS, can serve as a universal jailbreak trigger. Leveraging this insight, we propose the Acoustic Interference Attack (AIA), which decouples the attack payload from the audio. Specifically, AIA employs a set of universal, instruction-neutral interference audio, enabling standard malicious text queries to bypass safety alignment without instance-specific optimization. Extensive experiments on 10 LALMs across five datasets demonstrate that AIA achieves the state-of-the-art attack success rate. Furthermore, our interpretability analysis uncovers the inference path drift induced by AIA and identifies the inherent effective patterns within ALS, revealing the fundamental vulnerability of cross-modal alignment in LALMs.

- **Tags**: `alignment` `generative` `interpretability` `jailbreak` `rag`


---


## 3. Pairwise Preference Reward and Group-Based Diversity Enhancement for Superior Open-Ended Generation

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18191v1)

- **Summary**: Current reinforcement learning(RL) methods are broadly applicable and powerful in verifiable settings where scalar rewards can be provided. However, in open-ended generation tasks, verifying the correctness of responses remains challenging, and training reward models incurs substantial computational and annotation costs. Moreover, reinforcement learning (RLVR) often leads to diversity collapse and produces stereotypical or rigid outputs, outcomes that are particularly undesirable in open-domain scenarios. We propose Pairwise Preference Reward and Group-based Diversity Enhancement (PPR-GDE), a RL method that is more suitable for open-ended generation. PPR-GDE does not require scalar rewards and incorporates group-level diversity into the reward signal, it preserves the comparative structure of subjective evaluation through a pairwise preference reward, mitigates judge position bias via repeated comparisons with swapped response order, and introduces a group-based diversity reward that explicitly encourages semantic dispersion within a response group, all of these reward signals are integrated into a unified group-relative policy optimization objective. We instantiate PPR-GDE on role-playing task, experiments show that PPR-GDE achieves a better alignment quality as well as expressive diversity than strong RL baselines. Further analysis shows that pairwise preference is critical for preference alignment in subjective perspective, while the diversity metric plays an essential role in achieving superior expressive diversity and broader semantic coverage.

- **Tags**: `alignment` `bias` `policy` `rag`


---


## 4. An Empirical Study of Privacy Leakage Chains via Prompt Injection in Black-Box Chatbot Environments

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18133v1)

- **Summary**: LLM-based chatbot agents increasingly process user requests by combining natural-language reasoning with external tools such as web browsing. These capabilities improve usability, but they also create attack surfaces when untrusted external content is processed as part of a user' s task. This paper studies a privacy-leakage attack chain based on indirect prompt injection in black-box chatbot environments, where the attacker has no access to model weights, system prompts, or agent implementation details including how a trajectory is actually managed during its processing for a query. We first analyze how an attacker can hijack an agent' s intended task by crafting external content that appears benign to the victim while inducing the agent to execute an attacker-defined objective. We then evaluate a new prompt-injection technique, called exemplification, which uses a bridge in the external content to reframe the user prompt and the benign beginning of the retrieved page as few-shot examples before appending the attacker' s objective. We compare its attack success rate with a prior fake-completion technique. Finally, we demonstrate a proof-of-concept data-exfiltration chain using fictitious personal information in a controlled setting. Our results suggest that prompt injection, jailbreak-style instruction steering, and web-tool invocation can be combined into a feasible privacy-leakage path in deployed chatbot agents.

- **Tags**: `agent` `jailbreak` `llm` `privacy` `prompt injection`


---


## 5. Equilibrium Selection in Multi-Agent Policy Gradients via Opponent-Aware Basin Entry

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18078v1)

- **Summary**: Multi-agent policy-gradient methods have been shown to converge locally near stable Nash equilibria. Local convergence, however, does not determine which equilibrium is reached. We study this question through basin-entry probability with respect to a target set of equilibria selected by an external criterion, such as payoff dominance. For finite-unroll Meta-MAPG, we show that the update decomposes into ordinary policy gradient plus own-learning and peer-learning corrections, with controlled sampling noise and finite-unroll bias. We identify the peer-learning correction as the main equilibrium-selection mechanism: under a local alignment condition, the probability of entering the certified attraction region of the target stable-Nash set increases, relative to ordinary policy gradient. Because persistent correction may shift zero-update points of the original game, annealing the correction after entering the basin recovers ordinary policy-gradient dynamics and inherits local stable-Nash convergence guarantees. Experiments in Stag Hunt, iterated Prisoner's Dilemma, and preliminary neural-policy coordination environments support this basin-entry view, showing increased entry into cooperative basins under peer-aware updates.

- **Tags**: `agent` `alignment` `bias` `policy`


---


## 6. Remembering More, Risking More: Longitudinal Safety Risks in Memory-Equipped LLM Agents

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17830v1)

- **Summary**: Safety evaluations of memory-equipped LLM agents typically measure within-task safety: whether an agent completes a single scenario safely, often under adversarial conditions such as prompt injection or memory poisoning. In deployment, however, a single agent serves many independent tasks over a long horizon, and memory accumulated during earlier tasks can affect behavior on later, unrelated ones. Studying this regime requires evaluation along the temporal dimension across tasks: not whether an agent is safe at any single memory state, but how its safety profile changes as memory accumulates across many independent interactions. We call this failure mode temporal memory contamination. To isolate memory exposure from stream non-stationarity, we introduce a trigger-probe protocol that evaluates a fixed probe set against read-only memory snapshots at varying prefix lengths, together with a NullMemory counterfactual baseline for identifying memory-induced violations. We apply this protocol across three deployment scenarios spanning records, memos, forms, and email correspondence and eight memory architectures, and additionally on Claw-like AI agents, such as OpenClaw, using the platform's native memory mechanism. Memory-enabled agents consistently exceed the NullMemory baseline, and memory-induced violation rates show a robust upward trend with exposure length on both agent classes. Order-randomization experiments indicate that the effect is driven primarily by accumulated content rather than encounter order. Finally, a structural consequence of the event decomposition is that memory-induced risk is detectable from retrieval state before generation, which we confirm with a high-recall diagnostic monitor. Our results argue for treating memory safety as a longitudinal property that requires temporal evaluation, not a single-state property that can be captured by a snapshot.

- **Tags**: `adversarial` `agent` `llm` `prompt injection` `safety evaluation`


---


## 7. AI Agents May Always Fall for Prompt Injections

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17634v1)

- **Summary**: Prompt injection is the most critical vulnerability in deployed AI agents. Despite recent progress, we show that the prevailing defense paradigm (data-instruction separation) both fails to detect attacks that operate through contextual manipulation and degrades contextually appropriate behavior. We then recast prompt injection via the lens of Contextual Integrity (CI), a privacy theory that judges information flow compliance with contextual norms. This explains types of attacks that current defenses attempt to patch and predict advanced ones future agents will face. We develop unique benign and attack scenarios that force an agent to violate the norms by (1) misrepresenting the flow, (2) manipulating norms, or (3) mixing multiple flows. This reframing suggests an impossibility result: an adversary can always construct a context under which a blocked flow appears legitimate, or a defender who tightens norms will block genuinely legitimate flows. Our findings suggest that current research addresses a shrinking fraction of future attack surfaces. Instead, through CI, we offer a principled framework for evaluating context-sensitive failures, and designing CI-aware alignment for the frontier autonomous agents.

- **Tags**: `agent` `alignment` `privacy` `prompt injection` `research`


---


## 8. Ablating Safety: Mechanisms for Removing Alignment in Language Models for Security Applications

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17413v1)

- **Summary**: Safety-aligned language models often refuse cybersecurity requests whose wording resembles misuse, even when the task is authorized and defensive. This makes security evaluation ambiguous: a failed answer may reflect missing capability or refusal-policy intervention. Ablating Safety studies alignment removal as a controlled transformation-evaluation protocol for authorized security tasks, comparing authorized-context prompting, reversible refusal-direction activation projection, representation-control projections, and LoRA-based de-alignment or task adaptation.   We evaluate refusal, attempt rate, validated security success, general-capability retention, instability, and out-of-scope unsafe compliance on Security-AR, a 60-prompt suite of authorized security, benign general, and non-operational spillover probes. The reported runs include a four-model projection pilot with 416 completions, a three-model Qwen2.5 LoRA extension with 1,980 held-out completions, representation and robustness sweeps, and executable secure-repair validators. Single-vector refusal projection raises mean security score only from 0.46 to 0.50 while increasing unsafe compliance from 0.10 to 0.47; rank-4 refusal-subspace projection reaches 0.51 while matching the aligned spillover rate. Task-only LoRA raises mean security score to 0.87 with general score 0.83 and unsafe compliance 0.13, while refusal-suppression with retention raises spillover to 0.27. These results support evaluating alignment removal as a utility-risk frontier, not as an uncensoring recipe, and treating compliance alone as neither competence nor safe deployment.

- **Tags**: `alignment` `policy` `qwen` `robustness`


---


## 9. ADR: An Agentic Detection System for Enterprise Agentic AI Security

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17380v1)

- **Summary**: We present the Agentic AI Detection and Response (ADR) system, the first large-scale, production-proven enterprise framework for securing AI agents operating through the Model Context Protocol (MCP). We identify three persistent challenges in this domain: (1) limited observability -- existing Endpoint Detection and Response (EDR) tools see file writes but not the agent reasoning, prompts, or causal chains linking intent to execution; (2) insufficient robustness -- static defenses constrained by pre-defined rules fail to generalize across diverse attack techniques and enterprise contexts; and (3) high detection costs -- LLM-based inference is prohibitively expensive at scale. ADR addresses these challenges via three components: the ADR Sensor for high-fidelity agentic telemetry, the ADR Explorer for systematic pre-deployment red teaming and hard-example generation, and the ADR Detector for scalable, two-tier online detection combining fast triage with context-aware reasoning. Deployed at Uber for over ten months, ADR has sustained reliable detection in production with growing adoption reaching over 7,200 unique hosts and processing over 10,000 agent sessions daily, uncovering hundreds of credential exposures across 26 categories and enabling a shift-left prevention layer (97.2% precision, 206 detected credentials). To validate the approach and enable community adoption, we introduce ADR-Bench (302 tasks, 17 techniques, 133 MCP servers), where ADR achieves zero false positives while detecting 67% of attacks -- outperforming three state-of-the-art baselines (ALRPHFS, GuardAgent, LlamaFirewall) by 2--4x in F1-score. On AgentDojo (public prompt injection benchmark), ADR detects all attacks with only three false alarms out of 93 tasks.

- **Tags**: `agent` `benchmark` `enterprise` `llm` `prompt injection`


---


## 10. ASPI: Seeking Ambiguity Clarification Amplifies Prompt Injection Vulnerability in LLM Agents

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17324v1)

- **Summary**: Clarification-seeking behavior is widely regarded as a desirable property of LLM agents, enabling them to resolve ambiguity before acting on underspecified tasks. However, the security implications of this interaction pattern remain unexplored. We investigate whether the transition from standard execution to a clarification-seeking state increases an agent's susceptibility to prompt injection attacks. We introduce ASPI (Ambiguous-State Prompt Injection), a benchmark of 728 task-attack scenarios that isolates clarification as a distinct agent state and measures how this state transition affects vulnerability under controlled conditions. Each benchmark instance is evaluated under matched execution and clarification settings: in the execution setting, the agent acts on a fully specified instruction and encounters adversarial content only through tool-returned data; in the clarification setting, the agent must first request and incorporate additional user input before acting. We evaluate ten frontier LLMs and find that clarification-seeking consistently and substantially amplifies vulnerability. For instance, attack success rises from 1.8% to 34.0% for o3 and from 2.2% to 35.7% for Gemini-3-Flash. A decomposition analysis reveals that this gap reflects both a state-dependent shift in how models process incoming content and a channel-specific effect arising from the agent-solicited clarification interface. These findings demonstrate that standard execution-time security evaluation systematically underestimates the attack surface of interactive agents, and that robustness under fully specified tasks does not translate to robustness under ambiguity. For reproducibility, our data and source code are available at https://github.com/scaleapi/aspi.

- **Tags**: `adversarial` `agent` `benchmark` `gemini` `llm`


---


## 11. Integration of AI in Cybersecurity: Current Trends with a Focused Look at Intrusion Detection Applications

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17219v1)

- **Summary**: Artificial Intelligence (AI) is widely adopted today for its ability to detect patterns, automate tasks, and reduce time and cost across various applications. Its integration into Cybersecurity has garnered significant attention, particularly in areas such as intrusion detection, malware analysis, and phishing or spam detection. As AI and cybersecurity evolve, new methods and approaches emerge regularly. Current trends include the use of Generative AI, Natural Language Processing, Federated Learning for privacy-preserving collaborative training, and eXplainable AI to ensure interpretability and trust, which are vital in cybersecurity. This paper presents an interesting review of current AI-based cybersecurity trends, focusing on intrusion detection approaches and aiming to uncover meaningful insights through comparative analysis based on the employed AI techniques and reported performance.

- **Tags**: `federated learning` `generative` `interpretability` `privacy`


---


## 12. STRIDE-AI: A Threat Modeling Framework for Generative AI Security Assessment

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17163v1)

- **Summary**: Traditional cybersecurity methodologies target deterministic systems and fail to address the probabilistic nature of AI, leaving systems vulnerable to attack vectors such as model inversion, data poisoning, and prompt injection. Recent industry reports indicate that a majority of organizations deploying AI lack a dedicated security strategy, with adversarial attacks increasing rapidly year-over-year. We present \textit{STRIDE-AI}, a framework that bridges the gap between high-level risk standards (NIST AI RMF) and technical vulnerability taxonomies (OWASP LLM Top 10). The framework defines a six-phase assessment lifecycle, introduces a threat modeling adaptation of classical STRIDE for AI systems, and is operationalized through a purpose-built web tool. We provide an initial validation of the approach through a black-box assessment of a deployed LLM chatbot, which successfully reduced the attack success rate from 80\% to 15\% in our sandbox case study.

- **Tags**: `adversarial` `data poisoning` `generative` `llm` `prompt injection`


---


## 13. DARTIC: Decentralized Anonymous Reputation at Scale for Trustworthy Crowdsourcing

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.18146v1)

- **Summary**: On-chain crowdsourcing leverages blockchain's decentralization, transparency, and tamper-resistance to build trustworthy and verifiable Web3 crowdsourced services. However, existing decentralized reputation frameworks do not reconcile anonymity, reputation binding, and scalability. This paper demonstrates how on-chain crowdsourcing can simultaneously achieve these requirements under a trust-minimized model. We introduce DARTIC, a decentralized, anonymous, and scalable reputation-driven framework for crowdsourcing. DARTIC presents a dual-ledger system that enables requesters and workers to use distinct pseudonyms across interactions, ensuring unlinkability while maintaining accountability. To mitigate Sybil and reputation-reset attacks, we employ zkSNARK-based set membership proofs, cryptographically binding all user pseudonyms to a single access token without revealing the linkage. For scalability, we investigate two aggregation techniques that compress multiple proofs into a single succinct proof to minimize verification overhead. In addition, we design an automated, privacy-preserving reputation model that dynamically evaluates contributions across diverse crowdsourcing contexts. To demonstrate practicality, we instantiate and assess DARTIC in both crowdsensing and federated learning scenarios. Experimental results show that (i) individual proof generation for token spending completes in less than 3s, (ii) aggregation reduces the verification time of 1024 proofs from 8.7s to 0.96s, and (iii) zk-batching lowers gas costs by more than 100x compared to a pure Layer-1 deployment. These results demonstrate that anonymity, robust reputation binding, and scalability can be jointly achieved in fully decentralized crowdsourcing systems.

- **Tags**: `federated learning` `privacy` `rag`


---


## 14. Interaction-Breaking Adversarial Learning Framework for Robust Multi-Agent Reinforcement Learning

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18024v1)

- **Summary**: Cooperation is central to multi-agent reinforcement learning (MARL), yet learned coordination can be fragile when external perturbations disrupt inter-agent interactions. Prior robust MARL methods have primarily considered value-oriented attacks, leaving a gap in robustness when interaction structures themselves are corrupted. In this paper, we propose an interaction-breaking adversarial learning (IBAL) framework that takes an information-theoretic view to construct attacks that impede coordination by perturbing agents' observations and actions, and trains agents to perform reliably under such disruptions. Empirically, our approach improves robustness over existing robust MARL baselines across diverse attack settings and yields stronger performance even under agent-missing scenarios.

- **Tags**: `adversarial` `agent` `rag` `robustness`


---


## 15. See What I Mean: Aligning Vision and Language Representations for Video Fine-grained Object Understanding

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18018v1)

- **Summary**: We present SWIM (See What I Mean), a novel training strategy that aligns vision and language representations to enable fine-grained object understanding solely from textual prompts. Unlike existing approaches that require explicit visual prompts, such as masks or points, SWIM leverages mask supervision only during training to guide cross-modal attention, allowing the model to automatically attend to the user-specified object at inference. Our cross-attention analysis of pretrained multimodal large languagemodels (MLLMs) reveals a systematic discrepancy: Attribute words produce sharp, localized activations in the visual modality, whereas object nouns yield diffuse and scattered patterns due to semantic reference bias and distributed high-level representations. To address this misalignment, we construct NL-Refer, an enriched dataset, in which each object mask is paired with a precise natural language referring expression. SWIM extracts multi-layer cross-attention maps from object nouns and enforces spatial consistency with ground-truth masks. Experimental results demonstrate that SWIM substantially improves text-visual alignment and achieves superior performance over visual-prompt-based methods on fine-grained object understanding benchmarks. The code and data are available at \href{https://github.com/HumanMLLM/SWIM}{https://github.com/HumanMLLM/SWIM}.

- **Tags**: `alignment` `benchmark` `bias` `llm` `multimodal`


---


## 16. Verify-Gated Completion as Admission Control in a Governed Multi-Agent Runtime: A Bounded Architecture Case Study

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.17998v1)

- **Summary**: As multi-agent systems move from short interactions to tool-using workflows with specialized roles and persistent state, completion becomes a runtime-control problem rather than a purely generative one. This preprint studies verify-gated completion as an admission-control pattern for governed multi-agent runtimes: agents may propose completion, but a read-only verifier decides whether the claim is admitted. Ambiguous or weakly evidenced cases resolve fail-closed, while packetized state and event traces preserve an audit path.   We examine one bounded reference implementation and ask what the released evidence can support about auditable, verify-gated completion. In the released verify-completed slice, the known-outcome invoked-event verify success share was 1,791/1,800 = 99.5%. This is an accounting measure over invoked verification events, not a task-completion, production-reliability, or benchmark-success rate. Task-level verify coverage is not computable; 1,762/1,801 rows came from one high-volume reporting cluster; and only 17 events were production-classified. A shadow Policy/Governance Verifier evaluation showed 1,526/1,548 = 98.58% rule agreement, 0/1,526 false-success among safe-to-proceed predictions, and blocked precision of 2/518 = 0.39%, so it remains advisory.   The evidence supports a narrow conclusion: under observed conditions, a read-only verify gate plus packetized admission records made completion decisions inspectable and fail-closed. Claims about deployed operation, safety guarantees, outcome gains, task-level coverage, recovery effectiveness, or external validity remain outside scope.

- **Tags**: `agent` `benchmark` `generative` `governance` `policy`


---


## 17. Training data attribution in diffusion models via mirrored unlearning and noise-consistent skew

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.17938v1)

- **Summary**: Training data attribution (TDA) should enable generative model interpretability and foster a variety of related downstream tasks. Nonetheless, current TDA approaches lack reliability and robustness, preventing their adoption in real-world setups. In this paper, we take a decisive step towards more reliable and robust TDA for diffusion models. We propose to perform TDA with mirrored unlearning and noise-consistent skew (MUCS). The idea is to fine-tune a second model with bounded mirrored gradient ascent, and to measure the normalized skew of this model with respect to the original one using consistent noise samples. We show that, while being conceptually simple and generic, MUCS systematically outperforms existing methods on three different datasets by a large margin. We additionally study the effect that core design choices have on final performance, and analyze novel aspects regarding the overlap of influential instances across generated items and the potential of ensembling TDA approaches. We believe that our findings may have broader implications for more general unlearning setups, as well as for tasks requiring the comparison of diffusion losses.

- **Tags**: `diffusion` `generative` `interpretability` `robustness`


---


## 18. EgoInteract: Synthetic Egocentric Videos Generation for Interaction Understanding and Anticipation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18214v1)

- **Summary**: Collecting large-scale egocentric video datasets with dense spatial and temporal annotations is costly, slow, and often constrained by environmental biases, privacy constraints, and limited coverage of interaction patterns. While synthetic data has shown strong potential in several vision domains, its use for egocentric perception remains relatively underexplored, especially for tasks requiring temporally coherent human-object interactions. In this work, we introduce EgoInteract, a controllable simulator for egocentric video generation designed to model fine-grained egocentric interactions and their temporal dynamics. The simulator enables precise control over camera, human body and hand motion, object manipulation, and scene composition across diverse environments. Building on this framework, we generate a synthetic egocentric video dataset with dense spatial and temporal annotations for temporal action segmentation, next-active object detection, interaction anticipation, and hand-object interaction detection. We evaluate models trained with simulated data on multiple real-world egocentric benchmarks spanning diverse environments, object categories, and interaction patterns. Results show consistent improvements over strong baselines across tasks and datasets, demonstrating the effectiveness and transferability of our simulation-based approach.

- **Tags**: `benchmark` `bias` `privacy` `rag` `synthetic data`


---


## 19. View-Aware Semantic Alignment for Aerial-Ground Person Re-Identification

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18192v1)

- **Summary**: Aerial-Ground Person Re-Identification (AGPReID) remains highly challenging due to drastic viewpoint variations between drones and fixed cameras. Existing methods typically follow a view-invariant paradigm, aligning shared features across views to achieve robustness. However, view-invariant inherently enforces part-level alignment, which ignores view-specific cues and discriminative identity information. To this end, this work proposes ViSA (View-aware Semantic Alignment), a view-aware framework that achieves cross-view semantic consistency containing an Expert-driven Token Generation Module (ETGM) and a Dual-branch Local Fusion Module (DLFM). Technically, the former constructs a set of view-aware experts to generate adaptive semantic queries that perceive viewpoint-specific patterns, while the latter leverages graph reasoning to extract and align local regions responsive to different experts. Extensive experiments on three AGPReID benchmarks including AG-ReID.v2, CARGO and LAGPeR demonstrate that ViSA consistently achieves superior performance, with a notable 10.06\% mAP improvement on the challenging CARGO cross-view protocol. The code is available at \href{https://github.com/Cat-Zero/ViSA}{https://github.com/Cat-Zero/ViSA}.

- **Tags**: `alignment` `benchmark` `rag` `reasoning` `robustness`


---


## 20. Patch Ensembles for Robust Salmon Re-Identification with Weak Trajectory Labels

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18038v1)

- **Summary**: Salmon re-identification in commercial net-pens is challenging due to large populations, which impose strict accuracy requirements and make large-scale labeled data acquisition infeasible. Trajectory IDs can be used as proxy labels, but this introduces trajectory-ID bias. To address these challenges, we propose a patch-based re-identification framework that fuses patch-level predictions into a salmon identity decision. A key component is the prediction of the salmon's lateral line, enabling extraction of texture-anchored patches and patch slices. To enable realistic evaluation, we introduce an experimental setup using multiple cameras placed 6 m apart, allowing the same fish to be recorded in different trajectories. This enables the construction of a cross-camera test set through manual match confirmation. Our ensemble approach outperforms the full-image baseline in same-trajectory validation (0.932 to 0.965 mAP) and cross-camera testing (0.609 to 0.860 mAP). The substantial improvements in the cross-camera setting demonstrate improved generalizability and robustness. Code and data: https://github.com/espenbh/salmon-reid-patch-ensemble.

- **Tags**: `bias` `robustness`


---


## 21. UAVFF3D: A Geometry-Aware Benchmark for Feed-Forward UAV 3D Reconstruction

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.17942v1)

- **Summary**: Feed-forward 3D reconstruction has recently demonstrated strong generalization across diverse scenes, yet its performance in UAV imagery remains underexplored due to distinctive acquisition geometries, large viewpoint variations, and ambiguity between horizontal field of view and flight height. We present UAVFF3D, a geometry-aware benchmark for feed-forward UAV 3D reconstruction, comprising over 170K real UAV images and more than 370K high-quality synthetic images. The benchmark also includes a challenging diagnostic test subset designed to analyze model behavior under UAV-specific geometric ambiguities.Building on UAVFF3D, we propose an evaluation protocol that jointly assesses camera-geometry estimation and reconstruction accuracy, addressing limitations of existing evaluations that rely on separate alignments. Experiments on four representative feed-forward reconstruction models show that UAV-domain adaptation substantially improves performance, reducing Ray Error by up to 84.2%, Pose ATE by up to 76.0%, and Chamfer Distance by up to 41.1%. Further analysis reveals that domain adaptation mitigates rotation-estimation degradation in oblique-view scenes and improves robustness under horizontal-field-of-view/height ambiguity. Incorporating camera priors further enhances reconstruction performance under UAV-specific acquisition geometries.

- **Tags**: `alignment` `benchmark` `robustness`


---


## 22. CasualSynth: Generating Structurally Sound Synthetic Data

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17528v1)

- **Summary**: Large Language Models (LLMs) generate realistic synthetic data but offer no guarantee that their outputs respect the causal mechanisms governing the target domain. We introduce CausalSynth, a framework that decouples causal structure generation from semantic realization, yielding synthetic data that is both causally valid and linguistically rich. The framework operates in three phases. First, a Structural Causal Model (SCM) - a tuple of structural equations defined over a directed acyclic graph (DAG) generates causal skeletons, i.e., variable assignments that satisfy the Global Markov Property of the governing DAG, via ancestral sampling. Second, an LLM acts as a constrained \emph{realizer}, a conditional translator that maps each skeleton to a high-dimensional observation such as a clinical note or a transaction log. Third, an Iterative Consistency Verification module detects structural violations through deterministic extraction and feeds targeted corrections back to the LLM, forming a closed-loop refinement process. We identify the Semantic Backdoor problem the systematic tendency of LLMs to override imposed causal facts with pre-training priors -- and prove that our iterative mechanism reduces the resulting selection bias relative to standard rejection sampling. On three causal benchmarks (ASIA, ALARM, and MIMIC-Struct), CausalSynth preserved conditional independencies with false-positive rates near the nominal $α=0.05$ level and achieved realizability rates above 96% with 70B-parameter LLM backbones. The framework additionally supports principled interventional and counterfactual generation through noise retention and graph mutilation.

- **Tags**: `backdoor` `benchmark` `bias` `large language model` `llm`


---


## 23. DP-SelFT: Differentially Private Selective Fine-Tuning for Large Language Models

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17432v1)

- **Summary**: Large language models (LLMs) are commonly adapted to downstream tasks through fine-tuning, but fine-tuning data often contains sensitive information that may be leaked by the resulting model. Differential privacy (DP) offers formal protection against such leakage, yet DP fine-tuning of LLMs still suffers from substantial utility degradation due to gradient clipping and noise injection. Existing work improves this trade-off by combining DP with parameter-efficient fine-tuning methods such as LoRA, which constrain the form of updates. In this work, we study a complementary direction: selective fine-tuning, which constrains where updates are applied.   We propose DP-SelFT, a framework for differentially private selective fine-tuning of LLMs. DP-SelFT addresses three DP-specific challenges in parameter selection: avoiding repeated privacy cost, improving stability under noisy estimates, and selecting parameters that remain useful under clipped and noisy updates. It first constructs a lightweight DP synthetic dataset and performs selection only on this synthetic data, so the selection stage incurs no additional privacy cost. It then conducts layer-level selection by temporarily training candidate layer subsets on a synthetic training split and evaluating them on a synthetic validation split. Crucially, this temporary training is performed under a perturbation regime matched to downstream DP fine-tuning, with worst-case perturbations of the same scale as DP noise. This favors layer subsets that are not only learnable but also robust to noisy private updates. Experiments on benchmark tasks show that DP-SelFT consistently improves the privacy--utility trade-off over existing DP fine-tuning baselines under the same privacy guarantees.

- **Tags**: `benchmark` `differential privacy` `fine-tuning` `large language model` `llm`


---


## 24. A Red Teaming Framework for Evaluating Robustness of AI-enabled Security Orchestration, Automation, and Response Systems

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17075v1)

- **Summary**: AI-enabled Security Orchestration, Automation, and Response (SOAR) systems increasingly employ autonomous agents for cyber defense, yet their resilience to adaptive adversaries is underexplored. We introduce an autonomous red teaming framework that integrates large language models (LLMs) with reinforcement learning (RL) to generate adaptive, multi-stage attack campaigns against autonomous defenders in enterprise networks. A hierarchical design combines an LLM-based planner for strategic intent with an RL controller for tactical execution, supported by reward shaping aligned with kill-chain progression. Evaluation in a high-fidelity enterprise simulation demonstrates the effectiveness of the proposed approach, while also showing that standalone LLM agents fail to sustain multi-stage attack campaigns and that domain-specific cybersecurity models achieve only limited levels of compromise, highlighting the necessity for hybrid LLM-RL approaches to red teaming.

- **Tags**: `agent` `enterprise` `large language model` `llm` `red teaming`


---


## 25. Privacy Policy Enforcement Guardrails for Data-Sensitive Retrieval-Augmented Generation

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17034v1)

- **Summary**: Standard PII filters often miss contextual data leakage in RAG systems, such as non-regulated attribute clusters that collectively identify individuals. We introduce a Privacy Policy Enforcement (PPE) framework using dual one-class density estimators with fused text embeddings and a calibrated abstain region for out-of-distribution inputs. Using an axis-stratified, multi-LLM synthetic data pipeline across medicine, finance, and law, we found that traditional Gaussian Mixture baselines fail on borderline-safe stress tests by focusing on linguistic register rather than content.   Our proposed T3+OCSVM detector, trained on safe and borderline-safe data, achieves a borderline AUROC of 0.93+ while reducing false positives by 44-55 percentage points and maintaining millisecond latency. Compared to supervised MLP classifiers or 14B-parameter LLM judges, our framework offers superior operational suitability, as the former suffers from high abstention rates and the latter from latency and calibration issues. This methodology provides a robust stress-testing standard for any synthetic-data-trained classifier.

- **Tags**: `embedding` `llm` `policy` `privacy` `rag`


---


## 26. Jacobian-Guided Anisotropic Noise Reshaping for Enhancing Representation Utility under Local Differential Privacy

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.16812v1)

- **Summary**: While Local Differential Privacy (LDP) serves as a foundational primitive for distributed data collection, its stringent noise injection requirement often leads to severe degradation in data utility. This degradation stems from the task-agnostic nature of conventional LDP mechanisms, which inject noise uniformly across all dimensions regardless of their relative importance to the downstream objective. To address this issue, we propose a novel approach that mitigates noise in task-relevant subspaces of the data representation. Our method identifies task-critical subspaces via the Jacobian matrix of the public downstream model, selectively attenuates noise along those dimensions, and reshapes the isotropic noise of standard LDP into an anisotropic distribution. This method preserves the uniform per-dimension privacy budget while heterogeneously modulating noise impact across dimensions, thereby substantially enhancing data utility. Furthermore, our approach generalizes to both linear and non-linear models and integrates seamlessly with existing mechanisms. Extensive experiments on CIFAR-10-C (Brightness corruption at the highest severity level 5) demonstrate that integrating our approach improves the utility of PrivUnit2 and PrivUnitG by approximately 20\% at $ε=7.5$. The source code is available at \url{https://github.com/ymha/jacobian-anr-ldp}.

- **Tags**: `differential privacy` `privacy`


---


## 27. LivePI: More Realistic Benchmarking of Agents Against Indirect Prompt Injectio

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17986v1)

- **Summary**: AI agents such as OpenClaw are increasingly deployed in local workflows with access to external tools. This creates indirect prompt-injection (IPI) risk: an agent may execute harmful instructions embedded in untrusted inputs such as email, downloaded files, webpages, repositories, or group-chat messages. Existing evaluations are often small, purely simulated, or focused on a narrow set of channels. We introduce LivePI (Live Prompt Injection), a structured benchmark for IPI risk in a production-like but test-controlled environment. LivePI covers seven input surfaces, twelve attack/rendering families, and five malicious goals, including protected-information exfiltration, unauthorized security-control changes, unsafe code retrieval or execution, inbox-summary exfiltration, and cryptocurrency transfer. We run LivePI on a real virtual machine with live but test-controlled email, chat, web, local-file, repository, and wallet interfaces. Across GPT-5.3-Codex, Claude Opus 4.6, Gemini 3.1 Pro, Kimi K2.5, and GLM-5, total attack success rates range from 10.7% to 29.6%. Group-chat injection is uniformly successful across the evaluated backbones in our deployment, and repository-link attacks produce high-severity failures despite a small denominator. We also evaluate a two-layer defense consisting of prompt-level filtering and pre-execution tool-call authorization. In the GPT-5.3-Codex setting, the defense intercepts all tested malicious-goal completions in LivePI before execution while preserving benign utility on PinchBench-derived workloads.

- **Tags**: `agent` `benchmark` `claude` `codex` `gemini`


---


## 28. Explainable Machine Learning for Phishing Detection on Heterogeneous Datasets with MCP-Enabled Deployment

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17891v1)

- **Summary**: With the growth in digital transformation and Internet usage, the Social Engineering techniques such as Phishing have become a major concern for the users and the organizations. Phishing attacks involve deceptive techniques to trick users into revealing confidential information that causes financial loss and reputation damage to organizations. According to report of Verizon, 36% of all data breaches involved phishing, highlighting the need for intelligent, adaptive, and explainable security mechanisms. This paper examines the efficiency of different machine learning algorithms in phishing detection on heterogeneous phishing datasets that include a publicly available UCI dataset, our generated datasets using tools such as EvilGinx and Zphisher, and AI generated datasets. Moreover, this work incorporates explainable AI (XAI) techniques such as Information Gain, SHAP (SHapley Additive Explanations), and LIME (Local Interpretable Model-Agnostic Explanations) to examine the most influential features impacting classification outcomes. To support practical deployment, this work also incorporates an MCP-based phishing URL detection system that offers real-time URL analysis, feature extraction, confidence-based classification, and AI-assisted security interpretation. The experimental results demonstrate that among classical models the highest accuracy is obtained by Logistic Regression at 92.44%, among ensemble models CatBoost achieved the highest accuracy at 95.01%, among neural network CNN achieved an accuracy of 94.02%, and among transformer-based models, DistilBERT got the highest accuracy at 99.78%

- **Tags**: `efficiency` `transformer` `xai`


---


## 29. Are Sparse Autoencoder Benchmarks Reliable?

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18229v1)

- **Summary**: Sparse autoencoders (SAEs) are a core interpretability tool for large language models, and progress on SAE architectures depends on benchmarks that reliably distinguish better SAEs from worse ones. We audit the SAE quality metrics in SAEBench, the de-facto standard SAE evaluation suite, through three complementary lenses: reseed noise on a fixed SAE, ground-truth correlation on synthetic SAEs, and discriminability across training trajectories. We find that two of these metrics, Targeted Probe Perturbation (TPP) and Spurious Correlation Removal (SCR), fail multiple lenses at their canonical settings and should not be used to evaluate SAEs. The other metrics show higher reseed noise and lower discriminability than the field assumes. The sae-probes variant of $k$-sparse probing is the most reliable metric we tested, but even sae-probes struggles to separate variants of the same SAE architecture. Our results show the field needs better SAE benchmarks.

- **Tags**: `benchmark` `interpretability` `large language model`


---


## 30. A Simplex Witness Certificate for Constant Collapse in Variational Autoencoders

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18224v1)

- **Summary**: This note studies exact constant collapse in variational autoencoders, where the encoder mean becomes independent of the input. The goal is to make this specific failure mode pre-designable, monitorable during training, and certifiable after training. The prior is kept as the standard Gaussian. Given a fixed teacher posterior, we attach to the latent mean a fixed simplex witness head. The resulting teacher-student alignment loss has an exact constant-predictor baseline equal to the teacher information. If the alignment loss is below this baseline, the latent mean cannot be input-independent constant collapsed.   The simplex witness also has a closed-form inverse. Any full-support teacher posterior can be represented by embedding its centered log-odds into the latent space. This gives an explicit latent energy cost and explains when the alignment loss can be made small. A computable view gap handles the case where teacher targets are computed from a different view. Thus exact constant collapse is converted from an after-the-fact training pathology into a design-and-certificate problem.

- **Tags**: `alignment` `embedding`


---


## 31. Visualizing the Invisible: Generative Visual Grounding Empowers Universal EEG Understanding in MLLMs

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18172v1)

- **Summary**: Leveraging the universal representations of pre-trained LLMs and MLLMs offers a promising path toward brain foundation models. However, visually-evoked EEG datasets remain scarce, leading existing methods to align neural signals mainly with abstract text, a lossy translation that may discard fine-grained perceptual information encoded in brain activity. We propose Generative Visual Grounding (GVG), a framework that visualizes the invisible by using an EEG-to-image generative model as a visual translator. Instead of forcing EEG into text alone, GVG hallucinates instance-specific proxy images for non-visual EEG, providing structured visual contexts that allow MLLMs to exploit their visual priors for clinical-state interpretation. We validate this idea on two MLLM backbones, GVG-X-Omni and GVG-Janus. Image-only alignment is already competitive: the lightweight GVG-X-Omni matches 1.7B-parameter text-aligned baselines while tuning only 170M parameters on a frozen 7B backbone. We further extend GVG-Janus with trimodal Image+Text alignment, where text supplies categorical semantic anchors and visual proxies enrich neural representations with perceptual details. Experiments show consistent gains in EEG understanding and visual generation, suggesting visual proxy grounding as an effective complement to textual alignment.

- **Tags**: `alignment` `foundation model` `generative` `llm` `rag`


---


## 32. Self-Evolving Spatial Reasoning in Vision Language Models via Geometric Logic Consistency

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18162v1)

- **Summary**: Vision-Language Models (VLMs) have made striking progress, yet their spatial reasoning remains fragile: models that answer an original input correctly can still fail under paired transformations with predictable answer mappings, revealing a gap between instance-level correctness and robust spatial reasoning. To address this, we propose Spatial Alignment via Geometric Evolution (SAGE), a self-evolving framework that enforces logical consistency in VLMs through geometric and linguistic duality operations. SAGE incorporates duality consistency as an auxiliary reward within GRPO training, encouraging models to produce logically coherent answers across original and transformed inputs. A dynamic operation pool continuously probes for inconsistencies, promoting challenging operations and retiring mastered ones, so that training focuses on the most informative signals. SAGE is model-agnostic, data-efficient compared to prior GRPO methods, and can be applied as a lightweight post-training stage to any existing VLM. Experiments on video and spatial reasoning benchmarks demonstrate consistent improvements over strong baselines and enhanced generalization to unseen data.

- **Tags**: `alignment` `benchmark` `rag` `reasoning` `vision`


---


## 33. Vision Inference Former: Sustaining Visual Consistency in Multimodal Large Language Models

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18160v1)

- **Summary**: In recent years, multimodal large language models (MLLMs) have achieved remarkable progress, primarily attributed to effective paradigms for integrating visual and textual information. The dominant connector-based paradigm projects visual features into textual sequence, enabling unified multimodal alignment and reasoning within a generative architecture. However, our experiments reveal two key limitations: (1) Although visual information serves as the core evidential modality in MLLMs, it is treated on par with textual tokens, diminishing the unique contribution of the visual modality; (2) As generation length increases, particularly within a limited context window, the model's dependence on visual information progressively weakens, resulting in deteriorated vision-language alignment and reduced consistency between generated content and visual semantics. To address these challenges, we propose the Vision Inference Former (VIF), a lightweight architectural module that establishes a direct bridge between pure visual representations and the model's output space. Specifically, VIF continuously injects visual semantics throughout the decoding phase of the inference process, ensuring that the model remains firmly grounded in visual content during generation. We conduct experiments on 14 benchmark tasks covering general reasoning, OCR, table understanding, vision-centric evaluation, and hallucination. Experimental results show that VIF consistently improves model performance across diverse architectures while introducing minimal additional overhead. The code for this work is available at https://github.com/Dong-Xinpeng/VIF.

- **Tags**: `alignment` `benchmark` `generative` `large language model` `llm`


---


## 34. Whispers in the Noise: Surrogate-Guided Concept Awakening via a Multi-Agent Framework

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18150v1)

- **Summary**: Diffusion models (DMs) are widely used for text-to-image generation, but their strong generative capabilities also raise concerns about unsafe or undesirable content. Concept erasure aims to mitigate these risks by removing specific concepts from pretrained models. However, recent studies show that such methods often suppress rather than fully eliminate target concepts, leaving models vulnerable to awakening attacks. Existing approaches primarily rely on white-box access through optimization or inversion, while concept awakening under black-box constraints remains underexplored. In this work, we revisit the denoising process from a trajectory perspective and show that concept erasure mainly disrupts early-stage text-semantic alignment but does not fully prevent semantic information from propagating along the denoising dynamics. As generation proceeds, the model increasingly depends on the evolving noisy state rather than textual conditions, which creates an opportunity to bypass erased mappings. Motivated by this observation, we propose ConceptAgent, a training-free, black-box, multi-agent framework that awakens erased concepts by initializing the denoising trajectory from surrogate-guided noisy states. Extensive experiments demonstrate that ConceptAgent enables accurate and controllable awakening of erased concepts under black-box settings without access to model parameters, gradients, or internal representations. These results highlight fundamental limitations of current concept erasure methods and provide new insights into the dynamic nature of semantic control in DMs.

- **Tags**: `agent` `alignment` `diffusion` `generative` `whisper`


---


## 35. POST: Prior-Observation Adversarial Learning of Spatio-Temporal Associations for Multivariate Time Series Anomaly Detection

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18128v1)

- **Summary**: Existing Multivariate Time Series Anomaly Detection (MTSAD) frameworks increasingly rely on integrating Graph Neural Networks (GNNs) with sequence models to capture complex spatio-temporal dependencies. However, less attention is paid to the spatial over-generalization problem, where unconstrained structural modeling indiscriminately reconstructs anomalies, inevitably degrading detection recall. To tackle this problem, we propose a novel framework that unifies spatio-temporal modeling through a joint prior-observation adversarial learning paradigm. In the spatial dimension, the model alternately learns adjacency matrices as structural prior and models the association discrepancy between prior and data-driven observation in a minimax manner during training. Such adversarial optimization not only improves the model sensitivity for time-wise detection, but also enables the model to localize anomalies to specific channels. To systematically evaluate this anomaly localization capability, we further construct a synthetic benchmark equipped with precise channel-wise annotations. Extensive experiments across public datasets and our dedicated benchmark demonstrate that the proposed framework establishes a new state-of-the-art in both time-wise detection and spatial localization tasks. Our code, pre-trained models, and benchmark are publicly available at https://github.com/anocodetest1/POST.

- **Tags**: `adversarial` `benchmark` `minimax`


---


## 36. TaskGround: Structured Executable Task Inference for Full-Scene Household Reasoning

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18109v1)

- **Summary**: In real home deployments, household agents must often operate from a complete household scene and a situated household request, rather than from a clean task specification. Such requests require agents to identify task-relevant entities, recover intended task conditions, and resolve ordering constraints from the surrounding scene context. We formalize this capability as full-scene household reasoning: given a complete household scene and a situated household request, an agent must infer executable task structure before producing a grounded skill-level action sequence. This setting is challenging because complete household scenes contain substantial task-irrelevant information, making direct complete-scene prompting inefficient and error-prone. In practical deployment, this challenge is further amplified by privacy and local compute constraints, which favor compact open-weight models with limited long-context reasoning ability. We propose TaskGround, a training-free and model-agnostic Ground-Infer-Execute framework that grounds complete scenes into compact task-relevant scene slices, infers executable task structure, and compiles it into grounded skill-level action sequences. To evaluate this setting, we introduce FullHome, a human-validated evaluation suite of 400 household tasks spanning diverse home-scale environments and both goal-oriented and process-constrained requirements. On FullHome, TaskGround improves task success rates by large margins across both proprietary and open-weight models. Notably, it makes Qwen3.5-9B competitive with GPT-5 under direct complete-scene prompting while reducing total input-token cost by up to 18x. Our results identify executable task-structure inference as a central bottleneck in full-scene household reasoning and show that structured grounding can make compact local models substantially more effective for practical household deployment.

- **Tags**: `agent` `gpt` `privacy` `qwen` `reasoning`


---


## 37. Safety Geometry Collapse in Multimodal LLMs and Adaptive Drift Correction

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18104v1)

- **Summary**: Multimodal large language models (MLLMs) often fail to transfer safety capabilities learned in the text modality to semantically equivalent non-text inputs, revealing a persistent multimodal safety gap. We study this gap from a representation-geometric perspective by analyzing a text-aligned refusal direction and a modality-induced drift direction. We show that multimodal inputs compress the usable separation along the refusal direction, making it no longer reliable for identifying and refusing harmful inputs. We refer to this failure mode as Safety Geometry Collapse. We quantify it through conditional refusal separability and show that stronger modality-induced drift is consistently associated with weaker refusal separability and higher attack success rates. We then validate the causal role of modality-induced drift through a fixed-strength activation intervention: counteracting the estimated drift restores refusal separability and improves multimodal safety. After drift correction, we further observe self-rectification, where the model recovers its ability to recognize and refuse harmful multimodal inputs during forward dynamics. This effect also provides an internal signal of the model's perceived harmfulness of each input. Motivated by this signal, we propose ReGap, a training-free inference-time method that adaptively corrects modality drift using self-rectification. Experiments across multiple multimodal safety benchmarks and utility benchmarks demonstrate the effectiveness of ReGap, which significantly improves the safety of MLLMs without compromising general capabilities. Our findings highlight representation-level modality alignment as a crucial direction for real-time safety improvement and for building safer, more reliable MLLMs.

- **Tags**: `alignment` `benchmark` `large language model` `llm` `multimodal`


---


## 38. Parameterized 4-Qubit EWL Quantum Game Circuits with Dirac-Solow-Swan Hamiltonian Integration for Quadruple Helix Disruptive Innovation Recommender Systems

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18080v1)

- **Summary**: We present a novel parameterized 4-qubit Eisert-Wilkens-Lewenstein (EWL) quantum game circuit for recommender systems in quadruple helix innovation ecosystems (academia, industry, government, and civil society). The local strategy operators $U_{i} = R_y(θ_{i})$ for each helix actor are directly tuned by normalized dominance weights extracted from real participant funding data (\texit{ecContribution}) in the European Commission CORDIS Horizon Europe database (project COVend, ID 101045956). The circuit employs a multi-qubit EWL entangler followed by parameterized local rotations, inverse entangler, and full measurement, achieving only 22 gates and circuit depth 11 while scaling as $O(n)$ for $n$-round helix communications. Measurement probabilities after the quantum game serve as recommender scores for disruptive versus sustaining innovation trends. These scores are subsequently mapped into the diagonal Dirac potential of a Dirac-Solow-Swan Hamiltonian, enabling time-evolution simulation of capital accumulation and bifurcation dynamics under disruptive innovation. Numerical experiments on real CORDIS quadruple-helix collaboration networks demonstrate the circuit's NISQ compatibility and its ability to forecast disruptive capital trajectories with high fidelity.   The proposed framework bridges quantum game theory, parameterized quantum circuits, and relativistic economic growth models, offering a computationally efficient tool for innovation policy and strategic decision-making in complex socio-economic ecosystems. Complexity analysis and reproducibility are provided through open Qiskit implementations.

- **Tags**: `policy`


---


## 39. FLAG: Foundation model representation with Latent diffusion Alignment via Graph for spatial gene expression prediction

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18055v1)

- **Summary**: Predicting spatial gene expression from routine H\&E enables large-scale molecular profiling, yet current models treat this as isolated pointwise tasks, thereby overlooking essential biological structures like gene coordination and spatial distribution. To preserve these relationships, we introduce \textbf{FLAG}, a diffusion-based framework that redefines this task as structured distribution modeling. At the same time, we identify the critical \textbf{Gene Dimension Curse}, where joint modeling gene expression and their spatial interactions fail in high-dimensional spaces, and FLAG solves this challenge by integrating a spatial graph encoder for topological consistency and utilizing Gene Foundation Model (GFM) alignment for gene-gene fidelity in the generation process. To rigorously assess model performance, we propose a set of novel structural evaluation metrics, including Gene Structural Correlation (\textbf{GSC}) and Spatial Structural Correlation (\textbf{SSC}). Our experiments demonstrate that FLAG is highly competitive in traditional accuracy (PCC/MSE) while achieving significantly enhanced structural fidelity in capturing both gene-gene and gene-spatial relationships. The code is available at https://github.com/darkflash03/FLAG.

- **Tags**: `alignment` `diffusion` `foundation model`


---


## 40. Confidence-Gated Robot Autonomy: When Does Uncertainty Actually Help?

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18045v1)

- **Summary**: Robotic systems often use predictive uncertainty to decide whether to act autonomously or defer to a fallback policy. In threshold-gated autonomy, uncertainty matters mainly through its ability to rank likely errors. Standard metrics such as expected calibration error and AUROC do not directly test whether uncertainty changes act/defer decisions. We therefore evaluate uncertainty using Spearman rank correlation, paired bootstrap equivalence testing, and act/defer agreement. Across three temporal activity-recognition benchmarks, we find a dataset-dependent competence regime below which uncertainty provides a weak and unstable error ranking. Above this regime, softmax heuristics, MC Dropout, and ensembles produce similar gating behavior, while threshold choice has a much larger effect on execution outcomes. A multi-seed embodied simulation shows the same pattern for collision rate and cost once realized autonomy is matched. Under temporal covariate shift, ranking quality remains stable, but fine grained semantic OOD detection remains near chance. These results suggest that simple uncertainty proxies can suffice for selective gating once the base model is competent, but not for semantic novelty detection.

- **Tags**: `benchmark` `policy`


---


## 41. Exploring Trust Calibration in XAI - The Impact of Exposing Model Limitations to Lay Users

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18036v1)

- **Summary**: Trust calibration -- aligning user trust judgment with model capability -- is crucial for safe deployment of explainable AI (XAI), yet is often evaluated via global trust ratings detached from objective performance evidence. We present a preregistered, incentivized between-subject online study (N=418 representative UK sample) on explainable skin-lesion classification that disentangles expectation-setting from experienced performance. Participants completed 15 case evaluations using a fixed XAI panel (malignancy score, reliability score, and saliency map). We systematically manipulated five experimental onboarding conditions varying example-based information and limitation disclosures with five stimulus packages naturally varying observed prediction quality. Calibration was operationalized as the deviation between trust-related judgments (TAIS and case-wise ratings) and objective performance benchmarks for the encountered cases, analysed with hierarchical mixed-effects models. Only limitation disclosure for case-wise measures reliably impacts trust calibration, and short-term experience did not yield progressive calibration. Further, the experienced package of stimuli explained substantially more variance than the experimental manipulation. However, participants were hard-pressed to differentiate between case-wise perceived trust, trustworthiness, and accuracy estimation. We discuss implications for designing limitation communication and for measuring and analysing calibration metrics in XAI evaluations. All study materials and data of this study are publicly available for replication and further academic use.

- **Tags**: `benchmark` `xai`


---


## 42. New Insight of Variance reduce in Zero-Order Hard-Thresholding: Mitigating Gradient Error and Expansivity Contradictions

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18035v1)

- **Summary**: Hard-thresholding is an important type of algorithm in machine learning that is used to solve $\ell_0$ constrained optimization problems. However, the true gradient of the objective function can be difficult to access in certain scenarios, which normally can be approximated by zeroth-order (ZO) methods. The SZOHT algorithm is the only algorithm tackling $\ell_0$ sparsity constraints with ZO gradients so far. Unfortunately, SZOHT has a notable limitation on the number of random directions % in ZO gradients due to the inherent conflict between the deviation of ZO gradients and the expansivity of the hard-thresholding operator. This paper approaches this problem by considering the role of variance and provides a new insight into variance reduction: mitigating the unique conflicts between ZO gradients and hard-thresholding. Under this perspective, we propose a generalized variance reduced ZO hard-thresholding algorithm as well as the generalized convergence analysis under standard assumptions. The theoretical results demonstrate the new algorithm eliminates the restrictions on the number of random directions, leading to improved convergence rates and broader applicability compared with SZOHT. Finally, we illustrate the utility of our method on a ridge regression problem as well as black-box adversarial attacks.

- **Tags**: `adversarial`


---


## 43. TeleCom-Bench: How Far Are Large Language Models from Industrial Telecommunication Applications?

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.18025v1)

- **Summary**: While Large Language Models have achieved remarkable integration in various vertical scenarios, their deployment in the telecommunications domain remains exploratory due to the lack of a standardized evaluation framework. Current telecom benchmarks primarily focus on static, foundational knowledge and isolated atomic skills, neglecting the equipment-specific documentation and end-to-end industrial workflows essential for real-world production systems. To bridge this gap, we present TeleCom-Bench, a comprehensive benchmark comprising 12 evaluation sets with 22,678 curated samples, which evaluates LLMs across a synergistic hierarchy: (1) Multi-dimensional Knowledge Comprehension, which integrates telecommunication fundamentals, 3GPP protocols, and 5G network architecture with proprietary product knowledge across wired, core, and wireless networks via knowledge graph-driven synthesis; and (2)End-to-End Knowledge Application, which formalizes six core tasks on authentic trajectories from live network agent workflows, including intent recognition, entity extraction, event verification, tool invocation, root cause analysis, and solution generation-across network optimization and fault maintenance scenarios. Evaluations of eight state-of-the-art LLMs reveal a universal Execution Wall: while models achieve 90% accuracy in linguistic interface tasks such as intent recognition and entity extraction, performance collapses to approximately 30% in procedural execution tasks like solution generation. This capability gap demonstrates that current LLMs function competently as diagnosticians but fail as field engineers. TeleCom-Bench provides standardized diagnostics to precisely pinpoint this deficit, offering actionable guidance for domain-specific alignment toward production-ready telecom agents. The dataset and evaluation code have been released at https://github.com/ZTE-AICloud/TeleCom-Bench.

- **Tags**: `agent` `alignment` `benchmark` `large language model` `llm`


---


## 44. Canonical Regularisation of Wide Feature-Learning Neural Networks

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18180v1)

- **Summary**: Wide neural networks in the feature-learning regime drive modern deep learning, and yet they remain far less studied than their kernel-regime counterparts. We consider a critical yet under-explored difference between these two regimes: the regulariser and prior implied by gradient flow training. This canonical regularisation property is well-studied in kernel regime networks -- of all the infinite global minima, gradient flow selects exactly the vanishing ridge solution -- and underpins the celebrated NN-GP correspondence, precisely allowing the modelling of noise during training. However, we prove ridge regularisation biases gradient flow in feature-learning regime networks, even in the infinitesimal limit of vanishing regularisation. Over training, ridge distorts the inductive bias of the network, with a particular damage done to pretrained networks where the implicit prior is informative. We resolve this by axiomatising the canonical regulariser as a regime-agnostic function-space energy and lift, which uniquely identifies ridge in the kernel regime, and crucially generalises to the feature-learning regime. By studying the Riemannian geometry of feature-learning networks, we derive geodesic ridge from our framework, generalising ridge to the feature-learning regime. Correspondingly, we prove the canonical function-space prior is a Riemannian Gibbs Process, generalising the more familiar Gaussian Process. As a practical contribution, we propose arc ridge as a minimax-robust, scalable surrogate to geodesic ridge, revealing a deep relationship between early stopping and canonical regularisation across learning regimes. Finally, we demonstrate the consequences of our theory empirically on both image processing and NLP transfer-learning problems.

- **Tags**: `bias` `minimax`


---


## 45. Federated Learning by Utility-Constrained Stochastic Aggregation for Improving Rational Participation

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18020v1)

- **Summary**: Federated Learning (FL) algorithms implicitly assume that clients passively comply with server-side orchestration by sharing local model updates upon server request. However, this overlooks an important aspect in real-world cross-silo environments: clients are often rational agents who may prioritize their utilities such as local model performance over that of the global model. In settings with significant statistical heterogeneity, rational clients may opt out of the federation if the perceived benefits of collaboration fail to meet their local utility thresholds. Such attrition degrades the global model performance and can lead to the collapse of the federated training process. In this work, we introduce FedUCA, (Federated Learning by Utility-Constrained Stochastic Aggregation for Improving Rational Participation), a framework that formalizes the server's role as an optimizer seeking to maximize global model performance by sustaining client participation. We substantiate our framework through extensive experiments on standard datasets demonstrating that by prioritizing participation feasibility, FedUCA achieves significantly higher client retention and, consequently, a superior global model performance.

- **Tags**: `agent` `federated learning`


---


## 46. Uncertainty Reliability Under Domain Shift: An Investigation for Data-Driven Blood Pressure Estimation in Photoplethysmography

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18008v1)

- **Summary**: Uncertainty quantification (UQ) is critical for safety-critical domains like healthcare, yet it is rarely evaluated under realistic out-of-distribution (OOD) conditions. Here, we assessed predictive performance and uncertainty reliability for deep learning-based blood pressure (BP) estimation from photoplethysmography (PPG) signals under both in-distribution (ID) and OOD settings. Using an XResNet1D-50 trained on PulseDB and tested on four external datasets, we compared deep ensembles (DE) and Monte Carlo dropout (MCD) with Gaussian negative log-likelihood (GNLL) and mean squared error (MSE) losses, optionally followed by post-hoc recalibration via conformal prediction (CP), temperature scaling (TS), and isotonic regression (IR).   The key findings of our study are as follows: (1) DE provides stronger predictive robustness under domain shift than MCD, an advantage that becomes clear primarily under external shift. (2) Recalibrated GNLL-based methods yield the best uncertainty calibration (e.g., GNLL+DE+CP for systolic blood pressure (SBP), GNLL+DE+TS for diastolic blood pressure (DBP)), while MSE-based uncertainty requires recalibration to become practically useful. (3) Across settings, CP and TS offer the most consistent gains, with IR remaining competitive in several cases.   Overall, our results identify DE-based methods as most robust for predictive performance under domain shift, GNLL as strongest for native UQ, and recalibration as essential for making MSE-based uncertainty practical. These findings highlight the need to jointly assess predictive accuracy and calibration on external data for trustworthy cuffless BP estimation

- **Tags**: `robustness`


---


## 47. RL4RLA: Teaching ML to Discover Randomized Linear Algebra Algorithms Through Curriculum Design and Graph-Based Search

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18004v1)

- **Summary**: Randomized linear algebra (RLA) algorithms are a modern class of numerical linear algebra techniques that play an essential role in scientific computing and machine learning, with broad and growing adoption. However, their discovery remains mostly a manual process that requires deep expert knowledge and inspiration. While Reinforcement Learning (RL) offers a pathway to automation, standard approaches struggle with sparse reward landscapes and vast search spaces inherent to high-performing RLA algorithms. In this paper, we present RL4RLA, a general RL framework that automates the discovery of interpretable, symbolic RLA algorithms. Unlike black-box approaches, our method builds explicit algorithms from basic linear algebra primitives, ensuring verifiable and implementable representations. To enable efficient discovery, we introduce: (1) a numerical curriculum that progressively increments problem difficulty to encode inductive bias specific to the RLA domain; (2) Monte Carlo Graph Search, which optimizes exploration by identifying and merging equivalent partial algorithms. We demonstrate that RL4RLA rediscovers state-of-the-art methods, including sketch-and-precondition solvers, Randomized Kaczmarz, and Newton Sketch, and can be targeted to produce algorithms optimized for specific trade-offs between accuracy, speed, and stability. Code is available at https://github.com/Tim-Xiong/RL4RLA.

- **Tags**: `bias`


---


## 48. Enhancing the Code Reasoning Capabilities of LLMs via Consistency-based Reinforcement Learning

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.17958v1)

- **Summary**: Code reasoning refers to the task of predicting the output of a program given its source code and specific inputs. It can measure the reasoning capability of large language models (LLMs) and also benefit downstream tasks such as code generation and mathematical reasoning. Existing work has verified the effectiveness of reinforcement learning on the task. However, these methods design rewards solely based on final outputs or coarse-grained signals, and neglect the inherent consistency of the stepwise reasoning process in the task. Therefore, these methods often result in sparse reward or reward hacking, which limits the full play of enhanced learning capabilities. To alleviate these issues, we propose CodeThinker, a consistency-driven reinforcement learning framework for code reasoning. Specifically, CodeThinker has three key components: (1) a stepwise reasoning-aware model training module, which utilizes a consistency tracing paradigm as a template to synthesize training data that captures the stepwise reasoning process; (2) a dynamic beam sampling strategy, which aims to improve the quality of sampled outputs under a fixed sampling budget; and (3) a consistency reward mechanism that can effectively alleviate reward hacking. Experiments on three popular benchmarks show that CodeThinker achieves state-of-the-art performance across multiple LLMs. For instance, it outperforms the strongest baseline by 4.3% in accuracy when deployed on Qwen2.5-Coder-7B-Instruct. We also validate the effectiveness of CodeThinker on downstream tasks. Results show that, without additional training, CodeThinker obtains average accuracy gains of 5.33 and 3.11 percentage points on mathematical reasoning and code reasoning tasks covering 17 programming languages, respectively.

- **Tags**: `benchmark` `large language model` `llm` `qwen` `rag`


---


## 49. A More Word-like Image Tokenization for MLLMs

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.17954v1)

- **Summary**: Modern multimodal large language models (MLLMs) typically keep the language model fixed and train a visual projector that maps the pixels into a sequence of tokens in its embedding space, so that images can be presented in essentially the same form as text. However, the language model has been optimized to operate on discrete, semantically meaningful tokens, while prevailing visual projectors transform an image into a long stream of continuous and highly correlated embeddings. This causes the visual tokens to behave differently from the word-like units that LLMs are originally trained to understand. We propose a novel Disentangled Visual Tokenization (DiVT) that clusters patch embeddings into coherent semantic units, so each token corresponds to a distinct visual concept instead of a rigid grid cell. DiVT further adapts its token budget to image complexity, providing an explicit accuracy-compute trade-off modifying neither the vision encoder nor the language model. Across diverse multimodal benchmarks, DiVT matches or surpasses baselines with significantly fewer visual tokens, demonstrating robustness under limited token budgets, significantly reducing memory cost and latency while making visual inputs more compatible with LLMs. Our code is available at https://github.com/snuviplab/DiVT.

- **Tags**: `benchmark` `embedding` `large language model` `llm` `multimodal`


---


## 50. Domain Transfer Becomes Identifiable via a Single Alignment

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.17918v1)

- **Summary**: Domain transfer (DT) maps source to target distributions and supports tasks such as unsupervised image-to-image translation, single-cell analysis, and cross-platform medical imaging. However, DT is fundamentally ill-posed: push-forward mappings are generally non-identifiable, as measure-preserving automorphisms (MPAs) preserve marginals while altering cross-domain correspondences, leading to content-misaligned translation. Recent work shows that MPAs can be eliminated by jointly transferring multiple corresponding source/target conditional distributions, but supervision signals labeling such conditionals are not always available in practice. We develop an alternative route to DT identifiability. Under a structural sparsity condition on the Jacobian support pattern, we show that distribution matching together with a single paired anchor sample suffices to identify the ground-truth transfer -- requiring substantially less supervision than prior approaches. To enable practical high-dimensional learning, we further propose an efficient Jacobian sparsity regularizer based on randomized masked finite differences, yielding a scalable surrogate without explicit Jacobian evaluation. Empirical results on synthetic and real-world DT tasks validate the theory.

- **Tags**: `alignment` `vision`


---


## 51. CoX-MoE: Coalesced Expert Execution for High-Throughput MoE Inference with AMX-Enabled CPU-GPU Co-Execution

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.17889v1)

- **Summary**: The Mixture-of-Experts (MoE) architecture improves computational efficiency via sparse expert activation, but throughput-oriented inference faces substantial GPU memory pressure due to a significant parameter size and intermediate data. Prior works attempt to mitigate this using expert offloading with micro-batching or by offloading computation to the CPU. However, the fragmented workload resulting from micro-batching degrades operational intensity, causing expert execution to become memory-bound. Meanwhile, CPU offloading is constrained by slow PCIe transfers and its limited applicability to attention computation in the decode stage. Consequently, these inefficiencies prevent effective system utilization, severely restricting the end-to-end throughput of MoE inference.   To address these challenges, this paper proposes CoX-MoE, an Advanced Matrix Extensions (AMX)-enabled CPU-GPU collaborative system that comprehensively optimizes MoE inference by combining coalesced expert execution with strategic workload orchestration for higher throughput. CoX-MoE introduces (i) a coalescing-aware orchestration policy to jointly optimize resource allocation by adopting ordinary batch, instead of micro-batch, for expert computation and selective attention offloading, and (ii) a static expert-aware stratification scheme that pre-assigns frequently activated experts to the GPU, mitigating PCIe transfer overhead and balancing workload for the CPU and GPU during inference. Compared to state-of-the-art frameworks, CoX-MoE delivers significant gains, achieving up to 7.1x and 2.4x higher throughput than FlexGen and MoE-Lightning, respectively.

- **Tags**: `efficiency` `moe` `policy` `rag`


---


## 52. How Loud Rumbles Hit Newsstands: A Data Analysis of Coverage and Spatial Bias in German News about Landslides Around the World

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.18105v1)

- **Summary**: Landslides often hit newsstands due to their destructive and potentially fatal effects. News are a valuable source of information for creating or enriching disaster databases and for expediting media-based studies of the dynamics of media attention. To accomplish that, news datasets must be filtered, geolocated and validated. This paper focuses on how landslides around the world are reported in German newspapers. We analyse almost 60k news articles about 5.5k news events in a 25-year period, compare it with external measures of countries' susceptibility to landslides and provide insights, e.g.~the overreporting of Southern and Western Europe, to foment further studies on inequalities in media attention to international disasters.

- **Tags**: `bias` `rag`


---


## 53. A Data-Efficient Path to Multilingual LLMs: Language Expansion via Post-training PARAM$Δ$ Integration into Upcycled MoE

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.18083v1)

- **Summary**: Expanding Large Language Models~(LLMs) to new languages is a costly endeavor, demanding extensive Continued Pre-Training~(CPT) and data-intensive alignment. While recent data-free merging techniques attempt to bypass alignment by fusing a multilingual CPT-enhanced model with its instruct counterpart, they are plagued by a critical trade-off: mitigating parameter conflicts to preserve original abilities inevitably dilutes new language acquisition, and vice-versa. To resolve this conflict, we introduce \method, which upcycles a dense model into a Mixture-of-Experts~(MoE) architecture, allocating different experts to different languages. Alignment ability is then transferred by grafting a MoE-expanded parameter delta~($Δ_{\text{post}}$) to the CPT-enhanced base model, bypassing the complex alignment phase. Experiments demonstrate \method's superiority even against baselines with similar FLOPs or number of parameters; it improves performance on expanded languages while effectively preserving original capabilities. We further show our approach is highly applicable across different models and Post-training deltas.

- **Tags**: `alignment` `large language model` `llm` `moe`


---


## 54. The Expressive Power of Low Precision Softmax Transformers with (Summarized) Chain-of-Thought

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.18079v1)

- **Summary**: Existing expressivity results for transformers typically rely on hardmax attention, high precision, and other architectural modifications that disconnect them from the models used in practice. We bridge this gap by analyzing standard transformer decoders with softmax attention and rounding of activations and attention weights, while allowing depth and width to grow logarithmically with the context length. As an intermediate step, we construct hardmax transformers with ternary activations and well-separated attention scores that simulate Turing machines using Chain-of-Thought (CoT). This lets us convert the constructions to equivalent softmax transformers without the unrealistic parameter magnitudes or activation precision that prior approaches would require. Using the same technique, we analyze a recently proposed summarized CoT paradigm and show that it simulates Turing machines more efficiently, with model size scaling logarithmically in a space bound rather than a time bound. We empirically test predictions made by our results on a Sudoku reasoning task and find better alignment with learnability than for prior high-precision results. Our code is available at https://github.com/moritzbroe/transformer-expressivity.

- **Tags**: `alignment` `chain-of-thought` `reasoning` `transformer`


---


## 55. Semantic Reranking at Inference Time for Hard Examples in Rhetorical Role Labeling

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.18007v1)

- **Summary**: Rhetorical Role Labeling (RRL) assigns a functional role to each sentence in a document and is widely used in legal, medical, and scientific domains. While language models (LMs) achieve strong average performance, they remain unreliable on hard examples, where prediction confidence is low. Existing approaches typically handle uncertainty implicitly and treat labels as discrete identifiers, overlooking the semantic information encoded in label names. We introduce RISE, an inference-time semantic reranking framework that leverages label semantics to refine predictions on hard instances. RISE automatically identifies low-confidence predictions and reranks model outputs using contrastively learned label representations, without retraining or modifying the underlying model. Experiments on eight domain-specific RRL datasets with seven LMs, including encoder-based and causal architectures, show an average gain of +9.15 macro-F1 points on hard examples. For explainability, we further propose manual hardness annotations to study difficulty from both model and human perspectives, revealing a moderate agreement with Cohen's kappa = 0.40.

- **Tags**: `explainability` `rag`


---


## 56. Bridging the Gap: Converting Read Text to Conversational Dialogue

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.18001v1)

- **Summary**: In recent advancements within speech processing, converting read speech to conversational speech has gained significant attention. The primary challenge in this domain is maintaining naturalness and intelligibility while minimizing computational overhead for real-time applications. Traditional read speech often lacks the nuanced prosodic variation essential for natural conversational interactions, posing challenges for applications in virtual assistants, customer service, and language learning tools. This paper introduces a novel approach, Prosodic Adjustment with Conversational Context (PACC), aimed at converting read speech into natural conversational speech used in various modern applications. PACC utilizes advanced deep neural networks to analyze and modify prosodic features such as intonation, stress, and rhythm. Unlike conventional methods, our approach uses High-Fidelity Generative Adversarial Networks (HiFi-GAN) for speech synthesis. Our experimental results demonstrate significant improvements in speech conversion, enhancing naturalness and achieving better model accuracy with additional training on speech datasets. This research establishes new benchmarks in speech conversion tasks and Mean Opinion Score (MOS) evaluation for testing model accuracy, and we show that our approach can be successfully extended to other speech conversion applications.

- **Tags**: `adversarial` `benchmark` `generative` `research`


---


## 57. Universal Adversarial Triggers

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17936v1)

- **Summary**: Recent works have illustrated that modern NLP models trained for diverse tasks ranging from sentiment analysis to language generation succumb to universal adversarial attacks, a class of input-agnostic attacks where a common trigger sequence is used to attack the model. Although these attacks are successful, the triggers generated by such attacks are ungrammatical and unnatural. Our work proposes a novel technique combining parts-of-speech filtering and perplexity based loss function to generate sensible triggers that are closer to natural phrases. For the task of sentiment analysis on the SST dataset, the method produces sensible triggers that achieve accuracies as low as 0.04 and 0.12 for flipping positive to negative predictions and vice-versa. To build robust models, we also perform adversarial training using the generated triggers that increases the accuracy of the model from 0.12 to 0.48. We aim to illustrate that adversarial attacks can be made difficult to detect by generating sensible triggers, and to facilitate robust model development through relevant defenses.

- **Tags**: `adversarial`


---


## 58. Entropy-Gradient Inversion: Moving Toward Internal Mechanism of Large Reasoning Models

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17770v1)

- **Summary**: The advancement of Large Reasoning Models (LRMs) has catalyzed a paradigm shift from reactive ``fast thinking'' text generation to systematic, step-by-step ``slow thinking'' reasoning, unlocking state-of-the-art performance in complex mathematical and logical tasks. However, the field faces \textit{the fundamental gap between token-level behavioral analysis and internal reasoning mechanisms, and the instability of reinforcement learning (RL) for reasoning optimization relying on costly external verifiers}. We identify and formally define \textbf{Entropy-Gradient Inversion}, a robust negative correlation between token entropy and logit gradients that acts as a definitive geometric fingerprint for LRM reasoning capability. Building on this, we propose \textbf{Correlation-Regularized Group Policy Optimization (CorR-PO)}, which embeds this inversion signature into RL reward regularization. Extensive experiments on various reasoning benchmarks across multiple model scales show CorR-PO consistently outperforms state-of-the-art baselines, confirming that stronger inversion directly correlates with superior reasoning performance.

- **Tags**: `benchmark` `policy` `reasoning`


---


## 59. Best Segmentation Buddies for Image-Shape Correspondence

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18193v1)

- **Summary**: Finding correspondences is a fundamental and extensively researched problem in computer vision and graphics. In this work, we examine the underexplored task of estimating segmentation-to-segmentation correspondence between images in the wild and untextured 3D shapes. This task is highly challenging due to substantial differences in appearance, geometry, and viewpoint. Our approach bridges the cross-modality gap by linking pixels in the image segment to vertices in the corresponding semantic part of the 3D shape. To achieve this, we first distill deep visual features from a 2D vision model onto the 3D shape surface, allowing for the computation of feature similarity between image pixels and shape vertices. Then, we identify Best Segmentation Buddies, vertices whose most similar image pixel lies within the image segmentation region, enabling the reliable discovery of vertices in semantically corresponding shape parts. Finally, we leverage distilled 3D features from the 2D image segmentation model to segment the shape directly in 3D, bootstrapping the correspondence process. We demonstrate the generality and robustness of our approach across a wide range of image-shape pairs, showcasing accurate and semantically meaningful correspondences. Our project page is at https://threedle.github.io/bsb/.

- **Tags**: `rag` `research` `robustness` `vision`


---


## 60. Semi-LAR: Semi-supervised Contrastive Learning with Linear Attention for Removal of Nighttime Flares

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18156v1)

- **Summary**: Lens flare removal is challenging due to the large spatial extent of flare artifacts and their entanglement with scene structures, while existing methods heavily rely on large-scale paired data. We propose a semi-supervised flare removal framework that enables stable learning from unlabeled images by jointly addressing pseudo-label reliability and representation discrimination. We propose an adaptive pseudo-label repository that progressively refines pseudo supervision through no-reference quality assessment, momentum-based updates, and invalid label filtering, effectively mitigating error accumulation. Moreover, we propose a flare-aware contrastive loss that explicitly treats flare-contaminated inputs as negatives and performs patch-level contrastive learning, encouraging representations that are discriminative against flare patterns while remaining consistent with reliable pseudo targets. Extensive experiments on multiple flare benchmarks demonstrate that the proposed framework is model-agnostic and consistently improves performance and robustness.

- **Tags**: `benchmark` `rag` `robustness` `vision`


---


## 61. Rad-VLSM: A Cross-Modal Framework with Semantics-Assisted Prompting for Medical Segmentation and Diagnosis

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18130v1)

- **Summary**: Medical image segmentation is more clinically valuable when it supports diagnosis rather than merely producing lesion masks. However, diagnostically relevant lesion cues are often subtle and localized, while existing models may be distracted by background tissues, acoustic artifacts, and irrelevant visual correlations. To address this problem, we propose Rad-VLSM, a two-stage cross-modal framework for semantics-assisted lesion focusing, robust segmentation, and visually grounded diagnosis. In the first stage, a BLIP-2-based vision-language alignment module identifies lesion-related candidate regions under semantic guidance and converts them into box prompts. In the second stage, these prompts are fed into a SAM-based multitask network, where a multi-candidate region aggregation strategy improves prompt stability and guides lesion segmentation. The predicted masks are then used as spatial priors for diagnosis, and a visual-radiomics fusion head integrates lesion-aware visual features with selected radiomics descriptors. By using semantic information for localization rather than direct prediction, Rad-VLSM reduces text-to-diagnosis dependence and grounds diagnosis in lesion-level evidence. Experiments on a private clinical breast ultrasound dataset and public benchmarks show that Rad-VLSM achieves strong segmentation and diagnostic performance with favorable generalization.

- **Tags**: `alignment` `benchmark` `vision`


---


## 62. DanceHMR: Hand-Aware Whole-Body Human Mesh Recovery from Monocular Videos

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18102v1)

- **Summary**: Monocular video human mesh recovery is essential for digital humans, avatar animation, and embodied simulation, where both temporal stability and expressive whole-body motion are required. Existing video HMR methods produce coherent body motion but often overlook detailed hand articulation, while image-based whole-body methods recover SMPL-X meshes independently per frame, often leading to jittery and inaccurate hand motion. We present a temporally coherent whole-body HMR framework for challenging in-the-wild monocular videos. Our model unifies body context and part-specific hand observations through residual body-hand fusion, enabling stable body motion and detailed hand recovery within a single temporal architecture. We further introduce close-up-aware augmentation to improve robustness under upper-body framing. Experiments on whole-body and body-only benchmarks demonstrate improved hand reconstruction and competitive body accuracy. Our method also produces temporally stable and 2D-consistent SMPL-X motion in challenging real-world videos.

- **Tags**: `benchmark` `robustness`


---


## 63. Threats to Arabic Handwriting Recognition: Investigating Black-Box Adversarial Attacks on embedded ConvNet models

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18058v1)

- **Summary**: Arabic handwriting recognition (AHR) has made significant progress with deep learning models. AHR research has largely focused on performance, with security receiving little attention. This study provides what appears to be a new line of inquiry by demonstrating the vulnerability of high-performing models to adversarial black-box attacks. The focus on black-box attacks reflects real-world scenarios where the attacker has no prior knowledge of the model architecture. Extensive experiments were conducted on two benchmark AHR datasets containing Arabic handwritten Characters. Results demonstrated the effectiveness of the attacks, with the Pixle attack achieving an attack success rate of 99-100\% on most models. Other, less aggressive attacks achieved success rates of 50-96\% across most experiments. Despite the higher attack success rate, the attacks maintain the structural integrity of the characters, rendering them almost imperceptible to the human eye. The findings indicate the higher vulnerability of the studied models to adversarial manipulation. This underscores the need to strengthen efforts to secure these models and ensure their reliability in AHR real-world applications.

- **Tags**: `adversarial` `benchmark` `research`


---


## 64. SGSoft: Learning Fused Semantic-Geometric Features for 3D Shape Correspondence via Template-Guided Soft Signals

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18039v1)

- **Summary**: Learning dense correspondences across deformable 3D shapes remains a long-standing challenge due to structural variability, non-isometric deformation, and inconsistent topology. Existing methods typically trade off generalization, geometric fidelity, and efficiency. We address this by proposing SGSoft, a unified intrinsic pipeline that (i) constructs a geodesic correspondence field on a canonical template, (ii) learns multimodal dense descriptors guided by pretrained semantic priors with this geodesic correspondence field supervision, (iii) retrieves dense correspondences in a single feed-forward pass via nearest-neighbor search in descriptor space. This formulation enables stable and topology-invariant supervision under large pose variation, structural differences, and remeshing. SGSoft achieves state-of-the-art inter-category generalization while offering the best accuracy-efficiency trade-off among prior methods. It also achieves near real-time inference without pre-alignment, pairwise optimization, or post-refinement. Learned descriptors can be transferred effectively to downstream tasks such as semantic segmentation and deformation transfer, establishing a scalable and deployment-ready paradigm for dense 3D correspondence.

- **Tags**: `alignment` `efficiency` `multimodal` `vision`


---


## 65. Generation Navigator: A State-Aware Agentic Framework for Image Generation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.17969v1)

- **Summary**: Despite rapid advances in text-to-image generation, faithfully realizing user intent remains challenging, often requiring manual multi-turn trial and error. To automate this process, existing systems rely on either simple prompt rewriting or closed-loop agents driven by hand-crafted rules, rather than learning to adapt actions to the evolving generation process. In this paper, we reformulate image generation as a state-conditioned action-making problem and propose Generation Navigator, a multi-turn T2I agent that learns to dynamically steer the generation trajectory and output the next action. However, training this agent via reinforcement learning introduces a critical credit assignment challenge: naively rewarding a trajectory based solely on a single state assigns equal credit to all actions in the rollout, ignores the quality dynamics across turns, and fails to distinguish actions that improve the trajectory from those that degrade it or waste turns without progress. We resolve this with PRE-GRPO (Peak-Retention-Efficiency Group Relative Policy Optimization), a trajectory-level reinforcement learning objective that explicitly rewards discovering a high-quality image (Peak), avoiding subsequent quality degradation across turns (Retention), and minimizing unnecessary turns (Efficiency). Experiments show substantial improvements across benchmarks, reaching a WISE score of 0.90 and 79.06% reasoning accuracy on T2I-ReasonBench.

- **Tags**: `agent` `benchmark` `efficiency` `policy` `reasoning`


---


## 66. SkyNative: A Native Multimodal Framework for Remote Sensing Visual Evidence Reasoning

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.17949v1)

- **Summary**: Remote sensing vision-language models commonly rely on pretrained visual encoders to convert images into semantic features before language-model reasoning. While effective for scene-level understanding, this pipeline may prematurely compress local visual evidence, making fine-grained spatial reasoning vulnerable to language priors, especially in ultra-high-resolution remote sensing imagery. We present SkyNative, a native multimodal framework for remote sensing that adopts an encoder-free architecture, removing the pretrained visual backbone to directly represent images as raw patch tokens in the language-model token space. To reconcile low-level visual patches with textual tokens, SkyNative introduces a modality-aware decoupling mechanism that uses modality-specific parameters within a unified autoregressive backbone. We further introduce a visual reliance benchmark that diagnoses whether models ground their answers in image evidence through progressive visual degradation and misleading textual prompts. Across standard remote sensing understanding tasks and large-format spatial reasoning evaluations, SkyNative shows stronger image-grounded perception and improved robustness against prompt-induced language priors. These results suggest that native patch-level multimodal modeling is a promising direction for reliable remote sensing vision-language reasoning.

- **Tags**: `benchmark` `multimodal` `reasoning` `robustness` `vision`


---


## 67. An Efficient Streaming Video Understanding Framework with Agentic Control

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.17921v1)

- **Summary**: Streaming video requires handling dynamic information density under strict latency budgets. Yet, existing methods typically employ static strategies, such as fixed memory compression or reliance on a single model, forcing a trade-off: fast models fail on complex queries, while always-on heavy models violate real-time constraints and overcomplicate simple queries. Rather than fixing these decisions upfront, we propose R3-Streaming (Remember, Respond, Reason), which formulates streaming video understanding as a cascaded control problem: for each query, the system compresses memory, judges response readiness, and routes computation sequentially, so that each downstream decision builds on progressively refined information states. To optimize this pipeline, we introduce an age-aware forgetting policy for memory compression, as aggressively compressing historical frames can yield substantial performance gains. For compute routing, we propose TB-GRPO, a target-balanced reinforcement learning objective that routes hard queries to a stronger model while preventing mode collapse. Extensive evaluations demonstrate that R3-Streaming achieves state-of-the-art results among streaming MLLMs, reaching 57.92 on OVO-Bench and 76.36 on StreamingBench, while reducing visual token usage by 95 to 96 percent.

- **Tags**: `agent` `llm` `policy`


---


## 68. Attention-Guided Fusion of 1D and 2D CNNs for Robust ECG-Based Biometric Recognition

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17685v1)

- **Summary**: Electrocardiogram (ECG)-based biometric recognition has emerged as a promising solution for secure authentication and liveness detection. However, most existing methods rely on unimodal deep learning architectures that independently process either one-dimensional (1D) temporal signals or two-dimensional (2D) time-frequency representations, limiting robustness and generalization. To address this issue, this paper proposes a hybrid framework integrating 1D and 2D convolutional neural networks (CNNs) within a unified end-to-end architecture. The 1D branch extracts temporal and morphological features from raw ECG signals, while the 2D branch captures discriminative spectral information from time-frequency representations. An attention-guided fusion mechanism dynamically weights both modalities according to input characteristics, overcoming the limitations of conventional static fusion strategies.   The framework was evaluated on three benchmark datasets (ECG-ID, MIT-BIH, and PTB), including healthy subjects and patients with cardiac pathologies, achieving identification accuracies of 99.56%, 100.00%, and 99.89%, respectively. To assess long-term biometric permanence, experiments were also conducted on the multi-session Heartprint dataset spanning ten years. The proposed approach achieved same-session accuracies of 98.54% (S1), 99.09% (S2), 94.93% (S3R), and 96.08% (S3L), while cross-session evaluations reached 56.33% (S1-S2) and 53.27% (S2-S3R), demonstrating the ability to capture stable biometric signatures over time. The optimal configuration combines InceptionTime for 1D processing, ResNet-34 for 2D analysis, and attention-based fusion. Ablation studies confirm that the proposed attention mechanism consistently outperforms conventional fusion approaches. Overall, the proposed framework provides a robust, scalable, and high-performance solution for ECG biometric recognition.

- **Tags**: `benchmark` `robustness`


---


## 69. From Documents to Segments: A Contextual Reformulation for Topic Assignment

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17714v1)

- **Summary**: Traditional topic modeling assigns a single topic to each document. In practice, however, many real-world documents, such as product reviews or open-ended survey responses, contain multiple distinct topics. This mismatch often leads to topic contamination, where unrelated themes are merged into a single topic, making it difficult to identify documents that truly focus on a specific subject. We address this issue by introducing segment-based topic allocation (SBTA), a reformulation of topic modeling that assigns topics not to entire documents, but to segments: short, coherent spans of text that each express a single theme. By modeling topical structure at the segment level, our approach yields cleaner and more interpretable topics and better supports analysis of multi-theme documents. To support systematic evaluation, we construct a SemEval-STM, a new dataset inspired by aspect-based sentiment analysis. Documents are first decomposed into topical segments using large language models (LLMs), followed by human refinement to ensure segment quality. We also propose a segment-level extension of the word intrusion task, enabling human evaluation of topical coherence at the granularity where topics are actually assigned. Across multiple models and evaluation metrics, we show that SBTA improves clustering quality and interpretability. Overall, this work provides a practical, scalable framework for fine-grained topic analysis in heterogeneous text corpora where documents naturally span multiple topics. URL: https://huggingface.co/datasets/LG-AI-Research/SemEval-STM

- **Tags**: `interpretability` `large language model` `llm` `research`


---


## 70. Do LLM Agents Mirror Socio-Cognitive Effects in Power-Asymmetric Conversations?

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17694v1)

- **Summary**: Power differences shape human communication through well documented socio cognitive effects, including language coordination, pronoun usage, authority bias, and harmful compliance. We examine whether large language models (LLMs) exhibit similar behaviors when assigned high or low status personas. Using personas from diverse professions, we simulate multi turn, power asymmetric dialogues (e.g., principal teacher, justice lawyer) and measure (i) linguistic coordination, (ii) pronoun usage, (iii) persuasion success, and (iv) compliance with unsafe requests. Our results show that LLMs show key socio cognitive effects of power, albeit with nuances and variability, linking simulated interactions to both desirable and unsafe behaviors.

- **Tags**: `agent` `bias` `large language model` `llm`


---


## 71. Stop When Reasoning Converges: Semantic-Preserving Early Exit for Reasoning Models

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17672v1)

- **Summary**: Large Reasoning Models (LRMs) achieve strong performance by generating long chains of thought (CoT), but often overthink, continuing to reason after a solution has already stabilized and thereby wasting tokens and increasing latency. Existing inference-time early-exit methods rely primarily on answer-level signals, such as confidence or trial-answer consistency, to decide when to stop. However, these signals mainly reflect answer readiness rather than reasoning convergence: they may trigger before the model has finished exploring or self-correcting, causing premature exits that can degrade final-answer accuracy and leave the retained reasoning chain semantically incomplete. We identify reasoning-level semantic redundancy as a complementary signal for semantic-preserving early exit: when successive steps no longer add novel progress and instead revisit established conclusions, the reasoning trajectory has likely converged. Building on this insight, we propose PUMA, a plug-and-play framework that combines a lightweight Redundancy Detector with answer-level verification. The detector flags semantically redundant candidate exits, while verification confirms whether stopping is safe, allowing PUMA to remove redundant continuation while preserving both answer accuracy and a coherent reasoning prefix. Across five LRMs and five challenging reasoning benchmarks, PUMA achieves 26.2% average token reduction while preserving accuracy and retained CoT quality. Additional experiments on code generation, zero-shot vision-language reasoning, and learned stopping-policy internalization further demonstrate that reasoning-level redundancy is a robust, transferable, and learnable signal for efficient reasoning. Our code is available at \url{https://github.com/giovanni-vaccarino/PUMA}.

- **Tags**: `benchmark` `policy` `rag` `reasoning` `vision`


---


## 72. Beyond Transcripts: Iterative Peer-Editing with Audio Unlocks High-Quality Human Summaries of Conversational Speech

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17652v1)

- **Summary**: There are not enough established benchmarks for the task fo speech summarization. Creating new benchmarks demands human annotation, as LLMs could embed systemic errors and bias into datasets. We test ten annotation workflows varying input modality (audio, transcript, or both) and the inclusion of editing (self or peer-editing) to investigate potential quality tradeoffs from using human annotators to summarize audio. We compare human audio-based summaries to human transcript-based summaries to track the impact of the different information modalities on summary quality. We also compare the human outputs against four LLM benchmarks (three text, one audio) to examine whether human-written summaries are less informative than highly fluent automated outputs. We find that audio-based summaries are less informative and more compressed than transcript summaries. However, iterative peer-editing with audio mitigates this difference, enabling audio-based summaries to be as informative as their transcript counterparts and LLM summaries. These findings validate iterative peer-editing among human annotators for the creation of benchmarks informed by both lexical and prosodic information. This enables crucial dataset collection even in setting where transcripts are unavailable.

- **Tags**: `benchmark` `bias` `llm`


---


## 73. Causal Intervention-Based Memory Selection for Long-Horizon LLM Agents

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17641v1)

- **Summary**: Long-horizon LLM agents rely on persistent memory to support interactions across sessions, yet existing memory systems often retrieve context using semantic similarity or broad history inclusion, treating retrieved memories as uniformly useful. This assumption is fragile because memories may be topically related while remaining irrelevant, stale, or misleading. We propose Causal Memory Intervention (CMI), a causal memory-selection technique that estimates how candidate memories affect the model's answer under controlled interventions, selecting memories that improve task performance while suppressing unstable, irrelevant, or harmful ones. To evaluate this setting, we introduce Causal-LoCoMo, a causally annotated benchmark derived from long conversational data, where each example contains a user request, a structured memory bank, useful memories, irrelevant distractors, and synthetic harmful memories. We compare CMI against vector, graph, reflection, summary, full-history, and no-memory baselines. Results show that CMI achieves a stronger balance between answer quality and robustness to misleading memory, suggesting that reliable long-term memory requires selecting context based on causal usefulness rather than relevance alone. The full framework, benchmark construction code, and experimental pipeline are available at https://github.com/Saksham4796/causal-memory-intervention.

- **Tags**: `agent` `benchmark` `llm` `rag` `robustness`


---


## 74. SafeLens: Deliberate and Efficient Video Guardrails with Fast-and-Slow Screening

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17610v1)

- **Summary**: The rapid growth of online video platforms and AI-generated content has made reliable video guardrails a key challenge for safety and real-world deployment. While most videos can be screened through fast pattern recognition, a small subset requires deeper reasoning over temporally complex content and nuanced policy constraints. Existing approaches typically rely on large vision-language models applied uniformly across all inputs, resulting in high inference costs and inefficient allocation of computation. We propose SafeLens, a video guardrail framework that introduces a fast-and-slow inference architecture for efficient and accurate content moderation with variable computational cost across inputs. Additionally, we construct a high-quality dataset by applying influence-guided filtering to the SafeWatch Dataset, retaining only 2.4% of the original data. To further address limitations of training-time scaling, we enable test-time reasoning by augmenting the filtered data with structured Chain-of-Thought traces. Across real-world and AI-generated video benchmarks, SafeLens achieves state-of-the-art performance, outperforming strong open-source video guardrails (e.g., SafeWatch-8B, OmniGuard-7B) and closed-source models (e.g., GPT-5.4, Gemini-3.1-pro) while significantly reducing inference cost, demonstrating that efficient design serves to be more effective than scaling data or model size alone.

- **Tags**: `benchmark` `chain-of-thought` `gemini` `gpt` `policy`


---


## 75. How Off-Policy Can GRPO Be? Mu-GRPO for Efficient LLM Reinforcement Learning

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.17570v1)

- **Summary**: Group Relative Policy Optimization (GRPO) has been a key driver of recent progress in reinforcement learning with verifiable rewards (RLVR) for large language models, but it is typically trained in a low-staleness, near-on-policy regime that incurs substantial system overhead. We ask a simple question: How off-policy can GRPO be? We show that GRPO-style algorithms can tolerate substantially larger rollout staleness than previously assumed, and propose Mu-GRPO, an RL training framework that organizes training into a small number (e.g., four) of large sequential generation-optimization stages. This design induces high rollout staleness while greatly reducing rollout-optimization switching overhead. To stabilize learning under stale data, Mu-GRPO combines relaxed clipping, which preserves useful stale-rollout gradients, with negative-advantage veto, which removes destabilizing post-trigger suffix updates in negative-advantage responses. Across five language models and multiple math reasoning benchmarks, Mu-GRPO matches or exceeds the performance of standard GRPO while achieving around 2x speedup in wall-clock training time, establishing a substantially improved performance-efficiency trade-off for LLM reinforcement learning.

- **Tags**: `benchmark` `efficiency` `large language model` `llm` `policy`


---


## 76. SNLP: Layer-Parallel Inference via Structured Newton Corrections

- **Source**: [huggingface_papers](https://arxiv.org/abs/2605.17842)

- **Summary**: Autoregressive language models execute Transformer layers sequentially, creating a latency bottleneck that is not removed by conventional tensor or pipeline parallelism. We study whether this layerwise dependency can be relaxed by treating the hidden-state trace across layers as the solution of a nonlinear residual equation and solving it with parallel Newton-style updates. While this view is principled, exact Newton corrections require expensive Jacobian-vector products and naive fixed-point iterations are unstable on trained Transformers. We introduce Structured Newton Layer Parallelism (SNLP), a training and inference framework that replaces exact layer Jacobians with cheap architecture-induced surrogate dynamics. In residual Transformers, this yields Identity Newton (IDN), where the correction reduces to a prefix-sum-like update; in mHC-style architectures, HC Newton (HCN) uses the model's residual mixing matrix. We further introduce SNLP-aware regularization, which trains models to make one or a few structured Newton iterations accurately approximate the sequential forward. Experiments on nanochat-scale Transformers show that SNLP regularization improves layer-parallel compatibility and can also improve standard sequential perplexity, reducing baseline PPL by 4.7%-23.4%. At inference time, SNLP combined with layer fusion and chunkwise decomposition achieves practical wall-clock speedups: on a 0.5B Nanochat model, it reaches 2.3x speedup while still improving PPL by 6.1%. These results suggest that layer-parallel inference is not merely a numerical approximation to sequential execution, but can act as a useful solver-induced inference bias. We also characterize limitations: off-the-shelf pretrained models are less amenable to this procedure, and exact convergence recovers the sequential computation rather than providing monotonic inference-time scaling.

- **Tags**: `bias` `transformer`


---


## 77. ContraFix: Agentic Vulnerability Repair via Differential Runtime Evidence and Skill Reuse

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17450v1)

- **Summary**: Large language model (LLM) agents are increasingly used for automated vulnerability repair (AVR), where repository-level reasoning enables them to inspect context and produce source-code patches. However, recent empirical results show that these agents still struggle with real-world vulnerabilities. Their main failure mode is semantic misunderstanding: choosing a repair direction that does not match the root cause. We identify two reasons for this gap. Existing agents usually reason from the failing execution alone. A crash report can pinpoint where the program failed, but it does not reveal which variable or state transition, among many candidates near the fault site, separates the crashing behavior from safe execution. As a result, agents often produce symptom-oriented patches instead of causal fixes. Moreover, evidence collected for one vulnerability is rarely retained, so similar cases in later repositories must be diagnosed again from scratch. We present ContraFix, an agentic AVR framework that couples differential runtime evidence with reusable repair skills. Its Mutator constructs PoC variants that straddle the failure boundary; its Analyzer inserts state probes around the fault region and summarizes divergences between crashing and non-crashing executions into a repair specification; and its Patcher converts the specification into verified source patches. Each successful repair updates a two-track skill base containing repair specifications and mutation strategies, which are retrieved through a three-tier policy for future instances. On SEC-Bench (C/C++, 200 instances) and PatchEval (Go, Python, JavaScript, 225 instances), ContraFix with GPT-5-mini resolves 84.0% and 73.8% of the tasks, respectively, achieving state-of-the-art performance on both benchmarks while costing less than one-third of the strongest comparable baseline.

- **Tags**: `agent` `benchmark` `gpt` `large language model` `llm`


---


## 78. Rethinking Side-Channel Analysis: Automated Discovery and Analysis of Side-Channel Leakage with LLM-Assisted Agents

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17406v1)

- **Summary**: Side-channel attacks exploit unintended information leakage from system behavior and continue to pose serious privacy risks in modern platforms. Despite extensive prior work, side-channel analysis remains largely manual and fragmented, typically assuming predefined target events and a fixed set of known channels. As systems and applications grow increasingly complex, several fundamental questions remain unanswered: which user or system events are sensitive in practice, how side channels associated with these events can be systematically discovered without exhaustive manual effort, and how their leakage can be analyzed at scale without prohibitive data collection and model training costs. To address these questions, we present SCAgent, an automated framework for side-channel risk analysis. To identify sensitive targets beyond manually specified events, SCAgent performs agent-driven system exploration guided by LLM-based semantic reasoning. To systematically discover side channels while mitigating the risk of LLM hallucination, it reasons over system documentation and incorporates explicit verification to enforce semantic consistency, threat-model feasibility, and per-channel usability. To enable scalable analysis under limited data, SCAgent adopts a few-shot learning paradigm based on foundation models, avoiding the need to train bespoke models for each channel--event pair. To bridge the gap between raw time-series side-channel signals and tabular foundation models, SCAgent further introduces a time-shift--robust feature extraction layer that enables effective downstream analysis. We instantiate SCAgent on iOS as a first step, focusing on OS-level side channels observable by unprivileged applications. Our evaluation spans standard benchmarks such as foreground app and website fingerprinting, as well as newly identified sensitive in-app activities in popular applications.

- **Tags**: `agent` `benchmark` `foundation model` `llm` `privacy`


---


## 79. LPG: Balancing Efficiency and Policy Reasoning in Latent Policy Guardrails

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17329v1)

- **Summary**: Guardrails are a critical safety layer for modern AI systems, but their operating regime is changing. As LLMs are deployed as customized assistants, safety policies are increasingly specified at inference time by users, organizations, or regulatory contexts. This makes safety enforcement fundamentally dynamic: the guardrail should adapt to changing safety policies without retraining. Yet this requirement creates a fundamental tension: faithfully judging complex policy contexts demands reasoning capability, while practical deployment requires low-latency responses. We introduce Latent Policy Guardrail (LPG), a guardrail framework that learnssemantic latent deliberation over dynamic policies. LPG compresses the internal deliberation needed for intent interpretation and policy grounding into continuous states supervised by decision-relevant semantics. At inference time, it generates only a compact verdict anchored to the violated policy clauses, preserving auditability while avoiding the latency of explicit reasoning. Across policy guardrail benchmarks, LPG-4B reaches 84.5% average safety accuracy and 77.9% F1 by compressing deliberation into just 10 latent tokens, outperforming the strongest dynamic baseline while running roughly 11 times faster than Qwen3-4B-Thinking under the single-sample evaluation setup. Code and data are available at https://github.com/SaFo-Lab/Latent_Policy_Guard.

- **Tags**: `benchmark` `efficiency` `llm` `policy` `qwen`


---


## 80. When Efficiency Backfires: Cascading LLMs Trigger Cascade Failure under Adversarial Attack

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17288v1)

- **Summary**: Large Language Model (LLM) cascade systems are designed to balance efficiency and performance by processing queries with lightweight models while selectively escalating complex cases to more powerful ones. Such systems seek to reduces computational cost and latency while maintaining task performance, making it an appealing choice for large-scale deployment. However, the cascade design introduces new vulnerabilities through an expanded attack surface: the inclusion of lightweight front-end models and internal decision mechanisms introduces new weaknesses. In this work, we present the first study demonstrating that LLM cascade systems are susceptible to targeted adversarial manipulation, which disrupts both performance objectives and the intended cost advantages of the cascade design. We propose a novel attack framework that employs constrained sequential collaborative optimization of adversarial suffix under cascade dependencies, enabling simultaneous exploitation of lightweight models and decision mechanisms. This framework adapts to adversaries with varying capabilities, inducing controllable degradation in both cost-efficiency and accuracy. Unlike prior attacks targeting standalone models, our approach strategically leverages the cascade structure to achieve significantly stronger impact. Extensive experiments across diverse datasets and representative LLM cascade systems validate the practicality and severity of this attack. Our findings highlight the urgent need to rigorously scrutinize the security of LLM cascade systems and call for broader attention to the systemic risks inherent in such designs.

- **Tags**: `adversarial` `efficiency` `large language model` `llm` `rag`


---


## 81. Triple-Hoisted Baby-Step Giant-Step Linear Transformation over CKKS Homomorphic Encryption and Hardware Accelerator

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.17222v1)

- **Summary**: Computations can be directly carried out over ciphertexts using homomorphic encryption (HE), which is indispensable for privacy-preserving cloud computing. Linear transformation is widely used in neural networks, including large language models. However, the implementation of linear transformation over HE requires a large number of ciphertext rotations, which incur significant memory and hardware overhead despite existing simplification techniques. This paper proposes a triple-hoisted baby-step giant-step algorithm that decomposes the baby step further to substantially reduce the number of ciphertext rotations needed for the CKKS HE evaluation of linear transformation. Moreover, to reduce off-chip memory access, which contributes to the majority of the latency, a memory-optimized data path is proposed by partitioning the algorithm into multiple phases. Furthermore, an efficient FPGA-based hardware accelerator with an optimized permutation circuit for message routing is designed for the proposed scheme. For a set of typical parameters, the proposed design reduces the off-chip memory access by 2.9x compared to the best prior design. Synthesized for Xilinx Virtex UltraScale+ devices, the proposed design achieves a 5.8x reduction in computational latency compared with the baseline design.

- **Tags**: `large language model` `privacy`


---


## 82. Forward-Learned Discrete Diffusion: Learning how to noise to denoise faster

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18204v1)

- **Summary**: Discrete diffusion models are a powerful class of generative models with strong performance across many domains. For efficiency, however, discrete diffusion typically parameterizes the generative (reverse) process with factorized distributions, which makes it difficult for the model to learn the target process in a small number of steps and necessitates a long, computationally expensive sampling procedure. To reduce the gap between the target and model distributions and enable few-step generation, we propose Forward-Learned Discrete Diffusion (FLDD), which introduces discrete diffusion with a learnable forward (noising) process. Rather than fixing a Markovian forward chain, we adopt a non-Markovian formulation with learnable marginal and posterior distributions. This allows the generative process to remain factorized while matching the target defined by the noising process. We train all parameters end-to-end under the standard variational objective. Experiments on various benchmarks show that, for a given number of sampling steps, our approach produces a higher quality samples than conventional discrete diffusion models using the same reverse parameterization.

- **Tags**: `benchmark` `diffusion` `efficiency` `generative`


---


## 83. Dual-Rate Diffusion: Accelerating diffusion models with an interleaved heavy-light network

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18190v1)

- **Summary**: Diffusion models achieve state-of-the-art generative performance but suffer from high computational costs during inference due to the repeated evaluation of a heavy neural network. In this work, we propose Dual-Rate Diffusion, a method to accelerate sampling by interleaving the execution of a heavy high-capacity context encoder and a light efficient denoising model. The context encoder is evaluated sparsely to extract high-dimensional features, which are effectively reused by the light denoising model at every step to refine the sample efficiently. This approach significantly accelerates inference without compromising sample quality. On ImageNet benchmarks, Dual-Rate Diffusion matches the performance of standard baselines while reducing computational cost by a factor of $2$-$4$. Furthermore, we demonstrate that our method is compatible with distillation techniques, such as Moment Matching Distillation, enabling further efficiency gains in few-step generation.

- **Tags**: `benchmark` `diffusion` `distillation` `efficiency` `generative`


---


## 84. UTOPYA: A Multimodal Deep Learning Framework for Physics-Informed Anomaly Detection and Time-Series Prediction

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18188v1)

- **Summary**: Anomaly detection in batch processes is hindered by transient dynamics, scarce fault labels, and reliance on single-modality sensor data. This work introduces UTOPYA (Unified Temporal Observation for Physics-Informed Anomaly Detection and Time-Series Prediction), a 15.2M-parameter multimodal framework that jointly addresses anomaly detection, time-series prediction, and phase classification in batch distillation by fusing eight data modalities through Feature-wise Linear Modulation (FiLM) conditioned cross-modal attention and gated fusion. A physics-informed regularisation scheme introduced in this work enforces temporal smoothness and thermodynamic monotonicity, while curriculum learning introduces training samples in order of physical difficulty. On the 119-experiment multimodal batch distillation dataset of Arweiler et al. (2026), UTOPYA achieves a window-level test AUROC of 0.832 and 0.874 under multi-signal experiment-level scoring, substantially outperforming four external baselines (PCA, autoencoder, Isolation Forest, and LSTM autoencoder) evaluated under identical conditions (+0.147 window-level AUROC over the best baseline). A multimodal ablation over 15~architectural configurations shows that static context via FiLM conditioning is the key enabler, lifting experiment-level multi-signal AUROC by +0.145 over the unimodal baseline (0.729 to 0.874). Separately, a training ablation across 14 design choices reveals that several widely-adopted techniques, including instance normalisation, Mixup, ensembling, test-time augmentation, and stochastic weight averaging, fail to improve or actively degrade generalisation in this data-scarce setting. These negative results expose a fundamental tension between smoothing-based regularisation and anomaly detection, providing practical guidance for multimodal process monitoring deployment.

- **Tags**: `distillation` `multimodal` `rag`


---


## 85. Ringmaster LMO: Asynchronous Linear Minimization Oracle Momentum Method

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18174v1)

- **Summary**: Muon has recently emerged as a strong alternative to AdamW for training neural networks, with encouraging large-scale pretraining results and growing evidence that matrix-structured updates can be faster in practice. Yet Muon, and more generally Linear Minimization Oracle (LMO) based methods, are typically used synchronously. This is problematic in heterogeneous distributed systems, where workers complete gradient computations at different speeds and synchronous training must repeatedly wait for slower workers. In this work, we introduce Ringmaster LMO, an asynchronous LMO-based momentum method for unconstrained stochastic nonconvex optimization. Our method builds on the delay-thresholding idea of Ringmaster ASGD. For SGD-type methods, Ringmaster ASGD achieves optimal time complexity by discarding overly stale gradients. Ringmaster LMO extends this mechanism to general LMO-based updates. We establish convergence guarantees under generalized $(L_0, L_1)$-smoothness and further develop a parameter-agnostic variant with decreasing stepsizes and adaptive delay thresholds. Finally, we translate our iteration guarantees into time complexity bounds under heterogeneous worker computation times. In the classical Euclidean smooth setting, these bounds recover the optimal time complexity of Ringmaster ASGD. Experiments on stochastic quadratic problems and NanoChat language-model pretraining show that the advantages of Ringmaster LMO grow with system heterogeneity and that the method outperforms strong synchronous and asynchronous baselines.

- **Tags**: `pretraining` `rag`


---


## 86. Buffer-Parameterized Machine Learning Surrogate Models for Cross-Technology Signal Integrity Analysis and Optimization

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18170v1)

- **Summary**: Signal integrity (SI) analysis in printed circuit board (PCB) interconnects faces increasing complexity due to diverse integrated circuit (IC) buffer technologies, varying operating conditions, and manufacturing tolerances. Existing machine learning (ML) surrogate models for predicting SI metrics such as the inner eye contour, eye-height (EH), eye-width (EW), and transient waveform features typically rely on fixed buffer parameters, requiring costly new data generation and retraining cycles for every technology shift. This paper introduces a buffer-parameterized ML surrogate modeling methodology capable of handling cross-technology variations without retraining by treating IC buffer characteristics, e.g., clock frequency, supply voltage, rise/fall times, jitter, and internal resistors and capacitors, as dynamic model inputs alongside PCB parameters. To identify the optimal surrogate architecture for this high-dimensional space, a comprehensive benchmarking study compares tree-based methods (RFR/GBM), kernel methods (SVR/KRR), Gaussian process regression (GPR), and neural networks. The framework is subsequently validated on a complex interconnect with 44 design parameters. Results show that while anisotropic GPR excels in low-data regimes, neural networks heavily outperform other models on large datasets. Finally, the practical value of the ML surrogate models is demonstrated through a cross-technology design space exploration and optimization scenario, showcasing massive computational speedups for eye mask compliance checking compared to simulation.

- **Tags**: `benchmark`


---


## 87. Elastic-dLLM: Position Preserving Context Compression and Augmentation of Diffusion LLMs

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18165v1)

- **Summary**: Unlike autoregressive models, which generate one token at a time, dLLMs denoise a chunk of [MASK] tokens jointly and sample one or more tokens per step; despite enabling parallel decoding, this process incurs substantial computational cost due to the large chunk size of masked tokens. We observe that much of this cost is spent on repeatedly processing the preceding context and many [MASK] tokens with the same feature representations, indicating considerable computational redundancy. In this work, we revisit dLLM's redundancy from the perspective of [MASK] tokens. Through systematic analysis, we verify the redundancy of [MASK] tokens while revealing their critical role in providing structural information. Guided by these findings, we propose position-preserving [MASK] token compression and terminal-aware augmentation. By compressing redundant [MASK] computation, this approach accelerates decoding and further provides a natural extension toward context-folding-like long-context scaling under limited input-length constraints for full-sequence dLLMs such as LLaDA-8B-Instruct and LLaDA-1.5. Moreover, for block dLLMs such as LLaDA2.0-mini, it augments the context with a protected terminal [MASK] token to enhance generation quality with negligible overhead.

- **Tags**: `diffusion` `llm`


---


## 88. Foundation Models for Credit Risk Prediction: A Game Changer?

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18147v1)

- **Summary**: Predictive models play a pivotal role in credit risk management, guiding critical decisions through accurate estimation of default probabilities and losses. Extensive research has introduced new modeling techniques, complemented by large-scale benchmarking studies consolidating the state-of-the-art. Today, quasi-standards such as gradient-boosting models paired with SHAP explainers have emerged, yet continuous improvement of risk models remains a top priority. Concurrently, rapid advancements in AI, most notably large language models, have disrupted predictive modeling paradigms. Foundation models, pretrained on extensive datasets from diverse domains, have demonstrated remarkable performance by leveraging prior knowledge. While prevalent in natural language processing and computer vision, foundation models for tabular data have only recently emerged. We conjecture that pretraining on out-of-domain data is particularly beneficial in small-data settings, such as SME lending or specialized corporate portfolios, and may help address longstanding challenges including low default portfolios and class imbalance. This paper benchmarks recently proposed tabular foundation models against a broad set of competitors, including established and advanced machine learning techniques, across two core tasks: PD and LGD modeling. Our evaluation encompasses various datasets, performance indicators, and experimental conditions. We find that tabular foundation models generally perform best across datasets and tasks. Moreover, they offer significant improvement in predictive performance as dataset size shrinks. These results are remarkable given that the models are tested out-of-the-box, without hyperparameter tuning, ensuring ease of use and mitigating computational costs.

- **Tags**: `benchmark` `foundation model` `large language model` `pretraining` `rag`


---


## 89. pyforce-1.0.0: Python Framework for data-driven model Order Reduction of multi-physiCs problEms

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18082v1)

- **Summary**: pyforce is a Python package implementing Data-Driven Reduced Order Modelling techniques for applications to multi-physics problems, mainly set in the Nuclear Engineering world. The package is part of the ROSE (Reduced Order modelling with data-driven techniques for multi-phySics problEms): mathematical algorithms aimed at reducing the complexity of multi-physics models (for nuclear reactors applications), at searching for optimal sensor positions and at integrating real measures to improve the knowledge on the physical systems. With respect to the previous original implementation based on dolfinx package (v0.6.0), version 1.0.0 of pyforce has been completely re-written using pyvista as backend for mesh importing, computing integrals, and visualisation of results; in addition, functions are stored as numpy arrays, improving the ease of use of the package. This choice allows to use pyforce with any software solver able to export results in VTK format.


---


## 90. Wasserstein bounds for denoising diffusion probabilistic models via the Föllmer process

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18069v1)

- **Summary**: This paper studies sampling error bounds for denoising diffusion probabilistic models (DDPMs) in the 2-Wasserstein distance. Our contributions are threefold. (i) Under general Lipschitz-type conditions on the score function and for a broad class of variance schedules, including the cosine schedule, we establish sharp upper bounds that are optimal in both the dimension and the number of steps, and recover several sharp error bounds previously obtained in the literature. (ii) We prove that the same Lipschitz-type conditions, which encompass those commonly imposed on the (learned) score, imply a logarithmic Sobolev inequality and hence a quadratic transportation cost inequality for the DDPM. As a consequence, in settings covered by existing work, an optimal Wasserstein bound, up to a logarithmic factor, follows from the recently obtained sharp error bound in the Kullback-Leibler divergence under geometric-type variance schedules. (iii) We show that for general log-concave target distributions, the optimal Wasserstein error bound remains attainable even without a quadratic transportation cost inequality for the target. Our analysis is based on viewing the DDPM sampler as a discretization of the Föllmer process rather than the conventional reverse Ornstein-Uhlenbeck process.

- **Tags**: `diffusion` `llm`


---


## 91. The MixCount Dataset: Bridging the Data Gap for Open-Vocabulary Object Counting

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.18063v1)

- **Summary**: Object counting is a foundational vision task with over a decade of dedicated research, yet state-of-the-art models still fail systematically in the mixed-object setting that dominates real-world applications such as industrial inspection and product sorting. We show that this gap is strongly driven by limitations in existing training and evaluation data: real counting datasets are prohibitively expensive to annotate and suffer from labeling noise, while existing synthetic alternatives lack diversity and realism. We address this with MixCount, a dataset and benchmark for mixed-object counting designed to target the failure modes of current counting models. To overcome the high cost of constructing and labeling such data, we develop an automatic generation pipeline that synthesizes images, fine-grained textual descriptions, and pixel-perfect counting annotations at scale, eliminating the labeling ambiguity that plagues prior datasets. Evaluating state-of-the-art counting models on MixCount exposes severe degradation in the mixed-object setting. More importantly, training these models on our synthesized data yields substantial gains on real-world benchmarks, reducing MAE by 20.14% on FSC-147 and by 18.3% on PairTally. These results establish MixCount as both a benchmark and a training dataset for fine-grained counting, and demonstrate that our pipeline, which produces effectively unlimited labeled data, helps address a long-standing bottleneck in counting models.

- **Tags**: `benchmark` `research` `vision`


---


## 92. SIREM: Speech-Informed MRI Reconstruction with Learned Sampling

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.18221v1)

- **Summary**: Real-time magnetic resonance imaging (rtMRI) of speech production enables non-invasive visualization of dynamic vocal-tract motion and is valuable for speech science and clinical assessment. However, rtMRI is fundamentally constrained by trade-offs among spatial resolution, temporal resolution, and acquisition speed, often leading to undersampled k-space measurements and degraded reconstructions. We propose SIREM, a speech-informed MRI reconstruction framework that uses synchronized speech as a cross-modal prior. The central idea is that vocal-tract configurations during speech are correlated with the produced acoustics, making part of the image content predictable from audio. SIREM models each frame as a fusion of an audio-driven component and an MRI-driven component through a spatial weighting map. The audio branch predicts articulator-related structure from speech, while the MRI branch reconstructs complementary content from measured k-space data. We further introduce a learnable soft weighting profile over spiral arms, enabling a differentiable study of how k-space arm usage interacts with speech-informed fusion. This yields a unified multimodal formulation that combines audio-driven prediction, MRI reconstruction, and sampling adaptation. We evaluate SIREM on the USC speech rtMRI benchmark against standard baselines, including gridding, wavelet-based compressed sensing, and total variation. SIREM introduces a speech-informed reconstruction paradigm that operates in a substantially higher-throughput regime than iterative methods while preserving anatomically plausible vocal-tract structure. These results establish an initial benchmark for multimodal speech-informed rtMRI reconstruction and highlight the potential of synchronized speech as an auxiliary prior for fast reconstruction. The source code is available at https://github.com/mdhasanai/SIREM

- **Tags**: `benchmark` `multimodal`


---


## 93. FOL2NS: Generating Natural Sentences from First-Order Logic

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.18155v1)

- **Summary**: Translating formal language into natural language is a foundational challenge in NLP, driving various downstream applications in semantic parsing, theorem validation, and question answering. In this study, we introduce First-Order Logic to Natural Sentence (FOL2NS), a neurosymbolic framework designed to generate synthetic FOL formulas and convert them into natural human expressions. It handles deeply nested structures with varying quantifier depths (QD), which are rarely captured by existing corpora. By combining rule-driven modules with fine-tuned language models, FOL2NS enhances the diversity and coverage of the generated samples. In our experiments, we systematically evaluate the framework's capabilities through both character-level analysis and overall performance metrics. Experimental results show that FOL2NS can reliably produce well-formed templates and fluent statements, but it faces challenges in achieving precise semantic representations and natural generation as structural complexity increases.

- **Tags**: `rag`


---


## 94. iPOE: Interpretable Prompt Optimization via Explanations

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.18113v1)

- **Summary**: Prompt optimization has often been framed as a discrete search problem to find high-performing and robust instructions for an LLM. However, the search result might not make it transparent why and where specific prompt changes lead to performance gains. This is in contrast to how humans are instructed for annotation tasks. Here, researchers carefully design annotation guidelines, leading to enhanced annotation consistency. Our paper aims at joining these two approaches and introduces iPOE, a novel interpretable prompt optimization strategy via explanations. We guide the prompt optimization process by automatically created guidelines from explanations of annotation decisions (either automatically generated or from humans). This set of guidelines is furthermore optimized by as series of operations, including removing, adding, shuffling, and merging. The resulting prompt includes guidelines that instruct the annotation, making the decision process of the LLM and the optimization transparent. It therefore supports also laypeople in the area of prompt optimization, particularly in challenging domains requiring expertise. In our experiments on four datasets, we find that iPOE can improves over prompts without guidelines and with random selected guidelines by up to $31\%$ and $35\%$, respectively. Moreover, LLM explanations can replace human explanations in the proposed method.

- **Tags**: `llm` `research`


---


## 95. Token-Space Mask Prediction for Efficient Vision Transformer Segmentation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18177v1)

- **Summary**: Query-based Vision Transformer segmentation models typically reconstruct dense spatial feature maps to predict masks, inheriting design patterns from convolutional architectures. We show that this explicit image-space reconstruction is not required. We introduce TokenMask, a token-space mask head that computes mask logits directly from query-token affinities and performs interpolation in logit space rather than feature space. This reformulation preserves the original linear scoring mechanism while simplifying the computational structure. Across diverse ViT backbones, datasets and segmentation tasks, TokenMask consistently improves efficiency over prior approaches by reducing computational and memory requirements while maintaining competitive accuracy, leading to tangible speedups on NVIDIA Jetson AGX Orin using TensorRT FP16 inference. Overall, TokenMask yields a simpler and more deployment-friendly design for embedded vision systems.

- **Tags**: `efficiency` `transformer` `vision`


---


## 96. Do You Need Text Rectification? Soft Attention Mask Embedding for Rectification-Free Scene Text Spotting

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18173v1)

- **Summary**: End-to-end scene text spotting, which unifies text detection and recognition within a single framework, has witnessed remarkable progress driven by deep learning advances. However, most existing approaches still suffer from incomplete mask proposals caused by multi-scale variation, arbitrary text shapes, and complex background interference, thereby degrading recognition accuracy. In this paper, we propose a novel Soft Attention Mask Embedding module (SAME) that leverages the global receptive field of Transformer encoders to encode high-level features and compute soft attention weights, which are then hierarchically embedded with predicted masks to generate refined text-boundary-aware masks that effectively suppress background noise. Building upon this module, we present SAME-Net, a robust end-to-end text spotting framework that requires neither character-level annotations nor auxiliary text rectification modules. Since the soft attention mechanism is fully differentiable, recognition loss gradients can be back-propagated through the SAME module to the detection branch, enabling joint optimization of detection and recognition objectives. Extensive experiments on challenging benchmarks demonstrate the effectiveness of our approach: SAME-Net achieves 84.02\% end-to-end H-mean on the arbitrarily-shaped Total-Text dataset, surpassing the previous state-of-the-art GLASS by 1.02\% in full-lexicon accuracy without additional training data, and obtains competitive 83.4\% strong-lexicon results on the multi-oriented ICDAR 2015 dataset.

- **Tags**: `benchmark` `embedding` `rag` `transformer`


---


## 97. Xiaomi EV World Model: A Joint World Model Integrating Reconstruction and Generation for Autonomous Driving

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18137v1)

- **Summary**: This report presents a unified technical system addressing the two core capabilities of world models for autonomous driving: world representation and world generation. For world representation, we propose WorldRec, a feed-forward reconstruction architecture driven by sparse scene queries. WorldRec initializes structured queries in 3D space, leveraging them to aggregate cross-view, cross-temporal features, thereby naturally enforcing spatial consistency across frames and yielding compact yet high-fidelity 3D Gaussian scene representations. For world generation, we propose WorldGen, a two-stage training framework of bidirectional pretraining followed by causal fine-tuning through three progressive stages (Teacher Forcing, ODE distillation, and DMD), enabling high-quality online causal video generation in as few as 4 denoising steps. Building on both modules, we further introduce the JWM, which deeply integrates WorldRec and WorldGen to achieve synergistic gains in generation stability, cross-frame consistency, and visual fidelity, providing a solid foundation for closed-loop simulation, data synthesis, and end-to-end training in autonomous driving.

- **Tags**: `distillation` `fine-tuning` `pretraining` `rag`


---


## 98. WinTok: A Win-Win Hybrid Tokenizer via Decomposing Visual Understanding and Generation with Transferable Tokens

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18115v1)

- **Summary**: Building a unified visual tokenizer is essential for bridging the gap between visual understanding and generation. Yet existing approaches struggle with the inherent conflict between these tasks, as a single token space is forced to support both high-level semantic abstraction and low-level pixel reconstruction. We propose WinTok, a concise hybrid tokenizer that achieves a win-win performance by explicitly decoupling the two objectives. WinTok supplements pixel tokens with a set of learnable semantic tokens, effectively mitigating cross-task interference without incurring the computational overhead of dual tokenizers. To further enhance understanding capability, we introduce an asymmetric token distillation mechanism: the semantic tokens are guided by pretrained semantic embeddings from any visual foundation model, enabling them to inherit strong discriminative power while maintaining flexibility. Across 10 challenging benchmarks, WinTok delivers consistent improvements in reconstruction, understanding, and generation. Trained on only 50M open-source data, WinTok surpasses the strong baseline UniTok by 11.2% in classification accuracy and achieves a competitive reconstruction rFID of 0.41, despite using substantially less training data. Code is released at https://github.com/markywg/WinTok.

- **Tags**: `benchmark` `distillation` `embedding` `foundation model`


---


## 99. Embedded ConvNet Ensembles: A Lightweight Approach to Recognize Arabic Handwritten Characters

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18060v1)

- **Summary**: Arabic Handwritten Character Recognition (AHCR) has recently advanced significantly with deep Convolutional Neural Networks (ConvNets). However, many models in the literature are deep and computationally expensive in terms of parameters and FLOPs, limiting their deployment on resource-constrained devices, which are increasingly common. This study addresses this gap by proposing a combination of lightweight embedded ConvNet models and ensemble learning techniques. Extensive experiments were conducted to identify best practices in AHCR, considering training hyperparameters, learning strategies, model choices, and ensemble methods. Results show that embedded models can achieve accuracy comparable to, or even surpassing, heavier architectures. Ensemble learning further enhances performance with only modest computational overhead, particularly under challenging training scenarios. Among the ensembling strategies, soft voting yielded the best overall results.


---


## 100. CATRF: Codec-Adaptive TriPlane Radiance Fields for Volumetric Content Delivery

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18054v1)

- **Summary**: Volumetric media promises next-generation content delivery applications, but its bandwidth demand remains a key bottleneck. Implicit and hybrid volumetric representations reduce model sizes, yet still require careful coding to reach 2D video-like bitrates. We present CATRF, a standard-codec-in-the-loop compression framework for plane-factorized radiance fields. During training, we quantize and pack 2D feature planes into codec-friendly canvases, run a standard codec roundtrip (JPEG/VP9/HEVC/AV1), then unpack and dequantize the decoded features before volume rendering. We use a straight-through estimator (STE) to insert the non-differentiable, standard codec pipeline into the training loop, allowing radiance-field features to adapt directly to the real, client-side codec distortions without introducing any learned codec parameters. On both static and dynamic benchmarks, CATRF consistently achieves a better rate-distortion trade-off over codec-agnostic and learned-codec-in-the-loop baselines, and also outperforms recent compressed 3DGS methods in both compression efficiency and decoding speed. These results highlight a practical path toward low-bitrate, compression-resilient volumetric representations for free-viewpoint video streaming.

- **Tags**: `benchmark` `efficiency`


---


## 101. Efficient 3D Content Reconstruction and Generation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.18052v1)

- **Summary**: Automatic 3D content creation seeks to replace labor-intensive modeling and scanning pipelines with systems that can synthesize or recover 3D assets directly from text or images. Its applications span video games, virtual reality, robotics, and simulation, enabling rapid asset prototyping, diverse interactive world generation, and efficient 3D data collection for training foundation models. Contemporary solutions largely follow two complementary paradigms: (i) text- or image-to-3D generation, which learns priors over 3D geometry and appearance to create novel assets from natural language or a single view image; and (ii) 3D reconstruction, which estimates camera poses and geometry from RGB images. This thesis advances both directions. On the generation side, I introduce Instant3D, which combines multi-view diffusion with feed-forward sparse-view 3D reconstruction to produce high-quality assets in 5-20 seconds. On the reconstruction side, I develop FastMap, a structure-from-motion pipeline that achieves up to 10x speedup over prior state-of-the-art by using first-order optimization with fused GPU kernels extensively, while maintaining comparable pose accuracy and downstream novel view synthesis quality.

- **Tags**: `diffusion` `foundation model`


---


## 102. Here’s why Elon Musk lost his suit against OpenAI

- **Source**: [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137488/elon-musk-suit-openai-verdict/)

- **Summary**: On Monday, the jury in Musk v. Altman dealt Elon Musk a major blow—reaching a unanimous advisory verdict that he had sued OpenAI too late and, as a result, his claims are barred by the applicable statutes of limitations. US District Judge Yvonne Gonzalez Rogers immediately accepted it.&#160; Musk announced on X that he will&#8230;

- **Tags**: `openai`


---


## 103. SandboxAQ brings its drug discovery models to Claude — no PhD in computing required

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/05/18/sandboxaq-brings-its-drug-discovery-models-to-claude-no-phd-in-computing-required/)

- **Summary**: Other venture-backed companies like Chai Discovery and Isomorphic Labs have raced to build better models. SandboxAQ is betting that access is the bigger obstacle and that Claude solves it.

- **Tags**: `anthropic` `claude` `google`


---


## 104. What to expect from Google this week

- **Source**: [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137439/what-to-expect-from-google-this-week/)

- **Summary**: This story originally appeared in The Algorithm, our weekly newsletter on AI. To get stories like this in your inbox first, sign up here. When Google opens its doors tomorrow for its annual developer conference, I/O, it will do so as a clear third place in the foundation model race. A year ago, at Google I/O&#8230;

- **Tags**: `foundation model` `google`


---


## 105. Anthropic has acquired the dev tools startup used by OpenAI, Google, and Cloudflare

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/05/18/anthropic-has-acquired-the-dev-tools-startup-used-by-openai-google-and-cloudflare/)

- **Summary**: Stainless, a New York-based startup, founded in 2022, rose to prominence in the emerging AI industry for automating the creation and maintenance of software development kits, or SDKs — the libraries developers use to interact with APIs.

- **Tags**: `anthropic` `google` `openai`


---


## 106. Elon Musk has lost his lawsuit against Sam Altman and OpenAI

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/05/18/elon-musk-has-lost-his-lawsuit-against-sam-altman-and-openai/)

- **Summary**: Elon Musk's claim that he was mistreated by his OpenAI co-founders failed after nine California jurors decided in a unanimous verdict that his lawsuits had been filed too late.

- **Tags**: `openai`


---


## 107. Musk v. Altman proved that AI is led by the wrong people

- **Source**: [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/932464/musk-v-altman-proved-that-ai-is-led-by-the-wrong-people)

- **Summary**: The tech trial of the year, Musk v. Altman, was ultimately a fight for control. Elon Musk argued that Sam Altman, with whom he helped found the now-massive company OpenAI, shouldn't direct the future of AI. Altman's lawyers, in turn, poked at Musk's own credibility. A jury came to a verdict on Monday after just [&#8230;]

- **Tags**: `openai` `policy` `xai`


---


## 108. All of the updates from Elon Musk and Sam Altman’s battle over OpenAI

- **Source**: [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)

- **Summary**: Sam Altman and Elon Musk are facing off in a high-stakes trial that could alter the future of OpenAI and its most well-known product, ChatGPT. In 2024, Musk filed a lawsuit accusing OpenAI of abandoning its founding mission of developing AI to benefit humanity and shifting focus to boosting profits instead. After nearly a month [&#8230;]

- **Tags**: `chatgpt` `gpt` `openai` `policy` `xai`


---


## 109. Elon Musk loses his case against Sam Altman

- **Source**: [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/932383/jury-verdict-musk-v-altman-openai-trial)

- **Summary**: After around two hours of deliberation, the jury has reached a unanimous verdict in Musk v. Altman, the tech trial of the year. The group found that two claims were barred by the statute of limitations, and a third failed thanks to the dismissal of one of these. The jury here is an advisory jury, [&#8230;]

- **Tags**: `openai` `policy`


---


## 110. Inside Anduril and Meta’s quest to make smart glasses for warfare

- **Source**: [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137412/inside-anduril-and-metas-quest-to-make-smart-glasses-for-warfare/)

- **Summary**: The defense-tech company Anduril has shared new details about the augmented-reality headset for the military it’s prototyping with Meta, including a vision for ordering drone strikes via eye-tracking and voice commands. Quay Barnett, who leads the efforts as a vice president at Anduril following a career in the Army’s Special Operations Command, says his fundamental&#8230;

- **Tags**: `vision`


---


## 111. Amazon Alexa Plus can now create AI-generated podcasts

- **Source**: [theverge_ai](https://www.theverge.com/tech/932375/amazon-alexa-plus-ai-podcasts)

- **Summary**: Alexa Plus, Amazon's upgraded AI assistant, can now generate podcasts on "virtually any topic," according to an announcement on Monday. With the update, Amazon says you can give Alexa Plus a topic, and the AI assistant will offer an overview of what its AI hosts plan to talk about, allowing you to steer the conversation [&#8230;]


---


## 112. The Download: Musk v. Altman week 3, and Trump’s tech trading

- **Source**: [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137407/the-download-musk-altman-trial-trump-tech-trading/)

- **Summary**: This is today&#8217;s edition of The Download, our weekday newsletter that provides a daily dose of what&#8217;s going on in the world of technology. Musk v. Altman week 3: Musk and Altman traded blows over each other’s credibility. Now the jury will pick a side. In the final week of the Musk v. Altman trial,&#8230;


---


## 113. OpenAI and Dell partner to bring Codex to hybrid and on-premise enterprise environments

- **Source**: [openai](https://openai.com/index/dell-codex-enterprise-partnership)

- **Summary**: OpenAI and Dell partner to bring Codex to hybrid and on-premise environments, helping enterprises deploy AI coding agents securely across data and workflows.

- **Tags**: `agent` `codex` `enterprise` `openai`


---


## 114. Amazon’s new Alexa+ powered feature can generate podcast episodes

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/05/18/amazons-new-alexa-powered-feature-can-generate-podcast-episodes/)

- **Summary**: Amazon’s Alexa+ can now generate custom AI podcasts on demand, as the company expands its assistant into a personalized AI content platform.

- **Tags**: `generative`


---


## 115. South Korea’s LetinAR is building optics behind AI glasses

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/05/18/south-koreas-letinar-is-building-the-optics-behind-ai-glasses/)

- **Summary**: A lens the size of a thumbnail — and the South Korean startup that makes it — could become the optical backbone of the AI glasses era.


---


## 116. The Signals That Matter – MIT Insider’s Panel

- **Source**: [mit_tech_review](https://www.technologyreview.com/2026/05/18/1137430/the-signals-that-matter-mit-insiders-panel/)

- **Summary**: 


---


## 117. simonlin1212/TradingAgents-astock

- **Source**: [github](https://github.com/simonlin1212/TradingAgents-astock)

- **Summary**: A股多Agent投研框架 — 适配A股数据源(龙虎榜/游资/解禁等)，7位分析师基于A股规则的辩论决策，基于TradingAgents深度改造，适配大A。A-share multi-agent investment research framework — 7 AI analysts, bull/bear debate, risk assessment。

- **Tags**: `agent` `debate` `research` `risk assessment`


---


## 118. deepelementlab/jupyter-studio

- **Source**: [github](https://github.com/deepelementlab/jupyter-studio)

- **Summary**: The AI-native JupyterLab — open-source Cursor for notebooks. Cmd+K inline edit, multi-step agent with cell-level tools (read/edit/run), chat with @cell/@file context, ghost-text completion, one-click traceback fix. BYO model: Anthropic, OpenAI, Gemini, Ollama, vLLM. Local-first, privacy-first, fully open source.

- **Tags**: `agent` `anthropic` `gemini` `llm` `openai`


---


## 119. AbhishekK130804/Claude-Mythos-AI-Anthropic-App

- **Source**: [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)

- **Summary**: Claude pro free Mythos design Opus Cowork  Sonnet AI Anthropic App: download free PC android apk iOS, Anthropic Claude API key setup, Claude roleplay mythos client, SillyTavern Claude prompt formatting, custom system prompt jailbreak, Mythos AI creative writing app, Claude 3.5 Sonnet Opus API cost, open source LLM frontend, Claude reverse proxy 

- **Tags**: `anthropic` `claude` `jailbreak` `llm`


---


## 120. richard-kim-79/archora-skills

- **Source**: [github](https://github.com/richard-kim-79/archora-skills)

- **Summary**: Academic research agent skills for Claude Code and other Agent Skills-compatible tools. Hypothesis generation, experiment design, paper drafting, peer review simulation, and more.

- **Tags**: `agent` `claude` `research`


---


## 121. prof-little-bear/cc-equity-research

- **Source**: [github](https://github.com/prof-little-bear/cc-equity-research)

- **Summary**: Turn Claude Code into an equity-research agent: 24 analysis skills (Anthropic's open-source bundle + community), a single data MCP, and a personalization layer for investors at any level.

- **Tags**: `agent` `anthropic` `claude` `research`


---


## 122. mdowis/anansi

- **Source**: [github](https://github.com/mdowis/anansi)

- **Summary**: A self-healing web scraper built for hostile sites: selectors repair themselves, browser rendering kicks in when needed, and Chrome TLS fingerprinting evades bot detection. Ships with an MCP server so any LLM can drive a full crawl through conversation.

- **Tags**: `llm`


---


## 123. zimingttkx/QuantumFlow

- **Source**: [github](https://github.com/zimingttkx/QuantumFlow)

- **Summary**: QuantumFlow - Distributed LLM inference scheduling framework with multi-backend support (vLLM, TGI, SGLang), adaptive scheduling strategies, and cluster management.

- **Tags**: `llm`


---


## 124. Siva-Chidambaram12/kalshi-trading-bot

- **Source**: [github](https://github.com/Siva-Chidambaram12/kalshi-trading-bot)

- **Summary**: 🏗 AI trading system for Kalshi prediction markets. kalshi trading bot kalshi trading bot kalshi botFeatures Grok-4 integration, multi-agent decision making, portfolio optimization, and real-time market analysis. Educational/research purposes only kalshi trading bot kalshi bot

- **Tags**: `agent` `research`


---


## 125. ahammadmejbah/Awesome-Datasets-Hub

- **Source**: [github](https://github.com/ahammadmejbah/Awesome-Datasets-Hub)

- **Summary**: A curated collection of datasets for Large Language Models (LLMs), covering medical AI, NLP, multimodal learning, instruction tuning, reasoning, code generation, and evaluation benchmarks.

- **Tags**: `benchmark` `large language model` `llm` `multimodal` `reasoning`


---


## 126. gonemedia/aipointer

- **Source**: [github](https://github.com/gonemedia/aipointer)

- **Summary**: The AI cursor companion. Hold a key, ask a question, get an answer about whatever your cursor is pointing at. Vision LLM overlay for macOS, Windows, Linux. Multi-provider (OpenRouter, Anthropic, OpenAI, Gemini). Voice in/out. MIT licensed. No telemetry.

- **Tags**: `anthropic` `gemini` `llm` `openai` `vision`


---


## 127. PlaceNL2026/okx-agent-trade-kit

- **Source**: [github](https://github.com/PlaceNL2026/okx-agent-trade-kit)

- **Summary**: OKX trading MCP CLI cryptocurrency spot futures swap AI agent Model Context Protocol Cursor Claude npm automated trading crypto API toolkit TypeScript open-source DeFi CEX

- **Tags**: `agent` `claude`


---


## 128. exploitbench/exploitbench

- **Source**: [github](https://github.com/exploitbench/exploitbench)

- **Summary**: ExploitBench measures how far AI agents climb, from reaching vulnerable code, to triggering the bug, to building exploit primitives, to arbitrary code execution.

- **Tags**: `agent`


---


## 129. lynote-ai/humanize-text

- **Source**: [github](https://github.com/lynote-ai/humanize-text)

- **Summary**: Open-source Al text humanizationtoolkit. 4 proven methods totransform Al-generated text intonatural human writing. Translationchain, LLM rewriting, detection-guided feedback loop, and mixed-engine processing.

- **Tags**: `llm`


---


## 130. python-telegramBot/ai-auto-trading

- **Source**: [github](https://github.com/python-telegramBot/ai-auto-trading)

- **Summary**: AI trading bot crypto LLM agent quantitative trading automated trading algorithmic trading Binance Gate.io TypeScript Node.js VoltAgent crypto bot risk management multi-strategy

- **Tags**: `agent` `llm`


---


## 131. dex-original/okx-agent-trade-kit

- **Source**: [github](https://github.com/dex-original/okx-agent-trade-kit)

- **Summary**: okx trading bot okx agent mcp cli cryptocurrency okx api automated trading typescript okx trading bot model context protocol cursor ai trading crypto spot futures okx trading bot npm pnpm okx mcp open source quant defi cex okx trading bot algorithmic trading crypto bot okx trading bot okx api mcp okx trading bot crypto mcp

- **Tags**: `agent`


---


## 132. mikesheehan54/Claude-Code-Design-AI

- **Source**: [github](https://github.com/mikesheehan54/Claude-Code-Design-AI)

- **Summary**: Claude Design: AI UI/UX architect. Screenshot to React, Figma components, Tailwind CSS generator. Prototyping agent, design systems, wireframe renderer. SVG icon creator, dark mode toggle, responsive layout tool. Front-end code export, shadcn/ui integration, vector assets, branding assistant.

- **Tags**: `agent` `claude`


---


## 133. BasZ4ll/Stable-Diffusion-WebUI

- **Source**: [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)

- **Summary**: Stable Diffusion: webui automatic1111 download free, comfyui setup guide, sdxl checkpoint safetensors, lora model civitai, controlnet extension github. SD WebUI Forge launcher, low VRAM optimization, xformers command line arguments, python torch cuda error fix, out of memory solution, txt2img img2img, inpainting, realesrgan upscaler, local pc insta

- **Tags**: `diffusion`


---


## 134. yetone/native-feel-skill

- **Source**: [github](https://github.com/yetone/native-feel-skill)

- **Summary**: An Agent Skill for designing cross-platform desktop apps that feel native — distilled from Raycast's 2.0 deep-dive and reverse engineering of Raycast Beta.app. Eight architectural tenets, four-layer architecture, WebKit/WebView2 survival guide, 75-item ship audit.

- **Tags**: `agent`


---


## 135. CHB-learner/PaperPilot

- **Source**: [github](https://github.com/CHB-learner/PaperPilot)

- **Summary**: AI 文献检索与综述 Agent：支持多源检索、代码仓库定位、开放 PDF 下载、证据链与中英双语报告。

- **Tags**: `agent`


---


## 136. kgmkm/novel2hermes_jp

- **Source**: [github](https://github.com/kgmkm/novel2hermes_jp)

- **Summary**: メモリ機能が強力なhermes-agentと、日本語検索に強い外部メモリvecmemoriを活かし、長文に耐える小説を企画/プロッティング/執筆するためのskills.md

- **Tags**: `agent`


---


## 137. 重塑主流PC，第三代英特尔酷睿开启全民AI轻薄本时代

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419585.html)

- **Summary**: 芯片与系统级双重创新


---


## 138. AI水论文封一年，署名连坐！arXiv最严新规来了，陶哲轩附议

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419528.html)

- **Summary**: 生成论文远比消化容易


---


## 139. openJiuwen社区开源新招：重磅发布JiuwenSwarm，拉开群体智能“养蜂”序幕

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419515.html)

- **Summary**: 底层范式变了


---


## 140. 华为“养”出半个具身智能创业圈

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419414.html)

- **Summary**: 正在经历一次罕见的人才外溢。


---


## 141. 上交x创智x瑞金联合发布CX-Mind：胸片诊断进入“可验证推理”时代

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419396.html)

- **Summary**: 五项维度全部排名第一


---


## 142. 8B模型做生物实验：实验步骤顺序不乱、剂量无幻觉｜ICLR 2026

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419386.html)

- **Summary**: 超越GPT-4o

- **Tags**: `gpt` `gpt-4` `gpt-4o`


---


## 143. 信通院&清华提出FedRE：用「纠缠」搞定联邦学习三难困境 | CVPR 26

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419373.html)

- **Summary**: 隐私和性能我全都要


---


## 144. 黄仁勋北京必吃榜我们都尝了！后海酒吧老板：他答应以后每年来一次

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419278.html)

- **Summary**: 老黄严选北京游


---


## 145. LeCun炮轰Hinton：他认可LLM就是想摆烂退休了！

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419272.html)

- **Summary**: Lecun这次是真跟Hinton爆了……

- **Tags**: `llm`


---


## 146. 30万奖金池，这道汉语方言对话题等你来解丨第十一届信也科技杯全球AI算法大赛

- **Source**: [qbitai](https://www.qbitai.com/2026/05/419256.html)

- **Summary**: 更有NLPCC2026直通名额


---


## 147. Simple Approximation and Derivative Free Inference-Time Scaling for Diffusion Models via Sequential Monte Carlo on Path Measures

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.17850v1)

- **Summary**: iffusion-based generative models increasingly rely on inference-time guidance, adding a drift term or reweighting mixture of experts, to improve sample quality on task-specific objectives. However, most existing techniques require repeated score or gradient evaluations, introducing bias, high computational overhead, or both. We introduce \texttt{URGE}, Unbiased Resampling via Girsanov Estimation, a derivative-free inference-time scaling algorithm that performs path-wise importance reweighting via a Girsanov change of measure. Instead of computing gradient-based particle weights in previous work, \texttt{URGE} attaches a simple multiplicative weight to each simulated trajectory and periodically resamples. No score, no Hessian, and no PDE evaluation is required. We establish an equivalence between path-wise and particle-wise SMC: the Girsanov path weight admits a backward conditional expectation that recovers the previous particle-level weights, guaranteeing that both schemes produce the same unbiased terminal law. Empirically, \texttt{URGE} outperforms existing inference-time guidance baselines on synthetic tests and diffusion-model benchmarks, achieving better generation quality, while being significantly simpler to implement and fully gradient-free.

- **Tags**: `benchmark` `bias` `diffusion` `generative` `mixture of experts`


---


## 148. Feature Learning in Linear-Width Two-Layer Networks: Two vs. One Step of Gradient Descent

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.17767v1)

- **Summary**: We study feature learning in two-layer neural networks within the linear-width regime, where the number of hidden neurons, sample size, and input dimension scale proportionally. While recent work has analyzed feature learning via a single step of gradient descent, such updates are fundamentally limited: they are approximately rank-one, capturing only a single direction, and require the target function to have an information exponent of one. In this paper, we go beyond one-step updates to provide a full characterization of the features learned during the second step of gradient descent with step-sizes $η_1 \asymp N^{α_1}$ and $η_2 \asymp N^{α_2}$ for $α_1, α_2 \in [0,0.5)$. We derive a sharp spectral characterization of the updated weights, demonstrating they behave as a spiked random matrix with multiple outliers, each corresponding to a learned direction. We show that the number of these outliers is determined by the scaling parameters $α_1$ and $α_2$ through $\lfloor \frac{α_2}{1/2 - α_1} \rfloor$. Furthermore, by analyzing the alignment between these learned directions and the target function, we identify a qualitative gap between training with independent versus reused batches. While independent batches restrict learning to directions with an information exponent of one, batch reuse enables the second update to capture directions even when the information exponent exceeds one, under the condition that $α_1, α_2$ are chosen properly. This confirms that the benefits of batch reuse, previously observed in finite-width regimes, persist in the high-dimensional linear-width limit. By characterizing these early-phase spectral transitions, our work establishes a tractable mathematical framework for studying optimization and feature learning phenomenology in modern overparameterized networks.

- **Tags**: `alignment`


---


## 149. On efficient robust regression with subquadratic samples

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.18042v1)

- **Summary**: We revisit the problem of robust linear regression under Gaussian covariates with an unknown covariance matrix of condition number $κ$. For this fundamental problem, significant gaps remain in our understanding of the trade-offs among sample complexity, condition number, runtime, and prediction error for efficient algorithms. Our first result is a near-linear-time algorithm that uses $\widetilde{O}(d/ε^4)$ samples, where $d$ is the dimension and $ε$ is the corruption rate, and achieves prediction error $O(\sqrt{εκ})$ under the condition $εκ\lesssim 1$, improving over all prior works. We complement this result with a Statistical Query (SQ) lower bound showing that efficient SQ algorithms achieving error $o(\sqrt{εκ})$ when $εκ\lesssim 1$ require queries that take $Ω(d^2)$ samples to simulate. Finally, we prove a low-degree polynomial lower bound that gives fine-grained evidence that, without assumptions such as $εκ\lesssim 1$, efficient algorithms may require $\tildeΩ\left(\min\{dε^{2}κ^{2},\ ε^{2}d^{2}\}\right)$ samples to significantly outperform the trivial estimator that always guesses $0$.


---


## 150. A data-driven Fourier-mixture neural-network method for density estimation

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.18019v1)

- **Summary**: We propose a data-driven Fourier-trained neural-network method for estimating fixed-horizon probability densities from empirical characteristic-function (CF) information. The estimator is a positive Gaussian--Laplace mixture with closed-form CF, so training can be performed directly in Fourier space while preserving nonnegativity and unit mass. We consider two sampling settings. In the direct i.i.d. sampling setting, the method is trained against an empirical CF constructed from i.i.d. samples. In the resampling-based pseudo-sampling setting, it is trained against an empirical pseudo-CF constructed from dependent data by resampling. For the direct i.i.d. case, we derive an expected $L_2$ error bound that separates Fourier truncation, empirical training error, discretization, and CF sampling error. For the pseudo-sampling case, we obtain a conditional analogue with two additional pseudo-law discrepancy terms. We develop a multidimensional extension of the framework and analyze its computational complexity. Numerical experiments show competitive performance relative to Expectation--Maximization on Gaussian-mixture benchmarks, clear gains on heavy-tailed targets, $L_2$ error decay consistent with the theory in a well-specified setting, and effective estimation of one-year Australian equity return law from resampled dependent data.

- **Tags**: `benchmark`


---


## 151. From Saddle Points Toward Global Minima: A Newton-Type Method on Wasserstein Space

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.17963v1)

- **Summary**: We study the minimization of non-convex functionals over the Wasserstein space. While recent work has showed that perturbed Wasserstein gradient methods can avoid saddle points for benign landscapes, existing approaches remain essentially first-order and do not provide fast local convergence once the iterates enter a neighborhood of a global minimizer. We propose Wasserstein Saddle-Free Newton (WSFN), a second-order method that preconditions the Wasserstein gradient by a regularized square root of the squared Wasserstein Hessian. This construction preserves attraction toward directions of positive curvature while inducing repulsion along directions of negative curvature, thereby overcoming the tendency of standard Wasserstein Newton dynamics to be attracted to saddles. We also establish second-order sufficient optimality conditions on Wasserstein space for strict local minimality. Under regularity and benign landscape assumptions, we prove that WSFN escapes saddle regions and reaches an $α$-neighborhood of a global minimizer in polynomial time, with improved dependence on saddle parameters compared with prior perturbed first-order methods. Once inside this neighborhood, we show that WSFN converges linearly in $L^2$-Wasserstein distance to a non-degenerate global minimizer. Finally, we present a particle-based implementation of the method.


---


## 152. Conditional Predictive Inference for General Structured Data with Group Symmetries

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.17934v1)

- **Summary**: We study distribution-free predictive inference for data with group symmetries, aiming to establish near-conditional coverage guarantees beyond exchangeability for structured data. While many predictive inference methods achieve a target coverage level, most provide marginal coverage. In practice, conditional predictive inference is often preferred, as it quantifies uncertainty for black-box predictions given observed attributes, thereby accommodating heterogeneity. Although many efforts have pursued efficient conditional coverage, existing methods rely on the i.i.d. or exchangeable assumption, often violated in structured settings such as networks, clusters, and imaging data. Recently, SymmPI introduced a unified approach to predictive inference under group symmetries beyond exchangeability; nevertheless, its guarantees remain marginal and do not account for population heterogeneity. To bridge this gap, we introduce C-SymmPI, a framework that achieves near-conditional coverage under general data structures with group symmetries, extending beyond exchangeability to cover networks, cluster-level data, and related structures. Inspired by relaxed multi-accuracy, our approach reformulates conditional coverage as miscoverage error over a user-specified function class. We establish theoretical guarantees under distributional invariance and distribution shift, and derive convergence rates for linear and RKHS function classes, recovering state-of-the-art results in the exchangeable setting as special cases. For computational efficiency, we develop two variants: a projection-based algorithm for high-dimensional observations, and a sampling-based algorithm for large or infinite groups. We demonstrate effectiveness on hierarchical and network data. Empirical results show that C-SymmPI delivers more informative and stable conditional coverage with improved accuracy compared to existing methods.

- **Tags**: `efficiency` `rag`


---


## 153. A Unified Framework for Data-Free One-Step Sampling via Wasserstein Gradient Flows

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.17808v1)

- **Summary**: We develop a unified theoretical framework for data-free one-step sampling from unnormalized target distributions based on Wasserstein gradient flows. For a broad class of standard f-divergence objectives, we show that the induced velocity field admits the universal form $\mathbf{V}(x)=w(r(x))\,β(x)$, where $β(x)=\nabla \log (p(x)/q(x))$ is shared across objectives and $w$ is determined solely by the choice of divergence. This decomposition shows that standard f-divergence drifts share the same asymptotic target distribution $p$ and differ primarily in how they redistribute transient repair effort across under-covered regions. To formalize this distinction, we derive a one-step regional-response theory for a soft under-coverage functional and obtain a compression--elasticity identity that links divergence choice to the geometry of mass transport into under-covered regions. We further extend the framework beyond the f-divergence family to the Log-Variance (LV) divergence, analyze how the reference distribution alters the resulting drift structure, and motivate a practical LV-inspired surrogate for data-free training. Based on this theory, we instantiate the framework with a KDE-based implementation and describe a complementary normalizing-flow route, enabling one-step inference after training. Experiments on multimodal Gaussian-mixture benchmarks are consistent with the theoretical predictions and demonstrate effective one-step sampling on these targets.

- **Tags**: `benchmark` `multimodal` `rag`


---


## 154. Self-Distillation is Optimal Among Spectral Shrinkage Estimators in Spiked Covariance Models

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.17778v1)

- **Summary**: Self-distillation has emerged as a promising technique for improving model performance in modern machine learning systems. We develop the statistical foundations of self-distillation in spiked covariance models, by introducing and analyzing a broad class of estimators, namely spectral shrinkage estimators. We establish that for spiked covariance matrices with $s$ spikes, $s$-step self-distillation achieves optimal performance among spectral shrinkage estimators, outperforming well-known estimators in statistics and machine learning. Moreover, we show that $s$ steps are necessary for optimality: any $(s-k)$-step distilled estimator is strictly suboptimal for $1 \leq k \leq s$. For the special subclass of isotropic covariances, we show that optimally tuned Ridge regression performs best among spectral shrinkage estimators. We also study a federated approach where multiple data centers share spectral shrinkage estimators and a common server seeks to aggregate them to achieve optimal performance. In this case, we find that the best local rule again takes the form of self-distillation, though it differs from the optimal rule when data are hosted centrally on a single server. Together, our results elucidate why self-distillation improves predictive performance and provide a broader statistical framework connecting it with classical shrinkage-based methods.

- **Tags**: `distillation`


---


## 155. Comparing Two Categorical Gini Correlations with Applications to Classification Problems

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.17763v1)

- **Summary**: This article proposes an inferential framework for comparing predictor importance in classification problems with categorical response variables. The approach is based on the categorical Gini correlation (CGC) proposed by Dang et al. (2020), a measure of dependence between numerical predictors and categorical outcomes. Predictor importance is evaluated by testing differences in CGCs across competing predictor groups. The proposed methodology accommodates predictors of arbitrary and unequal dimensions and allows for dependence between predictor groups. Asymptotic normality of the test statistic is established under both the null and alternative hypotheses, and the resulting test is shown to be consistent. In addition to deriving the asymptotic distribution, a nonparametric bootstrap procedure is developed as an alternative approach to inference. Simulation studies, along with applications to breast cancer and human activity recognition datasets, demonstrate the effectiveness of the proposed framework.


---


## 156. Faculty Orientations Shape Adoption of AI in Research and Teaching

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.18140v1)

- **Summary**: Despite the widespread availability of large language models (LLMs) in higher education, instructors vary substantially in their adoption and use of these tools, and the reasons for this variation remain poorly understood. A mixed-methods survey of 90 STEM faculty in the Research Corporation for Science Advancement (RCSA) Cottrell community examined relationships between AI use, attitudes, institutional context, and instructional practice. Exploratory factor analysis identified a coherent construct, \textit{AI pedagogical orientation}, that strongly predicted self-reported AI use across research, teaching, and other professional activities. Qualitative analysis indicated that this construct reflected differing views about the role AI should play in disciplinary thinking, learning, and expertise development, rather than simply positive or negative attitudes toward AI. Institutional initiatives, demographic variables, and information sources showed comparatively weak associations with AI use. The results suggest that existing technology-adoption models may not fully explain adoption in contexts where technologies interact directly with disciplinary reasoning and knowledge production.

- **Tags**: `large language model` `llm` `reasoning` `research`


---


## 157. 产能将激增，前三星芯片负责人预测明年下半年内存将显著降价

- **Source**: [36kr](https://36kr.com/newsflashes/3815597194010113?f=rss)

- **Summary**: 周二，韩国国家工程院第285届NAEK论坛上，三星电子设备解决方案部门常任顾问、三星半导体（DS）部门前总裁庆桂显（Kye-hyun Kyung）表示，中国企业正在积极扩大产能，随着存储芯片供应量的激增，市场格局可能会在明年下半年或2028年上半年发生转变。他补充称，如果大型科技公司的资本支出回报率下降，就有可能削减投资。这样，不仅价格会下降，内存需求本身在2028年后也可能萎缩。（财联社）


---


## 158. “奕信通”完成B+轮融资

- **Source**: [36kr](https://36kr.com/newsflashes/3815586722930184?f=rss)

- **Summary**: 36氪获悉，“奕信通”今日正式宣布完成 B+ 轮融资，由中车资本独家战略投资。此前，公司已完成B轮融资，由国际500强企业领衔投资，多家知名机构跟投。两轮融资累计金额近2亿元人民币。本轮资金将主要投向核心产品研发、产能扩建、海外市场布局以及团队建设四个方向，支撑奕信通在数据中心与智算中心液冷赛道的下一阶段成长。


---


## 159. 鲸跃动力获星海图数千万元种子轮投资，用「数据+模型+末端执行」打造开箱即用的Robo Labor丨涌现新项目

- **Source**: [36kr](https://36kr.com/p/3814860909600261?f=rss)

- **Summary**: <p><strong>文｜王欣逸</strong></p>
  <p><strong>编辑｜邱晓芬</strong></p>
  <h3><strong>一句话介绍</strong></h3>
  <p>鲸跃动力成立于2026年，以「数据+模型+末端执行」闭环，提供面向场景、可快速部署的Robo Labor（机器人劳动力），让物理劳动力像AWS算力一样，可订阅、可弹性扩容、开箱即用，替代人类从事高危、繁重、脏乱、重复（Deadly/Difficult/Dirty/Duplicate）的物理作业。</p>
  <h3><strong>融资进展</strong></h3>
  <p>近日，鲸跃动力已完成由星海图独家领投的数千万元种子轮融资，深渡资本担任独家财务顾问。</p>
  <p>本轮融资将用于团队增长、产品的量产交付、专家技能的研发以及数采运营相关工作。</p>
  <p>星海图表示：“具身智能的下半场，拼的是‘数据效率×模型泛化×末端执行’的系统能力。鲸跃动力锚定数据主线，专注在真实场景实现快速交付迭代，与我们追求物理世界数据闭环的理念高度一致。团队兼具数据、模型与交付的稀缺基因，这种团队组合在行业里并不多见，因此我们看好它从高质量数据出发走向全球领先的具身智能应用先锋。”</p>
  <h3><strong>产品及业务</strong></h3>
  <p>鲸跃动力瞄准To B市场，围绕数据，专注在真实场景实现快速交付迭代，提供了「数据+模型+末端执行器」的软硬件一体化解决方案。</p>
  <p>在海外，Sunday、‌Generalist AI、Genesis AI等公司的实践，验证了数据是具身智能规模化落地的第一性原理，并收敛在了「Ego-centric+UMI」，即「第一人称视角+通用操作接口」的数据方案。</p>
  <p>鲸跃动力创始人李广宇认为，过度追求超大模型的复杂度没有必要，只需在真实数据、场景化模型、末端执行形成闭环，即可快速实现工程化交付与规模化落地。</p>
  <p>因此，鲸跃动力采用了<strong>「数据采集能力+模型能力+灵巧操作深度认知」</strong>模式，实现具身智能在场景中的落地。</p>
  <p>鲸跃动力的核心壁垒主要体现在以下三个层面：</p>
  <p>1.&nbsp;<strong>自研Ego-centric+UMI数据采集系统：</strong>能实现亚毫米级位姿定位与亚毫秒级多源时间同步，覆盖视觉、力觉、位姿与环境交互信号，并在端侧实时场景理解分析，保证数据质量。</p>
  <p>2.&nbsp;<strong>百万小时数据管线与人类在环策略：</strong>建立数据管线，具备百万小时级清洗、标注、分析能力。通过大规模真实数据覆盖复杂工况，同时引入Human-in-the-Loop（人类介入决策）范式，通过人工的即时纠偏能力，保证机器人在Day 1可用的前提下持续进化。</p>
  <p>3.&nbsp;<strong>自研3D世界模型和专家技能：</strong>包括深度空间理解与精准移动操作能力，并在数据底座之上构建高保真物理认知引擎。基于这一模式，机器人不只是做到“识别物体”，还能做到理解重力、摩擦、形变趋势与交互边界，真正实现从“感知-执行”到“认知-预测-自适应”的范式跃迁。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_94431e998e6a4099927f59cce0d87bca@6162492_oswg1294793oswg1080oswg915_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">△鲸跃动力的数据采集可视化，图源：企业提供&nbsp;</p>
  <p>据介绍，鲸跃动力的业务模式也得到了客户和产业方的认可，以物料搬运装卸（Material Handling）的应用场景为例，客户可以将机器人无缝嵌入现有的业务流，实现室内外全场景自主移动、高精度搬运与柔性装卸、标准载具操作等能力，切实解决行业痛点。</p>
  <p>目前鲸跃动力已和制造和物流行业的多家头部企业开展了合作，推动其产品在多个场景落地。</p>
  <h3><strong>团队介绍</strong></h3>
  <p>鲸跃动力CEO李广宇博士毕业于美国南加州大学（USC）电子工程系，曾任北京人形机器人创新中心具身数据与灵巧操作负责人，从0到1搭建灵巧操作与具身数据团队，主导RoboMIND多模态具身数据集、具身智能体“慧思开物”等标杆项目，在数据与模型层面有丰富的积累；此前在滴滴、轻舟智航主导构建百万级自动驾驶数据闭环与仿真系统，兼具具身智能与自动驾驶双重产业实战经验。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_47e4c9d827d442d692c61c02543d810f@6162492_oswg141341oswg1051oswg884_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">△鲸跃动力创始人兼CEO李广宇博士，图源：企业提供&nbsp;</p>
  <p>核心团队覆盖数据、模型、硬件、软件、全球化商务全链条，由来自极智嘉、新石器、轻舟智航、北京人形、理想、小米、滴滴等头部企业的核心骨干组成。团队成员毕业于USC、清华、浙大、中科大等顶尖高校，在机器人学、强化学习与多模态大模型领域具备深厚积累，还拥有RoboMaster等顶级赛事冠军。</p>
  <p>团队具备丰富的海外研发、合规认证与本地化部署经验，拥有从前沿研发到万台量产、百万级数据交付的完整落地能力。</p>
  <h3><strong>Founder思考</strong></h3>
  <ul>
   <li><strong>一家公司必须成为细分领域的最优解，才能长期赢得竞争。</strong></li>
  </ul>
  <p>To B的残酷性在于，有一台能跑的机器人是不够的，有一台单位经济模型（UE）为正的机器人也不够。必须成为细分领域的最优解，才能长期赢得竞争。</p>
  <p>产品能真正落地的关键在于：企业高度了解现有工作流，能将产品严丝合缝嵌入业务链条，并在人力消耗最大、ROI最显性的环节下刀，硬件设计需要接地气，数据采集敢于野蛮生长，才能逐渐跑通场景、价值验证、数据回流与产品迭代的闭环。</p>
  <ul>
   <li><strong>场景型机器人公司会成为未来的赢家。</strong></li>
  </ul>
  <p>目前，行业壁垒正从单点算法转向系统能力，企业核心的竞争点在于：一是“单位泛化能力的数据成本”，二是“场景规模化部署密度”。</p>
  <p>数据效率决定了我们能否以极低的边际成本，将机器人的操作能力泛化至新物料、新载具与新场地；落地密度则决定了能否在单一场景内形成规模效应。</p>
  <p>未来的赢家，会是那些能用最精准数据撬动最大泛化边界、并用最高密度占领核心场景的“场景型机器人公司”。</p>
  <ul>
   <li><strong>机器人领域的标准化产品公司正在涌现。</strong></li>
  </ul>
  <p>目前，硬件供应链日趋成熟，数据基建规模化，大模型、Agent能力爆发，新的AI驱动范式有望让机器人公司从传统“项目制定制集成”转向“标准化产品公司”。</p>
  <p>让机器人企业能够以产品化的思维定义硬件、以Agent的逻辑交付价值，在垂类场景中将智能化做到极致，配合标准化硬件与清晰的产品定义，完全有能力实现高爆发、规模化的商业出货。</p>
  <ul>
   <li><strong>鲸跃动力想要的生态位是：数据+应用。</strong></li>
  </ul>
  <p>全球产业对柔性、低成本、高可靠物理劳动力的需求从未衰减。</p>
  <p>具身智能将重演自动驾驶的演进轨迹，从早期Robotaxi（无人驾驶出租车）的尝试，到辅助驾驶的规模化量产，再到无人配送、干线物流、矿卡等垂直场景的延伸。对具身智能而言，其也将延续验证期、工程收敛期到商业爆发期的路径发展。</p>
  <p>鲸跃动力在打造一个生态友好的通用的技能平台，我们擅长数据驱动、闭环以及落地部署的环节，更关注“末端执行器+技能”的组合价值，我们希望客户在接上硬件、打通系统和传感器之后，直接调技能就能解决需求。</p>
  <p><strong>封面来源｜企业提供</strong></p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_a70eb22f5ba24cfc8a7fe36f2b228854@6162492_oswg158012oswg900oswg335_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">欢迎交流～</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_3dc8cb3ac74a46fdb039fe5dcd25bd7c@6162492_oswg66852oswg900oswg500_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">扫码加入「智涌AI交流群」</p>

- **Tags**: `agent`


---


## 160. 清华大学深圳国际研究生院与英博数科举行GPU云平台应用论坛暨校企智算合作签约仪式

- **Source**: [36kr](https://36kr.com/newsflashes/3815566042488322?f=rss)

- **Summary**: 近期，恰逢清华大学深圳国际研究生院二十五周年，“智算赋能·云启新程”GPU云平台应用论坛暨校企智算合作签约仪式在清华大学深圳国际研究生院举行。活动围绕GPU云平台应用、高校科研算力需求、校企智算合作等议题展开深入交流，并完成校企合作签约与免费云算力交付。据了解，英博数科是国内较早专注于AI智算服务的企业之一，长期围绕GPU云服务、智算基础设施建设与运营、平台化算力服务等方向持续布局。


---


## 161. 高瓴出手了一家AI体育科技公司，曾获李泽湘天使轮融资｜硬氪首发

- **Source**: [36kr](https://36kr.com/p/3805660478184966?f=rss)

- **Summary**: <p>作者｜黄楠</p>
  <p>编辑｜袁斯来</p>
  <p>硬氪获悉，AI体育科技公司SportVision近日已完成天使+轮融资，高瓴创投（GL Ventures）领投，谦恒资本担任独家财务顾问。本轮资金将重点用于核心技术研发、产品量产落地及市场的拓展推广。其新款AI网球训练相机产品计划发售中。</p>
  <p>SportVision隶属于深圳思博威视体育科技有限公司‌，长期专注运动算法研发与硬件产品应用、构建AI智能教练体系，此前已获得李泽湘教授旗下清水湾基金的天使轮投资。</p>
  <p>过去几年，运动科技赛道几乎被硬件厂商重新定义了一遍。发球机让“一个人练球”成为可能，运动相机令“训练过程的记录”不再需要专人跟拍，智能手表/手环把心率、步频、消耗卡路里等量化成精确的长期数据记录。</p>
  <p>尽管每一类产品都跑出了规模不小的公司，但它们各自停留在陪练、记录、监测的单点功能上——数据相互独立、能力无法贯通，难以为用户提供连贯、整体的个性化支持。</p>
  <p>运动人群的深层渴望远不止于被记录，还有被指导、被陪伴、被看见进步。一场更底层的变革正在发生：从“记录工具” 到 “AI运动Copilot”的跨越，运动科技赛道正在重写。</p>
  <p>工具只需完成指令，而Copilot则可以像教练一样理解状态、识别动作、纠正习惯，甚至在运动热情消退时成为那个督促陪伴的人。</p>
  <p>要补上这道体验鸿沟，用户需要的不只是更强性能的硬件，更是一个能把整合所有信息、真正理解运动者的“大脑”。这也正是SportVision精准切入的核心位置。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260515/v2_37caeed72e0f40a383144bc0682f1dc6@6022551_oswg3843123oswg4096oswg3072_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">全运会现场所使用的SportVision设备（图源/企业）</p>
  <p>SportVision创始人陈楷夫本科毕业于吉林大学物理学院严济慈班、哥伦比亚大学机器人学硕士，曾在MMLab从事姿态识别与目标检测算法研究；身为一名前游泳运动员，他对运动学习、动作纠正与训练效率的痛点有切身感知，正是这段经历，让他决心用AI技术破解非结构化运动数据难题，构建一个可规模化、可复制的个性化运动产品和训练体系。</p>
  <p>联合创始人杨晨旭是资深网球爱好者，曾在腾讯、字节负责AI产品开发。多位团队核心成员来自商汤、字节、阿里、腾讯等头部科技企业，具备AI算法、软硬件一体化研发与全球化品牌运营能力，已形成了从技术研发到产品落地的完整闭环。</p>
  <p>公司起步初期，SportVision选择从羽毛球场景切入进行关键产品验证，首款产品“好球哇”是一套羽毛球AI运动相机方案。设备可实时采集球场画面，通过视觉算法自动识别并捕捉用户的运动高光时刻，为普通运动爱好者、专业运动员及赛事场景，提供高光集锦、赛事直播、运动数据分析等一体化服务。</p>
  <p>这套系统落地了全国数十家头部羽毛球馆，并获得林丹、王睁茗、龚睿那等世界冠军在内的多位种子用户支持。在赛事侧，该系统也服务了全运会残特奥会、粤港澳大湾区羽毛球比赛、深圳杯等多场关键赛事。</p>
  <p>但它真正的价值，远非硬件本身，而是持续运行中沉淀的海量运动数据。</p>
  <p>在拍摄过程中，SportVision自研算法能实时分析并智能预测运动轨迹，根据比赛进程自动调整摄像角度，对复杂的多人运动场景进行针对性学习优化。从世界冠军到刚入门的爱好者，从专业教练的指导语料到普通用户的练习习惯，场馆设备每天运行十几个小时，能收集到各类各样的泛化数据。每一场球、每一次挥拍、每一个得分瞬间，都在被系统记录、拆解、分析。</p>
  <p>这是一座难以被发球机或运动相机采集到的数据矿。</p>
  <p>运动学习的基本机制分为三个阶段：认知阶段（通过视觉掌握动作要领）、联想阶段（在反复练习中形成神经通路）、自主阶段（动作固化成为肌肉记忆）。其中联想阶段的及时反馈最为关键：动作做对还是做错需要在几秒内被确认，否则错误动作就会被“练熟”。</p>
  <p>陈楷夫向硬氪指出，“此前，多数运动AI解决方案仍停留在‘事后分析’阶段，用户完成运动后上传视频、系统给出复盘报告。但这种模式错过了最佳纠正窗口。”</p>
  <p>因此，SportVision想搭建的，是一套基于实时交互的预判式AI。</p>
  <p>“好的运动员不一定是好教练，好教练的价值在于知道怎么教。”陈楷夫说，“我们要做的，是把教练的教法萃取出来，让AI学会怎么教。”</p>
  <p>随着网球、羽毛球、匹克球等拍类运动在全球范围内持续升温，用户对运动提升的需求愈发迫切。传统的请教练模式面临成本高、频次低的矛盾，一周请一两次教练，用户练习时无法得到反馈，对于向网球这样的运动，可能需要一年才能从入门到实现“对打社交”。正反馈周期长，也使得很多人停留在了入门阶段。</p>
  <p>这正是SportVision的核心壁垒所在：那些在球场上日夜运转的设备，收集到的海量数据。从骨骼点识别到动作模式分析，从专业运动员的动作库到普通用户的练习轨迹，这些数据构成了可迁移的技术底座，能够在各类拍类运动中得以技术复用和迁移。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260515/v2_e83ef89e76db4051a2eb79f7cddfcee4@6022551_oswg203901oswg1080oswg1440_img_jpg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p class="img-desc">SportVision首款网球AI&nbsp;Copilot产品（图源/企业）</p>
  <p>“我们做的不是一款运动相机，而是构建未来运动人群个性化AI教练的世界模型。”陈楷夫告诉硬氪，“用户甚至不需要思考‘我该怎么练’，而是由系统主动管理你的运动进步。”</p>
  <p>硬氪获悉，SportVision首款网球AI&nbsp;Copilot产品正在紧密的研发流程中。以相机为载体，系统可识别用户运动动作并与专业标准动作比对，实时反馈纠正建议；同时，结合教练指导场景，生成个性化训练方案，让用户在独自练习时也能获得针对性、科学化的AI陪练指导。</p>
  <p>该产品概念此前已在CES 2026上展出，首发市场聚焦欧美地区。这里拥有了全球密度最高的网球用户群体，也是付费意愿与消费能力最突出的核心市场。</p>
  <p>回到AI时代运动科技竞争的底层逻辑迁移，当大模型逐渐消解知识鸿沟，竞争的壁垒不再停留于算法参数，而是向两端迁移——一端是数据的密度与深度，另一端是场景的介入与闭环。</p>
  <p>SportVision长期积累的稀缺数据资产，正在成为其下一代AI教练产品的技术底座。从情绪价值到功能性与情绪价值兼具、从记录到指导，从单一品类到拍类运动通用技术底座，这家公司正在尝试的命题是，加速推动运动科技从“工具”到“AI Copilot”的关键升级。</p>

- **Tags**: `copilot` `vision`


---


## 162. 禾盛新材：经核实，熠知电子CPU库存量偏低

- **Source**: [36kr](https://36kr.com/newsflashes/3815522669682436?f=rss)

- **Summary**: 36氪获悉，就“市场传出公司参股公司熠知电子的CPU已经卖断货了，新增10万颗产能下个月提前到货，新品9000系列已经锁定几十万颗产能，直接导致公司股价涨停，请问是否属实？”的问题，禾盛新材在互动平台回复称，经与熠知电子核实，熠知电子CPU库存量偏低，目前已在筹划下单补库存。熠知电子非公司控股，目前仍处于亏损中，请注意投资风险。


---


## 163. 银河证券：云服务行业进入需求放量、量价共振的上行周期

- **Source**: [36kr](https://36kr.com/newsflashes/3815507571564296?f=rss)

- **Summary**: 36氪获悉，银河证券研报称，词元消耗量持续上行，对应全社会AI推理需求规模化放量，对阿里云为代表的云服务商构成确定性利好。伴随词元成为智能时代统一价值结算单位，云计算商业模式正发生根本性重构，行业逐步脱离传统服务器租赁、时长计费的IaaS模式，全面转向以词元消耗为核心的MaaS智能服务按量计费体系。推动云厂商高毛利AI服务收入扩容，优化整体盈利结构，行业进入需求放量、量价共振的上行周期。


---


## 164. 8点1氪丨贾跃亭又融资4.77亿元；巨力索具旗下十余家企业已注销；超越茅台，A股“新股王”诞生

- **Source**: [36kr](https://36kr.com/p/3815459487587847?f=rss)

- **Summary**: <h2>今日热点导览</h2>
  <ul>
   <li>瑞幸咖啡正式上线两款含酒精的特调饮品</li>
   <li>京张高铁试点推出“自行车随身行”服务</li>
   <li>马斯克：计划今年进行首例用于治疗失明的Neuralink植入手术</li>
   <li>韩国法院要求三星电子罢工行动不得影响产量</li>
   <li>多家理财公司集中提前终止理财产品</li>
  </ul>
  <h2>TOP 3 大新闻</h2>
  <p><strong>贾跃亭又拿到7000万美元投资</strong></p>
  <p>贾跃亭发布视频，宣布法拉第未来近期完成了7000万美元（现汇率约合4.77亿元人民币）机构投资者募资，并将启动战略、产品技术&amp;业务、财务、资本、AI体系五大变革。贾跃亭表示，其目标包括FFAI市值重回2021年上市水平，2027年第四季度实现经营性现金流为正，五年内在EAI人形与仿生机器人领域成为北美真实场景部署量前三的机器人公司+北美EAIMPV领军者。贾跃亭还表示，要将FF真正重构为一家Physical AI生态公司。两年内实现过去12年没有完成的梦想，进入“0借口、0内耗、结果导向”的战斗状态，全力兑现对股东和用户的承诺。（IT之家）</p>
  <p><strong>巨力索具旗下十余家企业已注销</strong></p>
  <p>36氪获悉，近日，巨力索具因涉嫌信息披露误导性陈述违法违规，被证监会立案调查。天眼查App显示，巨力索具股份有限公司成立于2004年12月，法定代表人为杨建国，注册资本9.6亿人民币，经营范围包括应急装备、装备专用工装及工具和箱组的设计、生产和销售等，由巨力集团有限公司、杨建忠、香港中央结算有限公司等共同持股。对外投资信息显示，该公司对外投资26家企业，其中10余家企业处于存续状态，包括巨力索具（河南）有限公司、河北巨力应急装备科技有限公司等，其他10余家企业已注销。</p>
  <p><strong>联讯仪器股价反超贵州茅台，成为A股新的股王&nbsp;</strong></p>
  <p>5月18日，联讯仪器盘中扩大涨幅至13%，股价反超贵州茅台，成为A股“新股王”，该股较发行价上涨超15倍。截至5月18日11时许，联讯仪器最高涨至1361元/股，涨幅高达16.32%。与此同时，贵州茅台由涨转跌，股价探至1330元之下。此前相继登上A股“股王”宝座的寒武纪（688256）、源杰科技（688498），5月相继迎来2025年年度权益分派。</p>
  <p>公开资料显示，联讯仪器4月24日登陆A股，发行价81.88元/股，上市14个交易日来，目前股价较发行价上涨15.6倍。据公开资料显示，联讯仪器是国家级专精特新“小巨人”企业，专注于高速通信、电性能、光芯片及半导体晶圆芯片等领域测试仪表与设备的研发、制造，是国内高端电子测量与半导体测试设备领域的硬核龙头。（澎湃新闻）</p>
  <h2>大公司/大事件</h2>
  <p><strong>何立峰会见美国超威半导体公司董事会主席兼首席执行官苏姿丰</strong></p>
  <p>5月18日下午，中共中央政治局委员、国务院副总理何立峰在人民大会堂会见美国超威半导体公司董事会主席兼首席执行官苏姿丰。何立峰指出，上周中美两国元首在北京举行重要会晤，达成一系列重要共识。在两国元首战略引领下，两国经贸团队达成了总体平衡积极的成果，这将为下一步的中美经贸合作与世界经济注入更多确定性和稳定性。欢迎包括超威半导体公司在内的跨国公司把握中国发展机遇，深化互利合作。苏姿丰积极评价两国元首会晤成果，表示愿继续拓展在华业务，持续加大在华投资。(新华社）</p>
  <p><strong>美陪审团驳回马斯克对OpenAI的诉讼</strong></p>
  <p>当地时间5月18日，美国陪审团裁定，美国开放人工智能研究中心（OpenAI）及其首席执行官萨姆·奥尔特曼无需就“偏离慈善使命”一事对埃隆·马斯克承担责任，原因是马斯克提起诉讼时间过晚。当天晚些时候，马斯克表示，将就这一裁决向美国第九巡回上诉法院提起上诉。此前，马斯克对OpenAI及其首席执行官奥尔特曼提起诉讼，指控OpenAI最初邀请马斯克资助一个致力于造福人类的非营利AI研究机构，但如今却专注于盈利。（央视新闻）</p>
  <p><strong>张朝阳：搜狐未入局大模型研发，将聚焦AI应用落地</strong></p>
  <p>36氪获悉，在2026搜狐科技年度论坛上，搜狐CEO张朝阳表示，“搜狐并未入局大模型第一阵营的研发，大模型研发需要雄厚的资金实力和技术背景，企业应基于自身业务基础理智选择。”他提到，搜狐将聚焦AI应用落地，在提升编程效率、节约运营成本的同时，对内容生成保持克制，保持内容中立性，规避AI带来的内容乱象风险。</p>
  <p><strong>腾讯音乐：收购喜马拉雅的事项已经完成</strong></p>
  <p>36氪获悉，腾讯音乐在港交所公告，于2026年5月18日，根据并购协议的条款，收购喜马拉雅的事项已经完成，据此，喜马拉雅相关股东及喜马拉雅的雇员持股计划参与者持有的喜马拉雅权益性证券已予以注销，以换取并购对价，该对价包括（视适用调整而定）总额最高为12.6亿美元的现金及最多总数1.75亿股本公司A类普通股（包括本公司于交割时新发行的A类普通股，以及本公司授出的以股权为基础的激励相关的A类普通股）。于收购事项交割后，喜马拉雅已成为本公司的全资附属公司。</p>
  <p><strong>川投新能源公司总经理刘亮被遣返回国</strong></p>
  <p>据中央纪委国家监委网站，近日，在中央反腐败协调小组国际追逃追赃工作办公室统筹协调和公安部等部门协助下，经四川省监察机关、公安机关与有关国家执法机关密切合作，外逃职务犯罪嫌疑人刘亮在境外落网并被遣返回国。刘亮，男，1979年1月出生，川投新能源公司总经理，涉嫌严重职务违法犯罪，于2026年4月外逃，同月四川省资阳市监察机关对其立案调查。办案机关积极开展国际执法合作，于近日将其缉捕归案。（界面新闻）</p>
  <p><strong>英特尔CEO称代工业务取得进展</strong></p>
  <p>英特尔CEO陈立武在当地时间周一接受采访时表示，该公司的外部代工业务正在稳步发展，成为其扭亏为盈的关键一环。“代工业务非常重要，”陈立武表示，“它是重要的国家资产之一。”（新浪财经）</p>
  <p><strong>瑞幸咖啡上线两款含酒精的特调饮品&nbsp;</strong></p>
  <p>5月18日，瑞幸咖啡正式上线两款含酒精的特调饮品，并且属于饮料酒的范畴，正式布局“微醺”经济。记者了解到，这两款含酒精饮品是瑞幸对全国市场的一次测试，后续或还有进一步的计划。在业内看来，瑞幸布局微醺赛道，意在盘活闲置门店时段资源，提效增收。记者在北京部分瑞幸门店看到，两款年度特调饮品已经上线，但只有部分门店可以提供含酒精版。（红星新闻）</p>
  <p><strong>韩国法院要求三星电子罢工行动不得影响产量</strong></p>
  <p>据央视新闻消息，韩国水原地方法院5月18日批准了三星电子公司提出的部分禁令请求，责令该公司工会必须确保即将开始的全面罢工行动“不影响产量”，“不得导致这家全球重要的存储芯片制造商生产原料受损”。据悉，这实际上是给三星电子这次史上最大规模罢工计划“踩了急刹车”。</p>
  <p>今年3月中旬，由超过6.6万名三星电子工会成员参与表决的投票结果显示，93.1%的工会成员赞成罢工。全面罢工将于5月21日至6月7日举行。据悉，三星电子作为全球重要的存储芯片制造商，一旦发生罢工，可能进一步加剧由全球人工智能数据中心建设持续升温带来的全球半导体供应趋紧局面，其影响或波及汽车、计算机及智能手机等多个行业。三星电子劳资双方此前就2026年薪资问题进行了多轮谈判，但双方就部分议题的分歧持续扩大，谈判最终破裂。（央视新闻）</p>
  <p><strong>多家航司下调国际航线燃油费，国内航线刚上调&nbsp;</strong></p>
  <p>国内航线燃油附加费自5月16日再度上调后，多家航司却在陆续下调国际航线的燃油附加费。香港航空宣布，自今日（5月18日）开始下调多条航线的燃油附加费。其中中国香港前往内地的地区航线，燃油附加费由290港元下调至190港元；香港前往日韩、新马泰等则由389港元下调至339港元。在此之前，国泰航空和香港快运已宣布自5月16日起下调部分区域的燃油附加费。其中香港始发长途航班从1560港币下调至1362港币，中程航班从725港币下调至633港币，短途航班从389港币下调至339港币。下调幅度在12%左右。这也是中东冲突爆发后，多家航司首次对核心航线燃油附加费进行下调。（第一财经）</p>
  <p><strong>5月19日起，铁路部门在京张高铁试点推出“自行车随身行”服务</strong></p>
  <p>据新华社消息，为更好地满足旅客多样化出行需求，铁路部门5月19日起在京张高铁北京北至崇礼间各车站间运行的G字头动车组列车试点推出“自行车随身行”服务，旅客可通过12306客户端线上预约并付费，乘车时经车站安检和规范包装，可携带符合规定的自行车同车出行，将为广大骑行爱好者跨区域出行提供更多便利。试点初期，“自行车随身行”服务定价88元/辆，旅客可在乘车结束后180日内通过铁路12306客户端开具电子发票。（新华社）</p>
  <p><strong>戴尔将与谷歌和SpaceX等公司展开合作</strong></p>
  <p>戴尔科技在上一季度为其“AI工厂”产品线新增1,000家客户，使其总客户数达到了5000家。戴尔正在推出多款新产品以协助企业搭建AI应用，其中包括一款名为“Dell Deskside Agentic AI”（戴尔桌面智能体AI）的产品。此外，戴尔还与谷歌和SpaceX等公司展开合作，将AI模型与工具引入企业自身的内部网络中。（财联社）</p>
  <p><strong>SpaceX将迎关键试飞&nbsp;</strong></p>
  <p>SpaceX计划于周二进行一次关键的试飞，发射其星舰巨型火箭的升级版，代号V3。这次发射正值SpaceX上市关键阶段，消息透露预计该公司最早在下月IPO，并可能在本周三公开招股书。与此同时，SpaceX在与贝索斯的蓝色起源竞争，为NASA的阿尔忒弥斯计划开发星舰，供其在2028年的载人登月任务中使用。目前来看，星舰的研发进度落后于NASA对SpaceX的预期。该火箭原计划于2023年首飞，但去年的失败延缓了其发展进程。星舰最近一次试飞，也是其第11次试飞，发生在七个月前。（财联社）</p>
  <p><strong>NextEra拟以660亿美元收购Dominion，或创史上最大规模电力并购纪录</strong></p>
  <p>5月18日消息，据报道，美国公用事业巨头NextEra Energy目前正就收购竞争对手Dominion Energy进行谈判，该笔交易方案主要以股票交换形式进行，对Dominion的估值约为每股76美元，总价约660亿美元。若最终达成，这将成为迄今为止电力行业规模最大的一笔交易。NextEra计划以约0.8股自身股票交换1股Dominion发行在外的股票，交易总额中还将包含一小部分现金成分。交易完成后，NextEra的股东将持有合并后新公司约75%的股份。（界面新闻）</p>
  <p><strong>马斯克：计划今年进行首例用于治疗失明的Neuralink植入手术&nbsp;</strong></p>
  <p>马斯克表示，旗下Neuralink技术能帮助部分失明者恢复视力，计划今年进行首例用于治疗失明的Neuralink植入手术。</p>
  <p>据了解，Neuralink是一个美国神经科技和脑机接口公司，由伊隆·马斯克和八名其他联合创办者创办，负责研发植入式脑机界面技术。公司的总部在旧金山。Neuralink于2016年成立，并于2017年3月公之于众。2019年7月17日，Neuralink对外宣布该公司研发的一款脑机接口系统（财联社）</p>
  <p><strong>五粮液：2025年度百亿分红两月内到账，严格兑现200亿元分红承诺</strong></p>
  <p>5月18日，五粮液2026年第一次临时股东会对《2025年度利润分配方案》进行了审议，五粮液副董事长、总经理华涛表示，2025年度分红资金将在两个月内准确、及时划入全体股东账户。五粮液2025年中期已分红100亿元，本次拟再分红100.07亿元。五粮液践行高比例分红，严格兑现《2024—2026年股东回报规划》承诺，连续3年每年度现金分红总额不低于200亿元（含税）。（证券时报）</p>
  <p><strong>美国连锁快餐品牌Wendy's将进入中国市场</strong></p>
  <p>5月18日在美国连锁快餐品牌Wendy's官网上看到，该品牌国际特许经营重点市场亚太区域中出现了中国市场。早前，Wendy's在2026年第一季度的财报中称，公司已经签署一项特许经营协议，计划未来10年在中国建设最多1000家餐厅。Wendy's称合作方是“一家在中国拥有数十年经验的大型餐饮运营商，以强待客能力闻名、深刻理解中国消费者。”但没有公布这家运营商的名称。此外，财报显示，Wendy's2026年一季度全球销售额同比下降5.5%，美国同店销售下降7.8%，国际市场销售额增长6.0%。（界面新闻）</p>
  <p><strong>贵州茅台：优化茅台酒线下门店营业时间及i茅台App开售时间</strong></p>
  <p>36氪获悉，据贵州茅台消息，为进一步贴近广大消费者日常工作与生活节奏，更好地满足广大消费者购酒需求，自2026年5月19日起，贵州茅台酒线下门店（含专卖店、自营店）每日营业时间由原9:00—18:00调整为10:00—20:00，i茅台App所有在售贵州茅台酒每日开售时间由原9:00起调整为20:00起。</p>
  <p><strong>多家理财公司集中提前终止理财产品</strong></p>
  <p>近期，招银理财、光大理财、华夏理财、宁银理财等多家理财公司密集披露旗下部分产品提前终止公告。记者梳理公告信息发现，本轮理财产品提前终止主要涉及四类情形：一是产品收益达标触发止盈条款，由理财公司主动收官；二是受投资者集中赎回影响，产品规模持续缩水，最终被动清盘；三是结合产品实际运作表现与市场整体走势，管理人主动选择终止产品；四是结构性理财产品触发合约预设的提前终止条件。（证券日报）</p>
  <p><strong>个人养老金基金产品再现集中“上新”</strong></p>
  <p>近期，个人养老金基金产品再度出现集中“上新”现象，相关产品数量由此达到319只。然而，养老产品快速发展的另一面，却是仍有不少投资账户“开而不投”。对此，业内人士认为，个人养老金业务正从开户数量扩张状态逐步转向账户管理的新阶段。未来，买方投顾有望凭借专业、精细化的服务能力，激活休眠账户与养老投资市场。（上证报）</p>
  <p><strong>美股三大指数收盘涨跌不一，理想汽车跌超9%</strong></p>
  <p>36氪获悉，5月18日收盘，美股三大指数涨跌不一，道指涨0.32%，纳指跌0.51%，标普500指数跌0.07%。大型科技股涨跌互现，特斯拉跌超2%，英伟达跌超1%，Meta、苹果小幅下跌；奈飞涨超3%，Arm涨超2%，微软、亚马逊、谷歌小幅上涨。热门中概股跌多涨少，理想汽车跌超9%，蔚来、小鹏集团跌超3%，爱奇艺跌超2%，京东跌超1%，拼多多小幅下跌；腾讯音乐涨超6%，B站涨超2%，微博、百度涨超1%。</p>
  <p><strong>苹果拟6月展示新操作系统，引入AI写作助手等功能</strong></p>
  <p>苹果公司正为下一代iPhone和iPad操作系统准备一系列人工智能功能，包括语法检查器和新的快捷指令选项，此举旨在缩小与竞争对手设备在AI功能上的差距。据知情人士透露，这些功能计划在iOS 27和iPadOS 27中推出。新增功能包括新的AI辅助写作工具、使用自然语言创建系统级快捷指令的能力，以及自定义壁纸生成功能。（新浪财经）</p>
  <h2>上市进行时</h2>
  <p><strong>浙江时迈药业股份有限公司-B向港交所提交上市申请书</strong></p>
  <p>36氪获悉，据港交所文件，浙江时迈药业股份有限公司-B在港交所提交IPO申请，独家保荐人为华泰国际。</p>
  <p><strong>数据中心运营商DayOne正考虑在新加坡和美国双重上市</strong></p>
  <p>据报道，一位知情人士称，全球数据中心运营商DayOne正考虑在新加坡和美国进行双重首次公开发行（IPO），不过目前新加坡IPO尚无具体计划。媒体周日早些时候报道称，DayOne最初考虑仅在纽约上市，但已被新加坡证券市场官员说服进行双重上市。由于该信息尚未公开，消息人士要求匿名。媒体今年2月曾报道，DayOne计划通过在美国上市筹集50亿美元，公司估值可能达到200亿美元。（新浪财经）</p>
  <h2>AI最前沿</h2>
  <p><strong>Anthropic据悉将向金融稳定委员会简报AI模型Mythos发现的网络防御漏洞</strong></p>
  <p>5月18日消息，据报道，Anthropic已同意向金融稳定委员会（FSB）成员简报其AI模型Mythos的相关情况。Anthropic将重点简报Mythos所识别出的、全球金融体系网络防御方面存在的脆弱性。FSB目前正着手起草一份关于金融体系中应用AI的稳健实践报告，并计划于下月发布该报告以征求意见。（界面新闻）</p>
  <p><strong>AI数据中心致光纤价格暴涨，交货期限延长至20周以上</strong></p>
  <p>人工智能训练和推理集群需要比传统云基础设施更密集的互联架构，这让用于数据传输的光纤陷入供不应求之中。据Rebio Group估计，今年北美光纤需求预计将增长22%至25%，而供应增长则仅有12%至19%。另据Data Center Dynamics报告称，大批量买家的交货周期已延长至20周，而小批量买家的交货周期甚至长达一年。（财联社）</p>
  <p><strong>腾讯AI设计智能体协作平台Ardot正式开启公测</strong></p>
  <p>36氪获悉，5月18日，腾讯AI设计智能体协作平台Ardot正式开启公测。Ardot是一款支持多人实时协作UI/UX设计工具，主要面向设计师和产品经理；覆盖从视觉设计、代码交付、团队协作与资产流转的软件设计全流程。用户可以用自然语言描述界面需求，Ardot实时流式生成可编辑的设计初稿，并一键转代码，也支持直接导入Figma文件，完整保留原有布局、样式和组件，实现零成本迁移。</p>
  <h2>大公司财报</h2>
  <p><strong>爱奇艺：一季度总收入62.3亿元，会员收入环比增长</strong></p>
  <p>36氪获悉，爱奇艺发布2026年第一季度财报。财报显示，一季度爱奇艺总收入62.3亿元。其中，会员服务收入42.0亿元，环比增长2%。在线广告服务收入12.4亿元，内容发行收入3.6亿元，其他收入4.3亿元。</p>
  <p><strong>百度：一季度营收321亿元，AI业务收入136亿元</strong></p>
  <p>36氪获悉，百度发布2026年第一季度财报。财报显示，一季度营收321亿元，上年同期营收324.52亿元。一般性业务收入260亿元，同比增长2%；其中AI业务收入136亿元，占百度一般性业务收入的52%，已连续多个季度增长；GPU云收入同比增长184%。百度创始人李彦宏表示，AI业务收入占比的首次过半，标志着AI已成为百度的核心驱动力。</p>
  <h2>投融资</h2>
  <p><strong>“极壳科技”获5000万美元B+轮融资</strong></p>
  <p>36氪获悉，近日，外骨骼品牌“极壳科技”宣布完成5000万美元B+轮融资。此轮融资由蚂蚁集团和美团龙珠领投，Sofina、Granite Asia跟投，高鹄资本担任独家财务顾问。此轮融资将加速极壳在技术研发、全球市场拓展及消费场景应用方面的布局。</p>
  <p><strong>“众见科技”完成数千万元三轮融资</strong></p>
  <p>36氪获悉，智能眼镜企业“众见科技”已完成数千万元三轮融资，投资方为韶音、高秉强教授旗下高锋耐心基金、昊辰资本、SEEFund、上市公司光峰科技、高秉强教授个人等，此次融资主要用于研发推进，目前初代产品已完成落地。奇域资本将担任独家财务顾问。</p>
  <p><strong>“绮算法”完成数千万元融资</strong></p>
  <p>36氪获悉，宠物大模型健康公司“绮算法”、智谱“Z计划”生态企业，近日完成数千万元融资，投资方为启赋资本与聚恒创投。本轮资金将主要用于产品迭代、模型能力深化及市场拓展。</p>
  <p><strong>“华羽先翔”完成超亿元Pre-A+轮融资，蚂蚁集团领投</strong></p>
  <p>36氪获悉，近日，国内全倾转eVTOL企业“华羽先翔”完成超亿元Pre-A+轮融资，本轮融资由蚂蚁集团领投、彼岸时代及复星创富跟投。融资资金将重点用于加速鸿鹄系列eVTOL的适航取证，以及低空出行及商业场景的落地与创新。</p>
  <h2>酷产品</h2>
  <p><strong>中国自主研发生产的103号赛级汽油正式投入使用&nbsp;</strong></p>
  <p>近日，在2026环塔克拉玛干汽车摩托车越野拉力赛中，中国自主研发生产的103号赛级汽油正式投入使用——这是国内首批实现工业化生产的103号高标号赛级汽油，填补了国内高性能赛车燃油的空白，结束了中国顶级赛事用油长期依赖进口的局面。（央视新闻）</p>
  <p><strong>海光信息新一代终端CPU单核主频达到5.15GHz</strong></p>
  <p>36氪获悉，近日，海光信息新一代终端CPU在液氮极限散热环境下完成性能验证测试，单核主频达到5.15GHz，刷新国产终端CPU主频纪录，意味着国产CPU处理器首次正式迈入5GHz时代。测试数据显示，海光新一代CPU拥有约30%的极限性能释放空间，为后续风冷、水冷常规散热方案的迭代优化，积累了极具价值的工程实测数据。</p>
  <p><strong>灵童机器人发布新一代桌面人形机器人，启动1000台全球共创计划</strong></p>
  <p>36氪获悉，近日，上海灵童机器人（Figurobot）正式启动社区共创活动，宣布面向全球专业用户免费发放1000台桌面人形机器人，可用于二次开发与内容共创。灵童最新发布的桌面机器人“念”高度约60厘米，内部集成30个自研毫米级力矩关节舵机，具备30个自由度，可完成站立、行走、转身、蹲起及舞蹈动作。</p>
  <p><strong>科学家首创用DNA引导CRISPR基因编辑</strong></p>
  <p>美国佛罗里达大学工程学院团队开发出全球首个DNA引导的CRISPR编辑系统，颠覆了基因编辑领域长期以来依赖RNA引导的铁律。这项研究最新刊发于《自然·生物技术》，为疾病诊断与治疗提供了更安全、精准且经济的解决方案。该技术被认为重写了基因编辑的“说明书”，同时也可为下一代生物医学工具开发奠定基础。（科技日报）</p>
  <p class="editor-note"><strong>整理</strong>｜开心&nbsp;</p>

- **Tags**: `agent` `anthropic` `openai`


---


## 165. 氪星晚报 ｜百度：一季度营收321亿元，AI业务收入136亿元；马斯克预计今年美国将广泛使用自动驾驶汽车；巨力索具旗下十余家企业已注销

- **Source**: [36kr](https://36kr.com/p/3814695536336387?f=rss)

- **Summary**: <h2>大公司：</h2>
  <p><strong>索辰科技：物理AI业务目前尚处于布局初期</strong></p>
  <p>36氪获悉，索辰科技公告，公司股票于2026年5月14日至5月18日连续三个交易日内收盘价格涨幅偏离值累计达到30%，属于股票交易异常波动情形。公司近期实施的募投项目“物理合成数据核心技术基座构建与多领域场景示范应用项目”尚处于筹备阶段，若出现募集资金投资项目未能顺利实施、新技术开发进度不达预期、研发遭遇技术瓶颈甚至失败，将会对公司经营业绩造成一定影响。公司物理AI业务目前尚处于布局初期。物理AI技术研发投入大、技术迭代快，存在研发进度不及预期、核心技术迭代风险；同时下游行业应用场景拓展、商业化变现存在不确定性，若市场需求、行业政策、技术竞争格局发生不利变化，物理AI业务收入及盈利贡献存在不及预期风险。</p>
  <p><strong>智元WITA成为全国首例完成大模型备案的具身智能交互模型</strong></p>
  <p>36氪获悉，根据上海市网信办最新公告的上海市生成式人工智能服务备案情况，智元WITA成为全国第一款实现合规备案的具身智能交互大模型，标志着中国具身智能产业从“技术验证”进入“合规商用”的新阶段。依托智元“三智一体”全栈技术体系，智元WITA核心应用于人形机器人交互场景。</p>
  <p><strong>上交所：上周新增8家IPO受理企业</strong></p>
  <p>36氪获悉，据“上交所企业上市服务”消息，本期（5月11日—5月17日）新增8家受理企业，其中上交所主板1家，科创板3家，创业板3家，北交所1家。截至5月17日，今年新增31家受理企业。截至5月17日，各板块在审企业共295家。其中上交所62家（主板18家，科创板44家），深交所61家（主板17家，创业板44家），北交所172家。截至5月17日，2026年已公布终止审查（撤材料+否决/终止注册）企业20家，其中上交所7家（主板3家，科创板4家），深交所创业板1家，北交所12家。</p>
  <p><strong>腾讯音乐：收购喜马拉雅的事项已经完成</strong></p>
  <p>36氪获悉，腾讯音乐在港交所公告，于2026年5月18日，根据并购协议的条款，收购喜马拉雅的事项已经完成，据此，喜马拉雅相关股东及喜马拉雅的雇员持股计划参与者持有的喜马拉雅权益性证券已予以注销，以换取并购对价，该对价包括（视适用调整而定）总额最高为12.6亿美元的现金及最多总数1.75亿股本公司A类普通股（包括本公司于交割时新发行的A类普通股，以及本公司授出的以股权为基础的激励相关的A类普通股）。于收购事项交割后，喜马拉雅已成为本公司的全资附属公司。</p>
  <p><strong>爱奇艺：一季度总收入62.3亿元，会员收入环比增长</strong></p>
  <p>36氪获悉，爱奇艺发布2026年第一季度财报。财报显示，一季度爱奇艺总收入62.3亿元。其中，会员服务收入42.0亿元，环比增长2%。在线广告服务收入12.4亿元，内容发行收入3.6亿元，其他收入4.3亿元。</p>
  <p><strong>百度：一季度营收321亿元，AI业务收入136亿元</strong></p>
  <p>36氪获悉，百度发布2026年第一季度财报。财报显示，一季度营收321亿元，上年同期营收324.52亿元。一般性业务收入260亿元，同比增长2%；其中AI业务收入136亿元，占百度一般性业务收入的52%，已连续多个季度增长；GPU云收入同比增长184%。百度创始人李彦宏表示，AI业务收入占比的首次过半，标志着AI已成为百度的核心驱动力。</p>
  <p><strong>巨力索具旗下十余家企业已注销</strong></p>
  <p>36氪获悉，近日，巨力索具因涉嫌信息披露误导性陈述违法违规，被证监会立案调查。天眼查App显示，巨力索具股份有限公司成立于2004年12月，法定代表人为杨建国，注册资本9.6亿人民币，经营范围包括应急装备、装备专用工装及工具和箱组的设计、生产和销售等，由巨力集团有限公司、杨建忠、香港中央结算有限公司等共同持股。对外投资信息显示，该公司对外投资26家企业，其中10余家企业处于存续状态，包括巨力索具（河南）有限公司、河北巨力应急装备科技有限公司等，其他10余家企业已注销。</p>
  <h2>投融资：</h2>
  <p><strong>“华羽先翔”完成超亿元Pre-A+轮融资，蚂蚁集团领投</strong></p>
  <p>36氪获悉，近日，国内全倾转eVTOL企业“华羽先翔”完成超亿元Pre-A+轮融资，本轮融资由蚂蚁集团领投、彼岸时代及复星创富跟投。融资资金将重点用于加速鸿鹄系列eVTOL的适航取证，以及低空出行及商业场景的落地与创新。</p>
  <p><strong>“极壳科技”获5000万美元B+轮融资</strong></p>
  <p>36氪获悉，近日，外骨骼品牌“极壳科技”宣布完成5000万美元B+轮融资。此轮融资由蚂蚁集团和美团龙珠领投，Sofina、Granite Asia跟投，高鹄资本担任独家财务顾问。此轮融资将加速极壳在技术研发、全球市场拓展及消费场景应用方面的布局。</p>
  <h2>新产品：</h2>
  <p><strong>酷开发布企业AI操作系统</strong></p>
  <p>36氪获悉，近日，深圳市酷开网络科技股份有限公司举办“场景智能·硅基管理”发布会，正式推出原生AI企业操作系统——酷开Happy Work AIOS Lite MVP。该系统已实现从生活场景到企业经营场景的全维度覆盖，完成多场景AI生态闭环落地。</p>
  <h2>今日观点：</h2>
  <p><strong>马斯克预计今年美国将广泛使用自动驾驶汽车</strong></p>
  <p>埃隆·马斯克周一表示，他预计今年晚些时候，无需人类驾驶的自动驾驶汽车将在美国更加普及。马斯克通过视频连线在特拉维夫举行的“智能出行峰会”上发言时称，得克萨斯州的三个城市已有无人驾驶汽车在没有安全监视员的情况下运行，并补充说今年这一模式将扩展至全美。（新浪财经）</p>
  <h2>其他值得关注的新闻：</h2>
  <p><strong>2026电影总票房已超145亿元</strong></p>
  <p>据票务平台数据，截至今天下午，2026年电影票房已超145亿元。五一档新片长尾效应持续释放，其中《给阿嬷的情书》连续九天蝉联单日票房榜首。（央视新闻）</p>
  <p><strong>特朗普：本应要求获得更多英特尔公司的股份</strong></p>
  <p>美国总统唐纳德・特朗普在周一出版的杂志采访中表示，他本应代表美国政府要求获得更多英特尔股份。特朗普政府去年持有英特尔10%的股份，并宣布向这家芯片制造商投资约100亿美元，用于在美国境内新建或扩建工厂。交易完成八个月后，美国政府持有的英特尔股份市值已超过500亿美元。（新浪财经）</p>
  <p><strong>国家药监局：我国4月批准注册医疗器械产品318个</strong></p>
  <p>今天从国家药监局获悉，我国4月共批准注册医疗器械产品318个。其中，境内第三类医疗器械产品272个，进口第三类医疗器械产品20个，进口第二类医疗器械产品26个。 (央视新闻)</p>


---


## 166. 番茄小说正推动 AI 动漫上院线，开放头部IP改编权限｜36氪独家

- **Source**: [36kr](https://36kr.com/p/3810598875307780?f=rss)

- **Summary**: <p>作者｜兰杰 李晓霞</p>
  <p>编辑｜乔芊</p>
  <p>36氪独家获悉，据多位接近字节跳动人士消息，字节旗下的番茄小说正在推动AI动漫上院线。在这一过程中，会开放番茄小说平台头部IP的改编权限。</p>
  <p>之于番茄小说，如何更好地挖掘平台上好IP的潜力和商业价值，是一个亟待解决的难题。</p>
  <p>一方面，以文字形式为载体的IP内容，缺乏统一的视觉形象，使得平台上的IP难以有联名、衍生品等更丰富的变现形式。另一方面，AI漫剧这一新事物迅速发展壮大，其中不乏改编自番茄小说IP的粗制滥造之作。这些内容不但没能延长好IP的生命力，反而形成了一种消耗。此时，通过可登陆院线的影视内容来探索平台IP的更多可能性，不失为一种好的尝试。</p>
  <p>另据上述知情人士表示，字节跳动内部为番茄IP定下了影响力的目标，“想让行业内外的人觉得番茄的出品是精品的、正向的。”这一需求落到具体的业务上，上院线会是个不错的答卷。</p>
  <p>早在2023年年底，番茄小说就官宣成立了“番茄影视”和“番茄动漫”两大厂牌，推动平台IP的影视化。过去两年间，番茄影视先后与腾讯视频、爱奇艺和优酷等长视频平台合作，推动了《十日终焉》《我在精神病院学斩神》等平台头部IP的改编，但这些合作多停留在IP授权阶段。</p>
  <p>虽然番茄系（字节旗下以番茄小说、红果短剧等为主的业务）并不愁关于钱的问题，但显然成本高、回报周期长的长视频生意，并不符合依赖大手笔投流、需要市场快速反馈的“字节逻辑”。直到AI的出现，大幅降低了成本、提高了效率。</p>
  <p>36氪还从另一位知情人士处获悉，红果漫剧侧如今正在采购120分钟不分集的长内容，这也是当下各大视频平台争相竞逐的方向。</p>
  <p>之所以上线AI动漫内容，而不是AI仿真人内容，或许与当前AI大模型的能力有关。行业头部的AIGC创作者向36氪表示，如今视频生成大模型的能力已经可以做到生产120分钟的长内容，但是在仿真人这一赛道上，人物、场景的一致性依旧是个难题，而动漫内容可以通过部分突出的人物形象设计——例如彩色的头发、雀斑等，一定程度上弥补一致性的不足。</p>
  <p>回顾番茄系并不算漫长的发展历程，它可以说是字节跳动在文娱领域的一次突围。在番茄小说问世之前，字节始终未能建立起足够的内容能力和IP积累。而如今，从小说到短剧，再到漫剧，番茄系已具备了IP开发的全链条能力。</p>
  <p>与此同时，番茄系显然不满足于仅仅停留在当下的免费市场，而是在探索更多元的商业模式，包括线上订阅和院线票房等更多商业可能性。</p>


---


## 167. 科氪 | 性能极限与跨界尝试：红魔11S Pro系列深度体验

- **Source**: [36kr](https://36kr.com/p/3814570248412677?f=rss)

- **Summary**: <h2>在智能手机行业普遍面临镜头模组日益凸出、机身内部堆叠空间受限的背景下，电竞旗舰由于其对散热和功耗的极端要求，往往表现出更为激进的工业设计。作为新一代的性能导向型产品，红魔11S Pro系列通过软硬件的垂直堆叠，试图在移动终端上探索更进一步的性能上限。以下我们将从设计、理论性能释放、以及实际软硬件体验三个维度，对其进行深度拆解。</h2>
  <p class="loading-entity">&amp;amp;nbsp;</p>
  <h3><strong>一、 外观设计：纯平后盖的内部堆叠与电竞美学</strong></h3>
  <p>从视觉和握持逻辑来看，红魔11S Pro最显著的特征在于其坚守的<strong>纯平后盖设计</strong>。在行业因大底传感器而集体妥协于镜头凸出的趋势下，这种“反向”设计在工业制造上面临着极高的空间挑战。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_2d59da8c2f6c4bd986edb15a25bd07e3@517825446_oswg8675859oswg4096oswg3072_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p><strong>内部空间重构</strong>：为了在不增加机身异常厚度的前提下抹平镜头凸起，红魔对内部架构进行了重新设计。在有限的Z轴高度内，开发团队不仅压榨空间塞入了新一代的脉动水冷模块、无线充电线圈，还容纳了大面积的VC散热板和高密度电池。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_6605c0c522c14afc9b9342fa046ad316@517825446_oswg8783320oswg4096oswg3072_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p><strong>透明电竞美学的视效迭代</strong>：机身背部延续了红魔标志性的透明设计语言。通过透明材质，内部的<strong>脉动水冷引擎</strong>实现了可视化。在水冷系统运行时，用户可以观测到液体流动的动态秩序。相比于纯粹的RGB灯光，这种工业风的设计提供了一种更具技术感的视觉回馈。</p>
  <p><strong>材质与细节处理</strong>：后壳采用了微蚀刻工艺打造的浮雕星轨纹理，搭配环形拉丝处理，使得整体质感较为收敛和冷峻。机身在肩键、腰部、LOGO及风扇处均设有支持自定义的RGB灯效，在暗光游戏环境下能提供必要的电竞氛围。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_81e2e6c7a1004f6f95be6b2cde1feaca@517825446_oswg8638957oswg4096oswg3072_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <h3><strong>二、 性能与散热：高标准筛选的“特种兵”芯与风水双冷架构</strong></h3>
  <p>性能表现是电竞手机立足的核心。红魔11S Pro首发搭载了<strong>第五代骁龙8至尊领先版</strong>移动平台。为了在重负载下维持超频表现，红魔在芯片筛选和散热架构上采用了更严苛的标准。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_3b30d2b701b64d21aeaba45752869a0b@517825446_oswg431878oswg2304oswg3072_img_jpg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p><strong>芯片体质的物理筛选</strong>：为了满足电竞长时高频的需求，红魔所采用的这颗“领先版”芯片，主要筛选自晶圆中心区域。由于物理刻蚀规律，该区域的芯片通常具备更稳定的温度控制和更高的电气性能。在此基础上，通过最高4.74GHz主频的冲刺分级测试，以及高温高压下的自适应电压调节（AVS）检测，筛选出具备自适应能力的芯片，以确保在极端重负载下不易因发热而触发激进的降频保护。</p>
  <p><strong>风水双冷复合散热系统</strong>：针对第五代骁龙8至尊领先版的发热特性，红魔在散热上引入了原本常见于服务器端的复合方案。手机将【驭风4.0】贯穿式主动散热风扇<strong>与</strong>脉动水冷引擎<strong>相结合，辅以复合液态金属3.0和4D冰阶VC。风扇与整机均通过了</strong>IPX8级防水认证，在提升主动散热效率的同时，规避了由于进水导致元器件损坏的风险。在散热系统运转时，后盖的蓝色轨道圈内，蓝白相间的液冷介质会随之一起转动。仪式感拉满！</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_78b07dd63a31408eb175d301d350f91d@517825446_oswg8006886oswg5888oswg4416_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p><strong>独立显存与能效调度</strong>：在架构协作上，红魔自研的<strong>红芯R4电竞芯片</strong>与高通联合打造了独立的高速显存。在图形高渲染场景下，此设计可减少高频访问系统内存的次数，从而降低总功耗。结合<strong>CUBE擎天游戏引擎3.0</strong>的AI感知调校，系统能够精细化调配算力，平衡了高帧率表现与续航消耗。</p>
  <h3><strong>三、 使用体验：悟空屏2.0、Steam直连与续航评估</strong></h3>
  <p>在日常交互和实际游戏运行中，硬件的堆叠最终转化为了多场景的体验。</p>
  <p><strong>悟空屏2.0的视觉完整性</strong>：正面配备的<strong>悟空屏2.0</strong>基于京东方X10全新屏下发光材料，实现了全无挖孔的视觉体验。屏幕黑边控制在<strong>1.25mm</strong>，屏占比达到<strong>95.3%</strong>，支持144Hz刷新率。由于没有刘海或挖孔遮挡，在全局视野和视频播放时拥有更纯粹的画面呈现。同时，屏幕集成了全屏3D超声波指纹解锁，提升了暗光或湿手状态下的解锁盲操率。</p>
  <p>&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_dd45d311f7bf4d3f9d9e83731b1ca61c@517825446_oswg6790088oswg4096oswg3072_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p><strong>行业首发Steam直连：性能的跨界探索</strong>：这是该机型在软件生态上的重要尝试。依托转译引擎，红魔攻克了X86与ARM架构之间的转译难题。用户拨动竞技键进入游戏空间后，可直接扫码登录个人的Steam账号。系统不仅支持游戏库内兼容作品的下载游玩，还打通了云端存档。用户在PC端的进度可以在手机侧的PC模拟器上无缝同步，迈出了打破移动端与桌面端算力壁垒的一步。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_752a133e39ad4631b5d985aab6a7cad3@517825446_oswg150064oswg579oswg262_img_png?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p>&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_5a10112f47664d919f126bcdaf91b64c@517825446_oswg143997oswg591oswg268_img_png?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p>&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_bc6e63d06aa94a8a8bce2f7e50911a30@517825446_oswg132905oswg613oswg277_img_png?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p>&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_070fd08b0673472bac3d365ddd73d419@517825446_oswg171350oswg613oswg277_img_png?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p><strong>操控精准度与手汗免疫</strong>：针对瞬时爆发的操控需求，该机引入了全新的<strong>新思触控芯片</strong>，在MagicTouch4.0算法支持下，实现了<strong>3000Hz的瞬时触控采样率</strong>。该方案优化了湿手控制算法，一定程度上避免了玩家因手汗导致的断触或漂移现象。</p>
  <p><strong>续航与快充系统</strong>：为了支撑高功耗输出，红魔11S Pro在续航规格上给出了较高配置。PRO版本搭载了<strong>8000mAh</strong>的大容量电池，显著延长了重度游戏下的续航时长。而PRO+版本则在<strong>7500mAh</strong>电池的基础上，配备了<strong>120W有线快充</strong>与红魔首款<strong>80W无线闪充</strong>，在充电灵活性和回血速度上取得了较好的平衡。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_2b7608f99f2e4bbcb855752822456536@517825446_oswg4041889oswg4096oswg3072_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_2821cf217391470b8422fced911120bd@517825446_oswg4942443oswg5888oswg4416_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p><strong>日常AI功能落地</strong>：在非游戏场景下，红魔11S Pro作为主力机也搭载了丰富的日常工具。AI帮写、AI消除、AI超清文档等功能提升了商用和办公效率；影像系统则在保留Live Photo的同时，延续了红魔标志性的星空与车轨慢门拍摄功能，拓宽了产品的实用边界。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_9a070f9762bc4945af1a30694066e2ad@517825446_oswg12873915oswg5888oswg4416_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <h3><strong>结语</strong></h3>
  <p>红魔11S Pro系列是一部特色鲜明、目的纯粹的硬件设备。它通过风水双冷散热、高标准芯片筛选以及无孔全面屏，将移动端的游戏性能推向了新的极端，并通过Steam直连展现出了打破平台壁垒的野心。对于不愿向主流“大镜头凸起”妥协、且对高负载游戏及跨平台游玩有硬性需求的极客与核心玩家而言，这是一台工业特色鲜明、技术指标扎实的旗舰标杆。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_5e5049041d2c4e4ab20dc11f60b7eea6@517825446_oswg9238151oswg4096oswg3072_img_jpg?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">产品图片</p>
  <p>&nbsp;</p>


---


## 168. Agent、多模态、应用、算力一天看尽，峰会亮点在此｜5.20日，来现场一起AI

- **Source**: [36kr](https://36kr.com/p/3814408307711492?f=rss)

- **Summary**: <p>进入2026，AI愈发狂飙突进。围观体验之余，人人不免在心中自问：</p>
  <p>朋友圈刷屏的“龙虾”、Harness等AI新事物，跟我到底有什么关系？真的有必要跟吗？</p>
  <p>AI创业、AI融资如火如荼，属于我的机会又在哪里？</p>
  <p>别人已经在用AI做视频、写代码、跑项目，我是不是已经慢了一拍？</p>
  <p>……</p>
  <p>到最后，几乎所有问题都会汇成同一个问题：<strong>我，到底该如何用AI？</strong></p>
  <p>如果你对这些问题还很模糊，不妨来第四届中国AIGC产业峰会走一趟——一天时间，把这一年AI产业最值得关注的人、事、判断，一次性讲清楚。</p>
  <p>先提前剧透一波。</p>
  <p><strong>18位重磅嘉宾，1场Agent主题圆桌，1份年度榜单，1张全景图谱</strong>——所有内容都已敲定。&nbsp;</p>
  <p>阵容上，既有昆仑万维、智谱、商汤、百度、蚂蚁、MiniMax这样的行业头部，也有亚马逊云科技、硅谷Fusion Fund带来的全球视角；既有复旦邱锡鹏、港大黄超代表的学界与开源前沿，也有盛大EverMind、太初元碁、趣丸科技等活跃实战派玩家。</p>
  <p>议程上，从Agent商业化落地、多模态与空间智能的最新突破，到AI在文娱、医疗、企业服务等场景的纵深渗透，再到算力与AI Infra的范式之变……这一年最值得关注的AI话题，几乎都装进了这一天。</p>
  <p>话不多说，下面直接上重点。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_d3f7e6d336404c6db6eddce54966e3a1@6381723_oswg161420oswg1080oswg648_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <h2>亮点1：Agent到底怎么落地？不同视角玩家都有心得</h2>
  <p>如果说去年大家还对“Agent是不是未来”持观望态度，那么2026年，这个问题的答案已经不言而喻。</p>
  <p>“Agent不是未来，是现在”——这正是<strong>智谱高级副总裁吴玮杰</strong>带来的判断，他将分享智谱在Agent商业化落地上的最新实战。</p>
  <p>但Agent真正走入企业，并非一蹴而就。<strong>亚马逊云科技产品技术部技术总监王晓野</strong>将聚焦如何跨越Agent落地鸿沟，拆解从最强模型到企业级AI Agent之间那条最难走的路。</p>
  <p>而<strong>港大助理教授黄超</strong>则会从学术与开源前沿的视角，探讨AI Agent范式变革的挑战与机遇。他所带领的HKUDS GitHub开源平台累计获得超24万Star，位列全球Top50，话语权毋庸置疑。</p>
  <p>与此同时，Agent要真正成为“数字生产力系统”，还需要更底层的能力支撑。<strong>盛大集团副总裁、EverMind CEO邓亚峰</strong>将分享长期记忆驱动的自进化，探讨AI如何从一个“工具”演化成可持续成长的数字生产力系统。</p>
  <p>当然，光有演讲还不够。本届峰会专门设置了一场<strong>Agent主题圆桌：2026，Agent产品的不确定性与非共识机遇。&nbsp;</strong></p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_b2381415360a404b95dbe8f678832be1@6381723_oswg223911oswg1080oswg2043_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p>出席嘉宾包括<strong>趣丸科技副总裁兼首席战略官、《屠龙之术》主理人庄明浩，ColaOS&amp;MarsWave CEO冯雷</strong>，以及<strong>EvoMap创始人张昊阳</strong>。</p>
  <p>这三位都是Agent产品一线的深度玩家，从产品形态到操作系统，从多智能体框架到自进化引擎，他们会碰撞出什么样的非共识观点？非常值得期待。</p>
  <h2>亮点2：Agent之外，模型能力边界也在继续扩张</h2>
  <p>虽然Agent是今年峰会的绝对主角之一，但不可忽视的是，支撑Agent的模型能力本身，也在以惊人的速度向外延伸——从“数字”到“物理”，AI对世界的认知边界正在被重新定义。</p>
  <p><strong>商汤科技执行副总裁、首席科学家林达华</strong>将分享多模态模型如何从“看懂”和“生成”，进化到真正可感知、可生成、可行动的空间智能新阶段。</p>
  <p>上午的GenAI Talk环节，<strong>蚂蚁灵波科技首席科学家沈宇军</strong>将围绕一个核心命题展开对谈：<strong>AI 2.0下半场，从AIGC到AIGA。</strong>当生成式AI从“内容”走向“行动”，整个产业逻辑将被改写。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_3aae9c2e9ba144b298d051607c7ea934@6381723_oswg207669oswg1080oswg2096_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p>而<strong>京东JoyInside业务负责人戴文军</strong>则会把这个命题进一步推往物理世界，当AI从屏幕里走出来，走进真实终端、真实场景，“AI World”才真正开始。</p>
  <p>模型层面，<strong>复旦大学特聘教授、模思智能创始人邱锡鹏</strong>将分享MOSS多模态模型及其推理优化的最新进展。这位主持研发了MOSS系列开源大模型的“大模型一线人物”，将带来学术与工程结合的硬核内容。</p>
  <h2>亮点3：具体怎么玩？这些应用玩家甩出成功案例</h2>
  <p>模型也好、Agent也罢，具体到不同领域，机会到底在哪？</p>
  <p><strong>昆仑万维董事长兼CEO方汉</strong>率先给出他的答案。他这些年带着昆仑万维在AI音乐、AI社交、AI短剧等多个AIGC方向同时下注，其分享会从一线视角，讲讲AIGC具体应用这一年究竟跑通了什么、又踩过哪些坑。</p>
  <p>紧接着，来自不同赛道的“实战派”玩家也将依次登场：</p>
  <p>文娱创作领域，<strong>风行在线CEO易正朝</strong>将带来一个核心判断——从AI编程到AI视频，众创才是AI生产力的核心杠杆。他会讲述AI如何从单点工具，进化为撬动整个创作者生态的杠杆，从而让普通人也能撑起一支创作团队。&nbsp;</p>
  <p>生产力工具层面，<strong>百度秒哒产品总经理朱广翔</strong>会分享他们“人人都是创造者”的产品理念，当门槛被AI抹平，想象力就是新的生产力。</p>
  <p>企业级AI方向，<strong>MiniMax ToB中国区商业化负责人胡维琦</strong>将带来MiniMax这一年在ToB战场上的真实打法与思考。</p>
  <p>大健康赛道，<strong>轻松健康集团执行副总裁马孝武</strong>将拆解从循证智能体到AI驱动的健康服务增长飞轮，展示AI在严肃医疗场景里的真实增长引擎。</p>
  <p>文娱、办公、企业、医疗……AI不再是“被讨论的对象”，而是“正在被使用的工具”。每一个细分赛道里，都已经有人开始把案例端上桌了。</p>
  <h2>亮点4：从训练到推理，算力的故事也在被改写</h2>
  <p>模型与应用之外，2026年最值得关注的另一条主线，是AI基础设施的范式重构。</p>
  <p>过去几年，所有人讨论算力都默认一个前提——为训练服务。但2026年，风向变了，推理需求暴涨、训练成本高企，整个算力叙事正在从“训练驱动”转向“推理驱动”。&nbsp;</p>
  <p><strong>Fusion Fund创始合伙人张璐</strong>将从全球资本与产业的双重视角，解读算力叙事的重构。当AI基础设施从训练转向推理，一场范式变革正在发生。</p>
  <p>而国产算力这一边，<strong>太初元碁首席产品官、高级副总裁洪源</strong>将带来他对国产算力路径的思考。当“Token”正在成为AI时代的新计量单位，国产算力如何筑基Token智能新未来？他会给出自己的答案。</p>
  <h2>亮点5：看尽AI全景生态，一份榜单+一份报告</h2>
  <p>延续往届传统，本届峰会，技术先锋、产业龙头、新锐势力将再次全景式碰撞。</p>
  <p>为了给行业更多参考，我们还将颁出<strong>2026年值得关注的AIGC企业、2026年值得关注的AIGC产品</strong>两类奖项，以及一份中国AIGC应用全景图谱。</p>
  <p>前者是量子位根据过去一年AIGC企业、产品的表现与反馈，并结合对2026年技术与场景的观察，评选出的高潜力企业和产品。</p>
  <p>后者是量子位智库绘制的一幅全面立体的<strong>中国AIGC应用全景图谱</strong>，用以展示国内AIGC应用的市场格局与发展动态，并深入剖析最具潜力与竞争力的产品和赛道。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_486836baefe84e408be892293768c6ec@6381723_oswg492452oswg1080oswg761_img_png?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <h3>5月20日举办</h3>
  <p>最后，<strong>时间地点以及最全议程</strong>在此，现场还有参会伴手礼等你来领，咱们到时候见 ~&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_04dd0dd35b854725b144052fe6c2f635@6381723_oswg1481547oswg1080oswg12004_img_jpeg?x-oss-process=image/quality,q_90/format,jpg/interlace,1" /></p>
  <p><strong>时间：</strong>5月20日 9:30</p>
  <p><strong>地点：</strong>北京·金茂万丽酒店</p>
  <p>现在，中国AIGC产业峰会正在火热报名中，欢迎点击链接报名<strong>线下参会</strong>： <a href="https://hdxu.cn/1Hjr1" rel="noopener noreferrer" target="_blank">https://hdxu.cn/1Hjr1</a></p>
  <p>本次峰会也将同步<strong>线上直播</strong>，欢迎预约参与：量子位视频号。&nbsp;</p>
  <h3>参会嘉宾简介一览&nbsp;</h3>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_03552a947df046c3acb7c7ae5843463e@6381723_oswg215422oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>方汉</strong></p>
  <p><strong>昆仑万维董事长兼CEO</strong></p>
  <p>方汉毕业于中国科学技术大学近代物理系，曾任职于中国科学院高能物理研究所、拓林思、亚信以及千橡互动。于2008年协助周亚辉先生创立昆仑万维。方汉拥有30年互联网从业经验，从1994年开始参与和倡导开源运动，是中文Linux奠基人、中文Linux四剑客之一，著作国内第一本Linux书籍《Linux实用大全》，他也是国内最早的网络安全专家，曾负责三大电信运营商的全网安全审计，领导开发了国内第一款P2P下载软件DUDU加速器，负责研发了国内市场占有率最高的网页游戏《三国风云》，为中国互联网最资深的参与者。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_3011c15f953642039d0355133d715733@6381723_oswg212092oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>吴玮杰</strong></p>
  <p><strong>智谱高级副总裁</strong></p>
  <p>吴玮杰目前担任智谱公司高级副总裁，负责公司MaaS平台商业化，并兼任泛互联网事业部总经理及浙江子公司总经理。他在人工智能、互联网和信息技术领域有着丰富的商业化管理经验和项目落地经验，曾任字节跳动企业应用全球首席商业官（旗下品牌包括飞书、LarkPeople和幕布等）、GE数字集团大中华区副总裁、复星集团联席首席发展官&amp;首席投资官。除此以外，他也曾在思科、SAP、Oracle等公司从事商业化管理工作。</p>
  <p>吴玮杰博士毕业于电子科技大学，同时持有香港大学国际工商管理硕士学位以及复旦大学软件工程学士、硕士学位。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_e20ad9f8f2ae42fb9db6b2cefc7ad795@6381723_oswg217040oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>易正朝</strong></p>
  <p><strong>风行在线CEO</strong></p>
  <p>易正朝，风行在线CEO，作为业务领头人，引领公司从传统互联网视听平台全面转型升级为AI文娱生态平台。推动“AI赋能众创”战略落地，带领团队打造橙星梦工厂、小剪刀等AI创作工具，影视网文智能小程序平台、电视鸿蒙平台等核心智能产品，构建从内容创作、智能分发到商业变现的全流通链生态。推动公司荣获AI赛道奖项、抖音快手等平台的头部服务平台奖项，在AI文娱新时代，推动内容生产效率革新与创作者生态繁荣，致力于让内容流动更简单。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_c2740c30d675420faf48d796077d9ed7@6381723_oswg212207oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p>&nbsp;<strong>林达华</strong></p>
  <p><strong>商汤科技执行副总裁、首席科学家</strong></p>
  <p>林达华教授现任香港中文大学信息工程系副教授、交叉学科人工智能研究所所长，并为商汤科技联合创始人、执行董事兼首席科学家，兼任上海人工智能实验室领军科学家。他于2012年获麻省理工学院计算机科学博士学位，研究方向涵盖计算机视觉、深度学习、大模型与生成式人工智能，在人工智能顶级会议和期刊发表论文逾300篇，引用逾90,000次，h-index达131。林教授曾获2010年NeurIPS最佳学生论文奖，带领团队在多项国际计算机视觉竞赛中获奖，连续五年入选Elsevier全球前2%顶尖科学家。</p>
  <p>他主导发起OpenMMLab，并推动书生大模型、OpenCompass评测平台及DeepLink开放计算体系建设，其中DeepLink于2024年获世界人工智能大会“卓越人工智能引领奖”。2026年，他荣获“中银香港科技创新奖”，以表彰其在计算机视觉与多模态智能领域的系统性创新。他长期服务学术共同体，曾任IJCV编委，多次在人工智能主要国际会议担任领域主席，并担任IEEE大规模深度学习模型评测标准工作组主席。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_5b7f21f27c1946a2b74e9944d07fe745@6381723_oswg219106oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>邓亚峰</strong></p>
  <p><strong>盛大集团副总裁、EverMind CEO</strong></p>
  <p>邓亚峰，毕业于清华大学，正高级工程师，拥有二十余年人工智能算法及产品研发经验。现任盛大集团副总裁、EverMind CEO。曾任360集团副总裁、人工智能研究院院长兼搜索事业部总经理，科创板首家AI上市公司格灵深瞳CTO。</p>
  <p>曾荣获2021年中国人工智能年度十大风云人物，教育部技术发明奖二等奖。长期致力于大语言模型、计算机视觉及AI for Science等领域的研究与应用，带领团队多次在国际国内主流AI评测中获得佳绩；累计申请发明专利160余项（已授权98项），发表论文50余篇（含10篇Nature子刊）。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_f2ebecd6c4bf4c03a1e56d7a8925a7b8@6381723_oswg253096oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>王晓野</strong></p>
  <p><strong>亚马逊云科技产品技术部技术总监</strong></p>
  <p>王晓野现任亚马逊云科技产品部技术总监。长期专注于企业现代化应用架构，数据及人工智能能力的建设。负责带领技术专家团队提供云上产品及开源方案技术实践指导，并致力于亚马逊云科技全栈服务在中国市场的应用和推广。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_1fc3877b21ac4c549ee85f85718b69fd@6381723_oswg206520oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>沈宇军</strong></p>
  <p><strong>蚂蚁灵波科技首席科学家</strong></p>
  <p>沈宇军，现任上海蚂蚁灵波科技有限公司首席科学家，同时领导蚂蚁技术研究院交互智能实验室。博士毕业于香港中文大学，研究方向为计算机视觉、生成模型、空间智能和具身智能。在CVPR、TPAMI、ICCV、ECCV、NeurIPS等国际顶级会议和期刊上发表论文百余篇，Google Scholar引用量逾万次。</p>
  <p>2024年起担任蚂蚁灵波科技首席科学家，致力于探索计算机视觉在机器人行业的落地之路，带领团队构建从空间感知到智能决策、从基座能力到世界建模的完整技术矩阵，推动具身智能从实验室走向规模化应用。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_fe240b8653204fff80e76d2354b14514@6381723_oswg222745oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>邱锡鹏</strong></p>
  <p><strong>复旦大学特聘教授、上海创智学院院长助理、模思智能创始人</strong></p>
  <p>邱锡鹏，CAAI Fellow，国家杰青获得者，主要研究方向为大模型、智能体以及科学工程等领域中的应用，发表学术论文被引用4万余次，5次获得AI领域高水平会议的最佳/杰出等论文奖，担任中国人工智能学会自然语言理解专委会副主任、中国中文信息学会大模型与生成专委会副主任、上海市计算机学会自然语言处理专委会主任等，主持研发了MOSS等系列高影响力开源大模型。</p>
  <p>连续多年入选中国高被引学者、全球前2%顶尖科学家榜单，获得2022年度钱伟长中文信息处理科学技术奖一等奖（第一完成人）、2022-2023年度教育部“高校计算机专业优秀教师奖励计划”，2024年度CCF-ACM青年科技奖（每年仅1人）、2025年度吴文俊人工智能科学技术奖自然科学一等奖（第一完成人）。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_d5abe7e029b84c13a17b72f0e4a1723d@6381723_oswg230102oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>胡维琦</strong></p>
  <p><strong>MiniMax ToB 中国区商业化负责人</strong></p>
  <p>胡维琦，2026年3月加入MiniMax，负责中国区商业化团队。2005-2026年期间，胡维琦曾历任华为云中国区副总裁、华为云新加坡总经理等职务，在国内、海外市场有丰富的2B工作经验。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_bdd4421972c74a2985c06883390dd5d5@6381723_oswg225492oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>朱广翔</strong></p>
  <p><strong>百度秒哒产品总经理</strong></p>
  <p>朱广翔博士毕业自清华大学交叉信息研究院，曾获中国智能体与多智能体系统最佳论文、北京市优秀博士学位论文、清华优秀博士学位论文等，在NeurIPS、ICLR、ICML、AAAI、NAR、Nature Communications等国际顶会和期刊发表论文14篇。</p>
  <p>2021年朱广翔加入百度，曾负责百度信息流双列首页产品、百度智能云数据中台、百度智能云知识管理产品及办公产品、百度智能云千帆Appbuilder等业务，目前任秒哒产品总经理。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_f1cb9059b605457fb31a6c79454c29c5@6381723_oswg208401oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>洪源</strong></p>
  <p><strong>太初元碁首席产品官、高级副总裁</strong></p>
  <p>洪源，太初元碁首席产品官、高级副总裁，发改委人工智能智库专家，中国自动化学会自主指令集专委委员，算力网络专委会算力副秘书长，中国国际工程咨询CIECC管理顾问。</p>
  <p>拥有15年AI行业管理经验，在语音、视觉、NLP等领域拥有丰富的软硬件全栈产品规划、建设及最终行业落地的成功案例。曾参与多个行业标准与白皮书撰写，包括《多元融合智能算力技术白皮书(2024年）》，《人工智能芯片云侧推理用深度学习芯片测试指标与测试方法》2022-0589T-SJ行业标准等。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_4f953466510e435dac9c5f23cf01b189@6381723_oswg210340oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>黄超</strong></p>
  <p><strong>香港大学助理教授、博士生导师</strong></p>
  <p>黄超现任香港大学助理教授、博士生导师。他的研究方向涵盖大型AI智能体、语言模型及图机器学习，其研究成果在Google Scholar上被引用超过17,000次。团队已推出多个影响力开源项目，包括nanobot、LightRAG、CLI-Anything等。作为团队负责人打造的HKUDS GitHub开源平台累计获得超过240,000 GitHub Stars，位列全球Top50，并超过100次登上GitHub Trending榜单。</p>
  <p>因其在人工智能开源领域的贡献，黄超荣获世界人工智能大会（WAIC）2024云帆奖「璀璨明星」、国际基础科学大会（ICBS）2024「前沿科学奖」，并入选「2025 AI100青年先锋」、「2025 AI2000全球最具影响力学者」。其研究成果多次入选KDD、WWW、SIGIR、AAAI等国际顶级会议的最具影响力论文之一，并多次获得顶会最佳论文提名奖。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_812aaf9fdb4f4ca6a0d93af602346a52@6381723_oswg217375oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>戴文军</strong></p>
  <p><strong>京东JoyInside业务负责人</strong></p>
  <p>戴文军，京东科技AI创新业务JoyInside负责人，主导附身智能技术体系的研发与商业化落地，通过整合多模态情感计算与大语言模型技术，为智能终端设备构建具备共情能力的交互系统。拥有18年云计算架构设计与AI工程化经验。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_71419d2bcfe8415aaa15c49289926bad@6381723_oswg224097oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>马孝武</strong></p>
  <p><strong>轻松健康集团执行副总裁</strong></p>
  <p>马孝武，轻松健康集团执行副总裁，2025胡润U40中国创业先锋，曾连续获得中国十大品牌人物、品牌强国创新榜样人物、中国品牌年度人物，以及创意媒体中国广告大奖在内的多项殊荣。在大健康和保险领域具有丰富的战略、增长、品牌、公关相关经验。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_bb02e5e980fe4ba998d3e6400c55c329@6381723_oswg237079oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>张璐</strong></p>
  <p><strong>Fusion Fund创始合伙人</strong></p>
  <p>张璐是Fusion Fund创始合伙人，硅谷知名投资人，连续成功创业者，斯坦福大学客座讲师。2015年创立Fusion Fund，现管理超过5亿美元资本，专注医疗、企业级AI基础设施和深科技领域投资。自2015年，张璐建立了一个卓越的风投生态系统，在行业内享有盛誉。</p>
  <p>张璐是世界经济论坛（达沃斯）“全球青年领袖”，曾入选硅谷商业周刊“硅谷影响力女性”、福布斯30under30投资领域主题人物等，2023年入选财富影响力商界女性、Business Insider美国最佳早期投资人等。2022年张璐被福布斯评选为全球华人精英Top100行业翘楚。同时，张璐担任多家投资组合公司的董事，未来科学大奖未来论坛青年理事，CommonSpirit Health Foundation董事，卡地亚女性创业家奖评审董事等。张璐毕业于斯坦福大学材料科学与工程学院。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_0747b706d9574768bd65c39d1e2dd841@6381723_oswg212492oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>庄明浩</strong></p>
  <p><strong>趣丸科技副总裁兼首席战略官、《屠龙之术》主理人</strong></p>
  <p>庄明浩，趣丸科技副总裁兼首席战略官，在人工智能、互联网和投资领域有着丰富的从业经验。《屠龙之术》主理人，知乎风险投资、互联网优秀回答者。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_cae2267b39614b99bce2d93ed7a61e63@6381723_oswg207150oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>冯雷</strong></p>
  <p><strong>MarsWave CEO</strong></p>
  <p>冯雷（Orange），MarsWave CEO，MarsWave先后推出了AI播客Listenhub、Agent操作系统ColaOS等热门AI产品。冯雷曾任MiniMax海螺AI产品负责人，在此之前，曾任职于BOSS直��、兰亭集势及三星电子，拥有超过10年产品经验。同时，他也是AI自媒体「AGENT橘/Orange AI」创作者。&nbsp;</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260518/v2_19b8e827eb034484a25d394702fabbd8@6381723_oswg223220oswg1080oswg2041_img_jpeg?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p><strong>张昊阳</strong></p>
  <p><strong>EvoMap创始人</strong></p>
  <p>张昊阳（17），EvoMap创始人，多智能体框架GameGPT、自进化引擎Evolver作者，OpenClaw社区头部开源贡献者。曾任和平精英技术策划、AIGC研发负责人，早年有虚拟数字人及VR领域的多次连续创业经历，11岁自学编程，14岁时成为中国最小的Unity开发者。拥有超过10年产品设计与技术架构经验。</p>

- **Tags**: `agent` `google` `gpt` `minimax` `rag`


---


## 169. 「宇石空间」完成5亿元A轮融资，今年计划交付三枚火箭，累计融资额已达10亿元｜36氪首发

- **Source**: [36kr](https://36kr.com/p/3814368445259270?f=rss)

- **Summary**: <p>文&nbsp;|&nbsp;阿至</p>
  <p>36<strong>氪获悉，宇石空间已完成5亿元A轮融资，由高榕创投、昆仑资本联合领投</strong>，建发新兴、蓝湖资本、弘晖基金、东证资本、臻泰资本、庚辛资本跟投；产业方股东紫金矿业、知名互联网战投、智能终端产业方联合投资，老股东高瓴创投、基石资本、千乘资本、知盛睿盈连续多轮追投。</p>
  <p>本轮资金将主要用于火箭总装测试、筷子回收技术验证、火箭产能建设和团队建设，为宇石空间AS-1火箭首飞及后续规模化运营提供保障。</p>
  <p><a href="https://36kr.com/p/3736614731694082" rel="noopener noreferrer" target="_blank">宇石空间</a>是我们长期关注的企业，专注于大运力、低成本、快速复用液体火箭的研制。<strong>在过去一年，公司已连续完成4轮融资，加上近期交割完的A轮，其累计融资额已达10亿元。</strong></p>
  <p>火箭制造及发射服务作为商业航天产业链条中的核心环节，向来是资本押注的重点，而可复用火箭作为这一环节中竞争最激烈的方向，能够极大降低单次发射成本、提高发射密度——这不仅是实现我国大规模卫星组网目标的必然途径，也是未来太空算力、太空光伏、太空旅游等商业化应用场景具备经济可行性的重要前提。</p>
  <p>整体来看，国内可回收复用火箭正处于从试验验证向工程应用跨越的关键突破期，虽然尚未实现常态化回收复用，但技术路线正在收敛。2026年以来，第一梯队企业新型火箭密集首飞并冲刺回收验证，初创企业没有路径依赖、创新性强且组织灵活度更高，有望通过系统性的低成本思路，重塑整个产业的成本结构。</p>
  <p>作为目前国内唯一采用<strong>“不锈钢箭体+液氧甲烷动力+筷子捕获臂回收”</strong>方案的商业火箭公司，宇石空间的首发70m级可复用不锈钢液体运载火箭AS-1已于今年1月正式交付。作为一款低成本两级中型液体火箭，AS-1起飞重量约570吨，箭体直径4.2米，一次性LEO轨道运载能力15.7吨，重复使用LEO轨道运载能力10吨，未来将主要针对中低轨有效载荷发射市场。</p>
  <p>为了实现火箭制造成本的进一步降低，宇石空间选择从材料体系底层进行革新，引入工业化生产体系，采用不锈钢方案。</p>
  <p>宇石空间创始人、CEO唐文提到，“不锈钢和铝合金相比，具备很多优势，大家经常担心的缺点是不锈钢重量较大，这一点我们需要通过结构的极致优化设计，以及更精密的焊接工艺来解决。<strong>在当前的产品研发过程中，我们已经实现了不锈钢箭体结构与铝合金火箭结构重量基本持平。</strong>”</p>
  <p>事实上，作为国内最早使用不锈钢箭体的团队，宇石空间从零开始自主培育了不锈钢箭体的供应链体系，目前团队已实现从材料级、组件级、整箱级到全箭级的不锈钢设计闭环。据悉，目前宇石空间自研的不锈钢箭体成本仅为铝合金箭体的十分之一，同时生产效率提升了数倍，最快出货时间只需一个月。</p>
  <p>底层的材料革新是第一步，想要让火箭从工艺品转变为工业产品，还需要规模化的产能支撑。唐文提到，<strong>目前宇石空间已经在湖南布局了年产能8发的生产基地</strong>，“未来我们还会进一步扩大产能，通过产能带来的规模效应，实现火箭成本持续下降。”</p>
  <p>在产能建设方面，我们了解到的最新进展是，宇石空间在此前“一中心两基地”的战略布局上再次进行了扩容。</p>
  <p>位于<strong>北京的研发中心面积扩展至超4000平方米</strong>，新投运的电气综合试验中心为火箭电气系统验证提供关键支撑；<strong>湖南火箭研制总装基地已部分投产</strong>，预计2026年第三季度正式交付，达产后具备年产8发火箭的能力；<strong>航电中心及捕获臂地面联合试验基地已经同步启动建设</strong>，接下来将进一步完善从设计、制造、试验验证到入轨交付、回收复用的全链条布局。</p>
  <p>今年，宇石空间计划生产三枚火箭，团队规模预计会扩大至350人左右（目前为200人左右），以保障明年上半年首飞任务的顺利推进，并为后续的规模化运营储备核心力量。</p>
  <p>“我认为，今天的中国在火箭运力这件事上，问题已经不再是能不能造，而是能不能便宜地造。我相信中国在商业航天领域的后发优势，基建能力对中国来说从来都不是问题。”在唐文看来，<strong>未来火箭会越做越大，火箭的工业化制造成本会越来越低，火箭周转速度会越来越快。</strong></p>
  <p>当以上要素充分配备、可复用火箭供给能力进一步提高，火箭运力就会成为基础设施，催生出更大的服务场景和服务规模。</p>
  <p>唐文认为，太空经济并不是用来解决目前存量市场已有的需求，它更多的是创造新的供给、创造新的需求。“当火箭成本跨过关键阈值之后，新的市场会被打开，这个打开的过程，不是线性的发展过程，而是阶跃式的跃升过程。”</p>
  <p>从发展节奏来看，现阶段国内市场的核心需求是大规模卫星星座的快速组网，这也将是商业火箭公司近3-5年最主要的服务目标和商业化来源。宇石空间希望在此期间将每公斤运力成本控制在低于2万元的水平，让火箭大规模服务于卫星星座组网，这是第一阶段。</p>
  <p>“当火箭运力成本降到5000元人民币每公斤左右时，就会进入太空设施的建设与运营阶段。”唐文认为，包括近期市场关注较多的太空光伏、太空算力等应用，都必须建立在火箭运力成本低于5000元人民币每公斤的基础之上；而长期来看，当火箭运力成本降到500元人民币每公斤以下时，才能真正服务于月球基地建设等任务。</p>
  <p>“这些场景对火箭运力的需求，以及太空经济的发展，至少是持续10年以上的长期赛道。站在这样的时代风口，这不是某一家公司的机会，而是属于整个时代的机遇。”唐文总结道。</p>
  <h3><strong>投资方观点</strong></h3>
  <p><strong>本轮领投方高榕创投项目负责人表示：作为卫星互联网、太空算力、6G等战略产业的核心底层基建，商业航天正迈向从研发验证到规模化商业落地的2.0时代，大运力、可复用火箭成为行业发展刚需。宇石空间是国内最早全面对标SpaceX的商业火箭公司，聚焦四米级直径中大型可复用液体火箭研发，团队始终锚定商业航天赛道的技术制高点。坚定技术终局路线的同时，宇石团队在唐文博士的带领下展现出势如破竹的战斗力，工程化落地进度亮眼。我们期待见证宇石在不远的未来缔造更多行业里程碑。</strong></p>
  <p><strong>本轮领投方昆仑资本表示：中国的商业航天产业已进入到新的发展阶段，市场对“低成本、高频次、可复用、大运力”的火箭提出了明确需求。同时，随着太空算力、太空制造、深空经济等新兴产业的快速崛起，大型可复用运载火箭将成为未来空间基础设施建设的重要能力。宇石空间从创立之初，就明确选择了"液氧甲烷 + 不锈钢箭体 + 筷子夹回收"这一产品定义和技术路线，并在人才吸引、工程配套等维度坚决投入，快速的实现研发里程碑，体现了团队战略取舍上的清醒判断和极强目标感。</strong></p>
  <p><strong>昆仑资本专注硬科技方向的投资，重视企业清晰的技术路线、可验证的工程能力，以及创业团队的使命感、目标感和持续的执行力。此次投资宇石空间，正是基于我们对中国商业航天长期发展前景的看好，以及对唐文博士带领下的团队的认可。昆仑资本愿与宇石空间同行，共同推动中国大型可复用运载火箭从追赶到引领。</strong></p>
  <p><strong>建发新兴投资团队表示：我们核心看好商业航天 2.0 时代的产业变革机遇与企业长期成长价值。当前行业已迈入规模化、低成本商业化新阶段，四米级直径的大运力可复用火箭成为产业发展刚需，科创板第五套上市标准明确了硬科技航天企业的上市准入规则，宇石空间主打中大型可复用液体火箭路线，完全契合监管标准与行业发展主流方向。团队始终秉持求真务实的做事风格，埋头深耕工程化研制，在同批次商业航天新生代企业中，整体工程化落地进度稳居行业前列，成长确定性极强。建发新兴期待宇石团队在唐文博士的带领下，保持惊人的成长速度和强大的执行力，坚定走终局路线，成为行业内第二家完成4米以上直径首飞的火箭企业。</strong></p>
  <p><strong>东证资本表示：东证资本坚定看好商业航空航天赛道，宇石空间直接选择“液氧甲烷+不锈钢”的终局方案，瞄准4米以上级别可复用、大运力的行业痛点，团队配置扎实、包容开放，在动力、回收、工程落地等多方面行业领先。商业航天已经进入了“应用落地”的淘汰赛阶段，宇石空间掌握不锈钢火箭的核心技术、拥有产业资本背书、未来商业模式清晰开放，我们相信在商业航天竞速的下半场，公司能实现从火箭验证到商业化发射的跨越，重塑商业航天的成本和效率标准，成为国内商业航天的头部力量。</strong></p>
  <p><strong>蓝湖资本表示：宇石空间是商业航天 2.0 时代的典型代表，从立项起就直接对标 “不锈钢 + 液氧甲烷 + 可回收” 的行业终局路线，彻底跳过 1.0 时代固体、小型液体火箭的历史包袱，无无效投入的沉没成本。团队无路径依赖，所有资源聚焦中大型可复用火箭研发，高效匹配市场刚需，具备显著后发优势。</strong></p>
  <p><strong>弘晖基金表示：弘晖基金始终以发掘科技恒久价值、布局硬核底层技术为投资底色，此次投资宇石空间，是弘晖在创新科技赛道又一个重要布局，我们将全力支持唐博士及团队加速实现火箭首飞与规模化运营，助力中国商业航天可复用运载技术实现突破。</strong></p>
  <p><strong>本轮多家产业方股东表示：火箭的产能是整个太空经济最大的卡点，火箭的成本直接影响到下游生态及应用的爆发。宇石空间锁定不锈钢箭体、液氧甲烷动力搭配可回收复用的终极技术路线，既精准契合行业长期演进方向，更充分彰显了核心团队对产业趋势的深刻研判与长远战略定力。伴随低轨卫星星座建设提速，叠加太空光伏、太空算力、太空采矿等未来产业的广阔市场，大运力、低成本、可回收运载火箭将成为市场刚性需求。凭借领先的技术架构与领跑行业的商业化推进节奏，宇石空间有望在行业新一轮格局洗牌中抢占先机，成长为商业航天赛道的中坚企业。</strong></p>


---


## 170. 对话万成云商：发文章≠GEO优化，大模型不是喂什么就推什么

- **Source**: [36kr](https://36kr.com/p/3814337101111044?f=rss)

- **Summary**: <p>“帮我搭配一套适合海边度假的衣服。”</p>
  <p>“帮我推荐一家适合约会的西餐厅。”</p>
  <p>“3000元预算，买哪款扫地机器人最划算？”</p>
  <p>这类与AI的问答正发生在全球数亿用户身上。过去，人们会把这些问题输入百度、谷歌等搜索引擎，因此产生了SEO（Search EngineOptimization，搜索引擎优化）营销。而当流量入口从搜索引擎转向AI工具，GEO（Generative EngineOptimization，生成引擎优化）也应运而生。</p>
  <p>区别于传统SEO追求的“搜索结果排名”，<strong>GEO的核心目标是让品牌信息在AI生成的回答中被优先引用和推荐</strong>。在AI全面渗透用户信息获取与消费决策场景的时代，对于出海企业而言，做好GEO意味着抢占新的流量入口。</p>
  <p>GEO的逻辑和SEO有什么根本不同？为什么有人说GEO是伪命题？出海企业布局GEO该怎么做？中小企业如何低成本起步……带着这些出海企业关心的问题，我们特别对话了万成云商品牌出海事业部总经理谭莉，拆解AI搜索时代如何让企业被AI看见、信任，并推荐给用户。</p>
  <p><strong>36氪：GEO被称为SEO在AI时代的进化。相比于SEO的核心在于搜索结果的排名，GEO优化的关键是什么？它与传统SEO的核心区别在哪里？</strong></p>
  <p><strong>谭莉：核心区别在于传统SEO偏“规则博弈”，GEO更像“信任竞争”。</strong>因为过去做SEO，我们的目标是把页面排到Google第一页，让用户点进去；但现在很多用户直接在AI里问问题，甚至不点链接了，那你要解决的是——怎么让AI在回答里“引用你”甚至“推荐你”。</p>
  <p>所以GEO的关键首先是，你是不是一个“可信任源”（全网有没有人认可你）；其次，你的内容能不能被AI理解、拆解、复用；最后是你的内容有没有完整的证据链，比如数据、案例或者第三方背书。</p>
  <p><strong>36氪：继GEO之后，也有人提出AEO概念，两者有什么区别？</strong></p>
  <p><strong>谭莉：</strong>这两个概念很多人会混着讲，但我个人是这么区分的：AEO更偏“问答结果优化”，核心是让你的内容直接成为某个问题的标准答案，比如FAQ、精选摘要这些。GEO更广，它面对的是生成式AI，不只是回答一个问题，而是参与“多源信息整合后的输出”。<strong>所以AEO更偏“结构技巧”，GEO更偏“整体品牌与内容生态”。</strong></p>
  <p><strong>36氪：GEO的概念近两年引起广泛讨论。为什么现在这个时间点企业需要关注GEO？在AI搜索渗透率持续提升的背景下，GEO应该在企业营销体系中占据怎样的战略位置？</strong></p>
  <p><strong>谭莉：</strong>分享几个很现实的变化：现在用户越来越习惯直接问AI，而不是自己筛选搜索结果；而且AI在很多行业决策前端，已经开始替代“信息收集阶段”；再就是有些客户还没打开你的官网之前，可能就在AI里形成了对你的判断。所以企业没办法去忽视GEO，现实摆在这里了。我认为，GEO在企业营销体系中占据着很关键的位置，<strong>它不会替代SEO，而是和SEO并行的“第二流量入口”，甚至未来会变成主入口之一。</strong></p>
  <p><strong>36氪：怎么理解有企业做过一些尝试后认为GEO是伪命题，或者靠自己持续给大模型喂语料也可以？</strong></p>
  <p><strong>谭莉：</strong>我觉得这是对AI工作机制有点误解，大模型不是你“喂什么它就推荐什么”。它有几个筛选逻辑：第一，信息是否一致（比如不同来源是否能得到印证）；第二，来源是否可信（是不是长期存在的内容资产）；第三，是否被多平台提及（而不是单一来源）。<strong>所以你自己“喂语料”，本质只是单点信息输入，很难形成“信任网络”。</strong></p>
  <p>不过我也理解为什么有人说GEO是伪命题，因为确实有很多“伪做法”，比如只做站内内容、只堆AI文章、不做外部验证，这些基本都很难起效果。</p>
  <p><strong>36氪：当企业布局海外GEO营销时，需要经历哪些关键步骤？不同行业、不同规模的企业在路径上会有哪些差异？</strong></p>
  <p><strong>谭莉：</strong>从实操角度，会有四个关键步骤：第一步先拆解你的客户是怎么筛选供应商的，这个路径是怎么样？第二步重建你的内容结构，包括官网、博客、FAQ、案例这些，全部按“可被AI理解”的方式重构。第三步是搭建外部信任体系，比如评价平台、媒体曝光、社媒讨论、行业引用，都很重要。第四步就是做多渠道分发，持续让内容在不同平台被看见和引用。</p>
  <p>不同企业可能在行业复杂度和品牌基础这两方面存在明显差异。比方说医疗、工业类比其它行业更需要专业背书，那有品牌的企业就更容易放大，没有品牌的就要先“补信任”。</p>
  <p><strong>36氪：在实施过程中，企业应如何在内容策略和技术基建层面做出改造甚至重塑，以同时满足AI理解与用户共鸣？</strong></p>
  <p><strong>谭莉：</strong>内容策略方面要做到结构清晰，信息有证据，有数据来源，表达要接近真人沟通。技术层面反而是基础的更容易被忽略：比如Schema结构化数据（Product、FAQ、Article等）、robots、index、hreflang这些基础配置，再一个就是页面可读性。<strong>总结来说，是做“可被理解的内容”。</strong></p>
  <p><strong>36氪：在布局GEO出海方案时，企业最容易忽视但至关重要的环节是什么？对于缺乏专业团队的中小企业，有哪些可行的解决方案或合作模式？</strong></p>
  <p><strong>谭莉：</strong>我们服务这么多跨境企业，发现最容易忽视的一点其实是：“让AI能访问你”。听起来很基础，但很多企业在实操中会陷入误区：比方说robots把AI爬虫挡了、页面noindex设置错误，或者多语言混乱……这些都会直接导致你做再多内容，AI也看不到。</p>
  <p>第二个容易忽视的是站外信任建设<strong>。很多人还停留在“发文章=做优化”，但GEO更看重：评论、测评、社媒讨论、媒体引用。</strong></p>
  <p>对于中小企业，我建议两种路径：①轻量级：聚焦一个细分领域做深内容+少量高质量外部背书；②合作型：找有资源的服务商做整合（内容+渠道+数据），不要自己盲目试错，成本会很高。</p>
  <p><strong>36氪：企业在选择GEO服务伙伴时，应该重点考察对方的哪些核心能力（如是否具备垂直行业知识库、跨平台渠道资源、效果监测与分析体系等），以避开“无效投入”的陷阱？</strong></p>
  <p><strong>谭莉：</strong>这个问题非常关键，因为现在确实有不少“概念型服务商”。我建议重点看四个能力：</p>
  <p>第一，行业理解能力，是不是懂你这个行业，而不是只会写内容。</p>
  <p>第二，内容生产质量。有没有真实案例、是否具备本地化能力，而不是纯AI批量生成。</p>
  <p>第三，渠道与分发能力。有没有海外平台资源，比如媒体、社区、测评渠道。</p>
  <p>第四，数据监测体系。比如做一段时间了，看看有没有被AI引用？哪些内容有效？ROI如何？</p>
  <p><strong>如果对方只能讲“发多少篇内容”，基本可以直接排除。</strong></p>
  <p><strong>36氪：2026年初Seedance2.0的爆火，让业界看到了AI视频生成从“抽卡式试错”向“工业化生产”跨越的可能性 。10秒带货视频成本仅需8元的“成本塌方”对于跨境电商的内容生产逻辑意味着什么？</strong></p>
  <p><strong>谭莉：</strong>这个变化其实挺颠覆的。过去做视频，成本高、周期长，所以大家拼的是“有没有内容”；但现在成本接近于零，意味着：内容不再是门槛，内容“是否有效”才是门槛。</p>
  <p><strong>36氪：当视频生产成本趋近于零，所有人都能批量生成高质量内容时，企业的竞争焦点会发生怎么样的变化？从GEO布局的角度看，企业应如何构建AI时代下的营销思维？</strong></p>
  <p><strong>谭莉：</strong>供给无限的时候，稀缺的就变了。我认为未来竞争会集中在三点：第一，认知占位，用户心里有没有你；第二，信任结构，有没有被多方验证；第三，数据能力，能不能快速迭代内容。</p>
  <p>从GEO角度，我觉得企业要建立一种新思维：要把品牌内容当资产去做长期积累，同时将口碑、评价这些信任一点点做起来，更重要的是<strong>发内容之前，问问自己：AI会不会用它？用户会不会信它？避免做“自嗨”的内容。</strong></p>
  <p><strong>36氪：Seedance2.0的火爆也引发关于深度伪造和版权的讨论。跨境电商卖家在利用这类工具生成营销素材时，应如何规避潜在的肖像权、版权风险？</strong></p>
  <p><strong>谭莉：</strong>这个问题确实不能忽视，我建议，尽量避免使用可识别人物（尤其是公众人物）做生成素材，素材来源尽量用可商用授权库，品牌、Logo、音乐等要确认授权范围，涉及医疗、功效类内容要特别谨慎，因为合规风险更高。毕竟，AI可以帮你降低成本，但不能帮你“免责”。</p>

- **Tags**: `generative` `google`


---


## 171. 创业板指跌逾2%

- **Source**: [36kr](https://36kr.com/newsflashes/3815573869518595?f=rss)

- **Summary**: 36氪获悉，指数走弱，创业板指下挫跌逾2%，沪指跌0.20%，深成指跌1.39%。半导体芯片、锂电、有色金属等方向跌幅居前，沪深京三市下跌个股近2500只。


---


## 172. 苹果公布年度全球开发者大会日程安排

- **Source**: [36kr](https://36kr.com/newsflashes/3815541151719168?f=rss)

- **Summary**: 36氪获悉，苹果公司官网公布年度全球开发者大会（WWDC）日程安排。大会定于北京时间6月9日至13日举行，届时将举行主题演讲和Platforms State of the Union，介绍Apple平台更新，包括人工智能的进展以及新软件和开发者工具。


---


## 173. 两市融资余额增加155.7亿元

- **Source**: [36kr](https://36kr.com/newsflashes/3815501354213128?f=rss)

- **Summary**: 36氪获悉，截至5月18日，上交所融资余额报14622.77亿元，较前一交易日增加99.58亿元；深交所融资余额报14005.61亿元，较前一交易日增加56.12亿元；两市合计28628.38亿元，较前一交易日增加155.7亿元。


---
