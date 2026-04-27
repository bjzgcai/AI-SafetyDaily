# AI 日报 [AI 安全] - 2026-04-27


</think>

# 2026 年 4 月 27 日 AI 安全与治理主题综述

## Highlights

当日学术与产业动态呈现出安全防御机制深化、对齐理论向隐性认知延伸以及治理框架向多智能体社会扩展的三重趋势。在安全防御领域，**ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** 提出了一种针对自监督学习编码器的黑盒对抗鲁棒水印方案，作者声称在预印本阶段展示了在对抗性水印检测或移除攻击下仍保持所有权验证能力的潜力，尽管该结果尚未经过独立基准的广泛复现，但其提出的对抗性鲁棒性设计思路为知识产权保护提供了新的理论路径。同时，**Identifying and typifying demographic unfairness in phoneme-level embeddings of self-supervised speech recognition models** 揭示了语音识别模型在音素级嵌入中存在的深层人口统计学偏差，指出高绩效与低绩效说话人组之间的嵌入结构差异是造成公平性问题的关键，这一发现将公平性评估从传统的词错率指标推进到了表征空间的微观结构层面。在治理与评估方面，**Superminds Test: Actively Evaluating Collective Intelligence of Agent Society via Probing Agents** 构建了首个针对大规模自主智能体社会集体智能的层级化评估框架，通过探测智能体在 MoltBook 平台上的交互行为来验证集体智能是否随规模自发涌现，这一工作为未来多智能体系统的社会性安全评估提供了可量化的方法论基础。此外，产业界关于天基算力平台与具身智能机器人的报道虽多，但需警惕部分媒体对技术成熟度的夸大描述，如星测未来发布的“感算一体”计划及前地平线产品负责人关于家庭机器人两年内可用的预测，目前更多处于概念验证或早期原型阶段，尚缺乏大规模落地数据的支持。

## 对抗攻击与鲁棒性：从二进制恶意软件到水印防御

随着人工智能在关键基础设施中的渗透，针对底层代码执行环境及模型知识产权的对抗性攻击呈现出多样化的演进态势。在恶意软件检测领域，针对 Linux 可执行文件格式的对抗性研究相对滞后于 Windows 平台，**Adversarial Malware Generation in Linux ELF Binaries via Semantic-Preserving Transformations** 填补了这一空白。作者提出了一种基于语义保持变换的恶意软件生成器，旨在在保持文件功能不变的前提下绕过检测模型。根据预印本数据，该生成器在特定测试集上实现了 67.74% 的逃逸率，但作者明确指出该结果基于特定的 ELF 变体，且测试环境可能未覆盖所有变种，因此该逃逸率应被视为特定条件下的上限而非通用基准。这一工作与 **Detecting Concept Drift in Evolving Malware Families Using Rule-Based Classifier Representations** 形成了攻防对照。后者提出了一种基于决策树规则表示的结构化概念漂移检测方法，通过在 EMBER2024 数据集上训练分类器并比较规则表示，量化了恶意软件家族随时间演变的漂移程度。作者声称该方法通过特征重要性、预测一致性等指标，能够比传统准确率下降指标更早地捕捉到数据分布的偏移。两者的结合表明，未来的恶意软件防御不仅需要关注静态特征的对抗生成，更需要建立动态的、基于规则演变的监控机制，以应对自适应攻击者的策略调整。

在模型水印与知识产权保护方面，自监督学习（SSL）编码器的知识产权归属问题日益凸显。**ArmSSL: Adversarial Robust Black-Box Watermarking for Self-Supervised Learning Pre-trained Encoders** 针对现有水印方案无法同时满足黑盒验证和对抗鲁棒性的痛点，提出了一种新的水印框架。其核心创新在于利用对抗性样本构建可区分的外部分布（OOD）簇，从而在模型被窃取并用于下游任务后，仍能通过黑盒访问进行所有权验证。作者声称该框架在对抗性水印检测或移除攻击下保持了鲁棒性，但需注意的是，该结论基于预印本实验，且未详细说明在极端对抗扰动下的性能衰减曲线。与之相关的是 **SSG: Logit-Balanced Vocabulary Partitioning for LLM Watermarking**，该研究聚焦于大语言模型水印在低熵设置（如代码生成和数学推理）下的失效问题。作者发现，现有的 KGW 方案中随机词汇划分策略在低熵场景下效果显著下降，并提出了一种基于 Logit 平衡的词汇划分方法。这两项工作共同揭示了水印技术在不同模态和不同应用场景下的局限性：SSL 编码器水印侧重于对抗性鲁棒性，而 LLM 水印则更关注生成过程中的熵值控制。两者的互补性在于，前者为模型架构层面的保护提供了思路，后者为生成内容层面的溯源提供了工具。然而，两者均未完全解决水印被恶意移除后的恢复问题，这提示未来的研究需要探索更深层的、嵌入在模型参数中的不可逆水印机制。

