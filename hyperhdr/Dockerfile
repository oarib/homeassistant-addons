FROM ubuntu:22.04

# Éviter les prompts interactifs (comme pour tzdata)
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

RUN apt-get update && apt-get install -y \
    git cmake build-essential qtbase5-dev libqt5serialport5-dev \
    libusb-1.0-0-dev libturbojpeg0-dev libavcodec-dev libavformat-dev \
    libswscale-dev libqt5svg5-dev qttools5-dev-tools qttools5-dev \
    libudev-dev pkg-config tzdata && \
    rm -rf /var/lib/apt/lists/*

# Copier les sources clonées par GitHub Actions
COPY hyperhdr-source /opt/hyperhdr

# Compilation
WORKDIR /opt/hyperhdr
RUN mkdir build && cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release .. && \
    make -j$(nproc) && make install

CMD ["hyperhdr"]
