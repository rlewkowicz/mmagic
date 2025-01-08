# Docker Image

## CUDA Docker

For modern cuda docker integrations you'll need recent a docker version and the nvidia-container-toolkit

Docker:
```shell
# This will install the latest docker for your system regardless of how
# you installed it. Could break things If you have something custom.
curl -fsSL https://get.docker.com | sed 's/sleep [0-9]*/sleep 0/g' | sh
```

Nvidia container toolkit:
https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html


## Build

```shell
docker build -t mmagic .
```

Run it with

```shell
docker run --gpus all --shm-size=8g -it -v {DATA_DIR}:/mmagic/data mmagic
```

**Note**:
Prior documentation used pytorch images. Refer to prior commits if needed. Versions defined in this [Dockerfile](Dockerfile) is not up-to-date.
If you use this Dockerfile in your project, you probably want to make some updates.
Feel free to submit an issue or PR for the update.
