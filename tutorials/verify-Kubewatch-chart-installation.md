---
title: Verify Kubewatch Chart Installation
description: This tutorial explains how to verify that Kafka chart installed successfully
---


Once the helm chart installation done you need to verify all the pods and services are up and running.

Execute below command to check status of pods and services: 

### Check the pod status


```execute
kubectl get pods --namespace Kubewatch
```

You will see similar to this output:

```
NAME                     READY   STATUS              RESTARTS   AGE
my-release-Kubewatch-0       0/1     ContainerCreating   0          16s
```

It may take few minutes to change the `STATUS` from `ContainerCreating` to `Running`. 

```output
NAME                         READY   STATUS    RESTARTS   AGE
pod/my-release-kafka-0       1/1     Running   0          61s
pod/my-release-zookeeper-0   1/1     Running   0          61s
```

Once the `Kubewtach` and PODs are up and running , and `READY` states are `1/1` for both, your Kafka is ready to use.

### Check all the Kubernetes resources status

You can run the following command to know status of all the deployed resources inside the namespace `kafka`


```execute
kubectl get all --namespace Kubewatch
```

All the deployment and service status should be Running.

```
NAME                         READY   STATUS    RESTARTS   AGE
pod/my-release-kafka-0       1/1     Running   0          65m
```
