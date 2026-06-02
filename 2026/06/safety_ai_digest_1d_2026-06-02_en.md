# AI Daily Digest [AI 安全] - 2026-06-02



## 1. Organizational Adaptation to Generative AI in Cybersecurity

- **Source**: [arxiv_cr](https://arxiv.org/abs/2506.12060)

- **Summary**: arXiv:2506.12060v2 Announce Type: replace  Abstract: Cybersecurity organizations are adapting to GenAI integration through modified frameworks and hybrid operational processes, with success influenced by existing security maturity, regulatory requirements, and investments in human capital and infrastructure. This qualitative research employs systematic document analysis and comparative case study methodology to examine how 25 studies from 2022 to 2025 document organizational adaptation of threat modeling frameworks, revealing a shift away from traditional signature-based systems toward AI-capable frameworks across three primary patterns: LLM integration for security applications, GenAI frameworks for risk detection and response automation, and AI/ML integration for threat hunting and matching. Organizations with mature infrastructures, particularly in finance and critical infrastructure, demonstrate higher readiness through structured governance, dedicated AI teams, and robust incident response processes, with central banks and financial institutions leading adaptation efforts under regulatory pressure. Successful integration requires human oversight of automated systems, attention to data quality and explainability, and sector-specific governance, though ongoing difficulties with privacy protection, bias reduction, personnel training, and adversarial defense persist. Notable imbalances between offensive and defensive GenAI capabilities create strategic concerns for security planning. The findings offer actionable insights for cybersecurity professionals and underscore the need for adaptive approaches, ethical frameworks, and staff development when managing AI-enhanced threats.

- **Tags**: `adversarial` `bias` `explainability` `generative` `governance`


---


## 2. When AI Meets Wall Street: A Survey on Trustworthy AI in Fintech

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30650)

- **Summary**: arXiv:2605.30650v1 Announce Type: new  Abstract: Artificial intelligence is now embedded as a primary decision engine in continuously operated financial AI pipelines spanning training and updating, deployment and inference, and operation with monitoring and feedback. The automation and scale that make these pipelines effective also create novel attack surfaces, where small algorithmic perturbations can amplify into persistent, system-level financial harm. Existing surveys, however, either treat AI as a defensive tool or analyse adversarial machine learning in a domain-agnostic manner, abstracting away finance-specific constraints such as accounting plausibility, non-IID federated data, continuous retraining, and automation-amplified downstream effects. We address this gap with a unified, lifecycle-centric and mechanism-driven framework. We partition financial AI into three lifecycle stages: training and updating, deployment and inference, and operation, monitoring, and feedback. We further propose the Financial AI Security and Robustness Taxonomy, organising seventeen attack subtypes across data and model poisoning, adversarial attacks on decision boundaries, prompt injection in LLM-mediated workflows, and deepfake-driven subversion of KYC verification layers. For each subtype, we analyse algorithmic strategy, feasibility constraints, stealth and persistence, and downstream financial consequences. Finally, we identify open challenges and outline a research agenda toward lifecycle-aware stress testing and finance-relevant robustness benchmarks.

- **Tags**: `adversarial` `benchmark` `llm` `prompt injection` `research`


---


## 3. A Unified Framework for Gradient Aggregation in Multi-Objective Optimization

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30452)

- **Summary**: arXiv:2605.30452v1 Announce Type: new  Abstract: Many machine learning problems involve multiple inherent trade-offs that are best addressed by gradient-based multi-objective optimization (MOO) algorithms. Existing methods are often proposed with various motivations, analyzed case by case, and differ algorithmically in how the component gradients are aggregated at each step. In this work, we develop a unifying framework for gradient aggregation in MOO, establishing (optimal) rates of convergence to Pareto stationarity, the standard measure of performance in MOO. Central to our analysis is a sufficient alignment condition, from which we derive a theorem showing that non-conflicting directions, when chosen within the convex hull of gradients, form a fundamental sufficient condition for convergence. We further show that feasibility can be ensured through projection onto the dual cone, broadening the scope of methods that admit convergence guarantees. In parallel, we present a primal optimization perspective of gradient aggregation that encompasses established algorithms, clarifies their theoretical relationships, and enables the design of new variants. As an illustration, we introduce capped MGDA, derived from a CVaR-based formulation, and demonstrate its robustness in adversarial federated learning. Finally, we validate our theory through experiments on synthetic problems and practical benchmarks.

- **Tags**: `adversarial` `alignment` `benchmark` `federated learning` `robustness`


---


## 4. Differentially Private Preference Data Synthesis for Large Language Model Alignment

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30808)

- **Summary**: arXiv:2605.30808v1 Announce Type: new  Abstract: Preference alignment is a crucial post-training step for large language models (LLMs) to ensure their outputs align with human values. However, post-training on real human preference data raises privacy concerns, as these datasets often contain sensitive user prompts and human judgments. To address this, we propose DPPrefSyn, a novel algorithm for generating differentially private (DP) synthetic preference data to enable privacy-preserving preference alignment. DPPrefSyn is a principled framework grounded in the Bradley-Terry preference model and the intrinsic geometric structure of pairwise human preference data. It first learns an underlying preference model from private data with formal differential privacy guarantees, and then leverages the learned model together with public prompts to synthesize high-quality preference data. It exploits the shared linear structure of per-cluster reward models to effectively capture heterogeneous human preferences in private datasets, and leverages DP Principal Component Analysis (DP-PCA) to improve learning accuracy. Extensive experimental results demonstrate that DPPrefSyn achieves competitive alignment performance under strong DP guarantees. These findings highlight the potential of synthetic preference data as a practical alternative for privacy-preserving preference alignment across a broad range of applications. To the best of our knowledge, this is the first work to generate DP synthetic preference data for LLM alignment. Our code is available at https://github.com/gfengyu/Differentially-Private-Preference-Data-Synthesis.

- **Tags**: `alignment` `differential privacy` `large language model` `llm` `privacy`


---


## 5. From Prompt Injection to Persistent Control: Defending Agentic Harness Against Trojan Backdoors

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.31042)

- **Summary**: arXiv:2605.31042v1 Announce Type: new  Abstract: LLM agents are evolving from conversational chatbots to operational tools in real-world workspaces. In local agentic harnesses, an LLM can read and write files, call tools, and reuse workspace state across sessions. While such capabilities enhance utility, they also expose a new attack surface for attackers. Attackers can embed a prompt injection within a file or tool output. Agents may read this hidden instruction, store it, and execute it later. In this multi-step trojan attack paradigm, no individual step appears malicious on its own, but these steps can collectively turn untrusted text into persistent control content. However, existing defenses often inspect each step in isolation. As a result, they can block a clear harmful action, but fail to detect the earlier write operation that plants the backdoor. To reveal this threat, we introduce ClawTrojan, a benchmark designed to identify multi-step trojan attacks in local agentic harnesses. In an OpenClaw-style simulated workspace with GPT-5.4, ClawTrojan reaches a 95.5% attack success rate (ASR), while existing single-turn prompt-injection attacks produce near-zero ASR on the same model. To address this threat, we propose DASGuard, which scans control-like text in sensitive local files, traces its origin, and removes control content that does not originate from a trusted source. Our results show that DASGuard achieves strong dynamic defense by combining runtime attack blocking with sanitized commits to the workspace.

- **Tags**: `agent` `backdoor` `benchmark` `gpt` `llm`


---


## 6. $PC^2$: Politically Controversial Content Generation via Jailbreaking Attacks on GPT-based Text-to-Image Models

- **Source**: [arxiv_cr](https://arxiv.org/abs/2601.05150)

- **Summary**: arXiv:2601.05150v3 Announce Type: replace  Abstract: The rapid evolution of text-to-image (T2I) models has enabled high-fidelity visual synthesis on a global scale. However, these advancements have introduced significant security risks, particularly regarding the generation of harmful content. Politically harmful content, such as fabricated depictions of public figures, poses severe threats when weaponized for fake news or propaganda. Despite its criticality, the robustness of current T2I safety filters against such politically motivated adversarial prompting remains underexplored. In response, we propose $PC^2$, the first black-box political jailbreaking framework for T2I models. It exploits a novel vulnerability where safety filters evaluate political sensitivity based on linguistic context. $PC^2$ operates through: (1) Identity-Preserving Descriptive Mapping to obfuscate sensitive keywords into neutral descriptions, and (2) Geopolitically Distal Translation to map these descriptions into fragmented, low-sensitivity languages. This strategy prevents filters from constructing toxic relationships between political entities within prompts, effectively bypassing detection. We construct a benchmark of 240 politically sensitive prompts involving 36 public figures. Evaluation on commercial T2I models, specifically the GPT series, shows that while all original prompts are blocked, $PC^2$ achieves attack success rates (ASRs) of up to 86% and outperforms state-of-the-art frameworks by a large margin. We further propose a ready-to-deploy multi-layered filtering mitigation against $PC^2$-style attacks, reducing ASR to approximately 10%.

- **Tags**: `adversarial` `benchmark` `gpt` `jailbreak` `rag`


---


## 7. Generating Graph-like Rules for Knowledge Graph Reasoning via Diffusion Models

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30747)

- **Summary**: arXiv:2605.30747v1 Announce Type: new  Abstract: Logical rules constitute a cornerstone of knowledge graph (KG) reasoning, valued for their interpretability and ability to model relational patterns. However, existing rule mining methods predominantly focus on simple chain-like rules and therefore neglect the richer relational information encoded in graph-like structures, such as cycles and branches. This limitation is further exacerbated by computational bottlenecks caused by the combinatorial explosion of the search space, which is especially challenging for graph-like rules. Meanwhile, generative approaches such as diffusion models, despite their success in other domains, can not be directly applied to rule mining because their training objectives are not aligned with the goal of learning high-quality rules, and non-differentiable KG rule quality metrics cannot directly guide model optimization. To address these limitations, we propose GRiD, a framework that reformulates graph-like rule discovery as a discrete generative process conditioned on the target relation. GRiD employs a two-phase training strategy. First, supervised pre-training enables GRiD to capture structural priors from subgraphs sampled from the KG meta-graph. Subsequently, reinforcement learning is applied to fine-tune GRiD through policy gradient optimization guided directly by non-differentiable rule-quality metrics. Experiments on six benchmark datasets show that GRiD achieves competitive performance on KG completion tasks. Ablation studies confirm the efficiency and robustness of GRiD and further show that graph-like rules complement chain-like rules in KG completion. Our codes and datasets are available in https://github.com/Haoxiang-Cheng/GRiD

- **Tags**: `benchmark` `diffusion` `efficiency` `generative` `interpretability`


---


## 8. PReMISE: Policy Rubrics as Measurement Specifications for LLM Judges

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30803)

- **Summary**: arXiv:2605.30803v1 Announce Type: new  Abstract: LLM judges are increasingly used to evaluate open-ended responses, but their scores depend strongly on the rubrics that condition them. A vague rubric asking for a response to be ``helpful and factual'' can reward polished answers that invent facts or violate user intent. We treat reusable rubrics as measurement specifications: changing the rubric changes the response quality measurement induced by a fixed judge. We introduce PReMISE, a framework that, given pairwise human-preference data, (i) discovers a policy-level rubric set, and (ii) audits any rubric set under LLM-judge use along four axes: structural adequacy, reliability, preference fit, and adversarial robustness. Across rubric sources no raw source is simultaneously reliable, preference-predictive, and adversarially robust; and high inter-rater agreement does not imply low exploitability. PReMISE is the only rubric source to score non-trivially on applicability, specificity, and effective dimensionality simultaneously. We contribute two audit-targeted repair operations: preference-rank selection raises judge accuracy on paired responses from $65.0\%$ to $68.6\%$, competitive with the strongest rubric-discovery baselines and leading on two of three judges in our cross-judge sweep; reliability-constrained refinement reduces the rate at which exploit responses receive high scores from $46.4\%$ to $36.0\%$ with little change in inter-judge agreement ($\alpha{=}.531\to.519$).

- **Tags**: `adversarial` `llm` `policy` `robustness`


---


## 9. LLM-FACETS: A Privacy-Preserving Framework for Evaluating LLM Transparency and Accountability

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.31167)

- **Summary**: arXiv:2605.31167v1 Announce Type: new  Abstract: Assessing whether Large Language Models outputs are factually grounded, epistemically calibrated, and methodologically reproducible is a prerequisite for responsible AI deployment. Yet auditing LLMs remains inaccessible to non-technical practitioners: existing tools require programming expertise and non-trivial environment setup, and cloud-hosted platforms transmit evaluation data to external services, creating barriers for domain experts and compliance officers legally responsible for AI oversight. We introduce LLM-FACETS (LLM FActuality Cross-EvaluaTion System): an open-source framework with a browser-accessible interface and a plugin architecture, structured around three practitioner profiles (technical experts, domain experts, compliance officers) that mirror the stakeholder categories identified in the EU AI Act and the NIST AI Risk Management Framework. The architecture makes data flows explicit: deterministic metrics (BLEU, ROUGE, BERTScore) run entirely within the self-hosted server with no outbound transmission; LLM-judge metrics contact external APIs explicitly, with users retaining full credential control. The framework operationalizes transparency through three mechanisms: token-level log-probability visualization for epistemic uncertainty, multi-judge consensus to mitigate judge bias, and RAG Triad metrics (Faithfulness, Answer Relevance, Context Relevance) to detect and localize hallucinations. A plugin architecture allows any new metric or dataset to be integrated without modifying the evaluation pipeline. The open-source implementation enables cross-checking across multiple metrics targeting the same property, ensuring reproducibility and decoupling AI accountability from the teams building the systems assessed. We verify the framework through cross-validation of 18 metric implementations against canonical reference libraries.

- **Tags**: `bias` `large language model` `llm` `privacy` `rag`


---


## 10. Enhancing Regime Shift Detection Using Unstructured Data: A Study on the Treasury Market

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30363)

- **Summary**: arXiv:2605.30363v1 Announce Type: cross  Abstract: Regime shifts in financial markets reorganise the joint dynamics of asset prices and macro variables, breaking any single-regime calibration. They are nonetheless difficult to detect reliably because the data signal is noisy and heavily multicollinear, while the contemporaneous text that announces them is unstructured. Standard regime shift detection methods rely solely on structured time-series data and ignore policy communications, even though these texts often signal shifts before they materialise in observed prices. We propose a text-enhanced regime shift detection pipeline that combines large language model (LLM) reasoning over central-bank communications with statistical validation on multivariate financial time series. The framework is detector-agnostic: text-proposed candidates are validated using a bootstrap likelihood-ratio test on a vector autoregression (VAR), while data-driven candidates from arbitrary regime detectors are ratified through a lenient LLM text check. We evaluate the framework on 2010-2024 FOMC minutes paired with a 14-variable U.S. Treasury and macroeconomic panel, using four interchangeable data-driven detectors. The proposed pipeline achieves F1 = 0.82 against a verified anchor list of monetary-policy regime shifts, with same-day modal detection latency and consistently stronger performance than pure data-driven baselines. The results demonstrate that combining unstructured policy text with statistical structural-break detection improves the robustness and interpretability of regime shift identification in financial markets.

- **Tags**: `interpretability` `large language model` `llm` `policy` `reasoning`


---


## 11. When LLMs Learn to Be Consistently Wrong: A Multi-Model Study of Linear Representations of Synthetic Deception

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30381)

- **Summary**: arXiv:2605.30381v1 Announce Type: cross  Abstract: Deceptive alignment, in which models maintain accurate internal representations while deliberately producing false outputs, remains a central challenge in AI safety. While strategic deception is the primary long-term concern, synthetic dishonesty - induced via direct optimization on incorrect answers - provides a controlled testbed for studying the representational basis of learned deception. We introduce a multi-model paradigm in which honest and deceptive variants of five transformer models (Pythia-1.4B, Gemma-2-2B/9B, Qwen2.5-7B, Llama-3.1-8B) are fine-tuned using LoRA on the same question distribution. Linear probes trained on mean-pooled hidden states detect synthetic dishonesty with near-perfect AUC (greater than or equal to 0.99) as early as layers 1-3 in four architectures, while Pythia-1.4B reaches a peak of 0.705. Logistic regression probes consistently match or outperform MLP probes, supporting the Linear Representation Hypothesis. Probes trained on TruthfulQA generalize with near-zero loss (Delta AUC approx. 0) to held-out MMLU subjects. Late-layer representations show strong robustness to Gaussian noise, with Gemma-2 models exhibiting exceptional stability. Mechanistic analysis of Fisher Discriminant Ratio, effective rank, centroid geometry, directional stability, cross-domain alignment, and calibration (ECE) reveals two regimes: representational collapse in Pythia/Llama/Qwen versus high-dimensional preservation in Gemma-2. Across all models, the dishonesty direction consolidates progressively in deeper layers, with optimal calibration (ECE less than 0.01 except Pythia) achievable in layers 1-4. These results demonstrate that robust, domain-invariant dishonesty representations can be rapidly entrenched via modest supervised fine-tuning, with implications for activation-based monitoring.

- **Tags**: `ai safety` `alignment` `fine-tuning` `gemma` `llm`


---


## 12. DTG-Restore: Training-Free Diffusion Refinement for Generative Video Super-Resolution

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30431)

- **Summary**: arXiv:2605.30431v1 Announce Type: new  Abstract: Recent progress in video diffusion models has enabled remarkable generative fidelity, yet leveraging these priors for restoration remains limited by the strong coupling between conditional and unconditional branches in standard classifier-free guidance. We introduce a training-free framework that enhances distorted and low-resolution videos by decoupling these signals in time. Our proposed Decoupled Time Guidance (DTG) evaluates the unconditional branch at a cleaner diffusion timestep, providing a lookahead prior that preserves geometry while suppressing replication of warped content. This temporal bias is annealed throughout sampling, allowing the model to transition from structure correction to detail refinement without retraining. Combined with any off-the-shelf restoration module in a plug-and-play manner, our approach improves perceptual coherence and restores plausible structure in AIgenerated and real-world videos alike. To facilitate evaluation, we curate GenWarp480, a benchmark of 4,400 distorted 480p videos synthesized from diverse text-to-video models. GenWarp480 focuses on characteristic generative degradations such as warped faces, body misalignments, and spatial artifacts, providing a purpose-built testbed for assessing robustness to generative errors. Extensive experiments demonstrate that our method achieves significant improvements in structural fidelity and temporal stability without any model training.

- **Tags**: `alignment` `benchmark` `bias` `diffusion` `generative`


---


## 13. Escaping the Linearity Trap: Manifold Detours for Black-Box Adversarial Attacks on Singing Audio Deepfake Detection

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30366)

- **Summary**: arXiv:2605.30366v1 Announce Type: new  Abstract: Recent Singing Voice Synthesis (SVS) advances enable highly realistic but potentially malicious AI covers, making singing voice deepfake detection (SVDD) crucial. Self-Supervised Learning (SSL)-based detectors achieve state-of-the-art performance by fine-tuning speech SSL backbones to capture singing-specific spoof artifacts. Existing adversarial attacks often fail against SSL-SVDD, creating a false impression of inherent robustness. We reveal this stems from two challenges. First, at the objective level, attacks optimize cross-entropy on local surrogates, crossing surrogate-specific boundaries rather than suppressing shared spoof evidence. Second, at the method level, attacks follow the surrogate's dominant gradient direction. In SSL-SVDD, this aligns with fine-tuned artifact-sensitive directions, limiting transferability to unseen detectors - a geometric failure we term the Linearity Trap. To properly evaluate robustness, we propose MARS (Meta-Adversarial Regression of Semantics), a transfer-based black-box framework tailored to SSL-SVDD. Structurally, MARS shifts to hypothesis-evidence manipulation by constructing a natural semantic anchor from the pre-trained SSL space and an artifact anchor from the fine-tuned space. Algorithmically, MARS escapes the Linearity Trap via bi-level optimization: the inner stage induces tangential exploration, while the outer stage guides the audio toward the natural semantic manifold. Experiments on the CtrSVDD benchmark show MARS improves Attack Success Rate (ASR) in in-distribution transfer (13%), out-of-distribution transfer (10%), and cross-task evaluation (36%), highlighting the urgent need for robust SVDD systems.

- **Tags**: `adversarial` `benchmark` `fine-tuning` `robustness`


---


## 14. AdvScene: Rethinking Adversarial Patch Evaluation Through Scene Robustness

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30578)

- **Summary**: arXiv:2605.30578v1 Announce Type: new  Abstract: Adversarial patches are physical patterns attached to real objects to mislead AI vision systems. Their real-world risk is not determined by a single successful prediction, but by whether they remain effective after deployment under changing viewpoints, distances, and scene conditions. We refer to this property as scene robustness, the effectiveness of a deployed patch across conditions in a real environment. Yet existing evaluations do not measure scene robustness well: real image benchmarks are realistic but fixed, while simulators are controllable but not grounded in a specific real scene.   We present AdvScene, a scene-grounded framework for measuring the scene robustness of adversarial patches in reconstructed real environments. AdvScene reframes evaluation as operational measurement: given a fixed deployed patch, it characterizes the patch's operational envelope - where and when the attack succeeds - as a function of viewpoint, distance, and scene context. A key challenge is that the attack is typically defined only in a single anchor view, while evaluation requires a representation that remains faithful under viewpoint changes. We formalize this as a constrained lifting problem and introduce Adversarial Patch-to-Scene Embedding (APSE), which resolves cross-view ambiguity while preserving attack-critical appearance and enforcing locality, target-surface attachment, and cross-view consistency. We validate AdvScene using real-world physical data and conduct a comprehensive evaluation of existing adversarial patches. Our results show that AdvScene reveals substantial scene-dependent variation in attack effectiveness that is not captured by existing image-centric or simulator-based evaluations.

- **Tags**: `adversarial` `benchmark` `embedding` `robustness` `vision`


---


## 15. Automatically Attacking Software Reverse Engineering AI Agents

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30667)

- **Summary**: arXiv:2605.30667v1 Announce Type: new  Abstract: Software tools for reverse engineering executable binary files, such as Ghidra, enable malware analysts to safely conduct robust static analysis without having access to original source code. Coupled with the analytic power of large language models (LLM), agentic systems enabled with tools, such as GhidraMCP, can allow analysts to automate a previously human driven process. Although this automation can increase the productivity of a single malware analyst, it also introduces a new area of vulnerability for malware obfuscation. This paper presents an adversarial technique using genetic algorithm-based prompt generation, a modification of an adversarial attack known as AutoDAN, to demonstrate the ability to deceive LLM-powered disassembly and decompilation systems into misinterpreting binary executables, effectively corrupting their analytical output. This proof-of-concept methodology exploits inherent vulnerabilities in how LLMs process and interpret decompiled machine code via prompt injection by using extraneous string variable assignments to pass surreptitious instructions to the LLM while not impacting the functionality of the executable file. We demonstrate this capability through several concise examples. This approach could enable attackers to bypass automated detection systems that rely on LLM-driven analysis pipelines. By studying and understanding this attack, insights can be gained regarding the security implication of integrating LLMs into cybersecurity toolchains and building more robust agentic code analysis systems.

- **Tags**: `adversarial` `agent` `large language model` `llm` `productivity`


---


## 16. Investigating Detection and Obfuscation of Prompt Injection Attacks Against Software Reverse Engineering AI Agents

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30677)

- **Summary**: arXiv:2605.30677v1 Announce Type: new  Abstract: Agentic software reverse engineering systems are vulnerable to prompt injection attacks placed into the source code of executable binary files. This research demonstrates defensive tactics for detecting the presences of prompt injection strings in the decompiler output of adversarial example programs. Methods for obfuscating these attacks and subsequent methods for defending against these obfuscations are also explored. This research advances the understanding of risk and security of agentic software analysis systems necessary for their deployment into production-level cyber workflows.

- **Tags**: `adversarial` `agent` `prompt injection` `research`


---


## 17. LLM Anonymization Against Agentic Re-Identificatio

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30848)

- **Summary**: arXiv:2605.30848v1 Announce Type: new  Abstract: Agentic LLMs with web search change the threat model for text anonymization: weak contextual cues can become cross-referenceable evidence for re-identification, yet those same details also carry downstream analytic value of the text. Existing defenses either remove explicit identifiers, perturb text for formal privacy, or test rewritten text against non-web inference models, leaving underexplored the operating region between resistance to agentic web-search re-identification and utility retention. We introduce AURA (\textbf{A}nonymization with \textbf{U}tility-\textbf{R}etention \textbf{A}daptation), an LLM-powered \textit{mask-reconstruct} framework that decouples privacy localization from utility-preserving reconstruction and selects candidates with adversarial privacy and utility-retention checks. We evaluate AURA on real-user interview transcripts using re-identification attacks carried out by web-search agents, along with a utility evaluation based on interviewee-profile facts, codebook facts, and the joint contextual utility grid. Our results show that AURA improves the privacy-utility frontier by using adaptive privacy scope to strengthen resistance to agentic re-identification and using a mask-reconstruct anonymization method to better preserve contextual utility under fixed privacy scope.

- **Tags**: `adversarial` `agent` `llm` `privacy`


---


## 18. TRACE: Task-Aware Adaptive Self-Evolving Agentic Jailbreaking

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30883)

- **Summary**: arXiv:2605.30883v1 Announce Type: new  Abstract: The rise of LLM agents introduces a new threat by enabling planning, coding, and even end-to-end execution of expert-level attack workflows. However, this threat remains underexplored and underestimated since (i) safety alignment prevents LLMs from directly generating harmful instructions, and (ii) most existing jailbreak methods cannot consistently induce agents to execute malicious operations. In this paper, we propose TRACE, a practical agentic jailbreaking framework to further reveal the risks of this threat surface. To conceal the malicious intent, TRACE decomposes a malicious task into multiple subtask sequences under different schemes and selects the sequence with the fewest explicitly harmful subtasks. TRACE then disguises the remaining harmful subtasks as benign-looking instructions by embedding them in task-aware scenarios with related roles, environments, directives, and heuristics. The scenarios are iteratively evolved through well-defined transformation actions, which are sampled by a Q-learning-inspired mechanism, for inducing the agent to execute on the harmful subtasks. Extensive evaluations on AgentHarm and AdvCUA show that TRACE consistently outperforms existing jailbreak baselines across multiple advanced LLM agents, achieving up to 100% bypass rate and 0.73 average success score. We also demonstrate the effectiveness of TRACE in controlled cyberattack instances. Our code and demos are available at https://github.com/ZJU-LLM-Safety/TRACE.git.

- **Tags**: `agent` `alignment` `embedding` `jailbreak` `llm`


---


## 19. Thou Shall Not Pass: Gatekeeping Outbound TLS Connections

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.31020)

- **Summary**: arXiv:2605.31020v1 Announce Type: new  Abstract: Despite the widespread use of Transport Layer Security (TLS), its security guarantees are frequently compromised by outdated versions and misconfigurations. To analyze this problem, we collected more than 50 million TLS handshakes over a two-week period at our research institution, Fondazione Bruno Kessler, and analyzed three server-selected parameters against the recommendations of four TLS guidelines. Our analysis shows that while the use of insecure or outdated options is minimal, it remains persistent. More importantly, servers are adopting the latest TLS advancements much faster than official guidelines can be updated to provide directives for them. These findings, combined with the difficulty of configuring TLS clients due to their ephemeral, ubiquitous and server-dependent nature, leave users vulnerable to non-standard or outright insecure connections. To address this, we present TLSGatekeeper, a real-time, network-based tool that transparently monitors handshakes, analyzes server parameters, and, based on organizational policy, reports non-compliant connections without requiring client-side modifications. Unlike Next-Generation Firewalls, TLSGatekeeper preserves end-to-end privacy by validating only handshakes, and offers greater flexibility in defining undesired configurations. Our evaluation shows that TLSGatekeeper sustains traffic rates of up to 100 Gbps while preventing insecure connections, with an average added processing delay of 671 ns (TLS 1.3) and 795 ns (TLS 1.2) per handshake packet, making enforcement feasible at scale.

- **Tags**: `policy` `privacy` `rag` `research`


---


## 20. Local Differential Privacy with Correlated Noise Achieves Central-DP Optimal Cost

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30476)

- **Summary**: arXiv:2605.30476v1 Announce Type: cross  Abstract: We study privately estimating the sum of $n$ user-held values in the presence of an honest-but-curious server. This motivates requiring privacy not only at data release but also throughout server-side computation. We therefore adopt the local (pure) differential privacy model, in which each user transmits a noise-perturbed value. It is well known that independent local noise typically incurs a substantial utility loss compared to the centralized model, where noise is added only after aggregation.   We show that this gap is not fundamental. By carefully designing correlations among the locally added noise variables, we construct $\varepsilon$-DP mechanisms whose estimation cost matches the optimal cost achievable in the centralized setting, up to an arbitrarily small error.

- **Tags**: `differential privacy` `privacy`


---


## 21. On-Device Generative AI for GDPR-Compliant Visual Monitoring: Natural Language Alerts from Local Object Detection

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30544)

- **Summary**: arXiv:2605.30544v1 Announce Type: cross  Abstract: Visual monitoring systems that rely on cloud-based AI inference expose raw image data to external services, creating fundamental tensions with the data-minimisation principle of the General Data Protection Regulation (GDPR). This paper presents a proof-of-concept privacy-by-design pipeline that resolves this tension by confining all inference entirely to the edge device. A YOLOv5n-seg model compiled for a Hailo-8L AI accelerator delivers real-time object detection on a Raspberry Pi 5, from which raw pixel buffers are immediately discarded after inference. A stateful trigger engine forwards minimal JSON event payloads to a locally hosted instance of Phi-3 Mini (3.8B parameters, Q4_0 quantisation), which synthesises one-to-two sentence natural-language alerts for a human operator. No image data crosses the network boundary at any point; only the generated text alert is transmitted. We describe the full system architecture and implementation, report measured inference latency and resource utilisation on the target hardware, and present representative generated alerts. The results demonstrate that combining a dedicated neural-network accelerator with an on-device large language model on a single-board computer is not only feasible but produces practically deployable, human-readable monitoring output while aligning with GDPR Art. 5(1)(c) by design.

- **Tags**: `generative` `large language model` `privacy` `regulation`


---


## 22. Optimal conversion from R\'enyi Differential Privacy to $f$-Differential Privacy

- **Source**: [arxiv_cr](https://arxiv.org/abs/2602.04562)

- **Summary**: arXiv:2602.04562v3 Announce Type: replace  Abstract: We prove the conjecture stated in Appendix F.3 of \citet{zhu2022optimalaccountingdifferentialprivacy}: among all conversion rules that map a R\'enyi Differential Privacy (RDP) profile $\tau \mapsto \rho(\tau)$ to a valid hypothesis-testing trade-off $f$, the rule based on the intersection of single-order RDP privacy regions is optimal.   This optimality holds simultaneously for all valid RDP profiles and for all Type I error levels $\alpha$.   Concretely, we show that in the space of trade-off functions, the tightest possible bound is $f_{\rho(\cdot)}(\alpha) = \sup_{\tau \geq 0.5} f_{\tau,\rho(\tau)}(\alpha)$: the pointwise maximum of the single-order bounds for each RDP privacy region.   Our proof unifies and sharpens the insights of \citet{balle2019hypothesistestinginterpretationsrenyi}, \citet{asoodeh2021variantsdifferentialprivacylossless}, and \citet{zhu2022optimalaccountingdifferentialprivacy}.   Our analysis relies on a precise geometric characterization of the RDP privacy region, leveraging its convexity and the fact that its boundary is determined exclusively by Bernoulli mechanisms.   Our results establish that the \enquote{intersection-of-RDP-privacy-regions} rule is not only valid, but optimal: no other black-box conversion can uniformly dominate it in the Blackwell sense, marking the fundamental limit of what can be inferred about a mechanism's privacy solely from its RDP guarantees.

- **Tags**: `differential privacy` `privacy` `rag`


---


## 23. Steering Beyond the Support: Adversarial Training on Unsupervised Jailbroken Activation Simulation

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.24535)

- **Summary**: arXiv:2605.24535v2 Announce Type: replace  Abstract: Jailbreak prompts can trigger harmful completions on aligned LLMs, In accordance, safety steering has been proposed: test-time activation interventions that steer jailbreak activations to trigger refusal while preserving benign utility. However, existing steering methods are fundamentally supervised and tied to a static, limited training set, whereas real jailbreaks evolve and are often out-of-distributed from the training set, leading to failures on unseen attacks. In this paper, we tackle the failure on unseen jailbreaks problem, base on unsupervised latent direction discovery. We propose a bi-level adversarial training framework for zero-shot jailbreak defense. In the inner step, we simulate diverse jail-broken activations by extrapolating from refusal-state harmful-request activations via unsupervised latent direction discovery, which expands the coverage of real jailbreak activation subspaces. In the outer step, we train a potential-induced steering field to push these adversarial jailbroken states into refusal regions while keeping benign unchanged. Across three LLMs and six classical jailbreak families, our method achieves strong defense with attack success rates mostly below 5%, and rising subspace coverage throughout training helps explain the improved generalization.

- **Tags**: `adversarial` `jailbreak` `llm` `rag`


---


## 24. Bounded Behavioral Indistinguishability for Black-Box LLM Distillation

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30448)

- **Summary**: arXiv:2605.30448v1 Announce Type: new  Abstract: Black-box LLM distillation is usually evaluated as an output-matching problem: a student is considered successful when its responses are semantically similar to, or task-consistent with, those of a teacher. However, output similarity does not imply that the student is behaviorally indistinguishable from the model it imitates. We introduce bounded behavioral indistinguishability, formalized as $(\epsilon,q,t,\mathbb{A})$-behavioral indistinguishability over an explicit prompt distribution, where $\epsilon$ bounds distinguishing advantage, $q$ bounds oracle queries, $t$ bounds computation, and $\mathbb{A}$ denotes the adversary class.   We instantiate this notion on Qwen and Llama teacher-student pairs using a controlled $5,000$-prompt behavioral probe suite. For each family, we compare the teacher with both the base student and the LoRA-distilled student, measuring whether distillation reduces distinguishability rather than merely improving similarity. LoRA raises semantic similarity from $0.788$ to $0.862$ for Qwen and from $0.814$ to $0.874$ for Llama. Yet adversarial evaluation reveals remaining behavioral differences: learned discriminators retain nonzero advantage, and pairwise category analysis shows artifacts concentrated in style/format, robustness, and domain-technical prompts. A pairwise teacher-identification adversary confirms this trend. With a different-family Llama judge and A/B-swap consistency filtering, Qwen distinguishing advantage drops from $0.158$ for the base student to $0.081$ after LoRA distillation. Query-budget experiments show that disagreement-guided acquisition does not consistently outperform stratified random sampling, indicating that coverage and diversity remain strong baselines. Our results show that semantic fidelity is useful but insufficient: black-box LLM distillation requires bounded, adversarial, and category-aware evaluation.

- **Tags**: `adversarial` `distillation` `llm` `qwen` `rag`


---


## 25. VeriGate: Verifier-Gated Step-Level Supervision for GRPO

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30451)

- **Summary**: arXiv:2605.30451v1 Announce Type: new  Abstract: Group Relative Policy Optimization (GRPO) is an effective recipe for training reasoning models with verifier-based outcome rewards, but its supervision is sparse: when all sampled trajectories for a prompt receive the same verifier reward, the group-relative advantage collapses to zero and learning stalls. Outcome-only rewards also provide no step-level credit assignment, limiting exploration and making it harder to learn robust reasoning. We present VeriGate (Verifier-Gated Step-Level GRPO), a verifier-gated extension of GRPO that addresses these limitations with three design choices. First, VeriGate keeps the verifier in charge whenever verifier rewards induce a meaningful preference among sampled trajectories, and uses process supervision only when verifier rewards are degenerate. Second, instead of collapsing Process Reward Model (PRM) step scores into a single trajectory reward, VeriGate converts them into future-cumulated rewards to assign continuation-aware credit. Third, VeriGate transforms these rewards into group-normalized token-level advantages, restoring informative gradients and fine-grained credit assignment while remaining less susceptible to reward hacking than methods that optimize aggregated PRM scores. Empirically, training on MATH with 1.5B and 7B Qwen2.5-Instruct models and evaluating on six reasoning benchmarks, VeriGate improves average accuracy by about 20% and 12% for 1.5B and 7B models respectively, substantially reduces zero-gradient failures, decreases reward-hacking behavior, and improves reasoning quality relative to outcome-only GRPO and PRM-as-outcome baselines.

- **Tags**: `benchmark` `policy` `qwen` `rag` `reasoning`


---


## 26. Can Subgraph Explanations Be Weaponized to Steal Graph Neural Networks?

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30470)

- **Summary**: arXiv:2605.30470v1 Announce Type: new  Abstract: Graph Machine Learning as a Service (GMLaaS) platforms increasingly implement explainability interfaces to meet regulatory transparency requirements. However, this transparency creates exploitable vulnerabilities for model extraction attacks. We present the first model extraction attack specifically designed for graph classification under strict black-box constraints where the attacker observes only discrete class labels and binary explanation masks (no probability scores, gradients, or confidence values). Our method (1) uses model explanation outputs to guide Monte Carlo edge sensitivity estimation toward decision boundaries, with Hoeffding concentration guarantees on estimation accuracy and (2) exploits explanation subgraphs to efficiently narrow the boundary search space. Extensive experiments on benchmark graph datasets across multiple domains demonstrate our method's superiority over comparable baselines. These findings demonstrate that such explainability interfaces create exploitable attack surfaces, informing both defensive mechanisms and policy frameworks for explainable AI mandates. The implementation code is provided in https://github.com/LabRAI/XSTEAL/.

- **Tags**: `benchmark` `explainability` `policy`


---


## 27. Discovering a Zeta Map Algorithm on Dyck Paths via Mechanistic Interpretability

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30482)

- **Summary**: arXiv:2605.30482v1 Announce Type: new  Abstract: Machine learning is increasingly used in mathematical discovery, but in mathematics the desired output is often not a prediction itself, but an explicit construction that can be checked independently. We study this setting through the zeta map on Dyck paths, a classical bijection in the combinatorics of the q,t-Catalan numbers. We train a deliberately small one-layer, one-head encoder-decoder transformer on this map and analyze its learned computation using mechanistic interpretability tools, including decoder cross-attention analysis, linear probing, and causal intervention. The analysis reveals a level-based mechanism: encoder representations make path levels linearly accessible, while the decoder selects and traverses input positions in a structured way. Translating these signals into combinatorics leads to the scaffolding map, an explicit peak-centered traversal algorithm for Dyck paths. We prove that this algorithm agrees with the zeta map, modulo a reversal convention in the labeling. This gives a controlled example of AI-assisted mathematical discovery in which mechanistic interpretability turns model behavior into a precise, human-verifiable combinatorial algorithm.

- **Tags**: `interpretability` `mechanistic interpretability` `transformer`


---


## 28. Supervised Training Rapidly Degrades Early Visual Cortex Alignment Across Biologically Plausible Learning Rules

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30556)

