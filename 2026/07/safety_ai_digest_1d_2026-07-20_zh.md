# AI 日报 [AI 安全] - 2026-07-20


# 2026-07-20 AI Safety Thematic Digest

## Highlights

今日研究进展显著聚焦于 Agent 系统的运行时治理与深层安全评估，其中三项工作尤为关键。**Beyond Success Rate: Cost-Aware Evaluation of Offensive and Defensive Security Agents** 提出了在固定推理预算下衡量安全 Agent 效能的新范式，挑战了单纯以成功率为导向的评估标准。**Recursive Harness Self-Improvement** 揭示了训练 Harness 作为数据生成组件对模型进化的潜在影响，为 Agent 自我改进机制的安全性提供了新的理论视角。**Behavioral Privacy Leakage in Agentic Negotiation** 则形式化了多轮交互中的行为隐私泄露风险，指出传统加密手段无法防御基于动态谈判轨迹的推断攻击。这些工作共同指向一个核心议题：随着 Agent 自主性的增强，其内部状态、执行成本及交互模式本身已成为需要被严格监控和防护的安全边界。

## Agent 安全与治理

当前 Agent 安全研究正从静态的代码审计转向动态的运行时治理，重点在于如何量化 Agent 在复杂环境中的实际风险与收益。**Beyond Success Rate: Cost-Aware Evaluation of Offensive and Defensive Security Agents** 指出，现有的安全 Agent 评估往往过分强调在宽松预算下的峰值能力，如漏洞发现或渗透测试完成率，却忽视了运营环境中每一步推理、工具调用和遥测查询的实际成本消耗。作者通过 Cybench 和 Splunk BOTS v1 等挑战任务，对比了模型在固定成本约束下的表现，表明仅报告最佳情况的成功率会掩盖资源耗尽导致的系统脆弱性。这一观点与 **Recursive Harness Self-Improvement** 中关于 Harness 演化的讨论形成了互补：如果 Harness 不仅是推理时的脚手架，更是生成未来训练数据的组件，那么评估 Harness 的质量就等同于评估未来模型的安全性。作者提出，优化用户构建的 Harness 不仅能提升即时性能，还能改善用于后续训练的轨迹质量，但这同时也引入了 Harness 本身被恶意利用或产生偏差的风险。

在隐私与安全交叉领域，**Behavioral Privacy Leakage in Agentic Negotiation** 将注意力从显式数据泄露转移到了更为隐蔽的行为层面。尽管密码学技术能保护谈判中明确披露的约束值，但对手仍可通过观察让步轨迹、时间间隔和收敛模式来推断私有信息。该研究设计了自适应随机谈判策略，旨在保证 $(\varepsilon, \delta)$-差分隐私的同时维持谈判效用。这与 **Cura 1T: Specialized Model for Agentic Healthcare** 中提到的医疗 Agent 场景形成对照：后者虽然采用了人类门控的递归自我改进（RSI）循环来确保临床推理的准确性，但其核心挑战在于单一任务的窄更新可能破坏其他通用能力。这表明，无论是金融谈判还是医疗诊断，Agent 的“黑盒”决策过程都可能成为隐私泄露或功能退化的源头。值得注意的是，**Cura 1T** 的作者声称通过 RSI 循环提升了特定任务表现，但在缺乏独立第三方验证的情况下，这种自我迭代机制是否会导致模型漂移或安全性下降，仍需进一步观察。相比之下，**Behavioral Privacy Leakage** 提出的形式化防御方案更具可验证性，它强调了在协议设计阶段引入随机性的重要性，而非仅仅依赖事后检测。

此外，**From Human-Centric to Agentic Code Review: The Impact of Different Generations of Generative AI Technology on Review Quality** 探讨了软件供应链安全的新维度。随着 LLM 和 AI Agent 审查员介入代码集成流程，传统的代码审查效率和质量面临重构。该研究分析了超过 100 万个 Pull Requests，试图量化 AI 辅助审查对整体软件质量的影响。虽然这主要是一个软件工程问题，但从安全角度看，如果 AI 审查员未能识别复杂的逻辑漏洞或后门，将直接导致恶意代码流入生产环境。这与 **Recursive Harness Self-Improvement** 中提到的 Harness 质量影响训练数据质量的逻辑一致：如果审查工具（Harness）本身存在缺陷，生成的反馈数据将污染整个开发流程。因此，Agent 治理不仅涉及模型本身的对齐，还涉及支撑其运行的基础设施（如审查工具、评估 Harness）的可靠性。

## 工具调用、提示注入与运行时防御

