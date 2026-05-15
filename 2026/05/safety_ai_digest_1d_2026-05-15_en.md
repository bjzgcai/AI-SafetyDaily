# AI Daily Digest [AI 安全] - 2026-05-15


# AI Safety Thematic Digest: 2026-05-15

## Highlights

Three academic developments stand out today for their potential to reshape safety evaluation and defense mechanisms. First, the introduction of **Privacy Auditing with Zero (0) Training Run** offers a critical post-hoc framework for auditing differential privacy parameters in deployed systems without requiring interventional access or retraining, addressing a major bottleneck in privacy compliance for foundation models. Second, **MetaBackdoor: Exploiting Positional Encoding as a Backdoor Attack Surface in LLMs** reveals a novel vulnerability where structural token position, rather than textual content, serves as a trigger, challenging existing content-based filtering assumptions. Third, **Talk is (Not) Cheap: A Taxonomy and Benchmark Coverage Audit for LLM Attacks** provides a rigorous external validation of current safety benchmarks, revealing significant gaps in collective threat coverage that undermine confidence in current alignment metrics.

## Adversarial Attacks & Robustness

The landscape of adversarial security is shifting from content-based manipulation to structural and environmental exploitation. A significant concern raised by **MetaBackdoor** is the exploitation of positional encoding in Transformer-based LLMs. Unlike traditional backdoors that rely on explicit textual triggers, this attack surface leverages the inherent positional information required by the architecture, rendering standard content filters ineffective. This finding necessitates a re-evaluation of how model inputs are sanitized, as it suggests that safety mechanisms must now account for structural metadata rather than just semantic content.

In parallel, defenses against prompt injections in autonomous systems are evolving. **WARD: Adversarially Robust Defense of Web Agents Against Prompt Injections** addresses the vulnerability of web agents to HTML or visual interface injections. While existing guard models struggle with generalization and latency, WARD proposes a robust defense architecture. However, the efficacy of such defenses is questioned by **One Step to the Side: Why Defenses Against Malicious Finetuning Fail Under Adaptive Adversaries**, which demonstrates that current robustness claims often rely on fixed attacks that do not account for adaptive adversaries. The authors survey 15 recent defenses and identify a shared weakness where mechanisms obscure or misdirect the model rather than fundamentally securing it. This contradiction highlights a critical gap: robustness against static threats does not guarantee resilience against adaptive fine-tuning attacks.

Furthermore, the scope of adversarial threats extends beyond text. **Systematic Discovery of Semantic Attacks in Online Map Construction through Conditional Diffusion** presents MIRAGE, a framework for discovering semantic attacks on autonomous vehicle mapping that bypass standard adversarial defenses by exploiting latent manifolds of real-world data. Similarly, **Backdoor Threats in Variational Quantum Circuits** surveys vulnerabilities in NISQ computing, showing that backdoor attacks can embed hidden malicious behaviors in quantum circuits. These works collectively suggest that as AI systems integrate into physical and quantum infrastructures, the attack surface expands to include environmental and hardware-level manipulations.

## Model Alignment & Safety Benchmarks

Alignment research is moving towards more dynamic and context-aware safety mechanisms. **EVA: Editing for Versatile Alignment against Jailbreaks** proposes editing models to reduce jailbreak vulnerabilities without the computational overhead of full safety fine-tuning. This contrasts with **LiSA: Lifelong Safety Adaptation via Conservative Policy Induction**, which focuses on guardrails that adapt to local privacy norms and organizational policies in real-time. While EVA targets static model weights, LiSA addresses the contextual nature of safety failures in deployed agents.

The reliability of these alignment efforts is scrutinized by **Talk is (Not) Cheap**, which audits six public benchmarks against a 507-leaf taxonomy of inference-time attacks. The study reveals that primary frameworks like HarmBench and InjecAgent suffer from incomplete coverage, meaning a model passing these benchmarks may still be vulnerable to untested attack vectors. This finding is corroborated by **The Great Pretender: A Stochasticity Problem in LLM Jailbreak**, which notes that methods claiming high attack success rates (ASR) often fail to deliver consistent results across different model instances due to stochasticity issues.

