# AI 日报 [AI 安全] - 2026-05-15


# 2026-05-15 AI 安全与治理每日综述

## Highlights

今日安全研究领域的核心突破集中在**大模型攻击面的扩展**与**隐私审计的实用化**两个方向。首先，**MetaBackdoor: Exploiting Positional Encoding as a Backdoor Attack Surface in LLMs** 揭示了基于 Transformer 架构的 LLM 存在新型后门攻击路径，攻击者无需修改文本内容即可利用位置编码触发恶意行为，这对现有的基于内容过滤的防御体系提出了严峻挑战。其次，**Privacy Auditing with Zero (0) Training Run** 提出了一种无需干预训练流程的后验隐私审计框架，解决了大型部署模型中难以进行差分隐私参数验证的痛点。此外，针对 Agent 安全，**WARD: Adversarially Robust Defense of Web Agents Against Prompt Injections** 展示了在开放 Web 环境中防御提示注入攻击的新范式。产业层面，尽管 Musk 与 Altman 的诉讼案进入尾声，但关于 AI 数据主权与隐私泄露的讨论（如 MIT Tech Review 报道的 Deepfake 隐私问题）持续升温，凸显了治理框架滞后于技术发展的现状。

## 对抗攻击与鲁棒性

当前对抗攻击研究正从传统的输入扰动向更隐蔽的架构层面渗透。**MetaBackdoor: Exploiting Positional Encoding as a Backdoor Attack Surface in LLMs** 与 **One Step to the Side: Why Defenses Against Malicious Finetuning Fail Under Adaptive Adversaries** 共同指向了模型内部表示的脆弱性。前者指出位置编码本身可作为触发器，这意味着传统的基于文本内容的检测机制可能完全失效；后者则表明，针对恶意微调的防御机制在面对自适应攻击者时往往存在单一弱点，即防御者试图掩盖或误导攻击路径，反而暴露了新的攻击面。这两项工作互为补充，揭示了模型鲁棒性不仅取决于训练数据的质量，更取决于对模型内部机制（如位置编码、微调过程）的深层理解。

在评估与检测方面，**The Great Pretender: A Stochasticity Problem in LLM Jailbreak** 对现有的 Jailbreak 评估方法提出了质疑，指出某些声称具有高攻击成功率（ASR）的方法可能受随机性影响，无法在独立验证中复现。这与 **Talk is (Not) Cheap: A Taxonomy and Benchmark Coverage Audit for LLM Attacks** 的结论相呼应，后者通过构建 4x6 的目标 - 技术矩阵，发现主流基准（如 HarmBench, InjecAgent）在覆盖威胁面方面存在显著缺失。这表明当前的对抗评估可能存在“虚假繁荣”，即基准测试的通过率提升并不等同于真实安全性的增强。相比之下，**Can Visual Mamba Improve AI-Generated Image Detection?** 则尝试从架构层面改进检测能力，探索视觉 Mamba 在识别 AI 生成图像方面的潜力，为多模态内容的真实性验证提供了新的技术路径。

## 隐私保护与联邦学习

隐私保护研究正从理论优化转向工程落地。**Privacy Auditing with Zero (0) Training Run** 提出的零训练运行审计框架，利用固定数据集进行后验分析，避免了大型部署模型重新训练的高昂成本，为合规性审计提供了可操作的工具。这与 **Limits of Personalizing Differential Privacy Budgets** 的理论发现形成对比，后者指出在均值估计任务中，完全个性化的隐私预算并非最优解，简单的阈值操作即可达到相近效果，这为实际部署中的隐私预算分配提供了简化依据。

在联邦学习领域，**DisAgg: Distributed Aggregators for Efficient Secure Aggregation in Federated Learning** 针对现有安全聚合协议通信轮次多、计算开销大的问题，提出了分布式聚合器方案，旨在平衡隐私保护与通信效率。这一方向与 **Backdoor Threats in Variational Quantum Circuits: Taxonomy, Attacks, and Defenses** 中关于量子计算安全性的探讨形成跨领域的呼应，尽管后者关注的是量子电路中的后门风险，但两者都强调了在分布式或协作式计算环境中，数据与模型更新过程中的潜在泄露风险。值得注意的是，**Toward Covert Quantum Computing** 进一步探讨了量子计算环境下的隐私问题，提出了隐蔽量子计算的概念，这在多租户云平台上对于防止同机用户探测计算行为具有重要意义。

