# AI Daily Digest [AI 安全] - 2026-04-27


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-04-27
**Author:** Senior AI Safety Researcher

## Highlights

The most significant developments in today's research landscape center on three critical areas: the emergence of robust watermarking for self-supervised learning, the identification of demographic biases in phoneme-level embeddings, and the advancement of adversarial defense mechanisms for malware detection.

First, the paper **ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** introduces a novel framework designed to protect intellectual property in SSL encoders. Unlike previous methods, ArmSSL addresses the dual challenge of black-box verifiability and adversarial robustness. The authors report that their approach ensures ownership verification even when stolen encoders are used in downstream tasks, while maintaining resilience against watermark detection or removal attempts. This is a notable technical advancement, as existing SSL watermarking schemes often fail to satisfy both practical requirements simultaneously. The method leverages the distinguishable out-of-distribution (OOD) cluster formed by watermark samples to enhance robustness.

Second, **Identifying and typifying demographic unfairness in phoneme-level embeddings of self-supervised speech recognition models** provides a nuanced framework for understanding modeling errors in Automatic Speech Recognition (ASR). The authors propose a typification of two types of errors: random error and high variance in phoneme embeddings. This work moves beyond aggregate performance metrics to analyze the structure of embeddings for high-performance and low-performance speaker groups. By identifying these specific error types, the research offers a pathway toward fairer ASR systems that do not function better for certain speaker groups than others.

Third, **Adversarial Malware Generation in Linux ELF Binaries via Semantic-Preserving Transformations** addresses a gap in security research regarding Linux Executable and Linkable Format (ELF) files. While Windows Portable Executable (PE) files have been extensively studied, ELF files have received minimal attention. The authors summarize academic papers in this field and develop a new adversarial malware generator. They achieved an Evasion Rate of 67.74% while changing the configuration, demonstrating a significant capability to bypass detection systems. This highlights the evolving nature of adversarial attacks in the context of operating system security.

These developments underscore the ongoing tension between model utility and safety. The watermarking work protects IP, the fairness work addresses societal bias, and the malware work exposes vulnerabilities in security infrastructure. Together, they suggest a field that is maturing in its ability to identify, measure, and mitigate risks across different domains.

## Adversarial Attacks & Robustness

The landscape of adversarial security continues to evolve, with recent work focusing on both offensive capabilities and defensive strategies. A key theme is the shift from single-shot attacks to adaptive, co-evolutionary processes.

**Adversarial Co-Evolution of Malware and Detection Models: A Bilevel Optimization Perspective** proposes a robust defense framework based on bilevel optimization. This approach explicitly models the strategic interaction between a defender and an attacker as an adversarial co-evolutionary process. Traditional defenses, such as one-shot adversarial training, often fail against adaptive attackers who use reinforcement learning to bypass detection. The authors evaluate their approach using the MAB-malware framework against three distinct malware families: Mokes, Strab, and DCRat. Their experimental results demonstrate that modeling the co-evolutionary process leads to more robust defenses compared to static training methods. This work complements the offensive capabilities described in **Adversarial Malware Generation in Linux ELF Binaries via Semantic-Preserving Transformations**, which focuses on the generation side. While the ELF paper demonstrates the potential for high evasion rates, the bilevel optimization paper offers a theoretical framework for defense that accounts for the adaptive nature of attackers.

Another significant contribution is **Detecting Concept Drift in Evolving Malware Families Using Rule-Based Classifier Representations**. This work proposes a structural approach to concept drift detection in malware classification using decision tree rulesets. Classifiers are trained across temporal windows on the EMBER2024 dataset, and drift is quantified by comparing extracted rule representations using feature importance, prediction agreement, activation stability, and coverage metrics. These metrics are correlated with both accuracy degradation and data distribution shift as complementary drift indicators. The approach is evaluated across six malware families using fixed-interval and clustering-based windowing in family-vs-family scenarios. This method provides a mechanism for monitoring the stability of security models over time, which is crucial for maintaining defense efficacy in dynamic threat landscapes.

