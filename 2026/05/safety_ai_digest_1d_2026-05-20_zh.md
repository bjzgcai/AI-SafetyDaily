# AI 日报 [AI 安全] - 2026-05-20


### **2026年5月20日 AI安全专题综述**

#### **Highlights**

今日的学术进展凸显了AI安全领域从单一模型防护向复杂系统治理的范式转移。首先，在**Agent安全**方向，多项研究共同指出，当前主流的提升模型鲁棒性的方法不足以应对自主智能体引入的系统性风险，必须采用系统安全的思维框架。其次，在**后门攻防**领域，针对快速植入攻击的轻量级检测方法取得突破，同时攻击面也扩展到了统一多模态模型和新型扩散语言模型。最后，在**多模态对齐与防御**方面，研究者开始揭示利用多图像输入、自然语言指令等更隐蔽的攻击路径，并提出了基于结构分析的新防御范式。产业层面，谷歌I/O大会全面展示了其AI代理化布局，引发了关于信任、隐私和安全边界的广泛讨论。

---

#### **一、 Agent安全与治理：从模型漏洞到系统风险**

随着大语言模型演变为具备规划、记忆和工具使用能力的自主Agent，其安全问题已超越传统提示注入的范畴，演变为复杂的系统性风险。**《Agent Security is a Systems Problem》** 一文明确主张，应将驱动Agent的AI模型视为不可信组件，并在系统层面强制实施安全不变量。该文指出，单纯增强模型鲁棒性是不充分的，必须借鉴操作系统、网络安全和形式化方法中的技术来构建防护层。这一立场得到了**《OEP: Poisoning Self-Evolving LLM Agents via Locally Correct but Non-Transferable Experiences》** 的经验支持。该研究发现，通过精心构造的“局部正确但不可迁移”的经验来毒化自进化Agent的记忆，可以诱导其在反思过程中产生有害的泛化行为，而这种攻击绕过了现有安全过滤器。这深刻揭示了Agent自主学习机制中一个先前未受重视的脆弱点。

针对动态交互场景，**《Surviving the Unseen: Predictive Defense for Novel Multi-Turn Multimodal Attacks》** 提出了一种预测性防御框架。该框架意识到，攻击者会通过多轮对话、跨模态扰动将恶意意图分散在纵向交互轨迹中，而静态的、仅评估单轮输入的防御机制会失效。同时，**《RoboJailBench: Benchmarking Adversarial Attacks and Defenses in Embodied Robotic Agents》** 发布了首个针对具身机器人的对抗攻防基准，其核心创新在于强调评估安全与遵循良性指令能力之间的权衡，而非仅仅追求攻击成功率，这为衡量真实场景下的安全性能提供了更全面的视角。

#### **二、 后门攻击与检测：速度、广度与新范式**

后门攻击与检测的“军备竞赛”仍在加速，并向新的模型架构蔓延。在防御端，应对快速攻击的轻量级检测器成为焦点。**《Lightweight and Fast Backdoor Model Detection》** 提出了DFBScanner，旨在解决后门可在毫秒级植入而现有检测需要分钟或小时级处理的“速度差”问题。无独有偶，**《Fast and Lightweight Backdoor Detection via Head Random Probing》** 提出了HTell，其核心思想是通过探测模型预测头部的统一表征来检测后门，而非逆向工程复杂的触发模式，从而实现了快速、无需干净数据的检测。这些方法在效率和实用性上相比传统方法有显著提升。

攻击面则在持续扩大。**《Token by Token, Compromised: Backdoor Vulnerabilities in Unified Autoregressive Models》** 首次证明，统一自回归模型因其共享的参数和多模态词表，可能遭受“跨模态后门攻击”，即一个触发器能同时影响文本和图像输出，这为多模态模型的安全部署敲响了警钟。**《Backdooring Masked Diffusion Language Models》** 则将后门研究的触角伸向了新兴的掩码扩散语言模型，提出了SHADOWMASK攻击，证明了这一新范式同样面临严重的训练时安全威胁。在联邦学习场景下，**《Detecting and Mitigating Backdoor Attacks in OTA-FL Systems》** 针对空中联邦学习因信道叠加特性无法区分个体更新的问题，提出了一种两阶段鲁棒聚合方案，以应对非独立同分布数据下恶意更新与良性数据漂移难以区分的挑战。

#### **三、 多模态对齐与防御：从单点突破到结构分析**

针对多模态大模型（MLLM）的越狱攻击正变得更为复杂和隐蔽。**《DMN: A Compositional Framework for Jailbreaking Multimodal LLMs with Multi-Image Inputs》** 揭示了多图像输入这一常被忽视的攻击面，攻击者可以通过将有害请求分布到多张图像中，或利用额外的视觉推理任务来分散模型注意力，从而突破安全对齐。**《DarkLLM: Learning Language-Driven Adversarial Attacks with Large Language Models》** 则另辟蹊径，训练一个LLM将自然语言攻击指令转换为潜空间的对抗向量，使得攻击具备了可扩展性和灵活性，不再局限于单一预设目标。