## Agent 安全与治理

随着 Agent 系统从聊天界面走向自主执行任务，安全边界正在从“回答质量”向“操作后果”转移。**WARD: Adversarially Robust Defense of Web Agents Against Prompt Injections** 针对 Web Agent 在开放环境中易受 HTML 或视觉界面注入攻击的问题，提出了鲁棒防御方案，解决了现有 Guard 模型泛化能力差、误报率高的问题。**Do Coding Agents Understand Least-Privilege Authorization?** 则通过 AuthBench 基准测试，发现当前模型在推断最小权限授权边界方面仍存在不足，这直接关联到 Agent 在访问文件系统或执行 Shell 命令时的安全风险。

在长期安全适应方面，**LiSA: Lifelong Safety Adaptation via Conservative Policy Induction** 强调了 Guardrails 需要适应本地隐私规范和组织政策，而非仅依赖预部署规范。这与 **Angel or Demon: Investigating the Plasticity Interventions' Impact on Backdoor Threats in Deep Reinforcement Learning** 的研究形成对比，后者关注深度强化学习中的可塑性干预对后门漏洞的影响，指出现有研究多集中于 Vanilla 场景，而忽略了现代 Agent 中内置的可塑性组件可能带来的风险。此外，**Talk is (Not) Cheap: A Taxonomy and Benchmark Coverage Audit for LLM Attacks** 指出，现有的攻击基准在覆盖威胁面方面存在不足，这要求 Agent 安全评估必须超越单一基准，采用更全面的威胁建模。

## 安全评估基准与工具

安全评估基准的建设正在向多模态和特定领域深化。**ROK-FORTRESS: Measuring the Effect of Geopolitical Transcreation for National Security and Public Safety** 引入了双语、文化对抗的 NSPS 基准，利用英韩语言对和美韩地缘政治轴，填补了多语言安全评估的空白。**EVA-Bench: A New End-to-end Framework for Evaluating Voice Agents** 则专注于语音 Agent 的评估，解决了模拟对话生成与语音特定失败模式测量的挑战。在视觉与记忆方面，**MemEye: A Visual-Centric Evaluation Framework for Multimodal Agent Memory** 指出现有评估往往忽略视觉证据的保留，而 **PDI-Bench (Perspective Distortion Index)** 则提供了量化视频生成中几何一致性的框架。

开源工具生态也在同步发展。**secureagentics/Adrian** 提供了运行时安全监控与控制，能够实时捕获恶意工具使用和策略漂移。**outputguard** 专注于验证和修复 LLM 结构化输出，提供多种 JSON 修复策略。在联邦学习与隐私计算方面，**DisAgg** 的开源实现为高效安全聚合提供了参考。这些工具与基准的结合，正在构建一个从理论评估到工程防御的完整闭环。然而，**Talk is (Not) Cheap** 的审计结果显示，即便有这些工具，基准覆盖的不足仍可能导致防御盲区。

## 行业观察与治理挑战

产业层面的动态反映了安全治理的紧迫性。Musk 与 Altman 的诉讼案进入最后阶段，虽然主要涉及公司治理与使命偏离，但其背后折射出 AI 公司权力结构与公众利益之间的张力。MIT Tech Review 报道的 Deepfake 隐私泄露事件（如面部识别导致旧色情视频被关联）

---


## 参考来源

