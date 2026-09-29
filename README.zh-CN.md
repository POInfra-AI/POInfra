<p align="center">
  <img src="assets/poinfra-logo.png" alt="POInfra" width="720">
</p>

<div align="center">
  <a href="#项目"><img src="https://img.shields.io/badge/Papers-arXiv-B31B1B?logo=arxiv" alt="Papers"></a>
  <a href="https://huggingface.co/Guowei-Zou"><img src="https://img.shields.io/badge/Hugging_Face-Models_%26_Data-FFD21E?logo=huggingface" alt="Models and data"></a>
  <a href="#快速开始"><img src="https://img.shields.io/badge/Getting_Started-Guide-8A2BE2?logo=readthedocs" alt="Getting started"></a>
  <a href="#项目"><img src="https://img.shields.io/badge/Code-Project_Repositories-181717?logo=github" alt="Project repositories"></a>
</div>

<div align="center">

[![English](https://img.shields.io/badge/lang-English-blue.svg)](README.md)
[![简体中文](https://img.shields.io/badge/语言-简体中文-red.svg)](README.zh-CN.md)

</div>

<h1 align="center"><sub>POInfra：生成模型的策略优化</sub></h1>

**POInfra 聚焦生成模型的策略优化。** 我们研究如何将扩散模型与流模型用于策略建模，如何通过强化学习改进策略，以及如何利用推理时的额外计算提升决策质量。

我们的研究始于 **D2PPO**，将扩散策略预训练中的分散正则化与 PPO 微调相结合，随后扩展到高效的一步策略、多智能体协同生成、在线微调，以及推理时引导与规划。共同目标是将表达能力强的生成模型转化为有效的决策策略。

**PO** 代表 **Policy Optimization（策略优化）**，**Infra** 体现了围绕这一研究方向构建可复用基础设施的目标。本仓库汇集相关方法和资源，现有实现通过各自的项目仓库运行。

<div align="center">
  <img src="assets/overview.svg" alt="POInfra 研究架构：数据、预训练、策略优化、推理与评估" width="100%">
</div>

## 最新动态

- [2026/09] 🔥 **POInfra** 正式上线，汇集从 D2PPO 开始的生成模型策略优化研究。
- [2026/09] 🔥 **MA-FPPO** 预印本已在 arXiv 上线，项目页提供策略执行视频，以及多智能体流预训练与在线微调的演示。 [Project](https://ma-fppo.github.io/) · [Paper](https://arxiv.org/abs/2609.32594) · [Code](https://github.com/ma-fppo/MA-FPPO).
- [2026/07] 🔥 **G2MAF** 探索多智能体流策略的测试时梯度引导。 [Project](https://g2maf.github.io/) · [Paper](https://arxiv.org/abs/2609.31286) · [Code](https://github.com/g2maf/G2MAF).
- [2026/07] 🔥 **MA-WAM** 探索用于测试时规划的多智能体世界动作模型。 [Project](https://ma-wam.github.io/) · [Paper](https://arxiv.org/abs/2609.31281) · [Code](https://github.com/ma-wam/MA-WAM).
- [2026/05] 🔥 **CoFlow** 提出面向离线多智能体决策的协同少步流方法。 [Project](https://guowei-zou.github.io/coflow/) · [Paper](https://arxiv.org/abs/2605.01457) · [Code](https://github.com/Guowei-Zou/coflow-release).
- [2026/01] 🔥 **OGPO** 的初版预印本以 DMPO 名称发布，该工作现已录用至 **ACM MM 2026**。 [Project](https://ogpo-project.github.io/) · [Paper](https://arxiv.org/abs/2601.20701) · [Code](https://github.com/ogpo-project/OGPO).

- [2025/10] 🔥 **DM1** introduces 分散正则化下的 MeanFlow 一步机器人操作. [Project](https://guowei-zou.github.io/dm1/) · [Paper](https://arxiv.org/abs/2510.07865) · [Code](https://github.com/Guowei-Zou/dm1-release).
- [2025/08] 🔥 **D2PPO** 提出带分散损失的扩散策略优化方法，该工作现已录用至 **AAAI 2026**。 [Project](https://guowei-zou.github.io/d2ppo/) · [Paper](https://arxiv.org/abs/2508.02644) · [Code](https://github.com/Guowei-Zou/d2ppo-release).

## 设计理念与研究方向

POInfra 的核心目标是推动具身智能落地，让机器人走进工厂和千家万户，在真实环境中完成有用的工作，创造生产力和实际价值。围绕这一目标，我们关注一个核心问题：**如何让生成模型从学习已有行为，走向能够持续改进、适应新任务并高效执行的决策策略？**

面向机器人控制与多智能体协作，我们将研究组织为**数据、预训练、策略优化、推理和评估**五个相互关联的环节，研究如何从经验中学习、通过反馈改进，并在有限的交互和计算资源下做出有效决策。

### 从经验中学习，为策略改进建立基础

离线演示与交互轨迹为预训练提供行为经验。**D2PPO** 在扩散策略预训练中引入分散正则化，**DM1** 研究这一正则化在机器人操作的 MeanFlow 策略中的应用。这些工作关注表征多样性与高效动作生成，为后续策略学习建立基础。**CoFlow** 将离线数据学习拓展到多智能体的协同少步轨迹生成。

### 通过环境反馈优化生成策略

策略优化是 POInfra 的核心。**D2PPO** 通过 PPO 微调扩散策略，**OGPO** 研究面向实时机器人控制的一步生成策略优化，**MA-FPPO** 研究多智能体决策中的流策略预训练与在线微调。围绕这些不同类型的生成模型，我们研究如何利用已有经验，并通过任务反馈探索更好的行为。

### 在执行时兼顾响应速度与决策质量

**DM1** 与 **OGPO** 研究一步生成策略，减少动作生成所需的计算。**G2MAF** 通过 Q 值梯度引导，将多智能体流策略的动作调整到估计价值更高的方向。**MA-WAM** 研究用于测试时规划的多智能体世界动作模型。这些方向分别关注动作生成速度、动作价值和未来结果的预测。

### 以任务结果与部署成本检验研究进展

我们根据任务特点，评估成功率、回报、胜率、推理时间和真机表现，同时关注获得这些表现所需的数据、交互与计算成本。评估结果进一步指导预训练、策略优化和推理方法的设计，让方法改进服务于实际部署。

## 项目

### 机器人控制

| 方法 | 研究内容 | 论文 | 项目页 | 代码 |
| --- | --- | --- | --- | --- |
| **D2PPO** | 分散损失下的扩散策略预训练与 PPO 微调 | [AAAI 2026 / arXiv](https://arxiv.org/abs/2508.02644) | [项目页](https://guowei-zou.github.io/d2ppo/) | [D2PPO-release](https://github.com/Guowei-Zou/d2ppo-release) |
| **DM1** | 分散正则化下的 MeanFlow 一步机器人操作 | [arXiv](https://arxiv.org/abs/2510.07865) | [项目页](https://guowei-zou.github.io/dm1/) | [DM1-release](https://github.com/Guowei-Zou/dm1-release) |
| **OGPO** | 面向实时机器人控制的一步生成式策略优化 | [ACM MM 2026 / arXiv](https://arxiv.org/abs/2601.20701) | [项目页](https://ogpo-project.github.io/) | [OGPO-release](https://github.com/ogpo-project/OGPO) |

### 多智能体决策

| 方法 | 研究内容 | 论文 | 项目页 | 代码 |
| --- | --- | --- | --- | --- |
| **CoFlow** | 面向离线多智能体决策的协同少步流生成 | [arXiv](https://arxiv.org/abs/2605.01457) | [项目页](https://guowei-zou.github.io/coflow/) | [CoFlow-release](https://github.com/Guowei-Zou/coflow-release) |
| **MA-FPPO** | 多智能体流预训练策略优化 | [arXiv](https://arxiv.org/abs/2609.32594) | [项目页](https://ma-fppo.github.io/) | [MA-FPPO-release](https://github.com/ma-fppo/MA-FPPO) |
| **G2MAF** | 多智能体流策略的测试时梯度引导 | [arXiv](https://arxiv.org/abs/2609.31286) | [项目页](https://g2maf.github.io/) | [G2MAF-release](https://github.com/g2maf/G2MAF) |
| **MA-WAM** | 用于测试时规划的多智能体世界动作建模 | [arXiv](https://arxiv.org/abs/2609.31281) | [项目页](https://ma-wam.github.io/) | [MA-WAM-release](https://github.com/ma-wam/MA-WAM) |

所有链接的仓库均已公开。G2MAF 和 MA-WAM 目前只有项目 README，尚未包含实现代码。上表中的实现链接指向各项目的独立发布版本，目前尚未整合为统一软件包。

## 研究动机

### D2PPO：方法框架

<p align="center">
  <a href="https://guowei-zou.github.io/d2ppo/"><img src="assets/framework/d2ppo.png" alt="D2PPO 方法框架" width="900"></a>
</p>

[项目页](https://guowei-zou.github.io/d2ppo/)

### OGPO

<p align="center">
  <a href="https://ogpo-project.github.io/"><img src="assets/motivation/ogpo.png" alt="OGPO 研究动机" width="900"></a>
</p>

[项目页](https://ogpo-project.github.io/)

### CoFlow

<p align="center">
  <a href="https://guowei-zou.github.io/coflow/"><img src="assets/motivation/coflow.png" alt="CoFlow 研究动机" width="900"></a>
</p>

[项目页](https://guowei-zou.github.io/coflow/)

### MA-FPPO

<p align="center">
  <a href="https://ma-fppo.github.io/"><img src="assets/motivation/ma-fppo.webp" alt="MA-FPPO 研究动机" width="900"></a>
</p>

[项目页](https://ma-fppo.github.io/)

### G2MAF

<p align="center">
  <a href="https://g2maf.github.io/"><img src="assets/motivation/g2maf.webp" alt="G2MAF 研究动机" width="900"></a>
</p>

[项目页](https://g2maf.github.io/)

### MA-WAM

<p align="center">
  <a href="https://ma-wam.github.io/"><img src="assets/motivation/ma-wam.webp" alt="MA-WAM 研究动机" width="900"></a>
</p>

[项目页](https://ma-wam.github.io/)

## 快速开始

根据你希望研究的问题选择对应实现：

| 目标 | 使用入口 |
| --- | --- |
| 预训练扩散策略并进行 PPO 微调 | [D2PPO 安装与示例](https://github.com/Guowei-Zou/d2ppo-release) |
| 研究机器人操作的一步生成式策略 | [DM1 安装与评估](https://github.com/Guowei-Zou/dm1-release) |
| 研究一步策略的在线优化 | [OGPO 训练与评估](https://github.com/ogpo-project/OGPO) |
| 使用离线多智能体数据训练协同流模型 | [CoFlow 安装与实验](https://github.com/Guowei-Zou/coflow-release#setup) |

例如，可以通过以下命令获取 D2PPO 实现：

```bash
git clone https://github.com/Guowei-Zou/d2ppo-release.git
cd d2ppo-release
```

随后按该仓库的安装说明配置环境和任务。各项目分别提供依赖、数据集、检查点及评估流程的说明。

## 参与贡献

欢迎围绕生成式策略优化、结果复现和跨项目公共组件开展讨论。跨项目的建议可以提交到本仓库的 [Issues](https://github.com/POInfra-AI/POInfra/issues)，具体方法的问题或缺陷请提交到对应的实现仓库。

## 引用

使用相关方法或资源时，请引用对应论文。各项目仓库或网站提供 BibTeX。OGPO 的 arXiv 链接也包含早期 DMPO 预印本的版本记录。

## 维护者

[Guowei Zou](https://github.com/Guowei-Zou) · 中山大学

## 面向实际部署的进一步探索

沿着从学习到部署的过程，POInfra 将研究拓展到以下八个方向：

1. **拓展训练数据。** 利用世界模型生成数据，缓解具身智能数据不足的问题，为策略学习提供更丰富的场景和行为经验。
2. **构建更贴近现实的训练环境。** 从真实交互数据中学习世界模型，将其作为强化学习的仿真环境，探索缩小仿真与现实差距的方法。
3. **改善数据覆盖之外的表现。** 通过在线强化学习优化预训练策略，让机器人根据环境反馈调整行为，探索已有数据之外的有效解决方案。
4. **降低新任务适配成本。** 研究上下文学习，让机器人利用任务示例与交互经验适应新任务，减少部署时进行参数微调的需求。
5. **满足实时控制需求。** 研究一步生成模型及其策略优化方法，减少动作生成延迟，在提高响应速度的同时改进任务表现。
6. **增强前瞻决策能力。** 研究隐空间世界模型与基于世界模型的测试时规划，通过预测未来状态和行动后果优化当前决策。
7. **支持失败恢复与长程任务。** 探索 Agent RL，让机器人根据执行反馈识别失败、调整计划并尝试恢复，协调多个步骤完成任务。
8. **推动多机器人具身协作。** 构建大规模多智能体具身数据集与仿真环境，研究面向物理交互和真实协作需求的策略优化算法，让多个机器人能够共同完成生产与生活中的任务。
