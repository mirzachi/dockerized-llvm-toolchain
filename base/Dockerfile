# Base image
FROM ubuntu:21.10

# Add some metadata for inspection purposes
LABEL version="1.0" \
      maintainer="mirza.avdic@tum.de" \
      description="Base image for all LLVM toolchain images."

# Install necessary dependencies and remove the apt cache since we do not need it later on
RUN apt-get update && \
    apt-get -y install build-essential git  && \
    rm -rf /var/lib/apt/lists/*

# Download, compile and install cmake
ENV cmake_version "3.21.0"
RUN wget https://github.com/Kitware/CMake/releases/download/v${cmake_version}/cmake-${cmake_version}.tar.gz
RUN tar -xzf cmake-${cmake_version}.tar.gz
RUN cd cmake-${cmake_version} && \
    ./bootstrap && make install && \
    cd .. && \
    rm -r cmake-*