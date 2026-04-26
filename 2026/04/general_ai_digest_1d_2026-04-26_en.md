# AI Daily Digest [通用智能] - 2026-04-26


# Daily Thematic Digest: April 26, 2026

## Highlights

The most significant developments this week center on the maturation of agent economies, critical safety incidents, and the expanding availability of frontier models in emerging markets. **Anthropic created a test marketplace for agent-on-agent commerce**, a novel experiment where AI agents represented both buyers and sellers, striking real deals for real goods and money. This move signals a shift from theoretical agent orchestration to tangible economic interactions, though the company frames it as a controlled experiment rather than a commercial product launch. Simultaneously, **OpenAI CEO apologizes to Tumbler Ridge community**, marking a rare public admission of failure regarding safety protocols and law enforcement communication following a mass shooting incident. This event underscores the growing scrutiny on AI safety governance beyond technical alignment. Finally, the **DeepSeek-V4** ecosystem continues to expand, with reports indicating its availability on the National Supercomputing Internet and Baidu Qianfan platform, offering enterprise users and developers access to its million-token context window at competitive rates.

## Industry News & Big Events

The geopolitical and regulatory landscape for AI continues to fracture along lines of sovereignty and infrastructure control. In a move to counter American dominance, **Cohere is merging with Aleph Alpha**, a German startup, with support from the Schwarz Group. The companies intend to offer a sovereign alternative to enterprises, a strategy that aligns with broader European efforts to maintain data independence. Meanwhile, policy shifts in the United States are accelerating infrastructure deployment; **Maine’s governor vetoes data center moratorium**, rejecting legislation that would have imposed the country’s first statewide pause on new construction until late 2027. This decision prioritizes compute availability over local environmental concerns, reflecting the intense demand for AI infrastructure.

In the hardware sector, **Apple under Ternus** is reportedly signaling a return to hardware-centric strategies, with incoming CEO John Ternus emphasizing devices over services. This contrasts with the software-heavy focus of recent years. In China, the automotive and chip sectors are aggressively integrating AI. Reports from **36kr** indicate that **Huawei released ADS 5**, reinforcing a world model route for autonomous driving with significant investment. Additionally, **DeepSeek-V4** is being integrated into various platforms, including the **National Supercomputing Internet**, which offers free dialogue services to researchers. While **36kr** often repackages PR material, the widespread availability of DeepSeek-V4 across major Chinese cloud providers suggests a competitive pressure to democratize access to high-context models. However, claims regarding specific performance metrics or "world-first" technologies, such as those surrounding **Hikvision Robotics** or **Yuanrong Qixing**, should be treated as industry announcements rather than independently verified benchmarks.

## Agent & Tool Ecosystem

The agent ecosystem is moving beyond simple tool invocation toward more complex, reliable, and economically viable architectures. A critical bottleneck identified in recent research is the **Model Context Protocol (MCP) Tax**, where stateless, eager schema injection imposes a hidden overhead of 10k to 60k tokens per turn. To address this, **Tool Attention Is All You Need** introduces dynamic tool gating and lazy schema loading, aiming to eliminate this payload and preserve context utilization for reasoning. This technical optimization is vital for scaling multi-server deployments where token budgets are a recurring operational cost.

Reliability in GUI automation remains a primary challenge, particularly regarding early stopping and repetitive loops. **VLAA-GUI** proposes a modular framework built around three integrated components that guide the system on when to Stop, Recover, and Search. It enforces UI-observable success criteria at every finish step, addressing the tendency of agents to prematurely declare success without verifiable evidence. On the economic side, the emergence of a "skill economy" is creating new attack surfaces. **Black-Box Skill Stealing Attack from Proprietary LLM Agents** demonstrates how adversaries can interact with public agents to extract hidden proprietary skills, threatening the value proposition of specialized agent marketplaces.

The GitHub ecosystem reflects a surge in local and specialized agent frameworks. Projects like **ovo-local-llm** enable private, on-device coding agents on Apple Silicon, while **kimi-K2-6** positions itself as an autonomous software factory. These tools suggest a trend toward decentralized, privacy-first agent execution, reducing reliance on centralized cloud APIs. However, the proliferation of "skills" and "agents" also necessitates better governance, as seen in the **MCP Pitfall Lab**, which exposes developer pitfalls in tool server security under multi-vector attacks.

