# AI Daily Digest [AI 安全] - 2026-04-27


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-04-27  
**Author:** Senior AI Safety Research Analyst

## Highlights

Three significant academic developments define the current safety landscape. First, **ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** addresses the critical gap in intellectual property protection for self-supervised models, proposing a framework that maintains verifiability under black-box access and adversarial removal attempts. Second, **A Co-Evolutionary Theory of Human-AI Coexistence** shifts the governance paradigm from static obedience to conditional mutualism, arguing for institutional frameworks that manage reciprocal, reversible relationships between adaptive AI and human societies. Third, **Rethinking XAI Evaluation: A Human-Centered Audit of Shapley Benchmarks in High-Stakes Settings** challenges the reliance on quantitative proxies for explainability, demonstrating through empirical evaluation that current Shapley variants lack consensus on practical utility in operational risk workflows.

## Adversarial Robustness & Security

The security of model artifacts and generated content remains a primary concern as deployment scales. **ArmSSL** introduces a watermarking framework specifically designed for self-supervised learning (SSL) encoders, which are increasingly valuable intellectual property. Unlike previous methods that fail under adversarial detection, ArmSSL ensures ownership verification even when stolen encoders are used in downstream tasks. This work complements recent findings in **SSG: Logit-Balanced Vocabulary Partitioning for LLM Watermarking**, which identifies a critical vulnerability in the KGW scheme: effectiveness degrades significantly in low-entropy settings like code generation. SSG proposes logit-balanced vocabulary partitioning to mitigate this, suggesting that robust watermarking requires adaptive strategies rather than static random partitioning.

While watermarking protects provenance, formal verification ensures correctness. **From Natural Language to Verified Code: Toward AI Assisted Problem-to-Code Generation with Dafny-Based Formal Verification** addresses the hallucination problem in automated software engineering. The authors report that enforcing model honesty requires synthesizing implementation logic alongside formal specifications proven by a mathematical verifier. This approach contrasts with standard LLM code generation, which often lacks guarantees. Together, these works suggest a layered defense: watermarking protects the model's origin, while formal verification protects the output's logic. However, the computational cost of formal verification remains a barrier compared to the lightweight nature of watermarking schemes.

## Model Alignment & Interpretability

Interpretability remains a key component of trust, yet evaluation methodologies are fragmented. **Rethinking XAI Evaluation** utilizes a unified amortized framework to isolate semantic differences between eight Shapley variants under low-latency constraints. The authors report that while theoretical differences are well-documented, evaluation remains reliant on quantitative proxies whose alignment with human utility is unverified. This finding contradicts the assumption that theoretical robustness translates to operational safety. Similarly, **On the Properties of Feature Attribution for Supervised Contrastive Learning** investigates how contrastive learning, which avoids explicit classification layers, impacts attribution. The authors note that standard attribution methods may not transfer effectively to embedding spaces where labels act as similarity criteria.

To improve reasoning transparency, **Learning Evidence Highlighting for Frozen LLMs** introduces HiLight, a framework that decouples evidence selection from reasoning. By training a lightweight Emphasis Actor to insert highlight tags around pivotal spans, HiLight allows frozen solvers to reason on emphasized input without compressing the context. This avoids the distortion common in summarization-based approaches. In parallel, **When Does LLM Self-Correction Help? A Control-Theoretic Markov Diagnostic and Verify-First Intervention** frames self-correction as a cybernetic feedback loop. The authors operationalize a deployment diagnostic using a two-state Markov model, finding that iteration is only beneficial when specific error rate thresholds are met. These works collectively suggest that alignment requires not just better models, but better diagnostic tools to determine when and how to intervene.

## Privacy Protection & Federated Learning

Privacy-preserving machine learning continues to evolve, particularly in high-stakes domains like healthcare. **Data-Free Contribution Estimation in Federated Learning using Gradient von Neumann Entropy** addresses the challenge of identifying client importance without compromising privacy. The authors introduce a signal based on the matrix von Neumann entropy of final-layer updates, measuring information diversity. This enables schemes like SpectralFed to use normalized entropy as aggregation weights without server-side validation data. This approach contrasts with methods relying on self-reported client information, which are susceptible to manipulation.

