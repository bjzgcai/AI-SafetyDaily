# AI 日报 [AI 安全] - 2026-07-09


# 每日 AI 安全研究综述：2026-07-09

## Highlights

当日研究进展中，最核心的突破集中在 Agent 架构的自动化设计及其带来的治理挑战、基于全轨迹的行为评估方法以及世界模型在长程推理中的物理一致性缺陷。**《Automating the Design of Embodied Agent Architectures》** 揭示了通过算法自动搜索 Agent 架构可能引入未知的攻击面，为运行时安全监控提出了新难题；**《AgentLens: Production-Assessed Trajectory Reviews for Coding Agent Evaluation》** 则标志着安全评估从单一任务结果向复杂交互轨迹的转变，强调了对 Agent 决策过程的持续审计；**《Imagined Rollouts are Kinematic, Not Dynamic: A Diagnosis of Long-Horizon World-Model Failure》** 从理论层面诊断了世界模型在模拟未来时的物理偏差，指出这种“运动学而非动力学”的幻觉是导致 Agent 在长程任务中发生灾难性失效的根本原因之一。

## Agent 安全与治理

随着自主 Agent 系统逐渐从文本交互走向具身智能，其内部架构的复杂性正在指数级上升，这直接影响了安全治理的有效性。传统上，Agent 的安全依赖于人工设计的模块边界，但 **《Automating the Design of Embodied Agent Architectures》** 提出的 Agent 架构搜索（AAS）技术，虽然提升了性能，却将原本透明的设计空间转化为黑盒。作者指出，当感知、记忆、规划与行动模块的连接关系由算法自动决定时，研究人员难以预判信息存储的具体位置及模型调用的潜在路径，这种架构的不透明性使得传统的静态代码审计失效。这意味着未来的 Agent 治理不能仅依赖规则匹配，而需要建立针对动态架构的运行时监控机制，以应对因架构变异导致的意外行为。

在治理手段方面，现有的评估范式正经历从“任务通过率”到“行为可解释性”的深刻转型。**《AgentLens: Production-Assessed Trajectory Reviews for Trajectory Reviews for Coding Agent Evaluation》** 提供了一个关键视角，即生产环境中的人类用户更关注 Agent 如何遵循指令、使用工具以及从错误中恢复的过程，而非仅仅关注最终代码是否运行成功。该工作结合形式化验证与大模型生成的轨迹审查，试图量化 Agent 在交互过程中的合规性。这与当前许多仅关注最终结果的基准测试形成对比，强调了在安全评估中纳入“过程安全”的重要性。然而，这种方法也面临挑战，即如何确保大模型生成的审查本身不被恶意利用，或者是否存在对特定行为模式的偏见。

此外，Agent 的内部状态管理直接关系到记忆污染和上下文注入的风险。**《Dual Latent Memory in Vision-Language-Action Models for Robotic Manipulation》** 探讨了视觉 - 语言 - 动作模型中的双重潜在记忆机制。主流模型通常假设马尔可夫性质，忽略历史经验对当前决策的影响，但这限制了长程任务的执行能力。该研究提出的 LaMem-VLA 框架将记忆嵌入到原生潜在空间中，使历史经验能与多模态推理无缝交织。从安全角度看，这种紧密耦合的记忆机制虽然提升了效率，但也增加了外部输入干扰内部状态的难度。如果攻击者能够操纵记忆检索过程，可能导致 Agent 在物理操作中产生严重的逻辑偏差。因此，内存访问控制与潜在空间的完整性校验将成为具身 Agent 安全治理的核心议题。

## 运行时稳定性与物理安全

Agent 在开放环境中的运行时稳定性是防止物理伤害的关键，这要求底层模型不仅具备推理能力，还需符合物理世界的动力学规律。**《Imagined Rollouts are Kinematic, Not Dynamic: A Diagnosis of Long-Horizon World-Model Failure》** 深入剖析了世界模型在长程预测中的失败模式。作者发现，现有模型倾向于生成运动学上一致但动力学上不合理的未来画面，例如物体移动看似平滑却忽略了力的作用。这种“运动学而非动力学”的偏差在短视图中不易察觉，但在长程规划中会导致累积误差，进而引发碰撞或失控。这一诊断结果为运行时防御提供了新的指标，即通过检测想象轨迹是否符合物理约束来提前终止高风险操作。

强化学习在 Agent 训练中的不稳定性同样构成安全隐患。**《Single-Rollout Asynchronous Optimization for Agentic Reinforcement Learning》** 讨论了异步优化在长视界任务中的应用。虽然异步更新提高了吞吐量，但现有的系统在训练稳定性和任务有效性之间缺乏平衡，特别是在 GRPO 框架下的组采样策略可能导致梯度估计偏差。如果训练过程不稳定，Agent 可能在部署后表现出不可预测的策略漂移。因此，在 Agent 上线前，必须对异步训练过程中的收敛性和策略方差进行严格验证，防止因优化目标函数设计不当而产生的对抗性行为。

对于具身智能而言，物理反馈的准确性是最后一道防线。**《OmniTacTune: Policy-Agnostic Real-World RL for Tactile Residual Adaptation of Visual Policies》** 提出了一种策略无关的真实世界强化学习管道，用于通过触觉残差修正预训练的视觉策略。视觉策略往往在接触丰富的操作中失效，而触觉信号能提供关键的力与几何信息。该工作通过两阶段设计引导触觉数据适应视觉先验，显著提升了物理操作的鲁棒性。这表明，单纯依赖视觉或语言模型的 Agent 存在物理安全盲区，引入多模态触觉反馈并建立相应的自适应机制，是降低物理交互风险的有效途径。

## 评估基准与仿真环境

