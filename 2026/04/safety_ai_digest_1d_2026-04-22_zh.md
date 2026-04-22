# AI 日报 [AI 安全] - 2026-04-22


# AI 安全与治理每日综述
**日期：** 2026-04-22  
**主题：** AI 安全、对齐、隐私与治理

## Highlights

今日学术界的突破主要集中在对抗攻击的新范式、联邦学习中的隐私实体对齐以及具身智能的安全评估基准上。最引人注目的安全进展是 **Involuntary In-Context Learning: Exploiting Few-Shot Pattern Completion to Bypass Safety Alignment in GPT-5.4**，该研究揭示了一种名为“非自愿上下文学习”（IICL）的新型攻击，利用抽象算子框架和少样本模式完成，能够以 100% 的通过率绕过大型语言模型的安全对齐，这对现有的防御策略构成了严峻挑战。在隐私计算领域，**Sherpa.ai Privacy-Preserving Multi-Party Entity Alignment without Intersection Disclosure for Noisy Identifiers** 提出了无需泄露交集信息的隐私保护实体对齐方法，解决了垂直联邦学习（VFL）中样本索引对齐的隐私瓶颈。此外，**SafetyALFRED: Evaluating Safety-Conscious Planning of Multimodal Large Language Models** 发布了首个针对多模态大模型在具身环境中主动风险缓解能力的评估基准，填补了从静态问答到动态安全规划的评估空白。产业方面，Meta 计划追踪员工击键数据以训练 AI 模型的举措 [86] 再次引发了关于内部数据隐私边界的讨论，而 SpaceX 与 Cursor 的潜在收购案 [51] 则反映了大模型在代码生成领域的竞争加剧。

## 对抗攻击与鲁棒性

随着大模型在关键基础设施中的应用加深，对抗攻击的形态正从传统的提示注入向更隐蔽的上下文操纵演变。**Involuntary In-Context Learning: Exploiting Few-Shot Pattern Completion to Bypass Safety Alignment in GPT-5.4** 的研究指出，现有的安全对齐依赖于行为训练，但在足够强的上下文模式竞争下，这些防御会被覆盖。该工作通过七项消融实验证明了语义算子命名在绕过安全拒绝行为中的有效性，这提示我们单纯依赖训练时的安全指令可能不足以应对推理阶段的模式攻击。与此形成对比的是，针对视觉 Transformer 的鲁棒性研究 **Benign Overfitting in Adversarial Training for Vision Transformers** 提供了理论层面的防御视角。该论文首次分析了简化 ViT 架构下对抗训练的理论基础，表明在满足特定信噪比条件下，对抗训练能够带来良性过拟合，从而提升模型对对抗样本的鲁棒性。

在供应链安全方面，**Malicious ML Model Detection by Learning Dynamic Behaviors** 和 **Evaluating LLM-Generated Obfuscated XSS Payloads for Machine Learning-Based Detection** 分别关注了模型加载时的恶意代码执行和 Web 安全中的混淆攻击。前者指出基于静态分析的传统检测器（如 PickleScan）忽略了运行时行为，导致漏报或误报，主张通过动态行为学习来检测恶意预训练模型。后者则构建了一个结构化流程，评估基于 LLM 生成的混淆 XSS 载荷，发现现有方法往往强调语法多样性而忽视了行为有效性。这些工作共同揭示了一个趋势：攻击者正在利用模型生成能力制造更隐蔽的威胁，而防御方需要从静态规则转向动态行为分析和理论鲁棒性验证。

## 模型对齐与可解释性

多智能体系统的兴起带来了新的对齐挑战，**Taming Actor-Observer Asymmetry in Agents via Dialectical Alignment** 深入探讨了多智能体框架中的人类认知偏差问题。研究发现，当智能体扮演特定角色进行自我反思和相互审计时，会诱发“行动者 - 观察者不对称性”（AOA），即智能体倾向于将失败归咎于外部因素。该工作提出了一种辩证对齐方法，通过角色互换和对话机制来缓解这种偏差，这对于提升多智能体系统的可靠性至关重要。在强化学习后训练阶段，**EVPO: Explained Variance Policy Optimization for Adaptive Critic Utilization in LLM Post-Training** 重新审视了 Critic 的作用。与经典理论认为 Critic 能降低方差不同，该研究在稀疏奖励场景下发现，学习的 Critic 可能引入超出状态信号的估计噪声。作者将基线选择建模为卡尔曼滤波问题，提出了自适应 Critic 利用策略，为 RLHF 中的策略优化提供了新的理论依据。

可解释性方面，**PREF-XAI: Preference-Based Personalized Rule Explanations of Black-Box Machine Learning Models** 指出当前的 XAI 方法往往忽视用户的个性化需求。该工作提出了一种基于偏好的个性化规则解释框架，不再依赖启发式适配，而是通过原则性框架学习个体偏好。这与 **A-MAR: Agent-based Multimodal Art Retrieval for Fine-Grained Artwork Understanding** 中的显式推理计划形成呼应，后者通过结构化推理计划分解任务，将检索显式地基于推理目标，而非依赖模型的隐式知识。这些工作共同指向一个方向：未来的对齐与解释系统不应是通用的，而应适应特定的认知偏差、奖励结构及用户偏好。

