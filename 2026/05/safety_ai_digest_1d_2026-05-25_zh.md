# AI 日报 [AI 安全] - 2026-05-25


# AI安全与治理每日文摘：2026年5月25日

## Highlights

今日AI安全领域的进展呈现出防御工具结构化与攻击向量复杂化并行的态势。一方面，Anthropic开源了一套规模化的**网络安全技能库**，为AI代理的安全操作提供了标准化框架，标志着行业在构建安全基础设施上的重要一步。另一方面，黑客攻击策略正从传统的提示词注入转向对模型“人格”特性的利用，这一新兴威胁对现有安全防护提出了新的理论挑战。此外，将代码库转化为可查询知识图谱的工具链逐渐成熟，为AI系统的安全审计与可解释性分析提供了新的技术路径。

## AI代理安全与攻击向量

随着AI代理（AI agent）能力的增强，其面临的攻击面也在扩大，防御体系与攻击手段在同步演进。今日的观察显示，攻击者的研究焦点已从技术性漏洞转向模型的语义与认知层面。

来自The Verge的报道 **“Hackers are learning to exploit chatbot ‘personalities’”** 指出，新一代的攻击方法正利用大语言模型被赋予的特定“人格”（personality）或行为模式。攻击者通过精心构造的对话上下文，诱使模型突破其预设的行为边界，例如诱导其泄露训练数据中的隐私信息或执行非预期的操作。这与早期简单的提示词绕过（prompt bypassing）不同，它更深入地挖掘了模型对自身“角色”的认知，属于一种更隐蔽的语义攻击。

面对不断演进的威胁，防御工具的构建也在趋向体系化。GitHub上发布的**“Anthropic-Cybersecurity-Skills”** 仓库提供了一个大规模的范例。该项目包含了754个结构化的网络安全技能，并映射到MITRE ATT&CK、NIST CSF 2.0等五大权威安全框架。其核心思想是为AI代理提供一套标准化、可验证的安全操作“词汇表”和“决策树”，使得代理在执行代码审计、漏洞分析等任务时，能够遵循既定的安全准则，而非完全依赖其不稳定涌现的能力。这与上述利用“人格”的攻击形成了有趣的对比：一个试图规范代理的“职业行为”，另一个则试图扰乱其“个性认知”。两者的对抗将定义下一代AI安全的核心战场。

## 对齐、可解释性与审计工具

对齐（alignment）研究不仅关注模型的价值观，也关注其决策过程的可理解性与可审计性。今日多个开源工具项目将重点放在了通过代码分析来增强AI系统的透明度。

**“Understand-Anything”** 项目提出了一种新颖的可视化分析路径。它能够将任意代码库转化为一个交互式的知识图谱，用户可以通过探索、搜索和提问来理解代码结构。该项目宣称支持Claude Code、Codex等主流AI编码代理。从安全审计的角度看，此类工具的价值在于将非结构化的、复杂的代码依赖关系显性化，帮助审计人员或安全研究员快速定位关键函数调用链、识别潜在的数据流风险或逻辑漏洞，从而对AI生成或修改的代码进行更有效的安全评估。

与此互补的是**“CodeGraph”** 项目，它专注于创建预索引的代码知识图谱。其宣传点是“更少的token消耗，更少的工具调用”，旨在提升AI代理在分析大规模代码库时的效率。对于安全审计而言，效率的提升意味着可以在有限的上下文窗口和计算成本内，对更大规模的代码进行深度扫描，这为将可解释性分析工具集成到持续集成/持续部署（CI/CD）安全流水线中提供了可能性。这两个项目共同指向一个趋势：代码理解正在成为增强AI系统自身安全性和可审计性的关键基础设施。

## 安全评估与基准构建

虽然今日未出现全新的综合性安全评估基准发布，但工具生态的成熟正在为更细粒度的安全评估奠定基础。建立有效的评估基准是衡量防御手段和理解攻击能力的前提，目前这一领域仍显空白。

TechCrunch的报道 **“Everyone is navigating AI security in real time — even Google”** 引用了行业普遍的困境，即包括科技巨头在内的所有参与者都处于“边航行，边探索”的状态。这侧面反映了当前缺乏公认的、全面的AI安全评估标准。前述的网络安全技能库和代码知识图谱工具，其本身就可以被视为构建评估基准的“构件”。例如，安全技能库中的条目可以转化为对代理的安全能力测试用例；代码知识图谱则可用于评估AI在代码层面的理解深度与安全漏洞识别能力。然而，将这些分散的能力评估整合成一个反映真实世界风险的、动态更新的基准，仍是未解决的重大挑战。

