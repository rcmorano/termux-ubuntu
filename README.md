# Introduction

These [baids] will setup a chroot inside a Termux [0] shell by downloading an Ubuntu core cloud image [1] and allow executing commands by using proot [2].

# Instructions

* Setup copy+paste snippet:
```
# install depends
pkg install git
# install baids
curl -sSL https://raw.githubusercontent.com/rcmorano/baids/master/baids | bash -s install
source ~/.baids/baids
# install these baids
git clone git@github.com:rcmorano/termux-ubuntu-baids.git ~/.baids/functions.d/termux-ubuntu
baids-reload
```
* Setup an ubuntu-bionic chroot (or let it be done by the fisrt shell/exec baid execution):
```
termux-ubuntu-setup bionic
```
* Spawn a ubuntu-focal shell:
```
termux-ubuntu-shell focal 
```
* Execute a specific command into a ubuntu-bionic chroot:
```
termux-ubuntu-exec bionic cat /etc/lsb-release
```

# Misc

## Setup SSH server

* Run inside an ubuntu-shell:
```
apt-get update -qq && apt-get install -y openssh-server
# set ssh server to listen on an unprivileged port
sed -i 's|^#Port=.*|Port=44444' /etc/ssh/sshd_config
service ssh start
```
* Add some ssh pubkeys or setup an user (root user does not have any passwd set by default)


[baids]: https://github.com/rcmorano/baids
[0]: https://play.google.com/store/apps/details?id=com.termux
[1]: https://partner-images.canonical.com/core
[2]: https://wiki.termux.com/wiki/PRoot