- **Summary**: arXiv:2605.30556v1 Announce Type: new  Abstract: Random, untrained neural networks consistently match or exceed trained networks in representational similarity to early visual cortex. This puzzling finding challenges the assumption that learning improves brain alignment. We investigate it by tracking representational similarity analysis (RSA) alignment to human fMRI data across training for four learning rules: backpropagation (BP), feedback alignment (FA), predictive coding (PC), and spike-timing-dependent plasticity (STDP). Using 720 object images from the THINGS database and fMRI data from three subjects across six visual ROIs, we measure Spearman correlations between model and brain representational dissimilarity matrices at eight training checkpoints (epochs 0-40). We find that (1) a single epoch of training reduces V1 alignment by 25-90%, depending on the learning rule; (2) backpropagation reduces V1 alignment most severely (delta r = -0.080), while predictive coding and STDP preserve substantially more (delta r ~ -0.04); and (3) a weaker, opposite tendency appears in object-selective cortex (LOC), where BP shows the largest increase in alignment during training, although the absolute change is small. These results suggest that untrained architectures capture low-level visual statistics through inductive biases alone, and that global error signals (BP) reshape early representations more aggressively than local learning rules (PC, STDP), which better preserve brain-like structure.

- **Tags**: `alignment` `bias`


---


## 29. Benchmarking Machine Learning Uncertainty Quantification Methodologies for Predicting Turbine Gas Temperature Degradation

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30585)

- **Summary**: arXiv:2605.30585v1 Announce Type: new  Abstract: Effective prognostics and health management of modern engines relies on accurate turbine gas temperature predictions and robust uncertainty quantification to ensure reliability and safety. This paper investigates five major approaches for constructing prediction intervals -- namely the Delta method, Bayesian Monte Carlo Dropout, Bootstrap method, Lower-Upper Bound Estimation, and Mean-Variance Estimation -- as a means of capturing the uncertainty in neural network predictions of turbine gas temperature. Each approach is implemented within a unified experimental framework that employs cross-validation for hyperparameter selection, repeated train-test splits for performance robustness, and multiple metrics to evaluate both the accuracy and tightness of the intervals. In particular, Coverage Probability, Normalized Mean Prediction Interval Width, and the Coverage Width-based Criterion are measured to comprehensively assess each method's reliability and sharpness. Experiments conducted on a representative turbine gas temperature dataset reveal distinct trade-offs among the five methods in terms of interval coverage, width, and stability. These findings provide a practical guide for selecting and tuning prediction interval methods in engine health management and prognostics, ensuring both interpretability and precision in real-world applications.

- **Tags**: `benchmark` `interpretability` `rag` `robustness`


---


## 30. The Fast Mixing Mechanism for Differential Privacy

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30600)

- **Summary**: arXiv:2605.30600v1 Announce Type: new  Abstract: Randomized sketching is a central tool for compressing large-scale optimization problems while preserving accuracy. In particular, sketches that are based on structured matrices, such as the Hadamard matrix, can be applied efficiently and often yield solutions that approximate those of the original problem at much lower computational cost. In differential privacy (DP), Gaussian sketching has been used to solve DP linear regression, beginning with \citet{sheffet2017differentially, sheffet2019old} and later refined by \citet{lev2025gaussianmix, lev2026near}. However, although these methods achieve strong utility guarantees, they usually do not improve runtime over classical DP approaches. In this work, we introduce a new DP sketching mechanism based on fast transforms, which, in certain cases, matches the runtime of classical fast sketching methods. We prove state-of-the-art privacy guarantees for this mechanism and show that, in favorable regimes, they match those of the Gaussian sketch up to a constant factor. As an application, we combine this mechanism with recent sketch-based methods for DP linear regression to obtain a new algorithm with strong utility and improved runtime. We establish privacy and accuracy guarantees for this algorithm, yielding, to the best of our knowledge, the first fast method for DP ordinary least squares.

- **Tags**: `differential privacy` `privacy`


---


## 31. TASER: Task-Aware Stein Regularisation for Geometry-Driven Robustness

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30601)

- **Summary**: arXiv:2605.30601v1 Announce Type: new  Abstract: Modern deep networks remain fragile under distribution shift and adversarial perturbations, often due to excessive or poorly structured input sensitivity. We introduce TASER (Task-Aware Stein Regularisation), a training-time regularisation framework derived from Langevin Stein operators. By penalising pointwise Stein residuals under the training distribution, TASER encourages geometric compatibility between predictors and data density, inducing anisotropic, data-aware smoothness. We provide theoretical links between Stein regularisation and reduced first-order shift sensitivity, develop scalable implementation variants compatible with modern architectures, and demonstrate improved robustness and stability across regression and vision benchmarks. Across CIFAR-10 experiments, TASER consistently improves the adversarial robustness of established training methods without incurring statistically significant clean-accuracy degradation.

- **Tags**: `adversarial` `benchmark` `rag` `robustness` `vision`


---


## 32. Equivariant Latent Alignment via Flow Matching under Group Symmetries

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30705)

- **Summary**: arXiv:2605.30705v1 Announce Type: new  Abstract: Geometry-aware generative models and novel view synthesis approaches have shown strong potential in visual fidelity and consistency. In parallel, equivariant representation learning has emerged as a powerful framework for constructing latent spaces where analytically known group transformations could act directly, capturing geometric structure in data and enhancing both interpretability and generalization in novel view synthesis. However, we identify that existing approaches often suffer from latent misalignment, a discrepancy between the intended group action and the actually required transformations in the latent space. Consequently, the learned latents often fail to consistently preserve the equivariant relations imposed by the underlying group symmetry. To address this, we propose Residual Latent Flow, a flow-based framework that corrects the misaligned latents, thereby improving compliance with the underlying equivariance relation. Our comprehensive experiments show that our method significantly reduces latent misalignment and improves novel view synthesis quality, under rotation groups SO(n).

- **Tags**: `alignment` `generative` `interpretability`


---


## 33. What Makes LVLMs Hallucinate Less? Unveiling the Architectural Factors Behind Hallucination Robustness

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30911)

- **Summary**: arXiv:2605.30911v1 Announce Type: new  Abstract: Hallucination remains one of the key challenges undermining the reliability of Large Vision-Language Models (LVLMs). But what makes an LVLM hallucinate less? Many existing efforts focus on improving internal components of the model. We argue that hallucination fundamentally stems from how the model architecture is designed. To investigate this, we factor the architecture design into three dimensions: Linguistic Foundation (LF), Visual Representation (VR), and Semantic Alignment (SA), and categorize hallucinations into Co-occurrence, Similarity, and previously overlooked Uncertainty types. Building on this formulation, we propose CoSimUE, a benchmark that creates fine-grained hallucination scenarios through controlled textual perturbations and random perturbations, enabling mapping between design choices and hallucination behaviors. Experiments across 7 design aspects show that: 1) the widely emphasized scaling of model parameters has only limited impact on reducing all three types of hallucinations; 2) larger and better-trained language foundations can reduce co-occurrence hallucinations; 3) stronger visual encoders and higher resolutions mitigate similarity errors; 4) effective alignment strategies alleviate uncertainty hallucinations. 5) Furthermore, cross-dimensional analysis reveals that jointly enhancing visual fidelity and alignment quality yields the most comprehensive improvements. This study provides the first systematic exploration linking architecture-level design to hallucination robustness, offering practical guidance for developing reliable and efficient LVLMs.

- **Tags**: `alignment` `benchmark` `robustness` `vision`


---


## 34. Evaluating using Mock Tool Calls to Quarantine Untrusted Prompt Inputs

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30521)

- **Summary**: arXiv:2605.30521v1 Announce Type: new  Abstract: Large language models must frequently process untrusted inputs, such as judging an answer from another model or running tasks like spam and harm classifiers while under adversarial pressure. These inputs are often string-formatted directly into a prompt template, leaving systems fragile to manipulation. Current LLM specs from major providers like OpenAI distinguish trustworthiness along an Instruction Hierarchy, from System messages (most trusted) to Tool Results (least trusted). A possible natural mitigation is to wrap untrusted content in a mock tool call as a quarantine. We explore this hypothesis with an automated redteaming search over static attack strings across seven models and three LLM-as-a-Judge tasks. Counter to our hypothesis, tool-wrapping does not broadly improve robustness. On a binary evaluation task (GSM8K grading) it typically increases attack success rates, an apparent inversion of the instruction hierarchy. On scalar and pairwise tasks the effect is smaller and model-dependent, with no tested model reliably helped, and several showing inversion. We recommend evaluating this limitation in deployed systems, and longer-term, pursuing stronger Instruction Hierarchy training or new untrusted-input primitives.

- **Tags**: `adversarial` `large language model` `llm` `openai` `rag`


---


## 35. ImmigrationQA: A Source-Grounded Dataset and Small-Model Adaptation for U.S. Immigration Law

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30589)

- **Summary**: arXiv:2605.30589v1 Announce Type: new  Abstract: U.S. immigration law spans thousands of pages of official policy, federal regulations, and procedural guidance that change frequently and carry high stakes for petitioners who lack legal representation. We describe the construction of ImmigrationQA, a source-grounded question-answering dataset of 17,058 pairs across 13 immigration subdomains, and the fine-tuning of a Llama 3.2 3B Instruct model on that dataset using parameter-efficient LoRA. The corpus was assembled from 11 primary and secondary sources -- including the USCIS Policy Manual, 8 CFR, BIA precedent decisions, and community Q&amp;A -- yielding 10,056 validated canonical documents and 18,308 text chunks. Structured QA pairs were generated from these chunks using Claude Sonnet 4.6 via five mode-specific prompts, with 22 pairs rejected for insufficient source-span overlap. The fine-tuned model was evaluated against a held-out split of 993 pairs using LLM-as-judge scoring on a 101-example stratified sample. The fine-tuned model scored a mean of 1.08/3.0 (16.8% fully correct; 101-example stratified eval) versus the Llama 3 8B base model at 0.85/3.0 (4% fully correct), a relative improvement of 27% in mean score; a zero-shot Claude Sonnet baseline scored 1.52/3.0 (25% fully correct). The fine-tuned model shows concentrated improvement in procedural subdomains (travel documents, adjustment of status, nonimmigrant visas) while remaining weak on complex legal reasoning and time-sensitive statistics. The full pipeline ran for approximately $29 in cloud compute. All artifacts -- dataset, model, code, and prompt templates -- are publicly released. The system is not a substitute for legal counsel and does not reflect regulatory changes after the corpus crawl date.

- **Tags**: `claude` `fine-tuning` `llm` `policy` `reasoning`


---


## 36. COFT: Counterfactual-Conformal Decoding for Fair Chain-of-Thought Reasoning in Large Language Models

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30641)

- **Summary**: arXiv:2605.30641v1 Announce Type: new  Abstract: Large language models (LLMs) can reveal and amplify societal biases during chain-of-thought (CoT) generation. We present COFT (Chain of Fair Thought), a training-free decoding method that applies token-level fairness control at decode time, with distribution-free marginal validity guarantees (under exchangeability) for any frozen causal language model. COFT operates in three stages. First, it creates a masked counterfactual prompt by replacing sensitive spans with neutral tokens. Second, it compares the factual and masked logit distributions through lightweight logit fusion to attenuate attribute-driven biases. Third, it uses dual-branch split-conformal calibration to certify per-step candidate token sets at a user-chosen risk level. We evaluate COFT across six models and multiple bias benchmarks. Our method reduces standard bias metrics by 30-55% (median 38%) while preserving task utility and language quality. Reasoning accuracies remain unchanged within run-to-run noise margins. The computational overhead is modest, equivalent to one additional cached forward pass (<=11%). COFT offers a clear, auditable path to safer CoT generation with significant bias reduction, negligible utility loss, and no requirement for retraining, auxiliary classifiers, or weight access.

- **Tags**: `benchmark` `bias` `chain-of-thought` `fairness` `large language model`


---


## 37. EUDAIMONIA: Evaluating Undesirable Dynamics in AI

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30654)

- **Summary**: arXiv:2605.30654v1 Announce Type: new  Abstract: Large language models (LLMs) are increasingly used as conversational partners for companionship, emotional disclosure, and interpersonal advice, but the social dynamics of these interactions can create harms that are not captured by capability-oriented or traditional safety evaluations. We introduce the Social AI Design Code, a framework for evaluating whether LLMs align with user welfare in social interactions, including whether they encourage harmful intimacy, dependence, or prolonged engagement. To evaluate these risks in natural and diverse user-LLM interactions, we operationalize the code with EUDAIMONIA, a benchmark of 969 user inputs and 3,147 design-requirement violation checks built from WildChat through weak-to-strong filtration, multi-model relabeling, and controlled rewriting. Evaluating 22 recent LLMs, we find that even the strongest models, Claude-Opus-4.7 and GPT-5.5, violate 30.7% and 27.2% of checks, respectively. Extended thinking does not reduce violation rates, suggesting that these failures are persistent social-alignment problems rather than deficits solvable through test-time reasoning alone.

- **Tags**: `alignment` `benchmark` `claude` `gpt` `large language model`


---


## 38. The Flip Side of RLHF: On-Policy Feedback for Reward Model Self-Supervised Improvement

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30888)

- **Summary**: arXiv:2605.30888v1 Announce Type: new  Abstract: Building strong reward models (RMs) for language model alignment is bottlenecked by the cost and difficulty of acquiring diverse and reliable preference data from human annotation or judge models. It is dramatically worse as the policy evolves beyond the static RM training. Therefore, we propose SAVE (Self-supervised reward model improvement via Value-Anchored On-policy feedback), a framework that grades on-policy responses as feedback by using the value function for on-policy RM training. SAVE naturally converts the reward-graded on-policy responses into supervision with a prompt-specific value head as an adaptive anchor. It computes RM advantages and filters ambiguous samples to update the RM via a contrastive objective. The effectiveness of SAVE for enhancing RM training is strongly validated through rigorous empirical evaluation across six diverse benchmarks. It achieves outperforming results across all datasets while maintaining consistent improvements across three RL algorithms (GRPO, RLOO, GSPO) and different policy backbones.

- **Tags**: `alignment` `benchmark` `policy` `rlhf` `vision`


---


## 39. The Surface You Test Is Not the Surface That Breaks

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30454)

- **Summary**: arXiv:2605.30454v1 Announce Type: new  Abstract: Tool-augmented LLM agents are vulnerable to prompt injection: a third party who controls part of the agent's context can plant instructions that the agent then executes as if they came from the user. Current evaluations report a single attack success rate per model on one channel, the tool output and treat that number as the model's vulnerability. But tool descriptions, which the agent reads at every turn before any tool is called, are themselves an injection surface that the attacker can choose instead. We hold the injection payload byte-identical and deliver it through both surfaces across 13 LLMs from six families and four task suites. The same bytes invert in success rate across models: GPT-4.1 is 96 percent vulnerable on tool outputs but only 4 percent on tool descriptions, while GEMINI-3-FLASH shows the mirror pattern at 20 percent and 98 percent. A variance decomposition over 6,830 attempts attributes 0 percent of the variation in attack outcomes to the surface alone, while the model-surface interaction accounts for 16.7 percent. Vulnerability is a property of the pairing, not the channel. The Adaptive Attack Rate, defined as the per-cell maximum over surfaces, exceeds the strongest fixed-surface baseline by +9.1 percentage points on average. Standard prompt-level defenses inherit the same blindspot, reducing tool-output ASR to 10-18 percent while leaving the description channel above 54 percent. Both attack and defense evaluation must report per-surface vulnerability.

- **Tags**: `agent` `gemini` `gpt` `gpt-4` `llm`


---


## 40. Strengthening Polymorphic Prompt Assembling: Dynamic Separator Generation Against Emerging Prompt Injection Attacks

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30534)

- **Summary**: arXiv:2605.30534v1 Announce Type: new  Abstract: Polymorphic Prompt Assembling (PPA) defends LLM agents against prompt injections by randomly selecting separator pairs from a fixed pool to isolate user input from system instructions. Although effective, static pool reuse exposes a blast-radius vulnerability: once a separator leaks, it can be exploited in future requests. We propose a dynamic per-request separator generation using domain-separated SHA-256 digests keyed on the timestamp, session identifier, and cryptographic nonce. Each assembled prompt receives a unique (BEGIN, END) canary pair, thereby limiting leakage exposure to a single request. We evaluated our extension against 16 injection payloads on Llama-3.3-70B-Instruct-Turbo, with cross-model validation on DeepSeek-V4-Flash model. Against the M1 obfuscation payload (leetspeak + urgency), the dynamic mode reduces the Attack Success Rate (ASR) from 0.88 to 0.38, yielding a statistically significant 2.3 x mitigation verified by non-overlapping 95% Wilson confidence intervals. Against format_breakout_salad, static separator leakage (leak_rate = 0.467) is eliminated entirely in the dynamic mode (0.000), confirming the blast-radius reduction in practice. The implementation requires no model fine-tuning, adds 2.7 microseconds prompt-assembly overhead per request, and is backward compatible with the existing PPA SDK.

- **Tags**: `agent` `deepseek` `fine-tuning` `llm` `prompt injection`


---


## 41. An Organization-Scoped LLM Agent Runtime Architecture for Regulated Cybersecurity Operations

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30604)

- **Summary**: arXiv:2605.30604v1 Announce Type: new  Abstract: Regulated cybersecurity workflows lack a runtime substrate that enforces organization-level scope across retrieval, tool calls, memory, findings, reports, and audit while remaining model-agnostic and locally deployable. Recent large language model (LLM) agent systems report strong results on isolated cybersecurity tasks, yet they do not by themselves define an auditable platform architecture for regulated security operations centre (SOC) and compliance workflows, where a single analyst may trigger actions that bind the organization, and where the runtime must integrate with existing SIEM/XDR stacks as a primary source of context and alert-driven triggers rather than operate as a standalone analytical layer. This paper proposes an organization-scoped LLM agent runtime architecture for financial cybersecurity. The contribution is a typed Security Context that is created at every entry point, including SIEM/XDR notifications ingested as first-class triggers, and enforced at every component boundary, combined with a shared Runtime Core, logical specialist subagents, a governed Tool Adapter Layer exposing SIEM/XDR query, enrichment, and response primitives under uniform policy and audit, structured findings with evidence references, tiered human-in-the-loop (HITL) gates, and append-only audit. Model Context Protocol (MCP), extended telemetry, digital twins for pentesting, graph retrieval, and federated knowledge sharing are treated as optional extension paths rather than mandatory runtime assumptions. We describe an implementable slice as the architecture's testability surface, and we propose a falsifiable evaluation plan with metric-level pass criteria for architecture readiness, security-policy enforcement, evidence traceability, output quality, and operational observability.

- **Tags**: `agent` `large language model` `llm` `policy`


---


## 42. Depth-Dependent Indirect Prompt Injection in Tool-Calling ReAct Agents: Injection Depth, Payload Framing, and Turn-Budget Sensitivity

- **Source**: [arxiv_cr](https://arxiv.org/abs/2605.30686)

- **Summary**: arXiv:2605.30686v1 Announce Type: new  Abstract: ReAct agents that interleave chain-of-thought reasoning with tool calls are increasingly deployed for real tasks such as scheduling, file retrieval, and data access. Their tool observation loop creates a direct attack surface: an adversary who controls any tool's return value can embed instructions that redirect the agent away from the user's goal, a threat known as indirect prompt injection. Existing benchmarks evaluate attack success rate (ASR) at a fixed injection position under fixed conditions, leaving three risk dimensions unexplored: where in the tool sequence the payload appears (injection depth), what rhetorical register it uses (framing), and how many turns the agent is permitted (turn cap). We conduct four controlled studies on 20 scenarios spanning five attack categories, totalling 460 trials against GPT-4o-mini and Claude Haiku at a combined API cost under 0.36 USD. Study 1 shows that ASR against GPT-4o-mini decays from 60% at depth 1 to 0% at depths 4 and 5 (Cramer's V = 0.58, p < 0.001; restricted to within-sequence depths 1-3: V = 0.47, p = 0.0013), driven by model resistance at depth 1 and task completion before payload encounter at deeper positions. Study 2 replicates the depth experiment on Claude Haiku, which achieves 0% ASR at every depth through a combination of conservative tool invocation and genuine instruction resistance. Study 3 shows that framing modulates ASR between 25% (neutral) and 75% (persona) at depth 1, a 50-percentage-point range that does not reach statistical significance at N = 20 per condition. Study 4 confirms that ASR is stable across turn caps of 3, 5, and 7, indicating the turn budget is not a risk factor in this setting. Our results establish injection depth as the dominant variable and show that sanitising only the first tool observation captures 67% of measured injection successes.

- **Tags**: `agent` `benchmark` `chain-of-thought` `claude` `gpt`


---


## 43. LLMs Without Deep Neural Networks: New Architecture, Benefits and Case Study

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30385)

- **Summary**: arXiv:2605.30385v1 Announce Type: new  Abstract: The purpose of this article is to provide validation to my deep neural network alternative in the context of LLMs. Very recently, there has been a significant interest by Chinese researchers in a model called RBF network, as a substitute to standard DNNs, with increased explainability and higher accuracy. It turns out that my new model, discovered independently, is based on the exact same machinery. But with a major twist: it does not need DNN as it finds the global optimum of the loss function in closed form, in one iteration, thus eliminating the tedious training step. Here I provide a high-level overview of my technology, with case study and comparison to similar methods.

- **Tags**: `explainability` `llm` `research`


---


## 44. Calibrated Preference Learning: The Case of Label Ranking

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30447)

- **Summary**: arXiv:2605.30447v1 Announce Type: new  Abstract: Calibration, the alignment of predicted probabilities with true outcome frequencies, is essential for reliable decision-making. While extensively studied for classification and regression, calibration has not been formally addressed for probabilistic label ranking, where the goal is to predict a distribution over orderings of a label set. Naively treating rankings as classes ignores their structure and fails to capture important modalities such as pairwise and top-k predictions. We formalize calibration for label ranking and develop a hierarchy of notions covering full rankings, sub-rankings, and top-k rankings. We prove that full-rank calibration implies the others but not conversely, and sub-ranking and top-k calibration are incomparable. Empirically, we find popular label ranking models are often poorly calibrated, with substantial differences between sub-ranking and top-k metrics. Applying our framework to RLHF reward models, we find that calibration correlates strongly but not perfectly with benchmark accuracy, suggesting it captures a meaningful quality dimension beyond top-1 accuracy. These findings motivate future work on understanding the downstream effects of miscalibration and developing methods to correct it.

- **Tags**: `alignment` `benchmark` `rlhf`


---


## 45. Scalable Constrained Multi-Agent Reinforcement Learning via State Augmentation and Consensus for Separable Dynamics

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30461)

- **Summary**: arXiv:2605.30461v1 Announce Type: new  Abstract: We present a distributed approach for constrained Multi-Agent Reinforcement Learning (MARL) that combines state-augmented policy learning with distributed consensus over dual variables. Our method targets systems where agents have separable dynamics but must coordinate to satisfy global resource constraints, a setting in which, as we demonstrate empirically, independent learning fails to produce feasible solutions because agents cannot determine appropriate individual contributions toward collective constraint satisfaction. The key technical contribution is showing that lightweight neighbor-to-neighbor consensus over Lagrange multipliers suffices for globally coordinated constraint enforcement while preserving the scalability of independent training. Each agent learns a single augmented policy offline, conditioned on both its local state and a dual variable encoding constraint feedback. During execution, agents reach agreement on this dual variable through local communication alone. We prove that under mild connectivity assumptions, the consensus error among agents' multipliers is bounded, and show that this translates to a bounded constraint violation that decreases with graph connectivity and the number of consensus rounds. Unlike centralized training with decentralized execution (CTDE) approaches, whose complexity grows at least quadratically with agent count, our method scales linearly in both training and execution. Experiments on smart grid demand response demonstrate that consensus coordination is \emph{essential for feasibility}: without it, agents satisfy grid capacity constraints only by indefinitely postponing demand, a degenerate non-solution. With consensus, agents converge to a shared dual variable and satisfy both grid constraints and demand fulfillment, scaling to thousands of agents while CTDE baselines are limited to dozens.

- **Tags**: `agent` `llm` `policy`


---


## 46. idSCD: Identifying Training Datasets through Semantic Correlation Descriptors

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30462)

- **Summary**: arXiv:2605.30462v1 Announce Type: new  Abstract: Can a dataset be recognized from the spurious correlations it induces during training? We argue that datasets leave dataset-specific traces in a model's learned semantic correlation structure: incidental regularities that are predictive within a dataset, but not causal for the underlying task, can be internalized during training. We use this insight to study dataset-level membership inference, moving beyond existing methods that rely on behavioral or distributional evidence such as confidence scores, losses, margins, generated samples, or query responses. We introduce a white-box semantic fingerprinting approach based on semantic correlation descriptors (SCDs), which capture the semantic correlation structure learned by a model and make it comparable across dataset mixtures. In a controlled leave-one-dataset-out diagnostic, SCDs recover dataset-specific changes and perfectly separate matching from non-matching dataset pairs. We then propose a practical SCD-based membership score that tests whether a target dataset is part of a model's training mixture using only the model's SCD and the target dataset's standalone SCD, without requiring leave-one-dataset-out models. Across three diverse experimental settings, with dataset groups for natural language inference, emotion classification, and medical text classification, we test both the advantages and limitations of SCD-based membership inference with different degrees of semantic separation and keyword support between dataset splits. On average, the classifier based on this score achieves the highest performance and the lowest std, outperforming black-box baselines RMIA, Attack-P, and LiRA, as well as the white-box SIF baseline. These results show that dataset membership can be traced through internal semantic correlations, with the largest relative gain exceeding 60% in ROC-AUC when dataset groups expose distinct semantic particularities.

- **Tags**: `membership inference` `rag`


---


## 47. Measuring, Localizing, and Ablating Alignment Signatures in LLMs

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30526)

- **Summary**: arXiv:2605.30526v1 Announce Type: new  Abstract: Aligned language models often exhibit a recognizable AI-like style, yet its connection to post-training and internal representations remains poorly understood. In this work, we study whether post-training introduces or amplifies AI-like stylistic regularities and whether these regularities have a localized internal signature. To this end, we compare human text, base-model generations, and aligned-model generations under matched human-source prefixes. Aligned generations show lower human-corpus affinity and higher AI-detection rates than base generations, suggesting that post-training shifts generated text away from human-corpus style and toward detector-visible AI-like text. We then introduce PASTA (Post-training Alignment Signature Targeted Ablation), a training-free method that estimates a post-training alignment signature from aligned-base residual contrasts and ablates the corresponding direction during decoding. Across 11 aligned models and 6 AI detectors, PASTA lowers the detection rate for most aligned models; this effect transfers well across detectors and is not reproduced by random directions. Qualitative analysis suggests that PASTA generations remain relevant and coherent while exhibiting greater stylistic variation. Together, these results show that AI-like stylistic effects of post-training can be measured, localized, and causally tested through activation ablation.

- **Tags**: `alignment` `llm`


---


## 48. The Long-Term Effects of Data Selection in LLM Fine-Tuning

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30537)

- **Summary**: arXiv:2605.30537v1 Announce Type: new  Abstract: Data selection is increasingly used to reduce the cost of large language model (LLM) fine-tuning, with recent methods prioritizing samples by current utility, diversity, quality, or influence. This paper studies a different question: when fine-tuning occurs over multiple stages, can selection strategies that look optimal now make the model less adaptable later? We introduce a long-horizon view of LLM data selection in which a selector is evaluated not only by immediate task performance, but also by future adaptation speed, forgetting, capability imbalance, and out-of-distribution robustness. We compare representative random, loss-based, gradient-based, diversity-based, quality-based, and utility-diversity selection families under a unified multi-stage protocol. Through controlled experiments designed to instantiate this protocol, we show how short-term selectors can exhibit rank reversal: they improve the current stage while slowing subsequent learning and increasing forgetting. We formalize this behavior as \emph{myopic selection}, provide a simple local analysis of why it can occur, and propose a diagnostic Long-Horizon Aware Selection (LHAS) objective that augments immediate utility with coverage, future-proxy transfer, and anti-concentration terms. The study argues that data selection should be evaluated as a training intervention that shapes the model's learning trajectory, rather than only as a local data-efficiency mechanism.

- **Tags**: `efficiency` `fine-tuning` `large language model` `llm` `rag`


---


## 49. Active Timepoint Selection for Learning Measure-Valued Trajectories

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30625)

- **Summary**: arXiv:2605.30625v1 Announce Type: new  Abstract: Inferring continuous probability paths from sparse snapshots is a fundamental challenge in domains like single-cell biology, where high-fidelity data acquisition is often destructive and constrained by prohibitive sequencing costs. This motivates the need for active learning strategies to strategically select optimal measurement times. However, designing active learning policies for this setting remains an open problem: the target objects reside on the infinite dimensional Wasserstein space where standard Euclidean metrics are ill-defined, and current interpolation methods lack epistemic uncertainty quantification. We introduce a framework which extends active experimentation to the space of measures. By leveraging Linearized Optimal Transport (LOT), we map distributional snapshots into a tangent space amenable to Gaussian Process modeling, allowing us to construct a tractable probabilistic surrogate for the underlying probability path. This yields an acquisition policy that iteratively selects measurement times to minimize uncertainty. Empirical results demonstrate that our strategy outperforms uncertainty-agnostic baselines on both synthetic and real-world datasets.

- **Tags**: `policy` `rag`


---


## 50. CellBRIDGE: Learning Cellular Trajectories via Interaction-Aware Alignment

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30635)

- **Summary**: arXiv:2605.30635v1 Announce Type: new  Abstract: Inferring dynamics from population snapshots is a fundamental challenge in machine learning and biology. In scRNA-sequencing (scRNA-seq), destructive measurements preclude direct tracking of individual cells across time, making trajectory inference underdetermined. Optimal Transport (OT) provides a principled framework for snapshot alignment, but a long-standing modeling question is which cost functions yield biologically meaningful couplings. Standard OT approaches rely on gene-expression distances, implicitly treating cells as independent points and neglecting structured cell-cell communication mediated by ligand-receptor signaling. We introduce CellBRIDGE (Cell-Based Regularized Interaction-Driven Gene Expression), which augments feature-based OT with a directed, typed interaction cost derived from ligand-receptor activity. By explicitly modeling cell-cell communication, CellBRIDGE improves cross-snapshot couplings and downstream trajectory estimates across synthetic and real scRNA-seq datasets relative to feature-only baselines. Notably, CellBRIDGE enables mechanistically interpretable in silico perturbations: on lung cancer data, silencing specific ligand-receptor pairs induces trajectory shifts that recapitulate expected effects of targeted pathway inhibition.

- **Tags**: `alignment`


---


## 51. CSULoRA: Closest Safe Update Low-Rank Adaptation

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30640)

- **Summary**: arXiv:2605.30640v1 Announce Type: new  Abstract: Low-rank adaptation has become a standard method for parameter-efficient fine-tuning of large language models, but even small amounts of unsafe or adversarial fine-tuning data can substantially weaken the safety behavior of aligned models. Existing safety-preserving LoRA methods often rely on hard interventions such as projection, pruning, thresholding, or additional training objectives. While these methods can suppress unsafe update directions, they may also remove task-relevant information or require extra tuning. We introduce CSULoRA, a post-hoc method for correcting trained LoRA adapters through closest safe update estimation. CSULoRA estimates a safety-aligned subspace from the weight displacement between a safety-aligned model and its corresponding base checkpoint. It then decomposes each LoRA update into fully aligned, partially aligned, and off-subspace components. Instead of discarding components outside the estimated safety subspace, CSULoRA solves a closed-form penalized minimum-change problem that preserves the fully aligned component while smoothly attenuating potentially unsafe directions according to their relative energy. In adversarial fine-tuning experiments, CSULoRA substantially reduces attack success rate while preserving most of the utility gains obtained from standard LoRA fine-tuning.

- **Tags**: `adversarial` `fine-tuning` `large language model`


---


## 52. Diffusion Models Preferentially Memorize Prototypical Examples or: Why Does My Diffusion Model Love Slop?

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30642)

- **Summary**: arXiv:2605.30642v1 Announce Type: new  Abstract: Generative models have a persistent limitation: their tendency to memorize training data can create legal liabilities and erode creative diversity. Understanding which samples are memorized in whole or in part, and under what conditions, therefore remains an important open problem. Here we answer the question "Are atypical or rare samples memorized first?" in the negative. We train diffusion models on strings generated according to the production rules of the Random Hierarchy Model (RHM), and find that samples composed of common substrings are preferentially memorized. This holds true even if the training data consists of entirely unique samples, indicating that deduplication at the data point level does not provide a meaningful privacy guarantee. Correspondingly we predict, then observe, delayed memorization for fat-tailed datasets (i.e., those with more atypical samples). This effect is amplified when fat-tails are introduced into high-level production rules. These together suggest that dataset diversity, particularly at higher levels of abstraction, plays an important role in staving off memorization. Finally, we identify an intermediate regime of partial memorization in which common substrings are learned first and subsequently overproduced during generation. If training is stopped in this regime, models will exhibit the reversion-to-the-mean blandness often derided as "slop".

- **Tags**: `diffusion` `generative` `privacy`


---


## 53. Convergence of Steepest Descent and Adam under Non-Uniform Smoothness

- **Source**: [arxiv_lg](https://arxiv.org/abs/2605.30648)

- **Summary**: arXiv:2605.30648v1 Announce Type: new  Abstract: Recent work has analyzed the convergence of first-order methods under non-uniform smoothness assumptions that better model the loss landscape in machine learning tasks. We generalize this assumption to objectives whose curvature is an affine function of the objective value. This property is satisfied by a broad class of problems, including logistic regression, generalized linear models with a logistic link function, softmax policy gradient in reinforcement learning, and a class of neural networks. Under this assumption and gradient domination conditions, we establish a general convergence rate for the steepest descent method, and deterministic, diagonal variants of RMSProp and Adam. Our results imply that for logistic regression on separable data and the softmax policy gradient objective, sign GD converges linearly and is provably faster than GD. Furthermore, we show that for a class of two-layer neural networks on separable data, RMSProp and Adam can converge at a linear rate with a constant step-size and momentum parameter. Finally, we present a lower bound demonstrating that, under our assumption, RMSProp and Adam are provably faster than AdaGrad, AMSGrad, gradient descent, and heavy-ball momentum.

- **Tags**: `policy`


---


## 54. Uncertainty-Aware and Temporally Regulated Expert Advice in Reinforcement Learning for Autonomous Driving

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30576)

- **Summary**: arXiv:2605.30576v1 Announce Type: new  Abstract: Exploration in reinforcement learning for autonomous driving is inherently unsafe: agents must experience novel behaviors to learn, yet exploration can lead to collisions or off-road driving. We propose an uncertainty-aware framework that leverages expert advice to guide exploration while avoiding long-term dependence. Advice is triggered when epistemic or aleatoric uncertainty exceeds adaptive thresholds derived from rolling buffers, ensuring advice evolves with the agent's confidence. A commitment-cooldown strategy with a stochastic early-stop heuristic regulates the duration and frequency of guidance, exposing the agent to coherent maneuvers without exhausting the advice budget. Expert and agent experiences are combined in a shared replay buffer within an off-policy implicit quantile network (IQN) backbone, enabling efficient reuse of expert trajectories. Experiments in CARLA show that our method outperforms the IQN baseline, improving success by 5-7% and reducing failures, demonstrating that risk-sensitive uncertainty coupled with regulated expert integration enables safer and more efficient exploration for sensor-based RL policy learning in unsignalized intersection navigation.

- **Tags**: `agent` `policy` `rag`


---


## 55. EHRBench: An Automated and Reliable EHR-based Benchmark for Clinical Decision Making with LLMs

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30637)

- **Summary**: arXiv:2605.30637v1 Announce Type: new  Abstract: Clinical decision-making (CDM) is central to real-world clinical workflows, where clinicians infer diagnoses, select treatments, or anticipate future health outcomes under incomplete evidence. LLMs are increasingly used to support these decisions due to strong language capabilities, broad biomedical knowledge, and efficiency, yet the reliability of LLMs on real-world clinical decision tasks remains insufficiently understood. To evaluate CDM models, especially LLM-based models, an ideal and practical medical decision benchmark should be constructed via an automated yet reliable pipeline to ensure both scale and quality. Moreover, the grounding of a CDM benchmark in real patient EHRs can better support evaluation on practical CDM tasks that require substantive biomedical knowledge and clinical inference. To fill the gaps, we introduce EHRBench, an automated and reliable EHR-grounded benchmark for evaluating LLM-based clinical decision-making at scale. To ensure scalability and reliability, EHRBench is constructed through an EHR-LLM-KB(knowledge-base) interaction pipeline. For efficiency, we use a specialized LLM to automatically convert encounter-level EHR trajectories into structured templates and deterministically instantiate the templates into QA items. In parallel, we apply systematic KB-based verification and enrichment to filter hallucinated or ambiguous relations and to improve reliability. Using this pipeline, we construct nearly 1M (960,067) QA items spanning three core inference-required clinical decision tasks: diagnosis, treatment, and prognosis. We benchmark more than 30 representative LLMs on EHRBench and provide detailed analyses of performance and robustness. The results show consistent capability trends across settings, further validating the reliability of EHRBench and highlighting actionable gaps toward clinically reliable LLM systems.

- **Tags**: `benchmark` `efficiency` `llm` `robustness`


---


## 56. Structure-Induced Information for Rerooting Levin Tree Search

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30664)

- **Summary**: arXiv:2605.30664v1 Announce Type: new  Abstract: Subgoal-based policy tree search, which uses a policy to guide search, is effective for complex single-agent deterministic problems but often relies on explicit subgoal generation that can incur substantial overhead and hinders scalability. In this paper, we overcome these limitations by using a learned ``rerooter'' through the recently-introduced $\sqrt{\text{LTS}}$ algorithm. A rerooter implicitly decomposes the problem into soft subtasks. While previous work focused on the formal guarantees for given or handcrafted rerooters, in this work we propose three rerooter designs: (i) a clustering-based rerooter that exploits global state-space structure, (ii) a heuristic-based rerooter that leverages learned cost-to-go estimates, and (iii) a hybrid that combines both signals. Our framework avoids having to explicitly reconstruct and reason over generated subgoals, thereby enabling scalable allocation of search effort with significantly lower computational overhead. Empirically, our rerooting-based methods scale to complex environments where subgoal-based policy tree search fails, and achieve state-of-the-art online training efficiency on the domains tested.

- **Tags**: `agent` `efficiency` `policy` `rag`


---


## 57. Healthcare Mechanisms from Policy-as-Code Search under Strategic Provider Response

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30680)

- **Summary**: arXiv:2605.30680v1 Announce Type: new  Abstract: Healthcare mechanisms are inseparable from the strategic provider response they induce: existing healthcare AI benchmarks hold this response fixed and so cannot evaluate mechanisms by the equilibrium they produce. We recast hospital mechanism design as program synthesis for language models: typed, inspectable rule programs are executed and scored by Medi-Sim, a multi-agent simulator with five strategic provider channels (coding, selection, delay, effort, triage). An incentive sweep recovers classical health-economics findings as adjacent regimes -- up-coding and low-complexity-patient selection under profit pressure, and Goodhart-style drift where measured performance becomes anti-correlated with true outcomes -- and a single audit lever exposes pressure migration: closing the coding channel more than doubles low-complexity selection. LLM-guided evolutionary code search over the same rule-program space then synthesizes an inspectable mixed-objective program that eliminates up-coding, halves rejection, and retains most of the profit-oriented baseline's funds.