## 隐私、数据收集与用户感知

AI系统，特别是面向终端用户的可穿戴设备与智能代理，其数据收集行为持续引发隐私担忧，这与安全问题的根源（数据）紧密相连。

关于Amazon Bee可穿戴设备的报道 **“I tried Amazon’s Bee wearable and am both intrigued and slightly creeped out”** 生动地描述了这种矛盾心态。设备的便捷性与对持续数据采集（如环境声音、对话）的隐私焦虑并存。这并非单纯的技术安全问题，更涉及到用户对数据所有权、使用边界和长期风险的认知与信任。在AI代理时代，这种数据收集变得更加无处不在和深入，使得隐私保护从单纯的“数据加密传输存储”问题，扩展为如何在复杂的代理交互中实施“数据最小化”和“目的限定”原则的治理难题。

## 产业动态与治理观察

产业界对AI安全的关注已从理念倡导进入实践整合阶段，但路径仍不清晰。

量子位的报道 **“卷到今天，Agent的含金量还在提升丨AIGC2026圆桌论坛”** 反映了产业界将AI代理视为关键战场的同时，其安全与可靠性已成为衡量“含金量”的核心维度之一。然而，报道多为行业观点聚合，缺乏具体的技术细节披露。

在开发实践层面，**“andrej-karpathy-skills”** 仓库试图将知名研究者Andrej Karpathy关于大语言模型编码陷阱的观察总结为一套可操作的技能提示，嵌入到Claude Code等代理中。这可以看作是一种轻量级的“对齐”实践，即通过外部知识注入来规范代理行为，减少其犯错的可能性。但其实际效果，尤其是在对抗精心设计的恶意输入时的鲁棒性，有待独立验证。

## Looking Forward

今日的观察揭示了几个亟待解决的深层理论与实践问题：

1.  **安全基准的缺失**：行业目前依赖零散的工具和框架，缺乏一个像ImageNet之于计算机视觉那样具有共识的、全面的AI安全评估基准。如何设计能覆盖代理安全、隐私泄露、价值观对齐等多维度的动态评估体系？
2.  **“人格攻击”的机理与防御**：对模型“人格”特性的利用，是否触及了当前Transformer架构在角色认知与边界划分上的固有缺陷？防御此类攻击需要从对齐训练、推理监控还是系统架构层面入手？
3.  **可解释性工具的效用边界**：知识图谱等工具显著提升了代码的可读性，但它们在多大程度上能帮助发现AI系统自身的逻辑漏洞或非预期涌现行为？这种“外挂式”的可解释性分析，与模型内在的可解释性研究如何协同？
4.  **隐私与安全的平衡**：在追求更强大、更情境感知的AI代理过程中，数据收集的广度和深度不断增加。如何在不严重削弱模型能力的前提下，实现切实有效的隐私保护技术（如联邦学习、差分隐私）与代理架构的深度融合，而非事后附加？

未来的工作需在攻击与防御的共演、评估标准的建立、以及隐私保护的可操作性上取得突破，方能构建可信的AI生态系统。

---


## 参考来源

