# Docker Cross-Compiling Toolchains
As [dockcross](http://github.com/dockcross/dockcross) (or crosstool-ng) doesn't seem to actually use the configured glibc version, let's just build our own docker containers with a linux ARM cross-compiler.

## Usage
Docker containers are pushed to the GitHub container registry (ghcr.io) by a build pipeline on new tags.
To build them yourself, run `docker build` on the individual dockerfiles like this:
```shell
cd linux-gnueabihf-debian11
docker build -t $some_useful_name .
```

All dockerfiles support these build tools:
- GNU make

To cross-compile something, mount the working directory to `/work` and run your make command like this:
```shell
docker run --rm -v $(pwd):/work ghcr.io/considerit/cross-linux-armhf-debian11 make $target
```

## Images and Library Versions

Image                   | arch    | gcc | glibc
----------------------- | ------- | --- | -----
linux-aarch64-debian11  | aarch64 |  10 | 2.31
linux-armhf-ubuntu18    | armhf   |   7 | 2.27
linux-armhf-debian10    | armhf   |   8 | 2.28
linux-armhf-debian11    | armhf   |  10 | 2.31
