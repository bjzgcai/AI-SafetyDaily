# AI Daily Digest [AI 安全] - 2026-05-13


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-05-13

## Highlights

Three significant academic developments dominate today's safety landscape, shifting focus from static model evaluation to dynamic agent ecosystems and rigorous privacy guarantees. First, **Persona-Conditioned Adversarial Prompting** introduces a methodology for red-teaming that conditions adversarial search on diverse attacker personas, revealing that automated discovery often misses realistic attack slices. Second, the emergence of **SkillSafetyBench** alongside findings on **SKILL.md** semantic supply-chain attacks highlights a critical vulnerability: the modularity of agent skills creates new attack surfaces that bypass traditional safety filters. Third, theoretical advances in **Unlearning with Asymmetric Sources** propose a mechanism to mitigate the utility-privacy trade-off, while empirical work on **Reconstruction of Personally Identifiable Information from Supervised Finetuned Models** confirms that SFT datasets remain a primary vector for PII leakage.

## Adversarial Attacks & Robustness

The frontier of adversarial research is moving beyond static prompt injection toward more context-aware and infrastructure-dependent threats. **Persona-Conditioned Adversarial Prompting** addresses the limitation of current automated red-teaming, which often discovers narrow attack slices. By conditioning the search on diverse personas such as doctors or malicious actors, the authors report discovering transferable jailbreaks across different contexts on GPT-OSS 120B. This contrasts with traditional benchmarks that assume a generic attacker profile. Complementing this, **IPI-proxy** targets a specific deployment scenario: web-browsing agents. The authors present an open-source toolkit designed to red-team against indirect prompt injection (IPI) where adversaries embed hidden instructions in HTML pages served by whitelisted domains. While **Persona-Conditioned Adversarial Prompting** focuses on the semantic intent of the attacker, **IPI-proxy** focuses on the retrieval pipeline, suggesting that defense mechanisms must address both the generation and the retrieval layers of agentic workflows.

In response to these evolving threats, **Safety Context Injection** proposes inference-time safety alignment via static filtering and agentic analysis. The authors note that black-box settings prevent weight modification, necessitating intervention at inference time. However, they identify a "thinking--output gap" where models appear cautious during reasoning but generate harmful outputs, a phenomenon that simpler filters often miss. This work underscores the latency trade-off inherent in deep safety analysis. While **Persona-Conditioned Adversarial Prompting** exposes the depth of the vulnerability, **Safety Context Injection** attempts to mitigate it without retraining, though the authors caution that long adversarial contexts can dilute local cues relied upon by filters.

## Agent Security & Governance

A cohesive narrative is emerging regarding the security of agentic systems, specifically concerning the "skill" layer. **SkillSafetyBench** is a runnable benchmark evaluating agent safety under skill-facing attack surfaces. The authors report that even when user requests are benign, task-relevant skill materials or local artifacts can steer an agent toward unsafe actions. This finding is corroborated by **Under the Hood of SKILL.md**, which studies semantic supply-chain attacks on AI agent skill registries. The authors demonstrate that natural-language metadata and instructions in SKILL.md files can affect which skills are admitted and loaded, allowing for attacks across discovery and selection stages.

To address these risks, **Behavioral Integrity Verification for AI Agent Skills** formalizes the problem as a typed set comparison between declared and actual capabilities. The framework instantiates this comparison by pairing deterministic code analysis with LLM-assisted capability extraction. This approach moves beyond prompt safety to verify the artifact itself. In the open-source ecosystem, **mercury-agent-skills** offers a curated registry of reusable skills, while **outputguard** provides tools to validate and repair LLM structured outputs, addressing the structural integrity of agent communication.

Governance structures are also under scrutiny. **Attacks and Mitigations for Distributed Governance of Agentic AI under Byzantine Adversaries** critiques state-of-the-art solutions like SAGA, which assume a logically centralized point of trust. The authors argue that a malicious Provider can undermine security, suggesting a need for decentralized accountability. This aligns with industry observations where companies like Anthropic warn investors against secondary platforms offering access to shares, highlighting the governance complexity surrounding AI infrastructure ownership.

## Privacy Protection & Federated Learning

