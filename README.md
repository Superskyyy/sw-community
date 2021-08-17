# SkyWalking Community Analysis

## Introduction
A collection of useful settings and scripts for SkyWalking stakeholders to setup CHAOSS GrimoireLab in seconds.

Collects Git, GitHub data from around 30 SkyWalking Ecosystem projects.

## CHAOSS Introduction
[CHAOSS Metrics](https://chaoss.community/metrics/)

[GrimoireLab](https://chaoss.community/software/#user-content-grimoirelab)

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

then `docker-compose up -d`


After the initialization step, go to `localhost:5601` to view the kibana dashboard of GrimoireLab.

Note the data will not appear in a short time if your access to GitHub is slow/ unstable, 
try to use [FastGitHub](https://github.com/dotnetcore/FastGithub) to accelerate the process, else it could take you hours before the projects are fully collected.
