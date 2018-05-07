This repository contains Dockerfiles that are used to build components
of Micro-Manager.

# Builds

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
  filename--inside the container.

- If CONFIGURE=true, the build system is remade and the configure
  script is rerun before running 'make' and 'make install'. If
  CONFIGURE=false, only 'make' and 'make install' are run.
  
- The build artifacts will be saved to the host system in the
  directory specified in the Dockerfile (typically this is
  <HOST_DIR>/target).
  
## Micro-Manager plugins (Maven)

```
cd micro-manager/mvn-plugin
```

Create an image containing Maven and the Micro-Manager dependency
.jars.

```
./build TARGET_DIR
```

- TARGET_DIR is the path to the folder containing the Micro-Manager
  build artifacts.
  
-----

Compile a Micro-Manager Maven plugin.

```
./run PLUGIN_DIR
```

- PLUGIN_DIR is the root directory of your plugin, which typically
  contains the pom.xml file.
  
# Acknowledgements
- [Micro-Manager](https://micro-manager.org/)
- [Docker](https://www.docker.com/)
- [Maven](https://maven.apache.org/)

...and the many, many people behind *all* the software that we
rely on.
