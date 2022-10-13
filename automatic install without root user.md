# Install packages in Linux (CentOS) without root user with automatic dependency handling


It is possible to use yum and rpm to install any package in the repository of the distribution. Here is the recipe:

## Find the package name
Use `yum search`.

## Download
Download the package and all of its dependencies using `yumdownloader` (which is available on CentOS by default). You'll need to pass it `--resolve` to get dependency resolution. `yumdownloader` downloads to the current directory unless you specify a `--destdir`.
```
mkdir -p ~/rpm
yumdownloader --destdir ~/rpm --resolve vim-common
```
## Choose a prefix location
It might be `~`, `~/centos`, or `~/y`. If your home is slow because it is on a network file system, you can put it in `/var/tmp/...`.
```
mkdir ~/centos
```
## Extract all .rpm packages
Extract all .rpm packages to your chosen prefix location.
```
cd ~/centos && rpm2cpio ~/rpm/x.rpm | cpio -id
```
rpm2cpio outputs the .rpm file as a .cpio archive on stdout.
cpio reads it from from stdin
-i means extract (to the current directory)
-d means create missing directory
You can optionally use -v: verbose

## Configure the environment
You will need to configure the environment variable PATH and LD_LIBRARY_PATH for the installed packages to work correctly. Here is the corresponding sample from my ~/.bashrc:
```
export PATH="$HOME/centos/usr/sbin:$HOME/centos/usr/bin:$HOME/centos/bin:$PATH"

export MANPATH="$HOME/centos/usr/share/man:$MANPATH"

L='/lib:/lib64:/usr/lib:/usr/lib64'
export LD_LIBRARY_PATH="$HOME/centos/usr/lib:$HOME/centos/usr/lib64:$L"
```

Now if you want to install a lot of packages that way, you might want to automate the process. If so, have a look at this repository.

Extra note: if you are trying to install any of ```gcc, zlib, make, cmake, git, fish, zsh or tmux ```, you should really consider using conda, see my other answer.
