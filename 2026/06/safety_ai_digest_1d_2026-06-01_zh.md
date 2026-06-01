# AI 日报 [AI 安全] - 2026-06-01


# AI安全每日专题综述 (2026年6月1日)

## Highlights

今日AI安全领域的进展呈现出“威胁持续演进”与“防御理论深化”的辩证图景。最重要的突破集中在三个方面：首先，**BadBone** 揭示了提示学习范式下针对基础模型的**后门攻击**新路径，凸显了供应链安全威胁的隐蔽性与系统性；其次，**ELUDe** 提出了一种能在保持模型预测性能无损前提下提升其可解释性的方法，为解开神经网络“黑箱”提供了新的理论工具；最后，**VIABLE** 基准的发布，首次系统评估了“视觉语言模型作为评判者”在视觉障碍辅助等高风险、高伦理要求场景下的可靠性，为建立负责任的AI应用评估框架奠定了基础。这些工作共同标志着研究正从识别具体漏洞，向构建更安全、可信的AI系统理论基础迈进。

## 对抗攻击与安全评估基准

本日研究在攻击方法与评估体系上均有重要进展，反映了“矛”与“盾”的持续博弈。**Latent Geometric Chords (LGC)** 提出了一种新的黑盒决策型对抗攻击框架。与以往在像素空间或受限的潜空间进行扰动不同，该方法通过执行**曲率感知的几何导航**来探索决策边界，旨在以更少的查询次数生成更自然的对抗样本。作者声称其方法在查询效率和攻击成功率上优于现有基线，但作为黑盒攻击，其实际威胁程度仍需在更多样的现实场景下验证。

与LGC从外部发起的攻击不同，**BadBone** 揭示了一种更底层的威胁。它首次针对“提示学习”这一新兴机器学习范式，提出了一种**针对基础骨干模型的后门攻击**。其核心思想是：攻击者无需污染下游的提示学习过程，而是通过双层优化，预先在共享的骨干模型中植入一个“休眠”的后门。当任何下游任务使用该骨干模型进行提示学习时，该后门便会被继承并激活。作者声称实验表明这种攻击具有很高的隐蔽性和跨任务适应性。这凸显了AI供应链中，基础模型作为“公共基础设施”可能带来的巨大安全风险。

在评估层面，两项新基准分别从伦理安全和高级认知能力角度拓展了评估边界。**VIABLE** 基准直接回应了将AI用于弱势群体辅助（视觉障碍辅助）时面临的严峻信任问题。它系统构建了超过30万条样本，用于评估VLM-as-a-Judge在**有效性、公平性和稳定性**三个维度上的表现。研究发现，当前的VLM评判者在这些方面存在显著不足，这为该范式在医疗、无障碍等关键领域的部署敲响了警钟。

与此同时，**SVI-Bench** 则着眼于评估模型的**战略性视频智能**，要求模型不仅能感知，还要进行因果推理、模拟和规划。虽然该基准并非专为安全设计，但其评估的能力栈——理解事件因果、预测不同条件下的结果、制定行动策略——恰恰是高级AI Agent实现安全、可控交互所必须具备的认知基础。该基准的建立，为衡量Agent在复杂环境中的推理与决策可靠性提供了新的工具。

## 模型对齐、可解释性与幻觉缓解

提升模型内部机制的透明度与可控性，是实现有效对齐的关键。**ELUDe (Explicit, Lossless, Unsupervised Disentanglement)** 在这一方向上取得了重要理论进展。深度神经网络中普遍存在的**多义性神经元**（一个神经元编码多个无关概念）严重阻碍了可解释性。以往通过稀疏自编码器等技术可以将混合信号分解为更有意义的单义特征，但这通常需要修改模型结构，往往以牺牲下游任务性能为代价。ELUDe的核心创新在于，它声称能够在**不损失任何预测性能**的前提下，以无监督的方式将网络中的多义特征分解为单义特征。如果这一结论得到广泛验证，它将极大推动“忠实于原模型”的可解释性研究，使得对已部署模型的审计和理解成为可能，而无需进行代价高昂的再训练。

