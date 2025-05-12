# Purpose

## Preface

While development on Linux is friendly, Windows no, this is a fact, just look on `pacman` installing `libsdl2` or any-other library easily, why Windows does not exists one thing like this?

I mean, yeah, there is, I know, but I will not use, because it does not what I want.

## Voke

### Fundamentals

`voke` is a C++/C library-manager, `voke` should replace the usage of stupid hand-downloading and library installation. On Linux all local libraries install on `/usr/local/share` if CMake is used, so we can easily add packages on any compiler. `voke` does this, compile if needed (or share bin) and install on all compilers path.

### Library

A global format to define compile definitions, CMake provides one by default, but we need create an own.
```voke
# compiler.voke
--tag                  a tag

--url                  any git repository url

--git-clone-args       useful for large commits history

--build-system         specify build-system: cmake etc

--headers              where public headers file are: path/to/header.hpp path/to/header2.hpp; note they are added under `include-target-dir`
--headers-dirs         where public headers dirs are: path/to/headers path/to/headers2; note they are added under `include-target-dir`

--binaries "--target gnu32 gnu64 clang32 clang64 --dirs dir/to/lib --files path/to/lib.a"
--binaries "--target clang-msvc32 clang-msvc64 mingw32 mingw64 --dirs dir/to/lib --files path/to/lib.a"

--run                  the command for building the project, runs on project dir
                       all wildcards:
                        - $dir              project directory
                        - $c                C compiler target
                        - $cpp              C++ compiler target
                        - $cmake-build-dir  where CMake put generated makefiles, controlled by voke


```

This way we can compile any library/compiler.

### Compiler

(?)

### Installed Compiler

Installed compilers are tracked in `installed-compilers.voke` file under voke system dir, each line describe a compiler.

```voke
# installed-compilers.voke                                                                  
--tag clang --version 19.1.7 --binary-dir /usr/bin --lib-dir /lib64 --include-dir /usr/include --c clang, --cpp clang++ 
--tag gnu --version 14.2.7 20250207 --binary-dir /usr/bin  --lib-dir /lib64 --include-dir /usr/include --c gcc --cpp g++
```

### Installed Library

Installed libraries are tracked in `installed-libraries.voke` file under voke system diur, each line describe a library:

```voke
# installed-libraries.voke
--tag libekg --version 2.0.0 --libs /lib64/libekg.a --includes /usr/include/ekg --compiler clang --type cpp --arch 64
```

### Hosting

We will not force any library to implement `.voke`, all this, is careful imeplemented by VokeGpu, of course, the community too.

For hosting we will use initially GitHub, a repository called `voke-libraries` where all templates will be added. The structure is like this:

```
> libsdl2
> libglew
> etc
readme.MD
```

Each folder is a library, in each folder:
```
.voke
```

### Installing

`voke` will fetch all branches and update the libraries template, then, check if installed libraries contains a new version, if needed [upgrade](./args.md#sync-upgrade).

When [installing](./args.md#sync) an unique library, `voke` will check if can download a release with the binary or download the source for compile later with all the compile-template.

With the binary and headers located, `voke` will copy to `include/` and `bin/` for all supported installed compilers.
