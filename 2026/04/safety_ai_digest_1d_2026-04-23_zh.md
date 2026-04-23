# AI 日报 [AI 安全] - 2026-04-23


# AI Safety Thematic Digest: 2026-04-23

## Highlights

今日 AI 安全与治理领域呈现出“激进部署”与“严峻风险”并存的态势。最引人注目的安全事件是 **Anthropic’s most dangerous AI model just fell into the wrong hands**，其新发布的网络安全模型 Mythos 被未经授权的用户获取，暴露了前沿模型在供应链分发环节的巨大漏洞。与此同时，**Now Meta will track what employees do on their computers to train its AI agents** 揭示了企业级数据收集边界的模糊化，引发了关于员工隐私与数据主权的伦理争议。在技术架构层面，**Introducing workspace agents in ChatGPT** 与 **Speeding up agentic workflows with WebSockets in the Responses API** 标志着 Agent 从对话辅助向自主工作流执行的转变，这对现有的安全围栏提出了新的性能与逻辑挑战。

---

## Agent 安全与治理：自主性的双刃剑

随着大模型从被动问答转向主动执行，Agent 的安全治理已成为今日讨论的核心。OpenAI 推出的 **Introducing workspace agents in ChatGPT** 允许企业级用户部署可自主执行复杂工作流的云端 Agent，这虽然提升了生产力，但也扩大了攻击面。OpenAI 在 **Speeding up agentic workflows with WebSockets in the Responses API** 中通过 WebSocket 和连接级缓存优化了 Agent 循环的延迟，这种性能优化在提升响应速度的同时，也意味着 Agent 在做出决策前可供人类干预的时间窗口被进一步压缩。

针对这一趋势，开源社区正在涌现一批旨在增强 Agent 可控性的工具。**Polaris 是一个事务驱动的 AI 软件工厂内核**，它并未将 LLM 视为聊天助手，而是将其降级为受限决策组件，由系统内核统一接管执行、审计与回滚。这种“内核接管”的思路与 **agents-md** 形成了鲜明对比，后者通过标准化的 `AGENTS.md` 文件来规范 Agent 行为，旨在消除顺从性（sycophancy）并强制验证循环。两者在治理层级上互补：`agents-md` 侧重于提示词与行为规范的标准化，而 Polaris 则从系统架构层面实现了执行与审计的分离。此外，**skill-doctor** 作为一个本地优先的编码 Agent 技能检查器，专注于分析技能冲突与风险评估，为 Agent 技能库的审计提供了细粒度工具。

然而，现实中的安全防线仍显脆弱。**Anthropic’s most dangerous AI model just fell into the wrong hands** 报道指出，Anthropic 的 Mythos 模型被第三方承包商泄露给非授权用户。这一事件与 Anthropic 此前声称的 Mythos 是“危险工具”形成讽刺性对照，表明即便有严格的访问控制，供应链中的信任链（Supply Chain Trust）依然可能被内部人员或承包商突破。这提示我们，单纯的模型访问控制已不足以应对风险，必须结合类似 Polaris 的系统级审计机制，确保 Agent 在失控前能被强制回滚。

## 隐私保护与数据主权：企业监控与本地化对抗

在数据层面，企业利用 AI 训练的需求与个人隐私保护之间的张力日益加剧。**Now Meta will track what employees do on their computers to train its AI agents** 披露了 Meta 正在安装 MCI 工具，记录员工在办公电脑上的鼠标移动、点击及截图，用于训练其 Agent。这种做法将员工工作数据直接纳入模型训练集，不仅涉及劳动伦理问题，更触犯了数据最小化原则。这种“全量采集”的模式与当前隐私计算的趋势背道而驰。

作为对抗性方案，开源社区提供了多种隐私优先的本地化工具。**vela** 是一个 AI 驱动的 IDE，采用本地 LLM 加 RAG 架构，强调隐私优先和 BYOK（Bring Your Own Key），专为网络小说作者等对隐私敏感的用户设计。**ovo-local-llm** 则进一步在 Apple Silicon 上实现了本地化的 Claude Code 风格 Agent，无需 API Key 即可运行代码与对话工作流。这些工具的核心价值在于将数据处理留在本地（Local-first），切断了数据向云端大模型厂商的单向流动。

