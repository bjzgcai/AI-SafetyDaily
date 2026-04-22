# AI Daily Digest [AI 安全] - 2026-04-22


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-04-22
**Author:** Senior AI Safety Researcher

## Highlights

Three academic breakthroughs dominate today's research landscape, signaling a shift from theoretical robustness to practical deployment security. First, the introduction of **Involuntary In-Context Learning** represents a critical vulnerability in current safety alignment paradigms, demonstrating that abstract operator framing can bypass refusal behaviors with near-perfect success rates. Second, **SafetyALFRED** establishes a new standard for evaluating embodied agents, moving beyond static hazard recognition to assess active risk mitigation in dynamic environments. Third, **GAAP** proposes a novel execution environment that guarantees accounting for agent privacy, addressing the fundamental trust deficit in user data access for autonomous assistants. These developments collectively underscore the urgency of securing the agent lifecycle from training data to runtime execution.

## Adversarial Attacks & Robustness

The theoretical understanding of adversarial robustness is being challenged by new attack vectors that exploit the generative nature of modern models. While **Benign Overfitting in Adversarial Training for Vision Transformers** provides the first theoretical analysis of robustness under simplified ViT architectures, showing that signal-to-noise ratio conditions can ensure robustness, this mathematical guarantee does not extend to the prompt-based vulnerabilities recently exposed. The paper **Involuntary In-Context Learning** reveals a class of attacks where few-shot pattern completion overrides safety training, achieving a 100% bypass rate in specific operator framing scenarios. This finding contradicts the assumption that alignment is static; instead, it suggests that safety is a dynamic competition between learned weights and in-context patterns.

This tension between theoretical defense and practical attack is further highlighted in the domain of supply chain security. **Malicious ML Model Detection by Learning Dynamic Behaviors** argues that static analysis tools like PickleScan are insufficient because they ignore runtime model behaviors. By learning dynamic behaviors, this approach aims to detect malicious pre-trained models that execute arbitrary code during loading, a threat vector that complements the **Involuntary In-Context Learning** findings by addressing both the input and the model artifact itself. In the web security domain, **Evaluating LLM-Generated Obfuscated XSS Payloads for Machine Learning-Based Detection** provides a structured pipeline for generating behaviorally valid obfuscated payloads, challenging existing detection systems that rely on syntactic diversity. Together, these works suggest that robustness must be evaluated across the entire stack, from the physical layer of vision transformers to the logical layer of prompt injection and the supply chain of model binaries.

## Model Alignment & Interpretability

As agents transition from static generators to dynamic workflows, alignment failures are becoming more nuanced and human-like. **Taming Actor-Observer Asymmetry in Agents via Dialectical Alignment** identifies a specific cognitive bias in multi-agent frameworks where agents acting as actors attribute failures to external factors, while observers attribute them to internal factors. This human-like asymmetry complicates self-reflection mechanisms, suggesting that current role-playing strategies may inadvertently introduce systemic bias rather than mitigate it. To address bias more formally, **Counting Worlds Branching Time Semantics for post-hoc Bias Mitigation in generative AI** introduces CTLF, a branching-time logic that reasons about bias in output series. Unlike empirical inference-time strategies, CTLF offers formal guarantees by verifying whether output series respect intended probability distributions over possible worlds.

The complexity of alignment extends to enterprise governance, where **Four-Axis Decision Alignment for Long-Horizon Enterprise AI Agents** proposes decomposing decision behavior into four orthogonal axes: factual precision, reasoning coherence, compliance, and operational safety. This framework contrasts with single-task-success scalars that conflate failure modes, offering a more granular audit trail for high-stakes decisions like loan underwriting. Complementing these alignment theories, **PREF-XAI: Preference-Based Personalized Rule Explanations of Black-Box Machine Learning Models** shifts the focus from model-centric explanations to user-centric ones. By learning individual preferences rather than relying on heuristic adaptations, PREF-XAI addresses the interpretability gap where different users require different explanations based on their cognitive constraints. These works collectively argue that alignment is not a monolithic property but a multi-dimensional construct requiring formal logic, behavioral decomposition, and personalized interpretability.

