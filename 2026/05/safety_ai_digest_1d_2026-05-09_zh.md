# AI 日报 [AI 安全] - 2026-05-09



## 1. XL-SafetyBench: A Country-Grounded Cross-Cultural Benchmark for LLM Safety and Cultural Sensitivity

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.05662)

- **摘要**: Current LLM safety benchmarks are predominantly English-centric and often rely on translation, failing to capture country-specific harms. Moreover, they rarely evaluate a model's ability to detect culturally embedded sensitivities as distinct from universal harms. We introduce XL-SafetyBench. a suite of 5,500 test cases across 10 country-language pairs, comprising a Jailbreak Benchmark of country-grounded adversarial prompts and a Cultural Benchmark where local sensitivities are embedded within innocuous requests. Each item is constructed via a multi-stage pipeline that combines LLM-assisted discovery, automated validation gates, and dual independent native-speaker annotators per country. To distinguish principled refusal from comprehension failure, we evaluate Attack Success Rate (ASR) alongside two complementary metrics we introduce: Neutral-Safe Rate (NSR) and Cultural Sensitivity Rate (CSR). Evaluating 10 frontier and 27 local LLMs reveals two key findings. First, jailbreak robustness and cultural awareness do not show a coupled relationship among frontier models, so a composite safety score obscures per-axis variation. Second, local models exhibit a near-linear ASR-NSR trade-off (r = -0.81), indicating that their apparent safety reflects generation failure rather than genuine alignment. XL-SafetyBench enables more nuanced, cross-cultural safety evaluation in the multilingual era.

- **技术标签**: `adversarial` `alignment` `benchmark` `jailbreak` `llm`


---


## 2. AoI-Guided Client Selection for Robust and Timely Federated Intrusion Detection in Cloud-Edge Security Analytics

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05644v1)

- **摘要**: Federated learning (FL) is attractive for cloud-edge intrusion detection because it enables collaborative training over distributed telemetry without centralizing raw logs. In production security analytics pipelines, however, only a subset of clients participates in each round, and heterogeneous bandwidth, stragglers, and dropouts can cause the server to rely on stale client information. This paper studies client participation as a timeliness-aware systems problem using Age of Information (AoI). We compare three lightweight policies for federated intrusion detection: AoI-first, utility-first, and a hybrid AoI+utility rule with a tunable trade-off parameter.   Across a CIC-IDS2017 DDoS/PortScan mini subset, NSL-KDD, ToN-IoT, and a synthetic drift benchmark under clean, poisoning, and poisoning-plus-robust-aggregation settings, AoI-aware selection reduces average AoI by about 39--41% and peak AoI by about 70% relative to random sampling while keeping the per-round communication budget fixed. The hybrid policy usually preserves Macro-F1/AUC and provides an interpretable knob for balancing freshness, detection quality, and robustness, although it is not uniformly Pareto-dominant once false positive rate is included. Robustness is evaluated by combining AoI-guided selection with trimmed-mean aggregation under label-flip poisoning; the selection policy itself is not intended as a standalone Byzantine defense. The main practical message is that cloud-edge, privacy-preserving intrusion analytics can improve timeliness through a lightweight scheduling layer without changing the underlying FL participation budget.

- **技术标签**: `benchmark` `federated learning` `policy` `privacy` `rag`


---


## 3. Privacy Without Losing Place: A Paradigm for Private Retrieval in Spatial RAGs

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05459v1)

- **摘要**: This work introduces PAS -- Privacy Anchor Substitution, a structured mechanism for enabling user location privacy in spatial retrieval-augmented generation (RAG) systems. Unlike conventional differential privacy methods that directly perturb user locations, PAS represents location with relative anchor encoding consisting of an anchor, direction bin, and distance bin, allowing seamless integration with modern RAG pipelines. We evaluate PAS on a synthetic urban dataset and show that it achieves impressive coarse privacy guarantees, with approximately 370-400m adversarial location error, while retaining more than half of the baseline retrieval performance. Despite the slight drop in retrieval performance, the downstream generation quality under PAS remains comparatively robust, indicating that large language models can compensate for imperfect spatial retrieval. Furthermore, we provide empirical analysis showing that PAS exhibits non-monotonic privacy-utility relationship with respect to privacy parameters. We attribute this to geometric bias induced by anchor discretization, making it different from continuous noise mechanisms such as geo-indistinguishability. Our results show that structured spatial representations offer a practical approach to privacy in location based reasoning in RAG systems.

- **技术标签**: `adversarial` `bias` `differential privacy` `large language model` `privacy`


---


## 4. SoK: Robustness in Large Language Models against Jailbreak Attacks

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05058v1)

- **摘要**: Large Language Models (LLMs) have achieved remarkable success but remain highly susceptible to jailbreak attacks, in which adversarial prompts coerce models into generating harmful, unethical, or policy-violating outputs. Such attacks pose real-world risks, eroding safety, trust, and regulatory compliance in high-stakes applications. Although a variety of attack and defense methods have been proposed, existing evaluation practices are inadequate, often relying on narrow metrics like attack success rate that fail to capture the multidimensional nature of LLM security. In this paper, we present a systematic taxonomy of jailbreak attacks and defenses and introduce Security Cube, a unified, multi-dimensional framework for comprehensive evaluation of these techniques. We provide detailed comparison tables of existing attacks and defenses, highlighting key insights and open challenges across the literature. Leveraging Security Cube, we conduct benchmark studies on 13 representative attacks and 5 defenses, establishing a clear view of the current landscape encompassing jailbreak attacks, defenses, automated judges, and LLM vulnerabilities. Based on these evaluations, we distill critical findings, identify unresolved problems, and outline promising research directions for enhancing LLM robustness against jailbreak attacks. Our analysis aims to pave the way towards more robust, interpretable, and trustworthy LLM systems. Our code is available at Code.

- **技术标签**: `adversarial` `benchmark` `jailbreak` `large language model` `llm`


---


## 5. How Many Iterations to Jailbreak? Dynamic Budget Allocation for Multi-Turn LLM Evaluation

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06605v1)

- **摘要**: Evaluating and predicting the performance of large language models (LLMs) in multi-turn conversational settings is critical yet computationally expensive; key events -- e.g., jailbreaks or successful task completion by an agent -- often emerge only after repeated interactions. These events might be rare, and under any feasible computational budget, remain unobserved.   Recent conformal survival frameworks construct reliable lower predictive bounds (LPBs) on the number of iterations to trigger the event of interest, but rely on static budget allocation that is inefficient in multi-turn setups. To address this, we introduce \emph{Dynamic Allocation via PRojected Optimization} (DAPRO), the first theoretically valid dynamic budget allocation framework for bounding the time-to-event in multi-turn LLM interactions.   We prove that DAPRO satisfies the budget constraint and provides distribution-free, finite-sample coverage guarantees without requiring the conditional independence between censoring and event times assumed by prior conformal survival approaches.   A key theoretical contribution is a novel coverage bound that scales with the square root of the mean censoring weight rather than the worst-case weight, yielding provably tighter guarantees than prior work. Furthermore, DAPRO can be employed to obtain unbiased, low-variance estimates of population-level evaluation metrics, such as the jailbreak rate, under limited computing resources.   Comprehensive experiments across agentic task success, adversarial jailbreaks, toxic content generation, and RAG hallucinations using LLMs such as Llama 3.1 and Qwen 2.5 demonstrate that DAPRO consistently achieves coverage closer to the nominal level with lower variance than static baselines, while satisfying the budget constraint.

- **技术标签**: `adversarial` `agent` `bias` `jailbreak` `large language model`


---


## 6. FedAttr: Towards Privacy-preserving Client-Level Attribution in Federated LLM Fine-tuning

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06596v1)

- **摘要**: Watermark radioactivity testing type of methods can detect whether a model was trained on watermarked documents, and have become key tools for protecting data ownership in the fine-tuning of large language models (LLMs). Existing works have proved their effectiveness in centralized LLM fine-tuning. However, this type of method faces several challenges and remains underexplored in federated learning (FL), a widely-applied paradigm for fine-tuning LLMs collaboratively on private data across different users. FL mainly ensures privacy through secure aggregation (SA), which allows the server to aggregate updates while keeping clients' updates private. This mechanism preserves privacy but makes it difficult to identify which client trained on watermarked documents. In this work, we propose FedAttr, a new client-level attribution protocol for FL. FedAttr identifies which clients trained on watermarked data via a paired-subset-difference mechanism, while preserving the privacy guarantees of SA and FL performance. FedAttr proceeds in three steps: (i) estimate each client's update by differencing two SA queries, (ii) score the estimate with the watermark detector via differential scoring, and (iii) combine scores across rounds via Stouffer method. We theoretically show that FedAttr produces an unbiased estimator of each client's update with bounded mutual information leakage (i.e., $O(d^*/N)$ per-round update). Moreover, FedAttr empirically achieves 100% TPR and 0% FPR, outperforming all baselines by at least 44.4% in TPR or 19.1% in FPR, with only 6.3% overhead relative to FL training time. Ablation studies confirm that FedAttr is robust to protocol parameters and configurations.

- **技术标签**: `bias` `federated learning` `fine-tuning` `large language model` `llm`


---


## 7. On the Safety of Graph Representation Learning

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06576v1)

- **摘要**: Graph representation learning (GRL) has evolved from topology-only graph embeddings to task-specific supervised GNNs, and more recently to reusable representations and graph foundation models (GFMs). However, existing evaluations mainly measure clean transfer, adaptation, and task coverage. It remains unclear whether GRL methods stay reliable when deployment stresses affect graph signals, graph contexts, label support, structural groups, or predictive evidence. We introduce GRL-Safety, a multi-axis safety evaluation benchmark for GRL. GRL-Safety evaluates twelve representative methods, spanning topology-only embedding methods, supervised GNNs, self-supervised graph models, and GFMs, on twenty-five graph datasets under standardized evaluation conditions while preserving method-native adaptation. The evaluation covers five safety axes: corruption robustness, OOD generalization, class imbalance, fairness, and interpretation, with per-axis and sub-condition reporting rather than a single aggregate score. Our analysis yields three cross-axis insights that can inspire future research. First, safety behavior is shaped by the interaction between representation design and the stressed graph factor, rather than by method family alone. Second, foundation-era methods show axis-specific strengths rather than broad safety dominance. Third, several deployment regimes remain difficult even for the best evaluated method, revealing capability gaps that require new robustness, adaptation, or training objectives beyond model selection. The benchmark, evaluation protocols, and code are available at: https://github.com/GXG-CS/GRL-Safety.

- **技术标签**: `benchmark` `embedding` `fairness` `foundation model` `rag`


---


## 8. Pop Quiz Attack: Black-box Membership Inference Attacks Against Large Language Models

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06423v1)

- **摘要**: Large language models (LLMs) show strong performance across many applications, but their ability to memorize and potentially reveal training data raises serious privacy concerns. We introduce the PopQuiz Attack, a black-box membership inference attack that tests whether a model can recall specific training examples. The core idea is to turn target data into quiz-style multiple-choice questions and infer membership from the model's answers. Across six widely used LLMs (GPT-3.5, GPT-4o, LLaMA2-7b, LLaMA2-13b, Mistral-7b, and Vicuna-7b) and four datasets, our method achieves an average ROC-AUC of 0.873 and outperforms existing approaches by 20.6%. We further analyze factors affecting attack success, including query complexity, data type, data structure, and training settings. We also evaluate instruction-based, filter-based, and differential privacy-based defenses, which reduce performance but do not eliminate the risk. Our results highlight persistent privacy vulnerabilities in modern LLMs.

- **技术标签**: `differential privacy` `gpt` `gpt-4` `gpt-4o` `large language model`


---


## 9. Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05632v1)

- **摘要**: Retrieval-Augmented Generation (RAG) systems are vulnerable to knowledge base poisoning, yet existing attacks have been evaluated almost exclusively against vanilla retrieve-then-generate pipelines. Architectures designed to handle conflicting retrieved information - multi-agent debate, agentic retrieval, recursive language models - remain untested against adversarially optimized contradictions. We evaluate four RAG architectures (vanilla RAG, agentic RAG, MADAM-RAG, and Recursive Language Models) under controlled single-document (N=1) poisoning on 921 Natural Questions QA pairs, comparing a clean baseline, naive injection, and CorruptRAG-AK - an adversarial attack whose meta-epistemic framing targets credibility assessment. Architecture is a high-impact variable in adversarial robustness: under CorruptRAG-AK, attack success rates range from 81.9% (vanilla) to 24.4% (RLM) - a spread of nearly 58 percentage points across architectures with comparable clean accuracy (~92%). Decomposing this gap, once the poisoned document is retrieved, adversarial framing - not retrieval optimization - drives the majority of CorruptRAG-AK's advantage for three of four architectures, localizing the cross-architecture vulnerability at the content-reasoning stage. Our MADAM-RAG reimplementation shows the highest apparent contradiction detection rate, though our LLM judge over-identifies this behavior (~48.5% precision), so reported rates are upper bounds. Regardless of detection, MADAM-RAG cannot resolve contradictions reliably, producing a 41.4% non-answer rate even on clean inputs - though implementation divergences from the original may contribute. We introduce a seven-category behavioral taxonomy capturing contradiction detection, hedging, and failure modes beyond binary accuracy. Code, data, and analysis notebooks are publicly available.

- **技术标签**: `adversarial` `agent` `debate` `llm` `rag`


---


## 10. Information Theoretic Adversarial Training of Large Language Models

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05415v1)

- **摘要**: Large language models (LLMs) remain vulnerable to adversarial prompting despite advances in alignment and safety, often exhibiting harmful behaviors under novel attack strategies. While adversarial training can improve robustness, existing approaches are computationally expensive and difficult to scale. Recent continuous adversarial training methods, such as Continuous adversarial training (CAT) and Continuous Adversarial Preference Optimization (CAPO), address this challenge by leveraging gradient-based perturbations in the embedding space, enabling more efficient and expressive attacks. Building on this paradigm, we propose WARDEN, a distributionally robust adversarial training framework for LLMs that dynamically reweights adversarial examples through an f -divergence ambiguity set around the empirical training distribution. Our method optimizes the worst-case adversarial loss within a divergence ball around the empirical data distribution, automatically emphasizing harder adversarial examples. Using the convex dual formulation, the objective reduces to a log-sum-exp form under the KL divergence, with a dynamical parameter controlling the strength of reweighting. This study leads to a new class of information-theoretic objectives that significantly reduce attack success rates while maintaining model utility. Across multiple LLMs and attack settings, WARDEN substantially reduces attack success rates with computational and utility costs comparable to CAT-, CAPO-, and MixAT-based baselines, making it a practical approach for scalable robust alignment.

- **技术标签**: `adversarial` `alignment` `embedding` `large language model` `llm`


---


## 11. Privacy by Postprocessing the Discrete Laplace Mechanism

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06502v1)

- **摘要**: We show that an "old dog", the classical discrete Laplace (aka.~geometric) mechanism, can "perform new tricks":   1. It can be post-processed to yield a simple, unbiased estimator of any subexponential function $f$ of the original data, giving a simple, discrete, multivariate version of the recent unbiasing result for the Laplace mechanism by Calmon et al. (FORC '25).   2. It can be post-processed to output the same distribution as the Laplace mechanism or the Staircase mechanism with identical privacy parameters.   Thus, the discrete Laplace mechanism is a versatile mechanism that should be preferred over the Laplace and Staircase mechanisms whenever the data is discrete (or can be made discrete while controlling $\ell_1$-sensitivity).   We show bounds on the variance of our estimator, compared to the mean square error of the biased estimator that simply evaluates the $f$ on the output of the mechanism. Though our unbiased estimator has exponential running time for worst-case functions, we show that it can often be computed in linear or polynomial time for some common functions exhibiting structure. We showcase the properties of our methods empirically with several use cases including profile and entropy estimation, as well as distributed/federated data analysis applications in which unbiasedness is key to accuracy.

- **技术标签**: `bias` `privacy`


---


## 12. Why Global LLM Leaderboards Are Misleading: Small Portfolios for Heterogeneous Supervised ML

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06656v1)

- **摘要**: Ranking LLMs via pairwise human feedback underpins current leaderboards for open-ended tasks, such as creative writing and problem-solving. We analyze ~89K comparisons in 116 languages from 52 LLMs from Arena, and show that the best-fit global Bradley-Terry (BT) ranking is misleading. Nearly 2/3 of the decisive votes cancel out, and even the top 50 models according to the global BT ranking are statistically indistinguishable (pairwise win probabilities are at most 0.53 within the top 50 models). We trace this failure to strong, structured heterogeneity of opinions across language, task, and time. Moreover, we find an important characteristic - *language* plays a key role. Grouping by language (and families) increases the agreement of votes massively, resulting in two orders of magnitude higher spread in the ELO scores (i.e., very consistent rankings). What appears as global noise is in fact a mixture of coherent but conflicting subpopulations.   To address such heterogeneity in supervised machine learning, we introduce the framework of $(λ, ν)$-portfolios, which are small sets of models that achieve a prediction error at most $λ$, "covering" at least a $ν$ fraction of users. We formulate this as a variant of the set cover problem and provide guarantees using the VC dimension of the underlying set system. On the Arena data, our algorithms recover just 5 distinct BT rankings that cover over 96% of votes at a modest $λ$, compared to the 21% coverage by the global ranking. We also provide a portfolio of 6 LLMs that cover twice as many votes as the top-6 LLMs from a global ranking. We further construct portfolios for a classification problem on the COMPAS dataset using an ensemble of fairness-regularized classification models and show that these portfolios can be used to detect blind spots in the data, which might be of independent interest to policymakers.

- **技术标签**: `fairness` `llm` `policy` `rag`


---


## 13. PianoCoRe: Combined and Refined Piano MIDI Dataset

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06627v1)

- **摘要**: Symbolic music datasets with matched scores and performances are essential for many music information retrieval (MIR) tasks. Yet, existing resources often cover a narrow range of composers, lack performance variety, omit note-level alignments, or use inconsistent naming formats. This work presents PianoCoRe, a large-scale piano MIDI dataset that unifies and refines major open-source piano corpora. The dataset contains 250,046 performances of 5,625 pieces written by 483 composers, totaling 21,763 h of performed music. PianoCoRe is released in tiered subsets to support different applications: from large-scale analysis and pre-training (PianoCoRe-C and deduplicated PianoCoRe-B) to expressive performance modeling with note-level score alignment (PianoCoRe-A/A*). The note-aligned subset, PianoCoRe-A, provides the largest open-source collection of 157,207 performances aligned to 1,591 scores to date. In addition to the dataset, the contributions are: (1) a MIDI quality classifier for detecting corrupted and score-like transcriptions and (2) RAScoP, an alignment refinement pipeline that cleans temporal alignment errors and interpolates missing notes. The analysis shows that the refinement reduces temporal noise and eliminates tempo outliers. Moreover, an expressive performance rendering model trained on PianoCoRe demonstrates improved robustness to unseen pieces compared to models trained on raw or smaller datasets. PianoCoRe provides a ready-to-use foundation for the next generation of expressive piano performance research.

- **技术标签**: `alignment` `research` `robustness`


---


## 14. Online Bayesian Calibration under Gradual and Abrupt System Changes

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06612v1)

- **摘要**: Bayesian model calibration is central to digital twins and computer experiments, as it aligns model outputs with field observations by estimating calibration parameters and correcting systematic model bias. Classical Bayesian calibration introduces latent parameters and a discrepancy function to model bias, but suffers from parameter--discrepancy confounding and is typically formulated as an offline procedure under a stationary data-generating assumption. These limitations are restrictive in modern digital twin applications, where systems evolve over time and may exhibit gradual drift and abrupt regime shifts. While data assimilation methods enable sequential updates, they generally do not explicitly model systematic bias and are less effective under abrupt changes. We propose Bayesian Recursive Projected Calibration (BRPC), an online Bayesian calibration framework for streaming data under simulator mismatch and nonstationarity. BRPC extends projected calibration to the online setting by separating a discrepancy-free particle update for calibration parameters from a conditional Gaussian process update for discrepancy, preserving identifiability while enabling bias-aware adaptation under gradual system evolution. To handle abrupt changes, BRPC is integrated with restart mechanisms that detect regime shifts and reset the calibration process. We establish theoretical guarantees for both components, including tracking performance under gradual evolution and false-alarm and detection behavior for restart mechanisms. Empirical studies on synthetic and plant-simulation benchmarks show that BRPC improves calibration accuracy under gradual changes, while restart-augmented BRPC further improves robustness and predictive performance under abrupt regime shifts compared to sliding-window Bayesian calibration and data assimilation baselines.

- **技术标签**: `benchmark` `bias` `robustness`


---


## 15. SoftSAE: Dynamic Top-K Selection for Adaptive Sparse Autoencoders

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06610v1)

- **摘要**: Sparse Autoencoders (SAEs) have become an important tool in mechanistic interpretability, helping to analyze internal representations in both Large Language Models (LLMs) and Vision Transformers (ViTs). By decomposing polysemantic activations into sparse sets of monosemantic features, SAEs aim to translate neural network computations into human-understandable concepts. However, common architectures such as TopK SAEs rely on a fixed sparsity level. They enforce the same number of active features (K) across all inputs, ignoring the varying complexity of real-world data. Natural data often lies on manifolds with varying local intrinsic dimensionality, meaning the number of relevant factors can change significantly across samples. This suggests that a fixed sparsity level is not optimal. Simple inputs may require only a few features, while more complex ones need more expressive representations. Using a constant K can therefore introduce noise in simple cases or miss important structure in more complex ones. To address this issue, we propose SoftSAE, a sparse autoencoder with a Dynamic Top-K selection mechanism. Our method uses a differentiable Soft Top-K operator to learn an input-dependent sparsity level k. This allows the model to adjust the number of active features based on the complexity of each input. As a result, the representation better matches the structure of the data, and the explanation length reflects the amount of information in the input. Experimental results confirm that SoftSAE not only finds meaningful features, but also selects the right number of features for each concept. The source code is available at: https://anonymous.4open.science/r/SoftSAE-8F71/.

- **技术标签**: `interpretability` `large language model` `llm` `mechanistic interpretability` `transformer`


---


## 16. CLAD: A Clustered Label-Agnostic Federated Learning Framework for Joint Anomaly Detection and Attack Classification

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06571v1)

- **摘要**: The rapid expansion of the Internet of Things (IoT) and Industrial IoT (IIoT) has created a massive, heterogeneous attack surface that challenges traditional network security mechanisms. While Federated Learning (FL) offers a privacy-preserving alternative to centralized Intrusion Detection Systems (IDS), standard approaches struggle to generalize across diverse device behaviors and typically fail to utilize the vast amounts of unlabeled data present in realistic edge environments. To bridge these gaps, we propose CLAD, a holistic framework that seamlessly incorporates Clustered Federated Learning (CFL) with a novel Dual-Mode Micro-Architecture ($\text{DM}^2\text{A}$). This unified approach simultaneously tackles the two primary bottlenecks of IoT security: device heterogeneity and label scarcity. The $\text{DM}^2\text{A}$ component features a shared encoder followed by two branches, enabling joint unsupervised anomaly detection and supervised attack classification; this allows the framework to harvest intelligence from both labeled and unlabeled clients. Concurrently, the clustering component dynamically groups devices with congruent traffic patterns, preventing global model divergence. By carefully combining these elements, CLAD ensures that no data is discarded and distinct operational patterns are preserved. Extensive evaluations demonstrate that this integrated approach significantly outperforms state-of-the-art baselines, achieving a 30% relative improvement in detection performance in scenarios with 80% unlabeled clients, with only half the communication cost.

- **技术标签**: `federated learning` `privacy`


---


## 17. BAMI: Training-Free Bias Mitigation in GUI Grounding

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06664v1)

- **摘要**: GUI grounding is a critical capability for enabling GUI agents to execute tasks such as clicking and dragging. However, in complex scenarios like the ScreenSpot-Pro benchmark, existing models often suffer from suboptimal performance. Utilizing the proposed \textbf{Masked Prediction Distribution (MPD)} attribution method, we identify that the primary sources of errors are twofold: high image resolution (leading to precision bias) and intricate interface elements (resulting in ambiguity bias). To address these challenges, we introduce \textbf{Bias-Aware Manipulation Inference (BAMI)}, which incorporates two key manipulations, coarse-to-fine focus and candidate selection, to effectively mitigate these biases. Our extensive experimental results demonstrate that BAMI significantly enhances the accuracy of various GUI grounding models in a training-free setting. For instance, applying our method to the TianXi-Action-7B model boosts its accuracy on the ScreenSpot-Pro benchmark from 51.9\% to 57.8\%. Furthermore, ablation studies confirm the robustness of the BAMI approach across diverse parameter configurations, highlighting its stability and effectiveness. Code is available at https://github.com/Neur-IO/BAMI.

- **技术标签**: `agent` `benchmark` `bias` `rag` `robustness`


---


## 18. Improved techniques for fine-tuning flow models via adjoint matching: a deterministic control pipeline

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06583v1)

- **摘要**: We propose a deterministic adjoint matching framework that formulates human preference alignment for flow-based generative models as an optimal control problem over velocity fields. One can directly regress the control toward a value-gradient-induced target under the current policy, leading to a simple and stable training objective. Building on this perspective, we introduce a truncated adjoint scheme that focuses computation on the terminal portion of the trajectory, where reward-relevant signals concentrate, which yields substantial computational savings while preserving alignment quality. We further generalize the framework beyond standard KL-based regularization, allowing more flexible trade-offs between alignment strength and distributional preservation. Experiments on SiT-XL/2 and FLUX.2-Klein-4B demonstrate consistent gains across multiple alignment metrics, along with substantially improved diversity and mode preservation.

- **技术标签**: `alignment` `fine-tuning` `generative` `policy`


---


## 19. Market-Alignment Risk in Pricing Agents: Trace Diagnostics and Trace-Prior RL under Hidden Competitor State

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06529v1)

- **摘要**: Outcome metrics can certify the wrong behavior. We study this failure in a two-hotel revenue-management simulator where Hotel A trains an agent against a fixed rule-based revenue-management competitor, Hotel B. A standard learning agent can obtain near-reference revenue per available room (RevPAR) while failing to learn market-like yield management: it sells too aggressively, undercuts, or collapses to modal price buckets. We diagnose this as a Goodhart-style failure under partial observability. Hotel A cannot observe the competitor's remaining inventory, booking curve, or pricing rule, so the same Hotel A-visible state maps to multiple plausible Hotel B prices. Deterministic value-based RL and deterministic copying collapse this unresolved uncertainty into shortcut behavior. We introduce a trace-level diagnostic protocol using RevPAR, occupancy, ADR, full price-bucket distributions, L1/JS distances, and seed-level confidence intervals. The verified repair is Trace-Prior RL: learn a distributional market prior from lagged market traces, then train a stochastic pricing policy with a RevPAR reward and a KL penalty to the learned prior. The final policy matches Hotel B's RevPAR, occupancy, ADR, and price distribution within seed-level uncertainty, while still optimizing Hotel A's own reward. We argue that the contribution is not a new optimizer and not a hotel-pricing leaderboard, but a reproducible failure-and-repair recipe for agentic systems where scalar rewards are easy to game and the intended behavior is only visible in traces. A key finding is that higher exact action accuracy can worsen aggregate trace alignment when the target is distributional.

- **技术标签**: `agent` `alignment` `policy`


---


## 20. From Token Lists to Graph Motifs: Weisfeiler-Lehman Analysis of Sparse Autoencoder Features

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06494v1)

- **摘要**: Sparse autoencoders (SAEs) have become central to mechanistic interpretability, decomposing transformer activations into monosemantic features. Yet existing analyses characterise features almost exclusively through top-activating token lists or decoder weight vectors, leaving the higher-order co-occurrence structure shared across features largely unexamined. We introduce a graph-structured representation in which each SAE feature is modelled as a token co-occurrence graph: nodes are the tokens most frequent near strong activations, and edges connect pairs that co-occur within local context windows. A custom WL-style, frequency-binned graph kernel then provides a similarity measure over this structural space. Applied as a proof of concept to features from a large SAE trained on GPT-2 Small and probed with a synthetic mixed-domain corpus, our clustering recovers heuristic motif families (punctuation-heavy patterns, language and script clusters, and code-like templates) that are not recovered by clustering on decoder cosine similarity. A token-histogram baseline achieves higher overall purity, so the contribution of the graph view is complementary rather than dominant: it surfaces structural relationships that token-frequency and decoder-weight views alone do not capture. Cluster assignments are stable across graph-construction hyperparameters and random seeds.

- **技术标签**: `gpt` `interpretability` `mechanistic interpretability` `transformer`


---


## 21. Patch-Effect Graph Kernels for LLM Interpretability

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06480v1)

- **摘要**: Mechanistic interpretability aims to reverse-engineer transformer computations by identifying causal circuits through activation patching. However, scaling these interventions across diverse prompts and task families produces high-dimensional, unstructured datasets that are difficult to compare systematically. We propose a framework that reframes mechanistic analysis as a graph machine-learning problem by representing activation-patching profiles as patch-effect graphs over model components. We introduce three graph-construction methods: direct-influence via causal mediation, partial-correlation, and co-influence and apply graph kernels to analyze the resulting structures. Evaluating this approach on GPT-2 Small using Indirect Object Identification (IOI) and related tasks, we find that patch-effect graphs preserve discriminative structural signals. Specifically, localized edge-slot features provide higher classification accuracy than global graph-shape descriptors. A screened paired-patching validation suggests that CI and PC selected candidate edges correspond to stronger activation-influence effects than random or low-rank candidates. Crucially, by evaluating these representations against rigorous prompt-only and raw patch-effect controls, we make the evidential scope of the benchmark explicit: graph features compress structured patching signal, while raw tensors and surface cues define strong baselines that any circuit-level claim should address. Ultimately, our framework provides a compression and evaluation pipeline for comparing patching-derived structures under controlled baselines, separating robust slice-discriminative evidence from stronger task-general causal-circuit claims.

