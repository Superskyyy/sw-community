# SkyWalking Community Analysis

## Introduction
A collection of useful settings and scripts for SkyWalking stakeholders to setup CHAOSS GrimoireLab in seconds.

Collects Git, GitHub data from around 30 SkyWalking Ecosystem projects.

## CHAOSS Introduction
[CHAOSS Metrics](https://chaoss.community/metrics/)

[GrimoireLab](https://chaoss.community/software/#user-content-grimoirelab)

Note the affliation analysis is based on a email domains, which wrongly identifies `qq.com and vip.qq.com` as Tencent employees.

So the prodided version removes this chunk from organizations.json in `default-grimoirelab-settings`.
```
        "Tencent": [
            {
                "domain": "qq.com",
                "is_top": true
            },
            {
                "domain": "vip.qq.com",
                "is_top": true
            }
        ],
```

Example Screenshot from Dashboard - 

![localhost_5601_app_kibana (1)](https://user-images.githubusercontent.com/26076517/129667010-3bd334c1-e4aa-40e7-bb83-05ceb34ea59b.png)

![localhost_5601_app_kibana (2)](https://user-images.githubusercontent.com/26076517/129667123-7a1c5545-5be3-4bb7-afdc-d82b3e8e2f84.png)

## Current Usage 
### Manual - 

Copy the `projects.json` to your `default-grimoirelab-settings` folder.

You may wish to set more than one GitHub access token in `setup.cfg` given hourly GitHub API limits.

You will need to increase the `max_map_count` for Elasticsearch before bringing up the ES container, else it will fail.

WSL2 on Windows machine- 
`
wsl -d docker-desktop;
sysctl -w vm.max_map_count=262144
`

Linux
```console
sysctl -w vm.max_map_count=262144
```

MacOS
```
$ screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty
(then run:) sysctl -w vm.max_map_count=262144
```
then `docker-compose up -d`


After the initialization step, go to `localhost:5601` to view the kibana dashboard of GrimoireLab.

Note the data will not appear in a short time if your access to GitHub is slow/ unstable, 
try to use [FastGitHub](https://github.com/dotnetcore/FastGithub) to accelerate the process, else it could take you hours before the projects are fully collected.
