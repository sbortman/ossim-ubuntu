FROM ubuntu:18.04

WORKDIR /work

ENV OSSIM_INSTALL_PREFIX=/usr/local \
    OSSIM_DATA=/data \
    OSSIM_PREFS_FILE=/usr/local/share/ossim/ossim-preferences-template \
    LD_LIBRARY_PATH=/usr/local/lib64:/usr/local/lib \
    JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64 \
    REPOSITORY_MANAGER_URL=https://nexus.ossim.io/repository \
    OSSIM_DEV_HOME=/work \
    OSSIM_HOME=/work/ossim \
    OSSIM_VERSION=1.9.0 \
    OSSIM_VERSION_TAG=RELEASE \
    # GROOVY_HOME=/work/groovy-3.0.5 \    
    KAKADU_VERSION=vs8_0_5-02003C

COPY ./build-kakadu.sh ./build-ossim.sh ./build-joms.sh /work/
COPY ./ossim/ /work/ossim/
COPY ./ossim-oms/ /work/ossim-oms/
COPY ./ossim-plugins/ /work/ossim-plugins/
COPY ./ossim-video/ /work/ossim-video/
COPY ./ossim-private/ /work/ossim-private/
COPY ./ossim-qt4/ /work/ossim-qt4/

# COPY  ./apache-groovy-binary-3.0.5.zip /work

RUN apt update -y \
    && apt install -y cmake git vim g++ libgeos-dev libgeotiff-dev libcurl4-openssl-dev ffmpeg libavcodec-dev \
    libavformat-dev  libavdevice-dev libgdal-dev  openjdk-11-jdk qt4-dev-tools \
    && ./build-kakadu.sh \
    && ./build-ossim.sh \
    # && ./build-joms.sh \
    && echo ""

CMD bash
