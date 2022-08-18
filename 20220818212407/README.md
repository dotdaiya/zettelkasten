# Useful Linux commands

## Information

```bash
compgen -c # will list all the commands you could run.
compgen -a # will list all the aliases you could run.
compgen -b # will list all the built-ins you could run.
compgen -k # will list all the keywords you could run.
compgen -A # function will list all the functions you could run

lsb_release -a # will list all information of the system
uname -a # TODO
hostnamectl #TODO
cat /etc/issue #TODO
cat /etc/os-release # print operating system info
lsb_release -crid # print operating system info

source # reads and executes commands for the file indicated
printenv # print all environment variables
```

## FileSystem Managment

```bash
tar -C /myfolder -zxvf file_name.tar.gz # extract a .tar.gz in specified folder
tar -C /myfolder -xvf file_name.tar # extrar a .tar in specified folder
```

## Network

```bash
ss -ltpn # see socket information

netstat -s # display network info

cat/var/log/auth.log | grep ssh # check ssh log in debian
cat/var/log/auth.log | grep sshd # check sshd log in debian
```
