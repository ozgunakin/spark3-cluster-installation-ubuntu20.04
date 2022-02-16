---
description: >-
  This project includes Apache Spark cluster installation and integration on 3
  server.
---

# Spark3 Multinode Cluster Installation on Ubuntu20.04

## Step 1 - Install Java

If java is not installed on your servers, you can install java by following the instructions in;&#x20;

{% embed url="https://github.com/ozgunakin/java-installation-on-ubuntu20.04" %}

## Step 2 - Configure Host Files

You need to configure host names and host files for each node.

* [x] Open the hosts file

```
sudo nano /etc/hosts
```

* [ ] Add IP addresses and hostnames of each node in the cluster.

```
160.75.61.200 master
160.75.61.201 slave1
160.75.61.202 slave2
```

## Step 3 - Install Scala

```
sudo apt-get install scala
```

## Step 4 - Configure SSH

You need to install open ssh on each node and you need to configure a passwordless ssh connection between nodes.

* [x] Install Open SSH server and client.

```
sudo apt-get install openssh-server openssh-client
```

* [x] Generate Key Pairs on Master

```
ssh-keygen
```

* [x] Copy the content of .ssh/id_rsa.pub(of master) to .ssh/authorized\__keys (of all the slaves as well as master)&#x20;

```
ssh-copy-id user@master
ssh-copy-id user@slave1
ssh-copy-id user@slave2
```

* [x] Test your connection

```
ssh user@slave1
```

## Step 5 - Install Apache Spark

We will do these steps on all nodes.

* [x] Download Apache Spark

```
wget https://dlcdn.apache.org/spark/spark-3.2.1/spark-3.2.1-bin-hadoop3.2.tgz
```

* [x] Extract the file

```
tar xvf spark-3.2.1-bin-hadoop3.2.tgz
```

* [x] Move the extracted file to the opt directory

```
sudo mv spark-3.2.1-bin-hadoop3.2 /opt/
```
