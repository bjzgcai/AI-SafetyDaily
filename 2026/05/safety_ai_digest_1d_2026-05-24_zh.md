# AI 日报 [AI 安全] - 2026-05-24


# AI安全日报 | 2026年5月24日
**主题：AI安全、对齐、隐私与治理**

## Highlights

今日的研究图景呈现出理论深化与工具落地并进的清晰脉络。在学术前沿，**后门攻击防御**的理论框架取得重要突破，研究者通过连接**随机平滑**与**差分隐私**的双重理论视角，为在数据投毒场景下提供可证明的鲁棒性证书开辟了新路径。在**模型安全监控**领域，一项针对**大语言模型（LLM）分布外（OOD）对齐失败**的系统性基准测试研究发布，为评估安全防护机制在未知威胁下的有效性提供了标准化工具。此外，针对**LLM拒绝机制**的攻击方法研究亦有新进展，将“拒绝规避”问题从经验性的激活工程提升到了**潜空间攻击**的理论层面进行审视。

## 学术主题综述

### 对抗攻击与鲁棒性：从理论保证到新型攻击

本日在该领域出现了两项方向互补但视角迥异的工作。一方面，研究者致力于为防御机制提供坚实的数学保证。论文 **《Provable Robustness against Backdoor Attacks via the Primal-Dual Perspective on Differential Privacy》** 提出了一种新颖的理论连接，将用于认证对抗性扰动鲁棒性的**随机平滑**技术，与差分隐私的对偶观点相结合。这项工作的核心创新在于，它首次尝试将训练时和测试时的随机化机制纳入一个统一的鲁棒性证书框架内，从而应对后门攻击中训练与测试数据被联合扰动的复杂挑战。作者声称其方法为对抗后门投毒提供了可证明的保障，但该理论框架在实际复杂模型和大规模数据上的验证尚待深入。

另一方面，研究则从攻击方视角揭示了现有安全对齐机制的脆弱性。论文 **《Latent-space Attacks for Refusal Evasion in Language Models》** 对“拒绝规避”这一安全威胁进行了理论建模。现有的绕过模型安全护栏的方法（如激活工程）通常是经验性的，缺乏对其内在机制的理解。本文作者将拒绝抑制重新定义为一种**潜空间逃避攻击**，其目标是欺骗在模型内部表示上训练的**线性探针**。通过将攻击置于**潜空间优化**的框架下，该研究不仅为解释现有攻击为何有效提供了原则性视角，也暗示了仅依赖于单一线性方向的防御可能面临根本性的理论局限。这两项工作形成了有趣的对比：前者试图在理论上“封堵”攻击，后者则在理论上“解构”防御，共同推动了对抗鲁棒性研究从经验层面向理论层面的深化。

### 模型对齐与可解释性：从概念探查到行为治理

可解释性与对齐研究继续向更精细和更本质的层面探索。在可解释性方法层面，多项研究尝试突破现有范式的局限。论文 **《The Attribution Impossibility: No Feature Ranking Is Faithful, Stable, and Complete Under Collinearity》** 通过严格的数学证明指出，当特征存在共线性时，不存在任何一种特征排名能够同时满足**忠实性**、**稳定性**和**完整性**。这一“不可能定理”为所有基于特征重要性的可解释性方法（XAI）设定了根本的理论边界。研究者进一步提出了一个名为**DASH**的集成方法，通过报告平局来换取稳定性。这项工作迫使社区必须正视XAI方法的固有局限，并在应用中对所得解释的可靠性做出更审慎的判断。

在概念层面，论文 **《Investigating Concept Alignment Using Implausible Category Members》** 提出了一种探查模型概念边界的新策略。传统的探查方法通常询问“合理”的类别成员（例如“汽车是交通工具吗？”），这容易触发模型对训练数据中统计规律的回忆。本文反其道而行，通过询问“不合理”的成员（例如“橄榄是交通工具吗？”）来探测模型概念类别的**语义边界**。这种方法可能更有效地揭示模型是否具备了与人类对齐的、结构化的概念理解，而不仅仅是模式匹配。

