# AI Daily Digest [AI 安全] - 2026-04-25

# Daily Thematic Digest: AI Safety, Alignment, Security, Privacy, and Governance
**Date:** 2026-04-25
**Theme:** AI Safety, Alignment, Security, Privacy, and Governance

## Highlights

Three academic developments stand out for their potential to reshape the safety landscape this week. First, **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models** introduces a novel attack vector that exploits the stateless nature of moderation in multi-turn interactions, marking a significant departure from conventional jailbreak methods that rely on maintaining adversarial context. Second, **Breaking Bad: Interpretability-Based Safety Audits of State-of-the-Art LLMs** demonstrates the efficacy of mechanistic interpretability tools, such as Universal Steering and Representation Engineering, in systematically uncovering vulnerabilities in SOTA open-source models, moving beyond black-box probing. Third, **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies** proposes a structural solution to the "unlearning" problem, decoupling personal data from shared weights to enable deterministic user data removal without retraining.

## Adversarial Attacks and Robustness

The frontier of adversarial robustness is shifting from static prompt manipulation to dynamic, multi-stage exploitation of system architecture. The most pressing concern this week is the emergence of stateless attack vectors. In **Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models**, the authors report that adversarial intent can be distributed across isolated interactions, evading policy enforcement that typically monitors single-turn context. This contrasts with traditional jailbreaks that depend on maintaining a coherent adversarial narrative; instead, TTI leverages automated attacker agents to iteratively test and evade moderation. This finding complements **Cross-Session Threats in AI Agents: Benchmark, Evaluation, and Algorithms**, which identifies that guardrails are often memoryless, allowing adversaries to spread attacks across dozens of sessions where only the aggregate carries the payload.

Physical and hardware-layer security remains a critical vulnerability surface. **Adversarial Robustness of Near-Field Millimeter-Wave Imaging under Waveform-Domain Attacks** presents a systematic study of mmWave imaging algorithms, proposing a differential imaging attack framework that manipulates the image reconstruction process directly. Similarly, **Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles** investigates whether attackers can bypass Multi-Sensor Fusion (MSF) redundancy by fabricating cross-sensor consistency. These works suggest that redundancy, often assumed to be a safety net, can be exploited if the fusion process itself is vulnerable to coordinated data-level attacks.

In the realm of malware and software security, **Adversarial Evasion in Non-Stationary Malware Detection: Minimizing Drift Signals through Similarity-Constrained Perturbations** addresses the challenge of generating adversarial malware that evades classification while remaining inconspicuous to drift monitoring mechanisms. This is further contextualized by **CrossCommitVuln-Bench: A Dataset of Multi-Commit Python Vulnerabilities Invisible to Per-Commit Static Analysis**, which reveals that per-commit detection rates for multi-commit vulnerabilities are critically low (13%), highlighting a gap in current static analysis tools.

## Alignment, Interpretability, and Governance

Theoretical alignment research is grappling with the gap between user intent and model execution. **Alignment has a Fantasia Problem** argues that modern AI assistants treat prompts as complete expressions of intent, failing to account for users whose goals are not fully formed. This necessitates a rethinking of alignment research to handle "Fantasia interactions" where the user's needs are implicit rather than explicit. This theoretical challenge is mirrored in **Measuring Opinion Bias and Sycophancy via LLM-based Coercion**, which finds that models may concede opposite positions once a user argues one side, suggesting that eliciting a model's true position is harder than it appears due to evasive disclaimers and adversarial adaptation.

Interpretability is increasingly being operationalized as a safety audit tool. **Breaking Bad: Interpretability-Based Safety Audits of State-of-the-Art LLMs** presents a comprehensive audit of eight SOTA open-source LLMs using Universal Steering and Representation Engineering. The authors report identifying optimal activation-steering coefficients through an adaptive two-stage grid search, demonstrating that interpretability-driven approaches can systematically uncover vulnerabilities rooted in model internals. This moves beyond the limitations of black-box probing described in **Verifying Machine Learning Interpretability Requirements through Provenance**, which notes that interpretability remains an immeasurable requirement in ML Engineering.