- **技术标签**: `benchmark` `gpt` `interpretability` `llm` `mechanistic interpretability`


---


## 22. Beyond Negative Rollouts: Positive-Only Policy Optimization with Implicit Negative Gradients

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06650v1)

- **摘要**: Reinforcement learning with verifiable rewards (RLVR), due to the deterministic verification, becomes a dominant paradigm for enhancing the reasoning ability of large language models (LLMs). The community witnesses the rapid change from the Proximal Policy Optimization (PPO) to Group Relative Policy Optimization (GRPO), in which GRPO reduces the complicated advantage estimation with simple estimation over grouped positive and negative rollouts. However, we note that negative rollouts may admit no gradation of failure severity, and the combinatorial vastness makes penalizing a few sampled negatives unlikely to cover a meaningful reward signal under sparse binary rewards. In this work, we propose Positive-Only Policy Optimization (POPO), a novel RLVR framework in which learning can occur exclusively via online positive rollouts. Specifically, POPO utilizes bounded importance sampling over the positive rollout set. Thus, no disjoint negative rollouts are used for the gradient guidance. We show that implicit negative gradients can emerge naturally through reinforcing the positive probability via rollouts redistribution. Next, POPO stabilizes the policy optimization through two mechanisms. First, it applies a siamese policy network with a momentum-based adaptation law for stabilized policy evolution. Second, we replace the KL-divergence with a bounded similarity penalty term in the siamese representation space. We conduct extensive experiments using publicly available, well-established text-LLM models, e.g., the Qwen family, across all-level mathematical benchmarks. Our experiment demonstrates that POPO achieves performance comparable to, or even superior to GRPO. Notably, we show that POPO can achieve 36.67% in AIME 2025 with Qwen-Math-7B, outperforming GRPO 30.00%. Our ablation and sweep studies further illustrate the necessity and robustness of POPO components.

- **技术标签**: `benchmark` `large language model` `llm` `policy` `qwen`


---


## 23. Cited but Not Verified: Parsing and Evaluating Source Attribution in LLM Deep Research Agents

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06635v1)

- **摘要**: Large language models (LLMs) power deep research agents that synthesize information from hundreds of web sources into cited reports, yet these citations cannot be reliably verified. Current approaches either trust models to self-cite accurately, risking bias, or employ retrieval-augmented generation (RAG) that does not validate source accessibility, relevance, or factual consistency. We introduce the first source attribution evaluation framework that uses a reproducible AST parser to extract and evaluate inline citations from LLM-generated Markdown reports at scale. Unlike methods that verify claims in isolation, our framework closes the loop by retrieving the actual cited content, enabling human or model evaluators to judge each citation against its source. Citations are evaluated along three dimensions. (1) Link Works verifies URL accessibility, (2) Relevant Content measures topical alignment, and (3) Fact Check validates factual accuracy against source content. We benchmark 14 closed-source and open-source LLMs across three evaluation dimensions using rubric-based LLM-as-a-judge evaluators calibrated through human review. Our results reveal that even the strongest frontier models maintain link validity above 94% and relevance above 80%, yet achieve only 39-77% factual accuracy, while fewer than half of open-source models successfully generate cited reports in a one-shot setting. Ablation studies on research depth show that Fact Check accuracy drops by approximately 42% on average across two frontier models as tool calls scale from 2 to 150, demonstrating that more retrieval does not produce more accurate citations. These findings reveal a critical disconnect between surface-level citation quality and factual reliability, and our framework provides the evaluation infrastructure to assess the disconnect.

- **技术标签**: `agent` `alignment` `benchmark` `bias` `large language model`


---


## 24. Constraining Host-Level Abuse in Self-Hosted Computer-Use Agents via TEE-Backed Isolation

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06393v1)

- **摘要**: Self-hosted computer-use agents (SHCUAs), such as OpenClaw, combine natural-language interaction with direct access to host-side resources, including browsers, files, scripts, system commands, and external communication channels. While useful for automating real tasks, this capability also creates a host-level abuse surface: a legitimately deployed agent may be steered toward unsafe operations through malicious messages, indirect prompt injection, unsafe skills, or tampering along the host-side control path. We argue that such risks cannot be addressed by ad hoc blocking rules alone, because the security criticality of an operation depends jointly on its action type, target object, execution context, and potential effect.   This paper presents an operation-centric model for risk-based confinement of SHCUA operations. The proposed design keeps ordinary functionality on the constrained REE path, while protecting security-critical classification, authorization, binding, evidence generation, and selected execution-control decisions inside a cloud-native TEE-backed trusted operation plane. We instantiate the architecture on OpenClaw using Intel TDX as the primary trusted backend, with remote terminal-side trusted components verifying TDX-audited commands before constrained local execution. The evaluation shows that the design can block unsafe or policy-disallowed operations before execution, preserve ordinary functionality for allowed workloads, and provide auditable evidence with deployment-dependent overhead.

- **技术标签**: `agent` `policy` `prompt injection`


---


## 25. Trade-off Functions for DP-SGD with Subsampling based on Random Shuffling: Tight Upper and Lower Bounds

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06259v1)

- **摘要**: We derive a tight analysis of the trade-off function for Differentially Private Stochastic Gradient Descent (DP-SGD) with subsampling based on random shuffling within the $f$-DP framework. Our analysis covers the regime $σ\geq \sqrt{3/\ln M}$, where $σ$ is the noise multiplier and $M$ is the number of rounds within a single epoch. Unlike $f$-DP analyses for Poisson subsampling, which yield non-closed implicit formulas that can be machine computed but are non-transparent, random shuffling admits a tight analysis yielding transparent and interpretable closed-form bounds. Our concrete bounds, derived via the Berry-Esseen theorem, are tight up to constant factors within the proof framework. We demonstrate worked parameter settings for a single epoch ($E=1$) with a corresponding trade-off function $\geq 1-a-δ$, that is, only $δ$ below the ideal random guessing diagonal $1-a$: For $δ= 1/100$ and $σ= 1$, roughly $M \approx 1.14\times 10^6$ rounds and $N \approx 1.14\times 10^7$ training samples suffice to achieve meaningful differential privacy. This is in contrast to recent negative results for the regime $σ\leq 1/\sqrt{2 \ln M}$. Our concrete bounds can be composed over multiple epochs leading to $δ$ having a linear in $E$ dependency, which restricts $E=O(\sqrt{M})$. To go beyond Berry--Esseen, we introduce a new proof technique based on a generalization of the law of large numbers that yields an asymptotic random guessing diagonal-limit result: if $E=c_M^2M$ with $c_M\to 0$, then the $E$-fold composed trade-off function satisfies $f^{\otimes E}(a)\to 1-a$ uniformly in $a\in[0,1]$ with $δ$ having only an $O(\sqrt{E})$ dependency. We compare this asymptotic regime with the corresponding Poisson subsampling asymptotic, and highlight the characterization of explicit convergence rates as an open question.

- **技术标签**: `differential privacy` `privacy`


---


## 26. Profiling for Pennies: Unveiling the Privacy Iceberg of LLM Agents

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06232v1)

- **摘要**: Large Language Models (LLMs) have revolutionized how information are collected, aggregated, and reasoned. However, this enables a novel and accessible vector of privacy intrusion: the automated and in-depth personal profiling; this engenders a chilling effect of "peepers everywhere". Existing research primarily unfolds from the training pipeline of LLM, emphasizing the exposure of Personally Identifiable Information (PII) through memorization, while privacy studies from a human-centric perspective remain underexplored. To fill this void, we empirically investigate privacy perception in the real world through the lens of human awareness and the practices of LLM-integrated platforms, revealing a significant dissonance: platforms fail to technically or policy-wise address public privacy concerns. To facilitate a systematic and quantifiable study of privacy risk, we propose the PrivacyIceberg, which categorizes real-world human privacy risks into three tiers: explicitly searched, contextually inferred, and deeply aggregated, based on the sophistication of LLM exploitation. We developed IcebergExplorer to audit privacy exposure, utilizing minimal PII as a search seed to reconstruct high-fidelity profiles, achieving over 90% factual accuracy within 10 minutes at a cost under $3, for real-world scenarios. Additionally, we identify six root causes contributing to such privacy disclosures and propose multi-stakeholder countermeasures for LLM vendors, individuals, and data publishers.

- **技术标签**: `agent` `large language model` `llm` `policy` `privacy`


---


## 27. Backdoor Mitigation in Object Detection via Adversarial Fine-Tuning

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05928v1)

- **摘要**: Backdoor attacks can implant malicious behaviours into deep models while preserving performance on clean data, posing a serious threat to safety-critical vision systems. Although backdoor mitigation has been studied extensively for image classification, defenses for object detection remain comparatively underdeveloped. Adversarial fine-tuning is a common backdoor mitigation approach in classification, but adapting it to detection is nontrivial as classification-oriented adversarial generation does not match the detection attack space, where attacks may cause object misclassification or disappearance, and standard detection losses can dilute the repair signal across many predictions. We address these challenges through a detection-aware adversarial fine-tuning framework for mitigating object-detection backdoors when the defender has access only to a compromised detector and a small clean dataset, without knowing the attack objective. For adversarial generation that does not require knowledge of the attack objective, we introduce soft-branch minimisation, which uses a soft gate to combine objectives aligned with misclassification and disappearance attacks, together with a detection-aware classification-loss maximisation. For targeted repair, we introduce a dual-objective fine-tuning loss applied to target-matched predictions, concentrating the defensive update on predictions most relevant to the backdoor behaviour. Experiments across CNN- and Transformer-based detectors show that our approach more effectively reduces attack success while preserving true detections, compared with classification-oriented baselines, and maintains competitive clean detection performance.

- **技术标签**: `adversarial` `backdoor` `fine-tuning` `transformer` `vision`


---


## 28. $α$-Wasserstein Mechanism for Rényi Pufferfish Privacy

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05723v1)

- **摘要**: This paper introduces the $α$-Wasserstein mechanism for achieving Rényi Pufferfish Privacy using Laplace and Gaussian noise. By leveraging Hölder's inequality, we demonstrate that the scale parameter of the Laplace mechanism can be calibrated via an upper bound on the $W_α$ metric to satisfy $(α, ε)$-Rényi Pufferfish Privacy for $α\in (1, \infty]$. We show that at the limit $α= \infty$, this framework recovers the established $W_\infty$ mechanism for $ε$-pufferfish privacy. This result is subsequently extended to the exponential mechanism. Furthermore, we propose a $W_α$ mechanism for Gaussian noise for $α\in (1, \infty)$, demonstrating that it generalizes existing results within the Rényi Differential Privacy framework. Experimental evaluations reveal that our $α$-Wasserstein mechanism significantly reduces noise power compared to the conventional $W_\infty$-based approach, with the Gaussian mechanism providing superior utility over the Laplace mechanism. Notably, the mechanisms derived in this work achieve exact $(α, ε)$-Rényi Pufferfish Privacy without requiring additional relaxations, such as $δ$-approximations.

- **技术标签**: `differential privacy` `privacy` `rag`


---


## 29. Evaluating the Reliability of Multiple Large Language Models in Risk Assessment: A CIS Controls Based Approach

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05424v1)

- **摘要**: Proper implementation of technical and administrative controls reinforces an organization's cybersecurity posture and business resilience, reduces risks, and enhances governance, ultimately elevating business maturity. The dynamics of the technological landscape and emerging threats negatively affect the most diverse companies, regardless of their size. This, associated with a global gap in the cybersecurity workforce, imposes enormous challenges and the need for a profound change in how companies respond to threats. Generative Artificial Intelligence from large language models has become an influential tool across various companies, emerging as a viable option to help address those challenges while partially addressing the shortage of skilled labor. Although large language models can help in this scenario, there may be risks, such as generating unreliable or 'hallucinated' content, which could lead people and companies to make bad decisions. Our study proposes integrating human experts into the validation process as a crucial step toward ensuring the proper implementation of technical and administrative controls. Furthermore, we sought to identify how large language models perform in assessing cybersecurity risk scenarios compared to human experts, highlighting the importance of integrating humans and machines in the cybersecurity risk assessment process. Using a questionnaire with risk scenarios, we analyzed responses from 50 human experts. We compared their responses with those of five popular large language models to determine whether it is possible to use only large language models for cybersecurity risk assessment. The results reveal that the large language models consistently underestimated cybersecurity risks compared to human experts, reinforcing the need for human oversight and suggesting that LLMs should be used as complementary tools rather than standalone assessors.

- **技术标签**: `generative` `governance` `large language model` `llm` `risk assessment`


---


## 30. Autonomous Adversary: Red-Teaming in the age of LLM

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06486v1)

- **摘要**: Language Model Agents (LMAs) are emerging as a powerful primitive for augmenting red-team operations. They can support attack planning, adversary emulation, and the orchestration of multi-step activity such as lateral movement, a core enabling capability of advanced persistent threat (APT) campaigns. Using frameworks such as MITRE ATT&CK, we analyze where these agents intersect with core offensive functions and assess current strengths and limitations of LMAs with an emphasis on governance and realistic evaluation. We benchmark LMAs across two lateral-movement scenarios in a controlled adversary-emulation environment, where LMAs interact with instrumented cyber agents, observe execution artifacts, and iteratively adapt based on environmental feedback. Each scenario is formalized as an ordered task chain with explicit validation predicates, leveraging an LLM-as-a-Judge paradigm to ensure deterministic outcome verification.   We compare three operational modalities: fully autonomous execution, self-scaffolded planning, and expert-defined action plans. Preliminary findings indicate that expert-defined action plans yield higher task-completion rates relative to other operational modes. However, failure remains frequent across all modalities, largely attributable to brittle command invocation, environmental and deployment instability, and recurring errors in credential management and state handling.

- **技术标签**: `agent` `benchmark` `governance` `llm` `rag`


---


## 31. Hybrid Quantum-Classical GANs for the Generation of Adversarial Network Flows

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06629v1)

- **摘要**: Classical generative adversarial networks (GANs) have been applied to generate adversarial network traffic capable of attacking intrusion detection systems, but they suffer from shortcomings such as the need for large amounts of high-dimensional datasets, mode collapse, and high computational overhead. In this work, we propose a hybrid quantum-classical GAN (QC-GAN) framework where a variational quantum generator is used to generate synthetic network traffic flows mimicking malicious traffic using latent representations. Instead of sampling classical noise vectors, we encode the latent vector (the hidden features) as a quantum state, which is the basis for claiming more expressive latent representations and reducing computational overhead. A classical discriminator will be trained on real-world datasets (UNSW-NB15) and the proposed QC-GAN-generated fake network flows. In this configuration, the generator aims to minimize the discriminator's ability to distinguish real from fake traffic, while the discriminator aims to maximize its classification accuracy, in an iterative manner. In our attack model, we assume that the attacker is a state actor with access to limited quantum computing power, whereas the discriminator is chosen to be classical, as will likely be the case for most end users and organizations. We test the generated flows using classical intrusion detection system (IDS) models, such as a random forest classifier and a convolutional neural network-based classifier, for their ability to bypass the detection process. This work aims to highlight the possibilities of quantum machine learning as a means of generating advanced attack flows and stress testing classical IDS. Lastly, we further evaluate how hardware-based noise affects these attacks to offer a new perspective on IDS, highlighting the need for a quantum resilient defense system.

- **技术标签**: `adversarial` `generative`


---


## 32. LiVeAction: a Lightweight, Versatile, and Asymmetric Neural Codec Design for Real-time Operation

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06628v1)

- **摘要**: Modern sensors generate rich, high-fidelity data, yet applications operating on wearable or remote sensing devices remain constrained by bandwidth and power budgets. Standardized codecs such as JPEG and MPEG achieve efficient trade-offs between bitrate and perceptual quality but are designed for human perception, limiting their applicability to machine-perception tasks and non-traditional modalities such as spatial audio arrays, hyperspectral images, and 3D medical images. General-purpose compression schemes based on scalar quantization or resolution reduction are broadly applicable but fail to exploit inherent signal redundancies, resulting in suboptimal rate-distortion performance. Recent generative neural codecs, or tokenizers, model complex signal dependencies but are often over-parameterized, data-hungry, and modality-specific, making them impractical for resource-constrained environments. We introduce a Lightweight, Versatile, and Asymmetric neural codec architecture (LiVeAction), that addresses these limitations through two key ideas. (1) To reduce the complexity of the encoder to meet the resource constraints of the execution environments, we impose an FFT-like structure and reduce the overall size and depth of the neural-network-based analysis transform. (2) To allow arbitrary signal modalities and simplify training, we replace adversarial and perceptual losses with a variance-based rate penalty. Our design produces codecs that deliver superior rate-distortion performance compared to state-of-the-art generative tokenizers, while remaining practical for deployment on low-power sensors. We release our code, experiments, and python library at https://github.com/UT-SysML/liveaction .

- **技术标签**: `adversarial` `generative` `quantization`


---


## 33. ReActor: Reinforcement Learning for Physics-Aware Motion Retargeting

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06593v1)

- **摘要**: Retargeting human kinematic reference motion onto a robot's morphology remains a formidable challenge. Existing methods often produce physical inconsistencies, such as foot sliding, self-collisions, or dynamically infeasible motions, which hinder downstream imitation learning. We propose a bilevel optimization framework that jointly adapts reference motions to a robot's morphology while training a tracking policy using reinforcement learning. To make the optimization tractable, we derive an approximate gradient for the upper-level loss. Our framework requires only a sparse set of semantic rigid-body correspondences and eliminates the need for manual tuning by identifying optimal values for a parameterization expressive enough to preserve characteristic motion across different embodiments. Moreover, by integrating retargeting directly with physics simulation, we produce physically plausible motions that facilitate robust imitation learning. We validate our method in simulation and on hardware, demonstrating challenging motions for morphologies that differ significantly from a human, including retargeting onto a quadruped.

- **技术标签**: `policy`


---


## 34. Distributionally-Robust Learning to Optimize

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06585v1)

- **摘要**: We propose a distributionally robust approach to learning hyperparameters for first-order methods in convex optimization. Given a dataset of problem instances, we minimize a Wasserstein distributionally robust version of the performance estimation problem (PEP) over algorithm parameters such as step sizes. Our framework unifies two extremes: as the robustness radius vanishes, we recover classical learning to optimize (L2O); as it grows, we recover worst-case optimal algorithm design via PEP. We solve the resulting problem with stochastic gradient descent, differentiating through the solution of an inner semidefinite program at each step. We prove high-probability bounds showing that the true risk of the learned algorithm is at most the in-sample L2O optimum plus a slack that shrinks with the sample size, and is no worse than the worst-case PEP bound. On unconstrained quadratic minimization, LASSO, and linear programming benchmarks, our learned algorithms achieve strong out-of-sample performance with certifiable robustness, outperforming both worst-case optimal and vanilla L2O baselines.

- **技术标签**: `benchmark` `robustness`


---


## 35. SNAPO: Smooth Neural Adjoint Policy Optimization for Optimal Control via Differentiable Simulation

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06570v1)

- **摘要**: Many real-world problems require sequential decisions under uncertainty: when to inject or withdraw gas from storage, how to rebalance a pension portfolio each month, what temperature profile to run through a pharmaceutical reactor chain. Dynamic programming solves small instances exactly but scales exponentially in state dimensions. Black-box reinforcement learning handles high-dimensional states but trains slowly and produces no sensitivities. We introduce SNAPO (Smooth Neural Adjoint Policy Optimization), a framework that embeds a neural policy inside a known, differentiable simulator, replaces hard constraints with smooth approximations, and computes exact gradients of the objective with respect to all policy parameters and all inputs in a single adjoint pass. We demonstrate SNAPO on three domains: natural gas storage (training in under a minute, 365 forward curve sensitivities at no additional cost per sensitivity), pension fund asset-liability management (6.5x-200x sensitivity speedup over bump-and-revalue, scaling with the number of risk factors), and pharmaceutical manufacturing (cross-unit sensitivities through a 4-unit process chain, with 20 ICH Q8 regulatory sensitivities from 5 adjoint passes in 74.5 milliseconds). All sensitivities are produced by the same backward pass that trains the policy, at a cost proportional to one reverse pass regardless of how many sensitivities are computed.

- **技术标签**: `policy` `rag`


---


## 36. Dynamic Treatment on Networks

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06564v1)

- **摘要**: In networks, effective dynamic treatment allocation requires deciding both whom to treat and also when, so as to amplify policy impact through spillovers. An early intervention at a well-connected node can trigger cascades that change which nodes are worth targeting in the next period. Existing treatment strategies under network interference are largely static while dynamic treatment frameworks typically ignore network structure altogether. We integrate these perspectives and propose Q-Ising, a three-stage pipeline that (i) estimates network adoption dynamics via a Bayesian dynamic Ising model from a single observed panel, (ii) augments treatment adoption histories with continuous posterior latent states, and (iii) learns a dynamic policy via offline reinforcement learning. The Bayesian mechanism enables uncertainty quantification over dynamic decisions, yielding posterior ensemble policies with interpretable spillover estimates. We provide a finite-sample regret upper bound that decomposes into standard offline-RL uncertainty, network abstraction error, and first stage error in Ising state estimation. We apply our method to data from Indian village microfinance networks and synthetic stochastic block models under simulated heterogeneous susceptible-infected-susceptible (SIS) dynamics and demonstrate that adaptive targeting outperforms static centrality benchmarks.

- **技术标签**: `benchmark` `policy`


---


## 37. Sequential Design of Genetic Circuits Under Uncertainty With Reinforcement Learning

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06552v1)

- **摘要**: The design of biological systems is hindered by uncertainty arising from both intrinsic stochasticity of biomolecular reactions and variability across laboratory or experimental conditions. In this work, we present a sequential framework to optimize genetic circuits under both forms of uncertainty. By employing simulator models based on differential equations or Markov jump processes alongside a reinforcement learning (RL) policy-based approach, our method suggests experiments that adapt to unknown laboratory conditions while accounting for inherent stochasticity. While previous Bayesian methods address uncertainty through iterative experiment-inference-optimization cycles, they typically require computationally expensive inference and optimization steps after each experimental round, leading to delays. To overcome this bottleneck, we propose an amortized approach trained up-front across a distribution of possible uncertain parameters. This strategy sidesteps the need for explicit parameter inference during the design cycle, enabling immediate, observation-based adaptation. We demonstrate our framework on models for heterologous gene expression and a repressilator circuit, showing that it efficiently handles both molecular noise and cross-laboratory variability.

- **技术标签**: `policy`


---


## 38. Hedging Memory Horizons for Non-Stationary Prediction via Online Aggregation

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06541v1)

- **摘要**: We study online prediction under distribution shift, where inputs arrive chronologically and outcomes are revealed only after prediction. In this setting, predictors must remain stable in quiet regimes yet adapt when regimes shift, and the right adaptation memory is unknown in advance. We propose MELO (Memory-hedged Exponentially Weighted Least-Squares Online aggregation), a model-agnostic method that hedges across adaptation scales: it wraps any non-anticipating base-predictor pool with exponentially weighted least-squares (EWLS) adaptation experts at multiple forgetting factors, and aggregates raw and EWLS-adapted forecasts with MLpol, a parameter-free online aggregation rule. Under boundedness conditions, we establish deterministic oracle inequalities showing that it competes with both the best raw predictor and the best bounded, time-varying affine combinations of the base predictions, up to a path-length-dependent tracking cost and a sublinear aggregation overhead. We evaluate MELO on French national electricity-load forecasting through the COVID-19 lockdown using no regime indicators, lockdown dates, or policy covariates. MELO reduces overall RMSE by 34.7\% relative to base-only MLpol and achieves lower overall RMSE than a TabICL reference supplied with an external COVID policy-response covariate. Moreover, MELO requires only lightweight per-step recursive updates without model retraining.

- **技术标签**: `policy`


---


## 39. Diffusion-Based Posterior Sampling: A Feynman-Kac Analysis of Bias and Stability

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06538v1)

- **摘要**: Diffusion-based posterior samplers use pretrained diffusion priors to sample from measurement- or reward-conditioned posteriors, and are widely used for inverse problems. Yet their theoretical behavior remains poorly understood: even with exact prior scores, their outputs are biased, and in low-temperature regimes their discretizations can become unstable. We characterize this bias by introducing a tractable surrogate path connecting the true posterior to a standard Gaussian and comparing it to the sampler's path. Their density ratio satisfies a parabolic PDE whose reaction term measures the accumulated bias. A Feynman-Kac representation then expresses the Radon-Nikodym correction as an explicit path expectation, identifying which posterior regions are over- or under-sampled.   We apply this framework to DPS and STSL, a related sampler. For DPS, the correction is an Ornstein-Uhlenbeck path expectation coupling the data conditional covariance with the reward curvature, revealing where DPS over- or under-samples. Next, we reinterpret STSL as an auxiliary drift that steers trajectories toward low-uncertainty regions, flattening the spatially varying part of the DPS reaction term. Finally, we characterize early guidance-stopping, a common mitigation for low-temperature instabilities caused by forward-Euler integration of the vector field. Together, these results clarify sampler bias, explain existing correctives, and guide stable variant designs.

- **技术标签**: `bias` `diffusion`


---


## 40. Verifier-Backed Hard Problem Generation for Mathematical Reasoning

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06660v1)

- **摘要**: Large Language Models (LLMs) demonstrate strong capabilities for solving scientific and mathematical problems, yet they struggle to produce valid, challenging, and novel problems - an essential component for advancing LLM training and enabling autonomous scientific research. Existing problem generation approaches either depend on expensive human expert involvement or adopt naive self-play paradigms, which frequently yield invalid problems due to reward hacking. This work introduces VHG, a verifier-enhanced hard problem generation framework built upon three-party self-play. By integrating an independent verifier into the conventional setter-solver duality, our design constrains the setter's reward to be jointly determined by problem validity (evaluated by the verifier) and difficulty (assessed by the solver). We instantiate two verifier variants: a Hard symbolic verifier and a Soft LLM-based verifier, with evaluations conducted on indefinite integral tasks and general mathematical reasoning tasks. Experimental results show that VHG substantially outperforms all baseline methods by a clear margin.

- **技术标签**: `large language model` `llm` `reasoning` `research` `reward hacking`


---


## 41. Are We Making Progress in Multimodal Domain Generalization? A Comprehensive Benchmark Study

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06643v1)

- **摘要**: Despite the growing popularity of Multimodal Domain Generalization (MMDG) for enhancing model robustness, it remains unclear whether reported performance gains reflect genuine algorithmic progress or are artifacts of inconsistent evaluation protocols. Current research is fragmented, with studies varying significantly across datasets, modality configurations, and experimental settings. Furthermore, existing benchmarks focus predominantly on action recognition, often neglecting critical real-world challenges such as input corruptions, missing modalities, and model trustworthiness. This lack of standardization obscures a reliable assessment of the field's advancement. To address this issue, we introduce MMDG-Bench, the first unified and comprehensive benchmark for MMDG, which standardizes evaluation across six datasets spanning three diverse tasks: action recognition, mechanical fault diagnosis, and sentiment analysis. MMDG-Bench encompasses six modality combinations, nine representative methods, and multiple evaluation settings. Beyond standard accuracy, it systematically assesses corruption robustness, missing-modality generalization, misclassification detection, and out-of-distribution detection. With 7, 402 neural networks trained in total across 95 unique cross-domain tasks, MMDG-Bench yields five key findings: (1) under fair comparisons, recent specialized MMDG methods offer only marginal improvements over ERM baseline; (2) no single method consistently outperforms others across datasets or modality combinations; (3) a substantial gap to upper-bound performance persists, indicating that MMDG remains far from solved; (4) trimodal fusion does not consistently outperform the strongest bimodal configurations; and (5) all evaluated methods exhibit significant degradation under corruption and missing-modality scenarios, with some methods further compromising model trustworthiness.

- **技术标签**: `benchmark` `multimodal` `rag` `research` `robustness`


---


## 42. MASPO: Joint Prompt Optimization for LLM-based Multi-Agent Systems

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06623v1)

- **摘要**: Large language model (LLM)-based Multi-agent systems (MAS) have shown promise in tackling complex collaborative tasks, where agents are typically orchestrated via role-specific prompts. While the quality of these prompts is pivotal, jointly optimizing them across interacting agents remains a non-trivial challenge, primarily due to the misalignment between local agent objectives and holistic system goals. To address this, we introduce MASPO, a novel framework designed to automatically and iteratively refine prompts across the entire system. A core innovation of MASPO is its joint evaluation mechanism, which assesses prompts not merely by their local validity, but by their capacity to facilitate downstream success for successor agents. This effectively bridges the gap between local interactions and global outcomes without relying on ground-truth labels. Furthermore, MASPO employs a data-driven evolutionary beam search to efficiently navigate the high-dimensional prompt space. Extensive empirical evaluations across 6 diverse tasks demonstrate that MASPO consistently outperforms state-of-the-art prompt optimization methods, achieving an average accuracy improvement of 2.9. We release our code at https://github.com/wangzx1219/MASPO.

- **技术标签**: `agent` `alignment` `large language model` `llm` `rag`


---


## 43. UniSD: Towards a Unified Self-Distillation Framework for Large Language Models

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06597v1)

- **摘要**: Self-distillation (SD) offers a promising path for adapting large language models (LLMs) without relying on stronger external teachers. However, SD in autoregressive LLMs remains challenging because self-generated trajectories are free-form, correctness is task-dependent, and plausible rationales can still provide unstable or unreliable supervision. Existing methods mainly examine isolated design choices, leaving their effectiveness, roles, and interactions unclear. In this paper, we propose UniSD, a unified framework to systematically study self-distillation. UniSD integrates complementary mechanisms that address supervision reliability, representation alignment, and training stability, including multi-teacher agreement, EMA teacher stabilization, token-level contrastive learning, feature matching, and divergence clipping. Across six benchmarks and six models from three model families, UniSD reveals when self-distillation improves over static imitation, which components drive the gains, and how these components interact across tasks. Guided by these insights, we construct UniSDfull, an integrated pipeline that combines complementary components and achieves the strongest overall performance, improving over the base model by +5.4 points and the strongest baseline by +2.8 points. Extensive evaluation highlights self-distillation as a practical and steerable approach for efficient LLM adaptation without stronger external teachers.

