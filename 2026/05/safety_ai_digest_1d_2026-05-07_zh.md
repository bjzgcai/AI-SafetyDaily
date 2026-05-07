# AI 日报 [AI 安全] - 2026-05-07


# AI 安全与治理日报：2026 年 05 月 07 日

## Highlights

今日学术圈在生成模型稳定性与智能体评估基准方面取得关键进展，其中 **Stream-R1: Reliability-Perplexity Aware Reward Distillation for Streaming Video Generation** 提出了一种针对流式视频生成的可靠性感知奖励蒸馏方法，旨在解决现有蒸馏模型中因忽略采样方差而导致的质量瓶颈，这对高保真视频生成的安全性至关重要。同时，**OpenSearch-VL: An Open Recipe for Frontier Multimodal Search Agents** 发布了首个完全开源的前沿多模态深度搜索智能体训练配方，填补了工业界在可复现性上的空白，为评估搜索智能体的幻觉风险提供了基准。在垂直领域安全方面，**SymptomAI: Towards a Conversational AI Agent for Everyday Symptom Assessment** 的大规模实地部署研究揭示了通用大模型在日常医疗问诊场景中的潜在风险，尽管其在特定案例上表现优异，但在真实世界复杂交互中的诊断一致性仍需警惕。

## 生成模型的安全性与鲁棒性

随着扩散模型向少步推理和流式生成演进，效率提升往往伴随着安全边界的模糊。在视频生成领域，**Stream-R1: Reliability-Perplexity Aware Reward Distillation for Streaming Video Generation** 与 **Stream-T1: Test-Time Scaling for Streaming Video Generation** 共同指向了蒸馏过程中的可靠性问题。前者指出，现有的分布匹配蒸馏（DMD）方法将教师模型的所有输出视为同等可靠的监督信号，忽略了学生模型在生成过程中的可靠性方差，这可能导致模型在长序列生成中出现累积误差。作者声称其提出的方法通过区分跨采样和跨空间的方差，能够提升生成质量，但这一结论仍需独立复现以验证其在对抗扰动下的鲁棒性。相比之下，**Stream-T1** 侧重于推理阶段的时间扩展（Test-Time Scaling），利用流式生成的分块特性降低计算开销，虽然作者展示了其在时间控制上的优势，但测试时扩展带来的计算不确定性尚未被充分评估。

在图像编辑与保真度方面，**StableI2I: Spotting Unintended Changes in Image-to-Image Transition** 提出了一个动态评估框架，旨在解决现有评估忽略语义对应和空间结构一致性的问题。该工作强调了在图像编辑任务中，除了指令遵循外，内容保真度（Content Fidelity）是防止生成内容被恶意篡改的关键指标。这与 **Lightning Unified Video Editing via In-Context Sparse Attention** 形成了互补，后者通过稀疏注意力机制解决了上下文学习（ICL）中的计算瓶颈，但稀疏化可能引入的信息丢失风险需要结合 **StableI2I** 的评估框架进行安全审计。此外，**APEX: Large-scale Multi-task Aesthetic-Informed Popularity Prediction for AI-Generated Music** 揭示了生成内容中的审美偏见问题，该模型基于大量 AI 生成音乐训练，虽然能预测流行度，但其训练数据中可能隐含的版权与风格同质化风险，对内容生态的多样性构成了潜在威胁。

## 智能体安全与复杂任务评估

智能体（Agent）在复杂环境中的决策能力日益增强，但其安全性评估基准仍显滞后。 **OpenSearch-VL: An Open Recipe for Frontier Multimodal Search Agents** 与 **OpenSeeker-v2: Pushing the Limits of Search Agents with Informative and High-Difficulty Trajectories** 均关注搜索智能体的训练数据与轨迹合成。前者强调开源配方对于复现前沿能力的重要性，指出工业界的高资源密集型流水线掩盖了数据质量对智能体行为的影响；后者则通过引入高难度轨迹证明，简单的监督微调（SFT）在特定数据增强下也能达到前沿水平。这两项工作共同指向了一个核心问题：智能体的“深度搜索”能力是否建立在可靠证据之上，而非仅仅是概率匹配。 **Rethinking Reasoning-Intensive Retrieval: Evaluating and Advancing Retrievers in Agentic Search Systems** 进一步指出，现有基准如 BRIGHT 仅评估检索器的孤立表现，缺乏对迭代搜索中证据组合构建的评估，这可能导致智能体在长链条推理中引入错误信息。

