# AI 日报 [AI 安全] - 2026-07-02


# 每日 AI 安全主题综述：智能体攻防与运行时治理

## Highlights

当日最核心的进展集中在智能体（Agent）的自动化攻防能力构建与运行时基础设施的标准化上。**T3MP3ST** 作为一个自主红队测试平台，展示了多智能体协同进行进攻性安全元测试的能力，标志着对抗性评估正从静态基准转向动态交互阶段。在防御侧，**CodeAuditSkill** 通过集成可利用性验证子智能体，实现了 Web 项目安全审计的闭环，显著提升了漏洞挖掘的可信度。与此同时，**agent-runtime** 等中性运行时核心的出现，暗示了 Agent 基础设施正在向可审计、标准化的方向演进，为运行时防御提供了必要的底层支撑。这些进展共同指向一个趋势：智能体的安全性不再仅依赖模型本身的对齐，更取决于其运行环境、工具调用链路的可控性以及自动化评估体系的完善程度。

## Agent 安全与治理

当前智能体安全研究的重心正从单一模型的指令遵循转向复杂任务链路上的风险管控，这一转变在近期的开源项目中体现得尤为明显。传统的对齐方法往往假设智能体处于封闭环境，但实际部署中，智能体需要频繁调用外部工具并访问敏感数据，这引入了新的攻击面。**T3MP3ST** 作为自主红队测试平台，其核心价值在于它不仅仅是一个测试脚本，而是一个能够自我演化的多智能体进攻性安全元测试框架。该系统允许攻击者模拟多个具有不同目标的智能体协同工作，以发现目标系统或模型在长程任务中的逻辑漏洞，这种多智能体对抗模式比单点提示注入更具威胁性，因为它能模拟真实的供应链攻击路径。与之形成鲜明对比的是 **CodeAuditSkill**，这是一个运行在特定编码助手中的 Web 项目安全代码审计技能。该项目并未止步于静态规则匹配，而是按语言专属漏洞清单系统化源码审计，并对每条高中危漏洞并行启动子智能体进行可利用性验证，最终输出可交付的审计报告。这种“检测即验证”的方法论有效减少了误报率，体现了防御侧对自动化验证闭环的追求。

然而，自动化审计能力的提升也引发了关于责任归属的新问题。**ai-data-analyst-agent** 提出了一种可追溯、自生长的数据分析智能体方法论，强调指标优先和独立的只读验证机制。该工作与 **CodeAuditSkill** 在目标上存在互补性，前者侧重于业务数据的可信分析，后者侧重于代码层面的漏洞挖掘，两者共同构成了应用层安全的双重防线。值得注意的是，尽管这些工具声称能显著提升安全性，但其本身也是基于大语言模型构建的，因此存在被提示注入的风险。例如，如果攻击者能够控制 **CodeAuditSkill** 的输入上下文，可能会诱导其忽略高危漏洞或生成虚假报告。此外，**reverse-flow-skill** 提供了一个面向本地逆向工程流程的技能，默认在沙盒环境中工作，这种设计虽然限制了潜在危害，但也暴露了当前智能体在缺乏物理隔离环境下难以保证操作安全的现状。

在治理层面，**agent-runtime** 的出现代表了基础设施层的尝试。作为一个独立的智能体运行时核心，它支持中性 LLM 类型、提供商客户端及工具循环协议。这种架构设计的意义在于将智能体的决策逻辑与执行环境解耦，使得安全策略可以在运行时层统一实施，而非分散在各个应用端。相比之下，许多现有的开源项目如 **Free-Claude-Code-AI-Desktop-App** 或 **GPT-5.6-Sol-Free** 等，虽然提供了便捷的桌面应用接口，但其背后的 API 密钥管理和数据流向往往缺乏透明度。这类非官方封装的应用程序可能成为中间人攻击的载体，导致用户凭证泄露或模型行为被篡改。因此，行业亟需建立类似 **agent-runtime** 这样的标准运行时规范，以约束第三方应用的权限边界和数据访问范围。

## 工具调用与运行时防御

智能体与环境的交互是安全风险的高发区，特别是在涉及浏览器代理、文件系统和网络请求时。**fortress** 项目展示了一种用于阻止爬虫和浏览器代理被封锁的隐身 Chromium 引擎，虽然其主要目的是反爬，但从安全角度看，它揭示了智能体在网络环境中维持持久连接的技术手段。这种技术若被恶意利用，可能导致智能体绕过企业防火墙或进行隐蔽的数据外传。为了应对此类风险，**reverse-flow-skill** 强调了本地沙盒的重要性，要求在 CTF、wargame 或训练靶场环境中工作，这种“默认隔离”的理念对于防止智能体在执行逆向工程或漏洞研判时破坏宿主系统是至关重要的。

