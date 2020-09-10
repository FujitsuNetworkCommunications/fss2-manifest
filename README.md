# FSS2Linux

![N|FssLinux](http://www.fujitsu.com/global/resources/design/stylesheets/images/css_images/fujitsu/symbolmark.gif)

FSS2 Linux is based of poky 2.3 (pyro), 4.1 or 4.9 kernel and hosted on public github server maintained by Fujitsu organization.
Following describes workflow and steps to download FSS2Linux from public github and create a working build environment.

## Installation

### Preprequites
#### Build system
FSS2Linux requires one of the following sanity tested distros for building distro.
```sh
    - Ubuntu-15.04
    - Ubuntu-16.04
    - Ubuntu-16.10
    - Fedora-24
    - Fedora-25
    - CentOS-7
    - Debian-8
    - openSUSE-42.1
    - openSUSE-42.2
```
### Working with yocto build
Install the dependencies and devDependencies and restart the server.

Ubuntu and Debian:


```sh
$ sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib \
build-essential chrpath socat cpio python python3 python3-pip python3-pexpect \
xz-utils debianutils iputils-ping libsdl1.2-dev xterm
```

Fedora:

```sh
$ sudo dnf install gawk make wget tar bzip2 gzip python3 unzip perl patch \
diffutils diffstat git cpp gcc gcc-c++ glibc-devel texinfo chrpath ccache \
perl-Data-Dumper perl-Text-ParseWords perl-Thread-Queue perl-bignum socat \
python3-pexpect findutils which file cpio python python3-pip xz which SDL-devel xterm
```

CentOS:

```sh
$ sudo yum install -y epel-release
$ sudo yum makecache
$ sudo yum install gawk make wget tar bzip2 gzip python unzip perl patch \
diffutils diffstat git cpp gcc gcc-c++ glibc-devel texinfo chrpath socat \
perl-Data-Dumper perl-Text-ParseWords perl-Thread-Queue python34-pip xz \
which SDL-devel xterm
```

OpenSUSE:

```sh
$ sudo zypper install python gcc gcc-c++ git chrpath make wget python-xml \
diffstat makeinfo python-curses patch socat python3 python3-curses tar \
python3-pip python3-pexpect xz which libSDL-devel xterm
```

### Install repo tools
repo tools is based off andriod project and required to build yocto

```sh
mkdir ~/bin
export PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
cd ~/bin
chmod +x repo
```

### Configure Git for the first time
```sh
cd
git config --global user.name "your Name"
git config --global user.email "you@email.com"
```

## Building FSS2Linux

#### Qemux86-64 target
```sh
cd
mkdir working_dir
cd working_dir
repo init -u https://github.com/FujitsuNetworkCommunications/fss2-manifest -b pyro-20.1
repo sync
source poky/fss2-init-build-env
bitbake core-image-minimal
```

#### T600 PPC target
```sh
cd
mkdir working_dir
cd working_dir
repo init -u https://github.com/FujitsuNetworkCommunications/fss2-manifest -b pyro-20.1
repo sync
source poky/fss2-init-build-env -m t600
bitbake core-image-minimal
```

#### T700 PPC target
```sh
cd
mkdir working_dir
cd working_dir
repo init -u https://github.com/FujitsuNetworkCommunications/fss2-manifest -b pyro-20.1
repo sync
source poky/fss2-init-build-env -m 700
bitbake core-image-minimal
```

License
----

[GPLv2](https://github.com/FujitsuNetworkCommunications/fss2-manifest/blob/master/LICENSE.md)


## Maintainers 

Dan Berger  @drberger
Rajeev Shekar @rshekarfnc
David T @dwterwil