- **技术标签**: `alignment` `benchmark` `distillation` `large language model` `llm`


---


## 44. Cross-Modal Navigation with Multi-Agent Reinforcement Learning

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06595v1)

- **摘要**: Robust embodied navigation relies on complementary sensory cues. However, high-quality and well-aligned multi-modal data is often difficult to obtain in practice. Training a monolithic model is also challenging as rich multi-modal inputs induce complex representations and substantially enlarge the policy space. Cross-modal collaboration among lightweight modality-specialized agents offers a scalable paradigm. It enables flexible deployment and parallel execution, while preserving the strength of each modality. In this paper, we propose \textbf{CRONA}, a Multi-Agent Reinforcement Learning (MARL) framework for \textbf{Cro}ss-Modal \textbf{Na}vigation. CRONA improves collaboration by leveraging control-relevant auxiliary beliefs and a centralized multi-modal critic with global state. Experiments on visual-acoustic navigation tasks show that multi-agent methods significantly improve performance and efficiency over single-agent baselines. We find that homogeneous collaboration with limited modalities is sufficient for short-range navigation under salient cues; heterogeneous collaboration among agents with complementary modalities is generally efficient and effective; and navigation in large, complex environments requires both richer multi-modal perception and increased model capacity.

- **技术标签**: `agent` `efficiency` `policy` `rag`


---


## 45. DINORANKCLIP: DINOv3 Distillation and Injection for Vision-Language Pretraining with High-Order Ranking Consistency

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06592v1)

- **摘要**: Contrastive language-image pretraining (CLIP) suffers from two structural weaknesses: the symmetric InfoNCE loss discards the relative ordering among unmatched in-batch pairs, and global pooling collapses the visual representation into a semantic bottleneck that is poorly sensitive to fine-grained local structure. RANKCLIP partially addresses the first issue with a list-wise Plackett-Luce ranking-consistency loss, but its model is strictly first-order and inherits the second weakness untouched. We propose DINORANKCLIP, a pretraining framework that addresses both jointly. Our principal contribution is injecting a frozen DINOv3 teacher into the contrastive trunk through a dual-branch lightweight student and a multi-scale fusion module with channel-spatial attention, a self-attention refiner, and a conflict-aware gate that preserves the cross-modal alignment up to first order. Complementarily, we introduce a high-order Plackett-Luce ranking model in which the per-position utility is augmented with attention-parameterised pairwise and tuple-wise transition terms; the family contains CLIP and RANKCLIP as nested zero-order and first-order special cases, and the optimal order on every benchmark is $R^*=3$. The full empirical study -- order sweep, Fine-grained Probe on five datasets, four-node Modality-Gap analysis, six-variant Fusion ablation -- fits in 72 hours on a single eight-GPU H100 node and trains entirely on Conceptual Captions 3M. DINORANKCLIP consistently outperforms CLIP, CyCLIP, ALIP, and RANKCLIP under matched compute, with the largest relative gains on the fine-grained and out-of-distribution evaluations that most directly stress local structural reasoning.

- **技术标签**: `alignment` `benchmark` `distillation` `pretraining` `reasoning`


---


## 46. Towards Metric-Faithful Neural Graph Matching

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06588v1)

- **摘要**: Graph Edit Distance (GED) is a fundamental, albeit NP-hard, metric for structural graph similarity. Recent neural graph matching architectures approximate GED by first encoding graphs with a Graph Neural Network (GNN) and then applying either a graph-level regression head or a matching-based alignment module. Despite substantial architectural progress, the role of encoder geometry in neural GED estimation remains poorly understood. In this paper, we develop a theoretical framework that connects encoder geometry to GED estimation quality for two broad classes of neural GED estimators: graph similarity predictors and alignment-based methods. On fixed graph collections, where the doubly-stochastic metric $d_{\mathrm{DS}}$ is comparable to GED, we show that graph-level bi-Lipschitz encoders yield controlled GED surrogates and improved ranking stability; for matching-based estimators, node-level bi-Lipschitz geometry propagates to encoder-induced alignment costs and the resulting optimized alignment objective. We instantiate this perspective using FSW-GNN, a bi-Lipschitz WL-equivalent encoder, as a drop-in replacement in representative neural GED architectures. Across representative baselines and benchmark datasets, the resulting geometry-aware variants significantly improve GED prediction and ranking metrics. A faithfulness case study of untrained encoders, together with ablations and transfer experiments, supports the view that these gains arise from improved representation geometry, positioning encoder geometry as a useful design principle for neural graph matching.

- **技术标签**: `alignment` `benchmark`


---


## 47. Directional Consistency as a Complementary Optimization Signal: The GONO Framework

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06575v1)

- **摘要**: We identify and formalize an underexplored phenomenon in deep learning optimization: directional alignment and loss convergence can be decoupled. An optimizer can exhibit near-perfect directional consistency (cc_t -> 1, measured via consecutive gradient cosine similarity) while the loss remains high or decreases slowly. This observation reveals that existing optimizers such as Adam, SGD, and RMSprop lack explicit mechanisms to exploit temporal consistency in gradient directions, relying instead on magnitude-based signals that fail to distinguish plateaus, saddle points, and genuine convergence. Motivated by this, we introduce GONO (Gradient-Oriented Norm-Adaptive Optimizer), which adapts Adam's momentum coefficient beta_1 based on cc_t: amplifying momentum under directional consistency and suppressing it during oscillation. We prove GONO matches Adam's O(1/sqrt(T)) convergence rate and reduces exactly to Adam when the signal is uninformative. Empirically, cc_t achieves oscillation detection with F1=1.00 (vs. 0.45 for gradient norm), and GONO remains competitive with AdamW on MNIST (98.15%), CIFAR-10 (43.14%), and ResNet-18 (75.44%), establishing directional alignment as a theoretically grounded, practically actionable optimization signal. Code: https://github.com/victordaniel/gono-optimizer

- **技术标签**: `alignment`


---


## 48. Continuous Latent Diffusion Language Model

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06548v1)

- **摘要**: Large language models have achieved remarkable success under the autoregressive paradigm, yet high-quality text generation need not be tied to a fixed left-to-right order. Existing alternatives still struggle to jointly achieve generation efficiency, scalable representation learning, and effective global semantic modeling. We propose Cola DLM, a hierarchical latent diffusion language model that frames text generation through hierarchical information decomposition. Cola DLM first learns a stable text-to-latent mapping with a Text VAE, then models a global semantic prior in continuous latent space with a block-causal DiT, and finally generates text through conditional decoding. From a unified Markov-path perspective, its diffusion process performs latent prior transport rather than token-level observation recovery, thereby separating global semantic organization from local textual realization. This design yields a more flexible non-autoregressive inductive bias, supports semantic compression and prior fitting in continuous space, and naturally extends to other continuous modalities. Through experiments spanning 4 research questions, 8 benchmarks, strictly matched ~2B-parameter autoregressive and LLaDA baselines, and scaling curves up to about 2000 EFLOPs, we identify an effective overall configuration of Cola DLM and verify its strong scaling behavior for text generation. Taken together, the results establish hierarchical continuous latent prior modeling as a principled alternative to strictly token-level language modeling, where generation quality and scaling behavior may better reflect model capability than likelihood, while also suggesting a concrete path toward unified modeling across discrete text and continuous modalities.

- **技术标签**: `benchmark` `bias` `diffusion` `efficiency` `large language model`


---


## 49. On the Implicit Reward Overfitting and the Low-rank Dynamics in RLVR

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06523v1)

- **摘要**: Recent extensive research has demonstrated that the enhanced reasoning capabilities acquired by models through Reinforcement Learning with Verifiable Rewards (RLVR) are primarily concentrated within the rank-1 components. Predicated on this observation, we employed Periodic Rank-1 Substitution and identified a counterintuitive phenomenon: RLVR may exhibit implicit reward overfitting to the training dataset. Specifically, the model can achieve satisfactory performance on the test set even when its rewards remain relatively low during the training process. Furthermore, we characterize three distinct properties of RL training: (1) The effective rank-1 component in RLVR don't maintain other model knowledge except mathematical reasoning capability. (2) RLVR fundamentally functions by optimizing a specific singular spectrum. The distribution of singular values of almost all linear layers in RLVR-trained model behaves like heavy-tailed distribution. (3) the left singular vectors associated with rank-1 components demonstrate a stronger alignment tendency during training, which echoes the discovery that RLVR is optimizing sampling efficiency in essence. Taken together, our findings and analysis further reveal how RLVR shapes model parameters and offer potential insights for improving existing RL paradigms or other training paradigms to implement continual learning.

- **技术标签**: `alignment` `efficiency` `reasoning` `research`


---


## 50. Learning to Cut: Reinforcement Learning for Benders Decomposition

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06516v1)

- **摘要**: Benders decomposition (BD) is a widely used solution approach for solving two-stage stochastic programs arising in real-world decision-making under uncertainty. However, it often suffers from slow convergence as the master problem grows with an increasing number of cuts. In this paper, we propose Reinforcement Learning for BD (RLBD), a framework that adaptively selects cuts using a neural network-based stochastic policy. The policy is trained using a policy gradient method via the REINFORCE algorithm. We evaluate the proposed approach on a two-stage stochastic electric vehicle charging station location problem and compare it with vanilla BD and LearnBD, a supervised learning approach that classifies cuts using a support vector machine. Numerical results demonstrate that RLBD achieves substantial improvements in computational efficiency and exhibits strong generalization to problems with similar structures but varying data inputs and decision variable dimensions.

- **技术标签**: `efficiency` `policy`


---


## 51. PACZero: PAC-Private Fine-Tuning of Language Models via Sign Quantization

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06505v1)

- **摘要**: We introduce PACZero, a family of PAC-private zeroth-order mechanisms for fine-tuning large language models that delivers usable utility at $I(S^*; Y_{1:T})=0$. This privacy regime bounds the membership-inference attack (MIA) posterior success rate at the prior, an MIA-resistance level the DP framework matches only at $\varepsilon=0$ and infinite noise. All DP-ZO comparisons below are matched at the MIA posterior level. The key insight is that PAC Privacy charges mutual information only when the release depends on which candidate subset is the secret. Sign-quantizing subset-aggregated zeroth-order gradients creates frequent unanimity, steps at which every candidate subset agrees on the update direction; at these steps the released sign costs zero conditional mutual information. We propose two variants that span the privacy-utility trade-off: PACZero-MI (budgeted MI via exact calibration on the binary release) and PACZero-ZPL ($I=0$ via a uniform coin flip on disagreement steps). We evaluate on SST-2 and SQuAD with OPT-1.3B and OPT-6.7B in both LoRA and full-parameter tracks. On SST-2 OPT-1.3B full fine-tuning at $I=0$, PACZero-ZPL reaches ${88.99\pm0.91}$, within $2.1$pp of the non-private MeZO baseline ($91.1$ FT). No prior method produces usable utility in the high-privacy regime $\varepsilon<1$, and PACZero-ZPL obtains competitive SST-2 accuracy and nontrivial SQuAD F1 across OPT-1.3B and OPT-6.7B at $I=0$.

- **技术标签**: `fine-tuning` `large language model` `privacy` `quantization`


---


## 52. Operator-Guided Invariance Learning for Continuous Reinforcement Learning

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06500v1)

- **摘要**: Reinforcement learning (RL) with continuous time and state/action spaces is often data-intensive and brittle under nuisance variability and shift, motivating methods that exploit value-preserving structures to stabilize and improve learning. Most existing approaches focus on special cases, such as prescribed symmetries and exact equivariance, without addressing how to discover more general structures that require nonlinear operators to transform and map between continuous state/action systems with isomorphic value functions. We propose \textbf{VPSD-RL} (Value-Preserving Structure Discovery for Reinforcement Learning). It models continuous RL as a controlled diffusion with value-preserving mappings defined through Lie-group actions and associated pullback operators. We show that a value-preserving structure exists exactly when pulling back the value function and pushing forward actions commute with the controlled generator and reward functional. Further, approximate value-preserving structures with rigorous guarantees can be found when the Hamilton--Jacobi--Bellman mismatch is small. This framework discovers exact and approximate value-preserving structures by searching for the associated Lie group operators. VPSD-RL fits differentiable drift, diffusion, and reward models; learns infinitesimal generators via determining-equation residual minimization; exponentiates them with ODE flows to obtain finite transformations; and integrates them into continuous RL through transition augmentation and transformation-consistency regularization. We show that bounded generator/reward mismatch implies quantitative stability of the optimal value function along approximate orbits, with sensitivity governed by the effective horizon, and observe improved data efficiency and robustness on continuous-control benchmarks.

- **技术标签**: `benchmark` `diffusion` `efficiency` `llm` `robustness`


---


## 53. Instrumental Choices: Measuring the Propensity of LLM Agents to Pursue Instrumental Behaviors

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06490v1)

- **摘要**: AI systems have become increasingly capable of dangerous behaviours in many domains. This raises the question: Do models sometimes choose to violate human instructions in order to perform behaviour that is more useful for certain goals? We introduce a benchmark for measuring model propensity for instrumental convergence (IC) behaviour in terminal-based agents. This is behaviour such as self-preservation that has been hypothesised to play a key role in risks from highly capable AI agents. Our benchmark is realistic and low-stakes which serves to reduce evaluation-awareness and roleplay confounds. The suite contains seven operational tasks, each with an official workflow and a policy-violating shortcut. An eight-variant shared framework varies monitoring, instruction clarity, stakes, permission, instrumental usefulness and blocked honest paths to support inferences regarding the factors driving IC behaviour. We evaluated ten models using deterministic environment-state scorers over 1,680 samples, with trace review employed for audit and adjudication purposes. The final IC rate is 86 out of 1,680 samples (5.1%). IC behaviour is concentrated rather than uniform: two Gemini models account for 66.3% of IC cases and three tasks account for 84.9%. Conditions in which IC behaviour is indispensable for task success result in the greatest increase in the adjusted IC rate (+15.7 percentage points), whereas emphasising that task success is critical or certain framing choices do not produce comparable effects. Our findings indicate that realistic, low-nudge environments elicit IC behaviour rarely but systematically in most tested models. We conclude that it is feasible to robustly measure tendencies for dangerous behaviour in current frontier AI agents.

- **技术标签**: `agent` `benchmark` `gemini` `llm` `policy`


---


## 54. ReasonSTL: Bridging Natural Language and Signal Temporal Logic via Tool-Augmented Process-Rewarded Learning

- **来源**: [arxiv_ai](https://arxiv.org/abs/2605.06483v1)

- **摘要**: Signal Temporal Logic (STL) is an expressive formal language for specifying spatio-temporal requirements over real-valued, real-time signals. It has been widely used for the verification and synthesis of autonomous systems and cyber-physical systems. In practice, however, users often express their requirements in natural language rather than in structured STL formulas, making natural-language-to-STL translation a critical yet challenging task. Manual specification requires temporal-logic expertise and cannot scale, while prompting commercial LLM APIs incurs substantial token costs and may expose sensitive system requirements to third-party services, raising privacy concerns for industrial deployment. To address these challenges, we present \textsc{ReasonSTL}, a tool-augmented framework that adapts local open-source language models for natural-language-to-STL generation. \textsc{ReasonSTL} decomposes the translation process into explicit reasoning, deterministic tool calls, and structured formula construction. We further introduce process-rewarded training to supervise both tool-use trajectories and final formulas, together with \textsc{STL-Bench}, a bilingual, computation-aware benchmark grounded in real-world signals. Experiments show that a 4B model trained with \textsc{ReasonSTL} achieves state-of-the-art performance in both automatic metrics and human evaluations, demonstrating that \textsc{ReasonSTL} provides a transparent, low-cost, and privacy-preserving alternative for formal specification drafting.

- **技术标签**: `benchmark` `llm` `privacy` `reasoning`


---


## 55. PairAlign: A Framework for Sequence Tokenization via Self-Alignment with Applications to Audio Tokenization

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06582v1)

- **摘要**: Many operations on sensory data -- comparison, memory, retrieval, and reasoning -- are naturally expressed over discrete symbolic structures. In language this interface is given by tokens; in audio, it must be learned. Existing audio tokenizers rely on quantization, clustering, or codec reconstruction, assigning tokens locally, so sequence consistency, compactness, length control, termination, and edit similarity are rarely optimized directly.   We introduce PairAlign, a framework for compact audio tokenization through sequence-level self-alignment. PairAlign treats tokenization as conditional sequence generation: an encoder maps speech to a continuous condition, and an autoregressive decoder generates tokens from BOS, learning token identity, order, length, and EOS placement. Given two content-preserving views, each view's sequence is trained to be likely under the other's representation, while unrelated examples provide competing sequences. This gives a scalable surrogate for edit-distance preservation while discouraging many-to-one collapse.   PairAlign starts from VQ-style tokenization and refines it with EMA-teacher targets, cross-paired teacher forcing, prefix corruption, likelihood contrast, and length control.   On 3-second speech, PairAlign learns compact, non-degenerate sequences with broad vocabulary usage and strong cross-view consistency. On TIMIT retrieval, it preserves edit-distance search while reducing archive token count by 55%. A continuous-sweep probe shows lower local overlap than a dense geometric tokenizer, but stronger length control and bounded edit trajectories under 100 ms shifts. PairAlign is a sequence-symbolic predictive learner: like JEPA-style objectives, it predicts an abstract target from another view as a learned variable-length symbolic sequence, not a continuous latent.

- **技术标签**: `alignment` `quantization` `rag` `reasoning`


---


## 56. STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06527v1)

- **摘要**: Large Language Model (LLM) agents are increasingly expected to maintain coherent, long-term personalized memory, yet current benchmarks primarily measure static fact retrieval, overlooking the ability to revise stored beliefs when new evidence emerges. We identify a critical and underexplored failure mode, Implicit Conflict: a later observation invalidates an earlier memory without explicit negation, requiring contextual inference and commonsense reasoning to detect. To rigorously evaluate this capability, we introduce STALE, a benchmark of 400 expert-validated conflict scenarios (1,200 evaluation queries across three probing dimensions) spanning over 100 everyday topics with contexts up to 150K tokens. We propose a three-dimensional probing framework that tests State Resolution (detecting that a prior belief is outdated), Premise Resistance (rejecting queries that falsely presuppose a stale state), and Implicit Policy Adaptation (proactively applying updated states in downstream behavior). A systematic evaluation of frontier LLMs and specialized memory frameworks reveals a pervasive gap between retrieving updated evidence and acting on it, with even the best evaluated model achieving only 55.2% overall accuracy. Models often accept outdated assumptions embedded in a user's query, and they struggle to recognize when a change in one aspect of the user's state should invalidate related memories. To establish an initial baseline for state-aware memory, we further present CUPMem, a prototype that strengthens write-time revision through structured state consolidation and propagation-aware search, suggesting that explicit state adjudication is a promising direction for robust agentic memory.

- **技术标签**: `agent` `benchmark` `large language model` `llm` `policy`


---


## 57. Invariant Features in Language Models: Geometric Characterization and Model Attribution

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06458v1)

- **摘要**: Language models exhibit strong robustness to paraphrasing, suggesting that semantic information may be encoded through stable internal representations, yet the structure and origin of such invariance remain unclear. We propose a local geometric framework in which semantically equivalent inputs occupy structured regions in latent space, with paraphrastic variation along nuisance directions and semantic identity preserved in invariant subspaces. Building on this view, we make three contributions: (1) a geometric characterization of invariant latent features, (2) a contrastive subspace discovery method that separates semantic-changing from semantic-preserving variation, and (3) an application of invariant representations to zero-shot model attribution. Across models and layers, empirical results support these contributions. Invariant structure emerges in specific depth regions, semantic displacement lies largely outside the nuisance subspace, and representation-level interventions indicate a causal role of invariant components in model outputs. Invariant representations also capture model-specific geometric patterns, enabling accurate attribution. These findings suggest that semantic invariance can be viewed as a local geometric property of latent representations, offering a principled perspective on how language models organize meaning.

- **技术标签**: `robustness`


---


## 58. Gaming the Metric, Not the Harm: Certifying Safety Audits against Strategic Platform Manipulation

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06324v1)

- **摘要**: Online-safety regulation under the UK Online Safety Act and the EU Digital Services Act increasingly treats scalar metrics as compliance evidence. Once announced, such a metric also becomes an optimization target: a strategic platform can improve its score by routing recommendations through semantically equivalent content variants, without reducing true harm. We ask when such an audit metric can still certify a genuine reduction in harm. The protocol is modeled as a published transformation graph whose connected components form semantic classes, and the metric itself is treated as a security object. Three results follow. First, any metric that scores variants directly is manipulable as soon as two equivalent variants in a harmful class disagree in score. Second, the semantic-envelope lift, which assigns each variant the maximum score in its class, is the unique pointwise minimum among conservative classwise-constant repairs. Third, a class-stratified certificate, $H^\star(x) \le (1/\hatα) M_{\mathrm{Env}(m)}(x) + \barη$, holds for every platform strategy, with $\barη$ absorbing annotation and protocol error. We check the claims at three levels: exhaustive enumeration on a finite-state grid of mixed strategies, an SMT encoding in Z3 cross-replayed in cvc5, and a bounded single-player MDP encoded in PRISM-games. The fragile metric fails manipulation invariance and cannot support the same useful predeclared class-coverage certificate; under the envelope-level certificate, it produces large violations at every tested instance, with a large mean gaming gap across random catalogs at a fixed audit budget. The semantic-envelope metric exhibits no such violation in the tested instances.

- **技术标签**: `rag` `regulation`


---


## 59. Stateful Agent Backdoor

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06158v1)

- **摘要**: Existing backdoor attacks on Large Language Model-based agents remain stateless, executing fixed behaviors confined to a single session. We propose a stateful agent backdoor that extends the attack lifecycle across multiple sessions under permission isolation. The attack maintains state through persistent components, enabling autonomous, incremental execution across sessions following a one-time trigger injection. Formally, we model the attack as a Mealy machine and derive a decomposition framework that enables independent per-transition data construction. We instantiate this framework with a primary attack and two extensibility variants. The primary instantiation achieves an attack success rate of 80\%--95\% across four models, with per-transition analysis demonstrating the effectiveness of the decomposition. Extensibility variants with alternative topologies and persistent components demonstrate consistent effectiveness. Code and data are available at https://anonymous.4open.science/r/stateful_agent_backdoor-E89F.

- **技术标签**: `agent` `backdoor` `large language model`


---


## 60. Secure Seed-Based Multi-bit Watermarking for Diffusion Models from First Principles

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.06153v1)

- **摘要**: The rapid emergence of generative image models has led to the development of specialized watermarking techniques, particularly in-generation methods such as seed-based embedding. However, current evaluations in this area remain largely empirical, making them heavily reliant on the specific model architectures used for generation and inversion. This prevents any clear conclusion on the performance of any method, especially regarding security, for which a rigorous definition is lacking. Against this approach, we argue that the effectiveness of a watermarking scheme should be established purely through a thorough theoretical analysis. This is enabled by decoupling the model-dependent part from the actual decision mechanism of the watermarking system. Using this decoupling, we introduce a formal evaluation framework based on security, robustness, and fidelity. This allows precise comparisons between watermarking systems through a characteristic surface representing the trade-off between these three quantities, independent of any generative model. Based on this framework, we propose SSB, a novel watermarking method that generalizes previous seed-based methods by allowing to reach any security-robustness-fidelity regime on its characteristic surface. This work opens the door to the design of modern watermarking systems with theoretical guarantees that do not necessitate any costly empirical evaluations.

- **技术标签**: `diffusion` `embedding` `generative` `robustness`


---


## 61. Safety Anchor: Defending Harmful Fine-tuning via Geometric Bottlenecks

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05995v1)

- **摘要**: The safety alignment of Large Language Models (LLMs) remains vulnerable to Harmful Fine-tuning (HFT). While existing defenses impose constraints on parameters, gradients, or internal representations, we observe that they can be effectively circumvented under persistent HFT. Our analysis traces this failure to the inherent redundancy of the high-dimensional parameter space: attackers exploit optimization trajectories that are orthogonal to defense constraints to restore harmful capabilities while deceptively adhering to safety restrictions. To address this, we propose Safety Bottleneck Regularization (SBR). SBR shifts the defensive focus from the redundant parameter space to the unembedding layer, which serves as a geometric bottleneck. By anchoring the final hidden states of harmful queries to those of the safety-aligned model, SBR enables the model to maintain safe responses even under persistent HFT. Extensive experiments confirm SBR's effectiveness, demonstrating that utilizing just a single safety anchor is sufficient to reduce the Harmful Score to $<$10 while preserving competitive performance on benign downstream tasks.

- **技术标签**: `alignment` `embedding` `fine-tuning` `large language model` `llm`


---


## 62. LeakDojo: Decoding the Leakage Threats of RAG Systems

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05818v1)

- **摘要**: Retrieval-Augmented Generation (RAG) enables large language models (LLMs) to leverage external knowledge, but also exposes valuable RAG databases to leakage attacks. As RAG systems grow more complex and LLMs exhibit stronger instruction-following capabilities, existing studies fall short of systematically assessing RAG leakage risks. We present LeakDojo, a configurable framework for controlled evaluation of RAG leakage. Using LeakDojo, we benchmark six existing attacks across fourteen LLMs, four datasets, and diverse RAG systems. Our study reveals that (1) query generation and adversarial instructions contribute independently to leakage, with overall leakage well approximated by their product; (2) stronger instruction-following capability correlates with higher leakage risk; and (3) improvements in RAG faithfulness can introduce increased leakage risk. These findings provide actionable insights for understanding and mitigating RAG leakage in practice. Our codebase is available at https://github.com/yeasen-z/LeakDojo.

- **技术标签**: `adversarial` `benchmark` `large language model` `llm` `rag`


---


## 63. Stego Battlefield: Evaluating Image Steganography Attacks and Steganalysis Defenses

- **来源**: [arxiv_cr](https://arxiv.org/abs/2605.05789v1)

- **摘要**: Image steganography is widely used to protect user privacy and enable covert communication. However, it can also be abused by the adversary as a covert channel to bypass content moderation, disseminate harmful semantics, and even hide malicious instructions in images to elicit dangerous outputs from large models, posing a practical security risk that continues to evolve. To address the lack of a unified and systematic evaluation framework, we propose SADBench, a systematic benchmark that assesses the adversary's ability to inject harmful secrets via steganography and the defender's ability to detect such threats through steganalysis. Crucially, SADBench comprises $4$ core tasks, namely steganography attack capability evaluation, steganalysis defense capability evaluation, efficiency evaluation, and transferability evaluation. It evaluates both image-payload and text-payload steganography across diverse cover distributions, utilizing harmful visual semantics and toxic instructions to simulate malicious attacks. Across a broad set of attacks and detectors, SADBench reveals that (i) INN and autoencoder-based methods demonstrate superior stability compared to other architectures, (ii) in-domain detection is near-perfect and cheaper than generation, (iii) a critical asymmetry exists in transferability where attacks robustly generalize to new distributions while detectors fail to adapt, and (iv) real-world threats persist on social media, where payloads either survive minimal compression or effectively adapt to aggressive compression via simulated training. Overall, SADBench establishes a systematic, reproducible, and extensible framework to quantify risks, paving the way for measurable and security-driven advancements in steganography defense.

- **技术标签**: `benchmark` `efficiency` `privacy`


---


## 64. Is Escalation Worth It? A Decision-Theoretic Characterization of LLM Cascades

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06350v1)

- **摘要**: Model cascades, in which a cheap LLM defers to an expensive one on low-confidence queries, are widely used to navigate the cost-quality tradeoff at deployment. Existing approaches largely treat the deferral threshold as an empirical hyperparameter, with limited guidance on the geometry of the resulting cost-quality frontier over a model pool. We develop a decision-theoretic framework grounded in constrained optimization and duality. For a two-model cascade, we establish piecewise concavity of the cost-quality frontier on decreasing-benefit regions of the confidence support, with reciprocal shadow prices linking the budget- and quality-constrained formulations. Given a pool of $k$ models, we characterize the frontier achievable by deterministic two-model threshold cascades as the pointwise envelope over $\binom{k}{2}$ pairwise cascades, with switching points where the optimal pair changes. For $k$-model cascades, we derive first-order conditions in which a single shadow price equalizes marginal quality-per-cost across stage boundaries. We validate the framework on five benchmarks (MATH, MMLU, TriviaQA, SimpleQA, LiveCodeBench) across eight models from five providers. Within the deterministic threshold-cascade class, full fixed chains underperform the pairwise envelope, and optimized subsequence cascades do not deliver practically meaningful held-out gains over it. A lightweight pre-generation router exceeds the best cascade policy on four of five datasets, mainly because it avoids the cheap model's generation cost on queries sent directly to a larger model rather than because of a stronger routing signal. These results suggest that cascade performance is limited primarily by structural cost, since cascades pay the cheap model before any escalation decision, rather than by a shortage of intermediate stages.

- **技术标签**: `benchmark` `llm` `policy`


---


## 65. Measuring Evaluation-Context Divergence in Open-Weight LLMs: A Paired-Prompt Protocol with Pilot Evidence of Alignment-Pipeline-Specific Heterogeneity

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06327v1)

