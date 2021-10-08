<meta charset="UTF-8">

RIME: Rime Input Method Engine
===
[![Build Status](https://travis-ci.org/rime/librime.svg)](https://travis-ci.org/rime/librime)
[![Build status](https://ci.appveyor.com/api/projects/status/github/rime/librime?svg=true)](https://ci.appveyor.com/project/rime/librime)
[![GitHub release](https://img.shields.io/github/release/rime/librime.svg)](https://github.com/rime/librime/releases)
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

Rime with your keystrokes.

Project home
---
[rime.im](https://rime.im)

License
---
[The 3-Clause BSD License](https://opensource.org/licenses/BSD-3-Clause)

Features
===
  - A modular, extensible input method engine in cross-platform C++ code,
    built on top of open-source technologies
  - Covering features found in a large variety of Chinese input methods,
    either shape-based or phonetic-based
  - Built with native support for Traditional Chinese, conversion to Simplified
    Chinese and other regional standards via OpenCC
  - Rime input schema, a DSL in YAML syntax for fast trying out innovative ideas
    of input method design
  - Spelling Algebra, a mechanism to create variant spelling, especially useful
    for Chinese dialects
  - Support for chord-typing with a generic Qwerty keyboard

Install
===
Follow the instructions to build librime on platforms other than Linux:
  - [macOS](https://github.com/rime/librime/tree/master/README-mac.md)
  - [Windows](https://github.com/rime/librime/tree/master/README-windows.md)

Build dependencies
---
  - compiler with C++14 support
  - capnproto>=0.7.0
  - cmake>=2.8
  - libboost>=1.48
  - libcapnp>=0.7.0
  - libglog (optional)
  - libleveldb
  - libmarisa
  - libopencc>=1.0.2
  - libyaml-cpp>=0.5
  - libgtest (optional)

Runtime dependencies
---
  - libboost
  - libcapnp
  - libglog (optional)
  - libleveldb
  - libmarisa
  - libopencc
  - libyaml-cpp

Build and install librime on Linux
---
```
make
sudo make install
```
Another build method on ubuntu
```
sudo apt install pkg-config -y
sudo apt install libboost-all-dev -y
sudo apt install libgoogle-glog-dev -y
sudo apt install libyaml-cpp-dev -y
sudo apt install libmarisa-dev -y
sudo apt install libgtest-dev -y
sudo apt install libsnappy-dev -y
sudo apt install libopencc-dev -y
sudo apt install libleveldb-dev -y

git clone --recurse-submodules https://github.com/rime-windows/librime.git
mkdir librime/build
cd librime/build
rm -rf * && cmake .. -DENABLE_LOGGING=OFF -DBUILD_TEST=OFF && make && ls && sudo make install
```

Build on Windows
===
1. download and install `VS 2019` from [Microsoft Visual Studio site](https://visualstudio.microsoft.com/downloads/)
2. install [cmake](https://cmake.org/)
3. install [git](https://git-scm.com/), then clone `vcpkg` source code and install required libraries on `D disk (d:/vcpkg)`
```
d:
cd /
git clone https://github.com/microsoft/vcpkg.git
cd d:/vcpkg
bootstrap-vcpkg.bat

vcpkg integrate install

vcpkg install boost:x86-windows boost:x64-windows
vcpkg install gtest:x86-windows gtest:x64-windows
vcpkg install gflags:x86-windows gflags:x64-windows
vcpkg install glog:x86-windows glog:x64-windows
vcpkg install opencc:x86-windows opencc:x64-windows
vcpkg install openssl:x86-windows openssl:x64-windows
vcpkg install yaml-cpp:x86-windows yaml-cpp:x64-windows
vcpkg install zlib:x86-windows zlib:x64-windows
vcpkg install zstd:x86-windows zstd:x64-windows
```
4. clone librime source code to `d:/librime/`
```
d:
cd /
git clone --recurse-submodules https://github.com/rime-windows/librime.git
```
5. use `cmake` generate the build environment.
```
d:
mkdir d:/librime/build
cd d:/librime/build
cmake .. -DCMAKE_TOOLCHAIN_FILE=D:/vcpkg/scripts/buildsystems/vcpkg.cmake -DENABLE_LOGGING=OFF -DBUILD_TEST=OFF
```
6. open `Visual Studio 2019 Developer Command Prompt`, then build librime with it.
```
d:
cd d:/librime/build
devenv rime.sln /build debug
devenv rime.sln /build debug
```
7. done

Frontends
===

Official:
  - [ibus-rime](https://github.com/rime/ibus-rime): IBus frontend for Linux
  - [Squirrel](https://github.com/rime/squirrel): frontend for macOS
  - [Weasel](https://github.com/rime/weasel): frontend for Windows

Third-party:
  - [emacs-rime](https://github.com/DogLooksGood/emacs-rime): frontend for Emacs
  - [fcitx-rime](https://github.com/fcitx/fcitx-rime): Fcitx frontend for Linux
  - [iRime](https://github.com/jimmy54/iRime): frontend for iOS
  - [PIME](https://github.com/EasyIME/PIME): frontend for Windows
  - [Trime](https://github.com/osfans/trime): frontend for Android
  - [XIME](https://github.com/stackia/XIME): frontend for macOS

Plugins
===
  - [librime-charcode](https://github.com/rime/librime-charcode) Module that
    deals with character encoding; depends on boost::locale and ICU libraries
  - [librime-legacy](https://github.com/rime/librime-legacy) Legacy module with
    GPL-licensed code

Related works
===
  - [plum](https://github.com/rime/plum): Rime configuration manager and input
    schema repository
  - [Combo Pinyin](https://github.com/rime/home/wiki/ComboPinyin): an innovative
    chord-typing practice to input Pinyin
  - essay: the vocabulary and language model for Rime
  - [SCU](https://github.com/neolee/SCU): Squirrel Configuration Utilities

Credits
===
We are grateful to the makers of the following open source libraries:

  - [Boost C++ Libraries](http://www.boost.org/) (Boost Software License)
  - [google-glog](https://github.com/google/glog) (The 3-Clause BSD License)
  - [Google Test](https://github.com/google/googletest) (The 3-Clause BSD License)
  - [LevelDB](https://github.com/google/leveldb) (The 3-Clause BSD License)
  - [marisa-trie](https://github.com/s-yata/marisa-trie) (BSD 2-Clause License, LGPL 2.1)
  - [OpenCC](https://github.com/BYVoid/OpenCC) (Apache License 2.0)
  - [yaml-cpp](https://github.com/jbeder/yaml-cpp) (MIT License)

Contributors
===
  - [佛振](https://github.com/lotem)
  - [鄒旭](https://github.com/zouxu09)
  - [Weng Xuetian](http://csslayer.info)
  - [Chongyu Zhu](http://lembacon.com)
  - [Zhiwei Liu](https://github.com/liuzhiwei)
  - [BYVoid](http://www.byvoid.com)
  - [雪齋](https://github.com/LEOYoon-Tsaw)
  - [瑾昀](https://github.com/kunki)
  - [osfans](https://github.com/osfans)
  - [jakwings](https://github.com/jakwings)
  - [Prcuvu](https://github.com/Prcuvu)
  - [hchunhui](https://github.com/hchunhui)