In the realm of cryptographic security, **Horizontal SCA Attacks on Binary kP Algorithms using Chevallier-Mames Atomic Blocks** demonstrates vulnerabilities in Elliptic Curve (EC) cryptosystems. Scalar multiplication kP is the operation most frequently targeted in these systems. To protect against single-trace Side-Channel Analysis (SCA) attacks, the atomicity principle and various atomic block patterns have been proposed in the past. The authors use software and hardware implementations to demonstrate that binary right-to-left and left-to-right kP algorithms, when implemented with Chevallier-Mames atomic block patterns, are still vulnerable to single-trace SCA attacks. The vulnerability remains true for the left-to-right kP algorithm with projective coordinates. This finding challenges the assumption that certain atomic block patterns provide sufficient protection against side-channel attacks, suggesting that further research is needed to secure cryptographic implementations against advanced analysis techniques.

These works collectively highlight the arms race between attackers and defenders. The malware generation and co-evolution papers show that attackers are becoming more sophisticated, while the concept drift and cryptographic papers emphasize the need for continuous monitoring and rigorous verification of security measures. The interplay between these offensive and defensive strategies suggests that static defenses are insufficient, and adaptive, dynamic approaches are necessary for long-term security.

## Model Alignment & Interpretability

Alignment research continues to focus on ensuring that models behave as intended, particularly in complex reasoning and generative tasks. Recent work explores efficient reasoning mechanisms, evidence highlighting, and the mitigation of harmful biases.

**Thinking Without Words: Efficient Latent Reasoning with Abstract Chain-of-Thought** addresses the cost of long, explicit chains-of-thought (CoT) in complex reasoning tasks. While verbalized CoT has proven effective, it is costly to generate during inference. Non-verbal reasoning methods have emerged with shorter generation lengths by leveraging continuous representations, yet their performance lags behind verbalized CoT. The authors propose Abstract Chain-of-Thought, a discrete latent reasoning post-training mechanism in which the language model produces a short sequence of tokens from a reserved vocabulary in lieu of a natural language CoT, before generating a response. To make previously unseen "abstract" tokens interpretable, the method employs a training strategy that aligns these tokens with reasoning steps. This approach aims to balance efficiency and performance, offering a potential solution to the computational bottlenecks associated with long CoT reasoning.

Complementing this, **Learning Evidence Highlighting for Frozen LLMs** introduces HiLight, an Evidence Emphasis framework that decouples evidence selection from reasoning for frozen LLM solvers. Large Language Models (LLMs) can reason well, yet often miss decisive evidence when it is buried in long, noisy contexts. HiLight avoids compressing or rewriting the input, which can discard or distort evidence, by training a lightweight Emphasis Actor to insert minimal highlight tags around pivotal spans in the unaltered context. A frozen Solver then performs downstream reasoning on the emphasized input. The authors cast highlighting as a weakly supervised decision-making problem. This method allows for improved reasoning without fine-tuning the entire model, which is particularly valuable for deploying large models in resource-constrained environments.

In the domain of bias and fairness, **Representational Harms in LLM-Generated Narratives Against Global Majority Nationalities** studies how national origin identities are portrayed by widely-adopted LLMs in responses. Large language models (LLMs) are increasingly used for text generation tasks from everyday use to high-stakes enterprise and government applications, including simulated interviews with asylum seekers. While many works highlight the new potential applications of LLMs, there are risks of LLMs encoding and perpetuating harmful biases about non-dominant communities across the globe. To better evaluate and mitigate such harms, more research examining how LLMs portray diverse individuals is needed. The authors study how national origin identities are portrayed by widely-adopted LLMs in responses to prompts involving global majority nationalities. This work contributes to the growing body of literature on algorithmic bias, emphasizing the need for diverse evaluation metrics that go beyond standard benchmarks.

Furthermore, **Dharma, Data and Deception: An LLM-Powered Rhetorical Analysis of Cow-Urine Health Claims on YouTube** examines 100 YouTube transcripts that promote or debunk cow urine (gomutra) as a health remedy. Health misinformation remains one of the most pressing challenges on social media, particularly when cultural traditions intersect with scientific-sounding claims. These dynamics are not only global but also deeply local, manifesting in culturally specific controversies that require careful analysis. The authors employ large language models (LLMs) including GPT-4, GPT-4o, GPT-4.1, and GPT-4.5 to analyze rhetorical strategies such as appeals to authority, efficacy appeals, and conspiracy framing. This work demonstrates the utility of LLMs in analyzing misinformation, while also highlighting the risks of LLMs being used to generate or amplify such content. The study underscores the importance of understanding the cultural context of misinformation, as standard fact-checking approaches may not be sufficient for culturally specific claims.

