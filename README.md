# LOEB

The *Linaro OpenEmbedded Builder* aims to simplify the building of OE images, with the specific changes that the different stages of the CI pipeline requires.


## Quickstart

```shell
mkdir lkft-1234
cd lkft-1234
loeb init
loeb apply lkft
loeb env
bitbake rpb-console-image
```


## More-common-start

```shell
mkdir lkft-1235
cd lkft-1235
loeb copyconfig https://ci.linaro.org/job/openembedded-lkft-linux-mainline/818/DISTRO=rpb,MACHINE=hikey,label=docker-stretch-amd64
loeb init
loeb apply lkft
ln -s ../oe-downloads downloads
ln -s ../oe-sstate-cache sstate-cache
loeb env
bitbake rpb-console-image
```


## Update Git repositories

```shell
loeb save
repo sync
loeb restore
```


## Notes
* The configuration file is `.loeb.config` in the root directory of the builds. See what's in it.
* To exit the loeb environment, just `exit` from the shell.
* Requires `xpath` (`libxml-xpath-perl` in Debian) for `loeb copyconfig`.
* `loeb reset` will `git-reset` all repos and will wipe out the build directory.

