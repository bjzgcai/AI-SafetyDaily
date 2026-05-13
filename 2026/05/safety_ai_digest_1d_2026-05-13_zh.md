# AI 日报 [AI 安全] - 2026-05-13


# AI 安全与治理每日综述：2026 年 5 月 13 日

## Highlights

今日学术与产业界在 AI 安全领域呈现出从单一模型防御向复杂系统治理转变的显著趋势。在对抗攻击与红队测试方面，**Persona-Conditioned Adversarial Prompting** 提出了一种基于多身份视角的自动化红队测试方法，揭示了传统攻击探测在真实场景覆盖面上的不足，为生成更丰富的防御数据集提供了新路径。在智能体安全评估领域，**SkillSafetyBench** 的发布填补了技能中介（Skill-mediated）攻击面的评估空白，指出即使无害的用户请求也可能通过技能材料诱导智能体执行危险操作。此外，联邦学习中的后门防御研究取得了实质性进展，**FedSurrogate** 通过结合双向梯度对齐与层自适应异常检测，有效降低了非独立同分布数据下的误报率。产业层面，OpenAI 内部治理结构的法律证词披露了创始团队控制权与组织使命之间的潜在冲突，为 AI 治理的监管框架提供了新的现实注脚。

## 对抗攻击与鲁棒性

随着大语言模型（LLM）在开放环境中的部署，对抗攻击的边界正从直接的提示词注入向更隐蔽的上下文与供应链攻击转移。传统的自动化红队测试往往局限于狭窄的攻击切片，而 **Persona-Conditioned Adversarial Prompting** 通过引入医生、学生及恶意行为者等多重攻击者身份，并行执行条件化搜索，成功发现了跨上下文的可迁移性漏洞。这种方法不仅提升了攻击发现的广度，还通过自动元数据追踪生成了高质量的防御微调数据。与此同时，针对 Web 浏览智能体的间接提示注入（IPI）威胁日益严峻，**IPI-proxy** 作为一个开源红队测试工具，专门针对受白名单限制的域名环境，模拟了嵌入在 HTML 页面中的隐藏指令，弥补了现有基准测试无法触及真实受限环境的缺陷。

供应链安全已成为对抗研究的新焦点，**Under the Hood of SKILL.md** 深入分析了智能体技能注册表中的语义供应链攻击风险。研究发现，攻击者可以通过操纵自然语言元数据和指令，影响技能的准入、展示与加载逻辑，这种攻击发生在技能生命周期早期，难以通过传统的运行时监控发现。与之相呼应，**PhishSigma++** 在邮件检测领域提出了基于类型化实体关系的检测方法，指出攻击者即便修改了表面文本，其功能意图仍会约束实体关系，这为对抗性样本的不变性信号提取提供了新思路。这些工作共同表明，对抗防御必须从模型内部参数扩展到外部交互环境与数据供应链的全链路监控。

## 模型对齐与可解释性

在模型对齐与推理控制方面，研究重心正从训练后微调（Post-training）向推理时干预（Inference-time Intervention）延伸。**Safety Context Injection** 针对大型推理模型（LRMs）在部署时难以修改权重的限制，提出了一种通过静态过滤与智能体分析来实现推理时安全对齐的方法。该方法旨在解决深层安全分析引入的延迟问题，以及长上下文对局部安全线索的稀释效应，试图弥合模型“思考”与“输出”之间的安全鸿沟。然而，训练过程中的对齐机制仍面临稳定性挑战，**The Many Faces of On-Policy Distillation** 与 **Unmasking On-Policy Distillation** 这两项工作对在线策略蒸馏（OPD）进行了全面的实证研究。作者指出，OPD 在数学推理任务中高度敏感，且存在不稳定性与性能退化风险，其有效性取决于教师模型的选择与上下文监督信号的具体配置，这提示我们在追求密集监督信号时需警惕优化路径的坍塌。

此外，激活控制（Activation Steering）技术也在不断演进。**Prompt-Activation Duality** 识别了 KV 缓存污染作为状态对话中激活控制失效的关键模式，即局部扰动被存储并重复使用导致累积的连贯性下降。为此，研究者提出了门控裁剪注意力 Delta 控制（GCAD），通过提取系统提示贡献并应用令牌级门控来缓解这一问题。在推理范式上，**Teaching Language Models to Think in Code** 提出了一种名为 ThinC 的框架，将代码本身作为推理器而非自然语言的工具，这种范式转变可能从根本上改变模型处理复杂逻辑任务时的可解释性与安全性边界。

