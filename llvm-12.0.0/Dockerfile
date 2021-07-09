# Base image
FROM docker.pkg.github.com/mirzachi/dockerized-llvm-toolchain/base:1.0

# Add some metadata for inspection purposes
LABEL version="1.0" \
      maintainer="mirza.avdic@tum.de" \
      description="Containerized LLVM 12.0.0 toolchain"

# LLVM Version to download
ENV LLVM_VERSION 12

# Copy LLVM install script
COPY common/install-llvm.sh /home/root/install-llvm.sh

WORKDIR /home/root

# Install LLVM toolchain
RUN ls -la /home/root && ./install-llvm.sh ${LLVM_VERSION}

# Add generic symbolic links for often used tools
RUN ln -s /usr/bin/clang-${LLVM_VERSION} /usr/bin/clang && \
    ln -s /usr/bin/clang++-${LLVM_VERSION} /usr/bin/clang++ && \
    ln -s /usr/bin/clang-tidy-${LLVM_VERSION} /usr/bin/clang-tidy && \
    ln -s /usr/bin/clang-format-${LLVM_VERSION} /usr/bin/clang-format

ENTRYPOINT ["/bin/bash"]