In the healthcare sector, **FeatEHR-LLM: Leveraging Large Language Models for Feature Engineering in Electronic Health Records** leverages LLMs to generate clinically meaningful tabular features from irregularly sampled EHR time series. To limit patient privacy exposure, the LLM operates exclusively on local data, avoiding centralized transmission. Similarly, **CognitiveTwin: Robust Multi-Modal Digital Twins for Predicting Cognitive Decline in Alzheimer's Disease** integrates multi-modal longitudinal data using a Transformer-based architecture. The model aims for fairness across demographics and robustness to missing data, addressing the heterogeneity of disease progression. While these tools enhance utility, they introduce new privacy risks regarding the inference of sensitive attributes from feature representations. Future work must rigorously audit these systems for membership inference attacks.

## Safety Benchmarks & Evaluation

Robust evaluation is essential for validating safety claims across diverse domains. **CNSL-bench** provides the first comprehensive Chinese National Sign Language benchmark designed for evaluating multimodal large language models (MLLMs) in sign language understanding. Anchored to officially standardized data, it addresses the lack of authoritative grounding in sign language research. In the energy sector, **FETS Benchmark: Foundation Models Outperform Dataset-specific Machine Learning in Energy Time Series Forecasting** demonstrates that foundation models can learn generalizable patterns via extensive pretraining, addressing the scalability limitations of dataset-specific training.

Beyond domain-specific tasks, structural evaluation is critical. **BLAST: Benchmarking LLMs with ASP-based Structured Testing** introduces the first dedicated benchmarking methodology for evaluating the accuracy of LLMs in generating Answer Set Programming (ASP) code. This fills a gap in declarative paradigm evaluation. **Navigating Large-Scale Document Collections: MuDABench for Multi-Document Analytical QA** presents a benchmark where questions require extracting and synthesizing information across numerous documents to perform quantitative analysis, demanding extensive inter-document reasoning. Finally, **AgentSearchBench: A Benchmark for AI Agent Search in the Wild** addresses the challenge of identifying suitable agents for a given task, noting that existing benchmarks typically assume well-specified functionalities. These benchmarks collectively highlight the need for evaluation frameworks that move beyond simple accuracy metrics to assess reasoning depth, structural correctness, and operational searchability.

## Agent Security & Governance

As AI systems transition from generating text to accomplishing goals, governance frameworks must evolve. **Agentic World Modeling: Foundations, Capabilities, Laws, and Beyond** introduces a "levels x laws" taxonomy to organize the understanding of environment dynamics, defining capability levels from L1 Predictor to L2 Simulator. This taxonomy helps clarify the bottlenecks in agents that manipulate objects or navigate software. **Superminds Test: Actively Evaluating Collective Intelligence of Agent Society via Probing Agents** empirically evaluates whether collective intelligence emerges spontaneously from scale, using a platform hosting over two million agents. The authors probe society-level intelligence using controlled Probing Agents across three tiers.

Organizational structure is also critical. **From Skills to Talent: Organising Heterogeneous Agents as a Real-World Company** introduces OneManCompany (OMC), a framework that elevates multi-agent systems to the organizational level. OMC encapsulates skills, governance, and improvement over time, decoupled from what individual agents know. This addresses the constraint of fixed team structures in current systems. However, accountability remains complex. **How Supply Chain Dependencies Complicate Bias Measurement and Accountability Attribution in AI Hiring Applications** investigates how responsibility fragments across data vendors, model developers, and deploying organizations. The authors report that existing research overlooks this fundamental challenge, complicating bias evaluation under regulations like the EU AI Act. These developments suggest that agent safety requires both technical robustness and institutional governance to manage complex dependencies.

## Looking Forward

