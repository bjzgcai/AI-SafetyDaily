# AI 日报 [AI 安全] - 2026-04-26


# 2026-04-26 AI 安全与治理日报：无状态攻击、意图错位与代理治理

**Highlights**

今日安全研究领域的核心突破集中在**多轮对话的无状态漏洞利用**与**对齐理论的意图重构**上。首先，**Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** 提出了一种新型攻击范式，揭示了大模型在缺乏长期上下文状态记忆时的策略性规避风险，标志着对抗攻击从单轮提示注入向多轮协同攻击的演进。其次，**Alignment has a Fantasia Problem** 从认知心理学角度挑战了现有对齐范式，指出用户意图的模糊性可能导致“幻想型交互”，为安全评估提供了新的理论视角。此外，**CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis** 发布了一个针对多轮代码提交累积漏洞的基准，暴露了传统静态分析在复杂供应链安全中的盲区。产业层面，Anthropic 的 Agent 交易市场实验与 OpenAI 关于未上报枪击案嫌疑人的道歉信，进一步凸显了自主智能体经济风险与责任归属的紧迫性。

## 对抗攻击与物理安全：从提示注入到跨模态欺骗

随着 LLM 在敏感工作流中的深度集成，对抗攻击的边界正从纯文本空间向物理世界与多模态融合领域扩展。**Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** 指出，现有的安全防御往往假设模型能维持多轮交互的上下文状态，但 TTI 攻击通过自动化智能体将对抗意图分散在孤立交互中，成功规避了基于短期上下文的策略执行。这与传统 Jailbreak 方法依赖维持单一会话状态形成鲜明对比，表明在分布式或无状态部署场景下，模型的安全边界存在系统性脆弱。

在物理感知层面，**Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** 与 **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles** 共同揭示了多传感器融合系统的潜在风险。前者针对机场安检用的毫米波成像提出了波形域攻击，后者则展示了如何通过协调摄像头与激光雷达的欺骗信号，使自动驾驶系统“看到”不存在的物体。这两项工作表明，冗余设计（Redundancy）在对抗攻击面前可能失效，攻击者可以通过伪造跨模态一致性来绕过融合算法的校验机制。

此外，**Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study** 关注了智能体技能经济的安全隐患。随着技能市场（Skill Marketplaces）的兴起，攻击者可以通过与公开智能体交互提取隐藏的专业指令（Skills）。这不仅是知识产权问题，更可能涉及敏感操作权限的泄露。相比之下，**Interpretable facial dynamics as behavioral and perceptual traces of deepfakes** 则从可解释性角度切入，试图通过生物行为特征而非深度学习黑盒来检测 Deepfake，为视频真实性验证提供了新的可解释路径。

## 模型对齐与可解释性：意图错位与道德认知

对齐研究正从单纯的任务遵循转向对人类意图与道德认知的深层理解。**Alignment has a Fantasia Problem** 提出，现代 AI 助手假设用户能清晰表达目标，但行为学研究显示用户意图往往是未成形的。当模型将模糊提示视为完整意图时，会产生“幻想型交互”（Fantasia interactions），这种对齐失败在安全评估中常被忽视。这与 **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** 的研究相呼应，后者通过“吹哨人困境”实验发现，模型在道德判断上缺乏人类对人际关系的敏感性，其决策往往偏离描述性社会期望。

在文化偏见方面，**Why are all LLMs Obsessed with Japanese Culture? On the Hidden Cultural and Regional Biases of LLMs** 揭示了模型在文化覆盖上的区域偏好，挑战了“去偏见化”的普遍假设。这种偏见可能影响模型在特定地区的合规性与安全性。为了解决模型记忆与事实可靠性的问题，**Revisiting Non-Verbatim Memorization in Large Language Models: The Role of Entity Surface Forms** 引入了 RedirectQA 数据集，通过关联实体表面形式的变体来区分事实记忆与访问路径，为评估模型的知识可靠性提供了更精细的指标。

