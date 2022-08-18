# Set up WSL2 with debian

To set up WSL2 on windows you need numerous steps. First you need to
active two windows features: Windows Subsystem for Linux and Hyper-V.

After activating those features go to a cmd as admin and type

```bash
wsl -l -v
wsl --set-default-version 2
```

Then restart the computer. After restarting go to the cmd again. Now you
can select your distro, I prefer debian because I'm used to. You can
change your default distro with `wsl --setdefault <distro-name>`. Don't
install Debian on console, install it through Windows Store.
Now you can enter the distro with `wsl.exe`. Once inside, these are the
steps to install docker:

```bash
$ sudo apt update && apt dist-upgrade
$ sudo apt install --no-install-recommends apt-transport-https ca-certificates curl gnupg2 lsb-release
$ sudo source /etc/os-release
$ sudo mkdir -p /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
$ sudo chmod a+r /etc/apt/keyrings/docker.gpg
$ sudo apt update
$ sudo apt install docker-ce docker-ce-cli containerd.io
$ sudo usermod -aG docker <username>
$ exec su -l <username> # to reload
```

Then to make sure that docker is accesible from the outside without
Docker Desktop, we need to execute these steps:

```bash
$ DOCKER_DIR=/mnt/wsl/shared-docker
$ mkdir -pm o=,ug=rwx "$DOCKER_DIR"
$ sudo chgrp docker "$DOCKER_DIR"
$ sudo mkdir /etc/docker
$ sudo vi /etc/docker/daemon.json

{
    "hosts": ["unix:///mnt/wsl/shared-docker/docker.sock"],
    "iptables": false
}

$ sudo vi /etc/sudoers

%docker ALL=(ALL) NOPASSWD: /usr/bin/dockerd

$ sudo dockerd # to test if it works it should output
# "API listen on /mnt/wsl/shared-docker/docker.sock"
$ docker -H unix:///mnt/wsl/shared-docker/docker.sock run --rm hello-world # another test
```

To make it automatic, edita `.bashrc` or `.profile`.

That's it. Neverthless, I want to investigate how to create Virtual
Machines with Hyper-V without WSL2, WSL2 has it's issues.
