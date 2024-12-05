# Molecular Dynamics Simulation on Google Colab

This guide provides detailed instructions for setting up and running molecular dynamics (MD) simulations on Google Colab Pro+, with optimized workflows for significant performance gains. 

Note: Google Colab Pro+ sessions have an unset runtime limit (typically 12-24 hours), and high-performance GPUs may not always be available. For longer simulations, this guide includes methods for saving and resuming interrupted simulations using Google Drive integration. If your simulation requires continuous computation beyond Colab's limitations, you may consider alternative cloud resources such as Google Compute Engine or AWS.

## Prerequisites

Before you begin, make sure you have the following:

- A Google account to access Google Colab and Drive.
- Knowledge of molecular dynamics simulations and BASH commands
- Familiarity with using Google Colab notebooks

Our recently published [paper on bioRxiv](https://www.biorxiv.org/content/10.1101/2024.11.14.623563v1.abstract) explores:

- Optimized GROMACS Performance on Colab: By re-compiling GROMACS on Colab, we achieved significant speed-ups compared to the default pre-compiled version.
- Session Management Solutions: Methods to address session timeouts and hardware limitations by saving progress to Google Drive and resuming interrupted simulations.
- GPU vs. TPU Benchmarks: Comparative analysis of CUDA-enabled GPUs versus Google TPUv2 units, with insights into their relative advantages for MD simulations.

You can cite our paper if you find these instructions useful.

## Setup

1. **Open a Google Colab Notebook:**
   - Go to [Google Colab](https://colab.research.google.com/).
   - Sign in with your Google account if you're not already signed in.
   - Create a new notebook or open an existing one.
   - Select processor type or you can integrate custom Google Compute Engine virtual machines (VMs) for faster computing.

2. **For longer background runtime (considered up to 24 hours) and better hardware availability, consider subscribing to Google Colab Pro+.**

Important: Please check our paper to decide which processor type you prefer and detailed information: [Our paper on bioRxiv](https://www.biorxiv.org/content/10.1101/2024.11.14.623563v1.abstract)

3a. **Option 1**: Quick Setup - Less performance: Install GROMACS:
```
!apt-get install -y gromacs
```

3b. **Option 2**: Recompile GROMACS with CUDA Support (Recommended):
For significantly better performance, especially when using GPUs, recompile GROMACS with CUDA support. This is the suggested method for running simulations efficiently on Google Colab. Follow the detailed instructions in this repository to set up a CUDA-enabled installation.

First 
```
# Install required packages
!apt-get update
!apt-get install -y build-essential cmake git libfftw3-dev libgsl-dev

# Install CUDA (if not already installed)
!apt-get install cuda

# Check if GPU is available (optional, but useful for verification)
!nvidia-smi
```
```
# if gromacs already installed:
!gmx --version

!apt-get remove --purge gromacs

```
```
# Download the latest version of GROMACS 2024.3
!wget https://ftp.gromacs.org/gromacs/gromacs-2024.3.tar.gz

# Extract the tarball
!tar xfz gromacs-2024.3.tar.gz

```
```
# Navigate to the GROMACS source directory
%cd gromacs-2024.3

# Create a build directory
!mkdir build
%cd build

# Configure the build with CUDA (GPU) support
!cmake .. -DGMX_BUILD_OWN_FFTW=ON -DGMX_GPU=CUDA -DCMAKE_INSTALL_PREFIX=/usr/local/gromacs

# Compile the source code using all available cores
!make -j$(nproc)

# Install GROMACS
!make install

# Manually export GROMACS binary to the PATH
import os
os.environ['PATH'] += ":/usr/local/gromacs/bin"
```
```

# Check GROMACS version to confirm installation
!gmx --version

```

4a. Option 1: You can upload files from the side-bar, files section.
   
4b. Option 2 (Recommended): You can mount your google drive with this command: (NOTE: Google Drive mounting may not work if you use custom Google Compute Engine VM)
```
from google.colab import drive
drive.mount('/content/drive')
```

5. For benchmark files, you check this website: (https://www.mpinat.mpg.de/grubmueller/bench)

6. Add another code for the benchmark:   
```
!gmx mdrun -s benchMEM.tpr -nsteps 5000 -deffnm benchMEM && tar cvzf benchMEM.tar benchMEM*
```

7. You can download .log file from side-bar.

8. If you want to run .sh script file, you can use the following code:
```
!apt-get update && apt-get install dos2unix
!chmod +x start.sh
!dos2unix start.sh
!./start.sh
```

9. If you want to run .csh script file, you can use the following code:
```
!apt-get install -y csh
!chmod +x start.csh
!csh start.csh
```

