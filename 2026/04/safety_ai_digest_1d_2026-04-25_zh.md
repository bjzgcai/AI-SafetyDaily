# AI 日报 [AI 安全] - 2026-04-25

# AI Safety Thematic Digest  
**Date:** 2026-04-25  
**Theme:** AI Safety, Alignment, Security, Privacy, and Governance  
**Author:** Senior AI Safety Researcher  

## Highlights  

今日安全研究领域的核心进展集中在**多轮对话状态漏洞利用**、**隐私保护下的模型合并技术**以及**Agent 系统性的安全评估框架**三个方向。  

1.  **多轮攻击新范式**：[**Transient Turn Injection: Exposing Stateless Multi-Turn Vulnerabilities in Large Language Models**] 提出了一种利用模型无状态特性的新型攻击方法 TTI，揭示了当前基于单轮检测的防御机制在长上下文交互中的失效风险。  
2.  **隐私计算新路径**：[**Differentially Private Model Merging**] 与 [**Separable Expert Architecture: Toward Privacy-Preserving LLM Personalization via Composable Adapters and Deletable User Proxies**] 分别从模型合并与架构解耦角度，提出了满足差分隐私要求及实现用户数据可删除性的方案。  
3.  **Agent 安全基准化**：[**MCP Pitfall Lab: Exposing Developer Pitfalls in MCP Tool Server Security under Multi-Vector Attacks**] 与 [**AVISE: Framework for Evaluating the Security of AI Systems**] 等开源框架的发布，填补了工具调用与跨会话攻击的评估空白。  

---  

## 对抗攻击与鲁棒性：从单轮对抗到状态利用  

[**Transient Turn Injection**] 指出攻击者可通过 TTI 技术将恶意意图分散在多个无状态的对话回合中，从而绕过基于上下文的审核。这与 [**Stealthy Backdoor Attacks against LLMs Based on Natural Style Triggers**] 中提出的自然风格触发器形成互补，表明静态防御已不足以应对动态交互威胁。  

在物理世界领域，[**Cross-Modal Phantom: Coordinated Camera-LiDAR Spoofing Against Multi-Sensor Fusion in Autonomous Vehicles**] 揭示了多传感器融合中的潜在漏洞。针对上述威胁，[**Auto-ART: Structured Literature Synthesis and Automated Adversarial Robustness Testing**] 提供了系统化的防御视角，但尚未完全覆盖长上下文状态利用场景。  

## 模型对齐与可解释性：意图理解与内部机制审计  

对齐研究正从“指令遵循”向“意图形成”转变。[**Alignment has a Fantasia Problem**] 提出用户目标往往未成形，可能导致模型偏离真实需求。这与 [**Measuring Opinion Bias and Sycophancy via LLM-based Coercion**] 中模型立场摇摆的发现相互印证。  

可解释性方面，[**Breaking Bad: Interpretability-Based Safety Audits of State-of-the-Art LLMs**] 展示了基于解释性的审计方法，而 [**Reasoning Primitives in Hybrid and Non-Hybrid LLMs**] 则关注内部推理机制的透明性问题。  

## 隐私保护与数据治理：从差分隐私到架构解耦  

[**Differentially Private De-identification of Dutch Clinical Notes**] 评估了基于差分隐私的文本脱敏方法，但 [**Benchmarking the Utility of Privacy-Preserving Cox Regression**] 指出 DP 在生存分析中的效用损失问题。  

模型层面，[**Differentially Private Model Merging**] 提出后处理技术，而 [**Separable Expert Architecture**] 通过三层架构实现数据确定性删除。监管方面，[**Bounding the Black Box: A Statistical Certification Framework for AI Risk Regulation**] 试图量化“可接受风险”。  

## Agent 安全与治理：工具调用与跨会话威胁  

[**MCP Pitfall Lab**] 揭示了工具元数据与供应链中的多重风险。[**Cross-Session Threats in AI Agents**] 指出当前护栏多为无状态，攻击者可跨会话累积恶意意图。针对此，[**Polaris: A Transaction-Driven AI Software Factory Kernel**] 提出事务驱动的 Agent 内核架构。  

[**CI-Work: Benchmarking Contextual Integrity in Enterprise LLM Agents**] 显示企业级 Agent 的隐私违规率达 15.8%-30%，与 [**Black-Box Skill Stealing Attack from Proprietary LLM Agents**] 中技能窃取风险形成关联。  

## 安全评估基准与工具  

[**AVISE**] 扩展了基于心智理论的 Red Queen 攻击，[**Auto-ART**] 提供鲁棒性评估。[**MathDuels**] 提出自我博弈基准，[**AUDITA**] 构建音频问答基准。[**CrossCommitVuln-Bench**] 关注代码安全中的跨 Commit 漏洞。  

---  

## Looking Forward  

尽管上述工作在多个维度取得了进展，但以下理论问题与假设仍需进一步验证：  

1.  **多轮状态利用的理论边界**：需量化 Agent 记忆长度与攻击面之间的数学关系。  
2.  **隐私与效用的动态平衡**：如何在保证形式化隐私的同时维持复杂任务的统计效用。  
3.  **Agent 意图对齐的量化**：目前缺乏评估模型是否理解用户未成形目标的可量化指标。  
4.  **跨模态攻击的防御协同**：需建立跨传感器与跨模态攻击的统一防御框架。  

---  

## 参考来源  

（保持原参考文献列表完全不变，包括顺序、标题和链接）