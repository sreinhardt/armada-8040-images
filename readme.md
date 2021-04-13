### Armada 8040 Image Builders

This repo contains a series of dockerfiles and submodules for external code needed to build U-Boot and OS images. If there are any specific configurations added they will be for Macchiatobins.

### Linaro GCC base container

```sh
cd linaro
docker build --rm --force-rm -t armada8040:linaro_gcc .
```
[![linaro_gcc](https://github.com/mipsou/armada-8040-images/actions/workflows/linaro_gcc.yml/badge.svg)](https://github.com/mipsou/armada-8040-images/actions/workflows/linaro_gcc.yml)

### Building U-Boot

```sh
cd uboot
docker build --rm --force-rm -t armada8040:uboot .
docker run -ti --name uboot armada8040:uboot
docker cp uboot:/build/atf-marvell/build/a80x0_mcbin/release/flash-image.bin ./images/
docker rm uboot
docker rmi armada8040:uboot
```

### Building PfSense

```sh
cd pfsense
docker build --rm --force-rm -t armada8040:pfsense .
```