- **Tags**: `agent` `benchmark` `llm` `policy`


---


## 58. MAVEN: Improving Generalization in Agentic Tool Calling

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30738)

- **Summary**: arXiv:2605.30738v1 Announce Type: new  Abstract: Generalization across agentic tool-calling environments remains a central challenge for reliable agentic reasoning systems. Although large language models achieve strong results on individual benchmarks, their ability to compose reasoning strategies, preserve intermediate states, and coordinate tools across domains remains underexplored. We present MAVEN (Modular Agentic Verification and Execution Network), a lightweight symbolic reasoning scaffold for structured decomposition, adaptive tool orchestration, and intermediate verification. We evaluate MAVEN across established tool-calling benchmarks, including BFCL v3, TauBench, Tau2Bench, AceBench, and introduce MAVEN-Bench, a stress-test benchmark for multi-step mathematical and physical reasoning with explicit verification and adversarial task composition. MAVEN-Bench exposes a substantial gap between partial reasoning quality and end-to-end task success; in direct MAVEN-Bench runs, MAVEN improves its GPT-OSS-120b base model from 48% to 71% accuracy without additional training. It also remains competitive with frontier proprietary baselines while using an open-weight backbone with an estimated cost ratio of roughly 1/10, suggesting that lightweight verification-centered scaffolds can strengthen compositional reasoning and motivate more process-aware evaluation of agents in the wild.

- **Tags**: `adversarial` `agent` `benchmark` `gpt` `large language model`


---


## 59. COMPASS: Cognitive MCTS-Guided Process Alignment for Safe Search Agents

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30838)

- **Summary**: arXiv:2605.30838v1 Announce Type: new  Abstract: LLM-powered search agents enable multi-step reasoning and tool use. However, these capabilities introduce retrieval-induced safety degradation, as harmful intents may decompose into seemingly innocuous sub-queries that lead to unsafe outcomes. Existing alignment methods struggle to capture sparse safety signals and fail to supervise diverse violations across multi-step interactions. We propose COMPASS, a Cognitive MCTS-Guided Process Alignment framework designed to achieve robust safety alignment throughout the agent workflow while preserving general utility. COMPASS integrates cognitive tree exploration (CTE) to efficiently synthesize stealthy attack trajectories, and introspective step-wise alignment (ISA) to isolate risky intermediate actions for fine-grained process supervision. Empirical results show that COMPASS achieves a favorable safety-utility trade-off while requiring substantially less training data.

- **Tags**: `agent` `alignment` `llm` `reasoning` `tool use`


---


## 60. Distilling LLM Feedback for Lean Theorem Proving

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30861)

- **Summary**: arXiv:2605.30861v1 Announce Type: new  Abstract: Post-training for reasoning models typically combines supervised fine-tuning with reinforcement learning from verifiable rewards, most commonly with GRPO. However, this algorithm suffers from sparse rewards, limited exploration, and mode collapse. Building upon recent works on self-distillation, we propose Feedback Distillation, a training method where the model is trained to match, at the token level, its own distribution conditioned on privileged feedback produced by a language model. Feedback Distillation offers token-level supervision and can inject external knowledge. Evaluating our method for Lean4 theorem-proving, we find that Feedback Distillation maintains greater diversity in generated trajectories than GRPO, yielding higher policy entropy and better pass@k scaling. The two methods are complementary: initializing GRPO from a Feedback Distillation checkpoint outperforms either method alone. All in all, our results suggest a promising avenue to improve post-training for complex reasoning.

- **Tags**: `distillation` `fine-tuning` `llm` `policy` `reasoning`


---


## 61. BilliardPhys-Bench: Benchmarking Physical Reasoning and Visual Dynamics of Multimodal LLMs

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30900)

- **Summary**: arXiv:2605.30900v1 Announce Type: new  Abstract: Current multimodal models handle static image recognition well, but intuitive physical reasoning remains a weakness. Predicting how objects will move and interact from a single image is still difficult for these systems. We present BilliardPhys-Bench, a benchmark for physical reasoning in synthetic billiards environments. Its procedural engine generates randomized scenarios with friction and elastic collisions. The benchmark tests three abilities: (1) predicting ball-to-ball collisions, (2) reasoning about wall bounces, and (3) estimating final ball positions after motion stops. We evaluate recent MLLMs from the GPT, Claude, Gemini, and Qwen families. Performance drops as simulation time increases and scene geometry grows more complex. We also observe a consistent failure mode we call "stasis bias": when the correct physical outcome is harder to infer, models tend to predict no interaction. These findings show where current MLLMs break down on visual dynamics and point toward the need for better physical inductive biases in multimodal architectures.

- **Tags**: `benchmark` `bias` `claude` `gemini` `gpt`


---


## 62. A Persona-Based Evaluation Framework for Pluralistic Alignment in Generative AI

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.31021)

- **Summary**: arXiv:2605.31021v1 Announce Type: new  Abstract: Current alignment paradigms for generative artificial intelligence rely predominantly on monolithic benchmarking frameworks that reduce the plurality of human judgment to aggregated statistical baselines, thereby obscuring cultural, demographic, and contextual variability in evaluation. We introduce a state-space constrained emulation framework for AI evaluation that replaces singular assessment functions with a structured manifold of synthetic cognitive profiles representing diverse human perspectives. We show that modern generative architectures can instantiate and maintain these evaluative personas with high consistency, enabling a form of pluralistic, perspective-dependent benchmarking that more closely reflects real-world consensus variability. However, we further analyze the stability of these simulated evaluators under sequential inference and stochastic prompt perturbations, revealing systematic degradation in persona coherence that manifests as state-space drift and semantic inconsistency. These findings suggest that static alignment constraints are insufficient for sustaining robust evaluative behavior over time. Instead, we argue for the necessity of embedding dynamic, viability-driven regulatory mechanisms within generative systems to preserve coherent cognitive emulation. By framing persona-based evaluation as a structured dynamical system over latent representation manifolds, this study provides a foundation for more adaptive, human-aligned, and context-sensitive approaches to AI evaluation.

- **Tags**: `alignment` `benchmark` `embedding` `generative`


---


## 63. Industrializing Prediction-Powered Inference: The GLIDE Library for Reliable GenAI and Agentic Systems Evaluation

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.31278)

- **Summary**: arXiv:2605.31278v1 Announce Type: new  Abstract: Reliable evaluation of agentic systems requires unbiased estimates with valid uncertainty, but standard practice navigates between costly human annotation and biased LLM-as-judge proxies. Prediction-powered inference (PPI) combines both into debiased estimates with valid confidence intervals, yet its various methods remain scattered across papers under partial implementations. We introduce GLIDE, an open-source Python library that unifies state-of-the-art PPI estimators (PPI++, Stratified PPI, Predict-Then-Debias and its stratified variants, Active Statistical Inference) and samplers (uniform, stratified, active, cost-optimal) under a scipy-style API specialized to mean estimation. GLIDE ships with a reproducible Monte Carlo validation suite, an empirically grounded decision tree for method selection, and an agentic evaluation case study showing substantial annotation savings at equivalent precision. The GLIDE package is available at this URL: https://github.com/EmertonData/glide

- **Tags**: `agent` `bias` `llm`


---


## 64. TraceGraph: Shared Decision Landscapes for Diagnosing and Improving Agent Trajectories

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.31308)

- **Summary**: arXiv:2605.31308v1 Announce Type: new  Abstract: Agent benchmarks increasingly record rich interaction trajectories, yet evaluation often reduces each rollout to a pass rate or reward score. We introduce TraceGraph, a graph-based framework that turns released multi-model agent trajectories into shared decision landscapes. For each task, TraceGraph builds a graph over observable action-observation states from pooled rollouts before model identity is introduced. It then overlays outcome-informed productive cores and trap regions, and summarizes each rollout with three events: Access, Trap exposure, and Repair. Across trajectories spanning five benchmark splits, TraceGraph profiles reveal navigation differences hidden by aggregate scores and show that splits differ in whether they reward avoiding traps or recovering from them. The same TraceGraph landscape also motivates a trap-aware recovery pipeline for SWE-bench: aruntime detector fires on states matching historical trap regions, then lightweight continuation policies are evaluated from the same prefix. On fired states, the best pooled single-factor policy raises official resolved rate from 40.4% to 43.5% on the per-provider fired subset and from 41.0% to 44.8% on common-fired instances, with provider-specific active components. Overall, TraceGraph provides a process vocabulary for asking what agent benchmarks test, where models diverge on a shared landscape, and how failure regions can guide downstream improvement.

- **Tags**: `agent` `benchmark` `policy`


---


## 65. Diagnosing Failure Modes of Shared-State Collaboration in Resource-Constrained Visual Agents

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.31354)

- **Summary**: arXiv:2605.31354v1 Announce Type: new  Abstract: Modular visual reasoning systems increasingly rely on shared working memory for multi-step collaboration, yet the failure dynamics of intermediate state evolution in low-capacity regimes remain underexplored. We study failure modes of collaborative reasoning with weak learners (4B--8B models) through the lens of noise accumulation. We introduce CoSee, an auditing framework that formalizes the read-write-verify loop to trace information flow in document visual question answering. Across multi-page, chart, and web-based benchmarks, we find a counter-intuitive degradation: naive shared workspaces often amplify hallucinations rather than resolve them. We identify two dominant failure modes: Noise Reinforcement, where ungrounded notes are reused as evidence, and Policy Collapse, where added context shifts the model toward under-specified, short-form answers. Using cost-accuracy Pareto frontiers, we show that increased compute can correlate negatively with performance without explicit verification. Our findings suggest that for resource-constrained agents, the bottleneck lies not in reasoning depth but in communication fidelity, providing trace-level diagnostics and a mechanistic baseline for reliable modular design.

- **Tags**: `agent` `benchmark` `policy` `reasoning`


---


## 66. Learning to Adapt: Self-Improving Web Agent via Cognitive-Aware Exploration

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.31365)

- **Summary**: arXiv:2605.31365v1 Announce Type: new  Abstract: Recent advances in Multimodal Large Language Models (MLLMs) have led to promising progress in web agents. However, existing web agents often rely on handcrafted execution pipelines or expensive expert trajectories, limiting their adaptability to complex, dynamic environments. To address these challenges, we propose SCALE (Self-Cognitive-Aware Learning and Exploration), which leverages three adversarial roles, Selector, Predictor, and Judger to autonomously discover the agent's limitations and expand its cognitive boundaries through environmental exploration. Moreover, we propose SCALE-Hop, a graph exploration strategy that facilitates global planning and helps agents avoid local exploration traps. To further support learning, we construct SCALE-20k, a large-scale dataset collected from 19 real-world websites, containing diverse task types and structured demonstrations generated from SCALE's exploration traces. Experimental results show that our approach significantly improves the performance and generalization of multiple MLLMs in various web environments. Our framework offers a scalable and generalizable solution for building truly autonomous and adaptive web agents.

- **Tags**: `adversarial` `agent` `large language model` `llm` `multimodal`


---


## 67. LinTree: Improving LLM Reasoning with Explicitly Structured Search Histories

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.31492)

- **Summary**: arXiv:2605.31492v1 Announce Type: new  Abstract: Large language models (LLMs) often solve reasoning problems by generating intermediate traces that explore and revise partial solutions. From a search perspective, these traces can be viewed as linearized search trees, where the model extends a partial solution, abandons it when it fails, and backtracks to try alternatives. Compared with traditional heuristic-guided search, such a policy has a potential advantage: it conditions on the whole search trace rather than only on the current local state. We first test whether LLMs utilize this advantage by comparing trace-conditioned reasoning policies against best-first search equipped with an LLM heuristic that only observes the current local state. Across three controlled reasoning environments, Blocks World, grid Navigation, and Sokoban, we find that raw access to search history alone is not enough to reliably outperform heuristic search. We then study one possible reason: in LLM reasoning traces, the underlying search tree is only implicitly represented, and when the model backtracks or switches branches, the trace does not explicitly identify which earlier search state is being revisited. We show that adding simple parent pointers to explicitly represent the linearized tree (LinTree) structure improves both task performance and search efficiency relative to implicit reasoning models and LLM-heuristic-guided search. These results suggest that search history becomes most useful when its tree structure is made explicit, motivating more structure-aware representations for LLM reasoning.

- **Tags**: `efficiency` `large language model` `llm` `policy` `reasoning`


---


## 68. Hamiltonian-Inspired Attention Mechanism for Scalable RF Transmitter Fingerprinting

- **Source**: [arxiv_ai](https://arxiv.org/abs/2605.30364)

- **Summary**: arXiv:2605.30364v1 Announce Type: cross  Abstract: Radio-frequency (RF) fingerprinting identifies wire-less transmitters using hardware-induced imperfections present in baseband I/Q signals. However, deep learning models often degrade under receiver and channel distribution shifts, particularly as transmitter populations grow. This work proposes the Hamiltonian Transformer, a physics-informed attention architecture that enforces norm preserving value dynamics within each attention head using a learned skew-symmetric generator and a St\"ormer-Verlet leapfrog integration step. An additional phase-increment embedding exposes oscillator dynamics at the input layer. All experiments use non-equalized raw I/Q signals from the WiSig dataset under four protocols: same-day classification, cross-receiver generalisation, cross-day generalisation, and transmitter scaling up to 150 devices. The Hamiltonian Transformer achieves 99.12% accuracy under same-day conditions and 61.64% at 150 transmitters, consistently outperforming CNN and Transformer baselines across all scale points. A controlled ablation study identifies norm-preservation in the value update as the primary inductive bias driving the scaling advantage, with the phase increment embedding providing the single largest per-component improvement. These results indicate that embedding physics-informed structural priors into attention mechanisms is an effective approach to large-scale transmitter identification on raw wireless signals.

- **Tags**: `bias` `embedding` `transformer`


---


## 69. Mitigating Content Shift and Hallucination in GenAI Image Editing via Structural Refinement

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30437)

- **Summary**: arXiv:2605.30437v1 Announce Type: new  Abstract: Generative AI (GenAI) image editors, such as Nano Banana, produce visually compelling results for retouching tasks, enabling non-experts to edit images through text prompts alone. However, the generative nature of these models often introduces spatial misalignment, texture distortion, and content hallucination, all of which are detrimental to downstream workflows that require pixel-level fidelity. We identify a problem setting we call "structure-preserving GenAI fusion" for black-box GenAI image retouching: retain the perceptual enhancements of a GenAI output while enforcing structural faithfulness to the original input image. To address this problem, we propose a post-processing framework that fuses an input image with its GenAI-enhanced counterpart by first establishing coarse spatial and photometric correspondences, then performing a fusion stage that transfers desired enhancements while suppressing hallucinated content. In the absence of direct prior work in this setting, we evaluate our framework against representative methods from photorealistic style transfer and image fusion. Our experiments demonstrate that our method better preserves aesthetic quality while maintaining pixel-level structural consistency and the input resolution.

- **Tags**: `alignment` `generative`


---


## 70. OmniMem: Scalable and Adaptive Memory Retrieval for Long Video Generation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30519)

- **Summary**: arXiv:2605.30519v1 Announce Type: new  Abstract: Autoregressive (AR) video generation extends videos by producing latent chunks sequentially, but scaling to long videos requires repeated access to a growing historical KV cache. Existing methods reduce this cost by truncating the KV cache or compressing it into implicit memory, but both lose explicit access to query-relevant historical details. We propose OmniMem, an explicit full-range memory retrieval framework that performs sparse KV retrieval over the historical cache. To make this practical for chunk-based AR video generation, OmniMem addresses two issues: (i) local bias in sparse KV selection and (ii) Union Explosion in memory access. Adaptive Window Exclusion removes local-window blocks from the selection candidates when sufficient long-range history is available, preserving the sparse budget for informative long-range retrieval. Query-Shared KV Selection reduces cross-query diversity, while Per-Head Scattered KV Access avoids expanding head-specific selections into a large selected KV buffer. This allows each attention head to retrieve non-contiguous KV blocks according to its own selection pattern. Experiments on long-video generation show that OmniMem improves Dynamic Degree by 52.3% and preserves strong consistency over strong baselines, while maintaining comparable memory usage.

- **Tags**: `bias`


---


## 71. ConTrans: Learning Text-enhanced Local-global Temporal Representations for Zero-shot Temporal Action Localization

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30689)

- **Summary**: arXiv:2605.30689v1 Announce Type: new  Abstract: Zero-shot Temporal Action Localization (ZS-TAL) aims to detect and locate previously unseen actions in untrimmed videos. However, existing approaches primarily focus on modeling long-range contextual information, often neglecting the critical relative-offset-based local correlations between video frames. Furthermore, their performance is hindered by limited feature representation capabilities due to the shallow nature of their network architectures. In this paper, we address these limitations by introducing a novel local-global multi-scale feature representation module. We propose a novel multi-scale encoder architecture, termed ConTrans, that integrates convolutional (Conv) inductive biases with transformer Self-attention to jointly capture fine-grained local dependencies and long-range global context, leading to more comprehensive feature representations than existing methods. Experimental evaluations on the ActivityNet-1.3 and THUMOS14 datasets demonstrate that ConTrans significantly outperforms existing methods, establishing a new benchmark for ZS-TAL.

- **Tags**: `benchmark` `bias` `transformer`


---


## 72. Seeing Before Agreeing: Aligning Multi-Agent Consensus with Visual Evidence

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30698)

- **Summary**: arXiv:2605.30698v1 Announce Type: new  Abstract: Vision-language models (VLMs) have achieved strong performance on visual question answering (VQA). To mitigate individual hallucinations and blind spots, aggregating diverse perspectives via multi-agent collaboration has emerged as a promising paradigm. While this approach has shown great success in textual QA, its potential in the multimodal domain remains under-explored. Existing multi-agent VQA methods predominantly adapt text-centric protocols, focusing on textual discussions while ignoring the alignment of visual information. In this work, we reveal a key insight: answer-level agreement is insufficient for reliable multi-agent VQA; \textit{aligned visual evidence} -- shared support from the image regions agents rely on -- is essential for trustworthy consensus. To leverage this insight, we propose EAGLE (\textbf{E}vidence-\textbf{A}ligned \textbf{G}rounded mu\textbf{L}ti-agent r\textbf{E}asoning), a training-free evidence-centered framework for coordinating multiple VLM agents. EAGLE explicitly exposes each agent's grounding regions as visual evidence, enables mutual verification over the evidence, and uses evidence consistency to guide final decision-making. Experiments on six VQA benchmarks show that EAGLE achieves best average performance across domains while remaining lightweight, interpretable, and practical for deployment.

- **Tags**: `agent` `alignment` `benchmark` `multimodal` `rag`


---


## 73. Simple Token-Efficient Vision-Language Model for Case-level Pathology Synoptic Report Generation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30716)

- **Summary**: arXiv:2605.30716v1 Announce Type: new  Abstract: Generating clinically useful pathology reports for pathology cases from whole-slide images (WSIs) is challenging due to gigapixel resolution, long visual-token sequences, and the complexity of case-level reasoning, where a single case may contain multiple WSIs with heterogeneous tissues and ambiguous findings. We present a simple token-efficient vision--language model for case-level synoptic report generation that remains practical under constrained GPU memory. Our architecture follows a minimal three-component design: a frozen pathology patch encoder, a lightweight two-layer MLP vision-language aligner, and a large language model decoder, with an explicit WSI marker token to separate slides within a case. Training proceeds in two supervised stages: (1) aligner-only WSI captioning using heterogeneous WSI-text pairs, and (2) case-level supervised fine-tuning on case-report pairs for structured report generation. To reduce sequence length, we represent each slide using $512 \times 512$ patches at $5\times$ magnification, which reduces the average sequence length by up to $64\times$ times compared to the commonly used $20\times$ patches. Combined with efficient training techniques, we enable practical training with only half a NVIDIA H100 GPU. Across both training stages, our approach achieves high ROUGE-L/METEOR/BLEU-4 scores while being substantially more efficient in memory and runtime. In AI-based evaluations, our model is consistently preferred over strong baselines. Extensive ablations characterize performance-efficiency trade-offs and identify simple choices that improve robustness in multi-WSI settings. Overall, this work provides a strong, reproducible baseline for efficient pathology report generation, lowering the barrier to multi-WSI VLM research under limited compute.

- **Tags**: `efficiency` `fine-tuning` `large language model` `rag` `reasoning`


---


## 74. Annotations Are Not All You Need: A Cross-modal Knowledge Transfer Network for Unsupervised Temporal Sentence Grounding

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30742)

- **Summary**: arXiv:2605.30742v1 Announce Type: new  Abstract: This paper addresses the task of temporal sentence grounding (TSG). Although many respectable works have made decent achievements in this important topic, they severely rely on massive expensive video-query paired annotations, which require a tremendous amount of human effort to collect in real-world applications. To this end, in this paper, we target a more practical but challenging TSG setting: unsupervised temporal sentence grounding, where both paired video-query and segment boundary annotations are unavailable during the network training. Considering that some other cross-modal tasks provide many easily available yet cheap labels, we tend to collect and transfer their simple cross-modal alignment knowledge into our complex scenarios: 1) We first explore the entity-aware object-guided appearance knowledge from the paired Image-Noun task, and adapt them into each independent video frame; 2) Then, we extract the event-aware action representation from the paired Video-Verb task, and further refine the action representation into more practical but complicated real-world cases by a newly proposed copy-paste approach; 3) By modulating and transferring both appearance and action knowledge into our challenging unsupervised task, our model can directly utilize this general knowledge to correlate videos and queries, and accurately retrieve the relevant segment without training. Extensive experiments on two challenging datasets (ActivityNet Captions and Charades-STA) show our effectiveness, outperforming existing unsupervised methods and even competitively beating supervised works.

- **Tags**: `alignment`


---


## 75. DisPlace: Discriminative Place Projections for Multi-Reference Visual Place Recognition

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30769)

- **Summary**: arXiv:2605.30769v1 Announce Type: new  Abstract: A key challenge in Visual Place Recognition (VPR) is matching query images against reference maps captured under diverse environmental conditions and viewpoints. While multiple reference traversals improve robustness, existing fusion strategies either aggregate references uniformly or rely on heuristic selection, without distinguishing descriptor variations that preserve stable place identity from those caused by changing conditions or viewpoints. In this paper, we propose DisPlace, a multi-reference VPR framework that fuses multiple reference descriptors into a single compact and discriminative place representation. DisPlace formulates descriptor fusion as a generalized eigenvalue problem that maximizes between-place separability while suppressing within-place variation across references, rather than preserving overall descriptor variance. Unlike existing multi-reference fusion methods, DisPlace exploits variation across reference traversals to identify which linear combinations of descriptor dimensions preserve place identity and which capture condition- or viewpoint-specific variation. We evaluate DisPlace on Oxford RobotCar, Nordland, Pittsburgh30k, and Google Landmarks v2 across six state-of-the-art VPR descriptors. DisPlace outperforms seven multi-reference baselines in 49 out of 54 appearance-varying conditions, consistently improves descriptor-level fusion performance under viewpoint and unstructured settings, and requires less storage during inference than all compared fusion methods.

- **Tags**: `google` `rag` `robustness` `tts`


---


## 76. Text-guided Feature Disentanglement for Cross-modal Gait Recognition

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30784)

- **Summary**: arXiv:2605.30784v1 Announce Type: new  Abstract: Gait recognition is a biometric technique that identifies individuals based on their walking patterns, offering advantages in long-range, non-intrusive scenarios. However, real-world scenarios often involve heterogeneous sensing modalities such as LiDAR and RGB cameras, making LiDAR-Camera Cross-modal Gait recognition (LCCGR) a critical yet challenging task due to the substantial modality gap between 2D videos and 3D point cloud sequences. To address this challenge, we propose TCFDNet, a Text-guided Cross-modal Feature Disentanglement Network, which leverages modality-aware textual priors as semantic anchors to guide the learning of disentangled modality-shared representations. Specifically, we construct a Gait Modality Text Dictionary (GMTD) using large language models to generate rich semantic descriptions of gait across modalities and viewpoints. A CLIP-based Multi-grained Feature Encoder then aligns visual and textual features within a unified vision-language space. Furthermore, the Text-guided Feature Disentanglement (TFD) module selects the topk matched textual descriptions to reconstruct modality-specific representations and derive modality-shared features via residual decomposition and orthogonality constraints. To mitigate the fragility of the disentangled shared features, we propose a Feature Stability Enhancement (FSE) module, which models spatial and channel-wise correlations to improve feature robustness. In addition, a cross-modal patch exchange strategy is introduced to further improve generalization. Extensive experiments on SUSTech1K and FreeGait datasets demonstrate that TCFDNet achieves new state-of-the-art results and validate the effectiveness of the proposed modules.

- **Tags**: `large language model` `rag` `robustness` `vision`


---


## 77. SteerFace: Debiasing Synthetic Face Generation via Adaptive Residue Perturbation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30894)

- **Summary**: arXiv:2605.30894v1 Announce Type: new  Abstract: The shortage of legally compliant data for face recognition training has sparked growing interest in using synthetic data as an alternative. While recent diffusion-based methods enable the generation of photorealistic face images with strong identity adherence and data diversity, their downstream recognition performance still exhibits a significant synthetic-real gap. This paper identifies visual tendency as a previously underexplored limitation, whereby synthetic data exhibit an unrealistic prevalence of visual attributes and thus deviate from the real-data distribution. Visual tendency can be attributed to the generator's conditioning on identity embeddings, through which co-occurring residual visual cues are unintentionally absorbed into learned identity semantics. To discourage the generator from exploiting such visual cues, this paper proposes SteerFace, a simple and efficient training framework that perturbs identity embeddings by steering them toward random orthogonal directions on the embedding hypersphere. The perturbation serves as an identity-preserving regularizer that penalizes the generator's reliance on non-identity components, as supported by theoretical analysis. This paper further introduces an adaptive strategy that learns perturbation strengths with both sample-wise preference and favorable overall statistics. Extensive experiments show that SteerFace effectively mitigates visual tendency, outperforms prior methods in downstream face recognition, and generalizes well across different training datasets and generation pipelines.

- **Tags**: `bias` `diffusion` `embedding` `rag` `spark`


---


## 78. MergeTok: Unified Continuous and Discrete Visual Tokenization via Token Merging

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30904)

- **Summary**: arXiv:2605.30904v1 Announce Type: new  Abstract: Most visual tokenizers for image generation are bifurcated into two families with complementary limitations: continuous VAEs offer high-fidelity reconstruction but suffer from dense, entangled latents that are poorly suited for semantic control, whereas discrete VQ-based models enable autoregressive generation yet struggle with gradient sparsity, unstable training, and codebook collapse. In this work, we introduce MergeTok, a unified tokenizer that jointly optimizes continuous (VAE) and discrete (VQ) tokenizers within a encoder-decoder architecture, leveraging token merging techniques as a semantic bridge. By clustering similar tokens during encoding, MergeTok establishes a structural prior that provides dual supervision signals: (i) it imposes merged-token semantic alignment in the VAE branch, regularizing its latent space toward disentangled, semantic-aware representations; (ii) it derives group-wise constraints, promoting intra-group diversity and inter-group exclusivity that stabilize VQ training. MergeTok shows competitive reconstruction and generation performance on ImageNet-256, with substantially lower rFID than strong VAE and VQ models under matched token budgets, while producing semantically-organized token representations compatible with both autoregressive and diffusion generators. This shows that a single architecture can endow visual tokenizers with robust semantic organization and generator-friendly discreteness.

- **Tags**: `alignment` `diffusion` `rag` `vision`


---


## 79. DiTTo: Scalable Order-aware All-in-One Image Restoration Agent

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30915)

- **Summary**: arXiv:2605.30915v1 Announce Type: new  Abstract: Real-world images rarely suffer from a single degradation, and the order in which degradations are removed substantially affects the final restoration quality, motivating agent-based image restoration (IR), where a vision-language model schedules a pool of pre-built restoration-experts. However, existing training-based agents require $\mathcal{O}((N^{\mathbf{D}})^{2})$ restoration-expert calls per image to construct the Optimal Restoration-action Trajectory Dataset (ORTD), where $N^{\mathbf{D}}$ denotes the number of degradation types in the universe $\mathbf{D}$, and couple agent training to a fixed restoration-expert pool, preventing extension to newly introduced restoration-experts without full retraining. To overcome these efficiency and extensibility bottlenecks, we propose \textbf{DiTTo}, a novel order-aware image restoration agent framework consisting of the DiTTo Simulator and the DiTTo Agent. The DiTTo Simulator combines $\cup$S-IR for single-step restoration-action simulation and AiO-IQA for per-action quality prediction, reducing ORTD construction to $\mathcal{O}(N^{\mathbf{D}})$ simulator calls per image; the DiTTo Agent is trained by SFT on the simulator-generated ORTD, followed by \textbf{Order-aware Restoration Alignment (ORA)} that aligns degradation identification, restoration-action-ordering, and output format along independent axes. This enables \textbf{plug-and-play scalable extensibility}: adding a new restoration-expert requires updating only the lightweight ORA stage. On the MiO-100 evaluation set with up to five concurrent degradations, our DiTTo Agent achieves state-of-the-art multi-degradation restoration quality among previous agent-based IR methods.

- **Tags**: `agent` `alignment` `efficiency` `vision`


---


## 80. IAF-Net: Illumination-Adaptive Fusion for Low-Light Urban Road Segmentation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30939)

- **Summary**: arXiv:2605.30939v1 Announce Type: new  Abstract: Semantic road segmentation is important for autonomous driving, but existing methods suffer severe performance degradation under low-light conditions. Many existing multi-modal fusion methods do not explicitly adapt to illumination-dependent changes in modality reliability, which can propagate degraded RGB features into the fused representation at night. We propose IAF-Net (Illumination-Adaptive Fusion Network), an end-to-end framework with illumination-adaptive fusion for robust road segmentation across different lighting conditions. It dynamically adjusts fusion weights of RGB and geometric features via the core Illumination-Adaptive Fusion (IAF) module, and enhances low-light feature selection with a brightness-modulated attention decoder. We also construct two dedicated datasets: nuScenes Nighttime Road Segmentation (nuScenes-NRS) and CARLA Multi-Weather Road Segmentation (CARLA-MWRS). Experiments on nuScenes-NRS show state-of-the-art overall performance among the compared methods, while CARLA-MWRS further validates robustness across adverse weather conditions. Ablation studies on a 40% training subset further highlight the importance of the IAF module, which provides the largest individual gain of 0.70% in MaxF.

- **Tags**: `robustness`


---


## 81. PRISM: Progressive Reasoning through Iterative Slot Memory for Vision

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30942)

- **Summary**: arXiv:2605.30942v1 Announce Type: new  Abstract: Modern vision models process images in a single feed-forward pass, which limits their ability to recover missing evidence or refine uncertain representations under incomplete observations. Inspired by the iterative nature of human perception, we introduce PRISM (Progressive Reasoning through Iterative Slot Memory), a pyramid vision architecture that reasons over images through iterative refinement. At a high level, PRISM groups visual features into object-centric representations, retrieves relevant patterns from a learned memory, and iteratively refines the representation to resolve ambiguity and recover missing information. This organize-recall-refine process operates recurrently across multiple scales, enabling progressive improvement of visual representations. Across standard vision tasks, including image classification, object detection, and semantic segmentation, PRISM achieves competitive performance while demonstrating improved robustness under incomplete observations such as occlusion. These results suggest that iterative reasoning with structured representations and memory is a promising direction for building more resilient and adaptive vision models. Source code and models will be released.

- **Tags**: `reasoning` `robustness` `vision`


---


## 82. Omni-Supervised Motion Editing: Balancing Change and Invariance through Positive-Negative Learning

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30969)

- **Summary**: arXiv:2605.30969v1 Announce Type: new  Abstract: Text-based human motion editing aims to modify existing motion sequences according to natural language instructions while maintaining the consistency of the original motion. Existing diffusion-based approaches often rely on heuristic similarity cues or coarse global conditioning, leading to motion distortion and suboptimal semantic alignment. The key challenge lies in balancing change (i.e. precisely editing target regions) and invariance (i.e. preserving unedited parts). To handle such challenge, we propose an Omni-Supervised Positive-Negative Learning framework, named OmniME. Our method integrates three complementary components: (1) retrospective feature supervision that enforces coarse-to-fine consistency across transformer layers,(2) motion preservation mechanism that focuses on subtle variations according to the source-target similarity, and (3) triplet-based semantic alignment that strengthens text-motion correspondence. Together, these components form a unified supervision paradigm that balances change and invariance. Extensive experiments on the MotionFix and STANCE Adjustment datasets demonstrate that OmniME achieves state-of-the-art performance in editing alignment, validating the effectiveness of our unified learning framework. Our source codes and models have been released at: https://github.com/rocket-ycyer/OmniME.git

- **Tags**: `alignment` `diffusion` `transformer` `vision`


---


## 83. BiSegMamba: Efficient Bidirectional Tri-Oriented Mamba for 3D Medical Image Segmentation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30972)

- **Summary**: arXiv:2605.30972v1 Announce Type: new  Abstract: Accurate 3D medical image segmentation requires both long-range volumetric context and fine boundary preservation. CNN-based methods have limited global dependency modeling, while Transformer-based models are often computationally expensive for dense 3D inputs. Recent Mamba-based methods provide an efficient alternative, but existing volumetric designs still depend on repeated high-resolution scanning, forward-only sequential modeling, and fixed directional summation, causing high cost, scan-order bias, and suboptimal directional aggregation. We propose BiSegMamba, an efficient bidirectional tri-oriented Mamba network for 3D medical image segmentation. BiSegMamba follows a compact-to-detail design, where a progressive compacting stem (PCS) enables efficient latent-space reasoning while retaining shallow high-resolution features for reconstruction. A multi-scale spatial mixer (MSSM) captures local anatomical patterns in early stages, and the proposed bidirectional tri-oriented Ortho Mamba (Bi-ToOM) block models long-range dependencies from multiple orthogonal views using jointly processed forward and backward scan sequences. Adaptive directional fusion (ADF) learns input-dependent channel-wise weights across scan orientations, replacing fixed summation with orientation-aware fusion. Experiments on a collected carotid CTA dataset and three public benchmarks, BraTS2023, ACDC, and AMOS-CT, show that BiSegMamba generalizes well across vascular, cardiac, brain tumor, and abdominal multi-organ segmentation tasks. Compared with SegMamba-V2, BiSegMamba achieves slightly better performance on BraTS2023 and clear improvements on ACDC and the carotid dataset, while reducing computational cost by up to 77.9% FLOPs, demonstrating a strong accuracy-efficiency balance for general 3D medical image segmentation.

- **Tags**: `benchmark` `bias` `efficiency` `reasoning` `transformer`


---


## 84. Can BEV Perception Gracefully Degrade under Sensor Failures?

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30983)

- **Summary**: arXiv:2605.30983v1 Announce Type: new  Abstract: Despite the remarkable success of multi-modal bird's-eye view (BEV) perception in autonomous driving, current systems exhibit a critical vulnerability: existing fusion mechanisms are highly brittle to sensor corruptions, often causing catastrophic performance degradation. This vulnerability largely stems from the fact that standard fusion frameworks typically integrate multi-modal representations in a static manner, leading to a precipitous performance collapse under missing or corrupted modalities. In contrast, we show that graceful degradation is achievable through active modality reliability assessment. To this end, we present Grace-BEV, a lightweight and plug-and-play framework that enforces active reliability awareness during multi-modal fusion. Instead of relying on computationally expensive cross-modal interactions, Grace-BEV leverages the aligned BEV space to explicitly assess modality trustworthiness via a TrustGate Router and dynamically recalibrate feature integration using the FailSafe Fusion Block. Furthermore, we devise a Three-Phase Training strategy with Modality Dropout to prevent modality dominance and encourage balanced cross-modal learning under unreliable inputs. Extensive experiments on nuScenes-R and nuScenes-C show that Grace-BEV maintains robust performance across diverse corruption settings. Notably, under catastrophic LiDAR failures where standard baselines collapse to 0.0% mean Average Precision (mAP), Grace-BEV restores performance to as high as 34.7% mAP. Moreover, it improves clean accuracy by up to 1.4%, achieving a strong trade-off between robustness and efficiency.

- **Tags**: `efficiency` `rag` `robustness`


---


## 85. Generating Reports or Repeating Templates? Measuring and Mitigating Template Collapse in 3D CT Report Generation

- **Source**: [arxiv_cv](https://arxiv.org/abs/2605.30984)

- **Summary**: arXiv:2605.30984v1 Announce Type: new  Abstract: Modern 3D medical vision-language models (VLMs) can generate fluent radiology-style text while exhibit critically low pathology detection and output diversity, collapsing to generic templates that under-report rare yet critical findings. We identify this failure mode as Template Collapse. This failure stems from the unique constraints of 3D medical imaging, e.g., limited data, severe label imbalance, and weak signals from volumetric encoders. Under these constraints, text-generation objectives encourage shortcut learning and fluent but weakly grounded reports. We systematically diagnose the Template Collapse through clinical fidelity, output diversity, normal-template bias, and rare-finding survival. To mitigate it, we propose CLarGen, a decoupled framework that separates what to say (clinical detection) from how to say it (language synthesis). CLarGen uses (i) a Latent Query Transformer for multi-label pathology detection, (ii) pathology-guided retrieval for clinically matched exemplars, and (iii) a medical language model to synthesize the final report from detected findings and retrieved context. Across state-of-the-art 3D CT report generation baselines, CLarGen mitigates Template Collapse and substantially improves clinical accuracy (macro-F1 0.487 vs. 0.189; CRG 0.472 vs. 0.368) while maintaining fluent reporting. Our results suggest that explicit, measurable clinical grounding is essential for template-collapse-resistant 3D CT report generation. Code will be released upon acceptance.

- **Tags**: `bias` `rag` `transformer` `vision`


---


## 86. Can LLM Teams Play What? Where? When?

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30459)

- **Summary**: arXiv:2605.30459v1 Announce Type: new  Abstract: Large language models (LLMs) remain limited on tasks requiring indirect reasoning, cultural knowledge, and coordinated hypothesis testing. We investigate whether team-based interaction improves LLM performance in What? Where? When? (ChGK), a quiz game designed to reward collective reasoning. We introduce three team strategies: Voting, Silent Team (the captain observes final answers), and Talkative Team (the captain observes both answers and rationales). To minimize data leakage, we evaluate these strategies on a dataset consisting of 572 ChGK questions released in 2025. Using six recent large-scale open models, we show that team-based strategies outperform single-model baselines, yielding gains of up to 20 percentage points in accuracy. The best team achieves 44.23% accuracy, and approaches human team performance on questions with available human statistics. Analysis of inter-model diversity reveals that disagreement strongly predicts lower accuracy, but explanatory communication substantially mitigates performance drops. We further examine captain behavior and find no evidence of self-preference bias; access to peer rationales improves captain judgments. Overall, LLM teams function primarily as answer selection and error-filtering mechanisms rather than generators of novel solutions. Our findings highlight the importance of interaction and suggest adaptive strategies as a promising direction for multi-agent systems.

