# Super Mario War

![Linux status][build-linux-img] ![Windows status][build-mingw-img] [![AppVeyor][appveyor-img]][appveyor-link] [![Discord][discord-img]][discord-link]

Super Mario War is a fan-made multiplayer Super Mario Bros. style deathmatch game in which players try to beat one another in a variety of gameplay modes. You can play on teams, design your own levels, design your own worlds, and much more!
This repo is made for handheld RG353P specific build.

## Building instructions

### Requirements

- C++11 supporting compiler (eg. gcc-4.8)
- CMake (>= 2.6)
- SDL (1.2 or 2.0), with
    - SDL_image
    - SDL_mixer
- zlib
- yaml-cpp (included)
- ENet (optional, included)

You can use package managers for getting these dependencies:
- Debian-based: `apt-get install cmake libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev zlib1g-dev`

### Get the code

This repository contains some submodules which you can use if the dependencies are not available for your OS, are outdated or you simply don't want to install them on your system. To use the included libraries, do a recursive cloning:

```sh
git clone --recursive https://github.com/mmatyas/supermariowar.git
cd supermariowar/
mkdir build
cd build/

CC=aarch64-linux-gnu-gcc CXX=aarch64-linux-gnu-g++ \
CFLAGS='-march=armv8-a' CXXFLAGS='-march=armv8-a' \
PKG_CONFIG_DIR="" PKG_CONFIG_LIBDIR="/usr/lib/aarch64-linux-gnu/pkgconfig" \
cmake -DDISABLE_DEFAULT_CFLAGS=1 ..
patch < smw_rg353p.patch

make
```

## How to play

Please see documentation in the docs/ directory.

[build-linux-img]: https://github.com/mmatyas/supermariowar/actions/workflows/build_linux.yml/badge.svg
[build-mingw-img]: https://github.com/mmatyas/supermariowar/actions/workflows/build_mingw.yml/badge.svg
[appveyor-img]: https://ci.appveyor.com/api/projects/status/github/mmatyas/supermariowar?svg=true
[appveyor-link]: https://ci.appveyor.com/project/mmatyas/supermariowar
[discord-img]: https://img.shields.io/badge/Discord-7389D8?logo=discord&logoColor=white
[discord-link]: https://discord.gg/SC4uXQB