在具身智能与物理交互方面， **RLDX-1 Technical Report** 与 **A Benchmark for Interactive World Models with a Unified Action Generation Framework (iWorld-Bench)** 试图解决机器人策略在真实物理环境中的泛化问题。RLDX-1 基于多流动作 Transformer 构建灵巧操作策略，但其在复杂物理任务中的安全性（如力控失效）尚未在报告中详细披露。iWorld-Bench 则提供了包含 33 万视频片段的大规模交互数据集，旨在评估世界模型的距离感知与记忆能力。然而， **Workspace-Bench 1.0: Benchmarking AI Agents on Workspace Tasks with Large-Scale File Dependencies** 提出了更为严峻的安全挑战，即智能体在处理具有大规模文件依赖的工作空间任务时，可能因错误解析隐式依赖而导致系统破坏。这要求未来的智能体评估不仅关注任务完成度，还需纳入对文件系统操作的安全审计。 **PhysForge: Generating Physics-Grounded 3D Assets for Interactive Virtual World** 则从资产生成角度切入，强调物理属性标注对于虚拟世界交互安全的重要性，缺乏物理逻辑的资产可能导致具身智能在模拟环境中产生不可预测的行为。

## 垂直领域治理与隐私

在医疗与法律等高风险领域，大模型的应用必须经过严格的治理验证。 **SymptomAI: Towards a Conversational AI Agent for Everyday Symptom Assessment** 通过 Fitbit 应用对近 1.4 万名参与者进行了随机对照试验，结果显示 AI 代理在诊断评估上表现尚可，但作者强调这主要基于精心设计的案例，对于日常生活中的非结构化症状报告，其诊断一致性仍存在不确定性。这一发现警示我们，不能简单地将实验室环境下的性能外推至真实医疗场景。 **PatRe: A Full-Stage Office Action and Rebuttal Generation Benchmark for Patent Examination** 则关注法律推理的完整性，该基准模拟了专利审查的全生命周期，包括办公室行动生成与申请人反驳。由于专利审查涉及复杂的法律逻辑，该基准的发布有助于评估模型在知识产权领域的推理可靠性，防止生成具有误导性或侵权风险的法律文本。

在隐私与数据利用方面， **Parameter-Efficient Multi-View Proficiency Estimation: From Discriminative Classification to Generative Feedback** 探讨了多视图技能评估中的隐私问题，特别是在康复和人才识别场景中，细微的动作差异可能涉及个人生物特征。虽然该工作提出了参数高效的架构，但在多视图融合过程中如何防止生物特征泄露仍需进一步研究。 **Awaking Spatial Intelligence in Unified Multimodal Understanding and Generation** 提出的 JoyAI-Image 模型虽然实现了视觉理解与生成的统一，但其训练数据中包含的长文本渲染监督与空间编辑信号，可能涉及用户隐私数据的二次利用，需在模型发布前进行严格的数据脱敏审计。

## 开源安全工具与基础设施

开源社区正在构建针对智能体安全的基础设施，其中 **Agent_Memory_Techniques** 提供了涵盖对话缓冲区、向量存储及知识图谱的 30 个可运行 Jupyter 笔记本，为智能体记忆管理提供了标准化工具，有助于防止记忆污染和上下文泄露。 **agent-safety-eval-lab** 则专注于智能体轨迹和工具使用的安全评估，填补了自动化安全测试的空白。 **goblintown** 提出了一种多智能体编排协议，通过角色分工（如 Gremlin 攻击输出、Troll 仲裁）来模拟对抗环境，这种“红队”机制对于测试智能体系统的鲁棒性具有参考价值。此外， **books-for-bots** 将 EPUB 转换为带偏移量的 Markdown，有助于提高智能体阅读长文档时的 Token 效率，减少因上下文截断导致的逻辑错误。这些工具的共同趋势是将安全评估从模型训练后阶段前移至开发阶段，强调在智能体构建初期即引入安全约束。

## 产业动态与治理观察

产业界的安全事件与治理争议持续发酵。 **Musk v. Altman trial** 的最新进展显示，OpenAI 前 CTO Mira Murati 在证词中指控 CEO Sam Altman 关于新模型安全标准的陈述不实，这一法律纠纷直接触及了 AI 治理的核心——安全承诺的可信度。虽然这是法律层面的指控，但其反映出的内部安全标准透明度问题值得业界关注。在基础设施层面， **SpaceX may spend up to $119B on 'Terafab' chip factory in Texas** 的报道引发了对算力集中化风险的担忧，如此大规模的垂直整合可能加剧算力垄断，进而影响安全研究的开放性与多样性。 **Google shuts down Project Mariner** 则是一个典型的案例，该实验性功能因无法维持而被关停，这提示我们，过度承诺的 AI 功能若缺乏可靠的安全验证，极易导致产品失败。

