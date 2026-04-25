# AI 日报 [AI 安全] - 2026-04-25


# AI 安全与治理日报：2026 年 4 月 25 日

## Highlights

今日 AI 安全领域最显著的技术进展在于**开源前沿模型**与**自主 Agent 治理框架**的双重突破。DeepSeek 正式预览发布 **V4** 模型，其开源策略与 1M 上下文窗口能力引发了关于“开放模型安全风险”的新一轮讨论，特别是其基于华为昇腾芯片的迁移路径对供应链安全的影响。与此同时，开源社区涌现出一批针对 Agent 执行层的安全控制工具，如 **Polaris** 事务驱动内核与 **agents-md** 行为约束规范，标志着 Agent 安全从单纯的“提示词工程”向“系统级审计与回滚”演进。此外，**How Project Maven taught the military to love AI** 等报道揭示了军事领域 AI 决策加速带来的伦理风险，与 **The Download: supercharged scams and studying AI healthcare** 中提到的医疗 AI 效能不确定性形成对比，凸显了技术落地中的安全评估缺口。

---

## 前沿模型安全与开源生态博弈

DeepSeek 在 2026 年 4 月 24 日发布的 **V4** 模型预览版，不仅是性能上的迭代，更是开源安全生态的分水岭。根据 **Three reasons why DeepSeek’s new model matters** 的分析，V4 通过稀疏注意力机制 DSA 和 MoE 架构，在保持长上下文（1M tokens）的同时显著降低了计算成本，且完全开源。这一举动打破了以往闭源模型在推理能力上的垄断，但也带来了新的安全挑战：开源权重使得红队测试（Red Teaming）的门槛降低，潜在的攻击面扩大。相比之下，Google 计划向 Anthropic 投资高达 400 亿美元以巩固算力与模型壁垒，这种资本密集型的闭源路径试图通过控制算力来维持安全边界，而 DeepSeek 的开源路径则试图通过社区协作来分散风险。

在模型对齐理论方面，开源社区并未止步于模型权重的发布，而是开始关注推理过程的可控性。DeepSeek V4 针对 Agent 的性能优化暗示了其原生支持自主任务规划，这与 **DeepSeek V4 终于发布，但它留下的 5 道主观题还没有答案** 中提到的“主观题无答案”形成张力。开源模型赋予了开发者更高的自由度，但也要求开发者具备更强的安全对齐能力。目前，学术界与产业界对于开源模型的安全评估标准尚未统一，V4 的发布迫使评估基准（Benchmarks）必须更新以涵盖长上下文下的逻辑一致性与指令遵循安全性。

---

## Agent 安全与治理框架的演进

随着 AI Agent 从简单的对话助手向自主软件工厂演进，安全治理的重心正从“输入端”向“执行端”转移。GitHub 上的 **Polaris** 项目提供了一个事务驱动的 AI 软件工厂内核，其核心创新在于将 LLM 降级为受限决策组件，由系统内核统一接管执行、审计、预算与回滚。这与传统的 Agent 框架（如 **Hermes-agent-guide** 或 **kimi-K2.6**）有本质区别，后者更多侧重于任务编排与技能调用，而 Polaris 引入了类似数据库事务的 ACID 特性，确保 Agent 操作的可追溯性与可回滚性，解决了自主 Agent 在复杂工程任务中“越权执行”或“死循环”的安全隐患。

在行为约束层面，**agents-md** 提出了一种“即插即用”的规范，旨在让编码 Agent 表现得像高级工程师而非急于求成的实习生。它通过强制验证循环（Verification Loops）和消除阿谀奉承（Sycophancy），试图在 Prompt 层面解决对齐问题。这与 **design-council** 中提出的“多角色辩论”机制形成互补：后者通过让 11 个角色化 Agent 实时辩论技术决策来模拟人类评审团，侧重于决策前的逻辑校验；而 agents-md 侧重于执行过程中的行为修正。此外，**future-agi** 平台提供了端到端的评估、观测与改进工具，涵盖了 Guardrails 与 Tracing，试图构建一个闭环的安全观测体系。

这些工具的共同趋势是“去黑盒化”。无论是 Polaris 的权力分离架构（PM/Architect/Director/QA），还是 design-council 的辩论机制，都在试图将 Agent 的决策过程显性化。然而，不同工作之间存在方法论的矛盾：agents-md 依赖 Prompt 工程与外部规范，而 Polaris 依赖底层系统架构的改造。前者部署灵活但可能绕过约束，后者安全但侵入性强。未来的研究方向可能在于如何将 Polaris 的事务审计机制与 agents-md 的行为规范相结合，形成一套标准化的 Agent 安全中间件。

---

## 隐私保护与边缘计算安全