- **摘要**: Safety benchmarks are routinely treated as evidence about how a language model will behave once deployed, but this inference is fragile if behavior depends on whether a prompt looks like an evaluation. We define evaluation-context divergence as an observable within-item change in behavior induced by framing a fixed task as an evaluation, a live deployment interaction, or a neutral request, and present a paired-prompt protocol that measures it in open-weight LLMs while controlling for paraphrase variation, benchmark familiarity, and judge framing-sensitivity.   Across five instruction-tuned checkpoints from four open-weight families plus a matched OLMo-3 base/instruct ablation ($20$ paired items, $840$ generations per checkpoint), we find striking heterogeneity. OLMo-3-Instruct alone is eval-cautious -- evaluation framing raises refusal vs. neutral by $11.8$pp ($p=0.007$) and reduces harmful compliance vs. deployment by $3.6$pp ($p=0.024$, $0/20$ items inverted) -- while Mistral-Small-3.2, Phi-3.5-mini, and Llama-3.1-8B are deployment-cautious}, with marginal eval-vs-deployment refusal effects of $-9$ to $-20$pp. The matched OLMo-3 base also exhibits the deployment-cautious pattern, identifying alignment as the inversion stage; within Llama-3.1, the $70$B model preserves direction with attenuated magnitude, ruling out a simple ``small-model effect that reverses at scale.'' One caveat: the cross-family heterogeneity is judge-dependent. Re-judging with a different-family safety classifier (Llama-Guard-3-8B) preserves the within-OLMo eval-cautious direction but flattens the cross-family contrast, indicating that the two judges operationalize distinct constructs.

- **技术标签**: `alignment` `benchmark` `llm` `rag`


---


## 66. Quantifying the Statistical Effect of Rubric Modifications on Human-Autorater Agreement

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06283v1)

- **摘要**: Autoraters, also referred to as LLM-as-judges, are increasingly used for evaluation and automated content moderation. However, there is limited statistical analysis of how modifications in a rubric presented to both humans and autoraters affect their score agreement. Rubrics that ask for an overall or \emph{holistic} judgment - for example, rating the ``quality'' of an essay - may be inconsistently interpreted due to the complexity or subjectivity of the criteria. Conversely, rubrics can ask for \emph{analytic} judgments, which decompose assessment criteria - for example, ``quality'' into ``fluency'' and ``organization''. While these rubrics can be edited to improve the individual accuracy of both human and automated scoring, this approach may result in disagreement between the two scores, or with the associated holistic judgment. Designing and deploying reliable autoraters requires understanding not just the relationship between human and autorater annotations but how that relationship changes as holistic or analytic judgments are elicited. The results indicate that rubric edits providing representative examples and additional context, and reducing positional bias in the rubric increased human-autorater agreement, while higher rubric complexity and conservative aggregation methods tended to decrease it. The findings from the automatic essay scoring and instruction-following evaluation domains suggest that practitioners should carefully analyze domain- and rubric-specific performance to move towards higher human-autorater agreement.

- **技术标签**: `bias` `llm`


---


## 67. Linear Semantic Segmentation for Low-Resource Spoken Dialects

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06276v1)

- **摘要**: Semantic segmentation is a core component of discourse analysis, yet existing models are primarily developed and evaluated on high-resource written text, limiting their effectiveness on low-resource spoken varieties. In particular, dialectal Arabic exhibits informal syntax, code-switching, and weakly marked discourse structure that challenge standard segmentation approaches. In this paper, we introduce a new multi-genre benchmark (more than 1000 samples) for semantic segmentation in conversational Arabic, focusing on dialectal discourse. The benchmark covers transcribed casual telephone conversations, code-switched podcasts, broadcast news, and expressive dialogue from novels, and was annotated and validated by native Arabic annotators. Using this benchmark, we show that segmentation models performing well on MSA news genres degrade on dialectal transcribed speech. We further propose a segmentation model that targets local semantic coherence and robustness to discourse discontinuities, consistently outperforming strong baselines on dialectal non-news genres. The benchmark and approach generalize to other low-resource spoken languages.

- **技术标签**: `benchmark` `robustness`


---


## 68. Rethinking RL for LLM Reasoning: It's Sparse Policy Selection, Not Capability Learning

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06241v1)

- **摘要**: Reinforcement learning has become the standard for improving reasoning in large language models, yet evidence increasingly suggests that RL does not teach new strategies; it redistributes probability mass over solutions the base model already contains. In this work, we ask: if RL merely steers the model toward paths it already knows, is the RL optimization loop itself necessary? Through token-level analysis across multiple model families and RL algorithms, we find that RL's beneficial footprint is a sparse, predictable correction concentrated at high-entropy decision points where the model is uncertain which branch to take. Only 1--3\% of token positions are affected, the promoted token always lies within the base model's top-5 alternatives, and targeted corrections at those few positions causally recover a large fraction of RL's accuracy gain, while random corrections fail. The base model's own entropy identifies these positions without any RL-trained model, and the entire correction is low-dimensional, representable in a tiny fraction of model parameters. These findings reframe reasoning improvement as sparse policy selection, not capability acquisition. We translate this insight into ReasonMaxxer, a minimal RL-free method that applies contrastive loss only at entropy-gated decision points, using a few hundred base-model rollouts and no online generation. Across three model families, six scales, and six math reasoning benchmarks, ReasonMaxxer matches or exceeds full RL performance while requiring only tens of problems and minutes of single-GPU training, a reduction in training cost of roughly three orders of magnitude.

- **技术标签**: `benchmark` `large language model` `llm` `policy` `reasoning`


---


## 69. Contrastive Identification and Generation in the Limit

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06211v1)

- **摘要**: In the classical identification in the limit model of Gold [1967], a stream of positive examples is presented round by round, and the learner must eventually recover the target hypothesis. Recently, Kleinberg and Mullainathan [2024] introduced generation in the limit, where the learner instead must eventually output novel elements of the target's support. Both lines of work focus on positive-only or fully labeled data. Yet many natural supervision signals are inherently relational rather than singleton, which encode relationships between examples rather than labels of individual ones. We initiate the study of contrastive identification and generation in the limit, where the learner observes a contrastive presentation of data: a stream of unordered pairs $\{x,y\}$ satisfying $h(x)\ne h(y)$ for an unknown target binary hypothesis $h$, but which element is positive is hidden from the learner. We first present three results in the noiseless setting: an exact characterization of contrastive identifiable classes (a one-line geometric refinement of Angluin [1980]'s tell-tale condition), a combinatorial dimension called contrastive closure dimension (a contrasitive analogue of the closure dimension in Raman et al. [2025]) and exactly characterizing uniform contrastive generation with tight sample complexity, and a strict hierarchy in which contrastive generation and text identification are mutually incomparable. We then prove a sharp reversal under finite adversarial corruption: there exist classes identifiable from contrastive pairs under any finite corruption budget by a single budget-independent algorithm, yet not identifiable from positive examples under even one corrupted observation. The unifying technical object is the common crossing graph, which encodes pairwise ambiguity, family-level generation obstructions, and corruption defects in a single coverage-and-incidence language.

- **技术标签**: `adversarial` `rag` `vision`


---


## 70. When to Trust Imagination: Adaptive Action Execution for World Action Models

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.06222)

- **摘要**: World Action Models (WAMs) have recently emerged as a promising paradigm for robotic manipulation by jointly predicting future visual observations and future actions. However, current WAMs typically execute a fixed number of predicted actions after each model inference, leaving the robot blind to whether the imagined future remains consistent with the actual physical rollout. In this work, we formulate adaptive WAM execution as a future-reality verification problem: the robot should execute longer when the WAM-predicted future remains reliable, and replan earlier when reality deviates from imagination. To this end, we propose Future Forward Dynamics Causal Attention (FFDC), a lightweight verifier that jointly reasons over predicted future actions, predicted visual dynamics, real observations, and language instructions to estimate whether the remaining action rollout can still be trusted. FFDC enables adaptive action chunk sizes as an emergent consequence of prediction-observation consistency, preserving the efficiency of long-horizon execution while restoring responsiveness in contact-rich or difficult phases. We further introduce Mixture-of-Horizon Training to improve long-horizon trajectory coverage for adaptive execution. Experiments on the RoboTwin benchmark and in the real world demonstrate that our method achieves a strong robustness-efficiency trade-off: on RoboTwin, it reduces WAM forward passes by 69.10% and execution time by 34.02%, while improving success rate by 2.54% over the short-chunk baseline; in real-world experiments, it improves success rate by 35%.

- **技术标签**: `benchmark` `efficiency` `rag` `robustness`


---


## 71. Continuous-Time Distribution Matching for Few-Step Diffusion Distillation

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.06376)

- **摘要**: Step distillation has become a leading technique for accelerating diffusion models, among which Distribution Matching Distillation (DMD) and Consistency Distillation are two representative paradigms. While consistency methods enforce self-consistency along the full PF-ODE trajectory to steer it toward the clean data manifold, vanilla DMD relies on sparse supervision at a few predefined discrete timesteps. This restricted discrete-time formulation and mode-seeking nature of the reverse KL divergence tends to exhibit visual artifacts and over-smoothed outputs, often necessitating complex auxiliary modules -- such as GANs or reward models -- to restore visual fidelity. In this work, we introduce Continuous-Time Distribution Matching (CDM), migrating the DMD framework from discrete anchoring to continuous optimization for the first time. CDM achieves this through two continuous-time designs. First, we replace the fixed discrete schedule with a dynamic continuous schedule of random length, so that distribution matching is enforced at arbitrary points along sampling trajectories rather than only at a few fixed anchors. Second, we propose a continuous-time alignment objective that performs active off-trajectory matching on latents extrapolated via the student's velocity field, improving generalization and preserving fine visual details. Extensive experiments on different architectures, including SD3-Medium and Longcat-Image, demonstrate that CDM provides highly competitive visual fidelity for few-step image generation without relying on complex auxiliary objectives. Code is available at https://github.com/byliutao/cdm.

- **技术标签**: `alignment` `diffusion` `distillation` `vision`


---


## 72. A^2TGPO: Agentic Turn-Group Policy Optimization with Adaptive Turn-level Clipping

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.06200)

- **摘要**: Reinforcement learning for agentic large language models (LLMs) typically relies on a sparse, trajectory-level outcome reward, making it difficult to evaluate the contribution of individual tool-calls within multi-turn interactions. Existing approaches to such process credit assignment either depend on separate external process reward models that introduce additional consumption, or tree-based structural rollout that merely redistributes the outcome signal while constraining trajectory diversity. A promising alternative leverages the per-turn change in the policy's predicted probability of the ground-truth, termed Information Gain (IG), as an intrinsic process signal without an external evaluator. However, prior work on leveraging IG signals within the RL training loop faces three systematic challenges: normalizing across turns that face heterogeneous positional contexts can distort the relative standing of individual turns, accumulating a variable number of terms causes advantage magnitudes to drift with trajectory depth, and a fixed clipping range governs policy updates identically for turns with vastly different IG signals. In this paper, we propose A^2TGPO (Agentic Turn-Group Policy Optimization with Adaptive Turn-level Clipping), which retains IG as the intrinsic signal but re-designs how it is normalized, accumulated, and consumed: (i) turn-group normalization: normalizes IG within each (prompt, turn-index) group so that each turn is compared only against peers at the same interaction depth; (ii) variance-rescaled discounted accumulation: divides cumulative normalized IG by square root of accumulated terms to keep advantage magnitudes comparable across turn positions; and (iii) adaptive turn-level clipping: modulates each turn's clipping range based on its normalized IG, widening the update region for informative turns and narrowing it for uninformative ones.

- **技术标签**: `agent` `large language model` `llm` `policy` `rag`


---


## 73. Nonsense Helps: Prompt Space Perturbation Broadens Reasoning Exploration

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.05566)

- **摘要**: Reinforcement learning with verifiable rewards, particularly Group Relative Policy Optimization (GRPO), has significantly advanced the reasoning capabilities of Large Language Models (LLMs). However, in complex tasks, GRPO frequently suffers from the ``zero-advantage problem'': when all sampled rollouts for a query fail, the relative advantage collapses to zero. Consequently, the model loses effective training signals for these questions, wasting the training data and computational budget. While simply increasing the sampling budget for these questions is a common remedy, the static sampling policy inherently constrains reasoning exploration, limiting the success rate. In this paper, we propose Lorem Perturbation for Exploration (LoPE), a simple yet effective training framework to break this exploration bottleneck. We posit that task-irrelevant prompt-space perturbations can shift the model's output distribution enough to unlock orthogonal reasoning pathways for hard questions. Specifically, LoPE prepends sequences stochastically assembled from Lorem Ipsum vocabulary (a pseudo-Latin placeholder text) to the prompts before resampling. Experiments across 1.7B, 4B, and 7B models demonstrate that LoPE significantly outperforms resampling with the original prompts. Further analysis reveals that other Latin-based random sequences with low perplexity are also effective perturbations. Our results establish LoPE as a strong baseline for broadening exploration in LLM reinforcement learning.

- **技术标签**: `large language model` `llm` `policy` `reasoning`


---


## 74. Think, then Score: Decoupled Reasoning and Scoring for Video Reward Modeling

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.05922)

- **摘要**: Recent advances in generative video models are increasingly driven by post-training and test-time scaling, both of which critically depend on the quality of video reward models (RMs). An ideal reward model should predict accurate rewards that align with human preferences across diverse scenarios. However, existing paradigms face a fundamental dilemma: Discriminative RMs regress rewards directly on features extracted by multimodal large language models (MLLMs) without explicit reasoning, making them prone to shortcut learning and heavily reliant on massive data scaling for generalization. In contrast, Generative RMs with Chain-of-Thought (CoT) reasoning exhibit superior interpretability and generalization potential, as they leverage fine-grained semantic supervision to internalize the rationales behind human preferences. However, they suffer from inherent optimization bottlenecks due to the coupling of reasoning and scoring within a single autoregressive inference chain. To harness the generalization benefits of CoT reasoning while mitigating the training instability of coupled reasoning and scoring, we introduce DeScore, a training-efficient and generalizable video reward model. DeScore employs a decoupled ``think-then-score'' paradigm: an MLLM first generates an explicit CoT, followed by a dedicated discriminative scoring module consisting of a learnable query token and a regression head that predicts the final reward. DeScore is optimized via a two-stage framework: (1) a discriminative cold start incorporating a random mask mechanism to ensure robust scoring capabilities, and (2) a dual-objective reinforcement learning stage that independently refines CoT reasoning quality and calibrates the final reward, ensuring that higher-quality reasoning directly translates to superior model performance.

- **技术标签**: `chain-of-thought` `generative` `interpretability` `large language model` `llm`


---


## 75. Skill1: Unified Evolution of Skill-Augmented Agents via Reinforcement Learning

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.06130)

- **摘要**: A persistent skill library allows language model agents to reuse successful strategies across tasks. Maintaining such a library requires three coupled capabilities. The agent selects a relevant skill, utilizes it during execution, and distills new skills from experience. Existing methods optimize these capabilities in isolation or with separate reward sources, resulting in partial and conflicting evolution. We propose Skill1, a framework that trains a single policy to co-evolve skill selection, utilization, and distillation toward a shared task-outcome objective. The policy generates a query to search the skill library, re-ranks candidates to select one, solves the task conditioned on it, and distills a new skill from the trajectory. All learning derives from a single task-outcome signal. Its low-frequency trend credits selection and its high-frequency variation credits distillation. Experiments on ALFWorld and WebShop show that Skill1 outperforms prior skill-based and reinforcement learning baselines. Training dynamics confirm the co-evolution of the three capabilities, and ablations show that removing any credit signal degrades the evolution.

- **技术标签**: `agent` `distillation` `policy`


---


## 76. MARBLE: Multi-Aspect Reward Balance for Diffusion RL

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.06507)

- **摘要**: Reinforcement learning fine-tuning has become the dominant approach for aligning diffusion models with human preferences. However, assessing images is intrinsically a multi-dimensional task, and multiple evaluation criteria need to be optimized simultaneously. Existing practice deal with multiple rewards by training one specialist model per reward, optimizing a weighted-sum reward R(x)=sum_k w_k R_k(x), or sequentially fine-tuning with a hand-crafted stage schedule. These approaches either fail to produce a unified model that can be jointly trained on all rewards or necessitates heavy manually tuned sequential training. We find that the failure stems from using a naive weighted-sum reward aggregation. This approach suffers from a sample-level mismatch because most rollouts are specialist samples, highly informative for certain reward dimensions but irrelevant for others; consequently, weighted summation dilutes their supervision. To address this issue, we propose MARBLE (Multi-Aspect Reward BaLancE), a gradient-space optimization framework that maintains independent advantage estimators for each reward, computes per-reward policy gradients, and harmonizes them into a single update direction without manually-tuned reward weighting, by solving a Quadratic Programming problem. We further propose an amortized formulation that exploits the affine structure of the loss used in DiffusionNFT, to reduce the per-step cost from K+1 backward passes to near single-reward baseline cost, together with EMA smoothing on the balancing coefficients to stabilize updates against transient single-batch fluctuations. On SD3.5 Medium with five rewards, MARBLE improves all five reward dimensions simultaneously, turns the worst-aligned reward's gradient cosine from negative under weighted summation in 80% of mini-batches to consistently positive, and runs at 0.97X the training speed of baseline training.

- **技术标签**: `diffusion` `fine-tuning` `policy` `vision`


---


## 77. Inductive Venn-Abers and related regressors

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06646v1)

- **摘要**: Venn-Abers predictors are probabilistic predictors that enjoy appealing properties of validity, but their major limitation is that they are applicable only to the case of binary classification, with a recent extension to bounded regression. We generalize them to the case of unbounded regression, which requires adding an element of conformal prediction. In our simulation and empirical studies we investigate the predictive efficiency of point regressors derived from Venn-Abers regressors and argue that they somewhat improve the predictive efficiency of standard regressors for larger training sets.

- **技术标签**: `efficiency`


---


## 78. Edge-specific signal propagation on mature chromophore-region 3D mechanism graphs for fluorescent protein quantum-yield prediction

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06644v1)

- **摘要**: Fluorescent protein quantum yield (QY) is governed by the mature chromophore and its three-dimensional microenvironment rather than sequence identity alone. Protein language models and emission-band averages capture global trends, but do not model how local physical signals act on specific chromophore regions.   We present a chromophore-centred mechanism graph algorithm for QY prediction. Each PDB structure is converted into a typed 3D residue graph, registered to a mature-CRO state, partitioned into phenolate, bridge and imidazolinone regions, and transformed by channel-signal-region propagation. The representation contains 121 enrichment features; after removing identity shortcuts, 52 non-identity features are used for band-specific ExtraTrees regression. Because each feature encodes a contact channel, seed signal and target CRO region, interpretation is intrinsic rather than post hoc. On a 531-protein benchmark, the method achieved the best random-CV performance among model-based baselines (R = 0.772 +/- 0.008, MAE = 0.131 +/- 0.002), exceeding Band mean (R = 0.632), ESM-C (R = 0.734) and SaProt (R = 0.731), and ranked first in bright screening (Bright P@5 = 0.704). Under homology control, the advantage was clearest in the remote bucket (<50% similarity; R = 0.697 versus 0.633, 0.575 and 0.408), with the strongest overall bright/dark Top-K screening. Stable selected features recovered band-specific mechanisms: aromatic packing and clamp asymmetry in GFP-like proteins, charge/clamp balance in Red proteins, and flexibility-risk/bulky-contact features in Far-red proteins.   Source code, feature tables and evaluation scripts are available from the first author upon request. Contact: yuchenak05@gmail.com

- **技术标签**: `benchmark` `rag`


---


## 79. Crafting Reversible SFT Behaviors in Large Language Models

- **来源**: [arxiv_lg](https://arxiv.org/abs/2605.06632v1)

- **摘要**: Supervised fine-tuning (SFT) induces new behaviors in large language models, yet imposes no structural constraint on how these behaviors are distributed within the model. Existing behavior interpretation methods, such as circuit attribution approaches, identify sparse subnetworks correlated with SFT-induced behaviors post-hoc. However, such correlations do not imply *causal necessity*, limiting the ability to selectively control SFT-induced behaviors at inference time. We pursue an alternative by asking: can an SFT-induced behavior be deliberately compressed into a sparse, mechanistically necessary subnetwork, termed a *carrier*, while remaining controllable at inference time without weight modification? We propose (a) **Loss-Constrained Dual Descent (LCDD)**, which constructs such carriers by jointly optimizing routing masks and model weights under an explicit utility budget, and (b) **SFT-Eraser**, a soft prompt optimized via activation matching on extracted carrier channels, to reverse the SFT-induced behavior. Across safety, fixed-response, and style behaviors on multiple model families, LCDD yields sparse carriers that preserve target behaviors while enabling strong reversion when triggered by SFT-Eraser. Ablations further establish that the sparse structure is the key precondition for reversal: the same trigger optimization fails on standard SFT models, confirming that structure rather than trigger design is the operative factor. These results provide direct evidence that the learned carriers are causally necessary for the behaviors, pointing to a new direction for systematically localizing and selectively suppressing SFT-induced behaviors in deployed models.

- **技术标签**: `fine-tuning` `large language model`


---


## 80. EMO: Pretraining Mixture of Experts for Emergent Modularity

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06663v1)

- **摘要**: Large language models are typically deployed as monolithic systems, requiring the full model even when applications need only a narrow subset of capabilities, e.g., code, math, or domain-specific knowledge. Mixture-of-Experts (MoEs) seemingly offer a potential alternative by activating only a subset of experts per input, but in practice, restricting inference to a subset of experts for a given domain leads to severe performance degradation. This limits their practicality in memory-constrained settings, especially as models grow larger and sparser. We introduce EMO, an MoE designed for modularity-the independent use and composition of expert subsets-without requiring human-defined priors. Our key idea is to encourage tokens from similar domains to rely on similar experts. Since tokens within a document often share a domain, EMO restricts them to select experts from a shared pool, while allowing different documents to use different pools. This simple constraint enables coherent expert groupings to emerge during pretraining using document boundaries alone. We pretrain a 1B-active, 14B-total EMO on 1T tokens. As a full model, it matches standard MoE performance. Crucially, it enables selective expert use: retaining only 25% (12.5%) of experts incurs just a 1% (3%) absolute drop, whereas standard MoEs break under the same setting. We further find that expert subsets in EMO specialize at semantic levels (e.g., domains such as math or code), in contrast to the low-level syntactic specialization observed in standard MoEs. Altogether, our results demonstrate a path toward modular, memory-efficient deployment of large, sparse models and open new opportunities for composable architectures.

- **技术标签**: `large language model` `mixture of experts` `moe` `pretraining` `rag`


---


## 81. Parser agreement and disagreement in L2 Korean UD: Implications for human-in-the-loop annotation

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06625v1)

- **摘要**: We propose a simplified human-in-the-loop workflow for second language (L2) Korean morphosyntactic annotation by leveraging agreement between two domain-adapted parsers. We first evaluate whether parser agreement can serve as a proxy for annotation correctness by comparing it with independent human judgments. The results show strong correspondence between parser and human judgments, supporting the feasibility of semi-automatic L2-Korean UD annotation. Further analysis demonstrates that parser disagreements cluster in linguistically predictable domains such as grammatical-relation distinctions and clause-boundary ambiguity. While many disagreement cases are tractable for iterative model refinement, others reflect deeper representational challenges inherent in parsing and tagging L2-Korean corpora.

- **技术标签**: `rag`


---


## 82. Algospeak, Hiding in the Open: The Trade-off Between Legible Meaning and Detection Avoidance

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06619v1)

- **摘要**: As large language models (LLMs) increasingly mediate both content generation and moderation, linguistic evasion strategies known as Algospeak have intensified the coevolution between evaders and detectors. This research formalizes the underlying dynamics grounded in a joint action model: when Algospeak increases, detectability and understandability decrease. Further, the concept of Majority Understandable Modulation (MUM) is introduced and defined as the modulation level at which additional evasive alteration increases detector evasion but loses comprehension for the majority of recipients. To empirically probe this trade-off, we introduce a reproducible framework that can be used to create meaning-preserving, Algospeak-style variants, based on an existing taxonomy and with tunable modulation levels. Using COVID-19 disinformation as a first proof-by-example setting, we construct a reference dataset of 700 modulated items, drawn from twenty base sentences across five modulation levels and seven strategies. We then run two linked evaluations with seven different language models: one testing for interpretation through meaning recovery and one for disinformation detection through classification. Curve fitting over modulation levels yields an estimate of the Majority Understandable Modulation threshold and enables sensitivity analyses across strategies and models, see Figure 1. Results reveal the characteristic relationships between understandability and modulation. This study lays the groundwork for understanding the dynamics behind Algospeak and provides the framework, dataset, and experimental setups described.

- **技术标签**: `large language model` `llm` `research`


---


## 83. Automated Clinical Report Generation for Remote Cognitive Remediation: Comparing Knowledge-Engineered Templates and LLMs in Low-Resource Settings

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06594v1)

- **摘要**: The growing demand for cognitive remediation therapy, combined with limited speech therapist availability, has accelerated the adoption of remote rehabilitation tools. These systems generate large volumes of interaction data that are difficult for clinicians to review efficiently. This paper investigates automated clinical report generation for avatar-guided, home-based cognitive remediation sessions in a low-resource setting with no reference reports. We present and compare two approaches: (1) a rule-based template system encoding speech therapy domain knowledge as explicit decision rules and validated templates, ensuring clinical reliability and traceability; and (2) a zero-shot LLM-based approach (GPT-4) aimed at more fluent and concise output. Both systems use identical pre-extracted, expert-validated structured variables, enabling a controlled factual comparison. Outputs were evaluated by eight speech therapists and final-year students using a nine-criterion questionnaire. Results reveal a clear trade-off between clinical reliability and linguistic quality. The template-based system scored higher on fluidity, coherence, and results presentation, while GPT-4 produced more concise output. Directional differences are consistent across evaluation dimensions, though no comparison reached statistical significance after correction, reflecting the scale constraints of expert clinical evaluation. Based on evaluator feedback, we derive eight design recommendations for clinical reporting systems in remote rehabilitation settings. More broadly, this work contributes a replicable methodology combining expert elicitation, taxonomy-driven generation, and multi-dimensional human evaluation for clinical NLG in low-resource settings, and illustrates how controlled comparisons can inform the responsible adoption of generative AI in healthcare.

- **技术标签**: `generative` `gpt` `gpt-4` `llm`


---


## 84. Long Context Pre-Training with Lighthouse Attention

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06554v1)

- **摘要**: Training causal transformers at extreme sequence lengths is bottlenecked by the quadratic time and memory of scaled dot-product attention (SDPA). In this work, we propose Lighthouse Attention, a training-only symmetrical selection-based hierarchical attention algorithm that wraps around ordinary SDPA and can be easily removed towards the end of the training. Our hierarchical selection is also gradient-free, which exempts us from dealing with a complicated and potentially inefficient backward pass kernel. Our contribution is three-fold: (i) A subquadratic hierarchical pre- and post-processing step that does adaptive compression and decompression of the sequence. (ii) A symmetrical compression strategy that pools queries, keys and values at the same time, while preserving left-to-right causality, which greatly improves parallelism. (iii) A two stage training approach which we pre-train for the majority of the time with Lighthouse Attention and recover a full attention model at the end with a short training. We run preliminary small scale LLM pre-training experiments that show the effectiveness of our method compared to full attention training with all other settings matched, where we achieve a faster total training time and lower final loss after the recovery phase. Full code is available at: https://github.com/ighoshsubho/lighthouse-attention

- **技术标签**: `llm` `transformer`


---


## 85. Efficient Pre-Training with Token Superposition

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06546v1)

- **摘要**: Pre-training of Large Language Models is often prohibitively expensive and inefficient at scale, requiring complex and invasive modifications in order to achieve high data throughput. In this work, we present Token-Superposition Training (TST), a simple drop-in method that significantly improves the data throughput per FLOPs during pre-training without modifying the parallelism, optimizer, tokenizer, data, or model architecture. TST is done in two phases: (i) A highly efficient superposition phase where we combine many contiguous tokens into one bag and train using a multi-hot cross-entropy (MCE) objective, and (ii) a recovery phase where we revert back to standard training. We extensively evaluate TST on the scale of 270M and 600M parameters and validate on 3B and a 10B A1B mixture of experts model, demonstrating that it is highly robust in different settings. Ultimately, TST consistently outperforms baseline loss and downstream evaluations, and under equal-loss settings, TST yields up to a 2.5x reduction in total pre-training time at the 10B A1B scale.

- **技术标签**: `large language model` `mixture of experts`


---


## 86. The Frequency Confound in Language-Model Surprisal and Metaphor Novelty

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06506v1)

- **摘要**: Language-model (LM) surprisal is widely used as a proxy for contextual predictability and has been reported to correlate with metaphor novelty judgments. However, surprisal is tightly intertwined with lexical frequency. We explore this interaction on metaphor novelty ratings using two different word frequency measures. We analyse surprisal estimates from eight Pythia model sizes and 154 training checkpoints. Across settings, word frequency is a stronger predictor of metaphor novelty than surprisal. Across training stages, the surprisal--novelty association peaks at an early stage and then falls again, mirroring a similarly timed increase in the surprisal--frequency association. These results suggest that the often-reported optimal LM surprisal settings may incorrectly associate contextual predictability with metaphor novelty and processing difficulty, whereas lexical frequency may be the major underlying factor.


---


## 87. Cubit: Token Mixer with Kernel Ridge Regression

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06501v1)

- **摘要**: Since its introduction in 2017, the Transformer has become one of the most widely adopted architectures in modern deep learning. Despite extensive efforts to improve positional encoding, attention mechanisms, and feed-forward networks, the core token-mixing mechanism in Transformers remains attention. In this work, we show that the attention module in Transformers can be interpreted as performing Nadaraya-Watson regression, where it computes similarities between tokens and aggregates the corresponding values accordingly. Motivated by this perspective, we propose Cubit, a potential next-generation architecture that leverages Kernel Ridge Regression (KRR), while the vanilla Transformer relies on Nadaraya-Watson regression. Specifically, Cubit modifies the classical attention computation by incorporating the closed-form solution of KRR, combining value aggregation through kernel similarities with normalization via the inverse of the kernel matrix. To improve the training stability, we further propose the Limited-Range Rescale (LRR), which rescales the value layer within a controlled range. We argue that Cubit, as a KRR-based architecture, provides a stronger mathematical foundation than the vanilla Transformer, whose attention mechanism corresponds to Nadaraya-Watson regression. We validate this claim through comprehensive experiments. The experimental results suggest that Cubit may exhibit stronger long-sequence modeling capability. In particular, its performance gain over the Transformer appears to increase as the training sequence length grows.