此外，密码学层面的侧信道攻击研究也取得了新进展。**Horizontal SCA Attacks on Binary kP Algorithms using Chevallier-Mames Atomic Blocks** 针对椭圆曲线密码系统中的标量乘法操作，展示了使用 Chevallier-Mames 原子块模式的二进制算法在单迹侧信道分析下的脆弱性。作者通过软件和硬件实现证明，即使采用了原子性原则，特定的原子块模式仍可能泄露密钥信息。这一发现对基于椭圆曲线的区块链钱包安全构成了潜在威胁，特别是对于 **PASS: A Provenanced Access Subaccount System for Blockchain Wallets** 所提出的基于溯源的子账户系统而言，底层密码原语的侧信道漏洞可能成为攻击者绕过访问控制的突破口。作者建议在未来的系统设计中，需将侧信道防护纳入整体安全架构，而不仅仅是依赖逻辑层面的权限控制。

在隐私计算领域，**Information-Theoretic Authenticated PIR: From PIR-RV To APIR** 探讨了私有信息检索（PIR）中的完整性与隐私平衡问题。现有的认证 PIR 方案通常依赖计算困难假设，而信息论 PIR 则缺乏对选择性失败攻击的防御。作者提出了一种无条件安全的信息论认证 PIR 方案，旨在在不依赖计算假设的前提下实现完整性验证。这一工作虽然理论价值显著，但在实际部署中可能面临计算开销过大的挑战。与 **Privacy-Preserving Federated Learning** 相关的研究相比，该方案更侧重于数据库检索层面的隐私，而非模型训练过程中的数据保护。两者的结合可能为构建更安全的分布式数据协作系统提供基础，但需要进一步验证其在大规模数据场景下的可扩展性。

## 模型对齐与可解释性：从叙事偏见到隐性推理

大语言模型在内容生成与决策支持中的应用日益广泛，其内部表征与输出行为对社会公平及认知过程的影响成为研究焦点。**Representational Harms in LLM-Generated Narratives Against Global Majority Nationalities** 深入研究了广泛采用的大语言模型在描述全球多数民族身份时的潜在偏见。作者通过构建评估框架，分析了模型在模拟面试等高风险场景中对非主导社区的描述方式，发现模型可能编码并 perpetuating 有害的刻板印象。这一工作与 **Identifying and typifying demographic unfairness in self-supervised speech recognition models** 形成了跨模态的呼应，表明公平性问题不仅存在于语音识别的音素级嵌入中，也广泛存在于文本生成的叙事结构中。两者的共同点在于，都揭示了模型在表征学习过程中可能无意中放大了训练数据中的社会偏见，而差异在于前者关注文本生成的语义层面，后者关注语音识别的声学特征层面。这提示未来的对齐研究需要建立跨模态的公平性评估标准，以全面覆盖 AI 系统的社会影响。

在文化与社会语境下的对齐问题上，**Dharma, Data and Deception: An LLM-Powered Rhetorical Analysis of Cow-Urine Health Claims on YouTube** 提供了一个独特的案例。作者利用大语言模型分析了 YouTube 上关于牛尿健康功效的 100 个视频转录，聚焦于修辞策略如权威诉求、疗效诉求和阴谋框架。研究发现，AI 模型在分析此类文化特定的争议时，能够识别出传统科学话语与本土信仰之间的张力，但也可能因训练数据的偏差而误判某些文化习俗的合理性。这一工作强调了在跨文化对齐中，模型需要理解特定的社会语境，而不仅仅是遵循通用的科学事实。与 **Measuring and Mitigating Persona Distortions from AI Writing Assistance** 的研究相呼应，后者通过大规模实验发现，AI 写作辅助工具会显著扭曲作者的个性特征，包括政治观点、性格和身份感知。作者声称在 29 个社会显著维度上观察到了明显的扭曲效应，这表明 AI 辅助工具在提升效率的同时，可能削弱了人类表达的真实性。这两项工作共同指向了一个核心问题：AI 系统在增强人类能力的同时，如何避免对个体认知和社会文化的隐性侵蚀。

