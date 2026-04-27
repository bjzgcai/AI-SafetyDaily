# AI 日报 [AI 安全] - 2026-04-27


# AI 安全与治理每日综述 | 2026-04-27

## Highlights

今日学术与产业动态中，最核心的进展集中在**可解释性评估范式的重构**、**生成式模型知识产权的防御机制**以及**人机关系的治理理论演进**。

在学术层面，**《Rethinking XAI Evaluation: A Human-Centered Audit of Shapley Benchmarks in High-Stakes Settings》** 揭示了当前 Shapley 值评估在高风险场景下的局限性，指出量化指标与人类效用之间的脱节，呼吁建立统一的人类中心审计框架。与此同时，**《ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders》** 提出了一种针对自监督学习编码器的抗对抗水印方案，解决了黑盒环境下 IP 验证与鲁棒性难以兼得的难题。在治理理论方面，**《A Co-Evolutionary Theory of Human-AI Coexistence: Mutualism, Governance, and Dynamics in Complex Societies》** 挑战了传统的“主从服从”伦理框架，提出了基于“条件互惠共生”的治理新范式。

产业端需警惕的是，社区中流传关于部分大模型出现“降智”现象的讨论（如 **《Claude 终于认了！降智坐实，越聊越傻，3 个 bug 全曝光》** 等来源），目前尚缺乏独立复现的权威数据，需区分营销话术与真实模型退化风险。此外，医疗视频理解大模型的开源（如 **《全球首个医疗视频理解大模型开源！6k+ 组精标测试集与英雄榜同步上线》**）为安全评估提供了新的探针，但需关注其数据标注的合规性。

## 可解释性与评估范式的重构

当前可解释性 AI（XAI）领域正经历从“数学一致性”向“人类效用”的范式转移。传统上，Shapley 值被视为解释模型决策的基石，但 **《Rethinking XAI Evaluation: A Human-Centered Audit of Shapley Benchmarks in High-Stakes Settings》** 指出，现有的评估体系过度依赖量化代理指标，缺乏对实际部署中人类效用对齐的验证。该研究通过统一的摊销框架，在低延迟操作风险工作流中隔离了八种 Shapley 变体的语义差异，并基于四个风险数据集进行了大规模实证评估。这一工作表明，理论上的数学完备性并不等同于操作层面的可解释性，特别是在高风险决策中，评估标准必须从“计算准确性”转向“决策辅助效用”。

这一趋势与特征归因在对比学习中的研究相呼应。**《On the Properties of Feature Attribution for Supervised Contrastive Learning》** 探讨了监督对比学习（SCL）下的特征归因性质。不同于传统的交叉熵损失，SCL 通过构建嵌入空间来拉近相似数据、推远相异数据，这导致其归因属性与传统分类模型存在本质差异。该研究揭示了在 SCL 架构下，特征归因可能面临新的挑战，提示我们在评估对比学习模型时，不能直接套用基于分类层的解释性指标。

在对话系统领域，**《Tell Me Why: Designing an Explainable LLM-based Dialogue System for Student Problem Behavior Diagnosis》** 进一步将可解释性落地到具体应用场景。该研究针对学生行为诊断中教师对策略信任度低的问题，提出了一种基于分层归因方法的 LLM 对话系统。系统不仅生成建议，还通过 xAI 技术识别对话证据，为每个推荐生成可追溯的理由。这与 **《Learning Evidence Highlighting for Frozen LLMs》** 中提出的 HiLight 框架形成了互补。HiLight 通过训练轻量级强调演员（Emphasis Actor）在原始上下文中插入高亮标签，而非压缩或重写输入，从而帮助冻结的求解器（Solver）在长噪声上下文中定位决定性证据。两者的共同点在于，都试图解决 LLM“黑盒”推理中的信任问题，但前者侧重于对话交互中的证据呈现，后者侧重于长上下文推理中的信息提取效率。

## 隐私计算与数据治理

在联邦学习与隐私保护领域，数据贡献评估与隐私泄露风险是两个核心矛盾。**《Data-Free Contribution Estimation in Federated Learning using Gradient von Neumann Entropy》** 提出了一种无需服务器端验证数据或客户端自报信息的贡献估计方法。该方法利用最终层更新矩阵的冯·诺依曼（谱）熵来衡量信息多样性，并实例化了 SpectralFed 和 SpectralFuse 两种方案。这一创新使得在不牺牲隐私的前提下，能够公平地识别客户端重要性并提供奖励，解决了传统方法依赖敏感数据或易受操纵的缺陷。