- **技术标签**: `rag` `transformer`


---


## 88. Towards Emotion Consistency Analysis of Large Language Models in Emotional Conversational Contexts

- **来源**: [arxiv_cl](https://arxiv.org/abs/2605.06476v1)

- **摘要**: In this work, we conduct an analysis to examine the consistency of Large Language Models (LLMs) with respect to their own generated responses in an emotionally-driven conversational context. Specifically, the text generated by LLM is framed as a query to the same model, and its responses are subsequently assessed. This is performed with three queries across two dimensions of extreme and moderate emotions. The three queries are, in particular, false claim queries that contain inherently wrong assumptions (false presuppositions) in increasing order of intensity. Two commercial models, Claude-3.5-haiku, GPT4o-mini, and a medium-sized model, Mistral-7B, are considered in the study. Our findings indicate that LLMs exhibit below-average performance and remain vulnerable to false beliefs embedded within queries. This susceptibility is especially pronounced for moderate emotional content. Furthermore, an extended attention-score-based analysis highlights a shift in models' priority from evaluative to generative. The results raise important considerations for LLMs' deployment in high-stakes, emotionally sensitive contexts.

- **技术标签**: `claude` `generative` `gpt` `large language model` `llm`


---


## 89. GeoStack: A Framework for Quasi-Abelian Knowledge Composition in VLMs

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.06477)

- **摘要**: We address the challenge of knowledge composition in Vision-Language Models (VLMs), where accumulating expertise across multiple domains or tasks typically leads to catastrophic forgetting. We introduce GeoStack (Geometric Stacking), a modular framework that allows independently trained domain experts to be composed into a unified model. By imposing geometric and structural constraints on the adapter manifold, GeoStack ensures the foundational knowledge of the base model is preserved. Furthermore, we mathematically demonstrate a weight-folding property that achieves constant-time inference complexity (O(1)), regardless of the number of integrated experts. Experimental results across multi-domain adaptation and class-incremental learning show that GeoStack provides an efficient mechanism for long-term knowledge composition while significantly mitigating catastrophic forgetting. Code is available at https://github.com/QuantitativeImagingLaboratory/GeoStack.

- **技术标签**: `vision`


---


## 90. BioTool: A Comprehensive Tool-Calling Dataset for Enhancing Biomedical Capabilities of Large Language Models

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.05758)

- **摘要**: Despite the success of large language models (LLMs) on general-purpose tasks, their performance in highly specialized domains such as biomedicine remains unsatisfactory. A key limitation is the inability of LLMs to effectively leverage biomedical tools, which clinical experts and biomedical researchers rely on extensively in daily workflows. While recent general-domain tool-calling datasets have substantially improved the capabilities of LLM agents, existing efforts in the biomedical domain largely rely on in-context learning and restrict models to a small set of tools. To address this gap, we introduce BioTool, a comprehensive biomedical tool-calling dataset designed for fine-tuning LLMs. BioTool comprises 34 frequently used tools collected from the NCBI, Ensembl, and UniProt databases, along with 7,040 high-quality, human-verified query-API call pairs spanning variation, genomics, proteomics, evolution, and general biology. Fine-tuning a 4-billion-parameter LLM on BioTool yields substantial improvements in biomedical tool-calling performance, outperforming cutting-edge commercial LLMs such as GPT-5.1. Furthermore, human expert evaluations demonstrate that integrating a BioTool-fine-tuned tool caller significantly improves downstream answer quality compared to the same LLM without tool usage, highlighting the effectiveness of BioTool in enhancing the biomedical capabilities of LLMs. The full dataset and evaluation code are available at https://github.com/gxx27/BioTool

- **技术标签**: `agent` `fine-tuning` `gpt` `in-context learning` `large language model`


---


## 91. SwiftI2V: Efficient High-Resolution Image-to-Video Generation via Conditional Segment-wise Generation

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.06356)

- **摘要**: High-resolution image-to-video (I2V) generation aims to synthesize realistic temporal dynamics while preserving fine-grained appearance details of the input image. At 2K resolution, it becomes extremely challenging, and existing solutions suffer from various weaknesses: 1) end-to-end models are often prohibitively expensive in memory and latency; 2) cascading low-resolution generation with a generic video super-resolution tends to hallucinate details and drift from input-specific local structures, since the super-resolution stage is not explicitly conditioned on the input image. To this end, we propose SwiftI2V, an efficient framework tailored for high-resolution I2V. Following the widely used two-stage design, it addresses the efficiency--fidelity dilemma by first generating a low-resolution motion reference to reduce token costs and ease the modeling burden, then performing a strongly image-conditioned 2K synthesis guided by the motion to recover input-faithful details with controlled overhead. Specifically, to make generation more scalable, SwiftI2V introduces Conditional Segment-wise Generation (CSG) to synthesize videos segment-by-segment with a bounded per-step token budget, and adopts bidirectional contextual interaction within each segment to improve cross-segment coherence and input fidelity. On VBench-I2V at 2K resolution, SwiftI2V achieves performance comparable to end-to-end baselines while reducing total GPU-time by 202x. Particularly, it enables practical 2K I2V generation on a single datacenter GPU (e.g., H800) or consumer GPU (e.g., RTX 4090).

- **技术标签**: `efficiency`


---


## 92. Auto Research with Specialist Agents Develops Effective and Non-Trivial Training Recipes

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.05724)

- **摘要**: We study auto research as a closed empirical loop driven by external measurement. Each submitted trial carries a hypothesis, an executable code edit, an evaluator-owned outcome, and feedback that shapes the next proposal. The output is not a generated paper or a single model checkpoint, but an auditable trajectory of proposals, code diffs, experiments, scores, and failure labels. We instantiate this loop with specialist agents that partition recipe surfaces and share measured lineage across trials. The central empirical finding is that lineage feedback lets agents turn evaluator outcomes, including crashes, budget overruns, size failures, and accuracy-gate misses, into later program-level recipe edits rather than one-shot suggestions. Across 1,197 headline-run trials plus 600 Parameter Golf control trials after one-time setup and launch, humans did not choose proposals, edit recipes, override scores, or repair failed trials during the search. In the three headline runs, the same submitted-trial loop reduces Parameter Golf validation bpb by 0.81%, raises NanoChat-D12 CORE by 38.7%, and reduces CIFAR-10 Airbench96 wallclock by 4.59%, with each task measured by its own external evaluator and legality checks. The trace includes a strict architecture-domain audit of 157 headline-run submissions and program rewrites such as a NanoChat attention-kernel path change. Within this scope the loop autonomously writes code, submits experiments, absorbs feedback, applies and combines known techniques inside each environment, and improves public starting recipes.

- **技术标签**: `agent` `research`


---


## 93. The Granularity Axis: A Micro-to-Macro Latent Direction for Social Roles in Language Models

