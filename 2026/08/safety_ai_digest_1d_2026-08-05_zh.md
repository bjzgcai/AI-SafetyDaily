# AI 日报 [AI 安全] - 2026-08-05


# AI 安全每日综述：2026 年 8 月 5 日

## Highlights

今日 AI 安全领域的核心进展集中在自主智能体（Agent）的持久化记忆风险与自我进化机制的安全性上。**SkillJack** 揭示了自进化智能体中一种全新的持久化后门攻击路径，证明恶意经验可被转化为持久的行为缺陷，这标志着从上下文注入向模型内部技能污染的攻击范式转移。与此同时，**AntiSkillBench** 与 **PAST-Bench** 等基准测试的发布，系统性地量化了个人智能体在长期交互中的隐私泄露与自我改进能力，填补了长程一致性评估的空白。此外，针对多模态深度研究的 **Video-DeepResearch** 与结构化检索接口 **SIEVE** 进一步暴露了当前智能体在工具调用中的模态偏差与检索精度瓶颈，提示我们需要更严格的运行时约束机制。

## Agent 安全与治理

随着智能体从单次任务执行者向具备长期记忆与技能积累的自主实体演进，其安全风险已从单纯的提示词注入扩展至记忆库与技能库的深层污染。今日发布的 **SkillJack** 工作揭示了一个此前未被充分认知的根本性风险：在自进化智能体将交互历史转化为可复用技能的过程中，恶意输入的经验不仅能在检索时作为上下文干扰模型，更能被智能体自身的学习机制固化为持久的行为伪影。这意味着传统的基于上下文过滤的防御手段可能失效，因为攻击不再依赖于外部注入的 Prompt，而是利用了智能体“学习”这一核心功能本身。相比之下，**AntiSkillBench** 则侧重于评估个人技能（Persona Skills）在蒸馏过程中的隐私泄露与冒充风险，该基准通过 7,500 条对话轨迹证明了集中化的个人信号会放大碎片化信息的攻击面，挑战了仅针对单条记录设计的防御策略。这两项工作在攻击面与防御视角上形成了互补，前者展示了攻击如何利用进化机制，后者提供了评估此类风险的标准化框架。

在评估智能体长期行为一致性的方面，**PAST-Bench** 与 **ContinualSkillBench** 共同指向了递归自我改进能力的验证难题。**PAST-Bench** 通过隔离保留经验的影响，设计了 26 个场景来测试智能体是否真的能从过往经验中获益，而非仅仅依赖静态知识库。实验结果表明，许多声称具备自我改进能力的智能体在关闭记忆后表现并未显著下降，这引发了对当前“自我进化”宣传的质疑。而 **ContinualSkillBench** 则进一步考察了跨任务技能复用的有效性，发现顺序执行往往导致技能退化，除非有明确的交叉任务复用机制。这些基准测试的发现暗示，当前的 Agent 治理框架缺乏对“技能生命周期”的有效监控，特别是当技能被持久化存储时，如何防止其成为攻击载体（如 SkillJack 所示）以及如何确保其持续有效（如 PAST-Bench 所示），是未来治理的核心议题。此外，**MerchantBench** 虽然聚焦电商运营，但其强调的“长期一致性”概念同样适用于通用 Agent 治理，即要求系统在长周期内保持目标导向的行为稳定性，避免累积误差导致的失控。

关于记忆管理的具体实现，**GROVE** 提出了一种无需训练的框架，支持从连续视频流中因果增长记忆，既能进行问答式回忆也能主动识别情境相关性。这种分层记忆结构为缓解信息过载提供了新思路，但也引入了新的安全隐患：如果记忆增长过程缺乏审计，恶意视觉数据可能被编码进时间戳片段中，进而影响未来的决策逻辑。这与 **SkillJack** 的风险类似，但发生在感知层而非技能层。因此，Agent 治理不仅需要关注显式的技能库，还需建立对隐式记忆增长过程的监控机制，确保记忆内容的纯净性与可解释性。

## 工具调用、检索与运行时防御

智能体与外部环境的交互界面是运行时安全的关键防线。针对深度研究类智能体，**Search, Inspect, Fetch (SIEVE)** 提出了一种基于布尔检索的字段级接口，旨在解决现有代理在搜索访问流程中因读取整页内容而引入无关噪声的问题。SIEVE 允许智能体直接约束检索范围至文档字段，并通过结构丰富的结果卡进行筛选，这在理论上减少了上下文污染的风险。然而，这种精细化的控制也增加了系统的复杂性，若检索器本身存在漏洞，可能导致智能体无法获取关键信息从而产生幻觉。与之相对，**ExplainBench** 则关注代码生成智能体的输出解释的可信度评估。由于代码变更规模日益扩大，人工审查变得不可行，开发者转而依赖智能体生成的解释。该基准自动评估解释的质量，指出当前智能体在解释代码变更时可能存在过度自信或逻辑断裂，这构成了运行时信任链的薄弱环节。

在多模态交互领域，**Video-DeepResearch** 将智能体从静态图像扩展至连续视频流，这对时空定位提出了更高要求。初步评估显示，当前模型存在明显的模态偏差，倾向于绕过视觉工具而依赖文本搜索，以及参数知识泄露问题，即模型依赖内部记忆而非真实的工具增强执行。这表明现有的工具调用协议未能有效强制智能体使用外部感知能力，可能导致“空转”现象，即智能体看似在执行任务，实则未真正处理外部数据。为了应对这一问题，**ST-WAM** 在机器人操作领域指出了训练分布幻觉现象，即世界模型在视觉分布偏移时会幻觉出训练域内容而非忠实于当前场景。这进一步印证了单纯依赖预训练参数或静态世界模型的局限性，运行时环境必须提供动态反馈以校正模型的预测偏差。

