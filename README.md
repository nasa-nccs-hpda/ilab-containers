# Container Repository Overview
This repository hosts all container recipe files (refactored from application-specific repositories) built by the Innovation Lab (IL) development team.  Primarly, two types of containers exist:  1) General-purpose, and 2) Application-specific.  General-puropse containers contain reusable functionality for multiple applications.  Application-specific containers host unique software and configuration artifacts for a specific use.  The application-specific containers incorporate and extend the core general-purpose containers.

# Container Technology
IL recipes are written for deployment to Singularity frameworks (as required by CISTO/NCCS). Each recipe is used when building the corresponding container image using syntax of the general form:  

$ singularity build *target container name* *container recipe*.  For example:

```
$ /usr/bin/sudo /usr/local/bin/singularity build ilab-core-2.0.0.simg ilab-core-2.0.0.def 
```

Containers are built hiearchically.  For example, the based Python scientific system container is the parent of the IL core container.  This approach allows for managing specific software dependencies and versions per container while giving the target image flexibility for extended application-specific features.


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

# Container Access

The IL containers can be hosted on any platform with a Singularity client.  For user convenience and centralized management, the containers are available on ADAPT.  To access them, log into dsg103 (or equivalent VM) and navigate to the shared iluser container directory: 

```
gtamkin@dsg103:~$ cd /att/gpfsfs/briskfs01/ppl/iluser/containers
gtamkin@dsg103:/att/gpfsfs/briskfs01/ppl/iluser/containers$ ls -alt *.simg
-rwxr-xr-x 1 iluser  ilab   1089593344 Dec 10 21:08 cisto-centos-gdal-2.0.0.simg
-rwxr-xr-x 1 iluser  ilab   3959197696 Dec  2 08:26 conda-gdal-vanilla.simg
-rwxr-xr-x 1 root    root   1012498432 Nov 18 11:37 cisto-jupyter-lab-2.0.0.simg
-rwxr-xr-x 1 iluser  ilab   1175150592 Nov  2 16:23 ilab-core-7.0.3.simg
-rwxr-xr-x 1 iluser  ilab   1175126016 Oct 28 22:40 ilab-core-7.0.2.simg
-rwxr-xr-x 1 iluser  ilab   1175121920 Oct 28 22:05 ilab-core-7.0.1.simg
-rwxr-xr-x 1 root    root    893939712 Oct  8 10:43 test-cisto-data-science-3.0.0.simg
-rwxr-xr-x 1 iluser  ilab   1017962496 Oct  6 18:43 ilab-core-6.0.0.simg
-rwxr-xr-x 1 iluser  ilab   4103323648 Sep  9 17:43 ilab-landslide-1.0.0.simg
-rwxr-xr-x 1 iluser  ilab    250040320 Sep  7 18:39 ilab-vnc-1.0.0.simg
-rwxr-xr-x 1 iluser  ilab   2338299904 Sep  3 17:02 ilab-hyperclass-1.0.6.simg
-rwxr-xr-x 1 gtamkin k3000   335241216 Aug 20 14:50 ilab-r-3.0.0.simg
-rwxr-xr-x 1 iluser  ilab    332738560 Aug 19 18:08 ilab-r-2.0.1.simg
-rwxr-xr-x 1 iluser  ilab    237334528 Aug 13 17:35 ilab-r-3.6.3.simg
-rwxr-xr-x 1 iluser  ilab   1154277376 Jul 24 15:07 ilab-floodmap-1.0.0.simg
-rwxr-xr-x 1 iluser  ilab   1021177856 Jul  1 14:39 ilab-aviris-3.0.0.simg
-rwxr-xr-x 1 iluser  ilab   1020416000 Jul  1 13:42 ilab-core-5.0.0.simg
-rwxr-xr-x 1 iluser  ilab    864210944 Jun 16 12:25 cisto-data-science-2.0.0-06152020.simg
-rwxr-xr-x 1 iluser  ilab   3765039104 Jun 12  2020 ilab-salad-1.1.0.simg
-rwxr-xr-x 1 iluser  ilab  12020183040 Jun  8  2020 ilab-cb-6.0.0.simg
-rwxr-xr-x 1 iluser  ilab   3765035008 Jun  8  2020 ilab-salad-1.0.0.simg
-rwxr-xr-x 1 iluser  ilab  12011393024 Jun  5  2020 ilab-cb-5.0.0.simg
-rwxr-xr-x 1 iluser  ilab   1017065472 May 12  2020 ilab-aviris-2.3.0.simg
-rwxr-xr-x 1 iluser  ilab   1005064192 May  8  2020 ilab-aviris-2.2.0.simg
-rwxr-xr-x 1 iluser  ilab    867876864 May  5  2020 cisto-data-science-2.0.0.simg
-rwxr-xr-x 1 iluser  ilab    994873344 May  5  2020 ilab-aviris-2.0.0.simg
-rwxr-xr-x 1 iluser  ilab    994127872 May  5  2020 ilab-core-3.0.0.simg
-rwxr-xr-x 1 iluser  ilab   1437360128 May  5  2020 ilab-apps-1.0.0.simg
-rwxr-xr-x 1 gtamkin k3000  4065329152 May  1  2020 ilab-otb-gpu-1.0.0.simg
-rwxrwxr-x 1 gtamkin k3000   994058240 May  1  2020 ilab-core-2.0.0.simg
-rwxrwxr-x 1 gtamkin k3000   994803712 May  1  2020 ilab-aviris-1.0.0.simg
-rwxr-xr-x 1 iluser  ilab   1003683840 Apr 30  2020 ilab-core-1.0.0.simg
```

## Execute a Container

The syntax to run a container takes the general form of:  

$ singularity run *container-path* *command*.  For example:

```
gtamkin@dsg103:~$ singularity run /att/gpfsfs/briskfs01/ppl/iluser/containers/cisto-centos-gdal-2.0.0.simg ogrinfo --formats | grep GDB
WARNING: Bind mount '/home/gtamkin => /home/gtamkin' overlaps container CWD /home/gtamkin, may not be available
  OpenFileGDB -vector- (rov): ESRI FileGDB
  FileGDB -vector- (rw+): ESRI FileGDB
```

## Shell into a Container

The syntax to run a shell in a container takes the general form of:  

$ singularity shell *container-path*.  For example:

```
gtamkin@dsg103:~$ singularity shell /att/gpfsfs/briskfs01/ppl/iluser/containers/cisto-centos-gdal-2.0.0.simg 
WARNING: Bind mount '/home/gtamkin => /home/gtamkin' overlaps container CWD /home/gtamkin, may not be available
Singularity> ogrinfo --formats | grep GDB
  OpenFileGDB -vector- (rov): ESRI FileGDB
  FileGDB -vector- (rw+): ESRI FileGDB
Singularity> ls
JupyterLinks  R  Untitled.ipynb  bin  slurm-9291.out  slurm-9359.out  slurm-9371.out  temp.txt
```





