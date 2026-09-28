<p align="center">
  <img src="assets/poinfra-logo.png" alt="POInfra" width="640">
</p>

<h1 align="center">Policy Optimization for Generative Policies</h1>

<p align="center">
  Learning, fine-tuning, and improving decisions with generative models.
</p>

<p align="center">
  <a href="#research">Research</a> ·
  <a href="#getting-started">Getting started</a> ·
  <a href="#development">Development</a> ·
  <a href="#citation">Citation</a>
</p>

POInfra brings together research on generative policies for robot control and multi-agent decision-making. We study how to learn these policies from data, improve them through online interaction, and refine their decisions through inference-time guidance and planning.

This repository is the shared entry point to the projects, papers, and available implementations. Each project currently maintains its own code and instructions.

## Research

Our work connects three questions:

- **Policy learning:** How can generative models learn useful action distributions from data?
- **Online optimization:** How can pretrained policies improve through interaction while retaining useful prior behavior?
- **Inference-time optimization:** How can guidance and world-model planning improve decisions at execution time?

| Project | Focus | Resources | Implementation |
| --- | --- | --- | --- |
| **OGPO** | One-step generative policy optimization for real-time robot control | [Project](https://ogpo-project.github.io/) · [Paper](https://arxiv.org/abs/2601.20701) · [Code](https://github.com/ogpo-project/OGPO) | Released |
| **MA-FPPO** | Multi-agent flow-pretrained policy optimization | [Project](https://ma-fppo.github.io/) | Not publicly released |
| **G2MAF** | Test-time gradient guidance for multi-agent flow policies | [Project](https://g2maf.github.io/) · [Paper](https://arxiv.org/abs/2609.31286) · [Repository](https://github.com/g2maf/G2MAF) | Release in preparation |
| **MA-WAM** | Multi-agent world-action modeling for test-time planning | [Project](https://ma-wam.github.io/) · [Paper](https://arxiv.org/abs/2609.31281) · [Repository](https://github.com/ma-wam/MA-WAM) | Release in preparation |

## Getting started

**To run an available implementation**, start with [OGPO](https://github.com/ogpo-project/OGPO). Its repository provides the installation, data, checkpoint, training, and evaluation instructions. Follow the dependencies and environment requirements documented there.

**To explore the research**, use the project pages above for method descriptions, results, and available resources. G2MAF and MA-WAM currently provide project information in their public repositories; their implementations are not yet available.

POInfra does not yet provide a shared installation package or a unified training command.

## Development

We plan to develop reusable components where the projects share practical requirements:

- Interfaces for generative policies and action sampling.
- Data loading and checkpoint conventions.
- Training and evaluation examples with documented configurations.

The first integration milestone is a runnable example with a documented environment and evaluation procedure. Additional projects can then adopt shared components while retaining the settings needed to reproduce their papers.

## Citation

If you use a method, implementation, dataset, or checkpoint, cite the corresponding project using the citation provided in its repository or project page. POInfra currently has no separate framework paper.

## Maintainer

[Guowei Zou](https://github.com/Guowei-Zou) · Sun Yat-sen University

Questions about an individual method or reproduction should go to the corresponding project repository. Cross-project suggestions can be raised in this repository's issues.