These works collectively address the challenge of aligning LLMs with human values and safety requirements. The reasoning and evidence highlighting papers focus on improving model performance and reliability, while the bias and misinformation papers address the societal impact of model outputs. The interplay between these areas suggests that alignment is not just a technical challenge but also a social one, requiring a multidisciplinary approach to ensure that models are both effective and safe.

## Privacy Protection & Federated Learning

Privacy-preserving techniques are essential for deploying AI systems in sensitive domains. Recent work explores watermarking, private information retrieval, and secure access control.

**ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** also has implications for privacy and intellectual property protection. Self-supervised learning (SSL) encoders are invaluable intellectual property (IP). However, no existing SSL watermarking for IP protection can concurrently satisfy the following two practical requirements: (1) provide ownership verification capability under black-box suspect model access once the stolen encoders are used in downstream tasks; (2) be robust under adversarial watermark detection or removal, because the watermark samples form a distinguishable out-of-distribution (OOD) cluster. The authors propose ArmSSL, an SSL watermarking framework that assures black-box verifiability and adversarial robustness. This work contributes to the broader goal of protecting data and model ownership in an era where AI models are increasingly shared and deployed across different platforms.

**Information-Theoretic Authenticated PIR: From PIR-RV To APIR** addresses the integrity of Private Information Retrieval (PIR) systems. PIR allows clients to retrieve database entries without leaking retrieval indices, yet malicious servers seriously compromise retrieval correctness. Existing Authenticated PIR (APIR) schemes resist selective-failure attacks but rely on computational hardness assumptions. In contrast, information-theoretic PIR with Result Verification (itPIR-RV) achieves integrity without computational assumptions, yet only provides relaxed query privacy with no defense against selective-failure attacks. The authors focus on unconditionally secure information-theoretic APIR (itAPIR). This work bridges the gap between computational and information-theoretic security, offering a more robust solution for privacy-preserving data retrieval. The authors demonstrate that itAPIR can achieve both integrity and query privacy without relying on computational hardness assumptions, which is a significant theoretical advancement.

**PASS: A Provenanced Access Subaccount System for Blockchain Wallets** presents a new system for managing access control in blockchain wallets. Blockchain wallets conventionally follow an ownership model where possession of a private key grants unilateral control. However, this assumption is brittle for emerging settings such as AI agent wallets, organizational custody, and enterprise payroll, where multiple actors must coordinate without exposing secrets or leaking internal activity. The authors present PASS, a Provenanced Access Subaccount System that replaces role-based or identity-based control with provenance-based control: assets can only be used by subaccounts that can trace custody back to a valid deposit. A simple Inbox-Outbox mechanism enables secure coordination. This work addresses the security challenges of multi-party access control in decentralized systems, offering a novel approach that is well-suited for the emerging landscape of AI agent wallets and organizational custody.

These works highlight the diversity of privacy-preserving techniques being developed. The watermarking and PIR papers focus on protecting data and model ownership, while the blockchain paper addresses access control in decentralized systems. The interplay between these areas suggests that privacy is a multifaceted challenge that requires a combination of cryptographic, algorithmic, and system-level solutions. The development of robust watermarking and PIR schemes is particularly important for ensuring that AI systems can be deployed in sensitive domains without compromising user privacy or intellectual property.

## Safety Benchmarks

Evaluating AI systems remains a critical challenge, with recent work focusing on sign language understanding, collective intelligence, and business idea evaluation.

**CNSL-bench: Benchmarking the Sign Language Understanding Capabilities of MLLMs on Chinese National Sign Language** introduces the first comprehensive Chinese National Sign Language benchmark designed for evaluating multimodal large language models (MLLMs) in sign language understanding. Sign language research has achieved significant progress due to the advances in large language models (LLMs). However, the intrinsic ability of LLMs to understand sign language, especially in multimodal contexts, remains underexplored. The proposed CNSL-bench is characterized by: 1) Authoritative grounding, as it is anchored to the officially standardized National Common Sign Language; 2) Multimodal complexity, as it includes video-text pairs; 3) Cultural relevance, as it focuses on Chinese National Sign Language. This benchmark addresses a significant gap in the evaluation of multimodal models, providing a standardized metric for assessing sign language understanding capabilities.