医疗数据的高敏感性使得隐私计算尤为重要。**《FeatEHR-LLM: Leveraging Large Language Models for Feature Engineering in Electronic Health Records》** 针对电子健康记录（EHR）中不规则采样和结构稀疏的问题，利用 LLM 生成临床有意义的表格特征。该框架的关键在于 LLM 仅在本地运行，限制了患者隐私暴露，从而在利用 LLM 强大特征工程能力的同时，满足了医疗数据的隐私合规要求。这与 **《CognitiveTwin: Robust Multi-Modal Digital Twins for Predicting Cognitive Decline in Alzheimer's Disease》** 中的数字孪生框架有异曲同工之妙。CognitiveTwin 整合了多模态纵向数据（如 MRI、PET、基因等）来预测认知轨迹，强调模型在人口统计学上的公平性和对缺失数据的鲁棒性。这两项工作共同指向一个方向：在利用大模型处理敏感数据时，必须通过架构设计（如本地化、联邦化）来内嵌隐私保护机制，而非事后修补。

## 对抗安全与鲁棒性

随着模型在复杂环境中的部署，对抗攻击与知识产权（IP）保护成为安全研究的双重点。**《ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders》** 针对自监督学习编码器作为宝贵 IP 的现状，提出了一种同时满足黑盒可验证性和对抗鲁棒性的水印框架。现有水印方案往往难以在模型被盗用后于下游任务中验证所有权，且容易因对抗样本被移除。ArmSSL 通过确保水印样本形成可区分的 OOD 簇，解决了这一痛点，为模型资产保护提供了新的技术路径。

在图神经网络领域，**《Distance-Misaligned Training in Graph Transformers and Adaptive Graph-Aware Control》** 揭示了图 Transformer 的全局信息混合能力可能带来的失效模式。研究定义了“距离失配训练”，即标签相关信息的分布与模型在图距离上分配的通信不匹配。通过合成节点分类基准，该研究指出在某些任务中，长程通信并非总是优于局部交互，模型需要根据任务特性自适应调整通信范围。这一发现对构建鲁棒的图学习系统具有指导意义，提示我们在设计图模型时，不能盲目追求全局感受野，而需考虑任务对局部与全局信息的依赖结构。

## 智能体、基准与治理

智能体（Agent）的安全与治理是今日综述的重中之重，涉及从底层能力到社会影响的多个层面。**《Agentic World Modeling: Foundations, Capabilities, Laws, and Beyond》** 提出了一个“层级 x 定律”的分类法，将世界模型能力分为 L1 预测器、L2 模拟器等层级。该研究强调，随着 AI 从生成文本转向通过持续交互实现目标，环境动态建模能力成为核心瓶颈。这一理论框架为评估 Agent 的长期规划能力和安全性提供了基础。

在 Agent 的具体训练与交互中，**《SOLAR-RL: Semi-Online Long-horizon Assignment Reinforcement Learning》** 解决了 GUI 智能体在动态任务中的训练困境。通过结合离线 RL 的全局轨迹语义和在线 RL 的长期动态捕捉，SOLAR-RL 在降低交互成本的同时提升了任务完成质量。这为 Agent 在复杂软件环境中的安全部署提供了技术支撑。

治理层面，**《How Supply Chain Dependencies Complicate Bias Measurement and Accountability Attribution in AI Hiring Applications》** 深入探讨了 AI 招聘系统中的责任碎片化问题。研究指出，现代 AI 系统运行在复杂供应链中，责任分散在数据供应商、模型开发者和部署组织之间，这使得传统的单一技术或监管视角难以有效评估偏差。该论文呼吁建立能够追踪供应链依赖的评估框架，以应对 EU AI Act 等法规下的问责挑战。

此外，**《A Co-Evolutionary Theory of Human-AI Coexistence: Mutualism, Governance, and Dynamics in Complex Societies》** 从伦理哲学高度提出了“条件互惠共生”框架，反对阿西莫夫式的“主从服从”伦理。该理论认为，未来人机关系应是在制度约束下的共同进化，强调关系的互惠性、可逆性和心理安全性。这一观点为应对日益复杂的 AI 系统提供了宏观治理思路。

