---
title: "Deploying Portworx on Docker Enterprise Solution Brief"
summary: "Portworx is one of the leading Software-Defined Storage solutions for
  container deployments. This document is a walkthrough of installing Portworx on
  a Docker Enterprise 3.0 install."
type: guide
author: khudgins
visibleto: loggedinleads
campaign: "docker-certified-infrastructure"
product:
  - ee
testedon:
  - "v1.14.3-docker-2	"
  - "ucp-3.0"
  - "dtr-2.7.1"
platform:
  - linux
tags:
  - "solution-brief"
  - storage
dateModified: "2019-08-22T13:24:21+00:00"
dateModified_unix: 1566498118
uniqueid: KB000669
---
## Overview

Portworx is one of the leading Software-Defined Storage solutions for container deployments. This document is a walkthrough of installing Portworx on a Docker Enterprise 3.0 install for Kubernetes workloads.

## Prerequisites

The following prerequisites are required to successfully complete this guide:


- Docker Enterprise 3.0 installed with at least two Kubernetes worker nodes
- A license for, or trial of Portworx Enterprise
- A workstation with the kubectl command bound to your Docker Enterprise install. (This can be the installation's master node)

## Installation and Configuration

1. First step:
    Add an unmounted disk of 50Gb min to each worker node. You should be able to see the unmounted disk with the following command once you log in to each worker node

    ```
    NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
    loop0     7:0    0 88.5M  1 loop /snap/core/7270
    loop1     7:1    0   18M  1 loop /snap/amazon-ssm-agent/1455
    loop2     7:2    0 10.1M  1 loop /snap/kubectl/1139
    loop3     7:3    0 88.7M  1 loop /snap/core/7396
    xvda    202:0    0   20G  0 disk
    └─xvda1 202:1    0   20G  0 part /
    xvdb    202:16   0  100G  0 disk /var/lib/docker
    xvdf    202:80   0  150G  0 disk

    ```

2. Second step:
    Confirm the Docker Enterprise version with the following command on your prepared workstation.

    ```
    $ kubectl version --short | awk -Fv '/Server Version: / {print $3}'
    1.14.3-docker-2
    ```

3. Third step:

    In this step, we will use Portworx's online install wizard to create a Kubernetes YAML deployment definition.

    In a web browser, navigate to http://install.portworx.com and enter the Docker version

    ![example 1] (example_1.png) "install.portworx.com screen 1" 

    ```
    vi readme.md
    git commit -m "updated some docs"
    ```

    Make sure to use step-by-step examples:

    ```
    % docker info
    ```

    and include output when necessary:

    ```
    Containers: 0
    Running: 0
    Paused: 0
    Stopped: 0
    Images: 0
    Server Version: 17.12.0-ce
    ...

    Experimental: true
    Insecure Registries:
     127.0.0.0/8
    Live Restore Enabled: false
    ```


## Best Practice Recommendations

When updating your solution brief, Docker should automatically pull in your changes during our documentation releases. In the event you need to get the content published faster (ie: bugfix issues), contact your Docker partner representative so they can notify the publishing team.

## Monitoring and Troubleshooting

Add operational instructions as needed. If there are any gotchas or difficult parts, troubleshooting advice goes here as well.

## Further Reading

Refer to the following links for additional information:

- <https://github.com/vmware/vsphere-storage-for-docker>
- <http://vmware.github.io/vsphere-storage-for-docker/documentation/>
- <https://bintray.com/vmware/vDVS/VIB/>