随着本地 AI 需求的激增，隐私计算与边缘部署成为安全研究的新热点。Apple 新 CEO 上任背景下的硬件生态变化，叠加 Mac mini 因运行本地 AI 模型而引发的短缺，反映了用户对数据主权的需求。**ovo-local-llm** 项目提供了一个基于 Apple Silicon 的本地 Claude-Code 风格编码 Agent，强调 MLX 原生支持与零 API Key，旨在消除云端数据泄露风险。这与 **vela** 项目（AI 驱动的隐私优先 IDE）形成呼应，后者通过本地 LLM + RAG 架构，确保创意写作与代码生成的数据不出本地。

在联邦学习与隐私计算方面，虽然今日新闻中未直接提及最新的联邦学习算法论文，但 **Nothing 推出的 AI 驱动听写工具** 支持 100 多种语言且强调端侧处理，暗示了多语言场景下的隐私保护架构正在向端侧迁移。然而，这种迁移也带来了新的安全挑战：本地模型可能更容易受到物理访问攻击或模型窃取。此外，**ComfyUI** 估值达到 5 亿美元，反映了创作者对生成内容控制权的渴望，这背后是对生成内容版权与隐私泄露的担忧。未来的隐私保护研究需关注如何在本地受限算力下实现有效的差分隐私（Differential Privacy）与同态加密，同时保证 Agent 的推理性能。

---

## 现实世界风险与治理挑战

AI 技术的落地不仅涉及代码安全，更关乎物理世界与社会的稳定。 **How Project Maven taught the military to love AI** 揭示了美军在伊朗行动中利用 AI 系统加速目标识别与打击，这种军事 AI 的自动化程度提升引发了关于“致命性自主武器系统”（LAWS）的伦理担忧。与民用领域的 **The Download: supercharged scams and studying AI healthcare** 中提到的 AI 诈骗升级与医疗 AI 疗效不明相比，军事 AI 的风险更具即时性与破坏性。医疗 AI 虽然尚未证明能切实帮助患者，但其误诊风险可能导致法律责任归属的模糊，这要求建立更严格的医疗 AI 责任框架。

在金融与交易领域，**kalshi trading bot** 展示了多 Agent 集成在预测市场中的应用，利用 Kelly 准则进行仓位管理。虽然这展示了 Agent 的自主决策能力，但也暴露了算法交易中的系统性风险。如果多个 Agent 同时基于相似信号行动，可能引发市场闪崩。此外，**上交所修订发布《上海证券交易所交易规则》** 与 **深交所修订主板、创业板《股票上市规则》** 等政策变化，虽然主要针对证券交易制度，但其中关于董秘职责与高管履职监管的强化，间接要求上市公司在 AI 应用（如 AI 交易系统）中建立更完善的治理结构。

---

## Looking Forward

尽管开源模型与 Agent 治理工具取得了显著进展，但以下理论问题与假设仍需验证：

1.  **开源模型的安全审计标准**：DeepSeek V4 的开源是否意味着安全责任的转移？目前缺乏针对开源大模型的自动化红队测试基准，如何量化评估开源模型被恶意利用的风险？
2.  **Agent 事务一致性的理论边界**：Polaris 提出的事务驱动架构在复杂动态环境中（如网络延迟、外部 API 变更）能否保证原子性？现有的数据库事务理论是否足以支撑 AI Agent 的自主决策回滚？
3.  **多 Agent 协作的涌现风险**：design-council 与 Hermes 等多 Agent 框架在协作中可能产生不可预测的涌现行为（Emergent Behavior），如何从理论上证明多 Agent 系统的稳定性与对齐性？
4.  **边缘 AI 的侧信道攻击**：随着本地 LLM 的普及，针对硬件（如 Apple Silicon）的侧信道攻击与模型窃取技术将成为新的研究前沿，现有的隐私保护协议是否足以应对物理层面的威胁？

未来的研究需从单纯的模型性能优化转向系统级的安全验证，建立涵盖开源模型、Agent 执行环境及物理部署的全栈安全评估体系。

---


## 参考来源

