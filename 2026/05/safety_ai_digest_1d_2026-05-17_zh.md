# AI 日报 [AI 安全] - 2026-05-17


# AI 安全与治理日报：2026-05-17

## 亮点

当日学术进展在视频生成评估与视觉模型幻觉抑制方面取得显著突破。**Quantitative Video World Model Evaluation for Geometric-Consistency** 提出了 PDI-Bench 基准，试图解决生成视频物理几何一致性的量化评估难题，为视频世界模型的安全性提供了新的审计维度。在模型可靠性方面，**MHSA: A Lightweight Framework for Mitigating Hallucinations via Steered Attention in LVLMs** 提出了一种基于注意力引导的轻量级框架，直接针对大视觉语言模型中的幻觉问题进行缓解，而非仅停留在检测层面。此外，学术出版治理方面，**ArXiv will ban authors for a year if they let AI do all the work** 标志着预印本平台开始收紧对生成式 AI 滥用行为的管控，这为 AI 科研伦理确立了新的底线。产业界虽有 OpenAI 相关人事变动及媒体关于高额 Token 消耗的传闻，但独立验证尚待确认，需警惕营销话术对安全讨论的干扰。

## 视频生成的一致性与安全评估

随着生成式视频模型向长序列和复杂叙事发展，保持实体一致性和物理合理性成为安全部署的关键前提。**EntityBench: Towards Entity-Consistent Long-Range Multi-Shot Video Generation** 构建了一个包含 140 个剧集的基准，通过追踪角色、物体和位置的一致性，揭示了现有模型在长程多镜头生成中的实体漂移问题。该基准与 **Quantitative Video World Model Evaluation for Geometric-Consistency** 形成互补，后者引入了 PDI-Bench 框架，利用分割和点跟踪技术量化几何失真，弥补了以往依赖主观人类判断的不足。这两项工作共同指向了视频生成安全评估的标准化需求，即从单纯的内容生成转向对物理世界逻辑的验证。

在生成机制层面，**RAVEN: Real-time Autoregressive Video Extrapolation with Consistency-model GRPO** 通过一致性模型 GRPO 解决了自回归视频外推中的分布偏移问题，提升了长时生成的稳定性。与此同时，**Warp-as-History: Generalizable Camera-Controlled Video Generation from One Training Video** 提出了一种无需后训练的相机控制接口，将相机运动转化为历史变形，降低了控制分支对大规模标注数据的依赖。这些方法在提升可控性的同时，也引入了新的安全风险，例如相机控制可能被用于生成特定视角的伪造视频。因此，**EntityBench** 和 **PDI-Bench** 的评估标准对于防止此类深度伪造技术的滥用至关重要，它们为后续的安全审计提供了可量化的几何与实体约束指标。

## 视觉推理与幻觉抑制

视觉语言模型在医疗和安防领域的应用日益广泛，但其推理过程的不可解释性和幻觉问题构成了直接的安全隐患。**LATERN: Test-Time Context-Aware Explainable Video Anomaly Detection** 针对视频异常检测任务，提出了上下文感知框架，利用 VLM 的视觉推理能力解决片段级推理缺乏时序结构的问题，从而提供更连贯的异常解释。在医疗诊断领域，**Evidential Reasoning Advances Interpretable Real-World Disease Screening** 引入了 EviScreen 框架，通过检索历史病例的区域级证据来增强疾病筛查的可解释性，这种基于证据的推理路径对于临床决策的安全性至关重要。

针对大视觉语言模型普遍存在的幻觉问题，**MHSA: A Lightweight Framework for Mitigating Hallucinations via Steered Attention in LVLMs** 提出了一种通过引导注意力来纠正跨模态注意力模式的方法，旨在从生成端而非检测端解决不一致内容。与之相呼应，**SteerSeg: Attention Steering for Reasoning Video Segmentation** 则专注于视频推理分割任务，通过识别并修正注意力图来改善空间定位的模糊性。这些工作表明，单纯依赖模型输出是不够的，必须通过干预中间表示（如注意力图或证据检索）来确保推理的忠实度。相比之下，**ATLAS: Agentic or Latent Visual Reasoning? One Word is Enough for Both** 探讨了视觉推理中代理模式与潜在模式的权衡，指出直接生成图像的计算成本与代理模式的外部执行延迟之间的平衡点，这为构建更安全的推理架构提供了理论参考。

## 持续学习与模型更新安全

