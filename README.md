# LibreWolf Package for Void Linux

I have taken the responsibility of unofficially maintaining LibreWolf for Void
Linux as the void-packages repository doesn't accept browser forks:
> Browser forks, including those based on Chromium and Firefox, are generally
> not accepted. Such forks require heavy patching, maintenance and hours of
> build time.

## Compiling
### Preparing the environment

Clone the void-packages repository:
```
$ git clone https://github.com/void-linux/void-packages
```

Change to the new `void-packages` repository and install the bootstrap
packages:
```
$ cd void-packages
$ ./xbps-src binary-bootstrap
```

### Downloading the package

```
$ git clone https://github.com/index-0/librewolf-voidlinux.git
```
Once you have cloned the repository, copy the contents inside the srcpkg folder
into the void-packages srcpkg folder.

### Building the package

Once the bootstrap is ready, you can build the package with:
```
$ ./xbps-src pkg <pkgname>
```
Note: if your computer has enough resources, the -j <n> option can be used to
speed the building process, just take into consideration that 6 GiB of memory
is needed per job to prevent the system from hanging.

After a while, the above step will create a binary in `hostdir/binpkgs` named
`<pkgname>-<version>_<revision>.<arch>.xbps`.

### Building for another architecture

You must first create a new masterdir for the desired architecture:
```
$ ./xbps-src -m <masterdir> binary-bootstrap <arch>
```
where `<masterdir>` can have any name, I suggest `masterdir-<arch>`.

Once the bootstrap for the new masterdir is ready, you can proceed to build
packages with:
```
$ ./xbps-src -m <masterdir> pkg <package>
```

## Installing

Once the package is in `hostdir/binpkgs/` you can install it with:
```
# xbps-install -R hostdir/binpkgs <package>
```
