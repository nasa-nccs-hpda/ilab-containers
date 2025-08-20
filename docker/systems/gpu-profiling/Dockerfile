FROM ubuntu:22.04

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    nvtop \
    htop \
    procps \
    dstat \
    pciutils \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

CMD ["nvtop"]
