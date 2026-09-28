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
- [2026/09] 🔥 **MA-FPPO** 项目页上线，提供论文、策略执行视频，以及多智能体流预训练与在线微调的演示。 [Project](https://ma-fppo.github.io/) · [Paper](https://ma-fppo.github.io/assets/MA-FPPO.pdf) · [Code](https://github.com/ma-fppo/MA-FPPO).
- [2026/07] 🔥 **G2MAF** 探索多智能体流策略的测试时梯度引导。 [Project](https://g2maf.github.io/) · [Paper](https://arxiv.org/abs/2609.31286) · [Code](https://github.com/g2maf/G2MAF).
- [2026/07] 🔥 **MA-WAM** 探索用于测试时规划的多智能体世界动作模型。 [Project](https://ma-wam.github.io/) · [Paper](https://arxiv.org/abs/2609.31281) · [Code](https://github.com/ma-wam/MA-WAM).
- [2026/05] 🔥 **CoFlow** 提出面向离线多智能体决策的协同少步流方法。 [Project](https://guowei-zou.github.io/coflow/) · [Paper](https://arxiv.org/abs/2605.01457) · [Code](https://github.com/Guowei-Zou/coflow-release).
- [2026/01] 🔥 **OGPO** 的初版预印本以 DMPO 名称发布，该工作现已录用至 **ACM MM 2026**。 [Project](https://ogpo-project.github.io/) · [Paper](https://arxiv.org/abs/2601.20701) · [Code](https://github.com/ogpo-project/OGPO).

- [2025/10] 🔥 **DM1** introduces 分散正则化下的 MeanFlow 一步机器人操作. [Project](https://guowei-zou.github.io/dm1/) · [Paper](https://arxiv.org/abs/2510.07865) · [Code](https://github.com/Guowei-Zou/dm1-release).
- [2025/08] 🔥 **D2PPO** 提出带分散损失的扩散策略优化方法，该工作现已录用至 **AAAI 2026**。 [Project](https://guowei-zou.github.io/d2ppo/) · [Paper](https://arxiv.org/abs/2508.02644) · [Code](https://github.com/Guowei-Zou/d2ppo-release).

## 主要研究方向

### 扩散策略优化

**D2PPO** 研究扩散策略中的表征学习，在预训练阶段引入分散正则化，再通过环境交互进行 PPO 微调。这是我们生成式策略学习与优化研究的起点。

### 高效生成式策略

**DM1** 研究机器人操作中 MeanFlow 策略的分散正则化。**OGPO** 面向实时机器人控制，研究一步生成式策略优化。这些工作探索如何在减少动作生成计算量的同时保留有效的生成表征。

### 多智能体策略学习与优化

**CoFlow** 基于离线多智能体数据研究协同的少步轨迹生成。**MA-FPPO** 研究多智能体决策中的流策略预训练与在线微调，将研究扩展到需要考虑其他智能体行为的策略。

### 推理时引导与规划

**G2MAF** 研究多智能体流策略的测试时梯度引导。**MA-WAM** 研究用于测试时规划的多智能体世界动作模型，通过引导或基于模型的规划改进执行时的决策。

## 项目

### 机器人控制

| 方法 | 研究内容 | 论文 | 项目页 | 代码 |
| --- | --- | --- | --- | --- |
| **D2PPO** | 分散损失下的扩散策略预训练与 PPO 微调 | [AAAI 2026 / arXiv](https://arxiv.org/abs/2508.02644) | [项目页](https://guowei-zou.github.io/d2ppo/) | [实现](https://github.com/Guowei-Zou/d2ppo-release) |
| **DM1** | 分散正则化下的 MeanFlow 一步机器人操作 | [arXiv](https://arxiv.org/abs/2510.07865) | [项目页](https://guowei-zou.github.io/dm1/) | [实现](https://github.com/Guowei-Zou/dm1-release) |
| **OGPO** | 面向实时机器人控制的一步生成式策略优化 | [ACM MM 2026 / arXiv](https://arxiv.org/abs/2601.20701) | [项目页](https://ogpo-project.github.io/) | [实现](https://github.com/ogpo-project/OGPO) |

### 多智能体决策

| 方法 | 研究内容 | 论文 | 项目页 | 代码 |
| --- | --- | --- | --- | --- |
| **CoFlow** | 面向离线多智能体决策的协同少步流生成 | [arXiv](https://arxiv.org/abs/2605.01457) | [项目页](https://guowei-zou.github.io/coflow/) | [实现](https://github.com/Guowei-Zou/coflow-release) |
| **MA-FPPO** | 多智能体流预训练策略优化 | [PDF](https://ma-fppo.github.io/assets/MA-FPPO.pdf) | [项目页](https://ma-fppo.github.io/) | [实现](https://github.com/ma-fppo/MA-FPPO) |
| **G2MAF** | 多智能体流策略的测试时梯度引导 | [arXiv](https://arxiv.org/abs/2609.31286) | [项目页](https://g2maf.github.io/) | [待发布](https://github.com/g2maf/G2MAF) |
| **MA-WAM** | 用于测试时规划的多智能体世界动作建模 | [arXiv](https://arxiv.org/abs/2609.31281) | [项目页](https://ma-wam.github.io/) | [待发布](https://github.com/ma-wam/MA-WAM) |

G2MAF 和 MA-WAM 的公开仓库目前包含项目介绍，具体实现尚待发布。上表中的实现链接指向各项目的独立发布版本，目前尚未整合为统一软件包。

## 方法概览

### D2PPO：从扩散策略预训练到 PPO 微调

<p align="center">
  <img src="https://raw.githubusercontent.com/Guowei-Zou/d2ppo-release/master/assets/d2ppo_architecture.jpg" alt="D2PPO architecture: dispersive policy pretraining and PPO fine-tuning" width="900">
</p>

[方法、机器人演示与实验结果](https://guowei-zou.github.io/d2ppo/)

### OGPO：一步生成式策略优化

<p align="center">
  <img src="https://raw.githubusercontent.com/ogpo-project/OGPO/master/sample_figs/OGPO-framework.png" alt="OGPO framework" width="900">
</p>

[方法、机器人演示与实验结果](https://ogpo-project.github.io/)

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
