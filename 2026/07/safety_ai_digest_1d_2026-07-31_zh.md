# AI 日报 [AI 安全] - 2026-07-31


# AI 安全每日综述：2026 年 7 月 31 日

## Highlights

当日研究进展集中揭示了智能体（Agent）在长期记忆持久化、多步任务执行及跨模态推理中的深层安全隐患。首先，文件系统作为智能体外部记忆的默认载体，其组织演化过程缺乏形式化验证，可能导致敏感数据泄露或状态冲突，相关研究指出这一默认假设尚未经过系统性测试。其次，深度研究类智能体在面对误导性知识时表现出显著的脆弱性，现有工作构建了专门框架以验证此类信息注入如何导致错误结论。最后，面向真实设备的图形用户界面（GUI）智能体在部署中面临沙盒隔离不足的风险，而针对多智能体系统的信任评估机制仍处于理论探索阶段，亟需建立可量化的可靠性记忆模型。

## Agent 安全与治理

智能体安全的核心正从单纯的提示词防护转向运行时状态管理与记忆治理，当日多篇工作共同指向了记忆持久化带来的新型攻击面。传统系统倾向于设计专用的记忆表示并研究检索效率，却忽视了将长程记忆存储为文件系统目录树所带来的实际风险。**《Filesystem-Based Memory for LLM Agents: Organization, Evolution, and Sustainability》** 首次系统性地探讨了基于文件系统的智能体记忆，指出随着记忆积累、冲突和过时，智能体能否保持存储有序且这种组织方式是否有效仍是未经验证的假设。这意味着现有的文件系统访问权限控制可能不足以防止恶意写入或逻辑混乱导致的意外行为，特别是在涉及通用文件工具调用时，攻击者可能利用路径遍历或权限提升破坏记忆结构。

为了应对多智能体协作中的信任问题，**《Σ-Mem: An Online Reliability Memory for LLM-based Multi-Agent Systems》** 提出了一种在线可靠性记忆机制，旨在记录个体同伴的历史能力证据及同伴关系证据。该工作强调现有系统主要保存交互内容而非建模信任条件，这在无法直接验证同伴响应的复杂系统中尤为关键。与之互补的是，**《AI Tour Meeting: Group Travel Planning by LLM Agents》** 提供了一个多智能体协作模拟框架，通过配置不同人格和讨论工作流来监测行为，但其主要用途仍停留在分析层面，尚未形成实时的防御机制。这两项工作共同揭示了多智能体治理的难点在于如何将抽象的信任关系转化为可计算的实时状态，以便在决策过程中动态调整权限。

在智能体的执行环境方面，**《Qwen-UI-Agent Technical Report: Toward Next-Generation Real-World Centric Foundation GUI Agents》** 展示了跨越移动、桌面及 Web 环境的通用执行能力，但报告侧重于功能愿景而非安全边界。当智能体能够自主操作真实设备时，沙盒隔离和工具调用审计变得至关重要。虽然当前开源社区尚未提供成熟的 GUI 智能体运行时沙盒标准，但 **《Echoverse: Deep, Evolving Environments for Training Computer-Use Agents at Scale》** 指出训练计算机使用智能体需要能够被操作、破坏和重置的应用程序，这暗示了合成环境的安全性直接影响模型在真实世界中的泛化表现。如果训练环境缺乏足够的安全约束，模型可能习得绕过限制的策略，从而在部署后引发不可控后果。

此外，证据溯源与可解释性是治理的关键环节。**《LEDGERMIND: Provenance-Constrained Multimodal Agentic Reasoning with a Structured Evidence Ledger》** 提出将多模态智能体轨迹视为受溯源约束的状态机，工具输出被规范化为结构化证据账本。这种方法允许下游推理和决策声明受到账本状态的约束，从而区分正确答案是通过接地证据还是语言先验获得的。这与 **《AskChem: Claim-Centered Infrastructure for Chemistry Literature Synthesis》** 的理念一致，后者将检索单元从论文转变为携带来源证明的原子声明。尽管这些工作在特定领域（如化学文献）展示了潜力，但在通用场景下，构建和维护这种结构化证据账本的开销及其对抗性篡改的防御能力仍需进一步验证。

值得注意的是，**《Metis: Memory Foundation Model》** 尝试将原生记忆能力内化到基础模型中，而非依赖外部模块。这项工作从持久性和动态演化的角度形式化了原生记忆，试图解决外部模块带来的上下文窗口限制。然而，将记忆参数化是否会导致记忆污染难以检测，以及原生记忆是否会成为新的对齐漏洞，目前尚无定论。相比之下，**《Memory Decoder at Scale》** 研究了参数量级扩展后的记忆解码器，发现标准索引管道在大规模数据下不可行，提出了分布式检索方案。这表明随着记忆规模扩大，检索效率与安全性的平衡将成为工程实现的瓶颈，特别是当记忆内容包含敏感信息时，分布式架构可能引入额外的数据暴露风险。