Geopolitical and cultural context further complicates alignment. **ROK-FORTRESS** introduces a bilingual, culturally adversarial National Security and Public Safety benchmark using the English-Korean language pair and U.S.-ROK geopolitical axis. This moves beyond simple translation-only benchmarks to test how language and geopolitical context interact, addressing the limitation of current multilingual safety assessments. Additionally, **RealICU** challenges existing medical benchmarks by introducing hindsight-annotated data, arguing that treating historical clinician actions as ground truth is insufficient for assessing true reasoning capabilities in high-stakes environments.

## Privacy Protection & Federated Learning

Privacy-preserving machine learning continues to face challenges in balancing utility with rigorous auditing. **Privacy Auditing with Zero (0) Training Run** is a significant methodological advance, allowing for empirical lower bounds on differential privacy parameters using fixed datasets in an observational regime. This is particularly relevant for large deployed systems where retraining is infeasible. Complementing this, **DisAgg: Distributed Aggregators for Efficient Secure Aggregation in Federated Learning** proposes a new protocol to reduce communication rounds and cryptographic overhead in federated settings, addressing the scalability issues of existing secure-aggregation schemes.

However, the limits of personalization in privacy are being tested. **Limits of Personalizing Differential Privacy Budgets** demonstrates that for mean estimation, full personalization offers limited gains compared to a simple thresholding operator for choosing the effective privacy budget. This suggests that complex personalization strategies may not always yield the expected privacy-utility trade-off improvements, urging a re-evaluation of budget allocation strategies in federated systems.

## Agent Security & Governance

As agents gain autonomy, authorization and governance mechanisms are becoming critical. **Do Coding Agents Understand Least-Privilege Authorization?** introduces AuthBench, a benchmark of 120 realistic terminal tasks, to study whether models can infer permission boundaries. The results indicate a need for explicit authorization frameworks, as agents often lack the inherent understanding of least-privilege principles. This is supported by the emergence of open-source tools like **secureagentics/Adrian**, which provides runtime security monitoring to catch malicious tool use and policy drift in real time.

The infrastructure for agentic modeling is also maturing. **Orchard** is an open-source framework for scalable agentic modeling, focusing on environment interaction and training rather than just orchestration. Similarly, **Nexus** offers a multi-agent framework for time series forecasting that integrates unstructured contextual data. These tools reflect a shift towards building robust agent ecosystems, yet they raise governance questions highlighted by **Beyond Individual Intelligence**, which surveys the risks of error propagation and failure attribution in multi-agent systems. The recent adoption of Model Context Protocol (MCP) servers, such as **JazzCashMCP** and **okx-agent-trade-kit**, further standardizes agent interactions but introduces new security surfaces that require auditing.

Industry news regarding the Musk vs. Altman trial and data center opposition underscores the growing tension between AI capability and governance. While legal proceedings focus on corporate control, public sentiment, as reflected in surveys regarding data center construction, indicates a strong preference for local oversight and data sovereignty. This aligns with policy discussions on establishing AI and data sovereignty in the age of autonomous systems, where enterprises must balance capability with control over proprietary data.

## Multimodal & Generative Safety

Generative models are facing increased scrutiny regarding their physical and visual fidelity. **Can Visual Mamba Improve AI-Generated Image Detection?** investigates whether newer architectures can better detect deepfakes, a critical concern given recent reports on deepfake pornography and identity theft. **Quantitative Video World Model Evaluation for Geometric-Consistency** introduces PDI-Bench to audit geometric coherence in generated videos, addressing the subjectivity of human judgment in evaluation.

In the realm of video generation, **Warp-as-History** and **RAVEN** propose methods for camera-controlled and real-time autoregressive video generation. While these improve generative capabilities, they also necessitate robust detection frameworks. **MemEye** evaluates multimodal agent memory from a visual-centric perspective, ensuring agents preserve visual evidence for later reasoning, which is crucial for accountability in long-term interactions.

## Looking Forward

Several theoretical questions remain unresolved. The efficacy of defenses against adaptive adversaries, as highlighted in **One Step to the Side**, suggests that current robustness claims are incomplete; future research must validate defenses against adversaries that evolve alongside the defense mechanisms. The intersection of quantum computing and security, explored in **Toward Covert Quantum Computing** and **Backdoor Threats in Variational Quantum Circuits**, requires a richer framework for covertness and security that accounts for multi-tenant quantum environments.

