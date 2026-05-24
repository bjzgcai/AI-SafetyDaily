# AI Daily Digest [AI 安全] - 2026-05-24


# AI Safety Daily Digest: 2026-05-24

## Highlights

Today's research showcases a maturing focus on fundamental limits and practical robustness in AI safety. A significant theoretical breakthrough connects **differential privacy** and **randomized smoothing** to provide the first provable robustness certificate against backdoor attacks, a major step toward securing machine learning pipelines end-to-end. In interpretability, a new benchmark exposing **cross-modal redundancy** in Vision-Language Models (VLMs) challenges the validity of prevailing explainability evaluation methods, while a foundational **impossibility theorem** on feature attribution under collinearity formally delineates a core challenge for trustworthy AI. These works collectively advance the field by establishing clearer boundaries and more rigorous methodologies for safety-critical systems.

---

## Academic Themes

### Adversarial Attacks & Robustness

The day's most notable contribution in this domain is a work bridging two major robustness paradigms: **"Provable Robustness against Backdoor Attacks via the Primal-Dual Perspective on Differential Privacy."** The authors connect randomized smoothing—previously used for certifying robustness against evasion and poisoning—to the dual view of differential privacy via *privacy profiles*. This allows them to construct a single robustness certificate that accounts for joint perturbations at both training and test time, a previously elusive goal for backdoor attacks. The method provides a formal, unified guarantee, moving beyond empirical defenses to a principled, provable security framework.

Complementing this is a study on evasion in the latent space: **"Latent-space Attacks for Refusal Evasion in Language Models."** This work reframes the empirical success of activation-steering methods (like ablating a "refusal direction") as a formal *evasion attack against linear probes* in the model's latent space. By providing a principled account of these transformations, the paper offers a more systematic understanding of how safety alignment can be circumvented internally, highlighting a vulnerability that certified defenses like the one above must eventually address.

### Model Alignment & Interpretability

Interpretability research today reveals critical flaws in how we evaluate explainability and establishes new theoretical boundaries. The paper **"Measuring Cross-Modal Synergy: A Benchmark for VLM Explainability"** delivers a sharp critique of the status quo. The authors demonstrate that unimodal perturbation metrics can be fundamentally misleading because VLMs often rely on **cross-modal redundancy**—using text priors alone to answer visual queries. Their new benchmark forces evaluation to measure genuine *cross-modal reasoning*, exposing a collapse in current methods that penalize faithful explainers. This calls for a paradigm shift in how we assess multimodal model understanding.

In a complementary theoretical vein, **"The Attribution Impossibility"** proves a profound limitation: no feature ranking can be simultaneously **faithful, stable, and complete** when features are collinear. The work rigorously quantifies this for four model classes and machine-verifies it using Lean 4. It resolves the issue by proposing *DASH*, an ensemble method that provides stable rankings by explicitly reporting ties, thus mapping the complete design space for attribution methods and offering a practical path forward.

### Privacy Protection & Federated Learning

A key challenge in privacy-preserving ML is transitioning from theoretical frameworks to real-world deployment. The paper **"Embedding-Based Federated Learning with Runtime Governance for Iron Deficiency Prediction"** directly addresses this gap. By deploying a system across two distinct clinical environments (AUMC and NHSBT), the authors confront practical hurdles like differing data distributions and institutional constraints. Their use of frozen domain-specific embeddings and runtime governance mechanisms represents a serious attempt to build FL systems that are not just private but also *operational* in heterogeneous, high-stakes settings.

On the frontier of data deletion rights, **"DualOptim+: Bridging Shared and Decoupled Optimizer States for Better Machine Unlearning in Large Language Models"** proposes a novel optimization framework. It introduces a *base state* for shared representations and *delta states* for objective-specific residuals, allowing the optimizer to adaptively manage the conflict between forgetting and retaining gradients. The quantized variant, DualOptim+ 8bit, further addresses the memory overhead concern, aiming to make machine unlearning more practical for large models.

### Safety Benchmarks & Evaluation

Benchmarking efforts are evolving to target more nuanced and realistic failure modes. **"Benchmarking and Improving Monitors for Out-Of-Distribution Alignment Failure in LLMs"** introduces the MOOD benchmark to stress-test monitoring pipelines. Recognizing that true OOD failures are rare in off-the-shelf models, the authors cleverly design a *restricted training set* to create OOD scenarios, enabling a systematic study of whether current monitors can detect novel misalignment.

Meanwhile, **"AttuneBench: A Conversation-Based Benchmark for LLM Emotional Intelligence"** moves beyond synthetic prompts to evaluate emotional understanding in genuine, multi-turn conversations. This is crucial for safety and alignment, as emotional misalignment can lead to harmful or ineffective interactions. By grounding evaluation in real dialogues, AttuneBench provides a more authentic measure of a model's ability to perceive and respond to human emotional states.