在 Agent 的具体执行层面，防止工具滥用和运行时错误是保障安全的关键。**DSWorld: A Data Science World Model for Efficient Autonomous Agents** 提出了一种预测环境状态转换的世界模型，允许 Agent 在执行昂贵的数据分析操作前预判结果。这种方法本质上是一种运行时沙盒的变体，通过模拟而非真实执行来降低试错成本。作者结合结构化框架，展示了如何在无需实际运行代码的情况下评估操作可行性。这与 **RAGU: A Multi-Step GraphRAG Engine with a Compact Domain-Adapted LLM** 中针对检索增强生成（RAG）的架构优化相呼应。RAGU 通过分离提取与整合阶段，利用 DBSCAN 去重和 Leiden 社区检测来减少知识图谱中的噪声实体。虽然 RAGU 主要关注检索精度，但在安全语境下，结构化的知识图谱能有效缓解提示注入攻击，因为经过清洗和类型化的实体比原始文本更难以被恶意构造的上下文误导。

然而，即使有了更好的检索和执行预测，Agent 的记忆管理仍是薄弱环节。**RecGPT-V3 Technical Report** 指出，大规模推荐系统中的多 Agent 推理面临无状态行为建模的挑战，即每次请求重新处理完整用户历史，这不仅浪费计算资源，也容易导致上下文信息的丢失或混淆。这种状态管理的缺失可能导致 Agent 在长周期任务中遗忘关键的安全约束或用户偏好。相比之下，**xHC: Expanded Hyper-Connections** 探索了 Transformer 残差流的扩展作为记忆缩放轴，虽然实验显示 N=4 之后收益递减，但这种架构创新为构建具有更长上下文窗口且更稳定的 Agent 提供了硬件层面的可能性。如果 Agent 能够更稳定地维护长期记忆，就能更好地追踪跨会话的攻击痕迹，从而增强对抗提示注入的能力。

在代码审查这一具体工具场景中，**From Human-Centric to Agentic Code Review** 的研究暗示了 AI 审查员可能存在的幻觉风险。如果 AI 审查员过于自信地接受看似合理的代码变更而忽略深层逻辑漏洞，这将构成一种新型的工具调用漏洞。因此，未来的运行时防御不仅需要沙盒隔离，还需要对 AI 审查员的输出进行二次验证，类似于 **DSWorld** 中提出的预测机制，即在代码合并前进行模拟执行分析。

## 模型对齐与强化学习优化

底层强化学习算法的选择直接影响 Agent 的对齐程度和鲁棒性。**When Does Muon Help Agentic Reinforcement Learning?** 研究了 Muon 优化器在稀疏奖励 Agent 强化学习中的表现，发现将其应用于隐藏权重矩阵并结合 Group-in-Group Policy Optimization (GiGPO) 时，最终验证成功率有显著提升。这一发现与 **On-Policy Delta Distillation** 中提出的蒸馏方法形成对比，后者主张使用教师模型与基础模型之间的差异信号（Delta Signal）而非直接模仿输出来提供监督。两者都试图解决传统强化学习中奖励信号稀疏或误导的问题，但路径不同：前者侧重于优化器的数学性质，后者侧重于损失函数的设计。

**Agon: Competitive Cross-Model RL with Implicit Rival Grading of Reasoning** 引入了另一种思路，即让两个竞争模型互为评分者。这种方法解决了传统 RLVR（Reinforcement Learning from Verifiable Rewards）仅对最终答案打分而无法评估推理过程优劣的问题。作者声称，通过迫使模型在解决难题时必须优于看到其工作过程的对手，可以训练出更深层次的推理能力。这与 **Beyond Entropy: Correctness-Aware Advantage Shaping via Contrastive Policy Optimization** 的观点不谋而合，后者指出熵正则化无法区分有用不确定性和有害混淆，因此提出了基于 token 级对比不一致性的正确性感知优势塑造。这两项工作共同表明，简单的奖励最大化已不足以应对复杂的 Agent 对齐问题，必须引入更细粒度的过程监督和对比机制。

值得注意的是，**S1-Omni: A Unified Multimodal Reasoning Model for Scientific Understanding, Prediction, and Generation** 虽然主要关注科学领域的统一建模，但其架构设计强调了异构数据和专家知识的联合建模。这种统一性对于安全至关重要，因为它减少了因模型碎片化而导致的安全盲区。然而，**Xiaomi-Robotics-1: Scaling Vision-Language-Action Models with over 100K Hours of Real-World Trajectories** 提醒我们，现实世界轨迹的规模并不直接等同于安全性。尽管该模型在移动操作任务上表现出强大的泛化能力，但真实物理环境中的意外碰撞或失控风险依然存在。因此，对齐研究不能仅停留在数字空间的推理能力上，必须考虑物理世界的鲁棒性，正如 **Benchmarking Sensor Robustness in Plasma Diagnostic Models** 所强调的，在传感器失效或信号丢失等极端物理条件下，模型的诊断能力必须保持稳健。

## 安全评估基准与事件响应

建立可靠的评估基准是验证上述安全假设的前提。**Benchmarking Sensor Robustness in Plasma Diagnostic Models** 提供了一个重要的方法论参考，即针对特定领域（如核聚变诊断）的物理故障场景进行系统性评估。该研究在 TokaMark 数据集上评估了多种模型在传感器死亡、信号中断等六种物理故障场景下的表现，并引入了鲁棒性指标。这启示我们在评估通用 Agent 安全时，也应引入类似的“故障注入”测试，而不仅仅是标准的基准测试。例如，在 **Beyond Success Rate** 中提到的安全 Agent 评估，除了成本约束外，还应包含在工具 API 返回错误或网络延迟时的降级处理能力。