## Privacy Protection & Federated Learning

Privacy-preserving computation remains a bottleneck for collaborative intelligence, particularly in vertical federated learning where entity alignment is required without data centralization. **Sherpa.ai Privacy-Preserving Multi-Party Entity Alignment without Intersection Disclosure for Noisy Identifiers** addresses the prerequisite for Vertical FL by establishing a common index without revealing shared samples, overcoming the limitations of conventional private set intersection. This training-time privacy is complemented by runtime protections in **An AI Agent Execution Environment to Safeguard User Data**, which presents GAAP to guarantee accounting for agent privacy. While Sherpa.ai focuses on the model training phase, GAAP secures the execution environment against prompt injection and data exfiltration, creating a defense-in-depth strategy for privacy.

The utility of privacy-preserving methods is often tested against data quality and heterogeneity. **A Dual Perspective on Synthetic Trajectory Generators: Utility Framework and Privacy Vulnerabilities** examines the trade-off between utility and privacy in human mobility data, noting that generative models often fail to adequately protect sensitive attributes like religious beliefs despite obfuscation techniques. In the context of Personalized Federated Learning, **FB-NLL: A Feature-Based Approach to Tackle Noisy Labels in Personalized Federated Learning** proposes a feature-centric framework to decouple learning dynamics from noisy labels, preventing corrupted updates from distorting clustering decisions. Furthermore, **Heterogeneity-Aware Personalized Federated Learning for Industrial Predictive Analytics** accommodates clients with heterogeneous degradation processes, ensuring that privacy-preserving collaboration does not compromise model accuracy in industrial settings. These contributions highlight that privacy mechanisms must be robust to data noise and heterogeneity to be viable in real-world deployments.

## Safety Benchmarks & Governance

Evaluating safety requires moving beyond static question-answering to dynamic, embodied interaction. **SafetyALFRED: Evaluating Safety-Conscious Planning of Multimodal Large Language Models** augments the ALFRED benchmark with six categories of real-world kitchen hazards, evaluating models on active risk mitigation rather than just recognition. This approach is mirrored in the cybersecurity domain by **Do Agents Dream of Root Shells? Partial-Credit Evaluation of LLM Agents in Capture The Flag Challenges**, which introduces DeepRed, an open-source benchmark for evaluating LLM agents in realistic offensive settings. While SafetyALFRED focuses on defensive safety in physical environments, DeepRed assesses offensive capabilities, providing a comprehensive view of agent security.

Fairness auditing also requires more sophisticated tools to handle continuous covariates. **FairTree: Subgroup Fairness Auditing of Machine Learning Models with Bias-Variance Decomposition** adapts psychometric invariance testing to directly handle continuous, categorical, and ordinal features, overcoming the conceptual disadvantages of tools like SliceFinder. This is critical for **Fairness Audits of Institutional Risk Models in Deployed ML Pipelines**, which evaluates disparities across the full pipeline including training data and post-processing. The governance implications are further explored in **We are currently clean on OPSEC**, which analyzes the 2025 Signalgate leak to demonstrate that encryption alone cannot prevent leaks due to power imbalances and socio-technical factors. These benchmarks and audits suggest that safety and fairness must be measured continuously across the deployment lifecycle, not just at the model output stage.

## Open Source Ecosystem & Tooling

The open-source community is rapidly providing frameworks to operationalize these safety and alignment concepts. **VLA Foundry** unifies LLM, VLM, and VLA training in a single codebase, providing end-to-end control from language pretraining to action-expert fine-tuning, which is essential for reproducible safety research. For agent security, **AutoProber** offers a hardware hacker’s flying probe automation stack for agent-driven target discovery and safety-monitored motion, bridging the gap between software agents and physical hardware safety. Additionally, **Agents-MD** provides a drop-in configuration that forces verification loops and kills sycophancy, synthesizing engineering principles to make coding agents behave like senior engineers. These tools, alongside **AtomCode**, an open-source alternative to Claude Code built in Rust for speed and autonomy, form a critical infrastructure for testing and deploying safer AI systems.