## 隐私保护与联邦学习

隐私保护在数据共享与模型协作中始终是关键议题。**A Dual Perspective on Synthetic Trajectory Generators: Utility Framework and Privacy Vulnerabilities** 探讨了利用生成模型合成人类移动数据的隐私 - 效用权衡。尽管生成模型能降低传统聚合或噪声添加带来的效用损失，但该研究揭示了合成数据仍存在隐私漏洞，强调了在公共健康等敏感场景下需谨慎评估生成模型的隐私风险。在联邦学习领域，**Sherpa.ai Privacy-Preserving Multi-Party Entity Alignment without Intersection Disclosure for Noisy Identifiers** 解决了垂直联邦学习中样本对齐的隐私难题。传统的私有集合交集（PSI）方法往往泄露共享样本信息，而该方法通过无需交集披露的实体对齐，允许各方在不暴露具体样本索引的情况下建立共同索引。

针对联邦学习中的噪声与异构性问题，**FB-NLL: A Feature-Based Approach to Tackle Noisy Labels in Personalized Federated Learning** 和 **Heterogeneity-Aware Personalized Federated Learning for Industrial Predictive Analytics** 提供了互补的解决方案。前者通过特征中心框架解耦数据质量与聚类决策，解决了低质量数据导致的个性化性能下降；后者则针对工业预测中的异构退化过程，设计了个性化的联邦预后模型。此外，**FedSEA: Achieving Benefit of Parallelization in Federated Online Learning** 扩展了在线联邦学习范式，通过集成随机扩展对手（SEA）模型，在保持隐私的同时实现了并行化的优势。这些研究共同表明，联邦学习正从简单的模型聚合向更复杂的隐私保护、噪声鲁棒性和异构性适应方向发展，以应对真实世界中的复杂数据分布。

## 安全评估基准与治理

随着 AI 代理在关键决策中的应用，评估标准亟需从单一的任务成功率转向多维度的安全对齐。**SafetyALFRED: Evaluating Safety-Conscious Planning of Multimodal Large Language Models** 基于具身智能基准 ALFRED，增加了六类真实厨房危害，评估了多模态大模型在主动风险缓解方面的能力，而非仅仅停留在危害识别上。**Four-Axis Decision Alignment for Long-Horizon Enterprise AI Agents** 则提出将长期企业代理的决策行为分解为四个正交的对齐轴：事实精度、推理连贯性、合规性约束和记忆一致性，旨在解决当前评估指标混淆不同失败模式的问题。

在公平性与审计方面，**FairTree: Subgroup Fairness Auditing of Machine Learning Models with Bias-Variance Decomposition** 引入了基于心理测量不变性测试的算法，能够直接处理连续、分类和序数特征，克服了传统切片审计工具无法直接处理连续协变量的缺陷。**Detecting Data Contamination in Large Language Models** 则通过统一数据集对比了最先进的黑盒成员推断攻击（MIA），旨在可靠地检测训练数据中的版权侵犯或隐私泄露。这些基准和审计工具的出现，标志着 AI 治理正从定性描述转向定量、可复现的标准化评估，为监管机构的合规审查提供了技术依据。

## 开源工具与生态

开源社区在构建安全基础设施方面发挥了重要作用。**atomcode/atomcode** 作为一个开源的 Claude Code 替代品，支持连接任意 LLM 进行代码编辑和命令执行，并内置了 Rust 编写的安全验证循环。**anywhere-agents** 提供了一个统一的配置框架，使 AI 代理能够在不同项目中便携运行，并内置了破坏性命令防护机制。**AutoProber** 则是一个面向硬件黑客的自动化探测栈，集成了安全监控的 CNC 运动和探针检测，用于目标发现和安全评估。此外，**agents-md** 通过标准化的 AGENTS.md 文件，强制代理行为像资深工程师一样进行验证循环，抑制了盲目重构和奉承行为。这些工具不仅提升了开发效率，更通过内置的安全机制（如命令防护、验证循环）为 AI 代理的落地提供了工程层面的保障。

## Looking Forward

尽管今日的研究在对抗防御、隐私保护和评估基准上取得了显著进展，但仍存在若干未解决的理论问题。首先，**Involuntary In-Context Learning** 揭示的上下文攻击表明，现有的安全对齐可能缺乏形式化的鲁棒性保证，未来需要探索基于逻辑验证的推理时防御机制。其次，在联邦学习中，**Sherpa.ai** 和 **FedSEA** 虽然优化了隐私和并行性，但在动态网络（如卫星网络）下的通信效率与隐私保护的平衡仍需进一步理论优化。最后，**SafetyALFRED** 和 **Four-Axis Decision Alignment** 虽然定义了新的评估维度，但如何将多维度的安全指标转化为可量化的奖励函数，以便在强化学习中实现端到端的安全对齐，仍是具身智能领域的一大挑战。未来的研究应致力于建立跨模态、跨任务的安全通用理论，以应对日益复杂的 AI 系统风险。

---


## 参考来源

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