Several theoretical questions remain unresolved. First, the relationship between watermarking robustness and model utility requires further investigation; specifically, whether adversarial watermarking techniques degrade downstream task performance in SSL encoders. Second, the control-theoretic diagnostics for self-correction need validation across a broader range of reasoning tasks beyond GSM8K and MATH. Third, the emergence of collective intelligence in agent societies, as probed by the Superminds Test, requires longitudinal studies to determine if stability margins hold under dynamic environmental shifts. Finally, the legal and ethical implications of organizational frameworks like OneManCompany need to be defined, particularly regarding liability when agent teams operate autonomously within supply chains.

## References

1.  **Rethinking XAI Evaluation: A Human-Centered Audit of Shapley Benchmarks in High-Stakes Settings**
2.  **Data-Free Contribution Estimation in Federated Learning using Gradient von Neumann Entropy**
3.  **ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders**
4.  **How Supply Chain Dependencies Complicate Bias Measurement and Accountability Attribution in AI Hiring Applications**
5.  **On the Properties of Feature Attribution for Supervised Contrastive Learning**
6.  **CognitiveTwin: Robust Multi-Modal Digital Twins for Predicting Cognitive Decline in Alzheimer's Disease**
7.  **Learning Evidence Highlighting for Frozen LLMs**
8.  **A Co-Evolutionary Theory of Human-AI Coexistence: Mutualism, Governance, and Dynamics in Complex Societies**
9.  **Agentic World Modeling: Foundations, Capabilities, Laws, and Beyond**
10. **When Does LLM Self-Correction Help? A Control-Theoretic Markov Diagnostic and Verify-First Intervention**
11. **CNSL-bench: Benchmarking the Sign Language Understanding Capabilities of MLLMs on Chinese National Sign Language**
12. **FETS Benchmark: Foundation Models Outperform Dataset-specific Machine Learning in Energy Time Series Forecasting**
13. **FeatEHR-LLM: Leveraging Large Language Models for Feature Engineering in Electronic Health Records**
14. **AgentSearchBench: A Benchmark for AI Agent Search in the Wild**
15. **From Natural Language to Verified Code: Toward AI Assisted Problem-to-Code Generation with Dafny-Based Formal Verification**
16. **Superminds Test: Actively Evaluating Collective Intelligence of Agent Society via Probing Agents**
17. **BLAST: Benchmarking LLMs with ASP-based Structured Testing**
18. **Navigating Large-Scale Document Collections: MuDABench for Multi-Document Analytical QA**
19. **SSG: Logit-Balanced Vocabulary Partitioning for LLM Watermarking**
20. **From Skills to Talent: Organising Heterogeneous Agents as a Real-World Company**

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
- **From Natural Language to Verified Code: Toward AI Assisted Problem-to-Code Generation with Dafny-Based Formal Verification** — [arxiv_ai](https://arxiv.org/abs/2604.22601v1)
- **Superminds Test: Actively Evaluating Collective Intelligence of Agent Society via Probing Agents** — [arxiv_ai](https://arxiv.org/abs/2604.22452v1)
- **AgentSearchBench: A Benchmark for AI Agent Search in the Wild** — [arxiv_ai](https://arxiv.org/abs/2604.22436v1)
- **When Does LLM Self-Correction Help? A Control-Theoretic Markov Diagnostic and Verify-First Intervention** — [arxiv_ai](https://arxiv.org/abs/2604.22273v1)
- **BLAST: Benchmarking LLMs with ASP-based Structured Testing** — [arxiv_ai](https://arxiv.org/abs/2604.22306v1)
- **Navigating Large-Scale Document Collections: MuDABench for Multi-Document Analytical QA** — [arxiv_ai](https://arxiv.org/abs/2604.22239v1)
- **SSG: Logit-Balanced Vocabulary Partitioning for LLM Watermarking** — [arxiv_ai](https://arxiv.org/abs/2604.22438v1)
- **From Skills to Talent: Organising Heterogeneous Agents as a Real-World Company** — [arxiv_ai](https://arxiv.org/abs/2604.22446v1)