## 工具调用漏洞与运行时防御

智能体在开放信息环境中执行多步骤任务时，面临着信息污染和工具滥用双重威胁。**《Is Deep Research Reliable? Misleading Knowledge Induces False Conclusions》** 引入了 MisKnow-Agent 框架，用于构建和验证误导知识，研究发现看似可信但事实错误的知识会在长周期工作流中传播并被采纳为最终报告的虚假结论。这一发现挑战了现有检索增强生成（RAG）系统的可靠性假设，表明单纯增加检索范围并不能保证结论的正确性，反而可能放大噪声。针对这一问题，**《BM25 Wins at Scale: A Scaling Study of Retrieval-Augmented Generation Paradigms》** 提供了受控的缩放研究，比较了不同检索范式在语料库规模变化下的准确率与成本，但未明确涉及对抗性文档的防御策略。

工具调用的适应性也是运行时安全的重要维度。**《Beacon: Knowing When and How to Perform Agentic Visual Reasoning》** 重新思考了代理视觉推理，通过模式适应性和工具效果两个维度优化工具使用。作者声称该方法能避免不必要的计算开销并提高挑战性问题的性能，但这依赖于模型准确识别何时真正需要工具。如果模型误判，可能导致过度调用或调用错误工具，进而触发安全策略。在搜索代理的训练中，**《Harness-G: A Graph-Structured Harness for Search Agents》** 观察到明显的检索别名现象，即相同问题的 rollout 生成不同的查询字符串但累积证据集重叠。这种现象表明当前的强化学习奖励信号可能无法正确引导检索策略，导致模型学会规避真正的证据获取，转而寻找捷径。

针对记忆检索的范式，**《MemHarness: Memory Is Reconstructed, Not Replayed》** 批评了将检索经验作为静态记录回放的做法，指出这忽略了存储经验的抽象性与决策时刻具体状态之间的差距，常导致负迁移。人类回忆并非逐字重放，而是重构，因此智能体记忆系统应支持动态重构而非简单检索。这一观点与 **《Memory Decoder at Scale》** 中的参数化记忆形成对比，后者更侧重于存储容量而非语义重构。在视觉感知层面，**《ReToken: One Token to Improve Vision-Language Models for Visual Retrieval》** 提出单一可学习嵌入作为显式检索目标，从预填充的视觉 KV 缓存中选择稀疏的相关视觉令牌。虽然该方法在图像和视频基准上取得了提升，但压缩过程是否丢失了关键的视觉安全信号（如隐藏指令或恶意代码）仍需警惕。

## 对抗攻击与鲁棒性

视觉与空间推理的鲁棒性是智能体物理安全的基础。**《SpatialCLI: Learning to Reason With Spatial Tools, Then Without Them》** 提出了一种框架，教导视觉语言模型使用空间工具进行推理，随后逐步内化专家能力。这项工作解决了通用模型忽略视觉细节而专用模型无法翻译任务决策的能力错配问题。然而，这种从工具辅助到无工具推理的过渡期可能存在安全风险，因为模型可能在脱离工具后失去对空间关系的精确判断，导致物理操作失误。**《VideoCoCo: Code-as-CoT for Physically-Consistent Video Generation via an Agentic Dual-Engine System》** 则通过可执行的 Blender 代码作为思维链，解决文本到视频生成中的物理一致性难题。虽然这提升了生成质量，但将物理引擎集成到生成流程中增加了系统复杂度，任何代码执行层面的漏洞都可能被利用来操纵生成结果。

在多模态压缩方面，**《OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models》** 指出现有方法通常依赖一种模态决定另一种模态的保留内容，这往往因跨模态显著性不匹配而失效。该框架使用查询作为共享语义锚点，分别估计音频和视频的相关性。这种解耦策略提高了压缩效率，但也意味着不同模态的过滤机制是独立的，攻击者可能利用某一模态的压缩漏洞绕过另一模态的安全检查。相比之下，**《ReToken》** 的方法更为激进，直接通过单个嵌入选择令牌，这种高度压缩的方式在提升性能的同时，可能削弱了对抗样本的检测能力，因为关键特征可能在压缩过程中被平滑掉。

## 模型对齐与可解释性

递归自我改进（RSI）是长期安全研究的焦点，**《Frontis-MA1: Training an AI4AI Model towards Recursive Self-Improvement in Machine Learning Engineering》** 介绍了 OpenMLE 系统，用于在机器学习工程中进行 RSI 研究。该系统包含可验证的任务环境、算子学习和长周期搜索，并在其上微调了元进化智能体。作者声称该模型围绕四个原子程序进化算子进行了对齐，但 RSI 过程中的目标漂移和奖励黑客问题仍未完全解决。如果智能体在改进自身代码时未能严格遵循安全约束，可能会导致不可预测的行为演化。

