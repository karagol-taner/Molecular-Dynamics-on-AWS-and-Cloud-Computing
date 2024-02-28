# Molecular Dynamics Simulation on Google Colab

This guide provides instructions for setting up and running molecular dynamics simulations on Google Colab.

Note: Google Colab sessions have a maximum runtime of 12 hours. If your simulation requires more time, you may need to break it into shorter segments or consider alternative computing resources.

## Prerequisites

Before you begin, make sure you have the following:

- A Google account
- Knowledge of molecular dynamics simulations and BASH commands
- Familiarity with using Google Colab notebooks

## Setup

1. **Open a Google Colab Notebook:**
   - Go to [Google Colab](https://colab.research.google.com/).
   - Sign in with your Google account if you're not already signed in.
   - Create a new notebook or open an existing one.
 
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

