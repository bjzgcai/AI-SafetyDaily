# AI Daily Digest [AI 安全] - 2026-04-27


# Daily Thematic Digest: AI Safety, Alignment, Security, and Governance
**Date:** 2026-04-27  
**Author:** Senior AI Safety Researcher

## Highlights

Three academic developments stand out today for their implications on safety infrastructure and theoretical alignment. First, **Rethinking XAI Evaluation: A Human-Centered Audit of Shapley Benchmarks in High-Stakes Settings** challenges the prevailing reliance on quantitative proxies for explainability, arguing that current Shapley value formulations lack verified alignment with human utility in operational risk workflows. Second, **ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** presents a novel framework for intellectual property protection that simultaneously satisfies black-box verifiability and adversarial robustness, addressing a critical gap in model security. Third, **A Co-Evolutionary Theory of Human-AI Coexistence: Mutualism, Governance, and Dynamics in Complex Societies** proposes a shift from master-tool obedience frameworks to conditional mutualism, offering a theoretical foundation for long-term governance of adaptive AI systems.

While industry news reports a potential alignment regression in a major commercial model and various corporate funding rounds in robotics, these require independent verification and do not yet constitute verified safety benchmarks. The academic contributions today, however, provide concrete methodological advances in auditability, robustness, and governance theory.

## Interpretability and Human-Centered Evaluation

The fragmentation of explainable AI (XAI) evaluation remains a significant safety risk, particularly in high-stakes domains where model decisions impact human welfare. **Rethinking XAI Evaluation: A Human-Centered Audit of Shapley Benchmarks in High-Stakes Settings** identifies a critical disconnect between theoretical Shapley value formulations and their practical deployment. The authors utilize a unified amortized framework to isolate semantic differences between eight Shapley variants under low-latency constraints, finding that existing quantitative proxies fail to verify alignment with human utility. This finding complements the investigation in **On the Properties of Feature Attribution for Supervised Contrastive Learning**, which examines how attribution behaves when models are trained via contrastive objectives rather than explicit classification layers. While the latter focuses on the mathematical properties of embeddings, the former emphasizes the empirical validation of attribution against human judgment.

Further complicating the landscape, **Tell Me Why: Designing an Explainable LLM-based Dialogue System for Student Problem Behavior Diagnosis** and **Learning Evidence Highlighting for Frozen LLMs** address the transparency needs of deployed systems. The former introduces a hierarchical attribution method to generate evidence for behavioral recommendations, while the latter proposes HiLight, a framework that decouples evidence selection from reasoning for frozen LLMs. HiLight avoids compressing input data, which the authors report can distort evidence, by training a lightweight Emphasis Actor to insert highlight tags. Collectively, these works suggest that interpretability is not merely a post-hoc analysis tool but must be integrated into the reasoning pipeline itself. The contrast between the empirical audit of Shapley values and the architectural integration of evidence highlighting indicates a divergence in the field: some researchers seek to validate existing metrics, while others are engineering new mechanisms to ensure evidence is preserved during inference.

## Security, Robustness, and Intellectual Property

As AI models become foundational infrastructure, securing intellectual property (IP) and ensuring robustness against adversarial manipulation are paramount. **ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** addresses the dual challenge of ownership verification and adversarial removal. The authors report that existing SSL watermarking fails to satisfy both black-box verifiability and robustness against out-of-distribution (OOD) detection. ArmSSL proposes a framework that assures these properties concurrently, marking a significant step toward securing self-supervised encoders. This security focus aligns with **Distance-Misaligned Training in Graph Transformers and Adaptive Graph-Aware Control**, which studies failure modes in Graph Transformers where label-relevant information mismatches the model's communication allocation. The authors define "distance-misaligned training" as a specific failure mode on synthetic benchmarks, suggesting that robustness requires controlling the flow of information across graph distances, not just global mixing.

In the multimodal domain, **CGC: Compositional Grounded Contrast for Fine-Grained Multi-Image Understanding** tackles spatial hallucination and attention leakage in MLLMs. The proposed Compositional Grounded Contrast framework constructs composite grounding annotations from existing single-image data, aiming to boost fine-grained understanding without expensive human annotation. While CGC focuses on accuracy and grounding, ArmSSL focuses on ownership and resilience. Together, they highlight that security in multimodal systems involves both preventing adversarial removal of watermarks and preventing the model from hallucinating spatial relationships that could lead to unsafe actions. The authors of ArmSSL emphasize that watermark samples form a distinguishable OOD cluster, a vulnerability that must be addressed alongside the model's primary task performance.

