# AI 日报 [AI 安全] - 2026-07-17


# AI 安全每日综述：2026 年 7 月 17 日

## Highlights

当日研究进展中，最引人注目的突破集中在具身智能体的安全性与多智能体系统的治理机制上。**BadWAM: When World-Action Models Dream Right but Act Wrong** 揭示了世界动作模型（WAMs）在视觉漂移攻击下的脆弱性，表明即使模型能正确预测未来状态，微小的视觉扰动仍可能导致行动偏差，这对具身安全构成了直接威胁。与此同时，**SearchOS-V1: Towards Robust Open-Domain Information-Seeking Agent Collaboration** 提出了一种系统级框架，将隐式的搜索进度转化为显式共享状态，有效解决了多智能体协作中的重复循环和预算浪费问题，为 Agent 运行时治理提供了新思路。此外，**Rethinking the Evaluation of Harness Evolution for Agents** 对现有的自动化测试用例演化方法提出了根本性质疑，指出当前评估协议存在自我验证偏差，呼吁建立更严格的任务级搜索基线对比标准，这标志着安全评估领域正从单纯追求性能指标转向关注评估过程本身的可靠性。

## Agent 安全与治理

随着大语言模型向自主 Agent 演进，其面临的安全风险已从静态文本生成扩展至动态环境交互与长期规划领域。在具身智能方面，**BadWAM: When World-Action Models Dream Right but Act Wrong** 的研究打破了以往认为世界模型耦合动作与预测即具备内在鲁棒性的假设。作者构建了一个统一的框架来建模和评估世界动作漂移攻击，通过微小的视觉扰动诱导模型产生看似合理但实际错误的行动序列。这一发现表明，仅依靠内部一致性检查不足以保障物理世界的操作安全，必须引入外部监控机制来验证动作与真实环境的匹配度。与之形成互补的是 **RxBrain: Embodied Cognition Foundation Model with Joint Language-Visual Reasoning and Imagination**，该工作试图通过联合语言与视觉想象来增强具身认知，虽然未直接讨论攻击防御，但其强调的抽象计划结构与视觉想象的互补角色，为理解具身决策的可解释性提供了基础，有助于后续设计针对此类模型的异常检测器。

在多智能体协作与运行时治理层面，**SearchOS-V1: Towards Robust Open-Domain Information-Seeking Agent Collaboration** 直面了当前 Web 搜索智能体在长交互历史中容易陷入死循环的痛点。该系统通过将脆弱的隐式搜索进度转化为显式、持久且共享的状态，使得多个 Agent 能够协同追踪任务进展，避免了因单点失败导致的资源耗尽。这种显式状态管理不仅提升了效率，更重要的是降低了因上下文丢失而引发的幻觉风险，属于一种内建的安全治理机制。类似地，**GRASP: GRanularity-Aware Search Policy for Agentic RAG** 则专注于检索增强生成（RAG）场景下的 Agent 安全策略。该研究引入了基于强化学习的框架，训练 Agent 自适应协调互补的检索工具，以控制上下文粒度并防止无关 Token 干扰推理。这两项工作共同指向一个趋势：Agent 的安全性不再仅仅依赖于模型本身的对齐能力，而是越来越依赖于对工具调用流程、检索粒度以及多智能体间状态同步的精细化管控。

在机器人策略的长程执行安全上，**RoboTTT: Context Scaling for Robot Policies** 展示了将视觉运动上下文扩展至 8K 时间步的技术潜力，这使得机器人能够在不增加推理延迟的情况下实现单样本模仿学习和在线策略改进。然而，这种超长上下文的引入也带来了新的安全风险，例如记忆污染或指令注入的可能性。结合 **LongStraw: Long-Context RL Beyond 2M Tokens under a Fixed GPU Budget** 的工作，我们可以看到业界正在努力解决推理上下文长度与强化学习后训练之间的差距。LongStraw 提出的架构感知执行栈允许在固定 GPU 预算下进行百万 Token 级别的 RL 后训练，这对于处理 Agent 累积的观察、工具输出和决策至关重要。尽管这些技术显著提升了 Agent 的能力上限，但也意味着攻击面随之扩大，如何在保持长程依赖能力的同时防止恶意输入在长窗口中被放大，是未来 Agent 运行时防御的核心挑战。

