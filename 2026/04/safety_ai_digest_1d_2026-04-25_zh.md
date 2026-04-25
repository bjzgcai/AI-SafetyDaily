# AI 日报 [AI 安全] - 2026-04-25


# AI 安全与治理日报：2026-04-25

## Highlights

今日 AI 安全与治理领域呈现出“开源模型边界拓展”与“智能体安全基建”并行的态势。最核心的进展在于 **DeepSeek V4** 的开源发布，其 1M 上下文窗口与混合专家架构（MoE）在提升推理效率的同时，引发了对长上下文安全边界与开源模型对齐验证的新讨论。与此同时，开源社区涌现出一批针对 Agent 安全性的基础设施工具，如 **Polaris** 事务驱动内核与 **Agents.md** 行为对齐规范，标志着智能体安全从“对话层”向“执行层”的防御纵深延伸。在治理层面，上交所与深交所修订交易规则强化董秘职责，以及美军 Project Maven 系统的实战化应用，进一步凸显了 AI 在金融与军事领域的合规与杀伤链控制风险。

---

## 开源模型的安全边界与治理

随着 **DeepSeek V4** 的正式预览，开源模型在性能上已逼近甚至部分超越闭源系统，这一里程碑事件将安全研究的焦点从“能力差距”转移至“风险敞口”。该模型基于 MoE 架构与稀疏注意力机制 DSA，实现了 1.6T 参数规模下的 1M 上下文处理，并完成了从英伟达到华为昇腾芯片的训练框架迁移。这种架构创新虽然降低了计算成本，但也带来了新的安全挑战：长上下文窗口（1M tokens）极易成为 Prompt Injection 与 Context Poisoning 的温床，攻击者可能利用超长历史记忆注入恶意指令，绕过传统的上下文过滤机制。

与 DeepSeek V4 的开源策略形成对比的是，Google 计划向 Anthropic 投资高达 400 亿美元以锁定算力资源，这反映了头部厂商在算力安全上的“围墙花园”策略。这种算力集中化趋势可能导致安全评估资源的垄断，使得开源社区在对抗性测试与红队演练上处于劣势。此外，DeepSeek V4 的发布也引发了对供应链安全的关注，其训练框架的国产化迁移（华为昇腾）虽然解决了算力卡脖子问题，但也意味着安全审计标准需从 CUDA 生态向国产硬件生态适配，现有的安全工具链可能面临兼容性失效的风险。

## 智能体安全与可验证性

智能体（Agent）从“辅助工具”向“自主执行者”演进的过程中，安全验证机制的缺失已成为行业痛点。今日开源社区涌现的多个项目试图填补这一空白，其中 **Polaris** 事务驱动的 AI 软件工厂内核尤为引人注目。Polaris 将 LLM 降级为受限决策组件，通过 KernelOne 底座与 ContextOS 三层记忆系统，实现了企业级的无人值守交付流水线。其核心创新在于引入了“三省六部”权力分离架构（PM/Architect/Director/QA），强制将执行、审计、预算与回滚权限分离，这在理论上解决了 Agent 越权执行与不可回滚的致命风险。

相比之下，**Agents.md** 则侧重于行为对齐与提示工程层面的防御。该工具通过合成 Karpathy 的四个原则与 Boris Cherny 的工作流，强制 Agent 在编码过程中执行验证循环，抑制“奉承性”（Sycophancy）与未经授权的 Refactor。这种“软性”对齐策略与 Polaris 的“硬性”内核控制形成了互补：前者通过规范提示词与交互逻辑减少幻觉，后者通过系统架构限制执行权限。此外，**Hermes Agent** 框架与 **design-council** 插件进一步扩展了多智能体协作的安全边界，通过引入角色专门化的 Peer Agents 辩论机制，在技术决策阶段引入对抗性验证，试图在代码生成前解决逻辑漏洞。这些工具共同指向一个趋势：Agent 安全不再依赖单一模型，而是需要构建包含审计、回滚、权限隔离与对抗验证的完整生态系统。

## 隐私计算与端侧安全

在数据隐私保护方面，端侧计算（On-device Computing）正成为对抗数据泄露与云端监控的关键防线。Apple 新 CEO John Ternus 上任前夕，Mac mini 因本地运行 AI 模型的需求而供不应求，这一现象折射出市场对隐私敏感型 AI 应用的强烈需求。配合 **ovo-local-llm** 等开源项目的发布，用户可以在 Apple Silicon 上运行本地 Claude-Code 风格的 Agent，无需 API Key 即可实现零数据外泄的编码与推理工作。这种“本地优先”的架构设计，从物理层面切断了云端模型对私有代码与数据的访问路径。

然而，端侧安全并非无懈可击。随着 **Nothing** 等厂商推出支持百种语言的本地语音工具，以及 **ComfyUI** 等媒体生成工具估值突破 5 亿美元，本地模型的可信执行环境（TEE）与模型完整性验证成为新的研究课题。如果本地模型被篡改或注入后门，端侧设备可能成为数据泄露的源头。因此，未来的隐私计算研究需从单纯的“数据不出域”转向“模型可信与执行环境隔离”的双重保障。

## 行业治理与政策监管

AI 治理的边界正从技术层面延伸至金融与军事领域。上交所与深交所近期修订发布的《股票交易规则》与《上市规则》，明确要求强化董秘在 AI 信息披露与治理合规中的职责，这标志着 AI 应用风险已被纳入上市公司合规监管的核心范畴。规则中关于“董秘履职嵌入日常经营”与“控股股东同业竞争披露”的细化，为 AI 驱动的企业决策提供了制度性约束，防止算法黑箱导致的财务造假或内幕交易。

在军事安全领域，**Project Maven** 系统的实战化应用揭示了 AI 在杀伤链中的加速效应。在针对伊朗的突袭中，AI 系统使目标打击速度翻倍，这引发了对“算法战争”伦理的深层担忧。当 AI 能够自主加速目标识别与打击流程时，人类在环（Human-in-the-loop）的控制机制是否依然有效？此外，**AI 驱动诈骗**（AI-driven scams）的升级也表明，安全防御必须从被动响应转向主动对抗，特别是在金融营销与网络安全领域，八部门联合发布的《金融产品网络营销管理办法》正是对此类风险的制度化回应。

## Looking Forward

尽管今日在 Agent 安全工具与开源模型发布上取得了显著进展，但理论层面的未解问题依然严峻。首先，**长上下文安全验证** 仍缺乏标准化的基准测试，1M tokens 的上下文窗口是否意味着攻击面的指数级扩大，尚需形式化验证方法的介入。其次，**多智能体协作的问责机制** 尚未建立，当 Polaris 或 Hermes 等框架中的多个 Agent 协同决策导致事故时，责任归属在技术架构与法律层面均存在真空。最后，**开源模型的对齐可验证性** 仍是悬而未决的难题，DeepSeek V4 的开源虽然促进了技术民主化，但如何确保其权重文件在分发过程中未被篡改，且其对齐策略在开放环境下依然有效，需要社区建立更完善的模型指纹与审计协议。未来的研究需重点关注如何在保持模型开放性的同时，构建可验证的安全沙箱与动态防御体系。

---


## 参考来源

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