目前的安全评估体系仍存在明显的滞后性。大多数基准测试侧重于模型在理想条件下的表现，而忽略了 **RecGPT-V3** 中提到的状态丢失问题或 **Behavioral Privacy Leakage** 中的动态推断攻击。未来的评估框架应当是一个动态的、持续的过程，涵盖从训练阶段的 Harness 质量到推理阶段的成本控制和隐私保护。特别是对于 **Cura 1T** 这类采用递归自我改进的模型，评估不应止步于单次迭代的结果，而应监测多轮迭代后的性能漂移和安全属性衰减。

## Looking Forward

尽管近期工作在 Agent 评估、隐私保护和强化学习优化方面取得了进展，但仍存在若干未解决的理论问题。首先，**Recursive Harness Self-Improvement** 中提出的 Harness 优化机制，其长期安全性尚未得到充分验证；如果 Harness 为了短期性能而牺牲了某些安全约束，可能会导致灾难性的模型退化。其次，**Behavioral Privacy Leakage** 虽然提出了形式化防御，但在高维、非结构化交互中的隐私泄露边界仍需进一步量化，特别是在面对具备高级推理能力的对手时。最后，关于 **DSWorld** 和 **Agon** 提出的预测与对抗机制，如何在保证推理深度的同时避免过度计算开销，仍是工程落地的瓶颈。未来的研究需要将这些分散的安全模块——从底层的优化器选择到上层的运行时监控——整合到一个统一的 Agent 安全架构中，以实现真正的端到端可控。

---


## 参考来源

- **From Human-Centric to Agentic Code Review: The Impact of Different Generations of Generative AI Technology on Review Quality** — [huggingface_papers](https://arxiv.org/abs/2607.13196)
- **RAGU: A Multi-Step GraphRAG Engine with a Compact Domain-Adapted LLM** — [huggingface_papers](https://arxiv.org/abs/2607.11683)
- **RESOURCE2SKILL: Distilling Executable Agent Skills from Human-Created Multimodal Resources** — [huggingface_papers](https://arxiv.org/abs/2606.29538)
- **Cura 1T: Specialized Model for Agentic Healthcare** — [huggingface_papers](https://arxiv.org/abs/2607.15314)
- **Beyond Success Rate: Cost-Aware Evaluation of Offensive and Defensive Security Agents** — [huggingface_papers](https://arxiv.org/abs/2607.15263)
- **DSWorld: A Data Science World Model for Efficient Autonomous Agents** — [huggingface_papers](https://arxiv.org/abs/2607.15901)
- **When Does Muon Help Agentic Reinforcement Learning?** — [huggingface_papers](https://arxiv.org/abs/2607.16169)
- **Recursive Harness Self-Improvement** — [huggingface_papers](https://arxiv.org/abs/2607.15524)
- **Behavioral Privacy Leakage in Agentic Negotiation: Formalizing and Mitigating Inference Attacks via Randomized Policies** — [huggingface_papers](https://arxiv.org/abs/2607.06815)
- **xHC: Expanded Hyper-Connections** — [huggingface_papers](https://arxiv.org/abs/2607.14530)
- **RecGPT-V3 Technical Report** — [huggingface_papers](https://arxiv.org/abs/2607.15591)
- **Agon: Competitive Cross-Model RL with Implicit Rival Grading of Reasoning** — [huggingface_papers](https://arxiv.org/abs/2607.07690)
- **S1-Omni: A Unified Multimodal Reasoning Model for Scientific Understanding, Prediction, and Generation** — [huggingface_papers](https://arxiv.org/abs/2607.15686)
- **Xiaomi-Robotics-1: Scaling Vision-Language-Action Models with over 100K Hours of Real-World Trajectories** — [huggingface_papers](https://arxiv.org/abs/2607.15330)
- **VideoRAE: Taming Video Foundation Models for Generative Modeling via Representation Autoencoders** — [huggingface_papers](https://arxiv.org/abs/2607.14088)
- **REBASE: Reference-Background Subspace Elimination for Training-Free In-Context Segmentation** — [huggingface_papers](https://arxiv.org/abs/2607.09082)
- **On-Policy Delta Distillation** — [huggingface_papers](https://arxiv.org/abs/2607.15161)
- **Benchmarking Sensor Robustness in Plasma Diagnostic Models: A Systematic Evaluation on TokaMark** — [huggingface_papers](https://arxiv.org/abs/2607.11915)
- **Audio-Visual Flamingo: Open Audio-Visual Intelligence for Long and Complex Videos** — [huggingface_papers](https://arxiv.org/abs/2607.16107)
- **Beyond Entropy: Correctness-Aware Advantage Shaping via Contrastive Policy Optimization** — [huggingface_papers](https://arxiv.org/abs/2607.14614)