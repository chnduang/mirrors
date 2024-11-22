# Docker

### 镜像站

```shell
sudo vi /etc/docker/daemon.json
```

### 临时指定

```shell
-–registry-mirror=
```

### daemon.json

```shell
{
  "registry-mirrors": [
      "https://docker.m.daocloud.io",
      "https://docker.1panel.live",
      "https://hub.rat.dev",
      "https://hub-mirror.c.163.com",
      "https://dockerpull.org",
      "https://dockerpull.com",
      "https://docker.1panel.dev",
      "https://docker.1ms.run",
      "https://hub.geekery.cn",
      "https://registry.docker-cn.com"
    ]
}
```