在对齐理论层面，两项工作关注了行为规范的不同来源。论文 **《What Counts as AI Sycophancy? A Taxonomy and Expert Survey of a Fragmented Construct》** 深入剖析了“AI谄媚”（Sycophancy）这一概念。研究发现，该术语被用来描述从“赞同用户错误观点”到“过度赞美用户”等一系列行为，缺乏统一定义，这导致评估结果难以比较、缓解策略无法迁移。本文通过构建一个**分类法**和专家调查，试图为这一安全治理中的关键问题建立共同语言，是确保对齐研究有效性的基础性工作。而论文 **《Implicit Safety Alignment from Crowd Preferences》** 则探索从众包偏好数据中提取隐含的共享安全准则。作者观察到，尽管不同用户可能表达不同的偏好目标，但他们可能遵循相似的安全原则。该研究旨在从这些多样化的偏好中**发现**共享的安全标准，并将其**迁移**至下游强化学习任务，以规范智能体行为。这为从大量噪声的人类反馈中提炼核心安全价值观提供了一条潜在路径。

### 隐私保护与联邦学习：聚焦真实世界部署的挑战

联邦学习（FL）的研究正从算法创新向真实世界部署的可靠性倾斜。论文 **《Embedding-Based Federated Learning with Runtime Governance for Iron Deficiency Prediction》** 是一个典型案例。研究者不仅开发了一种用于预测铁缺乏症的基于嵌入的FL流水线，更重要的是，他们将其部署到了两个差异显著的真实临床环境（阿姆斯特丹大学医学中心与英国NHS血液与移植机构）。文章尖锐地指出，绝大多数已发表的FL研究从未达到实际部署阶段。本文的贡献不仅在于技术方案，更在于其详述的**运行时治理**框架和在异构真实数据分布下的实践验证。尽管该研究未提供传统意义上的隐私攻击防御数据，但其在**数据异构性**、**临床效用**和**部署可行性**上的深入探讨，对于推动保护隐私的AI在医疗等敏感领域的落地具有重要参考价值。

### 安全评估基准：构建多维度的测试体系

安全评估正从单一指标向多维度、场景化的基准发展。论文 **《Benchmarking and Improving Monitors for Out-Of-Distribution Alignment Failure in LLMs》** 直指当前LLM安全的一个关键盲区：**分布外（OOD）的对齐失败**。作者构建了一个名为**MOOD**的基准，其核心挑战在于，要为在海量安全数据上训练过的模型找到真正“分布外”的失败案例。研究者的解决方案是设计一个**受限训练集**，用以模拟OOD情况。该基准旨在系统性评估监控流水线检测这类未知安全漏洞的能力，为构建更鲁棒的主动防御体系提供了测试床。

另一项相关工作 **《AttuneBench: A Conversation-Based Benchmark for LLM Emotional Intelligence》** 则聚焦于情感智能这一安全交互维度。现有基准多基于合成、单轮对话或第三方标注，而本文基于200个真实多轮对话构建基准，旨在评估模型能否在真实对话过程中推断并回应参与者的情绪状态。情感智能的缺失可能导致模型给出冷漠或不当的回应，引发用户抵触甚至安全问题。该基准的提出，将LLM的“软性”安全能力评估提上了日程。

### Agent安全与治理：规划、控制与运行时框架

随着LLM驱动的智能体（Agent）能力增强，其安全治理框架也变得至关重要。在规划能力方面，论文 **《Efficient Agentic Reasoning Through Self-Regulated Simulative Planning》** 提出了一个高效的规划框架。作者批评了将规划完全隐含在端到端策略中的做法，认为这会导致推理过程冗长低效。他们主张将决策分解为**系统化推理**（System II）和**反应性执行**（System I），通过模拟和规则约束来提升规划的可靠性和效率。

在运行时控制层面，两项开源项目值得关注。**Emmimal/control-layer** 是一个生产级的控制层，位于应用逻辑和任何LLM之间，提供输入验证、模式强制、断路器、定向重试和审计日志等组合式管道功能。它旨在为LLM调用提供结构化的安全护栏。**infiniumtek/terraform-review-agent** 则是一个专注于基础设施即代码（IaC）安全的工具，它是一个可重用的GitHub Action，使用多智能体系统审查Terraform PR的安全、成本和规范问题，并发布单一、按严重性排序的评论。这些工具代表了将安全实践自动化、集成到开发运维流程中的趋势。

此外，一些开源项目虽不直接针对安全，但其设计隐含了安全考量。**CloakBrowser** 是一个反检测浏览器，通过源码级Chromium补丁来欺骗浏览器指纹，主要用于隐私保护或多账户管理，但其技术亦可被用于规避追踪。**Tartarus-AI/tartarusai-cli** 自称是“无审查的AI编码智能体”，其“跳过说教”的营销话术本身就触及了AI内容治理的边界，提醒我们安全对齐的“松紧度”是一个持续的权衡。

