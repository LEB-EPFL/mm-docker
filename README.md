This repository contains Dockerfiles that are used to build components
of Micro-Manager.

# Quick reference

## Micro-Manager Java components

```
cd micro-manager/build-java
```

Create the image for compiling the Micro-Manager Java components:

```
./build
```

-----

Compile the Micro-Manager Java components:

```
./run HOST_DIR CONT_DIR SETUP_SCRIPT CONFIGURE
```

- HOST_DIR is the parent folder containing the micro-manager Git
  repository, the 3rdpartypublic Subversion repository, and any
  additional build resources on the host system. The source code and
  3rdpartypublic dependencies live on the host system instead of
  inside the container because they are frequently changed and quite
  large.
  
- CONT_DIR the directory corresponding to the HOST_DIR in the Docker
  container.

- SETUP_SCRIPT is the full path to the setup script--including the
  filename--inside the container. Typically, it is /src/setup. You can
  verify this in the
  [Dockerfile](https://github.com/LEB-EPFL/mm-docker/blob/master/micro-manager/build-java/Dockerfile)

- If CONFIGURE=true, the build system is remade and the configure
  script is rerun before running 'make' and 'make install'. If
  CONFIGURE=false, only 'make' and 'make install' are run.
  
- The build artifacts will be saved to the host system in the
  directory specified in the Dockerfile (typically this is
  <HOST_DIR>/target).

### Example
```
./run ~/src/micro-manager /src/micromanager /src/setup true
```

## Micro-Manager 2.0 plugins (Maven)

```
cd micro-manager/mvn-plugin-2.0
```

Create an image containing Maven and the Micro-Manager dependency
.jars.

```
./build TARGET_DIR
```

- TARGET_DIR is the path to the folder containing the Micro-Manager
  build artifacts.
  
- The image will only include MMCoreJ, MMAcqEngine, and MMJ_ installed
  into the container's local Maven repository.
  
-----

Compile a Micro-Manager 2.0 plugin with Maven.

```
./run PLUGIN_DIR
```

- PLUGIN_DIR is the root directory of your plugin, which typically
  contains the pom.xml file.
  
# Docker images

Pre-built Docker images may be pulled from the [LEB Dockerhub
repository](https://hub.docker.com/r/epflbiophys/micro-manager/). Only
the run scripts are needed if using the pre-built images.

# Acknowledgements
- [Micro-Manager](https://micro-manager.org/)
- [Docker](https://www.docker.com/)
- [Maven](https://maven.apache.org/)

...and the many, many people behind *all* the software that we
rely on.
