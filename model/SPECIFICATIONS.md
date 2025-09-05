# Specifications

## Preface

Voke should be structured to be stable. The environment, security and software purposes.

## Fundamentals

### Windows

Voke should primary work for Windows support.

#### Environment

On installing process, should be asked for configure the Voke environment:
```bat
~ Configuring Voke environment... 
~ Compilers installation dir (empty for default):
```

The default compilers installation dir under `<documents>/cxx/` can be changed latery using `voke --configure` or editing the file under  `<appdata>/<local>/voke/config.vklang`.

So if user set a different dir under other disk, the OS can interact with PATH this disk when running voke software.

### Linux

#### Environment

For Linux you can not change the default compilers dir, we use the native Linux dirs (`/usr/*`). The configure file and cache-dir is set under `~/.local/voke/`, you also, can not change this.

### Security

~

### Software

To reduce external libraries to zero. Except for std. A specialized description-language should be written for Voke, named `vklang`. Which will be used internally in Voke for process of storing per-library, per-compiler properties.

The voke should fetch libraries and compilers from a host, for compilers we will support most of all windows versions, including Microsoft compiler. Libraries can be installed for all compilers once or for only one compiler.

Voke should be a good way to setup local stuff. Can be used not only for libraries but installig compilers, without using an incomplete C/C++ compilers packages from a package-manager.

Voke should be a pacman-like software to be friendly with Arch users. While on Linux is easy to install libraries, build tools and compilers. This will affect goodly the Windows development environment for Vokegpu. May you think why we are not writing a cargo or something else. This is because there are many solutions for this as [xmake](https://xmake.io/). We do not want to write a new-build system or a framework to develop things in C++, but a complete library-manager for ALL build-systems frameworks. While we write a layer of compatibility with CMake, Ninja and Maven etc without directly solving problems between these tools. 