- **Privacy Auditing with Zero (0) Training Run** — [arxiv_cr](https://arxiv.org/abs/2605.14591v1)
- **XAI and Statistical Analysis for Reliable Intrusion Detection in the UAVIDS-2025 Dataset: From Tree to Hybrid and Tabular DNN Ensembles** — [arxiv_cr](https://arxiv.org/abs/2605.13922v1)
- **MetaBackdoor: Exploiting Positional Encoding as a Backdoor Attack Surface in LLMs** — [arxiv_cr](https://arxiv.org/abs/2605.15172v1)
- **Analyzing Codes of Conduct for Online Safety in Video Games at Scale** — [arxiv_cr](https://arxiv.org/abs/2605.15047v1)
- **WARD: Adversarially Robust Defense of Web Agents Against Prompt Injections** — [arxiv_cr](https://arxiv.org/abs/2605.15030v1)
- **Do Coding Agents Understand Least-Privilege Authorization?** — [arxiv_cr](https://arxiv.org/abs/2605.14859v1)
- **Can Visual Mamba Improve AI-Generated Image Detection? An In-Depth Investigation** — [arxiv_cr](https://arxiv.org/abs/2605.14799v1)
- **EVA: Editing for Versatile Alignment against Jailbreaks** — [arxiv_cr](https://arxiv.org/abs/2605.14750v1)
- **LiSA: Lifelong Safety Adaptation via Conservative Policy Induction** — [arxiv_cr](https://arxiv.org/abs/2605.14454v1)
- **The Great Pretender: A Stochasticity Problem in LLM Jailbreak** — [arxiv_cr](https://arxiv.org/abs/2605.14418v1)
- **Toward Covert Quantum Computing** — [arxiv_cr](https://arxiv.org/abs/2605.14325v1)
- **Day-to-Day Traffic Network Modeling under Route-Guidance Misinformation: Endogenous Trust and Resilience in CAV Environments** — [arxiv_cr](https://arxiv.org/abs/2605.14204v1)
- **ROK-FORTRESS: Measuring the Effect of Geopolitical Transcreation for National Security and Public Safety** — [arxiv_cr](https://arxiv.org/abs/2605.14152v1)
- **Backdoor Threats in Variational Quantum Circuits: Taxonomy, Attacks, and Defenses** — [arxiv_cr](https://arxiv.org/abs/2605.13796v1)
- **DisAgg: Distributed Aggregators for Efficient Secure Aggregation in Federated Learning** — [arxiv_cr](https://arxiv.org/abs/2605.13708v1)
- **Ideology Prediction of German Political Texts** — [huggingface_papers](https://arxiv.org/abs/2605.14352)
- **Limits of Personalizing Differential Privacy Budgets** — [arxiv_cr](https://arxiv.org/abs/2605.13503v1)
- **Talk is (Not) Cheap: A Taxonomy and Benchmark Coverage Audit for LLM Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.15118v1)
- **One Step to the Side: Why Defenses Against Malicious Finetuning Fail Under Adaptive Adversaries** — [arxiv_cr](https://arxiv.org/abs/2605.14605v1)
- **Angel or Demon: Investigating the Plasticity Interventions' Impact on Backdoor Threats in Deep Reinforcement Learning** — [arxiv_cr](https://arxiv.org/abs/2605.14587v1)
- **Systematic Discovery of Semantic Attacks in Online Map Construction through Conditional Diffusion** — [arxiv_cr](https://arxiv.org/abs/2605.14396v1)
- **Warp-as-History: Generalizable Camera-Controlled Video Generation from One Training Video** — [huggingface_papers](https://arxiv.org/abs/2605.15182)
- **Learning to Build the Environment: Self-Evolving Reasoning RL via Verifiable Environment Synthesis** — [huggingface_papers](https://arxiv.org/abs/2605.14392)
- **Self-Distilled Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.15155)
- **Quantitative Video World Model Evaluation for Geometric-Consistency** — [huggingface_papers](https://arxiv.org/abs/2605.15185)
- **ATLAS: Agentic or Latent Visual Reasoning? One Word is Enough for Both** — [huggingface_papers](https://arxiv.org/abs/2605.15198)
- **RAVEN: Real-time Autoregressive Video Extrapolation with Consistency-model GRPO** — [huggingface_papers](https://arxiv.org/abs/2605.15190)
- **Topology-Preserving Neural Operator Learning via Hodge Decomposition** — [huggingface_papers](https://arxiv.org/abs/2605.13834)
- **EVA-Bench: A New End-to-end Framework for Evaluating Voice Agents** — [huggingface_papers](https://arxiv.org/abs/2605.13841)
- **RealICU: Do LLM Agents Understand Long-Context ICU Data? A Benchmark Beyond Behavior Imitation** — [huggingface_papers](https://arxiv.org/abs/2605.13542)
- **FrameSkip: Learning from Fewer but More Informative Frames in VLA Training** — [huggingface_papers](https://arxiv.org/abs/2605.13757)
- **Vividh-ASR: A Complexity-Tiered Benchmark and Optimization Dynamics for Robust Indic Speech Recognition** — [huggingface_papers](https://arxiv.org/abs/2605.13087)
- **F-GRPO: Factorized Group-Relative Policy Optimization for Unified Candidate Generation and Ranking** — [huggingface_papers](https://arxiv.org/abs/2605.12995)
- **VGGT-Edit: Feed-forward Native 3D Scene Editing with Residual Field Prediction** — [huggingface_papers](https://arxiv.org/abs/2605.15186)
- **Darwin Family: MRI-Trust-Weighted Evolutionary Merging for Training-Free Scaling of Language-Model Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.14386)
- **MemEye: A Visual-Centric Evaluation Framework for Multimodal Agent Memory** — [huggingface_papers](https://arxiv.org/abs/2605.15128)
- **Orchard: An Open-Source Agentic Modeling Framework** — [huggingface_papers](https://arxiv.org/abs/2605.15040)
- **Nexus : An Agentic Framework for Time Series Forecasting** — [huggingface_papers](https://arxiv.org/abs/2605.14389)
- **LLM-based Detection of Manipulative Political Narratives** — [huggingface_papers](https://arxiv.org/abs/2605.14354)
- **Beyond Individual Intelligence: Surveying Collaboration, Failure Attribution, and Self-Evolution in LLM-based Multi-Agent Systems** — [huggingface_papers](https://arxiv.org/abs/2605.14892)
- **Elon Musk’s SpaceXAI has been bleeding staff since its merger** — [techcrunch_ai](https://techcrunch.com/2026/05/14/elon-musks-spacexai-has-been-bleeding-staff-since-its-merger/)
- **Establishing AI and data sovereignty in the age of autonomous systems** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137168/establishing-ai-and-data-sovereignty-in-the-age-of-autonomous-systems/)
- **Closing time** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/931006/musk-v-altman-closing-arguments-analysis)
- **What happens when AI starts building itself?** — [techcrunch_ai](https://techcrunch.com/2026/05/14/what-happens-when-ai-starts-building-itself/)
- **OpenAI is reportedly preparing legal action against Apple; it wouldn’t be the first partner to feel burned** — [techcrunch_ai](https://techcrunch.com/2026/05/14/openai-is-reportedly-preparing-legal-action-against-apple-it-wouldnt-be-the-first-partner-to-feel-burned/)
- **Behold, the Elon Musk jackass trophy** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/930893/elon-musk-sam-altman-trial-ai-safety-jackass-statue)
- **OpenAI’s Codex is now in the ChatGPT mobile app** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/930763/openai-codex-chatgpt-ios-android-app-preview)
- **Microsoft starts canceling Claude Code licenses** — [theverge_ai](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad)
- **Use this map to find the data centers in your backyard** — [theverge_ai](https://www.theverge.com/policy/930629/data-center-policy-map-interactive)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **Americans do not want AI data centers in their backyards** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/930477/ai-data-centers-gallup-survey-70-percent-opposition)
- **Data readiness for agentic AI in financial services** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137034/data-readiness-for-agentic-ai-in-financial-services/)
- **The Download: deepfake porn’s stolen bodies and AI sharing private numbers** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137257/the-download-deepfake-porn-bodies-ai-exposing-phone-numbers/)
- **The Tesla Semi could be a big deal for electric trucking** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137197/tesla-semi-electric-trucking/)
- **You can make an app for that** — [theverge_ai](https://www.theverge.com/tech/928905/vibe-code-personal-software-revolution)
- **The shock of seeing your body used in deepfake porn** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137161/ai-porn-nonconsensual-deepfakes-takedown-piracy-copyright/)
- **Who decides what AI tells you? Campbell Brown, once Meta’s news chief, has thoughts** — [techcrunch_ai](https://techcrunch.com/2026/05/13/who-decides-what-ai-tells-you-campbell-brown-once-metas-news-chief-has-thoughts/)
- **What the jury will actually decide in the case of Elon Musk vs. Sam Altman** — [techcrunch_ai](https://techcrunch.com/2026/05/14/what-the-jury-will-actually-decide-in-the-case-of-elon-musk-vs-sam-altman/)
- **OpenAI says Codex is coming to your phone** — [techcrunch_ai](https://techcrunch.com/2026/05/14/openai-says-codex-is-coming-to-your-phone/)
- **Clawdmeter turns your Claude Code usage stats into a tiny desktop dashboard** — [techcrunch_ai](https://techcrunch.com/2026/05/14/clawdmeter-turns-your-claude-code-usage-stats-into-a-tiny-desktop-dashboard/)
- **Cerebras raises $5.5B, then stock pops $108%, in the first huge tech IPO of 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/14/cerebras-raises-5-5b-kicking-off-2026s-ipo-season-with-a-bang/)
- **Khosla Ventures is betting $10M on Ian Crosby, whose first startup, Bench, imploded** — [techcrunch_ai](https://techcrunch.com/2026/05/14/khosla-ventures-is-betting-10m-on-ian-crosby-whose-last-startup-bench-imploded/)
- **Cisco cuts nearly 4,000 jobs to spend more on AI, reports ‘record quarterly revenue’** — [techcrunch_ai](https://techcrunch.com/2026/05/14/cisco-cuts-nearly-4000-jobs-to-spend-more-on-ai-reports-record-quarterly-revenue/)
- **Two weeks left: Startup Battlefield 200 applications close May 27** — [techcrunch_ai](https://techcrunch.com/2026/05/14/two-weeks-left-startup-battlefield-200-applications-close-may-27/)
- **Wirestock raises $23M to supply creative multimodal data to AI labs** — [techcrunch_ai](https://techcrunch.com/2026/05/14/wirestock-raises-23m-to-supply-multi-modal-data-to-ai-labs/)
- **Work with Codex from anywhere** — [openai](https://openai.com/index/work-with-codex-from-anywhere)
- **Clio’s $500M milestone arrives just as Anthropic ups the ante** — [techcrunch_ai](https://techcrunch.com/2026/05/13/clios-500m-milestone-arrives-just-as-anthropic-ups-the-ante/)
- **secureagentics/Adrian** — [github](https://github.com/secureagentics/Adrian)
- **simonlin1212/TradingAgents-astock** — [github](https://github.com/simonlin1212/TradingAgents-astock)
- **r0b0tlab/hermes-concurrent-agents** — [github](https://github.com/r0b0tlab/hermes-concurrent-agents)
- **DeepExperience/HyperEyes** — [github](https://github.com/DeepExperience/HyperEyes)
- **ldpGitHub/ai-app-bridge** — [github](https://github.com/ldpGitHub/ai-app-bridge)
- **TehreemArbab/JazzCashMCP** — [github](https://github.com/TehreemArbab/JazzCashMCP)
- **talentsache/aipointer** — [github](https://github.com/talentsache/aipointer)
- **johunsang/semble_rs** — [github](https://github.com/johunsang/semble_rs)
- **PlaceNL2026/okx-agent-trade-kit** — [github](https://github.com/PlaceNL2026/okx-agent-trade-kit)
- **ndcorder/outputguard** — [github](https://github.com/ndcorder/outputguard)
- **python-telegramBot/ai-auto-trading** — [github](https://github.com/python-telegramBot/ai-auto-trading)
- **cosmicstack-labs/mercury-agent-skills** — [github](https://github.com/cosmicstack-labs/mercury-agent-skills)
- **Isoform/yansu-skill** — [github](https://github.com/Isoform/yansu-skill)
- **sno-ai/llmix** — [github](https://github.com/sno-ai/llmix)
- **ab-613/OpenGravity** — [github](https://github.com/ab-613/OpenGravity)
- **mikesheehan54/Claude-Code-Design-AI** — [github](https://github.com/mikesheehan54/Claude-Code-Design-AI)
- **yaassin12/DeepSeek-V4-Pro-App** — [github](https://github.com/yaassin12/DeepSeek-V4-Pro-App)
- **yetone/native-feel-skill** — [github](https://github.com/yetone/native-feel-skill)
- **nexu-io/html-anything** — [github](https://github.com/nexu-io/html-anything)
- **zghhui/OmniNFT** — [github](https://github.com/zghhui/OmniNFT)
- **人手一个数据库，Kimi背后这套AI基建到底有多能扛？** — [qbitai](https://www.qbitai.com/2026/05/417731.html)
- **重生之我在AI时代当老板：让一群Agent互相PUA** — [qbitai](https://www.qbitai.com/2026/05/417816.html)
- **淘天金码奖落幕：20 名超级工程师诞生，推动 AI Native 实践** — [qbitai](https://www.qbitai.com/2026/05/417927.html)
- **国产GPU组了个开源局，把SGLang等核心开发者都摇来了！** — [qbitai](https://www.qbitai.com/2026/05/417791.html)
- **Robotaxi第一股又涨疯了** — [qbitai](https://www.qbitai.com/2026/05/417754.html)
- **腾讯开源 Agent 记忆技术方案，Token 消耗最高降低 61%** — [qbitai](https://www.qbitai.com/2026/05/417753.html)
- **阿里 AI 应用新进展：悟空开始逐步规模化放量** — [qbitai](https://www.qbitai.com/2026/05/417748.html)
- **田渊栋AI创业估值315亿，老黄苏妈都投了，姚班施天麟也是合伙人** — [qbitai](https://www.qbitai.com/2026/05/417468.html)
- **亚历山大王回应一切：LeCun、Manus，“我的父母都是中国人”** — [qbitai](https://www.qbitai.com/2026/05/417488.html)
- **36氪首发｜航天发动机核心部件厂商获投，国内唯一具备核心部件一站式制造能力的民营企业** — [36kr](https://36kr.com/p/3809936183860740?f=rss)
- **麦记牛奶谢永亮：2025年是唯一窗口期，糖水赛道胜负已定｜厚雪专访** — [36kr](https://36kr.com/p/3809931035844359?f=rss)
- **36氪首发 | 前大疆核心成员做消费级CNC，获美团、昆仑资本、奇绩创坛投资近亿元** — [36kr](https://36kr.com/p/3809919654403587?f=rss)
- **2026年上半年最火赛道：具身智能行业前4月融资超200笔，总规模超550亿元** — [36kr](https://36kr.com/p/3809911566704388?f=rss)
- **抢跑618，iPhone 17 Pro系列首次官方降价** — [36kr](https://36kr.com/newsflashes/3809908500225540?f=rss)
- **阿里巴巴等来收获期，外卖大战已无大波澜** — [36kr](https://36kr.com/p/3807527591058948?f=rss)
- **丰田提交申请，拟在美国得克萨斯州斥资20亿美元建厂** — [36kr](https://36kr.com/newsflashes/3809866940030720?f=rss)
- **独家对谈｜广告人小马宋的烟火与锋芒：非精英们的精英生存指南** — [36kr](https://36kr.com/p/3807543008698118?f=rss)
- **8点1氪丨周大福回应金饰又涨价；韩国一季度未成年人股票账户暴涨近十倍；张雪机车820RR暂停生产交付** — [36kr](https://36kr.com/p/3809785128869641?f=rss)
- **氪星晚报｜千里智驾CEO辟谣离职传闻；三星在计划罢工前夕启动减产** — [36kr](https://36kr.com/p/3809007831375621?f=rss)
- **腾讯要懂得花钱** — [36kr](https://36kr.com/p/3808999399497221?f=rss)
- **三大指数全部翻红** — [36kr](https://36kr.com/newsflashes/3809972223532550?f=rss)
- **Anthropic同意以9000亿美元估值开展融资轮的条款** — [36kr](https://36kr.com/newsflashes/3809965649157639?f=rss)