- **Three reasons why DeepSeek’s new model matters** — [mit_tech_review](https://www.technologyreview.com/2026/04/24/1136422/why-deepseeks-v4-matters/)
- **8 Gemini tips for organizing your space (and life)** — [google_ai](https://blog.google/products-and-platforms/products/gemini/gemini-spring-cleaning-tips/)
- **Google to invest up to $40B in Anthropic in cash and compute** — [techcrunch_ai](https://techcrunch.com/2026/04/24/google-to-invest-up-to-40b-in-anthropic-in-cash-and-compute/)
- **Apple’s new CEO, and why Elon Musk wants to buy Cursor for $60B** — [techcrunch_ai](https://techcrunch.com/podcast/apples-new-ceo-and-why-elon-musk-wants-to-buy-cursor-for-60b/)
- **Marked-up Mac minis flood eBay amid shortages driven by AI** — [techcrunch_ai](https://techcrunch.com/2026/04/24/mac-mini-price-expensive-ebay-shortage-ai-memory/)
- **How Project Maven taught the military to love AI** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/917996/project-maven-military-ai-katrina-manson)
- **The Download: supercharged scams and studying AI healthcare** — [mit_tech_review](https://www.technologyreview.com/2026/04/24/1136400/the-download-supercharged-scams-questionable-ai-healthcare/)
- **Uber CTO Praveen Neppalli Naga joins stacked StrictlyVC SF lineup for April 30 event** — [techcrunch_ai](https://techcrunch.com/2026/04/24/uber-cto-praveen-neppalli-naga-joins-stacked-strictlyvc-sf-lineup-for-april-30-event/)
- **Tim Cook is stepping down. What happens to Apple now?** — [techcrunch_ai](https://techcrunch.com/video/tim-cook-is-stepping-down-what-happens-to-apple-now/)
- **DeepSeek previews new AI model that ‘closes the gap’ with frontier models** — [techcrunch_ai](https://techcrunch.com/2026/04/24/deepseek-previews-new-ai-model-that-closes-the-gap-with-frontier-models/)
- **AirPods, Touch Bars, and the rest of Tim Cook&#8217;s legacy** — [theverge_ai](https://www.theverge.com/podcast/917965/apple-ceo-cook-ternus-transition)
- **Musk vs. Altman is here, and it&#8217;s going to get messy** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/917755/musk-altman-openai-xai-gossip)
- **China’s DeepSeek previews new AI model a year after jolting US rivals** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/918035/deepseek-preview-v4-ai-model)
- **Prestigious photo contest answers ‘what is a photo?’** — [theverge_ai](https://www.theverge.com/gadgets/918016/prestigious-photo-contest-answers-what-is-a-photo)
- **Health-care AI is here. We don’t know if it actually helps patients.** — [mit_tech_review](https://www.technologyreview.com/2026/04/24/1136352/health-care-ai-dont-know-actually-helps-patients/)
- **Meta’s loss is Thinking Machines’ gain** — [techcrunch_ai](https://techcrunch.com/2026/04/24/metas-loss-is-thinking-machines-gain/)
- **ComfyUI hits $500M valuation as creators seek more control over AI-generated media** — [techcrunch_ai](https://techcrunch.com/2026/04/24/comfyui-hits-500m-valuation-as-creators-seek-more-control-over-ai-generated-media/)
- **Nothing introduces an AI-powered dictation tool** — [techcrunch_ai](https://techcrunch.com/2026/04/24/nothing-introduces-an-ai-powered-dictation-tool/)
- **In another wild turn for AI chips, Meta signs deal for millions of Amazon AI CPUs** — [techcrunch_ai](https://techcrunch.com/2026/04/24/in-another-wild-turn-for-ai-chips-meta-signs-deal-for-millions-of-amazon-ai-cpus/)
- **sjsyrek/design-council** — [github](https://github.com/sjsyrek/design-council)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **linedelmont81825829134/LLM-Prompt-Orchestration-Engine** — [github](https://github.com/linedelmont81825829134/LLM-Prompt-Orchestration-Engine)
- **selmakcby/claude-agents-skills** — [github](https://github.com/selmakcby/claude-agents-skills)
- **kimi-K2-6/kimi-K2.6** — [github](https://github.com/kimi-K2-6/kimi-K2.6)
- **jwangkun/hermes-agent-guide** — [github](https://github.com/jwangkun/hermes-agent-guide)
- **dainsiahtill-dev/Polaris** — [github](https://github.com/dainsiahtill-dev/Polaris)
- **chaohong-ai/ai-auto-work** — [github](https://github.com/chaohong-ai/ai-auto-work)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **muxprotocol/kalshi-trading-bot** — [github](https://github.com/muxprotocol/kalshi-trading-bot)
- **intertwine/dspy-agent-skills** — [github](https://github.com/intertwine/dspy-agent-skills)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **TheRealSeanDonahoe/agents-md** — [github](https://github.com/TheRealSeanDonahoe/agents-md)
- **alchaincyf/huashu-design** — [github](https://github.com/alchaincyf/huashu-design)
- **低头是日常，抬头是阅读** — [36kr](https://36kr.com/p/3780986341153798?f=rss)
- **最前线｜AI+激光通信，中科天塔要用「太空智驾」体系实现卫星管理模式的三级跨越** — [36kr](https://36kr.com/p/3780910411193602?f=rss)
- **豆神教育：澄清一季度财报不实信息，报告尚在编制中** — [36kr](https://36kr.com/newsflashes/3780811173567491?f=rss)
- **找钢网集团：上市以来累计出资约4090.26万港币回购公司股份** — [36kr](https://36kr.com/newsflashes/3780788529716228?f=rss)
- **永辉超市CEO王守诚：调改已步入第二阶段** — [36kr](https://36kr.com/newsflashes/3780777463504128?f=rss)
- **ST新华锦：申请撤销部分其他风险警示** — [36kr](https://36kr.com/newsflashes/3780774441131009?f=rss)
- **阿里云百炼上线DeepSeek-V4** — [36kr](https://36kr.com/newsflashes/3780771345472515?f=rss)
- **鹏鼎控股：控股股东及一致行动人拟合计减持不超1.73%股份** — [36kr](https://36kr.com/newsflashes/3780763532647427?f=rss)
- **上交所修订发布《上海证券交易所交易规则》，7月6日起正式实施** — [36kr](https://36kr.com/newsflashes/3780766597897223?f=rss)
- **深交所修订主板、创业板《股票上市规则》和《规范运作指引》** — [36kr](https://36kr.com/newsflashes/3780765831781633?f=rss)
- **氪星晚报｜美团万亿级参数大模型开放测试，训练全程由国产算力集群完成；百度联盟正式发布海外App业务；央行等八部门发布金融产品网络营销管理办法** — [36kr](https://36kr.com/p/3777694346548482?f=rss)
- **科氪|高配不溢价，20万内首选！国民好车2.0深蓝L06增程版折后价低至127155元起** — [36kr](https://36kr.com/p/3780654186535941?f=rss)
- **最前线｜AI收入破亿后的路径选择：微盟推行AI First战略与B端交付的挑战** — [36kr](https://36kr.com/p/3780556402531330?f=rss)
- **DeepSeek V4终于发布，但它留下的5道主观题还没有答案** — [36kr](https://36kr.com/p/3780375304312072?f=rss)
- **融了2000万美金，这家2000万美金ARR的AI公司，推出“视频版Photoshop”「Buzzy」** — [36kr](https://36kr.com/p/3780352721851397?f=rss)
- **茅台向经销商「要利润」** — [36kr](https://36kr.com/p/3780191213229314?f=rss)
- **用“活人感”做科技社区，小红书能成吗？** — [36kr](https://36kr.com/p/3778772970444033?f=rss)
- **博裕、经纬、顺为等投资前新石器COO超亿元，押注AI超便携电子纸｜硬氪独家** — [36kr](https://36kr.com/p/3778175428777218?f=rss)
- **simonw/llm-openai-via-codex** — [github](https://github.com/simonw/llm-openai-via-codex)
- **dexwritescode/neurons** — [github](https://github.com/dexwritescode/neurons)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **YilmazKadir/Volt** — [github](https://github.com/YilmazKadir/Volt)
- **realZillionX/InspireSkill** — [github](https://github.com/realZillionX/InspireSkill)
- **g2i-ai/agents** — [github](https://github.com/g2i-ai/agents)
- **热门中概股美股盘前多数上涨，理想汽车跌近4%** — [36kr](https://36kr.com/newsflashes/3780829195590658?f=rss)
- **美股大型科技股盘前普涨，英特尔涨超25%** — [36kr](https://36kr.com/newsflashes/3780822122732550?f=rss)
- **Mobileye 2026财年一季度营收增长27%，自动驾驶商业化进程持续推进** — [qbitai](https://www.qbitai.com/2026/04/406775.html)
- **100%主流车企的共同选择：一个AI“通用底座”正在汽车行业成型** — [qbitai](https://www.qbitai.com/2026/04/406767.html)
- **真有人做AI小猫啊？！生产力和情绪价值都拉满了** — [qbitai](https://www.qbitai.com/2026/04/406560.html)
- **Coordination Engineering关键一环，JiuwenClaw再发布Team Skills技能新范式** — [qbitai](https://www.qbitai.com/2026/04/406393.html)
- **DeepSeek V4终于发布！打破最强闭源垄断，明确携手华为芯片** — [qbitai](https://www.qbitai.com/2026/04/406359.html)
- **荣耀WIN游戏本等多款新品正式发布，荣耀PC家族全面爆发** — [qbitai](https://www.qbitai.com/2026/04/406402.html)
- **优必选发布Thinker cosmos：加码开发者生态，推动人形机器人走向规模化** — [qbitai](https://www.qbitai.com/2026/04/406806.html)
- **PPIO首批上线DeepSeek-V4预览版，1M超长上下文能力开箱即用** — [qbitai](https://www.qbitai.com/2026/04/406802.html)
- **DeepSeek-V4发布，华为云首发适配** — [qbitai](https://www.qbitai.com/2026/04/406791.html)