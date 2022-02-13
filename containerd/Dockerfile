FROM debian:bullseye-slim

RUN apt update \
    && apt install -y wget iptables openssl ca-certificates \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /root

# Install ContainerD
ENV CONTAINERD_VERSION=1.5.9
RUN wget -q https://github.com/containerd/containerd/releases/download/v$CONTAINERD_VERSION/containerd-$CONTAINERD_VERSION-linux-amd64.tar.gz && \
    tar -xf containerd-$CONTAINERD_VERSION-linux-amd64.tar.gz && \
    rm containerd-$CONTAINERD_VERSION-linux-amd64.tar.gz

# Configure Basic CNI
ENV CNI_VERSION=1.0.1
RUN wget -q https://github.com/containernetworking/plugins/releases/download/v$CNI_VERSION/cni-plugins-linux-amd64-v$CNI_VERSION.tgz && \
    mkdir -p /etc/cni/net.d /opt/cni/bin && \
    tar -xf cni-plugins-linux-amd64-v$CNI_VERSION.tgz -C /opt/cni/bin/ && \
    rm cni-plugins-linux-amd64-v$CNI_VERSION.tgz

# Install RUNC
ENV RUNC_VERSION=1.1.0
RUN wget -q https://github.com/opencontainers/runc/releases/download/v$RUNC_VERSION/runc.amd64 && \
    mv runc.amd64 /bin/runc && \
    chmod +x /bin/runc

ADD etc/cni /etc/cni
ADD etc/containerd /etc/containerd

LABEL org.opencontainers.image.source https://github.com/drydock-app/library

WORKDIR /var/log/containerd
ENTRYPOINT ["/root/bin/containerd"]