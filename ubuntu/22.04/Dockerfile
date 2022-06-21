FROM ubuntu:22.04 as base

RUN apt-get update \
    && apt-get install -y \
        curl \
        clang-14 \
        clang-tools-14 \
        gdb \
        liblldb-14-dev \
        lldb-14 \
        llvm-14 \
        locales \
        make \
        sudo \
        git \
        nodejs \
        npm \
        tar \
        zip \
        apt-transport-https \
        ca-certificates \
        gnupg \
        software-properties-common \
        wget \
    && wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc | apt-key add - \
    && apt-add-repository 'deb https://apt.kitware.com/ubuntu/ jammy main' \
    && rm -rf /var/lib/apt/lists/* \
    && locale-gen en_US.UTF-8

RUN curl -L -o azure-cli_jammy_all.deb https://aka.ms/InstallAzureCliJammyEdge \
    && dpkg -i azure-cli_jammy_all.deb \
    && apt-get update \
    && apt-get install -y \
        autoconf \
        automake \
        build-essential \
        gettext \
        libgdiplus \
        libicu-dev \
        libkrb5-dev \
        liblttng-ust-dev \
        libnuma-dev \
        libssl-dev \
        libtool \
        libunwind8 \
        libunwind8-dev \
        uuid-dev \
        libcurl4-openssl-dev \
        python3 \
        binfmt-support \
        binutils-arm-linux-gnueabihf \
        binutils-s390x-linux-gnu \
        cmake \
        cpio \
        debootstrap \
        qemu \
        qemu-user-static \
        rpm2cpio \
        libbz2-dev \
        libz-dev \
        liblzma-dev \
        libarchive-dev \
        libbsd-dev \
        libmpc-dev \
        libxml2-utils \
        lld-14 \
        python3-lldb-14 \
    && rm -rf /var/lib/apt/lists/*

COPY sources.list /sources.list

RUN mkdir -p /rootfs/s390x \
    && qemu-debootstrap --arch s390x jammy /rootfs/s390x \
    http://ports.ubuntu.com/ubuntu-ports/ \
    && cp /sources.list /rootfs/s390x/etc/apt/sources.list \
    && chroot /rootfs/s390x apt-get update \
    && chroot /rootfs/s390x apt-get -f -y install \
    && chroot /rootfs/s390x apt-get -y install build-essential \
    symlinks \
    libicu-dev \
    liblttng-ust-dev \
    libcurl4-openssl-dev \
    libkrb5-dev \
    libssl-dev \
    zlib1g-dev \
    && chroot /rootfs/s390x symlinks -cr /usr \
    && chroot /rootfs/s390x apt-get clean