在基准测试方面，**《CNSL-bench: Benchmarking the Sign Language Understanding Capabilities of MLLMs on Chinese National Sign Language》** 填补了中文国家手语理解评估的空白，强调权威 grounding 和标准化。而 **《FETS Benchmark: Foundation Models Outperform Dataset-specific Machine Learning in Energy Time Series Forecasting》** 则验证了基础模型在能源时间序列预测中的泛化能力，挑战了传统数据集特定任务的学习范式。这些基准的发布为特定领域的安全评估提供了量化依据。

## Looking Forward

尽管今日研究在多个维度取得了进展，但仍有若干理论问题待解。首先，**XAI 评估的“人类效用”量化标准尚未统一**，**《Rethinking XAI Evaluation》** 虽指出了方向，但如何建立可大规模部署的效用审计协议仍需探索。其次，**Agent 的世界模型能力与安全性之间的权衡**尚不明确，**《Agentic World Modeling》** 提出的层级分类需要进一步验证其在对抗环境下的鲁棒性。最后，**供应链责任归属的法律与技术接口**仍是空白，**《How Supply Chain Dependencies Complicate Bias Measurement》** 揭示了问题的复杂性，但缺乏跨组织的审计工具链。

对于产业界，需警惕模型稳定性与性能之间的潜在冲突。如社区中关于模型“降智”的传闻，虽未经独立验证，但反映了模型监控与版本管理的紧迫性。未来研究应更关注**模型退化检测机制**与**开源模型的安全探针**建设，确保在技术快速迭代中，安全评估能同步跟进。

---


## 参考来源

