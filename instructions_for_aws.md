# Molecular Dynamics Simulation on Amazon AWS EC2

This guide provides instructions for setting up and running molecular dynamics simulations on Amazon Elastic Compute Cloud (EC2).

This information is provided without any advice, recommendations, or guarantees.

Please cite [our paper on bioRxiv](https://www.biorxiv.org/content/10.1101/2024.11.14.623563v1.abstract) if you find these instructions useful.

## Prerequisites

Before you begin, make sure you have the following:

- An Amazon Web Services (AWS) account
- Access to Amazon EC2
- Knowledge of BASH commands and molecular dynamics simulations

## Setup
1. **Launch an EC2 Instance:**
   - Sign in to the AWS Management Console.
   - Navigate to the EC2 dashboard.
   - Choose Ubuntu for the EC2 instance platform. **(Do not forget to secure the private key file)**

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
```
sudo apt install dos2unix
```

4. You can install files with wget:
```
wget <URL>
```

5. For benchmark files, please check this website: (https://www.mpinat.mpg.de/grubmueller/bench)

6. Benchmark code:
```
gmx mdrun -s benchMEM.tpr -nsteps 5000 -deffnm benchMEM && tar cvzf benchMEM.tar benchMEM*
```

7. For making the code keep running when you close terminal (while running the instance), you can add nohup to code. For example:
```
nohup gmx mdrun -deffnm example -v > output.log &
```
8. You can reach the output file with tail (see the progress on time) or cat command.
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
```
dos2unix start.sh #if the script file is start.sh
chmod +x start.sh

./start.sh

nohup ./start.sh > script_output.log 2>&1 & #if you want to run script on background
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
- IF you are using non-GPU system like t3.micro, you can add -nt 1 to gmx code for 1 CPU thread only.
- Also, you can modify checkpoints with -cpt option. Example:
```
nohup gmx mdrun -nt 1 -deffnm step6.0_minimization -cpi md.cpt -cpt 3 -v > script_output.log &
```

13. If your local internet speed is low, you can upload files to Google Drive using VM's internet connection using a third party tool called [gdrive.](https://github.com/prasmussen/gdrive)
```
wget https://github.com/BugCode1/gdrive/releases/download/2.1.2/gdrive_2.1.2_linux_386.tar.gz
tar -xvf gdrive_2.1.2_linux_386.tar.gz
./gdrive about
./gdrive upload --parent GoogleDriveFolderID --recursive ./FolderName
```

