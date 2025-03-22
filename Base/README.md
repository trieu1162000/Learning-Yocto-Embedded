# Raspberry Pi core minimal image

This guide intends to summarize the essencial steps performed to build a Raspberry Pi minmal image using Yocto.

## Download software dependencies

To build the image we are going to use the [Poky](http://git.yoctoproject.org/cgit/cgit.cgi/poky) and the layers [meta-openembedded](http://git.openembedded.org/meta-openembedded) , [meta-raspberrypi](https://github.com/agherzan/meta-raspberrypi) .

The list of all meta-raspberrypi dependencies are contained in the [Readme.md](https://github.com/agherzan/meta-raspberrypi/blob/krikstone /README.md#dependencies) the provided MACHINE's are  listed on the [layer-contentens.md](https://github.com/agherzan/meta-raspberrypi/blob/krikstone /docs/layer-contents.md#supported-machines)


- Use Git to clone Poky repo using the apropriate [version](https://wiki.yoctoproject.org/wiki/Releases) branch.
```$ git clone -b krikstone  git://git.yoctoproject.org/poky.git```

- Enter into the Poky folder  
```$ cd poky```

- Use Git to clone the meta-rasperrypi layer repo using the apropriate [version](https://wiki.yoctoproject.org/wiki/Releases) branch.  
```$ git clone -b krikstone  git://git.yoctoproject.org/meta-raspberrypi```

- Use Git to clone the meta-openembedded layer repo using the apropriate [version](https://wiki.yoctoproject.org/wiki/Releases) branch.  
```$ git clone -b krikstone  git://git.openembedded.org/meta-openembedded```

## Modify
- Initialize the build env  
```$ source oe-init-build-env```
- Modify your local.conf file: Set your machine to ```MACHINE = "raspberrypi"``` according to your Raspberry Pi [model](https://github.com/agherzan/meta-raspberrypi/blob/krikstone /docs/layer-contents.md#supported-machines).

- Modify the bbplayers.conf file and add all the listed dependencies listed on the [Readme.md](https://github.com/agherzan/meta-raspberrypi/blob/krikstone /README.md#dependencies).  

```
BBLAYERS ?= " \
    /home/joao/yocto/poky/meta \
    /home/joao/yocto/poky/meta-poky \
    /home/joao/yocto/poky/meta-yocto-bsp \
    /home/joao/yocto/poky/meta-raspberrypi \

## Build
- Build the image  *minimal* ```$ bitbake -k core-image-minimal```.  
Other available images are listed [here](https://github.com/agherzan/meta-raspberrypi/blob/krikstone /docs/layer-contents.md#images).
