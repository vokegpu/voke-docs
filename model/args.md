discuss.

## Flow

### Compiler

`voke -sc *`  
`     --sync-compiler *`

Install a compiler, for example MinGW32-x86_64:
`voke -Sc mingw64`  
`     --sync-compiler mingw64`

### Sync

`voke -s *`  
`     --sync *`

Sync a library, it will search for the library under `voke-libraries` repository.  
This installs or update.

Custom options:

| - | `voke -s * -b *`    install directly the binary.  
      `          --bin *`  

| - | `voke -s * -v *`        install a specified version.  
      `          --version *`

### Sync-Upgrade

`voke`
`     -su`
`     --sync-upgrade`


Sync and upgrade ALL libraries current installed, this will ask for updagrade all latest libraries.