# Moving the default docker dir

```bash
1. $ vim /lib/systemd/system/docker.service
2.   REPLACE 'ExecStart=/usr/bin/docker daemon -H fd://' WITH 'ExecStart=/usr/bin/docker daemon -g /new/path/docker -H fd://'
3. $ systemctl stop docker
4. $ systemctl daemon-reload
5. $ rsync -aqxP /var/lib/docker/ /new/path/docker
6. $ systemctl start docker
```