对比 Meta 的云端监控模式与 vela/ovo 的本地化模式，可以看出数据主权正在从“平台中心”向“用户中心”转移。然而，本地化也带来了新的安全挑战，如 **windbg-decompile-ext** 所示，利用 LLM 对实时函数进行反编译和伪代码生成，虽然提升了逆向工程效率，但也可能被用于恶意软件分析或漏洞挖掘。这要求隐私保护工具不仅要防止数据泄露，还需防止本地模型被滥用。

## 鲁棒性与评估：学术突破与基准演进

在模型本身的鲁棒性方面，CVPR 2026 的相关研究提供了理论支撑。**Elucidating the SNR-t Bias of Diffusion Probabilistic Models** 深入剖析了扩散概率模型中的信噪比偏差问题，这对于生成式内容的真实性与安全性至关重要。如果模型存在系统性偏差，可能导致生成内容在特定分布下失效或被恶意利用。与此同时，**国产多模态 Agent 拿下医学分割 SOTA** 展示了多模态 Agent 在关键垂直领域（医疗）的突破，该研究无需修改模型或增加 Token 即达到 SOTA，这对医疗 AI 的安全部署具有积极意义，意味着更低的推理成本与更高的可解释性潜力。

在评估体系上，**Production-grade DSPy 3.2.x agent skills + validated end-to-end examples** 提供了生产级的 Agent 技能评估框架，涵盖了 GEPA、BetterTogether 和 RLM 等验证方法。这与 **agents-md** 中提到的“强制验证循环”相呼应，表明行业正从单纯依赖模型能力转向依赖系统化的验证流程。然而，学术界的鲁棒性研究与工业界的部署速度之间存在鸿沟。例如，**神秘模型「大象」：仅 100B 拿下 SOTA** 虽然展示了极高的 Token 效率，但如此高效的模型若缺乏相应的对齐评估，可能加速有害内容的生成。

## 基础设施与对齐：算力与效率的博弈

基础设施的演进直接影响安全策略的实施。**We're launching two specialized TPUs for the agentic era** 显示 Google 正在推出专为 Agent 时代设计的 TPU，这意味着未来的 Agent 将拥有更强的实时推理能力。结合 OpenAI 的 **Speeding up agentic workflows with WebSockets in the Responses API**，算力与网络协议的优化使得 Agent 能够以毫秒级延迟响应。这种效率提升对于实时安全防御（如实时拦截恶意指令）是必要的，但也可能让攻击者利用更短的延迟进行自动化攻击。

在模型对齐方面，**神秘模型「大象」：仅 100B 拿下 SOTA** 与 **全球首个世界统一模型发布，机器人家庭成员来了** 暗示了模型架构正在向统一化、高效化发展。统一模型（World Model）的出现可能简化对齐过程，但也可能将风险集中化。如果统一模型存在对齐缺陷，其影响范围将远超单一任务模型。此外，**Google turns Chrome into an AI co-worker for the workplace** 和 **AI Overviews are coming to your Gmail at work** 表明 AI 正在深度嵌入企业基础设施，这种渗透使得传统的边界防御（Perimeter Defense）失效，安全重心必须转向模型内部的行为约束。

## Looking Forward

尽管工具与理论在不断进步，但几个关键问题仍未解决。首先，**供应链信任模型** 亟待重构。Anthropic Mythos 的泄露表明，即便有严格的权限管理，内部人员或承包商仍是最大风险点。未来的安全架构需要引入类似零信任（Zero Trust）的持续验证机制，而非依赖静态的访问令牌。其次，**数据收集的伦理边界** 尚不明确。Meta 的员工监控案例表明，企业利用 AI 训练数据时缺乏透明度和同意机制。我们需要建立类似 GDPR 的 AI 数据使用规范，明确“训练数据”的获取必须基于显式授权。最后，**Agent 的自主性阈值** 需要理论界定。当 Agent 能够自主调用工具并执行回滚（如 Polaris 所示）时，如何确保其目标函数不被局部优化误导？这需要从理论层面重新定义“对齐”在自主系统中的含义，而不仅仅是提示词层面的约束。

---
*Digest compiled by Senior AI Safety Researcher.*

---


## 参考来源