记忆系统的管理同样是运行时安全的关键环节。**awesome-ai-companion**  curated list 中包含了大量关于长期 AI 伴侣关系的开源项目，涉及前端、后端、记忆系统及硬件载体。随着智能体具备长期记忆能力，如何确保记忆数据不被滥用或泄露成为了核心挑战。如果记忆系统缺乏加密存储或访问控制，攻击者可能通过历史对话记录推断出用户的隐私偏好或敏感信息。此外，**Math2GGB** 等 Cursor Agent Skill 展示了智能体驱动真实引擎（如 GeoGebra）的能力，这种直接控制外部软件的行为要求极高的权限验证机制。一旦智能体获得了对图形引擎的控制权，理论上它可以利用渲染漏洞或内存溢出攻击来突破沙盒限制。

在工具调用的具体实现上，**agentic-trading-desk** 提供了一个有趣的案例，它使用确定性 Python 引擎计算资产评分，而 AI 仅负责获取数据，人类批准每一笔订单。这种“人机回环”的设计在一定程度上缓解了全自动交易带来的市场操纵风险，但也反映了当前技术在完全信任智能体决策方面仍存在不足。相比之下，**CryptoAgentPro.beta** 专注于加密货币策略交易，这类高风险场景下的智能体若缺乏严格的资金限额和异常行为监控，极易造成不可逆的经济损失。因此，运行时防御不仅需要技术手段，还需要结合业务逻辑的约束，例如在金融类应用中强制引入人工审批节点或设置自动熔断机制。

## 模型能力与安全评估基准

尽管安全基础设施日益重要，但底层模型的能力分布仍是决定安全基线的关键因素。近期开源社区涌现了大量高性能的开放权重模型，如 **MiniMax-M3-Free** 和 **Gemma-4-free-desktop-app**。这些模型声称在 SWE-bench 等基准上达到 SOTA 水平，且支持本地部署。然而，本地部署并不意味着绝对安全，相反，由于缺乏云端服务商的集中式安全过滤，本地模型更容易受到提示注入攻击或产生幻觉导致的错误决策。特别是 **MiniMax-M3** 声称拥有 1M-token 上下文和原生视频理解能力，这意味着智能体可以处理更长、更复杂的任务序列，从而增加了攻击者在长上下文中隐藏恶意指令的可能性。

在评估基准方面，**OpenSquilla** 发布的 0.5.0 Preview 版本在多模型集成登顶 DRACO 双榜，对比名单中出现了最新旗舰 Fable 5。这表明行业正在尝试建立统一的性能与安全综合评估体系。然而，目前的基准测试大多侧重于功能完成度，对于智能体在对抗环境下的鲁棒性测试仍显不足。**Tencent Hunyuan Hy3** 的发布虽然在智能水平上有所提升，但其 API 接入后的数据流转安全仍需关注。当模型能力越强，其潜在的破坏力也越大，因此评估体系需要从“能否完成任务”转向“能否安全地完成任务”。

值得注意的是，市场上存在大量未经证实的模型宣称，如 **GPT-5.6-Sol-Free** 声称超越 Claude Mythos 5，这类信息往往缺乏独立验证。在安全研究中，盲目信任未经验证的模型权重可能导致供应链污染。因此，研究人员应优先选择经过社区广泛审查的开源模型，并在本地环境中进行严格的安全测试，而不是直接使用商业公司提供的免费 API 接口，后者可能存在数据收集或后门植入的风险。

## Looking Forward

展望未来，智能体安全领域仍面临若干未解决的理论问题与技术挑战。首先是自主红队测试的伦理边界问题，**T3MP3ST** 这类平台虽然能发现漏洞，但其生成的攻击向量若被公开，可能被恶意利用。如何在促进安全研究与防止武器化之间取得平衡，需要行业制定明确的准则。其次是记忆系统的形式化验证，目前大多数记忆管理方案依赖于启发式规则，缺乏数学上的安全性证明，未来需要探索基于形式化方法的记忆隔离机制。最后是运行时标准的统一，**agent-runtime** 等项目的出现表明基础设施正在分化，但缺乏跨平台的通用安全协议可能导致碎片化的安全实践。建议后续研究重点关注智能体在异构环境下的权限最小化原则，以及建立针对多智能体协作场景的动态风险评估框架，以确保智能体生产力的释放不会以牺牲基本安全为代价。

---


## 参考来源