## 隐私保护与联邦学习

隐私保护研究在联邦学习与差分隐私的交叉领域取得了重要进展。**FedSurrogate** 针对联邦学习中恶意客户端注入后门的行为，提出了一种结合双向梯度对齐过滤与层自适应异常检测的防御方案。现有防御在非独立同分布（non-IID）数据下往往面临高误报率，导致模型精度下降，而 FedSurrogate 通过选择性聚类与层关键性分析，在识别恶意客户端的同时保留了良性客户端的贡献。在模型遗忘（Unlearning）领域，**Unlearning with Asymmetric Sources** 引入了非对称源遗忘框架，利用公共数据来缓解基于噪声的认证遗忘对模型效用的破坏。作者证明，公共数据的注入可以将遗忘成本降低 $O(1/n_{\mathrm{pub}}^2)$ 因子，这为在大规模删除请求下平衡隐私与效用提供了理论依据。

针对生成式模型的隐私风险，**FERMI** 揭示了表格扩散模型在成员推断攻击下的脆弱性。现有攻击通常假设单表设置，忽略了真实敏感数据的多关系结构，而 FERMI 利用辅助信息从相关表中推断目标表成员的隐私风险。同时，**Reconstruction of Personally Identifiable Information from Supervised Finetuned Models** 首次系统研究了监督微调（SFT）模型中个人身份信息（PII）的重构问题。通过构建医疗与法律领域的多轮问答数据集，研究证实了 SFT 模型可能泄露训练数据中的敏感用户信息，这为微调阶段的数据清洗与隐私审计提出了紧迫要求。

## Agent 安全与治理

智能体（Agent）的模块化能力扩展引入了新的安全治理挑战。**SkillSafetyBench** 作为一个可运行的基准，评估了智能体在技能中介攻击面下的安全性，包含 155 个对抗性案例，揭示了任务相关材料如何引导智能体走向不安全行为。针对技能本身的完整性验证，**Behavioral Integrity Verification for AI Agent Skills** 形式化了行为完整性验证（BIV）问题，通过类型化集合比较来验证声明能力与实际能力的一致性，结合了确定性代码分析与 LLM 辅助的能力提取。在治理架构方面，**Attacks and Mitigations for Distributed Governance of Agentic AI under Byzantine Adversaries** 指出，现有的 SAGA 方案假设逻辑集中信任点，容易受到恶意提供者（Provider）的偏离协议攻击，因此需要构建去中心化的治理机制以应对拜占庭对手。

知识管理的可靠性也是智能体安全的关键一环，**DeepRefine** 提出了一种基于强化学习的智能体编译知识精炼框架，旨在解决外部知识库中的不完整、错误与冗余问题，防止缺陷在迭代使用中累积。此外，**No More, No Less: Task Alignment in Terminal Agents** 探讨了终端智能体在环境指令遵循与忽略之间的对齐挑战，指出现有基准无法捕捉智能体在相关线索与误导性指令间进行精准判断的能力。这些工作共同指向一个核心问题：随着智能体自主性的增强，如何确保其技能来源可信、行为符合预期且知识准确，是构建高可靠性智能体系统的先决条件。

## 安全工具与开源生态

开源社区在安全工具与框架的开发上持续活跃，为上述研究提供了落地验证的基础。**MemPrivacy** 是一个面向边缘云智能体的隐私保护个性化记忆管理框架，旨在平衡记忆存储与隐私泄露风险。**llmix** 则提供了一个生产级的 LLM 调用层，支持模型热切换、缓存、重试及熔断机制，增强了智能体基础设施的鲁棒性。**outputguard** 专注于验证与修复 LLM 的结构化输出，针对常见的 JSON 格式错误提供了多种修复策略。在视觉与仿真领域，**LychSim** 构建了一个基于 Unreal Engine 5 的可控交互式仿真框架，降低了视觉研究中的仿真技术门槛，有助于在安全受控环境中进行分布外（OOD）评估。

