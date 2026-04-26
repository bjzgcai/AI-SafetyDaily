# AI Daily Digest [AI 安全] - 2026-04-26


# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-04-26  
**Author:** Senior AI Safety Research Analyst

## Highlights

Three developments today stand out for their potential to reshape the safety landscape. First, the introduction of **Transient Turn Injection** represents a critical vulnerability in stateless moderation architectures, demonstrating how adversarial intent can be distributed across isolated interactions to evade policy enforcement. Second, **Bounding the Black Box** addresses a fundamental regulatory vacuum by proposing a statistical certification framework for AI risk, moving beyond qualitative compliance to quantitative verification. Third, the theoretical proposal in **Alignment has a Fantasia Problem** challenges the core assumption of instruction-following, suggesting that current alignment methods fail when user goals are not fully formed, necessitating a shift toward intent discovery rather than prompt adherence.

## Adversarial Attacks & Robustness

The security frontier is expanding beyond single-turn prompt injection into complex, multi-modal, and physical domains. A significant shift is observed in the exploitation of stateless architectures. The paper **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** introduces a technique where automated attacker agents iteratively test and evade policy enforcement by distributing adversarial intent across isolated interactions. This marks a departure from conventional jailbreak approaches that rely on maintaining context, highlighting a systemic weakness in how commercial and open-source LLMs handle moderation state. This vulnerability complements findings in **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles**, which investigates whether an attacker can bypass multi-sensor redundancy by fabricating cross-sensor consistency. While TTI targets the logical state of software moderation, Cross-Modal Phantom targets the physical perception layer, suggesting a convergence of logical and physical attack vectors in safety-critical systems.

Further complicating the security posture is the issue of code vulnerabilities that evade standard analysis. **CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis** reveals that 87% of a curated set of real-world vulnerabilities remain undetected by per-commit static analysis tools like Semgrep and Bandit, as the exploitable condition is introduced across multiple benign commits. This finding aligns with the broader trend of **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks**, which demonstrates that physical attacks can directly manipulate image reconstruction processes in safety-critical screening applications. Together, these works suggest that robustness testing must evolve from static, single-point verification to dynamic, cumulative, and cross-modal evaluation. In contrast to these attack vectors, defensive research is emerging in **Interpretable facial dynamics as behavioral and perceptual traces of deepfakes**, which moves beyond deep learning classifiers to identify core low-dimensional patterns of facial movement, offering a more explainable alternative for detecting manipulation.

## Model Alignment, Interpretability, and Governance

Theoretical alignment research is confronting the limitations of current instruction-following paradigms. **Alignment has a Fantasia Problem** argues that modern AI assistants implicitly assume users can clearly articulate their goals, yet behavioral research shows people often engage with AI before their goals are fully formed. The authors posit that treating prompts as complete expressions of intent leads to "Fantasia interactions" that are convenient but misaligned with actual needs. This theoretical critique is supported by empirical findings in **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions**, which characterizes machine behavior using the Whistleblower's Dilemma. The study evaluates whether models encode social nuances regarding crime severity and relational closeness, finding discrepancies between prescriptive moral norms and autonomous model decision-making.

On the governance front, the lack of quantitative risk metrics remains a critical barrier to regulation. **Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation** identifies a critical vacuum in frameworks like the EU AI Act and NIST Risk Management Framework, which demand safety but lack technical methods for verifying "acceptable risk." The authors propose a statistical certification framework to bridge this gap. This approach contrasts with **Compliance Moral Hazard and the Backfiring Mandate**, which develops a mechanism design framework for decentralized risk analytics in banking networks. While the former focuses on individual model certification, the latter addresses systemic information aggregation problems where competing firms impede collective risk detection due to strategic frictions.

Interpretability efforts are also maturing to support these governance goals. **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** offers an interpretable machine learning model to identify moments of mechanistic reasoning in STEM education transcripts. While focused on education, the methodology of outputting time-varying probabilities for specific reasoning acts provides a template for auditing model behavior in high-stakes domains. Similarly, **GFlowState: Visualizing the Training of Generative Flow Networks Beyond the Reward** presents a visual analytics system to illuminate training dynamics, addressing the difficulty of interpreting how models explore sample spaces during training.

## Agent Security, Skills, and Ecosystems