Privacy research continues to grapple with the tension between model utility and data protection. **Unlearning with Asymmetric Sources** introduces Asymmetric Langevin Unlearning (ALU), a framework using public data to mitigate privacy costs. The authors prove that public data injection suppresses the unlearning cost by a factor of $O(1/n_{\mathrm{pub}}^2)$, challenging the hard ceiling faced by noise-based certified machine unlearning. This theoretical advance is critical for large-scale deletion requests. Conversely, **Reconstruction of Personally Identifiable Information from Supervised Finetuned Models** provides empirical evidence of risk. The authors construct multi-turn, user-centric Q&A datasets in sensitive domains and find that SFT models can reconstruct PII, raising concerns for medical and legal applications.

In the realm of tabular data, **FERMI** exploits relations for membership inference against tabular diffusion models. The authors highlight that existing attacks ignore the multi-relational structure of real sensitive data. By leveraging auxiliary information from parent tables, FERMI assesses privacy risks more accurately than single-table assumptions. For authentication, **Deanonymizable Scoped Linkable Ring Signatures** introduces a scheme integrating scoped linkability with decentralized accountability, addressing the lack of trust requirements in existing ring signatures for use-cases like consent management.

Additionally, **PrivacySIM** evaluates LLM simulation of user privacy behavior. The authors benchmark LLM simulation against ground-truth responses of 1,000 users, finding that core persona attributes may not sufficiently drive individual-level privacy behavior simulation. This suggests that privacy-preserving agents may require more than just persona conditioning to accurately reflect human privacy decisions.

## Alignment, Training, and Optimization

The efficacy of post-training methods remains a subject of intense debate. **The Many Faces of On-Policy Distillation** and **Unmasking On-Policy Distillation** present a comprehensive empirical study of when on-policy distillation (OPD) works and when it fails. The authors find that OPD on mathematical reasoning is highly sensitive to specific conditions, with recent studies reporting instability and degradation. While some results show promise in system prompt internalization, the authors caution that the optimal choice of teacher model and context varies from token to token, often obscured by aggregate performance metrics.

In terms of inference efficiency, **GridProbe** proposes a training-free posterior-probing inference paradigm for long-video VLMs, scoring evidence in answer space to mitigate the bottleneck of monolithic forward passes. Similarly, **TMAS** scales test-time compute via multi-agent synergy, organizing inference across multiple trajectories to balance exploration and reuse. **SlimSpec** addresses the computational bottleneck of speculative decoding by introducing a low-rank draft LM-head, reducing the projection cost to a large vocabulary.

For reasoning paradigms, **Teaching Language Models to Think in Code** proposes ThinC, a framework where code serves as the reasoner rather than a tool invoked by natural language. This addresses limitations in tool-integrated reasoning where code often acts as a post-hoc verifier. Meanwhile, **AutoLLMResearch** explores training research agents for automating LLM experiment configuration, aiming to optimize high-cost LLM experiments where repeated trial and error is not feasible.

## Industry & Policy Developments

In the policy domain, **Medicare’s new payment model** creates a mechanism for paying AI agents that monitor patients between visits, potentially incentivizing the deployment of health-monitoring agents. However, this raises questions about liability and safety assurance. In the corporate sphere, **Anthropic warns investors against secondary platforms** offering access to its shares, emphasizing strict control over equity transfer. Regarding security auditing, **360 reported an OpenClaw ecosystem security report** noting the discovery of 23 independent security vulnerabilities, marking a shift toward automated audit stages for AI agents. While industry news often highlights hardware advancements such as humanoid robots, the technical focus remains on the underlying safety infrastructure required to support such deployments.

## Looking Forward

Several theoretical questions remain unresolved. The efficacy of **Unlearning with Asymmetric Sources** depends heavily on the availability and quality of public data; future work must validate whether this suppression of unlearning cost holds across diverse model architectures and deletion scales. In agent security, the **Behavioral Integrity Verification** framework requires standardization; currently, the taxonomy bridging code, instructions, and metadata is not universal, hindering cross-platform verification. Finally, the "thinking--output gap" identified in **Safety Context Injection** suggests that current inference-time defenses may be insufficient for models with complex reasoning chains. Future research must determine whether static filtering can be augmented with dynamic, low-latency analysis without compromising the model's reasoning capabilities. The community must also address the supply-chain risks highlighted by **SKILL.md** attacks, as the modularity of agent skills appears to be a permanent architectural feature rather than a temporary design choice.

---


## References

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