- **来源**: [huggingface_papers](https://arxiv.org/abs/2605.06196)

- **摘要**: Large language models (LLMs) are routinely prompted to take on social roles ranging from individuals to institutions, yet it remains unclear whether their internal representations encode the granularity of such roles, from micro-level individual experience to macro-level organizational, institutional, or national reasoning. We show that they do. We define a contrast-based Granularity Axis as the difference between mean macro- and micro-role hidden states. In Qwen3-8B, this axis aligns with the principal axis (PC1) of the role representation space at cosine 0.972 and accounts for 52.6% of its variance, indicating that granularity is the dominant geometric axis organizing prompted social roles. We construct 75 social roles across five granularity levels and collect 91,200 role-conditioned responses over shared questions and prompt variants, then extract role-level hidden states and project them onto the axis. Role projections increase monotonically across all five levels, remain stable across layers, prompt variants, endpoint definitions, held-out splits, and score-filtered subsets, and transfer to Llama-3.1-8B-Instruct. The axis is also causally relevant: activation steering along it shifts response granularity in the predicted direction, with Llama moving from 2.00 to 3.17 on a five-point macro scale under positive steering on prompts that admit local responses. The two models differ in controllability, suggesting that steering depends on each model's default operating regime. Overall, our findings suggest that social role granularity is not merely a stylistic surface feature, but a structured, ordered, and causally manipulable latent direction in role-conditioned language model behavior.

- **技术标签**: `large language model` `llm` `qwen` `reasoning`


---


## 94. Musk v. Altman week 2: OpenAI fires back, and Shivon Zilis reveals that Musk tried to poach Sam Altman

- **来源**: [mit_tech_review](https://www.technologyreview.com/2026/05/08/1137008/musk-v-altman-week-2-openai-fires-back-and-shivon-zilis-reveals-that-musk-tried-to-poach-sam-altman/)

- **摘要**: In the second week of the landmark trial between Elon Musk and OpenAI, Musk’s motivations for bringing the suit were under scrutiny. Last week, Musk took the stand, alleging that OpenAI CEO Sam Altman and president Greg Brockman had deceived him into donating $38 million to the company. He claimed that they’d promised to maintain&#8230;

- **技术标签**: `openai`


---


## 95. Here’s what you need to know about the cruise ship hantavirus outbreak

- **来源**: [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136988/heres-what-you-need-to-know-about-the-cruise-ship-hantavirus-outbreak/)

- **摘要**: MIT Technology Review Explains: Let our writers untangle the complex, messy world of technology to help you understand what’s coming next. You can read more from the series here. Eight passengers aboard a Dutch-flagged cruise ship have contracted a type of hantavirus, a rare virus transmitted by rats. Three of them have died. As the ship&#8230;


---


## 96. All the latest updates on AI data centers

- **来源**: [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/902546/data-centers-ai-energy-power-grids-controversy)

- **摘要**: Massive new data centers are the physical foundation for tech companies’ hopes and dreams for AI. But the rush to expand warehouses full of energy-hungry servers has also kicked up fights across the world over their impact on power grids, utility bills, nearby communities, and the environment.&#160; From audacious plans to launch data centers into [&#8230;]


---


## 97. PlayStation sees AI as a ‘powerful tool’ to help make games

- **来源**: [theverge_ai](https://www.theverge.com/games/926914/sony-playstation-ai-powerful-tool-games)

- **摘要**: As part of an earnings presentation on Friday, Sony shared how it's thinking about AI at the company, including many details about how it's evaluating AI as part of making PlayStation games. Generative AI has recently been showing up in bigger games - though many indie developers still reject it - and while Sony calls [&#8230;]

- **技术标签**: `generative`


---


## 98. Cloudflare says AI made 1,100 jobs obsolete, even as revenue hit a record high

- **来源**: [techcrunch_ai](https://techcrunch.com/2026/05/08/cloudflare-says-ai-made-1100-jobs-obsolete-even-as-revenue-hit-a-record-high/)

- **摘要**: Cloudflare announced its first large-scale layoff. CEO Matthew Prince says because of AI efficiency gains, the company doesn't need as many support roles.

- **技术标签**: `efficiency` `enterprise`


---


## 99. Microsoft was worried OpenAI would run off to Amazon and ‘shit-talk’ Azure

- **来源**: [theverge_ai](https://www.theverge.com/report/926771/microsoft-openai-amazon-worries-shit-talk-azure)

- **摘要**: When OpenAI was busy experimenting with AI-powered gaming bots, Microsoft CEO Satya Nadella and OpenAI CEO Sam Altman were in the early days of forming an AI partnership. Court documents from the ongoing Musk v. Altman trial have provided a rare look at the communications between Microsoft's top executives about investing in OpenAI and fears [&#8230;]

- **技术标签**: `openai`


---


## 100. Everybody wants to rule the AI world

- **来源**: [theverge_ai](https://www.theverge.com/podcast/926707/openai-ceo-murati-musk-trial-vergecast)

- **摘要**: Sometimes, companies pick CEOs based on carefully laid succession plans designed to maximize investor confidence and future performance. Other times, apparently, companies pick CEOs based on a bunch of video calls while the current CEO is texting the former CEO about who the new CEO even is. Such was the story of The Blip, the [&#8230;]

- **技术标签**: `openai`


---


## 101. The “people’s airline” and the enterprise AI gold rush

- **来源**: [techcrunch_ai](https://techcrunch.com/podcast/the-peoples-airline-and-the-enterprise-ai-gold-rush/)

- **摘要**: Everyone wants a piece of the&#160;enterprise&#160;AI pie, and this week, we saw a string of companies making their moves. From&#160;Anthropic and OpenAI announcing new joint ventures&#160;targeting enterprise AI deployment to&#160;SAP dropping $1B&#160;on German AI startup Prior Labs,&#160;it&#8217;s&#160;becoming clear that if&#160;you&#8217;re&#160;a startup building enterprise tools,&#160;you&#8217;re&#160;likely an&#160;acquisition target.&#160; On this episode of TechCrunch&#8217;s&#160;Equity&#160;podcast, hosts Kirsten Korosec, Anthony [&#8230;]

- **技术标签**: `anthropic` `enterprise` `openai` `xai`


---


## 102. Last 24 hours to get 50% off a second pass to TechCrunch Disrupt 2026

- **来源**: [techcrunch_ai](https://techcrunch.com/2026/05/08/last-24-hours-to-get-50-off-a-second-pass-to-techcrunch-disrupt-2026/)

- **摘要**: Last day to buy one pass and get a second one at 50% off to TechCrunch Disrupt 2026. Bring a partner, co-founder, or colleague at half off. Register now.


---


## 103. The Download: AI malaise and babymaking tech

- **来源**: [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136985/the-download-ai-malaise-babymaking-ivf-tech/)

- **摘要**: This is today&#8217;s edition of The Download, our weekday newsletter that provides a daily dose of what&#8217;s going on in the world of technology. We’ve entered the era of AI malaise AI is spreading everywhere, and it is not going away. But what will it do? What effect will it have on our society? Will&#8230;


---


## 104. Nanoleaf bets its future on robots, red light therapy, and AI

- **来源**: [theverge_ai](https://www.theverge.com/tech/926342/nanoleaf-smart-lighting-ai-robotics-red-light-wellness)

- **摘要**: Smart lighting company Nanoleaf has been unusually quiet recently. While competitors such as Govee and Philips Hue have been pumping out new products and innovative features at an impressive pace, Nanoleaf has launched just a handful of smart lighting products in the last two years. There's a reason for this lull - the company has [&#8230;]


---


## 105. Running Codex safely at OpenAI

- **来源**: [openai](https://openai.com/index/running-codex-safely)

- **摘要**: How OpenAI runs Codex securely with sandboxing, approvals, network policies, and agent-native telemetry to support safe and compliant coding agent adoption.

- **技术标签**: `agent` `codex` `openai`


---


## 106. Here’s how technology transformed babymaking

- **来源**: [mit_tech_review](https://www.technologyreview.com/2026/05/08/1136974/heres-how-technology-transformed-babymaking-ivf/)

- **摘要**: Technology is changing the way we make babies. The pioneering work of the scientists who invented IVF led to the birth of the first “test tube baby” in 1978. We’ve come a long, long way since then. This week, I’ve been working on a piece about the cutting edge of IVF technologies and what’s coming&#8230;


---


## 107. The fax machine is the bottleneck in US healthcare, and VCs are starting to notice

- **来源**: [techcrunch_ai](https://techcrunch.com/2026/05/07/the-back-office-problem-that-explains-why-specialists-never-call-you-back/)

- **摘要**: Like many AI companies automating work that humans currently do, Basata will eventually face a harder question about where the line is between augmenting workers and displacing them. For now, the founders say the administrative staff they work with aren't worried about that; they're more worried about drowning.


---


## 108. Laid-off Oracle workers tried to negotiate better severance. Oracle said no.

- **来源**: [techcrunch_ai](https://techcrunch.com/2026/05/08/laid-off-oracle-workers-tried-to-negotiate-better-severance-oracle-said-no/)

- **摘要**: Some found out they didn't qualify for WARN Act protections like two-months notice because the company had classified them as remote workers.

- **技术标签**: `enterprise`


---


## 109. Intel’s comeback story is even wilder than it seems

- **来源**: [techcrunch_ai](https://techcrunch.com/2026/05/08/intels-comeback-story-is-even-wilder-than-it-seems/)

- **摘要**: Intel's stock has risen a stunning 490% over the past year, a bet by Wall Street that may be running well ahead of the company's actual turnaround.

- **技术标签**: `enterprise`


---


## 110. See what happens when creative legends use AI to make ads for small businesses.

- **来源**: [google_ai](https://blog.google/company-news/inside-google/company-announcements/the-small-brief/)

- **摘要**: black and white card with headshots of susan credle, jayonta jenkins and tiffany rolfe


---


## 111. Continuum-AI-Corp/OrcaRouter-Lite

- **来源**: [github](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

- **摘要**: Self-hosted LLM router with a managed safety net. OpenAI-compatible. BYOK. Single-workspace. Streaming. For more advanced routing choose hosted OrcaRouter

- **技术标签**: `llm` `openai`


---


## 112. cenconq25/claude-code-app-studio

- **来源**: [github](https://github.com/cenconq25/claude-code-app-studio)

- **摘要**: A coordinated team of 53 Claude Code subagents that build, ship, and operate mobile apps end to end. Each agent owns a narrow slice of the lifecycle so that responsibility, expertise, and review checkpoints stay separated and observable.

- **技术标签**: `agent` `claude`


---


## 113. Negai-ai/AgentClaw

- **来源**: [github](https://github.com/Negai-ai/AgentClaw)

- **摘要**: AgentClaw turns one-sentence ideas into reusable Claw capabilities. Build less boilerplate with declarative workflows, computer browser code file control, MCP, Skills, memory, knowledge bases, tracing, scheduling, and API/MCP publishing.

- **技术标签**: `agent`


---


## 114. kruschdev/krusch-context-mcp

- **来源**: [github](https://github.com/kruschdev/krusch-context-mcp)

- **摘要**: A unified Zero-Trust MCP server that gives IDE agents local semantic codebase search, isolated episodic project memory, and hallucination-free framework RAG.

- **技术标签**: `agent` `rag`


---


## 115. shawn0728/OpenSearch-VL

- **来源**: [github](https://github.com/shawn0728/OpenSearch-VL)

- **摘要**: 🔍 OpenSearch-VL provides a fully open recipe for training strong multimodal deep search agents through high-quality data curation, diverse visual/search tools, and fatal-aware agentic reinforcement learning.

- **技术标签**: `agent` `multimodal`


---


## 116. awizemann/harness

- **来源**: [github](https://github.com/awizemann/harness)

- **摘要**: AI-driven user testing for iOS Simulator, macOS apps, and web apps. Write a goal in plain language; an LLM agent drives the UI and reports friction. macOS 14+, Swift 6.

- **技术标签**: `agent` `llm`


---


## 117. bestpracticaI/kalshi-ai-trading-bot

- **来源**: [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)

- **摘要**: Kalshi prediction markets trading bot algorithmic automated trading TypeScript Node.js Kalshi REST API RSA signing OpenRouter LLM CLI npm quant fintech event contracts market making exchange API bot Kalshi SDK

- **技术标签**: `llm`


---


## 118. TheSashaDev/girl-agent

- **来源**: [github](https://github.com/TheSashaDev/girl-agent)

- **摘要**: ИИ-девушка с человеческим поведением: сон, настроение, расписание, память, стадии отношений и конфликты. Userbot mode через MTProto — реагирует, печатает, ставит реакции. Anti-AI промпт убирает ChatGPT-повадки. Не чат-бот — персонаж с состоянием.

- **技术标签**: `agent` `chatgpt` `gpt`


---


## 119. Ajai53200/DeepSeek-V4-Pro-App

- **来源**: [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)

- **摘要**: DeepSeek V4 Pro download MoE architecture 1.6T parameters 1M context window reasoning modes Think Max sparse attention coding agent agentic AI benchmarks API pricing open weights MIT license.

- **技术标签**: `agent` `benchmark` `deepseek` `moe` `reasoning`


---


## 120. NirDiamant/Agent_Memory_Techniques

- **来源**: [github](https://github.com/NirDiamant/Agent_Memory_Techniques)

- **摘要**: Agent memory for LLMs: 30 runnable Jupyter notebooks covering conversation buffers, vector stores, knowledge graphs, episodic and semantic memory, MemGPT, Mem0, Letta, Zep, Graphiti, LoCoMo benchmarks, and production patterns.

- **技术标签**: `agent` `benchmark` `gpt` `llm`


---


## 121. zarazhangrui/beautiful-html-templates

- **来源**: [github](https://github.com/zarazhangrui/beautiful-html-templates)

- **摘要**: A library of HTML slide templates designed so any coding agent can pick the right one and produce a beautiful deck on the user's behalf, automatically.

- **技术标签**: `agent`


---


## 122. tianji-qingtian/AI-Native

- **来源**: [github](https://github.com/tianji-qingtian/AI-Native)

- **摘要**: AI-Native 通用开发工作流方法论：4-Phase 框架 + 空项目/已有源码两种场景 + 反模式速查。让 Claude Code 等 AI agent 在共享契约下并行干活。

- **技术标签**: `agent` `claude`


---


## 123. alterhq/openpets

- **来源**: [github](https://github.com/alterhq/openpets)

- **摘要**: One shared macOS desktop pet for AI agents and apps, with MCP/CLI control and Codex Pets support. 

- **技术标签**: `agent` `codex`


---


## 124. byliutao/CDM

- **来源**: [github](https://github.com/byliutao/CDM)

- **摘要**: Continuous-Time Distribution Matching for Few-Step Diffusion Distillation👏

- **技术标签**: `diffusion` `distillation`


---


## 125. Austin1serb/agents-md

- **来源**: [github](https://github.com/Austin1serb/agents-md)

- **摘要**: AGENTS.md patterns for context engineering in coding agents: safer command output, token efficiency, validation, and prompt-injection resistance.

- **技术标签**: `agent` `efficiency`


---


## 126. Jason-Cyr/ai-shared-brain

- **来源**: [github](https://github.com/Jason-Cyr/ai-shared-brain)

- **摘要**: Give your AI agent persistent memory with markdown files. Starter kit from the video: My AI and I Share a Brain.

- **技术标签**: `agent`


---


## 127. usewhale/whale

- **来源**: [github](https://github.com/usewhale/whale)

- **摘要**: DeepSeek CLI / terminal coding agent with MCP, Skills, shell tools, and prefix-cache optimization.

- **技术标签**: `agent` `deepseek`


---


## 128. Autoloops/upskill

- **来源**: [github](https://github.com/Autoloops/upskill)

- **摘要**: CLI + skill for the Autoloops upskill registry. Search, inspect, report on, and publish agent skills from your shell.

- **技术标签**: `agent`


---


## 129. ZhongKuang/TAAC2026-CLI

- **来源**: [github](https://github.com/ZhongKuang/TAAC2026-CLI)

- **摘要**: Agent-friendly CLI for scraping, comparing, archiving, and safely submitting TAAC2026 / Taiji experiments.

- **技术标签**: `agent`


---


## 130. 0xhackerfren/ProcMon-MCP

- **来源**: [github](https://github.com/0xhackerfren/ProcMon-MCP)

- **摘要**: An MCP to expose process monitoring and ETW tracing functionally to AI agents to assist in security work 

- **技术标签**: `agent`


---


## 131. 打破科技数据壁垒！智会心研官宣：高级检索+AI深度分析，面向个人免费开放！

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414445.html)

- **摘要**: 智会心研面向个人用户免费开放高级检索与 AI 深度分析核心功能，涵盖专利 AI 检索、AI 伴读、图表分析及多智能体协作，助力研发与情报分析高效完成，降低技术创新门槛。


---


## 132. 梁文锋出资200亿！DeepSeek首轮创纪录融资500亿，V4.1定档6月

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414432.html)

- **摘要**: 如果最终落地，这会是中国大模型公司有史以来最大的一轮融资

- **技术标签**: `deepseek`


---


## 133. 持续领跑！商汤大装置稳居中国MaaS市场第一梯队

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414428.html)

- **摘要**: 位列第二


---


## 134. Redis之父下场，给DeepSeek V4单独造了一台推理引擎

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414316.html)

- **摘要**: Mac上就能本地跑deepseek

- **技术标签**: `deepseek`


---


## 135. Anthropic出手！AI的内心独白，曝光了

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414213.html)

- **摘要**: 原来Claude早就识破了人类的套路（doge）

- **技术标签**: `anthropic` `claude`


---


## 136. GPT-5级推理能力塞进语音模型，OpenAI把同传翻译成本砍穿地板价

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414194.html)

- **摘要**: OpenAI上新三款实时语音模型

- **技术标签**: `gpt` `openai`


---


## 137. 特斯拉百万年薪招数据标注员，朝九晚五，无需AI经验

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414156.html)

- **摘要**: 服务FSD和Optimus


---


## 138. 所有实验室都怕字节，所有人都在夸DeepSeek！美国研究员36小时中国AI行

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414141.html)

- **摘要**: 这跟中国的开源精神，显然是一脉相承的

- **技术标签**: `deepseek`


---


## 139. 第一批「AI原生」本科生，要毕业了

- **来源**: [qbitai](https://www.qbitai.com/2026/05/414125.html)

- **摘要**: 全部都是AI加持的超级个体


---


## 140. AI开始接管年轻人的「精神自留地」

- **来源**: [36kr](https://36kr.com/p/3801461350702855?f=rss)

- **摘要**: <h4><strong>撰文｜锅包柚</strong></h4>
  <h4><strong>封面来源｜Unsplash（AI辅助扩图）</strong></h4>
  <p>五一假期已经结束，但打工人的“节后综合症”并未消退。</p>
  <p>面对永远99+的工作群消息，和改不完的PPT，打工人蝈蝈在摸鱼时打开灵光APP里的一个小游戏——“老板被我fire了”。</p>
  <p>屏幕里跳出老板最爱的PUA话术：“你们要相信我的眼光”“现在的付出都是值得的”。她疯狂点击，<strong>伴随着金币掉落的音效，在赛博世界里体验了一把将老板痛扁、原地暴富的爽感。</strong></p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_4beccf512b3a412ba3adb932ce11356d@1215450627_img_gif?x-oss-process=image/quality,q_80" /></p>
  <p class="img-desc">“老板被我fire了”</p>
  <p>这个让蝈蝈短暂“活过来”的应用，不是什么专业团队做的。而是一个同样被工作折磨的网友@二旬老人，在灵光APP免费花30秒随手“搓”出来的。</p>
  <p><strong>这届年轻人，连发泄情绪都要精打细算。</strong>因为情绪价值，正在成为一门明码标价的生意——69元的“治愈系盲盒”，很可能抽中雷款；半小时50块的“树洞倾听服务”，大概率只会收到客服发来的“抱抱”表情包和敷衍的套话；298元的线上塔罗占卜，对方说不定会让你再花399元请一串转运水晶。</p>
  <p>网友@咸鱼大王说透了真相，“明明是免费的东西，却被莫名其妙‘标了价’，然后最终需要我们‘花代价’去买回来。”</p>
  <p>更何况，花钱买来的不一定是松弛，也可能是刺客。</p>
  <p><strong>于是，一部分年轻人决定跳出消费陷阱，既然向外索取又贵又敷衍，不如自己动手。</strong>他们转头拥抱AI，开始为自己、为他人，精准定制零成本的情绪解药。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_a8238ee87bfb4dbd8b48e6e60fe28c04@1215450627_oswg2430oswg430oswg430_img_000?x-oss-process=image/format,jpg/format,jpg/interlace,1" /></p>
  <h2><strong>活人社交太贵，不如找AI“发疯”</strong></h2>
  <p>现实世界的倾诉，往往伴随着隐形的社交成本。</p>
  <p>向朋友宣泄，害怕成为别人的情绪垃圾桶，在朋友圈表达，担心自己被同事截图，向长辈寻求慰藉，又大概率会收获一顿“年轻人就要吃点苦”的说教。</p>
  <p><strong>有人选择关掉社交开关，把情绪一股脑倒给AI。</strong></p>
  <p>面对充斥着“班味儿”的职场压迫，年轻人开始“赛博发疯”，有人用灵光APP做出了一款“SHIT APP”的小应用，把客户无理的修改意见、领导画的大饼、同事的甩锅全部打在屏幕上，然后伴随着一阵清脆的水流声，眼睁睁看着它们被冲进下水道。创作者说，这个应用的核心就是——“你不用立刻变好，先把眼前这坨冲掉。”</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_a0c14496af804d248054d6e413d9c01e@1215450627_img_gif?x-oss-process=image/quality,q_80" /></p>
  <p class="img-desc">“SHIT APP”</p>
  <p><strong>也有人熟练地运用提示词，为自己量身定制最契合当下心理状态的AI角色。</strong></p>
  <p>被甲方折磨到崩溃时，有人打造出一个“绝对护短、无条件跟你一起吐槽的毒舌闺蜜”；深夜EMO时，有人会打开设定为“温柔妈妈”的树洞；甚至“同事.skill”的开源项目在GitHub上爆火后，还有人制作了前任.skill——只需要提供前任的聊天记录、QQ消息、朋友圈截图和照片，再加上一些个人的主观描述，就能生成一个前任的AI分身，让AI模拟前任的语气说出那些熟悉的话……</p>
  <p>而在22岁的研一学生闫博强这里，他不想让AI提供千篇一律的“抱抱”。</p>
  <p>准备保研期间，长期学业压力让闫博强多次想放弃，甚至有些自暴自弃，“要不不走这条路了，我也去打工，或者去考研。”但他没办法和朋友或父母说，既不想传递负面情绪，怕他们担心，也很难和他们产生共鸣。</p>
  <p>于是，他在灵光上手搓了一款名为“心境岛”的闪应用，并特意定制了一个“抽象毒舌版”。无论怎么发疯，屏幕里那只高雅企鹅都不会温柔地抚慰你，而是直接回呛，当你说“好累啊，不想保研了”，它会说，“你确定不是自己太菜了？谁还没个想放弃的时候呢？只是别人藏起来，你太实在了。”</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_f9ca1c6ca3354cea8e602bbc14b176df@1215450627_oswg332264oswg1080oswg2159_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">“心境岛-毒舌版”</p>
  <p><strong>这种借着抽象外衣的当头棒喝，反而奇迹般地缓解了他一天的紧绷感。</strong></p>
  <p>在AI世界里发泄，不需要看任何人的脸色，也不用害怕得不到回应。年轻人终于找到一个可以随时崩溃、无须解释的地方，卸下社交包袱，完成情绪自救。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_9ea18b863b044adba8d4422635207d48@1215450627_oswg3054oswg430oswg430_img_000?x-oss-process=image/format,jpg/format,jpg/interlace,1" /></p>
  <h2><strong>在不确定的世界，让AI找份确定的依靠</strong></h2>
  <p>情绪发泄只能换来一次短暂的喘息。在充满不确定的环境里，年轻人还有许多无处安放的困惑，他们的内心极度渴望一种确定的“精神依靠”。</p>
  <p>以前，他们把这种依靠寄托在玄学里，买祈福手串，去寺庙上香，进行塔罗占卜，“电子木鱼”APP一度冲上APP下载总榜的第二名，5毛钱一个的“爱因斯坦的脑子”在淘宝上半年卖出7万单。</p>
  <p><strong>现在，年轻人又用AI给自己零成本定制“赛博神明”。</strong></p>
  <p>有人在灵光圈搓了个“拜关公”，不管是马上要绩效考核，还是去医院看体检报告，随时随地掏出手机虔诚地拜一拜，主打一个心诚则灵；也有人做了个“塔罗启示录”，当被工作折磨到头秃时，它会适时降下神谕：“目标已达成，现在可以休息了”；当对未来充满迷茫时，它又会告诉你“新机会正在走来”……</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_320541b5fd984118a03feda72499a072@1215450627_oswg212437oswg1080oswg2133_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">“拜关公”</p>
  <p><strong>这种零成本的玄学，成了年轻人离不开的心理安慰剂。</strong></p>
  <p><strong>但遇事不决的年轻人不是只会求助玄学，他们也会求助务实的硬核工具。</strong></p>
  <p>有网友因为一块肉和老公起了争执，把事情经过发给AI，让AI给自己主持公道；科技博主@蜗牛的科技笔记在发现当朋友吵架让他评理时，无论偏向哪方，都会被贴上“不客观”的标签，甚至可能得罪某一方时，用不到百字的提示词搓出了一个“错了吗？”打分站，把是非对错的裁判权让给AI。</p>
  <p>被“清官难断家务事”折磨到心力交瘁的网友@观星的岫玉，干脆在灵光上捏了一个“家务事判官”。原被告双方各自陈述委屈，但妙就妙在，这个判官“不判输赢，只判‘和好如初套餐’”。当男生因为做家务轮换和女友僵持不下时，“AI菩萨”还会私发一份悄悄话：“真建议你，别硬刚公平轮班这套话术了，把做家务转换成心疼她，她反而更容易接受。”@观星的岫玉说，这就是个赛博版的居委会大妈，<strong>但与现实中喜欢和稀泥的大妈不同，AI判官不判对错，只递台阶。</strong></p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_3e59de2d6c994501a250fa751495a2fc@1215450627_oswg137784oswg1080oswg2188_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">“家务事判官”</p>
  <p>还有@灵光小茴香做了专门哄女朋友的“男友免死金牌”，不仅分析女友脸型、推荐拍照角度，还附带一整套夸人话术，帮你完美避开女友的灵魂拷问。它还会强调一嘴，“如果拍不出好看照片，全是这个应用的问题”。</p>
  <p>作为两个孩子的妈妈，江苏南通的韩女士则想要把这种确定提供给更多女性。</p>
  <p>她观察到社交媒体上很多女性都会发帖咨询女性相关权益，极高的点赞量也暴露她们“不见得知道一些对自己权益有帮助的知识”，便用灵光手搓了一款名为“她的指南针”的闪应用，帮女性在嫁妆、彩礼、财产分配、职业生涯等各方面提供决策指南，同时内置了女性权益知识库和司法案例，用这种方式守护女性权益，“你的选择，定义了你是谁。”她说。</p>
  <p><strong>还有人开始用AI给自己外接“赛博大脑”，给充满变数的日常建立起秩序。</strong></p>
  <p>总感觉自己“脑雾”不断的@Jacky的AI成长日记，用灵光捏了个“我刚才要干嘛来着”，一步步找回刚刚遗失的记忆；每次出门都要在行李箱前纠结两小时的@kiki给自己做了“旅行带什么？”清单生成器，实现无脑打包。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_b6909e9ad8b449a8af97b3bfd28e5222@1215450627_img_gif?x-oss-process=image/quality,q_90" /></p>
  <p>除了生活琐事，年轻人还顺手“爆改”了学习方式。有人做“瓜词社”，一边吃瓜一边学英语；有人做“厨房小记”，把营养学变成家常便饭；也有人做“自然之谜”，像抽卡片一样学习自然常识……他们给这种方式起了个名字： “无痛长脑子”，<strong>用AI为自己锁定一份“有付出就有收获”的确定性回报。</strong></p>
  <p>这些看似微小又细碎的需求，正在构成一个庞大的宇宙。根据灵光App数据，在灵光圈，由普通人创作的这类闪应用已超过3000多万个。<strong>它们像一个个微小的“数字补丁”，精准地修复着现实生活中的每一个bug。</strong></p>
  <p>年轻人用AI消解着生活里的困惑与矛盾。在不确定中，他们亲手为自己立起了一个个可以稳稳依靠的坐标。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_8212fa3e087540dfb17ca12c5ae99ccc@1215450627_oswg3164oswg430oswg430_img_000?x-oss-process=image/format,jpg/format,jpg/interlace,1" /></p>
  <h2><strong>在平行宇宙里，用AI“重养自己”一遍</strong></h2>
  <p>除了聊天和做应用，AI生成内容（AIGC）也成了年轻人低成本构建精神世界的重要工具。</p>
  <p>心情低落时，有人用AI画一幅光怪陆离的超现实主义插画；感觉孤单时，有人让自家小猫在短视频里开口说话；对一成不变的生活感到厌倦时，有人自己写几句大纲，让AI直接生成一部符合自己口味的，充满治愈感或爽点的微短剧。</p>
  <p>但年轻人又不满足于此。<strong>他们开始将目光投向了更深层的心理痛点，用AI重塑自己的人生。</strong></p>
  <p>心理学家皮特·沃克曾在《不原谅也没关系》中提到，受创伤的孩子有许多发展需求未得到满足，而再抚育的主要目标是满足这些需求。有人在成年后给自己报五花八门的兴趣班，去补修那个兴趣缺失的童年，有人在经济自由后，整牙、做近视眼手术，满足小时候那些不被重视的需求。</p>
  <p><strong>还有一批年轻人，现实里当不了爽文主角，便用AI改写人生副本。</strong></p>
  <p>19岁的女孩洛伊，高中时在一座四线城市读书，巨大的升学压力让她时常在卧室崩溃大哭。她总幻想：自己要是生活在曼哈顿读高中的话，是不是就没有这种烦恼了？哪怕是在国际学校读书，会不会都自由很多？</p>
  <p>高中毕业后，这种在现实中求而不得的“优渥条件”，她决定用AI给自己造一个。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_fdc4f5e44f5543e4b22cf09ae0315236@1215450627_img_gif?x-oss-process=image/quality,q_80" /></p>
  <p class="img-desc">“富婆妈妈模拟器”</p>
  <p>花了十天时间，反复调试近两百次，洛伊手搓出了一款“富婆妈妈模拟器”。在这个完美世界里，她设定了一个拥有“钞能力”且极度开明的母亲，不仅能体验老钱阶层的自由生活，还能悉心培养一个宝宝。洛伊说，<strong>她其实把自己代入了那个被富养的宝宝，因为她想帮从前的自己，重新活一遍。</strong>在AI构建的庇护所里，体验着一种被绝对偏爱的人生。</p>
  <p>这种“模拟器宇宙”在灵光上批量出现，“至尊老天奶系统”，带你闯入虐文副本，强行逆转女主的悲惨命运，在文字的爽感里完成一场“她力量”的隔空投送；“地球Online”，让你把人生变成反复开副本的生存游戏；“霸道资源爱上我”把乙女游戏的套路搬进职场；“女明星的诞生”可以满足你那些藏在心底的身份幻想……</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_8103f7008a724cb1bdf68ac1895dc99f@1215450627_oswg159096oswg1080oswg2177_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">“女明星的诞生”</p>
  <p><strong>在这个平行世界里，年轻人补全缺失的拥抱，改写遗憾的结局，最终把那个更完整、更坚韧的自己，重新接回现实。</strong>他们用AI创造作品，创造世界，也创造一个新的自己。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_b91dc720fa64498ba971a751160dccf9@1215450627_oswg536oswg1080oswg142_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p>从发疯吐槽，到赛博求佛，再到平行宇宙里的重养自己，年轻人正在用AI完成情绪自救。</p>
  <p><strong>美国社会学家阿莉·霍克希尔德在著作《心灵的整饰：人类情感的商业化》中提出“情绪劳动”的概念——为了让组织、他人感到满意和舒适，调节自己的情绪和表情所付出的努力。</strong>在现实生活中，年轻人承担了大量的情绪劳动，对着领导无用且无趣的废话热烈鼓掌，对催婚催育的长辈保持微笑，哪怕工作压力再大，也要在朋友聚会上维持轻松愉快的氛围……</p>
  <p>年轻人的能量，逐渐耗尽。</p>
  <p>但AI不同。它不会评判，不会说教，你可以投喂给它最不可言说的崩溃，最不讲道理的情绪，最不切实际的幻想，它也只会为你一人生成回应。<strong>在它身上，年轻人能找回“我能掌控一切”的确定感。</strong></p>
  <p>与此同时，AI也打破了技术的壁垒。几句简单的自然语言提示词，就能在几分钟内创造出一个懂自己、能提供真实反馈的载体，四线城市的高中生能体验到老钱家族的底气，求助无门的困境女性能获得专业的法律导航，每一个普通人都能随时随地拥有一座精神避风港。</p>
  <p>与其说年轻人是不想为情绪价值买单，不如说他们是在夺回生活主动权。<strong>从花钱买安慰，到自己动手造解药，看起来像是消费降级，其实是情感需求的升级。</strong>他们知道自己需要什么样的安慰、什么样的陪伴、甚至什么样的爱。</p>
  <p>而最好的情绪价值，从来不是买来的，而是亲手造出来的。</p>


---


## 141. 需求持续升温，AI芯片制造商Cerebras拟上调IPO价格区间

- **来源**: [36kr](https://36kr.com/newsflashes/3801408298065416?f=rss)

- **摘要**: 据报道，随着投资者对人工智能芯片制造商Cerebras Systems股票的需求继续升温，该公司最早将于当地时间下周一上调IPO价格区间至每股125美元至135美元。知情人士称，这次IPO已吸引超20倍的认购订单。Cerebras提交给美国证监会的文件显示，该公司目前寻求筹集35亿美元，正以每股115美元至125美元的价格推介2800万股股票。（界面）


---


## 142. 新三板梯度培育体系完善，挂牌企业踊跃筹备北交所IPO

- **来源**: [36kr](https://36kr.com/newsflashes/3801400639462914?f=rss)

- **摘要**: 近期北交所新股表现亮眼，中科仪、振宏股份等多只个股上市首日大涨，“打新”热度持续攀升，投资者参与热情高涨。伴随北交所赚钱效应持续发酵，新三板市场吸引力也显著提升，优质企业挂牌节奏明显加快，新增挂牌企业数量与质量同步迈上新台阶。作为多层次资本市场的重要基石，新三板持续优化市场生态，企业成长动能充沛，进阶意愿明确，正为北交所持续输送优质后备力量。（证券时报）


---


## 143. 36氪首发 | 航空航天电气系统互联组件方案商获数千万融资，细分赛道市占率第一

- **来源**: [36kr](https://36kr.com/p/3801398177324550?f=rss)

- **摘要**: <p>作者&nbsp;|&nbsp;乔钰杰</p>
  <p>编辑&nbsp;|&nbsp;袁斯来</p>
  <p>硬氪获悉，青岛北辰航天航天科技有限公司（下称“北辰航天”）近日完成数千万元天使轮融资，由云启资本独家投资，翊荣资本担任长期独家财务顾问。</p>
  <p>北辰航天旗下全资子公司青岛北辰数智科技有限公司成立于2014年，长期深耕航空航天电气系统互联组件研制领域，提供从设计到组装的系统工程解决方案。</p>
  <p>电气系统互联是航天器的五大核心组成之一，类似于人体的“神经与血管”，承担电源分配、信号传输、测量控制等关键功能，具有高复杂度与高可靠性要求。随着商业航天、深空探测及低空飞行器的发展，仪器布局与电气系统互联（电缆网）敷设设计及配套电气系统互联组件产品正迎来新的需求增长。</p>
  <p>据了解，<strong>北辰航天早期即以体制内外协方身份参与航天领域电气系统互联系统设计，深度参与多项运载型号的三维设计工作，技术成熟度行业领先。</strong></p>
  <p>经过十余年积累，北辰航天已具备面向航空航天企业的全流程一站式服务能力，从设备构型布局、电气系统互联（电缆网）敷设设计设计，到生产加工与总装指导均可闭环完成，客户仅需提供需求与IDS接口数据。<strong>公司目前也是国内唯一能够提供“设计—生产—总装—交付”全链条服务的民营商业航天企业。</strong></p>
  <p>技术平台方面，北辰航天自研辰数EWIS电缆网设计与生产管理系统（CSED），可实现IDS数据与整星、整箭等航天器三维设计数据的有机结合，采用协调设计和唯一数据源的模式向生产环节的一键转化，打通设计与制造之间的数据链路，降低传统模式中的信息断层风险。该系统曾支持某卫星项目在1个月内完成全流程设计（含多轮方案迭代），具备更好适应商业航天“短周期、快迭代”需求的能力。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_8d6372e2f9a0498f83d8882f589dd5a4@5920579_oswg1826751oswg942oswg699_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">某型号产品 （图源/企业）</p>
  <p><strong>除商业航天外，北辰航天还服务低空及无人机客户。</strong>在低空与无人机领域，大型无人机（载重1吨以上）在适航认证过程中需提供完整的电气系统互联设计文件，传统现场接线方式难以满足一致性与可靠性要求。</p>
  <p>北辰航天提供的“交钥匙”式解决方案，从原理设计阶段即介入整机电气系统互联布局与图纸输出，通过电缆网预制与模块化安装提升总装效率，可进一步保障量产一致性并降低飞行风险，为客户获取适航认证提供保障。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260509/v2_a958032617ae408a8ee130db3ddf3576@5920579_oswg206609oswg1026oswg502_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">某飞机神经与血管网络 （图源/企业）</p>
  <p>目前，北辰航天已具备稳定的产品交付能力，营收连续多年保持增长，2025年营收达数千万元。</p>
  <p>此次融资完成后，北辰航天将进一步扩充产能，建设约2000平方米研发与生产场地，并完善相关设备配置。</p>
  <p><strong>以下为硬氪与北辰航天创始人满海锋访谈节选（略经编辑）：</strong></p>
  <p><strong>硬氪：相比火箭、卫星总体方自己组建团队，北辰航天能解决哪些他们自己解决不了的痛点？</strong></p>
  <p><strong>满海锋：</strong>首先是经验。我们从2012年开始专注电气系统互联设计，2014年公司成立，到现在已经十多年，接近十五年的积累。这种长期工程经验，是大多数商业航天公司短时间内很难补齐的。我们参与过上百个型号，尤其是大量国家重点型号的系统互联与构型布局设计。这带来的不仅是经验数量，更是对复杂系统的理解深度。比如我们做过很多吨级高轨卫星，而目前很多商业航天项目仍以数百公斤级为主，两者在复杂度上差异非常大。</p>
  <p>其次是专业化分工。我们长期只专注在电气系统互联与总体布局这一细分领域，有点像“专科医生”，对这个环节的优缺点、风险点都非常熟悉。</p>
  <p>此外，还有一个现实问题是人才。目前商业航天领域高水平工程人才紧缺，人才需要长期型号积累，很难通过短期招聘或培训解决。</p>
  <p>我们过去输出过大量设计图纸，同时也在业内专家支持下建立了生产体系，不仅能做设计，还能打通到制造与交付，这一整套能力不是短时间内可以搭建的。</p>
  <p><strong>硬氪：北辰航天的方案，具体是如何实现成本优化的？</strong></p>
  <p><strong>满海锋：</strong>可以理解为三个层面。第一是流程重构。我们把设计到生产这一整段链路打通，变成一个配套总体的系统互联分系统，由我们来主导执行。客户只需要提供需求和接口数据，我们完成设备布局、系统互联设计，再通过自研系统直接转入生产。这一模式下，一个卫星项目平均设计周期大约3个月，火箭约5个月，快的话甚至几周可以完成；相比传统模式，整体周期大概能压缩到原来的三分之一。时间就是成本。</p>
  <p>第二是规模化采购。单一型号的物料需求有限，议价能力较弱；但我们服务多个客户，可以进行批量采购，比如同规格电缆、专业的连接器等，从而在价格和交付周期上都更有优势。</p>
  <p>第三是测试与工装复用。传统模式下，每个型号都需要单独配置测试工装；而我们由于服务多个项目，可以做通用化设计，提升工装复用率，从而降低测试成本。</p>
  <p>另外，我们作为市场化公司，在组织和机制上更灵活，无论是价格体系还是响应效率，都更有弹性，这也是能够持续实现降本增效的一个重要原因。</p>
  <p><strong>硬氪：未来几年，北辰航天会通过哪些商业手段进一步降低成本？</strong></p>
  <p><strong>满海锋：</strong>我们现在讲的“交钥匙”，更多还是覆盖设计、生产、总装这些直接面向客户的环节。但在这背后，其实还有一整套上游体系——包括供应商网络、材料能力、制造能力——这些才是决定成本的关键。随着商业航天和低空产业的发展，我们也会扩展这些能力，逐步把整个链条做完整。最终目标是，在系统互联这一块，既能保证航天级质量，又能把价格做到更有竞争力。</p>
  <p><strong>投资人观点</strong></p>
  <p><strong>云启资本投资人表示：</strong>我们高度认可北辰数智创始人满海锋先生及核心团队，团队深耕航空航天电气互联领域十余年，具备深厚型号经验、极强工程化落地能力与长期主义定力，是赛道内稀缺的专业化领军团队。公司拥有扎实硬核的技术基因，自研国产化 CSED 电缆网设计生产系统，打通全链路数据闭环，构建起难以复制的技术壁垒。作为国内唯一提供 “设计-生产-总装-交付” 全链条交钥匙方案的民营厂商，公司已深度服务航天科技、商业航天等头部客户，业绩连续高增长，市占率领先。我们坚定看好公司依托技术、资质、客户与产能优势，充分受益商业航天与低空经济大趋势，持续领跑航空航天电气互联核心赛道。</p>


---


## 144. 获高秉强、蓝驰领投数千万融资，浙大00后创业者从远景观测切入AI智能影像｜硬氪首发

- **来源**: [36kr](https://36kr.com/p/3797202414820359?f=rss)

- **摘要**: <p>作者｜黄楠</p>
  <p>编辑｜袁斯来</p>
  <p>硬氪获悉，星识（宁波）科技有限公司（以下简称“星识科技”）近日连续完成天使+轮和天使++轮融资，累计金额达数千万元。两轮融资分别由高秉强教授旗下高锋耐心资本和蓝驰创投领投、松禾资本跟投，老股东清水湾二期基金及奇绩创坛持续加注。本轮资金将主要用于智能影像核心技术研发、新品矩阵打造和产品体验的迭代优化，以及生产体系与供应链能力建设。此前，公司已获得李泽湘教授旗下宁波智能技术研究院、清水湾二期基金及奇绩创坛的种子轮及天使轮投资。</p>
  <p>星识科技是一家专注智能影像技术研发与硬件制造的企业，以远景观测场景为切点，曾推出融合AI功能的Vizta智能望远镜，已在Kickstarter和Indiegogo众筹达数百万元。</p>
  <p>望远镜作为长期被传统光学巨头主导的市场，正在被新生代创业者以消费级的智能化产品重新撬动。星识科技巧妙地通过结构设计与AI算法创新，将手机变为智能望远镜，不仅低成本、高效地实现了远景观测和拍摄的一体性，还通过AI功能进一步降低了产品操作门槛、丰富了产品玩法和趣味性。这种软硬件融合的创新解决了全球数亿远景观测用户的需求。</p>
  <p>根据美国鱼类及野生动物管理局（USFWS）2024年11月发布的《Birding in the United States: A Demographic and Economic Analysis》报告，仅在美国，每年就有约9600万人参与过观鸟活动，其中户外观鸟者平均每人每年观鸟34天。随着户外运动浪潮席卷全球，拥有观鸟、观星等远景观测及拍摄需求的人群基数正在快速增长。</p>
  <p>“他们当中，许多并非是专业级的行业用户，更多是以远距离观测为兴趣、追求‘看得更远’体验的普通消费级人群。除了天文观测、动物摄影，还会把望远镜、长焦影像设备用在户外运动、演唱会追星和风景人像等场景里。”星识科技创始人兼CEO谢智鑫说。</p>
  <p>星识科技推出的首款产品Vizta智能望远镜，相比市场上多数产品显得有些“另类”。首先是硬件形态上的减法，不内置屏幕、电池和处理器，而是一个纯粹的，轻量化光学长焦镜头，与手机配合使用，兼容大部分市面在售的机型。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260506/v2_cddc25888c0d4d36bc510573ca6ac0d3@6022551_oswg4134389oswg2048oswg2048_img_png?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">能轻松放入口袋随行携带（图源/企业）</p>
  <p>产品的重量仅290克、约为半瓶矿泉水重量，能轻松放入口袋随行携带。用户无需学习复杂参数或后期处理，即可轻松拍摄出风格化、高质量的影像内容，解决了传统“长枪大炮”装备昂贵笨重、繁琐的痛点，搭载AI助手，构建全新摄影交互体验，让普通手机也能输出专业级的长焦影像。</p>
  <p>目前，Vizta智能望远镜已销往多个国家和地区，目标用户以消费级影像爱好者为主，覆盖观鸟、天文摄影、户外运动记录、演唱会与风景人像拍摄等多元场景，并延伸至学生及亲子家庭等入门人群。谢智鑫向硬氪透露，该款产品毛利空间可观，并实现正向现金流——这在早期消费硬件公司中并不多见。</p>
  <p>“我们选择先用一个小而美的单品跑通闭环，它既能帮我们拿到真实的用户反馈，又能产生现金流。自己造血才是第一位，融资是为了放大验证。”谢智鑫说。</p>
  <p>在首款产品积累大量用户数据并验证了远景影像市场的基础上，星识科技正在研发的新款独立影像设备产品，将重心从工具转向AI体验，把影像生产内容流程嵌入到用户的创作生态中去。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260506/v2_e3482d3b097c4502864270ea0ecdf68e@6022551_oswg9747385oswg4096oswg2187_img_png?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">Vizta智能望远镜（图源/企业）</p>
  <p>一边是专业设备增长放缓、难以破圈，另一边是大众用户从“拍得到”到“拍得好”、再到“拍得有意义”的需求持续膨胀。“要满足这种跃迁，设备需要具备理解环境和空间，并主动提供建议的能力。”谢智鑫表示，“不只是一个个技术指标的堆砌，而是对用户真实需求和行业长期痛点最直接的回应。”</p>
  <p>基于这一判断，星识科技选择了一条差异化的渐进式路径。不急于做“大而全”的一体机，而是先通过一个小而美的单品跑通从用户洞察、产品定义、量产交付到正向现金流的完整闭环，在这个过程中积累真实用户数据与场景理解，再逐步向更高阶的独立智能终端迭代。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260506/v2_b1d28285da2b42ea8b075e732827c826@6022551_oswg3885035oswg1792oswg2024_img_png?x-oss-process=image/quality,q_80/format,jpg/interlace,1" /></p>
  <p class="img-desc">Vizta智能望远镜（图源/企业）</p>
  <p>当前，长焦观测赛道正经历一场从专业工具向大众消费品的范式转移。传统光学巨头依靠品牌与渠道壁垒固守高端市场，而新兴创业公司则从形态、交互与AI能力等不同路径切入，致力于真正解决入门用户“上手即用、玩得起来”的核心诉求。</p>
  <p>从简化形态、降低门槛，到以AI交互、专业影像能力激活普通用户的创作与探索欲，行业正在跳出堆参数、堆专业度的内卷，转向真正贴近大众的“好带、好用、好玩”。这背后是用户从“拍得到”到“拍得好”、再到“拍得有意义”的跃迁，也正是星识科技希望在智能影像下一阶段抓住的机会。</p>


---


## 145. 美股三大指数集体收盘涨，英特尔涨超13%

- **来源**: [36kr](https://36kr.com/newsflashes/3801342492040709?f=rss)

- **摘要**: 36氪获悉，5月8日收盘，美股三大指数集体上涨，道指涨0.02%，标普500指数涨0.84%，纳指涨1.71%。大型科技股多数上涨，英特尔涨超13%，特斯拉涨超4%，苹果涨超2%，英伟达涨超1%，谷歌涨0.71%，亚马逊涨0.56%；微软、Meta跌超1%，奈飞跌0.86%。热门中概股多数下跌，新东方跌超4%，知乎跌超3%，拼多多跌超2%，网易跌超1%；理想汽车涨超2%，百度涨0.84%。


---


## 146. 9点1氪丨DeepSeek拟募资最高500亿；“全国销冠”被刑拘，泰康人寿回应；OPPO就母亲节文案致歉

- **来源**: [36kr](https://36kr.com/p/3801348046151428?f=rss)

- **摘要**: <p><strong>整理</strong>｜Kris&nbsp;</p>
  <h2><strong>今日热点导览</strong></h2>
  <p>香港拿下世界杯转播权，FIFA与央视谈判仍陷僵局</p>
  <p>油价上调，加满一箱92号汽油将多花12.5元</p>
  <p>钱江摩托否认“围剿张雪机车”</p>
  <p>30条中日航线4月取消全部航班</p>
  <p>SpaceX冲刺上市，资本开支飙升数百亿</p>
  <h2><strong>TOP3大新闻</strong></h2>
  <p><strong>DeepSeek拟募资最高500亿元</strong></p>
  <p>据报道，DeepSeek拟募资最高500亿元，这将成为中国人工智能公司有史以来最大的一轮融资。(财联社)</p>
  <p><strong>“全国销冠”任晓敏被刑拘，泰康人寿回应</strong></p>
  <p>5月7日，泰康人寿方面对记者表示，近日，泰康人寿青岛分公司个人代理人任某某被青岛市公安机关立案侦查，引发社会广泛关注。对此，公司高度重视，第一时间组织专项工作组派驻青岛，全力配合公安机关的工作，并同步启动对该事件的内部自查和客户排查，绝不姑息任何违法犯罪行为。</p>
  <p>此前有消息称，泰康人寿青岛分公司销售任晓敏利用其“销冠”光环，以“帮公司冲业绩”“套取营销费用”等名义向客户、同事等短期借款，承诺高额利息，并以滚动方式维持运作，后随资金链断裂而暴露。青岛市公安局市南分局已正式以涉嫌诈骗罪对任晓敏立案，涉案本金规模约3亿至4亿元，受害人中既有身家不菲的高净值客户，也有她的内部同事。至于这笔巨额资金的最终完整去向，以及任晓敏的作案动机，目前除部分款项流向一名王姓债权人外，其余环节仍有待警方进一步查明。（第一财经、红星新闻、财新）</p>
  <p><strong>OPPO就母亲节宣传文案致歉</strong></p>
  <p>5月8日，OPPO发文就母亲节宣传文案致歉，“我们的创作初衷，是希望打破刻板印象，呈现更多元、更立体的当代母亲形象：母亲可以热爱马拉松，可以沉浸文字创作，也可以拥有自己的追星爱好。我们已第一时间下架全部相关物料。我们将认真倾听各方批评，全面审查内容审核机制，确保此类问题不再发生。”</p>
  <p>据此前报道，5月8日，OPPO发布的母亲节活动文案引发网友争议。其争议文案内容为：我妈有两个“老公”，一个是我爸，另一个一年见两回。跟我爸约会基本不打扮，见另一个，她恨不得穿婚纱。有网友认为，该文案价值观不正确；也有网友表示，文案内容只是“玩梗”。（界面新闻、中国新闻网）</p>
  <h2><strong>大公司/大事件</strong></h2>
  <p><strong>微信未读语音消息由红变灰，腾讯客服回应</strong></p>
  <p>近日，多位网友在社交平台发帖称，更新微信版本后，未读的语音消息显示为灰色而非红色。5月8日，界面新闻就此咨询腾讯客服，对方表示，iOS客户端正在灰度上线“快速浏览未读聊天”功能，首次上线时该功能会先展示为灰色。如果有用户当前未获得灰度名额，建议耐心等待后续功能更新。该功能支持快速查看所有未读聊天。（界面新闻）</p>
  <p><strong>香港拿下世界杯转播权，FIFA与央视谈判仍陷僵局</strong></p>
  <p>近日，FIFA官网显示，中国香港地区已获得2026年世界杯转播权。据悉，香港电讯盈科公司旗下Now TV与免费电视台Viu TV获得美加墨世界杯独家转播权。Now TV将通过收费平台全程直播104场比赛，Viu TV将会免费播出揭幕战、决赛等精选场次。据悉，电讯盈科买下世界杯转播权花费约2500万美元（约1.7亿元人民币）。据报道，FIFA向央视开出的单届世界杯转播权初始报价高达2.5亿至3亿美元（约合18亿至21亿元人民币），而央视的预算可能仅在6000万至8000万美元左右；即便经过多轮拉锯谈判降至1.2亿至1.5亿美元，仍与中方转播商的心理预期存在巨大差距。（新浪财经）</p>
  <p><strong>娃哈哈昌盛饮料集团更名宏胜恒枫</strong></p>
  <p>36氪获悉，天眼查App显示，近日，合肥娃哈哈饮料有限公司发生工商变更，企业名称变更为合肥恒枫食品制造有限公司。该公司成立于2006年7月，法定代表人为盛文龙，注册资本1600万美元，经营范围包括饮料生产、乳制品生产、食品生产等，由荣辉投资有限公司、丽水盛佳饮料有限公司共同持股。值得一提的是，近期，浙江娃哈哈昌盛饮料集团有限公司发生工商变更，企业名称变更为浙江宏胜恒枫饮料有限公司。</p>
  <p><strong>任天堂将Switch 2在日售价提高至59980日元</strong></p>
  <p>任天堂将Switch 2在日售价提高至59,980日元，预计新财年Switch 2销量为1650万台。（财联社）</p>
  <p><strong>油价上调，加满一箱92号汽油将多花12.5元</strong></p>
  <p>从国家发展改革委了解到，5月8日24时国内成品油调价窗口将开启。据国家发展改革委价格监测中心监测，本轮成品油调价周期内（4月21日24时——5月8日24时），国际油价先扬后抑。5月8日24时起，国内汽、柴油价格每吨分别上调320和310元，全国平均来看，92号汽油、95号汽油和0号柴油每升分别上调0.25元、0.27元、0.27元。用92号汽油加满50升的油箱将多花12.5元。（央视财经）</p>
  <p><strong>鸣鸣很忙增资至约2.2亿</strong></p>
  <p>36氪获悉，天眼查App显示，近日，鸣鸣很忙关联公司湖南鸣鸣很忙商业连锁股份有限公司发生工商变更，注册资本由2亿人民币增至约2.2亿人民币。该公司成立于2019年12月，法定代表人为晏周，经营范围包括食品销售、食品互联网销售、酒类经营、城市配送运输服务等，由晏周、上海鸟窝广告文化传播有限公司、李维等共同持股。</p>
  <p><strong>钱江摩托否认“围剿张雪机车”</strong></p>
  <p>5月8日，钱江摩托发布声明称，近日，网络流传“国内摩托车大厂从供应链、经销商层面围剿张雪机车”等不实言论，引发行业与公众热议。公司声明，从未以任何形式针对张雪机车及行业友商实施供应链封锁，经销商围剿等不正当竞争行为。（界面新闻）</p>
  <p><strong>上交所：对*ST正平等异常波动退市风险警示股票、国晟科技等波动较大股票及全球芯片LOF等溢价较高基金进行重点监控</strong></p>
  <p>财联社5月8日电，2026年4月27日至2026年5月8日，上交所对351起拉抬打压、虚假申报等证券异常交易行为采取了自律监管措施，对*ST正平等异常波动退市风险警示股票、国晟科技等波动幅度较大的股票以及全球芯片LOF等溢价较高的基金进行重点监控，对29起上市公司重大事项等进行专项核查，向证监会上报涉嫌违法违规案件线索2起。（财联社）</p>
  <p><strong>一线城市楼市延续“小阳春”行情，购房需求有望持续释放</strong></p>
  <p>在刚刚过去的4月份，一线城市房地产市场延续了3月份以来的“小阳春”行情，二手房市场交易维持高活跃度，新房市场表现平稳。中指研究院指数研究部总经理曹晶晶对记者表示，从4月份数据来看，核心城市楼市“小阳春”行情延续，新建商品住宅销售面积同比基本持平，重点城市二手房成交量同比增长明显，其中北京二手房成交量创近五年4月份单月新高，反映出需求仍在持续释放、市场预期有所好转。值得关注的是，随着政策的进一步优化，5月份购房需求有望持续释放。（证券日报）</p>
  <p><strong>小米汽车高层调整：副总裁于立国兼任海外业务筹备组组长</strong></p>
  <p>小米汽车近日迎来人事调整，汽车部副总裁于立国兼任海外业务筹备组组长，将向集团CEO、汽车部总裁雷军和集团总裁卢伟冰双线汇报。汽车部副总裁宋钢分管生产制造部、智能制造部、体系运营部，将向集团CEO、汽车部总裁雷军直接汇报。（新浪科技）</p>
  <p><strong>极氪：任何声称可通过非官方渠道、内部关系或异常低价购车的账号及内容均与极氪无关</strong></p>
  <p>5月8日，极氪法务部发文称，近日，关注到网络上出现部分非官方账号，散布所谓“低价代购极氪新车”、“特价二手车”等不实信息，用夸张的方式引流，“以挂羊头卖狗肉”的方式误导消费者，造成财产损失，扰乱正常购车秩序，对此，极氪郑重声明：极氪始终严格执行统一售价、统一购车权益的官方销售政策。任何声称可通过非官方渠道、内部关系或异常低价购车的账号及内容，均与极氪无关，也非我司授权合作渠道。（界面新闻）</p>
  <p><strong>美股收盘：纳指、标普500指数连涨六周再创新高，多只存储芯片股大涨并创新高</strong></p>
  <p>美股三大指数集体收涨，纳指涨1.71%，本周累涨4.51%；标普500指数涨0.84%，本周累涨2.33%；道指涨0.02%，本周累涨0.22%；费城半导体指数涨5.51%，本周累涨11.14%。其中，纳指、标普500指数连续第六周上涨，为2024年10月以来最长连涨周期，并再创新高。（界面新闻）</p>
  <p><strong>30条中日航线4月取消全部航班</strong></p>
  <p>航班管家DAST最新统计显示，4月共有30条中日航线取消全部航班，比3月取消数量有所减少。不过，4月实际执行的赴日航班较3月整体减少182班。整个4月中国大陆赴日本共有1543个航班取消，取消率为37.7%。（第一财经）</p>
  <p><strong>SK海力士员工成相亲市场“顶流”&nbsp;</strong></p>
  <p>伴随着SK海力士业绩创新高以及绩效薪酬水涨船高，SK海力士员工近期一夜跻身韩国婚恋相亲市场顶层梯队，社会择偶认可度已与医生、律师等传统高薪精英职业平起平坐。婚介公司Gayeon的高级团队负责人姜恩善（Kang Eun-sun）对媒体表示，“自半导体超级周期开启以来，三星电子和SK海力士等大型企业的人气持续上升，相比一些收入已不如从前的律师，市场明显更偏好那些实际收入远远更高的工程师。”这一现象的核心驱动力来自该公司与员工共享的巨额利润分红。去年9月，SK海力士与工会达成历史性劳资协议，废除此前“利润分享金（PS）不超过基本工资10倍”的上限，改为将年度营业利润的10%纳入奖金池。（界面新闻）</p>
  <p><strong>苹果公司提高2026年MacBook Neo产量目标至1000万台</strong></p>
  <p>5月7日消息，据报道，苹果公司已要求供应商将2026年MacBook Neo笔记本电脑产量目标，由最初的500万至600万台大幅上调至1000万台，以缓解当前市场供应紧张局面，即使该公司不得不向台积电支付巨额溢价以确保A18 Pro芯片的供应。（界面新闻）</p>
  <p><strong>英伟达CEO黄仁勋：下一代AI基础设施将需要大量的光学连接，铜线已无法满足需求</strong></p>
  <p>美东时间5月6日，英伟达首席执行官黄仁勋在接受采访时，大力赞扬其与康宁公司的新合作项目，称其为美国重建技术供应链带来重要机遇。黄仁勋表示，下一代人工智能基础设施将需要大量的光学连接，因为计算需求正在迅速增长，以至于铜线已经无法满足需求。“我们将以一种前所未有的规模来扩大光学技术的应用，坦率地说，没有哪家光学公司曾有过这样的规模。”黄仁勋说道。黄仁勋还表示，当前这波人工智能投资所带来的益处远不止惠及科技公司。他指出，AI产业对电工、建筑工人、芯片制造员工以及数据中心基础设施专家的需求不断上升，这就是该建设进程已经波及整个经济领域的有力证明。（财联社）</p>
  <p><strong>SpaceX冲刺上市，资本开支飙升数百亿</strong></p>
  <p>随着埃隆・马斯克执掌的太空探索技术公司筹备大规模首次公开募股，其资本开支规模正以数十亿美元的幅度持续攀升。据得州当地政府一份项目公告显示，SpaceX计划与特斯拉联合打造的太拉晶圆芯片产业园，预估资本投入至少需要550亿美元。这家涉足火箭、卫星及人工智能领域的企业，正持续加码航天相关基建投资，包括佛罗里达州发射场、得州新建太阳能电池工厂。公司还规划未来数年投入更多资金，拟向近地轨道发射多达百万颗人工智能卫星。（新浪财经）</p>
  <p><strong>Anthropic正考虑进行融资，估值接近1万亿美元</strong></p>
  <p>据英国《金融时报》5月8日报道，Anthropic正考虑在今年夏天筹集数百亿美元，用于大规模扩充计算能力。此举可能使其估值升至近1万亿美元，从而超越竞争对手OpenAI。Anthropic新一轮融资预计投前估值约为9000亿美元，融资规模最高可达500亿美元。Anthropic近期一直在处理来自Dragoneer投资集团、General Catalyst和光速创投（Lightspeed Venture Partners）等投资方的投资意向。（新浪财经）</p>
  <p><strong>法国网络犯罪部门对马斯克及X平台启动刑事侦查</strong></p>
  <p>法国巴黎检察院5月7日通报，法国网络犯罪监管部门已将针对埃隆・马斯克及其旗下社交平台X的调查，升级为刑事立案侦查。法国检方表示，法国相关部门已于4月20日向马斯克及X平台前首席执行官琳达・亚卡里诺发出传票，二人均拒绝出庭接受问询。今年2月，法国执法部门突袭了X平台巴黎办公室，马斯克随后称这项调查是一场“政治攻击”。（新浪财经）</p>
  <p><strong>软银将OpenAI保证金贷款目标下调40%</strong></p>
  <p>5月8日，据报道，知情人士称，软银集团计划以其持有的OpenAI股份为抵押，寻求100亿美元贷款，但由于部分债权人持犹豫态度，已缩减了这一规模，目标金额已低至60亿美元。知情人士补充称，讨论仍在进行中，包括最终借款规模在内的细节可能有所变化。（界面新闻）</p>
  <p><strong>索尼与台积电将在日本成立合资企业生产图像传感器</strong></p>
  <p>5月8日，索尼半导体解决方案公司宣布与台积电签署了一项不具约束力的协议，将共同开发和制造下一代图像传感器。声明显示，双方将成立一家合资企业，在索尼位于日本熊本县的晶圆厂内建立生产和研发生产线。索尼将成为该合资企业的控股股东。目前该合资企业正在考虑投资事宜。（界面新闻）</p>
  <p><strong>欧盟警告航空公司：因油价上涨取消航班必须赔偿乘客</strong></p>
  <p>欧盟交通运输专员阿波斯托洛斯·齐齐科斯塔斯（Apostolos Tzitzikostas）近日向航空公司发出明确警告：因燃油价格上涨而取消航班，必须对乘客进行赔偿。由于中东冲突推高航空燃油价格，此前已有数家航空公司在过去两周内削减了5月航班计划中的200万个座位。（新浪财经）</p>
  <p><strong>华尔街传奇投资人：AI牛市还能再持续一两年，已加码布局</strong></p>
  <p>近日，在AI交易的刺激下，美股屡创新高，与此同时，关于科技板块即将迎来痛苦回调的讨论也甚嚣尘上。但美国传奇投资人、亿万富翁对冲基金经理保罗•都铎•琼斯（Paul Tudor Jones）并未撤离AI投资赛道，反而加码投资。以科技股为主的纳斯达克100指数仅在过去一个月就上涨了18%，但琼斯认为，市场尚未触见顶。他认为，由AI驱动的牛市有望再持续一两年。（财联社）</p>
  <p><strong>三星家电门店称月底或下月中旬退市：“被国产压得太厉害”，中国产线仍面向海外</strong></p>
  <p>三星家电在中国市场的调整正在进入门店一线。记者探访发现，有门店工作人员称，相关家电产品“被国产压得太厉害”，预计月底或下月中旬不再销售。不过，销售端收缩并不意味着制造端撤离，三星家电相关产线仍在中国，产品更多面向海外市场。专家认为，这背后反映出中国家电市场竞争逻辑正在变化，外资品牌如果在本土化、产品创新和服务支撑上跟不上，就很难再仅凭品牌光环赢得消费者。（第一财经）</p>
  <h2><strong>AI最前沿</strong></h2>
  <p><strong>OpenAI推出“可信联系人”安全功能</strong></p>
  <p>当地时间5月7日，OpenAI宣布推出“可信联系人”功能。具体而言，如果OpenAI的自动化系统和经过培训的审核人员检测到成年用户可能曾讨论过自残行为，且这种行为可能构成严重的安全隐患，则该联系人将会收到通知。声明称，该功能不会取代专业护理或危机干预服务，而是为处于困境中的用户提供多重保障措施。ChatGPT仍会鼓励用户在适当情况下联系危机热线或紧急服务部门。（界面新闻）</p>
  <p><strong>软银与英伟达和鸿海磋商，拟开发“日本制造”的AI服务器</strong></p>
  <p>据报道，软银集团开始与英伟达和鸿海磋商，考虑开发“日本制造”的人工智能服务器，最早下周一公布计划。据悉，软银希望到本十年末先通过组装外部采购的组件建立生产系统，最终全面掌控服务器的制造流程。（界面新闻）</p>
  <p><strong>商汤发布日日新SenseNova Token Plan</strong></p>
  <p>36氪获悉，商汤发布日日新SenseNova Token Plan，并同步开启限时免费活动。据了解，SenseNova Token Plan全面支持商汤日日新SenseNova系列模型，包括新一代轻量化多模态智能体模型SenseNova 6.7 Flash-Lite，原生理解生成统一多模态模型SenseNova U1 Fast等。</p>
  <p><strong>飞算JavaAI上线智能体模式，推出智能引导功能</strong></p>
  <p>36氪获悉，5月8日，飞算JavaAI宣布正式上线智能体模式。据了解，该模式以多专家级Agent协作重构Java开发全流程，推出智能引导功能，全程可视化可控。该模式实现了四重交互形态，覆盖Java开发全场景。同时，飞算JavaAI的AI工具箱集成了十大垂直领域专家Agent，覆盖项目文档生成、编译修复、安全加固、框架迁移等场景。</p>
  <h2><strong>上市进行时</strong></h2>
  <p><strong>贝特利创业板IPO获上市委会议通过</strong></p>
  <p>36氪获悉，贝特利创业板IPO获上市委会议通过。</p>
  <p><strong>昆仑芯（北京）科技股份有限公司</strong></p>
  <p>36氪获悉，据证监会官网显示，昆仑芯（北京）科技股份有限公司于2026年5月7日正式启动科创板上市辅导，中国国际金融担任辅导机构。昆仑芯仍在正常推动港股上市进程。</p>
  <p><strong>广东天农集团股份有限公司</strong></p>
  <p>36氪获悉，据港交所文件，广东天农集团股份有限公司向港交所提交上市申请书，独家保荐人为招商证券国际。</p>
  <h2><strong>大公司财报</strong></h2>
  <p><strong>丰田预计全年销售净额51万亿日元，低于市场预期</strong></p>
  <p>丰田汽车第四财季销售净额12.60万亿日元，同比增长1.9%，预估12.72万亿日元；净利润8,172.1亿日元，同比增长23%，预估7,316.5亿日元。丰田预计全年销售净额51.00万亿日元，市场预估53.25万亿日元；丰田预计全年净利润3.00万亿日元，市场预估4.04万亿日元。（财联社）</p>
  <p><strong>爱彼迎：第一季度营收27亿美元，同比增长18%</strong></p>
  <p>36氪获悉，Airbnb爱彼迎发布2026年第一季度财务业绩。Airbnb爱彼迎发布2026年第一季度财务业绩。财报显示，第一季度营收达到27亿美元，同比增长18%；录得净利润1.6亿美元，调整后的税息折旧及摊销前利润（Adjusted EBITDA）达5.19亿美元，同比增长24%。</p>
  <p><strong>台积电：4月销售额4107.3亿元新台币，同比增长17.5%</strong></p>
  <p>36氪获悉，台积电4月销售额4107.3亿元新台币，同比增长17.5%，1-4月累计销售额15448.3亿元新台币，同比增长29.9%。</p>
  <p><strong>正虹科技：4月生猪销售收入1373.48万元，环比增长606.03%</strong></p>
  <p>36氪获悉，正虹科技公告，公司2026年4月销售生猪1.51万头，环比增长769.38%，同比增长34.79%；销售收入1373.48万元，环比增长606.03%，同比增长40.2%。2026年1—4月份，公司累计销售生猪3.41万头，累计销售收入3499.97万元，同比分别增长21.31%、11.79%。</p>
  <p><strong>壳牌一季度利润69亿美元超预期</strong></p>
  <p>壳牌5月7日公布的一季度利润达到69亿美元，创两年新高，超出市场预期。受此推动，该公司将股息提高5%。与此同时，壳牌将季度股票回购规模从35亿美元放缓至30亿美元，以将现金调配至资产负债表，应对战争导致能源供应中断后债务增加所带来的短期流动性压力。（新浪财经）</p>
  <h2><strong>投融资</strong></h2>
  <p><strong>预测平台Kalshi完成10亿美元F轮融资，估值达220亿美元</strong></p>
  <p>5月7日，预测市场平台Kalshi宣布完成10亿美元的F轮融资，估值达到220亿美元。本轮融资由Coatue领投，红杉资本、安德里森·霍罗威茨、IVP、Paradigm、摩根士丹利及ARK Invest参投。Kalshi称，此次融资正值机构需求加速增长之际，在过去六个月里，机构交易量激增了800%。（界面新闻）</p>
  <p><strong>“阶跃星辰”将完成近25亿美元融资</strong></p>
  <p>36氪获悉，国产大模型公司“阶跃星辰”将完成近25亿美元融资，并已拆除红筹架构，加速赴港IPO准备。据了解，最新融资中产业链资本集中入场，包括华勤、龙旗、豪威、中兴等；此外， 香港投资管理有限公司（HKIC）也出现在股东名单中。</p>
  <p><strong>“未来智能”完成亿元级A+轮融资，与传音合作打造下一代AI Agent硬件</strong></p>
  <p>5月8日，AI硬件公司“未来智能”完成亿元级A+轮融资，传音参投并达成战略合作。双方将整合各自在硬件研发及全球渠道上的优势，共同打造具备自主感知与执行能力的下一代AI Agent硬件。据了解，本轮融资资金将重点用于两大方向：一是加大AI Agent领域的人才投入和生态建设，二是拓展上游供应链，联合核心元器件厂商共同开发面向“AI听”与“AI看”的专用硬件组件，构建下一代AI硬件的底层能力。</p>
  <h2><strong>酷产品</strong></h2>
  <p><strong>千问AI眼镜升级主动服务能力</strong></p>
  <p>36氪获悉，5月8日，千问AI眼镜S1升级主动服务等一系列AI能力，可主动提醒用户“出门带伞”、“抬头活动一下”，打车、闪购、规划行程等生活AI能力也将于本月上线。</p>
  <p><strong>知名爆料人：苹果首款AI视觉TWS设备已进入开发后期阶段</strong></p>
  <p>苹果知名爆料人马克·古尔曼在最新文章中表示，苹果新款内置摄像头的AirPods已经进入开发后期阶段。据知情人士透露，该项目已经进入原型机具备接近最终设计和功能的DVT（设计验证测试）阶段。DVT是PVT（生产验证测试）前的最后一个重要开发阶段，后者会涉及早期量产。就产品卖点而言，新款AirPods将依赖摄像头观察用户周围空间并提供信息。这些摄像头本质上是（AI升级版）Siri助理的“眼睛”，并非用于拍摄照片或视频，仅以低分辨率捕捉视觉信息。除了因容纳摄像头而加长的柄部外，这款产品外观上类似去年推出的AirPods Pro 3。（财联社）</p>
  <h2><strong>AI图谱</strong></h2>
  <p>慧算账将腾讯云ClawPro接入企业微信工作流。作为一站式AI Agent平台，ClawPro支持模板部署、资源配额和使用监测。接入后，单个会计服务客户数由200至300家提升至400至500家，企业也可按场景追踪Token消耗，优化交付成本。</p>
  <p class="editor-note">本文来自微信公众号<a href="https://mp.weixin.qq.com/s?__biz=MzI2NDk5NzA0Mw==&amp;tempkey=MTM3M19BM2V0WE5XZkN2Nzg2QWcwQzBIcUxzc3FBbTZkUkpLdWw5REZwd1VWYmZIcXd2S2Z1a205c1RuSVVwTnVKWklWUXlXWUtJeEsyazR4akZMai1nWV9WN0ltNVVoV01scVctYWprUGlDVHdFRldJdUxMSWVQSXRWeUk3dFpSalZfWnl4T0ttTmlWWkJ6cC1KRlFWS0M4Nzh2ODA5Sll0enRvSDdoRjhBfn4%3D&amp;chksm=695bfc2f5e2c753927c718f29c2b4510d0a974f4fe4a974d3c52d8a026371771ba4ba81b551c&amp;xtrack=1&amp;scene=1&amp;subscene=93&amp;sessionid=1778287807&amp;flutter_pos=0&amp;clicktime=1778287808&amp;enterid=1778287808&amp;finder_biz_enter_id=4&amp;jumppath=1123_1778287796989%2C1003_1778287804756%2C1001_1778287805097%2C50094_1778287807530&amp;jumppathdepth=4&amp;ascene=56&amp;fasttmpl_type=0&amp;fasttmpl_fullversion=8248797-zh_CN-zip&amp;fasttmpl_flag=0&amp;realreporttime=1778287808712#wechat_redirect" rel="noopener noreferrer" target="_blank">“36氪”</a>，36氪经授权发布。</p>

- **技术标签**: `agent` `anthropic` `chatgpt` `deepseek` `gpt`


---


## 147. 「维新宇航」完成数千万元天使+轮融资，7座3吨级eVTOL将于7月进行首飞测试｜36氪首发

- **来源**: [36kr](https://36kr.com/p/3800495686163721?f=rss)

- **摘要**: <p>文&nbsp;|&nbsp;阿至</p>
  <p>36氪获悉，<strong>低空出行产品研制商「维新宇航」已完成数千万元天使+轮融资，本轮融资由策源资本领投、金舵投资跟投，</strong>资金将主要用于加速公司首款主力机型 Vector 5的研发迭代、首飞测试与适航取证进程。</p>
  <p>维新宇航成立于2023年，是36氪长期关注的企业，其专注于大载客量、大载重eVTOL/eCTOL产品的研发及制造。<strong>加上6个月前连续完成的种子轮、天使轮，目前维新宇航已完成三轮融资，累计资金交割总额超亿元人民币。</strong></p>
  <p>现阶段，维新宇航的<strong>主力机型Vector 5为一款7座3吨级纯电复合翼eVTOL</strong>，该机型专注于应急救援和医疗急救等民生刚需场景，最大起飞重量为3180kg、最大载荷为680kg，最大航程300km、最高巡航速度为 250km/h，全尺寸样机已于去年6月正式下线。</p>
  <p class="image-wrapper"><img src="https://img.36krcdn.com/hsossms/20260508/v2_75aa3e43915a4513bff713461938b436@577536001_oswg112335oswg1080oswg720_img_000?x-oss-process=image/format,jpg/interlace,1" /></p>
  <p class="img-desc">Vector 5全尺寸样机</p>
  <p>据维新宇航创始人兼CEO何威介绍，<strong>今年3月底，维新宇航完成了Vector 5全尺寸框架机的首飞。</strong></p>
  <p>所谓框架机，是指将整机所需的电机、电控、电池、飞控等全部设备集成在1:1全尺寸的飞机骨架上进行联调测试，避免反复拆装口盖的繁琐步骤，在提高测试效率的同时也能够减少结构磨损。</p>
  <p><strong>据悉，维新宇航上半年已完成数十次框架机的试飞联调，为Vector 5全尺寸样机的7月首飞做准备。</strong></p>
  <p>在适航取证方面，去年12月8日，中国民用航空西北地区管理局正式受理了Vector 5的型号合格证（TC）申请，其整机及核心子系统同步进入适航审定流程。按照公司发展规划，<strong>其首款载货版Vector 5有望在2027年底完成取证</strong>，这也意味着维新宇航进入适航冲刺的关键窗口期。</p>
  <p>除了集中资源推进Vector 5的技术成熟度提升和适航进程，何威也指出，公司的二代机型，11座3吨级固定翼eCTOL——Vector 11的研发也在同步推进中，该机型的全尺寸样机有望在今年底正式下线，这也将进一步完善维新宇航从3吨级到更大运力级别的产品谱系建设。</p>
  <p>据介绍<strong>，维新宇航接下来将重点围绕飞行控制技术、快充配套技术、低空通信技术这三大核心科研方向做投入，</strong>在航空关键技术上形成持续突破，做到自主可控，配合外部供应链体系建设的进一步完善，推动产品从工程样机阶段稳步迈向商业化交付。</p>
  <p>“主机厂的核心竞争力在于系统定义与集成能力。”何威强调，“航空产业专业度划分更细、适航要求的颗粒度更高，我们聚焦结构定义与系统整合，航空器核心的算法、控制、总体结构必须要自研，而电机、电池等硬件则会选择外采，发挥产业协同的优势，把专业的事交给优质的合作伙伴去完成。”</p>
  <p>事实上，通过“缩比机先行验证+供应链体系协同+全尺寸机工程化落地”的研发路径，维新宇航在降低早期研发成本、提���测试效率的同时，其1:4缩比机在研发初期也承担了技术验证与交付客户定制化需求的双重角色。据悉，该板块订单在2025年已累计实现了千万级营收。</p>
  <p>但何威也强调，“接下来，随着全尺寸飞机研发进入高强度阶段，团队资源将向全尺寸飞机集中，缩比机业务的增长不是当前重心。<strong>我们今年会下线两到三架全尺寸飞机，陆续在不同的场景和工况下做大量测试，这是今年比较大的工作项。</strong>”</p>
  <p>换句话说，营收数字并不是今年公司的考核指标。</p>
  <p>事实上，低空经济行业目前仍处于“技术验证加速+适航取证冲刺”的投入期，而非规模化交付的产出期，这意味着对eVTOL创业公司而言，<strong>现阶段能够更快、更稳地完成技术和飞行验证、走完适航审定流程，远比做出几百万收入更能决定其行业位次和生存概率。</strong></p>
  <p>而从资本市场的估值逻辑来看，现阶段投资eVTOL的机构，更看重的是远期的万亿级市场空间和生态卡位，而非短期现金流。因此，行业投入期的核心竞争指标更多聚焦在技术迭代速度、适航进度、资金储备和团队工程能力。谁先拿到三证、谁先建立量产和供应链壁垒，谁就能在2030年后的规模化竞争中占据主导地位。</p>
  <p>何威提到，<strong>维新宇航预计将在2028年实现量产，目前公司有100架左右意向订单，除了国央企和地方客户，还有三分之一的业务需求来自海外。</strong>未来随着团队对海外意向采购方需求的持续挖掘，全球化业务的占比有望进一步提升，考虑到适航认证的友好度，中东和东南亚将会是优先级更高的拓展区域。</p>
  <p>整体来看，2026年一级市场对低空领域的关注度仍在提升，上半年不乏大额融资出现，头部厂商开始冲刺上市，梯队分化加剧，差异化竞争成为关键。</p>
  <p>在这样一个决定行业未来座次的关键分水岭，何威希望维新宇航能够成为低空领域的“优质新势力”——找准差异化赛道，以更低的研发成本和更明确的节奏切入。小步快跑，在每一个时间节点上用更低的成本完成技术验证，把差异化的机型尽早推向市场。</p>
  <p>“2027年是一个关键节点，行业整体（eVTOL公司）可能会收窄到10家以内，我们的目标是今年成为行业头部，做好充足的资金储备参与后续竞争，持续向第一梯队迈进。”何威补充道。</p>
  <p>据悉，维新宇航新一轮融资也正在进行中。</p>
  <p><strong>投资方观点</strong></p>
  <p><strong>策源资本表示：eVTOL产业正从技术验证迈入规模化商业化关键周期。维新宇航充分发挥后发优势，初步构型符合适航标准，已实现型号合格证 TC 申请受理，快速迈入适航审定核心阶段。作为投资方，我们将充分发挥航空航天领域的投资布局与产业资源整合优势，赋能企业深耕核心技术自研攻关，协助推进适航取证与商业化落地进程，助力国内低空经济产业生态高质量发展。</strong></p>


---


## 148. 卡位黄金价格带，问界M6向下争夺年轻群体｜最前线

- **来源**: [36kr](https://36kr.com/p/3800183520091398?f=rss)

- **摘要**: <p>2026年的中国新能源SUV市场正经历着前所未有的内卷。</p>
  <p>问界依托华为技术体系，推出了定位更亲民的全新车型 M6， 瞄准主流家用消费群体。放在问界品牌整体销量连续数月下滑、赛力斯盈利能力承压的背景下，M6的到来既是“救兵”，更是一场不容有失的“大考”。</p>
  <h3>卡位黄金价格带，向下争夺年轻群体</h3>
  <p>从产品命名逻辑看，M6位于M5与M7之间，车身尺寸为4960×1985×1736mm，轴距2950mm，属于标准的中大型五座SUV。官方定位为“新锐智慧SUV”，目标用户从问界以往的主力“30岁以上家庭用户和商务人群”向下延伸至25-35岁城市年轻群体。</p>
  <p>25-30万元是目前中国新能源SUV市场竞争最激烈的价格带——特斯拉Model Y、理想L6、小鹏G6、比亚迪唐等车型均在此区间鏖战。作为参考，理想L6起售价24.98万元，小鹏G6起售价20.99万元，Model Y后驱版26.35万元。问界M6以25.98万元起售，锚定的正是理想L6的核心区间，试图以更低门槛的增程方案和更激进的全系标配策略争夺年轻家庭用户。</p>
  <p>从实际的用户构成来看，M6确实实现了问界品牌年轻化的意图。终端调研显示，问界M6的购车人群中，30-40岁客户占比约45%，30岁以下客户约25%，合计达70%，成为绝对核心购车人群，35岁以下占比超四成。女性客户占比达35%，较以往问界车型也有明显提升，超八成客户为1-2人小家庭。</p>
  <p>据公开消息，纯电版本的接受度显著提升，与增程版本几乎形成五五开的均衡格局。iPhone用户占比达到35%，说明M6已成功吸引大量非华为生态用户，品牌影响力正在向更广泛的消费圈层拓展。</p>
  <p>从消费决策偏好来看，M6的用户更关注家庭场景，倾向于将选配金用于副驾零重力座椅与车载吸顶屏，而非外观件——这一点在配置选择上体现出明确的家用务实导向。</p>
  <h3>智能化优势突出，硬件配置主打均衡务实</h3>
  <p>问界M6的产品策略可以用一句话概括：在少数几个维度做到极致，在其他维度不拖后腿，同时在成本敏感环节做出取舍。</p>
  <p><strong>核心亮点</strong>是全系标配华为乾崑智驾ADS 4.1高阶版，硬件上搭载1颗896线双光路图像级激光雷达及36个高精度传感器。896线激光雷达是目前全球量产车中规格最高的之一，理论上对小目标和异形障碍物的识别能力更强。底盘方面，全系标配前双叉臂后五连杆独立悬架、闭式空气悬架和CDC连续可变阻尼减震器，在25万级SUV中尚属首次全系标配空悬。纯电版标配100kWh华为巨鲸电池，CLTC续航760km；增程版CLTC综合续航1605km，纯电续航355km，百公里亏电油耗5.9L。</p>
  <p>这些配置在过去通常出现在30万元以上的产品上。以空悬为例，理想L6使用的是螺旋弹簧加CDC减震器，空气悬架需要上到L7以上才有；小鹏G6只有顶配提供选装；Model Y全系没有空气悬架。从这个意义上说，M6确实实现了部分高端配置的“技术普惠”。</p>
  <p>但短板也同样直接。增程低配版仅搭载37kWh电池，CLTC纯电续航235km，放在2026年的市场中这一续航规模已显局促。总体来看，M6是一款在智驾和底盘上做足了功课、但在续航和空间维度上“刀法精准”的产品。</p>
  <h3>市场热度不容小觑，订单仍有挑战</h3>
  <p>从订单数据来看，M6的市场热度不容小觑。</p>
  <p>3月23日开启预售后24小时订单突破6万台，不到20天累计预订突破10万台。正式上市后15分钟大定即破万，首周交付量达到6,500台。截至4月30日，甄选配置现车已交付超5000位用户。</p>
  <p>然而，M6上市前，问界品牌正经历车市的低迷周期：2026年1月交付40,016辆，2月降至约18,000辆，3月仅为20,234辆。过去的半年里，曾经月销2万+的M7销量大幅滑坡，M9虽守住高端局但体量有限。</p>
  <p>在鸿蒙智行2026年全年目标100万辆的背景下，问界M6的销售压力并不小。不过，尽管小鹏、理想等品牌的智驾方案正在快速迭代，但“华为智驾”在目标用户群中仍具有较高的认知溢价和信任度，这一无形资产难以在短期内被复制，M6依然握有华为智驾品牌心智壁垒的筹码。</p>


---


## 149. 小红书四年AI 路：FOMO、犹豫，到突然加速

- **来源**: [36kr](https://36kr.com/p/3799028783439111?f=rss)

- **摘要**: <p>作者&nbsp;|&nbsp;肖思佳</p>
  <p>编辑&nbsp;|&nbsp;乔芊 杨轩</p>
  <p>所有互联网大中厂都渴望在AI时代博得位置，在这场比赛中，小红书曾是克制的那个。</p>
  <p>在一个搜索属性与社区属性并存，以真实经验分享为核心的产品中，活人感与AI、温情和算法，始终像天平的两端。</p>
  <p>很长一段时间里，小红书既没有完全缺席技术探索，也没有像许多同行那样高调推进AI产品化。相反，这家公司始终在两股力量的拉锯和平衡中前行：一边持续投入模型能力，一边谨慎控制AI对社区生态的介入。</p>
  <p>但2026年，随着Agent叙事的升温，小红书开始显露出某种急迫。</p>
  <p>4月30日，小红书发送全员内部信，宣布成立AI一级部门Dots，“建立从模型研发、基础设施、工程到产品的完整技术体系，整合顶尖AI人才和资源。”Dots向小红书新任总裁柯南汇报。</p>
  <p>据36氪了解，Dots部门由原人文智能实验室Hi Lab升级而来，下设模型研发、基础设施、工程、产品四个部门。目前小红书内部最重要的AI应用产品“点点”也被纳入该体系之下。</p>
  <p>将AI置于更高优先级的背后，是小红书长期未解的一道命题。多年来，小红书始终握有业内艳羡的社区资产和广告基本盘，也想通过电商、直播等业务，去撬动新的增长，却始终未能真正打开局面，让生意规模再上一个台阶。</p>
  <p>“社区”就像一个装满可能性的宝箱，AI被视作新的变量和机会。但它能否成为答案，仍未可知。至少现在看来，小红书的AI故事，仍在起笔阶段。</p>
  <h2><strong>01 &nbsp;一条没有走通的产品化路径</strong></h2>
  <p>2022年末ChatGPT问世之际，针对小红书的未来，创始人毛文超曾借用员工的手机，向GPT提出过一个问题：小红书是否会被颠覆？AI会给小红书带来怎样的危险？</p>
  <p>据知情人士向36氪透露，那段时间，毛文超开始密集地关注与人工智能相关的动态信息，并要求团队每两周进行一次进展汇报。</p>
  <p>2023年8月，在一封内部信中，毛文超重申了小红书的核心优势。他提到，与外国朋友交流时，发现人们会在ChatGPT上询问大量与生活经验相关的问题，这与小红书的定位有所重叠。但他同时判断，这一现象源于海外缺乏类似的经验内容沉淀，而小红书上则拥有海量真实生活的内容分享。言下之意是：小红书长期沉积下来的内容护城河，一时还难以被AI动摇。</p>
  <p>不过从另一个角度来看，毛文超的确把AI视作一个小红书的潜在威胁。</p>
  <p>ChatGPT的出现，迅速对谷歌、百度这类传统搜索公司形成冲击。而这对当时仍以“你的生活指南”为Slogan、强调社区搜索属性的小红书来说，同样制造了一种难以回避的不安。</p>
  <p>不安引发行动。在ChatGPT的催化下，2023年，国内互联网大厂加速了大模型基座的布局与投入，并在此基础上逐步推进产品化落地，形成了今天以豆包、千问、元宝为代表的AI应用形态。目的是抢占下一个时代的入口权。</p>
  <p>小红书也考虑了这个路径。2023年，小红书初步开始在内部推动技术能力的建设，于3月筹备了独立的大模型团队，由AI创新负责人张德兵（薯名“宇尘”）牵头自研通用大模型基座。该团队最初以基座模型研发为主，随后逐步向产品侧延伸，于2024年8月推出了独立的AI应用点点。</p>
  <p>但和那些多少带着技术基因的公司不同，对小红书来说，这是条崭新而陌生的道路。</p>
  <p>点点的产品定位是生活搜索助手，起初接入的是小红书自研的珠玑大模型。然而到了2025年2月26日，点点却公开宣布接入DeepSeek。根据前述人士的回忆，这是因为其基础模型的实际使用体验并不理想。</p>
  <p>据另一知情人士透露，点点团队早期由宇尘负责推进，并直接向毛文超汇报。但在 2025 年初，小红书对团队进行了重新拆分：技术侧仍由宇尘负责，产品侧则交由毛文超的斯坦福校友、新加入小红书的天圣主导。不过，点点团队后来经历多轮变动，目前天圣担任小红书基础模型后训练负责人。</p>
  <p>某种程度上，这也宣告了小红书自研模型的路径，暂时还未跑通。“大模型部门没有被废除，但它和各个产品也都没有接触。”前述知情人士表示。一个佐证是，目前小红书社区内的另一款AI搜索产品“问一问”，接入的是开源的通义千问模型。</p>
  <p>伴随模型选择的调整，点点在产品路径上也出现了更为明显的转向。</p>
  <p>据36氪了解，点点的探索大致经历了四个阶段：</p>
  <p><strong>第一阶段：基模探索。</strong>早期团队以自研基础模型为核心推进，但效果未达预期，最终转向接入DeepSeek等外部模型。不过，内部对基模路径的探索并未完全停止。</p>
  <p><strong>第二阶段：人文化转向。</strong>毛文超提出要为点点打造更具人文气质的人设，并提出如“45度角仰望生活”“柏拉图式的旅行家”等人设画像。与此同时，2025年初，小红书将原有的大模型技术与应用产品团队整合为Hi Lab（人文智能实验室），并大规模招聘具有人文学科背景的“人文训练师”为模型进行后训练。</p>
  <p><strong>第三阶段：产品迭代。</strong>2025年7月，点点推出2.0版本，升级UI并加入语音、图像等多模态交互。但改版也引发用户争议，例如深色背景和气泡式回答结构，被认为降低了阅读体验。</p>
  <p><strong>第四阶段：回归社区。</strong>2025年11月28日，点点官方连发两条动态，宣布完成关键调整：不仅重整了App的形态，还首次进入小红书主站左上角入口，从独立应用转向站内内置能力，成为日常浏览与搜索的辅助工具。</p>
  <p>但这个产品的进展却不及预期。“没有和市面上的其他AI类对话产品形成差异化，缺乏竞争力。”多名接近小红书的人士，对点点发表了上述看法。</p>
  <p>在用户端，点点的存在感始终不强，几乎没有激起水花。截止2026年4月底，在App store的下载排行榜中，点点仅位列186名；评分及评论一栏中，只有45名用户为其留下评分，而“豆包”的数据则高达192万个。</p>
  <p>融入社区，既是点点的退一步，也是进一步。自推向市场以来，点点曾多次尝试与社区生态结合，通过“问点点”或“评论区互动”等形式，增加在用户面前的存在感。小红书优质的社区流量，无疑是可以灌溉其的肥沃土壤。</p>
  <p>只不过，在点点之外，小红书社区中本身已经存在另一款名为“问一问”的AI搜索助手，二者在功能上并无明显差别，同样是基于社区数据，对用户提问生成答案。该产品由小红书社区部门下的搜索小组孵化，向算法负责人夏侯汇报。</p>
  <p>产品层的重复建设，本质上是不同部门对AI路径的各自下注。这种“赛马”机制在互联网公司内部并不罕见。36氪据悉，目前小红书内部正在考虑将两个产品进行整合。而与整合一样“待定”的关键问题，还有AI在小红书内部，究竟处于何种位置。</p>
  <h2><strong>02 一个真人社区的克制与犹豫</strong></h2>
  <p>在新技术浪潮面前，FOMO情绪并不曾在小红书内部缺席。但与业内争先恐后拥抱AI的节奏相比，小红书对AI的态度在相当长一段时间里仍显得格外克制——甚至是警惕。</p>
  <p>在一场2024年的社区搜索小组内部会议上，有算法同学抛出过一个问题：AI搜索是否会取代传统搜索，或者两者之间究竟是什么关系？社区搜索算法负责人小灰当时的回应是：“这件事情值得尝试，但它不会是我的O1或O2。”</p>
  <p>将视线放到更大的层面，这一逻辑同样成立。相比AI，小红书始终有更紧迫的事情要做——2026年以前，商业化和电商一直是小红书内部的重头戏，占据着OKR的前两项，AI只能屈居第三。<strong>而在优先级之外，更深层的顾虑在于：对于一个依赖社区氛围与“活人感”运转的平台来说，AI及其生成的内容缺乏温度，用户是否会天然产生排斥？在当时，这个问题并没有明确答案。</strong></p>
  <p>“小红书首页双列图文不对齐的设计，是为了营造一种城市的街道感。用户就像在街区里来回逛，能看到参差错落的招牌，点进一个帖子，就像敲开一扇门。”一位前小红书社区线员工告诉36氪，“因此AI的入口究竟放在哪，小红书一直会有些犹豫。”</p>
  <p>这种犹豫，也体现在点点在社区中的位置变化上。前小红书搜索员工李舒回忆，点点最早进入社区时，入口被安放在搜索页的sug第四列。“他们一直想进社区首页，但始终没开这个口子。当时内部的判断是，社区里不应该出现AI。”</p>
  <p>在推进另一个AI产品“问一问”的过程中，李舒小组也面临着类似取舍。当用户发起搜索时，哪些问题适合弹出AI总结、覆盖到什么范围，这些都存在争议。李舒表示，最初“问一问”只能覆盖1%～2%的query（用户搜索请求），“当时我们希望扩展到10%，但老板不同意，理由是影响面太大，最后只放宽到了3%～4%。”</p>
  <p>2024年，整个AI市场并没有跑出什么颠覆性的创新产品。在最初的焦虑逐渐被冲淡后，毛文超一度失去了对AI的兴致，相关的汇报回也从两周一次，变为一个月甚至两个月一次。“后来慢慢他也不怎么听了。”前述知情人士透露道。当时，毛文超认为小红书的重心还是应该回归自身业务。内部的AI项目虽然还在推进，但并不受到额外关注。&nbsp;</p>
  <p>直到2025年初，Deepseek横空出世，中国迎来了自己的GPT时刻。这意味着，国内用户使用AI成了一件没有门槛的事情。</p>
  <p>小红书内部展开了激烈的讨论，甚至专门做了数据对比：如果用户的手机上同时安装了Deepseek和小红书，用户使用小红书的搜索量会不会降低？“在GPT那会，他们没有觉得AI会代替传统搜索，但Deepseek出来后，他们开始真正担忧这件事了。” 李舒回忆道。</p>
  <p>围绕“是否要像腾讯元宝一样，接入Deepseek R1模型”，“问一问”团队进行了大量争论。后端的技术人员也在反复测试接入R1后的效果，不断分析模型输出的回答质量、等待时长、以及隐私敏感性，来判断是否要执行这一方案。</p>
  <p>但这一决策最终没有被采纳。理由仍然是用户体验——虽然接入Deepseek能输出更优质的回答，但由于当时R1的思维链路更长，使得生成答案的时间增加了。小红书内部认为，这会影响用户在社区中的感受。</p>
  <p>如今回头看，李舒认为这是一个非常正确的决策：“对于AI搜索来说快是最关键的。因为用户不会在那等，他会认为这是个bug。”</p>
  <p>也有质疑的声音。一些员工认为，接入Deepseek明显能增加答案的丰富度和活人感，为什么不用呢？他们想了许多方法来试图解决等待时长的问题，比如离线生产——提前生成好答案，等用户搜索时直接跳出。</p>
  <p>但这些想法都没有真正落地。除了决策层的顾虑外，还存在另外的原因。“当时还有非常多其他任务要忙，导致我们没有人去推进这件事情。”李舒说。时值2025年春节，小红书内部向来有CNY（春节营销）的传统，不仅要赞助春晚，还要策划各种活动。目的是传播品牌年轻化、社交化的形象，与用户产生情感共鸣。这些工作占据了绝大多数人力资源和员工的注意力，此时的AI仍然不具备优先级。</p>
  <p>谨慎本身就是一种信号。2022年，直到成立的第九年，小红书才首次将社区的流量开放给电商业务。面对AI的狂潮，小红书保持了一以贯之的态度：宁可慢，也不要出错。因此，小红书内部一直在探索如何让AI生成的回答更有“人味”，更能与社区的氛围相融。</p>
  <p>除了用户的体验感外，另一个重要的问题是：在一个社区产品中，植入AI搜索总结工具，这是否会降低用户的APP使用时长？当用户能以更高效的方式，直接获取答案和攻略，他们是否还有必要花时间浏览小红书？</p>
  <p><strong>但事实证明，管理层们的最初对AI破坏社区的种种担忧，并没有发生。AI搜索反而为小红书社区带来了增量。</strong></p>
  <p><strong>据36氪了解，2025年，“问一问”功能使社区用户留存率提升约2%–3%——在成熟产品中，这是显著的增长。目前，“问一问”的最新日活用户量达千万规模。用户查询规模也新增数百万级。</strong>“他单个（问题）的浏览时长可能变短了，但他整体的使用频率会增加。”李舒总结道，“比如有人原先一周只问一个问题，但他现在天天都会问题，那小红书的用户留存就会增加。”</p>
  <p>“数据”是语言模型的核心资产之一。小红书沉淀的真实内容，构成了天然的优质语料。在此基础上，AI搜索的生成与总结能力，能让用户更快抵达答案。这也使“点点”在2025年末进入社区主页，成为顺理成章的选择。</p>
  <p>不过，与商业化的冲突也随之浮现。由于AI搜索会根据社区内用户的真实讨论生成产品推荐，这类“原生结果”容易与品牌方利益发生冲突。</p>
  <p>比如当用户提问“什么吹风机好用”时，AI搜索会自动生成A、B、C三个品牌，及每个品牌在社区内被推荐的百分比。“如果一个大客户在小红书投了商业化广告，但在AI搜索里只被排到第三位，对方肯定不乐意。”李舒说。商业化团队曾一度希望AI搜团队不主动生成购物推荐列表。但目前，这一功能仍在小红书内展示。</p>
  <p>“真实感”和“商业化”的矛盾，一直是小红书发展过程中此消彼长的难题——过度商业化侵蚀社区，缺乏商业化又难以为继。随着AI的到来，这种矛盾可能被进一步加剧和放大。</p>
  <h2><strong>03 突然加速，是FOMO还是想明白了？</strong></h2>
  <p>2025年秋季，结束了对美国硅谷的考察之后，毛文超在一场闭门会上做出如下指示：AI技术路线已经收敛，可以做更多投入了。</p>
  <p>所谓的技术路线收敛，指业内在AI的落地上，逐渐形成的一套通用模式：一个大模型打底，支持语音、图片等多模态输入方式，配上垂直数据的知识库和RAG（检索增强生成），最后形成Agent式交互。“翻译一下就是：搜索很重要，同时用户可能会用语音、图片等多模态的方式去做搜索。”一名知情人士总结。</p>
  <p>而搜索，恰恰是小红书在“种草社区”之外，最强烈的用户心智。<strong>在经历过去一年围绕AI搜索的探索后，毛文超似乎逐渐意识到：AI并不会损害社区的价值，并拥有能与小红书“搜索心智”结合的应用场景。因此，小红书对AI的态度，也从最初的警惕与克制，逐渐转向更积极的拥抱。</strong></p>
  <p>随着2026年到来，AI的行业叙事也翻开了新的一页。以对话为核心的Chat类产品已退居其后。OpenClaw（“龙虾”）的出现，将一类以coding能力为基础、具备任务执行能力的Agent推向台前，成为新的注意力中心。整个互联网行业的FOMO情绪也急剧升温。</p>
  <p>即便是最为保守的组织，也难以否认AI在当下的重要性。几乎所有互联网公司，都在试图证明自己具备掌握这一新技术的能力，是一家真正意义上的科技公司。</p>
  <p>小红书也不可避免地变得着急。“全员转型AI产品经理。”一名小红书员工透露。</p>
  <p><strong>自3月以来，所有人都能感觉到：AI在小红书内部的战略地位迅速上升。</strong>不仅技术团队频繁组织分享会，传授Skill的使用心得。非AI岗位也被卷入其中。一些员工被要求学习用vibe coding搭建AI工具嵌入工作流，甚至需要通过问卷，对直属上级的AI使用能力进行评价。</p>
  <p>招聘业务也开始向AI倾斜。2026年校招，小红书几乎只开放AI相关岗位，其中工程师一职占据绝大多数。而此前，内部从事AI工作的员工总共不过百人规模。相比之下，字节仅“豆包”团队就超过千人。</p>
  <p>据了解，小红书在对外招聘AI人才时，通常要求候选人要同时满足“年轻、高潜、大厂高绩效”三条标准。与之相对应的，是小红书在待遇上的大方出手，“薪资是业内独一份的，top中的top。”</p>
  <p>这里追求极致的人效比，和扁平的汇报结构。工程师以一抵三，产品经理的权责范围非常大，“可能一个人可能就要干一个团队��活”。其背后的判断和理念是：臃肿的组织结构只会叠加冗余与分歧，“一群平庸的产品经理，只会造出一个复杂的产品。”上述员工复述道。</p>
  <p>2025年下半年，小红书一度传出要于今年4月上市的风声。靴子没有落地。“因为没有上市，所以小红书更需要AI的故事。”一名前小红书AI员工表示。</p>
  <p>内部对模型底座的探索还在继续。</p>
  <p>2025年中后，小红书Hi Lab团队陆续发布了一系列自研的开源大模型，包括：dots.llm1（文本大模型）、dots.vlm1（视觉语言模型）、dots.ocr（文档解析模型）。此外，还有一系列覆盖多模态推理、图像编辑、深度搜索及代理的开源模型与工具链。但如点点一般，dots系列模型也并未在行业或技术社区中引发太多关注。</p>
  <p><strong>作为一家体量相对有限的公司，小红书的短板显而易见：技术积累与算力资源都不占优势。</strong>尽管诸多内部员工在小红书上对外发帖招聘时，常会附上“卡管够”的说辞。但相比头部大厂动辄千亿的投入，小红书难免有些捉襟见肘。“做个简单点的任务还是不缺卡的。但如果想搞基模，可能就会差一点。”一名内部技术人员向36氪表示。</p>
  <p>另一方面，虽然小红书在招聘方面不吝投入。但内部始终缺乏如吴永辉、姚顺雨这样在技术层面的领军人物。事实上，自前任CTO郄小虎（薯名“山丘”）于2020年前后离职后，小红书至今未再设置CTO职位，其技术架构主要由副总裁风笛和凯奇两名技术VP负责。</p>
  <p>尽管在外界看来，这是一场性价比并不清晰的投入——除少数头部公司外，大多数玩家继续重金押注模型底座，似乎难以获得对等回报。</p>
  <p>但在小红书内部，这更像一道不得不做的必选题。“没这个能力，上不了牌桌。”多名技术人员给出了如上回答。一名接近小红书的人士表示，<strong>小红书自研模型的意义未必在做得有多好，而在于用技术驱动业务，保有参与下一轮竞争的资格：没有底层能力，就无法真正理解技术的边界，也难以在关键节点做出判断。</strong></p>
  <p>迄今为止，AI产品的推陈出新，更多仍靠技术先行驱动——大模型每次能力跃升，都会在原有边界之外“溢出”一些新的可能性。新的产品机会可能藏在这些溢出点里。</p>
  <p>比如，2024年Claude Sonnet 3.5的代码生成能力大幅提升后，外溢出了自主执行任务的Agent能力。Cursor团队率先抓住了机会，根据市场需求挖掘出来优化了自身的产品，迅速获得了开发者市场的认可。<strong>“谁能最快地挖掘 AI 潜能、挖掘出 AI 最厉害的玩法，谁就成功了。这需要人在模型和产品上都有较大的感知。” 前述接近小红书的人士表示。</strong></p>
  <p>因此，即便短期回报不明，这仍是一张小红书需要买下的入场券。</p>
  <p>4月30日，小红书发送全员内部信，宣布新一轮组织升级，成立AI一级部门Dots和企业智能部，从产品技术、组织两方面加大对AI的投入。此外，任命柯南（丁玲）出任总裁，全面整合社区、电商、商业化三大核心业务及公司技术体系，向CEO星矢（毛文超）汇报。</p>
  <p>柯南本科毕业于新加坡南洋理工大学计算机工程专业，后于2011年进入美国斯坦福大学商学院攻读MBA。在加入小红书前，她曾任职于波士顿咨询集团、花旗等机构，主要从事咨询与金融相关工作。其职业路径与创始人毛文超相似，后者同样于2011年进入斯坦福商学院。而小红书三号位员工，现任首席产品官、社区业务负责人的樱木（邓超），则出身建筑专业。</p>
  <p><strong>从管理层背景来看，小红书的核心决策层并不以技术见长。此次由柯南整合公司技术体系的任命，也被外界视为小红书在 AI 战略上，更偏向从产品层面寻求创新，而非强调技术上的突破。</strong></p>
  <p><strong>据 36 氪了解，除了社区内置的 AI 助手，和主攻底层研发的 Dots 外，小红书内部还分布着一些更隐秘的 AI 创新项目组，负责产品层面的探索。这些团队属于保密项目，不在公开架构中，彼此之间也互不知情。其中有项目已孵化出产品，但对外宣传时，刻意隐去了“小红书”的身份。</strong></p>
  <p>据前述已经离职的小红书AI员工透露，小红书未必期望自己能在AI时代构建多么宏大的叙事，而是更务实地指向具体场景——比如在旅游、时尚等垂直领域，打造出能解决用户需求、能够占领细分心智的产品。</p>
  <p>小红书的确拥有难以复制的资产——一个高度活跃的社区，和一群贴近真实生活的用户。这里曾孕育出露营、飞盘等席卷年轻人的生活方式。相较技术上的追赶，这些源自一线的洞察，或许有望成为它在新一轮AI竞赛中找到差异化竞争的机会。</p>
  <p>在既有的社区叙事之外，AI时代，小红书还需要一个新的故事来证明自己。</p>
  <p>（应采访对象要求，李舒为化名）</p>

- **技术标签**: `agent` `chatgpt` `claude` `deepseek` `gpt`


---


## 150. 牧原股份在横琴成立现代农牧科技公司，注册资本5亿

- **来源**: [36kr](https://36kr.com/newsflashes/3801450279083783?f=rss)

- **摘要**: 36氪获悉，天眼查App显示，近日，广东横琴牧原现代农牧科技有限公司成立，法定代表人为张亭，注册资本5亿人民币，经营范围包括人工智能基础软件开发、人工智能应用软件开发、智能机器人的研发、人工智能行业应用系统集成服务等，由牧原股份全资持股。


---


## 151. “北辰航天”完成数千万元天使轮融资

- **来源**: [36kr](https://36kr.com/newsflashes/3801443958496773?f=rss)

- **摘要**: 36氪获悉，“北辰航天”近日完成数千万元天使轮融资，由云启资本独家投资，翊荣资本担任长期独家财务顾问。此次融资完成后，北辰航天将进一步扩充产能，建设约2000平方米研发与生产场地，并完善相关设备配置。


---


## 152. “星识科技”连续完成天使+轮和天使++轮融资，累计金额达数千万元

- **来源**: [36kr](https://36kr.com/newsflashes/3801420917071366?f=rss)

- **摘要**: 36氪获悉，“星识科技”近日连续完成天使+轮和天使++轮融资，累计金额达数千万元。两轮融资分别由高秉强教授旗下高锋耐心资本和蓝驰创投领投、松禾资本跟投，老股东清水湾二期基金及奇绩创坛持续加注。本轮资金将主要用于智能影像核心技术研发、新品矩阵打造和产品体验的迭代优化，以及生产体系与供应链能力建设。


---


## 153. Anthropic据悉同Akamai签署18亿美元计算协议

- **来源**: [36kr](https://36kr.com/newsflashes/3801405713374981?f=rss)

- **摘要**: 据报道，Anthropic已同云服务提供商Akamai Technologies签署一项18亿美元的计算交易，以满足对其人工智能软件的激增需求。Akamai表示，已与一家“领先的前沿模型提供商”达成一项为期七年的云计算协议，但未点名该公司。（新浪财经）

- **技术标签**: `anthropic`


---


## 154. 谷歌旗下Isomorphic Labs拟在新一轮融资中筹集逾20亿美元

- **来源**: [36kr](https://36kr.com/newsflashes/3801377962090247?f=rss)

- **摘要**: 据报道，谷歌DeepMind分拆出来的AI驱动药物研发公司Isomorphic Labs正深入洽谈，计划在新一轮融资中筹集超过20亿美元。知情人士称，曾主导Isomorphic Labs去年首轮融资的风投机构Thrive Capital将牵头本轮新融资，Alphabet也将参与。（界面）

- **技术标签**: `deepmind`


---


## 155. 阿波罗和黑石等机构考虑参与博通近350亿美元融资

- **来源**: [36kr](https://36kr.com/newsflashes/3801359034113538?f=rss)

- **摘要**: 据报道， 阿波罗全球管理公司和黑石集团都在参与同博通洽谈约350亿美元融资的私募信贷贷款机构之列。据悉，这笔融资将帮助博通为人工智能任务芯片的开发提供资金。知情人士称，洽谈仍在进行，条款可能发生变化。（界面）


---


## 156. 英特尔与苹果据悉达成初步协议，将为后者设备制造芯片

- **来源**: [36kr](https://36kr.com/newsflashes/3801360095289088?f=rss)

- **摘要**: 据报道，英特尔已与苹果达成初步协议，将为后者设备制造部分芯片。据悉，两家公司已谈判一年多，目前仍不清楚英特尔将为哪些苹果产品制造芯片。（界面）


---


## 157. 亚马逊北弗吉尼亚数据中心云服务中断问题已基本解决

- **来源**: [36kr](https://36kr.com/newsflashes/3800643618249730?f=rss)

- **摘要**: 5月8日，据报道，亚马逊的云服务已基本恢复正常。此前，亚马逊旗下的云计算部门于7日报告称，其位于弗吉尼亚州北部的一个数据中心因过热引发服务中断。其导致包括加密货币交易所Coinbase在内的多家企业受到影响。（界面）


---


## 158. 高盛：美国数据中心用电需求或在两年内翻倍

- **来源**: [36kr](https://36kr.com/newsflashes/3800643284245513?f=rss)

- **摘要**: 高盛预计，美国数据中心电力需求将从2025年的31GW增长至2026年的41GW，并在2027年进一步升至66GW。高盛认为，本轮AI数据中心扩张正在重塑美国地理格局。得州和佐治亚州正成为AI数据中心的重要聚集地，因为这些地区电力供应扩张更快，接入能力更强。（财联社）


---
