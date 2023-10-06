FROM debian:11-slim

ARG workdir=/work
ENV CROSS_SYSROOT=/var/cross-sysroot

# install basic utilities
RUN apt update && apt -y install git rsync python3

# git might complain about ownership, so ignore it
RUN git config --global --add safe.directory $workdir

# install aarch64 cross-compiler
RUN apt -y install g++-aarch64-linux-gnu

# install basic build tools
RUN apt -y install build-essential make ccache cmake ninja-build

# setup CMake for cross-compiling
RUN mkdir -p ${CROSS_SYSROOT}/include/
RUN mkdir -p ${CROSS_SYSROOT}/lib/
ENV CMAKE_TOOLCHAIN_FILE=${CROSS_SYSROOT}/toolchain.cmake
COPY linux-aarch64-tc.cmake ${CMAKE_TOOLCHAIN_FILE}
COPY cmake-cross.sh /usr/bin/cmake-cross

WORKDIR $workdir