## 工具调用、提示注入与运行时防御

Agent 的工具调用能力和提示词工程一直是安全研究的焦点，当这些能力被集成到复杂的 RAG 或自动化工作流中时，风险变得更加隐蔽。**Chat2Scenic: An Iterative RAG-Based Framework for Scenario Generation in Autonomous Driving** 虽然主要应用于自动驾驶测试场景生成，但其核心逻辑涉及利用 RAG 从法规描述中自动生成可执行脚本。这项工作揭示了在将自然语言指令转化为代码或配置时的潜在风险，如果检索到的法规片段被篡改或包含误导性信息，生成的测试脚本可能无法覆盖真实的安全边界。这与 **GRASP** 中提到的防止无关 Token 干扰推理的目标一致，强调了在工具调用链中引入内容过滤和语义校验的重要性。

在训练与蒸馏过程中的运行时安全方面，**SEED: Self-Evolving On-Policy Distillation for Agentic Reinforcement Learning** 提出了一种将完成的轨迹转化为训练时后见之明技能的方法，旨在填补结果奖励与令牌级策略学习之间的监督缺口。然而，**Demystifying On-Policy Distillation: Roles, Pathologies, and Regulations** 的研究对此类蒸馏过程进行了系统性剖析，指出了其中存在的病理现象。作者确认了提示多样性比每问题采样数量更重要，且蒸馏的有效性完全取决于引导信号的质量。这意味着如果用于蒸馏的数据集包含潜在的对抗样本或错误推理路径，学生模型可能会继承并放大这些缺陷。因此，在实施如 SEED 这样的自进化框架时，必须建立严格的数据清洗和信号质量验证机制，以防止训练过程中的安全退化。

此外，**Smarter and Cheaper at Once: Byte-Exact KV-Cache Grafting Turns a Frozen Small Model into a Verified-Knowledge Flywheel** 探讨了通过字节精确的键值缓存嫁接来增强小模型能力的方法。虽然其主要贡献在于效率，但这种将外部知识作为 KV 状态恢复的技术，实际上改变了模型的内存访问模式。如果 KV 缓存的来源不可信，或者在恢复过程中发生位翻转，可能会导致模型行为偏离预期。这种运行时内存管理的灵活性为未来的提示注入攻击提供了新的向量，即攻击者可能通过操纵 KV 缓存而非直接修改输入文本来影响模型输出，这要求运行时沙盒和内存审计工具必须具备更高的细粒度监控能力。

## 对抗攻击与鲁棒性

视觉与视频生成领域的对抗攻击研究正在从单纯的图像分类扩展到复杂的时序推理和物理模拟中。**Hierarchical Denoising For Multi-Step Visual Reasoning** 提出了一种分层去噪框架，旨在解决视频模型在逻辑一致性和低延迟流式推理方面的不足。尽管该工作主要关注生成质量，但其对多步推理逻辑一致性的强调，间接回应了对抗攻击中常见的时序不一致问题。如果模型无法保证多帧之间的逻辑连贯性，攻击者便可以利用这种断裂来植入误导性的视觉信息。**UniVR: Thinking in Visual Space for Unified Visual Reasoning** 进一步探索了从纯视觉演示中学习复杂推理和物理动态的能力，其采用的 VR-GRPO 范式强制在整个推理过程中保持逻辑连贯和物理一致性。这表明，提升模型在视觉空间中的推理鲁棒性，本身就是一种防御手段，能够减少因物理常识缺失而被特定视觉对抗样本欺骗的风险。

