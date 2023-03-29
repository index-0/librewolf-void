# LibreWolf Package for Void Linux

I have taken the responsibility of unofficially maintaining LibreWolf for Void
Linux as the void-packages repository doesn't accept browser forks, according
to the repository:
> Browser forks, including those based on Chromium and Firefox, are generally
> not accepted. Such forks require heavy patching, maintenance and hours of
> build time.

## Compiling
### Preparing the environment

Clone the void-packages repository:
```
$ git clone https://github.com/void-linux/void-packages
```

Change to the new `void-packages` folder and proceed to build the bootstrap:
```
$ cd void-packages
$ ./xbps-src binary-bootstrap
```

### Downloading the package

```
$ git clone https://github.com/index-0/librewolf-voidlinux.git
```
Once you have cloned the repository, copy the contents inside the srcpkgs folder
into the void-packages srcpkgs folder.

### Building the package

Once the bootstrap is ready, it's time to build the package with:
```
$ ./xbps-src pkg <pkgname>
```
**Note**: _if your computer has enough resources, the -j \<n\> option can be used to
speed the building process, just take into consideration that 6 GiB of memory
is needed per job to prevent the system from hanging._

After a while, the above step will create a binary in `hostdir/binpkgs` named
`<pkgname>-<version>_<revision>.<arch>.xbps`.

## Installing

Once the package is successfully built and in the `hostdir/binpkgs` directory
you can install it with:
```
# xbps-install -R hostdir/binpkgs <package>
```

## Keeping your Environment Up-to-Date

Before compiling Librewolf, it is recommended that you update your environment
to ensure you have the latest changes. This involves updating your local
void-packages repository and then updating the bootstrap packages.

### Updating the Repository

Update your local void-packages repository to the latest version:
```
$ git pull origin master
```

### Updating the Bootstrap Packages

Sometimes, you may need to update the bootstrap packages to the latest version
available in the repositories. To do this run:
```
$ ./xbps-src bootstrap-update
```