### Agent Security & Governance

As LLM-based agents become more autonomous, controlling their behavior through their interface with the world is a growing research focus. **"Harnesses for Inference-Time Alignment over Execution Trajectories"** provides a formal lens on agent harness design, separating it into *task decomposition* and *guided execution*. It reveals the non-linear trade-off: increased decomposition or guidance can sometimes degrade final performance, highlighting that harness engineering is a delicate optimization problem, not just a scaling exercise.

Building on this, **"Adapting the Interface, Not the Model: Runtime Harness Adaptation for Deterministic LLM Agents"** proposes *Life-Harness*, a system that evolves the agent's interface at runtime without modifying model weights. This is particularly valuable for deterministic, rule-governed domains where failures often stem from model-environment mismatches rather than model capability limits. Together, these works suggest that the future of agent safety may lie significantly in the sophisticated control of the model's runtime environment.

## Open-Source Contributions

Notable security-focused tools emerged today. The **control-layer** project offers a production-grade pipeline for LLM input validation, schema enforcement, and audit logging, acting as a critical safety middleware. The **terraform-review-agent** leverages a multi-agent system to automatically audit infrastructure-as-code for security and cost issues, integrating safety checks directly into the development lifecycle.

## Looking Forward

Today's digest highlights several unresolved theoretical questions. The certified robustness framework for backdoor attacks opens the door to a key hypothesis: *can similar primal-dual DP connections be forged to certify robustness against a broader class of data poisoning attacks?* The attribution impossibility theorem raises the question of how to design *stably faithfutable* methods for non-linear models beyond the studied classes. Furthermore, the demonstration of cross-modal redundancy in VLMs begs the question: *how pervasive are these unimodal shortcuts in other multimodal architectures, and can they be systematically detected and mitigated during training?* Finally, the focus on agent harnesses prompts inquiry into whether formal methods can be developed to *verify the safety properties of an entire agent-harness system* before deployment.

---


## References