在更广泛的模型架构层面，**Spectral Rewiring for Exploration, Purification, and Model Merging** 揭示了强化学习更新主要集中在基础模型的谱空间中。作者提出的子空间对齐重连（SAR）方法，旨在保留推理有效的谱核心，同时避免全参数更新带来的推理性能抑制和合并干扰。这一发现对于对抗鲁棒性具有重要意义，因为许多对抗攻击正是利用了模型参数空间的微小扰动。通过限制更新仅在特定的谱子空间内进行，理论上可以增强模型对非结构化扰动的抵抗力。然而，这也引发了关于模型可解释性的新问题，即如何确保这些谱空间的编辑不会无意中削弱模型对特定类型攻击的防御能力。

## 模型对齐与可解释性

模型对齐技术的进步直接关系到 Agent 在开放环境中的行为可控性。**MeanFlowNFT: Bringing Forward-Process RL to Average-Velocity Generators** 将前向过程的强化学习应用于平均速度生成器，优化了扩散和流模型的偏好对齐。这种方法不需要反向过程轨迹或似然估计，提高了训练效率，但在对齐目标的设计上仍需警惕。如果奖励函数未能准确捕捉人类意图，高效的训练反而可能加速模型偏离安全边界。**DeepLoop: Depth Scaling for Looped Transformers** 则从架构角度探讨了通过循环应用紧凑块来扩展序列计算深度的可能性。这种 tied-depth 效应的形式化分析表明，共享更新的聚合梯度可能会改变残差缩放问题，进而影响模型的长期稳定性。在安全语境下，这意味着我们需要重新评估循环 Transformer 在处理长程依赖时的可预测性，防止因深度堆叠导致的梯度爆炸或逻辑崩溃。

**Video = World + Event Stream** 提出的 Wan-Streamer v0.3 将视频重构为世界加事件流的单一组织视图，这是一种新的预训练任务范式。虽然主要面向生成质量，但这种将稳定环境与动态事件解耦的表示学习，为未来的安全监控提供了理论基础。如果模型能够明确区分“世界”（持久上下文）和“事件”（变化），那么安全系统可以更精准地识别哪些变化属于正常的事件流，哪些属于异常的入侵或攻击信号。这种结构化的表示学习有助于提升模型的可解释性，使安全审计人员能够更清晰地追踪导致特定输出的因果链条。

## 安全评估基准与事件响应

评估体系的可靠性是衡量 AI 安全水平的基石，当前的基准测试往往存在过度拟合或评估偏差的问题。**Rethinking the Evaluation of Harness Evolution for Agents** 尖锐地指出了现有自动测试用例演化方法的根本缺陷。由于演化过程本身是迭代搜索，如果在同一公共基准上报告最终性能，会导致评估结果虚高。作者建议应与简单的任务级搜索基线在匹配的反馈和推理预算下进行对比，以确定增益是否真实。这一观点对于所有 Agent 安全评估都适用，提醒研究者不能盲目相信自动化测试工具的评分，必须建立独立的外部验证机制。

在视频生成领域，**KeyFrame-Compass: Towards Comprehensive Evaluation of Keyframe-Conditioned Video Generation** 和 **MultiRef-Compass: Towards Comprehensive Evaluation of Multi-Reference-to-Audio-Video Generation** 分别填补了关键帧条件生成和多参考音视频生成的评估空白。这两个基准涵盖了精心策划的样本，旨在评估模型在保持参考忠实度的同时维持整体质量的能力。对于安全而言，这些基准不仅关乎生成质量，还关乎内容合规性。例如，在多参考设置中，模型必须正确绑定和组合多个参考源，如果这一过程缺乏约束，攻击者可能利用多模态输入的复杂性绕过内容过滤器。因此，这些基准的建立不仅是性能评测的需要，更是构建多模态安全护栏的前提。

**Chat2Scenic** 虽然侧重于自动驾驶场景生成，但其评估框架同样具有通用参考价值。它解决了从法规描述自动生成可执行脚本的编译率问题，这实际上是评估 Agent 将抽象规则转化为具体行动能力的关键指标。在安全事件中，这种转化能力决定了 Agent 能否正确执行紧急避险指令。因此，未来的安全评估应更多关注 Agent 在规则遵循和指令转化上的准确率，而不仅仅是任务完成度。

## Looking Forward

