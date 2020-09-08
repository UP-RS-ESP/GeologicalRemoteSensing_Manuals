---
title: "Python Environment and Software Setup for Remote Sensing Master's Courses"
subtitle: ""
subject: "Installation and Setup Guide"
date: "24 August 2020"
author: "[Ben Purinton](purinton@uni-potsdam.de), [Bodo Bookhagen](bodo.bookhagen@uni-potsdam.de) and others"
keywords: [installation python software ssh]
titlepage: true
toc-own-page: true
disable-header-and-footer: false
listings-disable-line-numbers: true
header-left:  "Install Document"
header-right: "Aug-24 2020"
footer-left: ""
lang: "en"
---

# Objectives

This document describes in detail the installation of a Python environment for courses in the Remote Sensing Master's. We will install the Python environment using the package manager [Miniconda](https://docs.conda.io/en/latest/miniconda.html) and use the command line to add the Python packages that serve as our toolbox. Installation on both Windows and MacOS / Linux are similar. We suggest using Ubuntu or some other Linux-based distribution (Mac is Linux-based) as these are the most flexible operating systems, but Windows OS will work as well. We also discuss the Jupyter Notebook environment that we use for lectures and homework, how to access and work remotely using the PC Pool at Potsdam using `ssh` logins, and finally some additional software to install (e.g., QGIS).


# Python Installation

## Why We Choose Python

