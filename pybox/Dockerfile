# =======================================================================================#
#                                                                                        #
# This Dockerfile sets up a container based on the Ubuntu 18:04 image to run PyBox       #
#                                                                                        #
FROM ubuntu:18.04
MAINTAINER David Topping (david.topping@manchester.ac.uk)
#                                                                                        #
#    Copyright (C) 2018  David Topping : david.topping@manchester.ac.uk                  #
#                                      : davetopp80@gmail.com                            #
#    Personal website: davetoppingsci.com                                                #
#                                                                                        #
#    All Rights Reserved.                                                                #
#    This file is part of PyBox.                                                         #
#                                                                                        #
#    PyBox is free software: you can redistribute it and/or modify it under              #
#    the terms of the GNU General Public License as published by the Free Software       #
#    Foundation, either version 3 of the License, or (at your option) any later          #
#    version.                                                                            #
#                                                                                        #
#    PyBox is distributed in the hope that it will be useful, but WITHOUT                #
#    ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS       #
#    FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more              #
#    details.                                                                            #
#                                                                                        #
#    You should have received a copy of the GNU General Public License along with        #
#    PyBox.  If not, see <http://www.gnu.org/licenses/>.                                 #
#                                                                                        #
##########################################################################################
# Please note:                                                                           #
# The default Docker container provides access as root. This might cause a security      #
# issue and it is important to check this with your local sysadmin where possible        #
# The current image also builds to over 4GB. Please ensure you have adequate space to    #
# build and run                                                                          #
# Please check the project Github wiki for planned updates to security and build         #
# procedures                                                                             #
##########################################################################################

# ========================== Basic configuration =================================
ARG DEBIAN_FRONTEND=noninteractive 
RUN apt-get update && apt-mark hold linux-image-generic linux-headers-generic
RUN apt-get install -y build-essential \
    apt-utils \
    wget \
    libgl1-mesa-glx \
    gfortran \
    cmake \
    vim \
    unzip \
    pkgconf \
    libpng-dev \
    libfreetype6-dev \
    libfontconfig1 \
    libxrender1 \
    xauth \
    git \
    subversion \
    libblas-dev \
    liblapack-dev \
 && apt-get clean

# ========================== Create directory structure ==========================
RUN mkdir -p /Code
RUN mkdir -p /Code/Anaconda
RUN mkdir -p /Code/Git_repos
RUN mkdir -p /Downloads

# ========================== Install Anaconda Python =============================
WORKDIR /Code/Anaconda
RUN wget -q https://repo.continuum.io/archive/Anaconda3-5.2.0-Linux-x86_64.sh
RUN printf '\nyes\n\nyes\nno\n' | bash Anaconda3-5.2.0-Linux-x86_64.sh
RUN rm Anaconda3-5.2.0-Linux-x86_64.sh
# - add anaconda python to path
ENV PATH="/root/anaconda3/bin/:${PATH}"
# - add relevant conda channels and install modules for UManSysProp and PyBox
RUN conda config --append channels conda-forge && conda update -c conda-forge --all
RUN conda install -c openbabel openbabel==2.4.1 \
 && conda install xlsxwriter flask-wtf Werkzeug=0.16.0 \
 && conda install -c conda-forge assimulo

# =========================== Clone UManSysProp ==================================
WORKDIR /Code/Git_repos
RUN git clone https://github.com/loftytopping/UManSysProp_public.git
# ============================= Clone PyBox ======================================
RUN git clone https://github.com/huanglangwen/PyBox.git --branch 1.0.2 --depth 1

WORKDIR /Code