尽管上述工作在 Agent 安全、运行时防御及评估基准方面取得了显著进展，但仍存在若干未解决的理论问题亟待验证。首先，具身智能体在物理世界中的安全边界尚未明确，**BadWAM** 揭示的攻击向量表明，仅靠内部世界模型的一致性检查不足以抵御外部视觉扰动，未来需要建立跨模态的物理一致性验证协议。其次，长上下文训练与推理之间的差距依然存在，**LongStraw** 和 **RoboTTT** 虽然提升了上下文容量，但如何在百万 Token 级别的环境中防止提示注入和记忆污染，尚缺乏成熟的理论模型。最后，评估基准的独立性仍是悬而未决的挑战，**Rethinking the Evaluation of Harness Evolution** 指出的自我验证偏差问题，暗示我们需要开发完全独立的第三方评估平台，以替代目前普遍使用的自动化测试演化流程。只有在这些基础问题上取得突破，AI Agent 才能真正具备在开放环境中安全运行的可信能力。

---


## 参考来源

- **GRASP: GRanularity-Aware Search Policy for Agentic RAG** — [huggingface_papers](https://arxiv.org/abs/2607.10463)
- **SearchOS-V1: Towards Robust Open-Domain Information-Seeking Agent Collaboration** — [huggingface_papers](https://arxiv.org/abs/2607.15257)
- **RxBrain: Embodied Cognition Foundation Model with Joint Language-Visual Reasoning and Imagination** — [huggingface_papers](https://arxiv.org/abs/2607.14187)
- **SEED: Self-Evolving On-Policy Distillation for Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2607.14777)
- **Chat2Scenic: An Iterative RAG-Based Framework for Scenario Generation in Autonomous Driving** — [huggingface_papers](https://arxiv.org/abs/2607.14387)
- **Rethinking the Evaluation of Harness Evolution for Agents** — [huggingface_papers](https://arxiv.org/abs/2607.12227)
- **LongStraw: Long-Context RL Beyond 2M Tokens under a Fixed GPU Budget** — [huggingface_papers](https://arxiv.org/abs/2607.14952)
- **MeanFlowNFT: Bringing Forward-Process RL to Average-Velocity Generators** — [huggingface_papers](https://arxiv.org/abs/2607.15273)
- **Hierarchical Denoising For Multi-Step Visual Reasoning** — [huggingface_papers](https://arxiv.org/abs/2607.15278)
- **Spectral Rewiring for Exploration, Purification, and Model Merging** — [huggingface_papers](https://arxiv.org/abs/2607.03065)
- **BadWAM: When World-Action Models Dream Right but Act Wrong** — [huggingface_papers](https://arxiv.org/abs/2607.15207)
- **Video = World + Event Stream** — [huggingface_papers](https://arxiv.org/abs/2607.15038)
- **Smarter and Cheaper at Once: Byte-Exact KV-Cache Grafting Turns a Frozen Small Model into a Verified-Knowledge Flywheel** — [huggingface_papers](https://arxiv.org/abs/2607.14431)
- **UniVR: Thinking in Visual Space for Unified Visual Reasoning** — [huggingface_papers](https://arxiv.org/abs/2607.12800)
- **KeyFrame-Compass: Towards Comprehensive Evaluation of Keyframe-Conditioned Video Generation** — [huggingface_papers](https://arxiv.org/abs/2607.14202)
- **Demystifying On-Policy Distillation: Roles, Pathologies, and Regulations** — [huggingface_papers](https://arxiv.org/abs/2607.13399)
- **SUFLECA: Scaling Up Feature Learning for CAD-to-image Alignment** — [huggingface_papers](https://arxiv.org/abs/2607.15058)
- **RoboTTT: Context Scaling for Robot Policies** — [huggingface_papers](https://arxiv.org/abs/2607.15275)
- **MultiRef-Compass: Towards Comprehensive Evaluation of Multi-Reference-to-Audio-Video Generation** — [huggingface_papers](https://arxiv.org/abs/2607.14189)
- **DeepLoop: Depth Scaling for Looped Transformers** — [huggingface_papers](https://arxiv.org/abs/2607.13491)