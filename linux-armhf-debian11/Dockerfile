FROM debian:11-slim

RUN apt update

# install basic build tools
RUN apt -y install make git ccache rsync python3

# install armhf cross-compiler
RUN apt -y install g++-arm-linux-gnueabihf

# git might complain about ownership, so ignore it
RUN git config --global --add safe.directory /work

WORKDIR /work
