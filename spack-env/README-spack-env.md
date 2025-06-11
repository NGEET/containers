# Spack Environment configuration for Dockerfile build

This subdirectory contains the Spack environment configuration, `spack.yaml`, to be used with Spack's `containerize` cability to develop Dockerfiles. These Dockerfiles will then be used to build container images for other needs.  The environment is configured to run on Ubuntu Jammy (22.04).

## Overview

The Spack environment is defined in the `spack.yaml` file, which specifies the operating system, version, and the required packages. The following packages are included in this environment:

- **OpenMPI**: A high-performance message passing library.
- **NetCDF-C**: A library for array-oriented data access.
- **NetCDF-Fortran**: Fortran interface to the NetCDF library.
- **CMake**: A tool for managing the build process of software.
- **Perl XML::LibXML**: A Perl module for working with XML.
- **Netlib LAPACK**: A library for linear algebra operations.
- **ESMF**: The Earth System Modeling Framework, with support for MPI and NetCDF.


## Usage

A github workflow will utilize the `spack.yaml` file to generate a dockerfile, to in turn build and publish a container image on the github container registry.