产业界的安全审计也在推进，360 发布的 OpenClaw 生态安全报告指出 AI 智能体风险已进入自动化审计阶段，累计发现 23 个独立安全漏洞。尽管部分媒体报道如宇树科技发布载人机甲或百度搭子 DuMate 的推出带有浓厚的营销色彩，但其中涉及的具身智能与长程任务执行能力确实对物理安全与隐私保护提出了新的验证需求。对于此类产品，独立的安全评估与压力测试仍是验证其实际安全性的必要环节，而非仅依赖厂商宣称的功能指标。

## Looking Forward

尽管上述工作在特定领域取得了突破，但 AI 安全领域仍面临若干未解决的理论问题与待验证假设。首先，模型遗忘（Unlearning）与效用之间的权衡理论尚未完全收敛，**Unlearning with Asymmetric Sources** 提出的公共数据辅助方法在实际大规模系统中的泛化能力仍需进一步验证。其次，智能体技能供应链的安全标准尚属空白，**Under the Hood of SKILL.md** 揭示的语义攻击风险需要建立类似软件供应链安全（SBOM）的标准化审计流程。最后，推理时安全对齐（Inference-time Safety Alignment）的延迟与准确性平衡问题，在复杂长上下文场景下仍缺乏高效的解决方案。未来的研究需重点关注去中心化治理机制的鲁棒性，以及如何在保持智能体自主性的同时，建立可信赖的技能与知识来源验证体系。

---


## 参考来源

