# Copyright (C) 2018 Laboratory of Experimental Biophysics
# Ecole Polytechnique Federale de Lausanne (EPFL), Switzerland
#
# Creates an image for building Micro-Manager plugins.
#

FROM maven:3.5.3-jdk-8 as install_jars
MAINTAINER Kyle M. Douglass <kyle.m.douglass@gmail.com>

ARG MM_ROOT="/micro-manager"
ARG JARS_DIR="share/micro-manager/jars"
ARG MM_MVN_REPO="/root/.m2/repository/org/micro-manager"

COPY . ${MM_ROOT}
WORKDIR ${MM_ROOT}
RUN ${MM_ROOT}/setup "${JARS_DIR}"

# Copy just the build dependencies into the image.
FROM maven:3.5.3-jdk-8 as app

ARG MM_MVN_REPO="/root/.m2/repository/org/micro-manager"

COPY --from=install_jars ${MM_MVN_REPO}/MMCoreJ-2.0gamma ${MM_MVN_REPO}/MMCoreJ-2.0gamma
COPY --from=install_jars ${MM_MVN_REPO}/MMAcqEngine-2.0gamma ${MM_MVN_REPO}/MMAcqEngine-2.0gamma
COPY --from=install_jars ${MM_MVN_REPO}/MMJ_-2.0gamma ${MM_MVN_REPO}/MMJ_-2.0gamma