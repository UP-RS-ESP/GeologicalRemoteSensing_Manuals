---
title: "Required and suggested software for the course RSM02"
subtitle: "Lidar, SfM, and Pointclouds"
subject: "Lidar, SfM, and Pointclouds"
date: "Apr-13 2020"
author: "[Bodo Bookhagen](bodo.bookhagen@uni-potsdam.de)"
keywords: [Pointcloud software installation]
titlepage: false
toc-own-page: false
disable-header-and-footer: false
listings-disable-line-numbers: true
header-left:  "Required and suggested software for the course RSM02"
header-right: "April-13 2020"
footer-left: ""
lang: "en"
...
# Required and suggested software for the course RSM02

## Objectives
This document briefly describes what Software to setup for performing analysis steps and working with point cloud data and for lidar classification. *Please install this software on your laptop - it will allow you to use it locally and if required, you can access the PC Pool (logins will be provided). All software is open source.*

You can use Windows and most of the software will also be easily installed on a Mac. _We suggest to use Ubuntu or some other Linux-based distribution as these are the most flexible systems, but Windows OS will work as well._

# Software

## Command Line Tools and GUI
Packages only used for pointcloud data:

- [CloudCompare](https://www.danielgm.net/cc)
  - Point Cloud analysis and visualization. Includes many useful point-cloud analysis tools, but is slower for the visualization of large pointclouds. *Runs on every OS.*
- [displaz](http://c42f.github.io/displaz/)
  - Very fast and versatile viewer. Can be run from python, but we mostly use the command line.
  - _Windows Users:_ Download the binary and run.
  - _Ubuntu Users:_ This likely will need to be compiled on your machine - follow the instructions on the github page
  - _Mac Users:_ Due to the recent updates for the X11 Server, this doesn't properly compile. You may end up using CloudCompare instead (which is slower for visualization, but still allows you to do all steps).
- [LAStools/LASlib](https://liblas.org/)
  - Open Source Software for working with LAS files.
- [LAStools](https://rapidlasso.com/lastools/)
  - Commercial Software. Very powerful and fast. Licenses are available on the PC Pools (logins are provided). You can install an unlicensed version on your computer and run some of the commands locally.

We expect you to install the packages [CloudCompare](https://www.danielgm.net/cc), [displaz](http://c42f.github.io/displaz/), and [LAStools](https://rapidlasso.com/lastools/) on your own. Installing instructions are provided on the download webpages. [LAStools/LASlib](https://liblas.org/) will be installed via anaconda/miniconda (see next).

## Python Packages
We will rely on the following *python* packages and environments as well as several tools for pointcloud analysis, some python programming, and general data analysis:

- [Python 3.x](https://www.python.org/)
- [PDAL](https://pdal.io/)
- [LAStools/LASlib](https://liblas.org/)
- [GDAL](https://gdal.org/)
- [scipy](https://www.scipy.org/)
- [numpy](https://numpy.org/)
- [pandas](https://pandas.pydata.org/)
- [pylidar](http://www.pylidar.org/en/latest/)
- [laspy](https://pypi.org/project/laspy/)
- and several other tools


### _Windows Users_: Install command line tools and Python packages
One option is to install this via [Anaconda](https://www.anaconda.com/) and select the packages *gdal, pdal, Pylidar, pdal, lastools, numpy, pandas and matplotlib*.

You can also install the required packages via the `anaconda shell`. Depending on your installation, you may need to add the channel *conda-forge* to the search environment:
```bash
conda config --prepend channels conda-forge
```

I suggest to create a separate conda environment dedicated to the analysis of pointcloud data (e.g. `Py3_PC`):
```bash
conda config --prepend channels conda-forge
conda create -y -n Py3_PC python=3.* pip scipy pandas ^
  numpy matplotlib scikit-image gdal ipython spyder ^
  statsmodels jupyter pyproj lastools pdal ^
  pykdtree h5py
conda activate Py3_PC
pip install laspy
```

#### Alternative option Windows Users
Install [Linux Subsystem on Windows](https://docs.microsoft.com/en-us/windows/wsl/install-win10) and use miniconda (see next section). Installing the Linux subsystem (use Ubuntu 18.04) is generally a useful thing to do for Windows users (if your hardware space allows it), but is not required for this course.

### _Ubuntu and Mac Users_: Install command line tools and Python packages
You can install Anaconda for Mac, but you may prefer the command line approach described below.
Install [miniconda3](https://docs.conda.io/en/latest/miniconda.html) and the packages via `conda install`. Download and install the required software via the command line/shell:
```bash
cd ~
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
sh ./Miniconda3-latest-Linux-x86_64.sh
```

You may have to include additional channels for installation:
```bash
conda config --prepend channels conda-forge
```

Install the conda packages (will take some time):
```bash
conda config --prepend channels conda-forge
conda create -y -n Py3_PC python=3.* pip scipy pandas numpy matplotlib scikit-image gdal ipython spyder statsmodels jupyter pyproj lastools pdal pykdtree h5py
conda activate Py3_PC
pip install laspy
```

# Additional considerations
## Editor
We will be doing some coding and it may be useful to use an editor to take notes as well. Install your favorite editor - for example [Atom](https://atom.io/) or [Notepad++ on Windows](https://notepad-plus-plus.org/download/) or [Spyder](https://www.spyder-ide.org/). Spyder is included in the Windows Anaconda distribution and is installed via the command line above.


# Remote login to the PC Pools in Building 27 in Golm
The remote login to the PC Pool computers will work through a [ssh](https://en.wikipedia.org/wiki/Secure_Shell) connection. This command-line based approach allows you to run the commercial software package [LAStools](https://rapidlasso.com/lastools/) and will allow you to run calculations for a longer duration of time. You copy data from your local computer to the remote computer via [sftp](https://en.wikipedia.org/wiki/Secure_file_transfer_program) or [rsync](https://en.wikipedia.org/wiki/Rsync) on Mac/Ubuntu, [robocopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy) on Windows-PowerShell, both are for the command line, or [FileZilla](https://filezilla-project.org/) (use the [Filezilla Client](https://filezilla-project.org/download.php?type=client)) (GUI). If you are not familiar with the command line, I suggest to use FileZilla, which supports the sftp protocol and drag'n'drop procedures.

*Keep in mind: Likely, your download speed will be very fast (i.e., it will be fast to pull files from the PC Pool), but your upload speed will be slow (i.e., you have to be patient if you put data on the PC Pool)*

**You will be sent a separate Email with login information to the PC Pool computers. There will be some sharing necessary because there are more participants than computers, but this will barely effect computing efficiency.**

## Login via [ssh](https://en.wikipedia.org/wiki/Secure_Shell)
SSH stands for secure shell and is a safe and encrypted way to access computers remotely. X-Windows (graphical interface) commands can be also forwarded, but this is very slow and not suggested. *We will work with the SSH command line environment*. SSH is implemented on all OS.

### Windows Users
You need to start the [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7) (From the Start Menu Click Start, type PowerShell (search for it), and then click Windows PowerShell). You can simply login in to the PC pool computer with (I am using the IP of `pcpool1`):

```bash
ssh student@141.89.113.160
```

Replace YOURUSERNAME with your login name sent to you (`student` or `student1`) via email and use the IP address 141.89.XXX.YYY given in the email as well. Your login will only work on that system assigned to you.

### Ubuntu/Linux and Mac Users
Open the terminal and use ssh. You can simply login in to the PC pool computer with (I am using the IP of pcpool1):
```bash
ssh student@141.89.113.160
```

Replace YOURUSERNAME with your login name sent to you (student or student1) via email and use the IP address 141.89.XXX.YYY given in the email as well. Your login will only work on that system assigned to you.

## SSH Note
If you are interested in a graphical login (i.e., you can open windows from the command line), use for example:

```
ssh -X student@141.89.113.160
```

But be prepared - this is very slow and not advised. It may take several minutes until a graphical window opens.

*You can use the ssh login and work on the remote computer - similar to your terminal / shell on your local computer.*

# Data storage on PC Pool computers
Do not store your data in your home directory (`/home/student`). Instead use `/DATA` for fast, local storage and `/NAS` for network storage. I suggest that you create your own directory. For the user bodo, I would write (you should use your own name ;):

```
mkdir /DATA/bodo
```
*We will periodically wipe/erase the home directory and you would loose all your data.*

# File transfer between local and remote computers
## FileZilla (Graphical User Interface) - *Your most likely choice*
If you don't want to use the command line, you can install [Filezilla Client](https://filezilla-project.org/download.php?type=client) and create a directory entry for your remote PC pool. This is a straight forward way to copy files back and forth (you see progress and expected up/download times). This will work well for a few files. If you plan to move back-and-forth files continuosly, you may want to look into rsync or a similar


## Command Line option 1: [rsync](https://en.wikipedia.org/wiki/Rsync) (only for Ubuntu/Mac Users)
If you like to work on the command line (because it is more efficient), [rsync](https://en.wikipedia.org/wiki/Rsync) is the best option.

## Command Line option 2: [scp](https://en.wikipedia.org/wiki/Secure_copy) (only for Ubuntu/Mac Users)
With [scp](https://en.wikipedia.org/wiki/Secure_copy) you can copy files from the command line. The syntax is simple: `scp <localfilename> <remotefilename>`. For example, if I (user: `student` on computer `141.89.113.160`) want to copy the file `my_python_script.py` from my local computer to the pc pool, use:

```bash
scp my_python_script.py student@141.89.113.160:/DATA/bodo
```

## Command Line option 3: [sftp](https://en.wikipedia.org/wiki/Secure_file_transfer_program)
The local computer is your own laptop/desktop computer, the remote machine is the computer in the PC Pool. With [sftp]() you can copy a file on the command line (_Windows Users:_ Use the powershell, _Ubuntu and Mac users:_ use the terminal/command line). The syntax is simple: `sftp <remotecomputername>`. For example, if I (user: `student` on computer `141.89.113.160`) want to copy the file `my_python_script.py` from my local computer to the pc pool, use:

```bash
sftp student@141.89.113.160
cd /DATA/bodo
put my_python_script.py
```
