# termux-ubuntu

A script to install Ubuntu chroot in Termux

# Setup

```
UBUNTU_CODENAME=focal
mkdir -p ${HOME}/ubuntu-chroots/${UBUNTU_CODENAME} && cd ${HOME}/ubuntu-chroots/${UBUNTU_CODENAME}
curl -sSL https://raw.githubusercontent.com/rcmorano/baids/master/baids | bash -s ${UBUNTU_CODENAME}
```

# Usage

```
UBUNTU_CODENAME=focal
cd ${HOME}/ubuntu-chroots/${UBUNTU_CODENAME}
bash ubuntu-shell
```

# Setup SSH server
UBUNTU_CODENAME=focal
cd ${HOME}/ubuntu-chroots/${UBUNTU_CODENAME}
bash ubuntu-shell apt-get update -qq && apt-get install -y openssh-server
# set ssh server to listen on an unprivileged port
bash ubuntu-shell sed -i 's|^#Port=.*|Port=44444' /etc/ssh/sshd_config
bash ubuntu-shell service ssh start
