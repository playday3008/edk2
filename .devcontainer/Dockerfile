# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.233.0/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use ubuntu-22.04 or ubuntu-18.04 on local arm64/Apple Silicon): ubuntu-22.04, ubuntu-20.04, ubuntu-18.04
ARG VARIANT="jammy"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
USER root

# Add i386 arch
RUN dpkg --add-architecture i386

# Install tools
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y full-upgrade \
    && apt-get -y install \
        ccache build-essential bison flex uuid-dev iasl nasm python-is-python3 make qemu file \
        gcc g++ gcc-arm-linux-gnueabihf g++-arm-linux-gnueabihf gcc-aarch64-linux-gnu g++-aarch64-linux-gnu gcc-riscv64-unknown-elf \
        libc6-dev:i386 libx11-dev:i386 libxext-dev:i386 lib32gcc-11-dev \
        clang clang-format clang-tidy llvm lld lldb

# Clean up
RUN apt-get autoremove -y \
    && apt-get clean -y

USER vscode