在模型持续迭代的过程中，如何防止灾难性遗忘并确保新知识的安全注入是安全研究的核心议题。**ACE-LoRA: Adaptive Orthogonal Decoupling for Continual Image Editing** 提出了一种动态正则化框架，利用自适应正交解耦来识别并正交化任务干扰，有效缓解了图像编辑任务中的灾难性遗忘。在更广泛的 multimodal 大语言模型领域，**Octopus: History-Free Gradient Orthogonalization for Continual Learning in Multimodal Large Language Models** 引入了无历史梯度正交化方法，避免了基于重放的隐私泄露风险，同时解决了传统正则化策略在参数干扰上的不足。

这两项工作在持续学习的安全性上采取了不同的技术路径，ACE-LoRA 侧重于参数空间的正交化以保护旧知识，而 Octopus 则通过梯度层面的正交化来减少对新任务的干扰。它们的共同点在于都试图在不存储历史数据的前提下实现知识的累积，这对于保护用户隐私数据至关重要。然而，持续学习本身也带来了新的攻击面，例如通过特定任务注入后门或破坏模型原有的安全对齐。因此，**ACE-LoRA** 和 **Octopus** 的评估不仅应关注性能指标，还应包含对模型鲁棒性和对齐稳定性的安全审计，特别是在多任务场景下，防止任务间的负面迁移导致安全策略失效。

## 安全基准与代理工具链

随着 AI 代理（Agent）在金融和自动化任务中的普及，其潜在的安全风险日益凸显。**ExploitBench** 作为一个开源项目，旨在衡量 AI 代理从访问漏洞代码到执行任意代码的能力，为评估代理的安全边界提供了量化标准。在工具链方面，**CloakBrowser** 提供了一套反检测浏览器工具，支持指纹伪造和会话隔离，虽然其初衷可能用于隐私保护，但也可能被用于规避安全监控或进行自动化攻击。此外，多个开源项目如 **TradingAgents-astock** 和 **kalshi-trading-bot** 展示了多智能体在金融交易中的应用，这些系统涉及高风险的自动化决策，其内部逻辑的透明度和风险控制机制需要严格审查。

在安全工具的开发上，**jupyter-studio** 和 **native-feel-skill** 等开源项目致力于构建更安全的开发环境，强调本地优先和隐私保护。然而，像 **anansi** 这样的自愈网络爬虫工具，虽然提高了数据采集效率，但也可能绕过网站的安全防护机制。这些工具的存在表明，AI 安全研究不仅要关注模型本身，还要关注其运行环境和交互接口。对于金融类代理，**TradingAgents-astock** 和 **kalshi-trading-bot** 的多智能体辩论机制虽然旨在降低风险，但缺乏独立的第三方审计，其决策逻辑的透明度仍需验证。因此，**ExploitBench** 的引入为评估此类代理的破坏性能力提供了必要的基准，建议将其纳入常规的安全测试流程中。

## 治理与行业动态

在政策与治理层面，**ArXiv will ban authors for a year if they let AI do all the work** 的举措反映了学术界对生成式 AI 滥用的警惕，这有助于维护科研诚信，但也引发了关于 AI 辅助写作边界的讨论。OpenAI 方面，**OpenAI co-founder Greg Brockman takes charge of product strategy** 显示公司内部战略调整，而 **OpenAI 与马耳他达成协议，所有马耳他民众都能使用 ChatGPT Plus** 则展示了 AI 服务在特定地区的普及策略。对于中文科技媒体关于 **3 个人带 100 个 AI 程序员，一个月烧掉 130 万美元** 的报道，需谨慎对待，此类数据缺乏官方财务审计支持，可能属于夸大宣传，不应作为评估 AI 经济效率的可靠依据。

此外，**SpaceX 加速驶入纳斯达克** 和 **杭州机器人展** 等产业新闻虽然展示了 AI 硬件和基础设施的发展，但其中涉及的安全标准尚未明确。例如，人形机器人产业链的爆发式增长伴随着物理安全标准的缺失，而 Token 工厂的落地则引发了对算力能源消耗和环境影响的担忧。在治理方面，**PlaceNL2026/okx-agent-trade-kit** 和 **open-gitagent/langship.sh** 等开源项目试图建立代理的治理框架，但目前的治理机制多依赖于社区共识，缺乏强制性的安全规范。因此，行业在追求效率的同时，应建立更严格的合规审查机制，确保 AI 系统的部署符合安全与伦理标准。

## Looking Forward

尽管当日研究在视频评估、幻觉抑制和持续学习方面取得了进展，但仍存在若干未解决的理论问题。首先，视频世界模型的几何一致性评估标准尚未统一，**PDI-Bench** 与 **EntityBench** 的指标如何协同工作以全面覆盖安全风险仍需验证。其次，持续学习中的灾难性遗忘缓解方法在极端任务分布下的鲁棒性尚不明确，**ACE-LoRA** 和 **Octopus** 在大规模多模态场景下的安全性需要更多实证研究。最后，AI 代理的治理框架仍处于早期阶段，**ExploitBench** 等安全基准如何与现有的合规标准对接，以及如何在保护隐私的同时实现有效的安全审计，是未来需要重点攻克的难题。建议后续研究关注跨模态攻击的防御机制，以及建立更透明的 AI 供应链安全评估体系。

