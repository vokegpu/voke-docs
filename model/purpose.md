# Purpose

## Preface

While development on Linux is friendly, Windows no, this is a fact, just look on `pacman` installing `libsdl2` or any-other library easily, why Windows does not exists one thing like this?

I mean, yeah, there is, I know, but I will not use, because it does not what I want.

## Voke

### Fundamentals

`voke` is a C++/C library-manager, `voke` should replace the usage of stupid hand-downloading and library installation. On Linux all local libraries install on `/usr/local/share` if CMake is used, so we can easily add packages on any compiler. `voke` does this, compile if needed (or share bin) and install on all compilers path.

### Compiler Definitions Template

A global format to define compile definitions, CMake provides one by default, but we need create an own.
```
# .voke
type: "library"
url: "https://github.com/owner/library"
binary: [mingw: "regex", "win-clang": "regex", "unix-clang": "regex", etc]
cmake: "./"
mkfiletype: "Ninja"
excludecompiler: ["mingw", "emscripten"]
dargs: "-D CUSTOM=1"
src: "./src"
include: "./include"
output: "./build/lib/win32"
```

You do not need to define this, but it is defined like this by default:
```
run: ["cmake -S $cmake -B ./cmake-build -G $mkfiletype $dargs", "cmake --build ./cmake-build"]
```

This way we can compile any library.

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

When [installing](./args.md#sync) an unique library, `voke` will check if can download from an binary and extract the binary or download the source for compile with the toolchain.

With the binary located and headers located, `voke` will copy for all supported compilers, and the`.cmake`.