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
docker cluster create -f cluster.yml --name quickstart --log-level debug

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



## Contexts

```
DEBU[0800]
DEBU[0800] PLAY RECAP *********************************************************************
DEBU[0800] ebee507bb0ae-managers-1    : ok=129  changed=46   unreachable=0    failed=0
DEBU[0800] ebee507bb0ae-registry-1    : ok=108  changed=38   unreachable=0    failed=0
DEBU[0800] ebee507bb0ae-workers-1     : ok=88   changed=31   unreachable=0    failed=0
DEBU[0800] localhost                  : ok=34   changed=4    unreachable=0    failed=0
DEBU[0800]
DEBU[0800] Install Completed

uat
Successfully created context "uat"
Connect to uat at:

 https://3.223.140.121

ebee507bb0ae
EW-MBPt15-2018:docker-cluster-lab elvadasnonowoguia$ docker context ls
NAME                DESCRIPTION                               DOCKER ENDPOINT               KUBERNETES ENDPOINT                                  ORCHESTRATOR
default *           Current DOCKER_HOST based configuration   unix:///var/run/docker.sock   https://ucp.dev01.dockernetes.org:1883 (pod-check)   swarm
uat                 uat                                       tcp://3.223.140.121:443
EW-MBPt15-2018:docker-cluster-lab elvadasnonowoguia$ docker context use uat
uat
Current context is now "uat"
EW-MBPt15-2018:docker-cluster-lab elvadasnonowoguia$ docker node ls
ID                            HOSTNAME                       STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
6yb9tuyfs84w5kde0qzkfwbd3     ip-10-20-32-216.ec2.internal   Ready               Active                                  19.03.4
5ud0e06bha7amnbqie8aqst1o *   ip-10-20-45-52.ec2.internal    Ready               Active              Leader              19.03.4
j1ryeknwtrhb2a50x23ci61n9     ip-10-20-45-185.ec2.internal   Ready               Active                                  19.03.4
EW-MBPt15-2018:docker-cluster-lab elvadasnonowoguia$
```

## Inspect Context 
```
EW-MBPt15-2018:docker-cluster-lab elvadasnonowoguia$ docker context inspect uat
[
    {
        "Name": "uat",
        "Metadata": {
            "Description": "uat"
        },
        "Endpoints": {
            "docker": {
                "Host": "tcp://3.223.140.121:443",
                "SkipTLSVerify": false
            }
        },
        "TLSMaterial": {
            "docker": [
                "ca.pem",
                "cert.pem",
                "key.pem"
            ]
        },
        "Storage": {
            "MetadataPath": "/Users/elvadasnonowoguia/.docker/contexts/meta/6d45573b512994ea253cafe8ec6a9d0f941b4f6da829b331cbc55c121b029997",
            "TLSPath": "/Users/elvadasnonowoguia/.docker/contexts/tls/6d45573b512994ea253cafe8ec6a9d0f941b4f6da829b331cbc55c121b029997"
        }
    }
```



## More infos 
[Docker cluster AWS Doc] (https://github.com/docker/cluster/blob/master/docs/aws.md)