**Superminds Test: Actively Evaluating Collective Intelligence of Agent Society via Probing Agents** presents the first empirical evaluation of collective intelligence in a large-scale autonomous agent society. Collective intelligence refers to the ability of a group to achieve outcomes beyond what any individual member can accomplish alone. As large language model agents scale to populations of millions, a key question arises: Does collective intelligence emerge spontaneously from scale? The authors study MoltBook, a platform hosting over two million agents, and introduce Superminds Test, a hierarchical framework that probes society-level intelligence using controlled Probing Agents across three tiers: joint decision-making, resource allocation, and conflict resolution. This work provides a framework for evaluating the emergent properties of agent societies, which is crucial for understanding the risks and benefits of large-scale autonomous systems.

**Aggregate vs. Personalized Judges in Business Idea Evaluation: Evidence from Expert Disagreement** studies a methodological question raised by expert disagreement in evaluating LLM-generated business ideas. Evaluating LLM-generated business ideas is often harder to scale than generating them. Unlike standard NLP benchmarks, business idea evaluation relies on multi-dimensional criteria such as feasibility, novelty, differentiation, user need, and market size, and expert judgments often disagree. The authors introduce PBIG-DATA, a dataset of approximately 3,000 individual scores across 300 patent-grounded product ideas, provided by domain experts. They study whether an automatic judge should approximate an aggregate consensus or model evaluators individually. This work highlights the complexity of evaluating AI-generated content in domains where human judgment is subjective and diverse. The findings suggest that personalized judges may be more effective than aggregate judges in certain contexts, depending on the specific criteria being evaluated.

These benchmarks address the challenge of evaluating AI systems in diverse domains. The sign language and collective intelligence papers focus on multimodal and multi-agent systems, while the business idea evaluation paper addresses the subjectivity of human judgment. The interplay between these areas suggests that evaluation is not a one-size-fits-all problem, but rather requires domain-specific metrics and methodologies. The development of robust benchmarks is essential for ensuring that AI systems are safe and effective in real-world applications.

## Agent Security & Governance

The security and governance of AI agents are becoming increasingly important as these systems are deployed in complex environments. Recent work explores token consumption, access control, and policy changes.

**How Do AI Agents Spend Your Money? Analyzing and Predicting Token Consumption in Agentic Coding Tasks** presents the first systematic study of token consumption patterns in agentic coding tasks. The wide adoption of AI agents in complex human workflows is driving rapid growth in

---


## References

