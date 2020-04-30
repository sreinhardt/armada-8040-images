FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive
ENV APT_FLAGS="-y -qq"

# Base system config, leave gcc here for c libs
RUN dpkg-divert --local --rename --add /sbin/initctl &&\
  ln -sf /bin/true /sbin/initctl &&\
  apt-get update &&\
  apt-get install $APT_FLAGS build-essential make curl xz-utils vim git &&\
  apt-get autoremove $APT_FLAGS && apt-get clean $APT_FLAGS &&\
  rm -rf /var/lib/apt/lists* /tmp/* /var/tmp/*

# bring in aarch64 toolchain for x86_64 hosts
RUN mkdir /build/gcc-linaro &&\
  curl -L https://releases.linaro.org/components/toolchain/binaries/latest-7/aarch64-linux-gnu/gcc-linaro-7.5.0-2019.12-x86_64_aarch64-linux-gnu.tar.xz |\
  tar -xJ --strip-components=1 -C /build/gcc-linaro

# Create user and set perms on build tools
RUN useradd -Md /build -G users -s /usr/bin/bash build &&\
  mkdir -p /build/host &&\
  chown -R build:users /build &&\
  chmod -R 777 /build/gcc-linaro/bin

# cp linaro.dockerfile dockerfile
# docker build --rm --force-rm -t armada8040:linaro_gcc .
# docker run -ti --rm armada8040:linaro_gcc
# docker rmi armada8040:linaro_gcc
