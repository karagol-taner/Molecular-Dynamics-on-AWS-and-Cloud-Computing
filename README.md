# Molecular Dynamics on Cloud Computing

Molecular Dynamics on Google Compute Engine, AWS (Amazon Web Services), and other Cloud Computing services

This repository is accompanied by [a published paper on bioRxiv](https://www.biorxiv.org/content/10.1101/2024.11.14.623563v1.abstract) that benchmarks molecular dynamics simulations on various cloud platforms, with a specific focus on optimizing Google Colab for scientific computing.

DOI/Cite:

[Karagöl, T., & Karagöl, A. (2024). Benchmarking GROMACS on Optimized Colab Processors and the Flexibility of Cloud Computing for Molecular Dynamics. bioRxiv, 2024-11.](https://www.biorxiv.org/content/10.1101/2024.11.14.623563v1.abstract) 

or 

[![DOI](https://zenodo.org/badge/761850636.svg)](https://zenodo.org/doi/10.5281/zenodo.10751372)

## Overview
Molecular dynamics (MD) simulations are a powerful computational tool used in various fields of science, including chemistry, biology, and materials science. GROMACS is a widely used open-source molecular dynamics simulation software designed for biochemical molecules.

Molecular Dynamics simulations traditionally relied on costly on-premises infrastructure like supercomputers or clusters for High-Performance Computing (HPC). However, in recent years, there's been a significant shift towards utilizing computing resources provided by commercial cloud providers. This shift is driven by the flexibility and accessibility these platforms offer, irrespective of an organization's financial capacity. 

Popular platforms such as Google Compute Engine and AWS now provide scalable computing infrastructure. Researchers can harness these cloud resources to conduct Molecular Dynamics simulations efficiently, without the constraints of traditional on-premises setups. This transition empowers researchers with greater flexibility and cost-effectiveness in their computational work. Monitoring and managing usage is crucial for optimizing costs, and cloud providers often offer tools and calculators to help users estimate expenses based on their specific requirements.This repository demonstrates how to use compute engine resources like AWS cloud computing and Google Compute Engine to accelerate molecular dynamics simulations, enabling researchers to tackle larger and more complex systems while optimizing costs and scalability. 

Another alternative to these platforms is Google Colab, which offers GPU and TPU resources in an easily accessible, cloud-based environment. Colab’s simplicity make it a game-changer for students, educators, and researchers, democratizing access to computational resources. Run GROMACS simulations on Google Colab with significant performance improvements achieved through recompilation and optimization.
Overcome Colab-specific challenges, such as session timeouts and GPU/TPU availability, by integrating with Google Drive to save and resume simulations.
Set up and utilize CUDA and MPI environments in Colab to enhance performance.
Benchmark GPU-enabled simulations on Colab versus TPU-based workflows, highlighting trade-offs in speed and efficiency.

## Instructions
**For Google Compute Engine (Google Cloud): [Instructions for Google Compute Engine](instructions_for_gce.md)**

**For AWS: [Instructions for AWS ](instructions_for_aws.md)**

**For Google Colab: [Instructions for Colab](instructions_for_colab.md)**

This information is provided without any advice, recommendations, or guarantees.

Our recently published paper explores:

**Optimized GROMACS Performance on Colab**: By re-compiling GROMACS on Colab, we achieved significant speed-ups compared to the default pre-compiled version.

**Session Management Solutions**: Methods to address session timeouts and hardware limitations by saving progress to Google Drive and resuming interrupted simulations.

**GPU vs. TPU Benchmarks**: Comparative analysis of CUDA-enabled GPUs versus Google TPUv2 units, with insights into their relative advantages for MD simulations.

## References
1. Amazon Web Services. "Amazon EC2" Accessed February 22, 2024. https://aws.amazon.com/ec2/.
2. Kutzner, C., Kniep, C., Cherian, A., Nordstrom, L., Grubmüller, H., de Groot, B. L., & Gapsys, V. (2022). GROMACS in the Cloud: A Global Supercomputer to Speed Up Alchemical Drug Design. Journal of chemical information and modeling, 62(7), 1691–1711. https://doi.org/10.1021/acs.jcim.2c00044
3. For Benchmarks: Dept. of Theoretical and Computational Biophysics, Max Planck Institute for Multidisciplinary Sciences, Göttingen, https://www.mpinat.mpg.de/grubmueller/bench
4. Google. "Google Colaboratory" Accessed February 22, 2024. https://colab.research.google.com/.
5. [GROMACS Documentation](http://manual.gromacs.org/)
6. [Google Compute Engine Documentation](https://cloud.google.com/compute)