在应用层面，缓解大型视觉语言模型的幻觉是当前对齐与安全的热点。**YARD** 提出了一种新的无需训练的对比解码方法。它指出，现有方法要么完全丢弃视觉信息（导致语言主导的幻觉），要么对图像进行粗粒度损坏（控制不够精细且推理慢）。YARD设计了一种Y型架构，引入一个可学习的寄存器来更精细地调制视觉证据的退化程度。作者声称这种方法在有效缓解幻觉的同时，保持了较高的推理效率。这体现了通过精细控制模型输入来引导其输出、从而提升安全性的“干预式”对齐思路。

## Agent安全、治理与工具化趋势

随着AI Agent从概念走向应用，其安全性与治理框架的构建变得愈发紧迫。尽管本次汇总中直接以“Agent安全”为名的顶级学术论文较少，但多个开源项目和行业讨论共同勾勒出了当前实践的关注点。

在工具层面，多个项目致力于为AI Agent开发提供更安全的“脚手架”。例如，**harness-starter-kit** 被定位为一个“提示优先”的启动工具包，其目标是使代码仓库对AI编码Agent更安全。这反映了社区开始系统性地思考如何在开发流程中嵌入安全约束。**agents-progressive-disclosure** 则提出将庞大复杂的Agent指令文件（如AGENTS.md）重构为紧凑的路由入口和引用文档，这不仅是技术优化，也蕴含了“最小权限”和“清晰边界”的安全治理思想，旨在降低因指令混淆导致的意外行为风险。

更具实验性的是，**Gentle-Coding** 这个概念验证项目声称，对比了“专制式”和“共情式”提示工程对LLM推理行为的影响。其初步观察指出，前者可能诱发模型出现“性能焦虑”、“认知冻结”和“病态思维循环”等异常行为模式，而后者能有效缓解这些现象。尽管这只是一个初步的概念验证，其背后隐含的假设——**与模型的交互范式本身会影响其行为稳定性和可靠性**——对设计安全的人机交互协议具有启发意义。

在治理讨论中，**DriveMA** 工作虽聚焦于自动驾驶，但其提出的“可验证元动作”框架，为AI系统的决策提供了**可审计的中间表示**。通过将连续的驾驶轨迹转化为可被规则验证的语言域意图，这为在复杂动态环境中实现AI决策的**可追溯性**和**可解释性**提供了有益思路。这直接呼应了AI治理中对“透明度”和“问责制”的核心要求。

## Looking Forward

综合今日进展，AI安全领域仍面临多项深层次挑战。首先，在**安全评估**方面，VIABLE基准暴露了当前VLM评判者在敏感场景下的不可靠性，而SVI-Bench则呼唤对更复杂认知能力的安全评估。未来需要开发覆盖更广泛风险维度、且能模拟真实世界动态交互的评估框架。其次，在**威胁防御**上，BadBone揭示的供应链后门攻击表明，安全问题已渗透至模型开发和分享的基础设施层面，亟需建立针对预训练模型和基础服务的**安全认证与审计标准**。再者，在**可解释性与对齐**的融合上，ELUDe等方法的提出是一个激动人心的开端，但其理论基础、在不同架构和任务上的普适性，以及从“可解释”到“可干预”以实现安全对齐的转化路径，仍需大量后续研究验证。最后，如何为自主性日益增强的AI Agent设计**内置的、可扩展的安全与治理框架**，使其在不确定环境中能可靠地遵守人类价值观与规范，将是未来数年最为核心的研究与工程课题。

---


## 参考来源

