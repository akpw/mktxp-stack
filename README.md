![License](https://img.shields.io/badge/License-GNU%20GPL-blue.svg)
![Language](https://img.shields.io/badge/docker-%230db7ed.svg)
![License](https://img.shields.io/badge/mikrotik-routeros-orange)
![License](https://img.shields.io/badge/prometheus-exporter-blueviolet)

## Description
MKTXP-Monitor is an out-of-the-box dockerized monitoring stack for [MKTXP Exporter](https://github.com/akpw/mktxp). This is mostly to get people up & running with [mktxp](https://github.com/akpw/mktxp) and have your Mikrotik routers monitored with least amount of configuration, though this project also adds some extra capabilitis such an [Loki](https://grafana.com/docs/loki/latest/?tech=target&pg=oss-loki&plcmt=quick-links&cta=A)-based Mikrotik log processing, etc. 


#### Requirements:
[Docker](https://docs.docker.com/get-docker/)\
[Docker Compose](https://docs.docker.com/compose/install/)


#### Install:
 - Download the code from this repository and extract it into a directory:
```
wget https://github.com/akpw/mktxp-monitor/archive/main.zip
unzip main.zip
cd mktxp-monitor-main
```

- [Edit the base mktxp config file]((https://github.com/akpw/mktxp#getting-started)) & [add a dedicated user to your router](https://github.com/akpw/mktxp#mikrotik-device-config):
```
nano mktxp/mktxp.conf
```

```
/user group add name=mktxp_group policy=api,read
/user add name=mktxp_user group=mktxp_group password=mktxp_user_password
```

 - Run docker-compose, give the containers some time to start up and then point your Web browser to [Grafana]:(http://localhost:3000)
```
docker-compose -f ./docker-compose-mktxp.yml up -d
```