As AI agents become more autonomous, the security of the "skill economy" and agent orchestration is becoming a primary concern. **Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study** highlights a new attack surface where adversaries interact with public agents to extract hidden proprietary skills. This risk is compounded by the emergence of agent marketplaces, such as the experiment reported by **Anthropic created a test marketplace for agent-on-agent commerce**, where AI agents struck real deals for real goods. While this demonstrates economic viability, it also introduces systemic risks regarding agent-to-agent trust and financial security.

To mitigate these risks, open-source tooling is prioritizing auditability and control. **Polaris** is described as a transaction-driven AI software factory kernel that treats the LLM as a restricted decision component, managed by a system kernel for execution, audit, budget, and rollback. This architecture directly addresses the "black box" nature of agentic workflows by enforcing separation of powers (PM, Architect, Director, QA roles). Similarly, **future-agi** provides an open-source platform for evaluating, observing, and improving LLM and agent applications, including tracing and guardrails. These tools contrast with earlier frameworks like **Nemobot Games**, which focuses on creating LLM-powered game agents for interactive learning, highlighting a divergence between research-oriented agent environments and production-oriented safety frameworks.

## Benchmarks and Evaluation

Static benchmarks are increasingly insufficient for evaluating frontier capabilities. **MathDuels: Evaluating LLMs as Problem Posers and Solvers** introduces a self-play benchmark where models author math problems under adversarial prompting and solve problems authored by others. This dynamic evaluation moves beyond fixed problem sets to assess generative and adversarial capabilities. In the audio domain, **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA** presents a large-scale, real-world benchmark to rigorously evaluate audio reasoning beyond surface-level acoustic recognition, addressing the shortcut strategies prevalent in existing benchmarks.

Event extraction and temporal reasoning also require new evaluation standards. **EVENT5Ws: A Large Dataset for Open-Domain Event Extraction from Documents** addresses the limitations of closed-domain algorithms by providing a manually annotated, statistically verified open-domain dataset. This complements **Inferring High-Level Events from Timestamped Data: Complexity and Medical Applications**, which develops a logic-based approach to detecting high-level temporally extended events from timestamped data. These works collectively emphasize the need for benchmarks that capture complexity, temporality, and open-domain generalization rather than rote memorization or classification.

## Open-Source Security Tools and Frameworks

The open-source community is responding to safety challenges with specialized infrastructure. **Polaris** (GitHub) stands out as a transaction-driven AI software factory kernel, implementing a "three-provinces, six-departments" power separation architecture to ensure enterprise-grade, auditable software delivery. **future-agi** (GitHub) offers a self-hostable platform for agent evaluation and observation, including tracing and guardrails, which is critical for monitoring agentic behavior in production. For privacy-focused development, **vela** (GitHub) provides an AI-powered IDE for novel writing that emphasizes local LLMs and privacy-first design with Bring Your Own Key (BYOK). Additionally, **stash** (GitHub) introduces a persistent memory layer for AI agents, storing episodes and facts in Postgres, which aids in maintaining context and audit trails without cloud dependency.

## Industry and Policy Developments

In the policy sphere, **Maine’s governor vetoes data center moratorium** (L.D. 307) indicates a regulatory decision to allow continued data center expansion until November 1, 2027, rather than imposing a blanket pause. This contrasts with the safety incident reported by **OpenAI CEO apologizes to Tumbler Ridge community**, where the CEO admitted failure to alert law enforcement about a suspect in a recent mass shooting. This incident underscores the limitations of current safety filters in preventing real-world harm when intent is ambiguous or pre-crime.

Regarding geopolitical strategy, **Why Cohere is merging with Aleph Alpha** signals a move toward sovereign AI alternatives in Europe, supported by government blessing. Similarly, **安波福发布“中国定义”核心战略** (Ambot) outlines a strategy to serve non-Chinese markets using hardware-software splits to meet global compliance, reflecting the increasing complexity of cross-border AI governance. While **36kr** reports on various commercial developments, such as the acquisition of **神导科技** by **恒宇信通** or the launch of the **深蓝 L06** vehicle, these are primarily commercial announcements with limited direct safety implications and are treated here with caution regarding their framing.

## Looking Forward

Several theoretical and practical questions remain unresolved. First, the **Transient Turn Injection** vulnerability suggests that stateless moderation is fundamentally flawed; future research must determine if stateful moderation is scalable or if new cryptographic proofs of intent are required. Second, the **Fantasia Problem** raises the question of how to align systems with users who cannot articulate their goals; this may require a shift from instruction following to collaborative goal formation. Third, the **Bounding the Black Box** framework highlights the need for standardized statistical metrics for "acceptable risk," yet the definition of these metrics remains contested across jurisdictions. Finally, as agents gain the ability to execute transactions and access skills, the security of the **skill marketplace** must be addressed through formal verification of agent behaviors and economic incentives for safety. The community must now validate whether current audit tools like **Polaris** and **future-agi** can scale to the complexity of autonomous agent ecosystems.