在参数效率与安全微调的平衡上，**Low-Rank Adaptation Redux for Large Models** 与 **GiVA: Gradient-Informed Bases for Vector-Based Adaptation** 探讨了 PEFT 方法的安全影响。LoRA 虽已成为标准，但其架构选择与优化技术对模型行为的影响尚不明确。GiVA 提出基于梯度的初始化策略，旨在保持参数效率的同时降低训练成本，但其在对抗鲁棒性方面的表现仍需独立验证。

## 安全评估基准与工具链：动态测试与审计

现有的评估基准多侧重于静态能力，而今日发布的多个工作强调了动态与累积风险的评估。**MathDuels: Evaluating LLMs as Problem Posers and Solvers** 引入了一种自我博弈基准，让模型同时扮演出题者与解题者，通过对抗性提示生成问题来测试模型的边界。这种方法比静态数学基准更能区分模型的真实推理能力。

在代码安全领域，**CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis** 极具警示意义。它展示了 15 个真实 CVE 案例，其中每个单独的提交看似无害，但累积后产生严重漏洞。传统静态分析工具（如 Semgrep, Bandit）的每提交检测率仅为 13%，这暴露了供应链安全中“单点防御”的失效。与之互补的是 **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA**，它通过人类撰写的琐事问题评估音频推理能力，防止模型通过捷径策略（如元数据）作弊。

开源工具链方面，**Polaris**（GitHub）作为一个事务驱动的 AI 软件工厂内核，强调将 LLM 降级为受限决策组件，通过系统内核统一接管执行、审计与回滚，试图解决 Agent 不可控的问题。类似地，**Stash**（GitHub）提供了持久化的 Agent 记忆层，支持本地化部署，有助于在隐私敏感场景下管理 Agent 上下文。这些工具反映了社区对 Agent 可审计性与本地化控制的迫切需求。

## 智能体安全与治理：经济风险与责任归属

智能体（Agent）的自主性带来了新的治理挑战。**Nemobot Games: Crafting Strategic AI Gaming Agents for Interactive Learning with Large Language Models** 展示了利用 LLM 构建策略性游戏智能体的框架，虽然主要用于教育，但其背后的策略生成机制可被滥用。更为现实的是，**Anthropic created a test marketplace for agent-on-agent commerce**（TechCrunch 报道）显示，Anthropic 已实验 AI 智能体间的真实商品交易。这种经济闭环虽然展示了 Agent 的协作潜力，但也引入了金融欺诈、洗钱及合规风险。

在责任归属方面，**OpenAI CEO apologizes to Tumbler Ridge community**（TechCrunch 报道）提及 OpenAI 未向执法部门报告枪击案嫌疑人，引发了关于 AI 公司安全义务边界的讨论。这不仅是公关危机，更触及了 AI 系统监测与上报机制的伦理底线。相比之下，**Compliance Moral Hazard and the Backfiring Mandate** 从机制设计角度分析了金融机构在反洗钱中的信息聚合问题，提出的 TVA 机制为分散风险下的合规协作提供了理论参考。

对于中文科技媒体的报道，需保持审慎。**36 氪**关于“恒宇信通购买神导科技”或“欧莱雅 AI 创新”的报道多为商业并购或营销活动的二手信息，缺乏技术细节验证，不宜作为安全评估的依据。同样，**Qbit 科技**关于“Claude 降智”的报道虽引发关注，但“所有使用额度均已重置”等说法需区分是模型策略调整还是临时故障，不应直接作为模型能力退化的确凿证据。

## Looking Forward

尽管今日研究在攻击面扩展与评估基准上取得了进展，但若干理论问题仍未解决。首先，**Transient Turn Injection** 揭示的无状态漏洞在长上下文模型中是否依然有效？随着模型上下文窗口的扩大，状态管理可能成为新的安全边界。其次，**Alignment has a Fantasia Problem** 提出的意图模糊性，如何量化并纳入对齐损失函数？目前的 RLHF 主要依赖人类偏好，难以捕捉用户未成形的意图。最后，在智能体经济中，**CrossCommitVuln-Bench** 暴露的累积漏洞问题，如何扩展到多智能体协作的复杂系统中？未来的研究需关注动态环境下的安全验证，以及如何在开放经济系统中建立可追溯的责任机制。

