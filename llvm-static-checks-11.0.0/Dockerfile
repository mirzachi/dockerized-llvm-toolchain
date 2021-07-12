# Base image
FROM ghcr.io/mirzachi/dockerized-llvm-toolchain/base:main

# Add some metadata for inspection purposes
LABEL version="1.0" \
      maintainer="mirza.avdic@tum.de" \
      description="Containerized clang-format and clang-tidy 11.0.0"

# LLVM Version to download
ENV LLVM_VERSION 11

# Copy LLVM install script
COPY common/install-llvm-static-checks.sh /home/root/install-llvm-static-checks.sh

WORKDIR /home/root

# Install LLVM toolchain
RUN ls -la /home/root && ./install-llvm-static-checks.sh ${LLVM_VERSION}

# Add generic symbolic links for often used tools
RUN ln -s /usr/bin/clang-tidy-${LLVM_VERSION} /usr/bin/clang-tidy && \
    ln -s /usr/bin/clang-format-${LLVM_VERSION} /usr/bin/clang-format

ENTRYPOINT ["/bin/bash", "-l", "-c"]