The main reasons that we choose Python in our classes are: (1) it's open source requiring no license or fees and (2) it's popular in the geoscience and remote sensing communities. Beyond this, Python is versatile, easy to read and learn, and has excellent support online. Most questions or issues can be solved with web searches and on sites like [StackOverflow](https://stackoverflow.com/questions/tagged/python).


## Basic Terminology

We will define more terms as we go through our courses, but these are the basics to get you started and following along:

[Python](https://www.python.org/doc/essays/blurb/) is a _**programming language**_, which allows a user to pass human-readable instructions ("add 2+2") through an interpreter that converts them to machine-readable code ("0010110000"). Other popular, open-source languages for data analysis include R, Java, and C++. Many _**packages**_ exist for Python, which serve as toolboxes containing functions for specific tasks like linear algebra, machine learning, and plotting figures. These packages are developed by one or more users and can be installed to a given Python _**virtual environment**_. Most operating systems include some native install of Python, but it is wise to keep separate Python environments for different tasks (e.g., data analysis). These virtual environments (and the various Python packages within them) are kept isolated from one another thus preventing any package or system conflicts.

**Note:** If you want a deeper understanding of Python you're encouraged to have a look through the official [Python Tutorial](https://docs.python.org/3/tutorial/index.html).


## Environment Manager: Anaconda vs. Miniconda

[Anaconda](https://www.anaconda.com/products/individual) is a popular Python environment manager for data science. Downloading Anaconda provides many scientific packages automatically and allows users to install new environments and additional packages easily using either a desktop application or a built in Anaconda shell. In our courses we prefer to use the light-weight version of Anaconda, called [Miniconda](https://docs.conda.io/en/latest/miniconda.html). Miniconda is a much smaller version of Anaconda that only contains the command-line tool `conda`, Python, and a small number of useful packages like `pip`. We'll discuss virtual environment and package installs using `conda` and `pip` below.


## The Command Line

Before we move on, we need to familiarize ourselves with the computer's _**command line**_ (sometimes called a _**shell**_ or _**terminal**_). The command line of any OS allows you to pass instructions to the computer in the form of lines of text. You can think of command-line instructions as an alternative to clicking in a graphical user interface (_**GUI**_). Among many things, you can: open programs; move through your file structures; create, rename, and delete folders and files; and, of course, manage your Python environments!

On Windows you can open a command-line prompt by running the program "cmd.exe" (Open the start menu > search for "cmd" or "command prompt" > click the icon). You should see something like this:

![Windows command line.](img/windows-cmd-line.png)

On Mac or Linux you can open the "terminal" program (Open the system search > search "terminal" > click the icon). You should see something like this:

![MacOS / Linux command line.](img/linux-cmd-line.png)


### Basic Command-Line Navigation

Rather than clicking around in Finder or Explorer, you can move around your computer's entire file-system structure (so navigating in and out of folders along _**file paths**_), create new folders, move files, and list folder contents with a few commands worth memorizing. You can also find cheat sheets with these and other commands online for both [Windows](http://www.cs.columbia.edu/~sedwards/classes/2015/1102-fall/Command%20Prompt%20Cheatsheet.pdf) and [MacOS / Linux](https://cheatography.com/davechild/cheat-sheets/linux-command-line/). _**Note:** Windows uses back slashes whereas Mac and Linux use forward slashes for file paths._ _**Also Note:** A `>` means Windows prompt and `$` refers to Mac / Linux._

To navigate to different folders:
```
$ cd path/to/folder
```
or
```
> cd path\to\folder
```
You can navigate "up" to a parent folder using:
```
cd ..
```
Once in a directory you can list the contents using:
```
$ ls
```
```
> dir
```
Create a folder:
```
mkdir <foldername>
```
Copy a file or folder to a new location:
```
$ cp <file or foldername> new/location/
```
```
> copy <file or foldername> new\location\
```
Move or rename a file or folder:
```
$ mv <folder or filename> <new name or path to new location>
```
```
> move <folder or filename> <new name or path to new location>
```
Delete a file or folder:
```
$ rm <file or folder name>
```
```
> del <file or folder name>
```

_**Last Note:** Your command prompt should support something called "tab completion" meaning that you can just type the first few letters of the filename or path you are interested in and then press the tab button on your keyboard to complete the name. Very useful rather than typing out huge file / path names!_


## Install Miniconda

Now that we are familiar with some basic terms, the idea of Python environments, and our command line, it's time to install things. The first step is installing Miniconda from here: [https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html). Download the installer corresponding to your operating system, the latest Python version, and your system architecture (most likely that is 64-bit for any computer purchased in the last ~10 years). As of August 19th, 2020 the file would be:

  - Windows: "Python 3.8 Miniconda3 Windows 64-bit"
  - Mac: "Python 3.8 Miniconda3 MacOSX 64-bit bash"
  - Linux: "Python 3.8 Miniconda3 Linux 64-bit"


### Windows

Open the downloaded file (e.g., "Miniconda3-latest-Windows-x86_64.exe") and follow the prompts. For the destination folder you can use the default (which should be something like `C:\Users\USERNAME\miniconda3`) or change it to another location. As shown in the below figure, be sure to add Miniconda to the system PATH (which tells the command line where the commands like `conda` are), you can ignore the warning it gives:

![Add Miniconda to the system path during Windows install.](img/windows-add-conda-to-path.png)


### Mac / Linux

For Mac and Linux you should have downloaded a `.sh` bash file. This is a command-line script that you can run in the terminal. Open your terminal and navigate to the Downloads folder (or wherever you put the Miniconda `.sh` file) using: `cd path/to/Downloads/`. When you enter the command `ls` in this folder you should see the Miniconda file listed. From here simply run:

```
$ bash <filename>.sh
```

Then follow the command line prompts asking for the install location (e.g., `/home/miniconda3/`) and saying "yes" to adding Miniconda to the system path when prompted.


## `conda`: Create Python Environment for Course

To make sure `conda` is installed go to your command prompt and enter `conda list`. This should show a list of installed packages. If you get an error like "conda not found" then you may not have added `conda` to the system path. If you don't get an error then we can create our virtual Python environment for the course _Data Analysis and Statistics_. You can find a good cheat sheet for `conda` commands [here](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf).

First we create the new environment using:
```
conda create -n DataAnalysis python=3.*
```
Say "y" when prompted to proceed. This creates a new environment within the Miniconda3 directory called `DataAnalysis`. We are also telling the environment to use the latest Python 3 version using the `*` [wildcard character](https://en.wikipedia.org/wiki/Wildcard_character).

To install packages into this new environment we first need to activate it using:
```
> conda activate DataAnalysis
```
or, on Mac / Linux:
```
$ source activate DataAnalysis
```
To deactivate the environment, simply run:
```
> conda deactivate
```
or, on Mac / Linux:
```
$ source deactivate
```
When the environment is active you will see `(DataAnalysis)` to the left of your command prompt as in this example from Windows:

![Activating and deactivating your new conda environment.](img/windows-conda-activate-deactivate.png)


## Install Packages in the Environment

For this course (_Data Analysis and Statistics_) we will rely on some fundamental packages including:

  - [numpy](https://numpy.org/) for math
  - [matplotlib](https://matplotlib.org/) for plotting
  - [pandas](https://pandas.pydata.org/) for tabular data manipulation
  - [scipy](https://www.scipy.org/) for advanced math
  - [rasterio](https://rasterio.readthedocs.io/en/latest/) for geospatial array manipulation
  - [jupyter notebook](https://jupyter.org/) for interactive scripting, we'll run the lecture materials and homeworks through the Jupyter Notebook interface (using [Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/))

From the command line, activate the environment so that you see `(DataAnalysis)` next to the command prompt. Now enter the following commands (same for any OS):

```
conda config --prepend channels conda-forge
conda install --y numpy matplotlib pandas scipy rasterio jupyterlab
```

In the end you should see something like this (without any failure messages):

![Successful installation of packages using conda.](img/windows-conda-install.png)

You can update any package (when new versions are released) using:
```
conda update <package name>
```

You can also install packages directly into your base conda environment, such that you do not need to create a new environment and activate / deactivate it. To do this you just run:
```
conda install <package name>
```
without the `conda create env` command. However, this isn't recommended as package conflicts can occasionally occur. You can always delete and remake virtual environments, so duplicate packages on your system are okay (the packages / environments tend to be relatively small in size). Conceptually, this is similar to the schematic in the following figure:

![Visualization of core Python and virtual environment installed with Miniconda. On the left: Core Python 3.6 containing the packages NumPy and pandas. On the right: A Python 3.8 virtual environment called "DataAnalysis" installed in the Miniconda directory containing the packages matplotlib and pandas. These Python environments exist completely isolated from one another, hence the double install of pandas. Modified from source: https://python-for-scientists.readthedocs.io/en/latest/_pages/environments.html](img/environments_folders-2.png)


### Side Note: pip and conda

We installed packages using the `conda` command-line tool. The Miniconda install also included another Python package installer called `pip`. You may occasionally come across Python packages that need to be installed using `pip install <package name>` rather than `conda install <package name>`, and you can use `pip` from within the `conda` environment. `conda` and `pip` play nicely together, although if you installed a package with one or the other you should also do any package updates with the same one. You can read more about this [here](https://www.anaconda.com/blog/understanding-conda-and-pip).

**Note:** Before installing any package to an environment you should search the internet for the installation instructions (e.g., using Google to search: "install pandas using conda" or "install openCV using pip").


## Testing the Install

Now let's just check that the Python environment for _Data Analysis and Statistics_ is ready to go before we move on. Please run the following at your command line:
```
python -c "import matplotlib, numpy, pandas, scipy, rasterio"
```
This shouldn't produce any output (or errors).


## Jupyter Notebook

Jupyter Notebooks offer a way to write rich text (in the [Markdown](https://en.wikipedia.org/wiki/Markdown) format) and code together in one document, execute blocks of code in an underlying _**kernel**_, and output results and figures below each code block. The kernel that Jupyter uses for Python is IPython!

Jupyter works through a web browser communicating locally with your computer ports, so you don't need an internet connection to run it. In this course we'll rely on [Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/) which consists of many modular elements including a file browser, text editor, terminal window, interactive IPython console, and notebook viewer. **Note: Jupyter Notebook code + markdown files always end with the extension `.ipynb`.**

You should have already installed Jupyter Lab via `conda install jupyterlab`. To start a new session go to your `DataAnalysis` activated command line (navigated to the folder for this class) and enter:

```
jupyter notebook --generate-config
jupyter notebook password
```

These steps generate a configuration file for Jupyter and allow you to create a password to access the Jupyter Lab session. Now you can enter:

```
jupyter lab --no-browser
```

Now open a new internet browser (**either Firefox, Google Chrome, or Safari; NOT e.g., Windows Internet Explorer**) and enter the url "http://localhost:8888/".

**Note:** Jupyter defaults to port 8888, you can specify a port of your choosing by adding `--port=XXXX` to the previous command (e.g., `jupyter lab --no-browser --port=1111`), then change 8888 in the url to whatever XXXX port you entered.

You will have to enter the password you set and choose a kernel (Python3). Then you will see a screen like this:

![Jupyter Lab showing the launcher and file browser (whatever folder you ran the `jupyter lab --no-browser` command from).](img/open-jupyter-lab.png)

You can open a new console to get an interactive IPython prompt (**Note:** to enter commands in the prompt you need to enter them in the bottom and then press `Shift + Enter` on your keyboard). You can also open a new `.ipynb` notebook by going to File > New > Notebook. Drag and drop the tabs around the screen into whatever configuration you like.

![Jupyter Lab with a new notebook (left) and IPython console (right) both opened.](img/jupyter-lab-configuration.png)


# Working Remotely: PC Pool in Golm (Building 27)

If you do not or cannot install the required software or Python environment on your personal computer, we have the option of working remotely through the PC Pool at Campus Golm. Heavy computation may also require the more powerful PC Pool on campus, so it's good to familiarize yourself with these steps and generate your own ssh private/public key pair for login to the PC Pool.


## Login Via `ssh`

[SSH](https://en.wikipedia.org/wiki/Secure_Shell) stands for secure shell and is a safe and encrypted way to access computers remotely. We will work with the `ssh` command-line environment. The below steps will walk you through ssh private/public key generation, allowing secure and easy login without passwords. Once logged into the remote PC Pool computer you will be in a Linux (Ubuntu 18.04.5) command-line environment.


### `ssh` Key Generation and Login: Windows

Windows does not come with `ssh` in the default command-line environment. The use of [PuTTY](https://www.putty.org/) is recommended. PuTTY is an ssh client, that has the capability to generate private/public ssh keys and login to remote servers. *As an alternative to the below steps, consider installing the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) available in Windows 10. This will give you a Linux terminal identical to Ubuntu (or whatever Linux flavor you prefer). In that case you could use the instructions in the next section for ssh login on Linux / Mac.*

1. Install [PuTTY](https://www.putty.org/) on your computer.

2. Open the program "PuTTYgen" (Open the start menu > search for "PuTTYgen" > click the icon), a key generator that is installed along with PuTTY.

3. Using PuTTYgen (see below figure): Generate a 2048 bit private/public key pair, save the public and private key to a secure location on your personal computer, and copy-paste the public key to send via email to the system administrator Harald Schernthanner ([hschernt@uni-potsdam.de](mailto:hschernt@uni-potsdam.de)). **Important: Keep your private key somewhere safe, consider adding a key passphrase in PuTTYgen, and _never_ handout your private key!**

![Generate 2048 bit private/public key pair using PuTTYgen](img/putty-keygen_steps.png)

4. Harald Schernthanner ([hschernt@uni-potsdam.de](mailto:hschernt@uni-potsdam.de)) generates an account for you after receiving your public key via email, puts your key on the system, contacts you when your account is ready, and tells you your username and the IP of your assigned machine.

5. When the account is ready, please login using PuTTY (Open the start menu > search for "PuTTY" > click the icon). You need to enter the *IP address of your assigned machine*:

![Enter IP address of you assigned machine in PuTTY on Windows](img/putty-hostname.png)

6. To complete the login in PuTTY you have to tell the program the path to the private key (Connection > SSH > Auth), then you can press "Open" to login (and "Yes" to the security alert):

![Point PuTTY to the private key you saved in the previous step (Connection > SSH > Auth > "Private key file for authentication"). After the IP address and private key path are entered you can click "Open".](img/putty-private-key-load.png)

![Say "Yes" to the security alert which should only occur on your very first login.](img/putty-connect-security-alert.png)

7. With login complete you will enter your username and end up on a command-line terminal for your assigned computer. Below we see user `ben` logged into `pcpool10`. You are now remotely logged into the PC Pool!

![Logged on to the PC Pool as user `ben` on computer `pcpool10`](img/putty-logged-on.png)


### `ssh` Key Generation and Login: Linux / Mac

On Linux or Mac, you should be able to use `ssh` right away from the terminal without installing any additional software.

1. Open a terminal and execute:
```
ssh-keygen
```

2. You will be asked to "Enter file in which to save the key (/home/ben/.ssh/id_rsa):". Here, define a folder and filename (e.g., `/home/yourusername/yourkeyname`). When you are asked to "Enter a passphrase:" leave it blank by pressing enter (we don't necessarily need a passphrase for the public key).

3. This generates two files: First the private key named `yourkeyname` (**keep it in a safe place and do not hand it out**) and second the public key named `yourkeyname.pub`. Send the public key to the administrator Harald Schernthanner ([hschernt@uni-potsdam.de](mailto:hschernt@uni-potsdam.de)).

4. Harald Schernthanner ([hschernt@uni-potsdam.de](mailto:hschernt@uni-potsdam.de)) generates an account for you after receiving your public key via email, puts your key on the system, contacts you when your account is ready, and tells you your username and the IP of your assigned machine.

5. Login with `ssh` from your terminal. You need to enter the *IP address of your assigned machine*. For username `ben` logging onto the assigned computer with IP address `141.89.113.170` (After the `-i` flag you have to define **the path to your private key**):
```
ssh -i /home/ben/yourkeyname ben@141.89.113.170
```


## Data Storage on PC Pool Computers

Do not store your data in your home directory (`/home/student`). Instead use `/DATA` for fast, local storage and `/NAS` for network storage. You should create your own sub-directory. For the user `ben`, I would write:
```
mkdir /DATA/ben
```

_**Note: We periodically wipe the `/home` directory, so you would lose all your data, hence use the `/DATA` directory.**_


## File Transfer Between Local and Remote Computers

At times you will need to move files between your local computer and the remote machines in the PC Pool. For instance, after you finish processing a large dataset on the remote computer you may want to transfer the output to your local system to look at the results and create figures. Or, for an `.ipynb` Jupyter notebook that you ran on the server, you may want to transfer it to your local computer after running. This is a common task and there are many options for file transfer between local and remote systems via SSH File Transfer Protocol ([SFTP](https://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol)).

*Keep in mind: Likely, your download speed will be very fast (i.e., it will be fast to pull files from the PC Pool), but your upload speed will be slow (i.e., you have to be patient if you put data on the PC Pool).*


### GUI: FileZilla - *Your most likely choice*

You can install [FileZilla Client](https://filezilla-project.org/download.php?type=client) on any OS. This is a straight forward way to copy files back and forth (you see progress and expected up/download times). If you plan to move files back-and-forth continuously, you may want to look into `rsync` or a similar command-line option.

When you open FileZilla for the first time you will need to click the top left icon ("Open the Site Manager" with the little server icons underneath "File"). In the Site Manager window create a new site, call it "pc-pool", and fill out the "General" tab exactly as below (changing the fields to your host IP, username, and SSH private key file location):

![Open a FileZilla session and create a new site to the remote pc-pool host with your username and SSH private key.](img/filezilla-connect.png)

After you click "Connect" you can see all of the files on the local and remote systems in two side-by-side panels, navigate around the system folders, and copy data back and forth:

![FileZilla connected to remote host showing the file browser for both the local and remote computers.](img/filezilla-connect-browse.png)

**Note:** The new site "pc-pool" will stay in your site manager list and you can easily reconnect in your next FileZilla session as long as you don't move your SSH private key to a new location.


### Command Line: `rsync`

If you like to work on the command line (because it is more efficient), [rsync](https://en.wikipedia.org/wiki/Rsync) is the best option. It should come standard on Linux / Mac. For Windows: it is included in the [Cygwin](https://www.cygwin.com/) Linux-like terminal; can be added to the [Git](https://gitforwindows.org/) shell via [these instructions](http://tlundberg.com/blog/2020-06-15/installing-rsync-on-windows/); and/or is included in the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) available in Windows 10.

The basic syntax is:
```
rsync <options> <local filename> <remote filename>
```
For example, if I (user: `ben` on computer `141.89.113.160`) want to copy the file `my_jupyter_notebook.ipynb` from my local computer to the PC Pool location `/DATA/ben`, use:
```
rsync -avzh --progress my_jupyter_notebook.ipynb ben@141.89.113.160:/DATA/ben/
```
Or to transfer a remote file on the PC pool to my current directory (**Note:** the period (`.`) below refers to _**current directory**_, so wherever you are currently `cd`'d to):
```
rsync -avzh --progress ben@141.89.113.160:/DATA/ben/my_jupyter_notebook.ipynb .
```
The `rsync` options used here include: `-a` (archive), `-v` (verbose), `-z` (compress), `-h` (human readable), and `--progress` (progress bar). You can read about the `rsync` options online via the [manual](https://linux.die.net/man/1/rsync) or in [cheat sheets](https://devhints.io/rsync).


## Using Jupyter Remotely Via SSH

You can run Jupyter on the remote PCs to harness more computing power and to use datasets that you may not want (or be able) to download locally. To start a Jupyter Lab session on your remote PC, you need to login via SSH:
```
ssh -i /home/my_username/yourkeyname my_username@my_pc_ip_address
```
Once logged in, you should start a `screen` session, which keeps your Jupyter notebook alive even if you lose your internet connection:
```
screen
```
You can familiarize yourself with a few important `screen` commands [here](https://www.geeksforgeeks.org/screen-command-in-linux-with-examples/). The most important commands are as follows:

To give the screen session a useful name for finding it later:
```
screen -S screen_name
```
To detach from a screen session without killing the screen (and thus killing the processing), use the keyboard shortcut: `Ctrl-a + d`

And to re-join a detached screen:
```
screen -r screen_name
```

Next, to start your Jupyter Lab running in the current screen session, we need to decide on which port to send the data out of.

_**Note: Use the Four-Digit Port number (e.g., 8888) that was assigned to you along with your PC IP address and username. If you accidentally use the same port as someone else on the same PC, you would be trying to edit each other's notebooks!**_

Before we run the Jupyter notebook, we need to do:
```
conda/source activate <Class Environment Name>
jupyter notebook --generate-config
jupyter notebook password
```
This will first activate the Python environment for the class (e.g., `DataAnalysis` in place of `<Class Environment Name>`), then generate a configuration file for Jupyter, and then allow you to create a password to access the notebook.

Following this, you need to `cd` into the remote directory where your data is stored, e.g., `cd /DATA/my_username/BigData_Labs/`. Make sure that you have your own directory set up on the `/DATA` drive! Otherwise you will overwrite each other's Jupyter notebooks!

Now start the Jupyter Lab session on the server:
```
jupyter lab --no-browser --port=XXXX
```

Replace "XXXX" with your assigned port number. Now you are all set on the server side and you can open a new command line / terminal on your local computer.

The next step is to tell your local computer how to access the remotely running Jupyter Lab you started on the server. We do this via port forwarding. Once again, this is a simple one-line command **run in a new command-line prompt on your local computer**:
```
ssh -N -f -L localhost:YYYY:localhost:XXXX my_username@my_pc_ip_address
```

Here, "XXXX" is the same port you used in the remote PC command above, and "YYYY" is the port you want your laptop to listen on (you can use the default 8888 in place of "YYYY", or whatever port you prefer). This command won't show any output – you can check it is working by opening up your web browser, and navigating to the url "http://localhost:YYYY/".

You should now be able to access the Lab exercises directly from your browser, while using the computing power of the PC Pool. File transfers between the local and remote machines for datasets, notebooks, and outputs from running scripts can be accomplished FileZilla or `rsync`, as described above.


# Additional Software: Command-Line Tools and GUIs

Besides Python / Jupyter, there is some additional software to install for courses in the master's program:

- **A Text Editor**
  - For coding and taking small notes, a text editor is required.
  - Install your favorite editor - for example [Atom](https://atom.io/) is a great choice, or [Notepad++ on Windows](https://notepad-plus-plus.org/download/), or [Spyder](https://www.spyder-ide.org/). Spyder includes a full Python development environment. It can be installed using `conda install -c anaconda spyder`.

- [QGIS](https://www.qgis.org/en/site/)
  - A Geographic Information System (GIS) similar to ArcGIS, but open source and free!
  - Please follow the [download instructions](https://www.qgis.org/en/site/forusers/download.html) for your operating system. Feel free to install either the latest release or long term version (v3.14 and 3.10, respectively, as of 31-Aug 2020): e.g., "QGIS Standalone Installer Version 3.10 (64 bit)".
  - When complete, please install the additional [Semi-Automatic Classification Plugin](https://plugins.qgis.org/plugins/SemiAutomaticClassificationPlugin/) by opening QGIS and then going to "Plugins" > "Manage and install Plugins" > and searching "Semi-Automatic Classification Plugin".

- [Sentinel Application Platform (SNAP)](http://step.esa.int/main/download/snap-download/)
  - An ESA-designed program to work with Sentinel and other radar and optical data.
  - Many commands are included in QGIS, but some steps for processing radar data require the SNAP toolbox. When downloading, use the appropriate OS version and select just the "Sentinel Toolboxes" (installer containing Sentinel-1, -2, and -3 toolboxes). In class, we will make use of both the Sentinel-1 and Sentinel-2 toolboxes, as well as the Sen2Cor plugin (available as a standalone module or within SNAP).

- [GDAL/OGR Command-Line Utilities](https://gdal.org/).
  - This is a very useful addition to QGIS (in fact, QGIS is built on top of GDAL/OGR) as it allows you to work with vector (OGR commands) and raster (GDAL commands) data on the command line directly. This software is well programmed, uses multiple cores (if available), and is generally much faster than ArcGIS.
  - For all OS: GDAL utilities can be installed via `conda`. Install the `gdal` libraries using `conda install -c conda-forge gdal`.
  - For Windows you can install the "OsGeo4W Shell" to access the GDAL utilities by following the instructions [here](https://trac.osgeo.org/osgeo4w/).

- [CloudCompare](https://www.danielgm.net/cc)
  - Used for point cloud analysis and visualization. Includes many useful point-cloud analysis tools, but is slower for the visualization of large point clouds.
  - Runs on every OS. Just pick the appropriate version and download it from [here](http://www.danielgm.net/cc/release/).

- [displaz](http://c42f.github.io/displaz/)
  - Very fast and versatile point cloud viewer. Can be run from python, but we mostly use the command line.
  - _Windows Users:_ Download the installer and run.
  - _Ubuntu Users:_ This likely will need to be compiled on your machine - follow the instructions on the [github page](https://github.com/c42f/displaz).
  - _Mac Users:_ Due to recent updates for the X11 Server, this doesn't properly compile. You may end up using CloudCompare instead (which is just a bit slower for visualization).

- [LAStools](https://rapidlasso.com/lastools/)
  - Commercial software for point cloud manipulation. Very powerful and fast.
  - Licenses are available on the PC Pool (which can be accessed remotely via the ssh instructions). You can install an unlicensed version on your computer and run some of the commands locally, but file sizes are very restricted using the unlicensed version.
