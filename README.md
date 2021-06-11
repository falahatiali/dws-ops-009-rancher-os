[@dwsclass](https://github.com/dwsclass) dws-ops-009-rancher-os

RancherOS Excercise...

Question

**RancherOS**
 **__________________________**
 
## **Install RancherOS and enable auto resize disk:**

[@install-rancher](https://github.com/falahatiali/dws-ops-009-rancher-os/blob/master/install-rancher.yaml)

 
 **__________________________**
 
## **Change Hostname in Rancher:**

```
 - sudo su - #change to root user
 - ros config set hostname dwsclass-alifalahati #change hostname
 - reboot #reboot. its necessary
 
```

**__________________________**

## **How to disable debug, autologin, password capabilities ?**
 
 [@disable-capabilities](https://github.com/falahatiali/dws-ops-009-rancher-os/blob/master/disable-capabilities.yaml)

```
1 - ros config validate -i disable-capabilities.yaml
2 - ros config merge -i disable-capabilities.yaml
```

**__________________________**

## **change default ssh port to 2222**
 
 [@change-ssh-port](https://github.com/falahatiali/dws-ops-009-rancher-os/blob/master/ssh.yaml)

```
1 - ros config validate -i ssh.yaml
2 - ros config merge -i ssh.yaml
```

**__________________________**

## **Enable NFS service**
 
 [@nfs](https://github.com/falahatiali/dws-ops-009-rancher-os/blob/master/nfs.yaml)

```
1 - ros config validate -i nfs.yaml
2 - ros config merge -i nfs.yaml
```


**__________________________**

## **Enable NodeExporter serivice**
 
 [@node-exporter](https://github.com/falahatiali/dws-ops-009-rancher-os/blob/master/node-exporter.yml)

```
1 - ros config validate -i node-exporter.yaml
2 - ros config merge -i node-exporter.yaml
```

**__________________________**

## **Change TimeZone**
 

```
1 - ros config set environment.TZ "Asia/Tehran"
```

You can edit following file:

```
vi /usr/share/ros/os-config.yml
```

seach for console and add following key-value:
```
TZ=Asia/Tehran # in environment
```
you should see following settings:
```
    console:                                  
      image: rancher/os-console:v1.5.8
      command: ros console-init        
      labels:                                     
        io.rancher.os.scope: system             
        io.rancher.os.after: cloud-init-execute
        io.docker.compose.rebuild: always     
        io.rancher.os.console: default
      environment:                   
      - HTTP_PROXY                             
      - HTTPS_PROXY                      
      - NO_PROXY                      
      - TZ=Asia/Tehran                                                 
```
## **Console**

BusyBox Console

```
/home
/opt
/var/lib/docker
/var/lib/rancher
/var/lib/kubelet
```