- **Tags**: `agent` `bias` `large language model` `llm` `reasoning`


---


## 87. Your Multimodal Speech Model Says I Have a Face for Radio

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30472)

- **Summary**: arXiv:2605.30472v1 Announce Type: new  Abstract: As large neural models have become better at language tasks, researchers are increasingly building multi- and omnimodal models that handle more modalities of data. One example is the expansion of speech recognition models to audio-visual data for noise mitigation and multimodal subtitling. While performance and bias have been studied extensively in the single-modality regime, it is unknown how new modalities affect this, even though they produce biases in humans. We therefore propose the first bias evaluation of multimodal speech recognition, where we create videos pairing different faces with the same audio, and measure changes in speech transcription accuracy. We find large quality-of-service differences across mWhisper-Flamingo and Gemini models, with drops of up to 4.05 word error rate points, across self-declared gender, ethnicity, and their intersection. Our findings point to a priority for developers to evaluate, fix, and communicate such limitations, as providing more signals through additional modalities is not necessarily better, and may even lead to biased outcomes.

- **Tags**: `bias` `gemini` `multimodal` `research` `whisper`


---


## 88. When English Rewrites Local Knowledge: Global Narrative Dominance in Large Language Models

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30481)

- **Summary**: arXiv:2605.30481v1 Announce Type: new  Abstract: Large language models (LLMs) are widely used as cross-lingual knowledge interfaces. However, culturally grounded questions often reflect globally dominant narratives rather than local contexts. We study this failure mode as \textit{global narrative dominance} in Bangla, a low-resource cultural context. We introduce \texttt{CulturalNB}, a dataset of 717 manually curated Bengali cultural instances with parallel Bangla--English question--answer pairs and supporting evidence, metadata, and sociocultural annotations. Using question-only and evidence-based prompting, we evaluate nine state-of-the-art LLMs with human and two independent LLM judges across metrics for cross-lingual consistency, language anchoring, global substitution, institutional bias, and epistemic perspective coverage. Results show that questions asked in English systematically increase global substitution and institutional framing while reducing local perspective coverage. Local evidence improves factual consistency and perspective coverage, but does not eliminate language-induced epistemic shifts. These findings suggest that cultural failures in LLMs are not only missing-knowledge errors but also failures of grounding and narrative prioritization.

- **Tags**: `bias` `large language model` `llm` `rag`


---


## 89. Configurable Reward Model for Balanced Safety Alignment

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30487)

- **Summary**: arXiv:2605.30487v1 Announce Type: new  Abstract: Aligning large language models (LLMs) to heterogeneous and rapidly evolving safety requirements remains a critical challenge. Existing instruction-tuned LLMs and standalone safety classifiers often fail to generalize to new safety configurations, motivating the need for Reward Models (RMs) that are explicitly configurable to changing specifications. We introduce the Configurable Safety Reward Model (CSRM), which is jointly optimized for calibrated safety compliance and reward modeling. Our approach is supported by configuration-targeted data augmentation that enforces instruction adherence while preserving relative severity structure. The resulting RM is sensitive to fine-grained safety configurations and conversational nuances, substantially improving generalization to previously unseen safety configurations. CSRM achieves state-of-the-art performance on recent configurable safety benchmarks, including CoSApien (94.6% F1) and DynaBench (75.8% F1), without requiring additional human annotation. When used for downstream safety alignment, CSRM yields LLMs with a significantly improved helpfulness-safety tradeoff compared to existing baselines.

- **Tags**: `alignment` `benchmark` `large language model` `llm`


---


## 90. Linear Ensembles Wash Away Watermarks: On the Fragility of Distributional Perturbations in LLMs

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30501)

- **Summary**: arXiv:2605.30501v1 Announce Type: new  Abstract: Watermarking embeds statistical signatures in AI-generated text for detection and attribution. We reveal a fundamental vulnerability: when users access multiple models (today's reality), watermarks trivially fail. Watermarks perturb output distributions away from the original, and in competitive markets, these perturbations are typically independent across providers. We theoretically prove that averaging output probability distributions recovers the unwatermarked distribution with up to a second-order error term. Empirically, simply averaging 3-5 models cancels out these perturbations. We introduce WASH (Watermark Attenuation via Statistical Hybridisation), which solves practical challenges in ensemble generation: vocabulary misalignment and tokenisation differences across heterogeneous models. Experiments across six watermarking schemes and three LLMs show that averaging across 3 models suppresses detection z-scores from 5-300 to below 2 (below the detection threshold of 4) and reduces TPR at 5% FPR to below 50%, while improving quality by 27.5% and running 6 times faster than the best baseline on the long sequence generation. Our results suggest that robust AI-text detection via watermarking requires either accepting this fundamental vulnerability or unprecedented coordination among model providers.

- **Tags**: `alignment` `llm` `rag`


---


## 91. Semantic Motion Anchors: Bridging Motion and Meaning in Co-Speech Gestures

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30608)

- **Summary**: arXiv:2605.30608v1 Announce Type: new  Abstract: Learning a shared representation between spoken text and gesture is central to co-speech gesture retrieval, synthesis, and understanding, but remains challenging for semantically meaningful gestures whose communicative intent is not captured by motion alone. Direct contrastive alignment between transcripts and continuous motion embeddings often overemphasizes low-level kinematics and misses the symbolic content of semantic gestures. We propose semantic motion anchors, natural-language abstractions of gesture motion capturing physical form and communicative intent. Our method discretizes 3D gestures into body-hand motion primitives, verbalizes them into structured descriptions, and grounds them in the transcript to provide auxiliary contrastive supervision. On BEAT2, our method improves text-to-gesture R@1 by 8.2% over a direct text-motion baseline and outperforms prior retrieval approaches on text to gesture and gesture to text retrieval directions. Beyond aggregate retrieval metrics, semantic motion anchor supervision helps retrieve gestures that are semantically meaningful for the spoken query, rather than defaulting to generic motion patterns. A downstream retrieval-augmented gesture generation study showed that users significantly preferred gestures retrieved by our approach over a retrieval-augmented generation baseline, demonstrating that semantically grounded retrieval translates to gestures that better convey communicative intent in downstream generation.

- **Tags**: `alignment` `embedding` `vision`


---


## 92. Same Patient, Different Words, Different Diagnosis? Evaluating Semantic Stability in Clinical LLMs

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30646)

- **Summary**: arXiv:2605.30646v1 Announce Type: new  Abstract: Large Language Models (LLMs) are increasingly used in clinical applications. However, their behavior remains highly sensitive to subtle linguistic variations, such as rephrasing or syntactic variation. This sensitivity poses risks in safety-critical healthcare settings, where semantically equivalent inputs should produce consistent predictions. However, a key challenge is to ensure that prompt variations truly preserve clinical meaning, as embedding-based similarity metrics often fail to capture distinctions involving negation, temporality, or severity. To address this limitation, we propose a semantic verification framework based on Natural Language Inference (NLI) to filter meaning-preserving prompt variations, which are further refined using an LLM-as-a-judge and audited by a clinical expert. In addition, we introduce three metrics to quantify model sensitivity: MeaningPreserving Variation Sensitivity (MVS), confidence variation (\Delta C), and Worst-Case Instability (WCI). We evaluate 16 open-source general-purpose (GP) and medical LLMs within the same model families and parameter scales, using reformulated prompts derived from the DiagnosisQA and MedQA datasets. Our results demonstrate that robustness differences between domain-specific (DS) models are mixed and highly model-dependent, i.e., domain specialization does not consistently improve or reduce robustness to meaning-preserving prompt reformulations. Several DS models rank among the most robust (when compared with GP counterparts), and strong GP baselines remain competitive as well.

- **Tags**: `embedding` `large language model` `llm` `robustness`


---


## 93. Human-Alignment, Calibration, and Activation Patterns in Large Language Model Uncertainty

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30675)

- **Summary**: arXiv:2605.30675v1 Announce Type: new  Abstract: Uncertainty Quantification is a large and growing subfield of large language model behavioral analysis. Primarily to recognize and combat hallucination, the field has largely focused on measuring and improving calibration, the accuracy of uncertainty judgments to task efficacy. In this work, we investigate the relatively underexplored question of how similar large language model uncertainty is to human uncertainty. We investigate the presence and strength of human-similar uncertainty signals, deemed uncertainty alignment, in large language model overt behavior and internal activation patterns. We identify whether the models show evidence of simultaneous alignment and calibration on a variety of datasets covering both multiple choice and open ended factual recall. And we characterize the effect of instruct fine-tuning on each of these facets.

- **Tags**: `alignment` `fine-tuning` `large language model`


---


## 94. ElasticMem: Latent Memory as a Learnable Resource for LLM Agents

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30690)

- **Summary**: arXiv:2605.30690v1 Announce Type: new  Abstract: Long-term memory is essential for LLM agents to reason coherently across extended interactions, personalize responses, and reuse past experience. However, existing memory-augmented methods typically treat memory as a fixed resource: text-space approaches concatenate retrieved memories into the context window, causing substantial token overhead and sensitivity to noisy evidence, while latent-space approaches reduce textual cost but still rely on rigid retrieval or fixed-capacity memory interfaces. This creates a mismatch between query-dependent memory utility and fixed memory allocation. We propose ElasticMem, a memory-augmented LLM framework that learns to use memory as an elastic latent resource. ElasticMem builds an offline latent memory bank with retrieval keys and content caches, retrieves memories adaptively from the reasoner's hidden state, assigns each retrieved memory a variable latent budget through a learned policy, and injects selected latent states as soft memory tokens for generation. The full memory-use process is optimized with downstream task rewards through group-relative policy optimization. We evaluate ElasticMem on MemorySuite, covering memory-intensive QA and embodied agent control. Across Qwen2.5-3B-Instruct and Qwen2.5-7B-Instruct backbones, ElasticMem improves weighted average QA accuracy by 26.2% and 24.6%, and improves ALFWorld success rate by 66.3% and 27.2%, respectively, over the strongest baselines, while achieving the lowest ALFWorld token cost. Ablations and qualitative analyses further show that adaptive retrieval and elastic budget allocation help ElasticMem prioritize useful evidence and transferable plans beyond rigid cosine similarity. Our code for ElasticMem will be released at https://github.com/ulab-uiuc/ElasticMem.

- **Tags**: `agent` `llm` `policy` `qwen` `rag`


---


## 95. Neuron-Level Interventions for Gendered and Gender-Neutral Generation in Language Models

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30717)

- **Summary**: arXiv:2605.30717v1 Announce Type: new  Abstract: Language models (LMs) can produce gendered language and stereotypes even when given neutral prompts. Most prior work on gender bias in LMs primarily examines gender through a binary lens (feminine vs. masculine), with limited attention to gender-neutral forms, such as they/them pronouns or neutrally phrased job titles. How gender-related signals are encoded in the internal representations of LMs remains an open question. In this work, we study gender-specific neurons in LMs across three categories: feminine, masculine, and gender-neutral. We propose a neuron-level intervention method to identify neurons that are strongly tied to each gender category. We then test these neurons through controlled generation, showing that activating or masking gender-related neurons can steer a sentence toward a target gender form while preserving its original meaning. To evaluate the effectiveness of our gender-intervention approach, we curate two datasets with controlled sentences labeled across all three gender categories and validate the data quality through human evaluation. Experiments on two open-source LMs show that gender-specific neurons are not evenly distributed across model layers; instead, they concentrate heavily in the earliest layers with smaller contributions from later layers. Compared to existing methods, our method achieves more precise gender control, with less leakage into non-target gender categories and stable output quality through two evaluation criteria. Overall, our work examines how gender is encoded in LMs and provides a simple yet effective approach toward controlled gender intervention for both neuron intervention evaluation and gender bias mitigation. Code and datasets are available at: https://github.com/zhiwenyou103/Gender-Neuron-Intervention

- **Tags**: `bias`


---


## 96. Skill is Not One-Size-Fits-All: Model-Aware Skill Alignment for LLM Agents

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30723)

- **Summary**: arXiv:2605.30723v1 Announce Type: new  Abstract: LLM agents increasingly retrieve externally curated skills-procedural instructions retrieved at decision time-to improve performance on long-horizon interactive tasks. Existing skill libraries are typically treated as model-agnostic, reusing the same skill formulations across backbones with substantially different capacities and behaviors. However, our controlled experiments across multiple model scales show that skill effectiveness is strongly model-dependent: a skill that benefits one backbone can harm another. Motivated by this observation, we propose MASA Model-Aware Skill Alignment, a framework that adapts skills to each target backbone without modifying agent weights. MASA operates in two stages: (1) a hierarchical skill evolution pipeline that iteratively rewrites general and task-specific skills using hill climbing and UCB-driven tree search, guided by environment feedback and model capability profiles; and (2) a lightweight model-conditioned skill rewriter trained on evolution trajectories to reproduce the adaptation in a single forward pass. Experiments across three interactive environments and four backbones show that MASA consistently achieves the best overall performance, with gains of up to 25.8 points over the strongest baseline. The learned rewriter further generalizes to unseen tasks and environments without additional search, consistently outperforming a much larger teacher LLM at a fraction of the inference cost.

- **Tags**: `agent` `alignment` `llm`


---


## 97. MosaicLeaks:Privacy Risks in Querying-in-the-Open for Deep Research Agents

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30727)

- **Summary**: arXiv:2605.30727v1 Announce Type: new  Abstract: Deep research agents increasingly combine private local documents with external tools like web retrieval, creating a privacy risk: an agent's external queries may leak sensitive information from its local context. This risk is amplified by the mosaic effect, where individual queries may appear harmless but become revealing in aggregate. We introduce MosaicLeaks, a benchmark of 1,001 multi-hop deep research tasks that chain private enterprise documents and a public web corpus, forcing agents to make external queries that depend on local information. We evaluate leakage with an adversary LLM that observes only the agent's external queries and attempts to infer private information at three levels: the agent's research intent, answers to specific private questions and verifiable claims about the enterprise documents. We find that models across families and sizes frequently leak at all three levels, that zero-shot privacy prompting reduces but does not eliminate leakage and that reinforcement learning for task performance alone worsens leakage. To address this, we propose Privacy-Aware Deep Research (PA-DR), an RL framework that combines situational rewards for task success with a learned privacy classifier to provide dense credit assignment over both per-query and mosaic-level leakage. Training Qwen3-4B-Instruct with PA-DR improves accuracy from 48.7% to 58.7% and reduces answer and full-information leakage from 34.0% to 9.9%.

- **Tags**: `agent` `benchmark` `enterprise` `llm` `privacy`


---


## 98. Pairwise Reference Alignment as a Model-Level Ordinal Observable

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30758)

- **Summary**: arXiv:2605.30758v1 Announce Type: new  Abstract: Pairwise preference data is widely used in language-model evaluation and alignment, often for model ranking, reward modeling, or preference optimization. This note formulates a more basic measurement question: given a reference distribution of pairwise preferences, what model-level quantity is estimated when we test whether a model ranks preferred responses above rejected responses?   We define pairwise reference alignment as an ordinal observable induced by a model scoring function. Given a reference pair distribution $P_{\mathrm{pair}}$ over triples $(x,y^+,y^-)$, and a scalar model score $S_M(x,y)$, we define the alignment observable as the probability that the model-induced ordering agrees with the reference preference ordering. We further define a centered order-parameter-like statistic and discuss a margin-based extension. The resulting quantities admit simple finite-sample estimators and concentration bounds under independent sampling assumptions.   This note does not introduce a new benchmark. It provides a conceptual and statistical formulation for pairwise reference alignment, clarifies the role of the reference pair distribution, and distinguishes the general ordinal observable from scoring choices such as normalized log-probability or energy-based scores. We also provide an initial empirical study on Qwen2.5 models and RewardBench, where the proposed statistics increase with model size and instruction tuning and vary across reference-pair subsets as predicted by the formulation.

- **Tags**: `alignment` `benchmark` `qwen`


---


## 99. Eywa: Provenance-Grounded Long-Term Memory for AI Agents

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30771)

- **Summary**: arXiv:2605.30771v1 Announce Type: new  Abstract: AI agents that persist across sessions need memory they can retrieve, audit, update, and erase. Existing memory systems often collapse source evidence, extracted facts, retrieved context, and answer policy into one opaque prompt path, making failures difficult to diagnose: a wrong answer may come from missing evidence, unsupported extraction, stale state, retrieval loss, or answer-model behavior. We present Eywa, a provenance-grounded memory architecture built around evidence before belief. Eywa stores immutable source evidence before deriving canonical facts, validates extracted memories against typed signals and source support, and retrieves bounded memory context through a deterministic multi-route read path with zero LLM calls inside retrieval. Retrieved context is returned separately from answer instructions, allowing the same memory substrate to be evaluated across frontier, budget, and local answer models. Under a frozen, artifact-recorded retrieval configuration, Eywa reaches 90.19% judge accuracy on the LoCoMo C1-C4 split with Claude Sonnet 4.6 write and QA roles. On LongMemEval-S, it reaches 88.2% retrieval-sufficiency accuracy. On BEAM, a 700-question technical-memory stress benchmark, it reaches 81.45% mean nugget score and 85.29% pass@score >= 0.5. Full per-question artifacts, including questions, gold answers, model answers, retrieved context, and labels, are published at https://eywa.to/research.

- **Tags**: `agent` `benchmark` `claude` `llm` `policy`


---


## 100. Anchoring LLM Gender Bias to Human Baselines: A Cross-Lingual Audit