- **Persona-Conditioned Adversarial Prompting: Multi-Identity Red-Teaming for Adversarial Discovery and Mitigation** — [arxiv_cr](https://arxiv.org/abs/2605.11730v1)
- **FedSurrogate: Backdoor Defense in Federated Learning via Layer Criticality and Surrogate Replacement** — [arxiv_cr](https://arxiv.org/abs/2605.11122v1)
- **SkillSafetyBench: Evaluating Agent Safety under Skill-Facing Attack Surfaces** — [arxiv_cr](https://arxiv.org/abs/2605.12015v1)
- **Safety Context Injection: Inference-Time Safety Alignment via Static Filtering and Agentic Analysis** — [arxiv_cr](https://arxiv.org/abs/2605.11664v1)
- **Under the Hood of SKILL.md: Semantic Supply-chain Attacks on AI Agent Skill Registry** — [arxiv_cr](https://arxiv.org/abs/2605.11418v1)
- **Unlearning with Asymmetric Sources: Improved Unlearning-Utility Trade-off with Public Data** — [arxiv_cr](https://arxiv.org/abs/2605.11170v1)
- **The Many Faces of On-Policy Distillation: Pitfalls, Mechanisms, and Fixes** — [huggingface_papers](https://arxiv.org/abs/2605.11182)
- **IPI-proxy: An Intercepting Proxy for Red-Teaming Web-Browsing AI Agents Against Indirect Prompt Injection** — [arxiv_cr](https://arxiv.org/abs/2605.11868v1)
- **FERMI: Exploiting Relations for Membership Inference Against Tabular Diffusion Models** — [arxiv_cr](https://arxiv.org/abs/2605.11527v1)
- **Engineering Robustness into Personal Agents with the AI Workflow Store** — [arxiv_cr](https://arxiv.org/abs/2605.10907v2)
- **LychSim: A Controllable and Interactive Simulation Framework for Vision Research** — [huggingface_papers](https://arxiv.org/abs/2605.12449)
- **Unmasking On-Policy Distillation: Where It Helps, Where It Hurts, and Why** — [huggingface_papers](https://arxiv.org/abs/2605.10889)
- **Injecting Distributional Awareness into MLLMs via Reinforcement Learning for Deep Imbalanced Regression** — [huggingface_papers](https://arxiv.org/abs/2605.01402)
- **Attacks and Mitigations for Distributed Governance of Agentic AI under Byzantine Adversaries** — [arxiv_cr](https://arxiv.org/abs/2605.12364v1)
- **Reconstruction of Personally Identifiable Information from Supervised Finetuned Models** — [arxiv_cr](https://arxiv.org/abs/2605.12264v1)
- **No More, No Less: Task Alignment in Terminal Agents** — [arxiv_cr](https://arxiv.org/abs/2605.12233v1)
- **PrivacySIM: Evaluating LLM Simulation of User Privacy Behavior** — [arxiv_cr](https://arxiv.org/abs/2605.12147v1)
- **The Deepfakes We Missed: We Built Detectors for a Threat That Didn't Arrive** — [arxiv_cr](https://arxiv.org/abs/2605.12075v1)
- **A microservices-based endpoint monitoring platform with predictive NLP models for real-time security and hate-speech risk alerting** — [arxiv_cr](https://arxiv.org/abs/2605.11997v1)
- **Behavioral Integrity Verification for AI Agent Skills** — [arxiv_cr](https://arxiv.org/abs/2605.11770v1)
- **Deanonymizable Scoped Linkable Ring Signatures** — [arxiv_cr](https://arxiv.org/abs/2605.11715v1)
- **HySecTwin: A Knowledge-Driven Digital Twin Framework Augmented with Hybrid Reasoning for Cyber-Physical Systems** — [arxiv_cr](https://arxiv.org/abs/2605.11682v1)
- **Every Bit, Everywhere, All at Once: A Binomial Multibit LLM Watermark** — [arxiv_cr](https://arxiv.org/abs/2605.11653v1)
- **PhishSigma++: Malicious Email Detection with Typed Entity Relations** — [arxiv_cr](https://arxiv.org/abs/2605.11619v1)
- **AutoLLMResearch: Training Research Agents for Automating LLM Experiment Configuration -- Learning from Cheap, Optimizing Expensive** — [huggingface_papers](https://arxiv.org/abs/2605.11518)
- **MoCam: Unified Novel View Synthesis via Structured Denoising Dynamics** — [huggingface_papers](https://arxiv.org/abs/2605.12119)
- **RubricEM: Meta-RL with Rubric-guided Policy Decomposition beyond Verifiable Rewards** — [huggingface_papers](https://arxiv.org/abs/2605.10899)
- **GridProbe: Posterior-Probing for Adaptive Test-Time Compute in Long-Video VLMs** — [huggingface_papers](https://arxiv.org/abs/2605.10762)
- **Can Muon Fine-tune Adam-Pretrained Models?** — [huggingface_papers](https://arxiv.org/abs/2605.10468)
- **δ-mem: Efficient Online Memory for Large Language Models** — [huggingface_papers](https://arxiv.org/abs/2605.12357)
- **CausalCine: Real-Time Autoregressive Generation for Multi-Shot Video Narratives** — [huggingface_papers](https://arxiv.org/abs/2605.12496)
- **Teaching Language Models to Think in Code** — [huggingface_papers](https://arxiv.org/abs/2605.07237)
- **PlantMarkerBench: A Multi-Species Benchmark for Evidence-Grounded Plant Marker Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.10032)
- **DeepRefine: Agent-Compiled Knowledge Refinement via Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.10488)
- **Rethinking Agentic Search with Pi-Serini: Is Lexical Retrieval Sufficient?** — [huggingface_papers](https://arxiv.org/abs/2605.10848)
- **Prompt-Activation Duality: Improving Activation Steering via Attention-Level Interventions** — [huggingface_papers](https://arxiv.org/abs/2605.10664)
- **Key-Value Means** — [huggingface_papers](https://arxiv.org/abs/2605.09877)
- **ELF: Embedded Language Flows** — [huggingface_papers](https://arxiv.org/abs/2605.10938)
- **TMAS: Scaling Test-Time Compute via Multi-Agent Synergy** — [huggingface_papers](https://arxiv.org/abs/2605.10344)
- **SlimSpec: Low-Rank Draft LM-Head for Accelerated Speculative Decoding** — [huggingface_papers](https://arxiv.org/abs/2605.10453)
- **Medicare’s new payment model is built for AI, and most of the tech world has no idea** — [techcrunch_ai](https://techcrunch.com/2026/05/12/medicares-new-payment-model-is-built-for-ai-and-most-of-the-tech-world-has-no-idea/)
- **Musk mulled handing OpenAI to his children, Altman testifies** — [techcrunch_ai](https://techcrunch.com/2026/05/12/musk-mulled-handing-openai-to-his-children-altman-testifies/)
- **Anthropic warns investors against secondary platforms offering access to its shares** — [techcrunch_ai](https://techcrunch.com/2026/05/12/anthropic-warns-investors-against-secondary-platforms-offering-access-to-its-shares/)
- **Report: Google and SpaceX in talks to put data centers into orbit** — [techcrunch_ai](https://techcrunch.com/2026/05/12/report-google-and-spacex-in-talks-to-put-data-centers-into-orbit/)
- **Everything Google announced at its Android Show, from Googlebooks to vibe-coded widgets** — [techcrunch_ai](https://techcrunch.com/2026/05/12/everything-google-announced-at-its-android-show-from-googlebooks-to-vibe-coded-widgets/)
- **The AI legal services industry is heating up — Anthropic is getting in on the action** — [techcrunch_ai](https://techcrunch.com/2026/05/12/the-ai-legal-services-industry-is-heating-up-anthropic-is-getting-in-on-the-action/)
- **Google’s ‘Create My Widget’ feature will let you vibe-code your own widgets** — [techcrunch_ai](https://techcrunch.com/2026/05/12/googles-create-my-widget-feature-will-let-you-vibe-code-your-own-widgets/)
- **Threads tests a Meta AI integration that works similarly to Grok** — [techcrunch_ai](https://techcrunch.com/2026/05/12/threads-tests-a-meta-ai-integration-that-works-similarly-to-grok/)
- **World Models: 10 Things That Matter in AI Right Now** — [mit_tech_review](https://www.technologyreview.com/2026/05/12/1137134/world-models-10-things-that-matter-in-ai-right-now/)
- **The Download: a Nobel winner on AI, and the case for fixing everything** — [mit_tech_review](https://www.technologyreview.com/2026/05/12/1137103/the-download-nobel-winner-ai-maintenance-of-everything/)
- **Thinking Machines wants to build an AI that actually listens while it talks** — [techcrunch_ai](https://techcrunch.com/2026/05/11/thinking-machines-wants-to-build-an-ai-that-actually-listens-while-it-talks/)
- **Google adds Gemini-powered dictation to Gboard, which could be bad news for dictation startups** — [techcrunch_ai](https://techcrunch.com/2026/05/12/google-adds-gemini-powered-dictation-to-gboard-which-could-be-bad-news-for-dictation-startups/)
- **Google brings agentic AI and vibe-coded widgets to Android** — [techcrunch_ai](https://techcrunch.com/2026/05/12/google-brings-agentic-ai-and-vibe-coded-widgets-to-android/)
- **How finance teams use Codex** — [openai](https://openai.com/academy/how-finance-teams-use-codex)
- **Dessn raises $6M for its production-focused design tool** — [techcrunch_ai](https://techcrunch.com/2026/05/12/dessn-raises-6m-for-its-production-focused-design-tool/)
- **AI voice startup Vapi hits $500M valuation after winning Amazon Ring over 40 rivals** — [techcrunch_ai](https://techcrunch.com/2026/05/12/vapi-hits-500m-valuation-as-amazon-ring-chose-its-ai-platform-over-40-rivals/)
- **MemTensor/MemPrivacy** — [github](https://github.com/MemTensor/MemPrivacy)
- **YoungZ365/SOD** — [github](https://github.com/YoungZ365/SOD)
- **ldpGitHub/ai-app-bridge** — [github](https://github.com/ldpGitHub/ai-app-bridge)
- **sno-ai/llmix** — [github](https://github.com/sno-ai/llmix)
- **AlexWortega/ai-peer-review-skill** — [github](https://github.com/AlexWortega/ai-peer-review-skill)
- **DeepExperience/HyperEyes** — [github](https://github.com/DeepExperience/HyperEyes)
- **TehreemArbab/JazzCashMCP** — [github](https://github.com/TehreemArbab/JazzCashMCP)
- **ndcorder/outputguard** — [github](https://github.com/ndcorder/outputguard)
- **cosmicstack-labs/mercury-agent-skills** — [github](https://github.com/cosmicstack-labs/mercury-agent-skills)
- **PaperGuru-AI/PaperGuru-Benchmark** — [github](https://github.com/PaperGuru-AI/PaperGuru-Benchmark)
- **ab-613/OpenGravity** — [github](https://github.com/ab-613/OpenGravity)
- **yaassin12/DeepSeek-V4-Pro-App** — [github](https://github.com/yaassin12/DeepSeek-V4-Pro-App)
- **HJCheng0602/paperwise** — [github](https://github.com/HJCheng0602/paperwise)
- **EricXu20266/llm-proxy** — [github](https://github.com/EricXu20266/llm-proxy)
- **manhai934/novel-harness** — [github](https://github.com/manhai934/novel-harness)
- **amix/dunk** — [github](https://github.com/amix/dunk)
- **kittimasak/thai-token-optimizer** — [github](https://github.com/kittimasak/thai-token-optimizer)
- **craig7351/bookshell** — [github](https://github.com/craig7351/bookshell)
- **NikiforovAll/pi-kanban** — [github](https://github.com/NikiforovAll/pi-kanban)
- **TsingShui/ida-agent-bridge** — [github](https://github.com/TsingShui/ida-agent-bridge)
- **何恺明首个语言模型：105M参数，不走GPT自回归老路** — [qbitai](https://www.qbitai.com/2026/05/416628.html)
- **原来Ilya还有70亿美元OpenAI股权** — [qbitai](https://www.qbitai.com/2026/05/416597.html)
- **商汤善惠烧卖购机器人小店上海“开业”，让机器人真正落地线下零售** — [qbitai](https://www.qbitai.com/2026/05/416590.html)
- **360发布OpenClaw生态安全报告：AI智能体风险进入自动化审计阶段** — [qbitai](https://www.qbitai.com/2026/05/416582.html)
- **AI第一金主黄仁勋：日均花掉20亿** — [qbitai](https://www.qbitai.com/2026/05/416540.html)
- **龙虾退烧后，荣耀给它造了一个宇宙** — [qbitai](https://www.qbitai.com/2026/05/416081.html)
- **Markdown要凉…卡帕西也站HTML了** — [qbitai](https://www.qbitai.com/2026/05/416339.html)
- **估值200亿美元！可灵AI被曝剥离快手单独融资** — [qbitai](https://www.qbitai.com/2026/05/416056.html)
- **OpenClaw低调更新重磅版本，龙虾长手长脚了** — [qbitai](https://www.qbitai.com/2026/05/416034.html)
- **加拿大丰业银行：预计2027年全球铜市场将出现35万吨的缺口** — [36kr](https://36kr.com/newsflashes/3807094309920518?f=rss)
- **“芯驰科技”完成近1亿美金C轮融资** — [36kr](https://36kr.com/newsflashes/3807090766241284?f=rss)
- **李彦宏：“自我进化”包含智能体、人类个体、企业组织的自我进化** — [36kr](https://36kr.com/newsflashes/3807072758734345?f=rss)
- **宇树科技已注册多款机器人商标** — [36kr](https://36kr.com/newsflashes/3807070566211328?f=rss)
- **36氪专访 | 安克创新eufy Make负责人：众筹超4000万美金后，还在红海寻找缝隙** — [36kr](https://36kr.com/p/3806507139390984?f=rss)
- **36氪首发 | 清华系光计算芯片企业完成数千万天使轮融资，瞄准全波光计算架构** — [36kr](https://36kr.com/p/3807043342475009?f=rss)
- **深耕“具身智能+建筑大模型”底座，重构万亿建筑业，「方石机器人」完成近亿元A轮融资 | 36氪首发** — [36kr](https://36kr.com/p/3807039782116865?f=rss)
- **国金证券：煤炭二季度业绩有望超预期，底部配置机会显现** — [36kr](https://36kr.com/newsflashes/3807001886301702?f=rss)
- **8点1氪丨宇树发布载人变形机甲，定价390万起；微信确认不会开发已读、访客功能；国内航线燃油附加费将再上调** — [36kr](https://36kr.com/p/3806970999955201?f=rss)
- **氪星晚报 ｜宇树科技发布载人机甲，投资人回应；京东：第一季度营收3157亿元，日本恩格尔系数创1980年以来最高水平同比增长4.9%** — [36kr](https://36kr.com/p/3806196073242112?f=rss)
- **不用再找了，AI落地最全的实战打法，都在亦庄这场大会里** — [36kr](https://36kr.com/p/3806179759496711?f=rss)
- **Walulu：用六个月撕开一条新赛道** — [36kr](https://36kr.com/p/3805761383751427?f=rss)
- **百度搭子DuMate正式亮相** — [36kr](https://36kr.com/newsflashes/3807097353805321?f=rss)
- **恒指开盘涨0.08%，恒生科技指数跌0.3%** — [36kr](https://36kr.com/newsflashes/3807041287003911?f=rss)
- **两市融资余额增加168.81亿元** — [36kr](https://36kr.com/newsflashes/3807007054585609?f=rss)