防御方面，研究开始深入到底层几何结构。**《On the Geometric Limits of Transformer Defenses against Obfuscation Attacks》** 指出了一个关键矛盾：高检测性能并不等同于表征鲁棒性。研究发现，经过多算子混淆的对抗提示可以部分“坍缩”到干净提示的嵌入流形上（即“潜在嵌入坍缩”），从而在语义层面欺骗分类器。这提示防御评估应超越分类准确率，关注模型内部表征的稳定性。**《BiRD: A Bidirectional Ranking Defense Mechanism for Retrieval Augmented Generation》** 为RAG系统的安全提供了新思路，它不再仅仅分析文档内容的语义相关性，而是通过建模文档在检索排名中的双向行为来识别中毒文档，因为恶意文档在向前后文检索时会表现出异常的排名不一致性。

#### **四、 隐私保护与联邦学习：创新架构与可信计算**

隐私计算技术继续在边缘场景和创新架构中深化。**《XAI FL-IDS》** 将联邦学习与SHAP可解释性结合，用于构建分布式入侵检测系统，旨在同时解决数据隐私和模型决策不透明两大痛点。**《Towards Family-Grouped Hierarchical Federated Learning on Sub-5KB Models》** 针对超低功耗可穿戴设备进行隐私保护的心电监测，提出了一种三层架构的联邦学习方案，展示了在极严格资源约束下实现隐私保护协同训练的可行性。

在可信计算与隐私的交叉领域，**《The Privacy Subsidy in Glosten-Milgrom》** 从信息论角度为隐私机制（如对交易方向信号进行二进制翻转）建立了经济学模型，量化了隐私保护对市场价差和福利的影响。**《MultiBallot: Verifiable and privacy-preserving E-Collecting in the Swiss setting》** 则设计了一个针对瑞士电子签名收集的安全协议，在不依赖匿名信道的前提下，实现了参与隐私和可验证性，为电子政务中的隐私保护提供了具体方案。

#### **五、 安全评估基准与可解释性**

全面、可靠的安全评估基准是推动领域进步的基石。除了前文提到的 **《RoboJailBench》** ，**《LLMEval-Logic: A Solver-Verified Chinese Benchmark for Logical Reasoning of LLMs with Adversarial Hardening》** 发布了一个基于真实情境、经过对抗性强化的中文逻辑推理基准，以应对现有基准被前沿模型迅速饱和的问题。**《MixRea》** 基于“非注意盲视”理论，设计了评估LLM在显式任务指令下能否关注到隐含重要上下文线索的基准，揭示了模型与人类注意力模式的差异。

可解释性研究在多个层面展开。**《Exploring and Developing a Pre-Model Safeguard with Draft Models》** 提出了一种“预模型防护”策略，即在调用目标大模型前，先用一个轻量的草稿模型对提示进行安全审计，试图在安全误报和计算成本之间找到平衡。**《CLIF: Concept-Level Influence Functions for Transparent Bottleneck Models》** 将影响函数的应用从样本级扩展到概念级，增强了NLP模型在医学诊断等高风险领域的可解释性。**《Mechanisms of Object Localization in Vision-Language Models》** 通过机制可解释性工具，探究了视觉语言模型中对象定位的驱动机制，为理解模型工作原理提供了新见解。

#### **六、 产业动态与政策启示**

谷歌在I/O 2026大会上全面展示了其AI代理化战略，发布了Gemini 3.5系列模型、Gemini Spark 24/7代理助手，并将AI深度集成到搜索、购物、邮件等核心产品中。这种激进的产品化路径，在提升用户便利的同时，也必然将数据隐私、Agent行为可控性等安全问题推向更广阔的公众视野。国内方面，DeepSeek就用户反馈的隐私泄露疑虑发布了技术说明，将其归因于特殊字符触发的模型幻觉，而非真正的安全事件，这凸显了用户对模型行为确定性和隐私安全的高度关切。OpenAI宣布加入C2PA内容来源标准并集成Google的SynthID，是行业在AI生成内容溯源和透明度方面的积极进展。Anthropic的Pre-training团队引入了知名研究员Andrej Karpathy，预示着前沿基础模型研发的人才竞争仍在继续。

#### **Looking Forward**

今日的文献揭示了若干关键的未解问题：第一，**系统安全范式的可行性**：将Agent安全视为系统问题后，如何设计具体、可形式化验证的安全架构，以兼容AI模型的快速迭代？第二，**后门检测的根本局限**：轻量级检测器能否应对未来更自适应、更不可见的攻击模式，其安全性保证是否存在理论上限？第三，**多模态对齐的失衡**：在单模态上已捉襟见肘的对齐技术，如何有效扩展到输入输出空间呈指数增长的多模态与具身场景，并平衡安全、有用性和泛化能力？第四，**隐私保护的共谋威胁**：在联邦学习和多方计算中，如何设计机制来应对参与者之间日益复杂的合谋攻击？这些问题的探索，将继续定义下一代AI系统的安全边界。

---


## 参考来源

