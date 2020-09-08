---
title: "Additional Remote Sensing, GIS, and Spatial-Analysis Software"
subtitle: ""
subject: "Additional Software"
date: "7 September 2020"
author: "[UP Geological Remote Sensing](https://up-rs-esp.github.io/) - [Dr. Harald Schernthanner](mailto:hschernt@uni-potsdam.de)"
keywords: [installation software]
titlepage: false
toc-own-page: false
disable-header-and-footer: false
listings-disable-line-numbers: true
header-left:  "Additional Software"
header-right: "Sep-7 2020"
footer-left: ""
lang: "en"
---

# Contact

If you have questions about this document you can find our team webpage with contact info at [https://up-rs-esp.uni-potsdam.de/](https://up-rs-esp.github.io/). Most questions can be addressed to Dr. Harald Schernthanner ([hschernt@uni-potsdam.de](mailto:hschernt@uni-potsdam.de)).

# Additional Software: Command-Line Tools and GUIs

Besides Python / Jupyter, there is some additional software to install for courses in the master's program:

- **A Text Editor**
  - For coding and taking small notes, a text editor is required. Your computer comes with one (e.g., "Notepad" on Windows), but you should install something with more coding functionality.
  - Install your favorite editor - for example [Atom](https://atom.io/) is a great choice and the one we recommend on any platform.
  - You can also use [Notepad++ on Windows](https://notepad-plus-plus.org/download/)

- _Optional:_ [Spyder](https://www.spyder-ide.org/)
  - Spyder includes a full Python development environment. It can be installed using `conda install -c anaconda spyder`.
  - If you are coming from MATLAB or R, this may be a good option for getting started coding in Python.

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
