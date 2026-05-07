# AI Daily Digest [AI 安全] - 2026-05-07


# Daily Thematic Digest: AI Safety, Alignment, Security, and Governance
**Date:** 2026-05-07
**Author:** Senior AI Safety Researcher

## Highlights

Three developments stand out today as critical inflection points for the field. First, the academic community is aggressively moving to democratize agentic search capabilities through **OpenSearch-VL** and **OpenSeeker-v2**, challenging the closed, resource-intensive pipelines previously dominated by industrial giants. This shift is vital for safety auditing, as reproducible training recipes allow for independent verification of agent behaviors. Second, **SymptomAI** provides one of the largest empirical deployments of conversational AI for medical assessment, involving nearly 14,000 participants. This study offers rare, real-world data on how LLMs perform in unstructured, everyday patient interactions, moving beyond curated vignettes to actual safety-critical deployment. Third, testimony from OpenAI’s former CTO, Mira Murati, during the ongoing *Musk v. Altman* trial suggests a disconnect between public safety assurances and internal legal assessments. This underscores the growing tension between corporate governance narratives and the technical realities of model safety standards.

## Agentic Reasoning and Reproducible Benchmarks

The landscape of agentic evaluation is shifting from isolated task performance to complex, multi-step reasoning environments. Historically, frontier search agents relied on proprietary data and reinforcement learning pipelines that were opaque to the broader community. **OpenSearch-VL** directly addresses this by providing a fully open-source recipe for training multimodal deep search agents using agentic reinforcement learning. By curating dedicated high-quality training data and transparent trajectory synthesis pipelines, this work enables the community to audit the reasoning chains of search agents rather than treating them as black boxes. This aligns with findings from **OpenSeeker-v2**, which demonstrates that simple Supervised Fine-Tuning (SFT) on informative, high-difficulty trajectories can rival more complex RL pipelines. The authors report that when fueled with high-quality data, SFT approaches are surprisingly powerful, suggesting that data curation may be a more significant bottleneck than algorithmic complexity for safety-critical reasoning.

However, the scope of evaluation must expand beyond search. **Workspace-Bench 1.0** introduces a necessary benchmark for AI agents operating within complex file dependencies, a scenario often overlooked in standard benchmarks. Unlike previous evaluations that rely on pre-specified files, this framework tests agents on identifying and updating explicit and implicit dependencies among heterogeneous files. This is a critical safety consideration, as agents manipulating real-world workspaces pose risks of data corruption or unintended side effects. Complementing this, **BRIGHT-P** rethinks reasoning-intensive retrieval, arguing that existing benchmarks like BRIGHT evaluate retrievers in isolation rather than as part of an evidence portfolio construction process. The authors propose that retrievers in agentic systems must provide complementary evidence across iterative search and synthesis, a requirement that current static benchmarks fail to capture. Together, these works highlight a consensus that future safety evaluations must account for the iterative, interactive, and dependency-heavy nature of real-world agent deployment.

## Multimodal Fidelity, Efficiency, and Physical Grounding

In the realm of generative models, the focus is increasingly on balancing efficiency with fidelity, particularly regarding unintended changes and physical consistency. **StableI2I** proposes a unified evaluation framework that explicitly measures content fidelity and pre-post consistency in image-to-image transitions. The authors note that existing evaluations largely fail to assess whether output images preserve the semantic correspondence and spatial structure of the input, a gap that poses significant risks for applications like image restoration or editing where fidelity is paramount. This concern for unintended changes is echoed in **D-OPSD**, which addresses the challenge of continuously tuning step-distilled diffusion models. The authors find that applying standard fine-tuning techniques compromises the inherent few-step inference capability, necessitating an on-policy self-distillation paradigm to maintain performance without degrading the model's efficiency.

