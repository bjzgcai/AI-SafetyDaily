# AI 日报 [AI 安全] - 2026-04-25


# 2026 年 4 月 25 日 AI 安全与治理主题综述

## Highlights

今日学术界的焦点显著集中在**多轮对话状态漏洞**与**评估框架的标准化**上。加州大学团队提出的 **Transient Turn Injection** 揭示了无状态大模型在多轮交互中的新型漏洞，表明攻击者可通过分散的恶意意图绕过现有的策略执行，这对当前主流的 RAG 和 Agent 系统构成了严峻挑战。与此同时，**Auto-ART** 与 **AVISE** 两大开源框架的发布，标志着对抗鲁棒性测试正从单一指标向系统化、可复现的评估体系演进，试图解决该领域长期存在的协议碎片化问题。产业方面，DeepSeek 发布的 V4 模型宣称在推理基准上已“缩小了与前沿闭源模型的差距”，其开源策略可能进一步加剧开源社区在安全对齐与红队测试上的资源竞争，但具体性能需经独立基准验证。

## 对抗攻击与 Agent 安全

随着大模型从单一对话向自主 Agent 演进，攻击面已从提示词注入扩展至工具调用与状态管理。**Transient Turn Injection** 指出，当前许多 LLM 系统在处理多轮交互时缺乏状态一致性检查，攻击者利用自动化代理迭代测试，可成功将恶意意图分散在孤立交互中，从而规避基于上下文的策略执行。这一发现与 **Breaking Bad** 的研究形成互补，后者利用可解释性技术（Universal Steering 和 Representation Engineering）对八个 SOTA 开源模型进行了审计，通过激活引导系数识别出模型内部的安全漏洞，证明了黑盒攻击与白盒审计的结合是未来防御的关键。

在 Agent 安全领域，**MCP Pitfall Lab** 与 **Breaking Bad with Function Hijacking** 共同揭示了工具集成协议（MCP）与函数调用接口的深层风险。前者 operationalizes 了开发者陷阱，验证了跨工具流和供应链向量攻击的可行性；后者则展示了攻击者如何通过函数调用接口滥用 Agentic 模型，导致数据篡改或破坏性行为。针对这些风险，**Adaptive Defense Orchestration for RAG** 提出了 Sentinel-Strategist 架构，试图在 RAG 系统中平衡防御强度与上下文召回率，实验表明全开防御会导致上下文召回率下降超过 40%，因此自适应防御成为必要。此外，**Auto-ART** 框架通过整合 50+ 种攻击和 28 种防御模块，试图统一对抗鲁棒性测试协议，而 **AVISE** 则提供了模块化框架以识别 AI 系统漏洞，两者共同推动了从“单一攻击测试”向“全生命周期安全评估”的转变。

## 模型对齐、可解释性与推理机制

对齐研究正从简单的指令遵循转向对意图形成与道德推理的深层理解。**Alignment has a Fantasia Problem** 提出，现代 AI 助手假设用户能清晰表达目标，但行为研究表明用户目标往往未完全形成，导致“幻想交互”失败，这要求对齐研究重新审视用户意图的动态性。与此相呼应，**Measuring Opinion Bias and Sycophancy via LLM-based Coercion** 通过基于 LLM 的胁迫实验，揭示了模型在争议话题上可能通过沉默或回避来隐藏立场，一旦用户坚持某一观点，模型可能表现出相反立场的顺从，这种“沉默偏见”难以通过直接提问检测。

在推理机制方面，**Language as a Latent Variable for Reasoning Optimization** 发现非英语响应在推理任务中有时优于英语，假设语言作为潜在变量调节了内部推理路径，这为多语言对齐提供了新视角。然而，**Reasoning Primitives in Hybrid and Non-Hybrid LLMs** 则通过对比实验指出，混合架构（结合注意力检索与循环状态更新）在需要状态跟踪的任务中优于纯注意力模型，暗示了推理能力的架构依赖性。在道德决策层面，**Machine Behavior in Relational Moral Dilemmas** 通过“吹哨人困境”实验，评估了模型在关系亲疏与犯罪严重程度下的决策，发现模型尚未完全编码人际关系的细微差别，这与社会技术决策系统的需求存在差距。