- **Provable Robustness against Backdoor Attacks via the Primal-Dual Perspective on Differential Privacy** — [arxiv_lg](https://arxiv.org/abs/2605.21780)
- **Embedding-Based Federated Learning with Runtime Governance for Iron Deficiency Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.21563)
- **Measuring Cross-Modal Synergy: A Benchmark for VLM Explainability** — [arxiv_ai](https://arxiv.org/abs/2605.22168)
- **The Attribution Impossibility: No Feature Ranking Is Faithful, Stable, and Complete Under Collinearity** — [arxiv_lg](https://arxiv.org/abs/2605.21492)
- **Leveraging Self-Paced Curriculum Learning for Enhanced Modality Balance in Multimodal Conversational Emotion Recognition** — [arxiv_lg](https://arxiv.org/abs/2605.21565)
- **PEARL: Unbiased Percentile Estimation via Contrastive Learning for Industrial-Scale Livestream Recommendation** — [arxiv_lg](https://arxiv.org/abs/2605.21752)
- **AOP-Wiki EMOD 3.0: Data Model Expansions and Content Evaluation Framework for Using Agentic AI to Improve Integration between AOPs and New Approach Methodologies (NAMs)** — [arxiv_ai](https://arxiv.org/abs/2605.21645)
- **Investigating Concept Alignment Using Implausible Category Members** — [arxiv_ai](https://arxiv.org/abs/2605.21683)
- **A Causal Argumentation Method for Explainability of Machine Learning Models** — [arxiv_ai](https://arxiv.org/abs/2605.21758)
- **What Counts as AI Sycophancy? A Taxonomy and Expert Survey of a Fragmented Construct** — [arxiv_ai](https://arxiv.org/abs/2605.21778)
- **Implicit Safety Alignment from Crowd Preferences** — [arxiv_ai](https://arxiv.org/abs/2605.21822)
- **ECPO: Evidence-Coupled Policy Optimization for Evidence-Certified Candidate Ranking** — [arxiv_ai](https://arxiv.org/abs/2605.21993)
- **Teaching Language Models to Forecast Research Success Through Comparative Idea Evaluation** — [arxiv_lg](https://arxiv.org/abs/2605.21491)
- **Harnesses for Inference-Time Alignment over Execution Trajectories** — [arxiv_lg](https://arxiv.org/abs/2605.21516)
- **A Reproducible Log-Driven AutoML Framework for Interpretable Pipeline Optimization in Healthcare Risk Prediction** — [arxiv_lg](https://arxiv.org/abs/2605.21528)
- **DualOptim+: Bridging Shared and Decoupled Optimizer States for Better Machine Unlearning in Large Language Models** — [arxiv_lg](https://arxiv.org/abs/2605.21539)
- **Tabular foundation models for robust calibration of near-infrared chemical sensing data** — [arxiv_lg](https://arxiv.org/abs/2605.21544)
- **PeakFocus: Bridging Peak Localization and Intensity Regression via a Unified Multi-Scale Framework for Electricity Load Forecasting** — [arxiv_lg](https://arxiv.org/abs/2605.21550)
- **Expectation Consistency Loss: Rethink Confidence Calibration under Covariate Shift** — [arxiv_lg](https://arxiv.org/abs/2605.21552)
- **Beyond Single Slot: Joint Optimization for Multi-Slot Guaranteed Display Advertising** — [arxiv_lg](https://arxiv.org/abs/2605.21556)
- **From Parameters to Data: A Task-Parameter-Guided Fine-Tuning Pipeline for Efficient LLM Alignment** — [arxiv_lg](https://arxiv.org/abs/2605.21558)
- **Objective-Induced Bias and Search Dynamics in Multiobjective Unsupervised Feature Selection** — [arxiv_lg](https://arxiv.org/abs/2605.21561)
- **ConTact: Contact-First Antibody CDR Design via Explicit Interface Reasoning** — [arxiv_lg](https://arxiv.org/abs/2605.21600)
- **When Are Teacher Tokens Reliable? Position-Weighted On-Policy Self-Distillation for Reasoning** — [arxiv_lg](https://arxiv.org/abs/2605.21606)
- **$\textit{BlockFormer}$ : Transformer-based inference from interaction maps** — [arxiv_lg](https://arxiv.org/abs/2605.21617)
- **Alike Parts: A Feature-Informed Approach to Local and Global Prototype Explanations** — [arxiv_lg](https://arxiv.org/abs/2605.21646)
- **Dropout Universality: Scaling Laws and Optimal Scheduling at the Edge-of-Chaos** — [arxiv_lg](https://arxiv.org/abs/2605.21648)
- **Benchmarking and Improving Monitors for Out-Of-Distribution Alignment Failure in LLMs** — [arxiv_ai](https://arxiv.org/abs/2605.21602)
- **Latent-space Attacks for Refusal Evasion in Language Models** — [arxiv_ai](https://arxiv.org/abs/2605.21706)
- **AttuneBench: A Conversation-Based Benchmark for LLM Emotional Intelligence** — [arxiv_ai](https://arxiv.org/abs/2605.21739)
- **Who Uses AI? Platforms, Workforce, and AI Exposure** — [arxiv_ai](https://arxiv.org/abs/2605.21743)
- **Trace2Skill: Verifier-Guided Skill Evolution for Long-Context EDA Agents** — [arxiv_ai](https://arxiv.org/abs/2605.21810)
- **Planning in the LLM Era: Building for Reliability and Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.21902)
- **AI-Enabled Serious Games: Integrating Intelligence and Adaptivity in Training Systems** — [arxiv_ai](https://arxiv.org/abs/2605.21962)
- **A Camera-Cooperative ISAC Framework for Multimodal Non-Cooperative UAVs Sensing** — [arxiv_ai](https://arxiv.org/abs/2605.22090)
- **ArborKV: Structure-Aware KV Cache Management for Scaling Tree-based LLM Reasoning** — [arxiv_ai](https://arxiv.org/abs/2605.22106)
- **Efficient Agentic Reasoning Through Self-Regulated Simulative Planning** — [arxiv_ai](https://arxiv.org/abs/2605.22138)
- **Adapting the Interface, Not the Model: Runtime Harness Adaptation for Deterministic LLM Agents** — [arxiv_ai](https://arxiv.org/abs/2605.22166)
- **LLM-Metrics: Measuring Research Impact Through Large Language Model Memory** — [arxiv_ai](https://arxiv.org/abs/2605.22176)
- **CLORE: Content-Level Optimization for Reasoning Efficiency** — [arxiv_ai](https://arxiv.org/abs/2605.22211)
- **Elon Musk has given up on solar power (on Earth)** — [techcrunch_ai](https://techcrunch.com/2026/05/23/elon-musk-has-given-up-on-solar-power-on-earth/)
- **Google’s new anything-to-anything AI model is wild** — [theverge_ai](https://www.theverge.com/tech/936507/gemini-omni-hands-on-deepfake-ai-video)
- **Ferrari is using IBM’s AI to create F1 superfans** — [techcrunch_ai](https://techcrunch.com/2026/05/23/ferrari-is-using-ai-to-create-f1-superfans/)
- **AbhishekK130804/Claude-Mythos-AI-Anthropic-App** — [github](https://github.com/AbhishekK130804/Claude-Mythos-AI-Anthropic-App)
- **5bv57zcm44-max/NOXUS-AI-Open-WhatsApp** — [github](https://github.com/5bv57zcm44-max/NOXUS-AI-Open-WhatsApp)
- **Emmimal/control-layer** — [github](https://github.com/Emmimal/control-layer)
- **infiniumtek/terraform-review-agent** — [github](https://github.com/infiniumtek/terraform-review-agent)
- **ayush016/android-lead-agent-skills** — [github](https://github.com/ayush016/android-lead-agent-skills)
- **wanshuiyin/ARIS-in-AI-Offer** — [github](https://github.com/wanshuiyin/ARIS-in-AI-Offer)
- **open-gsd/gsd-pi** — [github](https://github.com/open-gsd/gsd-pi)
- **kingbootoshi/directional-prompting** — [github](https://github.com/kingbootoshi/directional-prompting)
- **mikaeldengale-cloud/Deepseek-v4-Pro-App** — [github](https://github.com/mikaeldengale-cloud/Deepseek-v4-Pro-App)
- **SalhaNabil/CloakBrowser** — [github](https://github.com/SalhaNabil/CloakBrowser)
- **h4ckf0r0day/awesome-ai-web-scraping** — [github](https://github.com/h4ckf0r0day/awesome-ai-web-scraping)
- **xuanlinAI/overmind** — [github](https://github.com/xuanlinAI/overmind)
- **leiting-eric/DailyBrief** — [github](https://github.com/leiting-eric/DailyBrief)
- **kingbootoshi/goal-ledger** — [github](https://github.com/kingbootoshi/goal-ledger)
- **op7418/ai-desk-card** — [github](https://github.com/op7418/ai-desk-card)
- **hasanyilmaz/operon** — [github](https://github.com/hasanyilmaz/operon)
- **zhongweiv/hermes-edu-skills** — [github](https://github.com/zhongweiv/hermes-edu-skills)
- **c4pt0r/pie** — [github](https://github.com/c4pt0r/pie)
- **nkzw-tech/cloudsail** — [github](https://github.com/nkzw-tech/cloudsail)
- **Tartarus-AI/tartarusai-cli** — [github](https://github.com/Tartarus-AI/tartarusai-cli)
- **“五类人AI替代不了，企业做第二名最稳妥” | 昆仑万维方汉@AIGC2026** — [qbitai](https://www.qbitai.com/2026/05/423202.html)
- **OpenAI大神教你如何榨干Codex** — [qbitai](https://www.qbitai.com/2026/05/423179.html)
- **DeepSeek V4价格打骨折，宁王京东网易抢着入场，梁文锋：目标是AGI** — [qbitai](https://www.qbitai.com/2026/05/423162.html)
- **中证投服提名独立董事已扩展至14家A股公司，最高年薪达25万元** — [36kr](https://36kr.com/newsflashes/3822733352390786?f=rss)
- **华泰证券：看好2026年起交换芯片在AI驱动下开启二次成长** — [36kr](https://36kr.com/newsflashes/3822612389941383?f=rss)
- **“天韵相机”项目负责人：香港航天员操作港研仪器意义重大** — [36kr](https://36kr.com/newsflashes/3822609989734531?f=rss)
- **圆桌对话：下一个杀手级AI产品，会出现在哪个赛道？| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3821714896408713?f=rss)
- **老虎国际：未有“拒不配合监管”等言论，2023年起已全停内地开户营销** — [36kr](https://36kr.com/newsflashes/3821606327111813?f=rss)
- **圆桌对话：当AI进入产业前线：未来最稀缺的AI人才，会是谁？| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3821542483857801?f=rss)
- **圆桌对话：人才特种兵：“AI原生人才”与“产业老炮”的共生手册| 2026AI Partner·北京亦庄AI+产业大会** — [36kr](https://36kr.com/p/3821533415985283?f=rss)
- **对话王小川：离开通用人工智能的主干道之后** — [36kr](https://36kr.com/p/3821521291038856?f=rss)
- **圆桌对话：AI浓度与转化率：数字体验的实战增长法则** — [36kr](https://36kr.com/p/3821519307591811?f=rss)
- **康斯特回应是否与SpaceX扩大合作，称单一用户影响有限** — [36kr](https://36kr.com/newsflashes/3821498732302723?f=rss)
- **36氪首发 | 北大项目孵化，国内首家原生机器人“大脑芯片”企业获数亿元融资** — [36kr](https://36kr.com/p/3821371042877575?f=rss)
- **屈臣氏计划下半年赴中国香港、伦敦两地上市** — [36kr](https://36kr.com/newsflashes/3821499521060998?f=rss)