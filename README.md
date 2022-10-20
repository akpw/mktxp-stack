![License](https://img.shields.io/badge/License-GNU%20GPL-blue.svg)
![Language](https://img.shields.io/badge/docker-%230db7ed.svg)
![License](https://img.shields.io/badge/mikrotik-routeros-orange)
![License](https://img.shields.io/badge/prometheus-exporter-blueviolet)

## Description
MKTXP-Stack is a dockerized monitoring stack for [MKTXP Exporter](https://github.com/akpw/mktxp). 

As an out-of-the-box solution, it lets you quickly get up & running with [MKTXP](https://github.com/akpw/mktxp), [Prometheus](https://prometheus.io/), and [Grafana](https://grafana.com/) and have your Mikrotik RouterOS devices monitored with least amount of configuration. 

While complementary to [MKTXP](https://github.com/akpw/mktxp), this project also adds some extra capabilitis such an Mikrotik log processing based on [syslog-ng](https://www.syslog-ng.com/) & [Loki](https://grafana.com/docs/loki/latest).


## Requirements:
[Docker Compose](https://docs.docker.com/compose/install/)


## Install & Getting Started:
 - Download the code from this repository and extract it into a directory:
```
wget https://github.com/akpw/mktxp-stack/archive/main.zip
unzip main.zip
cd mktxp-stack-main
```

- Configure mktxp as described in [MKTXP Getting Started](https://github.com/akpw/mktxp#getting-started):\
  a) edit the main mktxp config file, adding your Mikrotik device ip address & authentication info to provided sample entry:
  ```
  nano mktxp/mktxp.conf
  ```

  b) if needed, [add a dedicated API user](https://github.com/akpw/mktxp#mikrotik-device-config) from the mktxp config to your RouterOS device:
  ```
  /user group add name=mktxp_group policy=api,read
  /user add name=mktxp_user group=mktxp_group password=mktxp_user_password
  ```

 - Run docker-compose:
```
docker-compose -f ./docker-compose-mktxp.yml up -d
```

Now give the containers some time to start up and point your Web browser to [Grafana](http://localhost:3000), where you should see the default MKTXP Dashboard:
<img src="https://akpw-s3.s3.eu-central-1.amazonaws.com/mktxp_black.png" width="400" height="620">


## Mikrotik Logging pipeline
<img width="400" alt="Screenshot 2022-10-20 at 10 26 25 AM" src="https://user-images.githubusercontent.com/5028474/196961203-24e48499-da84-404b-adb6-d17e56cb6732.png">