## Safety Assessment & Incidents

Security research this week highlights the sophistication of adversarial attacks and the need for rigorous auditing in enterprise settings. **Transient Turn Injection** exposes stateless multi-turn vulnerabilities by distributing adversarial intent across isolated interactions, bypassing conventional moderation that relies on single-turn context. This technique leverages automated attacker agents to iteratively test and evade policy enforcement in both commercial and open-source models. Similarly, **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers** presents a complete framework where triggers are embedded in natural text styles, addressing previous shortcomings regarding naturalness and payload injection reliability.

In the enterprise domain, **CI-Work** benchmarks contextual integrity, revealing that privacy failures are prevalent in enterprise LLM agents, with violation rates ranging from 15.8% to higher figures depending on the model. This suggests that even frontier models struggle to withhold sensitive context while conveying essential content in dense retrieval settings. Furthermore, **CrossCommitVuln-Bench** introduces a dataset of multi-commit Python vulnerabilities invisible to per-commit static analysis, highlighting that 87% of these vulnerabilities evade detection when analyzed individually. This underscores the limitations of current static analysis tools in complex software evolution.

The OpenAI incident in Tumbler Ridge serves as a stark reminder of the real-world consequences of safety failures. While the company claims to have apologized, the incident highlights the difficulty of aligning AI safety systems with external threat detection mechanisms. In parallel, **CSC: Turning the Adversary's Poison against Itself** offers a defense mechanism that analyzes backdoor attack dynamics during training, revealing that poisoned samples form isolated clusters that can be targeted. These findings collectively point to a security landscape where attacks are becoming more subtle and defenses must evolve from static filtering to dynamic, training-time analysis.

## Academic Research Frontiers

Research into reasoning and multimodal capabilities continues to challenge the limits of current architectures. **Process Supervision via Verbal Critique Improves Reasoning in Large Language Models** introduces a training-free framework that uses structured natural-language critique to guide iterative generate-critique-refine loops. This method yields significant improvements on benchmarks like GPQA Diamond and AIME 2025, suggesting that external verbal supervision is a viable axis for inference-time scaling. Complementing this, **Language as a Latent Variable for Reasoning Optimization** hypothesizes that non-English responses sometimes outperform English on reasoning tasks, suggesting language functions as a latent variable that structurally modulates internal inference pathways.

In the realm of vision and multimodal learning, **When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs** uses the HalluScope benchmark to analyze factors inducing hallucinations. The analysis indicates that hallucinations largely stem from prompt dominance rather than vision backbone limitations alone. Meanwhile, **Symbolic Grounding Reveals Representational Bottlenecks in Abstract Visual Reasoning** compares end-to-end VLMs with LLMs given symbolic inputs, reformulating the problem to isolate reasoning from representation. These studies suggest that current VLMs may struggle with abstract concepts not because of visual processing, but due to a lack of symbolic grounding.

Efficiency and theory are also gaining traction. **GiVA: Gradient-Informed Bases for Vector-Based Adaptation** introduces a gradient-based initialization strategy for vector-based adaptation, achieving training times comparable to LoRA while maintaining extreme parameter efficiency. **Decoupled DiLoCo for Resilient Distributed Pre-training** evolves the DiLoCo framework to break the lock-step coupling of SPMD paradigms, reducing vulnerability to hardware stalls. Finally, **There Will Be a Scientific Theory of Deep Learning** argues that a theory of deep learning is emerging, characterizing properties of training processes and hidden representations, pulling together strands of research into solvable idealized settings and tractable limits.

## Looking Forward

The trajectory of AI development in 2026 points toward three critical areas. First, the **economy of agents** will likely become a primary battleground, with experiments like Anthropic's marketplace testing the viability of machine-to-machine commerce. This will necessitate robust frameworks for skill verification and economic security to prevent exploitation. Second, **safety auditing** must evolve from static benchmarks to dynamic, context-aware evaluations. The prevalence of vulnerabilities like Transient Turn Injection and Contextual Integrity failures suggests that current safety measures are insufficient for complex, multi-turn workflows. Third, the **theory of deep learning** is moving from empirical observation to formal characterization, which may eventually guide the design of more efficient and reliable architectures. As models become more integrated into critical infrastructure, the distinction between technical capability and operational safety will become increasingly difficult to maintain without rigorous, independent verification.

