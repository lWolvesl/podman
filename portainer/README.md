## PODMAN SHELL
```shell
systemctl --user enable --now podman.socket

podman run -d -p 49443:9443 --security-opt label=disable --name=portainer --restart=always -v /run/user/$(id -u)/podman/podman.sock:/var/run/docker.sock:Z -v /data/szh2/podman/portainer:/data  docker.io/portainer/portainer-ce
```

## cuda 支持
```shell
nvidia-ctk cdi generate --output=/etc/cdi/nvidia.yaml
```

### 测试
```shell
nvidia-ctk cdi list

podman run --rm --device nvidia.com/gpu=all docker.io/nvidia/cuda:12.3.1-base-ubuntu20.04 nvidia-smi -L

podman run --rm --device nvidia.com/gpu=0 --device nvidia.com/gpu=1 --security-opt=label=disable ubuntu nvidia-smi -L
```

## podman mirror
`/etc/containers/registries.conf`