关于硬件与供应链， **Samsung crosses $1T valuation** 与 **Apple to pay $250M to settle lawsuit over Siri's delayed AI features** 反映了市场对 AI 能力的期待与法律风险之间的张力。特别是苹果因过度承诺 Siri 功能而面临集体诉讼，这为其他厂商敲响了警钟：在 AI 功能发布前，必须确保技术可行性与宣传的一致性，避免误导用户。 **DeepSeek could hit $45B valuation** 等融资新闻虽显示行业热度，但需警惕资本驱动下的安全妥协风险。对于 **36kr** 等媒体关于 **PixelBloom** 或 **临界点** 机器人的融资报道，应保持审慎，此类信息多为商业宣传，缺乏对技术安全性的独立验证，不应作为评估行业安全水平的依据。

## Looking Forward

当前研究仍面临若干未解决的理论问题。首先，流式视频生成中的 **Test-Time Scaling** 虽然降低了计算成本，但其对生成内容一致性的长期影响尚未被充分建模，特别是在对抗性攻击下的鲁棒性存疑。其次，智能体在复杂工作空间中的 **File Dependencies** 解析能力，本质上是一个符号与神经网络的融合问题，目前缺乏统一的理论框架来保证智能体不会因错误依赖而破坏系统。最后，医疗与法律等垂直领域的 **Real-world Deployment** 风险表明，实验室基准无法完全模拟真实世界的复杂性，未来的安全评估需要更多基于实地部署的长期追踪数据。在治理层面，随着算力基础设施的集中化，如何确保开源安全工具与评估基准的独立性，防止其被商业利益所裹挟，将是 2026 年及以后需要持续关注的核心议题。

---


## 参考来源