- **XAI FL-IDS: A Federated Learning and SHAP-Based Explainable Framework for Distributed Intrusion Detection Systems** — [arxiv_cr](https://arxiv.org/abs/2605.19448)
- **Lightweight and Fast Backdoor Model Detection** — [arxiv_cr](https://arxiv.org/abs/2605.18907)
- **RoboJailBench: Benchmarking Adversarial Attacks and Defenses in Embodied Robotic Agents** — [arxiv_cr](https://arxiv.org/abs/2605.19328)
- **BiRD: A Bidirectional Ranking Defense Mechanism for Retrieval Augmented Generation** — [arxiv_cr](https://arxiv.org/abs/2605.20123)
- **Towards Family-Grouped Hierarchical Federated Learning on Sub-5KB Models: A Feasibility Study of Privacy-Preserving ECG Monitoring for Ultra-Resource-Constrained Wearables** — [arxiv_cr](https://arxiv.org/abs/2605.18862)
- **Smooth Partial Lotteries for Stable Randomized Selection** — [arxiv_lg](https://arxiv.org/abs/2605.20069v1)
- **Decentralized autonomous organization and blockchain-based incentivization framework for community-based facilities management** — [arxiv_cr](https://arxiv.org/abs/2605.18773)
- **Fast and Lightweight Backdoor Detection via Head Random Probing** — [arxiv_cr](https://arxiv.org/abs/2605.18908)
- **DMN: A Compositional Framework for Jailbreaking Multimodal LLMs with Multi-Image Inputs** — [arxiv_cr](https://arxiv.org/abs/2605.18915)
- **OEP: Poisoning Self-Evolving LLM Agents via Locally Correct but Non-Transferable Experiences** — [arxiv_cr](https://arxiv.org/abs/2605.18930)
- **Surviving the Unseen: Predictive Defense for Novel Multi-Turn Multimodal Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.18988)
- **Agent Security is a Systems Problem** — [arxiv_cr](https://arxiv.org/abs/2605.18991)
- **Be Kind, Rewrite: Benign Projections via Rewriting Defend Against LLM Data Poisoning Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.19147)
- **On the Geometric Limits of Transformer Defenses against Obfuscation Attacks: Latent Embedding Collapse & Performance Robustness Gap** — [arxiv_cr](https://arxiv.org/abs/2605.19159)
- **Token by Token, Compromised: Backdoor Vulnerabilities in Unified Autoregressive Models** — [arxiv_cr](https://arxiv.org/abs/2605.19227)
- **Detecting and Mitigating Backdoor Attacks in OTA-FL Systems: A Two-Stage Robust Aggregation Scheme** — [arxiv_cr](https://arxiv.org/abs/2605.19253)
- **MultiBallot: Verifiable and privacy-preserving E-Collecting in the Swiss setting** — [arxiv_cr](https://arxiv.org/abs/2605.19312)
- **Exploring and Developing a Pre-Model Safeguard with Draft Models** — [arxiv_cr](https://arxiv.org/abs/2605.19321)
- **Backdooring Masked Diffusion Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.19262)
- **The Privacy Subsidy in Glosten-Milgrom: Bid-Ask Spread and Welfare under Flip-Noise Direction Observation** — [arxiv_cr](https://arxiv.org/abs/2605.19742)
- **MSAVBench: Towards Comprehensive and Reliable Evaluation of Multi-Shot Audio-Video Generation** — [arxiv_cv](https://arxiv.org/abs/2605.20183v1)
- **When Critics Disagree: Adaptive Reward Poisoning Attacks in RIS-Aided Wireless Control System** — [arxiv_lg](https://arxiv.org/abs/2605.20037v1)
- **Detecting Fluent Optimization-Based Adversarial Prompts via Sequential Entropy Changes** — [arxiv_lg](https://arxiv.org/abs/2605.19966v1)
- **Auditing Privacy in Multi-Tenant RAG under Account Collusion** — [arxiv_lg](https://arxiv.org/abs/2605.19847v1)
- **Towards Fine-Grained Robustness: Attention-Guided Test-Time Prompt Tuning for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.19956v1)
- **A Framework for Evaluating Zero-Shot Image Generation in Concept-based Explainability** — [arxiv_cv](https://arxiv.org/abs/2605.19855v1)
- **Stitched Value Model for Diffusion Alignment** — [arxiv_cv](https://arxiv.org/abs/2605.19804v1)
- **Mechanisms of Object Localization in Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.19792v1)
- **Where Does Authorship Signal Emerge in Encoder-Based Language Models?** — [arxiv_cl](https://arxiv.org/abs/2605.19908v1)
- **Mega-ASR: Towards In-the-wild^2 Speech Recognition via Scaling up Real-world Acoustic Simulation** — [arxiv_cl](https://arxiv.org/abs/2605.19833v1)
- **Mathematical Reasoning in Large Language Models: Benchmarks, Architectures, Evaluation, and Open Challenges** — [arxiv_cl](https://arxiv.org/abs/2605.19723v1)
- **DarkLLM: Learning Language-Driven Adversarial Attacks with Large Language Models** — [arxiv_cr](https://arxiv.org/abs/2605.18868)
- **Atoms of Thought: Universal EEG Representation Learning with Microstates** — [arxiv_lg](https://arxiv.org/abs/2605.20182v1)
- **Multi-axis Analysis of Image Manipulation Localization** — [arxiv_lg](https://arxiv.org/abs/2605.20174v1)
- **SAGE: Scalable Automatic Gating Ensemble for Confident Negative Harvesting in Fraud Detection** — [arxiv_lg](https://arxiv.org/abs/2605.20157v1)
- **Beyond Prediction Accuracy: Target-Space Recovery Profiles for Evaluating Model-Brain Alignment** — [arxiv_lg](https://arxiv.org/abs/2605.20127v1)
- **Beyond Isotropy in JEPAs: Hamiltonian Geometry and Symplectic Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.20107v1)
- **Optimal Representation Size: High-Dimensional Analysis of Pretraining and Linear Probing** — [arxiv_lg](https://arxiv.org/abs/2605.20105v1)
- **INSHAPE: Instance-Level Shapelets for Interpretable Time-Series Classification** — [arxiv_lg](https://arxiv.org/abs/2605.20088v1)
- **Towards Distillation Guarantees under Algorithmic Alignment for Combinatorial Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.20074v1)
- **Training Neural Networks with Optimal Double-Bayesian Learning** — [arxiv_lg](https://arxiv.org/abs/2605.20009v1)
- **Learning with Foresight: Enhancing Neural Routing Policy via Multi-Node Lookahead Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.19975v1)
- **Your Neighbors Know: Leveraging Local Neighborhoods for Backdoor Detection in Decentralized Learning** — [arxiv_lg](https://arxiv.org/abs/2605.19969v1)
- **StruMPL: Multi-task Dense Regression under Disjoint Partial Supervision and MNAR Labels** — [arxiv_lg](https://arxiv.org/abs/2605.19931v1)
- **PixVerve: Advancing Native UHR Image Generation to 100MP with a Large-Scale High-Quality Dataset** — [arxiv_cv](https://arxiv.org/abs/2605.20147v1)
- **Spatially Prompted Visual Trajectory Prediction for Egocentric Manipulation** — [arxiv_cv](https://arxiv.org/abs/2605.20085v1)
- **Cardiac fat segmentation using computed tomography and an image-to-image conditional generative adversarial neural network** — [arxiv_cv](https://arxiv.org/abs/2605.20064v1)
- **RECIPE: Procedural Planning via Grounding in Instructional Video** — [arxiv_cv](https://arxiv.org/abs/2605.19976v1)
- **Feed-Forward Gaussian Splatting from Sparse Aerial Views** — [arxiv_cv](https://arxiv.org/abs/2605.19949v1)
- **GLUT: 3D Gaussian Lookup Table for Continuous Color Transformation** — [arxiv_cv](https://arxiv.org/abs/2605.19889v1)
- **Structural Energy Guidance for View-Consistent Text-to-3D Generation** — [arxiv_cv](https://arxiv.org/abs/2605.19876v1)
- **Passive Construction Site Safety Monitoring via Persona-Scaffolded Adversarial Chain-of-Thought VLM Verification** — [arxiv_cv](https://arxiv.org/abs/2605.19869v1)
- **When Preference Labels Fall Short: Aligning Diffusion Models from Real Data** — [arxiv_cv](https://arxiv.org/abs/2605.19839v1)
- **LaCoVL-FER: Landmark-Guided Contrastive Learning Network with Vision-Language Enhancement for Facial Expression Recognition** — [arxiv_cv](https://arxiv.org/abs/2605.19821v1)
- **MixRea: Benchmarking Explicit-Implicit Reasoning in Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2605.20128v1)
- **ThoughtTrace: Understanding User Thoughts in Real-World LLM Interactions** — [arxiv_cl](https://arxiv.org/abs/2605.20087v1)
- **CopT: Contrastive On-Policy Thinking with Continuous Spaces for General and Agentic Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.20075v1)
- **Text-to-SPARQL Generation with Reinforcement Learning: A GRPO-based Approach on DBLP** — [arxiv_cl](https://arxiv.org/abs/2605.20066v1)
- **Rewarding Beliefs, Not Actions: Consistency-Guided Credit Assignment for Long-Horizon Agents** — [arxiv_cl](https://arxiv.org/abs/2605.20061v1)
- **PEEK: Context Map as an Orientation Cache for Long-Context LLM Agents** — [arxiv_cl](https://arxiv.org/abs/2605.19932v1)
- **Are Tools Always Beneficial? Learning to Invoke Tools Adaptively for Dual-Mode Multimodal LLM Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.19852v1)
- **CLIF: Concept-Level Influence Functions for Transparent Bottleneck Models** — [arxiv_cl](https://arxiv.org/abs/2605.19848v1)
- **FineBench: Benchmarking and Enhancing Vision-Language Models for Fine-grained Human Activity Understanding** — [arxiv_cl](https://arxiv.org/abs/2605.19846v1)
- **CADENet: Condition-Adaptive Asynchronous Dual-Stream Enhancement Network for Adverse Weather Perception in Autonomous Driving** — [arxiv_cl](https://arxiv.org/abs/2605.19837v1)
- **From Prompts to Pavement Through Time: Temporal Grounding in Agentic Scene-to-Plan Reasoning** — [arxiv_cl](https://arxiv.org/abs/2605.19824v1)
- **Synthesis and Evaluation of Long-term History-aware Medical Dialogue** — [arxiv_cl](https://arxiv.org/abs/2605.19766v1)
- **LLMEval-Logic: A Solver-Verified Chinese Benchmark for Logical Reasoning of LLMs with Adversarial Hardening** — [arxiv_cl](https://arxiv.org/abs/2605.19597v1)
- **GoLongRL: Capability-Oriented Long Context Reinforcement Learning with Multitask Alignment** — [arxiv_cl](https://arxiv.org/abs/2605.19577v1)
- **Library Drift: Diagnosing and Fixing a Silent Failure Mode in Self-Evolving LLM Skill Libraries** — [arxiv_cl](https://arxiv.org/abs/2605.19576v1)
- **m3BERT: A Modern, Multi-lingual, Matryoshka Bidirectional Encoder** — [arxiv_cl](https://arxiv.org/abs/2605.19568v1)
- **HaorFloodAlert: Deseasonalized ML Ensemble for 72-Hour Flood Prediction in Bangladesh Haor Wetlands** — [arxiv_lg](https://arxiv.org/abs/2605.20167v1)
- **Interpretable Computer Vision for Defect Detection in X-ray Tomography of Aerospace SiC/SiC Composites** — [arxiv_lg](https://arxiv.org/abs/2605.20159v1)
- **PiG-Avatar: Hierarchical Neural-Field-Guided Gaussian Avatars** — [arxiv_cv](https://arxiv.org/abs/2605.20185v1)
- **CaMo: Camera Motion Grounded Evaluation and Training for Vision-Language Models** — [arxiv_cv](https://arxiv.org/abs/2605.20165v1)
- **TIDE: Efficient and Lossless MoE Diffusion LLM Inference with I/O-aware Expert Offload** — [arxiv_cl](https://arxiv.org/abs/2605.20179v1)
- **When Does Model Collapse Occur in Structured Interactive Learning?** — [arxiv_lg](https://arxiv.org/abs/2605.20151v1)
- **Goal-Oriented Lower-Tail Calibration of Gaussian Processes for Bayesian Optimization** — [arxiv_lg](https://arxiv.org/abs/2605.20145v1)
- **TideGS: Scalable Training of Over One Billion 3D Gaussian Splatting Primitives via Out-of-Core Optimization** — [arxiv_cv](https://arxiv.org/abs/2605.20150v1)
- **SetCon: Towards Open-Ended Referring Segmentation via Set-Level Concept Prediction** — [arxiv_cv](https://arxiv.org/abs/2605.20110v1)
- **MetaEarth-MM: Unified Multimodal Remote Sensing Image Generation with Scene-centered Joint Modeling** — [arxiv_cv](https://arxiv.org/abs/2605.20090v1)
- **Demis Hassabis said this might be the ‘foothills of the singularity.’ What?** — [theverge_ai](https://www.theverge.com/tech/934260/google-io-ai-singularity-demis-hassabis)
- **The future of Google is a search box that does everything** — [theverge_ai](https://www.theverge.com/tech/934217/google-search-box-does-everything-ai-io-2026)
- **Google’s AI future demands trust — and your personal data** — [theverge_ai](https://www.theverge.com/tech/934172/google-io-gemini-ai-trust-personal-data)
- **From teen hacker to Iron Dome researcher, this founder raised $28M to fight AI phishing** — [techcrunch_ai](https://techcrunch.com/2026/05/19/from-teen-hacker-to-iron-dome-researcher-this-founder-raised-28m-to-fight-ai-phishing/)
- **Gemini will use Volvo’s external cameras to interpret parking signs** — [theverge_ai](https://www.theverge.com/transportation/933556/google-io-gemini-volvo-ex60-camera-ai-parking)
- **The 13 biggest announcements at Google I/O 2026** — [theverge_ai](https://www.theverge.com/tech/933415/google-io-2026-biggest-announcements-ai-gemini)
- **Google wants to compete with Anthropic’s Mythos** — [theverge_ai](https://www.theverge.com/tech/933921/google-wants-to-compete-with-anthropics-mythos)
- **Elon Musk said Sam Altman ‘stole’ a non-profit — but the trial showed he had similar aims** — [techcrunch_ai](https://techcrunch.com/2026/05/19/elon-musk-said-sam-altman-stole-a-non-profit-but-the-trial-showed-he-had-similar-aims/)
- **Google takes a page out of Meta’s book, announces new audio-powered smart glasses at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-takes-a-page-out-of-metas-book-announces-new-audio-powered-smart-glasses-at-io-2026/)
- **Google’s Genie world model can now simulate real streets with Street View** — [techcrunch_ai](https://techcrunch.com/2026/05/19/googles-genie-world-model-can-now-simulate-real-streets-with-street-view/)
- **With Gemini 3.5 Flash, Google bets its next AI wave on agents, not chatbots** — [techcrunch_ai](https://techcrunch.com/2026/05/19/with-gemini-3-5-flash-google-bets-its-next-ai-wave-on-agents-not-chatbots/)
- **Google Search as you know it is over** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-search-as-you-know-it-is-over/)
- **Introducing OpenAI for Singapore** — [openai](https://openai.com/index/introducing-openai-for-singapore)
- **Roundtables: Inside the Musk v. Altman Trial** — [mit_tech_review](https://www.technologyreview.com/2026/05/19/1137454/roundtables-inside-the-musk-v-altman-trial/)
- **Google can now vibe-code you an Android app** — [theverge_ai](https://www.theverge.com/tech/932364/google-ai-studio-native-android-apps-vibe-code-google-io-2026)
- **Would you let robots spend your money? Google is betting on it** — [theverge_ai](https://www.theverge.com/news/932927/google-io-agentic-ai-shopping-universal-cart)
- **Google Search is getting its biggest changes ever** — [theverge_ai](https://www.theverge.com/tech/932970/google-search-ai-update-io-2026)
- **Gmail is going to start talking to you** — [theverge_ai](https://www.theverge.com/tech/932973/google-gmail-live-ai-keep-docs-io-2026)
- **Agentic app coding gets an upgrade with Google’s release of Android CLI** — [techcrunch_ai](https://techcrunch.com/2026/05/19/agentic-app-coding-gets-an-upgrade-with-googles-release-of-android-cli/)
- **Google’s AI Studio now lets anyone build Android apps in minutes** — [techcrunch_ai](https://techcrunch.com/2026/05/19/googles-ai-studio-now-lets-anyone-build-android-apps-in-minutes/)
- **Google launches Antigravity 2.0 with an updated desktop app and CLI tool at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-launches-antigravity-2-0-with-an-updated-desktop-app-and-cli-tool-at-io-2026/)
- **Google introduces Gemini Spark, a 24/7 agentic assistant with Gmail integration, at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-introduces-gemini-spark-a-24-7-agentic-assistant-with-gmail-integration/)
- **Google’s Gemini Omni turns images, audio, and text into video — and that’s just the start** — [techcrunch_ai](https://techcrunch.com/2026/05/19/googles-gemini-omni-turns-images-audio-and-text-into-video-and-thats-just-the-start/)
- **OpenAI co-founder Andrej Karpathy joins Anthropic’s pre-training team** — [techcrunch_ai](https://techcrunch.com/2026/05/19/openai-co-founder-andrej-karpathy-joins-anthropics-pre-training-team/)
- **I/O 2026** — [google_ai](https://blog.google/innovation-and-ai/technology/developers-tools/google-io-2026-collection/)
- **How AI Mode is changing the way people search in the U.S.** — [google_ai](https://blog.google/products-and-platforms/products/search/ai-mode-us-insights/)
- **Understanding the modern cybercrime landscape** — [mit_tech_review](https://www.technologyreview.com/2026/05/19/1136925/understanding-the-modern-cybercrime-landscape/)
- **The Download: Musk v. Altman, smart glasses for warfare, and Google I/O** — [mit_tech_review](https://www.technologyreview.com/2026/05/19/1137505/the-download-musk-altman-trial-smart-glasses-warfare-google-i-o/)
- **Colossal Biosciences is growing chickens in a 3D-printed artificial eggshell** — [mit_tech_review](https://www.technologyreview.com/2026/05/19/1137471/colossal-biosciences-is-growing-chickens-in-a-3d-printed-container/)
- **Google just declared itself a contender in AI design at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/ai-design-tools-are-the-next-big-battleground-and-google-is-going-all-in-at-io-2026/)
- **You can now talk to your Gmail inbox, as seen at Google IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/you-can-now-talk-to-your-gmail-inbox-as-seen-at-google-io-2026/)
- **How to use Google’s new AI agents to go beyond your standard searches** — [techcrunch_ai](https://techcrunch.com/2026/05/19/how-to-use-googles-new-ai-agents-to-go-beyond-your-standard-searches/)
- **OpenAI is making it easier to check if an image was made by their models** — [techcrunch_ai](https://techcrunch.com/2026/05/19/openai-is-making-it-easier-to-check-if-an-image-was-made-by-their-models/)
- **Google’s new Universal Cart wants to follow your entire shopping journey across the internet** — [techcrunch_ai](https://techcrunch.com/2026/05/19/googles-new-universal-cart-wants-to-follow-your-entire-shopping-journey-across-the-internet/)
- **Google adds voice-based prompting to Docs and Keep** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-adds-voice-based-prompting-to-docs-and-keep/)
- **Google updates its Gemini app to take on ChatGPT and Claude at IO 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/19/google-updates-its-gemini-app-to-take-on-chatgpt-and-claude-at-io-2026/)
- **I/O 2026: Welcome to the agentic Gemini era** — [google_ai](https://blog.google/innovation-and-ai/sundar-pichai-io-2026/)
- **Gemini 3.5: frontier intelligence with action** — [google_ai](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-5/)
- **A new era for AI Search** — [google_ai](https://blog.google/products-and-platforms/products/search/search-io-2026/)
- **Everything new in our Google AI subscriptions, fresh from I/O 2026** — [google_ai](https://blog.google/products-and-platforms/products/google-one/google-ai-subscriptions/)
- **Advancing content provenance for a safer, more transparent AI ecosystem** — [openai](https://openai.com/index/advancing-content-provenance)
- **New ways to create and get things done in Google Workspace** — [google_ai](https://blog.google/products-and-platforms/products/workspace/workspace-updates/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **kevintsai1202/teaching-site-skills** — [github](https://github.com/kevintsai1202/teaching-site-skills)
- **richard-kim-79/archora-skills** — [github](https://github.com/richard-kim-79/archora-skills)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **mdowis/anansi** — [github](https://github.com/mdowis/anansi)
- **zimingttkx/QuantumFlow** — [github](https://github.com/zimingttkx/QuantumFlow)
- **ahammadmejbah/Awesome-Datasets-Hub** — [github](https://github.com/ahammadmejbah/Awesome-Datasets-Hub)
- **exploitbench/exploitbench** — [github](https://github.com/exploitbench/exploitbench)
- **Siva-Chidambaram12/kalshi-trading-bot** — [github](https://github.com/Siva-Chidambaram12/kalshi-trading-bot)
- **dex-original/okx-agent-trade-kit** — [github](https://github.com/dex-original/okx-agent-trade-kit)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **BasZ4ll/Stable-Diffusion-WebUI** — [github](https://github.com/BasZ4ll/Stable-Diffusion-WebUI)
- **yetone/native-feel-skill** — [github](https://github.com/yetone/native-feel-skill)
- **Google just redesigned the search box for the first time in 25 years — here’s why it matters more than you think.** — [venturebeat_ai](https://venturebeat.com/technology/google-just-redesigned-the-search-box-for-the-first-time-in-25-years-heres-why-it-matters-more-than-you-think)
- **xuanlinAI/overmind** — [github](https://github.com/xuanlinAI/overmind)
- **hunhee98/pluck** — [github](https://github.com/hunhee98/pluck)
- **ForgeAILab/forge** — [github](https://github.com/ForgeAILab/forge)
- **jigripokri/POHA** — [github](https://github.com/jigripokri/POHA)
- **CHB-learner/PaperPilot** — [github](https://github.com/CHB-learner/PaperPilot)
- **DaoyuanLi2816/can-i-finetune-this** — [github](https://github.com/DaoyuanLi2816/can-i-finetune-this)
- **kgmkm/novel2hermes_jp** — [github](https://github.com/kgmkm/novel2hermes_jp)
- **Bridging the Disciplinary Gap in Explainable AI: From Abstract Desiderata to Concrete Tasks** — [arxiv_cy](https://arxiv.org/abs/2605.20081)
- **Addressing the Reality Gap: A Three-Tension Framework for Agentic AI Adoption** — [arxiv_cy](https://arxiv.org/abs/2604.27245)
- **苏姿丰上海开讲：AI正在重新定义计算的每一层** — [qbitai](https://www.qbitai.com/2026/05/420531.html)
- **完成“由铁到钢”的生态蜕变 刘军携联想全场景AI终端点亮智能未来** — [qbitai](https://www.qbitai.com/2026/05/420561.html)
- **抢先李飞飞！世界模型能多人联机玩FPS游戏了** — [qbitai](https://www.qbitai.com/2026/05/420083.html)
- **国产GPU开始造世界！国内首个全栈具身智能仿真平台来了** — [qbitai](https://www.qbitai.com/2026/05/420084.html)
- **Cursor新模型，你怎么还在套Kimi？马斯克你怎么还吆喝上了？？** — [qbitai](https://www.qbitai.com/2026/05/419990.html)
- **Going PLACES: Participatory Localized Red Teaming for Text-to-Image Safety in the Global South** — [arxiv_cy](https://arxiv.org/abs/2605.19190)
- **GRASP: Deterministic argument ranking in interaction graphs** — [arxiv_cy](https://arxiv.org/abs/2605.19141)
- **Rethinking the A in STEAM: Insights from and for AI Literacy Education** — [arxiv_cy](https://arxiv.org/abs/2405.18179)
- **Quantifying the Climate Risk of Generative AI: Region-Aware Carbon Accounting with G-TRACE and the AI Sustainability Pyramid** — [arxiv_cy](https://arxiv.org/abs/2511.04776)
- **Designing escalation criteria for international AI incident response: criteria, triggers, and thresholds** — [arxiv_cy](https://arxiv.org/abs/2604.23183)
- **CAPC-CG: A Large-Scale, Expert-Directed LLM-Annotated Corpus of Adaptive Policy Communication in China** — [arxiv_cy](https://arxiv.org/abs/2510.08986)
- **Technologies and Security Challenges in Metaverse** — [arxiv_cy](https://arxiv.org/abs/2510.09621)
- **Beyond Nutrition Labels: How Analogical Reasoning Shapes Synthetic Media Disclosure Design** — [arxiv_cy](https://arxiv.org/abs/2605.19045)
- **Stop Drawing Scientific Claims from LLM Social Simulations Without Robustness Audits** — [arxiv_cy](https://arxiv.org/abs/2605.18890)
- **The Accessibility Capability Boundary: Operational Limits and Expansion Potential of AI-Generated Browser-Native Accessibility Systems** — [arxiv_cy](https://arxiv.org/abs/2605.19638)
- **ALSO: Adversarial Online Strategy Optimization for Social Agents** — [arxiv_cy](https://arxiv.org/abs/2605.15768)
- **Smooth Piecewise Cutting for Neural Operator to Handle Discontinuities and Sharp Transitions** — [arxiv_ml](https://arxiv.org/abs/2605.19823v1)
- **Probabilistic Multivariate Time Series Forecasting with Diffusion Copulas** — [arxiv_ml](https://arxiv.org/abs/2605.19685v1)
- **Increasing Missingness to Reduce Bias: Richardson-SGD with Missing Data** — [arxiv_ml](https://arxiv.org/abs/2605.19641v1)
- **Online Market Making and the Value of Observing the Order Book** — [arxiv_ml](https://arxiv.org/abs/2605.19584v1)
- **Automated Grading of Handwritten Mathematics Using Vision-Capable LLMs** — [arxiv_cy](https://arxiv.org/abs/2605.19043)
- **Can LLMs Emulate Human Belief Dynamics?** — [arxiv_cy](https://arxiv.org/abs/2605.18781)
- **A City-Scale Dataset of Traffic Flows, Travel Times, and Urban Context** — [arxiv_cy](https://arxiv.org/abs/2605.18782)
- **How Far Are We From True Auto-Research?** — [arxiv_cy](https://arxiv.org/abs/2605.19156)
- **Are Rationales Necessary and Sufficient? Tuning LLMs for Explainable Misinformation Detection** — [arxiv_cy](https://arxiv.org/abs/2605.19285)
- **Journeys of Parents with LGBTQ+ Children: How Trauma and Healing Reshape Identity and (Mis)Informating Practices** — [arxiv_cy](https://arxiv.org/abs/2605.20024)
- **Improved visual-information-driven model for crowd simulation and its modular application** — [arxiv_cy](https://arxiv.org/abs/2504.03758)
- **Semi-Parametric Bayesian Additive Regression Trees for Risk Prediction with High-Dimensional Epigenetic Signatures and Low-Dimensional Covariates** — [arxiv_ml](https://arxiv.org/abs/2605.20143v1)
- **FLUXtrapolation: A benchmark on extrapolating ecosystem fluxes** — [arxiv_ml](https://arxiv.org/abs/2605.19812v1)
- **Latent Laplace Diffusion for Irregular Multivariate Time Series** — [arxiv_ml](https://arxiv.org/abs/2605.19805v1)
- **Fast Spawn\&Prune (FS\&P): Global convergence of stochastic conic particle gradient descent via birth/death process** — [arxiv_ml](https://arxiv.org/abs/2605.19784v1)
- **Minimax Optimal Variance-Aware Regret Bounds for Multinomial Logistic MDPs** — [arxiv_ml](https://arxiv.org/abs/2605.19768v1)
- **CogScale: Scalable Benchmark for Sequence Processing** — [arxiv_ml](https://arxiv.org/abs/2605.19758v1)
- **Gaussian Approximation and Multiplier Bootstrap for Federated Linear Stochastic Approximation** — [arxiv_ml](https://arxiv.org/abs/2605.19629v1)
- **MiMuon: Mixed Muon Optimizer with Improved Generalization for Large Models** — [arxiv_ml](https://arxiv.org/abs/2605.19619v1)
- **Posterior Contraction of Lévy Adaptive B-spline Regression in Besov Spaces** — [arxiv_ml](https://arxiv.org/abs/2605.19610v1)
- **Density-Ratio Losses for Post-Hoc Learning to Defer** — [arxiv_ml](https://arxiv.org/abs/2605.19557v1)
- **8点1氪丨谷歌推出Gemini 3.5系列模型；DeepSeek回应用户“对话泄露”疑虑；全国存款十强城市出炉** — [36kr](https://36kr.com/p/3816885092910212?f=rss)
- **2026福布斯中国人工智能科技企业TOP 50发布，中关村科金入选** — [36kr](https://36kr.com/newsflashes/3817185914520710?f=rss)
- **圆周率智能发布 iMLite AI（悟境）端侧实时决策引擎** — [36kr](https://36kr.com/newsflashes/3817118508713092?f=rss)
- **地瓜机器人与千寻智能达成战略合作** — [36kr](https://36kr.com/newsflashes/3817109218575489?f=rss)
- **宜春就进一步加强锂资源矿山监督管理征求意见** — [36kr](https://36kr.com/newsflashes/3817121466680200?f=rss)
- **Seedance 2.1即将推出？接近字节跳动人士：不属实** — [36kr](https://36kr.com/newsflashes/3817085893788546?f=rss)
- **“贝塔无限”连续完成种子轮、种子+轮数亿元融资** — [36kr](https://36kr.com/newsflashes/3817084193866889?f=rss)
- **平头哥AI芯片真武M890首次亮相，性能提升至3倍** — [36kr](https://36kr.com/newsflashes/3817080294999168?f=rss)
- **长鑫科技更新招股书，碧桂园错失300亿** — [36kr](https://36kr.com/p/3817039204139908?f=rss)
- **理想新L9上市72小时：老车主复购占大头，仍需从“家庭”破圈** — [36kr](https://36kr.com/p/3709756082466949?f=rss)
- **做出百万台割草机器人后，未岚大陆CEO决定让自己变得“不重要”｜硬氪专访** — [36kr](https://36kr.com/p/3814411349581316?f=rss)
- **要做数字劳动力生产工厂，「未来式智能」完成Pre-A轮融资** — [36kr](https://36kr.com/p/3816909945029760?f=rss)
- **早期项目 | Chance AI获美图等数百万美元投资，用户数已达20万** — [36kr](https://36kr.com/p/3816947890471812?f=rss)
- **当“躺平”、Gap被歧视，我们该如何度过奥德赛时期？ | 职场极端气候 ②** — [36kr](https://36kr.com/p/3816045694098952?f=rss)
- **氪星晚报 ｜SpaceX即将成为马斯克旗下第二家上市公司；京东、洋河集团等在宿迁成立新动能股权投资基金，出资额10亿** — [36kr](https://36kr.com/p/3816109626138119?f=rss)
- **裸辞九个月，降薪跳槽，一个80后营销人如何“上岸甲方”？｜百万年薪系列013** — [36kr](https://36kr.com/p/3816036564147718?f=rss)
- **影石：重新定义性价比** — [36kr](https://36kr.com/p/3815841756028425?f=rss)
- **新加坡加码人工智能布局，英伟达将落地本地研发中心** — [36kr](https://36kr.com/newsflashes/3817119265457027?f=rss)
- **飞猪推出酒店商家智能助理** — [36kr](https://36kr.com/newsflashes/3817110991799169?f=rss)
- **平头哥真武系列GPU已累计出货超56万片** — [36kr](https://36kr.com/newsflashes/3817111570482304?f=rss)