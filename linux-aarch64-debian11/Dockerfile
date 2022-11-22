FROM debian:11-slim

RUN apt update

# install basic build tools
RUN apt -y install make git ccache rsync python3

# install aarch64 cross-compiler
RUN apt -y install g++-aarch64-linux-gnu

# git might complain about ownership, so ignore it
RUN git config --global --add safe.directory /work

WORKDIR /work
