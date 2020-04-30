### Armada 8040 Image Builders

This repo contains a series of dockerfiles and submodules for external code needed to build U-Boot and OS images. If there are any specific configurations added they will be for Macchiatobins.

### Linaro GCC base container

```sh
cd linaro
docker build --rm --force-rm -t armada8040:linaro_gcc .
```

### Building U-Boot

```sh
cd uboot
docker build --rm --force-rm -t armada8040:uboot .
docker run -ti --rm -v ${pwd}:/build/host:rw armada8040:uboot
```
