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

### Building the package

Once the bootstrap is ready, you can build the package with:
```
$ ./xbps-src pkg <pkgname>
```

The above step will create a binary in `hostdir/binpkgs` named
`<pkgname>-<version>_<revision>.<arch>.xbps`.

### Building for other architectures

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

## Releases
If you don't feel like compiling the package yourself, I have a release page
where I upload the xbps binaries for both x86_64 glibc and musl.

For installing this way download the binary and then run:
```
$ cd downloads
$ xbps-rindex -a <pkgname>-<version>_<revision>.<arch>.xbps
# xbps-install -R $PWD <package>
```