- **Some of the nation’s rich are letting AI teach their kids** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/961505/wealthy-ai-schools-alpha-forge-prep)
- **Infuriating Google commercial imagines the founding fathers embracing AI** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/961468/google-ai-commercial-founding-fathers-declaration-of-independence)
- **claude-anthropic-ai/Free-Claude-Code-AI-Desktop-App** — [github](https://github.com/claude-anthropic-ai/Free-Claude-Code-AI-Desktop-App)
- **cvv-number/minimax-m3-desktop-app-free-api** — [github](https://github.com/cvv-number/minimax-m3-desktop-app-free-api)
- **soullive/GPT-5.6-Sol-Free** — [github](https://github.com/soullive/GPT-5.6-Sol-Free)
- **ai4s-research/open-science** — [github](https://github.com/ai4s-research/open-science)
- **Oft3r/agentic-trading-desk** — [github](https://github.com/Oft3r/agentic-trading-desk)
- **Amazon will stop accepting new customers for Mechanical Turk** — [techcrunch_ai](https://techcrunch.com/2026/07/05/amazon-will-stop-accepting-new-customers-for-mechanical-turk/)
- **amitshekhariitbhu/ai-agents-tutorial** — [github](https://github.com/amitshekhariitbhu/ai-agents-tutorial)
- **easylink-ai-open/agent-runtime** — [github](https://github.com/easylink-ai-open/agent-runtime)
- **lingbol088-spec/reverse-flow-skill** — [github](https://github.com/lingbol088-spec/reverse-flow-skill)
- **ryckli/CryptoAgentPro.beta** — [github](https://github.com/ryckli/CryptoAgentPro.beta)
- **Pluviobyte/rnskill** — [github](https://github.com/Pluviobyte/rnskill)
- **elder-plinius/T3MP3ST** — [github](https://github.com/elder-plinius/T3MP3ST)
- **fafa-ai-data-lab/ai-data-analyst-agent** — [github](https://github.com/fafa-ai-data-lab/ai-data-analyst-agent)
- **zhiyuwang720-dev/CodeAuditSkill** — [github](https://github.com/zhiyuwang720-dev/CodeAuditSkill)
- **nodobys/Claude-Sonnet-5-Free-Desktop-APP** — [github](https://github.com/nodobys/Claude-Sonnet-5-Free-Desktop-APP)
- **zvkzs/Gemma-4-free-desktop-app** — [github](https://github.com/zvkzs/Gemma-4-free-desktop-app)
- **DasterProkio/awesome-ai-companion** — [github](https://github.com/DasterProkio/awesome-ai-companion)
- **cwlin0131/coffee-chat-prep** — [github](https://github.com/cwlin0131/coffee-chat-prep)
- **Key-wxh/market-fish** — [github](https://github.com/Key-wxh/market-fish)
- **tiliondev/fortress** — [github](https://github.com/tiliondev/fortress)
- **GordenSun/Math2GGB** — [github](https://github.com/GordenSun/Math2GGB)
- **AI 砍掉的第一批大厂人：高薪，高绩效，高P｜深氪** — [36kr](https://36kr.com/p/3883456791163138?f=rss)
- **OpenSquilla发布0.5.0 Preview：多模型集成登顶DRACO双榜，对比名单中出现最新旗舰Fable 5** — [qbitai](https://www.qbitai.com/2026/07/443559.html)
- **Meta也来卖铲子了！小扎：模型可以慢，GPU必须赚** — [qbitai](https://www.qbitai.com/2026/07/443339.html)
- **华为更新韬定律论文！** — [qbitai](https://www.qbitai.com/2026/07/443186.html)
- **征程赶超｜WAIC 2026世界模型激辩：答案不在VLA或世界模型，而在？** — [qbitai](https://www.qbitai.com/2026/07/443522.html)
- **征程赶超｜WAIC 2026模型与智能体：后Scaling时代范式重构，迈入智能体生产力时代** — [qbitai](https://www.qbitai.com/2026/07/443399.html)
- **获DCM Ventures投资数百万美元，APTSell希望成为AI版的首席销售官｜涌现新项目** — [36kr](https://36kr.com/p/3883591654895873?f=rss)
- **跨境电商风向转变：新生代不再只拼价格，开始争“定价权”丨最前线** — [36kr](https://36kr.com/p/3883561480876297?f=rss)
- **8点1氪丨7-11指控耐克新鞋配色抄袭；A股新版交易规则今起施行；华尔街称苹果采购长鑫内存是为了压价** — [36kr](https://36kr.com/p/3883400536453381?f=rss)
- **SEAJ大幅上调2026财年日本产半导体设备销售额预期，预计将破纪录** — [36kr](https://36kr.com/newsflashes/3883843898765571?f=rss)
- **腾讯混元Hy3正式发布** — [36kr](https://36kr.com/newsflashes/3883833442430979?f=rss)
- **36氪首发｜前西门子、罗罗电动飞行团队创业做航空电驱系统，两轮连融数千万元** — [36kr](https://36kr.com/p/3883721315971078?f=rss)
- **上市前夜 | 哈工大在读博士以百亿市值冲港股IPO，创始三人只剩一人** — [36kr](https://36kr.com/p/3883708118921480?f=rss)
- **上市前夜｜4个月净利润38.4亿元，深圳存储黑马冲港股IPO** — [36kr](https://36kr.com/p/3883706720727303?f=rss)
- **2026，量子计算迟到的狂欢：能拿订单、奔赴IPO、市值破百亿** — [36kr](https://36kr.com/p/3883513899380744?f=rss)
- **鄂尔多斯、和达金服共同领投，「贻如科技」完成超亿元A轮融资｜36氪首发** — [36kr](https://36kr.com/p/3880060701388809?f=rss)
- **美的在北京成立新公司，注册资本200万** — [36kr](https://36kr.com/newsflashes/3883864322781448?f=rss)
- **爱仕达与智元机器人签署战略合作协议，五大方向开展深度合作** — [36kr](https://36kr.com/newsflashes/3883821411545091?f=rss)
- **千问大模型升级实时语音识别大模型Fun-ASR-Realtime** — [36kr](https://36kr.com/newsflashes/3883798757683464?f=rss)