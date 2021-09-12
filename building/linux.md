# Building on Linux
## Requirements:

Ubuntu 20.04:
Install the following:
### X11 Only
```
sudo apt install cmake gcc-10 g++-10 libssl-dev libavdevice-dev libboost-thread-dev libboost-filesystem-dev libboost-log-dev libpulse-dev libopus-dev libxtst-dev libx11-dev libxrandr-dev libxfixes-dev libevdev-dev libxcb1-dev libxcb-shm0-dev libxcb-xfixes0-dev
```

### X11 + KMS (Requires additional setup)
KMS allows Sunshine to grab the monitor with lower latency then through X11

```
sudo apt install cmake gcc-10 g++-10 libssl-dev libavdevice-dev libboost-thread-dev libboost-filesystem-dev libboost-log-dev libpulse-dev libopus-dev libxtst-dev libx11-dev libxrandr-dev libxfixes-dev libevdev-dev libxcb1-dev libxcb-shm0-dev libxcb-xfixes0-dev libdrm-dev libcap-dev
```

## Compilation:

### X11 Only
- `git clone https://github.com/loki-47-6F-64/sunshine.git --recurse-submodules`
- `cd sunshine && mkdir build && cd build`
- `cmake -DCMAKE_C_COMPILER=gcc-10 -DCMAKE_CXX_COMPILER=g++-10 -DSUNSHINE_ENABLE_DRM=OFF ..`
- `make -j ${nproc}`

### X11 + KMS
- `git clone https://github.com/loki-47-6F-64/sunshine.git --recurse-submodules`
- `cd sunshine && mkdir build && cd build`
- `cmake -DCMAKE_C_COMPILER=gcc-10 -DCMAKE_CXX_COMPILER=g++-10 ..`
- `make -j ${nproc}`

Continue here: [Setup](/setup/linux.md)