构建可信的 Agent 安全评估体系离不开高保真的仿真环境与标准化的基准测试。**《RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies》** 填补了通用机器人操作策略评估的空白。现有基准往往局限于简单任务或单一环境，无法全面反映 Agent 在真实物理部署中的能力。RoboDojo 统一了仿真与现实世界的评估标准，旨在解决仿真与真实部署之间的差距问题。这对于安全至关重要，因为许多在仿真中表现良好的策略在现实中可能因摩擦系数、光照变化等因素而失效。该基准的建立有助于识别那些仅在理想条件下有效的“过拟合”策略，从而筛选出更具泛化能力的安全模型。

大规模的空间智能测试也是评估 Agent 安全性的必要环节。**《WildCity: A Real-World City-Scale Testbed for Rendering, Simulation, and Spatial Intelligence》** 引入了一个城市级的真实世界多模态数据集，包含自动驾驶车队在复杂城市环境中采集的轨迹。人类可以构建跨越数十平方公里的空间心智地图，而 AI 在此规模下的表现仍是未解之谜。该数据集为评估 Agent 在长距离导航中的空间理解能力提供了基础，同时也暴露了数据收集过程中的隐私与安全风险。尽管主要侧重于空间智能，但其提供的城市级场景数据可用于测试 Agent 在复杂交通流中的避障与决策安全性，是验证具身 Agent 社会适应性的重要资源。

此外，**《Infinite Worlds with Versatile Interactions》** 展示了 LingBot-World 2.0 在无限交互地平线上的进展。通过因果预训练范式，该系统实现了无界交互并保持输出质量的一致性。这种能够驱动视频流的高保真仿真环境，为红队测试提供了理想的沙箱。然而，作者提到该系统通过蒸馏实时变体来保证响应速度，这引发了关于模型压缩过程中安全特性是否丢失的担忧。在利用此类仿真环境进行安全测试时，必须验证蒸馏后的模型是否保留了原始模型的安全对齐特征，防止因效率优化而牺牲了安全边界。

## Looking Forward

尽管上述工作在 Agent 架构、评估与物理安全方面取得了显著进展，但仍存在若干未解决的理论问题。首先，自动化架构搜索（如 **《Automating the Design of Embodied Agent Architectures》** 所述）带来的可解释性缺失，使得我们难以在事故发生前追溯责任归属，亟需发展针对动态图结构的可解释性分析工具。其次，世界模型的物理一致性诊断（如 **《Imagined Rollouts are Kinematic, Not Dynamic》** 所指出的）目前仍停留在诊断层面，尚未形成自动化的运行时干预机制，如何将动力学约束实时嵌入推理过程是一个待攻克的难点。最后，多模态对齐中的权衡问题（如 **《Splash》** 所示）表明，增加触觉等新模态可能会挤占原有语言推理的能力，如何在扩展感知维度的同时保持核心对齐目标的稳定性，仍需进一步的理论探索。未来的研究应重点关注这些跨领域的交叉风险，建立更加稳健的 Agent 安全防御体系。

---


## 参考来源

- **Automating the Design of Embodied Agent Architectures** — [huggingface_papers](https://arxiv.org/abs/2606.30111)
- **AgentLens: Production-Assessed Trajectory Reviews for Coding Agent Evaluation** — [huggingface_papers](https://arxiv.org/abs/2607.06624)
- **Single-Rollout Asynchronous Optimization for Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2607.07508)
- **Dual Latent Memory in Vision-Language-Action Models for Robotic Manipulation** — [huggingface_papers](https://arxiv.org/abs/2607.07608)
- **Sparse Delta Memory: Scaling the State of Linear RNNs through Sparsity** — [huggingface_papers](https://arxiv.org/abs/2607.07386)
- **Infinite Worlds with Versatile Interactions** — [huggingface_papers](https://arxiv.org/abs/2607.07534)
- **RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies** — [huggingface_papers](https://arxiv.org/abs/2607.04434)
- **RoboTALES: Learning Reasoning-Guided Robot Policies via Task-Aligned Simulated Futures** — [huggingface_papers](https://arxiv.org/abs/2607.06018)
- **Accurate, Interdisciplinary and Transparent Structure-property Understanding with Deep Native Structural Reasoning** — [huggingface_papers](https://arxiv.org/abs/2607.07708)
- **WildCity: A Real-World City-Scale Testbed for Rendering, Simulation, and Spatial Intelligence** — [huggingface_papers](https://arxiv.org/abs/2607.06838)
- **TESSERA v2: Scaling Pixel-wise Earth Foundation Models** — [huggingface_papers](https://arxiv.org/abs/2607.03949)
- **OmniTacTune: Policy-Agnostic Real-World RL for Tactile Residual Adaptation of Visual Policies** — [huggingface_papers](https://arxiv.org/abs/2607.03723)
- **OPSD-V: On-Policy Self-Distillation for Post-Training Few-Step Autoregressive Video Generators** — [huggingface_papers](https://arxiv.org/abs/2607.08766)
- **Wake up for Touch! Mask-isolated Tactile Alignment Learning in MLLMs** — [huggingface_papers](https://arxiv.org/abs/2607.00302)
- **Scaling Mixture-of-Experts Video Pretraining for Embodied Intelligence** — [huggingface_papers](https://arxiv.org/abs/2607.07675)
- **Imagined Rollouts are Kinematic, Not Dynamic: A Diagnosis of Long-Horizon World-Model Failure** — [huggingface_papers](https://arxiv.org/abs/2607.05966)
- **Token-Based Dual-view Fusion and Adaptation of Large Vision Models for Breast Cancer Classification** — [huggingface_papers](https://arxiv.org/abs/2607.06309)
- **Teaching LLMs a Low-Resource Language: Enhancing Code Completion in Pharo** — [huggingface_papers](https://arxiv.org/abs/2607.04939)