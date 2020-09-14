# image-builder-rpi For RDBOX

[![CircleCI](https://circleci.com/gh/rdbox-intec/image-builder-rpi.svg?style=svg)](https://circleci.com/gh/rdbox-intec/image-builder-rpi)

forked from [HypriotOS](https://github.com/hypriot/image-builder-rpi)  
The major design pattern of this software was abstracted from hypriot's image-builder-rpi, which is subject to the same license.

This repo builds the SD card image with RDBOX based on HypriotOS for the Raspberry Pi 3 series.
You can find released versions of the SD card image here in the GitHub
[releases page](./releases). To build this SD card image we have to

- take the files for the root filesystem from [`os-rootfs`](https://github.com/hypriot/os-rootfs)
- take the empty raw filesystem from [`image-builder-raw`](https://github.com/hypriot/image-builder-raw) with the two partitions
- install Docker tools Docker Engine, Docker Compose and Docker Machine
- install kubernetes by kubeadmn.
- Device settings are set so that turtlebot 3 can be used in haste.
- install tools of RDBOX networks applications.
  - transproxy
  - hostapd
  - softether-vpn
  - bridge-util
  - batctl
  - dnsmasq
  - nfs
  - ntp
  - etc...

## Contributing

You can contribute to this repo by forking it and sending us pull requests.
Feedback is always welcome!

You can build the SD card image locally with Vagrant.

### Setting up build environment

Make sure you have [vagrant](https://docs.vagrantup.com/v2/installation/) installed.
Then run the following command to create the Vagrant box and use the Vagrant Docker
daemon. The Vagrant box is needed to run guestfish inside.
Use `export VAGRANT_DEFAULT_PROVIDER=virtualbox` to strictly create a VirtualBox VM.

Start vagrant box

```bash
vagrant up
```

Export docker host

```bash
export DOCKER_HOST=tcp://127.0.0.1:2375
```

Check you are using docker from inside vagrant

```bash
docker info | grep 'Operating System'
Operating System: Ubuntu 16.04.4 LTS
```

### Build the SD card image

From here you can just make the SD card image. The output will be written and
compressed to `hypriotos-rpi-v1.10.0.rdbox-v0.0.25.img.zip'

```bash
make sd-image-rdbox
```

### Run Serverspec tests

comming soon.

### Run integration tests

comming soon.

## Deployment

comming soon.

## License

MIT - see the [LICENSE](./LICENSE) file for details.