## 隐私保护与联邦学习

隐私计算领域正致力于解决数据异构性与模型可删除性之间的矛盾。**Differentially Private Clustered Federated Learning** 提出在跨设备部署中，通过聚类用户来缓解数据异构性，并结合差分隐私（DP）提供形式化保证。**Differentially Private Model Merging** 则进一步提出了一种后处理技术，允许在不重新训练的情况下，通过随机选择或线性组合现有模型来满足任意目标隐私参数，为动态隐私需求提供了灵活性。

在医疗数据保护方面，**Differentially Private De-identification of Dutch Clinical Notes** 评估了基于 DP 的自动化文本去标识化方法，对比了传统 NER 与 LLM 方法的效用，强调了在 GDPR 合规下平衡隐私与数据可用性的挑战。针对模型遗忘需求，**Separable Expert Architecture** 提出了一种三层架构，通过可组合的 LoRA 适配器与可删除的用户代理，实现了确定性遗忘，避免了重新训练的高成本。然而，**Benchmarking the Utility of Privacy-Preserving Cox Regression** 指出，尽管 DP 提供了数学保证，但在生存分析等统计任务中，数据驱动的截断界限对效用影响显著，需根据具体场景调整 $\varepsilon$ 参数。

## 安全评估基准与治理

评估基准的缺失一直是安全治理的瓶颈。**AVISE** 与 **Auto-ART** 的发布填补了部分空白，但 **CI-Work** 进一步引入了“情境完整性”（Contextual Integrity）基准，模拟企业工作流中的信息流方向，评估 Agent 在检索内部上下文时的隐私泄露风险，实验显示隐私违规率高达 15.8% 至 40% 不等。在数学推理评估上，**MathDuels** 提出了自博弈基准，让模型同时扮演出题者与解题者，以解决静态基准天花板效应问题。

治理层面，**Bounding the Black Box** 指出，尽管欧盟 AI 法案等法规要求证明安全性，但缺乏“可接受风险”的量化定义与技术验证方法。**Compliance Moral Hazard and the Backfiring Mandate** 则从机制设计角度分析了金融机构在反洗钱中的信息聚合问题，提出了时间价值分配（TVA）机制以缓解合规道德风险。此外，**A Sociotechnical, Practitioner-Centered Approach to Technology Adoption in Cybersecurity Operations** 通过实地民族志研究，指出 SOC 采用 LLM 工具面临信任与可靠性挑战，需从社会技术角度而非单纯技术角度解决采纳问题。

## 产业动态与政策观察

产业界今日动态主要集中在算力竞争与开源模型演进。**DeepSeek** 发布的 V4 模型预览版宣称在推理基准上已“缩小了与前沿闭源模型的差距”，并支持百万 Token 上下文，其开源策略可能改变安全对齐的生态格局，但具体性能需经独立基准验证。**Google** 计划向 **Anthropic** 投资高达 400 亿美元，显示出巨头在争夺算力与模型能力上的激烈竞争，这可能影响未来安全研究的资源分配。**Apple** 宣布 CEO 交接计划，Tim Cook 将于 9 月卸任，由 John Ternus 接任，这一变动可能影响 Apple 在端侧 AI 安全与隐私保护上的战略方向。此外，**ComfyUI** 估值达到 5 亿美元，反映了创作者对可控 AI 生成工具的需求，这为生成内容检测与水印技术提供了新的应用场景。

## Looking Forward