- **D-OPSD: On-Policy Self-Distillation for Continuously Tuning Step-Distilled Diffusion Models** — [huggingface_papers](https://arxiv.org/abs/2605.05204)
- **Stream-R1: Reliability-Perplexity Aware Reward Distillation for Streaming Video Generation** — [huggingface_papers](https://arxiv.org/abs/2605.03849)
- **RLDX-1 Technical Report** — [huggingface_papers](https://arxiv.org/abs/2605.03269)
- **OpenSearch-VL: An Open Recipe for Frontier Multimodal Search Agents** — [huggingface_papers](https://arxiv.org/abs/2605.05185)
- **Stream-T1: Test-Time Scaling for Streaming Video Generation** — [huggingface_papers](https://arxiv.org/abs/2605.04461)
- **Lightning Unified Video Editing via In-Context Sparse Attention** — [huggingface_papers](https://arxiv.org/abs/2605.04569)
- **PhysForge: Generating Physics-Grounded 3D Assets for Interactive Virtual World** — [huggingface_papers](https://arxiv.org/abs/2605.05163)
- **StableI2I: Spotting Unintended Changes in Image-to-Image Transition** — [huggingface_papers](https://arxiv.org/abs/2605.04453)
- **Parameter-Efficient Multi-View Proficiency Estimation: From Discriminative Classification to Generative Feedback** — [huggingface_papers](https://arxiv.org/abs/2605.03848)
- **APEX: Large-scale Multi-task Aesthetic-Informed Popularity Prediction for AI-Generated Music** — [huggingface_papers](https://arxiv.org/abs/2605.03395)
- **Awaking Spatial Intelligence in Unified Multimodal Understanding and Generation** — [huggingface_papers](https://arxiv.org/abs/2605.04128)
- **Rethinking Reasoning-Intensive Retrieval: Evaluating and Advancing Retrievers in Agentic Search Systems** — [huggingface_papers](https://arxiv.org/abs/2605.04018)
- **PatRe: A Full-Stage Office Action and Rebuttal Generation Benchmark for Patent Examination** — [huggingface_papers](https://arxiv.org/abs/2605.03571)
- **A Benchmark for Interactive World Models with a Unified Action Generation Framework** — [huggingface_papers](https://arxiv.org/abs/2605.03941)
- **Workspace-Bench 1.0: Benchmarking AI Agents on Workspace Tasks with Large-Scale File Dependencies** — [huggingface_papers](https://arxiv.org/abs/2605.03596)
- **OpenSeeker-v2: Pushing the Limits of Search Agents with Informative and High-Difficulty Trajectories** — [huggingface_papers](https://arxiv.org/abs/2605.04036)
- **SymptomAI: Towards a Conversational AI Agent for Everyday Symptom Assessment** — [huggingface_papers](https://arxiv.org/abs/2605.04012)
- **Is xAI a neocloud now?** — [techcrunch_ai](https://techcrunch.com/2026/05/06/is-xai-a-neocloud-now/)
- **Five architects of the AI economy explain where the wheels are coming off** — [techcrunch_ai](https://techcrunch.com/2026/05/06/five-architects-of-the-ai-economy-explain-where-the-wheels-are-coming-off/)
- **Musk’s biggest loyalist became his biggest liability** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/925665/musk-altman-trial-shivon-zilis-testimony)
- **Google shuts down Project Mariner** — [theverge_ai](https://www.theverge.com/tech/925559/google-project-mariner-shut-down)
- **How David Sacks crashed and burned in the White House** — [theverge_ai](https://www.theverge.com/column/925487/david-sacks-trump-administration-ai-model-review)
- **Mira Murati tells the court that she couldn’t trust Sam Altman’s words** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/925338/openai-musk-v-altman-mira-murati)
- **SpaceX may spend up to $119B on ‘Terafab’ chip factory in Texas** — [techcrunch_ai](https://techcrunch.com/2026/05/06/spacex-may-spend-up-to-119-billion-on-terafab-chip-factory-in-texas/)
- **DeepSeek could hit $45B valuation from its first investment round** — [techcrunch_ai](https://techcrunch.com/2026/05/06/deepseek-could-hit-45b-valuation-from-its-first-investment-round/)
- **Khosla-backed robotics startup Genesis AI has gone full stack, demo shows** — [techcrunch_ai](https://techcrunch.com/2026/05/06/khosla-backed-robotics-startup-genesis-ai-has-gone-full-stack-demo-shows/)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **5 gardening tips you can try right in Search** — [google_ai](https://blog.google/products-and-platforms/products/search/gardening-tips/)
- **At TechCrunch Disrupt 2026, all your M&A questions will be answered** — [techcrunch_ai](https://techcrunch.com/2026/05/06/at-techcrunch-disrupt-2026-all-your-ma-questions-will-be-answered/)
- **3 days left to lock in 50% off a second ticket to TechCrunch Disrupt 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/06/3-days-left-to-lock-in-50-off-a-second-ticket-to-techcrunch-disrupt-2026/)
- **AI boom pushes Samsung to $1T** — [techcrunch_ai](https://techcrunch.com/2026/05/06/ai-boom-pushes-samsung-to-1t/)
- **Google&#8217;s AI search summaries will now quote Reddit** — [theverge_ai](https://www.theverge.com/tech/924993/google-ai-search-mode-overviews-update-reddit-links)
- **Microsoft’s Office and LinkedIn chief now runs Teams in latest reshuffle** — [theverge_ai](https://www.theverge.com/tech/924931/microsoft-office-copilot-windows-reorg-shuffle)
- **The Download: seafloor science and military chatbots** — [mit_tech_review](https://www.technologyreview.com/2026/05/06/1136917/the-download-seafloor-science-military-ai-chatbots/)
- **Chrome’s AI features may be hogging 4GB of your computer storage** — [theverge_ai](https://www.theverge.com/tech/924933/google-chrome-4gb-gemini-nano-ai-features)
- **Barry Diller trusts Sam Altman. But ‘trust is irrelevant’ as AGI nears, he says.** — [techcrunch_ai](https://techcrunch.com/2026/05/06/barry-diller-trusts-sam-altman-but-trust-is-irrelevant-as-agi-nears-he-says/)
- **Snap says its $400M deal with Perplexity ‘amicably ended’** — [techcrunch_ai](https://techcrunch.com/2026/05/06/snap-says-its-400m-deal-with-perplexity-amicably-ended/)
- **How Elon Musk left OpenAI, according to Greg Brockman** — [techcrunch_ai](https://techcrunch.com/2026/05/06/how-elon-musk-left-openai-according-to-greg-brockman/)
- **Google updates AI search to include quotes from Reddit and other sources** — [techcrunch_ai](https://techcrunch.com/2026/05/06/google-updates-ai-search-to-include-expert-advice-from-reddit-and-other-web-forums/)
- **Tinder owner Match Group is slowing hiring to pay for its increased use of AI tools** — [techcrunch_ai](https://techcrunch.com/2026/05/06/tinder-owner-match-group-is-slowing-hiring-to-pay-for-its-increased-use-of-ai-tools/)
- **Apple to pay $250M to settle lawsuit over Siri’s delayed AI features** — [techcrunch_ai](https://techcrunch.com/2026/05/06/apple-to-pay-250m-to-settle-lawsuit-over-siris-delayed-ai-features/)
- **Ethos raises $22.75M from a16z for its expert network with voice onboarding** — [techcrunch_ai](https://techcrunch.com/2026/05/06/ethos-raises-22-75m-from-a16z-for-its-expert-network-with-voice-onboarding/)
- **voidborne-d/master-skill** — [github](https://github.com/voidborne-d/master-skill)
- **0xbl33p/goblintown** — [github](https://github.com/0xbl33p/goblintown)
- **awizemann/harness** — [github](https://github.com/awizemann/harness)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **KSroido/Kagi-Session2API-MCP** — [github](https://github.com/KSroido/Kagi-Session2API-MCP)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **warpdot-dev/craft-agents-oss** — [github](https://github.com/warpdot-dev/craft-agents-oss)
- **warpdot-dev/composio** — [github](https://github.com/warpdot-dev/composio)
- **lukiIabs/trading-agents** — [github](https://github.com/lukiIabs/trading-agents)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **YutoTerashima/agent-safety-eval-lab** — [github](https://github.com/YutoTerashima/agent-safety-eval-lab)
- **wjn1996/HeavySkill** — [github](https://github.com/wjn1996/HeavySkill)
- **alvinunreal/openpets** — [github](https://github.com/alvinunreal/openpets)
- **adithya-s-k/RL_Envs_101** — [github](https://github.com/adithya-s-k/RL_Envs_101)
- **prime-radiant-inc/books-for-bots** — [github](https://github.com/prime-radiant-inc/books-for-bots)
- **kostyay/pi-k-excalidraw** — [github](https://github.com/kostyay/pi-k-excalidraw)
- **Naroh091/hermes-war-room** — [github](https://github.com/Naroh091/hermes-war-room)
- **00后下场整顿Agent：啥都不学就能用好AI，这才是正确打开方式** — [qbitai](https://www.qbitai.com/2026/05/413612.html)
- **一年磨一剑，今年最炸机器人Demo来了！** — [qbitai](https://www.qbitai.com/2026/05/413830.html)
- **云知声山海知医慧保大模型重磅发布：以高密智能深耕高价值场景，重构医疗保险数智新生态** — [qbitai](https://www.qbitai.com/2026/05/413782.html)
- **波士顿动力泯然众人了，高管集体出走，机器人“量产”只能造4台** — [qbitai](https://www.qbitai.com/2026/05/413613.html)
- **英伟达重新思考AI TCO：为何每Token成本才是唯一重要的指标** — [qbitai](https://www.qbitai.com/2026/05/413604.html)
- **Token需求狂飙千倍，22亿热钱涌向这家AGI Infra头号玩家** — [qbitai](https://www.qbitai.com/2026/05/413591.html)
- **马斯克22万张GPU全卖给Claude用：5小时限额翻倍，双方合作建太空算力** — [qbitai](https://www.qbitai.com/2026/05/413569.html)
- **AI PPT，这次是真不用返工了** — [qbitai](https://www.qbitai.com/2026/05/413296.html)
- **香蕉和GPT Image之外的第3条路：华人15人团队造出AI生图黑马** — [qbitai](https://www.qbitai.com/2026/05/413264.html)
- **腾讯等入股机器人灵巧手研发商临界点** — [36kr](https://36kr.com/newsflashes/3798889072663809?f=rss)
- **苹果高价买“芯”：MacBook Neo生产目标提高至1000万台** — [36kr](https://36kr.com/newsflashes/3798867347135491?f=rss)
- **对话孙来春：年入25亿的林清轩不想做中国欧莱雅 ｜厚雪专访** — [36kr](https://36kr.com/p/3797662460419337?f=rss)
- **斯坦福博士后创立的柔性触觉传感器公司获超亿元融资，低成本触觉手套将量产落地｜硬氪首发** — [36kr](https://36kr.com/p/3797155747748867?f=rss)
- **像素绽放PixelBloom完成C轮融资，全面发力AI办公解决方案Agent：从“一分钟生成PPT”到“交付商用级结果”** — [36kr](https://36kr.com/p/3797787228151048?f=rss)
- **8点1氪丨三星宣布停止在中国大陆市场销售所有家电产品；李嘉诚抛售资产套现约455亿；月之暗面将完成20亿美元新融资，估值破200亿美元** — [36kr](https://36kr.com/p/3798462137637892?f=rss)
- **氪星晚报｜三星电子借AI热潮市值突破1万亿美元；智源发布业内首个心脏磁共振多模态诊断智能体BAAI Cardiac Agent；财政部今年将在香港发行840亿元人民币国债** — [36kr](https://36kr.com/p/3797482256325888?f=rss)
- **“鹰瞰智翼”完成Pre-A轮数千万元融资** — [36kr](https://36kr.com/newsflashes/3798919451712776?f=rss)