Beyond 2D generation, the integration of physics into 3D asset generation is becoming a prerequisite for embodied AI. **PhysForge** introduces a decoupled two-stage framework supported by **PhysDB**, a large-scale dataset of 150,000 assets with four-tier physical annotations. The authors argue that interactive asset generation must be rooted in functional logic and hierarchical physics, moving beyond static geometry. This is further supported by **iWorld-Bench**, a comprehensive benchmark for training and testing world models on interaction-related abilities such as distance perception and memory. The construction of a diverse dataset with 330k video clips aims to address the lack of large-scale datasets for evaluating physical interaction capabilities. Meanwhile, **Stream-R1** and **Stream-T1** tackle the computational bottlenecks of video generation. **Stream-R1** introduces reliability-perplexity aware reward distillation, arguing that indiscriminate supervision caps distilled quality. **Stream-T1** proposes shifting focus to streaming video generation for test-time scaling, identifying that chunk-level synthesis is intrinsically suited for reducing computational overhead while enabling fine-grained temporal control. These efficiency gains are not merely performance optimizations; they reduce the energy footprint and latency, which are critical factors in the safety and accessibility of deployment.

## Governance, Real-World Safety, and Industry Incidents

The intersection of technical capability and governance is currently under intense scrutiny. The **SymptomAI** study represents a significant step in empirical safety validation. By deploying conversational AI agents for end-to-end patient interviewing and differential diagnosis via the Fitbit app, the researchers randomized participants (N=13,917) to interact with five AI agents. This corpus captures real-world symptom reporting, allowing for a more accurate assessment of diagnostic performance compared to curated case studies. The authors report that while models excel on complex scenarios with rich context, their performance in everyday life remains a critical area for investigation. This empirical approach contrasts with the theoretical safety claims often made by industry leaders.

This tension was highlighted during the *Musk v. Altman* trial, where Mira Murati testified under oath that CEO Sam Altman falsely stated that OpenAI's legal department determined a new model did not violate safety standards. While the trial proceedings are ongoing, this testimony suggests that internal safety determinations may not always align with public assurances. In parallel, industry shifts indicate a recalibration of risk. Google has pulled the plug on Project Mariner, an experimental feature designed to perform tasks across the web, citing a need to reassess the technology. Similarly, Apple agreed to pay $250 million to settle a class action lawsuit for overpromising the arrival of Siri’s AI features. These legal and product developments signal that the market is beginning to penalize companies that prioritize feature velocity over verified safety and reliability.

Open-source security tools are emerging to fill the gap left by corporate transparency. The **Agent_Memory_Techniques** repository provides 30 runnable Jupyter notebooks covering conversation buffers, vector stores, and knowledge graphs, offering a standardized way to audit memory mechanisms. Similarly, **agent-safety-eval-lab** offers a framework for agent trace and tool-use safety evaluation, allowing researchers to monitor how agents interact with external tools. These tools are essential for the community to independently verify the safety claims made by proprietary systems.

Regarding hardware and infrastructure, reports indicate that Samsung has announced the cessation of sales for all home appliances in the Chinese market to respond to changing market conditions, while Apple has increased production targets for the MacBook Neo to 10 million units. While these are business decisions, they reflect the intense demand for AI-capable hardware. In the robotics sector, reports of executive departures from Boston Dynamics and funding for specialized robotic hand startups like the one backed by Tencent and Baidu suggest a consolidation of effort towards dexterous manipulation. However, these industry movements must be viewed with caution; as noted in reports regarding the "Terafab" chip factory proposal by SpaceX, the capital intensity of AI infrastructure is rising, potentially creating barriers to entry that limit independent safety auditing.

## Looking Forward

Several theoretical and practical questions remain unresolved as the field moves toward more capable agents. First, the "trust" gap identified in the Murati testimony raises a fundamental question: How can external auditors verify safety claims when internal legal and safety departments operate under different incentives? The community needs standardized, third-party certification protocols that are independent of corporate legal departments. Second, the gap between simulated physics and real-world interaction remains significant. While **PhysForge** and **iWorld-Bench** make strides, the question of how to verify that a world model's internal physics simulation accurately predicts real-world consequences without costly physical testing remains open. Finally, as agents become more autonomous in workspace and medical settings, the definition of "harm" must evolve. Current benchmarks measure task success, but they do not adequately measure the long-term impact of agent decisions on human well-being or data integrity. Future research must prioritize longitudinal studies that track agent behavior over extended periods, moving beyond single-turn evaluations to understand the cumulative safety profile of agentic systems.

---


## References