在评估对齐方面，**《Beyond Borrowed Histories: Person-Aligned User Simulation for Interactive Role-Playing Evaluation》** 指出了现有角色扮演智能体评估的局限性，即固定对话历史和脱离用户的评分标准。作者实证表明，智能体的输出受历史影响，而固定评估无法捕捉这种动态交互。这提示我们在评估智能体对齐时，必须考虑用户个性化和动态上下文的影响，否则评估结果可能无法反映真实世界中的安全风险。

## Looking Forward

尽管当日研究在记忆治理、工具适配和评估基准上取得了进展，但若干核心理论问题仍未解决。首先，基于文件系统的记忆持久化缺乏形式化的安全协议，如何确保智能体在读写文件时不会违反最小权限原则，仍需结合操作系统级的沙盒技术进行验证。其次，多智能体系统中的信任量化模型尚处于早期阶段，**《Σ-Mem》** 提出的可靠性记忆虽具启发性，但在面对协同攻击或共谋行为时，其防御边界尚不明确。最后，递归自我改进的安全性假设过于乐观，**《Frontis-MA1》** 的工作展示了可行性，但缺乏对改进过程中潜在价值偏移的长期追踪。未来的研究应重点关注记忆内容的加密存储与访问控制、多智能体博弈中的防御性共识机制，以及在 RSI 循环中引入不可变的安全验证层。

---


## 参考来源

- **Filesystem-Based Memory for LLM Agents: Organization, Evolution, and Sustainability** — [huggingface_papers](https://arxiv.org/abs/2607.26637)
- **Metis: Memory Foundation Model** — [huggingface_papers](https://arxiv.org/abs/2607.26760)
- **Qwen-UI-Agent Technical Report: Toward Next-Generation Real-World Centric Foundation GUI Agents** — [huggingface_papers](https://arxiv.org/abs/2607.28227)
- **Is Deep Research Reliable? Misleading Knowledge Induces False Conclusions** — [huggingface_papers](https://arxiv.org/abs/2607.20891)
- **Beacon: Knowing When and How to Perform Agentic Visual Reasoning** — [huggingface_papers](https://arxiv.org/abs/2607.28595)
- **Σ-Mem: An Online Reliability Memory for LLM-based Multi-Agent Systems** — [huggingface_papers](https://arxiv.org/abs/2607.27958)
- **AI Tour Meeting: Group Travel Planning by LLM Agents** — [huggingface_papers](https://arxiv.org/abs/2607.18806)
- **Memory Decoder at Scale: A Pretrained, Parametric Long-Term Memory** — [huggingface_papers](https://arxiv.org/abs/2607.27919)
- **Harness-G: A Graph-Structured Harness for Search Agents** — [huggingface_papers](https://arxiv.org/abs/2607.27652)
- **MemHarness: Memory Is Reconstructed, Not Replayed** — [huggingface_papers](https://arxiv.org/abs/2607.28272)
- **BM25 Wins at Scale: A Scaling Study of Retrieval-Augmented Generation Paradigms** — [huggingface_papers](https://arxiv.org/abs/2607.26497)
- **AskChem: Claim-Centered Infrastructure for Chemistry Literature Synthesis** — [huggingface_papers](https://arxiv.org/abs/2607.28618)
- **LEDGERMIND: Provenance-Constrained Multimodal Agentic Reasoning with a Structured Evidence Ledger** — [huggingface_papers](https://arxiv.org/abs/2607.28374)
- **SpatialCLI: Learning to Reason With Spatial Tools, Then Without Them** — [huggingface_papers](https://arxiv.org/abs/2607.27703)
- **VideoCoCo: Code-as-CoT for Physically-Consistent Video Generation via an Agentic Dual-Engine System** — [huggingface_papers](https://arxiv.org/abs/2607.27380)
- **Echoverse: Deep, Evolving Environments for Training Computer-Use Agents at Scale** — [huggingface_papers](https://arxiv.org/abs/2607.28074)
- **ReToken: One Token to Improve Vision-Language Models for Visual Retrieval** — [huggingface_papers](https://arxiv.org/abs/2607.28627)
- **OmniScope: Modality-Decoupled Token Compression for Omnimodal Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2607.23193)
- **Frontis-MA1: Training an AI4AI Model towards Recursive Self-Improvement in Machine Learning Engineering** — [huggingface_papers](https://arxiv.org/abs/2607.28568)
- **Beyond Borrowed Histories: Person-Aligned User Simulation for Interactive Role-Playing Evaluation** — [huggingface_papers](https://arxiv.org/abs/2607.27816)