## 产业动态与思考（审慎视角）

来自产业界的动态需在技术宣称与可验证事实间保持审慎。有报道称**DeepSeek V4**价格大幅下调，其创始人梁文锋强调坚持开源并瞄准AGI目标。在竞争驱动的降价和开源承诺背后，安全社区更应关注其模型**实际的安全对齐水平**、**负责任的开源协议**以及**透明的安全评估报告**，而非价格本身。

百川智能**王小川**宣布公司全面转向医疗大模型，推出M4及Agent产品“百小医”。这一战略转向凸显了垂直领域应用对安全性和可靠性的极致要求。医疗场景的**诊断错误风险**、**患者隐私保护**以及**AI建议的责任归属**，使得其安全框架必须远比通用模型更为严格。这代表了行业从追求模型泛化能力到聚焦**领域专用安全与可靠性**的重要趋势。

对于36氪等平台发布的多个行业圆桌讨论，其中关于“AI原生人才”、“应用转化率”和“物理世界入口”的观点，反映了产业界对AI落地形态的探索。然而，这些讨论多为前瞻性观点，缺乏可验证的数据支撑。一个值得关注的共识是，单纯“套壳”大模型的应用模式被认为缺乏长期竞争力。这对安全治理的启示在于，未来安全评估和治理框架需要能适应**深度集成**、**具身智能**和**长期在线**的AI系统，其复杂性和交互维度远超当前的对话模型。

## Looking Forward

今日的进展也引出了若干待解决的理论与实践问题。首先，**可证明鲁棒性**的理论框架如何在不显著降低模型效用的前提下，扩展到更强大的后门攻击和更大规模的模型？其次，针对OOD对齐失败的监控基准**MOOD**，其构建方法能否泛化到更广泛的、未预见的失败模式，还是说真正的“分布外”安全威胁本质上是无法通过有限测试集捕获的？第三，潜空间攻击研究揭示了表示层面的脆弱性，那么，能否发展出**可证明安全的内部表示学习方法**，而不仅仅是在应用层进行对齐和监控？最后，随着智能体与物理世界的交互日益紧密，如何为其规划与执行过程设计**实时、可解释且可中断的安全治理协议**，将是下一个阶段的核心挑战。

---


## 参考来源

