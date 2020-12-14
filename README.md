# Container Repository Overview
This repository hosts all container recipe files (refactored from application-specific repositories) built by the Innovation Lab (IL) development team.  Primarly, two types of containers exist:  1) General-purpose, and 2) Application-specific.  General-puropse containers contain reusable functionality for multiple applications.  Application-specific containers host unique software and configuration artifacts for a specific use.  The application-specific containers incorporate and extend the core general-purpose containers.

# Container Technology
IL recipes are written for deployment to Singularity frameworks (as required by CISTO/NCCS). Each recipe is used when building the corresponding container image using syntax of the general form:  $ singularity build 'target container name' 'container recipe'

Example (ADAPT):
$ time /usr/bin/sudo -E SINGULARITY_NOHTTPS=1 /usr/local/bin/singularity build ilab-core-2.0.0.simg ilab-core-2.0.0.def 

Containers are built hiearchically.  For example, the based Python scientific system container is the parent of the IL core container.  This approach allows for managing specific software dependencies and versions per container while giving the target image flexibility for extended appliccation-specific features.


# Container Inventory (alphabetical order)

| Name  | Description  | Parent |
| :------------ |:---------------|:-----|
| cisto-data-science-*      | general purpose python data science ecosystem [Debian, NumPy, SciPy, Pandas, etc.]| docker: openjdk:8-jdk-stretch |
| ilab-apps-*      | Innovation Lab application snapshot [Debian, MMX, etc.]| singularity: ilab-core-* |
| ilab-core-*      | Innovation Lab debian common dependencies [Debian, Celery, GDAL, etc] | singularity: cisto-data-science-* |

| cisto-centos-gdal-*     | general purpose centos OS with GDAL         |   docker: centos |
| cisto-centos-gdal-*     | general purpose centos OS with GDAL         |   docker: centos |
| cisto-jupyter-lab-<X>      | general purpose jupyter lab host         |   $12 |
| zebra stripes | are neat        |    $1 |
