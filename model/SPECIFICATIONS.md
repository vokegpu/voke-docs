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

#### Security

~

#### Software

To reduce external libraries to zero. Except for std. A specialized description-language should be written for Voke, named `vklang`. Which will be used internally in Voke for process of storing per-library, per-compiler stuff.