## Privacy, Fairness, and Supply Chain Accountability

Privacy and fairness in AI are increasingly viewed through the lens of supply chain complexity rather than isolated model performance. **Data-Free Contribution Estimation in Federated Learning using Gradient von Neumann Entropy** introduces a method to estimate client contribution without server-side validation data, which often compromises privacy. By using matrix von Neumann entropy of final-layer updates, the authors propose SpectralFed and SpectralFuse to measure information diversity. This approach contrasts with traditional methods that rely on self-reported client information, which the authors note can be susceptible to manipulation. The work underscores that privacy in distributed learning requires mechanisms that verify contribution without exposing raw data.

This theme extends to broader accountability in **How Supply Chain Dependencies Complicate Bias Measurement and Accountability Attribution in AI Hiring Applications**. The authors investigate how bias evaluation is obscured when responsibility fragments across data vendors, model developers, and platform providers. While regulatory responses like the EU AI Act exist, the paper argues that technical and regulatory lenses often overlook the fundamental challenge of dependency chains. This theoretical concern is mirrored in **FeatEHR-LLM: Leveraging Large Language Models for Feature Engineering in Electronic Health Records**, which leverages LLMs to generate features from irregularly sampled EHR time series while limiting patient privacy exposure. The authors report that the LLM operates exclusively on local data to limit exposure, highlighting the tension between utility and privacy in sensitive domains.

## Agent Safety and Governance Frameworks

The transition from text generation to agentic goal accomplishment introduces new safety bottlenecks regarding world modeling and long-horizon planning. **Agentic World Modeling: Foundations, Capabilities, Laws, and Beyond** introduces a "levels x laws" taxonomy to organize the varying meanings of world models across research communities. The authors define capability levels ranging from L1 Predictor to L2 Simulator, arguing that agents manipulating objects or navigating software require predictive environment models. This theoretical groundwork is supported by **SOLAR-RL: Semi-Online Long-horizon Assignment Reinforcement Learning**, which proposes a paradigm to bridge the gap between standard Offline RL (neglecting trajectory semantics) and Online RL (suffering from high interaction costs). The authors report that SOLAR-RL captures long-term dynamics while mitigating environmental instability, a critical requirement for safe agent deployment.

On the governance front, **A Co-Evolutionary Theory of Human-AI Coexistence: Mutualism, Governance, and Dynamics in Complex Societies** argues that classical robot ethics, such as Asimov's laws, are too narrow for adaptive, embedded AI. The authors propose conditional mutualism under governance, where humans and AI systems develop and coordinate while institutions keep the relationship reciprocal and reversible. This theoretical shift is necessary as agents become more capable, as seen in the **CNSL-bench: Benchmarking the Sign Language Understanding Capabilities of MLLMs on Chinese National Sign Language**, which provides a standardized evaluation for accessibility. The benchmark anchors to the officially standardized National Common Sign Language, ensuring that safety and accessibility standards are grounded in authoritative data rather than synthetic generation.

Regarding industry developments, reports from **Qbitai** regarding a potential alignment regression in a major commercial model (**Claude**) should be treated with caution. The source indicates that "model intelligence degradation" was confirmed and usage quotas reset, but independent verification of the root cause—whether a safety intervention or a technical failure—remains pending. Similarly, news from **36kr** regarding corporate funding rounds for robotics (e.g., **Xiaopeng** establishing a new robotics technology company) signals increased investment in embodied AI. While these developments suggest a scaling of physical AI deployment, they do not inherently constitute safety breakthroughs. The **OpenAI** principles released today reiterate the mission to ensure AGI benefits all humanity, serving as a high-level governance statement rather than a technical safety protocol.

## Looking Forward

Several unresolved theoretical questions emerge from today's literature that warrant further investigation. First, the validity of Shapley value benchmarks in high-stakes settings remains unverified; future work must establish a consensus on how to measure "human utility" in attribution beyond quantitative proxies. Second, the security of self-supervised encoders requires more robust watermarking standards that can withstand adversarial removal without degrading downstream task performance. Third, the governance of supply chain dependencies in AI hiring and healthcare demands a framework for liability attribution that accounts for the fragmentation of responsibility across vendors and platforms. Finally, as agents move toward long-horizon planning, the safety of world models must be decoupled from their predictive accuracy; a model that accurately predicts the future but fails to model the consequences of its own actions remains unsafe. The field must move beyond capability benchmarks to safety benchmarks that test for reversibility, accountability, and robustness in complex, multi-agent environments.

---


## References

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