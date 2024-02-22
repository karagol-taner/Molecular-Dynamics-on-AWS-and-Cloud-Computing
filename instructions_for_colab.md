1. Open new Google Colabratory Notebook.
 
2. Add code for installing gromacs:
```
!apt-get install -y gromacs
```
3. You can upload files from side-bar, files section.

4. For benchmark files, you check this website: (https://www.mpinat.mpg.de/grubmueller/bench)

5. Add code to notebook for benchmark:   
```
!gmx mdrun -s benchMEM.tpr -nsteps 5000 -deffnm benchMEM && tar cvzf benchMEM.tar benchMEM*
```

6. You can download .log file from side-bar.