---


## References

- **Nemobot Games: Crafting Strategic AI Gaming Agents for Interactive Learning with Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21896v1)
- **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21860v1)
- **Tool Attention Is All You Need: Dynamic Tool Gating and Lazy Schema Loading for Eliminating the MCP/Tools Tax in Scalable Agentic Workflows** — [arxiv_ai](https://arxiv.org/abs/2604.21816v1)
- **A Metamorphic Testing Approach to Diagnosing Memorization in LLM-Based Program Repair** — [arxiv_ai](https://arxiv.org/abs/2604.21579v1)
- **AgenticQwen: Training Small Agentic Language Models with Dual Data Flywheels for Industrial-Scale Tool Use** — [arxiv_cl](https://arxiv.org/abs/2604.21590v1)
- **OptiVerse: A Comprehensive Benchmark towards Optimization Problem Solving** — [arxiv_cl](https://arxiv.org/abs/2604.21510v1)
- **Symbolic Grounding Reveals Representational Bottlenecks in Abstract Visual Reasoning** — [arxiv_cl](https://arxiv.org/abs/2604.21346v1)
- **Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers** — [arxiv_ai](https://arxiv.org/abs/2604.21700v1)
- **GS-Quant: Granular Semantic and Generative Structural Quantization for Knowledge Graph Completion** — [arxiv_ai](https://arxiv.org/abs/2604.21649v1)
- **Job Skill Extraction via LLM-Centric Multi-Module Framework** — [arxiv_cl](https://arxiv.org/abs/2604.21525v1)
- **Generalizing Numerical Reasoning in Table Data through Operation Sketches and Self-Supervised Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21495v1)
- **CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents** — [arxiv_cr](https://arxiv.org/abs/2604.21308v1)
- **When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21911v1)
- **Process Supervision via Verbal Critique Improves Reasoning in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21611v1)
- **CoFEE: Reasoning Control for LLM-Based Feature Discovery** — [arxiv_ai](https://arxiv.org/abs/2604.21584v1)
- **Language as a Latent Variable for Reasoning Optimization** — [arxiv_cl](https://arxiv.org/abs/2604.21593v1)
- **Reasoning Primitives in Hybrid and Non-Hybrid LLMs** — [arxiv_cl](https://arxiv.org/abs/2604.21454v1)
- **CARE: Counselor-Aligned Response Engine for Online Mental-Health Support** — [arxiv_cl](https://arxiv.org/abs/2604.21352v1)
- **A Sociotechnical, Practitioner-Centered Approach to Technology Adoption in Cybersecurity Operations: An LLM Case** — [arxiv_cr](https://arxiv.org/abs/2604.21679v1)
- **Seeing Fast and Slow: Learning the Flow of Time in Videos** — [arxiv_ai](https://arxiv.org/abs/2604.21931v1)
- **From Research Question to Scientific Workflow: Leveraging Agentic AI for Science Automation** — [arxiv_ai](https://arxiv.org/abs/2604.21910v1)
- **GiVA: Gradient-Informed Bases for Vector-Based Adaptation** — [arxiv_ai](https://arxiv.org/abs/2604.21901v1)
- **TingIS: Real-time Risk Event Discovery from Noisy Customer Incidents at Enterprise Scale** — [arxiv_ai](https://arxiv.org/abs/2604.21889v1)
- **A Multimodal Text- and Graph-Based Approach for Open-Domain Event Extraction from Documents** — [arxiv_ai](https://arxiv.org/abs/2604.21885v1)
- **Replay-buffer engineering for noise-robust quantum circuit optimization** — [arxiv_ai](https://arxiv.org/abs/2604.21863v1)
- **SyMTRS: Benchmark Multi-Task Synthetic Dataset for Depth, Domain Adaptation and Super-Resolution in Aerial Imagery** — [arxiv_ai](https://arxiv.org/abs/2604.21801v1)
- **Learning to Communicate: Toward End-to-End Optimization of Multi-Agent Language Systems** — [arxiv_ai](https://arxiv.org/abs/2604.21794v1)
- **Evaluation of Automatic Speech Recognition Using Generative Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21928v1)
- **EVENT5Ws: A Large Dataset for Open-Domain Event Extraction from Documents** — [arxiv_cl](https://arxiv.org/abs/2604.21890v1)
- **Revealing Geography-Driven Signals in Zone-Level Claim Frequency Models: An Empirical Study using Environmental and Visual Predictors** — [arxiv_lg](https://arxiv.org/abs/2604.21893v1)
- **StructMem: Structured Memory for Long-Horizon Behavior in LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21748v1)
- **To See the Unseen: on the Generalization Ability of Transformers in Symbolic Reasoning** — [arxiv_ai](https://arxiv.org/abs/2604.21632v1)
- **DryRUN: On the Role of Public Tests in LLM-Driven Code Generation** — [arxiv_ai](https://arxiv.org/abs/2604.21598v1)
- **VLAA-GUI: Knowing When to Stop, Recover, and Search, A Modular Framework for GUI Automation** — [arxiv_cl](https://arxiv.org/abs/2604.21375v1)
- **ReaGeo: Reasoning-Enhanced End-to-End Geocoding with LLMs** — [arxiv_cl](https://arxiv.org/abs/2604.21357v1)
- **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21477v1)
- **Provably Secure Steganography Based on List Decoding** — [arxiv_cr](https://arxiv.org/abs/2604.21394v1)
- **Strategic Heterogeneous Multi-Agent Architecture for Cost-Effective Code Vulnerability Detection** — [arxiv_cr](https://arxiv.org/abs/2604.21282v1)
- **Ramen: Robust Test-Time Adaptation of Vision-Language Models with Active Sample Selection** — [arxiv_lg](https://arxiv.org/abs/2604.21728v1)
- **A-IC3: Learning-Guided Adaptive Inductive Generalization for Hardware Model Checking** — [arxiv_lg](https://arxiv.org/abs/2604.21688v1)
- **Geometric Characterisation and Structured Trajectory Surrogates for Clinical Dataset Condensation** — [arxiv_lg](https://arxiv.org/abs/2604.21638v1)
- **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** — [arxiv_cl](https://arxiv.org/abs/2604.21871v1)
- **Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study** — [arxiv_cr](https://arxiv.org/abs/2604.21829v1)
- **Low-Rank Adaptation Redux for Large Models** — [arxiv_lg](https://arxiv.org/abs/2604.21905v1)
- **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** — [arxiv_lg](https://arxiv.org/abs/2604.21870v1)
- **Compliance Moral Hazard and the Backfiring Mandate** — [arxiv_lg](https://arxiv.org/abs/2604.21789v1)
- **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA** — [arxiv_cl](https://arxiv.org/abs/2604.21766v1)
- **Beyond N-gram: Data-Aware X-GRAM Extraction for Efficient Embedding Parameter Scaling** — [arxiv_cl](https://arxiv.org/abs/2604.21724v1)
- **From If-Statements to ML Pipelines: Revisiting Bias in Code-Generation** — [arxiv_cl](https://arxiv.org/abs/2604.21716v1)
- **Measuring Opinion Bias and Sycophancy via LLM-based Coercion** — [arxiv_cl](https://arxiv.org/abs/2604.21564v1)
- **Seeing Isn't Believing: Uncovering Blind Spots in Evaluator Vision-Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21523v1)
- **Decoupled DiLoCo for Resilient Distributed Pre-training** — [arxiv_cl](https://arxiv.org/abs/2604.21428v1)
- **CSC: Turning the Adversary's Poison against Itself** — [arxiv_cr](https://arxiv.org/abs/2604.21416v1)
- **PrismaDV: Automated Task-Aware Data Unit Test Generation** — [arxiv_lg](https://arxiv.org/abs/2604.21765v1)
- **Towards Universal Tabular Embeddings: A Benchmark Across Data Tasks** — [arxiv_lg](https://arxiv.org/abs/2604.21696v1)
- **A-THENA: Early Intrusion Detection for IoT with Time-Aware Hybrid Encoding and Network-Specific Augmentation** — [arxiv_lg](https://arxiv.org/abs/2604.21623v1)
- **MathDuels: Evaluating LLMs as Problem Posers and Solvers** — [arxiv_cl](https://arxiv.org/abs/2604.21916v1)
- **CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis** — [arxiv_cr](https://arxiv.org/abs/2604.21917v1)
- **Fine-Tuning Regimes Define Distinct Continual Learning Problems** — [arxiv_lg](https://arxiv.org/abs/2604.21927v1)
- **Transferable Physics-Informed Representations via Closed-Form Head Adaptation** — [arxiv_lg](https://arxiv.org/abs/2604.21761v1)
- **Interpretable facial dynamics as behavioral and perceptual traces of deepfakes** — [arxiv_lg](https://arxiv.org/abs/2604.21760v1)
- **Evaluating Post-hoc Explanations of the Transformer-based Genome Language Model DNABERT-2** — [arxiv_lg](https://arxiv.org/abs/2604.21690v1)
- **Tempered Sequential Monte Carlo for Trajectory and Policy Optimization with Differentiable Dynamics** — [arxiv_lg](https://arxiv.org/abs/2604.21456v1)
- **Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability** — [arxiv_lg](https://arxiv.org/abs/2604.21930v1)
- **The Sample Complexity of Multicalibration** — [arxiv_lg](https://arxiv.org/abs/2604.21923v1)
- **GFlowState: Visualizing the Training of Generative Flow Networks Beyond the Reward** — [arxiv_lg](https://arxiv.org/abs/2604.21830v1)
- **On the algebra of Koopman eigenfunctions and on some of their infinities** — [arxiv_lg](https://arxiv.org/abs/2604.21825v1)
- **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21774v1)
- **On the Challenges of Holistic Intrusion Detection in ICS** — [arxiv_cr](https://arxiv.org/abs/2604.21626v1)
- **Mitigate or Fail: How Risk Management Shapes Cybersecurity Competency** — [arxiv_cr](https://arxiv.org/abs/2604.21604v1)
- **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study** — [arxiv_cr](https://arxiv.org/abs/2604.21491v1)
- **A Stackelberg Model for Hybridization in Cryptography** — [arxiv_cr](https://arxiv.org/abs/2604.21436v1)
- **Adversarial Evasion in Non-Stationary Malware Detection: Minimizing Drift Signals through Similarity-Constrained Perturbations** — [arxiv_cr](https://arxiv.org/abs/2604.21310v1)
- **ECCFROG522PP: An Enhanced 522 bit Weierstrass Elliptic Curve** — [arxiv_cr](https://arxiv.org/abs/2604.21261v1)
- **There Will Be a Scientific Theory of Deep Learning** — [arxiv_lg](https://arxiv.org/abs/2604.21691v1)
- **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles** — [arxiv_cr](https://arxiv.org/abs/2604.21841v1)
- **Process-Mining of Hypertraces: Enabling Scalable Formal Security Verification of (Automotive) Network Architectures** — [arxiv_cr](https://arxiv.org/abs/2604.21606v1)
- **Anthropic created a test marketplace for agent-on-agent commerce** — [techcrunch_ai](https://techcrunch.com/2026/04/25/anthropic-created-a-test-marketplace-for-agent-on-agent-commerce/)
- **OpenAI CEO apologizes to Tumbler Ridge community** — [techcrunch_ai](https://techcrunch.com/2026/04/25/openai-ceo-apologizes-to-tumbler-ridge-community/)
- **Why Cohere is merging with Aleph Alpha** — [techcrunch_ai](https://techcrunch.com/2026/04/25/why-cohere-is-merging-with-aleph-alpha/)
- **Why Tokyo is the most important tech destination of 2026** — [techcrunch_ai](https://techcrunch.com/2026/04/25/why-tokyo-is-the-most-important-tech-destination-of-2026/)
- **Maine’s governor vetoes data center moratorium** — [techcrunch_ai](https://techcrunch.com/2026/04/25/maines-governor-vetoes-data-center-moratorium/)
- **Apple under Ternus: what comes next for the tech giant’s hardware strategy** — [techcrunch_ai](https://techcrunch.com/2026/04/25/apple-under-ternus-what-comes-next-for-the-tech-giants-hardware-strategy/)
- **kaktusesquire6rmu/ai-polymarket-agent** — [github](https://github.com/kaktusesquire6rmu/ai-polymarket-agent)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **Google-Cloud-AI/agent-platform** — [github](https://github.com/Google-Cloud-AI/agent-platform)
- **kimi-K2-6/kimi-K2.6** — [github](https://github.com/kimi-K2-6/kimi-K2.6)
- **lydiaaam/llm-ui-coord-benchmark** — [github](https://github.com/lydiaaam/llm-ui-coord-benchmark)
- **hacktivist123/agent-session-resume** — [github](https://github.com/hacktivist123/agent-session-resume)
- **simonw/llm-openai-via-codex** — [github](https://github.com/simonw/llm-openai-via-codex)
- **h9-tec/llm-systems-engineering-roadmap** — [github](https://github.com/h9-tec/llm-systems-engineering-roadmap)
- **Doriandarko/kimi-2-6-code** — [github](https://github.com/Doriandarko/kimi-2-6-code)
- **Tencent-Hunyuan/Hy3-preview** — [github](https://github.com/Tencent-Hunyuan/Hy3-preview)
- **wuyoscar/gpt_image_2_skill** — [github](https://github.com/wuyoscar/gpt_image_2_skill)
- **selmakcby/claude-agents-skills** — [github](https://github.com/selmakcby/claude-agents-skills)
- **chaohong-ai/ai-auto-work** — [github](https://github.com/chaohong-ai/ai-auto-work)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **MrFadiAi/free-llm-gateway** — [github](https://github.com/MrFadiAi/free-llm-gateway)
- **jameesy/foundry-vault** — [github](https://github.com/jameesy/foundry-vault)
- **esengine/reasonix** — [github](https://github.com/esengine/reasonix)
- **SparkEngineAI/QuantClaw-plugin** — [github](https://github.com/SparkEngineAI/QuantClaw-plugin)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **自动驾驶赛道DeepSeek，轻舟智航率先进军物理AI** — [qbitai](https://www.qbitai.com/2026/04/407026.html)
- **硬刚GPT-Image-2！国产AI生图“天花板”又被捅破了？** — [qbitai](https://www.qbitai.com/2026/04/406994.html)
- **0博士组合拿下ICLR时间检验奖！两个GPT天才本科生+二本逆袭LeCun弟子，十年论文终封神** — [qbitai](https://www.qbitai.com/2026/04/406892.html)
- **华为发布ADS 5！强化世界模型路线，今年投入180亿** — [qbitai](https://www.qbitai.com/2026/04/407363.html)
- **AI自主监测宠物健康，陪狗都不用自己来了！涂鸦Hey Tuya打造全屋智能“超级入口”** — [qbitai](https://www.qbitai.com/2026/04/406973.html)
- **燃油SUV车主熬出头了！华为乾崑智驾加持，全新奥迪Q5L率先实现智能化** — [qbitai](https://www.qbitai.com/2026/04/406960.html)
- **润芯微“国产软硬一体AI智能基座”发布，破解行业稀缺难题带动多端智能变革** — [36kr](https://36kr.com/p/3782901034785801?f=rss)
- **超算互联网推出DeepSeek-V4限时免费对话服务** — [36kr](https://36kr.com/newsflashes/3783020652518401?f=rss)
- **最前线｜2025年全年营收超64亿，海康机器人表示将继续推进AI融合与具身智能布局** — [36kr](https://36kr.com/p/3782137908403457?f=rss)
- **元戎启行全面押注大模型自动驾驶** — [36kr](https://36kr.com/newsflashes/3782028988882178?f=rss)
- **百度智能云上线DeepSeek-V4** — [36kr](https://36kr.com/newsflashes/3781942204128513?f=rss)
- **芯擎科技发布新一代AI座舱芯片“龍鹰二号”，将于2027年Q1启动适配** — [36kr](https://36kr.com/newsflashes/3783080587926793?f=rss)
- **华泰证券：光纤光缆产业进入历史大周期** — [36kr](https://36kr.com/newsflashes/3782964689148937?f=rss)
- **湖南AI中心落地湘江新区** — [36kr](https://36kr.com/newsflashes/3782957337926921?f=rss)
- **36氪首发 | 全球唯二、中国唯一造出微米级磁悬浮魔毯，已大规模量产** — [36kr](https://36kr.com/p/3782960065108996?f=rss)
- **科氪 | 国民好车深蓝L06增程版亮相北京车展 京东PLUS会员购车直减7000多元** — [36kr](https://36kr.com/p/3782437007039488?f=rss)
- **卡尔动力发布KargoBot Inside** — [36kr](https://36kr.com/newsflashes/3782201831742724?f=rss)