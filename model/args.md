# Args

## Compiler

```sh
voke -sc *
     --sync-compiler *
```

Install a compiler.

## Sync

```sh
voke -s *
     --sync *
```

Sync a library, it will search for the library under `voke-libraries` repository.  
This installs or update.

### Options

```sh
voke -s * -b *  
          --binary *  
```

Install using the binary.

```sh
voke -s * -v *
          --version *
```

Install with a specified version.

## Sync-Upgrade

```sh
voke
     -su
     --sync-upgrade
```

Sync and upgrade ALL libraries current installed, this will ask for updagrade all latest libraries.