FROM ubuntu:18.04

RUN apt update

# install basic build tools
RUN apt -y install make git ccache rsync

# install armhf cross-compiler
RUN apt -y install g++-arm-linux-gnueabihf

WORKDIR /work