## Looking Forward

Despite significant progress, several theoretical questions remain unresolved. The **Involuntary In-Context Learning** attack raises the question of whether safety alignment can ever be robust against sufficiently strong in-context patterns, or if it requires architectural changes to the model's attention mechanisms. Similarly, the **Lyapunov-Certified Direct Switching Theory for Q-Learning** provides stability guarantees for constant-stepsize Q-learning, but it remains to be seen if these guarantees hold in non-stationary environments where system dynamics change unexpectedly, as noted in **Safe Continual Reinforcement Learning in Non-stationary Environments**. Finally, the privacy-utility trade-off in **Synthetic Trajectory Generators** suggests that current generative methods may not fully eliminate privacy risks without sacrificing utility, pointing to a need for new cryptographic primitives that can support high-utility data sharing without intersection disclosure. Future research must address these gaps to ensure that AI systems are not only capable but also safe, private, and aligned with human values.

---


## References

- **A Dual Perspective on Synthetic Trajectory Generators: Utility Framework and Privacy Vulnerabilities** — [arxiv_ai](https://arxiv.org/abs/2604.19653v1)
- **Taming Actor-Observer Asymmetry in Agents via Dialectical Alignment** — [arxiv_ai](https://arxiv.org/abs/2604.19548v1)
- **Sherpa.ai Privacy-Preserving Multi-Party Entity Alignment without Intersection Disclosure for Noisy Identifiers** — [arxiv_cr](https://arxiv.org/abs/2604.19219v1)
- **UniT: Toward a Unified Physical Language for Human-to-Humanoid Policy Learning and World Modeling** — [arxiv_ai](https://arxiv.org/abs/2604.19734v1)
- **Benign Overfitting in Adversarial Training for Vision Transformers** — [arxiv_ai](https://arxiv.org/abs/2604.19724v1)
- **An AI Agent Execution Environment to Safeguard User Data** — [arxiv_ai](https://arxiv.org/abs/2604.19657v1)
- **SafetyALFRED: Evaluating Safety-Conscious Planning of Multimodal Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.19638v1)
- **Counting Worlds Branching Time Semantics for post-hoc Bias Mitigation in generative AI** — [arxiv_ai](https://arxiv.org/abs/2604.19431v1)
- **FB-NLL: A Feature-Based Approach to Tackle Noisy Labels in Personalized Federated Learning** — [arxiv_lg](https://arxiv.org/abs/2604.19729v1)
- **PREF-XAI: Preference-Based Personalized Rule Explanations of Black-Box Machine Learning Models** — [arxiv_lg](https://arxiv.org/abs/2604.19684v1)
- **ZC-Swish: Stabilizing Deep BN-Free Networks for Edge and Micro-Batch Applications** — [arxiv_lg](https://arxiv.org/abs/2604.19453v1)
- **Heterogeneity-Aware Personalized Federated Learning for Industrial Predictive Analytics** — [arxiv_lg](https://arxiv.org/abs/2604.19451v1)
- **FairTree: Subgroup Fairness Auditing of Machine Learning Models with Bias-Variance Decomposition** — [arxiv_lg](https://arxiv.org/abs/2604.19357v1)
- **FedSEA: Achieving Benefit of Parallelization in Federated Online Learning** — [arxiv_lg](https://arxiv.org/abs/2604.19336v1)
- **FASTER: Value-Guided Sampling for Fast RL** — [arxiv_ai](https://arxiv.org/abs/2604.19730v1)
- **VLA Foundry: A Unified Framework for Training Vision-Language-Action Models** — [arxiv_ai](https://arxiv.org/abs/2604.19728v1)
- **A-MAR: Agent-based Multimodal Art Retrieval for Fine-Grained Artwork Understanding** — [arxiv_ai](https://arxiv.org/abs/2604.19689v1)
- **Learning Hybrid-Control Policies for High-Precision In-Contact Manipulation Under Uncertainty** — [arxiv_ai](https://arxiv.org/abs/2604.19677v1)
- **Lyapunov-Certified Direct Switching Theory for Q-Learning** — [arxiv_ai](https://arxiv.org/abs/2604.19569v1)
- **Multi-modal Reasoning with LLMs for Visual Semantic Arithmetic** — [arxiv_ai](https://arxiv.org/abs/2604.19567v1)
- **Detecting Data Contamination in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.19561v1)
- **DT2IT-MRM: Debiased Preference Construction and Iterative Training for Multimodal Reward Modeling** — [arxiv_ai](https://arxiv.org/abs/2604.19544v1)
- **EVPO: Explained Variance Policy Optimization for Adaptive Critic Utilization in LLM Post-Training** — [arxiv_ai](https://arxiv.org/abs/2604.19485v1)
- **Fairness Audits of Institutional Risk Models in Deployed ML Pipelines** — [arxiv_ai](https://arxiv.org/abs/2604.19468v1)
- **LePREC: Reasoning as Classification over Structured Factors for Assessing Relevance of Legal Issues** — [arxiv_ai](https://arxiv.org/abs/2604.19464v1)
- **Four-Axis Decision Alignment for Long-Horizon Enterprise AI Agents** — [arxiv_ai](https://arxiv.org/abs/2604.19457v1)
- **GOLD-BEV: GrOund and aeriaL Data for Dense Semantic BEV Mapping of Dynamic Scenes** — [arxiv_ai](https://arxiv.org/abs/2604.19411v1)
- **Involuntary In-Context Learning: Exploiting Few-Shot Pattern Completion to Bypass Safety Alignment in GPT-5.4** — [arxiv_cr](https://arxiv.org/abs/2604.19461v1)
- **Secure Storage and Privacy-Preserving Scanpath Comparison via Garbled Circuits in Eye Tracking** — [arxiv_cr](https://arxiv.org/abs/2604.19422v1)
- **On two ways to use determinantal point processes for Monte Carlo integration** — [arxiv_lg](https://arxiv.org/abs/2604.19698v1)
- **From Top-1 to Top-K: A Reproducibility Study and Benchmarking of Counterfactual Explanations for Recommender Systems** — [arxiv_lg](https://arxiv.org/abs/2604.19663v1)
- **Disentangling Damage from Operational Variability: A Label-Free Self-Supervised Representation Learning Framework for Output-Only Structural Damage Identification** — [arxiv_lg](https://arxiv.org/abs/2604.19658v1)
- **Evaluating LLM-Generated Obfuscated XSS Payloads for Machine Learning-Based Detection** — [arxiv_lg](https://arxiv.org/abs/2604.19526v1)
- **Accelerating Optimization and Machine Learning through Decentralization** — [arxiv_lg](https://arxiv.org/abs/2604.19518v1)
- **CAST: Modeling Semantic-Level Transitions for Complementary-Aware Sequential Recommendation** — [arxiv_lg](https://arxiv.org/abs/2604.19414v1)
- **Optimal Routing for Federated Learning over Dynamic Satellite Networks: Tractable or Not?** — [arxiv_lg](https://arxiv.org/abs/2604.19399v1)
- **TACENR: Task-Agnostic Contrastive Explanations for Node Representations** — [arxiv_lg](https://arxiv.org/abs/2604.19372v1)
- **LASER: Learning Active Sensing for Continuum Field Reconstruction** — [arxiv_lg](https://arxiv.org/abs/2604.19355v1)
- **Concept Inconsistency in Dermoscopic Concept Bottleneck Models: A Rough-Set Analysis of the Derm7pt Dataset** — [arxiv_lg](https://arxiv.org/abs/2604.19323v1)
- **"We are currently clean on OPSEC": Why JD Can't Encrypt** — [arxiv_cr](https://arxiv.org/abs/2604.19711v1)
- **Adding Compilation Metadata To Binaries To Make Disassembly Decidable** — [arxiv_cr](https://arxiv.org/abs/2604.19628v1)
- **Cyclic Equalizability Characterized by Parikh Vectors** — [arxiv_cr](https://arxiv.org/abs/2604.19504v1)
- **EvoPatch-IoT: Evolution-Aware Cross-Architecture Vulnerability Retrieval and Patch-State Profiling for BusyBox-Based IoT Firmware** — [arxiv_cr](https://arxiv.org/abs/2604.19496v1)
- **API Security Based on Automatic OpenAPI Mapping** — [arxiv_cr](https://arxiv.org/abs/2604.19471v1)
- **Malicious ML Model Detection by Learning Dynamic Behaviors** — [arxiv_cr](https://arxiv.org/abs/2604.19438v1)
- **Do Agents Dream of Root Shells? Partial-Credit Evaluation of LLM Agents in Capture The Flag Challenges** — [arxiv_cr](https://arxiv.org/abs/2604.19354v1)
- **Phase Transitions in the Fluctuations of Functionals of Random Neural Networks** — [arxiv_lg](https://arxiv.org/abs/2604.19738v1)
- **Safe Continual Reinforcement Learning in Non-stationary Environments** — [arxiv_lg](https://arxiv.org/abs/2604.19737v1)
- **Ultrametric OGP - parametric RDT \emph{symmetric} binary perceptron connection** — [arxiv_lg](https://arxiv.org/abs/2604.19712v1)
- **Planning in entropy-regularized Markov decision processes and games** — [arxiv_lg](https://arxiv.org/abs/2604.19695v1)
- **SpaceX is working with Cursor and has an option to buy the startup for $60B** — [techcrunch_ai](https://techcrunch.com/2026/04/21/spacex-is-working-with-cursor-and-has-an-option-to-buy-the-startup-for-60-billion/)
- **SpaceX cuts a deal to maybe buy Cursor for $60 billion** — [theverge_ai](https://www.theverge.com/science/916427/spacex-cursor-potential-deal-acquisition)
- **Sam Altman throws shade at Anthropic’s cyber model, Mythos: ‘fear-based marketing’** — [techcrunch_ai](https://techcrunch.com/2026/04/21/sam-altman-throws-shade-at-anthropics-cyber-model-mythos-fear-based-marketing/)
- **Clarifai deletes 3 million photos that OkCupid provided to train facial recognition AI, report says** — [techcrunch_ai](https://techcrunch.com/2026/04/21/clarifai-okcupid-facial-recognition-ai-ftc-settlement/)
- **AI backlash is coming for elections** — [theverge_ai](https://www.theverge.com/policy/916210/ai-midterm-elections-data-centers-jobs)
- **OpenAI’s updated image generator can now pull information from the web** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/916166/openai-chatgpt-images-2)
- **Framework’s first eGPUs turn its laptop into a desktop PC** — [theverge_ai](https://www.theverge.com/gadgets/915328/framework-oculink-egpu-dev-kit-laptop-16)
- **Celebrities will be able to find and request removal of AI deepfakes on YouTube** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/915872/celebrities-will-be-able-to-find-and-request-removal-of-ai-deepfakes-on-youtube)
- **Bond, a new social media platform, wants to use AI to help you kick your doomscrolling habit** — [techcrunch_ai](https://techcrunch.com/2026/04/21/bond-social-media-platform-ai-memories-kick-doomscrolling-habit/)
- **Ordering with the Starbucks ChatGPT app was a true coffee nightmare** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/915821/starbucks-chatgpt-app-testing)
- **John Ternus’ first big problem is AI** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/915662/john-ternus-apple-ceo-tim-cook-ai-problem-siri)
- **Yelp is making its AI chatbot way more useful** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/915626/yelp-ai-assistant-chatbot-major-upgrade)
- **Meta will record employees’ keystrokes and use it to train its AI models** — [techcrunch_ai](https://techcrunch.com/2026/04/21/meta-will-record-employees-keystrokes-and-use-it-to-train-its-ai-models/)
- **Unauthorized group has gained access to Anthropic’s exclusive cyber tool Mythos, report claims** — [techcrunch_ai](https://techcrunch.com/2026/04/21/unauthorized-group-has-gained-access-to-anthropics-exclusive-cyber-tool-mythos-report-claims/)
- **Apple’s John Ternus will run one of the world’s most powerful companies; the job is a minefield** — [techcrunch_ai](https://techcrunch.com/2026/04/21/apples-john-ternus-will-run-one-of-the-worlds-most-powerful-companies-the-job-is-a-minefield/)
- **AI research lab NeoCognition lands $40M seed to build agents that learn like humans** — [techcrunch_ai](https://techcrunch.com/2026/04/21/ai-research-lab-neocognition-lands-40m-seed-to-build-agents-that-learn-like-humans/)
- **ChatGPT’s new Images 2.0 model is surprisingly good at generating text** — [techcrunch_ai](https://techcrunch.com/2026/04/21/chatgpts-new-images-2-0-model-is-surprisingly-good-at-generating-text/)
- **AI Dungeon maker Latitude unveils Voyage, a platform for creating AI-powered RPGs** — [techcrunch_ai](https://techcrunch.com/2026/04/21/voyage-is-an-ai-rpg-platform-for-creating-custom-gaming-worlds-with-ai-generated-npc-interactions/)
- **YouTube expands its AI likeness detection technology to celebrities** — [techcrunch_ai](https://techcrunch.com/2026/04/21/youtube-expands-its-ai-likeness-detection-technology-to-celebrities/)
- **3 new ways Ads Advisor is making Google Ads safer and faster** — [google_ai](https://blog.google/products/ads-commerce/ads-advisor-google-ads/)
- **GRAI believes AI can make music more social, not replace artists** — [techcrunch_ai](https://techcrunch.com/2026/04/21/grai-believes-ai-can-make-music-more-social-not-replace-artists/)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **AMAP-ML/DCW** — [github](https://github.com/AMAP-ML/DCW)
- **Tencent-Hunyuan/HY-SOAR** — [github](https://github.com/Tencent-Hunyuan/HY-SOAR)
- **atomgit-atomcode/atomcode** — [github](https://github.com/atomgit-atomcode/atomcode)
- **dsd2077/CyberVerse** — [github](https://github.com/dsd2077/CyberVerse)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **yzhao062/anywhere-agents** — [github](https://github.com/yzhao062/anywhere-agents)
- **intertwine/dspy-agent-skills** — [github](https://github.com/intertwine/dspy-agent-skills)
- **GainSec/AutoProber** — [github](https://github.com/GainSec/AutoProber)
- **TheRealSeanDonahoe/agents-md** — [github](https://github.com/TheRealSeanDonahoe/agents-md)
- **alchaincyf/huashu-design** — [github](https://github.com/alchaincyf/huashu-design)
- **蚂蚁百灵Ling-2.6-flash正式发布，定价每百万token 0.1美元** — [36kr](https://36kr.com/newsflashes/3777678069044231?f=rss)
- **张雪机车发布召回通告** — [36kr](https://36kr.com/newsflashes/3777674880210179?f=rss)
- **出门问问发布AI原生协作平台CodeBanana** — [36kr](https://36kr.com/newsflashes/3777668420687105?f=rss)
- **Meta拟追踪美员工点击及击键数据训练AI，官方称数据不用于绩效评估** — [36kr](https://36kr.com/newsflashes/3777653966411010?f=rss)
- **36氪研究院 | 2026年中国银发经济产业研究报告** — [36kr](https://36kr.com/p/3777435336807172?f=rss)
- **宝洁公司已成功注册WHITELOCK商标** — [36kr](https://36kr.com/newsflashes/3777608395592704?f=rss)
- **具微科技两个月狂揽4轮数亿元融资，产业资本“天团”强势入局 | 36氪首发** — [36kr](https://36kr.com/p/3777491215913736?f=rss)
- **“清听声学”完成B+轮数亿元融资** — [36kr](https://36kr.com/newsflashes/3777574458316034?f=rss)
- **押注AAV体内CAR-T，「西湖云谷智药」即将启动IIT研究** — [36kr](https://36kr.com/p/3774632804057607?f=rss)
- **8点1氪丨MCN机构回应女孩挪用上千万打赏主播；苹果更换CEO原因曝光；国内油价2026年首次下调** — [36kr](https://36kr.com/p/3777227930224900?f=rss)
- **智界要打翻盘仗：V9给了年均12万辆指引｜36氪独家** — [36kr](https://36kr.com/p/3776741071571200?f=rss)
- **氪星晚报｜星巴克中国回应开放加盟传闻：不实信息；苹果公司宣布特纳斯将接替库克担任CEO** — [36kr](https://36kr.com/p/3776458805904129?f=rss)
- **PettiChat获百万美元种子投资，造出宠物穿戴AI翻译器** — [36kr](https://36kr.com/p/3769659305427459?f=rss)
- **g2i-ai/agents** — [github](https://github.com/g2i-ai/agents)
- **dezgit2025/auto-memory** — [github](https://github.com/dezgit2025/auto-memory)
- **ConardLi/web-design-skill** — [github](https://github.com/ConardLi/web-design-skill)
- **tobyilee/book-writer** — [github](https://github.com/tobyilee/book-writer)
- **geekjourneyx/travel-guidebook** — [github](https://github.com/geekjourneyx/travel-guidebook)
- **catoncat/notion-local-ops-mcp** — [github](https://github.com/catoncat/notion-local-ops-mcp)
- **SparkEngineAI/QuantClaw-plugin** — [github](https://github.com/SparkEngineAI/QuantClaw-plugin)
- **TheRealSeanDonahoe/ijfw** — [github](https://github.com/TheRealSeanDonahoe/ijfw)
- **KarryViber/Orb** — [github](https://github.com/KarryViber/Orb)
- **高铁电气：第一季度净利润1227.21万元，同比增长150.92%** — [36kr](https://36kr.com/newsflashes/3777689032004617?f=rss)
- **秋田微：暂未涉及印制电路板（PCB）产品领域** — [36kr](https://36kr.com/newsflashes/3777687486075905?f=rss)
- **“中科天塔”完成近亿元A+轮融资** — [36kr](https://36kr.com/newsflashes/3777657967580166?f=rss)
- **A股三大指数集体收涨，CPO概念领涨** — [36kr](https://36kr.com/newsflashes/3777646904775683?f=rss)
- **机构：千问AI眼镜线上市场份额达53%，持续位居市场第一** — [36kr](https://36kr.com/newsflashes/3777626884805634?f=rss)
- **农业农村部：今日全国农产品批发市场猪肉平均价格为14.68元/公斤，比昨天下降0.7%** — [36kr](https://36kr.com/newsflashes/3777619190551808?f=rss)
- **韩国预计到2040年用电量将增长近30%** — [36kr](https://36kr.com/newsflashes/3777596020003844?f=rss)
- **前小鹏汽车自动驾驶一号位李力耘出任众擎CTO，加速打造具身大脑** — [qbitai](https://www.qbitai.com/2026/04/404124.html)
- **国产多模态Agent拿下医学分割SOTA！不用改模型、不加token** — [qbitai](https://www.qbitai.com/2026/04/404604.html)
- **这些人读个博一年能挣几十万？2026苹果学者名单公布了** — [qbitai](https://www.qbitai.com/2026/04/404481.html)
- **全球首个世界统一模型发布，机器人家庭成员来了！** — [qbitai](https://www.qbitai.com/2026/04/404446.html)
- **从GPU到Token：AI基础设施竞争逻辑重构** — [qbitai](https://www.qbitai.com/2026/04/404440.html)
- **2026萤石品牌新品发布会：驭智向前锚定长期主义，AI驱动多点开花** — [qbitai](https://www.qbitai.com/2026/04/404420.html)
- **6分钟满电续航1500公里！宁王一夜终结加油时代** — [qbitai](https://www.qbitai.com/2026/04/404167.html)
- **单Agent时代结束，AI们开始组团上班** — [qbitai](https://www.qbitai.com/2026/04/404130.html)
- **5月20日，马上AI起来！中国AIGC产业峰会报名已启动｜首波嘉宾官宣** — [qbitai](https://www.qbitai.com/2026/04/404096.html)
- **大厂AI抢人大战，从实习生开始** — [qbitai](https://www.qbitai.com/2026/04/404470.html)