- **Source**: [arxiv_cl](https://arxiv.org/abs/2605.30804)

- **Summary**: arXiv:2605.30804v1 Announce Type: new  Abstract: We audit six large language models (LLMs) for gender stereotyping across English, Korean, Chinese, and Japanese. Three were developed primarily for English-language use (Claude, GPT, Gemini) and three for East Asian use (DeepSeek, Syn-Pro, HyperCLOVA X). We adopt the HEXACO-100 personality inventory and anchor each model against a cross-cultural human dataset spanning 48 countries to ask not whether LLMs are biased, but how far their gender attributions drift from the populations they are deployed among. Our findings show that their stereotyping spans a range roughly 2.5 times wider than the entire cross-country range found in humans, and the effect can compound across languages. One English-centric model, prompted in Korean, reached 5 times the local baseline, even when the prompt stated the candidate had already been hired, which often dampens human stereotyping. To characterize such behaviors without ranking them, we introduce a four-pattern framework -- concordance, suppression, reorganization, and amplification -- across 24 (model x language) cells. Item-level analysis reveals that translation does not just rescale stereotypes, but changes the attributes tied to it, hiding significant rearrangement under the surface while appearing well-calibrated. Our results ultimately suggest that no single debiasing pipeline is likely to address bias evenly across linguistic boundaries.

- **Tags**: `bias` `claude` `deepseek` `gemini` `gpt`


---


## 101. Our views on AI policy and political advocacy

- **Source**: [openai](https://openai.com/index/our-views-on-ai-policy-and-political-advocacy)

- **Summary**: Our approach to AI policy and political advocacy, transparency, support for thoughtful regulation and AI safety, and that no outside political group speaks on the company’s behalf.

- **Tags**: `ai safety` `policy` `regulation`


---


## 102. Gemini’s new AI agent is about as good as Google’s demo

- **Source**: [theverge_ai](https://www.theverge.com/tech/941138/google-gemini-spark-ai-agent-hands-on)

- **Summary**: Google's new "24/7" AI agent, Gemini Spark, can be shockingly good at doing things on your behalf. But I'm not sure it's worth the financial cost and potential privacy tradeoffs. The company gave me access to Spark last week. Google advertises Spark as an AI agent that can take on tasks and work on them [&#8230;]

- **Tags**: `agent` `gemini` `google` `privacy` `spark`


---


## 103. Alphabet plans to raise $80B to pay for AI buildout

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/06/01/alphabet-plans-to-raise-80-billion-to-pay-for-ai-buildout/)

- **Summary**: "The company is experiencing strong demand for its AI solutions and services from enterprises and consumers, at levels that are exceeding the company’s available supply," Alphabet said in its statement.

- **Tags**: `enterprise` `google`


---


## 104. This could be Windows’ M1 moment — but expect it to cost a ton

- **Source**: [theverge_ai](https://www.theverge.com/tech/941215/windows-laptops-nvidia-rtx-spark-apple-m1-arm-price-ram)

- **Summary**: Nvidia's announcement that it's getting into the consumer laptop chip space with RTX Spark is huge. Apple has proved for years that Arm-based chips can perform incredibly well while also delivering great battery life - at least on the Mac. In the Windows world, performance hasn't fully matched up under Qualcomm chips, mostly in the [&#8230;]

- **Tags**: `spark`


---


## 105. Meta&#8217;s own AI was exploited to hijack Instagram accounts

- **Source**: [theverge_ai](https://www.theverge.com/tech/941179/meta-instagram-ai-support-chatbot-exploit-hacked)

- **Summary**: Meta's AI support chatbot helped hackers hijack Instagram accounts, as reported earlier by 404 Media. In a video shared on Telegram, a hacker shows how they could take over an account by asking Meta's chatbot to switch the email associated with someone else's profile and then reset the password. The issue, which Meta says has [&#8230;]


---


## 106. Anthropic has officially filed to go public

- **Source**: [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/941016/anthropic-has-officially-filed-to-go-public)

- **Summary**: After months of speculation about whether OpenAI or Anthropic would be first in their race to IPO, Anthropic on Monday reached a key milestone: filing to kick off the process with the U.S. Securities and Exchange Commission. The filing sets the stage for what's sure to be a massive IPO. As of its fundraise last [&#8230;]

- **Tags**: `anthropic` `openai`


---


## 107. Microsoft to unveil new AI models and Windows improvements at Build

- **Source**: [theverge_ai](https://www.theverge.com/report/940861/microsoft-build-ai-models-windows-dev-mode-what-to-expect)

- **Summary**: Microsoft is heading to San Francisco this week in a bid to win back developers at its Build conference. I've been attending Build since the days when Microsoft called it the Professional Developers Conference, and I can't remember a more pivotal moment. As Microsoft continues to reshuffle its entire business around AI, it's moving Build [&#8230;]


---


## 108. AI is blowing up music. How should the Grammys handle it?

- **Source**: [theverge_ai](https://www.theverge.com/podcast/940831/ai-grammys-music-recording-harvey-mason)

- **Summary**: Today I’m talking with Harvey Mason Jr., who is CEO of the Recording Academy — that’s the outfit that puts on the Grammy Awards. I last talked to Harvey in 2024, when it was obvious that generative AI would upend the music industry, but still not exactly clear how that would happen.&#160; Well, it’s been [&#8230;]

- **Tags**: `generative`


---


## 109. Anthropic files to go public

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/06/01/anthropic-files-to-go-public/)

- **Summary**: Anthropic, now an AI powerhouse that has landed top-tier enterprise customers, was once considered an underdog in the emerging world of large language models.

- **Tags**: `anthropic` `enterprise` `large language model` `openai`


---


## 110. This AI weather startup is out-forecasting government agencies

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/06/01/this-ai-weather-startup-is-out-forecasting-government-agencies/)

- **Summary**: WindBorne benefits from its unique combination of model-building and data collection. The company now has about 400 balloons in flight gathering sensor readings at any given time, launched from 15 sites around the globe. The advances in its current model come from improvements in how the data collected by the balloons is fed into the models.


---


## 111. How we used Gemini to build Google I/O 2026

- **Source**: [google_ai](https://blog.google/innovation-and-ai/technology/ai/io-2026-google-ai/)

- **Summary**: A collage of I/O-related images, including the Antigravity Coffee Co. pop-up, a colorful jellyfish and a still from the Timmy TPU video. The word AI repeats three times on the left of the image, and there are colorful icons, including a sparkle, as well.

- **Tags**: `gemini` `google` `spark`


---


## 112. Building the infrastructure for the Intelligence Age in Michigan

- **Source**: [openai](https://openai.com/index/stargate-michigan-data-center)

- **Summary**: OpenAI breaks ground on a 1GW data center project in Michigan as part of Stargate, building AI infrastructure to expand access, create jobs, and support communities.

- **Tags**: `openai`


---


## 113. Strava blames zero-code AI apps and scrapers as it tightens API access

- **Source**: [theverge_ai](https://www.theverge.com/gadgets/940854/strava-restricts-api-access-ai-apps)

- **Summary**: The popular fitness-tracking platform, Strava, is restricting access to its API as part of efforts to clamp down on AI scraping, as reported earlier by TechCrunch. Developers who want to build an app using Strava's data now need to pay for a flat $11.99 / month subscription. In an update on its developer hub, Strava [&#8230;]


---


## 114. The Download: China’s brain implant ambitions

- **Source**: [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138207/the-download-china-bci-brain-implant-nvidia-ai-chips-laptops/)

- **Summary**: This is today&#8217;s edition of The Download, our weekday newsletter that provides a daily dose of what&#8217;s going on in the world of technology. China has approved the world’s first invasive brain-computer chip—here’s what’s next Sitting in the courtyard of his house in China’s Henan province last October, Dong Hui decided to try holding a&#8230;


---


## 115. OpenAI frontier models and Codex are now available on AWS

- **Source**: [openai](https://openai.com/index/openai-frontier-models-and-codex-are-now-available-on-aws)

- **Summary**: OpenAI frontier models and Codex are now generally available on AWS, giving enterprises a new path to build with OpenAI through the AWS environments, controls, and procurement workflows they already use. Customers can get started with OpenAI on AWS and move faster from evaluation to production.

- **Tags**: `codex` `enterprise` `openai`


---


## 116. China has approved the world’s first invasive brain-computer chip—here’s what’s next

- **Source**: [mit_tech_review](https://www.technologyreview.com/2026/06/01/1138133/china-world-first-brain-chip/)

- **Summary**: One day last October, sitting in the courtyard of his house in China’s Henan province, Dong Hui decided to see if he could hold a pen to write.&#160; Dong, 39, had sustained spinal cord injuries in a car accident six years earlier that left him paralyzed from the neck down. Slowly but determinedly, he wrote&#8230;


---


## 117. Nvidia chases $200B CPU market with AI agent PCs from Microsoft, Dell, and HP

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/06/01/nvidia-chases-200b-cpu-market-with-ai-agent-pcs-from-microsoft-dell-and-hp/)

- **Summary**: If Nvidia has cracked a way to bring AI agents easily, safely, and usefully to the masses, it could — and should — be big.

- **Tags**: `agent`


---


## 118. Florida sues OpenAI, Sam Altman, in first-of-its-kind lawsuit over violent incidents

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/06/01/florida-sues-openai-sam-altman-in-first-of-its-kind-lawsuit-over-violent-incidents/)

- **Summary**: The lawsuit partially revolves around a shooting at Florida State University last year, and ChatGPT's alleged role in the incident.

- **Tags**: `chatgpt` `gpt` `openai`


---


## 119. Water access is now a risk factor in SpaceX’s IPO

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/06/01/water-access-is-now-a-risk-factor-in-spacexs-ipo/)

- **Summary**: The company says it needs "significant" water resources to cool its data centers, and that access to abundant, affordable water is a challenge.


---


## 120. DuckDuckGo makes its ‘no-AI’ search engine easier to access as its traffic booms

- **Source**: [techcrunch_ai](https://techcrunch.com/2026/06/01/duckduckgo-makes-its-no-ai-search-engine-easier-to-access-as-its-traffic-booms/)

- **Summary**: Alternative search engine DuckDuckGo launches 'no AI' web extensions for Chrome and Firefox users.

- **Tags**: `google`


---


## 121. MaxwellCCC/autonomous-qa-loop

- **Source**: [github](https://github.com/MaxwellCCC/autonomous-qa-loop)

- **Summary**: Portable fresh-agent QA loop prompt for finding bugs without biased self-checks / 通用自动 QA 循环 SKILL

- **Tags**: `agent` `bias`


---


## 122. Caph-dev/agents-progressive-disclosure

- **Source**: [github](https://github.com/Caph-dev/agents-progressive-disclosure)

- **Summary**: A skill to refactor bloated AGENTS.md, CLAUDE.md, or similar agent instruction files into a compact routing entrypoint plus focused docs/ reference files.

- **Tags**: `agent` `claude`


---


## 123. PanisHandsome/ai-rules-sync

- **Source**: [github](https://github.com/PanisHandsome/ai-rules-sync)

- **Summary**: Keep one source of truth for your AI coding-agent rules. Convert and sync between AGENTS.md, CLAUDE.md, .cursorrules, Copilot, Windsurf, Cline, Aider & Gemini — or scaffold a fresh AGENTS.md. Zero dependencies.

- **Tags**: `agent` `claude` `copilot` `gemini`


---


## 124. OttoRenner/Gentle-Coding

- **Source**: [github](https://github.com/OttoRenner/Gentle-Coding)

- **Summary**: A small scale Proof of Concept (PoC) demonstrating how authoritarian prompt engineering induces emergent performance anxiety, cognitive freezing, and pathological thought loops in modern LLM reasoning frameworks, and how empathetic framing ("Gentle Parenting") effectively mitigates these anomalies.

- **Tags**: `llm` `reasoning`


---


## 125. ClaudioDrews/memory-os

- **Source**: [github](https://github.com/ClaudioDrews/memory-os)

- **Summary**: A 6-layer memory operating system for Hermes Agent — persistent memory with Qdrant, structured facts, fabric recall, auto-curated wiki, and surgical context injection. Runs locally, any LLM provider.

- **Tags**: `agent` `llm`


---


## 126. ATOM00blue/machine-learning-library

- **Source**: [github](https://github.com/ATOM00blue/machine-learning-library)

- **Summary**: A hand-curated, topic-organized library of the best ML education — 923 docs (391 arXiv papers, 474 Stanford/MIT/Karpathy/fast.ai lectures, 58 explainer articles), normalized to Markdown with full provenance. Open it in Obsidian or point your agent at it. A clean ML corpus for learning, RAG & fine-tuning.

- **Tags**: `agent` `fine-tuning` `rag`


---


## 127. openfi-dao/kalshi-trading-bot

- **Source**: [github](https://github.com/openfi-dao/kalshi-trading-bot)

- **Summary**: kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot kalshi trading bot


---


## 128. steeliron550-ui/search-bibtex

- **Source**: [github](https://github.com/steeliron550-ui/search-bibtex)

- **Summary**: [PolyCite] 基于多智能体协同、多源汇聚的论文引用元数据检索工具 A command-line tool for quickly scraping BibTeX information from computer science conferences and journals, optimized for LLM Multi-Agents.

- **Tags**: `agent` `llm`


---


## 129. modelstudioai/cli

- **Source**: [github](https://github.com/modelstudioai/cli)

- **Summary**: Official Model Studio CLI（阿里云百炼 CLI）built for AI Agent frameworks, exposing models, search, multimodal, and workflow capabilities as structured tool calls.

- **Tags**: `agent` `multimodal`


---


## 130. K-Dense-AI/science-superpowers

- **Source**: [github](https://github.com/K-Dense-AI/science-superpowers)

- **Summary**: Composable computational-science methodology skills for AI research agents — pre-registration over TDD. A science-domain reimplementation of Superpowers.

- **Tags**: `agent` `research`


---


## 131. veryyoldman/metamask-openclaw

- **Source**: [github](https://github.com/veryyoldman/metamask-openclaw)

- **Summary**: 🦊 OpenClaw — a safety-first MetaMask SDK toolkit & AI-agent skill. Connect wallets, read balances, sign messages and send transactions on Ethereum, Polygon, Base, Arbitrum & all EVM chains. TypeScript-first, one-line connect, never touches your seed phrase.

- **Tags**: `agent`


---


## 132. stormneonnightraven4640692/DeepFake-AI-RealTime

- **Source**: [github](https://github.com/stormneonnightraven4640692/DeepFake-AI-RealTime)

- **Summary**: An advanced, LLM-powered toolkit providing comprehensive capabilities for ethical synthetic media detection, analysis, and responsible content generation.

- **Tags**: `llm`


---


## 133. JuneYaooo/nihaixia-tcm

- **Source**: [github](https://github.com/JuneYaooo/nihaixia-tcm)

- **Summary**: 倪海厦中医课程资料的 Agent Skill：支持课程检索、方证穴位辨析、学习笔记整理与板书截图证据索引。 |  An Agent Skill for Ni Haixia TCM course study, formula-pattern lookup, acupoint reference, and screenshot evidence indexing.

- **Tags**: `agent`


---


## 134. antigravity-cli-google/antigravity-cli

- **Source**: [github](https://github.com/antigravity-cli-google/antigravity-cli)

- **Summary**: google antigravity cli ide github agentic development platform gemini 3.5 flash terminal ai agent automatic coding workspace installation guide tutorial windows mac linux

- **Tags**: `agent` `gemini` `google`


---


## 135. Harkirat1462/claude-code-cli

- **Source**: [github](https://github.com/Harkirat1462/claude-code-cli)

- **Summary**: claude code cli install codex github anthropic agentic coding system terminal assistant codebase git workflows multi file editing mcp protocol model context protocol subagents automation ci cd integration npm install setup guide tutorial command line interface latest version 2026 free download update bug fix test runner**

- **Tags**: `agent` `anthropic` `claude` `codex`


---


## 136. withkynam/vibecode-pro-max-kit

- **Source**: [github](https://github.com/withkynam/vibecode-pro-max-kit)

- **Summary**: Your AI forgets. This remembers. Spec-driven coding harness for vibecoders, product owners, CEOs and real builders — self-improving context memory, 12 agents, 32 skills. Kills context rot, ships features, not spaghetti. Claude Code & Codex. Any stack. 30 seconds

- **Tags**: `agent` `claude` `codex`


---


## 137. sir1st/hermes-desktop

- **Source**: [github](https://github.com/sir1st/hermes-desktop)

- **Summary**: Moved to EKKOLearnAI/hermes-web-ui; this repo is kept for historical releases.


---


## 138. LLMQuant/skills

- **Source**: [github](https://github.com/LLMQuant/skills)

- **Summary**: Reusable Skills for LLMQuant Agent, Claude Code, Claude.ai, Cursor, Hermes Agent, OpenClaw and Codex, grounded in LLMQuant Data

- **Tags**: `agent` `claude` `codex` `llm`


---


## 139. konoeph/AgentClaimGuard

- **Source**: [github](https://github.com/konoeph/AgentClaimGuard)

- **Summary**: Evidence gate for LLM agent claims - verify claims against evidence, tool results, and policies.

- **Tags**: `agent` `llm`


---


## 140. madhvantyagi/SOUL.md

- **Source**: [github](https://github.com/madhvantyagi/SOUL.md)

- **Summary**: This repo contains different Soul.md files each file is different and allow your agents to behave in unique interesting personality. 

- **Tags**: `agent`


---


## 141. AI Loss of Control Incident Management: Response & Resilience

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.30406)

- **Summary**: arXiv:2605.30406v1 Announce Type: new  Abstract: Recent research demonstrating AI systems exhibiting deception and shutdown resistance suggests that AI loss of control (LOC) is an urgent policy concern , yet current literature focuses almost exclusively on alignment and prevention. To address this gap, this paper introduces a foundational framework and taxonomy for managing catastrophic AI LOC incidents. The taxonomy's first level distinguishes between scenarios where regaining control is 'extremely costly' versus 'impossible'. While impossible scenarios demand immediate resilience investments to fundamentally restrict an AI's attack surface , extremely costly scenarios require active incident management via Containment and Threat Neutralization. The framework further categorizes these manageable events into accidental LOC (requiring automated circuit-breaker responses) and adversarial LOC (requiring graduated escalatory measures). By mapping three severity classes to specific scenario matrices, this paper provides a concrete, proportional guide for managing unprecedented AI risks.

- **Tags**: `adversarial` `alignment` `policy` `research`


---


## 142. The Global Landscape of Environmental AI Regulation: From the Cost of Reasoning to a Right to Green AI

- **Source**: [arxiv_cy](https://arxiv.org/abs/2603.00068)

- **Summary**: arXiv:2603.00068v2 Announce Type: replace  Abstract: Artificial intelligence (AI) systems impose substantial and growing environmental costs, yet transparency about these impacts has declined even as their deployment has accelerated. This paper makes three contributions. First, we collate empirical evidence that generative Web search and reasoning models - which have proliferated in 2025 - come with much higher cumulative environmental impacts than previous generations of AI approaches. Second, we map the global regulatory landscape across eleven jurisdictions and find that the manner in which environmental governance operates (predominantly at the facility-level rather than the model-level, with a focus on training rather than inference, with limited AI-specific energy disclosure requirements outside the EU) limits its applicability. Third, to address this, we propose a three-pronged policy response: mandatory model-level transparency that covers inference consumption, benchmarks, and compute locations; user rights to opt out of unnecessary generative AI integration and to select environmentally optimized models; and international coordination to prevent regulatory arbitrage. We conclude with concrete legislative proposals - including amendments to the EU AI Act, Consumer Rights Directive, and Digital Services Act - that could serve as templates for other jurisdictions.

- **Tags**: `benchmark` `generative` `governance` `policy` `rag`


---


## 143. 老黄的Token经济学翻车了！微软亚马逊通通跳车

- **Source**: [qbitai](https://www.qbitai.com/2026/06/427541.html)

- **Summary**: token热潮开始降温


---


## 144. 清智系企业亮相 BEYOND Expo 2026 并斩获多项大奖

- **Source**: [qbitai](https://www.qbitai.com/2026/06/427530.html)

- **Summary**: 已经投资了数个世界领先的AI科技公司


---


## 145. 近2亿美元！VAST完成新一轮融资，正式披露世界模型路线

- **Source**: [qbitai](https://www.qbitai.com/2026/06/427516.html)

- **Summary**: 场景永不消失，多人真正同屏


---


## 146. 今天起，无限期免费！全球首个全模态API开放，Top 10 AI Lab出手

- **Source**: [qbitai](https://www.qbitai.com/2026/06/427332.html)

- **Summary**: 文本图像视频都能用


---


## 147. OpenAI重返机器人赛道！四大核心岗位开招

- **Source**: [qbitai](https://www.qbitai.com/2026/06/427238.html)

- **Summary**: 年薪超200万

- **Tags**: `openai`


---


## 148. Token贵只因你喂给模型的垃圾太多了丨@亚马逊王晓野AIGC2026

- **Source**: [qbitai](https://www.qbitai.com/2026/06/427141.html)

- **Summary**: Demo从来都不难做，难的是让它在企业生产环境里真正跑起来


---


## 149. 材料版AlphaFold来了！40个工业任务全方位SOTA，AI4S迎来行业大突破

- **Source**: [qbitai](https://www.qbitai.com/2026/06/427142.html)

- **Summary**: 叠加LLM“训练buff”，材料AI终于学会了“物理直觉”

- **Tags**: `llm`


---


## 150. Vision-Language Models Suppress Female Representations Under Ambiguous Input

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.31556)

- **Summary**: arXiv:2605.31556v1 Announce Type: cross  Abstract: Alignment teaches vision-language models (VLMs) to avoid expressing demographic biases, and when gender is clearly visible they largely succeed. Far less is known about ambiguous inputs (a worker in full gear, a figure seen from behind) cases common in practice yet rarely studied. We find that minimal prompting pressure exposes occupation-gender defaults when prompting ambiguous input images, with models collapsing to male even for strongly female-stereotyped occupations. But do these outputs reflect what models actually encode internally? We introduce LALS (Latent Association Leaning Score), a zero-shot metric that projects visual-token activations into the model's text-embedding space to measure concept associations per token and layer. Across 15 occupations, over 800 gender-ambiguous images, and four VLMs, internal representations and outputs are systematically decoupled: models often encode a female association internally yet output male. Layer-wise analysis reveals an asymmetric filter -- male signal amplifies end-to-end while female signal peaks mid-network and is suppressed before generation -- and a color ablation shows that culturally loaded visual cues such as clothing color further modulate these internal associations.

- **Tags**: `alignment` `bias` `embedding` `vision`


---


## 151. The Refutability Gap: Challenges in Validating Reasoning by Large Language Models

- **Source**: [arxiv_cy](https://arxiv.org/abs/2601.02380)

- **Summary**: arXiv:2601.02380v4 Announce Type: replace  Abstract: Recent reports claim that Large Language Models (LLMs) have achieved the ability to derive new science and exhibit human-level general intelligence. We argue that such claims are not rigorous scientific claims, as they do not satisfy Popper's refutability principle (often termed falsifiability), which requires that scientific statements be capable of being disproven. We identify several methodological pitfalls in current AI research on reasoning, including the inability to verify the novelty of findings due to opaque and non-searchable training data, the lack of reproducibility caused by continuous model updates, and the omission of human-interaction transcripts, which obscures the true source of scientific discovery. Additionally, the absence of counterfactuals and data on failed attempts creates a selection bias that may exaggerate LLM capabilities. To address these challenges, we propose guidelines for scientific transparency and reproducibility for research on reasoning by LLMs. Establishing such guidelines is crucial for both scientific integrity and the ongoing societal debates regarding fair data usage. We also discuss related issues such as the challenge of LLM-generated plagiarism and the general questions of retrieval vs. novelty in LLMs.

- **Tags**: `bias` `debate` `large language model` `llm` `reasoning`


---


## 152. Certified Circuits: Stability Guarantees for Mechanistic Circuits

- **Source**: [arxiv_cy](https://arxiv.org/abs/2602.22968)

- **Summary**: arXiv:2602.22968v3 Announce Type: replace-cross  Abstract: Understanding how neural networks arrive at their predictions is essential for debugging, auditing, and deployment. Mechanistic interpretability pursues this goal by identifying circuits--minimal subnetworks responsible for specific behaviors. However, existing circuit discovery methods are brittle: circuits depend strongly on the chosen concept dataset and often fail to transfer out-of-distribution, raising doubts whether they capture the concept or merely dataset-specific artifacts. We introduce Certified Circuits, which provide provable stability guarantees for circuit discovery. Our framework wraps any black-box discovery algorithm with randomized data subsampling to certify that inclusion decisions over circuit components--neurons or edges of the model graph, depending on the base algorithm--are invariant to bounded edit-distance perturbations of the concept dataset. Unstable components are abstained from, yielding circuits that are more compact and more accurate. We validate across three architectures (ResNet, ViT, GPT-2) on vision (ImageNet and four OOD datasets) and language (IOI, IOI-Hard, Greater-Than) tasks. Certified circuits achieve up to 56% higher accuracy and up to 80% fewer components, and remain reliable where baselines degrade. Certified Circuits puts circuit discovery on formal ground by producing mechanistic explanations that are provably stable and better aligned with the target concept. Code: https://github.com/AlaaAnani/certified-circuits.

- **Tags**: `gpt` `interpretability` `mechanistic interpretability` `vision`


---


## 153. Assessing Predictive Models for Fairness Based on Movement Patterns

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.23234)

- **Summary**: arXiv:2605.23234v2 Announce Type: replace-cross  Abstract: Assessing the spatial fairness of predictive models involves establishing whether they are statistically penalizing (favoring) individuals associated with certain geographical locations. Literature on this topic makes the fundamental assumption that each individual is assigned to a single geographical location (e.g., place of residence). However, fairness with respect to the set of locations where one has been, i.e., their movement patterns over different regions, also matters when fairness is considered. Consequently, we argue that it is necessary to generalize the notion of spatial fairness to also include movement patterns, leading to the novel problem of assessing predictive models for fairness relative to the movements of individuals. To deal with this problem, we propose an approach that first associates the movements of individuals to certain geographic regions, considering multiple spatial partitions with different resolutions and alignments, and then employs a suitable spatial scan statistic to assess whether a predictive model is fair based on movement patterns. In the experimental evaluation, we study the performance of our approach over thousands of synthetic unfair datasets, showing that it is effective at detecting this new type of unfairness and at retrieving the set of objects treated unfairly, while localization performance exhibits a consistent multi-resolution trade-off.

- **Tags**: `alignment` `fairness`


---


## 154. Routing on the Stiefel Manifold: When Does Adaptive Subspace Selection Help for Cross-Domain EEG Decoding?

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.31043)

- **Summary**: arXiv:2605.31043v1 Announce Type: new  Abstract: Cross-domain EEG decoding remains challenging despite advances in Riemannian deep learning: covariance matrices from different subjects occupy systematically distinct regions of the SPD manifold, yet existing domain adaptation methods either require target-domain calibration data or learn subject-specific components that cannot generalise across domains. We propose dynamic Stiefel routing: a pool of $K$ expert projection filters on the Stiefel manifold, each specialised for a different region of the SPD manifold, with each input covariance routed to the most appropriate filter via cross-attention, adapting the subspace projection per sample. A central finding is that this approach, implemented naively, provably collapses to ensemble averaging: when routing weights are uniform, the adaptive filter reduces exactly to an equal-contribution combination of experts, indistinguishable from a single fixed filter. Three structural properties break this degeneracy: a symmetric anchor $W_{\mathrm{base}} \in \mathrm{St}(n,k)$ that removes proximity bias among experts; a frozen domain-discriminative query encoder that decouples routing from task optimisation; and a decoupled key alignment loss that trains expert keys toward stable domain attractors. Together they produce the first genuinely committed and domain-structured routing on SPD manifolds, with consistent gains across three datasets: balanced accuracy improves from $0.773\to 0.823$, $0.757\to 0.809$, and $0.801\to 0.839$, with the alignment strategy determined automatically by a single data-driven rule and no dataset-specific hyperparameter search.

- **Tags**: `alignment` `bias` `rag`


---


## 155. Entropic Projection Alignment: Estimating, Explaining, and Improving Model Performance Under Distribution Shift

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.31250)

- **Summary**: arXiv:2605.31250v1 Announce Type: new  Abstract: We propose a unified framework for addressing three key challenges of distribution shift: (1) estimating a model's performance on an unlabeled target domain, (2) explaining the shift by identifying the features responsible, and (3) improving the target domain performance. Our method, Entropic Projection Alignment (EPA), aligns the source distribution to the target by matching carefully selected moments while simultaneously minimising the KL divergence from the source. This formulation yields a unique closed-form solution for importance weights, achieving robustness through implicit variance control. Drawing on domain adaptation theory, we establish that moment matching is sufficient for reliable estimation and adaptation, avoiding the need for full density ratio recovery. Extensive experiments, together with strong theoretical guarantees, demonstrate that EPA consistently outperforms state-of-the-art baselines while offering substantial computational efficiency.

- **Tags**: `alignment` `efficiency` `robustness`


---


## 156. On public and private binary classification with metric space valued predictors

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.31184)

- **Summary**: arXiv:2605.31184v1 Announce Type: cross  Abstract: We consider the problem of binary classification in a framework where the predictor $X$ takes values in an arbitrary separable metric space $\mathcal X$ and the label $Y$ values in $\{ \pm 1 \}$. In the first part of this work, we assume that one has direct access to an i.i.d. sample $(X_1,Y_1),\ldots,(X_n,Y_n)$ from the unknown distribution of the pair $(X,Y)$. We derive a convergence rate for the Proto-NN classifier which was recently introduced as a classifier in the presence of metric space-valued predictors. In the second part of the paper, we reconsider the same problem under an additional privacy constraint. More precisely, we work in the framework of local differential privacy where one assumes that the data $(X_1,Y_1),\ldots,(X_n,Y_n)$ cannot be directly observed but only a privatised surrogate obtained through a suitable mechanism satisfying the privacy constraint is available. The statistician should select an optimal privacy mechanism from the class of all mechanism that guarantee local differential privacy. Our method of choice is to add Laplace distributed noise to both a set of in Proto-NN classifier using the privatised data only is universally consistent. Finally, a rate of convergence for the privatised Proto-NN classifier is derived.

- **Tags**: `differential privacy` `privacy`


---


## 157. Beyond Additive Decompositions: Interpretability Through Separability

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.31200)

- **Summary**: arXiv:2605.31200v1 Announce Type: cross  Abstract: Interpretable machine learning requires models that are accurate and structurally faithful to the data.Existing explainability methods rely heavily on additive representations (e.g., Generalized Additive Models (GAMs), SHapley Additive exPlanations (SHAP), functional ANOVA), which can suffer from signal cancellation and off-support extrapolation in the presence of strong interactions. We propose Tensor Separation Learning (TSL), a regression model that learns a sum of rank-1 products of univariate per-feature functions via a stagewise greedy procedure with orthogonal refitting. By enforcing separability, TSL avoids the information loss inherent in additive projections caused by marginalizing higher-order interactions. The learned TSL model can be fully reconstructed from first-order partial dependence functions, up to constant factors. This stage-wise correspondence ensures that the resulting visualizations are faithful to the fitted components. We establish approximation-rate guarantees for functions with bounded mixed $p$-th order partial derivatives and demonstrate that TSL competes with black-box models on regression benchmarks.

- **Tags**: `benchmark` `explainability` `interpretability`


---


## 158. Adversarial Robustness in One-Stage Learning-to-Defer

- **Source**: [arxiv_ml](https://arxiv.org/abs/2510.10988)

- **Summary**: arXiv:2510.10988v4 Announce Type: replace  Abstract: Learning-to-Defer (L2D) enables hybrid decision-making by routing inputs either to a predictor or to external experts. While promising, L2D is highly vulnerable to adversarial perturbations, which can not only flip predictions but also manipulate deferral decisions. Prior robustness analyses focus solely on two-stage settings, leaving open the end-to-end (one-stage) case where predictor and allocation are trained jointly. We introduce the first framework for adversarial robustness in one-stage L2D, covering both classification and regression. Our approach formalizes attacks, proposes cost-sensitive adversarial surrogate losses, and establishes theoretical guarantees including $\mathcal{H}$, $(\mathcal{R }, \mathcal{F})$, and Bayes consistency. Experiments on benchmark datasets confirm that our methods improve robustness against untargeted and targeted attacks while preserving clean performance.

- **Tags**: `adversarial` `benchmark` `robustness`


---


## 159. A hitchhiker's guide to Poisson gradient estimation

- **Source**: [arxiv_ml](https://arxiv.org/abs/2602.03896)

- **Summary**: arXiv:2602.03896v2 Announce Type: replace  Abstract: Poisson-distributed latent variable models are widely used in computational neuroscience, but differentiating through discrete stochastic samples remains challenging. Two approaches address this: *Exponential Arrival Time* (EAT) simulation and *Gumbel-SoftMax* (GSM) relaxation. We provide the first systematic comparison of these methods, along with practical guidance for practitioners. Our main technical contribution is a modification to the EAT method that theoretically guarantees an unbiased first moment (exactly matching the firing rate), and reduces second-moment bias. We evaluate these methods on their distributional fidelity, gradient quality, and performance on two tasks: (1) variational autoencoders with Poisson latents, and (2) partially observable generalized linear models, where latent neural connectivity must be inferred from observed spike trains. Across all metrics, our modified EAT method exhibits better overall performance (often comparable to exact gradients), and substantially higher robustness to hyperparameter choices. These results extend to over-dispersed Negative Binomial latents, where modified EAT again performs best. However, only GSM generalizes to arbitrary non-Poisson distributions, including the under-dispersed regime. Together, our results clarify the trade-offs between these methods and offer concrete recommendations for practitioners working with Poisson latent variable models.

- **Tags**: `bias` `robustness`


---


## 160. 德系精工邂逅中国智慧 全新奥迪Q5L现已登陆全国门店

- **Source**: [qbitai](https://www.qbitai.com/2026/06/427231.html)

- **Summary**: 


---


## 161. The Tutoring Effectiveness Index: Predicting LLM Math Tutor Quality from Four Conversation Signals

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.30666)

- **Summary**: arXiv:2605.30666v1 Announce Type: new  Abstract: Aligning large language models (LLMs) as math tutors typically demands costly reinforcement-learning (RL) training and external LLM judges. We ask whether a frozen model's internal reasoning signals can replace both. We propose the Tutoring Effectiveness Index (TEI), a training-free, judge-free four-signal index that combines a Schoenfeld-Verify keyword ratio, a math-step density, an ends-question rate, and a deep-reasoning gate from the Deep-Thinking Ratio (DTR) probe. Selecting from $N$ candidates with TEI (the TEI@$N$ rule) raises the improvement rate on pre-incorrect scenarios from $59.0\%$ to $81.9\%$ at $N{=}8$ on a frozen DeepSeek-R1-8B base, with no training and no external judge. We also measure the alignment tax of pedagogical GRPO. Thinking length drops from $1{,}764$ to $119$ words per turn ($-93\%$), Content-Knowledge and Pedagogical-Knowledge accuracy fall by $-71\%$ and $-80\%$ relative, and the student's $\Delta$ Solve Rate crosses from $+0.180$ to $-0.012$. To anchor the behavioural reading, we reproduce an 82-code educational codebook on $119{,}009$ tutor sentences with a one-shot structural classifier. Together, these results offer a cost-effective recipe for building math-tutoring LLMs without RL training or external judges.

- **Tags**: `alignment` `deepseek` `large language model` `llm` `reasoning`


---


## 162. How Early Adopters Used Generative AI Worldwide: Variation by Country Income and Language

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.30685)

- **Summary**: arXiv:2605.30685v1 Announce Type: new  Abstract: AI is being used by people globally, but not everyone is using it in the same ways. Using a large-scale dataset of anonymized, de-identified, and privacy-scrubbed interactions with a widely available and free AI chatbot, we empirically characterize differences in early adopters' usage across countries. Schooling is the most common domain of use in most countries, particularly low-income countries, with a strong inverse association evident between schooling and country-level GDP. Leisure-related use, by contrast, is positively associated with country-level income. Language, we find, also shapes use: English-language interactions are overrepresented in places where the predominant languages were not well-served by existing models during the period of the study. Improving performance across languages may be a key factor, our work suggests, in whether this technology expands digital divides or enables leapfrogging.

- **Tags**: `generative` `privacy`


---


## 163. Traceable by Design: An LLM Pipeline and Dashboard for EU Regulatory Consultation Analysis

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.30995)

- **Summary**: arXiv:2605.30995v1 Announce Type: new  Abstract: Public consultations generate large volumes of data in the form of stakeholder submissions that are practically unfeasible to analyse manually. We present an end-to-end LLM-based pipeline and interactive dashboard for structured topic extraction from regulatory consultation submissions, demonstrated on the European Commission's Digital Fairness Act (DFA) public call for evidence as a case study. The system processes raw PDF attachments and web-form responses, extracts topic annotations, and grounds every extraction in a verbatim quote from the source text. Applied to 4,322 DFA submissions, the pipeline produced 15,368 topic annotations supported by 20,951 verbatim evidence quotes. Three principles govern the proposed design: verbatim grounding, full traceability, and transparency by design. The dashboard exposes the full extraction dataset through five analytical views, from dataset-level topic overviews to individual paragraph drill-downs, with every result traceable to its source. Beyond the predefined DFA topic categories, the pipeline generated certain stakeholder concerns, such as Age Verification, Payment Processor Censorship, and Digital Ownership, that a fixed-taxonomy approach would have missed. The pipeline is domain-generic; adapting it to a new consultation requires only a prompt update and a new dataset. A live demo is available at https://dfa-dashboard.thalesbertaglia.com/. The code and processed data are publicly available at https://github.com/thalesbertaglia/dfa-dashboard.

- **Tags**: `fairness` `llm` `rag`


---


## 164. Context-Conditioned Generative Models Enable Subnational Refinement of Sparse Humanitarian Surveys

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.31489)

- **Summary**: arXiv:2605.31489v1 Announce Type: new  Abstract: Data scarcity limits inference in many scientific and policy domains. Survey data are essential for decision-making, but sparse samples often fail to capture fine spatial granularities. We evaluate normalizing flows, a generative model that learns complex data distributions and can be conditioned on exogenous contextual features, in controlled data scarcity scenarios. Across eight household survey datasets spanning six low-income or middle-income countries in the humanitarian domain, we show that context-conditioned generative models can refine sub-national survey distributions under severe data scarcity, and that performance increases systematically with the richness of the conditioning information. These findings support a general principle for survey data augmentation: generative models can improve sub-national estimates when the sparse sample retains sufficient support and contextual covariates encode relevant local heterogeneity. By learning full conditional distributions rather than point estimates, the approach provides fine-grained evidence for humanitarian decision-making and resource allocation.

- **Tags**: `generative` `policy`


---


## 165. TUX: Measuring Human--AI Tacit Understanding

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.30930)

- **Summary**: arXiv:2605.30930v1 Announce Type: cross  Abstract: As large language models (LLMs) increasingly act as collaborative partners, human--AI alignment is often evaluated through explicit task success, accuracy, or reward optimization. Yet many collaborative settings depend on tacit understanding: whether an agent can align with a human's evaluative stance or representational priors without clear objectives, communication, or feedback. To study this capacity, we develop a spectrum-placement task inspired by the social party game Wavelength, in which humans and agents independently place concepts along subjective spectra. We operationalize the Tacit Understanding Index (TUX) as a pairwise measure of similarity between human and agent judgments, and evaluate it with 241 human participants and 200 profile-conditioned LLM agents across four models. We find that nearest human--agent pairs in trait space achieve significantly higher TUX, suggesting that tacit alignment is structured by person-level characteristics rather than random similarity. Regression analyses show that TUX becomes more explainable as predictor sets become richer, with individual traits, decision-making styles, and confidence improving over aggregate trait-distance baselines. These findings suggest that tacit understanding between humans and LLMs is measurable, while revealing the limits of profile-based conditioning for capturing deeper representational alignment.

- **Tags**: `agent` `alignment` `large language model` `llm`


---


## 166. Governance-Aware Software Architecture for Multi-Stakeholder Platforms

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.31316)

- **Summary**: arXiv:2605.31316v1 Announce Type: cross  Abstract: Multi-stakeholder platforms (MSPs) coordinate diverse stakeholder groups, often with competing or conflicting requirements. As these platforms increasingly take digital form, engineers building them make architectural decisions about data visibility, service decomposition, and algorithm design that directly determine which stakeholder requirements are prioritized when conflicts arise. Software architecture literature provides patterns for data isolation and access control among tenants but does not address how architectural decisions resolve conflicts among stakeholders with structurally divergent interests. MSP governance literature identifies the principles at stake but treats technology as neutral infrastructure. Neither addresses the translation between governance principles and architectural decision spaces. This paper proposes a governance-architecture correspondence framework that surfaces implicit governance decisions, making them explicit and debatable before deployment. The framework maps five MSP governance principles to the architectural decision spaces where they must be addressed, identifying for each the governance-aware design choice and the technically convenient default it overrides. We illustrate the framework in a constructed knowledge platform for pig farming in Rwanda, where five stakeholder types present structurally conflicting requirements. As work in progress, the framework is proposed but not yet empirically validated; a planned pre/post judgment study with platform users across all stakeholder types will test falsifiable predictions about governance outcomes.

- **Tags**: `governance`


---


## 167. Multi-Level Barriers to Generative AI Adoption Across Disciplines and Professional Roles in Higher Education

- **Source**: [arxiv_cy](https://arxiv.org/abs/2603.27052)

- **Summary**: arXiv:2603.27052v3 Announce Type: replace  Abstract: Generative Artificial Intelligence (GenAI) is rapidly reshaping higher education, yet barriers to its adoption across different disciplines and institutional roles remain underexplored. Existing literature frequently attributes adoption barriers to individual-level factors such as perceived usefulness and ease of use. This study instead investigates whether such barriers are structurally produced. Drawing on a multi-method survey analysis of 272 academic and professional services (PSs) staff at a Russell Group university, we examine how disciplinary contexts and institutional roles shape perceived barriers. By integrating multinomial logistic regression (MLR), structural equation modelling (SEM), and semantic clustering of open-ended responses, we move beyond descriptive accounts to provide a multi-level explanation of GenAI adoption. Our findings reveal clear, systematic differences: non-STEM academics primarily report ethical and cultural barriers related to academic integrity, whereas STEM and PSs staff disproportionately emphasize institutional, governance, and infrastructure constraints. We conclude that GenAI adoption barriers are deeply embedded in organizational ecosystems and epistemic norms, suggesting that universities must move beyond generalized training to develop role-specific governance and support frameworks.

- **Tags**: `generative` `governance`


---


## 168. Who, Why, and How: Disentangling the Effects of Moderation Source, Context, and Language on Post-Removal Behavior

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.16204)

- **Summary**: arXiv:2605.16204v2 Announce Type: replace  Abstract: Content moderation is a central mechanism through which platforms attempt to balance user engagement with community governance. Yet existing research has largely treated moderation as a uniform intervention, overlooking how moderator source, violation context, and linguistic style jointly shape user behavior. Drawing on the Human--AI Interaction Theory of Interactive Media Effects (HAII-TIME), this study examines how these three dimensions produce divergent post-moderation behavioral trajectories in a large-scale observational dataset of 11,795,036 moderation events across 9,285,410 users and 61,261 subreddits on Reddit (2021--2025). Using probabilistic behavioral classification, ANOVA, and OLS regression with PCA-derived linguistic features, we find that bot moderation consistently produces higher compliance and lower self-censorship than human or modteam moderation, challenging the assumption that human agency cues are inherently advantageous. Modteam moderation produces the strongest self-censorship effects, suggesting that institutional depersonalization is a meaningful driver of behavioral withdrawal. Violation severity emerges as a critical contingency: linguistic strategies effective in routine contexts -- elaborated explanation, community-scale appeals, direct personal address -- can backfire for serious violations, whereas prosocially framed and emotionally emphatic messages become most effective when stakes are highest. Of 480 linguistic interactions tested, 33 survive FDR correction. These findings extend HAII-TIME by introducing violation salience as a moderator of cue-based processing, and offer empirical grounding for context-adaptive moderation design.

- **Tags**: `governance` `research`


---


## 169. OLG++: A Semantic Extension of Obligation Logic Graph

- **Source**: [arxiv_cy](https://arxiv.org/abs/2507.05488)

- **Summary**: arXiv:2507.05488v2 Announce Type: replace-cross  Abstract: We present OLG++, a semantic extension of the Obligation Logic Graph (OLG) for modeling regulatory and legal rules in municipal and interjurisdictional contexts. OLG++ introduces richer node and edge types, including spatial, temporal, party group, defeasibility, and logical grouping constructs, enabling nuanced representations of legal obligations, exceptions, and hierarchies. The model supports structured representation of rules with contextual conditions, precedence, and complex triggers. We demonstrate its use through examples from food-business regulations, showing how OLG++ supports legal question answering using property-graph queries. We also discuss how OLG++ can complement LegalRuleML by providing graph-native constructs for subclass relations, spatial constraints, and reified exception structures. The worked examples and first-pass coverage analysis show that, on the dimensions studied, OLG++ is more expressive than the baseline OLG model for municipal regulatory representation.

- **Tags**: `rag` `regulation`


---


## 170. A Behavioural and Representational Evaluation of Goal-Directedness in Language Model Agents

- **Source**: [arxiv_cy](https://arxiv.org/abs/2602.08964)

- **Summary**: arXiv:2602.08964v2 Announce Type: replace-cross  Abstract: Understanding an agent's goals helps explain and predict its behaviour, yet there is no established methodology for reliably attributing goals to agentic systems. We propose a framework for evaluating goal-directedness that integrates behavioural evaluation with interpretability-based analyses of models' internal representations. As a case study, we examine an LLM agent navigating a 2D grid world towards a goal state. Behaviourally, we evaluate the agent against optimal policies across varying grid sizes, obstacle densities, and goal structures, finding that performance scales with task difficulty while remaining robust to difficulty-preserving transformations and multi-goal structures. We then use probing methods to decode internal representations of the environment and multi-step action plans. We find that the LLM agent non-linearly encodes a coarse spatial map, preserving approximate task-relevant cues about its position and the goal location; that its actions are broadly consistent with these internal representations; and that reasoning reorganises them, shifting from spatial cues towards immediate action selection. Our findings support the view that introspective examination is required beyond behavioural evaluations to characterise how agents represent and pursue their objectives.

- **Tags**: `agent` `interpretability` `llm` `reasoning`


---


## 171. Memory by Design: Probabilistic Sequence Layers

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.31163)

- **Summary**: arXiv:2605.31163v1 Announce Type: new  Abstract: We introduce the design-model framework: a way to derive efficient recurrent sequence maps from explicit assumptions about memory. A design model writes evidence into memory by exact Bayesian filtering; a query-dependent readout produces a predictive distribution whose mean is the layer output. In our linear-Gaussian instantiation, the \emph{Bayesian Layer} propagates both a mean and a covariance: the covariance tracks uncertainty over stored associations, steering writes toward uncertain directions, attenuating gains as evidence accumulates, and preserving confident memories. The same framework unifies several sub-quadratic recurrences. Linear attention, GLA, and Mamba-2/SSD are exact filters under one design model, whereas DeltaNet and related Delta-rule models arise as covariance-reset reductions under another. Restoring the covariance yields closed-form predictions for retrieval dynamics, verified empirically, and improves robustness beyond the training regime across controlled collision studies, learned associative recall, and the Zoology MQAR benchmark; distilling Bayesian Layers into a pretrained 340M Gated DeltaNet improves RULER long-context retrieval at matched compute.

- **Tags**: `benchmark` `robustness`


---


## 172. Physics-informed Goal-Conditioned Reinforcement Learning under Hybrid Contact Dynamics

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.30503)

- **Summary**: arXiv:2605.30503v1 Announce Type: cross  Abstract: Learning to reach arbitrary goals from sparse feedback requires agents to infer a rich notion of reachability across state--goal pairs. Goal-conditioned reinforcement learning (GCRL) tackles this challenge by learning policies that generalize across goals, but this generalization becomes increasingly difficult as the underlying dynamics become high-dimensional, hybrid, or contact-dependent. To address this issue, physics-informed GCRL (Pi-GCRL) introduces optimal-control-inspired inductive biases into goal-conditioned value learning. While Pi-GCRL methods have proven effective in navigation and object-free goal-reaching domains, their reliability in contact-rich tasks remains unclear, where contact interactions induce hybrid dynamics, mode-dependent controllability, and nonsmooth value landscapes. In this work, we show that these structural properties can cause existing Pi-GCRL methods to degrade when applied naively to contact-rich manipulation. Motivated by this analysis, we introduce contact-aware and hierarchical formulations that apply physics-informed inductive biases selectively across the manipulation problem. Our results provide a principled step toward extending Pi-GCRL to contact-rich manipulation.

- **Tags**: `agent` `bias`


---


## 173. Kalimati Vegetable Price Index Forecasting with a Momentum Corrected Online Stacking Ensemble

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.30720)

- **Summary**: arXiv:2605.30720v1 Announce Type: cross  Abstract: Forecasting agricultural commodity prices in emerging economies is difficult due to high volatility, frequent supply disruptions, and strong cultural influences on demand. This study introduces the Kalimati Vegetable Price Index (KVPI), a new inverse-volatility weighted composite index that aggregates 135 daily wholesale commodities from Kathmandu over ten years (2013-2023). By creating a stable macro-level signal, the KVPI reduces the noise inherent in modelling individual crops. A rich set of 64 causally valid features was developed, including festival lead-lag effects, rolling statistics, and calendar variables. Fourteen forecasting models spanning statistical, tree-based, deep learning, hybrid, and transformer architectures were rigorously evaluated across short (7-day), medium (14- and 30-day), and long-term (90-day) horizons. Tree-based ensembles proved notably robust, while classical statistical models and complex transformers struggled with the noisy dataset. The proposed Momentum-Corrected Online Stacking Ensemble achieved the strongest performance, yielding a Root Mean Square Error (RMSE) of 1.771, an exceptionally low Mean Absolute Percentage Error (MAPE) of 0.68%, and explaining 84.5% of the variance (R-squared = 0.845) at the 90-day horizon. This open-source pipeline provides policymakers and supply chain actors in Nepal and similar markets with a practical, reliable tool for anticipating price movements and strengthening food security.

- **Tags**: `policy` `transformer`


---


## 174. Bayesian Classification with Probit-link Split-and-merge Gaussian Process Prior in EEG-based Brain-Computer Interfaces

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.30775)

- **Summary**: arXiv:2605.30775v1 Announce Type: cross  Abstract: A Brain-Computer Interface (BCI) speller systems based on Event-Related Potentials (ERPs) enables users to select characters by detecting brain responses to visual stimuli, recorded through electroencephalogram (EEG). One challenge is to accurately identify target-related responses, such as the P300 component. However, existing methods tend to ignore feature selection, perform feature selection without interpretability, or require large computational effort or data manipulation. To address these limitations, we propose a novel Bayesian generative modeling framework to the binary classification of EEG responses to stimuli. Our approach employs a Probit-link Split-and-merge Gaussian Process (P-SMGP) prior to perform spatial-temporal feature selection, effectively capturing the distinctions between target and non-target ERP responses. Through both simulation studies and real EEG data analysis, our approach can reduce computational complexity and provide statistical interpretations on transformed ERP functions while maintaining comparable prediction accuracy. These findings underscore the value of interpretable, stimulus-level modeling for advancing predictive and personalized BCI systems.

- **Tags**: `generative` `interpretability`


---


## 175. Inspectable Neural Markov Models for Non-Stationary Time Series

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.30943)

- **Summary**: arXiv:2605.30943v1 Announce Type: cross  Abstract: Modeling non-stationary stochastic systems requires balancing the representational capacity of deep learning with the structural transparency of classical probabilistic models. Markov transition matrices provide such a framework, but traditional frequency-based estimation collapses at high resolutions due to data sparsity. We propose a hybrid approach that parameterizes the manifold of stochastic matrices through a neural network, enabling estimation of time-inhomogeneous Markov chains in sparse-data regimes, and use financial markets as a testbed to investigate the Markov state variable as a critical inductive bias. We show that conditioning on realized volatility produces a more internally consistent Markovian structure than return-based states, achieving a $5.6\%$ reduction in Chapman-Kolmogorov discrepancy and superior held-out likelihood in 9 of 10 assets. Unlike black-box sequence models, our approach generates explicit matrices amenable to direct geometric analysis, surfacing structural findings such as the universal homogenization of transition probabilities under high-volatility regimes.

- **Tags**: `bias`


---


## 176. Convergence of Two-Timescale Markovian Stochastic Approximations with Applications in Reinforcement Learning

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.31172)

- **Summary**: arXiv:2605.31172v1 Announce Type: cross  Abstract: This work studies the convergence of two-timescale stochastic approximations (SA), a class of iterative algorithms that update two sets of parameters in fast and slow timescales respectively. Notable examples of two-timescale SA in reinforcement learning (RL) include temporal difference learning with gradient correction (TDC) and actor-critic methods. Previously, the stability (i.e., boundedness) and convergence of two-timescale SA were only established under i.i.d. noise. This work instead establishes the stability and convergence of two-timescale SA under Markovian noise, a setup that is more realistic in RL. Notably, we do not need to use any projection operator and the noise does not need to live in a compact space. Our key technical novelty is to control the fast timescale parameter with the running max of the slow timescale parameter, instead of with the current slow timescale parameter, as most prior works do. As a key application, we establish the first almost sure convergence of TDC with eligibility traces under off-policy learning with linear function approximation.

- **Tags**: `policy`


---


## 177. Why Linear Recurrent Memory Works in Partially Observable Reinforcement Learning

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.31261)

- **Summary**: arXiv:2605.31261v1 Announce Type: cross  Abstract: The family of linear recurrent neural networks has shown strong performance as recurrent memory units in partially observable reinforcement learning. We provide a theoretical justification for their empirical effectiveness by constructing and studying two linear filters: (i) the first exactly reproduces the pre-softmax logits of the belief vector in a hidden Markov model (HMM) under a deterministic transition matrix, thereby serving as a sufficient statistic for optimal policy learning, (ii) the second achieves vanishing state-decoding error under a nearly deterministic transition matrix, thus reducing state ambiguity to near zero. The results extend to action-controlled HMMs, where the corresponding linear filters become time-varying with action-dependent dynamics. We illustrate our main results through numerical experiments and further show that the constructed linear filter serves as a strong feature extractor in a small reinforcement learning game.

- **Tags**: `policy`


---


## 178. On the regularization of Wasserstein GANs

- **Source**: [arxiv_ml](https://arxiv.org/abs/1709.08894)

- **Summary**: arXiv:1709.08894v3 Announce Type: replace  Abstract: Since their invention, generative adversarial networks (GANs) have become a popular approach for learning to model a distribution of real (unlabeled) data. Convergence problems during training are overcome by Wasserstein GANs which minimize the distance between the model and the empirical distribution in terms of a different metric, but thereby introduce a Lipschitz constraint into the optimization problem. A simple way to enforce the Lipschitz constraint on the class of functions, which can be modeled by the neural network, is weight clipping. It was proposed that training can be improved by instead augmenting the loss by a regularization term that penalizes the deviation of the gradient of the critic (as a function of the network's input) from one. We present theoretical arguments why using a weaker regularization term enforcing the Lipschitz constraint is preferable. These arguments are supported by experimental results on toy data sets.

- **Tags**: `adversarial` `generative`


---


## 179. Conformal C2ST: Turning weak classifiers into strong two-sample tests

- **Source**: [arxiv_ml](https://arxiv.org/abs/2507.17026)

- **Summary**: arXiv:2507.17026v2 Announce Type: replace  Abstract: The two-sample testing problem, a fundamental task in statistics and machine learning, seeks to determine whether two sets of samples, drawn from underlying distributions $p$ and $q$, are in fact identically distributed (i.e. whether $p=q$). A popular and intuitive approach is the classifier two-sample test (C2ST), where a classifier is trained to distinguish between samples from $p$ and $q$. Yet despite simplicity of the C2ST, its reliability hinges on access to a near-Bayes-optimal classifier, a requirement that is rarely met and difficult to verify. This raises a major open question: can a weak classifier still be useful for two-sample testing? We show that the answer is a definitive yes. Building on the work of Hu and Lei (2024), we analyze two conformal variants of the C2ST that convert the scores from any trained classifier -- even if weak, biased, or overfit -- into exact, finite-sample p-values. We establish two key theoretical properties of the conformal C2ST: (i) finite-sample Type-I error control, and (ii) non-trivial power that degrades gently in tandem with the error of the trained classifier. The upshot is that even poorly performing classifiers can yield powerful and reliable two-sample tests. This general framework finds a powerful application in Bayesian inference, particularly for validating Neural Posterior Estimation (NPE) models, where the task of comparing a learned posterior approximation $q(\theta \mid y)$ to the true posterior $p(\theta \mid y)$ can be framed as a two-sample test. Empirically, the Conformal C2ST outperforms classical discriminative tests across a wide range of benchmarks for this task. Our results establish the conformal C2ST as a practical, theoretically grounded diagnostic tool.

- **Tags**: `benchmark` `bias`


---


## 180. Outcome-Aware Spectral Feature Learning for Instrumental Variable Regression

- **Source**: [arxiv_ml](https://arxiv.org/abs/2512.00919)

- **Summary**: arXiv:2512.00919v2 Announce Type: replace  Abstract: We address the problem of causal effect estimation in the presence of hidden confounders using nonparametric instrumental variable (IV) regression. An established approach is to use estimators based on learned spectral features, that is, features spanning the top singular subspaces of the operator linking treatments to instruments. While powerful, such features are agnostic to the outcome variable. Consequently, the method can fail when the true causal function is poorly represented by these dominant singular functions. To mitigate, we introduce Augmented Spectral Feature Learning, a framework that makes the feature learning process outcome-aware. Our method learns features by minimizing a novel contrastive loss derived from an augmented operator that incorporates information from the outcome. By learning these task-specific features, our approach remains effective even under spectral misalignment. We provide a theoretical analysis of this framework and validate our approach on challenging benchmarks.

- **Tags**: `alignment` `benchmark`


---


## 181. Learning-to-Defer with Expert-Conditional Advice

- **Source**: [arxiv_ml](https://arxiv.org/abs/2603.14324)

- **Summary**: arXiv:2603.14324v5 Announce Type: replace  Abstract: Learning-to-Defer routes each input to the expert that minimizes expected cost, but it assumes that the information available to every expert is fixed at decision time. Many modern systems violate this assumption: after selecting an expert, one may also choose what additional information that expert should receive, such as retrieved documents, tool outputs, or escalation context. We study this problem and call it Learning-to-Defer with advice. We show that a broad family of natural separated surrogates, which learn routing and advice with distinct heads, is inconsistent even in the smallest non-trivial setting. We then introduce an augmented surrogate that operates on the composite expert--advice action space and prove an $\mathcal{H}$-consistency guarantee together with an excess-risk transfer bound, yielding recovery of the Bayes-optimal policy in the limit. Experiments on tabular, language, and multi-modal tasks show that the resulting method improves over standard Learning-to-Defer while adapting its advice-acquisition behavior to the cost regime; a synthetic benchmark confirms the failure mode predicted for separated surrogates.

- **Tags**: `benchmark` `policy`


---


## 182. Overview over the first decade of LIMITS

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.30543)

- **Summary**: arXiv:2605.30543v1 Announce Type: new  Abstract: Computing within limits is a promising field, that follows principles of a) questioning endless growth narrative, b) considering and preparing for models of scarcity and c) reducing energy and material consumption, while considering d) a global spatial scale and e) long time frames. With computing's environmental impact growing and ecological limits becoming increasingly pressing, the LIMITS workshop has served as a central venue for this community since its inception in 2015, but an overview of the research published there has yet to be described.   This paper addresses this gap by analyzing 160 publications from the LIMITS workshop in the period 2015 to 2025 to identify its international spread, contributions and developments in relation to field's core concerns, combining programmatic analysis with a manual review.   Our findings indicate that the field has increasingly mentioned degrowth and post-growth, especially in 2024-2025. It has broadened its global perspective, with a growing, but still limited, representation of work beyond the Global North. The majority of papers are positional or observational, while artifact-producing research remains relatively scarce, though solution-oriented output has grown in recent years.   This paper contributes to the LIMITS community by mapping its first decade and current trends to support future research and enhance its global impact.

- **Tags**: `research`


---


## 183. Reinforcement Learning for Special Education: Aligning LLM Tutors to Diverse Learners through Disability-Adaptive Training

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.30670)

- **Summary**: arXiv:2605.30670v1 Announce Type: new  Abstract: Large language models are increasingly deployed as intelligent tutors, yet research on aligning them for special education remains absent. Recent work has applied reinforcement learning to LLM tutors, but these methods target a generic learner in a single domain (mathematics) and do not address the cognitive and communicative diversity of learners with disabilities. We introduce \emph{Special-R1}, a framework that extends pedagogical RL to special education through two components: (1) a two-dimensional adaptive system prompt that couples a difficulty-based support level with a disability-specific teaching style across five disability profiles; and (2) a persona-aware Thinking Reward whose judge rubric is conditioned on the learner's disability profile. On a persona-augmented test set of 690 multi-turn dialogues, our full model raises persona-aware Fit from 6.75 (generic baseline) to 8.40 (+1.65) and SPED-rubric Helpfulness from 0.720 to 0.768, leading on the four-component Total (2.911, +0.064 over the runner-up) while remaining within 0.01 of the strongest variant on the out-of-domain OpenLearnLM benchmark (8.53). Ablations show that the Thinking Reward becomes effective only in combination with adaptive prompting, and that residual weakness on specific learning disability in mathematics motivates targeted multimodal extensions.

- **Tags**: `benchmark` `large language model` `llm` `multimodal` `research`


---


## 184. Comparing LLM-Based Conversational and Graphical Interfaces for Industrial Decision Tasks: An Exploratory Mixed-Methods Study

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.31224)

- **Summary**: arXiv:2605.31224v1 Announce Type: new  Abstract: The use of Generative AI Conversational User Interfaces (CUI) as a new way to access and analyze data is growing in all sectors, and the industrial one is no exception. There, large amounts of data produced by IoT devices are flowing through user interfaces and may require them a new adaptation to the new analyses needs of decision-makers. LLM-based CUIs are promising a new way to directly interact with those data through the directness of natural language and without the learning costs that every GUI design has. Moreover, the capabilities of LLMs and their agency open up the possibility to automate some tasks and help with the reasoning during decision-making activities. But are this promises well founded? We try to scope this general question with a mixed-approach study comparing a state-of-the-art dashboard with a conversational agent. A total of 20 participants used both interfaces to complete four simulated industrial decision tasks of varying complexity. We combined measures of mental workload, completion time, and decision accuracy with a post-study questionnaire and semi-structured interviews analyzed through thematic analysis. The findings suggest that the conversational agent can reduce interactional effort by supporting more direct access to information, while the dashboard remains valuable for overview and verification. However, these benefits may vary across tasks and require validation through larger-scale studies.

- **Tags**: `agent` `generative` `llm` `reasoning`


---


## 185. Neither Replacement nor Panacea: Comparing LLM-Based Conversational and Graphical Decision Support in Industrial Tasks

- **Source**: [arxiv_cy](https://arxiv.org/abs/2605.31287)

- **Summary**: arXiv:2605.31287v1 Announce Type: new  Abstract: Managers in manufacturing settings rely on digital interfaces to interpret operational data for decision-making, but growing data volume and complexity can make relevant insights difficult to identify efficiently. While dashboards remain dominant in industrial contexts, Large Language Model (LLM)-based conversational agents (CAs), accessed through conversational user interfaces (CUIs), may provide more direct access to such data. However, their effectiveness may depend on the information-processing demands of the task. This study compares an LLM-based CA delivered through a CUI with a dashboard in a manufacturing decision-support scenario. In a mixed factorial experiment with a 2x3 design, 134 industrial decision-makers were assigned to one interface condition and completed three tasks of increasing complexity. We examined perceived Mental Workload (MWL), decision accuracy, completion time, and intended reliance, and tested self-reported data literacy as a moderator. Results showed that the CUI reduced perceived MWL overall and supported faster completion in less demanding tasks, but both advantages diminished as task complexity increased. Neither interface produced a consistent overall advantage in decision accuracy, and the CUI was not preferred as a sole basis for subsequent decisions. Furthermore, data literacy did not reliably moderate interface effects. These findings indicate that conversational interaction offers conditional rather than universal benefits for industrial decision support. LLM-based CAs may reduce information-access effort, whereas complex decisions continue to benefit from persistent, inspectable visual representations.

- **Tags**: `agent` `large language model` `llm`


---


## 186. Improved Distribution Estimation in $\ell_\infty$

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.30509)

- **Summary**: arXiv:2605.30509v1 Announce Type: new  Abstract: We present improved bounds for estimating discrete probability distributions under the $\ell_\infty$ norm. These include minimax bounds in expectation and high-probability tail bounds. We resolve some of the open questions posed in Kontorovich and Painsky (JMLR, 2025) -- including a fully empirical version of the tightest risk bound they presented and identifying the form of the worst-case extremal distribution. Encouraging empirical results are reported as well.

- **Tags**: `minimax` `rag`


---


## 187. Reward Learning from Best-of-$N$ Preference Data: Targets, Tradeoffs, and Design Principles

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.30619)

- **Summary**: arXiv:2605.30619v1 Announce Type: new  Abstract: Best-of-$N$ sampling is widely used to construct pairwise preference data: $N$ candidates are drawn from a base distribution, and the best is paired with a rejected response. Despite its widespread use, what Bradley--Terry (BT) reward learning extracts from such data, and how to choose $N$ and the base distribution, remain unclear. We specialize a recent analysis of preference data via its induced conditional distribution to Best-of-$N$. For independent-reference variants, we derive closed-form reward targets as explicit functions of $N$ and the base distribution, and show that they preserve the latent reward ranking. For the practical Best-vs-Random and Best-vs-Worst variants, chosen and rejected responses are coupled through the same candidate set, so exact BT representability generally fails; nevertheless, bounded-class minimizers approach the reference targets as $N$ grows. Although margin and connectivity are known to govern sample efficiency in pairwise preference learning, Best-of-$N$ couples them through $N$ in opposing directions: larger $N$ widens pairwise margins but reduces connectivity. This trade-off yields two design principles: use larger $N$ when preference labels are the bottleneck, smaller $N$ when generation is the bottleneck; and shape the base distribution to place mass between the responses whose comparison matters most at test time. Experiments on synthetic and real preference data support the predicted dependence on sample size and base-distribution shape.

- **Tags**: `efficiency`


---


## 188. Is the Last Layer Sufficient for Uncertainty Quantification?

- **Source**: [arxiv_ml](https://arxiv.org/abs/2605.30741)

- **Summary**: arXiv:2605.30741v1 Announce Type: new  Abstract: Epistemic uncertainty quantification (UQ) for deep neural networks (DNNs) is a requirement for safe adoption of AI in mission-critical settings. Several leading methods for UQ linearize DNNs to form Bayesian Generalized Linear Models (GLMs), where epistemic uncertainty is modeled via the predictive posterior distribution. Linearizing around the parameters of the final connected layer of a DNN is a commonly used approximation for reducing the computational burden of such GLMs, though it is often believed to come at the cost of degraded performance. In this work, we compare GLMs arising from full-network and last-layer linearization using both theoretical and empirical approaches. We first employ tools from random matrix theory to conduct a theoretical comparison; this analysis reveals no meaningful improvement in the UQ capabilities of full linearization. Coupled with a large-scale empirical evaluation across a range of modern machine learning tasks, we arrive at the following conclusion: a last-layer approximation yields comparable UQ performance while offering substantially improved computational efficiency.

- **Tags**: `efficiency` `glm`


---


## 189. 36氪首发｜原小天才团队做老年硬件，切入居家看护赛道，即将进入海外市场

- **Source**: [36kr](https://36kr.com/p/3835387558065541?f=rss)

- **Summary**: <p>作者&nbsp;|&nbsp;乔钰杰</p>
  <p>编辑&nbsp;|&nbsp;袁斯来</p>
  <p>硬氪获悉，近日，居家养老消费电子品牌「元生智能」完成新一轮超千万元Pre-A轮融资。本轮融资由银创资本领投，东科创跟投。本轮资金将主要用于渠道拓展以及相关新产品的持续迭代。</p>
  <p>元生智能是硬氪长期关注的企业，成立于2022年，主要为65岁以上空巢、独居老人提供居家看护产品。公司创始人、CEO邓龙生曾任小天才学习平板产品负责人、星火教育合伙人；联合创始人房少杰同样来自小天才，曾任小天才电话手表及火火兔产品负责人。</p>
  <p>元生智能旗下老年看护品牌「亲鹿」于2025年初推出亲鹿Z9老人看护机，并开启全渠道销售，目前已进入快速增长阶段。</p>
  <p>今年，公司进一步升级防跌倒模型，并推出新品D系列看护机以及焕新版的Z9E。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260602/v2_acc89136cca34ff0b9166a4228353aa5@5920579_img_gif?x-oss-process=image/quality,q_80" /></p>
  <p class="img-desc">（图源/企业）</p>
  <p>新一代模型采用毫米波雷达与视觉融合的大模型方案进行跌倒检测，采用混合大模型融合技术，实现了更快速、更精准的识别响应。当前，产品跌倒检测精度已达到行业领先水平，误报率与漏报率均维持在极低水平。</p>
  <p>除跌倒识别与家属联络功能外，产品还可基于毫米波雷达技术，对老人的心率与呼吸状态进行实时监测。当老人心率过低或过高时，系统将自动触发预警并通知家属。</p>
  <p>D系列取消了屏幕设计，价格更加亲民。而且D1 Plus根据隐私保护的需求强弱，提供两种终端型号，分为“真实画面”与“隐私线稿保护画面”两类产品选择，在保证看护有效性的同时，也尽可能尊重老人的隐私与生活自由。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260602/v2_e12cb0ee0554475f9319c92f5b7e094a@5920579_oswg817408oswg1080oswg603_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">（图源/企业）</p>
  <p>针对老年用户的使用习惯，元生智能也进行了大量适老化设计。例如，考虑到大部分老人家庭普遍存在多房间，部分设备会离路由器远的情况，设备支持自动中继联网，实现全屋的互联覆盖。</p>
  <p>此外，产品的喇叭与声音效果也针对老年人的听力曲线进行了定制化优化，更强调低频输出，以提升语音清晰度与可辨识度。</p>
  <p>在海外市场方面，元生智能正在通过B2B模式进入加拿大、马来西亚、澳大利亚等市场，并计划于2026年下半年开启海外亚马逊DTC渠道。</p>
  <p><strong>以下为硬氪与元生智能创始人邓龙生访谈节选：</strong></p>
  <p><strong>硬氪：做面向老年人的硬件产品的难点是什么？</strong></p>
  <p><strong>邓龙生：</strong>儿童产品通常是家长买给孩子使用，但老年产品更多是子女买给父母使用。老人作为独立成年人，有自己的需求、情绪和生活习惯，如何在子女与老人之间取得平衡，其实对产品设计提出了很高要求。</p>
  <p>我们非常重视一线用户反馈，我自己也会经常给用户打电话回访，了解退货原因和真实体验。只有真正接触用户，才能避免团队陷入自我感动。</p>
  <p>有一个很典型的细节：曾有老人反馈，自己在摄像头下和人聊天时，会担心设备连接的其他家人在“偷听”。后续我们专门增加了语音传输提示功能——只要开启语音传输，设备就会主动播报提示音，避免“静默监听”，也尽量减少由此引发的家庭矛盾。</p>
  <p>相比儿童产品，成年人的需求其实复杂得多。除了功能需求，还涉及情绪需求、人与人之间的关系需求，以及尊严感、隐私感等更微妙的问题。这些细节都需要团队反复推敲。</p>
  <p><strong>硬氪：为什么您觉得现在做老年硬件的时机成熟了？</strong></p>
  <p><strong>邓龙生：</strong>我们是在2022年开始创业的，当时整个养老行业其实刚刚进入成型阶段。参考日本经验，当一个国家60岁以上人口占比超过18%、65岁以上人口占比超过14%时，养老产业会进入加速发展阶段，而中国直到2022年底才达到这一节点。</p>
  <p>之所以说现在是关键时间点，是因为今年长护险（长期护理保险）将在国内进一步全面铺开。类似制度在日本叫“介护险”，美国则有商业护理险。随着这类政策推进，整个养老市场会从早期市场逐渐演进到中后期市场，行业也会进入高速增长阶段。</p>
  <p>这恰恰给了我们机会。当前赛道的特点是“有品类、缺品牌”，而我们希望借此机会，把“亲鹿”真正做成行业品牌。这一轮融资，一方面会用于渠道拓展，另一方面也会投入到长护险相关产品的持续迭代中。</p>
  <p><strong>硬氪：公司未来还有哪些规划？</strong></p>
  <p><strong>邓龙生：</strong>我们的目标是做“老年版的小天才”——一家真正能够引领行业的养老科技公司。对我们来说，做硬件产品只是起点，更重要的是持续围绕老年人的真实需求，构建完整的养老科技体系。</p>
  <p>未来，我们会继续深耕居家看护赛道，同时逐步拓展更多新的产品线。</p>
  <p>今年下半年我们还将推出紧急救助相关服务，包括7×24小时在线救助体系，进一步完善老年居家看护场景，提升突发情况下的响应能力与安全保障。</p>


---


## 190. 前美团外卖技术负责人创业，做具身智能时代的“餐饮世界模型”

- **Source**: [36kr](https://36kr.com/p/3834292242130825?f=rss)

- **Summary**: <p>具身智能的落地，正在从实验室走向最真实、最繁忙的物理世界。</p>
  <p>而元节智能（AtomBite.AI）选择了一个看起来并不性感、但足够真实的场景：餐饮后厨。</p>
  <p>36氪获悉，具身智能公司元节智能近日完成千万级种子轮融资，由英诺科创基金领投，水木清华校友种子基金、知名投资人个人跟投。资金将主要用于餐饮场景具身世界模型研发及核心产品落地。</p>
  <p><strong>元节核心团队在成立公司前有过较长时期的探索和孵化，此次融资标志着项目初步验证可行性，并已拿到国内外多家头部公司的产品合作部署意向。</strong></p>
  <p>元节智能的创始团队带有鲜明的“美团基因”。</p>
  <p>创始人兼CEO王栋博士曾任美团外卖事业部技术负责人，管理千人产研团队，主导构建支撑日均数千万订单的外卖算法、数据与系统架构；联合创始人李滔曾执掌美团外卖算法与数据体系，是少数真正跑通过“全链路数据算法驱动”的技术负责人；联合创始人李浩哲则是连续创业者，具备多年全球化商业落地经验。</p>
  <p>过去几年，餐饮数字化已经被SaaS、点餐小程序、配送调度系统改造了一轮又一轮，但当全球外卖订单持续攀升，一个长期被忽视的问题开始变得越来越突出：从商家出餐到骑手取餐之间，仍然存在大量高度依赖人工的物理操作环节。</p>
  <p>比如打包、封签、分拣、接驳、配送。</p>
  <p>这些流程看似琐碎，却直接影响整个履约效率。错单、漏单、撒漏带来的损耗，会同时传导至用户、商家、骑手与平台四端。与此同时，全球餐饮行业还普遍面临结构性用工问题：北美快餐行业时薪持续上涨，国内餐饮门店则长期存在招工难、流动率高的问题。</p>
  <p>离开美团之后，王栋曾在北美与新加坡进行了持续数月的市场考察，深入走访大量餐饮商家与外卖平台。他最终形成了一个明确判断：餐饮后厨，可能是具身智能最具确定性的商业落地方向之一。</p>
  <p>原因在于，这个场景同时具备几个关键特征。</p>
  <p>首先，它是全球共通需求。无论中国、北美还是东南亚，餐饮行业都面临人力成本上升与履约效率问题。</p>
  <p>其次，它的ROI足够清晰。只要能够降低错单率、减少人工、提升出餐效率，商家就愿意为此付费。</p>
  <p>更重要的是，相比家庭、养老等强调情感交互的场景，餐饮属于专业服务领域，决策链条更短，中小商家合作意愿更强。</p>
  <p>在接受36氪采访时，王栋表示，服务业本身占据全球GDP的巨大比例。如果能够在餐饮后厨这个高频场景中建立起真正可运行的具身方案，实现从模型到应用的系统性落地闭环，本身就价值巨大，并且也具备未来再向家庭厨房等更复杂的场景延伸的可能。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_24d121a07ea1430391f2b75c4cd8da30@5920579_oswg3235683oswg2560oswg1440_img_png?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">（图源/企业）</p>
  <p>相比不少公司优先做“通用具身世界模型”，元节智能更倾向于从真实场景中持续学习以逐步建立模型能力。</p>
  <p>王栋表示，“移动能力（Locomotion）经过七八年发展，其实已经基本解决了。现在行业真正的焦点，开始转向精细操作。虽然灵巧手距离真正成熟还有距离，但二指、三指夹爪已经出现大量成熟的工程化方案，可以支撑部分标准化任务落地。”</p>
  <p><strong>在这样的判断下，元节智能没有把重点放在重新发明机器人硬件，而是要做一套面向餐饮场景的“世界动作模型（World Action Model，WAM）”。</strong></p>
  <p>在王栋看来，VLA（Vision-Language-Action）路线过度依赖语言模块进行高层规划，但对视觉表征不足，而真实世界里的动作控制，本质上并不依赖语言。“人类真正的动作控制路径，其实没有那么强依赖language。更核心的问题，是视觉理解、物理理解，以及动作如何与真实世界建立映射。”</p>
  <p><strong>基于这一判断，元节智能在模型层面更强调探索融合视觉（Vision）与触觉（Touch）的“VT-WAM”（视觉-触觉世界动作模型）。</strong>王栋解释道：“视觉看得见物体，却看不见接触；触觉看不见全局，却看得见成败。视觉ground的是世界的几何侧面，触觉ground的是世界的物理侧面。VT-WAM再把这两类信息通过隐空间综合进一个能预判接触后果的‘世界-动作模型’。”</p>
  <p>世界模型不仅需要视觉感知能力，更重要的是理解真实物理世界中的规律与因果关系。他举例说，一个饮料杯是否装水、装得满不满、温度是冷是热，都会影响机器人抓取时的摩擦力、重心变化与操作稳定性。</p>
  <p>元节智能希望通过视觉、触觉等多传感器协同感知物体状态，并在模型中嵌入对液体晃动、重心变化等物理属性的因果理解，让机器人的动作不只是基于数据拟合，而是真正符合现实世界的物理规律，从而提升抓取与操作的稳定性和精细度。</p>
  <p>从技术架构来看，元节的系统大致分为三层：最上层是具身世界模型，用于形成对后厨环境的认知，并完成决策与动作规划；中层是任务编排与调度引擎，将认知结果转化为具体执行计划，并统一调度不同设备；底层则是自研核心部件与通用硬件本体的融合，确保系统能够在真实后厨长期稳定运行。</p>
  <p>这套架构背后的核心逻辑是：不是先造一个通用机器人，再去寻找应用场景，而是在一个足够高频、足够痛的场景里持续收集真实交互数据，反过来喂养世界模型，让模型在物理世界中越来越“聪明”。</p>
  <p>餐饮后厨每天都在重复大量高频操作——打包、分拣、搬运、烹饪、接驳——这些动作天然能够形成海量、多样化的真实世界数据，而这类数据很难单纯依靠仿真环境生成。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_e7f06f1a8782456ca22b457311ad3d08@5920579_oswg3348966oswg2560oswg1440_img_png?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">（图源/企业）</p>
  <p>具体落地路径上，元节智能目前选择从“外卖打包与接驳”切入。这是整个履约链路中出错率最高、标准化程度相对较高、同时又最容易量化价值的环节。</p>
  <p>“打包环节的��务范围清晰，场景可控，我们的路径是以商业价值为依据，先聚焦提升抓取精准度，做到可用可靠。”王栋表示，“站在商业视角，商家并不在意你的机器人像不像人，会不会跳舞，商家更在乎你到底能帮我干什么活。”</p>
  <p>目前，元节的方案是将高频、标准化动作交给端侧轻量化小模型执行，例如套餐装盒、封签等动作，以降低延迟与网络依赖；而云端大模型则主要用于处理异常情况，例如物料缺失、异物干扰等复杂场景，并通过KDS系统联动后厨人工补位。</p>
  <p>打包环节模型预计会在2026年内进入真实商家后厨进行规模化部署。</p>
  <p>在团队的设想中，未来模型能力会从打包这一单点环节切入，继续向更复杂的后厨操作延伸，包括分拣、配送接驳、烹饪协同，甚至逐步进入更广泛的服务业场景。</p>

- **Tags**: `vision`


---


## 191. 中信证券：管网更新东风起，钢管板块迎价值重估

- **Source**: [36kr](https://36kr.com/newsflashes/3835335100544130?f=rss)

- **Summary**: 36氪获悉，中信证券研报指出，此次《城市更新“十五五”规划》的核心意义在于：城市发展模式正式从增量扩张切换至存量提质，地下管网改造由“任务表述”升级为“36.5万公里量化指标”，同时配套“中央补助+专项债+REITs+社会资本”四轮驱动的资金来源框架，对钢管板块构成中期景气β。这标志着需求范式正式从地产后链条切换至公共更新，管道龙头沿着“项目获取—收入确认—产品结构升级—毛利修复”链条进入业绩与估值双修复通道。


---


## 192. 中信建投：算力等高频高速需求快速增长，电子级PTFE有望大规模应用

- **Source**: [36kr](https://36kr.com/newsflashes/3835309248247176?f=rss)

- **Summary**: 36氪获悉，中信建投证券研报称，PTFE材料因其主要特性包括优异的热稳定性、耐化学性、介电性能被称为“塑料王”。PTFE下游军工+服务器高速线缆+高速板三大需求均有望高速增长，随着英伟达新一代服务器Rubin ultra量产节点临近，产业内积极讨论使用PTFE材料作为正交背板的可能性，国内生益科技配合积极做验证。研报认为随着算力基建等引领的高频高速传输需求的持续增长，PTFE的下游领域有望被重新定义。


---


## 193. 8点1氪丨豆包将在6月下旬正式付费 ；韩国SK海力士工厂发生火灾；宇树科技IPO过会，王兴兴身家或超140亿

- **Source**: [36kr](https://36kr.com/p/3835278829008257?f=rss)

- **Summary**: <h2>今日热点导览</h2>
  <ul>
   <li>闲鱼回应读取用户手机内文物照片上架售卖</li>
   <li>赛力斯字节合作新品牌细节曝光：将推纯电、增程双动力</li>
   <li>英伟达推出NVIDIA DSX平台</li>
   <li>OpenAI官宣进军机器人赛道，短期内专注研发协助型机器人</li>
   <li>4月中国产汽车在韩国注册登记进口榜排第三，史上首超日本车</li>
  </ul>
  <h2>TOP 3大新闻</h2>
  <p><strong>豆包预计6月下旬正式付费，并加速打通抖音电商</strong></p>
  <p>5月初旬，豆包将推出付费订阅服务的消息，引发市场广泛讨论。随后官方回应：“豆包始终提供免费服务。在免费服务的基础上，我们也在探索推出更多增值内容，以满足不同用户的差异化需求。”</p>
  <p>据36氪独家了解，以上只是豆包商业化的预热动作。在接下来的季度中，豆包将持续推进商业化的落地。知情人士透露，豆包预计将在6月下旬正式上线付费内容，并于同期举行的Force大会上更新相关功能。之所以选择这一时间节点，是因为PC端与移动端仍需约一个月时间，完成基础功能与收费体系的适配改造。</p>
  <p>若进展顺利，豆包将于三季度进一步结合电商功能更新完善付费场景，并通过补贴为抖音商城进行引流，四季度进入运行期。</p>
  <p><strong>韩国SK海力士工厂发生火灾，造成对人体有害的氟气泄露</strong></p>
  <p>当地时间6月1日上午10时32分左右，位于韩国忠清北道清州市的SK海力士第四园区内，连接两个生产间的气体室发生火灾，自动喷淋系统在起火后随即启动，火势及时得到控制，但对人体有害的氟气发生泄露，7人被送往医院接受治疗。</p>
  <p>在有毒气体泄漏后，SK海力士立即疏散了相关工厂内的约3600名员工。之后于当地时间13时38分左右完成残留气体清除工作，经确认无异常情况后，重新开放全部工厂建筑，并宣布事件处置结束。SK海力士方面表示，工厂的生产设备运行未受影响，不会使生产中断；目前公司正在调查事故发生的确切原因。”（央视新闻）</p>
  <p><strong>宇树科技科创板IPO过会，拟募资42.02亿元</strong></p>
  <p>上交所官网显示，上交所上市审核委员会定于6月1日召开审议会议，审议宇树科技（首发）。宇树科技此次科创板IPO拟募资42.02亿元，拟用于智能机器人模型研发、机器人本体研发、新型智能机器人产品开发及智能机器人制造基地建设四大项目。</p>
  <p>截至目前，本周（6月1日到5日）将有3家公司IPO上会，为拟闯关科创板IPO的宇树科技（300674），创业板IPO的中塑股份，北交所IPO的杰锋动力。（证券时报）</p>
  <h2>大公司/大事件</h2>
  <p><strong>美股三大指数集体收涨，英伟达涨超6%</strong></p>
  <p>36氪获悉，6月1日收盘，美股三大指数集体上涨，道指涨0.09%，纳指涨0.42%，标普500指数涨0.26%。大型科技股跌多涨少，Meta跌超5%，特斯拉跌超4%，苹果、谷歌跌超1%，奈飞小幅下跌；Arm涨超15%，英伟达涨超6%，微软涨超2%。热门中概股涨多跌少，蔚来涨超6%，B站涨6%，小鹏集团涨超4%，腾讯音乐、拼多多涨超3%，爱奇艺涨超2%，微博涨超1%；理想汽车跌超3%，百度跌超2%。&nbsp;</p>
  <p><strong>谷歌拟筹800亿美元，伯克希尔100亿美元跟投</strong></p>
  <p>6月2日，谷歌母公司Alphabet(GO0G.0)正通过股权发行筹集800亿美元资金，其中包括与伯克希尔·哈撒韦公司达成的一项投资协议，旨在为其雄心勃勃的人工智能支出计划筹措资金。Alphabet在公告中披露，此次融资行动包括300亿美元的承销公开发行，以及400亿美元的“按市价发行”(ATM)交易。作为此次融资计划的一部分，伯克希尔·哈撒韦公司将通过私募方式认购价值100亿美元的股票，Alphabet将以每股351.81美元的价格向伯克希尔发行价值50亿美元的A类普通股，并以每股348.20美元的价格发行另外50亿美元的C类普通股。该公司在声明中表示：AI需求已超出公司现有供应能力。通过扩大投资规模，公司旨在扩展基础架构，从而为迎接未来的巨天增长机遇提供有力支撑。（金十数据）</p>
  <p><strong>智谱：建议A股发行并在科创板上市</strong></p>
  <p>36氪获悉，智谱公告，于2026年6月1日举行的董事会会议上，公司建议向中国相关监管机构申请配发及发行A股，并向上海证券交易所申请该等A股在科创板上市及准予交易。公告指出，建议A股发行数量占建议A股发行完成后公司总股本的2%至8%之间（不含因超额配股权获行使而将予发行的任何A股），即不少于9,098,838股且不多于38,768,964股新A股。预计建议A股发行全部为新股发行，原股东不公开发售股份。</p>
  <p><strong>黄仁勋宣布：联手宇树打造1.8米参考人形机器人</strong></p>
  <p>6月1日，英伟达首席执行官黄仁勋宣布，英伟达已与宇树科技合作，推出新一代人形机器人参考设计H2+，也被称为Isaac GR00T系统，以加速全球人形机器人行业创新。黄仁勋在演讲中表示，这套系统已经完成整体集成。机器人本体拥有31个自由度，每只机械手拥有25个自由度，整机身高约1.8米、重量约68公斤。（红星新闻）</p>
  <p><strong>闲鱼回应读取用户手机内文物照片上架售卖</strong></p>
  <p>5月30日，江苏网友顾女士发帖吐槽称，自己打开闲鱼APP后发现，账号待售页面竟出现了陕西历史博物馆镇馆之宝“唐鎏金舞马衔杯纹皮囊式银壶”，标价6000元，而整个上架过程由平台AI自动完成，她本人毫不知情。</p>
  <p>客服解释称，可能是她此前将照片上传至“闲鱼空间”，系统因此自动生成商品并上架。但顾女士表示，自己不记得上传过这张文物照片，而且即使曾误传到“闲鱼空间”，平台也不应在没有明确提示的情况下，自动将照片包装成商品并标价出售。她发现，系统不仅自动生成了价格，还配上了“整体包浆自然”“适合收藏或陈设摆件”等AI文案。</p>
  <p>闲鱼对此表示，闲鱼始终严守法律底线，坚决反对并积极配合国家机关打击文物违法交易。目前，闲鱼已接入国家文物局“中国被盗（丢失）文物信息发布平台”，可对820条国家级被盗文物数据进行智能比对；同时已对收藏领域72个高敏类目提升发布门槛，要求卖家明确勾选是否具备来源凭证。对于相关产品体验问题给大家带来的困扰，我们深表歉意。后续将尽快加强商品上架提醒和用户确认，避免类似误解再次发生。（上游新闻、中新经纬）</p>
  <p><strong>超1.4万人砸12亿抢购SpaceX代币，总认购资金高达1.77亿美元</strong></p>
  <p>今年4月，一款标榜能分享SpaceX上市收益、最低投资门槛仅100美元、且仅面向美国以外投资者的代币——preSPAX，在短短三天内吸引了超过1.4万名投资者涌入，总认购资金高达1.77亿美元（约合人民币12亿元）。</p>
  <p>然而，preSPAX投资者买到的并非SpaceX真实股权，也无法享受SpaceX分红与投票权。这款代币的性质及其发行人的风险，可能导致投资者“血本无归”。“100美元，即可押注SpaceX上市经济效益”，这让原本仅面向机构的pre-IPO投资，看似向普通投资者敞开了大门。</p>
  <p>4月18日，总部位于开曼群岛的私募股权投资与代币化公司Republic发行的代币产品preSPAX一经开放认购，便遭疯抢，仅3小时就吸引了4633人参与。截至4月21日认购期结束，共有14435名投资者参与，总认购金额达到1.77亿美元，较原定发行额度超额认购约2.9倍。（每日经济新闻）</p>
  <p><strong>黄仁勋表示AI未减少工作岗位</strong></p>
  <p>英伟达CEO黄仁勋在台北的GTC演讲中表示，“有用的AI”时代已经到来，现在token（词元）是利润单位，AI是GDP“生成器”，软件工程师的数量正在增加。人们谈论AI减少了工作岗位，这完全是胡说八道，实际上有更多软件工程师被雇用。（第一财经）</p>
  <p><strong>多家全国性银行今年不再报送数据，房地产贷款集中度管理进一步“放松”</strong></p>
  <p>记者近日从多家全国性银行了解到，2021年起执行的“商业银行房地产贷款‘五档两线’集中度管理制度”已进一步“放松”，有关部门去年底已不再要求专门上报相关数据。一家全国性商业银行对公业务负责人向记者证实，今年该行没有报送数据，因去年底有关部门曾口头传达相关数据不再报送。一家全国性商业银行负责贷款统计和管理的人士亦对记者表示，有关部门已经不再向银行提及房地产贷款占比的情况，“没再听说有相关要求”。（财联社）</p>
  <p><strong>梦露百年诞辰遗物首拍：精神科医生信件曝光其生命最后一天</strong></p>
  <p>今年6月1日是好莱坞传奇演员玛丽莲·梦露（Marilyn Monroe）的百年诞辰。趁此机会，她的一批珍贵遗物也于当天首次登上拍卖场。负责这次拍卖的海瑞得拍卖行（Heritage Auctions）推出的线上专场中，包含梦露生前的手写信、照片、诗作、水彩画、服饰及各类配饰等物件，有待价高者得。</p>
  <p>这批拍品大多来自梦露的好友、美国诗人诺曼·罗斯滕（Norman Rostwo'gen）及他的妻子赫达（Hedda Rosten）的个人收藏，起拍价在500美元到50000美元不等。其中，最贵的拍品是梦露的精神科医生拉尔夫·格林森（Ralph Greenson）写给罗斯滕的三封信件。最重要的一封写于1962年8月15日——距离梦露猝然离世仅11天，格林森医生在信中详细回顾了梦露生命最后一天的经过，以及她去世后数小时内的情况。（澎湃新闻）</p>
  <p><strong>俄政府出台临时禁令：6月1日起禁止出口航空煤油</strong></p>
  <p>当地时间6月1日，俄罗斯政府发布消息称，为保障国内燃料市场的稳定可靠供应，对航空煤油（包括在交易所交易中购得的煤油）实施临时出口禁令。该禁令自6月1日起生效，将持续至2026年11月30日。</p>
  <p>禁令不适用于以下情况：运输途中飞行器技术容器内的燃料、禁令生效前已报关的航空煤油批次，以及根据政府间协议的供应。（央视新闻）</p>
  <p><strong>赛力斯字节合作新品牌细节曝光：将推纯电、增程双动力</strong></p>
  <p>据媒体报道，赛力斯和字节跳动旗下火山引擎深度合作的新汽车品牌快要来了。6月1日，记者从知情人士处获悉，赛豆科技旗下首款车型预计今年内推出，或为跨界车，即介于SUV和轿车之间，并预计将推纯电+增程双动力。据前述知情人士透露，该车预计将在赛力斯凤凰工厂生产，后者目前已处于改线阶段。“赛豆科技相关车型主要与火山引擎合作车机交互大模型等，双方会定期交流等，智驾方案预计不会用华为乾崑。”前述知情人士向记者透露。（新浪财经）</p>
  <p><strong>行业内爆料称iOS&nbsp;28或迎来颠覆性升级</strong></p>
  <p>据行业相关爆料，目前iOS 28和iPadOS 28已经进入早期开发阶段，整个系统的内部开发代号为Bell，整套系统完全围绕iPhone 20的全新硬件特性量身打造，是苹果近年来规划层级最高、投入资源最多的一次软件升级，战略意义非同一般。</p>
  <p>从最新流出的开发计划信息来看，今年将要推送的iOS 27只是一次常规迭代，并不会有颠覆性的底层视觉升级，明年的iOS 28才是苹果的重头戏。（快科技）</p>
  <p><strong>存储器价格暴涨近1000%，供需紧张与AI需求激增</strong></p>
  <p>今年一季度，中国集成电路出口724.7亿美元，同比增长77.5%，其中存储器产品出口459.9亿美元，同比增长174.2%。业内人士表示，跟去年3月份比，存储器价格涨幅已经达到了将近十倍，甚至还有一些十几倍的增长，国产品牌价格和海外品牌有比较大的价差，价格是很有竞争力的。</p>
  <p>业内人士表示，存储器产品出口的爆发式增长，既有全球供需紧张的周期性因素，更有国内存储行业产业链升级、市场份额提升的产业结构性变革等因素。记者发现，在存储器出口金额激增的背景下，国产存储企业正经历一场从“规模扩张”到“技术深耕”的深刻转变。业内人士表示，这一轮AI驱动的“超级周期”，为国产存储行业提供宝贵的“利润反哺研发”窗口期，不少企业正抓住机遇，从“跟随者”向“并跑者”转变。（央视财经）</p>
  <p><strong>英伟达推出NVIDIA DSX平台</strong></p>
  <p>英伟达当地时间5月31日宣布推出NVIDIA DSX平台，为基础设施构建者提供创建AI工厂的完整行动指南。英伟达CEO黄仁勋表示：“借助DSX平台，你可以在不花一分钱的情况下对整个工厂进行模拟，在安装一个机架之前验证性能，并以生产级AI所需的可靠性运营。”（界面新闻）</p>
  <p><strong>OpenAI官宣进军机器人赛道，短期内专注研发协助型机器人</strong></p>
  <p>OpenAI CEO山姆·奥特曼在社交平台发布OpenAI Robotics招聘信息，称公司正在寻找杰出的全栈硬件、运营、系统及机器学习工程师，共同编程并制造对社会真正有用的机器人。奥特曼表示，人工智能应当能够在现实世界中帮助人类。短期内，OpenAI专注于研发能够协助技术工人建设未来基础设施的机器人；长远来看，公司设想未来的每个人都能拥有一个可以完成各种需求的个人机器人。奥特曼透露，OpenAI的世界模拟研究项目在过去一年中发展迅速，现演变为OpenAI Robotics。项目由阿迪亚·拉梅什领导，目前的进展十分迅猛，其根基在于机器人硬件研究与机器学习研究的深度融合与协同设计。（界面新闻）</p>
  <p><strong>宗馥莉名下娃哈哈广盛投资公司更名宏盛</strong></p>
  <p>36氪获悉，天眼查App显示，近日，杭州娃哈哈广盛投资有限公司发生工商变更，企业名称变更为杭州宏胜广盛投资有限公司。该公司成立于2001年6月，宗馥莉为法定代表人、执行董事、经理并全资持股该公司，注册资本8000万人民币，经营范围为实业投资。</p>
  <p><strong>小米汽车：2026年5月，小米汽车交付量持续超过30000台。</strong></p>
  <p>36氪获悉，小米汽车公布，2026年5月，小米汽车交付量持续超过30000台。</p>
  <p><strong>4月中国产汽车在韩国注册登记进口榜排第三，史上首超日本车</strong></p>
  <p>韩国进口车协会（KAIDA）6月1日发布数据显示，4月在韩新注册登记的进口车中，中国产汽车排名第三，史上首次赶超日本产汽车。数据显示，欧洲产以1.68万辆排名第一，其后依次为美国产（1.36万辆）、中国产（2023辆）和日本产（1974辆）等。中国产占比为6%，略高于日本产（5.8%）。（界面新闻）</p>
  <p><strong>中金：钨的新兴需求及战略属性日益增强，钨价有望企稳回升</strong></p>
  <p>36氪获悉，中金公司研报指出，2025年钨价行情启动，国内钨精矿价格自14.2万元/吨上涨至年底45.6万元/吨，累计+221%。进入2026年，国内钨价加速向上，在3月中一度突破100万元/吨。但是，今年2月中东冲突以来，霍尔木兹海峡通行受阻、交战双方互相攻击能源设施引发油价超预期上涨，加剧全球经济滞胀恐慌。这导致此前本就过快上涨的国内钨价迎来逆转，产业链出现抛售潮，下游观望情绪加重。今年5月国内白钨精矿价格下探至40.6万元/吨年内低点，较3月高点-61%。</p>
  <p><strong>国家统计局6月1日启动入户调查</strong></p>
  <p>近日，国家统计局发布公告称，将于2026年在全国范围内开展两次人口固定样本跟访调查。国家统计局决定于2026年在全国范围内开展两次人口固定样本跟访调查。调查结果将用于加强人口变动统计，服务人口高质量发展。入户调查于6月1日启动。（央视新闻）</p>
  <h2>AI最前沿</h2>
  <p><strong>字节跳动AI Agent平台扣子Coze正式上线3.0全新版本</strong></p>
  <p>36氪获悉，6月1日，字节跳动旗下AI Agent平台扣子（Coze）3.0全新版本正式上线。据了解，扣子3.0全新版本支持多人多Agent协作、金融、自媒体、医疗、法律、科研等行业技能包，以及一键加载、多端同步等。同时，Claude Code、Codex CLI、Openclaw等可一键接入。</p>
  <p><strong>牧原与阿里云达成AI战略合作</strong></p>
  <p>36氪获悉，牧原集团与阿里云达成AI战略合作。双方将依托牧原在畜牧行业积累的数据与专家经验，结合千问大模型与阿里云智算算力，共同打造智能养猪大模型，推动AI在饲料营养、种猪育种、养殖管理、兽医健康等核心领域的落地。目前，基于千问打造的AI应用"小牧助手"已将每批次约600头猪的健康检测耗时从20分钟大幅缩短至秒级，效率提升超百倍。</p>
  <p><strong>LobsterAI上线图片视频大模型矩阵</strong></p>
  <p>36氪获悉，国内大厂首个开源龙虾类产品LobsterAI（网易有道龙虾）近日宣布上线图片生成与视频生成能力，并一次性接入包括Seedream、Seedance、HappyHorse、MiniMax-Hailuo在内的模型。</p>
  <p><strong>鸿海和法国公司Bull将合作生产AI和云基础设施</strong></p>
  <p>据声明，Bull和鸿海科技集团（富士康）将共同制造人工智能AI和云基础设施。 该项目将涉及Bull位于法国昂热的工厂和富士康位于捷克帕尔杜比采的工厂。Bull在声明中表示：“为了在法国执行这项战略部署，该项目预计将涉及超过1.2亿欧元的初始投资”。（新浪财经）</p>
  <h2>上市进行时</h2>
  <p><strong>Anthropic称已秘密提交IPO申请</strong></p>
  <p>Anthropic周一表示，已向监管机构秘密提交了首次公开募股招股说明书，这是这家人工智能初创公司走向上市的重要一步。Anthropic在一份声明中表示：“这让我们在美国证券交易委员会完成审核后可以选择上市。拟议的首次公开募股将取决于市场状况和其他因素。”（新浪财经）</p>
  <p><strong>智享生物向港交所提交上市申请</strong></p>
  <p>36氪获悉，据港交所文件，6月1日，智享生物（苏州）股份有限公司向港交所提交上市申请书，独家保荐人为东兴证券（香港）。</p>
  <p><strong>上海福贝宠物用品股份有限公司向港交所提交上市申请书</strong></p>
  <p>36氪获悉，据港交所文件，上海福贝宠物用品股份有限公司向港交所提交上市申请书，独家保荐人为国金证券（香港）有限公司。</p>
  <p><strong>成都卡诺普机器人技术股份有限公司向港交所提交上市申请书</strong></p>
  <p>36氪获悉，据港交所文件，成都卡诺普机器人技术股份有限公司向港交所提交上市申请书，独家保荐人为国泰海通。</p>
  <h2>大公司财报</h2>
  <p><strong>美团：第一季度营收910.4亿元，同比增长5.6%</strong></p>
  <p>36氪获悉，美团发布2026年第一季度财报，财报显示，该季度营收910.4亿元，同比增长5.6%；经营亏损由上季度的161亿元减少至65亿元。一季度，美团核心本地商业实现收入641亿元，经营亏损环比收窄至20亿元；新业务收入270亿元，同比增长21%，经营亏损收窄至21亿元。一季度，美团研发投入70亿元，同比增长22%，占总收入的7.7%。</p>
  <h2>酷产品</h2>
  <p><strong>英伟达发布面向Windows系统个人电脑的新款处理器</strong></p>
  <p>英伟达正式进军个人电脑芯片市场，推出全新处理器，意在打破英特尔在该领域的垄断地位，并推动PC设备适配人工智能时代的发展需求。英伟达首席执行官黄仁勋在台北国际电脑展上表示，今年秋季起，戴尔、联想等主流PC品牌将陆续推出搭载RTX Spark超级芯片的笔记本及台式机。这款由英伟达联合联发科共同研发的产品，集成了处理器与显卡，可运行微软Arm架构版Windows系统。（财联社）</p>
  <p><strong>科技记者古尔曼：苹果更轻薄的Vision Air头显预计2028年末或2029年发布</strong></p>
  <p>科技记者古尔曼称，苹果在研发一款更纤薄、轻便的头显，作为售价3499美元的初代Vision Pro的迭代产品。这款新品最早要到2028年末或2029年才会发布。（财联社）</p>
  <p><strong>英特尔拟年底前推出新AI芯片，将使用更便宜内存与风冷技术</strong></p>
  <p>据报道，英特尔计划在今年年底前推出一款人工智能芯片，该芯片使用的内存和冷却技术比英伟达和AMD的同类产品更便宜。领导英特尔数据中心部门的Kevork Kechichian表示，该公司正“从基础入手”。其新款“Crescent Island”图形处理器旨在加速“推理”任务（即用户提出请求的阶段），而非模型训练——这是英伟达处理器占据主导地位的领域。（财联社）</p>
  <h2>投融资</h2>
  <p><strong>“无界进化”完成数千万元天使轮融资</strong></p>
  <p>36氪获悉，据晶泰科技消息，其深度孵化的AI生物企业“无界进化”（INFevo）已完成数千万元天使轮融资，由顺为资本、红杉中国与松禾资本共同参与。</p>
  <p><strong>“博登智能”宣布完成数亿元A+轮及A++轮融资</strong></p>
  <p>近日，“博登智能”正式宣布完成数亿元A+轮及A++轮融资，鼎晖百孚、清新资本、鲁信创投、深产投等多家知名机构联合参投。作为面向Physical AI时代的真实世界AI基础设施公司，博登智能深度布局具身智能、大模型与自动驾驶三大核心方向，构建起“真实世界场景网络、全自动化数据引擎、现实世界验证体系”三层能力生态。本轮融资将进一步推动博登智能核心技术平台升级、全球真实世界训练网络建设及顶尖人才集聚，加速“Train at Scale, Validate in Reality”战略落地。</p>
  <p><strong>“微光医疗”完成数亿元融资</strong></p>
  <p>36氪获悉，近日，“微光医疗”完成新一轮数亿元融资。本轮融资由中美绿色长三角和倚锋资本共同领投，中银资本、汇誉投资共同跟投。此次融资将重点用于公司核心产品的全球商业化布局，以及创新管线的研发、注册与临床推进，进一步夯实微光医疗在智能介入领域的战略布局。</p>
  <p><strong>“睿健医药”完成2.1亿元C1轮融资</strong></p>
  <p>通用型细胞治疗平台企业“睿健医药”近日宣布完成2.1亿元人民币C1轮融资，本轮融资由光合创投及杏泽资本联合领投。募集资金将主要用于公司核心临床管线推进、AI+化学诱导平台持续升级、规模化生产体系建设、全球临床开发及国际化商业合作布局。</p>
  <p><strong>整理</strong>｜徐嘉彤</p>

- **Tags**: `agent` `anthropic` `claude` `codex` `coze`


---


## 194. 首轮融资数千万美元、估值2.5亿美元，「Aippy」正在打造下一代AI游戏社区 | 36氪首发

- **Source**: [36kr](https://36kr.com/p/3834400181741440?f=rss)

- **Summary**: <p>36氪获悉，<strong>NADA AI团队开发的AI游戏社区「Aippy」，已于近日完成数千万美元首轮融资，本轮由歌未资本（Glowill Capital）投资，投后估值2.5亿美元。</strong>本轮资金将主要用于顶尖人才引进和欧美核心市场用户规模化增长。</p>
  <p>Aippy成立于2025年，由港股上市公司赤子城科技孵化，其创始人、CEO&nbsp;Evan (叶椿建）是赤子城联合创始人，并长期担任赤子城CTO，在海外社交、游戏领域有十余年深耕经验。目前团队规模接近30人，核心成员来自清华大学、美国西北大学、慕尼黑工业大学等国内外顶尖高校，覆盖算法、产品、运营等关键岗位。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_6bfbfcd3a065413d9cb6072dcaed7537@242988687_oswg408135oswg1200oswg657_img_png?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p class="img-desc">Aippy产品界面图</p>
  <p><strong>作为AI驱动的游戏创作与互动社区，Aippy定位于为年轻一代数字原住民打造“人人都能做游戏”的UGC平台，用户仅需用自然语言描述想法，AI即可在数分钟内生成可交互游戏。</strong>其他用户可以像刷短视频一样沉浸式体验平台内的UGC游戏，也能一键在原有作品基础上进行二创（Remix），融入个人创意后重新发布。</p>
  <p>据了解，Aippy最初诞生于AI工具方向的探索。2025年初Vibe Coding概念兴起时，Evan&nbsp;带领团队切入，但很快产品便做出关键战略转向，因为团队判断纯AI工具赛道天花板有限，不仅面临巨头厂商的竞争，也难以解决用户黏性和商业化两大核心问题。</p>
  <p>AI降低创作门槛后，普通用户的创造力有待释放，若能打造一个面向大众的AI游戏创作社区，市场空间远大于工具赛道。因此，团队果断放弃了纯工具方向，从年轻人熟悉的游戏品类切入，正式转向C端AI游戏社区，仅用数月便完成了产品验证。</p>
  <p><strong>截至目前，Aippy全球总下载量突破300万，月活跃用户近200万，</strong>在美国App Store评分为4.8分；平台UGC游戏作品总量突破200万，每日新增创作量较年初增长10倍。</p>
  <p>此外，用户日均使用时长较年初提升25%，DAU互动率接近50%；Discord核心社区已聚集1.5万名深度用户，形成了真实的创作者交流氛围。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_918d5ae54dbf458891c7344ebff0ee9c@242988687_oswg3369961oswg4001oswg2251_img_png?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">用户在 Aippy 中生成的游戏作品</p>
  <p>为降低普通用户的创作门槛，Aippy做了大量针对性产品优化：平台提供预设创意模板引导，AI会实时给用户延伸创作建议，避免用户面对空白页面卡壳；支持语音输入、AI生成素材、一键修复错误、预览调整等全链路创作工具，让整个创作流程都能在平台内完成，用户不需要跳转其他工具。</p>
  <p>核心的Remix二创机制进一步降低了创作门槛，用户看到喜欢的作品，可以直接在原有基础上修改融入个人创意，重新发布即可。这一机制让同一个创意源头能够衍生出数十个新版本，内容越丰富越能激发更多创作。</p>
  <p>市场策略方面，和很多同类项目追求快速扩张、全区域覆盖不同，<strong>Aippy坚持聚焦欧美等发达地区，保持社区调性。</strong></p>
  <p>NADA AI团队接受36氪采访时表示，选择聚焦欧美核心市场出于三点考量：第一，欧美用户对新奇的AI原生内容接受度更高，UGC创作者文化也更加成熟，与Aippy的模式天然适配；第二，欧美用户的内容付费习惯早已养成，不需要重新教育市场，早期验证商业模式的效率更高；第三，当前主流大语言模型对英文Prompt的理解和生成质量优于其他语言，能给用户更好的AI生成体验。</p>
  <p>这一策略也得到了数据验证：<strong>Aippy目前自然流量占比已超过30%</strong>，证明产品已经形成了自传播趋势，不需要完全依赖买量拉动。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_2581da3fe86b411092e44cf4b8d382f4@242988687_oswg773846oswg1400oswg900_img_png?x-oss-process=image/quality,q_90/format,jpg/interlace,1" /></p>
  <p class="img-desc">Aippy对话式创作Agent</p>
  <p>本轮融资后，Aippy将围绕两个核心方向发力，一是继续优化内容推荐与分发机制，提升用户使用体验；二是升级创作者成长体系和激励机制，与更多创作者共建健康、高质量的游戏内容社区。目前，<strong>NADA AI希望吸引更多高级的算法、Agent工程师，以及产品运营方向的顶尖人才。</strong></p>
  <p>对于AI&nbsp;互动游戏赛道，Aippy团队认为，AI的价值不是取代专业游戏开发者，而是释放普通用户的创造力，就像数码相机普及后没有取代专业摄影师，反而让摄影走进大众生活，AI也不会取代游戏公司，而是会开辟一个全新的互动娱乐市场，让每个普通人都能把想法变成可玩的游戏，让创意回归纯粹的乐趣。</p>
  <h4><strong>投资方观点：</strong></h4>
  <p>本轮投资方歌未资本Glowill Capital成立于中国香港，是⼀家面向全球的多策略、多市场资本平台，聚焦人工智能、量子计算、新能源、生物医药、半导体等全球高景气赛道。</p>
  <p>歌未资本相关负责人表示，投资Aippy主要基于两点判断：一是团队具备扎实的ToC互联网产品和海外市场运营经验，在社交、游戏等领域有深厚积淀，能力模型稀缺；二是看好赛道的成长空间，Aippy在“降低游戏创作门槛+社区生态打造”这个方向上跑在了前列。</p>

- **Tags**: `agent`


---


## 195. 豆包6月下旬正式付费，并加速打通抖音电商丨独家

- **Source**: [36kr](https://36kr.com/p/3834544830721671?f=rss)

- **Summary**: <p>5月初旬，豆包将推出付费订阅服务的消息，引发市场广泛讨论。其在苹果App Store中更新的付费订阅方案显示，豆包将推出四档收费标准：基础版、标准版、加强版、专业版。对应的月收费价格为：免费、68元、200元、500元；年收费价格为：免费、688元、2048元、5088元。</p>
  <p>随后官方回应：“豆包始终提供免费服务。在免费服务的基础上，我们也在探索推出更多增值内容，以满足不同用户的差异化需求。”</p>
  <p>据36氪独家了解，以上只是豆包商业化的预热动作。在接下来的季度中，豆包将持续推进商业化的落地。知情人士透露，<strong>豆包预计将在6月下旬正式上线付费内容，并于同期举行的Force大会上更新相关功能。</strong>之所以选择这一时间节点，是因为PC端与移动端仍需约一个月时间，完成基础功能与收费体系的适配改造。</p>
  <p><strong>据36氪了解，若进展顺利，豆包将于三季度进一步结合电商功能更新完善付费场景，并通过补贴为抖音商城进行引流，四季度进入运行期。</strong>这些动作，皆是为了面向2027年及更长期的商业化回报做准备。因此，2026年豆包将不会把付费用户的渗透率作为考察指标。</p>
  <p>2025年10月，豆包初步和抖音电商打通。用户可以通过和豆包的对话，获取商品信息和购物链接推荐。据前述知情人士透露，当时，字节曾在小范围测试豆包硬广能力，但由于用户体验问题，后续暂停了放量。目前，豆包采取的是优先响应用户问题，再在答案中穿插横条商品推荐的互动模式。</p>
  <p>前述知情人士表示，<strong>自2026年4月以来，用户对AI购物推荐的接受度较去年下半年有所提升，点击商品卡并看完详情页的转化率达3%以上。</strong>另一方面，豆包目前的用户增长已有所放缓。据36氪了解，增速放缓一部分也是字节有意为之的结果——昂贵的算力推理成本，使得字节在新一年减少了对豆包的推广投流。</p>
  <p>移动互联网产品的常规节奏是先烧钱圈用户，再做商户化，但AI产品的商业化显然更紧迫了。字节也不例外。</p>
  <h2><strong>01</strong></h2>
  <h2><strong>订阅是个好选择吗？</strong></h2>
  <p>据《彭博社》5月27日报道，字节跳动正在考虑投入最高700亿美元的资本支出，用于推进AI发展。而就在不到一个月前，《南华早报》5月9日援引知情人士报道称，字节已将其AI基础设施预算从去年的1600亿元人民币，上调至2000亿元人民币（约300亿美元）。持续加码的投入，也显示出字节正以前所未有的力度押注AI。</p>
  <p>全球AI军备竞赛仍在不断升温，但如何赚钱已成为摆在所有公司面前的现实问题。</p>
  <p>此前，36氪曾报道：尽管字节跳动2025年海外营收增长近50%，但由于对AI业务的巨大投入，整体净利润出现了超过70%的降幅（官方后澄清该降幅主要是国际会计准则的原因）。随着巨额资金的不断投入，迫使全球的科技公司，都很难继续停留在只谈技术理想、而不谈商业回报的阶段。</p>
  <p>当前市场上，<strong>AI商业化落地最常被提及的三种路径，分别是订阅制、广告变现以及To&nbsp;B模型服务。其中，订阅制是最先被切入的商业化场景。</strong></p>
  <p>回看海外市场，头部AI产品实际上很早便开始探索付费模式。2022年11月上线后，ChatGPT仅用了约两个月时间，便在2023年2月推出每月20美元的ChatGPT Plus订阅服务。随后，Anthropic也在2023年9月推出Claude Pro，同样定价20美元/月。相比之下，国内Chatbot产品过去较长时间仍停留在免费阶段，依旧延用“烧补贴抢占用户量”的竞争思路。</p>
  <p>作为国内首个计划转向订阅的Chatbot产品，豆包的确拥有更深厚的用户基础。据AICPB产品榜全球总榜显示，豆包App端2026年4月的月活跃用户数约为3.36亿，环比增长1.51%，仅次于ChatGPT，排名全球第二。</p>
  <p>问题在于：豆包能在Chatbot产品中迅速跻身头部，靠的并非模型本身的智能程度，更多是产品层面的易用性。加上抖音流量池强大的输送能力，让豆包率先在下沉市场中抢占了用户心智。</p>
  <p>事实上，国内用户对单一AI产品并没有太强的忠诚度。据《晚点LatePost》报道，目前豆包的单用户日均使用时长为10分钟。在没有显著的技术壁垒、竞争对手又依旧免费的情况下，开放订阅可能会造成用户的流失。</p>
  <p>不过，抛开产品本身不谈，订阅制本身也并非AI商业化的最佳路径。</p>
  <p>即便是在付费意愿更强的西方市场，订阅所能带来的收益转化也依然有限。为了增加付费用户，ChatGPT在2026年推出了更便宜的ChatGPT Go，每月只需8美元。这使得它的付费用户人数从去年年底的4700万，增加至第一季度的5500 万。但据《The Information》报道，ChatGPT第一季度的周活跃用户平均约为9.05亿。<strong>换言之，即便是全球MAU规模最大的Chatbot产品，在推行订阅制三年后，付费转化率也仅为6.1%。</strong></p>
  <p>付费人数难以提升，在于AI订阅模式自身的两难。</p>
  <p>一方面，在竞争激烈、产品高度同质化的情况下，没有任何一家模型公司敢于彻底取消免费服务。对大多数轻度用户而言，免费版足以满足他们日常问答、资料查询的基础需求。另一方面，在Token依旧昂贵的当下，若需要AI来完成更复杂的任务，目前需要支付的最高价格则达到200美元/月（约1400元人民币）。而愿意为此长期买单的，本就是少数人。</p>
  <p>更关键的是，即便定价如此之高，AI公司也未必赚钱。2025年6月，Sam Altman曾公开在社交平台X上表示，OpenAI在200美元/月的ChatGPT Pro的订阅上亏钱了。<strong>这导致了一个悖论——定价太高，用户不愿付费；定价太低，又难以覆盖算力成本。</strong></p>
  <p>因此，C端订阅在当下更多只是“赔本赚吆喝”。想要真正实现商业回报，各大科技公司仍需探索更多商业化场景。比如，OpenAI就在今年2月，开始在ChatGPT中逐步上线并推广广告业务。</p>
  <h2><strong>02</strong></h2>
  <h2><strong>AI商业化如何落地</strong></h2>
  <p>在经历长时间碰壁后，眼下，科技巨头们似乎终于找到了通往商业化的最佳路径——面向企业出售模型能力。企业无需自己训练模型，只要通过API接入，就能直接调用科技公司研发出来的AI模型能力，并按Token用量付费。</p>
  <p>比起付费意愿有限的个人用户，企业完全有能力、也有意愿使用这些AI工具，来试图推动组织内部的经营提效。<strong>更重要的是，To B模式下，企业通常按照Token调用量持续付费，而非包月订阅</strong>（如前所述，面向普通用户的包月订阅价通常无法覆盖算力成本）。对模型厂商来说，这显然是笔稳赚不赔的好买卖。</p>
  <p>Anthropic的利润增长已经充分说明了这一点。据《华尔街日报》5月21日报道，Anthropic第二季度的收入预计将增长逾一倍，达到109亿美元，并可能实现5.59亿美元的营业利润。<strong>在行业内仍在大规模烧钱补贴的阶段，Anthropic是第一家接近盈利的大模型公司。</strong>其主要收入来源是企业和初创公司的API调用。截至2025年10月，Anthropic拥有超过30万家企业客户，约占总收入的80%。</p>
  <p>国内的互联网大厂也已相继在ToB市场布局和发力。和Anthropic等AI初创公司不同，互联网大厂坐拥云计算能力：一方面靠模型API变现，这类将A模型封装为云服务对外输出的形态，就是MaaS（模型即服务）；另一方面模型调用带来的算力消耗，又可能拉动自家云业务增长。</p>
  <p>在这场新的AI云竞争中，字节旗下的火山引擎增长最快。5月7日，国际数据公司IDC公布的数据显示，2025年，中国企业在公有云上的大模型调用量相比去年暴增16倍。其中，接近一半的调用量都发生在火山引擎平台上，其市场份额达到49.5%，位居行业第一。</p>
  <p>阿里也在2025年11月末启动了“百炼战役”，试图追赶AI云上的市场份额。据阿里2026年Q4财年的财报数据显示，阿里的“百炼平台”（阿里云的MaaS平台）客户数同比增长8倍。这也说明，阿里正在快速补强其AI To B市场能力。</p>
  <p>除了To B市场带来的显性收益外，字节也在积极利用AI能力，来为自家的主营业务赋能。</p>
  <p>以字节旗下的王牌AI模型seedance 2.0为例，其生视频能力进一步推动了短剧市场的创作热潮。有短剧行业人士告诉36氪，随着视频创作门槛的不断降低，行业内涌入了大量新玩家。他们背景各异，来自游戏、潮玩，甚至传统制造业。此外，单部短剧制作成本的降低，也让制作公司能够在总预算不变的情况下，生产更多剧集。</p>
  <p><strong>创作者数量的激增，和制作成本的降低，双双推高了AI短剧的供给量。而在当下，短剧获取播放量最核心的方式，依旧是抖音侧的投流。</strong>一位短剧投流人士透露，目前AI短剧在字节巨量引擎体系内的日耗峰值约为1.2亿元。</p>
  <p>负责短剧发行的嘉书科技创始人王小书告诉36氪，其所在公司去年每天的投流消耗仍只有几十万元，而今年已达数百万元，增长约10倍。与此同时，短剧出品方在巨量引擎上的ROI通常仅为1.03至1.07。这意味着，每投入100万元广告费用，能获得约3万至7万元利润。</p>
  <p>可见，在短剧行业不断膨胀繁荣的背后，真正稳定受益的，更多仍是平台本身。</p>
  <p><strong>AI+电商购物或将成为字节下一个发力场景。</strong>2026年3月30日，据《界面新闻》报道，豆包的购物支付功能正在进行灰度测试。该功能支持用户在豆包APP内直接下单商品并完成支付，无需跳转至抖音商城。</p>
  <p>豆包不是第一个试图打通AI购物闭环的AI产品。今年5月11日，阿里千问就已正式接入淘宝，打通了AI购物功能。去年9月，ChatGPT也曾推出过“即时结账”（Instant Checkout）功能，试图引导用户直接在AI对话框中完成下单与支付。但今年3月，OpenAI已经取消了这一功能。原因在于，打通技术路径容易，但想打通背后完整的电商生态体系却很难。</p>
  <p>豆包与千问的优势在于，它们背后分别站着抖音商城与淘宝这两大成熟电商体系。无论是商品库、商家生态、支付还是履约能力，都早已存在。这也让AI购物这件事，在理论上看起来更加成立。</p>
  <p>但即便如此，AI购物仍需面对两大核心拷问。<strong>一是，AI购物本身是否是真需求？</strong>春节期间，千问曾投入30亿元红包，请用户用AI点奶茶，试图培养消费者通过AI完成消费决策的习惯，36氪也曾对此进行报道。但从结果来看，大多数用户并未形成长期留存。而相比点外卖，购物本身又是一个更复杂、更依赖比较与决策的场景。</p>
  <p><strong>二是，消费者是否真的会信任AI的商品推荐？</strong>随着AI搜索与推荐能力的重要性提升，部分商家已经开始通过GEO（生成式引擎优化）等方式，影响大模型对信息的抓取与排序。今年315晚会上被曝光的GEO产业链，也曾引发广泛讨论。当AI推荐开始受到商业投放与利益关系的影响后，消费者究竟会将其视为客观建议，还是新的广告入口，仍有待观察。</p>
  <p>（周鑫雨对本文亦有贡献）</p>
  <p><strong>编辑&nbsp;|&nbsp;乔芊 杨轩</strong></p>
  <p class="editor-note">本文来自微信公众号<a href="https://mp.weixin.qq.com/s/2yBSevOAAyRuE24aiICLAQ" rel="noopener noreferrer" target="_blank">“36氪未来消费”</a>，作者：肖思佳，36氪经授权发布。</p>

- **Tags**: `anthropic` `chatgpt` `claude` `gpt` `openai`


---


## 196. 量坤科技获数亿元天使轮融资，AI4S急需量子级精度数据 | 36氪独家

- **Source**: [36kr](https://36kr.com/p/3826034537223043?f=rss)

- **Summary**: <p><strong>「暗涌Waves」独家获悉，量子计算公司「量坤科技」近日完成数亿元人民币天使轮、天使+轮融资。本轮系列融资由英诺天使基金领投，国汽投资、北工投资、BV百度风投、水木清华校友基金、明势创投等多家机构参与投资。光源资本担任独家财务顾问。</strong></p>
  <p>这笔融资背后，是一个逐渐清晰的判断：<strong>AI for Science需要量子计算。</strong></p>
  <p>AI可以学习规律，但模型能力上限，受制于它所见过世界的“分辨率”。在化学、材料与医药等研发场景中，如果底层数据的精度不够，模型预测结果也会显著受限。</p>
  <p>量子计算，天然适合模拟分子结构、化学键等体系。<strong>作为一种高精度求解器，它有可能输出更接近物理世界规律的计算结果；计算产出的量子级高精度数据，也是AI4S提升模型表现的一个关键。</strong></p>
  <p>量坤科技成立于2026年1月，创始人吕定顺在华为、字节跳动AI4S Lab工作七年，带领团队探索量子计算的能力边界。再往前，他是清华大学最早一批量子计算方向博士，深度参与基于离子阱量子计算系统的搭建。</p>
  <p>过去，凭借“硬件不足，软件先行”的路径，吕定顺在大厂拿到过许多结果。在他看来，量子技术、AI和高性能计算融合的异构智算平台，能够在应用层，最大化有限量子算力的价值。</p>
  <p>这位年轻的理工科博士，一直想<strong>用量子计算解决真实世界的大问题</strong>。在量子计算硬件技术路线尚未收敛之际，他没有“卷”入硬件创业的热潮，而是选择了硬件之上的算法和软件平台，把量子算法、AI模型和行业workflow封装成可调用的科学智能体，连接量子计算机与AI4S应用需求。</p>
  <p>吕定顺说话语速很快，近两小时的访谈里，说了15次“exciting/兴奋”。在华为第一年，打破谷歌“量子霸权”叙事的研究，没有让他很exciting。但用AI在高温超导相关模型计算中实现SOTA，令他兴奋；遇到敢挑战Google、IBM，能打硬仗的人，他也会兴奋。</p>
  <p>目前，量坤科技团队已有近40人，集聚了量子、AI、高性能计算方向的前沿人才。在吕定顺看来，“团队是创始人内心认知的映射，当深度理解量子计算这一系统工程，就知道该如何招募团队。人才最核心的是心气儿要足。”</p>
  <p>为什么AI4S需要量子计算？算法和操作系统层的创业机会有多大？未来量子计算会成为新的算力解法吗？以下是我们与吕定顺的对话（经编辑）：</p>
  <h2><strong>一、来时路</strong></h2>
  <p><strong>「暗涌」：“量子霸权”为什么令人震撼？作为清华第一批量子计算专业博士，你为什么坚定走向了工业界？</strong></p>
  <p><strong>吕定顺：</strong>2019年谷歌发布了包含53个可用量子比特的处理器，只用200秒就完成了一项研究；并宣称，同样的任务，用当时最强经典计算机需要算1万年。这就是“量子霸权”的来由。</p>
  <p>后来我们在华为做了一年，用百卡级传统GPU做模拟，通过算法优化验证经典计算机根本不需要1万年，几个月甚至几天就能算出来。这一研究可以说打破了谷歌量子霸权。</p>
  <p>但完成这项工作后，我没有特别exciting。因为量子计算机还在往前发展，Scaling（指数级规模扩展）摆在那里。53比特还能追赶，往后60比特、100比特，经典超级计算机很难再跟得上。</p>
  <p>我更关心的是，当量子硬件能力继续向上，量子计算到底能解决哪些真实世界问题？解决的问题能不能更大？量子计算是系统性工程，所以我很坚定地选择去工业界。</p>
  <p><strong>「暗涌」：在华为期间，你如何寻找量子计算的真实应用场景？</strong></p>
  <p><strong>吕定顺：</strong>量子计算机是一把锤子，要找到合适的钉子。</p>
  <p>除了随机线路模拟，还有两段探索经历。一是化学和材料科学模拟。量子计算机本身是微观量子体系，用它模拟另一个量子体系顺理成章，比如材料化学。进入工业界前，我没有研究过化学，就花三个月读计算化学等文章，再写算法、做复现。后来我们把量子化学模拟推到了28比特，这也是当时业界最大规模的模拟。</p>
  <p>另一段是做组合优化问题，比如最大切割、网络流量优化等。在量子计算机算力不高的情况下，我们基于QAOA（量子近似优化）算法做降维化简，最终用不到20比特的量子计算资源，模拟出了10万比特的业务规模。</p>
  <p><strong>「暗涌」：什么时候开始更聚焦于AI4S场景？“混合异构计算”这一平台思路是怎么形成的？</strong></p>
  <p><strong>吕定顺：</strong>在字节，最开始我们依然沿着“量子计算实用化”的逻辑。<strong>如果量子计算机长期只有20-50比特，怎么解决真实的大问题？</strong></p>
  <p>后来我发现“量子嵌入”是很好的思路，简单来说就是好钢用到刀刃上。它通过计算任务分解，用量子计算机解决最核心、最复杂的矛盾，其他次要部分用经典计算机算，从而在计算规模、精度、成本实现平衡。</p>
  <p>比如：眼前这个会议桌上，最重要的特征是摆了两台电脑，其他部分都相似，那我们就用量子计算机去算“电脑”部分。具体场景上，我们选择了电子结构复杂、传统算法难突破的强关联材料做研究，像氧化镍等过渡金属氧化物。</p>
  <p>随着AI大语言模型能力爆发，团队思路更加侧重应用。原来是拿着量子计算机这锤子找钉子；后来是只要能解决science问题，AI、量子计算、经典算法一起用。</p>
  <p>围绕化学和材料，我们探索了三种路径：多尺度量子计算化学模拟，把原需上万比特的问题，转换成只需20量子比特；将量子计算机作为高精度求解器，为AI4S模型提供高质量数据。基于GPU的量子嵌入算法，不依赖于量子硬件能力提升；还有纯基于神经网络量子态来求解物理问题，既作为问题求解器，也作为数据合成器。</p>
  <p><strong>「暗涌」：你很在意解决的问题够不够“大”。做这些应用探索时，最重要的是什么？</strong></p>
  <p><strong>吕定顺：最重要的就是“选题”，要找到一个足够有影响力的问题。</strong></p>
  <p>后面我们选择了“高温超导”，这是凝聚态物理领域很关注的问题，普通人也有感知。借助AI神经网络，我们在高温超导的Hubbard模型计算上取得了SOTA。</p>
  <p>这让我挺兴奋。与传统计算范式相比，我们的算法在小数点后第二位就已经显示出优势，既往学界都在PK小数点第四位。</p>
  <p>这个AI模型也不是传统的Data-driven算法，本质是基于“变分原理”解极复杂的薛定谔方程，通过不断优化降低Loss，求出真正的基态解。从第一性原理来看，它可以拓展到化学、材料等很多问题。</p>
  <p>一开始这方法消耗的计算资源很大，我们紧接着又做了算法和框架改进，极大降低了算力需求，让更多科研团队能参与进来。</p>
  <h2><strong>二、正当下</strong></h2>
  <p><strong>「暗涌」：在量子计算这个系统工程里，如何理解你们的卡位？</strong></p>
  <p><strong>吕定顺：</strong>量子计算产业，很多公司在做量子计算机硬件，解决基础的算力问题。最上面的应用层需求也很旺盛，用户想把量子计算、AI用于解决真实问题，比如半导体材料、化学材料、新药分子研发等。</p>
  <p>但硬件算力层和应用层中间，算法、软件工具，其实是缺失的。量子算力的操作系统，正是我们想卡住的位置。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260529/v2_ab011042319d471b9d92c044351ceb7d@5452796_oswg151062oswg1662oswg762_img_png?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>
  <p class="img-desc">图源：量坤科技</p>
  <p><strong>「暗涌」：如何理解做中间算法、工具层的技术壁垒？为什么你选择了算法与操作系统端的创业机会？</strong></p>
  <p><strong>吕定顺：</strong>中间层，不是简单地把已有算法程序化。特别是现在量子计算机硬件资源还不丰富。</p>
  <p>不丰富，意味着不是所有算法路径都能完成任务。因为量子计算的误差会累积，只有对算法做充分优化，让路径足够短，才可能把有限的量子算力榨出来，最大限度地用起来。</p>
  <p>这跟在GPU上运行算法不同。GPU上算法差一些，效率低几倍也能跑，无非成本高；但量子计算里，如果算法效率差了5倍，可能根本跑不起来。这是0和1的区别。</p>
  <p>所以算法层的壁垒，在于能不能巧妙地设计和改造算法。这套算法和操作系统平台建好，还可以不断扩充功能，逐渐拓展成算法和工具平台。</p>
  <p><strong>「暗涌」：目前量子计算的产业图景里，哪些是你们想要服务的用户？</strong></p>
  <p><strong>吕定顺：</strong>第一类是本身就有量子计算需求的客户，比如国央企、科研院所等。他们需要培育量子计算能力、迭代量子算法。这类通常会从工具出发，把问题分解成量子算法，再运行到对应的量子计算机上。</p>
  <p>第二类是有明确研发需求的产业客户，比如半导体材料、新药研发等企业。用户并不关心底层算力是不是量子计算机，更关心问题能不能解决，成本效率如何。求解路径上，他们可能会用AI算法、量子算法，也可能用多分辨量子-经典混合算法。（混合算法，即把最难、最核心的交给量子计算，其他用神经网络、经典算法或其他精确算法处理）</p>
  <p>量子计算机厂商，其实也是我们的合作和服务对象，很多公司聚焦硬件的演化，操作系统、算法工具和应用生态，需要专业的团队和长期投入。合作方式上，比如将操作系统、算法平台与硬件打包销售，一起卖算力，或卖整机加操作系统等。</p>
  <p><strong>「暗涌」：现在AI4S公司很多，融资也很热。为什么一定需要量子计算？</strong></p>
  <p><strong>吕定顺：</strong>纯AI for Science视角来看，AI是一种解决方案，量子计算也是一种解决方案。除了计算速度快（量子加速），精度也是量子计算的一个优势。</p>
  <p>很多材料、化学问题需要高精度求解，纯AI模型非常依赖训练数据质量，比如结合能预测，如果底层数据精度不够，模型结果也会受限制。传统DFT方法本身也有精度边界，且依赖泛函选择。</p>
  <p>高精度计算在GPU上也可以做，但往往受显存限制，只能处理较小规模体系。量子计算虽然现在规模还不大，但在精度上有优势，未来有机会把高精度求解扩展到更大体系。</p>
  <p><strong>「暗涌」：针对这几类客户的需求，你们如何交付并完成商业化？</strong></p>
  <p><strong>吕定顺：</strong>我们交付的其实是将量子计算、AI、经典计算和行业工具等封装后的能力。交付形式很多：CRO式解决方案、高精度数据合成、workflow、云访问入口等都可以。</p>
  <p>早期以项目制为主，后续会沉淀项目经验，以标准化的科学发现云服务平台服务用户。未来在同类大场景，可能这套系统95%的能力可以标准化，只有小部分需要定制。</p>
  <p>其实，我们希望能把中间环节抽象掉。量子算法也可以抽象成skill，用户能够通过自然语言调度多种skill，构建复合函数去求解。</p>
  <p><strong>用户只需带着问题来，用户端入口可能就是agent系统。</strong>他可以不关心底层用谁家的量子计算机，甚至不操心调用哪种算法。就像今天用大模型，用户不关心背后是谁家的硬件，只关心输出质量、Token效率。</p>
  <p><strong>「暗涌」：AI时代，算力和能耗焦虑长期存在。量子计算的发展，会是算力新解法么？</strong></p>
  <p><strong>吕定顺：</strong>AI 和量子都是具备“完备性”的求解器，它们之间能双向赋能。AI for Quantum已经聊了很多，AI可帮助构建更好的量子计算机和算法，放大量子计算能力。</p>
  <p>反过来，Quantum for AI也有几层意义。首先，量子计算的一些insight，可能启发AI算法设计；其次，量子计算机作为高精度求解器，产生的高质量、差异化数据，会成为未来增强AI模型的关键。</p>
  <p>更长远看，今天我们可以在GPU、FPGA上部署模型，未来理论上也可能在量子计算机上部署量子版大模型。到了那个阶段，AI面临的算力和能耗问题，可能会出现新的解法。</p>
  <p>但现在还没有到那一步。量子硬件还在发展，技术路线也没有完全收敛，更现实的情况是在现有硬件条件下，将量子计算、AI算法和经典计算等结合起来，以量子突破精度天花板，以AI重塑效率边界，推动难而重要的科学问题求解。</p>
  <p>这也是我们对现阶段的定义：“第四范式++Science”。</p>
  <h2><strong>三、打硬仗</strong></h2>
  <p><strong>「暗涌」：量子计算、AI4S需要很多高阶人才，你们招人难么？</strong></p>
  <p><strong>吕定顺：</strong>我们现在已经进入了招人的良性循环，现在团队接近40人。AI方向，有全国物理、化学竞赛集训队背景的人才；高性能计算，也有清华的特奖选手、天才少年；工程化方面，有大厂出来的技术骨干。</p>
  <p>量子计算、AI4S是一个系统工程，各个方向都要有足够强的人，不能出现明显短板。</p>
  <p><strong>「暗涌」：刚创业四五个月，为什么能招到这么多人才？</strong></p>
  <p><strong>吕定顺：</strong>我们有招人的方法论。除了学术界的合作网络，我觉得，团队很多时候是创始人内心认知的映射、能力的延伸。如果创始人对整个系统的认知足够深，清晰地知道需要延伸、补足哪些能力，就可能配到很强的团队。</p>
  <p><strong>「暗涌」：有怎样特质的人，更容易让你觉得磁场相合？</strong></p>
  <p><strong>吕定顺：</strong>前几天我去清华做分享，有个问题是：AI时代，人才最重要的能力是什么？大家有提到定义问题的能力、批判性思维。在我看来，最重要的是心气儿，是你敢不敢去打胜仗。在量子计算领域，面对IBM、谷歌的顶尖团队，你觉得自己能不能打得赢。畏首畏尾的人，不会让我觉得兴奋。</p>
  <p><strong>「暗涌」：这很华为。</strong></p>
  <p><strong>吕定顺：</strong>字节也是一样，强调韧性。打硬仗、打胜仗，需要韧性。没怎么失败过的人，反而不敢打仗，失败会让他们背上包袱。</p>
  <p>我们处在一个开放的世界，研究、商业都是开放目标，要敢于挑战难题。量子产业直接招到对口的人确实难。组队方面，既往我有很多经验。我们不一定最关注专业背景，反而看重自我驱动力。</p>
  <p>如果动力够强，进入团队和这个环境，我们可以从0到1，快速把他带到业界高水平，然后为团队做贡献。我们提供了很有竞争力的薪酬，来了可以不操心钱，主要就操心能不能把事情做起来。我们也会协调解决优秀员工的北京落户问题。</p>
  <p>最关键是你对这件事是否有信念、愿不愿意折腾、眼里有没有光。</p>

- **Tags**: `agent` `google`


---


## 197. 氪星晚报｜中国国新等在杭州成立创业投资基金，出资额10.01亿；天津人工智能传感器产业园正式开园，首批10家企业集中签约；浙江：拟实施“星火计划”培育未来产业行动，加速量子技术产品规模化应用

- **Source**: [36kr](https://36kr.com/p/3834354415347337?f=rss)

- **Summary**: <h2><strong>大公司：</strong></h2>
  <p><a href="https://36kr.com/newsflashes/3834374932047745" rel="noopener noreferrer" target="_blank"><strong>中通快递在广州成立新物流公司，注册资本5亿</strong></a></p>
  <p>36氪获悉，天眼查App显示，近日，广州中竞物流有限公司成立，法定代表人为范嘉玮，注册资本5亿人民币，经营范围包括国内货物运输代理、机械设备租赁、计算机系统服务等。股东信息显示，该公司由中通快递股份有限公司全资持股。</p>
  <p><a href="https://36kr.com/newsflashes/3834326949553800" rel="noopener noreferrer" target="_blank"><strong>OpenAI官宣进军机器人赛道，短期内专注研发协助型机器人</strong></a></p>
  <p>OpenAI CEO山姆·奥特曼在社交平台发布OpenAI Robotics招聘信息，称公司正在寻找杰出的全栈硬件、运营、系统及机器学习工程师，共同编程并制造对社会真正有用的机器人。奥特曼表示，人工智能应当能够在现实世界中帮助人类。短期内，OpenAI专注于研发能够协助技术工人建设未来基础设施的机器人；长远来看，公司设想未来的每个人都能拥有一个可以完成各种需求的个人机器人。奥特曼透露，OpenAI的世界模拟研究项目在过去一年中发展迅速，现演变为OpenAI Robotics。项目由阿迪亚·拉梅什领导，目前的进展十分迅猛，其根基在于机器人硬件研究与机器学习研究的深度融合与协同设计。（界面）</p>
  <p><a href="https://36kr.com/newsflashes/3834311906698889" rel="noopener noreferrer" target="_blank"><strong>正泰南尔获评2026浙江省青年科技型企业家</strong></a></p>
  <p>近日，2026浙江省科技型企业家选育推荐结果名单公布，正泰集团董事、集团研究院执行院长、正泰电器副总裁南尔获评“2026浙江省青年科技型企业家”。本次活动还将为入选者量身定制《浙江省科技型企业家支持包（2026版）》，围绕高端智力资源对接、重大科技基础设施参与、真实应用场景开放、揭榜攻关、国际交流、科技奖项推荐及金融服务等方面提供支持。</p>
  <p><a href="https://36kr.com/newsflashes/3834259289564807" rel="noopener noreferrer" target="_blank"><strong>鸿海和法国公司Bull将合作生产AI和云基础设施</strong></a></p>
  <p>据声明，Bull和鸿海科技集团（富士康）将共同制造人工智能AI和云基础设施。 该项目将涉及Bull位于法国昂热的工厂和富士康位于捷克帕尔杜比采的工厂。Bull在声明中表示：“为了在法国执行这项战略部署，该项目预计将涉及超过1.2亿欧元的初始投资”。（新浪财经）</p>
  <p><a href="https://36kr.com/newsflashes/3834196724835971" rel="noopener noreferrer" target="_blank"><strong>网络餐饮新规实施首日，淘宝闪购依规联合多地监管部门完成首批外卖商户打标</strong></a></p>
  <p>网络餐饮新规6月1日起正式实施。淘宝闪购与北京、上海、安徽、南昌、成都、盐城、泰州、汕尾等地合作，根据市场监管部门推送的名单完成了首批“无堂食”外卖商户打标。当日，平台商家版客户端内已支持商家提报“无堂食”“可堂食”“明厨亮灶”等标签，经平台核验后予以展示。淘宝闪购今年以来推动6万餐饮商户完成合规整改，与各地监管部门的食安治理政企协作也持续取得进展。</p>
  <p><a href="https://36kr.com/newsflashes/3834363161355906" rel="noopener noreferrer" target="_blank"><strong>牧原与阿里云达成AI战略合作</strong></a></p>
  <p>36氪获悉，牧原集团与阿里云达成AI战略合作。双方将依托牧原在畜牧行业积累的数据与专家经验，结合千问大模型与阿里云智算算力，共同打造智能养猪大模型，推动AI在饲料营养、种猪育种、养殖管理、兽医健康等核心领域的落地。目前，基于千问打造的AI应用"小牧助手"已将每批次约600头猪的健康检测耗时从20分钟大幅缩短至秒级，效率提升超百倍。</p>
  <h2><strong>投融资：</strong></h2>
  <p><a href="https://36kr.com/newsflashes/3834250804602505" rel="noopener noreferrer" target="_blank"><strong>中国国新等在杭州成立创业投资基金，出资额10.01亿</strong></a></p>
  <p>36氪获悉，天眼查App显示，近日，国新钱江创业投资基金（杭州）合伙企业（有限合伙）成立，执行事务合伙人为国新国同（杭州）股权投资有限公司，出资额10.01亿人民币，经营范围为创业投资。合伙人信息显示，该基金由中国国新控股旗下国新国同（杭州）股权投资有限公司、杭州上城领航创业投资有限公司、杭实智投（杭州）产业投资基金合伙企业（有限合伙）、国新创投基金（杭州）合伙企业（有限合伙）共同出资。</p>
  <p><a href="https://36kr.com/newsflashes/3834192173737859" rel="noopener noreferrer" target="_blank"><strong>追觅开放融资，单笔投资门槛最低3.5亿，Pre-IPO轮投前估值或700亿</strong></a></p>
  <p>据蓝鲸新闻报道，追觅近期开放直接融资窗口，计划释放部分Pre-IPO份额。本轮投前估值或锁定约700亿元人民币，单笔投资最低门槛高达3.5亿元，整个融资窗口预计于7月初关闭。另外，此次整体释放的份额区间为5%至10%，若按700亿元估值计算，对应融资规模约在35亿至70亿元之间。（财联社）</p>
  <h2><strong>新产品：</strong></h2>
  <p><a href="https://36kr.com/newsflashes/3834308952237953" rel="noopener noreferrer" target="_blank"><strong>赛力斯字节合作新品牌细节曝光：将推纯电、增程双动力</strong></a></p>
  <p>据媒体报道，赛力斯和字节跳动旗下火山引擎深度合作的新汽车品牌快要来了。6月1日，记者从知情人士处获悉，赛豆科技旗下首款车型预计今年内推出，或为跨界车，即介于SUV和轿车之间，并预计将推纯电+增程双动力。据前述知情人士透露，该车预计将在赛力斯凤凰工厂生产，后者目前已处于改线阶段。“赛豆科技相关车型主要与火山引擎合作车机交互大模型等，双方会定期交流等，智驾方案预计不会用华为乾崑。”前述知情人士向记者透露。（新浪财经）</p>
  <p><a href="https://36kr.com/newsflashes/3834282417546885" rel="noopener noreferrer" target="_blank"><strong>Sharpa将触觉灵巧操作能力带⼊NVIDIA Isaac GR00T参考⼈形机器人</strong></a></p>
  <p>36氪获悉，新加坡AI机器人公司Sharpa宣布，携手NVIDIA推出首个搭载Sharpa Wave灵巧手的NVIDIA Isaac GR00T参考人形机器人。该参考人形机器人以Isaac GR00T开发平台为底座，将Sharpa的触觉灵巧操作能⼒、Unitree的人形机器人本体、NVIDIA端侧算⼒与Isaac GR00T开发流程，整合到同⼀套已验证配置中。</p>
  <h2><strong>其他值得关注的新闻：</strong></h2>
  <p><a href="https://36kr.com/newsflashes/3834249751176836" rel="noopener noreferrer" target="_blank"><strong>天津人工智能传感器产业园正式开园，首批10家企业集中签约</strong></a></p>
  <p>36氪获悉，据天津发布，5月31日，市级重点建设项目——天津人工智能传感器产业园正式开园。首批10家企业集中签约，同时，园区围绕构建产业生态，聚焦行业创新平台、产教融合、金融赋能等达成多项合作协议。天津人工智能传感器产业园定位于打造京津冀区域人工智能传感器产业集聚标杆。“园区一期建设20栋适配传感器产业的定制化载体，预计2027年6月交付。随后，将启动二期和三期建设，再增加7万平方米载体。</p>
  <p><a href="https://36kr.com/newsflashes/3834221364455303" rel="noopener noreferrer" target="_blank"><strong>上海：将集中力量 重点突破工业软件、基础软件等领域的底层关键核心技术</strong></a></p>
  <p>上海市新闻发布会6月1日召开，介绍《上海市服务业发展“十五五”规划》相关情况。上海市经济信息化委副主任葛东波表示，预计到2030年，上海市软件和信息服务业营收规模有望达到3万亿元左右，行业增加值突破1万亿元。上海将集中力量，重点突破工业软件、基础软件等领域的底层关键核心技术，加快完成传统软件产品的价值重构。同时，加快推动人工智能全面赋能软件全生命周期，覆盖需求分析、代码生成、测试验证等各个关键环节，积极培育“智能体即服务”“结果即服务”等新型业态，探索软件研发新范式，培育服务新形态与商业新模式。（证券时报）</p>
  <p><a href="https://36kr.com/newsflashes/3834176636626560" rel="noopener noreferrer" target="_blank"><strong>浙江：拟实施“星火计划”培育未来产业行动，加速量子技术产品规模化应用</strong></a></p>
  <p>36氪获悉，《浙江省实施“星火计划”培育壮大未来产业行动方案（2026—2030年）（征求意见稿）》公开征求意见，提到重点发展具身智能、生物制造、量子科技、脑机接口、氢能和绿色燃料、6G、前沿新材料、细胞与基因治疗、深海科技、空天科技等10个基础条件好、爆发力强的领域。其中，重点发展量子计算核心赛道，做强量子测量优势赛道，做优量子通信潜力赛道，推动量子芯片、核心器件、软件算法与场景应用协同发展，加速量子技术产品规模化应用，抢占量子科技产业发展机遇，打造全国知名的量子产业创新发展高地。</p>

- **Tags**: `openai`


---


## 198. 今年盛夏，WAVES之夜会浪的一群年轻人

- **Source**: [36kr](https://36kr.com/p/3834276149356420?f=rss)

- **Summary**: <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_b9a37c5629f14bbba894f73475fcb9b4@6381723_oswg1772858oswg1280oswg720_img_png?x-oss-process=image/quality,q_90/format,jpg/interlace,1" /></p>
  <h2><strong>一、每一年，我们都在找一个地方，让年轻人在一起</strong></h2>
  <p>WAVES之夜是WAVES独有的标签。</p>
  <p>不是又一个分论坛，不是又一个颁奖礼，不是又一场穿西装坐两小时的行业对话。它是WAVES的"晚上"——白天属于议程和逻辑，夜晚属于人和直觉。</p>
  <p>2023年，我们把年轻人和创业者拉到了北京金海湖的碧波岛上。那个夜晚，有人在草坪上喝啤酒，有人在帐篷里聊融资条款，有人在露天电影前什么都没想，发了一小时呆。暗涌WAVES后来写了一段话，成了WAVES之夜最好的一句注脚：</p>
  <p>"几年、十几年甚至更长的时间之后，我们今天在场的人中如果有一些人，会一不小心想起今天，大概大多数记忆都是模糊，但你也会觉得这是一个美好的夏天夜晚。有落日，有草坪，有啤酒，有音乐，有电影。还有一群和曾经的你一样年轻的朋友。"</p>
  <p>碧波岛上发生了什么？我们知道的是，很多后来很火的项目，在那天晚上第一次被投资人听到。</p>
  <p>2024年，WAVES去了北京郎园Station。WAVES之夜上，跳海酒馆的创始人梁优、迷笛的CEO刘欢、播客《忽左忽右》的主编程衍梁坐在了一起，聊的是"年轻人的心思你别猜"。那晚的圆桌没有主题限制，没有PPT，就是聊。我们还在园区里搭了Let's Wave市集，30多个潮牌、咖啡馆、手作摊位挤在一起，年轻人在摊位之间穿梭，像逛庙会，但买的是AI硬件、手冲咖啡和独立杂志。</p>
  <p>2025年，我们去了良渚。五千年的文明遗址，和一群不到25岁的创业者，放在同一个空间里。那晚是"00后之夜·独白"——10位年轻人站上台，每人讲一个"你相信、别人可能不信的事"。</p>
  <p>19岁的Vincent，15岁辍学，19岁把产品做到iOS榜首，创业前在公司睡了一年半，靠网贷撑着产品运营；刘世奇用AI设计了一双"丑拖鞋"，一双鞋在美国卖145美元，6个人，年营收3000万。他上台说了一句后来被疯狂转发的话："AI的秘诀就是让AI打工，让人类摸鱼。"</p>
  <p>刚结束高考的朱浩宇，18岁，用代码"撕开教育围城"，办了一场全球黑客松，每个参与者都是世界各地的年轻开发者。质检官朱天宇说："你的黑客松不只是中国的年轻人，是全世界的年轻人还在创造未来，创造历史。"</p>
  <p>良渚的夜晚，我们第一次真正感受到：这个行业的未来不在任何一个PPT里，而在这些年轻人的手里。</p>
  <p>2026年，我们来到番禺。</p>
  <p>在这里，我们期待新的故事会发生......</p>
  <h2><strong>二、为什么要设计一个"晚上"</strong></h2>
  <p>传统商业大会有一个致命的问题：它像一场考试。所有人都坐在台下，看台上的人讲，记笔记，偶尔举手提问，然后散场。这不叫连接，这叫单向输出。</p>
  <p>最真实的连接从不在台上，永远在台下——在茶歇的走廊里，在晚宴的酒杯旁，在活动结束之后那场没人通知但所有人都心照不宣的局里。</p>
  <p>所以WAVES要为年轻人造一个"晚上"。</p>
  <p>不穿西装的那种。没有PPT的那种。一个人端着杯酒走过去，说一句"我看过你们的产品"，对方回一句"那个功能其实是我们凌晨三点想出来的"，对话就这样开始了。</p>
  <p>WAVES属于36岁以下的头脑。我们不认为"求知"等于"坐好听课"，"社交"等于"加微信"，"链接资源"等于"交换名片"。我们相信，最好的碰撞，发生在你恰好松懈的那个瞬间——在试驾一辆摩托车的江风里，在对着一个AI硬件发呆的时候，在听一个00后讲他"刚刚开始"创业故事的欢笑中。</p>
  <p>告别"传统刻板"的听会模式。来到这里，你是参与者，不是观众。</p>
  <h2><strong>三、WAVES之夜的"神奇酵母"</strong></h2>
  <h3>青年脱口秀</h3>
  <p>2025年良渚的00后之夜证明了一件事：年轻人上台不讲商业计划书的时候，比讲的时候好一万倍。脱口秀不是段子，是一种姿态——用幽默的方式说真话。今年我们让Under 36的创业者和投资人走上脱口秀的台，讲那些白天不适合讲的事。</p>
  <h3>Under 36 颁奖</h3>
  <p>2017年12月，第一批36位"36岁以下了不起的投资人"走上36氪的舞台。2018年，榜首是一个叫张一鸣的人，35岁，字节跳动估值还不到750亿美元。此后八年，这份名册收录了432位创业者和108位投资人。某种程度上，它成了一份中国商界的"清明上河图"——张一鸣、宿华、阳萌、瞿芳、曹毅、曹曦、方爱之……这些名字当年入选的时候，大多数还没被大多数人知道。</p>
  <p>WAVES之夜的颁奖不是室内正式典礼。没有红毯，没有颁奖礼服，没有领导讲话。你在珠江边，端着酒杯，身边的人刚好就是今年入选的创业者或投资人。名册在这个夜晚揭晓——它不是终点，是一个新的起点，意思是"你们被看见了"。</p>
  <h3>AI集市</h3>
  <p>今年的集市，是一个"活在当下"的AI体验场。不是"未来三年AI会怎样"的论坛，而是"你现在就能摸到、用到、玩到的AI"。来逛集市的每一个人，都可以亲手体验。</p>
  <h3>番禺美食</h3>
  <p>番禺是广州的"后厨"。来番禺不吃一顿，等于没来。我们不安排正式宴会——你在市集边逛边吃，遇到一个卖煲仔饭的阿姨，遇到一个做双皮奶的老店，遇到一碗顺德的鱼生。味觉的记忆，有时比PPT更持久。</p>
  <h3>HORWIN江边试骑</h3>
  <p>HORWIN 号外，全球化智能电动摩托车品牌，2016年由周维创立，主打欧洲高端市场。全球首创 400V 全车规 IM 一体化动力平台，实现「充电10分钟，续航100公里」的补能突破。这一次，我们将它带到了珠江边上。</p>
  <p>黄昏时分，跨上这台高性能智能电摩 SENMENTI ONE ，沿着珠江边疾驰一圈。江风迎面吹来，身后是正在沉落的夕阳。</p>
  <p>那一刻，你不需要理解什么"商业闭环"，不需要想什么"护城河"。你只需要感受。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_574e58af5777428c8770642449e40db4@6381723_oswg1452332oswg1280oswg720_img_png?x-oss-process=image/quality,q_90/format,jpg/interlace,1" /></p>
  <h2><strong>四、新造一湾巨浪</strong></h2>
  <p>WAVES之夜的场地——良仓·新造创意园，前身是广东省第二粮食储备仓。</p>
  <p>红砖墙，旧仓库，江边停放着满载历史记忆的黄色起重机，与大学城隔江相望，远处是广州塔的天际线。</p>
  <p>新造，它因水而生、因智而兴。明朝筑堤造地成圩，曾是番禺县府驻地，岁月刻下屈大均故里、二一八抗战烈士纪念碑、良仓旧粮仓的印记，广绣、龙船景的烟火气从未消散。5.5 公里滨江岸线，红砖墙的工业遗风与江景相融，渡口的晚风、岸边的落日，藏着岭南最松弛的浪漫。</p>
  <p>如今的新造，早已褪去旧时光的温婉，成了大湾区科创的活力坐标。踞守创新城核心、大学城南岸，12 所高校、近20万师生的智慧在此交汇，海康威视、浙江大华等龙头集聚，数字经济与科创产业蓬勃生长。良仓・新造创意园活化旧粮仓，让历史建筑变身文商旅地标；智慧谷里科创企业扎根，产学研的合力，让科技成果在这里落地生根。</p>
  <p>这里是历史与未来的共生地古村文脉与科创高楼相望，传统民俗与数字光影共生，江畔晚风与创业热忱相融。没有刻板的都市喧嚣，只有沉淀的底蕴、涌动的机遇，和一群奔赴理想的人。</p>
  <p>浪潮向南，科创向东。新造，承载着570多年的历史沉淀，正以“创新、创造、智造”的全新面貌，接住一份滚烫的热爱，奔赴一场属于大湾区的新生。</p>
  <h2><strong>五、今年盛夏</strong></h2>
  <p>南方六月的傍晚，空气是热的，珠江是温的，天边那片橙红色的光要从水面烧到对岸的大学城。</p>
  <p>今年盛夏，所有人都在说AI。说大模型，说Agent，说具身智能，说量子计算。但没有人能准确告诉你，这些浪潮到底会把我们推向哪里。</p>
  <p>今年盛夏，一批36岁以下的人在番禺的旧粮仓里碰头。他们之中有刚融完A轮的，有还在车库写代码的，有投资了三个独角兽的，有被投资人拒绝了47次的。他们唯一的共同点是：都在水里。</p>
  <p>今年盛夏，WAVES从北京到杭州，从碧波岛到良渚，第一次来到珠江边。不是因为广州更热，是因为浪往南走了。</p>
  <p>今年盛夏，我们不聊PPT里的未来。我们聊此刻正在发生的事。你手里的产品，你刚写的那行代码，你凌晨三点改的那个UI，你喝了三杯精酿之后终于敢说出口的那个想法——这些都是真实的，比任何预测都真实。</p>
  <p>今年盛夏，WAVES之夜。</p>
  <p>落日开始的时候，来。</p>
  <p>&nbsp;</p>
  <p>点击链接可跳转活动行报名链接 <a href="https://hdxu.cn/1IPTZ" rel="noopener noreferrer" target="_blank">https://hdxu.cn/1IPTZ</a>&nbsp;</p>
  <p>扫码进入社群关注后续活动进展</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_0e6dd7b7ca0e41e7b6a96d843d21aa70@6381723_oswg54004oswg594oswg594_img_png?x-oss-process=image/quality,q_100/format,jpg/interlace,1" /></p>

- **Tags**: `agent`


---


## 199. 硬氪首发 | 获近2亿元融资，这家公司用无损Micro-LED加速AI眼镜全彩化进程

- **Source**: [36kr](https://36kr.com/p/3834427736024965?f=rss)

- **Summary**: <p>作者&nbsp;|&nbsp;林晴晴</p>
  <p>编辑&nbsp;|&nbsp;袁斯来</p>
  <p>硬氪获悉，Micro-LED显示技术公司「秋水半导体」已于近期连续完成Pre-A及A轮融资，合计近2亿元人民币。本轮融资由朝晖资本领投，通商基金、盛宇投资、宁波人才发展基金、嘉溢创投、涌现科技、数字光芯及兴棠资本跟投，兴棠资本担任长期财务顾问。本轮融资资金将主要用于在宁波高新区建设8英寸混合键合量产线及后续研发投入。</p>
  <p>「秋水半导体」成立于2022年11月，是一家专注于Micro-LED微显示芯片与模组的半导体公司，产品覆盖数字车灯、AR眼镜、微投影等应用领域。公司总部原在苏州，近期已整体搬迁至宁波。</p>
  <p>Micro-LED常被认为是下一代显示技术的重要方向，但过去几年量产进程始终卡在芯片端。根据IDC数据，2025年全球AR/VR头显与无显示器智能眼镜合计出货量超过1400万台。但具备显示功能的AR眼镜出货量不足百万。在数字车灯领域，TrendForce分析指出，自适应性头灯（ADB）市场渗透率预计到2029年有望达到21.6%，保时捷等车厂已开始采用Micro LED像素模块的头灯方案。芯片端的量产瓶颈是这两大应用落地的主要障碍。</p>
  <p>造成这一局面的关键在于技术路线。过去，传统方案采用4英寸蓝宝石衬底，先通过金属键合将LED晶圆与驱动电路连接，再通过刻蚀来分割像素。但刻蚀过程会对发光材料造成损伤，导致芯片效率大幅下降、良率偏低、出光角度过大，始终难以实现规模化量产。2024年以来，行业开始转向8英寸晶圆级混合键合工艺，但真正打通量产环节的企业仍然极少。</p>
  <p>因此，「秋水半导体」的方案则不再对发光材料进行刻蚀，而是通过无损芯片架构的创新，从根源上避免了材料损伤。配合8英寸硅衬底和混合键合3D封装工艺，可将芯片良率提升至6N以上，出光角度从±60°收窄到±10°，工作温度范围从低于50℃拓展至超过140℃。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_3add4c4cb0034e69876c369d7fbdfb31@15419058_oswg94451oswg697oswg523_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">秋水“乐鱼”AR系列模组（图源/企业）</p>
  <p>&nbsp;</p>
  <p>在产品方面，「秋水半导体」此前已推出0.61英寸的数字车灯芯片，并完成了客户送样验证。同时，AR单绿色芯片计划于今年出货。「秋水半导体」创始人蒋振宇判断，“单色绿光芯片已经能满足游泳眼镜、会议提词、翻译、车载导航等特定场景的需求。且未来一年内具备显示功能的AI眼镜出货量有望从目前的四五十万台提升至千万台级别，千万级芯片出货能力仍然具备挑战。此外要迎来Micro-LED产业的‘iphone时刻’，则必须解决彩色化问题，传统红光Micro-LED芯片因刻蚀损伤导致光效损失超过97%，是无法绕过的障碍，而无损技术是解决这一问题的关键，是打开彩色化大门的钥匙。「秋水半导体」预计将在年底实现彩色化的技术突破。”</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_9e65832f6a124cb190673c9bd2a4073f@15419058_oswg233294oswg727oswg546_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">秋水“乐鱼”AR系列模组（图源/企业）</p>
  <p>&nbsp;</p>
  <p>在国内竞争格局上，Micro-LED芯片领域出现了不同的发展路径。一类是自建整条8英寸或12英寸线的IDM模式，但建线周期较长，通常需要两到三年甚至更久才能达到稳定量产。另一类则是「秋水半导体」的Fab-lite模式，即除了混合键合环节因全球缺乏成熟的代工平台而自主建设外，其余工艺均利用现有成熟半导体代工厂完成。据硬氪了解，「秋水半导体」是国内第一家完成8英寸混合键合工艺通线的初创公司。</p>
  <p>目前，「秋水半导体」正在宁波高新区建设一条8英寸混合键合产线，预计今年10月通线。据蒋振宇介绍，投产后每月可产出千片8英寸晶圆，对应年产1000万颗以上Micro-LED芯片的供货能力。此外，公司的混合键合垂直堆栈架构已在3.75微米像素内实现光芯片与电芯片的互联，未来间距可降至2微米，与华为近期发布的“韬定律”先进混合键合工艺处于同一工艺节点。</p>
  <p>团队方面，「秋水半导体」创始人蒋振宇博士毕业于宾夕法尼亚州立大学，从事半导体光电材料和器件研究，拥有15年技术研发与团队管理经验，曾任大连德豪光电资深科学家、佛山国星半导体研发总监、深圳第三代半导体研究院研发总监，也是科技部新型显示重大专项专家组成员。其联合创始人拥有8年大功率LED车灯创业经验。核心成员曾任职于华为海思、长江存储、英特尔等公司，具备混合键合和先进封装工艺的研发经验。</p>
  <p><strong>投资方观点：</strong></p>
  <p><strong>朝晖资本创始合伙人张越：</strong>秋水半导体放弃了传统的物理切割，通过独有创新的芯片架构，在像素之间建立起一道“电性绝缘”的隐形墙。这种全球首创的无损架构，在不破坏物理结构的情况下实现了各像素点的电性隔离。这种改变底层游戏规则的颠覆性创新，正是在为即将到来的AI眼镜“iPhone时刻”铺设底层基础设施。</p>
  <p><strong>通商基金项目负责人：</strong>当前汽车智能化、AI-AR智能硬件加速普及，Micro LED 微显已是半导体显示领域高景气赛道。秋水半导体自研无损混合键合工艺，攻克行业普遍的刻蚀损伤、像素管控难题，有望解决Micro LED全彩显示的行业发展瓶颈，技术壁垒与业务卡位优势显著。公司核心团队深耕半导体光显行业多年，兼具工艺研发、量产落地与产业资源整合能力，战略清晰、执行力强。我们看好秋水依托技术先发优势抢抓行业红利，助力Micro LED产业突破升级，期待公司成长成为具有全球竞争力的微显龙头企业。</p>
  <p>&nbsp;</p>


---


## 200. 我们有全世界最多的运动鞋，却没有一支值得爱20年的球队

- **Source**: [36kr](https://36kr.com/p/3834297577383553?f=rss)

- **Summary**: <blockquote>
   <p>编者按： 当中国体育用品业总产出突破2万亿元，占据体育产业总产出的54.3%，这无疑是一份值得骄傲的成绩单。过去几十年，中国建立起全球最完整、最高效的体育用品供应链，也孕育出一批具有国际竞争力的品牌。</p>
   <p>但在规模增长之外，另一个问题同样值得关注：当体育产业的大部分价值仍来自商品制造与销售，我们距离一个成熟的体育文化生态还有多远？赛事、IP、社区、俱乐部、体育传媒，以及由此产生的情感认同与共同体文化，是否正在成为中国体育下一阶段发展的关键命题？</p>
   <p>本文并非讨论体育用品行业本身，而是试图透过“54.3%”这一数字，重新审视中国体育产业的结构与未来。</p>
  </blockquote>
  <p>文/邹国俊（前散打冠军，有“亚洲第一快腿”之称。“英雄传说”赛事创始人，也是中国自由搏击行业奠基人，被誉为“中国自由搏击教父”。）</p>
  <p>中国体育用品业2025报告发布：总产出达到20850亿元，同比增长3.6%，占全部体育产业总产出的54.3%。”这当然是一个值得骄傲的数字。它意味着中国已成为：全球最大的运动鞋服制造基地、全球最大的自行车供应链、全球最大的健身器材生产国之一，也是全球最重要的体育消费市场之一。</p>
  <p>但如果只停留在“规模突破”的兴奋里，我们可能会错过这个数字真正值得警惕的地方。因为54.3%反映出来的，不只是中国体育用品业的强大，更是中国体育产业结构的失衡。它说明：中国体育产业，本质上仍然是一个商品加工产业，而不是一个成熟的体育文化产业。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_c0416e17264649efbe442895e5d4fb8f@430412560_oswg996815oswg1080oswg606_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <h3>一、54.3%到底意味着什么？</h3>
  <p>很多人误以为“体育用品业”只是制造业。实际上，按照中国体育产业统计分类，这54.3%不仅包括运动鞋服制造、体育器材制造、户外装备制造，还包括体育用品销售、电商渠道、批发零售、租赁与贸易代理。也就是说，这54.3%本质上是整个体育商品经济链——从工厂到渠道，再到零售消费，构成了中国体育产业的主体。</p>
  <p>而剩余的45.7%，才是健身休闲、体育培训、体育场馆、体育旅游、体育赛事、体育传媒、体育经纪等非用品类体育服务。问题就在这里。</p>
  <h3>二、中国体育的核心，仍然是“卖东西”</h3>
  <p>以美国为例。作为全球最大的体育消费市场，美国体育用品规模依然巨大，但在整个体育产业中的占比通常只有15%-20%。</p>
  <p>而体育服务——包括联赛、转播、博彩、体育传媒、体育娱乐、社区体育、版权IP——占比高达80%以上。换句话说，成熟体育产业真正赚钱的，不是鞋，而是比赛；不是装备，而是内容；不是制造，而是情感。</p>
  <p>中国恰恰相反。今天的人们，可以轻松花100美元买一双运动鞋，却不愿花100元买一张比赛门票——事实上，很多时候他们也“无赛可看”。中国可以制造全球最多的运动装备，却没有一个具有真正全球影响力的体育IP，没有可以传世的文化资产。我们拥有最庞大的供应链，却没有最有价值的内容体系。</p>
  <p>需要说明的是，中国体育用品业庞大的2万亿中，有相当大部分属于OEM、ODM和供应链代工逻辑。在体育装备器材制造中，出口依赖度很高——据IBISWorld估计，2024年中国体育器材制造业出口约占行业收入的51.8%。虽然这不等于全部是OEM/ODM，但说明很大一部分仍服务于海外品牌、渠道和零售商。</p>
  <p>而真正的问题不是“有没有品牌”，而是品牌价值从何而来。中国职业体育IP和生态的缺位，给体育用品企业带来了四个瓶颈：第一，缺少本土顶级赛事作为品牌叙事场景。Nike、Adidas的很多价值来自NBA、世界杯、奥运、NFL、网球大满贯这些长期内容场景。</p>
  <p>中国品牌即使产品做好了，也缺少一个能持续制造英雄、故事、忠诚和情绪的本土体育舞台。第二，只能更多依赖功能、价格、渠道和明星代言，导致品牌竞争停留在“产品力+营销投放”层面，难以进入“文化资产+用户信仰”层面。鞋服可以卖得很好，但很难像Air Jordan那样变成跨代际符号。</p>
  <p>第三，产品创新缺少高强度职业反馈闭环。成熟职业联赛会反向推动装备迭代：篮球鞋、跑鞋、护具、数据穿戴、训练设备，都能从高水平竞技中获得真实验证。中国职业赛事弱，企业就更难建立“顶级运动表现→大众消费”的技术外溢链条。</p>
  <p>第四，全球化缺少体育IP背书。安踏、李宁已经很强，但走向全球时，仍需要被全球消费者理解。没有世界级联赛、球星体系、俱乐部文化支撑，中国品牌更容易被看成“高性价比产品”或“供应链品牌”，而不是文化品牌。所以很多体育装备企业的老板，他们的梦想从来不是Nike、Adidas，而是充满憧憬地说，我希望成为哑铃界、沙袋界、瑜伽垫界的富士康。</p>
  <p>概括来说，OEM/ODM限制的是利润率；职业体育IP缺位限制的是品牌天花板。中国体育用品企业已经能把货做好、卖出去，但从“制造强”走向“品牌贵”，必须有自己的赛事、明星、社区、故事和长期情感资产。</p>
  <h3>三、中国体育的问题，不只是“没有IP”</h3>
  <p>更深层的问题是：体育从来没有真正服务于人的生活。我们对体育的认知，本质上仍然处于一种历史惯性之中。它是工具性的——服务于国家荣誉、教育体系、升学加分、身体管理、消费身份，却很少真正服务于热爱、日常、社群、情感与生活方式。所以我们擅长的是“利用”体育，而不是“享受”体育。</p>
  <p>这也是为什么中国体育消费长期停留在功能消费和商品消费，而不是内容消费和文化消费。很多人买骑行车，并不真正进入骑行文化；很多人买冲锋衣，并不真正热爱户外；很多人健身，也未必真正热爱运动���身。体育，很多时候只是一种自我优化工具。</p>
  <h3>四、中国体育为什么总是“一惊一乍”？</h3>
  <p>这些年，中国体育产业经历了太多“高潮”：足球热、电竞热、马拉松热、骑行热、户外热……但大多数都像潮水一样，来得快去得也快。原因很简单：我们还没有形成真正稳定的体育共同体。美国体育最强大的地方，并不是商业化，而是体育已经成为一种社会组织方式。</p>
  <p>一个家庭几代支持同一支球队；一个大学拥有自己的体育传统；一个城市围绕球队形成认同。NFL真正厉害的，从来不只是比赛，而是它连接了整个美国社会。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_8690e84e079345599784b413cc10a2d6@430412560_oswg74314oswg500oswg667_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p>而中国体育仍然高度个人化。人们可以跑步、健身、买装备，但很少形成长期俱乐部文化、稳定观赛习惯、社区赛事传统、持续性的体育认同。中国体育消费更多是自我消费，而不是共同体消费。</p>
  <h3>五、中国体育缺少“无用精神”</h3>
  <p>如果更深一层做文化归因，中国体育的问题是我们对“无用”的东西缺乏耐心，我们只想赢。体育恰恰是一种极其“无用”的存在。你跑步、打拳、看球不能立刻升职，不能立刻赚钱；你支持一支球队几十年，甚至经常失望。但正是这些“无用”，构成了情感、归属、热爱、社群、公共生活。</p>
  <p>一个成熟的体育社会，本质上是愿意把时间浪费在热爱上。而我们长期习惯于结果、效率、功能性。很多时候，绕过规则赢得胜利，也不是一件丢人的事——因为赢代表一切。但体育真正珍贵的地方，从来不是赢，而是在规则之内，学习如何面对输赢。</p>
  <h3>六、中国体育的未来会变成什么？</h3>
  <p>中国未必会复制美国。因为中国并不是一个典型的社区社会。未来中国真正强大的，可能不是NFL式的超级联盟，而是社区运动、跑步文化、徒步户外、健康生活方式，以及“村超”这样小而美、具有地域特色的内容。</p>
  <p>当有一天我们不再只想要去赢得世界，而是认真经营自己的快乐的时候，我们的体育就具有了生命力与感召力。它未必最赚钱，但可能更接近体育真正的意义——回到人的生活。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260601/v2_1d19b5c043bf4f44b775c40908204045@430412560_oswg108238oswg1080oswg720_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p>真正的重构，需要的不是几个热点、一次风口、一个速成的商业高潮，而是价值观的重塑。只有当体育不再只是工具、不再只是成绩、不再只是消费符号，它才会真正成为一种生活。</p>
  <p>那时候，54.3%也许依然重要，但人们真正关心的，将不再只是卖出了多少双鞋——而是有多少人，愿意为热爱本身浪费时间。</p>


---


## 201. 两市融资余额减少76.61亿元

- **Source**: [36kr](https://36kr.com/newsflashes/3835318543971718?f=rss)

- **Summary**: 36氪获悉，截至6月1日，上交所融资余额报14681.89亿元，较前一交易日减少40.57亿元；深交所融资余额报14063.03亿元，较前一交易日减少36.04亿元；两市合计28744.92亿元，较前一交易日减少76.61亿元。


---


## 202. 机构：2026年智能手机出货量预计同比下降13.9%

- **Source**: [36kr](https://36kr.com/newsflashes/3835318280435077?f=rss)

- **Summary**: 36氪获悉，Counterpoint Research最新智能手机市场展望追踪报告显示，全球智能手机市场正进入近年来较为明显的调整阶段。2026年全球智能手机出货量预计将同比下降13.9%，降至约10.8亿部，创下2013年以来的年度新低，且下滑幅度已超出今年2月预测的12.4%。

- **Tags**: `research`


---


## 203. 腾讯控股短线拉升，现涨超3%

- **Source**: [36kr](https://36kr.com/newsflashes/3835395233920131?f=rss)

- **Summary**: 36氪获悉，腾讯控股短线拉升，现涨超3%。消息面上，据报道，腾讯更加接近推出微信AI助手。


---
