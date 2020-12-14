# Container Repository Overview
This repository hosts all container recipe files (refactored from application-specific repositories) built by the Innovation Lab (IL) development team.  Primarly, two types of containers exist:  1) General-purpose, and 2) Application-specific.  General-puropse containers contain reusable functionality for multiple applications.  Application-specific containers host unique software and configuration artifacts for a specific use.  The application-specific containers incorporate and extend the core general-purpose containers.

# Container Technology
IL recipes are written for deployment to Singularity frameworks (as required by CISTO/NCCS). Each recipe is used when building the corresponding container image using syntax of the general form:  $ singularity build 'target container name' 'container recipe'

Example (ADAPT):
$ time /usr/bin/sudo -E SINGULARITY_NOHTTPS=1 /usr/local/bin/singularity build ilab-core-2.0.0.simg ilab-core-2.0.0.def 

Containers are built hiearchically.  For example, the based Python scientific system container is the parent of the IL core container.  This approach allows for managing specific software dependencies and versions per container while giving the target image flexibility for extended appliccation-specific features.


# Container Inventory (alphabetical order)

| Name  | Description  | Parent | OS |
| :------------ |:---------------|:-----|:-----|
| cisto-centos-gdal-*     | general purpose GDAL source build         |   docker: centos | Centos |
| cisto-conda-*     | general purpose Conda environment         |   singularity: ubuntu:18.04 | Ubuntu |
| cisto-conda-gdal-*     | general purpose Conda with GDAL binaries         |   singularity: cisto-conda-1.0.0.simg | Ubuntu |
| cisto-data-science-*      | general purpose Python data science ecosystem [NumPy, SciPy, Pandas, etc.]| docker: openjdk:8-jdk-stretch | Debian |
| cisto-jupyter-lab-*      | general purpose Jupyter Lab host         |   singularity: ilab-apps-1.0.0.simg | Debian |
| ilab-apps-*      | IL application snapshot [MMX, etc.]| singularity: ilab-core-* | Debian |
| ilab-aviris-*      | IL AVIRIS application | singularity: ilab-core-* |  Debian |
| ilab-cb-*      | IL Chesapeake Bay Water Quality  application | singularity: ilab-core-* | Debian |
| ilab-cb-*-sandbox     | IL Chesapeake Bay Water Quality  application | singularity: ilab-core-* | Debian |
| ilab-core-*      | IL common dependencies [Celery, GDAL, etc] | singularity: cisto-data-science-* | Debian |
| ilab-floodmap-*      | IL Flood Map application | singularity: ilab-core-* | Debian |
| ilab-gee-*      | IL Google Earth Engine application | singularity: ilab-core-* | Debian |
| ilab-hyper-*      | IL Hyper spectral Engine application | singularity: ilab-core-* | Debian |
| ilab-landslide-*      | IL Landslide Hazard Analysis for Situational Awareness (LHASA), SALaD, OTB application | singularity: ilab-salad-* | Debian |
| ilab-mmx-*      | IL MerraMax (MMX) application | singularity: ilab-core-* | Debian |
| ilab-otb-gpu-*      | IL Orfeo Toolbox (without Tensor Flow) with GPU support application | docker: nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04 | Ubuntu |
| ilab-r-*     | general purpose R environment         |   docker: ubuntu:18.04 | Ubuntu |
| ilab-salad-*      | IL emi-Automatic Landslide Detection System (SALaD) application | singularity: ilab-otb-gpu-2.0.0.simg | Ubuntu |





