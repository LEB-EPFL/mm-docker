# Copyright (C) 2018 Laboratory of Experimental Biophysics
# Ecole Polytechnique Federale de Lausanne (EPFL), Switzerland
#
# Creates a container for building the Micro-Manager Java components.
#

FROM openjdk:8-jdk
MAINTAINER Kyle M. Douglass <kyle.m.douglass@gmail.com>

ARG APP_ROOT="/src"
ARG SRC_DIR="${APP_ROOT}/micro-manager"
ARG MM_SRC_DIR="${SRC_DIR}/micro-manager"
ARG MM_BUILD_DIR="${SRC_DIR}/targets"

RUN apt update && apt -y install --no-install-recommends \
    ant \
    autoconf \
    automake \
    build-essential \
    libboost-all-dev \
    libtool \
    pkg-config \
    swig \
    && mkdir -p "${SRC_DIR}"

# setup is the script that compiles Micro-manager.
COPY setup ${APP_ROOT}
VOLUME ${SRC_DIR}
WORKDIR ${SRC_DIR}

CMD [ "${APP_ROOT}/setup ${MM_SRC_DIR} ${MM_BUILD_DIR} true"]