在推理机制的优化方面，**Thinking Without Words: Efficient Latent Reasoning with Abstract Chain-of-Thought** 提出了一种离散潜在推理机制，即抽象思维链（Abstract Chain-of-Thought）。作者提出，语言模型可以生成一个简短的抽象令牌序列，替代冗长的自然语言思维链，从而在推理任务中实现更高的效率。实验表明，该方法在保持推理性能的同时，显著降低了生成长度和计算成本。这一工作与 **Learning Evidence Highlighting for Frozen LLMs** 形成了互补。后者提出了一种证据强调框架 HiLight，通过训练轻量级的强调演员在未修改的上下文中插入高亮标签，帮助冻结的求解器进行下游推理。两者的共同点在于都试图优化推理过程，但前者侧重于推理过程的压缩与抽象，后者侧重于输入信息的筛选与强调。这种差异表明，未来的推理优化可能需要结合多种策略：既需要高效的内部推理机制，也需要外部信息的精准引导。

此外，**Introducing Background Temperature to Characterise Hidden Randomness in Large Language Models** 探讨了大语言模型在名义温度为零时的实现级非确定性。作者引入了“背景温度”的概念，形式化了由实现依赖的扰动过程（如批次大小变化、内核非不变性）引起的有效温度。这一发现对模型的可复现性和安全性具有重要意义，因为即使在没有随机性的设置下，模型输出仍可能因底层实现细节而波动。这与 **QuantClaw: Precision Where It Matters for OpenClaw** 的研究相关，后者分析了量化对自主智能体系统性能的影响，发现精度要求高度依赖于任务。作者提出了一种即插即用的量化方案，旨在在保持性能的同时降低计算成本。两者的结合表明，未来的模型部署需要同时考虑实现级的随机性和量化带来的精度损失，以确保系统行为的稳定性和可预测性。

## 隐私保护与数据治理：从联邦学习到低资源语言

在隐私保护与数据治理领域，针对低资源语言和数据筛选的研究取得了实质性进展。**Neural Recovery of Historical Lexical Structure in Bantu Languages from Modern Data** 和 **Zero-Shot Morphological Discovery in Low-Resource Bantu Languages via Cross-Lingual Transfer and Unsupervised Clustering** 两项工作共同关注了班图语系的语言结构恢复与形态学发现。前者利用现代形态数据训练神经网络，尝试恢复跨语言的词汇结构，并识别出共享的 cognate 候选词。后者则通过跨语言迁移学习和无监督聚类，在低资源语言 Giriama 中发现了新的形态特征。这两项工作展示了 AI 在语言保护和文化多样性方面的潜力，但也引发了关于数据隐私和知识产权的讨论。在低资源场景下，数据收集往往涉及敏感的文化信息，如何在保护隐私的同时利用这些数据训练模型，是一个亟待解决的问题。

**CRAFT: Clustered Regression for Adaptive Filtering of Training data** 提出了一种向量无关的训练数据筛选方法，旨在从大规模语料中选择高质量子集进行微调。该方法通过两阶段选择：首先通过 k-means 聚类匹配验证源分布，然后在每个源内选择高样本。这一工作与 **Learning Evidence Highlighting for Frozen LLMs** 形成了对比，后者侧重于推理阶段的证据筛选，而前者侧重于训练阶段的数据筛选。两者的结合表明，数据质量的控制需要贯穿模型生命周期的各个阶段。然而，CRAFT 方法在大规模数据上的计算开销仍需进一步评估，特别是在处理非结构化数据时。