---


## 参考来源

- **LATERN: Test-Time Context-Aware Explainable Video Anomaly Detection** — [arxiv_cv](https://arxiv.org/abs/2605.15054v1)
- **EntityBench: Towards Entity-Consistent Long-Range Multi-Shot Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.15199v1)
- **ATLAS: Agentic or Latent Visual Reasoning? One Word is Enough for Both** — [arxiv_cv](https://arxiv.org/abs/2605.15198v1)
- **VGGT-$Ω$** — [arxiv_cv](https://arxiv.org/abs/2605.15195v1)
- **Aligning Latent Geometry for Spherical Flow Matching in Image Generation** — [arxiv_cv](https://arxiv.org/abs/2605.15193v1)
- **RAVEN: Real-time Autoregressive Video Extrapolation with Consistency-model GRPO** — [arxiv_cv](https://arxiv.org/abs/2605.15190v1)
- **Quantitative Video World Model Evaluation for Geometric-Consistency** — [arxiv_cv](https://arxiv.org/abs/2605.15185v1)
- **Warp-as-History: Generalizable Camera-Controlled Video Generation from One Training Video** — [arxiv_cv](https://arxiv.org/abs/2605.15182v1)
- **Evidential Reasoning Advances Interpretable Real-World Disease Screening** — [arxiv_cv](https://arxiv.org/abs/2605.15171v1)
- **Computational Imaging Priors for Wireless Capsule Endoscopy: Monte Carlo-Guided Hemoglobin Mapping for Rare-Anomaly Detection** — [arxiv_cv](https://arxiv.org/abs/2605.15062v1)
- **DiffusionOPD: A Unified Perspective of On-Policy Distillation in Diffusion Models** — [arxiv_cv](https://arxiv.org/abs/2605.15055v1)
- **Characterizing the visual representation of objects from the child's view** — [arxiv_cv](https://arxiv.org/abs/2605.14990v1)
- **MHSA: A Lightweight Framework for Mitigating Hallucinations via Steered Attention in LVLMs** — [arxiv_cv](https://arxiv.org/abs/2605.14966v1)
- **Evo-Depth: A Lightweight Depth-Enhanced Vision-Language-Action Model** — [arxiv_cv](https://arxiv.org/abs/2605.14950v1)
- **ACE-LoRA: Adaptive Orthogonal Decoupling for Continual Image Editing** — [arxiv_cv](https://arxiv.org/abs/2605.14948v1)
- **Octopus: History-Free Gradient Orthogonalization for Continual Learning in Multimodal Large Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.14938v1)
- **Multi-scale Coarse-to-fine Modeling for Test-time Human Motion Control** — [arxiv_cv](https://arxiv.org/abs/2605.14935v1)
- **Road Maps as Free Geometric Priors: Weather-Invariant Drone Geo-Localization with GeoFuse** — [arxiv_cv](https://arxiv.org/abs/2605.14925v1)
- **SteerSeg: Attention Steering for Reasoning Video Segmentation** — [arxiv_cv](https://arxiv.org/abs/2605.14908v1)
- **Hierarchical Image Tokenization for Multi-Scale Image Super Resolution** — [arxiv_cv](https://arxiv.org/abs/2605.14891v1)
- **The haves and have nots of the AI gold rush** — [techcrunch_ai](https://techcrunch.com/2026/05/16/the-haves-and-have-nots-of-the-ai-gold-rush/)
- **Research repository ArXiv will ban authors for a year if they let AI do all the work** — [techcrunch_ai](https://techcrunch.com/2026/05/16/research-repository-arxiv-will-ban-authors-for-a-year-if-they-let-ai-do-all-the-work/)
- **OpenAI co-founder Greg Brockman takes charge of product strategy** — [techcrunch_ai](https://techcrunch.com/2026/05/16/openai-co-founder-greg-brockman-reportedly-takes-charge-of-product-strategy/)
- **simonlin1212/TradingAgents-astock** — [github](https://github.com/simonlin1212/TradingAgents-astock)
- **deepelementlab/jupyter-studio** — [github](https://github.com/deepelementlab/jupyter-studio)
- **mdowis/anansi** — [github](https://github.com/mdowis/anansi)
- **EliasOulkadi/shokunin** — [github](https://github.com/EliasOulkadi/shokunin)
- **Siva-Chidambaram12/kalshi-trading-bot** — [github](https://github.com/Siva-Chidambaram12/kalshi-trading-bot)
- **talentsache/aipointer** — [github](https://github.com/talentsache/aipointer)
- **johunsang/semble_rs** — [github](https://github.com/johunsang/semble_rs)
- **ahammadmejbah/Awesome-LLM-Datasets** — [github](https://github.com/ahammadmejbah/Awesome-LLM-Datasets)
- **exploitbench/exploitbench** — [github](https://github.com/exploitbench/exploitbench)
- **PlaceNL2026/okx-agent-trade-kit** — [github](https://github.com/PlaceNL2026/okx-agent-trade-kit)
- **Isoform/yansu-skill** — [github](https://github.com/Isoform/yansu-skill)
- **python-telegramBot/ai-auto-trading** — [github](https://github.com/python-telegramBot/ai-auto-trading)
- **ab-613/OpenGravity** — [github](https://github.com/ab-613/OpenGravity)
- **KenKaneki18/CloakBrowser** — [github](https://github.com/KenKaneki18/CloakBrowser)
- **mikesheehan54/Claude-Code-Design-AI** — [github](https://github.com/mikesheehan54/Claude-Code-Design-AI)
- **yaassin12/DeepSeek-V4-Pro-App** — [github](https://github.com/yaassin12/DeepSeek-V4-Pro-App)
- **yetone/native-feel-skill** — [github](https://github.com/yetone/native-feel-skill)
- **nexu-io/html-anything** — [github](https://github.com/nexu-io/html-anything)
- **deepakness/google-ai-search-optimization** — [github](https://github.com/deepakness/google-ai-search-optimization)
- **open-gitagent/langship.sh** — [github](https://github.com/open-gitagent/langship.sh)
- **龙虾之父月烧940万元的token！要不是入职OpenAI还真用不起** — [qbitai](https://www.qbitai.com/2026/05/418822.html)
- **SFT别急着接RL！你的多模态大模型可能一直在“带伤训练”** — [qbitai](https://www.qbitai.com/2026/05/418814.html)
- **不用再找了，AI落地最全的实战打法，都在亦庄这场大会里** — [qbitai](https://www.qbitai.com/2026/05/418620.html)
- **史上最大IPO来袭，SpaceX加速驶入纳斯达克** — [36kr](https://36kr.com/p/3812789087264519?f=rss)
- **杭州机器人展吸引全球客商“淘”宝，意向合作总金额突破213亿元** — [36kr](https://36kr.com/newsflashes/3812949703073285?f=rss)
- **首个东数西算、算电融合的特大型Token工厂落子无锡** — [36kr](https://36kr.com/newsflashes/3812945055342086?f=rss)
- **3个人带100个AI程序员，一个月烧掉130万美元！OpenAI：钱我出** — [36kr](https://36kr.com/p/3812925591887368?f=rss)
- **韩国SK海力士来锡对接深化合作** — [36kr](https://36kr.com/newsflashes/3812953571565312?f=rss)
- **特斯拉两年来首次上调Model Y美国售价** — [36kr](https://36kr.com/newsflashes/3812950639927048?f=rss)
- **28亿，肯德基也要被卖了？** — [36kr](https://36kr.com/p/3812816225459713?f=rss)
- **宏桥控股：公司2026年预计资本开支约90亿元，目前暂无铝加工板块新增扩张规划** — [36kr](https://36kr.com/newsflashes/3812844853812995?f=rss)
- **6.4k Stars！用Claude Code写论文的全套流水线，有人打包开源了** — [36kr](https://36kr.com/p/3812800346742274?f=rss)
- **阿斯麦与塔塔电子签署谅解备忘录** — [36kr](https://36kr.com/newsflashes/3812704658447875?f=rss)
- **长安汽车否认与千里科技合作** — [36kr](https://36kr.com/newsflashes/3812843633991425?f=rss)
- **36氪首发 | 宠物健康大模型公司连融两轮，软硬一体化布局，已服务超200家宠物医院** — [36kr](https://36kr.com/p/3812788568907520?f=rss)
- **48022桌需退款，这家网红店出了什么事？** — [36kr](https://36kr.com/p/3812706162220548?f=rss)
- **传三星Exynos 2700芯片正考虑放弃FOWLP先进封装工艺** — [36kr](https://36kr.com/newsflashes/3813031303372293?f=rss)
- **韩国头部企业一季度营业利润突破千亿美元，超六成来自三星海力士** — [36kr](https://36kr.com/newsflashes/3812848957529860?f=rss)
- **摩尔线程与国家具身智能应用中试基地签署战略合作协议** — [36kr](https://36kr.com/newsflashes/3812778475167490?f=rss)
- **OpenAI与马耳他达成协议，所有马耳他民众都能使用ChatGPT Plus** — [36kr](https://36kr.com/newsflashes/3812703324249856?f=rss)