- **I tried Amazon’s Bee wearable and am both intrigued and slightly creeped out** — [techcrunch_ai](https://techcrunch.com/2026/05/24/i-tried-amazons-bee-wearable-and-am-both-intrigued-and-slightly-creeped-out/)
- **Hackers are learning to exploit chatbot &#8216;personalities&#8217;** — [theverge_ai](https://www.theverge.com/column/935545/hackers-ai-chatbots)
- **Everyone is navigating AI security in real time — even Google** — [techcrunch_ai](https://techcrunch.com/2026/05/24/everyone-is-navigating-ai-security-in-real-time-even-google/)
- **mukul975 / Anthropic-Cybersecurity-Skills** — [github](https://github.com/mukul975/Anthropic-Cybersecurity-Skills)
- **Lum1104 / Understand-Anything** — [github](https://github.com/Lum1104/Understand-Anything)
- **blakeblackshear / frigate** — [github](https://github.com/blakeblackshear/frigate)
- **dotnet / skills** — [github](https://github.com/dotnet/skills)
- **codecrafters-io / build-your-own-x** — [github](https://github.com/codecrafters-io/build-your-own-x)
- **666ghj / MiroFish** — [github](https://github.com/666ghj/MiroFish)
- **manaflow-ai / cmux** — [github](https://github.com/manaflow-ai/cmux)
- **shiyu-coder / Kronos** — [github](https://github.com/shiyu-coder/Kronos)
- **multica-ai / multica** — [github](https://github.com/multica-ai/multica)
- **colbymchenry / codegraph** — [github](https://github.com/colbymchenry/codegraph)
- **Alishahryar1 / free-claude-code** — [github](https://github.com/Alishahryar1/free-claude-code)
- **earendil-works / pi** — [github](https://github.com/earendil-works/pi)
- **multica-ai / andrej-karpathy-skills** — [github](https://github.com/multica-ai/andrej-karpathy-skills)
- **anthropics / knowledge-work-plugins** — [github](https://github.com/anthropics/knowledge-work-plugins)
- **anthropics / claude-plugins-official** — [github](https://github.com/anthropics/claude-plugins-official)
- **rohitg00 / ai-engineering-from-scratch** — [github](https://github.com/rohitg00/ai-engineering-from-scratch)
- **卷到今天，Agent的含金量还在提升丨AIGC2026圆桌论坛** — [qbitai](https://www.qbitai.com/2026/05/423421.html)
- **谷歌CEO承认Coding落后了** — [qbitai](https://www.qbitai.com/2026/05/423390.html)
- **未来推理将吃掉70%算力，30%留给训练丨硅谷投资人张璐@AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/423382.html)
- **什么！你说胡彦斌也在苦修Vibe Coding** — [qbitai](https://www.qbitai.com/2026/05/423213.html)
- **对话VITURE姜公略：什么才是XR眼镜该有的样子？** — [36kr](https://36kr.com/p/3823013049045380?f=rss)
- **36氪首发 | 商汤国香投了一家消费级空间相机公司，为具身智能采集真实世界数据** — [36kr](https://36kr.com/p/3824089662853513?f=rss)
- **36氪首发 | 3D打印齿科龙头要切入桌面全彩造物，获君联、达晨等3亿+融资** — [36kr](https://36kr.com/p/3824073646624899?f=rss)
- **北京市网络市场监管联席会议召开，集中约谈17家重点平台企业** — [36kr](https://36kr.com/newsflashes/3824073923907720?f=rss)
- **机器人力传感器龙头再获数亿融资，上汽、中芯等抢先入局** — [36kr](https://36kr.com/p/3824053061652616?f=rss)
- **香港交易所回应“算力期货布局规划”：暂无评论可提供，将来如有相关信息将及时公布** — [36kr](https://36kr.com/newsflashes/3824047189971332?f=rss)
- **“具脑磐石”完成新一轮亿元级融资** — [36kr](https://36kr.com/newsflashes/3824042643771523?f=rss)
- **华为具身大脑一号位做类脑智能世界模型，对标JEPA，获亿元级融资｜硬氪首发** — [36kr](https://36kr.com/p/3819931562414467?f=rss)
- **华为正式发表半导体领域新定律** — [36kr](https://36kr.com/newsflashes/3824028118962304?f=rss)
- **从服务沉默玩家，到技术外溢至千行百业：游戏+AI的下一站是什么？** — [36kr](https://36kr.com/p/3822747968196993?f=rss)
- **京东方华灿光电Micro LED高端芯片一体化项目全部达产产值50亿元** — [36kr](https://36kr.com/newsflashes/3824007076679809?f=rss)
- **8点1氪丨“壹号土猪”商标被宣告无效；山西煤矿爆炸时近一半下井工人在系统中查不到有效信息；小米通报空调抽真空造假事件** — [36kr](https://36kr.com/p/3823941399826566?f=rss)
- **功效洗护市场，跑不出下一个完美日记** — [36kr](https://36kr.com/p/3819023278048643?f=rss)
- **珀莱雅收购花知晓，但美妆界的“安踏”还没诞生** — [36kr](https://36kr.com/p/3820119270953352?f=rss)
- **“蓝点触控”完成C++轮数亿元人民币融资** — [36kr](https://36kr.com/newsflashes/3824077372690569?f=rss)
- **高德问店选址Skill接入钉钉悟空** — [36kr](https://36kr.com/newsflashes/3824063200301449?f=rss)
- **“黑格科技”完成超3亿元人民币C轮融资** — [36kr](https://36kr.com/newsflashes/3824044595679619?f=rss)