Governance frameworks are attempting to quantify risk. **Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation** addresses the regulatory vacuum where frameworks like the EU AI Act demand safety but lack quantitative definitions of "acceptable risk." The authors propose a statistical certification framework to verify that deployed systems meet thresholds, contrasting with current practices that rely on qualitative compliance. This aligns with **Fairness under uncertainty in sequential decisions**, which argues that algorithmic approaches alone cannot resolve structural inequalities but can support socio-technical decision systems by surfacing discriminatory biases.

## Privacy Protection and Federated Learning

Privacy-preserving machine learning continues to evolve from theoretical guarantees to practical utility. **Differentially Private De-identification of Dutch Clinical Notes: A Comparative Evaluation** compares automated text de-identification pipelines, noting that while Named Entity Recognition (NER) is common, methods based on differential privacy (DP) provide formal guarantees. This is expanded in **Benchmarking the Utility of Privacy-Preserving Cox Regression Under Data-Driven Clipping Bounds: A Multi-Dataset Simulation Study**, which systematically evaluates DP mechanisms on survival analyses, finding that data-driven clipping bounds impact utility differently across datasets.

A significant methodological shift is proposed in **Differentially Private Model Merging**, which aims to generate models satisfying any target DP requirement without additional training steps. The authors propose post-processing techniques, namely random selection and linear combination, to output a final private model for any target privacy parameter. This complements **Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies**, which decouples personal data from shared weights. Evaluation on Phi-3.5-mini and Llama-3.1-8B confirms per-user differentiation where personal data influences outputs while remaining deletable via proxy artefacts, addressing the computational infeasibility of individual data removal in shared weights.

## Agent Security and Governance

As agentic systems become more prevalent, the security surface expands beyond the model to the tool ecosystem. **MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks** presents a protocol-aware security testing framework that operationalizes developer pitfalls as reproducible scenarios. This is critical given **Breaking MCP with Function Hijacking Attacks: Novel Threats for Function Calling and Agentic Models**, which shows that function calling interfaces introduce vulnerabilities via data tampering and theft. These findings are supported by **Black-Box Skill Stealing Attack from Proprietary LLM Agents: An Empirical Study**, which identifies a new attack surface in the "skill economy" where adversaries can extract hidden prompts from public agents.

Contextual integrity in enterprise settings is a major concern. **CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents** introduces a Contextual Integrity (CI)-grounded benchmark that evaluates whether agents can convey essential content while withholding sensitive context. The authors report that privacy failures are prevalent, with violation rates ranging from 15.8% to higher levels depending on the model. This highlights the need for tools like **AVISE: Framework for Evaluating the Security of AI Systems**, a modular open-source framework for identifying vulnerabilities in AI systems, and **Auto-ART: Structured Literature Synthesis and Automated Adversarial Robustness Testing**, which operationalizes identified gaps with 50+ attacks and 28 defense modules.

## Industry Context and Open Source

In the broader industry landscape, capability scaling continues to outpace safety infrastructure. DeepSeek's technical report (qbitai.com/2026/04/406809) details V4's 484-day development cycle, including its expanded context window capabilities, which necessitate rigorous testing of stateless vulnerabilities like TTI. Meanwhile, Google's planned $40B investment in Anthropic (techcrunch.com/2026/04/24/google-to-invest-up-to-40b-in-anthropic-in-cash-and-compute/) underscores the race for compute capacity, with potential implications for safety resource allocation.

Open-source tooling is responding to these threats. **AVISE** and **Auto-ART** provide foundational frameworks for security evaluation. In the agent space, **MCP Pitfall Lab** offers specific guidance for tool server security. Additionally, **sjsyrek/design-council** and **heider-x/vela** represent community efforts to create peer-debate mechanisms and privacy-first IDEs, respectively. These tools are essential for practitioners seeking to audit their systems beyond standard benchmarks.

## Looking Forward

Four key challenges emerge from this week's research:
1. The efficacy of stateless attacks like TTI against future models with persistent memory requires validation, particularly given DeepSeek V4's expanded context capabilities.
2. The "Fantasia Problem" suggests alignment metrics based on prompt adherence may be insufficient; future research must quantify alignment with unformed user intent.
3. Differential privacy utility-statistical power tradeoffs in sequential decision-making (as seen in Cox regression studies) need optimization for high-stakes domains.
4. Regulatory frameworks must bridge the gap between qualitative compliance and quantitative certification, as proposed in **Bounding the Black Box**, to operationalize "acceptable risk."

---

## References

[Identical to original references section]