Furthermore, the validity of safety benchmarks remains a critical hypothesis awaiting validation. The gaps identified in **Talk is (Not) Cheap** and **The Great Pretender** suggest that current benchmarks may provide a false sense of security. Future work must focus on developing dynamic, coverage-agnostic evaluation methods that can adapt to novel attack vectors like the positional encoding backdoor. Finally, the integration of agents into critical infrastructure, from traffic networks to healthcare, requires rigorous testing of trust evolution and failure attribution, as seen in **Day-to-Day Traffic Network Modeling** and **Beyond Individual Intelligence**. The community must move beyond static alignment towards lifelong safety adaptation that accounts for contextual and geopolitical nuances.

---


## References

- **Privacy Auditing with Zero (0) Training Run** — [arxiv_cr](https://arxiv.org/abs/2605.14591v1)
- **XAI and Statistical Analysis for Reliable Intrusion Detection in the UAVIDS-2025 Dataset: From Tree to Hybrid and Tabular DNN Ensembles** — [arxiv_cr](https://arxiv.org/abs/2605.13922v1)
- **MetaBackdoor: Exploiting Positional Encoding as a Backdoor Attack Surface in LLMs** — [arxiv_cr](https://arxiv.org/abs/2605.15172v1)
- **Analyzing Codes of Conduct for Online Safety in Video Games at Scale** — [arxiv_cr](https://arxiv.org/abs/2605.15047v1)
- **WARD: Adversarially Robust Defense of Web Agents Against Prompt Injections** — [arxiv_cr](https://arxiv.org/abs/2605.15030v1)
- **Do Coding Agents Understand Least-Privilege Authorization?** — [arxiv_cr](https://arxiv.org/abs/2605.14859v1)
- **Can Visual Mamba Improve AI-Generated Image Detection? An In-Depth Investigation** — [arxiv_cr](https://arxiv.org/abs/2605.14799v1)
- **EVA: Editing for Versatile Alignment against Jailbreaks** — [arxiv_cr](https://arxiv.org/abs/2605.14750v1)
- **LiSA: Lifelong Safety Adaptation via Conservative Policy Induction** — [arxiv_cr](https://arxiv.org/abs/2605.14454v1)
- **The Great Pretender: A Stochasticity Problem in LLM Jailbreak** — [arxiv_cr](https://arxiv.org/abs/2605.14418v1)
- **Toward Covert Quantum Computing** — [arxiv_cr](https://arxiv.org/abs/2605.14325v1)
- **Day-to-Day Traffic Network Modeling under Route-Guidance Misinformation: Endogenous Trust and Resilience in CAV Environments** — [arxiv_cr](https://arxiv.org/abs/2605.14204v1)
- **ROK-FORTRESS: Measuring the Effect of Geopolitical Transcreation for National Security and Public Safety** — [arxiv_cr](https://arxiv.org/abs/2605.14152v1)
- **Backdoor Threats in Variational Quantum Circuits: Taxonomy, Attacks, and Defenses** — [arxiv_cr](https://arxiv.org/abs/2605.13796v1)
- **DisAgg: Distributed Aggregators for Efficient Secure Aggregation in Federated Learning** — [arxiv_cr](https://arxiv.org/abs/2605.13708v1)
- **Ideology Prediction of German Political Texts** — [huggingface_papers](https://arxiv.org/abs/2605.14352)
- **Limits of Personalizing Differential Privacy Budgets** — [arxiv_cr](https://arxiv.org/abs/2605.13503v1)
- **Talk is (Not) Cheap: A Taxonomy and Benchmark Coverage Audit for LLM Attacks** — [arxiv_cr](https://arxiv.org/abs/2605.15118v1)
- **One Step to the Side: Why Defenses Against Malicious Finetuning Fail Under Adaptive Adversaries** — [arxiv_cr](https://arxiv.org/abs/2605.14605v1)
- **Angel or Demon: Investigating the Plasticity Interventions' Impact on Backdoor Threats in Deep Reinforcement Learning** — [arxiv_cr](https://arxiv.org/abs/2605.14587v1)
- **Systematic Discovery of Semantic Attacks in Online Map Construction through Conditional Diffusion** — [arxiv_cr](https://arxiv.org/abs/2605.14396v1)
- **Warp-as-History: Generalizable Camera-Controlled Video Generation from One Training Video** — [huggingface_papers](https://arxiv.org/abs/2605.15182)
- **Learning to Build the Environment: Self-Evolving Reasoning RL via Verifiable Environment Synthesis** — [huggingface_papers](https://arxiv.org/abs/2605.14392)
- **Self-Distilled Agentic Reinforcement Learning** — [huggingface_papers](https://arxiv.org/abs/2605.15155)
- **Quantitative Video World Model Evaluation for Geometric-Consistency** — [huggingface_papers](https://arxiv.org/abs/2605.15185)
- **ATLAS: Agentic or Latent Visual Reasoning? One Word is Enough for Both** — [huggingface_papers](https://arxiv.org/abs/2605.15198)
- **RAVEN: Real-time Autoregressive Video Extrapolation with Consistency-model GRPO** — [huggingface_papers](https://arxiv.org/abs/2605.15190)
- **Topology-Preserving Neural Operator Learning via Hodge Decomposition** — [huggingface_papers](https://arxiv.org/abs/2605.13834)
- **EVA-Bench: A New End-to-end Framework for Evaluating Voice Agents** — [huggingface_papers](https://arxiv.org/abs/2605.13841)
- **RealICU: Do LLM Agents Understand Long-Context ICU Data? A Benchmark Beyond Behavior Imitation** — [huggingface_papers](https://arxiv.org/abs/2605.13542)
- **FrameSkip: Learning from Fewer but More Informative Frames in VLA Training** — [huggingface_papers](https://arxiv.org/abs/2605.13757)
- **Vividh-ASR: A Complexity-Tiered Benchmark and Optimization Dynamics for Robust Indic Speech Recognition** — [huggingface_papers](https://arxiv.org/abs/2605.13087)
- **F-GRPO: Factorized Group-Relative Policy Optimization for Unified Candidate Generation and Ranking** — [huggingface_papers](https://arxiv.org/abs/2605.12995)
- **VGGT-Edit: Feed-forward Native 3D Scene Editing with Residual Field Prediction** — [huggingface_papers](https://arxiv.org/abs/2605.15186)
- **Darwin Family: MRI-Trust-Weighted Evolutionary Merging for Training-Free Scaling of Language-Model Reasoning** — [huggingface_papers](https://arxiv.org/abs/2605.14386)
- **MemEye: A Visual-Centric Evaluation Framework for Multimodal Agent Memory** — [huggingface_papers](https://arxiv.org/abs/2605.15128)
- **Orchard: An Open-Source Agentic Modeling Framework** — [huggingface_papers](https://arxiv.org/abs/2605.15040)
- **Nexus : An Agentic Framework for Time Series Forecasting** — [huggingface_papers](https://arxiv.org/abs/2605.14389)
- **LLM-based Detection of Manipulative Political Narratives** — [huggingface_papers](https://arxiv.org/abs/2605.14354)
- **Beyond Individual Intelligence: Surveying Collaboration, Failure Attribution, and Self-Evolution in LLM-based Multi-Agent Systems** — [huggingface_papers](https://arxiv.org/abs/2605.14892)
- **Elon Musk’s SpaceXAI has been bleeding staff since its merger** — [techcrunch_ai](https://techcrunch.com/2026/05/14/elon-musks-spacexai-has-been-bleeding-staff-since-its-merger/)
- **Establishing AI and data sovereignty in the age of autonomous systems** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137168/establishing-ai-and-data-sovereignty-in-the-age-of-autonomous-systems/)
- **Closing time** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/931006/musk-v-altman-closing-arguments-analysis)
- **What happens when AI starts building itself?** — [techcrunch_ai](https://techcrunch.com/2026/05/14/what-happens-when-ai-starts-building-itself/)
- **OpenAI is reportedly preparing legal action against Apple; it wouldn’t be the first partner to feel burned** — [techcrunch_ai](https://techcrunch.com/2026/05/14/openai-is-reportedly-preparing-legal-action-against-apple-it-wouldnt-be-the-first-partner-to-feel-burned/)
- **Behold, the Elon Musk jackass trophy** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/930893/elon-musk-sam-altman-trial-ai-safety-jackass-statue)
- **OpenAI’s Codex is now in the ChatGPT mobile app** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/930763/openai-codex-chatgpt-ios-android-app-preview)
- **Microsoft starts canceling Claude Code licenses** — [theverge_ai](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad)
- **Use this map to find the data centers in your backyard** — [theverge_ai](https://www.theverge.com/policy/930629/data-center-policy-map-interactive)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **Americans do not want AI data centers in their backyards** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/930477/ai-data-centers-gallup-survey-70-percent-opposition)
- **Data readiness for agentic AI in financial services** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137034/data-readiness-for-agentic-ai-in-financial-services/)
- **The Download: deepfake porn’s stolen bodies and AI sharing private numbers** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137257/the-download-deepfake-porn-bodies-ai-exposing-phone-numbers/)
- **The Tesla Semi could be a big deal for electric trucking** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137197/tesla-semi-electric-trucking/)
- **You can make an app for that** — [theverge_ai](https://www.theverge.com/tech/928905/vibe-code-personal-software-revolution)
- **The shock of seeing your body used in deepfake porn** — [mit_tech_review](https://www.technologyreview.com/2026/05/14/1137161/ai-porn-nonconsensual-deepfakes-takedown-piracy-copyright/)
- **Who decides what AI tells you? Campbell Brown, once Meta’s news chief, has thoughts** — [techcrunch_ai](https://techcrunch.com/2026/05/13/who-decides-what-ai-tells-you-campbell-brown-once-metas-news-chief-has-thoughts/)
- **What the jury will actually decide in the case of Elon Musk vs. Sam Altman** — [techcrunch_ai](https://techcrunch.com/2026/05/14/what-the-jury-will-actually-decide-in-the-case-of-elon-musk-vs-sam-altman/)
- **OpenAI says Codex is coming to your phone** — [techcrunch_ai](https://techcrunch.com/2026/05/14/openai-says-codex-is-coming-to-your-phone/)
- **Clawdmeter turns your Claude Code usage stats into a tiny desktop dashboard** — [techcrunch_ai](https://techcrunch.com/2026/05/14/clawdmeter-turns-your-claude-code-usage-stats-into-a-tiny-desktop-dashboard/)
- **Cerebras raises $5.5B, then stock pops $108%, in the first huge tech IPO of 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/14/cerebras-raises-5-5b-kicking-off-2026s-ipo-season-with-a-bang/)
- **Khosla Ventures is betting $10M on Ian Crosby, whose first startup, Bench, imploded** — [techcrunch_ai](https://techcrunch.com/2026/05/14/khosla-ventures-is-betting-10m-on-ian-crosby-whose-last-startup-bench-imploded/)
- **Cisco cuts nearly 4,000 jobs to spend more on AI, reports ‘record quarterly revenue’** — [techcrunch_ai](https://techcrunch.com/2026/05/14/cisco-cuts-nearly-4000-jobs-to-spend-more-on-ai-reports-record-quarterly-revenue/)
- **Two weeks left: Startup Battlefield 200 applications close May 27** — [techcrunch_ai](https://techcrunch.com/2026/05/14/two-weeks-left-startup-battlefield-200-applications-close-may-27/)
- **Wirestock raises $23M to supply creative multimodal data to AI labs** — [techcrunch_ai](https://techcrunch.com/2026/05/14/wirestock-raises-23m-to-supply-multi-modal-data-to-ai-labs/)
- **Work with Codex from anywhere** — [openai](https://openai.com/index/work-with-codex-from-anywhere)
- **Clio’s $500M milestone arrives just as Anthropic ups the ante** — [techcrunch_ai](https://techcrunch.com/2026/05/13/clios-500m-milestone-arrives-just-as-anthropic-ups-the-ante/)
- **secureagentics/Adrian** — [github](https://github.com/secureagentics/Adrian)
- **simonlin1212/TradingAgents-astock** — [github](https://github.com/simonlin1212/TradingAgents-astock)
- **r0b0tlab/hermes-concurrent-agents** — [github](https://github.com/r0b0tlab/hermes-concurrent-agents)
- **DeepExperience/HyperEyes** — [github](https://github.com/DeepExperience/HyperEyes)
- **ldpGitHub/ai-app-bridge** — [github](https://github.com/ldpGitHub/ai-app-bridge)
- **TehreemArbab/JazzCashMCP** — [github](https://github.com/TehreemArbab/JazzCashMCP)
- **talentsache/aipointer** — [github](https://github.com/talentsache/aipointer)
- **johunsang/semble_rs** — [github](https://github.com/johunsang/semble_rs)
- **PlaceNL2026/okx-agent-trade-kit** — [github](https://github.com/PlaceNL2026/okx-agent-trade-kit)
- **ndcorder/outputguard** — [github](https://github.com/ndcorder/outputguard)
- **python-telegramBot/ai-auto-trading** — [github](https://github.com/python-telegramBot/ai-auto-trading)
- **cosmicstack-labs/mercury-agent-skills** — [github](https://github.com/cosmicstack-labs/mercury-agent-skills)
- **Isoform/yansu-skill** — [github](https://github.com/Isoform/yansu-skill)
- **sno-ai/llmix** — [github](https://github.com/sno-ai/llmix)
- **ab-613/OpenGravity** — [github](https://github.com/ab-613/OpenGravity)
- **mikesheehan54/Claude-Code-Design-AI** — [github](https://github.com/mikesheehan54/Claude-Code-Design-AI)
- **yaassin12/DeepSeek-V4-Pro-App** — [github](https://github.com/yaassin12/DeepSeek-V4-Pro-App)
- **yetone/native-feel-skill** — [github](https://github.com/yetone/native-feel-skill)
- **nexu-io/html-anything** — [github](https://github.com/nexu-io/html-anything)
- **zghhui/OmniNFT** — [github](https://github.com/zghhui/OmniNFT)
- **人手一个数据库，Kimi背后这套AI基建到底有多能扛？** — [qbitai](https://www.qbitai.com/2026/05/417731.html)
- **重生之我在AI时代当老板：让一群Agent互相PUA** — [qbitai](https://www.qbitai.com/2026/05/417816.html)
- **淘天金码奖落幕：20 名超级工程师诞生，推动 AI Native 实践** — [qbitai](https://www.qbitai.com/2026/05/417927.html)
- **国产GPU组了个开源局，把SGLang等核心开发者都摇来了！** — [qbitai](https://www.qbitai.com/2026/05/417791.html)
- **Robotaxi第一股又涨疯了** — [qbitai](https://www.qbitai.com/2026/05/417754.html)
- **腾讯开源 Agent 记忆技术方案，Token 消耗最高降低 61%** — [qbitai](https://www.qbitai.com/2026/05/417753.html)
- **阿里 AI 应用新进展：悟空开始逐步规模化放量** — [qbitai](https://www.qbitai.com/2026/05/417748.html)
- **田渊栋AI创业估值315亿，老黄苏妈都投了，姚班施天麟也是合伙人** — [qbitai](https://www.qbitai.com/2026/05/417468.html)
- **亚历山大王回应一切：LeCun、Manus，“我的父母都是中国人”** — [qbitai](https://www.qbitai.com/2026/05/417488.html)
- **36氪首发｜航天发动机核心部件厂商获投，国内唯一具备核心部件一站式制造能力的民营企业** — [36kr](https://36kr.com/p/3809936183860740?f=rss)
- **麦记牛奶谢永亮：2025年是唯一窗口期，糖水赛道胜负已定｜厚雪专访** — [36kr](https://36kr.com/p/3809931035844359?f=rss)
- **36氪首发 | 前大疆核心成员做消费级CNC，获美团、昆仑资本、奇绩创坛投资近亿元** — [36kr](https://36kr.com/p/3809919654403587?f=rss)
- **2026年上半年最火赛道：具身智能行业前4月融资超200笔，总规模超550亿元** — [36kr](https://36kr.com/p/3809911566704388?f=rss)
- **抢跑618，iPhone 17 Pro系列首次官方降价** — [36kr](https://36kr.com/newsflashes/3809908500225540?f=rss)
- **阿里巴巴等来收获期，外卖大战已无大波澜** — [36kr](https://36kr.com/p/3807527591058948?f=rss)
- **丰田提交申请，拟在美国得克萨斯州斥资20亿美元建厂** — [36kr](https://36kr.com/newsflashes/3809866940030720?f=rss)
- **独家对谈｜广告人小马宋的烟火与锋芒：非精英们的精英生存指南** — [36kr](https://36kr.com/p/3807543008698118?f=rss)
- **8点1氪丨周大福回应金饰又涨价；韩国一季度未成年人股票账户暴涨近十倍；张雪机车820RR暂停生产交付** — [36kr](https://36kr.com/p/3809785128869641?f=rss)
- **氪星晚报｜千里智驾CEO辟谣离职传闻；三星在计划罢工前夕启动减产** — [36kr](https://36kr.com/p/3809007831375621?f=rss)
- **腾讯要懂得花钱** — [36kr](https://36kr.com/p/3808999399497221?f=rss)
- **三大指数全部翻红** — [36kr](https://36kr.com/newsflashes/3809972223532550?f=rss)
- **Anthropic同意以9000亿美元估值开展融资轮的条款** — [36kr](https://36kr.com/newsflashes/3809965649157639?f=rss)