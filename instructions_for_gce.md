
# Molecular Dynamics Simulation on Google Compute Engine

This guide provides instructions for setting up and running molecular dynamics simulations on Google Compute Engine (GCE). 

## Prerequisites

Before you begin, make sure you have the following:

- A Google Cloud Platform (GCP) account
- Access to Google Compute Engine
- Knowledge of BASH commands and molecular dynamics simulations

## Setup

1. **Create a GCE Instance:**
   - Navigate to the Google Cloud Console.
   - Click on the "Compute Engine" menu option.
   - Click the "Create Instance" button.
   - Choose Ubuntu for the instance platform (Boot Disk section).
   - You can apply for Quota update for more CPU cores.

2. Run the SSH. To upgrade the packages on your system, you can use the apt package manager:
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

4. You can install files with wget or SSH interface Upload button:
```
wget <URL>
```

5. For benchmark files, please check this website: (https://www.mpinat.mpg.de/grubmueller/bench), Benchmark code:
```
gmx mdrun -s benchMEM.tpr -nsteps 5000 -deffnm benchMEM && tar cvzf benchMEM.tar benchMEM*
```

6. For making the code keep running when you close terminal (while running the instance), you can add nohup to code. For example:
```
nohup gmx mdrun -deffnm example -v > output.log &
```
7. You can reach the output file with tail (see the progress on time) or cat command.
```
tail -f output.log
```
```
cat output.log
```
8. You can run .sh bash scripts or .csh scripts
```
sudo apt-get install dos2unix  #for running the .sh bash file
```
```
dos2unix start.sh #if the script file is start.sh
chmod +x start.sh

./start.sh

nohup ./start.sh > script_output.log 2>&1 & #if you want to run script on background
```
9. You can use SCP to securely transfer files between your EC2 instance and your local Windows computer.
You will need an SCP client for Windows, such as WinSCP or PuTTY's pscp.

10. If you use WinSCP client, you will need to have private key file.ppk. You can generate this file with PuTTYgen. After generating SSH key, copy the open-ssh format on the screen and paste this key to Google instance options SSH key section. If you want to access the first user filws via WinSCP, you can edit the username at the end of the key. You should make the username same as the original username.

11. Configure WinSCP to use the private key:

- Open WinSCP.
- In the login dialog, enter the hostname (Instance's public IP address), your username, and leave the password field empty.
- Click on the "Advanced..." button to open the Advanced Site Settings dialog.
- In the Advanced Site Settings dialog, go to the "SSH" section.
- Under "SSH > Authentication", click on the ellipsis (...) button next to "Private key file" and select the .ppk file you created or converted.
- Click "OK" to close the Advanced Site Settings dialog.

12. Some additional GROMACS instructions:
- You can modify checkpoints with -cpt option. Example:
```
nohup gmx mdrun -deffnm step6.0_minimization -cpi md.cpt -cpt 3 -v > script_output.log &
```

12. If your local internet speed is low, you can upload files to Google Drive using VM's internet connection using a third party tool called [gdrive.](https://github.com/prasmussen/gdrive)
```
wget https://github.com/BugCode1/gdrive/releases/download/2.1.2/gdrive_2.1.2_linux_386.tar.gz
tar -xvf gdrive_2.1.2_linux_386.tar.gz
./gdrive about
./gdrive upload --parent GoogleDriveFolderID --recursive ./FolderName
```
If gdrive doesnt work, you can use another tool called gdown to downbload large folders:
```
pip install gdown
pip install --upgrade gdown

export PATH="$HOME/.local/bin:$PATH"
source ~/.bashrc

gdown folder_url -O /tmp/folder --folder
```