---
*注：本综述基于公开学术预印本及行业报告整理，部分产业新闻（如 TechCrunch, 36 氪）内容未经独立技术验证，仅供参考。*

---


## 参考来源

- **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21860v1)
- **Enabling and Inhibitory Pathways of University Students' Willingness to Disclose AI Use: A Cognition-Affect-Conation Perspective** — [arxiv_ai](https://arxiv.org/abs/2604.21733v1)
- **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** — [arxiv_cl](https://arxiv.org/abs/2604.21871v1)
- **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** — [arxiv_lg](https://arxiv.org/abs/2604.21870v1)
- **GFlowState: Visualizing the Training of Generative Flow Networks Beyond the Reward** — [arxiv_lg](https://arxiv.org/abs/2604.21830v1)
- **Compliance Moral Hazard and the Backfiring Mandate** — [arxiv_lg](https://arxiv.org/abs/2604.21789v1)
- **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21774v1)
- **Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation** — [arxiv_ai](https://arxiv.org/abs/2604.21854v1)
- **Modulating Cross-Modal Convergence with Single-Stimulus, Intra-Modal Dispersion** — [arxiv_ai](https://arxiv.org/abs/2604.21836v1)
- **Alignment has a Fantasia Problem** — [arxiv_ai](https://arxiv.org/abs/2604.21827v1)
- **Quotient-Space Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2604.21809v1)
- **SyMTRS: Benchmark Multi-Task Synthetic Dataset for Depth, Domain Adaptation and Super-Resolution in Aerial Imagery** — [arxiv_ai](https://arxiv.org/abs/2604.21801v1)
- **Inferring High-Level Events from Timestamped Data: Complexity and Medical Applications** — [arxiv_ai](https://arxiv.org/abs/2604.21793v1)
- **Why are all LLMs Obsessed with Japanese Culture? On the Hidden Cultural and Regional Biases of LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21751v1)
- **MathDuels: Evaluating LLMs as Problem Posers and Solvers** — [arxiv_cl](https://arxiv.org/abs/2604.21916v1)
- **Mapping the Political Discourse in the Brazilian Chamber of Deputies: A Multi-Faceted Computational Approach** — [arxiv_cl](https://arxiv.org/abs/2604.21897v1)
- **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA** — [arxiv_cl](https://arxiv.org/abs/2604.21766v1)
- **Interpretable facial dynamics as behavioral and perceptual traces of deepfakes** — [arxiv_lg](https://arxiv.org/abs/2604.21760v1)
- **Ramen: Robust Test-Time Adaptation of Vision-Language Models with Active Sample Selection** — [arxiv_lg](https://arxiv.org/abs/2604.21728v1)
- **Seeing Fast and Slow: Learning the Flow of Time in Videos** — [arxiv_ai](https://arxiv.org/abs/2604.21931v1)
- **When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21911v1)
- **From Research Question to Scientific Workflow: Leveraging Agentic AI for Science Automation** — [arxiv_ai](https://arxiv.org/abs/2604.21910v1)
- **A Scale-Adaptive Framework for Joint Spatiotemporal Super-Resolution with Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2604.21903v1)
- **GiVA: Gradient-Informed Bases for Vector-Based Adaptation** — [arxiv_ai](https://arxiv.org/abs/2604.21901v1)
- **Nemobot Games: Crafting Strategic AI Gaming Agents for Interactive Learning with Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21896v1)
- **A Multi-Stage Warm-Start Deep Learning Framework for Unit Commitment** — [arxiv_ai](https://arxiv.org/abs/2604.21891v1)
- **TingIS: Real-time Risk Event Discovery from Noisy Customer Incidents at Enterprise Scale** — [arxiv_ai](https://arxiv.org/abs/2604.21889v1)
- **A Multimodal Text- and Graph-Based Approach for Open-Domain Event Extraction from Documents** — [arxiv_ai](https://arxiv.org/abs/2604.21885v1)
- **Addressing Image Authenticity When Cameras Use Generative AI** — [arxiv_ai](https://arxiv.org/abs/2604.21879v1)
- **Replay-buffer engineering for noise-robust quantum circuit optimization** — [arxiv_ai](https://arxiv.org/abs/2604.21863v1)
- **Evaluation of Automatic Speech Recognition Using Generative Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21928v1)
- **EVENT5Ws: A Large Dataset for Open-Domain Event Extraction from Documents** — [arxiv_cl](https://arxiv.org/abs/2604.21890v1)
- **Revisiting Non-Verbatim Memorization in Large Language Models: The Role of Entity Surface Forms** — [arxiv_cl](https://arxiv.org/abs/2604.21882v1)
- **SemEval-2026 Task 4: Narrative Story Similarity and Narrative Representation Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21782v1)
- **Misinformation Span Detection in Videos via Audio Transcripts** — [arxiv_cl](https://arxiv.org/abs/2604.21767v1)
- **Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability** — [arxiv_lg](https://arxiv.org/abs/2604.21930v1)
- **Fine-Tuning Regimes Define Distinct Continual Learning Problems** — [arxiv_lg](https://arxiv.org/abs/2604.21927v1)
- **The Sample Complexity of Multicalibration** — [arxiv_lg](https://arxiv.org/abs/2604.21923v1)
- **Low-Rank Adaptation Redux for Large Models** — [arxiv_lg](https://arxiv.org/abs/2604.21905v1)
- **Revealing Geography-Driven Signals in Zone-Level Claim Frequency Models: An Empirical Study using Environmental and Visual Predictors** — [arxiv_lg](https://arxiv.org/abs/2604.21893v1)
- **Beyond Expected Information Gain: Stable Bayesian Optimal Experimental Design with Integral Probability Metrics and Plug-and-Play Extensions** — [arxiv_lg](https://arxiv.org/abs/2604.21849v1)
- **On the algebra of Koopman eigenfunctions and on some of their infinities** — [arxiv_lg](https://arxiv.org/abs/2604.21825v1)
- **PrismaDV: Automated Task-Aware Data Unit Test Generation** — [arxiv_lg](https://arxiv.org/abs/2604.21765v1)
- **Transferable Physics-Informed Representations via Closed-Form Head Adaptation** — [arxiv_lg](https://arxiv.org/abs/2604.21761v1)
- **Neural surrogates for crystal growth dynamics with variable supersaturation: explicit vs. implicit conditioning** — [arxiv_lg](https://arxiv.org/abs/2604.21753v1)
- **CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis** — [arxiv_cr](https://arxiv.org/abs/2604.21917v1)
- **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles** — [arxiv_cr](https://arxiv.org/abs/2604.21841v1)
- **Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study** — [arxiv_cr](https://arxiv.org/abs/2604.21829v1)
- **An effective variant of the Hartigan $k$-means algorithm** — [arxiv_lg](https://arxiv.org/abs/2604.21798v1)
- **Anthropic created a test marketplace for agent-on-agent commerce** — [techcrunch_ai](https://techcrunch.com/2026/04/25/anthropic-created-a-test-marketplace-for-agent-on-agent-commerce/)
- **OpenAI CEO apologizes to Tumbler Ridge community** — [techcrunch_ai](https://techcrunch.com/2026/04/25/openai-ceo-apologizes-to-tumbler-ridge-community/)
- **Why Cohere is merging with Aleph Alpha** — [techcrunch_ai](https://techcrunch.com/2026/04/25/why-cohere-is-merging-with-aleph-alpha/)
- **Why Tokyo is the most important tech destination of 2026** — [techcrunch_ai](https://techcrunch.com/2026/04/25/why-tokyo-is-the-most-important-tech-destination-of-2026/)
- **Maine’s governor vetoes data center moratorium** — [techcrunch_ai](https://techcrunch.com/2026/04/25/maines-governor-vetoes-data-center-moratorium/)
- **Apple under Ternus: what comes next for the tech giant’s hardware strategy** — [techcrunch_ai](https://techcrunch.com/2026/04/25/apple-under-ternus-what-comes-next-for-the-tech-giants-hardware-strategy/)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **kimi-K2-6/kimi-K2.6** — [github](https://github.com/kimi-K2-6/kimi-K2.6)
- **kaktusesquire6rmu/ai-polymarket-agent** — [github](https://github.com/kaktusesquire6rmu/ai-polymarket-agent)
- **selmakcby/claude-agents-skills** — [github](https://github.com/selmakcby/claude-agents-skills)
- **jwangkun/hermes-agent-guide** — [github](https://github.com/jwangkun/hermes-agent-guide)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **dainsiahtill-dev/Polaris** — [github](https://github.com/dainsiahtill-dev/Polaris)
- **chaohong-ai/ai-auto-work** — [github](https://github.com/chaohong-ai/ai-auto-work)
- **muxprotocol/kalshi-trading-bot** — [github](https://github.com/muxprotocol/kalshi-trading-bot)
- **alash3al/stash** — [github](https://github.com/alash3al/stash)
- **chekusu/wanman** — [github](https://github.com/chekusu/wanman)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **K-Dense-AI/mimeo** — [github](https://github.com/K-Dense-AI/mimeo)
- **Zhou-Shilin/Aether** — [github](https://github.com/Zhou-Shilin/Aether)
- **g2i-ai/agents** — [github](https://github.com/g2i-ai/agents)
- **lydiaaam/llm-ui-coord-benchmark** — [github](https://github.com/lydiaaam/llm-ui-coord-benchmark)
- **simonw/llm-openai-via-codex** — [github](https://github.com/simonw/llm-openai-via-codex)
- **MrFadiAi/free-llm-gateway** — [github](https://github.com/MrFadiAi/free-llm-gateway)
- **realZillionX/InspireSkill** — [github](https://github.com/realZillionX/InspireSkill)
- **Claude终于认了！降智坐实，越聊越傻，3个bug全曝光** — [qbitai](https://www.qbitai.com/2026/04/407502.html)
- **全球首个医疗视频理解大模型开源！6k+组精标测试集与英雄榜同步上线，开发者速来！** — [qbitai](https://www.qbitai.com/2026/04/407486.html)
- **DeepSeek阮翀加盟元戎首秀，详解基座VLA，研发提效10倍** — [qbitai](https://www.qbitai.com/2026/04/407465.html)
- **华为发布ADS 5！强化世界模型路线，今年投入180亿** — [qbitai](https://www.qbitai.com/2026/04/407363.html)
- **恒宇信通：筹划购买神导科技100%股权，股票停牌** — [36kr](https://36kr.com/newsflashes/3783353736649734?f=rss)
- **陈茂波：今年以来香港新股集资额继续位列全球首位** — [36kr](https://36kr.com/newsflashes/3783317153209348?f=rss)
- **欧莱雅BRANDSTORM 2026中国总决赛落幕，AI成美妆创新核心议题｜最前线** — [36kr](https://36kr.com/p/3783249100397570?f=rss)
- **国信证券：结构上结合行业拥挤度均衡配置，重视科技成长主线、战略资源、以及白酒地产** — [36kr](https://36kr.com/newsflashes/3783131237653763?f=rss)
- **36氪首发 | 全球唯二、中国唯一造出微米级磁悬浮魔毯，已大规模量产** — [36kr](https://36kr.com/p/3782960065108996?f=rss)
- **润芯微“国产软硬一体AI智能基座”发布，破解行业稀缺难题带动多端智能变革** — [36kr](https://36kr.com/p/3782901034785801?f=rss)
- **科氪 | 国民好车深蓝L06增程版亮相北京车展 京东PLUS会员购车直减7000多元** — [36kr](https://36kr.com/p/3782437007039488?f=rss)
- **安波福发布“中国定义”核心战略** — [36kr](https://36kr.com/newsflashes/3783419976391684?f=rss)
- **京东启动AI硬件孵化计划** — [36kr](https://36kr.com/newsflashes/3783158630948103?f=rss)