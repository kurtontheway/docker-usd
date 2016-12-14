############################################################
# Dockerfile to build USD on VFX Platform 2016
# Based on nvidia/cuda:devel-centos6

FROM nvidia/cuda:devel-centos6

MAINTAINER Aloys Baillet - Animal Logic

ENV BUILD_PROCS 7
ENV BUILD_DIR /opt/usd
ENV TMP_DIR /tmp/usd-build
ENV DOWNLOADS_DIR /tmp/usd-downloads

ENV PATH $BUILD_DIR/bin:$PATH
ENV PKG_CONFIG_PATH=$BUILD_DIR/lib/pkgconfig:$PKG_CONFIG_PATH
ENV LD_LIBRARY_PATH=$BUILD_DIR/lib64:$BUILD_DIR/lib:$LD_LIBRARY_PATH

RUN yum -y groupinstall "Development Tools"
RUN yum -y install \
    wget \
    cmake \
    openssl-devel \
    openssl \
    sqlite-devel \
    sqlite \
    glibc-devel.x86_64 \
    libicu-devel\
    libicu \
    wget \
    git \
    tar \
    bzip2 \
    bzip2-devel \
    glibc-devel.x86_64 \
    glibc-devel.i686 \
    zlib-devel.x86_64 \
    texinfo.x86_64 \
    libXext-devel \
    cmake \
    openssl-devel \
    libXext-devel \
    libXt-devel \
    libicu-devel \
    sqlite-devel \
    tk-devel \
    ncurses \
    ncurses-devel \
    freetype-devel.x86_64 \
    libxml2-devel.x86_64 \
    libxslt-devel.x86_64 \
    mesa-libGL-devel.x86_64 \
    libXrandr-devel.x86_64 \
    libXinerama-devel.x86_64 \
    libXcursor-devel.x86_64 \
    glut-devel \
    libXmu-devel \
    libXi-devel \
    pulseaudio-libs-devel.x86_64 \
    xorg-x11-fonts-Type1 \
    ca-certificates

COPY cert/*.pem /etc/pki/ca-trust/source/anchors/

RUN update-ca-trust force-enable && \
    update-ca-trust extract

COPY scripts/download_base.sh /tmp/
RUN /tmp/download_base.sh

COPY scripts/build_base.sh /tmp/
RUN /tmp/build_base.sh

ENV CC=$BUILD_DIR/bin/gcc
ENV CXX=$BUILD_DIR/bin/g++

CMD bash