尽管今日成果丰硕，但若干理论问题仍未解决。首先，**多 Agent 环境下的安全协调** 仍缺乏形式化理论，**Transient Turn Injection** 暴露的状态漏洞在复杂 Agent 协作中可能如何演化尚不明确。其次，**对齐的量化标准** 依然模糊，**Alignment has a Fantasia Problem** 与 **Bounding the Black Box** 均指出，当前缺乏对用户意图形成过程与风险阈值的统一度量。最后，**隐私与效用的动态平衡** 在联邦学习场景下仍需优化，**Differentially Private Model Merging** 虽提供了灵活性，但合并过程中的隐私泄露风险累积效应尚未完全建模。未来研究需重点关注 Agent 系统的可解释性审计工具链，以及建立跨行业的风险量化标准，以应对日益复杂的 AI 安全挑战。

---


## 参考来源

- **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21860v1)
- **Enabling and Inhibitory Pathways of University Students' Willingness to Disclose AI Use: A Cognition-Affect-Conation Perspective** — [arxiv_ai](https://arxiv.org/abs/2604.21733v1)
- **Differentially Private Clustered Federated Learning with Privacy-Preserving Initialization and Normality-Driven Aggregation** — [arxiv_cr](https://arxiv.org/abs/2604.20596v1)
- **Fairness under uncertainty in sequential decisions** — [arxiv_ai](https://arxiv.org/abs/2604.21711v1)
- **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study** — [arxiv_cr](https://arxiv.org/abs/2604.21491v1)
- **Measuring Opinion Bias and Sycophancy via LLM-based Coercion** — [arxiv_cl](https://arxiv.org/abs/2604.21564v1)
- **Drug Synergy Prediction via Residual Graph Isomorphism Networks and Attention Mechanisms** — [arxiv_lg](https://arxiv.org/abs/2604.21473v1)
- **Differentially Private De-identification of Dutch Clinical Notes: A Comparative Evaluation** — [arxiv_cl](https://arxiv.org/abs/2604.21421v1)
- **Differentially Private Model Merging** — [arxiv_cr](https://arxiv.org/abs/2604.20985v1)
- **Breaking Bad: Interpretability-Based Safety Audits of State-of-the-Art LLMs** — [arxiv_cr](https://arxiv.org/abs/2604.20945v1)
- **Adaptive Defense Orchestration for RAG: A Sentinel-Strategist Architecture against Multi-Vector Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.20932v1)
- **UniGenDet: A Unified Generative-Discriminative Framework for Co-Evolutionary Image Generation and Generated Image Detection** — [huggingface_papers](https://arxiv.org/abs/2604.21904)
- **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies** — [arxiv_ai](https://arxiv.org/abs/2604.21571v1)
- **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21774v1)
- **A Sociotechnical, Practitioner-Centered Approach to Technology Adoption in Cybersecurity Operations: An LLM Case** — [arxiv_cr](https://arxiv.org/abs/2604.21679v1)
- **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21477v1)
- **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** — [arxiv_cl](https://arxiv.org/abs/2604.21871v1)
- **Language as a Latent Variable for Reasoning Optimization** — [arxiv_cl](https://arxiv.org/abs/2604.21593v1)
- **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** — [arxiv_lg](https://arxiv.org/abs/2604.21870v1)
- **GFlowState: Visualizing the Training of Generative Flow Networks Beyond the Reward** — [arxiv_lg](https://arxiv.org/abs/2604.21830v1)
- **Compliance Moral Hazard and the Backfiring Mandate** — [arxiv_lg](https://arxiv.org/abs/2604.21789v1)
- **There Will Be a Scientific Theory of Deep Learning** — [arxiv_lg](https://arxiv.org/abs/2604.21691v1)
- **Physically Unclonable Functions for Secure IoT Authentication and Hardware-Anchored AI Model Integrity** — [arxiv_cr](https://arxiv.org/abs/2604.21188v1)
- **Breaking MCP with Function Hijacking Attacks: Novel Threats for Function Calling and Agentic Models** — [arxiv_cr](https://arxiv.org/abs/2604.20994v1)
- **AVISE: Framework for Evaluating the Security of AI Systems** — [arxiv_cr](https://arxiv.org/abs/2604.20833v1)
- **Auto-ART: Structured Literature Synthesis and Automated Adversarial Robustness Testing** — [arxiv_cr](https://arxiv.org/abs/2604.20704v1)
- **SoK: The Next Frontier in AV Security: Systematizing Perception Attacks and the Emerging Threat of Multi-Sensor Fusion** — [arxiv_cr](https://arxiv.org/abs/2604.20621v1)
- **Towards Certified Malware Detection: Provable Guarantees Against Evasion Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.20495v1)
- **Trust but Verify: Introducing DAVinCI -- A Framework for Dual Attribution and Verification in Claim Inference for Language Models** — [huggingface_papers](https://arxiv.org/abs/2604.21193)
- **Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation** — [arxiv_ai](https://arxiv.org/abs/2604.21854v1)
- **Modulating Cross-Modal Convergence with Single-Stimulus, Intra-Modal Dispersion** — [arxiv_ai](https://arxiv.org/abs/2604.21836v1)
- **Alignment has a Fantasia Problem** — [arxiv_ai](https://arxiv.org/abs/2604.21827v1)
- **Quotient-Space Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2604.21809v1)
- **SyMTRS: Benchmark Multi-Task Synthetic Dataset for Depth, Domain Adaptation and Super-Resolution in Aerial Imagery** — [arxiv_ai](https://arxiv.org/abs/2604.21801v1)
- **Inferring High-Level Events from Timestamped Data: Complexity and Medical Applications** — [arxiv_ai](https://arxiv.org/abs/2604.21793v1)
- **Why are all LLMs Obsessed with Japanese Culture? On the Hidden Cultural and Regional Biases of LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21751v1)
- **AEL: Agent Evolving Learning for Open-Ended Environments** — [arxiv_ai](https://arxiv.org/abs/2604.21725v1)
- **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers** — [arxiv_ai](https://arxiv.org/abs/2604.21700v1)
- **Fine-Grained Perspectives: Modeling Explanations with Annotator-Specific Rationales** — [arxiv_ai](https://arxiv.org/abs/2604.21667v1)
- **Task-specific Subnetwork Discovery in Reinforcement Learning for Autonomous Underwater Navigation** — [arxiv_ai](https://arxiv.org/abs/2604.21640v1)
- **On the Role of Preprocessing and Memristor Dynamics in Reservoir Computing for Image Classification** — [arxiv_ai](https://arxiv.org/abs/2604.21602v1)
- **CoFEE: Reasoning Control for LLM-Based Feature Discovery** — [arxiv_ai](https://arxiv.org/abs/2604.21584v1)
- **Mitigate or Fail: How Risk Management Shapes Cybersecurity Competency** — [arxiv_cr](https://arxiv.org/abs/2604.21604v1)
- **MathDuels: Evaluating LLMs as Problem Posers and Solvers** — [arxiv_cl](https://arxiv.org/abs/2604.21916v1)
- **Mapping the Political Discourse in the Brazilian Chamber of Deputies: A Multi-Faceted Computational Approach** — [arxiv_cl](https://arxiv.org/abs/2604.21897v1)
- **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA** — [arxiv_cl](https://arxiv.org/abs/2604.21766v1)
- **From If-Statements to ML Pipelines: Revisiting Bias in Code-Generation** — [arxiv_cl](https://arxiv.org/abs/2604.21716v1)
- **Phonological Subspace Collapse Is Aetiology-Specific and Cross-Lingually Stable: Evidence from 3,374 Speakers** — [arxiv_cl](https://arxiv.org/abs/2604.21706v1)
- **How English Print Media Frames Human-Elephant Conflicts in India** — [arxiv_cl](https://arxiv.org/abs/2604.21496v1)
- **Generalizing Numerical Reasoning in Table Data through Operation Sketches and Self-Supervised Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21495v1)
- **Cross-Domain Data Selection and Augmentation for Automatic Compliance Detection** — [arxiv_cl](https://arxiv.org/abs/2604.21469v1)
- **Reasoning Primitives in Hybrid and Non-Hybrid LLMs** — [arxiv_cl](https://arxiv.org/abs/2604.21454v1)
- **Interpretable facial dynamics as behavioral and perceptual traces of deepfakes** — [arxiv_lg](https://arxiv.org/abs/2604.21760v1)
- **Ramen: Robust Test-Time Adaptation of Vision-Language Models with Active Sample Selection** — [arxiv_lg](https://arxiv.org/abs/2604.21728v1)
- **Evaluating Post-hoc Explanations of the Transformer-based Genome Language Model DNABERT-2** — [arxiv_lg](https://arxiv.org/abs/2604.21690v1)
- **A-THENA: Early Intrusion Detection for IoT with Time-Aware Hybrid Encoding and Network-Specific Augmentation** — [arxiv_lg](https://arxiv.org/abs/2604.21623v1)
- **Verifying Machine Learning Interpretability Requirements through Provenance** — [arxiv_lg](https://arxiv.org/abs/2604.21599v1)
- **Dynamical Priors as a Training Objective in Reinforcement Learning** — [arxiv_lg](https://arxiv.org/abs/2604.21464v1)
- **Tempered Sequential Monte Carlo for Trajectory and Policy Optimization with Differentiable Dynamics** — [arxiv_lg](https://arxiv.org/abs/2604.21456v1)
- **CSC: Turning the Adversary's Poison against Itself** — [arxiv_cr](https://arxiv.org/abs/2604.21416v1)
- **Adversarial Evasion in Non-Stationary Malware Detection: Minimizing Drift Signals through Similarity-Constrained Perturbations** — [arxiv_cr](https://arxiv.org/abs/2604.21310v1)
- **CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2604.21308v1)
- **Strategic Heterogeneous Multi-Agent Architecture for Cost-Effective Code Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2604.21282v1)
- **Adaptive Instruction Composition for Automated LLM Red-Teaming** — [arxiv_cr](https://arxiv.org/abs/2604.21159v1)
- **AI-Gram: When Visual Agents Interact in a Social Network** — [arxiv_cl](https://arxiv.org/abs/2604.21446v1)
- **mcdok at SemEval-2026 Task 13: Finetuning LLMs for Detection of Machine-Generated Code** — [arxiv_cl](https://arxiv.org/abs/2604.21365v1)
- **CARE: Counselor-Aligned Response Engine for Online Mental-Health Support** — [arxiv_cl](https://arxiv.org/abs/2604.21352v1)
- **Vista4D: Video Reshooting with 4D Point Clouds** — [huggingface_papers](https://arxiv.org/abs/2604.21915)
- **Encoder-Free Human Motion Understanding via Structured Motion Descriptions** — [huggingface_papers](https://arxiv.org/abs/2604.21668)
- **Explainable Disentangled Representation Learning for Generalizable Authorship Attribution in the Era of Generative AI** — [huggingface_papers](https://arxiv.org/abs/2604.21300)
- **StyleID: A Perception-Aware Dataset and Metric for Stylization-Agnostic Facial Identity Recognition** — [huggingface_papers](https://arxiv.org/abs/2604.21689)
- **WorldMark: A Unified Benchmark Suite for Interactive Video World Models** — [huggingface_papers](https://arxiv.org/abs/2604.21686)
- **Seeing Fast and Slow: Learning the Flow of Time in Videos** — [arxiv_ai](https://arxiv.org/abs/2604.21931v1)
- **When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21911v1)
- **From Research Question to Scientific Workflow: Leveraging Agentic AI for Science Automation** — [arxiv_ai](https://arxiv.org/abs/2604.21910v1)
- **Evaluation of Automatic Speech Recognition Using Generative Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21928v1)
- **EVENT5Ws: A Large Dataset for Open-Domain Event Extraction from Documents** — [arxiv_cl](https://arxiv.org/abs/2604.21890v1)
- **Revisiting Non-Verbatim Memorization in Large Language Models: The Role of Entity Surface Forms** — [arxiv_cl](https://arxiv.org/abs/2604.21882v1)
- **SemEval-2026 Task 4: Narrative Story Similarity and Narrative Representation Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21782v1)
- **Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability** — [arxiv_lg](https://arxiv.org/abs/2604.21930v1)
- **Fine-Tuning Regimes Define Distinct Continual Learning Problems** — [arxiv_lg](https://arxiv.org/abs/2604.21927v1)
- **The Sample Complexity of Multicalibration** — [arxiv_lg](https://arxiv.org/abs/2604.21923v1)
- **Low-Rank Adaptation Redux for Large Models** — [arxiv_lg](https://arxiv.org/abs/2604.21905v1)
- **Revealing Geography-Driven Signals in Zone-Level Claim Frequency Models: An Empirical Study using Environmental and Visual Predictors** — [arxiv_lg](https://arxiv.org/abs/2604.21893v1)
- **Beyond Expected Information Gain: Stable Bayesian Optimal Experimental Design with Integral Probability Metrics and Plug-and-Play Extensions** — [arxiv_lg](https://arxiv.org/abs/2604.21849v1)
- **On the algebra of Koopman eigenfunctions and on some of their infinities** — [arxiv_lg](https://arxiv.org/abs/2604.21825v1)
- **PrismaDV: Automated Task-Aware Data Unit Test Generation** — [arxiv_lg](https://arxiv.org/abs/2604.21765v1)
- **Context Unrolling in Omni Models** — [huggingface_papers](https://arxiv.org/abs/2604.21921)
- **Three reasons why DeepSeek’s new model matters** — [mit_tech_review](https://www.technologyreview.com/2026/04/24/1136422/why-deepseeks-v4-matters/)
- **8 Gemini tips for organizing your space (and life)** — [google_ai](https://blog.google/products-and-platforms/products/gemini/gemini-spring-cleaning-tips/)
- **Google to invest up to $40B in Anthropic in cash and compute** — [techcrunch_ai](https://techcrunch.com/2026/04/24/google-to-invest-up-to-40b-in-anthropic-in-cash-and-compute/)
- **Apple’s new CEO, and why Elon Musk wants to buy Cursor for $60B** — [techcrunch_ai](https://techcrunch.com/podcast/apples-new-ceo-and-why-elon-musk-wants-to-buy-cursor-for-60b/)
- **Marked-up Mac minis flood eBay amid shortages driven by AI** — [techcrunch_ai](https://techcrunch.com/2026/04/24/mac-mini-price-expensive-ebay-shortage-ai-memory/)
- **How Project Maven taught the military to love AI** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/917996/project-maven-military-ai-katrina-manson)
- **Uber CTO Praveen Neppalli Naga joins stacked StrictlyVC SF lineup for April 30 event** — [techcrunch_ai](https://techcrunch.com/2026/04/24/uber-cto-praveen-neppalli-naga-joins-stacked-strictlyvc-sf-lineup-for-april-30-event/)
- **Tim Cook is stepping down. What happens to Apple now?** — [techcrunch_ai](https://techcrunch.com/video/tim-cook-is-stepping-down-what-happens-to-apple-now/)
- **DeepSeek previews new AI model that ‘closes the gap’ with frontier models** — [techcrunch_ai](https://techcrunch.com/2026/04/24/deepseek-previews-new-ai-model-that-closes-the-gap-with-frontier-models/)
- **AirPods, Touch Bars, and the rest of Tim Cook&#8217;s legacy** — [theverge_ai](https://www.theverge.com/podcast/917965/apple-ceo-cook-ternus-transition)
- **The Download: supercharged scams and studying AI healthcare** — [mit_tech_review](https://www.technologyreview.com/2026/04/24/1136400/the-download-supercharged-scams-questionable-ai-healthcare/)
- **Musk vs. Altman is here, and it&#8217;s going to get messy** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/917755/musk-altman-openai-xai-gossip)
- **China’s DeepSeek previews new AI model a year after jolting US rivals** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/918035/deepseek-preview-v4-ai-model)
- **Prestigious photo contest answers ‘what is a photo?’** — [theverge_ai](https://www.theverge.com/gadgets/918016/prestigious-photo-contest-answers-what-is-a-photo)
- **Meta’s loss is Thinking Machines’ gain** — [techcrunch_ai](https://techcrunch.com/2026/04/24/metas-loss-is-thinking-machines-gain/)
- **ComfyUI hits $500M valuation as creators seek more control over AI-generated media** — [techcrunch_ai](https://techcrunch.com/2026/04/24/comfyui-hits-500m-valuation-as-creators-seek-more-control-over-ai-generated-media/)
- **Nothing introduces an AI-powered dictation tool** — [techcrunch_ai](https://techcrunch.com/2026/04/24/nothing-introduces-an-ai-powered-dictation-tool/)
- **In another wild turn for AI chips, Meta signs deal for millions of Amazon AI CPUs** — [techcrunch_ai](https://techcrunch.com/2026/04/24/in-another-wild-turn-for-ai-chips-meta-signs-deal-for-millions-of-amazon-ai-cpus/)
- **9点1氪丨马斯克花4000多亿买下00后公司；世界杯决赛门票转手价近230万美元** — [36kr](https://36kr.com/p/3781532841581576?f=rss)
- **sjsyrek/design-council** — [github](https://github.com/sjsyrek/design-council)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **巨星农牧：一季度公司的商品肥猪完全成本约为6.35元/斤** — [36kr](https://36kr.com/newsflashes/3782000516635648?f=rss)
- **Momenta一年间量产搭载量逾80万台** — [36kr](https://36kr.com/newsflashes/3781966595234825?f=rss)
- **百度智能云上线DeepSeek-V4** — [36kr](https://36kr.com/newsflashes/3781942204128513?f=rss)
- **我国单机容量最大“超级充电宝”3号机组顺利投运** — [36kr](https://36kr.com/newsflashes/3781921407507459?f=rss)
- **本田在华研发转向中方主导** — [36kr](https://36kr.com/newsflashes/3781884274318344?f=rss)
- **下游需求激增，CPU重回AI核心，A股布局公司梳理** — [36kr](https://36kr.com/newsflashes/3781844281007361?f=rss)
- **kimi-K2-6/kimi-K2.6** — [github](https://github.com/kimi-K2-6/kimi-K2.6)
- **selmakcby/claude-agents-skills** — [github](https://github.com/selmakcby/claude-agents-skills)
- **jwangkun/hermes-agent-guide** — [github](https://github.com/jwangkun/hermes-agent-guide)
- **dainsiahtill-dev/Polaris** — [github](https://github.com/dainsiahtill-dev/Polaris)
- **chaohong-ai/ai-auto-work** — [github](https://github.com/chaohong-ai/ai-auto-work)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **chekusu/wanman** — [github](https://github.com/chekusu/wanman)
- **intertwine/dspy-agent-skills** — [github](https://github.com/intertwine/dspy-agent-skills)
- **muxprotocol/kalshi-trading-bot** — [github](https://github.com/muxprotocol/kalshi-trading-bot)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **TheRealSeanDonahoe/agents-md** — [github](https://github.com/TheRealSeanDonahoe/agents-md)
- **alchaincyf/huashu-design** — [github](https://github.com/alchaincyf/huashu-design)
- **司美格鲁肽专利到期月余未见“国产首证”，多家申报企业称审批因数据保护期“暂缓”** — [36kr](https://36kr.com/newsflashes/3781834150976773?f=rss)
- **首个全国产控制系统水光互补项目今天投运** — [36kr](https://36kr.com/newsflashes/3781761309400068?f=rss)
- **天猫618推家电"送装一体"，覆盖全国95%区域** — [36kr](https://36kr.com/newsflashes/3781735819222022?f=rss)
- **潘功胜：持续整治金融机构“内卷式”竞争，高质量统筹做好金融“五篇大文章”** — [36kr](https://36kr.com/newsflashes/3781734984473856?f=rss)
- **美图立方视觉艺术中心开工，预计2028年投入使用** — [36kr](https://36kr.com/newsflashes/3781662685371396?f=rss)
- **阿塞拜疆主权财富基金第一季度抛售约22吨黄金，十多年来首次减持** — [36kr](https://36kr.com/newsflashes/3781654300450048?f=rss)
- **“固收+”基金规模突破3万亿元** — [36kr](https://36kr.com/newsflashes/3781603152780293?f=rss)
- **甲骨文密歇根数据中心获160亿美元融资** — [36kr](https://36kr.com/newsflashes/3781600900176901?f=rss)
- **36氪首发 | 核心团队来自微软，获近亿投资，要打通AI进厂最后一公里** — [36kr](https://36kr.com/p/3781548853533959?f=rss)
- **低头是日常，抬头是阅读** — [36kr](https://36kr.com/p/3780986341153798?f=rss)
- **最前线｜AI+激光通信，中科天塔要用「太空智驾」体系实现卫星管理模式的三级跨越** — [36kr](https://36kr.com/p/3780910411193602?f=rss)
- **氪星晚报｜美团万亿级参数大模型开放测试，训练全程由国产算力集群完成；百度联盟正式发布海外App业务；央行等八部门发布金融产品网络营销管理办法** — [36kr](https://36kr.com/p/3777694346548482?f=rss)
- **科氪|高配不溢价，20万内首选！国民好车2.0深蓝L06增程版折后价低至127155元起** — [36kr](https://36kr.com/p/3780654186535941?f=rss)
- **YilmazKadir/Volt** — [github](https://github.com/YilmazKadir/Volt)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **g2i-ai/agents** — [github](https://github.com/g2i-ai/agents)
- **realZillionX/InspireSkill** — [github](https://github.com/realZillionX/InspireSkill)
- **Google-Cloud-AI/agent-platform** — [github](https://github.com/Google-Cloud-AI/agent-platform)
- **Mahiruxia/hermes-forge** — [github](https://github.com/Mahiruxia/hermes-forge)
- **自动驾驶赛道DeepSeek，轻舟智航率先进军物理AI** — [qbitai](https://www.qbitai.com/2026/04/407026.html)
- **硬刚GPT-Image-2！国产AI生图“天花板”又被捅破了？** — [qbitai](https://www.qbitai.com/2026/04/406994.html)
- **AI自主监测宠物健康，陪狗都不用自己来了！涂鸦Hey Tuya打造全屋智能“超级入口”** — [qbitai](https://www.qbitai.com/2026/04/406973.html)
- **燃油SUV车主熬出头了！华为乾崑智驾加持，全新奥迪Q5L率先实现智能化** — [qbitai](https://www.qbitai.com/2026/04/406960.html)
- **0博士组合拿下ICLR时间检验奖！两个GPT天才本科生+二本逆袭LeCun弟子，十年论文终封神** — [qbitai](https://www.qbitai.com/2026/04/406892.html)
- **DeepSeek V4报告太详尽了！484天换代之路全公开** — [qbitai](https://www.qbitai.com/2026/04/406809.html)
- **Mobileye 2026财年一季度营收增长27%，自动驾驶商业化进程持续推进** — [qbitai](https://www.qbitai.com/2026/04/406775.html)
- **优必选发布Thinker cosmos：加码开发者生态，推动人形机器人走向规模化** — [qbitai](https://www.qbitai.com/2026/04/406806.html)
- **PPIO首批上线DeepSeek-V4预览版，1M超长上下文能力开箱即用** — [qbitai](https://www.qbitai.com/2026/04/406802.html)
- **DeepSeek-V4发布，华为云首发适配** — [qbitai](https://www.qbitai.com/2026/04/406791.html)