- **D-OPSD: On-Policy Self-Distillation for Continuously Tuning Step-Distilled Diffusion Models** — [huggingface_papers](https://arxiv.org/abs/2605.05204)
- **Stream-R1: Reliability-Perplexity Aware Reward Distillation for Streaming Video Generation** — [huggingface_papers](https://arxiv.org/abs/2605.03849)
- **RLDX-1 Technical Report** — [huggingface_papers](https://arxiv.org/abs/2605.03269)
- **OpenSearch-VL: An Open Recipe for Frontier Multimodal Search Agents** — [huggingface_papers](https://arxiv.org/abs/2605.05185)
- **Stream-T1: Test-Time Scaling for Streaming Video Generation** — [huggingface_papers](https://arxiv.org/abs/2605.04461)
- **Lightning Unified Video Editing via In-Context Sparse Attention** — [huggingface_papers](https://arxiv.org/abs/2605.04569)
- **PhysForge: Generating Physics-Grounded 3D Assets for Interactive Virtual World** — [huggingface_papers](https://arxiv.org/abs/2605.05163)
- **StableI2I: Spotting Unintended Changes in Image-to-Image Transition** — [huggingface_papers](https://arxiv.org/abs/2605.04453)
- **Parameter-Efficient Multi-View Proficiency Estimation: From Discriminative Classification to Generative Feedback** — [huggingface_papers](https://arxiv.org/abs/2605.03848)
- **APEX: Large-scale Multi-task Aesthetic-Informed Popularity Prediction for AI-Generated Music** — [huggingface_papers](https://arxiv.org/abs/2605.03395)
- **Awaking Spatial Intelligence in Unified Multimodal Understanding and Generation** — [huggingface_papers](https://arxiv.org/abs/2605.04128)
- **Rethinking Reasoning-Intensive Retrieval: Evaluating and Advancing Retrievers in Agentic Search Systems** — [huggingface_papers](https://arxiv.org/abs/2605.04018)
- **PatRe: A Full-Stage Office Action and Rebuttal Generation Benchmark for Patent Examination** — [huggingface_papers](https://arxiv.org/abs/2605.03571)
- **A Benchmark for Interactive World Models with a Unified Action Generation Framework** — [huggingface_papers](https://arxiv.org/abs/2605.03941)
- **Workspace-Bench 1.0: Benchmarking AI Agents on Workspace Tasks with Large-Scale File Dependencies** — [huggingface_papers](https://arxiv.org/abs/2605.03596)
- **OpenSeeker-v2: Pushing the Limits of Search Agents with Informative and High-Difficulty Trajectories** — [huggingface_papers](https://arxiv.org/abs/2605.04036)
- **SymptomAI: Towards a Conversational AI Agent for Everyday Symptom Assessment** — [huggingface_papers](https://arxiv.org/abs/2605.04012)
- **Is xAI a neocloud now?** — [techcrunch_ai](https://techcrunch.com/2026/05/06/is-xai-a-neocloud-now/)
- **Five architects of the AI economy explain where the wheels are coming off** — [techcrunch_ai](https://techcrunch.com/2026/05/06/five-architects-of-the-ai-economy-explain-where-the-wheels-are-coming-off/)
- **Musk’s biggest loyalist became his biggest liability** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/925665/musk-altman-trial-shivon-zilis-testimony)
- **Google shuts down Project Mariner** — [theverge_ai](https://www.theverge.com/tech/925559/google-project-mariner-shut-down)
- **How David Sacks crashed and burned in the White House** — [theverge_ai](https://www.theverge.com/column/925487/david-sacks-trump-administration-ai-model-review)
- **Mira Murati tells the court that she couldn’t trust Sam Altman’s words** — [theverge_ai](https://www.theverge.com/ai-artificial-intelligence/925338/openai-musk-v-altman-mira-murati)
- **SpaceX may spend up to $119B on ‘Terafab’ chip factory in Texas** — [techcrunch_ai](https://techcrunch.com/2026/05/06/spacex-may-spend-up-to-119-billion-on-terafab-chip-factory-in-texas/)
- **DeepSeek could hit $45B valuation from its first investment round** — [techcrunch_ai](https://techcrunch.com/2026/05/06/deepseek-could-hit-45b-valuation-from-its-first-investment-round/)
- **Khosla-backed robotics startup Genesis AI has gone full stack, demo shows** — [techcrunch_ai](https://techcrunch.com/2026/05/06/khosla-backed-robotics-startup-genesis-ai-has-gone-full-stack-demo-shows/)
- **Live updates from Elon Musk and Sam Altman’s court battle over the future of OpenAI** — [theverge_ai](https://www.theverge.com/tech/917225/sam-altman-elon-musk-openai-lawsuit)
- **5 gardening tips you can try right in Search** — [google_ai](https://blog.google/products-and-platforms/products/search/gardening-tips/)
- **At TechCrunch Disrupt 2026, all your M&A questions will be answered** — [techcrunch_ai](https://techcrunch.com/2026/05/06/at-techcrunch-disrupt-2026-all-your-ma-questions-will-be-answered/)
- **3 days left to lock in 50% off a second ticket to TechCrunch Disrupt 2026** — [techcrunch_ai](https://techcrunch.com/2026/05/06/3-days-left-to-lock-in-50-off-a-second-ticket-to-techcrunch-disrupt-2026/)
- **AI boom pushes Samsung to $1T** — [techcrunch_ai](https://techcrunch.com/2026/05/06/ai-boom-pushes-samsung-to-1t/)
- **Google&#8217;s AI search summaries will now quote Reddit** — [theverge_ai](https://www.theverge.com/tech/924993/google-ai-search-mode-overviews-update-reddit-links)
- **Microsoft’s Office and LinkedIn chief now runs Teams in latest reshuffle** — [theverge_ai](https://www.theverge.com/tech/924931/microsoft-office-copilot-windows-reorg-shuffle)
- **The Download: seafloor science and military chatbots** — [mit_tech_review](https://www.technologyreview.com/2026/05/06/1136917/the-download-seafloor-science-military-ai-chatbots/)
- **Chrome’s AI features may be hogging 4GB of your computer storage** — [theverge_ai](https://www.theverge.com/tech/924933/google-chrome-4gb-gemini-nano-ai-features)
- **Barry Diller trusts Sam Altman. But ‘trust is irrelevant’ as AGI nears, he says.** — [techcrunch_ai](https://techcrunch.com/2026/05/06/barry-diller-trusts-sam-altman-but-trust-is-irrelevant-as-agi-nears-he-says/)
- **Snap says its $400M deal with Perplexity ‘amicably ended’** — [techcrunch_ai](https://techcrunch.com/2026/05/06/snap-says-its-400m-deal-with-perplexity-amicably-ended/)
- **How Elon Musk left OpenAI, according to Greg Brockman** — [techcrunch_ai](https://techcrunch.com/2026/05/06/how-elon-musk-left-openai-according-to-greg-brockman/)
- **Google updates AI search to include quotes from Reddit and other sources** — [techcrunch_ai](https://techcrunch.com/2026/05/06/google-updates-ai-search-to-include-expert-advice-from-reddit-and-other-web-forums/)
- **Tinder owner Match Group is slowing hiring to pay for its increased use of AI tools** — [techcrunch_ai](https://techcrunch.com/2026/05/06/tinder-owner-match-group-is-slowing-hiring-to-pay-for-its-increased-use-of-ai-tools/)
- **Apple to pay $250M to settle lawsuit over Siri’s delayed AI features** — [techcrunch_ai](https://techcrunch.com/2026/05/06/apple-to-pay-250m-to-settle-lawsuit-over-siris-delayed-ai-features/)
- **Ethos raises $22.75M from a16z for its expert network with voice onboarding** — [techcrunch_ai](https://techcrunch.com/2026/05/06/ethos-raises-22-75m-from-a16z-for-its-expert-network-with-voice-onboarding/)
- **voidborne-d/master-skill** — [github](https://github.com/voidborne-d/master-skill)
- **0xbl33p/goblintown** — [github](https://github.com/0xbl33p/goblintown)
- **awizemann/harness** — [github](https://github.com/awizemann/harness)
- **NirDiamant/Agent_Memory_Techniques** — [github](https://github.com/NirDiamant/Agent_Memory_Techniques)
- **KSroido/Kagi-Session2API-MCP** — [github](https://github.com/KSroido/Kagi-Session2API-MCP)
- **AlexCheema/talos-vs-macbook** — [github](https://github.com/AlexCheema/talos-vs-macbook)
- **TheSashaDev/girl-agent** — [github](https://github.com/TheSashaDev/girl-agent)
- **Ajai53200/DeepSeek-V4-Pro-App** — [github](https://github.com/Ajai53200/DeepSeek-V4-Pro-App)
- **bestpracticaI/kalshi-ai-trading-bot** — [github](https://github.com/bestpracticaI/kalshi-ai-trading-bot)
- **warpdot-dev/craft-agents-oss** — [github](https://github.com/warpdot-dev/craft-agents-oss)
- **warpdot-dev/composio** — [github](https://github.com/warpdot-dev/composio)
- **lukiIabs/trading-agents** — [github](https://github.com/lukiIabs/trading-agents)
- **zarazhangrui/beautiful-html-templates** — [github](https://github.com/zarazhangrui/beautiful-html-templates)
- **YutoTerashima/agent-safety-eval-lab** — [github](https://github.com/YutoTerashima/agent-safety-eval-lab)
- **wjn1996/HeavySkill** — [github](https://github.com/wjn1996/HeavySkill)
- **alvinunreal/openpets** — [github](https://github.com/alvinunreal/openpets)
- **adithya-s-k/RL_Envs_101** — [github](https://github.com/adithya-s-k/RL_Envs_101)
- **prime-radiant-inc/books-for-bots** — [github](https://github.com/prime-radiant-inc/books-for-bots)
- **kostyay/pi-k-excalidraw** — [github](https://github.com/kostyay/pi-k-excalidraw)
- **Naroh091/hermes-war-room** — [github](https://github.com/Naroh091/hermes-war-room)
- **00后下场整顿Agent：啥都不学就能用好AI，这才是正确打开方式** — [qbitai](https://www.qbitai.com/2026/05/413612.html)
- **一年磨一剑，今年最炸机器人Demo来了！** — [qbitai](https://www.qbitai.com/2026/05/413830.html)
- **云知声山海知医慧保大模型重磅发布：以高密智能深耕高价值场景，重构医疗保险数智新生态** — [qbitai](https://www.qbitai.com/2026/05/413782.html)
- **波士顿动力泯然众人了，高管集体出走，机器人“量产”只能造4台** — [qbitai](https://www.qbitai.com/2026/05/413613.html)
- **英伟达重新思考AI TCO：为何每Token成本才是唯一重要的指标** — [qbitai](https://www.qbitai.com/2026/05/413604.html)
- **Token需求狂飙千倍，22亿热钱涌向这家AGI Infra头号玩家** — [qbitai](https://www.qbitai.com/2026/05/413591.html)
- **马斯克22万张GPU全卖给Claude用：5小时限额翻倍，双方合作建太空算力** — [qbitai](https://www.qbitai.com/2026/05/413569.html)
- **AI PPT，这次是真不用返工了** — [qbitai](https://www.qbitai.com/2026/05/413296.html)
- **香蕉和GPT Image之外的第3条路：华人15人团队造出AI生图黑马** — [qbitai](https://www.qbitai.com/2026/05/413264.html)
- **腾讯等入股机器人灵巧手研发商临界点** — [36kr](https://36kr.com/newsflashes/3798889072663809?f=rss)
- **苹果高价买“芯”：MacBook Neo生产目标提高至1000万台** — [36kr](https://36kr.com/newsflashes/3798867347135491?f=rss)
- **对话孙来春：年入25亿的林清轩不想做中国欧莱雅 ｜厚雪专访** — [36kr](https://36kr.com/p/3797662460419337?f=rss)
- **斯坦福博士后创立的柔性触觉传感器公司获超亿元融资，低成本触觉手套将量产落地｜硬氪首发** — [36kr](https://36kr.com/p/3797155747748867?f=rss)
- **像素绽放PixelBloom完成C轮融资，全面发力AI办公解决方案Agent：从“一分钟生成PPT”到“交付商用级结果”** — [36kr](https://36kr.com/p/3797787228151048?f=rss)
- **8点1氪丨三星宣布停止在中国大陆市场销售所有家电产品；李嘉诚抛售资产套现约455亿；月之暗面将完成20亿美元新融资，估值破200亿美元** — [36kr](https://36kr.com/p/3798462137637892?f=rss)
- **氪星晚报｜三星电子借AI热潮市值突破1万亿美元；智源发布业内首个心脏磁共振多模态诊断智能体BAAI Cardiac Agent；财政部今年将在香港发行840亿元人民币国债** — [36kr](https://36kr.com/p/3797482256325888?f=rss)
- **“鹰瞰智翼”完成Pre-A轮数千万元融资** — [36kr](https://36kr.com/newsflashes/3798919451712776?f=rss)