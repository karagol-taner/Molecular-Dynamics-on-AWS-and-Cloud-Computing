1. Choose Ubuntu for the EC2 instance platform. (Do not forget to secure the private key file)

2. To upgrade the packages on your system, you can use the apt package manager:
```
sudo apt update  
sudo apt upgrade 
```
3. Install Gromacs and other installations
```
sudo apt install gromacs
```
```
sudo apt-get install openmpi-bin libopenmpi-dev
```

4. You can install files with wget:
```
wget <URL>
```

5. For benchmark files, you check this website: (https://www.mpinat.mpg.de/grubmueller/bench)

6. Benchmark code:
```
gmx mdrun -s benchMEM.tpr -nsteps 5000 -deffnm benchMEM && tar cvzf benchMEM.tar benchMEM*
```

7. For making the code keep running when you close terminal (while running the instance), you can add nohup to code. For example:
```
nohup gmx mdrun -deffnm example -v > output.log &
```
8. You can reach output file with tail (see the progress on time) or cat command.
```
tail -f output.log
```
```
cat output.log
```
9. You can run .sh bash scripts or .csh scripts
```
sudo apt-get install dos2unix  #for running the .sh bash file
```
10. You can use SCP to securely transfer files between your EC2 instance and your local Windows computer.
You will need an SCP client for Windows, such as WinSCP or PuTTY's pscp.

11. If you use WinSCP client, you will need to configure WinSCP to use the private key:

- Open WinSCP.
- In the login dialog, enter the hostname (EC2 instance's public IP address or hostname), your username, and leave the password field empty.
- Click on the "Advanced..." button to open the Advanced Site Settings dialog.
- In the Advanced Site Settings dialog, go to the "SSH" section.
- Under "SSH > Authentication", click on the ellipsis (...) button next to "Private key file" and select the .ppk file you created or converted.
- Click "OK" to close the Advanced Site Settings dialog.

12. Some additional GROMACS instructions for EC2:
- IF you are yousing non-GPU system like t3 micro, you can add -nt 1 to gmx code, also you can modify checkpoints with -cpi md.cpt -cpt 3 option. Example:
```
nohup gmx mdrun -nt 1 -deffnm step6.0_minimization -cpi md.cpt -cpt 3 -v > script_output.log &
```
