<p align="center">
  <img src="assets/poinfra-logo.png" alt="POInfra" width="720">
</p>

<div align="center">
  <a href="#projects"><img src="https://img.shields.io/badge/Papers-arXiv-B31B1B?logo=arxiv" alt="Papers"></a>
  <a href="https://huggingface.co/collections/Guowei-Zou/poinfra-models-and-datasets"><img src="https://img.shields.io/badge/Hugging_Face-Models_%26_Data-FFD21E?logo=huggingface" alt="Models and data"></a>
  <a href="#getting-started"><img src="https://img.shields.io/badge/Getting_Started-Guide-8A2BE2?logo=readthedocs" alt="Getting started"></a>
  <a href="#projects"><img src="https://img.shields.io/badge/Code-Project_Repositories-181717?logo=github" alt="Project repositories"></a>
</div>

<div align="center">

[![English](https://img.shields.io/badge/lang-English-blue.svg)](README.md)
[![简体中文](https://img.shields.io/badge/语言-简体中文-red.svg)](README.zh-CN.md)

</div>

<h1 align="center"><sub>POInfra: Policy Optimization for Generative Models</sub></h1>

**POInfra focuses on policy optimization for generative models.** We study how diffusion and flow models can serve as policies, how these policies can improve through reinforcement learning, and how additional computation at inference time can improve their decisions.

Our research began with **D2PPO**, which combines dispersive regularization for diffusion policy pretraining with PPO fine-tuning. The research extends to efficient one-step policies, coordinated multi-agent generation, online fine-tuning, and inference-time guidance and planning. The common goal is to turn expressive generative models into effective decision-making policies.

**PO** stands for **Policy Optimization**, and **Infra** reflects our goal of building reusable infrastructure around this research. This repository brings together the methods and resources. Available implementations currently run through their individual project repositories.

## Models and datasets

[Browse the POInfra collection on Hugging Face](https://huggingface.co/collections/Guowei-Zou/poinfra-models-and-datasets), or open a project resource directly below.

| Project | Models | Datasets |
| --- | --- | --- |
| **OGPO** | [Hugging Face](https://huggingface.co/ogpo-project/OGPO-checkpoints) | [Hugging Face](https://huggingface.co/datasets/ogpo-project/OGPO-datasets) |
| **CoFlow** | [Hugging Face](https://huggingface.co/Guowei-Zou/CoFlow-checkpoints) | [Hugging Face](https://huggingface.co/datasets/Guowei-Zou/CoFlow-datasets) |
| **MA-FPPO** | [Hugging Face](https://huggingface.co/ma-fppo/MA-FPPO) | — |
| **G2MAF** | [Hugging Face](https://huggingface.co/g2maf/G2MAF) | — |
| **MA-WAM** | [Hugging Face](https://huggingface.co/ma-wam/MA-WAM) | — |

## Video overview

A two-minute introduction to POInfra, with real robot demonstrations and multi-agent environments.

https://github.com/user-attachments/assets/c93f9101-ff76-4da4-84df-8372ea182742

<div align="center">
  <img src="assets/overview.svg" alt="POInfra research architecture: data, pretraining, policy optimization, inference, and evaluation" width="100%">
</div>

## What's NEW!

- [2026/09] 🔥 **POInfra** is launched, bringing together our research on policy optimization for generative models, beginning with D2PPO.
- [2026/09] 🔥 **MA-FPPO** is now available on arXiv. The project page includes policy rollouts and a presentation of multi-agent flow pretraining and online fine-tuning. [Project](https://ma-fppo.github.io/) · [Paper](https://arxiv.org/abs/2609.32594) · [Code](https://github.com/ma-fppo/MA-FPPO) · [Models](https://huggingface.co/ma-fppo/MA-FPPO).
- [2026/07] 🔥 **G2MAF** explores test-time gradient guidance for multi-agent flow policies. [Project](https://g2maf.github.io/) · [Paper](https://arxiv.org/abs/2609.31286) · [Code](https://github.com/g2maf/G2MAF).
- [2026/07] 🔥 **MA-WAM** explores multi-agent world-action models for test-time planning. [Project](https://ma-wam.github.io/) · [Paper](https://arxiv.org/abs/2609.31281) · [Code](https://github.com/ma-wam/MA-WAM).
- [2026/05] 🔥 **CoFlow** introduces coordinated few-step flow for offline multi-agent decision-making. [Project](https://guowei-zou.github.io/coflow/) · [Paper](https://arxiv.org/abs/2605.01457) · [Code](https://github.com/Guowei-Zou/coflow-release).
- [2026/09] 🔥 The updated **OGPO** preprint (v2) is available. The work is now accepted at **ACM MM 2026**. [Project](https://ogpo-project.github.io/) · [Paper](https://arxiv.org/abs/2601.20701v2) · [Code](https://github.com/ogpo-project/OGPO).

- [2025/10] 🔥 **DM1** introduces MeanFlow with dispersive regularization for one-step robotic manipulation. [Project](https://guowei-zou.github.io/dm1/) · [Paper](https://arxiv.org/abs/2510.07865) · [Code](https://github.com/Guowei-Zou/dm1-release).
- [2025/08] 🔥 **D2PPO** introduces diffusion policy optimization with dispersive loss. The work is now accepted at **AAAI 2026**. [Project](https://guowei-zou.github.io/d2ppo/) · [Paper](https://arxiv.org/abs/2508.02644) · [Code](https://github.com/Guowei-Zou/d2ppo-release).

## Design Philosophy and Research Directions

POInfra aims to bring embodied intelligence into practical use, enabling robots to perform useful work in factories and homes and create tangible value. We focus on a central question: **How can generative models move from learning existing behavior to becoming decision-making policies that continually improve, adapt to new tasks, and act efficiently?**

For robot control and multi-agent cooperation, we organize our research around five connected stages: **data, pretraining, policy optimization, inference, and evaluation**. Together, these stages address how to learn from experience, improve through feedback, and make effective decisions with limited interaction and computation.

### Learn from experience and prepare policies for improvement

Offline demonstrations and interaction trajectories provide the behavioral experience for pretraining. **D2PPO** introduces dispersive regularization during diffusion policy pretraining, and **DM1** studies this regularization for MeanFlow policies in robotic manipulation. These projects investigate representation diversity and efficient action generation as foundations for subsequent policy learning. **CoFlow** extends learning from offline data to coordinated few-step trajectory generation for multiple agents.

### Improve generative policies through environment feedback

Policy optimization is at the core of POInfra. **D2PPO** fine-tunes diffusion policies with PPO, **OGPO** develops one-step generative policy optimization for real-time robot control, and **MA-FPPO** studies flow policy pretraining and online fine-tuning for multi-agent decision-making. Across these model families, we study how policies can use prior experience while exploring better behavior through task feedback.

### Balance responsiveness and decision quality during execution

**DM1** and **OGPO** study one-step policies to reduce the computation needed to generate actions. **G2MAF** uses Q-value gradient guidance to steer multi-agent flow policies toward actions with higher estimated value. **MA-WAM** studies multi-agent world-action models for test-time planning. These directions address action generation speed, action value, and anticipation of future outcomes.

### Evaluate progress through task outcomes and deployment costs

Evaluation covers task success rate, return, win rate, inference time, and performance on physical robots, as appropriate for each task. We consider both task performance and the data, interaction, and computation required to achieve it. These results inform the design of pretraining, policy optimization, and inference methods, connecting methodological progress to practical deployment.

## Projects

### Robot control

| Method | Research focus | Paper | Project | Code |
| --- | --- | --- | --- | --- |
| **D2PPO** | Diffusion policy pretraining with dispersive loss and PPO fine-tuning | [AAAI 2026 / arXiv](https://arxiv.org/abs/2508.02644) | [Website](https://guowei-zou.github.io/d2ppo/) | [D2PPO-release](https://github.com/Guowei-Zou/d2ppo-release) |
| **DM1** | MeanFlow with dispersive regularization for one-step robotic manipulation | [arXiv](https://arxiv.org/abs/2510.07865) | [Website](https://guowei-zou.github.io/dm1/) | [DM1-release](https://github.com/Guowei-Zou/dm1-release) |
| **OGPO** | One-step generative policy optimization for real-time robot control | [ACM MM 2026 / arXiv](https://arxiv.org/abs/2601.20701v2) | [Website](https://ogpo-project.github.io/) | [OGPO](https://github.com/ogpo-project/OGPO) |

### Multi-agent decision-making

| Method | Research focus | Paper | Project | Code |
| --- | --- | --- | --- | --- |
| **CoFlow** | Coordinated few-step flow for offline multi-agent decision-making | [arXiv](https://arxiv.org/abs/2605.01457) | [Website](https://guowei-zou.github.io/coflow/) | [CoFlow-release](https://github.com/Guowei-Zou/coflow-release) |
| **MA-FPPO** | Multi-agent flow-pretrained policy optimization | [arXiv](https://arxiv.org/abs/2609.32594) · [Models](https://huggingface.co/ma-fppo/MA-FPPO) | [Website](https://ma-fppo.github.io/) | [MA-FPPO-release](https://github.com/ma-fppo/MA-FPPO) |
| **G2MAF** | Test-time gradient guidance for multi-agent flow policies | [arXiv](https://arxiv.org/abs/2609.31286) | [Website](https://g2maf.github.io/) | [G2MAF-release](https://github.com/g2maf/G2MAF) |
| **MA-WAM** | Multi-agent world-action modeling for test-time planning | [arXiv](https://arxiv.org/abs/2609.31281) | [Website](https://ma-wam.github.io/) | [MA-WAM-release](https://github.com/ma-wam/MA-WAM) |

All linked repositories are public. G2MAF and MA-WAM currently contain a project README, with no implementation files yet. Implementation links above refer to separate project releases, rather than modules integrated into a single package.

## Research motivations

### D2PPO — Framework

<p align="center">
  <a href="https://guowei-zou.github.io/d2ppo/"><img src="assets/framework/d2ppo.png" alt="D2PPO framework" width="900"></a>
</p>

[Project](https://guowei-zou.github.io/d2ppo/)

### OGPO

<p align="center">
  <a href="https://ogpo-project.github.io/"><img src="assets/motivation/ogpo.png" alt="OGPO research motivation" width="900"></a>
</p>

[Project](https://ogpo-project.github.io/)

### CoFlow

<p align="center">
  <a href="https://guowei-zou.github.io/coflow/"><img src="assets/motivation/coflow.png" alt="CoFlow research motivation" width="900"></a>
</p>

[Project](https://guowei-zou.github.io/coflow/)

### MA-FPPO

<p align="center">
  <a href="https://ma-fppo.github.io/"><img src="assets/motivation/ma-fppo.webp" alt="MA-FPPO research motivation" width="900"></a>
</p>

[Project](https://ma-fppo.github.io/)

### G2MAF

<p align="center">
  <a href="https://g2maf.github.io/"><img src="assets/motivation/g2maf.webp" alt="G2MAF research motivation" width="900"></a>
</p>

[Project](https://g2maf.github.io/)

### MA-WAM

<p align="center">
  <a href="https://ma-wam.github.io/"><img src="assets/motivation/ma-wam.webp" alt="MA-WAM research motivation" width="900"></a>
</p>

[Project](https://ma-wam.github.io/)

## Getting started

Choose the implementation that matches the question you want to explore:

| Goal | Starting point |
| --- | --- |
| Pretrain a diffusion policy and fine-tune it with PPO | [D2PPO setup and examples](https://github.com/Guowei-Zou/d2ppo-release) |
| Study one-step generative policies for manipulation | [DM1 setup and evaluation](https://github.com/Guowei-Zou/dm1-release) |
| Study online optimization of one-step policies | [OGPO training and evaluation](https://github.com/ogpo-project/OGPO) |
| Train coordinated flow models on offline multi-agent data | [CoFlow setup and experiments](https://github.com/Guowei-Zou/coflow-release#setup) |

For example, obtain the D2PPO implementation with:

```bash
git clone https://github.com/Guowei-Zou/d2ppo-release.git
cd d2ppo-release
```

Then follow the repository's installation instructions, environment setup, and task configurations. Each project documents its own dependencies, datasets, checkpoints, and evaluation procedure.

## Contributing

We welcome discussions about generative policy optimization, reproducibility, and components that could be shared across projects. Open an [issue](https://github.com/POInfra-AI/POInfra/issues) for cross-project ideas. For a method-specific question or bug, use the corresponding implementation repository.

## Citation

Please cite the papers corresponding to the methods and resources you use. BibTeX entries are available in each project's repository or website. 

## Maintainer

[Guowei Zou](https://guowei-zou.github.io/Guowei-Zou/) · Sun Yat-sen University

## Further Directions for Real-World Deployment

Following the path from learning to deployment, we are extending this research in eight directions:

1. **Expand training data.** Explore world models as a source of generated data to address data scarcity in embodied intelligence and provide richer scenarios and behavioral experience for policy learning.
2. **Build training environments closer to reality.** Learn world models from real interactions and use them as simulation environments for reinforcement learning, exploring ways to reduce the gap between simulation and reality.
3. **Improve performance beyond dataset coverage.** Optimize pretrained policies through online reinforcement learning so robots can adjust their behavior using environment feedback and explore effective solutions beyond existing data.
4. **Reduce the cost of adapting to new tasks.** Study in-context learning so robots can use task examples and interaction experience to adapt, reducing the need for parameter fine-tuning during deployment.
5. **Meet real-time control requirements.** Study one-step generative models and their policy optimization to reduce action generation latency while improving task performance.
6. **Enable decisions that anticipate future outcomes.** Study latent world models and world-model-based test-time planning to improve current decisions by predicting future states and action outcomes.
7. **Support failure recovery and long-horizon tasks.** Explore Agent RL so robots can identify failures from execution feedback, revise plans, attempt recovery, and coordinate multiple steps to complete tasks.
8. **Advance cooperation among embodied robots.** Develop large-scale datasets and simulation environments for multi-agent embodied intelligence, and study policy optimization for physical interaction and cooperation so multiple robots can work together in industrial and everyday settings.
