<p align="center">
  <img src="assets/poinfra-logo.png" alt="POInfra" width="720">
</p>

<h1 align="center">POInfra: Policy Optimization for Generative Models</h1>

<p align="center">
  Diffusion and flow policies for robot control and multi-agent decision-making.
</p>

<p align="center">
  <a href="#overview">Overview</a> ·
  <a href="#news">News</a> ·
  <a href="#research-directions">Research directions</a> ·
  <a href="#projects">Projects</a> ·
  <a href="#getting-started">Getting started</a> ·
  <a href="#citation">Citation</a>
</p>

## Overview

**POInfra focuses on policy optimization for generative models.** We study how diffusion and flow models can serve as policies, how these policies can improve through reinforcement learning, and how additional computation at inference time can improve their decisions.

Our research began with **D2PPO**, which combines dispersive regularization for diffusion policy pretraining with PPO fine-tuning. The research extends to efficient one-step policies, coordinated multi-agent generation, online fine-tuning, and inference-time guidance and planning. The common goal is to turn expressive generative models into effective decision-making policies.

**PO** stands for **Policy Optimization**, and **Infra** reflects our goal of building reusable infrastructure around this research. This repository brings together the methods and resources. Available implementations currently run through their individual project repositories.

## News

- **September 2026:** POInfra launches as the shared entry point for our work on generative policy optimization. [G2MAF](https://arxiv.org/abs/2609.31286) and [MA-WAM](https://arxiv.org/abs/2609.31281) preprints are available.
- **2026:** [OGPO](https://ogpo-project.github.io/) is accepted at **ACM Multimedia 2026**. The earlier preprint was released under the name DMPO.
- **May 2026:** [CoFlow](https://arxiv.org/abs/2605.01457) studies coordinated few-step flow generation for offline multi-agent decision-making.
- **October 2025:** [DM1](https://arxiv.org/abs/2510.07865) studies MeanFlow with dispersive regularization for one-step robotic manipulation.
- **August 2025:** The [D2PPO preprint](https://arxiv.org/abs/2508.02644) introduces diffusion policy optimization with dispersive loss. D2PPO is accepted at **AAAI 2026**.

## Research directions

### Diffusion policy optimization

**D2PPO** studies representation learning in diffusion policies. Dispersive regularization is applied during pretraining, followed by PPO fine-tuning through environment interaction. This establishes the starting point of our work on learning and optimizing generative policies.

### Efficient generative policies

**DM1** investigates dispersive regularization for MeanFlow policies in robotic manipulation. **OGPO** develops one-step generative policy optimization for real-time robot control. These projects study how to retain useful generative representations while reducing the computation needed to produce actions.

### Multi-agent policy learning and optimization

**CoFlow** studies coordinated few-step trajectory generation from offline multi-agent data. **MA-FPPO** studies flow policy pretraining and online fine-tuning for multi-agent decision-making. Together, these projects extend the research to policies whose decisions must account for other agents.

### Inference-time guidance and planning

**G2MAF** studies gradient guidance for multi-agent flow policies at test time. **MA-WAM** studies multi-agent world-action models for test-time planning. These projects investigate how to improve decisions during execution through guidance or model-based planning.

## Projects

### Robot control

| Method | Research focus | Paper | Project | Code |
| --- | --- | --- | --- | --- |
| **D2PPO** | Diffusion policy pretraining with dispersive loss and PPO fine-tuning | [AAAI 2026 / arXiv](https://arxiv.org/abs/2508.02644) | [Website](https://guowei-zou.github.io/d2ppo/) | [Implementation](https://github.com/Guowei-Zou/d2ppo-release) |
| **DM1** | MeanFlow with dispersive regularization for one-step robotic manipulation | [arXiv](https://arxiv.org/abs/2510.07865) | [Website](https://guowei-zou.github.io/dm1/) | [Implementation](https://github.com/Guowei-Zou/dm1-release) |
| **OGPO** | One-step generative policy optimization for real-time robot control | [ACM MM 2026 / arXiv](https://arxiv.org/abs/2601.20701) | [Website](https://ogpo-project.github.io/) | [Implementation](https://github.com/ogpo-project/OGPO) |

### Multi-agent decision-making

| Method | Research focus | Paper | Project | Code |
| --- | --- | --- | --- | --- |
| **CoFlow** | Coordinated few-step flow for offline multi-agent decision-making | [arXiv](https://arxiv.org/abs/2605.01457) | [Website](https://guowei-zou.github.io/coflow/) | [Implementation](https://github.com/Guowei-Zou/coflow-release) |
| **MA-FPPO** | Multi-agent flow-pretrained policy optimization | See project page | [Website](https://ma-fppo.github.io/) | Not publicly released |
| **G2MAF** | Test-time gradient guidance for multi-agent flow policies | [arXiv](https://arxiv.org/abs/2609.31286) | [Website](https://g2maf.github.io/) | [Release pending](https://github.com/g2maf/G2MAF) |
| **MA-WAM** | Multi-agent world-action modeling for test-time planning | [arXiv](https://arxiv.org/abs/2609.31281) | [Website](https://ma-wam.github.io/) | [Release pending](https://github.com/ma-wam/MA-WAM) |

The G2MAF and MA-WAM repositories currently contain project information. Implementation links above refer to separate project releases, rather than modules integrated into a single package.

## Methods at a glance

### D2PPO: from diffusion policy pretraining to PPO fine-tuning

<p align="center">
  <img src="https://raw.githubusercontent.com/Guowei-Zou/d2ppo-release/master/assets/d2ppo_architecture.jpg" alt="D2PPO architecture: dispersive policy pretraining and PPO fine-tuning" width="900">
</p>

[Method, robot demonstrations, and results](https://guowei-zou.github.io/d2ppo/)

### OGPO: one-step generative policy optimization

<p align="center">
  <img src="https://raw.githubusercontent.com/ogpo-project/OGPO/master/sample_figs/OGPO-framework.png" alt="OGPO framework" width="900">
</p>

[Method, robot demonstrations, and results](https://ogpo-project.github.io/)

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

Please cite the papers corresponding to the methods and resources you use. BibTeX entries are available in each project's repository or website. The linked arXiv record for OGPO also contains the earlier DMPO preprint history.

## Maintainer

[Guowei Zou](https://github.com/Guowei-Zou) · Sun Yat-sen University