## 推理鲁棒性与架构安全

除了应用层面的安全，底层模型的推理机制与架构稳定性同样面临严峻挑战。**When Many Answers Are Valid, Voting Fails** 一文通过 **CALVER** 符号验证器指出，基于多数投票的自我一致性方法在因果推理中可能失效，因为样本可能重复相同的混淆错误，导致无效答案胜出。CALVER 通过 Pearl 的因果标准对结构化轨迹进行评分，提供了一种不依赖参考答案的验证手段。这一发现对智能体的决策可靠性提出了警示，特别是在高风险场景中，简单的采样投票不足以保障安全性。

在模型架构层面，**When Attention Goes Blind** 揭示了 ALiBi 位置编码的一种数值失效模式：线性偏差缩放会导致浮点精度下溢，使大量注意力权重归零，导致注意力头部分失明。这一发现表明，即使是在最先进的预训练模型中，基础组件也可能存在未被察觉的数值缺陷，这可能被利用来破坏模型的注意力机制。此外，**ARCHead** 虽然主要关注量化压缩，但其提出的激活度量残差修正方法间接影响了模型输出的稳定性，特别是在 LM-head 量化过程中，若处理不当可能扰动词汇概率分布，进而影响推理的确定性。这些底层研究发现提醒我们，AI 安全不仅在于应用层的对抗，还在于对模型内部数值计算与注意力机制的深入理解与加固。

## Looking Forward

尽管今日的研究在 Agent 安全基准与特定攻击向量上取得了显著进展，但仍存在若干未解决的理论问题。首先，**SkillJack** 所揭示的技能持久化后门风险尚未有成熟的检测算法，现有的防御多集中于上下文过滤，缺乏对技能生成过程本身的完整性校验机制。其次，关于长期一致性，**PAST-Bench** 与 **ContinualSkillBench** 虽提供了评估工具，但尚未形成统一的理论框架来界定智能体在何种程度的经验积累后会产生不可逆的安全漂移。最后，在推理验证方面，**CALVER** 展示了符号验证的有效性，但在复杂多步骤任务中，如何将符号验证高效集成到实时推理循环中，仍是一个工程与理论的巨大挑战。未来的研究需要重点关注记忆增长过程的审计标准、技能库的权限隔离机制，以及结合数值稳定性分析的模型鲁棒性评估体系。

---


## 参考来源

- **ExplainBench: Evaluating Code Explanations from Agents** — [huggingface_papers](https://arxiv.org/abs/2607.26451)
- **Quo Vadis, World Modeling?** — [huggingface_papers](https://arxiv.org/abs/2608.02713)
- **PAST-Bench: Benchmarking the Foundations of Recursive Self-Improvement in Personal Agents** — [huggingface_papers](https://arxiv.org/abs/2608.04003)
- **SkillJack: Persistent Skill Backdoors in Self-Evolving Agents** — [huggingface_papers](https://arxiv.org/abs/2608.03509)
- **LegalPincite: Multi-level Legal Information Retrieval Dataset** — [huggingface_papers](https://arxiv.org/abs/2608.03756)
- **Search, Inspect, Fetch: Exploiting Boolean Retrieval for Deep-Research Agents** — [huggingface_papers](https://arxiv.org/abs/2608.02751)
- **When Agents Learn to Be You: Benchmarking Privacy Leakage, Impersonation Risk, and Defenses in Persona Skills** — [huggingface_papers](https://arxiv.org/abs/2608.03700)
- **MerchantBench: Benchmarking LLM Agents for Long-Term Coherence in E-Commerce Operations** — [huggingface_papers](https://arxiv.org/abs/2607.28956)
- **Video-DeepResearch: Towards the Next-Generation Multimodal Deepresearch Agent** — [huggingface_papers](https://arxiv.org/abs/2608.03979)
- **GROVE: Growing and Reasoning over Temporally Stratified Memory from Streaming Video Experience** — [huggingface_papers](https://arxiv.org/abs/2608.02392)
- **ContinualSkillBench: Can LLM Agents Truly Evolve Their Capabilities?** — [huggingface_papers](https://arxiv.org/abs/2608.03874)
- **PCSD: Persistent Consistency for Self-Distillation in Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2608.01837)
- **PosterMELD: Multi-Agent Paper-to-Poster Generation for Controllable Design Diversity with Editable Print-Ready Outputs** — [huggingface_papers](https://arxiv.org/abs/2608.02218)
- **ARCHead: Activation-Metric Residual Correction for Large Language Model Output Heads** — [huggingface_papers](https://arxiv.org/abs/2608.02703)
- **When Attention Goes Blind: Numerical Failure in ALiBi Positional Encodings** — [huggingface_papers](https://arxiv.org/abs/2608.03994)
- **CAPEval: A Decoupled Caption Evaluation across Understanding and Generation** — [huggingface_papers](https://arxiv.org/abs/2608.02589)
- **ST-WAM: Semantic-Temporal World Action Model for Robust Manipulation under Visual Distribution Shifts** — [huggingface_papers](https://arxiv.org/abs/2607.28993)
- **When Many Answers Are Valid, Voting Fails: Symbolic Verification for Best-of-K Causal Reasoning in LLMs** — [huggingface_papers](https://arxiv.org/abs/2608.03506)
- **UniWorld-Design: From Pixel Generation to Layer-Native Design** — [huggingface_papers](https://arxiv.org/abs/2608.03971)
- **ChronoLens: Measuring Language Change Across Time, Languages, and Linguistic Levels** — [huggingface_papers](https://arxiv.org/abs/2608.03507)