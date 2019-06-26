# Command Line Script

## Getting Started: Logging in

Connect to Quest using ssh (**s**ecure **sh**ell) protocol
```bash
ssh <NetID>@quest.northwestern.edu
```

Print working directory
```bash
pwd
```

List your allocations (storage in /projects/<allocationID>)
```bash
groups
```

Summarize **d**isk **u**sage in your home folder
```bash
du -h ~
```

Logout from Quest, return to your computer
```bash
logout
```

## Getting Started: Software Modules

Connect to Quest using ssh (**s**ecure **sh**ell) protocol
```bash
ssh <NetID>@quest.northwestern.edu
```

Check the version of Python
```
python --version
#Python 2.7.5
```
It seems system has python 2.7. Can we use Python 3.6?

Check available software provided by modules
```
module avail
```

Load python/anaconda3.6 module (to use python 3.6)
```
module load python/anaconda3.6
```

Let's see if the module is loaded
```bash
module list
```

Let's check the version of python again
```
python --version
#Python 3.6.0 :: Anaconda 4.3.0 (64-bit)
```

Now python 3.6 can be used

Unload python/anaconda3.6 module
```bash
module unload python/anaconda3.6
```

Check python version
```bash
python --version
#Python 2.7.5
```

## Getting Started: Clone GitHub Repository

Logout from Quest, return to your computer
```bash
logout
```

Clone the Github repository for the training materials
```bash
git clone https://github.com/nuitrcs/intro-quest-ciera-workshop
```

**C**hange **d**irectory to cloned folder
```bash
cd intro-quest-ciera-workshop
```

**L**i**s**t the files/folders in the cloned folder
```bash
ls
```

Change directory to the parent folder
```bash
cd ../
```

## Getting Started: Transfers

### Cyberduck

Copy cloned folder from your computer to Quest using Cyberduck

Connect to Quest using ssh (**s**ecure **sh**ell) protocol
```bash
ssh <NetID>@quest.northwestern.edu
```

**L**i**s**t the files/folders in the home folder
```bash
ls
```

Change directory to copied folder
```bash
cd intro-quest-ciera-workshop
```

**L**i**s**t the files/folders in intro-quest-ciera-workshop
```bash
ls
```

### SFTP

Logout from Quest, return to your computer
```bash
logout
```

**R**e**m**ove (i.e. delete) cloned folder from your computer
```bash
rm -Rf intro-quest-ciera-workshop
```

List the files/folders to see if the folder is removed
```bash
ls
```

Connect to Quest with **s**ecure **f**ile **t**ransfer **p**rotocol (**sftp**)
```bash
sftp <NetID>@quest.northwestern.edu
```

Download intro-quest-ciera-workshop folder to your computer
```sftp
get -r intro-quest-ciera-workshop
```

List existing files on Quest
```sftp
ls
```

**L**ocally **l**i**s**t existing files (i.e. in your computer)
```sftp
lls
```

Change directory to intro-quest-ciera-workshop
```sftp
cd intro-quest-ciera-workshop
```

Remove “submit_generic.sh” file on Quest
```sftp
rm submit_generic.sh
```

List existing files in intro-quest-ciera-workshop
```sftp
ls
```

Locally change directory to cloned folder on your local computer
```sftp
lcd intro-quest-ciera-workshop
```

Upload “submit_generic.sh” to Quest
```sftp
put submit_generic.sh
```

List existing files on Quest again
```sftp
ls
```

Quit sftp, return to your computer
```sftp
quit
```

Print working directory
```bash
pwd
```

### SCP

Change directory to “intro-quest-ciera-workshop” folder on your
local computer.

```bash
cd intro-quest-ciera-workshop
```

Remove "submit_generic.sh" file from your computer
```bash
rm submit_generic.sh
```

List existing files in intro-quest-ciera-workshop
```bash
ls
```

**S**ecure **c**o**p**y submit_generic.sh from Quest to your computer.
```bash
scp <NetID>@quest.northwestern.edu:~/intro-quest-ciera-workshop/submit_generic.sh ./submit_generic.sh
```

List files in intro-quest-ciera-workshop on your computer
```bash
ls
```

## Getting Started: Batch Job Submission

Connect to Quest using ssh (**s**ecure **sh**ell) protocol
```bash
ssh <NetID>@quest.northwestern.edu
```

Change directory to "intro-quest-ciera-workshop"
```bash
cd intro-quest-ciera-workshop
```

Print out (con**cat**enate) submission script, "submit_generic.sh"
```bash
cat submit_generic.sh
```

To edit submit_generic.sh we will use VIM
```bash
vim submit_generic.sh
```

Let's take a look at whereami.sh and helloworld.py
```bash
cat whereami.sh
```

```bash
cat helloworld.py
```

After editing submit_generic.sh, we will submit your job to batch processing
```bash
sbatch submit_generic.sh
```
This command will return a jobID.

You can check the status of your jobs in the queue
```bash
squeue -u <NetID>
```

Detailed information can be obtained using the jobID
```bsah
checkjob <jobID>
```

When the job ends, investigate errlog, outlog and python_output.txt
```bash
cat errlog
```

```bash
cat outlog
```

```bash
cat python_output.txt
```

## Getting Started: Interactive Job Submission

Use FastX or terminal. If terminal is the choice:

**PC users with GitBash (requires Xming)**
```bash
export DISPLAY=localhost:0
ssh -XY <NetID>@quest.northwestern.edu
```

**MAC users with terminal (requires XQuartz)**
```bash
ssh -X <NetID>@quest.northwestern.edu
```

After connecting to Quest, submit your interactive job
```bash
srun --x11 --account=w10001 --partition=w10001 --time=00:10:00 --nodes=1 --ntasks-per-node=1 --mem-per-cpu=1G --pty bash -l
```

Once the interactive session starts on the compute node, we will start
Matlab user interface.

Check available Matlab modules
```bash
module avail matlab
```

Load matlab/r2018a module
```bash
module load matlab/r2018a
```

Start Matlab
```
matlab
```

The Matlab graphical user interface (GUI) should start at this point.

Close the GUI and end the interactive session by logging out.
```bash
logout
```

After logging out, the system will take you back to the login node.