# containerd

This image provides a functional installation of
[containerd](https://github.com/containerd/containerd)
with [runc](https://github.com/opencontainers/runc),
and [CNI plugin](https://github.com/containernetworking/plugins). 
It is useful for experimenting with `containerd` or CNI configuration, or developing clients of the
[Container Runtime Interface (CRI)](https://github.com/kubernetes/cri-api). 

By default, the CNI is configured with a [loopback](./etc/cni/99-loopback.conf) and
[bridge](./etc/cni/10-bridge.conf) interface, and `containerd` is [configured](./etc/config.toml)
to use the `native` snapshotter for maximum compatibility. For everything to work, you must run the
container in `privileged` mode with `host` networking:

```
docker run -it \ 
    --network host \
    --privileged \
    drydockapp/containerd:latest
```