- **Provable Robustness against Backdoor Attacks via the Primal-Dual Perspective on Differential Privacy** — [arxiv_lg](https://arxiv.org/abs/2605.21780)
- **Embedding-Based Federated Learning with Runtime Governance for Iron Deficiency Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.21563)
- **Measuring Cross-Modal Synergy: A Benchmark for VLM Explainability** — [arxiv_ai](https://arxiv.org/abs/2605.22168)
- **The Attribution Impossibility: No Feature Ranking Is Faithful, Stable, and Complete Under Collinearity** — [arxiv_lg](https://arxiv.org/abs/2605.21492)
- **Leveraging Self-Paced Curriculum Learning for Enhanced Modality Balance in Multimodal Conversational Emotion Recognition** — [arxiv_lg](https://arxiv.org/abs/2605.21565)
- **PEARL: Unbiased Percentile Estimation via Contrastive Learning for Industrial-Scale Livestream Recommendation** — [arxiv_lg](https://arxiv.org/abs/2605.21752)
- **AOP-Wiki EMOD 3.0: Data Model Expansions and Content Evaluation Framework for Using Agentic AI to Improve Integration between AOPs and New Approach Methodologies (NAMs)** — [arxiv_ai](https://arxiv.org/abs/2605.21645)
- **Investigating Concept Alignment Using Implausible Category Members** — [arxiv_ai](https://arxiv.org/abs/2605.21683)
- **A Causal Argumentation Method for Explainability of Machine Learning Models** — [arxiv_ai](https://arxiv.org/abs/2605.21758)
- **What Counts as AI Sycophancy? A Taxonomy and Expert Survey of a Fragmented Construct** — [arxiv_ai](https://arxiv.org/abs/2605.21778)
- **Implicit Safety Alignment from Crowd Preferences** — [arxiv_ai](https://arxiv.org/abs/2605.21822)
- **ECPO: Evidence-Coupled Policy Optimization for Evidence-Certified Candidate Ranking** — [arxiv_ai](https://arxiv.org/abs/2605.21993)
- **Teaching Language Models to Forecast Research Success Through Comparative Idea Evaluation** — [arxiv_lg](https://arxiv.org/abs/2605.21491)
- **Harnesses for Inference-Time Alignment over Execution Trajectories** — [arxiv_lg](https://arxiv.org/abs/2605.21516)
- **A Reproducible Log-Driven AutoML Framework for Interpretable Pipeline Optimization in Healthcare Risk Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.21528)
- **DualOptim+: Bridging Shared and Decoupled Optimizer States for Better Machine Unlearning in Large Language Models** — [arxiv_lg](https://arxiv.org/abs/2605.21539)
- **Tabular foundation models for robust calibration of near-infrared chemical sensing data** — [arxiv_lg](https://arxiv.org/abs/2605.21544)
- **PeakFocus: Bridging Peak Localization and Intensity Regression via a Unified Multi-Scale Framework for Electricity Load Forecasting** — [arxiv_lg](https://arxiv.org/abs/2605.21550)
- **Expectation Consistency Loss: Rethink Confidence Calibration under Covariate Shift** — [arxiv_lg](https://arxiv.org/abs/2605.21552)
- **Beyond Single Slot: Joint Optimization for Multi-Slot Guaranteed Display Advertising** — [arxiv_lg](https://arxiv.org/abs/2605.21556)
- **From Parameters to Data: A Task-Parameter-Guided Fine-Tuning Pipeline for Efficient LLM Alignment** — [arxiv_lg](https://arxiv.org/abs/2605.21558)
- **Objective-Induced Bias and Search Dynamics in Multiobjective Unsupervised Feature Selection** — [arxiv_lg](https://arxiv.org/abs/2605.21561)
- **ConTact: Contact-First Antibody CDR Design via Explicit Interface Reasoning** — [arxiv_lg](https://arxiv.org/abs/2605.21600)
- **When Are Teacher Tokens Reliable? Position-Weighted On-Policy Self-Distillation for Reasoning** — [arxiv_lg](https://arxiv.org/abs/2605.21606)
- **$\textit{BlockFormer}$ : Transformer-based inference from interaction maps** — [arxiv_lg](https://arxiv.org/abs/2605.21617)
- **Alike Parts: A Feature-Informed Approach to Local and Global Prototype Explanations** — [arxiv_lg](https://arxiv.org/abs/2605.21646)
- **Dropout Universality: Scaling Laws and Optimal Scheduling at the Edge-of-Chaos** — [arxiv_lg](https://arxiv.org/abs/2605.21648)
- **Benchmarking and Improving Monitors for Out-Of-Distribution Alignment Failure in LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.21602)
- **Latent-space Attacks for Refusal Evasion in Language Models** — [arxiv_ai](https://arxiv.org/abs/2605.21706)
- **AttuneBench: A Conversation-Based Benchmark for LLM Emotional Intelligence** — [arxiv_ai](https://arxiv.org/abs/2605.21739)
- **Who Uses AI? Platforms, Workforce, and AI Exposure** — [arxiv_ai](https://arxiv.org/abs/2605.21743)
- **Trace2Skill: Verifier-Guided Skill Evolution for Long-Context EDA Agents** — [arxiv_ai](https://arxiv.org/abs/2605.21810)
- **Planning in the LLM Era: Building for Reliability and Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.21902)
- **AI-Enabled Serious Games: Integrating Intelligence and Adaptivity in Training Systems** — [arxiv_ai](https://arxiv.org/abs/2605.21962)
- **A Camera-Cooperative ISAC Framework for Multimodal Non-Cooperative UAVs Sensing** — [arxiv_ai](https://arxiv.org/abs/2605.22090)
- **ArborKV: Structure-Aware KV Cache Management for Scaling Tree-based LLM Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.22106)
- **Efficient Agentic Reasoning Through Self-Regulated Simulative Planning** — [arxiv_ai](https://arxiv.org/abs/2605.22138)
- **Adapting the Interface, Not the Model: Runtime Harness Adaptation for Deterministic LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2605.22166)
- **LLM-Metrics: Measuring Research Impact Through Large Language Model Memory** — [arxiv_ai](https://arxiv.org/abs/2605.22176)
- **CLORE: Content-Level Optimization for Reasoning Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.22211)
- **Elon Musk has given up on solar power (on Earth)** — [techcrunch_ai](https://techcrunch.com/2026/05/23/elon-musk-has-given-up-on-solar-power-on-earth/)
- **Google’s new anything-to-anything AI model is wild** — [theverge_ai](https://www.theverge.com/tech/936507/gemini-omni-hands-on-deepfake-ai-video)
- **Ferrari is using IBM’s AI to create F1 superfans** — [techcrunch_ai](https://techcrunch.com/2026/05/23/ferrari-is-using-ai-to-create-f1-superfans/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **5bv57zcm44-max/NOXUS-AI-Open-WhatsApp** — [github](https://github.com/5bv57zcm44-max/NOXUS-AI-Open-WhatsApp)
- **Emmimal/control-layer** — [github](https://github.com/Emmimal/control-layer)
- **infiniumtek/terraform-review-agent** — [github](https://github.com/infiniumtek/terraform-review-agent)
- **ayush016/android-lead-agent-skills** — [github](https://github.com/ayush016/android-lead-agent-skills)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **open-gsd/gsd-pi** — [github](https://github.com/open-gsd/gsd-pi)
- **kingbootoshi/directional-prompting** — [github](https://github.com/kingbootoshi/directional-prompting)
- **mikaeldengale-cloud/Deepseek-v4-Pro-App** — [github](https://github.com/mikaeldengale-cloud/Deepseek-v4-Pro-App)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **h4ckf0r0day/awesome-ai-web-scraping** — [github](https://github.com/h4ckf0r0day/awesome-ai-web-scraping)
- **xuanlinAI/overmind** — [github](https://github.com/xuanlinAI/overmind)
- **leiting-eric/DailyBrief** — [github](https://github.com/leiting-eric/DailyBrief)
- **kingbootoshi/goal-ledger** — [github](https://github.com/kingbootoshi/goal-ledger)
- **op7418/ai-desk-card** — [github](https://github.com/op7418/ai-desk-card)
- **hasanyilmaz/operon** — [github](https://github.com/hasanyilmaz/operon)
- **zhongweiv/hermes-edu-skills** — [github](https://github.com/zhongweiv/hermes-edu-skills)
- **c4pt0r/pie** — [github](https://github.com/c4pt0r/pie)
- **nkzw-tech/cloudsail** — [github](https://github.com/nkzw-tech/cloudsail)
- **Tartarus-AI/tartarusai-cli** — [github](https://github.com/Tartarus-AI/tartarusai-cli)
- **“五类人AI替代不了，企业做第二名最稳妥” | 昆仑万维方汉@AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/423202.html)
- **OpenAI大神教你如何榨干Codex** — [qbitai](https://www.qbitai.com/2026/05/423179.html)
- **DeepSeek V4价格打骨折，宁王京东网易抢着入场，梁文锋：目标是AGI** — [qbitai](https://www.qbitai.com/2026/05/423162.html)
- **中证投服提名独立董事已扩展至14家A股公司，最高年薪达25万元** — [36kr](https://36kr.com/newsflashes/3822733352390786?f=rss)
- **华泰证券：看好2026年起交换芯片在AI驱动下开启二次成长** — [36kr](https://36kr.com/newsflashes/3822612389941383?f=rss)
- **“天韵相机”项目负责人：香港航天员操作港研仪器意义重大** — [36kr](https://36kr.com/newsflashes/3822609989734531?f=rss)
- **圆桌对话：下一个杀手级AI产品，会出现在哪个赛道？| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3821714896408713?f=rss)
- **老虎国际：未有“拒不配合监管”等言论，2023年起已全停内地开户营销** — [36kr](https://36kr.com/newsflashes/3821606327111813?f=rss)
- **圆桌对话：当AI进入产业前线：未来最稀缺的AI人才，会是谁？| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3821542483857801?f=rss)
- **圆桌对话：人才特种兵：“AI原生人才”与“产业老炮”的共生手册| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3821533415985283?f=rss)
- **对话王小川：离开通用人工智能的主干道之后** — [36kr](https://36kr.com/p/3821521291038856?f=rss)
- **圆桌对话：AI浓度与转化率：数字体验的实战增长法则** — [36kr](https://36kr.com/p/3821519307591811?f=rss)
- **康斯特回应是否与SpaceX扩大合作，称单一用户影响有限** — [36kr](https://36kr.com/newsflashes/3821498732302723?f=rss)
- **36氪首发 | 北大项目孵化，国内首家原生机器人“大脑芯片”企业获数亿元融资** — [36kr](https://36kr.com/p/3821371042877575?f=rss)
- **屈臣氏计划下半年赴中国香港、伦敦两地上市** — [36kr](https://36kr.com/newsflashes/3821499521060998?f=rss)