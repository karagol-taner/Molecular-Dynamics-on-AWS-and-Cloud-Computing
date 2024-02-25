1. Choose Ubuntu for the EC2 instance platform. (Do not forget to secure the private key file)

2. To upgrade the packages on your system, you can use the apt package manager:
```
sudo apt update     # This updates the package lists
sudo apt upgrade    # This upgrades the installed packages to their latest versions
```
3. Install Gromacs
```
sudo apt install gromacs
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

7. For making the code keep runing when you close terminal (keep running the instance), you can add nohup to code. For example:
```
nohup gmx mdrun -nt 1 -deffnm example -cpi md.cpt -cpt 3 -v > output.log &
```
8. You can reach output file with tail (see the progress on time) or cat command.
```
tail -f output.log
```
```
cat output.log
```

9. You can use SCP to securely transfer files between your EC2 instance and your local Windows computer.
You will need an SCP client for Windows, such as WinSCP or PuTTY's pscp.

10. If you use WinSCP client, you will need to configure WinSCP to use the private key:

- Open WinSCP.
- In the login dialog, enter the hostname (EC2 instance's public IP address or hostname), your username, and leave the password field empty.
- Click on the "Advanced..." button to open the Advanced Site Settings dialog.
- In the Advanced Site Settings dialog, go to the "SSH" section.
- Under "SSH > Authentication", click on the ellipsis (...) button next to "Private key file" and select the .ppk file you created or converted.
- Click "OK" to close the Advanced Site Settings dialog.

11. Some additional GROMACS instructions for EC2:
- IF you are yousing non-GPU system like t3 micro, you can add -nt 1 to gmx code, also you can modify checkpoints with -cpi md.cpt -cpt 3 option.