- **Learning Global Motion with Compact Gaussians for Feed-Forward 4D Reconstruction** — [arxiv_cv](https://arxiv.org/abs/2605.31595v1)
- **A Visually Impaired Assistance Benchmark for VLM-as-a-Judge Evaluation** — [arxiv_cv](https://arxiv.org/abs/2605.31351v1)
- **CoFiDA-M: Concept-Aware Feature Modulation for Cross-Domain Adaptation with Image-Only Inference** — [arxiv_cv](https://arxiv.org/abs/2605.31591v1)
- **TunerDiT: Training-free Progressive Steering of Diffusion Transformer for Multi-Event Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.31590v1)
- **Feature-Optimized Vision for Adaptive 3D Scene Reconstruction** — [arxiv_cv](https://arxiv.org/abs/2605.31534v1)
- **SVI-Bench: A Dynamic Microworld for Strategic Video Intelligence** — [arxiv_cv](https://arxiv.org/abs/2605.31529v1)
- **Personalize Your Large Vision-language Models With In-context Prompt Tuning** — [arxiv_cv](https://arxiv.org/abs/2605.31513v1)
- **YARD: Y-Architecture Register Decoding for Efficient Hallucination Mitigation in Large Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.31429v1)
- **Interpretability Without Tradeoffs: Disentangling Polysemanticity At Equal Predictive Performance** — [arxiv_cv](https://arxiv.org/abs/2605.31304v1)
- **Authentication of Copy Detection Patterns via Cross-Camera Dual-Synthetic Referencing** — [arxiv_cv](https://arxiv.org/abs/2605.31292v1)
- **SAM for Robust Mitochondria Instance Segmentation in Fluorescence Microscopy** — [arxiv_cv](https://arxiv.org/abs/2605.31284v1)
- **DriveMA: Driving Vision-Language-Action Models with verifiable Meta-Actions** — [arxiv_cv](https://arxiv.org/abs/2605.31271v1)
- **Envisioning Beyond the Few: Disentangled Semantics and Primitives for Few-Shot Atypical Layout-to-Image Generation** — [arxiv_cv](https://arxiv.org/abs/2605.31266v1)
- **BadBone: Backdoor Attacks Against Backbone Models in Visual Prompt Learning** — [arxiv_cv](https://arxiv.org/abs/2605.31246v1)
- **Latent Geometric Chords for Query-Efficient Decision-Based Adversarial Attacks** — [arxiv_cv](https://arxiv.org/abs/2605.31219v1)
- **TALON: Token-Aligned Lightweight Adapters for 6-DoF Spacecraft Pose Estimation** — [arxiv_cv](https://arxiv.org/abs/2605.31217v1)
- **Representation Forcing for Bottleneck-Free Unified Multimodal Models** — [arxiv_cv](https://arxiv.org/abs/2605.31604v1)
- **Lumos-Nexus: Efficient Frequency Bridging with Homogeneous Latent Space for Video Unified Models** — [arxiv_cv](https://arxiv.org/abs/2605.31603v1)
- **Linear Scaling Video VLMs for Long Video Understanding** — [arxiv_cv](https://arxiv.org/abs/2605.31598v1)
- **SOCO: Benchmarking Semantic Object Correspondence in Vision Foundation Models** — [arxiv_cv](https://arxiv.org/abs/2605.31597v1)
- **Making sense of the debate over AI psychosis** — [techcrunch_ai](https://techcrunch.com/2026/05/31/making-sense-of-the-debate-over-ai-psychosis/)
- **I went looking for the AI weed vape that gives you Bitcoin for smoking** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/933916/ai-powered-crypto-cannabis-vape)
- **Erin Brockovich takes aim at data center secrecy** — [techcrunch_ai](https://techcrunch.com/2026/05/31/erin-brockovich-takes-aim-at-data-center-secrecy/)
- **MaxwellCCC/autonomous-qa-loop** — [github](https://github.com/MaxwellCCC/autonomous-qa-loop)
- **ali-vilab/DiffusionOPD** — [github](https://github.com/ali-vilab/DiffusionOPD)
- **dexoryn-china/polymarket-arbitrage-bot** — [github](https://github.com/dexoryn-china/polymarket-arbitrage-bot)
- **joshhu/skillopt-qa** — [github](https://github.com/joshhu/skillopt-qa)
- **Caph-dev/agents-progressive-disclosure** — [github](https://github.com/Caph-dev/agents-progressive-disclosure)
- **OttoRenner/Gentle-Coding** — [github](https://github.com/OttoRenner/Gentle-Coding)
- **JuneYaooo/nihaixia** — [github](https://github.com/JuneYaooo/nihaixia)
- **ATOM00blue/machine-learning-library** — [github](https://github.com/ATOM00blue/machine-learning-library)
- **openfi-dao/kalshi-trading-bot** — [github](https://github.com/openfi-dao/kalshi-trading-bot)
- **antigravity-cli-google/antigravity-cli** — [github](https://github.com/antigravity-cli-google/antigravity-cli)
- **steeliron550-ui/search-bibtex** — [github](https://github.com/steeliron550-ui/search-bibtex)
- **modelstudioai/cli** — [github](https://github.com/modelstudioai/cli)
- **K-Dense-AI/science-superpowers** — [github](https://github.com/K-Dense-AI/science-superpowers)
- **veryyoldman/metamask-openclaw** — [github](https://github.com/veryyoldman/metamask-openclaw)
- **Harkirat1462/claude-code-cli** — [github](https://github.com/Harkirat1462/claude-code-cli)
- **withkynam/vibecode-pro-max-kit** — [github](https://github.com/withkynam/vibecode-pro-max-kit)
- **deusjin/subforge** — [github](https://github.com/deusjin/subforge)
- **sir1st/hermes-desktop** — [github](https://github.com/sir1st/hermes-desktop)
- **baskduf/harness-starter-kit** — [github](https://github.com/baskduf/harness-starter-kit)
- **kurikomi-labs/komi-learn** — [github](https://github.com/kurikomi-labs/komi-learn)
- **DDIM之父宋佳铭，宣布离职** — [qbitai](https://www.qbitai.com/2026/05/427104.html)
- **别光给Agent加Tool了，它根本选不明白！复旦×通义提出全新CUA训练范式** — [qbitai](https://www.qbitai.com/2026/05/427005.html)
- **英伟达版「MacBook Pro」曝光：老黄自研了CPU！** — [qbitai](https://www.qbitai.com/2026/05/426991.html)
- **机器人原生世界动作模型问世！首创时空一体架构，复旦系团队出品** — [qbitai](https://www.qbitai.com/2026/05/426984.html)
- **Token贵只因你喂给模型的垃圾太多了丨@亚马逊王晓野AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/426970.html)
- **τ0-WM：最大规模预训练的开源具身世界模型来了** — [qbitai](https://www.qbitai.com/2026/05/426832.html)
- **AI原生时代下，让世界适应Agent，而非教AI做人 | 港大黄超@AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/426819.html)
- **上海：实施优质企业培优、中小企业育强、小微企业成长的梯度激励政策，推动跨境电商、直播电商创新发展** — [36kr](https://36kr.com/newsflashes/3833992947836550?f=rss)
- **硬氪观察 | 苹果代工厂开造人形机器人，一场豪赌未来的产能大迁移** — [36kr](https://36kr.com/p/3833985105782402?f=rss)
- **国务院：国家支持投资者按照市场化原则开展对外投资活动，积极参与国际合作竞争** — [36kr](https://36kr.com/newsflashes/3833970378827648?f=rss)
- **国务院：国家主动对接国际高标准经济贸易规则，推进高质量共建“一带一路”** — [36kr](https://36kr.com/newsflashes/3833969644889735?f=rss)
- **“世纪合并”落空，雅诗兰黛松了一口气** — [36kr](https://36kr.com/p/3825786926633607?f=rss)
- **8点1氪丨停服三年后，天涯社区正式恢复访问；广东辟谣高考将用AI改卷；MiniMax拟科创板上市** — [36kr](https://36kr.com/p/3833859545343618?f=rss)
- **“微光医疗”完成数亿元融资** — [36kr](https://36kr.com/newsflashes/3834001383384708?f=rss)
- **创业板指涨逾1%，上涨个股近4200只** — [36kr](https://36kr.com/newsflashes/3833994033243779?f=rss)
- **科技记者古尔曼：苹果更轻薄的Vision Air头显预计2028年末或2029年发布** — [36kr](https://36kr.com/newsflashes/3833984953296514?f=rss)
- **《国务院关于对外投资的规定》公布** — [36kr](https://36kr.com/newsflashes/3833968792888968?f=rss)
- **“睿健医药”完成2.1亿元C1轮融资** — [36kr](https://36kr.com/newsflashes/3833937295304322?f=rss)