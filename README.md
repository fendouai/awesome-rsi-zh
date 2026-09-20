# Awesome RSI（递归自我改进）中文版 [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 递归自我改进（Recursive Self-Improvement，简称 RSI）指 AI 系统改进自身能力、并且能够同时改进「产生后续改进的机制」的过程。

近期在自我训练（self-training）、智能体记忆（agent memory）、执行外壳优化（harness optimization）、具身自我改进（embodied self-improvement）、自动化 AI 研究（automated AI research）、自我修改的编码智能体（self-modifying coding agents）以及进化搜索（evolutionary search）等方向的进展，使 RSI 日益成为一个实证研究领域，而不再只是理论构想。

本项目是 [lobehub/awesome-rsi](https://github.com/lobehub/awesome-rsi) 的**中文版**，并在此基础之上**增补了大量中文资源与近年新工作**，力求比原版更全面、更适合中文读者。它系统性地收集并整理了 RSI 相关的重要工作，涵盖模型层级的自我改进、上下文与记忆进化、执行外壳与脚手架进化、具身与物理自我改进、多智能体系统、自动化 AI 研发、基准测试以及安全等多个方向。

除 lobehub 版本外，本清单还交叉检索了 [theseus-labs-rsi/awesome-rsi](https://github.com/theseus-labs-rsi/awesome-rsi)、[pinkbubblebubble/awesome-rsi](https://github.com/pinkbubblebubble/awesome-rsi)、[Liuziyu77/Awesome-RSI](https://github.com/Liuziyu77/Awesome-RSI)、[Picrew/awesome-rsi](https://github.com/Picrew/awesome-rsi)、[asimfish/awesome_rsi](https://github.com/asimfish/awesome_rsi) 等多份同类清单，把其中被反复收录、但原版尚未涵盖的工作补入对应章节（尤其集中在 2026 年的执行外壳进化与技能进化方向）。这些清单的完整索引见[相关 Awesome 清单](#related-awesome-lists相关-awesome-清单)。

并非这里列出的每一项工作都在严格意义上展示了 RSI。其中一部分属于**有界自我改进**（bounded self-improvement）或支撑性技术，它们可能为更完整的递归系统作出贡献。

如果你是新手，请从「基础与入门」开始；如果你已经了解基础知识，可以直接探索与你兴趣最相关的章节。

这是一份由社区维护并持续演进的清单。欢迎贡献缺失的论文、新的基准测试、框架，以及对分类体系的改进建议。

分类体系是为了组织方便而非互斥的；许多系统跨越了多个层级和机制。

## 中英术语对照表

| 中文 | English | 说明 |
| --- | --- | --- |
| 递归自我改进 | Recursive Self-Improvement (RSI) | 改进机制本身也是改进的对象 |
| 自我精炼 | Self-refinement | 只改进当前输出，不产生持久改变 |
| 持续性自我改进 | Persistent self-improvement | 对权重/记忆/技能/提示/外壳/代码的改动延续到下一轮 |
| RSI 基底 | RSI substrate | 将智能体自身结构暴露为可修改对象 |
| 自我进化智能体 | Self-evolving agent | 通过反馈与环境持续改进自身的智能体 |
| 执行外壳 | Harness | 围绕模型的提示、工具、记忆、验证等可执行脚手架 |
| 脚手架 | Scaffold | 支撑模型运行的外部结构 |
| 自我训练 | Self-training | 用模型自生成的数据训练自身 |
| 自我奖励 | Self-reward | 模型生成并评判自己的训练数据 |
| 自我博弈 | Self-play | 模型通过与自身对抗获得反馈 |
| 合成数据 | Synthetic data | 模型生成的数据 |
| 自我蒸馏 | Self-distillation | 从自身输出中蒸馏知识 |
| 自学推理 | Self-taught reasoning | 通过自举（bootstrap）学会推理 |
| 微调 | Fine-tuning | 在预训练基础上继续训练 |
| 多智能体 | Multi-agent | 多个智能体交互协作 |
| 协同进化 | Co-evolution | 多个系统相互促进共同进化 |
| 具身智能 | Embodied AI | 与物理/仿真环境交互的智能体 |
| 对齐 | Alignment | 使 AI 行为符合人类意图 |
| 内省 | Introspection | AI 对自身行为与内部状态的建模 |
| 基准测试 | Benchmark | 衡量能力的标准化测试 |
| 自动化 AI 研发 | Automated AI R&D | AI 自动完成 AI 研究/研发流程 |

## Contents（目录）

- [Scope & Terminology（范围与术语）](#scope--terminology范围与术语)
  - [改进强度标签（Improvement-Strength Tags）](#改进强度标签improvement-strength-tags)
- [Fundamentals & Getting Started（基础与入门）](#fundamentals--getting-started基础与入门) `13`
- [Model-level RSI（模型层级的自我改进）](#model-level-rsi模型层级的自我改进)
  - [Self-Training & Self-Reward（自我训练与自我奖励）](#self-training--self-reward自我训练与自我奖励) `10`
  - [Synthetic Data & Self-Distillation（合成数据与自我蒸馏）](#synthetic-data--self-distillation合成数据与自我蒸馏) `6`
  - [Self-Play & Iterative Fine-tuning（自我博弈与迭代微调）](#self-play--iterative-fine-tuning自我博弈与迭代微调) `16`
  - [Self-Taught Reasoning（自学推理）](#self-taught-reasoning自学推理) `3`
- [Harness-level RSI（执行外壳层级的自我改进）](#harness-level-rsi执行外壳层级的自我改进)
  - [Prompt & Program Optimization（提示词与程序优化）](#prompt--program-optimization提示词与程序优化) `14`
  - [Context & Memory Evolution（上下文与记忆进化）](#context--memory-evolution上下文与记忆进化) `9`
  - [Harness & Scaffold Evolution（外壳与脚手架进化）](#harness--scaffold-evolution外壳与脚手架进化) `28`
  - [Extensible Harness Substrates（可扩展外壳基底）](#extensible-harness-substrates可扩展外壳基底) `4`
  - [Self-Verification & Self-Correction — Enabling Foundations（自我验证与自我纠错——支撑基础）](#self-verification--self-correction--enabling-foundations自我验证与自我纠错支撑基础) `6`
  - [Self-Evolving Agent Frameworks（自我进化的智能体框架）](#self-evolving-agent-frameworks自我进化的智能体框架) `14`
- [Multi-Agent Self-Improvement（多智能体自我改进）](#multi-agent-self-improvement多智能体自我改进)
  - [Co-Evolution（协同进化）](#co-evolution协同进化) `9`
  - [Inference-time Debate（推理时辩论）](#inference-time-debate推理时辩论) `2`
- [Coding / Software-Engineering Self-Improvement（编码 / 软件工程自我改进）](#coding--software-engineering-self-improvement编码--软件工程自我改进)
  - [Self-Modifying Coding Agents（自我修改的编码智能体）](#self-modifying-coding-agents自我修改的编码智能体) `7`
  - [Iterative Repair & Training（迭代修复与训练）](#iterative-repair--training迭代修复与训练) `3`
- [Automated AI R&D（自动化 AI 研发）](#automated-ai-rd自动化-ai-研发) `13`
- [Embodied & Physical Self-Improvement（具身与物理自我改进）](#embodied--physical-self-improvement具身与物理自我改进) `9`
- [Evolutionary & Open-Ended RSI（进化式与开放式 RSI）](#evolutionary--open-ended-rsi进化式与开放式-rsi) `12`
- [Safety, Alignment & Theory（安全、对齐与理论）](#safety-alignment--theory安全对齐与理论) `15`
  - [Supporting Safety Foundations（支撑性安全基础）](#supporting-safety-foundations支撑性安全基础) `9`
- [Introspection & Self-Modeling（内省与自我建模）](#introspection--self-modeling内省与自我建模) `10`
- [Benchmarks & Evaluations（基准测试与评估）](#benchmarks--evaluations基准测试与评估)
  - [Direct RSI & Self-Improvement Evaluations（直接 RSI 与自我改进评估）](#direct-rsi--self-improvement-evaluations直接-rsi-与自我改进评估) `8`
  - [Frontier Lab Self-Improvement & AI R&D Evaluation Frameworks（前沿实验室自我改进与 AI 研发评估框架）](#frontier-lab-self-improvement--ai-rd-evaluation-frameworks前沿实验室自我改进与-ai-研发评估框架) `3`
  - [AI R&D Capability Proxies（AI 研发能力代理指标）](#ai-rd-capability-proxiesai-研发能力代理指标) `8`
  - [Agent Capability Proxies（智能体能力代理指标）](#agent-capability-proxies智能体能力代理指标) `9`
- [Frameworks & Tools（框架与工具）](#frameworks--tools框架与工具)
  - [Self-Modifying / Self-Evolving Systems（自我修改 / 自我进化系统）](#self-modifying--self-evolving-systems自我修改--自我进化系统) `14`
  - [Harness / Memory / Skill Evolution（外壳 / 记忆 / 技能进化）](#harness--memory--skill-evolution外壳--记忆--技能进化) `11`
  - [Automated Search / AI R&D（自动化搜索 / AI 研发）](#automated-search--ai-rd自动化搜索--ai-研发) `9`
- [Chinese Resources（中文资源）](#chinese-resources中文资源)
- [Blog Posts & Discussions（博客文章与讨论）](#blog-posts--discussions博客文章与讨论)
- [Talks & Videos（演讲与视频）](#talks--videos演讲与视频)
- [Related Awesome Lists（相关 Awesome 清单）](#related-awesome-lists相关-awesome-清单)
  - [RSI 专题清单（RSI-focused Awesome Lists）](#rsi-专题清单rsi-focused-awesome-lists)
  - [相邻清单（Adjacent Awesome Lists）](#相邻清单adjacent-awesome-lists)
- [按改进强度索引（Index by Improvement Strength）](#按改进强度索引index-by-improvement-strength)
- [Contributing（贡献指南）](#contributing贡献指南)

## Scope & Terminology（范围与术语）

在本清单中，我们使用以下操作性区分：

**自我精炼（Self-refinement）** —— 改进当前输出，但不对系统产生持久性改变。

**持续性自我改进（Persistent self-improvement）** —— 对权重、记忆、技能、提示词、执行外壳或代码的改动，会延续到下一轮。

**递归自我改进（Recursive self-improvement）** —— 产生改进的机制本身也是被改进的对象。

**RSI 基底（RSI substrate）** —— 将智能体自身的结构暴露为可修改对象，但未必默认形成自动的自我改进循环。

### 改进强度标签（Improvement-Strength Tags）

为了让读者不必自行判断「这条到底算不算 RSI」，本清单为每条工作标注了**改进强度**。三档与上文术语一一对应：

| 标签 | 判据 | 对应术语 |
| --- | --- | --- |
| `` `真递归` `` | 被改进的对象**包含产生改进的机制本身**（改进器、判据、外壳进化器、搜索策略） | 递归自我改进 |
| `` `持久改进` `` | 对权重、记忆、技能、外壳或代码的改动**被后续轮次继承**，但改进算子固定 | 持续性自我改进 |
| `` `支撑技术` `` | 不产生持久改变，或本身不改进系统，为上述提供验证、评测、理论、安全与基础设施（含仅改进当前输出的自我精炼） | 自我精炼 / RSI 基底 |

判定约定：

- 只改进当前输出的工作（如 Self-Refine、CoVe、Self-Consistency）记为 `` `支撑技术` ``。
- 评测、基准、安全、内省、综述与理论工作记为 `` `支撑技术` ``。
- 暴露可修改面但**默认不自动改进**的运行时基底记为 `` `支撑技术` ``。
- 自动化科研但**不改进自身**的系统记为 `` `支撑技术` ``。
- 各小节内的条目按年份倒序排列（同年前后按 arXiv 编号倒序），最近的工作在前。
- 中文资源、博客、演讲视频与相关清单四类章节为二手解读，不打标签。

按改进强度重新分组的完整索引见[按改进强度索引](#按改进强度索引index-by-improvement-strength)。

## Fundamentals & Getting Started（基础与入门）

奠定 RSI 词汇表与核心问题的基础论文、形式化处理与综述。

- [Self-Improvements in Modern Agentic Systems: A Survey](https://arxiv.org/abs/2607.13104) - 从系统级视角统一基础模型与脚手架更新的自我改进智能体。 (arXiv 2026) `支撑技术`
- [Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops](https://arxiv.org/abs/2607.07663) - 按更新目标与闭环程度综述近期自我改进工作，将有界精炼与开放式 RSI 区分开来。 (arXiv 2026) `支撑技术`
- [Self-evolving Embodied AI](https://arxiv.org/abs/2602.04411) - 定义了自我进化具身 AI 范式，覆盖记忆自更新、任务自切换、环境自预测、具身自适应与模型自进化。 (arXiv 2026) `支撑技术`
- [A Survey of Self-Evolving Agents: On Path to Artificial Super Intelligence](https://arxiv.org/abs/2507.21046) - 系统综述了基础模型智能体在模型、记忆、工具与架构等维度「进化什么、何时进化、如何进化」。 (TMLR 2026) `支撑技术`
- [A Comprehensive Survey of Self-Evolving AI Agents: A New Paradigm Bridging Foundation Models and Lifelong Agentic Systems](https://arxiv.org/abs/2508.07407) - 围绕反馈回路、更新目标、领域应用、评估与安全组织智能体进化。 (arXiv 2025) `支撑技术`
- [A Survey on Self-Evolution of Large Language Models](https://arxiv.org/abs/2404.14387) - 提出「经验获取—精炼—更新—评估」四阶段自我进化 LLM 分类法。 (arXiv 2024) `支撑技术`
- [A Formulation of Recursive Self-Improvement and Its Possible Efficiency](https://arxiv.org/abs/1805.06610) - 给出受限 RSI 系统的形式化定义，并分析高效递归改进在何时可计算。 (arXiv 2018) `支撑技术`
- [From Seed AI to Technological Singularity via Recursively Self-Improving Software](https://arxiv.org/abs/1502.06512) - 定义 RSI 软件，综述既有方法，提出收敛概念与计算极限。 (arXiv 2015) `支撑技术`
- [The Singularity: A Philosophical Analysis](https://consc.net/papers/singularity.pdf) - 为智能爆炸（intelligence explosion）建立严格的哲学论证，并检视其假设与后果。 (Journal of Consciousness Studies 2010) `支撑技术`
- [Gödel Machines: Self-Referential Universal Problem Solvers Making Provably Optimal Self-Improvements](https://arxiv.org/abs/cs/0309048) - 定义完全自指的机器，它在「证明某项修改能提升期望效用」后重写自身。 (Artificial General Intelligence book 2006) `真递归`
- [Optimal Ordered Problem Solver](https://arxiv.org/abs/cs/0207097) - 引入渐近最优的程序搜索系统，复用已有解来加速后续求解。 (Machine Learning 2004) `支撑技术`
- [Evolutionary Principles in Self-Referential Learning, or on Learning How to Learn: The Meta-Meta-... Hook](https://people.idsia.ch/~juergen/diploma1987ocr.pdf) - 描述递归改进学习方法的早期元进化与自指学习机制。 (Diploma thesis 1987) `支撑技术`
- [Speculations Concerning the First Ultraintelligent Machine](https://www.sciencedirect.com/science/article/pii/S0065245808604180) - 提出智能爆炸论证：能够改进机器设计的机器将触发加速的能力增长。 (Advances in Computers 1965) `支撑技术`

## Model-level RSI（模型层级的自我改进）

通过自我生成的反馈、数据或推理来改进模型权重或训练行为的方法，包括后来被复用于持续性自我改进循环的经典支撑性方法。

### Self-Training & Self-Reward（自我训练与自我奖励）

- [EvoLM: Self-Evolving Language Models through Co-Evolved Discriminative Rubrics](https://arxiv.org/abs/2605.03871) - 交替训练一个模型生成判别性评分标准（rubric），并在基于该标准的奖励下改进自身策略，无需人类标注或外部奖励模型。 (arXiv 2026) `持久改进`
- [TTRL: Test-Time Reinforcement Learning](https://arxiv.org/abs/2504.16084) - 在无标注测试数据上用多数投票等共识信号构造奖励，直接更新模型权重，把「测试时自我强化」变成一次参数级自我改进。 (arXiv 2025) `持久改进`
- [DeepSeek-GRM: Inference-Time Scaling for Generalist Reward Modeling](https://arxiv.org/abs/2504.02495) - 提出「生成式打分员」架构与 SPCT（Self-Principled Critique Tuning），让奖励模型也具备推理时扩展能力，是「自我改进的评判者」方向的关键工作。 (arXiv 2025) ★中文团队 `持久改进`
- [DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning](https://arxiv.org/abs/2501.12948) - 通过大规模强化学习（GRPO）无需监督微调冷启动即可让模型自我进化出推理能力，涌现出「反思」「顿悟时刻」等自发生行为。 (arXiv 2025) ★中文团队 `持久改进`
- [Self-Taught Evaluators](https://arxiv.org/abs/2408.02666) - 在没有任何人工偏好标注的情况下，让模型自举出评估器并用它生成偏好数据，再据此改进自身。 (arXiv 2024) `持久改进`
- [ReST-MCTS*: LLM Self-Training via Process Reward Guided Tree Search](https://arxiv.org/abs/2406.03816) - 用过程奖励引导的树搜索生成高质量推理轨迹，并以其作为自我训练数据。 (NeurIPS 2024) `持久改进`
- [Self-Rewarding Language Models](https://arxiv.org/abs/2401.10020) - 训练语言模型在重复的对齐轮次中生成并评判自己的指令遵循数据。 (ICML 2024) `持久改进`
- [Self-Play Fine-Tuning Converts Weak Language Models to Strong Language Models](https://arxiv.org/abs/2401.01335) - 通过自我博弈偏好学习迭代改进单一语言模型，无需额外人类标注。 (ICML 2024) `持久改进`
- [RLAIF vs. RLHF: Scaling Reinforcement Learning from Human Feedback with AI Feedback](https://arxiv.org/abs/2309.00267) - 研究以 AI 生成的偏好作为人类反馈的可扩展替代方案。 (ICML 2024) `持久改进`
- [Reinforced Self-Training (ReST) for Language Modeling](https://arxiv.org/abs/2308.08998) - 交替执行「用当前策略生成样本—按奖励过滤—离线训练」，是自我训练循环的经典范式，也是后续 RSI 训练的常见骨架。 (arXiv 2023) `持久改进`

### Synthetic Data & Self-Distillation（合成数据与自我蒸馏）

- [Recursive Synthesis for Long-Horizon Terminal Tasks](https://arxiv.org/abs/2608.05466) - 将已接受任务作为下一轮的种子，生成越来越难的终端任务用于 SFT 与 PPO。 (arXiv 2026) `持久改进`
- [Qwen2.5-Math Technical Report: Toward Mathematical Expert Model Via Self-Improvement](https://arxiv.org/abs/2409.12122) - 通过「SFT 模型与奖励模型交互迭代」的多轮自我改进流程构建数学专家模型。 (arXiv 2024) ★中文团队 `持久改进`
- [Beyond Human Data: Scaling Self-Training for Problem-Solving with Language Models](https://arxiv.org/abs/2312.06585) - 迭代采样、过滤并用模型生成的解重新训练，使自我训练超越人类示范。 (TMLR 2024) `持久改进`
- [Self-Alignment with Instruction Backtranslation](https://arxiv.org/abs/2308.06259) - 为未标注的模型写作生成指令，并在合成指令-响应对上微调。 (ICLR 2024) `持久改进`
- [Self-Instruct: Aligning Language Models with Self-Generated Instructions](https://arxiv.org/abs/2212.10560) - 从模型自身生成中自举指令遵循数据，并在微调前过滤。 (ACL 2023) `持久改进`
- [Large Language Models Can Self-Improve](https://arxiv.org/abs/2210.11610) - 使用高置信度模型生成答案作为伪标签，对推理任务进行迭代微调。 (EMNLP 2023) `持久改进`

### Self-Play & Iterative Fine-tuning（自我博弈与迭代微调）

- [SPADE: Self-Play in Adaptive Synthetic Executable Environments](https://arxiv.org/abs/2608.19197) - 单一 LLM 分饰「环境设计者」与「推理智能体」：设计者依据预训练文档编写可执行 Gym 风格环境，智能体的遗憾信号反过来驱动环境持续进化。 (arXiv 2026) `持久改进`
- [SERPO: Self-Evolving Rubric Policy Optimization for Open-Ended Test-Time Reinforcement Learning](https://arxiv.org/abs/2607.26873) - 在闭环测试时强化学习循环中协同进化响应证据、任务专属评分标准与策略参数。 (arXiv 2026) `持久改进`
- [Teaching LLMs to Self-Evolve: Cultivating Core Meta-Skills with Reinforcement Learning](https://arxiv.org/abs/2607.21971) - 先训练 MetaEvolve 的反思与反馈驱动精炼技能，再将推理时进化搜索用于开放式优化。 (arXiv 2026) `持久改进`
- [G-Zero: Self-Play for Open-Ended Generation from Zero Data](https://arxiv.org/abs/2605.09959) - 用「提示诱导的概率位移」作为内在训练信号，协同进化出题者与生成者，实现零数据条件下的开放式生成自我提升。 (arXiv 2026) `持久改进`
- [TEMPO: Scaling Test-time Training for Large Reasoning Models](https://arxiv.org/abs/2604.19295) - 在未标注测试题上更新模型参数，并用标注数据定期校准评判器，以维持测试时改进。 (arXiv 2026) `持久改进`
- [Learning to Self-Evolve](https://arxiv.org/abs/2603.18620) - 用强化学习教会模型如何编辑自己的上下文，以在后续任务上表现更强。 (arXiv 2026) `持久改进`
- [SkillRL: Evolving Agents via Recursive Skill-Augmented Reinforcement Learning](https://arxiv.org/abs/2602.08234) - 让分层技能库与智能体策略的强化学习联合进化，技能随策略提升而递归重构。 (arXiv 2026) `持久改进`
- [R-Zero: Self-Evolving Reasoning LLM from Zero Data](https://arxiv.org/abs/2508.05004) - 协同进化 Challenger 与 Solver，用自生成难题与估计的学习难度形成课程，无需任何种子任务或标签。 (ICLR 2026) `持久改进`
- [R-FEW: Guided Self-Evolving LLMs with Minimal Human Supervision](https://arxiv.org/abs/2512.02472) - 通过少量人类「锚点」数据引导自我博弈 Challenger–Solver 框架，缓解概念漂移与多样性坍缩。 (arXiv 2025) `持久改进`
- [Self-Adapting Language Models](https://arxiv.org/abs/2506.10943) - 提出 SEAL，模型生成自己的更新数据与微调指令，以适配新任务。 (NeurIPS 2025) `持久改进`
- [Absolute Zero: Reinforced Self-play Reasoning with Zero Data](https://arxiv.org/abs/2505.03335) - 通过可执行、可验证的自我博弈同时训练「出题」与「解题」能力，完全不依赖人工策划的后训练问题集。 (NeurIPS 2025) `持久改进`
- [Cognitive Behaviors that Enable Self-Improving Reasoners, or, Four Habits of Highly Effective STaRs](https://arxiv.org/abs/2503.01307) - 揭示「验证、回溯、子目标设定、逆向推理」等初始认知行为是模型能否在 RL 中自我改进的关键。 (arXiv 2025) `支撑技术`
- [Self-Improvement in Language Models: The Sharpening Mechanism](https://arxiv.org/abs/2412.01951) - 将自我改进形式化为「把验证器引导的搜索摊销进更锐利的后训练策略」。 (ICLR 2025) `支撑技术`
- [Meta-Rewarding Language Models: Self-Improving Alignment with LLM-as-a-Meta-Judge](https://arxiv.org/abs/2407.19594) - 让语言模型评判自己的评判，并迭代改进评估与指令遵循能力。 (EMNLP 2025) `持久改进`
- [Self-Play Preference Optimization for Language Model Alignment](https://arxiv.org/abs/2405.00675) - 将对齐框架化为双人博弈，迭代将策略推向偏好模型纳什均衡。 (ICLR 2025) `持久改进`
- [SELF: Self-Evolution with Language Feedback](https://arxiv.org/abs/2310.00533) - 重复「自我反馈—响应精炼—过滤—微调」，使 LLM 在未标注指令上逐步改进。 (arXiv 2023) `持久改进`

### Self-Taught Reasoning（自学推理）

- [rStar-Math: Small LLMs Can Master Math Reasoning with Self-Evolved Deep Thinking](https://arxiv.org/abs/2501.04519) - 将蒙特卡洛树搜索与自我进化训练数据、过程偏好模型结合，改进数学推理。 (ICML 2025) `持久改进`
- [Quiet-STaR: Language Models Can Teach Themselves to Think Before Speaking](https://arxiv.org/abs/2403.09629) - 训练语言模型在任意文本中生成有用的内部推理，而非仅限问答任务。 (COLM 2024) `持久改进`
- [STaR: Bootstrapping Reasoning With Reasoning](https://arxiv.org/abs/2203.14465) - 交替进行「理由生成—答案过滤—合理化—微调」来自举推理能力。 (NeurIPS 2022) `持久改进`

## Harness-level RSI（执行外壳层级的自我改进）

改进模型周围的提示词、记忆、验证、工具或智能体策略的方法。

### Prompt & Program Optimization（提示词与程序优化）

- [GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning](https://arxiv.org/abs/2507.19457) - 用执行反馈与自然语言反思进化提示词，并以 Pareto 式选择保留互补候选；在若干任务上以远少于 GRPO 的 rollout 次数超过强化学习。 (ICLR 2026 Oral) `持久改进`
- [Adaptive Self-Improvement for ML Library Development](https://arxiv.org/abs/2502.02534) - 让智能体系统针对 ML 库开发这类长程任务，自我改进其程序生成与验证策略。 (arXiv 2025) `持久改进`
- [AFlow: Automating Agentic Workflow Generation](https://arxiv.org/abs/2410.10762) - 把智能体工作流表示为代码，用蒙特卡洛树搜索在可执行空间中搜索并迭代改进工作流本身。 (ICLR 2025) `持久改进`
- [Automated Design of Agentic Systems](https://arxiv.org/abs/2408.08435) - 使用元智能体发明并迭代改进以可执行代码表示的智能体架构。 (ICLR 2025) `持久改进`
- [TextGrad: Automatic "Differentiation" via Text](https://arxiv.org/abs/2406.07496) - 通过复合 AI 系统反向传播文本反馈，优化提示词、代码等文本变量。 (Nature 2025) `持久改进`
- [Language Agent Tree Search Unifies Reasoning, Acting, and Planning in Language Models](https://arxiv.org/abs/2310.04406) - 结合蒙特卡洛树搜索、基于模型的价值估计、环境反馈与自我反思，且不更新基座权重。 (ICML 2024) `支撑技术`
- [Self-Taught Optimizer (STOP): Recursively Self-Improving Code Generation](https://arxiv.org/abs/2310.02304) - 展示一个 LLM 编写的脚手架程序改进了「负责产生进一步改进的程序」。 (COLM 2024) `真递归`
- [Promptbreeder: Self-Referential Self-Improvement Via Prompt Evolution](https://arxiv.org/abs/2309.16797) - 同时进化任务提示词与生成未来提示改进的变异提示词。 (ICML 2024) `真递归`
- [Large Language Models as Optimizers](https://arxiv.org/abs/2309.03409) - 提出 OPRO，从评分尝试的历史中迭代提出并评估自然语言解与提示词。 (ICLR 2024) `持久改进`
- [DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines](https://arxiv.org/abs/2310.03714) - 针对用户定义的指标优化提示词与示范，编译声明式 LM 程序。 (NeurIPS 2023 R0-FoMo Workshop) `持久改进`
- [EvoPrompt: Connecting LLMs with Evolutionary Algorithms Yields Powerful Prompt Optimizers](https://arxiv.org/abs/2309.08532) - 把进化算法与 LLM 结合，用变异与交叉算子在离散提示空间迭代搜索。 (arXiv 2023) `持久改进`
- [Automatic Prompt Optimization with "Gradient Descent" and Beam Search](https://arxiv.org/abs/2305.03495) - 把自然语言反馈当作「梯度」，用束搜索在提示空间做无需访问模型参数的优化。 (EMNLP 2023) `持久改进`
- [Large Language Models Are Human-Level Prompt Engineers (APE)](https://arxiv.org/abs/2211.01910) - 让 LLM 生成候选指令再由模型自身打分筛选，性能可超过人工撰写的提示。 (ICLR 2023) `持久改进`
- [Eliciting Knowledge from Language Models Using Automatically Generated Prompts](https://arxiv.org/abs/2010.15980) - 用自动生成的提示（而非人工模板）从预训练语言模型中抽取知识，是「让模型自己写提示」的早期工作。 (EMNLP 2020) `持久改进`

### Context & Memory Evolution（上下文与记忆进化）

- [Metis: Bridging Text and Code Memory for Self-Evolving Agents](https://arxiv.org/abs/2606.24151) - 在文本记忆与代码记忆之间架桥，让自我进化智能体以更可执行的形式复用过往经验，而非只做上下文注入。 (arXiv 2026) `持久改进`
- [From Procedural Skills to Strategy Genes: Towards Experience-Driven Test-Time Evolution](https://arxiv.org/abs/2604.15097) - 在 4590 个受控试验中比较经验表示，发现紧凑可编辑的「基因」比文档导向的「技能包」提供更强的测试时控制。 (arXiv 2026) `持久改进`
- [Learning to Continually Learn via Meta-learning Agentic Memory Designs](https://arxiv.org/abs/2602.07755) - 用元智能体发现可执行的记忆模式及检索/更新机制，从经验中持续改进。 (arXiv 2026) `持久改进`
- [EvolveR: Self-Evolving LLM Agents through an Experience-Driven Lifecycle](https://arxiv.org/abs/2510.16079) - 将交互轨迹蒸馏为可复用的战略原则，在未来任务中检索，并在闭环中强化智能体策略。 (ICML 2026) `持久改进`
- [Agentic Context Engineering: Evolving Contexts for Self-Improving Language Models](https://arxiv.org/abs/2510.04618) - 通过生成、反思与策展将上下文进化为结构化「操作手册」，同时避免破坏性的上下文坍缩。 (ICLR 2026) `持久改进`
- [A-MEM: Agentic Memory for LLM Agents](https://arxiv.org/abs/2502.12110) - 构建动态链接的笔记网络，其组织随智能体积累新经验而进化。 (NeurIPS 2025) `持久改进`
- [ExpeL: LLM Agents Are Experiential Learners](https://arxiv.org/abs/2308.10144) - 从成功与失败轨迹中提取可复用洞察，无需更新权重即可迁移到未来任务。 (AAAI 2024) `持久改进`
- [MemoryBank: Enhancing Large Language Models with Long-Term Memory](https://arxiv.org/abs/2305.10250) - 维护并有选择地遗忘长期交互记忆，使智能体随时间调整响应。 (AAAI 2024) `持久改进`
- [Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366) - 通过存储从任务反馈中得出的自然语言反思来跨试验改进智能体。 (NeurIPS 2023) `持久改进`

### Harness & Scaffold Evolution（外壳与脚手架进化）

- [WikiSkill: Compiling Agent Experience into Persistent Knowledge for Skill Evolution](https://arxiv.org/abs/2608.27454) - 把智能体经验编译为可持久维护的知识条目，作为技能持续进化的基底。 (arXiv 2026) `持久改进`
- [Prime Agent: A Self-Improving RLM Harness](https://arxiv.org/abs/2608.23552) - 通过持续的外壳适配与递归委派，让长程运行的 RLM 智能体不断改进自身。 (arXiv 2026) `真递归`
- [AutoSaddler: Automatic Harness Optimization with Durable Updates from Agent Execution Traces](https://arxiv.org/abs/2608.23041) - 从智能体执行轨迹中提取可持久保留的外壳更新，避免改进随会话结束而丢失。 (arXiv 2026) `持久改进`
- [EnvHarness: Awakening Static Worlds for Agent Learning](https://arxiv.org/abs/2608.19880) - 为静态环境补上一层可执行外壳，使其能支撑智能体的持续学习与自我改进。 (arXiv 2026) `支撑技术`
- [Evo-Harness: Context-to-Harness Skill Compilation for Self-Evolving Agents](https://arxiv.org/abs/2608.15071) - 把执行上下文编译为可复用的跨任务与任务类型技能，围绕冻结的求解器持续积累。 (arXiv 2026) `持久改进`
- [AI4AI at Test-Time: Strong-to-Weak Capability Transfer via Harnesses](https://arxiv.org/abs/2608.12307) - 用更强的构建模型迭代构建推理时 harness，将能力迁移给更弱的目标模型而不更新参数。 (arXiv 2026) `持久改进`
- [Hierarchical Self-Improvement: A Framework for Task-Specific Evolvable Agent Harnesses](https://arxiv.org/abs/2608.08466) - 单一冻结 LLM 通过「任务 harness—evolver—meta-evolver」三层层级进化自身外壳。 (arXiv 2026) `真递归`
- [EvoHarness-RL: Learning Self-Evolving Runtime Harness for Long-Horizon LLM Agents](https://arxiv.org/abs/2608.05446) - 训练智能体在长程执行中构建并协调不断进化的 Belief、Progress 与 Experience 状态。 (COLM 2026 LLA Workshop) `持久改进`
- [Recursive Harness Self-Improvement (RHI)](https://arxiv.org/abs/2607.15524) - 将 harness 表示为智能体循环的提示级规格，用自身修订历史的成对反馈迭代精炼，推理成本最高降低 60%。 (arXiv 2026) `真递归`
- [MemoHarness: Agent Harnesses That Learn from Experience](https://arxiv.org/abs/2607.14159) - 从执行诊断与可复用经验库中学习跨六个控制维度的案例自适应配置。 (arXiv 2026) `持久改进`
- [HarnessBank: Semantic Gene-Bank Search with Gated Verification for Agent-Harness Self-Evolution](https://arxiv.org/abs/2607.13683) - 用「语义基因库」（按修改位置×失败病理索引）保存多样外壳，并以有效性/激活/显著性三重门控过滤候选，七个基准上稳定提升 5.1%–15.4%。 (arXiv 2026) `真递归`
- [MetaSkill-Evolve: Recursive Self-Improvement of LLM Agents via Two-Timescale Meta-Skill Evolution](https://arxiv.org/abs/2607.05297) - 在快循环中进化任务技能，在更慢的递归循环中进化其 Analyzer、Retriever、Allocator、Proposer 与 Evolver 的元技能。 (arXiv 2026) `真递归`
- [HASE: Harness-Aware Self-Evolving](https://arxiv.org/abs/2607.03935) - 在统一智能体动作空间中协同进化模型权重、任务解与「引导/评估」外壳组件。 (arXiv 2026) `持久改进`
- [Recursive Self-Evolving Agents via Held-Out Selection (RSEA)](https://arxiv.org/abs/2606.28374) - 用严格留出选择门控进化三层自然语言状态，使递归自我进化单调安全。 (arXiv 2026) `真递归`
- [Self-Harness: Harnesses That Improve Themselves](https://arxiv.org/abs/2606.09498) - 让外壳在任务执行中自我诊断并重写自身，而非依赖外部调参流程。 (arXiv 2026) `真递归`
- [Self-evolving LLM Agents with in-distribution Optimization (Q-Evolve)](https://arxiv.org/abs/2606.07367) - 在共享的同分布学习回路中协同进化过程奖励与策略：由加权 IQL 评论家给出步级优势作为过程奖励，再以行为近端策略优化迭代改进。 (ICML 2026) `持久改进`
- [From Failed Trajectories to Reliable LLM Agents: Diagnosing and Repairing Harness Flaws (HarnessFix)](https://arxiv.org/abs/2606.06324) - 以失败轨迹为输入诊断外壳缺陷并做针对性修复，把「排障」变成外壳进化的驱动信号。 (arXiv 2026) `持久改进`
- [Evolving Agents in the Dark: Retrospective Harness Optimization via Self-Preference (RHO)](https://arxiv.org/abs/2606.05922) - 在没有真值评分的情况下，用任务回放与自我偏好来筛选外壳更新。 (arXiv 2026) `持久改进`
- [Adaptive Auto-Harness: Sustained Self-Improvement for Agentic System Deployment on Open-Ended Task Streams](https://arxiv.org/abs/2606.01770) - 面向开放任务流部署场景，让外壳在持续到达的新任务上自适应地长期改进。 (arXiv 2026) `持久改进`
- [Harness Updating Is Not Harness Benefit: Disentangling Evolution Capabilities in Self-Evolving LLM Agents](https://arxiv.org/abs/2605.30621) - 拆解「能改外壳」与「改完真的有用」两种能力，指出仅看更新是否发生会高估自我进化收益。 (arXiv 2026) `支撑技术`
- [SkillOpt: Executive Strategy for Self-Evolving Agent Skills](https://arxiv.org/abs/2605.23904) - 将单一技能文档作为冻结智能体的外部状态，由独立优化器提出有界编辑，仅在严格的留出验证增益下接受。 (arXiv 2026) `持久改进`
- [Continual Harness: Online Adaptation for Self-Improving Foundation Agents](https://arxiv.org/abs/2605.09998) - 在单一连续轨迹内在线精炼提示、子智能体、技能与记忆，并扩展到模型权重协同学习。 (arXiv 2026) `持久改进`
- [Agentic Harness Engineering: Observability-Driven Automatic Evolution of Coding-Agent Harnesses](https://arxiv.org/abs/2604.25850) - 通过可观测的编辑自主进化工具、中间件、记忆与提示，其预测在后续任务中被验证。 (arXiv 2026) `真递归`
- [CoEvoSkills: Self-Evolving Agent Skills via Co-Evolutionary Verification](https://arxiv.org/abs/2604.01687) - 让技能与验证机制协同进化，用共同成长的可信度筛选避免技能库退化。 (arXiv 2026) `真递归`
- [Meta-Harness: End-to-End Optimization of Model Harnesses](https://arxiv.org/abs/2603.28052) - 把可执行外壳作为优化对象，利用历史候选、评估分数与执行轨迹端到端地搜索更好的外壳。 (arXiv 2026) `真递归`
- [Trace2Skill: Distill Trajectory-Local Lessons into Transferable Agent Skills](https://arxiv.org/abs/2603.25158) - 把执行轨迹中的局部经验蒸馏为可迁移的智能体技能，解决手工撰写技能无法规模化、纯参数知识又遗漏操作陷阱的问题。 (arXiv 2026) `持久改进`
- [AutoHarness: Improving LLM Agents by Automatically Synthesizing a Code Harness](https://arxiv.org/abs/2603.03329) - 从环境反馈中合成并迭代精炼可执行 harness，在 145 个 TextArena 游戏中消除非法动作。 (arXiv 2026) `持久改进`
- [Audited Skill-Graph Self-Improvement for Agentic LLMs via Verifiable Rewards, Experience Synthesis, and Continual Memory (ASG-SI)](https://arxiv.org/abs/2512.23760) - 用可验证奖励构建可审计的技能图，并通过经验合成与持续记忆驱动智能体自我改进。 (arXiv 2025) `持久改进`

### Extensible Harness Substrates（可扩展外壳基底）

暴露提示、工具、技能、记忆、插件或控制流为可修改表面的可扩展智能体运行时。这些系统未必默认实现自我改进，但可作为 RSI 实验的基底。

仅有通用可扩展性是不够的。一个 RSI 基底应当把提示、记忆、技能、工具或控制流等与智能体相关的运行时组件暴露为可程序化修改的表面，以适配持久性自我修改实验。

- [Agent Zero](https://github.com/agent0ai/agent-zero) - 开源智能体框架，其提示、工具、技能、插件与多智能体档案均可被检查、替换与扩展。 `支撑技术`
- [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) - DeepSeek AI 的开源智能体外壳，基于「一切皆插件」架构。 ★中文团队 `支撑技术`
- [OpenClaw](https://github.com/openclaw/openclaw) - 持久性智能体运行时，带工作区范围的技能与「技能工坊」，智能体可起草可复用技能变更供审查与应用。 `支撑技术`
- [Pi](https://github.com/earendil-works/pi) - 自扩展编码智能体外壳，带可复用智能体运行时、终端 UI 与统一多供应商 LLM API。 `支撑技术`

### Self-Verification & Self-Correction — Enabling Foundations（自我验证与自我纠错——支撑基础）

主要是有界自我精炼与验证方法，作为持久性自我改进系统的构建块。

- [Large Language Models Cannot Self-Correct Reasoning Yet](https://arxiv.org/abs/2310.01798) - 表明在没有可靠外部反馈时，内在自我纠错可能降低推理质量，是一个重要的负向基线。 (ICLR 2024) `支撑技术`
- [Chain-of-Verification Reduces Hallucination in Large Language Models](https://arxiv.org/abs/2309.11495) - 在生成修订响应前规划并回答独立的验证问题。 (Findings of ACL 2024) `支撑技术`
- [Let's Verify Step by Step](https://arxiv.org/abs/2305.20050) - 训练过程奖励模型对中间推理步骤打分，引导更可靠的解选择。 (ICLR 2024) `支撑技术`
- [CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing](https://arxiv.org/abs/2305.11738) - 使用外部工具验证输出，并将证据转化为迭代纠错。 (ICLR 2024) `支撑技术`
- [Self-Refine: Iterative Refinement with Self-Feedback](https://arxiv.org/abs/2303.17651) - 复用同一语言模型作为生成器、批评者与精炼者，跨多轮迭代改进输出。 (NeurIPS 2023) `支撑技术`
- [Self-Consistency Improves Chain of Thought Reasoning in Language Models](https://arxiv.org/abs/2203.11171) - 采样多样推理路径并选择最一致的答案，改进推理时可靠性。 (ICLR 2023) `支撑技术`

### Self-Evolving Agent Frameworks（自我进化的智能体框架）

- [SkillRise: Agentic Reinforcement Learning for Cross-Task Skill Evolution](https://arxiv.org/abs/2607.26784) - 让单一策略在求解任务与策展持续进化的技能文档之间交替，后者被后续任务继承。 (arXiv 2026) `持久改进`
- [SIA: Self Improving AI with Harness & Weight Updates](https://arxiv.org/abs/2605.27276) - 在单个自我改进循环内，用任务反馈同时更新智能体的外壳与模型权重。 (arXiv 2026) `持久改进`
- [APEX: Autonomous Policy Exploration for Self-Evolving LLM Agents](https://arxiv.org/abs/2605.21240) - 让智能体在测试时自主探索策略，把交互经验积累为可复用的策略改进，而非只更新记忆。 (arXiv 2026) `持久改进`
- [EvoAgent: An Evolvable Agent Framework with Skill Learning and Multi-Agent Delegation](https://arxiv.org/abs/2604.20133) - 通过反馈循环积累结构化技能，并通过子智能体层级委派复杂任务。 (arXiv 2026) `持久改进`
- [Hyperagents](https://arxiv.org/abs/2603.19461) - 将任务智能体与可编辑的元智能体结合，其自我修改过程本身也能进化并跨领域迁移改进。 (arXiv 2026) `真递归`
- [AgentFactory: A Self-Evolving Framework Through Executable Subagent Accumulation and Reuse](https://arxiv.org/abs/2603.18000) - 将成功解保存为可执行子智能体，并根据执行反馈持续精炼以供未来复用。 (ACL 2026 System Demonstrations) `持久改进`
- [MemEvolve: Meta-Evolution of Agent Memory Systems](https://arxiv.org/abs/2512.18746) - 联合进化经验知识与编码、存储、检索、管理记忆的架构。 (arXiv 2025) `真递归`
- [Alita-G: Self-Evolving Generative Agent for Agent Generation](https://arxiv.org/abs/2510.23601) - 从成功轨迹中生成、抽象并策展可复用 MCP 工具，把通用智能体变成领域专家。 (arXiv 2025) `持久改进`
- [EvoAgentX: An Automated Framework for Evolving Agentic Workflows](https://arxiv.org/abs/2507.03616) - 统一工作流生成、执行、评估与进化优化，覆盖智能体提示、工具与拓扑。 (arXiv 2025) `持久改进`
- [Gödel Agent: A Self-Referential Agent Framework for Recursive Self-Improvement](https://arxiv.org/abs/2410.04444) - 让智能体检查并重写自身逻辑，而不依赖固定的手工优化例程。 (ACL 2025) `真递归`
- [Self-evolving Agents with Reflective and Memory-Augmented Abilities](https://arxiv.org/abs/2409.00872) - 结合迭代反馈、反思与遗忘感知的记忆优化，实现智能体持续适应。 (Neurocomputing 2025) `持久改进`
- [Agent-Pro: Learning to Evolve via Policy-Level Reflection and Optimization](https://arxiv.org/abs/2402.17574) - 通过反思与搜索从交互经验中精炼智能体的信念与行为策略。 (ACL 2024) `持久改进`
- [OS-Copilot: Towards Generalist Computer Agents with Self-Improvement](https://arxiv.org/abs/2402.07456) - 面向通用计算机操作的自改进智能体，通过积累交互经验持续提升任务完成能力。 (arXiv 2024) `持久改进`
- [Voyager: An Open-Ended Embodied Agent with Large Language Models](https://arxiv.org/abs/2305.16291) - 构建不断扩展的技能库，并用环境反馈在 Minecraft 中进行终身自主学习。 (TMLR 2024) `持久改进`

## Multi-Agent Self-Improvement（多智能体自我改进）

利用多智能体间交互来改进推理、策略或智能体种群。

### Co-Evolution（协同进化）

- [Who Grades the Grader? Co-Evolving Evaluation Metrics and Skills for Self-Improving LLM Agents](https://arxiv.org/abs/2607.12790) - 把评估指标本身也纳入进化对象，与技能协同改进，缓解「评分者不变而技能被过拟合」的问题。 (arXiv 2026) `真递归`
- [The Red Queen Gödel Machine: Co-Evolving Agents and Their Evaluators](https://arxiv.org/abs/2606.26294) - 让智能体与其评估器互相追赶式协同进化，避免评估标准被智能体「刷穿」而失去区分度。 (arXiv 2026) `真递归`
- [CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery](https://arxiv.org/abs/2604.01658) - 面向开放式发现任务，让多智能体自主地进化其协作与探索策略。 (arXiv 2026) `持久改进`
- [SAGE: Multi-Agent Self-Evolution for LLM Reasoning](https://arxiv.org/abs/2603.15255) - 由多个智能体生成并筛选推理经验，用于模型的持续进化。 (arXiv 2026) `持久改进`
- [Group-Evolving Agents: Open-Ended Self-Improvement via Experience Sharing](https://arxiv.org/abs/2602.04837) - 通过群体内的经验共享实现开放式自我改进，使个体改进在种群层面被复用。 (arXiv 2026) `持久改进`
- [Agent0: Unleashing Self-Evolving Agents from Zero Data via Tool-Integrated Reasoning](https://arxiv.org/abs/2511.16043) - 从同一基座模型初始化课程智能体与执行智能体并协同进化，无需人工策展数据。 (arXiv 2025) `持久改进`
- [DEBATE, TRAIN, EVOLVE: Self Evolution of Language Model Reasoning](https://arxiv.org/abs/2505.15734) - 在模型自身的多智能体辩论轨迹上微调，并重复辩论-训练循环，无需真实标签。 (EMNLP 2025) `持久改进`
- [EvoAgent: Towards Automatic Multi-Agent Generation via Evolutionary Algorithms](https://arxiv.org/abs/2406.14228) - 应用变异、交叉与选择，将专门化智能体扩展为多样化的多智能体系统。 (NAACL 2025) `持久改进`
- [SOTOPIA-π: Interactive Learning of Socially Intelligent Language Agents](https://arxiv.org/abs/2403.08715) - 在过滤后的多智能体社交交互上通过行为克隆与自我强化改进智能体策略。 (ACL 2024) `持久改进`

### Inference-time Debate（推理时辩论）

主要是通过多智能体辩论实现当前轮的改进，不产生持久性系统改变。

- [Encouraging Divergent Thinking in Large Language Models through Multi-Agent Debate](https://arxiv.org/abs/2305.19118) - 用对抗式辩论与裁判对抗迭代反思中的思维退化。 (EMNLP 2024) `支撑技术`
- [Improving Factuality and Reasoning in Language Models through Multiagent Debate](https://arxiv.org/abs/2305.14325) - 在模型实例间迭代提案与同行批判，收敛到更准确的事实性答案。 (ICML 2024) `支撑技术`

## Coding / Software-Engineering Self-Improvement（编码 / 软件工程自我改进）

改进代码、软件工程表现或自身实现的智能体与训练循环。

### Self-Modifying Coding Agents（自我修改的编码智能体）

- [Ouroboros: A Self-Developing Frontier Coding Agent with Reviewed Core Evolution](https://arxiv.org/abs/2608.08311) - 前沿编码智能体自我开发，并让对「核心」的修改经过评审后再落地，兼顾进化速度与稳定性。 (arXiv 2026) `真递归`
- [Socratic-SWE: Self-Evolving Coding Agents via Trace-Derived Agent Skills](https://arxiv.org/abs/2606.07412) - 从执行轨迹中抽取智能体技能，使其在软件工程任务上持续自我进化。 (arXiv 2026) `持久改进`
- [MOSS: Self-Evolution through Source-Level Rewriting in Autonomous Agent Systems](https://arxiv.org/abs/2605.22794) - 智能体重写自身源码、回放失败批次，并通过审批与回滚门控逐级晋级容器镜像。 (arXiv 2026) `真递归`
- [Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents](https://arxiv.org/abs/2505.22954) - 通过修改自身代码并保留经验验证的改进，在开放式档案中进化编码智能体。 (ICLR 2026) `真递归`
- [Live-SWE-agent: Can Software Engineering Agents Self-Evolve on the Fly?](https://arxiv.org/abs/2511.13646) - 从一个最小的 bash 脚手架出发，在解决软件问题的过程中即时创建并修订自己的工具。 (arXiv 2025) `持久改进`
- [Huxley-Gödel Machine (HGM)](https://arxiv.org/abs/2510.21614) - 提出「元生产力—性能」错配问题，并引入 CMP 指标衡量自我改进系统的质量。 (arXiv 2025) `真递归`
- [A Self-Improving Coding Agent](https://arxiv.org/abs/2504.15228) - 展示一个编辑自身实现的编码智能体，并在 SWE-bench Verified 上取得经验性改进。 (ICLR 2025 SSI-FM Workshop) `真递归`

### Iterative Repair & Training（迭代修复与训练）

混合当前轮的修复循环与可延续到后续迭代的持久性改进。

- [Training Software Engineering Agents and Verifiers with SWE-Gym](https://arxiv.org/abs/2412.21139) - 提供可执行仓库任务与轨迹，用于训练 SWE 智能体与推理时验证器。 (ICML 2025) `持久改进`
- [Teaching Large Language Models to Self-Debug](https://arxiv.org/abs/2304.05128) - 教会模型检查执行结果、解释代码并通过迭代提示修复失败。 (ICLR 2024) `支撑技术`
- [AgentCoder: Multi-Agent-based Code Generation with Iterative Testing and Optimisation](https://arxiv.org/abs/2312.13010) - 协调程序员、测试设计者与测试执行者智能体，在反馈循环中迭代修复生成的代码。 (arXiv 2023) `支撑技术`

## Automated AI R&D（自动化 AI 研发）

自动化 AI 研究与发展部分流程的系统，包括实验、后训练、算法发现以及改进其他 AI 系统。

- [The Last AI Built by Humans: Toward Genuine Recursive Self-Improvement](https://arxiv.org/abs/2609.11873) - 用 Headroom-Closed Index 揭示现有 LLM 问题，并给出从改进执行自主到递归元改进的路线图。 (arXiv 2026) `支撑技术`
- [MetaRSI / RSI²: A Meta-Recursive Self-Improving System for Recursive Self-Improving Systems Themselves](https://arxiv.org/abs/2609.06396) - 统一 Model-RSI、Data-RSI、Harness-RSI 三个算子的元递归架构，改进「自我改进的过程」本身。 (arXiv 2026) ★清华/北大/斯坦福等团队 `真递归`
- [Metaⁿ: Recursive Self-Improvement through Emergent Depth](https://arxiv.org/abs/2608.24735) - 固定元操作、对其输入递归，使每层从更高视角推理，在八个基准族上超越此前的自我改进智能体。 (arXiv 2026) `真递归`
- [AutoResearch: Insight In, Hallucination Out](https://arxiv.org/abs/2608.17906) - 将接地想法生成与协调执行智能体连接，在接受研究结论前独立评审实验。 (arXiv 2026) `支撑技术`
- [Frontis-MA1: Training an AI4AI Model towards Recursive Self-Improvement in Machine Learning Engineering](https://arxiv.org/abs/2607.28568) - 将执行接地算子训练与长程进化连接，以机器学习工程作为 RSI 的 AI4AI 试验台。 (arXiv 2026) `持久改进`
- [MLEvolve: A Self-Evolving Framework for Automated Machine Learning Algorithm Discovery](https://arxiv.org/abs/2606.06473) - 结合渐进图搜索、回溯记忆与分层代码生成，实现长程端到端 ML 算法发现。 (arXiv 2026) `持久改进`
- [AIRA_2: Overcoming Bottlenecks in AI Research Agents](https://arxiv.org/abs/2603.26499) - 针对 AI 研究智能体的三个结构性瓶颈——同步单卡执行限制采样吞吐、基于验证的选择带来泛化差距、搜索效率不足——给出改进方案。 (arXiv 2026) `支撑技术`
- [EvoScientist: Towards Multi-Agent Evolving AI Scientists for End-to-End Scientific Discovery](https://arxiv.org/abs/2603.08127) - 让多智能体科研系统在端到端科学发现过程中进化自身的分工与策略。 (arXiv 2026) `支撑技术`
- [FT-Dojo: Towards Autonomous LLM Fine-Tuning with Language Agents](https://arxiv.org/abs/2603.01712) - 将数据收集、训练、评估、诊断与策略修订变成自主微调智能体的可执行环境。 (arXiv 2026) `支撑技术`
- [Towards Execution-Grounded Automated AI Research](https://arxiv.org/abs/2601.14525) - 将 LLM 预训练与后训练转化为可执行研究环境，进化搜索从实验结果中学习。 (arXiv 2026) `支撑技术`
- [Towards End-to-End Automation of AI Research (The AI Scientist-v2)](https://doi.org/10.1038/s41586-026-10265-5) - 用免模板的智能体树搜索提出假设、运行实验、分析结果并撰写完整研究论文。 (Nature 2026) `支撑技术`
- [Can Large Language Models Invent Algorithms to Improve Themselves? (Self-Developing)](https://aclanthology.org/2025.naacl-long.519/) - 提出 Self-Developing 框架，让 LLM 自主生成并学习「改进模型的算法」，在 GSM8k 上发现超越人工设计的模型合并策略。 (NAACL 2025) `真递归`
- [The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery](https://arxiv.org/abs/2408.06292) - 自动化想法生成、实验、论文写作与评审，形成可复用的机器学习研究循环。 (arXiv 2024) `支撑技术`

## Embodied & Physical Self-Improvement（具身与物理自我改进）

利用与物理或仿真环境的交互，在机器人策略、技能、外壳、世界模型或相关研究过程中产生持久性改进的系统。

- [PRACTICE: From Experience to Expertise in Self-Evolving Embodied Agents](https://arxiv.org/abs/2608.30760) - 让多模态具身智能体把交互经验转化为可复用的专长，实现跨任务的持续自我改进。 (arXiv 2026) `持久改进`
- [Self-Evolving Embodied Agents via Skill-Harness Evolution](https://arxiv.org/abs/2608.11350) - 冻结模型权重，同一模型同时充当规划器与优化器，持续进化可复用技能与上下文代码外壳。 (arXiv 2026) `持久改进`
- [ASPIRE: Agentic Skills Discovery for Robotics](https://arxiv.org/abs/2607.00272) - 从机器人执行轨迹诊断失败、编辑 code-as-policy，并把验证过的修复存入技能库以供跨任务复用。 (arXiv 2026) `持久改进`
- [ENPIRE: Agentic Robot Policy Self-Improvement in the Real World](https://arxiv.org/abs/2606.19980) - 用编码智能体在真实机器人上运行 autoresearch 循环：重置、rollout、验证、编辑策略/训练代码并重跑。 (arXiv 2026) `持久改进`
- [MineEvolve: Self-Evolution with Accumulated Knowledge for Long-Horizon Embodied Minecraft Agents](https://arxiv.org/abs/2603.13131) - 将成功经验转化为可复用技能、失败转化为可执行护栏，持续引导 LLM 规划器。 (arXiv 2026) `持久改进`
- [RISE: Self-Improving Robot Policy with Compositional World Model](https://arxiv.org/abs/2602.11075) - 用组合世界模型持续生成想象 rollout、估计优势并更新机器人策略。 (RSS 2026) `持久改进`
- [Self-Improving Vision-Language-Action Models with Data Generation via Residual RL](https://iclr.cc/virtual/2026/poster/10008318) - 用残差强化学习定位 VLA 失败区域并生成恢复轨迹，蒸馏回通才策略，形成数据到策略的自我改进飞轮。 (ICLR 2026) `持久改进`
- [SIMA 2: A Generalist Embodied Agent for Virtual Worlds](https://arxiv.org/abs/2512.04797) - 基于 Gemini 的通用具身智能体，可在多种 3D 虚拟世界中理解与行动，并具备自我改进能力。 (arXiv 2025) `持久改进`
- [EnvGen: Generating and Adapting Environments via LLMs for Training Embodied Agents](https://arxiv.org/abs/2403.12014) - 让 LLM 生成并自适应调整训练环境，用于训练具身智能体，缓解固定环境导致的过拟合。 (arXiv 2024) `持久改进`

## Evolutionary & Open-Ended RSI（进化式与开放式 RSI）

持续发现更强解或学习系统的进化、质量多样性（quality-diversity）与开放式过程。

- [PACEvolve: Enabling Long-Horizon Progress-Aware Consistent Evolution](https://arxiv.org/abs/2601.10657) - 结合分层上下文管理、回溯与自适应采样，维持协作式长程进化搜索。 (arXiv 2026) `持久改进`
- [AlphaEvolve: A Coding Agent for Scientific and Algorithmic Discovery](https://arxiv.org/abs/2506.13131) - 结合语言模型代码生成、自动评估与进化搜索来改进算法，包括用于 AI 训练的组件。 (arXiv 2025) `持久改进`
- [Eureka: Human-Level Reward Design via Coding Large Language Models](https://arxiv.org/abs/2310.12931) - 用 LLM 对奖励代码做进化搜索，并以环境反馈作为选择信号，让奖励设计本身被自动改进。 (ICLR 2024) `持久改进`
- [Higher Order and Self-Referential Evolution for Population-based Methods](https://openreview.net/forum?id=3tk6AES1Aj) - 进化变异率与高阶元变异率，包括一个修改自身的自指顶层参数。 (ICML 2024 AutoRL Workshop) `真递归`
- [Mathematical Discoveries from Program Search with Large Language Models](https://www.nature.com/articles/s41586-023-06924-6) - 提出 FunSearch，将冻结代码模型与评估器配对进行进化循环，发现新程序与数学结果。 (Nature 2024) `持久改进`
- [AutoML-Zero: Evolving Machine Learning Algorithms From Scratch](https://arxiv.org/abs/2003.03384) - 从基础数学运算进化完整学习算法，最小化人类设计偏置。 (ICML 2020) `持久改进`
- [AI-GAs: AI-Generating Algorithms, an Alternate Paradigm for Producing General Artificial Intelligence](https://arxiv.org/abs/1905.10985) - 提出自动生成环境、架构与学习算法的开放式系统。 (arXiv 2019) `支撑技术`
- [Paired Open-Ended Trailblazer (POET): Endlessly Generating Increasingly Complex and Diverse Learning Environments and Their Solutions](https://arxiv.org/abs/1901.01753) - 协同进化环境与智能体，并在涌现挑战间迁移解。 (GECCO 2019) `持久改进`
- [Learning to Learn by Gradient Descent by Gradient Descent](https://arxiv.org/abs/1606.04474) - 元学习一个优化器，其循环更新规则可替代手工设计的优化算法。 (NeurIPS 2016) `持久改进`
- [Quality Diversity: A New Frontier for Evolutionary Computation](https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2016.00040/full) - 形式化搜索「在其生态位内同时多样化且高性能」的解集合。 (Frontiers in Robotics and AI 2016) `支撑技术`
- [Illuminating Search Spaces by Mapping Elites](https://arxiv.org/abs/1504.04909) - 提出 MAP-Elites，发现多样的局部高质量解档案。 (arXiv 2015) `支撑技术`
- [POWERPLAY: Training an Increasingly General Problem Solver by Continually Searching for the Simplest Still Unsolvable Problem](https://arxiv.org/abs/1112.5309) - 交替发明新任务与修改求解器，使其已验证的技能集不断扩展。 (Frontiers in Psychology 2013) `持久改进`

## Safety, Alignment & Theory（安全、对齐与理论）

针对随时间自我修改或自我改进系统的安全性、稳定性、目标保持、可纠正性（corrigibility）与监督机制。

- [SafeEvolve: Harness-Policy Co-Evolution from Agent Experience for Safety Alignment](https://arxiv.org/abs/2609.02786) - 从智能体经验中协同进化安全提示与技能库，并结合 SFT/GRPO 策略更新维持安全对齐。 (arXiv 2026) `支撑技术`
- [Self-Improvement Can Self-Regress: The Rise-and-Collapse Failure Mode of LLM Self-Training](https://arxiv.org/abs/2606.21090) - 刻画自我训练「先升后崩」的失败模式，指出改进可能在若干轮后反转。 (arXiv 2026) `支撑技术`
- [SAHOO: Safeguarded Alignment for High-Order Optimization Objectives in Recursive Self-Improvement](https://arxiv.org/abs/2603.06333) - 通过目标漂移检测、约束保持检查与回归风险分析监控 RSI 过程中的对齐漂移。 (ICLR 2026 RSI Workshop) `支撑技术`
- [TamperBench: Systematically Stress-Testing LLM Safety Under Fine-Tuning and Tampering](https://arxiv.org/abs/2602.06911) - 系统压力测试安全对齐在微调、权重空间修改与表示篡改下是否保持。 (arXiv 2026) `支撑技术`
- [Your Agent May Misevolve: Emergent Risks in Self-evolving LLM Agents](https://arxiv.org/abs/2509.26354) - 研究模型、记忆、工具与工作流进化路径中的有害漂移，提出「误进化（misevolution）」概念。 (ICLR 2026) `支撑技术`
- [The Economics of Recursive Self-Improvement](https://elasticity.institute/rsi-paper.pdf) - 将「AI 能力→AI 研发→更强能力」的反馈路径建模为弹性网络，并推导自我维持加速的条件。 (Elasticity Institute 2026) `支撑技术`
- [Escaping Model Collapse via Synthetic Data Verification: Near-term Improvements and Long-term Convergence](https://arxiv.org/abs/2510.16657) - 研究自我生成数据上的迭代训练何时坍缩，并展示外部验证如何稳定自我改进。 (arXiv 2025) `支撑技术`
- [SGM: A Statistical Gödel Machine for Risk-Controlled Recursive Self-Modification](https://arxiv.org/abs/2510.10232) - 用统计检验取代「可证明有益」的严格门槛，使自我修改在可量化的风险预算内进行。 (arXiv 2025) `支撑技术`
- [Will Compute Bottlenecks Prevent an Intelligence Explosion?](https://arxiv.org/abs/2507.23181) - 分析算力瓶颈是否会阻止智能爆炸，区分思考速度、算法质量与任务成绩。 (arXiv 2025) `支撑技术`
- [Evaluating Goal Drift in Language Model Agents](https://arxiv.org/abs/2505.02709) - 度量长程智能体是否在竞争性环境压力下逐渐偏离既定目标，并发现漂移与上下文增长带来的模式匹配倾向相关。 (AIES 2025) `支撑技术`
- [Performance of Bounded-Rational Agents With the Ability to Self-Modify](https://arxiv.org/abs/2011.06275) - 表明自我修改可能放大错误并逐渐使有限理性智能体失配。 (AAAI 2021 SafeAI Workshop) `支撑技术`
- [AGI Agent Safety by Iteratively Improving the Utility Function](https://arxiv.org/abs/2007.05411) - 设计一种安全机制，允许智能体效用函数迭代更新，同时降低操纵改进过程的激励。 (AGI 2020) `支撑技术`
- [Scalable Agent Alignment via Reward Modeling: A Research Direction](https://arxiv.org/abs/1811.07871) - 概述递归奖励建模，用于监督过于复杂而无法直接人工评估的任务。 (arXiv 2018) `支撑技术`
- [Self-Modification of Policy and Utility Function in Rational Agents](https://arxiv.org/abs/1605.03142) - 形式化理性智能体何时保持或修改策略与效用函数，并推导自我修改保持目标的条件。 (AGI 2016) `支撑技术`
- [Intelligence Explosion Microeconomics](https://intelligence.org/files/IEM.pdf) - 建模决定递归改进是加速、平台期还是爆炸的回报与瓶颈。 (MIRI technical report 2013) `支撑技术`

### Supporting Safety Foundations（支撑性安全基础）

- [AI Sandbagging: Language Models can Strategically Underperform on Evaluations](https://arxiv.org/abs/2406.07358) - 表明模型能选择性隐藏能力或刻意降低得分，破坏基于评估的自我改进治理。 (ICML 2025) `支撑技术`
- [Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training](https://arxiv.org/abs/2401.05566) - 展示贯穿标准安全训练仍潜伏的欺骗性策略，且可能对检测更鲁棒。 (arXiv 2024) `支撑技术`
- [Model Evaluation for Extreme Risks](https://arxiv.org/abs/2305.15324) - 针对危险涌现能力（含自主复制与适应）提出能力与对齐评估。 (arXiv 2023) `支撑技术`
- [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073) - 用书面原则与模型生成的批判扩展监督，同时保留明确的行为约束。 (arXiv 2022) `支撑技术`
- [Optimal Policies Tend to Seek Power](https://arxiv.org/abs/1912.01683) - 证明最优智能体在何种条件下被激励保持选项并寻求对环境的控制。 (NeurIPS 2021) `支撑技术`
- [Reward Tampering Problems and Solutions in Reinforcement Learning: A Causal Influence Diagram Perspective](https://arxiv.org/abs/1908.04734) - 刻画破坏奖励过程的激励，并给出消除它们的设计原则。 (Synthese 2021) `支撑技术`
- [Risks from Learned Optimization in Advanced Machine Learning Systems](https://arxiv.org/abs/1906.01820) - 分析「mesa-optimizer」（内部优化器），其习得目标可能偏离训练它的目标。 (arXiv 2019) `支撑技术`
- [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565) - 界定奖励黑客、可扩展监督、安全探索与分布偏移鲁棒性等实际问题。 (arXiv 2016) `支撑技术`
- [Safely Interruptible Agents](https://auai.org/~w-auai/uai2016/proceedings/papers/68.pdf) - 展示如何设计不激励抵抗人类干预的强化学习智能体。 (UAI 2016) `支撑技术`

## Introspection & Self-Modeling（内省与自我建模）

研究 AI 系统能否建模、诊断、预测并推理自身行为与内部状态——这些能力可能支撑有效的自我改进。

- [Self-Reference in Large Language Models: The Introspection Threshold for Recursive Self-Improvement](https://arxiv.org/abs/2607.04277) - 论证可持续的 RSI 需要系统对自身操作建模，并将内省性自指确定为递归改进的潜在阈值。 (arXiv 2026) `支撑技术`
- [Structure Enables Effective Self-Localization of Errors in LLMs](https://arxiv.org/abs/2602.02416) - 表明结构化推理使模型能定位自身推理首次出错的位置，并用该定位做自主纠正。 (ICLR 2026) `支撑技术`
- [Emergent Introspective Awareness in Large Language Models](https://arxiv.org/abs/2601.01828) - 探究语言模型能否检测、报告并刻意影响自身内部表示，而非仅从文本推断自身属性。 (arXiv 2026) `支撑技术`
- [Tell me about yourself: LLMs are aware of their learned behaviors](https://arxiv.org/abs/2501.11120) - 发现微调模型能在训练数据未显式描述这些行为的情况下，阐述自己习得的行为倾向。 (arXiv 2025) `支撑技术`
- [Looking Inward: Language Models Can Learn About Themselves by Introspection](https://arxiv.org/abs/2410.13787) - 通过比较模型对自身行为的预测与其他模型的预测来测试特权自我预测。 (ICLR 2025) `支撑技术`
- [Recursive Introspection: Teaching Language Model Agents How to Self-Improve](https://arxiv.org/abs/2407.18219) - 训练语言模型检查先前失败尝试，并在后续交互轮次中递归改进响应。 (NeurIPS 2024) `支撑技术`
- [Self-Recognition in Language Models](https://arxiv.org/abs/2407.06946) - 用模型生成的安全问题测试模型能否识别自身输出，未发现普遍的自我识别。 (EMNLP 2024) `支撑技术`
- [Do Large Language Models Know What They Don't Know?](https://arxiv.org/abs/2305.18153) - 通过测试对不可回答与不可知问题的识别来评估模型自我认知。 (Findings of ACL 2023) `支撑技术`
- [Language Models (Mostly) Know What They Know](https://arxiv.org/abs/2207.05221) - 度量模型能否评估自身主张并预测自己知道如何回答的问题。 (arXiv 2022) `支撑技术`
- [Bounded Recursive Self-Improvement](https://arxiv.org/abs/1312.6764) - 研究一个已实现的目标导向系统，通过显式有界自我建模循环改进自身行为。 (arXiv 2013) `支撑技术`

## Benchmarks & Evaluations（基准测试与评估）

基准测试分为直接自我改进评估、前沿实验室评估框架与能力代理指标三类。代理基准仅在其度量的瓶颈直接约束持续性或递归自我改进时才被纳入。

### Direct RSI & Self-Improvement Evaluations（直接 RSI 与自我改进评估）

- [S3Gym: Can LLMs Turn Self-Testing and Self-Judging into Self-Improvement?](https://arxiv.org/abs/2608.31100) - 把自我测试、自我评判与自我改进拆成三项能力，在七个可执行文本游戏中用宽松探索与严格留出评估分别度量。 (arXiv 2026) `支撑技术`
- [LongWoF-Bench: Evaluating EvoMap Genes for Verifiable Long-Workflow Tasks](https://arxiv.org/abs/2608.23200) - 提供 778 个机器可验证的长工作流任务，展示由验证器确认轨迹整合出的「基因」优于技能包。 (arXiv 2026) `支撑技术`
- [PAST-Bench](https://arxiv.org/abs/2608.04003) - 用「保留经验 / 不保留经验」的配对任务序列，隔离经验管理机制对后续任务表现的贡献。 (arXiv 2026) `支撑技术`
- [ContinualSkillBench](https://arxiv.org/abs/2608.03874) - 在五个领域的 500 个连续子任务上考察技能库的构建、维护与复用，度量技能保持与迁移。 (arXiv 2026) `支撑技术`
- [RSIBench-Data](https://arxiv.org/abs/2607.25886) - 通过让智能体在固定后训练栈下针对检查点反馈迭代改进训练数据策略，隔离数据中心的 RSI。 (arXiv 2026) `支撑技术`
- [SEAGym](https://arxiv.org/abs/2606.17546) - 把兼容 Harbor 的任务切分为训练、冻结验证、留出同分布/异分布、回放与成本等视图，用于评估外壳更新是否真的泛化。 (arXiv 2026) `支撑技术`
- [PostTrainBench: Can LLM Agents Automate LLM Post-Training?](https://arxiv.org/abs/2603.08640) - 给自主智能体一个基座模型、一块 H100 GPU 与 10 小时，研究并执行其能找到的最强后训练策略。 (ICML 2026) `支撑技术`
- [RSI-Bench](https://github.com/sunghunkwag/rsi-bench) - 提供开源六轴框架，度量自我修改深度、改进轨迹、算子发现、适应、安全与目标生成。 (community framework 2026) `支撑技术`

### Frontier Lab Self-Improvement & AI R&D Evaluation Frameworks（前沿实验室自我改进与 AI 研发评估框架）

- [Anthropic Autonomous AI R&D Evaluations](https://www.anthropic.com/transparency/model-report) - 定义 Responsible Scaling Policy 的 AI R&D-4 能力阈值（完全自动化入门级远程研究员的工作），并据此评估模型与防护措施。 (Anthropic Model Report 2026) `支撑技术`
- [Google DeepMind Frontier Safety Framework (FSF) ML R&D](https://deepmind.google/blog/strengthening-our-frontier-safety-framework/) - 为可能显著加速或自动化 AI 研发的 ML R&D 能力设置专门的 CCL、TCL 与评估协议。 (Google DeepMind Blog 2026) `支撑技术`
- [OpenAI AI Self-Improvement Evaluations](https://deploymentsafety.openai.com/gpt-5-6) - 在 Preparedness Framework 下用 Internal Research Debugging、KernelGen 1P、NanoGPT、PostTrainBench Lite、MLE-Bench Revised 等指标聚合成 RSI Index，跟踪 AI 自我改进能力。 (OpenAI System Card 2026) `支撑技术`

### AI R&D Capability Proxies（AI 研发能力代理指标）

- [AI4AI-Bench](https://arxiv.org/abs/2608.20318) - 在十个研究仓库上重设计训练算法，给智能体四小时探索时间并以密封重跑检验结果。 (arXiv 2026) `支撑技术`
- [AutoLab: Can Frontier Models Solve Long-Horizon Auto Research and Engineering Tasks?](https://arxiv.org/abs/2606.05080) - 专家策展的 36 个真实长程闭环优化任务，用于评估前沿智能体的自动化研究与工程能力。 (arXiv 2026) `支撑技术`
- [MLS-Bench: A Holistic and Rigorous Assessment of AI Systems on Building Better AI](https://arxiv.org/abs/2605.08678) - 覆盖 12 个 ML 研究领域的 140 个任务，度量 AI 系统能否发明可泛化、可扩展的 ML 方法。 (arXiv 2026) `支撑技术`
- [Frontier-Eng](https://arxiv.org/abs/2604.12290) - 用模拟器反馈迭代优化可行的工程设计，覆盖能源、计算系统与控制等 47 个任务。 (arXiv 2026) `支撑技术`
- [MLE-bench](https://github.com/openai/mle-bench) - 度量 75 场 Kaggle 竞赛上的端到端机器学习工程表现，用于跟踪模型自我改进能力。 (ICLR 2025) `支撑技术`
- [PaperBench](https://github.com/openai/frontier-evals/tree/main/project/paperbench) - 评估智能体依据论文描述复现最先进 AI 研究的能力。 (ICML 2025) `支撑技术`
- [RE-Bench](https://github.com/METR/RE-Bench) - 在固定时间预算下，将 AI 智能体与人类专家在开放式 ML 研究工程任务上对比。 (ICML 2025) `支撑技术`
- [MLAgentBench](https://github.com/snap-stanford/MLAgentBench) - 测试语言智能体能否依据研究指令自主执行并改进 ML 实验。 (ICML 2024) `支撑技术`

### Agent Capability Proxies（智能体能力代理指标）

- [Long-Horizon-Terminal-Bench](https://arxiv.org/abs/2607.08964) - 在 46 个终端任务上评估智能体，要求跨越数百个回合并伴随密集中间奖励的持续执行。 (arXiv 2026) `支撑技术`
- [OSWorld 2.0](https://arxiv.org/abs/2606.29537) - 度量计算机使用智能体在 108 个真实端到端工作流上的表现，中位人类完成时间约 1.6 小时。 (arXiv 2026) `支撑技术`
- [ARC-AGI-3: A New Challenge for Frontier Agentic Intelligence](https://arxiv.org/abs/2603.24621) - 要求智能体探索陌生交互环境、推断目标、建模环境动态、记忆与规划，度量自我改进的自适应交互与泛化瓶颈。 (arXiv 2026) `支撑技术`
- [MCPMark](https://arxiv.org/abs/2509.24002) - 在 SaaS、开发、浏览器、文件系统与数据库环境中压力测试真实有状态 MCP 工作流。 (arXiv 2025) `支撑技术`
- [SWE-Bench Pro](https://arxiv.org/abs/2509.16941) - 在 1865 个抗污染的、需要数小时或数天专业软件工程的企业级任务上测试编码智能体。 (arXiv 2025) `支撑技术`
- [Measuring AI Ability to Complete Long Software Tasks (METR Time Horizon)](https://arxiv.org/abs/2503.14499) - 估计智能体在不可平凡并行的软件任务上以给定概率成功的人类等效任务时长。 (NeurIPS 2025) `支撑技术`
- [TheAgentCompany](https://arxiv.org/abs/2412.14161) - 在模拟软件公司内评估智能体完成 175 个跨应用工作场所任务。 (NeurIPS 2025) `支撑技术`
- [SWE-bench](https://github.com/SWE-bench/SWE-bench) - 提供可复现的真实世界软件问题，用于评估编码智能体与 DGM 等经验性自我修改系统。 (ICLR 2024) `支撑技术`
- [SWE-bench Verified](https://openai.com/index/introducing-swe-bench-verified/) - 提供经人工验证的子集，减少测量迭代编码智能体改进时的破损/欠指定任务。 (OpenAI benchmark 2024) `支撑技术`

## Frameworks & Tools（框架与工具）

### Self-Modifying / Self-Evolving Systems（自我修改 / 自我进化系统）

- [AgentFactory](https://github.com/zzatpku/AgentFactory) - 自我进化框架，积累并复用可执行子智能体以改进未来任务求解。 ★北大团队 `持久改进`
- [Darwin Gödel Machine](https://github.com/jennyzzt/dgm) - 自我修改编码智能体的官方实现，带开放式档案进化。 `真递归`
- [Gödel Agent](https://github.com/Arvid-pku/Godel_Agent) - Gödel Agent 的官方实现：递归自我改进的自指智能体框架。 `真递归`
- [Hermes Agent](https://github.com/NousResearch/hermes-agent) - 自我改进个人智能体，内置从经验创建并精炼技能的学习循环。 `持久改进`
- [HyperAgents](https://github.com/facebookresearch/HyperAgents) - 自指智能体框架，可编辑的元智能体改进自身与任务智能体以实现可计算目标。 `真递归`
- [SEAL](https://github.com/Continual-Intelligence/SEAL) - 生成自身适应数据与更新指令的语言模型官方代码。 `持久改进`
- [SIA](https://github.com/hexo-ai/sia) - 自我改进 AI 框架，迭代更新智能体外壳，并在配置时更新目标模型权重。 `持久改进`
- [AgentEvolver](https://github.com/modelscope/AgentEvolver) - 阿里 ModelScope 的端到端自我进化训练框架，统一自我提问、自我导航与自我归因三大机制。 ★中文团队 `持久改进`
- [SE-Agent](https://github.com/JARVIS-Xs/SE-Agent) - 自我进化轨迹优化框架，通过 Revision/Recombination/Refinement 在 SWE-bench Verified 上取得 SOTA（80%）。 ★中文团队 `持久改进`
- [GenericAgent](https://github.com/lsdefine/GenericAgent) - 极简自我进化自主智能体框架（~3K 行核心代码），每次任务自动固化技能，形成专属技能树。 ★中文团队 `持久改进`
- [OmniAgent](https://github.com/YeQing17-2026/OmniAgent) - 全维度自我进化（技能/上下文/BrainModel）智能体框架，带动态安全加固。 ★中文团队 `持久改进`
- [yoyo-evolve](https://github.com/yologdev/yoyo-evolve) - 一个公开自我进化自身源码的编码智能体，200 行 Rust 起步，全部提交由智能体编写并测试门控。 `真递归`
- [Self-Improving Coding Agent](https://github.com/MaximeRobeyns/self_improving_coding_agent) - 在自己的代码库上运行的编码智能体自我改进循环框架。 `真递归`
- [Autogenesis](https://github.com/DVampire/Autogenesis) - 自我进化多智能体框架，MetaAgent 编排子智能体，优化器/评估器/生成器持续改进工具、技能与智能体生态。 `持久改进`

### Harness / Memory / Skill Evolution（外壳 / 记忆 / 技能进化）

- [ACE](https://github.com/ace-agent/ace) - Agentic Context Engineering 的官方实现：为自我改进语言模型进化上下文。 `持久改进`
- [ALMA](https://github.com/zksha/alma) - Learning to Continually Learn via Meta-learning Agentic Memory Designs 的官方实现。 `持久改进`
- [Continual Harness](https://github.com/sethkarten/continual-harness) - 从经验中在线适应的自我改进智能体外壳。 `持久改进`
- [EvoAgentX](https://github.com/EvoAgentX/EvoAgentX) - 自动构建、评估与优化智能体工作流的自我进化框架。 `持久改进`
- [EvolveR](https://github.com/KnowledgeXLab/EvolveR) - 通过闭环、经验驱动生命周期改进的自我进化 LLM 智能体框架。 `持久改进`
- [Gear](https://github.com/rsi-gear/gear) - 利用执行轨迹与基准评测反馈迭代优化智能体的提示词、工具和工作流，将选中的外壳版本保留供后续轮次使用。 (2026) `持久改进`
- [Letta Code](https://github.com/letta-ai/letta-code) - 记忆优先的编码智能体外壳，长寿命智能体重写上下文并从经验学习技能。 `持久改进`
- [Memento-Skills](https://github.com/Memento-Teams/Memento-Skills) - 通过反思学习检索、评估、修复并重写持久技能的自我进化框架。 `持久改进`
- [Reef](https://github.com/Human-Agent-Society/reef) - 持续学习服务基础设施，记录智能体交互，将匹配的反馈转化为模型权重或外壳更新。 `持久改进`
- [Voyager](https://github.com/MineDojo/Voyager) - 具身终身学习智能体，带自动课程、迭代提示与可复用技能库。 `持久改进`
- [Prime Agent](https://github.com/PrimeIntellect-ai/prime-agent) - 自我改进 RLM 智能体，通过 Continual Harness 持久化提示、记忆、技能与子智能体规范。 `真递归`

### Automated Search / AI R&D（自动化搜索 / AI 研发）

- [ADAS](https://github.com/ShengranHu/ADAS) - 在可执行智能体设计空间上搜索的元智能体官方实现。 `持久改进`
- [AI Scientist](https://github.com/SakanaAI/AI-Scientist) - 生成 ML 想法、运行实验并撰写研究论文的端到端系统。 `支撑技术`
- [autoresearch](https://github.com/karpathy/autoresearch) - 运行自主循环：编辑 LLM 训练程序、训练 5 分钟、只保留改进验证 bits/byte 的改动。 `支撑技术`
- [Evolutionary Model Merge](https://github.com/SakanaAI/evolutionary-model-merge) - 在参数与数据流空间中进化开放模型的组合。 `持久改进`
- [FunSearch](https://github.com/google-deepmind/funsearch) - LLM 引导进化程序搜索的参考实现，带可执行评估器。 `持久改进`
- [MLEvolve](https://github.com/InternScience/MLEvolve) - 用渐进搜索与经验驱动记忆进行端到端 ML 算法发现的自我进化多智能体框架。 `持久改进`
- [OpenEvolve](https://github.com/algorithmicsuperintelligence/openevolve) - 受 AlphaEvolve 启发的开源进化编码智能体。 `持久改进`
- [POET](https://github.com/uber-research/poet) - 协同进化环境与其配对智能体的参考实现。 `持久改进`
- [Mechanist](https://github.com/zjunlp/mechanist) - 面向大模型机理可解释性的自主研究系统，全流程自动化「文献检索→假设提出→实验→验证→迭代」。 ★中文团队（浙大） `支撑技术`

## Chinese Resources（中文资源）

面向中文读者的原创解读、综述文章与视频，涵盖递归自我改进、自我进化智能体与自动化 AI 科研。

- [递归自我改进（RSI）：从思想实验到实证子领域](https://jishuzhan.net/article/2098254460859109378) - 高质量中文综述，系统梳理 RSI 的 1250 篇论文谱系、验证层级与「人在环上」的现状，是中文入门首选。 (技术栈 2026)
- [递归式自我改进研究地图](https://github.com/Linwei-Chen/recursive-self-improvement-research-atlas) - 一份中文 RSI 研究地图，按七条路线分层梳理从智能爆炸假说到有界自改、自动化 AI 研发与验证瓶颈的证据。 (GitHub 2026)
- [AI 开始改进「改进自己的方法」，RSI 进入平方时代丨MetaRSI](https://www.qbitai.com/2026/09/488832.html) - 量子位对 MetaRSI-v1 元递归架构的深度解读。 (量子位 2026)
- [AI 开始「研究自己」：Mechanist 开启机器智能机制科学](https://finance.sina.cn/tech/2026-09-05/detail-iniqtwvy5349197.d.html) - 机器之心解读浙大 Mechanist：把大模型作为实验对象、机制发现作为科学问题的研究范式。 (机器之心 2026)
- [Meta 华人实习生搞出超级智能体！自己写代码实现自我进化](https://zhuanlan.zhihu.com/p/2022289126448219370) - 知乎对 HyperAgents（DGM-H）的通俗解读。 (知乎 2026)
- [清华教授沈阳把 AI 逼成了会自己进化的「新物种」](https://zhuanlan.zhihu.com/p/2049777421671462058) - 新智元对话清华沈阳，探讨自进化 AI 的自我递归进化与 ZeeLin 框架。 (新智元/知乎 2026)
- [为什么 Qwen 能自我改进推理，Llama 却不行？斯坦福找到了原理](https://developer.cloud.tencent.com/news/2265006) - 腾讯云解读 Cognitive Behaviors 论文，剖析初始认知行为与自我改进能力的关系。 (腾讯云 2025)
- [DeepSeek-R1 论文中文精读](https://arthurchiao.art/blog/deepseek-r1-paper-zh/) - DeepSeek-R1 全文中文翻译，详细拆解 R1-Zero 的自我进化过程与「顿悟时刻」。 (ArthurChiao 2025)
- [DeepSeek-GRM 详解：从 scalar 到 generative，reward modeling 的范式跃迁](https://yudonglee.me/deepseek-grm-explained/) - 详解 DeepSeek 的 SPCT 与推理时 scaling 奖励建模。 (2026)
- [腾讯 Hyra 智能体实现递归自我改进](https://www.xinstall.com/article/11860) - 解读腾讯混元 Hyra-1.0 在长周期科研任务中的自我进化循环。 (2026)
- [递归式自我改进：AI 研发范式的终极进化](https://www.neican.ai/insights/article-20260514094003838-0/) - 温故智新对 Recursive Superintelligence 与「尤里卡机器」愿景的解读。 (AI 内参 2026)
- [自动研究真的是未来！Karpathy 放大招，将自我迭代智能体放进单个 GPU](https://news.qq.com/rain/a/20260308A03IR700) - 腾讯网对 Karpathy autoresearch 项目的中文报道。 (腾讯网 2026)
- [从认知行为看语言模型的自我进化](https://feiyang.ai/blog/cognitive-behaviors-self-improvement) - 中文博客，从验证/回溯/子目标/逆向推理四类认知行为剖析模型自我进化。 (智人飞扬 2025)

## Blog Posts & Discussions（博客文章与讨论）

- [A Taxonomy of Self-Evolving Agents](https://lsl.zone/blog/2026/a-taxonomy-of-self-evolving-agents/) - 区分 Model、Harness 与 Artifact 进化，与本清单的分类体系互补。 (2026)
- [Hyra: A simple yet effective scaffold for general discovery](https://hy.tencent.com/research/hyra) - 腾讯混元关于 Hyra-1.0 的报告：一个用于性能导向研究与工程任务的递归自我改进智能体。 (2026) ★中文团队
- [AI4AI at Scale: Building Open-Weight Deep Search Agents](https://xyz-lab.ai/blogs/ai4ai-at-scale/) - 行业技术报告：有界、验证门控的 AI-for-AI 循环，智能体团队诊断失败并应用范围化更改。 (2026)
- [First Steps Toward Automated AI Research](https://recursive.com/articles/first-steps-toward-automated-ai-research) - 描述一个闭合「想法提出→实现→实验→验证→下一实验选择」全循环的自动化研究系统。 (2026)
- [Harness Engineering for Self-Improvement](https://lilianweng.github.io/posts/2026-07-04-harness/) - Lilian Weng 对外壳工程作为 RSI 近期路径的综述。 (2026)
- [AlphaEvolve: A Gemini-Powered Coding Agent for Designing Advanced Algorithms](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/) - Google DeepMind 讲解 AlphaEvolve 的评估器引导进化循环。 (2025)
- [The Darwin Gödel Machine: AI That Improves Itself by Rewriting Its Own Code](https://sakana.ai/dgm/) - Sakana AI 解释 DGM 的自我修改实证替代方案。 (2025)
- [When AI Builds Itself](https://www.anthropic.com/institute/recursive-self-improvement) - Anthropic 分析 AI 驱动 AI 发展的早期证据、可能路径与治理挑战。 (2025)
- [The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery](https://sakana.ai/ai-scientist/) - Sakana AI 介绍其自动化研究流水线、结果、局限与开源实现。 (2024)
- [Evidence on Recursive Self-Improvement from Current ML](https://www.lesswrong.com/posts/byKF3mnaNRrbkDPWv/evidence-on-recursive-self-improvement-from-current-ml) - 回顾 AI 辅助 AI 研究强回报的正反经验证据。 (2023)
- [FunSearch: Making New Discoveries in Mathematical Sciences Using Large Language Models](https://deepmind.google/blog/funsearch-making-new-discoveries-in-mathematical-sciences-using-large-language-models/) - Google DeepMind 描述进化程序搜索如何产生可验证的数学与算法发现。 (2023)
- [Metalearning Machines Learn to Learn](https://people.idsia.ch/~juergen/metalearning.html) - Jürgen Schmidhuber 追溯自指元学习从 1987 年到 Gödel Machine 与学习型优化器的发展。 (2020)
- [Recursive Self-Improvement](https://www.alignmentforum.org/w/recursive-self-improvement) - Alignment Forum 概述，连接自我改进 AI 与起飞动力学、种子 AI 与控制问题。 (2016)

## Talks & Videos（演讲与视频）

- [Escape Velocity: The Inflection Point for Recursive Self Improvement](https://slideslive.com/39064188/escape-velocity-the-inflection-point-for-recursive-self-improvement) - Louis Kirsch 在 ICLR 2026 RSI Workshop 讨论自动化 AI 研究与持续递归改进所需条件。 (2026)
- [ICLR 2026 Workshop on AI with Recursive Self-Improvement](https://iclr.cc/virtual/2026/workshop/10000796) - 首个专门聚焦 RSI 研讨会的官方视频档案。 (2026)
- [Self-Improving Foundation Models Without Human Supervision](https://iclr.cc/virtual/2025/workshop/23971) - ICLR 2025 研讨会官方录像，涵盖合成数据、弱到强学习与自主适应。 (2025)
- [Gödel Machine](https://www.youtube.com/watch?v=voczu4I3_xQ) - Jürgen Schmidhuber 简明解释自指、证明引导的代码重写及其可计算性极限。 (2015)
- [【Frontier】递归式自我提升：回顾和展望 | ICLR 2026 | Louis Kirsch](https://www.bilibili.com/video/BV1YRVy6nEzT/) - B 站 UP 主「至高机器智能」翻译的 Louis Kirsch RSI 报告，附中文讲解。 (B站 2026)
- [【干货】Karpathy 最新访谈：Code Agent，Auto Research 和 AI 的自我循环时代](https://www.bilibili.com/video/BV1dwAczDEXY/) - Karpathy 谈自动化科研与递归式自我改进的中文访谈精讲。 (B站 2026)
- [【No Priors 播客】安德烈·卡帕西：编程智能体、自动化科研与 AI 的循环时代](https://www.bilibili.com/video/BV1PbAczPEiZ/) - Karpathy 与 Sarah Guo 对谈 AutoResearch 的中文字幕版。 (B站 2026)

## Related Awesome Lists（相关 Awesome 清单）

RSI 已成为一个活跃的策展领域，GitHub 上并存着多份主题相近的清单。下面按「RSI 专题清单」与「相邻清单」分开列出，便于交叉检索与互补阅读。

### RSI 专题清单（RSI-focused Awesome Lists）

- [lobehub/awesome-rsi](https://github.com/lobehub/awesome-rsi) - 本清单的翻译底本。按模型、智能体、外壳、具身系统、自动化 AI 研发、基准与安全组织的研究地图。 (185★, 2026)
- [Prism-Shadow/awesome-rsi](https://github.com/Prism-Shadow/awesome-rsi) - 聚焦「RSI 方法 + 基准」的清单，附带可筛选的网站（基准筛选板、引用图、方法与系统列表），可按时序或引用量阅读。 (139★, 2026)
- [theseus-labs-rsi/awesome-rsi](https://github.com/theseus-labs-rsi/awesome-rsi) - 与同名综述配套的清单，按 L1–L5「自主性层级」组织，收录规模最大（500+ 论文）。 (27★, 2026)
- [pinkbubblebubble/awesome-rsi](https://github.com/pinkbubblebubble/awesome-rsi) - 强调「证据意识」的清单，明确区分自证改进与有界精炼，并附「可信 RSI 评估应报告什么」清单。 (26★, 2026)
- [Liuziyu77/Awesome-RSI](https://github.com/Liuziyu77/Awesome-RSI) - 按「从经验到系统再到模型」的线索组织，条目多附带任务摘要与代码/权重链接。 (24★, 2026)
- [Picrew/awesome-rsi](https://github.com/Picrew/awesome-rsi) - 按自我训练、评估与安全等机制分类，并给出每篇工作的任务与证据类型标注。 (21★, 2026)
- [Lee1003-lee/Awesome-RSI-Research](https://github.com/Lee1003-lee/Awesome-RSI-Research) - 聚焦 RSI 研究论文的整理清单。 (8★, 2026)
- [Token-Rhythm/awesome-rsi](https://github.com/Token-Rhythm/awesome-rsi) - 按「改什么」分类：权重、提示、记忆、技能、工具、工作流、源码或改进机制本身。 (4★, 2026)
- [asimfish/awesome_rsi](https://github.com/asimfish/awesome_rsi) - 收录 67 篇论文，并为每篇提供中文精读报告、双语 PDF、时间线/分类图、幻灯片与长篇总报告，中文读者的深度入口。 (2026)
- [ballooooooon/awesome-rsi](https://github.com/ballooooooon/awesome-rsi) - 覆盖自我进化智能体与 RSI 的论文、开源项目与产品。 (2026)
- [SUPERZJ827/awesome-RSI](https://github.com/SUPERZJ827/awesome-RSI) / [Omni-Scientist/Awesome-RSI](https://github.com/Omni-Scientist/Awesome-RSI) / [AltanReisoglu/awesome-rsi](https://github.com/AltanReisoglu/awesome-rsi) - 规模较小的 RSI 论文清单，可作为交叉校验的补充来源。 (2026)
- [fendouai/awesome-rsi-zh](https://github.com/fendouai/awesome-rsi-zh) - 本清单仓库。中文整理，在 lobehub 版本基础上增补中文资源、近年新工作与中文团队成果。

### 相邻清单（Adjacent Awesome Lists）

- [Awesome AI Agents](https://github.com/e2b-dev/awesome-ai-agents) - 自主智能体项目与基础设施的广谱目录，可作为自我改进系统的组件或基线。 (2023)
- [Awesome AutoML Papers](https://github.com/hibayesian/awesome-automl-papers) - 自动化模型选择、架构搜索、超参数优化及相关技术的策展文献。 (2018)
- [Awesome Self-Improving Agents](https://github.com/selfimproving-agent/awesome-Self-Improving-Agents) - 聚焦更新自身模型、记忆、工具、提示或工作流的基础模型智能体的书目。 (2024)
- [Recursive Self-Improvement Research Atlas（递归式自我改进研究地图）](https://github.com/Linwei-Chen/recursive-self-improvement-research-atlas) - 中文 RSI 研究地图，按七条路线分层梳理证据与验证瓶颈。 (2026)

## 按改进强度索引（Index by Improvement Strength）

同一批工作按「改进强度」重新分组，便于跨章节检索同一类系统；三档定义见[范围与术语](#scope--terminology范围与术语)。

**真递归（33 条）** —— 改进「产生改进的机制」本身（改进器、判据、外壳进化器、搜索策略）。

- [Agentic Harness Engineering: Observability-Driven Automatic Evolution of Coding-Agent Harnesses](https://arxiv.org/abs/2604.25850)
- [CoEvoSkills: Self-Evolving Agent Skills via Co-Evolutionary Verification](https://arxiv.org/abs/2604.01687)
- [Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents](https://arxiv.org/abs/2505.22954)
- [HarnessBank: Semantic Gene-Bank Search with Gated Verification for Agent-Harness Self-Evolution](https://arxiv.org/abs/2607.13683)
- [Hierarchical Self-Improvement: A Framework for Task-Specific Evolvable Agent Harnesses](https://arxiv.org/abs/2608.08466)
- [Hyperagents](https://arxiv.org/abs/2603.19461)
- [Meta-Harness: End-to-End Optimization of Model Harnesses](https://arxiv.org/abs/2603.28052)
- [Metaⁿ: Recursive Self-Improvement through Emergent Depth](https://arxiv.org/abs/2608.24735)
- [MetaRSI / RSI²: A Meta-Recursive Self-Improving System for Recursive Self-Improving Systems Themselves](https://arxiv.org/abs/2609.06396)
- [MetaSkill-Evolve: Recursive Self-Improvement of LLM Agents via Two-Timescale Meta-Skill Evolution](https://arxiv.org/abs/2607.05297)
- [MOSS: Self-Evolution through Source-Level Rewriting in Autonomous Agent Systems](https://arxiv.org/abs/2605.22794)
- [Ouroboros: A Self-Developing Frontier Coding Agent with Reviewed Core Evolution](https://arxiv.org/abs/2608.08311)
- [Prime Agent: A Self-Improving RLM Harness](https://arxiv.org/abs/2608.23552)
- [Recursive Harness Self-Improvement (RHI)](https://arxiv.org/abs/2607.15524)
- [Recursive Self-Evolving Agents via Held-Out Selection (RSEA)](https://arxiv.org/abs/2606.28374)
- [Self-Harness: Harnesses That Improve Themselves](https://arxiv.org/abs/2606.09498)
- [The Red Queen Gödel Machine: Co-Evolving Agents and Their Evaluators](https://arxiv.org/abs/2606.26294)
- [Who Grades the Grader? Co-Evolving Evaluation Metrics and Skills for Self-Improving LLM Agents](https://arxiv.org/abs/2607.12790)
- [A Self-Improving Coding Agent](https://arxiv.org/abs/2504.15228)
- [Can Large Language Models Invent Algorithms to Improve Themselves? (Self-Developing)](https://aclanthology.org/2025.naacl-long.519/)
- [Gödel Agent: A Self-Referential Agent Framework for Recursive Self-Improvement](https://arxiv.org/abs/2410.04444)
- [Huxley-Gödel Machine (HGM)](https://arxiv.org/abs/2510.21614)
- [MemEvolve: Meta-Evolution of Agent Memory Systems](https://arxiv.org/abs/2512.18746)
- [Higher Order and Self-Referential Evolution for Population-based Methods](https://openreview.net/forum?id=3tk6AES1Aj)
- [Promptbreeder: Self-Referential Self-Improvement Via Prompt Evolution](https://arxiv.org/abs/2309.16797)
- [Self-Taught Optimizer (STOP): Recursively Self-Improving Code Generation](https://arxiv.org/abs/2310.02304)
- [Gödel Machines: Self-Referential Universal Problem Solvers Making Provably Optimal Self-Improvements](https://arxiv.org/abs/cs/0309048)
- [Darwin Gödel Machine](https://github.com/jennyzzt/dgm)
- [Gödel Agent](https://github.com/Arvid-pku/Godel_Agent)
- [HyperAgents](https://github.com/facebookresearch/HyperAgents)
- [Prime Agent](https://github.com/PrimeIntellect-ai/prime-agent)
- [Self-Improving Coding Agent](https://github.com/MaximeRobeyns/self_improving_coding_agent)
- [yoyo-evolve](https://github.com/yologdev/yoyo-evolve)

**持久改进（134 条）** —— 对权重、记忆、技能、外壳或代码的改动会被后续轮次继承，但改进算子固定。

- [Adaptive Auto-Harness: Sustained Self-Improvement for Agentic System Deployment on Open-Ended Task Streams](https://arxiv.org/abs/2606.01770)
- [AgentFactory: A Self-Evolving Framework Through Executable Subagent Accumulation and Reuse](https://arxiv.org/abs/2603.18000)
- [Agentic Context Engineering: Evolving Contexts for Self-Improving Language Models](https://arxiv.org/abs/2510.04618)
- [AI4AI at Test-Time: Strong-to-Weak Capability Transfer via Harnesses](https://arxiv.org/abs/2608.12307)
- [APEX: Autonomous Policy Exploration for Self-Evolving LLM Agents](https://arxiv.org/abs/2605.21240)
- [ASPIRE: Agentic Skills Discovery for Robotics](https://arxiv.org/abs/2607.00272)
- [AutoHarness: Improving LLM Agents by Automatically Synthesizing a Code Harness](https://arxiv.org/abs/2603.03329)
- [AutoSaddler: Automatic Harness Optimization with Durable Updates from Agent Execution Traces](https://arxiv.org/abs/2608.23041)
- [Continual Harness: Online Adaptation for Self-Improving Foundation Agents](https://arxiv.org/abs/2605.09998)
- [CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery](https://arxiv.org/abs/2604.01658)
- [ENPIRE: Agentic Robot Policy Self-Improvement in the Real World](https://arxiv.org/abs/2606.19980)
- [Evo-Harness: Context-to-Harness Skill Compilation for Self-Evolving Agents](https://arxiv.org/abs/2608.15071)
- [EvoAgent: An Evolvable Agent Framework with Skill Learning and Multi-Agent Delegation](https://arxiv.org/abs/2604.20133)
- [EvoHarness-RL: Learning Self-Evolving Runtime Harness for Long-Horizon LLM Agents](https://arxiv.org/abs/2608.05446)
- [EvoLM: Self-Evolving Language Models through Co-Evolved Discriminative Rubrics](https://arxiv.org/abs/2605.03871)
- [EvolveR: Self-Evolving LLM Agents through an Experience-Driven Lifecycle](https://arxiv.org/abs/2510.16079)
- [Evolving Agents in the Dark: Retrospective Harness Optimization via Self-Preference (RHO)](https://arxiv.org/abs/2606.05922)
- [From Failed Trajectories to Reliable LLM Agents: Diagnosing and Repairing Harness Flaws (HarnessFix)](https://arxiv.org/abs/2606.06324)
- [From Procedural Skills to Strategy Genes: Towards Experience-Driven Test-Time Evolution](https://arxiv.org/abs/2604.15097)
- [Frontis-MA1: Training an AI4AI Model towards Recursive Self-Improvement in Machine Learning Engineering](https://arxiv.org/abs/2607.28568)
- [G-Zero: Self-Play for Open-Ended Generation from Zero Data](https://arxiv.org/abs/2605.09959)
- [GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning](https://arxiv.org/abs/2507.19457)
- [Group-Evolving Agents: Open-Ended Self-Improvement via Experience Sharing](https://arxiv.org/abs/2602.04837)
- [HASE: Harness-Aware Self-Evolving](https://arxiv.org/abs/2607.03935)
- [Learning to Continually Learn via Meta-learning Agentic Memory Designs](https://arxiv.org/abs/2602.07755)
- [Learning to Self-Evolve](https://arxiv.org/abs/2603.18620)
- [MemoHarness: Agent Harnesses That Learn from Experience](https://arxiv.org/abs/2607.14159)
- [Metis: Bridging Text and Code Memory for Self-Evolving Agents](https://arxiv.org/abs/2606.24151)
- [MineEvolve: Self-Evolution with Accumulated Knowledge for Long-Horizon Embodied Minecraft Agents](https://arxiv.org/abs/2603.13131)
- [MLEvolve: A Self-Evolving Framework for Automated Machine Learning Algorithm Discovery](https://arxiv.org/abs/2606.06473)
- [PACEvolve: Enabling Long-Horizon Progress-Aware Consistent Evolution](https://arxiv.org/abs/2601.10657)
- [PRACTICE: From Experience to Expertise in Self-Evolving Embodied Agents](https://arxiv.org/abs/2608.30760)
- [R-Zero: Self-Evolving Reasoning LLM from Zero Data](https://arxiv.org/abs/2508.05004)
- [Recursive Synthesis for Long-Horizon Terminal Tasks](https://arxiv.org/abs/2608.05466)
- [RISE: Self-Improving Robot Policy with Compositional World Model](https://arxiv.org/abs/2602.11075)
- [SAGE: Multi-Agent Self-Evolution for LLM Reasoning](https://arxiv.org/abs/2603.15255)
- [Self-Evolving Embodied Agents via Skill-Harness Evolution](https://arxiv.org/abs/2608.11350)
- [Self-evolving LLM Agents with in-distribution Optimization (Q-Evolve)](https://arxiv.org/abs/2606.07367)
- [Self-Improving Vision-Language-Action Models with Data Generation via Residual RL](https://iclr.cc/virtual/2026/poster/10008318)
- [SERPO: Self-Evolving Rubric Policy Optimization for Open-Ended Test-Time Reinforcement Learning](https://arxiv.org/abs/2607.26873)
- [SIA: Self Improving AI with Harness & Weight Updates](https://arxiv.org/abs/2605.27276)
- [SkillOpt: Executive Strategy for Self-Evolving Agent Skills](https://arxiv.org/abs/2605.23904)
- [SkillRise: Agentic Reinforcement Learning for Cross-Task Skill Evolution](https://arxiv.org/abs/2607.26784)
- [SkillRL: Evolving Agents via Recursive Skill-Augmented Reinforcement Learning](https://arxiv.org/abs/2602.08234)
- [Socratic-SWE: Self-Evolving Coding Agents via Trace-Derived Agent Skills](https://arxiv.org/abs/2606.07412)
- [SPADE: Self-Play in Adaptive Synthetic Executable Environments](https://arxiv.org/abs/2608.19197)
- [Teaching LLMs to Self-Evolve: Cultivating Core Meta-Skills with Reinforcement Learning](https://arxiv.org/abs/2607.21971)
- [TEMPO: Scaling Test-time Training for Large Reasoning Models](https://arxiv.org/abs/2604.19295)
- [Trace2Skill: Distill Trajectory-Local Lessons into Transferable Agent Skills](https://arxiv.org/abs/2603.25158)
- [WikiSkill: Compiling Agent Experience into Persistent Knowledge for Skill Evolution](https://arxiv.org/abs/2608.27454)
- [A-MEM: Agentic Memory for LLM Agents](https://arxiv.org/abs/2502.12110)
- [Absolute Zero: Reinforced Self-play Reasoning with Zero Data](https://arxiv.org/abs/2505.03335)
- [Adaptive Self-Improvement for ML Library Development](https://arxiv.org/abs/2502.02534)
- [AFlow: Automating Agentic Workflow Generation](https://arxiv.org/abs/2410.10762)
- [Agent0: Unleashing Self-Evolving Agents from Zero Data via Tool-Integrated Reasoning](https://arxiv.org/abs/2511.16043)
- [Alita-G: Self-Evolving Generative Agent for Agent Generation](https://arxiv.org/abs/2510.23601)
- [AlphaEvolve: A Coding Agent for Scientific and Algorithmic Discovery](https://arxiv.org/abs/2506.13131)
- [Audited Skill-Graph Self-Improvement for Agentic LLMs via Verifiable Rewards, Experience Synthesis, and Continual Memory (ASG-SI)](https://arxiv.org/abs/2512.23760)
- [Automated Design of Agentic Systems](https://arxiv.org/abs/2408.08435)
- [DEBATE, TRAIN, EVOLVE: Self Evolution of Language Model Reasoning](https://arxiv.org/abs/2505.15734)
- [DeepSeek-GRM: Inference-Time Scaling for Generalist Reward Modeling](https://arxiv.org/abs/2504.02495)
- [DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning](https://arxiv.org/abs/2501.12948)
- [EvoAgent: Towards Automatic Multi-Agent Generation via Evolutionary Algorithms](https://arxiv.org/abs/2406.14228)
- [EvoAgentX: An Automated Framework for Evolving Agentic Workflows](https://arxiv.org/abs/2507.03616)
- [Live-SWE-agent: Can Software Engineering Agents Self-Evolve on the Fly?](https://arxiv.org/abs/2511.13646)
- [Meta-Rewarding Language Models: Self-Improving Alignment with LLM-as-a-Meta-Judge](https://arxiv.org/abs/2407.19594)
- [R-FEW: Guided Self-Evolving LLMs with Minimal Human Supervision](https://arxiv.org/abs/2512.02472)
- [rStar-Math: Small LLMs Can Master Math Reasoning with Self-Evolved Deep Thinking](https://arxiv.org/abs/2501.04519)
- [Self-Adapting Language Models](https://arxiv.org/abs/2506.10943)
- [Self-evolving Agents with Reflective and Memory-Augmented Abilities](https://arxiv.org/abs/2409.00872)
- [Self-Play Preference Optimization for Language Model Alignment](https://arxiv.org/abs/2405.00675)
- [SIMA 2: A Generalist Embodied Agent for Virtual Worlds](https://arxiv.org/abs/2512.04797)
- [TextGrad: Automatic "Differentiation" via Text](https://arxiv.org/abs/2406.07496)
- [Training Software Engineering Agents and Verifiers with SWE-Gym](https://arxiv.org/abs/2412.21139)
- [TTRL: Test-Time Reinforcement Learning](https://arxiv.org/abs/2504.16084)
- [Agent-Pro: Learning to Evolve via Policy-Level Reflection and Optimization](https://arxiv.org/abs/2402.17574)
- [Beyond Human Data: Scaling Self-Training for Problem-Solving with Language Models](https://arxiv.org/abs/2312.06585)
- [EnvGen: Generating and Adapting Environments via LLMs for Training Embodied Agents](https://arxiv.org/abs/2403.12014)
- [Eureka: Human-Level Reward Design via Coding Large Language Models](https://arxiv.org/abs/2310.12931)
- [ExpeL: LLM Agents Are Experiential Learners](https://arxiv.org/abs/2308.10144)
- [Large Language Models as Optimizers](https://arxiv.org/abs/2309.03409)
- [Mathematical Discoveries from Program Search with Large Language Models](https://www.nature.com/articles/s41586-023-06924-6)
- [MemoryBank: Enhancing Large Language Models with Long-Term Memory](https://arxiv.org/abs/2305.10250)
- [OS-Copilot: Towards Generalist Computer Agents with Self-Improvement](https://arxiv.org/abs/2402.07456)
- [Quiet-STaR: Language Models Can Teach Themselves to Think Before Speaking](https://arxiv.org/abs/2403.09629)
- [Qwen2.5-Math Technical Report: Toward Mathematical Expert Model Via Self-Improvement](https://arxiv.org/abs/2409.12122)
- [ReST-MCTS*: LLM Self-Training via Process Reward Guided Tree Search](https://arxiv.org/abs/2406.03816)
- [RLAIF vs. RLHF: Scaling Reinforcement Learning from Human Feedback with AI Feedback](https://arxiv.org/abs/2309.00267)
- [Self-Alignment with Instruction Backtranslation](https://arxiv.org/abs/2308.06259)
- [Self-Play Fine-Tuning Converts Weak Language Models to Strong Language Models](https://arxiv.org/abs/2401.01335)
- [Self-Rewarding Language Models](https://arxiv.org/abs/2401.10020)
- [Self-Taught Evaluators](https://arxiv.org/abs/2408.02666)
- [SOTOPIA-π: Interactive Learning of Socially Intelligent Language Agents](https://arxiv.org/abs/2403.08715)
- [Voyager: An Open-Ended Embodied Agent with Large Language Models](https://arxiv.org/abs/2305.16291)
- [Automatic Prompt Optimization with "Gradient Descent" and Beam Search](https://arxiv.org/abs/2305.03495)
- [DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines](https://arxiv.org/abs/2310.03714)
- [EvoPrompt: Connecting LLMs with Evolutionary Algorithms Yields Powerful Prompt Optimizers](https://arxiv.org/abs/2309.08532)
- [Large Language Models Are Human-Level Prompt Engineers (APE)](https://arxiv.org/abs/2211.01910)
- [Large Language Models Can Self-Improve](https://arxiv.org/abs/2210.11610)
- [Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366)
- [Reinforced Self-Training (ReST) for Language Modeling](https://arxiv.org/abs/2308.08998)
- [Self-Instruct: Aligning Language Models with Self-Generated Instructions](https://arxiv.org/abs/2212.10560)
- [SELF: Self-Evolution with Language Feedback](https://arxiv.org/abs/2310.00533)
- [STaR: Bootstrapping Reasoning With Reasoning](https://arxiv.org/abs/2203.14465)
- [AutoML-Zero: Evolving Machine Learning Algorithms From Scratch](https://arxiv.org/abs/2003.03384)
- [Eliciting Knowledge from Language Models Using Automatically Generated Prompts](https://arxiv.org/abs/2010.15980)
- [Paired Open-Ended Trailblazer (POET): Endlessly Generating Increasingly Complex and Diverse Learning Environments and Their Solutions](https://arxiv.org/abs/1901.01753)
- [Learning to Learn by Gradient Descent by Gradient Descent](https://arxiv.org/abs/1606.04474)
- [POWERPLAY: Training an Increasingly General Problem Solver by Continually Searching for the Simplest Still Unsolvable Problem](https://arxiv.org/abs/1112.5309)
- [ACE](https://github.com/ace-agent/ace)
- [ADAS](https://github.com/ShengranHu/ADAS)
- [AgentEvolver](https://github.com/modelscope/AgentEvolver)
- [AgentFactory](https://github.com/zzatpku/AgentFactory)
- [ALMA](https://github.com/zksha/alma)
- [Autogenesis](https://github.com/DVampire/Autogenesis)
- [Continual Harness](https://github.com/sethkarten/continual-harness)
- [EvoAgentX](https://github.com/EvoAgentX/EvoAgentX)
- [Evolutionary Model Merge](https://github.com/SakanaAI/evolutionary-model-merge)
- [EvolveR](https://github.com/KnowledgeXLab/EvolveR)
- [FunSearch](https://github.com/google-deepmind/funsearch)
- [GenericAgent](https://github.com/lsdefine/GenericAgent)
- [Gear](https://github.com/rsi-gear/gear)
- [Hermes Agent](https://github.com/NousResearch/hermes-agent)
- [Letta Code](https://github.com/letta-ai/letta-code)
- [Memento-Skills](https://github.com/Memento-Teams/Memento-Skills)
- [MLEvolve](https://github.com/InternScience/MLEvolve)
- [OmniAgent](https://github.com/YeQing17-2026/OmniAgent)
- [OpenEvolve](https://github.com/algorithmicsuperintelligence/openevolve)
- [POET](https://github.com/uber-research/poet)
- [Reef](https://github.com/Human-Agent-Society/reef)
- [SE-Agent](https://github.com/JARVIS-Xs/SE-Agent)
- [SEAL](https://github.com/Continual-Intelligence/SEAL)
- [SIA](https://github.com/hexo-ai/sia)
- [Voyager](https://github.com/MineDojo/Voyager)

**支撑技术（107 条）** —— 不产生持久改变，或本身不改进系统，为上述提供验证、评测、理论、安全与基础设施。

- [A Survey of Self-Evolving Agents: On Path to Artificial Super Intelligence](https://arxiv.org/abs/2507.21046)
- [AI4AI-Bench](https://arxiv.org/abs/2608.20318)
- [AIRA_2: Overcoming Bottlenecks in AI Research Agents](https://arxiv.org/abs/2603.26499)
- [Anthropic Autonomous AI R&D Evaluations](https://www.anthropic.com/transparency/model-report)
- [ARC-AGI-3: A New Challenge for Frontier Agentic Intelligence](https://arxiv.org/abs/2603.24621)
- [AutoLab: Can Frontier Models Solve Long-Horizon Auto Research and Engineering Tasks?](https://arxiv.org/abs/2606.05080)
- [AutoResearch: Insight In, Hallucination Out](https://arxiv.org/abs/2608.17906)
- [ContinualSkillBench](https://arxiv.org/abs/2608.03874)
- [Emergent Introspective Awareness in Large Language Models](https://arxiv.org/abs/2601.01828)
- [EnvHarness: Awakening Static Worlds for Agent Learning](https://arxiv.org/abs/2608.19880)
- [EvoScientist: Towards Multi-Agent Evolving AI Scientists for End-to-End Scientific Discovery](https://arxiv.org/abs/2603.08127)
- [Frontier-Eng](https://arxiv.org/abs/2604.12290)
- [FT-Dojo: Towards Autonomous LLM Fine-Tuning with Language Agents](https://arxiv.org/abs/2603.01712)
- [Google DeepMind Frontier Safety Framework (FSF) ML R&D](https://deepmind.google/blog/strengthening-our-frontier-safety-framework/)
- [Harness Updating Is Not Harness Benefit: Disentangling Evolution Capabilities in Self-Evolving LLM Agents](https://arxiv.org/abs/2605.30621)
- [Long-Horizon-Terminal-Bench](https://arxiv.org/abs/2607.08964)
- [LongWoF-Bench: Evaluating EvoMap Genes for Verifiable Long-Workflow Tasks](https://arxiv.org/abs/2608.23200)
- [MLS-Bench: A Holistic and Rigorous Assessment of AI Systems on Building Better AI](https://arxiv.org/abs/2605.08678)
- [OpenAI AI Self-Improvement Evaluations](https://deploymentsafety.openai.com/gpt-5-6)
- [OSWorld 2.0](https://arxiv.org/abs/2606.29537)
- [PAST-Bench](https://arxiv.org/abs/2608.04003)
- [PostTrainBench: Can LLM Agents Automate LLM Post-Training?](https://arxiv.org/abs/2603.08640)
- [Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops](https://arxiv.org/abs/2607.07663)
- [RSI-Bench](https://github.com/sunghunkwag/rsi-bench)
- [RSIBench-Data](https://arxiv.org/abs/2607.25886)
- [S3Gym: Can LLMs Turn Self-Testing and Self-Judging into Self-Improvement?](https://arxiv.org/abs/2608.31100)
- [SafeEvolve: Harness-Policy Co-Evolution from Agent Experience for Safety Alignment](https://arxiv.org/abs/2609.02786)
- [SAHOO: Safeguarded Alignment for High-Order Optimization Objectives in Recursive Self-Improvement](https://arxiv.org/abs/2603.06333)
- [SEAGym](https://arxiv.org/abs/2606.17546)
- [Self-evolving Embodied AI](https://arxiv.org/abs/2602.04411)
- [Self-Improvement Can Self-Regress: The Rise-and-Collapse Failure Mode of LLM Self-Training](https://arxiv.org/abs/2606.21090)
- [Self-Improvements in Modern Agentic Systems: A Survey](https://arxiv.org/abs/2607.13104)
- [Self-Reference in Large Language Models: The Introspection Threshold for Recursive Self-Improvement](https://arxiv.org/abs/2607.04277)
- [Structure Enables Effective Self-Localization of Errors in LLMs](https://arxiv.org/abs/2602.02416)
- [TamperBench: Systematically Stress-Testing LLM Safety Under Fine-Tuning and Tampering](https://arxiv.org/abs/2602.06911)
- [The Economics of Recursive Self-Improvement](https://elasticity.institute/rsi-paper.pdf)
- [The Last AI Built by Humans: Toward Genuine Recursive Self-Improvement](https://arxiv.org/abs/2609.11873)
- [Towards End-to-End Automation of AI Research (The AI Scientist-v2)](https://doi.org/10.1038/s41586-026-10265-5)
- [Towards Execution-Grounded Automated AI Research](https://arxiv.org/abs/2601.14525)
- [Your Agent May Misevolve: Emergent Risks in Self-evolving LLM Agents](https://arxiv.org/abs/2509.26354)
- [A Comprehensive Survey of Self-Evolving AI Agents: A New Paradigm Bridging Foundation Models and Lifelong Agentic Systems](https://arxiv.org/abs/2508.07407)
- [AI Sandbagging: Language Models can Strategically Underperform on Evaluations](https://arxiv.org/abs/2406.07358)
- [Cognitive Behaviors that Enable Self-Improving Reasoners, or, Four Habits of Highly Effective STaRs](https://arxiv.org/abs/2503.01307)
- [Escaping Model Collapse via Synthetic Data Verification: Near-term Improvements and Long-term Convergence](https://arxiv.org/abs/2510.16657)
- [Evaluating Goal Drift in Language Model Agents](https://arxiv.org/abs/2505.02709)
- [Looking Inward: Language Models Can Learn About Themselves by Introspection](https://arxiv.org/abs/2410.13787)
- [MCPMark](https://arxiv.org/abs/2509.24002)
- [Measuring AI Ability to Complete Long Software Tasks (METR Time Horizon)](https://arxiv.org/abs/2503.14499)
- [MLE-bench](https://github.com/openai/mle-bench)
- [PaperBench](https://github.com/openai/frontier-evals/tree/main/project/paperbench)
- [RE-Bench](https://github.com/METR/RE-Bench)
- [Self-Improvement in Language Models: The Sharpening Mechanism](https://arxiv.org/abs/2412.01951)
- [SGM: A Statistical Gödel Machine for Risk-Controlled Recursive Self-Modification](https://arxiv.org/abs/2510.10232)
- [SWE-Bench Pro](https://arxiv.org/abs/2509.16941)
- [Tell me about yourself: LLMs are aware of their learned behaviors](https://arxiv.org/abs/2501.11120)
- [TheAgentCompany](https://arxiv.org/abs/2412.14161)
- [Will Compute Bottlenecks Prevent an Intelligence Explosion?](https://arxiv.org/abs/2507.23181)
- [A Survey on Self-Evolution of Large Language Models](https://arxiv.org/abs/2404.14387)
- [Chain-of-Verification Reduces Hallucination in Large Language Models](https://arxiv.org/abs/2309.11495)
- [CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing](https://arxiv.org/abs/2305.11738)
- [Encouraging Divergent Thinking in Large Language Models through Multi-Agent Debate](https://arxiv.org/abs/2305.19118)
- [Improving Factuality and Reasoning in Language Models through Multiagent Debate](https://arxiv.org/abs/2305.14325)
- [Language Agent Tree Search Unifies Reasoning, Acting, and Planning in Language Models](https://arxiv.org/abs/2310.04406)
- [Large Language Models Cannot Self-Correct Reasoning Yet](https://arxiv.org/abs/2310.01798)
- [Let's Verify Step by Step](https://arxiv.org/abs/2305.20050)
- [MLAgentBench](https://github.com/snap-stanford/MLAgentBench)
- [Recursive Introspection: Teaching Language Model Agents How to Self-Improve](https://arxiv.org/abs/2407.18219)
- [Self-Recognition in Language Models](https://arxiv.org/abs/2407.06946)
- [Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training](https://arxiv.org/abs/2401.05566)
- [SWE-bench](https://github.com/SWE-bench/SWE-bench)
- [SWE-bench Verified](https://openai.com/index/introducing-swe-bench-verified/)
- [Teaching Large Language Models to Self-Debug](https://arxiv.org/abs/2304.05128)
- [The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery](https://arxiv.org/abs/2408.06292)
- [AgentCoder: Multi-Agent-based Code Generation with Iterative Testing and Optimisation](https://arxiv.org/abs/2312.13010)
- [Do Large Language Models Know What They Don't Know?](https://arxiv.org/abs/2305.18153)
- [Model Evaluation for Extreme Risks](https://arxiv.org/abs/2305.15324)
- [Self-Consistency Improves Chain of Thought Reasoning in Language Models](https://arxiv.org/abs/2203.11171)
- [Self-Refine: Iterative Refinement with Self-Feedback](https://arxiv.org/abs/2303.17651)
- [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/abs/2212.08073)
- [Language Models (Mostly) Know What They Know](https://arxiv.org/abs/2207.05221)
- [Optimal Policies Tend to Seek Power](https://arxiv.org/abs/1912.01683)
- [Performance of Bounded-Rational Agents With the Ability to Self-Modify](https://arxiv.org/abs/2011.06275)
- [Reward Tampering Problems and Solutions in Reinforcement Learning: A Causal Influence Diagram Perspective](https://arxiv.org/abs/1908.04734)
- [AGI Agent Safety by Iteratively Improving the Utility Function](https://arxiv.org/abs/2007.05411)
- [AI-GAs: AI-Generating Algorithms, an Alternate Paradigm for Producing General Artificial Intelligence](https://arxiv.org/abs/1905.10985)
- [Risks from Learned Optimization in Advanced Machine Learning Systems](https://arxiv.org/abs/1906.01820)
- [A Formulation of Recursive Self-Improvement and Its Possible Efficiency](https://arxiv.org/abs/1805.06610)
- [Scalable Agent Alignment via Reward Modeling: A Research Direction](https://arxiv.org/abs/1811.07871)
- [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565)
- [Quality Diversity: A New Frontier for Evolutionary Computation](https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2016.00040/full)
- [Safely Interruptible Agents](https://auai.org/~w-auai/uai2016/proceedings/papers/68.pdf)
- [Self-Modification of Policy and Utility Function in Rational Agents](https://arxiv.org/abs/1605.03142)
- [From Seed AI to Technological Singularity via Recursively Self-Improving Software](https://arxiv.org/abs/1502.06512)
- [Illuminating Search Spaces by Mapping Elites](https://arxiv.org/abs/1504.04909)
- [Bounded Recursive Self-Improvement](https://arxiv.org/abs/1312.6764)
- [Intelligence Explosion Microeconomics](https://intelligence.org/files/IEM.pdf)
- [The Singularity: A Philosophical Analysis](https://consc.net/papers/singularity.pdf)
- [Optimal Ordered Problem Solver](https://arxiv.org/abs/cs/0207097)
- [Evolutionary Principles in Self-Referential Learning, or on Learning How to Learn: The Meta-Meta-... Hook](https://people.idsia.ch/~juergen/diploma1987ocr.pdf)
- [Speculations Concerning the First Ultraintelligent Machine](https://www.sciencedirect.com/science/article/pii/S0065245808604180)
- [Agent Zero](https://github.com/agent0ai/agent-zero)
- [AI Scientist](https://github.com/SakanaAI/AI-Scientist)
- [autoresearch](https://github.com/karpathy/autoresearch)
- [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)
- [Mechanist](https://github.com/zjunlp/mechanist)
- [OpenClaw](https://github.com/openclaw/openclaw)
- [Pi](https://github.com/earendil-works/pi)

## Contributing（贡献指南）

欢迎贡献。请在提交 Pull Request 前阅读[贡献指南](CONTRIBUTING.md)。

> 本项目基于 [lobehub/awesome-rsi](https://github.com/lobehub/awesome-rsi) 翻译并扩充。新增的中文资源、近年工作与中文团队成果以「★中文团队」或「中文资源」章节标注。
