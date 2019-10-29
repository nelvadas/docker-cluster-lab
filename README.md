# Bootstraping Docker EE clusters : The easy way
This lab purpose is to demonstrate how to bootstrap a Docker EE cluster easily using *docker cluster* command.



## Provide Cloud details

```
$ cat ~/.aws/credentials

[default]
aws_access_key_id = *****
aws_secret_access_key = ***

```

## Provide a cluster description 

cluster.yml 



## Create the Cluster 

```
docker cluster create -f cluster.yml 
```


/.docker/cluster/clusters/6b0f556107c7/license/docker-ee.lic



```
DEBU[0719] PLAY RECAP *********************************************************************
DEBU[0719] 04e616e36619-managers-1    : ok=129  changed=46   unreachable=0    failed=0
DEBU[0719] 04e616e36619-registry-1    : ok=108  changed=38   unreachable=0    failed=0
DEBU[0719] 04e616e36619-workers-1     : ok=88   changed=31   unreachable=0    failed=0
DEBU[0719] localhost                  : ok=34   changed=4    unreachable=0    failed=0
DEBU[0719]
DEBU[0719] Install Completed

quickstart
Successfully created context "quickstart"
Connect to quickstart at:

 https://34.236.237.84

04e616e36619
EW-MBPt15-2018:docker-cluster-lab$
```



## Check Contexts

```
EW-MBPt15-2018:docker-cluster-lab $ docker context  ls
NAME                DESCRIPTION                               DOCKER ENDPOINT               KUBERNETES ENDPOINT           ORCHESTRATOR
default *           Current DOCKER_HOST based    unix:///var/run/docker.sock   https://ucp.dev01.dockernetes.org:1883 (appa)   swarm
quickstart          quickstart                                tcp://34.236.237.84:443
EW-MBPt15-2018:docker-cluster-lab $
```
