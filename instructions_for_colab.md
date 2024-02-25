1. Open a new Google Colaboratory Notebook.
 
2. Add code for installing GROMACS:
```
!apt-get install -y gromacs
```
3. You can upload files from the side-bar, files section. You can mount your google drive with this command:
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

