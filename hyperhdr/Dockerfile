FROM ubuntu:22.04

RUN apt update && apt install -y \
    git cmake build-essential qtbase5-dev libqt5serialport5-dev \
    libusb-1.0-0-dev libturbojpeg0-dev libavcodec-dev libavformat-dev \
    libswscale-dev libqt5svg5-dev qttools5-dev-tools qttools5-dev \
    && rm -rf /var/lib/apt/lists/*

RUN git clone --recurse-submodules https://github.com/awawa-dev/HyperHDR.git /opt/hyperhdr \
    && mkdir /opt/hyperhdr/build \
    && cd /opt/hyperhdr/build \
    && cmake -DCMAKE_BUILD_TYPE=Release .. \
    && make -j$(nproc) \
    && make install

CMD ["hyperhdr"]
