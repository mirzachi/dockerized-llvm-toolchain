# Base image
FROM ubuntu:21.04

# Add some metadata for inspection purposes
LABEL version="1.0" \
      maintainer="mirza.avdic@tum.de" \
      description="Base image for all LLVM toolchain images."

# Set timezone
ENV TZ=Europe
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Install necessary dependencies and remove the apt cache since we do not need it later on
RUN apt-get update && \
    apt-get -y install build-essential git wget lsb-release wget software-properties-common && \
    rm -rf /var/lib/apt/lists/*

# Download, compile and install cmake
ENV cmake_version "3.20.5"
RUN wget https://github.com/Kitware/CMake/releases/download/v${cmake_version}/cmake-${cmake_version}.tar.gz
RUN tar -xzf cmake-${cmake_version}.tar.gz
RUN cd cmake-${cmake_version} && \
    ./bootstrap -- -DCMAKE_USE_OPENSSL=OFF && make install -j8 && \
    cd .. && \
    rm -r cmake-*

ENTRYPOINT ["/bin/bash"]