- **AI failure could trigger the next financial crisis, warns Elizabeth Warren** — [theverge_ai](https://www.theverge.com/policy/917026/ai-economy-bubble-elizabeth-warren)
- **Tesla just increased its spending plan to $25B — here’s where the money is going** — [techcrunch_ai](https://techcrunch.com/2026/04/22/tesla-just-increased-its-capex-to-25b-heres-where-the-money-is-going/)
- **OpenAI now lets teams make custom bots that can do work on their own** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/917065/openai-chatgpt-workspace-agents-custom-teams-bots)
- **How SpaceX preempted a $2B fundraise with a $60B buyout offer** — [techcrunch_ai](https://techcrunch.com/2026/04/22/how-spacex-preempted-a-2b-fundraise-with-a-60b-buyout-offer/)
- **Watch Sony’s elite ping-pong robot beat top-ranked players** — [theverge_ai](https://www.theverge.com/tech/916800/sony-ai-ace-ping-pong-table-tennis-robot-cameras)
- **Anthropic&#8217;s Mythos rollout has missed America’s cybersecurity agency** — [theverge_ai](https://www.theverge.com/policy/916758/anthropic-mythos-preview-cisa-left-out)
- **Google Meet will take AI notes for in-person meetings too** — [theverge_ai](https://www.theverge.com/tech/916779/google-meet-ai-notetaker-in-person-meetings)
- **Google turns Chrome into an AI co-worker for the workplace** — [techcrunch_ai](https://techcrunch.com/2026/04/22/google-turns-chrome-into-an-ai-coworker-for-the-workplace/)
- **Now Meta will track what employees do on their computers to train its AI agents** — [theverge_ai](https://www.theverge.com/tech/916681/meta-ai-agents-employee-tracking)
- **OpenAI teams up with Infosys to bring AI tools to more businesses** — [techcrunch_ai](https://techcrunch.com/2026/04/22/openai-teams-up-with-infosys-to-bring-ai-tools-to-more-businesses/)
- **Making ChatGPT better for clinicians** — [openai](https://openai.com/index/making-chatgpt-better-for-clinicians)
- **Exclusive: Google deepens Thinking Machines Lab ties with new multibillion-dollar deal** — [techcrunch_ai](https://techcrunch.com/2026/04/22/exclusive-google-deepens-thinking-machines-lab-ties-with-new-multi-billion-dollar-deal/)
- **Google Maps is about to get a big dose of AI** — [techcrunch_ai](https://techcrunch.com/2026/04/22/google-maps-is-about-to-get-a-big-dose-of-ai/)
- **The Download: introducing the 10 Things That Matter in AI Right Now** — [mit_tech_review](https://www.technologyreview.com/2026/04/22/1136310/the-download-10-things-that-matter-in-ai-right-now/)
- **We're launching two specialized TPUs for the agentic era.** — [google_ai](https://blog.google/innovation-and-ai/infrastructure-and-cloud/google-cloud/tpus-8t-8i-cloud-next/)
- **Anthropic’s most dangerous AI model just fell into the wrong hands** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/916501/anthropic-mythos-unauthorized-users-access-security)
- **Introducing workspace agents in ChatGPT** — [openai](https://openai.com/index/introducing-workspace-agents-in-chatgpt)
- **AI needs a strong data fabric to deliver business value** — [mit_tech_review](https://www.technologyreview.com/2026/04/22/1135295/ai-needs-a-strong-data-fabric-to-deliver-business-value/)
- **3 things Michelle Kim is into right now** — [mit_tech_review](https://www.technologyreview.com/2026/04/22/1135423/3-things-michelle-kim/)
- **One town’s scheme to get rid of its geese** — [mit_tech_review](https://www.technologyreview.com/2026/04/22/1135430/california-town-scheme-get-rid-geese/)
- **There is no nature anymore** — [mit_tech_review](https://www.technologyreview.com/2026/04/22/1135440/editors-letter-may-2026/)
- **Los Angeles is finally going underground** — [mit_tech_review](https://www.technologyreview.com/2026/04/22/1135449/los-angeles-subway-going-underground/)
- **Google updates Workspace to make AI your new office intern** — [techcrunch_ai](https://techcrunch.com/2026/04/22/google-updates-workspace-to-make-ai-your-new-office-intern/)
- **Hands on with X’s new AI-powered custom feeds** — [techcrunch_ai](https://techcrunch.com/2026/04/22/hands-on-with-xs-new-ai-powered-custom-feeds/)
- **Google Cloud launches two new AI chips to compete with Nvidia** — [techcrunch_ai](https://techcrunch.com/2026/04/22/google-cloud-next-new-tpu-ai-chips-compete-with-nvidia/)
- **Google makes an interesting choice with its new agent-building tool for enterprises** — [techcrunch_ai](https://techcrunch.com/2026/04/22/google-makes-an-interesting-choice-with-its-new-agent-building-tool-for-enterprises/)
- **AI Overviews are coming to your Gmail at work** — [techcrunch_ai](https://techcrunch.com/2026/04/22/ai-overviews-are-coming-to-your-gmail-at-work/)
- **AI is spitting out more potential drugs than ever. This startup wants to figure out which ones matter.** — [techcrunch_ai](https://techcrunch.com/2026/04/22/ai-is-spitting-out-more-potential-drugs-than-ever-this-start-up-wants-to-figure-out-which-ones-matter/)
- **The most interesting startups showcased at Google Cloud Next 2026** — [techcrunch_ai](https://techcrunch.com/2026/04/22/the-most-interesting-startups-showcased-at-google-cloud-next-2026/)
- **Speeding up agentic workflows with WebSockets in the Responses API** — [openai](https://openai.com/index/speeding-up-agentic-workflows-with-websockets)
- **Workspace agents** — [openai](https://openai.com/academy/workspace-agents)
- **sjsyrek/design-council** — [github](https://github.com/sjsyrek/design-council)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **AMAP-ML/DCW** — [github](https://github.com/AMAP-ML/DCW)
- **atomgit-atomcode/atomcode** — [github](https://github.com/atomgit-atomcode/atomcode)
- **dainsiahtill-dev/Polaris** — [github](https://github.com/dainsiahtill-dev/Polaris)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **dsd2077/CyberVerse** — [github](https://github.com/dsd2077/CyberVerse)
- **intertwine/dspy-agent-skills** — [github](https://github.com/intertwine/dspy-agent-skills)
- **TheRealSeanDonahoe/agents-md** — [github](https://github.com/TheRealSeanDonahoe/agents-md)
- **alchaincyf/huashu-design** — [github](https://github.com/alchaincyf/huashu-design)
- **36氪首发 | 电磁零部件厂商完成数千万元融资，核心团队来自德企，产品已规模化上车** — [36kr](https://36kr.com/p/3778732502095106?f=rss)
- **36氪首发 | 清华、哈工大团队做灵巧手，成本降到三分之一，三个月融资近亿元** — [36kr](https://36kr.com/p/3778730451391751?f=rss)
- **中金：A股市场近期建议关注三条主线** — [36kr](https://36kr.com/newsflashes/3778698889729028?f=rss)
- **银河证券：预计美股的进一步上行动力仍受财报季业绩兑现影响** — [36kr](https://36kr.com/newsflashes/3778695594333191?f=rss)
- **中金：公募一季度加仓通信、化工及电力设备，减仓有色和电子** — [36kr](https://36kr.com/newsflashes/3778692808365063?f=rss)
- **中信证券：中国创新药产业有望迎来管线潜力的验证与价值提升** — [36kr](https://36kr.com/newsflashes/3778683301106694?f=rss)
- **开年连融两轮的“可以玩的抖音”，又融了5000万美金｜涌现新项目** — [36kr](https://36kr.com/p/3778135439709446?f=rss)
- **一个对话框、一只青蛙、一周4万用户，Ribbi做对了什么？** — [36kr](https://36kr.com/p/3778121523025154?f=rss)
- **华泰证券：2026北京车展将启幕，建议关注自主品牌高端车型** — [36kr](https://36kr.com/newsflashes/3778673966896136?f=rss)
- **中信证券：漫剧行业景气度仍在持续** — [36kr](https://36kr.com/newsflashes/3778671351075846?f=rss)
- **光线传媒：公司第一款3A游戏开发进展比较顺利** — [36kr](https://36kr.com/newsflashes/3778668459561987?f=rss)
- **中信证券：光模块设备伴随下游资本开支与高效化、国产化趋势迎来高景气** — [36kr](https://36kr.com/newsflashes/3778666196063234?f=rss)
- **8点1氪丨张雪机车发布召回通告；哪吒汽车创始人已被列为“老赖”；英国新法案规定08后终身不得购烟** — [36kr](https://36kr.com/p/3778660962505989?f=rss)
- **最前线｜华为猛士深化战略合作，新技术将逐步落地4款以上全新车型** — [36kr](https://36kr.com/p/3777981126644745?f=rss)
- **氪星晚报｜快手618商家大会于杭州启动 ；OpenAI据悉正洽谈向一家私募股权合资企业投资至多15亿美元；事关节能降碳工作，中办、国办重磅文件对外发布** — [36kr](https://36kr.com/p/3774776026874375?f=rss)
- **36氪研究院 | 2026年中国银发经济产业研究报告** — [36kr](https://36kr.com/p/3777435336807172?f=rss)
- **具微科技两个月狂揽4轮数亿元融资，产业资本“天团”强势入局 | 36氪首发** — [36kr](https://36kr.com/p/3777491215913736?f=rss)
- **xigua-wang/skill-doctor** — [github](https://github.com/xigua-wang/skill-doctor)
- **pomclaw/pomclaw** — [github](https://github.com/pomclaw/pomclaw)
- **g2i-ai/agents** — [github](https://github.com/g2i-ai/agents)
- **jameesy/foundry-vault** — [github](https://github.com/jameesy/foundry-vault)
- **tobyilee/book-writer** — [github](https://github.com/tobyilee/book-writer)
- **pengrambo3-tech/ZeusHammer** — [github](https://github.com/pengrambo3-tech/ZeusHammer)
- **geekjourneyx/travel-guidebook** — [github](https://github.com/geekjourneyx/travel-guidebook)
- **YGYOOO/WorldX** — [github](https://github.com/YGYOOO/WorldX)
- **kernullist/windbg-decompile-ext** — [github](https://github.com/kernullist/windbg-decompile-ext)
- **SparkEngineAI/QuantClaw-plugin** — [github](https://github.com/SparkEngineAI/QuantClaw-plugin)
- **A股三大指数集体高开，半导体板块领涨** — [36kr](https://36kr.com/newsflashes/3778733535073282?f=rss)
- **央行公开市场今日资金投放量持平到期量** — [36kr](https://36kr.com/newsflashes/3778730121483522?f=rss)
- **恒指开盘跌0.25%，恒生科技指数跌0.04%** — [36kr](https://36kr.com/newsflashes/3778729916797960?f=rss)
- **“不造车的特斯拉”亮出“舱驾一体”全家桶，汽车长出“主动理解力”，奇瑞比亚迪等10+巨头力挺** — [qbitai](https://www.qbitai.com/2026/04/404721.html)
- **香港科创标杆奖项！商汤首席科学家林达华荣获中银香港科创奖** — [qbitai](https://www.qbitai.com/2026/04/404631.html)
- **RGB-Mini LED电视普及风暴，海信正式发布小墨E5S Pro** — [qbitai](https://www.qbitai.com/2026/04/404798.html)
- **国产多模态Agent拿下医学分割SOTA！不用改模型、不加token** — [qbitai](https://www.qbitai.com/2026/04/404604.html)
- **这些人读个博一年能挣几十万？2026苹果学者名单公布了** — [qbitai](https://www.qbitai.com/2026/04/404481.html)
- **全球首个世界统一模型发布，机器人家庭成员来了！** — [qbitai](https://www.qbitai.com/2026/04/404446.html)
- **从GPU到Token：AI基础设施竞争逻辑重构** — [qbitai](https://www.qbitai.com/2026/04/404440.html)
- **科大讯飞发布燎原N30m笔记本，重塑全栈国产AIPC新标杆** — [qbitai](https://www.qbitai.com/2026/04/404713.html)
- **神秘模型「大象」：仅100B拿下SOTA，Token效率超高！** — [qbitai](https://www.qbitai.com/2026/04/404645.html)
- **大厂AI抢人大战，从实习生开始** — [qbitai](https://www.qbitai.com/2026/04/404470.html)