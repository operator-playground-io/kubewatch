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
NAME                         READY   STATUS       RESTARTS   AGE
kubewatch-7595695645-x966d   1/1     Running       0          14s
```

### To check logs 

```execute
kubectl logs -f kubewatch-7595695645-x966d
```

You will get Similar Output

```
E0208 06:20:52.681504       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Deployment: deployments.apps is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "deployments" in API group "apps" at the cluster scope
E0208 06:20:53.682553       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Pod: pods is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "pods" in API group "" at the cluster scope
E0208 06:20:53.683031       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Deployment: deployments.apps is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "deployments" in API group "apps" at the cluster scope
E0208 06:20:54.684115       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Pod: pods is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "pods" in API group "" at the cluster scope
E0208 06:20:54.685593       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Deployment: deployments.apps is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "deployments" in API group "apps" at the cluster scope
E0208 06:20:55.686953       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Pod: pods is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "pods" in API group "" at the cluster scope
E0208 06:20:55.687083       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Deployment: deployments.apps is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "deployments" in API group "apps" at the cluster scope
E0208 06:20:56.688484       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Pod: pods is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "pods" in API group "" at the cluster scope
E0208 06:20:56.689537       1 reflector.go:123] github.com/bitnami-labs/kubewatch/pkg/controller/controller.go:466: Failed to list *v1.Deployment: deployments.apps is forbidden: User "system:serviceaccount:default:kubewatch" cannot list resource "deployments" in API group "apps" at the cluster scope

```

The above  error occurs due to  improper permission for cluster. To fix the permission apply the below configs,

```execute
cat <<EOF | kubectl apply -f -
---
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: kubewatch
rules:
- apiGroups: ["", "extensions", "apps", "batch"]
  resources: [ "pods", "jobs", "namespaces", "services", "deployments", "replicationcontrollers", "replicasets", "daemonsets"]
  verbs: ["get", "watch", "list"]
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: kubewatch
  namespace: default
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
  name: kubewatch
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: kubewatch
subjects:
  - kind: ServiceAccount
    name: kubewatch
    namespace: default
EOF

```


You will see similar Output;


```
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: kube-system/kube-scheduler-event-k8s-ibm-operators-playground-ndwmzi.softlayer.com" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: local-path-storage/local-path-provisioner-59d7b946f5-zznq4" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: olm/olm-operator-946bd977f-mmrdp" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: olm/packageserver-5bc8644956-qzmrq" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: kube-system/kube-flannel-ds-amd64-lhggv" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: kubernetes-dashboard/kubernetes-dashboard-6ff4884d7-64gjd" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: olm/catalog-operator-7b788c597d-hnhlb" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: kube-system/etcd-event-k8s-ibm-operators-playground-ndwmzi.softlayer.com" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: kubernetes-dashboard/dashboard-metrics-scraper-c79c65bb7-lvfrp" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: olm/operatorhubio-catalog-rkcbx" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: olm/packageserver-5bc8644956-n4bqw" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Processing add to pod: default/kubewatch-7595695645-j9242" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Kubewatch controller synced and ready" pkg=kubewatch-pod
time="2021-02-08T06:31:34Z" level=info msg="Kubewatch controller synced and ready" pkg=kubewatch-deployment

```

Kubewatch is sucuessfull installed.