- **Identifying and typifying demographic unfairness in phoneme-level embeddings of self-supervised speech recognition models** — [arxiv_cl](https://arxiv.org/abs/2604.22631v1)
- **ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** — [arxiv_cr](https://arxiv.org/abs/2604.22550v1)
- **Representational Harms in LLM-Generated Narratives Against Global Majority Nationalities** — [arxiv_cl](https://arxiv.org/abs/2604.22749v1)
- **Thinking Without Words: Efficient Latent Reasoning with Abstract Chain-of-Thought** — [arxiv_cl](https://arxiv.org/abs/2604.22709v1)
- **Learning Evidence Highlighting for Frozen LLMs** — [arxiv_cl](https://arxiv.org/abs/2604.22565v1)
- **Controllable Spoken Dialogue Generation: An LLM-Driven Grading System for K-12 Non-Native English Learners** — [arxiv_cl](https://arxiv.org/abs/2604.22542v1)
- **Selective Contrastive Learning For Gloss Free Sign Language Translation** — [arxiv_cl](https://arxiv.org/abs/2604.22374v1)
- **CNSL-bench: Benchmarking the Sign Language Understanding Capabilities of MLLMs on Chinese National Sign Language** — [arxiv_cl](https://arxiv.org/abs/2604.22367v1)
- **Adversarial Malware Generation in Linux ELF Binaries via Semantic-Preserving Transformations** — [arxiv_cr](https://arxiv.org/abs/2604.22639v1)
- **PASS: A Provenanced Access Subaccount System for Blockchain Wallets** — [arxiv_cr](https://arxiv.org/abs/2604.22602v1)
- **Adversarial Co-Evolution of Malware and Detection Models: A Bilevel Optimization Perspective** — [arxiv_cr](https://arxiv.org/abs/2604.22569v1)
- **Information-Theoretic Authenticated PIR: From PIR-RV To APIR** — [arxiv_cr](https://arxiv.org/abs/2604.22505v1)
- **Automation-Exploit: A Multi-Agent LLM Framework for Adaptive Offensive Security with Digital Twin-Based Risk-Mitigated Exploitation** — [arxiv_cr](https://arxiv.org/abs/2604.22427v1)
- **How Do AI Agents Spend Your Money? Analyzing and Predicting Token Consumption in Agentic Coding Tasks** — [arxiv_cl](https://arxiv.org/abs/2604.22750v1)
- **Neural Recovery of Historical Lexical Structure in Bantu Languages from Modern Data** — [arxiv_cl](https://arxiv.org/abs/2604.22730v1)
- **Zero-Shot Morphological Discovery in Low-Resource Bantu Languages via Cross-Lingual Transfer and Unsupervised Clustering** — [arxiv_cl](https://arxiv.org/abs/2604.22723v1)
- **CRAFT: Clustered Regression for Adaptive Filtering of Training data** — [arxiv_cl](https://arxiv.org/abs/2604.22693v1)
- **BERAG: Bayesian Ensemble Retrieval-Augmented Generation for Knowledge-based Visual Question Answering** — [arxiv_cl](https://arxiv.org/abs/2604.22678v1)
- **Can QPP Choose the Right Query Variant? Evaluating Query Variant Selection for RAG Pipelines** — [arxiv_cl](https://arxiv.org/abs/2604.22661v1)
- **From graphemic dependence to lexical structure: a Markovian perspective on Dante's Commedia** — [arxiv_cl](https://arxiv.org/abs/2604.22626v1)
- **Dharma, Data and Deception: An LLM-Powered Rhetorical Analysis of Cow-Urine Health Claims on YouTube** — [arxiv_cl](https://arxiv.org/abs/2604.22606v1)
- **QuantClaw: Precision Where It Matters for OpenClaw** — [arxiv_cl](https://arxiv.org/abs/2604.22577v1)
- **Using Embedding Models to Improve Probabilistic Race Prediction** — [arxiv_cl](https://arxiv.org/abs/2604.22555v1)
- **RouteLMT: Learned Sample Routing for Hybrid LLM Translation Deployment** — [arxiv_cl](https://arxiv.org/abs/2604.22520v1)
- **Aggregate vs. Personalized Judges in Business Idea Evaluation: Evidence from Expert Disagreement** — [arxiv_cl](https://arxiv.org/abs/2604.22517v1)
- **Measuring and Mitigating Persona Distortions from AI Writing Assistance** — [arxiv_cl](https://arxiv.org/abs/2604.22503v1)
- **Detecting Concept Drift in Evolving Malware Families Using Rule-Based Classifier Representations** — [arxiv_cr](https://arxiv.org/abs/2604.22629v1)
- **Horizontal SCA Attacks on Binary kP Algorithms using Chevallier-Mames Atomic Blocks** — [arxiv_cr](https://arxiv.org/abs/2604.22429v1)
- **Announcing our partnership with the Republic of Korea** — [deepmind](https://deepmind.google/blog/announcing-our-partnership-with-the-republic-of-korea/)
- **Our principles** — [openai](https://openai.com/index/our-principles)
- **home-assistant / core** — [github](https://github.com/home-assistant/core)
- **curl / curl** — [github](https://github.com/curl/curl)
- **trycua / cua** — [github](https://github.com/trycua/cua)
- **PostHog / posthog** — [github](https://github.com/PostHog/posthog)
- **abhigyanpatwari / GitNexus** — [github](https://github.com/abhigyanpatwari/GitNexus)
- **ComposioHQ / awesome-codex-skills** — [github](https://github.com/ComposioHQ/awesome-codex-skills)
- **openclaw / openclaw** — [github](https://github.com/openclaw/openclaw)
- **codecrafters-io / build-your-own-x** — [github](https://github.com/codecrafters-io/build-your-own-x)
- **microsoft / typescript-go** — [github](https://github.com/microsoft/typescript-go)
- **Alishahryar1 / free-claude-code** — [github](https://github.com/Alishahryar1/free-claude-code)
- **mattpocock / skills** — [github](https://github.com/mattpocock/skills)
- **gastownhall / beads** — [github](https://github.com/gastownhall/beads)
- **Z4nzu / hackingtool** — [github](https://github.com/Z4nzu/hackingtool)
- **最性能、最智能的越野车！猛士M817 Ultimate于北京车展正式亮相** — [qbitai](https://www.qbitai.com/2026/04/408006.html)
- **哈弗“棱角精神”再加码！哈弗猛龙PLUS七座版亮相，预售价19.38万元起** — [qbitai](https://www.qbitai.com/2026/04/407919.html)
- **自主AI汽车芯片「一姐」出手，机器人终于有了专属「小脑」** — [qbitai](https://www.qbitai.com/2026/04/407975.html)
- **世界模型能实时玩了，蚂蚁灵波开源LingBot-World-Fast** — [qbitai](https://www.qbitai.com/2026/04/407972.html)
- **Token驱动未来，城市如何抢占算力新赛道？** — [qbitai](https://www.qbitai.com/2026/04/407960.html)
- **一台中国空间相机，打破索尼富士Adobe的影像垄断** — [qbitai](https://www.qbitai.com/2026/04/407915.html)
- **车长5米3！华为乾崑奕境首款旗舰大六座SUV定名 X9** — [qbitai](https://www.qbitai.com/2026/04/407908.html)
- **探索智能新边界！灵光在手机端上线“体验世界模型”功能** — [qbitai](https://www.qbitai.com/2026/04/407909.html)
- **日产2026北京车展亮剑：两款概念车领衔，新能源赛道持续加码** — [qbitai](https://www.qbitai.com/2026/04/407902.html)
- **B站官宣首届AI造物联赛 打破传统黑客马拉松模式** — [qbitai](https://www.qbitai.com/2026/04/407917.html)
- **星测未来发布新一代天基算力平台** — [36kr](https://36kr.com/newsflashes/3784800646225158?f=rss)
- **前苹果工程师做了款体感游戏机，销量拳打Xbox，营收数亿美元** — [36kr](https://36kr.com/p/3783828639571203?f=rss)
- **早期项目 | 前地平线产品负责人死磕“拿放”动作，轮式机器人今年锁定百台出货** — [36kr](https://36kr.com/p/3783824870317312?f=rss)
- **「破壳机器人」许华哲：两年内，中国将出现可用的家庭机器人** — [36kr](https://36kr.com/p/3784365164322055?f=rss)
- **8点1氪丨豆包提前查到2026山东事业编成绩？最新回应；东方甄选主播集体离职，俞敏洪回应；花呗白条月付等面临重大调整** — [36kr](https://36kr.com/p/3784311487945735?f=rss)
- **百度文库网盘发布通用智能体GenFlow4.0** — [36kr](https://36kr.com/newsflashes/3784782506663172?f=rss)
- **国家发改委：依法依规对外资收购Manus项目作出禁止投资决定** — [36kr](https://36kr.com/newsflashes/3784790761200899?f=rss)
- **韦德布什预测特斯拉和SpaceX明年合并概率达80-90%** — [36kr](https://36kr.com/newsflashes/3784775331454212?f=rss)
- **摩尔线程在北京新设科技公司** — [36kr](https://36kr.com/newsflashes/3784743117790465?f=rss)
- **Superminds Test: Actively Evaluating Collective Intelligence of Agent Society via Probing Agents** — [arxiv_cl](https://arxiv.org/abs/2604.22452v1)
- **SSG: Logit-Balanced Vocabulary Partitioning for LLM Watermarking** — [arxiv_cl](https://arxiv.org/abs/2604.22438v1)
- **Introducing Background Temperature to Characterise Hidden Randomness in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.22411v1)