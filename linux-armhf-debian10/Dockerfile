FROM debian:10-slim

ARG workdir=/work

# install basic utilities
RUN apt update && apt -y install git rsync python3

# git might complain about ownership, so ignore it
RUN git config --global --add safe.directory $workdir

# install armhf cross-compiler
RUN apt -y install g++-arm-linux-gnueabihf

# install basic build tools
RUN apt -y install build-essential make ccache

WORKDIR $workdir