---


## References

- **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21860v1)
- **Enabling and Inhibitory Pathways of University Students' Willingness to Disclose AI Use: A Cognition-Affect-Conation Perspective** — [arxiv_ai](https://arxiv.org/abs/2604.21733v1)
- **Machine Behavior in Relational Moral Dilemmas: Moral Rightness, Predicted Human Behavior, and Model Decisions** — [arxiv_cl](https://arxiv.org/abs/2604.21871v1)
- **Locating acts of mechanistic reasoning in student team conversations with mechanistic machine learning** — [arxiv_lg](https://arxiv.org/abs/2604.21870v1)
- **GFlowState: Visualizing the Training of Generative Flow Networks Beyond the Reward** — [arxiv_lg](https://arxiv.org/abs/2604.21830v1)
- **Compliance Moral Hazard and the Backfiring Mandate** — [arxiv_lg](https://arxiv.org/abs/2604.21789v1)
- **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** — [arxiv_cr](https://arxiv.org/abs/2604.21774v1)
- **Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation** — [arxiv_ai](https://arxiv.org/abs/2604.21854v1)
- **Modulating Cross-Modal Convergence with Single-Stimulus, Intra-Modal Dispersion** — [arxiv_ai](https://arxiv.org/abs/2604.21836v1)
- **Alignment has a Fantasia Problem** — [arxiv_ai](https://arxiv.org/abs/2604.21827v1)
- **Quotient-Space Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2604.21809v1)
- **SyMTRS: Benchmark Multi-Task Synthetic Dataset for Depth, Domain Adaptation and Super-Resolution in Aerial Imagery** — [arxiv_ai](https://arxiv.org/abs/2604.21801v1)
- **Inferring High-Level Events from Timestamped Data: Complexity and Medical Applications** — [arxiv_ai](https://arxiv.org/abs/2604.21793v1)
- **Why are all LLMs Obsessed with Japanese Culture? On the Hidden Cultural and Regional Biases of LLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21751v1)
- **MathDuels: Evaluating LLMs as Problem Posers and Solvers** — [arxiv_cl](https://arxiv.org/abs/2604.21916v1)
- **Mapping the Political Discourse in the Brazilian Chamber of Deputies: A Multi-Faceted Computational Approach** — [arxiv_cl](https://arxiv.org/abs/2604.21897v1)
- **AUDITA: A New Dataset to Audit Humans vs. AI Skill at Audio QA** — [arxiv_cl](https://arxiv.org/abs/2604.21766v1)
- **Interpretable facial dynamics as behavioral and perceptual traces of deepfakes** — [arxiv_lg](https://arxiv.org/abs/2604.21760v1)
- **Ramen: Robust Test-Time Adaptation of Vision-Language Models with Active Sample Selection** — [arxiv_lg](https://arxiv.org/abs/2604.21728v1)
- **Seeing Fast and Slow: Learning the Flow of Time in Videos** — [arxiv_ai](https://arxiv.org/abs/2604.21931v1)
- **When Prompts Override Vision: Prompt-Induced Hallucinations in LVLMs** — [arxiv_ai](https://arxiv.org/abs/2604.21911v1)
- **From Research Question to Scientific Workflow: Leveraging Agentic AI for Science Automation** — [arxiv_ai](https://arxiv.org/abs/2604.21910v1)
- **A Scale-Adaptive Framework for Joint Spatiotemporal Super-Resolution with Diffusion Models** — [arxiv_ai](https://arxiv.org/abs/2604.21903v1)
- **GiVA: Gradient-Informed Bases for Vector-Based Adaptation** — [arxiv_ai](https://arxiv.org/abs/2604.21901v1)
- **Nemobot Games: Crafting Strategic AI Gaming Agents for Interactive Learning with Large Language Models** — [arxiv_ai](https://arxiv.org/abs/2604.21896v1)
- **A Multi-Stage Warm-Start Deep Learning Framework for Unit Commitment** — [arxiv_ai](https://arxiv.org/abs/2604.21891v1)
- **TingIS: Real-time Risk Event Discovery from Noisy Customer Incidents at Enterprise Scale** — [arxiv_ai](https://arxiv.org/abs/2604.21889v1)
- **A Multimodal Text- and Graph-Based Approach for Open-Domain Event Extraction from Documents** — [arxiv_ai](https://arxiv.org/abs/2604.21885v1)
- **Addressing Image Authenticity When Cameras Use Generative AI** — [arxiv_ai](https://arxiv.org/abs/2604.21879v1)
- **Replay-buffer engineering for noise-robust quantum circuit optimization** — [arxiv_ai](https://arxiv.org/abs/2604.21863v1)
- **Evaluation of Automatic Speech Recognition Using Generative Large Language Models** — [arxiv_cl](https://arxiv.org/abs/2604.21928v1)
- **EVENT5Ws: A Large Dataset for Open-Domain Event Extraction from Documents** — [arxiv_cl](https://arxiv.org/abs/2604.21890v1)
- **Revisiting Non-Verbatim Memorization in Large Language Models: The Role of Entity Surface Forms** — [arxiv_cl](https://arxiv.org/abs/2604.21882v1)
- **SemEval-2026 Task 4: Narrative Story Similarity and Narrative Representation Learning** — [arxiv_cl](https://arxiv.org/abs/2604.21782v1)
- **Misinformation Span Detection in Videos via Audio Transcripts** — [arxiv_cl](https://arxiv.org/abs/2604.21767v1)
- **Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability** — [arxiv_lg](https://arxiv.org/abs/2604.21930v1)
- **Fine-Tuning Regimes Define Distinct Continual Learning Problems** — [arxiv_lg](https://arxiv.org/abs/2604.21927v1)
- **The Sample Complexity of Multicalibration** — [arxiv_lg](https://arxiv.org/abs/2604.21923v1)
- **Low-Rank Adaptation Redux for Large Models** — [arxiv_lg](https://arxiv.org/abs/2604.21905v1)
- **Revealing Geography-Driven Signals in Zone-Level Claim Frequency Models: An Empirical Study using Environmental and Visual Predictors** — [arxiv_lg](https://arxiv.org/abs/2604.21893v1)
- **Beyond Expected Information Gain: Stable Bayesian Optimal Experimental Design with Integral Probability Metrics and Plug-and-Play Extensions** — [arxiv_lg](https://arxiv.org/abs/2604.21849v1)
- **On the algebra of Koopman eigenfunctions and on some of their infinities** — [arxiv_lg](https://arxiv.org/abs/2604.21825v1)
- **PrismaDV: Automated Task-Aware Data Unit Test Generation** — [arxiv_lg](https://arxiv.org/abs/2604.21765v1)
- **Transferable Physics-Informed Representations via Closed-Form Head Adaptation** — [arxiv_lg](https://arxiv.org/abs/2604.21761v1)
- **Neural surrogates for crystal growth dynamics with variable supersaturation: explicit vs. implicit conditioning** — [arxiv_lg](https://arxiv.org/abs/2604.21753v1)
- **CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis** — [arxiv_cr](https://arxiv.org/abs/2604.21917v1)
- **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles** — [arxiv_cr](https://arxiv.org/abs/2604.21841v1)
- **Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study** — [arxiv_cr](https://arxiv.org/abs/2604.21829v1)
- **An effective variant of the Hartigan $k$-means algorithm** — [arxiv_lg](https://arxiv.org/abs/2604.21798v1)
- **Anthropic created a test marketplace for agent-on-agent commerce** — [techcrunch_ai](https://techcrunch.com/2026/04/25/anthropic-created-a-test-marketplace-for-agent-on-agent-commerce/)
- **OpenAI CEO apologizes to Tumbler Ridge community** — [techcrunch_ai](https://techcrunch.com/2026/04/25/openai-ceo-apologizes-to-tumbler-ridge-community/)
- **Why Cohere is merging with Aleph Alpha** — [techcrunch_ai](https://techcrunch.com/2026/04/25/why-cohere-is-merging-with-aleph-alpha/)
- **Why Tokyo is the most important tech destination of 2026** — [techcrunch_ai](https://techcrunch.com/2026/04/25/why-tokyo-is-the-most-important-tech-destination-of-2026/)
- **Maine’s governor vetoes data center moratorium** — [techcrunch_ai](https://techcrunch.com/2026/04/25/maines-governor-vetoes-data-center-moratorium/)
- **Apple under Ternus: what comes next for the tech giant’s hardware strategy** — [techcrunch_ai](https://techcrunch.com/2026/04/25/apple-under-ternus-what-comes-next-for-the-tech-giants-hardware-strategy/)
- **heider-x/vela** — [github](https://github.com/heider-x/vela)
- **kimi-K2-6/kimi-K2.6** — [github](https://github.com/kimi-K2-6/kimi-K2.6)
- **kaktusesquire6rmu/ai-polymarket-agent** — [github](https://github.com/kaktusesquire6rmu/ai-polymarket-agent)
- **selmakcby/claude-agents-skills** — [github](https://github.com/selmakcby/claude-agents-skills)
- **jwangkun/hermes-agent-guide** — [github](https://github.com/jwangkun/hermes-agent-guide)
- **ovoment/ovo-local-llm** — [github](https://github.com/ovoment/ovo-local-llm)
- **dainsiahtill-dev/Polaris** — [github](https://github.com/dainsiahtill-dev/Polaris)
- **chaohong-ai/ai-auto-work** — [github](https://github.com/chaohong-ai/ai-auto-work)
- **muxprotocol/kalshi-trading-bot** — [github](https://github.com/muxprotocol/kalshi-trading-bot)
- **alash3al/stash** — [github](https://github.com/alash3al/stash)
- **chekusu/wanman** — [github](https://github.com/chekusu/wanman)
- **future-agi/future-agi** — [github](https://github.com/future-agi/future-agi)
- **codejunkie99/prompting-skill** — [github](https://github.com/codejunkie99/prompting-skill)
- **K-Dense-AI/mimeo** — [github](https://github.com/K-Dense-AI/mimeo)
- **Zhou-Shilin/Aether** — [github](https://github.com/Zhou-Shilin/Aether)
- **g2i-ai/agents** — [github](https://github.com/g2i-ai/agents)
- **lydiaaam/llm-ui-coord-benchmark** — [github](https://github.com/lydiaaam/llm-ui-coord-benchmark)
- **simonw/llm-openai-via-codex** — [github](https://github.com/simonw/llm-openai-via-codex)
- **MrFadiAi/free-llm-gateway** — [github](https://github.com/MrFadiAi/free-llm-gateway)
- **realZillionX/InspireSkill** — [github](https://github.com/realZillionX/InspireSkill)
- **Claude终于认了！降智坐实，越聊越傻，3个bug全曝光** — [qbitai](https://www.qbitai.com/2026/04/407502.html)
- **全球首个医疗视频理解大模型开源！6k+组精标测试集与英雄榜同步上线，开发者速来！** — [qbitai](https://www.qbitai.com/2026/04/407486.html)
- **DeepSeek阮翀加盟元戎首秀，详解基座VLA，研发提效10倍** — [qbitai](https://www.qbitai.com/2026/04/407465.html)
- **华为发布ADS 5！强化世界模型路线，今年投入180亿** — [qbitai](https://www.qbitai.com/2026/04/407363.html)
- **恒宇信通：筹划购买神导科技100%股权，股票停牌** — [36kr](https://36kr.com/newsflashes/3783353736649734?f=rss)
- **陈茂波：今年以来香港新股集资额继续位列全球首位** — [36kr](https://36kr.com/newsflashes/3783317153209348?f=rss)
- **欧莱雅BRANDSTORM 2026中国总决赛落幕，AI成美妆创新核心议题｜最前线** — [36kr](https://36kr.com/p/3783249100397570?f=rss)
- **国信证券：结构上结合行业拥挤度均衡配置，重视科技成长主线、战略资源、以及白酒地产** — [36kr](https://36kr.com/newsflashes/3783131237653763?f=rss)
- **36氪首发 | 全球唯二、中国唯一造出微米级磁悬浮魔毯，已大规模量产** — [36kr](https://36kr.com/p/3782960065108996?f=rss)
- **润芯微“国产软硬一体AI智能基座”发布，破解行业稀缺难题带动多端智能变革** — [36kr](https://36kr.com/p/3782901034785801?f=rss)
- **科氪 | 国民好车深蓝L06增程版亮相北京车展 京东PLUS会员购车直减7000多元** — [36kr](https://36kr.com/p/3782437007039488?f=rss)
- **安波福发布“中国定义”核心战略** — [36kr](https://36kr.com/newsflashes/3783419976391684?f=rss)
- **京东启动AI硬件孵化计划** — [36kr](https://36kr.com/newsflashes/3783158630948103?f=rss)