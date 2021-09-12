---
parent: Building
nav_order: 2
---
# Building on Windows 10

## Requirements:

First you need to install [MSYS2](https://www.msys2.org), then startup "MSYS2 MinGW 64-bit" and install the following packages using `pacman -S`:

	mingw-w64-x86_64-openssl mingw-w64-x86_64-cmake mingw-w64-x86_64-toolchain mingw-w64-x86_64-opus mingw-w64-x86_64-x265 mingw-w64-x86_64-boost git mingw-w64-x86_64-make cmake make gcc

## Compilation:
- `git clone https://github.com/loki-47-6F-64/sunshine.git --recursive`
- `cd sunshine && mkdir build && cd build`
- `cmake -G"Unix Makefiles" ..`
- `mingw32-make`

Continue here: [Setup](/setup/windows10.html)