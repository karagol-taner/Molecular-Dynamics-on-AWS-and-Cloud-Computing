1. Chose Ubuntu for EC2 instance platform. (Don not forget to secure private key file)

2. To upgrade the packages on your system, you can use the apt package manager:
```
sudo apt update     # This updates the package lists
sudo apt upgrade    # This upgrades the installed packages to their latest versions
```
3. Install gromacs
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

7. You can use SCP to securely transfer files between your EC2 instance and your local Windows computer.
You will need an SCP client for Windows, such as WinSCP or PuTTY's pscp.

8. If you use WinSCP client, you will need to configure WinSCP to use the private key:

- Open WinSCP.
- In the login dialog, enter the hostname (EC2 instance's public IP address or hostname), your username, and leave the password field empty.
- Click on the "Advanced..." button to open the Advanced Site Settings dialog.
- In the Advanced Site Settings dialog, go to the "SSH" section.
- Under "SSH > Authentication", click on the ellipsis (...) button next to "Private key file" and select the .ppk file you created or converted.
- Click "OK" to close the Advanced Site Settings dialog.