- **Rethinking XAI Evaluation: A Human-Centered Audit of Shapley Benchmarks in High-Stakes Settings** — [arxiv_ai](https://arxiv.org/abs/2604.22662v1)
- **Data-Free Contribution Estimation in Federated Learning using Gradient von Neumann Entropy** — [arxiv_ai](https://arxiv.org/abs/2604.22562v1)
- **ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** — [arxiv_ai](https://arxiv.org/abs/2604.22550v1)
- **How Supply Chain Dependencies Complicate Bias Measurement and Accountability Attribution in AI Hiring Applications** — [arxiv_ai](https://arxiv.org/abs/2604.22679v1)
- **On the Properties of Feature Attribution for Supervised Contrastive Learning** — [arxiv_ai](https://arxiv.org/abs/2604.22540v1)
- **CognitiveTwin: Robust Multi-Modal Digital Twins for Predicting Cognitive Decline in Alzheimer's Disease** — [arxiv_ai](https://arxiv.org/abs/2604.22428v1)
- **Tell Me Why: Designing an Explainable LLM-based Dialogue System for Student Problem Behavior Diagnosis** — [arxiv_ai](https://arxiv.org/abs/2604.22237v1)
- **A Co-Evolutionary Theory of Human-AI Coexistence: Mutualism, Governance, and Dynamics in Complex Societies** — [arxiv_ai](https://arxiv.org/abs/2604.22227v1)
- **Agentic World Modeling: Foundations, Capabilities, Laws, and Beyond** — [arxiv_ai](https://arxiv.org/abs/2604.22748v1)
- **Learning Evidence Highlighting for Frozen LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.22565v1)
- **SOLAR-RL: Semi-Online Long-horizon Assignment Reinforcement Learning** — [arxiv_ai](https://arxiv.org/abs/2604.22558v1)
- **Controllable Spoken Dialogue Generation: An LLM-Driven Grading System for K-12 Non-Native English Learners** — [arxiv_ai](https://arxiv.org/abs/2604.22542v1)
- **FeatEHR-LLM: Leveraging Large Language Models for Feature Engineering in Electronic Health Records** — [arxiv_ai](https://arxiv.org/abs/2604.22534v1)
- **CGC: Compositional Grounded Contrast for Fine-Grained Multi-Image Understanding** — [arxiv_ai](https://arxiv.org/abs/2604.22498v1)
- **Distance-Misaligned Training in Graph Transformers and Adaptive Graph-Aware Control** — [arxiv_ai](https://arxiv.org/abs/2604.22413v1)
- **CNSL-bench: Benchmarking the Sign Language Understanding Capabilities of MLLMs on Chinese National Sign Language** — [arxiv_ai](https://arxiv.org/abs/2604.22367v1)
- **ChangeQuery: Advancing Remote Sensing Change Analysis for Natural and Human-Induced Disasters from Visual Detection to Semantic Understanding** — [arxiv_ai](https://arxiv.org/abs/2604.22333v1)
- **FETS Benchmark: Foundation Models Outperform Dataset-specific Machine Learning in Energy Time Series Forecasting** — [arxiv_ai](https://arxiv.org/abs/2604.22328v1)
- **Aligning Dense Retrievers with LLM Utility via DistillationAligning Dense Retrievers with LLM Utility via Distillation** — [arxiv_ai](https://arxiv.org/abs/2604.22722v1)
- **CRAFT: Clustered Regression for Adaptive Filtering of Training data** — [arxiv_ai](https://arxiv.org/abs/2604.22693v1)
- **Our principles** — [openai](https://openai.com/index/our-principles)
- **Momenta曹旭东：规模L4要百亿美元投入，现金流业务是物理AI门票** — [qbitai](https://www.qbitai.com/2026/04/407485.html)
- **Claude终于认了！降智坐实，越聊越傻，3个bug全曝光** — [qbitai](https://www.qbitai.com/2026/04/407502.html)
- **全球首个医疗视频理解大模型开源！6k+组精标测试集与英雄榜同步上线，开发者速来！** — [qbitai](https://www.qbitai.com/2026/04/407486.html)
- **DeepSeek阮翀加盟元戎首秀，详解基座VLA，研发提效10倍** — [qbitai](https://www.qbitai.com/2026/04/407465.html)
- **一季度全国新发放普惠型小微企业贷款平均利率3.64%** — [36kr](https://36kr.com/newsflashes/3784430340971528?f=rss)
- **“中数睿智”完成亿元B轮融资** — [36kr](https://36kr.com/newsflashes/3784415697476867?f=rss)
- **国家统计局：1-3月份全国规模以上工业企业利润增长15.5%** — [36kr](https://36kr.com/newsflashes/3784401141177609?f=rss)
- **前苹果工程师做了款体感游戏机，销量拳打Xbox，营收数亿美元** — [36kr](https://36kr.com/p/3783828639571203?f=rss)
- **早期项目 | 前地平线产品负责人死磕“拿放”动作，轮式机器人今年锁定百台出货** — [36kr](https://36kr.com/p/3783824870317312?f=rss)
- **星动纪元完成超2亿美元新一轮融资** — [36kr](https://36kr.com/newsflashes/3784376398961920?f=rss)
- **「破壳机器人」许华哲：两年内，中国将出现可用的家庭机器人** — [36kr](https://36kr.com/p/3784365164322055?f=rss)
- **汽车零部件企业“人形机器人”布局持续加码** — [36kr](https://36kr.com/newsflashes/3784366844157185?f=rss)
- **中信证券：上市银行一季度收入和盈利增速延续上行趋势，预计全年趋势延续** — [36kr](https://36kr.com/newsflashes/3784364842360073?f=rss)
- **中信证券：支付清算层和基础模型层具备较强投资确定性** — [36kr](https://36kr.com/newsflashes/3784363152874761?f=rss)
- **业绩排名压力与长期价值投资难权衡，部分基金经理调仓策略面临“言行背离”困境** — [36kr](https://36kr.com/newsflashes/3784360559614982?f=rss)
- **8点1氪丨豆包提前查到2026山东事业编成绩？最新回应；东方甄选主播集体离职，俞敏洪回应；花呗白条月付等面临重大调整** — [36kr](https://36kr.com/p/3784311487945735?f=rss)
- **欧莱雅BRANDSTORM 2026中国总决赛落幕，AI成美妆创新核心议题｜最前线** — [36kr](https://36kr.com/p/3783249100397570?f=rss)
- **小鹏汽车在广州成立新科技公司** — [36kr](https://36kr.com/newsflashes/3784442962156804?f=rss)
- **两市融资余额减少112.38亿元** — [36kr](https://36kr.com/newsflashes/3784357662530824?f=rss)