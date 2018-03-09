# Sandbox OpenCV

# Table of Contents
&nbsp;&nbsp;[1. Software License Agreement](#1-software-license-agreement)
<a name="1. Software License Agreement"/>  
&nbsp;&nbsp;[2. OpenCV Project](#2-opencv-project)
<a name="2. OpenCV Project"/>  
&nbsp;&nbsp;&nbsp;&nbsp;[2.1. OpenCV Project Tree](#21-opencv-project-tree)
<a name="2.1. OpenCV Project Tree"/>  
&nbsp;&nbsp;[3. OpenCV Installation](#3-opencv-installation)
<a name="3. OpenCV Installation"/>  
&nbsp;&nbsp;&nbsp;&nbsp;[3.1. Install dependencies](#31-install-dependencies)
<a name="3.1. Install dependencies"/>  
&nbsp;&nbsp;&nbsp;&nbsp;[3.2. Get OpenCV](#32-get-opencv)
<a name="3.2. Get OpenCV"/>  
&nbsp;&nbsp;&nbsp;&nbsp;[3.3. Install OpenCV](#33-install-opencv)
<a name="3.3. Install OpenCV"/>  
&nbsp;&nbsp;&nbsp;&nbsp;[3.4. Uninstall OpenCV](#34-uninstall-opencv)
<a name="3.4. Uninstall OpenCV"/>  
&nbsp;&nbsp;[4. References](#4-references)
<a name="4. References"/>

# 1. Software License Agreement
**MIT License**

**Copyright (c) 2018 Tiago Sarmento Santos**

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

# 2. OpenCV Project
This OpenCV Sandbox project aims to held code examples for computer vision based on OpenCV.
This project is mainly focused on RaspberryPi (ARM platform) in order to explore the NEON and VFP3 features.

## 2.1. OpenCV Project Tree
[TODO]

# 3. OpenCV Installation
This is installation procedure as been done for OpenCV version 3.4.0, "virtually" could be applied to other versions.
Details on installation procedure can be found here: [install-opencv-3.4.0]( https://docs.opencv.org/3.4.0/d7/d9f/tutorial_linux_install.html "OpenCV-3.4.0 Installation Guide")

## 3.1. Install dependencies
OpenCV installlation can be configured in many different ways, enabling and disabling features, thus several dependencies exist for: compiler, required and optional packages.

### 3.1.1. Compiler dependencies
The compiler dependencies are:
```
$ sudo apt-get update
$ sudo apt-get install build-essential
```

### 3.1.2. Required dependencies
The required package dependencies are:
```
$ sudo apt-get update
$ sudo apt-get install cmake git pkg-config libgtk2.0-dev libavcodec-dev libavformat-dev libswscale-dev
```

### 3.1.3. Optional dependencies
The optional package dependencies are:
```
$ sudo apt-get update
$ sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev libv4l-dev libxvidcore-dev 
$ sudo apt-get install libx264-dev libgtk-3-dev libatlas-base-dev gfortran python2.7-dev python3-dev
```

## 3.2. Get OpenCV
In order to get OpenCV, you have two options, either you clone an OpenCV branch from github or you download a released version.
For the installation you will need both: **opencv** and **opencv-contrib**.
These methods can be done as:
```
# For GIT clone:
$ git clone https://github.com/opencv/opencv.git
$ cd opencv
$ git checkout 3.4.0

$ git clone https://github.com/opencv/opencv_contrib
$ cd opencv_contrib
$git checkout 3.4.0

# For direct download:
$ wget -c opencv-3.4.0.tar.gz https://github.com/opencv/opencv/archive/3.4.0.tar.gz
$ tar -xzvf 3.4.0.tar.gz

$ wget -c opencv_contrib-3.4.0.tar.gz https://github.com/opencv/opencv_contrib/archive/3.4.0.tar.gz
$ tar -xzvf 3.4.0.tar.gz
```
After, getting OpenCV you lust have two directories: **opencv-3.4.0/** and **opencv_contrib-3.4.0/**.

## 3.3. Install OpenCV
The last step is the build of OpenCV itself.
Here is provided the build setup with **NEON** and **VFP3** enabled, if your platform does not support this features in may need to disable them.
```
# Installation of OpenCV
$ mkdir build
$ ls .
build  opencv-3.4.0  opencv_contrib-3.4.0
$ cd build
$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
        -D CMAKE_INSTALL_PREFIX=/usr/local \
        -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib-3.4.0/modules \
        -D WITH_GTK_2_X=ON \
        -D BUILD_DOCS=ON \
        -D BUILD_EXAMPLES=ON \
        -D BUILD_PERF_TESTS=ON \
        -D BUILD_TESTS=ON \
        -D INSTALL_C_EXAMPLES=ON \
        -D INSTALL_TESTS=ON \
        -D ENABLE_NEON=OFF \
        -D ENABLE_VFPV3=OFF \
        ../opencv-3.4.0
$ make
$ sudo make install
$ ldconfig
```

## 3.4. Uninstall OpenCV
There are two possible ways to uninstall Opencv:

### 3.4.1. Uninstall through Make
If you have installed OpenCV from sources, the make command should have created a uninstall profile on build directory.
To proceed with uninstallation follow this steps:
```
$ cd build
$ sudo make uninstall
```

### 3.4.2. Uninstall through "Brute Force"
The previous point should be enough to uninstall OpenCV, however if you did not have installed OpenCV from sources or if you are not satisfied with the uninstallation done above, you can execute the following commands for "brute force" cleanup:
**(Please note that this command will request to remove all files and directories containing the string "opencv", so use it carefully to not delete unwanted files or directories.)**
```
$ sudo find / -name "*opencv*" -exec rm -irf {} \;
$ sudo ldconfig
$ sudo ldconfig -vp
```

# 4. References
* OpenCV [opencv](https://www.opencv.org/ "OpenCV Webpage")
* OpenCV Github [opencv-github](https://github.com/opencv "OpenCV Github")
* OpenCV pyimagesearch tutorials [opencv-pyimagesearch-tutorials](https://www.pyimagesearch.com/opencv-tutorials-resources-guides/ "pyimagesearch tutorials")

