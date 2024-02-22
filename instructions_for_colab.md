1. Open a new Google Colaboratory Notebook.
 
2. Add code for installing GROMACS:
```
!apt-get install -y gromacs
```
3. You can upload files from the side-bar, files section.

4. For benchmark files, you check this website: (https://www.mpinat.mpg.de/grubmueller/bench)

5. Add another code for the benchmark:   
```
!gmx mdrun -s benchMEM.tpr -nsteps 5000 -deffnm benchMEM && tar cvzf benchMEM.tar benchMEM*
```

6. You can download .log file from side-bar.
