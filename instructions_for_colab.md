# Molecular Dynamics Simulation on Google Colab

This guide provides detailed instructions for setting up and running molecular dynamics (MD) simulations on Google Colab, with optimized workflows for significant performance gains. Using the tools and techniques outlined here, researchers can overcome Colab’s session limitations and maximize the platform's potential for MD simulations.

Note: Google Colab sessions have a runtime limit (typically 12 hours), and high-performance GPUs may not always be available. For longer simulations, this guide includes methods for saving and resuming interrupted simulations using Google Drive integration. If your simulation requires continuous computation beyond Colab's limitations, you may consider alternative cloud resources such as Google Compute Engine or AWS.

## Prerequisites

Before you begin, make sure you have the following:

- A Google account to access Google Colab and Drive.
- Knowledge of molecular dynamics simulations and BASH commands
- Familiarity with using Google Colab notebooks

Our recently published [paper on bioRxiv](https://www.biorxiv.org/content/10.1101/2024.11.14.623563v1.abstract) explores:

- Optimized GROMACS Performance on Colab: By re-compiling GROMACS on Colab, we achieved significant speed-ups compared to the default pre-compiled version.
- Session Management Solutions: Methods to address session timeouts and hardware limitations by saving progress to Google Drive and resuming interrupted simulations.
- GPU vs. TPU Benchmarks: Comparative analysis of CUDA-enabled GPUs versus Google TPUv2 units, with insights into their relative advantages for MD simulations.

You can cite our paper if you find this instructions usuful.

## Setup

1. **Open a Google Colab Notebook:**
   - Go to [Google Colab](https://colab.research.google.com/).
   - Sign in with your Google account if you're not already signed in.
   - Create a new notebook or open an existing one.
   - You can integrate custom Google Compute Engine virtual machines (VMs) for faster computing.
 
2. Add code for installing GROMACS:
```
!apt-get install -y gromacs
```
3. You can upload files from the side-bar, files section. You can mount your google drive with this command: (NOTE: Google Drive mounting does not work if you use custom Google Compute Engine VM)
```
from google.colab import drive
drive.mount('/content/drive')
```
4. For benchmark files, you check this website: (https://www.mpinat.mpg.de/grubmueller/bench)

5. Add another code for the benchmark:   
```
!gmx mdrun -s benchMEM.tpr -nsteps 5000 -deffnm benchMEM && tar cvzf benchMEM.tar benchMEM*
```

6. You can download .log file from side-bar.

7. If you want to run .sh script file, you can use the following code:
```
!apt-get update && apt-get install dos2unix
!chmod +x start.sh
!dos2unix start.sh
!./start.sh
```