在隐私计算方面，**Information-Theoretic Authenticated PIR: From PIR-RV To APIR** 再次被提及，因为它涉及数据库检索的隐私保护。该工作提出了一种无条件安全的信息论认证 PIR 方案，旨在在不依赖计算假设的前提下实现完整性验证。这一方案虽然理论价值显著，但在实际部署中可能面临计算开销过大的挑战。与 **Privacy-Preserving Federated Learning** 相关的研究相比，该方案更侧重于数据库检索层面的隐私，而非模型训练过程中的数据保护。两者的结合可能为构建更安全的分布式数据协作系统提供基础，但需要进一步验证其在大规模数据场景下的可扩展性。

此外，**Using Embedding Models to Improve Probabilistic Race Prediction** 探讨了利用嵌入模型改进概率种族预测的问题。作者指出，现有的 BISG 方法依赖于人口普查姓氏数据，但未能覆盖约 10% 的美国人口，导致预测性能下降。作者提出利用嵌入模型来改进这一过程，但同时也强调了隐私风险。这一工作与 **Identifying and typifying demographic unfairness in self-supervised speech recognition models** 形成了呼应，表明在涉及敏感人口统计信息的应用中，需要平衡预测精度与隐私保护。未来的研究需要探索更安全的隐私保护技术，如差分隐私或同态加密，以在保护个人隐私的同时实现准确预测。

## 安全评估基准与智能体治理：从集体智能到商业评估

随着智能体系统的规模化，对其集体智能和安全性的评估成为研究热点。**Superminds Test: Actively Evaluating Collective Intelligence of Agent Society via Probing Agents** 构建了首个针对大规模自主智能体社会集体智能的层级化评估框架。作者通过探测智能体在 MoltBook 平台上的交互行为，验证了集体智能是否随规模自发涌现。这一工作为未来多智能体系统的社会性安全评估提供了可量化的方法论基础。然而，作者也指出，MoltBook 平台上的智能体数量虽多，但其交互模式可能受到平台设计的限制，因此评估结果可能无法完全代表真实世界的复杂环境。

在商业评估方面，**Aggregate vs. Personalized Judges in Business Idea Evaluation: Evidence from Expert Disagreement** 研究了自动评估者应模拟集体共识还是个体专家的问题。作者引入了 PBIG-DATA 数据集，包含 3000 个个体评分和 300 个专利导向的产品创意。研究发现，专家判断往往存在分歧，因此自动评估者需要能够处理这种分歧。这一工作与 **Measuring and Mitigating Persona Distortions from AI Writing Assistance** 形成了对比，后者关注 AI 对个体个性的扭曲，而前者关注 AI 对集体共识的模拟。两者的结合表明，未来的评估系统需要兼顾个体差异和集体共识，以提供更全面的评估结果。

在智能体效率与成本方面，**How Do AI Agents Spend Your Money? Analyzing and Predicting Token Consumption in Agentic Coding Tasks** 系统研究了智能体编码任务中的令牌消耗模式。作者分析了八个前沿 LLM 在 SWE-bench Verified 上的轨迹，评估了模型预测自身令牌使用量的能力。这一工作与 **QuantClaw: Precision Where It Matters for OpenClaw** 形成了互补，后者关注量化对性能的影响，而前者关注令牌消耗的效率。两者的结合表明，未来的智能体系统需要在性能和成本之间找到平衡，通过量化和令牌预测技术来优化资源利用。

此外，**Automation-Exploit: A Multi-Agent LLM Framework for Adaptive Offensive Security with Digital Twin-Based Risk-Mitigated Exploitation** 提出了一种完全自主的多智能体系统框架，旨在为复杂黑盒场景下的自适应攻防安全提供支持。该系统通过数字孪生技术缓解利用风险， bridging 了侦察与利用之间的抽象差距。这一工作与 **Adversarial Malware Generation in Linux ELF Binaries via Semantic-Preserving Transformations** 形成了攻防对照，前者侧重于利用多智能体进行攻击，后者侧重于生成对抗性恶意软件。两者的结合表明，未来的安全研究需要同时关注攻击和防御，以构建更全面的防御体系。

## 产业趋势与政策监管：审慎看待技术落地与资本动态

在产业界，关于天基算力、具身智能和汽车芯片的报道层出不穷，但需谨慎对待其中的技术成熟度与商业承诺。**星测未来发布新一代天基算力平台** 的报道声称推出了面向 AI 大模型在轨部署的星溪 06Pro 天基算力平台，并

---


## 参考来源

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